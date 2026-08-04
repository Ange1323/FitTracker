# Recomp Tracker PWA — recipes and nutrition drawer

This package keeps the original local-first tracker and adds:

- reusable recipes stored locally under the new `rt_recipes` key;
- a slide-out nutrition menu with the last five days of protein, carbohydrate and fat totals;
- five-day summary statistics;
- one-tap recipe logging into today's intake;
- recipe support in JSON backup/export while remaining compatible with older backups.

Existing storage keys remain unchanged:

- `rt_meas`
- `rt_nutri`
- `rt_preset`
- `rt_adj`

Deploy all files together to the same GitHub Pages repository. Replace the old files, including `sw.js`, so the service-worker cache moves to the new version. Existing measurements and nutrition entries remain in the browser's local storage at the same site URL.
