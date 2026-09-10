# Small Steps — website

The two pages Google Play requires (privacy policy, support) plus a German
Impressum and a small landing page. Plain HTML and one stylesheet: no build
step, no framework, no scripts, no third-party requests.

That last point is deliberate. A privacy policy that loads a third-party font
would contradict its own text. Verified by searching every file for `http`:
four hits, none of them a request the browser makes. Two are the supervisory
authority's link in `privacy.html` (German and English section), one is the Play
Store link on the landing page — all three are `href`s the reader clicks — and
the fourth is the `xmlns` namespace identifier in `icon.svg`, an XML name that
is never fetched.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | Landing page |
| `privacy.html` | **Privacy policy — the URL Play requires.** German, English below |
| `support.html` | Support and FAQ, German and English |
| `impressum.html` | German provider identification (§ 5 DDG) |
| `style.css` | Everything visual; light and dark, respects the system setting |
| `icon.svg` | Favicon — the app mark, inline SVG, no external request |

## Nothing left to fill in

The last placeholder — the Play Store link on the landing page — went in on
10 September 2026, once the app was live in production. There is no `class="todo"`
marker left anywhere, and the style that rendered it has been removed from
`style.css` so a new one cannot be added by accident.

The VAT section is **absent on purpose**, because no VAT id was supplied. If one
exists, it has to go back in: a missing but required VAT id is a defect in the
Impressum.

## Two rules these pages follow

**Nothing on a public page explains itself to the developer.** The Impressum
used to carry a card saying it was "eine sorgfältig gebaute Vorlage, aber keine
Rechtsberatung" and a note arguing why no phone number was needed; the privacy
policy explained *why* it avoided the phrase "your data never leaves your
device". All of that was written for whoever maintains the site, and it was
sitting on pages meant for visitors. It is gone. The substance it was wrapped
around — Android's automatic backup really does copy the database into the
user's own Google account — is stated as a fact in its own section instead.

**A dead legal link is worse than none.** The EU online-dispute (OS) platform
was shut down on 20 July 2025, and since then linking to it can itself be
treated as anticompetitive. The link is removed; the § 36 VSBG statement about
not participating in consumer arbitration stays, because that obligation did
not go away with the platform.

## Publishing on GitHub Pages

Live at `manuelgut-create/small-steps`, files at the repository root, deployed
by the `pages-build-deployment` workflow on every push to `main`.

**Updating a page:** this folder is not a git working copy, so the practical
route is *Add file → Upload files* on the repository, dropping the changed files
in by their existing names, committing directly to `main`. The workflow then
redeploys; a run takes well under a minute.

If it ever has to be set up again:

1. Create a **public** repository, for example `small-steps`.
2. Copy the contents of this folder into it (the files at the repository root,
   not inside a `site/` folder).
3. Repository → **Settings → Pages** → Source: *Deploy from a branch*, branch
   `main`, folder `/ (root)` → Save.
4. After a minute the pages are live at:

```
https://manuelgut-create.github.io/small-steps/privacy.html
https://manuelgut-create.github.io/small-steps/support.html
```

GitHub Pages also serves these without the extension
(`…/small-steps/privacy`). Either form works in the Play Console; use whichever
you paste consistently.

5. Open both URLs in a private window to confirm they load **without being
   logged in**. Play rejects a privacy policy that is not publicly reachable.

## Keeping it honest

If the app ever changes what it does with data, this policy has to change with
it. The current text matches the app as built: no account, no server, no
tracking, local database, local notifications, purchase through Google Play,
and Android auto-backup left on.
