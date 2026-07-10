# Level 7: Power-Ups ⚡

**Goal:** Stop writing everything yourself — plug in code that thousands of programmers
have already written (third-party **packages**), managed with **uv**. Then use that power
to call real APIs on the internet... including Roblox's.

You installed uv back in Level 4 and used one blade of the Swiss-army knife. Time to open
the rest.

## The concepts

```bash
uv init my-project        # start a new Python project (creates pyproject.toml)
cd my-project
uv add rich               # install a package INTO this project
uv run main.py            # run your code with the project's packages available
```

```python
# using rich — a package that makes terminal output beautiful
from rich import print
print("[bold red]CRITICAL HIT![/bold red] :boom:")

# using requests — talk to the internet
import requests
response = requests.get("https://api.github.com/users/octocat")
data = response.json()        # JSON becomes dicts and lists — Level 5 skills!
print(data["name"])
```

`pyproject.toml` is your project's mod list — anyone (including future-you) can recreate
your exact setup from it. That's why it gets committed to git.

## Core Quests

1. **`uv init` a project called `api-explorer`** inside your `python/` folder. Commit the
   `pyproject.toml` so your mentor can see your dependencies.
2. **Pimp your adventure.** Add `rich` and give your text adventure colored output — red
   damage, green pickups, a styled title screen. (Copy your adventure into the new
   project, or `uv init` inside its folder.)
3. **`roblox_lookup.py`** — the cool one. Roblox has public APIs. Build a tool that asks
   for a Roblox username and prints their profile info:
   - `POST https://users.roblox.com/v1/usernames/users` with a JSON body
     `{"usernames": ["thename"]}` gets you their user id
     (hints: `requests.post(url, json={...})`, and the answer comes back wrapped in a
     `"data"` list — print the whole response first and dig in)
   - `GET https://users.roblox.com/v1/users/<id>` gets their display name, description,
     and join date
   - Print it nicely with `rich`. Try it on your own username!
4. **Explore one more API** of your choosing and build something tiny with it. Ideas:
   `https://official-joke-api.appspot.com/random_joke`, a weather API, the pokéapi.
   The quest here is *reading unfamiliar docs and figuring out the JSON shape yourself.*
5. **Notes** (`level-07.md`): what's a package? What's an API? What's JSON? In your own
   words, plus questions.

## Side Quests

- Browse pypi.org and write down 3 packages that sound cool and what they do.
- Add a `--fancy` mode to `roblox_lookup.py` that also fetches their avatar thumbnail URL
  (search the Roblox docs for the thumbnails API — detective mode).
- Ask your mentor about what `uv sync` and the `uv.lock` file are for.

## 🎮 Roblox Connection

This level IS the Roblox connection — you just talked to Roblox's real servers, the same
ones the Roblox app uses. In the Boss Level, this flow reverses: your *game* will call
*your* API. Same `requests`-style idea, opposite direction. You now know both sides of
the conversation.
