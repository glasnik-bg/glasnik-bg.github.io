# glasnik.bg

Public website for **ГЛАСНИК ООД (GLASNIK LTD OOD)** — the anonymous professional
community platform for Bulgaria and Central & Eastern Europe.

Static site, deployed to GitHub Pages from `main` by `.github/workflows/static.yml`.
Served at **https://glasnik.bg** via the `CNAME` file.

## Pages

| File | Purpose |
| --- | --- |
| `index.html` | Home — product overview, waiting-list form, company block |
| `company.html` | Registered company details — the page an Apple reviewer looks for |
| `contact.html` | Contact addresses and registered office |
| `support.html` | User support — the App Store Connect *Support URL* |
| `privacy.html` | Privacy policy — the App Store Connect *Privacy Policy URL* |
| `terms.html` | Terms of Service |
| `guidelines.html` | Community Guidelines |
| `cookies.html` | Cookie Policy |
| `employers.html` | For Employers |
| `delete-account.html` | Account deletion — required by App Store Guideline 5.1.1(v) |
| `site.css` | The single stylesheet for every page |
| `img/` | Logo (`logo.png`), wordmark artwork (`wordmark.png`, `wordmark-white.png`), favicon, Apple touch icon and the social-share image (`og.jpg`). Exported from the app repo (`frontend/assets`, October 2026 logo) |
| `img/avatars/` | The app's own avatar illustrations (SVG), used in the example posts and the phone mock-up |
| `fonts/` | Manrope, the app's typeface, self-hosted (SIL Open Font License, `fonts/OFL.txt`) so the site makes no requests to Google or any other third party |

All pages share one header (logo + wordmark images), one footer and one stylesheet. The look follows the app's dark theme: surface `#0B1530`, cards `#13213F`, primary `#8EBFF5`, coral `#F07152`, logo gradient `#0969D0 → #0548A8 → #032D79`. If you add a page, copy
the `<header class="site">` and `<footer class="site">` blocks from any existing
page verbatim so the chrome stays identical.

## Registered company details

These appear in the footer of every page and in full on `company.html`:

```
ГЛАСНИК ООД (GLASNIK LTD OOD)
ЕИК / UIC 208861127 · VAT BG208861127
18A Neofit Hilendarski str., Vitosha District, Sofia 1434, Bulgaria
```

The Latin name must match the D-U-N-S record character for character — Apple's
verification team compares them.

## Before submitting the Apple enrolment

1. Point DNS for `glasnik.bg` at GitHub Pages:

   ```
   A     @   185.199.108.153
   A     @   185.199.109.153
   A     @   185.199.110.153
   A     @   185.199.111.153
   CNAME www glasnik-bg.github.io.
   ```

   Then **Settings → Pages → Custom domain → `glasnik.bg`**, and tick
   **Enforce HTTPS** once the certificate issues.

2. Make sure these mailboxes receive mail: `contact@`, `support@`, `privacy@`,
   `legal@`.

3. Load `https://glasnik.bg` from outside your own network and confirm it serves
   over HTTPS with the company name visible.

## Waiting-list form

`index.html` posts `{username, email}` as JSON to an Azure Logic App HTTP trigger.
The endpoint URL is in the inline script at the bottom of that file.

## Legal pages

The source of truth for the legal text is `legal/*.md` in the app repository. When a
policy changes there, update the matching page here. The privacy policy here carries the
October 2026 additions (2.6 Crash reports, password-reset emails, crash-report legal basis).

## Home page

`index.html` shows the app as it really looks: the example cards in *What we do* and the
phone in *The app* are built from the app's own colours, typeface, avatars and layout
(Home, Guilds, a post with comments, and the anonymous composer). The content in them is
illustrative. When the app's design changes, update these to match. The page has no
external dependencies: no CDN, no web fonts from Google, no tracking.
