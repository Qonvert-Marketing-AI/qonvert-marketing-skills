# Яндекс Директ MCP. Проверка UTM и yclid перед запуском

Начните с одной обезличенной рекламной ссылки. Qonvert Marketing AI проверит, какие UTM-поля и идентификаторы видны в её параметрах. Для этой проверки кабинет Директа и аккаунт Qonvert не нужны.

## Первая проверка

1. Добавьте **Qonvert Connect** как удалённый MCP с транспортом Streamable HTTP. Адрес сервера `https://mcp.qonvert.ai/mcp`.
2. Спросите «Какой UTM-метки не хватает в этой ссылке и есть ли в ней yclid?» Для прямого вызова используйте `check_marketing_tracking_url` с аргументами `url` и `language` со значением `ru`.

| Синтетическая ссылка отеля | Ответ гостевой проверки |
| --- | --- |
| `https://example.com/booking?utm_source=yandex&utm_medium=cpc&yclid=synthetic-example` | Не хватает `utm_campaign`, параметр `yclid` виден. |
| `https://example.com/booking?utm_source=yandex&utm_medium=cpc&utm_campaign=hotel_bookings&yclid=synthetic-example` | Все три основные UTM на месте, параметр `yclid` виден. |

## Что сверить в браузере и Метрике

- Откройте разрешённую тестовую ссылку и посмотрите конечный адрес после редиректов. Убедитесь, что выбранные метки сохранились.
- Для реального перехода используйте идентификатор, полученный от Директа. Значение `synthetic-example` только демонстрирует наличие поля. Отсутствие `yclid` в черновом URL само по себе не означает проблему.
- Проверьте нужную цель отдельно. Для регистрации это успешное завершение регистрации. Для покупки сверяйте событие с фактом подтверждённой оплаты. Разбор строки URL эти события не проверяет. [Директ и Метрика](https://yandex.ru/support/direct/ru/statistics/metrika) · [Метки в Метрике](https://yandex.ru/support/metrica/ru/general/source-tags)

## Когда понадобятся данные кабинета

Откройте [справочник Яндекс Директ MCP](https://qonvert.ai/ru/connect/yandex-direct?utm_source=github&utm_medium=guide&utm_campaign=yandex_direct_mcp&utm_content=guest_tracking). Войдите через Qonvert Connect, выберите проект и разрешите доступ к нужному кабинету. Агент может начать с `get_project` и `list_connections`, затем выбрать `yandex_direct_mcp`. В проверке без входа этот инструмент попросил авторизацию. Для работы с кабинетом действуют разрешения проекта и условия выбранного тарифа.

Если у вас есть только примеры ссылок и выгрузки, можно использовать открытый скилл [Audit Campaign Tracking](../skills/audit-campaign-tracking/SKILL.md).
