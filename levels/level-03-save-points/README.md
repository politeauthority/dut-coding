# Level 3: Save Points 💾

**Goal:** Learn git and GitHub — the save system of programming. From this level on, ALL
your homework gets pushed to GitHub, and your mentor reviews it before each session.

In games, you'd never play a hard level without save points. git gives your code save
points (**commits**) you can always return to, and GitHub puts your saves in the cloud so
they're safe and shareable. Every professional programmer on Earth uses this. Every day.

## Your notes go public 📣

Your whole `spawn-point` folder — code AND your Obsidian vault — becomes a public GitHub
repo this level. That's on purpose: real developers publish their notes and learning in
public, and future-you will love having this record. GitHub even renders Markdown, so
your notes are readable right on the website. Remember the Level 1 rule: first name only,
nothing personal. Give your vault a read-through before the big push.

## The daily loop (memorize this)

```bash
git status                     # what changed?
git add .                      # stage everything ("put it in the chest")
git commit -m "what I did"     # save point!
git push                       # upload to GitHub
```

And to see your history: `git log --oneline` — your list of save points.

## Core Quests

1. **Make it official.** Your `spawn-point` folder is now a git repo pushed to GitHub.
   Add a `README.md` at the top describing who you are and what this repo is (use your
   Markdown skills — this page is your programmer identity!).
2. **Build the commit habit.** Every time you sit down to do homework this cycle, end by
   committing and pushing. By next session your `git log` should show **at least 6
   commits** with real messages. (This proves you worked multiple days — that's the point.)
3. **Time travel drill.** In `experiments/`: make a file, commit it, change it, commit
   again, then run `git log --oneline` and `git diff HEAD~1` to see what changed between
   your save points. Write in your notes what `diff` showed you.
4. **Break it and fix it (safely).** Change a file, DON'T commit, then run
   `git checkout -- filename` (or `git restore filename`). Where did your changes go?
   Write down what happened — you just used a save point to undo a mistake.
5. **Notes.** `level-03.md`, committed and pushed, with the daily loop written from
   memory and your questions.

## Side Quests

- Explore GitHub: find the repo for Python itself (`python/cpython`). How many people
  have contributed?
- Put a fun profile picture and bio on your GitHub account.
- Find out what a "branch" is. Just the idea — we'll use them later.

## 🎮 Roblox Connection

Big Roblox studios (the teams behind games like Adopt Me) keep their game code in git,
just like this. A tool called **Rojo** syncs files between a git repo and Roblox Studio so
whole teams can work on one game without overwriting each other. In the Boss Level,
your Roblox scripts will live in this very repo.
