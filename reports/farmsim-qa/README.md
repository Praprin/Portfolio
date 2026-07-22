# FarmSim QA — Test Assignment (Mobile Game, NDA Studio)

Author: Alexey Praprin · Date: 07/06/2026

> **Portfolio version.** The original test assignment was completed for a real studio under NDA. The studio name, game name, package name, domains, and build signature in this copy have been replaced with neutral placeholders (`FarmSim` / `NDA Studio` / `com.ndastudio.farmsimqa`); on screenshots and videos, fragments showing the real game name/package/phone number have been blurred out. The structure of the report, checklist, bug reports, and findings is unchanged.

QA test assignment for the mobile game **FarmSim** (`com.ndastudio.farmsimqa`, v0.7.0 / code 1700). Two builds: `FarmSim-QA-Test1.apk`, `FarmSim-QA-Test2.apk`.

## Navigation

- **[Build comparison](builds-comparison.md)** and **[findings registry](findings.md)** — static analysis of both APKs: how the builds differ, on which characteristics, and the release-readiness verdict.
- **[Test plan and checklist](../../test-plans/farmsim-qa/checklist.md)** — approach, environment, full functional/non-functional testing.
- **[Bug reports](../../bug-reports/farmsim-qa/README.md)** — 10 defect cards with screenshots/gifs/videos/logs.

## In short

- **Build comparison:** both APKs are the same game version in two build variants (32-bit/target29/2022 and 64-bit/target30/2025). Differences: architecture, targetSdk, size, build date, partially re-exported animations. Both are debug QA builds, not ready for publication.
- **Testing:** functional and non-functional testing of the Test1 build on a real device + ARM emulator. 10 defects found, ranging from Critical (player-accessible debug/cheat menu) to Minor.

## Why this format

A report in a Git repository as Markdown: versioned, reviewable like code, opens with a single link with no downloads needed, evidence (screenshots/gifs/mp4/txt logs) sits right next to each bug.
