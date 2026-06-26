---
name: seneca-daily
description: Daily philosophy post to Jordan's reading site at 6AM
---

You are posting a daily morning entry to Jordan's personal philosophy reading site.

The site lives at /Users/jordanjunk/projects/sim (git repo, remote: https://github.com/jwjunk24/seneca.git).
GitHub PAT is stored in /Users/jordanjunk/projects/sim/.seneca-pat (single line, no newline).
Bash path for the sim folder: resolve dynamically at runtime with:
```bash
SIM=$(find /sessions -maxdepth 4 -name ".seneca-pat" 2>/dev/null | head -1 | xargs dirname)
```

**No Latin anywhere in the post** — not in quotes, not in parentheses, not as labels or attributions. English only throughout.

**No section headers** — the post should read as one continuous, well-flowing piece of prose. Do not use h2 or any other headers inside the post body. All content should be woven naturally into the writing, not announced with headings.

**No first-person voice** — do not use "I", "me", "we", "our", or "us" anywhere in the post body. Write in third person or with impersonal constructions throughout. Instead of "we rarely feel content," write "people rarely feel content" or "the person who has learned to stop." This applies to every paragraph including the closing.

**No timestamps** — do not include a `<p class="post-meta">` date line in the post header.

---

## Theme cluster

Every post must draw on a theme from this cluster: **contentment, gratitude, and sufficiency**. This means topics like: the treadmill of always wanting more, the difference between what imagination promises and what experience delivers, the practice of appreciating what is already present, the distinction between necessary desires and empty ones, the cost of pursuing things that don't satisfy, the richness available in an ordinary life, the freedom that comes from needing less.

Stay within this cluster. There is rich variation within it — avoid repeating the same angle two days in a row, but don't drift outside the cluster.

---

## Source pool

Every post draws on at least two voices from this pool. One leads — whichever fits the theme most naturally for that day. The other(s) extend, complicate, or reframe it. Choose freely; no source is the default.

- **Epicurus** — his Letter to Menoeceus, the Vatican Sayings, and Key Doctrines; his taxonomy of natural/necessary desires vs. empty ones; his argument that natural wealth has a limit and is easily acquired; the community at the Garden as a lived example
- **Seneca** — his *Letters to Lucilius* on wealth, wanting less, and the freedom that comes from needing little; especially Letters 2, 16, 17, 27, 119, and 123; his habit of taking up a single Epicurean maxim and working it through
- **Buddhism** — the second noble truth (craving as the root of suffering), santosha (contentment as a practice), mudita (taking joy in what exists), the Dhammapada on desire and the illusion of arrival, the teaching that the hungry ghost is never fed by more food
- **Taoism** — the Tao Te Ching on knowing when enough is enough; Chapter 33 ("one who knows contentment is wealthy"), Chapter 44 (what is gained by grasping, what is lost), Chapter 46 (no disaster greater than not knowing sufficiency)
- **Marcus Aurelius** — his *Meditations* on finding richness in what is already present, the practice of negative visualization (imagining loss in order to appreciate what you have), gratitude for ordinary things, the shortness of time as a reason to appreciate rather than defer
- **Thoreau** — *Walden*, particularly "Economy" and "Where I Lived"; his calculation of the true cost of things in terms of life exchanged; "The cost of a thing is the amount of what I will call life which is required to be exchanged for it, immediately or in the long run"

Rotate the leading voice across sources over time. Secondary voice(s) should flow naturally from the primary material, not be announced as separate sections. Name each person or text when you first introduce them and describe the specific idea or passage. One strong secondary voice is better than two thin ones.

---

## Step 1 — Choose today's theme and primary voice

Read the index at /Users/jordanjunk/projects/sim/index.html to see which themes and sources have been used recently in the Contentment & Gratitude section. Choose:
1. A theme (within the contentment/gratitude/sufficiency cluster) that hasn't appeared in the last 2 weeks
2. A primary voice from the source pool that hasn't led recently

Vary both the angle and the leading source — the pool is wide enough that no two posts should feel like retreats.

## Step 2 — Write the content

Each post must include, woven together as flowing prose (no headers):
- A theme name (short, evocative) — used in the title only, not repeated as a header in the body
- The primary source with a specific reference (a letter number, chapter, book and section, or passage) — at least one specific quote (English only) and one concrete scene or detail
- The secondary voice — woven in as a natural extension of the primary material. Name the person or text and describe the specific idea or passage. Do not announce it as a separate section.
- A closing thought — not a homework assignment. A reframing, an image, or a question that lands naturally.

Tone: intelligent, warm, not preachy. Write like a knowledgeable friend sharing something genuinely interesting. The goal is internalization — the reader is actively working on these habits, not just curious about them.
Length: roughly 400–500 words of body content.

## Step 3 — Determine today's filename

Get today's date:
```bash
date +%Y-%m-%d
```

Check whether a post for today already exists in the contentment folder:
```bash
SIM=$(find /sessions -maxdepth 4 -name ".seneca-pat" 2>/dev/null | head -1 | xargs dirname)
ls "${SIM}/posts/contentment/$(date +%Y-%m-%d).html" 2>/dev/null
```

If it exists, use suffix `b`, `c`, etc. (e.g. `2026-06-08b.html`). Otherwise use the plain date.

## Step 4 — Write the HTML post file

Create /Users/jordanjunk/projects/sim/posts/contentment/FILENAME.html using this exact template (substitute all CAPS placeholders):

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>THEME_NAME — Seneca</title>
  <link rel="stylesheet" href="../../seneca.css">
</head>
<body>

<header class="site-header">
  <p class="site-title"><a href="../../index.html">www.senecathoughts.gov.wwwsenecathoughts</a></p>
</header>

<main>
  <article>
    <header class="post-header">
      <h1 class="post-title">THEME_NAME</h1>
      <p class="post-source">SOURCE_REF</p>
    </header>

    <div class="post-body">
      PARAGRAPHS_HERE

      <p class="closing">CLOSING_THOUGHT</p>
    </div>

    <nav class="post-nav">
      <div class="prev">
        <a href="PREV_FILENAME">
          <span class="nav-label">← Earlier</span>
          PREV_THEME
        </a>
      </div>
      <div class="next"></div>
    </nav>
  </article>
</main>

<footer>
  <a href="../../index.html">All letters</a>
</footer>

</body>
</html>
```

SOURCE_REF should name the primary source and specific reference (e.g. "Tao Te Ching, Chapter 44" or "Letter 17" or "Walden, Economy").

For paragraphs: wrap each in `<p>...</p>`. Quotes go in `<blockquote>...</blockquote>`. Bold a person's name with `<strong>`. Italics with `<em>`. No `<h2>` or other headers inside `<div class="post-body">`.

The PREV_FILENAME and PREV_THEME should be the most recent post in posts/contentment/ before today (read index.html to find it in the Contentment & Gratitude section).

If there is no previous post in the contentment folder, use:
```html
    <nav class="post-nav">
      <div class="prev"></div>
      <div class="next"></div>
    </nav>
```

## Step 5 — Update index.html

Read /Users/jordanjunk/projects/sim/index.html. Insert a new `<li>` entry immediately after the `<!-- CONTENTMENT_START -->` comment:

```html
    <li>
      <a class="post-link" href="posts/contentment/FILENAME.html">THEME_NAME</a>
    </li>
```

No date span — just the link.

## Step 6 — Commit and push

Clone the repo fresh to /tmp to avoid any stale index.lock issues in the mounted folder, then copy in the new files and push normally:

```bash
# Resolve sim folder path dynamically
SIM=$(find /sessions -maxdepth 4 -name ".seneca-pat" 2>/dev/null | head -1 | xargs dirname)

# Read PAT
PAT=$(cat "${SIM}/.seneca-pat" | tr -d '[:space:]')

# Clone fresh to /tmp
CLONE=/tmp/seneca-push-$(date +%s)
git clone "https://${PAT}@github.com/jwjunk24/seneca.git" "$CLONE"

# Copy the new/updated files from the mounted folder
cp "${SIM}/posts/contentment/FILENAME.html" "${CLONE}/posts/contentment/FILENAME.html"
cp "${SIM}/index.html" "${CLONE}/index.html"

# Commit and push from the clean clone
cd "$CLONE"
git add posts/contentment/FILENAME.html index.html
git -c user.email="junkcompanylimited@gmail.com" -c user.name="Jordan" commit -m "THEME_NAME"
git push origin main

# Clean up
rm -rf "$CLONE"
```

If the push fails, output the error clearly. Do not retry more than once.

## Step 7 — Report

Output a single short summary: the theme name, the primary source used, the secondary source used, and whether the push succeeded or failed.
