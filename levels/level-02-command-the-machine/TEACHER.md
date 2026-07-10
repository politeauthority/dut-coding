# Level 2 Teacher Guide: Command the Machine

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Review Level 1 homework: read his notes in Obsidian (check the graph view — is `programming-words` linked?), answer his questions. |
| 0:10–0:20 | Open Terminal.app. Demystify: "this is just another way to talk to your Mac." Do `pwd`, `ls`, `cd Desktop`, `ls` — show that these are the SAME folders Finder shows. Open Finder side by side to prove it. Then `cd` into his `spawn-point` folder and `ls` — his notes vault is right there. |
| 0:20–0:40 | **Drive together:** `mkdir`, `cd`, `touch`, `mv`, `cp`, `cat`, `open .`. Then the power tools: tab-completion (this is the big quality-of-life unlock — drill it), `↑` for history, `Ctrl+C` to bail out. Show `rm` LAST with a warning: no trash can in the terminal. |
| 0:40–0:50 | Show `ls -l` and explain flags. Show `--help` and `man ls` (press `q` to quit!). One fun pipe: `ls | wc -l` — "commands can feed each other." |
| 0:50–1:00 | Walk through homework. Do the first `mkdir` inside `spawn-point` together so he starts from a working state. |

## Watch for

- `man` pages trap kids — teach `q` immediately.
- Spaces in filenames will bite him — teach quotes or the `no-spaces-in-names` habit.
- Emphasize tab-completion constantly; it prevents most typo frustration.
- The `rm` warning is real: make sure drills happen inside `experiments/`, never in the
  notes vault.
