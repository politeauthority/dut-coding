# Level 12 Teacher Guide: The Leaderboard 🏅

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Homework review: the down/up/data-survives demo, and check his INSERT uses parameters (quest 4). |
| 0:10–0:20 | Concept: key→value model vs. tables. Speed demo pitch: Redis keeps data in memory. Add `redis:7` to compose, `docker compose exec redis redis-cli`, play: `SET coins 100`, `GET coins`, `INCR coins`. |
| 0:20–0:35 | **Sorted sets — the leaderboard data type.** `ZADD leaderboard 120 alex`, add a few players, `ZREVRANGE leaderboard 0 9 WITHSCORES` = instant top-10. `ZINCRBY` for "player earned points." This maps SO cleanly to games that it teaches itself. |
| 0:35–0:50 | Python side: `uv add redis`, a few lines mirroring what he did in redis-cli. Sketch the homework architecture: POST writes to BOTH Postgres (permanent record) and Redis (fast ranks); GET top-10 reads Redis. Draw the boxes! Three containers, one team. |
| 0:50–1:00 | Homework walkthrough. Remind him: after this level, the backend for the Boss Level is DONE. |

## Watch for

"why two databases?!" — keep the vault/whiteboard framing and remind him
Redis (by default) can lose data on restart, which is exactly why the permanent record
lives in Postgres. Also `ZREVRANGE` vs `ZRANGE` (highest-first vs lowest-first) trips
everyone once.
