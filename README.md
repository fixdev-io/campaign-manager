# Campaign Manager (Monorepo)

Микросервисная система для управления кампаниями. Состоит из:

- campaign-api — создание и запуск кампаний
- segment-service — получение сегментов пользователей
- delivery-service — отправка сообщений
- policy-service — проверка контактных политик
- analytics-service — логирование и аналитика
- workflows — Temporal Workflow'ы
- libs — общие модели и утилиты

---

## ☕ Java окружение

Для корректной работы проекта требуется **Java 21**.

Если используешь [SDKMAN](https://sdkman.io/):

```bash
sdk install java 21.0.2-tem
sdk env  # автоматически активирует java=21.0.2-tem из .sdkmanrc
```

Файл `.sdkmanrc` уже включён в проект.

Также для IDE и CLI доступен `.java-version`.

Проверь текущую версию:

```bash
java -version
# Должно быть Java 21
```
