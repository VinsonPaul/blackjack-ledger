# Blackjack Ledger — PWA Install Guide

You have a complete PWA bundle. To install it on your phone, the files need to be served over **HTTPS** (a hard requirement for service workers / offline mode on iOS and modern Android).

Pick whichever path below fits you.

## Option A — Netlify Drop (easiest, ~60 seconds)

1. Go to **https://app.netlify.com/drop**
2. Drag the entire `blackjack-pwa` folder (unzipped) onto the page
3. Netlify gives you a URL like `https://something-random.netlify.app`
4. Open that URL on your iPhone in **Safari**
5. Tap **Share** → **Add to Home Screen**
6. Done — you have an icon, full-screen launch, and offline support

No account required for the initial deploy.

## Option B — GitHub Pages

1. Create a repo, drop these files at the root, push
2. Settings → Pages → Deploy from main branch
3. Wait 1 min, then open the resulting `https://yourname.github.io/repo` URL on iPhone Safari
4. Add to Home Screen

## Option C — Android APK (if you want a true installable app)

1. Deploy via Option A or B first (you need a public HTTPS URL)
2. Go to **https://www.pwabuilder.com**, paste the URL
3. Click "Build" → "Android" → download the signed APK
4. Sideload to your Android phone

## Option D — Local-only (no internet)

If you're only ever using this on a single device with the file already loaded, you can:
- Open `index.html` directly in iOS Safari from Files → Add to Home Screen still works for the icon, but offline caching via the service worker requires HTTPS, so you may need to be online the first time the page loads each session.

## Files in this bundle

- `index.html` — the app
- `manifest.webmanifest` — PWA metadata
- `sw.js` — service worker for offline support
- `icon-180.png` — iOS home-screen icon
- `icon-192.png`, `icon-512.png` — Android / standard PWA icons
- `icon.svg` — source vector if you want to tweak the icon

## How to update later

Bump the `CACHE_NAME` in `sw.js` (e.g. `v1` → `v2`) whenever you change `index.html`. The service worker will fetch the new version on next launch.
