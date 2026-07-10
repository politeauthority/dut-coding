# Level 14 Teacher Guide: 🏆 BOSS LEVEL — Connect Everything

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Review the obby. Play it. Die in the lava at least once, with dignity. |
| 0:10–0:20 | The architecture drawing (above) — have HIM explain each box and which level taught it. This retrieval moment is the whole course clicking together. |
| 0:20–0:30 | **The plumbing problem:** Roblox runs your game in the cloud; `localhost` is only YOUR Mac — Roblox's servers can't see it. Two options: (a) **Studio playtest mode** — playtests run locally, so localhost works! Start here. (b) A tunnel (e.g. ngrok or cloudflared) to give your laptop a temporary public URL for testing from real Roblox. Do (a) live today. |
| 0:30–0:50 | **Wire it live:** Game Settings → Security → ✅ Allow HTTP Requests. Then in the finish-pad script: `HttpService:PostAsync(...)` with the player's name and coins, wrapped in `pcall` (Luau's try/except!). Run the compose stack, playtest, touch the pad... check `test_client.py`'s GET — **his score is in the database.** Savor it. |
| 0:50–1:00 | Homework = the full build. Also discuss the graduation demo: he presents the whole system to family, explains every box. |

## Watch for

HTTP must be enabled per-place (the checkbox); Game Settings is only accessible once the
place is published to Roblox (File → Publish — it can stay private), so publish before
hunting for the checkbox. `pcall` is mandatory — network calls fail and un-wrapped errors
will confuse him; frame it as "try/except, Luau edition". Keep the API on plain HTTP
locally; if you use a tunnel, note the URL changes each restart (free tier).

Two HttpService facts to have in your pocket: requests are rate-limited to ~500/minute
per game server (the 30-second leaderboard poll is nowhere close, but a bugged
loop-without-wait will hit it and stall requests), and HttpService refuses to call
`roblox.com` domains from in-game — so his Level 7 trick of hitting Roblox's own APIs
won't work from inside the game; that's what Open Cloud is for. If Flask moved off port
5000 back in Level 9 (AirPlay), remember to match the port in the Luau `API` constant.
