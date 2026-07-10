# Level 11 Teacher Guide: The Vault 🗄️

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Homework review: `docker compose up` his server together. |
| 0:10–0:20 | Concept: tables = spreadsheets with rules (columns have types, rows are records). SQL = the language for asking questions about them. Show a `scores` table sketch on paper: id, player, score, created_at. |
| 0:20–0:40 | **Live:** add `postgres` to his `compose.yaml` (image, `POSTGRES_PASSWORD`, volume). `docker compose up`, then `docker compose exec db psql -U postgres` — a SQL prompt! Together: `CREATE TABLE`, a few `INSERT`s, then play with `SELECT ... WHERE ... ORDER BY ... LIMIT`. Frame SELECT as "asking the vault questions." |
| 0:40–0:50 | The payoff plan: show how Python talks to Postgres (`uv add "psycopg[binary]"` — the `[binary]` extra avoids needing libpq installed — plus a 6-line connect+query example). He'll wire the Flask app to it for homework. |
| 0:50–1:00 | Homework walkthrough — especially the "scores survive a restart" victory condition. |

## Watch for

The semicolon in psql (statement won't run without it; he'll think it's
frozen). Connection strings have many pieces — give him a working template. The
`db` hostname (vs `localhost`) inside compose is the subtle one: containers reach each
other by service name. Draw it. And the sneakiest bug of the level: psycopg doesn't
autocommit — an INSERT without `conn.commit()` silently vanishes, and his POST route will
"work" while storing nothing. If he reports "scores disappear but no error," that's it.
