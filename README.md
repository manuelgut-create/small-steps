# Small Steps — website

The public pages for the Android app **Small Steps: Habit Tracker**: privacy
policy, support, and the German Impressum.

Served by GitHub Pages from `main` / root:

- <https://manuelgut-create.github.io/small-steps/>
- <https://manuelgut-create.github.io/small-steps/privacy.html>
- <https://manuelgut-create.github.io/small-steps/support.html>
- <https://manuelgut-create.github.io/small-steps/impressum.html>

Plain HTML and one stylesheet. No build step, no framework, no scripts, and no
third-party requests — a privacy policy that loaded a third-party font would
contradict its own text.

| File | Purpose |
| --- | --- |
| `index.html` | Landing page |
| `privacy.html` | Privacy policy, German with an English version below |
| `support.html` | Support and FAQ, German and English |
| `impressum.html` | German provider identification (§ 5 DDG) |
| `style.css` | Everything visual; light and dark, follows the system setting |
| `icon.svg` | Favicon — the app mark, local so nothing is fetched elsewhere |

## Keeping it honest

If the app ever changes what it does with data, `privacy.html` has to change with
it. The current text matches the app as built: no account, no server, no
tracking, a local database, local notifications, purchases through Google Play,
and Android auto-backup left on.
