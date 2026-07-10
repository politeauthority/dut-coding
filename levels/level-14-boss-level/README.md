# Level 14: 🏆 BOSS LEVEL — Connect Everything

**Goal:** Your Roblox game talks to YOUR backend. When a player finishes your obby, the
game sends their score over HTTP to your Flask API, which stores it in Postgres and ranks
it in Redis, and a global leaderboard appears in-game. Every single level of this course
is load-bearing in this build. This is a real, professional architecture — built by you.

```
Roblox game (Luau) ──HTTP──▶ Flask API (Python) ──▶ Postgres (permanent record)
        ▲                        │                └▶ Redis (live rankings)
        └────── leaderboard ◀────┘        ...all running in docker compose
```

## The key new code

Luau's `requests` is **HttpService** (server scripts only!):

```lua
local HttpService = game:GetService("HttpService")
local API = "http://localhost:5000"     -- works in Studio playtests

local function submitScore(playerName, score)
    local body = HttpService:JSONEncode({player = playerName, score = score})
    local ok, err = pcall(function()      -- pcall = try/except, Luau edition
        HttpService:PostAsync(API .. "/api/scores", body,
            Enum.HttpContentType.ApplicationJson)
    end)
    if not ok then
        warn("Score upload failed: " .. tostring(err))
    end
end

local function getLeaderboard()
    local ok, result = pcall(function()
        return HttpService:JSONDecode(
            HttpService:GetAsync(API .. "/api/leaderboard"))
    end)
    if ok then return result else return {} end
end
```

## The Boss Fight (final project checklist)

Build it in phases — commit messages tell the story:

**Phase 1 — score submission.** Finish pad calls `submitScore` with the player's name and
coins. Prove scores land in Postgres (your `test_client.py` is now a debugging tool —
notice how every old project keeps becoming a tool?).

**Phase 2 — leaderboard in game.** A part with a **SurfaceGui** + TextLabels (search:
"roblox surfacegui leaderboard" — final detective exam). A script fetches
`/api/leaderboard` every 30 seconds (loop + `task.wait(30)`) and updates the board.
Top-10, live, in your world.

**Phase 3 — polish for the demo.** A proper spawn/title area, obby is beatable but not
trivial, coins along the way, victory message with their global rank
(`/api/rank/<player>` — you built that route two levels ago, knowing this day would come).

**Phase 4 — 🎓 Graduation demo.** Present to your family: play the obby, finish it, walk
to the leaderboard, see your name appear. Then explain the architecture drawing — every
box, in your own words, including what happens in the two seconds after you touch the
finish pad. If you can explain that, you're not a kid who did a course. You're a
developer.

**Phase 5 — write it up.** A README for the game project + add it to your website from
Level 8 (which is starting to look like a real portfolio, isn't it?).

## Side Quests (a.k.a. New Game+)

- **Rojo + git:** the pro workflow — your Luau scripts as files in your repo, synced into
  Studio ([rojo.space](https://rojo.space)). Your game code finally lives in version
  control like everything else.
- **Publish for real:** run the tunnel (ngrok/cloudflared), publish the game, and have a
  friend's score appear on your leaderboard from THEIR house.
- **Security thinking:** right now, anyone who finds your API could POST a fake score of
  999999. How would you stop that? (Shared-secret header? Validation? This question is
  the doorway to real backend engineering — no wrong answers, discuss with your mentor.)
- **Open Cloud:** Roblox's official APIs for managing your game from outside — your
  Python scripts can read your game's DataStores. Full circle: Level 7 skills, aimed at
  your own game.

## What's next?

You now have: a terminal, git, Python, APIs, web, Docker, two databases, and a shipped
game that uses all of it. Realistic next arcs, in whatever order sounds fun:

- **More game:** deeper Luau — RemoteEvents, client/server, real DataStores, monetization
- **More web:** JavaScript properly, then a frontend framework — make your leaderboard a
  live webpage anyone can visit
- **More backend:** deploy your compose stack to a real cloud server so it's up 24/7
- **More Python:** automate something in your actual life; that's where it gets addictive

GG. 🏆
