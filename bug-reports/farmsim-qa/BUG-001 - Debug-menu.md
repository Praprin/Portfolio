# BUG-001 - Встроенное debug/cheat-меню доступно игроку («Show debug GUI»)

| Поле                 | Значение                                       |
| -------------------- | ---------------------------------------------- |
| **Type**             | Security / Dev-артефакт                        |
| **Severity**         | Critical                                       |
| **Priority**         | High                                           |
| **Status**           | Open                                           |
| **Affects build**    | Test1 (v0.7.0 / code 1700)                     |
| **Environment**      | Xiaomi 12T Pro, Android 15 (API 35), arm64     |
| **Component / Area** | Отладочные артефакты / Экономика / Монетизация |
| **Reproducibility**  | Always                                         |

## Шаги воспроизведения

1. Запустить игру, дождаться загрузки главного меню - надпись «Show debug GUI» будет видна на экране
2. Тапнуть по кнопке **«Show debug GUI»** 
3. Открывается панель отладки/читов

## Ожидаемый результат

В сборке нет доступного игроку отладочного/читерского интерфейса; игрок не может произвольно менять игровое состояние.

## Фактический результат

Открывается полноценная чит-панель, позволяющая:

- задать hard/soft-валюту = **100000** (set hard / set soft);
- Add / Sub lives, +1h / +1m unlimited lives;
- Nullify boosters, Upgrade farm, Reset tutorials, Reset upgrades;
- вкладки Misc / Gameplay / **Change level** / Time
- и т.п.

В правом нижнем углу виден watermark **«Development Build»** 

## Вложения

![Кнопка «Show debug GUI» на экране](attachments/BUG-001/debug_gui_button.jpg)

![Открытая чит-панель](attachments/BUG-001/cheat_panel.jpg)

## Заметки

Артефакт dev-сборки. Прямая угроза экономике и монетизации (IAP): игрок бесплатно накручивает валюту/жизни/уровни. Кнопка не скрыта - доступна с игрового экрана. Связано с общим статусом «нерелизная сборка» (изучение билда выявило факты, указывающие на это: F-01 debuggable build/release, следы отладочной консоли Lunar Console, эндпоинты, содержащие в адресе "QA", watermark Development Build). **Рекомендация:** полностью убрать debug/cheat GUI и dev-флаги из релизной сборки.
