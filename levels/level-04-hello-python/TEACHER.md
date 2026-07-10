# Level 4 Teacher Guide: Hello, Python 🐍

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Homework review via his GitHub repo (look at commit history together — celebrate the streak). |
| 0:10–0:20 | Install Python via `uv`: `curl -LsSf https://astral.sh/uv/install.sh | sh`, then `uv python install`. Tell him: "uv is a Swiss-army tool for Python — today we only use one blade. Level 7 unlocks the rest." Run `uv run python` to get a REPL: type `2 + 2`, `"hi " * 100`. The REPL-as-calculator moment is fun. |
| 0:20–0:45 | **Write a program together** in VS Code: `hello.py` in his `python/` folder. Build up gradually: `print` → variables → `input()` → f-strings → `if/elif/else` with a number comparison. End with a mini "greeter" that asks name + age and responds differently based on age. Run with `uv run python hello.py`. |
| 0:45–0:55 | Deliberately make 3 errors together (typo a variable name, forget a quote, forget a colon) and use Level-1 detective skills to read each error. Normalize errors NOW. |
| 0:55–1:00 | Homework walkthrough. Commit and push what you wrote together. |

## Watch for

`=` vs `==` confusion, strings vs numbers (`input()` returns a string!
`int()` is needed — this WILL bite him in the number-guessing homework, let it, then help
him find it), and indentation errors. These three are the classic beginner walls.
