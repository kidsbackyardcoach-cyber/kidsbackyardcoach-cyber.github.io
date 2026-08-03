# Backyard Coach

**English** · [中文](README.zh.md) · [Español](README.es.md)

**12-week practice plans for parents coaching soccer, t-ball, flag football, and basketball to 3–5 year olds — even if you've never played the sport yourself.**

Available in English, 中文 (Simplified Chinese), and Español.

[**→ Open the app**](https://kidsbackyardcoach-cyber.github.io/)

---

## What this is

Most youth sports resources assume you already know the sport and already know how to run a session. This one assumes neither. It answers the two questions a parent actually has on a Saturday morning:

1. **What do I buy?** — checklists by priority, with rough prices and an explicit "don't buy this yet" list
2. **What do we actually do for the next 25 minutes?** — a full season of sessions, with a timer

Everything is built around one constraint: **a four-year-old's attention span is about two to five minutes per activity.** Every design decision follows from that.

---

## Features

| | |
|---|---|
| **Sport primers** | Never played? Each sport gets a plain-language explanation with diagrams — the field, how a game works, how scoring works, the rules that matter, and eight terms you'll hear. Plus an honest picture of what the game actually looks like at age 4. |
| **12-week seasons** | Four sports. Two 25-minute sessions per week, in four phases from first touch to a real small-sided game. Each week has a focus and one concrete milestone to look for. |
| **56 drills** | Every drill has setup, how to play, the exact phrase to say, and how to make it easier or harder on the spot. |
| **Practice timer** | Full-screen run mode with a clock readable at arm's length in sunlight. |
| **Gear lists** | Three priority tiers, drawn illustrations, running budget total, and a list of what *not* to buy. |
| **Movement kit** | Optional ladder / hurdle / cone games that swap into any week's warm-up. |
| **Coaching guide** | Eight rules, developmental expectations, and troubleshooting for the wanderer, the meltdown, and the kid who dominates. |
| **Progress tracking** | Mark sessions done; progress saves in your browser. |

---

## The coaching principles behind it

These are load-bearing. If you change the content, keep these:

- **25 minutes, total.** A short practice that stays fun beats an hour that falls apart.
- **One ball per child.** Two kids sharing a ball means one kid touching a ball.
- **No lines, no laps, no lectures.** A child standing in a line is a child not practicing.
- **Games, not drills.** Same skill, different wrapper — only one of them works at this age.
- **Nobody ever sits out.** Elimination games produce a crying child and a ruined practice. Every game here is designed so getting caught means rejoining immediately.
- **End while they still want more.** The goal of practice one is that they ask for practice two.

---

## Running it

### Locally

It's a single HTML file with no build step. Open `index.html` in any browser. That's it.

### On GitHub Pages

1. Put `index.html` at the root of a public repo
2. **Settings → Pages →** Source: *Deploy from a branch*, branch `main`, folder `/ (root)`
3. Wait 1–2 minutes — your site appears at `https://kidsbackyardcoach-cyber.github.io/`

### On a phone

Open the URL in Safari or Chrome → **Share → Add to Home Screen**. It gets its own icon and opens full-screen without browser chrome. For most families this is the app — no store, no install, no account.

---

## Technical notes

- **Single file, zero dependencies.** No framework, no build, no bundler, no package.json. ~160 KB of HTML/CSS/JS.
- **Fonts** load from Google Fonts (Barlow, Barlow Condensed, Noto Sans SC). First load needs a connection; after that it's cached. Swap to system fonts if you need full offline.
- **Storage** uses `localStorage`, with a fallback chain so it also runs inside Claude artifacts and degrades to memory-only if storage is blocked. Progress is per-device and per-browser — clearing site data resets it.
- **All illustrations and diagrams are inline SVG**, drawn for this project. No product photos, no brand marks, no licensed imagery — deliberate, so the app can be published or sold without an image-rights problem.
- **Internationalization** is a plain object lookup (`T[lang]`), with per-item translations nested in the content objects (`drill.zh.how`). No i18n library. Adding a fourth language means adding one key to each object.
- **Accessibility:** semantic buttons with `aria-pressed`, visible keyboard focus rings, and `prefers-reduced-motion` respected.

### Structure inside the file

```
<style>          design tokens, per-sport accent colors, per-language type rules
IC               16 gear icons (SVG)
T                UI strings, 3 languages
FIG              6 field/play diagrams (SVG generators)
BASICS           sport primers, 3 languages
MOVE / D         43 drills, 3 languages
SEASON           12 weeks x 4 sports, 3 languages
SPORTS / KIT     gear lists and prices
RULES / FIXES    coaching guide, 3 languages
                 render + state functions
```

---

## Contributing

**Translations** are the most useful contribution. Each translatable item is an object keyed by language code — add your language code alongside `en` / `zh` / `es` in `T`, `D`, `SEASON`, `SPORTS`, `BASICS`, `RULES`, and `FIXES`, then add a button to `#langsw`.

Notes for translators:

- Keep drill **cues** short and shoutable. They're meant to be yelled across a yard, not read.
- The **Chinese** build switches to Noto Sans SC and disables uppercase transforms — uppercase styling doesn't apply to Chinese characters. If you add a non-Latin script, add the equivalent CSS override.
- **Spanish** here is neutral Latin American, leaning Mexican in vocabulary (*cubeta*, *tenis*, *gis*). Regional variants welcome as separate codes.

**New drills** need all six fields (`n`, `setup`, `how`, `cue`, `e`, `h`) in every supported language, plus a `tag` that exists in `T[lang].tags`.

---

## Important notes

**This is not medical, safety, or professional coaching advice.** It's a set of age-appropriate activities compiled for informal backyard play. Use your own judgment about your child, supervise directly, and check with your pediatrician about any physical activity concerns.

**On safety specifically:**

- Flag football at this age is **non-contact**. No helmets, no pads, no tackling. If you're being sold protective gear for a four-year-old, you're being sold the wrong game.
- **"Drop the bat"** is the single most important rule in the t-ball section. Children swing and then run while still holding it. Teach it from day one, every time.
- Prices are **rough US estimates for budgeting**, not live prices, and will go stale. Check current listings.
- Equipment size recommendations (size 3 ball, 24–26" bat, 6" hurdles) reflect standard guidance for this age group. Confirm against your league's rules if joining one.

---

## Contact

Questions, bug reports, translation offers, or a photo of your kid actually using this — I'd like to hear about it.

**kidsbackyardcoach@gmail.com**

If you're reporting a problem, it helps to include your phone or browser, the language you had selected, and which sport and week you were on.

---

## Copyright and use

© 2026 Backyard Coach. All rights reserved.

This project is published so parents can use it, not as open-source software. The source is visible here because it's a single HTML file served by GitHub Pages — visibility is not a license.

**You may:** use the app freely with your own family, team, or group; link to it; and print sessions for your own use.

**Please ask first before:** redistributing or hosting your own copy, publishing modified versions, bundling it into another product, or using it commercially.

Contributions and translations are welcome — see above. By submitting one, you agree it can be included in this project. If you want to build something on top of this, get in touch; the answer is usually yes.

*This is a plain-language summary, not legal advice.*

---

## Roadmap

Ideas, in rough order of usefulness:

- [ ] Offline-capable: embed fonts, add a service worker
- [ ] Traditional Chinese (繁體中文) for Taiwan and Hong Kong
- [ ] Tennis, track and field, and a rainy-day indoor module
- [ ] A 3-year-old track (shorter sessions, simpler drills) and a 5–6 track
- [ ] Print view — one page per session for the fridge
- [ ] Export/import progress, so it survives a new phone
