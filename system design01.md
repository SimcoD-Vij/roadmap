# 📅 Day-by-Day System Design Timetable
### Zero to MNC Production-Grade Engineer — 210 Days

> **Daily Structure (4–6 hours/day)**
> - 🌅 **Morning Block** (1.5 hrs): Study + Notes
> - 🛠️ **Afternoon Block** (2 hrs): Hands-on Build
> - 📝 **Evening Block** (1 hr): Document + Commit + Recall
>
> **Legend**: 📖 Study | 🛠️ Build | 📝 Document | 🔁 Recall | ✅ Checkpoint

---

---

# 🟣 PHASE 0: Mental Models & Foundations (Days 1–14)

---

## 📅 DAY 1 — How Computers Actually Work

### 🌅 Morning Block (1.5 hrs)
- 📖 Read: Von Neumann Architecture — CPU, Memory, Storage, I/O Bus
- 📖 Study: What happens when you press the power button (POST, BIOS/UEFI, bootloader, OS)
- 📖 Learn: Binary and hexadecimal — why machines use base-2
- 📖 Understand: Bits → Bytes → KB → MB → GB → TB (not just sizes — what each holds)
- 📖 Watch: "How CPU works" — YouTube (Crash Course Computer Science Ep 7–8)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Draw by hand: A diagram of a computer — CPU, RAM, Disk, GPU, NIC, connected by a bus
- 🛠️ Create a markdown file: `latency-cheat-sheet.md`
  - Fill in: L1 cache (~1ns), L2 (~5ns), L3 (~30ns), RAM (~100ns), SSD (~100µs), HDD (~10ms), Network (~150ms)
  - Add real-world analogies: "L1 cache = reaching into your pocket. HDD = flying to another city to retrieve a document."
- 🛠️ Create GitHub account if not done. Set up SSH key for authentication.
- 🛠️ Create repository: `learning-journal`

### 📝 Evening Block (1 hr)
- 📝 Push your first commit: `docs: add day 1 — computer architecture diagram and latency cheat sheet`
- 📝 Write in journal: What surprised you? What didn't make sense?
- 🔁 Recall: Close notes. Answer: "What is the difference between RAM and an SSD? Why does it matter for software?"

---

## 📅 DAY 2 — CPU Deep Dive & Memory Hierarchy

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: CPU fetch-decode-execute cycle in detail
- 📖 Study: CPU cache — L1/L2/L3, cache hits vs cache misses, why cache exists
- 📖 Study: Clock speed vs core count — why 4 cores at 3GHz ≠ always faster than 2 cores at 4GHz
- 📖 Study: Hyper-threading — what it is and what it actually does
- 📖 Study: Moore's Law — what it predicted, why it's slowing, what engineers do instead (more cores, better cache, specialized chips like GPUs/TPUs)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Open terminal (Linux or WSL on Windows): Run `lscpu` — understand every field
- 🛠️ Run `cat /proc/cpuinfo` — read what your actual CPU exposes to the OS
- 🛠️ Run `free -h` — understand memory available vs used vs cached
- 🛠️ Write a Python script that:
  - Creates a list of 1 million numbers
  - Times how long it takes to sum them (measures RAM access speed)
  - Compare with a pre-computed result (simulates cache hit)
- 🛠️ Add output to `learning-journal` with explanation

### 📝 Evening Block (1 hr)
- 📝 Commit: `docs: day 2 — CPU internals, lscpu output, memory benchmark`
- 📝 Update latency cheat sheet with one more column: "Software implication"
- 🔁 Recall: "Why does a web server care about cache hit rate? Give a specific example."

---

## 📅 DAY 3 — Linux: The Engineer's Operating System

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: What an operating system does — process management, memory management, file system, device management
- 📖 Study: Linux filesystem hierarchy — what lives where and WHY
  - `/` (root), `/etc` (config files), `/var` (variable data — logs), `/proc` (virtual FS for process info), `/home` (user directories), `/usr/bin` (user programs), `/tmp` (temporary files)
- 📖 Read: First 3 chapters of "The Linux Command Line" (free online at linuxcommand.org)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Practice these commands until comfortable — do NOT just read, type every one:
  - Navigation: `pwd`, `ls -la`, `cd`, `tree`
  - File ops: `touch`, `mkdir`, `cp`, `mv`, `rm -rf` (careful!), `cat`, `less`, `head`, `tail`
  - Search: `grep -r "pattern" .`, `find / -name "filename"`, `locate`
  - Text: `echo`, `wc -l`, `sort`, `uniq`, `cut`, `awk`
- 🛠️ Create a markdown "Linux Command Reference" in your learning-journal
- 🛠️ Explore: `cat /proc/meminfo`, `cat /proc/cpuinfo`, `df -h`, `lsblk`

### 📝 Evening Block (1 hr)
- 📝 Commit: `docs: day 3 — linux filesystem hierarchy, command reference`
- 🔁 Recall: "What is the difference between `/etc` and `/var`? What would you store in each?"
- 🔁 Recall: "What does `grep -r "error" /var/log` do?"

---

## 📅 DAY 4 — Linux: Processes, Users, Permissions

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Processes — what they are, how they're created (fork/exec model), PID, PPID
- 📖 Study: Process states: Running, Sleeping, Stopped, Zombie
- 📖 Study: Users and groups in Linux — UID/GID, root user, sudo
- 📖 Study: File permissions — rwx for owner/group/others, numeric representation (755 = rwxr-xr-x)
- 📖 Study: `chmod`, `chown`, `chgrp`, `umask`

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Run `ps aux` — identify every column. Find the PID of your terminal.
- 🛠️ Run `top` then `htop` (install with `apt install htop`) — understand CPU%, MEM%, TIME+
- 🛠️ Practice: `kill -9 PID`, `kill -15 PID` — what's the difference?
- 🛠️ Create a user: `sudo useradd -m testuser`, set password, switch to them with `su testuser`
- 🛠️ Create files with different permissions and verify with `ls -la`
- 🛠️ Practice: make a script executable with `chmod +x script.sh`
- 🛠️ Write your first shell script: `hello.sh` that prints your name and today's date

### 📝 Evening Block (1 hr)
- 📝 Commit: `docs: day 4 — linux processes, permissions, first shell script`
- 🔁 Recall: "What does `chmod 644 file.txt` mean? Who can read? Who can write?"
- 🔁 Recall: "What is a zombie process? When does it occur?"

---

## 📅 DAY 5 — Linux: Shell Scripting Fundamentals

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Shell script syntax — shebang (`#!/bin/bash`), variables, `$()` command substitution
- 📖 Study: Control flow — `if/elif/else`, `for`, `while`, `case`
- 📖 Study: Functions in bash
- 📖 Study: Exit codes — `$?`, `exit 0` (success), `exit 1` (failure)
- 📖 Study: Pipes (`|`) and redirection (`>`, `>>`, `<`, `2>`, `2>&1`)
- 📖 Study: Cron jobs — scheduling scripts to run automatically

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Build Script 1: `system-info.sh`
  - Prints: hostname, OS version, CPU model, total RAM, disk usage, uptime
  - Each piece labeled clearly in the output
- 🛠️ Build Script 2: `monitor.sh`
  - Checks CPU usage (extract from `top` output)
  - Checks disk usage (from `df`)
  - Checks RAM free (from `free`)
  - If any metric is above threshold (e.g., disk > 80%), print a WARNING message
  - Run it with `while true; do ./monitor.sh; sleep 60; done`
- 🛠️ Add a cron job: `crontab -e` → run monitor.sh every 5 minutes, redirect output to `/var/log/my-monitor.log`

### 📝 Evening Block (1 hr)
- 📝 Commit both scripts with detailed comments in the code
- 📝 Write README for your scripts folder
- 🔁 Recall: "Explain pipes in Linux with an example. What does `cat /var/log/syslog | grep error | tail -20` do?"

---

## 📅 DAY 6 — Git: Version Control as Engineering Discipline

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Why version control exists — the problem it solves (history, collaboration, rollback)
- 📖 Study: Git internals — blobs, trees, commits, refs, the `.git` directory
- 📖 Study: Core commands in depth: `init`, `clone`, `add`, `status`, `commit`, `log`, `diff`
- 📖 Study: Remote operations: `push`, `pull`, `fetch`, `remote`
- 📖 Study: Conventional commits standard: `feat:`, `fix:`, `docs:`, `refactor:`, `chore:`, `test:`
- 📖 Read: Pro Git Book — Chapters 1–3 (free at git-scm.com)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Initialize a new local repo and practice full workflow: init → add → commit → push
- 🛠️ Practice `git log --oneline --graph --all` — understand commit history visually
- 🛠️ Create a GitHub Profile README repository (`username/username`)
  - Write: who you are, what you're learning, what you're building
  - Add progress badges if you like
- 🛠️ Organize your `learning-journal` with folders: `phase-0/`, `phase-1/`, etc.
- 🛠️ Practice `git diff` to see what changed before committing

### 📝 Evening Block (1 hr)
- 📝 Commit with proper conventional commit message
- 🔁 Recall: "What is the difference between `git fetch` and `git pull`?"
- 🔁 Recall: "What does `git add -p` do and why is it useful?"

---

## 📅 DAY 7 — Git: Branching, Merging, and Collaboration

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Branches — what they are internally (just a pointer to a commit), why they're cheap in Git
- 📖 Study: `git branch`, `git checkout -b`, `git switch -c`
- 📖 Study: Merging — fast-forward vs 3-way merge
- 📖 Study: Rebasing — what it does, when to use it, why it rewrites history
- 📖 Study: Pull Requests — the collaboration workflow (branch → PR → review → merge)
- 📖 Study: `.gitignore` — what to ignore and why (node_modules, __pycache__, .env, secrets)
- 📖 Study: Git stash — save work-in-progress

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Create a feature branch, make changes, merge back to main (practice both merge and rebase)
- 🛠️ Deliberately create a merge conflict:
  - Create two branches that both modify the same line
  - Merge them and resolve the conflict manually
  - Document how you resolved it
- 🛠️ Set up a proper `.gitignore` for a Python project
- 🛠️ Practice: `git stash`, `git stash pop`, `git stash list`
- 🛠️ On GitHub: Create a PR from a branch, write a description, merge it

### 📝 Evening Block (1 hr)
- 📝 Commit: `docs: day 7 — git branching, merge conflict resolution documented`
- 📝 Write a short document: "My Git workflow" — the process you'll follow for every project
- 🔁 Recall: "When would you rebase instead of merge? What's the danger of rebasing?"

---

## 📅 DAY 8 — Git Advanced + GitHub Ecosystem

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Git tags — annotated vs lightweight, semantic versioning (MAJOR.MINOR.PATCH)
- 📖 Study: Git hooks — pre-commit, pre-push hooks (run linting before commit)
- 📖 Study: GitHub features: Issues, Projects (kanban), Releases, GitHub Pages
- 📖 Study: Git branching strategies: Git Flow vs Trunk-Based Development — tradeoffs
- 📖 Study: How open-source contribution works (fork → clone → branch → PR to upstream)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Set up GitHub Pages for your `learning-journal` repo — enable it in Settings
- 🛠️ Create a `CHANGELOG.md` in your learning-journal repo and start tracking what you build
- 🛠️ Create a pre-commit hook that checks for debug print statements before committing
- 🛠️ Tag your current commit as `v0.1.0` — your first "release" of your learning journal
- 🛠️ Create a GitHub Issue for your next project ("Build system monitor script") and close it with a commit reference

### 📝 Evening Block (1 hr)
- 📝 Commit everything. Your commit graph should now have 8 days of commits.
- 🔁 Recall: "What is semantic versioning? When do you bump MAJOR vs MINOR vs PATCH?"

---

## 📅 DAY 9 — Linux Networking Basics + SSH

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Network interfaces in Linux — `eth0`, `lo` (loopback), `wlan0`
- 📖 Study: IP addresses — what they are, static vs dynamic (DHCP)
- 📖 Study: `ifconfig` / `ip addr show` — reading your network config
- 📖 Study: SSH — how it works (asymmetric encryption, key exchange, session keys)
- 📖 Study: SSH key pairs — public key (server keeps), private key (you keep)
- 📖 Study: `~/.ssh/config` — configuring SSH aliases for multiple servers

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Generate an SSH key pair: `ssh-keygen -t ed25519 -C "your@email.com"`
- 🛠️ Add public key to GitHub (already done) — verify with `ssh -T git@github.com`
- 🛠️ Install VirtualBox (free) and create an Ubuntu Server VM (no GUI)
- 🛠️ SSH into your VM from your host machine using key-based auth
- 🛠️ Configure `~/.ssh/config` with an alias for your VM
- 🛠️ Practice: `scp` to copy files between host and VM, `rsync` for efficient sync

### 📝 Evening Block (1 hr)
- 📝 Document your VM setup: IP address, how SSH was configured, your `~/.ssh/config`
- 🔁 Recall: "What is the difference between symmetric and asymmetric encryption in the context of SSH?"

---

## 📅 DAY 10 — Linux: Text Processing & Log Analysis

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: `grep` — regular expressions basics, `-i` (case insensitive), `-r` (recursive), `-v` (invert), `-E` (extended regex)
- 📖 Study: `awk` — field processing (`awk '{print $1, $3}'`), filtering (`awk '$2 > 100'`)
- 📖 Study: `sed` — stream editor, substitution (`sed 's/old/new/g'`)
- 📖 Study: `sort`, `uniq`, `wc`, `cut`, `tr`, `head`, `tail`
- 📖 Study: Log files — `/var/log/syslog`, `/var/log/auth.log`, `journalctl`

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Generate a fake log file (write a script that generates 1000 lines of fake web server logs in Apache Combined Log Format)
- 🛠️ Use grep/awk/sed to answer:
  - "How many 404 errors occurred?"
  - "What are the top 10 most-visited URLs?"
  - "Which IP addresses made more than 50 requests?"
  - "What's the total bytes transferred?"
- 🛠️ Write a script `analyze-logs.sh` that runs all these queries and outputs a summary report

### 📝 Evening Block (1 hr)
- 📝 Commit: the log file, analysis script, and sample output
- 📝 Write documentation: "How to analyze web server logs with Linux tools"
- 🔁 Recall: "Write a command that counts the unique IP addresses in a web server log file"

---

## 📅 DAY 11 — Linux: Package Management & System Administration

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Package managers — `apt` (Debian/Ubuntu), how packages, repos, and dependencies work
- 📖 Study: `systemd` — the init system, services, units
- 📖 Study: `systemctl` — start/stop/enable/disable/status services
- 📖 Study: `journalctl` — reading systemd logs
- 📖 Study: Cron vs systemd timers — scheduled tasks
- 📖 Study: `/etc/hosts` — local DNS override, how it's used

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Create a systemd service file for your `monitor.sh` script (runs it as a background service)
- 🛠️ Start, stop, restart the service. Check its logs with `journalctl -u your-service -f`
- 🛠️ Install common tools: `curl`, `wget`, `htop`, `net-tools`, `dnsutils`, `nmap`, `tmux`
- 🛠️ Practice `tmux`: create sessions, windows, panes — essential for long-running remote work
- 🛠️ Set up automatic security updates: `apt install unattended-upgrades`

### 📝 Evening Block (1 hr)
- 📝 Commit: your systemd service file with comments, monitoring script
- 🔁 Recall: "What is the difference between `systemctl enable` and `systemctl start`?"

---

## 📅 DAY 12 — Environment Variables, Config Management & Security Basics

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Environment variables — `$PATH`, `$HOME`, `export`, `.bashrc` vs `.bash_profile` vs `.profile`
- 📖 Study: Why secrets must NEVER be in code — API keys, passwords, DB credentials
- 📖 Study: `.env` files — pattern for storing secrets locally
- 📖 Study: Secret rotation — why and how
- 📖 Study: SSH config hardening — disable root login, password auth, change default port
- 📖 Study: `ufw` (Uncomplicated Firewall) — allow/deny ports

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Harden your VM's SSH config: disable password login, disable root login, enable key-only auth
- 🛠️ Set up `ufw`: allow SSH (22), deny everything else. Test it works.
- 🛠️ Create a `.env.example` file (with placeholder values) — this is what you commit to Git
- 🛠️ Create a `.env` file (with real values) — add to `.gitignore` immediately
- 🛠️ Write a Python script that reads from `.env` using `python-dotenv` library
- 🛠️ Verify your Git history has NEVER had a real secret committed (it shouldn't)

### 📝 Evening Block (1 hr)
- 📝 Commit: hardened SSH config notes, `.env.example`, Python dotenv script
- 🔁 Recall: "Why should you never commit secrets to Git? What do you do if you accidentally commit one?"

---

## 📅 DAY 13 — Python Fundamentals for Engineering

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Python as an engineering tool — not a beginner tutorial, but how engineers use it
- 📖 Study: Data structures and their time complexity: list O(n), dict O(1), set O(1)
- 📖 Study: List comprehensions, generator expressions, `map`/`filter`
- 📖 Study: Error handling — `try/except/finally`, custom exceptions, logging vs printing
- 📖 Study: `logging` module — why `print()` is wrong in production, log levels (DEBUG/INFO/WARNING/ERROR/CRITICAL)
- 📖 Study: Virtual environments — `venv`, `pip`, `requirements.txt`

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Set up a Python project with venv properly
- 🛠️ Rewrite your `monitor.sh` logic as a Python script `monitor.py` using:
  - `psutil` library (system metrics)
  - `logging` module (not print statements)
  - Proper error handling
  - `.env` for configuration (threshold values)
- 🛠️ Add a `requirements.txt` and document how to install and run

### 📝 Evening Block (1 hr)
- 📝 Commit: Python monitor script, requirements.txt, README with setup instructions
- 🔁 Recall: "What is the time complexity of looking up a key in a Python dictionary? Why?"

---

## 📅 DAY 14 — Phase 0 Review, Portfolio Setup & Checkpoint

### 🌅 Morning Block (1.5 hrs)
- 📖 Review all notes from Days 1–13
- 📖 Attempt to answer ALL active recall questions from previous days without notes
- 📖 Identify what's still unclear — mark it for revisiting
- 📖 Read: "What makes a good GitHub profile?" — research top engineering portfolios

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Polish your GitHub Profile README:
  - Add a "Currently Learning" section
  - Link to your learning-journal repo
  - Add technology badges (shields.io — free)
- 🛠️ Make sure every repo has a proper README with: description, how to run, what you learned
- 🛠️ Complete the Phase 0 checklist:
  - [ ] GitHub account + profile README ✅
  - [ ] `learning-journal` with 14 consecutive commits ✅
  - [ ] Latency cheat sheet with analogies ✅
  - [ ] System monitor script (bash + Python versions) ✅
  - [ ] Merge conflict created and resolved ✅
  - [ ] VM set up and SSH key configured ✅
  - [ ] Log analysis script with sample output ✅
  - [ ] Systemd service running ✅

### 📝 Evening Block (1 hr)
- 📝 Write your Phase 0 retrospective in `learning-journal`:
  - "What I built"
  - "What was harder than expected"
  - "What I would revisit"
- 📝 Tag: `v0.2.0` — Phase 0 complete
- 🔁 Final Recall: "Explain to someone who knows nothing: What is a process? What is a thread? What is a file descriptor?"

---

---

# 🟢 PHASE 1: Computer Networks & Data Flow (Days 15–35)

---

## 📅 DAY 15 — OSI Model: The Framework for Everything

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: OSI 7-layer model — not as a memorization exercise but as a *mental model*
- 📖 For each layer, learn: what problem it solves, what protocols operate here, what can fail here
- 📖 Study: TCP/IP model (4 layers) vs OSI model — how they relate
- 📖 Study: Protocol Data Units (PDU) — bits → frames → packets → segments → data

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Install Wireshark (free): capture your first packets on your network interface
- 🛠️ Open a browser, go to http://example.com, stop capture. Find and label packets at each OSI layer:
  - Layer 2: Ethernet frame (MAC addresses)
  - Layer 3: IP packet (source/destination IPs)
  - Layer 4: TCP segment (ports, SYN/ACK)
  - Layer 7: HTTP request
- 🛠️ Take annotated screenshots of each packet type

### 📝 Evening Block (1 hr)
- 📝 Create `networking-lab` repo on GitHub
- 📝 Commit: OSI model reference table, annotated Wireshark screenshots
- 🔁 Recall: "What layer does a router operate at? What layer does a switch operate at? Why?"

---

## 📅 DAY 16 — IP Addressing, Subnetting & Routing

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: IPv4 addressing — 32-bit address, dotted decimal notation
- 📖 Study: Network classes (A, B, C) — historical context and why CIDR replaced them
- 📖 Study: CIDR notation — `/24` means 24 bits for network, 8 bits for hosts (256 addresses)
- 📖 Study: Private IP ranges: 10.0.0.0/8, 172.16.0.0/12, 192.168.0.0/16
- 📖 Study: NAT (Network Address Translation) — how your router maps private to public IPs
- 📖 Study: Default gateway, routing tables — `ip route show` on Linux
- 📖 Study: IPv6 basics — 128-bit, why it was necessary

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Practice subnetting: given `192.168.1.0/24`, calculate: network address, broadcast address, first host, last host, number of hosts
- 🛠️ Do 10 subnetting exercises (ipcalc.es — free online tool to verify your answers)
- 🛠️ Run on your VM: `ip addr show`, `ip route show`, `ip neigh show` (ARP table)
- 🛠️ Ping your VM from host. Capture in Wireshark. Identify the ICMP packets.
- 🛠️ Draw your home network topology: router, your machine, VM, IP addresses of each

### 📝 Evening Block (1 hr)
- 📝 Commit: network topology diagram, subnetting exercise answers, command output
- 🔁 Recall: "What is NAT and why does it exist? What is the problem it creates for peer-to-peer connections?"

---

## 📅 DAY 17 — TCP vs UDP: The Transport Layer

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: TCP in depth — three-way handshake (SYN/SYN-ACK/ACK), four-way teardown
- 📖 Study: TCP features: reliable delivery (ACKs + retransmission), flow control (receive window), congestion control (slow start, AIMD)
- 📖 Study: TCP sequence numbers — how out-of-order packets are reordered
- 📖 Study: UDP — connectionless, no guarantee, why it's used (DNS, video streaming, gaming, VoIP)
- 📖 Study: TCP head-of-line blocking — why HTTP/3 switched to QUIC (UDP-based)
- 📖 Study: Common ports: 22 (SSH), 25 (SMTP), 53 (DNS), 80 (HTTP), 443 (HTTPS), 3306 (MySQL), 5432 (PostgreSQL), 6379 (Redis)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Wireshark capture: Open a TCP connection with `curl -v http://example.com`
  - Find the three-way handshake (SYN, SYN-ACK, ACK)
  - Find the HTTP GET request
  - Find the four-way teardown (FIN, FIN-ACK)
  - Annotate each packet with what it represents
- 🛠️ Write a simple Python TCP server (socket programming) and client — send "Hello" and receive it
- 🛠️ Write the same for UDP — note you don't need to accept connections

### 📝 Evening Block (1 hr)
- 📝 Commit: Wireshark screenshots annotated, Python TCP and UDP socket code
- 🔁 Recall: "If a packet is lost in TCP, what happens? In UDP, what happens? Why does this difference matter for video streaming?"

---

## 📅 DAY 18 — DNS: The Internet's Phone Book

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: DNS resolution flow — stub resolver → recursive resolver → root nameserver → TLD nameserver → authoritative nameserver
- 📖 Study: DNS record types:
  - `A` — domain → IPv4 address
  - `AAAA` — domain → IPv6 address
  - `CNAME` — domain alias
  - `MX` — mail server
  - `TXT` — arbitrary text (SPF, DKIM, verification)
  - `NS` — nameserver delegation
  - `PTR` — reverse DNS (IP → domain)
- 📖 Study: TTL (Time to Live) — caching of DNS records
- 📖 Study: DNS caching: browser → OS → router → ISP resolver
- 📖 Study: DNS over HTTPS (DoH) and DNS over TLS (DoT) — why they exist

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Use `dig` to trace a full DNS resolution:
  - `dig google.com` — basic query
  - `dig +trace google.com` — see every step from root to authoritative
  - `dig MX gmail.com` — find mail servers
  - `dig TXT google.com` — see TXT records
- 🛠️ Set up your own local DNS using `dnsmasq` on your VM:
  - Add a fake domain `myapp.local` pointing to `127.0.0.1`
  - Resolve it from your host machine
- 🛠️ Capture DNS queries in Wireshark — see them on UDP port 53

### 📝 Evening Block (1 hr)
- 📝 Commit: DNS trace output, dnsmasq config, Wireshark DNS capture
- 📝 Write: "What happens when you type google.com" — now you can fill in the DNS part accurately
- 🔁 Recall: "What happens if a DNS server is unreachable? What's the fallback?"

---

## 📅 DAY 19 — HTTP/1.1: The Protocol of the Web

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: HTTP request structure — method, URL, HTTP version, headers, body
- 📖 Study: HTTP response structure — status line, headers, body
- 📖 Study: HTTP methods: GET, POST, PUT, PATCH, DELETE, HEAD, OPTIONS
- 📖 Study: HTTP status codes in depth:
  - 200 OK, 201 Created, 204 No Content
  - 301 Moved Permanently, 302 Found, 304 Not Modified
  - 400 Bad Request, 401 Unauthorized, 403 Forbidden, 404 Not Found, 409 Conflict, 429 Too Many Requests
  - 500 Internal Server Error, 502 Bad Gateway, 503 Service Unavailable, 504 Gateway Timeout
- 📖 Study: HTTP headers — `Content-Type`, `Authorization`, `Cache-Control`, `ETag`, `Cookie`, `CORS`
- 📖 Study: Statelessness — HTTP has no memory between requests

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Use `curl -v` to make requests and read raw headers:
  - `curl -v https://httpbin.org/get` — see response headers
  - `curl -X POST -H "Content-Type: application/json" -d '{"key":"value"}' https://httpbin.org/post`
  - `curl -I https://google.com` — HEAD request, see redirects
- 🛠️ Use browser DevTools (F12 → Network tab): inspect real HTTP requests to any website
  - Find: request headers, response headers, status code, timing breakdown (DNS, connect, TTFB, download)
- 🛠️ Write a Python script that makes HTTP requests using `requests` library and logs all headers

### 📝 Evening Block (1 hr)
- 📝 Commit: curl command examples with output, Python HTTP client script
- 🔁 Recall: "What is the difference between `401 Unauthorized` and `403 Forbidden`? When would each occur?"

---

## 📅 DAY 20 — HTTPS & TLS: Security in the Protocol Layer

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Why HTTP is insecure — plaintext, anyone on network can read it (man-in-the-middle)
- 📖 Study: TLS handshake — ClientHello, ServerHello, Certificate, Key Exchange, Finished
- 📖 Study: Symmetric vs asymmetric encryption:
  - Asymmetric (RSA/ECDH): Exchange keys securely. Slow. Used ONCE in handshake.
  - Symmetric (AES): Encrypt data. Fast. Used for actual data transfer.
- 📖 Study: SSL certificates — who issues them (CAs), DV vs OV vs EV certs
- 📖 Study: Certificate pinning, HSTS (HTTP Strict Transport Security)
- 📖 Study: Let's Encrypt — free SSL certificates, ACME protocol

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Inspect a TLS handshake in Wireshark: `curl https://google.com` while capturing
  - Find: Client Hello, Server Hello, Certificate, Application Data (encrypted)
- 🛠️ Install `openssl` and run: `openssl s_client -connect google.com:443` — see the certificate chain
- 🛠️ Set up a self-signed certificate for your local VM:
  - `openssl req -x509 -newkey rsa:4096 -keyout key.pem -out cert.pem -days 365 -nodes`
- 🛠️ Configure NGINX on your VM to serve HTTPS with the self-signed cert
- 🛠️ Use `curl -k` to connect to it (skip cert verification) and see the HTTPS response

### 📝 Evening Block (1 hr)
- 📝 Commit: NGINX HTTPS config, Wireshark TLS capture screenshot
- 📝 Write: "How HTTPS protects your data — what it encrypts, what it doesn't"
- 🔁 Recall: "Does HTTPS hide the destination IP address? Why or why not?"

---

## 📅 DAY 21 — HTTP/2 & HTTP/3: Evolution of the Web Protocol

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: HTTP/1.1 problems:
  - Head-of-line blocking: one slow request blocks the pipeline
  - Connection limits: browsers open 6 connections per domain
  - Header overhead: same headers sent every request (no compression)
- 📖 Study: HTTP/2 solutions:
  - Multiplexing: multiple requests on one connection, no blocking
  - Header compression (HPACK)
  - Server push
  - Binary framing (not human-readable text)
- 📖 Study: HTTP/2 new problem: TCP head-of-line blocking (one lost packet blocks all streams)
- 📖 Study: HTTP/3 and QUIC: UDP-based, built-in encryption (TLS 1.3), no HOL blocking at transport layer

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Use Chrome DevTools → Network → Protocol column to see which sites use h2 vs h3
- 🛠️ Configure NGINX to serve HTTP/2 (requires HTTPS):
  - `listen 443 ssl http2;` in your NGINX config
  - Verify with: `curl --http2 -I https://yourdomain`
- 🛠️ Benchmark: measure response time difference between HTTP/1.1 and HTTP/2 for 10 parallel requests
  - Use `curl` with `--http1.1` flag vs without (defaults to h2 if available)

### 📝 Evening Block (1 hr)
- 📝 Commit: NGINX HTTP/2 config, benchmark results
- 🔁 Recall: "What specific problem does QUIC solve that HTTP/2 couldn't fix? Why does QUIC use UDP?"

---

## 📅 DAY 22 — Build: Full "What Happens When You Type google.com" Document

### 🌅 Morning Block (1 hr)
- 📖 Review all Days 15–21 notes
- 📖 Read: "What happens when you type google.com" (GitHub repo — the famous one)

### 🛠️ Afternoon Block (2.5 hrs)
- 🛠️ Write your OWN comprehensive version of "What happens when you type google.com" — in your own words, step by step:
  1. Keyboard hardware interrupt → OS reads keystrokes
  2. Browser check URL (is it a search? is it a domain?)
  3. Browser DNS cache check
  4. OS DNS cache check (`/etc/hosts`)
  5. DNS resolver query → root → TLD → authoritative
  6. TCP connection to IP:443 (SYN → SYN-ACK → ACK)
  7. TLS handshake
  8. HTTP/2 GET request sent
  9. Server processes, sends response
  10. Browser parses HTML, fetches CSS/JS/images (more TCP connections or HTTP/2 streams)
  11. JavaScript executes
  12. Page renders
- 🛠️ Add a diagram for each major step

### 📝 Evening Block (1 hr)
- 📝 Commit this document as `what-happens-google.md` — this is a portfolio piece
- 📝 Optional: Post it on Dev.to as your first technical article
- 🔁 Recall: Everything from memory now. Close notes.

---

## 📅 DAY 23 — Load Balancers & Reverse Proxies

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Proxy vs Reverse Proxy — direction of connection initiation
- 📖 Study: Load balancing algorithms:
  - Round Robin: requests rotate between servers
  - Least Connections: send to server with fewest active connections
  - IP Hash: same client IP always goes to same server (sticky sessions)
  - Weighted Round Robin: distribute proportional to server capacity
- 📖 Study: Layer 4 vs Layer 7 load balancing — what's different
- 📖 Study: NGINX as a reverse proxy — `proxy_pass`, upstream blocks
- 📖 Study: Health checks — how load balancers detect dead backends

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Install NGINX on your VM
- 🛠️ Run 2 Python HTTP servers on different ports (port 8001 and 8002) — each responding with their own port number in the response body (so you can see which one handled the request)
- 🛠️ Configure NGINX upstream block to load balance between them with Round Robin
- 🛠️ Test: `curl localhost` 10 times — verify requests alternate between servers
- 🛠️ Change to Least Connections — test again
- 🛠️ Add health check: stop one server and verify NGINX stops sending traffic to it

### 📝 Evening Block (1 hr)
- 📝 Commit: NGINX config (commented), test output showing traffic distribution, architecture diagram
- 🔁 Recall: "What is SSL termination at the load balancer? What are the tradeoffs?"

---

## 📅 DAY 24 — CDN Concepts & Edge Caching

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: What is a CDN — edge servers geographically distributed, cache content close to users
- 📖 Study: How CDN caching works — `Cache-Control`, `max-age`, `s-maxage`, `ETag`, `Last-Modified`
- 📖 Study: Cache invalidation — the hard problem. Strategies: TTL expiry, event-based purge, versioned URLs
- 📖 Study: Cache-Control directives: `public` vs `private`, `no-cache` vs `no-store`, `must-revalidate`
- 📖 Study: Conditional requests: `If-None-Match` (ETag), `If-Modified-Since` → 304 Not Modified

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Add `Cache-Control` headers to your NGINX config for different content types
- 🛠️ Use curl to observe caching headers: `curl -I https://example.com` — read Cache-Control, ETag
- 🛠️ Simulate a CDN with NGINX proxy caching:
  - Configure `proxy_cache_path` and `proxy_cache` directives
  - Verify: first request hits backend, subsequent requests hit cache (check `X-Cache-Status` header)
- 🛠️ Test cache invalidation: change content on backend, observe old content still served from cache

### 📝 Evening Block (1 hr)
- 📝 Commit: NGINX proxy cache config, test output showing cache hits
- 🔁 Recall: "What is the difference between `Cache-Control: no-cache` and `Cache-Control: no-store`?"

---

## 📅 DAY 25 — Build First Real API with Network Concepts Applied

### 🌅 Morning Block (1 hr)
- 📖 Study: FastAPI basics — why it's fast (ASGI, async), automatic OpenAPI docs
- 📖 Install: `pip install fastapi uvicorn`

### 🛠️ Afternoon Block (3 hrs)
- 🛠️ Build a "Network Diagnostics API" — a REST API that:
  - `GET /dns/{domain}` → resolves domain to IP(s) using Python `socket.getaddrinfo()`
  - `GET /ping/{host}` → pings a host and returns RTT using `subprocess`
  - `GET /headers` → returns all headers of the incoming request
  - `GET /ip` → returns the client's IP address
  - `GET /traceroute/{host}` → runs traceroute and returns hops (subprocess)
- 🛠️ Add NGINX in front of it as a reverse proxy
- 🛠️ Test all endpoints with `curl` and document sample responses
- 🛠️ Access Swagger docs at `http://localhost/docs`

### 📝 Evening Block (1 hr)
- 📝 Commit: Full API code, NGINX config, README with API docs and sample curl commands
- 📝 Take screenshot of Swagger UI — add to README
- 🔁 Recall: "What is ASGI? How is it different from WSGI? Why does it matter for concurrency?"

---

## 📅 DAY 26 — Wireshark Deep Dive + Network Protocol Analysis

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Wireshark display filters — `http`, `tcp.port == 443`, `ip.addr == x.x.x.x`, `tcp.flags.syn == 1`
- 📖 Study: Wireshark color coding — what each color means
- 📖 Study: Follow TCP Stream — see the full conversation in human-readable form
- 📖 Study: Packet statistics — Protocol Hierarchy, Endpoints, Conversations

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Capture exercise 1: Your FastAPI application
  - Make 50 requests with `hey` load testing tool: `hey -n 50 http://localhost/dns/google.com`
  - Analyze in Wireshark: How many TCP connections? Are they reused (HTTP keep-alive)?
- 🛠️ Capture exercise 2: A login form (httpbin.org/post)
  - Submit a POST with username + password over plain HTTP
  - Find the credentials in Wireshark — proves why HTTPS is non-negotiable
- 🛠️ Save your `.pcap` files and commit them to your networking-lab repo

### 📝 Evening Block (1 hr)
- 📝 Annotate screenshots showing what you found in each capture
- 🔁 Recall: "How would a network engineer diagnose 'the website is slow' using Wireshark?"

---

## 📅 DAY 27 — Networking Lab: Build a Monitored Network Topology

### 🌅 Morning Block (1 hr)
- 📖 Plan your local network lab: 3 VMs — a web server, an application server, and a monitoring server

### 🛠️ Afternoon Block (3 hrs)
- 🛠️ Create 3 lightweight VMs in VirtualBox (use Ubuntu Server, minimal install)
  - VM1: NGINX web server (reverse proxy)
  - VM2: FastAPI application server
  - VM3: Will be used for monitoring later
- 🛠️ Configure networking: VMs on a private network, can communicate with each other
- 🛠️ Deploy your Network Diagnostics API on VM2, NGINX on VM1 proxying to VM2
- 🛠️ Draw: Your lab topology diagram with IP addresses, arrows showing traffic flow

### 📝 Evening Block (1 hr)
- 📝 Commit: topology diagram, VM configuration notes, deployment steps
- 📝 This topology is your base for the entire course
- 🔁 Recall: "What is the difference between a private network (VirtualBox host-only) and NAT networking for VMs?"

---

## 📅 DAY 28 — WebSockets & Real-Time Communication

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: WebSocket upgrade — starts as HTTP, `Upgrade: websocket` header, switches protocol
- 📖 Study: WebSocket frame structure — binary/text frames, ping/pong, close frames
- 📖 Study: When to use WebSockets vs HTTP polling vs Server-Sent Events (SSE)
  - WebSocket: bidirectional, low-latency (chat, gaming, collaborative editing)
  - SSE: server-to-client only, simpler (live dashboards, notifications)
  - Long polling: fallback for environments without WebSocket support
- 📖 Study: WebSocket scaling challenges — sticky sessions required (or Redis pub/sub)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Build a real-time chat application with FastAPI WebSockets:
  - Multiple clients can connect
  - Any message sent is broadcast to ALL connected clients
  - Show connected user count
- 🛠️ Build a simple HTML client (served by FastAPI) that connects and chats
- 🛠️ Capture the WebSocket connection in Wireshark — see the HTTP upgrade, then binary frames

### 📝 Evening Block (1 hr)
- 📝 Commit: chat app code, HTML client, Wireshark WebSocket capture screenshot
- 🔁 Recall: "What happens to a WebSocket connection if the load balancer doesn't support sticky sessions?"

---

## 📅 DAY 29 — gRPC & Protocol Buffers

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Why gRPC? — binary protocol, strongly typed, HTTP/2 based, auto-generated client/server code
- 📖 Study: Protocol Buffers (.proto files) — schema definition language
- 📖 Study: gRPC service types: Unary, Server Streaming, Client Streaming, Bidirectional Streaming
- 📖 Study: gRPC vs REST tradeoffs:
  - gRPC: faster, typed, requires shared proto files, harder to debug
  - REST: universal, JSON is human-readable, easy to consume from anywhere

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Install: `pip install grpcio grpcio-tools`
- 🛠️ Write a `.proto` file for a simple User service (GetUser, CreateUser)
- 🛠️ Generate Python code: `python -m grpc_tools.protoc ...`
- 🛠️ Implement the server and a client
- 🛠️ Compare response time: same operation via REST (FastAPI) vs gRPC — benchmark with 1000 requests

### 📝 Evening Block (1 hr)
- 📝 Commit: `.proto` file, server, client, benchmark results comparison
- 🔁 Recall: "Google uses gRPC internally. Facebook uses Thrift. Netflix uses REST. What factors would drive this choice?"

---

## 📅 DAY 30 — Postman, API Testing & OpenAPI Documentation

### 🌅 Morning Block (1 hr)
- 📖 Study: OpenAPI specification — the standard for documenting REST APIs
- 📖 Study: Postman collections — grouping API requests, environment variables, tests
- 📖 Study: Contract testing — testing that your API matches its documented specification

### 🛠️ Afternoon Block (2.5 hrs)
- 🛠️ Add proper OpenAPI metadata to your FastAPI app (title, description, version, tags)
- 🛠️ Create Postman collection:
  - One request per endpoint
  - Environment variables for base URL, auth token
  - Automated tests in each request (status code checks, response schema validation)
- 🛠️ Export the Postman collection as JSON and commit it
- 🛠️ Add a link to your Swagger docs in your README

### 📝 Evening Block (1 hr)
- 📝 Commit: enriched OpenAPI metadata, Postman collection JSON, Swagger screenshot
- 🔁 Recall: "What is the difference between API documentation and API specification?"

---

## 📅 DAY 31–35 — Phase 1 Integration Week

### DAY 31 — Networking Review + Write "What Happens" Document Upgrade
- 📖 Review everything from Days 15–30
- 🛠️ Upgrade your "what happens when you type google.com" with more detail from everything learned
- 📝 Commit the final, comprehensive version

### DAY 32 — Network Security Concepts
- 📖 Study: Firewalls (stateless vs stateful), DDoS attacks, rate limiting at network layer
- 📖 Study: Common attacks: MITM, DNS spoofing, SYN flood, SQL injection (preview)
- 🛠️ Configure `ufw` on all 3 VMs with proper firewall rules (only necessary ports open)
- 📝 Document your firewall rules and the reasoning for each

### DAY 33 — Build: Minimal API Gateway with NGINX
- 🛠️ Configure NGINX as an API Gateway:
  - Route `/api/users/` to User service
  - Route `/api/orders/` to Order service (just stubs for now)
  - Add rate limiting: 10 requests/second per IP
  - Add request logging with correlation ID (generate UUID in NGINX, pass as header)
- 📝 Commit: NGINX API gateway config with full comments

### DAY 34 — Load Testing Your API
- 🛠️ Install `locust` (Python load testing tool): `pip install locust`
- 🛠️ Write a Locust test file: 100 virtual users, ramp up over 30 seconds, run for 5 minutes
- 🛠️ Run the load test against your NGINX → FastAPI setup
- 🛠️ Record: requests/sec, failure rate, p50/p95/p99 latency
- 📝 Commit: locust test file, results CSV, screenshot of Locust web UI during test

### DAY 35 — Phase 1 Checkpoint & Portfolio Push
- 📖 Review ALL Phase 1 active recall questions
- 🛠️ Ensure all repos are organized and README files are complete
- ✅ Phase 1 checklist:
  - [ ] Wireshark capture with full annotation
  - [ ] "What happens when you type google.com" — comprehensive version
  - [ ] Network Diagnostics API deployed and documented
  - [ ] NGINX reverse proxy + load balancer working
  - [ ] WebSocket chat application
  - [ ] gRPC service with benchmark comparison
  - [ ] Postman collection exported and committed
  - [ ] NGINX API gateway with rate limiting
  - [ ] Load test results with Locust

---

---

# 🔵 PHASE 2: Operating Systems & Hardware (Days 36–56)

---

## 📅 DAY 36 — Processes & the Process Lifecycle

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Process in depth — PCB (Process Control Block), PID, PPID, memory layout (text, data, heap, stack segments)
- 📖 Study: `fork()` syscall — copies parent process, returns 0 to child and PID to parent
- 📖 Study: `exec()` family — replaces process image with a new program
- 📖 Study: Process states in detail — Running, Runnable, Interruptible Sleep, Uninterruptible Sleep, Zombie, Stopped
- 📖 Study: `wait()` syscall — why parent must wait for child to prevent zombies

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Write a Python program that:
  - Uses `os.fork()` to create 5 child processes
  - Each child sleeps a random amount then exits with a unique exit code
  - Parent waits for all children and reports each exit code
- 🛠️ Deliberately create a zombie: fork without wait, observe with `ps aux | grep Z`
- 🛠️ Use `strace` to see syscalls: `strace ls` — understand what simple commands do at OS level
- 🛠️ Run: `cat /proc/PID/status`, `/proc/PID/maps`, `/proc/PID/fd` for a running process

### 📝 Evening Block (1 hr)
- 📝 Commit: fork demo code, zombie demo code, strace output, /proc exploration notes
- 🔁 Recall: "What is a zombie process? Why is it a problem? How do you prevent it?"

---

## 📅 DAY 37 — Threads, Concurrency & the GIL

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Thread vs Process — shared memory, lighter weight, same address space
- 📖 Study: Python's GIL — why it exists (CPython memory management), what it prevents, what it doesn't
- 📖 Study: `threading` module — Thread class, daemon threads
- 📖 Study: `multiprocessing` module — bypasses GIL, true parallelism
- 📖 Study: `asyncio` — cooperative concurrency (single thread), event loop, coroutines, `async/await`

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Benchmark 3 approaches for a CPU-bound task (calculate prime numbers):
  - Sequential (baseline)
  - Threading (does GIL prevent speedup?)
  - Multiprocessing (bypasses GIL)
  - Compare execution time on a machine with 4+ cores
- 🛠️ Benchmark for an I/O-bound task (make 100 HTTP requests):
  - Sequential
  - Threading
  - Asyncio
  - Compare — threading and asyncio should be fast, sequential should be slow
- 🛠️ Write results in a comparison table

### 📝 Evening Block (1 hr)
- 📝 Commit: benchmark code, results table, explanation of why each approach differs
- 🔁 Recall: "When should you use asyncio vs threading vs multiprocessing? Give a use case for each."

---

## 📅 DAY 38 — Race Conditions & Synchronization

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Race condition — two threads read-modify-write shared data simultaneously
- 📖 Study: Critical section — code that accesses shared resources
- 📖 Study: Mutex (mutual exclusion lock) — only one thread enters critical section
- 📖 Study: Deadlock — conditions: Mutual Exclusion, Hold and Wait, No Preemption, Circular Wait
- 📖 Study: Deadlock prevention vs deadlock avoidance vs deadlock detection
- 📖 Study: Semaphore — counting semaphore (controls N simultaneous accesses)
- 📖 Study: Condition variables — wait for a condition, notify when it changes

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Demonstrate race condition:
  - 10 threads each increment a counter 10,000 times (should be 100,000 total)
  - Without lock: result is wrong (less than 100,000)
  - With Lock: result is correct
- 🛠️ Demonstrate deadlock:
  - Thread A acquires Lock1, waits for Lock2
  - Thread B acquires Lock2, waits for Lock1
  - Both hang forever
  - Fix: always acquire locks in the same order
- 🛠️ Implement a thread-safe queue (producer/consumer) using Condition variables

### 📝 Evening Block (1 hr)
- 📝 Commit: race condition demo + fix, deadlock demo + fix, producer/consumer code
- 📝 Write documentation explaining the bug and the fix for each
- 🔁 Recall: "What are the 4 conditions for deadlock? If you eliminate one, deadlock is impossible — which is easiest to eliminate and why?"

---

## 📅 DAY 39 — Memory Management: Stack, Heap & Virtual Memory

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Stack vs Heap — allocation, deallocation, size limits, access speed
- 📖 Study: Stack overflow — infinite recursion, what the OS does
- 📖 Study: Heap allocation — `malloc`/`free` in C, GC in Python/Java
- 📖 Study: Virtual memory — page tables, address translation
- 📖 Study: Paging — fixed-size pages (typically 4KB), page faults, demand paging
- 📖 Study: Swap space — when RAM is full, pages move to disk (very slow!)
- 📖 Study: Memory-mapped files — `mmap` syscall, how databases use it

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Read `/proc/PID/maps` for your Python script — understand each region (text, heap, stack, mmap'd libs)
- 🛠️ Write a Python script that allocates large amounts of memory (list of large arrays) and monitor with `htop`
- 🛠️ Observe swap usage: `vmstat 1 10` — watch si/so columns (swap in/out)
- 🛠️ Write a Python script using `mmap` to read a large file efficiently
- 🛠️ Measure: reading 1GB file with normal read() vs mmap — compare speed

### 📝 Evening Block (1 hr)
- 📝 Commit: mmap benchmark, memory allocation monitoring notes
- 🔁 Recall: "What is a page fault? What are the two types? Which is catastrophic?"

---

## 📅 DAY 40 — File System Internals

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Inodes — what they store (permissions, timestamps, block pointers) and what they DON'T (the filename!)
- 📖 Study: Directory entries — map filename → inode number
- 📖 Study: Hard links vs symbolic links — what happens at the inode level
- 📖 Study: ext4 internals — block groups, journal, superblock
- 📖 Study: File system journaling — why it exists (crash recovery), data vs metadata journaling

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Explore inodes: `ls -i` to see inode numbers, `stat filename` to see inode details
- 🛠️ Create a hard link and symbolic link — compare behavior when the original is deleted
- 🛠️ Create a test filesystem image:
  - `dd if=/dev/zero of=testfs.img bs=1M count=100`
  - `mkfs.ext4 testfs.img`
  - Mount it: `mount -o loop testfs.img /mnt/test`
  - Create files, check inode usage: `df -i`
- 🛠️ Use `debugfs` to inspect ext4 internals

### 📝 Evening Block (1 hr)
- 📝 Commit: inode exploration output, hard link vs symlink behavior documented
- 🔁 Recall: "You delete a file but disk space isn't freed. What could cause this?"

---

## 📅 DAY 41 — I/O: Sequential vs Random, Buffered vs Direct

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Sequential vs random I/O — why sequential is faster (HDDs: seek time, SSDs: less so)
- 📖 Study: OS page cache — buffered I/O goes through cache, direct I/O bypasses it
- 📖 Study: `fsync()` — forces page cache to flush to disk. Essential for durability.
- 📖 Study: Write-Ahead Logging (WAL) — write to log first (sequential), then apply to data files
- 📖 Study: `O_DIRECT` — bypass page cache (used by databases that manage their own cache)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Benchmark sequential vs random read of a 1GB file:
  - Sequential: read 1GB file from start to end
  - Random: read 1000 random 1MB chunks
  - Time both. Observe with `iostat -x 1` during the test.
- 🛠️ Implement a minimal WAL in Python:
  - Every write operation: append to log file first (with `fsync`), then apply to data file
  - Simulate a crash (Ctrl+C during apply) → recover from log on next start
- 🛠️ Monitor I/O with `iotop -ao` during your benchmarks

### 📝 Evening Block (1 hr)
- 📝 Commit: benchmark results, WAL implementation with recovery
- 🔁 Recall: "Why does Kafka achieve high throughput? What I/O pattern does it use?"

---

## 📅 DAY 42 — Signals, IPC & System Calls

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Signals — SIGTERM (graceful), SIGKILL (force), SIGHUP (reload config), SIGINT (Ctrl+C)
- 📖 Study: Signal handlers — catching signals in code for graceful shutdown
- 📖 Study: IPC mechanisms:
  - Pipes (`|`) — unidirectional, related processes
  - Named pipes (FIFOs) — persistent, any processes
  - Unix sockets — bidirectional, local only (faster than TCP)
  - Shared memory — fastest IPC, most complex
  - Message queues (POSIX) — kernel-managed queue
- 📖 Study: System calls — the interface between user space and kernel

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Write a Python server that handles SIGTERM for graceful shutdown:
  - Finish processing current request
  - Close DB connections
  - Log "shutting down" message
  - Then exit cleanly
- 🛠️ Write a parent-child pair communicating via Unix socket (faster than TCP for local IPC)
- 🛠️ Use `strace` to observe the syscalls made during your FastAPI request handling

### 📝 Evening Block (1 hr)
- 📝 Commit: graceful shutdown implementation, Unix socket IPC code
- 🔁 Recall: "Why is SIGKILL unstoppable? What can't it interrupt?"

---

## 📅 DAY 43 — CPU Scheduling & Context Switching

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: CPU scheduling algorithms — FIFO, Round Robin, Priority, CFS (Completely Fair Scheduler — Linux default)
- 📖 Study: Context switch — what the OS saves and restores, why it's expensive (~microseconds)
- 📖 Study: Process priority (`nice` values), real-time scheduling
- 📖 Study: CPU affinity — pin process to specific core(s)
- 📖 Study: NUMA — Non-Uniform Memory Access, why memory location relative to CPU matters

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Use `perf stat` to count context switches: `perf stat -e context-switches your_script.py`
- 🛠️ Benchmark: N threads all fighting for CPU vs N processes on N cores (CPU affinity set)
- 🛠️ Use `taskset` to pin a CPU-intensive process to a specific core — measure throughput
- 🛠️ Observe scheduler behavior: `watch -n 0.5 "ps -eo pid,ni,cls,pri,psr,comm | head -20"`

### 📝 Evening Block (1 hr)
- 📝 Commit: context switch benchmark, CPU affinity test results
- 🔁 Recall: "Why do database servers often have 'CPU pinning' configurations?"

---

## 📅 DAY 44 — Hardware: Storage Deep Dive (HDD vs SSD vs NVMe)

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: HDD mechanics — spinning platters, read/write heads, seek time (~10ms), rotational latency, sequential bandwidth
- 📖 Study: SSD — NAND flash, no moving parts, wear leveling, sequential: ~500MB/s, random ~10x better than HDD
- 📖 Study: NVMe — PCIe interface (not SATA), sequential: ~3500MB/s, latency ~20µs
- 📖 Study: Storage IOPS — what they measure, why random IOPS matter for databases
- 📖 Study: RAID levels — RAID 0 (stripe, no redundancy), RAID 1 (mirror), RAID 5 (stripe + parity), RAID 10 (stripe + mirror)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Benchmark your actual storage:
  - `dd if=/dev/zero of=testfile bs=1G count=1 oflag=dsync` — sequential write speed
  - `fio` tool: `sudo apt install fio` — benchmark random read/write IOPS
  - Compare results with published HDD/SSD/NVMe specs
- 🛠️ Document your machine's storage type, actual measured performance vs theoretical max

### 📝 Evening Block (1 hr)
- 📝 Commit: fio benchmark results, storage comparison table (HDD vs SSD vs NVMe theoretical and measured)
- 🔁 Recall: "A database workload is primarily random reads. Which storage matters most: sequential speed or IOPS? Why?"

---

## 📅 DAY 45 — Hardware-Software Architecture: Putting It All Together

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Network Interface Cards (NIC) — how packets arrive: wire → NIC → DMA → kernel ring buffer → socket buffer → application
- 📖 Study: Interrupt coalescing — why NICs batch interrupts (tradeoff: latency vs CPU usage)
- 📖 Study: Kernel bypass networking — DPDK, why companies like Cloudflare bypass the kernel
- 📖 Study: CPU-memory-storage-network interaction in a real web request

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Draw a complete hardware-to-software architecture for a web server handling one HTTP request:
  - NIC receives packet → interrupt → kernel network stack → socket → FastAPI → PostgreSQL → Redis → Response path
  - Label: which hardware component is involved at each step, which Linux kernel subsystem handles it
- 🛠️ Research: How does Cloudflare handle 100M+ requests/day? Write a 1-page summary with diagram.

### 📝 Evening Block (1 hr)
- 📝 Commit: architecture diagram, Cloudflare research summary
- 🔁 Recall: "Trace the path of a single byte of data from a PostgreSQL database on disk to a user's browser screen"

---

## 📅 DAY 46–49 — OS & Hardware Integration Projects

### DAY 46 — Build: System Performance Monitor (Full Version)
- 🛠️ Build a comprehensive Python system monitor using `psutil`:
  - CPU: usage per core, frequency, context switches, interrupts
  - Memory: total, used, cached, swap, page faults
  - Disk: I/O reads/writes/latency per device
  - Network: bytes in/out per interface, error count, drop count
  - Processes: top 10 by CPU and memory
- 🛠️ Output as structured JSON (for future Prometheus integration)
- 📝 Commit with full documentation

### DAY 47 — Build: WAL-Based Key-Value Store
- 🛠️ Build a crash-safe key-value store in Python:
  - `set(key, value)` → writes to WAL, then updates in-memory dict
  - `get(key)` → reads from in-memory dict
  - `recover()` → on startup, replays WAL to rebuild in-memory state
  - `checkpoint()` → compacts WAL into snapshot file, then truncates WAL
- 📝 Commit with crash recovery test and documentation

### DAY 48 — Concurrency Deep Dive: Async Python Server
- 🛠️ Build an async HTTP server from scratch using Python `asyncio` (no FastAPI):
  - Handle multiple concurrent connections
  - Each connection handler is a coroutine
  - Measure: how many concurrent connections can it handle?
- 📝 Commit and compare with synchronous version

### DAY 49 — Phase 2 Review + Checkpoint
- 📖 Review all Phase 2 notes
- ✅ Checklist:
  - [ ] Fork/zombie/wait demo
  - [ ] Race condition + deadlock demos with fixes
  - [ ] Concurrency benchmark (CPU-bound vs I/O-bound)
  - [ ] WAL implementation with recovery
  - [ ] Storage benchmarks (HDD/SSD/NVMe comparison)
  - [ ] Full hardware-to-software architecture diagram
  - [ ] System performance monitor script

---

---

# 🟡 PHASE 3: Databases (Days 50–84)

---

## 📅 DAY 50 — Relational Model & SQL Foundations

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Relational model — tables, rows, columns, primary keys, foreign keys, constraints
- 📖 Study: SQL data types — INTEGER, BIGINT, VARCHAR, TEXT, BOOLEAN, DECIMAL, TIMESTAMP, UUID, JSONB
- 📖 Study: Normalization — 1NF (atomic values), 2NF (no partial dependency), 3NF (no transitive dependency)
- 📖 Install: PostgreSQL (`sudo apt install postgresql`) — use `psql` CLI

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Design and create a normalized schema for an e-commerce system:
  - `users (id, email, name, created_at, deleted_at)`
  - `products (id, name, description, price, stock_count, category_id)`
  - `categories (id, name, parent_id)`
  - `orders (id, user_id, status, total_amount, created_at)`
  - `order_items (id, order_id, product_id, quantity, unit_price)`
  - `addresses (id, user_id, street, city, state, country, postal_code)`
- 🛠️ Create schema in PostgreSQL, add proper constraints (NOT NULL, UNIQUE, FK)
- 🛠️ Insert 1000 rows of fake data using Python `faker` library

### 📝 Evening Block (1 hr)
- 📝 Create `postgres-projects/ecommerce-schema/` in your GitHub
- 📝 Commit: SQL DDL file, seed data script, dbdiagram.io link in README
- 🔁 Recall: "What is the difference between 2NF and 3NF? Give an example of each violation."

---

## 📅 DAY 51 — SQL: Queries, JOINs & Aggregations

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: SELECT with WHERE, ORDER BY, LIMIT, OFFSET
- 📖 Study: JOINs — INNER, LEFT, RIGHT, FULL OUTER, CROSS — when and why each
- 📖 Study: GROUP BY + HAVING — aggregation with filtering
- 📖 Study: Aggregate functions: COUNT, SUM, AVG, MIN, MAX, COUNT DISTINCT
- 📖 Study: Subqueries — correlated vs non-correlated
- 📖 Study: CTEs (Common Table Expressions) — `WITH` clauses, readability vs performance

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Write SQL queries to answer real business questions on your e-commerce DB:
  1. Top 10 customers by total spend in last 30 days
  2. Products with low stock (stock_count < 10) in each category
  3. Revenue by category this month vs last month
  4. Customers who made an order in the last 7 days but NOT in the previous 30 days
  5. Average order value by day of week
  6. Products never ordered (LEFT JOIN trick)
  7. Identify duplicate users (same email registered twice)

### 📝 Evening Block (1 hr)
- 📝 Commit: SQL query file with comments explaining each query's business purpose
- 🔁 Recall: "What is the difference between WHERE and HAVING? Can you use HAVING without GROUP BY?"

---

## 📅 DAY 52 — Advanced SQL: Window Functions, CTEs & Optimization

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Window functions — `ROW_NUMBER()`, `RANK()`, `DENSE_RANK()`, `LAG()`, `LEAD()`, `SUM() OVER()`, `PARTITION BY`
- 📖 Study: Recursive CTEs — for hierarchical data (categories, org charts, friend networks)
- 📖 Study: EXPLAIN and EXPLAIN ANALYZE — how to read a query plan
  - Seq Scan vs Index Scan vs Bitmap Index Scan
  - Hash Join vs Nested Loop vs Merge Join
  - Cost estimation and actual execution time

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Window function queries:
  - Rank products by sales volume within each category
  - Calculate rolling 7-day revenue using `SUM() OVER (ORDER BY date ROWS BETWEEN 6 PRECEDING AND CURRENT ROW)`
  - Show each order's value compared to that customer's average order (LAG/LEAD)
- 🛠️ Use `EXPLAIN ANALYZE` on 3 of your complex queries — take note of:
  - Which nodes are most expensive?
  - Is it doing a sequential scan on a large table?
- 🛠️ Try to rewrite one slow query to avoid a sequential scan (hint: it may need an index)

### 📝 Evening Block (1 hr)
- 📝 Commit: window function queries, EXPLAIN ANALYZE outputs before/after optimization
- 🔁 Recall: "What is the N+1 query problem? Show me with an example and then show the fix."

---

## 📅 DAY 53 — Indexes: The Most Important Performance Tool

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: B-Tree index internals — how data is organized, why it's O(log n) to search
- 📖 Study: Index types in PostgreSQL: B-Tree, Hash, GiST, GIN, BRIN
- 📖 Study: Composite indexes — column order matters! Why?
- 📖 Study: Index-only scans — when the index has all data needed (no heap fetch)
- 📖 Study: Partial indexes — index only rows matching a condition (e.g., `WHERE deleted_at IS NULL`)
- 📖 Study: Index bloat and VACUUM — dead tuples, autovacuum

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Generate 1 million rows in your orders table (use a PL/pgSQL loop or Python bulk insert)
- 🛠️ Query: "Find all orders for user_id = 12345" — run EXPLAIN ANALYZE:
  - WITHOUT index: Seq Scan (slow)
  - ADD index: `CREATE INDEX idx_orders_user_id ON orders(user_id);`
  - AFTER index: Index Scan (fast) — record the timing difference
- 🛠️ Create a partial index for active orders (status = 'pending') — test query speed
- 🛠️ Create a composite index and test column order matters

### 📝 Evening Block (1 hr)
- 📝 Commit: SQL with timing results table (before/after each index), EXPLAIN ANALYZE screenshots
- 🔁 Recall: "You have a composite index on (user_id, created_at). Does a query filtering only on created_at use this index? Why or why not?"

---

## 📅 DAY 54 — Transactions & ACID Properties

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Transactions — `BEGIN`, `COMMIT`, `ROLLBACK`, `SAVEPOINT`
- 📖 Study: ACID in depth:
  - **Atomicity**: PostgreSQL uses WAL to ensure all-or-nothing
  - **Consistency**: Constraints (FK, UNIQUE, CHECK) are enforced at commit
  - **Isolation**: How concurrent transactions interact (see below)
  - **Durability**: WAL ensures committed data survives crashes
- 📖 Study: Isolation levels and their anomalies:
  - Read Uncommitted: dirty reads (PostgreSQL doesn't implement this)
  - Read Committed (default): no dirty reads, but non-repeatable reads possible
  - Repeatable Read: no non-repeatable reads, but phantom reads possible
  - Serializable: completely isolated, as if transactions ran sequentially

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Demonstrate isolation anomalies:
  - Open 2 psql sessions simultaneously
  - Demo non-repeatable read: Session A reads row, Session B updates it, Session A reads again — different!
  - Demo phantom read: Session A counts rows, Session B inserts, Session A counts again — different!
  - Fix with `SET TRANSACTION ISOLATION LEVEL REPEATABLE READ;`
- 🛠️ Demonstrate deadlock in PostgreSQL:
  - Session A: UPDATE orders WHERE id=1; UPDATE orders WHERE id=2
  - Session B: UPDATE orders WHERE id=2; UPDATE orders WHERE id=1
  - PostgreSQL will detect and resolve with an error — handle it in application code

### 📝 Evening Block (1 hr)
- 📝 Commit: Transaction isolation demo scripts, deadlock demo, documentation
- 🔁 Recall: "Your payment service needs to deduct from account A and credit account B. How do you ensure this is atomic even if the server crashes halfway through?"

---

## 📅 DAY 55 — PostgreSQL: Stored Procedures, Views & Triggers

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: PL/pgSQL — PostgreSQL's procedural language
- 📖 Study: Functions vs Stored Procedures — return value vs side effects
- 📖 Study: Views — virtual tables, updatable views, materialized views (pre-computed, must be refreshed)
- 📖 Study: Triggers — execute function before/after INSERT/UPDATE/DELETE
- 📖 Study: When to use stored procedures vs application logic — tradeoffs

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Create a stored procedure: `checkout_book(user_id, book_id)` for your Library Management System:
  - Check book is available
  - Create a checkout record
  - Decrement available count
  - All in one transaction
- 🛠️ Create a trigger: `updated_at` column automatically updates on any row update
- 🛠️ Create a materialized view: `monthly_revenue_summary` — pre-computed, refreshed daily
- 🛠️ Build Library Management System complete: Users, Books, Checkouts, Fines

### 📝 Evening Block (1 hr)
- 📝 Commit: Library Management System SQL (DDL + stored procedures + triggers + views)
- 🔁 Recall: "What is a materialized view? When would you choose it over a regular view?"

---

## 📅 DAY 56 — Redis: In-Memory Data Structures

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Redis data structures and time complexity:
  - String: `SET`, `GET`, `INCR`, `DECR`, `EXPIRE` — O(1)
  - Hash: `HSET`, `HGET`, `HGETALL` — O(1) per field
  - List: `LPUSH`, `RPUSH`, `LPOP`, `LRANGE` — O(1) push/pop, O(n) range
  - Set: `SADD`, `SMEMBERS`, `SINTERSTORE` — O(1) add, O(n) members
  - Sorted Set: `ZADD`, `ZRANGE`, `ZRANK` — O(log n) operations
- 📖 Study: Redis Pub/Sub — simple message broadcasting
- 📖 Study: Redis persistence — RDB (periodic snapshots) vs AOF (append-only log)
- 📖 Study: Redis Sentinel vs Redis Cluster

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Install Redis: `sudo apt install redis-server`
- 🛠️ Explore all data types with `redis-cli`:
  - String: store a user session
  - Hash: store user profile fields
  - List: implement a simple message queue
  - Set: track unique visitors per day
  - Sorted Set: build a leaderboard (score = points)
- 🛠️ Implement TTL-based session storage: sessions expire after 30 minutes of inactivity

### 📝 Evening Block (1 hr)
- 📝 Commit: redis-cli command examples with output, session storage implementation
- 🔁 Recall: "Why would you use a Sorted Set for a leaderboard? What operations does it give you that a Hash wouldn't?"

---

## 📅 DAY 57 — Redis: Caching Patterns & Cache-Aside Implementation

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Cache-Aside (Lazy Loading) pattern — flow, implementation, TTL strategy
- 📖 Study: Cache stampede / thundering herd — what happens when many requests miss cache simultaneously
- 📖 Study: Cache warming — pre-populating cache before traffic arrives
- 📖 Study: Cache eviction policies: LRU, LFU, TTL-only — when to use each
- 📖 Study: Redis as a cache: `maxmemory`, `maxmemory-policy` configuration

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Add Redis caching to your FastAPI + PostgreSQL e-commerce API:
  - `GET /products/{id}` — cache result for 60 seconds
  - Add cache hit/miss logging: `logger.info("Cache HIT for product %s", product_id)` or `MISS`
  - Add `X-Cache` header in response: `HIT` or `MISS`
- 🛠️ Benchmark: 1000 requests to `/products/1` with cache vs without cache — compare latency

### 📝 Evening Block (1 hr)
- 📝 Commit: FastAPI + Redis caching code, benchmark results with cache hit rate
- 🔁 Recall: "What is the cache stampede problem? How would you prevent it in production?"

---

## 📅 DAY 58 — Redis: Rate Limiting & Real Use Cases

### 🌅 Morning Block (1 hr)
- 📖 Study: Rate limiting algorithms revisited — Fixed Window, Sliding Window, Token Bucket with Redis implementation
- 📖 Study: Redis Lua scripts — atomic execution across multiple commands (no race conditions)

### 🛠️ Afternoon Block (3 hrs)
- 🛠️ Implement 3 rate limiters in Redis + FastAPI middleware:
  1. Fixed Window: `INCR key; EXPIRE key 60` — limit 100 requests/minute per IP
  2. Sliding Window: Use a sorted set of timestamps, remove expired, count remaining
  3. Token Bucket: Store (tokens, last_refill) in Hash, Lua script to atomically refill + consume
- 🛠️ Test each: hammer with 200 requests, verify the 101st returns 429 Too Many Requests
- 🛠️ Add `X-RateLimit-Remaining` and `Retry-After` headers to the 429 response

### 📝 Evening Block (1 hr)
- 📝 Commit: all 3 rate limiter implementations, test output showing 429s, explanation of tradeoffs
- 🔁 Recall: "Why is the fixed window rate limiter vulnerable to burst attacks at window boundaries? Draw it."

---

## 📅 DAY 59 — NoSQL: MongoDB & Document Databases

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Document model — BSON documents, flexible schema, nested documents, arrays
- 📖 Study: When MongoDB makes sense — evolving schema, hierarchical data, content management
- 📖 Study: MongoDB query language — find, insert, update, delete, aggregation pipeline
- 📖 Study: MongoDB indexing — similar to SQL but for document fields
- 📖 Study: Schema design in MongoDB — embedding vs referencing (opposite intuition from SQL!)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Install MongoDB or use Docker: `docker run -d -p 27017:27017 mongo`
- 🛠️ Model a blog system: Posts contain embedded Comments (not separate collection)
  - Compare with relational approach: what queries are faster? What's harder?
- 🛠️ Use MongoDB aggregation pipeline: find top 10 most-commented posts

### 📝 Evening Block (1 hr)
- 📝 Commit: MongoDB schema, comparison document (SQL schema vs MongoDB schema for same domain)
- 🔁 Recall: "In MongoDB, when should you embed a document vs reference another collection? Give criteria."

---

## 📅 DAY 60 — CAP Theorem & Distributed Database Concepts

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: CAP Theorem — Consistency, Availability, Partition Tolerance — you get 2
- 📖 Study: Why Partition Tolerance is non-negotiable in distributed systems
- 📖 Study: CP systems: PostgreSQL, Redis (in certain configs) — consistency over availability
- 📖 Study: AP systems: Cassandra, DynamoDB — availability over consistency
- 📖 Study: Eventual consistency — how it works, convergence, conflict resolution
- 📖 Study: PACELC theorem — extends CAP to include latency tradeoffs

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Write a comprehensive comparison document:
  - PostgreSQL: ACID, CP, vertical scaling, when to use
  - Redis: CP/AP depending on config, caching, when to use
  - MongoDB: flexible, AP-leaning, when to use
  - Cassandra (conceptual): AP, write-optimized, time-series, when to use
- 🛠️ Draw: Decision tree for database selection based on requirements

### 📝 Evening Block (1 hr)
- 📝 Commit: comparison document, decision tree diagram
- 🔁 Recall: "Instagram uses PostgreSQL. Twitter used MySQL. WhatsApp uses Mnesia. Explain why each makes sense for their use case."

---

## 📅 DAY 61 — Database Scaling: Read Replicas & Sharding

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Read replicas — async replication, replication lag, use cases (reporting, read-heavy workloads)
- 📖 Study: Sharding — horizontal partitioning, shard key selection, hotspot problem
- 📖 Study: Shard key options: range-based, hash-based, geographic — tradeoffs of each
- 📖 Study: Cross-shard queries — why they're expensive and how to minimize them
- 📖 Study: Resharding — adding/removing shards, consistent hashing approach

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Set up PostgreSQL streaming replication between two VMs:
  - Primary: `wal_level = replica`, configure `pg_hba.conf` for replication user
  - Replica: `recovery.conf` (or `standby.signal` in PG12+) pointing to primary
  - Test: insert on primary, read from replica — measure replication lag
- 🛠️ Write a Python application that routes reads to replica and writes to primary
- 🛠️ Design (on paper) a sharding strategy for a social network with 100M users — justify your shard key

### 📝 Evening Block (1 hr)
- 📝 Commit: replication setup guide, Python read/write routing code, sharding design document
- 🔁 Recall: "You chose user_id as a shard key for a social network. A celebrity user has 50M followers. What problem does this cause?"

---

## 📅 DAY 62 — Connection Pooling & Database Performance

### 🌅 Morning Block (1 hr)
- 📖 Study: Why connection pooling? — PostgreSQL connection cost: fork process, ~5MB RAM per connection
- 📖 Study: PgBouncer — PostgreSQL connection pooler, transaction mode vs session mode
- 📖 Study: SQLAlchemy connection pool — `pool_size`, `max_overflow`, `pool_timeout`
- 📖 Study: Slow query logging — `log_min_duration_statement` in PostgreSQL

### 🛠️ Afternoon Block (2.5 hrs)
- 🛠️ Install PgBouncer: `sudo apt install pgbouncer`
- 🛠️ Configure PgBouncer in front of PostgreSQL
- 🛠️ Benchmark:
  - 500 concurrent connections directly to PostgreSQL → observe PostgreSQL strain
  - 500 concurrent connections through PgBouncer → observe improvement
- 🛠️ Enable slow query logging in PostgreSQL (log queries > 100ms)
- 🛠️ Run a query that takes > 100ms, find it in PostgreSQL logs

### 📝 Evening Block (1 hr)
- 📝 Commit: PgBouncer config, benchmark results comparing direct vs pooled connections
- 🔁 Recall: "What is the difference between PgBouncer transaction mode and session mode? Which can't you use with PostgreSQL advisory locks?"

---

## 📅 DAY 63 — Object Storage with MinIO

### 🌅 Morning Block (1 hr)
- 📖 Study: Object storage vs block storage vs file storage
- 📖 Study: S3 API — the de-facto standard, how MinIO implements it
- 📖 Study: Presigned URLs — time-limited access, server-side generation, why they're secure

### 🛠️ Afternoon Block (3 hrs)
- 🛠️ Run MinIO with Docker: `docker run -p 9000:9000 -p 9001:9001 minio/minio server /data`
- 🛠️ Access MinIO console at localhost:9001, create a bucket
- 🛠️ Build a file upload service in FastAPI:
  - `POST /upload` → accepts file, stores in MinIO, returns object URL
  - `GET /file/{filename}` → generates presigned URL (expires in 1 hour)
  - `DELETE /file/{filename}` → deletes from MinIO
- 🛠️ Add upload size limits and file type validation
- 🛠️ Record a Loom demo video of the upload/download flow

### 📝 Evening Block (1 hr)
- 📝 Commit: FastAPI file service code, MinIO Docker setup, README with demo video link
- 🔁 Recall: "Why is object storage better than storing files on a local disk in a distributed system?"

---

## 📅 DAY 64–70 — Phase 3 Projects & Checkpoint

### DAY 64 — E-Commerce Schema Optimization
- 🛠️ Add 5M rows to your e-commerce DB using batch inserts
- 🛠️ Identify the top 5 slowest queries with `pg_stat_statements`
- 🛠️ Optimize each with indexes, query rewrites, or materialized views
- 📝 Document before/after with EXPLAIN ANALYZE

### DAY 65 — Redis Leaderboard + Pub/Sub
- 🛠️ Build a real-time leaderboard: players earn points, leaderboard updates live
- 🛠️ Add Redis Pub/Sub: when leaderboard changes, publish event → WebSocket server broadcasts to all connected clients
- 📝 Commit with architecture diagram

### DAY 66 — Full-Stack Database Layer for E-Commerce
- 🛠️ Wire your e-commerce PostgreSQL schema to your FastAPI app
- 🛠️ Add SQLAlchemy ORM models for all tables
- 🛠️ Add Redis caching for product listings
- 🛠️ Add rate limiting on all public endpoints
- 📝 Commit with full API documentation

### DAY 67 — Database Migration Strategy
- 📖 Study: Alembic (Python migration tool), zero-downtime migrations, expand-contract pattern
- 🛠️ Set up Alembic for your e-commerce project
- 🛠️ Practice: add a column → migrate → backfill data → make column NOT NULL (3-step zero-downtime migration)
- 📝 Commit migration files and document the zero-downtime strategy

### DAY 68 — Elasticsearch / Full-Text Search
- 🛠️ Run Elasticsearch or Meilisearch with Docker
- 🛠️ Index your product catalog
- 🛠️ Add a `GET /search?q=...` endpoint using fuzzy full-text search
- 📝 Commit and document

### DAY 69 — Database Documentation & Architecture Writeup
- 📝 Write a comprehensive README for your `postgres-projects` repository:
  - Schema diagram (dbdiagram.io link + screenshot)
  - Index strategy explanation
  - Query optimization examples
  - Benchmark results

### DAY 70 — Phase 3 Checkpoint
- ✅ Checklist:
  - [ ] E-commerce schema with 1M+ rows and optimized indexes
  - [ ] Library Management System with stored procedures
  - [ ] EXPLAIN ANALYZE before/after index optimization
  - [ ] Redis caching layer with hit rate logging
  - [ ] Redis rate limiter (3 algorithms implemented)
  - [ ] Redis leaderboard with Pub/Sub
  - [ ] PostgreSQL streaming replication setup
  - [ ] PgBouncer connection pooling benchmark
  - [ ] File upload service with MinIO
  - [ ] Full-text search with Elasticsearch/Meilisearch
  - [ ] Alembic database migrations

---

---

# 🟠 PHASE 4: Backend Engineering (Days 71–119)

---

## 📅 DAY 71 — Authentication: JWT, Sessions & OAuth

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: JWT structure in depth — header.payload.signature, base64url encoding, signing algorithms (HS256 vs RS256)
- 📖 Study: Access tokens vs refresh tokens — expiry, rotation strategy
- 📖 Study: OAuth 2.0 flows — Authorization Code, Client Credentials, PKCE
- 📖 Study: JWT vulnerabilities — algorithm confusion attack (`alg: none`), expired token acceptance, short-lived tokens
- 📖 Study: Session-based auth vs JWT — when to use each

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Build auth system in FastAPI:
  - `POST /register` — email, password (bcrypt hashed, cost factor 12)
  - `POST /login` — validate, return access JWT (15min) + refresh JWT (7days, stored in HttpOnly cookie)
  - `POST /refresh` — validate refresh token, issue new access token
  - `POST /logout` — add refresh token to Redis blacklist
  - Protected endpoint requiring valid JWT
- 🛠️ Test: manual JWT tampering → should be rejected

### 📝 Evening Block (1 hr)
- 📝 Commit: full auth service code, security documentation
- 🔁 Recall: "What is the `alg: none` JWT attack? How do you prevent it?"

---

## 📅 DAY 72 — RBAC, Permissions & API Security

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: RBAC (Role-Based Access Control) — roles, permissions, role-permission mapping
- 📖 Study: ABAC (Attribute-Based Access Control) — more granular, policy-based
- 📖 Study: API security checklist: input validation, output encoding, SQL injection prevention, CORS policy
- 📖 Study: OWASP API Security Top 10 — know the categories

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Add RBAC to your auth service:
  - Roles: admin, manager, user
  - Permissions: read:users, write:users, delete:users, read:orders, etc.
  - Middleware decorator: `@require_permission("write:users")`
- 🛠️ Test: user tries admin endpoint → 403 Forbidden
- 🛠️ Add input validation with Pydantic models (length limits, regex validation, type coercion)

### 📝 Evening Block (1 hr)
- 📝 Commit: RBAC implementation, security documentation including OWASP mitigations
- 🔁 Recall: "What is CORS? Why does it exist? When would you set `Access-Control-Allow-Origin: *` and when is that dangerous?"

---

## 📅 DAY 73 — API Design: Versioning, Pagination & Error Handling

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: API versioning — URL versioning (`/v1/`), header versioning, semantic versioning of APIs
- 📖 Study: Pagination — offset-based (simple, but slow at high offsets), cursor-based (efficient), page-based
- 📖 Study: Consistent error response format — error code, message, details, request_id
- 📖 Study: Idempotency — why `POST /payments` must be idempotent (Idempotency-Key header)
- 📖 Study: Rate limit response headers — `X-RateLimit-Limit`, `X-RateLimit-Remaining`, `Retry-After`

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Implement cursor-based pagination on `GET /products`:
  - Client sends `?cursor=LAST_SEEN_ID&limit=20`
  - Server returns items + next cursor
  - Benchmark vs offset pagination at deep pages (1M+ rows)
- 🛠️ Implement idempotency for a payment endpoint:
  - Client sends `Idempotency-Key: uuid` header
  - Server checks Redis for this key — if found, return cached response
  - If not, process and cache result with key
- 🛠️ Standardize error responses across all endpoints

### 📝 Evening Block (1 hr)
- 📝 Commit: pagination implementation, idempotency middleware, error format documentation
- 🔁 Recall: "Why does offset pagination perform poorly at high page numbers? What SQL does it generate?"

---

## 📅 DAY 74–75 — Build: Production-Grade Auth Service (Complete)

### DAY 74 — Auth Service Core
- 🛠️ Complete the auth service with all features:
  - Registration with email verification (generate token, send email via SMTP)
  - Login with brute force protection (Redis: track failed attempts, lockout after 5 failures)
  - Password reset flow (email → token → reset form → new password)
  - JWT access + refresh token rotation
  - RBAC middleware
  - Rate limiting on all auth endpoints

### DAY 75 — Auth Service Testing & Docs
- 🛠️ Write tests with pytest:
  - Unit tests: password hashing, JWT generation/validation
  - Integration tests: full registration → login → access protected endpoint flow
  - Security tests: test that tampered JWT is rejected, test that expired token is rejected
- 🛠️ Complete OpenAPI documentation with examples for every endpoint
- 📝 Commit: full auth service, test suite, Postman collection, API docs

---

## 📅 DAY 76 — Apache Kafka: Architecture & Setup

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Kafka architecture — brokers, topics, partitions, consumer groups, offsets, ZooKeeper vs KRaft
- 📖 Study: Log anatomy — segment files, index files, time-based and size-based retention
- 📖 Study: Producer configurations: `acks` (0, 1, all), `retries`, `linger.ms`, `batch.size`
- 📖 Study: Consumer configurations: `auto.offset.reset`, `enable.auto.commit`, `max.poll.records`
- 📖 Study: Consumer group rebalancing — what triggers it, partition assignment strategies

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Run Kafka with Docker Compose (include Zookeeper or use KRaft mode, include Kafka UI)
- 🛠️ Use `kafka-topics.sh` to: create topic, list topics, describe topic (partitions, replicas)
- 🛠️ Use `kafka-console-producer.sh` and `kafka-console-consumer.sh` to send/receive messages
- 🛠️ Create a topic with 3 partitions — observe how messages distribute

### 📝 Evening Block (1 hr)
- 📝 Commit: Docker Compose file, kafka-topics commands and output, Kafka UI screenshot
- 🔁 Recall: "What happens to a Kafka consumer's messages if it goes offline for 3 hours? What controls how long messages are retained?"

---

## 📅 DAY 77 — Kafka: Python Producer & Consumer

### 🌅 Morning Block (1 hr)
- 📖 Study: `confluent-kafka` Python library — producer and consumer APIs
- 📖 Study: Delivery reports — how producers confirm messages were received by broker
- 📖 Study: Exactly-once semantics — idempotent producer, transactional producer

### 🛠️ Afternoon Block (3 hrs)
- 🛠️ Build a Python Kafka producer:
  - Sends 10,000 order events to `orders` topic
  - Each event: `{order_id, user_id, product_id, quantity, timestamp}`
  - Uses `acks=all` for safety
  - Logs delivery confirmation for each message
- 🛠️ Build a Python Kafka consumer:
  - Consumer group: `inventory-service`
  - Reads from `orders`, prints each message
  - Commits offsets manually (not auto-commit)
- 🛠️ Test: start consumer, then producer — watch events flow
- 🛠️ Test: stop consumer mid-way, restart — verify it resumes from where it left off (offset management)

### 📝 Evening Block (1 hr)
- 📝 Commit: producer code, consumer code, test run output
- 🔁 Recall: "What is the difference between at-most-once, at-least-once, and exactly-once delivery?"

---

## 📅 DAY 78 — Build: Order Processing Pipeline with Kafka

### 🌅 Morning Block (1 hr)
- 📖 Plan: Design the event-driven order processing architecture:
  - Order API → `orders` topic → Inventory Service → `inventory-updated` topic → Notification Service
  - Dead letter queue for failed messages

### 🛠️ Afternoon Block (3 hrs)
- 🛠️ Implement 3 microservices:
  1. **Order API** (FastAPI): `POST /orders` → validates, publishes to `orders` topic, returns order_id
  2. **Inventory Service** (Python Kafka consumer): reads `orders`, checks stock in Redis/PostgreSQL, publishes to `inventory-updated` or `orders-failed`
  3. **Notification Service** (Python Kafka consumer): reads `inventory-updated`, sends email confirmation via SMTP
- 🛠️ Implement dead letter queue: messages that fail 3 times go to `orders-dlq` topic
- 🛠️ Run all 3 services + Kafka + PostgreSQL + Redis with Docker Compose

### 📝 Evening Block (1 hr)
- 📝 Commit: all 3 service codebases, Docker Compose, architecture diagram showing event flow
- 🔁 Recall: "In this pipeline, if the Notification Service fails, does the customer order still complete? Why?"

---

## 📅 DAY 79 — Microservices vs Monolith Decision

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Monolith advantages — simpler deployment, no network latency, ACID transactions across features, easier debugging
- 📖 Study: Microservices advantages — independent deployment, technology diversity, team autonomy, independent scaling
- 📖 Study: Microservices costs — network calls (latency, failure), distributed transactions, data consistency challenges, operational complexity
- 📖 Study: Strangler Fig pattern — gradually migrating monolith to microservices
- 📖 Study: Domain-Driven Design (DDD) basics — bounded contexts, aggregates, domain events

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Refactor your e-commerce monolith:
  - Current: all routes in one FastAPI app
  - Extract: User Service (separate FastAPI app on port 8001)
  - Extract: Product Service (separate FastAPI app on port 8002)
  - Keep: Order Service integrated with both via HTTP calls for now
- 🛠️ Document what broke and how you fixed it (inter-service auth, shared models, etc.)

### 📝 Evening Block (1 hr)
- 📝 Commit: before/after architecture comparison document + code
- 🔁 Recall: "What is a distributed monolith? Why is it worse than either a monolith or proper microservices?"

---

## 📅 DAY 80 — API Gateway & Service Discovery

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: API Gateway responsibilities — routing, auth, rate limiting, SSL termination, request logging
- 📖 Study: Service discovery — how services find each other's IPs/ports
  - Client-side: service asks registry (Consul, Eureka), then calls directly
  - Server-side: request goes to load balancer, it queries registry
- 📖 Study: NGINX as an API gateway — location blocks for routing

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Configure NGINX as API Gateway for your 3 microservices:
  - `/api/v1/users/` → User Service (port 8001)
  - `/api/v1/products/` → Product Service (port 8002)
  - `/api/v1/orders/` → Order Service (port 8003)
  - Add JWT validation at gateway level (NGINX + Lua, or a small auth middleware service)
  - Add rate limiting at gateway level
  - Add request ID header generation

### 📝 Evening Block (1 hr)
- 📝 Commit: NGINX API Gateway config with full comments, architecture diagram
- 🔁 Recall: "Should you validate JWT at the API gateway or in each individual service? Argue both sides."

---

## 📅 DAY 81 — Circuit Breaker & Retry Patterns

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Cascading failures — how one slow service can bring down all services that depend on it
- 📖 Study: Circuit breaker pattern — Closed (normal), Open (failing, reject requests), Half-Open (testing recovery)
- 📖 Study: Retry with exponential backoff — `wait = base_delay * 2^attempt + jitter`
- 📖 Study: Timeout strategy — always set timeouts on inter-service HTTP calls
- 📖 Study: Bulkhead pattern — isolate failures in separate thread pools

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Implement circuit breaker in Python from scratch:
  - Track success/failure counts in a sliding window
  - Open circuit after 5 consecutive failures
  - Half-open: allow one request after 30 seconds
  - Close if the test request succeeds
- 🛠️ Test: deliberately make Product Service fail → observe Order Service circuit open → stop cascading

### 📝 Evening Block (1 hr)
- 📝 Commit: circuit breaker implementation, test demonstrating it working
- 🔁 Recall: "What is the difference between a circuit breaker and retry? Can you use both?"

---

## 📅 DAY 82 — Saga Pattern: Distributed Transactions

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Why distributed transactions are hard — 2PC (Two-Phase Commit), its failure modes
- 📖 Study: Saga pattern — sequence of local transactions with compensating transactions for rollback
- 📖 Study: Choreography vs Orchestration:
  - Choreography: services react to events (decentralized)
  - Orchestration: central saga orchestrator coordinates steps

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Implement an order placement saga (choreography style):
  - Step 1: Order Service creates order (status: PENDING), publishes `order-created` event
  - Step 2: Inventory Service reserves stock, publishes `stock-reserved` or `stock-failed`
  - Step 3: Payment Service charges card, publishes `payment-processed` or `payment-failed`
  - Compensating: on `payment-failed`, Inventory Service releases reserved stock
- 🛠️ Test the failure path: payment fails → stock is released → order marked failed

### 📝 Evening Block (1 hr)
- 📝 Commit: saga implementation, state machine diagram for order status, failure test
- 🔁 Recall: "What is a compensating transaction? Give an example from a real e-commerce scenario."

---

## 📅 DAY 83–84 — Phase 4 Integration & Checkpoint

### DAY 83 — E-Commerce Platform: Full Integration
- 🛠️ Bring everything together:
  - NGINX API Gateway → 3 microservices
  - Auth service with JWT (all services validate JWT)
  - PostgreSQL per service (separate schemas or databases)
  - Redis for caching and rate limiting
  - Kafka for order processing events
  - MinIO for product images
  - All running with Docker Compose

### DAY 84 — Phase 4 Checkpoint
- ✅ Checklist:
  - [ ] Auth service: registration, login, JWT, RBAC, refresh tokens
  - [ ] Cursor-based pagination implemented
  - [ ] Idempotency middleware on payment endpoints
  - [ ] Kafka order processing pipeline (3 services)
  - [ ] Microservices extracted from monolith
  - [ ] NGINX API gateway with routing and rate limiting
  - [ ] Circuit breaker implemented and tested
  - [ ] Saga pattern for distributed transactions
  - [ ] Full Docker Compose for all services

---

---

# 🔴 PHASE 5: System Design (Days 85–161)

---

## 📅 DAY 85 — System Design Interview Framework

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: The structured approach for system design interviews:
  1. **Clarify requirements** (5 min): Functional (what does it do?) + Non-functional (scale, latency, availability)
  2. **Back-of-envelope estimation** (5 min): Users, DAU, RPS, storage, bandwidth
  3. **High-level design** (10 min): Major components, APIs, data flow
  4. **Deep dive** (15 min): The hardest components, focus where interviewer probes
  5. **Identify bottlenecks & scale** (5 min): Where does it break? How do you fix it?
- 📖 Study: Estimation techniques — know these by heart: 100K RPS is 1B requests/day, 1B users × 1KB data = 1TB

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Practice estimation: given "Design Twitter for 300M users", compute:
  - DAU (assume 20% → 60M active/day)
  - Tweets per day (assume each user tweets 0.1 times/day → 6M tweets/day)
  - Reads per day (100:1 read:write → 600M reads/day → ~7,000 RPS)
  - Storage: 140 chars × 4 bytes = 560 bytes × 6M = 3.36GB/day
  - Bandwidth for reads: 7,000 RPS × 560 bytes = ~4MB/s (trivial)
- 🛠️ Write up the estimation in a template document

### 📝 Evening Block (1 hr)
- 📝 Create template: `system-design-template.md` in your GitHub
- 🔁 Recall: "A video streaming service has 100M users, each watches 30 min/day at 5Mbps quality. What's the bandwidth requirement?"

---

## 📅 DAY 86 — Design: URL Shortener (bit.ly)

### 🌅 Morning Block (1.5 hrs)
- 📖 Think through the problem completely before reading any solutions
- 📖 Identify key challenges: unique ID generation, 301 vs 302 redirect, analytics tracking, custom aliases, URL expiry

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Write complete `ARCHITECTURE.md` for URL shortener:
  - Requirements (functional + non-functional)
  - Estimation (1000 writes/day, 100K reads/day → 100:1 ratio)
  - API design: `POST /shorten`, `GET /{code}` → 302 redirect
  - Database schema
  - Component diagram
  - Deep dive: ID generation — Base62 encoding, collision avoidance, auto-increment vs random
  - Caching: cache popular redirects in Redis (cache-aside, LRU)
  - Analytics: async click tracking via Kafka
  - Scaling: read replicas, CDN for redirects

### 📝 Evening Block (1 hr)
- 🛠️ Implement the URL shortener fully in Python + PostgreSQL + Redis
- 📝 Commit: architecture doc + full implementation
- 🔁 Recall: "Should the redirect be 301 (permanent) or 302 (temporary)? What are the caching implications?"

---

## 📅 DAY 87 — Design: Rate Limiter Service

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Design a distributed rate limiter service — all servers must share state
- 📖 Think: where does the rate limiter live? API Gateway? Middleware? Separate service?
- 📖 Think: how to handle race conditions when multiple servers check limits simultaneously (Redis Lua scripts)

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Write `ARCHITECTURE.md` for a standalone rate limiter service
- 🛠️ Implement: a distributed rate limiter that multiple API servers can call
  - Redis backend for shared state
  - Sliding window algorithm
  - gRPC interface (so API servers can check rate limit without HTTP overhead)

### 📝 Evening Block (1 hr)
- 📝 Commit: architecture doc + distributed rate limiter implementation
- 🔁 Recall: "If you have 10 API servers and a rate limit of 100 req/sec per user, how do you enforce it globally?"

---

## 📅 DAY 88 — Design: Key-Value Store (like Redis/DynamoDB)

### 🌅 Morning Block (1.5 hrs)
- 📖 Design a simple distributed key-value store from first principles
- 📖 Think through: data partitioning, replication, consistency, failure handling
- 📖 Study: Consistent hashing in detail — virtual nodes, ring topology

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Implement consistent hashing in Python:
  - N virtual nodes per server
  - add_server(), remove_server(), get_server(key)
  - Observe: adding one server only moves ~1/N of the data
- 🛠️ Write `ARCHITECTURE.md` for a distributed KV store

### 📝 Evening Block (1 hr)
- 📝 Commit: consistent hashing implementation with tests, architecture document
- 🔁 Recall: "Why do we use virtual nodes in consistent hashing? What problem do they solve?"

---

## 📅 DAY 89–91 — Design: Twitter/X Feed

### DAY 89 — Fan-Out Architecture
- 📖 Study: Fan-out on write vs fan-out on read — the fundamental Twitter challenge
- 📖 Study: Hybrid approach: fan-out on write for normal users, fan-out on read for celebrities
- 🛠️ Write complete `ARCHITECTURE.md` for Twitter-like system

### DAY 90 — Implementation: Post Service + Fan-Out
- 🛠️ Build Post Service: create post, fetch home timeline
- 🛠️ Implement fan-out on write: when post is created → Redis Pub/Sub → followers' feed updated
- 🛠️ Test with 100 followers — verify feed update

### DAY 91 — Deep Dive + Documentation
- 🛠️ Identify the celebrity problem: user with 10K followers posting → 10K Redis writes
- 🛠️ Implement hybrid: users with < 1000 followers: fan-out on write; > 1000: fan-out on read
- 📝 Commit: full implementation, architecture decision document explaining the hybrid approach

---

## 📅 DAY 92–95 — Design: Ride-Sharing (Uber-like)

### DAY 92 — Geospatial Architecture
- 📖 Study: Geohashing — encoding lat/lng into a string prefix, nearby search using prefix matching
- 📖 Study: Quadtrees — alternative to geohashing, used by some mapping services
- 📖 Study: Redis GEO commands — `GEOADD`, `GEORADIUS`
- 🛠️ Implement: find nearby drivers using Redis GEO

### DAY 93 — Real-Time Location & Matching
- 🛠️ Build driver location service: driver sends location via WebSocket every 5 seconds
- 🛠️ Build matching service: when ride requested, find nearest available driver

### DAY 94 — Pricing & Surge
- 📖 Study: Surge pricing algorithm — supply vs demand ratio in geographic zone
- 🛠️ Write `ARCHITECTURE.md` for complete ride-sharing system

### DAY 95 — Documentation
- 📝 Commit all code, architecture document, decision records

---

## 📅 DAY 96–100 — Design: YouTube/Video Streaming

### DAY 96–97 — Video Processing Pipeline
- 📖 Study: Video transcoding — why multiple formats/resolutions (adaptive bitrate streaming, HLS)
- 🛠️ Write `ARCHITECTURE.md` for video streaming platform
- 🛠️ Set up a minimal video transcoding pipeline using `ffmpeg` and a job queue (Celery + Redis)

### DAY 98–99 — CDN & Delivery
- 📖 Study: Adaptive bitrate streaming (HLS/DASH) — how Netflix/YouTube serve video
- 🛠️ Serve a video using HLS from NGINX — segment the video with ffmpeg, serve playlist file
- 📝 Document the full video delivery architecture

### DAY 100 — Milestone Checkpoint
- ✅ 100 days completed! Do a complete review of everything built
- 📝 Write a "100 days of learning" retrospective document
- 🛠️ Update GitHub profile README with progress

---

## 📅 DAY 101–119 — Design: Chat, Design Principles & Scalability

### DAY 101–104 — Design: Chat System (WhatsApp)
- 📖 Study: Message ordering guarantees, delivery acknowledgments (sent/delivered/read receipts)
- 📖 Study: Online presence — how to track user online status at scale
- 🛠️ Build: WebSocket-based chat with rooms, message persistence in PostgreSQL
- 🛠️ Scale: add Redis Pub/Sub to support multi-server WebSocket routing
- 📝 Architecture document with delivery guarantee explanation

### DAY 105–108 — Scalability Patterns Deep Dive
- **DAY 105**: Implement consistent hashing for a distributed cache simulation
- **DAY 106**: Build all 4 rate limiting algorithms and compare
- **DAY 107**: Implement a simple CDN simulation — proxy server with caching
- **DAY 108**: Build a service health check and failover system

### DAY 109–112 — Reliability Engineering
- **DAY 109**: Exponential backoff + jitter implementation and unit tests
- **DAY 110**: Write availability calculation for your e-commerce platform (identify SPOFs)
- **DAY 111**: Build a simple chaos engineering tool (randomly kill services, measure recovery time)
- **DAY 112**: Write runbooks for top 5 failure scenarios in your system

### DAY 113–116 — System Design Practice (Mock Interviews)
- **DAY 113**: Design a Notification System (email + push + SMS) — 30-minute timed exercise
- **DAY 114**: Design a Search Autocomplete system — 30-minute timed exercise
- **DAY 115**: Design a Web Crawler — 30-minute timed exercise
- **DAY 116**: Record yourself doing a 30-minute system design (Loom) — watch it back critically

### DAY 117–119 — Phase 5 Documentation & Checkpoint
- **DAY 117**: Finalize all architecture documents — ensure each follows the template
- **DAY 118**: Create a "system designs" section on your GitHub with index of all designs
- **DAY 119**: Phase 5 checkpoint — all architecture docs reviewed, all implementations committed

---

---

# ⚫ PHASE 6: Production, DevOps & Cloud (Days 120–210)

---

## 📅 DAY 120 — Docker: Fundamentals & Architecture

### 🌅 Morning Block (1.5 hrs)
- 📖 Study: Docker architecture — daemon, client, images, containers, registry
- 📖 Study: Linux namespaces (PID, network, mount, IPC, UTS) — container isolation
- 📖 Study: cgroups — resource limits (CPU, memory, I/O, network)
- 📖 Study: Dockerfile best practices — layer caching, .dockerignore, non-root user
- 📖 Study: Multi-stage builds — compile in one stage, minimal runtime in next

### 🛠️ Afternoon Block (2 hrs)
- 🛠️ Write a production Dockerfile for your FastAPI auth service:
  - Multi-stage: builder (pip install) → runtime (minimal image)
  - Non-root user
  - Health check instruction
  - Minimize image size (compare with and without multi-stage)
- 🛠️ Build and run: `docker build -t auth-service:v1 .`
- 🛠️ Test: `docker exec -it container_id /bin/sh` — explore inside

### 📝 Evening Block (1 hr)
- 📝 Commit: Dockerfile with comments, `.dockerignore`, image size before vs after optimization table
- 🔁 Recall: "What is the difference between a container and a VM? What makes containers faster to start?"

---

## 📅 DAY 121 — Docker Compose: Full Stack Orchestration

### 🌅 Morning Block (1 hr)
- 📖 Study: Docker Compose — service definitions, networking, volumes, depends_on, health checks
- 📖 Study: Environment variable injection in Compose — `.env` file, `env_file`, `environment` key

### 🛠️ Afternoon Block (3 hrs)
- 🛠️ Write a complete `docker-compose.yml` for your e-commerce platform:
  - `nginx` (API gateway)
  - `user-service` (FastAPI)
  - `product-service` (FastAPI)
  - `order-service` (FastAPI)
  - `postgres` (database)
  - `redis` (cache)
  - `kafka` + `zookeeper` (message broker)
  - `minio` (object storage)
  - All on the same Docker network
  - Health checks for each service
  - Volume mounts for PostgreSQL and MinIO data persistence
- 🛠️ Test: `docker compose up -d` — all services start and are healthy
- 🛠️ Test: `docker compose down` and `docker compose up` — data persists

### 📝 Evening Block (1 hr)
- 📝 Commit: `docker-compose.yml`, `.env.example`
- 📝 Update main README: "Start entire platform with: `docker compose up -d`"
- 🔁 Recall: "What is the difference between `docker compose up` and `docker compose up --build`?"

---

## 📅 DAY 122–125 — GitHub Actions CI/CD Pipeline

### DAY 122 — CI: Lint + Test
- 📖 Study: GitHub Actions syntax — workflows, jobs, steps, triggers, runners
- 🛠️ Create `.github/workflows/ci.yml`:
  - Trigger: on push to any branch, on PR to main
  - Jobs: lint (ruff), unit tests (pytest), integration tests (pytest with Docker services)
  - Use `services:` block to spin up PostgreSQL + Redis in CI
- 📝 Commit, see green/red CI status on GitHub

### DAY 123 — CI: Docker Build + Security Scan
- 🛠️ Add to CI pipeline:
  - Build Docker image
  - Push to GitHub Container Registry (GHCR)
  - Run `trivy` vulnerability scanner on the image
  - Run `bandit` for Python security linting
- 📝 Add CI badge to README

### DAY 124 — CD: Automated Deployment
- 🛠️ Deploy to Render.com or Railway.app (free tier):
  - Set up deployment via GitHub Actions on merge to `main`
  - Use secrets in GitHub Actions for deployment keys
  - Add smoke test: curl the health endpoint after deployment

### DAY 125 — Blue-Green Deployment Strategy
- 📖 Study: Blue-green deployment, canary releases, rolling updates — definitions and tradeoffs
- 🛠️ Simulate blue-green with NGINX: two identical backends, switch NGINX upstream atomically
- 📝 Commit: deployment strategy documentation, CI/CD pipeline YAML files

---

## 📅 DAY 126–130 — Kubernetes Fundamentals

### DAY 126 — Kubernetes Architecture & Concepts
- 📖 Study: Control plane (API Server, etcd, Scheduler, Controller Manager) + Worker nodes (kubelet, kube-proxy, container runtime)
- 📖 Study: Core objects: Pod, Deployment, Service, Ingress, ConfigMap, Secret
- 🛠️ Install minikube: `minikube start`
- 🛠️ Explore: `kubectl get all --all-namespaces`

### DAY 127 — Deploy to Kubernetes
- 🛠️ Write Kubernetes Deployment YAML for auth service:
  - 2 replicas
  - Resource requests and limits (CPU: 100m/500m, Memory: 128Mi/256Mi)
  - Liveness probe + readiness probe
- 🛠️ Write Service YAML (ClusterIP type)
- 🛠️ Deploy: `kubectl apply -f deployment.yml`
- 🛠️ Test rolling update: change image tag, apply → watch pods restart one-by-one

### DAY 128 — Ingress & ConfigMaps
- 🛠️ Install NGINX Ingress Controller in minikube
- 🛠️ Write Ingress YAML: route `/api/users` to user-service, `/api/products` to product-service
- 🛠️ Create ConfigMap for application configuration (non-secret values)
- 🛠️ Create Secret for database credentials (base64 encoded, mounted as env vars)

### DAY 129 — Horizontal Pod Autoscaler (HPA)
- 🛠️ Install metrics-server in minikube
- 🛠️ Create HPA: scale auth-service between 1 and 10 replicas based on CPU > 50%
- 🛠️ Load test with locust → watch pods auto-scale up → stop test → watch scale down

### DAY 130 — Kubernetes Checkpoint
- 📝 Commit: all YAML manifests, architecture diagram of K8s topology
- ✅ All services deployed to minikube with HPA

---

## 📅 DAY 131–140 — Observability: Prometheus + Grafana + Loki

### DAY 131 — Prometheus Fundamentals
- 📖 Study: Pull-based metrics, data model (metric_name{label=value} value timestamp), metric types (Counter, Gauge, Histogram, Summary)
- 🛠️ Instrument FastAPI with prometheus-fastapi-instrumentator: auto-generates request count, duration, in-progress
- 🛠️ Run Prometheus in Docker: scrape your FastAPI `/metrics` endpoint
- 🛠️ Query in Prometheus UI: `rate(http_requests_total[5m])`

### DAY 132 — Custom Metrics
- 🛠️ Add custom application metrics:
  - `auth_logins_total` counter (label: success/failure)
  - `active_users_gauge` (track logged-in users)
  - `order_processing_duration_histogram`
  - `cache_hits_total` vs `cache_misses_total`
- 📝 Commit: instrumented FastAPI code

### DAY 133 — Grafana Dashboards
- 🛠️ Add Grafana to Docker Compose, connect to Prometheus
- 🛠️ Build RED dashboard (one panel per metric):
  - Rate: `rate(http_requests_total[1m])`
  - Errors: `rate(http_requests_total{status=~"5.."}[1m])`
  - Duration: `histogram_quantile(0.99, rate(http_request_duration_seconds_bucket[5m]))`
- 🛠️ Add business metrics panels: logins/min, orders/min, cache hit rate

### DAY 134 — Load Test + Dashboard Demo
- 🛠️ Run locust for 10 minutes with 50 virtual users
- 🛠️ Screenshot Grafana dashboard during the load test — this is your portfolio screenshot
- 🛠️ Export Grafana dashboard as JSON, commit to GitHub

### DAY 135 — Prometheus Alerting
- 🛠️ Write alerting rules:
  - Alert if error rate > 5% for 2 minutes
  - Alert if p99 latency > 500ms for 5 minutes
  - Alert if auth service is down (up == 0)
- 🛠️ Connect Alertmanager to send to email (or webhook)

### DAY 136 — Loki: Log Aggregation
- 📖 Study: Loki architecture — push-based, labels, LogQL query language
- 🛠️ Add Loki + Promtail to Docker Compose
- 🛠️ Configure Promtail to collect logs from all your containers
- 🛠️ Query logs in Grafana: `{service="auth-service"} |= "ERROR"`

### DAY 137 — Distributed Tracing with Jaeger
- 📖 Study: Distributed tracing — trace ID, spans, parent-child relationships
- 🛠️ Add OpenTelemetry instrumentation to FastAPI
- 🛠️ Run Jaeger in Docker
- 🛠️ Make a request → find the full trace in Jaeger UI (see time spent in each service)

### DAY 138 — Build Full Observability Stack
- 🛠️ Complete `docker-compose.observability.yml`:
  - Prometheus + Alertmanager
  - Grafana (with pre-provisioned dashboards)
  - Loki + Promtail
  - Jaeger
- 📝 Commit with full setup guide

### DAY 139 — Observability Documentation
- 📝 Write: "My Observability Stack" guide — architecture diagram, what each tool does, how they connect
- 📝 Commit dashboard JSON, alert rules YAML, all documentation

### DAY 140 — Phase 6 Mid-Checkpoint
- ✅ Docker multi-stage builds optimized
- ✅ Full CI/CD pipeline with lint/test/build/deploy
- ✅ Kubernetes deployment with HPA
- ✅ Prometheus + Grafana with RED metrics
- ✅ Load test screenshots in Grafana
- ✅ Loki log aggregation
- ✅ Distributed tracing with Jaeger

---

## 📅 DAY 141–160 — Capstone Project: Social Platform Backend

### DAY 141–143 — Architecture & Setup
- 📖 Design the full architecture (6+ services)
- 🛠️ Create GitHub organization for the capstone
- 🛠️ Set up each service repository with CI pipeline

### DAY 144–148 — Core Services Implementation
- **DAY 144**: User Service (registration, login, JWT, profiles)
- **DAY 145**: Post Service (create/read posts, timelines)
- **DAY 146**: Media Service (image upload via MinIO, presigned URLs)
- **DAY 147**: Search Service (Meilisearch full-text search of posts and users)
- **DAY 148**: API Gateway (NGINX routing to all services)

### DAY 149–152 — Event-Driven Features
- **DAY 149**: Kafka integration — post created events
- **DAY 150**: Notification Service — Kafka consumer → email notifications
- **DAY 151**: Feed Service — fan-out on write for timelines using Redis + Kafka
- **DAY 152**: Analytics Service — event tracking, view counts using Redis HyperLogLog

### DAY 153–156 — Infrastructure Layer
- **DAY 153**: Docker Compose for local development (all services)
- **DAY 154**: Kubernetes manifests for all services
- **DAY 155**: CI/CD pipelines for each service (GitHub Actions)
- **DAY 156**: Observability stack (Prometheus + Grafana + Loki + Jaeger) for all services

### DAY 157–158 — Load Testing & Performance
- 🛠️ Write comprehensive Locust test: realistic user flows (register → post → view feed → search)
- 🛠️ Run: 200 virtual users, 30-minute test
- 🛠️ Screenshot Grafana during test — save as portfolio evidence
- 🛠️ Find and fix at least 2 performance bottlenecks discovered during load test

### DAY 159 — Documentation Sprint
- 📝 Write `ARCHITECTURE.md` for the full system
- 📝 Create portfolio website (GitHub Pages): project page with architecture diagram + live demo link
- 📝 Write blog series: 3 articles on Hashnode about the system

### DAY 160 — Capstone Demo Recording
- 🛠️ Record: 15-minute architecture walkthrough (Loom or YouTube unlisted)
  - Show the architecture diagram
  - Demonstrate: post a message → notification appears → search for it
  - Show Grafana dashboard with real metrics
  - Show Jaeger trace for a request
- 📝 Link video in GitHub README and portfolio website

---

## 📅 DAY 161–175 — System Design Interview Prep

### DAY 161–165 — Daily Design Practice
- **DAY 161**: Design a Notification System (30 min timed, then self-review)
- **DAY 162**: Design Dropbox/Google Drive (30 min timed, then self-review)
- **DAY 163**: Design a Distributed Message Queue like Kafka (30 min timed)
- **DAY 164**: Design a Search Engine (30 min timed)
- **DAY 165**: Design Netflix (30 min timed)

### DAY 166–170 — Mock Interview Recording
- 🛠️ Record yourself solving a system design problem (no notes, timed at 45 min)
- 🛠️ Watch the recording critically — assess: communication, structure, completeness
- 🛠️ Focus areas: estimation, depth on the hardest component, tradeoff discussion

### DAY 171–175 — Weak Areas Reinforcement
- 📖 Identify the 3 system design areas where you're weakest (from self-review)
- 📖 Deep dive into each — read, research, redesign

---

## 📅 DAY 176–195 — Portfolio & Visibility Sprint

### DAY 176–180 — GitHub Polish
- 🛠️ Ensure every repo has: proper README, CI badge, architecture diagram, one-command Docker startup
- 🛠️ Pin 6 best repositories on GitHub profile
- 🛠️ GitHub profile README: update with all completed projects

### DAY 181–185 — Technical Writing
- 📝 Publish 3 articles on Hashnode (one per major project):
  1. "How I built a distributed order processing system with Kafka"
  2. "Building a production-grade observability stack from scratch"
  3. "System design: How I designed and implemented a Twitter-like feed"

### DAY 186–190 — Portfolio Website
- 🛠️ Build a portfolio website with GitHub Pages:
  - Projects section with architecture diagrams
  - Blog section linking to Hashnode articles
  - Skills section
  - Contact

### DAY 191–195 — Professional Network
- 🛠️ Post 3 LinkedIn technical posts (architecture diagram + explanation)
- 🛠️ Share to relevant communities: Hacker News, Dev.to, relevant Discord servers
- 🛠️ Submit to "Show HN" on Hacker News

---

## 📅 DAY 196–210 — Final Review & Interview Preparation

### DAY 196–200 — Complete Roadmap Review
- Review Phase 0–6 notes systematically
- Attempt every active recall question cold (from memory)
- Identify remaining gaps

### DAY 201–205 — Interview Practice
- **DAY 201**: System design interview (self-recorded, 45 min)
- **DAY 202**: Technical deep dive: explain your capstone project in detail
- **DAY 203**: Behavioral questions preparation (STAR format for engineering scenarios)
- **DAY 204**: Whiteboard system design practice (draw by hand, photograph)
- **DAY 205**: Full mock interview: system design + behavioral (ask a friend or use Pramp.com)

### DAY 206–208 — Final Portfolio Audit
- 📝 Audit every GitHub repository for completeness
- 📝 Verify all CI pipelines are green
- 📝 Confirm portfolio website is live and all links work
- 📝 Verify Grafana dashboard screenshot is in capstone README

### DAY 209 — Final Retrospective
- 📝 Write your complete "210 days" retrospective:
  - What you built (full list)
  - What you learned that surprised you most
  - What you would teach your day-1 self
  - Where you want to go next
- 📝 Tag the capstone: `v1.0.0` — production-ready

### DAY 210 — Done 🎉
- ✅ You've gone from zero to a portfolio that proves:
  - System design thinking at MNC level
  - Production-grade implementation experience
  - DevOps and observability skills
  - Real documentation and communication ability
- 📝 Update GitHub profile README: mark journey as complete, add "Open to opportunities"

---

## 📊 Complete Checklist: All 210 Days

### Phase 0 (Days 1–14)
- [ ] Latency cheat sheet with real-world analogies
- [ ] System monitor script (bash + Python)
- [ ] Merge conflict created, resolved, documented
- [ ] Shell scripts committed as systemd service
- [ ] GitHub profile README live

### Phase 1 (Days 15–35)
- [ ] Wireshark TCP handshake capture annotated
- [ ] "What happens when you type google.com" document
- [ ] Network Diagnostics FastAPI deployed
- [ ] NGINX load balancer with round-robin and health checks
- [ ] WebSocket chat application
- [ ] Locust load test results committed

### Phase 2 (Days 36–49)
- [ ] Race condition + fix committed
- [ ] Deadlock + fix committed
- [ ] CPU-bound vs I/O-bound concurrency benchmark
- [ ] WAL implementation with crash recovery
- [ ] Storage benchmark (HDD/SSD/NVMe)

### Phase 3 (Days 50–70)
- [ ] E-commerce PostgreSQL schema (1M+ rows)
- [ ] EXPLAIN ANALYZE before/after index optimization
- [ ] Redis caching with hit rate logging
- [ ] Redis rate limiter (3 algorithms)
- [ ] PostgreSQL read replica setup
- [ ] MinIO file upload service

### Phase 4 (Days 71–84)
- [ ] JWT auth service (register, login, RBAC, refresh)
- [ ] Kafka order processing pipeline
- [ ] Microservices extracted from monolith
- [ ] NGINX API gateway
- [ ] Circuit breaker implementation
- [ ] Saga pattern for distributed transactions

### Phase 5 (Days 85–119)
- [ ] URL Shortener: full implementation
- [ ] Twitter-like feed with fan-out
- [ ] 5+ system design documents (ADR format)
- [ ] Consistent hashing implementation
- [ ] Architecture walkthrough video recorded

### Phase 6 (Days 120–210)
- [ ] Multi-stage Docker builds (before/after size comparison)
- [ ] GitHub Actions CI/CD pipeline (green badge in README)
- [ ] Kubernetes deployment with HPA
- [ ] Prometheus + Grafana RED dashboard
- [ ] Grafana screenshot during load test
- [ ] Loki log aggregation running
- [ ] Capstone project: 6+ services deployed
- [ ] 15-minute architecture walkthrough video
- [ ] Portfolio website live on GitHub Pages
- [ ] 3 technical articles published

---

> **Daily Commitment**: 4–6 hours/day, 7 days/week.
> **Non-negotiable rule**: Every day has a GitHub commit. No exceptions.
> **Remember**: The documentation IS the portfolio. If it's not documented, it doesn't exist.

---
*Total: 210 days | ~30 weeks | 900–1260 hours of deliberate practice*