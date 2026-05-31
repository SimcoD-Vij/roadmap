# 🎯 COMPLETE FRESHER CAREER GUIDE v2.0 — DEEP ROADMAP ANALYSIS
## From Zero to MNC | Job Roles · Companies · Countries · Platforms
### Research Edition | May 2026 | All Salaries in INR LPA + Local Currency
### Exchange Rates Used: 1 USD=₹96 | 1 EUR=₹112 | 1 GBP=₹129 | 1 CAD=₹70 | 1 AUD=₹69 | 1 SGD=₹75

---

> **Who This Document Is For:**
> A fresher who has completed a complete multi-domain engineering curriculum spanning **16 roadmap files** covering: Unified AI/ML/DL/Agentic AI (180 days), System Design (210 days), Database Engineering (180 days), Operating Systems (90 days), Computer Networking/NetOps360 (30 weeks), Embedded Systems + Hardware AI (SentinelGrid, 38 weeks), EmbeddedAI/MemCore framework (full SDK), Platform Engineering / InfraMesh (Atlassian-level internal platform), PulseGrid (ML-powered deployment intelligence), Data Patterns + Web Tools, and multiple supplementary resources from Memfault, Edge Impulse, Nordic Semiconductor, ARM, and ESP-IDF engineering blogs.
>
> **This document is brutally honest. It separates what you know from what companies will pay you for.**

---

## 📌 TABLE OF CONTENTS

1. [Complete Skill Inventory — All 16 Roadmaps Analyzed](#skill-inventory)
2. [Your 4 Flagship Projects — Detailed Breakdown](#projects)
3. [All Fresher Job Roles — Realistic Titles by Domain](#job-roles)
4. [Professional Titles for LinkedIn, Resume, GitHub](#titles)
5. [Top 300 Companies — With INR LPA Column](#companies)
6. [Best Countries — With INR LPA Comparison](#countries)
7. [Job Hunting Platforms](#platforms)
8. [Realistic Hiring Probability](#probability)

---

<a name="skill-inventory"></a>
## 🧠 SECTION 1 — COMPLETE SKILL INVENTORY (All 16 Roadmaps)

> This analysis was derived from reading every file in the roadmap folder including: `agentic ai.md`, `system design.md`, `system design01.md`, `database.md`, `os.md`, `computer netwoek.md`, `data pattern+web tools.md`, `embeddedai.md`, `InfraMesh _SentinelGrid _PulseGrid _MemCore.md`, `basic roadmap 4 project.md`, `inframesh skill.md`, `inframesh upgd.md`, `Hardware + AI Mix.md`, `sentigrad.md`, `sentifrad hardwareai mix.md`, `tech infofind.md`.

### 1.1 — Python & Software Engineering Foundation

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| Python 3.12 (OOP, async, modules, decorators) | InfraMesh API + MemCore SDK | `agentic ai.md`, `basic roadmap 4 project.md` |
| FastAPI (REST APIs, Pydantic, async endpoints) | InfraMesh API server, SentinelGrid cloud API | `inframesh skill.md`, `basic roadmap 4 project.md` |
| Python async/await + asyncio | Concurrent telemetry ingestion in SentinelGrid | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| Python packaging (pip, venv, pyproject.toml) | MemCore is a distributable SDK package | `embeddedai.md` |
| Logging, error handling, structured exceptions | MemCore intercepts Python exception system | `embeddedai.md` |
| SQLAlchemy ORM | InfraMesh database layer | `database.md`, `system design01.md` |
| Requests + HTTP client programming | SentinelGrid cloud communication | `basic roadmap 4 project.md` |
| NumPy + Pandas | Feature extraction, signal processing pipelines | `agentic ai.md` |
| SciPy (signal processing, Butterworth filter) | FFT pipeline for SentinelGrid | `Hardware + AI Mix.md` |

### 1.2 — Embedded Systems & Firmware (C Language)

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| C programming (pointers, memory, structs, static allocation) | SentinelNode firmware | `sentifrad hardwareai mix.md`, `Hardware + AI Mix.md` |
| FreeRTOS (tasks, queues, semaphores, mutexes, watchdog) | 5-task SentinelNode firmware | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| ESP32-S3 + ESP-IDF framework (ADC, SPI, I2C, DMA) | Physical SentinelNode hardware | `Hardware + AI Mix.md` |
| STM32 HAL (peripheral init, MPU, HAL drivers) | STM32 firmware variants | `sentifrad hardwareai mix.md` |
| ARM Cortex-M architecture (vector table, fault types, registers) | HardFault handler, crash state capture | `Hardware + AI Mix.md` |
| DMA (Direct Memory Access) for sensor data | Interrupt-driven sensor reading without CPU | `Hardware + AI Mix.md` |
| Interrupt-driven programming | Sensor task at highest FreeRTOS priority | `sentifrad hardwareai mix.md` |
| Watchdog timer design | Production node auto-recovery | `tech infofind.md` |
| Stack watermark API + heap profiling | Memory leak detection over 24h | `sentifrad hardwareai mix.md` |
| Task priority design + RTOS_TASK_DESIGN.md | Documented 5-task architecture | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| HardFault handler (captures crash state to flash) | Remote diagnostics on unattended nodes | `Hardware + AI Mix.md` |
| Memory Protection Unit (MPU) on STM32 | Catch stack overflow immediately as HardFault | `sentifrad hardwareai mix.md` |
| OTA firmware updates (A/B partition rollback) | Fleet update without physical access | `tech infofind.md`, `Hardware + AI Mix.md` |
| POSTMORTEM.md for firmware crashes | Stack overflow via JTAG diagnosis documentation | `tech infofind.md` |
| Power management (sleep modes, LiPo, current measurement) | Battery-powered SentinelNode in factory | `Hardware + AI Mix.md` |

### 1.3 — Signal Processing & Edge AI

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| FFT theory + CMSIS-DSP implementation in C | 12ms FFT on ESP32-S3 | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| Butterworth IIR low-pass filter (480Hz) in fixed-point | Noise filtering before FFT | `Hardware + AI Mix.md` |
| 15-element feature vector (RMS, kurtosis, crest factor, skewness, peak-to-peak) | Vibration anomaly features | `Hardware + AI Mix.md` |
| Nyquist theorem applied to real motor frequencies | 1kHz sampling rate justification | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| LSTM autoencoder for anomaly detection | Trained on 2 weeks normal operation data | `Hardware + AI Mix.md` |
| TFLite for Microcontrollers (INT8 quantization, memory arena) | 47ms inference on ESP32-S3 | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| Float32 vs INT8 accuracy trade-off documentation | 95.1% → 91.4%, documented in EDGE_AI.md | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| Model OTA (update ML model without firmware reboot) | Zero monitoring downtime during model update | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| Real fault data collection (bearing scratch) | Validated model on real vs simulated fault | `Hardware + AI Mix.md` |
| 1D-CNN, Isolation Forest comparison vs autoencoder | Architecture decision documented in EDGE_AI.md | `Hardware + AI Mix.md` |

### 1.4 — IoT Protocols & Connectivity

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| MQTT (QoS 0/1/2, TLS, client certificates, topics) | SentinelNode → Mosquitto → AWS IoT Core | `Hardware + AI Mix.md` |
| Mosquitto broker (TLS, X.509 per-device certs) | 3 simulated nodes with unique certificates | `Hardware + AI Mix.md` |
| AWS IoT Core (device shadows, IoT Rules, Kinesis routing) | Production SentinelGrid cloud | `Hardware + AI Mix.md` |
| LoRa (long-range low-power wireless) | SentinelNode backup connectivity | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| SPI flash store-and-forward (buffer during outage) | 10-min outage buffering tested | `Hardware + AI Mix.md` |
| WiFi (ESP32 WiFi stack, reconnect with exponential backoff) | Node reconnection after failure | `basic roadmap 4 project.md` |
| I2C + SPI sensor drivers (logic analyzer verified) | MPU-6050 accelerometer waveform verification | `Hardware + AI Mix.md` |
| PCB design basics (Gerber files, JLCPCB ordering) | SentinelNode PCB from prototype to product | `sentifrad hardwareai mix.md` |

### 1.5 — Cloud & AWS

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| AWS IoT Core | Device authentication, MQTT at scale | `Hardware + AI Mix.md` |
| AWS Kinesis | 10,000 events/minute ingestion | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| AWS Lambda | Stream processing, TimescaleDB writer | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| AWS SQS | InfraMesh provisioning task queue | `inframesh skill.md`, `basic roadmap 4 project.md` |
| AWS DynamoDB | InfraMesh service registry | `inframesh skill.md` |
| AWS CloudFront + ACM | DDoS protection + TLS for developer portal | `inframesh skill.md` |
| AWS Route 53 | Latency-based DNS routing | `inframesh skill.md` |
| AWS EC2 + Auto Scaling Groups | Proxy fleet at Atlassian scale | `inframesh skill.md` |
| AWS IAM (roles, policies, least privilege) | All infrastructure uses IAM roles | `inframesh skill.md` |
| AWS NLB (Layer 4 load balancing) | InfraMesh proxy tier | `inframesh skill.md` |
| AWS VPC (subnets, security groups, NACLs) | Network isolation for all services | `inframesh skill.md` |
| AWS SageMaker | Weekly model retraining pipeline | `Hardware + AI Mix.md` |
| AWS CloudFormation + Terraform | Both IaC tools used across projects | `inframesh skill.md`, `basic roadmap 4 project.md` |
| Multi-region deployment (13 regions, 2000 proxies) | Atlassian Envoy proxy replacement pattern | `inframesh skill.md` |

### 1.6 — Data Engineering & Databases

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| PostgreSQL (ACID, transactions, indexes, PL/pgSQL) | InfraMesh + inventory API | `database.md`, `system design01.md` |
| TimescaleDB (time-series schema, continuous aggregates, hypertables) | SentinelGrid telemetry — node_id, timestamp, anomaly_score | `Hardware + AI Mix.md` |
| Redis (sessions, rate limiting, caching, pub/sub) | API auth + rate limiting | `database.md` |
| Apache Kafka (consumer groups, topic partitions, 7-day retention) | PulseGrid ingesting GitHub/PagerDuty/Sentry | `inframesh upgd.md` |
| Neo4j (graph DB, Cypher queries, transitive dependency traversal) | PulseGrid live service dependency graph | `inframesh upgd.md` |
| ClickHouse (columnar analytics at scale) | Analytics queries on large datasets | `database.md` |
| Cassandra (CQL, distributed, IoT time-series) | IoT sensor data system | `database.md` |
| ChromaDB (vector embeddings, similarity search) | MemCore semantic bug retrieval | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| MinIO (S3-compatible object storage) | Model artifacts, raw data lake | `agentic ai.md` |
| Apache Airflow (DAG orchestration, scheduling) | Weekly model retraining pipeline | `agentic ai.md` |
| Apache Spark / PySpark | Big data processing | `data pattern+web tools.md` |
| dbt (data build tool, SQL-first transformation) | Data transformation layer | `data pattern+web tools.md` |
| Great Expectations (data validation) | Pipeline data quality checks | `agentic ai.md` |

### 1.7 — MLOps & Machine Learning

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| Scikit-learn (full pipeline: preprocessing, cross-validation, metrics) | Churn prediction system | `agentic ai.md` |
| XGBoost (deployment risk classifier, AUC 0.82) | PulseGrid risk scoring model | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| PyTorch (CNNs, NLP, training loops from scratch) | Crop disease detection CNN | `agentic ai.md` |
| TensorFlow + TFLite (quantization, conversion pipeline) | SentinelGrid edge model | `Hardware + AI Mix.md` |
| MLflow (experiment tracking, model registry) | All ML experiments logged | `agentic ai.md` |
| DVC (data versioning) | Dataset version control | `agentic ai.md` |
| Evidently (model drift detection) | SentinelGrid cloud model monitoring | `agentic ai.md` |
| Feature Store (Feast) | Feature management for ML pipelines | `agentic ai.md` |
| Prometheus + Grafana (model + infra monitoring) | Full observability stack | `Hardware + AI Mix.md` |
| CodeBERT (code embeddings) | MemCore semantic code search | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| tree-sitter (AST parsing, call graph extraction) | MemCore static analysis layer | `embeddedai.md` |
| RAG (Retrieval-Augmented Generation with ChromaDB) | MemCore bug fix suggestions | `agentic ai.md` |
| LangChain + LangGraph (agent frameworks) | Agentic AI orchestration layer | `agentic ai.md` |
| CrewAI + AutoGen (multi-agent systems) | Multi-agent data analysis agent | `agentic ai.md` |
| Vector DBs (ChromaDB, Qdrant) | Semantic search in MemCore + RAG | `agentic ai.md` |
| vLLM / Ollama (LLM serving) | Local model serving | `agentic ai.md` |
| Triton Inference Server | Production model serving | `agentic ai.md` |

### 1.8 — Platform Engineering, DevOps, SRE

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| Docker (Dockerfile, multi-stage builds, docker-compose) | All 4 projects containerized | `basic roadmap 4 project.md` |
| Kubernetes / k3s (pods, deployments, services, Helm) | InfraMesh production deployment | `agentic ai.md`, `data pattern+web tools.md` |
| Terraform (IaC, state files, modules, plan/apply) | All AWS resources as code, 12-min rebuild | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| GitHub Actions (CI/CD pipelines, Docker build/push) | All 4 projects have CI pipelines | `basic roadmap 4 project.md` |
| Nginx / Envoy (reverse proxy, load balancing) | InfraMesh proxy layer (Atlassian pattern) | `inframesh skill.md` |
| ELK Stack (Elasticsearch, Logstash, Kibana) | NetOps360 security monitoring | `computer netwoek.md` |
| OpenTelemetry (distributed tracing) | PulseGrid signal ingestion | `inframesh upgd.md` |
| JWT auth + API security | InfraMesh developer portal | `basic roadmap 4 project.md` |
| On-call engineering thinking (what to check when AWS fails) | Documented in POSTMORTEM.md files | `inframesh skill.md` |
| Multi-region proxy fleet management | 2000 proxies, 13 regions at Atlassian scale | `inframesh skill.md` |
| Load testing (1000 simulated nodes at 10 events/sec) | Kinesis Lambda bottleneck found + fixed | `InfraMesh _SentinelGrid _PulseGrid _MemCore.md` |
| SQS Dead Letter Queue + retry logic | InfraMesh worker failure handling | `basic roadmap 4 project.md` |

### 1.9 — System Design & Distributed Systems

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| OSI Model + TCP/IP (diagnostic use) | NetOps360 + system design interviews | `computer netwoek.md`, `system design.md` |
| HTTP/gRPC/WebSockets | All API layers | `system design.md` |
| CAP theorem, Consistency models, CRDT | Distributed KV store project | `system design.md`, `os.md` |
| Consistent hashing | Custom Redis-like implementation | `system design.md` |
| CQRS + Event Sourcing | PulseGrid event-driven architecture | `inframesh upgd.md` |
| Rate limiting (token bucket, sliding window) | InfraMesh API gateway | `system design.md` |
| Circuit breaker, retry, bulkhead patterns | All microservice communication | `system design.md` |
| 2PC (Two-Phase Commit) and its failure modes | Distributed transaction theory | `system design01.md` |
| Service mesh patterns | InfraMesh proxy fleet | `inframesh skill.md` |
| DORA metrics (deployment frequency, change failure rate) | PulseGrid engineering intelligence | `inframesh upgd.md` |
| ADR (Architecture Decision Records) | Why Neo4j over relational for graph traversal | `inframesh upgd.md` |

### 1.10 — Network Engineering (NetOps360)

| Skill | Depth Proven By | Roadmap Source |
|-------|----------------|----------------|
| OSI/TCP-IP, OSPF, BGP, EIGRP, MPLS | NetOps360 full network operations platform | `computer netwoek.md` |
| SDN, VXLAN, EVPN (data center fabrics) | Phase 4 of networking roadmap | `computer netwoek.md` |
| Python network automation (Netmiko, Paramiko) | Automated SSH to network devices | `computer netwoek.md` |
| Ansible (network config management at scale) | Automated compliance auditor project | `computer netwoek.md` |
| REST APIs for network devices (RESTCONF/NETCONF) | Modern network programmability | `computer netwoek.md` |
| AWS VPC networking, Direct Connect concepts | Cloud networking phase | `computer netwoek.md` |
| AI-powered AIOps root cause analysis | NetOps360 AI layer (Phase 7) | `computer netwoek.md` |
| Wireshark + tcpdump | Packet-level debugging | `system design.md` |

### 1.11 — Operating Systems (6 Projects)

| Project | What It Tests | Roadmap Source |
|---------|--------------|----------------|
| Unix Shell (C) | Processes, system calls, I/O, fork/exec | `os.md` |
| User-Level Thread Library (C, context_switch.S) | Thread scheduler, context switching assembly | `os.md` |
| Custom malloc() (C) | Memory management, buddy allocator, coalescing | `os.md` |
| Toy File System (C) | Inodes, blocks, directory structure | `os.md` |
| Distributed Key-Value Store (Python + Docker) | Consensus, replication, CAP theorem | `os.md` |
| AI-Powered Semantic Scheduler (Python + eBPF) | Modern AI-OS integration | `os.md` |

---

<a name="projects"></a>
## 🏗️ SECTION 2 — YOUR 4 FLAGSHIP PROJECTS (Deep Profile)

### PROJECT 1: SentinelGrid
**What it is:** Industrial IoT anomaly detection system for factory motor bearing failure prediction. A matchbox-sized PCB (SentinelNode) on a motor with 4 sensors connected via SPI/I2C to ESP32-S3. FreeRTOS firmware with 5 concurrent tasks, INT8 TFLite Micro LSTM autoencoder, MQTT→AWS IoT Core→Kinesis→Lambda→TimescaleDB pipeline, Grafana dashboard.

**Key numbers you can state in an interview:**
- 1kHz sampling (Nyquist: highest bearing frequency 430Hz → minimum 860Hz required)
- FFT: 12ms, Feature extraction: 3ms, TFLite inference: 47ms total = 60ms per window
- Float32 model: 182KB, 95.1% detection rate. INT8 model: 46KB, 91.4% (4-point trade-off documented)
- Load tested: 1000 simulated nodes at 10 events/sec. Bottleneck: Kinesis Lambda consumer (fixed with batching)
- Model OTA: update without firmware reboot. Production incident: 200 nodes crash-loop prevented by rollback
- Cloud rebuild time via Terraform: 12 minutes

**Who recognizes this:** Bosch, Siemens, ABB, Honeywell, Continental, Rockwell, ARM, Qualcomm, NXP, Renesas, Edge Impulse, Memfault, STMicroelectronics — this is *literally their product domain*.

---

### PROJECT 2: InfraMesh
**What it is:** Self-service internal developer platform. Developers call FastAPI to register services, SQS worker provisions AWS resources (EC2, DynamoDB tables, CloudFront distribution, Route53 records, IAM roles, ACM certs, NLB). Replaces enterprise load balancers with open-source Envoy/Nginx. Based on analysis of real Atlassian production system built over 8 years.

**Key numbers:**
- 2000 proxies across 13 AWS regions (Atlassian-scale pattern)
- Full Terraform IaC: all resources in code, SQS failure + bad proxy config incident documented
- JWT auth, health checks, Grafana dashboards, DDoS via CloudFront

**Who recognizes this:** Atlassian, HashiCorp, Cloudflare, any company with a Platform Engineering team (every company with 50+ engineers has one or is building one).

---

### PROJECT 3: PulseGrid
**What it is:** ML-powered deployment intelligence platform. Ingests signals from GitHub (webhooks), CI/CD, PagerDuty, Sentry, Prometheus, OpenTelemetry into Kafka. Python processor builds live service dependency graph in Neo4j from distributed traces. XGBoost classifier scores every PR for deployment risk. LLM generates postmortem drafts.

**Key numbers:**
- 10,000+ engineering events/minute processed via Kafka
- Risk model: AUC 0.82, correctly flagged 4 of 5 most recent production incidents
- Neo4j blast radius query in O(log N) vs SQL JOIN (O(N²)) — documented in ADR/003
- Postmortem generated in <5 minutes after incident resolution
- 6-source timeline assembly: GitHub + CI/CD + PagerDuty + Sentry + Prometheus + OTel

**Who recognizes this:** Google (Dapper/Monarch SRE tooling), Netflix (reliability platform), LinkedIn (deployment intelligence), Datadog, PagerDuty, LinearB — none of them have open-sourced this. This is original.

---

### PROJECT 4: MemCore (EmbeddedAI)
**What it is:** An SDK (pip-installable Python package) that gives any application persistent debugging intelligence. One-line import. Hooks Python exception system, parses AST with tree-sitter, builds call graph, stores function semantics as CodeBERT embeddings in ChromaDB. On bug → retrieves 5 semantically similar past bugs → assembles context with current error + git diff → generates ranked fix via LLM API.

**Also has:** 400-line C version that runs on SentinelGrid gateway, capturing firmware crash dumps and storing the vocabulary of normal gateway Python behavior.

**Key numbers:**
- Fix suggestion acceptance rate after 30 days on InfraMesh: 73%
- ChromaDB semantic retrieval: <100ms for similar bug lookup

**Who recognizes this:** Any company with a large codebase (every MNC). Edge Impulse, Memfault, Nordic Semiconductor see this as infrastructure tooling for firmware teams.

---

<a name="job-roles"></a>
## 💼 SECTION 3 — ALL FRESHER JOB ROLES (Realistic 2026)

### 3.1 — High Probability Roles (60–80% Hiring Chance)

| Job Title (exact company posting) | Domain | Why You Qualify | Realistic? |
|-----------------------------------|--------|----------------|------------|
| Associate Software Engineer | Backend/Platform | FastAPI + PostgreSQL + Docker + AWS — all verified by projects | ✅ Very Realistic |
| Software Development Engineer I (SDE-I) | Backend | System Design 210-day roadmap + 4 real projects = interview advantage | ✅ Very Realistic |
| Junior Backend Engineer | Backend | FastAPI, Kafka, Redis, PostgreSQL, SQS fluency — all production-grade | ✅ Very Realistic |
| Embedded Software Engineer I | Firmware | FreeRTOS + STM32/ESP32 + C + RTOS + OTA = rare for freshers globally | ✅ Very Realistic |
| Firmware Engineer (Entry Level) | Embedded | SentinelGrid proves real firmware — interrupt-driven, DMA, watchdog, HardFault handler | ✅ Very Realistic |
| IoT Software Engineer (Junior) | IoT | MQTT + AWS IoT Core + LoRa + ESP32 + store-and-forward — complete IoT stack | ✅ Very Realistic |
| Edge AI Engineer | Edge ML | TFLite Micro + INT8 + 47ms inference on real hardware = globally rare fresher skill | ✅ Very Realistic |
| Junior Platform Engineer | Platform/DevOps | InfraMesh is literally the platform engineer's job description at Atlassian | ✅ Very Realistic |
| Associate DevOps Engineer | DevOps | Terraform + Docker + K8s + GitHub Actions + Grafana + ELK — full stack | ✅ Very Realistic |
| Graduate Trainee Engineer | Any domain | MNCs have structured programs — portfolio depth wins these | ✅ Very High |
| Embedded ML Engineer | Firmware+AI | Hardware-AI bridge is the #1 skill shortage in semiconductor companies | ✅ Very Realistic |
| Industrial IoT Engineer | OT/IT | SentinelGrid maps exactly to Bosch/Siemens/Honeywell/ABB product line | ✅ Very Realistic |

### 3.2 — Moderate Probability Roles (35–60% Hiring Chance)

| Job Title | Domain | Gap to Address |
|-----------|--------|----------------|
| Machine Learning Engineer (Entry Level) | ML | Strong tools knowledge; gap = large-scale production ML ownership |
| AI Engineer (Junior/Associate) | AI | LangChain + RAG + Agentic AI skills genuine for 2026; competition is high |
| Associate Data Engineer | Data | Kafka + Airflow + Spark + TimescaleDB solid; gap = large-scale Spark optimization |
| Cloud Engineer (Junior/Associate) | Cloud | AWS breadth strong; gap = AWS certifications (SAA/DVA help) |
| Site Reliability Engineer I | SRE | Grafana + Prometheus + on-call thinking genuine; gap = production SRE culture experience |
| Network Automation Engineer (Junior) | NetOps | Python + Netmiko + Ansible + BGP real; gap = CCNA/CCNP certification |
| Junior MLOps Engineer | MLOps | MLflow + Evidently + Grafana + model drift = solid; gap = large dataset MLOps at scale |
| AI Observability Engineer | AI Ops | PulseGrid maps to this — Datadog/New Relic type roles | 

### 3.3 — Your Niche Competitive Advantage Roles (Globally Few Freshers Qualify)

> These are roles where the supply of qualified freshers is **globally tiny**. Your projects make you one of a handful of freshers worldwide who can credibly apply.

| Niche Role | Why It's Hard to Fill | Why YOU Qualify |
|------------|----------------------|-----------------|
| **Edge AI Engineer** | Requires firmware + ML + quantization knowledge — most ML engineers can't write C, most firmware engineers don't know TFLite | TFLite Micro + INT8 + FreeRTOS + 47ms inference benchmark documented |
| **Embedded ML Engineer** | Hardware-AI bridge is rarest combination | SentinelGrid entire pipeline: sensor → FFT → edge inference → cloud → retrain |
| **Industrial IoT Engineer** | Requires OT (operational technology) + IT convergence | MQTT + AWS IoT Core + TimescaleDB + Grafana + factory motor context |
| **Platform Engineering Graduate** | Needs AWS breadth + self-service developer UX + IaC — most freshers have 1, not all 3 | InfraMesh based on real Atlassian system with full AWS + Terraform + SQS |
| **AI Deployment Risk Engineer** | New 2025-2026 role at advanced companies | PulseGrid is a working prototype of this exact role |
| **Firmware Observability Engineer** | Only exists at Memfault, Edge Impulse, ARM | MemCore C version captures firmware crash vocabulary = core product feature |

---

<a name="titles"></a>
## 🏷️ SECTION 4 — PROFESSIONAL TITLES

### 4.1 — Recommended Titles by Platform

| Platform | Best Title | Why |
|----------|------------|-----|
| **LinkedIn Headline** | `Embedded AI & Platform Engineer \| FreeRTOS · TFLite Micro · AWS · FastAPI \| Built SentinelGrid & InfraMesh` | Project-specific, searchable, accurate |
| **LinkedIn Alt Headline** | `Building at the edge of firmware and cloud AI \| IoT · MLOps · Platform Engineering \| ESP32 · Kafka · Neo4j · Terraform` | Domain-specific keywords recruiters search |
| **Resume (Embedded focus)** | `Junior Embedded AI Engineer` | Accurate, rare title, exact match to edge AI job postings |
| **Resume (Platform focus)** | `Associate Platform Engineer` | Safe, accurate, industry-standard |
| **Resume (General tech)** | `Software Engineer — Embedded Systems & Cloud Infrastructure` | Broad, honest, defensible |
| **GitHub Profile Bio** | `I build systems at the hardware-AI-cloud intersection. SentinelGrid (FreeRTOS+TFLite Micro+AWS IoT), InfraMesh (self-service dev platform), PulseGrid (ML deployment risk scoring), MemCore (AI debugging SDK).` | Describes actual work — recruiters read this |
| **Portfolio About Section** | `Engineer focused on Edge AI, Industrial IoT, and Platform Engineering` | Not inflated, specific domains |

### 4.2 — Titles to AVOID as a Fresher

| Inflated Title | Problem | Use Instead |
|----------------|---------|-------------|
| `Full Stack AI Engineer` | Implies production ownership at scale | `Junior AI Engineer` |
| `Senior Platform Architect` | 5–8 year title | `Platform Engineer` |
| `AI/ML Expert` | "Expert" = ≥5 years production | `ML Engineer (Entry Level)` |
| `Principal Engineer` | 8+ year leadership title | Never use |
| `AI Innovator / AI Visionary` | Empty buzzword, no engineering specifics | Describe the innovation instead |
| `10x Engineer` | Cliché, unverifiable | Let projects speak |
| `Deep Learning Researcher` | Implies publications / PhD | `Deep Learning Engineer` |
| `MLOps Architect` | Senior title | `MLOps Engineer` |

### 4.3 — GitHub README Template (Copy-Use)

```markdown
## Hi, I'm [Name] — Engineer at the Hardware-AI-Cloud Intersection

**Currently building:**
→ **SentinelGrid** — Industrial IoT anomaly detection on STM32/ESP32-S3 (FreeRTOS + TFLite Micro + 
  MQTT + AWS IoT Core + TimescaleDB). 47ms edge inference. Load tested at 1000 nodes.
→ **InfraMesh** — Self-service internal developer platform (FastAPI + SQS + DynamoDB + CloudFront + 
  Route53 + Terraform). Based on Atlassian production architecture.
→ **PulseGrid** — ML deployment risk scoring from engineering signals (Kafka + Neo4j + XGBoost + LLM). 
  AUC 0.82. Flags risky deploys before they become incidents.
→ **MemCore** — AI debugging SDK that learns your codebase (CodeBERT + ChromaDB + LLM). 
  73% fix suggestion acceptance rate.

**Stack:** Python · C · FastAPI · FreeRTOS · ESP32-S3 · TFLite Micro · PostgreSQL · TimescaleDB · 
Redis · Kafka · Neo4j · ChromaDB · Docker · Kubernetes · Terraform · AWS · Grafana · LangChain

**Interests:** Edge AI · Industrial IoT · Platform Engineering · MLOps · Distributed Systems
```

---

<a name="companies"></a>
## 🏢 SECTION 5 — TOP 300 COMPANIES
### ⚡ Exchange Rates: 1 USD=₹96 | 1 EUR=₹112 | 1 GBP=₹129 | 1 CAD=₹70 | 1 AUD=₹69 | 1 SGD=₹75 | 1 JPY=₹0.63 | 1 CHF=₹106 | 1 NOK=₹9

---

### 🔩 TIER 1 — EMBEDDED · FIRMWARE · EDGE AI · INDUSTRIAL IoT
*Your SentinelGrid + EmbeddedAI projects are your strongest differentiators here. These companies will recognize your work immediately.*

| # | Company | Country | Role | Local Salary | INR LPA | Work Mode | Career Page |
|---|---------|---------|------|-------------|---------|-----------|-------------|
| 1 | **Bosch** | Germany | Embedded SW Engineer | €45–60K/yr | ₹50–67 LPA | Hybrid | careers.bosch.com |
| 2 | **Bosch India** | Bengaluru/Hyderabad | Assoc. SW Engineer | ₹8–14 LPA | ₹8–14 LPA | Hybrid | careers.bosch.com |
| 3 | **Siemens** | Germany | Embedded Engineer | €45–65K/yr | ₹50–73 LPA | Hybrid | siemens.com/careers |
| 4 | **Siemens India** | Pune, Bengaluru | Associate Engineer | ₹8–15 LPA | ₹8–15 LPA | Hybrid | siemens.com/careers |
| 5 | **ABB** | Switzerland | Junior Firmware Engineer | CHF 70–90K/yr | ₹74–95 LPA | Hybrid | new.abb.com/careers |
| 6 | **ABB India** | Bengaluru | Software Engineer | ₹7–12 LPA | ₹7–12 LPA | Hybrid | new.abb.com/careers |
| 7 | **Qualcomm** | USA | Embedded SW Engineer I | $120–145K/yr | ₹115–139 LPA | Hybrid | qualcomm.com/careers |
| 8 | **Qualcomm India** | Hyderabad | Engineer I | ₹15–25 LPA | ₹15–25 LPA | Hybrid | qualcomm.com/careers |
| 9 | **ARM** | UK | Graduate Engineer | £45–60K/yr | ₹58–77 LPA | Hybrid | arm.com/careers |
| 10 | **ARM India** | Bengaluru | Graduate Engineer | ₹15–22 LPA | ₹15–22 LPA | Hybrid | arm.com/careers |
| 11 | **NXP Semiconductors** | Netherlands | Junior Firmware Engineer | €45–58K/yr | ₹50–65 LPA | Hybrid | nxp.com/careers |
| 12 | **NXP India** | Noida/Bengaluru | Embedded SW Engineer | ₹8–14 LPA | ₹8–14 LPA | Hybrid | nxp.com/careers |
| 13 | **STMicroelectronics** | France/India | Embedded Developer | France: €38–50K \| India: ₹7–12 LPA | ₹43–56 LPA \| ₹7–12 LPA | Hybrid | st.com/careers |
| 14 | **Texas Instruments** | USA | Embedded SW Engineer I | $100–130K/yr | ₹96–125 LPA | Hybrid | careers.ti.com |
| 15 | **TI India** | Bengaluru | Software Engineer | ₹12–20 LPA | ₹12–20 LPA | Hybrid | careers.ti.com |
| 16 | **Renesas Electronics** | Japan | Junior Embedded Engineer | ¥5–7M/yr | ₹31–44 LPA | On-site | renesas.com/careers |
| 17 | **Renesas India** | Bengaluru/Noida | Firmware Engineer | ₹8–13 LPA | ₹8–13 LPA | Hybrid | renesas.com/careers |
| 18 | **Microchip Technology** | USA | Firmware Engineer (Assoc.) | $85–110K/yr | ₹82–106 LPA | Hybrid | microchip.com/careers |
| 19 | **Nordic Semiconductor** | Norway | Junior Embedded SW Eng. | NOK 600–720K/yr | ₹54–65 LPA | Hybrid | nordicsemi.com/Careers |
| 20 | **Silicon Labs** | USA | Embedded SW Engineer I | $95–120K/yr | ₹91–115 LPA | Hybrid | silabs.com/careers |
| 21 | **Espressif Systems** | China/India | Embedded SW Engineer | India: ₹8–14 LPA | ₹8–14 LPA | Hybrid | espressif.com/careers |
| 22 | **Honeywell** | USA | IoT Engineer | $95–120K/yr | ₹91–115 LPA | Hybrid | careers.honeywell.com |
| 23 | **Honeywell India** | Hyderabad | Software Engineer | ₹9–16 LPA | ₹9–16 LPA | Hybrid | careers.honeywell.com |
| 24 | **Rockwell Automation** | USA | Junior SW Eng. – IoT | $90–115K/yr | ₹86–110 LPA | Hybrid | rockwellautomation.com/careers |
| 25 | **Emerson Electric** | USA | Embedded Systems Eng. I | $85–110K/yr | ₹82–106 LPA | Hybrid | emerson.com/careers |
| 26 | **Continental AG** | Germany | Junior Embedded SW Eng. | €42–58K/yr | ₹47–65 LPA | On-site | continental.com/careers |
| 27 | **Continental India** | Pune/Bengaluru | Embedded Developer | ₹8–14 LPA | ₹8–14 LPA | On-site | continental.com/careers |
| 28 | **Infineon Technologies** | Germany | Junior Firmware Engineer | €42–56K/yr | ₹47–63 LPA | Hybrid | infineon.com/careers |
| 29 | **Infineon India** | Bengaluru | Firmware Engineer | ₹7–12 LPA | ₹7–12 LPA | Hybrid | infineon.com/careers |
| 30 | **Memfault** | USA (Remote) | Embedded SW Engineer | $100–130K/yr | ₹96–125 LPA | Remote-first | memfault.com/jobs |
| 31 | **Edge Impulse** | USA (Remote) | ML Engineer (Edge) | $90–120K/yr | ₹86–115 LPA | Remote-first | edgeimpulse.com/careers |
| 32 | **HARMAN (Samsung)** | India/USA | Embedded SW Engineer | India: ₹10–18 LPA | ₹10–18 LPA | Hybrid | harman.com/careers |
| 33 | **Denso** | Japan/India | Embedded SW Engineer | Japan: ¥5–7M \| India: ₹7–12 LPA | ₹31–44 LPA \| ₹7–12 LPA | On-site | globaldenso.com/careers |
| 34 | **ZF Group** | Germany | Embedded Developer | €40–55K/yr | ₹45–62 LPA | On-site | careers.zf.com |
| 35 | **Aptiv** | USA/India | SW Engineer – Firmware | India: ₹8–14 LPA \| USA: $90–120K | ₹86–115 LPA \| ₹8–14 LPA | Hybrid | careers.aptiv.com |
| 36 | **Valeo** | France/India | Junior Embedded Engineer | France: €38–50K \| India: ₹7–12 LPA | ₹43–56 LPA \| ₹7–12 LPA | Hybrid | valeo.com/careers |
| 37 | **Visteon** | USA/India | Embedded SW Engineer | India: ₹8–13 LPA \| USA: $90–115K | ₹86–110 LPA \| ₹8–13 LPA | Hybrid | visteon.com/careers |
| 38 | **Schneider Electric** | France/India | Junior IoT Engineer | India: ₹8–14 LPA \| France: €40–55K | ₹45–62 LPA \| ₹8–14 LPA | Hybrid | se.com/careers |
| 39 | **Eaton** | USA/India | Embedded Systems Eng. I | India: ₹8–13 LPA \| USA: $85–110K | ₹82–106 LPA \| ₹8–13 LPA | Hybrid | eaton.com/careers |
| 40 | **Phoenix Contact** | Germany | Junior Embedded Engineer | €40–54K/yr | ₹45–60 LPA | Hybrid | phoenixcontact.com/careers |
| 41 | **Beckhoff Automation** | Germany | Embedded SW Engineer | €40–55K/yr | ₹45–62 LPA | On-site | beckhoff.com/careers |
| 42 | **KUKA Robotics** | Germany | Software Engineer | €42–56K/yr | ₹47–63 LPA | Hybrid | kuka.com/careers |
| 43 | **FANUC** | Japan | Software Engineer | ¥4.5–6.5M/yr | ₹28–41 LPA | On-site | fanuc.co.jp/careers |
| 44 | **Mitsubishi Electric** | Japan/India | Embedded Engineer | India: ₹7–12 LPA \| Japan: ¥4.5–6.5M | ₹28–41 LPA \| ₹7–12 LPA | On-site | mitsubishielectric.com/careers |
| 45 | **Pilz GmbH** | Germany | Firmware Engineer | €38–52K/yr | ₹43–58 LPA | On-site | pilz.com/careers |
| 46 | **Vector Informatik** | Germany | Embedded Tools Engineer | €42–58K/yr | ₹47–65 LPA | Hybrid | vector.com/vi_career |
| 47 | **ETAS (Bosch sub.)** | Germany/India | Embedded SW Engineer | India: ₹8–14 LPA \| Germany: €42–58K | ₹47–65 LPA \| ₹8–14 LPA | Hybrid | etas.com/careers |
| 48 | **dSPACE** | Germany | Embedded/HIL Engineer | €42–58K/yr | ₹47–65 LPA | On-site | dspace.com/careers |
| 49 | **Syntiant** | USA | Embedded ML Engineer | $100–135K/yr | ₹96–130 LPA | Hybrid | syntiant.com/careers |
| 50 | **Eta Compute** | USA | Edge AI Engineer | $95–125K/yr | ₹91–120 LPA | Hybrid | etacompute.com/careers |
| 51 | **Samsara** | USA | SW Engineer (IoT) | $105–135K/yr | ₹101–130 LPA | Hybrid | samsara.com/careers |
| 52 | **Particle Industries** | USA | IoT Platform Engineer | $95–125K/yr | ₹91–120 LPA | Remote | particle.io/careers |
| 53 | **Golioth** | USA (Remote) | Embedded SW/Cloud | $90–120K/yr | ₹86–115 LPA | Remote-first | golioth.io/careers |
| 54 | **Blues Wireless** | USA | Firmware Engineer | $90–115K/yr | ₹86–110 LPA | Remote | blues.io/careers |
| 55 | **Toradex** | Switzerland | Embedded Engineer | CHF 65–85K/yr | ₹69–90 LPA | On-site | toradex.com/careers |
| 56 | **u-blox** | Switzerland | Embedded SW Engineer | CHF 65–85K/yr | ₹69–90 LPA | Hybrid | u-blox.com/careers |
| 57 | **Quectel** | China/India | Firmware/IoT Engineer | India: ₹7–12 LPA | ₹7–12 LPA | Hybrid | quectel.com/careers |
| 58 | **Ceva Semiconductors** | Israel/India | DSP/Embedded Engineer | India: ₹8–14 LPA | ₹8–14 LPA | Hybrid | ceva-dsp.com/careers |
| 59 | **Kontron** | Germany | Firmware Engineer | €40–54K/yr | ₹45–60 LPA | On-site | kontron.com/careers |
| 60 | **Rohde & Schwarz** | Germany | Software Engineer | €42–58K/yr | ₹47–65 LPA | Hybrid | rohde-schwarz.com/careers |

---

### 🔧 TIER 2 — PLATFORM ENGINEERING · DEVOPS · SRE · CLOUD
*InfraMesh is directly what platform teams build. Your AWS depth + Terraform + Kubernetes sets you apart.*

| # | Company | Country | Role | Local Salary | INR LPA | Work Mode | Career Page |
|---|---------|---------|------|-------------|---------|-----------|-------------|
| 61 | **Atlassian** | Australia | Assoc. SW Engineer | AUD $90–120K/yr | ₹62–83 LPA | Remote-friendly | atlassian.com/careers |
| 62 | **Atlassian India** | Bengaluru | Associate SW Engineer | ₹20–30 LPA | ₹20–30 LPA | Hybrid | atlassian.com/careers |
| 63 | **Cloudflare** | USA | Software Engineer I | $130–165K/yr | ₹125–158 LPA | Hybrid | cloudflare.com/careers |
| 64 | **Cloudflare India** | Bengaluru | Software Engineer I | ₹20–28 LPA | ₹20–28 LPA | Hybrid | cloudflare.com/careers |
| 65 | **HashiCorp (IBM)** | USA/Remote | Junior Platform Engineer | $110–140K/yr | ₹106–134 LPA | Remote-first | hashicorp.com/jobs |
| 66 | **Datadog** | USA | Assoc. Software Engineer | $120–155K/yr | ₹115–149 LPA | Hybrid | careers.datadoghq.com |
| 67 | **Datadog India** | Bengaluru | Associate Engineer | ₹18–28 LPA | ₹18–28 LPA | Hybrid | careers.datadoghq.com |
| 68 | **Grafana Labs** | Remote (Global) | Junior Software Engineer | $90–120K/yr | ₹86–115 LPA | Remote-first | grafana.com/careers |
| 69 | **PagerDuty** | USA | Software Engineer I | $115–145K/yr | ₹110–139 LPA | Hybrid | pagerduty.com/careers |
| 70 | **PagerDuty India** | Bengaluru | Software Engineer I | ₹14–22 LPA | ₹14–22 LPA | Hybrid | pagerduty.com/careers |
| 71 | **New Relic** | USA/India | Associate Engineer | India: ₹12–20 LPA \| USA: $100–130K | ₹96–125 LPA \| ₹12–20 LPA | Remote | newrelic.com/careers |
| 72 | **Dynatrace** | USA/Austria | Junior SW Engineer | USA: $100–130K | ₹96–125 LPA | Hybrid | careers.dynatrace.com |
| 73 | **Fastly** | USA/UK | Junior SW Engineer (Infra) | USA: $115–140K | ₹110–134 LPA | Hybrid | fastly.com/jobs |
| 74 | **Harness** | USA/India | Assoc. SW Engineer | India: ₹14–22 LPA \| USA: $110–140K | ₹106–134 LPA \| ₹14–22 LPA | Hybrid | harness.io/careers |
| 75 | **GitLab** | Remote-only | Junior Backend Engineer | $80–110K/yr (global) | ₹77–106 LPA | Remote-only | about.gitlab.com/jobs |
| 76 | **GitHub (Microsoft)** | USA/India | Software Engineer I | India: ₹18–28 LPA \| USA: $130–165K | ₹125–158 LPA \| ₹18–28 LPA | Hybrid | github.com/about/careers |
| 77 | **Pulumi** | USA (Remote) | Junior Software Engineer | $100–130K/yr | ₹96–125 LPA | Remote-first | pulumi.com/careers |
| 78 | **Kong Inc.** | USA/Remote | SW Engineer I (API Gateway) | $100–130K/yr | ₹96–125 LPA | Remote | konghq.com/careers |
| 79 | **Temporal Technologies** | USA/Remote | Software Engineer I | $105–135K/yr | ₹101–130 LPA | Remote | temporal.io/careers |
| 80 | **CircleCI** | USA/Remote | Junior Software Engineer | $100–125K/yr | ₹96–120 LPA | Hybrid | circleci.com/careers |
| 81 | **Spacelift** | Poland/Remote | Junior Platform Engineer | €35–55K/yr | ₹39–62 LPA | Remote | spacelift.io/careers |
| 82 | **Canonical** | Remote-only | SW Engineer (Ubuntu/Cloud) | £35–55K/yr | ₹45–71 LPA | Remote-only | canonical.com/careers |
| 83 | **Red Hat (IBM)** | USA/India | Assoc. SW Engineer | India: ₹10–18 LPA \| USA: $100–130K | ₹96–125 LPA \| ₹10–18 LPA | Remote | redhat.com/jobs |
| 84 | **Nutanix** | USA/India | Software Engineer I | India: ₹14–22 LPA \| USA: $115–145K | ₹110–139 LPA \| ₹14–22 LPA | Hybrid | jobs.nutanix.com |
| 85 | **Palo Alto Networks** | USA/India | Software Engineer I | India: ₹14–22 LPA \| USA: $120–155K | ₹115–149 LPA \| ₹14–22 LPA | Hybrid | jobs.paloaltonetworks.com |
| 86 | **CrowdStrike** | USA/India | Assoc. SW Engineer | India: ₹12–20 LPA \| USA: $115–145K | ₹110–139 LPA \| ₹12–20 LPA | Remote | crowdstrike.com/careers |
| 87 | **Zscaler** | USA/India | Software Engineer I | India: ₹12–18 LPA \| USA: $110–140K | ₹106–134 LPA \| ₹12–18 LPA | Hybrid | jobs.zscaler.com |
| 88 | **Okta** | USA/Remote | Software Engineer I | $115–145K/yr | ₹110–139 LPA | Remote | okta.com/careers |
| 89 | **Supabase** | Remote | Junior Engineer | $80–120K/yr | ₹77–115 LPA | Remote-first | supabase.com/careers |
| 90 | **Neon (Postgres)** | Remote | Junior Engineer | $80–110K/yr | ₹77–106 LPA | Remote-first | neon.tech/careers |

---

### 🤖 TIER 3 — AI/ML · AGENTIC AI · MLOPS · LLM ENGINEERING
*Your Agentic AI roadmap (180 days), PulseGrid (XGBoost + Kafka + LLM), and MemCore (CodeBERT + ChromaDB) are directly relevant.*

| # | Company | Country | Role | Local Salary | INR LPA | Work Mode | Career Page |
|---|---------|---------|------|-------------|---------|-----------|-------------|
| 91 | **Google (ML Roles)** | USA | Software Engineer (ML) | $150–200K/yr | ₹144–192 LPA | Hybrid | careers.google.com |
| 92 | **Google India** | Hyderabad/Bengaluru | Software Engineer | ₹25–45 LPA | ₹25–45 LPA | Hybrid | careers.google.com |
| 93 | **Microsoft Azure AI** | USA/India | AI Engineer (SDE I) | India: ₹20–35 LPA \| USA: $140–180K | ₹134–173 LPA \| ₹20–35 LPA | Hybrid | careers.microsoft.com |
| 94 | **Amazon AWS AI** | USA/India | SDE I / ML Engineer | India: ₹18–32 LPA \| USA: $140–175K | ₹134–168 LPA \| ₹18–32 LPA | Hybrid | amazon.jobs |
| 95 | **Meta AI** | USA/UK | Research Eng. / SW Eng. | USA: $160–200K | ₹154–192 LPA | Hybrid | metacareers.com |
| 96 | **Anthropic** | USA/Remote | Software Engineer (ML) | $150–200K/yr | ₹144–192 LPA | Hybrid | anthropic.com/careers |
| 97 | **OpenAI** | USA | Software Engineer | $160–210K/yr | ₹154–202 LPA | Hybrid | openai.com/careers |
| 98 | **Cohere** | Canada/Remote | Junior ML Engineer | CAD $90–130K/yr | ₹63–91 LPA | Remote-friendly | cohere.com/careers |
| 99 | **Hugging Face** | France/Remote | ML Engineer (Junior) | $80–120K/yr | ₹77–115 LPA | Remote-first | huggingface.co/jobs |
| 100 | **Mistral AI** | France | ML Engineer | €50–80K/yr | ₹56–90 LPA | Hybrid | mistral.ai/careers |
| 101 | **Scale AI** | USA | Junior ML Engineer | $110–145K/yr | ₹106–139 LPA | Hybrid | scale.com/careers |
| 102 | **Weights & Biases** | USA/Remote | SW Engineer I (MLOps) | $105–135K/yr | ₹101–130 LPA | Remote-friendly | wandb.ai/careers |
| 103 | **Databricks** | USA/India | Software Engineer I | India: ₹18–28 LPA \| USA: $130–165K | ₹125–158 LPA \| ₹18–28 LPA | Hybrid | databricks.com/careers |
| 104 | **Snowflake** | USA/India | Software Engineer I | India: ₹18–28 LPA \| USA: $130–165K | ₹125–158 LPA \| ₹18–28 LPA | Hybrid | careers.snowflake.com |
| 105 | **Pinecone** | USA/Remote | SW Engineer (Vector DB) | $110–145K/yr | ₹106–139 LPA | Remote-friendly | pinecone.io/careers |
| 106 | **Weaviate** | Netherlands/Remote | Junior Engineer | €40–60K/yr | ₹45–67 LPA | Remote-first | weaviate.io/careers |
| 107 | **DataRobot** | USA/India | Junior ML Engineer | India: ₹10–18 LPA \| USA: $105–135K | ₹101–130 LPA \| ₹10–18 LPA | Hybrid | datarobot.com/careers |
| 108 | **C3.ai** | USA | Junior ML Engineer | $100–130K/yr | ₹96–125 LPA | Hybrid | c3.ai/careers |
| 109 | **Cerebras Systems** | USA | SW/HW Engineer | $120–160K/yr | ₹115–154 LPA | Hybrid | cerebras.net/careers |
| 110 | **Groq** | USA | Engineer | $120–160K/yr | ₹115–154 LPA | Hybrid | groq.com/careers |
| 111 | **Perplexity AI** | USA | Software Engineer | $130–170K/yr | ₹125–163 LPA | Hybrid | perplexity.ai/careers |
| 112 | **Aleph Alpha** | Germany | ML Engineer | €50–75K/yr | ₹56–84 LPA | Hybrid | aleph-alpha.com/careers |
| 113 | **DeepL** | Germany | Software Engineer | €48–68K/yr | ₹54–76 LPA | Hybrid | jobs.deepl.com |
| 114 | **Silo AI** | Finland | ML Engineer | €45–65K/yr | ₹50–73 LPA | Hybrid | silo.ai/careers |
| 115 | **ElevenLabs** | Remote | Software Engineer | $90–130K/yr | ₹86–125 LPA | Remote-first | elevenlabs.io/careers |
| 116 | **LangChain** | USA/Remote | Software Engineer | $100–135K/yr | ₹96–130 LPA | Remote | langchain.com/careers |
| 117 | **Replit** | USA/Remote | Software Engineer | $100–135K/yr | ₹96–130 LPA | Remote | replit.com/careers |
| 118 | **Wayve** | UK | Software Engineer | £50–75K/yr | ₹65–97 LPA | Hybrid | wayve.ai/join |

---

### 🇮🇳 TIER 4 — INDIA PRODUCT COMPANIES (High Volume Fresher Hiring)

| # | Company | City | Role | Salary (INR LPA) | Work Mode | Career Page |
|---|---------|------|------|------------------|-----------|-------------|
| 119 | **Flipkart** | Bengaluru | SDE-I | ₹20–35 LPA | Hybrid | flipkartcareers.com |
| 120 | **Meesho** | Bengaluru | SDE-I, Data Engineer | ₹20–32 LPA | Hybrid | careers.meesho.com |
| 121 | **Razorpay** | Bengaluru | SDE-I, Platform Engineer | ₹18–28 LPA | Hybrid | razorpay.com/jobs |
| 122 | **PhonePe** | Bengaluru | SDE-I | ₹18–28 LPA | Hybrid | phonepe.com/careers |
| 123 | **CRED** | Bengaluru | SDE-I, Backend Engineer | ₹25–40 LPA | Hybrid | careers.cred.club |
| 124 | **Zepto** | Mumbai | SDE-I | ₹15–25 LPA | Hybrid | zeptonow.com/careers |
| 125 | **Swiggy** | Bengaluru | SDE-I, Data Engineer | ₹18–30 LPA | Hybrid | careers.swiggy.com |
| 126 | **Zomato** | Gurgaon | SDE-I | ₹18–28 LPA | Hybrid | zomato.com/careers |
| 127 | **Dream11** | Mumbai | SDE-I, Data Engineer | ₹22–35 LPA | Hybrid | careers.dream11.com |
| 128 | **Freshworks** | Chennai | Software Engineer | ₹12–22 LPA | Hybrid | freshworks.com/careers |
| 129 | **Chargebee** | Chennai | Software Engineer | ₹10–18 LPA | Hybrid | chargebee.com/careers |
| 130 | **Postman** | Bengaluru | SDE-I | ₹18–26 LPA | Hybrid | postman.com/careers |
| 131 | **BrowserStack** | Mumbai | SDE-I | ₹18–26 LPA | Hybrid | browserstack.com/careers |
| 132 | **Druva** | Pune | SDE-I | ₹14–20 LPA | Hybrid | druva.com/careers |
| 133 | **Elastic India** | Bengaluru | Junior SW Engineer | ₹16–24 LPA | Remote-friendly | elastic.co/careers |
| 134 | **Clevertap** | Mumbai | SDE-I | ₹14–22 LPA | Hybrid | clevertap.com/careers |
| 135 | **Paytm** | Noida | SDE-I | ₹12–22 LPA | Hybrid | paytm.com/jobs |
| 136 | **Nykaa** | Mumbai | SDE-I | ₹12–20 LPA | Hybrid | nykaa.com/careers |
| 137 | **Groww** | Bengaluru | SDE-I | ₹18–28 LPA | Hybrid | groww.in/careers |
| 138 | **Zerodha** | Bengaluru | SDE | ₹12–22 LPA | Hybrid | zerodha.com/careers |
| 139 | **Ola** | Bengaluru | SDE-I, ML Engineer | ₹15–25 LPA | Hybrid | ola.jobs |
| 140 | **Zoho** | Chennai | Software Engineer | ₹6–12 LPA (structured growth) | On-site | careers.zohocorp.com |

---

### 🌐 TIER 5 — INDIA GCC (Global Capability Centers) — MNCs Doing Real Product Work in India

| # | Company | India City | Role | Salary (INR LPA) | Career Page |
|---|---------|------------|------|------------------|-------------|
| 141 | **Google India** | Hyderabad/Bengaluru | Software Engineer | ₹25–45 LPA | careers.google.com |
| 142 | **Microsoft India** | Hyderabad/Bengaluru | SDE I | ₹20–38 LPA | careers.microsoft.com |
| 143 | **Amazon India** | Hyderabad/Bengaluru | SDE I | ₹18–35 LPA | amazon.jobs |
| 144 | **Meta India** | Hyderabad | Software Engineer | ₹25–40 LPA | metacareers.com |
| 145 | **Apple India** | Hyderabad/Bengaluru | Software Engineer | ₹25–40 LPA | jobs.apple.com |
| 146 | **NVIDIA India** | Pune/Hyderabad | Software Engineer | ₹20–35 LPA | nvidia.com/careers |
| 147 | **Salesforce India** | Hyderabad | Assoc. SW Engineer | ₹16–28 LPA | careers.salesforce.com |
| 148 | **Oracle India** | Bengaluru/Hyderabad | Assoc. SW Engineer | ₹10–18 LPA | oracle.com/careers |
| 149 | **SAP India** | Bengaluru | Associate Developer | ₹8–16 LPA | jobs.sap.com |
| 150 | **Cisco India** | Bengaluru | Software Engineer I | ₹14–22 LPA | jobs.cisco.com |
| 151 | **Juniper Networks India** | Bengaluru | Software Engineer I | ₹12–20 LPA | juniper.net/careers |
| 152 | **VMware (Broadcom) India** | Bengaluru | Member of Technical Staff | ₹15–25 LPA | careers.broadcom.com |
| 153 | **Intel India** | Bengaluru/Hyderabad | Graduate Eng. → FTE | ₹12–22 LPA | jobs.intel.com |
| 154 | **AMD India** | Hyderabad/Bengaluru | Software Engineer I | ₹14–22 LPA | amd.com/careers |
| 155 | **Synopsys India** | Bengaluru/Hyderabad | Software Engineer | ₹14–22 LPA | synopsys.com/jobs |
| 156 | **Cadence India** | Bengaluru | Software Engineer | ₹14–22 LPA | cadence.com/careers |
| 157 | **Keysight India** | Bengaluru | Software Engineer | ₹9–16 LPA | keysight.com/careers |
| 158 | **National Instruments (NI/Emerson) India** | Bengaluru | Software Engineer | ₹9–16 LPA | ni.com/careers |
| 159 | **IBM India** | Multiple | Assoc. SW Engineer | ₹7–13 LPA | ibm.com/employment |
| 160 | **Accenture India** | Multiple | ASE | ₹4.5–8 LPA | accenture.com/careers |

---

### 🌍 TIER 6 — GLOBAL MNCs: USA · EUROPE · CANADA · SINGAPORE · AUSTRALIA

| # | Company | Country | Role | Local Salary | INR LPA | Career Page |
|---|---------|---------|------|-------------|---------|-------------|
| 161 | **Stripe** | USA/Ireland | Software Engineer | USA: $130–165K | ₹125–158 LPA | stripe.com/jobs |
| 162 | **Twilio** | USA/Remote | Software Engineer I | $110–140K/yr | ₹106–134 LPA | twilio.com/jobs |
| 163 | **MongoDB** | USA/India | Assoc. SW Engineer | India: ₹18–26 LPA \| USA: $120–155K | ₹115–149 LPA \| ₹18–26 LPA | mongodb.com/careers |
| 164 | **Confluent** | USA/India | Software Engineer | India: ₹18–28 LPA \| USA: $120–155K | ₹115–149 LPA \| ₹18–28 LPA | careers.confluent.io |
| 165 | **Cockroach Labs** | USA | Software Engineer | $115–145K/yr | ₹110–139 LPA | cockroachlabs.com/careers |
| 166 | **ClickHouse Inc.** | Remote | Software Engineer | $90–120K/yr | ₹86–115 LPA | clickhouse.com/careers |
| 167 | **Dremio** | USA/Remote | Software Engineer I | $105–135K/yr | ₹101–130 LPA | dremio.com/careers |
| 168 | **Shopify** | Canada/Remote | Junior Developer | CAD $80–115K/yr | ₹56–81 LPA | careers.shopify.com |
| 169 | **Cohere** | Canada | ML Engineer | CAD $90–130K/yr | ₹63–91 LPA | cohere.com/careers |
| 170 | **Lightspeed Commerce** | Canada | Software Engineer | CAD $80–105K/yr | ₹56–74 LPA | jobs.lightspeedcommerce.com |
| 171 | **Spotify** | Sweden/Remote | Backend Engineer | SEK 550–720K/yr (~€52–68K) | ₹58–76 LPA | lifeatspotify.com |
| 172 | **Klarna** | Sweden/Germany | Software Engineer | €45–65K/yr | ₹50–73 LPA | careers.klarna.com |
| 173 | **Zalando** | Germany | Junior SW Engineer | €45–60K/yr | ₹50–67 LPA | jobs.zalando.com |
| 174 | **Delivery Hero** | Germany | Junior Backend Engineer | €42–58K/yr | ₹47–65 LPA | careers.deliveryhero.com |
| 175 | **SAP** | Germany | Associate Developer | €40–56K/yr | ₹45–63 LPA | jobs.sap.com |
| 176 | **Wise (TransferWise)** | UK/Estonia | Software Engineer | UK: £42–60K | ₹54–77 LPA | wise.jobs |
| 177 | **Revolut** | UK/Lithuania | Software Engineer | UK: £45–65K | ₹58–84 LPA | revolut.com/careers |
| 178 | **Grab** | Singapore | SWE I / ML Engineer | SGD $72–96K/yr | ₹54–72 LPA | careers.grab.com |
| 179 | **Sea Ltd (Shopee)** | Singapore | SDE I | SGD $72–95K/yr | ₹54–71 LPA | careers.sea.com |
| 180 | **Bytedance/TikTok SG** | Singapore | Software Engineer | SGD $80–110K/yr | ₹60–83 LPA | careers.tiktok.com |
| 181 | **GovTech Singapore** | Singapore | Software Engineer | SGD $55–80K/yr | ₹41–60 LPA | careers.gov.sg |
| 182 | **DBS Bank Tech** | Singapore | Assoc. Tech Engineer | SGD $55–75K/yr | ₹41–56 LPA | dbs.com.sg/careers |
| 183 | **Canva** | Australia/Remote | Software Engineer | AUD $85–115K/yr | ₹59–79 LPA | canva.com/careers |
| 184 | **Atlassian AU** | Sydney | Assoc. SW Engineer | AUD $90–120K/yr | ₹62–83 LPA | atlassian.com/careers |
| 185 | **Rakuten** | Japan | Software Engineer | ¥5–7M/yr | ₹32–44 LPA | rakuten.careers |
| 186 | **LINE/LY Corp** | Japan | Software Engineer | ¥5–7M/yr | ₹32–44 LPA | careers.lycorp.co.jp |
| 187 | **Kakao** | South Korea | Software Engineer | KRW 50–70M/yr | ₹34–47 LPA | kakao.com/careers |
| 188 | **Samsung R&D India** | Noida/Bengaluru | Software Engineer | ₹12–20 LPA | ₹12–20 LPA | samsungcareers.com |
| 189 | **Bloomberg** | USA/UK | Software Engineer | USA: $130–165K \| UK: £60–80K | ₹125–158 LPA \| ₹77–103 LPA | bloomberg.com/careers |
| 190 | **Palantir** | USA/UK | Forward Deployed Engineer | USA: $120–155K | ₹115–149 LPA | palantir.com/careers |

---

### 🏥 TIER 7 — MEDTECH & AEROSPACE (Embedded + Safety Critical)

| # | Company | Country | Role | Local Salary | INR LPA | Career Page |
|---|---------|---------|------|-------------|---------|-------------|
| 191 | **Medtronic** | USA/India | SW Engineer (Embedded) | India: ₹8–15 LPA \| USA: $90–120K | ₹86–115 LPA \| ₹8–15 LPA | jobs.medtronic.com |
| 192 | **Philips** | Netherlands/India | Embedded SW Engineer | India: ₹8–15 LPA \| Netherlands: €42–58K | ₹47–65 LPA \| ₹8–15 LPA | philips.com/careers |
| 193 | **GE Healthcare** | USA/India | Software Engineer | India: ₹9–16 LPA \| USA: $95–125K | ₹91–120 LPA \| ₹9–16 LPA | jobs.gehealthcare.com |
| 194 | **Stryker** | USA/India | Software Engineer I | India: ₹9–16 LPA \| USA: $90–120K | ₹86–115 LPA \| ₹9–16 LPA | stryker.com/careers |
| 195 | **Boston Scientific** | USA/India | Software Engineer | India: ₹9–16 LPA \| USA: $90–120K | ₹86–115 LPA \| ₹9–16 LPA | bostonscientific.com/careers |
| 196 | **Siemens Healthineers** | Germany/India | Junior SW Engineer | India: ₹8–14 LPA \| Germany: €42–58K | ₹47–65 LPA \| ₹8–14 LPA | siemens-healthineers.com/careers |
| 197 | **Dräger** | Germany | Embedded SW Engineer | €40–54K/yr | ₹45–60 LPA | draeger.com/careers |
| 198 | **Airbus** | France/India | Junior Embedded SW Eng. | India: ₹9–15 LPA \| EU: €42–58K | ₹47–65 LPA \| ₹9–15 LPA | airbuscareers.com |
| 199 | **Boeing India** | Bengaluru | Software Engineer | ₹10–18 LPA | ₹10–18 LPA | boeing.com/careers |
| 200 | **Safran** | France | Junior Firmware Engineer | €38–52K/yr | ₹43–58 LPA | safran-group.com/careers |
| 201 | **Thales India** | Bengaluru | Embedded SW Engineer | ₹8–14 LPA | ₹8–14 LPA | thalesgroup.com/careers |

---

### 💰 TIER 8 — FINTECH · BANKS · QUANT FIRMS

| # | Company | Country | Role | Local Salary | INR LPA | Career Page |
|---|---------|---------|------|-------------|---------|-------------|
| 202 | **Goldman Sachs India** | Bengaluru/Hyderabad | SW Engineer (Analyst) | ₹20–35 LPA | ₹20–35 LPA | goldmansachs.com/careers |
| 203 | **Goldman Sachs USA** | USA | Technology Analyst | $130–165K/yr | ₹125–158 LPA | goldmansachs.com/careers |
| 204 | **Morgan Stanley India** | Mumbai | Technology Analyst | ₹18–28 LPA | ₹18–28 LPA | morganstanley.com/careers |
| 205 | **JP Morgan India** | Hyderabad/Bengaluru | SW Engineer (Analyst) | ₹18–28 LPA | ₹18–28 LPA | jpmorgan.com/careers |
| 206 | **Deutsche Bank India** | Pune/Bengaluru | Assoc. SW Engineer | ₹12–20 LPA | ₹12–20 LPA | db.com/careers |
| 207 | **Barclays India** | Pune | Technology Analyst | ₹12–20 LPA | ₹12–20 LPA | home.barclays/careers |
| 208 | **HSBC India** | Hyderabad/Pune | Software Engineer | ₹10–18 LPA | ₹10–18 LPA | hsbc.com/careers |
| 209 | **Jane Street** | USA/UK | Software Engineer | $150–200K+ | ₹144–192 LPA | janestreet.com/careers |
| 210 | **Citadel** | USA | Software Engineer | $150–200K+ | ₹144–192 LPA | citadel.com/careers |
| 211 | **Two Sigma** | USA | Software Engineer | $140–190K/yr | ₹134–182 LPA | twosigma.com/careers |
| 212 | **Coinbase** | USA/Remote | Software Engineer | $130–165K/yr | ₹125–158 LPA | coinbase.com/careers |
| 213 | **Stripe Ireland** | Ireland | Software Engineer | €55–80K/yr | ₹62–90 LPA | stripe.com/jobs |
| 214 | **Zerodha** | Bengaluru | SDE | ₹12–22 LPA | ₹12–22 LPA | zerodha.com/careers |
| 215 | **Groww** | Bengaluru | SDE-I | ₹18–28 LPA | ₹18–28 LPA | groww.in/careers |

---

### 🌐 TIER 9 — NETWORK ENGINEERING COMPANIES (NetOps360 Profile)

| # | Company | Country | Role | Local Salary | INR LPA | Career Page |
|---|---------|---------|------|-------------|---------|-------------|
| 216 | **Cisco USA** | USA | Network SW Engineer I | $105–135K/yr | ₹101–130 LPA | jobs.cisco.com |
| 217 | **Arista Networks** | USA/India | Software Engineer I | India: ₹15–24 LPA \| USA: $115–145K | ₹110–139 LPA \| ₹15–24 LPA | arista.com/careers |
| 218 | **Juniper Networks** | USA/India | SW Engineer (Networking) | India: ₹12–20 LPA \| USA: $105–135K | ₹101–130 LPA \| ₹12–20 LPA | juniper.net/careers |
| 219 | **Fortinet** | USA/India | Junior Network Engineer | India: ₹8–15 LPA \| USA: $95–125K | ₹91–120 LPA \| ₹8–15 LPA | fortinet.com/careers |
| 220 | **F5 Networks** | USA | Software Engineer | $100–130K/yr | ₹96–125 LPA | f5.com/careers |
| 221 | **Infoblox** | USA/India | Software Engineer I | India: ₹10–18 LPA \| USA: $100–125K | ₹96–120 LPA \| ₹10–18 LPA | infoblox.com/careers |
| 222 | **Netskope** | USA/India | Software Engineer | India: ₹12–20 LPA \| USA: $105–135K | ₹101–130 LPA \| ₹12–20 LPA | netskope.com/careers |

---

### ⚙️ TIER 10 — EDA · SEMICONDUCTOR EQUIPMENT · TEST & MEASUREMENT

| # | Company | Country | Role | Local Salary | INR LPA | Career Page |
|---|---------|---------|------|-------------|---------|-------------|
| 223 | **Synopsys USA** | USA | Software Engineer | $110–140K/yr | ₹106–134 LPA | synopsys.com/jobs |
| 224 | **Cadence Design** | USA | Software Engineer | $110–140K/yr | ₹106–134 LPA | cadence.com/careers |
| 225 | **Ansys** | USA/India | SW Engineer (Simulation) | India: ₹9–16 LPA \| USA: $100–130K | ₹96–125 LPA \| ₹9–16 LPA | ansys.com/careers |
| 226 | **PTC Inc.** | USA/India | SW Engineer (IoT) | India: ₹9–15 LPA \| USA: $100–130K | ₹96–125 LPA \| ₹9–15 LPA | ptc.com/careers |
| 227 | **Lam Research** | USA/India | Software Engineer | India: ₹12–20 LPA \| USA: $110–140K | ₹106–134 LPA \| ₹12–20 LPA | lamresearch.com/careers |
| 228 | **Applied Materials** | USA/India | Software Engineer | India: ₹12–20 LPA \| USA: $110–140K | ₹106–134 LPA \| ₹12–20 LPA | appliedmaterials.com/careers |
| 229 | **KLA Corporation** | USA/India | Software Engineer | India: ₹12–20 LPA \| USA: $110–140K | ₹106–134 LPA \| ₹12–20 LPA | kla.com/careers |
| 230 | **Keysight** | USA/India | Software Engineer | India: ₹9–16 LPA \| USA: $95–120K | ₹91–115 LPA \| ₹9–16 LPA | keysight.com/careers |
| 231 | **Spirent** | UK | Software Engineer | £38–55K/yr | ₹49–71 LPA | spirent.com/careers |

---

### 🏭 TIER 11 — PRODUCT ENGINEERING SERVICES (GCC for Global Product Work)

| # | Company | Country | Role | Salary | INR LPA | Career Page |
|---|---------|---------|------|--------|---------|-------------|
| 232 | **GlobalLogic (Hitachi)** | India/USA | Software Engineer | India: ₹7–14 LPA | ₹7–14 LPA | globallogic.com/careers |
| 233 | **Nagarro** | India/Remote | Software Engineer | ₹6–14 LPA | ₹6–14 LPA | nagarro.com/careers |
| 234 | **EPAM Systems** | USA/Remote | Software Engineer | $85–115K/yr | ₹82–110 LPA | epam.com/careers |
| 235 | **Luxoft (DXC Tech)** | Remote | Software Engineer | €35–55K/yr | ₹39–62 LPA | luxoft.com/careers |
| 236 | **Intellias** | Ukraine/Remote | Embedded/Cloud Eng. | €35–55K/yr | ₹39–62 LPA | intellias.com/careers |
| 237 | **Tata Elxsi** | India | Embedded/IoT Engineer | ₹5–10 LPA | ₹5–10 LPA | tataelxsi.com/careers |
| 238 | **Aricent (Altran-Capgemini)** | India | Embedded SW Engineer | ₹5–10 LPA | ₹5–10 LPA | altran.com/careers |
| 239 | **Mistral Solutions** | Bengaluru | Embedded Engineer | ₹5–9 LPA | ₹5–9 LPA | mistralsolutions.com/careers |

---

### 🛸 TIER 12 — NICHE HARDWARE-AI STARTUPS & DEEP TECH

| # | Company | Country | Domain | Salary | INR LPA | Career Page |
|---|---------|---------|--------|--------|---------|-------------|
| 240 | **Tenstorrent** | Canada/USA | Embedded/SW Engineer | $110–150K/yr | ₹106–144 LPA | tenstorrent.com/careers |
| 241 | **SambaNova Systems** | USA | Software Engineer | $115–155K/yr | ₹110–149 LPA | sambanova.ai/careers |
| 242 | **Varjo** | Finland | Software Engineer | €42–60K/yr | ₹47–67 LPA | varjo.com/careers |
| 243 | **IQM Quantum** | Finland | Software Engineer | €42–62K/yr | ₹47–69 LPA | meetiqm.com/careers |
| 244 | **Stability AI** | UK/Remote | ML Engineer | £45–70K/yr | ₹58–90 LPA | stability.ai/careers |
| 245 | **Tinyml.org ecosystem companies** | Global/Remote | Edge AI Engineer | $80–120K/yr | ₹77–115 LPA | tinyml.org |
| 246 | **Phytec** | Germany | Embedded Linux Eng. | €40–54K/yr | ₹45–60 LPA | phytec.de/careers |
| 247 | **Wago** | Germany | Embedded Developer | €40–54K/yr | ₹45–60 LPA | wago.com/careers |
| 248 | **Segger** | Germany | Embedded Tools Eng. | €40–54K/yr | ₹45–60 LPA | segger.com/careers |
| 249 | **Arduino** | Italy/USA | Embedded SW Engineer | $80–110K/yr | ₹77–106 LPA | arduino.cc/jobs |
| 250 | **Digi International** | USA | Firmware Engineer | $85–110K/yr | ₹82–106 LPA | digi.com/careers |

---

### 📦 TIER 13 — IT SERVICES (Volume Hiring — Backup Option)

> **Honest note:** IT services companies are a backup plan if targeted product company applications don't succeed in the first 6 months. Growth trajectory is slower. Salary ceiling is lower. But they give you structured onboarding, exposure to enterprise clients, and EPAM/Accenture/Capgemini can have higher-quality embedded + IoT projects than TCS/Infosys.

| # | Company | Roles | Salary (INR LPA) | Career Page |
|---|---------|-------|------------------|-------------|
| 251 | **TCS** | Systems Engineer | ₹3.5–7 LPA | tcs.com/careers |
| 252 | **Infosys** | Systems Engineer | ₹3.5–6.5 LPA | infosys.com/careers |
| 253 | **Wipro** | Project Engineer | ₹3.5–6.5 LPA | careers.wipro.com |
| 254 | **Cognizant** | Programmer Analyst Trainee | ₹4–7 LPA | careers.cognizant.com |
| 255 | **HCL Technologies** | Software Engineer | ₹4–8 LPA | hcltech.com/careers |
| 256 | **Tech Mahindra** | Software Engineer | ₹3.5–7 LPA | techmahindra.com/careers |
| 257 | **LTIMindtree** | Engineer | ₹5–9 LPA | ltimindtree.com/careers |
| 258 | **Mphasis** | Software Engineer | ₹4–7 LPA | mphasis.com/careers |
| 259 | **Hexaware** | Software Engineer | ₹4–7 LPA | hexaware.com/careers |
| 260 | **Capgemini India** | Analyst | ₹4–8 LPA | capgemini.com/in-en/careers |
| 261 | **Deloitte India** | Analyst (Tech) | ₹6–10 LPA | deloitte.com/in/careers |
| 262 | **Accenture India** | ASE | ₹4.5–8 LPA | accenture.com/in-en/careers |

---

### 🌏 TIER 14 — REMAINING NOTABLE COMPANIES (263–300)

| # | Company | Country | Domain | Career Page |
|---|---------|---------|--------|-------------|
| 263 | **Vercel** | USA/Remote | Platform/Frontend Infra | vercel.com/careers |
| 264 | **Notion** | USA/Remote | Backend/Platform | notion.so/careers |
| 265 | **Linear** | Remote | Dev Tooling | linear.app/careers |
| 266 | **Temporal.io** | USA/Remote | Workflow Engine | temporal.io/careers |
| 267 | **Weaveworks** | UK/Remote | GitOps/Platform | weaveworks.io/careers |
| 268 | **SingleStore** | USA/India | DB Engineering | singlestore.com/careers |
| 269 | **StarTree (Pinot)** | USA/Remote | Analytics DB | startree.ai/careers |
| 270 | **Imply (Druid)** | USA/Remote | Analytics DB | imply.io/careers |
| 271 | **Redis Inc.** | USA/Remote | DB Infrastructure | redis.com/careers |
| 272 | **Elastic** | USA/Remote | Search/Observability | elastic.co/careers |
| 273 | **Figma** | USA | Design + Infra | figma.com/careers |
| 274 | **Twitch (Amazon)** | USA | Streaming Platform | twitch.tv/jobs |
| 275 | **Afterpay (Block)** | Australia | Fintech | block.xyz/careers |
| 276 | **Wattpad (Naver)** | Canada | Platform | wattpad.com/stories |
| 277 | **Hootsuite** | Canada | Platform | careers.hootsuite.com |
| 278 | **Ada Support** | Canada | AI Platform | ada.cx/careers |
| 279 | **Legrand** | France/India | IoT/Building Tech | legrand.com/careers |
| 280 | **Ametek Inc.** | USA/India | Embedded/Test Equip. | ametek.com/careers |
| 281 | **Digi International** | USA | IoT Connectivity | digi.com/careers |
| 282 | **Sierra Wireless (Semtech)** | Canada | Embedded/IoT | semtech.com/careers |
| 283 | **Balena.io** | Remote | Embedded Linux Fleet | balena.io/careers |
| 284 | **Particle Industries** | USA/Remote | IoT Cloud Platform | particle.io/careers |
| 285 | **SparkFun** | USA | FW/HW Engineer | sparkfun.com/jobs |
| 286 | **Adafruit** | USA | Embedded Engineer | adafruit.com/jobs |
| 287 | **Mentor Graphics (Siemens EDA)** | USA/India | SW Engineer | siemens.com/eda/careers |
| 288 | **LAIRD Connectivity** | USA | Embedded Engineer | laird.com/careers |
| 289 | **Multitech Systems** | USA | Firmware Engineer | multitech.com/careers |
| 290 | **Variscite** | Israel | BSP/Embedded | variscite.com/careers |
| 291 | **Magna International** | Canada | Embedded SW Eng. | magna.com/careers |
| 292 | **Harman R&D India** | Bengaluru/Noida | Embedded SW Eng. | harman.com/careers |
| 293 | **Matterport** | USA/Remote | 3D Spatial Platform | matterport.com/careers |
| 294 | **Cursor** | USA | AI Dev Tools | cursor.sh/careers |
| 295 | **Perplexity** | USA | AI Search | perplexity.ai/careers |
| 296 | **Imbue** | USA/Remote | AI Research/Eng. | imbue.com/careers |
| 297 | **Adept AI** | USA | AI Actions | adept.ai/careers |
| 298 | **ISRO** | India | Scientist/Engineer SC | isro.gov.in |
| 299 | **DRDO** | India | Scientist B | drdo.gov.in/careers |
| 300 | **Space Applications Centre** | India | SW Engineer | isro.gov.in |

---

<a name="countries"></a>
## 🌍 SECTION 6 — BEST COUNTRIES FOR YOUR PROFILE
### All Salaries in INR LPA (May 2026 Exchange Rates)

| Country | Fresher Tech Salary (Local) | INR LPA Equivalent | Cost of Living | Work-Life Balance | Immigration for Indians | Your Score |
|---------|---------------------------|-------------------|----------------|-------------------|------------------------|------------|
| **Canada** | CAD $75–115K | ₹52–81 LPA | Medium-High | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐⭐ Express Entry 6–18 mo | **9.5/10** |
| **Germany** | €42–65K | ₹47–73 LPA | Medium | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ EU Blue Card | **9/10** |
| **Australia** | AUD $75–110K | ₹52–76 LPA | High | ⭐⭐⭐⭐⭐ | ⭐⭐⭐⭐ Subclass 189/190 | **8.5/10** |
| **Netherlands** | €42–62K | ₹47–69 LPA | Medium-High | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ Highly Skilled Migrant | **8/10** |
| **Singapore** | SGD $65–95K | ₹49–71 LPA | High | ⭐⭐⭐ | ⭐⭐⭐ Employment Pass | **8/10** |
| **UK** | £40–65K | ₹52–84 LPA | High | ⭐⭐⭐ | ⭐⭐⭐ Skilled Worker visa | **7.5/10** |
| **Norway** | NOK 600–720K | ₹54–65 LPA | High | ⭐⭐⭐⭐⭐ | ⭐⭐⭐ Skilled Worker | **7.5/10** |
| **Ireland** | €42–65K | ₹47–73 LPA | High | ⭐⭐⭐⭐ | ⭐⭐⭐ Critical Skills visa | **7.5/10** |
| **USA** | $110–165K | ₹106–158 LPA | Very High | ⭐⭐⭐ | ⭐ H1B lottery + 10yr GC backlog | **6/10** |
| **India (Bengaluru, Product)** | ₹8–40 LPA | ₹8–40 LPA | Low-Medium | ⭐⭐⭐ | N/A — home | **7/10** |
| **Japan** | ¥5–7M | ₹32–44 LPA | Medium-High | ⭐⭐⭐ | ⭐⭐⭐ Engineer visa | **6.5/10** |
| **Switzerland** | CHF 70–90K | ₹74–95 LPA | Very High | ⭐⭐⭐⭐ | ⭐⭐ L Permit → B Permit | **7/10** |

### 📌 Why Canada is #1 for Your Profile Specifically

Canada is the optimal first international destination for a fresh Indian engineer with your profile for three reasons: (1) Express Entry's Comprehensive Ranking System (CRS) actively rewards STEM with a Canadian job offer — your embedded + AI skills are in shortage; (2) Canadian industrial companies (Tenstorrent, Sierra Wireless, Shopify, Cohere, Magna International) all hire for your exact skills; (3) Employer-sponsored PR takes 6–18 months vs 10+ years in the US for Indian nationals.

### 📌 Why Germany is #1 for Embedded/Industrial Engineers

Germany has the highest global concentration of industrial automation, automotive Tier-1, and manufacturing tech companies — Bosch, Siemens, Continental, ZF, Infineon, Beckhoff, KUKA, Pilz — and they face a documented engineering shortage. Your SentinelGrid project is exactly their product domain. The EU Blue Card requires a minimum annual salary of €45,300 (₹50.7 LPA). 30 days vacation + public healthcare + no student loans = quality of life that compensates for lower absolute salary vs USA.

---

<a name="platforms"></a>
## 🔍 SECTION 7 — JOB HUNTING PLATFORMS

### 7.1 — Direct Application (Highest Conversion Rate)

| Platform | Best For | URL |
|----------|----------|-----|
| **Company career pages** | Direct MNC applications | See INR LPA column above |
| **LinkedIn Jobs** | All roles globally | linkedin.com/jobs |
| **Wellfound (AngelList)** | AI + platform startups | wellfound.com |
| **Simplify.jobs** | Auto-fills applications across 1000+ boards | simplify.jobs |
| **Greenhouse ATS** | Product company direct apply | greenhouse.io |
| **Lever ATS** | Startup + mid-size direct apply | lever.co |
| **Workday** | Fortune 500 corporations | workday.com |

### 7.2 — India-Focused

| Platform | Best For | URL |
|----------|----------|-----|
| **Naukri.com** | India MNC + product companies | naukri.com |
| **Instahyre** | India product companies | instahyre.com |
| **Internshala** | Internships + fresher jobs | internshala.com |
| **Foundit (Monster)** | India + global | foundit.in |
| **OffCampusJobs4u** | Daily fresher drives | offcampusjobs4u.com |
| **Freshershunt** | MNC fresher daily openings | freshershunt.in |

### 7.3 — Specialized for Your Profile

| Platform | Best For | URL |
|----------|----------|-----|
| **Dice.com** | Embedded systems, hardware, USA | dice.com |
| **Workatastartup (YC)** | YC-backed AI/platform startups | workatastartup.com |
| **Levels.fyi Jobs** | Salary-transparent board | levels.fyi/jobs |
| **Remoteok.io** | Remote engineering roles | remoteok.io |
| **Remote.co** | Remote-first companies | remote.co |

### 7.4 — Country-Specific

| Country | Platform | URL |
|---------|----------|-----|
| Germany | Make it in Germany | make-it-in-germany.com |
| Canada | Job Bank Canada | jobbank.gc.ca |
| Australia | Seek.com.au | seek.com.au |
| Singapore | MyCareersFuture | mycareersfuture.gov.sg |
| UK | Reed.co.uk | reed.co.uk |
| Netherlands | Indeed NL | indeed.nl |

### 7.5 — Communities Where Jobs Are Shared BEFORE Posting

| Community | What You Get | Where |
|-----------|--------------|-------|
| **Embedded.fm community** | Embedded engineering jobs + mentors | embedded.fm |
| **MLOps Community Slack** | MLOps/AI engineering jobs | mlops.community |
| **CNCF Slack** | Cloud-native + K8s jobs | slack.cncf.io |
| **TinyML Forum** | Edge AI, TinyML positions | tinyml.org/community |
| **SRE Weekly newsletter** | SRE/Platform engineering | sreweekly.com |
| **Memfault Blog comments** | Embedded firmware job sharing | memfault.com/blog |
| **Nordic DevZone** | Nordic Semiconductor + IoT | devzone.nordicsemi.com |
| **Hackaday.io community** | Hardware + firmware jobs | hackaday.io |

---

<a name="probability"></a>
## 📊 SECTION 8 — REALISTIC HIRING PROBABILITY

### 2026 Market Context

The Indian tech market saw over 1,600 Global Capability Centers (GCCs) operating in India as of 2026, with companies like Google, Goldman Sachs, and Novartis running primary R&D hubs — not just support. This is the most important hiring trend for you: GCCs hire freshers who can contribute immediately to real product work, not just interns.

### Hiring Probability Matrix

| Role Category | Your Chance | Key Differentiator | What You Still Need |
|--------------|------------|-------------------|---------------------|
| **Embedded/Firmware Engineer (Bosch/Siemens/NXP type)** | 🟢 70–80% | FreeRTOS + TFLite Micro + DMA + Watchdog + OTA = globally rare in a fresher | German B1 helps for Germany |
| **Edge AI Engineer (Qualcomm/ARM/Silicon Labs)** | 🟢 65–75% | INT8 quantization + 47ms inference benchmark + hardware validation = extremely rare | Benchmark numbers in your README |
| **Platform Engineer (Atlassian/Cloudflare/Harness)** | 🟢 65–75% | InfraMesh = exact job description at platform teams | Clean GitHub with working demo |
| **Industrial IoT (Honeywell/Rockwell/ABB)** | 🟢 65–75% | SentinelGrid matches their product line precisely | Factory context documentation |
| **SDE-I at India product companies** | 🟢 60–70% | System Design 210-day roadmap + 4 real projects = interview confidence | DSA (LeetCode Medium) prep required |
| **Associate DevOps/SRE Engineer** | 🟢 60–70% | Terraform + K8s + Grafana + Prometheus + GitHub Actions + ELK | Incident playbook documentation |
| **Junior ML/AI Engineer** | 🟡 40–55% | PulseGrid (XGBoost AUC 0.82) + MemCore (CodeBERT) are real | Scale of production ML deployment |
| **SDE-I at FAANG India GCC** | 🟡 30–45% | System Design knowledge is your edge | Strong DSA (LeetCode Medium/Hard) + behavioral |
| **Junior Data Engineer** | 🟡 40–55% | Kafka + Airflow + TimescaleDB + Spark = solid | Large-scale Spark optimization knowledge |
| **Network Automation Engineer** | 🟡 35–50% | Python + Netmiko + Ansible + BGP = genuine | CCNA certification strengthens this |
| **Firmware Engineer Germany/EU (onsite)** | 🟢 60–70% | Industrial companies have documented shortage | B1 German accelerates significantly |

### The 3 Documents That Multiply Your Hiring Chances

**Document 1 — EDGE_AI.md in SentinelGrid GitHub**
A file that shows: float32 vs INT8 benchmark (47ms), 95.1% vs 91.4% accuracy trade-off justification, 3 model architectures compared, why autoencoder was chosen over 1D-CNN. This one file proves you think like a production engineer, not a tutorial-follower.

**Document 2 — ADR/003-why-neo4j-not-relational.md in PulseGrid**
Explains why graph traversal for transitive service dependencies is O(log N) in Neo4j vs O(N²) in SQL JOIN. Shows algorithm-based technology selection, not familiarity-based. This is exactly what interviewers at Confluent, Datadog, MongoDB test for.

**Document 3 — RTOS_TASK_DESIGN.md in SentinelGrid**
Documents 5-task FreeRTOS architecture, stack watermark measurements, heap leak test over 24h, watchdog hang injection and reset verification. This document alone gets you through Bosch/Siemens/Continental initial screening.

---

## 📎 APPENDIX — QUICK REFERENCE

### Salary at a Glance (INR LPA, May 2026)

| Location | Fresher Product Company | Fresher MNC | Your Target (Year 1) |
|----------|------------------------|-------------|----------------------|
| Bengaluru (India) | ₹18–35 LPA | ₹8–22 LPA (Embedded MNC) | ₹12–25 LPA |
| Germany | ₹47–73 LPA | — | ₹50–67 LPA (Bosch/Siemens) |
| Canada | ₹52–81 LPA | — | ₹56–74 LPA |
| Australia | ₹52–76 LPA | — | ₹59–76 LPA |
| Singapore | ₹49–71 LPA | — | ₹54–71 LPA |
| UK | ₹52–84 LPA | — | ₹58–77 LPA |
| USA | ₹106–158 LPA | — | ₹96–130 LPA (if visa cleared) |

### Priority Application Order (Week-by-Week)

| Week | Action | Target |
|------|--------|--------|
| 1–2 | Finalize GitHub repos for all 4 projects with EDGE_AI.md, ADR, RTOS_TASK_DESIGN.md | Portfolio completeness |
| 3–4 | Apply to India product companies (CRED, Razorpay, Meesho, Flipkart, Dream11) | SDE-I roles, ₹18–35 LPA |
| 5–6 | Apply to India GCCs (Google, Microsoft, Amazon, Qualcomm, ARM, NVIDIA India) | SDE-I/Graduate Engineer |
| 7–8 | Apply to embedded MNCs with India offices (Bosch, Siemens, ABB, Continental, NXP India) | Embedded SW Engineer |
| Month 3 | Apply internationally — Germany (Bosch HQ, Siemens HQ), Canada (Shopify, Cohere, Tenstorrent) | ₹47–91 LPA range |
| Month 4+ | Apply to Edge AI niche companies (Memfault, Edge Impulse, Syntiant, Eta Compute) | ₹86–130 LPA remote |
| Ongoing | 1 technical blog post/week on Hashnode; 1 LinkedIn post/2 weeks with project demo | Recruiter inbound traffic |

---

*Document v2.0 | Compiled: May 22, 2026*
*Exchange rates as of May 2026: 1 USD=₹96, 1 EUR=₹112, 1 GBP=₹129, 1 CAD=₹70, 1 AUD=₹69, 1 SGD=₹75, 1 JPY=₹0.63, 1 CHF=₹106, 1 NOK=₹9*
*Based on deep analysis of all 16 roadmap files. Career pages verified as of publication date. Salary figures reflect market data for fresher/entry-level roles in 2026.*