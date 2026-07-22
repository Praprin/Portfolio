# BUG-006 - System Back button/gesture (Android Back) doesn't work anywhere in the game

| Field                 | Value                                                                       |
| -------------------- | ------------------------------------------------------------------------------ |
| **Type**             | Functional (+ related Usability)                                               |
| **Severity**         | Major                                                                          |
| **Priority**         | Medium                                                                         |
| **Status**           | Open                                                                           |
| **Affects build**    | Test1 (v0.7.0 / code 1700)                                                     |
| **Environment**      | Xiaomi 12T Pro, Android 15 (API 35), arm64; gesture navigation (edge swipe) |
| **Component / Area** | Navigation / system integration (Back)                                        |
| **Reproducibility**  | Always                                                                         |

## Preconditions

The game is running (main menu / gameplay / any nested window).

## Steps to reproduce

1. On any screen, perform the system "Back" gesture (swipe left-to-right) or press the system "Back" button.
2. Observe the game's response.

## Expected result

System "Back" returns to the previous screen / opens the pause menu / shows an exit prompt - per Android convention, the app should respond to Back.

## Actual result

System "Back" and the back gesture **have no effect anywhere** - no response, the screen doesn't change. There's no way to return to the previous screen via the system method (the app doesn't handle Android Back).

## Attachments

![Back swipe with no response](attachments/BUG-006/SwipeBack_Bug.gif)

## Notes (impact + UX)

The defect is compounded by the lack of navigation affordance in the UI: there's no visible "Back"/arrow button (usually "←" in the top-left corner) in the game; the only way out of gameplay is a small "Pause" button in the corner → menu → "Exit", which is hard to discover (not noticed immediately; it's not obvious that exit is hidden inside pause).

**Violations:** Android convention (Back handling), usability heuristics (visibility of navigation, recognition rather than recall).
**Recommendation:** handle system Back (in Unity, `KeyCode.Escape`) as "back/pause"; add a visible back/exit element on gameplay screens.
