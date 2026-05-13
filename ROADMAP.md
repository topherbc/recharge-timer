# Recharge Timer — ROADMAP

## Vision

Recharge Timer is a cognitive reset tool — not just a break timer. It combines timed breaks with theta-wave binaural beats, content cards for cognitive deloading, and a clean UI designed for screen sharing in classrooms, meetings, and co-working sessions. The goal is to help people genuinely reset their minds during breaks, not just count down the seconds.

**Target audiences:**
- Teachers & classrooms (brain breaks, screen projection)
- Remote workers & developers (focus/reset cycles)
- Meeting facilitators (timed breaks with a shared screen)
- Anyone who wants breaks that actually recharge

**Key differentiators:**
- Binaural beats tuned for cognitive reset (not generic white noise)
- Post-break content cards: trivia, prompts, facts, comics, GIFs — cognitive deloading through novelty
- Classroom-ready: `?muted=true` URL param, clean projection-friendly UI
- Zero accounts, zero tracking cookies, fully client-side

---

## Pre-Launch: Features

### Expandable Timer Presets

**Current state:** 3 fixed presets (short, medium, lunch) + custom timer input.

**Target:** 6-8 configurable preset slots.
- Users can add new presets, edit existing ones (label + duration), or remove them
- Default presets remain as starting point (short/medium/lunch)
- Cap at 6-8 to keep the selection screen clean and projection-friendly
- All stored in localStorage (`recharge_breaks`)
- UI: add button appears when under the cap, each preset has an edit/remove affordance

### Suggestion Form

**Current state:** No way for users to submit feedback or content ideas.

**Target:** A "Suggestions" section in the info modal.
- Simple form or link (Google Form / mailto) where users can suggest:
  - New GIFs, images, or memes
  - Spark prompts or "clear mind" statements
  - Trivia questions
  - Feature requests
- Lightweight — no backend, no database
- Placeholder for future full content bank feature (see Future Features below)

### Spark Library (Custom Post-Break Content)

**Current state:** 510 built-in content cards ("sparks") across 7 categories: spark (180), gif (160), xkcd (65), weirdfact (30), realtalk (30), meme (25), trivia (20). No way for users to customize.

**Target:** A "Spark Library" panel accessible from within the Settings modal.
- Opens as a larger modal/panel when clicking a "Spark Library" button in Settings
- Shows all content organized by category section (Sparks, GIFs, XKCD, Weird Facts, Real Talk, Memes, Trivia)
- Each section has a master toggle to enable/disable the entire category
- Each individual spark within a section has its own toggle to include/exclude it
- At the bottom: an "Add Spark" area where users can add their own content
  - Support for text, image URL, or GIF URL
  - User-added sparks stored in localStorage
  - User sparks appear in their own "My Sparks" section at the top
- Disabled built-in sparks tracked in localStorage (exclusion list, not a copy of all 510)
- Disabled sparks are skipped during the random draw; pool counter updates accordingly

---

## Pre-Launch: SEO Strategy

### Positioning & Keywords

Recharge Timer is NOT competing with generic "pomodoro timer" or "countdown timer" apps. It occupies a distinct niche: **cognitive reset tools with binaural beats, designed for classroom and workplace use.**

**Primary keyword clusters:**

| Cluster | Target Keywords |
|---------|----------------|
| Cognitive reset | cognitive reset timer, mental recharge break, brain reset tool, mind reset timer |
| Classroom/education | brain break timer for classroom, classroom break timer, teacher break timer tool, student brain break |
| Binaural/theta | theta wave break timer, binaural beats timer, focus reset with binaural beats, theta wave study timer |
| Mindful breaks | mindful break timer, work break timer with sounds, decompression timer, stress relief break timer |

### Title Tag
```
Recharge Timer — Brain Reset & Cognitive Break Timer with Theta Waves
```

### Meta Description
```
Free cognitive reset timer with theta-wave binaural beats and content cards for mental deloading.
Designed for classrooms, remote workers, and anyone who wants breaks that actually recharge.
No ads, no accounts, no tracking.
```

### Technical SEO Checklist

- [ ] `<meta name="description">` with keyword-rich copy
- [ ] `<meta name="theme-color" content="#E8900A">`
- [ ] `<link rel="canonical" href="https://recharge-timer.com/">`
- [ ] Open Graph tags (og:title, og:description, og:image, og:url, og:type)
- [ ] Twitter Card tags (summary_large_image)
- [ ] `<meta name="keywords">` (for Bing)
- [ ] Structured data: JSON-LD with `WebApplication` + `EducationalResource` schemas
- [ ] `<noscript>` block with keyword-rich fallback text for crawlers
- [ ] Semantic HTML: wrap content in `<main>`, `<header>`, `<section>`, proper `<h1>`
- [ ] `robots.txt` with sitemap reference
- [ ] `sitemap.xml` with lastmod date
- [ ] PWA `manifest.json` linked in `<head>`
- [ ] `<link rel="apple-touch-icon">`
- [ ] Image assets: og-image.png (1200x630), apple-touch-icon.png (180x180), icon-192.png, icon-512.png

### Performance SEO (Core Web Vitals)

- [ ] Defer non-critical JavaScript
- [ ] Preload Google Fonts
- [ ] Minimize layout shift (CLS) on initial load
- [ ] Run Lighthouse audit post-launch, fix anything below 90

### Post-Launch SEO Actions

- [ ] Submit sitemap to Google Search Console
- [ ] Submit sitemap to Bing Webmaster Tools
- [ ] Submit to Product Hunt
- [ ] Submit to AlternativeTo (alternative to: Pomodoro Timer, Break Timer, etc.)
- [ ] Submit to teacher tool directories and education resource sites
- [ ] Monitor Search Console for query data, optimize title/description based on actual search terms

---

## Pre-Launch: Hosting & Domain

### Custom Domain Setup

**CNAME file:** Create `/CNAME` containing `recharge-timer.com`

**Squarespace DNS records:**

| Type  | Host | Value               |
|-------|------|---------------------|
| A     | @    | 185.199.108.153     |
| A     | @    | 185.199.109.153     |
| A     | @    | 185.199.110.153     |
| A     | @    | 185.199.111.153     |
| CNAME | www  | topherbc.github.io  |

**GitHub Pages settings:**
1. Settings > Pages > Custom domain: `recharge-timer.com`
2. Enable "Enforce HTTPS" (wait for Let's Encrypt cert, ~minutes)

**Code changes:**
- Fix favicon path: `/recharge-timer/favicon.svg` → `/favicon.svg` (line 7 of index.html)
- No other path changes needed — `APP_BASE` and GIF refs already handle root deployment

**Notes:**
- DNS propagation: up to 48 hours (usually much faster)
- Old `topherbc.github.io/recharge-timer` URLs auto-redirect to custom domain
- HTTPS cert auto-provisions via Let's Encrypt after DNS resolves

### New Files

| File | Purpose |
|------|---------|
| `CNAME` | Custom domain for GitHub Pages |
| `robots.txt` | Search engine crawling rules |
| `sitemap.xml` | Search engine sitemap |
| `manifest.json` | PWA web app manifest |
| `.github/FUNDING.yml` | GitHub Sponsors/donate button on repo |
| `og-image.png` | Social share preview (1200x630) |
| `apple-touch-icon.png` | iOS home screen icon (180x180) |
| `icon-192.png` | PWA icon |
| `icon-512.png` | PWA icon |

---

## Pre-Launch: Analytics

### Cloudflare Web Analytics

- **Cost:** Free
- **Privacy:** No cookies, no personal data collection, no GDPR banner needed
- **Tracks:** Page views, unique visitors, Core Web Vitals (LCP, FID, CLS), referrers, device/browser/OS, country
- **Does NOT track:** Custom events (button clicks, which break types are used, etc.)

**Setup:**
1. Sign up at cloudflare.com
2. Add site, get beacon token
3. Add to `index.html` before `</body>`:
```html
<script defer src='https://static.cloudflareinsights.com/beacon.min.js'
        data-cf-beacon='{"token": "YOUR_TOKEN"}'></script>
```

**Note:** If custom event tracking becomes important later (understanding which break types are popular, completion rates, etc.), GoatCounter can be added alongside Cloudflare at no cost for non-commercial use.

---

## Pre-Launch: Monetization

### PayPal Donate Link

- **Single link** reusable across all future apps/projects
- **No platform fee** beyond standard PayPal processing (~2.9% + $0.30)
- **No account required** for donors (can pay with card)

**Placement:** Bottom of the info modal ("How It Works")
```
"Recharge Timer is free and always will be."
[☕ Support this project] → links to PayPal.me/USERNAME
```
Styled with existing CSS variables so it matches all themes.

### GitHub FUNDING.yml

Create `.github/FUNDING.yml`:
```yaml
custom: https://paypal.me/USERNAME
```
This adds a "Sponsor" button to the GitHub repository page.

---

## Future Features (Post-Launch)

### Content Bank
Users can upload their own images, GIFs, and text prompts to customize the post-break content cards. Toggle built-in categories on/off. All stored locally in the browser.

### Live Sharing / Classroom Projection
Enhanced features for shared-screen use: synced timers, presenter controls, simplified projection mode.

### Service Worker / Offline Support
Cache the app for offline use. Low priority since it's a single HTML file, but improves PWA install experience.

### Additional Binaural Beat Modes
Multiple beat presets tuned for different purposes:
- **Reset** (theta): default, for cognitive deloading during breaks
- **Focus** (gamma/beta): for getting back into work after a break
- **Calm** (alpha): for stress relief or longer breaks

---

## Implementation Order

1. **Expandable presets** — configurable timer slots
2. **Spark Library** — custom post-break content management
3. **Suggestion form** — info modal addition
4. **SEO + meta tags + structured data** — all the `<head>` changes
5. **Hosting files** — CNAME, robots.txt, sitemap.xml, manifest.json, icons
6. **Analytics** — Cloudflare beacon
7. **Monetization** — PayPal button in info modal, FUNDING.yml
8. **DNS + GitHub Pages config** — point domain, enable HTTPS
9. **Post-launch** — Search Console, Bing, Product Hunt submissions
