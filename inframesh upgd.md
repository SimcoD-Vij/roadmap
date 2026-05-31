# PulseGrid — Engineering Intelligence and Incident Prediction Platform
## A Completely Original Project | Real Problem | No Existing Open Solution | MNC-Standard

---

# ORIGIN OF THIS PROJECT

This project was not derived from any transcript, tutorial, or existing tool.

It was designed by identifying a specific gap: every company generates enormous amounts of engineering signals — from GitHub, from CI/CD pipelines, from incident management tools, from error trackers, from performance monitors — but nobody connects these signals into a single intelligent system that can predict problems before they occur and explain system behavior in plain language.

The companies that have built internal versions of this are Google (internal tool called Dapper/Monarch combined with SRE tooling), Netflix (internal reliability engineering platform), and LinkedIn (internal deployment intelligence system). None of them have open-sourced it. No startup has productized it well. This gap is real, documented, and actively discussed in SRE and platform engineering communities.

---

# SECTION 1 — THE PROBLEM

## What Happens in Every Engineering Organization Above 20 People

A company has 40 engineers working across 25 microservices. On a Tuesday afternoon, the payment service starts returning errors. Within 8 minutes, 12% of users cannot complete checkout. Revenue loss begins.

**What the on-call engineer experiences:**

14:22 — PagerDuty fires. Alert: "payment-service error rate above 5%."

14:23 — Engineer opens Grafana. Sees error rate spike. Tries to understand what changed.

14:25 — Opens GitHub. Looks at recent commits to payment-service. Finds a deployment 40 minutes ago. Checks the PR. 847 lines changed across 23 files.

14:28 — Opens the CI/CD pipeline logs. Build passed. All tests passed.

14:30 — Opens Sentry. 2,340 errors in the last 10 minutes. All pointing to a database connection timeout.

14:32 — Opens the database monitoring tool (separate login). Sees connection pool exhausted.

14:34 — Realizes the connection pool size was changed in the deployment. Reverts the change.

14:40 — Service recovers. 18 minutes of degraded service. Estimated loss: $45,000 in abandoned checkouts.

**The engineer then has to write a postmortem. From memory. Piecing together a timeline from 6 different tools.**

**What went wrong before the alert fired:**

- The PR that changed the connection pool was reviewed by two engineers who were not familiar with the production load on the payment service database
- The change was not tested under production-level concurrent connections
- Three other PRs in the past 2 weeks had touched the same database configuration file — a pattern that historically correlates with incidents in this codebase
- The deployment happened on a Tuesday afternoon — the highest traffic period of the week
- The engineer who understood the database configuration best was on vacation

None of this information was visible to anyone before the deployment happened.

**This happens in every engineering organization. Multiple times per month. The aggregate cost is enormous.**

## The Specific Gap PulseGrid Fills

There are tools for each individual signal:
- GitHub shows commits and PRs
- Jenkins/GitHub Actions shows build and test results
- PagerDuty shows incidents
- Sentry shows errors
- Datadog/Grafana shows metrics
- Jira shows tickets

**No tool connects them.** No tool says: "This deployment has a 73% probability of causing an incident in the next 4 hours based on patterns we have seen before." No tool says: "The blast radius if payment-service goes down right now is 8 dependent services affecting 34% of active users." No tool generates a postmortem draft automatically from all of the signals combined.

PulseGrid does all three.

---

# SECTION 2 — WHAT PULSGRID IS

## Full Name
**PulseGrid — Real-Time Engineering Intelligence and Incident Prediction Platform**

## One-Line Description
PulseGrid ingests signals from every engineering tool a company uses — GitHub, CI/CD pipelines, incident management, error tracking, performance monitoring — correlates them in real time using a stream processing pipeline and ML models, and produces three things that do not currently exist in any open tool: deployment risk scores before incidents happen, live blast radius maps for any service at any moment, and AI-generated postmortem drafts after incidents resolve.

## The Three Core Features

### Feature 1 — Deployment Risk Scoring (Before Incidents Happen)

When a developer opens a pull request, PulseGrid analyzes it in real time and produces a risk score from 0 to 100.

The risk score is computed from signals that no single tool combines:

**Code signals (from GitHub):**
- Size of the change (lines added, lines deleted, files touched)
- Which specific files were modified — files that have historically appeared in incident postmortems get higher weight
- Which components of the system were touched (PulseGrid maintains a component map)
- Time since those files were last touched — files modified after long dormancy have higher incident correlation
- Test coverage delta — did coverage decrease?
- PR review time — PRs reviewed in under 5 minutes have higher incident rates than PRs reviewed over 20 minutes
- Reviewer familiarity with the changed components — does the reviewer have recent commit history in these files?

**Deployment context signals:**
- Day of week and time of day — Tuesday 2PM has 3× the incident rate of Thursday 10AM in most engineering orgs
- Number of concurrent deployments — deploying 4 services simultaneously increases incident probability because causality becomes harder to isolate
- Days since last incident in this service — recent incident history indicates instability
- Current on-call engineer familiarity with this service — if the person who would respond to an incident has never been primary for this service, risk increases

**Historical signals (the ML component):**
- What did PRs that caused incidents look like? What features did they have in common?
- A gradient-boosted classifier trained on the organization's own incident history learns these patterns
- The model continuously retrains as new incidents are resolved

**Output:** A risk card appears on the PR itself (via GitHub webhook → PulseGrid → GitHub comment) that says:

```
PulseGrid Risk Assessment
─────────────────────────────────────────
Risk Score: 71 / 100  ⚠️  HIGH RISK

Contributing factors:
• 3 of 5 modified files appeared in incident postmortems (last 90 days)
• Deployment scheduled during peak traffic window (14:00–16:00 Tue)
• No reviewer has committed to payment/db/config.py in past 60 days
• Test coverage decreased from 84% → 79%
• 2 other services deploying simultaneously

Recommendation: Consider delaying to off-peak window or adding
a reviewer with database configuration experience.

Historical accuracy of this score: 68% of PRs scoring >70 caused incidents
─────────────────────────────────────────
```

This is not a hard block. It is intelligence. The team decides. But it is intelligence they did not have before.

### Feature 2 — Live Blast Radius Calculator (What Breaks If This Goes Down)

At any moment, an engineer opens PulseGrid and clicks on any service. PulseGrid shows in real time:

**What depends on this service (upstream):**
- Which services call this service directly
- Which services call those services (transitive dependencies)
- Which user-facing features route through this service

**What this service depends on (downstream):**
- Which databases this service queries
- Which other services this service calls
- Which third-party APIs this service uses

**Current impact estimate:**
- Based on live traffic data, what percentage of active users would be affected
- Which revenue-generating flows go through this service
- Estimated revenue impact per minute of downtime (configurable based on business metrics)

**The dependency graph is built automatically** by ingesting:
- Distributed traces from the observability system (OpenTelemetry/Jaeger) — if Service A's trace includes a call to Service B, the dependency is recorded
- Deployment manifests (Kubernetes service definitions, docker-compose files)
- API gateway routing rules
- Database connection strings (which service uses which database)

The graph updates continuously. It reflects the current state of the system, not a manually maintained diagram that goes stale.

**This solves a specific production pain:** In most companies, service dependency maps are either nonexistent or maintained manually in a Confluence document that is outdated within weeks. During an incident, engineers do not know what else will break when they restart a service or roll back a deployment. PulseGrid makes this knowledge automatic and live.

### Feature 3 — AI-Generated Incident Postmortem Draft

When PagerDuty marks an incident as resolved, PulseGrid automatically generates a postmortem draft within 5 minutes.

The draft is generated by:

**Step 1 — Timeline reconstruction:**
PulseGrid queries all ingested signals for the incident window (30 minutes before alert through resolution):
- All deployments that happened in the preceding 2 hours
- All error rate changes in Sentry
- All metric anomalies in the performance monitoring system
- All alert state changes in PagerDuty
- All Slack messages in the on-call channel (if Slack integration enabled)

**Step 2 — Root cause identification:**
Using the timeline, PulseGrid identifies the most probable causal event — the deployment or configuration change that preceded the anomaly by the shortest time interval while matching the incident's service scope.

**Step 3 — AI narrative generation:**
The timeline and identified root cause are passed to a language model (Claude API or similar) with a structured prompt that produces:
- A factual incident timeline in chronological order
- A root cause section with contributing factors
- An impact section with affected services, users, and estimated revenue
- A blank action items section (humans fill this in — AI does not generate action items because they require organizational context)

**Step 4 — Draft delivery:**
The postmortem draft is posted as a Confluence page (or Notion page or GitHub wiki page) and a Slack message is sent to the team: "PulseGrid has drafted a postmortem for the payment-service incident. Review and complete by Friday."

**What this saves:** A postmortem that takes a senior engineer 2-3 hours to write from memory across 6 tools now takes 20 minutes to review and complete. The factual reconstruction is done. The narrative is drafted. The engineer focuses on corrective actions and organizational learning — the parts that require human judgment.

---

# SECTION 3 — WHY THIS IS GENUINELY NEW

## What Existing Tools Do and Where They Stop

| Tool | What It Does | What It Cannot Do |
|------|-------------|------------------|
| GitHub | Shows PRs, commits, reviews | Does not know incident history or production impact |
| PagerDuty | Manages incidents, alerting | Does not know what caused the incident |
| Sentry | Tracks errors in production | Does not connect errors to deployments automatically |
| Datadog | Monitors metrics | Does not predict which deployment will cause metric anomalies |
| Backstage (Spotify) | Service catalog | Does not do live blast radius or risk scoring |
| LinearB / Haystack | Engineering metrics (DORA) | Measures past performance, does not predict future incidents |
| Cortex | Service scorecards | Static health checks, not real-time incident prediction |
| FireHydrant | Incident management | Response workflow, not prediction |
| Blameless | SRE platform | Retrospectives, not pre-deployment intelligence |

**None of these tools:**
- Score deployment risk before the deployment happens
- Calculate live blast radius from real traffic data
- Generate postmortem drafts automatically

The combination of all three in one system with a real-time stream processing pipeline connecting every engineering signal is what does not exist in open form.

## Companies That Have Internal Versions

**Google:** The SRE book documents Google's internal approach to deployment risk and blast radius. Google's internal tools (not public) do versions of this. The book is public; the tools are not.

**Netflix:** Netflix's engineering blog documents their Chaos Engineering platform (Chaos Monkey) and their deployment intelligence work. Their internal tools track deployment impact automatically.

**LinkedIn:** LinkedIn's engineering blog documents their "Nurse" system that monitors deployment health and triggers rollbacks. Partial but directionally similar.

**Stripe:** Stripe's engineering blog documents their deployment review system that adds context to PRs. Partial.

**None of these are open source. None are available as self-hostable tools.**

PulseGrid is the open, self-hostable version of what these companies built internally.

---

# SECTION 4 — WHO USES PULSGRID

## Primary User — The On-Call Engineer

**Before PulseGrid:** Incident happens → engineer opens 6 tools → manually correlates timeline → spends 18 minutes diagnosing what took 2 minutes to break.

**After PulseGrid:** Incident happens → engineer opens PulseGrid incident view → sees pre-assembled timeline, deployment correlation, blast radius, and probable root cause → diagnosis time: 3 minutes.

## Secondary User — The Engineering Team Lead or Tech Lead

Before merging a PR, they open PulseGrid's risk score. If the score is above 70 and the deployment window is peak traffic, they delay to off-peak. This decision, which previously required the tech lead to manually look at 4 sources of information, now takes 10 seconds.

## Tertiary User — The VP of Engineering or CTO

PulseGrid's reliability dashboard shows: which services have caused the most incidents in the past 90 days, which teams have the highest deployment risk scores, which parts of the system are the biggest blast radius risks, and how DORA metrics (deployment frequency, lead time, MTTR, change failure rate) are trending across all teams.

This gives leadership a data-driven view of engineering system health that previously required manual data collection from multiple tools — usually done quarterly and always outdated by the time it was reviewed.

---

# SECTION 5 — TECHNICAL REQUIREMENTS

## Functional Requirements

| Requirement | Priority | Description |
|-------------|----------|-------------|
| GitHub webhook ingestion | Critical | Receive PR opened/merged/closed events in real time |
| Deployment event ingestion | Critical | Receive deployment events from CI/CD (GitHub Actions, Jenkins, ArgoCD) |
| Incident event ingestion | Critical | Receive incident opened/resolved events from PagerDuty or OpsGenie |
| Error event ingestion | High | Receive error rate changes from Sentry or Datadog |
| Metric ingestion | High | Receive performance metrics from Prometheus or Datadog |
| Trace ingestion | High | Receive distributed traces from OpenTelemetry collector |
| PR risk scoring | Critical | Compute and post risk score as GitHub PR comment within 60 seconds of PR open |
| Risk model training | Critical | Weekly retraining of risk classifier on organization's incident history |
| Dependency graph construction | Critical | Build and maintain live service dependency graph from traces + manifests |
| Blast radius calculation | Critical | On-demand calculation of blast radius for any service |
| Incident timeline assembly | High | Automatic timeline reconstruction within 5 minutes of incident resolution |
| Postmortem draft generation | High | AI-generated postmortem posted to Confluence/Notion within 5 minutes |
| DORA metrics dashboard | Medium | Deployment frequency, lead time, MTTR, change failure rate per service and team |
| Alert: risk score above threshold | Medium | Notify team if PR risk score exceeds configurable threshold |
| Multi-organization support | Low | SaaS mode: multiple organizations with data isolation |

## Non-Functional Requirements

| Requirement | Target | How Measured |
|-------------|--------|--------------|
| Webhook processing latency | < 2 seconds from GitHub event to stored record | Prometheus histogram on webhook handler |
| Risk score computation | < 60 seconds from PR open to comment posted | End-to-end trace from webhook receipt to GitHub API call |
| Blast radius calculation | < 3 seconds for any service | API response time p99 |
| Postmortem draft generation | < 5 minutes from incident resolved to draft posted | Measured in PulseGrid incident log |
| Event ingestion throughput | 10,000 events per minute peak | Load tested with k6 + event simulator |
| Dependency graph freshness | Updated within 60 seconds of new trace data | Lag between trace ingestion and graph update |
| Uptime | 99.5% — PulseGrid is non-critical path (does not block deployments) | Uptime monitor |
| Data retention | 12 months of all events | TimescaleDB retention policy |

## Technology Stack

| Layer | Technology | Why This Choice |
|-------|-----------|----------------|
| Event Ingestion API | FastAPI + Python | Async webhook handlers, high throughput, Pydantic validation |
| Event Stream | Apache Kafka or AWS Kinesis | 10,000 events/minute requires durable, ordered, replayable stream |
| Stream Processor | Python (Faust or custom Kafka consumer) | Real-time event correlation, dependency graph updates |
| Risk Scoring Worker | Python + scikit-learn / XGBoost | Gradient boosted classifier for PR risk prediction |
| Graph Database | Neo4j or AWS Neptune | Service dependency graph — relationships are first-class data |
| Time-Series Database | TimescaleDB | All events stored with timestamp — time-range queries critical |
| Cache | Redis | Risk score cache, graph traversal cache, rate limiting |
| AI/LLM Integration | Claude API or OpenAI API | Postmortem narrative generation from structured timeline |
| GitHub Integration | GitHub Apps (webhooks + API) | Receive events, post comments, read PR metadata |
| PagerDuty Integration | PagerDuty webhooks + API | Receive incident events, read incident details |
| Sentry Integration | Sentry webhooks + API | Receive error rate events |
| Prometheus Integration | Prometheus remote_write | Receive metrics stream |
| OpenTelemetry Integration | OTLP receiver | Receive distributed traces for dependency graph |
| Backend API | FastAPI | Serve dashboard data, blast radius queries, DORA metrics |
| Frontend Dashboard | React + Recharts | Real-time dependency graph visualization, metrics, risk scores |
| Graph Visualization | D3.js or Cytoscape.js | Interactive service dependency map |
| Container Orchestration | Docker + Kubernetes or ECS | All services containerized |
| Infrastructure as Code | Terraform | All AWS resources |
| CI/CD | GitHub Actions | PulseGrid deploys itself through its own pipeline |
| Observability | PulseGrid monitors itself — structured logging, Prometheus metrics, Grafana | Dogfooding — PulseGrid must observe PulseGrid |

## Infrastructure

```
AWS Account:
├── ECS or EKS cluster
│   ├── FastAPI webhook ingestion service (3 replicas)
│   ├── Stream processor service (2 replicas)
│   ├── Risk scoring worker (2 replicas)
│   ├── Postmortem generator service (1 replica)
│   └── Backend API service (2 replicas)
├── MSK (Managed Kafka) or Kinesis
│   └── Topics: events.github, events.pagerduty, events.sentry,
│              events.metrics, events.traces, events.processed
├── RDS PostgreSQL
│   └── Organization config, user accounts, integration credentials
├── TimescaleDB (RDS PostgreSQL with TimescaleDB extension)
│   └── All ingested events, risk scores, incident timelines
├── Neptune or Neo4j on EC2
│   └── Service dependency graph
├── ElastiCache Redis
│   └── Risk score cache, graph cache, rate limiting
├── S3
│   └── Postmortem drafts, model artifacts, event archives
├── Secrets Manager
│   └── GitHub App credentials, PagerDuty API key, LLM API key
├── CloudFront + S3
│   └── React frontend static hosting
└── Application Load Balancer
    └── Routes to ingestion API and backend API
```

---

# SECTION 6 — WHAT IS COMPLETELY NEW IN PULSGRID

## The Three Things That Do Not Exist Anywhere

### New Thing 1 — Cross-Signal Risk Scoring Using Your Own Incident History

Every existing tool that measures PR risk uses generic heuristics — PR size, test coverage. These are weak signals. The strongest signal is: what did PRs that caused incidents in YOUR codebase look like?

PulseGrid trains on YOUR organization's incident history. A PR touching `payment/db/config.py` is high risk in your organization because that specific file appeared in 4 of your last 8 payment incidents. A PR touching the same file in another organization might be low risk. The model is personalized.

This requires: ingesting your GitHub PR history, ingesting your PagerDuty incident history, correlating them (which PRs were deployed within 2 hours before an incident?), extracting features from the correlated PRs, training a classifier, and continuously retraining as new incidents occur.

No open tool does this. Some commercial tools (Sleuth, LinearB) measure deployment frequency and MTTR but do not predict future incident probability from cross-signal patterns.

### New Thing 2 — Blast Radius Built From Live Traces (Not Manual Documentation)

Every company has a service dependency document somewhere. It is wrong. Services were added last month without updating the document. A service was deprecated but its clients were never updated in the doc. The service that the document says is low-risk is actually called by the payment service on every checkout.

PulseGrid builds the dependency graph from live distributed traces — the actual calls that are happening right now in production. If Service A's trace includes a span from Service B, the edge A→B exists in the graph. If no traces have included that edge in 7 days, the edge is marked dormant.

The blast radius is calculated from this live graph: if service X fails, traverse all upstream dependencies, weight each by call frequency (from trace data), and calculate user impact from traffic patterns.

This requires: OpenTelemetry trace ingestion, span parsing, graph database updates, graph traversal algorithms, traffic weighting. No open tool combines these.

### New Thing 3 — Structured Postmortem Generation From Correlated Signals

Existing AI postmortem tools (there are a few starting to appear) use only the incident management system data — the PagerDuty incident timeline and notes. This misses 80% of the relevant context.

PulseGrid's postmortem generator queries:
- The deployment that preceded the incident (from CI/CD events)
- The specific lines of code changed in that deployment (from GitHub)
- The error pattern in Sentry (what errors, which users, what frequency)
- The metric anomaly pattern (which metrics, what values, what time)
- The on-call slack messages (what the responder tried and when)
- The historical context (has this service had similar incidents before?)

It passes all of this as structured context to the LLM, not as raw text but as a structured schema that the prompt template fills in. The output is a factual, accurate first draft — not a hallucination, because every fact in the draft comes from a real ingested event.

This is 3–5 hours of postmortem work reduced to 20 minutes of review.

---

# SECTION 7 — HOW SKILLS FROM THE ROADMAP ARE USED

| Skill | Where Used in PulseGrid |
|-------|------------------------|
| Python Core | All backend services — ingestion, stream processing, risk scoring, postmortem generation |
| REST API (FastAPI) | Webhook ingestion API, dashboard backend API |
| Async Programming | Webhook handlers must process 10,000 events/minute without blocking |
| Pydantic Validation | Validates GitHub webhook payload, PagerDuty event schema, Sentry alert format |
| SQL + PostgreSQL | Organization data, integration credentials, user accounts |
| TimescaleDB | Every ingested event stored with timestamp — the core data store |
| Redis | Risk score cache (avoid recomputing for same PR on subsequent events), rate limiting |
| Message Queue (Kafka/Kinesis) | Event stream between ingestion and processing — decouples services |
| Stream Processing | Python Kafka consumer that processes events in real time, updates dependency graph |
| Graph Database (Neo4j) | Service dependency graph — relationships between services |
| ML (scikit-learn/XGBoost) | Gradient boosted classifier for PR risk scoring |
| ML Pipeline | Feature extraction from PR+incident data, training, evaluation, weekly retraining |
| LLM Integration (Claude API) | Postmortem draft generation from structured incident timeline |
| GitHub API + Webhooks | Receive PR events, post risk score comments, read PR diff |
| PagerDuty API | Receive incident events, read incident timeline |
| Git | All PulseGrid code versioned, CI/CD triggered by push |
| Linux | Deploying services to EC2/ECS, reading logs via SSH |
| Docker | Every service containerized, docker-compose for local development |
| Terraform | All AWS resources created as code |
| Kubernetes/ECS | Running all PulseGrid services in production |
| AWS Kinesis or Kafka on MSK | Event stream |
| AWS RDS | PostgreSQL + TimescaleDB |
| AWS ElastiCache | Redis |
| AWS Neptune (optional) or Neo4j | Graph database |
| Observability | PulseGrid monitors itself — Prometheus metrics, Grafana dashboard, structured logging |
| Postmortem Writing | PulseGrid generates postmortems AND has its own postmortems when it fails |
| Architecture Decision Records | ADR/ folder with decisions for: why Kafka, why Neo4j, why XGBoost not neural network |
| System Design | Dependency graph construction, blast radius algorithm, risk feature engineering |
| D3.js or Cytoscape.js | Interactive service dependency visualization in React dashboard |

---

# SECTION 8 — WHAT THE DASHBOARD SHOWS

```
PulseGrid — Engineering Intelligence Dashboard
════════════════════════════════════════════════════════════

CURRENT SYSTEM STATUS
├── Services monitored: 67
├── High-risk open PRs: 4  ← requires attention
├── Active incidents: 0
└── Last incident resolved: 3 days ago

HIGH-RISK OPEN PRs (Action Required)
┌─────────────────────────────────────────────────────────┐
│ PR #1847 — payment-service: update db connection pool   │
│ Risk Score: 71/100  ⚠ HIGH                              │
│ Factors: Modified file in 3 past incidents | Peak deploy │
│          window | Reviewer unfamiliar with component     │
│ Reviewer: @ravi_kumar  Posted: 2 hours ago              │
└─────────────────────────────────────────────────────────┘

SERVICE DEPENDENCY MAP (Live)
[Click any service to see blast radius]

     ┌──────────┐       ┌──────────────┐
     │  api-gw  │──────►│ payment-svc  │
     └──────────┘       └──────────────┘
          │                    │
          ▼                    ▼
     ┌──────────┐       ┌──────────────┐
     │ auth-svc │       │  payment-db  │
     └──────────┘       └──────────────┘

payment-service selected:
├── If this fails: 8 services affected
├── User impact: 34% of active sessions
└── Revenue impact: ₹1.8L per minute

DORA METRICS — LAST 30 DAYS
├── Deployment Frequency: 3.2 per day (industry: 1.0 — Elite)
├── Lead Time for Changes: 4.2 hours
├── MTTR: 18 minutes (industry: < 1 hour — Elite)
└── Change Failure Rate: 4.1% (industry: < 5% — Elite)

RELIABILITY TREND — TOP RISK SERVICES
├── payment-service: 3 incidents last 90 days  ← watch
├── auth-service: 1 incident last 90 days
└── notification-service: 0 incidents last 90 days
```

---

# SECTION 9 — HOW TO PRESENT THIS IN AN INTERVIEW

**Open with the problem — make it financial:**
"A P1 incident that takes 18 minutes to diagnose instead of 3 minutes costs, on average, $45,000 in revenue for a mid-size SaaS company. PulseGrid reduces diagnosis time by correlating signals that exist in 6 different tools into one view."

**Show the risk score on a real PR:**
Create a test GitHub repository, open a PR that changes many files. Show the PulseGrid bot commenting with the risk score within 60 seconds. Walk through each contributing factor. Explain that the feature weights are learned from the organization's own incident history — this is not a generic rule, it is a model trained on their data.

**Show the dependency graph:**
Open the dashboard. Click on a service. Show the blast radius calculation update in real time. Explain: "This graph is built from live distributed traces — it reflects what services actually call each other right now, not a manually maintained document that went stale 3 months ago."

**Show the postmortem draft:**
Trigger a simulated incident in the demo environment. Resolve it. Within 5 minutes, show the auto-generated Confluence page with the timeline, root cause, and impact section filled in. "A postmortem that takes 3 hours to write now takes 20 minutes to review."

**Show the ADR for the graph database decision:**
Open `ADR/003-why-neo4j-not-relational.md`. Explain why a relational database cannot efficiently compute transitive dependencies (blast radius requires graph traversal, not SQL joins). This demonstrates that you understand the problem deeply enough to make technology decisions based on algorithmic requirements, not familiarity.

**The closing statement:**
"This system cannot be built by following a tutorial. It requires understanding distributed systems, stream processing, graph databases, machine learning pipelines, LLM integration, and GitHub's webhook architecture simultaneously. I built it because I wanted to understand how all of these connect — and because this problem exists in every engineering organization and nobody has solved it in open source."

---

# SECTION 10 — COMPARISON WITH INFRAMESH AND SENTINELGRID

| Dimension | InfraMesh (Derived) | PulseGrid (Original) | SentinelGrid (Original) |
|-----------|-------------------|---------------------|------------------------|
| Origin | Atlassian transcript | Original problem identification | Original problem identification |
| Domain | Platform engineering / infra provisioning | Engineering intelligence / SRE | Hardware + Edge AI / Industrial IoT |
| Core Innovation | Self-service infra automation | Cross-signal incident prediction + blast radius + AI postmortem | Dual edge-cloud AI + worker safety + federated learning |
| Physical Hardware | None | None | Yes — custom PCB |
| AI Component | Traffic anomaly detection | Risk classification + LLM postmortem | Predictive maintenance + fault classification |
| Graph Component | No | Yes — Neo4j dependency graph | No |
| Stream Processing | No (queue-worker) | Yes — Kafka/Kinesis real-time | No |
| Industry Target | Any tech company | Any engineering org with 20+ engineers | Manufacturing, industrial |
| Open Source Gap | Backstage exists (partial) | Nothing does all three together | Augury exists (expensive, proprietary) |
| Rarity | Medium | High | Very High |
| Recommended For | Software-only learner who wants infra depth | Software learner who wants to show intelligence + AI | Hardware-AI mix learner |

---

**PulseGrid is recommended as the replacement for InfraMesh.**
**It is original. It solves a documented real problem. No open tool does all three features. The technology stack is richer (Kafka, Neo4j, LLM integration, GitHub Apps). The domain is broader (every software engineering organization). The AI component is more sophisticated (trained on your data, not generic rules).**