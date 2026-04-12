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

## Conventions

- All pages are self-contained static HTML (inline CSS, no build tools).
- Pages use Apple's SF Pro system font stack.
- Privacy policies must be bilingual (English + Vietnamese) with a language switcher.
- Screenshots are organized by device type (`iphone/`, `ipad/`).
- No external JS frameworks or CSS libraries — keep pages lightweight and dependency-free.

## Adding a New App

1. Create `docs/<app-name>/` directory
2. Add `index.html` (landing page) and `privacy-policy.html`
3. Add screenshots under `docs/<app-name>/screenshots/`
4. Update this file with the new app's details
