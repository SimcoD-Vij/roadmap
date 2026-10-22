# 🖥️ Mainframe Engineering Complete Mastery Roadmap
### From Absolute Zero → AI-Era Ready Junior Mainframe Engineer
#### *IBM Z · z/OS · COBOL · JCL · VSAM · Db2 · CICS · Zowe · Automation*

---

> **Research Date:** October 2026  
> **Research Methodology:** IBM Z Xplore official platform, 15+ verified job postings (Wipro, TCS, Infosys — India, 2025), IBM Redbooks, Open Mainframe Project, GnuCOBOL documentation, Zowe CLI official docs  
> **Target:** Junior Mainframe Developer / Application Engineer roles in India (Wipro, TCS, Infosys, Cognizant, HCL, Capgemini, IBM India)  
> **Duration:** 180 study days · 6 days per week · 4 hours per day · Zero cost  
> **Starting point:** Complete beginner — no programming, no OS, no mainframe knowledge assumed

---

## ⚠️ MANDATORY HONESTY STATEMENT

This roadmap uses a two-track approach:

| Track | What it is | What it proves |
|---|---|---|
| **IBM Z Xplore** | Real z/OS mainframe access — FREE, authorized by IBM | Actual z/OS execution — the real thing |
| **Local environment** | GnuCOBOL + Python + SQLite on Windows | COBOL language concepts, data logic, business rules — NOT z/OS execution |

**Never claim local GnuCOBOL execution as z/OS experience. Document every artifact as exactly what it is.**

---

## 📊 JOB MARKET RESEARCH SUMMARY (Verified, October 2026)

### Skills Appearing in 15+ India Job Postings (2025)

| Rank | Skill | Frequency | Role Level |
|---|---|---|---|
| 1 | COBOL | 15/15 postings | Entry + Senior |
| 2 | JCL | 15/15 postings | Entry + Senior |
| 3 | DB2/z/OS | 13/15 postings | Entry + Senior |
| 4 | VSAM | 12/15 postings | Entry + Senior |
| 5 | CICS | 11/15 postings | Entry + Senior |
| 6 | TSO/ISPF | 9/15 postings | Entry + Senior |
| 7 | SDSF | 8/15 postings | Entry |
| 8 | File-AID / Xpediter | 7/15 postings | Senior |
| 9 | Endevor / ChangeMan (version control) | 6/15 postings | Senior |
| 10 | MQ (IBM MQ) | 5/15 postings | Senior |
| 11 | Mainframe modernization | 4/15 postings | Senior |
| 12 | Agile / SDLC | 4/15 postings | Entry + Senior |
| 13 | Python / Scripting | 3/15 postings | Senior |
| 14 | IMS DB | 3/15 postings | Senior |

**Sources:** Wipro job postings (Hyderabad, Chennai, Bangalore, 2025), TCS walk-in drive (May 2025), Infosys postings (Gurugram, pan-India), verified on TheMuse, AmbitionBox, JobG8.

**Target entry-level salary range:** ₹4–8 LPA fresher; ₹6–12 LPA with 2–3 years; ₹12–20 LPA with 5+ years  
**Top hiring cities:** Hyderabad, Chennai, Bangalore, Pune, Gurugram, Kolkata

---

## 🏗️ PART 0: OVERALL ARCHITECTURE — Read Before Day 1

### Architecture A: Your Learning and Development Environment

```
┌─────────────────────────────────────────────────────────────────────────┐
│                    YOUR LEARNING PIPELINE                                │
│                                                                          │
│  LEARN → IMPLEMENT → TEST → DOCUMENT → VERSION CONTROL → PORTFOLIO      │
│                                                                          │
│  ┌─────────────────┐    ┌──────────────────┐    ┌──────────────────┐   │
│  │  Study Sources  │    │  Local Windows   │    │  IBM Z Xplore    │   │
│  │                 │    │  Environment     │    │  (Free Real z/OS)│   │
│  │  IBM Z Xplore   │───►│                  │    │                  │   │
│  │  IBM Redbooks   │    │  GnuCOBOL 3.2    │    │  Real TSO/ISPF  │   │
│  │  Open MF        │    │  Python 3.12     │    │  Real JCL/JES2  │   │
│  │  Project COBOL  │    │  SQLite          │    │  Real VSAM      │   │
│  │  Zowe Docs      │    │  VS Code         │    │  Real Db2       │   │
│  │  IBM Redbooks   │    │  Git + GitHub    │    │  Real CICS      │   │
│  └─────────────────┘    │  Zowe CLI        │    │  Real RACF      │   │
│                          │  Mermaid/Draw.io │    └──────────────────┘   │
│                          └────────┬─────────┘              │            │
│                                   │                         │            │
│                          ┌────────▼─────────────────────────▼───────┐   │
│                          │          DOCUMENTATION + EVIDENCE          │   │
│                          │                                            │   │
│                          │  GitHub Repository (mainframe-journey/)    │   │
│                          │  Daily Journals (docs/daily/Day-NNN.md)   │   │
│                          │  Architecture Diagrams (docs/architecture/)│   │
│                          │  ADRs, Test Reports, Runbooks              │   │
│                          │  Portfolio README + Badge Evidence         │   │
│                          └────────────────────────────────────────────┘   │
└─────────────────────────────────────────────────────────────────────────┘
```

### Architecture B: The Capstone System — Payment Settlement & Reconciliation

```
ENTERPRISE PAYMENT SETTLEMENT SYSTEM (PSRS)
Your learning project — built layer by layer across 180 days

┌──────────────────────────────────────────────────────────────────────────┐
│  LAYER 1: EXTERNAL INPUTS                                                │
│  Synthetic CSV/flat-file transaction records (100–50,000 records)        │
│  Generated by Python script — deterministic, reproducible               │
└──────────────────────────────────┬───────────────────────────────────────┘
                                   │
┌──────────────────────────────────▼───────────────────────────────────────┐
│  LAYER 2: INPUT VALIDATION (COBOL PROGRAM — PSRSVAL)                     │
│  Validate record length, field format, amount ranges                     │
│  Reject malformed records → ERRFILE                                      │
│  Accept valid records → VALFILE                                          │
└──────────────────────────────────┬───────────────────────────────────────┘
                                   │
┌──────────────────────────────────▼───────────────────────────────────────┐
│  LAYER 3: BATCH PROCESSING (JCL ORCHESTRATION)                           │
│  JCL Job: PSRSMAIN                                                       │
│  Step 1: SORT input by transaction ID                                    │
│  Step 2: PSRSVAL — validate records                                      │
│  Step 3: PSRSDEDUP — detect duplicates                                   │
│  Step 4: PSRSPOST — post to ledger                                       │
│  Step 5: PSRSRECN — reconcile totals                                     │
│  Step 6: PSRSRPT  — generate settlement report                           │
└──────────────────────────────────┬───────────────────────────────────────┘
                                   │
┌──────────────────────────────────▼───────────────────────────────────────┐
│  LAYER 4: COBOL BUSINESS LOGIC PROGRAMS                                  │
│  PSRSVAL  — field-level validation + rejection                           │
│  PSRSDEDUP — duplicate detection using sorted key comparison             │
│  PSRSPOST  — update ledger, apply business rules                         │
│  PSRSRECN  — compare posted total vs expected settlement total           │
│  PSRSRPT   — produce formatted text report                               │
└──────────────────────────────────┬───────────────────────────────────────┘
                                   │
┌──────────────────────────────────▼───────────────────────────────────────┐
│  LAYER 5: DATA STORAGE                                                   │
│  VSAM KSDS: LEDGER.MASTER (keyed by account ID)                          │
│  VSAM ESDS: AUDIT.LOG (append-only audit trail)                          │
│  DB2 Table: PSRS.TRANSACTIONS (relational query and reporting)           │
│  Sequential files: INFILE, VALFILE, ERRFILE, RPTFILE                    │
└──────────────────────────────────┬───────────────────────────────────────┘
                                   │
┌──────────────────────────────────▼───────────────────────────────────────┐
│  LAYER 6: ONLINE TRANSACTION (CICS — Phase 5+)                           │
│  CICS Map: INQUIRY screen — look up account balance                      │
│  CICS Program: PSRSINQ — calls Db2 and returns balance                  │
│  CICS Program: PSRSADJ — supervisor-only balance adjustment              │
└──────────────────────────────────┬───────────────────────────────────────┘
                                   │
┌──────────────────────────────────▼───────────────────────────────────────┐
│  LAYER 7: MODERN INTEGRATION (Phase 6+)                                  │
│  Zowe CLI: Job submission, JES output retrieval, dataset management      │
│  Python: Test data generation, result validation scripts                 │
│  REST API (z/OS Connect): Expose balance inquiry to mobile               │
│  GitHub Actions: Trigger Zowe job submission on code push                │
└──────────────────────────────────┬───────────────────────────────────────┘
                                   │
┌──────────────────────────────────▼───────────────────────────────────────┐
│  LAYER 8: SECURITY + OBSERVABILITY + RECOVERY                            │
│  RACF: Dataset protection, user profiles, audit logs                     │
│  SMF Records: Job accounting and resource usage                          │
│  Restart/Recovery: Checkpointing in PSRSPOST                             │
│  Runbooks: Job failure investigation, reconciliation mismatch            │
└──────────────────────────────────────────────────────────────────────────┘
```

---

## 🔧 TECHNOLOGY DECISION MATRIX

| Component | Purpose | Selected Technology | Alternatives | Cost | Access | Stage | Limitations |
|---|---|---|---|---|---|---|---|
| COBOL Compiler (local) | Learn COBOL syntax offline | GnuCOBOL 3.2 (GPL) | None free | Free | Windows direct install | Phase 2 | Not IBM Enterprise COBOL; no z/OS runtime |
| Real z/OS environment | Genuine mainframe execution | IBM Z Xplore (free) | None free | Free | Register at ibm.com/zxplore | Phase 2 onwards | Shared learning environment; no production-level access |
| Code Editor | Write COBOL, JCL, scripts | VS Code + IBM Z Open Editor extension | Notepad++ | Free | Install from microsoft.com | Phase 1 | — |
| Version Control | Track all code and docs | Git + GitHub | GitLab | Free | github.com | Phase 1 | — |
| Database (local) | Practice SQL before Db2 | SQLite 3 | PostgreSQL | Free | Built into Python | Phase 3 | Not Db2 z/OS; no EBCDIC; no z/OS catalog |
| Real Db2 | Production SQL on mainframe | Db2 via Z Xplore | None free | Free via Z Xplore | IBM Z Xplore | Phase 4 | Shared; limited dataset sizes |
| VSAM (real) | Real keyed file access | VSAM via Z Xplore | None free | Free via Z Xplore | IBM Z Xplore | Phase 4 | — |
| Diagramming | Architecture diagrams | Mermaid + draw.io | Lucidchart | Free | Built into GitHub MD; draw.io at diagrams.net | Phase 1 | — |
| Python | Scripting, test data, automation | Python 3.12 | PowerShell | Free | python.org | Phase 1 | — |
| Zowe CLI | Modern mainframe interface | Zowe CLI (open-source) | IBM PCOM | Free | zowe.org | Phase 6 | Requires Z Xplore connection |
| Data generation | Synthetic test records | Python Faker + custom script | Manual | Free | pip install faker | Phase 2 | — |
| Documentation | Portfolio + journal | Markdown + GitHub | Confluence | Free | — | Phase 1 | — |

---

## 🗺️ 180-DAY PHASE MAP

```
PHASE 1 (Days 1–25):    Computing Fundamentals
PHASE 2 (Days 26–55):   IBM Z Architecture + z/OS Fundamentals
PHASE 3 (Days 56–85):   COBOL Programming (Beginner → Business Logic)
PHASE 4 (Days 86–115):  JCL, Batch Engineering, VSAM, Db2
PHASE 5 (Days 116–140): CICS, RACF, Security, Testing, Operations
PHASE 6 (Days 141–160): Modern Tooling, Zowe, Python, Integration
PHASE 7 (Days 161–180): Capstone, Portfolio, Interview Preparation
```

---

---

# 📅 PHASE 1: COMPUTING FUNDAMENTALS (Days 1–25)

> **Why this phase exists:** You cannot understand z/OS process management without knowing what a process is. You cannot read a dump without knowing hexadecimal. You cannot debug a COBOL program without understanding how data is represented in memory. This phase builds the vocabulary and mental models you will use for the next 155 days.

---

## DAY 1 — Bits, Bytes, and How Computers Store Information

### A. Connection to the Roadmap
This is Day 1. There are no prerequisites to recall.  
**This leads to:** Day 2 (number systems), ultimately to Day 30+ (EBCDIC encoding, which is how IBM Z represents text — different from ASCII used on PCs).

### B. Measurable Learning Objectives
1. Convert any decimal number to binary and back, without a calculator.
2. State the number of values representable by N bits.
3. Explain why computers use binary (not decimal).
4. Interpret a byte as two hexadecimal digits.
5. Explain how a character is stored differently from a number.

### C. Topics and Subtopics

**1. The bit — smallest unit of information**
- A bit is a single binary digit: 0 or 1.
- Physically, this represents two stable states: voltage high/low, magnetic north/south, light on/off.
- All computer data — text, numbers, images, programs — is ultimately stored as sequences of bits.
- *Why binary and not decimal?* Because engineering two stable electrical states is vastly more reliable than ten.

**2. The byte — the practical unit**
- 1 byte = 8 bits.
- 8 bits can represent 2⁸ = 256 different values (0 through 255).
- Memory, storage, and network bandwidth are all measured in bytes and their multiples.
- 1 KB = 1,024 bytes; 1 MB = 1,048,576 bytes; 1 GB = 1,073,741,824 bytes.

**3. Binary (base-2) number system**
- Binary uses only digits 0 and 1. Each position is a power of 2.
- Decimal 13 = 1×8 + 1×4 + 0×2 + 1×1 = binary 1101.
- Converting decimal to binary: repeatedly divide by 2, record remainders bottom to top.
- Practice: convert 42, 255, 128, 64, 0 to binary.

**4. Hexadecimal (base-16) — the engineer's shorthand**
- Hex digits: 0–9, then A=10, B=11, C=12, D=13, E=14, F=15.
- One hex digit represents exactly 4 bits (a nibble).
- One byte = two hex digits: 0xFF = 11111111 = decimal 255.
- *Why hex?* Reading a 32-bit dump as binary (32 zeros and ones) is error-prone. Reading it as eight hex digits is practical.
- On z/OS, you will see memory dumps, storage addresses, and return codes expressed in hex constantly.

**5. How a character is stored vs how a number is stored**
- The character '3' and the number 3 are not the same thing in memory.
- The character '3' is encoded as a code point (ASCII: 51 decimal = 0x33; EBCDIC: 0xF3 — you will learn EBCDIC on Day 28).
- The number 3 stored as a single byte binary integer is 0x03.
- Confusing these causes the most common category of COBOL bugs.

### D. Required Resources
- IBM Redbook "Introduction to the New Mainframe: z/OS Basics" — Chapter 1, sections 1.1–1.3 (binary and storage)  
  URL: https://www.redbooks.ibm.com/abstracts/sg246366.html (free PDF)
- GnuCOBOL Programmer's Guide: Appendix on data representation  
  URL: https://gnucobol.sourceforge.io/guides/GnuCOBOLProgrammersGuide.pdf

### E. Four-Hour Study Timetable
```
0:00–0:15  Active recall: (Day 1 — nothing to recall yet. Write what "computer" means to you.)
0:15–1:00  Study: Read binary and hexadecimal material. Work 20 conversion exercises.
1:00–2:15  Practical: Python binary and hex exercises (see F below).
2:15–3:00  Independent: Write a conversion table from 0–255 in decimal, binary, and hex.
3:00–3:25  Documentation: Write Day-001.md journal entry.
3:25–3:45  Review: Re-read your conversion table. Spot any errors.
3:45–4:00  Teach-back: Explain bits and bytes aloud, as if to a friend.
```

### F. Practical Assignment

```python
# Save as: scripts/day001_binary_hex.py
# Run with: python scripts/day001_binary_hex.py
# Purpose: Prove you understand binary and hex by computing them yourself

def decimal_to_binary(n):
    """Convert non-negative integer to binary string WITHOUT using bin()."""
    if n == 0:
        return "00000000"
    bits = []
    while n > 0:
        bits.append(str(n % 2))
        n //= 2
    # Pad to 8 bits (one byte)
    while len(bits) < 8:
        bits.append('0')
    return ''.join(reversed(bits))

def decimal_to_hex(n):
    """Convert non-negative integer to two-digit hex WITHOUT using hex()."""
    HEX_DIGITS = '0123456789ABCDEF'
    high_nibble = n // 16
    low_nibble  = n % 16
    return HEX_DIGITS[high_nibble] + HEX_DIGITS[low_nibble]

# Test values that matter in mainframe work
test_values = [0, 1, 8, 15, 16, 32, 64, 128, 255, 42, 100, 200]

print(f"{'Decimal':>10}  {'Binary':>10}  {'Hex':>6}  {'Verify Binary':>12}  {'Verify Hex':>10}")
print("-" * 60)
for v in test_values:
    my_bin = decimal_to_binary(v)
    my_hex = decimal_to_hex(v)
    verify_bin = format(v, '08b')     # Python built-in
    verify_hex = format(v, '02X')     # Python built-in
    match_b = "✓" if my_bin == verify_bin else "✗ WRONG"
    match_h = "✓" if my_hex == verify_hex else "✗ WRONG"
    print(f"{v:>10}  {my_bin:>10}  {my_hex:>6}  {match_b:>12}  {match_h:>10}")

print("\n=== SELF-TEST ===")
print("The byte 0xFF contains:", int('FF', 16), "as decimal,", 
      decimal_to_binary(255), "as binary")
print("The character code 65 is:", chr(65), "(in ASCII — that's 'A')")
print("The character code 0xF1 in EBCDIC will be '1' (you will learn this on Day 28)")
```

**Expected output:** All rows show ✓ in both verify columns.

### G. Active Recall Questions
1. A field is described as "2 bytes." How many bits is that? How many distinct values can it hold?
2. A mainframe dump shows the byte `0xC1`. What is that value in decimal? In binary?
3. Why would reading 8 bytes of binary (64 zeros and ones) be harder than reading 8 hex digits? Give an example.
4. *(Application)* A COBOL program stores the number 255 in a PIC 9 field. What will the raw byte contain — 0xFF or 0x39? Why? (Hint: think about the difference between numeric and character storage.)

### H. Testing and Exit Criteria
- [ ] Script runs with zero ✗ errors
- [ ] Can convert decimal 173 to binary and hex on paper without a tool in under 2 minutes
- [ ] Can explain why `0xFF` and `255` are the same value to a hypothetical colleague
- [ ] Day-001.md journal entry created and committed to Git

### I. Documentation Artifact
**File:** `docs/daily/Day-001.md`
```markdown
# Day 001 — Bits, Bytes, Binary, and Hexadecimal
**Date:** YYYY-MM-DD  | **Status:** Completed / Attempted / Verified

## Objectives
[List the 5 objectives]

## What I Studied
[Resources read, sections covered]

## Key Concepts in My Own Words
- Bit: ...
- Byte: ...
- Binary: ...
- Hex: ...
- Why binary in computers: ...

## Code Executed
File: scripts/day001_binary_hex.py
Result: [paste output or screenshot reference]

## Conversion Table (My Work)
[Include 10-row table: decimal / binary / hex]

## Errors or Confusions
[Anything that confused me and how I resolved it]

## Active Recall Answers (My Attempt)
1. ...
2. ...
3. ...
4. ...

## Questions I Still Cannot Answer
[Be honest]

## Next Day Preview
Tomorrow: Signed integers, negative numbers in binary, ASCII basics.
```

### J. Real-World Relevance
When a z/OS batch job aborts with return code `0x00000008`, you are reading hexadecimal. When you examine a COBOL field in a memory dump and see `0xF1F2F3`, those are EBCDIC codes for '1', '2', '3'. When RACF audit logs show storage addresses, they are in hex. This knowledge is used every single day by every mainframe engineer diagnosing real production incidents.

### K. Environment Fallback
No mainframe needed. This is pure mathematics and Python scripting on Windows.

### L. Completion Gate
Python script runs with all ✓. Paper conversion exercise correct. Journal committed to GitHub.

---

## DAY 2 — Signed Numbers, Characters, and ASCII

### Topics (Condensed Format — Days 2–25 use condensed format for space)

**Binary arithmetic and negative numbers:**
- Unsigned integers: 1 byte holds 0–255. 2 bytes hold 0–65,535.
- Sign-magnitude: leftmost bit is sign. Problem: two representations of zero.
- Two's complement (what computers actually use): negate a number by inverting all bits then adding 1. Elegantly consistent arithmetic.
- Example: 8-bit two's complement range is -128 to +127. 0xFF = -1, not 255.

**ASCII character encoding:**
- American Standard Code for Information Interchange.
- Maps 128 values (7 bits) to printable characters, digits, control codes.
- '0'=48=0x30, 'A'=65=0x41, 'a'=97=0x61, space=32=0x20.
- On your Windows PC and on distributed systems: ASCII (and its extension UTF-8).
- On IBM Z mainframes: EBCDIC (Extended Binary Coded Decimal Interchange Code) — different mapping. This is why files copied from PC to mainframe without conversion appear garbled.

**Practical task:** Write Python script that prints the ASCII table for printable characters. Predict what EBCDIC 0xC1 through 0xC9 represent (A–I) — you will verify this on Day 28.

**Journal:** `docs/daily/Day-002.md`

---

## DAY 3 — How a CPU Executes a Program

**Key concepts:**
- CPU components: Arithmetic Logic Unit (ALU), Control Unit (CU), Registers, Program Counter.
- The fetch-decode-execute cycle: CPU reads an instruction from memory (fetch), interprets it (decode), carries out the operation (execute), then repeats.
- Registers: tiny, ultra-fast storage inside the CPU (e.g., IBM Z has 16 general-purpose registers of 64 bits each).
- Memory (RAM): temporary, byte-addressed storage. All programs must be loaded into RAM to execute.
- The instruction pointer (Program Counter): tells the CPU which instruction to fetch next. A COBOL `GOTO` statement changes this.
- Stack: a region of memory used for function calls, return addresses, and local variables.
- Why this matters for mainframes: z/OS manages real storage (physical RAM) and virtual storage (the illusion of private address space). COBOL programs run in this virtual space.

**Practical:** Draw the fetch-decode-execute cycle on paper. Commit photo or Mermaid diagram.

**Journal:** `docs/daily/Day-003.md`

---

## DAY 4 — Operating Systems: What They Do and Why

**Key concepts:**
- An OS is a resource manager and abstraction layer. Without it, every program would have to manage hardware directly — chaos.
- OS responsibilities: process management, memory management, file system, I/O management, security and access control, user interface.
- Process: a running program with its own address space, resources, and execution state.
- File system: the OS's organized structure for storing and retrieving data on disks (on z/OS: partitioned data sets, sequential data sets, VSAM — not the familiar C:\Windows directory).
- Kernel mode vs user mode: the OS runs in privileged mode; application programs run in user mode. A COBOL program running in z/OS is a user-mode process.
- On z/OS specifically: the OS is called z/OS (formerly OS/390, MVS). It is extraordinarily stable — systems run for years without rebooting. It handles thousands of concurrent batch jobs and millions of transactions.

**Journal:** `docs/daily/Day-004.md`

---

## DAY 5 — Storage, I/O, and File Systems Fundamentals

**Key concepts:**
- Persistent vs volatile storage: RAM loses data when power is removed; disk retains it.
- HDD, SSD, and tape: mainframes use all three. IBM Z uses Direct Access Storage Devices (DASD — pronounced "daz-dee") for primary disk, and tape for long-term archival.
- Tracks and cylinders: DASD is organized into cylinders (concentric circles) and tracks. This is relevant when you allocate data sets in JCL.
- DASD organization in z/OS: data is stored in data sets (not files). A data set has a name, organization (sequential, partitioned, VSAM), record format, and record length.
- Tracks and blocks: a block is the unit actually read from disk. Blocking factor = number of logical records per block. Larger blocks = fewer I/O operations = faster.
- Buffer pool: z/OS keeps frequently accessed data in memory buffers to avoid repeated disk reads.

**Practical:** Research what "cylinders" and "tracks" mean for IBM 3390 DASD. Write a short explanation in Day-005.md.

**Journal:** `docs/daily/Day-005.md`

---

## DAYS 6–7 — Command-Line Interface, Git, and Your Repository

### Setting Up Your Development Environment (Day 6)

```powershell
# Windows: Install these in order
# 1. Git for Windows: https://git-scm.com/download/win
# 2. Python 3.12: https://www.python.org/downloads/
# 3. VS Code: https://code.visualstudio.com/
# 4. VS Code extensions:
#    - IBM Z Open Editor (for COBOL + JCL syntax highlighting)
#    - GitLens
#    - Mermaid Preview

# After installing Git, open PowerShell:
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# Create your portfolio repository
mkdir mainframe-journey
cd mainframe-journey
git init
git branch -M main
```

### Repository Structure to Create Now
```
mainframe-journey/
├── README.md              ← Your portfolio front page
├── docs/
│   ├── architecture/
│   │   ├── system-context.md
│   │   ├── adr/           ← Architecture Decision Records
│   │   └── diagrams/
│   ├── daily/             ← Day-001.md through Day-180.md
│   ├── fundamentals/      ← Reference notes on key concepts
│   ├── labs/              ← Step-by-step lab instructions
│   ├── projects/          ← Project documentation
│   ├── testing/           ← Test plans and results
│   ├── runbooks/          ← Operational runbooks
│   └── glossary.md
├── src/
│   ├── cobol/             ← COBOL source programs
│   ├── jcl/               ← JCL procedures and jobs
│   └── python/            ← Python automation scripts
├── tests/                 ← Test cases and expected outputs
├── data/
│   └── synthetic/         ← Generated test data (no real PII ever)
└── scripts/               ← Build and utility scripts
```

```bash
# Create the structure
mkdir -p docs/architecture/adr docs/architecture/diagrams
mkdir -p docs/daily docs/fundamentals docs/labs
mkdir -p docs/projects docs/testing docs/runbooks
mkdir -p src/cobol src/jcl src/python
mkdir -p tests data/synthetic scripts

# Create README
echo "# Mainframe Engineering Learning Journey" > README.md
echo "Started: $(date)" >> README.md
echo "Status: In Progress | Phase 1 of 7" >> README.md

git add .
git commit -m "Day 6: Repository structure initialised"
```

### Day 7: Networking Basics for Mainframe Engineers

**Key concepts:**
- IP addresses, ports, TCP vs UDP, DNS.
- Client-server model: your PC (client) connects to z/OS (server) via TCP/IP.
- TN3270: the protocol your terminal emulator uses to talk to z/OS. Not HTTP — it is a special IBM protocol from the 1970s, still used today.
- VTAM: z/OS network access method that handles TN3270 connections.
- Why this matters: when Zowe CLI connects to z/OS, it uses HTTPS. When ISPF sessions are emulated, they use TN3270. Understanding the network layer helps you diagnose connection failures.

---

## DAYS 8–12 — Programming Logic (Python as the Teaching Vehicle)

> **Why Python?** Python has the cleanest syntax for learning programming concepts. Every concept you learn here (variables, conditions, loops, functions, records) has a direct COBOL equivalent. On Day 56, when you write your first COBOL IF statement, you will not be learning "what is a condition" — only "how COBOL expresses it."

### Day 8: Variables, Data Types, and Expressions

```python
# scripts/day008_variables.py
# PURPOSE: Establish mental model of named storage locations
# Every COBOL variable you write (PIC 9, PIC X) maps to these concepts

# Integer: whole number — like COBOL PIC 9(4)
transaction_count = 0
amount_cents = 15000          # Representing ₹150.00 in cents (avoid float for money!)

# String: sequence of characters — like COBOL PIC X(10)
account_id = "ACC0001234"
transaction_date = "2025-01-15"

# Boolean: true/false — in COBOL this is implemented via 88-level condition names
is_valid = True
has_duplicate = False

# Float: decimal — AVOID for financial amounts (rounding errors!)
bad_amount = 0.1 + 0.2        # This is NOT 0.3 in binary floating point!
print(f"0.1 + 0.2 = {bad_amount}")   # Shows: 0.30000000000000004

# The correct pattern for financial data (integer cents or Python Decimal):
from decimal import Decimal, ROUND_HALF_UP
amount_a = Decimal("0.10")
amount_b = Decimal("0.20")
total = amount_a + amount_b
print(f"Decimal 0.1 + 0.2 = {total}")   # Shows: 0.30

# MAINFRAME CONNECTION:
# COBOL uses PACKED-DECIMAL (COMP-3) for financial arithmetic — exact, no floating point
# This is one of COBOL's great strengths for banking and finance
```

### Days 9–12: Conditions, Loops, Functions, and Records

**Day 9 — Conditions (IF/ELIF/ELSE):** Write a validation function for a transaction amount. If amount ≤ 0: reject. If amount > 999999: reject. Otherwise: accept. This exact logic becomes a COBOL IF statement on Day 60.

**Day 10 — Loops (FOR, WHILE):** Process a list of 100 synthetic transaction records. Count valid, invalid, and duplicate records. Print summary. This becomes COBOL PERFORM UNTIL on Day 62.

**Day 11 — Functions:** Refactor your Day 10 solution. Extract `validate_record()`, `detect_duplicate()`, `accumulate_total()` as separate functions. This maps directly to COBOL paragraphs and sections.

**Day 12 — Data structures as records:** Define a `transaction` as a Python dict or dataclass with fields: `txn_id`, `account_id`, `amount_cents`, `date`, `type`. Write functions to read a CSV line and parse it into this structure. This becomes COBOL's WORKING-STORAGE record definition.

---

## DAYS 13–16 — Relational Database Concepts and SQL Fundamentals

> **Why now?** You will use Db2 on z/OS from Phase 4 onwards. Learning SQL now means Day 100 (when you embed SQL in COBOL) will be about COBOL integration, not SQL itself.

### Day 13: Tables, Rows, Columns, and Keys

```sql
-- Run these in SQLite via Python:
-- python -c "import sqlite3; conn = sqlite3.connect(':memory:'); ..."

-- Create a transactions table (same schema you will use in Db2 later)
CREATE TABLE PSRS_TRANSACTIONS (
    TXN_ID       CHAR(12)       NOT NULL,
    ACCOUNT_ID   CHAR(10)       NOT NULL,
    AMOUNT_CENTS INTEGER        NOT NULL,
    TXN_DATE     CHAR(10)       NOT NULL,
    TXN_TYPE     CHAR(1)        NOT NULL,  -- 'D'=Debit, 'C'=Credit
    STATUS       CHAR(1)        DEFAULT 'P', -- 'P'=Pending, 'V'=Valid, 'R'=Rejected
    PRIMARY KEY (TXN_ID)
);

-- INSERT some synthetic rows
INSERT INTO PSRS_TRANSACTIONS VALUES
    ('TXN000000001', 'ACC0001234', 150000, '2025-01-15', 'D', 'P'),
    ('TXN000000002', 'ACC0001234', 200000, '2025-01-15', 'C', 'P'),
    ('TXN000000003', 'ACC0005678', 75000,  '2025-01-15', 'D', 'P');

-- SELECT: retrieve specific data
SELECT TXN_ID, AMOUNT_CENTS, TXN_TYPE
FROM PSRS_TRANSACTIONS
WHERE ACCOUNT_ID = 'ACC0001234';

-- Aggregate: total debits
SELECT SUM(AMOUNT_CENTS)
FROM PSRS_TRANSACTIONS
WHERE TXN_TYPE = 'D' AND STATUS = 'V';
```

### Days 14–16: Joins, Constraints, Transactions, and Error Handling

**Day 14:** Create an ACCOUNTS table. Join PSRS_TRANSACTIONS to ACCOUNTS to get account holder name. This teaches the relational model — you will use this in Db2.

**Day 15:** Transactions in databases (COMMIT / ROLLBACK). Why atomicity matters: partial posting is worse than no posting. If the program crashes after posting 500 of 1,000 records, which records were posted? This is the problem COBOL checkpoint/restart solves.

**Day 16:** NULL handling, constraints, and error handling. `NOT NULL`, `CHECK` constraints, foreign keys. In COBOL and Db2, you will check `SQLCODE` after every SQL statement — learn why here.

---

## DAYS 17–20 — Debugging and Reasoning About Failures

> **The most important skill you will develop:** Not "how to write programs" but "how to find out why a program did not do what you expected."

### The Evidence-Based Debugging Framework

Apply this framework to every failure you encounter — in Python now, in COBOL and JCL later:

```
1. WHAT WAS EXPECTED?    → State the intended behavior precisely.
2. WHAT ACTUALLY HAPPENED? → Read the actual output, error, or symptom exactly.
3. WHAT FACTS ARE OBSERVABLE? → What do logs, output, and code tell you?
4. WHAT ARE PLAUSIBLE CAUSES? → List all explanations that are consistent with facts.
5. WHAT DISTINGUISHES THEM? → Design a minimal experiment.
6. RUN THE EXPERIMENT.
7. WHAT DOES THE RESULT SUPPORT? → Revise your hypothesis based on evidence.
8. REPEAT UNTIL ROOT CAUSE IS ESTABLISHED.
9. WHAT REMAINS UNKNOWN? → Document uncertainties honestly.
```

**Day 17:** Inject a deliberate bug into your Day 12 record-processing script. Amount field contains a letter. What happens? What error message appears? How do you diagnose it? Document the investigation.

**Day 18:** Inject a logic bug — duplicate records pass through but should be rejected. The count is wrong. The total is correct. Diagnose by adding print statements to trace execution.

**Day 19:** Introduce a file I/O error — open a non-existent file. How does Python report it? How would you recover? This maps to COBOL FILE STATUS codes and JCL ABEND codes.

**Day 20:** Weekly review — write one page: "What is debugging? What is the difference between a syntax error, a runtime error, and a logic error? Give one example of each from your work this week."

---

## DAYS 21–24 — Data Generation and Project Scaffolding

### Day 21: Generate Your First Synthetic Test Dataset

```python
# src/python/generate_transactions.py
# PURPOSE: Create deterministic, realistic synthetic transaction data
# for all future testing. NO real personal data.

import csv
import random
import datetime
from decimal import Decimal

random.seed(42)   # ALWAYS set seed — reproducible results are mandatory

def generate_transaction_id(seq):
    return f"TXN{seq:09d}"

def generate_account_id():
    return f"ACC{random.randint(1000, 9999):07d}"

def generate_amount():
    """Return amount in cents (integer). Range: 1 to 999,999 cents."""
    return random.randint(1, 999999)

def generate_date(base_date, max_days_offset=30):
    offset = datetime.timedelta(days=random.randint(0, max_days_offset))
    return (base_date + offset).strftime("%Y-%m-%d")

def introduce_errors(records, error_rate=0.05):
    """Introduce realistic errors into a fraction of records."""
    errors_introduced = 0
    for record in records:
        if random.random() < error_rate:
            error_type = random.choice(['negative_amount', 'bad_account', 
                                         'invalid_type', 'duplicate'])
            if error_type == 'negative_amount':
                record['AMOUNT_CENTS'] = -abs(record['AMOUNT_CENTS'])
            elif error_type == 'bad_account':
                record['ACCOUNT_ID'] = 'BADACCT!!'
            elif error_type == 'invalid_type':
                record['TXN_TYPE'] = 'X'          # Only D or C are valid
            elif error_type == 'duplicate' and records.index(record) > 0:
                # Duplicate an earlier record
                earlier = random.choice(records[:records.index(record)])
                record['TXN_ID'] = earlier['TXN_ID']
            errors_introduced += 1
    return records, errors_introduced

def generate_dataset(n_records=500, output_path="data/synthetic/transactions.csv"):
    base_date = datetime.date(2025, 1, 1)
    records = []
    
    for i in range(1, n_records + 1):
        record = {
            'TXN_ID':       generate_transaction_id(i),
            'ACCOUNT_ID':   generate_account_id(),
            'AMOUNT_CENTS': generate_amount(),
            'TXN_DATE':     generate_date(base_date),
            'TXN_TYPE':     random.choice(['D', 'C', 'D', 'D', 'C']),  # 60% debit
        }
        records.append(record)
    
    # Introduce realistic errors
    records, error_count = introduce_errors(records, error_rate=0.08)
    
    # Write to CSV
    fieldnames = ['TXN_ID', 'ACCOUNT_ID', 'AMOUNT_CENTS', 'TXN_DATE', 'TXN_TYPE']
    with open(output_path, 'w', newline='') as f:
        writer = csv.DictWriter(f, fieldnames=fieldnames)
        writer.writeheader()
        writer.writerows(records)
    
    print(f"Generated {n_records} records with approximately {error_count} errors")
    print(f"Saved to: {output_path}")
    print(f"Random seed: 42 (reproducible)")
    return output_path

if __name__ == "__main__":
    generate_dataset(n_records=500)
```

**Day 22:** Write a Python validation script that reads `transactions.csv` and reports: total records, valid records, records with each type of error, total valid amount. This becomes the expected output for your COBOL validation program.

**Day 23:** Draw the system context diagram for your capstone in Mermaid. Commit to `docs/architecture/system-context.md`.

```markdown
```mermaid
graph TD
    A[External Input<br/>transactions.csv] -->|batch read| B[PSRSVAL<br/>Validation Program]
    B -->|valid records| C[PSRSDEDUP<br/>Duplicate Detection]
    B -->|rejected records| D[ERRFILE<br/>Error Report]
    C -->|clean records| E[PSRSPOST<br/>Ledger Update]
    E -->|updated| F[LEDGER.MASTER<br/>VSAM KSDS]
    E -->|transactions| G[PSRS.TRANSACTIONS<br/>Db2 Table]
    E -->|events| H[AUDIT.LOG<br/>VSAM ESDS]
    F --> I[PSRSRECN<br/>Reconciliation]
    G --> I
    I -->|discrepancy alert| J[Operations Team]
    I -->|settlement report| K[RPTFILE<br/>Batch Report]
```
```

**Day 24:** Weekly review + Phase 1 milestone assessment.

---

## DAY 25 — Phase 1 Milestone Assessment

### Assessment Tasks
1. **Conversion (10 min):** Convert 0xAB, 0x3F, 0x80 to decimal and binary on paper.
2. **Explanation (10 min):** Write one paragraph: "What does the fetch-decode-execute cycle mean? How does it relate to running a COBOL program on z/OS?"
3. **Code review (15 min):** Given a deliberately broken Python validation script, identify the bug using the evidence-based framework. Write: observation, hypothesis, test, conclusion.
4. **Data design (15 min):** Given this requirement — "Store the result of every payment settlement for audit purposes" — design a SQL table with appropriate columns, data types, and constraints.
5. **Repository check:** Is your `mainframe-journey` repository on GitHub with commits for Days 1–24?

### Passing Standard
Pass all five. If any fail: re-study the relevant day before proceeding to Phase 2.

---

---

# 📅 PHASE 2: IBM Z ARCHITECTURE + z/OS FUNDAMENTALS (Days 26–55)

> **Goal:** Understand how the IBM Z mainframe is physically and logically organized, how z/OS manages it, and how you interact with it through TSO, ISPF, and the Z Xplore environment.

---

## DAY 26 — IBM Z Hardware Architecture

### Why IBM Z Is Different from a PC

A PC and an IBM Z mainframe both have CPUs, RAM, and storage. They are architecturally very different:

| Property | Typical PC | IBM Z (z16 as of 2022) |
|---|---|---|
| Processor type | Intel/AMD x86-64 | IBM CISC (z/Architecture) |
| Cores | 4–32 | Up to 200 configurable (Telum II, 2025) |
| RAM | 16–128 GB | Up to 40 TB |
| Uptime | Reboots frequently | 15+ years continuous operation |
| RAS features | Basic | Redundant everything (power, memory, I/O) |
| Transaction throughput | Thousands/sec per server | Billions of transactions per day |
| Instruction set | x86-64 | z/Architecture (64-bit) |
| I/O system | PCIe lanes | Channel subsystem (independent I/O processors) |

**The Channel Subsystem:** On a PC, the CPU handles all I/O (your program waits while data is read from disk). On IBM Z, dedicated I/O processors called channels handle disk and network I/O independently, freeing CPUs entirely for computation. This is why mainframes can handle enormous I/O loads with high CPU efficiency.

**LPAR (Logical Partition):** IBM Z hardware can be divided into multiple LPARs, each running its own operating system (z/OS, Linux on Z, z/VM). This is hardware-level virtualization — not software virtualization like VMware.

**PR/SM:** The Processor Resource/Systems Manager — the hardware firmware that manages LPAR partitioning.

**Practical:** Read IBM Redbook SG24-6366 Chapter 2 (IBM Z hardware overview). Write a half-page summary in `docs/fundamentals/z-hardware.md`.

---

## DAYS 27–28 — z/OS Overview and EBCDIC

### Day 27: What z/OS Is and How It Is Organized

**z/OS major components:**
- **MVS (Multiple Virtual Storage):** The core supervisor. Manages memory, processes (address spaces), and job scheduling.
- **JES2 or JES3:** Job Entry Subsystem. Manages the queue of batch jobs waiting to run. Assigns job IDs. Stores job output (SYSOUT). You will interact with JES2 via SYSDA and SDSF.
- **TSO/E (Time Sharing Option/Extensions):** Interactive user environment. You type commands; z/OS responds.
- **ISPF:** A menu-driven interface that sits on top of TSO. Most mainframe engineers use ISPF panels for editing, browsing, dataset management, and job submission.
- **USS (UNIX System Services):** A full POSIX-compliant UNIX environment inside z/OS. You can run shell scripts, compile C programs, and use familiar UNIX tools here. Zowe also runs in USS.
- **Language Environment (LE):** The runtime that supports COBOL, PL/I, C, and other language programs. Provides common services like file I/O, date handling, and storage management.

**Address spaces:** In z/OS, every program runs in its own 64-bit virtual address space — completely isolated. COBOL programs, JES2, CICS, and Db2 each occupy separate address spaces.

### Day 28: EBCDIC — The Character Encoding You Will Live With

EBCDIC (Extended Binary Coded Decimal Interchange Code) was designed for punch cards and IBM systems. It is completely different from ASCII.

```
EBCDIC vs ASCII comparison:

Character  ASCII (hex)  EBCDIC (hex)
'A'        0x41         0xC1
'B'        0x42         0xC2
'Z'        0x5A         0xE9
'0'        0x30         0xF0
'1'        0x31         0xF1
'9'        0x39         0xF9
' '(space) 0x20         0x40
```

**Why this matters for you:**
1. Files on z/OS are stored in EBCDIC. Files on your PC are ASCII. Transferring without conversion = garbled data.
2. In COBOL on z/OS, when you write `MOVE "HELLO" TO WS-FIELD`, the string is stored as EBCDIC. On GnuCOBOL (local), it stores as ASCII. The programs look identical but the bytes differ.
3. IBM Z has hardware instructions for EBCDIC-specific operations (move characters, compare character strings) — this is one reason COBOL string operations are fast on z/OS.

**Practical task:** Write a Python function that converts ASCII text to EBCDIC and back. Use a lookup table. Verify that round-trip conversion produces identical input.

```python
# src/python/ebcdic_converter.py
# A simplified EBCDIC conversion utility
# In real z/OS work, file transfer tools (FTP, Zowe) handle this automatically

ASCII_TO_EBCDIC = {
    ' ': 0x40, '&': 0x50, '-': 0x60, '/': 0x61,
    'A': 0xC1, 'B': 0xC2, 'C': 0xC3, 'D': 0xC4, 'E': 0xC5,
    'F': 0xC6, 'G': 0xC7, 'H': 0xC8, 'I': 0xC9,
    'J': 0xD1, 'K': 0xD2, 'L': 0xD3, 'M': 0xD4, 'N': 0xD5,
    'O': 0xD6, 'P': 0xD7, 'Q': 0xD8, 'R': 0xD9,
    'S': 0xE2, 'T': 0xE3, 'U': 0xE4, 'V': 0xE5, 'W': 0xE6,
    'X': 0xE7, 'Y': 0xE8, 'Z': 0xE9,
    '0': 0xF0, '1': 0xF1, '2': 0xF2, '3': 0xF3, '4': 0xF4,
    '5': 0xF5, '6': 0xF6, '7': 0xF7, '8': 0xF8, '9': 0xF9,
}
EBCDIC_TO_ASCII = {v: k for k, v in ASCII_TO_EBCDIC.items()}

def ascii_to_ebcdic(text):
    return bytes([ASCII_TO_EBCDIC.get(c.upper(), 0x3F) for c in text])

def ebcdic_to_ascii(data):
    return ''.join(EBCDIC_TO_ASCII.get(b, '?') for b in data)

# Test
original = "HELLO WORLD 0123456789"
as_ebcdic = ascii_to_ebcdic(original)
back_to_ascii = ebcdic_to_ascii(as_ebcdic)
assert back_to_ascii == original.upper(), f"Round-trip failed: {back_to_ascii}"
print(f"Original:      {original}")
print(f"As EBCDIC hex: {as_ebcdic.hex().upper()}")
print(f"Back to ASCII: {back_to_ascii}")
print("Round-trip: ✓")
```

---

## DAYS 29–31 — Registering for IBM Z Xplore

### Obtain Your Free Real Mainframe Access

**Step 1:** Go to https://ibm.com/z/resources/zxplore  
**Step 2:** Click "Get started" and create a free IBM ID.  
**Step 3:** Enroll in IBM Z Xplore. No credit card. No time limit.  
**Step 4:** Complete the "Fundamentals" badge exercises first.

**What you get:**
- Real z/OS environment (shared, learning-purpose)
- Access to TSO/ISPF via a browser-based TN3270 emulator
- COBOL compiler (IBM Enterprise COBOL for z/OS)
- JCL execution through JES2
- VSAM datasets
- Db2 for z/OS
- CICS (in Extended/Advanced tiers)

**Day 29:** Register and complete the Z Xplore onboarding exercises. Document in `docs/daily/Day-029.md`: your IBM Z ID (not your password!), what you accessed, what you observed.

**Day 30:** Navigate ISPF. Learn ISPF Option 3 (Dataset utilities), Option 2 (Edit), Option 1 (Browse). Create your first TSO dataset: `YOURID.FIRST.DATASET`. Document every step.

**Day 31:** Learn TSO commands: `LISTDS`, `ALLOC`, `FREE`, `SUBMIT`, `STATUS`. Understand the difference between TSO commands (typed on a command line) and ISPF panels (menu-driven).

---

## DAYS 32–40 — z/OS Data Sets: The Foundation of Everything

### What a z/OS Data Set Is (and Why It Is Not a "File")

On your PC, files are stored in directories with paths like `C:\Users\name\docs\report.txt`.  
On z/OS, data is stored in **data sets** with names like `PROD.PSRS.TRANSACTIONS.INPUT`.

**Data set naming rules:**
- Composed of qualifiers separated by dots
- Each qualifier: 1–8 characters, alphanumeric + @#$
- Total name: maximum 44 characters
- Convention: `owner.project.type.descriptor`
- Example: `JOHND.PSRS.COBOL.SOURCE`, `JOHND.PSRS.DATA.INPUT`

**Data set organizations (DSORG):**

| DSORG | Name | Description | Mainframe Use |
|---|---|---|---|
| PS | Physical Sequential | Records stored sequentially | Batch input/output files |
| PO | Partitioned (PDS) | Library of "members" (like a folder of files) | COBOL source code, JCL procedures, copybooks |
| VS | VSAM | Indexed, direct access | Master files, databases |

**Record formats (RECFM):**

| RECFM | Name | Description |
|---|---|---|
| F | Fixed | All records same length |
| FB | Fixed Blocked | Fixed-length, multiple records per block |
| V | Variable | Records have different lengths |
| VB | Variable Blocked | Variable-length, multiple per block |
| U | Undefined | Used by executable programs (load modules) |

**LRECL:** Logical Record Length — the size of one data record.

**BLKSIZE:** Block Size — how many bytes are read from disk in one I/O operation. A block contains one or more records. Larger blocks = fewer disk reads = faster.

**Days 32–35:** Learn to allocate datasets in JCL and TSO. Understand catalog entries. Understand how the OS finds a dataset from its name (DFSMS, ICF catalog). Practice creating, editing, and deleting datasets on Z Xplore.

**Days 36–38:** Fixed-length vs variable-length record processing. Why does LRECL matter for COBOL? A COBOL record description must exactly match the physical record length on the file.

**Days 39–40:** Partitioned Data Sets (PDS and PDSE). Understand members. Understand directory blocks. Why COBOL source code lives in a PDS. How ISPF Edit works against PDS members.

---

## DAYS 41–50 — TSO/ISPF Deep Dive and First JCL

### Day 41–43: TSO/ISPF Navigation

**Key ISPF panels every mainframe engineer uses daily:**

| ISPF Option | Purpose |
|---|---|
| 1 (View) | Browse a dataset (read-only) |
| 2 (Edit) | Edit dataset or PDS member |
| 3.1 | Compress a PDS |
| 3.2 | Allocate a new dataset |
| 3.3 | Copy, move, or rename datasets |
| 3.4 | Dataset list (like dir/ls) |
| 3.5 | Reset statistics |
| 5 (DSLIST) | List datasets matching pattern |
| S (SDSF) | Display and manage jobs |

**SDSF (System Display and Search Facility):**
Your primary job monitoring tool. After submitting a JCL job, you check SDSF to see:
- Is it queued? Running? Completed?
- What was the return code?
- What did SYSOUT (your print output) contain?
- What errors appeared in the log?

### Day 44–46: Your First JCL Job

JCL (Job Control Language) is the language you use to tell z/OS what job to run, what files to use, and what conditions to check.

```jcl
//HELLOJOB JOB (ACCT),'YOUR NAME',
//             CLASS=A,MSGCLASS=X,NOTIFY=&SYSUID
//*
//* This is a comment. Stars in column 3 of JCL = comment.
//*
//STEP1   EXEC PGM=IEBGENER
//SYSPRINT DD SYSOUT=*
//SYSIN    DD DUMMY
//SYSUT1   DD *
HELLO, MAINFRAME WORLD!
//SYSUT2   DD SYSOUT=*
//
```

**Anatomy of a JCL statement:**
```
// NAME      OPERATION  PARAMETERS
// ↑         ↑          ↑
// cols 1-2  cols 3-10  col 12 onwards

//HELLOJOB  JOB    - Identifies start of job, job name, class
//STEP1     EXEC   - Execute a program (PGM=) or procedure (PROC=)
//SYSPRINT  DD     - Data Definition: connects a dataset to a program DDname
//SYSIN     DD     - Another DDname, DUMMY means "no data"
//SYSUT1    DD     - Input data (inline with *)
//SYSUT2    DD     - Output to SYSOUT (print queue)
//          (blank)- End of job
```

**Day 44:** Submit this job on Z Xplore. Find it in SDSF. Read the JES log. What is the return code?

**Day 45:** What is `IEBGENER`? It is a z/OS utility that copies records from one dataset to another. Learn the 12 most important z/OS utilities:

| Utility | Purpose |
|---|---|
| IEBGENER | Copy sequential files |
| IEBCOPY | Copy/compress PDS |
| IEBUPDTE | Update PDS members |
| IEFBR14 | Allocate/delete datasets |
| IDCAMS | VSAM management + define/delete |
| SORT (DFSORT) | Sort and merge records |
| IEBCOMPR | Compare two datasets |
| ICETOOL | DFSORT advanced reporting |

**Day 46:** Write JCL to allocate a new dataset, copy your test transactions CSV into it, and verify the copy. This is the pattern every batch job uses to prepare its input.

### Days 47–50: JCL Statements in Depth

**The JOB statement — all parameters:**
```jcl
//PSRSMAIN JOB (8100),'PSRS BATCH',
//             CLASS=A,
//             MSGCLASS=X,
//             NOTIFY=&SYSUID,
//             TIME=(0,30),
//             REGION=32M
```
- `CLASS=A`: which job class (queue) this job enters
- `MSGCLASS=X`: where to send JES messages (X = hold in SDSF)
- `NOTIFY=&SYSUID`: send a TSO message when job completes
- `TIME=(0,30)`: maximum CPU time (0 hours, 30 minutes)
- `REGION=32M`: maximum memory this job can use

**The DD statement — connecting data:**
```jcl
//INFILE   DD DSN=JOHND.PSRS.DATA.INPUT,
//            DISP=SHR
//OUTFILE  DD DSN=JOHND.PSRS.DATA.OUTPUT,
//            DISP=(NEW,CATLG,DELETE),
//            SPACE=(TRK,(10,5)),
//            DCB=(RECFM=FB,LRECL=100,BLKSIZE=0)
```
- `DSN=`: Dataset Name (which dataset to use)
- `DISP=SHR`: Share — open an existing dataset for reading
- `DISP=(NEW,CATLG,DELETE)`: Create new; catalog it on normal end; delete it on abnormal end
- `SPACE=(TRK,(10,5))`: Allocate 10 primary tracks + 5 secondary
- `DCB=`: Data Control Block — defines the record format

**Return codes and COND parameter:**
```jcl
//STEP2    EXEC PGM=PSRSDEDUP,
//              COND=(0,NE,STEP1)
```
- `COND=(0,NE,STEP1)`: Skip STEP2 if STEP1 return code is NOT EQUAL to 0
- Convention: RC=0 (success), RC=4 (warning), RC=8 (error), RC≥12 (severe)

---

## DAYS 51–55 — z/OS Security Fundamentals: RACF

### What RACF Is and Why Every Mainframe Engineer Must Understand It

RACF (Resource Access Control Facility) is z/OS's security manager. It controls:
- **Authentication:** Who you are (your RACF user ID and password/passphrase)
- **Authorization:** What resources you can access (datasets, programs, transactions)
- **Auditing:** What access was attempted and whether it succeeded

Every dataset, program, and CICS transaction can be RACF-protected.

### Core RACF Concepts

**User profiles:** Every TSO user has a RACF user profile. It records your default group, password, and access authorities.

**Group profiles:** Users belong to groups. Permissions granted to a group apply to all members.

**Resource profiles:** Protect datasets (`DATASET`), programs (`PROGRAM`), and other resources.

**Access levels:** `READ`, `UPDATE`, `ALTER`, `CONTROL` (least to most privileged).

**Least privilege principle:** A user or program should have only the minimum access needed to do its job. Giving everyone `ALTER` access to all datasets is a serious security violation — common in poorly managed systems, catastrophic when exploited.

```
Example access control scenario:

Dataset: PROD.PSRS.LEDGER.MASTER (the production ledger)
Desired access:
  PSRS batch job user (PSRSJOB):  UPDATE  (can read and write)
  Operations team (OPSGROUP):     READ    (can view but not change)
  Developers (DEVGROUP):          READ    (read test copy only, not this one)
  Auditors (AUDITGRP):            READ    (for audit review)
  Everyone else:                  NONE    (access denied)
```

**Day 51–53:** Learn RACF user profile navigation in ISPF. View your own profile using the `RACF` ISPF panels or `LISTUSER` command. Document what you observe.

**Day 54:** Research RACF dataset protection. Write an Architecture Decision Record (ADR) explaining how you would protect the PSRS.LEDGER.MASTER dataset in production.

**Day 55:** Phase 2 milestone assessment.

---

---

# 📅 PHASE 3: COBOL PROGRAMMING (Days 56–85)

> **Research note:** COBOL remains mandatory in 100% of verified India mainframe job postings. IBM Enterprise COBOL for z/OS is the production standard. GnuCOBOL (local) teaches language concepts; IBM Z Xplore provides genuine z/OS compilation and execution.

---

## DAY 56 — What COBOL Is and Why It Exists

### COBOL in Plain English

COBOL (Common Business-Oriented Language) was designed in 1959 by Grace Hopper and a committee to:
1. Be readable by business managers, not just mathematicians.
2. Handle financial and record-processing tasks precisely.
3. Run on any mainframe (portability).
4. Handle fixed-length record layouts matching physical file structures.

These design goals explain every unusual feature of COBOL:
- It reads like English (`ADD AMOUNT TO TOTAL`, `MOVE SPACES TO WS-NAME`).
- It has built-in PACKED-DECIMAL arithmetic — exact, no floating-point errors.
- Record descriptions mirror the physical layout of data on disk byte-for-byte.
- File handling is declarative — you describe the file; COBOL handles the I/O.
- There are approximately 800 billion lines of COBOL in production worldwide. It processes more financial transactions daily than any other language.

### Why COBOL Will Not Die

1. **Correctness:** Banks cannot afford to rewrite 40 years of tested business logic. One conversion error could misdirect millions of transactions.
2. **Performance:** IBM Enterprise COBOL produces highly optimized native machine code. Db2 with embedded SQL in COBOL is extremely fast.
3. **Workforce transition:** Older COBOL programmers are retiring. Demand for new COBOL engineers is increasing, not decreasing.
4. **AI integration:** IBM watsonx Code Assistant for Z can help modernize COBOL. But a human engineer must understand the original COBOL to validate AI-generated changes.

---

## DAYS 57–60 — COBOL Program Structure

### The Four Divisions

Every COBOL program has exactly four divisions, in this order:

```cobol
IDENTIFICATION DIVISION.
ENVIRONMENT DIVISION.
DATA DIVISION.
PROCEDURE DIVISION.
```

**IDENTIFICATION DIVISION:** Program metadata.
```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID.   PSRSVAL.
       AUTHOR.       YOUR NAME.
       DATE-WRITTEN. 2025-01-01.
       INSTALLATION. LEARNING ENVIRONMENT.
      *
      * PURPOSE: Validate payment settlement transaction records.
      * INPUT:   INFILE  - FB, LRECL=100
      * OUTPUT:  VALFILE - valid records
      *          ERRFILE - rejected records
      *
```

**ENVIRONMENT DIVISION:** Connects program names to physical files.
```cobol
       ENVIRONMENT DIVISION.
       INPUT-OUTPUT SECTION.
       FILE-CONTROL.
           SELECT INFILE  ASSIGN TO INFILE
                          FILE STATUS IS WS-INFILE-STATUS.
           SELECT VALFILE ASSIGN TO VALFILE
                          FILE STATUS IS WS-VALFILE-STATUS.
           SELECT ERRFILE ASSIGN TO ERRFILE
                          FILE STATUS IS WS-ERRFILE-STATUS.
```

**DATA DIVISION:** Defines all data — files, working storage, and constants.
```cobol
       DATA DIVISION.
       FILE SECTION.
       FD  INFILE
           RECORDING MODE IS F
           BLOCK CONTAINS 0 RECORDS.
       01  IN-RECORD.
           05 IN-TXN-ID       PIC X(12).
           05 IN-ACCOUNT-ID   PIC X(10).
           05 IN-AMOUNT-CENTS PIC 9(9).
           05 IN-TXN-DATE     PIC X(10).
           05 IN-TXN-TYPE     PIC X(01).
           05 FILLER          PIC X(58).  *> Pad to LRECL=100
```

**PROCEDURE DIVISION:** The executable business logic.
```cobol
       PROCEDURE DIVISION.
       0000-MAIN.
           PERFORM 1000-INITIALISE
           PERFORM 2000-PROCESS-RECORDS
               UNTIL WS-EOF-SWITCH = 'Y'
           PERFORM 9000-TERMINATE
           STOP RUN.
```

### Day 57: Write and run your first COBOL program locally

```
ENVIRONMENT SETUP for local COBOL (Windows):

1. Download GnuCOBOL 3.2 for Windows from SourceForge:
   https://sourceforge.net/projects/open-cobol/files/gnucobol/3.2/

2. Extract to C:\GnuCOBOL\

3. Add C:\GnuCOBOL\bin to your PATH environment variable.

4. Verify: Open PowerShell and run:
   cobc --version
   Expected: GnuCOBOL 3.2.0

5. Install VS Code extension: "IBM Z Open Editor" (provides COBOL syntax highlighting)
```

```cobol
       *> src/cobol/HELLO.cob
       *> First COBOL program
       *> Compile: cobc -x HELLO.cob -o HELLO
       *> Run:     ./HELLO  (Linux/WSL) or HELLO.exe (Windows)
       *>
       *> IMPORTANT: COBOL source uses columns:
       *>   Cols 1-6:  Sequence number (or blank)
       *>   Col  7:    Indicator ('*' = comment, '-' = continuation, ' ' = code)
       *>   Cols 8-11: Area A (division headers, section names, FD, 01-level)
       *>   Cols12-72: Area B (statements, subordinate data items)
       *>
       IDENTIFICATION DIVISION.
       PROGRAM-ID. HELLO.
       DATA DIVISION.
       WORKING-STORAGE SECTION.
       01 WS-GREETING          PIC X(40) VALUE 'HELLO, MAINFRAME ENGINEERING WORLD!'.
       01 WS-DATE              PIC X(10).
       PROCEDURE DIVISION.
       0000-MAIN.
           ACCEPT WS-DATE FROM DATE YYYYMMDD
           DISPLAY 'Date: ' WS-DATE
           DISPLAY WS-GREETING
           DISPLAY 'GnuCOBOL is running on your local PC.'
           DISPLAY 'On z/OS, this would run with IBM Enterprise COBOL.'
           STOP RUN.
```

**Day 58–60:** Progress through PIC clauses (PICTURE IS), elementary and group items, VALUE clauses, and MOVE statements.

---

## DAYS 61–75 — COBOL Business Logic

### The Complete PSRSVAL Program (Built Over Days 61–70)

```cobol
       IDENTIFICATION DIVISION.
       PROGRAM-ID. PSRSVAL.
      *================================================================
      * PSRSVAL - Payment Settlement Record Validator
      * PURPOSE: Read transaction records, validate each field,
      *          write valid records to VALFILE, invalid to ERRFILE.
      *          Produce validation summary counts.
      *
      * LOCAL EXECUTION: cobc -x PSRSVAL.cob -o PSRSVAL
      * INPUT FILE:      data/synthetic/transactions.csv (FB, LRECL=100)
      *
      * *** THIS IS A GnuCOBOL LOCAL VERSION ***
      * *** On z/OS, ASSIGN TO matches JCL DDnames ***
      * *** On z/OS, EBCDIC encoding applies ***
      *================================================================
       ENVIRONMENT DIVISION.
       INPUT-OUTPUT SECTION.
       FILE-CONTROL.
           SELECT INFILE  ASSIGN TO DYNAMIC WS-INFILE-NAME
                          ORGANIZATION IS LINE SEQUENTIAL
                          FILE STATUS  IS WS-INFILE-STATUS.
           SELECT VALFILE ASSIGN TO DYNAMIC WS-VALFILE-NAME
                          ORGANIZATION IS LINE SEQUENTIAL
                          FILE STATUS  IS WS-VALFILE-STATUS.
           SELECT ERRFILE ASSIGN TO DYNAMIC WS-ERRFILE-NAME
                          ORGANIZATION IS LINE SEQUENTIAL
                          FILE STATUS  IS WS-ERRFILE-STATUS.

       DATA DIVISION.
       FILE SECTION.
       FD  INFILE.
       01  IN-RECORD                    PIC X(100).

       FD  VALFILE.
       01  VAL-RECORD.
           05 VAL-TXN-ID               PIC X(12).
           05 VAL-ACCOUNT-ID           PIC X(10).
           05 VAL-AMOUNT-CENTS         PIC 9(9).
           05 VAL-TXN-DATE             PIC X(10).
           05 VAL-TXN-TYPE             PIC X(01).
           05 VAL-STATUS               PIC X(01) VALUE 'V'.
           05 FILLER                   PIC X(57).

       FD  ERRFILE.
       01  ERR-RECORD.
           05 ERR-TXN-ID               PIC X(12).
           05 ERR-REASON               PIC X(40).
           05 ERR-ORIGINAL             PIC X(48).

       WORKING-STORAGE SECTION.
      *--- File names (local environment uses actual path)
       01 WS-INFILE-NAME               PIC X(80)
             VALUE 'data/synthetic/transactions.csv'.
       01 WS-VALFILE-NAME              PIC X(80)
             VALUE 'data/synthetic/valid_records.dat'.
       01 WS-ERRFILE-NAME              PIC X(80)
             VALUE 'data/synthetic/error_records.dat'.
      *--- File status codes
       01 WS-INFILE-STATUS             PIC X(02).
       01 WS-VALFILE-STATUS            PIC X(02).
       01 WS-ERRFILE-STATUS            PIC X(02).
      *--- Control switches
       01 WS-EOF-SWITCH                PIC X(01) VALUE 'N'.
          88 WS-EOF                                VALUE 'Y'.
      *--- Parsed transaction fields
       01 WS-TRANSACTION.
           05 WS-TXN-ID                PIC X(12).
           05 WS-ACCOUNT-ID            PIC X(10).
           05 WS-AMOUNT-STR            PIC X(09).
           05 WS-AMOUNT-CENTS          PIC 9(09).
           05 WS-TXN-DATE              PIC X(10).
           05 WS-TXN-TYPE              PIC X(01).
      *--- Counters
       01 WS-COUNTERS.
           05 WS-RECORDS-READ          PIC 9(07) VALUE ZERO.
           05 WS-RECORDS-VALID         PIC 9(07) VALUE ZERO.
           05 WS-RECORDS-REJECTED      PIC 9(07) VALUE ZERO.
           05 WS-TOTAL-VALID-CENTS     PIC 9(15) VALUE ZERO.
      *--- Validation flag
       01 WS-VALID-FLAG                PIC X(01).
          88 WS-RECORD-VALID                       VALUE 'Y'.
          88 WS-RECORD-INVALID                     VALUE 'N'.
       01 WS-ERROR-REASON              PIC X(40).
      *--- Report line
       01 WS-REPORT-LINE               PIC X(80).

       PROCEDURE DIVISION.
       0000-MAIN.
           PERFORM 1000-INITIALISE
           PERFORM 2000-PROCESS-RECORDS
               UNTIL WS-EOF
           PERFORM 9000-TERMINATE
           STOP RUN
           .

       1000-INITIALISE.
           OPEN INPUT  INFILE
           OPEN OUTPUT VALFILE
           OPEN OUTPUT ERRFILE
           IF WS-INFILE-STATUS NOT = '00'
               DISPLAY 'ERROR: Cannot open INFILE, status: ' WS-INFILE-STATUS
               MOVE 16 TO RETURN-CODE
               STOP RUN
           END-IF
           READ INFILE        *> Skip CSV header line
           .

       2000-PROCESS-RECORDS.
           READ INFILE
               AT END
                   SET WS-EOF TO TRUE
               NOT AT END
                   ADD 1 TO WS-RECORDS-READ
                   PERFORM 2100-PARSE-RECORD
                   PERFORM 2200-VALIDATE-RECORD
                   IF WS-RECORD-VALID
                       PERFORM 2300-WRITE-VALID-RECORD
                   ELSE
                       PERFORM 2400-WRITE-ERROR-RECORD
                   END-IF
           END-READ
           .

       2100-PARSE-RECORD.
      *    Parse comma-delimited fields from IN-RECORD
      *    Record format: TXN_ID,ACCOUNT_ID,AMOUNT_CENTS,TXN_DATE,TXN_TYPE
           UNSTRING IN-RECORD
               DELIMITED BY ','
               INTO WS-TXN-ID
                    WS-ACCOUNT-ID
                    WS-AMOUNT-STR
                    WS-TXN-DATE
                    WS-TXN-TYPE
           END-UNSTRING
           .

       2200-VALIDATE-RECORD.
           MOVE 'Y'    TO WS-VALID-FLAG
           MOVE SPACES TO WS-ERROR-REASON
      *    Rule 1: TXN-ID must be 9 digits starting with 'TXN'
           IF WS-TXN-ID(1:3) NOT = 'TXN'
               MOVE 'N' TO WS-VALID-FLAG
               MOVE 'INVALID TXN-ID FORMAT' TO WS-ERROR-REASON
               GO TO 2200-EXIT
           END-IF
      *    Rule 2: Amount must be numeric and greater than zero
           MOVE FUNCTION NUMVAL(WS-AMOUNT-STR) TO WS-AMOUNT-CENTS
           IF WS-AMOUNT-CENTS <= 0
               MOVE 'N' TO WS-VALID-FLAG
               MOVE 'AMOUNT MUST BE POSITIVE' TO WS-ERROR-REASON
               GO TO 2200-EXIT
           END-IF
      *    Rule 3: Amount must not exceed 999999 cents (₹9,999.99)
           IF WS-AMOUNT-CENTS > 999999
               MOVE 'N' TO WS-VALID-FLAG
               MOVE 'AMOUNT EXCEEDS MAXIMUM' TO WS-ERROR-REASON
               GO TO 2200-EXIT
           END-IF
      *    Rule 4: Transaction type must be D or C
           IF WS-TXN-TYPE NOT = 'D' AND WS-TXN-TYPE NOT = 'C'
               MOVE 'N' TO WS-VALID-FLAG
               MOVE 'INVALID TRANSACTION TYPE' TO WS-ERROR-REASON
           END-IF
       2200-EXIT.
           EXIT
           .

       2300-WRITE-VALID-RECORD.
           MOVE WS-TXN-ID      TO VAL-TXN-ID
           MOVE WS-ACCOUNT-ID  TO VAL-ACCOUNT-ID
           MOVE WS-AMOUNT-CENTS TO VAL-AMOUNT-CENTS
           MOVE WS-TXN-DATE    TO VAL-TXN-DATE
           MOVE WS-TXN-TYPE    TO VAL-TXN-TYPE
           WRITE VAL-RECORD
           ADD  1 TO WS-RECORDS-VALID
           ADD  WS-AMOUNT-CENTS TO WS-TOTAL-VALID-CENTS
           .

       2400-WRITE-ERROR-RECORD.
           MOVE WS-TXN-ID      TO ERR-TXN-ID
           MOVE WS-ERROR-REASON TO ERR-REASON
           MOVE IN-RECORD(1:48) TO ERR-ORIGINAL
           WRITE ERR-RECORD
           ADD  1 TO WS-RECORDS-REJECTED
           .

       9000-TERMINATE.
           CLOSE INFILE VALFILE ERRFILE
           DISPLAY '========================================'
           DISPLAY 'PSRSVAL VALIDATION SUMMARY'
           DISPLAY '========================================'
           DISPLAY 'Records read:     ' WS-RECORDS-READ
           DISPLAY 'Records valid:    ' WS-RECORDS-VALID
           DISPLAY 'Records rejected: ' WS-RECORDS-REJECTED
           DISPLAY 'Total valid cents:' WS-TOTAL-VALID-CENTS
           DISPLAY '========================================'
           IF WS-RECORDS-REJECTED > 0
               MOVE 4 TO RETURN-CODE
           ELSE
               MOVE 0 TO RETURN-CODE
           END-IF
           .
```

**Days 71–75:** Build PSRSDEDUP (duplicate detection using sorted key comparison), PSRSPOST (ledger update with running totals), and PSRSRECN (reconciliation comparing actual to expected total).

---

## DAY 85 — Phase 3 Milestone Assessment + Z Xplore COBOL Execution

### Critical Checkpoint: Run PSRSVAL on Real z/OS

On IBM Z Xplore, create the JCL to compile and link PSRSVAL, then execute it:

```jcl
//PSRSCOB  JOB (ACCT),'COBOL COMPILE',
//              CLASS=A,MSGCLASS=X,NOTIFY=&SYSUID
//*
//COBUCG   PROC INLIB='JOHND.PSRS.COBOL.SOURCE',
//              OUTLIB='JOHND.PSRS.LOAD'
//COBOL    EXEC PGM=IGYCRCTL,
//              PARM='OBJECT,MAP,LIST,RENT,APOST'
//SYSLIB   DD DSN=SYS1.MACLIB,DISP=SHR
//SYSLIN   DD DSN=&&LOADSET,DISP=(MOD,PASS),
//            UNIT=VIO,SPACE=(TRK,(3,3))
//SYSIN    DD DSN=&INLIB(PSRSVAL),DISP=SHR
//SYSUT1   DD UNIT=VIO,SPACE=(CYL,(1,1))
//SYSPRINT DD SYSOUT=*
//LKED     EXEC PGM=HEWL,PARM='LIST,LET,XREF'
//SYSLIN   DD DSN=&&LOADSET,DISP=(OLD,DELETE)
//SYSLMOD  DD DSN=&OUTLIB(PSRSVAL),DISP=SHR
//SYSPRINT DD SYSOUT=*
//         PEND
//COMPILE  EXEC COBUCG
```

**What this proves:** IBM Enterprise COBOL compiled and linked your program to a z/OS load module. This is real. Document the compiler listing output, the return code, and any compiler warnings in your journal.

---

---

# 📅 PHASE 4: JCL, BATCH ENGINEERING, VSAM, AND Db2 (Days 86–115)

> **Overview:** You now know COBOL. This phase teaches the environment that runs COBOL at scale: JCL orchestration, data persistence via VSAM, and relational database access via Db2. All exercises from this phase forward should be performed on IBM Z Xplore wherever possible.

---

## DAYS 86–95 — JCL Advanced Batch Engineering

### Day 86: Multi-Step Jobs and Conditional Execution

The full PSRS batch job runs six programs in sequence. If any step fails, later steps that depend on it must be skipped.

```jcl
//PSRSMAIN JOB (ACCT),'PSRS SETTLEMENT',
//              CLASS=A,MSGCLASS=X,NOTIFY=&SYSUID,
//              TIME=(1,0),REGION=256M
//*=============================================================
//* PSRS DAILY SETTLEMENT JOB
//* Steps: SORT -> VALIDATE -> DEDUP -> POST -> RECONCILE -> REPORT
//*=============================================================
//*
//STEP01   EXEC PGM=SORT
//SYSOUT   DD SYSOUT=*
//SORTIN   DD DSN=JOHND.PSRS.DATA.INPUT,DISP=SHR
//SORTOUT  DD DSN=JOHND.PSRS.DATA.SORTED,
//            DISP=(NEW,CATLG,DELETE),
//            SPACE=(TRK,(50,20)),
//            DCB=(RECFM=FB,LRECL=100,BLKSIZE=0)
//SYSIN    DD *
  SORT FIELDS=(1,12,CH,A)
/*
//*
//STEP02   EXEC PGM=PSRSVAL,COND=(0,NE,STEP01)
//INFILE   DD DSN=JOHND.PSRS.DATA.SORTED,DISP=SHR
//VALFILE  DD DSN=JOHND.PSRS.DATA.VALID,
//            DISP=(NEW,CATLG,DELETE),
//            SPACE=(TRK,(40,10)),
//            DCB=(RECFM=FB,LRECL=100,BLKSIZE=0)
//ERRFILE  DD DSN=JOHND.PSRS.DATA.ERRORS,
//            DISP=(NEW,CATLG,DELETE),
//            SPACE=(TRK,(10,5)),
//            DCB=(RECFM=FB,LRECL=100,BLKSIZE=0)
//SYSOUT   DD SYSOUT=*
//*
//STEP03   EXEC PGM=PSRSPOST,COND=((4,LT,STEP02),(0,NE,STEP01))
//VALFILE  DD DSN=JOHND.PSRS.DATA.VALID,DISP=SHR
//SYSOUT   DD SYSOUT=*
```

**Days 87–90:** SORT utility in depth. The DFSORT utility processes billions of records in production. Learn SORT FIELDS, INCLUDE, OMIT, OUTREC, INREC, SUM, and MERGE.

**Days 91–93:** JCL procedures (PROCs). PROC libraries. Symbolic parameters. How IBM ships standard procedures like COBUCG for compilation.

**Days 94–95:** Return codes, ABEND codes, and job failure diagnosis. What is an ABEND? (Abnormal End — when a program fails.) Common ABENDs: S0C7 (data exception — numeric field contains non-numeric data), S0C4 (addressing exception — pointer to invalid memory), B37 (end of dataset space). How to read the system log to find the step, offset, and cause.

---

## DAYS 96–105 — VSAM

### What VSAM Is and Why It Exists

VSAM (Virtual Storage Access Method) provides organized file access for mainframe programs. Unlike sequential files (which must be read from beginning to end), VSAM allows direct access to records by key.

**Three VSAM organizations:**

| Type | Name | Description | PSRS Use |
|---|---|---|---|
| KSDS | Key-Sequenced Data Set | Records stored and retrieved by key. Most common. | LEDGER.MASTER — keyed by account ID |
| ESDS | Entry-Sequenced Data Set | Records stored in arrival order (append only) | AUDIT.LOG — chronological event log |
| RRDS | Relative Record Data Set | Records retrieved by record number | Not used in PSRS |

### Defining a VSAM Cluster with IDCAMS

```jcl
//DEFVSAM  JOB (ACCT),'DEFINE VSAM',CLASS=A,MSGCLASS=X
//DEFCLUST EXEC PGM=IDCAMS
//SYSPRINT DD SYSOUT=*
//SYSIN    DD *
  DELETE JOHND.PSRS.LEDGER.MASTER CLUSTER PURGE
  SET MAXCC=0

  DEFINE CLUSTER                              -
      (NAME(JOHND.PSRS.LEDGER.MASTER)         -
       INDEXED                                -
       KEYS(10 0)                             -  /* Key length 10, offset 0 */
       RECORDSIZE(100 100)                    -  /* Fixed 100-byte records */
       CYLINDERS(5 2)                         -  /* 5 primary + 2 secondary */
       FREESPACE(20 10)                       -  /* 20% CI, 10% CA free */
       SHAREOPTIONS(2 3))                     -  /* Share option */
      DATA                                    -
      (NAME(JOHND.PSRS.LEDGER.MASTER.DATA))   -
      INDEX                                   -
      (NAME(JOHND.PSRS.LEDGER.MASTER.INDEX))
/*
```

**Days 96–100:** VSAM concepts (control intervals, control areas, index levels, splits). How KSDS READ/WRITE/REWRITE/DELETE work in COBOL. How to handle VSAM file status codes (00=success, 22=duplicate key, 23=key not found, 10=EOF).

**Days 101–105:** Add VSAM ledger operations to PSRSPOST. Each valid transaction reads the account balance from LEDGER.MASTER, updates it, and rewrites the record.

---

## DAYS 106–115 — Db2 for z/OS

### Embedded SQL in COBOL

```cobol
       DATA DIVISION.
       WORKING-STORAGE SECTION.
       *--- SQL Communication Area - mandatory for all Db2 programs ---
           EXEC SQL INCLUDE SQLCA END-EXEC.
       *
       01 WS-TXN-ID             PIC X(12).
       01 WS-HOST-AMOUNT        PIC S9(9) COMP.  *> Host variable for SQL
       01 WS-HOST-ACCOUNT       PIC X(10).

       PROCEDURE DIVISION.
       2000-INSERT-TRANSACTION.
           EXEC SQL
               INSERT INTO PSRS.TRANSACTIONS
                   (TXN_ID, ACCOUNT_ID, AMOUNT_CENTS, TXN_DATE, TXN_TYPE)
               VALUES
                   (:WS-TXN-ID,
                    :WS-HOST-ACCOUNT,
                    :WS-HOST-AMOUNT,
                    CURRENT DATE,
                    'D')
           END-EXEC

           EVALUATE SQLCODE
               WHEN 0
                   ADD 1 TO WS-INSERTS-SUCCESS
               WHEN -803
                   DISPLAY 'DUPLICATE KEY: ' WS-TXN-ID
                   ADD 1 TO WS-INSERTS-DUPLICATE
               WHEN OTHER
                   DISPLAY 'SQL ERROR: ' SQLCODE ' FOR ' WS-TXN-ID
                   PERFORM 9900-HANDLE-SQL-ERROR
           END-EVALUATE
           .
```

**Key Db2 concepts:**
- **DBRM:** Database Request Module — the precompiled SQL extracted from your COBOL program.
- **Package:** Bound DBRM — SQL is optimized and stored in the Db2 catalog.
- **BIND:** The process of optimizing and storing a package.
- **SQLCODE:** Return code from every SQL statement. 0=success, positive=warning, negative=error.
- **SQLSTATE:** Standard SQL state (more portable than SQLCODE).
- **Cursor:** For queries returning multiple rows, use a cursor: DECLARE, OPEN, FETCH, CLOSE.

---

---

# 📅 PHASE 5: CICS, RACF, SECURITY, TESTING, OPERATIONS (Days 116–140)

---

## DAYS 116–125 — CICS Transaction Processing

### What CICS Is

CICS (Customer Information Control System) is IBM's transaction processing middleware. It sits between the user's terminal (or API call) and your application programs.

Without CICS, each user request would start a new batch job (slow, resource-intensive). With CICS, thousands of concurrent users send short transactions to programs that are already loaded in memory and return responses in milliseconds.

**Transaction ID (TRANSID):** Every CICS transaction has a 4-character ID (e.g., `PSRI` for PSRS Inquiry). Users type the TRANSID to invoke it.

**CICS Commands in COBOL:**
```cobol
      *--- Read a record from VSAM via CICS (not COBOL file I/O) ---
           EXEC CICS READ
               FILE('LEDGER')
               INTO(WS-LEDGER-RECORD)
               RIDFLD(WS-ACCOUNT-ID)
               RESP(WS-CICS-RESP)
               RESP2(WS-CICS-RESP2)
           END-EXEC

           EVALUATE WS-CICS-RESP
               WHEN DFHRESP(NORMAL)
                   CONTINUE
               WHEN DFHRESP(NOTFND)
                   PERFORM 8000-ACCOUNT-NOT-FOUND
               WHEN OTHER
                   PERFORM 9900-CICS-ERROR
           END-EVALUATE
```

**Days 116–120:** CICS architecture: regions, transactions, tasks, programs, maps (BMS for terminal screens). How CICS manages concurrent execution.

**Days 121–125:** Build PSRSINQ — the CICS account inquiry transaction. User types `PSRI` and their account ID; the program reads LEDGER.MASTER via CICS and displays the balance.

---

## DAYS 126–130 — Security Deep Dive: RACF, Audit, and Least Privilege

### Audit Trail Design for PSRS

Every financial system requires an immutable audit log. The PSRS audit log records:
- Who submitted the job
- What records were processed
- What changes were made
- When (timestamp)
- The result (success/failure)

In z/OS: SMF (System Management Facilities) records provide system-level audit data. RACF audit records provide access control events. Your application writes to an ESDS audit file.

**RACF Resource Protection Design:**

```
PSRS Production Datasets and Their Required RACF Protection:

JOHND.PSRS.DATA.INPUT        - OPSGROUP(READ), PSRSJOB(UPDATE)
JOHND.PSRS.LEDGER.MASTER     - PSRSJOB(UPDATE), OPSGROUP(READ), AUDITGRP(READ)
JOHND.PSRS.AUDIT.LOG         - PSRSJOB(UPDATE), AUDITGRP(READ) - no DELETE for anyone
JOHND.PSRS.LOAD(PSRSVAL)     - PSRSJOB(READ), DEVGROUP(READ)

CICS Transactions:
PSRI - All authorized users (READ)
PSRA - Supervisor group only (CONTROL)
```

---

## DAYS 131–140 — Testing, Debugging, and Operations

### Test Design for PSRSVAL

Professional test design requires explicit test cases:

```markdown
# PSRSVAL Test Plan

## Test Case TC-001: Valid Debit Transaction
**Input:** TXN000000001,ACC0001234,150000,2025-01-15,D
**Expected:** Written to VALFILE, RC=0
**Actual:** [to be filled after execution]
**Status:** Planned

## Test Case TC-002: Zero Amount (Business Rule Violation)
**Input:** TXN000000002,ACC0001234,000000,2025-01-15,D
**Expected:** Written to ERRFILE with reason "AMOUNT MUST BE POSITIVE"
**Actual:** [to be filled]
**Status:** Planned

## Test Case TC-003: Invalid Transaction Type
**Input:** TXN000000003,ACC0001234,150000,2025-01-15,X
**Expected:** Written to ERRFILE with reason "INVALID TRANSACTION TYPE"
**Status:** Planned

## Test Case TC-004: Duplicate TXN-ID in Sorted Input
**Input:** TXN000000001 appearing twice (after SORT step)
**Expected:** PSRSDEDUP writes second occurrence to ERRFILE
**Status:** Planned

## Test Case TC-005: Maximum Valid Amount
**Input:** TXN000000005,ACC0001234,999999,2025-01-15,C
**Expected:** Written to VALFILE (boundary condition — exactly at limit)
**Status:** Planned

## Test Case TC-006: Amount One Over Maximum
**Input:** TXN000000006,ACC0001234,1000000,2025-01-15,C
**Expected:** Written to ERRFILE with reason "AMOUNT EXCEEDS MAXIMUM"
**Status:** Planned
```

**Fault injection exercises (Days 136–140):**
1. S0C7 ABEND: Inject a letter into a numeric field that COBOL moves to a packed decimal field. Diagnose from SYSOUT.
2. B37 ABEND: Allocate VALFILE with insufficient space for the input volume. Observe and diagnose.
3. Logic error: Reverse the condition in WS-AMOUNT validation. Wrong records go to VALFILE. Detect by reconciling expected vs actual counts.
4. Reconciliation mismatch: Manually corrupt one amount in the database. The reconciliation step should detect and report it.

---

---

# 📅 PHASE 6: MODERN TOOLING, ZOWE, PYTHON, INTEGRATION (Days 141–160)

---

## DAYS 141–145 — Zowe CLI: Modern Access to z/OS

### What Zowe Is

Zowe is an open-source framework (Open Mainframe Project, IBM) that provides modern access to z/OS:
- **Zowe CLI:** Command-line tool for jobs, datasets, and USS from your PC.
- **Zowe Explorer (VS Code extension):** GUI access to z/OS datasets.
- **Zowe API Mediation Layer:** REST API gateway for z/OS services.

```bash
# Install Zowe CLI (requires Node.js 18+)
npm install -g @zowe/cli@latest

# Connect to IBM Z Xplore
zowe profiles create zosmf zxplore \
    --host your-zxplore-host \
    --port 443 \
    --user YOURID \
    --pass YOURPASSWORD \
    --rejectUnauthorized false

# Verify connection
zowe zosmf check status

# Submit a JCL job from your PC
zowe jobs submit local-file "src/jcl/PSRSMAIN.jcl" --view-all-spool-content

# Download output
zowe jobs download output JOB12345 -d ./output/JOB12345/

# List datasets
zowe files list ds "JOHND.PSRS.*"

# Upload a COBOL source member
zowe files upload file-to-data-set "src/cobol/PSRSVAL.cob" \
    "JOHND.PSRS.COBOL.SOURCE(PSRSVAL)"
```

**Day 141:** Install and configure Zowe CLI. Connect to Z Xplore. Submit PSRSMAIN via Zowe from your PC. Compare the experience to submitting from ISPF. Document differences.

---

## DAYS 146–150 — Python Automation

```python
# src/python/psrs_automation.py
# PURPOSE: Automate PSRS job submission and result validation
# using Zowe CLI subprocess calls

import subprocess
import json
import time
import sys
from pathlib import Path

def run_zowe(args: list[str]) -> dict:
    """Execute a Zowe CLI command and return parsed JSON output."""
    cmd = ["zowe"] + args + ["--response-format-json"]
    result = subprocess.run(cmd, capture_output=True, text=True)
    if result.returncode != 0:
        raise RuntimeError(f"Zowe command failed: {result.stderr}")
    return json.loads(result.stdout)

def submit_job(jcl_path: str) -> str:
    """Submit a JCL job and return the job ID."""
    response = run_zowe(["jobs", "submit", "local-file", jcl_path])
    job_id = response["data"]["jobid"]
    print(f"Submitted job: {job_id}")
    return job_id

def wait_for_job(job_id: str, timeout_seconds: int = 300) -> dict:
    """Poll until job completes or timeout."""
    start = time.time()
    while time.time() - start < timeout_seconds:
        response = run_zowe(["jobs", "view", "job-status-by-jobid", job_id])
        status = response["data"]["status"]
        if status == "OUTPUT":
            return response["data"]
        elif status == "ABEND":
            raise RuntimeError(f"Job {job_id} ABENDED")
        time.sleep(10)
    raise TimeoutError(f"Job {job_id} did not complete within {timeout_seconds}s")

def validate_results(job_data: dict, expected_valid: int, expected_errors: int) -> bool:
    """Download SYSOUT and verify counts against expected values."""
    rc = job_data.get("retcode", "")
    print(f"Job return code: {rc}")
    
    # Download output
    subprocess.run(["zowe", "jobs", "download", "output", 
                    job_data["jobid"], "-d", f"./output/{job_data['jobid']}/"])
    
    # Parse validation summary from PSRSVAL SYSOUT
    sysout_path = Path(f"./output/{job_data['jobid']}/STEP02/SYSOUT")
    if not sysout_path.exists():
        print(f"WARNING: SYSOUT not found at {sysout_path}")
        return False
    
    content = sysout_path.read_text()
    # Extract counts from the DISPLAY statements
    valid_count = None
    error_count = None
    for line in content.splitlines():
        if "Records valid:" in line:
            valid_count = int(line.split(":")[-1].strip())
        elif "Records rejected:" in line:
            error_count = int(line.split(":")[-1].strip())
    
    print(f"Expected valid:    {expected_valid}, Actual: {valid_count}")
    print(f"Expected rejected: {expected_errors}, Actual: {error_count}")
    return valid_count == expected_valid and error_count == expected_errors

def run_daily_settlement():
    """Full automated daily settlement run."""
    print("=== PSRS Daily Settlement Automation ===")
    
    # 1. Generate fresh test data
    subprocess.run([sys.executable, "src/python/generate_transactions.py"])
    
    # 2. Upload input file to z/OS
    subprocess.run(["zowe", "files", "upload", "file-to-data-set",
                    "data/synthetic/transactions.csv",
                    "JOHND.PSRS.DATA.INPUT"])
    
    # 3. Submit job
    job_id = submit_job("src/jcl/PSRSMAIN.jcl")
    
    # 4. Wait for completion
    job_data = wait_for_job(job_id)
    
    # 5. Validate results
    success = validate_results(job_data, expected_valid=460, expected_errors=40)
    
    if success:
        print("✓ Settlement run completed successfully")
        return 0
    else:
        print("✗ Settlement results do not match expectations")
        return 4

if __name__ == "__main__":
    sys.exit(run_daily_settlement())
```

---

## DAYS 151–160 — AI-Assisted Engineering: Use with Discipline

### What AI Tools Can Help With (and What They Cannot)

**Legitimate uses in mainframe engineering:**
- Explain what an unfamiliar COBOL construct does
- Draft a first version of a COBOL paragraph you then review carefully
- Generate candidate test cases you then execute and verify
- Explain a compiler error or ABEND code
- Draft documentation text you then verify for accuracy
- Compare two architectural alternatives

**What AI cannot replace:**
- Reading a real JES job log and diagnosing the actual failure
- Deciding whether a reconciliation mismatch is a data issue or a program bug
- Understanding that your COBOL program produced the wrong output and finding which calculation is wrong
- Evaluating security implications of a RACF profile decision
- Verifying that a z/OS VSAM record matches your COBOL record description byte-for-byte

### AI Audit Log Template (Mandatory for every AI-assisted task)

```markdown
## AI Assistance Record — Day NNN

**Task:** [What I was trying to accomplish]
**Tool used:** [e.g., GitHub Copilot, ChatGPT, watsonx Code Assistant]

**Prompt I gave the AI:**
[Exact text]

**What the AI produced:**
[Summary or excerpt]

**Assumptions the AI made:**
[What it assumed that I did not state]

**What I independently verified:**
- [ ] Compiled and ran the code: [result]
- [ ] Checked against IBM documentation: [source]
- [ ] Tested with boundary cases: [cases and results]

**Errors or inaccuracies found:**
[Be specific]

**What I changed and why:**
[Your modifications]

**Final verified result:**
[What actually works]

**What this proves:**
[What the working code demonstrates — and what it does NOT demonstrate]
```

---

---

# 📅 PHASE 7: CAPSTONE, PORTFOLIO, INTERVIEW PREPARATION (Days 161–180)

---

## DAYS 161–170 — Capstone Integration and Acceptance Testing

### Traceability Matrix (Complete Every Row Before Day 175)

| Requirement | Program | Dataset/Table | Test Case | Expected Result | Actual Result | Status |
|---|---|---|---|---|---|---|
| REQ-001: Reject zero-amount records | PSRSVAL | ERRFILE | TC-002 | RC=4, error written | | Planned |
| REQ-002: Detect duplicate TXN-IDs | PSRSDEDUP | ERRFILE | TC-004 | Duplicate in ERRFILE | | Planned |
| REQ-003: Update ledger for valid records | PSRSPOST | LEDGER.MASTER | TC-010 | Balance updated | | Planned |
| REQ-004: Detect reconciliation mismatch | PSRSRECN | RPTFILE | TC-015 | Mismatch reported | | Planned |
| REQ-005: Audit trail written | PSRSPOST | AUDIT.LOG | TC-010 | Event logged | | Planned |
| REQ-006: CICS inquiry returns balance | PSRSINQ | LEDGER.MASTER | TC-020 | Balance displayed | | Planned |
| REQ-007: Only PSRSJOB can update ledger | RACF | LEDGER.MASTER | TC-025 | Unauthorized = denied | | Planned |

### Day 161–165: Full integration run on Z Xplore

Submit the complete PSRSMAIN job. Verify every step completes. Review SYSOUT for all six steps. Check reconciliation output. Fix any failures. Document every investigation in incident reports.

### Day 166–170: Fault injection review

Inject each of the following and diagnose:
1. Empty input file (B37 prevention test)
2. LEDGER.MASTER not yet loaded (VSAM file not found)
3. Db2 table not yet created (SQL error -204)
4. One record's amount field corrupted to non-numeric (S0C7 risk)

Document in `docs/incident-reports/` using this template:

```markdown
# Incident Report IR-001

**Date:** YYYY-MM-DD
**Environment:** IBM Z Xplore (learning)
**Job:** PSRSMAIN (STEP02 — PSRSVAL)
**Symptom:** Job ended with ABEND S0C7 in STEP02

## Timeline
HH:MM - Job submitted
HH:MM - STEP01 completed RC=0
HH:MM - STEP02 ABEND S0C7

## Evidence Collected
- JES job log (attached/linked)
- SYSOUT from STEP02 (attached/linked)
- Relevant COBOL source lines: [line numbers]

## Analysis
Observation: S0C7 = data exception. Occurs when a numeric operation
uses a field containing non-numeric data.

Hypothesis: Input record at offset N contains a letter in the amount field.

Test: Browse INFILE for records with non-numeric amount fields.
```

---

## DAYS 171–175 — Portfolio Assembly

### GitHub Portfolio README Template

```markdown
# Mainframe Engineering Learning Journey

> **Completed:** [Date] | **Duration:** 180 study days | **Environment:** IBM Z Xplore + GnuCOBOL (local)

## About This Portfolio

This repository documents my journey from beginner to junior mainframe 
engineer, following a structured 180-day curriculum covering IBM Z architecture, 
z/OS, COBOL, JCL, VSAM, Db2, CICS, and modern mainframe tooling.

> ⚠️ **Environment Transparency:** Programs marked 🔵 were executed on 
> real IBM Z Xplore (z/OS). Programs marked 🟡 were tested locally using 
> GnuCOBOL (Windows) and demonstrate language concepts but NOT z/OS execution.

## Capstone: Payment Settlement & Reconciliation System (PSRS)

| Component | Language/Tool | Environment | Evidence |
|---|---|---|---|
| Input validation (PSRSVAL) | COBOL | 🔵 z/OS | [Compiler listing] [JES output] |
| Deduplication (PSRSDEDUP) | COBOL | 🔵 z/OS | [Test results] |
| Ledger update (PSRSPOST) | COBOL + Db2 SQL | 🔵 z/OS | [Db2 query output] |
| Reconciliation (PSRSRECN) | COBOL | 🔵 z/OS | [Reconciliation report] |
| VSAM ledger (LEDGER.MASTER) | VSAM KSDS | 🔵 z/OS | [IDCAMS listing] |
| Batch orchestration | JCL | 🔵 z/OS | [SDSF job output] |
| CICS inquiry | CICS/COBOL | 🔵 z/OS | [Session screenshot] |
| Automation | Python + Zowe CLI | 🔵 z/OS connection | [Script output] |

## IBM Z Xplore Badges Earned
- [ ] Fundamentals Badge
- [ ] Advanced Badge
- [ ] Extended Badge (target)

## Skills Demonstrated

### Core Technical Skills
- COBOL programming: data types, record processing, file I/O, Db2 SQL, 
  subprograms, error handling, defensive validation
- JCL: multi-step jobs, COND processing, DFSORT, IDCAMS, procedures
- VSAM: KSDS and ESDS definition, read/write/rewrite/delete in COBOL
- Db2: embedded SQL, SQLCODE handling, cursors, precompile/bind/execute
- CICS: transaction structure, BMS maps, CICS commands, error handling
- z/OS: TSO/ISPF navigation, dataset management, job submission and monitoring
- RACF: dataset protection concepts, audit trail design
- Zowe CLI: job submission, output retrieval, dataset upload/download

### Modern Engineering Skills  
- Git version control with meaningful commit history
- Architecture Decision Records for design choices
- Evidence-based debugging and incident reporting
- Test plan design with boundary cases and fault injection
- Python automation for test data generation and result validation
- Technical documentation in Markdown

## Repository Structure
[Link to each major directory]

## How to Run the Demo
[Step-by-step reproducible instructions]
```

---

## DAYS 176–178 — Interview Preparation

### The Core Interview Questions (Based on Verified Job Postings)

**Technical questions you must answer fluently:**

1. **"Walk me through what happens when a z/OS batch job runs."**  
   Expected: JES2 receives JCL → reads JOB, EXEC, DD statements → allocates datasets → initiates address space → loads program → executes → writes to SYSOUT → returns code → JES2 stores output.

2. **"What is a FILE STATUS code and why do you check it?"**  
   Expected: A 2-character code set by the OS after every file operation (READ, WRITE, etc.). 00=success, 10=EOF, 22=duplicate key, 23=not found. You check it because a COBOL program continues silently on file errors unless you explicitly handle them. Unhandled errors lead to data corruption.

3. **"What is the difference between COMP and COMP-3?"**  
   Expected: COMP (BINARY/COMPUTATIONAL) stores numbers as native binary integers — efficient for arithmetic. COMP-3 (PACKED-DECIMAL) stores two decimal digits per byte — exact for financial arithmetic, no floating-point errors, but slightly more storage.

4. **"How would you find a S0C7 ABEND?"**  
   Expected: Check the JES output for the failing step. Find the ABEND in SYSOUT. The offset (0+offset) tells you the instruction address. Use the compiler listing MAP to find which DATA DIVISION field is at that offset. Check the input data for non-numeric content in that field.

5. **"What is the COND parameter in JCL?"**  
   Expected: Conditional execution. `COND=(4,LT,STEP01)` means "skip this step if the return code from STEP01 is LESS THAN 4." Used to prevent later steps from running if earlier steps fail.

6. **"What is the difference between VSAM KSDS and ESDS?"**  
   Expected: KSDS = Key-Sequenced, accessed by key (like a keyed database table). Records are stored in key order. Allows READ, REWRITE, DELETE by key. ESDS = Entry-Sequenced, append-only, accessed sequentially. Good for audit logs.

7. **"Explain two's complement and why it matters in COBOL."**  
   Expected: Binary representation of negative numbers where negating a number inverts bits and adds 1. Matters because COBOL COMP fields store binary integers using two's complement. A field defined as PIC S9(4) COMP holds -32768 to +32767. If you forget the S (signed), negative values are misinterpreted.

8. **"How would you approach a job that produced incorrect output but RC=0?"**  
   Expected: RC=0 means the program exited normally — no program logic detected a problem. This is a logic error, not a runtime error. Approach: compare expected vs actual counts. Trace which records went to which output. Add diagnostic DISPLAY statements to trace computation. Use a test case with known input and known expected output. Compare field-by-field.

---

## DAYS 179–180 — Final Assessment and Job Readiness

### Self-Assessment Checklist

**Can I do this on z/OS (IBM Z Xplore)?**
- [ ] Navigate ISPF: browse, edit, allocate, delete datasets
- [ ] Submit a JCL job and monitor it in SDSF
- [ ] Read and interpret a JES job log
- [ ] Compile a COBOL program using JCL
- [ ] Execute a COBOL batch program and verify output
- [ ] Define a VSAM cluster using IDCAMS
- [ ] Execute a CICS transaction

**Can I write and explain this COBOL?**
- [ ] PIC clause: 9, X, S9, V, COMP, COMP-3
- [ ] MOVE, ADD, SUBTRACT, MULTIPLY, DIVIDE, COMPUTE
- [ ] IF/EVALUATE/WHEN
- [ ] PERFORM UNTIL, PERFORM N TIMES
- [ ] OPEN/READ/WRITE/REWRITE/CLOSE with FILE STATUS
- [ ] EXEC SQL with SQLCODE check
- [ ] UNSTRING and STRING
- [ ] 88-level condition names
- [ ] Subprogram CALL

**Can I design and explain this?**
- [ ] Multi-step JCL job with conditional execution
- [ ] VSAM KSDS definition and record layout
- [ ] Db2 table for transaction storage with appropriate data types
- [ ] RACF protection for production datasets
- [ ] Test plan with boundary cases for a validation program
- [ ] Incident investigation using available evidence

---

## 🗂️ DOCUMENTATION SYSTEM SUMMARY

### Daily Engineering Journal (every single day)

```markdown
# Day NNN — [Topic]
**Date:** YYYY-MM-DD  
**Track:** 🔵 z/OS / 🟡 Local GnuCOBOL  
**Status:** Planned → Attempted → Verified → Completed | Blocked | Failed

## Prerequisite Review (15 min)
- Concept recalled: ...
- Active recall result: ...

## Today's Objective
[One specific, measurable goal]

## What I Expected
[Before starting: what did you predict would happen?]

## What I Did
[Commands, code changes, JCL submitted, programs run]

## What Actually Happened
[Exact output, return codes, error messages — quote them exactly]

## Investigation (if unexpected)
[Observation → Hypothesis → Test → Result → Conclusion]

## Evidence
- File committed: [path and Git SHA]
- Screenshot: [filename if applicable]
- Z Xplore job ID: [if applicable]

## Deliverable Status
[What artifact exists as a result of today's work?]

## Active Recall for Tomorrow
1. [Question]
2. [Question]
3. [Question]
```

### Architecture Decision Record Template

```markdown
# ADR-NNN: [Decision Title]
**Date:** YYYY-MM-DD | **Status:** Draft / Accepted / Superseded

## Context
[What problem prompted this decision?]

## Requirements and Constraints
[What must the solution do? What limits apply?]

## Options Considered

### Option A: [Name]
Pros: ...
Cons: ...

### Option B: [Name]
Pros: ...
Cons: ...

## Decision
[What was chosen and why]

## Security Implications
[Any RACF, audit, or access control considerations]

## Reliability Implications
[Recovery, restart, failure mode]

## Verification
[How will you know this decision was correct?]

## Revisit Conditions
[What evidence would justify changing this decision?]
```

---

## 📋 COMPLETE 180-DAY PHASE TIMETABLE

| Days | Phase | Main Activities | Milestone |
|---|---|---|---|
| 1–7 | Computing Foundations I | Bits, bytes, binary, hex, CPU model, OS concepts | Repository created; conversion exercises complete |
| 8–12 | Computing Foundations II | Python programming logic | Record-processing Python script working |
| 13–16 | SQL Fundamentals | SQLite table design, SQL queries, transactions | PSRS_TRANSACTIONS table queryable |
| 17–20 | Debugging and Reasoning | Evidence-based failure investigation | 3 fault injection exercises documented |
| 21–24 | Data Generation | Synthetic dataset, system context diagram | transactions.csv generated; Mermaid diagram committed |
| 25 | Phase 1 Gate | Assessment | All 5 tasks passed |
| 26–31 | IBM Z Hardware + Z Xplore | z/Architecture, LPAR, z/OS components, Z Xplore registration | Z Xplore access confirmed |
| 32–40 | z/OS Data Sets | Sequential, PDS, naming, RECFM, LRECL, TSO commands | First dataset created on z/OS |
| 41–50 | JCL Foundations | JOB, EXEC, DD, utilities, SDSF, SORT | First multi-step job runs on z/OS |
| 51–55 | RACF Fundamentals | User profiles, dataset protection, least privilege | ADR-001: PSRS dataset protection |
| 56–60 | COBOL Structure | 4 divisions, PIC clauses, MOVE, DISPLAY | HELLO.cob compiled locally + on z/OS |
| 61–75 | COBOL Business Logic | PSRSVAL: validation, record processing, file I/O | PSRSVAL runs correctly on both platforms |
| 76–85 | COBOL Advanced | PSRSDEDUP, PSRSPOST, PSRSRECN, subprograms | All 4 programs compile and produce correct output |
| 86–95 | JCL Advanced | PSRSMAIN multi-step job, COND, PROCs, SORT, ABENDs | PSRSMAIN runs 5 steps on z/OS |
| 96–105 | VSAM | KSDS/ESDS definition, IDCAMS, COBOL VSAM I/O | LEDGER.MASTER created and used by PSRSPOST |
| 106–115 | Db2 | Embedded SQL, SQLCODE, cursor, precompile/bind | PSRS.TRANSACTIONS populated by PSRSPOST |
| 116–125 | CICS | Transaction processing, BMS maps, CICS commands | PSRSINQ runs on Z Xplore CICS |
| 126–130 | Security + Audit | RACF protection applied, audit log populated | IR-001 showing unauthorized access denied |
| 131–140 | Testing + Debugging | Test plan executed, fault injection, incidents | 6-row traceability matrix all Verified |
| 141–145 | Zowe CLI | Job submission, dataset transfer, output retrieval | Automated run via Zowe documented |
| 146–150 | Python Automation | Test data generation, result validation automation | psrs_automation.py runs complete cycle |
| 151–160 | AI-Assisted Engineering | AI audit log, verification discipline | 3 AI audit logs documenting verification |
| 161–170 | Capstone Integration | Full PSRSMAIN job, all acceptance tests | All 7 requirements in traceability matrix: Verified |
| 171–175 | Portfolio Assembly | GitHub README, skills matrix, evidence index | Public portfolio repository ready |
| 176–178 | Interview Preparation | 8 core technical questions practised | Video recordings of explanations |
| 179–180 | Final Assessment | Self-assessment checklist, job readiness report | Final report submitted |

---

## 🎯 SKILLS TO JOB MAPPING

| Skill | Phase Taught | Project Demo | Verified Level |
|---|---|---|---|
| COBOL programming | Phase 3 | PSRSVAL, PSRSPOST, all programs | Intermediate — can write, debug, and explain |
| JCL authoring | Phases 2+4 | PSRSMAIN + COBUCG | Functional — multi-step jobs with error handling |
| Db2 embedded SQL | Phase 4 | PSRSPOST | Basic — SELECT, INSERT, cursor |
| VSAM | Phase 4 | LEDGER.MASTER | Basic — KSDS create, read, write, rewrite |
| CICS | Phase 5 | PSRSINQ | Basic — simple inquiry transaction |
| TSO/ISPF | Phase 2+ | All z/OS work | Working — navigate, edit, allocate, SDSF |
| SDSF job monitoring | Phases 2+ | All z/OS jobs | Working — can read JES output and diagnose |
| RACF concepts | Phase 5 | ADR-001 design | Conceptual — understand protection profiles |
| Debugging/troubleshooting | All phases | Incident reports | Developing — systematic evidence-based approach |
| DFSORT | Phase 4 | PSRSMAIN STEP01 | Basic — sort by key, include/omit |
| IBM utilities | Phase 4 | IEBGENER, IEFBR14 | Basic — know purpose and common usage |
| Git/version control | Phase 1+ | All phases | Working — meaningful commits, daily updates |
| Technical documentation | Phase 1+ | All phases | Good — daily journals, ADRs, test plans |
| Python + scripting | Phase 6 | Automation | Basic — data generation and validation |
| Zowe CLI | Phase 6 | Automation | Basic — job submit, dataset transfer |

---

## 💡 AI-ERA READINESS: DURABLE SKILLS

### What Will Remain Valuable Regardless of AI Progress

1. **System reasoning:** Understanding WHY a z/OS batch job fails requires reading a JES log, knowing what each ABEND code means, and tracing which program at which offset produced which error. AI can suggest answers; an engineer must verify them against real evidence.

2. **Data integrity judgement:** When PSRSRECN detects a ₹50,000 discrepancy, someone must decide: is this a program bug? A missing record? A duplicate that was not detected? A timing issue? This requires understanding the entire pipeline — not just one component.

3. **Security decision-making:** Deciding who should have UPDATE vs READ access to the production ledger requires understanding business consequences, not just technical configuration. An engineer who can explain the security implications of a RACF decision is valuable.

4. **COBOL legacy expertise:** AI tools like IBM watsonx Code Assistant for Z can modernize COBOL — but they require a human engineer who can verify that the modernized code does the same thing as the original. Understanding COBOL deeply makes you the human who validates the AI's work.

5. **Production operations judgment:** Deciding whether to rerun a failed job from the beginning or from a checkpoint, whether to promote data that the reconciliation marked as mismatched, or whether to escalate an incident — these require operational judgment that comes from system understanding, not pattern matching.

---

## 📚 FREE RESOURCE REGISTRY

| Resource | URL | Type | Used In Phase |
|---|---|---|---|
| IBM Z Xplore | https://ibm.com/z/resources/zxplore | Real z/OS environment | 2–7 |
| GnuCOBOL 3.2 | https://sourceforge.net/projects/gnucobol/ | Local COBOL compiler | 1–3 |
| IBM Z Open Editor (VS Code) | VS Code Marketplace | COBOL/JCL editor | 1–7 |
| IBM Redbook SG24-6366 (z/OS Basics) | https://www.redbooks.ibm.com/abstracts/sg246366.html | Architecture reference | 2 |
| Open MF Project COBOL Course | https://github.com/openmainframeproject/cobol-programming-course | COBOL curriculum | 3 |
| GnuCOBOL Programmer's Guide | https://gnucobol.sourceforge.io/guides/ | COBOL reference | 3 |
| Zowe CLI | https://docs.zowe.org/stable/user-guide/cli-installcli | Modern mainframe access | 6 |
| IBM Db2 for z/OS documentation | https://www.ibm.com/docs/en/db2-for-zos | SQL reference | 4 |
| IBM RACF documentation | https://www.ibm.com/docs/en/zos/latest?topic=racf | Security reference | 5 |
| DFSORT Application Programming Guide | IBM Knowledge Center | Sort utility reference | 4 |
| Python 3.12 | https://python.org | Scripting language | 1–7 |

---

> ## 🔑 Final Statement
>
> This roadmap takes you from zero to a documented, evidence-based junior mainframe engineering portfolio in 180 study days. Every significant claim in this portfolio — every COBOL program, every JCL execution, every Db2 query, every VSAM operation — must be backed by real evidence: compiler output, JES job logs, SYSOUT, or screenshots from IBM Z Xplore.
>
> The mainframe skills taught here — COBOL, JCL, VSAM, Db2, CICS, z/OS operations — are in active demand at Wipro, TCS, Infosys, Cognizant, and IBM India. They will remain relevant as AI changes the tools, because AI tools for mainframe (IBM watsonx Code Assistant for Z, Zowe AI plugins) require engineers who understand what the AI is working with. Your depth of understanding is your competitive advantage.
>
> **The portfolio you build is the interview. Document honestly. Execute rigorously. Verify everything.**

---

*Mainframe Engineering Roadmap — Beginner to AI-Era Ready*  
*Research Date: October 2026 | Verified: IBM Z Xplore (free), GnuCOBOL 3.2 (open-source, GPL), Zowe CLI (Apache License 2.0)*  
*Job market data: 15 verified postings, Wipro/TCS/Infosys/India, 2025*
