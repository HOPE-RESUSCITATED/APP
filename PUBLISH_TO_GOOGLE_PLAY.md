# Publishing Narcan Partner to Google Play
## Hope Resuscitated — Step-by-Step Guide

---

## What You Have (Your PWA is Ready ✅)

- ✅ `manifest.json` — configured correctly
- ✅ `index.html` — app structure complete
- ✅ App icon (512x512)
- ✅ Feature graphic (1024x500)
- ✅ Step screenshots (step1–step8)
- ✅ `sw.js` — service worker (NEW — add this to your repo)
- ⚠️ Service worker registration — added to `index.html` (see updated file)

---

## Step 1: Deploy Your PWA to HTTPS

Your app must be live at a public HTTPS URL. Easiest free options:

### Option A: GitHub Pages (Recommended — Free)
1. Go to your GitHub repo: `github.com/HopeResuscitated/APP`
2. Settings → Pages → Source: `main` branch, `/NarcanPWA` folder
3. Your URL will be: `https://hoperesuscitated.github.io/APP/NarcanPWA/`

### Option B: Netlify (Also Free)
1. Go to [netlify.com](https://netlify.com) → "Add new site" → "Deploy manually"
2. Drag and drop your `NarcanPWA` folder
3. You get a free URL like `https://narcan-partner.netlify.app`

**Before moving on:** Open the live URL in Chrome → DevTools → Lighthouse → Run PWA audit. All checks should pass.

---

## Step 2: Add Updated Files to Your Repo

Copy these two files (included in this package) into your `NarcanPWA` folder:

| File | What Changed |
|------|-------------|
| `sw.js` | **NEW** — Service worker for offline support |
| `index.html` | Added SW registration + iOS meta tags |
| `manifest.json` | Added `orientation`, `categories`, `shortcuts` |

Commit and push to GitHub. If using GitHub Pages, it will auto-deploy.

---

## Step 3: Package with PWABuilder (Free, No Android Studio)

1. Go to **[pwabuilder.com](https://www.pwabuilder.com)**
2. Enter your live URL → click **Start**
3. Wait for it to analyze your PWA (should score green on all checks)
4. Click **Package for stores → Android**
5. Fill in the form:

| Field | Value |
|-------|-------|
| Package ID | `com.hoperesuscitated.narcanpartner` |
| App name | `Narcan Partner — Hope Resuscitated` |
| App version | `1.0.0` |
| App version code | `1` |
| Signing | Choose **"Let PWABuilder generate"** |

6. **IMPORTANT:** Save the generated `.keystore` file somewhere safe — you need it forever for all future updates.
7. Download the `.zip` — it contains your `.aab` file (Android App Bundle)

---

## Step 4: Set Up Digital Asset Links (Required!)

This tells Android that your app "owns" your website domain.

1. In the PWABuilder download, find `assetlinks.json`
2. Host it at: `https://your-domain.com/.well-known/assetlinks.json`

For GitHub Pages, create a file at:
```
NarcanPWA/.well-known/assetlinks.json
```

The content will look like:
```json
[{
  "relation": ["delegate_permission/common.handle_all_urls"],
  "target": {
    "namespace": "android_app",
    "package_name": "com.hoperesuscitated.narcanpartner",
    "sha256_cert_fingerprints": ["YOUR_FINGERPRINT_FROM_PWABUILDER"]
  }
}]
```

---

## Step 5: Create Google Play Developer Account

1. Go to [play.google.com/console](https://play.google.com/console)
2. Sign in with a Google account
3. Pay the one-time **$25 registration fee**
4. Complete identity verification (takes 1–3 days for new accounts)

---

## Step 6: Create Your App in Play Console

1. Click **Create app**
2. Fill in:
   - App name: `Narcan Partner`
   - Default language: English (US)
   - App or game: **App**
   - Free or paid: **Free**
3. Accept declarations → **Create app**

---

## Step 7: Complete the Store Listing

Navigate to **Store presence → Main store listing**

### App Info
- **Short description** (80 chars max):
  > Step-by-step overdose response guide for administering Naloxone/Narcan.

- **Full description** (4000 chars max):
  > Narcan Partner by Hope Resuscitated is a free, offline-capable emergency guide for responding to opioid overdoses. When every second counts, this app walks you through each step — from checking responsiveness to administering Narcan (naloxone) — with clear instructions, timers, and checklists.
  >
  > Features:
  > • Emergency Response Mode — guided step-by-step overdose response
  > • Practice Mode — learn the steps before an emergency
  > • Built-in timers for observation and dose intervals
  > • Dose tracking (up to 3 doses)
  > • Works offline — no internet required in an emergency
  > • Free, no ads, no accounts
  >
  > DISCLAIMER: This app is for educational purposes only. Always call 911 in an emergency. This app does not replace professional medical advice or training.

### Graphics
Upload these files (already in your project):

| Asset | File | Required Size |
|-------|------|---------------|
| App icon | `app_icon_512.png` | 512×512 |
| Feature graphic | `feature_graphic.png` | 1024×500 |
| Phone screenshot 1 | `step1.png` | Min 320px wide |
| Phone screenshot 2 | `step2.png` | |
| Phone screenshot 3 | `step3.png` | |
| Phone screenshot 4 | `step4.png` | |
| Phone screenshot 5 | `step5.png` | |

---

## Step 8: Complete Required Sections

### Content Rating
- Go to **Policy → App content → Content rating**
- Answer the questionnaire (this app: no violence, no mature content, public health)
- Category: **Reference**

### Target Audience
- Go to **Policy → App content → Target audience**
- Select: **18 and over** (or "All ages" — your choice)

### Health App Declaration ⚠️
Since this is a health/medical app, Google may require:
- Go to **Policy → App content → Health apps**
- Declare: This is an educational first-aid reference app, not a medical device
- Add disclaimer text to your app and store listing

### Data Safety
- Go to **Policy → App content → Data safety**
- This app collects NO user data → answer "No" to all data collection questions

---

## Step 9: Upload Your App Bundle

1. Go to **Release → Production → Create new release**
2. Upload your `.aab` file from PWABuilder
3. Add release notes:
   > Initial release of Narcan Partner — overdose response guide.
4. Click **Review release** → **Start rollout to Production**

---

## Step 10: Wait for Review

- First-time submissions: **3–7 business days**
- Google may ask follow-up questions for health apps
- You'll receive email updates on approval status

---

## Checklist Summary

- [ ] Deploy PWA to HTTPS URL
- [ ] Add `sw.js` to repo
- [ ] Update `index.html` with SW registration
- [ ] Update `manifest.json`
- [ ] Run Lighthouse PWA audit — all green
- [ ] Package with PWABuilder → get `.aab` + save `.keystore`
- [ ] Host `assetlinks.json` at `/.well-known/assetlinks.json`
- [ ] Create Google Play Developer account ($25)
- [ ] Create app in Play Console
- [ ] Complete store listing with all graphics
- [ ] Complete content rating, target audience, data safety
- [ ] Upload `.aab` and submit for review

---

## Helpful Links

- PWABuilder: https://pwabuilder.com
- Google Play Console: https://play.google.com/console
- PWA Checklist: https://web.dev/pwa-checklist
- Digital Asset Links tester: https://developers.google.com/digital-asset-links/tools/generator

---

*Built with care for the Hope Resuscitated mission. Every life matters.*
