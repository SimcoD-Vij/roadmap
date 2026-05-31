# 🌐 Complete Network Engineering Roadmap
### From Zero to MNC-Grade Production Engineer
> **Starting Point:** Absolute beginner — No Python, No Hardware knowledge  
> **End Goal:** Full-Stack Network Reliability Engineer (NRE) capable of MNC-standard production work  
> **Duration:** 30 Weeks (Daily structured learning + real projects)  
> **Documentation-First Philosophy:** Every day ends with something to publish

---

## 📐 ARCHITECTURE OVERVIEW — WHY THIS ORDER?

Before you start Day 1, read this. This is the **blueprint** of your entire journey. Like a building, you cannot put the roof before the walls, and you cannot put the walls before the foundation.

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    YOUR FULL LEARNING ARCHITECTURE                       │
│                                                                          │
│  PHASE 7: AI + AIOps (Weeks 29–30) ─────────────────── [ROOF]          │
│  ↑ Depends on: Monitoring, Automation, Cloud                             │
│                                                                          │
│  PHASE 6: Security + Monitoring (Weeks 25–28) ──────── [TOP FLOOR]     │
│  ↑ Depends on: Routing, Cloud, Automation                                │
│                                                                          │
│  PHASE 5: Cloud Networking (Weeks 17–20) ───────────── [3RD FLOOR]     │
│  ↑ Depends on: IP Routing, Switching, Automation tools                  │
│                                                                          │
│  PHASE 4: SDN + Data Center Fabrics (Weeks 14–16) ─── [2ND FLOOR]     │
│  ↑ Depends on: Advanced routing (BGP), Python                           │
│                                                                          │
│  PHASE 3: Automation + Python (Weeks 11–13) ────────── [1ST FLOOR]     │
│  ↑ Depends on: CLI knowledge, routing logic                              │
│                                                                          │
│  PHASE 2: Advanced Routing & Switching (Weeks 5–10) ── [GROUND FLOOR]  │
│  ↑ Depends on: Phase 1 fundamentals                                      │
│                                                                          │
│  PHASE 1: Networking Fundamentals (Weeks 1–4) ──────── [FOUNDATION]    │
│  ↑ Zero knowledge assumed. Start here.                                   │
└─────────────────────────────────────────────────────────────────────────┘
```

### Why This Architecture Was Designed This Way (Plain English)

Think of the internet like a city:
- **Phase 1** = Learning what roads, traffic lights, and addresses are
- **Phase 2** = Learning how big city expressways and highway routing works
- **Phase 3** = Learning how to write software that controls traffic lights automatically
- **Phase 4** = Learning how modern smart cities redesign themselves (SDN)
- **Phase 5** = Learning how cities connect to cloud-cities (AWS/Azure)
- **Phase 6** = Learning how police (security) and traffic cameras (monitoring) work
- **Phase 7** = Letting AI manage the city's traffic intelligently

Every phase **depends** on the one before it. Skipping one = building a house without walls.

---

## 📦 THE FINAL PROJECT: What You're Building

**Project Name:** `NetOps360` — An MNC-grade, open-source Network Operations Platform

This is the **production-grade project** you will build piece by piece. By Week 30, you will have:

| Component | What it does | Tech Stack |
|---|---|---|
| **Network Simulator Lab** | Virtual lab to practice routing | GNS3 / Containerlab (Open Source, Free) |
| **Config Automation Engine** | Push configs to 100+ devices automatically | Python + Ansible + Netmiko |
| **GitOps Pipeline** | Version-control all network configs like software code | GitHub + GitHub Actions (Free) |
| **Cloud Network** | VPC with hybrid on-prem connectivity | AWS Free Tier |
| **Security Monitoring** | Real-time threat detection and alerting | ELK Stack (Elasticsearch, Logstash, Kibana) — Free |
| **AI RCA Engine** | AI reads logs and finds root cause of failures | Python + Ollama (local LLM, Free) |
| **Documentation Portal** | Public proof of your work | GitHub Pages / Hashnode / Dev.to — Free |

**Total cost: ₹0 / $0** — Everything is open source or free tier.

---

## 📝 DOCUMENTATION STRATEGY — The Core of This Plan

Since documentation is your #1 goal, here is your complete system:

### Where to Document (Free Platforms)

| Platform | What to Post | URL |
|---|---|---|
| **GitHub** | All code, scripts, config files, lab diagrams | github.com |
| **Hashnode** | Daily/weekly technical blog posts | hashnode.com |
| **Dev.to** | Alternative technical blogging | dev.to |
| **LinkedIn** | Weekly project highlights + learnings | linkedin.com |
| **Notion** | Personal notes, weekly summaries | notion.so (free) |

### Daily Documentation Template

At the end of **every single day**, write this (takes 10–15 minutes):

```markdown
## Day [N] — [Topic Name]
**Date:** [Date]

### What I Learned
[2–3 sentences: the core concept in YOUR OWN words]

### The Lab I Did
[Screenshot or description of your GNS3/Packet Tracer lab]

### What I Got Wrong Initially
[What confused you, how you fixed it — this shows real learning]

### Code / Config I Wrote
[Paste the CLI commands or Python code you used]

### Connection to Real World
[How does this relate to what Google/Facebook/Amazon does?]

### Tomorrow's Topic
[One line preview]
```

Post this daily to **Hashnode or Dev.to**. After 30 weeks, you will have **200+ published articles** — an undeniable portfolio.

---

## 🏗️ PHASE 1: Networking Fundamentals (Weeks 1–4)
### "The Laws of How Data Travels"

**What this phase covers:** You will learn how a message you type reaches the other side of the world — at a wire level.

**Why this order?** Before you configure routers, you must understand why routers exist. Before routing, you must understand addressing. Before addressing, you must understand the physical signal.

**Tools you will install in this phase:**
- Wireshark (packet analyzer — see real network traffic)
- Cisco Packet Tracer (free, no hardware needed)
- GNS3 (professional-grade network simulator)
- VS Code (code editor)

---

### WEEK 1: The OSI Model, TCP/IP, and How Data Actually Moves

#### Day 1 — The OSI Model: The 7-Layer Map of Networking

**What it is (plain English):**  
The OSI model is a map that divides "how data travels" into 7 layers. Think of it like sending a physical letter: you write the content → fold it → put it in an envelope → write the address → give it to the post office → it goes on a truck → then a plane → then delivered. Each step is a "layer."

**The 7 Layers:**

| Layer | Number | Name | Job | Real Example |
|---|---|---|---|---|
| Application | 7 | Your app | Sends data from user app | Chrome browser, WhatsApp |
| Presentation | 6 | Translator | Encrypts, compresses data | HTTPS encryption (TLS) |
| Session | 5 | Traffic manager | Opens/closes connections | Login sessions |
| Transport | 4 | Delivery service | Ensures data arrives correctly | TCP (reliable), UDP (fast) |
| Network | 3 | Post office | Finds the route/address | IP address, Routers |
| Data Link | 2 | Street-level | Gets data to next device | MAC address, Switches |
| Physical | 1 | The wire | Actual electrical/light signals | Ethernet cable, Fiber optic |

**Why MNCs care:** When Google's SRE team gets a "Connection Refused" error, they immediately know it's a Layer 4 (Transport) issue. When there's a "Request Timeout," it might be Layer 3 (Network) packet loss. This model is the **diagnostic language** of the industry.

**Subtopics:**
- Layer 1 (Physical): Fiber optic cables (Single-mode vs Multi-mode), Copper (Cat6/6a), signal modulation, what "light levels" (dBm) mean
- Layer 2 (Data Link): Ethernet frames, MAC addresses, how switches use them for local delivery, Frame Check Sequence (FCS) for error detection
- Layer 3 (Network): IP addressing, difference between "forwarding" a packet vs "routing" (building the map)
- Layer 4 (Transport): TCP vs UDP, port numbers, reliability vs speed tradeoff
- Layers 5–7: Brief overview — these matter more in application development

**Assignment (Day 1):**
1. Install Wireshark: https://www.wireshark.org/download.html
2. Open Wireshark → capture traffic on your WiFi interface for 30 seconds
3. Find one HTTP or HTTPS packet in the list
4. Click it → expand the layers in the bottom pane
5. Write down what you see at Layer 2 (Ethernet), Layer 3 (IP), Layer 4 (TCP)
6. **Document:** Post a screenshot of your Wireshark capture with a 5-sentence explanation to Hashnode

---

#### Day 2 — Physical Layer Deep Dive: The Wire Itself

**What it is:**  
Before any protocol matters, data is just electricity or light moving through physical material. This is the foundation no textbook emphasizes enough.

**Subtopics:**
- **Copper cables:** How electrical signals travel. Cat5e (1Gbps), Cat6 (10Gbps up to 55m), Cat6a (10Gbps up to 100m). Why the "twist" in twisted-pair prevents interference.
- **Fiber optics:** Light travels through glass. Single-mode fiber (yellow jacket) = long distances (kilometers), used between buildings/cities. Multi-mode fiber (orange/aqua jacket) = short distances (within data centers).
- **dBm (decibel milliwatts):** How you measure signal strength on fiber. A light level of -3 dBm to -12 dBm is good. Below -25 dBm = the link will fail. This is what engineers check in data centers.
- **Wireless (Wi-Fi):** Radio waves. 2.4GHz = farther range, slower. 5GHz = shorter range, faster. 6GHz (Wi-Fi 6E) = newest standard.
- **Bandwidth vs Latency:** Bandwidth = how wide the pipe is (Gbps). Latency = how long it takes (milliseconds). A satellite connection has high bandwidth but terrible latency.

**Assignment (Day 2):**
1. Open your home router admin page (usually 192.168.1.1 or 192.168.0.1)
2. Find the "connected devices" section — note which are on 2.4GHz vs 5GHz
3. Use Wireshark: filter by `arp` in the filter bar — you'll see devices "announcing" themselves on the network
4. **Document:** Write "The Physical Layer Explained Like You're 10" on Hashnode — describe Wi-Fi in simple terms based on what you just saw

---

#### Day 3 — TCP: The Reliable Protocol

**What it is:**  
TCP (Transmission Control Protocol) is how your browser makes sure every piece of a webpage arrives correctly. If you're downloading a file, you want every byte to arrive — TCP guarantees this.

**Subtopics:**
- **The Three-Way Handshake:** Before data transfers, TCP "shakes hands"
  - Step 1: Your computer sends `SYN` ("I want to connect")
  - Step 2: Server responds `SYN-ACK` ("OK, I acknowledge, connect to me")
  - Step 3: Your computer sends `ACK` ("Connection established")
  - Without this, no TCP connection can happen
- **Sequence Numbers:** Every byte of data is numbered. If packet #1000 is lost, the receiver says "I got up to #999, resend from #1000"
- **Acknowledgment:** The receiver sends back "ACK" to confirm receipt. If the sender doesn't get an ACK within a timeout, it resends.
- **Flow Control (Sliding Window):** The receiver tells the sender "I can handle 65,000 bytes at once." If the receiver is slow, it shrinks the window. This prevents overwhelming the destination.
- **TCP RST (Reset):** When a server forcibly closes a connection (e.g., you try to connect to a port that's blocked or closed), it sends a RST. This is different from a "silent drop" where the packet disappears with no response.

**Assignment (Day 3):**
1. Open Wireshark, filter by `tcp`
2. Open a browser and go to http://example.com (not https — TCP is more visible)
3. Find the three packets: SYN, SYN-ACK, ACK — this is the handshake
4. Note the sequence numbers in each packet
5. **Document:** Draw the three-way handshake as a diagram (hand-drawn is fine, take a photo) and post it with your explanation

---

#### Day 4 — UDP and the Difference from TCP

**What it is:**  
UDP (User Datagram Protocol) is the "fire and forget" protocol. It sends data without confirming delivery. Faster, but unreliable. Used where speed matters more than perfection.

**Subtopics:**
- **Why UDP exists:** Video calls, online games, live streaming. If a video frame arrives late, you don't want the whole stream to wait for it to be resent — you just skip it (that's why video "smears" or freezes briefly)
- **DNS uses UDP:** When you type google.com, a DNS query goes out on UDP port 53. It's a tiny request — if it's lost, you just retry
- **VoIP (Voice over IP):** Phone calls use UDP. A dropped packet = brief static. A TCP retry would mean silence for 200ms — worse than static.
- **QUIC protocol:** Google's modern protocol (used in HTTP/3) that runs on UDP but adds its own reliability. It's faster than TCP because it doesn't have the handshake overhead.
- **Comparing TCP vs UDP:**

| Feature | TCP | UDP |
|---|---|---|
| Reliable delivery | ✅ Yes | ❌ No |
| Connection required | ✅ Yes (handshake) | ❌ No |
| Speed | Slower | Faster |
| Use case | Web browsing, file download | Video, gaming, DNS |

**Assignment (Day 4):**
1. In Wireshark, filter by `udp`
2. Open any website — you'll see DNS queries in UDP
3. Filter by `dns` to see the DNS request and response pairs
4. **Document:** Compare TCP and UDP in a table format on your blog — explain which protocol WhatsApp calls use and why

---

#### Day 5 — Intro to CLI and Setting Up Your Lab

**What it is:**  
The CLI (Command Line Interface) is how you talk to routers and switches. No mouse, just text commands. This is how every network engineer works.

**Subtopics:**
- **Install GNS3:** https://www.gns3.com/ (free, open source)
- **Install Cisco Packet Tracer:** https://www.netacad.com/courses/packet-tracer (free with Cisco NetAcad account)
- **IOS Modes (Cisco router command hierarchy):**
  - `>` = User EXEC mode (read-only, basic)
  - `#` = Privileged EXEC mode (full view access, use `enable` to get here)
  - `(config)#` = Global Configuration mode (make changes, use `configure terminal`)
- **Basic commands:**
  ```
  show version          → see router info
  show ip interface brief → see all interfaces and IP addresses
  show running-config   → see current configuration
  hostname R1           → name your router "R1"
  enable secret cisco   → set a password
  ```
- **SSH setup:** Securing your router so only you can log in remotely

**Assignment (Day 5):**
1. Install GNS3 or Packet Tracer
2. Create a simple topology: one router, one switch, two PCs
3. Name the router "MYROUTER1"
4. Configure a basic password and enable SSH
5. **Document:** Screenshot your topology + post the config commands you used. Title: "Day 5: My First Router Configuration"

---

### WEEK 2: Ethernet Switching and Layer 2

#### Day 6 — How a Switch Works: MAC Learning

**What it is:**  
A switch is a smart device that learns which device is connected to which port, so it only sends data where it needs to go — unlike a hub which blindly sends data everywhere.

**Subtopics:**
- **MAC Address:** Every network card has a unique 48-bit address (e.g., `AA:BB:CC:DD:EE:FF`). The first 24 bits = manufacturer ID, last 24 bits = unique device ID
- **MAC Address Table (CAM Table):** The switch's memory. It stores: "Port 1 → MAC AA:BB:CC:11:22:33"
- **Learning process:**
  1. **Learning:** PC1 sends a frame. Switch records "PC1's MAC is on Port 1"
  2. **Flooding:** If switch doesn't know where to send (unknown destination), it sends to ALL ports except the one it came from
  3. **Forwarding:** Once it knows the destination, it sends only to the correct port
  4. **Aging:** If a device is silent for 300 seconds, the switch forgets its MAC entry
- **Why flooding is dangerous at scale:** In a data center with 100,000 servers, flooding all unknown frames would melt the network. This is why large-scale data centers use VXLAN+EVPN (studied in Phase 4) to eliminate flooding.

**Assignment (Day 6):**
```
Lab: In Packet Tracer
1. Create topology: 3 PCs → 1 Switch
2. Ping PC2 from PC1 BEFORE adding any static configs
3. Run: show mac address-table on the switch
4. Observe how MAC entries appear after pings
5. Predict: what entries will appear if PC3 pings PC1?
```
**Document:** Screenshot the MAC table before and after pings. Explain what changed and why.

---

#### Day 7 — Collision Domains and Broadcast Domains

**What it is:**  
Understanding why switches replaced hubs and why VLANs replaced flat networks.

**Subtopics:**
- **Collision Domain:** The area where two devices can cause a collision if they transmit simultaneously. Each switch port = one collision domain. Hubs had ONE collision domain for all ports.
- **Broadcast Domain:** The area where a broadcast (sent to all devices) reaches. One VLAN = one broadcast domain. Too many devices in one broadcast domain = network slowdown.
- **ARP (Address Resolution Protocol):** "Who has IP 192.168.1.5? Tell 192.168.1.1" — this is a broadcast. If you have 10,000 devices, 10,000 devices receive every ARP. This is why VLANs matter.

**Assignment (Day 7):**
In Wireshark, filter by `arp`. Leave it running for 2 minutes. Count how many ARP broadcasts you see. 
**Document:** "Why Broadcasts Kill Large Networks" — explain what you observed

---

#### Day 8 — VLANs: Virtual Networks on One Physical Switch

**What it is:**  
VLANs allow you to divide one physical switch into multiple isolated virtual switches. The Finance department and Engineering department can be on the same switch hardware but completely isolated from each other.

**Subtopics:**
- **VLAN ID:** A number (1–4094) that tags each frame
- **Access Port:** A switch port that belongs to ONE VLAN. The device plugged in doesn't know about VLANs — it just sends normal traffic.
- **Trunk Port:** A switch port that carries MULTIPLE VLANs. Used to connect switches to switches and switches to routers.
- **802.1Q Standard:** The industry standard for VLAN tagging. It adds a 4-byte tag into the Ethernet frame header containing the VLAN ID.
- **Native VLAN:** Traffic that travels on a trunk WITHOUT a VLAN tag. VLAN 1 is the default native VLAN. Security risk: if misconfigured, attackers can "jump" VLANs. Best practice: change native VLAN to an unused VLAN number.
- **Configuration:**
  ```
  Switch(config)# vlan 10
  Switch(config-vlan)# name ENGINEERING
  Switch(config)# interface fastEthernet 0/1
  Switch(config-if)# switchport mode access
  Switch(config-if)# switchport access vlan 10
  ```

**Assignment (Day 8):**
```
Lab: Inter-VLAN ping test
- Create VLAN 10 (Engineering) and VLAN 20 (Finance)
- PC1 and PC2 in VLAN 10, PC3 in VLAN 20
- Confirm PC1 can ping PC2 but CANNOT ping PC3
- Document why this isolation happens
```

---

#### Day 9 — Trunking and Router-on-a-Stick

**What it is:**  
VLANs isolate networks. But what if Engineering needs to reach the internet (which Finance also uses)? You need inter-VLAN routing. "Router-on-a-Stick" is the classic solution.

**Subtopics:**
- **Sub-interfaces:** One physical router interface split into multiple logical interfaces, each serving one VLAN
- **Configuration:**
  ```
  Router(config)# interface GigabitEthernet0/0.10
  Router(config-subif)# encapsulation dot1q 10
  Router(config-subif)# ip address 192.168.10.1 255.255.255.0
  
  Router(config)# interface GigabitEthernet0/0.20
  Router(config-subif)# encapsulation dot1q 20
  Router(config-subif)# ip address 192.168.20.1 255.255.255.0
  ```
- **The trunk link:** The connection from the switch to the router must be a trunk, carrying both VLAN 10 and VLAN 20 frames

**Assignment (Day 9):**
Configure Router-on-a-Stick. PC in VLAN 10 should be able to ping PC in VLAN 20 (via the router).
**Document:** Draw the traffic path: "A packet from VLAN 10 to VLAN 20 takes this journey..."

---

#### Day 10 — Spanning Tree Protocol (STP): Preventing Network Loops

**What it is:**  
If you connect two switches with two cables (for redundancy), Ethernet frames will loop forever — like a phone call with infinite echo. STP blocks one path to prevent this. When the primary path fails, the blocked path unblocks.

**Subtopics:**
- **The loop problem:** Without STP, a broadcast frame circulates forever, exponentially multiplying (broadcast storm). Within seconds, the network CPU is at 100% and everything crashes.
- **How STP works:**
  1. Elect a Root Bridge (the switch with lowest priority, tie = lowest MAC)
  2. Every other switch finds its cheapest path to the Root Bridge (Root Port)
  3. On each network segment, one switch becomes the Designated Port (the one closest to root)
  4. All other ports in the segment are Blocked
- **STP Port States:** Blocking → Listening → Learning → Forwarding (classic STP takes 30-50 seconds)
- **RSTP (802.1w):** Rapid STP. Convergence in 1-2 seconds instead of 50. Uses proposal/agreement mechanism. This is what modern networks use.
- **Why MNCs avoid STP in data centers:** Modern data centers use a "Layer 3 to the edge" design (Spine-Leaf) where every link is a routed Layer 3 link. No Layer 2 loops = no STP needed. But enterprise campus networks still use STP heavily.

**Assignment (Day 10):**
```
Lab:
1. Build: 3 switches in a triangle (redundant connections)
2. Check which port STP blocked: show spanning-tree
3. Manually force a root bridge change: spanning-tree priority 0
4. Observe port state transitions
```
**Document:** "How STP Saved My Network (And Why It Sometimes Doesn't)" — explain the loop you would have had without STP

---

### WEEK 3: IP Addressing — The Mathematics of Networking

#### Days 11–12 — Binary and Subnetting

**What it is:**  
Every IP address is secretly a 32-bit binary number. To subnet (divide networks), you must understand binary arithmetic. This is the most important skill to master in early networking — every other concept depends on it.

**Binary to Decimal Conversion:**
```
Binary:  11000000 . 10101000 . 00000001 . 00000001
Decimal: 192      . 168      . 1        . 1

Each position in binary represents a power of 2:
128 | 64 | 32 | 16 | 8 | 4 | 2 | 1
  1 |  1 |  0 |  0 | 0 | 0 | 0 | 0  = 128 + 64 = 192
```

**Subnet Mask:**
- `255.255.255.0` = `/24` = first 24 bits are the NETWORK, last 8 bits are the HOST
- `255.255.255.128` = `/25` = first 25 bits are NETWORK, last 7 bits are HOST
- More network bits = smaller subnet (fewer hosts per subnet, more subnets)

**Subnetting Formula:**
```
Given: 192.168.1.0/24 → Split into 4 subnets

Step 1: We need 4 subnets → 2² = 4 → borrow 2 bits → /24 + 2 = /26
Step 2: Block size = 256 - 192 = 64 (from 4th octet of /26 mask: 11000000 = 192)
Step 3: Subnets:
  Subnet 1: 192.168.1.0/26   → Hosts: .1 to .62   → Broadcast: .63
  Subnet 2: 192.168.1.64/26  → Hosts: .65 to .126  → Broadcast: .127
  Subnet 3: 192.168.1.128/26 → Hosts: .129 to .190 → Broadcast: .191
  Subnet 4: 192.168.1.192/26 → Hosts: .193 to .254 → Broadcast: .255
```

**VLSM (Variable Length Subnet Masking):**  
Real-world networks need different sized subnets. Give the size that fits, not a one-size-fits-all.

**Assignment (Days 11–12):**
Given block 10.0.0.0/16, design subnets for:
- Sales dept: 500 hosts
- Engineering: 200 hosts
- Management: 30 hosts
- Point-to-point links: 2 hosts each (×5 links)

Calculate on paper first, then verify using: https://www.subnet-calculator.com  
**Document:** Post your full subnetting worksheet with work shown. Title: "How I Learned to Stop Wasting IPs"

---

#### Days 13–14 — IPv6: The Future Standard

**What it is:**  
IPv4 has ~4.3 billion addresses. We've run out. IPv6 has 340 undecillion addresses (a number so large it's incomprehensible). Every MNC is dual-stacking (running both IPv4 and IPv6).

**Subtopics:**
- **Format:** 128 bits, written in hexadecimal: `2001:0db8:85a3:0000:0000:8a2e:0370:7334`
- **Abbreviation rules:** 
  - Leading zeros in a group can be removed: `0db8` → `db8`
  - Consecutive all-zero groups can be replaced with `::` (only once per address)
  - `2001:0db8:0000:0000:0000:0000:0370:7334` → `2001:db8::370:7334`
- **Address Types:**
  - `fe80::/10` = Link-Local: auto-assigned, only works on local segment (like a street address that only works in your neighborhood)
  - `2000::/3` = Global Unicast: routable on the internet (like a worldwide postal address)
  - `fc00::/7` = Unique Local: private IPv6 (equivalent to 192.168.x.x in IPv4)
- **SLAAC:** Instead of DHCP, IPv6 devices can configure their own address by combining the network prefix (from the router's advertisement) with their MAC address

**Assignment (Days 13–14):**
1. On your PC, run `ipconfig /all` (Windows) or `ip addr` (Linux)
2. Find your link-local IPv6 address (starts with fe80)
3. In GNS3, configure a dual-stack router with both IPv4 and IPv6
4. Ping between hosts using IPv6
**Document:** "IPv6: Why Your Router Has Two Addresses" — explain link-local vs global

---

#### Day 15 — DHCP and DNS: The Services That Make IP Usable

**What it is:**  
IP addresses are numbers. DHCP automatically hands them out so you don't configure every device manually. DNS converts names like "google.com" into IP addresses like "142.250.190.78".

**Subtopics:**
- **DHCP Process (DORA):**
  - **D**iscover: Client broadcasts "Anyone give me an IP?"
  - **O**ffer: DHCP server responds "I offer you 192.168.1.50"
  - **R**equest: Client says "I'll take 192.168.1.50"
  - **A**cknowledge: Server confirms "It's yours for 8 hours"
- **DHCP Lease Time:** The IP is "rented." After the lease expires, the device must renew or get a new IP.
- **DNS Resolution:** When you type google.com:
  1. Your PC checks its local cache (did I look this up recently?)
  2. Asks your ISP's DNS server
  3. ISP may ask a root server → then TLD server (.com) → then Google's authoritative DNS
  4. Gets back: "google.com = 142.250.190.78"
  5. Your browser connects to 142.250.190.78

**Assignment (Day 15):**
1. In Wireshark, filter by `dhcp` — see the 4-step DORA process when a device connects
2. Filter by `dns` — search for any website and watch the DNS query and response
3. Identify the query type (A record for IPv4, AAAA for IPv6)
**Document:** Diagram the DORA process and DNS resolution chain

---

### WEEK 4: IP Routing — Teaching Packets Where to Go

#### Days 16–17 — Static Routing

**What it is:**  
Routing is the process of deciding which path a packet takes through a network. Static routing is where YOU manually tell the router the path. Like giving someone printed directions instead of GPS.

**Subtopics:**
- **Routing Table:** The router's "map." Contains: Network destination, Next hop (which neighbor router to send to), Exit interface
- **Administrative Distance (AD):** When multiple routing sources say different things about the same destination, the router picks the most trustworthy source:
  - Connected interface: AD 0 (most trusted — it's directly attached)
  - Static route: AD 1
  - OSPF: AD 110
  - BGP: AD 20 (eBGP) / 200 (iBGP)
- **Longest Prefix Match:** Router has two routes: `10.1.1.0/24` and `10.1.1.0/25`. A packet to `10.1.1.100` — which route wins? The `/25` wins because it's MORE specific. This is the most important rule in routing.
- **Floating Static Route:** A static route with high AD (e.g., 254) — only used if the primary route (e.g., from OSPF) disappears. Acts as a backup.

**Commands:**
```
ip route 192.168.2.0 255.255.255.0 10.0.0.2    ← "To reach 192.168.2.x, send to 10.0.0.2"
ip route 0.0.0.0 0.0.0.0 10.0.0.1              ← Default route: "For everything else, send here"
show ip route                                    ← See the routing table
```

**Assignment (Days 16–17):**
```
Lab: 3 routers in a line: R1 — R2 — R3
- Configure IPs on each link
- Configure static routes so R1 can ping R3's far interface
- Break the R1–R2 link: observe that traffic stops (no dynamic failover with static routes)
- Add a floating static route via a different path
```
**Document:** Draw your topology with all IP addresses labeled. Explain why static routing doesn't scale.

---

#### Days 18–19 — First Hop Redundancy: HSRP

**What it is:**  
Every device (PC, printer, server) needs a default gateway — the router it sends traffic to. If that router fails, everything on the network loses internet access. HSRP creates a "virtual router" that floats between two physical routers.

**Subtopics:**
- **The Problem:** PC has gateway set to 192.168.1.1. If Router A (192.168.1.1) fails, PC can't reach anywhere.
- **HSRP Solution:** 
  - Router A and Router B both participate in HSRP
  - They create a virtual IP (VIP) e.g., 192.168.1.254 and virtual MAC
  - PC uses 192.168.1.254 as its gateway
  - Router A is "Active" (responding to the virtual IP)
  - Router B is "Standby" (waiting)
  - If Router A fails, Router B takes over the virtual IP in ~3 seconds
- **VRRP:** The open standard version of HSRP (works across vendors)
- **GLBP:** Adds load balancing — both routers actively forward traffic

**Assignment (Days 18–19):**
Configure HSRP between two routers. Start a continuous ping to an external IP. Shut down the active router's interface. The ping should drop for only 3 seconds, then resume via the standby router.
**Document:** Capture the Wireshark trace showing HSRP failover. Post with explanation.

---

#### Day 20 — Week 1–4 Review + Phase 1 Milestone Project

**🏆 MILESTONE PROJECT 1: The Campus Network**

**Scenario:** You've been hired as a junior network engineer at a mid-size company. Your job: design and implement the office network from scratch.

**Requirements:**
- 3 VLANs: Management (VLAN 10), Engineering (VLAN 20), Finance (VLAN 30)
- All VLANs can reach the internet (via router)
- Finance cannot communicate with Engineering (security requirement)
- Redundant router (HSRP) for high availability
- DHCP service per VLAN
- Document every IP address in a spreadsheet (IPAM)

**Deliverables (post all to GitHub + write a blog post):**
1. Network diagram (draw on https://draw.io — free)
2. Complete configuration files for all devices
3. Screenshot of successful pings between allowed VLANs
4. Screenshot of failed ping between Finance and Engineering (proving isolation)
5. HSRP failover test result

**Real-world connection:** This is exactly what network engineers build in real offices. The VLAN isolation between Finance and Engineering is a real compliance requirement (PCI-DSS for financial data).

---

## 🏗️ PHASE 2: Advanced Routing and Switching (Weeks 5–10)
### "The CCNP Level — What MNCs Actually Run"

**Why now?** Phase 1 gave you the vocabulary. Phase 2 gives you the grammar. MNCs don't use static routes — they use dynamic protocols that automatically discover paths and recover from failures.

---

### WEEK 5: OSPF — The Enterprise Routing Standard

#### Days 21–22 — OSPF Fundamentals

**What it is:**  
OSPF (Open Shortest Path First) is a routing protocol where every router builds a complete map of the entire network (like Google Maps) and independently calculates the best path to every destination. If a link fails, every router updates its map and recalculates within milliseconds.

**Why OSPF over static routes?**
- 100 routers × 100 destinations = 10,000 static routes to maintain manually
- OSPF: add one router, it automatically appears in everyone's map

**Subtopics:**
- **Link State Database (LSDB):** Every OSPF router maintains an identical copy of the entire network map
- **LSAs (Link State Advertisements):** The "map updates" routers send each other
  - Type 1 (Router LSA): "Here are MY links" — stays within one OSPF area
  - Type 2 (Network LSA): Created by the Designated Router on Ethernet segments
  - Type 3 (Summary LSA): Created by ABRs, summarizes routes between areas
- **Dijkstra Algorithm:** OSPF uses this mathematical algorithm to find the shortest path in the LSDB. You don't need to understand the math — just know that OSPF runs it every time the topology changes.
- **Hello Packets:** OSPF routers send Hello packets every 10 seconds. This is how they discover neighbors. Dead interval = 40 seconds (4 × Hello). If no Hello received for 40 seconds, neighbor is declared dead.
- **OSPF Areas:** Large networks split into areas to limit recalculation scope:
  - Area 0 = Backbone area (mandatory)
  - Area 1, 2, etc. = Regular areas
  - All areas must connect to Area 0

**Assignment (Days 21–22):**
```
Lab:
1. Build a 4-router OSPF network (2 in Area 0, 2 in Area 1)
2. Capture Hello packets in Wireshark: filter by ospf
3. Run: show ip ospf database — identify Type 1 and Type 3 LSAs
4. Shut down a link — watch OSPF reconverge (show ip ospf neighbor)
```
**Document:** "OSPF Explained by Drawing Maps" — use an analogy of Google Maps to explain LSDB

---

#### Days 23–25 — OSPF Advanced Topics and Troubleshooting

**Subtopics:**
- **DR/BDR Election:** On broadcast networks (Ethernet), OSPF elects one Designated Router (DR) and one Backup DR (BDR). All other routers (DROthers) only form full adjacency with DR/BDR. This reduces OSPF traffic from O(n²) to O(n).
- **OSPF Network Types:**
  - Broadcast: Ethernet (DR/BDR election happens)
  - Point-to-Point: Serial links (no DR election, faster convergence)
- **Stub Areas:** Remote office areas that don't need to know all routes — just send everything to Area 0. Reduces routing table size at branch routers.
- **Route Summarization:** At Area Border Routers (ABRs), advertise one summarized route instead of 100 individual routes. E.g., instead of advertising 10.1.0.0/24 through 10.1.99.0/24, advertise 10.1.0.0/16.
- **Common OSPF failures:**
  - **ExStart state (stuck):** MTU mismatch between neighbors. Fix: `ip mtu 1500` on both sides
  - **2-WAY state:** Normal for DROther-to-DROther. Not a bug.
  - **Hello timer mismatch:** Both sides must have same Hello/Dead timers. Fix: match timers.

**Assignment (Day 25 — Break-Fix Lab):**
Download a "broken OSPF lab" from GNS3Vault. The symptoms: OSPF stuck in ExStart. Diagnose using debug commands. Find the MTU mismatch. Fix it. Document the Root Cause Analysis (RCA).
**Document:** Your RCA report — this is exactly how MNCs document post-incident reviews.

---

### WEEK 6: EIGRP — The Cisco-Enhanced Protocol

#### Days 26–28 — EIGRP Concepts and Tuning

**What it is:**  
EIGRP (Enhanced Interior Gateway Routing Protocol) is Cisco's advanced distance-vector protocol. It's faster than OSPF at convergence (backup paths are pre-calculated) and easier to configure.

**Subtopics:**
- **DUAL Algorithm (Diffusing Update Algorithm):** Pre-calculates loop-free backup paths. When primary path fails, it instantly switches to the pre-calculated backup without recalculation.
- **Terminology:**
  - **Feasible Distance (FD):** My router's total cost to reach a destination (the metric value I see in my routing table)
  - **Reported Distance (RD):** My neighbor's cost to the same destination (what they tell me)
  - **Successor:** The primary route (lowest FD)
  - **Feasible Successor:** The backup route (must satisfy: RD < FD of successor — guarantees loop-free)
- **Feasibility Condition:** If a neighbor's reported distance is lower than my feasible distance to the destination, it's a safe backup (guaranteed not to route back through me). This is the core of DUAL's loop prevention.
- **Metrics:** EIGRP uses Bandwidth and Delay by default (K-values). You can manipulate delay to influence path selection.
- **Unequal Cost Load Balancing:** Unique to EIGRP. The `variance` command allows using backup paths even if they're slower — proportionally distributing traffic across multiple paths.

**Assignment (Days 26–28):**
```
Lab:
1. Configure EIGRP on a 4-router topology with two paths to the destination
2. show ip eigrp topology — identify Successor and Feasible Successor
3. Use variance 2 to enable unequal load balancing
4. Write a comparison report: OSPF vs EIGRP — which does your company need?
```
**Document:** The OSPF vs EIGRP comparison post — this is a common interview question.

---

### WEEK 7: BGP — The Protocol That Runs the Internet

#### Days 29–33 — BGP Deep Dive

**What it is:**  
BGP (Border Gateway Protocol) is the routing protocol used between internet service providers and between large organizations. Every time you go to any website, BGP determined the global path. Every FAANG company (Facebook, Apple, Amazon, Netflix, Google) uses BGP internally.

**Why BGP is different from OSPF:**
- OSPF: Designed for speed and convergence (seconds). Used INSIDE one organization.
- BGP: Designed for policy and scale (can hold 900,000+ internet routes). Used BETWEEN organizations.

**Subtopics:**
- **ASN (Autonomous System Number):** A number that identifies an organization. Google is AS15169. Jio is AS55836. Your home ISP has one.
- **eBGP vs iBGP:**
  - External BGP (eBGP): Between two different ASNs (e.g., your company to your ISP)
  - Internal BGP (iBGP): Within the same ASN (e.g., between two routers inside Google's network)
- **BGP Finite State Machine:** BGP neighbors go through states before exchanging routes:
  Idle → Connect → Active → OpenSent → OpenConfirm → **Established** (healthy!)
  - "Active" state = stuck, trying to connect. Usually means TCP connectivity issue on port 179.
- **BGP Path Selection (13-step algorithm):** When BGP has multiple paths to the same destination, it picks the best using these steps (in order):
  1. Weight (Cisco proprietary, highest wins, local router only)
  2. Local Preference (higher wins, propagates within AS)
  3. Locally Originated (prefer routes you originated)
  4. AS Path Length (shorter wins — fewer hops through other ASNs)
  5. Origin Code (IGP > EGP > Incomplete)
  6. MED (lower wins — hint to external AS which entry point to use)
  7. eBGP > iBGP
  8. IGP metric to Next Hop (lower wins)
  ... and more

**Traffic Engineering with BGP:**
- **Local Preference:** Control which ISP your traffic goes OUT through ("prefer ISP A for all outbound")
- **AS Path Prepending:** Make your path look artificially longer to influence which ISP external traffic uses to reach YOU ("make ISP B the less preferred entry point")

**Assignment (Days 29–33):**
```
Lab: "The BGP Game"
- 3 ASNs: Your Company (AS65001), ISP_A (AS100), ISP_B (AS200)
- Configure eBGP peering to both ISPs
- Use Local Preference to force all your outbound traffic through ISP_A
- Use AS Path Prepending on routes advertised to ISP_B (making them look 3 hops longer)
- Verify: inbound traffic uses ISP_A
```
**Document:** "How Facebook Engineers Route Internet Traffic" — explain AS Path Prepending with the real-world analogy of telling customers "please use the front door, not the back"

---

### WEEK 8: Advanced Switching and Security

#### Days 34–37 — EtherChannel and Security Features

**Subtopics:**
- **EtherChannel (LACP):** Bundling multiple physical links into one logical link. 4 × 10Gbps links = one 40Gbps logical interface (with load balancing).
  - Important caveat: one TCP flow only uses ONE physical link (based on hash). So for single large file transfers, you won't see 40Gbps.
- **Port Security:** Lock a switch port to only allow specific MAC addresses. If a different device plugs in, the port shuts down.
- **DHCP Snooping:** The switch builds a table of "trusted" IP-to-MAC-to-Port mappings. Any DHCP server not on a "trusted" port is blocked. Prevents rogue DHCP servers from handing out bad gateway IPs.
- **Dynamic ARP Inspection (DAI):** ARP poisoning is a man-in-the-middle attack. The attacker sends fake ARP replies saying "I am the gateway." DAI validates ARP replies against the DHCP snooping table and drops invalid ones.
- **802.1X (Port-based Network Access Control):** Before a device can use a network port, it must authenticate (username/password or certificate). The switch acts as an enforcer. Used in every large enterprise.

**Assignment (Day 37 — Security Attack Lab):**
```
Advanced Lab (use Kali Linux VM):
1. Set up a small network: PC1, PC2, Switch, Router
2. Use Kali Linux and the "arpspoof" tool to perform ARP poisoning
3. Observe traffic redirection in Wireshark
4. Enable DAI on the switch
5. Verify the attack no longer works
```
**Document:** "I Hacked My Own Network (And Then Fixed It)" — a post showing the attack and the defense. This type of content gets attention from security recruiters.

---

### WEEK 9: WAN Technologies and MPLS

#### Days 38–43 — MPLS and VRFs

**What it is:**  
MPLS (Multiprotocol Label Switching) is how ISPs and large enterprises create private networks over shared infrastructure. Instead of routing by IP address (slow, requires looking up long addresses), MPLS routes by short 20-bit labels (fast, hardware-level).

**Subtopics:**
- **Why MPLS:** IP routing requires looking up 32-bit or 128-bit addresses. Labels are only 20 bits — faster lookup. More importantly, MPLS creates "tunnels" that separate customers.
- **Labels:** A 4-byte header added between Layer 2 and Layer 3 headers (called "Layer 2.5")
  - **Push:** Add a label to the packet (at the entry of the MPLS network)
  - **Swap:** Change the label at each hop
  - **Pop:** Remove the label (at the exit of the MPLS network)
- **LDP (Label Distribution Protocol):** How routers exchange and learn labels
- **VRF (Virtual Routing and Forwarding):** Creates separate routing tables for different customers on the same router. Customer A's 10.0.0.0/8 and Customer B's 10.0.0.0/8 can coexist on the same router without conflict — they're in separate VRFs.
- **MPLS L3VPN:** Service providers use MPLS + VRF + MP-BGP to create private L3 VPNs for enterprise customers. The enterprise thinks it has its own private network — the SP infrastructure is shared but invisible.

**Assignment (Days 38–43):**
```
Lab: Build a mini-ISP
- 3 P (Provider core) routers running MPLS + OSPF
- 2 PE (Provider Edge) routers at the edge
- 2 CE (Customer Edge) routers representing customer sites
- Create VRF "Customer_A" and VRF "Customer_B"
- Verify Customer_A can reach its own sites but NOT Customer_B
```
**Document:** "How Jio Gives You a Private Network (They're Lying — It's Shared)" — explain VRFs

---

### WEEK 10: Phase 2 Capstone + Break-Fix Challenge

#### Days 44–50 — Integration and Troubleshooting

**The MNC Interview Skill:** MNCs interview network engineers by giving them a broken network and saying "fix it, tell me what's wrong, and document the root cause." This week is entirely dedicated to that skill.

**Break-Fix Labs:**
1. OSPF neighbor stuck in ExStart (MTU mismatch)
2. BGP stuck in Active state (ACL blocking port 179)
3. VLAN 20 traffic not reaching VLAN 30 (missing trunk config)
4. EIGRP routes not redistributing into OSPF
5. HSRP not failing over (wrong priority configured)

Resources for labs: https://www.gns3vault.com (free)

**🏆 PHASE 2 CAPSTONE PROJECT: The Service Provider Simulation**

Build a mini-ISP network:
- 3 core routers (MPLS backbone) running OSPF
- 2 edge routers (PE) connecting to customers
- Customer A: 2 sites, full connectivity between sites
- Customer B: 3 sites, full connectivity between sites
- Customer A and B completely isolated from each other
- BGP for customer-to-ISP routing

**Deliverables:**
1. Full network diagram on draw.io
2. All configuration files in a GitHub repository
3. Evidence of working L3VPN (ping between Customer A sites)
4. Evidence of isolation (failed ping between Customer A and Customer B)
5. Root Cause Analysis document for at least 2 break-fix scenarios you solved

---

## 🏗️ PHASE 3: Automation and Programmability (Weeks 11–13)
### "Turning Network Engineers into Software Engineers"

**Why now?** You know how networks work manually. Now you learn to automate. This is where salary jumps from ₹8LPA to ₹25LPA+ in India.

**The mindset shift:** Instead of typing commands into 10 routers one by one, you write a Python script that does it to 1,000 routers in 30 seconds.

**Tools to install this phase:**
- Python 3.12 (python.org — free)
- VS Code with Python extension
- Ansible (pip install ansible)
- Git (git-scm.com — free)
- GitHub account (github.com — free)

---

### WEEK 11: Python for Complete Beginners (Networking Focus)

#### Day 51 — Python Setup and Your First Script

**Starting from absolute zero:**

```python
# This is a comment. Python ignores it.
# This is your first Python script.

print("Hello, Network Engineer!")

# Variables store information
router_name = "R1"
router_ip = "192.168.1.1"

print("Router:", router_name)
print("IP:", router_ip)
```

**Setup steps:**
1. Download Python: https://python.org (click "Downloads")
2. Install VS Code: https://code.visualstudio.com
3. In VS Code, install the "Python" extension (Ctrl+Shift+X → search Python)
4. Create a file `hello.py`, type the code above, press F5 to run

**What is a Virtual Environment?**  
A "bubble" that contains Python packages for one project without affecting other projects.
```bash
python -m venv mynetwork       ← Creates the bubble
source mynetwork/bin/activate  ← Enter the bubble (Mac/Linux)
mynetwork\Scripts\activate     ← Enter the bubble (Windows)
pip install netmiko            ← Install a package inside the bubble
```

**Assignment (Day 51):**
Write a Python script that:
- Stores your name, city, and learning goal in variables
- Prints a formatted introduction: "My name is [name]. I'm learning networking in [city]. My goal: [goal]"
**Document:** Post your first Python script on GitHub. Write "Day 1 of Python: What I Learned in 1 Hour" on Hashnode.

---

#### Day 52 — Data Structures: Lists and Dictionaries

**The most important Python concepts for networking:**

```python
# List: ordered collection (like a numbered list)
routers = ["192.168.1.1", "192.168.1.2", "192.168.1.3"]
print(routers[0])   # Prints first item: "192.168.1.1"

# Loop through a list:
for ip in routers:
    print("Checking router:", ip)

# Dictionary: key-value pairs (like a lookup table)
router_info = {
    "hostname": "R1",
    "ip": "192.168.1.1",
    "vendor": "Cisco",
    "model": "ISR4451"
}
print(router_info["hostname"])  # Prints: "R1"

# List of dictionaries (how you'd store multiple routers):
all_routers = [
    {"hostname": "R1", "ip": "192.168.1.1"},
    {"hostname": "R2", "ip": "192.168.1.2"},
    {"hostname": "R3", "ip": "192.168.1.3"}
]

for router in all_routers:
    print(f"Router {router['hostname']} is at {router['ip']}")
```

**JSON (JavaScript Object Notation):**  
APIs and network devices return data in JSON format. Python dictionaries and JSON are almost identical — this is why dictionaries are critical for networking automation.

**Assignment (Day 52):**
Create a Python script that:
- Stores 5 routers (hostname, IP, location) in a list of dictionaries
- Loops through and prints each router's info in a formatted table
**Document:** Post this as "Python Dictionaries: A Network Engineer's Best Friend"

---

#### Day 53–54 — Netmiko: SSH into Real Routers with Python

**What Netmiko is:**  
A Python library that automates SSH connections to network devices. Instead of manually opening a terminal and typing commands, Python does it.

```python
from netmiko import ConnectHandler

# Define your router
cisco_router = {
    'device_type': 'cisco_ios',
    'host': '192.168.1.1',        # Router's IP
    'username': 'admin',
    'password': 'cisco123',
}

# Connect and run commands
try:
    connection = ConnectHandler(**cisco_router)
    output = connection.send_command('show ip interface brief')
    print(output)
    connection.disconnect()
except Exception as e:
    print(f"Connection failed: {e}")
```

**Handling multiple devices:**
```python
from netmiko import ConnectHandler

routers = [
    {'device_type': 'cisco_ios', 'host': '192.168.1.1', 'username': 'admin', 'password': 'cisco123'},
    {'device_type': 'cisco_ios', 'host': '192.168.1.2', 'username': 'admin', 'password': 'cisco123'},
]

for router in routers:
    conn = ConnectHandler(**router)
    hostname = conn.find_prompt().replace('#', '')
    output = conn.send_command('show version')
    
    # Save to a file named after the hostname
    with open(f"{hostname}_backup.txt", 'w') as f:
        f.write(output)
    
    conn.disconnect()
    print(f"Backed up {hostname}")
```

**Assignment (Days 53–54):**
Write a script that:
1. Connects to all your GNS3 lab routers
2. Runs `show running-config` on each
3. Saves output to files named `hostname_YYYYMMDD.txt`
4. Handles failures gracefully (try/except — prints "Failed" instead of crashing)
**Document:** "I Backed Up 5 Routers in 5 Seconds with Python" — show the before (manual) vs after (automated)

---

#### Day 55 — Control Flow: Making Decisions in Python

```python
# If statements (decisions):
interface_status = "down"

if interface_status == "up":
    print("Interface is healthy")
elif interface_status == "down":
    print("ALERT: Interface is down! Notifying team.")
else:
    print("Unknown status")

# Functions (reusable blocks of code):
def check_interface(hostname, status):
    if status == "down":
        return f"ALERT: {hostname} interface is DOWN"
    return f"OK: {hostname} interface is UP"

result = check_interface("R1", "down")
print(result)
```

**Assignment (Day 55):**
Write a Python script using Netmiko that:
1. Connects to a router
2. Runs `show ip interface brief`
3. Parses the output for any interface showing "down"
4. Prints an alert for each down interface
**Document:** "Building a Network Health Checker in 30 Lines of Python"

---

### WEEK 12: Ansible — Configuration Management at Scale

#### Days 56–58 — Ansible Fundamentals

**What it is:**  
Ansible is a tool that configures hundreds of devices simultaneously using YAML files (playbooks). It's agentless — no software needed on the devices.

**Install Ansible:**
```bash
pip install ansible
pip install ansible-pylibssh
```

**The Inventory file (hosts.ini) — listing your devices:**
```ini
[routers]
R1 ansible_host=192.168.1.1
R2 ansible_host=192.168.1.2
R3 ansible_host=192.168.1.3

[all:vars]
ansible_user=admin
ansible_password=cisco123
ansible_connection=network_cli
ansible_network_os=ios
```

**A Playbook (YAML) — what to do to those devices:**
```yaml
---
- name: Configure NTP on all routers
  hosts: routers
  gather_facts: false
  
  tasks:
    - name: Set NTP server
      cisco.ios.ios_config:
        lines:
          - ntp server 8.8.8.8
          - ntp server 8.8.4.4
    
    - name: Set Syslog server
      cisco.ios.ios_config:
        lines:
          - logging host 192.168.100.50
          - logging trap informational
```

**Run the playbook:**
```bash
ansible-playbook -i hosts.ini ntp_config.yml
```

**Idempotency:** Run it 10 times — same result. Ansible checks if the config already exists before applying. This is the core philosophy of "Infrastructure as Code."

**Assignment (Days 56–58):**
Write an Ansible playbook that ensures ALL routers have:
- NTP servers configured
- Syslog server configured
- Domain name set
- Password encryption enabled
Test by running it twice — verify zero changes on second run (idempotency).
**Document:** "How I Configured 10 Routers in 30 Seconds with Ansible"

---

#### Day 59–60 — Jinja2 Templating: Config as Code

**What it is:**  
Instead of hardcoding configs, you create a template with variables. Ansible fills in the variables per device. Same template, different data = unique configs for each device.

**Template file (router_template.j2):**
```
hostname {{ hostname }}
!
interface GigabitEthernet0/0
 ip address {{ wan_ip }} {{ wan_mask }}
 no shutdown
!
interface GigabitEthernet0/1
 ip address {{ lan_ip }} {{ lan_mask }}
 no shutdown
!
ip route 0.0.0.0 0.0.0.0 {{ default_gateway }}
!
ntp server {{ ntp_server }}
```

**Variables file (host_vars/R1.yml):**
```yaml
hostname: R1
wan_ip: 203.0.113.1
wan_mask: 255.255.255.252
lan_ip: 192.168.10.1
lan_mask: 255.255.255.0
default_gateway: 203.0.113.2
ntp_server: 8.8.8.8
```

**Assignment (Days 59–60):**
Create a Jinja2 template for a standard branch office router. Create 5 different host_vars files (for 5 different branches). Use Ansible to render and push configurations.
**Document:** "The Template Revolution: How I Stopped Copy-Pasting Router Configs"

---

### WEEK 13: REST APIs — Talking to Modern Network Systems

#### Days 61–65 — APIs and the Requests Library

**What APIs are:**  
Modern network systems (Cisco DNA Center, AWS, Palo Alto, Juniper Mist) have REST APIs. Instead of logging in through SSH, you send HTTP requests (like a web browser) and get back data in JSON format.

**HTTP Methods:**
- `GET` — Read data ("give me the list of devices")
- `POST` — Create data ("add this new VLAN")
- `PUT` — Update data ("change this interface config")
- `DELETE` — Remove data ("delete this route")

**Python requests library:**
```python
import requests
import json

# Most APIs require a token (like a temporary password)
# First, get a token:
auth_url = "https://sandboxdnac.cisco.com/api/system/v1/auth/token"
response = requests.post(
    auth_url,
    auth=("devnetuser", "Cisco123!"),
    headers={"Content-Type": "application/json"}
)
token = response.json()["Token"]

# Now use the token to get device inventory:
inventory_url = "https://sandboxdnac.cisco.com/api/v1/network-device"
response = requests.get(
    inventory_url,
    headers={
        "X-Auth-Token": token,
        "Content-Type": "application/json"
    }
)

devices = response.json()["response"]
for device in devices:
    print(f"Hostname: {device['hostname']}, IP: {device['managementIpAddress']}")
```

**Free API sandboxes to practice (no hardware needed):**
- Cisco DevNet Sandbox: https://devnetsandbox.cisco.com (free, register once)
- ReqRes API (fake REST API for practice): https://reqres.in
- Public IP Geolocation API: https://ipapi.co/json/

**Assignment (Days 61–65):**
Write a Python script that:
1. Authenticates to Cisco DNA Center sandbox
2. Gets all devices in inventory
3. Filters for devices with "Router" in the family
4. Outputs a CSV file: Hostname, IP, Platform, Software Version
**Document:** "How Netflix Doesn't Log into Routers (They Use APIs)" — explain API-driven networking

---

**🏆 PHASE 3 CAPSTONE PROJECT: The Automated Compliance Auditor**

**Real-world problem this solves:** A company has 200 routers. Security policy requires:
- Password encryption enabled
- No Telnet (only SSH)
- NTP server configured
- No unused admin accounts

Manual audit: 2 engineers × 3 days = 6 person-days.  
Automated audit: 1 script × 3 minutes.

**Build:**
1. Python script using Netmiko to connect to all lab routers
2. Check each compliance requirement
3. For any violation: automatically apply the fix
4. Log all actions to a CSV: Device, Check, Status, Action Taken, Timestamp
5. Email a summary report (use Python's `smtplib` with Gmail SMTP)

**Tech Stack:**
- Python 3.12 + Netmiko + smtplib
- Git for version control
- GitHub repository for the code
- README.md documenting how to use it

This is a **real tool** that network engineers actually build and use. Put it on your GitHub profile.

---

## 🏗️ PHASE 4: SDN and Data Center Fabrics (Weeks 14–16)
### "How Modern Data Centers Are Built"

#### Days 66–70 — Software-Defined Networking (SDN)

**What it is:**  
Traditional networking: every router/switch is a brain AND a muscle. It decides the path AND forwards the packets.  
SDN: Separate the brain (controller, runs on a server) from the muscle (switch, just forwards packets). The controller programs all switches centrally.

**Why Google Built SDN (B4 Network — Real Case Study):**
- Traditional WAN links ran at 30-40% utilization (wasted capacity)
- Expensive dark fiber sat idle while other links were congested
- Google built a centralized SDN controller that sees ALL global demand
- It programs switches to use near 100% of all links by prioritizing traffic
- Result: Saved hundreds of millions in infrastructure costs

**Subtopics:**
- **OpenFlow:** The original SDN protocol. The controller installs "flow rules" in switches via OpenFlow. Each rule says: "If you see a packet with these headers, send it out this port"
- **Mininet:** Free, open-source network simulator for SDN. Creates virtual networks on your Linux machine.
- **Control Plane vs Data Plane:** Control plane = routing decisions (which path). Data plane = actual packet forwarding (moving the packet).
- **Cisco ACI:** Enterprise SDN for data centers. Instead of per-device configs, you define "application policies" and ACI pushes configs everywhere.
- **Cisco DNA Center:** Campus SDN. You say "I want VLAN 10 for Engineering everywhere" — DNA Center programs all switches.

**Assignment (Days 66–70):**
1. Install Mininet: http://mininet.org (runs on Ubuntu VM)
2. Create a simple topology with Python + Mininet
3. Install RYU controller (pip install ryu)
4. Write a Python RYU app that acts as a simple learning switch
5. Use the Cisco DevNet sandbox to explore DNA Center API
**Document:** "How Google Drives WAN Links to 100% (The B4 Story)" — deep analysis post

---

#### Days 71–77 — VXLAN and Spine-Leaf Data Center Architecture

**What it is:**  
Modern data centers use a completely different architecture than traditional networks. Understanding this is essential for anyone aiming at cloud/data center roles.

**The Problem with Traditional Data Centers:**
- Old design: Big hierarchical tree (Core → Distribution → Access)
- Problem 1: East-West traffic (server-to-server) has to go all the way up to Core and back down — high latency
- Problem 2: VLANs limited to 4,094 IDs — not enough for cloud providers with millions of tenants
- Problem 3: STP blocks redundant paths — wasted capacity

**The Solution: Spine-Leaf (Clos Network)**
```
     [Spine 1]  [Spine 2]  [Spine 3]    ← 3 spine switches (brain layer)
        |||         |||         |||
     [Leaf 1]  [Leaf 2]  [Leaf 3]       ← Every leaf connects to every spine
        |           |           |
    [Servers]   [Servers]   [Servers]
```

- Every leaf-to-spine path is equal latency (deterministic)
- No STP needed (all links are Layer 3, routed)
- ECMP (Equal-Cost Multi-Path) uses ALL paths simultaneously
- Adding capacity: add a leaf switch (plug into all spines) — takes 30 minutes

**VXLAN (Virtual Extensible LAN):**
- Wraps Layer 2 Ethernet frames inside UDP packets (port 4789)
- Allows you to stretch one VLAN across a Layer 3 network
- Supports 16 million VNIs (Virtual Network Identifiers) — vs 4,094 VLANs
- Used by AWS, Meta, Google, every major cloud provider

**EVPN (Ethernet VPN):**
- Uses MP-BGP to advertise MAC addresses as routes
- Eliminates "flood and learn" — no more broadcasting to find MAC addresses
- Control plane for VXLAN in modern data centers

**Assignment (Days 71–77):**
```
Lab in GNS3:
1. Build a 2-spine, 4-leaf topology
2. Configure BGP between all spines and leaves (eBGP underlay)
3. Configure VXLAN tunnels (NVE interfaces)
4. Configure BGP EVPN overlay
5. Verify: VM on Leaf 1 can ping VM on Leaf 4 (going through spines)
```
**Document:** "Why AWS Doesn't Use VLANs (And What They Use Instead)" — explain VXLAN in plain English

---

## 🏗️ PHASE 5: Cloud Networking (Weeks 17–20)
### "The Network Is Now Software"

**Setup:** Create an AWS account (free tier): https://aws.amazon.com/free/  
Free tier gives: 750 hours/month of EC2, 5GB S3, various other services — enough for all labs.

---

### WEEK 17: AWS VPC Fundamentals

#### Days 78–82 — Building Your First Cloud Network

**Mapping AWS to Traditional Networking:**

| Traditional | AWS Equivalent | What It Does |
|---|---|---|
| Data Center | VPC (Virtual Private Cloud) | Your private network space in AWS |
| Subnet | Subnet | Divides the VPC into sections |
| Router | Route Table | Determines where traffic goes |
| Internet Modem | Internet Gateway (IGW) | Connects VPC to internet |
| Firewall | Security Group + NACL | Controls who can access what |
| NAT Router | NAT Gateway | Lets private subnets reach internet |
| Dedicated line | Direct Connect | Private fiber to AWS |

**Public vs Private Subnet:**
- Public subnet: Has a route to the Internet Gateway (internet accessible)
- Private subnet: No route to Internet Gateway (internal only)
- Private subnet + NAT Gateway: Can initiate outbound connections (updates, patches) but internet cannot initiate inbound connections to it

**Security Groups (Stateful Firewall):**
```
Inbound Rules:
- Allow TCP 22 (SSH) from 0.0.0.0/0   ← Anyone can SSH in
- Allow TCP 80 (HTTP) from 0.0.0.0/0  ← Anyone can browse
- Allow TCP 443 (HTTPS) from 0.0.0.0/0

Outbound Rules:
- Allow All (default)                  ← Stateful: return traffic auto-allowed
```

**NACLs (Stateless Firewall) — subnet-level:**
- Must allow BOTH inbound AND outbound traffic explicitly
- Ephemeral ports (1024–65535): the random ports client uses for responses
- Common mistake: allow TCP 80 inbound but forget to allow ephemeral ports outbound → connection appears to work but responses never return

**Assignment (Days 78–82):**
1. Create a VPC: 10.0.0.0/16
2. Create 2 public subnets and 2 private subnets (across 2 AZs for HA)
3. Create an Internet Gateway and attach to VPC
4. Launch EC2 in public subnet — SSH into it
5. Launch EC2 in private subnet — verify it can't be reached from internet
6. Add NAT Gateway — verify private EC2 can run `yum update`
7. Troubleshooting exercise: block port 80 via Security Group, observe the failure
**Document:** "Building a Secure AWS Network From Scratch (Like a Bank Would)"

---

### WEEK 18: Hybrid Connectivity

#### Days 83–87 — VPNs and Direct Connect

**Site-to-Site VPN (Your home lab → AWS):**
1. In AWS: Create a "Customer Gateway" (represents your home router)
2. Create a "Virtual Private Gateway" (the AWS VPN endpoint)
3. Create a "Site-to-Site VPN Connection"
4. Download the configuration file for your router type
5. Apply VPN config to your GNS3/home router
6. Test: ping an EC2 private IP from your local router

**Transit Gateway (Hub-and-Spoke):**
- Problem: 50 VPCs, each needing to talk to each other = 1,225 peering connections
- Solution: Transit Gateway = one hub. Every VPC connects to it. TGW routes between them.
- Supports: VPC peering + Direct Connect + VPN all through one TGW

**Assignment (Days 83–87):**
Configure a Site-to-Site VPN between your GNS3 lab and AWS. Ping an EC2 instance from your simulated on-prem network.
**Document:** "Connecting My Home Lab to AWS (For Free)" — very unique blog post

---

### WEEK 19: Load Balancing and DNS

#### Days 88–91 — AWS Load Balancers and Route 53

**Application Load Balancer (ALB) — Layer 7:**
- Routes based on URL path: `/api/*` → API servers, `/images/*` → image servers
- Health checks: if a server fails, ALB stops sending traffic to it
- SSL termination: HTTPS decryption happens at ALB, servers receive plain HTTP

**Network Load Balancer (NLB) — Layer 4:**
- Ultra-high performance, millions of requests per second
- Used for TCP/UDP workloads, gaming, VoIP

**Route 53 Routing Policies:**
- Simple: one record → one IP
- Weighted: 90% → Server A, 10% → Server B (for canary deployments)
- Latency-based: user in Mumbai → Mumbai server, user in US → US server
- Failover: primary server fails → automatically point to backup

**Assignment (Days 88–91):**
1. Deploy 2 EC2 instances running Nginx
2. Create an ALB pointing to both
3. Configure health checks
4. Stop one EC2 — verify ALB only routes to the healthy one
5. Register a free domain (https://freenom.com) and point it to ALB via Route 53
**Document:** "How Netflix Serves 200 Million Users (The Load Balancer Story)"

---

### WEEK 20: Phase 5 Capstone Project

**🏆 PHASE 5 CAPSTONE: Hybrid Cloud Network**

**Scenario:** Your company is "migrating to the cloud." You need:

1. AWS VPC: `10.0.0.0/16` with public and private subnets
2. On-prem network (GNS3): `192.168.0.0/16`
3. Site-to-Site VPN connecting them
4. Web server on AWS EC2 (public subnet) accessible via ALB
5. Database on AWS RDS (private subnet) — not internet accessible
6. The Python backup script from Phase 3 runs on a scheduled Lambda function:
   - Backs up your on-prem router configs
   - Stores them in AWS S3
7. Route 53 domain pointing to your ALB

**Tech Stack:**
- AWS: VPC, EC2, RDS, ALB, S3, Lambda, Route 53, VPN Gateway
- GNS3: On-prem simulation
- Python: Lambda function + Netmiko for config backup
- Terraform (Infrastructure as Code): https://terraform.io (free)
  - Define ALL your AWS resources in code
  - Version-controlled in Git
  - Reproducible with one command: `terraform apply`

**This is production-grade.** Terraform + AWS + on-prem VPN + automated backups is exactly what a $50M company would run.

---

## 🏗️ PHASE 6: Security and Monitoring (Weeks 21–24)
### "You Can't Manage What You Can't See"

---

### WEEK 21: Network Security Deep Dive

#### Days 93–97 — Firewalls, IPSec, and Zero Trust

**Next-Generation Firewall (NGFW) concepts:**
- **Stateful inspection:** Track TCP connections — only allow traffic that's part of an established session
- **Application identification (App-ID):** Identify applications by behavior, not just port number. Facebook Chat on port 443 ≠ BitTorrent on port 443
- **User-ID:** Policies based on Active Directory username, not IP address
- **SSL inspection:** Decrypt HTTPS traffic, inspect it, re-encrypt. This is how corporate firewalls see inside encrypted traffic (controversial but standard in enterprises).

**IPSec VPN mechanics:**
- **Phase 1 (IKE — Internet Key Exchange):** Negotiate the secure tunnel parameters (encryption algorithm, hash, DH group, pre-shared key or certificates). Creates the ISAKMP SA.
- **Phase 2 (IPSec SA):** Negotiate the data encryption parameters. Creates the tunnel for actual traffic.
- **Common failures:**
  - Mismatched pre-shared key → Phase 1 fails
  - Mismatched encryption algorithm → Phase 1 fails
  - Mismatched proxy ACLs (what traffic should go through tunnel) → Phase 2 partial

**pfSense (Free, Open-Source Firewall):**
- Install as a VM: https://www.pfsense.org
- Replace your GNS3 router with pfSense for Phase 6 labs
- Provides: NGFW, IPSec VPN, traffic graphs, IDS/IPS (via Snort/Suricata packages)

**Assignment (Days 93–97):**
1. Install pfSense VM
2. Configure pfSense as your lab's internet gateway
3. Enable Snort IDS package
4. Generate some "attack traffic" using tools available in Kali Linux
5. Observe alerts in Snort
**Document:** "I Turned My Home Lab Into a Cybersecurity Lab (For Free)"

---

### WEEK 22: Quality of Service (QoS)

#### Days 98–101 — Traffic Prioritization

**What it is:**  
When bandwidth is limited (e.g., a 100Mbps WAN link), QoS decides which traffic gets priority. VoIP calls get first-class, bulk file transfers get economy class.

**DSCP (Differentiated Services Code Point):**
- A 6-bit field in the IP header that marks traffic priority
- EF (Expedited Forwarding) = 46 = highest priority (VoIP, real-time)
- AF (Assured Forwarding) = different levels of assured bandwidth
- BE (Best Effort) = 0 = default, no guarantees

**The QoS Pipeline:**
1. **Classification:** Identify the traffic (port 5060 = SIP/VoIP)
2. **Marking:** Set the DSCP value in the IP header
3. **Queuing:** Put traffic in the right queue (priority queue for VoIP)
4. **Scheduling:** Service queues in priority order

**Assignment (Days 98–101):**
Configure QoS in GNS3:
- Mark VoIP traffic (UDP 5060, 5004-5082) as EF
- Mark web traffic as AF31
- Simulate congestion and verify VoIP takes priority
**Document:** "Why Your Zoom Call Sounds Bad (And How Companies Fix It)"

---

### WEEKS 23–24: Monitoring Stack (ELK)

#### Days 102–112 — Building Your Monitoring Platform

**The ELK Stack (100% Free, Open Source):**
- **Elasticsearch:** Stores and indexes logs (database for logs)
- **Logstash:** Collects, parses, and transforms logs before storing
- **Kibana:** Web dashboard for visualizing logs

**Install on a Linux VM:**
```bash
# Install Elasticsearch
wget -qO - https://artifacts.elastic.co/GPG-KEY-elasticsearch | sudo gpg --dearmor -o /usr/share/keyrings/elasticsearch-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/elasticsearch-keyring.gpg] https://artifacts.elastic.co/packages/8.x/apt stable main" | sudo tee /etc/apt/sources.list.d/elastic-8.x.list
sudo apt update && sudo apt install elasticsearch kibana logstash

# Start services
sudo systemctl start elasticsearch kibana logstash
```

**Syslog collection:**
- Configure your GNS3 routers to send syslog to your ELK server
- Logstash receives the syslog, parses it, sends to Elasticsearch
- Kibana shows dashboards: interface errors, BGP drops, authentication failures

**Useful Kibana dashboards to build:**
1. Interface error rate over time (detect failing hardware)
2. BGP neighbor state changes (detect routing instability)
3. Failed SSH login attempts (detect brute force attacks)
4. Top talkers (which devices generating most traffic)

**Assignment (Days 102–112):**
1. Deploy ELK stack on Ubuntu VM
2. Configure all lab routers to send syslog
3. Create a Kibana dashboard showing router health
4. Simulate a failure (shut down OSPF) — observe the alerts in Kibana
5. Set up an email alert: if "OSPF neighbor down" appears in logs, send email
**Document:** "Building a Free Network Monitoring Platform" — this is a complete portfolio project

---

## 🏗️ PHASE 7: AI Integration and AIOps (Weeks 25–30)
### "The Future of Network Operations"

---

### WEEK 25–27: Machine Learning for Network Operations

#### The Self-Healing Network Project

**What AIOps is:**  
Instead of setting static thresholds ("alert if CPU > 90%"), AI learns the normal "heartbeat" of your network and alerts on anomalies. On Friday afternoons, high traffic is normal. At 3 AM Tuesday, unusual traffic is suspicious.

**Tools (all free, open source):**
- **Ollama:** Run LLMs locally (no OpenAI cost): https://ollama.ai
- **Scikit-learn:** Machine learning library for Python
- **Pandas:** Data analysis
- **Grafana:** Beautiful dashboards (alternative to Kibana)

**Anomaly Detection:**
```python
import pandas as pd
from sklearn.ensemble import IsolationForest
import numpy as np

# Load your collected metrics (from SNMP or ELK)
df = pd.read_csv("interface_errors_last_30days.csv")

# Train anomaly detection model
model = IsolationForest(contamination=0.05)  # 5% of data is anomalous
model.fit(df[['error_rate', 'input_bps', 'output_bps']])

# Predict anomalies in new data
new_data = df.tail(100)
anomalies = model.predict(new_data[['error_rate', 'input_bps', 'output_bps']])
# -1 = anomaly, 1 = normal

alert_rows = new_data[anomalies == -1]
print("Anomalies detected:")
print(alert_rows)
```

**LLM-Powered Root Cause Analysis:**
```python
import ollama
import json

# Get recent syslog from ELK
syslog_entries = [
    "OSPF neighbor 10.0.0.2 is down",
    "Interface GigabitEthernet0/1 is down",
    "BGP peer 203.0.113.1 lost",
    "CPU utilization is 95%"
]

prompt = f"""
You are a network engineer. Analyze these syslog entries and identify:
1. The root cause
2. The impact
3. The recommended fix

Syslog entries:
{json.dumps(syslog_entries, indent=2)}

Respond in plain English.
"""

response = ollama.chat(
    model='llama3',
    messages=[{'role': 'user', 'content': prompt}]
)
print(response['message']['content'])
```

**Assignment (Weeks 25–27):**
Build the "Self-Healing Network Monitor":
1. Collect interface error counters every minute from all routers (Python + Netmiko)
2. Store data in CSV (later upgrade to InfluxDB)
3. Train Isolation Forest on 7 days of baseline data
4. Run anomaly detection every 5 minutes
5. When anomaly detected: have Ollama LLM analyze recent syslog and generate plain-English RCA
6. Automatically: shut down failing interface and route traffic to backup path
**Document:** "I Built an AI That Fixes My Network (So I Can Sleep)" — this is viral-worthy content

---

### WEEKS 28–30: The Final Capstone

**🏆 FINAL CAPSTONE PROJECT: NetOps360**

This is the complete, MNC-grade system you've been building toward. It integrates everything.

**Architecture:**
```
┌─────────────────────────────────────────────────────────┐
│                    NetOps360 Platform                    │
│                                                          │
│  [GitHub Repo] ─── GitOps Pipeline ─── [Containerlab]   │
│       ↓                                       ↓          │
│  Config Store      Digital Twin Test     Production Lab  │
│                                                          │
│  [Python Scripts] ─── [Ansible] ─── [Netmiko]           │
│       ↓                                                  │
│  Compliance Auditor + Config Backup + Health Monitor     │
│                                                          │
│  [ELK Stack] ─── [Grafana] ─── [Ollama LLM]             │
│       ↓               ↓              ↓                   │
│  Log Storage    Dashboards    AI Root Cause Analysis     │
│                                                          │
│  [AWS VPC] ─── [Site-to-Site VPN] ─── [On-Prem Lab]    │
│       ↓                                                  │
│  Lambda: Scheduled Config Backups to S3                  │
└─────────────────────────────────────────────────────────┘
```

**Complete Tech Stack (All Free):**

| Component | Technology | Why This Choice |
|---|---|---|
| Network Simulation | GNS3 + Containerlab | Industry standard tools |
| Config Automation | Ansible + Netmiko | Used at Cisco, Juniper, Google |
| CI/CD Pipeline | GitHub Actions | Free, industry standard |
| Config Storage | GitHub (Git) | Version control for configs (GitOps) |
| Cloud Network | AWS Free Tier | Real cloud experience |
| IaC | Terraform | Industry standard for cloud infra |
| Log Management | ELK Stack | Used at Netflix, Uber |
| Dashboards | Grafana | Open source, professional-grade |
| Anomaly Detection | Python + Scikit-learn | ML without cloud cost |
| AI RCA | Ollama + Llama 3 (local) | No API cost |
| Documentation | GitHub Pages + Hashnode | Your public portfolio |

**Final Deliverables:**
1. Complete GitHub repository with all code
2. Architecture documentation (draw.io diagrams)
3. 30+ technical blog posts (one per week minimum)
4. Demonstration video (record with OBS — free): show the automated compliance check, config backup, and AI anomaly detection working
5. LinkedIn post series documenting your 30-week journey

---

## 📊 REAL-WORLD MNC PROBLEMS AND SOLUTIONS

These are documented cases you should reference in interviews and blog posts:

| Company | Problem | Solution | What You Learn From It |
|---|---|---|---|
| **Google (B4)** | WAN links only 30-40% utilized | SDN centralized TE controller — near 100% utilization | Always separate control plane from data plane at scale |
| **Facebook (2021 Outage)** | BGP withdrew DNS prefixes → entire internet lost Facebook → engineers locked out because VPN relied on DNS | Out-of-Band management that doesn't depend on production network | Never let management access depend on what you're managing |
| **Netflix** | Streaming from central datacenter → too slow → ISP congestion | Built Open Connect CDN — ISPs host Netflix boxes in local networks | Move data closer to users, not users closer to data |
| **AWS (2020 outage)** | Internal DNS service failed → everything depending on DNS cascaded | Circular dependency design error | Map dependencies before you deploy — avoid circular chains |

---

## 📅 30-WEEK DAILY SCHEDULE SUMMARY

| Week | Phase | Focus | Capstone/Project |
|---|---|---|---|
| 1 | P1 | OSI, TCP/IP, Physical Layer | Wireshark captures |
| 2 | P1 | VLANs, STP, Switching | Campus network lab |
| 3 | P1 | Subnetting, IPv6, DHCP/DNS | Subnet design exercise |
| 4 | P1 | Static routing, HSRP | **PROJECT 1: Campus Network** |
| 5 | P2 | OSPF fundamentals | Multi-area OSPF lab |
| 6 | P2 | EIGRP | OSPF vs EIGRP comparison |
| 7 | P2 | BGP fundamentals and attributes | Dual-ISP BGP lab |
| 8 | P2 | EtherChannel, security features | ARP poisoning + DAI lab |
| 9 | P2 | MPLS and VRFs | Mini-ISP build |
| 10 | P2 | Break-Fix challenge | **PROJECT 2: Service Provider Sim** |
| 11 | P3 | Python basics, Netmiko | Router backup script |
| 12 | P3 | Ansible, Jinja2 | Config management playbook |
| 13 | P3 | REST APIs, requests library | **PROJECT 3: Compliance Auditor** |
| 14 | P4 | SDN, Mininet, OpenFlow | SDN controller lab |
| 15 | P4 | ACI, DNA Center APIs | Postman API exploration |
| 16 | P4 | VXLAN, EVPN, Spine-Leaf | **PROJECT 4: Spine-Leaf Fabric** |
| 17 | P5 | AWS VPC, subnets, routing | AWS Free Tier lab |
| 18 | P5 | Hybrid VPN, Transit Gateway | Site-to-Site VPN |
| 19 | P5 | Load Balancing, Route 53 | ALB + health checks |
| 20 | P5 | Terraform IaC | **PROJECT 5: Hybrid Cloud Network** |
| 21 | P6 | pfSense, IPSec, SSL inspection | Firewall lab |
| 22 | P6 | QoS, DSCP, traffic shaping | VoIP prioritization lab |
| 23 | P6 | ELK setup, syslog collection | Monitoring stack |
| 24 | P6 | Kibana dashboards, alerting | **PROJECT 6: Monitoring Platform** |
| 25–27 | P7 | ML anomaly detection, Ollama LLM | AI anomaly detector |
| 28–30 | P7 | Integration + documentation | **PROJECT 7: NetOps360 Final** |

---

## 🔗 COMPLETE RESOURCE LIST (All Free)

### Software and Tools
- **GNS3:** https://gns3.com
- **Cisco Packet Tracer:** https://netacad.com
- **Containerlab:** https://containerlab.dev
- **Wireshark:** https://wireshark.org
- **pfSense:** https://pfsense.org
- **Python:** https://python.org
- **Ansible:** https://ansible.com
- **Terraform:** https://terraform.io
- **Ollama (local LLM):** https://ollama.ai
- **ELK Stack:** https://elastic.co (free tier)
- **Grafana:** https://grafana.com (free)
- **Mininet:** http://mininet.org

### Learning Resources
- **Cisco DevNet:** https://developer.cisco.com (free labs, sandboxes)
- **GNS3 Vault (free labs):** https://gns3vault.com
- **Professor Messer (CompTIA Network+ free):** https://professormesser.com
- **Jeremy's IT Lab (CCNA free):** https://youtube.com/@JeremysITLab
- **AWS Free Training:** https://aws.training
- **Terraform tutorials:** https://learn.hashicorp.com

### Documentation Platforms
- **GitHub:** https://github.com — ALL code goes here
- **Hashnode:** https://hashnode.com — Technical blogging
- **Dev.to:** https://dev.to — Alternative blogging
- **Draw.io:** https://draw.io — Network diagrams (free)

---

## 🎯 INTERVIEW PREPARATION MILESTONES

By the end of this roadmap, you will have:

✅ **200+ published technical articles** (Hashnode/Dev.to)  
✅ **7 completed projects** (all on GitHub with documentation)  
✅ **1 complete production-grade platform** (NetOps360)  
✅ **Real AWS experience** (hybrid network, Lambda, VPC)  
✅ **AI integration experience** (anomaly detection, LLM RCA)  
✅ **GitOps experience** (CI/CD for network configs)  
✅ **End-to-end troubleshooting methodology** (break-fix labs)  
✅ **Documented case studies** from Google, Netflix, Facebook, AWS

When an interviewer asks "Have you ever automated network configurations?" — you show them your GitHub.  
When they ask "How do you troubleshoot OSPF?" — you show them your published RCA report.  
When they ask "Do you understand cloud networking?" — you show them your AWS hybrid cloud architecture.

**The documentation IS the proof. Build it every day.**

---

*Last updated: May 2026 | Generated based on MNC-standard network engineering curriculum*