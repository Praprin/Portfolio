# BUG-004 - Unlocked upgrade image deforms during its "fly-to-inventory" animation

| Field                 | Value                                          |
| -------------------- | ------------------------------------------------- |
| **Type**             | UI / Visual (animation)                            |
| **Severity**         | Minor                                             |
| **Priority**         | Low                                               |
| **Status**           | Open                                              |
| **Affects build**    | Test1 (v0.7.0 / code 1700)                        |
| **Environment**      | Xiaomi 12T Pro, Android 15 (API 35), arm64        |
| **Component / Area** | UI / animations / reward collection                      |
| **Reproducibility**  | Always (observed consistently with all upgrades) |

## Preconditions

Player is on any level whose completion grants an upgrade. Level playthrough has started.

## Steps to reproduce

1. Option A: complete the level with a win. Option B: use the debug panel and select "Win level".
2. Wait for the progress bar to reach the next upgrade and for it to unlock.
3. Watch the upgrade showcase in the center of the screen.
4. Tap the upgrade to start its disappearance animation.
5. Watch the animation where the reward "flies" into the inventory/arsenal.

## Expected result

1. The unlocked upgrade image keeps its shape and proportions throughout the "fly-to-inventory" animation.

2. The image shrinks while keeping square proportions throughout the animation.

3. The image possibly should gradually fade out.

4. The upgrade picture should be preserved until the end of the disappearance animation - no placeholder should be visible.

## Actual result

1. During the "fly-to-inventory" animation, the upgrade image **deforms/distorts** (the sprite's proportions break). Observed with all upgrades.

2. The image shrinks along the X axis but not the Y axis.

3. No fade-out of the picture occurs.

4. At the very end of the animation, the picture disappears and only a distorted white placeholder remains.

## Attachments

![Upgrade "fly-away" animation with deformation](attachments/BUG-004/upgrade_item_image_deformation.gif)

![White placeholder at the end of the animation](attachments/BUG-004/white_placeholder.png)
