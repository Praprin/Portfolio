# BUG-002 - Currency counter disappears from the HUD (icon and animation remain)

| Field                 | Value                                                                                |
| -------------------- | ----------------------------------------------------------------------------------------- |
| **Type**             | UI / Visual (HUD)                                                                       |
| **Severity**         | Major                                                                                   |
| **Priority**         | Medium                                                                                  |
| **Status**           | Open                                                                                    |
| **Affects build**    | Test1 (v0.7.0 / code 1700)                                                              |
| **Environment**      | Xiaomi 12T Pro, Android 15 (API 35), arm64                                              |
| **Component / Area** | UI / HUD / currency counter (affects balance visibility)                                 |
| **Reproducibility**  | Sometimes (2 of 10+ launches, doesn't reproduce reliably) |

## Preconditions

The game is running, a normal gameplay session on the farm has begun.

## Steps to reproduce

> The bug is intermittent, there are no reliable steps. Below is the context in which it occurred.

1. Launch the game, play on the farm (earn currency)
2. In one of the sessions, the numeric currency counter in the HUD was absent from the very start of the session
3. Restarting the game brought the counter back (workaround)

## Expected result

A numeric balance is shown next to the currency icon in the HUD and updates when currency is earned; the currency icon has its animation.

## Actual result

The numeric currency counter is missing: the bill icon and its animation are in place, but **the amount isn't shown** - the player can't see how much they've earned or how much currency they have.

## Attachments

![Missing currency counter (gif from a screen recording)](attachments/BUG-002/missing_money_counter.gif)

![Missing currency counter (screenshot)](attachments/BUG-002/missing_money_counter.png)

## Notes

An intermittent UI defect - the evidence is mostly visual (screen recording). Recommended to correlate with the log around the time the counter disappeared (search for `Exception` / `NullReference` / `currency` / `counter` at session start) - possibly an initialization error for the counter UI element. If reproduced again, narrow down the conditions (specific screen/action right before it appears).
