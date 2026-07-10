# Roblox Primer for the Mentor

You're a professional programmer who has never touched Roblox. This is everything you
need to teach Levels 13–14 (and field Roblox questions throughout) without embarrassment.

## The platform in 90 seconds

Roblox is three things: a **client app** players use to browse and play games (Roblox
calls them **experiences**), a **cloud hosting platform** — when someone plays a game,
Roblox spins up authoritative game servers in *their* datacenters, you never host game
servers yourself — and **Roblox Studio**, the free IDE + engine you build in (think Unity
editor, but the deploy target is always Roblox's cloud). An experience contains one or
more **places** (levels/worlds); scripting is in **Luau**, Roblox's fork of Lua 5.1 with
gradual typing and performance work. Your student builds in Studio on his Mac, hits
Publish, and Roblox handles distribution, hosting, and multiplayer netcode.

## Mental model mapping (pro concept → Roblox)

| You know | Roblox equivalent |
|----------|-------------------|
| IDE + engine | Roblox Studio |
| The DOM / scene graph | The **DataModel**: everything is an **Instance** in one big tree (the Explorer panel is the tree view; Properties panel beside it) |
| Singletons / DI container | **Services**: `game:GetService("Players")`, `Workspace`, `HttpService`... |
| `console.log` + terminal | `print()` / `warn()` → the **Output** window (hidden by default: View → Output — open it first thing, always) |
| Server vs. client code | **Script** (runs on server) vs. **LocalScript** (runs on each player's client). Server is authoritative by default |
| Shared modules / imports | **ModuleScript** + `require()` |
| RPC / message bus between server & client | **RemoteEvent** / **RemoteFunction** (out of scope for this course — we stay server-side) |
| Try/except | `pcall(function() ... end)` → returns `ok, result` |
| `fetch` / `requests` | **HttpService** (`GetAsync`, `PostAsync`, `RequestAsync`, `JSONEncode`/`JSONDecode`) |
| Redis/Postgres for player data | **DataStoreService** (managed KV store per experience); **OrderedDataStore** for ranked data |
| git-friendly source layout | **Rojo** — syncs a filesystem project into Studio; without it, code lives inside the binary place file |
| npm | **Wally** (community package manager) |
| Prettier / ESLint | **StyLua** / **Selene** |
| Deploy to prod | File → **Publish to Roblox** (an experience can be private — publish ≠ public) |

## Luau vs. Lua vs. Python — what to know

- Tables are the only data structure — they're arrays AND dicts (like PHP arrays or JS
  objects). **1-indexed.** `#t` is length, `table.insert`/`table.remove` for array ops.
- `local` for variable declarations (globals are the default without it — teach `local`
  always).
- String concat is `..` (numbers coerce fine). Modern Luau also has backtick
  interpolation: `` print(`HP: {health}`) `` — closest thing to f-strings; fine to teach.
- `nil` ≈ `None`; only `nil` and `false` are falsy (0 and "" are truthy — differs from
  Python!).
- `~=` is "not equal" (not `!=`).
- Use `task.wait(n)` for sleeping; plain `wait()` is deprecated.
- Events are the paradigm: `something.EventName:Connect(fn)`. The course frames this as
  "callbacks you register" — the genuinely new concept vs. the Python levels.
- Luau has optional type annotations (`local x: number = 5`). Ignore them for this
  course.

## The three settings that eat sessions (all verified against current docs)

All live in **Home tab → Game Settings → Security**, and **Game Settings is only
clickable after the place is published** (File → Publish to Roblox — free, can stay
private). Publish early in the Level 13 session so this never blocks you.

1. **Allow HTTP Requests** — required for `HttpService` (Level 14). Off by default.
2. **Enable Studio Access to API Services** — required for DataStores to work in Studio
   playtests (Level 13 side quest). Off by default. Real-world caveat worth mentioning
   to him: Studio hits the *production* data stores, so pros use a test copy of the
   experience.
3. Both are per-experience, not per-account — a new project means flipping them again.

## HttpService — the Level 14 load-bearing wall

- **Server scripts only.** A LocalScript calling HttpService errors.
- Rate limit: **~500 requests/minute per game server.** The course's 30-second
  leaderboard poll uses 2/min; a buggy loop without `task.wait` will exhaust it and
  requests stall for ~30s.
- **Cannot call `roblox.com` domains** from in-game — deliberate. (His Level 7 Python
  scripts CAN call `users.roblox.com`; that's outbound from his Mac, different story.
  Official in-game-adjacent automation is **Open Cloud**, see below.)
- All the Async functions **yield** and **throw on failure** — always wrap in `pcall`.
- **Why localhost works in Studio:** playtests (the Play button, F5) run both the
  simulated server and client *on the local machine*, so `http://localhost:5000` reaches
  his Flask app. Once the game runs on Roblox's real cloud servers, localhost is
  meaningless — that's the Level 14 tunnel discussion (ngrok/cloudflared for a demo;
  real deployment is out of scope).

## Patterns the course uses (so you recognize them)

**leaderstats** — a magic-named convention: put a Folder named exactly `leaderstats` on a
Player object, add Value instances (e.g. an IntValue named "Coins"), and Roblox's built-in
player list UI displays them automatically. It's THE beginner pattern, used in Level 13:

```lua
local Players = game:GetService("Players")
Players.PlayerAdded:Connect(function(player)
    local stats = Instance.new("Folder")
    stats.Name = "leaderstats"
    stats.Parent = player
    local coins = Instance.new("IntValue")
    coins.Name = "Coins"
    coins.Parent = stats
end)
```

**Touched + debounce** — `part.Touched` fires many times per physical contact (every
touching body part, every physics frame). The Level 13 coin quest deliberately lets him
hit this; the fix is a boolean flag (a "debounce" in Roblox jargon). It's the platform's
classic first bug.

**Kill brick** — `humanoid.Health = 0` on touch. Every Roblox kid has seen one; building
it demystifies it.

## The pro ecosystem (Level 14 side quests / where he goes next)

- **Rojo** ([rojo.space](https://rojo.space)) — two-way sync between a filesystem project
  and Studio. This is how real studios get git, code review, and CI. It's a CLI tool +
  Studio plugin; `rojo init`, `rojo serve`, connect from the plugin. Genuinely worth an
  extra session if he's hooked — it makes his game a real repo.
- **Open Cloud** ([create.roblox.com/docs/cloud](https://create.roblox.com/docs/cloud)) —
  official REST APIs authenticated with API keys (created on the Creator Hub): read/write
  your experience's DataStores, publish places, send cross-server messages — from
  Python. This is the sanctioned way his Level 7 skills touch his own game from outside.
- **Wally, StyLua, Selene, luau-lsp** — package manager, formatter, linter, VS Code
  language server. Name-drop only.

## Kid-safety / account notes

- He's 13, so his account has 13+ defaults; parental controls live in account settings.
  Nothing in this course requires spending Robux or any money.
- Publishing an experience does NOT make it public — visibility is a separate toggle
  ("Private"/"Public" on the Creator Hub). Keep it private until the graduation demo;
  making it public is a fun family decision, not a requirement.
- Enabling HTTP means his game code can talk to arbitrary internet hosts. For this course
  it only talks to his own API — worth a glance at any script a tutorial tells him to
  paste (free-model scripts with sketchy webhooks are a real thing in the Roblox
  ecosystem; "read every script you paste" is good hygiene and on-theme for the course).

## Where the course touches Roblox — quick map

| Level | Touchpoint | What you need |
|-------|-----------|----------------|
| 1 | Creator Docs as a documentation example | Nothing |
| 2 | `~/Documents/Roblox` in the terminal | Only exists if Studio has saved local files — skip gracefully if empty |
| 4–6 | Python↔Luau comparison callouts | Nothing — just read them |
| 7 | Python calls `users.roblox.com` public APIs | No auth needed; POST `/v1/usernames/users`, GET `/v1/users/<id>` |
| 13 | Studio, Luau, obby, leaderstats | Publish the place; Output window open; API-services toggle for the DataStore side quest |
| 14 | HttpService → his Flask API | Publish + Allow HTTP Requests; playtest = localhost works; match the port if you moved off 5000 |

## Prep checklist before Level 13's session

- [ ] Install Roblox Studio on your own Mac and spend 30 minutes: make a baseplate, add
      a Part, add a Script to it, make the lava brick from Level 13, playtest with F5.
      That half hour is all the credibility you need.
- [ ] Create your own Roblox account if you don't have one (Studio requires login).
- [ ] Skim the official intro tutorial track at
      [create.roblox.com/docs/tutorials](https://create.roblox.com/docs/tutorials) —
      you'll recognize everything as "Unity-flavored web dev."
- [ ] Bookmark the [Luau/engine API reference](https://create.roblox.com/docs/reference/engine)
      — `Instance`, `BasePart`, `Players`, `HttpService` are the pages this course uses.

## Links

- Creator Docs (everything): https://create.roblox.com/docs
- Engine API reference: https://create.roblox.com/docs/reference/engine
- HttpService: https://create.roblox.com/docs/cloud-services/http-service
- Data stores: https://create.roblox.com/docs/cloud-services/data-stores
- Luau language site: https://luau.org
- DevForum (the Stack Overflow of Roblox): https://devforum.roblox.com
- Rojo: https://rojo.space · Open Cloud: https://create.roblox.com/docs/cloud
