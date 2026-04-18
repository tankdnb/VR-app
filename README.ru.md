# VR.app

[English](README.md) | Русский

`VR.app` - это не просто одна VR-программа.

Это публичный `репозиторий знаний`, `база наработок`, и `концентрат готовых
подходов` для разработки VR-утилит, overlay-приложений, инструментов,
диагностических средств, tracking helper-ов и экспериментальных XR-интеграций.

Проект начался как `Reality Window` MVP, но в процессе вырос в гораздо более
ценную вещь: не в один продукт, а в систематизированную базу знаний и рабочих
прототипов для будущих VR-инструментов.

## Что это за репозиторий

`VR.app` объединяет три слоя:

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

Правильнее воспринимать `VR.app` как:

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

- [Русский индекс документации](docs/README.ru.md)
- [Repository positioning](docs/foundation/repository-positioning.md)
- [Platform foundation](docs/foundation/platform-foundation.md)
- [Methods catalog](docs/research/methods/vr-utility-methods-catalog.md)
- [Project families](docs/research/landscape/project-families.md)
- [Project registry](docs/research/catalog/project-registry.md)
- [Discovery intake pipeline](docs/research/discovery/intake-pipeline.md)

## Главная идея репозитория

Не хранить просто список ссылок, а собирать:

- изученные методы и подходы
- сильные product patterns
- архитектурные решения
- reusable implementation ideas
- структурированный backlog дальнейшего изучения

Если коротко: `VR.app` - это публичная база знаний и рабочих наработок для
создания VR-приложений, утилит и инструментов.
