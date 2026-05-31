
# ATLASSIAN — Complete Engineering Master Roadmap
## From Zero Knowledge to MNC-Grade Production Systems
### All Four Projects | Daily Instructions | Concept First | Project Application | Portfolio Strategy

---

> **How to use this document:**
> Every day has a structure: **Concept → Why It Exists → How It Works → Project Application → Practice → Document → Recall**
> Read the concept section first, understand it without a computer.
> Then open the computer and do the practice.
> Never skip the documentation step — that is your proof of work.

---

# PART 0 — READ BEFORE DAY 1

## 0.1 The One Picture That Explains Everything

Before any code, any hardware, any cloud — understand this picture.

Every system you will ever build does five things:

```
SENSE → PROCESS → STORE → ANALYZE → ACT
```

| Step | What It Means | Real Example |
|------|--------------|--------------|
| SENSE | Collect data from the world | Vibration sensor reads motor. GitHub sends webhook. Developer submits form. |
| PROCESS | Transform raw data into structured information | FFT converts vibration to frequency. Kafka routes event. FastAPI validates request. |
| STORE | Keep information for later use | TimescaleDB stores telemetry. PostgreSQL stores service registry. ChromaDB stores bug memory. |
| ANALYZE | Find patterns, predict outcomes, detect problems | TFLite model scores anomaly. XGBoost scores PR risk. LLM generates postmortem. |
| ACT | Do something useful based on analysis | Alert engineer. Block dangerous deployment. Create DNS record. Suggest code fix. |

**Your four projects are all the same pipeline at different layers:**

| Project | SENSE | PROCESS | STORE | ANALYZE | ACT |
|---------|-------|---------|-------|---------|-----|
| SentinelGrid | Vibration/temp/current sensors | FreeRTOS + FFT | TimescaleDB | TFLite edge AI | Maintenance alert |
| PulseGrid | GitHub/PagerDuty/Sentry webhooks | Kafka stream | Neo4j + TimescaleDB | XGBoost + LLM | Risk score on PR |
| MemCore | Python exceptions + logs | AST parser | ChromaDB | CodeBERT + LLM | Fix suggestion |
| InfraMesh | Developer service registration | SQS worker | PostgreSQL | Health checker | DNS + load balancer |

**You are not learning four different things. You are learning one thing — the SENSE→PROCESS→STORE→ANALYZE→ACT pipeline — applied at four different layers.**

---

## 0.2 The Four Projects — One Paragraph Each

**SentinelGrid** sits at the physical layer. Hardware sensors on factory machines send vibration and temperature data. A microcontroller runs AI locally. An anomaly alerts a maintenance engineer before the machine breaks. Target companies: Bosch, Siemens, ABB, any manufacturing company.

**PulseGrid** sits at the engineering intelligence layer. It watches every PR, deployment, and incident in a software organization. It scores deployment risk before disasters happen. It generates postmortems automatically. Target companies: any tech company with 20+ engineers and recurring incidents.

**MemCore** sits at the application intelligence layer. It embeds into any software application and gives it persistent memory of its own bugs. It learns your codebase's patterns. Target companies: any company that wants self-healing software or better debugging.

**InfraMesh** sits at the infrastructure layer. Developers register services and get load balancers, DNS, health checks, and edge protection automatically. Target companies: any platform engineering team tired of manual infrastructure tickets.

---

## 0.3 The Shared Technology Foundation

All four projects use a common set of technologies. Learn each once. Apply to all four.

```
SHARED FOUNDATION
├── Python (language for backend, AI, scripts)
├── C (language for firmware — SentinelGrid + MemCore C agent)
├── FastAPI (REST API framework — all four projects)
├── PostgreSQL (relational database — all four projects)
├── TimescaleDB (time-series database — SentinelGrid + PulseGrid)
├── Redis (cache + rate limiting — InfraMesh + PulseGrid)
├── Docker (container runtime — all four projects)
├── GitHub Actions (CI/CD — all four projects)
├── Terraform (infrastructure as code — all four projects)
├── Grafana (dashboards — all four projects)
├── AWS (cloud platform — all four projects)
└── Git (version control — everything)

PROJECT-SPECIFIC
├── SentinelGrid: FreeRTOS, TFLite Micro, MQTT, AWS IoT Core, Kinesis
├── PulseGrid: Kafka, Neo4j, XGBoost, ChromaDB, Claude API
├── MemCore: tree-sitter, CodeBERT, ChromaDB, Claude API
└── InfraMesh: SQS, Route53, ALB, ACM, CloudFront
```

---

## 0.4 Your GitHub Repository Structure (Set This Up on Day 1)

Create these repositories immediately. Empty is fine. You will fill them daily.

```
github.com/[yourname]/
├── learning-journal/         ← Daily learning documentation (start Day 1)
├── sentinelgrid/            ← Hardware + AI project
├── pulsegrid/               ← Engineering intelligence project
├── memcore/                 ← Embedded AI SDK project
└── inframesh/               ← Infrastructure platform project
```

Each project repository must have this structure from Day 1:

```
project-name/
├── README.md                ← What it is, demo link, architecture diagram
├── ARCHITECTURE.md          ← System design decisions
├── DAILY_LOG.md             ← What you built each day (update daily)
└── docs/                   ← Detailed documentation (add as you learn)
```

---

## 0.5 The Rule That Makes This Work

> **Every concept you learn must be written down in your own words within 24 hours of learning it. Not the definition from the website. Your own words. What it means to YOU. How it fits into your projects.**

If you cannot explain it in your own words, you have not learned it. You have read it.

---

# PART 1 — PHASE 0: MENTAL FOUNDATIONS
## Days 1–21 | Before Any Code

---

### WHY THIS PHASE EXISTS

Most beginners skip straight to code. They write Python for 6 months without understanding why Python exists, what problem it solves, or how it connects to a database or a cloud server. Then they cannot answer interview questions about system design because they have memorized syntax without building mental models.

This phase builds the mental models first. You will understand how the internet works, how computers work, how data flows, and how systems fail — before writing a single function. This takes 3 weeks. It saves you 6 months of confusion later.

---

### DAY 1 — How the Internet Works

**Concept First (Read This Before Opening a Computer)**

The internet is a system of connected computers. When you type `google.com` in your browser, what actually happens?

1. Your browser asks a DNS server: "What is the IP address of google.com?"
2. The DNS server replies: "It is 142.250.80.46"
3. Your browser opens a TCP connection to 142.250.80.46 on port 443
4. Your browser sends an HTTP request: "GET / HTTP/1.1 Host: google.com"
5. Google's server sends back an HTTP response with HTML
6. Your browser renders the HTML

Every single web application you will ever build — InfraMesh, PulseGrid, the SentinelGrid backend — is a machine doing step 5: receiving HTTP requests and sending HTTP responses.

**Why DNS Matters for Your Projects:**
InfraMesh's core job is creating DNS records automatically. When a developer registers a service called `payment-service`, InfraMesh calls AWS Route53 and creates a DNS record so that `payment.company.com` resolves to the service's IP address. Without understanding DNS, you cannot understand InfraMesh.

**Why HTTP Matters for Your Projects:**
Every project has a FastAPI server that receives HTTP requests. PulseGrid receives HTTP webhooks from GitHub (POST requests with JSON bodies). InfraMesh's developers call `POST /api/v1/services` to register services. Understanding HTTP is understanding how all these pieces talk to each other.

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING (2h) | Read: "How DNS Works" — dnsimple.com/support/articles/dns-defined | dnsimple.com |
| MORNING | Read: MDN "HTTP Overview" — developer.mozilla.org/en-US/docs/Web/HTTP/Overview | MDN Web Docs |
| AFTERNOON (2h) | Practice: Open browser → DevTools (F12) → Network tab → load any website → study every request. Identify: request method, URL, status code, response headers | Your browser |
| AFTERNOON | Practice: Linux terminal — `curl -v https://httpbin.org/get` — read every line of the verbose output | Terminal |
| EVENING (1h) | Document in `learning-journal/day-01-internet.md`: Explain DNS and HTTP in your own words. Draw the request/response flow as ASCII art | GitHub commit |

**Mini Assignment:**
Write down: "When PulseGrid receives a GitHub webhook, what HTTP method does GitHub use? What does the URL look like? What is in the body?" Research this on developer.github.com/webhooks.

**Active Recall Questions:**
1. A developer visits `payment.company.com`. Trace the exact journey from their browser to the payment service IP address.
2. InfraMesh needs to create a DNS record. Which AWS service does it call?
3. HTTP status code 200 means success. What does 404 mean? 500? 201? 202?

**End of Day Mental Picture:**
Close your eyes. See: browser → DNS lookup → IP address → TCP connection → HTTP request → server processes → HTTP response → browser renders. This is the foundation of every web project you will build.

---

### DAY 2 — Load Balancers, Proxies, and Routing

**Concept First**

A load balancer sits in front of multiple servers and decides which server handles each incoming request. Without a load balancer, if you have 1000 users, all 1000 hit one server. With a load balancer, 333 hit server A, 333 hit server B, 333 hit server C.

A reverse proxy is like a load balancer but with more intelligence: it can also handle SSL termination (so your servers never deal with HTTPS), add authentication headers, cache responses, and rate-limit requests.

**The InfraMesh Connection:**
InfraMesh's entire job is to provision load balancers automatically. When a developer registers a service, the InfraMesh worker calls the AWS ALB API and creates routing rules. The developer's service immediately gets a load balancer in front of it. Understanding what a load balancer does is prerequisite to understanding what InfraMesh builds.

**The SentinelGrid Connection:**
SentinelGrid's Envoy proxy architecture (from the Atlassian transcript) uses Envoy as a programmable proxy that handles authentication, rate limiting, and routing for all backend services — the same concept as a reverse proxy, applied to industrial infrastructure.

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING (2h) | Read: nginx.com/resources/glossary/reverse-proxy-server | nginx.com |
| MORNING | Read: AWS ALB documentation overview | docs.aws.amazon.com/elasticloadbalancing |
| AFTERNOON (2h) | Install: `sudo apt install nginx` or `brew install nginx`. Configure nginx as reverse proxy to `python3 -m http.server 9000`. Test with `curl http://localhost:80` | Local machine |
| AFTERNOON | Break it: Stop the Python server. Try the curl again. Observe 502 Bad Gateway. This is what a failed health check looks like | Local machine |
| EVENING (1h) | Document: `learning-journal/day-02-loadbalancer.md`. Draw: Internet → Load Balancer → [Server A, Server B, Server C]. Add to InfraMesh README: "This is what InfraMesh automates" | GitHub |

**Active Recall Questions:**
1. A company has one server handling all traffic. 10,000 users visit simultaneously. The server crashes. How does a load balancer prevent this?
2. InfraMesh registers a service. The worker creates an ALB rule. What does the ALB do when a request arrives for that service?
3. What is the difference between a forward proxy and a reverse proxy?

---

### DAY 3 — Linux Command Line Fundamentals

**Concept First**

Every server in the world (SentinelGrid's gateway Raspberry Pi, InfraMesh's EC2 instances, PulseGrid's Kafka cluster) runs Linux. When something breaks in production, a terminal is your only interface to the broken system. No graphical interface. No mouse. Just commands.

Linux is not just a skill — it is the environment where all your software lives in production.

**Why Every Project Needs This:**
- SentinelGrid: SSH into the Raspberry Pi gateway to read MQTT broker logs
- InfraMesh: SSH into EC2 to see why the provisioning worker crashed
- PulseGrid: SSH into Kafka node to check consumer group lag
- MemCore: Terminal is how developers invoke MemCore's CLI (`memcore diagnose`)

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING (2h) | Complete OverTheWire Bandit levels 0–5. Document each level: challenge, command used, what you learned | overthewire.org/wargames/bandit |
| AFTERNOON (2h) | Complete OverTheWire Bandit levels 6–12 | overthewire.org/wargames/bandit |
| EVENING (1h) | Document: `learning-journal/day-03-linux.md`. For each Bandit level completed: write the challenge, the exact command, and what the command does. Commit with message: "Day 3: Linux Bandit levels 0-12 — learned file permissions, hidden files, SSH keys" | GitHub |

**Assignment (Do Before Day 4):**
Without looking anything up, answer: If I am in `/home/user/projects/myapp` and I type `cd ../../etc`, where am I? Why?

**Active Recall Questions:**
1. SentinelGrid's gateway is at IP 192.168.1.100. How do you SSH into it?
2. The InfraMesh worker crashed. You SSH into the EC2. How do you see the last 100 lines of the log file `/var/log/inframesh/worker.log` and keep watching for new lines?
3. The MQTT broker (Mosquitto) is running on port 1883. How do you verify it is actually listening?

---

### DAY 4 — Linux: Processes, Networking, Shell Scripts

**Concept First**

A process is a running program. When you start InfraMesh's FastAPI server, it becomes a process with a unique ID (PID). If it crashes, the PID disappears. If it hangs, the PID is there but the process is not responding.

Shell scripts are programs written in bash — the language of the terminal. They automate repetitive tasks. Your firmware OTA pipeline is a shell script that compiles, signs, and uploads firmware. Your deployment script is a shell script that pulls a Docker image and restarts a container.

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING (2h) | Complete OverTheWire Bandit levels 13–20 | overthewire.org/wargames/bandit |
| AFTERNOON (1h) | Practice: Run `python3 -m http.server 8080`. In another terminal: `ps aux | grep python` (find it), `lsof -i :8080` (see what is on the port), `kill -9 [PID]` (kill it), verify it is gone with `ps aux | grep python` | Terminal |
| AFTERNOON (1h) | Write your first shell script: `deploy.sh` that: creates a directory, copies a file into it, prints "Deployment complete", and logs the timestamp to a file | Text editor + terminal |
| EVENING (1h) | Document: `learning-journal/day-04-processes.md`. Write the shell script you created with explanation of every line | GitHub |

**Debugging Exercise:**
You deploy InfraMesh and the API is not responding. You SSH in. How do you determine if: (a) the process is not running, (b) the process is running but on the wrong port, (c) the process is running but out of memory?

---

### DAY 5 — Git and Version Control

**Concept First**

Git tracks every change to every file. Think of it as an unlimited undo button for your entire codebase that also records who made each change, when, and why.

In a professional team, no code ever goes directly to the main branch. A developer creates a branch, makes changes, opens a pull request, gets a code review, and then merges. This workflow is what PulseGrid monitors — it receives GitHub webhook events for every step of this process.

**Why Git Matters for All Projects:**
- Your firmware CI/CD pipeline triggers when you push to the `main` branch
- PulseGrid ingests PR events to score deployment risk
- Your Terraform infrastructure is versioned in Git — if you delete a resource by accident, you can see exactly what it was
- Every ADR, postmortem, and benchmark document is in Git — provably timestamped

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING (2h) | Complete learngitbranching.js.org — Introduction Sequence (all levels) | learngitbranching.js.org |
| AFTERNOON (2h) | Set up all 5 GitHub repositories. Add README.md with one sentence to each. Make your first meaningful commit to each: "Initial commit: project overview added" | GitHub.com |
| AFTERNOON | Write a `.gitignore` for a Python project. Add: `__pycache__/`, `*.pyc`, `.env`, `venv/`. Understand why each is excluded | GitHub |
| EVENING (1h) | Document: `learning-journal/day-05-git.md`. Write: "Why I chose these commit message formats, why branches exist, and how PulseGrid will watch my Git activity to score deployment risk" | GitHub |

**Active Recall Questions:**
1. You pushed a bug to main by accident. How do you revert to the previous commit without losing history?
2. PulseGrid receives a GitHub webhook when a PR is opened. What information does the webhook contain that PulseGrid uses to compute a risk score?
3. Your firmware has a bug affecting 1000 deployed nodes. You write a fix. Describe the Git workflow from fix to production.

---

### DAYS 6–7 — How Computers Work (CPU, Memory, Storage)

**Concept First (Day 6)**

A CPU executes instructions one at a time (modern CPUs do this billions of times per second). RAM is where data lives while a program runs — it is fast but temporary. Storage (SSD/flash) is where data lives when the program stops — it is slower but permanent.

For SentinelGrid firmware, this is not abstract: the ESP32-S3 has 512KB of RAM and 4MB of flash. Every variable, every stack frame, every buffer must fit in 512KB. If it does not, the firmware crashes. This constraint is why embedded C programming avoids `malloc` (dynamic memory allocation) and uses static buffers instead.

**Concept First (Day 7)**

The stack is where function calls live. Every time you call a function, a stack frame is pushed. When the function returns, the frame is popped. If you call functions recursively without a base case, the stack grows until it overflows — stack overflow.

In FreeRTOS (SentinelGrid's RTOS), each task gets its own stack. If you allocate too little stack for a task, it overflows and corrupts adjacent memory — causing mysterious crashes that look unrelated to the actual cause.

| Day | Block | Activity | Resource |
|-----|-------|----------|----------|
| 6 | MORNING | Read: CS50 Week 0 — "Computational Thinking" | cs50.harvard.edu/x |
| 6 | AFTERNOON | Practice: pythontutor.com — run a simple Python program with a function call. Watch the stack grow and shrink | pythontutor.com |
| 6 | EVENING | Document: How RAM vs Flash matters for SentinelGrid | GitHub |
| 7 | MORNING | Read: "Stack vs Heap" — cs50.harvard.edu/x Week 4 Memory section | cs50.harvard.edu/x |
| 7 | AFTERNOON | Practice: Write a Python recursive function without base case. Watch RecursionError (Python's stack overflow). Fix it. Understand why | Python REPL |
| 7 | EVENING | Document: "FreeRTOS gives each task its own stack. Stack overflow in the sensor task corrupts the FFT task's memory. This is why stack watermarks must be measured" | GitHub |

---

### DAYS 8–10 — How Systems Fail (Resilience Thinking)

**Concept First (Day 8)**

Every system will fail. The question is not whether but when and how. A well-designed system fails in a predictable, contained, recoverable way. A poorly designed system fails in a cascading, unpredictable, data-losing way.

**The Five Failure Modes You Must Know:**

1. **Process crash** — the program exits unexpectedly. Fix: watchdog that restarts it
2. **Network failure** — connection drops. Fix: retry with exponential backoff
3. **Database unavailable** — cannot read or write. Fix: cache + retry queue
4. **Dependency failure** — a service you call is down. Fix: circuit breaker + fallback
5. **Resource exhaustion** — out of memory, out of disk, out of connections. Fix: limits + monitoring

**Connection to All Projects:**

| Failure | InfraMesh Response | SentinelGrid Response | PulseGrid Response | MemCore Response |
|---------|-------------------|-----------------------|--------------------|-----------------|
| Network failure | SQS retains task until worker reconnects | Flash buffer stores telemetry offline | Kafka retains events | Queue fix suggestion locally |
| Process crash | Watchdog restarts worker | Hardware watchdog resets firmware | ECS restarts container | Restart agent |
| DB unavailable | Return 503, log alert | Continue local inference | Risk scoring from cache | Degrade to raw error display |
| Dependency failure | DLQ captures failed provisions | LoRa fallback for WiFi failure | Postmortem skips LLM step | Skip LLM, show raw context |

| Day | Block | Activity | Resource |
|-----|-------|----------|----------|
| 8 | MORNING | Read: Google SRE Book Chapter 3 "Embracing Risk" (free) | sre.google/sre-book/embracing-risk |
| 8 | AFTERNOON | Draw: On paper or excalidraw.com, the failure modes for InfraMesh. For each: what fails, what the user experiences, how the system recovers | excalidraw.com |
| 8 | EVENING | Document: `learning-journal/day-08-failure-modes.md` | GitHub |
| 9 | MORNING | Read: Netflix Tech Blog "5 Lessons from Chaos Engineering" | netflixtechblog.com |
| 9 | AFTERNOON | Design: Write `FAILURE_MODES.md` in the SentinelGrid repo. List 5 failure scenarios with recovery strategies | GitHub |
| 9 | EVENING | Read: One real postmortem from postmortems.com (a collection of real company postmortems) | postmortems.com |
| 10 | ALL DAY | REST AND REVIEW: Re-read Days 1–9. Update all documentation. Draw the master architecture for all four projects on excalidraw.com. Export and commit | excalidraw.com + GitHub |

---

### DAYS 11–14 — Systems Thinking and Architecture Patterns

**Concept First (Day 11): Synchronous vs Asynchronous**

Synchronous means: you ask for something and wait. The caller is blocked.
Asynchronous means: you ask for something, get an acknowledgment immediately, and the result arrives later. The caller continues.

InfraMesh uses asynchronous provisioning: the developer calls `POST /api/v1/services` and immediately gets back `{"status": "provisioning", "id": "abc123"}`. The actual provisioning (creating DNS records, configuring ALB) happens in the background via SQS + worker. The developer polls `GET /api/v1/services/abc123/status` until it says `complete`.

If InfraMesh was synchronous, the developer would wait 30 seconds with no response before getting the result. This violates the HTTP timeout limit and creates a terrible user experience.

**Concept First (Day 12): Queues and Workers**

A message queue is a buffer between a producer and a consumer. The producer puts messages in. The consumer takes messages out. They run at different speeds. If the producer is fast and the consumer is slow, messages accumulate in the queue — but nothing is lost.

```
PRODUCER (InfraMesh API)
    │ "provision service abc123"
    ▼
[SQS Queue]  ← messages wait here safely
    │ worker picks up
    ▼
CONSUMER (Provisioning Worker)
    │ creates DNS record
    │ creates ALB rule
    │ writes status to database
    ▼
DONE
```

**Concept First (Day 13): Databases and Why You Need Three Types**

Different data has different shapes. Using one database type for everything is like using a hammer for every job.

- **Relational (PostgreSQL):** Data with relationships. "Which services belong to which team?" "Which alerts are linked to which incidents?"
- **Time-series (TimescaleDB):** Data with timestamps. "What was the vibration level at 14:32:07?" Optimized for time-range queries.
- **Graph (Neo4j):** Data with complex relationships. "Which services does payment-service depend on, transitively?" Optimized for traversal.
- **Vector (ChromaDB):** Data expressed as embeddings. "Which past bugs are semantically similar to this new bug?" Optimized for similarity search.

**Concept First (Day 14): The Twelve-Factor App**

12factor.net defines how production applications should be designed. Every InfraMesh, PulseGrid, and MemCore service follows these principles. Read all 12 factors. The most important for you now:

- **III. Config:** Store config in environment variables, never in code. No passwords in source code.
- **XI. Logs:** Treat logs as event streams. Write to stdout, not to files.
- **XII. Processes:** Crash cleanly. Let the process manager restart. Do not hold state in memory.

| Day | Block | Activity | Resource |
|-----|-------|----------|----------|
| 11 | MORNING | Read: "Synchronous vs Asynchronous Programming" — realpython.com/async-io-python (first section only) | realpython.com |
| 11 | AFTERNOON | Draw: Two sequence diagrams — InfraMesh synchronous (bad) vs asynchronous (good) | excalidraw.com |
| 12 | MORNING | Read: AWS SQS documentation — "What is Amazon SQS?" | docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/welcome.html |
| 12 | AFTERNOON | Draw: The complete InfraMesh provisioning flow as a sequence diagram with SQS | excalidraw.com |
| 13 | MORNING | Read: "What is a time-series database?" — timescale.com/blog | timescale.com/blog/time-series-database |
| 13 | AFTERNOON | Research: Find one real-world use case for each of the 4 database types. Write in `learning-journal/day-13-databases.md` | GitHub |
| 14 | MORNING | Read: All 12 factors at 12factor.net | 12factor.net |
| 14 | AFTERNOON | For each of your 4 projects: write which 12-factor principles apply and how. Add to each project's `ARCHITECTURE.md` | GitHub |

**Phase 0 Completion Checkpoint:**

By Day 14, you must be able to answer these without looking anything up:
1. Explain how a DNS record creation in InfraMesh works from the moment a developer presses submit
2. Why does SentinelGrid use an asynchronous firmware OTA system instead of a synchronous one?
3. PulseGrid uses three database types. Name them and explain why each was chosen over a single database
4. A SentinelGrid node loses WiFi connection. What happens to its telemetry data?
5. Write the 12-factor principle that explains why InfraMesh never stores database passwords in source code

---

# PART 2 — PHASE 1: PROGRAMMING FOUNDATIONS
## Days 15–60 | Python Core + C Basics + First API

---

### WHY THIS PHASE EXISTS

Python is the primary language for all four projects: InfraMesh API, SentinelGrid gateway and ML pipeline, PulseGrid stream processor and risk model, MemCore vocabulary engine. C is the language for SentinelGrid firmware. You need both. This phase builds both from zero, always connecting each concept to where it appears in the projects.

**Phase 1 Architecture Target:** By Day 60 you will have a running FastAPI server for InfraMesh that accepts service registration requests, validates them, and stores them in PostgreSQL. This is the core of InfraMesh working end-to-end — no SQS yet, no AWS yet, just the foundation.

---

### WEEK 1 (Days 15–21): Python Basics

#### DAY 15 — Variables, Types, Operators

**Concept First**

A variable is a named container for a value. Python determines the type automatically. This is called dynamic typing.

Why types matter for your projects: Pydantic (used in all four FastAPI applications) enforces types. If a developer sends `"port": "8080"` (string) but InfraMesh expects `"port": 8080` (integer), Pydantic rejects the request before it reaches the database. Type enforcement prevents corrupt data.

```python
# InfraMesh service registration — types matter
service_name = "payment-service"    # str — must be a string
port = 8080                          # int — must be an integer
is_public = False                    # bool — must be true or false
health_check = "/health"             # str — must be a string
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: docs.python.org/3/tutorial/introduction.html (Chapter 3 — An Informal Introduction) | docs.python.org |
| AFTERNOON | Practice: HackerRank Python Easy — complete "Python If-Else", "Arithmetic Operators", "Python: Division" | hackerrank.com/domains/python |
| AFTERNOON | Build: In a new file `learning-journal/python/day15.py`, write 10 variables representing a SentinelGrid sensor reading: node_id (str), timestamp (str), vibration_rms (float), temperature_celsius (float), anomaly_score (float), battery_percent (int), wifi_rssi (int), is_anomaly (bool). Print each one | Python |
| EVENING | Document: `learning-journal/python/day15.md`. Explain each type you used and why. Which field should be a float vs int? | GitHub |

**Conceptual Test:**
A developer sends this to InfraMesh: `{"name": 42, "port": "eight-thousand-eighty", "public": "yes"}`. Which fields are wrong types? What should Pydantic do?

**Active Recall:**
1. What type should an anomaly score be? Why not int?
2. Why does SentinelGrid use float for sensor readings but int for port numbers?
3. What happens in Python when you add a string to an integer: `"port" + 8080`?

---

#### DAY 16 — Control Flow: If/Else and Loops

**Concept First**

Control flow determines which code runs. `if` runs code conditionally. `for` repeats code over a sequence. `while` repeats until a condition changes.

Every system you build has control flow at its core:
- InfraMesh worker: `for message in sqs_queue: process(message)`
- SentinelGrid gateway: `while True: msg = mqtt.receive(); process(msg)`
- PulseGrid risk scorer: `for pr_file in changed_files: if file in incident_history: risk += weight`

```python
# Simplified InfraMesh worker loop — control flow in production
for message in sqs_messages:
    if message['action'] == 'provision':
        create_dns_record(message['domain'])
        create_alb_rule(message['service'])
    elif message['action'] == 'deprovision':
        delete_dns_record(message['domain'])
    else:
        log_error(f"Unknown action: {message['action']}")
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: docs.python.org/3/tutorial/controlflow.html | docs.python.org |
| AFTERNOON | Practice: HackerRank — "Loops", "Print Function", "Write a function" | hackerrank.com/domains/python |
| AFTERNOON | Build: Write a Python script `day16-simulator.py` that simulates 10 SentinelGrid anomaly readings. For each reading: if anomaly_score > 0.8, print "CRITICAL ALERT: Machine needs immediate attention". If > 0.5, print "WARNING: Schedule maintenance". Otherwise print "OK". | Python |
| EVENING | Document: `learning-journal/python/day16.md`. Show your code. Write: "This control flow logic is exactly how SentinelGrid's stream processor categorizes incoming telemetry from Kinesis" | GitHub |

**Assignment:** Write a while loop that simulates a SentinelGrid node retrying an MQTT connection after failure. The loop tries every 1 second, then 2 seconds, then 4 seconds, then 8 seconds (exponential backoff), up to a maximum of 60 seconds. Print each retry attempt.

---

#### DAY 17 — Functions

**Concept First**

A function is a named, reusable block of code that takes inputs (parameters) and produces output (return value). Good functions do one thing well.

The most important principle for your projects: **Single Responsibility**. One function, one job. This is not a style preference — it is what makes your code debuggable. When SentinelGrid's signal processing pipeline fails, you need to know exactly which function failed and why. If one function does FFT + feature extraction + model inference + MQTT publish, you cannot isolate the failure.

```python
# BAD — one function doing everything
def process_sensor_data(raw_samples, mqtt_client):
    fft = numpy.fft.fft(raw_samples)
    features = extract_features(fft)
    score = model.predict(features)
    mqtt_client.publish(f"sentinel/node/{id}/telemetry", score)

# GOOD — one function, one job
def compute_fft(raw_samples: list) -> list:
    return numpy.fft.fft(raw_samples)

def extract_features(fft_result: list) -> list:
    return [compute_rms(fft_result), compute_kurtosis(fft_result)]

def score_anomaly(features: list) -> float:
    return model.predict([features])[0]

def publish_telemetry(node_id: str, score: float, mqtt_client) -> None:
    mqtt_client.publish(f"sentinel/node/{node_id}/telemetry", score)
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: docs.python.org/3/tutorial/controlflow.html#defining-functions | docs.python.org |
| AFTERNOON | Practice: Exercism Python track — complete "Hello World", "Two Fer", "Resistor Color" | exercism.org/tracks/python |
| AFTERNOON | Build: Write 4 functions for InfraMesh: `validate_service_name(name: str) -> bool`, `validate_port(port: int) -> bool`, `validate_domain(domain: str) -> bool`, `validate_service_request(name, port, domain) -> dict` that returns `{"valid": True/False, "errors": []}` | Python |
| EVENING | Document: Show your functions. Explain: "These validation functions are what Pydantic calls internally in InfraMesh's FastAPI endpoint before processing a registration request" | GitHub |

---

#### DAY 18 — Lists and Dictionaries

**Concept First**

A list is an ordered collection of items. A dictionary is a collection of key-value pairs.

In your projects, almost all data is either a list (many readings, many services, many events) or a dict (one structured record):

```python
# SentinelGrid telemetry reading — a dict
reading = {
    "node_id": "node-042",
    "timestamp": "2024-01-15T14:32:07Z",
    "vibration_rms": 0.82,
    "anomaly_score": 0.91
}

# Fleet health report — a list of dicts
fleet_health = [
    {"node_id": "node-001", "status": "healthy", "battery": 87},
    {"node_id": "node-042", "status": "critical", "battery": 23},
    {"node_id": "node-099", "status": "offline", "battery": None}
]
```

List comprehensions are the most important Python pattern for data processing:

```python
# Filter: only critical nodes
critical_nodes = [n for n in fleet_health if n["status"] == "critical"]

# Transform: extract all node IDs
node_ids = [n["node_id"] for n in fleet_health]

# Both: node IDs of offline nodes with battery < 20
problem_nodes = [n["node_id"] for n in fleet_health
                 if n["status"] == "offline" and
                 n["battery"] is not None and
                 n["battery"] < 20]
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: realpython.com/python-lists-tuples and realpython.com/python-dicts | realpython.com |
| AFTERNOON | Practice: HackerRank — "List Comprehensions", "Find the Runner-Up Score", "Nested Lists" | hackerrank.com/domains/python |
| AFTERNOON | Build: Create a Python script with a list of 20 simulated SentinelGrid node readings (dicts). Write 5 list comprehensions: (1) nodes with anomaly_score > 0.7, (2) average anomaly score, (3) node IDs of critical nodes, (4) readings from the last hour (simulate with timestamps), (5) sorted by anomaly_score descending | Python + GitHub |
| EVENING | Document: Show all 5 comprehensions. Write: "This is exactly how PulseGrid's Kafka stream processor filters and transforms incoming events before writing to TimescaleDB" | GitHub |

**Debugging Exercise:**
Given this code, find the bug:
```python
services = [{"name": "payment", "port": 8080}, {"name": "auth", "port": 8081}]
for service in services:
    if service["name"] == "payment":
        service["status"] = "active"
print([s for s in services if s["status"] == "active"])
```
What happens? Why? How do you fix it?

---

#### DAYS 19–21: Error Handling, Modules, File I/O

| Day | Core Concept | Production Connection | Practice Site | Build |
|-----|-------------|----------------------|---------------|-------|
| 19 | try/except/finally, custom exceptions, context managers | "Every database call, every API call, every file read can fail. InfraMesh wraps every AWS API call in try/except. SQS throttling → catch → backoff → retry" | exercism.org (Grains, Hamming) | Custom `InfraMeshError` and `SentinelGridTelemetryError` exception classes |
| 20 | Python modules, import system, `__init__.py`, package structure | "InfraMesh is a Python package with: `inframesh/api/`, `inframesh/worker/`, `inframesh/models/`. Import structure determines testability" | realpython.com/python-modules | Create the InfraMesh Python package structure. Empty files but correct structure |
| 21 | File I/O, JSON read/write, logging module | "Every project writes structured JSON logs. The Python `logging` module with a JSON formatter is how all projects log to stdout (12-factor principle XI)" | docs.python.org/3/library/logging | Implement structured JSON logging in InfraMesh: `{"timestamp": "...", "level": "INFO", "service": "inframesh", "event": "service_registered", "service_id": "abc123"}` |

---

### WEEK 2 (Days 22–28): Python Intermediate + First API

#### DAY 22 — Python Classes and OOP

**Concept First**

A class is a blueprint for objects. An object is an instance of a class. Classes bundle data (attributes) and behavior (methods) together.

Why classes matter for your projects: every major component in all four projects is a class. `ServiceRegistry`, `ProvisioningWorker`, `MQTTClient`, `AnomalyDetector`, `RiskScorer`, `MemoryEngine` — these are all classes because they combine data with the operations on that data.

```python
class ServiceRegistry:
    """Manages registered services in InfraMesh.
    
    This class represents the core domain model.
    It knows about services and what can be done with them.
    """
    
    def __init__(self, db_connection):
        self.db = db_connection
        self.services = {}  # in-memory cache
    
    def register(self, name: str, port: int, domain: str) -> dict:
        """Register a new service and return its record."""
        service = {
            "id": self._generate_id(),
            "name": name,
            "port": port,
            "domain": domain,
            "status": "pending",
            "created_at": datetime.now().isoformat()
        }
        self.db.insert("services", service)
        return service
    
    def get_status(self, service_id: str) -> str:
        """Return the current provisioning status."""
        service = self.db.find("services", service_id)
        if not service:
            raise ServiceNotFoundError(service_id)
        return service["status"]
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: realpython.com/python3-object-oriented-programming | realpython.com |
| AFTERNOON | Practice: HackerRank OOP challenges: "Class 1 - Dealing with Complex Numbers", "Class 2 - Find the Torsional Angle" | hackerrank.com/domains/python |
| AFTERNOON | Build: Complete `ServiceRegistry` class with: `__init__`, `register`, `get_status`, `list_services`, `deregister`. Use a Python dict as the "database" for now | Python + GitHub |
| EVENING | Document: Draw a class diagram for InfraMesh's main classes: `ServiceRegistry`, `ProvisioningWorker`, `HealthChecker`. Show their relationships | excalidraw.com + GitHub |

---

#### DAY 23 — Async Python (asyncio)

**Concept First**

Synchronous Python handles one thing at a time. If it takes 200ms to call the AWS Route53 API, Python waits 200ms and does nothing else.

Asynchronous Python handles many things concurrently. While waiting for the Route53 API response, it can handle other requests. This is critical for InfraMesh: if 100 developers register services simultaneously, synchronous Python would process them one by one (taking 100 × 200ms = 20 seconds). Async Python processes all 100 concurrently (taking ~200ms total).

```python
import asyncio
import httpx  # async HTTP client

# SYNCHRONOUS (slow)
def provision_all(services):
    for service in services:
        create_dns_record(service)  # waits 200ms each

# ASYNCHRONOUS (fast)
async def provision_all(services):
    tasks = [create_dns_record(service) for service in services]
    await asyncio.gather(*tasks)  # all 100 run concurrently

async def create_dns_record(service):
    async with httpx.AsyncClient() as client:
        await client.post("https://route53.amazonaws.com/...", ...)
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: realpython.com/async-io-python (first two sections) | realpython.com |
| AFTERNOON | Practice: Write an async Python script that simulates 10 concurrent DNS record creations (use `asyncio.sleep(0.2)` to simulate 200ms API call). Measure how long synchronous vs async takes | Python |
| AFTERNOON | Install FastAPI: `pip install fastapi uvicorn`. Run the FastAPI tutorial "First Steps". Note that FastAPI is async by default | fastapi.tiangolo.com |
| EVENING | Document: "InfraMesh API uses async FastAPI. Without async, 100 concurrent registrations would take 100× longer. With async, they all run concurrently. Measured difference: sync 20 seconds, async 0.3 seconds" | GitHub |

---

#### DAY 24 — FastAPI Fundamentals

**Concept First**

FastAPI is a Python web framework. It takes an HTTP request, runs your Python function, and returns an HTTP response. It automatically generates API documentation (Swagger UI) from your code. It validates request data using Pydantic.

FastAPI is the front door for all four projects:
- InfraMesh: developers call FastAPI to register services
- SentinelGrid: engineers call FastAPI to manage devices and push OTA commands
- PulseGrid: GitHub/PagerDuty/Sentry send webhooks to FastAPI
- MemCore: developers call FastAPI to get fix suggestions

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI(title="InfraMesh", version="1.0.0")

class ServiceRegistration(BaseModel):
    name: str
    port: int
    domain: str
    public: bool = False
    health_check: str = "/health"

@app.post("/api/v1/services", status_code=201)
async def register_service(request: ServiceRegistration):
    """Register a new service for automatic infrastructure provisioning."""
    # Pydantic already validated: name is str, port is int, etc.
    service_id = service_registry.register(
        name=request.name,
        port=request.port,
        domain=request.domain
    )
    return {"service_id": service_id, "status": "provisioning"}
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Complete: fastapi.tiangolo.com tutorial — "First Steps", "Path Parameters", "Query Parameters", "Request Body" | fastapi.tiangolo.com |
| AFTERNOON | Build: Create `inframesh/api/main.py` with 4 endpoints: `POST /api/v1/services` (register), `GET /api/v1/services` (list), `GET /api/v1/services/{id}` (get status), `DELETE /api/v1/services/{id}` (deregister). Use in-memory dict as storage for now | Python + GitHub |
| AFTERNOON | Test: Run `uvicorn main:app --reload`. Open `http://localhost:8000/docs`. Test all 4 endpoints from Swagger UI | Swagger UI |
| EVENING | Document: `inframesh/API.md`. Document each endpoint with: URL, method, request body schema, response schema, example request, example response | GitHub |

---

#### DAYS 25–28: Pydantic, Authentication, Testing

| Day | Concept | Why It Matters | Build |
|-----|---------|---------------|-------|
| 25 | **Pydantic models** — validators, nested models, custom validators | "Pydantic is the gatekeeper. It rejects malformed requests before they touch the database. A port number of -1 or 99999 would corrupt downstream provisioning" | Add Pydantic validators to InfraMesh: port must be 1-65535, name must match `^[a-z][a-z0-9-]*$`, domain must be valid FQDN |
| 26 | **JWT Authentication** — what a JWT is, claims, expiry, signing | "InfraMesh uses JWT to know which team is making the request. The JWT claim includes `team_id`, used for PostgreSQL row-level security. A developer from team-payments cannot see team-analytics services" | Add JWT auth to all InfraMesh endpoints using `python-jose`. Protected endpoints return 401 without valid token |
| 27 | **HTTP status codes and error responses** — consistent error format | "A 422 from InfraMesh means Pydantic rejected the request. A 409 means the service already exists. A 202 means provisioning started but not complete. Consistent codes let clients handle errors programmatically" | Add proper status codes and structured error responses: `{"error": "SERVICE_ALREADY_EXISTS", "message": "A service named 'payment' already exists", "service_id": "abc123"}` |
| 28 | **pytest and API testing** — test-driven confidence | "Tests are the safety net. Before deploying InfraMesh to production, the test suite must pass. GitHub Actions runs tests on every push. A failing test blocks the deployment" | Write 15 pytest tests for InfraMesh API: test valid registration, test duplicate name rejection, test invalid port, test unauthorized access, test service not found |

---

### WEEK 3–4 (Days 29–42): Databases

#### DAY 29 — What Databases Are and Why We Need Them

**Concept First**

A database stores data persistently. When your Python process restarts, in-memory dicts (what you have been using) are lost. Databases survive restarts.

**Choosing the Right Database:**

| If Your Data Looks Like | Use | Why |
|------------------------|-----|-----|
| Tables with relationships ("services belong to teams") | PostgreSQL | SQL handles relationships efficiently |
| Time-stamped measurements ("vibration was 0.82g at 14:32:07") | TimescaleDB | Optimized for time-range queries |
| Relationships between entities ("service A calls service B") | Neo4j | Graph traversal is native |
| Text/code that needs semantic search ("find bugs similar to this one") | ChromaDB | Vector similarity search |
| Simple key-value (session data, rate limit counters) | Redis | Microsecond latency |

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: "What is a relational database?" — postgresql.org/docs/current/intro-whatis.html | postgresql.org |
| AFTERNOON | Install: PostgreSQL locally. Connect with `psql`. Create a database called `inframesh_dev`. Create a table `services` with columns: `id UUID PRIMARY KEY, name VARCHAR(255), port INTEGER, domain VARCHAR(255), status VARCHAR(50), created_at TIMESTAMP` | postgresql.org docs |
| AFTERNOON | Practice: sqlzoo.net — complete "SELECT basics" and "SELECT from WORLD" | sqlzoo.net |
| EVENING | Document: `inframesh/DATABASE.md`. Write the `services` table schema with comments explaining why each column exists and what type it is | GitHub |

---

#### DAY 30 — SQL Fundamentals

**Concept First**

SQL is the language for talking to relational databases. Four operations cover everything:
- `SELECT` — read data
- `INSERT` — add data
- `UPDATE` — change data
- `DELETE` — remove data

```sql
-- InfraMesh: register a new service
INSERT INTO services (id, name, port, domain, status, created_at)
VALUES ('abc123', 'payment-service', 8080, 'payment.company.com', 'pending', NOW());

-- InfraMesh: check provisioning status
SELECT status, created_at FROM services WHERE id = 'abc123';

-- InfraMesh: list all services for a team
SELECT s.name, s.status, s.domain
FROM services s
JOIN teams t ON s.team_id = t.id
WHERE t.name = 'payments'
ORDER BY s.created_at DESC;

-- InfraMesh: update status after provisioning
UPDATE services SET status = 'active' WHERE id = 'abc123';
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Practice: sqlzoo.net — complete "SELECT from WORLD", "SELECT within SELECT" | sqlzoo.net |
| AFTERNOON | Practice: HackerRank SQL — "Revising the Select Query", "Select All", "Select By ID" | hackerrank.com/domains/sql |
| AFTERNOON | Build: Write 10 SQL queries for InfraMesh. Save in `inframesh/docs/queries.sql`. Each with a comment explaining what it does and when InfraMesh uses it | PostgreSQL + GitHub |
| EVENING | Document: `learning-journal/day-30-sql.md`. Explain the difference between WHERE and HAVING, and why JOIN matters for InfraMesh's team-based service listing | GitHub |

**Active Recall Questions:**
1. InfraMesh wants to find all services that have been in "pending" status for more than 5 minutes (stuck provisioning). Write the SQL query.
2. PulseGrid wants to count incidents per service in the last 30 days, sorted by incident count. Write the SQL query.
3. What is the difference between `DELETE FROM services` and `DROP TABLE services`?

---

#### DAYS 31–35: SQL Advanced + PostgreSQL + SQLAlchemy

| Day | Concept | Build | Practice Site |
|-----|---------|-------|---------------|
| 31 | **JOINs** (INNER, LEFT, RIGHT) — combining tables | InfraMesh query: services + teams + health_checks in one query | sqlzoo.net "The JOIN operation" |
| 32 | **Indexes** — why queries are slow and how to fix them | Add index on `services.name` and `services.team_id`. Measure EXPLAIN ANALYZE before/after | use-the-index-luke.com |
| 33 | **Transactions** — ACID properties, BEGIN/COMMIT/ROLLBACK | InfraMesh: registering service + creating DNS record must be atomic. If DNS fails, service must not be registered | postgresql.org/docs transactions |
| 34 | **SQLAlchemy async** — ORM connecting FastAPI to PostgreSQL | Replace InfraMesh's in-memory dict with real PostgreSQL via SQLAlchemy async ORM | sqlalchemy.org docs |
| 35 | **TimescaleDB** — time-series extension | Install TimescaleDB. Create `telemetry` hypertable for SentinelGrid. Add 1000 simulated rows. Query 24-hour window | docs.timescale.com |

---

### WEEKS 5–6 (Days 43–60): C Basics + Mini-Project Completion

#### DAY 43 — Why C Exists and What It Is

**Concept First**

C is 50 years old. Every operating system, every microcontroller, most databases have C at their core. Python is elegant but runs on a virtual machine that uses C internally. JavaScript engines are written in C++. Your ESP32-S3's firmware must be in C (or Rust) because there is no Python runtime that fits in 512KB of RAM.

C gives you direct control over hardware registers, memory addresses, and CPU timing. This control is both C's superpower (you can talk directly to the ADXL355 over SPI) and its danger (you can accidentally overwrite memory you don't own).

```c
/* Python version — convenient, slow, needs runtime */
samples = [0.82, 0.79, 0.91, 0.88]
rms = (sum(x**2 for x in samples) / len(samples)) ** 0.5

/* C version — explicit, fast, no runtime needed */
float compute_rms(float* samples, int count) {
    float sum_squares = 0.0f;
    for (int i = 0; i < count; i++) {
        sum_squares += samples[i] * samples[i];
    }
    return sqrtf(sum_squares / count);
}
/* This exact function runs on the ESP32-S3 in SentinelGrid */
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: CS50 Week 1 lecture notes | cs50.harvard.edu/x (Week 1) |
| AFTERNOON | Practice: CS50 Problem Set 1 — "Hello" (introductory C program) | cs50.harvard.edu/x |
| AFTERNOON | Compile your first C program with `gcc` on Linux. Understand the compilation process: source → assembly → binary | gcc on terminal |
| EVENING | Document: "C is compiled before running. Python is interpreted at runtime. Compiled code runs 10-100x faster. This is why SentinelGrid's FFT runs in C (12ms) rather than Python (which would be 50ms+ and require a Python runtime the ESP32 cannot run)" | GitHub |

---

#### DAYS 44–50: C Intermediate

| Day | Concept | Embedded Connection | Build |
|-----|---------|---------------------|-------|
| 44 | **Pointers** — memory addresses, dereferencing, pointer arithmetic | "DMA transfers use pointer arithmetic: `uint8_t* rx_buf = &buffer[0]; HAL_SPI_Receive(&hspi1, rx_buf, 6, 100)`" | Write C functions using pointers. compute_rms with float* instead of array |
| 45 | **Structs** — grouping related data | "ADXL355 status register is a struct: `struct adxl355_status { uint8_t data_ready: 1; uint8_t fifo_full: 1; uint8_t reserved: 6; }`" | Define structs for SentinelNode sensor readings |
| 46 | **Volatile keyword** — preventing compiler optimization of shared variables | "ISR sets `volatile bool data_ready = true`. Without volatile, compiler optimizes away the check in the main loop. Device never reads sensor data" | Demonstrate volatile necessity with a simple ISR simulation |
| 47 | **Memory layout** — stack, heap, BSS, text segments | "Static buffer `static float sample_buffer[1024]` in BSS. Stack frame for each FreeRTOS task. No malloc in production firmware" | Analyze memory usage of a simple C program with `size` command |
| 48 | **Bit manipulation** — AND, OR, XOR, shift for hardware registers | "Set GPIO pin high: `GPIOA->ODR |= (1 << 5)`. Clear: `GPIOA->ODR &= ~(1 << 5)`. Read: `(GPIOA->IDR >> 5) & 1`" | Write C macros for common bit operations used in sensor drivers |
| 49 | **C compilation and linking** — Makefile basics | "ESP-IDF uses CMake. Understanding build system means understanding how your firmware gets from source to binary on the chip" | Write a Makefile that compiles multiple C files |
| 50 | **Review + Mini-Project** | Build: A C program that simulates 1000 vibration samples, computes RMS, kurtosis, and a simple anomaly threshold. This is the CPU-side of SentinelGrid's signal processing | All above |

---

#### DAYS 51–60: Phase 1 Mini-Project — InfraMesh v0.1

**What You Build in Days 51–60:**

InfraMesh v0.1 — a working service registry with:
- FastAPI endpoints (register, list, status, delete)
- PostgreSQL storage via SQLAlchemy
- Pydantic validation
- JWT authentication
- pytest test suite (80%+ coverage)
- Swagger documentation
- Docker container
- docker-compose with FastAPI + PostgreSQL

| Day | Task | What You Produce |
|-----|------|-----------------|
| 51 | Project setup: Poetry, project structure, environment variables | `inframesh/` package structure, `.env.example` |
| 52 | Database models: SQLAlchemy models for `Service`, `Team` | `inframesh/models/service.py` |
| 53 | CRUD operations: create, read, update, delete service | `inframesh/crud/service.py` |
| 54 | API endpoints: all 4 endpoints connected to database | `inframesh/api/routes/services.py` |
| 55 | Authentication: JWT middleware protecting endpoints | `inframesh/api/auth.py` |
| 56 | Error handling: custom exceptions, consistent error responses | `inframesh/exceptions.py` |
| 57 | Tests: pytest with test database | `tests/test_services.py` (15 tests) |
| 58 | Docker: Dockerfile + docker-compose.yml | `Dockerfile`, `docker-compose.yml` |
| 59 | Documentation: API.md, DATABASE.md, RUNNING.md | `docs/` folder complete |
| 60 | Review + Deploy: Run full test suite. Deploy to a free cloud (Railway.app free tier). Get a public URL | Running service at public URL |

**Phase 1 Completion Assessment:**

Answer these without looking up:
1. What is the difference between `async def` and `def` in FastAPI?
2. A developer sends `{"name": "my service", "port": -1}`. Trace exactly what happens in InfraMesh from HTTP request to error response.
3. Your InfraMesh database has 10,000 services. The `GET /api/v1/services` endpoint is slow. What do you check first?
4. Write the SQL query to find all services registered in the last 24 hours that are still in "pending" status.
5. Describe the InfraMesh v0.1 architecture in one paragraph, naming every component and how they connect.

**Portfolio Action After Day 60:**
- InfraMesh v0.1 is live at a public URL
- GitHub has 45+ commits with clear messages
- README has a demo GIF (record with Loom or OBS)
- `API.md` has Swagger documentation link
- `ARCHITECTURE.md` has a system diagram

---

# PART 3 — PHASE 2: ASYNC SYSTEMS AND MESSAGING
## Days 61–90 | SQS, MQTT, Queues, Real InfraMesh

---

### WHY THIS PHASE EXISTS

InfraMesh v0.1 processes provisioning synchronously — the API waits while DNS records are created. This takes 30 seconds and often times out. Phase 2 adds the asynchronous queue-worker pattern that makes InfraMesh production-grade.

SentinelGrid needs MQTT to move telemetry from nodes to the gateway. PulseGrid needs Kafka to process engineering events at high volume. This phase teaches all message-passing systems with the same mental model: **producer puts messages in, consumer takes messages out, they run independently.**

---

### DAY 61 — Message Queues: The Mental Model

**Concept First**

Imagine a restaurant. The waiter takes your order (producer) and gives it to the kitchen (queue). The chef cooks it (consumer). The waiter does not stand and wait for the chef — they take the next table's order. The kitchen processes orders at its own pace.

This is exactly the InfraMesh architecture:
- Waiter = FastAPI endpoint (producer — takes orders from developers)
- Kitchen = SQS Queue (stores tasks safely)
- Chef = Provisioning Worker (consumer — executes provisioning tasks)

**Why Queues Are Critical:**
1. **Resilience:** If the worker crashes, messages stay in SQS. When it restarts, it continues from where it left off. No data loss.
2. **Decoupling:** The API and worker can be scaled independently. If provisioning is slow, add more workers — do not change the API.
3. **Rate limiting:** If 1000 developers register services simultaneously, SQS absorbs the burst. Workers process at a sustainable rate.

```
WITHOUT QUEUE (synchronous):
Developer waits 30 seconds. Server might timeout. Experience is terrible.

WITH QUEUE (asynchronous):
Developer gets response in 50ms: {"status": "provisioning", "id": "abc123"}
Worker creates DNS in background.
Developer polls every 2 seconds until status is "active".
```

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: AWS SQS "What is Amazon SQS?" | docs.aws.amazon.com/AWSSimpleQueueService |
| MORNING | Read: "Message Queues Explained" — cloudamqp.com/blog/what-is-message-queuing.html | cloudamqp.com/blog |
| AFTERNOON | Practice with LocalStack (free AWS simulation): `pip install localstack`. Start it. Create an SQS queue. Publish 5 messages. Consume them in Python | localstack.cloud |
| AFTERNOON | Build: InfraMesh provisioning worker — Python script that reads from SQS and prints "Provisioning service: [name]" | Python + LocalStack |
| EVENING | Document: Draw the complete InfraMesh async flow. "The API responds in 50ms. The worker processes in 30 seconds. The developer polls for status. No timeout. No blocking." | GitHub |

---

#### DAY 62 — Dead Letter Queues and Retry Logic

**Concept First**

What happens if the worker fails while processing a message? Without careful design, the message is lost. With a Dead Letter Queue (DLQ), failed messages are moved to a secondary queue after N failed attempts, where they can be inspected and replayed.

This is the difference between amateur and professional queue design:
- Amateur: message fails → gone forever → provisioning silently failed → developer never knows
- Professional: message fails 3× → moved to DLQ → alert fires → engineer inspects → replays when fixed

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: AWS SQS Dead Letter Queues documentation | docs.aws.amazon.com/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-dead-letter-queues |
| AFTERNOON | Build: Add DLQ to InfraMesh. Configure: max_receive_count=3. When worker fails (simulate with `raise Exception`), verify message goes to DLQ after 3 attempts. Write a DLQ monitor that alerts when DLQ depth > 0 | LocalStack + Python |
| AFTERNOON | Add exponential backoff to worker retry: 1s, 2s, 4s, 8s, max 60s | Python |
| EVENING | Document: `inframesh/ARCHITECTURE.md` — add DLQ design. Write: "A provisioning task that fails 3 times goes to the DLQ. This means zero silent failures. Every failure is visible and recoverable" | GitHub |

**Debugging Exercise:**
The InfraMesh DLQ has 47 messages. What do you do? Write a step-by-step investigation procedure.

---

#### DAYS 63–70: MQTT for SentinelGrid

| Day | Concept | Why | Build |
|-----|---------|-----|-------|
| 63 | **MQTT fundamentals** — publish/subscribe, broker, topics, client | "MQTT is designed for constrained devices with unreliable networks. HTTP would require the sensor to maintain a persistent connection. MQTT uses a broker that routes messages" | Install Mosquitto locally. Publish from Python. Subscribe in another terminal |
| 64 | **MQTT QoS levels** — 0 (fire and forget), 1 (at least once), 2 (exactly once) | "QoS 0 lost 2.3% of telemetry messages in our factory (unreliable WiFi). QoS 1 dropped 0%. SentinelGrid uses QoS 1 for telemetry" | Test QoS 0 vs 1 under simulated network interruption with Mosquitto |
| 65 | **MQTT topic design** — hierarchy, wildcards, pattern design | "Poor topic design makes filtering impossible. Good design: `sentinel/node/{id}/telemetry`. Subscribe with wildcard: `sentinel/node/+/telemetry` receives all nodes" | Design complete SentinelGrid topic hierarchy. Document in IOT_PROTOCOLS.md |
| 66 | **MQTT with TLS** — secure communication | "Without TLS, any device on the network can subscribe to all sensor data and inject fake readings. With TLS + client certificates, only authenticated SentinelNodes can publish" | Configure Mosquitto with self-signed TLS. Test rejected connection without certificate |
| 67 | **Store-and-forward pattern** — offline buffering | "SentinelGrid nodes in factories lose WiFi for hours. Without buffering, this data is lost during outages. The node writes to local flash, delivers on reconnect" | Simulate: disconnect broker, publish 100 messages (buffered), reconnect, verify all 100 delivered in order |
| 68 | **MQTT Python client** — paho-mqtt library | Python gateway that receives all node telemetry and writes to InfluxDB | SentinelGrid gateway: subscribe to `sentinel/node/+/telemetry`, parse JSON, write to local InfluxDB |
| 69 | **MQTT at scale** — broker capacity, multiple topics | "One Mosquitto instance handles ~10,000 simultaneous connections. At 200 nodes per facility × 50 facilities = 10,000 nodes. Need broker clustering" | Load test: Python script simulating 200 nodes publishing simultaneously. Measure broker CPU |
| 70 | **Review + Document** | All MQTT work | `IOT_PROTOCOLS.md` with complete MQTT architecture for SentinelGrid |

---

#### DAYS 71–80: Kafka for PulseGrid

**Why Kafka (not SQS or MQTT) for PulseGrid?**

PulseGrid needs to process 10,000+ engineering events per minute from multiple sources. Kafka provides three things that SQS and MQTT do not:
1. **Replay:** Kafka retains messages for 7 days. PulseGrid can reprocess past events when the risk model is retrained
2. **Multiple consumers:** Both the risk scorer and the dependency graph updater can consume the same GitHub event independently
3. **High throughput:** Kafka handles millions of messages per second vs SQS's thousands

| Day | Concept | Build |
|-----|---------|-------|
| 71 | Kafka fundamentals: topics, partitions, offsets, consumer groups | Install Kafka locally (Docker: `docker-compose -f kafka-compose.yml up`). Create 3 topics. Produce 100 messages. Consume in Python |
| 72 | Kafka partitioning: why and how | Create PulseGrid topic `events.github` with 6 partitions. Understand: all events from org-A go to partition 2 (consistent hashing on org_id) |
| 73 | Kafka consumer groups: parallel processing | Two Python consumers in the same group share the 6 partitions. Each consumer handles 3. Double consumers = double throughput |
| 74 | Kafka in Python: confluent-kafka-python | PulseGrid GitHub event consumer: receive PR event, parse, extract risk features, write to TimescaleDB |
| 75 | Kafka offset management: at-least-once delivery | Commit offset only after successful processing. If processing fails, event is reprocessed. Understand idempotency |
| 76 | Kafka dead letter topic: same as SQS DLQ | Failed events (unparseable JSON, unknown event type) → `events.dead-letter`. Alert when dead-letter topic grows |
| 77 | Kafka vs SQS vs MQTT: when to use each | Write comparison document. "SQS for InfraMesh (simple, managed, exactly what we need). Kafka for PulseGrid (replay, multiple consumers, high volume). MQTT for SentinelGrid (designed for IoT, QoS for unreliable networks)" |
| 78 | Event schema design: Avro/JSON for PulseGrid events | Design JSON schema for all PulseGrid event types: GitHub PR event, PagerDuty incident event, Sentry error event |
| 79 | Stream processing basics: filtering, transforming events in flight | Python Kafka consumer that enriches GitHub PR events with historical incident data before writing to TimescaleDB |
| 80 | Phase 2 Mini-Project: InfraMesh v0.2 | Add SQS provisioning queue to InfraMesh v0.1. API now returns immediately. Worker polls SQS. Status polling works end-to-end |

---

#### DAYS 81–90: Redis + Phase 2 Integration

| Day | Concept | Build |
|-----|---------|-------|
| 81 | Redis fundamentals: strings, hashes, lists, sets, sorted sets | Install Redis. Store InfraMesh service status in Redis hash. Retrieve in <1ms |
| 82 | Redis as cache: TTL, cache invalidation | Cache InfraMesh service list in Redis with 30s TTL. Reduces database queries from 100/minute to 2/minute |
| 83 | Redis as rate limiter: INCR + EXPIRE pattern | InfraMesh rate limiting: 10 registrations per minute per team. Redis INCR with 60s EXPIRE |
| 84 | Redis pub/sub: real-time notifications | When provisioning completes, worker publishes to Redis channel. FastAPI WebSocket endpoint pushes to browser |
| 85 | InfluxDB for SentinelGrid gateway | Install InfluxDB. Write SentinelGrid telemetry from MQTT gateway. Query last 1 hour of readings from one node |
| 86 | Grafana fundamentals: data sources, panels, dashboards | Connect Grafana to InfluxDB. Create SentinelGrid fleet health dashboard: node count, average anomaly score, offline nodes |
| 87 | Docker Compose for full stack | `docker-compose.yml` that starts: FastAPI + PostgreSQL + Redis + Mosquitto + InfluxDB + Grafana. One command: full stack |
| 88 | Environment variables and secrets: `.env`, Docker secrets | Extract all hardcoded values to `.env`. Add `.env.example`. Add to `.gitignore`. Add validation that all required env vars exist at startup |
| 89 | Integration testing: test the full stack | pytest tests that start the full docker-compose stack and test end-to-end: registration → SQS → worker → database → status check |
| 90 | Phase 2 Documentation and Assessment | Complete all docs. Phase 2 assessment questions |

**Phase 2 Completion Assessment:**

1. A message fails processing in InfraMesh's SQS worker. What happens after 1 failure, 2 failures, 3 failures?
2. SentinelGrid has 200 nodes publishing telemetry simultaneously to Mosquitto. The broker CPU spikes to 95%. What are three possible causes and fixes?
3. PulseGrid receives 10,000 GitHub events simultaneously (a large org has a deployment wave). Kafka has 6 partitions and 2 consumers. How many events does each consumer handle?
4. InfraMesh's `GET /api/v1/services` is called 1000 times per minute. Without Redis, this hits PostgreSQL 1000 times. With Redis cache (30s TTL), how many PostgreSQL queries per minute?
5. What is the difference between MQTT QoS 0, 1, and 2? Which does SentinelGrid use and why?

------

# PART 4 — PHASE 3: CLOUD, DEVOPS, AND INFRASTRUCTURE
## Days 91–150 | AWS, Docker, Terraform, CI/CD

---

### WHY THIS PHASE EXISTS

Code that only runs on your laptop is a hobby project. Code that runs reliably for thousands of users, survives hardware failures, scales to meet demand, and updates without downtime is engineering. Phase 3 teaches you how to take everything built in Phases 1–2 and deploy it to production.

**The Mental Model for This Phase:**
Every component you deploy in the cloud is a container. Every container needs infrastructure (compute, network, storage). Infrastructure is described as code (Terraform). Code is tested and deployed automatically (CI/CD). Everything is observed (CloudWatch, Grafana).

---

### DAYS 91–100: Docker and Containerization

#### DAY 91 — What Docker Is and Why It Exists

**Concept First**

"It works on my machine" is the classic developer excuse. It works because your machine has Python 3.11, specific packages, specific environment variables, and specific OS libraries. The production server has Python 3.9, different packages, and missing libraries. The code breaks.

Docker solves this by packaging the application AND its entire runtime environment into one portable unit called a container. The container runs identically on your Mac, your colleague's Windows laptop, and AWS EC2.

```dockerfile
# Dockerfile for InfraMesh API
# This is the recipe for building the container

FROM python:3.11-slim          # Start with Python 3.11 on Linux
WORKDIR /app                   # Set working directory
COPY pyproject.toml .          # Copy dependency list
RUN pip install -e .           # Install dependencies
COPY . .                       # Copy application code
EXPOSE 8080                    # Document the port
CMD ["uvicorn", "inframesh.api.main:app", "--host", "0.0.0.0", "--port", "8080"]
```

**Why All Four Projects Use Docker:**
- InfraMesh: 3 Docker containers — API, worker, and a migration runner
- SentinelGrid: Gateway Python pipeline in Docker. Cloud services in Docker
- PulseGrid: 6 containers — API, Kafka processor, risk scorer, postmortem generator, React frontend, Neo4j
- MemCore: SDK itself is a Python package, but demo environment is Docker

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: docs.docker.com/get-started — "What is Docker?" and "How Docker works" | docs.docker.com |
| AFTERNOON | Practice: play-with-docker.com — free browser-based Docker environment. Complete the "Alpine" tutorial | play-with-docker.com |
| AFTERNOON | Build: Write Dockerfile for InfraMesh API. Build it: `docker build -t inframesh-api .`. Run it: `docker run -p 8080:8080 inframesh-api`. Test with curl | Docker + local |
| EVENING | Document: `inframesh/DOCKER.md`. Write: "Without Docker: deploying to a new server requires 20 manual steps. With Docker: `docker run inframesh-api`. One command. Identical to local." | GitHub |

---

#### DAYS 92–95: Docker Advanced + Docker Compose

| Day | Concept | Why | Build |
|-----|---------|-----|-------|
| 92 | **Docker layers and caching** — how Docker builds images efficiently | "Put `COPY requirements.txt` before `COPY . .`. Docker caches the dependency layer. If only code changes, Docker reuses the cached layer. Build time: 3 minutes → 10 seconds" | Optimize InfraMesh Dockerfile. Measure build time before/after |
| 93 | **Docker Compose** — multi-container applications | "InfraMesh needs FastAPI + PostgreSQL + Redis running together. Docker Compose starts all three with one command and handles networking between them" | `docker-compose.yml` for InfraMesh: API depends on db, db has volume for data persistence |
| 94 | **Docker networking** — how containers talk to each other | "FastAPI container connects to PostgreSQL container at hostname 'db' (Docker service name), not 'localhost'. Environment variable: `DATABASE_URL=postgresql://user:pass@db:5432/inframesh`" | Debug: why does FastAPI container fail to connect to PostgreSQL? Fix the connection string |
| 95 | **Docker volumes** — persistent data | "PostgreSQL stores data in a Docker volume. Without a volume, all data is lost when the container restarts. `volumes: postgres_data:/var/lib/postgresql/data`" | Add named volume to docker-compose. Restart. Verify data persists |

---

#### DAYS 96–100: GitHub Actions (CI/CD)

**Concept First (Day 96)**

CI/CD stands for Continuous Integration / Continuous Deployment. Every time you push code to GitHub, an automated pipeline runs:
1. **Continuous Integration (CI):** Run tests. If tests fail, deployment is blocked.
2. **Continuous Deployment (CD):** If tests pass, automatically deploy to production.

This is how every professional engineering team works. PulseGrid deploys through GitHub Actions. SentinelGrid's firmware is compiled, signed, and uploaded to S3 through GitHub Actions. InfraMesh's Docker image is built, tested, and pushed to ECR through GitHub Actions.

```yaml
# .github/workflows/deploy.yml
name: Deploy InfraMesh

on:
  push:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Run tests
        run: |
          pip install -e ".[test]"
          pytest tests/ --cov=inframesh --cov-fail-under=80

  deploy:
    needs: test  # Only runs if test job passes
    runs-on: ubuntu-latest
    steps:
      - name: Build and push Docker image
        run: |
          docker build -t inframesh-api .
          docker push $ECR_REGISTRY/inframesh-api:$GITHUB_SHA
```

| Day | Build | What It Does |
|-----|-------|--------------|
| 96 | First GitHub Action: run pytest on every push | Tests run on every push. Failing test = red check on GitHub |
| 97 | Add Docker build step: build and push to Docker Hub | Every push to main builds and pushes a new Docker image |
| 98 | Add deployment step: SSH to EC2 and restart service | Full deployment: push → test → build → deploy. Zero manual steps |
| 99 | Add environment-specific pipelines: staging vs production | Push to `main` → deploy to staging. Create release tag → deploy to production |
| 100 | SentinelGrid firmware pipeline: compile → sign → upload to S3 | `firmware-ci.yml`: checkout → esp-idf build → sign with test key → upload to S3 with version tag |

---

### DAYS 101–120: AWS Core Services

#### DAY 101 — AWS Mental Model

**Concept First**

AWS is a collection of cloud services. Instead of buying and managing your own servers, you rent computing resources from Amazon and pay only for what you use.

The mental model: AWS is a data center you access through APIs. Every resource (server, database, queue, DNS record) is created through an API call. Terraform calls these APIs to create infrastructure.

**Services You Will Use:**

| Service | What It Is | Which Project |
|---------|-----------|---------------|
| EC2 | Virtual servers (Linux machines) | All projects — backend services run here |
| RDS | Managed PostgreSQL | InfraMesh, PulseGrid |
| S3 | Object storage (files, firmware binaries) | SentinelGrid OTA, PulseGrid postmortems |
| SQS | Message queue | InfraMesh provisioning |
| Lambda | Serverless functions (run code without a server) | SentinelGrid telemetry processing |
| IoT Core | MQTT broker for IoT devices | SentinelGrid — 10,000 nodes |
| Kinesis | High-throughput data streaming | SentinelGrid — telemetry pipeline |
| Route53 | DNS management | InfraMesh — creates DNS records for services |
| ALB | Application load balancer | InfraMesh — routes traffic to registered services |
| ACM | SSL/TLS certificate management | InfraMesh — HTTPS for all services |
| CloudFront | CDN and edge protection | SentinelGrid OTA, InfraMesh public services |
| IAM | Access management (who can do what) | All projects — security |
| CloudWatch | Logs and metrics | All projects — monitoring |
| ECR | Docker image registry | All projects — stores Docker images |

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Create: Free AWS account. Enable MFA immediately. Create IAM user with limited permissions (do not use root account) | aws.amazon.com |
| AFTERNOON | Explore: AWS console. Launch one t2.micro EC2 instance (free tier). SSH into it. Install nginx. Visit public IP in browser | AWS console |
| AFTERNOON | Read: "AWS Well-Architected Framework" — Reliability pillar summary | docs.aws.amazon.com/wellarchitected |
| EVENING | Document: `learning-journal/day-101-aws.md`. For each AWS service in the table above, write one sentence explaining what it does and which project uses it | GitHub |

---

#### DAYS 102–110: AWS Services in Depth

| Day | Service | Core Concept | Build |
|-----|---------|-------------|-------|
| 102 | **IAM** | Least privilege: a service only gets the permissions it needs. InfraMesh worker needs: Route53 create record, ALB create rule, ACM request cert. Nothing else | Create IAM role for InfraMesh worker with exactly those 3 permissions |
| 103 | **S3** | Object storage for any file. SentinelGrid stores firmware binaries here. PulseGrid stores postmortem drafts | Create S3 buckets. Upload firmware binary. Generate pre-signed URL for secure download |
| 104 | **RDS PostgreSQL** | Managed database: automated backups, patching, failover. Not self-managed | Launch RDS PostgreSQL. Connect from local machine. Migrate InfraMesh schema |
| 105 | **SQS in production** | Visibility timeout, long polling, FIFO queues vs standard | Move InfraMesh from LocalStack SQS to real AWS SQS. Configure DLQ |
| 106 | **Lambda functions** | Serverless: write Python function, AWS runs it when triggered. SentinelGrid: Lambda processes Kinesis telemetry stream | Write Lambda: receives SentinelGrid telemetry from Kinesis, writes to TimescaleDB |
| 107 | **AWS IoT Core** | Register SentinelNode device, create certificate, create IoT Rule routing to Kinesis | Register 3 simulated SentinelNodes. Publish telemetry. See it in Kinesis |
| 108 | **Route53** | Programmatic DNS record creation. InfraMesh's core feature | Python script that creates a Route53 A record. Verify it resolves with `dig` |
| 109 | **CloudWatch** | Logs and metrics. Every service sends logs to CloudWatch. Alerts when error rate spikes | Configure InfraMesh to send structured logs to CloudWatch. Create alarm: alert when error count > 10/minute |
| 110 | **ECR** | Docker image registry. GitHub Actions pushes images here. ECS pulls from here | Push InfraMesh Docker image to ECR. Pull and run on EC2 |

---

### DAYS 111–130: Terraform (Infrastructure as Code)

#### DAY 111 — Why Infrastructure as Code

**Concept First**

Imagine you built InfraMesh's AWS infrastructure by clicking in the AWS console. Three months later, the account is compromised and you must rebuild everything. You have no record of what you created, how it was configured, or in what order to create dependencies.

Infrastructure as Code (IaC) solves this: every AWS resource is described in code files. `terraform apply` creates everything exactly as described, in the correct order, handling dependencies automatically.

```hcl
# infrastructure/main.tf — InfraMesh AWS resources

# PostgreSQL database
resource "aws_db_instance" "inframesh" {
  identifier     = "inframesh-db"
  engine         = "postgres"
  engine_version = "15.4"
  instance_class = "db.t3.medium"
  
  db_name  = "inframesh"
  username = var.db_username
  password = var.db_password
  
  backup_retention_period = 7  # 7 days of automated backups
  deletion_protection     = true
}

# SQS queue for provisioning tasks
resource "aws_sqs_queue" "provisioning" {
  name                       = "inframesh-provisioning"
  message_retention_seconds  = 86400  # 24 hours
  visibility_timeout_seconds = 300    # 5 minutes per task

  redrive_policy = jsonencode({
    deadLetterTargetArn = aws_sqs_queue.provisioning_dlq.arn
    maxReceiveCount     = 3
  })
}
```

| Day | Concept | Build |
|-----|---------|-------|
| 111 | Terraform init, plan, apply | Create S3 bucket with Terraform. `terraform plan` shows what will be created. `terraform apply` creates it |
| 112 | Terraform state: what it is, why it matters | State tracks what Terraform has created. Store state in S3 (not locally). Configure remote state backend |
| 113 | Variables and outputs | Extract all hardcoded values to `variables.tf`. Create `outputs.tf` that prints created resource ARNs |
| 114 | VPC and networking | Create VPC, public subnet, private subnet, internet gateway, NAT gateway for InfraMesh |
| 115 | Terraform modules | Create reusable modules: `modules/rds-postgres`, `modules/sqs-with-dlq`. Used by multiple projects |
| 116 | Complete InfraMesh infrastructure | All InfraMesh AWS resources in Terraform: VPC, RDS, SQS, IAM roles, ECR | 
| 117 | Complete SentinelGrid infrastructure | IoT Core policies, Kinesis, Lambda, S3, CloudFront in Terraform |
| 118 | Terraform workspaces: dev, staging, production | Same Terraform code creates three different environments with different sizes |
| 119 | Terraform in CI/CD: `terraform plan` on PR, `terraform apply` on merge | GitHub Actions: show plan on PR. Engineer reviews. Merge triggers apply |
| 120 | Complete all four projects' Terraform | All infrastructure as code. `terraform destroy` cleans everything. `terraform apply` rebuilds in 15 minutes |

---

### DAYS 121–130: Observability and Monitoring

#### DAY 121 — The Three Pillars of Observability

**Concept First**

Observability is the ability to understand what is happening inside a system from its external outputs. A system that cannot be observed cannot be debugged in production.

Three pillars:
1. **Logs:** Text records of events. "Service started", "Error processing request", "Provisioning failed"
2. **Metrics:** Numerical measurements over time. Requests/second, error rate, response time
3. **Traces:** A request's journey through multiple services. "The GitHub webhook took 2ms in FastAPI, 50ms in Kafka, 120ms in the risk scorer, 800ms calling the LLM API"

**Why This Matters for All Four Projects:**

Without observability:
- InfraMesh: a provisioning task fails silently. Developer never knows. Support ticket arrives 2 days later.
- SentinelGrid: a node starts producing wrong readings due to a firmware bug. Nobody knows for weeks.
- PulseGrid: risk scores are wrong (model drift). Deployments get incorrect scores. Engineers stop trusting the tool.
- MemCore: fix suggestions are getting worse (vocabulary drift). Developers reject more suggestions. Tool loses adoption.

With observability: you see the problem before the user does.

```python
# Structured logging — what all four projects use
import structlog

logger = structlog.get_logger()

# This is what InfraMesh logs when processing a provisioning task
logger.info(
    "provisioning_started",
    service_id="abc123",
    service_name="payment-service",
    domain="payment.company.com",
    team="payments",
    worker_id="worker-2"
)

# This is searchable: find all provisioning_started events for domain="payment.company.com"
# This is parseable: every field is a structured key-value pair, not free text
```

| Day | Build | Document |
|-----|-------|----------|
| 121 | Implement structured logging in all FastAPI services using `structlog` | `OBSERVABILITY.md` — logging standard for all projects |
| 122 | Prometheus metrics: expose `/metrics` endpoint from all services | Counter: requests_total. Histogram: request_duration_seconds. Gauge: queue_depth |
| 123 | Grafana: install with Docker, connect to Prometheus | Create first dashboard: InfraMesh API request rate and latency |
| 124 | Alerting: Grafana alert when error rate > 5% | `RUNBOOK.md` entry: what to do when this alert fires |
| 125 | SentinelGrid observability: device health metrics to Grafana | Fleet dashboard: nodes online, battery distribution, anomaly score heatmap |
| 126 | PulseGrid observability: Kafka consumer lag to Grafana | Alert: consumer lag > 30 seconds indicates processing is falling behind |
| 127 | Distributed tracing with OpenTelemetry | Instrument InfraMesh API. See spans in Jaeger. Trace a slow provisioning request |
| 128 | Log aggregation: CloudWatch Logs Insights queries | Query: all ERROR logs from InfraMesh in the last 1 hour, grouped by error type |
| 129 | Runbook creation | Write 5 runbooks for InfraMesh. Each runbook: alert trigger, what it means, step-by-step investigation, remediation |
| 130 | Postmortem practice | Simulate an InfraMesh outage (kill the worker). Write a full postmortem. Timeline, root cause, corrective actions |

---

### DAYS 131–150: Production Deployment and Security

#### DAYS 131–135: Security Fundamentals

| Day | Concept | Why | Build |
|-----|---------|-----|-------|
| 131 | **HTTPS everywhere** — TLS, certificates, HSTS | "HTTP sends data in plaintext. TLS encrypts it. Any network between client and server can read HTTP. With TLS, only client and server can read it" | Configure TLS for InfraMesh API using AWS ACM + ALB |
| 132 | **Secret management** — never store secrets in code | "A database password in code is a security incident waiting to happen. Git history is permanent. AWS Secrets Manager stores secrets encrypted and rotates them automatically" | Move all InfraMesh secrets to AWS Secrets Manager. Access in Python via boto3 |
| 133 | **CORS** — cross-origin resource sharing | "PulseGrid's React dashboard (served from app.pulsegrid.io) calls the API (api.pulsegrid.io). Without CORS headers, the browser blocks the request" | Configure CORS in FastAPI. Allow only trusted origins |
| 134 | **Rate limiting** — protecting APIs from abuse | "Without rate limiting, a single malicious client can send 10,000 requests/second and crash InfraMesh. Redis INCR+EXPIRE: 100 requests/minute per team" | Implement rate limiting in InfraMesh using Redis |
| 135 | **Input validation and injection prevention** | "SQL injection: if InfraMesh builds SQL by string concatenation, an attacker sends `name='; DROP TABLE services;--` and deletes all services. Parameterized queries prevent this" | Verify all InfraMesh SQL uses parameterized queries. Run OWASP ZAP against API |

---

#### DAYS 136–150: Phase 3 Integration and Assessment

| Day | Task |
|-----|------|
| 136-139 | Complete InfraMesh v0.3: async provisioning + AWS infrastructure + monitoring + security |
| 140-143 | Complete SentinelGrid cloud pipeline: IoT Core + Kinesis + Lambda + TimescaleDB in Terraform |
| 144-147 | Complete PulseGrid infrastructure: Kafka + Neo4j + databases + CI/CD |
| 148-149 | Full documentation pass: all projects updated |
| 150 | Phase 3 assessment: 10 questions |

**Phase 3 Completion Assessment:**

1. A new engineer joins. They need to run InfraMesh locally in 5 minutes. What is the single command? What does it start?
2. InfraMesh's database password needs to be rotated. How do you do this without restarting the application?
3. PulseGrid's Kafka consumer lag is 45 seconds (alert fired). Write the 5-step investigation procedure.
4. Write a Terraform resource for an SQS queue with a DLQ, 3 max receive count, and 24-hour message retention.
5. Your InfraMesh deployment is causing errors. GitHub Actions completed successfully. Where do you look first in CloudWatch?

---

# PART 5 — PHASE 4: HARDWARE, FIRMWARE, AND EMBEDDED AI
## Days 151–240 | SentinelGrid Hardware + Firmware + TFLite

---

### WHY THIS PHASE EXISTS

SentinelGrid's intelligence starts at the hardware layer. The PCB is the physical body. The firmware is the nervous system. The edge AI model is the local intelligence. Without understanding these three layers, SentinelGrid is just a data logger — it collects sensor data and sends it to the cloud, but the cloud is the only intelligence. The vision of SentinelGrid is edge intelligence: the node detects anomalies locally, even without internet.

---

### DAYS 151–165: Electronics Fundamentals

| Day | Concept | Why It Matters for SentinelGrid | Build/Practice |
|-----|---------|--------------------------------|----------------|
| 151 | **Voltage, current, resistance** — Ohm's Law (V=IR) | "The ADXL355 needs 3.3V supply, 1mA current. The voltage regulator must output 3.3V at 100mA (headroom for startup surge)" | Calculate: ESP32-S3 uses 80mA active. Battery is 3.7V 3000mAh. How many hours does it last? |
| 152 | **Capacitors** — energy storage, decoupling, filtering | "Without a 100nF decoupling capacitor on every IC power pin, high-frequency noise corrupts ADC readings. This is the Revision 1 bug that took 2 weeks to find" | Simulate on falstad.com/circuit: RC low-pass filter. Observe filtering effect |
| 153 | **Schematic reading** — symbols, net names, power rails | "Reading the ADXL355 application circuit schematic tells me: 100nF on VDD, 10µF on VS, 0Ω on MISO for optional pullup. Every connection is specified" | Download ADXL355 datasheet from analog.com. Read Section 7 (SPI interface). Draw the application circuit |
| 154 | **PCB layout concepts** — traces, planes, clearance | "The Revision 1 PCB had the switching regulator too close to the ADC input. The 2MHz switching frequency coupled noise into the analog signal. Lesson: separate analog and digital sections" | View an open-source PCB design on GitHub (search "ESP32 board schematic KiCad") |
| 155 | **Power supply design** — LDO vs switching regulator | "LDO (linear regulator): quiet but inefficient (loses energy as heat). Switching regulator: efficient but noisy. SentinelNode: switching for main 3.3V (efficient), LDO for analog 3.3V (quiet ADC)" | Calculate: LDO input 5V, output 3.3V, 100mA load. How much power is lost as heat? |
| 156 | **Signal integrity** — impedance, ringing, termination | "The oscilloscope shows ringing on the SPI clock line — the signal overshoots 3.6V (above 3.3V logic level). Root cause: impedance mismatch. Fix: 33Ω series resistor on the clock line" | Watch: "EEVblog #280 - PCB Layout Tutorial" on YouTube |
| 157 | **ESD protection** — electrostatic discharge | "A technician touches an unprotected sensor input pin. The static discharge destroys the input. $0.05 TVS diode prevents this" | Identify ESD protection on any ESP32 devkit schematic |
| 158 | **Battery management** — LiPo charging, protection circuits | "LiPo battery: cannot discharge below 3.0V (damages cells permanently). Cannot charge above 4.2V (fire risk). LTC4054 IC manages both limits" | Read LTC4054 datasheet. Draw the application circuit |
| 159 | **KiCad introduction** — schematic editor | "KiCad is free, open-source. Every SentinelNode PCB is designed in KiCad. The schematic is version-controlled in Git alongside firmware" | Install KiCad. Complete "KiCad Getting Started" tutorial — kicad.org/help/learning-resources |
| 160 | **KiCad schematic** — place components, draw connections | Place ESP32-S3 symbol, add power symbols, draw one SPI connection | KiCad schematic editor |
| 161 | **BOM (Bill of Materials)** — component selection | Select ADXL355 (vibration), INA226 (current), MLX90614 (temperature), MQ-135 (gas). For each: read the datasheet first page | DigiKey.com datasheet search |
| 162 | **PCB layout introduction** — KiCad PCB editor | Place ESP32-S3 module and one sensor. Route the SPI traces | KiCad PCB editor |
| 163 | **Ground planes** — why they matter | "Add copper pour on ground layer. This reduces impedance of the return path for every signal. Significantly reduces EMI" | Add ground plane to your KiCad PCB layout |
| 164 | **Design Rule Check (DRC)** — verify PCB design | Run DRC in KiCad. Fix all errors. Zero errors means the PCB can be manufactured | KiCad DRC |
| 165 | **Gerber generation** — manufacturing files | Generate Gerbers from KiCad. View them in gerbv or KiCad Gerber viewer. These are the files sent to a PCB fab | KiCad Gerber export |

---

### DAYS 166–190: Embedded C and Firmware

#### DAY 166 — ESP-IDF Setup and Hello World

**Concept First**

ESP-IDF is Espressif's official development framework for ESP32. It includes:
- FreeRTOS (RTOS for task scheduling)
- HAL (Hardware Abstraction Layer — C functions for peripherals)
- WiFi, Bluetooth, MQTT libraries
- Partition table management and OTA support

Without ESP-IDF, you would write raw register manipulation for every peripheral. With ESP-IDF, `gpio_set_level(GPIO_NUM_5, 1)` turns on a GPIO — readable, portable, debuggable.

```c
// main.c — SentinelNode Entry Point
#include "freertos/FreeRTOS.h"
#include "freertos/task.h"
#include "esp_log.h"

static const char *TAG = "SentinelNode";

// This runs on CPU Core 1 (Core 0 is used by WiFi stack)
void app_main(void) {
    ESP_LOGI(TAG, "SentinelNode v2.3.1 starting...");
    
    // Initialize all subsystems
    sensor_init();
    mqtt_init();
    ota_init();
    
    // Create FreeRTOS tasks
    xTaskCreate(sensor_task, "sensor", 4096, NULL, 5, NULL);
    xTaskCreate(fft_task, "fft", 8192, NULL, 4, NULL);
    xTaskCreate(inference_task, "inference", 8192, NULL, 3, NULL);
    xTaskCreate(comms_task, "comms", 4096, NULL, 2, NULL);
    xTaskCreate(ota_task, "ota", 4096, NULL, 1, NULL);
    
    // Watchdog is fed by a timer, not a task
    esp_task_wdt_init(5, true);  // Reset if not fed for 5 seconds
}
```

| Day | Build | Resource |
|-----|-------|----------|
| 166 | Install ESP-IDF. Compile and flash hello_world example | docs.espressif.com/projects/esp-idf/en/latest/esp32s3/get-started |
| 167 | GPIO: blink LED on Wokwi simulator (no hardware needed) | wokwi.com — ESP32 LED blink project |
| 168 | UART logging: structured JSON log over serial | `ESP_LOGI` with JSON format matching SentinelGrid log schema |
| 169 | SPI driver: configure SPI master, read ADXL355 device ID | wokwi.com has ADXL345 (similar) simulator |
| 170 | I2C driver: configure I2C master, read INA226 device ID | wokwi.com I2C simulation |

---

#### DAYS 171–185: FreeRTOS Deep Dive

| Day | Concept | Production Problem It Solves | Build |
|-----|---------|------------------------------|-------|
| 171 | **Task creation**: `xTaskCreate`, stack size, priority | "Without tasks, WiFi blocks sensor reading. With tasks, they run independently" | Create sensor task + comms task. Observe they run concurrently |
| 172 | **Queue communication**: `xQueueCreate`, `xQueueSend`, `xQueueReceive` | "Sensor task produces 1000 samples/second. FFT task consumes at its own pace. Queue buffers between them" | Sensor task → queue → FFT task pipeline on Wokwi |
| 173 | **Mutex**: `xSemaphoreCreateMutex`, `xSemaphoreTake`, `xSemaphoreGive` | "Two tasks sharing SPI bus: without mutex, transactions overlap and corrupt each other" | Demonstrate SPI corruption without mutex. Fix with mutex |
| 174 | **Stack overflow detection**: watermark API, MPU | "Stack overflow corrupts adjacent memory. Looks like random crashes unrelated to the actual cause" | Deliberately cause stack overflow. Fix. Check watermarks |
| 175 | **Task watchdog**: `esp_task_wdt_add`, `esp_task_wdt_reset` | "A task stuck in an infinite loop due to a bug blocks everything. Watchdog detects no reset in 5 seconds → system resets" | Demonstrate: task hangs, watchdog resets after 5 seconds |
| 176 | **Power management**: `esp_light_sleep_start`, `esp_deep_sleep_start` | "Active mode: 80mA. Deep sleep: 48µA. 1000× current reduction. 6 months battery vs 5 days" | Measure current in active vs sleep mode (simulate with calculation) |
| 177 | **DMA for ADC**: circular buffer, transfer complete interrupt | "CPU copying 1000 ADC samples/second = 30% CPU utilization. DMA: 0% CPU. CPU runs FFT while DMA handles ADC" | Configure ADC + DMA on Wokwi. Measure: FFT runs faster when DMA handles ADC |
| 178 | **Interrupt handler**: IRAM_ATTR, minimal ISR, defer to task | "ISR must be fast. No malloc. No blocking. No logging. Set a flag and return. Task reads the flag" | Data-ready interrupt for ADXL355: ISR sets flag, sensor task reads it |
| 179 | **Hard fault handler**: save registers to flash | "Crash without crash handler: device resets, no information. With handler: registers saved, transmitted to cloud" | Implement hard fault handler that saves PC, LR, SP to NVS (ESP32 non-volatile storage) |
| 180 | **OTA implementation**: A/B partition, `esp_ota_begin/write/end` | "OTA without A/B: if new firmware crashes on boot, device is bricked permanently. With A/B: bootloader rolls back to working partition" | Implement OTA that downloads from HTTP server, writes to inactive partition, reboots |
| 181 | **Firmware signing**: generate key, sign binary, verify in bootloader | "Unsigned OTA: anyone can push malicious firmware. Signed: bootloader rejects anything not signed by our key" | Generate RSA key pair. Sign firmware with espsecure.py. Bootloader verifies |
| 182 | **Memory map**: partition table, flash layout | "SentinelNode flash: bootloader (64KB), OTA-0 (1MB), OTA-1 (1MB), model (256KB), NVS (64KB), data (512KB)" | Create custom partition table for SentinelNode |
| 183 | **BLE configuration interface**: GATT service, characteristic | "A technician configures a newly deployed node's WiFi credentials via BLE from a phone app — no keyboard needed" | BLE GATT server that exposes WiFi credentials as a writable characteristic |
| 184 | **Structured firmware logging**: JSON over UART → gateway → cloud | "Every task logs in JSON. Gateway collects, forwards to CloudWatch. Search by node_id + task + event_type" | All SentinelNode tasks log structured JSON. Gateway Python script forwards to InfluxDB |
| 185 | **Complete SentinelNode firmware v1.0** | All 7 tasks integrated, running on Wokwi. Stack watermarks measured, documented | FIRMWARE.md updated with all task specs |

---

### DAYS 186–210: Signal Processing and Edge AI

#### DAYS 186–195: Signal Processing Pipeline

| Day | Concept | Build |
|-----|---------|-------|
| 186 | FFT theory: time domain vs frequency domain | Python: generate 50Hz + 200Hz mixed signal. Plot time domain. Compute FFT. Plot frequency domain. See the two peaks |
| 187 | Windowing: Hann window, spectral leakage | Python: compare FFT with and without Hann window. Show leakage reduction |
| 188 | Feature extraction: RMS, kurtosis, spectral bands | Python: `extract_features(samples) -> np.array` — 15-element feature vector |
| 189 | C implementation of FFT: CMSIS-DSP | ESP-IDF: `arm_rfft_fast_f32` on synthetic data. Verify matches Python output |
| 190 | C implementation of feature extraction | Port Python feature extractor to C. Verify output matches within tolerance |
| 191 | Digital filter design: IIR Butterworth low-pass | Python: design 4th-order Butterworth at 480Hz. Port coefficients to C |
| 192 | Sensor fusion: combine vibration + temperature + current | Python: weighted ensemble. `fused_score = 0.6*vib + 0.25*curr + 0.15*temp` |
| 193 | Complete signal processing pipeline | End-to-end in Python: raw samples → filter → FFT → features → normalized vector |
| 194 | Port to C: complete pipeline in firmware | C implementation of full pipeline. Measure: total processing time < 20ms |
| 195 | Benchmark and document | `SIGNAL_PROCESSING.md` with: pipeline diagram, feature descriptions, timing measurements, accuracy validation |

---

#### DAYS 196–210: TinyML and Edge AI

| Day | Concept | Build |
|-----|---------|-------|
| 196 | Anomaly detection: why autoencoders | Download Case Western Reserve Bearing Dataset (free). Explore data |
| 197 | Autoencoder in PyTorch: architecture | Build: encoder (15→8→4), decoder (4→8→15). Train on normal data only |
| 198 | Training: loss curve, validation, threshold selection | Train 50 epochs. Plot loss. Set threshold at mean + 3*std on validation set |
| 199 | Evaluation: detection rate, false positive rate | Test on fault data. Target: >85% detection rate, <5% false positive rate |
| 200 | TFLite export: `converter.convert()` | Export trained model to `.tflite` format. Verify output matches PyTorch |
| 201 | Post-training quantization: INT8 | Quantize. Measure: size 182KB → 46KB. Accuracy 95.1% → 91.4% |
| 202 | TFLite Micro on ESP32-S3: `MicroInterpreter` | Deploy quantized model on Wokwi. Run inference on 15-element feature vector |
| 203 | Memory arena sizing: find minimum | Start with 100KB. Reduce until `AllocateTensors()` fails. Add 20% margin |
| 204 | Inference latency measurement: `esp_timer_get_time()` | Measure: 1000 inference runs. Min/max/average/p99. Document in BENCHMARKS.md |
| 205 | Model OTA: separate partition update | Download new model binary from S3. Write to model partition. Switch without reboot |
| 206 | Model drift detection: compare edge vs cloud scores | Python: compute KL divergence weekly. Alert if > 0.15 |
| 207 | Federated learning concept | Python simulation: compute gradients locally. Aggregate from 3 simulated nodes |
| 208 | Complete edge AI system end-to-end | Sensor → FFT → features → TFLite → score → MQTT alert if score > threshold |
| 209 | Cloud ML pipeline: weekly retraining | SageMaker: query TimescaleDB → train → evaluate → export → upload S3 |
| 210 | Phase 4 assessment and documentation | EDGE_AI.md complete. Interview statement written |

---

# PART 6 — PHASE 5: ADVANCED PROJECTS
## Days 211–300 | PulseGrid + MemCore Complete Implementation

---

### DAYS 211–255: PulseGrid — Engineering Intelligence Platform

#### DAYS 211–220: Graph Database and Dependency Mapping

**Concept First (Day 211)**

Neo4j stores data as nodes and edges (relationships). This is fundamentally different from a relational database's tables and rows.

```
RELATIONAL (PostgreSQL) — join 5 tables:
SELECT s.name, dep.name
FROM services s
JOIN service_dependencies sd ON s.id = sd.service_id
JOIN services dep ON sd.dependency_id = dep.id
WHERE s.name = 'payment-service'
-- Finds direct dependencies. For transitive dependencies: recursion needed.

GRAPH (Neo4j) — traverse edges:
MATCH (s:Service {name: 'payment-service'})-[*1..5]->(dep:Service)
RETURN dep.name, count(*) as dependency_depth
-- Finds ALL dependencies up to 5 hops. Milliseconds.
```

PulseGrid's blast radius calculator needs to answer: "If payment-service fails, which services are affected, and by how many hops?" This is a graph traversal problem. Neo4j is the right tool.

| Day | Build | Document |
|-----|-------|----------|
| 211 | Install Neo4j. Create service nodes. Create dependency edges | Cypher query basics in PULSEGRID.md |
| 212 | Populate from OpenTelemetry traces: parse spans, extract service→service calls | `graph_updater.py` |
| 213 | Blast radius query: traverse graph, weight by call frequency | `blast_radius.cypher` |
| 214 | API endpoint: `GET /api/v1/blast-radius/{service_id}` returns weighted impact | `routes/blast_radius.py` |
| 215 | Real-time graph updates: stream processor updates graph as traces arrive | Complete dependency graph pipeline |

---

#### DAYS 216–235: Risk Scoring and Postmortem Generation

| Day | Build |
|-----|-------|
| 216 | GitHub App: create, configure webhooks, receive first PR event |
| 217 | Parse PR event: extract 23 risk features |
| 218 | Historical incident data: correlate past PRs with past incidents |
| 219 | XGBoost model training: train on 6 months of synthetic incident history |
| 220 | Model evaluation: AUC, precision-recall curve, backtest on known incidents |
| 221 | Risk score API: POST score as GitHub PR comment in < 60 seconds |
| 222 | PagerDuty integration: receive incident webhooks, store in TimescaleDB |
| 223 | Incident timeline assembler: correlate events from 6 sources for incident window |
| 224 | ChromaDB: store past incidents as embeddings, query by similarity |
| 225 | Claude API integration: structured prompt with 8 context slots |
| 226 | Postmortem generator: RAG retrieval + LLM generation |
| 227 | Confluence integration: POST generated postmortem to Confluence page |
| 228 | DORA metrics: deployment frequency, lead time, MTTR, change failure rate |
| 229 | React dashboard: risk PR list, DORA metrics panels |
| 230 | D3.js dependency graph: interactive blast radius visualization |
| 231-235 | Integration testing, load testing (1000 events/minute), documentation |

---

#### DAYS 236–255: MemCore — Embedded AI SDK

| Day | Build | Concept Covered |
|-----|-------|----------------|
| 236 | tree-sitter AST parser: parse Python function, extract structure | Static code analysis |
| 237 | Call graph construction: which function calls which | Dependency analysis |
| 238 | CodeBERT embeddings: convert functions to semantic vectors | Semantic code understanding |
| 239 | ChromaDB storage: store function embeddings with metadata | Vector memory store |
| 240 | Exception hook: `sys.excepthook` — capture all unhandled exceptions | Runtime observation |
| 241 | Log interceptor: custom `logging.Handler` — capture all log output | Log analysis |
| 242 | Redis short-term memory: current session events, last 100 exceptions | Short-term context |
| 243 | PostgreSQL episodic memory: structured bug history | Long-term structured memory |
| 244 | Context assembler: retrieve similar past bugs + relevant code + recent changes | RAG assembly |
| 245 | LLM reasoning engine: structured prompt → Claude API → fix suggestions | Inference layer |
| 246 | Vocabulary drift detector: weekly recompute embeddings, compare to stored | Drift monitoring |
| 247 | New vocabulary entry creator: when pattern appears 3+ times, name it | Emergent vocabulary |
| 248 | Developer feedback loop: accept/reject/modify suggestion, store outcome | Continuous learning |
| 249 | SDK packaging: `pip install memcore`. Integration: `import memcore; memcore.watch()` | SDK design |
| 250 | CLI: `memcore diagnose`, `memcore history`, `memcore suggest` | Developer UX |
| 251 | Integration test: MemCore watching InfraMesh codebase | Cross-project integration |
| 252 | C agent: 400-line C implementation for firmware systems | Embedded variant |
| 253 | MemCore watching SentinelGrid gateway | Cross-project integration |
| 254 | Documentation: MEMCORE.md, API.md, examples/ | SDK documentation |
| 255 | Phase 5 assessment | 10 assessment questions |

---

# PART 7 — PHASE 6: PRODUCTION READINESS AND PORTFOLIO
## Days 301–360 | Integration + Documentation + Portfolio

---

### DAYS 301–330: Full System Integration

#### DAY 301 — Production Readiness Checklist

Before any system goes to production, answer all of these:

| Category | Checklist Item | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|----------|---------------|-----------|--------------|-----------|---------|
| Resilience | Does it survive a process crash? | ECS restarts container | HW watchdog resets firmware | ECS restarts | Restarts |
| Resilience | Does it survive a network failure? | SQS retains tasks | Flash buffer + LoRa fallback | Kafka retains events | Queues requests |
| Resilience | Does it survive a database failure? | Redis cache + 503 | Local inference continues | Cached risk scores | Raw error display |
| Security | Are secrets in Secrets Manager? | ✓ | ✓ | ✓ | ✓ |
| Security | Is all traffic encrypted (TLS)? | ✓ | ✓ (MQTT+TLS) | ✓ | ✓ |
| Security | Does it follow least-privilege IAM? | ✓ | ✓ | ✓ | N/A |
| Observability | Are structured logs going to CloudWatch? | ✓ | ✓ | ✓ | ✓ |
| Observability | Are metrics exposed to Prometheus? | ✓ | ✓ | ✓ | ✓ |
| Observability | Does Grafana have dashboards? | ✓ | ✓ | ✓ | ✓ |
| Observability | Are there runbooks for all alerts? | 5 runbooks | 5 runbooks | 4 runbooks | 2 runbooks |
| Deployment | Is there a CI/CD pipeline? | ✓ | ✓ (firmware) | ✓ | ✓ |
| Deployment | Is infrastructure in Terraform? | ✓ | ✓ | ✓ | N/A |
| Deployment | Can you rebuild from scratch in < 30 min? | ✓ (12 min) | ✓ (20 min) | ✓ (18 min) | ✓ (5 min) |
| Scale | Has it been load tested? | 100 concurrent | 200 nodes | 10K events/min | 100 bugs/hour |
| Disaster | Is there a documented disaster recovery procedure? | ✓ | ✓ | ✓ | ✓ |

#### DAYS 302–315: Integration Testing

| Day | Integration Test |
|-----|----------------|
| 302 | InfraMesh: register 100 services simultaneously. Verify all provision within 60 seconds. Zero failures |
| 303 | SentinelGrid: 10 nodes running 72 hours. Zero unplanned resets. Anomaly detection working |
| 304 | SentinelGrid: simulate 4-hour WiFi outage. Verify 0 telemetry lost. Verify chronological delivery on reconnect |
| 305 | SentinelGrid: deploy bad firmware to 1 node (canary). Verify rollback after 3 failed boots |
| 306 | PulseGrid: 1000 GitHub events simultaneously. Measure: all risk scores posted within 90 seconds |
| 307 | PulseGrid: simulate incident. Verify postmortem posted within 5 minutes of resolution |
| 308 | MemCore: inject heap memory leak (malloc without free) in InfraMesh. Verify MemCore detects the pattern |
| 309 | MemCore: inject a null pointer bug. Verify MemCore retrieves similar past null pointer bugs |
| 310 | Cross-project: deploy bad InfraMesh code. PulseGrid scores it as high risk. MemCore detects the bug pattern |

---

### DAYS 316–360: Documentation Strategy and Portfolio Building

#### DAY 316 — GitHub Documentation Strategy

**The README That Gets You an Interview**

Your project README is the first thing a hiring manager sees. It has 30 seconds to make them want to read more.

```markdown
# InfraMesh

> Self-service infrastructure provisioning platform. Developers register a service 
> and get DNS, load balancing, health monitoring, and edge protection in 30 seconds.

## Problem
Engineering teams lose 50+ hours/week on manual infrastructure tickets.
InfraMesh eliminates this entirely.

## Demo
![InfraMesh Demo](docs/demo.gif)
[Live at https://inframesh.yourname.dev/docs]

## Architecture
[Architecture diagram image here]

## Key Technical Decisions
| Decision | Why |
|----------|-----|
| Async provisioning via SQS | 30-second provisioning cannot block the API |
| PostgreSQL with row-level security | Teams cannot see each other's services |
| TimescaleDB for health checks | Time-range queries are 70x faster than PostgreSQL |

## Performance
- Service registration: 50ms response time
- Provisioning completion: < 30 seconds
- Health check processing: 1000/minute
- Load tested: 100 concurrent registrations, zero failures

## Technology Stack
Python, FastAPI, PostgreSQL, TimescaleDB, Redis, AWS (SQS, Route53, ALB, ACM),
Docker, Terraform, GitHub Actions, Grafana
```

| Day | Task |
|-----|------|
| 316 | Write production-quality README for all 4 projects following the template above |
| 317 | Create architecture diagrams using excalidraw.com. Export as PNG and SVG. Add to all READMEs |
| 318 | Record demo videos using Loom (free): 3-minute walkthrough of each project |
| 319 | Write `ARCHITECTURE.md` for all 4 projects: system design decisions, trade-offs, alternatives considered |
| 320 | Write `POSTMORTEMS/` for all 4 projects: minimum 2 each. Real incident simulations |
| 321 | Write `ADR/` folder for all 4 projects: minimum 5 decisions each |
| 322 | Write `BENCHMARKS.md` for all 4 projects: measured numbers only, no estimates |
| 323 | Write `SECURITY.md` for all 4 projects: how auth works, how secrets are managed, penetration test results |

---

#### DAY 324 — Portfolio Beyond GitHub

**Where to Publish Your Work**

GitHub is necessary but not sufficient. Your work should be visible in multiple places:

| Platform | What to Post | Why |
|----------|-------------|-----|
| **dev.to** (free blog) | Technical articles about what you built and what you learned | SEO finds you. Hiring managers Google your name |
| **Hashnode** (free blog) | Deep-dive architecture articles | Engineering community reads these |
| **LinkedIn** | Project announcements with architecture diagrams | Recruiters see this first |
| **Twitter/X** | Building-in-public posts with Grafana screenshots | Engineering community follows |
| **HackerNews (Show HN)** | When a project is ready, post "Show HN: [Project name] — [one line]" | High-signal community |
| **Reddit r/programming** | Technical deep-dives | Discussion drives profile visibility |
| **Your own website** | Portfolio page linking all projects | Permanent, professional |

**What to Write About:**

| Article Idea | When to Write |
|-------------|--------------|
| "How I built a self-healing firmware system with FreeRTOS and TFLite" | After SentinelGrid firmware is working |
| "Why we chose Neo4j over PostgreSQL for service dependency mapping" | After PulseGrid's graph database is built |
| "I built an AI that generates postmortems automatically" | After PulseGrid postmortem generator works |
| "The 3 mistakes that cost me 2 weeks in embedded firmware development" | After debugging real firmware bugs |
| "How SQS and dead letter queues make InfraMesh resilient" | After InfraMesh queue worker is complete |

**The Technical Blog Formula:**

```
Title: [Specific Result] — not "What I learned about Kafka"
      but "How I processed 10,000 engineering events/minute with Kafka for PulseGrid"

Opening (100 words): What problem you solved and why it matters
Problem (200 words): The specific challenge with concrete numbers
Solution (500 words): Architecture diagram + code snippet + explanation
Result (100 words): Measured outcome (latency, throughput, accuracy)
Lessons (100 words): What you learned / what you would do differently
```

---

#### DAYS 325–340: Active Recall and Interview Preparation

**System Design Interview Preparation**

System design interviews test whether you can design a system from scratch. The interviewer gives you a problem ("Design Twitter"), you spend 45 minutes asking clarifying questions, making trade-off decisions, and drawing an architecture.

Your four projects give you real answers to real system design questions:

| Interview Question | Your Real Answer |
|-------------------|-----------------|
| "Design a health check system" | "I built this in InfraMesh. The health check worker queries each service's /health endpoint every 30 seconds, stores results in TimescaleDB, and fires alerts after 3 consecutive failures. The most interesting trade-off was..." |
| "Design an anomaly detection system" | "I built two versions: cloud-side LSTM autoencoder and edge-side INT8 TFLite model. The edge model has 91.4% accuracy vs 95.1% for the cloud model, but it detects anomalies in 47ms without network dependency..." |
| "Design an event-driven architecture" | "PulseGrid is event-driven. GitHub sends webhooks to Kafka. Two consumers process the same event independently: the risk scorer and the dependency graph updater. Kafka retains events for 7 days for replay..." |
| "How do you handle distributed system failures?" | "I documented four failure modes per project. The most interesting is SentinelGrid's store-and-forward: nodes buffer telemetry in SPI flash during 4-hour WiFi outages and deliver chronologically on reconnect..." |

**Active Recall: 20 Questions to Answer Weekly**

1. What is the difference between a message queue and a pub/sub system?
2. Explain the A/B OTA partition scheme to someone who has never heard of it.
3. Why does SentinelGrid use TimescaleDB instead of PostgreSQL for telemetry?
4. What is a dead letter queue and when does a message go there?
5. Why does PulseGrid use Neo4j instead of PostgreSQL for the dependency graph?
6. What is a FreeRTOS mutex and why is it needed for the SPI bus?
7. How does InfraMesh know which team owns a service?
8. What is model quantization and what does it trade off?
9. Why does MemCore use ChromaDB instead of PostgreSQL for bug memory?
10. What happens to a SentinelGrid node when AWS IoT Core is unavailable?
11. What is exponential backoff and where is it used in these projects?
12. How does InfraMesh prevent one team from seeing another team's services?
13. What is the difference between Kafka consumer groups and individual consumers?
14. Why does SentinelGrid use MQTT instead of HTTP for telemetry?
15. What is a Terraform state file and why must it be stored remotely?
16. How does PulseGrid's risk model get retrained when conditions change?
17. What is the 12-factor app methodology and which principles apply to InfraMesh?
18. What is the difference between observability and monitoring?
19. How does the blast radius calculator in PulseGrid work technically?
20. What is an Architecture Decision Record and why do you write them?

---

#### DAYS 341–360: Final Assessment and Launch

**Day 341–350: Final Documentation Pass**

Every repository must have:
- [ ] README with demo GIF/video and live URL
- [ ] ARCHITECTURE.md with system diagram
- [ ] API.md with Swagger UI link
- [ ] DATABASE.md with schema and indexes
- [ ] BENCHMARKS.md with measured numbers
- [ ] SECURITY.md with auth and secret management
- [ ] OBSERVABILITY.md with logging and metrics strategy
- [ ] RUNBOOK.md with at least 5 runbooks
- [ ] ADR/ folder with at least 5 decisions
- [ ] POSTMORTEMS/ folder with at least 2 incidents
- [ ] .github/workflows/ with CI/CD pipeline
- [ ] infrastructure/ with Terraform

**Day 351–355: Live Deployment**

Every project must be deployed to a real public URL:
- InfraMesh: `https://inframesh.yourname.dev` (Railway.app free tier or AWS Free Tier)
- SentinelGrid API: `https://api.sentinelgrid.yourname.dev`
- PulseGrid: `https://pulsegrid.yourname.dev`
- MemCore: PyPI package at `pip install memcore-yourname`

**Day 356–360: Technical Blogging**

Write and publish 4 articles (one per project) on dev.to or Hashnode.

---

# PART 8 — QUICK REFERENCE TABLES

---

## Practice Sites by Skill (Complete Reference)

| Skill | Primary | Secondary | Advanced |
|-------|---------|-----------|---------|
| Python logic | exercism.org/tracks/python | hackerrank.com/domains/python | LeetCode Easy/Medium |
| SQL | sqlzoo.net | hackerrank.com/domains/sql | mode.com/sql-tutorial |
| System design | systemdesignschool.io | pramp.com | Google SRE Book |
| Linux | overthewire.org/wargames/bandit | cmdchallenge.com | linuxupskillchallenge.org |
| Git | learngitbranching.js.org | — | Pro Git Book (free) |
| Embedded C | wokwi.com (ESP32 sim) | onlinegdb.com | Nand2Tetris |
| FreeRTOS | wokwi.com + freertos.org | Percepio Tracealyzer (free tier) | FreeRTOS Reference Manual |
| Signal Processing | numpy FFT tutorial | kaggle.com bearing datasets | "Machinery Vibration" papers on arXiv |
| Edge AI | edgeimpulse.com | tinyml.org summit talks | paperswithcode.com |
| ML/Python AI | kaggle.com/learn | fast.ai | arXiv cs.LG |
| MQTT | hivemq.com/mqtt-guide | mosquitto.org docs | MQTT spec (OASIS) |
| Kafka | kafka.apache.org/quickstart | — | Confluent Kafka tutorials |
| Docker | docs.docker.com/get-started | play-with-docker.com | — |
| AWS | aws.amazon.com/getting-started | cloudcraft.co | AWS Well-Architected |
| Terraform | developer.hashicorp.com/terraform | — | registry.terraform.io |
| Neo4j | graphacademy.neo4j.com | — | — |
| Vector DB | docs.trychroma.com | — | "FAISS" paper |
| LLM Integration | platform.anthropic.com/docs | — | "RAG" paper (Lewis 2020) |
| Debugging | interrupt.memfault.com | stackoverflow.com | — |
| Architecture | excalidraw.com | draw.io | Google SRE Book (free) |
| PCB Design | kicad.org/help | learn.sparkfun.com | IPC-A-610 standard |
| Electronics | learn.sparkfun.com | falstad.com/circuit | "Art of Electronics" |

---

## Reference: Research Papers and Engineering Blogs

| Domain | Paper/Blog | URL | Why Read It |
|--------|-----------|-----|-------------|
| Embedded AI | "TinyML Survey 2023" | arXiv cs.LG | Overview of all edge ML techniques |
| Firmware production | Interrupt Blog | interrupt.memfault.com | What production firmware engineers do |
| Predictive maintenance | "Bearing fault detection" | search.semanticscholar.org | The ML behind SentinelGrid |
| IoT at scale | MQTT spec | mqtt.org/mqtt-specification | Understand QoS deeply |
| Graph databases | Neo4j "Graph Databases" book | neo4j.com/graph-databases-book | Free PDF |
| RAG systems | "RAG" by Lewis et al. (2020) | arxiv.org/abs/2005.11401 | Foundation of MemCore's architecture |
| SRE practices | Google SRE Book | sre.google/sre-book | Free. Read Chapters 3, 6, 13, 14 |
| Software entropy | "No Silver Bullet" by Brooks | cs.unc.edu/techreports | Why InfraMesh exists |
| Chaos Engineering | Netflix Tech Blog | netflixtechblog.com | How Netflix tests resilience |
| Time-series DBs | TimescaleDB blog | timescale.com/blog | Why TimescaleDB vs PostgreSQL |
| Edge AI embedded | Edge Impulse blog | edgeimpulse.com/blog | Real TinyML deployments |
| Firmware security | "Embedded Security" OWASP | owasp.org | Security for SentinelGrid OTA |

---

## The Non-Negotiable Daily Habit

```
Every single day, do three things:

1. LEARN: At least 1 hour of focused learning on today's topic
   (no multitasking, no YouTube in background, no phone)

2. BUILD: Write at least 10 lines of code or configuration
   (even if it is a test, a doc, a Terraform resource)

3. DOCUMENT: Commit at least one file to GitHub with a meaningful message
   "Day 47: Add Pydantic validator for service port range (1-65535)"
   "Day 112: TimescaleDB partition benchmark: 3.2s → 45ms"
   "Day 203: TFLite inference latency: 47ms average on ESP32-S3"

After 360 days, your GitHub shows 360 commits.
Each commit is proof of one day of engineering.
360 days of engineering cannot be faked.
This is your real credential.
```

DOCEOF
echo "Part 2 written: $(wc -l < /home/claude/atlassian_p2.md) lines"
Output

Part 2 written: 842 lines
Done

You are out of free messages until 11:10 AM
Upgrade





Claude is AI and can make mistakes. Please double-check responses.
