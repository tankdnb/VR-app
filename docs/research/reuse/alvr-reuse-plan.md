# ALVR Reuse Plan

- Date: `2026-04-09`
- Repo reviewed: `https://github.com/alvr-org/ALVR`
- Goal: identify which parts of `ALVR` are useful as donors for the `Reality Window` MVP on `PICO/OpenXR`.

## High-level conclusion

`ALVR` is not a good base product for this app, but it is a very good donor for:

- Android OpenXR bootstrap on standalone headsets;
- vendor-specific OpenXR extension handling;
- passthrough layer composition;
- `PICO` packaging metadata and runtime compatibility tricks.

It is **not** a good donor for:

- the streaming stack;
- the SteamVR remote-play architecture;
- the network protocol;
- the PC dashboard / server / codec pipeline.

## The most useful parts

### 1. Android OpenXR bootstrap

`ALVR` already ships an Android OpenXR client and initializes Android loader + instance creation.

Useful references:

- `alvr/client_openxr/src/lib.rs`
- `alvr/client_openxr/src/c_api.rs`

Why this matters:

- it validates a production-grade `OpenXR` app path on Android standalone headsets;
- it already handles `ndk_context` bootstrap from a C ABI entry point;
- it explicitly initializes the Android loader before `enumerate_extensions()` / `create_instance()`.

### 2. Runtime-specific loader selection for Pico

`ALVR` does something especially interesting for Pico:

- in `client_openxr/src/lib.rs`, it chooses a loader suffix based on platform;
- for `PicoNeo3`, `PicoG3`, `Pico4`, `Pico4Pro`, `Pico4Enterprise`, it uses `"_pico_old"`;
- then it loads `libopenxr_loader{suffix}.so`.

This is very relevant to our findings because:

- we already proved that the generic `libopenxr_loader.so` path was not enough on the headset;
- `ALVR` suggests that Pico compatibility may depend on a headset-specific loader build/package strategy.

### 3. Passthrough composition pattern

`ALVR` has a dedicated passthrough layer abstraction:

- `alvr/client_openxr/src/passthrough.rs`
- `alvr/client_openxr/src/extra_extensions/passthrough_fb.rs`

Why this is important:

- our latest probe showed `XR_FB_passthrough: true`;
- `ALVR` already creates `PassthroughFB`, `PassthroughLayerFB`, and submits it as an OpenXR composition layer;
- this is currently the closest code path to our next spike.

This is likely the single most valuable donor path in the repo for our next iteration.

### 4. Vendor extension pattern for unsupported APIs

`ALVR` has a strong pattern for vendor APIs that are not cleanly exposed by the higher-level crate:

- `alvr/client_openxr/src/extra_extensions/mod.rs`
- `alvr/client_openxr/src/extra_extensions/body_tracking_bd.rs`
- `alvr/client_openxr/src/extra_extensions/face_tracking_pico.rs`

What they do:

- define vendor extension names as constants;
- define raw structure types with explicit numeric `StructureType` values;
- fetch function pointers using `xrGetInstanceProcAddr`;
- build wrappers around vendor functionality.

Why this matters to us:

- our runtime advertises `XR_BD_external_camera` and `XR_BD_mr_management`;
- these are exactly the kinds of extensions where ALVR's pattern is more useful than its literal feature code.

### 5. Android manifest / permission / metadata setup

`ALVR`'s Android packaging metadata is valuable even if we do not reuse its app itself.

Useful reference:

- `alvr/client_openxr/Cargo.toml`

Notable points:

- OpenXR Android permissions:
  - `org.khronos.openxr.permission.OPENXR`
  - `org.khronos.openxr.permission.OPENXR_SYSTEM`
- OpenXR runtime broker queries:
  - `org.khronos.openxr.OpenXRRuntimeService`
  - provider authorities for the runtime broker
- Pico metadata:
  - `pvr.sdk.version = OpenXR`
  - `pxr.sdk.version_code = 5900`
  - `pvr.app.type = vr`
  - Pico eye/face/hand tracking related metadata

This is useful for making our on-device app more runtime-friendly on Pico.

### 6. C ABI bridge

`client_openxr/src/c_api.rs` exports a tiny Android-facing entry point:

- `alvr_entry_point(java_vm, context)`

This is useful if we later want:

- a thinner Java/Kotlin shell;
- most XR logic in Rust/native code;
- reusable native core with a small Android wrapper.

## What should not be reused

### 1. Streaming architecture

Do not reuse as a base:

- `client_core`
- `stream.rs`
- sockets / discovery / packet protocol
- decoder / encoder logic
- audio pipeline

Reason:

- our product is a local utility overlay, not a remote PCVR streaming stack.

### 2. SteamVR server / OpenVR driver stack

Do not reuse as a base:

- `server_openvr`
- dashboard / launcher / HTTP API
- SteamVR driver lifecycle logic

Reason:

- this is specific to ALVR's PC streamer model, not to our `PICO` on-device passthrough direction.

### 3. UI and settings framework

Interesting engineering, but low priority for us right now:

- dashboard-generated settings schema
- event transport
- multi-process configuration sync

Good ideas, but not where our current risk sits.

## Recommended reuse priority

### Phase 1

- Study and possibly port the Pico-specific loader strategy from `client_openxr/src/lib.rs`.
- Study and possibly adapt the `XR_FB_passthrough` wrapper from `extra_extensions/passthrough_fb.rs`.
- Reuse the vendor-extension wrapper pattern from `extra_extensions/mod.rs`.

### Phase 2

- Reuse Android manifest / permission / metadata ideas from `client_openxr/Cargo.toml`.
- Consider a thin C ABI / native-core boundary inspired by `c_api.rs`.

### Phase 3

- Borrow graphics/session setup ideas from `client_openxr/src/lib.rs` if we move to a richer on-device renderer.

### Never / almost never

- ALVR networking
- ALVR streaming protocol
- ALVR server/dashboard architecture
- ALVR codec stack as product foundation

## Practical implication for our project

The best way to use `ALVR` is not:

- "fork ALVR and remove what we do not need"

The best way is:

- keep our app architecture small and purpose-built;
- borrow `OpenXR client` techniques;
- borrow `passthrough layer` code paths;
- borrow `vendor extension wrapper` patterns.

## Sources

- `ALVR` repo root: https://github.com/alvr-org/ALVR
- ALVR architecture wiki: https://github.com/alvr-org/ALVR/wiki/How-ALVR-works
- `client_openxr` tree: https://github.com/alvr-org/ALVR/tree/master/alvr/client_openxr
- `passthrough.rs`: https://github.com/alvr-org/ALVR/blob/master/alvr/client_openxr/src/passthrough.rs
- `passthrough_fb.rs`: https://github.com/alvr-org/ALVR/blob/master/alvr/client_openxr/src/extra_extensions/passthrough_fb.rs
- `c_api.rs`: https://github.com/alvr-org/ALVR/blob/master/alvr/client_openxr/src/c_api.rs
- `client_openxr/Cargo.toml`: https://raw.githubusercontent.com/alvr-org/ALVR/master/alvr/client_openxr/Cargo.toml
