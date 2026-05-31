# ACOS — Adaptive Cognitive Operating System
## MNC Production-Grade Personal System: Zero to Deployed
### Complete Day-by-Day Roadmap from No Knowledge to Full Stack

---

> **What you are building:** A fully self-hosted, production-grade, MNC-quality Adaptive Cognitive Operating System — running on your PC and smartphone — that combines personal knowledge management, AI-driven adaptive feed, research automation, creative triggers, reminders, progress tracking, and an evolving creative fingerprint. Every day builds on the last. Every stage produces something real, documented, and recruiter-visible.

---

## Table of Contents

1. [System Vision and Final Architecture](#1-system-vision-and-final-architecture)
2. [Hardware and Software Requirements](#2-hardware-and-software-requirements)
3. [Phase Map Overview](#3-phase-map-overview)
4. [Phase 0 — Foundation (Days 1–14)](#4-phase-0--foundation-days-114)
5. [Phase 1 — Programming Core (Days 15–45)](#5-phase-1--programming-core-days-1545)
6. [Phase 2 — Databases and Storage (Days 46–70)](#6-phase-2--databases-and-storage-days-4670)
7. [Phase 3 — Networks and APIs (Days 71–100)](#7-phase-3--networks-and-apis-days-71100)
8. [Phase 4 — Backend Systems (Days 101–140)](#8-phase-4--backend-systems-days-101140)
9. [Phase 5 — AI and Intelligence Layer (Days 141–175)](#9-phase-5--ai-and-intelligence-layer-days-141175)
10. [Phase 6 — Frontend and Mobile (Days 176–210)](#10-phase-6--frontend-and-mobile-days-176210)
11. [Phase 7 — DevOps and Infrastructure (Days 211–245)](#11-phase-7--devops-and-infrastructure-days-211245)
12. [Phase 8 — System Integration (Days 246–280)](#12-phase-8--system-integration-days-246280)
13. [Phase 9 — Production Hardening (Days 281–300)](#13-phase-9--production-hardening-days-281300)
14. [Documentation Master Strategy](#14-documentation-master-strategy)
15. [Portfolio and Proof-of-Work System](#15-portfolio-and-proof-of-work-system)
16. [Active Recall and Conceptual Validation System](#16-active-recall-and-conceptual-validation-system)

---

## 1. System Vision and Final Architecture

### What the Final System Does

When complete, your ACOS will:

- Accept any natural language statement and detect intent automatically
- Fire all relevant tools (web scraper, YouTube summariser, Google Maps API, GitHub sync, reminder engine, historical DB, embedding engine, knowledge graph) without step-by-step instruction
- Maintain a personal knowledge store with semantic search
- Surface an adaptive, Instagram-style feed that rotates topics based on your mood, engagement, and creative fingerprint
- Generate plot triggers by finding historical parallels
- Track progress on skills, projects, and goals
- Run entirely on your personal PC and smartphone — no cloud dependency required
- Be extensible: any new tool or API plugs into Layer 2 without rewiring anything

### Final System Architecture

```
┌─────────────────────────────────────────────────────────────────┐
│                        ACOS — Full Stack                        │
├─────────────────────────────────────────────────────────────────┤
│  FRONTEND (React Native / PWA)                                  │
│  ├── Adaptive Feed UI (card-based, swipe-to-next)               │
│  ├── Note input (free-form, voice, URL, image)                  │
│  ├── Knowledge graph visualiser                                 │
│  ├── Progress dashboard                                         │
│  └── Map view (pinned places)                                   │
├─────────────────────────────────────────────────────────────────┤
│  API GATEWAY (FastAPI / NGINX)                                  │
│  ├── Auth (JWT)                                                 │
│  ├── Rate limiting                                              │
│  └── Request routing                                            │
├─────────────────────────────────────────────────────────────────┤
│  INTELLIGENCE LAYER (Python services)                           │
│  ├── Intent classifier (local LLM / rule engine)                │
│  ├── Tool orchestrator (chains tools on detected intent)        │
│  ├── Embedding engine (sentence-transformers)                   │
│  ├── Historical analogy engine                                  │
│  ├── Creative trigger generator                                 │
│  ├── Explore-exploit dial (spaced repetition)                   │
│  └── Scrappy search aggregator                                  │
├─────────────────────────────────────────────────────────────────┤
│  TOOL LAYER (pluggable modules)                                 │
│  ├── Web scraper (Playwright + BeautifulSoup)                   │
│  ├── YouTube transcript extractor                               │
│  ├── Google Maps / Places API client                            │
│  ├── GitHub sync agent                                          │
│  ├── Reminder engine (APScheduler)                              │
│  └── Progress tracker                                           │
├─────────────────────────────────────────────────────────────────┤
│  DATA LAYER                                                     │
│  ├── PostgreSQL + pgvector (notes, embeddings, projects)        │
│  ├── Redis (session cache, feed state, reminder queue)          │
│  ├── SQLite (offline mobile fallback)                           │
│  └── File store (media, screenshots, exports)                   │
├─────────────────────────────────────────────────────────────────┤
│  INFRASTRUCTURE (self-hosted)                                   │
│  ├── Docker Compose (local PC orchestration)                    │
│  ├── NGINX (reverse proxy, SSL via mkcert)                      │
│  ├── Prometheus + Grafana (monitoring)                          │
│  ├── Loki (log aggregation)                                     │
│  └── Watchtower (auto container updates)                        │
└─────────────────────────────────────────────────────────────────┘
```

### Technology Choices — Why Each One

| Layer | Technology | Why This, Not Alternatives |
|---|---|---|
| Backend language | Python | Fastest path from zero to AI/ML integration; largest ecosystem for NLP tools |
| API framework | FastAPI | Auto-generates OpenAPI docs; async; type-safe; production-used at Uber, Netflix |
| Primary DB | PostgreSQL | Relational + vector extension (pgvector); one DB for structured + semantic search |
| Vector search | pgvector | Keeps vectors in same DB as notes; no separate Pinecone/Weaviate needed |
| Cache/queue | Redis | Industry standard; handles feed state, reminders, and pub/sub in one service |
| Frontend | React + React Native | One codebase concept; web PWA + mobile from same components |
| Containerisation | Docker + Compose | Reproducible environment; industry standard for every MNC |
| Reverse proxy | NGINX | Production battle-tested; handles SSL, load balancing, static files |
| Monitoring | Prometheus + Grafana | Free, MNC-grade observability; used at every serious engineering company |
| Local LLM | Ollama (llama3) | Runs on your PC; private; no API cost; upgradeable |
| Embeddings | sentence-transformers | Local; free; production-quality semantic search |
| Scraping | Playwright | Handles JS-rendered pages; more powerful than requests+BS4 alone |
| CI/CD | GitHub Actions | Free for public repos; industry standard pipeline |

---

## 2. Hardware and Software Requirements

### Minimum PC Requirements

| Component | Minimum | Recommended | Why |
|---|---|---|---|
| CPU | 4-core (Intel i5 / Ryzen 5) | 8-core (i7 / Ryzen 7) | Docker + local LLM need cores |
| RAM | 8 GB | 16 GB | PostgreSQL + Redis + FastAPI + Ollama comfortably fit |
| Storage | 50 GB free SSD | 100 GB free SSD | Docker images + DB + model weights |
| GPU | Not required | NVIDIA 4GB+ VRAM | Speeds up local LLM inference |
| OS | Ubuntu 22.04 LTS (WSL2 on Windows works) | Ubuntu 22.04 LTS native | Best Docker + Python compatibility |
| Internet | Broadband | Broadband | Initial downloads only; runs offline after |

### Software to Install (Day 1)

```bash
# All free and open-source

# Core tools
sudo apt update && sudo apt upgrade -y
sudo apt install -y git curl wget build-essential python3 python3-pip python3-venv

# Docker
curl -fsSL https://get.docker.com | sh
sudo usermod -aG docker $USER

# Docker Compose
sudo apt install -y docker-compose-plugin

# Node.js (via nvm — version manager)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.7/install.sh | bash
nvm install 20

# VS Code
wget -qO- https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > packages.microsoft.gpg
sudo install -D -o root -g root -m 644 packages.microsoft.gpg /etc/apt/keyrings/packages.microsoft.gpg
echo "deb [arch=amd64 signed-by=/etc/apt/keyrings/packages.microsoft.gpg] https://packages.microsoft.com/repos/code stable main" | sudo tee /etc/apt/sources.list.d/vscode.list
sudo apt update && sudo apt install -y code

# Ollama (local LLM runtime)
curl -fsSL https://ollama.com/install.sh | sh
ollama pull llama3

# PostgreSQL client tools
sudo apt install -y postgresql-client

# Postman alternative — Bruno (API testing)
# Download from https://www.usebruno.com/

# Git config
git config --global user.name "Your Name"
git config --global user.email "your@email.com"
git config --global init.defaultBranch main
```

### Smartphone Requirements

| Component | Requirement | Why |
|---|---|---|
| OS | Android 10+ or iOS 14+ | React Native compatibility |
| Storage | 500 MB free | App + local SQLite cache |
| Network | WiFi access to PC | App talks to your PC's ACOS backend |
| Browser | Chrome / Safari | PWA fallback works without app install |

### Free Accounts to Create (Day 1)

- **GitHub** — version control and proof-of-work
- **Cloudflare** (free tier) — optional tunnel for remote access to your PC
- **Google Cloud** (free tier) — Maps/Places API (free quota sufficient for personal use)
- **YouTube Data API** — free quota for transcript extraction

---

## 3. Phase Map Overview

```
Phase 0  │ Days  1–14  │ Foundations — how computers, networks, OSes work
Phase 1  │ Days 15–45  │ Python programming — zero to backend-ready
Phase 2  │ Days 46–70  │ Databases — SQL, PostgreSQL, Redis, vectors
Phase 3  │ Days 71–100 │ Networks and APIs — HTTP, REST, FastAPI
Phase 4  │ Days 101–140│ Backend systems — auth, queues, scraping, scheduling
Phase 5  │ Days 141–175│ AI/ML layer — embeddings, classifiers, local LLM
Phase 6  │ Days 176–210│ Frontend + mobile — React, React Native, PWA
Phase 7  │ Days 211–245│ DevOps — Docker, CI/CD, monitoring, NGINX
Phase 8  │ Days 246–280│ Full integration — wire all layers into one system
Phase 9  │ Days 281–300│ Production hardening — security, perf, launch
```

**Daily time commitment:** 3–4 hours on weekdays, 5–6 hours on weekends.

---

## 4. Phase 0 — Foundation (Days 1–14)

### Why This Phase Exists

You cannot make intelligent decisions about technology if you do not understand what a computer actually does. Engineers who skip this phase make architecture mistakes for years. Every senior engineer can explain what happens when you type a URL and press Enter — from electrons to pixels.

---

### Day 1 — How a Computer Works

**What to learn:**
- Binary and how computers represent data (bits, bytes, integers, strings)
- CPU: fetch-decode-execute cycle
- Memory hierarchy: registers → L1/L2/L3 cache → RAM → SSD
- How an operating system sits between hardware and software
- Processes vs threads (conceptual only today)

**Why this matters for ACOS:**
Your system will have a FastAPI backend (a process), a PostgreSQL database (another process), Redis (another process), and an Ollama LLM (another process) — all running simultaneously. Understanding how the OS manages processes tells you why RAM matters and how Docker isolates them.

**What to build:**
Write a text file called `computer_model.md` in which you explain — in your own words — the journey of data from keyboard press to screen display.

**Conceptual test (answer before moving on):**
1. Why is RAM faster than SSD but slower than CPU cache?
2. If you have 8 GB RAM and run 3 processes each needing 3 GB, what happens?
3. What is the role of the OS scheduler?

**Where to document:** `~/acos-journal/day-01/computer-model.md` (local file today; push to GitHub on Day 3 after Git is set up)

---

### Day 2 — Operating System Deep Dive

**What to learn:**
- File system: what a directory tree actually is, inodes
- Processes and process management (`ps`, `top`, `htop`)
- File permissions (chmod, chown — why this matters for Docker)
- Environment variables and why software uses them
- The shell: bash basics, piping, redirection

**Practical tasks:**
```bash
# Run all of these and understand each output
ps aux
top
df -h
free -h
ls -la /etc
cat /proc/cpuinfo | grep "model name"
echo $PATH
which python3
```

**What to build:**
A bash script `system-health.sh` that prints: CPU model, total RAM, disk usage, running processes count, and current date. This becomes the monitoring seed for your ACOS health dashboard later.

**Conceptual test:**
1. Why do Docker containers need file permission awareness?
2. What is a process ID (PID) and why does it matter?
3. Why do applications use environment variables instead of hardcoding config?

---

### Day 3 — Git and Version Control

**What to learn:**
- Why version control exists (the disaster of `final_v2_REAL_final.py`)
- Git object model: blobs, trees, commits
- Working tree → staging → repository flow
- Branching: why branches exist, merge vs rebase
- Remote repositories: push/pull/fetch
- `.gitignore` — what never to commit (secrets, virtual envs, node_modules)

**Practical tasks:**
```bash
git init acos-project
cd acos-project
mkdir -p docs/journal/phase-0
touch README.md
git add .
git commit -m "chore: initialise ACOS project"

# Create GitHub repo and push
git remote add origin https://github.com/YOUR_USERNAME/acos-project
git push -u origin main
```

**What to build:**
Your GitHub repository with this initial structure:
```
acos-project/
├── README.md              ← Project overview (write this properly)
├── docs/
│   └── journal/
│       └── phase-0/
│           ├── day-01-computer-model.md
│           └── day-02-os-notes.md
├── .gitignore
└── scripts/
    └── system-health.sh
```

**README.md must contain:**
- What ACOS is (2–3 sentences)
- What you will build (architecture diagram in ASCII or Mermaid)
- Current phase
- How to run `system-health.sh`

**Why this is recruiter-visible:** Every commit you make from now is dated evidence of consistent work. A GitHub contribution graph with 300 days of green squares is more convincing than any resume bullet point.

**Conceptual test:**
1. What is the difference between `git merge` and `git rebase`?
2. Why should you never commit a `.env` file?
3. What does `git log --oneline --graph` show you?

---

### Day 4 — Networking Fundamentals Part 1

**What to learn:**
- OSI model — 7 layers, what each handles
- TCP/IP model — how it maps to OSI
- IP addresses: IPv4, subnets, CIDR notation (192.168.1.0/24)
- MAC addresses vs IP addresses — why both exist
- DNS: how a domain name becomes an IP address

**Why this matters for ACOS:**
Your smartphone app will talk to your PC's ACOS backend over your home WiFi. Understanding IP addresses, ports, and DNS is why you can type `http://192.168.1.100:8000` and reach your API. When you use Cloudflare Tunnel later, DNS is how the internet finds your PC.

**Practical tasks:**
```bash
# Explore your network
ip addr show           # Your PC's IP addresses
ip route show          # Routing table
cat /etc/resolv.conf   # Your DNS servers
nslookup google.com    # DNS resolution
ping 8.8.8.8           # ICMP reachability
traceroute google.com  # Path packets take
ss -tulnp              # Open ports on your machine
```

**What to build:**
A network diagram (draw it by hand, photograph it, or use draw.io free) showing: your phone → router → PC → ACOS backend. Label with IP addresses from your actual network. Save as `docs/diagrams/home-network.png`.

**Conceptual test:**
1. Why does your router have both a private IP (192.168.x.x) and a public IP?
2. What happens at each OSI layer when you visit `http://192.168.1.100:8000/api/notes`?
3. What is the difference between TCP and UDP, and which does your ACOS API need?

---

### Day 5 — Networking Fundamentals Part 2

**What to learn:**
- HTTP protocol: request/response structure, methods (GET, POST, PUT, DELETE, PATCH)
- HTTP status codes (200, 201, 400, 401, 403, 404, 500 — know these by heart)
- Headers: Content-Type, Authorization, Accept, Cache-Control
- HTTPS: what TLS does, why HTTP alone is unacceptable
- Ports: why 80 (HTTP), 443 (HTTPS), 5432 (PostgreSQL), 6379 (Redis), 8000 (FastAPI)

**Practical tasks:**
```bash
# Install curl and httpie
sudo apt install -y curl httpie

# Make real HTTP requests and read responses
curl -v https://httpbin.org/get
curl -X POST https://httpbin.org/post -H "Content-Type: application/json" -d '{"test": "hello"}'
http GET https://httpbin.org/headers
```

**What to document:**
Write `docs/journal/phase-0/http-reference.md` — your personal HTTP cheat sheet. Include: every method, every status code you learned, example request/response for each. You will reference this forever.

**Conceptual test:**
1. What is the difference between PUT and PATCH?
2. Why does a 401 mean something different from a 403?
3. What does `Content-Type: application/json` tell the server?

---

### Days 6–7 — Linux Command Line Mastery

**What to learn:**
- File manipulation: `cp`, `mv`, `rm`, `mkdir`, `find`, `grep`, `sed`, `awk`
- Process management: `kill`, `pkill`, `nohup`, `screen`, `tmux`
- Text processing: `cat`, `less`, `head`, `tail`, `sort`, `uniq`, `wc`
- Permissions deep dive: `chmod 755`, `chown`, setuid
- Cron jobs: scheduled task syntax
- SSH: key generation, connecting to remote systems

**Practical tasks:**
```bash
# Master these patterns
find / -name "*.py" 2>/dev/null | head -20
grep -r "TODO" ~/acos-project/
ps aux | grep python | awk '{print $2, $11}'
tail -f /var/log/syslog
# Set up a cron job that runs system-health.sh every hour
crontab -e
# Add: 0 * * * * /bin/bash ~/acos-project/scripts/system-health.sh >> ~/acos-logs/health.log 2>&1
```

**What to build:**
Upgrade `system-health.sh` to:
- Log to a file with timestamps
- Alert (echo) if RAM usage exceeds 80%
- Export output as JSON (for future API consumption)

**Why this matters for ACOS:**
Your ACOS backend will run as a Linux process. Debugging production issues means reading logs, finding processes, and understanding permissions. This is foundational.

---

### Days 8–10 — Docker and Containerisation Concepts

**What to learn:**
- Why containers exist: "works on my machine" problem solved
- Container vs VM: namespace + cgroup isolation vs full OS virtualisation
- Docker architecture: client, daemon, images, containers, volumes, networks
- Dockerfile: `FROM`, `RUN`, `COPY`, `ENV`, `EXPOSE`, `CMD`
- Docker Compose: multi-container orchestration
- Volume mounts: persistent data vs ephemeral containers

**Why this matters for ACOS:**
Your entire ACOS stack — PostgreSQL, Redis, FastAPI, NGINX, Prometheus, Grafana, Ollama — will run as Docker containers. One `docker-compose up` starts everything. This is how MNCs deploy.

**Practical tasks:**
```bash
# Pull and run your first containers
docker run hello-world
docker run -it ubuntu:22.04 bash
docker run -d -p 5050:80 nginx  # Visit http://localhost:5050

# Build your first image
mkdir docker-practice && cd docker-practice
cat > Dockerfile << 'EOF'
FROM python:3.11-slim
WORKDIR /app
COPY . .
RUN pip install flask
EXPOSE 5000
CMD ["python", "app.py"]
EOF

cat > app.py << 'EOF'
from flask import Flask, jsonify
app = Flask(__name__)

@app.route("/health")
def health():
    return jsonify({"status": "ok", "service": "acos-practice"})

if __name__ == "__main__":
    app.run(host="0.0.0.0", port=5000)
EOF

docker build -t acos-practice .
docker run -d -p 5000:5000 acos-practice
curl http://localhost:5000/health
```

**What to build:**
Your first `docker-compose.yml` for ACOS foundations:
```yaml
version: "3.9"
services:
  postgres:
    image: pgvector/pgvector:pg16
    environment:
      POSTGRES_DB: acos
      POSTGRES_USER: acos_user
      POSTGRES_PASSWORD: acos_pass
    volumes:
      - postgres_data:/var/lib/postgresql/data
    ports:
      - "5432:5432"

  redis:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    volumes:
      - redis_data:/data

volumes:
  postgres_data:
  redis_data:
```

Run it:
```bash
docker compose up -d
docker compose ps
docker compose logs postgres
```

**What to document:**
`docs/journal/phase-0/docker-architecture.md` — diagram of how Docker containers communicate on a virtual network, what volumes are, and why you chose each base image.

**Conceptual test:**
1. Why does PostgreSQL data survive `docker compose down` but not if you add `--volumes`?
2. What is the difference between `EXPOSE` in a Dockerfile and `-p` in `docker run`?
3. Why should you not run production databases as root inside containers?

---

### Days 11–14 — System Design Thinking Introduction

**What to learn:**
- What system design is: decomposing a problem into components with clear boundaries
- The CAP theorem: Consistency, Availability, Partition tolerance — pick two
- Horizontal vs vertical scaling
- Monolith vs microservices — tradeoffs (start monolith, extract services when painful)
- Caching strategies: cache-aside, write-through, TTL
- Message queues: why async processing exists
- Load balancers: what they do and why

**Why this matters:**
When a recruiter or engineering manager interviews you, they will ask "how would you design X?" You need a framework for thinking before you have production experience.

**What to build:**
Draw — on paper first, then digitise — the architecture of each of these systems. Do not look up answers. Think it through:
1. A URL shortener (like bit.ly) — what does it need?
2. A reminder system that notifies you at a specific time — what components?
3. A note-taking app that can search by meaning, not just keyword — what is different?

After drawing, write your reasoning in `docs/journal/phase-0/system-design-thinking.md`.

**Conceptual test:**
1. Your ACOS note store gets 10,000 notes. Keyword search is instant. Semantic (meaning-based) search takes 3 seconds. Why? What would you do?
2. If PostgreSQL goes down, should your app crash or should some features still work? How do you design for that?
3. What is the difference between latency and throughput?

**Phase 0 Completion Check:**
Before moving to Phase 1, you must be able to:
- [ ] Explain the OSI model without notes
- [ ] Run `docker compose up -d` and verify PostgreSQL + Redis are running
- [ ] Make an HTTP request with curl and read the response headers
- [ ] Push a commit to GitHub with a meaningful commit message
- [ ] Explain why you need containers for ACOS

---

## 5. Phase 1 — Programming Core (Days 15–45)

### Why Python First

Python is the language of: AI/ML, data processing, backend APIs, scripting, automation. Every intelligence layer in your ACOS — intent classifier, embedding engine, historical analogy engine — is Python. The FastAPI backend is Python. The scraping tools are Python. Learning Python first gives you the most leverage.

---

### Days 15–20 — Python Fundamentals

**What to learn (in order):**

**Day 15 — Data types and control flow**
- Variables, strings, integers, floats, booleans
- `if/elif/else`, `for`, `while`
- Lists, tuples, dictionaries, sets — when to use which
- String formatting with f-strings

**Day 16 — Functions and scope**
- Defining functions, parameters, return values
- `*args` and `**kwargs`
- Local vs global scope
- Lambda functions — what they are and when NOT to use them

**Day 17 — File I/O and error handling**
- Reading and writing files (`open`, `with`, `json`, `csv`)
- `try/except/finally`
- Custom exceptions
- Why error handling is not optional in production code

**Day 18 — Modules and packages**
- `import` system, `__init__.py`
- Virtual environments: why they exist, how to use them
- `pip` and `requirements.txt`
- Reading library documentation

**Day 19 — Object-oriented programming**
- Classes, instances, `__init__`
- Inheritance and composition — when each is right
- `@property`, `@classmethod`, `@staticmethod`
- Why OOP helps organise your ACOS codebase

**Day 20 — Pythonic patterns**
- List comprehensions and generator expressions
- `enumerate`, `zip`, `map`, `filter`
- Context managers (`with` statement internals)
- `dataclasses` — the clean way to define data structures

**Daily practice pattern:**
Every day, write 10 small programs (5–15 lines each) that exercise the concepts. Do not read then code — code first, fail, then look up what you need. Struggle is how you learn.

**What to build (Days 15–20 mini-project):**
A command-line note-taking tool:
```python
# notes_cli.py
# Features:
# - Add a note: python notes_cli.py add "My idea about Java concurrency"
# - List notes: python notes_cli.py list
# - Search notes: python notes_cli.py search "java"
# - Delete note: python notes_cli.py delete 3
# - Export to JSON: python notes_cli.py export notes.json
# Storage: JSON file (will be replaced by PostgreSQL in Phase 2)
```

This is the seed of your ACOS note system. You will refactor it in every subsequent phase.

**Where to document:**
`src/phase-1/notes-cli/` in your GitHub repo with:
- `README.md` explaining what it does, how to run it
- `notes_cli.py` with inline comments explaining every non-obvious line
- `DESIGN.md` explaining your data structure choices

---

### Days 21–28 — Python for Data and Automation

**What to learn:**

**Day 21–22 — Advanced data structures**
- `collections`: `Counter`, `defaultdict`, `deque`, `OrderedDict`
- When to use a list vs deque for your reminder queue
- Hash maps and why dictionary lookup is O(1)

**Day 23–24 — Regular expressions**
- `re` module: `match`, `search`, `findall`, `sub`
- Practical: extract place names, URLs, dates from free-form text
- This powers your intent classifier's entity extraction

**Day 25 — Working with APIs (requests library)**
```python
import requests

# Google Places API call
response = requests.get(
    "https://maps.googleapis.com/maps/api/place/findplacefromtext/json",
    params={
        "input": "filter coffee cafe near Marina Beach Chennai",
        "inputtype": "textquery",
        "fields": "name,geometry,place_id,formatted_address",
        "key": "YOUR_API_KEY"
    }
)
data = response.json()
```

**Day 26 — Async Python (asyncio)**
- Why async exists: waiting for I/O without blocking
- `async def`, `await`, `asyncio.gather`
- Why FastAPI needs async: multiple requests simultaneously
- Common mistake: using sync libraries inside async functions

**Day 27–28 — Testing**
- `pytest` basics
- Unit tests vs integration tests
- `assert` statements and why you write tests before features
- Test your notes_cli.py — every function should have a test

**What to build (Days 21–28 mini-project):**
Add to your notes CLI:
- Auto-detect if a note contains a place name (regex)
- Auto-detect if a note contains a URL
- Auto-detect if a note sounds like a reminder ("remind me", "don't forget", "deadline")
- Tag the note with detected type
- Write `pytest` tests for each detector

**This is your first version of the intent classifier.**

---

### Days 29–38 — Python Backend Patterns

**What to learn:**

**Day 29–30 — Decorators and middleware**
- How `@` decorators work under the hood
- Writing a timing decorator (measures function execution time)
- Writing a retry decorator (retries failed API calls)
- Logging decorator — wraps any function with structured log output

**Day 31–32 — Design patterns for ACOS**
- **Strategy pattern**: different enrichment strategies per note type (place → Maps API, technical → GitHub, creative → pattern matcher)
- **Observer pattern**: when a note is saved, notify all interested handlers
- **Chain of responsibility**: intent classifier passes note through chain of handlers
- **Factory pattern**: create the right tool based on detected intent

**Day 33–35 — Concurrency**
- `threading` vs `multiprocessing` vs `asyncio` — which for what
- Thread safety: why shared state is dangerous
- `concurrent.futures`: `ThreadPoolExecutor` for I/O-bound tasks
- Process pools for CPU-bound tasks (embedding generation)

**Day 36–38 — Structured logging and configuration**
- `structlog` or Python `logging` with JSON output
- 12-Factor App config: all config via environment variables
- `python-dotenv` for local development
- Why print() is not logging and why that matters in production

**What to build (Days 29–38 project):**
Refactor notes CLI into a proper Python package:
```
src/
└── acos_core/
    ├── __init__.py
    ├── models/
    │   ├── note.py          # Note dataclass
    │   └── intent.py        # Intent dataclass
    ├── classifiers/
    │   ├── base.py          # Abstract classifier
    │   ├── place.py         # Detects places
    │   ├── technical.py     # Detects code/tech topics
    │   └── creative.py      # Detects story/creative content
    ├── storage/
    │   └── json_store.py    # Still JSON, PostgreSQL comes in Phase 2
    ├── tools/
    │   └── maps_client.py   # Google Maps API wrapper
    └── tests/
        ├── test_classifiers.py
        └── test_storage.py
```

Push this to GitHub. Write a proper `README.md` with: architecture diagram, how to install, how to run tests (`pytest --cov`), example usage.

---

### Days 39–45 — Python Performance and Production Readiness

**What to learn:**

**Day 39–40 — Profiling and optimisation**
- `cProfile` and `line_profiler`
- Finding bottlenecks before optimising (measure, don't guess)
- Memory profiling with `memory_profiler`
- When to use generators to reduce memory usage

**Day 41–42 — Type hints and Pydantic**
- Python type hints: `str`, `int`, `List[str]`, `Optional[str]`, `Dict[str, Any]`
- Pydantic: runtime type validation with Python classes
- Why Pydantic is the backbone of FastAPI — every API request/response is a Pydantic model
- `BaseModel`, validators, `model_validator`

**Day 43–44 — Advanced testing**
- `pytest` fixtures
- Mocking: `unittest.mock.patch` — mock the Maps API so tests don't hit real endpoints
- Parameterised tests
- Coverage reports with `pytest-cov`

**Day 45 — Code quality tooling**
- `black` (formatter), `ruff` (linter), `mypy` (type checker)
- Pre-commit hooks: run quality checks before every commit
- `pyproject.toml` for project configuration

**Phase 1 Completion Project:**
A fully tested, typed, documented Python package `acos-core` with:
- Intent classifier (place, technical, creative, reminder, reflection)
- Note model with Pydantic
- JSON storage backend
- Google Maps API integration (for place notes)
- 80%+ test coverage
- GitHub Actions CI that runs tests on every push
- `README.md` with architecture, install, test instructions

**Recruiter visibility:** A Python package on GitHub with CI badges, test coverage, proper README, and commit history across 30 days is evidence that you write production-quality Python, not just scripts.

---

## 6. Phase 2 — Databases and Storage (Days 46–70)

### Why This Phase Is Critical

The intelligence of your ACOS depends entirely on how well you store, index, and query data. A note saved without an embedding cannot be semantically searched. A place saved without coordinates cannot appear on a map. A skill graph that is a flat list cannot show you connections. Database design is where ACOS gets its intelligence.

---

### Days 46–52 — SQL and PostgreSQL

**What to learn:**

**Day 46 — Relational model fundamentals**
- Tables, rows, columns, primary keys, foreign keys
- Why normalisation exists — preventing update anomalies
- 1NF, 2NF, 3NF — practical rules, not theoretical exercises
- When to denormalise intentionally (performance vs integrity tradeoff)

**Day 47 — Basic SQL**
```sql
-- Every query you will ever write is a variation of this
SELECT columns
FROM table
JOIN other_table ON condition
WHERE filter
GROUP BY column
HAVING group_filter
ORDER BY column
LIMIT n;
```
Master: `SELECT`, `INSERT`, `UPDATE`, `DELETE`, `JOIN` (inner, left, right, full), `GROUP BY`, `HAVING`, `ORDER BY`, `LIMIT`, `OFFSET`.

**Day 48 — Advanced SQL**
- Window functions: `ROW_NUMBER()`, `RANK()`, `LAG()`, `LEAD()`, `SUM() OVER()`
- CTEs (Common Table Expressions): `WITH cte AS (...)`
- Subqueries vs JOINs — when each performs better
- `EXPLAIN ANALYZE` — reading query execution plans
- Indexes: B-tree, Hash, GIN — when to use each

**Day 49 — PostgreSQL-specific features**
- `JSONB` columns — storing semi-structured data alongside relational data
- Full-text search with `tsvector` and `tsquery`
- Array columns
- Sequences and `SERIAL`/`BIGSERIAL`
- `pg_stat_statements` — seeing what queries are slow

**Day 50–51 — pgvector — semantic search**
```sql
-- Install extension
CREATE EXTENSION IF NOT EXISTS vector;

-- Create a table with an embedding column
CREATE TABLE notes (
    id BIGSERIAL PRIMARY KEY,
    content TEXT NOT NULL,
    note_type VARCHAR(50),
    embedding vector(384),  -- 384 dimensions for all-MiniLM-L6-v2
    created_at TIMESTAMPTZ DEFAULT NOW(),
    metadata JSONB DEFAULT '{}'
);

-- Create vector index for fast similarity search
CREATE INDEX ON notes USING ivfflat (embedding vector_cosine_ops)
    WITH (lists = 100);

-- Find semantically similar notes
SELECT id, content, 1 - (embedding <=> '[0.1, 0.2, ...]'::vector) AS similarity
FROM notes
ORDER BY embedding <=> '[0.1, 0.2, ...]'::vector
LIMIT 5;
```

**Day 52 — Database design for ACOS**
Design and create the full ACOS schema:

```sql
-- Core schema
CREATE TABLE notes (
    id BIGSERIAL PRIMARY KEY,
    raw_text TEXT NOT NULL,
    note_type VARCHAR(50) NOT NULL,  -- place, technical, creative, reflection, media, reminder
    tags TEXT[],
    embedding vector(384),
    created_at TIMESTAMPTZ DEFAULT NOW(),
    updated_at TIMESTAMPTZ DEFAULT NOW(),
    metadata JSONB DEFAULT '{}'
);

CREATE TABLE place_extensions (
    note_id BIGINT PRIMARY KEY REFERENCES notes(id) ON DELETE CASCADE,
    lat DOUBLE PRECISION,
    lng DOUBLE PRECISION,
    place_id VARCHAR(255),  -- Google Place ID
    address TEXT,
    opening_hours JSONB,
    photo_urls TEXT[]
);

CREATE TABLE technical_extensions (
    note_id BIGINT PRIMARY KEY REFERENCES notes(id) ON DELETE CASCADE,
    language VARCHAR(50),
    github_repo VARCHAR(255),
    verified_correct BOOLEAN DEFAULT FALSE,
    linked_docs TEXT[]
);

CREATE TABLE creative_extensions (
    note_id BIGINT PRIMARY KEY REFERENCES notes(id) ON DELETE CASCADE,
    themes TEXT[],
    mood VARCHAR(100),
    genre VARCHAR(100),
    connected_note_ids BIGINT[]
);

CREATE TABLE projects (
    id BIGSERIAL PRIMARY KEY,
    name VARCHAR(255) NOT NULL,
    description TEXT,
    status VARCHAR(50) DEFAULT 'active',
    completion_pct INTEGER DEFAULT 0,
    created_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE TABLE reminders (
    id BIGSERIAL PRIMARY KEY,
    note_id BIGINT REFERENCES notes(id),
    remind_at TIMESTAMPTZ NOT NULL,
    message TEXT,
    delivered BOOLEAN DEFAULT FALSE,
    created_at TIMESTAMPTZ DEFAULT NOW()
);

CREATE TABLE fingerprint_snapshots (
    id BIGSERIAL PRIMARY KEY,
    snapshot_date DATE NOT NULL,
    fingerprint_vector vector(384),
    top_domains TEXT[],
    explore_exploit_ratio FLOAT,
    created_at TIMESTAMPTZ DEFAULT NOW()
);
```

**What to document:**
`docs/database/schema.md` with:
- Entity-relationship diagram (use dbdiagram.io — free, paste SQL)
- Explanation of every table and why it exists
- Index strategy and why
- Query examples for common ACOS operations

---

### Days 53–60 — Redis and Caching

**What to learn:**

**Day 53–54 — Redis data structures**
- Strings: `SET key value EX 3600` (with TTL)
- Lists: push/pop from both ends — perfect for reminder queue
- Hashes: store session data
- Sets: track which topics a user has seen (deduplication)
- Sorted sets: feed items ranked by score — **this is your adaptive feed**
- Pub/Sub: event notifications

**Day 55–56 — Caching strategies**
- Cache-aside: application checks cache first, fills on miss
- Write-through: write to cache and DB simultaneously
- TTL strategy: how long should a scraped news article be cached?
- Cache invalidation: the hardest problem in computer science and why
- Redis keyspace notifications: trigger actions when cache expires

**Day 57–58 — Redis for ACOS adaptive feed**
```python
import redis

r = redis.Redis(host='localhost', port=6379, decode_responses=True)

# Adaptive feed implementation using sorted set
# Score = engagement_score + recency_weight - boredom_penalty
def add_to_feed(user_id: str, card_id: str, score: float):
    r.zadd(f"feed:{user_id}", {card_id: score})

# Get top 10 feed items
def get_feed(user_id: str, count: int = 10):
    return r.zrevrange(f"feed:{user_id}", 0, count-1, withscores=True)

# Mark as seen (remove from feed)
def mark_seen(user_id: str, card_id: str):
    r.zrem(f"feed:{user_id}", card_id)
    r.sadd(f"seen:{user_id}", card_id)

# Reminder queue (sorted by remind_at timestamp)
def schedule_reminder(reminder_id: str, remind_at_unix: float, message: str):
    r.zadd("reminders:queue", {reminder_id: remind_at_unix})
    r.hset(f"reminder:{reminder_id}", mapping={"message": message})
```

**Day 59–60 — Redis persistence and production config**
- RDB snapshots vs AOF persistence — which for ACOS
- Redis eviction policies: `allkeys-lru` for cache, `noeviction` for critical queues
- Redis Sentinel for high availability (concept — implement later)
- Connection pooling

---

### Days 61–70 — Storage Patterns and Migration

**What to learn:**

**Day 61–63 — Alembic: database migrations**
- Why you never manually alter a production database
- Migration files as code — version-controlled schema changes
- `alembic init`, `alembic revision --autogenerate`, `alembic upgrade head`
- Rollback strategy
- Zero-downtime migrations: adding columns is safe, dropping columns is dangerous

**Day 64–66 — SQLAlchemy ORM**
- Why ORMs: write Python, not SQL strings
- Models, sessions, relationships
- Lazy vs eager loading — the N+1 query problem
- Async SQLAlchemy for FastAPI
- When to bypass the ORM and write raw SQL (complex analytics queries)

**Day 67–68 — Full-text and vector search optimisation**
- Query planning for vector search with pgvector
- Combining text search and vector search (hybrid search)
- Benchmarking: measure search latency at 100, 1,000, 10,000 notes
- Index tuning for your specific query patterns

**Day 69–70 — Phase 2 Integration Project**
Migrate `acos-core` from JSON storage to PostgreSQL:
- Replace `json_store.py` with SQLAlchemy models
- Implement all CRUD operations
- Add `alembic` migrations
- Write integration tests that use a real test database
- Add semantic search: when you search for "calm coffee places", find notes semantically related to "peaceful, quiet café"
- Benchmark: show query times in `docs/database/benchmarks.md`

**Proof-of-work artifact:**
`docs/database/` containing:
- `schema.md` with ER diagram
- `migrations/` documenting every schema change
- `benchmarks.md` with search latency at different data sizes
- `query-examples.sql` with annotated queries

This shows: you understand relational design, can add vector search to PostgreSQL, and benchmark your own system — things most junior devs never do.

---

## 7. Phase 3 — Networks and APIs (Days 71–100)

### Days 71–80 — FastAPI Backend

**What to learn:**

**Day 71–73 — FastAPI fundamentals**
```python
from fastapi import FastAPI, HTTPException, Depends
from pydantic import BaseModel
from typing import Optional
import uvicorn

app = FastAPI(title="ACOS API", version="1.0.0")

class NoteCreate(BaseModel):
    raw_text: str
    note_type: Optional[str] = None  # auto-detected if None

class NoteResponse(BaseModel):
    id: int
    raw_text: str
    note_type: str
    tags: list[str]
    created_at: str

@app.post("/api/v1/notes", response_model=NoteResponse, status_code=201)
async def create_note(note: NoteCreate, db = Depends(get_db)):
    """
    Create a new note. Automatically detects intent and triggers enrichment.
    """
    detected_intent = await intent_classifier.classify(note.raw_text)
    saved_note = await note_service.create(note.raw_text, detected_intent, db)
    await enrichment_service.enrich_async(saved_note)  # non-blocking
    return saved_note

if __name__ == "__main__":
    uvicorn.run("main:app", host="0.0.0.0", port=8000, reload=True)
```

**Day 74–76 — API design best practices**
- REST resource naming: `/api/v1/notes`, not `/api/v1/getNotes`
- Versioning: why `/v1/` exists from day one
- Pagination: `?page=1&limit=20` or cursor-based
- Filtering and sorting as query parameters
- OpenAPI/Swagger: FastAPI generates this automatically — your API is self-documenting
- Error response format: consistent JSON errors everywhere

**Day 77–78 — Authentication (JWT)**
```python
from fastapi.security import OAuth2PasswordBearer, OAuth2PasswordRequestForm
from jose import JWTError, jwt
from passlib.context import CryptContext

# For personal use, single-user JWT is sufficient
SECRET_KEY = os.getenv("JWT_SECRET_KEY")
ALGORITHM = "HS256"
ACCESS_TOKEN_EXPIRE_MINUTES = 60 * 24 * 7  # 7 days

def create_access_token(data: dict):
    return jwt.encode(
        {**data, "exp": datetime.utcnow() + timedelta(minutes=ACCESS_TOKEN_EXPIRE_MINUTES)},
        SECRET_KEY,
        algorithm=ALGORITHM
    )
```

**Day 79–80 — Background tasks and webhooks**
- FastAPI `BackgroundTasks` for async enrichment after saving a note
- Task queues conceptually (Celery + Redis — implement in Phase 4)
- Webhooks: how external services notify your ACOS (GitHub push events, etc.)

---

### Days 81–90 — External API Integrations

**Day 81–83 — Google Maps / Places API**
```python
import httpx

class MapsClient:
    BASE_URL = "https://maps.googleapis.com/maps/api"

    def __init__(self, api_key: str):
        self.api_key = api_key

    async def find_place(self, query: str) -> dict | None:
        async with httpx.AsyncClient() as client:
            response = await client.get(
                f"{self.BASE_URL}/place/findplacefromtext/json",
                params={
                    "input": query,
                    "inputtype": "textquery",
                    "fields": "name,geometry,place_id,formatted_address,opening_hours",
                    "key": self.api_key
                }
            )
            data = response.json()
            if data["status"] == "OK" and data["candidates"]:
                return data["candidates"][0]
        return None
```

**Day 84–86 — YouTube transcript extraction**
```python
from youtube_transcript_api import YouTubeTranscriptApi

def get_transcript(video_url: str) -> str:
    video_id = extract_video_id(video_url)
    transcript = YouTubeTranscriptApi.get_transcript(video_id)
    return " ".join([entry["text"] for entry in transcript])
```

**Day 87–88 — Web scraping (Playwright)**
```python
from playwright.async_api import async_playwright

async def scrape_article(url: str) -> dict:
    async with async_playwright() as p:
        browser = await p.chromium.launch()
        page = await browser.new_page()
        await page.goto(url)
        title = await page.title()
        content = await page.inner_text("article, main, .content")
        await browser.close()
        return {"url": url, "title": title, "content": content}
```

**Day 89–90 — Rate limiting and resilience**
- Exponential backoff for failed API calls
- Circuit breaker pattern: stop calling a failing service
- API rate limit awareness: track calls, sleep when approaching limits
- `httpx` retry middleware

---

### Days 91–100 — Complete API Layer

**Day 91–95 — Full ACOS API**
Build out all endpoints:
```
POST   /api/v1/notes              Create note (auto-classify + enrich)
GET    /api/v1/notes              List notes (paginated, filterable)
GET    /api/v1/notes/:id          Get single note
PUT    /api/v1/notes/:id          Update note
DELETE /api/v1/notes/:id          Delete note
GET    /api/v1/notes/search       Semantic search
GET    /api/v1/feed               Get adaptive feed
POST   /api/v1/feed/:id/engage    Record engagement signal
GET    /api/v1/projects           List projects
POST   /api/v1/projects           Create project
GET    /api/v1/projects/:id/progress  Progress report
POST   /api/v1/reminders          Create reminder
GET    /api/v1/map/notes          Notes with coordinates (for map view)
GET    /api/v1/fingerprint        Current creative fingerprint state
POST   /api/v1/ingest/youtube     Submit YouTube URL for processing
POST   /api/v1/ingest/url         Submit article URL for scraping
```

**Day 96–100 — API testing and documentation**
- Bruno (API client): create a collection with all endpoints, example requests/responses
- Export Bruno collection to `docs/api/` in GitHub
- `pytest` integration tests for every endpoint
- OpenAPI spec exported to `docs/api/openapi.json`

**Proof-of-work:**
Running `docker compose up` → visiting `http://localhost:8000/docs` → seeing a fully interactive API documentation page with all endpoints. Screenshot this. It shows you can build a self-documenting production API.

---

## 8. Phase 4 — Backend Systems (Days 101–140)

### Days 101–115 — Task Queues and Scheduling

**What to learn:**

**Day 101–105 — Celery + Redis task queue**
```python
from celery import Celery
from kombu import Queue

celery_app = Celery(
    "acos",
    broker="redis://localhost:6379/0",
    backend="redis://localhost:6379/1",
    include=["acos.tasks.enrichment", "acos.tasks.feed", "acos.tasks.reminders"]
)

celery_app.conf.task_queues = (
    Queue("high_priority"),    # Reminders
    Queue("normal"),           # Enrichment
    Queue("low_priority"),     # Feed generation
)

# Task: enrich a note after saving
@celery_app.task(queue="normal", max_retries=3)
def enrich_note(note_id: int):
    note = get_note(note_id)
    if note.note_type == "place":
        result = maps_client.find_place(note.raw_text)
        save_place_extension(note_id, result)
    elif note.note_type == "technical":
        result = github_client.find_related_repos(note.raw_text)
        save_technical_extension(note_id, result)
    # ... etc

# Beat scheduler for periodic tasks
celery_app.conf.beat_schedule = {
    "update-fingerprint-weekly": {
        "task": "acos.tasks.fingerprint.update_fingerprint",
        "schedule": crontab(hour=0, minute=0, day_of_week=0),  # Every Sunday midnight
    },
    "check-reminders-every-minute": {
        "task": "acos.tasks.reminders.check_and_deliver",
        "schedule": 60.0,  # Every 60 seconds
    },
    "refresh-feed-daily": {
        "task": "acos.tasks.feed.refresh_all_feeds",
        "schedule": crontab(hour=6, minute=0),  # Every morning 6am
    },
}
```

**Day 106–110 — Reminder engine**
A production reminder engine has three parts:
1. **Storage:** `reminders` table in PostgreSQL
2. **Queue:** Redis sorted set where score = Unix timestamp of `remind_at`
3. **Poller:** Celery beat task running every minute — fetch all reminders where `score <= now`, mark delivered, send notification

Notification delivery options (all free, self-hosted):
- **Ntfy.sh:** Push notifications to your phone via a simple HTTP POST — no account needed if self-hosted
- **Email via SMTP:** Send to yourself using Gmail SMTP
- **Apprise:** Python library supporting 80+ notification services

**Day 111–115 — Event system (Observer pattern at scale)**
```python
from dataclasses import dataclass
from typing import Callable

@dataclass
class Event:
    type: str
    payload: dict

class EventBus:
    def __init__(self):
        self._handlers: dict[str, list[Callable]] = {}

    def subscribe(self, event_type: str, handler: Callable):
        self._handlers.setdefault(event_type, []).append(handler)

    async def publish(self, event: Event):
        for handler in self._handlers.get(event.type, []):
            await handler(event)

# When a note is saved, publish event — all interested systems react
event_bus.publish(Event(type="note.created", payload={"note_id": 42, "type": "place"}))
# Handlers: enrichment service, feed service, fingerprint update, reminder detector
```

---

### Days 116–130 — Intelligence Layer Implementation

**Day 116–120 — Intent classifier**
```python
import re
from dataclasses import dataclass
from enum import Enum

class IntentType(Enum):
    PLACE = "place"
    TECHNICAL = "technical"
    CREATIVE = "creative"
    REMINDER = "reminder"
    MEDIA = "media"
    REFLECTION = "reflection"
    RESEARCH = "research"

@dataclass
class DetectedIntent:
    primary: IntentType
    secondary: list[IntentType]
    entities: dict  # extracted entities: place names, URLs, dates, etc.
    confidence: float

class IntentClassifier:
    PLACE_PATTERNS = [
        r'\b(cafe|restaurant|place|visited|went to|tried)\b',
        r'\b(near|at|in|around)\s+[A-Z][a-z]+',
    ]
    REMINDER_PATTERNS = [
        r'\b(remind me|don\'t forget|deadline|due|schedule|set reminder)\b',
    ]
    TECHNICAL_PATTERNS = [
        r'\b(java|python|api|database|docker|git|code|function|class)\b',
    ]

    def classify(self, text: str) -> DetectedIntent:
        text_lower = text.lower()
        scores = {}

        for intent_type, patterns in [
            (IntentType.PLACE, self.PLACE_PATTERNS),
            (IntentType.REMINDER, self.REMINDER_PATTERNS),
            (IntentType.TECHNICAL, self.TECHNICAL_PATTERNS),
        ]:
            score = sum(1 for p in patterns if re.search(p, text_lower, re.I))
            scores[intent_type] = score / len(patterns)

        # Upgrade to local LLM in Phase 5 — this regex baseline ships first
        primary = max(scores, key=scores.get)
        return DetectedIntent(
            primary=primary,
            secondary=[k for k, v in scores.items() if v > 0 and k != primary],
            entities=self._extract_entities(text),
            confidence=scores[primary]
        )
```

**Day 121–125 — Creative fingerprint algorithm**
```python
import numpy as np
from sentence_transformers import SentenceTransformer

class FingerprintEngine:
    def __init__(self, db, model_name="all-MiniLM-L6-v2"):
        self.db = db
        self.model = SentenceTransformer(model_name)

    async def compute_fingerprint(self, user_id: str) -> np.ndarray:
        """
        Weighted average of all note embeddings.
        Recent notes weighted more heavily.
        High-engagement notes weighted more heavily.
        """
        notes = await self.db.fetch_all_notes_with_engagement()
        if not notes:
            return np.zeros(384)

        embeddings = np.array([n.embedding for n in notes])
        recency_weights = self._recency_weights([n.created_at for n in notes])
        engagement_weights = np.array([n.engagement_score for n in notes])
        combined_weights = recency_weights * engagement_weights
        combined_weights /= combined_weights.sum()

        return np.average(embeddings, axis=0, weights=combined_weights)

    def _recency_weights(self, timestamps) -> np.ndarray:
        """Exponential decay: recent notes matter more."""
        now = datetime.utcnow()
        ages_days = [(now - t).days for t in timestamps]
        return np.exp(-0.1 * np.array(ages_days))
```

**Day 126–130 — Historical analogy engine**
```python
class HistoricalAnalogyEngine:
    """
    Given a creative/research note, find historical events with similar patterns.
    Strategy:
    1. Extract key themes from note (using local LLM or keyword extraction)
    2. Embed the themes
    3. Search historical events DB by vector similarity
    4. Return top 3 analogies with explanation
    """

    HISTORICAL_EVENTS_DB = "data/historical_events.json"  # Build this yourself

    async def find_analogies(self, note_content: str) -> list[dict]:
        themes = await self.extract_themes(note_content)
        theme_embedding = self.model.encode(themes)
        similar_events = await self.db.vector_search(
            table="historical_events",
            query_vector=theme_embedding,
            limit=3
        )
        return [
            {
                "event": e.title,
                "year": e.year,
                "similarity": e.similarity,
                "parallel": await self.explain_parallel(note_content, e),
                "plot_trigger": await self.generate_plot_trigger(note_content, e)
            }
            for e in similar_events
        ]
```

---

### Days 131–140 — Adaptive Feed Engine

```python
class AdaptiveFeedEngine:
    """
    The cognitive Instagram.
    Surfaces content in three zones:
    - Consolidation (65%): revisit known topics via spaced repetition
    - Adjacent growth (25%): topics close to fingerprint but not yet documented
    - Wild card (10%): completely unrelated domain — prevents calcification
    """

    def __init__(self, db, redis_client, fingerprint_engine):
        self.db = db
        self.redis = redis_client
        self.fingerprint = fingerprint_engine

    async def generate_feed(self, user_id: str, count: int = 20) -> list[FeedCard]:
        fingerprint = await self.fingerprint.compute_fingerprint(user_id)
        explore_ratio = await self.get_explore_exploit_ratio(user_id)

        consolidation_count = int(count * (1 - explore_ratio))
        adjacent_count = int(count * explore_ratio * 0.7)
        wild_count = count - consolidation_count - adjacent_count

        cards = []
        cards += await self._consolidation_cards(user_id, fingerprint, consolidation_count)
        cards += await self._adjacent_cards(user_id, fingerprint, adjacent_count)
        cards += await self._wild_cards(user_id, fingerprint, wild_count)

        # Sort by composite score: relevance * engagement_history * recency
        scored = [(c, await self.score_card(c, user_id)) for c in cards]
        scored.sort(key=lambda x: x[1], reverse=True)

        return [c for c, _ in scored]

    async def record_engagement(self, user_id: str, card_id: str, signal: str):
        """
        signal: "deep_read" | "linked_note" | "skipped" | "bored" | "saved"
        Updates explore/exploit dial based on pattern of signals.
        """
        signal_weights = {
            "deep_read": 1.0,
            "linked_note": 1.5,
            "saved": 1.2,
            "skipped": -0.3,
            "bored": -0.5
        }
        weight = signal_weights.get(signal, 0)
        await self.redis.zincrby(f"engagement:{user_id}", weight, card_id)

        if signal == "bored":
            await self.shift_domain(user_id)
```

---

## 9. Phase 5 — AI and Intelligence Layer (Days 141–175)

### Days 141–155 — Embeddings and Semantic Search

**What to learn:**

**Day 141–145 — Sentence transformers and embeddings**
```python
from sentence_transformers import SentenceTransformer
import numpy as np

model = SentenceTransformer("all-MiniLM-L6-v2")  # 384-dim, fast, runs on CPU

# Generate embeddings for notes
def embed_text(text: str) -> list[float]:
    embedding = model.encode(text, normalize_embeddings=True)
    return embedding.tolist()

# Batch embed for efficiency
def embed_batch(texts: list[str]) -> list[list[float]]:
    return model.encode(texts, normalize_embeddings=True, batch_size=32).tolist()

# Semantic similarity
def cosine_similarity(a: list[float], b: list[float]) -> float:
    a, b = np.array(a), np.array(b)
    return float(np.dot(a, b) / (np.linalg.norm(a) * np.linalg.norm(b)))
```

**Day 146–150 — Local LLM with Ollama**
```python
import ollama

class LocalLLM:
    def __init__(self, model="llama3"):
        self.model = model

    async def classify_intent(self, text: str) -> dict:
        response = ollama.chat(
            model=self.model,
            messages=[{
                "role": "system",
                "content": """You are an intent classifier for a personal knowledge system.
                Classify the input into: place, technical, creative, reminder, media, reflection, research.
                Extract entities: place names, URLs, dates, people, concepts.
                Respond in JSON only."""
            }, {
                "role": "user",
                "content": text
            }],
            format="json"
        )
        return json.loads(response["message"]["content"])

    async def generate_plot_trigger(self, note: str, historical_event: dict) -> str:
        response = ollama.chat(
            model=self.model,
            messages=[{
                "role": "user",
                "content": f"""Given this creative note: "{note}"
                And this historical parallel: {historical_event["title"]} ({historical_event["year"]})
                Generate a specific, actionable plot trigger idea in 2-3 sentences."""
            }]
        )
        return response["message"]["content"]
```

**Day 151–155 — Hybrid search (text + vector)**
```python
async def hybrid_search(query: str, limit: int = 10) -> list[Note]:
    """
    Combines:
    1. Full-text search (fast, exact keyword matching)
    2. Vector similarity search (semantic, finds meaning-matches)
    Merges results with Reciprocal Rank Fusion.
    """
    query_embedding = embed_text(query)

    # Run both searches in parallel
    text_results, vector_results = await asyncio.gather(
        db.execute("""
            SELECT id, content, ts_rank(to_tsvector(content), plainto_tsquery($1)) as rank
            FROM notes
            WHERE to_tsvector(content) @@ plainto_tsquery($1)
            ORDER BY rank DESC LIMIT $2
        """, query, limit * 2),

        db.execute("""
            SELECT id, content, 1 - (embedding <=> $1::vector) as similarity
            FROM notes
            ORDER BY embedding <=> $1::vector
            LIMIT $2
        """, str(query_embedding), limit * 2)
    )

    return reciprocal_rank_fusion(text_results, vector_results, limit)
```

---

### Days 156–175 — Scrappy Search and Creative Trigger System

**Day 156–162 — Scrappy search engine**
The scrappy search is your "thinking stimulator". It runs a parallel multi-source search and returns the most *surprising* results — not the most popular.

```python
class ScrappySearchEngine:
    """
    Multi-source parallel search.
    Surprise score = semantic distance from fingerprint + relevance to query.
    A result you'd never have found yourself = high surprise score.
    """

    async def search(self, query: str, user_fingerprint: list[float]) -> list[ScrappyResult]:
        sources = await asyncio.gather(
            self.search_web(query),
            self.search_wikipedia(query),
            self.search_arxiv(query),  # For technical topics
            self.search_historical_db(query),
            self.search_your_own_notes(query),  # Cross-reference with what you know
        )

        all_results = [r for source in sources for r in source]
        scored = []
        for result in all_results:
            result_embedding = embed_text(result.summary)
            relevance = cosine_similarity(result_embedding, embed_text(query))
            surprise = 1 - cosine_similarity(result_embedding, user_fingerprint)
            # Surprise * Relevance: relevant BUT different from what you already know
            scored.append((result, relevance * 0.4 + surprise * 0.6))

        scored.sort(key=lambda x: x[1], reverse=True)
        return [r for r, _ in scored[:5]]
```

**Day 163–170 — Historical events database**
Build your own historical events corpus:
```python
# Sources:
# 1. Wikipedia API — free, structured
# 2. Project Gutenberg — public domain historical texts
# 3. GDELT Project — news event database (free)

import wikipedia

def build_historical_event(topic: str) -> dict:
    page = wikipedia.page(topic)
    return {
        "title": page.title,
        "summary": page.summary[:500],
        "content": page.content[:3000],
        "year": extract_year(page.content),
        "themes": extract_themes(page.content),
        "embedding": embed_text(page.summary)
    }

# Seed 500+ historical events across:
# Politics, wars, social movements, scientific discoveries,
# cultural shifts, economic crises, technological revolutions
```

**Day 171–175 — Feed card generation system**
Every feed item is a card. Cards are generated by card factories:

```python
class FeedCardFactory:
    card_types = {
        "recall_quiz": RecallQuizCard,
        "historical_parallel": HistoricalParallelCard,
        "scrappy_search": ScrappySearchCard,
        "youtube_summary": YouTubeSummaryCard,
        "gap_detection": GapDetectionCard,
        "plot_trigger": PlotTriggerCard,
        "place_memory": PlaceMemoryCard,
        "progress_report": ProgressReportCard,
    }

    async def create(self, card_type: str, context: dict) -> FeedCard:
        factory = self.card_types[card_type]
        return await factory.generate(context)
```

---

## 10. Phase 6 — Frontend and Mobile (Days 176–210)

### Days 176–190 — React Web App

**What to learn:**

**Day 176–180 — React fundamentals**
- Components, props, state
- `useState`, `useEffect`, `useCallback`, `useMemo`
- Context API for global state (auth, theme)
- React Router for navigation
- Fetch API / axios for API calls

**Day 181–185 — ACOS Web UI components**
Build these components:
```
src/
├── components/
│   ├── FeedCard/           # The adaptive feed card — swipe to skip
│   ├── NoteInput/          # Free-form note entry with intent preview
│   ├── KnowledgeGraph/     # D3.js force-directed graph of note connections
│   ├── MapView/            # Leaflet.js map with your pinned places
│   ├── ProgressDashboard/  # Project progress, skill coverage, streaks
│   └── RemindersPanel/     # Upcoming reminders
├── pages/
│   ├── Feed.jsx            # Main feed view
│   ├── Notes.jsx           # All notes, searchable
│   ├── Projects.jsx        # Project tracker
│   └── Map.jsx             # Places map
```

**Day 186–190 — PWA (Progressive Web App)**
```javascript
// service-worker.js — makes the app work offline
const CACHE_NAME = "acos-v1";
const OFFLINE_RESOURCES = ["/", "/index.html", "/manifest.json"];

self.addEventListener("install", (event) => {
    event.waitUntil(
        caches.open(CACHE_NAME).then(cache => cache.addAll(OFFLINE_RESOURCES))
    );
});

// manifest.json — enables "Add to Home Screen" on Android/iOS
{
    "name": "ACOS",
    "short_name": "ACOS",
    "start_url": "/",
    "display": "standalone",
    "theme_color": "#1a1a2e",
    "background_color": "#1a1a2e",
    "icons": [{"src": "/icon-512.png", "sizes": "512x512", "type": "image/png"}]
}
```

Install the PWA on your Android: visit `http://YOUR_PC_IP:3000` in Chrome → three dots → "Add to Home Screen". Your ACOS now lives on your phone's home screen as a full-screen app.

---

### Days 191–210 — React Native Mobile App

**What to learn:**
- Expo: zero-config React Native development environment
- Navigation: `@react-navigation/native`
- Local notifications: `expo-notifications` (for reminder delivery directly to phone)
- Offline storage: `expo-sqlite` (local SQLite for offline note entry)
- Location: `expo-location` (auto-detect location when adding a place note)

**Key mobile-specific features for ACOS:**
```javascript
// Auto-detect location when note contains place intent
import * as Location from 'expo-location';

async function handleNoteSubmit(text: string) {
    const intent = await detectIntent(text);  // Calls your API
    if (intent.primary === 'place') {
        const location = await Location.getCurrentPositionAsync();
        // Pre-fill coordinates before sending to API
        submitNote({text, location});
    } else {
        submitNote({text});
    }
}

// Local notification for reminders
import * as Notifications from 'expo-notifications';

async function scheduleReminder(message: string, triggerDate: Date) {
    await Notifications.scheduleNotificationAsync({
        content: { title: "ACOS Reminder", body: message },
        trigger: { date: triggerDate }
    });
}
```

---

## 11. Phase 7 — DevOps and Infrastructure (Days 211–245)

### Days 211–225 — Docker Compose Production Stack

**Full `docker-compose.yml` for your ACOS:**
```yaml
version: "3.9"

services:
  nginx:
    image: nginx:alpine
    ports:
      - "80:80"
      - "443:443"
    volumes:
      - ./nginx/nginx.conf:/etc/nginx/nginx.conf:ro
      - ./nginx/certs:/etc/nginx/certs:ro
    depends_on: [api]

  api:
    build: ./src/api
    environment:
      DATABASE_URL: postgresql+asyncpg://acos_user:acos_pass@postgres:5432/acos
      REDIS_URL: redis://redis:6379
      OLLAMA_HOST: http://ollama:11434
      GOOGLE_MAPS_API_KEY: ${GOOGLE_MAPS_API_KEY}
    depends_on:
      postgres: {condition: service_healthy}
      redis: {condition: service_healthy}

  worker:
    build: ./src/api
    command: celery -A acos.celery worker --loglevel=info -Q high_priority,normal,low_priority
    environment:
      DATABASE_URL: postgresql+asyncpg://acos_user:acos_pass@postgres:5432/acos
      REDIS_URL: redis://redis:6379

  beat:
    build: ./src/api
    command: celery -A acos.celery beat --loglevel=info
    depends_on: [worker]

  postgres:
    image: pgvector/pgvector:pg16
    environment:
      POSTGRES_DB: acos
      POSTGRES_USER: acos_user
      POSTGRES_PASSWORD: acos_pass
    volumes:
      - postgres_data:/var/lib/postgresql/data
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U acos_user -d acos"]
      interval: 10s
      timeout: 5s
      retries: 5

  redis:
    image: redis:7-alpine
    volumes:
      - redis_data:/data
    healthcheck:
      test: ["CMD", "redis-cli", "ping"]

  ollama:
    image: ollama/ollama
    volumes:
      - ollama_data:/root/.ollama
    ports:
      - "11434:11434"

  prometheus:
    image: prom/prometheus
    volumes:
      - ./monitoring/prometheus.yml:/etc/prometheus/prometheus.yml
      - prometheus_data:/prometheus

  grafana:
    image: grafana/grafana
    ports:
      - "3001:3000"
    volumes:
      - grafana_data:/var/lib/grafana
    environment:
      GF_SECURITY_ADMIN_PASSWORD: ${GRAFANA_PASSWORD}

  loki:
    image: grafana/loki
    volumes:
      - loki_data:/loki

volumes:
  postgres_data:
  redis_data:
  ollama_data:
  prometheus_data:
  grafana_data:
  loki_data:
```

---

### Days 226–235 — CI/CD with GitHub Actions

```yaml
# .github/workflows/ci.yml
name: ACOS CI

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    services:
      postgres:
        image: pgvector/pgvector:pg16
        env:
          POSTGRES_DB: acos_test
          POSTGRES_USER: acos_user
          POSTGRES_PASSWORD: acos_pass
        ports: ["5432:5432"]
        options: --health-cmd pg_isready --health-interval 10s

      redis:
        image: redis:7-alpine
        ports: ["6379:6379"]

    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-python@v5
        with: {python-version: "3.11"}
      - run: pip install -r requirements-dev.txt
      - run: alembic upgrade head
        env: {DATABASE_URL: "postgresql://acos_user:acos_pass@localhost/acos_test"}
      - run: pytest --cov=src --cov-report=xml -v
      - uses: codecov/codecov-action@v4

  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - run: docker build -t acos-api:${{ github.sha }} ./src/api
      - run: docker build -t acos-web:${{ github.sha }} ./src/web
```

---

### Days 236–245 — Monitoring, Observability, and Alerting

**Prometheus metrics in your FastAPI app:**
```python
from prometheus_client import Counter, Histogram, Gauge
from prometheus_fastapi_instrumentator import Instrumentator

notes_created = Counter("acos_notes_created_total", "Total notes created", ["note_type"])
search_latency = Histogram("acos_search_latency_seconds", "Search query latency")
feed_size = Gauge("acos_feed_size", "Current feed item count")

@app.on_event("startup")
async def startup():
    Instrumentator().instrument(app).expose(app)

@app.post("/api/v1/notes")
async def create_note(note: NoteCreate):
    notes_created.labels(note_type=detected_intent).inc()
    # ...
```

**Grafana dashboards to build:**
1. **System health:** CPU, RAM, disk per container
2. **API metrics:** request rate, latency p50/p95/p99, error rate
3. **ACOS metrics:** notes created per day, feed engagement, search latency
4. **Database:** query performance, connection pool, vacuum stats

Save dashboard JSON exports to `docs/monitoring/dashboards/`. Screenshot them. This is production-grade observability.

---

## 12. Phase 8 — System Integration (Days 246–280)

### Days 246–260 — Wire All Layers

This phase has one goal: make the full system work end-to-end. Every piece built in Phases 0–7 gets connected.

**Integration test: full note lifecycle**
```
1. Open ACOS mobile app
2. Type: "I want a reminder to study Java virtual threads tomorrow morning"
3. System fires:
   - Intent classifier → detects REMINDER + TECHNICAL
   - Entity extractor → extracts "Java virtual threads", "tomorrow morning"
   - Reminder engine → creates reminder at next day 9:00 AM
   - Technical classifier → links to Java skill graph
   - Progress tracker → notes gap in Java coverage
   - Feed engine → queues a "Gap detection" card + "Recall quiz" card
4. Phone receives push notification next morning
5. Feed shows Java virtual threads content
6. Engaging with the card updates explore-exploit dial
```

**Integration test: place note**
```
1. Type: "Incredible filter coffee at this tiny café near Marina Beach, want to revisit"
2. System fires:
   - Intent classifier → PLACE
   - Location detection (if on mobile) → coordinates
   - Google Maps API → finds top candidates, returns place details
   - Confirmation card → user confirms correct place
   - Map pin saved with your note attached
   - Feed engine → queues a "Place memory" card for 2 weeks later (spaced repetition)
```

**Integration test: creative/research trigger**
```
1. Type: "Investigating political decisions behind India's partition for a plot"
2. System fires:
   - Intent classifier → RESEARCH + CREATIVE
   - Historical analogy engine → finds 3 parallels (Korea 1945, Ireland 1921, etc.)
   - Scrappy search → web scrapes 5 recent academic articles on partition
   - Plot trigger generator → creates 3 specific story premises
   - All results packaged as feed cards with engagement tracking
```

---

### Days 261–280 — NGINX Configuration and Local HTTPS

**NGINX reverse proxy config for ACOS:**
```nginx
upstream acos_api {
    server api:8000;
    keepalive 32;
}

server {
    listen 80;
    server_name acos.local;
    return 301 https://$host$request_uri;
}

server {
    listen 443 ssl http2;
    server_name acos.local;

    ssl_certificate /etc/nginx/certs/acos.local.crt;
    ssl_certificate_key /etc/nginx/certs/acos.local.key;

    # API
    location /api/ {
        proxy_pass http://acos_api;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }

    # WebSocket for real-time feed updates
    location /ws/ {
        proxy_pass http://acos_api;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
    }

    # Frontend
    location / {
        root /usr/share/nginx/html;
        try_files $uri $uri/ /index.html;
    }
}
```

Generate local SSL certs with `mkcert`:
```bash
sudo apt install mkcert libnss3-tools
mkcert -install
mkcert acos.local "*.acos.local" localhost 127.0.0.1 ::1
```

Add to `/etc/hosts` on both PC and phone (via router DNS):
```
192.168.1.100  acos.local
```

---

## 13. Phase 9 — Production Hardening (Days 281–300)

### Days 281–290 — Security

**What to implement:**
- Input validation on every API endpoint (Pydantic + custom validators)
- SQL injection prevention (SQLAlchemy parameterised queries — already done)
- Rate limiting per endpoint (slowapi + Redis)
- CORS properly configured (only your phone's origin allowed)
- Secrets management: `.env` file, never committed, loaded via docker-compose env
- Database connection encryption (SSL mode for PostgreSQL)
- Dependency scanning: `pip-audit` in CI pipeline

**Security audit checklist (`docs/security/audit.md`):**
- [ ] No hardcoded secrets in codebase
- [ ] All endpoints require authentication
- [ ] Rate limiting on auth endpoints
- [ ] Database not exposed on public interface
- [ ] HTTPS only (HTTP redirects to HTTPS)
- [ ] Dependencies have no known CVEs

---

### Days 291–296 — Performance and Scalability

**Benchmarks to run and document:**

```bash
# Load test the API with locust
pip install locust

# locustfile.py
from locust import HttpUser, task, between

class ACOSUser(HttpUser):
    wait_time = between(1, 3)

    @task(3)
    def get_feed(self):
        self.client.get("/api/v1/feed", headers=self.auth_headers)

    @task(2)
    def create_note(self):
        self.client.post("/api/v1/notes",
            json={"raw_text": "Test note for load testing"},
            headers=self.auth_headers)

    @task(1)
    def search(self):
        self.client.get("/api/v1/notes/search?q=java", headers=self.auth_headers)

locust -f locustfile.py --headless -u 50 -r 5 --run-time 60s --host http://localhost
```

Document results in `docs/performance/load-test-results.md`.

---

### Days 297–300 — Final Documentation Sprint

**What to produce:**
1. `README.md` — complete rewrite with final architecture
2. `docs/ARCHITECTURE.md` — deep system design document
3. `docs/OPERATIONS.md` — how to run, backup, restore, upgrade
4. `docs/API.md` — link to OpenAPI spec
5. `docs/DECISIONS.md` — Architecture Decision Records (ADRs) for every major choice

---

## 14. Documentation Master Strategy

### The Core Principle

Documentation is not what you write after building. Documentation is **proof that you built and understood** what you built. Every artifact below is an answer to the question: "How would a senior engineer verify this person actually built this?"

---

### Domain → Platform → Format Mapping

#### Technical/Backend Code
| Artifact | Platform | Format | Recruiter Signal |
|---|---|---|---|
| Source code | GitHub | Well-structured repo, conventional commits | "They write production code, not scripts" |
| API documentation | GitHub Pages + OpenAPI | Auto-generated Swagger UI | "They document APIs like a team would" |
| Architecture decisions | GitHub (`docs/DECISIONS.md`) | ADR format (context, decision, consequences) | "They think in tradeoffs, not just features" |
| Test coverage | Codecov badge on README | Coverage report linked from CI | "They write tests — rare at junior level" |
| CI/CD proof | GitHub Actions tab | Green workflow runs, badge in README | "Their code ships through a pipeline" |

#### Database/Storage
| Artifact | Platform | Format | Recruiter Signal |
|---|---|---|---|
| Schema design | GitHub + dbdiagram.io | ER diagram + SQL DDL | "They design schemas before writing queries" |
| Migration history | GitHub (alembic migrations) | Versioned migration files | "They evolve schemas safely" |
| Query benchmarks | GitHub (`docs/database/benchmarks.md`) | Markdown with timing tables + EXPLAIN ANALYZE output | "They measure before optimising" |
| Index strategy | GitHub (`docs/database/indexes.md`) | Reasoning doc | "They understand query planning" |

#### Infrastructure/DevOps
| Artifact | Platform | Format | Recruiter Signal |
|---|---|---|---|
| Docker Compose | GitHub | `docker-compose.yml` with comments | "They can containerise a real stack" |
| Monitoring dashboards | GitHub | Grafana dashboard JSON exports + screenshots | "They built observability, not just code" |
| NGINX config | GitHub | Annotated config file | "They've done real web server configuration" |
| Load test results | GitHub | Markdown with charts | "They know what their system can handle" |

#### AI/ML Layer
| Artifact | Platform | Format | Recruiter Signal |
|---|---|---|---|
| Embedding benchmarks | GitHub + Jupyter notebook | Notebook with visualisations | "They understand what embeddings actually do" |
| Model comparison | GitHub | Markdown table comparing models on your use case | "They evaluate, not just pick randomly" |
| Search quality metrics | GitHub | Precision/recall at k for semantic search | "They measure ML system quality" |

#### Frontend/Mobile
| Artifact | Platform | Format | Recruiter Signal |
|---|---|---|---|
| Live demo | GitHub Pages / PWA link | Deployed and accessible | "It actually runs" |
| Component documentation | Storybook (optional) | Interactive component library | "They document UI components" |
| Screen recordings | GitHub README / YouTube (unlisted) | 60–90 second walkthrough | "They can show the system working end-to-end" |

---

### GitHub Repository Structure

```
acos-project/
├── README.md                    ← Hero doc: what, why, demo GIF, quick start
├── CHANGELOG.md                 ← Version history (keep-a-changelog format)
├── LICENSE                      ← MIT or Apache 2.0
├── .github/
│   ├── workflows/
│   │   ├── ci.yml
│   │   └── deploy.yml
│   └── ISSUE_TEMPLATE/
│       ├── bug_report.md
│       └── feature_request.md
├── docs/
│   ├── ARCHITECTURE.md          ← Full system design document
│   ├── DECISIONS.md             ← ADR log
│   ├── OPERATIONS.md            ← Runbook: setup, backup, restore
│   ├── api/
│   │   ├── openapi.json
│   │   └── examples/            ← Bruno API collection
│   ├── database/
│   │   ├── schema.md
│   │   ├── benchmarks.md
│   │   └── indexes.md
│   ├── diagrams/
│   │   ├── system-architecture.png
│   │   ├── data-flow.png
│   │   └── home-network.png
│   ├── monitoring/
│   │   └── dashboards/          ← Grafana JSON exports
│   ├── performance/
│   │   └── load-test-results.md
│   ├── security/
│   │   └── audit.md
│   └── journal/                 ← Your daily learning notes (Phase 0–9)
│       ├── phase-0/
│       ├── phase-1/
│       └── ...
├── src/
│   ├── api/                     ← FastAPI backend
│   ├── worker/                  ← Celery tasks
│   ├── web/                     ← React web app
│   └── mobile/                  ← React Native app
├── scripts/
│   ├── system-health.sh
│   ├── backup-db.sh
│   └── seed-historical-events.py
├── monitoring/
│   ├── prometheus.yml
│   └── grafana/
├── nginx/
│   └── nginx.conf
└── docker-compose.yml
```

### Commit Message Convention

Use Conventional Commits — it generates a changelog automatically:
```
feat: add semantic search to notes API
fix: correct timezone handling in reminder engine
docs: add database schema ER diagram
test: add integration tests for feed card generation
chore: upgrade sentence-transformers to 3.0
refactor: extract intent classifier into separate module
perf: add ivfflat index to reduce vector search latency by 60%
```

---

## 15. Portfolio and Proof-of-Work System

### What Makes This Project Stand Out

Most junior engineers build TODO apps or weather apps. You are building a system that:
- Uses PostgreSQL with vector extensions (pgvector) — used by companies doing AI search
- Runs a local LLM and generates embeddings — AI engineering
- Has a real task queue (Celery + Redis) — backend systems engineering
- Has Prometheus + Grafana monitoring — infrastructure engineering
- Deploys via Docker Compose — DevOps
- Has CI/CD with GitHub Actions — modern engineering practice
- Integrates 4+ external APIs — integration engineering
- Has a React + React Native frontend — full stack

This is a portfolio piece that demonstrates more depth than most engineers have after 2 years of work.

---

### Proof-of-Work Artifacts (Produce All of These)

**1. The Demo Video (most important)**
Record a 3–5 minute screen recording showing:
- You typing a natural language statement
- The intent classifier detecting intent
- The enrichment happening (place pin appearing on map, YouTube video being summarised)
- The adaptive feed updating
- A historical analogy trigger being generated
- A reminder being delivered to your phone

Upload: YouTube (unlisted) + GitHub README GIF (compress to < 10MB with `ffmpeg`)

**2. Architecture writeup (for engineering managers)**
Write `docs/ARCHITECTURE.md` as if explaining to a senior engineer joining your team:
- Why you chose PostgreSQL over MongoDB
- Why pgvector instead of a dedicated vector DB
- Why Celery instead of just background tasks
- Why local LLM instead of OpenAI API
- Every decision should have: context, options considered, decision made, consequences accepted

**3. Technical blog posts (for visibility)**
Write 5 blog posts on Dev.to or Hashnode (both free):
1. "Building semantic search with PostgreSQL and pgvector — from zero" (SEO: ranks for "pgvector tutorial")
2. "How I built a personal adaptive feed that's smarter than Instagram" (shareable, interesting angle)
3. "Running Llama 3 locally for intent classification — setup and benchmarks" (technical, specific)
4. "Self-hosting a full AI stack on a consumer PC — architecture and lessons"
5. "From 0 to production: what building an MNC-grade system solo taught me"

Cross-post to LinkedIn. Tag relevant people. These posts are how recruiters find you before you apply.

**4. GitHub profile optimisation**
- Pin this repo on your GitHub profile
- Add a GitHub profile README (same as your main repo README but personal)
- Ensure 300 days of commit activity (don't break the streak)
- Star count matters less than commit history depth

**5. Engineering interview prep from this project**
Every component you built answers a different interview question:
- "Design a feed algorithm" → you built one; explain the explore-exploit dial
- "How would you add semantic search?" → you did this; explain pgvector + hybrid search
- "How do you handle async tasks?" → Celery + Redis, explain the queue design
- "How do you monitor a production system?" → Prometheus + Grafana, show the dashboard
- "How would you scale this?" → you thought about this; explain what would bottleneck first

---

## 16. Active Recall and Conceptual Validation System

### How to Use These

After every phase, attempt all questions without notes. Then check your answers by building the thing. A correct answer you cannot implement is not understanding — it is pattern matching.

---

### Phase 0 Recall Questions
1. A request from your phone to your PC takes what path through the OSI model? Name the layer and what it contributes at each step.
2. Why does Docker need Linux namespaces and cgroups? What breaks without each?
3. What is the difference between a process and a thread? Give an example from ACOS where each is appropriate.

### Phase 1 Recall Questions
1. Your intent classifier is called 1,000 times per second. It uses regex today. What happens to your CPU? What would you change?
2. Why does `asyncio` not speed up CPU-bound code, only I/O-bound code?
3. What is the difference between `@classmethod` and `@staticmethod`? Give a real example from your ACOS codebase where each is right.

### Phase 2 Recall Questions
1. You have 100,000 notes. A vector search takes 2 seconds. What is the query plan doing? What index would you add and why?
2. What is the N+1 query problem? How did SQLAlchemy's lazy loading cause you one?
3. Why does Redis use sorted sets for the feed instead of a list?

### Phase 3 Recall Questions
1. Your ACOS API returns a 200 for a failed enrichment instead of the right error code. What are the downstream consequences?
2. What is the difference between authentication and authorisation? Where does each happen in your FastAPI app?
3. Why does your scraping service use Playwright instead of `requests`?

### Phase 4 Recall Questions
1. A Celery task fails halfway through enriching a note. The note exists in PostgreSQL but has no place extension. How do you detect and recover this?
2. Why does the fingerprint use weighted average rather than simple average? What breaks without weighting?
3. Your reminder queue uses Redis sorted sets. What happens to scheduled reminders if Redis restarts and has no persistence configured?

### Architecture Reasoning Tasks (Do These on Paper)
1. Your ACOS gets popular and 50 friends want to use it. What are the first 3 things that break? How do you fix each?
2. The local LLM inference takes 3 seconds per intent classification. This blocks your API response. What are 3 different architectural solutions? What are the tradeoffs of each?
3. You want to add a "mood detection" feature — ACOS detects your emotional state from your notes over time. What new tables do you need? What new service? What existing system does it integrate with?

---

## Final Note

Every day you follow this roadmap, you are building two things simultaneously:

The first is ACOS — a real, running, MNC-quality system that you use every day and that genuinely makes you more productive, creative, and focused.

The second is evidence — 300 days of dated commits, a system that actually runs, documentation that proves understanding, and a portfolio that answers the question every recruiter and engineering manager is really asking: "Can this person think like an engineer?"

You are not studying to pass a test. You are building a thing that matters to you, and the process of building it is turning you into an engineer.

Start Day 1 today.

---

*Document version: 1.0 | Generated for personal use | Update as you build*