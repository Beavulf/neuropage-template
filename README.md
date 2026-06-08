# NeuroPage Template

> Шаблон для генерации лендингов через Cursor AI + NeuroPage Pipeline

## Как использовать

1. **Pipeline (n8n + Notion)** генерирует файлы в папке `data/`
2. Клонируешь этот репозиторий под каждый новый проект
3. Кладёшь сгенерированные файлы в `data/`
4. Открываешь Cursor, вставляешь содержимое `starter-prompts/01-orchestrator.md` с указанием пути к `data/project-brief.json`
5. Cursor проходит все 10 фаз и генерирует готовый проект

## Структура

```
neuropage-template/
├── README.md
├── starter-prompts/          # 10 промптов для Cursor
│   ├── 01-orchestrator.md    # Главный оркестратор (запускать первым)
│   ├── 02-intake-analyst.md
│   ├── 03-clarifier.md
│   ├── 04-bootstrap.md
│   ├── 05-architect-roadmap.md
│   ├── 06-implementer.md
│   ├── 07-reviewer.md
│   ├── 08-tester.md
│   ├── 09-ui-engineer.md
│   └── 10-handover.md
├── data/                     # Сюда кладёшь файлы из Pipeline
│   ├── project-brief.json    # ← Главный файл (читает Orchestrator)
│   ├── site.json
│   ├── theme.json
│   ├── sections.json
│   └── final-copy.json
├── docs/                     # Авто-документация (заполняется агентами)
│   ├── ARCHITECTURE.md
│   └── DECISIONS.md
└── .cursor/
    └── rules/                # Правила для Cursor (создаёт 04-bootstrap)
```

## data/ — Схема файлов

См. `data/project-brief.schema.json` для полной JSON-схемы.

## Порядок запуска промптов

| Фаза | Промпт | Что делает |
|------|--------|------------|
| Phase 0 | 01 → 02 → 03 → 04 | Инициализация, анализ, уточнение, бутстрап |
| Phase 1 | 05 | Архитектура и роадмап |
| Phase 2 | 06 → 07 → 08 → 09 | Разработка, ревью, тесты, UI |
| Phase 3 | 10 | Передача клиенту |
