# BUG-007 - 2 or more music tracks play simultaneously when using the cheese factory (starting at level 15)

| Field                 | Value                                                           |
| -------------------- | ------------------------------------------------------------------ |
| **Type**             | Functional (Audio)                                                 |
| **Severity**         | Minor                                                              |
| **Priority**         | Medium                                                             |
| **Status**           | Open                                                               |
| **Affects build**    | Test1 (v0.7.0 / code 1700)                                         |
| **Environment**      | Xiaomi 12T Pro, Android 15 (API 35), arm64                         |
| **Component / Area** | Audio / music (using the cheese factory, level 15)               |
| **Reproducibility**  | Once (observed 1 time; requires repeating via debug -> level 15) |

## Preconditions

Player is at level 15 (the cheese factory's first appearance in the game), on the Level 15 launch menu (the level number button is visible)

## Steps to reproduce

1. Start level 15 and watch the new tutorial (using the cheese factory) at the start of gameplay.
2. Complete the tutorial, i.e. send a milk bottle to the cheese factory
3. Listen to the music - right after the cheese factory process activates, another (different) music track starts
4. Send another milk bottle to the cheese factory - listen, another layer of the same music starts

## Expected result

Only one music track (the level track) plays during the level. Music that played during the tutorial (or the level-select menu) correctly stops when it finishes - there's no overlap between the two tracks.

## Actual result

After finishing the tutorial and activating the cheese factory, another music track starts playing, and both keep playing continuously. Using the cheese factory again causes another copy of the same track to start. And doing it again adds yet another copy. Presumably 4 tracks can be heard at once (the overall volume rises each time, adding more music sounds).

## Attachments

- [Video with sound: two tracks audible at once (first proof)](attachments/BUG-007/Double_Music_Bug.mp4)
- [Video with sound: several tracks, shows what triggers the music start](attachments/BUG-007/2%2BSoundtracks_SameTime_OK.mp4)

> mp4 doesn't play inline in the GitHub repo view - the links open/download the video with sound.
