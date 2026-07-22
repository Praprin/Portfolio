# Test Checklist - FarmSim (FarmSim-QA-Test1.apk)

Status: Pass / Fail / Blocked / N/A / - (not checked).
Two result columns: **Physical device** (Xiaomi 12T Pro, API 35) and **Emulator** (AVD, Pixel 7, API 37).

N/A in the "Emulator" column = not run on the emulator (the case doesn't depend on screen/version, covered by the physical device).

---

## SMOKE TEST

Quick "is the build alive" check. All items Pass = start full testing below.

At least one Fail/Blocked = the build is rejected, don't start full testing, notify the team.

| #   | Check                                                         | Physical device | Emulator | Bug / comment                                                                                         |
| --- | ---------------------------------------------------------------- | --------------------- | -------- | ----------------------------------------------------------------------------------------------------- |
| S1  | APK installs without errors                                   | Pass                  | Pass     | installs on emulator                                                                                  |
| S2  | Cold start completes, no crash                              | Pass                  | Fail     | emulator (16 KB image): crash on startup - [BUG-009](../../bug-reports/farmsim-qa/BUG-009%20-%2016KB_Page_Size_Incompatible.md) |
| S3  | Loading screen finishes, main menu opens             | Pass                  | Blocked  | emulator smoke test stopped at S2                                                                      |
| S4  | Entering the game: the farm (farm_america scene) loads              | Pass                  | Blocked  |                                                                                                       |
| S5  | Basic core loop works (tapping an object/visitor responds) | Pass                  | Blocked  |                                                                                                       |
| S6  | No instant crash/ANR in the first few minutes                        | Pass                  | Blocked  |                                                                                                       |
| S7  | Quitting and relaunching the game works                        | Pass                  | Blocked  |                                                                                                       |

**Smoke result (physical device):** PASS
**Smoke result (emulator):** FAIL - crash on startup on the 16 KB image (BUG-009); not proceeding further on the emulator. There's no non-16 KB image in the current environment, so the emulator compatibility run is blocked.

---

# FULL TESTING (after Smoke = PASS)

## Installation and launch

| Check                                          | Physical device | Emulator | Bug / comment               |
| ------------------------------------------------- | --------------------- | -------- | --------------------------- |
| Permission requests are correct, denial doesn't crash the game | N/A                   | N/A      | No permission requests occurred |
| Game launches in landscape orientation           | Pass                  | N/A      |                             |
| App uninstalls cleanly                | Pass                  | N/A      |                             |

## Main menu and navigation

| Check                                              | Physical device | Emulator | Bug / comment                              |
| ----------------------------------------------------- | --------------------- | -------- | ---------------------------------------------------------------------- |
| Menu buttons are clickable, lead where expected             | Pass                  | N/A      |                                                                        |
| System "Back" button/gesture exists and works, no dead ends | Fail                  | N/A      | [BUG-006](../../bug-reports/farmsim-qa/BUG-006%20-%20System_BackButton_Gesture_Not_Working.md) |

## Core loop: visitors and orders

| Check                                                      | Physical device | Emulator | Bug / comment |
| ------------------------------------------------------------- | --------------------- | -------- | ------------- |
| Visitors appear (hipster/touristlady/flowerlady/common) | Pass                  | N/A      |               |
| Order completes, reward is granted                        | Pass                  | N/A      |               |
| Can't complete an order without resources (correct blocking)   | Pass                  | N/A      |               |

## Economy and production

| Check                                                                  | Physical device | Emulator | Bug / comment                                                                                                                                    |
| ------------------------------------------------------------------------- | --------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------------------------------ |
| Timer-based production starts/completes                           | Pass                  | N/A      |                                                                                                                                                  |
| Currency (cash) is credited/deducted correctly                           | Pass                  | N/A      | Correct in most runs, but there's an intermittent [BUG-002](../../bug-reports/farmsim-qa/BUG-002%20-%20Money_counter_disappeared.md) (money counter display disappears) |
| Stars/experience are credited                                                   | Pass                  | N/A      |                                                                                                                                                  |
| Balance doesn't go negative, no duplication                                | Pass                  | N/A      |                                                                                                                                                  |
| Currency/lives can't be changed illegitimately (no cheat menu accessible to the player) | Fail                  | N/A      | debug/cheat GUI is accessible - [BUG-001](../../bug-reports/farmsim-qa/BUG-001%20-%20Debug-menu.md)                                                                           |
| Rewards can't be farmed by changing system time (server-side check)     | Fail                  | N/A      | daily chests are granted repeatedly - [BUG-008](../../bug-reports/farmsim-qa/BUG-008%20-%20Time_Change_Daily_Chest_Exploit.md)                                          |

## Upgrades and boosters

| Check                             | Physical device | Emulator | Bug / comment |
| ------------------------------------ | --------------------- | -------- | ------------- |
| Time Booster works | Pass                  | N/A      |               |
| Shield booster works                  | Pass                  | N/A      |               |
| Cow upgrade works              | Pass                  | N/A      |               |
| Bakery upgrade works          | Pass                  | N/A      |               |
| Chicken upgrade works              | Pass                  | N/A      |               |
| Cheese Factory upgrade works           | Pass                  | N/A      |               |

## Reward collection

| Check                                  | Physical device | Emulator | Bug / comment |
| ----------------------------------------- | --------------------- | -------- | ------------- |
| Cash collection: animation + credit          | Pass                  | N/A      |               |
| Star collection works                       | Pass                  | N/A      |               |
| Completion checkmarks are correct | Pass                  | N/A      |               |

## Shop, Daily Deals, purchases (IAP)

| Check                                            | Physical device | Emulator | Bug / comment                                                                                  |
| --------------------------------------------------- | --------------------- | -------- | ------------------------------------------------------------------------------------------------- |
| Shop opens, prices are shown              | Pass                  | N/A      |                                                                                                |
| Daily Deals are available/refresh                    | Pass                  | N/A      |                                                                                                |
| Purchase via Google Play Billing initiates      | N/A                   | N/A      | IAP is mocked in the QA build; Play Billing catalog unavailable (`Unavailable product hard_*` in the log) |
| Test purchase completes (sandbox), item is granted | N/A                   | N/A      | gem purchase is mocked: completes instantly, free                                           |
| Cancelling a purchase without losing funds/crashing             | N/A                   | N/A      | real purchase flow not checkable on this build                                              |

## Gifts and tutorial

| Check                                            | Physical device | Emulator | Bug / comment                                                                                                     |
| --------------------------------------------------- | --------------------- | -------- | ----------------------------------------------------------------------------------------------------------------- |
| Gift can be received/opened, reward is credited | Fail                  | N/A      | box sits underneath the shop menu, flow gets stuck - [BUG-005](../../bug-reports/farmsim-qa/BUG-005%20-%20Z-order_Complex_Bug_%282varsiations%29.md) |
| Tutorial starts on first launch, can be completed  | Pass                  | N/A      |                                                                                                                   |

## UI / graphics / safe area

| Check                                                   | Physical device | Emulator | Bug / comment                                                                                              |
| ---------------------------------------------------------- | --------------------- | -------- | ---------------------------------------------------------------------------------------------------------- |
| No overlapping/clipped text                               | Fail                  | N/A      | with [BUG-005](../../bug-reports/farmsim-qa/BUG-005%20-%20Z-order_Complex_Bug_%282varsiations%29.md), different titles overlap |
| Window z-order is correct (popups/rewards over other menus) | Fail                  | N/A      | gift box under the shop - [BUG-005](../../bug-reports/farmsim-qa/BUG-005%20-%20Z-order_Complex_Bug_%282varsiations%29.md)       |
| UI is not covered by the cutout/notch (renders past the safe area)         | Pass                  | N/A      | notch on the emulator - see the "Compatibility" section                                                            |
| Spine animations are smooth, no glitches                       | Fail                  | N/A      | reward deforms during the animation - [BUG-004](../../bug-reports/farmsim-qa/BUG-004%20-%20Animation_Sprite_Deform.md)                 |
| No broken sprites, flickering                               | Fail                  | N/A      | white square in the production popup - [BUG-003](../../bug-reports/farmsim-qa/BUG-003%20-%20No_Picture_for_Eggs.md)                    |

## Sound

| Check                                               | Physical device | Emulator | Bug / comment                                                                                                             |
| ------------------------------------------------------ | --------------------- | -------- | ------------------------------------------------------------------------------------------------------------------------- |
| Music and SFX play                             | Pass                  | N/A      |                                                                                                                           |
| Visitor voice lines work                             | Pass                  | N/A      |                                                                                                                           |
| Sound mutes when the app is backgrounded                         | Pass                  | N/A      |                                                                                                                           |
| Only one music track plays at a time (no overlap) | Fail                  | N/A      | 2 tracks overlap after the cheese factory tutorial (level 15) - [BUG-007](../../bug-reports/farmsim-qa/BUG-007%20-%202_and%20More_Soundtracks_SameTime.md) |

## Save and state

| Check                                        | Physical device | Emulator | Bug / comment  |
| ----------------------------------------------- | --------------------- | -------- | -------------- |
| Progress is saved after quitting and relaunching | Pass                  | N/A      |                |
| Backgrounding/returning doesn't reset state    | Pass                  | N/A      |                |
| State isn't lost on crash                 | N/A                   | N/A      | no crashes occurred |

## Performance (physical device)

Perf is measured only on the physical device - numbers on the emulator aren't representative, so Emulator = N/A.

| Check                                                                    | Physical device | Emulator | Bug / comment                                                                  |
| --------------------------------------------------------------------------- | --------------------- | -------- | -------------------------------------------------------------------------------- |
| Stable FPS, no freezes                                                  | Pass                  | N/A      |                                                                                |
| No overheating/excessive battery drain over 15 min                         | Pass                  | N/A      |                                                                                |
| Acceptable screen load times                                           | Pass                  | N/A      |                                                                                |
| RAM usage: baseline is stable over 10+ min, no growth (no leak) | Pass                  | N/A      | Profiler: plateaus at ~500-540 MB, memory is released                              |
| Peak RAM usage (record MB)                                       | Pass                  | N/A      | peak ~620 MB; footprint is a bit high for low-end - check on 2-3 GB RAM         |
| No abnormal CPU spikes while idle                                          | Pass                  | N/A      | around 11-12% (test ~2 min), [screenshot](../../bug-reports/farmsim-qa/attachments/Profiler_App_CPU_Usage.png) |

## Interruptions and network

| Check                                                             | Physical device | Emulator | Bug / comment                                                                                                                             |
| -------------------------------------------------------------------- | --------------------- | -------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| An incoming call pauses the game, resumes correctly afterward | Fail                  | N/A      | a call doesn't pause the game; a VoIP call with app switching kicks the player to the menu - [BUG-010](../../bug-reports/farmsim-qa/BUG-010%20-%20Call_Interruption_Not_Handled.md) |
| Backgrounding (Home) and returning restores state              | Pass                  | N/A      |                                                                                                                                           |
| Offline (airplane mode): a clear error/degradation, no crash              | Pass                  | N/A      | no errors, the game just keeps working                                                                                                   |
| Switching Wi-Fi / mobile data on the fly doesn't crash the game                | Pass                  | N/A      |                                                                                                                                           |

## Negative / crash scenarios

| Check                                                     | Physical device | Emulator | Bug / comment |
| ------------------------------------------------------------ | --------------------- | -------- | ------------- |
| Spam-tapping / rapid repeated taps don't crash the game         | Pass                  | N/A      |               |
| Rotating the screen mid-transition/animation doesn't crash          | Pass                  | N/A      |               |
| No ANR (no freeze longer than 5 sec) during intensive actions | Pass                  | N/A      |               |

## Localization

| Check                                                      | Physical device | Emulator | Bug / comment |
| ------------------------------------------------------------- | --------------------- | -------- | ------------- |
| RU: text fits, no clipping/overlap, no missing lines | Pass                  | N/A      |               |
| EN: text fits, no clipping/overlap, no missing lines | Pass                  | N/A      |               |
| Language switching applies correctly                      | Pass                  | N/A      | RU/EN both OK  |

## Compatibility (emulator only)

This section is run **only on AVD** (there's nothing for the physical device to check here). Emulator smoke test is in the "Emulator" column of the SMOKE table above.

> **Environment limitation:** in the current Android Studio, emulator images are limited to preview API 37 - the matrix of older Android versions isn't covered. Modern configurations are covered by the physical device (Xiaomi 12T Pro, API 35). The APK is ARM-only: on an x86_64 image (API >= 30) the game runs via built-in ARM translation. **The only available image is 16 KB page size, and the game crashes on it (BUG-009), so the visual checks below couldn't be performed.**

| Check                                                                  | Emulator | Comment                                                                                                                                                                      |
| ------------------------------------------------------------------------- | -------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Device with a cutout/notch: UI in the safe area, nothing is clipped             | Blocked  | game doesn't start on the 16 KB image (BUG-009)                                                                                                                                   |
| Tablet / landscape: layout isn't stretched or clipped                    | Blocked  | same                                                                                                                                                                        |
| Different resolutions/DPI: no overlaps or broken sprites                     | Blocked  | same                                                                                                                                                                        |
| Interruptions via Extended Controls (call/network/battery)                  | Blocked  | same                                                                                                                                                                        |
| 16 KB image: game launches (checking the "Does not support 16 KB" finding) | Fail     | crash on startup: UnsatisfiedLinkError, libmain.so, alignment 8192 < 16384 - [BUG-009](../../bug-reports/farmsim-qa/BUG-009%20-%2016KB_Page_Size_Incompatible.md) (confirms the finding from Assignment #1) |

## Network traffic analysis (Fiddler)

Dynamic interception of **Test1** build HTTPS traffic on the physical device (Xiaomi 12T Pro).

**Method:** Fiddler proxy on the PC, the phone routes through the proxy over Wi-Fi; the Fiddler root certificate is installed as a user CA. The build **trusts the user-CA** (finding F-09), so interception succeeded.

**Confirmed game hosts** (attributed via SDK-specific domains):

- **Unity Ads:** config.unityads.unity3d.com, publisher-config.unityads.unity3d.com, httpkafka.unityads.unity3d.com, cdp.cloud.unity3d.com, config.uca.cloud.unity3d.com
- **Facebook / Meta SDK:** graph.facebook.com, graph-fallback.facebook.com, graph.fbpigeon.com
- **Firebase:** firebaselogging.googleapis.com
- **Geo / Google API:** freegeoip.app, play-fe.googleapis.com, spot-pa.googleapis.com
- **From static analysis (strings/arsc):** farmsim-qa.firebaseio.com, farmsim-qa.appspot.com

**Conclusions:**

- **Unity Ads genuinely reaches the network** → ads are present (refines the static-analysis finding).
- The game sends data to third-party services (Unity Ads, Facebook, Firebase) → confirms finding F-08; should be reflected in Data Safety / App Privacy.
- **F-09 confirmed in practice** (user-CA trust → interception is possible).
