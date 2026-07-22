# BUG-003 - White placeholder instead of the "Eggs" sub-icon under the unlocked "Chicken" upgrade image

| Field                 | Value                                                                                                                                                  |
| -------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Type**             | UI / Visual (text label)                                                                                                                                 |
| **Severity**         | Minor                                                                                                                                                     |
| **Priority**         | Medium                                                                                                                                                    |
| **Status**           | Open                                                                                                                                                      |
| **Affects build**    | Test1 (v0.7.0 / code 1700)                                                                                                                                |
| **Environment**      | Xiaomi 12T Pro, Android 15 (API 35), arm64                                                                                                                |
| **Component / Area** | UI / text / upgrade unlock popup                                                                                                                                 |
| **Reproducibility**  | Always (3/3) on unlocking "Chicken"; doesn't reproduce on other upgrades (all preceding ones and the next one, Shield) - the defect is tied to this specific item. |

## Preconditions

Gameplay progress up to the point of unlocking the "Chicken" upgrade (leveling up).

## Steps to reproduce

1. Option A: play through levels until the "Chicken" upgrade unlocks. Option B: use the debug panel to jump back to this unlock ("Win level").
2. Wait for the unlock popup showing the "Chicken" upgrade image.
3. Look at the area under the "Now available:" label.

## Expected result

Under the unlocked upgrade image, its name is shown, along with the "Now available:" label and a smaller icon of the item it unlocks (a pack of eggs).

## Actual result

The "Chicken" upgrade image renders correctly, but **the eggs picture doesn't show - a white square placeholder appears instead**. On other upgrades (all preceding ones and the next one, Shield), the label and icons display normally: the defect is tied to this specific item ("Chicken").

## Attachments

![Popup: white square instead of the eggs picture](attachments/BUG-003/chicken_eggs_bug.gif)

## Notes

The defect is in the label area under the image, tied to a specific item ("Chicken"); other upgrades correctly show a label or an additional icon + label. It looks like the needed image is missing/broken, so a white placeholder is shown instead.
