# Static site starter

A plain HTML/CSS/JS site that goes live on [Dockhold](https://dockhold.eu) with
no build step and no config. The fastest "it works" deploy — push it, get an
HTTPS URL.

[![Deploy on Dockhold](https://dockhold.eu/button.svg)](https://app.dockhold.eu/new?repo=https://github.com/dockhold/static-starter&name=static-starter&ref=button)

## Deploy it

1. Click **Use this template** (or fork this repo) to get your own copy.
2. Click the **Deploy on Dockhold** button above, or open
   [app.dockhold.eu/new](https://app.dockhold.eu/new), connect GitHub, and pick
   your repo.
3. That's it. Dockhold builds the included [`Dockerfile`](Dockerfile) and serves
   the site. It goes live at `https://<your-app>.dockhold.app` with HTTPS
   handled.

Every later push to your main branch redeploys automatically.

## Deploy with your AI tool

Install the Dockhold plugin or MCP server in your AI coding tool
([setup guide](https://dockhold.eu/docs/recipes/deploy-from-your-ai-tool)), then
say "put this online" in a folder with this template. The tool signs you in
through the browser once and reports the URL when the app is live.

Or from a terminal: `npx dockhold login`, then `npx dockhold deploy`.

## How it serves

There's one moving part, the last line of the [`Dockerfile`](Dockerfile):

```dockerfile
CMD serve -l $PORT .
```

`serve` hands out the files in this folder on the port Dockhold assigns
(`$PORT`). That `$PORT` is the only rule that matters. An app must listen on the
port the platform gives it, not a hardcoded one. The `start` script in
[`package.json`](package.json) runs the same command locally.

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
