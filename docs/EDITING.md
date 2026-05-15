# Editing the Site — Edge of Society Website

## How the Page Is Built

The entire site is one file: `index.html`. There is no build process, no CMS, no templates. To edit anything, open `index.html` in a text editor.

---

## Finding What to Edit

The HTML is organized into sections marked by `<section>` tags:

| Section ID | What It Contains |
|-----------|-----------------|
| (no id) | Hero — headline, subtitle, CTA buttons |
| `#list` | Episode list (compact, sidebar-style) |
| `#grid` | Episode grid (card layout with covers) |
| `#guests` | Guest cards |
| (footer) | Listen links, tagline |

**Tip:** Search for the section name inside the HTML to find where to make changes.

---

## Common Edits

### 1. Update Episode Status (Planning → Recording → Live)

Episode statuses use colored badges. Status is set on two places per episode:
- In the list view: `<div class="episode-num orange">02</div>` — color class = status
- In the grid view: `<div class="grid-card-num orange">Episode 02</div>` — same color class

**Color → Status mapping:**

| Color Class | Status | When to Use |
|-------------|--------|-------------|
| `red` | Planning | Episode is being planned |
| `orange` | Recording | Episode has been recorded |
| `yellow` | Editing / Pending | In post-production |
| `green` | Live | Episode is published |
| `blue` | Resource Holder | Special badge for guest type |
| `indigo` | Service Provider | Special badge for guest type |
| `violet` | Curious | Special badge for guest type |

**To change status:** replace `orange` with the appropriate color class in both the list item and the grid card for that episode number.

---

### 2. Add a Listen Link (YouTube / Podcast / Website)

Find the footer section and look for the three listen buttons. They're currently:

```html
<a href="#" class="btn btn-primary">
    <svg>…</svg> Listen on YouTube
</a>
<a href="#" class="btn btn-secondary">Podcast RSS</a>
<a href="#" class="btn btn-secondary">Website</a>
```

Replace `href="#"` with the actual URL.

---

### 3. Change a Guest Name or Community

Guest cards are in the `#guests` section around lines 384–393. Each card:

```html
<div class="guest-card">
    <h3>Julian</h3>
    <div class="community">Retribalize</div>
    <div class="type">Community Founder</div>
</div>
```

Edit the text inside `<h3>` (name), `.community` (their community), or `.type` (their role).

---

### 4. Add or Replace an Episode Cover Image

1. Place your image as `covers/ep0X.png` (e.g. `ep03.png`)
2. The site references it automatically in two places per episode:
   - List view: `<img src="covers/ep01.png" alt="Episode 1 cover">`
   - Grid view: `<img src="covers/ep01.png" alt="Episode 1">`
3. Both `<img>` tags have `onerror` handlers that gracefully hide the image if the file is missing — so the layout won't break if a cover is missing.

**Recommended size:** square images work best (the grid cards use `aspect-ratio: 1`).

---

### 5. Change the Hero Text

The hero section is right after the `<nav>`. Look for the `<h1>` tag — it currently says:

```html
<h1>Society Pilots on the <span class="highlight">Edge of the Monolith</span></h1>
```

Change the headline or the highlighted portion. Below it is the subtitle paragraph.

---

### 6. Change the Main Cover Image

Replace `cover.jpg` in the repo root. The hero section references it:

```html
<img src="cover.jpg" alt="Edge of Society — Season 1">
```

Best dimensions: wide format, at least 1200px wide.

---

## Adding a New Episode (After Season 1)

1. Add a new `<div class="episode-item">` to the list section
2. Add a new `<div class="grid-card">` to the grid section
3. Add a guest card in the guests section
4. Copy the pattern from an existing episode and update:
   - Episode number (02 → 03, etc.)
   - Title
   - Description
   - Duration
   - Cover image (`covers/ep0X.png`)
   - Status color

---

## CSS Notes

All styles are inline in the `<style>` block at the top of `index.html`. Key things:

- **CSS variables** in `:root` control colors — easy to do a global recolor
- **No external CSS files** — everything is self-contained
- **Font:** Inter from Google Fonts (loaded in `<head>`)
- **Responsive:** basic mobile styles at the bottom of the `<style>` block

---

## After Editing

```bash
git add .
git commit -m "update episode 3 to recording status"
git push
```

GitHub Actions deploys automatically in ~30–60 seconds.