# Bug Registry

## Summary table

| ID                                                                 | Title                                                                                                                      | Severity | Priority | Environment               | Repro                        | Status |
| ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- | -------- | -------- | ------------------------- | ---------------------------- | ------ |
| [BUG-001](BUG-001%20-%20Debug-menu.md)                             | Built-in debug/cheat menu accessible to the player ("Show debug GUI")                                                      | Critical | High     | Xiaomi 12T Pro / A15      | 5/5                          | Open   |
| [BUG-002](BUG-002%20-%20Money_counter_disappeared.md)              | Currency counter disappears from HUD (icon and animation remain)                                                           | Major    | Medium   | Xiaomi 12T Pro / A15      | Intermittent (several times) | Open   |
| [BUG-003](BUG-003%20-%20No_Picture_for_Eggs.md)                    | White square instead of text label under an unlocked upgrade                                                               | Minor    | Medium   | Xiaomi 12T Pro / A15      | Always (3/3, "Chicken")      | Open   |
| [BUG-004](BUG-004%20-%20Animation_Sprite_Deform.md)                | Chest reward deforms during animation                                                                                      | Minor    | Low      | Xiaomi 12T Pro / A15      | Once (1 time)                | Open   |
| [BUG-005](BUG-005%20-%20Z-order_Complex_Bug_%282varsiations%29.md) | Incorrect z-order of gift/reward/Daily Deals windows over the shop (overlap, blocked "Continue", leaks into gameplay)      | Major    | High     | Xiaomi 12T Pro / A15      | A/B: Always · C: Once        | Open   |
| [BUG-006](BUG-006%20-%20System_BackButton_Gesture_Not_Working.md)  | System Back button/gesture doesn't work anywhere in the game                                                               | Major    | Medium   | Xiaomi 12T Pro / A15      | 5/5                          | Open   |
| [BUG-007](BUG-007%20-%202_and%20More_Soundtracks_SameTime.md)      | Two music tracks play simultaneously after the cheese factory tutorial (level 15)                                          | Minor    | Medium   | Xiaomi 12T Pro / A15      | Once (1 time)                | Open   |
| [BUG-008](BUG-008%20-%20Time_Change_Daily_Chest_Exploit.md)        | Exploit: changing system time re-grants daily chests (no server-side check)                                                | Major    | Medium   | Xiaomi 12T Pro / A15      | Always                       | Open   |
| [BUG-009](BUG-009%20-%2016KB_Page_Size_Incompatible.md)            | Crash on startup on 16 KB page size devices (.so aligned for 4 KB) - incompatibility / Google Play risk                    | Major    | High     | AVD, 16 KB image / API 37 | Always                       | Open   |
| [BUG-010](BUG-010%20-%20Call_Interruption_Not_Handled.md)          | Call interruption: a regular call doesn't pause the game; a VoIP call with app switching kicks the player to the main menu | Major    | Medium   | Xiaomi 12T Pro / A15      | Always                       | Open   |

## Legend

**Severity:** Blocker → Critical → Major → Minor → Trivial.
**Priority:** High / Medium / Low.
**Status:** Open / In Progress / Fixed / Reopened / Closed.

## Stats (update as work progresses)

- Total bugs: 10 (ongoing)
- Critical/Blocker: 1 · Major: 6 · Minor/Trivial: 3


