# 🚀 The Complete Engineering Mastery Roadmap
## System Design + Data Engineering + Web Development + Production Architecture
### From Absolute Zero → MNC Staff-Level Engineer
#### *Starting from: no programming, no databases, no hardware knowledge, no system design*

---

> **What This Document Is:** A unified, day-by-day engineering learning system that combines System Design, Data Engineering, Web Development, and Production Architecture into one continuous roadmap. Every day connects to the next. Every concept builds on the last. Every project is a real system that real companies built — and you will rebuild it, document it, and publish it.
>
> **Who This Is For:** Someone who cannot write a single line of code today but wants to think, build, and communicate like a Staff Engineer at Google, Uber, Meta, or Netflix within 120 days.
>
> **The Core Philosophy:** You do not learn engineering by reading about it. You learn by *building* systems, *breaking* them intentionally, *fixing* them with evidence, and *explaining* every decision in writing that a recruiter, senior engineer, or technical interviewer can evaluate.

---

## 📐 SECTION 0: THE MASTER ARCHITECTURE — Read This Before Day 1

### 🗺️ The 120-Day Learning Universe

```
╔═══════════════════════════════════════════════════════════════════════════╗
║              120-DAY COMPLETE ENGINEERING MASTERY MAP                    ║
╠═══════════════════════════════════════════════════════════════════════════╣
║                                                                           ║
║  PHASE 0 (Days 0–7):   ENGINEERING SURVIVAL KIT                          ║
║  ┌──────────────────────────────────────────────────────────────────────┐ ║
║  │ Linux Terminal │ Python │ Git + GitHub │ How the Internet Works      │ ║
║  │ Mental Models │ Documentation Setup │ Dev Environment               │ ║
║  └──────────────────────────────────────────────────────────────────────┘ ║
║                                ↓                                         ║
║  PHASE 1 (Days 8–28):  THE 20 LOGIC PATTERNS OF ALL SOFTWARE             ║
║  ┌──────────────────────────────────────────────────────────────────────┐ ║
║  │ CRUD │ Client-Server │ ETL │ Event-Driven │ Producer-Consumer        │ ║
║  │ Pub-Sub │ MapReduce │ Pipeline │ State Machine │ Caching              │ ║
║  │ Auth Flow │ Microservices │ CQRS │ Saga │ Stream Processing          │ ║
║  └──────────────────────────────────────────────────────────────────────┘ ║
║       ↓ PROJECT 1: Pattern Portfolio App — 5 Patterns Live (Day 20–28)   ║
║                                ↓                                         ║
║  PHASE 2 (Days 29–49):  WEB FOUNDATIONS + NETWORKING INTERNALS           ║
║  ┌──────────────────────────────────────────────────────────────────────┐ ║
║  │ OSI Model │ TCP/IP │ HTTP/1→3 │ DNS │ TLS │ Browser Engine           │ ║
║  │ Critical Rendering Path │ HTML Semantics │ CSS Architecture           │ ║
║  │ JavaScript Runtime │ Event Loop │ Async/Await │ Core Web Vitals       │ ║
║  └──────────────────────────────────────────────────────────────────────┘ ║
║         ↓ PROJECT 2: High-Performance Landing Page (Day 42–49)           ║
║                                ↓                                         ║
║  PHASE 3 (Days 50–70):  BACKEND ENGINEERING + DATABASES                  ║
║  ┌──────────────────────────────────────────────────────────────────────┐ ║
║  │ REST APIs │ GraphQL │ WebSockets │ SQL Deep Dive │ NoSQL              │ ║
║  │ Indexing │ Transactions │ Caching (Redis) │ Message Queues           │ ║
║  │ Security │ Auth (JWT/OAuth) │ Rate Limiting │ Schema Design           │ ║
║  └──────────────────────────────────────────────────────────────────────┘ ║
║       ↓ PROJECT 3: Food Delivery Backend (Microservices) (Day 62–70)     ║
║                                ↓                                         ║
║  PHASE 4 (Days 71–85):  DATA ENGINEERING + PIPELINES                     ║
║  ┌──────────────────────────────────────────────────────────────────────┐ ║
║  │ ETL Pipelines │ Apache Airflow │ Batch vs Stream │ Kafka              │ ║
║  │ Data Lakes │ Spark │ dbt │ Cloud Storage (S3/GCS) │ Observability    │ ║
║  │ Data Quality │ Schema Evolution │ Data Contracts                      │ ║
║  └──────────────────────────────────────────────────────────────────────┘ ║
║         ↓ PROJECT 4: Real-Time Data Platform (Day 78–85)                 ║
║                                ↓                                         ║
║  PHASE 5 (Days 86–100): DEVOPS + CLOUD + INFRASTRUCTURE                  ║
║  ┌──────────────────────────────────────────────────────────────────────┐ ║
║  │ Docker │ Kubernetes │ CI/CD │ GitHub Actions │ Infrastructure as Code│ ║
║  │ Terraform │ Helm │ Monitoring (Prometheus + Grafana) │ ELK Stack     │ ║
║  │ OpenTelemetry │ Blue-Green Deploy │ Canary Release │ SRE Principles  │ ║
║  └──────────────────────────────────────────────────────────────────────┘ ║
║       ↓ PROJECT 5: Full Production Deployment Pipeline (Day 93–100)      ║
║                                ↓                                         ║
║  PHASE 6 (Days 101–120): SYSTEM DESIGN AT SCALE                          ║
║  ┌──────────────────────────────────────────────────────────────────────┐ ║
║  │ Scalability Patterns │ CAP Theorem │ Consistent Hashing │ Sharding   │ ║
║  │ Design: Twitter │ Design: Uber │ Design: YouTube │ Design: WhatsApp  │ ║
║  │ AI in Systems │ Vector DBs │ RAG Architecture │ Production Readiness │ ║
║  └──────────────────────────────────────────────────────────────────────┘ ║
║          ↓ CAPSTONE: Full-Stack Data Platform (Day 110–120)              ║
╚═══════════════════════════════════════════════════════════════════════════╝
```

---

### 🏗️ The Grand Mental Model — What Are You Actually Building?

Before touching a computer, understand what engineering IS. Use this analogy forever:

**Engineering a Tech System is Like Building and Running a City:**

| City Element | Tech Equivalent | Phase You Learn It |
|---|---|---|
| Roads and infrastructure | Computer Networks (TCP/IP, HTTP) | Phase 2 |
| Building blueprints | System Design & Architecture | Phase 6 |
| The construction crew's workflow | Git, CI/CD, Agile | Phase 0 + 5 |
| Water, electricity supply | Databases (SQL, NoSQL) | Phase 3 |
| Mail delivery service | APIs and Message Queues | Phase 3 |
| City surveillance & sensors | Monitoring, Logging, Observability | Phase 5 |
| Logistics and supply chain | Data Pipelines (ETL, Airflow, Kafka) | Phase 4 |
| Emergency services & protocols | Error handling, Transactions, Recovery | Phase 3 |
| City expansion plans | Scalability, Sharding, CAP Theorem | Phase 6 |
| City management software | Operating Systems, Linux | Phase 0 |
| Transport patterns (bus routes, metro) | The 20 Logic Patterns | Phase 1 |

**Why this order?** You cannot design a city's expansion plan if you don't know how roads or water pipes work. You cannot design a distributed system if you don't know how HTTP or databases work. Every phase is a prerequisite for the next.

---

## 🛠️ COMPLETE FREE TECH STACK — Justified

### Why Every Tool Was Chosen

| Category | Tool Chosen | Why This Tool Specifically | MNC That Uses It | Cost |
|---|---|---|---|---|
| **OS** | Ubuntu 24.04 LTS | All cloud servers. Industry default. Linux skills = universal. | Google, Amazon, Netflix | Free |
| **Language** | Python 3.12 | Fastest to learn. Data engineering standard. Excellent for systems simulation. | Everywhere | Free |
| **Frontend** | Vanilla JS → React 18 | Learn foundations before frameworks. React is MNC standard. | Meta, Airbnb, Netflix | Free |
| **Backend** | Node.js (Express/Fastify) | Same language (JS) as frontend, excellent for API servers, event-driven. | LinkedIn, Uber, Netflix | Free |
| **SQL Database** | PostgreSQL 16 | Most powerful open-source RDBMS. Used at Instagram, Notion, Stripe. | Everywhere | Free |
| **NoSQL Cache** | Redis 7 | Fastest in-memory store. Industry default cache. | Twitter, GitHub, Pinterest | Free |
| **NoSQL Document** | MongoDB 7 | Dominant document store. Flexible schema. | Expedia, Adobe | Free |
| **Message Queue** | Apache Kafka | Industry standard for event streaming. Powers LinkedIn, Uber, Netflix. | LinkedIn, Uber, Netflix | Free |
| **Data Pipeline** | Apache Airflow | Industry standard workflow orchestrator. Used at Airbnb (invented it), Google. | Airbnb, Google, Robinhood | Free |
| **Distributed Processing** | Apache Spark | Standard for big data. PySpark is the MNC data engineering language. | Amazon, IBM, JPMorgan | Free |
| **Containerization** | Docker | Non-negotiable. Every company uses containers. | Universal | Free |
| **Orchestration** | Kubernetes (Minikube locally) | Cloud-native standard. Kubernetes skills = premium salary. | Google, Amazon, Microsoft | Free |
| **CI/CD** | GitHub Actions | Simplest professional CI/CD. Integrated with GitHub portfolio. | Microsoft, thousands of startups | Free |
| **IaC** | Terraform | Standard for infrastructure as code. Universal cloud tool. | HashiCorp users = 99% of MNCs | Free |
| **Monitoring** | Prometheus + Grafana | The gold standard monitoring stack. Open-source version used everywhere. | Soundcloud, Grafana Labs clients | Free |
| **Logging** | ELK Stack (Elasticsearch, Logstash, Kibana) | Standard log aggregation. | Elastic customers = 70% of Fortune 500 | Free |
| **Tracing** | OpenTelemetry + Jaeger | Vendor-neutral distributed tracing standard. Backed by CNCF. | Google, Microsoft, AWS | Free |
| **Version Control** | Git + GitHub | Non-negotiable. Everything. | Universal | Free |
| **API Documentation** | Swagger/OpenAPI | Industry-standard API documentation format. | Used in every API-first company | Free |
| **Data Transformation** | dbt (data build tool) | Standard SQL-first data transformation. Used at every modern data team. | GitLab, JetBlue, Autotrader | Free |
| **Vector DB** | Qdrant (self-hosted) | Best open-source vector database. Used for AI features. | Emerging standard | Free |
| **Local AI** | Ollama + LLaMA 3 | Run AI locally. No API costs. | Alternative to OpenAI APIs | Free |
| **Blog** | Dev.to + Hashnode | Technical writing. Google-indexed. Recruiters find these. | Career tool | Free |
| **Diagrams** | draw.io (diagrams.net) | Free, professional system design diagrams. Industry-used format. | Free | Free |

---

## 📝 THE DOCUMENTATION INTELLIGENCE SYSTEM

### How Recruiters and Engineers Actually Verify Your Work

> Standard advice says "put it on GitHub and LinkedIn." That is incomplete. **The right documentation depends on what you built.**

Here is the full mapping system — for each type of work you produce:

---

### 🗺️ Project Type → Documentation Strategy Map

#### TYPE A: Networking / Infrastructure Projects
**What you build:** Network topology, packet analysis, TCP/IP experiments, DNS resolution, TLS handshake analysis

**How recruiters verify it:** They want to see that you ran real tools, captured real data, and can interpret real artifacts — not that you read about networking.

| Documentation Element | Platform | Why |
|---|---|---|
| **Wireshark packet captures (.pcap files)** | GitHub repo + README | Shows you actually captured traffic, not just read about it |
| **Network topology diagrams** | draw.io → exported PNG in GitHub | Demonstrates system thinking |
| **Annotated terminal outputs** | GitHub `experiments/` folder | Shows hands-on execution |
| **Performance metrics (latency, throughput)** | Grafana screenshot or markdown table | Shows measurement mindset |
| **Written explanation: "What I saw and why"** | Hashnode blog post | Long-form understanding proof |
| **Before/After comparisons** | README with screenshots | Shows engineering intuition |

**LinkedIn Post Format for Networking:**
```
"I ran Wireshark to capture the TLS handshake between my browser 
and google.com. Here's what I found: [3-4 specific observations with 
screenshot]. This is why HTTP/3 is different: [specific technical point].
Full analysis: [Hashnode link] | .pcap file: [GitHub link]
#NetworkEngineering #TLS #DistributedSystems"
```

---

#### TYPE B: Backend / API Projects
**What you build:** REST APIs, GraphQL servers, authentication systems, microservices

**How recruiters verify it:** They want a deployed API they can actually hit, API docs they can read, and tests they can run.

| Documentation Element | Platform | Why |
|---|---|---|
| **Live deployed API** | Railway.app or Render.com (free tier) | Recruiters can test it without cloning |
| **Swagger/OpenAPI docs** | Auto-generated, deployed with the app | Professional standard |
| **Postman Collection** | Exported JSON in GitHub | Shows API design competence |
| **Load test results** | k6 or Apache Bench output in README | Shows performance awareness |
| **Architecture Decision Records (ADRs)** | `docs/decisions/` folder in GitHub | Shows senior-level thinking |
| **Schema evolution changelog** | `CHANGELOG.md` in GitHub | Shows production mindset |
| **Test coverage report** | GitHub Actions artifact or README badge | Shows quality engineering |

**README Structure for Backend Projects:**
```markdown
## Architecture
[Diagram showing services, databases, message queues]

## API Documentation
[Link to live Swagger docs]

## Performance Benchmarks
| Endpoint | Avg Latency | p99 Latency | RPS |
|----------|------------|------------|-----|
| GET /users | 12ms | 45ms | 1200 |

## Decisions Made
- Why PostgreSQL over MongoDB: [link to ADR-001]
- Why JWT over sessions: [link to ADR-002]

## How to Run
[Single docker-compose up command]

## Test Coverage
![Coverage](badge_url) 87% coverage
```

---

#### TYPE C: Data Engineering / Pipeline Projects
**What you build:** ETL pipelines, Airflow DAGs, Kafka streams, Spark jobs, data warehouses

**How recruiters verify it:** They want to see the pipeline architecture, execution logs, data quality checks, and the dashboard that proves the data arrived correctly.

| Documentation Element | Platform | Why |
|---|---|---|
| **Airflow DAG graph screenshot** | GitHub README | Shows pipeline architecture visually |
| **Pipeline execution logs** | GitHub (sanitized log files) | Shows it actually ran |
| **Grafana dashboard screenshot** | GitHub README | Shows data arrived and metrics tracked |
| **Data quality report** | Markdown table in README | Shows production engineering mindset |
| **Row counts before/after** | Embedded in README | Proves data integrity |
| **Architecture diagram (source → sink)** | draw.io in GitHub | Demonstrates end-to-end thinking |
| **dbt model documentation** | dbt docs generate → GitHub Pages | Industry-specific credential |
| **Blog post: "What broke and how I fixed it"** | Dev.to | Shows debugging skill and honesty |

**GitHub Repo Structure for Data Projects:**
```
data-platform/
├── dags/                    ← Airflow DAG definitions
├── transformations/         ← dbt models
├── pipelines/               ← Spark/Python pipeline code
├── tests/                   ← Data quality tests
├── docs/
│   ├── architecture.md      ← Source-to-sink diagram
│   ├── data-dictionary.md   ← What every field means
│   └── runbooks/            ← How to operate this system
├── dashboards/              ← Exported Grafana JSON
├── benchmarks/              ← Performance measurements
└── CHANGELOG.md
```

---

#### TYPE D: DevOps / Infrastructure Projects
**What you build:** Docker images, Kubernetes deployments, CI/CD pipelines, Terraform configs, monitoring stacks

**How recruiters verify it:** They want to see the pipeline running (GitHub Actions screenshot), the Kubernetes cluster running (kubectl describe output), and the monitoring dashboard.

| Documentation Element | Platform | Why |
|---|---|---|
| **GitHub Actions run screenshot** | GitHub README | Shows CI/CD is real and working |
| **Kubernetes deployment YAML files** | GitHub | Shows IaC competence |
| **Terraform plan output** | GitHub (sanitized) | Shows IaC best practices |
| **Grafana dashboard screenshot** | GitHub README | Shows observability awareness |
| **Prometheus metrics query examples** | GitHub | Shows monitoring depth |
| **Docker image sizes (before/after optimization)** | GitHub README table | Shows performance mindset |
| **Deployment runbook** | `docs/runbooks/deploy.md` | Shows operational maturity |
| **Security scan results** (Trivy) | GitHub Actions output | Shows security awareness |

---

#### TYPE E: System Design / Architecture Work
**What you build:** Architecture diagrams, capacity calculations, tradeoff analyses, design documents

**How recruiters verify it:** They want to see your THINKING, not just the final diagram. The reasoning, tradeoffs considered, and alternatives rejected are the proof.

| Documentation Element | Platform | Why |
|---|---|---|
| **System design document (full)** | GitHub wiki or `docs/designs/` | Long-form engineering thinking proof |
| **Architecture diagram** | draw.io → GitHub | Visual communication skill |
| **Capacity estimation spreadsheet** | GitHub (exported CSV) | Shows quantitative thinking |
| **Tradeoffs table** | Markdown table in design doc | Shows maturity |
| **"Why not X?" section** | Part of the design doc | Demonstrates breadth of knowledge |
| **Blog post: Design walkthrough** | Hashnode or Dev.to | Teaching = deepest proof of understanding |
| **YouTube/Loom walkthrough video** | YouTube (unlisted) linked in GitHub | Shows communication skill |

**System Design Document Template:**
```markdown
# System Design: [System Name]

## Problem Statement
[What problem does this solve? Who uses it? At what scale?]

## Requirements
### Functional
- [What it must do]
### Non-Functional
- Target: X requests/second, Y ms p99 latency, Z% availability

## Capacity Estimation
- Daily active users: X million
- Read/Write ratio: X:1
- Storage needed: X TB/year
- Bandwidth: X GB/s peak

## High-Level Architecture
[diagram]

## Component Deep Dives
[Each major component, its internal design, and why this choice]

## Alternatives Considered
| Alternative | Why Rejected |
|-------------|-------------|
| [Option A] | [Specific tradeoff] |

## Open Questions
[What I still don't know]
```

---

#### TYPE F: Full-Stack / Product Projects
**What you build:** Web applications, APIs, databases, deployment — all together

**How recruiters verify it:** They want a live URL they can click, a clean codebase they can read, and proof the whole thing is actually running.

| Documentation Element | Platform | Why |
|---|---|---|
| **Live demo URL** | Vercel/Netlify (frontend) + Railway (backend) | They can use it without asking |
| **Loom/YouTube demo video (3–5 min)** | YouTube unlisted, linked in GitHub | Shows polish and communication |
| **GitHub with clean README** | GitHub | Starting point for every recruiter |
| **Performance audit** | Lighthouse score screenshot in README | Shows quality consciousness |
| **Architecture overview** | README section with diagram | Shows system thinking |
| **Known limitations** | README section | Shows engineering honesty and maturity |

---

### The Master Documentation Platform Decision Tree

```
What did you build?
│
├── Network experiment or infrastructure design?
│   → GitHub (packet captures, topology diagrams) + Hashnode (analysis post)
│
├── Backend API or microservice?
│   → GitHub + Railway/Render (live API) + Swagger docs + Dev.to blog
│
├── Data pipeline or ETL?
│   → GitHub (dbt docs + pipeline code) + Grafana screenshots + Hashnode
│
├── DevOps / CI/CD / Kubernetes?
│   → GitHub (YAML, Terraform, Actions screenshots) + Dev.to post
│
├── System design / architecture?
│   → GitHub (design docs) + Hashnode (walkthrough post) + YouTube (video)
│
└── Full-stack product?
    → GitHub + Vercel/Railway (live) + Loom/YouTube demo + Dev.to
```

---

### The Daily Documentation Ritual (Non-Negotiable)

Every single day, after studying, write this in your GitHub repo `phase-X/day-XX.md`:

```markdown
# Day XX — [Concept Name]

## 🎯 What I Studied
[One paragraph in plain English]

## 🧠 My Mental Model
[Explain it as if teaching a 10-year-old. This is the hardest part.
 If you can't do this, you didn't understand it yet.]

## 💻 What I Built / Ran
```bash
[actual command you ran]
```
[actual output — paste it, don't describe it]

## 🔗 How This Connects to Yesterday
[One sentence. Forces continuity in your thinking.]

## 🏭 Where I've Seen This in the Real World
[Google does X. Uber uses Y. Netflix solved Z this way.]

## ❓ Active Recall (Answer Tomorrow Without Notes)
1. [question]
2. [question]
3. [question]

## 🐛 What I Got Wrong or Confused About
[One honest observation. This builds credibility.]

## 📊 Evidence
[Screenshot, terminal output, or commit link]
```

**The LinkedIn rhythm:** Post every 3 days. Use the domain-specific template from the section above. Always include one specific technical insight, one proof artifact (screenshot or link), and always tag 3–5 relevant hashtags.

---

---

# 🟡 PHASE 0: ENGINEERING SURVIVAL KIT (Days 0–7)

> **Goal:** Get the tools working. Understand what a computer actually does. Speak to it through a terminal.
>
> **Hardware → Software Bridge:** Your computer has a CPU (brain), RAM (short-term memory), and a Disk (long-term memory). When you write code, it goes from your editor (disk) → into RAM when the program runs → processed by the CPU → output displayed. Everything you learn builds on this.

---

## Day 0: Environment Setup + The Mental Model

### What You Need to Understand Before Installing Anything

A computer is a machine that follows instructions. Those instructions are stored in files. Files live on a disk. When you run a file (a program), the CPU reads it from disk into RAM and executes it.

An **Operating System (OS)** is the software that manages this: who gets CPU time, how memory is divided, how programs open files. Linux is the OS of every server on the internet. Learning Linux = learning the language of servers.

### Installation Checklist

```bash
# If you're on Windows: Install WSL2 (Windows Subsystem for Linux)
# Search: "Install WSL2 Ubuntu" → follow Microsoft docs

# If you're on Mac: You already have a Unix terminal (iTerm2 recommended)
# If you're on a PC: Install Ubuntu 24.04 directly or in VirtualBox

# === After opening your Linux terminal ===

# Update software package list
sudo apt update && sudo apt upgrade -y

# Install every tool you'll use in the next 120 days
sudo apt install -y \
    git \
    python3 \
    python3-pip \
    nodejs \
    npm \
    docker.io \
    docker-compose \
    vim \
    curl \
    wget \
    htop \
    net-tools \
    postgresql-client \
    redis-tools \
    jq \
    tree

# Python libraries for data work
pip3 install \
    requests \
    pandas \
    psycopg2-binary \
    sqlalchemy \
    redis \
    kafka-python \
    apache-airflow \
    pyspark

# Verify each tool installed
git --version
python3 --version
node --version
docker --version
```

### The Five Commands That Run Everything

```bash
# 1. Where am I?
pwd

# 2. What's here?
ls -la

# 3. Move somewhere
cd Documents

# 4. Make a folder
mkdir my-project

# 5. Run a file
python3 my_script.py
```

### Create Your GitHub Repository

```bash
# Set up Git identity
git config --global user.name "Your Name"
git config --global user.email "you@email.com"

# Create your master portfolio repository
mkdir ~/engineering-mastery-journey
cd ~/engineering-mastery-journey
git init
echo "# 120-Day Engineering Mastery Journey" > README.md
echo "Started: $(date)" >> README.md
git add README.md
git commit -m "Day 0: The journey begins"
```

### 📝 Day 0 Documentation Task
- Create GitHub account → create repo `engineering-mastery-journey`
- First LinkedIn post: "Day 0 of my 120-day engineering journey. Goal: build production-grade systems from scratch. Starting today with a Linux terminal and no prior experience. #BuildInPublic #EngineeringJourney"

---

## Day 1: Linux Terminal — The Language of Servers

### Why Linux Is Not Optional
Every database server, every cloud virtual machine, every Kubernetes node, every CI/CD runner runs Linux. When you SSH into an AWS EC2 instance, you get a Linux terminal. When you `kubectl exec` into a pod, you get a Linux shell. The terminal is not just a tool — it is the primary interface of production systems.

### Core Linux Commands (With Why Each Matters to Engineers)

```bash
# ===== FILE SYSTEM NAVIGATION =====
pwd                     # Where are you? (print working directory)
ls -la                  # List ALL files including hidden ones, with details
cd /var/log             # Go to the system log folder (where servers write errors)
cd ~                    # Go home
cd -                    # Go back to previous location

# ===== FILES AND CONTENT =====
cat /etc/os-release     # Read a file (useful for checking system info)
head -20 /var/log/syslog    # Read first 20 lines (useful for logs)
tail -f /var/log/syslog     # LIVE view of a log file (follow mode)
                            # ↑ THIS is how engineers debug running servers
grep "ERROR" /var/log/syslog    # Find specific text in a file
grep -r "TODO" ~/my-project/    # Find text in ALL files in a folder

# ===== PIPES: The Most Powerful Concept in Linux =====
# A pipe (|) takes output of one command and feeds it to the next
ps aux | grep "python"          # List all processes, filter to Python ones
cat /var/log/syslog | grep "ERROR" | tail -50   # Last 50 errors in log
ls -la | sort -k5 -n | tail    # List files, sort by size, show biggest

# ===== PROCESSES =====
ps aux                  # Show all running processes
top                     # Live view (like Task Manager) — press q to quit
htop                    # Better live view
kill 12345              # Stop process with ID 12345
kill -9 12345           # Force stop (when normal kill doesn't work)

# ===== NETWORKING =====
curl https://api.github.com         # Make an HTTP GET request (like a browser)
curl -I https://google.com          # Get only HTTP headers (useful for debugging)
ping google.com                     # Test if a host is reachable
netstat -tlpn                       # What ports are open on this machine?
                                    # ↑ Critical for debugging "why can't I connect?"

# ===== PERMISSIONS =====
chmod +x myscript.sh    # Make a file executable (runnable)
sudo                    # Run as administrator (super user do)
                        # ↑ Never use sudo carelessly — it's like being root in your OS
```

### Assignment: Investigate Your Own System

```bash
# Answer these questions using Linux commands (no Googling the answers):
# 1. How much RAM does your system have?
cat /proc/meminfo | grep MemTotal

# 2. How many CPU cores?
nproc

# 3. What processes are using the most CPU right now?
ps aux --sort=-%cpu | head -10

# 4. What is your system's IP address?
ip addr show | grep inet

# 5. What is listening on port 5432 (PostgreSQL)?
sudo netstat -tlpn | grep 5432
```

### 📝 Day 1 Documentation
- In `phase-0-survival/day-01.md`: Include actual output of each command above
- Write: "The `tail -f` command matters for engineers because ___"

---

## Day 2: Python Foundations — Your Engineering Swiss Army Knife

### Why Python First (Not JavaScript, Not Java)

Python is: (a) easiest to read and write for beginners, (b) the dominant language in data engineering, (c) used for scripting, automation, and prototyping at every MNC, (d) excellent for learning programming concepts without syntax noise.

### Python as Systems Thinking Tool

```python
# Save as: phase-0-survival/systems_thinking.py
# Python is how we simulate system concepts before implementing them

# ===== VARIABLES AND TYPES =====
server_name = "web-server-01"      # String
port = 8080                        # Integer  
cpu_usage = 45.7                   # Float (decimal)
is_healthy = True                  # Boolean
requests_per_second = 12500        # Integer

print(f"Server: {server_name} | Port: {port} | CPU: {cpu_usage}% | RPS: {requests_per_second}")

# ===== LISTS = Ordered queues (like a request queue) =====
request_queue = ["user_A", "user_B", "user_C", "user_D"]
request_queue.append("user_E")         # New request arrives
next_to_process = request_queue.pop(0) # First-In, First-Out (FIFO)
print(f"Processing: {next_to_process} | Queue: {request_queue}")

# ===== DICTIONARIES = Lookup tables (like a database record) =====
user_database = {
    "user_001": {"name": "Alice", "email": "alice@example.com", "role": "admin"},
    "user_002": {"name": "Bob",   "email": "bob@example.com",   "role": "viewer"},
    "user_003": {"name": "Carol", "email": "carol@example.com", "role": "editor"},
}

# Simulate a database lookup
def find_user(user_id):
    user = user_database.get(user_id)
    if user:
        return f"Found: {user['name']} ({user['role']})"
    return "User not found"

print(find_user("user_001"))
print(find_user("user_999"))

# ===== LOOPS = Processing multiple items (like processing messages in a queue) =====
print("\n=== Active Users Report ===")
for user_id, user_data in user_database.items():
    status = "✅ Admin" if user_data["role"] == "admin" else "👤 User"
    print(f"  {user_id}: {user_data['name']} {status}")

# ===== FUNCTIONS = Reusable logic blocks =====
def calculate_server_load(requests, capacity):
    """
    Calculate server load percentage.
    If > 80%, alert needed.
    """
    load_percent = (requests / capacity) * 100
    status = "⚠️ HIGH" if load_percent > 80 else "✅ OK"
    return load_percent, status

load, status = calculate_server_load(9500, 10000)
print(f"\nServer Load: {load:.1f}% — {status}")
```

### Active Recall Questions (Answer Without Notes)
1. What is the difference between a list and a dictionary in Python?
2. Why would a request queue use FIFO (pop from position 0)?
3. What does `f"hello {name}"` do differently from `"hello " + name`?

### 📝 Day 2 Documentation
- Push `systems_thinking.py` to GitHub
- Write in `day-02.md`: "I modeled a user database using a dictionary because ___. A list is better for ___ and a dictionary is better for ___."

---

## Day 3: Git — Your Engineering Time Machine

### Why Git Is Not Just "Version Control"

Git is how engineers:
- Collaborate without overwriting each other's work
- Roll back mistakes in production
- Review each other's code before it ships
- Track the history of every decision ever made in a codebase
- Prove to recruiters that they actually wrote the code

Without Git, none of the above is possible. With Git, you have a time machine.

### Git Internals — What's Actually Happening

```bash
# === Git stores your project as a directed graph of snapshots ===

# Start fresh
mkdir git-experiment && cd git-experiment
git init

# Create a file
echo "First version of my API" > api.py
git add api.py           # Stage: tell Git "I want to save this"
git status               # What does Git know about?
git commit -m "feat: initial API structure"   # Save snapshot

# See what Git stores internally
ls -la .git/             # The entire repository lives here
ls .git/objects/         # Every version of every file, content-addressed

# Make a change
echo "Added authentication endpoint" >> api.py
git diff                 # What changed since last commit?
git add api.py
git commit -m "feat: add authentication endpoint"

# See the history
git log --oneline        # Clean list of snapshots
git log --graph          # Shows branching structure
```

### The Professional Git Workflow (Used at Every MNC)

```bash
# === TRUNK-BASED DEVELOPMENT (used at Google, Meta) ===

# Never commit directly to main. Always work on a branch.
git checkout -b feature/add-user-auth      # Create and switch to new branch

# ... do your work ...
git add .
git commit -m "feat(auth): implement JWT token generation"
                          ↑ Conventional Commits format:
                          # feat: new feature
                          # fix: bug fix
                          # docs: documentation
                          # refactor: code restructure
                          # test: adding tests
                          # chore: maintenance

# Push branch to GitHub
git push origin feature/add-user-auth

# On GitHub: Create a Pull Request → Code Review → Merge to main
```

### Practical Git Commands for Daily Use

```bash
# The seven commands you use every day:
git status              # What's changed?
git add .               # Stage everything
git commit -m "message" # Save snapshot
git push                # Upload to GitHub
git pull                # Download latest from GitHub
git log --oneline       # See history
git diff                # What changed?

# Recovery commands (when things go wrong):
git stash               # Temporarily hide changes
git stash pop           # Bring them back
git reset HEAD~1        # Undo last commit (keep changes)
git revert abc1234      # Undo a commit safely (creates new commit)
```

### Assignment: Git Bisect — Find the Bug
```bash
# Git bisect uses binary search to find which commit introduced a bug
# This is used in real production incident investigations

git bisect start
git bisect bad HEAD              # Current version is broken
git bisect good v1.0.0           # This version was fine
# Git automatically checks out commits for you to test
# You run your test, then say:
git bisect good    # OR
git bisect bad
# Git narrows down to the exact commit that broke things
```

### 📝 Day 3 Documentation
- Screenshot your `git log --graph` output → add to `day-03.md`
- Blog post draft: "What Git Actually Stores: A Visual Guide"
- LinkedIn: "TIL that Git stores every version of your code as a content-addressed hash. If two files have the same content, Git stores them once. It's basically a blockchain for your code. [screenshot] #Git #EngineeringJourney"

---

## Day 4: How the Internet Actually Works

### The Journey of a URL

When you type `https://www.netflix.com` and press Enter, 47 distinct technical steps happen before you see the page. Understanding all 47 is what separates a web developer from a systems engineer.

Here are the most important ones:

```
YOUR KEYBOARD → BROWSER → OS → NETWORK → DNS → TCP → TLS → HTTP → SERVER → DATABASE → RESPONSE → RENDER

Step 1: Browser checks its own DNS cache
        "Have I visited netflix.com before? Do I remember the IP?"
        
Step 2: If not cached → Ask OS → OS asks DNS Resolver
        (DNS = Phone book: "netflix.com" → "54.77.143.12")
        
Step 3: OS establishes TCP connection to IP 54.77.143.12:443
        THREE-WAY HANDSHAKE:
        Client → Server: "SYN" (I want to connect)
        Server → Client: "SYN-ACK" (OK, I'm ready)
        Client → Server: "ACK" (Great, let's go)
        
Step 4: TLS Handshake (encryption negotiation)
        Client → Server: "Hello, here's what encryption I support"
        Server → Client: "Here's my certificate (identity proof)"
        Both: "Agree on a shared secret key"
        All further communication is encrypted
        
Step 5: HTTP/2 GET request sent
        "GET / HTTP/2
        Host: netflix.com
        Accept-Language: en-US
        ..."
        
Step 6: Netflix's load balancer receives it, routes to a server
Step 7: Server queries database/cache for your user data
Step 8: Response sent back through the same TCP connection
Step 9: Browser receives HTML, CSS, JavaScript
Step 10: Browser renders the page (we study this in Phase 2)
```

### Observe This Yourself

```bash
# See DNS lookup in action
dig netflix.com           # What IP does this domain resolve to?
dig +trace google.com     # See the ENTIRE DNS resolution chain (root → TLD → domain)

# See TCP connection
curl -v https://google.com 2>&1 | head -50
# Look for: * Connected to google.com (IP) port 443
# Look for: * TLSv1.3

# Measure each step's timing
curl -w "\n--- Timing ---\n\
DNS Lookup:       %{time_namelookup}s\n\
TCP Connect:      %{time_connect}s\n\
TLS Handshake:    %{time_appconnect}s\n\
First Byte:       %{time_starttransfer}s\n\
Total:            %{time_total}s\n" \
-o /dev/null -s https://netflix.com
```

### The OSI Model — 7 Layers of the Network

```
Layer 7: APPLICATION  → HTTP, HTTPS, DNS, SMTP (what your app uses)
Layer 6: PRESENTATION → SSL/TLS encryption, compression
Layer 5: SESSION      → Managing connections (sessions)
Layer 4: TRANSPORT    → TCP (reliable) or UDP (fast)
Layer 3: NETWORK      → IP routing (how to get to 54.77.143.12)
Layer 2: DATA LINK    → MAC addresses, Ethernet frames
Layer 1: PHYSICAL     → Actual electrical signals, fiber optic light

Why engineers care:
- When debugging: "Is this a network error? Which layer?"
- When designing: "Should I use TCP or UDP? What tradeoffs?"
- When optimizing: "Why is TTFB slow? DNS? TCP? TLS?"
```

### Active Recall Questions
1. Why does a TLS handshake happen AFTER a TCP handshake?
2. What is the difference between TCP and UDP? When would you choose UDP?
3. If a user says "the website is slow," how would you determine if it's DNS, TCP, TLS, or server processing time?

### 📝 Day 4 Documentation
- In `day-04.md`: Paste your `curl -w` timing output and analyze each number
- Write: "The slowest step for me was ___. This is because ___."

---

## Days 5–7: Python Deep Dive — Data Structures and File I/O

### The Engineer's Python Toolkit

```python
# Save as: phase-0-survival/engineer_toolkit.py

import json
import csv
import time
from collections import defaultdict, Counter
from datetime import datetime

# ===== READING DATA (APIs return JSON, databases return tables) =====

# Simulate reading an API response (JSON format)
api_response_json = '''
{
  "status": "success",
  "data": {
    "users": [
      {"id": 1, "name": "Alice", "country": "India", "active": true},
      {"id": 2, "name": "Bob",   "country": "USA",   "active": false},
      {"id": 3, "name": "Carol", "country": "India", "active": true},
      {"id": 4, "name": "Dave",  "country": "UK",    "active": true}
    ]
  }
}
'''

data = json.loads(api_response_json)    # Parse JSON string into Python dict
users = data["data"]["users"]

# Filter active users
active_users = [u for u in users if u["active"]]
print(f"Active users: {len(active_users)}")

# Count users by country
country_counts = Counter(u["country"] for u in users)
print(f"Users by country: {dict(country_counts)}")

# ===== WRITING DATA (Saving results) =====
with open("output_report.json", "w") as f:
    json.dump({
        "generated_at": datetime.now().isoformat(),
        "total_users": len(users),
        "active_users": len(active_users),
        "by_country": dict(country_counts)
    }, f, indent=2)

print("Report saved to output_report.json")

# ===== ERROR HANDLING (Critical for production code) =====
def safe_fetch_user(user_id, database):
    """
    Always wrap potentially-failing operations in try/except.
    Production code must NEVER crash without handling the error.
    """
    try:
        user = database[user_id]
        return user
    except KeyError:
        print(f"Warning: User {user_id} not found in database")
        return None
    except Exception as e:
        print(f"Unexpected error fetching user {user_id}: {e}")
        return None

# ===== PERFORMANCE MEASUREMENT =====
def time_operation(func, *args):
    """Measure how long an operation takes."""
    start = time.perf_counter()
    result = func(*args)
    elapsed = time.perf_counter() - start
    return result, elapsed

def slow_search_users(query, users):
    """O(n) linear search — checks every user"""
    return [u for u in users if query.lower() in u["name"].lower()]

result, elapsed = time_operation(slow_search_users, "alice", users)
print(f"Search found {len(result)} users in {elapsed*1000:.3f}ms")
```

### Day 7: Shell Scripting — Automating Engineering Tasks

```bash
#!/bin/bash
# Save as: phase-0-survival/daily_health_check.sh
# Run with: chmod +x daily_health_check.sh && ./daily_health_check.sh

echo "======================================"
echo "SYSTEM HEALTH CHECK - $(date)"
echo "======================================"

# CPU Usage
CPU_USAGE=$(top -bn1 | grep "Cpu(s)" | awk '{print $2}' | cut -d. -f1)
echo "CPU Usage: ${CPU_USAGE}%"
if [ "$CPU_USAGE" -gt 80 ]; then
    echo "⚠️  WARNING: High CPU usage!"
fi

# Memory Usage
MEM_TOTAL=$(free -m | awk 'NR==2{print $2}')
MEM_USED=$(free -m | awk 'NR==2{print $3}')
MEM_PERCENT=$((MEM_USED * 100 / MEM_TOTAL))
echo "Memory: ${MEM_USED}MB / ${MEM_TOTAL}MB (${MEM_PERCENT}%)"

# Disk Usage
DISK_USAGE=$(df -h / | awk 'NR==2{print $5}' | cut -d% -f1)
echo "Disk Usage: ${DISK_USAGE}%"
if [ "$DISK_USAGE" -gt 90 ]; then
    echo "⚠️  WARNING: Disk almost full!"
fi

# Check if PostgreSQL is running
if systemctl is-active --quiet postgresql; then
    echo "✅ PostgreSQL: Running"
else
    echo "❌ PostgreSQL: Not Running"
fi

echo "======================================"
echo "Health check complete."
```

### 📝 Phase 0 Completion Checklist

- [ ] Linux terminal: can navigate, search, pipe, monitor processes
- [ ] Python: can write functions, work with JSON, handle errors
- [ ] Git: can commit, branch, push, and use conventional commits
- [ ] Networking: understand DNS → TCP → TLS → HTTP flow
- [ ] GitHub repo created and active
- [ ] First blog post published (Dev.to or Hashnode)
- [ ] LinkedIn post done with a specific technical insight

---

---

# 🔵 PHASE 1: THE 20 LOGIC PATTERNS OF ALL SOFTWARE (Days 8–28)

> **The Most Important Insight in This Entire Roadmap:** Every piece of software ever built — from Netflix's recommendation engine to a hospital's patient record system to your bank's payment processor — is built by combining and remixing 20 fundamental logic flow patterns. Learn these 20 patterns and you can understand, design, or debug virtually any system.
>
> **How to learn a pattern:** (1) Understand the abstract flow. (2) Find it in a real product you use. (3) Build a tiny version of it. (4) Document what you built and why.

---

## The 20 Patterns: Overview

```
┌─────────────────────────────────────────────────────────────────────────┐
│              THE 20 FUNDAMENTAL ENGINEERING PATTERNS                    │
├─────────────────────────────────────────────────────────────────────────┤
│                                                                         │
│  TIER 1: FOUNDATION (Learn first — everything else uses these)          │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │ 1. CRUD        │ 2. Client-Server   │ 3. ETL             │        │ │
│  │ 4. Auth Flow   │ 5. Caching         │ 6. State Machine   │        │ │
│  └────────────────────────────────────────────────────────────────────┘ │
│                                                                         │
│  TIER 2: ASYNC (Events and concurrency)                                 │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │ 7. Event-Driven      │ 8. Producer-Consumer  │ 9. Pub/Sub         │ │
│  │ 10. Observer         │ 11. Batch Processing  │ 12. Stream Proc.   │ │
│  └────────────────────────────────────────────────────────────────────┘ │
│                                                                         │
│  TIER 3: SCALE (Distributed systems)                                    │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │ 13. MapReduce        │ 14. Pipeline         │ 15. Microservices   │ │
│  │ 16. CQRS             │ 17. Saga Pattern      │ 18. Sharding        │ │
│  └────────────────────────────────────────────────────────────────────┘ │
│                                                                         │
│  TIER 4: AI ERA (2025 and beyond)                                       │
│  ┌────────────────────────────────────────────────────────────────────┐ │
│  │ 19. ML Workflow (Train→Deploy→Serve)  │ 20. RAG Architecture      │ │
│  └────────────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────────────┘
```

---

## Days 8–9: PATTERN 1 — CRUD (The Foundation of All Data Apps)

### What It Is

**CRUD = Create, Read, Update, Delete.** Every app that stores and retrieves data uses CRUD. A hospital's patient records. A bank's accounts. Twitter's tweets. Instagram's photos.

```
CREATE: Add new data
   User signs up → create new user record

READ: Retrieve data
   User opens their profile → read their record

UPDATE: Change existing data
   User changes profile picture → update their record

DELETE: Remove data
   User deletes their account → delete their record
```

### Where You See It Every Day

| App | Create | Read | Update | Delete |
|---|---|---|---|---|
| Gmail | Send email | Open email | Mark as read | Delete email |
| Instagram | Post photo | View feed | Edit caption | Delete post |
| Amazon | Place order | View order | Cancel order | N/A |
| Spotify | Create playlist | Play song | Edit playlist | Remove song |
| GitHub | Create repo | View code | Edit file | Delete repo |

### Build It: A Simple To-Do App Backend

```python
# Save as: phase-1-patterns/01-crud/todo_api.py
# A minimal CRUD API using Python dictionaries (no database yet)

from datetime import datetime

# Our "database" for now (a Python dictionary)
todos = {}
next_id = 1

def create_todo(title, description=""):
    """CREATE: Add a new to-do item"""
    global next_id
    todo = {
        "id": next_id,
        "title": title,
        "description": description,
        "completed": False,
        "created_at": datetime.now().isoformat(),
        "updated_at": datetime.now().isoformat()
    }
    todos[next_id] = todo
    next_id += 1
    print(f"✅ Created: #{todo['id']} — {title}")
    return todo

def read_todo(todo_id):
    """READ: Get a specific to-do"""
    todo = todos.get(todo_id)
    if todo:
        print(f"📖 Todo #{todo_id}: {todo['title']} ({'Done' if todo['completed'] else 'Pending'})")
        return todo
    print(f"❌ Todo #{todo_id} not found")
    return None

def read_all_todos():
    """READ: Get all to-dos"""
    print(f"\n📋 All Todos ({len(todos)} total):")
    for todo_id, todo in todos.items():
        status = "✓" if todo["completed"] else "○"
        print(f"  [{status}] #{todo_id}: {todo['title']}")
    return list(todos.values())

def update_todo(todo_id, title=None, completed=None):
    """UPDATE: Modify an existing to-do"""
    todo = todos.get(todo_id)
    if not todo:
        print(f"❌ Todo #{todo_id} not found")
        return None
    if title is not None:
        todo["title"] = title
    if completed is not None:
        todo["completed"] = completed
    todo["updated_at"] = datetime.now().isoformat()
    print(f"✏️  Updated: #{todo_id}")
    return todo

def delete_todo(todo_id):
    """DELETE: Remove a to-do"""
    if todo_id in todos:
        deleted = todos.pop(todo_id)
        print(f"🗑️  Deleted: #{todo_id} — {deleted['title']}")
        return True
    print(f"❌ Todo #{todo_id} not found")
    return False

# ===== Demo =====
print("=== CRUD Demo: To-Do App ===\n")
create_todo("Learn Python", "Study variables, loops, functions")
create_todo("Set up Git", "Create GitHub repo")
create_todo("Learn CRUD pattern", "Build a to-do API")
create_todo("THIS SHOULD BE DELETED", "Temporary item")

read_all_todos()

update_todo(1, completed=True)
update_todo(2, title="Master Git", completed=True)
delete_todo(4)

print()
read_all_todos()
```

### Active Recall Questions (Before Day 10, answer without notes)
1. Why is DELETE the most dangerous CRUD operation in production?
2. What is the difference between PUT and PATCH in REST APIs? (Both are "Update" — but how?)
3. Every database table corresponds to one of these: new record creation, reading records, modifying records, or removing them. What does this mean for how you design a database schema?

### 📝 CRUD Documentation
- Push `todo_api.py` to GitHub
- LinkedIn: "CRUD is the pattern under every app you've ever used. I just built it from scratch in Python to understand it deeply. [screenshot of output]. Day 9 of my journey. #Python #BackendEngineering"

---

## Days 10–11: PATTERN 2 — Client-Server Architecture

### What It Is

Every web application separates the work into two roles:
- **Client:** The part the user sees. Makes requests. (Browser, mobile app, another server)
- **Server:** The part that processes. Returns responses. (API server, web server)

```
CLIENT                          SERVER
  │                               │
  │── Request ──────────────────►│
  │   "GET /users/123"            │── Query database
  │                               │── Format response
  │◄── Response ─────────────────│
  │   {"id": 123, "name": "Alice"}│
  │                               │
  │ Render the data to the user   │
```

### Why This Separation Matters

- **Security:** The server controls access to data. The client only sees what the server allows.
- **Scalability:** You can run 100 servers for one million clients.
- **Separation of Concerns:** Frontend team works on the client. Backend team works on the server.

### Build It: A Simple HTTP Server

```python
# Save as: phase-1-patterns/02-client-server/simple_server.py
# We're building an HTTP server from scratch to understand the protocol

from http.server import HTTPServer, BaseHTTPRequestHandler
import json
from datetime import datetime

# Our in-memory "database"
users = {
    1: {"id": 1, "name": "Alice", "email": "alice@example.com"},
    2: {"id": 2, "name": "Bob",   "email": "bob@example.com"},
}

class RequestHandler(BaseHTTPRequestHandler):
    def do_GET(self):
        """Handle GET requests (reading data)"""
        print(f"\n→ Received: GET {self.path} from {self.client_address[0]}")
        
        if self.path == "/":
            # Root endpoint: return server info
            response = {
                "server": "My First HTTP Server",
                "time": datetime.now().isoformat(),
                "endpoints": ["/users", "/users/1", "/users/2"]
            }
            self._send_json(200, response)

        elif self.path == "/users":
            # Return all users
            self._send_json(200, {"users": list(users.values())})

        elif self.path.startswith("/users/"):
            # Return specific user
            try:
                user_id = int(self.path.split("/")[-1])
                user = users.get(user_id)
                if user:
                    self._send_json(200, user)
                else:
                    self._send_json(404, {"error": f"User {user_id} not found"})
            except ValueError:
                self._send_json(400, {"error": "Invalid user ID"})
        else:
            self._send_json(404, {"error": "Endpoint not found"})

    def _send_json(self, status_code, data):
        """Helper: send a JSON response"""
        body = json.dumps(data, indent=2).encode()
        self.send_response(status_code)
        self.send_header("Content-Type", "application/json")
        self.send_header("Content-Length", len(body))
        self.end_headers()
        self.wfile.write(body)
        
        status_symbols = {200: "✅", 404: "❌", 400: "⚠️"}
        print(f"← Sent: {status_symbols.get(status_code, '?')} HTTP {status_code}")
    
    def log_message(self, format, *args):
        pass  # Suppress default logging (we have our own)

if __name__ == "__main__":
    server = HTTPServer(("localhost", 8080), RequestHandler)
    print("🚀 Server started at http://localhost:8080")
    print("Try: curl http://localhost:8080/users")
    print("Try: curl http://localhost:8080/users/1")
    print("Try: curl http://localhost:8080/users/999")
    print("\nPress Ctrl+C to stop\n")
    server.serve_forever()
```

```bash
# Test your server from another terminal:
curl http://localhost:8080/
curl http://localhost:8080/users
curl http://localhost:8080/users/1
curl http://localhost:8080/users/999    # Should get 404
```

---

## Days 12–13: PATTERN 3 — ETL (Extract, Transform, Load)

### What It Is and Why It Defines Data Engineering

ETL is the pattern that moves data from where it is created (messy, unstructured, inconsistent) to where it is useful (clean, structured, queryable).

```
EXTRACT: Pull data from source(s)
  → CSV files, APIs, databases, log files, IoT sensors, web scraping

TRANSFORM: Clean and reshape it
  → Remove duplicates, fix formats, convert units, join datasets,
    apply business rules, handle nulls, standardize currencies

LOAD: Write it to a destination
  → Data warehouse, database, another API, files, dashboards

Real Example (Uber):
  EXTRACT: GPS coordinates from 5 million driver phones
  TRANSFORM: Calculate trip distances, apply surge pricing formula, 
             match to zones, convert to billing amounts
  LOAD: Write to payment database + analytics warehouse
```

### Build It: Stock Price ETL Pipeline

```python
# Save as: phase-1-patterns/03-etl/stock_etl.py

import requests
import json
import csv
from datetime import datetime, timedelta
from pathlib import Path

# ===== EXTRACT =====
def extract_stock_data(symbol: str) -> list[dict]:
    """
    Extract stock data from an API.
    Using Alpha Vantage free API (get free key at alphavantage.co)
    For demo: we'll generate mock data if no API key.
    """
    print(f"\n[EXTRACT] Pulling data for {symbol}...")
    
    # Mock data for demonstration (replace with real API call)
    raw_data = []
    base_price = 150.0
    for i in range(30):
        date = (datetime.now() - timedelta(days=i)).strftime("%Y-%m-%d")
        # Simulate realistic stock data with noise
        import random
        change = random.uniform(-5, 5)
        price = base_price + change
        raw_data.append({
            "date": date,
            "open": f"${price:.4f}",       # Messy: has $ sign
            "high": f"${price + 2:.4f}",
            "low": f"${price - 2:.4f}",
            "close": f"${price + 1:.4f}",
            "volume": f"{random.randint(10000000, 50000000):,}",  # Messy: has commas
            "symbol": symbol,
            "source": "mock_api"
        })
    
    print(f"  → Extracted {len(raw_data)} raw records")
    return raw_data

# ===== TRANSFORM =====
def transform_stock_data(raw_data: list[dict]) -> list[dict]:
    """
    Clean and transform raw stock data:
    1. Remove $ signs and commas
    2. Convert strings to proper numeric types
    3. Calculate derived fields
    4. Sort by date
    5. Handle data quality issues
    """
    print(f"\n[TRANSFORM] Cleaning {len(raw_data)} records...")
    
    cleaned = []
    errors = []
    
    for i, record in enumerate(raw_data):
        try:
            # Remove $ and commas, convert to float/int
            clean_record = {
                "date": datetime.strptime(record["date"], "%Y-%m-%d").date(),
                "symbol": record["symbol"].upper(),
                "open":   float(record["open"].replace("$", "").replace(",", "")),
                "high":   float(record["high"].replace("$", "").replace(",", "")),
                "low":    float(record["low"].replace("$", "").replace(",", "")),
                "close":  float(record["close"].replace("$", "").replace(",", "")),
                "volume": int(record["volume"].replace(",", "")),
            }
            
            # Derived fields (business logic)
            clean_record["daily_range"] = round(clean_record["high"] - clean_record["low"], 4)
            clean_record["price_change"] = round(clean_record["close"] - clean_record["open"], 4)
            clean_record["price_change_pct"] = round(
                (clean_record["price_change"] / clean_record["open"]) * 100, 4
            )
            
            # Data quality check
            if clean_record["high"] < clean_record["low"]:
                raise ValueError("High price is lower than Low price — data corruption!")
            if clean_record["volume"] < 0:
                raise ValueError("Negative volume — impossible!")
            
            cleaned.append(clean_record)
            
        except Exception as e:
            errors.append({"record_index": i, "error": str(e), "raw": record})
    
    # Sort by date ascending
    cleaned.sort(key=lambda x: x["date"])
    
    print(f"  → Cleaned: {len(cleaned)} records | Errors: {len(errors)}")
    if errors:
        print(f"  → Error details: {errors[:2]}")  # Show first 2 errors
    
    return cleaned

# ===== LOAD =====
def load_to_csv(data: list[dict], output_path: str) -> None:
    """Load transformed data to a CSV file."""
    print(f"\n[LOAD] Writing {len(data)} records to {output_path}...")
    
    Path(output_path).parent.mkdir(parents=True, exist_ok=True)
    
    with open(output_path, "w", newline="") as f:
        writer = csv.DictWriter(f, fieldnames=data[0].keys())
        writer.writeheader()
        writer.writerows(data)
    
    print(f"  → Saved to {output_path}")

def load_summary_report(data: list[dict]) -> dict:
    """Generate a summary report (would normally go to a DB or dashboard)."""
    prices = [r["close"] for r in data]
    volumes = [r["volume"] for r in data]
    
    report = {
        "symbol": data[0]["symbol"],
        "period": f"{data[0]['date']} to {data[-1]['date']}",
        "records": len(data),
        "avg_close": round(sum(prices) / len(prices), 2),
        "min_close": round(min(prices), 2),
        "max_close": round(max(prices), 2),
        "total_volume": sum(volumes),
        "up_days": sum(1 for r in data if r["price_change"] > 0),
        "down_days": sum(1 for r in data if r["price_change"] < 0),
    }
    return report

# ===== ORCHESTRATE THE PIPELINE =====
def run_etl_pipeline(symbol: str):
    """Run the full ETL pipeline."""
    print(f"{'='*50}")
    print(f"ETL PIPELINE: {symbol} Stock Data")
    print(f"{'='*50}")
    
    start_time = datetime.now()
    
    # EXTRACT
    raw_data = extract_stock_data(symbol)
    
    # TRANSFORM
    clean_data = transform_stock_data(raw_data)
    
    # LOAD
    timestamp = datetime.now().strftime("%Y%m%d_%H%M%S")
    output_file = f"output/{symbol}_{timestamp}.csv"
    load_to_csv(clean_data, output_file)
    
    # Report
    summary = load_summary_report(clean_data)
    elapsed = (datetime.now() - start_time).total_seconds()
    
    print(f"\n{'='*50}")
    print(f"✅ PIPELINE COMPLETE in {elapsed:.2f}s")
    print(f"  Symbol: {summary['symbol']}")
    print(f"  Period: {summary['period']}")
    print(f"  Avg Close: ${summary['avg_close']}")
    print(f"  Range: ${summary['min_close']} – ${summary['max_close']}")
    print(f"  Up Days: {summary['up_days']} | Down Days: {summary['down_days']}")
    print(f"{'='*50}")

if __name__ == "__main__":
    run_etl_pipeline("AAPL")
    run_etl_pipeline("GOOGL")
```

---

## Days 14–15: PATTERN 4 — Authentication Flow

### Why Auth Is Its Own Pattern

Every app that has users must answer: "How do I know who this person is?" This is authentication. "What are they allowed to do?" — that is authorization.

```
AUTHENTICATION FLOW:
1. User provides credentials (username + password)
2. Server VERIFIES: "Does this match what we have stored?"
3. Server issues a TOKEN (a signed proof of identity)
4. User includes the token with every future request
5. Server VERIFIES the token cryptographically

TOKEN (JWT) STRUCTURE:
┌─────────────────┬──────────────────┬─────────────────┐
│     Header      │     Payload      │    Signature    │
│ Algorithm: HS256│ user_id: 123     │ HMAC-SHA256(    │
│ Type: JWT       │ role: admin      │   header +      │
│                 │ expires: 3600    │   payload +     │
│                 │                  │   secret_key)   │
└─────────────────┴──────────────────┴─────────────────┘

The signature CANNOT be faked without the server's secret key.
This is why tokens can be verified without a database lookup.
```

### The Critical Security Mistakes Beginners Make

| Mistake | Why It's Dangerous | Correct Approach |
|---|---|---|
| Storing passwords in plain text | Database breach = all passwords leaked | Always hash with bcrypt or argon2 |
| Putting secrets in code | Anyone who reads your code has the key | Use environment variables |
| Tokens that never expire | Stolen token works forever | Short expiry (15 min) + refresh tokens |
| Not using HTTPS | Tokens can be intercepted | HTTPS always, everywhere |
| Storing sensitive data in JWT payload | Anyone can read the payload (it's base64) | Only store non-sensitive user ID |

---

## Days 16–17: PATTERN 5 — Caching

### What It Is and Why It Matters for Scale

```
WITHOUT CACHE:
User request → Server → Database query (50ms) → Response

WITH CACHE:
User request → Server → Cache HIT → Response (0.5ms) ← 100x faster
User request → Server → Cache MISS → Database (50ms) → Store in cache → Response

CACHE HIT RATE: What % of requests are served from cache
  90% hit rate = 90% of requests take 0.5ms instead of 50ms
  At 1M requests/day: saves ~12+ hours of database time
```

### Caching Strategies

```
1. CACHE-ASIDE (Most Common):
   App checks cache first → if miss, fetch DB, populate cache → return
   Used by: Twitter, Instagram, Reddit

2. WRITE-THROUGH:
   Every write goes to cache AND database simultaneously
   Never stale, but every write is slower
   Used by: Payment systems where stale data is unacceptable

3. WRITE-BEHIND (Write-Back):
   Write to cache only, async write to DB later
   Very fast writes, but data loss risk if cache crashes

4. READ-THROUGH:
   Cache is in front of DB, app only talks to cache
   Cache automatically fetches from DB on miss
```

### The Thundering Herd Problem (Real Production Issue)

```
SCENARIO:
- Redis cache stores "trending_posts" with a 60-second TTL
- 50,000 users/second are reading trending posts
- At exactly second 60, the cache key expires
- ALL 50,000 users simultaneously miss the cache
- ALL 50,000 requests hit the database at the same instant
- DATABASE CRASHES

SOLUTIONS:
1. Probabilistic Early Expiration: 
   If a cached item will expire in T seconds, refresh it 
   with probability P = 1/(T × decay_factor)
   This means ONE request refreshes the cache BEFORE it expires

2. Cache Stampede Lock:
   When cache misses, only ONE thread fetches from DB
   Other threads wait for that one thread to populate the cache
   Used at: Facebook, Twitter
```

---

## Days 18–19: PATTERNS 7–9 — Event-Driven, Producer-Consumer, Pub/Sub

### The Three Async Patterns That Power Modern Systems

```
PATTERN 7: EVENT-DRIVEN
"Something happened → other things react"

User signs up → EVENT: "user_registered"
               ↓
         ┌─────┼──────┐
         ▼     ▼      ▼
    Send   Update   Create
   welcome analytics default
   email  dashboard  avatar

Used by: Serverless functions, IoT, microservices

─────────────────────────────────────────────────────

PATTERN 8: PRODUCER-CONSUMER
"Producers generate work → Queue buffers it → Consumers process it"

Upload API → [Queue: image_resize_jobs] → Worker processes images
Order API  → [Queue: email_jobs]        → Email service sends emails
Web scraper→ [Queue: parse_jobs]        → Parsers extract data

Benefit: Producers and consumers run at DIFFERENT speeds
         If consumers are slow, the queue builds up — but producers don't block!

─────────────────────────────────────────────────────

PATTERN 9: PUBLISH/SUBSCRIBE
"Publishers broadcast events → Subscribers choose what to listen to"

PaymentService publishes "payment.completed"
                ↓
    ┌──────────┼──────────┐
    ▼          ▼          ▼
EmailSvc  InventorySvc  AnalyticsSvc
(receipt) (restock)     (track revenue)

Each subscriber is independent. Adding a new subscriber doesn't change the publisher.

Used by: AWS SNS, Google Pub/Sub, Kafka Topics
```

### Build It: Event-Driven Notification System

```python
# Save as: phase-1-patterns/07-event-driven/event_system.py

from typing import Callable, Any
from datetime import datetime
from collections import defaultdict
import threading
import queue
import time

class EventBus:
    """
    A simple event bus: the core of event-driven architecture.
    Subscribers register for event types.
    Publishers emit events.
    The bus routes events to subscribers.
    """
    def __init__(self):
        self._subscribers: dict[str, list[Callable]] = defaultdict(list)
        self._event_queue: queue.Queue = queue.Queue()
        self._running = False
    
    def subscribe(self, event_type: str, handler: Callable):
        """Register a function to handle a specific event type."""
        self._subscribers[event_type].append(handler)
        print(f"  📥 Subscribed: {handler.__name__} → '{event_type}'")
    
    def publish(self, event_type: str, data: dict):
        """Publish an event to all subscribers."""
        event = {
            "type": event_type,
            "data": data,
            "timestamp": datetime.now().isoformat()
        }
        self._event_queue.put(event)
        print(f"\n📤 Published: '{event_type}' — {data}")
    
    def start(self):
        """Start processing events in a background thread."""
        self._running = True
        thread = threading.Thread(target=self._process_events, daemon=True)
        thread.start()
    
    def _process_events(self):
        """Process events from the queue and dispatch to subscribers."""
        while self._running:
            try:
                event = self._event_queue.get(timeout=0.1)
                event_type = event["type"]
                handlers = self._subscribers.get(event_type, [])
                
                for handler in handlers:
                    try:
                        handler(event["data"])
                    except Exception as e:
                        print(f"  ❌ Handler '{handler.__name__}' failed: {e}")
                
                self._event_queue.task_done()
            except queue.Empty:
                continue

# ===== Event Handlers (Subscribers) =====
def send_welcome_email(data: dict):
    time.sleep(0.01)  # Simulate network call
    print(f"  📧 [EmailService] Welcome email sent to {data['email']}")

def create_default_settings(data: dict):
    print(f"  ⚙️  [SettingsService] Default settings created for user #{data['user_id']}")

def track_signup_analytics(data: dict):
    print(f"  📊 [Analytics] New signup tracked: {data['country']} user")

def send_payment_receipt(data: dict):
    print(f"  🧾 [Receipt] Receipt sent for ${data['amount']} to {data['email']}")

def update_inventory(data: dict):
    print(f"  📦 [Inventory] Reduced stock of '{data['product']}' by 1")

def record_revenue(data: dict):
    print(f"  💰 [Analytics] Revenue: +${data['amount']}")

# ===== Demo =====
bus = EventBus()
bus.start()

# Subscribe handlers to events
print("=== Registering Subscribers ===")
bus.subscribe("user.registered",   send_welcome_email)
bus.subscribe("user.registered",   create_default_settings)
bus.subscribe("user.registered",   track_signup_analytics)
bus.subscribe("payment.completed", send_payment_receipt)
bus.subscribe("payment.completed", update_inventory)
bus.subscribe("payment.completed", record_revenue)

time.sleep(0.1)  # Let subscribers register

print("\n=== Publishing Events ===")

# A new user signs up — one publish → three handlers fire
bus.publish("user.registered", {
    "user_id": 1001,
    "email": "alice@example.com",
    "country": "India"
})

time.sleep(0.2)

# A payment completes — one publish → three different handlers fire
bus.publish("payment.completed", {
    "order_id": "ORD-5678",
    "product": "MacBook Pro",
    "amount": 2499.00,
    "email": "alice@example.com"
})

time.sleep(0.5)
print("\n=== All events processed ===")
```

---

## Days 20–28: Remaining Patterns + PROJECT 1

### Days 20–21: Patterns 10–12 (Observer, Batch, Stream)

**Observer Pattern** — Used in React's state management, database triggers, real-time dashboards. One state change notifies all watchers.

**Batch Processing** — Used in nightly jobs, payroll runs, data warehouse loads. Process a lot of data at scheduled intervals.

**Stream Processing** — Used in fraud detection, real-time analytics, live dashboards. Process data the instant it arrives.

```python
# phase-1-patterns/11-batch/log_analyzer.py
# Batch processing: analyze 10,000 web server logs

import re
from collections import Counter
from datetime import datetime

def parse_log_line(line: str) -> dict | None:
    """Parse an Apache/Nginx log line."""
    # Log format: IP - - [date] "METHOD /path HTTP/1.1" STATUS BYTES
    pattern = r'(\S+) - - \[([^\]]+)\] "(\S+) (\S+) \S+" (\d+) (\d+)'
    match = re.match(pattern, line)
    if match:
        return {
            "ip": match.group(1),
            "timestamp": match.group(2),
            "method": match.group(3),
            "path": match.group(4),
            "status": int(match.group(5)),
            "bytes": int(match.group(6))
        }
    return None

def analyze_logs_in_batch(log_lines: list[str]) -> dict:
    """
    BATCH PROCESSING: Process all logs at once, generate summary.
    This runs at scheduled times (e.g., every hour) — not real-time.
    """
    print(f"[BATCH] Analyzing {len(log_lines):,} log lines...")
    start = datetime.now()
    
    parsed = [parse_log_line(line) for line in log_lines if parse_log_line(line)]
    
    results = {
        "total_requests": len(parsed),
        "status_codes": dict(Counter(r["status"] for r in parsed)),
        "top_pages": dict(Counter(r["path"] for r in parsed).most_common(5)),
        "top_ips": dict(Counter(r["ip"] for r in parsed).most_common(5)),
        "total_bytes": sum(r["bytes"] for r in parsed),
        "error_rate": sum(1 for r in parsed if r["status"] >= 400) / len(parsed) * 100
    }
    
    elapsed = (datetime.now() - start).total_seconds()
    print(f"[BATCH] Complete in {elapsed:.3f}s")
    return results
```

### Days 22–25: Patterns 13–18 (MapReduce, Pipeline, Microservices, CQRS, Saga, Sharding)

Brief implementation sketches for each:

```python
# PATTERN 13: MapReduce — Word count across a document
# MAP: split text → count each word locally
# REDUCE: combine all local counts → global count

from multiprocessing import Pool
from collections import Counter

def map_word_count(chunk: str) -> dict:
    """Map: count words in one chunk"""
    return dict(Counter(chunk.lower().split()))

def reduce_word_counts(partial_counts: list[dict]) -> dict:
    """Reduce: combine all chunk counts"""
    total = Counter()
    for partial in partial_counts:
        total.update(partial)
    return dict(total.most_common(10))

def mapreduce_word_count(text: str, num_workers: int = 4) -> dict:
    chunks = [text[i::num_workers] for i in range(num_workers)]
    with Pool(num_workers) as pool:
        partial_counts = pool.map(map_word_count, chunks)
    return reduce_word_counts(partial_counts)
```

```python
# PATTERN 17: Saga Pattern — Distributed transaction with compensation
# If any step fails, run compensating actions to undo previous steps

class TravelBookingSaga:
    """
    Booking a trip: Flight → Hotel → Car Rental
    If Car Rental fails, cancel Hotel and Flight
    """
    def __init__(self):
        self.completed_steps = []
    
    def book_flight(self, trip_id: str) -> bool:
        print(f"  ✈️  Booking flight for {trip_id}...")
        self.completed_steps.append("flight")
        return True  # Simulate success
    
    def cancel_flight(self, trip_id: str):
        print(f"  ↩️  COMPENSATING: Cancelling flight for {trip_id}")
    
    def book_hotel(self, trip_id: str) -> bool:
        print(f"  🏨 Booking hotel for {trip_id}...")
        self.completed_steps.append("hotel")
        return True
    
    def cancel_hotel(self, trip_id: str):
        print(f"  ↩️  COMPENSATING: Cancelling hotel for {trip_id}")
    
    def book_car(self, trip_id: str) -> bool:
        print(f"  🚗 Booking car for {trip_id}...")
        import random
        if random.random() < 0.5:  # 50% chance of failure
            print("  ❌ Car rental service unavailable!")
            return False
        self.completed_steps.append("car")
        return True
    
    def execute(self, trip_id: str):
        print(f"\n=== SAGA: Booking Trip {trip_id} ===")
        steps = [
            (self.book_flight, self.cancel_flight),
            (self.book_hotel, self.cancel_hotel),
            (self.book_car, None)
        ]
        
        for book_fn, cancel_fn in steps:
            if not book_fn(trip_id):
                print(f"\n❌ Saga failed! Running compensating transactions...")
                # Run compensating actions in REVERSE order
                for completed in reversed(self.completed_steps):
                    if completed == "flight": self.cancel_flight(trip_id)
                    if completed == "hotel":  self.cancel_hotel(trip_id)
                print("Saga rolled back. Trip NOT booked.")
                return False
        
        print(f"\n✅ Saga complete! Trip {trip_id} fully booked.")
        return True
```

---

## Days 25–28: PROJECT 1 — Pattern Portfolio Application

### The Problem It Solves
A single web application that demonstrates all 5 core patterns: CRUD (todo list), Client-Server (API), ETL (data import), Auth (login), and Caching (Redis). This is your first portfolio-grade project.

### Architecture

```
┌─────────────────────────────────────────────────────────────┐
│                 PATTERN PORTFOLIO APP                        │
│                                                             │
│  ┌──────────┐   HTTP   ┌─────────────────────────────────┐ │
│  │  Browser │◄────────►│  API Server (Python FastAPI)    │ │
│  │  (Client)│          │                                 │ │
│  └──────────┘          │  /todos     → CRUD Pattern      │ │
│                        │  /auth      → Auth Pattern      │ │
│                        │  /import    → ETL Pattern       │ │
│                        │  /search    → Caching Pattern   │ │
│                        └────────┬────────────────────────┘ │
│                                 │                           │
│                    ┌────────────┼────────────┐              │
│                    ▼            ▼            ▼              │
│              ┌──────────┐ ┌─────────┐ ┌──────────┐         │
│              │PostgreSQL│ │  Redis  │ │CSV Files │         │
│              │(primary) │ │ (cache) │ │(ETL src) │         │
│              └──────────┘ └─────────┘ └──────────┘         │
└─────────────────────────────────────────────────────────────┘
```

### Documentation: Project 1

**GitHub README must include:**
- Architecture diagram (above)
- Which patterns are demonstrated and where
- API documentation (endpoint list with request/response examples)
- How to run (`docker-compose up`)
- Screenshots of each pattern working
- Performance: "Cache hit vs miss latency comparison"

**Blog Post (Dev.to):** "I Built One App to Demonstrate 5 Fundamental Engineering Patterns. Here's What I Learned."

---

---

# 🟠 PHASE 2: WEB FOUNDATIONS + NETWORKING INTERNALS (Days 29–49)

> **Goal:** Understand what happens from the moment a user presses Enter to the moment pixels appear. This is the foundation of every web application you will ever build.

---

## Days 29–31: The Network Stack — Deep Dive

### TCP: Why Reliability Costs Latency

```
TCP THREE-WAY HANDSHAKE:
Before ANY data is sent, three round trips happen:

Client ──SYN──────────────────────────────────────► Server
       "I want to talk. My sequence number is 1000"

Client ◄─────────────────────────────SYN-ACK────── Server
       "OK. My sequence number is 5000. Yours received."

Client ──ACK──────────────────────────────────────► Server
       "Received. Let's talk."

Cost: 1.5 round trips BEFORE any data moves.
At 100ms latency (US to India): 150ms before first byte!

HTTP/1.1: New TCP connection per request = 1.5 RTT overhead EACH TIME
HTTP/2:   Reuse one TCP connection = 1.5 RTT ONCE, then multiple requests
HTTP/3:   Built on UDP, 0-RTT resumption = near-zero overhead for repeat visitors
```

### Hands-On: Network Analysis with curl

```bash
# Measure exactly where time is spent in each HTTP request
measure() {
    curl -w "
DNS Lookup:        %{time_namelookup}s
TCP Connect:       %{time_connect}s
TLS Handshake:     %{time_appconnect}s
Request Sent:      %{time_pretransfer}s
First Byte:        %{time_starttransfer}s
Total:             %{time_total}s
HTTP Version:      %{http_version}
Status:            %{http_code}
" -o /dev/null -s "$1"
}

measure https://google.com
measure https://github.com
measure https://stackoverflow.com

# Compare HTTP/1.1 vs HTTP/2
curl --http1.1 -o /dev/null -s -w "HTTP/1.1 total: %{time_total}s\n" https://nghttp2.org/
curl --http2    -o /dev/null -s -w "HTTP/2   total: %{time_total}s\n" https://nghttp2.org/
```

### DNS — The Internet's Phone Book

```bash
# See the full DNS resolution chain
dig +trace google.com

# Output will show:
# . (Root nameservers — 13 worldwide)
# com. (TLD nameservers for .com)
# google.com. (Google's authoritative nameservers)
# 142.250.77.14 (the actual IP)

# DNS Record Types
dig google.com A      # A record = IPv4 address
dig google.com AAAA   # AAAA record = IPv6 address  
dig google.com MX     # MX record = mail server
dig google.com TXT    # TXT record = verification, SPF
dig google.com CNAME  # CNAME = alias to another hostname
```

### Assignment: Network Debugging Scenario

**Scenario:** A user reports "the website is down." Walk through this diagnostic flow:

```bash
# Step 1: Is the domain resolving?
dig myapp.com +short
# If empty: DNS problem

# Step 2: Is the server reachable?
ping 54.77.143.12
# If no response: server down or firewall blocking ICMP

# Step 3: Is the port open?
nc -zv 54.77.143.12 443
# If refused: server running but app crashed, or port not open

# Step 4: Is the HTTP server responding?
curl -I https://myapp.com
# If TLS error: certificate expired
# If 5xx: application error
# If 404: deployment issue

# Step 5: Check server logs (if you have access)
ssh user@54.77.143.12 "tail -100 /var/log/nginx/error.log"
```

---

## Days 32–35: JavaScript Runtime — Understanding the Event Loop

### The Single Thread Illusion

JavaScript runs on ONE thread. Yet Node.js handles 50,000 concurrent requests. How?

```
THE EVENT LOOP:

JavaScript Engine (V8):
┌─────────────────┐
│  CALL STACK     │ ← Where synchronous code executes (one thing at a time)
│  (LIFO)         │
│                 │
│  main()         │
│  → fetchUser()  │
│    → parseJSON()│
└────────┬────────┘
         │ when a stack frame completes
         ▼
┌─────────────────────────────────────────────────────────┐
│  WEB APIS / libuv (Node.js)                             │
│  setTimeout, fetch, fs.readFile, setInterval            │
│  These run in the BACKGROUND (OS/C++ handles them)      │
└────────┬────────────────────────────────────────────────┘
         │ when complete, callback goes to:
         ▼
┌─────────────────┐    ┌─────────────────┐
│  MICROTASK      │    │  MACROTASK      │
│  QUEUE          │    │  QUEUE          │
│  (HIGH PRIORITY)│    │  (LOWER PRIO)   │
│  • Promises     │    │  • setTimeout   │
│  • queueMicro   │    │  • setInterval  │
│    task()       │    │  • I/O callbacks│
└────────┬────────┘    └────────┬────────┘
         │                     │
         └─────────┬───────────┘
                   ▼
           EVENT LOOP picks from MICROTASK QUEUE first,
           then MACROTASK QUEUE, then checks MICROTASK again...

KEY RULE: Call Stack must be EMPTY before Event Loop picks next task.
This is why blocking the call stack (long sync computation) freezes EVERYTHING.
```

### Predict the Output (Classic Interview Question)

```javascript
// What order do these print? Predict before running.

console.log("1: Start");

setTimeout(() => console.log("2: Timeout 0ms"), 0);

Promise.resolve().then(() => console.log("3: Promise resolved"));

queueMicrotask(() => console.log("4: Microtask"));

console.log("5: End");

// Answer:
// 1: Start
// 5: End
// 3: Promise resolved     ← Microtask queue (higher priority)
// 4: Microtask            ← Microtask queue
// 2: Timeout 0ms          ← Macrotask queue (processed AFTER all microtasks)
```

### Async/Await Deep Dive

```javascript
// Save as: phase-2-web/js-runtime/async_demo.js

// The Problem: Sequential vs Parallel Async Operations

async function fetchUserData(userId) {
    // Simulate API call
    return new Promise(resolve => setTimeout(() => 
        resolve({ id: userId, name: `User ${userId}`, posts: userId * 5 }), 
        100
    ));
}

// ❌ SLOW: Sequential (one after the other)
async function loadUsersSequential(userIds) {
    const start = Date.now();
    const users = [];
    for (const id of userIds) {
        const user = await fetchUserData(id);  // Waits for each one
        users.push(user);
    }
    console.log(`Sequential: ${Date.now() - start}ms`);
    return users;
}

// ✅ FAST: Parallel (all at once)
async function loadUsersParallel(userIds) {
    const start = Date.now();
    const users = await Promise.all(
        userIds.map(id => fetchUserData(id))  // All start simultaneously
    );
    console.log(`Parallel: ${Date.now() - start}ms`);
    return users;
}

// ✅ RESILIENT: Some might fail, we still get the successful ones
async function loadUsersResilient(userIds) {
    const results = await Promise.allSettled(
        userIds.map(id => fetchUserData(id))
    );
    
    const successful = results
        .filter(r => r.status === "fulfilled")
        .map(r => r.value);
    
    const failed = results
        .filter(r => r.status === "rejected")
        .map(r => r.reason);
    
    console.log(`Resilient: ${successful.length} ok, ${failed.length} failed`);
    return { successful, failed };
}

(async () => {
    const userIds = [1, 2, 3, 4, 5];
    
    await loadUsersSequential(userIds);  // ~500ms (100ms × 5)
    await loadUsersParallel(userIds);    // ~100ms (all run together)
    await loadUsersResilient(userIds);   // ~100ms with error handling
})();
```

---

## Days 36–40: Critical Rendering Path + Core Web Vitals

### How the Browser Renders a Page

```
1. Browser receives HTML from server
2. Parses HTML → builds DOM tree
3. Encounters <link rel="stylesheet"> → fetches CSS → builds CSSOM
   ⚠️ CSS is RENDER-BLOCKING: nothing renders until CSSOM is built
4. Encounters <script> → fetches, compiles, executes JS
   ⚠️ JS is PARSER-BLOCKING: pauses HTML parsing
5. Combines DOM + CSSOM → Render Tree (only visible elements)
6. Layout (Reflow): calculates exact pixel position of every element
7. Paint: fills in pixels (colors, borders, text)
8. Composite: GPU assembles layers into final frame

PERFORMANCE IMPLICATIONS:
• Move <script> to bottom or use `defer`/`async` attributes
• Inline critical CSS (above-the-fold styles) in <head>
• Use `font-display: swap` to prevent invisible text during font load
• Reserve space for images to prevent layout shift
```

### Core Web Vitals — What Google Measures

```bash
# Audit any website
npx lighthouse https://yoursite.com --view

# Or use Chrome DevTools → Performance → Record page load

# Three Key Metrics:
# LCP (Largest Contentful Paint): < 2.5s = Good
#   What: When is the largest visible element ready?
#   Fix: Optimize images, preload critical resources, fast servers

# CLS (Cumulative Layout Shift): < 0.1 = Good
#   What: How much does the page jump around while loading?
#   Fix: Reserve space for images (width/height attributes), avoid late DOM insertions

# INP (Interaction to Next Paint): < 200ms = Good
#   What: How quickly does the page respond to clicks?
#   Fix: Break up long JavaScript tasks, defer non-critical work
```

---

## Days 41–49: PROJECT 2 — High-Performance Landing Page

### Requirements (Must achieve ALL of these)
- Lighthouse score: 90+ on all four categories (Performance, Accessibility, Best Practices, SEO)
- Semantic HTML (no divs where header/main/article/nav/section would be more appropriate)
- Working CI/CD pipeline (GitHub Actions → Vercel auto-deploy on push)
- Responsive images (srcset, WebP format)
- Zero render-blocking resources
- Perfect Accessibility (keyboard navigation works, all images have alt text)

### Documentation: Project 2

**Platform:** GitHub + Vercel (live demo) + Lighthouse report in README

**GitHub README must show:**
- Before/after Lighthouse scores (screenshot)
- Which optimization technique fixed which metric
- CI/CD pipeline screenshot showing auto-deploy

**Blog post (Hashnode):** "What a 100/100 Lighthouse Score Actually Requires: A Technical Deep Dive"

---

---

# 🟢 PHASE 3: BACKEND ENGINEERING + DATABASES (Days 50–70)

> **Goal:** Build production-grade APIs and design data models that survive 1 million users, concurrent requests, and schema changes over time.

---

## Days 50–53: REST API Design (Professional Grade)

### What Separates a Beginner API from an MNC API

| Beginner | MNC Standard |
|---|---|
| No versioning (`/users`) | Versioned (`/v1/users`) |
| Inconsistent status codes | RFC-compliant (201 Create, 404 Not Found, 409 Conflict) |
| No pagination | Cursor-based pagination for large lists |
| Passwords logged | PII never logged |
| No idempotency | Idempotency keys for payment endpoints |
| No rate limiting | Per-user rate limits with Redis |
| Sync everywhere | Async for slow operations (email, PDF generation) |
| No API docs | OpenAPI/Swagger auto-generated |

### The Professional API Design

```python
# Save as: phase-3-backend/api/main.py
# FastAPI with professional production patterns

from fastapi import FastAPI, HTTPException, Depends, Request, Header
from fastapi.middleware.cors import CORSMiddleware
from fastapi.responses import JSONResponse
from pydantic import BaseModel, EmailStr, validator
from datetime import datetime, timedelta
import hashlib, secrets, time, redis, json
from typing import Optional
import uvicorn

app = FastAPI(
    title="Production API",
    version="1.0.0",
    description="An API demonstrating MNC-grade patterns"
)

# ===== CORS Middleware (always configure properly) =====
app.add_middleware(
    CORSMiddleware,
    allow_origins=["https://yourfrontend.com"],  # Never use ["*"] in production
    allow_methods=["GET", "POST", "PUT", "DELETE"],
    allow_headers=["Authorization", "Content-Type", "X-Idempotency-Key"],
)

# ===== Redis for rate limiting and caching =====
cache = redis.Redis(host="localhost", port=6379, db=0, decode_responses=True)

# ===== Rate Limiting (Token Bucket Algorithm) =====
def check_rate_limit(user_id: str, limit: int = 100, window: int = 60) -> bool:
    """
    Token bucket: each user gets `limit` requests per `window` seconds.
    Uses Redis atomic operations to be safe with concurrent requests.
    """
    key = f"rate_limit:{user_id}:{int(time.time() / window)}"
    pipe = cache.pipeline()
    pipe.incr(key)
    pipe.expire(key, window)
    results = pipe.execute()
    request_count = results[0]
    return request_count <= limit

# ===== Request Models (with validation) =====
class CreateUserRequest(BaseModel):
    email: EmailStr
    name: str
    password: str
    
    @validator("password")
    def password_strong_enough(cls, v):
        if len(v) < 8:
            raise ValueError("Password must be at least 8 characters")
        if not any(c.isupper() for c in v):
            raise ValueError("Password must contain an uppercase letter")
        return v
    
    @validator("name")
    def name_not_empty(cls, v):
        if not v.strip():
            raise ValueError("Name cannot be empty")
        return v.strip()

# ===== Idempotency: Safe to retry without duplicating effects =====
def get_or_create_idempotency_result(idempotency_key: str, create_fn):
    """
    If this key was used before, return the cached result.
    If not, execute create_fn and cache the result.
    Critical for payment and order endpoints.
    """
    cached = cache.get(f"idempotency:{idempotency_key}")
    if cached:
        print(f"  ↩️  Idempotency hit for key: {idempotency_key[:8]}...")
        return json.loads(cached), True  # (result, was_cached)
    
    result = create_fn()
    cache.setex(
        f"idempotency:{idempotency_key}", 
        86400,  # 24 hours
        json.dumps(result)
    )
    return result, False

# ===== API Endpoints =====
@app.post("/v1/users", status_code=201)
async def create_user(
    user: CreateUserRequest,
    request: Request,
    x_idempotency_key: Optional[str] = Header(None)
):
    """
    Create a new user.
    - Validates input with Pydantic
    - Checks idempotency (safe to retry)
    - Rate limited
    """
    # Rate limiting
    client_ip = request.client.host
    if not check_rate_limit(f"ip:{client_ip}", limit=10, window=60):
        raise HTTPException(
            status_code=429,
            detail="Too many requests. Please wait before trying again.",
            headers={"Retry-After": "60"}
        )
    
    def create_user_impl():
        # Hash password (NEVER store plaintext)
        password_hash = hashlib.sha256(user.password.encode()).hexdigest()
        # In real code, use bcrypt: import bcrypt; bcrypt.hashpw(...)
        
        # In real code: INSERT INTO users...
        return {
            "id": secrets.token_hex(8),
            "email": user.email,
            "name": user.name,
            "created_at": datetime.utcnow().isoformat()
        }
    
    if x_idempotency_key:
        result, was_cached = get_or_create_idempotency_result(
            x_idempotency_key, create_user_impl
        )
        return JSONResponse(
            content=result,
            status_code=200 if was_cached else 201,
            headers={"X-Idempotency-Result": "cached" if was_cached else "created"}
        )
    
    return create_user_impl()

@app.get("/v1/users")
async def list_users(
    cursor: Optional[str] = None,
    limit: int = 20
):
    """
    List users with cursor-based pagination.
    
    Why cursor-based instead of page/offset?
    - Offset pagination: "skip 1000 rows then return 20" is SLOW on large tables
    - Cursor pagination: "give me rows after ID X" uses an index = always fast
    """
    # In real code: SELECT * FROM users WHERE id > cursor LIMIT limit+1
    # Return limit+1 rows to know if there's a next page
    users = [{"id": i, "name": f"User {i}"} for i in range(1, limit + 2)]
    
    has_more = len(users) > limit
    page_users = users[:limit]
    next_cursor = page_users[-1]["id"] if has_more else None
    
    return {
        "data": page_users,
        "pagination": {
            "cursor": next_cursor,
            "has_more": has_more,
            "limit": limit
        }
    }

if __name__ == "__main__":
    uvicorn.run(app, host="0.0.0.0", port=8000, reload=True)
```

---

## Days 54–57: Databases — From Storage to Strategy

### How PostgreSQL Physically Stores Data

```
YOUR DATA ON DISK:

PostgreSQL divides your database into 8KB PAGES:

┌─────────────────────────────────────────────────────┐
│                  PAGE (8192 bytes)                   │
│                                                      │
│  Page Header (24 bytes): page LSN, checksum, flags  │
│                                                      │
│  Item Pointers (array):  [ptr1, ptr2, ptr3, ...]    │
│                           ↓      ↓      ↓            │
│  Free Space (middle)                                 │
│                                                      │
│  Tuple 3: (id=3, name='Carol', email='carol@...')   │
│  Tuple 2: (id=2, name='Bob',   email='bob@...')     │
│  Tuple 1: (id=1, name='Alice', email='alice@...')   │
│           (stored bottom-up within the page)        │
└─────────────────────────────────────────────────────┘

WHEN YOU UPDATE A ROW:
PostgreSQL does NOT modify the existing tuple.
It writes a NEW tuple and marks the old one as "dead."
This is MVCC (Multi-Version Concurrency Control):
  - Readers see the old version while writer creates the new one
  - No read-write blocking!
  - VACUUM cleans up dead tuples later
```

### The B-Tree Index (Why It Makes Queries 1000x Faster)

```
WITHOUT INDEX: Full table scan
SELECT * FROM users WHERE email = 'alice@example.com';
→ PostgreSQL reads EVERY ROW in the table
→ At 10 million rows: reads ~80MB of data
→ Time: 500-2000ms

WITH INDEX ON email:
→ PostgreSQL follows the B-Tree (like a binary search through a phone book)
→ 10 million rows → finds it in ~23 steps (log₂(10,000,000) ≈ 23)
→ Time: 0.5-2ms (1000x faster!)

B-TREE STRUCTURE:
                     [Alice, Mark, Sam]           ← Root node
                    /          |          \
        [Alice,Bob,Carol]  [Mark,Mary]  [Sam,Tom,Zara]   ← Internal nodes
         /   |   \
      [A] [Aal-Alz] [Am-Az]                              ← Leaf nodes (actual data)
```

### Live SQL Performance Analysis

```sql
-- Set up a test table with 1 million rows
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    email VARCHAR(255) UNIQUE,
    name VARCHAR(100),
    country VARCHAR(50),
    created_at TIMESTAMP DEFAULT NOW(),
    active BOOLEAN DEFAULT true
);

-- Insert 1 million rows (this takes a minute)
INSERT INTO users (email, name, country, active)
SELECT
    'user' || i || '@example.com',
    'User ' || i,
    CASE (i % 5)
        WHEN 0 THEN 'India'
        WHEN 1 THEN 'USA'
        WHEN 2 THEN 'UK'
        WHEN 3 THEN 'Germany'
        WHEN 4 THEN 'Japan'
    END,
    (i % 10 != 0)  -- 10% inactive
FROM generate_series(1, 1000000) i;

-- Query WITHOUT index (on country)
EXPLAIN ANALYZE 
SELECT COUNT(*) FROM users WHERE country = 'India';
-- Shows: Seq Scan (reads ALL rows) → ~200ms

-- Create index
CREATE INDEX idx_users_country ON users(country);

-- Query WITH index
EXPLAIN ANALYZE
SELECT COUNT(*) FROM users WHERE country = 'India';
-- Shows: Index Scan → ~5ms (40x faster!)

-- Composite index for multi-column queries
CREATE INDEX idx_users_country_active ON users(country, active);

EXPLAIN ANALYZE
SELECT * FROM users WHERE country = 'India' AND active = true LIMIT 10;
-- Uses the composite index!
```

### Transaction Isolation: Seeing the Problem Live

```sql
-- OPEN TWO TERMINALS. Run these in parallel to see isolation levels.

-- TERMINAL 1:
BEGIN;
SELECT balance FROM accounts WHERE id = 1;  -- Returns: 1000

-- TERMINAL 2 (while Terminal 1's transaction is open):
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;  -- 1000 → 900
COMMIT;

-- TERMINAL 1 (still in same transaction):
SELECT balance FROM accounts WHERE id = 1;
-- READ COMMITTED (default): Returns 900 (sees Terminal 2's change!)
-- REPEATABLE READ: Returns 1000 (sees snapshot from start of transaction)
-- SERIALIZABLE: Returns 1000 (most strict - serial execution emulated)
COMMIT;
```

---

## Days 58–62: Message Queues + Microservices Architecture

### Why Message Queues Exist

```
WITHOUT MESSAGE QUEUE:
API Server → sends email via SMTP → user waits 3 seconds → response

WITH MESSAGE QUEUE:
API Server → puts "send_email" job in queue → immediate response
                                    ↓
                          [Message Queue (Kafka/RabbitMQ)]
                                    ↓
                          Email Worker picks up job → sends email

Benefits:
1. API response time: 3000ms → 10ms
2. If email service is down: jobs queue up, sent later
3. Independently scale workers vs. API servers
4. Retry failed jobs automatically
```

### Kafka: The Industry Standard for Events at Scale

```bash
# Start Kafka with Docker Compose
cat > docker-compose-kafka.yml << 'EOF'
version: '3'
services:
  zookeeper:
    image: confluentinc/cp-zookeeper:7.5.0
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181
  
  kafka:
    image: confluentinc/cp-kafka:7.5.0
    depends_on: [zookeeper]
    ports:
      - "9092:9092"
    environment:
      KAFKA_BROKER_ID: 1
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://localhost:9092
      KAFKA_AUTO_CREATE_TOPICS_ENABLE: "true"
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1
EOF

docker-compose -f docker-compose-kafka.yml up -d
```

```python
# phase-3-backend/kafka/producer.py — order placement
from kafka import KafkaProducer
import json
from datetime import datetime

producer = KafkaProducer(
    bootstrap_servers=['localhost:9092'],
    value_serializer=lambda v: json.dumps(v).encode('utf-8')
)

# When a user places an order:
def place_order(user_id: int, items: list, total: float):
    order_event = {
        "event_type": "order.placed",
        "order_id": f"ORD-{datetime.now().timestamp():.0f}",
        "user_id": user_id,
        "items": items,
        "total": total,
        "timestamp": datetime.now().isoformat()
    }
    
    # Publish to Kafka topic
    future = producer.send("orders", value=order_event)
    record_metadata = future.get(timeout=10)
    
    print(f"✅ Order event published to Kafka:")
    print(f"   Topic: {record_metadata.topic}")
    print(f"   Partition: {record_metadata.partition}")
    print(f"   Offset: {record_metadata.offset}")
    
    return order_event["order_id"]

# Test it
order_id = place_order(
    user_id=1001,
    items=[{"name": "MacBook Pro", "qty": 1, "price": 2499}],
    total=2499.00
)
```

```python
# phase-3-backend/kafka/consumer_email.py — email service
from kafka import KafkaConsumer
import json

consumer = KafkaConsumer(
    "orders",
    bootstrap_servers=['localhost:9092'],
    group_id="email-service",        # Consumer group = work shared across instances
    auto_offset_reset='earliest',
    value_deserializer=lambda m: json.loads(m.decode('utf-8'))
)

print("📧 Email Service started. Waiting for order events...")

for message in consumer:
    event = message.value
    
    if event["event_type"] == "order.placed":
        # In real code: send actual email
        print(f"📬 Sending order confirmation email for {event['order_id']}")
        print(f"   To: User #{event['user_id']}")
        print(f"   Amount: ${event['total']}")
```

---

## Days 63–70: PROJECT 3 — Food Delivery Backend

### Architecture

```
┌───────────────────────────────────────────────────────────────────────┐
│                    FOOD DELIVERY BACKEND                              │
│                                                                       │
│  ┌──────────────┐                                                     │
│  │  API Gateway │ ← Single entry point, routes to microservices      │
│  │  (Nginx)     │                                                     │
│  └──────┬───────┘                                                     │
│         │                                                             │
│    ┌────┴────┬──────────┬──────────┬──────────┐                      │
│    ▼         ▼          ▼          ▼          ▼                       │
│  ┌──────┐ ┌──────┐ ┌──────────┐ ┌──────┐ ┌────────┐                 │
│  │ Auth │ │Order │ │Restaurant│ │Driver│ │Payment │                  │
│  │ Svc  │ │ Svc  │ │  Service │ │ Svc  │ │Service │                  │
│  │      │ │      │ │          │ │      │ │        │                  │
│  │:8001 │ │:8002 │ │  :8003   │ │:8004 │ │ :8005  │                  │
│  └──┬───┘ └──┬───┘ └────┬─────┘ └──┬───┘ └───┬────┘                 │
│     │        │           │          │          │                      │
│  PostgreSQL Kafka   MongoDB  PostgreSQL  Stripe API                   │
│  (users)  (events) (menus)  (trips)                                   │
│                                                                       │
│  Cross-cutting:                                                       │
│  Redis (cache + rate limiting) | Prometheus + Grafana (monitoring)   │
└───────────────────────────────────────────────────────────────────────┘
```

### Documentation: Project 3

**GitHub:** Microservices repo with one folder per service. `docker-compose.yml` at root to run all.

**Key artifacts:**
- Architecture diagram with service boundaries
- API documentation (Swagger for each service)
- Kafka topic map (which service publishes what, which subscribes)
- Load test report: "How many orders/second can the system handle?"
- Service dependency graph

**Blog post (Dev.to):** "I Built a Food Delivery Backend with 5 Microservices. Here's What I Got Wrong."

---

---

# 🔴 PHASE 4: DATA ENGINEERING + PIPELINES (Days 71–85)

> **Goal:** Build the systems that move, transform, and make sense of data at scale. This is the backbone of every data-driven company.

---

## Days 71–73: Data Engineering Landscape

### The Corporate Reality of Data Engineering

In a company like Uber, data flows like this:

```
SOURCES (raw data)                PIPELINE               CONSUMERS
┌──────────────────┐              ┌─────────┐            ┌────────────────┐
│ Driver GPS app   │──────────►  │         │  ────────► │ Surge pricing  │
│ Rider app events │──────────►  │  DATA   │            │ algorithm      │
│ Payment logs     │──────────►  │PIPELINE │  ────────► │ Finance reports│
│ Support tickets  │──────────►  │         │            │                │
│ Marketing data   │──────────►  │         │  ────────► │ ML models      │
│ Partner APIs     │──────────►  └─────────┘            └────────────────┘

The pipeline:
- Extracts from 50+ sources
- Handles schema changes (when the app team adds a new field)
- Handles late-arriving data (GPS pings from offline areas)
- Deduplicates (same GPS coordinate sent twice)
- Enforces data contracts (rider_id must always be non-null)
- Monitors data quality (alert if trip_count drops 30% suddenly)
- Makes data available in < 5 minutes for real-time, or hours for batch
```

### Apache Airflow — The Orchestrator

```python
# Save as: phase-4-data/dags/stock_etl_dag.py
# This is a production-grade Airflow DAG

from airflow import DAG
from airflow.operators.python import PythonOperator
from airflow.operators.email import EmailOperator
from airflow.sensors.filesystem import FileSensor
from airflow.utils.dates import days_ago
from datetime import datetime, timedelta
import pandas as pd
import psycopg2
import logging

logger = logging.getLogger(__name__)

# ===== DEFAULT ARGS: Apply to all tasks in the DAG =====
default_args = {
    "owner": "data-engineering-team",
    "depends_on_past": False,           # This run doesn't wait for yesterday's run
    "start_date": days_ago(1),
    "email_on_failure": True,
    "email": ["data-alerts@company.com"],
    "retries": 3,                       # Retry failed tasks 3 times
    "retry_delay": timedelta(minutes=5), # Wait 5 min between retries
    "execution_timeout": timedelta(hours=1),  # Kill task if it runs > 1 hour
}

# ===== TASK FUNCTIONS =====
def extract_stock_data(**context):
    """Extract stock data from Alpha Vantage API."""
    execution_date = context["execution_date"]
    logger.info(f"Extracting stock data for {execution_date.date()}")
    
    # Simulate extraction
    symbols = ["AAPL", "GOOGL", "MSFT", "AMZN"]
    all_data = []
    
    for symbol in symbols:
        # In production: call actual API
        data = {
            "symbol": symbol,
            "date": execution_date.date().isoformat(),
            "open": 150.0, "high": 155.0, "low": 148.0, "close": 153.0,
            "volume": 50000000
        }
        all_data.append(data)
    
    # Share data between tasks using XCom (Airflow's cross-task communication)
    context["task_instance"].xcom_push(key="raw_records", value=all_data)
    logger.info(f"Extracted {len(all_data)} records")
    return len(all_data)

def validate_and_transform(**context):
    """Validate data quality and transform."""
    raw_records = context["task_instance"].xcom_pull(
        task_ids="extract_stock_data", key="raw_records"
    )
    
    validation_errors = []
    clean_records = []
    
    for record in raw_records:
        errors = []
        
        # Data quality checks
        if record.get("close", 0) <= 0:
            errors.append(f"Invalid close price: {record.get('close')}")
        if record.get("high", 0) < record.get("low", 0):
            errors.append("High < Low — impossible!")
        if not record.get("symbol"):
            errors.append("Missing symbol")
        
        if errors:
            validation_errors.append({"record": record, "errors": errors})
        else:
            # Add derived fields
            record["daily_return_pct"] = round(
                (record["close"] - record["open"]) / record["open"] * 100, 4
            )
            clean_records.append(record)
    
    if validation_errors:
        logger.warning(f"Validation errors: {len(validation_errors)}")
        # Don't fail — log and continue (business decision)
    
    context["task_instance"].xcom_push(key="clean_records", value=clean_records)
    return len(clean_records)

def load_to_warehouse(**context):
    """Load clean data to PostgreSQL data warehouse."""
    clean_records = context["task_instance"].xcom_pull(
        task_ids="validate_and_transform", key="clean_records"
    )
    
    # In production: use actual connection
    logger.info(f"Loading {len(clean_records)} records to warehouse...")
    # conn = psycopg2.connect(...)
    # cursor.executemany("INSERT INTO stock_prices ...", clean_records)
    # conn.commit()
    
    logger.info("Load complete!")
    return len(clean_records)

# ===== DAG DEFINITION =====
with DAG(
    dag_id="stock_price_etl",
    default_args=default_args,
    description="Daily ETL for stock price data",
    schedule_interval="0 18 * * 1-5",   # 6pm on weekdays (market close)
    catchup=False,                        # Don't run for past missed dates
    tags=["finance", "etl", "daily"],
    doc_md="""
    ## Stock Price ETL Pipeline
    
    Extracts daily stock prices from Alpha Vantage API,
    validates data quality, and loads to the data warehouse.
    
    ### Dependencies
    - Alpha Vantage API access
    - PostgreSQL connection: `warehouse_db`
    
    ### SLA
    - Must complete within 1 hour of market close
    - Alert if > 0% validation error rate
    """
) as dag:
    
    extract_task = PythonOperator(
        task_id="extract_stock_data",
        python_callable=extract_stock_data,
    )
    
    transform_task = PythonOperator(
        task_id="validate_and_transform",
        python_callable=validate_and_transform,
    )
    
    load_task = PythonOperator(
        task_id="load_to_warehouse",
        python_callable=load_to_warehouse,
    )
    
    # Failure notification
    failure_email = EmailOperator(
        task_id="send_failure_alert",
        to=["data-team@company.com"],
        subject="ALERT: Stock ETL Failed - {{ ds }}",
        html_content="The stock price ETL pipeline failed. Check Airflow for details.",
        trigger_rule="one_failed"   # Only runs if a previous task fails
    )
    
    # Define task dependencies (the DAG graph)
    extract_task >> transform_task >> load_task
    [extract_task, transform_task, load_task] >> failure_email
```

---

## Days 74–77: Stream Processing with Kafka + Flink

### Batch vs Stream: The Fundamental Choice

```
BATCH PROCESSING:
  Collect → Wait → Process big chunk → Output
  
  Example: "Every night at 2am, calculate yesterday's revenue"
  Tools: Spark, SQL, Python scripts
  Latency: Minutes to hours
  Use when: Daily reports, ML training, data migration

STREAM PROCESSING:
  Data arrives → Process immediately → Output instantly
  
  Example: "Every time a payment occurs, update balance in real-time"
  Tools: Kafka Streams, Apache Flink, Spark Streaming
  Latency: Milliseconds to seconds
  Use when: Fraud detection, live dashboards, real-time recommendations
```

### Real-Time Fraud Detection (Streaming Example)

```python
# phase-4-data/streaming/fraud_detector.py
# Simulates a real-time fraud detection stream processor

from kafka import KafkaConsumer, KafkaProducer
import json, time
from collections import defaultdict
from datetime import datetime, timedelta

class FraudDetector:
    """
    Real-time fraud detection using stream processing.
    
    Rules (simplified version of actual MNC rules):
    1. More than 5 transactions in 10 minutes from same card → suspicious
    2. Transaction > $10,000 from a card that never spent > $500 → suspicious
    3. Same card used in two countries within 1 hour → impossible (physical)
    """
    
    def __init__(self):
        self.transaction_history = defaultdict(list)
        self.card_profiles = defaultdict(lambda: {"max_amount": 0, "countries": []})
        
        self.consumer = KafkaConsumer(
            "transactions",
            bootstrap_servers=['localhost:9092'],
            group_id="fraud-detection",
            value_deserializer=lambda m: json.loads(m.decode())
        )
        
        self.producer = KafkaProducer(
            bootstrap_servers=['localhost:9092'],
            value_serializer=lambda v: json.dumps(v).encode()
        )
    
    def is_velocity_fraud(self, card_id: str, timestamp: datetime) -> bool:
        """Rule 1: Too many transactions in short time"""
        recent = [
            t for t in self.transaction_history[card_id]
            if timestamp - t < timedelta(minutes=10)
        ]
        return len(recent) > 5
    
    def is_amount_anomaly(self, card_id: str, amount: float) -> bool:
        """Rule 2: Transaction much larger than historical max"""
        historical_max = self.card_profiles[card_id]["max_amount"]
        if historical_max > 0:
            return amount > historical_max * 20  # 20x jump is suspicious
        return False
    
    def is_geo_impossible(self, card_id: str, country: str, timestamp: datetime) -> bool:
        """Rule 3: Same card, different country, within 1 hour"""
        history = self.card_profiles[card_id]["countries"]
        for prev_country, prev_time in history:
            if prev_country != country and timestamp - prev_time < timedelta(hours=1):
                return True
        return False
    
    def process_transaction(self, txn: dict):
        card_id = txn["card_id"]
        amount = txn["amount"]
        country = txn["country"]
        timestamp = datetime.fromisoformat(txn["timestamp"])
        
        fraud_reasons = []
        
        if self.is_velocity_fraud(card_id, timestamp):
            fraud_reasons.append("velocity_anomaly")
        if self.is_amount_anomaly(card_id, amount):
            fraud_reasons.append("amount_anomaly")
        if self.is_geo_impossible(card_id, country, timestamp):
            fraud_reasons.append("geographic_impossibility")
        
        # Update history
        self.transaction_history[card_id].append(timestamp)
        self.card_profiles[card_id]["max_amount"] = max(
            self.card_profiles[card_id]["max_amount"], amount
        )
        self.card_profiles[card_id]["countries"].append((country, timestamp))
        
        if fraud_reasons:
            alert = {
                "transaction_id": txn["id"],
                "card_id": card_id,
                "amount": amount,
                "fraud_score": len(fraud_reasons) / 3,
                "reasons": fraud_reasons,
                "detected_at": datetime.now().isoformat(),
                "action": "BLOCK" if len(fraud_reasons) > 1 else "FLAG"
            }
            self.producer.send("fraud-alerts", value=alert)
            print(f"🚨 FRAUD DETECTED: Card {card_id[:8]}... | Score: {alert['fraud_score']:.0%} | Reasons: {fraud_reasons}")
            return alert
        
        print(f"✅ Clean: Card {card_id[:8]}... | ${amount:.2f} | {country}")
        return None
    
    def run(self):
        print("🔍 Fraud Detector started. Processing transaction stream...")
        for message in self.consumer:
            self.process_transaction(message.value)

if __name__ == "__main__":
    FraudDetector().run()
```

---

## Days 78–85: PROJECT 4 — Real-Time Data Platform

### Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                   REAL-TIME DATA PLATFORM                           │
│                                                                     │
│  Data Sources:                                                      │
│  [Web App Events] [Payment Service] [GPS Feed] [Partner APIs]      │
│         │                │               │           │             │
│         └────────────────┼───────────────┼───────────┘             │
│                          ▼                                          │
│              ┌───────────────────────┐                             │
│              │   Apache Kafka        │                             │
│              │   (Event Streaming)   │                             │
│              └───────────┬───────────┘                             │
│                          │                                          │
│         ┌────────────────┼────────────────┐                        │
│         ▼                ▼                ▼                        │
│  ┌─────────────┐  ┌──────────────┐  ┌──────────────┐              │
│  │  Airflow    │  │  Fraud       │  │  Analytics   │              │
│  │  (Batch     │  │  Detector    │  │  Aggregator  │              │
│  │  Pipelines) │  │  (Real-time) │  │  (Real-time) │              │
│  └──────┬──────┘  └──────┬───────┘  └──────┬───────┘              │
│         │                │                  │                      │
│         ▼                ▼                  ▼                      │
│  ┌──────────────────────────────────────────────────┐              │
│  │  PostgreSQL Data Warehouse                        │              │
│  │  (historical data, analytics tables)              │              │
│  └──────────────────────────────────────────────────┘              │
│                          ▼                                          │
│  ┌──────────────────────────────────────────────────┐              │
│  │  Grafana Dashboard                                │              │
│  │  (Real-time metrics, alerts, business KPIs)       │              │
│  └──────────────────────────────────────────────────┘              │
└─────────────────────────────────────────────────────────────────────┘
```

### Documentation: Project 4

**Platform:** GitHub + Grafana screenshot + Airflow DAG graph

**GitHub structure:**
```
real-time-data-platform/
├── dags/                 ← Airflow DAG files
├── consumers/            ← Kafka consumer services
├── producers/            ← Data source simulators
├── warehouse/            ← SQL schema + dbt models
├── dashboards/           ← Exported Grafana JSON
├── tests/                ← Data quality tests
├── docker-compose.yml    ← Start everything with one command
└── docs/
    ├── architecture.md   ← The architecture diagram above
    ├── data-flows.md     ← Which data flows where
    └── runbook.md        ← How to operate the system
```

**Blog post:** "How I Built a Real-Time Fraud Detection System Using Kafka and Python"

---

---

# ⚫ PHASE 5: DEVOPS + CLOUD + INFRASTRUCTURE (Days 86–100)

> **Goal:** Ship code reliably. Make systems observable. Automate everything. This is what makes the difference between "it works on my laptop" and "it works for 10 million users."

---

## Days 86–89: Docker — The Container Revolution

### Why Docker Changed Everything

**Before Docker:**
- "It works on my machine" was a real, expensive problem
- Setting up a development environment took days
- "Works in staging, fails in production" was common and mysterious
- Deploying meant SSHing into servers and running scripts manually

**After Docker:**
- Your app + its dependencies are packaged into one image
- Run `docker-compose up` and the entire stack starts in seconds
- The same image runs in development, testing, staging, and production
- No "works on my machine" — because it runs in the same environment everywhere

### Optimized Dockerfile: Reduce Image Size from 900MB to 100MB

```dockerfile
# ❌ BEGINNER DOCKERFILE (900MB image):
FROM node:18                    # Full Node.js image (900MB)
WORKDIR /app
COPY . .
RUN npm install                  # Installs dev dependencies too
CMD ["node", "server.js"]

# ✅ PRODUCTION DOCKERFILE (80MB image):
# Stage 1: Build stage (install deps, compile TypeScript, etc.)
FROM node:18-alpine AS builder  # Alpine is tiny (5MB vs 900MB)
WORKDIR /app
COPY package*.json ./
RUN npm ci --only=production    # Only production deps, exact versions
COPY . .

# Stage 2: Runtime stage (only what's needed to RUN the app)
FROM node:18-alpine AS runtime
WORKDIR /app
RUN addgroup -S appgroup && adduser -S appuser -G appgroup  # Non-root user (security!)
COPY --from=builder /app/node_modules ./node_modules
COPY --from=builder /app/src ./src
USER appuser                    # Run as non-root
EXPOSE 8000
CMD ["node", "src/server.js"]
```

### Docker Compose for the Full Stack

```yaml
# docker-compose.yml — Start your entire development environment
version: '3.8'

services:
  # Your application
  api:
    build: .
    ports:
      - "8000:8000"
    environment:
      DATABASE_URL: postgresql://devuser:devpass@db:5432/devdb
      REDIS_URL: redis://cache:6379
      KAFKA_BROKERS: kafka:9092
    depends_on:
      db:
        condition: service_healthy      # Wait for DB to be ready
      cache:
        condition: service_started
    volumes:
      - ./src:/app/src                  # Mount source for hot-reload in dev
    networks:
      - app-network
    restart: unless-stopped

  # PostgreSQL Database
  db:
    image: postgres:16-alpine
    environment:
      POSTGRES_DB: devdb
      POSTGRES_USER: devuser
      POSTGRES_PASSWORD: devpass
    volumes:
      - postgres_data:/var/lib/postgresql/data     # Persist data across restarts
      - ./database/init.sql:/docker-entrypoint-initdb.d/init.sql  # Run on first start
    ports:
      - "5432:5432"
    healthcheck:
      test: ["CMD-SHELL", "pg_isready -U devuser -d devdb"]
      interval: 10s
      timeout: 5s
      retries: 5
    networks:
      - app-network

  # Redis Cache
  cache:
    image: redis:7-alpine
    ports:
      - "6379:6379"
    command: redis-server --maxmemory 256mb --maxmemory-policy allkeys-lru
    networks:
      - app-network

  # Prometheus monitoring
  prometheus:
    image: prom/prometheus:latest
    volumes:
      - ./monitoring/prometheus.yml:/etc/prometheus/prometheus.yml
    ports:
      - "9090:9090"
    networks:
      - app-network

  # Grafana dashboards
  grafana:
    image: grafana/grafana:latest
    ports:
      - "3000:3000"
    environment:
      GF_SECURITY_ADMIN_PASSWORD: admin
    volumes:
      - grafana_data:/var/lib/grafana
    networks:
      - app-network

volumes:
  postgres_data:
  grafana_data:

networks:
  app-network:
    driver: bridge
```

---

## Days 90–93: Kubernetes — The Cloud Operating System

### Why Kubernetes After Docker

Docker runs ONE instance of your container. Kubernetes manages HUNDREDS of containers across DOZENS of servers, automatically:
- Restarts crashed containers
- Scales up when traffic spikes (adds more containers)
- Scales down when traffic drops (removes containers to save money)
- Routes traffic only to healthy containers
- Rolls out new versions without downtime

### Your First Kubernetes Deployment

```yaml
# k8s/deployment.yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: api-deployment
  labels:
    app: api
spec:
  replicas: 3                     # Run 3 instances of your app
  selector:
    matchLabels:
      app: api
  strategy:
    type: RollingUpdate
    rollingUpdate:
      maxUnavailable: 1           # Keep 2/3 running during deployment
      maxSurge: 1                 # Can temporarily run 4 instances
  template:
    metadata:
      labels:
        app: api
    spec:
      containers:
        - name: api
          image: your-registry/api:v1.2.3
          ports:
            - containerPort: 8000
          resources:
            requests:             # Minimum guaranteed resources
              memory: "128Mi"
              cpu: "100m"         # 100 millicores = 0.1 CPU
            limits:               # Maximum allowed resources
              memory: "512Mi"
              cpu: "500m"
          env:
            - name: DATABASE_URL
              valueFrom:
                secretKeyRef:     # Secrets stored in Kubernetes, not in code!
                  name: db-secret
                  key: url
          readinessProbe:         # Don't send traffic until app is ready
            httpGet:
              path: /health
              port: 8000
            initialDelaySeconds: 10
            periodSeconds: 5
          livenessProbe:          # Restart if app stops responding
            httpGet:
              path: /health
              port: 8000
            failureThreshold: 3
            periodSeconds: 10
```

```bash
# Start a local Kubernetes cluster
minikube start --memory=4096 --cpus=2

# Deploy your app
kubectl apply -f k8s/deployment.yaml
kubectl apply -f k8s/service.yaml

# Monitor the deployment
kubectl get pods                # See pod status
kubectl get deployments         # See deployment status
kubectl describe pod api-xxx    # Debug a specific pod
kubectl logs api-xxx            # See logs from a pod

# Scale manually
kubectl scale deployment api-deployment --replicas=5

# Simulate a pod crash and watch it auto-restart
kubectl delete pod api-xxx      # Kubernetes immediately creates a replacement!
```

---

## Days 94–97: CI/CD Pipelines

### The Professional GitHub Actions Pipeline

```yaml
# .github/workflows/main.yml
name: CI/CD Pipeline

on:
  push:
    branches: [main]
  pull_request:
    branches: [main]

env:
  REGISTRY: ghcr.io
  IMAGE_NAME: ${{ github.repository }}

jobs:
  # ===== JOB 1: TEST =====
  test:
    name: Test & Lint
    runs-on: ubuntu-latest
    
    services:
      postgres:
        image: postgres:16
        env:
          POSTGRES_PASSWORD: testpass
          POSTGRES_DB: testdb
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Set up Python
        uses: actions/setup-python@v4
        with:
          python-version: '3.12'
          cache: 'pip'
      
      - name: Install dependencies
        run: pip install -r requirements.txt
      
      - name: Lint with ruff
        run: ruff check .
      
      - name: Check types with mypy
        run: mypy src/
      
      - name: Run tests with coverage
        env:
          DATABASE_URL: postgresql://postgres:testpass@localhost/testdb
        run: pytest --cov=src --cov-report=xml --cov-fail-under=80
      
      - name: Upload coverage
        uses: codecov/codecov-action@v3
        with:
          files: coverage.xml

  # ===== JOB 2: SECURITY SCAN =====
  security:
    name: Security Scan
    runs-on: ubuntu-latest
    needs: test
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Dependency vulnerability scan
        uses: pypa/gh-action-pip-audit@v1
        with:
          inputs: requirements.txt
      
      - name: Secret scan
        uses: gitleaks/gitleaks-action@v2
        env:
          GITHUB_TOKEN: ${{ secrets.GITHUB_TOKEN }}

  # ===== JOB 3: BUILD & PUSH IMAGE =====
  build:
    name: Build Docker Image
    runs-on: ubuntu-latest
    needs: [test, security]
    if: github.ref == 'refs/heads/main'
    
    outputs:
      image-tag: ${{ steps.meta.outputs.tags }}
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Log in to GitHub Container Registry
        uses: docker/login-action@v3
        with:
          registry: ${{ env.REGISTRY }}
          username: ${{ github.actor }}
          password: ${{ secrets.GITHUB_TOKEN }}
      
      - name: Extract metadata
        id: meta
        uses: docker/metadata-action@v5
        with:
          images: ${{ env.REGISTRY }}/${{ env.IMAGE_NAME }}
          tags: |
            type=sha,prefix=sha-
            type=semver,pattern={{version}}
            latest
      
      - name: Build and push
        uses: docker/build-push-action@v5
        with:
          context: .
          push: true
          tags: ${{ steps.meta.outputs.tags }}
          cache-from: type=gha
          cache-to: type=gha,mode=max

  # ===== JOB 4: DEPLOY TO STAGING =====
  deploy-staging:
    name: Deploy to Staging
    runs-on: ubuntu-latest
    needs: build
    environment: staging
    
    steps:
      - uses: actions/checkout@v4
      
      - name: Update Kubernetes deployment
        run: |
          # In production: use kubectl or ArgoCD
          echo "Deploying image: ${{ needs.build.outputs.image-tag }}"
          echo "To staging Kubernetes cluster..."
```

---

## Days 98–100: Observability — The Three Pillars

### Metrics (Prometheus + Grafana)

```python
# Add metrics instrumentation to your FastAPI app
from prometheus_client import Counter, Histogram, Gauge, generate_latest
from fastapi import FastAPI, Request
import time

app = FastAPI()

# Define metrics
REQUEST_COUNT = Counter(
    "http_requests_total",
    "Total HTTP requests",
    ["method", "endpoint", "status_code"]
)

REQUEST_LATENCY = Histogram(
    "http_request_duration_seconds",
    "HTTP request latency",
    ["method", "endpoint"],
    buckets=[0.01, 0.025, 0.05, 0.1, 0.25, 0.5, 1.0, 2.5, 5.0]
)

ACTIVE_CONNECTIONS = Gauge(
    "active_connections",
    "Number of active connections"
)

# Middleware to automatically track all requests
@app.middleware("http")
async def track_metrics(request: Request, call_next):
    ACTIVE_CONNECTIONS.inc()
    start_time = time.time()
    
    response = await call_next(request)
    
    duration = time.time() - start_time
    REQUEST_COUNT.labels(
        method=request.method,
        endpoint=request.url.path,
        status_code=response.status_code
    ).inc()
    REQUEST_LATENCY.labels(
        method=request.method,
        endpoint=request.url.path
    ).observe(duration)
    ACTIVE_CONNECTIONS.dec()
    
    return response

# Endpoint for Prometheus to scrape metrics
@app.get("/metrics")
async def metrics():
    return generate_latest()
```

### PROJECT 5: Full Production Deployment Pipeline

**Deliverable:** The food delivery backend (Project 3) fully deployed with:
- Docker images in GitHub Container Registry
- Kubernetes deployment with 3 replicas
- GitHub Actions CI/CD that auto-deploys on merge to main
- Prometheus metrics collecting from all services
- Grafana dashboard showing RPS, latency p99, error rate
- Alerts configured for error rate > 1%

**Documentation:** This is the most complex project to document. Do it properly.

---

---

# 🟣 PHASE 6: SYSTEM DESIGN AT SCALE (Days 101–120)

> **Goal:** Learn to design systems that handle millions of users, billions of events, and global traffic. This is the capstone. Every prior phase was preparation for this.

---

## Days 101–103: Scalability Foundations

### The Numbers Every System Designer Must Know

```
Operation                    Latency
━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━━
L1 cache reference           0.5 ns
Branch misprediction         5 ns
L2 cache reference           7 ns
Mutex lock/unlock            25 ns
Main memory reference        100 ns
Compress 1K bytes with Zip   3,000 ns (3 μs)
Send 1K bytes over 1Gbps LAN 10,000 ns (10 μs)
Read 4K randomly from SSD    150,000 ns (150 μs)
Read 1MB sequentially from SSD 1,000,000 ns (1 ms)
Disk seek                    10,000,000 ns (10 ms)
Read 1MB sequentially from disk 20,000,000 ns (20 ms)
Send packet CA → Netherlands 150,000,000 ns (150 ms)

USE THESE IN SYSTEM DESIGN: "We need < 100ms latency.
A single disk seek is 10ms. So if one request needs 10+ disk seeks, 
we need caching. Here's where I'd add Redis..."
```

### The Scalability Toolkit

```
VERTICAL SCALING (Scale Up): Bigger machine
  Pros: Simple, no code changes
  Cons: Expensive, single point of failure, has a ceiling

HORIZONTAL SCALING (Scale Out): More machines
  Pros: No ceiling, fault tolerant, cheaper commodity hardware
  Cons: Need load balancer, distributed state management, complex

LOAD BALANCING:
  Round Robin: Request 1→Server A, Request 2→Server B, Request 3→Server C
  Least Connections: Route to server with fewest active connections
  IP Hash: Same client always goes to same server (session affinity)
  
  Tools: Nginx (free), HAProxy (free), AWS ALB, Cloudflare

DATABASE SCALING:
  Read Replicas: Write to Primary, Read from Replicas
  Sharding: Split data by key across multiple databases
  CQRS: Separate read and write databases entirely
  
CACHING LAYERS:
  CDN: Cache static files globally (CSS, JS, images)
  Redis: Cache database query results, sessions
  Application cache: In-process memory (fastest, but per-server)
```

---

## Days 104–108: System Design Case Studies

### Design Twitter (The Feed Problem)

**The Core Problem:** When Taylor Swift tweets, 90 million followers need to see it in their feed. How?

```
APPROACH 1: PUSH MODEL (Fan-out on write)
  When Taylor posts:
  → Write tweet to database
  → For each of 90M followers: append tweet_id to their feed cache

  Problem: 90 million cache writes in seconds. System overwhelmed.
  Used by: Regular users

APPROACH 2: PULL MODEL (Fan-out on read)
  When you open Twitter:
  → Find everyone you follow
  → Fetch their latest tweets
  → Merge and rank them

  Problem: If you follow 2000 people, that's 2000 database queries per open.
  Used by: Celebrity accounts (Taylor Swift) — their followers PULL the celebrity's content

TWITTER'S ACTUAL SOLUTION: HYBRID
  Normal users: Push model (precomputed feeds in Redis)
  Celebrities (>1M followers): Pull model (their tweets pulled at read time)
  The feed service merges both lists in real-time

ARCHITECTURE:
  Client → Feed Service
             ↓
         [Redis Cache]     ← Precomputed feed for normal follows
             ↓ (if miss or celebrity follows)
         [Tweet DB]        ← Live tweets from celebrities
             ↓
         Merge + Rank + Return
```

### Design Uber's Real-Time Location System

```
CHALLENGE:
- 5 million active drivers
- Each sends GPS coordinates every 4 seconds
- Riders need to see nearby drivers in < 1 second
- Need to find all drivers within X km of any point

MATH:
  5M drivers × 1 write per 4 seconds = 1.25M writes/second
  At peak: maybe 2M writes/second
  This CANNOT go to PostgreSQL (handles ~10,000 writes/second)

SOLUTION:
1. GPS writes go to Redis (not Postgres)
   Redis can handle 1M+ operations/second
   Driver location stored as: driver:{id} → geospatial data
   
2. Redis Geo Index for spatial queries
   GEOADD drivers:active {longitude} {latitude} {driver_id}
   GEORADIUS drivers:active {lat} {lng} 5 km → returns nearby driver IDs
   
3. PostgreSQL for permanent storage
   Async write: Kafka consumer writes GPS trails to PostgreSQL
   For analytics, billing, dispute resolution (not real-time)
   
4. WebSocket connection to driver app
   Driver app opens WebSocket → Server reads from Redis → pushes nearby riders

CAPACITY:
  5M drivers × 100 bytes per location = 500MB in Redis
  Redis handles this comfortably in memory
```

### Design YouTube's Video Upload and Processing

```
CHALLENGE:
- 500 hours of video uploaded every minute
- Must support 1080p, 4K, mobile-optimized formats
- Global CDN delivery to 2 billion users
- Zero downtime

VIDEO UPLOAD FLOW:
1. Client uploads to Object Storage (S3 or GCS) directly
   (Using pre-signed URL — avoids routing through API server)
   
2. Upload complete → S3 triggers event → Kafka

3. Transcoding workers consume from Kafka:
   - Convert original to multiple formats: 360p, 720p, 1080p, 4K
   - Extract thumbnail at 3-second intervals
   - Generate VTT subtitle timing
   - This is CPU-intensive: use a job queue with auto-scaling workers

4. Transcoded videos stored in Object Storage

5. CDN (Cloudflare/Akamai) configured to pull from Object Storage
   - User in Chennai → CDN edge node in Chennai serves the video
   - No round-trip to US servers for each video chunk

6. Adaptive bitrate streaming (HLS/DASH):
   Player automatically switches quality based on connection speed
   Fast connection → serves 4K chunks
   Slow connection → drops to 360p seamlessly

STORAGE ESTIMATION:
  500 hours video/minute × 60 min × 24 hrs = 720,000 hours/day
  1 hour at 720p ≈ 1.5GB
  720,000 × 1.5GB = 1,080,000 GB = 1 PB/day (before multiple formats!)
  
  Multiple formats × 3 = 3 PB/day of new video storage
  
  → Must use tiered storage: hot content on fast SSDs, old content on HDDs
```

---

## Days 109–113: AI Integration in Modern Systems

### Vector Databases and RAG Architecture

```python
# phase-6-design/rag/rag_system.py
# Build a Retrieval-Augmented Generation system using local AI (no API costs)

from sentence_transformers import SentenceTransformer
import qdrant_client
from qdrant_client.models import Distance, VectorParams, PointStruct
import ollama  # Local LLM

class RAGSystem:
    """
    RAG = Retrieval-Augmented Generation
    
    How it works:
    1. Index your documents as vectors (embeddings)
    2. User asks a question
    3. Find the most relevant documents using vector similarity
    4. Send question + relevant docs to LLM
    5. LLM answers using ONLY the provided context
    
    Why this matters:
    - LLMs hallucinate (make up facts)
    - RAG grounds the LLM in YOUR data
    - Companies use this for: internal knowledge bases, customer support,
      product documentation, contract analysis
    """
    
    def __init__(self):
        # Embedding model: converts text to vectors
        self.embedder = SentenceTransformer("all-MiniLM-L6-v2")
        
        # Vector database: stores and searches vectors
        self.vector_db = qdrant_client.QdrantClient(":memory:")  # In-memory for demo
        
        # Create collection
        self.vector_db.create_collection(
            collection_name="documents",
            vectors_config=VectorParams(
                size=384,           # Dimension of all-MiniLM-L6-v2 vectors
                distance=Distance.COSINE  # Similarity metric
            )
        )
    
    def index_documents(self, documents: list[dict]):
        """Convert documents to vectors and store in Qdrant."""
        texts = [doc["content"] for doc in documents]
        vectors = self.embedder.encode(texts).tolist()
        
        points = [
            PointStruct(
                id=i,
                vector=vector,
                payload=doc
            )
            for i, (doc, vector) in enumerate(zip(documents, vectors))
        ]
        
        self.vector_db.upsert(collection_name="documents", points=points)
        print(f"✅ Indexed {len(documents)} documents")
    
    def retrieve_context(self, query: str, top_k: int = 3) -> list[dict]:
        """Find most relevant documents for a query."""
        query_vector = self.embedder.encode([query])[0].tolist()
        
        results = self.vector_db.search(
            collection_name="documents",
            query_vector=query_vector,
            limit=top_k,
            score_threshold=0.5  # Only return results with similarity > 50%
        )
        
        return [
            {**result.payload, "similarity_score": result.score}
            for result in results
        ]
    
    def answer_question(self, question: str) -> dict:
        """Full RAG pipeline: retrieve → augment → generate."""
        print(f"\n❓ Question: {question}")
        
        # 1. RETRIEVE relevant documents
        context_docs = self.retrieve_context(question)
        print(f"📚 Retrieved {len(context_docs)} relevant documents")
        
        if not context_docs:
            return {"answer": "I don't have information about this topic.", "sources": []}
        
        # 2. AUGMENT the prompt with context
        context_text = "\n\n".join([
            f"Source [{i+1}]: {doc['content']}"
            for i, doc in enumerate(context_docs)
        ])
        
        prompt = f"""Answer the following question using ONLY the provided context.
If the context doesn't contain enough information, say so honestly.

CONTEXT:
{context_text}

QUESTION: {question}

ANSWER:"""
        
        # 3. GENERATE answer using local LLM (Ollama + LLaMA3)
        response = ollama.generate(
            model="llama3",
            prompt=prompt,
            options={"temperature": 0.1}  # Low temperature = more factual
        )
        
        return {
            "question": question,
            "answer": response["response"],
            "sources": context_docs,
            "confidence": "high" if context_docs[0]["similarity_score"] > 0.8 else "medium"
        }


# ===== Demo =====
rag = RAGSystem()

# Index company documentation
docs = [
    {"title": "Refund Policy", "content": "Customers can request a full refund within 30 days of purchase. For digital products, refunds are available within 7 days if the product is unused."},
    {"title": "Shipping Policy", "content": "We ship to 50 countries. Standard shipping takes 5-7 business days. Express shipping (2-3 days) is available for $15 extra."},
    {"title": "Account Management", "content": "You can change your password in Settings > Account > Security. For a forgotten password, use the 'Forgot Password' link on the login page."},
    {"title": "Subscription Plans", "content": "We offer Basic ($9/month), Pro ($29/month), and Enterprise ($99/month) plans. Annual billing saves 20%."},
]

rag.index_documents(docs)

# Answer user questions
result = rag.answer_question("Can I get my money back after 2 weeks?")
print(f"\n💬 Answer: {result['answer']}")
print(f"📊 Confidence: {result['confidence']}")
```

---

## Days 114–120: CAPSTONE — Full-Stack Data Platform

### The Final Project

**Build:** A complete data platform for a fictional e-commerce company called "ShopNow"

**What it includes:**
1. **Event ingestion:** Every user action (page view, click, purchase) flows through Kafka
2. **Real-time processing:** Fraud detection runs on the transaction stream
3. **Batch processing:** Nightly Airflow job builds the recommendation model training data
4. **Data warehouse:** PostgreSQL with dbt transformations for analytics
5. **REST API + GraphQL:** For frontend consumption
6. **Monitoring:** Full Prometheus + Grafana stack with business KPIs
7. **CI/CD:** GitHub Actions → Docker → Kubernetes auto-deploy
8. **AI feature:** Product recommendation using vector similarity (pgvector)
9. **Security:** JWT auth, rate limiting, input validation, secret management

**Deployed on:** Minikube locally (production-equivalent architecture)

---

### The Capstone Documentation (Your Portfolio Centerpiece)

**GitHub Repository: `shopnow-data-platform`**

**README must include:**
```markdown
# ShopNow Data Platform

## Architecture
[Full system diagram — every service, database, and connection]

## What This Demonstrates
- [Pattern 1]: Real-time fraud detection using Kafka stream processing
- [Pattern 2]: ETL pipeline with Airflow for recommendation training data
- [Pattern 3]: CQRS — separate read/write paths for orders
- [Pattern 4]: Event-driven notifications (order status updates)
- [Pattern 5]: RAG-based product search using pgvector

## System Design Decisions
[Link to ADR-001: Why Kafka over RabbitMQ]
[Link to ADR-002: Why PostgreSQL over MongoDB for orders]
[Link to ADR-003: Why Kubernetes over ECS]

## Performance
| Metric | Value |
|--------|-------|
| API p99 latency | 45ms |
| Kafka throughput | 50,000 events/s |
| Airflow job duration | 4 min |

## How to Run
docker-compose up -d   # Start everything
kubectl apply -f k8s/  # Deploy to Kubernetes

## What I'd Do Differently
[Honest reflection — shows maturity]
```

**Blog Post Series (Publish on Dev.to + Hashnode):**
1. "The Architecture of ShopNow: How I Designed a Complete E-Commerce Data Platform"
2. "From 0 to Kubernetes: My First Production Deployment"
3. "Building Real-Time Fraud Detection with Kafka in Python"
4. "How I Added AI-Powered Search to My E-Commerce Platform"
5. "120 Days of Engineering: What I Built, What I Learned, What I'd Do Differently"

---

---

# 📊 THE COMPLETE DAILY TIMETABLE

## Phase 0: Engineering Survival Kit (Days 0–7)

| Day | Morning (1.5h) | Afternoon (2h) | Evening (1h) | Output |
|-----|---------------|----------------|--------------|--------|
| 0 | Install Ubuntu, tools | GitHub setup | LinkedIn Day 0 post | Dev env ready |
| 1 | Linux terminal P1 | Explore /proc, investigate system | `day-01.md` | Push code |
| 2 | Python basics | Build systems_thinking.py | `day-02.md` | Push code |
| 3 | Git internals | Practice branching, git bisect | `day-03.md` | Blog draft |
| 4 | How internet works | curl experiments, DNS exploration | `day-04.md` | Push |
| 5 | Python data structures | Build engineer toolkit | `day-05.md` | |
| 6 | Python file I/O, error handling | Shell scripting | `day-06.md` | Push |
| 7 | Git workflow review | Write first blog post | Publish blog | **Phase 0 ✅** |

## Phase 1: The 20 Patterns (Days 8–28)

| Day | Morning (1.5h) | Afternoon (2h) | Evening (1h) | Output |
|-----|---------------|----------------|--------------|--------|
| 8 | CRUD pattern theory | Build todo_api.py | `day-08.md` | |
| 9 | CRUD: REST principles | Add SQLite persistence | `day-09.md` | LinkedIn |
| 10 | Client-Server pattern | Build simple_server.py | `day-10.md` | |
| 11 | Client-Server: HTTP methods | Test with curl + Postman | `day-11.md` | Push |
| 12 | ETL pattern: theory | Build stock_etl.py (extract) | `day-12.md` | |
| 13 | ETL: transform + load | Complete the pipeline | `day-13.md` | Blog post |
| 14 | Auth pattern: JWT theory | Build token generation | `day-14.md` | |
| 15 | Auth: bcrypt, refresh tokens | Complete auth flow | `day-15.md` | Push |
| 16 | Caching pattern | Build cache-aside | `day-16.md` | |
| 17 | Thundering herd + solutions | Implement request coalescing | `day-17.md` | LinkedIn |
| 18 | Event-Driven + Pub/Sub | Build event_system.py | `day-18.md` | |
| 19 | Producer-Consumer | Kafka setup + producer | `day-19.md` | Push |
| 20 | Batch vs Stream | Log analyzer (batch) | `day-20.md` | |
| 21 | MapReduce pattern | Word frequency MapReduce | `day-21.md` | Blog |
| 22 | Microservices pattern | Design service boundaries | `day-22.md` | |
| 23 | CQRS pattern | Separate read/write models | `day-23.md` | |
| 24 | Saga pattern | Build travel_booking_saga.py | `day-24.md` | LinkedIn |
| 25 | PROJECT 1 start | Set up FastAPI skeleton | `day-25.md` | |
| 26 | PROJECT 1: Core APIs | Implement CRUD + Auth | `day-26.md` | Push |
| 27 | PROJECT 1: Caching + ETL | Add Redis + CSV import | `day-27.md` | |
| 28 | PROJECT 1: Document + Deploy | README + blog post | README.md | **Project 1 ✅** |

## Phase 2: Web Foundations (Days 29–49)

| Day | Morning (1.5h) | Afternoon (2h) | Evening (1h) | Output |
|-----|---------------|----------------|--------------|--------|
| 29 | TCP/IP deep dive | Wireshark analysis | `day-29.md` | |
| 30 | HTTP 1 vs 2 vs 3 | curl timing comparisons | `day-30.md` | LinkedIn |
| 31 | DNS internals | dig +trace experiments | `day-31.md` | Push |
| 32 | JavaScript: Event Loop | Predict output exercises | `day-32.md` | |
| 33 | Closures + Prototype Chain | Build from scratch exercises | `day-33.md` | |
| 34 | Async/Await | Sequential vs parallel fetch | `day-34.md` | Blog |
| 35 | CSS: Critical Rendering Path | Inspect page load in DevTools | `day-35.md` | |
| 36 | Core Web Vitals | Lighthouse audit + fix | `day-36.md` | Push |
| 37 | Semantic HTML + Accessibility | Build accessible nav | `day-37.md` | |
| 38 | CSS Architecture (BEM/Tailwind) | Refactor CSS project | `day-38.md` | |
| 39 | Responsive Images | srcset + WebP experiment | `day-39.md` | LinkedIn |
| 40 | CSS Grid + Flexbox | Build complex layout | `day-40.md` | Push |
| 41 | PROJECT 2 start | Design + HTML skeleton | `day-41.md` | |
| 42 | PROJECT 2: CSS + Performance | Implement + measure | `day-42.md` | |
| 43 | PROJECT 2: CI/CD pipeline | GitHub Actions → Vercel | `day-43.md` | |
| 44 | PROJECT 2: Accessibility audit | Fix all a11y issues | `day-44.md` | |
| 45 | React internals: Virtual DOM | Debug re-render with Profiler | `day-45.md` | |
| 46 | React Hooks deep dive | Build custom hooks | `day-46.md` | Push |
| 47 | State management | Redux Toolkit + Zustand | `day-47.md` | Blog |
| 48 | Testing (Jest + Playwright) | Write tests for Project 2 | `day-48.md` | |
| 49 | PROJECT 2: Finalize + Blog | Polish + publish writeup | Blog post | **Project 2 ✅** |

## Phase 3: Backend + Databases (Days 50–70)

| Day | Morning (1.5h) | Afternoon (2h) | Evening (1h) | Output |
|-----|---------------|----------------|--------------|--------|
| 50 | REST API design principles | Build FastAPI skeleton | `day-50.md` | |
| 51 | Rate limiting + idempotency | Implement main.py patterns | `day-51.md` | Push |
| 52 | API security (JWT, CORS, CSP) | Build auth service | `day-52.md` | Blog |
| 53 | GraphQL + WebSockets | Add GraphQL endpoint | `day-53.md` | |
| 54 | PostgreSQL physical storage | Explore page structure | `day-54.md` | |
| 55 | Indexing + EXPLAIN ANALYZE | 1M row benchmark | `day-55.md` | LinkedIn |
| 56 | Transaction isolation | Reproduce all 4 anomalies | `day-56.md` | Push |
| 57 | MVCC + WAL internals | Read PostgreSQL source docs | `day-57.md` | |
| 58 | Redis: caching patterns | Implement Cache-Aside | `day-58.md` | |
| 59 | Redis: more patterns | Write-Through + TTL | `day-59.md` | Blog |
| 60 | Kafka setup + producers | Place order events | `day-60.md` | |
| 61 | Kafka consumers + groups | Email + inventory consumers | `day-61.md` | Push |
| 62 | Schema design: Uber | Design trips, rides, payments | `day-62.md` | |
| 63 | PROJECT 3 architecture | Service design document | `day-63.md` | |
| 64 | PROJECT 3: Auth + Order | Two services working | `day-64.md` | Push |
| 65 | PROJECT 3: Restaurant + Driver | Two more services | `day-65.md` | |
| 66 | PROJECT 3: Kafka integration | Events flowing | `day-66.md` | |
| 67 | PROJECT 3: Redis caching | Cache layer added | `day-67.md` | Push |
| 68 | PROJECT 3: API Gateway | Nginx routing | `day-68.md` | |
| 69 | PROJECT 3: Docker Compose | Everything in one command | `day-69.md` | Blog |
| 70 | PROJECT 3: Document + test | Load test + blog | README.md | **Project 3 ✅** |

## Phase 4: Data Engineering (Days 71–85)

| Day | Morning (1.5h) | Afternoon (2h) | Evening (1h) | Output |
|-----|---------------|----------------|--------------|--------|
| 71 | Data engineering landscape | Corporate data flows | `day-71.md` | |
| 72 | Airflow fundamentals | Install + first DAG | `day-72.md` | |
| 73 | Airflow: operators + XCom | Build stock_etl_dag.py | `day-73.md` | Blog |
| 74 | Batch vs Stream processing | Conceptual comparison | `day-74.md` | |
| 75 | Kafka Streams: theory | Stream processing patterns | `day-75.md` | |
| 76 | Build fraud_detector.py | Complete stream processor | `day-76.md` | LinkedIn |
| 77 | Data quality + contracts | Add validation layer | `day-77.md` | Push |
| 78 | PROJECT 4 design | Architecture design doc | `day-78.md` | |
| 79 | PROJECT 4: Kafka topics | Event schema design | `day-79.md` | |
| 80 | PROJECT 4: Airflow DAGs | All pipelines running | `day-80.md` | Push |
| 81 | PROJECT 4: Fraud detection | Stream processor live | `day-81.md` | |
| 82 | PROJECT 4: Grafana dashboard | Metrics visualized | `day-82.md` | |
| 83 | PROJECT 4: Data quality | Automated checks | `day-83.md` | Blog |
| 84 | PROJECT 4: Docker Compose | Full stack running | `day-84.md` | Push |
| 85 | PROJECT 4: Document + blog | Architecture writeup | Blog post | **Project 4 ✅** |

## Phase 5: DevOps + Cloud (Days 86–100)

| Day | Morning (1.5h) | Afternoon (2h) | Evening (1h) | Output |
|-----|---------------|----------------|--------------|--------|
| 86 | Docker fundamentals | Build optimized Dockerfile | `day-86.md` | |
| 87 | Docker multi-stage builds | 900MB → 80MB reduction | `day-87.md` | LinkedIn |
| 88 | Docker Compose advanced | Full stack compose file | `day-88.md` | Push |
| 89 | Docker networking + security | Trivy scan + non-root | `day-89.md` | |
| 90 | Kubernetes: Pods + Services | minikube first deploy | `day-90.md` | |
| 91 | Kubernetes: Deployments | Rolling update demo | `day-91.md` | Blog |
| 92 | Kubernetes: Ingress + Helm | Helm chart for Project 3 | `day-92.md` | Push |
| 93 | GitHub Actions: CI pipeline | Test + lint + build | `day-93.md` | |
| 94 | GitHub Actions: CD pipeline | Auto-deploy to minikube | `day-94.md` | |
| 95 | Terraform: IaC basics | Provision local infra | `day-95.md` | LinkedIn |
| 96 | Prometheus: metrics | Instrument FastAPI | `day-96.md` | Push |
| 97 | Grafana: dashboards | Build SLO dashboard | `day-97.md` | |
| 98 | ELK Stack: logging | Centralized log search | `day-98.md` | Blog |
| 99 | OpenTelemetry: tracing | Distributed trace demo | `day-99.md` | Push |
| 100 | PROJECT 5: Full pipeline | All integrated | README.md | **Project 5 ✅** |

## Phase 6: System Design (Days 101–120)

| Day | Morning (1.5h) | Afternoon (2h) | Evening (1h) | Output |
|-----|---------------|----------------|--------------|--------|
| 101 | Scalability math | Latency numbers exercise | `day-101.md` | |
| 102 | Load balancing + CDN | Nginx config practice | `day-102.md` | |
| 103 | Database scaling patterns | Read replicas + sharding | `day-103.md` | Blog |
| 104 | Design Twitter feed | Full design doc | Design doc | LinkedIn |
| 105 | Design Uber location | Full design doc | Design doc | |
| 106 | Design YouTube upload | Full design doc | Design doc | Push |
| 107 | Design WhatsApp messaging | Full design doc | Design doc | Blog |
| 108 | Design rate limiter | Full design doc | Design doc | |
| 109 | CAP theorem + Raft | raft.github.io exploration | `day-109.md` | |
| 110 | Vector databases + RAG | Build rag_system.py | `day-110.md` | Push |
| 111 | AI in systems (scheduling, search) | Research + document | `day-111.md` | |
| 112 | CAPSTONE: Architecture design | Full system design doc | Design doc | |
| 113 | CAPSTONE: Core services | 3 services running | `day-113.md` | |
| 114 | CAPSTONE: Data pipelines | Kafka + Airflow | `day-114.md` | Push |
| 115 | CAPSTONE: AI features | Vector search + RAG | `day-115.md` | |
| 116 | CAPSTONE: Full deployment | Kubernetes + CI/CD | `day-116.md` | |
| 117 | CAPSTONE: Monitoring | Complete observability | `day-117.md` | Blog |
| 118 | CAPSTONE: Load testing | k6 benchmark report | `day-118.md` | |
| 119 | Portfolio polish | All READMEs, LinkedIn | All updated | Push |
| 120 | Final blog post | "120 Days of Engineering" | Published | **Journey ✅** |

---

---

# 🏆 PROJECT PORTFOLIO SUMMARY

| # | Project | Real Problem Solved | Tech Stack | MNC Relevance |
|---|---------|---------------------|------------|---------------|
| **1** | Pattern Portfolio App | Demonstrates all 5 foundational patterns in one system | FastAPI, Redis, PostgreSQL, Docker | Proves breadth of pattern knowledge |
| **2** | High-Performance Landing Page | Client-side performance, 100/100 Lighthouse | HTML/CSS/JS, GitHub Actions, Vercel | Frontend + CI/CD basics |
| **3** | Food Delivery Backend | Microservices, async communication, polyglot persistence | FastAPI, Kafka, Redis, MongoDB, Nginx | Backend MNC-grade architecture |
| **4** | Real-Time Data Platform | Stream processing, batch pipelines, fraud detection | Kafka, Airflow, PostgreSQL, Grafana | Data engineering stack |
| **5** | Full Production Deployment | CI/CD, containers, orchestration, observability | Docker, Kubernetes, GitHub Actions, Prometheus | DevOps / SRE skills |
| **6** | ShopNow Data Platform (Capstone) | End-to-end: events → processing → APIs → AI → monitoring | Every tool in the stack | Staff-level portfolio piece |

---

# 🎯 INTERVIEW READINESS CHECKLIST

By Day 120, answer every one of these without hesitation:

### Patterns & Architecture
- [ ] Explain ETL vs ELT. When do you use each?
- [ ] What is event-driven architecture? Name 3 real systems that use it.
- [ ] Explain the Saga pattern. When would you use Saga over 2PC?
- [ ] What is CQRS? What problem does it solve?
- [ ] Why do microservices need a message queue? Why not just call each other directly?

### Web & Networking
- [ ] What happens between pressing Enter and seeing a webpage?
- [ ] What is Head-of-Line blocking? How does HTTP/2 solve it? Why does HTTP/3 solve it better?
- [ ] What is the JavaScript Event Loop? Why does blocking the main thread cause UI freezes?
- [ ] What are Core Web Vitals? How would you optimize LCP?

### Backend & Databases
- [ ] Design a rate limiter using Redis.
- [ ] Explain database transaction isolation levels with concrete examples of what goes wrong at each.
- [ ] Why does PostgreSQL use MVCC instead of locking?
- [ ] When would you use Kafka over RabbitMQ? What's the key architectural difference?

### Data Engineering
- [ ] What is Apache Airflow? What problem does it solve that a cron job doesn't?
- [ ] What is the difference between batch and stream processing? Give a use case for each.
- [ ] A Kafka topic has 3 partitions and you have 5 consumers in the same group. What happens?
- [ ] What is data quality? Name 4 data quality dimensions.

### DevOps & Cloud
- [ ] What is the difference between a Docker image and a container?
- [ ] Explain Kubernetes pods, deployments, and services. What does each do?
- [ ] What is a rolling deployment? What is a canary deployment? When do you use each?
- [ ] What are the three pillars of observability? What tool do you use for each?

### System Design
- [ ] Design Twitter's feed system. How does fan-out on write vs fan-out on read work?
- [ ] How does Uber track 5 million driver locations in real-time?
- [ ] What is the CAP theorem? Give a CP system and an AP system example.
- [ ] How would you scale a database that's receiving 1 million writes per second?

---

# 📣 WEEKLY BLOG POST CALENDAR

| Week | Title | Platform | Phase |
|------|-------|----------|-------|
| 1 | "120 Days, Zero Experience: My Engineering Roadmap" | LinkedIn Article | Phase 0 |
| 2 | "The 20 Logic Patterns That Explain Every Software System" | Dev.to | Phase 1 |
| 3 | "I Built 5 Engineering Patterns in One App: Here's What I Learned" | Hashnode | Phase 1 |
| 4 | "What Actually Happens When You Press Enter in Your Browser" | Dev.to | Phase 2 |
| 5 | "JavaScript's Event Loop: The Concept That Changed How I Think About Code" | Hashnode | Phase 2 |
| 6 | "Building a 100/100 Lighthouse Score Page from Scratch" | Dev.to | Phase 2 |
| 7 | "API Design Mistakes I Made and How MNCs Do It Properly" | Hashnode | Phase 3 |
| 8 | "How PostgreSQL Actually Stores Your Data (And Why It Changes Everything)" | Dev.to | Phase 3 |
| 9 | "I Built a Food Delivery Backend with 5 Microservices: Architecture and Lessons" | Hashnode | Phase 3 |
| 10 | "What Data Engineers Actually Do All Day: A Beginner's Guide" | Dev.to | Phase 4 |
| 11 | "Building Real-Time Fraud Detection with Kafka in Python" | Hashnode | Phase 4 |
| 12 | "Docker Multi-Stage Builds: Reducing Image Size from 900MB to 80MB" | Dev.to | Phase 5 |
| 13 | "My First Kubernetes Deployment: What No Tutorial Tells You" | Hashnode | Phase 5 |
| 14 | "Designing Twitter's Feed System: A System Design Case Study" | Dev.to | Phase 6 |
| 15 | "Building an AI-Powered Search with pgvector and LLaMA3 Locally" | Hashnode | Phase 6 |
| 16 | "120 Days of Engineering: Everything I Built, Broke, and Learned" | LinkedIn Article | Capstone |
| 17 | "The ShopNow Data Platform: My Capstone Architecture Explained" | Dev.to | Capstone |

---

> ## 📌 The Core Truth About Documentation
>
> **Documentation is not what you write after building something. It is what proves you built it.**
>
> A recruiter cannot run your code. An engineering manager cannot sit with you for 8 hours while you explain your project. A technical interviewer has 45 minutes.
>
> Your documentation must answer, without you being in the room:
> - "Did this person actually build this?"
> - "Do they understand WHY the design decisions were made?"
> - "Can they communicate engineering work professionally?"
> - "Would I trust this person to work on production systems?"
>
> Answer all four questions with every project you document. The code is the proof of the work. The writing is the proof of the understanding. Both are necessary. Neither is sufficient alone.
>
> **Start on Day 0. Commit every day. Publish every week. The documentation is the career.**

---

*Combined Roadmap v1.0 | Synthesized from: Data Engineering for Freshers, Tech Patterns & Projects, Web Development & System Design Interview Prep*
*Designed for: Zero-to-MNC-Grade Engineering in 120 Days*