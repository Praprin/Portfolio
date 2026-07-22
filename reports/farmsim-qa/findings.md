# Findings Registry - FarmSim (Supplement to Assignment #1)

Full list of what was determined about the two builds during static analysis (without running the game). Findings are grouped by topic, numbered F‑01…F‑22 for cross-referencing.

---

### 1. Readiness for Play Store publication

| Code  | Finding                             | What it means                                                                                                                                                   |
| ---- | ----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| F‑01 | Debug build                   | The game is built in developer (debug) mode. Google Play doesn't accept such builds, and it's also a security risk.                                       |
| F‑02 | Outdated target Android version       | The builds target an Android version below what Google Play currently requires. The game can't be published as-is.                                          |
| F‑03 | Builds for different CPU architectures        | One only works on old 32-bit phones, the other only on newer 64-bit ones. Google Play requires 64-bit support, so the 32-bit build won't pass. |
| F‑04 | A debug console is built into the game | A developer tool (an internal console) is embedded in the build. It shouldn't be present in the final version.                                                      |
| F‑05 | The game is connected to a test server | Both builds are configured for a test (QA) environment. The release needs a working (production) config.                                                              |

### 2. Security and privacy

| Code  | Finding                                       | What it means                                                                                                                                                              |
| ---- | --------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| F‑06 | Technical access keys are visible in the build      | Client-side keys and service addresses are stored inside the app. This is normal for apps, but they need to be protected via server-side settings.                       |
| F‑07 | The debug build is signed with a "production" key | Even though the builds are debug builds, they're signed with the company's real key - and both with the same one.                                                                         |
| F‑08 | Data is sent to third-party services              | The game transmits data to external services (analytics, crash reporting, ads, social networks). This needs to be honestly disclosed in the app's privacy section. |
| F‑09 | Insecure network configuration                   | The settings allow interception of the app's secure traffic. Convenient for testing, but a vulnerability in a release.                                                 |
| F‑10 | Install-tracking and ad-attribution service       | The game has a service that tracks install sources and sends data out.                                                                              |
| F‑11 | Leftover internal developer addresses       | Internal network addresses of the developer's work machine remain in the build settings - traces of the development build.                                             |

### 3. Permissions

| Code  | Finding                                   | What it means                                                                                                                                 |
| ---- | ----------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------- |
| F‑12 | Deprecated file-write permission  | The game requests a deprecated file-write permission. It no longer has effect on the newer build, but is still requested on the older one.                       |
| F‑13 | Wi-Fi permission with no clear function     | The game requests a Wi-Fi-network-related permission with no visible function tied to it. Google Play doesn't favor unnecessary permissions. |
| F‑14 | Same permission set in both builds | Both request the same things: internet access, network state, in-app purchases, notifications, and a couple of utility ones.                          |

### 4. Target platforms

| Code  | Finding                                      | What it means                                                                                                                         |
| ---- | -------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| F‑15 | Traces of TV and smartwatch support             | The build contains resources for Android TV and watches. This might not be actual support, just library leftovers - worth confirming. |
| F‑16 | Configuration for Chinese app stores | The build contains configuration for the vivo, xiaomi, huawei, and oppo stores. This means the game is planned for distribution outside Google Play too.    |

### 5. Technical build facts

| Code  | Finding                                    | What it means                                                                                                                 |
| ---- | ------------------------------------------ | ----------------------------------------------------------------------------------------------------------------------- |
| F‑17 | The game is built on an old Unity engine (2019) | This is most likely why the target Android version is low.                                                              |
| F‑18 | Launch screen and orientation                 | The game starts in horizontal (landscape) orientation. Launch settings are the same in both builds.                     |
| F‑19 | The game renders under the screen cutout               | The image renders into the notch area. There's a risk the UI could overlap the cutout - needs checking.               |
| F‑20 | Extra config file and trace of an iOS version      | The build contains an unnecessary duplicate config and a mention of iOS - meaning the game also has an iPhone version.                  |
| F‑21 | Internal code name from a cooking game   | Internally the code sits under the name of a different game ("cooking…"). It looks like the farm was built by reusing a cooking game's codebase. |

### 6. What the game consists of

| Code  | Finding                | What it means                                                                                                                                                                                                                          |
| ---- | ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| F‑22 | Map of game content | This is a farm time-management game: one location, visitors with orders, upgrades, boosters, reward collection, a shop, daily deals, gifts, tutorial hints. This list became the basis of the test checklist (Assignment #2). |

---
