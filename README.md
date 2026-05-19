# Tinnitus Noise Therapy & Tracker

A single-file web app for slow-ramp noise exposure therapy with progress tracking.
Everything lives in `index.html` — no install, no build, works offline.

## What it does

- **Therapy tab** — generates white / pink / brown / green noise that ramps **slowly
  up** to a target level, **holds**, then eases **back down**. A big **Stop & Cool
  Down** button fades it out gently over a configurable time whenever he stops
  manually. A live graph plots volume as **0–100%** against time, showing both the
  planned envelope and the actual played curve.
- **Log tab** — a monthly calendar. Tap any day to rate **pain / ringing / headache
  (0–5)**, mark that a **loud noise set off the tinnitus** (with a note), and mark
  when **ears returned to baseline** (it shows days since the last trigger). Days are
  colour-coded by severity; 🔔 = trigger, ✓ = baseline.
- **Analytics tab** — peak % per session over time (the main progress signal),
  total exposure, sessions per week, and symptom trends with trigger/baseline markers.
- **Settings tab** — envelope defaults, data backup, disclaimer.

## Running it on a phone

Pick one:

1. **Host it (recommended).** Drag the folder onto <https://app.netlify.com/drop>,
   or push to a GitHub repo and enable GitHub Pages. Open the URL on the phone, then
   use the browser's **Add to Home Screen** for a full-screen, app-like launch.
2. **Local file.** Send `index.html` to the phone (email/AirDrop/cloud) and open it
   in the browser. Works, but no home-screen install.

On **iPhone**: turn the silent/ring switch **off silent** or audio may not play.
Don't manually lock the screen mid-session — the app keeps the screen awake where
the browser supports it, but iOS can still suspend audio if locked.

## How volume works (important)

A web app **cannot read or set the phone's volume** — no browser exposes that, and
iOS blocks it entirely. So the model is: **set the phone volume once** to a
comfortable maximum and never touch it again. The app does the entire slow ramp
digitally. Don't also hand-adjust the phone mid-session — doing both throws off the
graph and progress history.

Volume is shown as **0–100%**, scaled by perceived loudness (so the slow ramp feels
gradual the whole way, not silent-then-sudden). 100% is the app's full output at the
phone volume you set. Because it's the same headphones and a fixed phone volume every
time, % is **consistent session to session** — a reliable way to track progress. It
is *not* a real-world decibel measurement.

## Backing up data

All data is stored only in this browser (`localStorage`). It is lost if browser
data is cleared or you switch devices/browsers.

- **Settings → Export backup** downloads a dated JSON file. Do this regularly.
- **Settings → Import** restores from a backup (replaces all current data).

## ⚠ Medical disclaimer

This is a personal self-tracking aid, **not a medical device**. The 0–100% scale is
relative to the app's output at your phone volume, not a real-world loudness
measurement. Follow the audiologist's prescribed program and volume limits. If pain,
ringing, or hearing worsens, stop and consult the clinician.
