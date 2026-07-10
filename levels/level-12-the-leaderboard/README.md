# Level 12: The Leaderboard 🏅

**Goal:** Meet **Redis** — a database so fast it answers in microseconds — and use its
famous *sorted sets* to build a proper game leaderboard. By the end of this level, your
backend is feature-complete for the Boss Level: Flask + Postgres + Redis, all in compose.

Postgres is the vault: safe, structured, thorough. Redis is the whiteboard by the door:
instant to read, instant to update, perfect for things you check constantly — like
leaderboards, counters, and "who's online." Real systems use both, each for what it's
best at. Now yours will too.

## The concepts

```bash
# in redis-cli — keys and values
SET player:alex:coins 100
GET player:alex:coins
INCR player:alex:coins          # add 1, atomically

# sorted sets — a collection where every member has a score, always kept in order
ZADD leaderboard 120 alex
ZADD leaderboard 300 sam
ZADD leaderboard 250 jo
ZREVRANGE leaderboard 0 9 WITHSCORES   # top 10, highest first — THE leaderboard command
ZINCRBY leaderboard 50 alex            # alex earned 50 points
ZREVRANK leaderboard alex              # what place is alex in? (0 = first)
```

```python
# python — same thing
import redis
r = redis.Redis(host="redis", port=6379, decode_responses=True)
r.zincrby("leaderboard", 50, "alex")
top = r.zrevrange("leaderboard", 0, 9, withscores=True)
```

## Core Quests

1. **redis-cli drills.** In the Redis container: build a leaderboard of 8 fake players,
   get the top 3, get one player's rank, give a player points, check how the ranks
   changed. Save the commands you used in `redis-drills.md`, committed.
2. **The final backend build.** Upgrade `leaderboard-server`:
   - `compose.yaml` now runs three services: `web`, `db` (Postgres), `redis`
   - `POST /api/scores` → INSERT into Postgres (the permanent record) AND
     `ZINCRBY`/`ZADD` in Redis (the live ranks)
   - `GET /api/leaderboard` → top 10 from Redis, as JSON
   - `GET /api/rank/<player>` → their rank + score from Redis (handle unknown players
     without crashing!)
3. **Prove the team works.** Extend `test_client.py`: add 10 players with random scores,
   print the top-10, print two players' ranks, then add points to a low-ranked player and
   show the ranks changed. Run it start-to-finish and paste the output in your notes.
4. **The tradeoff experiment.** `docker compose down` then `up`: which data survived
   (Postgres) and which didn't (Redis)? Write a "warm-up" note: how COULD you rebuild the
   Redis leaderboard from the Postgres table? (Just describe it — building it is a side
   quest.)
5. **Notes** (`level-12.md`): when Redis vs. when Postgres, in your own words. What's a
   sorted set? Questions.

## Side Quests

- Build the warm-up for real: on server startup, read all scores from Postgres and
  rebuild the Redis sorted set. Now your leaderboard is fast AND unkillable.
- Look up `EXPIRE` — keys that delete themselves. What game feature could use that?
  (Hint: "daily rewards", "double XP for the next hour"...)
- Add `GET /api/around/<player>` — the 2 players above and below them (nearby-rank
  leaderboards are what real games show!). `ZREVRANK` + `ZREVRANGE` combo.

## 🎮 Roblox Connection

When a Roblox game shows a *global* leaderboard — top players across every server of the
game — that's essentially Redis sorted sets behind an API (Roblox's own
`OrderedDataStore` is this same idea, with tighter limits). Yours is the real,
unrestricted version of it. Next level you step into Studio; the level after that, your
game and this backend meet. 🤝
