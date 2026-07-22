# BUG-010 - Call interruption handled incorrectly: a regular call doesn't pause the game; a VoIP call with app switching kicks the player to the main menu

| Field                 | Value                                                                             |
| -------------------- | ------------------------------------------------------------------------------------ |
| **Type**             | Functional (interruptions / lifecycle)                                             |
| **Severity**         | Major                                                                                |
| **Priority**         | Medium                                                                               |
| **Status**           | Open                                                                                 |
| **Affects build**    | Test1 (v0.7.0 / code 1700)                                                           |
| **Environment**      | Xiaomi 12T Pro, Android 15 (API 35), arm64                                           |
| **Component / Area** | Interruptions / lifecycle (onPause/onResume, audio focus, state restoration) |
| **Reproducibility**  | Always                                                                               |

## Preconditions

The game is running, active gameplay is in progress (a level).

## Variant A - a regular phone call doesn't pause the game

**Steps:**

1. Start gameplay (a level)
2. Trigger an incoming phone (GSM) call on the device
3. Observe the game's behavior during the call

**Expected result:**
The game pauses (or correctly goes to background), sound is muted/mixed under the call; after the call ends, the game resumes from the same point.

**Actual result:**
The game **doesn't pause** - it keeps running during the call (gameplay/timers don't stop, sound is muted but not stopped, the screen dims). After fully switching to the call screen and returning to the game - the game isn't paused, the session keeps going.

## Variant B - a VoIP call with app switching kicks the player to the main menu

**Steps:**

1. Start gameplay (a level)
2. Answer a call in a messaging app (VoIP)
3. Return to the game

**Expected result:**
Returning restores the current gameplay screen and session state (as with regular backgrounding), or the game pauses as with a GSM call.

**Actual result:**
On return, the game is in the "main menu" state, i.e. at the level-launch screen - the current gameplay screen/session progress is lost.

## Attachments

![Phone_Call_interruption_Bug](attachments/BUG-010/Phone_Call_interruption_Bug.gif)

- `attachments/BUG-010/call_interruption.mp4` (recording: behavior during a phone call)
