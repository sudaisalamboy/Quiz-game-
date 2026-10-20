# Setup Guide — Quiz Game (Trivia Master)

> A single-file HTML quiz game powered by the Open Trivia DB API, with categories, difficulty, timer, streaks, and persistent high scores.

Made by **Sudais Alam**.

---

## Project Overview

**Quiz Game (Trivia Master)** is a self-contained web app (`quiz game.html`). It fetches trivia questions from the Open Trivia DB API, lets the player choose category/difficulty/amount/timer, scores answers live, tracks streaks, and persists high scores, total quizzes, and streaks in the browser's `localStorage`.

---

## Prerequisites

- A modern web browser (Chrome, Edge, Firefox, Safari).
- An internet connection (to load the Open Trivia DB API and CDN-hosted fonts/icons).

No Node, no build tools, no server required.

---

## Installation

```bash
# 1. Clone
git clone https://github.com/sudaisalamboy/Quiz-game-.git
cd Quiz-game-

# 2. Open the file
#    Double-click "quiz game.html", or serve it (recommended).
```

---

## Running Locally

### Option A — Open directly
Double-click `quiz game.html`. It opens via `file://` and works for core play.

### Option B — Serve via a tiny local server (recommended)
```bash
# Python 3
python3 -m http.server 8080

# or Node
npx serve .
```
Then visit **http://localhost:8080/quiz%20game.html** (note the encoded space).

> Serving via HTTP gives the most consistent fetch behavior and avoids any browser quirks with `file://` origins.

---

## Project Structure

```
.
├── quiz game.html          # Entire app: markup, CSS, and JS in one file
├── README.md
├── SETUP.md
└── preview/preview.png
```

---

## Customization

- **Default quiz settings** — edit the `<select>` defaults in the setup screen (e.g. default `amount`, `timer`).
- **Brand colors** — edit the `:root` CSS variables at the top of `<style>`.
- **Run fully offline** — vendor Poppins + Font Awesome locally and update the `<link>`/`<script src>` paths. Note: questions still require the Open Trivia DB API, so a local cached question set would be needed for true offline play.
- **Change the API source** — replace the `fetch('https://opentdb.com/...')` calls with your own trivia API, keeping the same response shape.

---

## Deployment

Because it's a single static file, you can host it anywhere:

- **GitHub Pages** — push to the repo and enable Pages on the `main` branch root.
- **Netlify / Vercel / Cloudflare Pages** — drag-and-drop the folder, or connect the repo.
- **Any static host** (InfinityFree, your own server) — just upload `quiz game.html`.

> If hosting, consider renaming the file to `quiz-game.html` (no space) for cleaner URLs.

---

## Troubleshooting

| Problem | Fix |
|---------|-----|
| **"No questions load" / fetch error** | Open Trivia DB API is rate-limited (~1 req/sec). Wait a moment and retry. Also confirm you're online. |
| **Categories dropdown is empty** | The category list comes from `https://opentdb.com/api_category.php` — allow network access. |
| **Stats reset on refresh** | `localStorage` is per-browser/profile. Use the same browser; clearing site data wipes stats. |
| **HTML entities appear in questions** | The app decodes them; if you customize, ensure you decode `&quot;`, `&#039;`, `&amp;`, etc. |
| **Icons look like squares** | Font Awesome CDN blocked; vendor the CSS + webfonts locally. |
| **Fonts fall back to default** | Google Fonts blocked; allow the network or vendor Poppins locally. |
| **Timer not counting** | Ensure JavaScript is enabled and the browser isn't in strict background-throttle mode while tab is hidden. |

---

## Credits

Powered by the [Open Trivia DB](https://opentdb.com) API.

Made by **Sudais Alam**.
