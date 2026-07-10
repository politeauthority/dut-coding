# Level 10 Teacher Guide: Shipping Containers 🐳

## Session plan (1 hour)

| Time | Activity |
|------|----------|
| 0:00–0:10 | Homework review. Discuss quest 3: WHY did the scores vanish? (Memory vs. disk — sets up both Docker volumes and databases.) |
| 0:10–0:20 | Install Docker Desktop (download ahead of time — it's big). Concept: image = the recipe/cartridge, container = a running copy of it. `docker run hello-world`. |
| 0:20–0:35 | The wow demo: `docker run -p 8080:80 nginx` → visit localhost:8080. He just ran a web server that ISN'T installed on his Mac. Run a second one on 8081. Show `docker ps`, `docker stop`. |
| 0:35–0:50 | **Containerize HIS server.** Write a `Dockerfile` for `leaderboard-server` together, `docker build`, `docker run -p 5000:5000`. His own creation, in a box. |
| 0:50–1:00 | Show a minimal `compose.yaml` for his app and explain: "one file that describes your whole team of containers." Homework walkthrough. |

## Watch for

Docker Desktop must actually be RUNNING (whale icon) — the #1 beginner
error is `Cannot connect to the Docker daemon`. Port mapping direction (`-p outside:inside`)
confuses everyone; draw it. Apple Silicon works fine with the official images used here.
