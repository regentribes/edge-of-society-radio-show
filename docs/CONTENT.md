# Content Reference — Edge of Society Website

## Episode Data

The site displays **10 planned episodes** for Season 1. Each episode has:
- Cover image (`covers/ep0X.png`)
- Title
- Short description
- Featured guest name
- Status (Planning / Recording / Live)

### Episode List

| # | Episode Title | Guest | Status |
|---|-------------|-------|--------|
| 1 | Finding Your People | Julian | Planning |
| 2 | The Land Question | Jordan | Planning |
| 3 | Governance That Doesn't Suck | Nicole Reese | Planning |
| 4 | Money That Makes Sense | Murat | Planning |
| 5 | The Technology Question | Gini | Planning |
| 6 | Conflict as Fuel | Sam | Planning |
| 7 | Growing Without Losing Your Soul | NEOS Life | Planning |
| 8 | The Next Generation | Florian | Planning |
| 9 | Rituals and Culture | Frances | Planning |
| 10 | The Network Effect | Jean Luc | Planning |

### Cover Images

All episode covers live in `covers/`:
```
covers/ep01.png
covers/ep02.png
...
covers/ep10.png
```

Each is a square PNG (currently generated/collected per episode). Main cover art is `cover.jpg` (full-size hero image).

**Dimensions used on the site:**
- Hero/main cover: ~900px wide, displayed at full width
- Episode cards: square-ish thumbnails in a grid

---

## Guest List

Full details in `SHOW-BRIEF.md` and `EPISODE-TOPICS.md` in the repo root.

| Guest | Community | Role |
|-------|---------|------|
| Julian | Retribalize | Community Founder |
| Jordan | Wild Seeds — San Diego | Community Founder |
| Nicole Reese | Terrenity + Regen Tribe | Community Founder |
| Murat | The Ark — Costa Rica | Community Founder |
| Gini | Loveland — Community Root | Community Founder |
| Sam | TDF Oasa — Closer Community | Community Founder |
| NEOS Life | Portugal (couple) | Community Founder |
| Florian | Geodomes — Regen Designer & AI Engineer | Founder |
| Frances | Regenesis | Founder |
| Jean Luc | Regen Community Entrepreneur | Founder |

---

## Listen / Watch Links

The site has placeholder links for:
- YouTube (Coming soon)
- Podcast RSS (Coming soon)
- Website (Coming soon)

Once episodes are live, these should be replaced with real URLs in the `index.html` hero section and footer.

---

## CSS Variables

The site uses CSS custom properties defined in `:root` on `index.html`:

| Variable | Value | Use |
|---------|-------|-----|
| `--bg-primary` | `#0a0a0a` | Main background |
| `--bg-secondary` | `#111111` | Section backgrounds |
| `--bg-card` | `#1a1a1a` | Card backgrounds |
| `--accent` | `#22c55e` | Green accent (live, active) |
| `--red` | `#ef4444` | Status: alert |
| `--orange` | `#f97316` | Status: recording |
| `--yellow` | `#eab308` | Status: planning |
| `--green` | `#22c55e` | Status: live |
| `--blue` | `#3b82f6` | Guest type: resource holder |
| `--indigo` | `#6366f1` | Guest type: service provider |
| `--violet` | `#a855f7` | Guest type: curious |

Font: **Inter** (Google Fonts), weights 300–800.

---

## Topic Areas (Tags)

The hero section shows topic tags. These map to the show's focus areas:

- Regenerative Communities
- Neighborhood Design
- Collective Governance
- Land & Ownership
- AI for Communities

Additional per-episode tags are color-coded by theme.