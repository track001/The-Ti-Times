# The Ti Times

**Your world, before the world gets loud.**

An independently developed personal morning newspaper for cyber, space, technology, climbing, and daily Security+/CISSP practice. Built with React, Vite, GitHub Actions and GitHub Pages.

## Credits and inspiration

Inspired by **Karen X. Cheng's [The Morning Newspaper](https://newspaper.karenx.com/)**, a personalized Grok bot that assembles a morning newspaper from a user's schedule and inbox and can print it overnight. The Ti Times is an independent reimagining with a web-first editorial experience, interactive certification practice, and a personal archive. It does **not** use Karen's original code, templates, or brand assets and is not affiliated with or endorsed by her. No Gmail access is requested.

## Start in CodeSandbox

1. Import the **contents** of this folder as a new Vite/React project (or import the ZIP).
2. Run `npm install` then `npm run dev`.
3. Review the demo edition. The seeded Oct 23, 2026 content is explicitly labeled illustrative.
4. Push the project to a GitHub repo named `The-Ti-Times` on the `main` branch.
5. In GitHub **Settings → Pages → Build and deployment**, choose **GitHub Actions**.
6. In GitHub **Actions**, manually run **Publish daily newspaper** to generate an edition. It uses publicly accessible RSS feeds and publishes only when at least one feed succeeds.
7. The separate **Deploy to GitHub Pages** workflow builds the site on pushes to `main`.

Expected URL: `https://track001.github.io/The-Ti-Times/` (once published under that account).

## Daily editions and retention

- GitHub Actions runs daily around 06:30 **America/Denver**, with two UTC triggers to cover daylight saving time. GitHub scheduling is best effort, not guaranteed to execute at exactly 06:30.
- Generated editions are JSON files under `public/editions/`; the generator removes editions older than 30 calendar days.
- Starred editions are saved as complete snapshots in **localStorage** on the device where they were starred, and survive public archive pruning. They are **not synced between browsers/devices** and will be lost if browser storage is cleared. For cross-device permanent saves, add a private backend or export/import feature.
- Personal calendar and tasks are loaded in the user's browser only; they are **not written to public edition JSON**.

## Google Calendar and Tasks (optional)

1. In [Google Cloud Console](https://console.cloud.google.com/), create/select a project, enable **Google Calendar API** and **Google Tasks API**.
2. Configure the OAuth consent screen and an **OAuth 2.0 Web application** client.
3. Add authorized JavaScript origins for your site (e.g. `https://track001.github.io`) and CodeSandbox preview origin as needed.
4. Put the **public OAuth client ID** in `public/config.json` as `googleClientId`. Never commit a client secret or refresh token.
5. Google OAuth may require adding your Google account as a test user until your app is published/verified.
6. Open **My Desk → Connect Google Calendar + Tasks**. Tokens are kept in memory for the session, not persisted.

The app requests `calendar.events` and `tasks` scopes, **not Gmail**. Google Calendar and Tasks may require additional consent-screen configuration and verification for broader public use.

## Weather and personalization

Set `weatherLatitude`, `weatherLongitude`, `weatherLabel`, and `timezone` in `public/config.json`. Weather is retrieved from [Open-Meteo](https://open-meteo.com/) client-side. Do not store your private home address in the public repo.

## What is and isn't automated

- **Automated now:** RSS-backed headline collection, source links, rotating certification lessons/questions, daily JSON publishing, 30-day retention, GitHub Pages deployment.
- **Manual or future integration:** Personalized AI-written synthesis, up-to-the-minute custom climbing coverage, personal project sync, calendar items inside published articles, cloud-synced starred editions and quiz history.
- RSS items are attributed to their sources; the generator does not invent news stories when feeds are unavailable.

## Privacy

GitHub Pages and the repository are public. Never commit private calendar data, API secrets, personal email, or confidential work/project details. Google account data remains in browser memory for that session. Local starred editions, tasks, and quiz responses are stored in browser localStorage.

## Tech stack

React · Vite · Lucide · Google Identity Services · Google Calendar API · Google Tasks API · Open-Meteo · Python standard library · GitHub Actions · GitHub Pages.
