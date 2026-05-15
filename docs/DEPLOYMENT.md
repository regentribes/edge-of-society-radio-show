# Deployment — Edge of Society Website

## How It Works

The site is a **static HTML file** — `index.html` — deployed directly to **GitHub Pages**. There is no build step. No bundler. No Node.js. The HTML file and assets are pushed to the `master` branch, and a GitHub Actions workflow publishes them.

---

## CI/CD Pipeline

`.github/workflows/pages.yml` handles everything:

```yaml
on:
  push:
    branches: [master]
  workflow_dispatch:   # ← allows manual trigger

jobs:
  deploy:
    runs-on: ubuntu-latest
    steps:
      - Checkout          # pulls the repo
      - Setup Pages       # configures GitHub Pages
      - Upload artifact   # uploads the repo root as a static site
      - Deploy to GitHub Pages
```

**Trigger:** Any push to `master` automatically deploys. You can also trigger manually via GitHub UI → Actions → "Deploy to GitHub Pages" → Run workflow.

---

## How to Deploy

### Normal flow (push to master)

```bash
git add .
git commit -m "update episode 3 content"
git push
```

GitHub Actions picks it up automatically. Takes ~30–60 seconds.

### Manual trigger

1. Go to https://github.com/regentribes/edge-of-society-radio-show/actions
2. Click "Deploy to GitHub Pages"
3. Click "Run workflow"
4. Wait ~30 seconds, check the site

---

## Troubleshooting

### Site is 404 after push

The most common cause: the workflow wasn't set up before the first push. It was added 2026-05-14.

**Fix:** Manually trigger the workflow via GitHub Actions UI (workflow_dispatch). Then push again — from that point on it will auto-deploy.

### Workflow not showing in Actions

- Go to the repo → Actions tab
- If no workflows appear, check that `.github/workflows/pages.yml` exists on `master`
- If the repo was created before GitHub Pages was configured, you may need to go to Settings → Pages → Source and re-select "GitHub Actions"

### Changes not appearing

1. Check the Actions run completed successfully (green checkmark)
2. Wait 1–2 minutes — GitHub Pages can take a moment to propagate
3. Hard-refresh with Ctrl+Shift+R / Cmd+Shift+R
4. Try an incognito window

### "Page build warning" in GitHub Pages settings

This is a Jekyll warning — the site is plain HTML, not Jekyll, so it's harmless. The deploy still works.

---

## How to Update the Site

See [EDITING.md](./EDITING.md) for content updates.
See [CONTENT.md](./CONTENT.md) for episode and guest data.