# Level 1 Teacher Guide: Loading Screen

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Tour of the course: show the README map, explain levels/quests/the AI rule. Get him excited about the Boss Level. |
| 0:10–0:25 | Install VS Code and Obsidian together. Create the `spawn-point` folder with a `notes` vault inside (use Obsidian's "Create new vault" dialog and choose the location deliberately — this exact folder becomes his git repo in Level 3). Write his first Markdown note together — headings, lists, code blocks, and `Cmd+E` to flip between editing and reading view. |
| 0:25–0:35 | **Obsidian hooks:** make a `[[programming-words]]` link, click it to create the note, then open graph view to show the connection. Mention: "your notes will be public on GitHub in a few weeks, like a real dev blog" — and have the personal-info talk now (first name only, no school, etc.). |
| 0:35–0:45 | **Detective training.** Show a real error message (make Python print a `NameError` on your machine). Teach the reading order: last line first, what file/line, what did it *expect*. Then demo a good search: paste the error type, not the whole wall of text. |
| 0:45–0:55 | Tour of documentation: open the [Roblox Creator Docs](https://create.roblox.com/docs) and [Python docs](https://docs.python.org/3/) side by side. Point out: docs look scary, but you only read the tiny part you need. |
| 0:55–1:00 | Walk through the homework. Make sure Obsidian opens the vault and VS Code launches before you leave. |

## Watch for

- Kids often think notes = copying everything. Emphasize: notes are *short*, in your own
  words, and mostly "things I'll forget" (commands, gotchas, definitions).
- Obsidian's first-run screens (sync/account prompts) can be skipped — no account needed
  for a local vault.
- Put the vault INSIDE `spawn-point/`, not in iCloud's default location — iCloud syncing
  a git repo causes weird behavior later. Keep it in the home folder.
- The public-notes conversation is easier now than retroactively scrubbing personal info
  at Level 3. Set the norm on day one.

## Prep before the session

- Have download pages ready (or installers pre-downloaded): VS Code, Obsidian.
- Have a terminal ready with Python available to produce the demo `NameError`.
