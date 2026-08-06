# Changelog

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
