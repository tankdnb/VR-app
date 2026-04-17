# VR Reality Window Overlay MVP Spec

## Document Status

- Version: `0.1`
- Status: `Draft for implementation spike`
- Updated: `2026-04-09`
- Scope: `MVP`

## 1. Product Summary

### 1.1 Working Definition

Приложение представляет собой `SteamVR/OpenVR companion app`, которое добавляет в VR `Reality Window`:

- always-on-top overlay с изображением с внешней камеры HMD;
- окно появляется перед пользователем;
- окно может быть закреплено в мире или на руке;
- управление выполняется контроллерами через постоянный hand-attached control panel;
- настройки и пресеты сохраняются в профили.

### 1.2 Core Value

Продукт не заменяет полноценный passthrough и не пытается показать весь реальный мир. MVP решает более узкую задачу:

- быстро показать нужный фрагмент реального мира;
- не ломать immersion VR-сцены;
- работать предсказуемо и с низкой стоимостью по производительности;
- управляться без снятия шлема и без выхода из текущего VR-сценария.

### 1.3 Primary Use Cases

- посмотреть на стол, клавиатуру, телефон, кружку;
- быстро свериться с физическим окружением без full passthrough;
- закрепить окно в удобной зоне и использовать как утилитарный инструмент;
- вызвать окно на удержание через temporary peek.

## 2. Product Goals and Non-Goals

### 2.1 MVP Goals

- показать видеопоток в OpenVR overlay;
- поддержать `WorldLocked` и `HandLocked` режимы;
- обеспечить controller-first UX;
- дать быстрый доступ к базовым параметрам окна;
- сохранить/загрузить профили и пресеты;
- корректно переживать отсутствие или потерю источника камеры.

### 2.2 Non-Goals for MVP

- hand tracking как основной способ управления;
- desk detection, object detection, segmentation;
- depth-aware compositing;
- stereo reconstruction;
- alignment реального пространства с виртуальной сценой;
- сложные shader effects поверх видео.

## 3. UX Model

### 3.1 Core Flow

1. Пользователь вызывает приложение комбинацией на контроллере.
2. Перед пользователем появляется `Reality Window`.
3. На служебной руке отображается `Control Panel`.
4. Пользователь меняет положение окна, размер, прозрачность, crop и tilt.
5. Пользователь закрепляет окно в мире или на руке.
6. При необходимости сохраняет настройки в preset/profile.
7. Для быстрых проверок использует `Temporary Peek`: удержание показывает окно, отпускание скрывает.

### 3.2 UX Principles

- Окно должно вести себя как утилитарный инструмент, а не как debug-view.
- Все критичные действия должны требовать минимального числа нажатий.
- Базовый сценарий не должен зависеть от desktop UI.
- Input chaos должен быть ограничен: глобальных действий мало, остальное уходит в hand panel.
- При потере камеры пользователь должен увидеть понятный статус, а не "сломанное" окно.

### 3.3 UX Defaults

- окно спавнится чуть ниже центра взгляда;
- окно появляется на комфортной дистанции;
- control panel закреплен на отдельной служебной руке;
- panel всегда повернут лицом к HMD;
- temporary peek показывает окно в последней известной позе, если она валидна.

## 4. Functional Scope

### 4.1 Must-Have

- OpenVR overlay для окна реальности;
- отдельный overlay для hand control panel;
- привязка к контроллерам;
- настраиваемые bindings;
- spawn/reset перед пользователем;
- `WorldLocked` / `HandLocked`;
- opacity;
- crop вниз;
- tilt;
- scale;
- save/load preset;
- temporary peek;
- source abstraction;
- обработка `SourceUnavailable`.

### 4.2 Should-Have

- desktop hotkey;
- restore last session;
- fallback test source;
- headset-specific overrides в профиле;
- source diagnostics screen для spike/debug mode.

### 4.3 Not in MVP

- hand tracking;
- gesture-driven UI;
- environment understanding;
- semantic cropping;
- multi-window reality composition.

## 5. System Architecture

MVP строится из 6 модулей с жестким разделением ответственности.

### 5.1 Overlay Core

Отвечает за:

- регистрацию и lifecycle overlay в OpenVR;
- создание `Reality Window Overlay`;
- создание `Control Panel Overlay`;
- visibility и z-order;
- transform и обновление размеров;
- привязку к world space или device space;
- подачу текстуры в overlay.

Ключевые требования:

- быстрый show/hide без полного пересоздания;
- отдельные идентификаторы и lifecycle для window/panel;
- возможность обновлять transform независимо от видеоисточника.

### 5.2 Camera Provider Layer

Единый интерфейс доступа к видеопотоку.

Поддерживаемые реализации:

- `OpenVRTrackedCameraProvider`
- `ExternalCameraProvider`

Планируемые расширения:

- `MetaProvider`
- `PicoProvider`

Ключевой принцип:

- overlay subsystem не знает, откуда пришел кадр;
- provider subsystem не знает, как кадр показывается пользователю.

### 5.3 Reality Window Controller

Прикладная логика окна:

- текущий transform;
- anchor mode;
- opacity;
- crop;
- tilt;
- временная видимость;
- reset/spawn rules;
- state transitions для редактирования.

### 5.4 Hand Control Panel

Постоянный world-space control surface:

- toggle visibility;
- source status;
- anchor switch;
- opacity/crop/scale/tilt;
- save/load preset;
- reset pose;
- bindings editor entry;
- debug/status view.

### 5.5 Input Mapping System

Отвечает за:

- глобальные действия;
- chord, hold, long press;
- conflict resolution;
- routing input между panel и window edit mode;
- binding profiles и сохранение настроек.

### 5.6 Profile and Config System

Отвечает за:

- глобальные настройки приложения;
- input bindings;
- preset profiles;
- per-headset overrides;
- last session restore.

## 6. Module Interfaces

Ниже приведены рекомендуемые контракты на уровне приложения. Сигнатуры намеренно language-agnostic.

### 6.1 Camera Provider Interface

```text
interface ICameraProvider {
  Result Initialize(CameraProviderConfig config);
  bool IsAvailable();
  Result Start();
  Result Stop();
  FrameResult GetFrame();
  Size2D GetFrameSize();
  Timestamp GetTimestamp();
  CameraStatus GetStatus();
  ProviderDiagnostics GetDiagnostics();
  void Shutdown();
}
```

`CameraStatus`:

- `Uninitialized`
- `Ready`
- `Streaming`
- `Unavailable`
- `Error`

`FrameResult`:

- `success`
- `pixel_format`
- `buffer_handle | raw_buffer`
- `width`
- `height`
- `timestamp`

### 6.2 Overlay Core Interface

```text
interface IOverlayService {
  Result Initialize(OverlayConfig config);
  OverlayHandle CreateOverlay(OverlayDescriptor descriptor);
  Result ShowOverlay(OverlayHandle handle);
  Result HideOverlay(OverlayHandle handle);
  Result SetOverlayTexture(OverlayHandle handle, TextureRef texture);
  Result SetOverlayTransformAbsolute(OverlayHandle handle, Pose pose);
  Result SetOverlayTransformTrackedDevice(
    OverlayHandle handle,
    DeviceId device,
    Pose localPose
  );
  Result SetOverlayWidth(OverlayHandle handle, float meters);
  Result SetOverlayOpacity(OverlayHandle handle, float alpha);
  Result DestroyOverlay(OverlayHandle handle);
  void Shutdown();
}
```

### 6.3 Reality Window Controller Interface

```text
interface IRealityWindowController {
  Result Initialize(WindowProfile profile);
  Result Show(VisibilityMode mode);
  Result Hide();
  Result Toggle();
  Result ResetPoseFromHmd();
  Result SetAnchorMode(AnchorMode mode);
  Result SetTransform(Pose pose, float scale);
  Result AdjustOpacity(float delta);
  Result AdjustCropY(float delta);
  Result AdjustTilt(float deltaDegrees);
  WindowStateSnapshot GetState();
  Result ApplyPreset(string presetId);
  Result SavePreset(string presetId);
}
```

### 6.4 Input Mapping Interface

```text
interface IInputRouter {
  Result Initialize(InputConfig config);
  Result RegisterAction(ActionDescriptor action);
  Result Rebind(ActionId actionId, Binding binding);
  InputFrame Poll();
  RoutedActions Resolve(InputFrame frame, AppState state);
  BindingValidationResult Validate(InputConfig config);
}
```

### 6.5 Profile Store Interface

```text
interface IProfileStore {
  Result LoadAppConfig();
  Result SaveAppConfig(AppConfig config);
  Result LoadProfile(string profileId);
  Result SaveProfile(WindowProfile profile);
  Result DeleteProfile(string profileId);
  Result LoadLastSession();
  Result SaveLastSession(SessionSnapshot session);
}
```

## 7. Runtime State Model

### 7.1 Global App States

- `Idle`
- `WindowVisible`
- `PeekActive`
- `EditingWindow`
- `PanelFocused`
- `SourceUnavailable`

### 7.2 Window Substates

`VisibilityMode`

- `Hidden`
- `Shown`
- `PeekShown`

`AnchorMode`

- `WorldLocked`
- `HandLocked`

`InteractionMode`

- `Passive`
- `Move`
- `Rotate`
- `Scale`
- `Crop`
- `Tilt`

### 7.3 Control Panel States

- `Hidden`
- `Visible`
- `Focused`

### 7.4 Source States

- `NotInitialized`
- `Available`
- `Streaming`
- `Unavailable`
- `Recovering`
- `Error`

### 7.5 Transition Rules

- `Idle -> WindowVisible` при глобальном toggle.
- `WindowVisible -> Idle` при повторном toggle.
- `Idle -> PeekActive` при удержании peek binding.
- `PeekActive -> Idle` при отпускании peek binding.
- `WindowVisible -> EditingWindow` при выборе edit mode.
- `EditingWindow -> WindowVisible` при подтверждении или отмене.
- `PanelVisible -> PanelFocused` при наведении/активации panel input.
- `Any -> SourceUnavailable` если provider перестал отдавать usable frame.
- `SourceUnavailable -> Idle` после восстановления, если до ошибки окно было скрыто.
- `SourceUnavailable -> WindowVisible` после восстановления, если до ошибки окно было видно.

### 7.6 State Handling Notes

- `PeekActive` не должен переписывать сохраненный persistent visibility state.
- `SourceUnavailable` не должен терять профиль или transform окна.
- В `EditingWindow` panel input имеет приоритет над глобальными toggle, кроме аварийного hide.

## 8. Overlay and Pose Behavior

### 8.1 Spawn Algorithm

При первом показе или reset:

1. Считать текущий HMD pose.
2. Взять forward vector HMD.
3. Вычислить spawn point на `spawn_distance`.
4. Добавить вертикальный offset `spawn_offset_vertical`, по умолчанию ниже центра взгляда.
5. Ориентировать окно к пользователю.
6. Применить `spawn_yaw_lock_to_view`.

### 8.2 Recommended Defaults

- `spawn_distance = 0.55m`
- `spawn_offset_vertical = -0.12m`
- `spawn_yaw_lock_to_view = true`
- `default_scale = 0.35m`
- `default_opacity = 0.9`
- `default_tilt = 18deg`

### 8.3 Hand-Locked Behavior

- окно привязывается к выбранной руке;
- local pose задается смещением от controller/hand anchor;
- при `HandLocked` окно может иметь независимую ориентацию или режим `face_hmd`;
- для MVP по умолчанию окно сохраняет local tilt и yaw offset.

### 8.4 Panel Placement Behavior

- panel привязан к служебной руке;
- panel всегда ориентирован лицом к HMD;
- panel position сглаживается, чтобы не дрожал при небольших движениях руки;
- panel может быть временно скрыт без скрытия самого window overlay.

## 9. Input Model

### 9.1 Global Actions

- `toggle_window`
- `temporary_peek`
- `toggle_panel`
- `reset_window_pose`
- `switch_anchor_mode`

### 9.2 Edit Actions

- `move_window`
- `rotate_window`
- `scale_window`
- `adjust_tilt`
- `adjust_crop_y`
- `adjust_opacity`

### 9.3 Supported Binding Types

- `single_press`
- `double_press`
- `long_press`
- `hold`
- `two_button_chord`

### 9.4 Input Constraints

Для MVP ограничить набор глобальных действий:

- один toggle биндинг;
- один peek биндинг;
- один panel биндинг;
- один reset биндинг;
- один quick anchor switch.

Остальная настройка выполняется через panel.

### 9.5 Conflict Resolution

- если panel в фокусе, panel input выигрывает у edit action;
- `temporary_peek` имеет высокий приоритет и всегда может показать окно;
- `hide_window` должен быть доступен как safe exit;
- при конфликте одного и того же chord с разными действиями конфигурация считается невалидной.

## 10. Control Panel Specification

### 10.1 Required Controls

- window on/off;
- source status;
- anchor mode toggle;
- opacity slider;
- crop Y control;
- scale control;
- tilt control;
- reset pose;
- save preset;
- load preset;
- bindings settings entry;
- diagnostics entry.

### 10.2 Layout Rules

- крупные hit targets;
- минимальное число уровней навигации;
- критичные действия на первом экране;
- diagnostics и bindings можно увести на второй экран panel UI;
- текст должен быть читаемым в standing and seated scenarios.

### 10.3 Source Status States

- `Ready`
- `Streaming`
- `Unavailable`
- `Recovering`
- `Error`

UI должен отображать:

- текущий статус;
- название активного source provider;
- при ошибке краткое понятное сообщение;
- при debug mode дополнительные diagnostics.

## 11. Profiles and Configuration

### 11.1 Config Layers

`AppConfig`

- startup behavior;
- theme;
- language;
- debug flags;
- default spawn behavior;
- desktop hotkey;
- performance mode flags.

`InputConfig`

- bindings;
- thresholds;
- debounce;
- long press timing;
- repeat behavior.

`WindowProfile`

- transform;
- opacity;
- crop;
- tilt;
- anchor mode;
- panel behavior;
- source preference;
- spawn parameters.

`SessionSnapshot`

- last active profile;
- last source;
- last visibility state;
- last panel state.

### 11.2 JSON Shape

```json
{
  "app": {
    "startup_behavior": "manual",
    "language": "ru",
    "debug_mode": false,
    "desktop_hotkey": "Ctrl+Alt+R",
    "performance": {
      "target_fps": 60,
      "prefer_shared_texture": true,
      "enable_frame_throttle": true
    },
    "spawn_defaults": {
      "distance_m": 0.55,
      "offset_vertical_m": -0.12,
      "yaw_lock_to_view": true
    }
  },
  "input": {
    "long_press_ms": 350,
    "double_press_ms": 250,
    "debounce_ms": 40,
    "bindings": {
      "toggle_window": {
        "type": "two_button_chord",
        "hand": "right",
        "buttons": ["grip", "trigger"]
      },
      "temporary_peek": {
        "type": "hold",
        "hand": "left",
        "buttons": ["grip"]
      },
      "toggle_panel": {
        "type": "single_press",
        "hand": "left",
        "buttons": ["menu"]
      },
      "reset_window_pose": {
        "type": "long_press",
        "hand": "right",
        "buttons": ["menu"]
      },
      "switch_anchor_mode": {
        "type": "double_press",
        "hand": "right",
        "buttons": ["menu"]
      }
    }
  },
  "profiles": [
    {
      "id": "desk",
      "name": "Desk",
      "source_preference": "openvr_tracked_camera",
      "anchor_mode": "WorldLocked",
      "visibility_behavior": {
        "show_panel_with_window": true,
        "auto_hide_timeout_ms": 0
      },
      "window": {
        "position": [0.0, -0.12, -0.55],
        "rotation_euler_deg": [18.0, 0.0, 0.0],
        "scale_m": 0.35,
        "opacity": 0.9,
        "crop_offset_y": 0.2,
        "crop_scale": 1.0,
        "tilt_angle_deg": 18.0
      },
      "panel": {
        "service_hand": "left",
        "face_hmd": true,
        "visible": true
      },
      "headset_overrides": {
        "quest_2": {
          "window": {
            "opacity": 0.85
          }
        }
      }
    }
  ],
  "session": {
    "last_profile_id": "desk",
    "last_source": "openvr_tracked_camera",
    "window_visible": false,
    "panel_visible": true
  }
}
```

### 11.3 Storage Strategy

- формат хранения: `JSON`;
- один основной конфиг приложения;
- отдельная папка профилей или единый profiles block;
- запись на диск только при изменениях или явном save;
- при поврежденном конфиге приложение должно стартовать с defaults и писать warning.

## 12. Error Handling and Recovery

### 12.1 Source Unavailable

При потере источника:

- overlay не уничтожается;
- окно может перейти в placeholder state;
- panel показывает `SourceUnavailable`;
- приложение пытается восстановить stream;
- при успехе возвращается в предыдущее видимое состояние.

### 12.2 Recommended Placeholder

Для MVP по умолчанию:

- вместо черного экрана показывать status placeholder;
- если включен debug mode, показывать provider error code;
- если доступен `fallback_test_source`, разрешить ручное переключение.

### 12.3 Recovery Policy

- короткий авто-retry с backoff;
- после нескольких неудач состояние остается `Unavailable`;
- пользователь может руками инициировать reconnect из panel.

## 13. Performance and Technical Constraints

### 13.1 Performance Targets

- overlay update не должен создавать заметные hitches в SteamVR;
- видеообновление должно быть стабильно даже при скрытом panel;
- show/hide и temporary peek должны ощущаться мгновенно;
- CPU/GPU cost должен быть ограничен настройками quality/performance mode.

### 13.2 MVP Constraints

- desktop OS: `Windows`;
- VR runtime: `SteamVR/OpenVR`;
- controller-first input only;
- один активный reality window в MVP;
- один panel overlay в MVP.

### 13.3 Diagnostics to Capture

- provider availability;
- `HasCamera`;
- frame size;
- pixel format;
- time to first frame;
- stream acquire failures;
- reconnect count;
- overlay update time;
- dropped frames estimate.

## 14. Technical Spike Plan

### 14.1 Spike A: Camera Access Probe

Цель:

- доказать наличие usable camera feed на целевых HMD через SteamVR/OpenVR.

Проверки:

- HMD виден в SteamVR;
- `HasCamera` true/false;
- stream acquisition succeed/fail;
- frame size;
- pixel format;
- usable image buffer;
- частота обновления;
- reconnect stability.

Acceptance criteria:

- утилита печатает детальный статус провайдера;
- удается получить минимум один валидный кадр или достоверный error code;
- есть лог для Quest 2 и Pico 4 Pro как минимум по одному прогону на устройство.

### 14.2 Spike B: Minimal Overlay Renderer

Цель:

- показать texture-backed overlay в OpenVR.

Проверки:

- overlay виден и стабилен;
- show/hide работает без пересоздания;
- opacity влияет на картинку;
- pose и scale управляются программно;
- видео или test texture обновляется стабильно.

Acceptance criteria:

- приложение показывает обновляемую текстуру в world space;
- reset pose спавнит окно перед пользователем;
- frametime impact не выглядит критичным в ручном тесте.

### 14.3 Spike C: Controller UX Prototype

Цель:

- проверить пригодность controller-first UX до полноценной реализации.

Проверки:

- toggle;
- temporary peek;
- panel visibility;
- move/scale/tilt;
- preset save/load;
- reset pose.

Acceptance criteria:

- пользователь может выполнить базовый сценарий без desktop UI;
- временный peek ощущается предсказуемо;
- panel читается и доступен с руки без лишних движений.

## 15. Milestone Roadmap

### 15.1 Milestone 1: Probe Utility

Результат:

- отдельная утилита диагностики камеры;
- лог статусов и параметров;
- первичная матрица совместимости устройств.

### 15.2 Milestone 2: Minimal Runtime Overlay

Результат:

- один overlay;
- один источник текстуры;
- toggle, opacity, reset pose;
- базовый provider abstraction.

### 15.3 Milestone 3: Interaction Layer

Результат:

- input bindings;
- temporary peek;
- hand control panel;
- edit modes.

### 15.4 Milestone 4: Profiles

Результат:

- save/load profile;
- preset switching;
- last session restore;
- binding persistence.

### 15.5 Milestone 5: Stabilization

Результат:

- reconnect and recovery;
- source unavailable UX;
- performance tuning;
- headset-specific overrides.

## 16. Decisions Fixed Now

- Источник видео и overlay layer полностью развязаны.
- MVP строится вокруг utility overlay, а не вокруг full passthrough.
- Совместимость Quest 2 и Pico 4 Pro через SteamVR/OpenVR валидируется до активной разработки UI.
- Controller-first UX считается базовым и обязательным.
- Все будущие "умные" функции проектируются как расширения поверх текущих `crop + tilt + anchor + presets`.

## 17. Open Questions and Default Assumptions

### 17.1 Open Questions

- Какая рука по умолчанию считается сервисной для panel?
- Может ли окно и panel жить на одной и той же руке?
- Нужен ли автозапуск вместе со SteamVR?
- Нужен ли auto-hide окна при длительном бездействии?
- Temporary peek показывает последнюю позу или всегда вызывает reset-spawn?
- Нужен ли fallback source в production MVP или только в debug mode?

### 17.2 Assumptions for MVP Unless Changed

- panel по умолчанию находится на левой руке;
- если окно `HandLocked`, оно по умолчанию находится на правой руке;
- panel и window могут быть на разных руках;
- peek использует последнюю валидную позу окна;
- при отсутствии источника показывается status placeholder, а не черный экран;
- автозапуск со SteamVR не обязателен для первой версии.

## 18. Definition of Done for MVP

MVP считается готовым, если:

- на хотя бы одном поддерживаемом устройстве получен стабильный usable camera feed;
- окно стабильно отображается в OpenVR overlay;
- пользователь может вызвать окно, переместить его, изменить scale/opacity/crop/tilt;
- поддерживаются `WorldLocked` и `HandLocked`;
- работает `Temporary Peek`;
- работает hand-attached control panel;
- профили сохраняются и восстанавливаются;
- при потере источника пользователь получает понятный статус и может восстановить работу без перезапуска приложения.
