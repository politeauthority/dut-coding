# Level 13: Enter the Studio 🎮

**Goal:** Roblox Studio and **Luau** — for real this time. You've dabbled before, but now
you arrive with a programmer's toolkit: variables, functions, loops, dictionaries, and
detective skills. Watch how differently Studio feels when you can actually read the code.

Luau is Roblox's language (a supercharged Lua). Everything you learned in Python exists
here in slightly different clothes.

## Python → Luau phrasebook

| Python | Luau |
|--------|------|
| `coins = 100` | `local coins = 100` |
| `print(f"coins: {coins}")` | `print("coins: " .. coins)` |
| `if x > 5:` ... | `if x > 5 then` ... `end` |
| `for i in range(1, 11):` | `for i = 1, 10 do` ... `end` |
| `def heal(amount):` | `local function heal(amount)` ... `end` |
| `player = {"name": "Alex"}` | `local player = {name = "Alex"}` |
| `items = ["sword", "map"]` | `local items = {"sword", "map"}` — first item is `items[1]`! |
| `# comment` | `-- comment` |

The genuinely new idea is **events**: instead of a loop asking "did anything happen?",
you hand Roblox a function and say "run this WHEN it happens":

```lua
local part = script.Parent

part.Touched:Connect(function(hit)
    local character = hit.Parent
    local humanoid = character:FindFirstChild("Humanoid")
    if humanoid then
        humanoid.Health = 0        -- lava!
    end
end)
```

## Core Quests

Work in one place file — call it `boss-level` because it becomes your Boss Level game.

1. **Build a mini-obby** (5+ stages): lava parts that kill (script above — typed, not
   pasted!), at least one moving or disappearing platform (search the Creator Docs:
   `TweenService` for moving, or a loop with `task.wait()` + `Transparency`/`CanCollide`
   for disappearing), and a golden **finish pad**.
2. **Coins.** The leaderstats pattern from the session: give each joining player a Coins
   stat (`Players.PlayerAdded`), and make coin parts around the map that give +10 and
   vanish when touched (careful: only pay out once, not once per touch — a `local
   collected = false` flag; debugging this teaches a real lesson about events firing
   fast).
3. **The finish pad** awards +100 coins and prints a victory message. (Next level, it
   will ALSO post the player's coins to your API. Leave a comment in the script:
   `-- TODO: send to my leaderboard API`.)
4. **Translate your skills.** Pick one small Python program from Levels 4–5 (damage calc,
   times table, countdown...) and rewrite it as a Luau script that prints to Output. Put
   both versions side by side in your notes.
5. **Notes** (`level-13.md`): the phrasebook copied out BY HAND (it's a memorization
   trick), what an event is in your own words, plus what `FindFirstChild` does (detective
   mission: look it up in the Creator Docs). Questions.

## Side Quests

- Make a checkpoint system so dying returns you to the last checkpoint (search:
  "roblox checkpoint obby" — evaluating the tutorials you find is part of the quest).
- Look up **DataStoreService** and make coins persist between play sessions. Two setup
  traps: your game must be published to Roblox (File → Publish — it can stay private),
  and Studio playtests can't touch DataStores until you turn on **Game Settings →
  Security → Enable Studio Access to API Services**. Then compare in your notes: how is a
  DataStore like your Postgres setup? How is it more limited?
- Add sounds. Or particle effects on the coins. Make it juicy.

## 🎮 Roblox Connection

This level needs no connection section — you're IN it now. But notice what just happened:
concepts you learned in a terminal with Python (variables, functions, dictionaries,
events ≈ callbacks, saving data) all showed up here wearing costumes. That's the big
secret of programming: **learn the ideas once, and every new language is a phrasebook,
not a whole new world.**
