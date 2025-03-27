[🇷🇺 Русский](../ru/architecture.md) | [🇺🇸 English](../en/architecture.md)

# 🧱 Архитектура Campaign Manager

## Основные блоки:
- API Gateway (Spring Boot)
- Temporal Workflow Engine
- Segment Service
- Delivery Service
- Analytics

## Интеграции:
- Firebase / SMS API
- PostgreSQL / Kafka
- BI / ClickHouse

_Этот документ доступен также на [English](../en/architecture.md)_

---

## ⚙️ Настройка кампании

Каждая кампания содержит конфигурацию, определяющую поведение:

| Параметр | Описание |
|----------|----------|
| `segmentId` | Целевой сегмент |
| `startTime` / `endTime` | Временной диапазон активности кампании |
| `repeatInterval` | Периодичность повторов (например, ежедневно) |
| `timeWindowStart` / `timeWindowEnd` | Разрешённое время отправки |
| `maxMessagesPerUser` | Лимит сообщений на пользователя |
| `channel` | Канал (Push, SMS и т.д.) |
| `templateId` | Шаблон сообщения |
| `contactPolicyId` | Правила контактной политики |
| `priority` | Приоритет кампании |
| `abGroup` | Настройка A/B-тестирования (опц.) |

Temporal Workflow использует эти параметры для:
- Повторов (`repeatInterval`)
- Проверки временного окна (`timeWindow`)
- Контроль количества сообщений (`maxMessagesPerUser`)
- Выбора канала и шаблона

Настройка конфигурации позволяет гибко управлять поведением кампании без изменения кода.
