# lil svensk björn 🐻

A self-contained, offline-first PWA for learning Swedish (A1–C2), built as a personal study tool ahead of a move to Sweden. No backend, no build step, no dependencies — a single HTML file with vanilla JS and `localStorage`.

**[Live demo](https://TU-USUARIO.github.io/svensk-bjorn/)** · installable on iOS / Android / desktop

---

## Features

- **Vocabulary** across 15+ topics (everyday life, food, home, work, nature, feelings, clothes, numbers, family…), each tagged by CEFR level (A1–C2) and filterable per user
- **Spaced repetition (Leitner system)** — words move through 6 boxes (`[0,1,2,4,8,16]`-day intervals) based on recall success
- **Flashcards with images** — meaning is shown as an image on the answer side, not the Swedish word, to force picture → word association instead of translation-by-habit
- **Phrases, not just words** — ~80 everyday sentences (Duolingo-style) across all levels
- **Grammar module** — pronouns, en/ett, word order, negation, prepositions, questions, adjective agreement — each with a bilingual explanation and drills
- **Verb conjugation drills** — 4 conjugation groups, 30 verbs, present/past/supine/imperative
- **Reading comprehension** — graded texts (A1–B2) with inline comprehension questions
- **Translation & writing exercises** — Cambridge-style: SV→ES / ES→SV translation, plus free writing prompts with a model answer for self-check
- **Word of the Day**, XP/leveling, daily goal ring, streaks, badges
- **PDF export** of each day's newly learned flashcards (via `window.print()` + print stylesheet)
- **Multiple local profiles** — family members can use the same install with independent progress, levels and stats (profiles are device-local, not accounts — see [Notes](#notes))
- **Export/import** progress as JSON for backup or device migration
- **Installable PWA** — manifest + icons, works fully offline once loaded

## Tech

Single-file architecture by design — avoids any build tooling and keeps the app `file://`-safe and trivially hostable as a static site.

| | |
|---|---|
| Stack | HTML + CSS + vanilla JS (no framework, no bundler) |
| Persistence | `localStorage`, namespaced per profile |
| Content | Plain JS data objects (vocab, phrases, grammar, texts, verbs) — easy to extend |
| Audio | Browser `SpeechSynthesis` API (`sv-SE`) |
| Offline | Static PWA manifest + app icons, no service worker required for current scope |

## Repo contents

| File | Purpose |
|---|---|
| `index.html` | The entire app |
| `manifest.json` | PWA install metadata |
| `icon.svg`, `icon-192.png`, `icon-512.png` | App icon |
| `.nojekyll` | Tells GitHub Pages to serve files as-is |

Open `index.html` directly for local/offline use — no server needed.

## Deploy (GitHub Pages)

1. Push this repo to GitHub (public repos get Pages for free).
2. **Settings → Pages → Source:** Deploy from a branch → **Branch: `main`**, folder **`/ (root)`** → Save.
3. Wait ~1 min, reload the Pages settings page — your URL will appear:
   `https://TU-USUARIO.github.io/svensk-bjorn/`

## Install as an app

- **iPhone (Safari):** Share → Add to Home Screen
- **Android (Chrome):** ⋮ menu → Install app / Add to Home Screen
- **Desktop (Chrome/Edge):** Install icon in the address bar

## NFC tag (optional)

Write the Pages URL to an NFC sticker with an app like **NFC Tools**: Write → Add a record → URL/URI → paste the URL → Write. Tapping the tag then opens the app directly.

## Notes

- Progress is stored **per browser/device**, in `localStorage` — nothing is synced to a server.
- In-app **profiles** let multiple people share one device with separate stats, but this is a convenience layer, not real account isolation — for genuinely independent progress, use separate devices.
- **Framsteg → Export/Import** gives a JSON backup, useful when switching devices.
- Content level filters (A1–C2) are adjustable per profile under **Lär → Ordförråd**.

---

Built as a personal project to go from A2 to B1 Swedish before moving to Sweden. Hej då! 🐻
