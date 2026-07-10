# Level 13 Teacher Guide: Enter the Studio 🎮

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Homework review: run the three-container backend + test client. Tell him plainly: your backend is done and it's Boss-ready. |
| 0:10–0:20 | Studio tour with new eyes: Explorer = a tree of Instances (connect to HTML nesting!), Properties panel, and where Scripts live (ServerScriptService for server code). Baseplate + a Part + first script: `print("hello")` → show the Output window (his new terminal). |
| 0:20–0:40 | **Translate Python to Luau live:** variables (`local`), `if/then/end`, `for i = 1, 10 do`, tables (= dictionaries!), functions. Then the big new idea: **events** — `part.Touched:Connect(function(hit) ... end)`. Build a lava brick that kills you. Classic for a reason. |
| 0:40–0:50 | **leaderstats.** The in-game leaderboard pattern: create a `leaderstats` folder on each player, add a Coins IntValue, give coins on touch. This is THE most-searched Roblox pattern and it sets up the Boss Level perfectly. |
| 0:50–1:00 | Homework walkthrough. Show him the Luau section of the Creator Docs — he can now genuinely read it. |

## Watch for

Server scripts vs. local scripts (keep everything server-side this level;
just plant the concept "server = the referee, client = each player's screen"). Luau
tables start at index 1 (!) — mention it before it burns an hour. The Output window is
hidden by default; open it first thing.
