# Level 1: Loading Screen 🕹️

**Goal:** Set up your tools, start your programmer's notebook in **Obsidian**, and learn
the most important skill in all of programming: **how to find answers on your own.**

Here's a secret about professional programmers: they don't have everything memorized.
What makes them good is that they know *how to figure things out* — reading error
messages, searching well, and reading documentation. That's a skill, and you're going to
train it from day one.

## Your tools

- **VS Code** — where you'll write code, starting Level 4.
- **Obsidian** ([obsidian.md](https://obsidian.md)) — where you'll take notes. Obsidian
  notes are plain **Markdown** files in a folder (Obsidian calls the folder a **vault**).
  That matters: because your notes are just files, they can live in the same project as
  your code, be tracked by git, and be published on GitHub — which is exactly what will
  happen in Level 3. Your notes are going public, like a real developer's blog.

In this level you'll create a folder called `spawn-point` — your home base for the whole
course — with your notes vault inside it:

```
spawn-point/
└── notes/        ← your Obsidian vault
    └── level-01.md
```

## What good notes look like

One note per level (`level-01.md`, `level-02.md`, ...), each with three sections:

```markdown
# Level 1 Notes

## Things I learned
- Markdown headings use `#`, more `#` = smaller heading
- Obsidian stores notes as plain text files — nothing is locked in

## Commands / recipes I'll forget
- `Cmd+E` in Obsidian flips between editing and reading view

## Questions for my mentor
- Why do programmers use plain text files instead of Google Docs?
```

Notes are *short* and in your own words — mostly "things I'll forget" (commands, gotchas,
definitions). The **Questions for my mentor** section is required in every level's notes;
we start each session with it.

**Obsidian's superpower — links.** Type `[[level-02]]` in a note and it becomes a link to
that note. Link your notes whenever one topic touches another, then open the **graph
view** to see your knowledge as a growing web. By Level 14 it'll look like a galaxy.

**One rule, since these go public:** first name only, no school name, no addresses, no
personal photos. Write like the internet is reading — because it will be.

## How to find answers (the Detective Method)

1. **Read the error message.** Bottom line first. It usually tells you the file, the line
   number, and what went wrong. Errors are not the computer being mean — they're hints.
2. **Search smart.** Search the *type* of error plus a few key words, not your whole
   error. Good: `python NameError name is not defined`. Bad: pasting 40 lines.
3. **Check the official docs.** For Roblox: create.roblox.com/docs. For Python:
   docs.python.org. Official docs are more trustworthy than random videos.
4. **Rubber duck it.** Explain the problem out loud, line by line, to a toy (or the cat).
   Half the time you'll spot the bug while explaining.
5. **Ask a human (or AI) — the right way.** Say what you're trying to do, what you
   expected, what actually happened, and what you already tried. That last part matters.

## Core Quests (homework, ~3-4 hrs/week)

1. **Set up your notebook.** In your `spawn-point/notes` vault, create `level-01.md` with
   all three sections (learned / recipes / questions).
2. **Markdown practice.** In `level-01.md`, use at least: 2 heading sizes, a bulleted
   list, a numbered list, **bold**, *italic*, and a code block. Flip between editing and
   reading view (`Cmd+E`) to check how it renders.
3. **Feel the links.** Create a second note called `programming-words.md` — your personal
   dictionary. Every time you meet a new word this course (vault, Markdown, error,
   variable...), add it with a one-line definition in your own words. Link to it from
   `level-01.md` with `[[programming-words]]`, then open the graph view and see your
   first connection.
4. **Detective missions.** Find and write down (in your notes, with WHERE you found it):
   - What does `NameError` mean in Python?
   - What programming language do Roblox scripts use?
   - What year was Python created, and who created it?
   - On the Roblox Creator Docs, find the page about "Scripts" and write one sentence
     about what a Script is.
5. **Write 3 questions** you have about programming in your questions section. There are
   no dumb ones — "how does the computer actually run code?" is a great question.

## Side Quests (optional)

- Change your Obsidian theme (Settings → Appearance) and pick a favorite.
- Open one of your notes in VS Code too. Same file! Nothing about your notes is trapped
  inside Obsidian — write down why that's a big deal.
- Find out what "open source" means and write it in your own words... in
  `programming-words.md`, linked.

## 🎮 Roblox Connection

The Roblox Creator Docs you explored today are the *same docs* professional Roblox
developers use every day. By the end of this course you'll be reading pages like
`HttpService` and actually using them in a real game. Bookmark the site now — and make a
`[[roblox-ideas]]` note in your vault for game ideas as they hit you. Boss Level will
want them.
