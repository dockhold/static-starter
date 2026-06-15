# Static site starter

A plain HTML/CSS/JS site that goes live on [Dockhold](https://dockhold.eu) with
no build step and no config. The fastest "it works" deploy — push it, get an
HTTPS URL.

[![Deploy to Dockhold](https://img.shields.io/badge/Deploy%20to-Dockhold-2563eb?style=for-the-badge)](https://app.dockhold.eu/new?repo=https://github.com/dockhold/static-starter)

## Deploy it

1. Click **Use this template** (or fork this repo) to get your own copy.
2. Click the **Deploy to Dockhold** button above, or open
   [app.dockhold.eu/new](https://app.dockhold.eu/new), connect GitHub, and pick
   your repo.
3. That's it. Dockhold installs dependencies and starts the site for you. Your
   site goes live at `https://<your-app>.dockhold.app` with HTTPS handled.

Every later push to your main branch redeploys automatically.

## How it serves

There's one moving part: the `start` script in
[`package.json`](package.json).

```json
"start": "serve -l $PORT ."
```

`serve` hands out the files in this folder on the port Dockhold assigns
(`$PORT`). That `$PORT` is the only rule that matters — an app must listen on
the port the platform gives it, not a hardcoded one.

## Make it yours

- Edit [`index.html`](index.html) and [`style.css`](style.css).
- Add more pages as plain `.html` files; link them with relative paths
  (`./about.html`, `./style.css`).
- Keep assets relative so they resolve once the site is live.

## Run it locally

```bash
npm install
PORT=3000 npm start
# open http://localhost:3000
```

## Full walkthrough

[Deploy a static site](https://dockhold.eu/docs/recipes/deploy-a-static-site) —
the step-by-step recipe, including common fixes (404 at the root, missing start
script, assets 404).
