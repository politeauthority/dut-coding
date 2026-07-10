# Level 9: Serve It Up 🍽️

**Goal:** Until now your websites were files the browser opened. Now you'll build a
**server** — a Python program that sits there waiting, and *builds a response* every time
a browser (or another program) asks. This is how every real website and game backend
works, and it's the engine of your Boss Level.

We'll use **Flask**, a small, friendly Python web framework.

## The concepts

```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/")                      # when someone visits /
def home():
    return "<h1>Welcome to my server!</h1>"     # you can return HTML!

@app.route("/hello/<name>")          # URLs can have variables
def hello(name):
    return f"<p>Hello, {name}!</p>"

@app.route("/api/status")            # or return JSON — an API, like Level 7, but YOURS
def status():
    return jsonify({"status": "ok", "players_online": 42})

app.run(debug=True)                  # start listening on localhost:5000
```

Run it: `uv run app.py` → open `http://localhost:5000` in your browser.

> ⚠️ **Mac gotcha:** macOS has a feature called AirPlay Receiver that squats on port
> 5000. If Flask says "Address already in use" (or you get mystery 403 errors), turn it
> off: System Settings → search "AirPlay Receiver" → off. Or run Flask on another port.
> Congratulations on your first port conflict — a true rite of passage.

**localhost** = your own machine. **:5000** = the port (which "door" the server listens
at). Right now only your Mac can see it — it's a private internet of one.

## Core Quests

1. **`leaderboard-server` project** (this exact project grows into the Boss Level — name
   it well and keep it in git). Build these routes; store scores in a dictionary for now:
   - `GET /` — an HTML home page saying what this server is
   - `GET /api/scores` — returns all scores as JSON, sorted best-first
   - `POST /api/scores` — accepts JSON like `{"player": "Alex", "score": 120}` and adds
     it (look up `request.get_json()`; test it with `requests.post(...)` from a separate
     little `test_client.py` — you can't POST from the browser address bar!)
   - `GET /api/scores/<player>` — one player's best score, or a proper "not found"
     response (search: "flask return 404")
2. **`test_client.py`** — a script using `requests` that POSTs 5 scores and then GETs the
   leaderboard and prints it nicely with `rich`. Your own client talking to your own
   server. You are now both sides of the internet.
3. **Find the flaw.** Stop the server, start it again, GET the scores. Where did they
   go?! Write in your notes WHY they disappeared and what we might need to fix it.
   (That's not a bug in your code — it's THE reason databases exist. Level 11 awaits.)
4. **Notes** (`level-09.md`): draw (or write) the request/response loop. What's a route?
   What's localhost? Questions.

## Side Quests

- Make `GET /` show the actual top-10 as an HTML table, built from the dictionary with an
  f-string (a "server-rendered" page — fancy term, simple idea).
- Add `DELETE /api/scores/<player>` — search how to allow methods on a Flask route.
- Two servers at once: run a second copy on port 5001 (search: "flask change port").
  Why don't they collide?

## 🎮 Roblox Connection

Every big Roblox game runs servers like this. When a game shows a global leaderboard,
trade prices, or codes-to-redeem, a Roblox server is making an HTTP request to a backend
API that some developer built — often in Python, often looking *exactly* like your
`app.py`. In the Boss Level, your Roblox game calls THIS very server. Keep it safe.
