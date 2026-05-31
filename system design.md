
# 🏗️ System Design Mastery Roadmap
### From Absolute Zero → Principal Engineer (L6/L7) at an MNC
#### *Day-by-Day. Topic-by-Topic. Project-by-Project.*
##### *If you don't know what a server is, what a network packet is, or what "scale" means — start here.*

---

> **Who This Is For:** Someone starting with zero programming knowledge, zero networking knowledge, zero database experience, and zero system design exposure — but who wants to reach the level of a Principal/Staff Engineer at Google, Amazon, Meta, Uber, or Netflix within 110 days.
>
> **The Core Promise:** Every day connects to the next. Every project is real and buildable. Every concept is explained with the question "WHY does this exist?" before "HOW does it work?" By Day 110, you will be able to walk into any system design interview and design Twitter, YouTube, Uber, or Discord from scratch — and explain every decision.
>
> **Documentation First:** This roadmap treats documentation as the primary deliverable. Code proves you can build. Documentation proves you can think.

---

## 📐 SECTION 0: THE MASTER ARCHITECTURE — Read Before Day 1

### 🗺️ The 110-Day Learning Universe

```
╔═══════════════════════════════════════════════════════════════════════════════╗
║              YOUR 110-DAY SYSTEM DESIGN MASTERY MAP                          ║
╠═══════════════════════════════════════════════════════════════════════════════╣
║                                                                               ║
║  PHASE 1 (Days 1–14):   THE PHYSICS OF SOFTWARE                               ║
║  ┌─────────────────────────────────────────────────────────────────────────┐  ║
║  │ OSI Model · TCP/IP · UDP/QUIC · DNS · HTTP Evolution · APIs             │  ║
║  │ OS: Processes · Threads · I/O Models · Memory · Storage · Containers    │  ║
║  │ Load Balancers · Reverse Proxies · Traffic Distribution                 │  ║
║  └─────────────────────────────────────────────────────────────────────────┘  ║
║             ↓ PROJECT 1: Layer 7 Load Balancer (Days 13–14)                  ║
║                                   ↓                                          ║
║  PHASE 2 (Days 15–30):  DISTRIBUTED SYSTEMS THEORY                           ║
║  ┌─────────────────────────────────────────────────────────────────────────┐  ║
║  │ CAP Theorem · Consistency Models · Time & Clocks · Raft Consensus       │  ║
║  │ 2PC & Sagas · Replication · Sharding · Consistent Hashing · IDs        │  ║
║  │ Caching Deep Dive · Redis · CDNs · Bloom Filters · HyperLogLog          │  ║
║  └─────────────────────────────────────────────────────────────────────────┘  ║
║         ↓ PROJECT 2: Distributed Key-Value Store (Days 23–25)                ║
║                                   ↓                                          ║
║  PHASE 3 (Days 31–50):  MNC COMPONENT DEEP DIVE                              ║
║  ┌─────────────────────────────────────────────────────────────────────────┐  ║
║  │ DB Internals: B-Trees vs LSM Trees · MVCC · Postgres · Cassandra        │  ║
║  │ Kafka Architecture · Event Sourcing · CQRS · Message Semantics          │  ║
║  │ Microservices · API Gateways · Service Mesh · Circuit Breakers          │  ║
║  └─────────────────────────────────────────────────────────────────────────┘  ║
║    ↓ PROJECT 3: Build Your Own Redis (Days 33–40) + Mini-Kafka (Days 46–50)  ║
║                                   ↓                                          ║
║  PHASE 4 (Days 51–70):  PRODUCTION SYSTEM DESIGN                             ║
║  ┌─────────────────────────────────────────────────────────────────────────┐  ║
║  │ Observability: Metrics · Logs · Tracing · SLOs/SLAs/SLIs               │  ║
║  │ Rate Limiting Algorithms · Resilience Patterns · Capacity Planning      │  ║
║  │ Design: URL Shortener · Web Crawler · Chat App · Video Streaming        │  ║
║  └─────────────────────────────────────────────────────────────────────────┘  ║
║           ↓ PROJECT 4: Intelligent URL Shortener (Days 60–65)                ║
║                                   ↓                                          ║
║  PHASE 5 (Days 71–90):  AI-NATIVE SYSTEM DESIGN                              ║
║  ┌─────────────────────────────────────────────────────────────────────────┐  ║
║  │ RAG Architecture · Vector Databases · HNSW Indexing · Embeddings        │  ║
║  │ LLM Inference Ops · Semantic Caching · AI Guardrails · LLMOps           │  ║
║  │ Agentic Workflows · ReAct Pattern · Multi-Agent Systems · Tools         │  ║
║  └─────────────────────────────────────────────────────────────────────────┘  ║
║          ↓ PROJECT 5: AI-Powered Chat System (Days 80–90)                    ║
║                                   ↓                                          ║
║  PHASE 6 (Days 91–110):  PORTFOLIO + INTERVIEW MASTERY                       ║
║  ┌─────────────────────────────────────────────────────────────────────────┐  ║
║  │ Green Computing · Carbon-Aware Systems · MNC Case Studies               │  ║
║  │ Full Mock Interviews · Architecture Documentation · Portfolio Polish     │  ║
║  └─────────────────────────────────────────────────────────────────────────┘  ║
║         ↓ CAPSTONE: Anomaly-Detection Rate Limiter + AI Gateway (Days 96–110)║
╚═══════════════════════════════════════════════════════════════════════════════╝
```

---

### 🧠 Why This Order? The Honest Explanation

You cannot design a distributed system without first understanding what a single computer does. You cannot understand distributed databases without first understanding what a single database does. This roadmap builds knowledge in layers — like a city:

| Phase | What You're Building | Why This Phase Comes Here |
|---|---|---|
| Phase 1 (Networking + OS) | The roads and electricity | Without networking, there is no "distributed." Without OS understanding, you can't reason about performance |
| Phase 2 (Distributed Theory) | City planning laws | The mathematical constraints that govern ALL distributed systems |
| Phase 3 (MNC Components) | The actual buildings | The specific tools (Kafka, Redis, Postgres) that MNCs use |
| Phase 4 (System Design) | City blueprints | Putting all components together into real systems |
| Phase 5 (AI-Native Design) | Smart city automation | The 2025 layer that every MNC is adding to their stack |
| Phase 6 (Portfolio) | Your property portfolio | Proving ownership of everything you built |

---

## 🛠️ TECH STACK — MNC Grade, 100% Free and Open Source

| Category | Tool | Why This Specifically | Cost |
|---|---|---|---|
| **Primary Language** | Python 3.12 + Go 1.22 | Python for prototyping; Go for performance-critical implementations. Both used at Google/Uber | Free |
| **Networking Analysis** | Wireshark + tcpdump | The actual tools network engineers use in production. Non-negotiable. | Free |
| **Database: SQL** | PostgreSQL 16 | Gold standard relational DB. Used at Instagram, Uber, Notion. | Free |
| **Database: Wide Column** | Cassandra + ScyllaDB | Discord uses this for trillions of messages. LSM tree internals. | Free |
| **Cache** | Redis 7 | Industry standard. You will also BUILD your own. | Free |
| **Message Queue/Stream** | Apache Kafka | LinkedIn, Uber, Airbnb. The event streaming standard. | Free |
| **Container** | Docker + Kubernetes (minikube) | Every MNC deploys this way. | Free |
| **CI/CD** | GitHub Actions | Standard. Runs your tests and deployments automatically. | Free |
| **Observability** | Prometheus + Grafana + Jaeger | The three pillars of observability. Used at SoundCloud, Uber. | Free |
| **Load Balancer** | NGINX (study + configure) | You will also BUILD your own. | Free |
| **Vector Database** | Qdrant + pgvector | Open-source vector search. Used for RAG systems. | Free |
| **Local LLM** | Ollama (llama3/mistral) | Run AI locally. No API costs. | Free |
| **Diagram Tool** | Excalidraw (browser) | What engineers use in actual system design interviews. | Free |
| **Protocol Tool** | grpcurl + Postman | Test gRPC and REST APIs. | Free |
| **Version Control** | Git + GitHub | Non-negotiable. Everything goes here. | Free |
| **Documentation** | Markdown + GitHub Pages | Your portfolio's home. | Free |
| **Blog** | Hashnode + Dev.to | Technical writing. Recruiters find these via Google. | Free |

---

## 📝 THE DOCUMENTATION SYSTEM — Your Daily Proof-of-Work

### Why Documentation Is Your Primary Deliverable

A Principal Engineer is not someone who writes the most code. They are someone who can explain the most clearly why a system was built the way it was. Your documentation proves two things simultaneously: (1) you built it, and (2) you understood it.

### Platform Strategy

**GitHub (`system-design-mastery/`)** — Primary code and notes repository. Every engineer who evaluates you will go here first.

**Excalidraw exports** — Save every architecture diagram as PNG and commit to `system-design-mastery/designs/`. This is the artifact that proves you can think architecturally.

**Hashnode/Dev.to** — One blog post per week. These appear in Google search results. A blog post titled "I Implemented Raft Consensus From Scratch — Here's Every Mistake I Made" will be found by recruiters and engineers.

**Postman Public Collections** — For every API you build, make a public Postman collection. Any engineer can verify your API actually works.

**YouTube (Unlisted)** — For milestone projects, record a 3-5 minute walkthrough. This is the most powerful proof-of-work format: it shows the system working live.

### GitHub Repository Structure
```
system-design-mastery/
├── README.md                        ← Portfolio landing page
├── phase-1-physics/
│   ├── networking/                  ← Notes, experiments
│   ├── os-internals/
│   └── load-balancing/
├── phase-2-distributed/
│   ├── cap-theorem/
│   ├── consensus/
│   ├── sharding/
│   └── caching/
├── phase-3-components/
│   ├── db-internals/
│   ├── kafka-deep-dive/
│   └── microservices/
├── phase-4-system-design/
│   ├── url-shortener/
│   ├── web-crawler/
│   ├── chat-app/
│   └── video-streaming/
├── phase-5-ai-systems/
│   ├── rag-architecture/
│   ├── vector-search/
│   └── agents/
├── phase-6-portfolio/
│   └── mock-interviews/
├── projects/
│   ├── 01-layer7-load-balancer/
│   ├── 02-distributed-kv-store/
│   ├── 03-build-your-own-redis/
│   ├── 04-mini-kafka/
│   ├── 05-intelligent-url-shortener/
│   ├── 06-ai-chat-system/
│   └── 07-anomaly-rate-limiter/
├── designs/                         ← All Excalidraw PNGs
│   ├── twitter-design.png
│   ├── youtube-design.png
│   ├── uber-design.png
│   └── discord-design.png
└── adrs/                            ← Architecture Decision Records
    ├── adr-001-choosing-kafka.md
    ├── adr-002-consistent-hashing.md
    └── adr-003-lsm-vs-btree.md
```

### Daily Documentation Template
```markdown
# Day XX — [Topic Name]

## 🎯 Today's Learning Goal
[One sentence: what you're setting out to understand]

## 🧠 The Core Concept (Explain It Like You're Teaching)
[Write as if explaining to someone who has never heard of this.
 This is your primary understanding test. If you can't write this,
 you need to study more.]

## 🔧 What I Built or Experimented With
[Command output / code snippet / diagram]

## 🔗 The Connection Chain
Yesterday I learned [X] → Today [X] enables [Y] → Tomorrow [Y] leads to [Z]

## 🏭 Where This Lives at MNC Scale
[What does Google/Uber/Discord actually use this for?]

## ⚖️ The Tradeoff (Every Design Decision Has One)
[What does this approach gain? What does it sacrifice?]

## ❌ The Beginner Mistake
[What would someone who doesn't understand this deeply get wrong?]

## ❓ Active Recall (Answer From Memory Tomorrow)
1. 
2. 
3. 

## 📊 Evidence
[Link to GitHub commit / screenshot / diagram]
```

### Weekly Architecture Decision Record (ADR)
Every Sunday, write one ADR for a design decision you made that week:
```markdown
# ADR-XX: [Decision]
**Date:** [Date] | **Status:** Accepted

## Context — The Problem
[What situation required a decision?]

## The Decision
[What you chose to do]

## Why Not the Alternatives?
[Option A: Rejected because X. Option B: Rejected because Y.]

## Consequences
[What tradeoffs does this choice introduce?]

## How This Changes at 100x Scale
[What would you do differently if you had 100x more traffic?]
```

---

---

# 📅 THE COMPLETE DAY-BY-DAY TIMETABLE

## Daily Schedule Structure
```
EACH DAY (3–4 hours total):
  ├── 0:00–0:30  Review yesterday's active recall questions
  ├── 0:30–1:30  Study the day's core concept (reading + video)
  ├── 1:30–3:00  Practical task / experiment / code
  └── 3:00–3:30  Write daily documentation (fill the template)
```

---

---

# 🔵 PHASE 1: THE PHYSICS OF SOFTWARE (Days 1–14)

> **Goal:** Master the fundamental medium (network) and environment (operating system) before distributing anything. Every distributed system is just a collection of computers talking over a network. If you don't understand the network or the computer, you cannot reason about the system.
>
> **The Connecting Thread:** Each day's concept is a prerequisite for the next. OSI → TCP → HTTP → APIs → Processes → I/O → Storage → Containers → Load Balancers → Project.

---

## DAY 1: The OSI Model — The Blueprint of All Networks

### What You're Learning and Why
The OSI model is the language that ALL network engineers use to diagnose problems. When a connection fails in production, the first question is always "at which layer?" Understanding this tells you whether the problem is physical (Layer 1), IP routing (Layer 3), or application-level (Layer 7).

### Core Concepts

```
THE 7 LAYERS OF THE OSI MODEL (With Real-World Meaning)

Layer 7: APPLICATION    HTTP, HTTPS, DNS, gRPC, WebSocket
         "The language your application speaks"
         TOOLS THAT WORK HERE: NGINX (L7 load balancer), API Gateways

Layer 6: PRESENTATION   TLS/SSL encryption, compression, encoding
         "Make data readable and secure"
         IMPORTANT: TLS termination happens here. SSL certificates live here.

Layer 5: SESSION        Managing connection state
         "Maintain the conversation"
         Less commonly discussed but present in WebSocket sessions

Layer 4: TRANSPORT      TCP (reliable) vs UDP (fast)
         "Delivery guarantee mechanism"
         PORT NUMBERS live here. TCP port 443, 80, 5432, 6379.
         TOOLS: L4 load balancers (HAProxy in TCP mode)

Layer 3: NETWORK        IP Addressing, Routing
         "Which computer?"
         IP addresses live here. Routers work here.
         TOOLS: IP tables, VPNs, BGP routing

Layer 2: DATA LINK      MAC Addresses, Ethernet, Wi-Fi
         "Which network interface on that computer?"
         ARP (Address Resolution Protocol) bridges L3 and L2.

Layer 1: PHYSICAL       Electrical signals, fiber optic light, radio waves
         "The actual wire or air"

CRITICAL INSIGHT FOR SYSTEM DESIGN:
Most load balancers you'll design operate at L4 or L7.
L4: Fast (just looks at IP + port), can't read HTTP content
L7: Slower (reads HTTP headers), can route by URL path or hostname
```

### Practical Task (Day 1)

```bash
# Install Wireshark (GUI) or use tcpdump (terminal)
sudo apt install wireshark tcpdump

# Capture HTTP traffic to see OSI layers in real packets
sudo tcpdump -i lo -n -vvv 'port 8080' &

# In another terminal, start a simple web server
python3 -m http.server 8080 &

# Send a request and watch the packet dump
curl http://localhost:8080/

# YOU WILL SEE:
# IP header (Layer 3): source IP, destination IP
# TCP header (Layer 4): source port, destination port, sequence numbers
# HTTP data (Layer 7): GET / HTTP/1.1, headers

# For Wireshark: open GUI, select loopback interface, filter: tcp.port==8080
# Right-click a packet → "Follow TCP Stream" to see the full HTTP conversation
```

### Architecture Reasoning Task
Draw (in text or Excalidraw) the journey of a single HTTP request from your browser to google.com, labeling which OSI layer handles each step.

### Beginner Mistake
Treating the OSI model as abstract academic theory. It is a practical diagnostic tool. When you can't connect to a database, you ask: "Is port 5432 open?" (Layer 4). "Can the server resolve the hostname?" (Layer 7/3). "Is there an IP route?" (Layer 3).

### ✅ Active Recall (Answer Tomorrow Without Looking)
1. A user cannot reach your web application. What Layer 4 tool would you use to check if the port is open?
2. Why does a Layer 7 load balancer require more CPU than a Layer 4 load balancer?
3. Where does TLS encryption/decryption happen in the OSI model?

### 📝 Documentation Task
Commit `phase-1-physics/networking/day-01-osi.md` with the output of your tcpdump capture and your explanation of what each section means.

---

## DAY 2: TCP Deep Dive — Reliability at a Cost

### What You're Learning and Why
Every database connection, every API call, every microservice communication uses TCP. If you don't understand TCP, you can't understand connection pools, timeouts, or why QUIC (HTTP/3) exists.

### Core Concepts

```
THE TCP THREE-WAY HANDSHAKE:

Client                           Server
  │                                │
  │──── SYN (seq=1000) ──────────►│   "I want to connect, my seq is 1000"
  │                                │
  │◄─── SYN-ACK (seq=5000,        │   "OK, my seq is 5000, I acknowledge yours"
  │         ack=1001) ────────────│
  │                                │
  │──── ACK (ack=5001) ──────────►│   "Acknowledged. Connection open."
  │                                │
  │◄──────── DATA ────────────────►│   (actual communication)
  │                                │
  │──── FIN ─────────────────────►│   "I'm done, closing"

COST OF THE HANDSHAKE:
  Each handshake = ~1-2 RTT (Round Trip Time)
  At 50ms RTT: 2 × 50ms = 100ms before any data transfers
  
  WHY THIS MATTERS FOR SYSTEM DESIGN:
  - A naive app opens a new TCP connection for every database query
  - At 1000 queries/second: 1000 × 100ms overhead = system is unusable
  - Solution: CONNECTION POOLING (keep connections open and reuse them)
  - This is why PgBouncer, HikariCP, and Redis connection pools exist

TCP FLOW CONTROL (Sliding Window):
  - Receiver tells sender: "I have X bytes of buffer space"
  - Sender can only send X bytes before waiting for ACK
  - If buffer fills up: sender pauses → back-pressure
  - THIS IS HOW TCP PREVENTS FAST SENDERS FROM OVERWHELMING SLOW RECEIVERS

TCP CONGESTION CONTROL (Slow Start):
  - Connection starts by sending 1 packet
  - Each ACK doubles the window: 1 → 2 → 4 → 8 packets
  - At some threshold, grows linearly instead of exponentially
  - On packet loss: window halves (Congestion Avoidance)
  
HEAD-OF-LINE (HOL) BLOCKING:
  - TCP processes packets in order
  - Packet 5 lost → Packets 6, 7, 8 must WAIT even if they arrived
  - This is why HTTP/2 still has problems despite multiplexing
  - This is why HTTP/3 (QUIC on UDP) was invented
```

### Practical Task (Day 2)

```python
# Save as: phase-1-physics/networking/tcp_handshake_demo.py
# This shows you raw socket programming — what TCP actually looks like

import socket
import time

def tcp_client_demo(host: str, port: int):
    """
    Demonstrate what happens during a TCP connection.
    Each call to connect() triggers the 3-way handshake.
    """
    print(f"\n=== TCP Connection Demo to {host}:{port} ===")
    
    # Measure: single connection (includes handshake)
    start = time.perf_counter()
    sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock.connect((host, port))
    handshake_time = (time.perf_counter() - start) * 1000
    print(f"Connection established in {handshake_time:.2f}ms (includes 3-way handshake)")
    
    # Send HTTP request
    request = f"GET / HTTP/1.1\r\nHost: {host}\r\nConnection: close\r\n\r\n"
    sock.sendall(request.encode())
    
    # Receive response
    response = b""
    while True:
        chunk = sock.recv(4096)
        if not chunk:
            break
        response += chunk
    
    sock.close()
    total_time = (time.perf_counter() - start) * 1000
    
    print(f"First line of response: {response.split(b'\\r\\n')[0].decode()}")
    print(f"Total time: {total_time:.2f}ms")
    print(f"Handshake overhead: {handshake_time:.2f}ms ({handshake_time/total_time*100:.1f}% of total)")
    
    # Now demonstrate connection reuse (keep-alive)
    print("\n--- Now with connection reuse (simulating connection pool) ---")
    start2 = time.perf_counter()
    sock2 = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    sock2.connect((host, port))
    
    for i in range(5):
        # Reuse same connection — no handshake!
        req = f"GET / HTTP/1.1\r\nHost: {host}\r\nConnection: keep-alive\r\n\r\n"
        sock2.sendall(req.encode())
        resp = sock2.recv(4096)
    
    reuse_time = (time.perf_counter() - start2) * 1000
    sock2.close()
    print(f"5 requests with connection reuse: {reuse_time:.2f}ms")
    print(f"vs 5 new connections would be: {handshake_time * 5:.2f}ms minimum")

# Test against a known server
tcp_client_demo("httpbin.org", 80)
```

### Architecture Reasoning Task
A startup's API is slow. You measure that each API call to the database takes 150ms. The database query itself is only 2ms. Where are the other 148ms going? Design a fix.

*(Answer: New TCP connection + TLS handshake for every query. Fix: Connection pooling + persistent connections)*

### ✅ Active Recall (Day 2)
1. Why does a database connection pool of 10 connections handle 1000 requests/second better than opening 1000 new connections?
2. What is the "Sliding Window" in TCP and which side controls it?
3. What specific problem does QUIC solve that TCP cannot?

---

## DAY 3: UDP and QUIC — When Speed Beats Reliability

### Core Concepts

```
TCP vs UDP — THE FUNDAMENTAL TRADEOFF:

TCP:                            UDP:
✅ Reliable delivery            ✅ Fast (no handshake)
✅ Ordered                      ✅ Low latency
✅ Flow control                 ✅ No head-of-line blocking
❌ Handshake overhead           ❌ No delivery guarantee
❌ HOL blocking                 ❌ No ordering
❌ Connection setup time        ❌ No flow control

WHERE UDP IS USED:
- Video/Audio streaming (Netflix, YouTube live, Zoom)
  → A dropped video frame is better than a delayed one
- Online gaming (packet loss = skip, not stall)
- DNS queries (one UDP packet, fast response)
- QUIC/HTTP/3 (builds reliability ON TOP of UDP, but smarter than TCP)

QUIC (HTTP/3) — THE BEST OF BOTH WORLDS:
- Built on UDP (no kernel-level connection state)
- Multiplexed streams (each stream is INDEPENDENT)
- 0-RTT connection (resume previous connection with no handshake)
- Packet loss in Stream A does NOT affect Stream B
- Built-in TLS 1.3 (encryption is mandatory)
- Used by: Google (all Google services), YouTube, Facebook, Cloudflare

WHY GOOGLE INVENTED QUIC:
- On mobile networks, TCP's HOL blocking was catastrophic
- 10% packet loss on mobile → entire HTTP/2 multiplexed stream stalls
- QUIC on UDP: 10% packet loss → only that one stream stalls
- Result: 15% faster page loads, 30% fewer video rebuffers (Google's data)
```

### Practical Task (Day 3)

```python
# Build a UDP file transfer with manual reliability
# This shows you EXACTLY what TCP does — you're implementing it by hand
# Save as: phase-1-physics/networking/udp_reliable_transfer.py

import socket
import hashlib
import struct
import time
from dataclasses import dataclass

CHUNK_SIZE = 1024
TIMEOUT = 2.0

@dataclass
class Packet:
    seq: int        # Sequence number
    data: bytes     # Payload
    checksum: bytes # MD5 of data (integrity check)
    is_last: bool   # Is this the final packet?
    
    def serialize(self) -> bytes:
        header = struct.pack('!I?', self.seq, self.is_last)
        return header + self.checksum + self.data
    
    @classmethod
    def deserialize(cls, raw: bytes) -> 'Packet':
        seq, is_last = struct.unpack('!I?', raw[:5])
        checksum = raw[5:21]
        data = raw[21:]
        return cls(seq=seq, data=data, checksum=checksum, is_last=is_last)


class UDPSender:
    def __init__(self, host: str, port: int):
        self.sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        self.destination = (host, port)
    
    def send_file(self, data: bytes):
        chunks = [data[i:i+CHUNK_SIZE] for i in range(0, len(data), CHUNK_SIZE)]
        print(f"Sending {len(chunks)} chunks of {CHUNK_SIZE} bytes each")
        
        for i, chunk in enumerate(chunks):
            checksum = hashlib.md5(chunk).digest()
            packet = Packet(seq=i, data=chunk, checksum=checksum, is_last=(i == len(chunks)-1))
            serialized = packet.serialize()
            
            # Send with retry (this is what TCP does automatically)
            for attempt in range(3):
                self.sock.sendto(serialized, self.destination)
                # Wait for ACK
                self.sock.settimeout(TIMEOUT)
                try:
                    ack, _ = self.sock.recvfrom(8)
                    ack_seq = struct.unpack('!I', ack)[0]
                    if ack_seq == i:
                        print(f"Chunk {i}: ACK received")
                        break
                except socket.timeout:
                    print(f"Chunk {i}: Timeout! Retrying ({attempt+1}/3)")
            else:
                print(f"Chunk {i}: FAILED after 3 attempts")


class UDPReceiver:
    def __init__(self, port: int):
        self.sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)
        self.sock.bind(('0.0.0.0', port))
        self.received_chunks = {}
    
    def receive(self) -> bytes:
        print("Receiver listening...")
        while True:
            raw, addr = self.sock.recvfrom(CHUNK_SIZE + 100)
            packet = Packet.deserialize(raw)
            
            # Verify integrity
            expected_checksum = hashlib.md5(packet.data).digest()
            if packet.checksum != expected_checksum:
                print(f"Chunk {packet.seq}: CORRUPTED — dropping")
                continue
            
            self.received_chunks[packet.seq] = packet.data
            
            # Send ACK
            ack = struct.pack('!I', packet.seq)
            self.sock.sendto(ack, addr)
            print(f"Chunk {packet.seq}: Received and ACKed")
            
            if packet.is_last:
                # Reassemble in order
                result = b''.join(self.received_chunks[i] for i in sorted(self.received_chunks))
                print(f"Transfer complete: {len(result)} bytes")
                return result
```

### ✅ Active Recall (Day 3)
1. Why does video streaming use UDP instead of TCP?
2. What makes QUIC better than HTTP/2 for mobile networks?
3. What is "0-RTT" in QUIC and what is its security tradeoff?

---

## DAY 4: DNS — The Internet's Phonebook + First Load Balancer

### Core Concepts

```
HOW DNS WORKS (The Full Resolution Chain):

You type: www.google.com

Step 1: Browser checks LOCAL CACHE
        → Found? Return immediately. Done.
        
Step 2: Query your OS resolver (check /etc/hosts)
        → Found? Return. Done.
        
Step 3: Query your LOCAL DNS RESOLVER (your ISP's or 8.8.8.8)
        → Checks its cache. Found? Return. Done.
        
Step 4: LOCAL RESOLVER queries ROOT SERVER
        → "Who handles .com?"
        → Root says: "Ask a.gtld-servers.net"
        
Step 5: LOCAL RESOLVER queries .COM TLD SERVER
        → "Who handles google.com?"
        → TLD says: "Ask ns1.google.com"
        
Step 6: LOCAL RESOLVER queries GOOGLE'S AUTHORITATIVE SERVER
        → "What is www.google.com's IP?"
        → Returns: 142.250.80.46 with TTL=300
        
Step 7: Local resolver caches the answer (for TTL seconds)
        Returns IP to browser.

THIS IS SLOW: ~100-200ms for a cold DNS lookup
SOLUTION: TTL caching. Once resolved, cached until TTL expires.

DNS AS LOAD BALANCER:
  Google's authoritative server might return:
  www.google.com → 142.250.80.46  (US East data center)
  OR
  www.google.com → 74.125.21.46   (EU data center)
  
  Which one? Depends on WHERE you are asking from (Anycast routing)
  Your request goes to the nearest data center = lower latency

DNS RECORD TYPES (Know These for Interviews):
  A      → hostname → IPv4 address
  AAAA   → hostname → IPv6 address
  CNAME  → hostname → another hostname (alias)
  MX     → mail server for domain
  NS     → which nameservers handle this domain
  TXT    → arbitrary text (used for SPF, DKIM verification)
  
TTL STRATEGY FOR HIGH AVAILABILITY:
  Normal operation: TTL = 3600 (1 hour)
  Before planned failover: Set TTL = 60 (1 minute)
  Wait 1 hour (so all caches expire the old high-TTL value)
  Execute failover: update DNS
  Recovery: change TTL back to 3600
```

### Practical Task (Day 4)

```bash
# Trace the full DNS resolution path
dig +trace www.google.com

# See DNS record types
dig www.google.com A       # IPv4 address
dig www.google.com AAAA    # IPv6 address
dig google.com MX          # Mail servers
dig google.com NS          # Name servers
dig google.com TXT         # Text records (see SPF, DKIM)

# Measure DNS lookup time
time dig www.google.com    # First lookup (cold)
time dig www.google.com    # Second lookup (cached — much faster!)

# See your local DNS resolver
cat /etc/resolv.conf

# Set up local DNS override (simulate a CDN failover)
sudo bash -c 'echo "127.0.0.1 myfakeapp.local" >> /etc/hosts'
ping myfakeapp.local       # Works! No real DNS needed.
# Remove it:
sudo sed -i '/myfakeapp.local/d' /etc/hosts
```

### Design Reasoning Task
A company uses DNS TTL of 1 hour. Their primary server crashes. How long until all users are routed to the backup? What should they have done differently?

*(Answer: Up to 1 hour — all cached entries must expire. Should have used TTL = 60 seconds for production, or used BGP Anycast where failover is sub-second without DNS change)*

---

## DAY 5: HTTP Evolution and API Paradigms

### Core Concepts

```
HTTP PROTOCOL EVOLUTION — WHY IT CHANGED:

HTTP/1.1 (1997 — The Problem Era):
  - One request at a time per connection (even with keep-alive)
  - Text-based headers (verbose, large)
  - Workaround: "Domain sharding" — browsers open 6 connections to same server
  - Problem: HOL blocking at both L7 and L4 level
  - Still: >50% of internet traffic (backward compatible)

HTTP/2 (2015 — The Optimization):
  - Binary framing (not human-readable)
  - MULTIPLEXING: multiple streams on one TCP connection
  - HPACK header compression (headers deduplicated between requests)
  - Server Push (server sends resources before browser asks)
  - Eliminates L7 HOL blocking but NOT L4 (TCP-level)
  - Google PageSpeed, Chrome, NGINX all support it

HTTP/3 / QUIC (2022 — The Redesign):
  - Built on UDP, not TCP
  - Each stream is INDEPENDENT (L4 HOL blocking solved)
  - 0-RTT resumption (no handshake for repeat visitors)
  - TLS 1.3 is mandatory and built-in
  - Used by: All Google services, 25% of all internet traffic

API PARADIGMS (Which to Use When):

REST:
  ✅ Public APIs (everyone understands it)
  ✅ Simple CRUD operations
  ✅ Caching-friendly (HTTP verbs have semantics)
  ❌ Over-fetching (getting more data than needed)
  ❌ Under-fetching (needing multiple requests for related data)
  Used by: Twitter API, Stripe API, GitHub API

GraphQL:
  ✅ Client specifies exactly what fields it needs (no over/under-fetching)
  ✅ One endpoint for all queries
  ✅ Strong typing with schema
  ❌ Complex caching (every query is a POST to the same endpoint)
  ❌ N+1 query problem (requires DataLoader pattern to solve)
  ❌ Over-engineering for simple use cases
  Used by: GitHub (v4 API), Shopify, Facebook

gRPC:
  ✅ Binary serialization (Protocol Buffers) — 5-10x smaller than JSON
  ✅ Strong typing across languages (generate code from .proto)
  ✅ Bidirectional streaming
  ✅ HTTP/2 transport (efficient)
  ❌ Not human-readable (harder to debug)
  ❌ Browser support requires grpc-web proxy
  Used by: Google internal, Uber, Netflix, Kubernetes internals
  
RULE OF THUMB:
  External public API → REST
  Frontend to backend → REST or GraphQL (if flexible data needs)
  Service-to-service internal → gRPC
```

### Practical Task (Day 5)

```bash
# Install Protocol Buffers compiler
sudo apt install protobuf-compiler
pip install grpcio grpcio-tools

# Create a proto file
cat > user_service.proto << 'EOF'
syntax = "proto3";

service UserService {
  rpc GetUser (GetUserRequest) returns (User);
  rpc ListUsers (ListUsersRequest) returns (ListUsersResponse);
}

message GetUserRequest { int32 user_id = 1; }

message User {
  int32 id = 1;
  string name = 2;
  string email = 3;
  repeated string roles = 4;
}

message ListUsersRequest {
  int32 page = 1;
  int32 limit = 2;
}

message ListUsersResponse {
  repeated User users = 1;
  int32 total = 2;
}
EOF

# Generate Python code
python3 -m grpc_tools.protoc -I. --python_out=. --grpc_python_out=. user_service.proto

# Compare payload sizes
python3 << 'EOF'
import json
import sys

# The same data in JSON vs Protobuf
user_json = {
    "id": 12345,
    "name": "Alice Engineer",
    "email": "alice@example.com",
    "roles": ["admin", "user"]
}
json_bytes = json.dumps(user_json).encode()
print(f"JSON payload size:     {len(json_bytes)} bytes")
print(f"JSON content: {json.dumps(user_json)}")

# Protobuf for the same data would be ~15-20 bytes
# (Field tags + varint encoding + string length prefix)
# Actual measurement: try it with the generated code!
print(f"\nProtobuf is typically 60-80% smaller than JSON")
print(f"At 1M API calls/day: saves {(len(json_bytes) - 18) * 1_000_000 / 1024 / 1024:.0f} MB of network traffic")
EOF
```

### ✅ Active Recall (Day 5)
1. A mobile app frequently requests user data with 50 fields, but only ever uses 5 of them. Which API paradigm solves this? What's the tradeoff?
2. Why would you NOT use gRPC for a public API that third-party developers will call?
3. What is the N+1 problem in GraphQL and how is it solved?

---

## DAY 6: Processes, Threads, and Concurrency Models

### Core Concepts

```
PROCESS vs THREAD:

PROCESS:
  - Independent program in execution
  - Has its OWN memory space (isolated)
  - Expensive to create (~1ms, ~8MB memory overhead)
  - Communication requires IPC (pipes, sockets, shared memory)
  - Crash doesn't affect other processes
  - Examples: Your browser, your database, your application server

THREAD:
  - Lightweight unit of execution within a process
  - SHARES memory with other threads in same process
  - Cheap to create (~10µs, ~64KB stack)
  - Communication via shared variables (but requires synchronization!)
  - Crash CRASHES the entire process
  - Examples: Web server handling multiple requests simultaneously

THE GIL PROBLEM (Python-Specific):
  - CPython (standard Python) has a Global Interpreter Lock (GIL)
  - Only ONE Python thread executes Python bytecode at a time
  - Consequence: Python threads can't use multiple CPU cores for CPU-bound work
  - MYTH: Python threads are useless. REALITY: GIL released during I/O!
  - For I/O-bound work (waiting for network, disk): Python threads work great
  - For CPU-bound work: Use multiprocessing or Go/Rust/Java

GO GOROUTINES (The Better Model):
  - Goroutines are user-space threads (not OS threads)
  - ~2KB stack (vs ~8MB for OS threads)
  - Can run millions concurrently
  - Scheduled by Go runtime (not OS)
  - Communicate via CHANNELS (not shared memory)
  - "Don't communicate by sharing memory; share memory by communicating"

CONCURRENCY BUGS:
  Race Condition: Two threads read-modify-write same variable
    Thread A reads x=5, Thread B reads x=5
    Both add 1, both write 6. But x should be 7!
  
  Deadlock: T1 holds Lock A, wants Lock B.
             T2 holds Lock B, wants Lock A.
             Both wait forever.
  
  Livelock: Both processes keep responding to each other
             but neither makes progress (like two people in a hallway)
```

### Practical Task (Day 6)

```python
# Save as: phase-1-physics/os-internals/concurrency_demo.py
import threading
import time
from concurrent.futures import ThreadPoolExecutor, ProcessPoolExecutor

# ============================
# DEMO 1: Race Condition
# ============================
counter_unsafe = 0

def unsafe_increment():
    global counter_unsafe
    for _ in range(100000):
        counter_unsafe += 1   # NOT ATOMIC: read, add, write (3 steps!)

threads = [threading.Thread(target=unsafe_increment) for _ in range(5)]
[t.start() for t in threads]
[t.join() for t in threads]
print(f"Expected: 500000, Got: {counter_unsafe} (race condition!)")

# ============================
# DEMO 2: Fixed with Lock
# ============================
counter_safe = 0
lock = threading.Lock()

def safe_increment():
    global counter_safe
    for _ in range(100000):
        with lock:             # Only one thread at a time can enter
            counter_safe += 1

threads = [threading.Thread(target=safe_increment) for _ in range(5)]
[t.start() for t in threads]
[t.join() for t in threads]
print(f"Expected: 500000, Got: {counter_safe} (correct!)")

# ============================
# DEMO 3: GIL — I/O vs CPU bound
# ============================
import requests

def io_bound_task(url: str):
    """I/O bound: waiting for network. GIL released during I/O."""
    # In a real server: database queries, file reads, external API calls
    time.sleep(0.1)  # Simulate I/O wait
    return f"Done: {url}"

def cpu_bound_task(n: int):
    """CPU bound: computation. GIL NOT released."""
    return sum(i * i for i in range(n))

urls = ["http://example.com"] * 10

# I/O bound: threads work well (GIL released during sleep/network)
start = time.time()
with ThreadPoolExecutor(max_workers=10) as executor:
    results = list(executor.map(io_bound_task, urls))
print(f"I/O bound with threads: {time.time()-start:.2f}s (expected ~0.1s)")

# CPU bound: threads DON'T help due to GIL (use multiprocessing instead)
numbers = [10_000_000] * 4
start = time.time()
with ProcessPoolExecutor(max_workers=4) as executor:
    results = list(executor.map(cpu_bound_task, numbers))
print(f"CPU bound with processes: {time.time()-start:.2f}s (uses all cores)")
```

### ✅ Active Recall (Day 6)
1. A Python web server handles 1000 concurrent HTTP requests. Should it use threads or processes? Why?
2. What is a deadlock? Give a real system design scenario where it could occur.
3. Why do Go's goroutines scale to millions while OS threads max out at thousands?

---

## DAY 7: I/O Models and the C10K Problem

### Core Concepts

```
THE C10K PROBLEM (1999):
  How do you handle 10,000 concurrent network connections?
  
  NAIVE APPROACH — One Thread Per Connection:
    - Each connection = one OS thread = ~8MB stack
    - 10,000 connections = 80GB RAM just for thread stacks
    - Plus: context switching overhead between 10K threads
    - Result: Server falls over at ~1000 connections
    
  APACHE MODEL (Thread-Per-Request):
    - Worked at scale of 1999 internet
    - Died as web became more concurrent
  
  THE SOLUTION: I/O Multiplexing

I/O MULTIPLEXING — ONE THREAD, MANY CONNECTIONS:

  select() (old, works everywhere):
    - Pass a set of file descriptors to watch
    - Returns when any of them are ready
    - Limit: 1024 file descriptors max
    - Problem: O(n) scan of all FDs on every call

  poll() (slightly better):
    - No 1024 limit
    - Still O(n) scan

  epoll() (Linux, modern, fast):
    - Register interest once: epoll_ctl(fd)
    - Get notified ONLY when ready: epoll_wait()
    - O(1) — only returns ready FDs
    - Can watch millions of connections
    - THIS IS WHAT NGINX, Redis, Node.js use internally

EVENT LOOP (epoll under the hood):
  while True:
    ready_events = epoll_wait(timeout)   # Block until something is ready
    for event in ready_events:
      if event is "connection":
        accept_new_client(event.fd)
      elif event is "data_available":
        handle_client_data(event.fd)
      elif event is "writable":
        send_buffered_response(event.fd)
  
  NGINX handles 10,000+ concurrent connections with 1 thread per CPU core.
  Redis handles all clients with 1 thread total.
```

### Practical Task (Day 7)

```python
# Save as: phase-1-physics/os-internals/event_loop_server.py
# Build a chat server that handles multiple clients in ONE thread

import selectors
import socket
import types
from dataclasses import dataclass
from typing import Dict

@dataclass
class ClientConnection:
    addr: tuple
    outbuffer: bytes = b""

class SingleThreadedChatServer:
    """
    Handles unlimited concurrent connections in ONE thread.
    This is the model used by Redis, NGINX, and Node.js.
    """
    def __init__(self, host: str = "0.0.0.0", port: int = 9999):
        self.sel = selectors.DefaultSelector()  # Uses epoll on Linux
        self.clients: Dict[int, ClientConnection] = {}
        
        # Create listening socket
        self.server_sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        self.server_sock.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
        self.server_sock.bind((host, port))
        self.server_sock.listen(1000)
        self.server_sock.setblocking(False)
        
        # Register server socket for "incoming connection" events
        self.sel.register(self.server_sock, selectors.EVENT_READ, data="server")
        print(f"Single-threaded server listening on {host}:{port}")
        print("Connect with: nc localhost 9999 (multiple terminals!)")
    
    def accept_connection(self):
        conn, addr = self.server_sock.accept()
        conn.setblocking(False)
        self.clients[conn.fileno()] = ClientConnection(addr=addr)
        self.sel.register(conn, selectors.EVENT_READ, data=conn)
        print(f"New client: {addr} (total: {len(self.clients)})")
        self.broadcast(f"[SERVER] {addr[0]} joined\n".encode())
    
    def handle_client_data(self, conn: socket.socket):
        try:
            data = conn.recv(1024)
            if data:
                client = self.clients[conn.fileno()]
                msg = f"[{client.addr[0]}]: {data.decode().strip()}\n"
                print(f"Message: {msg.strip()}")
                self.broadcast(msg.encode(), sender_fd=conn.fileno())
            else:
                self.disconnect_client(conn)
        except ConnectionResetError:
            self.disconnect_client(conn)
    
    def broadcast(self, message: bytes, sender_fd: int = -1):
        """Send message to all clients except sender."""
        for fd, client in list(self.clients.items()):
            if fd != sender_fd:
                try:
                    # Get the socket from the selector
                    key = self.sel.get_key(fd)
                    key.fileobj.sendall(message)
                except Exception:
                    pass
    
    def disconnect_client(self, conn: socket.socket):
        fd = conn.fileno()
        if fd in self.clients:
            print(f"Client {self.clients[fd].addr} disconnected")
            del self.clients[fd]
        self.sel.unregister(conn)
        conn.close()
    
    def run(self):
        """THE EVENT LOOP — One thread, infinite connections."""
        while True:
            # epoll_wait: blocks until SOMETHING is ready (no busy-waiting)
            events = self.sel.select(timeout=None)
            for key, mask in events:
                if key.data == "server":
                    self.accept_connection()
                else:
                    self.handle_client_data(key.fileobj)

if __name__ == "__main__":
    server = SingleThreadedChatServer()
    server.run()
```

```bash
# Test: Open 3 terminals
# Terminal 1: python3 event_loop_server.py
# Terminal 2: nc localhost 9999  (type messages)
# Terminal 3: nc localhost 9999  (see messages from Terminal 2)
# All handled by ONE thread!
```

---

## DAY 8: Memory, Storage, and File Descriptors

### Core Concepts

```
VIRTUAL MEMORY:
  - Each process thinks it has ALL of RAM (4GB on 32-bit, 2^48 bytes on 64-bit)
  - OS uses page tables to translate virtual → physical addresses
  - Pages (4KB each) swapped to disk when RAM is full
  - "Thrashing": Too much swapping → disk I/O → system becomes unusable
  
  FOR SYSTEM DESIGN:
  - This is why "buffer pool size" matters in databases
  - PostgreSQL: shared_buffers = 25% of RAM (hot pages stay in buffer pool)
  - Redis: maxmemory (evicts keys when limit hit)

STORAGE HIERARCHY (Speed vs Cost):
  CPU Register  →  0.3 ns   → bytes
  L1 Cache      →  1 ns     → 32 KB
  L2 Cache      →  4 ns     → 256 KB
  L3 Cache      →  10 ns    → 8–32 MB
  RAM           →  100 ns   → 8–512 GB
  NVMe SSD      →  20 µs    → 1–8 TB
  SATA SSD      →  100 µs   → 1–4 TB
  HDD           →  5–10 ms  → 1–20 TB

  THIS EXPLAINS EVERYTHING:
  - Redis is fast because everything is in RAM (100 ns access)
  - B-Tree databases use bufferpool to keep hot pages in RAM
  - Sequential disk reads are faster than random reads
  - "Random I/O kills performance" = IOPS limit on HDDs

FILE DESCRIPTORS:
  - Linux: "Everything is a file"
  - Network sockets ARE file descriptors
  - Open files, pipes, /dev/ devices = file descriptors
  - Default limit: 1024 per process (ulimit -n)
  - High-performance servers need: 1M+ FDs (sysctl -w fs.file-max=2097152)
  - NGINX sets: worker_rlimit_nofile 65536;
```

### Practical Task (Day 8)

```bash
# See how many FDs your system allows
ulimit -n                          # Current limit (probably 1024)
cat /proc/sys/fs/file-max          # System-wide max

# See FDs used by PostgreSQL
ls /proc/$(pgrep postgres | head -1)/fd | wc -l

# Intentionally exhaust FDs to see the error
python3 << 'EOF'
files = []
try:
    while True:
        files.append(open('/dev/null', 'r'))
except OSError as e:
    print(f"Failed after {len(files)} open files: {e}")
finally:
    for f in files:
        f.close()
EOF

# Increase the limit for high-performance servers
ulimit -n 65536    # Temporary (this session only)
# Permanent: add to /etc/security/limits.conf:
# * soft nofile 65536
# * hard nofile 65536
```

---

## DAY 9: Load Balancing Architecture — L4 vs L7

### Core Concepts

```
LOAD BALANCING ALGORITHMS:

Round Robin:
  Request 1 → Server A
  Request 2 → Server B
  Request 3 → Server C
  Request 4 → Server A (cycles back)
  ✅ Simple. ❌ Ignores server load. If Server A handles heavy requests, it's overwhelmed.

Weighted Round Robin:
  Server A: weight=3 → gets 3/6 of traffic
  Server B: weight=2 → gets 2/6
  Server C: weight=1 → gets 1/6
  Use when servers have different specs.

Least Connections:
  Always send to server with FEWEST active connections.
  ✅ Better for long-lived connections (WebSockets, gRPC streaming)
  ❌ More complex to implement

IP Hash / Consistent Hashing:
  hash(client_ip) → always same server
  ✅ Session stickiness (user always hits same server)
  ❌ Uneven if IPs cluster (many users behind same NAT)
  Use for: stateful sessions, cache locality

L4 vs L7 LOAD BALANCING:

L4 (Transport Layer):
  - Sees: source IP, dest IP, source port, dest port
  - Does NOT read: HTTP headers, URL paths, cookies
  - Fast: just route the packet (no parsing)
  - Cheap: can handle millions of connections/second
  - Cannot: route /api to one server and / to another
  - Tools: HAProxy (TCP mode), AWS NLB, Linux LVS

L7 (Application Layer):
  - Reads: HTTP method, URL, headers, cookies
  - Can route: /api/* → backend servers, /static/* → CDN
  - Can modify: add headers (X-Real-IP), rewrite URLs
  - Can implement: SSL termination (decrypt HTTPS here, forward HTTP)
  - Slower than L4 (must parse HTTP)
  - Tools: NGINX, HAProxy (HTTP mode), AWS ALB, Envoy

HEALTH CHECKING:
  Load balancer must know which backends are healthy.
  
  Passive: Notice errors in real traffic (500 responses → mark unhealthy)
  Active: Send periodic health check requests (GET /health every 5s)
  
  Circuit Breaker: If backend fails 5 times in 30s → stop sending for 60s → try again
```

### Practical Task (Day 9)

```bash
# Configure NGINX as L7 load balancer between 3 Python servers

# Start 3 backend servers on different ports
python3 -c "
from http.server import HTTPServer, BaseHTTPRequestHandler
import sys

class Handler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.end_headers()
        self.wfile.write(f'Response from Server {sys.argv[1]}\n'.encode())
    def log_message(self, *args): pass

HTTPServer(('', int(sys.argv[1])), Handler).serve_forever()
" 8001 &

python3 -c "
from http.server import HTTPServer, BaseHTTPRequestHandler
import sys

class Handler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.end_headers()
        self.wfile.write(f'Response from Server {sys.argv[1]}\n'.encode())
    def log_message(self, *args): pass

HTTPServer(('', int(sys.argv[1])), Handler).serve_forever()
" 8002 &

python3 -c "
from http.server import HTTPServer, BaseHTTPRequestHandler
import sys

class Handler(BaseHTTPRequestHandler):
    def do_GET(self):
        self.send_response(200)
        self.end_headers()
        self.wfile.write(f'Response from Server {sys.argv[1]}\n'.encode())
    def log_message(self, *args): pass

HTTPServer(('', int(sys.argv[1])), Handler).serve_forever()
" 8003 &

# Create NGINX config
sudo tee /etc/nginx/sites-available/load_balancer.conf << 'EOF'
upstream backend_pool {
    # Round-robin by default
    server 127.0.0.1:8001 weight=3;  # Gets 3x traffic
    server 127.0.0.1:8002 weight=2;  # Gets 2x traffic
    server 127.0.0.1:8003 weight=1;  # Gets 1x traffic
    
    # Health check: remove server if it returns errors
    # keepalive 32;  # Reuse connections to backends
}

server {
    listen 8080;
    
    location / {
        proxy_pass http://backend_pool;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
    }
    
    # Route API traffic to different pool
    location /api/ {
        proxy_pass http://backend_pool;
    }
}
EOF

sudo nginx -t && sudo nginx -s reload

# Test it: send 10 requests and see distribution
for i in $(seq 1 10); do curl -s http://localhost:8080/; done
```

---

## DAYS 10–12: Containers, Microservices Basics, and Review

### Day 10: Containers From First Principles

```bash
# Understand what Docker ACTUALLY IS (it's just Linux namespaces + cgroups)

# 1. Create an isolated process namespace (like a container)
sudo unshare --fork --pid --mount-proc /bin/bash
# You're now in an isolated PID namespace!
# ps aux  -- only shows your processes
exit

# 2. Limit CPU and memory with cgroups (what Docker does internally)
sudo cgcreate -g cpu,memory:mycontainer
sudo cgset -r cpu.shares=512 mycontainer         # Half CPU share
sudo cgset -r memory.limit_in_bytes=100M mycontainer  # 100MB RAM limit

# 3. Docker combines all of this automatically:
docker run --memory=100m --cpus=0.5 --name mytest ubuntu:22.04 bash -c "free -h && nproc"

# THE KEY INSIGHT:
# Docker = namespaces (isolation) + cgroups (resource limits) + union filesystems (layers)
# There is NO hardware virtualization. Containers share the host kernel.
# That's why containers start in <1 second but VMs take 30+ seconds.
```

### Day 11: Container Orchestration Preview + System Design Framework

```
THE SYSTEM DESIGN INTERVIEW FRAMEWORK:

STEP 1 — CLARIFY (5 min):
  "Before I start, let me confirm the requirements."
  - Scale: How many users? DAU/MAU? Requests/second?
  - Features: Which exact features? Any out of scope?
  - Constraints: Read-heavy or write-heavy? Latency requirements? Strong or eventual consistency?
  - Non-functional: Availability (99.9%? 99.99%?)? Global or regional?

STEP 2 — ESTIMATE (3 min):
  Back-of-envelope calculation.
  "Let me estimate the scale to guide my design decisions."
  
  USEFUL NUMBERS TO MEMORIZE:
  - 86,400 seconds per day
  - 1M requests/day ÷ 86,400 = ~12 requests/second
  - 1B requests/day = ~12,000 requests/second
  - 1KB × 1M users = 1GB
  - 1MB × 1M users = 1TB
  - HDD sequential: 100 MB/s read
  - SSD sequential: 500 MB/s read
  - Network: 10 Gbps = 1.25 GB/s
  - Redis: 100K ops/second single node

STEP 3 — HIGH-LEVEL DESIGN (10 min):
  Draw: clients → API gateway → services → databases
  Identify: bottlenecks, single points of failure

STEP 4 — DEEP DIVE (15 min):
  Pick 2-3 most complex components. Go deep.
  Show your knowledge of internals.

STEP 5 — TRADEOFFS (5 min):
  "This design optimizes for X but sacrifices Y."
  "At 10x scale, I would change..."
  "The risk here is... and we mitigate by..."
```

### Day 12: Review + Practice Estimation

```
PRACTICE: BACK-OF-ENVELOPE FOR TWITTER

Given: 300M DAU, 500M tweets/day, 100 followers average

Calculations:
  Tweets/second = 500M ÷ 86,400 = ~5,800 tweets/second (write QPS)
  
  Timeline reads: Each user reads ~200 tweets/day
  Read QPS = 300M × 200 ÷ 86,400 = ~694,000 reads/second
  Read:Write ratio = 694,000 : 5,800 ≈ 120:1
  
  → THIS IS READ-HEAVY. Optimize for reads.
  → Caching is critical.
  → Consider pre-computed timelines (fan-out on write).
  
  Storage per tweet: 280 chars = ~280 bytes text + metadata = ~1KB
  Storage/day = 500M × 1KB = 500GB/day
  Storage/year = 500GB × 365 = ~180TB/year (just text)
  
  With media (assume 10% have images, avg 100KB):
  50M × 100KB = 5TB/day of media
  
  → Need object storage (not a database) for media
  → CDN is mandatory for media delivery
```

---

## DAYS 13–14: PROJECT 1 — Layer 7 Load Balancer

### Problem Statement
Build a functional HTTP load balancer from scratch. This proves you understand:
- TCP socket programming
- HTTP protocol parsing
- Round-robin algorithm
- Health checking
- Concurrency

### Architecture

```
CLIENT REQUEST
      │
      ▼
┌─────────────────────────────────────────────────────────────┐
│              YOUR LAYER 7 LOAD BALANCER                      │
│  Port: 8080                                                  │
│                                                              │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Request Handler                                      │  │
│  │  1. Accept TCP connection                            │  │
│  │  2. Read raw bytes until \r\n\r\n                   │  │
│  │  3. Parse HTTP method + Host header                  │  │
│  │  4. Call backend_selector.get_next()                │  │
│  │  5. Forward request to selected backend             │  │
│  │  6. Stream response back to client                  │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                              │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Round-Robin Backend Selector                         │  │
│  │  backends = [Server(8001), Server(8002), Server(8003)]│  │
│  │  current_index = 0 (atomic, thread-safe)             │  │
│  └──────────────────────────────────────────────────────┘  │
│                                                              │
│  ┌──────────────────────────────────────────────────────┐  │
│  │  Health Check Thread                                  │  │
│  │  Every 5 seconds: GET /health on each backend        │  │
│  │  If 2xx: mark healthy                                │  │
│  │  If fail: mark unhealthy, remove from rotation       │  │
│  │  If recovered: add back to rotation                  │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
      │
      ├── Backend Server A (8001)
      ├── Backend Server B (8002)
      └── Backend Server C (8003)
```

### Complete Implementation

```python
# Save as: projects/01-layer7-load-balancer/load_balancer.py

import socket
import threading
import time
import itertools
import logging
from dataclasses import dataclass, field
from typing import List, Optional
import urllib.request

logging.basicConfig(level=logging.INFO, format='%(asctime)s %(levelname)s %(message)s')
log = logging.getLogger(__name__)

@dataclass
class Backend:
    host: str
    port: int
    weight: int = 1
    healthy: bool = True
    total_requests: int = 0
    failed_requests: int = 0
    
    @property
    def address(self) -> tuple:
        return (self.host, self.port)
    
    def __str__(self):
        status = "✅" if self.healthy else "❌"
        return f"{status} {self.host}:{self.port} (requests: {self.total_requests})"


class RoundRobinSelector:
    """Thread-safe round-robin backend selection."""
    def __init__(self, backends: List[Backend]):
        self.backends = backends
        self._lock = threading.Lock()
        self._index = 0
    
    def get_next(self) -> Optional[Backend]:
        with self._lock:
            healthy = [b for b in self.backends if b.healthy]
            if not healthy:
                return None
            backend = healthy[self._index % len(healthy)]
            self._index = (self._index + 1) % len(healthy)
            return backend


class HealthChecker(threading.Thread):
    """Background thread that actively checks backend health."""
    def __init__(self, backends: List[Backend], interval: int = 5):
        super().__init__(daemon=True)
        self.backends = backends
        self.interval = interval
    
    def check_backend(self, backend: Backend) -> bool:
        try:
            url = f"http://{backend.host}:{backend.port}/health"
            with urllib.request.urlopen(url, timeout=2) as resp:
                return resp.status == 200
        except Exception:
            return False
    
    def run(self):
        log.info("Health checker started")
        while True:
            for backend in self.backends:
                was_healthy = backend.healthy
                backend.healthy = self.check_backend(backend)
                if was_healthy and not backend.healthy:
                    log.warning(f"Backend {backend} went UNHEALTHY")
                elif not was_healthy and backend.healthy:
                    log.info(f"Backend {backend} recovered to HEALTHY")
            time.sleep(self.interval)


class LoadBalancer:
    """
    Layer 7 HTTP Load Balancer.
    Parses HTTP headers to make routing decisions.
    """
    def __init__(self, host: str, port: int, backends: List[Backend]):
        self.host = host
        self.port = port
        self.selector = RoundRobinSelector(backends)
        self.health_checker = HealthChecker(backends)
        self.stats = {"total": 0, "success": 0, "failed": 0}
        self._stats_lock = threading.Lock()
    
    def parse_http_request(self, raw: bytes) -> dict:
        """Parse raw HTTP bytes into structured data."""
        text = raw.decode('utf-8', errors='replace')
        lines = text.split('\r\n')
        
        if not lines:
            return {}
        
        method, path, version = lines[0].split(' ', 2) if ' ' in lines[0] else ('GET', '/', 'HTTP/1.1')
        headers = {}
        for line in lines[1:]:
            if ':' in line:
                key, _, val = line.partition(':')
                headers[key.strip().lower()] = val.strip()
        
        return {"method": method, "path": path, "version": version, "headers": headers}
    
    def forward_request(self, client_sock: socket.socket, backend: Backend):
        """Forward client request to backend and return response."""
        try:
            # Read client request
            request_data = b""
            client_sock.settimeout(10)
            while True:
                chunk = client_sock.recv(4096)
                request_data += chunk
                if b'\r\n\r\n' in request_data:
                    break
            
            parsed = self.parse_http_request(request_data)
            log.info(f"{parsed.get('method')} {parsed.get('path')} → {backend.host}:{backend.port}")
            
            # Connect to backend
            backend_sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            backend_sock.settimeout(10)
            backend_sock.connect(backend.address)
            
            # Forward request with LB identification header
            modified_request = request_data.replace(
                b'\r\n\r\n',
                f'\r\nX-Forwarded-For: {client_sock.getpeername()[0]}\r\n'
                f'X-Load-Balancer: MyLB/1.0\r\n\r\n'.encode()
            )
            backend_sock.sendall(modified_request)
            
            # Stream response back to client
            while True:
                data = backend_sock.recv(4096)
                if not data:
                    break
                client_sock.sendall(data)
            
            backend_sock.close()
            backend.total_requests += 1
            
            with self._stats_lock:
                self.stats["total"] += 1
                self.stats["success"] += 1
                
        except Exception as e:
            log.error(f"Error forwarding to {backend}: {e}")
            backend.failed_requests += 1
            # Return 502 to client
            try:
                client_sock.sendall(
                    b"HTTP/1.1 502 Bad Gateway\r\nContent-Length: 16\r\n\r\nBackend Error\r\n"
                )
            except Exception:
                pass
            with self._stats_lock:
                self.stats["failed"] += 1
    
    def handle_client(self, client_sock: socket.socket, addr: tuple):
        try:
            backend = self.selector.get_next()
            if backend is None:
                log.error("No healthy backends available!")
                client_sock.sendall(
                    b"HTTP/1.1 503 Service Unavailable\r\nContent-Length: 24\r\n\r\nNo backends available\r\n"
                )
                return
            self.forward_request(client_sock, backend)
        finally:
            client_sock.close()
    
    def print_stats(self):
        while True:
            time.sleep(10)
            log.info(f"Stats: {self.stats}")
            for b in self.selector.backends:
                log.info(f"  {b}")
    
    def run(self):
        self.health_checker.start()
        threading.Thread(target=self.print_stats, daemon=True).start()
        
        server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
        server.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
        server.bind((self.host, self.port))
        server.listen(100)
        log.info(f"Load Balancer listening on {self.host}:{self.port}")
        
        while True:
            client_sock, addr = server.accept()
            thread = threading.Thread(target=self.handle_client, args=(client_sock, addr))
            thread.daemon = True
            thread.start()


if __name__ == "__main__":
    backends = [
        Backend(host="127.0.0.1", port=8001, weight=3),
        Backend(host="127.0.0.1", port=8002, weight=2),
        Backend(host="127.0.0.1", port=8003, weight=1),
    ]
    lb = LoadBalancer(host="0.0.0.0", port=8080, backends=backends)
    lb.run()
```

### Project 1 Documentation Strategy
**What makes this project credible to a hiring engineer:**

```
GitHub Repo: projects/01-layer7-load-balancer/
├── README.md       — Architecture diagram, how to run, what it demonstrates
├── load_balancer.py — The implementation
├── backends.py     — Start 3 test backends
├── test_lb.py      — Automated tests proving correctness
└── benchmark.md    — Load test results (requests/second, latency percentiles)

Blog Post: "I Built an HTTP Load Balancer From Scratch — Here's How HTTP Actually Works"
  - Include: what you learned about HTTP parsing, socket programming
  - Include: performance numbers (requests/second)
  - Include: architecture diagram

Evidence that impresses:
  - Screenshot of load balancer routing traffic to 3 backends
  - k6 load test output showing throughput
  - Health check recovery demo (kill a backend, it's removed; restart, it returns)
```

---

---

# 🟠 PHASE 2: DISTRIBUTED SYSTEMS THEORY (Days 15–30)

> **Goal:** Master the mathematical constraints that govern ALL distributed systems. These are the laws of physics for software. No amount of clever coding can violate them.
>
> **The Core Truth:** "The impossibility results of distributed computing define the solution space for every system you will ever build." — Every design decision in Phase 3+ follows from these constraints.

---

## DAY 15: CAP Theorem and PACELC — The Fundamental Tradeoffs

### Core Concepts

```
THE CAP THEOREM (Brewer, 2000):

In a distributed system experiencing a NETWORK PARTITION (P),
you can only guarantee ONE of:
  C = Consistency: Every read sees the most recent write
  A = Availability: Every request gets a response (not an error)

(Partition Tolerance is NOT optional — networks ALWAYS eventually partition)

THE REAL CHOICE: CP vs AP

CP Systems (Prefer Consistency over Availability during partition):
  - Refuse requests if can't guarantee consistency
  - Example: "I can't confirm this read is up-to-date, so I'll return an error"
  - Used by: PostgreSQL, HBase, ZooKeeper, etcd
  - When to use: Banking (you can't show stale balance), inventory (can't oversell)

AP Systems (Prefer Availability over Consistency during partition):
  - Return possibly stale data rather than returning an error
  - Example: "I'll give you what I have, but it might be 10 seconds old"
  - Used by: Cassandra, DynamoDB, CouchDB
  - When to use: Social media likes (few seconds stale is fine), product catalogs

PACELC THEOREM (Extends CAP to normal operation):
  During Partition (P):  Choose Availability (A) or Consistency (C)
  Else (E) [normal op]: Choose Latency (L) or Consistency (C)
  
  This matters because: even without a partition, strong consistency
  requires round-trips between nodes for every read → adds latency.
  
  Examples:
  DynamoDB: PA + EL (Available during partition, Low latency normally)
  Spanner:  PC + EC (Consistent during partition, Extra latency normally)
  Cassandra: PA + EL (configurable)
  MySQL:    PC + EC (Strong consistency, accepts latency)

REAL MNC DECISIONS:
  Amazon DynamoDB: Chose AP (availability) for shopping carts
    → Better to show a slightly stale cart than "Service Unavailable"
  
  Google Spanner: Chose CP (consistency) for financial systems
    → Cannot show stale account balances
  
  Cassandra at Discord: Chose AP for messages
    → 1 second delay in seeing a message is fine; downtime is not
```

### Architecture Reasoning Task
You are designing a ride-sharing app. For the following features, decide CP or AP and justify:
1. The driver's current GPS location shown to the passenger
2. The passenger's payment method on file
3. The number of available drivers in an area
4. Whether a specific driver is currently booked

*(Hints: 1=AP (staleness is fine), 2=CP (financial data), 3=AP (approximate is fine), 4=CP (double-booking is catastrophic))*

### ✅ Active Recall (Day 15)
1. You read that "Cassandra is AP." What exactly does this mean during a network partition?
2. Why does PACELC matter even when there are NO network partitions?
3. A banking system uses an AP database. What could go wrong during a network partition?

---

## DAY 16: Consistency Models — A Spectrum

### Core Concepts

```
CONSISTENCY MODELS (From Strongest to Weakest):

LINEARIZABILITY (Strong Consistency):
  - Every operation appears to happen instantaneously at a single point in time
  - If Write(x=5) completes, all subsequent reads must return 5
  - The gold standard. The most expensive.
  - Implementation: Raft, Paxos, 2PC
  - Used by: Google Spanner, ZooKeeper, etcd
  
SEQUENTIAL CONSISTENCY:
  - All processes see operations in the SAME order
  - But that order might not match real clock time
  - Slightly weaker than linearizability
  
CAUSAL CONSISTENCY:
  - Operations that are causally related are seen in order
  - Operations that are NOT causally related can be reordered
  - "If you saw me post, you must see my post before any replies to it"
  - Used by: MongoDB (causal sessions), some versions of DynamoDB
  
EVENTUAL CONSISTENCY:
  - If no new updates, eventually all replicas converge to same value
  - No guarantees about WHEN
  - Very high availability, very low latency
  - Used by: Cassandra (default), DynamoDB (default), DNS
  - Implementation: Vector clocks + anti-entropy + gossip protocol

READ YOUR OWN WRITES:
  - After you write something, you can always read it back
  - Weaker than strong consistency but stronger than eventual
  - How: Route all reads from user X to the replica that accepted X's write
  - Or: Attach a "read-at-timestamp" >= your write timestamp

MONOTONIC READS:
  - Once you read a value, you won't read an older value
  - Prevents: seeing "10 messages" then "8 messages" then "10 messages"

WHICH TO CHOOSE:
  User sees their OWN profile edits → Read Your Own Writes
  Social media feed → Eventual Consistency (seconds is fine)
  Shopping cart → Read Your Own Writes
  Payment confirmation → Linearizability
  Global leaderboard ranking → Sequential or Causal
```

### Practical Task (Day 16) — Simulate Consistency Levels

```python
# Save as: phase-2-distributed/consistency/consistency_demo.py
import threading
import time
import random
from typing import Optional

class Node:
    def __init__(self, node_id: str):
        self.id = node_id
        self.data = {}
        self.version = 0
        self.is_partitioned = False

class EventualConsistencyCluster:
    """Simulates eventual consistency: nodes sync asynchronously."""
    def __init__(self):
        self.nodes = [Node(f"node-{i}") for i in range(3)]
        self._sync_thread = threading.Thread(target=self._gossip_sync, daemon=True)
        self._sync_thread.start()
    
    def write(self, key: str, value: str, node_idx: int = 0) -> dict:
        node = self.nodes[node_idx]
        if not node.is_partitioned:
            node.data[key] = value
            node.version += 1
            return {"success": True, "written_to": node.id}
        return {"success": False, "error": "Node partitioned"}
    
    def read(self, key: str, node_idx: int = 0) -> dict:
        node = self.nodes[node_idx]
        value = node.data.get(key)
        return {"value": value, "from_node": node.id}
    
    def _gossip_sync(self):
        """Background thread: nodes gossip their data to peers."""
        while True:
            time.sleep(0.5)  # Simulate async replication delay
            for i, node in enumerate(self.nodes):
                if node.is_partitioned:
                    continue
                for other in self.nodes:
                    if other.id != node.id and not other.is_partitioned:
                        for key, val in node.data.items():
                            other.data[key] = val

# Demo
cluster = EventualConsistencyCluster()

print("=== Eventual Consistency Demo ===")
# Write to node 0
cluster.write("user:1", "Alice", node_idx=0)

# Immediately read from node 2 (sync hasn't happened yet)
read1 = cluster.read("user:1", node_idx=2)
print(f"Immediate read from node-2: {read1}")  # None — not synced yet!

# Wait for gossip
time.sleep(1)

# Read again from node 2
read2 = cluster.read("user:1", node_idx=2)
print(f"After 1s read from node-2: {read2}")  # Now it's there

print("\n=== Simulating Network Partition ===")
cluster.nodes[1].is_partitioned = True   # Partition node 1
cluster.write("user:1", "Alice Updated", node_idx=0)

time.sleep(1)

# Node 1 (partitioned) still has old value
read_partitioned = cluster.read("user:1", node_idx=1)
print(f"Partitioned node read: {read_partitioned}")  # Old value!

# Heal partition
cluster.nodes[1].is_partitioned = False
time.sleep(1)

read_healed = cluster.read("user:1", node_idx=1)
print(f"After partition healed: {read_healed}")  # New value eventually propagates
```

---

## DAY 17: Time and Clocks — Why Distributed Systems Are Hard

```
THE PROBLEM WITH PHYSICAL CLOCKS:

Every computer has a hardware clock. But:
- Clocks drift (computers are not perfectly synchronized)
- NTP (Network Time Protocol) corrects drift but with ±10ms precision
- At microsecond-level distributed operations, this is enormous

SCENARIO — WHY CLOCKS MATTER:
  Event A happens at Server 1: timestamp = 10:00:00.000
  Event B happens at Server 2: timestamp = 09:59:59.950 (50ms skew!)
  
  If you sort by timestamp: B appears to happen BEFORE A
  But in reality: A happened before B
  
  This breaks any system that relies on timestamps for ordering.

SOLUTION 1 — LAMPORT TIMESTAMPS (Logical Clocks):
  Rules:
  1. Each process keeps a counter (starts at 0)
  2. On any local event: counter++
  3. Before sending a message: counter++, attach counter to message
  4. On receiving message with timestamp T: counter = max(counter, T) + 1
  
  Guarantees: If A happened before B, Lamport(A) < Lamport(B)
  Does NOT guarantee: Lamport(A) < Lamport(B) means A happened before B
  (Concurrent events can have any ordering)

SOLUTION 2 — VECTOR CLOCKS (Causal Ordering):
  Each process keeps a VECTOR of counters (one per process)
  
  Process A clock: [A=0, B=0, C=0]
  A does local event: [A=1, B=0, C=0]
  A sends to B: [A=1, B=0, C=0] (attach to message)
  B receives: B_clock = element-wise max([A=1,B=0,C=0], [A=0,B=2,C=0]) + 1 on own index
            = [A=1, B=3, C=0]
  
  Now you can detect if events are concurrent (neither happened before the other)
  If concurrent: need conflict resolution (last-write-wins, merge, user prompt)

GOOGLE SPANNER — TRUETIME:
  Google solved this with HARDWARE:
  - Each datacenter has atomic clocks and GPS receivers
  - TrueTime API returns: [earliest_possible_time, latest_possible_time]
  - Uncertainty bound: typically 1-7ms
  - Before commit, Spanner WAITS for uncertainty to pass
  - Guarantees: global ordering with atomic clock precision
  - Cost: adds ~7ms latency to every write
  - Benefit: true global external consistency across continents
```

### Practical Task (Day 17)

```python
# Save as: phase-2-distributed/consistency/vector_clock.py

from dataclasses import dataclass, field
from typing import Dict, List, Tuple
import copy

@dataclass
class VectorClock:
    """
    Vector clock for causal ordering in distributed systems.
    Used by: Amazon Dynamo, Apache Cassandra (with modifications)
    """
    clocks: Dict[str, int] = field(default_factory=dict)
    
    def tick(self, process_id: str) -> 'VectorClock':
        """Increment this process's clock (local event)."""
        new = copy.deepcopy(self)
        new.clocks[process_id] = new.clocks.get(process_id, 0) + 1
        return new
    
    def merge(self, other: 'VectorClock') -> 'VectorClock':
        """Merge two clocks (on receive — take element-wise max)."""
        all_processes = set(self.clocks) | set(other.clocks)
        return VectorClock({
            p: max(self.clocks.get(p, 0), other.clocks.get(p, 0))
            for p in all_processes
        })
    
    def happens_before(self, other: 'VectorClock') -> bool:
        """Returns True if self happened BEFORE other (causal relationship)."""
        all_processes = set(self.clocks) | set(other.clocks)
        all_leq = all(self.clocks.get(p, 0) <= other.clocks.get(p, 0) for p in all_processes)
        at_least_one_less = any(self.clocks.get(p, 0) < other.clocks.get(p, 0) for p in all_processes)
        return all_leq and at_least_one_less
    
    def concurrent_with(self, other: 'VectorClock') -> bool:
        """Returns True if events are CONCURRENT (neither happened before the other)."""
        return not self.happens_before(other) and not other.happens_before(self)
    
    def __str__(self):
        return str(dict(sorted(self.clocks.items())))


# Simulate 3 distributed processes
def simulate_distributed_events():
    print("=== Vector Clock Simulation ===\n")
    
    # Initial clocks
    a_clock = VectorClock()
    b_clock = VectorClock()
    c_clock = VectorClock()
    
    # Event 1: A does local work
    a_clock = a_clock.tick("A")
    print(f"A does local event: A={a_clock}")
    
    # Event 2: A sends to B
    a_clock = a_clock.tick("A")
    msg_from_a = a_clock
    print(f"A sends message: A={a_clock}")
    
    # Event 3: B does local work first
    b_clock = b_clock.tick("B")
    print(f"B does local event before receiving: B={b_clock}")
    
    # Event 4: B receives A's message
    b_clock = b_clock.merge(msg_from_a).tick("B")  # merge then increment own
    # Wait — correct: receive merges, then tick for the receive event
    b_clock = msg_from_a.merge(b_clock)
    b_clock = b_clock.tick("B")
    print(f"B receives A's message: B={b_clock}")
    
    # Event 5: C does local work (CONCURRENT with A and B's events)
    c_clock = c_clock.tick("C")
    c_clock = c_clock.tick("C")
    print(f"C does work independently: C={c_clock}")
    
    print("\n--- Causal Analysis ---")
    print(f"Did A's first event happen before B's receive? {VectorClock({'A':1}).happens_before(b_clock)}")
    print(f"Are C's events concurrent with B's events? {c_clock.concurrent_with(b_clock)}")
    print("\nIf concurrent: need conflict resolution strategy!")
    print("Options: Last-Write-Wins (LWW), Multi-Value (return both), Application-level merge")

simulate_distributed_events()
```

---

## DAY 18: Distributed Consensus — Raft

### Core Concepts

```
THE CONSENSUS PROBLEM:
  Multiple nodes must AGREE on a single value.
  Even if some nodes fail or messages are lost.
  This is provably impossible with:
  - Asynchronous network + guaranteed termination (FLP impossibility)
  
  In practice: nodes have TIMEOUTS. If no response in T ms → assume failed.

RAFT ALGORITHM (Designed for Understandability):

3 ROLES:
  Leader: Handles ALL writes. Replicates to followers. Sends heartbeats.
  Follower: Accepts writes from leader. Votes in elections.
  Candidate: Running for leader. Requests votes.

LEADER ELECTION:
  1. Each follower has a random election timeout (150-300ms)
  2. If no heartbeat in timeout: become Candidate
  3. Increment term, vote for self, send RequestVote to all nodes
  4. If majority vote for you: become Leader, send heartbeat immediately
  5. If you see a node with higher term: revert to Follower
  
  WHY RANDOM TIMEOUT?
  Prevents two nodes becoming candidates at exactly the same time (split vote)

LOG REPLICATION:
  1. Client sends write to Leader
  2. Leader appends to its log (not committed yet)
  3. Leader sends AppendEntries to ALL followers
  4. Followers append to their logs, respond ACK
  5. When MAJORITY ACK: Leader commits the entry
  6. Leader responds to client: "Committed"
  7. Leader tells followers in next AppendEntries: "Commit up to index N"
  
  SAFETY GUARANTEE:
  A write is only committed when MAJORITY of nodes have it.
  Even if leader dies after commit: majority have the entry → new leader has it.

WHO USES RAFT:
  etcd (Kubernetes uses etcd for all cluster state)
  CockroachDB (global distributed SQL)
  TiKV (TiDB's storage layer)
  Consul (service mesh)
```

### Practical Task (Day 18)

```bash
# Visualize Raft interactively (no code needed — use the animation)
# Open in browser: https://raft.github.io/

# EXPERIMENT 1: Normal operation
# Press "Client Request" — watch log replication to followers

# EXPERIMENT 2: Leader failure
# Click on the Leader node → "Stop"
# Watch: followers timeout → election → new leader elected
# Measure: how long does leader election take?

# EXPERIMENT 3: Network partition
# Click "Partition" to split the cluster into two groups
# Try sending a client request — what happens?
# Heal the partition — what happens?

# Then implement a simplified version:
```

```python
# Save as: phase-2-distributed/consensus/raft_leader_election.py
# Simplified Raft leader election (no log replication — focus on election)

import threading
import time
import random
import enum
from dataclasses import dataclass, field
from typing import Optional, Set

class NodeState(enum.Enum):
    FOLLOWER = "follower"
    CANDIDATE = "candidate"
    LEADER = "leader"

@dataclass
class RaftNode(threading.Thread):
    node_id: int
    total_nodes: int
    all_nodes: list  # Will be set after creation
    
    state: NodeState = NodeState.FOLLOWER
    current_term: int = 0
    voted_for: Optional[int] = None
    leader_id: Optional[int] = None
    last_heartbeat: float = field(default_factory=time.time)
    election_timeout: float = field(default_factory=lambda: random.uniform(0.15, 0.30))
    votes_received: int = 0
    running: bool = True
    
    _lock: threading.Lock = field(default_factory=threading.Lock)
    
    def __post_init__(self):
        super().__init__(daemon=True)
        self.last_heartbeat = time.time()
    
    def become_follower(self, term: int, leader: Optional[int] = None):
        with self._lock:
            self.state = NodeState.FOLLOWER
            self.current_term = term
            self.voted_for = None
            self.leader_id = leader
            self.last_heartbeat = time.time()
            self.election_timeout = random.uniform(0.15, 0.30)
    
    def start_election(self):
        with self._lock:
            self.state = NodeState.CANDIDATE
            self.current_term += 1
            self.voted_for = self.node_id
            self.votes_received = 1  # Vote for self
            term = self.current_term
        
        print(f"[Node {self.node_id}] Starting election for term {term}")
        
        # Request votes from all other nodes
        granted_votes = 1
        for node in self.all_nodes:
            if node.node_id != self.node_id:
                granted = node.request_vote(self.node_id, term)
                if granted:
                    granted_votes += 1
        
        # Check if won
        with self._lock:
            if self.state == NodeState.CANDIDATE and self.current_term == term:
                if granted_votes > self.total_nodes // 2:
                    self.become_leader()
                else:
                    print(f"[Node {self.node_id}] Lost election (got {granted_votes}/{self.total_nodes} votes)")
                    self.state = NodeState.FOLLOWER
    
    def request_vote(self, candidate_id: int, candidate_term: int) -> bool:
        with self._lock:
            if candidate_term < self.current_term:
                return False  # Outdated candidate
            
            if candidate_term > self.current_term:
                self.current_term = candidate_term
                self.state = NodeState.FOLLOWER
                self.voted_for = None
            
            if self.voted_for is None or self.voted_for == candidate_id:
                self.voted_for = candidate_id
                self.last_heartbeat = time.time()  # Reset timer
                print(f"[Node {self.node_id}] Voted for Node {candidate_id} in term {candidate_term}")
                return True
        return False
    
    def become_leader(self):
        print(f"[Node {self.node_id}] *** BECAME LEADER for term {self.current_term} ***")
        self.state = NodeState.LEADER
        self.leader_id = self.node_id
        # Send initial heartbeats
        self.send_heartbeats()
    
    def send_heartbeats(self):
        term = self.current_term
        for node in self.all_nodes:
            if node.node_id != self.node_id:
                node.receive_heartbeat(self.node_id, term)
    
    def receive_heartbeat(self, leader_id: int, leader_term: int):
        with self._lock:
            if leader_term >= self.current_term:
                self.current_term = leader_term
                self.state = NodeState.FOLLOWER
                self.leader_id = leader_id
                self.last_heartbeat = time.time()
    
    def run(self):
        while self.running:
            time.sleep(0.05)  # Check every 50ms
            
            with self._lock:
                state = self.state
                elapsed = time.time() - self.last_heartbeat
                timeout = self.election_timeout
            
            if state == NodeState.FOLLOWER and elapsed > timeout:
                self.start_election()
            elif state == NodeState.LEADER:
                self.send_heartbeats()
                time.sleep(0.10)  # Heartbeat interval: 100ms


# Run the simulation
def run_raft_simulation():
    N = 5
    nodes = [RaftNode(node_id=i, total_nodes=N, all_nodes=[]) for i in range(N)]
    for node in nodes:
        node.all_nodes = nodes  # Connect all nodes
    
    print("=== Raft Leader Election Simulation ===")
    print(f"Starting {N} nodes. Waiting for leader election...\n")
    
    for node in nodes:
        node.start()
    
    time.sleep(1)  # Let election happen
    
    print("\n--- Current State ---")
    for node in nodes:
        with node._lock:
            print(f"Node {node.node_id}: {node.state.value}, term={node.current_term}, leader={node.leader_id}")

run_raft_simulation()
```

---

## DAY 19: Transactions — 2PC and Sagas

### Core Concepts

```
THE DISTRIBUTED TRANSACTION PROBLEM:
  Order Service: reserve inventory
  Payment Service: charge credit card
  Both must succeed or both must fail.
  
  But they're on different servers, different databases.
  How do you ensure atomicity?

TWO-PHASE COMMIT (2PC):
  
  PHASE 1 — PREPARE:
  Coordinator → Participant A: "Can you commit?"
  Coordinator → Participant B: "Can you commit?"
  Participants: Lock resources, write to redo log, respond "YES" or "NO"
  
  PHASE 2 — COMMIT or ABORT:
  If ALL said YES: Coordinator → all: "COMMIT"
  If ANY said NO: Coordinator → all: "ABORT"
  
  PROBLEMS:
  - Blocking: if coordinator crashes after Phase 1, participants are STUCK
    (They hold locks but don't know whether to commit or abort)
  - Single point of failure: coordinator
  - Latency: 2 round trips minimum
  
  WHEN TO USE: Tightly coupled systems (same datacenter, high control)
  Used by: PostgreSQL distributed transactions, some OLTP databases

SAGA PATTERN (The Microservices Solution):

  Instead of one big ACID transaction:
  Break into sequence of LOCAL transactions, each immediately committed.
  If any step fails: execute COMPENSATING TRANSACTIONS to undo previous steps.
  
  EXAMPLE — Hotel Booking Saga:
  
  Step 1: Reserve flight     → Committed locally
  Step 2: Reserve hotel      → Committed locally
  Step 3: Charge credit card → FAILS (card declined)
  
  Compensation:
  Undo Step 2: Cancel hotel reservation (compensating transaction)
  Undo Step 1: Cancel flight reservation (compensating transaction)
  
  CHOREOGRAPHY vs ORCHESTRATION:
  
  Choreography: Each service listens for events and reacts
    FlightBooked event → Hotel Service books hotel
    HotelBooked event → Payment Service charges card
    PaymentFailed event → Hotel Service cancels hotel
    HotelCancelled event → Flight Service cancels flight
    Pros: No central coordinator, decoupled
    Cons: Hard to visualize flow, distributed logic
  
  Orchestration: Central coordinator tells each service what to do
    Saga Orchestrator: "Flight Service, book a flight" → waits
    Saga Orchestrator: "Hotel Service, book a hotel" → waits
    Saga Orchestrator: "Payment Service, charge card" → FAIL
    Saga Orchestrator: "Hotel Service, cancel" → "Flight Service, cancel"
    Pros: Clear visibility, easy to debug
    Cons: Coupled to orchestrator
  
  MNC CHOICE: Orchestration (Uber, DoorDash) for visibility in production
```

---

## DAY 20: Quorums and Tunable Consistency

### Core Concepts

```
QUORUM-BASED SYSTEMS (Cassandra, DynamoDB):

Variables:
  N = Replication Factor (how many nodes store each piece of data)
  W = Write Quorum (how many nodes must ACK a write before success)
  R = Read Quorum (how many nodes must respond to a read)

THE RULE: R + W > N guarantees strong consistency
  (at least one node in the read set saw the latest write)

COMMON CONFIGURATIONS (N=3):

W=3, R=1: (Write all, read one)
  Writes: slow (wait for all 3 nodes), reads: very fast
  Can tolerate 0 node failures for writes, 2 for reads
  
W=1, R=3: (Write one, read all)
  Writes: very fast, reads: slow
  Can tolerate 2 node failures for writes, 0 for reads
  
W=2, R=2: (Quorum read and write) ← Most common
  Balanced. Can tolerate 1 node failure.
  R + W = 4 > 3 = N → Guaranteed to see latest write
  
W=1, R=1: (No quorum)
  Fastest, but eventual consistency only
  Used when speed is paramount and staleness is acceptable

CASSANDRA CONSISTENCY LEVELS:
  ONE: Just one node must ACK
  QUORUM: Majority must ACK  
  ALL: Every node must ACK
  LOCAL_QUORUM: Quorum within local datacenter only
  EACH_QUORUM: Quorum in each datacenter
  
EXAMPLE DECISIONS:
  User timeline (AP, speed): W=1, R=1 (eventual)
  User account balance (CP, safe): W=QUORUM, R=QUORUM
  User session (AP + read-own-writes): W=QUORUM, R=ONE (with session token)
```

---

## DAY 21: Replication Strategies

### Core Concepts

```
SINGLE-LEADER REPLICATION (Master-Slave):

  All writes → Leader → asynchronously replicated to Followers
  Reads: can go to any node
  
  Followers are read replicas (scale reads horizontally)
  
  PROBLEMS:
  - If leader dies: elect new leader (failover) = brief downtime
  - Replication lag: reads from replica may be stale
  - "Read your own writes" broken: write to leader, read from replica = old value
  
  SOLUTIONS:
  - Read from leader after writes (breaks read scaling)
  - Session token: include write timestamp, route reads to nodes that caught up
  - Replica lag monitoring with alert threshold
  
  USED BY: PostgreSQL, MySQL, MongoDB primary-secondary

MULTI-LEADER REPLICATION:

  Multiple nodes can accept writes.
  Each node replicates to others.
  
  PROBLEM: Write conflicts
  User A (in NYC) sets name = "Alice" on Leader 1
  User A (in London, same user) sets name = "Alicia" on Leader 2
  Both commit. Now leaders disagree. CONFLICT.
  
  RESOLUTION STRATEGIES:
  Last Write Wins (LWW): Use timestamp. Most recent wins.
    Problem: Clock skew! Wrong timestamp = wrong winner.
  
  Application-level: Return both values, let user pick.
    Used by: CouchDB
  
  CRDT (Conflict-free Replicated Data Types): Data structures that merge automatically.
    Counters, sets, maps with specific merge rules.
    Used by: Redis CRDT, collaborative editors
  
  USED BY: CouchDB, some Cassandra topologies, multi-region setups

LEADERLESS REPLICATION (Dynamo-style):

  Any node can accept a write.
  Write to W nodes simultaneously.
  Read from R nodes simultaneously.
  
  ANTI-ENTROPY: Background process compares and syncs replicas
  GOSSIP PROTOCOL: Nodes share state information (epidemic algorithm)
  
  USED BY: Amazon DynamoDB, Apache Cassandra, Riak
```

---

## DAY 22: Sharding — Horizontal Scaling

```
SHARDING = Split data across multiple database nodes.
Each node holds a SUBSET of the data.
Together they hold all of it.

WHY SHARD?
  - Single database node limit: ~TBs of data, ~100K ops/second
  - At Facebook/Twitter scale: need PBs of data, millions of ops/second
  - Solution: split data across N nodes, each handles 1/N of load

SHARD KEY SELECTION (THE MOST IMPORTANT DECISION):

Bad Key: timestamp or sequential ID
  → All new writes go to ONE shard (the latest) = "hotspot"
  → That shard becomes overwhelmed while others sit idle
  
Bad Key: user's country
  → Uneven distribution (more US users than Iceland users)
  → "Elephant" shard problem
  
Good Key: hash(user_id) % num_shards
  → Uniform distribution (hash distributes evenly)
  → No hotspots
  
TRADEOFF: Hash-based sharding makes RANGE QUERIES hard
  "Get all users with user_id between 1000 and 2000"
  These are scattered across all shards!
  Must query ALL shards and merge = N times the work

CROSS-SHARD QUERIES (The Hardest Problem):
  "Find all orders for users in California"
  If sharded by user_id: California users are on ALL shards
  Must query ALL shards and merge = expensive
  
  SOLUTIONS:
  1. Shard by the most common query dimension (user_id if most queries are by user)
  2. Denormalize: store user_location in orders table
  3. Separate analytics cluster with different partitioning scheme
  4. Application-level: scatter-gather across all shards

RESHARDING (The Nightmare):
  Your 10-shard cluster fills up. You add shard 11.
  Now hash(user_id) % 11 → different node than before!
  Must MOVE data from old nodes to new ones.
  
  SOLUTION: Consistent Hashing (tomorrow's topic)
```

---

## DAY 23: Consistent Hashing — The Elastic Solution

### Complete Implementation

```python
# Save as: phase-2-distributed/sharding/consistent_hash.py

import hashlib
from sortedcontainers import SortedDict
from collections import defaultdict
from typing import Optional, Dict, List

class ConsistentHashRing:
    """
    Consistent Hashing implementation.
    
    Traditional hash: hash(key) % N
    - Add node: N changes → ALL keys must move
    
    Consistent Hashing:
    - Keys and nodes both placed on a ring
    - Key → nearest node clockwise
    - Add node: only keys BETWEEN the new node and its predecessor move
    - Remove node: only that node's keys move to next node clockwise
    
    Used by: Amazon DynamoDB, Apache Cassandra, Chord DHT,
             Nginx upstream load balancer, Memcached clients
    """
    def __init__(self, virtual_nodes: int = 150):
        self.virtual_nodes = virtual_nodes
        self.ring: SortedDict[int, str] = SortedDict()  # position → node_id
        self.nodes: Dict[str, dict] = {}  # node_id → metadata
    
    def _hash(self, key: str) -> int:
        """Consistent hash using MD5 (stable across runs)."""
        return int(hashlib.md5(key.encode()).hexdigest(), 16)
    
    def add_node(self, node_id: str, capacity: int = 100) -> None:
        """Add a node. Higher capacity → more virtual nodes → more keys."""
        # Scale virtual nodes by capacity (heterogeneous hardware support)
        vnodes = int(self.virtual_nodes * (capacity / 100))
        self.nodes[node_id] = {"capacity": capacity, "virtual_nodes": vnodes}
        
        for i in range(vnodes):
            position = self._hash(f"{node_id}:vnode:{i}")
            self.ring[position] = node_id
        
        print(f"Added node '{node_id}' with {vnodes} virtual positions "
              f"(capacity={capacity}%)")
    
    def remove_node(self, node_id: str) -> None:
        """Remove a node. Its keys automatically go to the next node."""
        if node_id not in self.nodes:
            return
        
        vnodes = self.nodes[node_id]["virtual_nodes"]
        for i in range(vnodes):
            position = self._hash(f"{node_id}:vnode:{i}")
            self.ring.pop(position, None)
        
        del self.nodes[node_id]
        print(f"Removed node '{node_id}'")
    
    def get_node(self, key: str) -> Optional[str]:
        """Get the node responsible for a key."""
        if not self.ring:
            return None
        
        position = self._hash(key)
        keys = list(self.ring.keys())
        
        # Binary search for first position >= hash(key)
        idx = self.ring.bisect_right(position)
        if idx == len(keys):
            idx = 0  # Wrap around the ring
        
        return self.ring[keys[idx]]
    
    def get_nodes(self, key: str, n: int = 3) -> List[str]:
        """Get N nodes for a key (for replication)."""
        if not self.ring:
            return []
        
        position = self._hash(key)
        keys = list(self.ring.keys())
        idx = self.ring.bisect_right(position)
        
        result = []
        seen = set()
        for i in range(len(keys)):
            node = self.ring[keys[(idx + i) % len(keys)]]
            if node not in seen:
                result.append(node)
                seen.add(node)
            if len(result) == n:
                break
        return result
    
    def distribution_report(self, num_keys: int = 100_000) -> None:
        """Show how evenly keys are distributed."""
        from collections import Counter
        counts = Counter(self.get_node(f"key:{i}") for i in range(num_keys))
        
        print(f"\n=== Distribution Report ({num_keys:,} keys, {len(self.nodes)} nodes) ===")
        for node, count in sorted(counts.items(), key=lambda x: -x[1]):
            pct = count / num_keys * 100
            bar = "█" * int(pct / 2)
            print(f"  {node:20s}: {count:6,} keys ({pct:.1f}%) {bar}")
    
    def measure_data_movement(self, key_count: int = 100_000) -> None:
        """Measure what fraction of keys move when adding a node."""
        # Record current assignments
        before = {f"key:{i}": self.get_node(f"key:{i}") for i in range(key_count)}
        
        # Add a new node
        new_node = f"node-{len(self.nodes)+1}"
        self.add_node(new_node)
        
        # Compare assignments
        after = {f"key:{i}": self.get_node(f"key:{i}") for i in range(key_count)}
        moved = sum(1 for k in before if before[k] != after[k])
        
        print(f"\n=== Data Movement Analysis ===")
        print(f"Keys before: {key_count:,}")
        print(f"Keys that moved: {moved:,} ({moved/key_count*100:.1f}%)")
        print(f"Expected minimum (1/N of keys): {key_count/len(self.nodes):,.0f} "
              f"({100/len(self.nodes):.1f}%)")
        print("(Consistent hashing minimizes movement to ~1/N)")


# DEMONSTRATION
ring = ConsistentHashRing(virtual_nodes=150)

print("=== Phase 1: Starting with 3 Nodes ===")
ring.add_node("server-1", capacity=100)
ring.add_node("server-2", capacity=100)
ring.add_node("server-3", capacity=100)
ring.distribution_report()

print("\n=== Phase 2: Heterogeneous Hardware ===")
ring2 = ConsistentHashRing(virtual_nodes=100)
ring2.add_node("small-server",  capacity=50)   # Gets fewer virtual nodes
ring2.add_node("medium-server", capacity=100)
ring2.add_node("large-server",  capacity=200)  # Gets more virtual nodes
ring2.distribution_report()

print("\n=== Phase 3: Data Movement When Scaling ===")
ring3 = ConsistentHashRing(virtual_nodes=150)
ring3.add_node("server-A")
ring3.add_node("server-B")
ring3.add_node("server-C")
ring3.measure_data_movement(50_000)
```

---

## DAYS 24–25: PROJECT 2 — Distributed Key-Value Store

### Architecture

```
Your distributed KV store uses Consistent Hashing + Quorum reads

                        CLIENT
                           │
                    ┌──────▼──────┐
                    │  KV Client  │  Knows about all nodes
                    │  Uses       │  Computes shard via ConsistentHash
                    │  W=2, R=2   │  Sends to N=3 replicas
                    └──────┬──────┘
                           │
         ┌─────────────────┼─────────────────┐
         │                 │                 │
   ┌─────▼─────┐     ┌─────▼─────┐     ┌─────▼─────┐
   │  Node A   │     │  Node B   │     │  Node C   │
   │ :9001     │     │ :9002     │     │ :9003     │
   │ dict{}    │     │ dict{}    │     │ dict{}    │
   └───────────┘     └───────────┘     └───────────┘
   
Write flow (W=2):
  Client writes "user:1" = "Alice" to nodes A, B, C
  Wait for 2 ACKs → return success to user
  
Read flow (R=2):
  Client reads "user:1" from A and B
  Both return same version → return value
  If they disagree → return newest by timestamp (LWW)
```

---

## DAYS 26–30: Caching Deep Dive + CDNs + Probabilistic Structures

### Day 26: Caching Patterns

```
CACHE-ASIDE (Lazy Loading) — Most Common:
  1. App checks cache for key
  2. CACHE HIT: return value
  3. CACHE MISS: query database, store in cache, return value
  
  Pros: Only cache what's actually needed
  Cons: First request always slow (cache miss)
        Potential for stale data if cache not invalidated

WRITE-THROUGH:
  1. App writes to cache AND database simultaneously
  2. Every write = 2 operations (slower)
  
  Pros: Cache always up-to-date
  Cons: Many writes might cache data that's never read (waste)

WRITE-BACK (Write-Behind):
  1. App writes to cache only
  2. Cache asynchronously writes to database later
  
  Pros: Very fast writes
  Cons: Data loss if cache crashes before writing to DB

THUNDERING HERD PROBLEM:
  Popular cache key expires at midnight.
  10,000 users make requests at 00:00:01.
  All 10,000 miss the cache → all 10,000 query database simultaneously.
  Database crashes.
  
  SOLUTIONS:
  1. Jitter: Randomize TTL (TTL ± 20%) so not all expire at same time
  2. Lock: Only first thread recalculates, others wait
  3. Probabilistic Early Expiration (X-Fetch): 
     Start regenerating BEFORE expiry if p = β * δ * log(rand) < 0
  4. Background refresh: Never expire; refresh asynchronously before expiry
```

### Day 27: Implement LRU Cache

```python
# Save as: phase-2-distributed/caching/lru_cache.py
from collections import OrderedDict
from typing import Optional

class LRUCache:
    """
    O(1) get and put using OrderedDict (HashMap + DoublyLinkedList).
    
    WHY THIS DATA STRUCTURE:
    - HashMap: O(1) lookup by key
    - Doubly Linked List: O(1) move-to-front and remove-from-back
    
    REAL USAGE: Redis uses an approximated LRU (random sampling for speed)
    Used by: Redis, CPU page replacement, CDN edge cache eviction
    """
    def __init__(self, capacity: int):
        self.capacity = capacity
        self.cache = OrderedDict()
        self.hits = 0
        self.misses = 0
    
    def get(self, key) -> Optional[any]:
        if key not in self.cache:
            self.misses += 1
            return None
        # Move to end (most recently used)
        self.cache.move_to_end(key)
        self.hits += 1
        return self.cache[key]
    
    def put(self, key, value) -> None:
        if key in self.cache:
            self.cache.move_to_end(key)
        else:
            if len(self.cache) >= self.capacity:
                # Remove least recently used (front of OrderedDict)
                evicted_key, evicted_val = self.cache.popitem(last=False)
                # In a real system: log eviction for analysis
        self.cache[key] = value
    
    def stats(self) -> dict:
        total = self.hits + self.misses
        return {
            "hit_rate": f"{self.hits/max(total,1)*100:.1f}%",
            "hits": self.hits,
            "misses": self.misses,
            "current_size": len(self.cache),
        }

# Test with realistic access patterns
import random
cache = LRUCache(capacity=100)

# Simulate "hot" keys (80% of requests hit 20% of keys — Zipf distribution)
hot_keys = list(range(20))       # 20 hot keys
all_keys = list(range(1000))     # 1000 total keys

for i in range(10000):
    if random.random() < 0.8:
        key = random.choice(hot_keys)      # 80% of requests: hot key
    else:
        key = random.choice(all_keys)      # 20% of requests: any key
    
    if cache.get(key) is None:
        cache.put(key, f"value_{key}")     # Cache miss: load from "DB"

print("LRU Cache Statistics:")
for k, v in cache.stats().items():
    print(f"  {k}: {v}")
```

### Days 28–30: Redis Architecture, CDNs, Bloom Filters, HyperLogLog

```python
# Day 30: Bloom Filter — Space-efficient "definitely not / maybe" lookup
# Save as: phase-2-distributed/caching/bloom_filter.py

import hashlib
import math
from bitarray import bitarray  # pip install bitarray

class BloomFilter:
    """
    Bloom Filter: Probabilistic membership testing.
    
    "Is this URL in my list of malicious URLs?"
    - False NEGATIVE: impossible (if it's in the filter, it will always say YES)
    - False POSITIVE: possible (might say YES for something not in the filter)
    
    USED BY:
    - Google Chrome: SafeBrowsing (check malicious URLs client-side)
    - Cassandra: avoid disk reads for non-existent keys (before checking SSTables)
    - Akamai CDN: track which URLs are requested more than once (cache only popular items)
    - Bitcoin: SPV clients verify transactions without full blockchain
    
    SPACE EFFICIENCY:
    Storing 1M URLs exactly: 1M × 100 bytes/URL = 100MB
    Bloom filter for 1M URLs (1% false positive): ~9.6 bits/element = 1.2MB
    ~83x smaller!
    """
    def __init__(self, expected_items: int, false_positive_rate: float = 0.01):
        # Optimal filter size (bits)
        self.m = int(-expected_items * math.log(false_positive_rate) / (math.log(2) ** 2))
        # Optimal number of hash functions
        self.k = int((self.m / expected_items) * math.log(2))
        self.bit_array = bitarray(self.m)
        self.bit_array.setall(0)
        self.items_added = 0
        
        print(f"Bloom Filter: {expected_items:,} items, {false_positive_rate*100}% FPR")
        print(f"  Bit array size: {self.m:,} bits ({self.m/8/1024:.1f} KB)")
        print(f"  Hash functions: {self.k}")
    
    def _hash_positions(self, item: str):
        """Generate k different hash positions."""
        positions = []
        for i in range(self.k):
            h = int(hashlib.sha256(f"{item}:{i}".encode()).hexdigest(), 16)
            positions.append(h % self.m)
        return positions
    
    def add(self, item: str) -> None:
        for pos in self._hash_positions(item):
            self.bit_array[pos] = 1
        self.items_added += 1
    
    def might_contain(self, item: str) -> bool:
        """Returns True if item MIGHT be in set. False = definitely NOT in set."""
        return all(self.bit_array[pos] for pos in self._hash_positions(item))
    
    def false_positive_rate(self) -> float:
        """Current false positive probability."""
        return (1 - math.exp(-self.k * self.items_added / self.m)) ** self.k


# Demo: Malicious URL filter (like Google SafeBrowsing)
print("=== Malicious URL Bloom Filter ===")
bf = BloomFilter(expected_items=100_000, false_positive_rate=0.001)

# Add "known malicious" URLs
malicious_urls = [f"http://malware-site-{i}.evil" for i in range(100_000)]
for url in malicious_urls:
    bf.add(url)

# Test known malicious URL
url = "http://malware-site-12345.evil"
result = bf.might_contain(url)
print(f"\nKnown malicious URL: {result} (should be True)")

# Test safe URL
safe_url = "https://google.com"
result = bf.might_contain(safe_url)
print(f"Safe URL: {result} (should be False)")

# Measure actual false positive rate
false_positives = sum(1 for i in range(10_000)
                      if bf.might_contain(f"https://safe-site-{i}.com"))
print(f"\nEmpirical FPR: {false_positives/10_000*100:.2f}% (target: 0.1%)")
print(f"WITHOUT Bloom Filter: would need 10,000 database lookups")
print(f"WITH Bloom Filter: 0 database lookups for safe URLs (100% fast-path)")
```

---

---

# 🟡 PHASE 3: MNC COMPONENT DEEP DIVE (Days 31–50)

> **Goal:** Learn the internals of the specific tools that power Google, Meta, Amazon, and Discord. An L6 engineer doesn't just USE Kafka — they can explain WHY Kafka's log-based design beats traditional queues and WHEN to choose something else.

---

## DAYS 31–33: Database Storage Engines — B-Trees vs LSM Trees

### Core Concepts

```
B-TREE (Used by: PostgreSQL, MySQL, SQLite):

Structure: Balanced tree. Data stored in leaf nodes.
Each node: ~100-4000 pointers (branching factor)
Depth: ~3-4 levels for 1M records (very shallow)

READ PERFORMANCE:
  Find any record: O(log n) ≈ 3-4 disk reads
  Range query: traverse leaf nodes sequentially (fast)
  
WRITE PERFORMANCE:
  Insert anywhere in sorted order
  May require rebalancing (expensive: read-modify-write)
  EACH INSERT may cause 2-3 disk writes (read page + modify + write back)
  
OPTIMIZED FOR: Mixed read/write workloads, SQL databases

LSM TREE (Log-Structured Merge Tree — Cassandra, RocksDB, LevelDB):

Structure:
  Level 0: MemTable (in-memory write buffer)
  Level 1: SSTables (Sorted String Tables on disk) — recently flushed
  Level 2: Larger SSTables (from merging Level 1)
  ...increasing size levels

WRITE FLOW:
  1. Write arrives → added to MemTable (in-memory hash map) → instant!
  2. Also append to Write-Ahead Log (WAL) for crash recovery
  3. When MemTable is full: flush to SSTable (sorted, immutable file on disk)
  4. Compaction: background process merges SSTables → larger sorted files
  
  KEY INSIGHT: ALL writes are sequential (append-only). No random I/O!
  Sequential writes: ~500 MB/s on SSD
  Random writes: ~5 MB/s on HDD, ~100 MB/s on SSD
  
READ FLOW (the downside):
  Must check MemTable + ALL SSTables (many levels!)
  Bloom filters reduce false positives
  Compaction reduces levels, but read amplification is real
  
TRADEOFF:
  LSM: Write Amplification < Read Amplification
  B-Tree: Read Amplification < Write Amplification

MNC CHOICE:
  Write-heavy workloads (logs, events, IoT, time-series) → LSM (Cassandra/RocksDB)
  Read-heavy with complex queries (OLTP, analytics) → B-Tree (PostgreSQL/MySQL)
  Discord: Chose Cassandra (LSM) for messages (insert-heavy, reads by range)
  Uber: Chose LSM-based store for trip data (high write rate)
```

---

## DAYS 34–40: PROJECT 3 — Build Your Own Redis (Lite)

### Architecture

```
YOUR MINI-REDIS TCP SERVER

CLIENT (redis-cli)          YOUR REDIS SERVER
      │                              │
      │── *3\r\n$3\r\nSET\r\n... ──►│  Parse RESP protocol
      │                              │
      │                              │  Store in dict + check TTL
      │                              │
      │◄── +OK\r\n ─────────────────│  Return RESP response
      │                              │
      │── *2\r\n$3\r\nGET\r\n... ──►│  Lookup in dict
      │                              │
      │◄── $5\r\nhello\r\n ─────────│  Return value
```

### Implementation

```python
# Save as: projects/03-build-your-own-redis/server.py
# Compatible with redis-cli! Test with: redis-cli -p 7379 SET foo bar

import asyncio
import time
import logging
from typing import Dict, Optional, Tuple, Any

logging.basicConfig(level=logging.INFO)
log = logging.getLogger("mini-redis")

class RESPProtocol:
    """
    Redis Serialization Protocol (RESP) parser and builder.
    
    FORMAT:
    Simple String:  +OK\r\n
    Error:          -ERR message\r\n
    Integer:        :1000\r\n
    Bulk String:    $5\r\nhello\r\n  ($ = length prefix)
    Array:          *3\r\n$3\r\nSET\r\n$3\r\nkey\r\n$5\r\nvalue\r\n
    Null:           $-1\r\n
    """
    
    @staticmethod
    def encode_simple_string(s: str) -> bytes:
        return f"+{s}\r\n".encode()
    
    @staticmethod
    def encode_error(msg: str) -> bytes:
        return f"-ERR {msg}\r\n".encode()
    
    @staticmethod
    def encode_integer(n: int) -> bytes:
        return f":{n}\r\n".encode()
    
    @staticmethod
    def encode_bulk_string(s: Optional[str]) -> bytes:
        if s is None:
            return b"$-1\r\n"
        encoded = s.encode('utf-8')
        return f"${len(encoded)}\r\n".encode() + encoded + b"\r\n"
    
    @staticmethod
    async def parse_request(reader: asyncio.StreamReader) -> Optional[list]:
        """Parse one RESP command from the stream."""
        try:
            line = await reader.readline()
            if not line:
                return None
            
            line = line.strip().decode()
            if line.startswith('*'):
                # Array command: *3\r\n$3\r\nSET\r\n...
                num_args = int(line[1:])
                args = []
                for _ in range(num_args):
                    length_line = (await reader.readline()).strip().decode()
                    if length_line.startswith('$'):
                        length = int(length_line[1:])
                        data = await reader.readexactly(length + 2)  # +2 for \r\n
                        args.append(data[:-2].decode('utf-8'))
                return args
            elif line.startswith('+') or line.startswith('-') or line.startswith(':'):
                return [line[1:]]
        except (asyncio.IncompleteReadError, ValueError, UnicodeDecodeError):
            return None
        return None


class MiniRedis:
    """
    A Redis-compatible key-value store.
    
    Supports: SET, GET, DEL, EXISTS, EXPIRE, TTL, INCR, LPUSH, LRANGE, PING, INFO
    """
    def __init__(self):
        self.data: Dict[str, Any] = {}
        self.expiry: Dict[str, float] = {}
        self.start_time = time.time()
        self.stats = {"total_commands": 0, "keyspace_hits": 0, "keyspace_misses": 0}
    
    def _is_expired(self, key: str) -> bool:
        if key in self.expiry:
            if time.time() > self.expiry[key]:
                del self.data[key]
                del self.expiry[key]
                return True
        return False
    
    def _check_key(self, key: str) -> bool:
        """Returns True if key exists and is not expired."""
        if key not in self.data:
            return False
        return not self._is_expired(key)
    
    async def _cleanup_expired_keys(self):
        """Active expiry: background task removes expired keys periodically."""
        while True:
            await asyncio.sleep(1)
            expired = [k for k in list(self.expiry.keys())
                      if time.time() > self.expiry[k]]
            for key in expired:
                self.data.pop(key, None)
                self.expiry.pop(key, None)
            if expired:
                log.debug(f"Cleaned up {len(expired)} expired keys")
    
    def execute_command(self, args: list) -> bytes:
        self.stats["total_commands"] += 1
        cmd = args[0].upper()
        
        if cmd == "PING":
            return RESPProtocol.encode_simple_string("PONG")
        
        elif cmd == "SET":
            if len(args) < 3:
                return RESPProtocol.encode_error("wrong number of arguments")
            key, value = args[1], args[2]
            self.data[key] = value
            
            # Handle EX (expire in seconds): SET key val EX 60
            for i in range(3, len(args) - 1):
                if args[i].upper() == "EX":
                    self.expiry[key] = time.time() + float(args[i + 1])
                elif args[i].upper() == "PX":
                    self.expiry[key] = time.time() + float(args[i + 1]) / 1000
            
            return RESPProtocol.encode_simple_string("OK")
        
        elif cmd == "GET":
            if len(args) < 2:
                return RESPProtocol.encode_error("wrong number of arguments")
            key = args[1]
            if self._check_key(key):
                self.stats["keyspace_hits"] += 1
                return RESPProtocol.encode_bulk_string(str(self.data[key]))
            self.stats["keyspace_misses"] += 1
            return RESPProtocol.encode_bulk_string(None)
        
        elif cmd == "DEL":
            deleted = 0
            for key in args[1:]:
                if key in self.data:
                    del self.data[key]
                    self.expiry.pop(key, None)
                    deleted += 1
            return RESPProtocol.encode_integer(deleted)
        
        elif cmd == "EXISTS":
            count = sum(1 for k in args[1:] if self._check_key(k))
            return RESPProtocol.encode_integer(count)
        
        elif cmd == "EXPIRE":
            key, seconds = args[1], float(args[2])
            if self._check_key(key):
                self.expiry[key] = time.time() + seconds
                return RESPProtocol.encode_integer(1)
            return RESPProtocol.encode_integer(0)
        
        elif cmd == "TTL":
            key = args[1]
            if not self._check_key(key):
                return RESPProtocol.encode_integer(-2)  # Key doesn't exist
            if key not in self.expiry:
                return RESPProtocol.encode_integer(-1)  # No expiry
            remaining = int(self.expiry[key] - time.time())
            return RESPProtocol.encode_integer(max(0, remaining))
        
        elif cmd == "INCR":
            key = args[1]
            if not self._check_key(key):
                self.data[key] = "1"
                return RESPProtocol.encode_integer(1)
            try:
                val = int(self.data[key]) + 1
                self.data[key] = str(val)
                return RESPProtocol.encode_integer(val)
            except (ValueError, TypeError):
                return RESPProtocol.encode_error("value is not an integer")
        
        elif cmd == "LPUSH":
            key = args[1]
            if key not in self.data:
                self.data[key] = []
            elif not isinstance(self.data[key], list):
                return RESPProtocol.encode_error("WRONGTYPE operation")
            for val in args[2:]:
                self.data[key].insert(0, val)
            return RESPProtocol.encode_integer(len(self.data[key]))
        
        elif cmd == "LRANGE":
            key, start, stop = args[1], int(args[2]), int(args[3])
            if key not in self.data:
                return b"*0\r\n"
            lst = self.data[key]
            if stop == -1:
                stop = len(lst) - 1
            items = lst[start:stop + 1]
            result = f"*{len(items)}\r\n".encode()
            for item in items:
                result += RESPProtocol.encode_bulk_string(item)
            return result
        
        elif cmd == "INFO":
            uptime = int(time.time() - self.start_time)
            info = (
                f"# Server\r\nredis_version:mini-redis-1.0\r\nuptime_in_seconds:{uptime}\r\n"
                f"# Stats\r\ntotal_commands_processed:{self.stats['total_commands']}\r\n"
                f"keyspace_hits:{self.stats['keyspace_hits']}\r\n"
                f"keyspace_misses:{self.stats['keyspace_misses']}\r\n"
                f"# Keyspace\r\ndb0:keys={len(self.data)}\r\n"
            )
            return RESPProtocol.encode_bulk_string(info)
        
        else:
            return RESPProtocol.encode_error(f"unknown command '{cmd}'")


async def handle_client(reader: asyncio.StreamReader,
                        writer: asyncio.StreamWriter,
                        redis: MiniRedis):
    addr = writer.get_extra_info('peername')
    log.info(f"Client connected: {addr}")
    try:
        while True:
            args = await RESPProtocol.parse_request(reader)
            if args is None:
                break
            log.debug(f"Command: {args}")
            response = redis.execute_command(args)
            writer.write(response)
            await writer.drain()
    except (asyncio.IncompleteReadError, ConnectionResetError):
        pass
    finally:
        log.info(f"Client disconnected: {addr}")
        writer.close()


async def main():
    redis = MiniRedis()
    asyncio.create_task(redis._cleanup_expired_keys())
    
    server = await asyncio.start_server(
        lambda r, w: handle_client(r, w, redis),
        host='0.0.0.0', port=7379
    )
    log.info("Mini-Redis server on port 7379")
    log.info("Test with: redis-cli -p 7379")
    log.info("Commands: SET key value [EX seconds], GET key, TTL key, INCR key")
    
    async with server:
        await server.serve_forever()

if __name__ == "__main__":
    asyncio.run(main())
```

```bash
# Test your Mini-Redis with the real redis-cli
redis-cli -p 7379 SET mykey "hello world" EX 60
redis-cli -p 7379 GET mykey
redis-cli -p 7379 TTL mykey
redis-cli -p 7379 INCR counter
redis-cli -p 7379 LPUSH mylist a b c d
redis-cli -p 7379 LRANGE mylist 0 -1
redis-cli -p 7379 INFO
```

---

## DAYS 41–45: Kafka Architecture + Event-Driven Patterns

### Day 41: Kafka Internals

```
KAFKA ARCHITECTURE (Why It's Fast):

TOPIC: A named channel for messages
  topic: "user-events"
  topic: "order-created"
  topic: "payment-processed"

PARTITION: Ordered, immutable sequence of messages
  topic "user-events" → Partition 0, Partition 1, Partition 2
  
  WHY PARTITION?
  - Parallelism: Different consumers read different partitions simultaneously
  - Ordering guarantee: Messages within ONE partition are ordered
  - No global ordering across partitions!

OFFSET: Position of a message in a partition (starts at 0)
  Partition 0: [msg0][msg1][msg2][msg3]...
               offset=0  1    2    3
  
  Consumers TRACK their own offset (not the broker's job)
  Rewind by resetting offset: replay all historical events!

CONSUMER GROUP:
  Multiple consumers sharing work from a topic.
  Each partition consumed by exactly ONE consumer in a group.
  3 partitions + 3 consumers = 1 partition per consumer (perfect)
  3 partitions + 2 consumers = one consumer reads 2 partitions
  3 partitions + 4 consumers = one consumer idle

WHY KAFKA IS FAST:
  1. Sequential I/O: Messages appended to log (no random seeks)
  2. Zero-Copy: OS copies data directly from file to network (bypass CPU)
     Normal: Disk → Kernel → User Space → Kernel → Network
     Zero-Copy: Disk → Kernel → Network (2 copies instead of 4)
  3. Batching: Multiple messages in one network request
  4. Compression: Compress batches before sending

DELIVERY SEMANTICS:
  At-most-once: ACK before processing (can lose messages)
  At-least-once: ACK after processing (can duplicate messages)
  Exactly-once: Kafka Transactions (expensive but possible)
  
  IDEMPOTENCY: Design consumers to handle duplicates gracefully
  (Processing same message twice = same result)
```

### Day 42: Event Sourcing and CQRS

```
EVENT SOURCING:

Traditional: Store current STATE
  Users table: {id: 1, balance: 100}
  Update → replace the value

Event Sourcing: Store EVENTS (what happened)
  Event log:
    {event: "AccountCreated", amount: 200, timestamp: T1}
    {event: "Withdrawal",    amount: 50,  timestamp: T2}
    {event: "Deposit",       amount: -50, timestamp: T3}
  Current balance: replay all events → 200 - 50 - 50 = 100

BENEFITS:
  - Complete audit trail (required for banking, healthcare)
  - Time travel: replay events to any point in time
  - Debugging: know EXACTLY what caused current state
  - Projections: build different views from same event log

CQRS (Command Query Responsibility Segregation):

PROBLEM:
  Same database handles both writes (commands) and reads (queries)
  Writes: complex business logic, need consistency
  Reads: complex joins, aggregations, need speed
  
  They have conflicting requirements!

SOLUTION: Separate write model from read model
  
  Write side (Command Model):
  → Receives commands ("PlaceOrder", "UpdateProfile")
  → Validates business rules
  → Emits events ("OrderPlaced", "ProfileUpdated")
  → Stored in event store (Kafka or event DB)
  
  Read side (Query Model / Projection):
  → Consumes events from write side
  → Builds denormalized, read-optimized views
  → Can have MULTIPLE projections from same events
    (dashboard view, reporting view, search view)
  → Eventually consistent with write side

USED BY:
  - Netflix: Event sourcing for viewing history
  - Amazon: Event sourcing for order management
  - LinkedIn: CQRS for member profiles vs. recruiter search
```

---

## DAYS 46–50: PROJECT 4 — Mini-Kafka (Distributed Log)

### Architecture

```
YOUR MINI KAFKA (Append-only distributed log)

Producer → [Server] → append to log file
Consumer ← [Server] ← read from offset

LOG FILE STRUCTURE:
/logs/topic-A/partition-0.log
  [msg_len:4][msg_data:N]\n
  [msg_len:4][msg_data:N]\n
  ...

INDEX FILE:
/logs/topic-A/partition-0.index
  [offset:8][byte_position:8]
  (Binary file for O(1) seek to any offset)

MULTI-PARTITION:
  topic "events" → partition 0, 1, 2
  partition(key) = hash(key) % num_partitions
  Same key → always same partition → ordered for that key
```

---

---

# 🔵 PHASE 4: PRODUCTION SYSTEM DESIGN (Days 51–70)

> **Goal:** Synthesize everything into complete system designs. Learn the frameworks, tradeoffs, and MNC-standard patterns for designing any system at scale.

---

## DAYS 51–55: Production Architecture Patterns

### Day 51: Microservices Architecture Patterns

```
SERVICE DISCOVERY:
  Problem: Microservices start/stop dynamically. How does Service A find Service B's IP?
  
  Client-Side Discovery (Netflix Ribbon):
    Service A asks Service Registry for Service B's address
    Service A picks one (load balances itself)
    
  Server-Side Discovery (AWS ALB):
    Service A asks Load Balancer
    LB asks Registry, picks a backend, routes
    Service A doesn't know about registry at all
  
  Service Registry: Consul, etcd, Kubernetes DNS
  
API GATEWAY:
  Single entry point for all clients.
  Handles: authentication, rate limiting, SSL termination,
           request routing, request/response transformation,
           logging, caching.
  
  Nginx, Kong, AWS API Gateway, Envoy

CIRCUIT BREAKER PATTERN:
  Problem: Service A calls Service B. B is slow/down.
           A's thread pool fills up waiting for B.
           A becomes slow too. A's callers slow down. Cascade failure!
  
  Solution: Circuit Breaker wraps calls to B.
  CLOSED state: Normal operation. All calls go through.
  OPEN state: B failed 5 times in 30s. Fail FAST. Don't call B for 60s.
  HALF-OPEN state: After 60s, try one request. If success: CLOSED. If fail: OPEN.
  
  Used by: Netflix Hystrix, Resilience4j
```

### Day 52: Observability — Three Pillars

```
THE THREE PILLARS OF OBSERVABILITY:

1. METRICS (Prometheus + Grafana):
   Numerical time-series data.
   "95th percentile response time = 250ms"
   "Error rate = 0.1%"
   "Database connections in use = 78/100"
   
   KEY METRICS TO TRACK:
   Request Rate: requests/second
   Error Rate: errors/total requests × 100
   Latency: p50, p95, p99 response times
   Saturation: CPU %, memory %, thread pool %, connection pool %
   
   (Known as RED metrics: Rate, Errors, Duration)

2. LOGS (ELK Stack: Elasticsearch + Logstash + Kibana):
   Text records of what happened.
   "2024-01-01 10:00:00 ERROR PaymentService: Card declined for user 12345"
   
   BEST PRACTICES:
   Structured logs (JSON), not raw strings
   Include: request_id (for tracing), user_id, service_name
   Log levels: DEBUG, INFO, WARN, ERROR (don't log DEBUG in production)
   
3. TRACES (OpenTelemetry + Jaeger):
   Follow ONE request across MULTIPLE services.
   
   Request ID: abc-123
   spans:
     └── API Gateway (5ms)
         └── Auth Service (10ms)
             └── User Service (15ms)
                 └── Database (12ms)
         └── Order Service (50ms)
             └── Database (30ms)
             └── Kafka Publish (8ms)
   Total: 80ms
   
   Without tracing: "The request took 80ms" — but WHERE?
   With tracing: "Order Service → Database took 30ms" — NOW FIX IT

SLOs/SLAs/SLIs:
  SLI: Service Level Indicator — the actual measurement
       "99.5% of requests succeeded in last 30 days"
  SLO: Service Level Objective — the target
       "99.9% of requests must succeed"
  SLA: Service Level Agreement — the contract with consequences
       "If we fall below 99.9%, customer gets 10% discount"
  
  ERROR BUDGET:
       30 days × 24h × 60min = 43,200 minutes
       99.9% uptime = 0.1% downtime allowed = 43.2 minutes/month
       If you've used 43 minutes already: STOP all risky deployments!
```

### Day 53: Rate Limiting Algorithms

```python
# Save as: phase-4-production/rate_limiting/sliding_window.py

import time
import redis
from typing import Tuple

class SlidingWindowRateLimiter:
    """
    Sliding Window rate limiter using Redis Sorted Sets.
    
    More accurate than fixed window (no burst at window boundary).
    Used by: Stripe, GitHub, Twitter API
    
    ALGORITHM:
    1. Key = f"rate_limit:{user_id}"
    2. Score = current timestamp (milliseconds)
    3. Member = unique request ID
    
    On each request:
    1. Remove old entries (outside the window)
    2. Count remaining entries
    3. If count < limit: add new entry + allow
    4. If count >= limit: deny
    """
    def __init__(self, redis_client, limit: int, window_seconds: int):
        self.redis = redis_client
        self.limit = limit
        self.window_ms = window_seconds * 1000
    
    def is_allowed(self, identifier: str) -> Tuple[bool, dict]:
        """Check if request should be allowed. Returns (allowed, info)."""
        key = f"rate_limit:{identifier}"
        now_ms = int(time.time() * 1000)
        window_start = now_ms - self.window_ms
        
        pipe = self.redis.pipeline()
        # Remove old entries
        pipe.zremrangebyscore(key, 0, window_start)
        # Count current entries
        pipe.zcard(key)
        # Add this request (if we decide to allow it)
        pipe.zadd(key, {f"{now_ms}:{id(object())}": now_ms})
        # Set TTL on key (cleanup)
        pipe.expire(key, self.window_ms // 1000 + 1)
        results = pipe.execute()
        
        current_count = results[1]  # Count before this request
        
        if current_count >= self.limit:
            # Remove the entry we just added (we're denying this request)
            self.redis.zrem(key, f"{now_ms}:{id(object())}")
            retry_after = self.window_ms // 1000
            return False, {
                "allowed": False,
                "limit": self.limit,
                "current": current_count,
                "retry_after_seconds": retry_after,
                "error": "Rate limit exceeded"
            }
        
        return True, {
            "allowed": True,
            "limit": self.limit,
            "remaining": self.limit - current_count - 1,
            "window_seconds": self.window_ms // 1000
        }


class TokenBucketRateLimiter:
    """
    Token Bucket: Allows bursting but controls average rate.
    
    ALGORITHM:
    - Bucket has capacity N tokens
    - Tokens refill at rate R tokens/second
    - Each request consumes 1 token
    - If bucket empty: deny request
    
    ADVANTAGE over sliding window:
    - Allows bursts (good for legitimate traffic spikes)
    - A user can "save up" for a burst
    
    Used by: AWS API Gateway, many CDN rate limiters
    """
    def __init__(self, redis_client, capacity: int, refill_rate: float):
        self.redis = redis_client
        self.capacity = capacity       # Max tokens
        self.refill_rate = refill_rate # Tokens per second
    
    def is_allowed(self, identifier: str) -> Tuple[bool, dict]:
        key = f"token_bucket:{identifier}"
        now = time.time()
        
        # Lua script for atomicity (no race conditions)
        lua_script = """
        local key = KEYS[1]
        local capacity = tonumber(ARGV[1])
        local refill_rate = tonumber(ARGV[2])
        local now = tonumber(ARGV[3])
        
        local bucket = redis.call('HMGET', key, 'tokens', 'last_refill')
        local tokens = tonumber(bucket[1]) or capacity
        local last_refill = tonumber(bucket[2]) or now
        
        -- Refill tokens based on elapsed time
        local elapsed = now - last_refill
        tokens = math.min(capacity, tokens + elapsed * refill_rate)
        
        if tokens >= 1 then
            tokens = tokens - 1
            redis.call('HMSET', key, 'tokens', tokens, 'last_refill', now)
            redis.call('EXPIRE', key, 3600)
            return {1, math.floor(tokens)}  -- Allowed
        else
            redis.call('HMSET', key, 'tokens', tokens, 'last_refill', now)
            redis.call('EXPIRE', key, 3600)
            return {0, 0}  -- Denied
        end
        """
        result = self.redis.eval(lua_script, 1, key,
                                 self.capacity, self.refill_rate, now)
        allowed = result[0] == 1
        remaining = result[1]
        
        return allowed, {"allowed": allowed, "remaining_tokens": remaining,
                         "capacity": self.capacity}
```

---

## DAYS 55–70: System Design Deep Dives

### Day 55–57: Design Twitter at Scale

```
TWITTER SYSTEM DESIGN — COMPLETE WALKTHROUGH

STEP 1: REQUIREMENTS
  Functional:
  - Post tweets (280 chars + media)
  - Follow/unfollow users
  - Home timeline (tweets from followed users)
  - Like, retweet, reply
  - Search tweets
  - Notifications
  
  Non-Functional (Given in interview):
  - 300M DAU
  - 500M tweets/day = 5,800 writes/sec
  - Read-heavy: 120:1 read/write ratio
  - Latency: timeline load < 150ms
  - Availability: 99.99%

STEP 2: ESTIMATION
  Tweets/sec = 500M / 86,400 ≈ 5,800 writes/sec
  Timeline reads/sec = 300M × 10 timeline views / 86,400 = 34,700/sec
  Storage: 5,800 tweets/sec × 1KB = 5.8MB/sec = 500GB/day
  Media: 10% have images × 100KB = 580MB/sec = 50TB/day

STEP 3: HIGH-LEVEL ARCHITECTURE

Client → CDN (static assets)
      → Load Balancer
      → API Gateway (auth, rate limiting)
         → Tweet Service  (write tweets)
         → Timeline Service  (read timelines)
         → User Service  (follow/unfollow)
         → Search Service  (tweet search)
         → Notification Service

STEP 4: THE HARD PROBLEM — HOME TIMELINE

OPTION A: Pull Model (Compute on Read)
  "Who does Alice follow? Give me their last 20 tweets."
  SELECT tweets FROM tweets WHERE user_id IN (SELECT following FROM follows WHERE user_id=alice) ORDER BY created_at DESC LIMIT 20
  
  Problem at scale:
  - Alice follows 2000 people → 2000 DB lookups or one massive IN query
  - 34,700 timeline requests/sec × 2000 = 69M sub-queries/sec
  - Impossible to scale

OPTION B: Push Model / Fan-Out on Write
  When Bob (100 followers) tweets:
  → Tweet saved to DB
  → Async: for each of Bob's 100 followers: add tweet_id to their timeline cache
  → Alice's timeline in Redis: [tweet_id_bob, tweet_id_carol, ...]
  
  Alice reads timeline: ONE Redis read of her sorted set → lightning fast
  
  Problem: Celebrity with 100M followers:
  → 1 tweet × 100M pushes = 100M Redis writes
  → Can take minutes. Viral tweet causes massive lag.

OPTION C: Hybrid (Twitter's actual approach)
  Regular users (< 10K followers): Fan-out on write (Option B)
  Celebrities (> 10K followers): No pre-computed timeline push
  
  When Alice reads her timeline:
  1. Fetch Alice's pre-computed timeline from Redis (from non-celeb follows)
  2. ALSO: For each celebrity Alice follows, fetch their latest tweets in parallel
  3. Merge + sort all results
  4. Return to Alice
  
  Result: Fast for regular users (Redis), celebrities don't cause cascading writes.

DATABASES:
  Tweets: Cassandra (wide-column, write-heavy, partitioned by tweet_id)
  Timelines: Redis Sorted Set (tweet_id as score=timestamp)
  Followers/Following: PostgreSQL or Cassandra
  Media: S3-compatible object storage + CDN
  Search: Elasticsearch (inverted index for full-text)

STEP 5: TRADEOFFS
  "This design uses eventual consistency for timelines.
   A tweet might appear 100-500ms after posting.
   We chose AP over CP for this feature.
   For user authentication (logins), we use strong consistency."
```

### Day 58–60: Design YouTube

```
YOUTUBE SYSTEM DESIGN — VIDEO UPLOAD & STREAMING

SCALE:
  500 hours of video uploaded per minute
  1 billion video views per day = 11,500 views/sec

VIDEO UPLOAD FLOW:
  1. User uploads raw video → Upload Service
  2. Upload Service stores raw file in object storage (temp bucket)
  3. Publishes "VideoUploaded" event to Kafka
  
  4. Transcoding Service (consumes Kafka event):
     - Uses FFmpeg to transcode: 360p, 480p, 720p, 1080p, 4K
     - Can split into parallel tasks (different workers for different resolutions)
     - Each resolution → separate file in object storage
  
  5. Metadata Service: create video record (title, description, thumbnail)
  6. Thumbnails: AI model generates thumbnail options
  7. CDN Pre-population: push popular videos to edge nodes proactively

VIDEO STREAMING (Adaptive Bitrate):
  HLS (HTTP Live Streaming) or DASH:
  - Video split into small chunks (2-10 seconds each)
  - Each chunk encoded at multiple bitrates
  - Player checks bandwidth every few seconds
  - Downloads next chunk at appropriate bitrate
  
  Good network: 1080p chunks
  Network degrades: switch to 720p chunks → no buffering
  Network drops: 360p chunks → keeps playing

CDN STRATEGY:
  - 80% of views are popular videos (Zipf distribution)
  - Push popular videos to edge nodes (low latency)
  - Long-tail videos: pull from origin on first request, cache at edge
  
  Cache headers on video chunks:
  Cache-Control: max-age=31536000 (cache for 1 year — chunks never change!)
```

### Day 61–65: PROJECT 5 — Intelligent URL Shortener

```
URL SHORTENER SYSTEM DESIGN

REQUIREMENTS:
  - Shorten URL: tinyurl.com/abc123 → www.example.com/very-long-path
  - Redirect: tinyurl.com/abc123 → 301/302 to original URL
  - Analytics: track clicks (count, geography, device)
  - Scale: 100M URLs shortened total, 10B redirects/day

ESTIMATION:
  Redirects/sec = 10B / 86,400 = 115,000/sec (read-heavy!)
  New URLs/day = 100M / 365 = 274K/day = 3 writes/sec
  Storage: 100M × 500 bytes/URL = 50GB (small!)
  
  THIS IS EXTREMELY READ-HEAVY: 115K reads vs 3 writes/sec

BASE62 ENCODING:
  Characters: a-z, A-Z, 0-9 = 62 characters
  7 characters: 62^7 = 3.5 trillion unique combinations (enough!)
  
  Collision strategy:
  Option A: Pre-generate keys (KGS — Key Generation Service)
    - Background job pre-generates millions of base62 keys
    - Stores in "available keys" table
    - On shortening request: pick one, mark as used
    - Fast! No collision checking needed
    
  Option B: Hash-based
    - hash(longURL) → take first 7 characters of base62(hash)
    - Check if key exists in DB → if so, increment and retry
    - Simpler but risk of collisions

301 vs 302 REDIRECT:
  301 Permanent: Browser caches the redirect
    → Next time browser hits same URL: uses cached redirect (no server request)
    → Analytics CANNOT track repeat visits (browser never calls your server)
  
  302 Temporary: Browser does NOT cache the redirect
    → Every request goes through your server
    → Analytics CAN track every click
  
  CHOICE: Use 302 if you need analytics. Use 301 for CDN-level efficiency.

ARCHITECTURE:
  Write path: API → KGS (get key) → PostgreSQL (store mapping) → return short URL
  Read path: API → Redis cache → (miss) PostgreSQL → redirect
  Analytics: Kafka (click events) → Flink (process) → ClickHouse (analytics)
```

### Days 66–70: Design Chat App + Video Streaming

```
REAL-TIME CHAT (WhatsApp-style)

WEBSOCKET vs POLLING:
  Polling: Client asks "any new messages?" every 5 seconds
    → 5 second delay maximum
    → 200M users × 1 request/5s = 40M requests/sec (unnecessary load)
  
  Long Polling: Client asks, server waits up to 30s before responding
    → Better, but complex and wastes connections
  
  WebSocket: Persistent bidirectional TCP connection
    → Messages delivered instantly (< 100ms)
    → Server can PUSH without client asking
    → Used by: WhatsApp, Slack, Discord, Facebook Messenger

MESSAGE SCHEMA IN CASSANDRA:
  Partition key: chat_id (all messages for one chat on same partition)
  Clustering key: message_id (ordered within partition)
  
  CREATE TABLE messages (
    chat_id   UUID,
    message_id TIMEUUID,  -- UUID that encodes timestamp + unique
    sender_id UUID,
    content   TEXT,
    type      TEXT,  -- text, image, video
    PRIMARY KEY (chat_id, message_id)
  ) WITH CLUSTERING ORDER BY (message_id DESC);
  
  WHY CASSANDRA?
  - High write throughput (append-heavy: messages are insert-only)
  - Range queries work well with clustering key ordering
  - Horizontal scaling without joins
  - Used by: Discord for trillions of messages

MESSAGE DELIVERY STATUS:
  Sent: Server received the message
  Delivered: Recipient's device downloaded it
  Read: Recipient opened the conversation
  
  Implementation: 
  - Sender device ACKs → message "sent"
  - Recipient connects via WebSocket → server pushes → device ACKs → "delivered"
  - Recipient opens chat → client sends "read receipt" event
```

---

---

# 🔴 PHASE 5: AI-NATIVE SYSTEM DESIGN (Days 71–90)

> **Goal:** Understand how AI systems are built and operated at production scale. Every MNC is adding AI to their existing distributed systems stack. Understanding both is the competitive advantage.

---

## DAYS 71–75: RAG Architecture and Vector Databases

### Day 71: RAG System Design

```
RAG = Retrieval-Augmented Generation

THE PROBLEM:
  LLMs trained on public data. Don't know your private company docs.
  You can't fit 10TB of company knowledge in one prompt.
  
THE SOLUTION:
  1. Index your documents as vectors (embeddings) in a vector DB
  2. When user asks a question:
     a. Convert question to vector
     b. Search vector DB for similar document chunks (top-k)
     c. Inject retrieved chunks into LLM prompt
     d. LLM generates answer grounded in your documents

RAG PIPELINE ARCHITECTURE:

INGESTION (offline):
  Documents → Chunking → Embedding Model → Vector DB
  
  CHUNKING STRATEGIES:
  Fixed: 512 tokens, 50 token overlap
  Semantic: Split at paragraph boundaries
  Hierarchical: Parent chunks + child chunks (search child, return parent context)
  
  EMBEDDING MODELS:
  Local (free): all-MiniLM-L6-v2 (384 dims, fast)
  Local (better): nomic-embed-text (768 dims)
  API (best): OpenAI text-embedding-3-large (3072 dims)

RETRIEVAL (online):
  Question → embedding → ANN search → top-k chunks → LLM prompt

VECTOR DATABASE COMPARISON:
  pgvector: PostgreSQL extension. No new infra. 
            Good for < 1M vectors.
  Qdrant: Purpose-built. Fast. Open source. Best free option.
          Used by: Mistral AI, various startups.
  Weaviate: Open source. Built-in ML models.
  Pinecone: Fully managed. Best scalability. Not free.
  Milvus: Open source. Best for 100M+ vectors.

HNSW (Hierarchical Navigable Small World) — The Index:
  Approximate Nearest Neighbor (ANN) search.
  
  Regular search: Compare query to ALL N vectors = O(N). Too slow at scale.
  HNSW: Graph where similar vectors are connected.
        Navigate graph from coarse to fine layers.
        Find nearest neighbor in O(log N) steps.
        
  Tradeoff: Approximate (not exact). May miss ~1-5% of true neighbors.
  Acceptable: "Find 10 most relevant docs" doesn't need to be perfect.
```

### Day 72–73: Building a Complete RAG System

```python
# Save as: projects/06-ai-chat-system/rag_system.py

from qdrant_client import QdrantClient
from qdrant_client.models import Distance, VectorParams, PointStruct
from sentence_transformers import SentenceTransformer
import ollama
import uuid
import json
from typing import List, Dict

class ProductionRAGSystem:
    """
    Production-grade RAG system.
    
    Architecture:
    - Qdrant: Vector storage + HNSW search
    - SentenceTransformers: Local embedding model (no API costs)
    - Ollama: Local LLM (no API costs)
    
    Used pattern: Multi-stage retrieval
    1. Dense retrieval (vector similarity)
    2. Re-ranking (optional: reorder by relevance)
    3. Generation with citations
    """
    
    def __init__(self, collection_name: str = "documents"):
        self.collection_name = collection_name
        
        # Vector database (runs locally)
        self.qdrant = QdrantClient(host="localhost", port=6333)
        
        # Embedding model (runs locally, 384 dimensions)
        self.embedder = SentenceTransformer('all-MiniLM-L6-v2')
        self.vector_dim = 384
        
        # LLM (runs locally via Ollama)
        self.llm_model = "llama3"
        
        self._ensure_collection()
    
    def _ensure_collection(self):
        """Create vector collection if it doesn't exist."""
        collections = [c.name for c in self.qdrant.get_collections().collections]
        if self.collection_name not in collections:
            self.qdrant.create_collection(
                collection_name=self.collection_name,
                vectors_config=VectorParams(
                    size=self.vector_dim,
                    distance=Distance.COSINE  # Best for text similarity
                )
            )
            print(f"Created collection: {self.collection_name}")
    
    def ingest_document(self, title: str, content: str, metadata: dict = None) -> str:
        """
        Chunk, embed, and store a document.
        Returns the document ID.
        """
        # Chunk the document (simple fixed-size chunking)
        chunks = self._chunk_text(content, chunk_size=500, overlap=50)
        doc_id = str(uuid.uuid4())
        
        points = []
        for i, chunk in enumerate(chunks):
            embedding = self.embedder.encode(chunk).tolist()
            point = PointStruct(
                id=str(uuid.uuid4()),
                vector=embedding,
                payload={
                    "doc_id": doc_id,
                    "title": title,
                    "chunk_index": i,
                    "chunk_text": chunk,
                    "metadata": metadata or {}
                }
            )
            points.append(point)
        
        self.qdrant.upsert(collection_name=self.collection_name, points=points)
        print(f"Ingested '{title}': {len(chunks)} chunks stored")
        return doc_id
    
    def _chunk_text(self, text: str, chunk_size: int = 500, overlap: int = 50) -> List[str]:
        """Split text into overlapping chunks."""
        words = text.split()
        chunks = []
        for i in range(0, len(words), chunk_size - overlap):
            chunk = ' '.join(words[i:i + chunk_size])
            if chunk:
                chunks.append(chunk)
        return chunks
    
    def retrieve(self, query: str, top_k: int = 5) -> List[Dict]:
        """Find most relevant chunks for a query."""
        query_embedding = self.embedder.encode(query).tolist()
        
        results = self.qdrant.search(
            collection_name=self.collection_name,
            query_vector=query_embedding,
            limit=top_k,
            with_payload=True,
            score_threshold=0.5  # Only return results with >50% similarity
        )
        
        return [
            {
                "text": r.payload["chunk_text"],
                "title": r.payload["title"],
                "score": round(r.score, 4),
                "doc_id": r.payload["doc_id"]
            }
            for r in results
        ]
    
    def answer(self, question: str) -> Dict:
        """
        Full RAG pipeline: retrieve → augment → generate.
        """
        # Step 1: Retrieve relevant context
        retrieved_chunks = self.retrieve(question, top_k=5)
        
        if not retrieved_chunks:
            return {
                "answer": "I don't have relevant information to answer this question.",
                "sources": [],
                "chunks_used": 0
            }
        
        # Step 2: Build augmented prompt
        context_text = "\n\n".join([
            f"[Source: {chunk['title']} (relevance: {chunk['score']})]:\n{chunk['text']}"
            for chunk in retrieved_chunks
        ])
        
        prompt = f"""You are a helpful assistant. Answer the user's question using ONLY the provided context.
If the answer is not in the context, say "I don't have enough information."
Always cite which source your answer comes from.

CONTEXT:
{context_text}

QUESTION: {question}

ANSWER (with citations):"""
        
        # Step 3: Generate answer with local LLM
        response = ollama.chat(
            model=self.llm_model,
            messages=[{"role": "user", "content": prompt}],
            options={"temperature": 0.1}  # Low temperature for factual answers
        )
        
        return {
            "question": question,
            "answer": response["message"]["content"],
            "sources": [{"title": c["title"], "score": c["score"]} for c in retrieved_chunks],
            "chunks_used": len(retrieved_chunks)
        }
    
    def text_to_sql(self, natural_language_query: str, schema: str) -> str:
        """
        Convert natural language to SQL.
        IMPORTANT: Always validate generated SQL before executing!
        """
        prompt = f"""Convert the following natural language query to SQL.
Return ONLY the SQL query, nothing else.
Never include DROP, DELETE, UPDATE, or INSERT operations.
Always add LIMIT 100 unless the query asks for counts/aggregations.

Schema:
{schema}

Query: {natural_language_query}

SQL:"""
        
        response = ollama.chat(
            model=self.llm_model,
            messages=[{"role": "user", "content": prompt}],
            options={"temperature": 0.0}
        )
        
        sql = response["message"]["content"].strip()
        sql = sql.replace("```sql", "").replace("```", "").strip()
        return sql
```

### Days 75–77: Semantic Caching + LLMOps

```
SEMANTIC CACHING:

Traditional Redis cache:
  Key: "What is the capital of France?"
  Value: "Paris"
  
  User asks "What's France's capital?" → CACHE MISS (different string!)
  Hits the expensive LLM unnecessarily.

Semantic Cache:
  Store: (embedding("What is the capital of France?"), "Paris")
  
  New query: "What's France's capital?"
  1. Embed the new query
  2. Search cache for similar query vectors (cosine similarity > 0.95)
  3. CACHE HIT: "Paris" (even though the strings are different!)
  
  Implementation: pgvector or Qdrant as semantic cache layer

LLMOps METRICS TO TRACK:
  - Latency: time to first token, total generation time
  - Cost: tokens consumed per request
  - Quality: hallucination rate, relevance score, user feedback
  - Cache hit rate: what % of requests are semantic cache hits
  - Retrieval quality: are the right chunks being returned?

EVALUATION FRAMEWORKS:
  RAGAS: Faithfulness, Answer Relevancy, Context Precision, Context Recall
  TruLens: RAG triad evaluation
  LLM-as-a-Judge: use a cheap model to evaluate expensive model's outputs
```

### Days 78–80: AI Agents and the ReAct Pattern

```
THE AGENT ARCHITECTURE:

Traditional software: Input → Code → Output (deterministic)
AI Agent: Input → LLM → Reasoning → Tool Use → Observation → LLM → Output

ReAct Pattern (Reason + Act):
  Thought: "The user wants to know the weather in Chennai."
  Action: call_tool("weather_api", location="Chennai")
  Observation: {"temp": 35, "condition": "sunny", "humidity": 80}
  Thought: "Got the weather data. Now I can answer."
  Answer: "Chennai is currently 35°C and sunny with 80% humidity."

TOOL TYPES:
  Read-only: search, calculator, web_browse, database_query
  Write: send_email, create_ticket, update_database
  
  SAFETY: Agents with write access need guardrails!
  Never give an agent unrestricted database write access.

MULTI-AGENT SYSTEMS:
  
  Sequential (Pipeline):
    User Question → Research Agent → Analysis Agent → Writing Agent → Answer
    Each agent specializes. Output of one feeds next.
  
  Hierarchical (Manager-Worker):
    User: "Research AI trends and write a report"
    Manager Agent: breaks into subtasks
    → Research Agent: find relevant papers
    → Data Agent: extract statistics
    → Writing Agent: synthesize into report
    Manager Agent: review and compile
  
  PROBLEMS:
  - Infinite loops (A evaluates B, B evaluates A)
  - Context window overflow (long conversations)
  - Hallucination compounding (each agent adds error)
  
  SOLUTIONS:
  - Maximum iteration limit
  - State machine with defined termination conditions
  - "Trust but verify" — secondary agent checks primary agent's work
```

---

## DAYS 81–90: PROJECT 6 — AI-Powered Scalable Chat System

### Architecture

```
AI-POWERED CHAT SYSTEM (Production Architecture)

Client (Browser/Mobile)
  │ WebSocket (persistent)
  ▼
┌─────────────────────────────────────────────────────────────────┐
│                      API GATEWAY (NGINX)                         │
│  Rate limiting · TLS termination · WebSocket upgrade            │
└──────────────┬───────────────────────────────────────────────────┘
               │
    ┌──────────┴──────────┐
    │                     │
┌───▼──────────┐  ┌───────▼──────────┐
│ Chat Service │  │   AI Bot Service │
│ (Go/Node.js) │  │   (Python)       │
│ WebSocket    │  │   RAG + Ollama   │
│ management   │  │   Responds to    │
│              │  │   @ai mentions   │
└───┬──────────┘  └───────┬──────────┘
    │                     │
    │ Kafka topic: "chat.messages"
    ├──────────────────────┤
    │                      │
┌───▼──────────┐  ┌────────▼─────────┐
│  Cassandra   │  │     Qdrant       │
│  (message    │  │  (vector index   │
│   history)   │  │   of all chat    │
│              │  │   for semantic   │
│              │  │   search)        │
└──────────────┘  └──────────────────┘
    │
    │ Prometheus metrics
┌───▼──────────┐
│   Grafana    │
│  Dashboard   │
└──────────────┘

FEATURES:
  Real-time chat: WebSocket pub/sub via Redis
  Message history: Cassandra (infinite scrolling, ordered)
  AI assistant: @ai mention → RAG bot responds using chat history
  Semantic search: "Find messages about the deployment issue last week"
  Rate limiting: Redis sliding window per user
  Observability: Prometheus metrics + Grafana dashboard
```

---

---

# 🟢 PHASE 6: PORTFOLIO + INTERVIEW MASTERY (Days 91–110)

> **Goal:** Polish everything. Practice mock interviews. Build your professional presence. Ensure every project has the documentation to prove you built it.

---

## DAYS 91–95: Green Computing and Emerging Topics

### Day 91: Carbon-Aware System Design

```
THE PROBLEM:
  Training GPT-4: estimated 50,000 MWh of energy
  Running inference: millions of requests/day → significant carbon footprint
  MNCs now have legal and reputational carbon commitments.

CARBON-AWARE COMPUTING:
  Not all electricity is equal:
  - Solar farm in Arizona: near-zero carbon
  - Coal plant in Virginia: high carbon
  - Wind farm in Denmark: near-zero carbon
  
  STRATEGY:
  For batch workloads (ML training, nightly reports, backups):
  → Run when and where the grid is greenest
  → API: electricitymaps.com provides real-time carbon intensity per region
  
  For latency-sensitive (API requests):
  → Route to lowest-latency region as priority
  → Carbon optimization is secondary

IMPLEMENTATION:
  Carbon-Aware Load Balancer:
  1. Fetch carbon intensity for each datacenter region (cached 15min)
  2. For batch requests: prefer lowest carbon region (if latency within 50ms SLA)
  3. For real-time requests: prefer lowest latency region
  
  Scheduled workloads:
  - "Run this ML training job when grid carbon < 50 gCO2/kWh"
  - Kubernetes operator that delays pod scheduling based on carbon API
```

### Days 92–95: MNC Case Studies Deep Dive

```
DISCORD: MONGODB → CASSANDRA → SCYLLADB

Problem: Discord grew from 0 → trillions of messages
  Phase 1: MongoDB single replica set
    Failure point: ~100M messages. MongoDB OOM'd. Moved to Cassandra.
  
  Phase 2: Cassandra
    Worked for years. Issue: JVM garbage collection pauses.
    100ms latency spikes during GC → noticeable for Discord users.
    
  Phase 3: ScyllaDB (C++ rewrite of Cassandra's API)
    Same CQL protocol, same data model, but C++ instead of Java.
    No GC pauses. 10x better latency consistency.
    Discord reads 60% faster, writes 50% faster vs Cassandra.

UBER: POSTGRES → MYSQL+SCHEMALESS

Problem: Uber's trip data was write-heavy with frequent schema changes.
  Issue with Postgres: Every index must be updated on write.
            Schema changes require table rewrites.
            
  Solution: "Schemaless" — append-only document storage on top of MySQL.
  - Each row is one JSON document (no ALTER TABLE needed)
  - Secondary indexes: separate table with async updates
  - Immutable: never UPDATE rows, only INSERT new versions
  
  KEY LESSON: Sometimes the constraint is NOT the database engine,
  it's your usage pattern. Changing to append-only removed Uber's bottleneck.

NETFLIX: Moving to Active-Active Multi-Region

Original: One primary region (US East). Everything there.
  Problem: US East availability issue → all Netflix users worldwide affected.
  
  Solution: Active-Active across 3 AWS regions.
  Every region serves real traffic. No "standby" region.
  CassandraDB as global distributed store (AP system).
  
  CHALLENGE: Writes in two regions simultaneously → eventual consistency.
  Solution: Careful data modeling. Most Netflix data is append-only.
  (What you watched is never deleted. New watches are just inserted.)
```

---

## DAYS 96–110: PROJECT 7 — Anomaly Detection Rate Limiter (CAPSTONE)

### Architecture

```
AI-POWERED ANOMALY DETECTION RATE LIMITER

PROBLEM:
  Static rate limiting (100 req/min per IP) is:
  - Too loose: allows slow DDoS attacks
  - Too tight: blocks legitimate burst traffic
  
  Normal user: 5-50 req/min, varied endpoints, browser user-agent
  DDoS bot:    500 req/min, same endpoint, no user-agent, same IP subnet

AI SOLUTION:
  Train an Isolation Forest model on normal traffic patterns.
  If request pattern deviates significantly → anomaly → stricter limits.

SYSTEM:

  ┌─────────────────────────────────────────────────────────────┐
  │                  TRAFFIC INGESTION                           │
  │  All requests → Kafka topic "http.requests"                  │
  │  Payload: {ip, endpoint, user_agent, response_time, ts}      │
  └──────────────────────────────┬──────────────────────────────┘
                                 │
  ┌──────────────────────────────▼──────────────────────────────┐
  │              FEATURE EXTRACTION (Flink / Python)             │
  │  Per IP, rolling 5-min window:                               │
  │  - request_rate (req/sec)                                    │
  │  - endpoint_entropy (variety of endpoints hit)               │
  │  - user_agent_consistency (always same? suspicious)          │
  │  - error_rate (% of 4xx/5xx responses)                      │
  │  - ip_subnet_concentration (many IPs in same /24 subnet)    │
  └──────────────────────────────┬──────────────────────────────┘
                                 │
  ┌──────────────────────────────▼──────────────────────────────┐
  │              ANOMALY DETECTION (scikit-learn)                 │
  │  Isolation Forest trained on 7 days of normal traffic        │
  │  Anomaly score → normal (-1 to 0) or anomalous (0 to 1)     │
  │                                                              │
  │  Score < 0.3: Normal → apply standard rate limit            │
  │  Score 0.3-0.7: Suspicious → apply strict rate limit        │
  │  Score > 0.7: Attack → block IP, alert on-call              │
  └──────────────────────────────┬──────────────────────────────┘
                                 │
  ┌──────────────────────────────▼──────────────────────────────┐
  │              DYNAMIC RATE LIMITER (Redis)                    │
  │  Store per-IP anomaly score in Redis (TTL 5min)              │
  │  Rate limit middleware reads score → adjusts limit           │
  │  Normal: 100 req/min. Suspicious: 10 req/min. Attack: block  │
  └──────────────────────────────┬──────────────────────────────┘
                                 │
  ┌──────────────────────────────▼──────────────────────────────┐
  │              OBSERVABILITY (Prometheus + Grafana)            │
  │  - Requests allowed vs blocked per second                    │
  │  - Anomaly score distribution over time                     │
  │  - IP addresses flagged as anomalous                         │
  │  - Model accuracy (false positives tracked)                  │
  └─────────────────────────────────────────────────────────────┘

TECH STACK:
  Traffic capture: Kafka + Python consumer
  Feature extraction: Apache Flink (streaming) or Python with sliding window
  ML model: scikit-learn Isolation Forest
  Rate limiting: Redis (sliding window with Lua scripts)
  Deployment: Kubernetes + Helm
  CI/CD: GitHub Actions
  Monitoring: Prometheus + Grafana
```

---

## DAYS 105–110: Mock Interviews + Portfolio Polish

### The Mock Interview Framework

```
SYSTEM DESIGN INTERVIEW TEMPLATE (45 minutes):

1. CLARIFY (5 min) — Ask these questions every time:
   "How many users? DAU/MAU?"
   "What's the read/write ratio?"
   "What are the latency requirements?"
   "Strong or eventual consistency?"
   "What's the budget/constraint for this system?"

2. ESTIMATE (3 min) — Show math:
   "Let me calculate the scale..."
   [Write numbers on the whiteboard/Excalidraw]

3. HIGH-LEVEL DESIGN (10 min) — Draw the boxes:
   "Here are the main components..."
   [Draw in Excalidraw: clients, LB, services, DBs]

4. DEEP DIVE (20 min) — Go deep on complexity:
   "The hardest part of this design is [X]. Here's how I'd handle it..."
   Show: database choice reasoning, sharding strategy, caching layer, failure modes

5. FOLLOW-UP (5 min) — Anticipate their questions:
   "If traffic grew 10x, I'd change..."
   "The main risk in this design is..."
   "An alternative approach would be..."

PRACTICE SCHEDULE (Days 105–110):
  Day 105: Design Twitter (write it in 45 min, document it)
  Day 106: Design YouTube (write it in 45 min)
  Day 107: Design Uber (write it in 45 min)
  Day 108: Design WhatsApp (write it in 45 min)
  Day 109: Design Google Search (write it in 45 min)
  Day 110: Full mock interview with someone else timing you
```

---

---

# 📊 COMPLETE DAY-BY-DAY TIMETABLE (MASTER TABLE)

## Phase 1: Physics of Software (Days 1–14)

| Day | Topic | Subtopics | Assignment | Document |
|-----|-------|-----------|------------|----------|
| **1** | OSI Model | Layers 1–7, encapsulation, headers, MTU | tcpdump capture of HTTP traffic | `day-01-osi.md` + diagram |
| **2** | TCP Internals | 3-way handshake, flow control, congestion, HOL blocking | Raw socket TCP demo in Python | `day-02-tcp.md` |
| **3** | UDP and QUIC | UDP simplicity, reliability-on-UDP, QUIC features | UDP file transfer with checksum | `day-03-udp-quic.md` |
| **4** | DNS + Anycast | Record types, TTL, resolution chain, Anycast routing | `dig +trace` + local DNS override | `day-04-dns.md` |
| **5** | API Paradigms | REST vs GraphQL vs gRPC, Protobuf, payload comparison | Write `.proto`, measure JSON vs Protobuf size | `day-05-apis.md` + Postman collection |
| **6** | Processes + Threads | Stack vs Heap, context switch, GIL, goroutines, race conditions | Race condition demo + fix with Lock | `day-06-concurrency.md` |
| **7** | I/O Models | Blocking, non-blocking, epoll, event loop, C10K | Single-threaded multi-client chat server | `day-07-io.md` |
| **8** | Memory + Storage | Virtual memory, paging, inodes, FDs, HDD vs SSD | FD exhaustion experiment | `day-08-memory.md` |
| **9** | Load Balancing | L4 vs L7, algorithms, health checks, NGINX config | NGINX reverse proxy + weighted backends | `day-09-lb.md` |
| **10** | Containers | Namespaces, cgroups, Docker vs VM, Dockerfile | Build container from scratch with unshare | `day-10-containers.md` |
| **11** | System Design 101 | Framework: Clarify, Estimate, Design, Deep dive, Tradeoffs | First estimate: Twitter scale numbers | `day-11-design-framework.md` |
| **12** | Estimation Practice | Number drills, storage math, QPS calculations | Estimate YouTube, Uber, WhatsApp | `day-12-estimation.md` |
| **13–14** | **PROJECT 1** | Layer 7 Load Balancer (round-robin + health checks) | Full implementation in Python | `projects/01-load-balancer/README.md` + blog post |

## Phase 2: Distributed Systems Theory (Days 15–30)

| Day | Topic | Subtopics | Assignment | Document |
|-----|-------|-----------|------------|----------|
| **15** | CAP Theorem | CP vs AP, PACELC, partition tolerance | Reasoning exercise: ride-sharing decisions | `day-15-cap.md` + ADR |
| **16** | Consistency Models | Linearizability, eventual, causal, read-your-writes | Simulate eventual consistency in Python | `day-16-consistency.md` |
| **17** | Clocks + Time | Clock skew, NTP, Lamport timestamps, Vector clocks | Implement VectorClock class | `day-17-clocks.md` |
| **18** | Raft Consensus | Leader election, log replication, safety | raft.github.io simulation + Python leader election | `day-18-raft.md` |
| **19** | Transactions | 2PC, Saga pattern, choreography vs orchestration | Design travel booking saga with compensation | `day-19-transactions.md` |
| **20** | Quorums | N, W, R relationships, Cassandra consistency levels | Calculate quorum configs for 3 scenarios | `day-20-quorums.md` |
| **21** | Replication | Single-leader, multi-leader, leaderless, conflict resolution | Set up PostgreSQL streaming replication | `day-21-replication.md` |
| **22** | Sharding | Key-range, hash, hotspots, cross-shard queries | Design shard key for 3 different systems | `day-22-sharding.md` |
| **23** | Consistent Hashing | Hash ring, virtual nodes, data movement | Full ConsistentHashRing implementation | `day-23-consistent-hashing.md` |
| **23–25** | **PROJECT 2** | Distributed KV Store with quorum reads | Full implementation + kill-node test | `projects/02-distributed-kv/README.md` |
| **26** | Caching Patterns | Cache-aside, write-through, write-back, Thundering Herd | LRU Cache implementation | `day-26-caching.md` |
| **27** | LRU + LFU | OrderedDict, Heap-based LFU, O(1) operations | LRU + LFU both implemented | `day-27-eviction.md` |
| **28** | Redis Architecture | Event loop, RESP protocol, RDB vs AOF persistence | telnet raw RESP commands | `day-28-redis.md` |
| **29** | CDNs | Edge caching, push vs pull, Anycast, cache headers | Analyze YouTube CDN headers | `day-29-cdn.md` |
| **30** | Probabilistic Structures | Bloom filters, HyperLogLog, Count-Min Sketch | Bloom filter for URL malware detection | `day-30-bloom.md` + blog post |

## Phase 3: MNC Components (Days 31–50)

| Day | Topic | Subtopics | Assignment | Document |
|-----|-------|-----------|------------|----------|
| **31** | B-Tree Internals | Branching factor, leaf nodes, random I/O, read optimization | Visualize B-Tree with sqlite_analyzer | `day-31-btree.md` |
| **32** | LSM Tree Internals | MemTable, SSTable, WAL, compaction, write amplification | Draw LSM write lifecycle diagram | `day-32-lsm.md` |
| **33** | MVCC | Multi-version concurrency, PostgreSQL implementation | Run EXPLAIN ANALYZE on complex query | `day-33-mvcc.md` |
| **34–40** | **PROJECT 3** | Build Your Own Redis (RESP protocol + TTL + async) | Full implementation compatible with redis-cli | `projects/03-mini-redis/README.md` + blog post |
| **41** | Kafka Architecture | Topics, partitions, offsets, zero-copy, consumer groups | Produce 1M messages, measure throughput | `day-41-kafka.md` |
| **42** | Delivery Semantics | At-most/at-least/exactly-once, idempotency | Implement idempotent consumer | `day-42-delivery.md` |
| **43** | Event Sourcing | Immutable events, projections, time travel | Design event schema for order system | `day-43-event-sourcing.md` |
| **44** | CQRS | Command model vs query model, async projection | Implement simple CQRS order system | `day-44-cqrs.md` |
| **45** | Discord Case Study | MongoDB → Cassandra → ScyllaDB migration | Write analysis document | Blog post: Discord's DB journey |
| **46–50** | **PROJECT 4** | Mini-Kafka (append-only log + offset tracking) | Full implementation + consumer demo | `projects/04-mini-kafka/README.md` |

## Phase 4: Production Design (Days 51–70)

| Day | Topic | Subtopics | Assignment | Document |
|-----|-------|-----------|------------|----------|
| **51** | Microservices Patterns | Service discovery, API gateway, Circuit breaker | Implement circuit breaker decorator | `day-51-microservices.md` |
| **52** | Observability | Metrics (RED), logs (structured), tracing (OpenTelemetry) | Instrument FastAPI with Prometheus | Grafana dashboard screenshot |
| **53** | Rate Limiting | Token bucket, leaky bucket, sliding window, Redis+Lua | Sliding window rate limiter | `day-53-rate-limiting.md` |
| **54** | Resilience Patterns | Bulkhead, timeout, retry with backoff, fallback | Implement retry with exponential backoff | `day-54-resilience.md` |
| **55–57** | Design: Twitter | Timeline fanout, sharding, Cassandra schema | Full design doc + Excalidraw diagram | `designs/twitter.md` + blog post |
| **58–60** | Design: YouTube | Transcoding pipeline, HLS/DASH, CDN strategy | Full design doc + Excalidraw diagram | `designs/youtube.md` |
| **60–65** | **PROJECT 5** | Intelligent URL Shortener (Base62 + Redis + analytics) | Full implementation + load test | `projects/05-url-shortener/README.md` |
| **66–68** | Design: Chat App | WebSockets, Cassandra schema, message delivery | Cassandra message schema + design doc | `designs/chat-app.md` |
| **69–70** | Design: Discord | At-scale chat, read receipts, reaction system | Full design doc | `designs/discord.md` + blog post |

## Phase 5: AI-Native Design (Days 71–90)

| Day | Topic | Subtopics | Assignment | Document |
|-----|-------|-----------|------------|----------|
| **71** | RAG Architecture | Chunking, embedding, retrieval, generation | Design RAG system architecture | `day-71-rag.md` |
| **72** | Vector Databases | HNSW, cosine similarity, Qdrant setup | Ingest 100 docs, test semantic search | `day-72-vector-db.md` |
| **73** | Building RAG | Qdrant + SentenceTransformers + Ollama | Full RAG Q&A system working | Demo video |
| **74** | Semantic Caching | GPTCache, vector similarity cache, hit rate | Implement semantic cache | `day-74-semantic-cache.md` |
| **75** | LLMOps Metrics | Latency, cost, hallucination rate, RAGAS | Set up LLM metrics dashboard | Grafana screenshot |
| **76** | AI Guardrails | Prompt injection, NeMo Guardrails, input validation | Implement prompt injection detection | `day-76-guardrails.md` |
| **77** | Agent Architecture | ReAct pattern, tool calling, function calling | Build calculator + search agent | `day-77-agents.md` |
| **78** | Multi-Agent Systems | Sequential, hierarchical, consensus patterns | Design multi-agent code review system | Architecture diagram |
| **79** | Text-to-SQL | Schema injection, validation, safety | Text-to-SQL with safety guardrails | `day-79-text2sql.md` |
| **80–90** | **PROJECT 6** | AI-Powered Chat System (WebSocket + RAG bot + Cassandra) | Full deployment + demo video | `projects/06-ai-chat/README.md` + blog post |

## Phase 6: Portfolio + Interview (Days 91–110)

| Day | Topic | Subtopics | Assignment | Document |
|-----|-------|-----------|------------|----------|
| **91** | Green Computing | Carbon-aware load balancing, carbon APIs | Carbon intensity routing demo | `day-91-green.md` |
| **92** | Uber Case Study | Schemaless, append-only, MySQL sharding | Write analysis document | Blog post |
| **93** | Netflix Case Study | Active-active, Cassandra global, chaos engineering | Write analysis document | Blog post |
| **94** | Google Spanner | TrueTime, NewSQL, global consistency | Compare with Cassandra tradeoffs | `day-94-spanner.md` |
| **95** | System Design Review | Review all 8 design patterns covered | Re-draw Twitter without notes | Full redesign doc |
| **96–105** | **CAPSTONE PROJECT** | Anomaly Detection Rate Limiter (Kafka + Flink + ML + K8s) | Full deployment with CI/CD | `projects/07-anomaly-ratelimiter/README.md` |
| **106** | Mock Interview 1 | Design Twitter (timed, 45 minutes) | Write up the design | Mock interview notes |
| **107** | Mock Interview 2 | Design YouTube (timed, 45 minutes) | Write up the design | Mock interview notes |
| **108** | Mock Interview 3 | Design Uber (timed, 45 minutes) | Write up the design | Mock interview notes |
| **109** | Mock Interview 4 | Design WhatsApp (timed, 45 minutes) | Write up the design | Mock interview notes |
| **110** | Portfolio Review | Polish all READMEs, final blog post, LinkedIn update | Publish "110-Day System Design Journey" | Master blog post |

---

---

# 🏆 PROJECT PORTFOLIO SUMMARY

| # | Project | Phase | Real Problem Solved | Tech Stack | Interview Relevance |
|---|---------|-------|---------------------|------------|---------------------|
| **1** | Layer 7 Load Balancer | Networking | Distribute traffic, health checks | Python, sockets, HTTP, threading | "Design a load balancer" questions |
| **2** | Distributed KV Store | Distributed Theory | Consistent Hashing + Quorum | Python, consistent hashing | "Design DynamoDB" questions |
| **3** | Mini Redis | Components | RESP protocol, TTL, event loop | Python asyncio, sockets | "What is Redis?" deep dives |
| **4** | Mini Kafka | Components | Append-only log, offsets, consumers | Python, file I/O, sockets | "Design a message queue" |
| **5** | Intelligent URL Shortener | System Design | Base62, KGS, caching, analytics | Python, Redis, PostgreSQL, Kafka | Classic interview question |
| **6** | AI Chat System | AI Design | RAG + WebSocket + Cassandra | Python, Go, Cassandra, Qdrant, Ollama | AI-native system design |
| **7** | Anomaly Rate Limiter | Production + AI | DDoS detection + dynamic limits | Kafka, Flink, sklearn, Redis, K8s | Security-focused questions |

---

# 🎯 PROOF-OF-WORK: WHAT TO SHOW INTERVIEWERS

For each project, you need:
1. **GitHub repository** with clean README, architecture diagram, setup instructions
2. **Demo video** (3-5 minutes) showing it working (kill a node, show recovery)
3. **Blog post** explaining why you made each design decision
4. **Benchmark report** showing performance numbers (req/sec, latency)
5. **Architecture Decision Records** explaining alternatives you rejected

The engineer reviewing your application thinks:
*"Can this person design a system? Have they actually built something hard?"*

Your documentation must answer: **"Yes, here is the evidence."**

---

> ## 📌 The Final Principle
>
> Every senior engineer knows the patterns. Every principal engineer knows *when to break them*.
>
> Your journey through these 110 days teaches you the patterns. Your projects teach you the tradeoffs. Your documentation teaches you to communicate both.
>
> The engineer who can say **"I chose Cassandra over PostgreSQL here because we needed AP semantics, write-heavy throughput, and linear horizontal scaling — and I know this because I read the Discord migration case study AND reproduced the write amplification difference in a benchmark"** will outperform the engineer who can only say "Cassandra is good for scale."
>
> **Build it. Measure it. Document why.**












