# commit-rules

**Скилл для AI-агентов: единые Git-коммиты и описания pull request.**

[English](README.md) · [Инструкции скилла](SKILL.md) · [Conventional Commits 1.0.0](https://www.conventionalcommits.org/en/v1.0.0/)

![Git](https://img.shields.io/badge/Focus-Git-F05032?logo=git&logoColor=white) ![AI agents](https://img.shields.io/badge/AI-agent%20skill-374151)

## Назначение

`commit-rules` помогает AI-агентам составлять **англоязычные сообщения коммитов** и **описания PR** на основании реальных изменений репозитория. Для работы нужен только `SKILL.md`, зависимости приложения не требуются.

Агент изучает ветку, статус, изменения и последние коммиты. **Без явного запроса он не добавляет файлы в индекс и не создаёт коммиты.**

## Возможности

| Функция | Поведение |
| --- | --- |
| **Conventional Commits** | Выбирает `type` и `scope` по изменениям |
| **Точность** | Приоритет изменений в индексе; имя ветки — только подсказка |
| **Краткое описание** | Тело сообщения в виде коротких пунктов |
| **Несовместимые изменения** | Поддержка `!` и `BREAKING CHANGE:` |
| **Действия после релиза** | Примечания `Note:` при необходимости |
| **Pull requests** | Разделы Summary, Testing и Notes |
| **Контроль** | Нет автоматических коммитов или указания ИИ как соавтора |

## Установка

Скопируйте [SKILL.md](SKILL.md) в каталог скиллов вашего агента:

```text
<agent-skills-directory>/commit-rules/SKILL.md
```

Если агент не поддерживает скиллы, перенесите инструкции в соответствующий конфигурационный файл проекта.

## Использование

Попросите агента:

```text
Write a commit message for the current changes.
Write a pull request description for this branch.
```

Пример результата:

```text
feat(api): add task filtering

- add status filters to task search
- validate filter inputs to reject unsupported values
- cover filtering behavior with tests
```

Агент должен описывать фактические изменения, не придумывая детали реализации или результаты тестирования. Все ограничения указаны в [SKILL.md](SKILL.md).

## Структура

```text
SKILL.md      Инструкции для агента
README.md     Английская версия
README.ru.md  Русская версия
```

## Связанные проекты

- [ub-mode-php](https://github.com/Yatseck-k/ub-mode-php) — независимый скилл для работы с PHP-кодом.
- [ub-cdmu-php](https://github.com/Yatseck-k/ub-cdmu-php) — необязательный CLI-анализатор качества PHP.

`commit-rules` не зависит от этих проектов.
