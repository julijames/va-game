# Can you make it in the VA?

> The process of obtaining military veteran benefits can be a challenge. Think you can do it?

An interactive narrative game where the player is a returning veteran navigating the U.S. Veterans Affairs bureaucracy. Starting with **$4,750 in savings** and a target of about **180 days** of runway, the player works through housing, three VA departments (Physical Health, Mental Health, Disability & Benefit Claims), and life decisions about work and school. Each choice rolls between two possible outcomes, and the closing screen compares your total days against the 273-day national average for VA benefit processing.

This is a web rebuild of an Adobe Captivate SCORM project. All scenario text, choice labels, outcome copy, and meter deltas are verbatim from the original `VA Game Content.xlsx` spec, including original quirks ("appartment", "is list at", etc.).

## Play

Open `index.html` in any modern browser, or visit the deployed GitHub Pages URL.

## How it deploys

Static single-page app. No build step required.

- `index.html` — the entire app (React via CDN, Tailwind via CDN, Babel-standalone for in-browser JSX)
- `assets/` — 13 silhouette illustrations matching each scenario

To deploy via GitHub Pages: **Settings → Pages → Source: Deploy from a branch → Branch: `main` / `/ (root)`**. The game will be live at `https://[your-username].github.io/[repo-name]/` within a minute.

External dependencies (loaded from `unpkg.com` at runtime): React 18, ReactDOM 18, Tailwind CSS, Babel Standalone.

## Where the content lives

All game data is in `index.html`:

- **Scenarios (intro, choice slides, info slides)** → `const SCENARIOS = [...]`
- **Chapter groupings for the progress stepper** → `const CHAPTERS = [...]`
- **Starting meter values** → `START_SAVINGS = 4750`, `START_DAYS = 0`
- **Daily spending baseline / national average reference** → `DAILY_SPENDING = 26`, `NATIONAL_AVERAGE_DAYS = 273`

Each choice slide has two outcomes; the game picks one at random per playthrough (50/50) — this creates replayability and mirrors the "luck of the draw" feel of navigating real-world bureaucracy.

## Game flow

13 slides, sequential:

1. **Can you make it in the VA?** (title)
2. **Welcome Home** (overview of your situation: $4,750, 6 months runway)
3. **Housing** (choice: live with parents / get an apartment)
4. **VA Overview** (info: 700k veterans waiting, 200-day average wait)
5. **Department Overview** (info: 3 departments to navigate)
6. **Physical Health** (info)
7. **Health Choice** (choice: ask for a different team / give your team a chance)
8. **Mental Health** (choice: treat PTSD / refuse treatment)
9. **Disability and Benefit Claims** (info)
10. **Disability Dispute** (choice: dispute the 10% rating / accept it)
11. **Work** (info)
12. **VA Appt** (choice: job interview / VA appointment when they conflict)
13. **School** (choice: school on credit / keep working)

Final screen: "Did your choices speed things up?" — compares your total days to the 273-day national average and shows your remaining savings.

## Credits

Original content and game design: Juli James.
Original implementation: Adobe Captivate (SCORM).
Web rebuild: 2026.
