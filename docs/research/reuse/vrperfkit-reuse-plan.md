# vrperfkit Reuse Plan

## Purpose

Этот документ фиксирует, какие части `vrperfkit` стоит использовать в `VR Reality Window MVP`, а какие не подходят из-за другой архитектуры проекта.

Источник анализа: локальный клон `vrperfkit` в `C:\Users\Username\Documents\VR.app\.tmp\vrperfkit`.

## Short Summary

`vrperfkit` полезен нам как donor-репозиторий для:

- `D3D11` post-processing;
- upscaling and sharpening;
- части OpenVR math;
- утилит для работы с GPU resources.

`vrperfkit` не подходит как основа приложения, потому что он сделан как:

- `DLL proxy`;
- `hook/injector` в чужой процесс;
- модификатор submit path уже существующей VR-игры.

Наше приложение другое:

- standalone companion app;
- свой overlay lifecycle;
- свой camera provider;
- не встраивается в игру и не перехватывает `IVRCompositor::Submit`.

## Phase 1

Использовать только после перехода нашего overlay runtime с `SetOverlayRaw` на `D3D11 texture` pipeline.

### 1. D3D11 helper layer

Файлы:

- [d3d11_helper.h](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_helper.h)
- [d3d11_helper.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_helper.cpp)

Что взять:

- создание `ShaderResourceView`;
- создание `UnorderedAccessView`;
- создание `resolve texture`;
- создание `post-process texture`;
- `StoreD3D11State` / `RestoreD3D11State`.

Почему это полезно:

- если камера начнет приходить как `D3D11 texture` или мы сами перейдем на `TextureType_DirectX`, нам нужен аккуратный GPU-side post-process pipeline;
- state save/restore особенно полезен, если начнем делать compute/pixel shader pass перед отправкой texture в overlay.

Как использовать у нас:

- создать модуль `VRRealityWindow.D3D11`;
- завернуть helper-функции в наш `OverlayTextureProcessor`;
- не переносить MinHook/injector зависимости.

### 2. CAS / FSR / NIS upscalers

Файлы:

- [d3d11_post_processor.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_post_processor.cpp)
- [d3d11_post_processor.h](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_post_processor.h)
- [d3d11_cas_upscaler.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_cas_upscaler.cpp)
- [d3d11_fsr_upscaler.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_fsr_upscaler.cpp)
- [d3d11_nis_upscaler.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_nis_upscaler.cpp)
- [cas.sharpen.hlsl](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/cas/cas.sharpen.hlsl)
- [fsr_easu.hlsl](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/fsr/fsr_easu.hlsl)
- [NIS_Upscale.hlsl](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/nis/NIS_Upscale.hlsl)

Что взять:

- саму идею модульного post-process chain;
- `CAS` как самый вероятный первый кандидат;
- позже `FSR/NIS` для масштабирования feed при lower internal resolution.

Почему это полезно:

- наш camera feed, скорее всего, не всегда будет идеального разрешения;
- sharpening и upscale могут сильно улучшить читаемость клавиатуры, телефона и мелких объектов в overlay;
- это один из немногих реально ценных performance/quality апгрейдов для продукта.

Рекомендация:

- первым портировать `CAS`, потому что он проще и полезен даже без upscale;
- `FSR/NIS` включать только когда у нас появится texture-based renderer и понятная метрика качества.

### 3. GPU profiling pattern

Файл:

- [d3d11_post_processor.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_post_processor.cpp)

Что взять:

- timestamp/disjoint query pattern для оценки GPU стоимости пост-обработки.

Почему это полезно:

- у нас продукт performance-sensitive;
- нам нужен честный ответ, сколько стоит sharpening/upscale до отправки overlay.

Как использовать у нас:

- встроить как debug-only instrumentation;
- не переносить весь `debugMode` как есть, а адаптировать под наши diagnostics.

## Phase 2

Полезно, но не для первого технического доказательства.

### 4. OpenVR projection center math

Файл:

- [openvr_manager.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/openvr/openvr_manager.cpp)

Что взять:

- `CalculateProjectionCenters`;
- использование `GetProjectionRaw`;
- поправку на canted displays.

Почему это полезно:

- если мы захотим сделать lens-aware crop;
- если появится radial blur/mask/sharpen;
- если захотим более умную обработку под разные headset optics.

Почему не сейчас:

- наш текущий MVP рендерит простое окно в реальность;
- сейчас нам сначала нужно доказать доступ к real camera feed, а не идеальную optical correctness.

### 5. Resolution scaling heuristics

Файл:

- [resolution_scaling.h](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/resolution_scaling.h)

Что взять:

- простую логику расчета `input/output resolution`;
- выравнивание размеров до четных значений.

Почему это полезно:

- если мы добавим internal processing resolution;
- это поможет избежать лишних артефактов в upscaler/shader path.

### 6. Config design ideas

Файлы:

- [config.h](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/config.h)
- [config.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/config.cpp)

Что взять:

- группировку настроек по feature blocks;
- parse/validate/defaults pattern;
- печать активной конфигурации в лог.

Почему это полезно:

- у нас уже есть JSON settings, но когда добавятся post-process фичи, удобно будет держать их отдельным блоком:
  - `postprocess`
  - `sharpening`
  - `upscaling`
  - `quality`

### 7. Output capture for diagnostics

Файл:

- [d3d11_post_processor.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_post_processor.cpp)

Что взять:

- идею сохранения промежуточного или итогового output texture.

Почему это полезно:

- это очень поможет при дебаге качества camera feed;
- удобно сравнивать raw frame, cropped frame, sharpened frame.

## Never

Эти части не стоит переносить в наш проект как основу.

### 8. OpenVR submit hooks

Файлы:

- [openvr_hooks.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/openvr/openvr_hooks.cpp)
- [openvr_hooks.h](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/openvr/openvr_hooks.h)

Почему не брать:

- они хукают `IVRCompositor::Submit`, `WaitGetPoses`, `VRClientCoreFactory`;
- это нужно для модификации чужой игры изнутри;
- нам не нужно вмешиваться в render path игры, чтобы показать собственный overlay.

Риск:

- сильно усложняет поддержку;
- добавляет хрупкость по версиям интерфейсов OpenVR;
- создает лишние точки отказа.

### 9. Proxy DLL architecture

Файлы:

- [proxy/openvr.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/proxy/openvr.cpp)
- [proxy/dxgi.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/proxy/dxgi.cpp)
- [proxy/d3d11.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/proxy/d3d11.cpp)
- [dllmain.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/dllmain.cpp)

Почему не брать:

- это вся модель "подсунуть DLL рядом с игрой";
- она не соответствует нашему продукту;
- companion app должен жить как отдельный процесс с явным lifecycle.

### 10. Generic hook framework

Файлы:

- [hooks.h](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/hooks.h)
- [hooks.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/hooks.cpp)

Почему не брать:

- MinHook нам не нужен для текущего продукта;
- если мы идем в standalone overlay app, hook-based integration только увеличит технический долг.

### 11. Oculus-specific injection path

Файлы:

- [oculus_hooks.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/oculus/oculus_hooks.cpp)
- [oculus_manager.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/oculus/oculus_manager.cpp)

Почему не брать:

- это другая runtime-стратегия;
- она не приближает нас к показу tracked camera feed в OpenVR overlay.

### 12. DXVK / Vulkan patch path

Файлы:

- [openvr_manager.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/openvr/openvr_manager.cpp)

Почему не брать сейчас:

- это сложная совместимость ради перехвата чужих game textures;
- для MVP overlay app это просто не по критическому пути.

## Optional Later

### 13. NVIDIA Variable Rate Shading

Файлы:

- [d3d11_variable_rate_shading.cpp](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_variable_rate_shading.cpp)
- [d3d11_variable_rate_shading.h](C:/Users/Username/Documents/VR.app/.tmp/vrperfkit/src/d3d11/d3d11_variable_rate_shading.h)

Статус:

- не `Phase 1`;
- не `Never`;
- только как дальняя опция.

Почему:

- NVIDIA-only;
- завязано на `NVAPI`;
- польза выше для тяжелого stereo render path, чем для нашего небольшого overlay;
- может стать полезным только если overlay эволюционирует в более дорогую real-time post-process поверхность.

## Recommended Integration Order

1. Не переносить ничего из hook/proxy архитектуры.
2. Сначала закончить наш standalone `camera probe + texture overlay` путь.
3. Когда появится нативный `D3D11 texture` path, портировать:
   - `d3d11_helper`
   - `CAS`
   - GPU profiling queries
4. После этого, если будет реальная польза:
   - `FSR/NIS`
   - projection center math
   - output capture

## Final Recommendation

Из `vrperfkit` стоит использовать:

- идеи;
- шейдеры;
- D3D11 helper code;
- post-process architecture.

Из `vrperfkit` не стоит использовать:

- способ встраивания;
- hook/proxy runtime;
- всю модель "мод для игры".

Если коротко:

- `reuse selected rendering tech`
- `do not reuse product architecture`
