# Worklog

A personal productivity app for tracking work, tasks, time, reports, reminders, and Barker Studio projects.

This repository starts from the existing single-file Worklog prototype and is prepared for GitHub-based development and GitHub Pages deployment.

## Current app areas

- Today dashboard and quick capture
- Task pipelines and priorities
- Weekly/monthly reports
- Timesheet and manual time editing
- Reminders
- Barker Studio quotations, invoices, projects, and profile details

## Important: current data behavior

The current UI is a prototype. Most sample tasks, time blocks, clients, documents, and settings are JavaScript variables inside `index.html`. Reloading the page resets them to the values in the source file.

Do not enter real passwords, API keys, private bank details, or sensitive client information into the public repository.

## Recommended development path

### Phase 1 — GitHub + local app

1. Keep the current visual design.
2. Move changing data to browser storage (`localStorage` or IndexedDB).
3. Make dates and the current time dynamic.
4. Add import/export backup.
5. Turn the app into an installable PWA.

This phase is simplest and works well on one main device.

### Phase 2 — sync across devices

Add authentication and a cloud database. Recommended options:

- Firebase Authentication + Firestore
- Supabase Auth + Postgres

For this app, Firebase is a practical fit because the prototype already anticipates a Firebase-backed setup in its profile copy.

### Phase 3 — integrations

Add integrations only after the core data model is stable:

- Clockify API for time entries
- Google Drive / Docs for reports
- Browser/device notifications
- Calendar integration if useful

Never commit private API tokens to GitHub. Use a backend, serverless function, or provider-supported OAuth flow.

## Repository structure

```text
worklog/
├─ index.html
├─ .nojekyll
├─ .gitignore
├─ README.md
├─ .github/
│  └─ workflows/
│     └─ pages.yml
└─ docs/
   ├─ DEVELOPMENT.md
   └─ DATA-MODEL.md
```

## Run locally

The simplest way is to open `index.html` in a browser.

For a more realistic local web server:

```bash
python -m http.server 8080
```

Then open `http://localhost:8080`.

## Publish with GitHub Pages

1. Create a new repository on GitHub, for example `worklog`.
2. Upload all files in this folder or push them with Git.
3. Open **Settings → Pages**.
4. Under **Build and deployment → Source**, choose **GitHub Actions**.
5. Push to `main`.
6. Open the **Actions** tab and confirm the Pages workflow succeeds.
7. GitHub will show the published URL in the deployment result.

## First development milestone

Before adding more features, implement:

- persistent app state
- dynamic date/time
- backup/restore
- PWA installation
- a settings screen

See `docs/DEVELOPMENT.md` for the detailed roadmap.
