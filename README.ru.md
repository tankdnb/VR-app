# VR-apps-lab

[English](README.md) | Русский

`VR-apps-lab` - это не просто одна VR-программа.

Это публичный `репозиторий знаний`, `база наработок`, и `концентрат готовых
подходов` для разработки VR-утилит, overlay-приложений, инструментов,
диагностических средств, tracking helper-ов и экспериментальных XR-интеграций.

Проект начался как `Reality Window` MVP, но в процессе вырос в гораздо более
ценную вещь: не в один продукт, а в систематизированную базу знаний и рабочих
прототипов для будущих VR-инструментов.

## Что это за репозиторий

`VR-apps-lab` объединяет три слоя:

1. `Репозиторий знаний`
   - исследования GitHub-проектов, связанных с VR
   - выделенные методы и паттерны реализации
   - семейства похожих решений и overlap-анализ
   - backlog дальнейшего исследования

2. `Рабочая техническая база`
   - кодовые прототипы `OpenVR` overlay
   - reusable abstractions и экспериментальные модули
   - вспомогательные research-скрипты

3. `Архив экспериментов`
   - passthrough и camera-исследования
   - hardware-specific feasibility notes
   - тупиковые ветки, из которых всё равно были извлечены полезные инженерные
     выводы

## Для кого этот репозиторий

- для разработчиков VR-утилит и инструментов
- для тех, кто хочет быстро находить готовые подходы и архитектурные идеи
- для исследователей, которые хотят изучать public VR ecosystem системно
- для авторов overlay/dashboard/diagnostics/tracker-bridge решений
- для русскоязычных пользователей, которым удобнее заходить в тему через
  структурированную базу на русском

## Что здесь уже есть

- карта и каталог VR-проектов, полезных как reference или code donor
- методы и способы реализации VR utility software
- registry изученных репозиториев
- discovery workflow для поиска новых проектов
- code-level research waves
- рабочие прототипы `OpenVR` и `PICO/OpenXR` experiments

## Что не стоит обещать от этого репозитория

Это не:

- один законченный пользовательский продукт
- универсальное решение для passthrough на всех устройствах
- готовый SDK на все случаи жизни
- гарантия, что любой эксперимент в репозитории production-ready

Правильнее воспринимать `VR-apps-lab` как:

- `knowledge repository` для VR utility development
- `pattern library` по построению VR tools
- `working base` для новых утилит и исследований

## Структура репозитория

```text
src/
  VRRealityWindow.Core/      shared models, providers, processing pipeline
  VRRealityWindow.OpenVr/    OpenVR runtime integration and overlay presenter
  VRRealityWindow.App/       desktop CLI app for doctor/probe/overlay

spikes/
  PicoOpenXrExtensionProbe/  Android OpenXR probe app for PICO runtime testing

scripts/
  research/                  local helper scripts for GitHub research waves

docs/
  README.md                  docs index (EN)
  README.ru.md               docs index (RU)
  foundation/                позиционирование, roadmap, базовые документы
  experiments/               passthrough и feasibility-ветки
  research/                  catalog, methods, families, waves, reuse plans
```

## С чего начать

- [AGENTS.md](AGENTS.md)
- [Русский индекс документации](docs/README.ru.md)
- [Repository positioning](docs/foundation/repository-positioning.md)
- [Current operating context](docs/foundation/current-operating-context.md)
- [Platform foundation](docs/foundation/platform-foundation.md)
- [New session quickstart](docs/research/program/new-session-quickstart.md)
- [New chat prompt block](docs/research/program/new-chat-prompt-block.md)
- [Research operator quick reference](docs/research/program/research-operator-quick-reference.md)
- [Methods catalog](docs/research/methods/vr-utility-methods-catalog.md)
- [Project families](docs/research/landscape/project-families.md)
- [Project registry](docs/research/catalog/project-registry.md)
- [Discovery intake pipeline](docs/research/discovery/intake-pipeline.md)
- [Wave 12 research](docs/research/landscape/vr-projects-wave-12-synthetic-devices-input-emulation-and-diy-driver-paths.md)
- [Wave 13 research](docs/research/landscape/vr-projects-wave-13-vision-tracking-hand-bridges-and-headsetless-camera-runtimes.md)
- [Wave 14 research](docs/research/landscape/vr-projects-wave-14-tracker-ingress-osc-egress-and-role-binding-utilities.md)
- [Wave 15 research](docs/research/landscape/vr-projects-wave-15-overlay-hosts-and-scaffolds.md)
- [Wave 16 research](docs/research/landscape/vr-projects-wave-16-device-monitors-pose-exporters-and-environment-helpers.md)
- [Wave 17 research](docs/research/landscape/vr-projects-wave-17-openxr-runtime-managers-layers-and-service-hosts.md)
- [Wave 18 research](docs/research/landscape/vr-projects-wave-18-driver-learning-paths-and-repurposed-display-bridges.md)
- [Wave 19 research](docs/research/landscape/vr-projects-wave-19-vendor-mods-repurposed-output-bridges-and-alternative-hardware-paths.md)
- [Wave 20 research](docs/research/landscape/vr-projects-wave-20-performance-mods-graphics-injection-and-vr-sweet-spot-shaders.md)
- [Wave 21 research](docs/research/landscape/vr-projects-wave-21-openxr-provider-stacks-gaze-layers-and-runtime-side-utility-platforms.md)
- [Wave 22 research](docs/research/landscape/vr-projects-wave-22-vision-tracking-hosts-camera-full-body-bridges-and-hand-input-sidecars.md)
- [Wave 23 research](docs/research/landscape/vr-projects-wave-23-glove-platforms-poser-stacks-and-nonstandard-hardware-bridge-drivers.md)

## Главная идея репозитория

Не хранить просто список ссылок, а собирать:

- изученные методы и подходы
- сильные product patterns
- архитектурные решения
- reusable implementation ideas
- структурированный backlog дальнейшего изучения

Если коротко: `VR-apps-lab` - это публичная база знаний и рабочих наработок для
создания VR-приложений, утилит и инструментов.

## Как здесь проверяются изменения

`VR-apps-lab` не сопровождается как один shipping-продукт.

Для `research`- и `documentation`-изменений главные критерии качества такие:

- структура репозитория остаётся целостной;
- ссылки и навигация не ломаются;
- registry, families, methods и backlog остаются согласованными;
- описание проекта честно отражает границы реальной поддержки.

Для изменений в `prototype`-коде и runnable-инструментах проверка может
дополнительно включать build-check, smoke test и runtime notes для затронутого
модуля.
