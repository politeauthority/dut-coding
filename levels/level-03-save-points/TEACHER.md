# Level 3 Teacher Guide: Save Points

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Review Level 2 homework — have him drive: navigate his `spawn-point` folder in the terminal while you watch. |
| 0:10–0:20 | Concept with a whiteboard/paper: working folder → `git add` (choose what to save) → `git commit` (save point with a label) → `git push` (upload save to cloud). Analogy: add = putting items in the chest, commit = locking the chest with a label, push = backing it up to the cloud. |
| 0:20–0:40 | **Do it live:** create his GitHub account (needs a parent-approved email), `git init` inside `spawn-point/`, first `git add . && git commit`, create the GitHub repo (public!), connect it, push. Seeing his files — including his notes, rendered — appear on github.com is the magic moment; don't rush it. Browse his vault on GitHub together. |
| 0:40–0:50 | The daily loop: edit → `git status` → `git add` → `git commit -m "message"` → `git push`. Show `git log`. Show what a good commit message looks like ("add level 2 notes", not "stuff"). |
| 0:50–1:00 | Homework walkthrough. Set expectation: from now on, "done" means "pushed" — notes included. |

## Setup notes

- git ships with macOS (may trigger the Xcode Command Line Tools install — do it during
  the session if needed).
- Set up `git config --global user.name` / `user.email` together.
- For GitHub auth, the `gh auth login` flow via the [GitHub CLI](https://cli.github.com)
  or a fine-grained token — HTTPS + credential manager is simplest for a first-timer.
- **Obsidian + git:** commit the vault as-is, but consider a `.gitignore` with
  `notes/.obsidian/workspace*` — Obsidian rewrites those workspace files constantly and
  they'd pollute every `git status`. Writing his first `.gitignore` together is a nice
  teachable moment ("some files are yours, not the project's"). The rest of `.obsidian/`
  (theme, settings) is fine to commit.
- Before the first push, skim the vault together for personal info — easier to catch now
  than to scrub from git history later.

## Watch for

- The vim commit-message trap — set `git config --global core.editor "code --wait"` or
  teach `-m` from the start.
- Kids panic at `git status` red text; teach that red just means "not staged yet."
- If he edits notes in Obsidian mid-homework and forgets to push, the streak looks
  broken — tie "close Obsidian for the day" to "run the daily loop."
