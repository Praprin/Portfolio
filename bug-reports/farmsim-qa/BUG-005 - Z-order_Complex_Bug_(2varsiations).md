# BUG-005 - Incorrect z-order of gift/reward/Daily Deals windows over the shop (overlap, blocked "Continue", leaks into gameplay)

| Field                 | Value                                                                          |
| -------------------- | ----------------------------------------------------------------------------------- |
| **Type**             | UI / Visual (z-order / UI lifecycle)                                         |
| **Severity**         | Major                                                                             |
| **Priority**         | High                                                                              |
| **Status**           | Open                                                                              |
| **Affects build**    | Test1 (v0.7.0 / code 1700)                                                        |
| **Environment**      | Xiaomi 12T Pro, Android 15 (API 35), arm64                                        |
| **Component / Area** | UI / modal windows / z-order / UI lifecycle (gifts, Daily Deals, shop) |
| **Reproducibility**  | Variant A - **Always**; Variant B - **Sometimes** (2 times over 10+ sessions)          |

One defect (broken modal window/layer management) with several manifestations.

## Variant A - gift/Daily Deals windows layer over the shop (Always)

**Steps:**

1. Open the Shop and observe its menu - layer 1
2. Claim the daily gift and observe that the box appears BEHIND the Shop menu (layer 0), while the gift that pops out of it appears IN FRONT of the shop menu (layer 3)
3. Note the "Tap to continue" label at the bottom of the screen; tap it and observe that the gift doesn't disappear - the label isn't clickable
4. Buy an item with gems/crystals (e.g. Shield) and observe that the popup warning you're about to spend gems slides in BETWEEN the Shop menu and the daily gift display (i.e. layer 2)

**Expected result:**

1. The Daily Gift's animation and image display IN FRONT of the Shop menu (at layer 2)
2. The shop menu should somehow dim, blur, or both, so the gift animation is visible.
3. Tapping hides the gift and another item can be selected
4. When buying an item with gems, the warning popup also appears IN FRONT of the shop menu, and the shop menu loses focus via dimming and/or blur; upon purchase confirmation the popup disappears, and the item's animation and image happen IN FRONT of the shop menu.
5. If, say, the Daily Gift is already shown on screen, purchasing another item should be unavailable until the gift is tapped and disappears, i.e. the second item's animation shouldn't play ON TOP of the first
6. Screen titles (Reward/Shop) should also each appear on screen separately and not overlap each other at the same time

**Actual result:**

1. When the Daily Gift is claimed, it **always layers** over the Shop menu, and the "Tap to continue" label is visible but not clickable
2. When buying an item with gems, it layers over the Shop menu
3. Claiming them one after another stacks them with incorrect z-order, as described in the Steps
4. Parts end up below/above the shop in a mixed-up way
5. The only way out is tapping the "X" in the top-right corner, which closes the Shop menu and reveals the gift window, which can then be tapped to dismiss it
6. Screen titles (Reward/Shop) overlap each other, appearing at the same time and in the same place, as seen in the attached gif

## Variant B - gift UI leaks into gameplay (Sometimes, 2 times)

**Preconditions:**

1. The game is running
2. The Shop menu is open

**Steps (couldn't reproduce the defect again; below are the steps under which the bug occurred):**

1. Claim the Daily Gift in the bottom-left menu (the box shows under the shop, its contents above)
2. Buy an available item with gems in the top-left menu (the popup appears ABOVE the Shop menu and BELOW the Daily Gift display)
3. Confirm the gem purchase (the popup disappears), the Daily Gift elements stay as they were
4. Tap the "X" in the top-right, the Shop menu closes, the main menu appears (level launch)
5. Tap "Start Level", the Booster selection menu and "Play" button appear
6. Tap "Play", the level loading screen appears and the level itself begins

**Expected result:**

1. Tapping the gift or the "Tap to continue" label removes the gift UI
2. The Daily Gift UI is fully removed when the Shop closes and the level-launch screen appears
3. The Daily Gift UI is fully removed once the level itself loads

**Actual result:**

1. While the layers are overlapping, tapping the gift or the "Tap to continue" label doesn't remove the gift UI
2. After closing the shop, the box/gift **stays on top of the main menu**, visible on the Booster selection screen (IN FRONT of the Booster menu, but BEHIND the character layer explaining what to do). The gift UI **is hidden** during the level-loading animation screen, but is then visible **on top of gameplay** - it's only removed by tapping it, which works at that point.

## Attachments

![Variant A: gift window layering under and over the shop](attachments/BUG-005/Z-order_Bug_var1.gif)

![Variant B: gift UI leaking into gameplay](attachments/BUG-005/Z-order_Bug_var2.gif)
