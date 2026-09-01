# HAPA — Hellenic American Psychiatric Association

A bilingual (English / Greek) single-page website for HAPA, built by [Advon Media](https://advonmedia.com).

## Files

| File | What it is |
|---|---|
| `index.html` | The whole public website. Layout, styling and behaviour — no build step, no dependencies. |
| `content.json` | **Every word on the site, in both languages.** News, officers, committees, links, membership. |
| `admin.html` | The admin panel. Edits `content.json` in a friendly interface, with English and Greek side by side. |
| `assets/` | The HAPA emblem, the hero photograph, the news photographs and the favicons. |

## Editing the site

1. Open `admin.html` on the live site (e.g. `https://…/admin.html`).
2. Enter the panel passcode. The default is `hapa2026` — change it under **Publishing → Panel passcode**.
3. Edit anything. News is the first tab; every text field has an **EN** and a **ΕΛ** box.
4. Press **Publish to the website**.

### Bilingual content

Translatable values in `content.json` are objects:

```json
"heading": { "en": "Welcome", "el": "Καλωσόρισμα" }
```

The page reads whichever language the visitor has selected and falls back to English if a Greek
string is empty. Names, emails, URLs and dates are shared between the two languages.
The visitor's choice is remembered in their browser.

### Adding a photo to a news item

Put the image in `assets/` and set the item's **Image** field to `assets/your-file.webp`.
Officers can carry a portrait the same way, through the **Photo** field.

### Publishing

Two ways to save changes:

- **Download `content.json`** and upload it to this repository yourself. Always works.
- **Publish directly.** Under **Publishing**, paste a GitHub *fine-grained personal access token* with
  **Contents: read and write** on this repository. The panel writes `content.json` straight to `main`
  and GitHub Pages redeploys within a minute or two.

The token is stored only in the editor's own browser (`localStorage`). It is never part of the
website and is never committed. If the computer is lost, revoke the token on GitHub.

The passcode on the panel is convenience, not security — anyone can view the panel's source.
The real protection is that changing the site requires the GitHub token.

## Notes

- The site is in **preview indexing state**: `noindex,nofollow` plus `Disallow: /` in `robots.txt`.
  Remove both, and update `sitemap.xml`, when the real domain goes live.
- The contact form opens the visitor's own email client — no server, no third-party form service.
- The hero photograph is a generated image of the Parthenon, used because the original site's
  banner was only 1000 × 200 px. Swap `assets/acropolis-parthenon-hero.webp` for a licensed
  photograph at any time; nothing else needs to change.
