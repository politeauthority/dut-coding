# Level 6 Teacher Guide: Level Up Your Python 🧰

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Homework review. Play his shop game. |
| 0:10–0:25 | **Functions.** Motivate with his own code: find a repeated chunk in `shop.py` and extract it together. `def`, parameters, `return`. Analogy: you've been USING functions (`print`, `len`, `input`) all along — now you get to MAKE them. |
| 0:25–0:35 | **Files.** `open("save.txt", "w")` to write, `"r"` to read. Demo: save the player's coins to a file, quit, rerun, load them back. A program that REMEMBERS — this lands hard. |
| 0:35–0:45 | **Errors.** Revisit the Level 4 side quest: typing "banana" into `int(input())`. Now teach `try/except ValueError`. Wrap his guess-game input so it survives garbage input. |
| 0:45–1:00 | **Design the text adventure together on paper.** Rooms as a dictionary, a loop that reads commands, functions for each action. Leave with a sketch he can build from. |

## Watch for

`return` vs `print` confusion (the classic — a function that prints but
returns nothing). Also: forgetting `"w"` erases the file's old contents; let him discover
that, then explain modes.
