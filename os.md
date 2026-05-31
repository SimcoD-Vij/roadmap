# 🖥️ Operating Systems: Complete Mastery Roadmap
### From Absolute Zero → MNC Production-Grade Engineer
#### *If you don't know Python, C, or what a CPU is — start here.*

---

> **Document Purpose:** This is your complete, day-by-day learning system for Operating Systems. Every topic connects to the next. Every project solves a real-world problem. Every day ends with something you can publish online so that anyone — recruiter, engineer, or hiring manager — can see exactly what you built and learned.
>
> **This document was architected for you specifically:** someone starting with zero programming knowledge, zero hardware knowledge, but with the ambition to build MNC-grade production systems and document the journey publicly.

---

## 📐 SECTION 0: THE MASTER ARCHITECTURE — Read This First

Before you learn a single topic, you need to understand the **full map of what you are building.** Think of this like a city. You need to see the whole city from above before you start building individual houses.

### 🗺️ The Learning Universe (Bird's Eye View)

```
╔══════════════════════════════════════════════════════════════════════════╗
║                   YOUR 90-DAY LEARNING UNIVERSE                         ║
╠══════════════════════════════════════════════════════════════════════════╣
║                                                                          ║
║  PHASE 0 (Days 0-7):   SURVIVAL SKILLS                                  ║
║  ┌─────────────────────────────────────────────────────────────────────┐ ║
║  │ Linux Terminal │ Python Basics │ C Language Intro │ Git + GitHub    │ ║
║  └─────────────────────────────────────────────────────────────────────┘ ║
║                              ↓ feeds into                               ║
║  PHASE 1 (Days 8-20):  THE KERNEL & PROCESSES                          ║
║  ┌─────────────────────────────────────────────────────────────────────┐ ║
║  │ What is an OS │ CPU Modes │ System Calls │ Processes │ Scheduling   │ ║
║  └─────────────────────────────────────────────────────────────────────┘ ║
║                  ↓ PROJECT 1: Unix Shell (Day 18-20)                   ║
║                              ↓ feeds into                               ║
║  PHASE 2 (Days 21-38):  CONCURRENCY & THREADS                          ║
║  ┌─────────────────────────────────────────────────────────────────────┐ ║
║  │ Threads │ Locks │ Semaphores │ Deadlocks │ Real Crash Case Studies  │ ║
║  └─────────────────────────────────────────────────────────────────────┘ ║
║             ↓ PROJECT 2: User-Level Thread Library (Day 33-38)         ║
║                              ↓ feeds into                               ║
║  PHASE 3 (Days 39-52):  MEMORY MANAGEMENT                              ║
║  ┌─────────────────────────────────────────────────────────────────────┐ ║
║  │ Virtual Memory │ Paging │ TLB │ Page Faults │ Heap Allocation       │ ║
║  └─────────────────────────────────────────────────────────────────────┘ ║
║                  ↓ PROJECT 3: Custom malloc() (Day 46-52)              ║
║                              ↓ feeds into                               ║
║  PHASE 4 (Days 53-63):  FILE SYSTEMS & STORAGE                         ║
║  ┌─────────────────────────────────────────────────────────────────────┐ ║
║  │ HDD/SSD Physics │ Inodes │ Journaling │ Crash Consistency           │ ║
║  └─────────────────────────────────────────────────────────────────────┘ ║
║                 ↓ PROJECT 4: Toy File System (Day 57-63)               ║
║                              ↓ feeds into                               ║
║  PHASE 5 (Days 64-76):  DISTRIBUTED SYSTEMS                            ║
║  ┌─────────────────────────────────────────────────────────────────────┐ ║
║  │ Networking │ RPC │ CAP Theorem │ Consensus (Raft) │ Sharding        │ ║
║  └─────────────────────────────────────────────────────────────────────┘ ║
║            ↓ PROJECT 5: Distributed Key-Value Store (Day 70-76)        ║
║                              ↓ feeds into                               ║
║  PHASE 6 (Days 77-90):  AI + FUTURE SYSTEMS                            ║
║  ┌─────────────────────────────────────────────────────────────────────┐ ║
║  │ eBPF │ Spectre/Meltdown │ AI Scheduling │ NVM │ Kernel Security     │ ║
║  └─────────────────────────────────────────────────────────────────────┘ ║
║         ↓ PROJECT 6: AI-Powered Semantic Scheduler (Day 84-90)         ║
╚══════════════════════════════════════════════════════════════════════════╝
```

### 🏗️ Why This Architecture? (The Honest Explanation for a Beginner)

Think of an Operating System like the management staff of a large hotel:

| Hotel Analogy | OS Reality | Why You Learn It |
|---|---|---|
| Hotel building (hardware) | CPU, RAM, Disk | You need to know what rooms exist |
| Hotel manager (kernel) | OS Kernel | Who decides which guest gets which room |
| Guest request system | System Calls | How guests ask for services |
| Housekeeping schedule | Scheduler | Who gets the CPU and when |
| Room assignment ledger | Memory Manager | Who gets which RAM addresses |
| Storage room / archive | File System | Where things are stored permanently |
| Multiple hotels (chain) | Distributed Systems | When one building isn't enough |
| Smart management AI | AI in OS | The future — AI decides everything |

**Why do we start with Phase 0 (Terminal + Python + C)?**
Because every single thing in this roadmap requires:
1. A Linux terminal (this is where all OS work happens)
2. Python (to write simulations of OS concepts — readable, fast to learn)
3. C (to write actual OS code — this is what kernels are written in)

You cannot skip Phase 0. It is 7 days. It will save you 70 days of confusion.

---

## 🛠️ TECH STACK SELECTION — MNC Grade, 100% Free

### Why These Specific Tools? (Explained for a Non-Technical Person)

Every tool below was chosen because: (a) it is free and open-source, (b) it is used in actual production systems at Google, Amazon, Meta, or Nvidia, and (c) it is the kind of tool that appears on job descriptions.

| Category | Tool Chosen | Why MNC Grade | Cost |
|---|---|---|---|
| **Operating System** | Ubuntu 24.04 LTS | Every cloud server in the world runs Linux. Ubuntu is the standard dev version. | Free |
| **Primary Language** | C (GCC compiler) | Linux kernel, all major OS components are in C. Required. | Free |
| **Simulation Language** | Python 3.12 | Used to simulate OS algorithms before implementing in C. Google uses Python. | Free |
| **OS to Study** | xv6 (MIT) | Used in MIT's OS course. Small enough to read entirely. Used in FAANG interviews. | Free |
| **Build System** | GNU Make + CMake | How professional C projects are built. Used in Linux kernel itself. | Free |
| **Version Control** | Git + GitHub | Non-negotiable. Every MNC uses Git. Your public portfolio lives here. | Free |
| **Emulator** | QEMU | Run a fake CPU/computer to test OS code without damaging real hardware. | Free |
| **Debugger** | GDB (GNU Debugger) | Industry standard. Used by kernel developers. | Free |
| **Documentation** | GitHub Pages + Markdown | Your code repo becomes your portfolio website automatically. | Free |
| **Blogging** | Dev.to or Hashnode | Technical blog sites where recruiters actually look. | Free |
| **Container Tool** | Docker | Test distributed systems locally. Used everywhere. | Free |
| **Observability** | bpftrace + perf | The actual tools used inside Google/Meta kernel teams. | Free |
| **Distributed Systems** | etcd + gRPC + Protobuf | Used in Kubernetes (Google), every cloud company uses these. | Free |
| **Testing** | pytest + Google Test (gtest) | Industry-standard test frameworks. | Free |

---

## 📚 PRIMARY FREE LEARNING RESOURCES

| Resource | What It Is | Link |
|---|---|---|
| **OSTEP** (Operating Systems: Three Easy Pieces) | The most widely used OS textbook. Free online. Chapters align with this roadmap. | https://pages.cs.wisc.edu/~remzi/OSTEP/ |
| **MIT xv6 Book** | 100-page book explaining the xv6 OS we will study and modify | https://pdos.csail.mit.edu/6.828/2023/xv6/book-riscv-rev3.pdf |
| **The Linux Command Line (book)** | Free online. Learn Linux terminal. | https://linuxcommand.org/tlcl.php |
| **CS:APP (Computer Systems: A Programmer's Perspective)** | Deep dive into hardware-software interface | Free chapters online |
| **LeetCode / Neetcode.io** | Interview preparation for algorithm questions | Free tier available |
| **Brendan Gregg's Blog** | The person who invented bpftrace. Used by Netflix/Meta. | https://brendangregg.com |
| **The Raft Paper (Raft.github.io)** | Interactive visualization of the Raft consensus algorithm | https://raft.github.io |
| **MIT 6.S081 Course** | Full free course from MIT with labs, using xv6 | https://pdos.csail.mit.edu/6.S081/2023 |

---

## 📝 DOCUMENTATION SYSTEM — Your Daily Evidence Trail

This is the most important section for you. Documentation is not optional. It is the **product** of your learning.

### Platform Setup (Do This On Day 0)

#### 1. GitHub (Your Code Portfolio)
- Create account at: https://github.com
- Create a repository named: `os-mastery-journey`
- Structure it like this:
```
os-mastery-journey/
├── README.md              ← Your main portfolio page
├── phase-0-survival/      ← Phase 0 code + notes
├── phase-1-kernel/        ← Phase 1 code + notes
├── phase-2-concurrency/   ← Phase 2 code + notes
├── phase-3-memory/        ← Phase 3 code + notes
├── phase-4-filesystem/    ← Phase 4 code + notes
├── phase-5-distributed/   ← Phase 5 code + notes
├── phase-6-ai-systems/    ← Phase 6 code + notes
├── projects/              ← All 6 major projects
│   ├── 01-unix-shell/
│   ├── 02-thread-library/
│   ├── 03-custom-malloc/
│   ├── 04-toy-filesystem/
│   ├── 05-distributed-kvstore/
│   └── 06-semantic-scheduler/
└── docs/                  ← GitHub Pages website
```

#### 2. Dev.to or Hashnode (Your Written Blog)
- Create account at: https://dev.to OR https://hashnode.com
- These sites appear in Google search results. Recruiters find them.
- Write one article per week minimum summarizing what you learned.

#### 3. LinkedIn (Your Professional Signal)
- Post a "Today I Learned" (TIL) update every 2-3 days
- Tag it with: `#operatingsystems`, `#systemsprogramming`, `#linux`, `#computerscience`

### The Daily Documentation Template

Every single day, after studying, fill this in your GitHub repo's `phase-X/day-XX.md`:

```markdown
# Day XX: [Topic Name]

## 🎯 What I Studied Today
[1-2 sentences: what the topic is]

## 🧠 The Key Insight (In My Own Words)
[Explain it as if teaching a 10-year-old. This proves you understood it.]

## 💻 What I Built / Ran
[Code snippet or command you ran today]

## 🔗 How This Connects to Yesterday
[One sentence: how today's topic builds on yesterday's]

## 🤔 Question I Still Have
[One thing you're unsure about — shows intellectual honesty]

## 📊 Evidence
[Screenshot, terminal output, or link to code]
```

---

---

# 🟡 PHASE 0: SURVIVAL SKILLS (Days 0–7)

> **Goal:** Get comfortable with the tools before learning OS concepts. You cannot build a house without knowing how to use a hammer.
>
> **Why these 7 days matter:** Every OS concept you learn will need you to write code in a terminal, run a C program, or use Git to save your work. Skipping this is like trying to drive a car before learning what a steering wheel is.

---

## Day 0: Environment Setup

### What You're Doing Today
You are setting up your "workbench" — the place where all your OS work will happen.

### Step-by-Step Setup

**Step 1: Install Ubuntu Linux**

Option A (Easiest — No extra computer needed): Install VirtualBox
- Download VirtualBox (free): https://www.virtualbox.org/wiki/Downloads
- Download Ubuntu 24.04 ISO: https://ubuntu.com/download/desktop
- Create a VM: 4GB RAM, 40GB disk, 2 CPU cores
- Install Ubuntu inside the VM

Option B (If you have a spare laptop): Install Ubuntu directly

Option C (Cloud — for slow computers): Use Google Cloud Shell
- Go to: https://shell.cloud.google.com
- This gives you a free Linux terminal in your browser

**Step 2: Open a Terminal**
- On Ubuntu: Press `Ctrl + Alt + T`
- You will see something like: `yourname@computer:~$`
- This is called the **shell prompt**. Everything you type here runs on the computer.

**Step 3: Install Required Software**
```bash
# Update the system's software list
sudo apt update

# Install C compiler (GCC), build tool (Make), Python, Git, QEMU, and debugger
sudo apt install -y gcc make python3 python3-pip git qemu-system gdb vim curl wget
```

**Step 4: Create GitHub Account and Repo**
```bash
# Configure Git with your name and email
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# Create your project folder
mkdir -p ~/os-mastery-journey
cd ~/os-mastery-journey
git init
```

**Step 5: Write Your First File**
```bash
# Create your README
echo "# My OS Mastery Journey" > README.md
echo "Started: $(date)" >> README.md
git add README.md
git commit -m "Day 0: Journey begins"
```

### 📝 Documentation Task (Day 0)
- Create GitHub account
- Create repository `os-mastery-journey`
- Post on LinkedIn: "Day 0 of my Operating Systems journey. I just set up my Linux environment. The goal: understand how computers actually work at the deepest level. #Linux #OperatingSystems #100DaysOfCode"

---

## Day 1: Linux Terminal Basics — Part 1

### What You're Learning and Why
The terminal is the **only way** to talk to a computer at the OS level. Every command you will run for the next 89 days goes through here. This is not optional. This is like learning to walk before you run.

### Topics Covered
- What is a shell? (bash is the most common shell — it's a program that reads your commands)
- File system navigation
- File and directory operations
- Understanding file paths (absolute vs relative)

### Core Commands to Master

```bash
# NAVIGATION
pwd               # Print Working Directory — "Where am I right now?"
ls                # List files in current directory
ls -la            # List ALL files including hidden ones, with details
cd Documents      # Change Directory — move INTO Documents folder
cd ..             # Move UP one level (go to parent folder)
cd ~              # Go to your home directory (shortcut)
cd /              # Go to root directory (the very top of the file system)

# FILE OPERATIONS
touch hello.txt   # Create an empty file called hello.txt
mkdir myfolder    # Make a new directory
cp hello.txt backup.txt    # Copy a file
mv hello.txt renamed.txt   # Move or rename a file
rm renamed.txt    # Remove/delete a file (CAREFUL: no trash can!)
rm -rf myfolder   # Remove a folder and everything in it (VERY careful!)

# READING FILES
cat hello.txt     # Print entire file to screen
head -5 hello.txt # Print first 5 lines
tail -5 hello.txt # Print last 5 lines
less hello.txt    # Read file page by page (press q to quit)

# FINDING THINGS
find . -name "*.txt"          # Find all .txt files from current directory
grep "hello" hello.txt        # Find the word "hello" inside a file
grep -r "hello" ./myfolder    # Find "hello" in ALL files inside myfolder
```

### Understanding the Linux File System Layout

```
/                     ← Root (like C:\ on Windows)
├── bin/              ← Essential programs (ls, cd, echo live here)
├── etc/              ← Configuration files for programs
├── home/             ← Your personal folder (/home/yourname)
├── var/              ← Variable data (logs, databases)
├── usr/              ← Installed programs and libraries
├── dev/              ← Device files (your hard disk is /dev/sda)
├── proc/             ← Virtual folder: information about running processes
│   ├── 1234/         ← Folder for process with ID 1234
│   │   ├── status    ← Info about this process (try: cat /proc/self/status)
│   │   └── maps      ← Memory map of this process
└── sys/              ← Virtual folder: information about hardware
```

### Assignment: Explore Your System
```bash
# Find out how much RAM you have
cat /proc/meminfo | head -5

# Find out about your CPU
cat /proc/cpuinfo | grep "model name" | head -1

# See all running processes
ps aux | head -20

# See disk space
df -h
```

### 📝 Documentation Task (Day 1)
Write in your GitHub: `phase-0-survival/day-01.md`
- Include the output of `cat /proc/cpuinfo | grep "model name"` from your machine
- Explain in your own words: What is the difference between a file and a directory?

---

## Day 2: Linux Terminal Basics — Part 2

### Topics Covered
- Pipes and redirection (the most powerful Linux concept)
- Process management from the terminal
- Text editing with vim (you will use this for OS code)
- Shell scripting basics

### Pipes and Redirection — The Most Important Concept

```bash
# The PIPE symbol | means: "take the output of this command and feed it 
# as input to the next command"
ls -la | grep ".txt"          # List files, then filter to only show .txt files
cat /proc/meminfo | grep Mem  # Read memory info, show only lines with "Mem"
ps aux | sort -k3 -n | tail   # List processes, sort by CPU%, show top ones

# REDIRECTION: Instead of showing output on screen, save it to a file
ls -la > filelist.txt         # Save directory listing to a file (overwrites)
echo "hello" >> log.txt       # Append "hello" to log.txt (doesn't overwrite)
cat filelist.txt              # Now read the saved file

# Read FROM a file instead of keyboard
sort < unsorted.txt           # Sort the lines in unsorted.txt

# Combine them
grep "error" /var/log/syslog > errors.txt 2>&1
# This: finds "error" in the log, saves output to errors.txt, 
# AND captures any error messages (2>&1 means "errors go to same place as output")
```

### Process Management

```bash
# See all processes in real-time (like Task Manager)
top           # Press q to quit
htop          # Better version (install with: sudo apt install htop)

# Run a command in the background
sleep 100 &   # The & makes it run in background
jobs          # See background jobs
ps aux | grep sleep  # Find it by name
kill 12345    # Kill process with ID 12345 (replace with actual ID)
killall sleep # Kill all processes named "sleep"

# See how long a command takes
time ls -la /usr/bin
```

### Vim — The Terminal Text Editor

Vim is the text editor used by OS developers. It feels impossible at first. It gets fast with practice.

```bash
# Open a file in vim
vim myfile.txt

# MODES:
# Normal mode: navigate, delete, copy (press Escape to get here)
# Insert mode: type text (press i to enter)
# Command mode: save, quit (press : to enter)

# Essential vim commands:
i          # Enter Insert mode (start typing)
Esc        # Go back to Normal mode
:w         # Save the file
:q         # Quit vim
:wq        # Save AND quit
:q!        # Quit WITHOUT saving (force quit)
dd         # Delete current line (in Normal mode)
yy         # Copy current line
p          # Paste copied line
/hello     # Search for "hello" (press n for next match)
```

### Your First Shell Script

```bash
# Create a file called myscript.sh
vim myscript.sh
```

Type this inside vim (press `i` first to enter insert mode):
```bash
#!/bin/bash
# This is a comment. The first line tells the computer: use bash to run this.

echo "Hello! I am a shell script."
echo "Today is: $(date)"
echo "My username is: $(whoami)"
echo "I am running from: $(pwd)"

# Loop example
for i in 1 2 3 4 5; do
    echo "Counting: $i"
done

# If statement
if [ -f "README.md" ]; then
    echo "README.md exists!"
else
    echo "README.md does not exist."
fi
```

```bash
# Make the script executable and run it
chmod +x myscript.sh
./myscript.sh
```

### 📝 Documentation Task (Day 2)
- Add your shell script to GitHub: `phase-0-survival/myscript.sh`
- Screenshot the output and include in `day-02.md`
- Write: "A pipe in Linux means ___. I used it today to ___."

---

## Day 3: Python Basics — Part 1

### Why Python Before C?
Python lets you write simulations of OS algorithms (scheduling, memory management) in 20 lines instead of 200. You will use Python to *understand* a concept before implementing it properly in C. This is the professional way: prototype first, optimize later.

### Topics Covered
- Variables, data types, printing
- Lists and dictionaries (you will use these to simulate process queues and memory tables)
- Functions
- Loops and conditions

### Python Crash Course for OS Simulations

```python
# Save this as: phase-0-survival/python_basics.py
# Run with: python3 python_basics.py

# ---- VARIABLES AND TYPES ----
process_name = "firefox"       # String (text)
process_id = 1234              # Integer (whole number)
cpu_usage = 45.6               # Float (decimal number)
is_running = True              # Boolean (True or False)

print(f"Process: {process_name}, PID: {process_id}, CPU: {cpu_usage}%")

# ---- LISTS (like an ordered queue of processes) ----
ready_queue = ["process_A", "process_B", "process_C"]
print("Ready queue:", ready_queue)
ready_queue.append("process_D")    # Add to end
print("After adding D:", ready_queue)
first = ready_queue.pop(0)         # Remove from front (like a real queue)
print("Process that ran:", first)
print("Queue now:", ready_queue)

# ---- DICTIONARIES (like a process table: ID -> info) ----
process_table = {
    1001: {"name": "bash",    "state": "running", "priority": 5},
    1002: {"name": "firefox", "state": "waiting", "priority": 3},
    1003: {"name": "python3", "state": "sleeping","priority": 4},
}

# Look up a specific process
print("Process 1002:", process_table[1002])
print("Its name:", process_table[1002]["name"])

# Loop through all processes
for pid, info in process_table.items():
    print(f"PID {pid}: {info['name']} is {info['state']}")

# ---- FUNCTIONS ----
def calculate_turnaround_time(arrival_time, finish_time):
    """
    Turnaround time = time from when a process arrived to when it finished.
    This is a key OS scheduling metric.
    """
    return finish_time - arrival_time

result = calculate_turnaround_time(arrival_time=0, finish_time=10)
print(f"Turnaround time: {result} units")
```

### Your First OS Simulation in Python

```python
# Save as: phase-0-survival/fcfs_simulation.py
# FCFS = First Come, First Served scheduling (simplest possible scheduler)

def simulate_fcfs(processes):
    """
    Simulate First Come First Served CPU scheduling.
    Input: list of (name, arrival_time, burst_time) tuples
    Output: when each process finishes
    """
    current_time = 0
    results = []

    print("\n=== FCFS CPU Scheduling Simulation ===")
    print(f"{'Process':<12} {'Arrived':<10} {'Burst':<8} {'Start':<8} {'Finish':<8} {'Turnaround'}")
    print("-" * 60)

    for name, arrival, burst in processes:
        # CPU is free: jump to arrival time if needed
        if current_time < arrival:
            current_time = arrival

        start_time = current_time
        finish_time = current_time + burst
        turnaround = finish_time - arrival
        current_time = finish_time

        results.append((name, turnaround))
        print(f"{name:<12} {arrival:<10} {burst:<8} {start_time:<8} {finish_time:<8} {turnaround}")

    avg_turnaround = sum(t for _, t in results) / len(results)
    print(f"\nAverage Turnaround Time: {avg_turnaround:.2f} units")
    return results


# Define some processes: (name, arrival_time, burst_time)
processes = [
    ("chrome",    0, 8),    # Chrome arrives at time 0, needs 8 CPU units
    ("firefox",   2, 4),    # Firefox arrives at time 2, needs 4 units
    ("terminal",  4, 1),    # Terminal arrives at time 4, needs 1 unit
    ("vscode",    6, 6),    # VSCode arrives at time 6, needs 6 units
]

simulate_fcfs(processes)
```

Run this: `python3 fcfs_simulation.py`

You just simulated a CPU scheduler. That's OS theory, running on your machine.

### 📝 Documentation Task (Day 3)
- Push both Python files to GitHub
- In `day-03.md`, paste the output of your FCFS simulation
- Write: "FCFS means ___. A problem with it is ___ (hint: what if a very short process has to wait behind a very long one?)"

---

## Day 4: Python Basics — Part 2

### Topics Covered
- Classes and objects (how to model OS structures like Process Control Blocks)
- File I/O (reading and writing files — you will do this in the file system project)
- Error handling
- Sorting and queues

### Modeling OS Structures with Python Classes

```python
# Save as: phase-0-survival/process_model.py

class Process:
    """
    This models a Process Control Block (PCB).
    In a real OS, the kernel keeps this data structure for every running process.
    """
    # Process states (a process is always in exactly one of these states)
    STATES = ["new", "ready", "running", "waiting", "terminated"]

    def __init__(self, pid, name, priority=5):
        self.pid = pid               # Process ID (unique number)
        self.name = name             # Human-readable name
        self.priority = priority     # Scheduling priority (1=highest, 10=lowest)
        self.state = "new"           # Current state
        self.cpu_time_used = 0       # How much CPU time consumed
        self.arrival_time = 0        # When it entered the system

    def change_state(self, new_state):
        if new_state not in self.STATES:
            raise ValueError(f"Invalid state: {new_state}")
        old_state = self.state
        self.state = new_state
        print(f"  [PID {self.pid}] {self.name}: {old_state} → {new_state}")

    def __repr__(self):
        return f"Process(pid={self.pid}, name='{self.name}', state='{self.state}')"


class ReadyQueue:
    """
    A priority-based ready queue.
    In a real OS, the scheduler picks from this queue to decide who runs next.
    """
    def __init__(self):
        self.queue = []

    def add(self, process):
        self.queue.append(process)
        # Sort by priority (lower number = higher priority)
        self.queue.sort(key=lambda p: p.priority)
        process.change_state("ready")

    def get_next(self):
        if self.queue:
            process = self.queue.pop(0)  # Get highest priority process
            process.change_state("running")
            return process
        return None

    def __len__(self):
        return len(self.queue)

    def show(self):
        print("  Ready Queue:", [p.name for p in self.queue])


# ---- Demo ----
print("=== OS Process State Machine Demo ===\n")

# Create some processes
p1 = Process(1001, "firefox",  priority=3)
p2 = Process(1002, "terminal", priority=1)  # Highest priority
p3 = Process(1003, "vscode",   priority=5)

rq = ReadyQueue()

# Processes arrive and enter ready queue
print("Processes arriving:")
rq.add(p1)
rq.add(p2)
rq.add(p3)

rq.show()

# Scheduler picks next process
print("\nScheduler picks next process:")
running = rq.get_next()
print(f"Now running: {running.name}")
rq.show()
```

### 📝 Documentation Task (Day 4)
- Push to GitHub
- In `day-04.md`: draw a state diagram manually (or in text art) showing the 5 process states: new → ready → running → waiting → terminated. Explain what causes each transition.

---

## Day 5: C Language Crash Course — Part 1

### Why C? (The Real Reason)
The Linux kernel is ~30 million lines of C code. Every OS concept you will implement — shells, memory allocators, thread libraries, file systems — will be in C. You cannot avoid it.

### Topics Covered
- Variables, types, and memory
- Pointers (the hardest and most important concept in C)
- Functions and the stack

### C Fundamentals

```c
/* Save as: phase-0-survival/c_basics.c
   Compile with: gcc -o c_basics c_basics.c
   Run with: ./c_basics
*/

#include <stdio.h>   /* Standard I/O: printf, scanf */
#include <stdlib.h>  /* Memory allocation: malloc, free */
#include <string.h>  /* String functions: strlen, strcpy */

int main() {
    /* ---- BASIC TYPES ---- */
    int   process_id = 1234;         /* 4 bytes, whole number */
    float cpu_percent = 45.6f;       /* 4 bytes, decimal */
    char  name[32] = "firefox";      /* Array of characters = string */
    int   is_running = 1;            /* In C, 0=false, anything else=true */

    printf("PID: %d, CPU: %.1f%%, Name: %s\n", 
           process_id, cpu_percent, name);

    /* ---- POINTERS ---- 
       A pointer is a variable that stores a MEMORY ADDRESS.
       Think of memory as a long street of houses numbered 0, 1, 2, 3...
       A pointer stores a house number (address), not the house's contents.
    */
    int x = 42;         /* x is a variable. It lives somewhere in memory. */
    int *ptr = &x;      /* ptr is a POINTER. & means "give me the address of x" */
                        /* ptr now holds the address (house number) of x */

    printf("\nPointer Demo:\n");
    printf("Value of x:           %d\n",  x);
    printf("Address of x:         %p\n",  (void*)&x);   /* The memory address */
    printf("ptr stores address:   %p\n",  (void*)ptr);   /* Same address */
    printf("*ptr = value AT addr: %d\n",  *ptr);         /* The * "dereferences" */
                                                          /* = reads the value AT that address */

    /* Changing x through the pointer */
    *ptr = 100;         /* Change the value at the address ptr points to */
    printf("x is now: %d\n", x);   /* x changed! Because ptr pointed at x. */

    /* ---- WHY POINTERS MATTER FOR OS ----
       When the OS needs to pass large data structures (like a Process Control Block)
       to a function, it passes a POINTER to avoid copying the entire structure.
       When functions need to return multiple values, they take pointers as parameters.
    */

    /* ---- ARRAYS ---- */
    int ready_queue[5] = {1001, 1002, 1003, 1004, 1005};
    
    printf("\nReady Queue (PIDs):\n");
    for (int i = 0; i < 5; i++) {
        printf("  Position %d: PID %d\n", i, ready_queue[i]);
    }

    /* IMPORTANT: In C, the array name IS a pointer to the first element */
    printf("Address of ready_queue[0]: %p\n", (void*)ready_queue);
    printf("Address of ready_queue[1]: %p\n", (void*)&ready_queue[1]);
    /* Notice: the addresses differ by exactly 4 bytes (size of int) */

    return 0;
}
```

### 📝 Documentation Task (Day 5)
- Compile and run the C program. Screenshot the output.
- In `day-05.md`, explain: "A pointer in C is like ___. The difference between `x` and `&x` is ___."

---

## Day 6: C Language Crash Course — Part 2

### Topics Covered
- Structs (modeling data structures)
- Dynamic memory with malloc/free
- Linked lists (used everywhere in OS code)

```c
/* Save as: phase-0-survival/c_structs_malloc.c
   gcc -o c_structs c_structs_malloc.c && ./c_structs
*/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/* ---- STRUCT: Groups related data together ----
   This is how the OS kernel represents a process internally.
   The real Linux struct is called task_struct and has ~500 fields.
*/
struct ProcessControlBlock {
    int   pid;
    char  name[64];
    int   priority;
    int   state;       /* 0=ready, 1=running, 2=waiting, 3=terminated */
    int   cpu_time;
    struct ProcessControlBlock *next;  /* Pointer to next PCB in a linked list */
};

/* Type alias so we don't have to type "struct ProcessControlBlock" every time */
typedef struct ProcessControlBlock PCB;

/* ---- Create a new process (allocate memory dynamically) ---- */
PCB* create_process(int pid, const char* name, int priority) {
    /* malloc: ask the OS for memory at runtime */
    PCB *new_pcb = (PCB*) malloc(sizeof(PCB));
    
    if (new_pcb == NULL) {
        printf("ERROR: Out of memory!\n");
        return NULL;
    }
    
    new_pcb->pid = pid;
    strncpy(new_pcb->name, name, 63);
    new_pcb->priority = priority;
    new_pcb->state = 0;        /* Ready */
    new_pcb->cpu_time = 0;
    new_pcb->next = NULL;
    
    return new_pcb;
}

/* ---- Print all processes in the linked list ---- */
void print_process_list(PCB *head) {
    printf("\n=== Process List ===\n");
    PCB *current = head;
    int count = 0;
    while (current != NULL) {
        printf("  [%d] PID=%d, Name=%-12s, Priority=%d\n",
               count, current->pid, current->name, current->priority);
        current = current->next;
        count++;
    }
    printf("Total processes: %d\n", count);
}

/* ---- Free all memory when done ---- */
void destroy_process_list(PCB *head) {
    PCB *current = head;
    while (current != NULL) {
        PCB *next = current->next;
        free(current);         /* Return memory to the OS */
        current = next;
    }
}

int main() {
    /* Build a linked list of processes */
    PCB *process_list = NULL;   /* Start: empty list */
    PCB *tail = NULL;

    /* Create processes and link them */
    char* names[] = {"init", "bash", "firefox", "vim", "python3"};
    int priorities[] = {1, 2, 4, 3, 5};
    
    for (int i = 0; i < 5; i++) {
        PCB *new_p = create_process(1000 + i, names[i], priorities[i]);
        if (process_list == NULL) {
            process_list = new_p;
            tail = new_p;
        } else {
            tail->next = new_p;
            tail = new_p;
        }
    }

    print_process_list(process_list);
    destroy_process_list(process_list);
    
    printf("\nAll memory freed successfully.\n");
    return 0;
}
```

### 📝 Documentation Task (Day 6)
- Run the program. Notice: you created processes using `malloc` and destroyed them with `free`.
- Write in `day-06.md`: "malloc is like ___. free is like ___. If you forget to call free, it's called a ___ leak."

---

## Day 7: Git Workflow + First Blog Post

### Topics Covered
- Git add, commit, push workflow
- Writing a compelling technical README
- Publishing your first blog post

### Git Workflow Every Developer Uses

```bash
# The daily git ritual:
cd ~/os-mastery-journey

# 1. See what changed
git status

# 2. Stage the changes you want to save
git add phase-0-survival/day-07.md
# Or add everything:
git add .

# 3. Save with a message (commit)
git commit -m "Day 7: Completed Phase 0 survival skills"

# 4. Upload to GitHub
git push origin main

# Useful git commands
git log --oneline    # See history of commits
git diff             # See what changed since last commit
git branch           # List branches
```

### Write Your First Blog Post

On Dev.to or Hashnode, publish an article titled:

**"7 Days to Learn Linux Terminal, Python, and C: My OS Journey Begins"**

Include:
1. Why you are learning OS concepts
2. The tools you set up (Ubuntu, GCC, Python)
3. The hardest thing you learned (probably pointers)
4. One code snippet that surprised you
5. What you plan to build in the next 90 days

This post will appear in Google search results. It is your first public artifact.

### 📝 Phase 0 Completion Checklist

- [ ] Ubuntu Linux installed and working
- [ ] Can navigate terminal without looking at notes
- [ ] Git repo created and pushed to GitHub
- [ ] Python simulation of FCFS scheduling written and working
- [ ] C program with structs and malloc written and working
- [ ] Vim can be opened and a file saved without panic
- [ ] First blog post published on Dev.to/Hashnode
- [ ] LinkedIn post done

---

---

# 🔵 PHASE 1: THE KERNEL & PROCESSES (Days 8–20)

> **Goal:** Understand the fundamental abstraction of an Operating System: how software runs on hardware, what a process is, and how the CPU decides who runs when.
>
> **The connecting thread:** Every day this phase builds toward Project 1 — a Unix Shell — which combines everything you learn about processes, system calls, and I/O.

---

## Day 8: What Is an Operating System?

### The Concept (Explained From Zero)

Think of your computer's hardware — the CPU, RAM, and hard disk — as construction equipment: powerful but dangerous. You wouldn't let random workers directly operate a giant crane without training. The Operating System is the trained, trusted crew chief who:

1. **Allocates** resources fairly (who gets to use the CPU right now?)
2. **Abstracts** complexity (your program says "write to a file" — the OS figures out which disk sector)
3. **Protects** things (one program cannot read another program's private memory)

### The Von Neumann Architecture — Your Hardware Baseline

Before learning OS, you must understand what the OS manages.

```
┌─────────────────────────────────────────────────────────────────────┐
│                       COMPUTER HARDWARE                             │
│                                                                     │
│  ┌──────────────┐         ┌────────────────────────────────────┐   │
│  │     CPU      │◄───────►│            RAM (Memory)            │   │
│  │              │         │ 0x0000: [code for your program]    │   │
│  │ • Registers  │         │ 0x1000: [your program's variables] │   │
│  │   (tiny,     │         │ 0x2000: [OS kernel code]           │   │
│  │   super-fast)│         │ ...millions of addresses...        │   │
│  │ • ALU        │         └─────────────────┬──────────────────┘   │
│  │   (does math)│                           │                       │
│  │ • Control    │         ┌─────────────────▼──────────────────┐   │
│  │   Unit       │         │         STORAGE (Disk)             │   │
│  └──────┬───────┘         │  Permanent storage: files, OS data │   │
│         │                 └────────────────────────────────────┘   │
│         │                                                           │
│  ┌──────▼───────────────────────────────────────┐                  │
│  │              I/O DEVICES                      │                  │
│  │  Keyboard, Mouse, Display, Network Card       │                  │
│  └───────────────────────────────────────────────┘                  │
└─────────────────────────────────────────────────────────────────────┘

KEY INSIGHT: RAM is TEMPORARY. Turn off power → everything in RAM is gone.
             Disk is PERMANENT. Turn off power → files survive.
             CPU can only work on what's currently in RAM.
```

### The OS Lives Between Hardware and Your Apps

```
┌─────────────────────────────────────────┐
│     USER APPLICATIONS                   │
│  (Chrome, Python, your shell program)   │
├─────────────────────────────────────────┤
│     SYSTEM CALL INTERFACE               │  ← "Menu" of OS services
├─────────────────────────────────────────┤
│     OS KERNEL                           │  ← Trusted, privileged code
│  • Process Manager                      │
│  • Memory Manager                       │
│  • File System                          │
│  • Device Drivers                       │
├─────────────────────────────────────────┤
│     HARDWARE                            │
│  (CPU, RAM, Disk, Network, I/O)         │
└─────────────────────────────────────────┘
```

### Assignment: Explore the /proc Filesystem

The `/proc` directory in Linux is a window into the OS kernel. Every file here is generated in real-time by the kernel to show you its internal state.

```bash
# See all running processes (each numbered folder = one process)
ls /proc | grep '^[0-9]' | head -10

# Look inside your bash process (replace PID with actual bash PID)
echo $$          # This prints bash's own PID
cat /proc/$$/status | head -20   # Bash tells you about itself

# See what system calls your program makes (install strace first)
sudo apt install strace
strace -c ls    # Count how many times ls uses each system call
```

### 📝 Documentation Task (Day 8)
- In `phase-1-kernel/day-08.md`: Include the output of `strace -c ls`
- Write: "The most used system call when running `ls` was ___. My guess for why is ___."

---

## Day 9: CPU Privilege Levels — Kernel Mode vs User Mode

### The Problem This Solves

Imagine if every program running on your computer could directly access every memory location, including the OS kernel's code and the passwords stored in memory. Chaos. Any buggy or malicious program could crash the system or steal data.

Modern CPUs solve this with **hardware-enforced privilege levels**.

### The Ring Architecture

```
Ring 0 (KERNEL MODE)
┌──────────────────────────────────────┐
│  Can do ANYTHING:                    │
│  • Read/write ANY memory address     │
│  • Talk directly to hardware         │
│  • Enable/disable interrupts         │
│  • Run privileged instructions       │
│                                      │
│  WHO: Only the OS kernel runs here   │
└──────────────────────────────────────┘
          ↕ protected boundary ↕
Ring 3 (USER MODE)
┌──────────────────────────────────────┐
│  Can ONLY:                           │
│  • Access its own memory             │
│  • Run non-privileged instructions   │
│  • Request OS services (via syscall) │
│                                      │
│  WHO: All your programs live here    │
│  (Chrome, Python, your shell)        │
└──────────────────────────────────────┘
```

### The System Call: Crossing the Privilege Boundary

A **system call** (syscall) is the ONLY legal way for a user program to ask the kernel to do something privileged.

When you write `printf("hello")` in C:
1. `printf` eventually calls `write()` (a C library function)
2. `write()` executes a special CPU instruction: `syscall` (on x86-64) 
3. This **traps** into kernel mode (hardware enforced — cannot be faked)
4. The CPU automatically switches to Ring 0
5. The kernel checks: is this a valid request?
6. Kernel performs the operation
7. Kernel returns the result
8. CPU switches back to Ring 3 (user mode)
9. Your program continues

```
User Program                 Kernel
    │                           │
    │  printf("hello")          │
    │                           │
    │  write(1, "hello", 5)     │
    │                           │
    │──── syscall instruction ──►│  ← CPU switches to Ring 0
    │                           │
    │                           │  Kernel: "Is FD 1 valid? Yes. Write to stdout."
    │                           │
    │◄─── return value (5) ─────│  ← CPU switches back to Ring 3
    │                           │
    │  Continues...             │
```

### Look at System Calls Live

```bash
# Trace what happens when a simple program runs
strace echo "hello world"

# You will see lines like:
# write(1, "hello world\n", 12) = 12
#   ^ syscall name
#      ^ file descriptor (1 = stdout)
#              ^ string to write
#                              ^ bytes written

# Count system calls for different programs
strace -c python3 -c "print('hi')" 2>&1 | head -20
strace -c cat /etc/hostname 2>&1 | head -20
```

### 📝 Documentation Task (Day 9)
- Write in `day-09.md`: "When I ran `strace echo`, I saw the syscall `write(1, ...)`. The number 1 means ___."
- Draw (in text art) the sequence of events when `printf("hello")` runs.

---

## Day 10: Processes — The OS Abstraction

### What Is a Process?
A **process** is not a program. A program is a file on disk. A process is a program *running* — it has:
- Its own private memory space (virtual address space)
- A program counter (where in the code is it right now?)
- A set of registers (temporary calculation values)
- An open file list (what files has it opened?)
- A state (is it running, waiting, or sleeping?)

### The Process Control Block (PCB) in Linux

In Linux, every process is represented by a struct called `task_struct`. Here is a simplified version of what the kernel stores for each process:

```c
/* Simplified Linux task_struct (real one has ~400+ fields) */
struct task_struct {
    /* Identity */
    pid_t pid;                    /* Process ID */
    pid_t ppid;                   /* Parent's PID */
    char comm[16];                /* Command name */

    /* State */
    volatile long state;          /* -1=unrunnable, 0=runnable, >0=stopped */

    /* Scheduling */
    int prio;                     /* Scheduling priority */
    u64 utime, stime;             /* User/kernel CPU time used */

    /* Memory */
    struct mm_struct *mm;         /* Pointer to memory descriptor */

    /* File System */
    struct files_struct *files;   /* Open file descriptors */

    /* Linked list: all processes are connected */
    struct list_head tasks;
};
```

### The Process Lifecycle (5 States)

```
            ┌──── admitted ────┐
            │                  ▼
          [NEW] ──────────► [READY] ◄─── I/O complete or event
                               │
                 scheduler ────┤
                 dispatch      │
                               ▼
                           [RUNNING] ────► [TERMINATED]
                               │
                         I/O or ─►──────► [WAITING]
                         event wait
```

### The fork(), exec(), wait() System Calls

These 3 system calls are how ALL processes in Unix are created:

```c
/* Save as: phase-1-kernel/fork_demo.c
   gcc -o fork_demo fork_demo.c && ./fork_demo
*/
#include <stdio.h>
#include <stdlib.h>
#include <unistd.h>   /* fork(), getpid(), getppid() */
#include <sys/wait.h> /* wait() */

int main() {
    printf("PARENT: I am process %d\n", getpid());

    pid_t child_pid = fork();   /* Create an exact copy of this process */
    
    /* After fork(), BOTH parent and child run from this point */
    /* The ONLY difference: fork() returns 0 to child, child's PID to parent */

    if (child_pid == 0) {
        /* This block runs only in the CHILD process */
        printf("CHILD:  I am process %d, my parent is %d\n", 
               getpid(), getppid());
        
        /* exec() replaces this process with a new program */
        /* The child now becomes the 'ls' command */
        char *args[] = {"ls", "-la", NULL};
        execvp("ls", args);
        
        /* If execvp() returns, something went wrong */
        perror("execvp failed");
        exit(1);

    } else if (child_pid > 0) {
        /* This block runs only in the PARENT process */
        printf("PARENT: I created child with PID %d\n", child_pid);
        printf("PARENT: Waiting for child to finish...\n");

        int status;
        pid_t finished = wait(&status);   /* Block until child exits */
        
        printf("PARENT: Child %d finished with exit code %d\n",
               finished, WEXITSTATUS(status));
    } else {
        /* fork() returned -1: error */
        perror("fork failed");
        exit(1);
    }

    return 0;
}
```

### 📝 Documentation Task (Day 10)
- Run the fork demo. Observe both outputs.
- In `day-10.md`: "fork() creates a new process by ___. After fork(), the parent gets ___ and the child gets ___ as the return value. exec() then ___."

---

## Days 11–12: Scheduling — Who Runs Next?

### The Problem
Multiple processes want to use the CPU, but there is only one CPU (or a few). The **scheduler** must decide: which process runs next, and for how long?

### Key Metrics
- **Turnaround Time** = Finish Time − Arrival Time (how long did the process take overall?)
- **Response Time** = First Run − Arrival Time (how quickly did it get started?)
- **Throughput** = Processes completed per unit of time

### Algorithm 1: FCFS (First Come, First Served)
Simple but problematic. Long processes block short ones. Called the "Convoy Effect."

### Algorithm 2: Shortest Job First (SJF)
Best turnaround time but requires knowing the future (how long will this job run?). Not practical for interactive systems.

### Algorithm 3: Round Robin (RR) — The Basic Reality
Each process gets a fixed time slice (quantum). If it doesn't finish, it goes back to the ready queue.

### Algorithm 4: MLFQ (Multi-Level Feedback Queue) — The Industry Standard

```
MLFQ Structure:
┌─────────────────────────────────────────┐
│  Queue 0 (Highest Priority, 1ms slice)  │ ← New jobs start here
│  [interactive processes get preference] │
├─────────────────────────────────────────┤
│  Queue 1 (Medium Priority, 10ms slice)  │
│  [processes that used their Q0 slice]   │
├─────────────────────────────────────────┤
│  Queue 2 (Lowest Priority, 100ms slice) │
│  [CPU-hungry batch jobs live here]      │
└─────────────────────────────────────────┘

Rules:
1. Higher queue = runs first
2. Use full time slice → demoted to lower queue
3. Yield (do I/O) before slice ends → stay in same queue
4. Periodic "priority boost" moves all jobs to Queue 0
   (prevents starvation of long-running jobs)
```

### Simulate MLFQ in Python

```python
# Save as: phase-1-kernel/mlfq_simulation.py
from collections import deque
import time

class Process:
    def __init__(self, pid, name, total_burst):
        self.pid = pid
        self.name = name
        self.total_burst = total_burst     # Total CPU time needed
        self.remaining = total_burst       # Time still needed
        self.current_queue = 0            # Starts in highest priority queue
        self.arrival = 0
        self.first_run = -1
        self.finish_time = -1

class MLFQ:
    def __init__(self):
        # 3 queues with different time slices
        self.queues = [deque(), deque(), deque()]
        self.time_slices = [2, 5, 10]    # quantum for each queue level
        self.current_time = 0

    def add_process(self, process):
        process.arrival = self.current_time
        self.queues[0].append(process)   # New processes enter Queue 0
        print(f"t={self.current_time}: {process.name} arrived → Queue 0")

    def run(self):
        print("\n=== MLFQ Simulation ===")
        while any(len(q) > 0 for q in self.queues):
            # Find highest-priority non-empty queue
            selected_queue = None
            process = None
            for q_idx in range(3):
                if len(self.queues[q_idx]) > 0:
                    selected_queue = q_idx
                    process = self.queues[q_idx].popleft()
                    break
            
            if process is None:
                break

            quantum = self.time_slices[selected_queue]
            
            if process.first_run == -1:
                process.first_run = self.current_time

            # Run for min(quantum, remaining time)
            run_time = min(quantum, process.remaining)
            process.remaining -= run_time
            self.current_time += run_time

            print(f"t={self.current_time-run_time}-{self.current_time}: "
                  f"Running '{process.name}' from Q{selected_queue} "
                  f"(remaining={process.remaining})")

            if process.remaining == 0:
                process.finish_time = self.current_time
                turnaround = process.finish_time - process.arrival
                response = process.first_run - process.arrival
                print(f"  → '{process.name}' DONE! Turnaround={turnaround}, Response={response}")
            else:
                # Used full quantum: demote to lower queue
                next_queue = min(selected_queue + 1, 2)
                self.queues[next_queue].append(process)
                print(f"  → '{process.name}' preempted → moved to Q{next_queue}")

# Run the simulation
mlfq = MLFQ()
mlfq.add_process(Process(1, "vim",     burst:=2))    # Short interactive task
mlfq.add_process(Process(2, "compile", burst:=20))   # Long batch task
mlfq.add_process(Process(3, "browser", burst:=5))    # Medium task
```

### 📝 Documentation Task (Days 11-12)
- Run your MLFQ simulation
- In `day-11.md` and `day-12.md`: Explain why MLFQ is better than simple Round Robin for a mix of interactive (short) and batch (long) processes.
- Post on LinkedIn: "Today I built a CPU scheduler simulation in Python. MLFQ is the technique used in Windows and Linux. Here's what I learned: [insight]. #SystemsProgramming"

---

## Days 13–14: The Completely Fair Scheduler (Linux CFS)

### What Linux Actually Uses

Linux's CFS does not use fixed time slices or priority queues. Instead:

- Each process has a **vruntime** (virtual runtime) — a counter of how much CPU time it has consumed
- A **Red-Black Tree** (self-balancing tree) holds all processes, ordered by vruntime
- The scheduler always picks the process with the **lowest vruntime** (least CPU time consumed)
- This guarantees fairness: no process gets starved

```bash
# See CFS scheduler in action on your system
cat /proc/sched_debug | head -50

# See the vruntime of your bash process
cat /proc/$$/sched | grep vruntime
```

### Assignment: Read CFS Kernel Code

```bash
# If you have the Linux kernel source (install: sudo apt install linux-source)
# The scheduler lives in:
# /usr/src/linux-source-X.X/kernel/sched/fair.c

# This function picks the next process to run:
# static struct task_struct *pick_next_task_fair(...)

# Key data structure (simplified):
# struct sched_entity {
#     u64 vruntime;    /* How much CPU time has this process used? */
#     ...
# };
```

### 📝 Documentation Task (Days 13-14)
- Research: What is a Red-Black Tree? (Hint: it's a sorted data structure where lookup is always O(log n))
- Write: "CFS is fairer than Round Robin because ___. The vruntime means ___."

---

## Days 15–17: The xv6 Operating System

### What is xv6?
xv6 is a small operating system created by MIT. It has:
- ~15,000 lines of C code (the real Linux kernel has 30 million)
- Everything needed to understand OS concepts: processes, memory, file system
- The exact same architecture as Unix v6 (1976)

It's perfect for learning because you can read the ENTIRE OS in one week.

### Setup xv6

```bash
# Clone xv6 (RISC-V version, used in MIT 6.S081)
cd ~/os-mastery-journey
git clone https://github.com/mit-pdos/xv6-riscv.git
cd xv6-riscv

# Install the RISC-V compiler toolchain
sudo apt install gcc-riscv64-linux-gnu qemu-system-misc

# Build and run xv6 in QEMU (an emulator — no real hardware needed)
make qemu
# You should see xv6 boot! Press Ctrl+A then X to quit QEMU.
```

### Explore xv6 Source Code

```bash
# The most important files to read this week:
ls kernel/

# proc.h    → The struct that defines a process (like task_struct in Linux)
# proc.c    → Create/destroy processes, scheduler
# syscall.c → The system call dispatcher
# trap.c    → Handles interrupts and exceptions
# swtch.S   → THE context switch in assembly (just 15 lines!)
```

Read `kernel/proc.h` and compare the xv6 `struct proc` with the Linux `task_struct` you saw earlier.

### Assignment: Add a System Call to xv6

This is the canonical first OS assignment. You are modifying an actual kernel.

```bash
# GOAL: Add a system call called sys_getcount() that returns 
# how many system calls have been made since boot.

# Step 1: Add the syscall number to kernel/syscall.h
# Add: #define SYS_getcount 22

# Step 2: Add the handler declaration to kernel/syscall.c
# In the extern declarations: extern uint64 sys_getcount(void);
# In the syscall table: [SYS_getcount] sys_getcount,

# Step 3: Implement the handler in kernel/sysproc.c
uint64 sys_getcount(void) {
    extern int syscall_count;  // global counter
    return syscall_count;
}

# Step 4: Increment counter in kernel/syscall.c's syscall() function

# Step 5: Expose to user space (user/user.h and user/usys.pl)

# Step 6: Write a test program in user/getcount_test.c
```

### 📝 Documentation Task (Days 15-17)
- Document the exact files you modified and why in `phase-1-kernel/xv6-syscall-notes.md`
- Push your modified xv6 to a separate GitHub repo: `xv6-mods`
- Blog post: **"I Modified an Operating System Kernel for the First Time"** — describe what you changed, what you learned, and how it felt.

---

## Day 18: Shell Project Kickoff — Problem Statement

### Real-World Problem This Solves

Every terminal you've ever used (bash, zsh, Windows PowerShell) is a **shell**. A shell is a program that:
1. Reads your commands
2. Creates processes to execute them
3. Connects processes together with pipes
4. Manages your session

When you type `ls -la | grep ".txt" > results.txt`, the shell:
1. Creates two child processes: one for `ls`, one for `grep`
2. Creates a pipe (anonymous communication channel in memory)
3. Connects `ls`'s output to the pipe's write end
4. Connects `grep`'s input to the pipe's read end
5. Opens `results.txt` and connects `grep`'s output to it
6. Waits for both children to finish

### Architecture of Your Shell

```
┌─────────────────────────────────────────────────────────────────┐
│                     YOUR UNIX SHELL                             │
│                                                                 │
│  ┌─────────────────┐                                            │
│  │  REPL Loop      │  Read → Evaluate → Print → Loop           │
│  │  (main.c)       │                                            │
│  └────────┬────────┘                                            │
│           │                                                     │
│           ▼                                                     │
│  ┌─────────────────┐                                            │
│  │  Parser         │  "ls -la | grep txt > out.txt"            │
│  │  (parse.c)      │  → tokens: ["ls","-la","|","grep","txt",  │
│  └────────┬────────┘            ">","out.txt"]                  │
│           │                                                     │
│           ▼                                                     │
│  ┌─────────────────┐                                            │
│  │  Executor       │  For each command:                         │
│  │  (execute.c)    │  1. fork() → child process                 │
│  │                 │  2. set up pipes with pipe()               │
│  │                 │  3. redirect I/O with dup2()               │
│  │                 │  4. execvp() → run the command             │
│  └────────┬────────┘  5. parent wait()s for child              │
│           │                                                     │
│  ┌─────────────────┐                                            │
│  │  Built-ins      │  cd, exit, history (implemented in shell) │
│  │  (builtins.c)   │  (can't be external programs!)            │
│  └─────────────────┘                                            │
└─────────────────────────────────────────────────────────────────┘
```

### Tech Stack for the Shell Project
- Language: **C** (all real shells are in C or C++)
- Libraries: `<unistd.h>`, `<sys/wait.h>`, `<fcntl.h>`, `<stdlib.h>`
- Build: **GNU Make** with a proper Makefile
- Testing: **bash scripts** that run your shell and verify output
- Documentation: **README.md** with architecture diagram, usage examples, known limitations

---

## Days 19–20: Build the Unix Shell (PROJECT 1)

### Complete Shell Implementation

```c
/* Save as: projects/01-unix-shell/main.c
   This is a simplified but real, working shell.
   It handles: commands, arguments, pipes, redirection, built-ins.
*/

#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/wait.h>
#include <fcntl.h>
#include <errno.h>

#define MAX_LINE    1024
#define MAX_ARGS    64
#define MAX_PIPES   16

/* ---- Parse a line into an array of tokens ---- */
int tokenize(char *line, char **tokens, const char *delim) {
    int count = 0;
    char *tok = strtok(line, delim);
    while (tok && count < MAX_ARGS - 1) {
        tokens[count++] = tok;
        tok = strtok(NULL, delim);
    }
    tokens[count] = NULL;
    return count;
}

/* ---- Execute a single command with optional I/O redirection ---- */
void execute_command(char **args, int in_fd, int out_fd) {
    /* Check for I/O redirection tokens in args */
    int i;
    for (i = 0; args[i] != NULL; i++) {
        if (strcmp(args[i], ">") == 0) {
            /* Output redirection: open file for writing */
            int fd = open(args[i+1], O_WRONLY | O_CREAT | O_TRUNC, 0644);
            if (fd < 0) { perror("open"); exit(1); }
            dup2(fd, STDOUT_FILENO);   /* Replace stdout with file */
            close(fd);
            args[i] = NULL;            /* Remove > and filename from args */
            break;
        } else if (strcmp(args[i], "<") == 0) {
            /* Input redirection: open file for reading */
            int fd = open(args[i+1], O_RDONLY);
            if (fd < 0) { perror("open"); exit(1); }
            dup2(fd, STDIN_FILENO);
            close(fd);
            args[i] = NULL;
            break;
        }
    }

    /* Set up pipe connections */
    if (in_fd != STDIN_FILENO) {
        dup2(in_fd, STDIN_FILENO);
        close(in_fd);
    }
    if (out_fd != STDOUT_FILENO) {
        dup2(out_fd, STDOUT_FILENO);
        close(out_fd);
    }

    execvp(args[0], args);
    fprintf(stderr, "myshell: command not found: %s\n", args[0]);
    exit(127);
}

/* ---- Handle built-in commands (can't be external processes!) ---- */
int handle_builtin(char **args) {
    if (args[0] == NULL) return 0;
    
    if (strcmp(args[0], "exit") == 0) {
        printf("Goodbye!\n");
        exit(0);
    }
    if (strcmp(args[0], "cd") == 0) {
        char *dir = args[1] ? args[1] : getenv("HOME");
        if (chdir(dir) != 0) perror("cd");
        return 1;
    }
    if (strcmp(args[0], "pwd") == 0) {
        char cwd[1024];
        if (getcwd(cwd, sizeof(cwd))) printf("%s\n", cwd);
        return 1;
    }
    return 0;   /* Not a built-in */
}

int main() {
    char line[MAX_LINE];
    char *pipe_cmds[MAX_PIPES];
    char *args[MAX_ARGS];

    printf("MyShell v1.0 (type 'exit' to quit)\n");

    while (1) {
        /* Print prompt */
        char cwd[256];
        getcwd(cwd, sizeof(cwd));
        printf("[myshell %s]$ ", cwd);
        fflush(stdout);

        /* Read a line of input */
        if (!fgets(line, sizeof(line), stdin)) break;
        line[strcspn(line, "\n")] = '\0';   /* Remove newline */
        if (strlen(line) == 0) continue;

        /* Split by pipe | character */
        char line_copy[MAX_LINE];
        strcpy(line_copy, line);
        int num_cmds = tokenize(line_copy, pipe_cmds, "|");

        if (num_cmds == 1) {
            /* Simple command, no pipes */
            tokenize(line, args, " \t");
            if (handle_builtin(args)) continue;

            pid_t pid = fork();
            if (pid == 0) {
                execute_command(args, STDIN_FILENO, STDOUT_FILENO);
            } else if (pid > 0) {
                int status;
                waitpid(pid, &status, 0);
            } else {
                perror("fork");
            }
        } else {
            /* Pipeline: cmd1 | cmd2 | cmd3 ... */
            int pipes[MAX_PIPES][2];
            pid_t pids[MAX_PIPES];

            /* Create all pipes */
            for (int i = 0; i < num_cmds - 1; i++) {
                if (pipe(pipes[i]) < 0) { perror("pipe"); break; }
            }

            /* Fork and execute each command */
            for (int i = 0; i < num_cmds; i++) {
                char cmd_copy[MAX_LINE];
                strcpy(cmd_copy, pipe_cmds[i]);
                /* Trim leading spaces */
                char *cmd = cmd_copy;
                while (*cmd == ' ') cmd++;
                
                tokenize(cmd, args, " \t");

                int in_fd  = (i == 0) ? STDIN_FILENO  : pipes[i-1][0];
                int out_fd = (i == num_cmds-1) ? STDOUT_FILENO : pipes[i][1];

                pids[i] = fork();
                if (pids[i] == 0) {
                    /* Close all pipe ends we don't need */
                    for (int j = 0; j < num_cmds - 1; j++) {
                        if (j != i-1) close(pipes[j][0]);
                        if (j != i)   close(pipes[j][1]);
                    }
                    execute_command(args, in_fd, out_fd);
                }
            }

            /* Parent closes all pipe ends and waits for all children */
            for (int i = 0; i < num_cmds - 1; i++) {
                close(pipes[i][0]);
                close(pipes[i][1]);
            }
            for (int i = 0; i < num_cmds; i++) {
                waitpid(pids[i], NULL, 0);
            }
        }
    }
    return 0;
}
```

### Makefile for the Shell

```makefile
# Save as: projects/01-unix-shell/Makefile
CC = gcc
CFLAGS = -Wall -Wextra -g
TARGET = myshell

$(TARGET): main.c
	$(CC) $(CFLAGS) -o $(TARGET) main.c

clean:
	rm -f $(TARGET)

test:
	@echo "=== Running Shell Tests ==="
	@echo "ls -la | grep .c" | ./$(TARGET)
	@echo "echo hello world > /tmp/test.txt && cat /tmp/test.txt" | ./$(TARGET)
	@echo "Tests complete."
```

### Project README Template

```markdown
# 🐚 MyShell — Unix Shell Implementation

## What This Is
A Unix shell implemented in C as part of my Operating Systems learning journey.
This demonstrates understanding of: fork/exec/wait, pipes, I/O redirection,
and process management.

## Features
- ✅ Execute external commands (ls, cat, grep, etc.)
- ✅ Multi-level pipes (cmd1 | cmd2 | cmd3)
- ✅ Output redirection (cmd > file.txt)
- ✅ Input redirection (cmd < file.txt)  
- ✅ Built-in commands: cd, pwd, exit
- ✅ Zombie process prevention (proper wait())

## Architecture
[Include your architecture diagram here]

## How to Build and Run
    make
    ./myshell

## What I Learned
- fork() creates a copy of the current process
- execvp() replaces the child's code with the new program
- pipe() creates an anonymous in-memory channel
- dup2() redirects file descriptors to pipe ends
```

### 📝 Project 1 Documentation Checklist

- [ ] Code pushed to GitHub: `projects/01-unix-shell/`
- [ ] README.md with architecture diagram
- [ ] Blog post: **"I Built a Unix Shell from Scratch in C"** (publish on Dev.to/Hashnode)
- [ ] LinkedIn post with screenshot of your shell running a complex pipeline
- [ ] Add to your main `os-mastery-journey/README.md` portfolio page

---

---

# 🟠 PHASE 2: CONCURRENCY & SYNCHRONIZATION (Days 21–38)

> **Goal:** Understand and control what happens when multiple things run at the same time. This is the hardest part of systems programming and the part most likely to appear in senior engineering interviews.
>
> **The connecting thread:** You will study real disasters caused by concurrency bugs, learn the tools to prevent them, and build a User-Level Thread Library as Project 2.

---

## Days 21–22: What Is Concurrency? Race Conditions.

### The Core Problem

A **race condition** occurs when a program's behavior depends on the timing of events that you cannot control.

```c
/* Save as: phase-2-concurrency/race_demo.c
   gcc -o race_demo race_demo.c -lpthread && ./race_demo
   Run it multiple times. You'll get different answers each time.
*/
#include <stdio.h>
#include <pthread.h>
#include <stdlib.h>

int global_counter = 0;   /* SHARED variable — this is the danger */

void *increment_thread(void *arg) {
    for (int i = 0; i < 1000000; i++) {
        global_counter++;   /* This looks like one operation but IT IS NOT */
        /* The CPU actually does THREE steps:
           1. LOAD:  read global_counter from memory into a register
           2. ADD:   add 1 to the register value
           3. STORE: write register value back to memory
           If two threads are both doing this, they can interleave:
           Thread 1 LOADS (gets 5)
           Thread 2 LOADS (also gets 5, because Thread 1 hasn't stored yet)
           Thread 1 ADDS → register = 6
           Thread 2 ADDS → register = 6
           Thread 1 STORES 6
           Thread 2 STORES 6
           Result: 6, but we expected 7! One increment was LOST.
        */
    }
    return NULL;
}

int main() {
    pthread_t t1, t2;
    pthread_create(&t1, NULL, increment_thread, NULL);
    pthread_create(&t2, NULL, increment_thread, NULL);
    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
    printf("Expected: 2000000, Got: %d\n", global_counter);
    return 0;
}
```

### 📝 Documentation Task (Days 21-22)
- Run the race demo 5 times. Record the different values in `day-21.md`.
- Write: "The race condition happens because the `++` operation is not ___ (hint: the opposite of divisible). This means a thread can be ___ in the middle of it."

---

## Days 23–25: Locks, Mutexes, and Atomic Operations

### The Solution: Mutual Exclusion

```c
/* Save as: phase-2-concurrency/mutex_fix.c
   gcc -o mutex_fix mutex_fix.c -lpthread && ./mutex_fix
*/
#include <stdio.h>
#include <pthread.h>

int global_counter = 0;
pthread_mutex_t lock;    /* The mutex (mutual exclusion) lock */

void *safe_increment(void *arg) {
    for (int i = 0; i < 1000000; i++) {
        pthread_mutex_lock(&lock);   /* Acquire lock — only one thread at a time */
        global_counter++;            /* Critical section */
        pthread_mutex_unlock(&lock); /* Release lock */
    }
    return NULL;
}

int main() {
    pthread_mutex_init(&lock, NULL);
    pthread_t t1, t2;
    pthread_create(&t1, NULL, safe_increment, NULL);
    pthread_create(&t2, NULL, safe_increment, NULL);
    pthread_join(t1, NULL);
    pthread_join(t2, NULL);
    pthread_mutex_destroy(&lock);
    printf("Expected: 2000000, Got: %d\n", global_counter);
    return 0;
}
```

### Semaphores — More Powerful Than Mutexes

A **mutex** is a binary lock: one thread at a time. A **semaphore** is a counter: up to N threads at a time.

```c
/* Semaphore for the Producer-Consumer problem */
#include <semaphore.h>

sem_t empty_slots;    /* How many empty slots in buffer */
sem_t filled_slots;   /* How many filled slots in buffer */
pthread_mutex_t mutex; /* Protect the buffer itself */

void *producer(void *arg) {
    while (1) {
        int item = produce_item();
        sem_wait(&empty_slots);       /* Wait for an empty slot */
        pthread_mutex_lock(&mutex);
        buffer[in] = item;
        in = (in + 1) % BUFFER_SIZE;
        pthread_mutex_unlock(&mutex);
        sem_post(&filled_slots);      /* Signal: one more item available */
    }
}
```

---

## Days 26–27: Case Study — Mars Pathfinder (1997)

### The Real Story of Priority Inversion

In 1997, NASA's Mars Pathfinder landed successfully, then started resetting randomly. Engineers on Earth had to diagnose it remotely.

**The setup on Pathfinder:**
- Low-priority thread: Meteorological data collection (holds the bus mutex)
- Medium-priority thread: Communications (CPU-hungry, preempts others)
- High-priority thread: Bus management (needs the bus mutex to function)

**What happened:**
1. Low-priority thread grabs the bus mutex
2. High-priority thread wakes up, needs the bus mutex → BLOCKED (waiting for low-priority)
3. Medium-priority thread wakes up → preempts the low-priority thread (it has higher priority!)
4. Low-priority thread can't run to release the mutex
5. High-priority thread starves indefinitely
6. Watchdog timer: "High priority task isn't running → reset everything"

**The fix:** Priority Inheritance — when a low-priority thread holds a mutex that a high-priority thread needs, the low-priority thread temporarily inherits the high-priority, preventing medium-priority from preempting it.

```c
/* Priority Inheritance mutex in Linux */
pthread_mutexattr_t attr;
pthread_mutexattr_init(&attr);
pthread_mutexattr_setprotocol(&attr, PTHREAD_PRIO_INHERIT);
pthread_mutex_init(&mutex, &attr);
```

### 📝 Documentation Task (Days 26-27)
- Blog post: **"The Bug That Almost Crashed Mars Pathfinder: A Priority Inversion Story"**
- This is a perfect interview story. Practice explaining it out loud in under 2 minutes.
- LinkedIn: "Did you know a concurrency bug almost killed a Mars mission? I studied it today. [key insight]"

---

## Days 28–29: Deadlock

### The Four Conditions for Deadlock

All four must be true simultaneously for deadlock to occur:

1. **Mutual Exclusion**: Resources cannot be shared (one thread at a time)
2. **Hold and Wait**: Thread holds a resource while waiting for another
3. **No Preemption**: Resources cannot be forcibly taken away
4. **Circular Wait**: T1 waits for T2, T2 waits for T3, T3 waits for T1

```c
/* Classic deadlock: two threads, two locks, opposite order */
void *thread1(void *arg) {
    pthread_mutex_lock(&lock_A);    /* Gets lock A */
    sleep(1);                       /* Sleep increases chance of deadlock */
    pthread_mutex_lock(&lock_B);    /* Waits for lock B — DEADLOCK if t2 has it */
    /* ... do work ... */
    pthread_mutex_unlock(&lock_B);
    pthread_mutex_unlock(&lock_A);
    return NULL;
}

void *thread2(void *arg) {
    pthread_mutex_lock(&lock_B);    /* Gets lock B */
    sleep(1);
    pthread_mutex_lock(&lock_A);    /* Waits for lock A — DEADLOCK if t1 has it */
    /* ... do work ... */
    pthread_mutex_unlock(&lock_A);
    pthread_mutex_unlock(&lock_B);
    return NULL;
}

/* PREVENTION: Always acquire locks in the same order */
/* Both threads should always lock A before B */
```

---

## Days 30–33: The Thread Library Project (PROJECT 2 Kickoff)

### Real-World Problem This Solves
Python has threads. Java has threads. Go has goroutines. All of these, at their core, are built on the same mechanism you will implement: saving the CPU's registers and swapping to another set. Understanding this is what separates a "user of threads" from an "engineer who understands concurrency."

### Architecture

```
┌──────────────────────────────────────────────────────────────────┐
│               USER-LEVEL THREAD LIBRARY                          │
│                                                                  │
│  API (what the user calls):                                      │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │ uthread_create()  uthread_yield()  uthread_join()        │   │
│  │ uthread_exit()    uthread_self()                         │   │
│  └──────────────────────────────────────────────────────────┘   │
│                          │                                       │
│  Scheduler:                                                      │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  Ready Queue: [thread_A] [thread_B] [thread_C]           │   │
│  │  Running: [thread_A] ← currently executing               │   │
│  └──────────────────────────────────────────────────────────┘   │
│                          │                                       │
│  Context Switch (ASSEMBLY):                                      │
│  ┌──────────────────────────────────────────────────────────┐   │
│  │  Save: rsp, rbp, rbx, r12, r13, r14, r15 of current     │   │
│  │  Load: rsp, rbp, rbx, r12, r13, r14, r15 of next        │   │
│  └──────────────────────────────────────────────────────────┘   │
└──────────────────────────────────────────────────────────────────┘
```

### Thread Control Block Structure

```c
/* Save as: projects/02-thread-library/uthread.h */
#ifndef UTHREAD_H
#define UTHREAD_H

#include <stdint.h>

#define STACK_SIZE   (64 * 1024)    /* 64KB stack per thread */
#define MAX_THREADS  64

typedef enum {
    THREAD_READY,
    THREAD_RUNNING,
    THREAD_BLOCKED,
    THREAD_ZOMBIE,
} ThreadState;

/* Thread Control Block (TCB) — everything the scheduler needs to know */
typedef struct {
    int           tid;             /* Thread ID */
    ThreadState   state;           /* Current state */
    uint64_t     *stack;           /* Pointer to the stack (allocated with malloc) */
    uint64_t      stack_ptr;       /* Saved stack pointer (rsp) */
    
    /* Saved register state (callee-saved registers on x86-64) */
    uint64_t      rbp;
    uint64_t      rbx;
    uint64_t      r12, r13, r14, r15;
    
    void         *return_value;    /* Return value from thread function */
    int           join_tid;        /* Which thread is waiting for this one? */
} TCB;

/* Public API */
int  uthread_create(void *(*func)(void *), void *arg);
void uthread_yield(void);
void uthread_exit(void *retval);
int  uthread_join(int tid, void **retval);
int  uthread_self(void);

#endif
```

### The Context Switch in Assembly

```c
/* Save as: projects/02-thread-library/context_switch.S
   This is 15-20 lines of x86-64 assembly.
   It is the HEART of every thread system ever built.
*/

.text
.globl context_switch

/* context_switch(TCB *old_thread, TCB *new_thread)
   Arguments: rdi = old_thread, rsi = new_thread
*/
context_switch:
    /* SAVE current thread's registers into old_thread's TCB */
    movq  %rsp, 24(%rdi)    /* Save rsp (stack pointer) */
    movq  %rbp, 32(%rdi)    /* Save rbp (base pointer) */
    movq  %rbx, 40(%rdi)    /* Save rbx */
    movq  %r12, 48(%rdi)    /* Save r12 */
    movq  %r13, 56(%rdi)    /* Save r13 */
    movq  %r14, 64(%rdi)    /* Save r14 */
    movq  %r15, 72(%rdi)    /* Save r15 */

    /* RESTORE new thread's registers from new_thread's TCB */
    movq  24(%rsi), %rsp    /* Restore rsp */
    movq  32(%rsi), %rbp    /* Restore rbp */
    movq  40(%rsi), %rbx    /* Restore rbx */
    movq  48(%rsi), %r12    /* Restore r12 */
    movq  56(%rsi), %r13    /* Restore r13 */
    movq  64(%rsi), %r14    /* Restore r14 */
    movq  72(%rsi), %r15    /* Restore r15 */

    /* When we restore rsp, the CPU now uses the NEW thread's stack.
       The 'ret' instruction pops the return address from that stack,
       which is wherever the new thread was last executing. */
    ret
```

---

## Days 34–38: Complete the Thread Library

### Complete uthread.c Implementation

```c
/* projects/02-thread-library/uthread.c (simplified key parts) */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include "uthread.h"

static TCB threads[MAX_THREADS];
static int current_tid = -1;
static int next_tid = 0;

/* Assembly function from context_switch.S */
extern void context_switch(TCB *old_thread, TCB *new_thread);

void uthread_yield(void) {
    int old_tid = current_tid;
    
    /* Find next READY thread (round-robin) */
    int next = -1;
    for (int i = 1; i <= next_tid; i++) {
        int candidate = (old_tid + i) % (next_tid + 1);
        if (threads[candidate].state == THREAD_READY) {
            next = candidate;
            break;
        }
    }
    
    if (next == -1) return;  /* No other thread to run */
    
    threads[old_tid].state = THREAD_READY;
    threads[next].state    = THREAD_RUNNING;
    current_tid = next;
    
    /* THE MAGIC: switch CPU context to the new thread */
    context_switch(&threads[old_tid], &threads[next]);
    /* When this thread is scheduled again, execution resumes HERE */
}
```

### Test Your Thread Library

```c
/* projects/02-thread-library/test_uthread.c */
#include <stdio.h>
#include "uthread.h"

void *thread_function(void *arg) {
    int id = *(int *)arg;
    for (int i = 0; i < 5; i++) {
        printf("Thread %d: step %d\n", id, i);
        uthread_yield();    /* Voluntarily give up CPU */
    }
    return NULL;
}

int main() {
    int id1 = 1, id2 = 2, id3 = 3;
    int t1 = uthread_create(thread_function, &id1);
    int t2 = uthread_create(thread_function, &id2);
    int t3 = uthread_create(thread_function, &id3);
    
    uthread_join(t1, NULL);
    uthread_join(t2, NULL);
    uthread_join(t3, NULL);
    
    printf("All threads complete!\n");
    return 0;
}
```

### 📝 Project 2 Documentation Checklist

- [ ] Code in `projects/02-thread-library/`
- [ ] README with architecture diagram explaining the context switch
- [ ] Blog post: **"I Wrote a Thread Library in C. Here's How a Context Switch Actually Works."**
- [ ] Include the assembly code and explain each instruction in plain English
- [ ] LinkedIn update with the post link

---

---

# 🟢 PHASE 3: MEMORY MANAGEMENT (Days 39–52)

> **Goal:** Understand how the OS creates the illusion that every program has unlimited, private memory. Build your own `malloc`.
>
> **The connecting thread:** Days 39-45 are theory that directly enables you to build the custom malloc in Days 46-52.

---

## Days 39–40: Virtual Memory — The Illusion

### The Problem Virtual Memory Solves

Without virtual memory:
- Program A and Program B might accidentally share/overwrite each other's memory
- Programs would need to know their exact physical memory address (impossible)
- You couldn't run a program larger than physical RAM

Virtual memory creates a **private illusion**: every program thinks it owns ALL of memory (addresses 0 to ~2^48 on 64-bit systems). The OS transparently translates "virtual addresses" to "physical addresses" using hardware.

```
Process A thinks:            Physical RAM (actual hardware):
┌─────────────────┐          ┌─────────────────────────────┐
│ 0x0000: [code]  │──────►  │ 0x5000: [Process A's code]  │
│ 0x1000: [stack] │──────►  │ 0x9000: [Process A's stack] │
│ 0x2000: [heap]  │──────►  │ 0x1000: [Process A's heap]  │
└─────────────────┘          │                             │
                             │ 0x2000: [Process B's code]  │
Process B thinks:            │ 0x7000: [Process B's stack] │
┌─────────────────┐          │ 0x3000: [OS kernel]         │
│ 0x0000: [code]  │──────►  └─────────────────────────────┘
│ 0x1000: [stack] │
│ 0x2000: [heap]  │
└─────────────────┘

Both processes use address 0x0000, but they map to DIFFERENT physical locations.
The hardware (MMU = Memory Management Unit) does this translation on every access.
```

---

## Days 41–42: Paging and Page Tables

### How the Translation Works

Memory is divided into fixed-size chunks called **pages** (typically 4KB = 4096 bytes).

```
Virtual Address: 0x1234AB

Split it:
  [Virtual Page Number] [Page Offset]
  = [0x1234]           [0xAB]

The OS has a Page Table for this process:
  VPN 0x1234 → Physical Frame Number 0x5678

Physical Address = PFN 0x5678 | Offset 0xAB
                = 0x5678AB
```

### The TLB — The Hardware Cache for Translations

Looking up the page table in RAM takes ~100 ns. Memory accesses happen every few nanoseconds. The CPU would spend all its time translating, with no time for actual computation.

**Solution:** The TLB (Translation Lookaside Buffer) is a tiny, super-fast cache inside the CPU that stores recent VPN→PFN translations. Hit rate is typically >99%.

```bash
# Demonstrate TLB misses experimentally
cat << 'EOF' > tlb_demo.c
#include <stdio.h>
#include <stdlib.h>
#include <time.h>

#define PAGE_SIZE 4096
#define N_PAGES 4096

int main() {
    int *array = malloc(N_PAGES * PAGE_SIZE);
    struct timespec start, end;
    
    // Sequential access (TLB-friendly: same page many times)
    clock_gettime(CLOCK_MONOTONIC, &start);
    for (int i = 0; i < N_PAGES; i++)
        for (int j = 0; j < PAGE_SIZE/sizeof(int); j++)
            array[i * PAGE_SIZE/sizeof(int) + j] = 1;
    clock_gettime(CLOCK_MONOTONIC, &end);
    printf("Sequential: %ld ms\n", (end.tv_nsec - start.tv_nsec) / 1000000);

    // Strided access (TLB-thrashing: one element per page, many TLB misses)
    clock_gettime(CLOCK_MONOTONIC, &start);
    for (int i = 0; i < N_PAGES; i++)
        array[i * PAGE_SIZE/sizeof(int)] = 1;  // Jump one page each time
    clock_gettime(CLOCK_MONOTONIC, &end);
    printf("Strided:    %ld ms\n", (end.tv_nsec - start.tv_nsec) / 1000000);
    
    free(array);
    return 0;
}
EOF
gcc -O2 -o tlb_demo tlb_demo.c && ./tlb_demo
```

### 📝 Documentation Task (Days 41-42)
- Run the TLB demo. The strided access should be significantly slower.
- Write: "The TLB matters because ___. When you access memory in order (sequential), TLB hit rate is high because ___."

---

## Days 43–45: Page Faults, Swapping, and Virtual Memory Tricks

### Page Fault — The Controlled Crash

A **page fault** occurs when a program accesses a virtual address that has no corresponding physical frame. The CPU interrupts to the kernel, which handles it:

1. **Access to an unmapped page** → Allocate a new frame, update page table, retry
2. **Access to a swapped-out page** → Load from disk to RAM, update page table, retry
3. **Access to an illegal address** → Kill the process with SIGSEGV (segmentation fault)

### Copy-on-Write (COW) — How fork() is Actually Fast

When `fork()` is called, it doesn't copy ALL of the parent's memory:
1. Child gets its OWN page table, but each entry still points to the SAME physical frames as the parent
2. All shared pages are marked **read-only** in both parent and child
3. When either process tries to **write** to a shared page, a page fault triggers
4. The kernel then makes a **copy** of that specific page and updates one process's mapping
5. Only pages that are actually written get copied — pages that are only read are shared forever

This is why `fork()` is O(1) in time even though it "copies" a huge process.

---

## Days 46–52: Build a Custom Memory Allocator (PROJECT 3)

### Real-World Problem This Solves

`malloc()` is one of the most critical functions in any C program. Bad allocation causes:
- Memory leaks (forgetting to free → memory never returned to OS)
- Fragmentation (free memory exists but can't be used)
- Use-after-free bugs (using memory after freeing it → security vulnerabilities)

Google's `tcmalloc`, Facebook's `jemalloc`, and the Linux kernel's slab allocator are all custom memory allocators. Understanding how to build one is a core systems engineering skill.

### How Heap Memory Works

```
Your Process's Memory Layout:

High Address
┌──────────────────┐  ← Top of stack (grows DOWN)
│  Stack           │
│  (local vars,    │
│  function calls) │
│         ↓        │
│                  │
│   (gap)          │
│                  │
│         ↑        │
│  Heap            │  ← malloc() gives memory from here (grows UP)
│  (dynamic alloc) │
├──────────────────┤  ← Program break (sbrk() moves this up/down)
│  BSS Segment     │  (uninitialized global variables)
│  Data Segment    │  (initialized global variables)
│  Text Segment    │  (your compiled code)
Low Address
└──────────────────┘

sbrk(N): ask the OS to extend the heap by N bytes
mmap(NULL, N, ...): ask the OS for a completely new chunk of N bytes
```

### Block Structure for Your Allocator

```c
/* Every allocated/free block has this header + footer */
/*
 * [4 bytes: header][         user data         ][4 bytes: footer]
 *     ^                                               ^
 *     |← size + allocated bit                        |← same info
 *
 * The low bit of size is used as the "allocated" flag:
 * Header = (size | 1) if allocated, (size | 0) if free
 *
 * Example: a 32-byte free block:
 * [0x00000020][.....32 bytes of free space.....][0x00000020]
 * A 32-byte allocated block:
 * [0x00000021][.....32 bytes of user data.......][0x00000021]
 *
 * Free blocks form a doubly-linked list:
 * [header][prev_ptr][next_ptr][..padding..][footer]
 */
```

### Complete malloc Implementation

```c
/* Save as: projects/03-custom-malloc/mm.c */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <assert.h>
#include <unistd.h>   /* sbrk() */

/* ---- Configuration ---- */
#define ALIGNMENT       8         /* All allocations aligned to 8 bytes */
#define WSIZE           4         /* Word size: 4 bytes */
#define DSIZE           8         /* Double word: 8 bytes */
#define CHUNKSIZE      (1 << 12)  /* Extend heap by 4KB at a time */

/* ---- Macros to work with block headers/footers ---- */
#define ALIGN(size)     (((size) + (ALIGNMENT-1)) & ~(ALIGNMENT-1))
#define PACK(size, alloc) ((size) | (alloc))        /* Pack size+allocated bit */
#define GET(p)          (*(unsigned int *)(p))       /* Read a word from address p */
#define PUT(p, val)     (*(unsigned int *)(p) = (val))  /* Write a word */
#define GET_SIZE(p)     (GET(p) & ~0x7)              /* Get block size from header */
#define GET_ALLOC(p)    (GET(p) & 0x1)               /* Get allocated bit */
#define HDRP(bp)        ((char*)(bp) - WSIZE)        /* Header pointer from user ptr */
#define FTRP(bp)        ((char*)(bp) + GET_SIZE(HDRP(bp)) - DSIZE)  /* Footer ptr */
#define NEXT_BLKP(bp)   ((char*)(bp) + GET_SIZE(HDRP(bp)))          /* Next block */
#define PREV_BLKP(bp)   ((char*)(bp) - GET_SIZE((char*)(bp)-DSIZE)) /* Prev block */

static char *heap_listp = NULL;  /* Points to first block */

/* ---- Extend the heap by 'words' words ---- */
static void *extend_heap(size_t words) {
    char *bp;
    size_t size = (words % 2) ? (words + 1) * WSIZE : words * WSIZE;
    
    if ((bp = sbrk(size)) == (void *)-1) return NULL;
    
    PUT(HDRP(bp), PACK(size, 0));          /* Free block header */
    PUT(FTRP(bp), PACK(size, 0));          /* Free block footer */
    PUT(HDRP(NEXT_BLKP(bp)), PACK(0, 1)); /* New epilogue header */
    
    return coalesce(bp);
}

/* ---- Merge adjacent free blocks ---- */
static void *coalesce(void *bp) {
    size_t prev_alloc = GET_ALLOC(FTRP(PREV_BLKP(bp)));
    size_t next_alloc = GET_ALLOC(HDRP(NEXT_BLKP(bp)));
    size_t size = GET_SIZE(HDRP(bp));

    if (prev_alloc && next_alloc) {
        return bp;   /* Both neighbors allocated: nothing to merge */
    } else if (prev_alloc && !next_alloc) {
        /* Merge with next block */
        size += GET_SIZE(HDRP(NEXT_BLKP(bp)));
        PUT(HDRP(bp), PACK(size, 0));
        PUT(FTRP(bp), PACK(size, 0));
    } else if (!prev_alloc && next_alloc) {
        /* Merge with previous block */
        size += GET_SIZE(HDRP(PREV_BLKP(bp)));
        PUT(FTRP(bp), PACK(size, 0));
        PUT(HDRP(PREV_BLKP(bp)), PACK(size, 0));
        bp = PREV_BLKP(bp);
    } else {
        /* Merge with both neighbors */
        size += GET_SIZE(HDRP(PREV_BLKP(bp))) + GET_SIZE(FTRP(NEXT_BLKP(bp)));
        PUT(HDRP(PREV_BLKP(bp)), PACK(size, 0));
        PUT(FTRP(NEXT_BLKP(bp)), PACK(size, 0));
        bp = PREV_BLKP(bp);
    }
    return bp;
}

/* ---- Find a free block that fits 'asize' bytes (First Fit) ---- */
static void *find_fit(size_t asize) {
    void *bp;
    for (bp = heap_listp; GET_SIZE(HDRP(bp)) > 0; bp = NEXT_BLKP(bp)) {
        if (!GET_ALLOC(HDRP(bp)) && (asize <= GET_SIZE(HDRP(bp))))
            return bp;
    }
    return NULL;
}

/* ---- Place the allocation, split if remainder is large enough ---- */
static void place(void *bp, size_t asize) {
    size_t csize = GET_SIZE(HDRP(bp));
    if ((csize - asize) >= (2 * DSIZE)) {
        /* Block is big enough to split */
        PUT(HDRP(bp), PACK(asize, 1));
        PUT(FTRP(bp), PACK(asize, 1));
        bp = NEXT_BLKP(bp);
        PUT(HDRP(bp), PACK(csize - asize, 0));
        PUT(FTRP(bp), PACK(csize - asize, 0));
    } else {
        PUT(HDRP(bp), PACK(csize, 1));
        PUT(FTRP(bp), PACK(csize, 1));
    }
}

/* ---- PUBLIC API ---- */
int mm_init(void) {
    if ((heap_listp = sbrk(4 * WSIZE)) == (void *)-1) return -1;
    PUT(heap_listp, 0);                              /* Alignment padding */
    PUT(heap_listp + (1*WSIZE), PACK(DSIZE, 1));    /* Prologue header */
    PUT(heap_listp + (2*WSIZE), PACK(DSIZE, 1));    /* Prologue footer */
    PUT(heap_listp + (3*WSIZE), PACK(0, 1));        /* Epilogue header */
    heap_listp += (2 * WSIZE);
    return extend_heap(CHUNKSIZE/WSIZE) == NULL ? -1 : 0;
}

void *mm_malloc(size_t size) {
    if (size == 0) return NULL;
    size_t asize = ALIGN(size + DSIZE);   /* Add header/footer, align */
    
    void *bp = find_fit(asize);
    if (bp != NULL) {
        place(bp, asize);
        return bp;
    }
    /* No fit: extend heap */
    size_t extendsize = asize > CHUNKSIZE ? asize : CHUNKSIZE;
    if ((bp = extend_heap(extendsize/WSIZE)) == NULL) return NULL;
    place(bp, asize);
    return bp;
}

void mm_free(void *bp) {
    if (bp == NULL) return;
    size_t size = GET_SIZE(HDRP(bp));
    PUT(HDRP(bp), PACK(size, 0));
    PUT(FTRP(bp), PACK(size, 0));
    coalesce(bp);
}
```

### Benchmark Your malloc vs System malloc

```bash
# Compile and test
gcc -O2 -o malloc_test malloc_test.c mm.c

# Use valgrind to check for memory leaks
sudo apt install valgrind
valgrind --leak-check=full ./malloc_test

# Compare timing against system malloc
time ./malloc_test_system
time ./malloc_test_custom
```

### 📝 Project 3 Documentation Checklist

- [ ] Code in `projects/03-custom-malloc/`
- [ ] Valgrind shows zero memory leaks
- [ ] README explains what First Fit, splitting, and coalescing mean
- [ ] Blog post: **"I Wrote my own malloc(). Here's What Happens Inside Every Memory Allocation."**
- [ ] Include a diagram of heap layout with header/footer blocks

---

---

# 🔴 PHASE 4: FILE SYSTEMS & STORAGE (Days 53–63)

> **Goal:** Understand how files are stored on disk and how the OS guarantees they survive power outages.
>
> **The connecting thread:** You will build a toy file system stored in a single file, complete with format-on-disk structures.

---

## Days 53–54: Storage Hardware

### HDDs vs SSDs — Why It Matters for OS Design

**Hard Disk Drive (HDD) Physics:**
- Data stored on spinning magnetic platters
- A read head moves (seeks) to the right track
- The platter spins until the right sector comes under the head
- **Seek time: 3–10ms. Rotational latency: 0–4ms (average 2ms)**
- Sequential reads are 100x faster than random reads (the head doesn't need to move)

**Solid State Drive (SSD) Physics:**
- No moving parts. Data stored in flash memory cells.
- **NAND flash has a critical limitation:** You cannot overwrite a cell. You must **erase** the entire block first (512KB typically), then write.
- The **Flash Translation Layer (FTL)** inside the SSD hides this. It keeps a table mapping logical addresses to physical locations, enabling wear leveling.

```bash
# Measure your disk performance
sudo apt install fio
sudo fio --name=randread --ioengine=libaio --iodepth=16 \
    --rw=randread --bs=4k --direct=1 --size=1g --runtime=30 \
    --filename=/tmp/fio_test --output-format=normal
```

---

## Days 55–57: File System Internals

### The Three Pillars: Inodes, Bitmaps, and Data Blocks

```
Disk Layout for a Simple File System:
┌───────────┬──────────┬──────────┬──────────────────────────────┐
│ Superblock │  Inode   │  Block   │         Data Blocks           │
│           │  Bitmap  │  Bitmap  │  (actual file content)        │
│ (overall  │ (which   │ (which   │                              │
│  metadata)│ inodes   │ data     │ Block 0: [file A's data]     │
│           │ are used)│ blocks   │ Block 1: [file A's data]     │
│           │          │ are free)│ Block 2: [directory listing] │
│           │          │          │ Block 3: [file B's data]     │
└───────────┴──────────┴──────────┴──────────────────────────────┘

Superblock: size of disk, number of inodes, number of blocks

Inode (Index Node) for a file:
┌───────────────────────────────────────────────────┐
│ permissions: rw-r--r--                             │
│ size: 8192 bytes                                   │
│ owner: user1                                       │
│ created: 2024-01-01                               │
│ direct pointers: [block 5, block 9, block 12]     │  ← points to data blocks
│ indirect pointer: [block 20]                      │  ← block 20 contains MORE pointers
│ double indirect: [block 31]                       │  ← block of blocks of pointers
└───────────────────────────────────────────────────┘

When you type: cat myfile.txt
1. OS finds inode number for "myfile.txt" from the directory
2. OS reads the inode
3. Inode says data is in blocks 5, 9, 12
4. OS reads those 3 blocks in sequence
5. You see the file contents
```

### Crash Consistency: The Great Fear

What if power dies while writing? The file system could be left in a broken state.

**Journaling (ext4, NTFS, HFS+):**
1. Write a "transaction begin" record to the journal (a circular log)
2. Write all the data you intend to change to the journal
3. Write a "transaction commit" record to the journal
4. Now apply the changes to the real data structures
5. Mark the journal entry as complete

If power dies at any point before step 3: the transaction is incomplete. On reboot, discard it. The file system is in its old, consistent state (the operation just didn't happen).
If power dies after step 3: on reboot, replay the journal to finish the operation.

---

## Days 58–63: Build a Toy File System (PROJECT 4)

### Architecture

```
Your Single-File "Disk":
┌──────────────────────────────────────────────────┐
│ myfs.img (10MB file — pretend this is a disk)   │
│                                                  │
│ Bytes 0-511:       Superblock                    │
│ Bytes 512-1023:    Inode bitmap (which inodes    │
│                    are allocated)                │
│ Bytes 1024-1535:   Block bitmap (which data      │
│                    blocks are allocated)         │
│ Bytes 1536-3583:   Inode table (128 inodes,     │
│                    each 16 bytes)                │
│ Bytes 4096+:       Data blocks (4KB each)        │
└──────────────────────────────────────────────────┘
```

```c
/* Save as: projects/04-toy-filesystem/fs.h */
#include <stdint.h>
#include <time.h>

#define BLOCK_SIZE      4096
#define MAX_INODES      128
#define MAX_BLOCKS      2560       /* 10MB / 4KB */
#define DIRECT_BLOCKS   12
#define MAX_FILENAME    28

/* On-disk structures (everything stored exactly as these bytes on disk) */

typedef struct {
    uint32_t magic;            /* 0xDEADBEEF — identify our FS */
    uint32_t total_blocks;
    uint32_t total_inodes;
    uint32_t free_blocks;
    uint32_t free_inodes;
    uint32_t inode_start;      /* Block number where inodes begin */
    uint32_t data_start;       /* Block number where data begins */
} __attribute__((packed)) Superblock;

typedef struct {
    uint32_t mode;             /* File type and permissions */
    uint32_t uid;              /* Owner user ID */
    uint32_t size;             /* File size in bytes */
    uint32_t atime;            /* Last access time */
    uint32_t mtime;            /* Last modification time */
    uint32_t ctime;            /* Last status change time */
    uint32_t links;            /* Number of hard links */
    uint32_t blocks[DIRECT_BLOCKS]; /* Pointers to data blocks */
    uint32_t indirect;         /* Pointer to block of block pointers */
} __attribute__((packed)) Inode;

typedef struct {
    uint32_t inode_num;
    char name[MAX_FILENAME];
} __attribute__((packed)) DirEntry;

/* In-memory disk handle */
typedef struct {
    int fd;                /* File descriptor for the disk image */
    Superblock sb;
    uint8_t inode_bitmap[MAX_INODES / 8];
    uint8_t block_bitmap[MAX_BLOCKS / 8];
} Filesystem;

/* API */
Filesystem* fs_format(const char *disk_path);
Filesystem* fs_mount(const char *disk_path);
int fs_create(Filesystem *fs, const char *path);
int fs_write(Filesystem *fs, int inum, const void *buf, size_t len, off_t offset);
int fs_read(Filesystem *fs, int inum, void *buf, size_t len, off_t offset);
int fs_mkdir(Filesystem *fs, const char *path);
void fs_ls(Filesystem *fs, int dir_inum);
```

### mkfs — Format the Disk

```c
/* projects/04-toy-filesystem/mkfs.c */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <fcntl.h>
#include <unistd.h>
#include "fs.h"

Filesystem* fs_format(const char *disk_path) {
    /* Create a 10MB disk image */
    int fd = open(disk_path, O_RDWR | O_CREAT | O_TRUNC, 0644);
    if (fd < 0) { perror("open"); return NULL; }
    
    /* Seek to 10MB and write one byte to create the file size */
    lseek(fd, 10 * 1024 * 1024 - 1, SEEK_SET);
    write(fd, "\0", 1);
    lseek(fd, 0, SEEK_SET);

    /* Initialize superblock */
    Superblock sb = {
        .magic        = 0xDEADBEEF,
        .total_blocks = MAX_BLOCKS,
        .total_inodes = MAX_INODES,
        .free_blocks  = MAX_BLOCKS - 4,  /* Reserve 4 blocks for metadata */
        .free_inodes  = MAX_INODES - 1,  /* Reserve inode 0 for root dir */
        .inode_start  = 1,               /* Inodes start at block 1 */
        .data_start   = 4,               /* Data starts at block 4 */
    };
    
    pwrite(fd, &sb, sizeof(sb), 0);   /* Write superblock at byte 0 */

    /* Create root directory inode (inode 0) */
    Inode root_inode = {0};
    root_inode.mode  = 0x4000 | 0755; /* Directory | permissions */
    root_inode.links = 2;             /* . and .. */
    root_inode.size  = 0;
    /* ... allocate a data block for the directory entries ... */

    Filesystem *fs = malloc(sizeof(Filesystem));
    fs->fd = fd;
    fs->sb = sb;
    memset(fs->inode_bitmap, 0, sizeof(fs->inode_bitmap));
    memset(fs->block_bitmap, 0, sizeof(fs->block_bitmap));
    fs->inode_bitmap[0] |= 0x01;  /* Mark inode 0 (root) as used */

    printf("Formatted %s: %d blocks, %d inodes, magic=0x%08X\n",
           disk_path, sb.total_blocks, sb.total_inodes, sb.magic);
    return fs;
}
```

### 📝 Project 4 Documentation Checklist

- [ ] Implement: `fs_format`, `fs_mount`, `fs_create`, `fs_write`, `fs_read`, `fs_ls`
- [ ] Demo: create 5 files, write data, unmount, remount, read data back (proves persistence)
- [ ] Blog post: **"I Built a File System Stored in a Single File. Here's How Inodes Actually Work."**
- [ ] Diagram showing your exact on-disk byte layout

---

---

# 🟣 PHASE 5: DISTRIBUTED SYSTEMS (Days 64–76)

> **Goal:** Scale from one machine to many. Build a distributed key-value store.
>
> **Why this matters for MNCs:** AWS, Google Cloud, and Azure are fundamentally distributed systems. Understanding CAP theorem, consensus, and sharding is table stakes for cloud roles.

---

## Days 64–65: CAP Theorem and Distributed Systems Basics

### The CAP Theorem — The Three-Way Tradeoff

In a distributed system (multiple computers), you can only **guarantee 2 of these 3**:

- **C**onsistency: Every read gets the most recent write
- **A**vailability: Every request gets a response (not an error)
- **P**artition Tolerance: System works even if network connections between nodes fail

Since network partitions (nodes can't talk to each other) **will always happen**, you must choose:

- **CP (Consistent + Partition Tolerant)**: HBase, ZooKeeper, etcd. During a partition, refuse requests rather than give stale data.
- **AP (Available + Partition Tolerant)**: DynamoDB, Cassandra, DNS. During a partition, return possibly stale data rather than refuse.

There is no right answer. It depends entirely on your use case.

```bash
# Install etcd (a real CP distributed key-value store by CoreOS/Google)
# It powers Kubernetes. It is CP: uses Raft consensus.
sudo apt install etcd

# Start a single-node etcd
etcd &

# Use it
etcdctl put mykey "hello"
etcdctl get mykey
```

---

## Days 66–68: The Raft Consensus Algorithm

### Why Consensus Matters

In a distributed system, all nodes need to agree on: "What is the current state?" If node A says the value is X and node B says it's Y, the system is broken. Raft is an algorithm for reaching agreement even when some nodes fail.

**Three roles in Raft:**
- **Leader**: Accepts all writes. Replicates to followers.
- **Follower**: Accepts writes only from the leader.
- **Candidate**: Trying to become a leader (happens after leader failure)

**Leader Election:**
1. Each follower has a random timeout (150-300ms)
2. If a follower doesn't hear from a leader, it becomes a Candidate
3. Candidate sends RequestVote to all nodes
4. If a majority vote for it, it becomes Leader
5. Leader sends heartbeats to prevent new elections

Visualize this live: https://raft.github.io

---

## Days 69–76: Distributed Key-Value Store (PROJECT 5)

### Architecture

```
Distributed Key-Value Store (3 nodes):

┌─────────────────┐   ┌─────────────────┐   ┌─────────────────┐
│   Node 0        │   │   Node 1        │   │   Node 2        │
│   Port 8000     │   │   Port 8001     │   │   Port 8002     │
│   (LEADER)      │   │   (FOLLOWER)    │   │   (FOLLOWER)    │
│                 │   │                 │   │                 │
│  {A: 1, B: 2}  │   │  {A: 1, B: 2}  │   │  {A: 1, B: 2}  │
│  {C: 3}        │   │  {C: 3}        │   │  {C: 3}        │
└────────┬────────┘   └────────┬────────┘   └────────┬────────┘
         │    Raft replication │                      │
         └─────────────────────┼──────────────────────┘
                               │
               All writes go to Leader.
               Leader replicates to 2+ nodes before confirming.
               If Leader dies, followers elect a new one.

Client API:
  PUT key value  → Goes to Leader → replicated → "OK"
  GET key        → Any node can answer → "value"
```

### Tech Stack: gRPC + Protocol Buffers

```bash
# Install gRPC and protobuf (Google's tech, used everywhere)
pip3 install grpcio grpcio-tools

# Define the API in a .proto file
cat << 'EOF' > kvstore.proto
syntax = "proto3";

service KVStore {
  rpc Put(PutRequest)    returns (PutResponse);
  rpc Get(GetRequest)    returns (GetResponse);
  rpc Delete(DelRequest) returns (DelResponse);
}

message PutRequest  { string key = 1; string value = 2; }
message PutResponse { bool success = 1; string error = 2; }
message GetRequest  { string key = 1; }
message GetResponse { string value = 1; bool found = 2; }
message DelRequest  { string key = 1; }
message DelResponse { bool success = 1; }
EOF

# Generate Python code from the proto definition
python3 -m grpc_tools.protoc -I. --python_out=. --grpc_python_out=. kvstore.proto
```

### Server Implementation

```python
# Save as: projects/05-distributed-kvstore/server.py
import grpc
import time
import threading
import random
import logging
from concurrent import futures
import kvstore_pb2
import kvstore_pb2_grpc

logging.basicConfig(level=logging.INFO)

class KVStoreServicer(kvstore_pb2_grpc.KVStoreServicer):
    def __init__(self, node_id, peers):
        self.node_id = node_id
        self.peers = peers          # List of (host, port) for other nodes
        self.store = {}             # The actual key-value data
        self.lock = threading.Lock()
        self.is_leader = (node_id == 0)   # Simplified: node 0 starts as leader
        
    def Put(self, request, context):
        """Handle PUT requests. Only leader accepts writes."""
        if not self.is_leader:
            context.abort(grpc.StatusCode.FAILED_PRECONDITION, 
                         "Not the leader. Redirect to leader.")
            return kvstore_pb2.PutResponse(success=False)
        
        # Replicate to all followers first (simplified: no Raft here)
        # In real Raft: must replicate to majority before committing
        success_count = 1  # Count self
        for host, port in self.peers:
            try:
                with grpc.insecure_channel(f"{host}:{port}") as channel:
                    stub = kvstore_pb2_grpc.KVStoreStub(channel)
                    # In real implementation: send AppendEntries RPC
                    pass
                success_count += 1
            except Exception as e:
                logging.warning(f"Replication to {host}:{port} failed: {e}")
        
        # Commit to local store
        with self.lock:
            self.store[request.key] = request.value
        
        logging.info(f"[Node {self.node_id}] PUT {request.key}={request.value}")
        return kvstore_pb2.PutResponse(success=True)
    
    def Get(self, request, context):
        """GET can be served from any node."""
        with self.lock:
            value = self.store.get(request.key)
        if value is None:
            return kvstore_pb2.GetResponse(value="", found=False)
        return kvstore_pb2.GetResponse(value=value, found=True)


def serve(node_id, port, peers):
    server = grpc.server(futures.ThreadPoolExecutor(max_workers=10))
    kvstore_pb2_grpc.add_KVStoreServicer_to_server(
        KVStoreServicer(node_id, peers), server)
    server.add_insecure_port(f"[::]:{port}")
    server.start()
    logging.info(f"Node {node_id} started on port {port}")
    server.wait_for_termination()

if __name__ == "__main__":
    import sys
    node_id = int(sys.argv[1])
    ports = [8000, 8001, 8002]
    port = ports[node_id]
    peers = [(("localhost", p)) for i, p in enumerate(ports) if i != node_id]
    serve(node_id, port, peers)
```

### Run 3 Nodes with Docker

```yaml
# Save as: projects/05-distributed-kvstore/docker-compose.yml
version: '3'
services:
  node0:
    build: .
    command: python3 server.py 0
    ports:
      - "8000:8000"
    networks:
      - kvnet
  node1:
    build: .
    command: python3 server.py 1
    ports:
      - "8001:8001"
    networks:
      - kvnet
  node2:
    build: .
    command: python3 server.py 2
    ports:
      - "8002:8002"
    networks:
      - kvnet
networks:
  kvnet:
```

```bash
# Start all 3 nodes
docker-compose up

# Test the cluster from another terminal
python3 client.py put hello world
python3 client.py get hello
# Kill node 1 and verify data is still accessible
docker-compose stop node1
python3 client.py get hello    # Should still work
```

### 📝 Project 5 Documentation Checklist

- [ ] 3-node cluster running with Docker Compose
- [ ] CLI client to PUT and GET values
- [ ] Test: kill one node, show data is still accessible
- [ ] Blog post: **"I Built a Distributed Database from Scratch. Here's What CAP Theorem Actually Means."**
- [ ] Architecture diagram showing Raft leader election

---

---

# ⚫ PHASE 6: AI + FUTURE SYSTEMS (Days 77–90)

> **Goal:** Understand the research frontier of OS engineering and build an AI-enhanced system component.
>
> **Why this matters:** This separates a "senior engineer" from a "staff engineer" in interviews. Knowing eBPF, Spectre/Meltdown mitigations, and AI-in-OS shows you follow the frontier.

---

## Days 77–78: Meltdown & Spectre — When Hardware Lies

### The Vulnerability (Simplified)

Modern CPUs are **speculative**: they guess what the program will do next and execute instructions in advance. If the guess is wrong, the results are discarded. But the data was loaded into the CPU cache.

**Meltdown (2018):**
1. Attacker program reads kernel memory address X (should be illegal)
2. CPU speculatively loads the value before checking permissions
3. Permission check fails → CPU discards the result
4. BUT: the data is now in the L1 cache!
5. Attacker measures how long it takes to access different user-space addresses
6. Cache hit = fast = that was the value. Cache miss = slow.
7. Attacker has now read secret kernel data.

**The Fix: KPTI (Kernel Page Table Isolation)**
Separate user and kernel page tables completely. In user mode, the kernel's virtual addresses simply don't exist. The CPU cannot speculatively read from an address that isn't even mapped.

**Performance cost:** Every system call requires switching page tables → TLB flush. Early patches slowed some systems 5-30%.

```bash
# Check if your system has KPTI enabled
cat /sys/devices/system/cpu/vulnerabilities/meltdown
cat /sys/devices/system/cpu/vulnerabilities/spectre_v2
```

---

## Days 79–80: eBPF — The Programmable Kernel

### What eBPF Is

eBPF (Extended Berkeley Packet Filter) lets you load small, safe programs INTO the Linux kernel without modifying kernel source code or rebooting.

Think of it as: "Plugins for the kernel."

Netflix, Google, Meta, and Cloudflare use eBPF to:
- Profile applications with zero overhead
- Filter network packets at wire speed
- Monitor security events in real-time
- Debug production systems safely

```bash
# Install bpftrace (the high-level eBPF language)
sudo apt install bpftrace

# Count how many times each system call is called (system-wide!)
sudo bpftrace -e 'tracepoint:syscalls:sys_enter_* { @[probe] = count(); }' &
sleep 10
kill %1

# Trace every time a file is opened
sudo bpftrace -e 'tracepoint:syscalls:sys_enter_openat { printf("%s opened %s\n", comm, str(args->filename)); }'

# Histogram of read() sizes (in bytes)
sudo bpftrace -e 'tracepoint:syscalls:sys_enter_read { @bytes = hist(args->count); }'
```

---

## Days 81–83: AI in Operating Systems

### SchedCP — LLM-Based Scheduling

Traditional schedulers are blind to what programs are doing. SchedCP (2024 research) uses an LLM to:
1. Read system performance counters (CPU usage, cache misses, I/O wait)
2. Infer the workload's "intent" (is this a web server? A database? A batch job?)
3. Generate custom eBPF code to tune the scheduler for that specific workload

This achieves better tail latency and throughput than hand-tuned CFS parameters.

### Google's Llama — AI Memory Allocator

tcmalloc and jemalloc use static rules to decide which allocator bin to use. Google's Llama (2023) uses a neural network to predict the **lifetime** of an allocation at the moment of malloc():

- Short-lived objects → grouped together → when they all die, the entire huge page can be freed
- Long-lived objects → separate area → doesn't pollute the short-lived region's pages

Result: 10-15% reduction in fragmentation on production servers.

---

## Days 84–90: AI-Powered Semantic Scheduler (PROJECT 6)

### The Problem We're Solving

The Linux CFS scheduler doesn't know what a process IS. A web server and a video encoder have the same scheduling policy: share CPU time fairly based on vruntime.

But they have very different needs:
- Web server: needs LOW LATENCY (fast response per request)
- Video encoder: needs HIGH THROUGHPUT (total encoding speed doesn't care about response time)

### Your Solution: eBPF + ML Classifier

```
┌─────────────────────────────────────────────────────────────────┐
│                  SEMANTIC SCHEDULER ARCHITECTURE                 │
│                                                                  │
│  ┌──────────────────────┐                                        │
│  │  eBPF Observer       │                                        │
│  │  (runs inside kernel)│   Collects per-process signals:       │
│  │                      │   • syscall names and frequency       │
│  │  Attaches to:        │   • I/O wait time                     │
│  │  • sys_enter_read    │   • CPU burst length                  │
│  │  • sys_enter_write   │   • Context switch rate               │
│  │  • sys_enter_recv    │                                        │
│  └──────────┬───────────┘                                        │
│             │ (shared BPF map → user space)                      │
│             ▼                                                    │
│  ┌──────────────────────┐                                        │
│  │  Python ML Daemon    │   Classifies workload type:           │
│  │  (runs in user space)│   • Interactive (web server, shell)   │
│  │                      │   • Compute-bound (encoder, compiler) │
│  │  Uses sklearn or     │   • I/O-bound (database, backup)      │
│  │  a tiny neural net   │                                        │
│  └──────────┬───────────┘                                        │
│             │                                                    │
│             ▼                                                    │
│  ┌──────────────────────┐                                        │
│  │  Nice Value Adjuster │   Applies classification:             │
│  │                      │   • Interactive → nice -10 (high pri) │
│  │  Uses setpriority()  │   • I/O-bound → nice 0 (normal)      │
│  │  or sched_setattr()  │   • Batch → nice +10 (low priority)  │
│  └──────────────────────┘                                        │
└─────────────────────────────────────────────────────────────────┘
```

### Collect Data with eBPF

```bash
# syscall_monitor.bt — collect per-process syscall data
# Save as: projects/06-semantic-scheduler/syscall_monitor.bt

#!/usr/bin/env bpftrace

/* Count network-related syscalls per process */
tracepoint:syscalls:sys_enter_recvfrom,
tracepoint:syscalls:sys_enter_sendto {
    @net_syscalls[pid, comm] = count();
}

/* Count disk-related syscalls per process */
tracepoint:syscalls:sys_enter_read,
tracepoint:syscalls:sys_enter_write {
    @io_syscalls[pid, comm] = count();
}

/* Every 5 seconds, dump the stats */
interval:s:5 {
    print(@net_syscalls);
    print(@io_syscalls);
    clear(@net_syscalls);
    clear(@io_syscalls);
}
```

### Python ML Classifier

```python
# Save as: projects/06-semantic-scheduler/classifier.py
import subprocess
import time
import os
import re
from collections import defaultdict

# For a real ML classifier, use sklearn:
# pip install scikit-learn numpy
import numpy as np
from sklearn.ensemble import RandomForestClassifier

class WorkloadClassifier:
    def __init__(self):
        # Training data: [net_ratio, io_ratio, cpu_ratio] → label
        X_train = [
            [0.8, 0.1, 0.1],   # network-heavy → "interactive"
            [0.7, 0.2, 0.1],   # network-heavy → "interactive"
            [0.1, 0.1, 0.8],   # cpu-heavy → "compute-bound"
            [0.1, 0.1, 0.9],   # cpu-heavy → "compute-bound"
            [0.1, 0.8, 0.1],   # io-heavy → "io-bound"
            [0.2, 0.7, 0.1],   # io-heavy → "io-bound"
        ]
        y_train = ["interactive", "interactive", 
                   "compute", "compute",
                   "io-bound", "io-bound"]
        
        self.model = RandomForestClassifier(n_estimators=10)
        self.model.fit(X_train, y_train)
        print("Classifier trained.")

    def classify(self, net_count, io_count, cpu_estimate):
        total = net_count + io_count + cpu_estimate + 0.001
        features = [[net_count/total, io_count/total, cpu_estimate/total]]
        return self.model.predict(features)[0]

    def apply_priority(self, pid, workload_type):
        """Adjust process priority based on workload type."""
        nice_values = {
            "interactive": -5,    # Higher priority
            "compute":      5,    # Normal priority
            "io-bound":    10,    # Lower priority
        }
        nice = nice_values.get(workload_type, 0)
        try:
            os.setpriority(os.PRIO_PROCESS, pid, nice)
            print(f"[Scheduler] PID {pid}: classified as '{workload_type}', "
                  f"set nice={nice}")
        except PermissionError:
            print(f"[Scheduler] Need root to change priority of PID {pid}")


def monitor_loop():
    """Main monitoring loop."""
    classifier = WorkloadClassifier()
    process_stats = defaultdict(lambda: {"net": 0, "io": 0})
    
    print("Semantic Scheduler running. Monitoring all processes...")
    while True:
        # In a real system: read from BPF maps
        # Here: use /proc to estimate
        for pid_str in os.listdir("/proc"):
            if not pid_str.isdigit():
                continue
            pid = int(pid_str)
            try:
                with open(f"/proc/{pid}/status") as f:
                    status = f.read()
                name = re.search(r"Name:\s+(\S+)", status)
                if name:
                    name = name.group(1)
                    # Simplified: use I/O stats from /proc
                    io_path = f"/proc/{pid}/io"
                    if os.path.exists(io_path):
                        with open(io_path) as f:
                            io_data = f.read()
                        rchar = int(re.search(r"rchar:\s+(\d+)", io_data).group(1))
                        wchar = int(re.search(r"wchar:\s+(\d+)", io_data).group(1))
                        
                        prev_io = process_stats[pid]["io"]
                        io_delta = (rchar + wchar) - prev_io
                        process_stats[pid]["io"] = rchar + wchar
                        
                        if io_delta > 10000:  # Significant I/O activity
                            wtype = classifier.classify(0, io_delta, 1)
                            classifier.apply_priority(pid, wtype)
            except (PermissionError, FileNotFoundError, AttributeError):
                continue
        
        time.sleep(5)

if __name__ == "__main__":
    monitor_loop()
```

### 📝 Project 6 Documentation Checklist

- [ ] eBPF script collecting per-process syscall counts
- [ ] Python ML daemon classifying and adjusting priorities
- [ ] Demo video or GIF showing it working
- [ ] Blog post: **"I Built an AI-Powered CPU Scheduler. Here's How OS + ML Come Together."**
- [ ] This is your CAPSTONE. Write the best, most detailed README of your entire journey.

---

---

# 📊 COMPLETE DAILY TIMETABLE

## Phase 0: Survival Skills (Days 0–7)

| Day | Morning (1.5 hrs) | Afternoon (2 hrs) | Evening (1 hr) | Output |
|-----|-------------------|-------------------|----------------|--------|
| **0** | Set up Ubuntu + tools | Create GitHub repo | LinkedIn Day 0 post | Environment ready |
| **1** | Linux terminal Part 1 | Explore /proc filesystem | `day-01.md` | Push to GitHub |
| **2** | Linux terminal Part 2 | Write shell script | `day-02.md` | Blog draft |
| **3** | Python basics Part 1 | FCFS simulation | `day-03.md` | Push code |
| **4** | Python classes (PCB model) | Process state machine | `day-04.md` | Push code |
| **5** | C basics + pointers | C programs | `day-05.md` | Push code |
| **6** | C structs + malloc | Linked list of PCBs | `day-06.md` | Push code |
| **7** | Git workflow | Write first blog post | Publish on Dev.to | **Phase 0 ✅** |

## Phase 1: Kernel & Processes (Days 8–20)

| Day | Morning (1.5 hrs) | Afternoon (2 hrs) | Evening (1 hr) | Output |
|-----|-------------------|-------------------|----------------|--------|
| **8** | What is an OS? Von Neumann | Explore /proc, strace | `day-08.md` | LinkedIn |
| **9** | CPU rings, kernel/user mode | strace live demo | `day-09.md` | |
| **10** | Processes + PCB | fork() demo | `day-10.md` | Push |
| **11** | Scheduling: FCFS, SJF, RR | Python scheduling sim | `day-11.md` | |
| **12** | MLFQ deep dive | MLFQ Python simulation | `day-12.md` | Push |
| **13** | Linux CFS, vruntime | Read /proc/sched_debug | `day-13.md` | |
| **14** | CFS + Red-Black Trees | Kernel source reading | `day-14.md` | Blog post |
| **15** | xv6 setup | Compile and boot xv6 | `day-15.md` | |
| **16** | xv6 source: proc.h, proc.c | Trace a syscall in xv6 | `day-16.md` | |
| **17** | Add syscall to xv6 | Test your xv6 mod | `day-17.md` | Push xv6-mods repo |
| **18** | Shell architecture design | Write tokenizer + REPL | `day-18.md` | |
| **19** | Shell: fork+exec pipeline | Add pipe support | `day-19.md` | |
| **20** | Shell: redirection + signals | Test + document shell | README.md | **Project 1 ✅** |

## Phase 2: Concurrency & Synchronization (Days 21–38)

| Day | Morning (1.5 hrs) | Afternoon (2 hrs) | Evening (1 hr) | Output |
|-----|-------------------|-------------------|----------------|--------|
| **21** | Threads, race conditions | Race condition demo | `day-21.md` | |
| **22** | Why race conditions happen | Multiple runs, record results | `day-22.md` | |
| **23** | Locks, mutex, test-and-set | Mutex fix demo | `day-23.md` | |
| **24** | Semaphores | Producer-Consumer | `day-24.md` | |
| **25** | Condition variables | Bounded buffer | `day-25.md` | Blog post |
| **26** | Mars Pathfinder case study | Explain priority inversion | `day-26.md` | LinkedIn |
| **27** | Priority inheritance | Implement priority mutex | `day-27.md` | |
| **28** | Deadlock theory | Deadlock demo code | `day-28.md` | |
| **29** | Therac-25 case study | Study & document | `day-29.md` | Blog post |
| **30** | Thread library architecture | Design TCB struct | `day-30.md` | |
| **31** | x86-64 calling convention | Study assembly | `day-31.md` | |
| **32** | uthread_create() | Stack allocation | `day-32.md` | Push |
| **33** | context_switch assembly | Write .S file | `day-33.md` | |
| **34** | uthread_yield(), scheduler | Round-robin scheduler | `day-34.md` | |
| **35** | uthread_join(), uthread_exit() | Complete API | `day-35.md` | |
| **36** | Lock-free programming, CAS | Lock-free stack | `day-36.md` | |
| **37** | Event loops, epoll | Single-threaded server | `day-37.md` | |
| **38** | Test + document thread lib | Write README + test | README.md | **Project 2 ✅** |

## Phase 3: Memory Management (Days 39–52)

| Day | Morning (1.5 hrs) | Afternoon (2 hrs) | Evening (1 hr) | Output |
|-----|-------------------|-------------------|----------------|--------|
| **39** | Virtual memory concept | Memory layout diagram | `day-39.md` | |
| **40** | Address space layout | Read /proc/PID/maps | `day-40.md` | |
| **41** | Paging, page tables | Page table walk | `day-41.md` | |
| **42** | TLB, locality of reference | TLB miss experiment | `day-42.md` | Blog |
| **43** | Page faults, demand paging | Trigger a segfault | `day-43.md` | |
| **44** | Copy-on-write | Study fork() COW | `day-44.md` | |
| **45** | Page replacement: LRU, Clock | Python LRU simulator | `day-45.md` | |
| **46** | malloc architecture | Heap layout diagram | `day-46.md` | |
| **47** | sbrk(), mmap() | Request memory from OS | `day-47.md` | Push |
| **48** | Free list, headers/footers | Block structure code | `day-48.md` | |
| **49** | First fit, coalescing | find_fit() + coalesce() | `day-49.md` | |
| **50** | place(), splitting | Split large blocks | `day-50.md` | |
| **51** | mm_free(), realloc() | Complete allocator | `day-51.md` | |
| **52** | Benchmark + Valgrind | Test for leaks | README.md | **Project 3 ✅** |

## Phase 4: File Systems (Days 53–63)

| Day | Morning (1.5 hrs) | Afternoon (2 hrs) | Evening (1 hr) | Output |
|-----|-------------------|-------------------|----------------|--------|
| **53** | HDD vs SSD physics | Run fio benchmark | `day-53.md` | |
| **54** | Flash Translation Layer | Research wear leveling | `day-54.md` | |
| **55** | Inodes, bitmaps, superblock | Explore ext4 with dumpe2fs | `day-55.md` | Blog |
| **56** | Crash consistency problem | Simulate power failure | `day-56.md` | |
| **57** | Journaling (write-ahead log) | Study ext4 journal | `day-57.md` | |
| **58** | FS architecture design | Design disk layout | `day-58.md` | |
| **59** | fs_format() + mkfs | Create disk image | `day-59.md` | Push |
| **60** | Inode allocation, bitmaps | fs_create() | `day-60.md` | |
| **61** | fs_write(), fs_read() | Read/write implementation | `day-61.md` | |
| **62** | Directories, fs_ls() | Directory entries | `day-62.md` | |
| **63** | Persistence test + README | Mount, write, unmount, remount | README.md | **Project 4 ✅** |

## Phase 5: Distributed Systems (Days 64–76)

| Day | Morning (1.5 hrs) | Afternoon (2 hrs) | Evening (1 hr) | Output |
|-----|-------------------|-------------------|----------------|--------|
| **64** | Distributed basics | Lamport clocks | `day-64.md` | |
| **65** | CAP Theorem | Analyze DynamoDB vs HBase | `day-65.md` | Blog |
| **66** | Raft algorithm | raft.github.io visualization | `day-66.md` | |
| **67** | Raft leader election | Trace election steps | `day-67.md` | |
| **68** | gRPC + Protobuf | Write kvstore.proto | `day-68.md` | |
| **69** | KV store architecture | Design node diagram | `day-69.md` | Push |
| **70** | gRPC server implementation | Single-node working | `day-70.md` | |
| **71** | Consistent hashing | Hash ring implementation | `day-71.md` | |
| **72** | Replication basics | Leader-follower replication | `day-72.md` | |
| **73** | Fault tolerance | Simulate node death | `day-73.md` | |
| **74** | Docker Compose cluster | 3-node cluster running | `day-74.md` | |
| **75** | Client CLI tool | Test all operations | `day-75.md` | Blog |
| **76** | README + demo | Kill node, verify | README.md | **Project 5 ✅** |

## Phase 6: AI + Future Systems (Days 77–90)

| Day | Morning (1.5 hrs) | Afternoon (2 hrs) | Evening (1 hr) | Output |
|-----|-------------------|-------------------|----------------|--------|
| **77** | Spectre + Meltdown | Check /sys/vulnerabilities | `day-77.md` | |
| **78** | KPTI, Retpoline mitigations | Study kernel patches | `day-78.md` | Blog |
| **79** | eBPF introduction | bpftrace hello world | `day-79.md` | |
| **80** | eBPF programs + maps | Trace syscalls live | `day-80.md` | |
| **81** | AI in OS: SchedCP | Read SchedCP paper | `day-81.md` | |
| **82** | AI in OS: Google's Llama | Read Llama paper | `day-82.md` | Blog |
| **83** | Semantic scheduler design | Architecture design doc | `day-83.md` | |
| **84** | eBPF collector | syscall_monitor.bt | `day-84.md` | Push |
| **85** | Python ML classifier | Train workload classifier | `day-85.md` | |
| **86** | Priority adjuster daemon | Connect ML → setpriority | `day-86.md` | |
| **87** | Testing with real workloads | Benchmark improvements | `day-87.md` | |
| **88** | Full system integration | End-to-end test | `day-88.md` | |
| **89** | Portfolio polish | Update all READMEs | GitHub | |
| **90** | Final blog post + LinkedIn | Publish capstone article | Dev.to | **Journey ✅** |

---

---

# 🏆 PROJECT PORTFOLIO SUMMARY

| # | Project | Phase | Real Problem Solved | Tech Stack | MNC Relevance |
|---|---------|-------|---------------------|------------|---------------|
| **1** | Unix Shell | 1 | Every developer tool starts with a shell. Bash, zsh, fish — all built this way. | C, fork/exec, pipes | Google, Amazon SDE interviews |
| **2** | User-Level Thread Library | 2 | Python's `asyncio`, Go's goroutines, Node.js event loop — all share this concept | C, x86-64 assembly | Kernel developer interviews, Nvidia |
| **3** | Custom malloc() | 3 | Memory leaks cost real money in cloud. jemalloc (Facebook), tcmalloc (Google) solve this. | C, sbrk/mmap, GDB | Any systems role, Valgrind profiling |
| **4** | Toy File System | 4 | Databases (MySQL, Postgres) implement their own file management. So does HDFS. | C, binary I/O, disk layout | Storage engineer, Amazon EBS/EFS |
| **5** | Distributed KV Store | 5 | Redis, DynamoDB, Cassandra — multi-billion dollar products. Same core idea. | Python, gRPC, Docker, protobuf | AWS, Google Cloud, Meta infra |
| **6** | AI Semantic Scheduler | 6 | Google's SchedCP, Nvidia's AI workload isolation — active 2024-2025 research | eBPF, Python, sklearn | Staff-level, research roles |

---

# 📣 DOCUMENTATION STRATEGY — Your Public Evidence Trail

## Weekly Blog Post Calendar

| Week | Blog Post Title | Platform | Topics Covered |
|------|----------------|----------|----------------|
| Week 1 | "7 Days to Set Up a Linux Dev Environment as a Complete Beginner" | Dev.to | Phase 0 |
| Week 2 | "What Actually Happens When You Type a Command in Linux" | Dev.to | Syscalls, processes |
| Week 3 | "I Modified an Operating System Kernel. Here's What I Changed." | Hashnode | xv6 |
| Week 4 | "I Built a Unix Shell from Scratch. Here's Everything I Learned." | Dev.to | Project 1 |
| Week 5 | "The Mars Pathfinder Bug That Almost Killed a Mission" | LinkedIn Article | Mars Pathfinder |
| Week 6 | "Race Conditions, Deadlocks, and the Worst Software Bug in History (Therac-25)" | Dev.to | Concurrency |
| Week 7 | "How a Context Switch Actually Works: 15 Lines of Assembly That Run Your OS" | Hashnode | Project 2 |
| Week 8 | "What malloc() Does Internally: I Wrote My Own Version" | Dev.to | Project 3 |
| Week 9 | "How Files Are Actually Stored on Disk: Inodes, Bitmaps, and Superblocks" | Hashnode | Phase 4 |
| Week 10 | "The CAP Theorem Isn't Just Theory: I Built a Distributed Database" | Dev.to | Project 5 |
| Week 11 | "How Netflix Monitors 1 Million Production Servers with eBPF" | Hashnode | eBPF |
| Week 12 | "I Built an AI-Powered CPU Scheduler. Here's the Full Architecture." | Dev.to | Project 6 |
| Week 13 | "90 Days of OS Engineering: What I Built and What I Learned" | LinkedIn Article | Full journey |

## LinkedIn Post Templates

**Every 2-3 days**, post a short update:

```
Template A: "Today I Learned"
"TIL: [concept]. This matters because [real-world application]. 
I demonstrated it by [what you built/ran]. 
90-day OS journey: Day XX. #OperatingSystems #Linux #SystemsProgramming"

Template B: "Project Update"
"Just completed [project name]. It took [X] days and [N] lines of code.
The hardest part was [specific technical challenge].
The GitHub repo: [link]
#SystemsProgramming #OpenSource #BuildInPublic"

Template C: "Case Study"
"Did you know [Mars Pathfinder/Therac-25] happened because of [concurrency bug]?
Here's how it worked and what modern OS engineers do to prevent it:
[1-2 key points]
#OperatingSystems #TechHistory #SystemsEngineering"
```

---

# 🎯 INTERVIEW PREPARATION CHECKLIST

By the end of Day 90, you should be able to answer all of these from memory:

### Tier 1: Every Systems Interview
- [ ] What is the difference between a process and a thread?
- [ ] What is a system call? How does it differ from a function call?
- [ ] Explain fork(), exec(), and wait(). What is a zombie process?
- [ ] What is a race condition? Give a real example.
- [ ] What is a deadlock? What are the four conditions?
- [ ] Explain virtual memory and paging in simple terms.
- [ ] What is a TLB? Why does it exist?
- [ ] What is a page fault? What are the three types?

### Tier 2: Senior Systems Engineer
- [ ] Explain MLFQ scheduling. Why is it better than Round Robin for interactive workloads?
- [ ] How does Linux CFS work? What is vruntime? What data structure stores processes?
- [ ] Explain the Mars Pathfinder priority inversion. How was it fixed?
- [ ] What is journaling? What problem does it solve?
- [ ] Explain Copy-on-Write. Why does fork() not copy all memory immediately?
- [ ] What is the CAP theorem? Give a CP system and an AP system example.
- [ ] What is Raft consensus? Explain leader election in 2 minutes.

### Tier 3: Staff/Principal Level
- [ ] What is eBPF? How does the kernel verifier ensure safety?
- [ ] Explain Meltdown. What is KPTI? What is the performance cost?
- [ ] What is Spectre? What is a Retpoline?
- [ ] How does tcmalloc reduce lock contention? How does jemalloc reduce fragmentation?
- [ ] What is DPDK? Why does 100Gbps networking require kernel bypass?
- [ ] How does SchedCP use LLMs to improve scheduling?
- [ ] Design a thread scheduler for ARM big.LITTLE that optimizes for battery life.

---

# 🗂️ APPENDIX: QUICK REFERENCE

## Key System Calls Cheat Sheet

| Syscall | What It Does | C Header |
|---------|-------------|---------|
| `fork()` | Duplicate current process | `<unistd.h>` |
| `exec()` | Replace process with new program | `<unistd.h>` |
| `wait()` | Wait for child to terminate | `<sys/wait.h>` |
| `pipe()` | Create anonymous communication channel | `<unistd.h>` |
| `dup2()` | Duplicate file descriptor | `<unistd.h>` |
| `open()` | Open or create a file | `<fcntl.h>` |
| `read()` | Read bytes from a file descriptor | `<unistd.h>` |
| `write()` | Write bytes to a file descriptor | `<unistd.h>` |
| `mmap()` | Map file/device into memory | `<sys/mman.h>` |
| `sbrk()` | Extend the heap (used in malloc) | `<unistd.h>` |
| `clone()` | Create a thread (low-level) | `<sched.h>` |

## Process States at a Glance

| State | Meaning | What causes entry |
|-------|---------|------------------|
| New | Created but not yet admitted | fork() called |
| Ready | Waiting for CPU | I/O completed, or time slice expired |
| Running | Currently executing on CPU | Scheduler selected it |
| Waiting | Waiting for I/O or event | read(), sleep(), lock() |
| Terminated | Finished execution | exit() called or error |

## Common GDB Commands for Debugging OS Code

```bash
gcc -g -o myprogram myprogram.c    # Compile with debug symbols
gdb ./myprogram                     # Start debugger

(gdb) run                          # Run the program
(gdb) break main                   # Set breakpoint at main()
(gdb) break filename.c:42          # Breakpoint at line 42
(gdb) next                         # Execute next line (don't enter functions)
(gdb) step                         # Execute next line (enter functions)
(gdb) print variable_name          # Print value of variable
(gdb) print *pointer               # Print value at pointer
(gdb) info locals                  # Print all local variables
(gdb) backtrace                    # Show call stack (where am I?)
(gdb) continue                     # Continue until next breakpoint
(gdb) quit                         # Exit gdb
```

---

> ## 📌 Final Note: Why Documentation Is the Real Project
>
> The six code projects prove you can build. The 13 blog posts prove you can explain. The GitHub history proves you did it consistently over time. The LinkedIn updates prove you did it publicly and professionally.
>
> When a recruiter or hiring manager looks at your profile, they will see:
> - A GitHub with 90+ commits across 6 real systems projects
> - 13 detailed technical blog posts with thousands of words of explanation
> - A LinkedIn feed showing consistent, public learning over 3 months
>
> This combination is extraordinarily rare. Most candidates have either projects OR writing, not both. The combination makes the learning real in the eyes of any evaluator — not because you claim to have learned it, but because the evidence is public, timestamped, and detailed.
>
> **Start on Day 0. Commit every day. Publish every week. The documentation is the career.**

---
*Roadmap Version 1.0 — Built on reference: Operating Systems Architecture & Engineering: An Exhaustive Technical Roadmap for Systems Proficiency*
*Generated for: MNC-grade OS Engineering Career Preparation*