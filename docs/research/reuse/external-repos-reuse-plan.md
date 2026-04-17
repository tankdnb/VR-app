# External Repos Reuse Plan

## Purpose

Этот документ фиксирует, что именно можно использовать из внешних VR-проектов для `VR Reality Window MVP`, а что не стоит переносить в текущую кодовую базу.

Главный контекст:

- наш продукт сейчас является `standalone SteamVR/OpenVR companion app`;
- он управляет собственным overlay lifecycle;
- его главный риск сейчас не post-processing, а доступ к реальной внешней камере шлема.

Поэтому внешние репозитории мы рассматриваем не как готовую основу приложения, а как источники:

- архитектурных идей;
- D3D11/OpenXR runtime techniques;
- modular image-processing patterns;
- future-facing code donors.

## Projects Reviewed

- `fholger/openvr_fsr`
- `RavenSystem/VRPerfKit_RSF`
- `CamelCaseName/OpenVRPerfKit`
- `mbucchia/OpenXR-Toolkit`
- `mbucchia/Quad-Views-Foveated`
- `mbucchia/OpenXR-Eye-Trackers`
- `Granther/foveated-rendering`
- `retroluxfilm/reshade-vrtoolkit`
- `zhukovv/upscale-injection`

## Short Summary

Из этих проектов для нас полезны в первую очередь три направления:

1. `Modular frame processing`
2. `Native D3D11 texture pipeline`
3. `OpenXR API-layer architecture`

При этом ни один из изученных проектов не решает автоматически наш текущий blocker:

- они не доказывают, что `Quest/Pico` отдадут внешний camera feed через `OpenVR tracked camera API`.

## What We Already Reused

В текущий MVP уже встроена одна практическая идея, общая для `openvr_fsr`, `vrperfkit`, `OpenXR-Toolkit` и `reshade-vrtoolkit`:

- добавлен отдельный `FrameProcessingPipeline` между `ICameraProvider` и `OpenVrOverlayPresenter`.

Это зафиксировано в коде:

- [IFrameProcessor.cs](/Users/Username/Documents/VR.app/src/VRRealityWindow.Core/Abstractions/IFrameProcessor.cs)
- [FrameProcessingPipeline.cs](/Users/Username/Documents/VR.app/src/VRRealityWindow.Core/Processing/FrameProcessingPipeline.cs)
- [BottomFocusCropProcessor.cs](/Users/Username/Documents/VR.app/src/VRRealityWindow.Core/Processing/BottomFocusCropProcessor.cs)

Почему это важно:

- мы не тащим hook/injector архитектуру из чужих проектов;
- мы все равно получаем правильную точку расширения для будущих `CAS/FSR/NIS`;
- в этом же слое можно безопасно реализовывать `crop`, `sharpen`, `color adjust`, `masking`.

Первый процессор в этой цепочке:

- `BottomFocusCropProcessor`

Он дает MVP-приближение к `crop down` и концептуально ближе всего к идее из `upscale-injection`:

- обрабатывать и выделять только релевантную часть изображения, а не весь кадр одинаково.

## Best Donors For Current MVP

### 1. `fholger/openvr_fsr`

Полезность:

- самый компактный референс раннего `OpenVR + D3D11 post-process` пути;
- проще изучать, чем большой `vrperfkit`;
- хорошо показывает раннюю архитектуру `PostProcessor`, конфиг и хук-submit path.

Что брать:

- логику `post-process chain`;
- shader integration pattern;
- ideas for config/log/hotkey structure;
- `projection center` math, если позже понадобится lens-aware processing.

Что не брать:

- `openvr_api.dll` proxy model;
- virtual function hooks;
- `MinHook`-based integration path.

Вердикт:

- отличный `reference donor`;
- не база продукта.

### 2. `retroluxfilm/reshade-vrtoolkit`

Полезность:

- хороший референс для `single-pass VR-oriented post-processing`;
- особенно полезен для `clarity/sharpen/color correction` идей.

Что брать:

- композицию нескольких image adjustments в одном проходе;
- приоритизацию clarity over visual noise;
- selective processing around the useful field of view.

Что не брать:

- ReShade-dependent runtime model.

Вердикт:

- полезен как shader-pipeline reference;
- не заменяет наш overlay/runtime stack.

### 3. `zhukovv/upscale-injection`

Полезность:

- полезный low-level reference по `D3D11 compute shader injection`;
- интересен именно как пример "не обрабатывать то, что пользователь не увидит".

Что брать:

- compute-shader mindset для crop/upscale;
- идею экономии на частичном processing region;
- layout shader assets separately from host runtime.

Что не брать:

- `d3d11.dll` injection как продуктовую архитектуру.

Вердикт:

- полезно для будущего GPU crop/upscale path;
- не для текущего OpenVR companion skeleton.

## Best Donors After Moving To Native D3D11

### 4. `RavenSystem/VRPerfKit_RSF`

Полезность:

- практический форк с `HRM`, `dynamic modes`, `RDM`, compatibility toggles;
- полезен после того, как у нас появится нативный texture-based pipeline.

Что брать потом:

- идеи `dynamic radii`;
- `hidden radial mask`;
- runtime heuristics;
- richer config feature blocks.

Что пока не брать:

- всю hook/proxy модель;
- всю compatibility matrix под игры.

Вердикт:

- источник feature ideas для `Phase 2+`.

### 5. `CamelCaseName/OpenVRPerfKit`

Полезность:

- полезен как индикатор дальнейшей эволюции форка `VRPerfKit_RSF`;
- интересен для `D3D12`, новых SDK и более агрессивной эволюции upscalers.

Что брать потом:

- только конкретные rendering techniques, если нам действительно нужен `D3D12` или новый FSR-based path.

Что не брать сейчас:

- производную hook-архитектуру;
- расширение технического долга до того, как подтвержден реальный camera source.

Вердикт:

- смотреть после `VRPerfKit_RSF`, не раньше.

## Best Architectural Donors If We Pivot Toward OpenXR

### 6. `mbucchia/OpenXR-Toolkit`

Это самый сильный архитектурный референс из всего списка.

Что в нем особенно ценно:

- разделение на `API layer + companion app`;
- модульные image processors;
- eye tracker abstraction;
- зрелая config manager модель;
- runtime capability detection;
- graceful bypass when the layer should not act.

Что брать:

- архитектурные паттерны;
- `companion + runtime` split;
- image processor interfaces;
- diagnostics/config refresh patterns.

Что не брать один-в-один:

- весь слой целиком, пока мы еще на стадии `camera access proof`.

Вердикт:

- лучший референс, если MVP уйдет от `pure OpenVR companion` к `OpenXR-first architecture`.

### 7. `mbucchia/Quad-Views-Foveated`

Полезность:

- очень хороший reference по `OpenXR API layer routing`;
- аккуратно показывает, как обрабатывать advertised/blocked/implicit extensions;
- полезен для device/runtime-specific gating.

Что брать:

- extension mediation pattern;
- view configuration handling;
- bypass rules;
- composition-device/application-device split.

Вердикт:

- не нужен для первого OpenVR spike;
- очень полезен, если появится OpenXR path.

### 8. `mbucchia/OpenXR-Eye-Trackers`

Полезность:

- чистая reference implementation для `provider abstraction` поверх разных eye-tracker backends;
- показывает, как делать runtime-dependent fallback selection.

Что брать:

- provider selection logic;
- device-specific fallback chains;
- capability-driven enablement.

Вердикт:

- не про камеру;
- очень полезен как шаблон для будущего `CameraProvider` family, если мы пойдем в vendor-specific paths.

## Experimental Reference Only

### 9. `Granther/foveated-rendering`

Полезность:

- смотреть как экспериментальную ветку идей по dynamic/eye-tracked adaptation.

Вердикт:

- не базовый донор;
- только как secondary research material.

## What We Should Not Reuse As Product Architecture

- `DLL proxy` рядом с игрой
- `dxgi.dll`, `d3d11.dll`, `openvr_api.dll` hijack strategy
- `MinHook` as the basis of the product
- `IVRCompositor::Submit` interception model
- game-specific compatibility hacks as a core requirement

Причина простая:

- мы строим `utility companion app`, а не мод для игр.

## Practical Decision For Our Project

На сегодня лучший practical path такой:

1. Сохранять текущий `OpenVR companion` путь для `camera probe` и базового overlay.
2. Развивать `FrameProcessingPipeline` как единый слой обработки кадра.
3. Следующим техническим шагом делать `native D3D11 texture path`.
4. После этого портировать в pipeline `CAS` как первый реальный GPU processor.
5. Только затем оценивать `FSR/NIS`, `HRM/RDM`, dynamic modes.
6. Если `OpenVR tracked camera` так и не появится на целевых шлемах, рассматривать `vendor-specific camera path` или pivot к `OpenXR-first architecture`.

## Recommended Next Implementation Step

Самый разумный следующий шаг после текущего обновления:

- добавить в MVP `TextureBackedFrameProcessor` / `D3D11` path и подготовить место для первого `CAS` processor.

Это даст нам сразу три вещи:

- понятную точку интеграции кода из `openvr_fsr` / `vrperfkit`;
- честную почву для quality/performance comparison;
- базу для перехода от CPU processing к production-grade GPU pipeline.
