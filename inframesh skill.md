# Atlassian Engineer — Complete Skills Extraction from Transcript
## Mapped to Timestamps | Grouped by Category | Ordered for Learning | Anchored to One Enterprise Project

---

# SECTION 0 — THE ENTERPRISE PROJECT ANCHOR

Before reading any skill below, understand this.

Every single skill you will learn is taught inside ONE real evolving system:

## Project Name: InfraMesh
## What It Is:
A cloud-native, self-service internal developer platform that allows any developer at a large company to:
- Register their microservice
- Automatically get load balancing, DNS, routing, and edge protection
- Provision infrastructure without contacting any infrastructure team
- Monitor the health of their service
- Get rate limiting, authentication, DDoS protection automatically
- See real-time observability dashboards

This is **exactly** what the Atlassian engineer built over 8 years.
Every skill listed below maps to a specific part of InfraMesh.
Every time you learn a skill, you will know exactly where it lives inside this system.

---

# SECTION 1 — COMPLETE SKILLS EXTRACTED WITH TIMESTAMPS

## GROUP A — Programming Languages

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 04:03 | Python | "I had confidence in building web apps with Python at that time and they accepted my level of confidence and decided to hire me" |
| 06:52 | Python + Connexion (OpenAPI framework) | "I chose to build this in Python using... a library called Connexion. This is a Python library which takes an open API document and then creates the API handlers" |
| 07:00 | Flask (Python web framework) | "...then I eventually migrated that to just pure Flask" |
| 07:22 | FastAPI (Python web framework) | "...and then eventually migrated that to FastAPI which I believe is what it still is at the moment" |
| 30:12 | Rust (systems programming language) | "The authentication sidecar was created by me, written of course in the Lord's language, Rust" |

---

## GROUP B — AWS Services

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 07:58 | DynamoDB (AWS NoSQL database) | "we have a database, which was DynamoDB" |
| 08:21 | SQS (AWS Simple Queue Service) | "It would drop the task details into SQS. And the worker would then handle that" |
| 08:41 | CloudFront (AWS CDN + DDoS) | "maybe creating a CloudFront distribution" / "DDoS protection was really provided by CloudFront" |
| 14:49 | CloudFormation (Infrastructure as Code) | "they are provisioned by a CloudFormation template. This is an AWS thing that allows you to essentially do infrastructure as code" |
| 15:29 | VPC (Virtual Private Cloud) | "we'd probably have like a VPC" |
| 15:36 | Subnets | "we'd have a subnet inside that VPC" |
| 15:47 | Internet Gateway, Security Groups, Key Pairs | Listed as CloudFormation building blocks |
| 15:47 | IAM (Identity and Access Management) | "maybe an IAM role... IAM role has to be attached to all these" |
| 15:54 | Auto Scaling Groups (ASG) | "of course we need to have the auto scaling group... that's what's going to be creating these EC2 instances" |
| 16:05 | AMI (Amazon Machine Images) | "the auto scaling group needs an AMI" |
| 16:48 | NLB (Network Load Balancer) | "we might have an NLB in here, a layer four proxy" |
| 16:54 | ACM (AWS Certificate Manager) | "a bit of ACM" |
| 17:06 | Route 53 (AWS DNS) | "we also had a little bit of Route 53 records" |
| 20:07 | EC2 (Elastic Compute Cloud) | Referenced throughout — virtual servers running the proxies |
| 28:19 | CloudFront (DDoS protection role) | "DDoS protection was really provided by CloudFront. That was spearheaded by a colleague of mine" |

---

## GROUP C — Infrastructure and DevOps Tools

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 17:43 | HashiCorp Packer | "we had a repository that was using HashiCorp Packer" — used to build AMIs |
| 17:50 | SaltStack (configuration management) | "we had a SaltStack configuration... very similar to Puppet, Ansible, and Chef" |
| 18:14 | SaltStack states/provisioning | "install packages, put files, run services on a machine in a particular way, in a particular order" |
| 18:28 | Declarative configuration | "automates that process, makes that process declarative for you" |

---

## GROUP D — Networking and Proxy Technologies

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 02:36 | Latency-based DNS / Route 53 | "I was asked something about how latency-based DNS works... Route 53 did a triangulation based on the actual latency of the client" |
| 02:52 | Geolocation-based routing | "they use a geolocation database in order to do latency-based routing of DNS requests" |
| 10:09 | Envoy Proxy | "the tech that we chose for that was Envoy proxy... very similar to something like Nginx, but perhaps more modern" |
| 10:26 | Load balancers (enterprise vs open-source) | "replace the enterprise load balancers at Atlassian which had licensing costs, with an open-source cloud-native commodity proxy" |
| 11:02 | Dynamic proxy configuration | "Envoy has an API that allows you to configure it dynamically. Being able to reload the configuration at run time" |
| 23:13 | Envoy routing configuration | "routes, virtual hosts... you can configure what domains to accept traffic on... do routing, direct responses, redirects" |
| 24:43 | Envoy clusters | "any route can send to any cluster... one thousand services each have their own cluster" |
| 28:50 | Network filters / HTTP Connection Manager | "we use these network filters... in the HCM, we have access logs" |
| 29:44 | Sidecar pattern (containers on proxy) | "we need to use a sidecar model where Envoy is talking out the side and then these are their own services running locally on the proxy" |

---

## GROUP E — Architecture Concepts and Patterns

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 02:01 | Microservices | "they asked me a few questions about things like microservices and architectural things like that" |
| 02:07 | Containers | "containers and whatnot" |
| 04:55 | Open Service Broker pattern | "build an open service broker. This is a web app with an API which facilitates the provisioning of resources for a platform" |
| 05:02 | Kubernetes concepts | "it's sort of built to operate in a Kubernetes world where you're submitting these provisioning requests as things come up and down" |
| 08:21 | Asynchronous provisioning (queue-worker pattern) | "The client would say 'please provision something for me.' And the web worker wouldn't do it itself. It would actually send that over SQS" |
| 09:03 | Polling pattern | "the client's polling continuously to say 'Is it ready? Is it ready?'" |
| 11:27 | Control plane pattern | "the Envoy management server that I built, which we called the Envoy control plane" |
| 12:15 | Template-driven configuration | "the app polls these... templates and context... putting it into the templates, and rendering out different content as the context changes" |
| 14:49 | Infrastructure as Code | "infrastructure as code... allows you to create resources in AWS that you would normally create via the console" |
| 16:05 | Immutable infrastructure / AMI pipeline | "Packer to create an EC2, configure with SaltStack, snapshot it, turn it into an image (AMI)" |
| 17:06 | Multi-region deployment | "~2000 proxies, something like 13 regions" |
| 20:55 | Centralized edge infrastructure | "centralized load balancing managed by our team and all of the features that we provided to our customers would live in logic defined in these templates" |
| 22:05 | Platform enforcement | "the platform was previously providing very basic load balancing... forced a switch to where you could no longer expose your service publicly through their load balancer" |
| 25:54 | Centralization of cross-cutting concerns | "deal with the problems here before they reach a service... deal with certain concerns here before it reaches here... save a lot of time, save some money" |
| 26:49 | Multi-tenancy | "a generic multi-tenanted platform" |
| 29:51 | Sidecar architecture | "sidecars... set up and downloaded and configured onto the AMI by this provisioning AMI provisioning flow" |

---

## GROUP F — Security Skills

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 27:17 | Authentication | "authentication... we can deal with them here instead of on a bazillion back-end services" |
| 27:22 | Authorization | "authorization" — handled at the edge layer |
| 27:23 | DDoS protection | "DDoS protection" — provided by CloudFront |
| 27:26 | Rate limiting | "rate limiting" — handled as a sidecar |
| 22:12 | Preventing accidental public exposure | "you could no longer expose your service publicly through their load balancer... required explicit centralized configuration" |
| 19:18 | Security hardening (AMI level) | "security slash hardening" listed as part of AMI configuration |
| 30:12 | Rust for auth sidecar | "The authentication sidecar was created by me, written in Rust" — chosen for memory safety and performance |

---

## GROUP G — Observability

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 19:07 | Logging agents | "logging agents" listed as part of AMI |
| 19:28 | Metrics | "metrics" — part of observability agent |
| 19:28 | Tracing | "tracing" — part of observability agent |
| 19:28 | Observability agent | "observability agent... can cover logging, tracing, metrics" |
| 32:57 | Log message interpretation | "knowing what particular log messages mean" |
| 33:05 | Metrics-based debugging | "what sort of metrics to check when something is going wrong and what those metrics could allude to" |
| 33:20 | Incident scenarios | "Amazon could have an outage and the database isn't accessible... what if SQS stops working" |
| 33:33 | Bad configuration detection | "What happens if a proxy receives bad configuration? What if it receives configuration that's valid but destroys the traffic?" |

---

## GROUP H — API Design and Architecture

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 05:42 | OpenAPI / Swagger specification | "the open API document here that has the endpoints" |
| 05:46 | REST API design (catalog, provision, bind) | "the catalog endpoint... lists all the services and plans available... put and patch for updating and deletes" |
| 06:01 | Service catalog pattern | "you might say query the service broker and display some of the metadata in your console" |
| 24:01 | Input validation | "making sure the parameters were validated such that when those parameters were run through the logic in these resources, that it would produce valid resources" |
| 29:24 | Dynamic configuration over the wire | "sidecars... can actually receive configuration, which is dynamic over the wire locally" |

---

## GROUP I — Data Storage and Flow

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 07:58 | DynamoDB (status storage) | "When it is completed, the worker writes it to the database... the web server checks the status" |
| 13:36 | Data pulled from multiple sources | "the context actually comes from this database, but we are requesting it from the broker and other sources... an S3 bucket with some data, and maybe that data is changing over time" |
| 13:48 | Template rendering with dynamic context | "we take that data, it's dynamic, we feed that into the templates. The templates have logic that spits out particular Envoy configuration" |

---

## GROUP J — Engineering Practices and Soft Skills

| Timestamp | Skill | What He Said |
|-----------|-------|--------------|
| 31:54 | Diplomacy and conflict resolution | "I have grown tremendously in my diplomacy skills, conflict avoidance, probably conflict resolution as well" |
| 32:02 | Persuasion and proposal | "being able to persuade, propose ideas" |
| 32:09 | Teaching and mentoring | "the ability to teach, educate, and mentor" |
| 32:17 | Software maintenance thinking | "the ability to maintain things, maintain software and systems, to see where the cracks show up" |
| 32:30 | Onboarding and documentation | "there's the requirement to onboard people and write documentation and train people" |
| 32:44 | Debugging knowledge transfer | "when they go on call, they know where to look, what could go wrong, where do things break" |
| 34:08 | Codebase churn recognition | "The area that churns, it sort of becomes predictable where all the churn is going to be... it is a smell" |
| 34:35 | Software entropy awareness | "Building something is easy. Changing it and making sure that you can still change it over time is difficult" |
| 35:19 | Software coupling awareness | "Things start to get coupled, and all of a sudden when you change something in one area, it affects another" |
| 36:00 | Working with different personalities | "I was exposed to different types of managers and colleagues over time... everyone has different personalities and styles of working" |
| 37:04 | Mentoring balance | "striking the balance between how much time I give to the mentee... I don't want to give them answers to problems, but I don't want them to get so stuck they become frustrated" |
| 39:22 | Complex topic simplification | "I could boil down hard topics into something that was understandable" |

---

# SECTION 2 — SKILLS ORGANIZED INTO LEARNING ORDER

Below is the dependency-correct sequence. You cannot learn skill 5 before skill 3. Every skill listed builds on the previous.

## PHASE 0 — FOUNDATIONS (Learn These Before Everything Else)

```
1.  Linux and Command Line        → Foundation of every server, every deploy
2.  Networking Basics             → DNS, HTTP, TCP/IP, load balancers — he interviewed on these at 02:36
3.  Git and Version Control       → Every file in InfraMesh lives here
4.  Python (Core Language)        → He built everything in Python — 04:03, 06:52, 07:00, 07:22
```

## PHASE 1 — BACKEND DEVELOPMENT

```
5.  REST API Design               → OpenAPI spec mentioned at 05:42 — foundation of Open Service Broker
6.  FastAPI (Python framework)    → Migration target at 07:22 — builds the InfraMesh API layer
7.  Data Validation (Pydantic)    → Mentioned at 24:01 — validating all developer inputs
8.  SQL and Relational Databases  → Foundation before DynamoDB
9.  DynamoDB (NoSQL)              → 07:58 — status storage for async provisioning
```

## PHASE 2 — ASYNCHRONOUS SYSTEMS

```
10. Asynchronous Programming      → Concepts behind the queue-worker pattern
11. Message Queues (SQS)          → 08:21 — core pattern of InfraMesh provisioning
12. Worker Pattern                → The processor that handles SQS messages
13. Polling Pattern               → 09:03 — client polling for completion status
```

## PHASE 3 — INFRASTRUCTURE

```
14. Cloud Computing Concepts      → Before touching any specific AWS service
15. AWS EC2                       → 20:07 — virtual servers running proxies
16. AWS IAM                       → 15:47 — permissions for everything
17. AWS VPC and Networking        → 15:29 — network isolation
18. AWS Route 53 (DNS)            → 17:06, 02:36 — latency-based routing, DNS records
19. AWS SQS                       → 08:21 — managed queue in production
20. AWS DynamoDB                  → 07:58 — managed NoSQL
21. AWS CloudFront                → 08:41, 28:19 — CDN and DDoS protection
22. AWS ACM                       → 16:54 — SSL/TLS certificates
23. AWS NLB                       → 16:48 — layer 4 load balancing
24. AWS Auto Scaling Groups       → 15:54 — scaling EC2 instances
25. AWS CloudFormation            → 14:49 — infrastructure as code, AWS native
```

## PHASE 4 — PROXY AND NETWORKING

```
26. Reverse Proxy Concepts        → Before Envoy
27. Load Balancing Concepts       → Theory behind what Envoy replaces
28. Envoy Proxy                   → 10:09 — the edge proxy of InfraMesh
29. Envoy Configuration           → 23:13 — routes, clusters, listeners, virtual hosts
30. Dynamic Configuration         → 11:02 — runtime config without restarts
31. Control Plane Pattern         → 11:27 — Envoy management server (Sovereign)
32. Template-Driven Config        → 12:15 — Jinja-style templates for Envoy config
```

## PHASE 5 — DEVOPS AND INFRASTRUCTURE AS CODE

```
33. Containers and Docker         → Foundation before Kubernetes mentions
34. Kubernetes Concepts           → 05:02 — mentioned as the world OSB operates in
35. HashiCorp Packer              → 17:43 — AMI pipeline tool
36. SaltStack (Config Management) → 17:50 — configuring EC2s (like Ansible/Puppet/Chef)
37. AMI Pipeline                  → 16:05 — immutable infrastructure concept
38. Terraform (IaC — modern)      → Modern equivalent of CloudFormation, 14:49
39. Multi-Region Deployment       → 17:06 — 13 regions, 2000 proxies
```

## PHASE 6 — SECURITY

```
40. Authentication Concepts       → 27:17 — handled at edge
41. Authorization Concepts        → 27:22 — handled at edge
42. DDoS Protection               → 27:23, 28:19 — CloudFront layer
43. Rate Limiting                 → 27:26 — sidecar pattern
44. Sidecar Architecture          → 29:44 — independent services alongside proxy
45. Rust Basics                   → 30:12 — auth sidecar language (advanced, not immediate)
46. Security Hardening            → 19:18 — AMI-level OS hardening
```

## PHASE 7 — OBSERVABILITY

```
47. Structured Logging            → 19:07, 32:57 — logging agents, readable logs
48. Metrics                       → 19:28, 33:05 — what to check when things fail
49. Distributed Tracing           → 19:28 — following a request across services
50. Observability Agent Setup     → 19:28 — bundled inside AMI
51. Incident Investigation        → 33:14, 33:20 — AWS outage, SQS failure, bad proxy config
52. Dashboard and Alerting        → Grafana/CloudWatch for InfraMesh dashboards
```

## PHASE 8 — ARCHITECTURE AND DESIGN THINKING

```
53. Microservices Architecture    → 02:01 — the world InfraMesh operates in
54. API Design (REST + OpenAPI)   → 05:42 — Open Service Broker spec
55. Centralized Edge Infrastructure → 25:54 — single choke point for auth, rate limit, DDoS
56. Multi-Tenancy                 → 26:49 — serving many teams from one platform
57. Platform Engineering          → 22:05 — enforcement, governance, self-service
58. Service Mesh Concepts         → Beyond Envoy proxy — Istio, Linkerd context
59. Software Entropy              → 34:35 — why maintenance is harder than building
60. Codebase Churn Recognition    → 34:08 — architectural smell detection
```

## PHASE 9 — ENGINEERING SOFT SKILLS

```
61. Technical Documentation       → 32:30 — onboarding docs, runbooks
62. Architecture Decision Records → Documenting why decisions were made
63. Debugging Knowledge Transfer  → 32:44 — teaching others where to look
64. On-Call Engineering           → 33:14 — what to check, what to do when AWS fails
65. Mentoring                     → 37:04 — guiding without giving answers
66. Conflict Resolution           → 31:54, 36:00 — different personalities, different opinions
67. Technical Communication       → 39:22 — explaining hard topics simply
68. Software Changeability Thinking → 35:19 — coupling, cohesion, maintainability
```

---

# SECTION 3 — MASTER SKILL MAP: WHERE EACH SKILL LIVES IN INFRAMESH

```
InfraMesh Architecture (High Level)
─────────────────────────────────────────────────────────────────────
DEVELOPER
    │
    ▼
[ InfraMesh API — FastAPI + Python ]        ← Skills 4,5,6,7
    │               │
    │               ▼
    │         [ SQS Queue ]                  ← Skills 11,12,13
    │               │
    │               ▼
    │         [ Python Worker ]              ← Skills 4,10,11
    │               │
    ├───────────────┘
    ▼
[ DynamoDB / PostgreSQL ]                   ← Skills 8,9
    │
    ▼
[ Envoy Control Plane (Sovereign) ]         ← Skills 30,31,32
    │
    ▼
[ Envoy Proxy Fleet ]                       ← Skills 26,27,28,29
    │              │
    │     ┌────────┴────────────┐
    ▼     ▼                     ▼
[ Auth  [ Rate Limit   [ DDoS (CloudFront) ]
 Sidecar] Sidecar ]                          ← Skills 40-46
    │
    ▼
[ Backend Microservices ]                   ← Skill 53 (the things being protected)

INFRA LAYER
─────────────────────────────────────────────────────────────────────
[ CloudFormation / Terraform ]              ← Skills 25,38
[ VPC + Subnets + Security Groups + IAM ]   ← Skills 16,17
[ EC2 + Auto Scaling Groups ]               ← Skills 15,24
[ AMI Pipeline — Packer + SaltStack ]       ← Skills 35,36,37
[ Multi-Region (13 regions) ]               ← Skill 39
[ Route 53 (DNS) ]                          ← Skill 18

OBSERVABILITY LAYER
─────────────────────────────────────────────────────────────────────
[ Logging Agents + Metrics + Tracing ]      ← Skills 47,48,49,50
[ CloudWatch + Grafana Dashboards ]         ← Skill 52
[ Incident Runbooks ]                       ← Skill 64
```

---

# SECTION 4 — THE TIMESTAMP-TO-INFRAMESH MAP

This table tells you: when the speaker said something, what component of InfraMesh it is, and what you will build.

| Timestamp | What He Said | InfraMesh Component | What You Build |
|-----------|-------------|---------------------|----------------|
| 01:32 | HackerRank test — coding | - | Your LeetCode/HackerRank baseline |
| 01:39 | White paper on Cloudflare custom domains | DNS + routing concepts | Understanding how custom domains work |
| 02:01 | Microservices, containers, architecture interview | Architecture knowledge | Your system design vocabulary |
| 02:36 | Latency-based DNS, Route 53 | Route 53 in InfraMesh | DNS routing layer |
| 04:03 | Python confidence → got hired | All Python components | Every backend piece |
| 04:55 | Open Service Broker | InfraMesh API | Self-service provisioning API |
| 05:02 | Kubernetes world | Container orchestration | Where InfraMesh runs |
| 06:52 | Connexion → OpenAPI | API design | InfraMesh API specification |
| 07:00 | Flask | API framework | Intermediate API layer |
| 07:22 | FastAPI | API framework | Production InfraMesh API |
| 07:58 | DynamoDB | Status database | Provisioning status storage |
| 08:21 | SQS + worker | Async queue | InfraMesh task queue |
| 08:35 | DNS records, CloudFront, API configs | Provisioning tasks | What the worker provisions |
| 09:03 | Client polling | Polling pattern | Client-side status checking |
| 10:09 | Envoy Proxy | Edge proxy fleet | 2000 proxies across 13 regions |
| 10:26 | Replace enterprise load balancers | Load balancing | Cost reduction + flexibility |
| 11:02 | Dynamic Envoy config API | Dynamic config | No-restart config updates |
| 11:27 | Envoy control plane (Sovereign) | Control plane | Config management server |
| 12:15 | Templates + context | Template engine | Jinja-style config rendering |
| 13:36 | S3 + broker as context sources | Data sources | Context for template rendering |
| 14:49 | CloudFormation | IaC | All AWS resources as code |
| 15:29 | VPC | Networking | Isolated network for proxies |
| 15:47 | Security groups, IAM | Security | Least-privilege access |
| 15:54 | Auto Scaling Groups | Scaling | Elastic proxy fleet |
| 16:05 | AMIs | Immutable infra | Standard proxy image |
| 16:48 | NLB | Layer 4 proxy | Traffic entry point |
| 16:54 | ACM | SSL/TLS | Certificate management |
| 17:06 | Route 53 | DNS | Routing to proxy fleet |
| 17:43 | HashiCorp Packer | AMI pipeline | Automated image building |
| 17:50 | SaltStack | Config management | EC2 configuration automation |
| 19:07 | Logging agents | Observability | Centralized log collection |
| 19:28 | Metrics + tracing | Observability | Performance monitoring |
| 22:32 | Jira, Confluence, Bitbucket, Statuspage migration | Migration | Onboarding products to InfraMesh |
| 25:54 | Centralized concerns (auth, DDoS, rate limit) | Edge layer | Cross-cutting concern handling |
| 27:17 | Authentication at edge | Auth sidecar | Per-request auth |
| 27:22 | Authorization | Authz sidecar | Permission checking |
| 27:23 | DDoS | CloudFront layer | Attack protection |
| 27:26 | Rate limiting | Rate limit sidecar | Quota enforcement |
| 28:50 | Network filters, HCM, access logs | Envoy filters | Traffic introspection |
| 29:44 | Sidecar model | Sidecar pattern | Modular security components |
| 30:12 | Rust auth sidecar | Auth sidecar | High-performance auth |
| 31:54 | Diplomacy | Soft skill | Working with platform customers |
| 32:17 | Software maintenance | Engineering thinking | Long-term system health |
| 32:30 | Documentation, onboarding | Runbooks | On-call knowledge transfer |
| 33:14 | AWS outage, SQS failure, bad proxy config | Incident response | Production failure playbooks |
| 34:08 | Codebase churn | Architectural smell | Refactoring signals |
| 34:35 | Building is easy, maintaining is hard | Maintenance thinking | The real challenge of software |

---

# SECTION 5 — HOW EACH SKILL WILL BE TAUGHT (10-PART FRAMEWORK)

For each skill in the roadmap, the following structure will be used:

```
PART 1 — WHAT THIS THING ACTUALLY IS
  - What it is, why it exists, what problem it solves
  - Beginner / Intermediate / Enterprise view

PART 2 — WHAT YOU WILL LEARN
  - Concepts, subtopics, syntax, mechanisms
  - Mental models and engineering thinking

PART 3 — WHAT YOU WILL BE CAPABLE OF AFTER
  - Beginner capability → Intermediate → Professional
  - Real tasks that become possible

PART 4 — HOW THIS CONNECTS TO OTHER TECHNOLOGIES
  - Dependency chain: what comes before, what comes after
  - Data flow, request flow, architecture flow
  - Connections to backend, cloud, DevOps, security, monitoring

PART 5 — HOW THIS IS USED IN A REAL MNC
  - Real enterprise use case
  - Scale problems, debugging challenges, security concerns
  - Beginner mistakes vs. senior engineer thinking

PART 6 — REAL-WORLD PROJECT INTEGRATION (InfraMesh)
  - Exactly where this skill lives in InfraMesh
  - What data flows through it
  - What connects to it
  - What happens if it fails
  - How engineers debug it

PART 7 — DEBUGGING THINKING
  - Common bugs, architecture mistakes, scaling failures
  - Logs, monitoring, root cause analysis
  - Real production issue examples

PART 8 — DOCUMENTATION + PORTFOLIO + PROOF
  - How to document learning professionally
  - GitHub proof to maintain
  - What recruiters trust more
  - What makes a portfolio look real vs. fake

PART 9 — BEST WEBSITES AND TOOLS
  - Learning sites, debugging sites, practice platforms
  - Architecture tools, documentation tools, monitoring tools

PART 10 — ACTIVE RECALL + ENGINEERING INTERVIEW THINKING
  - Architecture questions
  - Debugging questions
  - "What if this fails?" questions
  - Scaling and integration questions
```

---

# SECTION 6 — TEACHING SEQUENCE WITH INFRAMESH INTEGRATION

Here is the exact order in which each skill should be learned, and what part of InfraMesh you will be building as you learn it.

```
PHASE 0 (Weeks 1–3): Foundations
─────────────────────────────────────────────────────
Skill 1:  Linux + Command Line
          → You will SSH into the InfraMesh EC2 instances
          → You will read proxy logs from the terminal
          → You will deploy code using shell scripts

Skill 2:  Networking (DNS, HTTP, TCP/IP, Load Balancers)
          → You will understand how the NLB → Envoy → Backend flow works
          → You will understand latency-based DNS (02:36 timestamp)
          → You will understand what a load balancer actually does

Skill 3:  Git and GitHub
          → Every InfraMesh file lives here
          → Terraform, Python code, SaltStack config, Dockerfiles

Skill 4:  Python Core
          → Foundation of ALL InfraMesh logic
          → API, worker, control plane, automation scripts

PHASE 1 (Weeks 4–7): Backend Development
─────────────────────────────────────────────────────
Skill 5:  REST API Design + OpenAPI
          → InfraMesh API specification (05:42)
          → The service broker catalog, provision, bind endpoints

Skill 6:  FastAPI
          → InfraMesh API server (07:22)
          → Developers call this to register services

Skill 7:  Data Validation + Pydantic
          → Validates all developer inputs before provisioning (24:01)

Skill 8:  SQL + PostgreSQL
          → Foundation before DynamoDB

Skill 9:  DynamoDB
          → Stores provisioning status (07:58)
          → Stores registered service state

PHASE 2 (Weeks 8–10): Async Systems
─────────────────────────────────────────────────────
Skill 10: Async Programming Concepts
Skill 11: SQS (Message Queues)
          → The core of InfraMesh provisioning (08:21)
Skill 12: Python Worker
          → Reads from SQS and provisions resources
Skill 13: Polling Pattern
          → Client checks if provisioning is done (09:03)

PHASE 3 (Weeks 11–16): AWS Cloud
─────────────────────────────────────────────────────
Skills 14–25: AWS services in order
          → Build InfraMesh's production infrastructure

PHASE 4 (Weeks 17–22): Proxy + Networking
─────────────────────────────────────────────────────
Skills 26–32: Envoy, dynamic config, control plane
          → Build the proxy fleet that serves Jira, Confluence, Bitbucket

PHASE 5 (Weeks 23–27): DevOps + IaC
─────────────────────────────────────────────────────
Skills 33–39: Docker, Packer, SaltStack, Terraform, AMI pipeline
          → Automate the creation of 2000 proxies across 13 regions

PHASE 6 (Weeks 28–32): Security
─────────────────────────────────────────────────────
Skills 40–46: Auth, authz, DDoS, rate limiting, sidecars
          → Protect every service behind InfraMesh

PHASE 7 (Weeks 33–36): Observability
─────────────────────────────────────────────────────
Skills 47–52: Logging, metrics, tracing, dashboards, incidents
          → See inside InfraMesh when it breaks at 3 AM

PHASE 8 (Weeks 37–42): Architecture Thinking
─────────────────────────────────────────────────────
Skills 53–60: Microservices, platform engineering, entropy
          → Understand WHY InfraMesh is designed the way it is

PHASE 9 (Ongoing): Soft Skills + Engineering Culture
─────────────────────────────────────────────────────
Skills 61–68: Documentation, mentoring, conflict, communication
          → Operate InfraMesh inside a real company with real people
```

---

# SECTION 7 — DOCUMENTATION AND PROOF MASTER PLAN

## GitHub Repository Structure for InfraMesh (Your Portfolio)

```
inframesh/
│
├── README.md                   → Project overview, architecture diagram, demo GIF
├── ARCHITECTURE.md             → System design decisions, why each component exists
├── API.md                      → All endpoints, request/response, Swagger link
├── DATABASE.md                 → Schema, indexes, query design decisions
├── INFRASTRUCTURE.md           → AWS resources, networking, security groups
├── TERRAFORM.md                → IaC decisions, how to apply, what it creates
├── ENVOY.md                    → Proxy architecture, how templates work, dynamic config
├── OBSERVABILITY.md            → Logging strategy, metrics, alert rules
├── RUNBOOK.md                  → On-call guide: what to do when things break
├── SECURITY.md                 → Auth, authz, rate limiting, DDoS design
├── SIDECAR.md                  → Sidecar pattern, what each sidecar does
├── ONBOARDING.md               → How a new team member understands the system
├── ADR/                        → Architecture Decision Records
│   ├── 001-why-fastapi.md
│   ├── 002-why-sqs-not-direct.md
│   ├── 003-why-envoy-not-nginx.md
│   ├── 004-why-sidecar-for-auth.md
│   └── 005-why-rust-for-auth.md
│
├── api/                        → FastAPI Python application
├── worker/                     → SQS consumer worker
├── control-plane/              → Envoy control plane (Sovereign equivalent)
├── infrastructure/             → Terraform files
│   ├── vpc.tf
│   ├── ec2.tf
│   ├── sqs.tf
│   ├── dynamodb.tf
│   ├── cloudfront.tf
│   └── iam.tf
├── packer/                     → HashiCorp Packer AMI pipeline
├── saltstack/                  → SaltStack configuration states
├── envoy/                      → Envoy config templates
├── sidecars/
│   ├── auth/                   → Rust auth sidecar
│   ├── rate-limit/             → Rate limiting sidecar
│   └── authz/                  → Authorization sidecar
├── observability/              → Grafana dashboards, Prometheus config
└── docker-compose.yml          → Local full-stack development
```

## Non-Fabricatable Proof Per Skill

| Skill | Proof That Cannot Be Faked |
|-------|---------------------------|
| Linux | OverTheWire Bandit levels 0–34 (sequential passwords prove completion) |
| Python | HackerRank Python certificate (public URL + verifiable) + Exercism profile |
| FastAPI | Live Swagger UI on deployed InfraMesh — anyone can test your API |
| Git | GitHub commit history timestamps — shows when you built each piece |
| SQL | HackerRank SQL certificate |
| AWS | AWS Certified Cloud Practitioner (Credly badge, globally verifiable) |
| Terraform | HashiCorp Terraform Associate (Credly badge) + IaC code in GitHub |
| Docker | Docker Hub repository with pushed images |
| Envoy | Working InfraMesh demo where proxy routes traffic dynamically |
| Observability | Live Grafana Cloud dashboard URL with real data |
| System Design | Written ADR documents in GitHub — quality of reasoning is the proof |
| Full System | **InfraMesh deployed on AWS with a real URL** — no tutorial produces this |

---

# SECTION 8 — ACTIVE RECALL BEFORE YOU START

Answer these honestly. These are not quiz questions. They are engineering thinking questions.

1. The speaker says he got hired because of "confidence and ability to learn unfamiliar systems quickly." What does that mean for how you should approach each skill — as a thing to memorize or as a system to understand?

2. At timestamp 34:35 he says "Building something is easy. Changing it and making sure you can still change it over time is difficult." Before you write a single line of code for InfraMesh — how will you write code that is easy to change six months later?

3. At timestamp 08:21, the provisioning request goes into a queue instead of being processed immediately. Why? What would break if the API processed it directly instead of queuing it?

4. He built 2000 proxies across 13 AWS regions using CloudFormation (14:49). Why not just click in the AWS console? What breaks at scale with manual clicking?

5. At timestamp 22:12, the platform *forced* services to use centralized load balancing — it was not optional. Why would a company force this? What security problem does it solve?

6. At timestamp 34:08 he identifies "churn" in a codebase as a smell. What does that mean? If you come back to InfraMesh 6 months after building it and a certain file has been changed 40 times while everything else was touched twice — what does that tell you about the design?

7. The auth sidecar was written in Rust (30:12) not Python. Why would you write one component in a completely different language? What does that tell you about choosing tools?

8. He says at 33:14 that engineers need to know: what to check when SQS stops working, what to check when a proxy gets bad config, what to check when AWS has an outage. Before learning the tools — what does it mean that these are the questions you need to be able to answer ON CALL at 3 AM?

---

**This document is your master reference. Every time you learn a new skill, come back here, find where it sits in InfraMesh, and understand its connections before writing a single line of code.**

**Start with Skill 1: Linux and Command Line.**
**Every reply request should be: "Teach me Skill [N]: [Name] using the 10-part framework."**