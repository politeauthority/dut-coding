# Level 10: Shipping Containers 🐳

**Goal:** Learn Docker — how professionals package programs so they run *anywhere*. Then
docker compose — how to run several programs together as one team. This unlocks the
databases in Levels 11–12.

The problem Docker solves: "it works on my machine" — a program needs the right Python,
the right packages, the right settings. A **container** packs the program AND its whole
environment into one sealed box that runs the same on any computer. Like a game cartridge:
snap it in, it just plays.

## The concepts

```bash
docker run hello-world               # run a tiny test container
docker run -p 8080:80 nginx          # run a web server; your port 8080 → its port 80
docker ps                            # what's running?
docker stop <name>                   # stop a container
docker build -t leaderboard .        # build an image from the Dockerfile HERE
docker run -p 5000:5000 leaderboard  # run YOUR image
```

A `Dockerfile` is the recipe for your image:

```dockerfile
FROM python:3.12-slim                    # start from an image that has Python
WORKDIR /app                             # work in /app inside the box
COPY . .                                 # copy your project files in
RUN pip install flask                    # install what it needs
CMD ["python", "app.py"]                 # what to run when the container starts
```

And `compose.yaml` describes a whole team of containers:

```yaml
services:
  web:
    build: .
    ports:
      - "5000:5000"
```

`docker compose up` starts the team. `docker compose down` stops it. (Next level, the
team gains a database member — that's where compose really shines.)

## Core Quests

1. **Cartridge collection.** Run 3 different public images and note what each does:
   `nginx` (with a port), `python:3.12` (try `docker run -it python:3.12` — an
   interactive Python inside the box! What's `-it`? Look it up), and one of your choice
   from hub.docker.com.
2. **Containerize `leaderboard-server`.** Write the `Dockerfile` (commit it!), build,
   run with `-p`, and prove it works by running `test_client.py` from your Mac against
   the containerized server. One catch to solve: inside the container, Flask must listen
   on `host="0.0.0.0"` — search "flask docker 0.0.0.0" and write down in your notes what
   that means.
3. **Compose it.** Write `compose.yaml` for your server. `docker compose up`, test it,
   `docker compose down`. Commit it.
4. **Cleanup patrol.** Learn `docker ps -a` and `docker images`. Remove stopped
   containers and unused images (`docker rm`, `docker rmi`, or discover `docker system
   prune` — read what it does BEFORE running it, detective rules apply).
5. **Notes** (`level-10.md`): image vs. container in your own words. What does
   `-p 8080:80` mean? Questions.

## Side Quests

- Change your Dockerfile to install from `pyproject.toml` properly (search: "uv in
  docker" — uv publishes an official guide).
- Find out what a **volume** is (`-v`) and why containers forget everything when removed.
  Connect this to your vanishing-scores mystery from Level 9...
- How big is your image (`docker images`)? Can you make it smaller?

## 🎮 Roblox Connection

The backends behind big Roblox games run in containers — studios package their APIs
exactly like you just packaged yours, then run hundreds of copies in the cloud when a
game goes viral. Roblox's own infrastructure runs on container tech too. When your game
has 10,000 concurrent players someday, "it runs the same everywhere" stops being a nice
idea and becomes survival.
