# Assignment #2 - Testing

Approach, environment, and notes for FarmSim testing. The actual test run is in the [checklist](checklist.md); defects found are in the [bug reports](../../bug-reports/farmsim-qa/README.md).

## Object

Build `FarmSim-QA-Test1.apk`, v0.7.0 / code 1700, arm64, targetSdk 30 — chosen as the newer and more release-like configuration.

## Environment / devices

| Configuration                | Type                   | Role                                              |
| --------------------------- | --------------------- | ------------------------------------------------- |
| Xiaomi 12T Pro (Android 14) | physical device | main run: perf, graphics, notch, interruptions |
| AVD, Pixel 7, API 37        | emulator              | compatibility check                            |

## Approach

- Functional testing via checklist (`checklist.md`) + game mechanics (orders, upgrades, boosters, collection, shop/IAP, daily deals, tutorial, save).
- Non-functional: performance, UI/layout, sound, interruptions, network, store guideline compliance.
- Negative scenarios and interruptions (spam-tapping, rotation, calls, backgrounding, offline).
- Dynamic: traffic interception (Fiddler) - cross-checking endpoints against declared data collection.
- Each checklist Fail -> a bug card in [`bug-reports/farmsim-qa/`](../../bug-reports/farmsim-qa/README.md)
- Attachments (screenshots/video/logs) - in [`bug-reports/farmsim-qa/attachments/`](../../bug-reports/farmsim-qa/attachments/)

## Observations on the QA build (not bugs - limitations/quirks of the build under test)

These aren't product defects but a consequence of testing a non-release QA build. Noting them and passing them to the team for context.

- **In-App Purchase (IAP) is mocked.** Real purchases via Google Play Billing **can't be verified** on this build: the product catalog fails to load (log shows `Unavailable product hard_2 … hard_80`), and buying gems completes **instantly and for free** with the message "Thank you. Enjoy the game" — this is a QA-build stub for acquiring/spending currency. The full purchase flow needs to be checked on a build from Play Console / internal testing.
- **Unity Ads doesn't initialize.** The log shows `Unity Ads SDK fail to initialize due to internal error`. Likely because this is a QA release (not production ad keys/settings). To confirm with the team. **Important:** this is also a correction to the static analysis - **Unity Ads is present in the game** (ads are integrated).
