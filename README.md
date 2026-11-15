# ENSTP Go — static site for GitHub Pages

Everything in `docs/` is the finished site. `docs/index.html` is the whole app
(guide, school presentation, timetables, campus map, assistant) — no build step, no Node.

## Publish (2 steps)

1. Put the `docs/` folder at the root of the repository `enstp-guide/enstp-connect-hub` and push
   (GitHub Desktop, or `git add docs && git commit -m "Static site" && git push`).
   The web uploader only accepts 100 files at a time and this folder has about 260, so use Git / GitHub Desktop.
2. On GitHub: **Settings → Pages → Build and deployment → Source: "Deploy from a branch"**,
   Branch `main`, folder **`/docs`** → Save.

The site appears at https://enstp-guide.github.io/enstp-connect-hub/ after a minute or two.

The "Node.js 20 is deprecated … actions/upload-artifact@v4" line is only a warning printed by
GitHub's own Pages workflow; it does not stop a deployment and can be ignored.

## Settings

Open `docs/index.html`, search for `var CFG` — four values:

| key | what it does |
| --- | --- |
| `video` / `poster` | presentation video on the home page (`''` hides it) |
| `community` | link to the online community app (needs the Lovable server). `''` hides the card |
| `ai` | optional URL of your own AI proxy. Empty = built-in assistant, which needs no credits |

## Updating content

- Timetables: replace `docs/edt/edt-*.jpg` / `.pdf` (official documents). The per-day lists come from
  `var EDT = {...}` inside `index.html`.
- Assistant pictures: `docs/images/assistant/` (`hai`, `bye`, `think`, `loading`).
- Texts, places, teachers: the data arrays inside `index.html` — the assistant and the search read
  the same data, so they update automatically.
