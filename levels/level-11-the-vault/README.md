# Level 11: The Vault 🗄️

**Goal:** Databases — where real applications keep data safe. You'll run **Postgres**
(the most-loved database in the world) in Docker, speak to it in **SQL**, and finally
solve the Level 9 mystery: your leaderboard will survive restarts.

A database is a program whose whole job is storing data: it never forgets, it can search
millions of records instantly, and it survives crashes, restarts, and power cuts. Your
dictionary-in-memory was a chest in a burning building. Postgres is a bank vault.

## The concepts

```sql
-- create a table (columns + types + rules)
CREATE TABLE scores (
    id SERIAL PRIMARY KEY,          -- auto-numbering ID
    player TEXT NOT NULL,
    score INTEGER NOT NULL,
    created_at TIMESTAMP DEFAULT now()
);

INSERT INTO scores (player, score) VALUES ('Alex', 120);

SELECT * FROM scores;                              -- everything
SELECT player, score FROM scores
    WHERE score > 100
    ORDER BY score DESC
    LIMIT 10;                                      -- a top-10 leaderboard IS this query
UPDATE scores SET score = 150 WHERE player = 'Alex';
DELETE FROM scores WHERE player = 'Alex';
```

The compose file gains a teammate:

```yaml
services:
  web:
    build: .
    ports: ["5000:5000"]
    environment:
      DATABASE_URL: postgres://postgres:secret@db:5432/postgres
  db:
    image: postgres:16
    environment:
      POSTGRES_PASSWORD: secret
    volumes:
      - dbdata:/var/lib/postgresql/data     # THIS is why data survives
volumes:
  dbdata:
```

Note: the web container reaches the database at hostname **`db`** — inside compose,
services find each other by name.

And Python talks to it with the `psycopg` package (`uv add "psycopg[binary]"`):

```python
import psycopg
conn = psycopg.connect("postgres://postgres:secret@db:5432/postgres")
conn.execute("INSERT INTO scores (player, score) VALUES (%s, %s)", ("Alex", 120))
conn.commit()   # ⚠️ INSERT/UPDATE/DELETE don't stick until you commit!
rows = conn.execute("SELECT player, score FROM scores ORDER BY score DESC").fetchall()
```

## Core Quests

1. **SQL drills in psql.** Create the `scores` table, insert 10 rows, then write and save
   (in `queries.sql`, committed) queries that answer: top 3 scores? every score by one
   player? the average score (search: SQL AVG)? how many rows total (search: COUNT)?
2. **The big wiring job.** Replace the dictionary in `leaderboard-server` with Postgres:
   `POST /api/scores` does an INSERT, `GET /api/scores` does the SELECT-ORDER BY-LIMIT.
   Use `psycopg` — and remember `conn.commit()` after the INSERT, or your scores will
   ghost you. Take it slow, git-commit at each working stage.
3. **The victory condition.** Run `test_client.py` to add scores → `docker compose down`
   → `docker compose up` → GET the scores. **They're still there.** Screenshot or paste
   the proof into your notes, and write one sentence connecting it to the Level 9 mystery.
4. **⚠️ Learn the #1 security rule.** Read about "SQL injection" (search: "SQL injection
   explained simply", or ask your mentor for the xkcd about little Bobby Tables). Rule:
   NEVER build SQL by gluing user input into the string — always pass parameters:
   `conn.execute("INSERT INTO scores (player, score) VALUES (%s, %s)", (player, score))`.
   Write the rule in your notes; use it in quest 2.
5. **Notes** (`level-11.md`): what's a table? What do SELECT / INSERT / WHERE do? Why did
   the data survive this time? Questions.

## Side Quests

- Add a second table `players` (id, name, favorite_game) and look up what a JOIN does.
- What happens if you `INSERT` a string into the score column? Try it. Why is the
  database refusing things a Python dict would happily accept — and why is that GOOD?
- Find out what an **index** is and why the leaderboard query gets slow with a million
  rows without one.

## 🎮 Roblox Connection

Roblox gives games a built-in mini-database called **DataStore** (you'll use it in Level
13) — but it's limited on purpose. When games need real power — trading histories,
economy analytics, cross-game accounts — studios run real databases like Postgres behind
an API. Games like Adopt Me process millions of trades; every one is a row in a table
with rules, exactly like your `scores`.
