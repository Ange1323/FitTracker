# Deploying version 4

Repository: `ange1323/FitTracker` · Pages: `https://ange1323.github.io/FitTracker/`
Pages builds from `main`, repository root.

**The Pages address must not change.** All tracker data lives in `localStorage`
scoped to the origin `https://ange1323.github.io`.

## Before you start

Open the live app and tap **Export backup**. Keep the JSON.

## 1. Branch

Branch selector → type `feature/v4-day-detail-trends` →
**Create branch: … from main**. Confirm the selector shows the new branch.

## 2. Upload

**Add file → Upload files**, drag in everything from this folder, and commit to
the branch with:

`V4: expandable day entries, selectable trend metrics`

These are root files only. The existing `beta/` folder is untouched by this
upload and stays on version 3.2.

## 3. Verify on the branch

| File | Must contain |
|---|---|
| `index.html` | `data-readd`, `accTrends`, `CHART_COLOR` |
| `sw.js` | `recomp-root-v4` |
| `VERSION` | `4.0.0` |

Confirm the original storage keys are still present in `index.html`:
`rt_meas`, `rt_nutri`, `rt_preset`, `rt_adj`, `rt_recipes`, `rt_activity`.
Version 4 adds one new key, `rt_charts`, holding the trend selection only.

## 4. Merge

**Contribute → Open pull request**, base `main`, review **Files changed**,
then **Merge pull request**. Pages rebuilds in 1–2 minutes.

## 5. Refresh the iPhone

1. Open the Pages URL in Safari and pull to refresh.
2. Fully close the Home Screen app (swipe the card away, not just Home).
3. Reopen. A second close/reopen is often needed before the new service worker
   takes control.
4. Confirm: tapping a day under **Last 5 days** expands it, and a **Trends**
   section appears in the drawer.

Never use Safari's *Clear History and Website Data*, and do not delete the Home
Screen icon — both wipe `localStorage` for the whole origin.

## Rollback

Revert the merge commit on `main`. Code rolls back; stored data is unaffected.
