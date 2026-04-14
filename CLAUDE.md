# pocket-docs

Public-facing documentation and landing pages for mobile apps, hosted via GitHub Pages or similar static hosting. These pages are linked from App Store / Google Play listings (privacy policy URLs, marketing pages, etc.).

## Repository Structure

```
docs/
  <app-name>/
    index.html          — Landing/marketing page
    privacy-policy.html — Privacy policy (required by app stores)
    screenshots/        — App screenshots used on the landing page
      iphone/
      ipad/
tools/
  screenshot-generator.html           — Browser-based App Store screenshot framing tool (Odo Max)
  screenshot-generator-tidysnap.html  — Browser-based App Store screenshot framing tool (Tidy Snap)
  screenshot-generator-chia.html     — Browser-based App Store screenshot framing tool (Chia)
```

## Current Apps

### Odo Max
- **Landing page:** `docs/odo-max/index.html`
- **Privacy policy:** `docs/odo-max/privacy-policy.html`
- **App Store:** https://apps.apple.com/vn/app/odo-max/id6761961579
- **Source code repo:** `/Users/huy.vu/Documents/Workspace/side-projects/speedometer/speedometer` — the actual iOS/iPadOS Swift project for Odo Max. Refer to this repo for app features, architecture, and implementation details when refining landing page copy or privacy policy content.
- **Description:** Free GPS speedometer app for iPhone & iPad. Real-time speed tracking, trip recording, built-in music player. No ads, no tracking, no subscriptions. 100% on-device privacy.
- **Contact email:** unamed000@gmail.com
- **Bilingual support:** Privacy policy and landing pages support English and Vietnamese.

### Tidy Snap
- **Landing page:** `docs/tidysnap/index.html`
- **Privacy policy:** `docs/tidysnap/privacy-policy.html`
- **Screenshot generator:** `tools/screenshot-generator-tidysnap.html`
- **App Store:** https://apps.apple.com/us/app/tidy-snap/id6762082915
- **Source code repo:** `/Users/huy.vu/Documents/Workspace/side-projects/pocket/Pocket Tidy/Pocket Tidy` — the actual iOS/iPadOS Swift project for Tidy Snap.
- **Description:** Free photo library decluttering app for iPhone & iPad. Tinder-style card swiping to keep or bin photos, dashboard with stats and 7-day activity chart, safe bin with restore, guided onboarding. No ads, no tracking, no subscriptions. 100% on-device privacy.
- **Contact email:** unamed000@gmail.com
- **Bilingual support:** Privacy policy supports English and Vietnamese. App supports English, Vietnamese, Japanese, and Simplified Chinese.
- **Branding:** Dark mode with pink-to-orange gradient primary accent (#ff6b8a → #ff8a50), green-to-mint secondary (#34d399 → #6ee7b7). Rounded typography, glassmorphism aesthetic.

### Chia
- **Landing page:** `docs/chia/index.html`
- **Privacy policy:** `docs/chia/privacy-policy.html`
- **Screenshot generator:** `tools/screenshot-generator-chia.html`
- **App Store:** https://apps.apple.com/app/chia-chi/id6762182642
- **Source code repo:** `/Users/huy.vu/Documents/Workspace/side-projects/chungchi/Chia` — the actual iOS/iPadOS Swift project for Chia.
- **Description:** Free bill-splitting and expense tracking app for iPhone & iPad. Create sessions for trips or events, add group members, track expenses and upfront funding, view per-member balance reports, export settlement summaries. Supports 9 currencies (VND, USD, EUR, JPY, KRW, THB, GBP, AUD, SGD). No ads, no tracking, no subscriptions. 100% on-device privacy with optional iCloud sync via CloudKit.
- **Contact email:** unamed000@gmail.com
- **Bilingual support:** Landing page and privacy policy support Vietnamese (primary) and English, with inline language toggle. Screenshot generator has a Vietnamese/English switcher for marketing copy. App supports English and Vietnamese.
- **Branding:** Dark mode with blue-to-purple gradient primary accent (#668EF5 → #AD6BF5). Secondary colors: green (#33B873) for positive balances/funding, orange (#F38C33) for expenses, red (#EB5757) for negative balances. App icon: three blue hands in Y-formation around a central "$" circle on white background.

## Tools

### Screenshot Generator (`tools/screenshot-generator.html`)

A self-contained browser-based tool for generating App Store marketing screenshots. Open it directly in a browser — no server needed.

**Concept:** Takes raw app screenshots and wraps them in polished marketing frames with gradient backgrounds, headlines, sublines, and optional badges. Outputs images at exact App Store required resolutions.

**How it works:**
- **Two tabs:** iPhone (5 slots) and iPad (6 slots), matching App Store screenshot requirements.
- **Output resolutions:** iPhone 6.7" = 1284×2778px, iPad 12.9" = 2064×2752px.
- **Per-slot configuration** (editable via modal):
  - `headline` — large bold text (supports `\n` for line breaks)
  - `subline` — smaller description text below headline
  - `badge` — optional pill badge at top (e.g. "FREE"), uses green-to-cyan gradient
  - `gradient` — 3-stop background gradient colors (dark theme by default)
- **Image count per slot:** 1, 2, or 3 screenshots per frame with different layouts:
  - **1 image:** centered, large, with rounded corners and shadow
  - **2 images:** side-by-side with slight opposite tilt (~2°)
  - **3 images:** fan layout — center image is the hero (large, no tilt), sides are 85% scale with ~4° tilt
- **Rendering:** Uses HTML5 Canvas API. Each frame draws: gradient background → radial glow → badge → headline → subline → screenshot(s) with rounded corners, shadows, borders → bottom fade.
- **Output:** Individual PNG downloads per frame, or "Download All as ZIP" (uses JSZip CDN).
- **Drag-and-drop:** Supports dropping multiple images onto a slot at once.
- **File naming:** `{device}_{index}_{slotId}.png` (e.g. `iphone_1_ip1.png`).

**To create this tool for a new app:**
1. Copy `tools/screenshot-generator.html`
2. Update `defaultDefs` array with the new app's marketing copy (labels, headlines, sublines, badges)
3. Adjust gradient colors to match the app's branding
4. Adjust slot count if different number of screenshots needed
5. If the app has different device targets, update `IPHONE_W/H` and `IPAD_W/H` constants

## Conventions

- All pages are self-contained static HTML (inline CSS, no build tools).
- Pages use Apple's SF Pro system font stack.
- Privacy policies must be bilingual (English + Vietnamese) with a language switcher.
- Landing pages must be bilingual (Vietnamese primary, English secondary) using inline `data-lang-vi` / `data-lang-en` spans toggled via CSS/JS. Vietnamese is the default visible language.
- Screenshots are organized by device type (`iphone/`, `ipad/`).
- No external JS frameworks or CSS libraries — keep pages lightweight and dependency-free.
- All landing pages include a sticky navbar with cross-app navigation links. When adding a new app, update the navbar in all existing landing pages.
- Screenshot generators support a Vietnamese/English language switcher for marketing copy, with Vietnamese as the default.

## Adding a New App

1. Create `docs/<app-name>/` directory
2. Add `index.html` (bilingual landing page, Vietnamese primary) and `privacy-policy.html` (bilingual with language switcher)
3. Add screenshots under `docs/<app-name>/screenshots/iphone/` and `screenshots/ipad/`
4. Create `tools/screenshot-generator-<app-name>.html` based on the existing generator — update marketing copy (both VI and EN), gradients, slot definitions, and branding colors to match the new app
5. Update navbar links in **all existing** landing pages (`docs/*/index.html`) to include the new app
6. Update this file with the new app's details
