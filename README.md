# Recomp Tracker PWA — version 4.0.0

This release keeps the existing local-first tracker and the Apple Health / Apple Watch activity
bridge, and restyles the app on a dark canvas with collapsible drawer sections.

## Added in version 3.1

- a dark UI across the whole app, with amber, mint and coral accents;
- collapsible drawer sections for Apple Watch activity, recent days, stats, and saved recipes;
- summary values (sync status, recipe count) visible on collapsed headers.

No storage keys changed in 3.1. Deploy over the same Pages URL and all history is preserved.

## Added in version 3

- daily Active Energy, Resting Energy, derived Total Energy, Steps, and Exercise Minutes;
- a `Sync Apple Health` button that runs a Shortcut named `Recomp Health Sync`;
- clipboard import after the Shortcut returns to Recomp;
- seven-day activity history and averages;
- manual activity entry as a fallback;
- activity data in version-3 JSON backups;
- a new independent local-storage key: `rt_activity`.

## Existing data remains compatible

These existing keys are unchanged:

- `rt_meas`
- `rt_nutri`
- `rt_preset`
- `rt_adj`
- `rt_recipes`

Do not change the GitHub Pages address when deploying this release. Browser data is tied to the existing site origin.

## Files

- `index.html` — complete tracker application;
- `manifest.webmanifest` — Home Screen / PWA metadata;
- `sw.js` — offline cache, versioned for this release;
- `APPLE-SHORTCUT-SETUP.md` — build instructions for the Apple Health Shortcut;
- `GITHUB-UPDATE-GUIDE.md` — safe branch and merge workflow;
- `CHANGELOG.md` — release changes;
- `RELEASE-CHECKS.md` — validation completed before packaging;
- `SHORTCUT-PAYLOAD.txt` — payload template for the Shortcut Text action;
- `VERSION` — release number.

Before deployment, use **Export backup** in the currently installed tracker. Then follow `GITHUB-UPDATE-GUIDE.md`.
