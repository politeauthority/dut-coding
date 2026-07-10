# Level 8 Teacher Guide: Your Corner of the Internet 🌐

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Homework review. Run his Roblox lookup tool on your username. |
| 0:10–0:20 | The big reveal: right-click → "View Page Source" on a site he likes (do roblox.com!). Every website is just text files. HTML = the bones (content/structure), CSS = the skin (looks). The browser is a program that turns those files into pictures. |
| 0:20–0:40 | **Build together:** `index.html` in his `web/` folder — `h1`, `p`, `img`, `a`, `ul`. Open it in the browser (`open index.html`). Then add a `<style>` block: colors, fonts, centering. Change something, refresh, see it — drill that loop. |
| 0:40–0:50 | **Publish.** Create the `username.github.io` repo on GitHub, clone it next to `spawn-point`, copy `index.html` in, push. (Pages auto-enables for that repo name; deploys take a minute or two — narrate the wait.) Load his site ON HIS PHONE. This is the biggest magic moment of the whole course — his own URL, on the real internet. |
| 0:50–1:00 | Homework walkthrough. Show him MDN (developer.mozilla.org) — the official docs of the web. |

## Watch for

The site must live in its own `username.github.io` repo — GitHub Pages only serves from a
repo root or a `/docs` folder, so his `spawn-point/web/` folder can't be published
directly. Keep the new repo NEXT TO `spawn-point`, never nested inside it. Also: unclosed
tags producing weird layouts (teach the VS Code auto-close +
indent trick), and case-sensitive file paths for images. Also decide together what's OK
to publish publicly — first name only, no school, no personal photos he wouldn't want
public. Good early internet-safety conversation.
