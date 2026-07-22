# Реестр багов

Каждый баг - отдельная карточка `BUG-XXX ... .md` (шаблон: `_TEMPLATE.md`). Вложения - в `attachments/BUG-XXX/`.

## Сводная таблица

| ID | Заголовок | Severity | Priority | Окружение | Repro | Статус |
|---|---|---|---|---|---|---|
| [BUG-001](BUG-001%20-%20Debug-menu.md) | Встроенное debug/cheat-меню доступно игроку («Show debug GUI») | Critical | High | Xiaomi 12T Pro / A15 | 5/5 | Open |
| [BUG-002](BUG-002%20-%20Money_counter_disappeared.md) | Пропал счётчик валюты в HUD (иконка и анимация остаются) | Major | Medium | Xiaomi 12T Pro / A15 | Плавающий (неск. раз) | Open |
| [BUG-003](BUG-003%20-%20No_Picture_for_Eggs.md) | Белый квадрат вместо текстовой подписи под разблокированным апгрейдом | Minor | Medium | Xiaomi 12T Pro / A15 | Always (3/3, «Курица») | Open |
| [BUG-004](BUG-004%20-%20Animation_Sprite_Deform.md) | Деформация награды из сундука во время анимации | Minor | Low | Xiaomi 12T Pro / A15 | Once (1 раз) | Open |
| [BUG-005](BUG-005%20-%20Z-order_Complex_Bug_%282varsiations%29.md) | Неправильный z-order окон подарков/наград/Daily Deals над магазином (перекрытие, блокировка «Продолжить», утечка в геймплей) | Major | High | Xiaomi 12T Pro / A15 | A/B: Always · C: Once | Open |
| [BUG-006](BUG-006%20-%20System_BackButton_Gesture_Not_Working.md) | Системная кнопка/жест «Назад» не работает нигде в игре | Major | Medium | Xiaomi 12T Pro / A15 | 5/5 | Open |
| [BUG-007](BUG-007%20-%202_and%20More_Soundtracks_SameTime.md) | Одновременно звучат две музыкальные дорожки после туториала по сыроварне (уровень 15) | Minor | Medium | Xiaomi 12T Pro / A15 | Once (1 раз) | Open |
| [BUG-008](BUG-008%20-%20Time_Change_Daily_Chest_Exploit.md) | Эксплойт: перевод системного времени повторно выдаёт ежедневные сундуки (нет серверной проверки) | Major | Medium | Xiaomi 12T Pro / A15 | Always | Open |
| [BUG-009](BUG-009%20-%2016KB_Page_Size_Incompatible.md) | Краш на старте на 16-КБ page size устройствах (.so под 4 КБ) - несовместимость / риск Google Play | Major | High | AVD, 16-КБ образ / API 37 | Always | Open |
| [BUG-010](BUG-010%20-%20Call_Interruption_Not_Handled.md) | Прерывание звонком: обычный звонок не ставит игру на паузу; VoIP-звонок с переключением выкидывает в главное меню | Major | Medium | Xiaomi 12T Pro / A15 | Always | Open |

## Легенда
**Severity (тяжесть):** Blocker → Critical → Major → Minor → Trivial.
**Priority (срочность):** High / Medium / Low.
**Status:** Open / In Progress / Fixed / Reopened / Closed.

> Severity - техническая тяжесть дефекта; Priority - срочность исправления. Это разные оси.

## Статистика (обновлять по итогам)
- Всего багов: 10 (продолжается)
- Critical/Blocker: 1 · Major: 6 · Minor/Trivial: 3
