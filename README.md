# HAPA — Hellenic American Psychiatric Association

A single-page website for HAPA, built by [Advon Media](https://advonmedia.com).

## Files

| File | What it is |
|---|---|
| `index.html` | The whole public website. Layout, styling and behaviour — no build step, no dependencies. |
| `content.json` | **Every word on the site.** News, officers, committees, links, membership details. |
| `admin.html` | The admin panel. Edits `content.json` in a friendly interface. |
| `assets/` | The HAPA emblem, the Acropolis header image and the favicons. |

## Editing the site

1. Open `admin.html` on the live site (e.g. `https://…/admin.html`).
2. Enter the panel passcode. The default is `hapa2026` — change it under **Publishing → Panel passcode**.
3. Edit anything. News items are on the first tab.
4. Press **Publish to the website**.

### Publishing

There are two ways to save changes:

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
  Swap the `<form>` handler for a Formspree endpoint if a server-side inbox is wanted later.
