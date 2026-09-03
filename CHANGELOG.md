# Changelog

## 4.0.0 — Day detail and selectable trends

**Last 5 days is now expandable.** Tap a day to see every item logged, each with
a `+ Today` button that copies it straight into today's intake. The open day
survives the re-render, so adding several items in a row doesn't collapse it.
Days with nothing logged show as a flat, dimmed row.

**Trends are selectable.** A new *Trends* section in the drawer toggles which of
the six weekly measurements are plotted. Selection persists under a new
`rt_charts` key.

- Each metric renders as its own chart, not overlaid. Weight is kg and the rest
  are cm — a shared y-axis would be meaningless.
- Series colours are Okabe-Ito re-stepped into the dark-mode lightness band, then
  validated against the dark surface: worst adjacent CVD dE 13.4 (deutan), worst
  normal-vision dE 15.2, all >= 3:1 contrast. Every chart is also text-labelled,
  so identity never rests on colour alone.

**Chart fixes** (both affect the existing Waist/Weight charts too):

- Y-axis labels adapt precision to the range. A 1 cm spread used to render
  "34, 34, 33"; it now renders "32.9, 33.5, 34.1".
- The final date label is anchored to the plot edge instead of centred on the
  last point, which was clipping it.
- Scoped the accordion chevron rule to its own summary — it was rotating and
  gold-colouring every nested day chevron.

No change to `rt_meas`, `rt_nutri`, `rt_preset`, `rt_adj`, `rt_recipes`,
`rt_activity`. Service-worker cache renamed to `recomp-root-v4`.

## 3.1.0 — Dark performance UI

- Restyled the entire app on a dark canvas (`#0E1626`) with amber, mint and coral accents.
- Collapsible drawer sections — Apple Watch activity, Last 5 days, 5-day stats, Saved recipes.
  Built on native `<details>`/`<summary>`, so they collapse without any JavaScript.
- Collapsed section headers keep their summary readable: the sync status badge and the recipe count.
- Score readout signals mint at 75+ and coral below, with a glow that follows the active colour.
- Updated `theme-color`, manifest colours, and the iOS status-bar style for the dark canvas.
- Service-worker cache renamed to `recomp-pwa-v3-1-dark`.
- **No storage changes.** `rt_meas`, `rt_nutri`, `rt_preset`, `rt_adj`, `rt_recipes` and
  `rt_activity` are untouched, so deploying over the existing Pages URL preserves all history.

## 3.0.0 — Apple Health Shortcut bridge

- Added a new `rt_activity` local-storage key for daily Apple Health records.
- Added Active Energy, Resting Energy, Total Energy, Steps, and Exercise Minutes views.
- Added a `Sync Apple Health` button that launches a Shortcut named `Recomp Health Sync`.
- Added clipboard import, manual fallback entry, seven-day activity history, and daily activity deletion.
- Added activity data to backup export/import while retaining compatibility with older backups.
- Preserved the existing `rt_meas`, `rt_nutri`, `rt_preset`, `rt_adj`, and `rt_recipes` keys.
- Updated the service-worker cache to `recomp-pwa-v3-apple-health` and changed navigation requests to network-first.

## 2.0.0 — Recipes and nutrition drawer

- Added reusable recipes under `rt_recipes`.
- Added the five-day nutrition drawer, statistics, and one-tap recipe logging.
