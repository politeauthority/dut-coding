# Level 8: Your Corner of the Internet 🌐

**Goal:** Learn HTML and CSS — the languages every website is made of — and publish a
real website, live on the internet, for free, using GitHub Pages.

## The concepts

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Alex's Site</title>
    <style>
      body   { font-family: sans-serif; background: #1a1a2e; color: #eee; }
      h1     { color: #e94560; }
      .card  { border: 2px solid #0f3460; padding: 16px; border-radius: 12px; }
    </style>
  </head>
  <body>
    <h1>Welcome to my site</h1>
    <p class="card">I'm learning to code. Here's my
       <a href="https://github.com/USERNAME">GitHub</a>.</p>
    <img src="cool.png" alt="something cool">
    <ul>
      <li>I like Roblox</li>
      <li>I'm building a text adventure</li>
    </ul>
  </body>
</html>
```

HTML = nested boxes with meaning (`h1` heading, `p` paragraph, `a` link, `img` image,
`ul/li` lists, `div` generic box). CSS = rules that say "boxes like THIS should look like
THAT." That's genuinely most of it.

## Core Quests

1. **Claim your magic repo.** GitHub has a special repo name: a public repo called
   exactly `USERNAME.github.io` (your GitHub username) automatically becomes a live
   website at that address. Create it on github.com, then `git clone` it NEXT TO your
   `spawn-point` folder (not inside it — never put a git repo inside another git repo).
   Your site lives in this new repo; `spawn-point/web/` stays for experiments.
2. **Build your personal site** with at least 3 pages linked to each other:
   - `index.html` — home: who you are (first name only!), what you're learning
   - `projects.html` — your text adventure, your API explorer... with descriptions and
     links to the code on GitHub
   - one free-choice page — favorite games, a top-10 list, anything
3. **Style it.** A shared look across pages: custom colors, at least one class you made
   up, centered content, and hover effects on links (`a:hover { ... }` — look it up on
   MDN, detective!).
4. **Publish it.** Push, wait a minute or two, then visit `https://USERNAME.github.io`.
   Put the live URL at the top of your `spawn-point` README.
5. **The layout challenge:** make a row of 3 "card" boxes side by side. You'll probably
   discover `display: flex` while searching. That's the point — searching for CSS
   answers is a daily pro activity.
6. **Notes** (`level-08.md`): what's the difference between HTML and CSS? What does a
   browser actually do? Questions.

## Side Quests

- Add a favicon (the little tab icon). Search: "html favicon".
- Find a Google Font you like and use it. Search: "google fonts how to use".
- Make the site look good on a phone. Search: "responsive design viewport meta".
- Peek at JavaScript: add a button with `onclick="alert('hi')"`. JS = the third language
  of the web; it makes pages *do* things. We'll meet it properly later.

## 🎮 Roblox Connection

roblox.com is HTML and CSS (plus a lot of JavaScript). Now that you can read page source,
inspect it! Also: many Roblox games have community sites, wikis, and Discord landing
pages — game devs who can build a web presence have a real edge. Your `projects.html`
will eventually show off your Boss Level game.
