# Recomp Tracker PWA

This is a PWA-ready version of `recomp-tracker-app.html`.

Files:
- `index.html`: the app, still local-first and self-contained except for the PWA helper files.
- `manifest.webmanifest`: app metadata for Home Screen install.
- `sw.js`: service worker cache for offline loading after first visit.
- `icon-*.png`: app icons.

Deploy the whole folder to an HTTPS host such as GitHub Pages, Netlify, Vercel, or your own server.
Then open the URL on iPhone in Safari and use Share -> Add to Home Screen.

Your measurements and nutrition entries remain in the browser on the phone via localStorage. Use the Export backup button periodically.
