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

---

## Pre-Launch: Binaural Beat Research & Optimization

### Current Implementation

- **Beat frequency:** 40 Hz (gamma range)
- **Carrier frequency:** 200 Hz (left ear), 240 Hz (right ear)
- **UI label:** "Binaural beat (40 Hz · requires headphones)"
- **Volume:** User-adjustable, default 50%
- **Behavior:** Plays continuously during timer, stops when timer ends or is cancelled

### The Problem

40 Hz is in the **gamma** range (30-100 Hz), associated with active cognition and focus. For a cognitive *reset* tool, this may not be optimal. The app's purpose is relaxation and mental deloading during breaks — theta (4-8 Hz) or alpha (8-12 Hz) ranges may be better suited.

### Research Tasks

1. **Optimal frequency for cognitive reset during short breaks**
   - Compare theta (4-8 Hz), alpha (8-12 Hz), and gamma (40 Hz)
   - Context: sessions are 5-30 minutes, goal is mental reset not deep meditation
   - Key question: which frequency range has the most evidence for rapid relaxation onset?

2. **Duration-dependent frequency selection**
   - Should a 5-minute break use a different frequency than a 30-minute break?
   - Does theta require longer exposure to be effective?

3. **Carrier frequency optimization**
   - Current: 200 Hz. Literature may support 400-440 Hz as more effective/comfortable
   - Impact on perceived tone quality and beat perception

4. **Fade-in/fade-out patterns**
   - Does ramping volume/frequency over the first 30-60 seconds improve relaxation onset?
   - Should the beat fade out before the timer ends to ease transition back?

5. **Layering with ambient sound**
   - Would adding pink noise, brown noise, or nature sounds alongside the binaural beat improve outcomes?
   - Or does it interfere with beat perception?

6. **Safety considerations**
   - Contraindications (epilepsy, seizure disorders)
   - Maximum recommended session duration
   - Whether a disclaimer is needed in the UI

### Research Findings

> **Note:** Citations marked [HIGH] are well-established references. Those marked [MODERATE] should be verified via PubMed or Google Scholar before citing publicly. PMIDs are included where known.

#### 1. Optimal Frequency for Cognitive Reset

40 Hz (gamma) promotes active cognition and focus — the opposite of what a reset break needs. Alpha (8-12 Hz) and theta (4-8 Hz) are associated with relaxation and mental downshifting.

**Sources:**
- Chaieb, Wilpert, Reber & Fell (2015). "Auditory Beat Stimulation and its Effects on Cognition and Mood States." *Frontiers in Psychiatry*, 6, 70. — Alpha beats linked to reduced anxiety; theta to meditative states; gamma enhanced attention/memory. [HIGH — PMID: 26074823]
- Garcia-Argibay, Santed & Reales (2019). "Efficacy of binaural auditory beats in cognition, anxiety, and pain perception: a meta-analysis." *Psychological Research*, 83(2), 357-372. — Theta/alpha beats had moderate effects on anxiety reduction. [HIGH — PMID: 28900723]
- Jirakittayakorn & Wongsawat (2017). "Brain Responses to a 6-Hz Binaural Beat: Effects on General Theta Rhythm and Frontal Midline Theta Activity." *Frontiers in Neuroscience*, 11, 365. — 6 Hz theta beats increased frontal midline theta, associated with meditative relaxation. [MODERATE]

#### 2. Duration-Dependent Frequency

Entrainment effects take several minutes to manifest, suggesting frequency should match session length.

- **Short breaks (5 min):** Alpha (10 Hz) — quick onset, light disengagement
- **Medium breaks (15 min):** Low-alpha/high-theta (7-8 Hz) — deeper relaxation
- **Long breaks (30 min):** Theta (6 Hz) — enough time for deep meditative rest

**Source:**
- Lavallee, Koren & Bhargava (2011). "A quantitative electroencephalographic study of meditation and binaural beat entrainment." *J of Alternative and Complementary Medicine*, 17(4), 351-355. — Entrainment requires several minutes to establish. [MODERATE — verify details]

#### 3. Carrier Frequency

400-440 Hz produces more clearly perceived binaural beats than 200 Hz.

**Sources:**
- Oster (1973). "Auditory Beats in the Brain." *Scientific American*, 229(4), 94-102. — Foundational paper; beats most clearly perceived at 400-500 Hz carriers. [HIGH]
- Pratt et al. (2010). "A comparison of auditory evoked potentials to acoustic beats and to binaural beats." *Hearing Research*, 262(1-2), 34-44. — Lower carriers (~250 Hz) produced weaker cortical responses than ~400 Hz. [MODERATE]

#### 4. Fade-In/Fade-Out

Abrupt tone onset triggers alerting/startle responses that counteract relaxation. Most studies use 30-60 second fade-in periods.

**Source:**
- Reedijk, Bolders & Hommel (2013). "The impact of binaural beats on creativity." *Frontiers in Human Neuroscience*, 7, 786. — Used gradual onset; noted abrupt stimuli disrupt intended cognitive states. [HIGH study existence, MODERATE exact citation]

#### 5. Sound Layering

Pink noise and nature sounds independently promote relaxation and may be additive with binaural beats. Pink noise preferred over white noise (less high-frequency energy). Masking also reduces listener fatigue from pure tones.

**Sources:**
- Alvarsson, Wiens & Nilsson (2010). "Stress Recovery during Exposure to Nature Sound and Environmental Noise." *Int J of Environmental Research and Public Health*, 7(3), 1036-1046. — Nature sounds accelerated physiological stress recovery. [HIGH — PMID: 20617017]
- Padmanabhan, Hildreth & Laws (2005). "Binaural beat audio and pre-operative anxiety." *Anaesthesia*, 60(9), 874-877. — Binaural beats embedded in nature sounds significantly reduced anxiety. [HIGH — PMID: 16115248]

#### 6. Safety Considerations

- **Epilepsy/seizures:** Rhythmic auditory stimulation can theoretically trigger seizures in auditory-sensitive epilepsy. Rare but documented — include a warning.
- **Volume:** Prolonged headphone use at high volume causes hearing damage. Recommend moderate levels.
- **Alertness:** Theta-range beats should not be used while driving or operating machinery.
- **Tinnitus:** Sustained tones may aggravate tinnitus in some users.
- **Not medical treatment:** Must not be marketed as treatment for any condition.

**Source:**
- Wahbeh, Calabrese & Zwickey (2007). "Binaural Beat Technology in Humans: A Pilot Study." *J of Alternative and Complementary Medicine*, 13(1), 25-32. — No adverse effects in healthy adults; caution recommended for neurological conditions. [MODERATE-HIGH]

### Recommended Changes

| Parameter | Current | Recommended | Evidence |
|-----------|---------|-------------|----------|
| Beat frequency | 40 Hz (gamma) | 10 Hz (alpha) as default | Strong |
| Duration-adaptive | No | 10 Hz / 8 Hz / 6 Hz for short / medium / long | Moderate (extrapolated) |
| Carrier frequency | 200 Hz | 400 Hz | Moderate-Strong |
| Fade-in | None | 30-60 seconds | Moderate |
| Fade-out | None | 15-30 seconds | Moderate |
| Sound layering | None | Optional pink noise / nature sounds | Moderate |
| Safety warning | None | Add epilepsy/seizure disclaimer in UI | Established |

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

1. **Binaural beat research** — validate frequency choices before any code changes
2. **Expandable presets** — feature work
3. **Suggestion form** — info modal addition
4. **SEO + meta tags + structured data** — all the `<head>` changes
5. **Hosting files** — CNAME, robots.txt, sitemap.xml, manifest.json, icons
6. **Analytics** — Cloudflare beacon
7. **Monetization** — PayPal button in info modal, FUNDING.yml
8. **DNS + GitHub Pages config** — point domain, enable HTTPS
9. **Post-launch** — Search Console, Bing, Product Hunt submissions
