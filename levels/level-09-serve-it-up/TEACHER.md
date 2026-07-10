# Level 9 Teacher Guide: Serve It Up 🍽️

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Homework review — browse his live site together. |
| 0:10–0:20 | Concept: the request/response loop. Browser says "GET /projects" → server (a program!) decides what to send back → browser renders it. Static files vs. a program that can respond *differently every time* — show that his lookup tool from Level 7 was the ASKING side; today he builds the ANSWERING side. |
| 0:20–0:40 | **Live build:** `uv init leaderboard-server`, `uv add flask`, `app.py` with a route returning "Hello!". Run it, visit `localhost:5000` in the browser. Mind blown: browser talking to HIS program. Add a route with a variable (`/hello/<name>`), then a JSON route. Visit his JSON route with `requests` from another terminal — full circle. |
| 0:40–0:50 | Explain `localhost` ("your Mac pretending to be the internet") and ports ("apartment numbers"). Start the homework's leaderboard design on paper: what routes? what data? |
| 0:50–1:00 | Homework walkthrough. |

## Watch for

macOS AirPlay Receiver squats on port 5000 — Flask fails with "Address already in use" or
requests hit a mystery AirTunes 403. Turn it off on his Mac BEFORE the live-build segment
(System Settings → search "AirPlay Receiver"), or standardize on another port for the
rest of the course. Also: forgetting to restart the server after edits (or use `debug=True` and
explain it), port-already-in-use errors (find and kill the old one — good terminal
practice!), and the URL/route mismatch typos. `localhost` vs the internet is worth
re-explaining twice.
