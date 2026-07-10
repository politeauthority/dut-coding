# Level 5 Teacher Guide: Loops & Loot 🔁

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Review homework from GitHub. Have him demo `number_guess.py`. |
| 0:10–0:25 | **Loops.** Start with `while`: upgrade his `number_guess.py` LIVE to allow unlimited guesses until correct. This is a huge "whoa" moment — his own game gets better. Then `for i in range(10)`. |
| 0:25–0:40 | **Lists.** `inventory = ["sword", "shield", "potion"]` — index, `append`, `remove`, `len`, and looping over it. Frame everything as game inventory. |
| 0:40–0:50 | **Dictionaries.** `player = {"name": "Alex", "hp": 100, "coins": 50}` — lookup by key, change values, add keys. Analogy: a list is a numbered backpack, a dict is a labeled chest. |
| 0:50–1:00 | Homework walkthrough. Sketch the shop program on paper together first — teach "plan before code." |

## Watch for

Infinite `while` loops (teach `Ctrl+C` as the escape hatch — connect back
to Level 2), off-by-one confusion with `range`, and list indexes starting at 0. The
0-index thing needs saying about ten times; that's normal.
