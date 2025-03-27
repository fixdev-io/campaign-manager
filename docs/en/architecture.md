[🇷🇺 Русский](../ru/architecture.md) | [🇺🇸 English](../en/architecture.md)

# 🧱 Campaign Manager Architecture

## Key components:
- API Gateway (Spring Boot)
- Temporal Workflow Engine
- Segment Service
- Delivery Service
- Analytics

## Integrations:
- Firebase / SMS API
- PostgreSQL / Kafka
- BI / ClickHouse

_This document is also available in [Русский](../ru/architecture.md)_

---

## ⚙️ Campaign Configuration

Each campaign includes a config that defines its behavior:

| Parameter | Description |
|----------|-------------|
| `segmentId` | Target user segment |
| `startTime` / `endTime` | Active time range for campaign |
| `repeatInterval` | Repeat interval (e.g. daily) |
| `timeWindowStart` / `timeWindowEnd` | Allowed sending hours |
| `maxMessagesPerUser` | Message limit per user |
| `channel` | Delivery channel (Push, SMS, etc.) |
| `templateId` | Message template to use |
| `contactPolicyId` | Contact policy rules |
| `priority` | Campaign priority |
| `abGroup` | A/B test configuration (optional) |

Temporal Workflow uses this configuration for:
- Scheduling repeats (`repeatInterval`)
- Enforcing time windows
- Limiting message frequency
- Selecting channel/template dynamically

CampaignConfig enables flexible runtime behavior without changing workflow logic.
