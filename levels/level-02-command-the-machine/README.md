# Level 2: Command the Machine ⌨️

**Goal:** Learn the terminal — the direct line to your Mac. Real programmers spend all
day here. It looks like hacker-movie stuff, and honestly, it kind of is.

Everything you do by clicking (open folders, make files, move stuff around) you can do by
*typing commands* — faster, and in ways clicking can't even do.

## Your command cheat sheet

Copy this into your notes and add to it as you learn:

| Command | What it does |
|---------|--------------|
| `pwd` | Print which folder you're in ("print working directory") |
| `ls` | List what's in this folder (`ls -l` for details, `ls -a` for hidden files) |
| `cd foldername` | Move into a folder (`cd ..` = go up, `cd ~` = go home) |
| `mkdir name` | Make a folder |
| `touch name.txt` | Make an empty file |
| `cat name.txt` | Print a file's contents |
| `cp a.txt b.txt` | Copy a file |
| `mv a.txt b.txt` | Move or rename a file |
| `rm name.txt` | Delete a file — ⚠️ FOREVER, no trash can |
| `open .` | Open the current folder in Finder |
| `echo "hi"` | Print text |
| `history` | Show commands you've run |

**Superpowers:** `Tab` = autocomplete names (use it always!), `↑` = repeat previous
commands, `Ctrl+C` = cancel whatever's happening, `q` = quit out of `man`.

## Core Quests

1. **Build out the base.** Your `spawn-point` folder already exists with your notes
   vault inside. Using ONLY the terminal (no Finder, no VS Code file panel), `cd` into it
   and build it out to this:

   ```
   spawn-point/
   ├── notes/          (already there — your Obsidian vault)
   ├── python/
   ├── web/
   └── experiments/
   ```

2. **Spy on Obsidian.** `cd` into `notes/` and run `ls`, then `ls -a`. There's a hidden
   `.obsidian` folder Obsidian uses for your settings! Look inside it with `ls .obsidian`
   — your theme choice from Level 1 is in there somewhere, as plain files. Write in your
   notes: what does a `.` at the start of a name mean on a Mac?
3. **File drills.** In `experiments/`, practice until these feel easy: create 5 files,
   rename 2 of them, copy one into a new subfolder, view one with `cat`, then delete the
   whole experiments mess and recreate it. Do this drill on 3 different days.
4. **Scavenger hunt.** Answer in your notes, using the terminal to find out:
   - How many files are on your Desktop? (hint: `ls | wc -l`)
   - What does the `-a` flag show in `ls` that plain `ls` doesn't? What are those files?
   - What does `whoami` print? What about `date`?
   - Use `man cp` (remember: `q` to quit) — what does the `-R` flag do?
5. **Notes.** `level-02.md` in your vault: your cheat sheet, things learned, questions
   for your mentor. Link `[[level-01]]` where it connects, and add new words to
   `[[programming-words]]`.

## Side Quests

- Learn `head`, `tail`, and `wc`. What do they do?
- Try `say "hello human"` in the terminal. 😄 Then find 2 more fun Mac-only commands.
- Find out what `sudo` means — but do NOT run sudo commands yet. Just learn what it is.

## 🎮 Roblox Connection

Roblox Studio saves your places and plugins as real files on your Mac. Try navigating to
`~/Documents/Roblox` in the terminal and `ls` around. Also: the pro Roblox tools you'll
meet in Level 14 (like Rojo) are *terminal programs* — no terminal skills, no pro tools.
