# Meeting Record / Toplantı Tutanağı

A bilingual (English/Turkish) meeting notes web app — single HTML file, no dependencies, deployable anywhere.

## Features

- **Auto meeting number** — increments automatically (MTG-0001, MTG-0002…) and persists via `localStorage`
- **Participant management** — add names and emails dynamically; live attendance stats
- **Online signature** — draw-pad for each participant (mouse & touch), saved as image data
- **Notification flow** — generates a shareable signature-request link per participant; copy & send manually (or wire up to an email backend)
- **Export to Excel** — exports the current meeting (and all past meetings from the same browser) to a `.xlsx` file; each meeting gets its own sheet, layout mirrors the original ÜY-FR-0006 template
- **Meeting archive** — every exported meeting is saved to `localStorage`; re-exporting produces a cumulative file with all meetings
- **Bilingual** — all labels in English and Turkish
- **Dark mode** — automatic via `prefers-color-scheme`
- **Print-ready** — use the Print button or Ctrl+P
- **Zero dependencies** — one HTML file; external assets are Tabler Icons and SheetJS, both via CDN

## Deploy to GitHub Pages

1. Create a new GitHub repository (e.g. `meeting-record`)
2. Upload `index.html` to the root of the repo (or the `docs/` folder)
3. Go to **Settings → Pages**
4. Under **Source**, select `Deploy from a branch` → choose `main` (or `master`) and `/ (root)` (or `/docs`)
5. Click **Save** — your site will be live at `https://<your-username>.github.io/<repo-name>/`

## Local use

Just open `index.html` in any modern browser — no server needed.

## Data storage

All data (participants, signatures, meeting counter) is stored in the browser's `localStorage`. Nothing is sent to any server. Each browser/device maintains its own state.

To reset meeting counter or clear data, open DevTools → Application → Local Storage and delete the keys prefixed with `mr_`.

## Connecting email notifications

The notify flow currently generates a shareable link. To send emails automatically:

1. Set up a small backend (e.g. a Cloudflare Worker, Vercel serverless function, or Node.js server)
2. Use an email API such as [Resend](https://resend.com), [SendGrid](https://sendgrid.com), or [Mailgun](https://mailgun.com)
3. Replace the copy-link flow in `index.html` with a `fetch()` POST to your endpoint

## Form reference

- **Form No:** ÜY-FR-0006
- **Published:** 03.05.2018
- **Revision:** 0
