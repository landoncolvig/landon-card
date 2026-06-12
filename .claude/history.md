# Project History

## 2026-05-30 15:25 — Card v2: Editorial Restyle + Desktop Layout

### Issue / Task
The existing dark-theme contact card (deployed via this repo at `card.daytanalytics.com`) didn't match the new `daytanalytics.com` marketing site's aesthetic. Landon wanted styling-only changes (no structural rework) so the card looked like part of the Dayta brand system, and asked to make it look good on web + mobile.

### Actions Taken
1. **Restyled to match marketing site:**
   - Swapped color system: black bg → cream `#F4EDDC` paper, white text → ink `#0A0908`
   - Swapped fonts: system stack → Fraunces (display) + IBM Plex Sans (body) + IBM Plex Mono (labels)
   - Replaced conic-gradient halo on avatar with hairline ink border + double-ring effect via box-shadow
   - Replaced rounded dark-surface buttons with hairline-separated rows (ink-outline icon squares, mono uppercase sublabels)
   - Primary CTA inverted: dark ink fill, cream text, ~24px padding, extends slightly beyond column edge
   - Added subtle SVG noise grain via `body::before` (matches marketing site)
   - Added DAYTA wordmark as top brand bar with hairline-bottom rule

2. **Bumped text sizes** (per Landon's feedback that the restyle was too small):
   - Pitch body 15px → 17px
   - Credentials body 14px → 16px
   - Button label 16px → 18px, sublabels 10.5px → 12px
   - Title 11px → 12.5px
   - Footer sig 13px → 16px

3. **Removed visual pinch:** the actions section had `border-top:1px solid var(--ink)` that ran into the dark primary CTA's left/right negative margin, creating an awkward "black box pinched against rule" effect. Removed the border-top.

4. **Trimmed redundant copy:**
   - Dropped eyebrow `Founder, est. Jan 2024` (redundant with title below)
   - Dropped brand-bar meta `Contact Card · Vol. 02` (kept just DAYTA logo + accent dot)
   - Dropped button sublabels that didn't add info (`Adds to your phone instantly`, `What we do`)
   - Dropped footer signature `Dayta Analytics` (redundant with wordmark up top)

5. **Desktop layout:**
   - Vertically centers card on viewport at `>=760px`
   - Hairline ink border + 18px offset shadow + editorial corner marks
   - Max-width 560px on desktop, 520px on mobile
   - Body uses flex column with `justify-content: center` on desktop

### Files Modified
- `index.html` — full restyle of inline `<style>` block + minor HTML changes (added brand bar, trimmed eyebrow/subs)
- `logo.png` — added (copied from marketing site repo)
- `CNAME` — unchanged (`card.daytanalytics.com`)

### Key Findings
- Playwright `--viewport=WxH` flag wasn't being honored by the playwright-test skill — both 390-wide and 1440-wide captures came back at 3810px wide. Real mobile QA required osascript to resize an actual Chrome window
- Headless Chrome `--window-size` also unreliable — captured at wider effective viewport than specified, leading me to think the mobile layout had clipping bugs that didn't actually exist
- The fix: use osascript to position/size a real Chrome window, then `screencapture -R<x>,<y>,<w>,<h>`

### Outstanding
- Pushed and live at `https://card.daytanalytics.com` (HTTPS already enforced from previous session)
- Lock screen wallpaper PNG was not regenerated to match the new aesthetic — it still uses the old black-background design with white QR card. Functionally fine (the QR scan still goes to the same URL) but doesn't visually match the new card. Worth regenerating if Landon wants brand consistency on his physical phone wallpaper

---

## 2026-06-11 20:40 - Session Summary
Session in landon-card - no detailed summary available

---

## 2026-06-11 20:41 - Session Summary
Session in landon-card - no detailed summary available

---
