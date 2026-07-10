# Level 7 Teacher Guide: Power-Ups ⚡

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Homework review — PLAY THE ADVENTURE GAME. Make a fuss; it's his biggest build yet. |
| 0:10–0:20 | Concept: packages = mods for Python. PyPI = the marketplace. Why projects need their own dependency list (two projects, different needs) → that's what `uv init` + `pyproject.toml` handle. Skip deep venv theory; "uv keeps each project's mods separate" is enough at 13. |
| 0:20–0:35 | **Live:** `uv init fun-tools`, look at `pyproject.toml`, `uv add rich`, then make a script print a rainbow table or progress bar with `rich`. Instant visual payoff. |
| 0:35–0:50 | **APIs.** `uv add requests`. Explain: an API is a website for programs — you ask a URL, you get data (JSON) back, and JSON is just Python dicts/lists in text form. Call a fun API together (e.g. a joke API or `api.github.com/users/<his-username>`), print fields from the response. |
| 0:50–1:00 | Homework walkthrough. Show him where package docs live (pypi.org, the rich docs) — Level 1 detective skills now apply to OTHER people's code. |

## Watch for

Confusion about "why doesn't `import rich` work in my old folder" —
reinforce: packages belong to a *project* now, run things with `uv run` from inside it.
Also JSON nesting (`data["a"][0]["b"]`) takes practice — do one together slowly.
