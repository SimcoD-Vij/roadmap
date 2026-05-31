# EmbeddedAI Project Roadmap
### MNC-Standard, Production-Grade, Fully Open-Source
#### From Absolute Zero to a Hardware-Aware, Self-Healing AI Debugging Framework

---

> **Who this is for:** Someone with zero Python, zero hardware, and zero AI knowledge,
> building toward an industrial-grade embedded AI debugging system that would be
> considered production-quality at a company like Bosch, Siemens, ARM, or Texas Instruments.
>
> **Documentation philosophy:** Every single day generates a GitHub commit, a journal
> entry, and one documented learning. By the end of this roadmap, your repository
> becomes your portfolio — proof of deliberate, connected, progressive work.

---

## PART 0 — BEFORE YOU START: UNDERSTAND WHAT YOU ARE BUILDING

Read this section completely before Day 1. You need to understand the destination
before you understand why each learning step matters.

---

### What Is EmbeddedAI?

EmbeddedAI is a framework — a tool that other developers install into their projects
— that does three things simultaneously:

First, it watches a software application or firmware running on a microcontroller in
real time, capturing every error, every anomaly, and every behavioral pattern it
observes.

Second, it stores everything it observes in a persistent memory system that grows
smarter over time — remembering past bugs, the fixes that worked, the fixes that
failed, and the decisions developers made. This memory is private to that specific
codebase and never resets.

Third, when something goes wrong, it retrieves the most relevant history from memory,
sends it to a large language model with full context, and either suggests a precise
fix or applies one autonomously — like a senior engineer who has been living inside
that codebase for years.

The reason this does not exist today is that it requires someone who understands both
firmware on physical hardware and AI memory systems simultaneously. That combination
is what this roadmap builds.

---

### The Complete System Architecture

Study this architecture diagram carefully. Every phase of this roadmap builds one
labeled component. When you feel lost on any given day, return here and ask: which
component am I building knowledge toward right now?

```
╔══════════════════════════════════════════════════════════════════════════╗
║              EMBEDDEDAI — PRODUCTION ARCHITECTURE                        ║
║                   MNC-Grade / Fully Open Source                          ║
╠══════════════════════════════════════════════════════════════════════════╣
║                                                                          ║
║  LAYER 1 — PHYSICAL LAYER                          [Phase 2]            ║
║  ┌────────────────────────────────────────────────────────────────┐     ║
║  │  STM32 Nucleo Board  ──or──  Wokwi / Renode Simulator         │     ║
║  │  FreeRTOS Tasks │ Flash Memory │ DMA │ Interrupts │ NVIC      │     ║
║  │  JTAG/SWD Debug Port │ UART/USB │ Hardware Timers             │     ║
║  └───────────────────────────┬────────────────────────────────────┘     ║
║                              │                                           ║
║  LAYER 2 — OBSERVATION LAYER               [Phase 2]                    ║
║  ┌────────────────────────────────────────────────────────────────┐     ║
║  │  OpenOCD + GDB Server  ──  Python GDB Bridge                  │     ║
║  │  Segger RTT Telemetry  ──  SVD Register Parser                │     ║
║  │  FreeRTOS Trace Hooks  ──  Hard Fault Handler                 │     ║
║  │  Renode Simulation Layer  ──  Wokwi MCP Agent Interface       │     ║
║  └───────────────────────────┬────────────────────────────────────┘     ║
║                              │                                           ║
║  LAYER 3 — INGESTION LAYER                 [Phase 2-3]                  ║
║  ┌────────────────────────────────────────────────────────────────┐     ║
║  │  Apache Kafka — Event Streaming Bus                           │     ║
║  │  OpenTelemetry SDK — Structured trace and span data           │     ║
║  │  Fluentd — Log aggregation and normalization                  │     ║
║  │  FastAPI — Internal service API layer                         │     ║
║  └───────────────────────────┬────────────────────────────────────┘     ║
║                              │                                           ║
║  LAYER 4 — KNOWLEDGE LAYER                 [Phase 3]                    ║
║  ┌────────────────────────────────────────────────────────────────┐     ║
║  │  Codebase Knowledge Graph                                     │     ║
║  │  Tree-sitter (AST Parser) → NetworkX → graph.json            │     ║
║  │                                                               │     ║
║  │  Semantic Memory Store                                        │     ║
║  │  ChromaDB (dev) + PostgreSQL + pgvector (production)         │     ║
║  │  Git-backed context repository (memory = commits)            │     ║
║  │                                                               │     ║
║  │  Letta (MemGPT) — Tiered Memory Controller                   │     ║
║  │  Core Memory │ Archival Memory │ Recall Memory               │     ║
║  └───────────────────────────┬────────────────────────────────────┘     ║
║                              │                                           ║
║  LAYER 5 — REASONING LAYER                 [Phase 3]                    ║
║  ┌────────────────────────────────────────────────────────────────┐     ║
║  │  LLM Engine (local-first, no cloud dependency)               │     ║
║  │  Ollama → DeepSeek Coder V2 / CodeLlama (runs on laptop)     │     ║
║  │  Claude API / OpenAI API — optional cloud fallback           │     ║
║  │                                                               │     ║
║  │  LangGraph — Stateful Agent Workflow (cyclic reasoning)      │     ║
║  │  Tools: save_bug │ search_memory │ retrieve_history          │     ║
║  │  RAG Pipeline: retrieve → reason → validate → respond        │     ║
║  └───────────────────────────┬────────────────────────────────────┘     ║
║                              │                                           ║
║  LAYER 6 — HEALING LAYER                   [Phase 4]                    ║
║  ┌────────────────────────────────────────────────────────────────┐     ║
║  │  Self-Healing Agent                                           │     ║
║  │  Git patch generator → pytest runner → canary deployer       │     ║
║  │  Confidence scorer → auto-rollback on failure                │     ║
║  │  Wokwi/Renode simulation validator for firmware patches      │     ║
║  └───────────────────────────┬────────────────────────────────────┘     ║
║                              │                                           ║
║  LAYER 7 — INTERFACE LAYER                 [Phase 5]                    ║
║  ┌────────────────────────────────────────────────────────────────┐     ║
║  │  Tauri (Rust) + React — Desktop Application                  │     ║
║  │  Live dashboard: telemetry, memory browser, fix history      │     ║
║  │  VS Code Extension — embedded in developer workflow          │     ║
║  │  Python SDK — one-line integration: import embeddedai        │     ║
║  └────────────────────────────────────────────────────────────────┘     ║
╚══════════════════════════════════════════════════════════════════════════╝
```

---

### Why Each Technology Was Chosen

This section explains every technology decision. Read it now. Re-read it at the
start of each phase. When a recruiter or interviewer asks why you chose technology X
over Y, your answer is already here.

**Apache Kafka instead of direct database writes:**
In production, firmware generates thousands of events per second. Writing each one
directly to a database creates a bottleneck that slows everything. Kafka is an event
streaming bus — it receives events at any rate, buffers them reliably, and lets
multiple consumers read independently without slowing each other. Bosch, Siemens,
and every major industrial company use Kafka for exactly this pattern. Free and
open source.

**PostgreSQL with pgvector instead of a cloud vector database:**
Pinecone and Weaviate are expensive at scale and send your data to external servers.
PostgreSQL is the most trusted open-source database in existence. The pgvector
extension adds vector similarity search directly inside PostgreSQL, giving you
structured bug history and semantic search in one system, with transactions, backups,
and 30 years of reliability. Free and open source.

**ChromaDB alongside PostgreSQL:**
ChromaDB requires zero configuration and runs in memory during development.
PostgreSQL with pgvector is used in production for reliability and scale. You develop
fast with ChromaDB, then migrate to pgvector when you need production hardening. This
is the standard MNC pattern: simple for development, enterprise-grade for production.

**Ollama with DeepSeek Coder V2:**
Running the LLM locally means no API costs, no data leaving the device, and no
internet dependency. For embedded firmware customers in automotive, medical, and
aerospace — this is mandatory, not optional. Their firmware code cannot leave the
building. DeepSeek Coder V2 has the strongest performance on C and low-level systems
code of any open-source model. Ollama makes running it locally a single command.
Free and open source.

**LangGraph instead of simple LangChain:**
LangGraph models the AI agent's reasoning as a stateful graph where the agent can
loop, retrieve more information, reconsider, and arrive at a better answer through
multiple steps. Real debugging requires iterative investigation. A single-shot answer
is almost always wrong for complex firmware bugs. Production AI systems at every
major company use graph-based agent orchestration. Free and open source.

**Tauri instead of Electron:**
Electron wraps a full Chrome browser in your app, consuming hundreds of megabytes of
RAM. Tauri uses your system's native web renderer and a Rust backend, producing apps
ten times smaller and significantly faster. GitHub, Microsoft, and major open-source
projects are migrating from Electron to Tauri. Free and open source.

**Git as the memory backing store:**
Every memory the AI creates is stored as a file in a git repository. Every update is
a commit. This gives you a complete, auditable, branchable, mergeable history of
everything the AI ever learned. A new developer can clone the memory repository and
immediately give the AI full history of that codebase. No existing tool does this.

**OpenTelemetry for structured observability:**
OpenTelemetry is the industry standard for distributed tracing, adopted by Google,
Microsoft, and AWS. Using it means your firmware events are compatible with Grafana,
Jaeger, and every enterprise monitoring tool automatically — out of the box, without
any custom integration work.

---

### Documentation System — Set This Up on Day 1

**GitHub:** Create a public repository named `embeddedai-journey`. Every single day
you must make at least one commit. Even if it is only a notes file, it proves you
worked that day. This is non-negotiable.

**Hashnode:** Free developer blogging at hashnode.com. Publish one post per week.
Tag every post: `embedded-systems`, `ai`, `python`, `firmware`, `open-source`. These
posts appear on Google and are found by recruiters.

**Repository structure from Day 1:**
```
embeddedai-journey/
├── README.md                         ← Updated weekly
├── journal/
│   ├── week-01/
│   │   ├── day-01.md
│   │   ├── day-02.md
│   │   └── ...
├── phase-01-foundations/
├── phase-02-hardware/
├── phase-03-firmware/
├── phase-04-ai-memory/
├── phase-05-self-healing/
├── phase-06-interface/
├── projects/
│   ├── project-01-crash-simulator/
│   ├── project-02-ingestion-api/
│   └── ...
└── architecture/
    └── decisions/                    ← ADR files explaining every tech choice
```

**Daily journal template — use this every single day:**
```markdown
# Day [N] — [Date]

## What I Studied Today
[Topic and subtopic name]

## What I Built
[Exactly what code, circuit, or concept was produced]

## What I Understood
[Explain in your own words as if teaching someone else]

## What Confused Me
[Honest record — shows intellectual honesty to employers]

## How This Connects to EmbeddedAI
[Which architecture layer does this knowledge build toward]

## Tomorrow's Plan
[One sentence]
```

---

## PHASE 1 — HOW COMPUTERS ACTUALLY WORK
### Duration: 5 Weeks | Days 1 to 35
### Architecture Component: Foundation for all seven layers
### Why: You cannot build a hardware observer without understanding what hardware is.
### You cannot build a memory system without understanding what memory physically is.

---

## WEEK 1 — Binary, Logic, and How a Computer Thinks
### Days 1 to 7

---

### Day 1 — What a Computer Is at the Lowest Level

**Morning — Study (2 hours)**

Topics:
- What binary is and why computers use only 0 and 1
- The physical reason: a transistor is a switch, it is either on (1) or off (0)
- What a bit is — one binary digit, one transistor state
- What a byte is — 8 bits grouped together, represents 0 to 255
- What a word is — typically 32 bits on your STM32, the natural processing size
- Hexadecimal notation — why firmware uses 0x40021000 instead of 1073877000

Subtopics:
- Converting decimal to binary by repeated division by 2
- Converting binary to decimal by summing powers of 2
- Converting between binary and hexadecimal — every 4 bits is one hex digit
- Why 0xFF = 255, why 0x00 = 0, why 0x40021000 is a memory address

Study resource: Nand2Tetris Unit 1, nand2tetris.org — completely free. The single
best computer science foundation course ever written.

**Afternoon — Build (2 hours)**

Build using Claude to run it if needed:

A Python script that takes any decimal number and outputs:
- Its binary representation
- Its hexadecimal representation  
- How many bytes it requires
- Whether it fits in a byte, a halfword, or a word

**Evening — Document (30 minutes)**

Write day-01.md. Answer in your own words:
1. Why does a transistor being on or off translate to 1 and 0?
2. What does 0x40021000 mean and why do embedded developers write addresses this way?
3. Which component of the EmbeddedAI architecture will use hex addresses?
   Answer: The SVD parser in Layer 2 translates hex register addresses to names.

Commit to GitHub: `docs: day 1 journal — binary, hex, and computer foundations`

---

### Day 2 — Logic Gates: Every Computation Ever Made Uses These

**Morning — Study (2 hours)**

Topics:
- What a transistor becomes when connected to other transistors: a logic gate
- AND gate: output is 1 only when BOTH inputs are 1
- OR gate: output is 1 when EITHER input is 1
- NOT gate: output is the opposite of the input
- NAND gate: AND followed by NOT — output is 0 only when BOTH inputs are 1
- Why NAND is called the universal gate — you can build any other gate from NAND alone

Subtopics:
- Truth tables — the complete description of a gate's behavior
- XOR gate — output is 1 when inputs DIFFER — used in checksums and encryption
- How logic gates combine: two AND gates feeding an OR gate creates more complex logic
- A flip-flop — two NAND gates cross-connected create a circuit that remembers one bit

Study resource: Continue Nand2Tetris Unit 1. Ben Eater's YouTube channel
"Building an 8-bit computer from scratch" — watch the first three videos.

**Afternoon — Build (2 hours)**

Python script that simulates all basic logic gates:
- Functions: and_gate(a, b), or_gate(a, b), not_gate(a), nand_gate(a, b), xor_gate(a, b)
- A test that verifies every gate against its complete truth table
- A half_adder function built from xor_gate and and_gate that adds two single bits

**Evening — Document (30 minutes)**

Write day-02.md. Answer:
1. Why is NAND called the universal gate?
2. How does a flip-flop remember a bit — draw the two states
3. Which EmbeddedAI component relies on understanding how memory stores bits?
   Answer: The flash memory controller in Layer 1 that stores bug patterns.

---

### Day 3 — Memory: What RAM and Flash Actually Are

**Morning — Study (2 hours)**

Topics:
- Three types of memory in your STM32 and what each is for
- Flash memory — stores your firmware permanently, survives power-off, 1MB on STM32F4
- SRAM — stores variables while running, lost on power-off, 192KB on STM32F4
- Registers — tiny memory slots inside the CPU core itself, hold one 32-bit value each
- Why registers are faster than SRAM — they are part of the processor silicon itself

Subtopics:
- The stack — a region of SRAM that grows and shrinks as functions call and return
- The heap — a region of SRAM you request and release manually with malloc/free
- Stack overflow — when the stack grows into the heap or other memory: instant crash
- Why stack overflow is one of the most common embedded bugs you will encounter
- What happens to SRAM when power is removed — the bits literally lose their state

**Afternoon — Build (2 hours)**

Python script that simulates a simplified memory model:
- A class called MemoryModel with flash (read-only array), sram (read-write array),
  registers (dictionary of register names to values)
- Methods: read_flash(address), read_sram(address), write_sram(address, value),
  read_register(name), write_register(name, value)
- A simulation of a stack: push(value) and pop() that track the stack pointer register

**Evening — Document (30 minutes)**

Write day-03.md. Draw a memory map diagram showing Flash at 0x08000000, SRAM at
0x20000000. Write: what physically happens inside SRAM when you write the number
42 to address 0x20000004?

---

### Day 4 — The CPU: Fetch, Decode, Execute

**Morning — Study (2 hours)**

Topics:
- The three-stage pipeline every processor runs forever: Fetch, Decode, Execute
- Fetch: read the next instruction from Flash at the address in the Program Counter
- Decode: figure out what the instruction means
- Execute: carry out the operation — add, move, branch, compare
- The Program Counter (PC) register — always holds the address of the next instruction
- What a branch instruction is — sets PC to a new address, creating loops and if-statements

Subtopics:
- The Stack Pointer (SP) register — always holds the address of the top of the stack
- The Link Register (LR) — holds the return address when a function is called
- What happens to PC, SP, and LR during a function call — the exact sequence
- Interrupts — a hardware signal that pauses the current instruction and jumps to a handler

**Afternoon — Build (2 hours)**

Extend your MemoryModel to simulate the fetch-decode-execute cycle:
- Add a simple instruction set: MOV, ADD, PUSH, POP, CALL, RET, BEQ
- A run() method that fetches from flash, decodes, executes, and increments PC
- A trace mode that prints each instruction as it executes — this is what a debugger shows

**Evening — Document (30 minutes)**

Write day-04.md. Answer: when an interrupt fires during execution of an ADD
instruction, what happens to the PC, SP, and LR registers in exact order?

---

### Day 5 — Communication Protocols: How Chips Talk

**Morning — Study (2 hours)**

Topics:
- Why chips need communication protocols — they have limited pins, data must be serialized
- UART — the simplest: two wires (TX and RX), no clock, both sides agree on speed (baud rate)
- SPI — four wires (MOSI, MISO, SCK, CS), has a clock, very fast, one master many slaves
- I2C — two wires (SDA, SCL), has a clock, each device has a 7-bit address
- USB — what your STM32 Nucleo uses to connect to your laptop for serial communication

Subtopics:
- UART framing: start bit (always 0), 8 data bits, stop bit (always 1)
- Baud rate — bits per second, both sides must match exactly or data is corrupted
- Why baud rate mismatch produces garbled output — the timing is off by exactly the ratio
- I2C clock stretching — a slave can hold the clock low to slow the master
- Why your EmbeddedAI observer uses UART to stream events to the Python layer

**Afternoon — Build (2 hours)**

Python script that simulates UART framing:
- A function uart_frame(byte, baud_rate) that returns the complete bit sequence with timing
- A function uart_decode(bit_sequence, baud_rate) that recovers the original byte
- A simulation showing what happens when decoder baud rate is 10% wrong

**Evening — Document (30 minutes)**

Write day-05.md. Draw the UART frame for transmitting the letter 'A' (ASCII 65 = 
01000001 binary) at 115200 baud. Calculate the bit duration in microseconds.

---

### Day 6 — DMA: The Hardware That Moves Data Without the CPU

**Morning — Study (2 hours)**

Topics:
- What DMA (Direct Memory Access) is — dedicated hardware that copies data independently
- Why DMA exists — the CPU is too valuable to spend cycles waiting for slow peripherals
- Three DMA modes: memory-to-memory, peripheral-to-memory, memory-to-peripheral
- DMA transfer complete interrupt — the hardware tells your CPU when the copy is done
- Circular DMA — automatically restarts when it reaches the end, for continuous streaming

Subtopics:
- Why DMA causes subtle bugs — the CPU and DMA can disagree about memory contents
- Cache coherency — the CPU's cache may have a stale copy of memory DMA just wrote
- What a DMA stream and channel are on STM32
- Why your EmbeddedAI firmware observer uses DMA to log events without affecting timing

**Afternoon — Build (2 hours)**

Python simulation of a DMA controller:
- A class DMAController with configure(source, destination, length, circular) method
- A transfer() method that copies data and calls a completion callback
- A simulation showing: CPU fills a buffer, DMA transfers it to output, CPU continues work
  during the transfer — proving DMA enables true concurrency

**Evening — Document (30 minutes)**

Write day-06.md. Write: why would using CPU-polled UART transmission in your observer
task affect the firmware being observed, and why does DMA solve this problem?

---

### Day 7 — Week 1 Review and Mini-Project 0

**Morning — Review (2 hours)**

Re-read journal entries from Days 1 to 6. Correct any explanations you now know
are incomplete. Update your README.md with a Week 1 summary.

**Afternoon and Evening — Mini-Project 0: The Hardware Simulator (4 hours)**

Build a Python program that simulates a minimal embedded system:

What it must do:
- A MemoryModel class: flash (read-only), sram (read-write), registers
- A CPU class with fetch-decode-execute cycle, PC, SP, LR registers
- A UART class that serializes bytes with correct framing at configurable baud rate
- A DMA class that transfers memory blocks with a completion callback
- A simulation of the STM32 startup sequence:
  1. CPU reads reset vector from flash at 0x00000004
  2. Sets SP from flash at 0x00000000
  3. Calls SystemInit() (simulated)
  4. Calls main() (your simulated program)
- Your simulated program blinks an LED (toggles a GPIO register) and sends "Hello"
  over the simulated UART using DMA

Why this matters for EmbeddedAI: You just simulated the startup of the exact hardware
your observer will run on. Understanding this sequence is why you will know what to
check when the GDB bridge fails to attach to a real device.

Real-world problem: Firmware developers often do not understand the startup sequence,
causing bugs that only appear at boot. This simulation makes the sequence explicit.

Document in GitHub: `projects/mini-project-00-hardware-simulator/` with source,
README explaining what each component simulates and why, and a Hashnode draft.

Commit: `feat: mini-project-00 hardware simulator — CPU, memory, UART, DMA`

---

## WEEK 2 — C Programming: The Language of Hardware
### Days 8 to 14

---

### Day 8 — Why C and the Compilation Pipeline

**Morning — Study (2 hours)**

Topics:
- What a compiled language is versus an interpreted language
- Why Python cannot run on a bare-metal microcontroller — it needs an interpreter which
  needs an OS which needs a CPU with memory management which a microcontroller does not have
- The C compilation pipeline in four stages:
  1. Preprocessor — handles #include and #define directives
  2. Compiler — translates C to assembly language
  3. Assembler — translates assembly to machine code (object files .o)
  4. Linker — combines object files into one binary (.elf) placed at exact memory addresses
- What a linker script is — tells the linker exactly where to place code in memory

Subtopics:
- Why firmware must be placed at 0x08000000 — that is where the STM32 boots from
- What .c, .h, .o, .elf, and .bin files are
- The startup file — C code that runs before main() to initialize the stack and BSS
- Cross-compilation — compiling on your x86 laptop to produce ARM machine code

Study resource: CS50 Week 1 at cs50.harvard.edu — free, the best C introduction.
Install gcc on your system: `sudo apt install gcc` (Linux) or use WSL on Windows.

**Afternoon — Build (2 hours)**

Write, compile, and run your first C programs:
- Hello World: understand every line including #include
- A program that prints the size of every C type: sizeof(char), sizeof(int), etc.
- A program that prints its own stack address and heap address to show they are different

**Evening — Document (30 minutes)**

Write day-08.md. Draw the four-stage compilation pipeline with a file at each stage.
Write: why must an embedded binary be placed at exactly 0x08000000 and what happens
if you get this wrong?

---

### Day 9 — Types, Variables, and Fixed-Width Integers

**Morning — Study (2 hours)**

Topics:
- C primitive types and their sizes: char (1 byte), short (2 bytes), int (usually 4 bytes),
  long (platform-dependent), float (4 bytes), double (8 bytes)
- Why platform-dependent sizes cause bugs in embedded code
- Fixed-width types from stdint.h: uint8_t, uint16_t, uint32_t, int8_t, int16_t, int32_t
- Why every professional embedded codebase uses uint32_t instead of unsigned int

Subtopics:
- Signed versus unsigned: uint8_t holds 0-255, int8_t holds -128 to 127
- Overflow and wraparound: adding 1 to a uint8_t holding 255 gives 0, not an error
- The volatile keyword: tells the compiler this variable can change without the program
  changing it — every hardware register must be declared volatile
- Why forgetting volatile on a hardware register causes the compiler to optimize away
  your reads, creating bugs that only appear in release builds

**Afternoon — Build (2 hours)**

C programs demonstrating type behavior:
- Print sizes of all types using sizeof
- Demonstrate overflow: uint8_t counter that counts to 255 then wraps to 0
- Demonstrate volatile: write a loop reading a volatile versus non-volatile variable,
  look at the assembly output with gcc -S to see the compiler optimizes away the
  non-volatile read but not the volatile read

**Evening — Document (30 minutes)**

Write day-09.md. Write: what is the exact hardware reason that every STM32 peripheral
register must be accessed through a volatile pointer? What bug does forgetting volatile
cause?

---

### Day 10 — Pointers: The Foundation of Hardware Programming

**Warning: This is Complexity Spike 1. Plan for 2 weeks of confusion here.
The solution is drawing memory diagrams by hand, not reading more theory.**

**Morning — Study (2 hours)**

Topics:
- What a pointer is: a variable that holds a memory ADDRESS instead of a value
- Declaration: `int *p` — p is a variable that holds the address of an integer
- Address-of operator: `&x` — gives you the memory address where x is stored
- Dereference operator: `*p` — gives you the value stored at the address p holds
- The NULL pointer: a pointer holding address zero — dereferencing it crashes the program

Subtopics:
- Pointer arithmetic: adding 1 to an int* moves it 4 bytes forward, not 1 byte
- Why this makes sense: a pointer to int always points to a complete integer
- The relationship between arrays and pointers: array name is pointer to first element
- array[i] and *(array + i) are identical — this is how array indexing works internally

**Afternoon — Build (3 hours — this needs more time)**

C programs that make pointers concrete:
- Declare an integer x = 42. Print the value, the address, and the value via a pointer.
  Draw the memory diagram for this on paper.
- Write a function swap(int *a, int *b) that swaps two integers. Call it and verify.
- Write a function that mimics reading a hardware register:
  `volatile uint32_t *RCC_AHB1ENR = (volatile uint32_t*)0x40023830;`
  Explain every part of this line in your journal.
- Demonstrate a NULL dereference crash and explain why it crashes.

**Evening — Document (45 minutes)**

Write day-10.md. This entry should be your longest so far. Draw:
1. A variable x at address 0x20000010 holding value 42
2. A pointer p at address 0x20000014 holding value 0x20000010
3. What *p evaluates to and why
4. The line `*(volatile uint32_t*)0x40023830 = 0x01` explained at every level:
   cast to pointer type → volatile → dereference → assign value

---

### Day 11 — Pointers: Arrays, Strings, and Structs

**Morning — Study (2 hours)**

Topics:
- Arrays in C: contiguous memory, the array name is a pointer to the first element
- Strings in C: arrays of char terminated by null byte '\0'
- Structs: grouping related variables into one named type
- How structs map to memory: members are laid out sequentially with padding for alignment
- Bit fields: packing multiple values into a single register-width struct

Subtopics:
- Struct padding: a struct with a char followed by an int has 3 bytes of padding
- Packed structs: `__attribute__((packed))` removes padding for exact memory layout
- Unions: all members share the same memory address — useful for type punning
- Why firmware uses structs to represent hardware register blocks — this is the entire
  basis of the STM32 HAL library

**Afternoon — Build (2 hours)**

C programs demonstrating structs and arrays:
- Define a struct UartConfig with fields: baud_rate (uint32_t), data_bits (uint8_t),
  stop_bits (uint8_t), parity (uint8_t) — with a bit field version also
- Print the sizeof each struct and explain the padding
- Write an array of UartConfig and iterate it with a pointer
- Write a function that takes a pointer to UartConfig and configures a simulated UART

**Evening — Document (30 minutes)**

Write day-11.md. Write the definition of the STM32 GPIO_TypeDef struct from the
STM32 HAL library (you can find it in the stm32f4xx.h header online). Explain why
this struct is placed at the exact memory address of the GPIO peripheral registers.

---

### Day 12 — Functions, the Call Stack, and Function Pointers

**Morning — Study (2 hours)**

Topics:
- Function declaration versus definition versus call — three separate concepts
- What happens on the stack when a function is called:
  1. Push return address onto stack
  2. Push function arguments onto stack (or pass in registers on ARM)
  3. Jump to function code
  4. Function executes with local variables on the stack
  5. Pop local variables, jump to return address
- Stack frames: the portion of the stack belonging to one function call
- Function pointers: storing a function's address in a variable, calling through it

Subtopics:
- Why deep recursion overflows the stack on a 192KB SRAM microcontroller
- How GDB's backtrace command works — it reads return addresses from the stack
- The ARM calling convention: first four arguments go in registers R0-R3
- Function pointers as callbacks: `void (*callback)(uint8_t)` — used for interrupt
  service routines and FreeRTOS task functions

**Afternoon — Build (2 hours)**

C programs demonstrating the call stack:
- A recursive factorial that prints the stack depth at each level
- A demonstration of stack overflow — a function that allocates a huge array locally
- An array of function pointers to different event handlers, called by index
  (this is exactly how the ARM interrupt vector table works)

**Evening — Document (30 minutes)**

Write day-12.md. Draw a stack diagram showing three nested function calls. Label
each stack frame with local variables and return address. Write: what does GDB show
you when you type "backtrace" and why is finding the crash point equivalent to
reading return addresses off the stack?

---

### Day 13 — Memory Management, malloc, and Why Embedded Avoids It

**Morning — Study (2 hours)**

Topics:
- malloc: requests a block from the heap, returns a pointer, returns NULL if no memory
- free: returns a block to the heap, must be called with the exact pointer malloc returned
- Memory leaks: calling malloc without free — heap grows until it collides with the stack
- Why memory leaks are catastrophic in long-running embedded systems
- Why embedded firmware typically avoids dynamic allocation entirely
- Static allocation: all memory decided at compile time, no surprises at runtime

Subtopics:
- Heap fragmentation: many small allocations and frees leave unusable gaps
- Double free: calling free twice on the same pointer — undefined behavior, often a crash
- Use after free: accessing memory after calling free — reads garbage, writes corrupt heap
- FreeRTOS heap implementations: heap_1 through heap_5, each with different tradeoffs
- Why your EmbeddedAI observer uses only static allocation — no malloc in observer code

**Afternoon — Build (2 hours)**

Write a simple memory allocator from scratch in C:
- A global array of 1024 bytes as the heap
- A header struct before each allocation recording the size and whether it is free
- malloc(size): searches the array for a free block of sufficient size, marks it used
- free(ptr): marks the block before ptr as free
- A test that allocates several blocks, frees some, and reallocates to verify it works

This single exercise teaches more about memory than any number of tutorials.

**Evening — Document (30 minutes)**

Write day-13.md. Explain: why does a firmware that runs for 30 days accumulate
memory leaks that eventually crash the device? Why is this impossible to reproduce
in a 1-hour test? Why does your EmbeddedAI memory system specifically track and
alert on allocation patterns?

---

### Day 14 — Week 2 Review and Project 1

**Morning — Review (2 hours)**

Re-read journal Days 8 to 13. Update the architecture/decisions/ folder with an ADR
(Architecture Decision Record) explaining why C is used for the firmware layer instead
of Rust (which you will learn later) or Assembly.

**Afternoon and Evening — Project 1: Firmware Crash Simulator and Analyzer (4 hours)**

Build a C program that simulates and analyzes three common firmware crash types:

What it must do:
- Simulate stack overflow: a recursive function that grows past a fixed stack limit
- Simulate null pointer dereference: write a function that dereferences a NULL pointer
  and catches it with signal handling (SIGSEGV on Linux)
- Simulate memory corruption: deliberately write past the end of an array and detect
  the corruption using a canary value (a known value placed at the boundary)
- For each crash, generate a structured crash report as JSON:
  ```json
  {
    "crash_type": "STACK_OVERFLOW",
    "timestamp": 1234567890,
    "function": "recursive_fill",
    "call_depth": 47,
    "stack_address": "0x20001F00",
    "description": "Stack pointer exceeded limit at depth 47"
  }
  ```
- Write a Python script that reads the JSON crash reports and produces a summary:
  crash frequency by type, most common crash location, severity ranking

Why this matters for EmbeddedAI: This is the first version of your crash observer.
The JSON format you define here is the format your memory store will use for the
next 5 months of development. The Python analyzer is the first version of your
reasoning layer.

Real-world problem solved: Firmware developers spend hours manually analyzing crash
logs with no structure. This project creates structured, machine-readable crash data
from the start.

Document in GitHub: `projects/project-01-crash-simulator/` with:
- C source with detailed comments explaining each crash mechanism
- Python analyzer script
- Three sample JSON crash reports
- README explaining each crash type, why it occurs in real firmware, and how your
  EmbeddedAI system will eventually detect it before it happens
- Draft Hashnode post: "The Three Most Common Firmware Crashes and How to Detect Them"

Commit: `feat: project-01 firmware crash simulator with JSON reporting`

---

## WEEK 3 — Python for AI Systems
### Days 15 to 21

---

### Day 15 — Python Fundamentals and Environment Setup

**Morning — Study (2 hours)**

Topics:
- Python vs C: interpreted, dynamically typed, garbage collected
- Why Python is used for the AI layer: the library ecosystem is unmatched
- Setting up Python properly: pyenv for version management, venv for virtual environments
- pip: Python's package manager
- Python syntax: variables, print, comments, input, basic types

Subtopics:
- Why virtual environments are mandatory in professional Python development
- requirements.txt and how to freeze/install dependencies
- f-strings: the modern Python string formatting
- The REPL: using Python interactively for exploration
- Running your crash report reader as your first real Python program

Study resource: Python.org official tutorial Chapters 1-4 — free.

**Afternoon — Build (2 hours)**

- Set up Python environment with pyenv and venv
- Write a Python script that reads your Project 1 JSON crash reports and pretty-prints
  them with analysis: which crash type appeared most, which was most severe
- Connect Day 14 directly to Day 15 — your Python reads your C output

**Evening — Document (30 minutes)**

Write day-15.md. Write: why does the EmbeddedAI architecture use Python for the
AI layer and C/Rust for the firmware layer instead of using one language for everything?

---

### Day 16 — Control Flow, Functions, and Error Handling

**Morning — Study (2 hours)**

Topics:
- if/elif/else, for loops, while loops, break, continue
- Functions: def, parameters, default arguments, return values, docstrings
- Exception handling: try/except/except SpecificError/finally/raise
- Modules: importing from the standard library (json, os, datetime, pathlib)
- The if __name__ == "__main__" pattern and why every professional Python file uses it

Subtopics:
- List comprehensions — the Pythonic alternative to for loops that build lists
- Dictionary comprehensions — building dicts in one line
- The *args and **kwargs patterns for flexible function signatures
- Why docstrings matter: your AI system reads function docstrings to understand intent

**Afternoon — Build (2 hours)**

Refactor your crash report reader into a proper module:
- Function read_crash_report(filepath: str) -> dict with docstring
- Function analyze_crashes(reports: list[dict]) -> dict that returns statistics
- Function format_report(analysis: dict) -> str that formats for human reading
- Exception handling for: file not found, invalid JSON, missing required fields
- if __name__ == "__main__": block that runs the full pipeline

**Evening — Document (30 minutes)**

Write day-16.md. Write a docstring for each function you wrote today. Explain:
why does the EmbeddedAI reasoning layer need clean, well-documented Python functions
rather than one large script?

---

### Day 17 — Data Structures: Building the Bug Memory Model

**Morning — Study (2 hours)**

Topics:
- Lists: ordered mutable sequences — used for collections of events
- Dictionaries: key-value stores — every bug event in your system is a dict
- Sets: unique collections — used for deduplication of similar events
- Dataclasses: the modern Python way to define structured data with type hints

Subtopics:
- When to use list vs dict vs set vs dataclass — the decision rules
- JSON serialization: json.dumps() and json.loads()
- Nested data structures: a dict of lists of dicts — common in bug databases
- The dataclass decorator: @dataclass, field(), __post_init__ for validation
- Type hints: List[str], Dict[str, Any], Optional[str] — used in production code

**Afternoon — Build (2 hours)**

Define the core data models for EmbeddedAI:

```python
@dataclass
class FirmwareCrashEvent:
    event_id: str
    timestamp: datetime
    crash_type: str          # STACK_OVERFLOW, NULL_DEREF, MEMORY_CORRUPT, HARD_FAULT
    severity: str            # CRITICAL, HIGH, MEDIUM, LOW
    function_name: str
    memory_address: str      # hex string: "0x20001F00"
    call_stack: List[str]    # list of function names
    register_state: Dict[str, str]  # register name to hex value
    raw_log: str
    resolved: bool = False
    fix_applied: Optional[str] = None
```

Write functions to:
- Create a FirmwareCrashEvent from a raw JSON string
- Serialize a FirmwareCrashEvent back to JSON
- Validate that required fields are present and correctly typed

**Evening — Document (30 minutes)**

Write day-17.md. Explain: why does the FirmwareCrashEvent include register_state
as a dictionary? Write: how will the LLM use the register_state field to diagnose
the crash in ways that a simple log message cannot?

---

### Day 18 — Databases: SQLite to PostgreSQL

**Morning — Study (2 hours)**

Topics:
- SQLite: a file-based relational database, zero configuration, standard library
- The sqlite3 module: creating connections, cursors, executing SQL
- Basic SQL: CREATE TABLE, INSERT INTO, SELECT FROM, WHERE, ORDER BY, LIMIT
- Why SQLite for development and PostgreSQL for production
- Database schema design for crash events

Subtopics:
- Primary keys, foreign keys, indexes
- Parameterized queries: why you NEVER format SQL strings with Python string formatting
- Transactions: BEGIN, COMMIT, ROLLBACK — ensuring data consistency
- The context manager pattern with sqlite3: `with conn:` auto-commits or rolls back

**Afternoon — Build (2 hours)**

Build your first real database layer:
- Schema:
  ```sql
  CREATE TABLE crash_events (
      id TEXT PRIMARY KEY,
      timestamp TEXT NOT NULL,
      crash_type TEXT NOT NULL,
      severity TEXT NOT NULL,
      function_name TEXT NOT NULL,
      memory_address TEXT,
      call_stack TEXT,        -- JSON string
      register_state TEXT,    -- JSON string
      raw_log TEXT,
      resolved INTEGER DEFAULT 0,
      fix_applied TEXT,
      created_at TEXT DEFAULT CURRENT_TIMESTAMP
  );
  CREATE INDEX idx_crash_type ON crash_events(crash_type);
  CREATE INDEX idx_severity ON crash_events(severity);
  ```
- Functions: insert_event(event: FirmwareCrashEvent), get_events_by_type(crash_type),
  get_unresolved_events(), mark_resolved(event_id, fix_description)

**Evening — Document (30 minutes)**

Write day-18.md. Write: why does the call_stack field store JSON instead of having
a separate table? When would you change this design? What does the index on crash_type
do for query performance?

---

### Day 19 — Async Python for Simultaneous Hardware and AI Operations

**Morning — Study (2 hours)**

Topics:
- Why your observer needs to receive hardware events and call the LLM simultaneously
- Blocking vs non-blocking operations: a blocking read() stops everything else
- asyncio: Python's built-in async framework based on an event loop
- async def: defining a coroutine — a function that can pause and resume
- await: pausing a coroutine until an async operation completes
- asyncio.gather: running multiple coroutines simultaneously

Subtopics:
- The event loop: the single thread that switches between coroutines
- asyncio.Queue: thread-safe data passing between coroutines without race conditions
- Why async is different from threading: no true parallelism, but no blocking either
- When to use async vs threading vs multiprocessing
- asyncio.sleep(0): yielding to the event loop without waiting

**Afternoon — Build (2 hours)**

Build an async event pipeline:
- Coroutine hardware_event_source(): simulates receiving events from firmware every 0.5s
- Coroutine event_processor(queue): reads from queue, stores in database
- Coroutine anomaly_detector(queue): reads from same queue, flags critical events
- asyncio.Queue connecting source to both consumers
- Main function using asyncio.gather to run all three simultaneously

**Evening — Document (30 minutes)**

Write day-19.md. Draw a diagram showing the event loop switching between your three
coroutines. Write: if the LLM API call takes 3 seconds, why does asyncio prevent
this from blocking new hardware events from being received?

---

### Day 20 — FastAPI: The Production API Layer

**Morning — Study (2 hours)**

Topics:
- What a REST API is and why services communicate via HTTP
- FastAPI: the fastest Python web framework, used by Netflix, Uber, and Microsoft
- Pydantic: data validation library integrated into FastAPI
- Path parameters, query parameters, and request bodies
- Automatic API documentation at /docs

Subtopics:
- HTTP methods: GET (read), POST (create), PUT (update), DELETE (remove)
- Status codes: 200, 201, 400, 422, 500 — what each means
- Dependency injection in FastAPI: reusing database connections across endpoints
- Background tasks: running work after returning a response
- CORS: why your React dashboard needs it configured

Study resource: FastAPI tutorial at fastapi.tiangolo.com — the best web framework
documentation in Python. Complete Sections 1-8 (takes about 3 hours total).

**Afternoon — Build (2 hours)**

Build your first production FastAPI service:
```python
POST /api/v1/events        # Receive a FirmwareCrashEvent, store in database
GET  /api/v1/events        # List events with filtering: ?crash_type=STACK_OVERFLOW
GET  /api/v1/events/{id}   # Get specific event
PUT  /api/v1/events/{id}/resolve  # Mark event as resolved with fix description
GET  /api/v1/stats         # Return crash counts by type and severity
```

With full Pydantic validation, proper error responses, and auto-generated /docs.

**Evening — Document (30 minutes)**

Write day-20.md. Open your /docs page, take a screenshot, and embed it in your
journal. Write: why does the EmbeddedAI architecture use a REST API between the
firmware observer and the AI reasoning layer instead of writing to the database
directly?

---

### Day 21 — Week 3 Review and Project 2

**Morning — Review (2 hours)**

Review Days 15-20. Write an ADR in architecture/decisions/ explaining why Python
was chosen for the AI/ingestion layers.

**Afternoon and Evening — Project 2: Production Firmware Event Ingestion API (4 hours)**

Build a complete, production-quality FastAPI service:

Requirements:
- All endpoints from Day 20 with full Pydantic validation
- SQLite for development storage with proper schema and indexes
- Structured JSON logging with log level, timestamp, correlation ID per request
- Health check endpoint: GET /health that returns service status
- A background task that runs every 60 seconds, checks for unresolved CRITICAL events
  older than 5 minutes, and logs an alert
- Environment variable configuration using python-dotenv
- A Makefile with commands: make run, make test, make lint, make format
- README with architecture diagram, API documentation, and setup instructions

Why this project matters: This is your Ingestion Layer endpoint in production.
Your firmware observer POSTs to exactly this API. The background alerting task
is the first version of your anomaly detection.

Real-world problem: Embedded teams have no centralized, queryable crash data from
deployed devices. This API provides that. It is deployable today.

Commit: `feat: project-02 production firmware event ingestion API`
Hashnode post: "Building a Production Crash Analytics API for Embedded Systems"

---

## WEEK 4 — Professional Engineering Practices
### Days 22 to 28

---

### Day 22 — Git: Professional Version Control

**Morning — Study (2 hours)**

Topics:
- What git actually is: a content-addressed storage system tracking file snapshots
- The three areas: working directory, staging area (index), repository
- Core workflow: git add, git commit, git push, git pull, git status, git log
- Branching: creating parallel lines of development
- Merging: combining branches — fast-forward vs three-way merge

Subtopics:
- What is inside the .git folder: objects (blobs, trees, commits), refs, HEAD
- git diff: understanding what changed between any two points
- git log --graph: visualizing branch history
- Conventional commits: feat:, fix:, docs:, test:, refactor: — used at every MNC
- git hooks: scripts that run automatically on events — used by Graphify for auto-sync

**Afternoon — Build (2 hours)**

- Initialize your embeddedai-journey repository properly if not already done
- Create a .gitignore appropriate for Python and C projects
- Write a CONTRIBUTING.md explaining how to make commits to your project
- Create 10 commits with proper conventional commit messages across your projects
- Create a feature branch, make changes, and merge it back with a merge commit

**Evening — Document (30 minutes)**

Write day-22.md. Explain: why does EmbeddedAI use git as the backing store for the
AI's memory? What advantage does git-backed memory have over a plain database?

---

### Day 23 — Docker: Every Service in a Container

**Morning — Study (2 hours)**

Topics:
- What a container is: an isolated process with its own filesystem, not a virtual machine
- Why Docker: eliminates environment differences between development, testing, production
- Dockerfile: instructions to build a container image layer by layer
- docker-compose: defining and running multi-container applications
- Volumes: persisting data outside the container lifecycle

Subtopics:
- The difference between an image (blueprint) and a container (running instance)
- Layer caching: why the order of Dockerfile instructions affects build speed
- Multi-stage builds: using a build container to compile, then a small runtime container
- Networks: how containers discover and connect to each other by service name
- Why every service in EmbeddedAI production runs in Docker

**Afternoon — Build (2 hours)**

- Write a production Dockerfile for your FastAPI service:
  - Multi-stage: builder stage installs dependencies, runtime stage copies only what is needed
  - Non-root user for security
  - Health check instruction
- Write a docker-compose.yml:
  - fastapi service (your app)
  - postgres service (PostgreSQL with pgvector)
  - adminer service (web UI for database inspection)
- Run the complete stack with `docker compose up`

**Evening — Document (30 minutes)**

Write day-23.md. Write: why does EmbeddedAI use separate Docker containers for
PostgreSQL and FastAPI instead of running both in one container? What happens if
you need to scale only the FastAPI service?

---

### Day 24 — PostgreSQL and pgvector: Production Database

**Morning — Study (2 hours)**

Topics:
- PostgreSQL versus SQLite: concurrent users, ACID compliance, extensions, performance
- psycopg2 and asyncpg: Python clients for PostgreSQL
- pgvector: adds a vector column type and similarity search operators to PostgreSQL
- The `<=>` operator: cosine distance between vectors in SQL
- HNSW index: approximate nearest neighbor search at production scale

Subtopics:
- Database migrations with Alembic: versioning your schema changes
- Connection pooling: why you cannot create a new database connection per request
- The asyncpg library: async PostgreSQL client for FastAPI
- EXPLAIN ANALYZE: understanding how PostgreSQL executes your queries
- Why pgvector beats Pinecone for your use case: free, self-hosted, ACID compliant

**Afternoon — Build (2 hours)**

Migrate your application from SQLite to PostgreSQL:
- Install pgvector extension in your Docker PostgreSQL
- Update schema to add a vector column: `embedding vector(384)` for future use
- Add a composite index on (crash_type, severity) for filtered queries
- Write an Alembic migration for the schema change
- Update your FastAPI service to use asyncpg with connection pooling

**Evening — Document (30 minutes)**

Write day-24.md. Write an ADR: "Why pgvector over Pinecone for vector storage."
Include cost comparison, data sovereignty argument, and operational simplicity.

---

### Day 25 — Testing: The Proof That Your System Works

**Morning — Study (2 hours)**

Topics:
- Why tests are not optional in production code: they are the proof your system works
- pytest: the standard Python testing framework, simpler and more powerful than unittest
- The three test levels: unit (one function), integration (service + database), end-to-end
- Test fixtures: shared setup that runs before each test
- Mocking: replacing external dependencies with controlled fakes

Subtopics:
- Parametrize decorator: running the same test with dozens of different inputs
- Coverage: pytest-cov shows what percentage of your code executes during tests
- The AAA pattern: Arrange (set up), Act (call), Assert (verify)
- TestClient in FastAPI: calling your API endpoints in tests without running a server
- Why 80% coverage is the professional minimum — not 100%, not 50%

**Afternoon — Build (2 hours)**

Write a comprehensive test suite for your ingestion API:
- 5 unit tests: test FirmwareCrashEvent creation, validation, serialization
- 5 integration tests: test each API endpoint with a real test database
- 3 error case tests: invalid JSON, missing required fields, unknown crash type
- 2 edge case tests: empty call stack, extremely long function name
- Achieve 80%+ coverage, verified with pytest-cov

**Evening — Document (30 minutes)**

Write day-25.md. Write: why does a firmware team need automated tests for their
crash analytics API? What would happen without them when a developer changes the
FirmwareCrashEvent schema?

---

### Day 26 — Observability: Knowing What Your System Is Doing

**Morning — Study (2 hours)**

Topics:
- The three pillars of observability: logs, metrics, traces
- Python logging module: levels, handlers, formatters
- Structured logging: JSON-formatted logs that can be queried programmatically
- Prometheus: a time-series metrics database, scrapes /metrics endpoints
- Grafana: a visualization tool that queries Prometheus and displays dashboards

Subtopics:
- OpenTelemetry: the industry standard API for all three observability pillars
- Correlation IDs: a unique ID per request that links all log lines from that request
- The opentelemetry-sdk package: instrumenting your FastAPI service
- Why observability matters: understanding production behavior without adding print statements
- How firmware events formatted as OpenTelemetry spans integrate with enterprise tooling

Study resource: OpenTelemetry Python documentation at opentelemetry.io/docs/languages/python

**Afternoon — Build (2 hours)**

Add complete observability to your FastAPI service:
- JSON structured logging with request_id, service_name, timestamp on every log line
- Prometheus metrics: request count, request latency histogram, database query latency
- OpenTelemetry trace for every API request with spans for database calls
- Docker Compose additions: prometheus, grafana containers
- Grafana dashboard showing: request rate, error rate, p50/p95/p99 latency

**Evening — Document (30 minutes)**

Write day-26.md with screenshots of your Grafana dashboard. Write: when a firmware
developer reports "the crash analytics API seems slow," what would you look at first
in Grafana and why?

---

### Day 27 — GitHub Actions: Automated Testing on Every Commit

**Morning — Study (2 hours)**

Topics:
- What CI/CD is: automated testing and deployment triggered by git events
- GitHub Actions: free CI/CD built into every GitHub repository
- Workflow files: .github/workflows/*.yml — YAML files defining pipelines
- Jobs and steps: a workflow has jobs, each job has steps
- Secrets: storing API keys in GitHub without committing them to code

Subtopics:
- Matrix strategy: run tests on Python 3.11 and 3.12 simultaneously
- Docker in GitHub Actions: building and testing your container in CI
- Code quality gates: black (formatting), isort (import sorting), mypy (type checking)
- Publishing to GitHub Container Registry on every release tag

**Afternoon — Build (2 hours)**

Write three GitHub Actions workflows:
1. ci.yml: runs on every push — pytest, black check, isort check, mypy
2. docker.yml: runs on every push to main — builds Docker image, pushes to GHCR
3. security.yml: runs weekly — bandit security scanner, safety dependency check

Make sure all three pass on your repository.

**Evening — Document (30 minutes)**

Write day-27.md. Write: why does every MNC require CI/CD pipelines before any code
reaches production? What would happen to EmbeddedAI if a developer pushed a change
that broke the ingestion API without any automated tests catching it?

---

### Day 28 — Week 4 Review and Project 3

**Afternoon and Evening — Project 3: Production Crash Analytics Platform (5 hours)**

Build the definitive version of your ingestion service:

All previous requirements plus:
- PostgreSQL with pgvector and proper Alembic migrations
- Docker Compose with PostgreSQL, FastAPI, Prometheus, Grafana
- OpenTelemetry distributed tracing
- GitHub Actions CI with all quality gates
- pytest suite with 80%+ coverage
- Rate limiting: maximum 100 requests per minute per IP
- Pagination: GET /events returns pages of 50 results
- A simple HTML dashboard at /dashboard (no React yet) showing crash statistics
- Makefile: make dev, make test, make lint, make build, make push

This project is MNC-standard quality. A senior engineer at Bosch could review this
and find nothing unprofessional.

Real-world problem: Any firmware team can deploy this to receive crash data from
devices in the field, query it, and track resolution progress.

Commit: `feat: project-03 production crash analytics platform v1`
Hashnode: "I Built a Production Crash Analytics Platform for Embedded Systems —
Here Is Every Decision I Made"

---

## WEEK 5 — Electronics and STM32 Foundations
### Days 29 to 35

---

### Day 29 — Electronics Fundamentals

**Morning — Study (2 hours)**

Topics:
- Voltage (V): electrical pressure, measured in volts
- Current (I): flow of electrons, measured in amperes
- Resistance (R): opposition to current flow, measured in ohms
- Ohm's Law: V = I × R — the most fundamental equation in electronics
- Power: P = V × I — watts, how much energy per second

Subtopics:
- GPIO: General Purpose Input/Output — the most basic hardware interface
- Logic levels: 3.3V high and 0V low for STM32, why 5V kills it
- Pull-up resistors: connecting a pin to VCC through a resistor so it reads HIGH by default
- Pull-down resistors: connecting a pin to GND through a resistor so it reads LOW by default
- Why floating inputs (connected to nothing) read random values — antenna effect

**Afternoon — Build (2 hours)**

Using Wokwi (free, browser-based STM32 simulator at wokwi.com):
- Create a new STM32F4 project
- Add an LED and calculate the correct resistor value using Ohm's Law
- Add a button with a pull-up resistor
- Note every component on screen — you will use this project all week

**Evening — Document (30 minutes)**

Write day-29.md. Calculate: if your LED has a forward voltage of 2.0V and you want
10mA through it, and your GPIO outputs 3.3V, what resistor value do you need?
Show the Ohm's Law calculation.

---

### Day 30 — STM32 Architecture and Memory Map

**Morning — Study (2 hours)**

Topics:
- What a microcontroller is: CPU core + Flash + SRAM + peripherals on one chip
- STM32F4 specifically: ARM Cortex-M4 core, 1MB Flash, 192KB SRAM, 168MHz max
- The STM32 memory map: the 4GB address space and what lives where
- AHB and APB buses: the on-chip highways connecting CPU to peripherals
- The clock system: why every peripheral must have its clock enabled before use

Subtopics:
- Flash at 0x08000000 — your compiled firmware lives here
- SRAM at 0x20000000 — your variables and stack live here
- Peripherals at 0x40000000 — hardware registers live here
- The RCC peripheral (Reset and Clock Control) at 0x40023800 — must configure first
- Why the memory map is important: every register address in your SVD parser refers to it

Study resource: Download the STM32F4 Reference Manual RM0090 from st.com. Free.
Bookmark it — you will use it for the rest of this roadmap.

**Afternoon — Build (2 hours)**

Python script that generates a complete STM32F4 memory map visualization:
- Reads a simplified JSON description of the STM32F4 memory regions
- Outputs an ASCII art memory map with addresses and labels
- Marks which regions your crash events will reference (SRAM addresses in stack traces)

**Evening — Document (30 minutes)**

Write day-30.md with your memory map diagram. Write: when your hard fault handler
captures a stack address of 0x2001FF00, what does that tell you about where in SRAM
the crash occurred and how close the stack was to its limit?

---

### Day 31 — Setting Up STM32 Development Environment

**Morning — Setup (3 hours)**

Install and verify:
1. STM32CubeIDE from st.com — free official IDE
2. arm-none-eabi-gcc: `sudo apt install gcc-arm-none-eabi` (Linux/WSL)
3. OpenOCD: `sudo apt install openocd`
4. Wokwi VS Code extension (if using VS Code)
5. Wokwi CLI: `npm install -g @wokwi/cli`
6. Renode from renode.io — free professional simulator

**Afternoon — Build (2 hours)**

First firmware project in Wokwi:
- Create STM32F4 project with STM32CubeIDE
- LED blink: toggle PA5 every 500ms using HAL_GPIO_TogglePin and HAL_Delay
- Then rewrite it without HAL: toggle PA5 by writing directly to GPIOA_ODR at 0x40020014
- Run both versions in Wokwi and verify identical behavior

**Evening — Document (30 minutes)**

Write day-31.md. Document every installation step with the exact commands you ran.
This becomes the setup guide in your project README and proves you went through the
process yourself.

---

### Day 32 — Reading Datasheets and Register Configuration

**Morning — Study (2 hours)**

Topics:
- What a datasheet is versus a reference manual
- How to navigate RM0090: contents page, register map table, peripheral chapter
- Register description tables: bit numbers, field names, access type (R, W, RW), reset value
- How to configure a GPIO pin in output mode by writing to its registers directly

Subtopics:
- GPIOA_MODER at 0x40020000: mode register, 2 bits per pin
- GPIOA_ODR at 0x40020014: output data register, 1 bit per pin
- RCC_AHB1ENR at 0x40023830: must set bit 0 to enable GPIOA clock before using it
- Read-modify-write: why you use |= and &= instead of = when changing register bits

**Afternoon — Build (2 hours)**

Write firmware that configures and uses GPIO using only direct register writes:
- No HAL, no CubeMX generated code, only register manipulation
- Enable GPIOA clock by writing to RCC_AHB1ENR
- Configure PA5 as output by writing to GPIOA_MODER
- Blink PA5 by writing to GPIOA_ODR
- Connect GDB to Wokwi simulation, set a breakpoint, read register values

**Evening — Document (30 minutes)**

Write day-32.md. Find the GPIOA_MODER register in RM0090. Screenshot the register
description table. Write: what bit values configure PA5 as a general purpose output?
Show the exact hex value you write and explain each bit.

---

### Day 33 — UART: The Embedded Developer's Console

**Morning — Study (2 hours)**

Topics:
- UART2 on STM32F4: TX on PA2, RX on PA3, connected to the ST-Link virtual COM port
- Baud rate calculation: derived from system clock and a divisor register
- The USART registers: CR1 (control), BRR (baud rate), DR (data), SR (status)
- Interrupt-driven reception: RXNE interrupt fires when a byte is received
- Redirecting printf to UART: implementing _write() syscall stub

Subtopics:
- Why printf goes to UART in embedded development: there is no screen
- The IT_RXNE interrupt: fired when the receive data register is not empty
- Circular reception buffer: storing incoming bytes without losing them
- Why your EmbeddedAI observer uses UART to stream structured JSON events

**Afternoon — Build (2 hours)**

UART firmware in Wokwi:
- Configure UART2 at 115200 baud using direct register writes (consult RM0090)
- Implement printf redirect to UART2
- Print "EmbeddedAI Observer Ready" on startup
- Print a JSON event every time the button is pressed:
  `{"event":"BUTTON_PRESS","ts":1234,"pin":"PC13"}`
- Python script on the other end that reads the serial port and parses the JSON

**Evening — Document (30 minutes)**

Write day-33.md. Write: what is the exact baud rate calculation for UART2 at 115200
baud when the system clock is 16MHz? Show the formula and the register value.

---

### Day 34 — Interrupts and the NVIC

**Morning — Study (2 hours)**

Topics:
- The NVIC: Nested Vectored Interrupt Controller, manages all 91 interrupt sources on STM32F4
- Interrupt priorities: 4-bit values on Cortex-M4, lower number = higher priority
- Preemption: a higher-priority interrupt can interrupt a lower-priority ISR
- The vector table: an array of function pointers at the start of Flash at 0x08000000
- Writing an ISR in C: function name must match the name in the startup file

Subtopics:
- The SysTick interrupt: fires every 1ms by default, drives HAL_GetTick() and HAL_Delay()
- The EXTI interrupt: triggered by external GPIO events — your button press
- Critical sections: disabling interrupts with __disable_irq() to protect shared data
- Interrupt latency on Cortex-M4: 12 clock cycles from interrupt signal to first ISR instruction
- Why the EmbeddedAI observer must understand interrupt context vs task context

**Afternoon — Build (2 hours)**

Interrupt-driven firmware in Wokwi:
- Configure EXTI interrupt on PC13 (button) at priority 1
- Configure TIM2 timer interrupt at priority 2 to fire every 100ms
- In each ISR, push a timestamped event struct to a volatile queue
- In the main loop, drain the queue and send events over UART as JSON
- Demonstrate that a high-priority ISR can preempt the UART transmission

**Evening — Document (30 minutes)**

Write day-34.md. Draw the timeline showing: TIM2 interrupt fires, begins sending
JSON over UART, button interrupt fires (higher priority), preempts UART ISR, button
ISR runs, returns, UART ISR resumes. Write: why is this preemption behavior critical
to understand for your observer?

---

### Day 35 — Week 5 Review and Project 4

**Afternoon and Evening — Project 4: Hardware Event Logger (5 hours)**

Build the first real hardware-to-software pipeline:

Firmware (in Wokwi):
- Three GPIO interrupt handlers at different priorities (simulating sensors)
- TIM2 interrupt generating periodic system health events every 500ms
- DMA-driven UART transmission of all events as newline-delimited JSON
- SysTick-based timestamps in all events
- Format: `{"ts":1234,"type":"GPIO_RISING","pin":"PA0","priority":1,"stack_free":892}`

Python receiver:
- Reads the Wokwi serial output (via wokwi-cli or WebSocket)
- Parses each JSON line into a FirmwareCrashEvent
- Stores all events in your PostgreSQL database via your Project 3 API
- Detects anomalies: any event where stack_free < 200 bytes triggers a CRITICAL alert
- Alerts stored in the database and logged to console

GitHub Actions:
- A wokwi CI step that runs your firmware for 30 seconds in simulation
- A test that verifies at least 60 events were received and correctly parsed

Why this matters: This is the first real connection between hardware and your software
stack. Your STM32 generates structured, typed events. Your Python system receives,
stores, and analyzes them. Every subsequent phase builds on this exact pipeline.

Real-world problem: Deployed devices currently have no way to send structured runtime
data to a central analytics system. This project provides that capability.

Commit: `feat: project-04 hardware event logger — first hardware-software pipeline`
Hashnode: "I Connected STM32 Firmware Events to a Python AI System"

---

## PHASE 2 — EMBEDDED SYSTEMS DEPTH
### Duration: 4 Weeks | Days 36 to 63
### Architecture Component: Physical Layer + Observation Layer
### Why: This builds the firmware observer — the component that watches firmware
### execution from inside. This is the hardest phase and the most unique part
### of your project. No existing AI tool can do what you build here.

---

## WEEK 6 — FreeRTOS: Real-Time Operating System
### Days 36 to 42

---

### Day 36 — What an RTOS Is and Why Firmware Needs One

Topics:
- What an RTOS is: a minimal OS for microcontrollers that manages concurrent tasks
- Tasks: independent units of execution, each with its own stack and priority
- The scheduler: runs the highest-priority ready task at all times
- Context switching: saving one task's CPU state (all registers) and loading another's

Subtopics:
- Cooperative vs preemptive scheduling — why preemptive is used in production
- Task states: Running (1 task), Ready (waiting for CPU), Blocked (waiting for event),
  Suspended (paused explicitly)
- The idle task: runs when no other task is ready, used for power management
- Why FreeRTOS: used in medical devices, automotive ECUs, aerospace systems — MISRA-C
  certifiable and battle-tested for 20 years

Study resource: FreeRTOS.org official documentation and the free FreeRTOS book PDF.

Document: Draw the complete task state diagram with all transitions labeled.

Build: FreeRTOS project in Wokwi with three tasks: LED_Task (blinks LED), UART_Task
(sends heartbeat every second), MONITOR_Task (prints all task stack usage every 5s).

---

### Day 37 — FreeRTOS Tasks and Stack Management

Topics: xTaskCreate parameters, task priorities, uxTaskGetStackHighWaterMark,
stack overflow detection, vTaskDelay vs HAL_Delay.

Build: Add stack overflow detection to all tasks using configCHECK_FOR_STACK_OVERFLOW.
Write a hook that sends a CRITICAL JSON event over UART when stack overflow is detected.
This is your first real observer capability.

---

### Day 38 — FreeRTOS Queues: The Safe Way to Pass Data Between Tasks

Topics: xQueueCreate, xQueueSend, xQueueReceive, xQueueSendFromISR,
queue blocking semantics, producer-consumer pattern.

Build: Refactor all event generation to use a central event queue. ISRs push to queue
using xQueueSendFromISR. Observer task reads from queue and sends over UART. This is
the exact architecture of your production observer.

---

### Day 39 — Semaphores, Mutexes, and Race Conditions

Topics: Binary semaphores, counting semaphores, mutexes, priority inversion,
priority inheritance, deadlock, critical sections.

Build: Add a mutex protecting UART access so multiple tasks can log safely. Demonstrate
the garbled output that occurs without the mutex. Add a counting semaphore that tracks
available buffer slots in your event queue.

---

### Day 40 — FreeRTOS Trace Hooks: The Observer Mechanism

**This is one of the most important days in the entire roadmap.**

Topics: Trace macros in FreeRTOSConfig.h, traceTASK_SWITCHED_IN,
traceTASK_SWITCHED_OUT, traceQUEUE_SEND, traceQUEUE_RECEIVE,
why trace hooks enable non-invasive observation.

Build: Implement all task switch trace hooks. Record every context switch as a
timestamped struct: {from_task, to_task, timestamp, from_stack_remaining}.
DMA-transmit this trace data over UART separately from application logs.
Python receiver that reconstructs the complete execution timeline from the trace.

Document: Write "The trace hook mechanism is why EmbeddedAI can observe firmware
execution without modifying the application being observed. This is what makes
non-invasive debugging possible."

---

### Day 41 — DMA for Zero-Overhead Logging

Topics: DMA UART transmission, circular DMA for reception, double buffering,
DMA transfer complete callbacks, measuring CPU overhead before and after.

Build: Replace all polled UART transmission in your observer with DMA. Measure CPU
usage with a high-watermark counter before and after. Document the improvement.

---

### Day 42 — Week 6 Review and Project 5

**Project 5: FreeRTOS Execution Observer**

Complete FreeRTOS application with:
- Three application tasks (sensor read, process, communicate)
- Observer task using trace hooks capturing every scheduling event
- DMA UART streaming of all observation data as JSON
- Python receiver detecting: tasks not running for too long, stack near overflow,
  queue fill level warnings
- All anomalies posted to your Project 3 API
- Wokwi CI test verifying the observer captures expected events

Real-world problem: Firmware developers have no visibility into RTOS execution
behavior without spending thousands on tools like Percepio Tracealyzer. This
provides equivalent visibility for free.

---

## WEEK 7 — GDB, OpenOCD, and Hardware Debugging
### Days 43 to 49

---

### Day 43 — GDB Fundamentals

Topics: Breakpoints, watchpoints, backtraces, printing variables, examining memory
with x command, GDB/MI interface.

Build: Connect GDB to your Wokwi simulation. Write a .gdbinit that automatically
sets breakpoints on all task functions and prints stack usage when each is hit.

---

### Day 44 — OpenOCD and JTAG

Topics: OpenOCD as GDB server, JTAG vs SWD protocols, ARM CoreSight architecture,
OpenOCD configuration files, flashing firmware with OpenOCD.

Build: Start OpenOCD, connect GDB, halt the running firmware, read the GPIOA_ODR
register at 0x40020014, modify it, verify the LED state changes. Document the
exact commands.

---

### Day 45 — GDB Python Scripting: Giving AI Eyes on Hardware

**This is Complexity Spike 2. This is where the AI gets access to hardware.**

Topics: The gdb Python module, gdb.execute(), gdb.parse_and_eval(),
gdb.Breakpoint, gdb.StopEvent, writing custom GDB commands in Python.

Build: A GDB Python script that:
- Automatically runs when GDB attaches to the target
- Reads the complete FreeRTOS task list by traversing the pxReadyTasksLists linked list
- For each task: reads name, state, priority, stack base, stack pointer, stack free bytes
- Outputs this as JSON to a file that your Python monitoring system reads
- Sets a breakpoint on vTaskSwitchContext that logs every context switch

This script is the core of your GDB bridge.

---

### Day 46 — SVD Parser: Translating Hardware to Human Language

Topics: SVD file structure (XML), peripheral/register/field hierarchy,
address-to-name translation, manufacturer quirks.

Build: Full SVD parser class:
```python
class SvdParser:
    def load(self, svd_path: str) -> None
    def translate_address(self, address: int) -> SvdRegister
    def decode_fields(self, register: SvdRegister, value: int) -> Dict[str, int]
    def format_for_llm(self, address: int, value: int) -> str
```
The format_for_llm method outputs: "RCC.AHB1ENR = 0x00000001 (GPIOAEN=1, all others=0)"
This is exactly what gets included in prompts to the LLM.

---

### Day 47 — Segger RTT: High-Speed Telemetry

Topics: RTT control block, magic string scanning, host-side RTT reading,
timing overhead comparison vs UART.

Build: Add RTT to your firmware for high-frequency telemetry (context switch data).
Python RTT reader via OpenOCD RTT server. Compare: UART at 115200 baud handles 11KB/s,
RTT handles 1MB/s with zero CPU overhead.

---

### Day 48 — Hard Fault Handler: The Most Important Firmware Component

**This is Complexity Spike 3. The hardest day in Phase 2.**

Topics: Hard fault causes (bad memory access, stack overflow, invalid instruction),
fault status registers (HFSR, CFSR, MMFAR, BFAR), the exception frame on the stack,
reading PC at fault time, recovery strategies.

Build: Complete hard fault handler that before resetting:
1. Reads CFSR, HFSR, MMFAR, BFAR
2. Extracts stacked PC (the address of the faulting instruction)
3. Reads the last 10 entries from your trace hook ring buffer
4. Reads all task stack usage from FreeRTOS
5. Formats everything as a comprehensive JSON crash report
6. Transmits over UART using polled (not DMA) transmission (DMA may be broken)
7. Stores key fields in backup SRAM (survives reset)
8. Resets the system

Python fault analyzer that reads the crash report and:
- Decodes the fault type from CFSR bits using your SVD parser knowledge
- Identifies the likely cause from the faulting PC address and recent execution trace
- Stores in PostgreSQL and triggers an alert

Document: "The hard fault handler is the last line of defense. By the time it runs,
something has gone seriously wrong. Its job is to capture everything useful about
the moment of death before the system resets."

---

### Day 49 — Week 7 Review and Project 6

**Project 6: Intelligent Hardware Debugger**

The complete observation pipeline:
- FreeRTOS firmware: observer task, trace hooks, DMA UART, RTT, hard fault handler
- GDB Python bridge: task list reader, context switch logger, register reader
- SVD parser: all addresses in crash reports translated to human-readable names
- FastAPI endpoint receiving comprehensive crash reports
- Python analyzer: fault type classification, severity scoring, anomaly detection
- Wokwi CI: 60-second simulation with 10 deliberately injected events verified

This is the most significant project milestone so far. It is the complete hardware
observation layer of EmbeddedAI.

---

## WEEK 8 — Simulation, CI, and Kafka
### Days 50 to 56

---

### Days 50-51 — Renode and Wokwi MCP

Topics: Renode installation and configuration, .resc machine files, Robot Framework
test scenarios, Wokwi MCP protocol, connecting an AI agent to Wokwi.

Build: Run your Project 6 firmware in Renode. Write 5 Robot Framework test scenarios
that verify your observer captures the correct events. Set up Wokwi MCP and connect
Claude to your simulation — have Claude write a small firmware fix, compile it,
and verify it runs correctly in simulation.

---

### Days 52-53 — Firmware CI/CD Pipeline

Topics: ARM cross-compilation in Docker, GitHub Actions for firmware, Wokwi CI
action, test result reporting.

Build: Complete GitHub Actions pipeline: compile firmware in Docker, run in Wokwi
simulation for 30 seconds, verify expected observer events were captured, post
results to your PostgreSQL database via your ingestion API.

---

### Days 54-56 — Apache Kafka Integration

Topics: Kafka concepts (topics, partitions, consumer groups, offsets), Docker Compose
Kafka setup, Python kafka-python library, producer and consumer patterns, why Kafka
replaces direct database writes.

Build: Add Kafka between your firmware event receiver and PostgreSQL:
- FirmwareEventProducer: publishes events to topic "firmware.events"
- CrashEventConsumer: reads from "firmware.events", writes to PostgreSQL
- AnomalyDetectorConsumer: reads from "firmware.events", detects anomalies
- Two consumers reading from the same topic independently — this is Kafka's superpower

**Project 7: Complete Observation Pipeline**
Everything from Phase 2 integrated: firmware → GDB bridge → RTT → Kafka → PostgreSQL,
containerized, observable, tested. A deployable production service.

---

## PHASE 3 — AI AND MEMORY SYSTEMS
### Duration: 5 Weeks | Days 57 to 91
### Architecture Component: Knowledge Layer + Reasoning Layer

---

## WEEK 9 — Embeddings and Semantic Search
### Days 57 to 63

---

### Day 57 — Vector Embeddings: Teaching AI to Understand Meaning

Topics: What an embedding is, why similar meanings produce close vectors, cosine
similarity calculation, the all-MiniLM-L6-v2 model, sentence-transformers library.

Build: Embed 20 real firmware bug descriptions collected from GitHub issues. Compute
all pairwise similarities. Verify that "stack overflow in UART ISR" and "ISR caused
stack exhaustion" score above 0.85 similarity. Document this with actual numbers.

---

### Day 58 — ChromaDB: Development Vector Database

Topics: ChromaDB collections, add/query/get/delete operations, metadata filtering,
distance functions, persistent storage.

Build: A FirmwareBugMemory class using ChromaDB:
- store_bug(event: FirmwareCrashEvent, embedding: List[float])
- find_similar(description: str, top_k: int = 5) -> List[SimilarBug]
- filter_by_type(crash_type: str) -> List[FirmwareCrashEvent]

Test: Store all your Project 1-6 bug events. Query with new descriptions. Verify
relevant bugs are retrieved even when using different terminology.

---

### Day 59 — pgvector: Production Semantic Search

Topics: pgvector installation, vector column type, HNSW index creation, cosine
similarity queries, combining vector search with SQL filters.

Build: Migrate FirmwareBugMemory from ChromaDB to pgvector. Add:
- Hybrid search: combine vector similarity with SQL filter on crash_type and severity
- Temporal decay: recent events weighted higher than old ones
- Alembic migration adding the embedding column to crash_events table

---

### Days 60-61 — Knowledge Graph: Mapping Your Codebase

Topics: Tree-sitter for AST parsing, NetworkX for graph construction, extracting
function call relationships, generating LLM-consumable codebase summaries.

Build: CodebaseMapper class:
- parse_firmware_project(path: str) -> CodebaseGraph
- get_function_context(function_name: str) -> str (which functions call it, what it calls)
- get_affected_components(function_name: str) -> List[str]
- summarize_for_llm() -> str (compressed architecture description for prompts)

Test on your Project 6 firmware. Verify it correctly maps the relationships between
your observer task, event queue, and UART transmission functions.

---

### Days 62-63 — RAG Pipeline: Retrieval Augmented Generation

Topics: RAG architecture, LangChain document loading and splitting, retrieval chains,
prompt templates, output parsers.

Build: FirmwareRAGPipeline:
- Given a new crash event, retrieve the 5 most similar past events
- Retrieve the codebase context for the affected function
- Assemble a structured prompt including: current event, similar past events,
  relevant code context, register state (translated via SVD parser)
- Call Ollama with DeepSeek Coder model
- Parse the response into a structured diagnosis

Test: Give it the hard fault from Project 6. Verify the retrieved context includes
the correct similar events and the diagnosis is accurate.

---

## WEEK 10 — Letta Memory and LangGraph Agent
### Days 64 to 70

---

### Day 64 — Letta: The Memory Architecture

Topics: Letta (MemGPT) architecture, three memory tiers, tool calling for memory
management, the agent-as-memory-controller pattern.

Build: Install Letta. Create a FirmwareDebugAgent with:
- Core memory: current firmware project context, chip family, FreeRTOS version
- Archival memory: all past bugs and fixes stored and searchable
- Recall memory: last 20 events in the current debugging session
- Tool: save_bug_resolution(bug_id, fix_description, fix_type)
- Tool: search_similar_bugs(description, chip_family)
- Tool: get_function_history(function_name)

---

### Days 65-67 — LangGraph: Stateful Reasoning Loops

Topics: LangGraph StateGraph, nodes, edges, conditional branching, state management,
the ReAct pattern (Reason + Act), multi-turn reasoning.

Build: FirmwareDebugGraph — a LangGraph workflow:
```
START
  ↓
receive_crash_event (node)
  ↓
retrieve_similar_bugs (node) — calls Letta archival search
  ↓
retrieve_code_context (node) — calls CodebaseMapper
  ↓
analyze_with_llm (node) — calls Ollama with assembled context
  ↓
confidence_check (conditional) — high confidence → suggest_fix, low → request_more_info
  ↓
suggest_fix / request_more_info (nodes)
  ↓
store_diagnosis (node) — saves to Letta memory
  ↓
END
```

Test: Run 10 real crash events through the graph. Verify the reasoning loops
correctly and retrieves relevant context at each step.

---

### Days 68-70 — Ollama and Local LLM Deployment

Topics: Ollama installation, pulling models, API usage, DeepSeek Coder V2
capabilities, prompt engineering for firmware debugging, system prompts.

Build: Write production-quality system prompts for firmware debugging:
- System prompt that establishes the agent as an embedded systems expert
- Firmware-specific prompt template that structures crash data for LLM reasoning
- Few-shot examples of good diagnoses included in the prompt
- Output format specification: JSON with diagnosis, confidence, suggested_fix, references

**Project 9: EmbeddedAI Reasoning Agent**

Complete reasoning agent that:
- Receives firmware crash events from Kafka
- Retrieves similar bugs and code context
- Reasons with a local LLM (no cloud required)
- Outputs structured diagnosis with confidence score
- Stores all diagnoses in Letta memory
- Tested with 20 crash scenarios, accuracy documented

---

## PHASE 4 — SELF-HEALING AGENT
### Duration: 4 Weeks | Days 71 to 98
### Architecture Component: Healing Layer

---

## WEEKS 11-12 — Safe Self-Healing
### Days 71 to 84

---

### Days 71-73 — Git Patch Generation

Topics: git internals (objects, refs, commits), programmatic git with GitPython,
generating unified diffs, creating branches, applying patches, reverting changes.

Build: PatchGenerator class:
- generate_patch(original_file: str, fixed_content: str) -> GitPatch
- create_fix_branch(bug_id: str) -> str
- apply_patch(patch: GitPatch, branch: str) -> bool
- revert_patch(branch: str) -> bool

---

### Days 74-75 — Automated Test Validation

Topics: pytest programmatic execution, test result parsing, coverage measurement,
what it means for a firmware patch to be "tested."

Build: PatchValidator class:
- run_tests(branch: str) -> TestResult
- validate_firmware_patch_in_simulation(patch: GitPatch) -> SimulationResult
  (compiles firmware, runs in Wokwi simulation, checks for expected behavior)
- calculate_confidence(test_result: TestResult, similar_past_fixes: List) -> float

---

### Days 76-78 — Confidence Scoring and Safe Autonomy

Topics: Calibrated uncertainty, confidence threshold design, what makes a fix
low-risk vs high-risk, the human-in-the-loop requirement.

Build: ConfidenceScorer with rules:
- High confidence (>0.9): identical bug seen 3+ times, same fix worked every time,
  tests pass, low code complexity → apply automatically
- Medium confidence (0.6-0.9): similar bug, similar fix, tests pass → present to developer
- Low confidence (<0.6): novel bug, uncertain fix, or complex code → explain and ask

---

### Days 79-84 — Canary Deployment and Rollback

Topics: Canary deployment strategy, blue-green deployment, automatic rollback
conditions, deployment gates.

Build: SelfHealingAgent that:
- Classifies each bug as high/medium/low confidence
- For high confidence: applies fix to git branch, runs tests in simulation,
  if tests pass commits to main, logs the autonomous action with full audit trail
- For medium confidence: creates a pull request with the fix, explanation, and
  test results for developer review
- For low confidence: posts detailed analysis to Slack/email, waits for human decision
- For all levels: records outcome in Letta memory to improve future confidence scoring

**Project 10: Safe Self-Healing Agent**

Demonstrated on 5 real bug scenarios with different confidence levels. Full audit
trail in git. Video demo showing: bug occurs → observer captures → AI diagnoses →
high-confidence fix applied automatically → tests pass → committed to main.

---

## WEEKS 13-14 — Full System Integration
### Days 85 to 98

---

### Days 85-91 — End-to-End Integration

Connect all layers into one running system:

Physical Layer (Wokwi simulation) → Observer Task → DMA UART → Python Receiver →
Kafka → [Crash Consumer → PostgreSQL] → [Anomaly Consumer → Alert] →
LangGraph Agent → Letta Memory → Confidence Scorer → SelfHealingAgent →
Git Patch → Wokwi Simulation Test → If pass: commit to main

Run 20 deliberately injected bugs through the complete pipeline. Document:
- Time from bug occurrence to AI diagnosis (target: under 30 seconds)
- Accuracy of diagnosis (correct root cause identified)
- Self-healing success rate for high-confidence bugs
- False positive rate (bugs flagged as high-confidence that were actually wrong)

---

### Days 92-98 — Performance, Reliability, and Production Hardening

Topics: Load testing with locust, database query optimization, LLM inference
latency optimization, retry logic, circuit breakers, graceful degradation.

Build: Production hardening of all services:
- Retry with exponential backoff on all external calls
- Circuit breaker on LLM calls (fall back to "insufficient data" if LLM is unavailable)
- Database connection pool tuning
- Kafka consumer group rebalancing handling
- Health checks for all services in Docker Compose

**Project 11: EmbeddedAI Alpha**
The complete system end-to-end. Containerized. Tested. Observable. Ready for the
interface layer.

---

## PHASE 5 — DEVELOPER INTERFACE
### Duration: 3 Weeks | Days 99 to 119
### Architecture Component: Interface Layer

---

## WEEKS 15-17 — Tauri + React Desktop Application
### Days 99 to 119

---

### Days 99-104 — React Fundamentals

Topics: React components, props, state with useState, effects with useEffect,
fetching data from FastAPI with fetch/axios, Tailwind CSS for styling.

Build: React dashboard with:
- Live telemetry feed (WebSocket from Kafka via FastAPI WebSocket endpoint)
- Crash event list with filtering and sorting
- Event detail view with register state decoded by SVD parser
- Statistics panel: crash counts by type, resolution rate, mean time to diagnose

---

### Days 105-110 — Tauri: Desktop Application

Topics: Tauri installation and project structure, Rust backend (minimal),
packaging for distribution, system tray integration, native file dialogs.

Build: Wrap your React dashboard in a Tauri application:
- System tray icon that shows a red/green indicator based on current crash status
- Native notification when a new CRITICAL crash is detected
- File dialog for selecting a firmware project to monitor
- Packaged as a .deb (Linux), .msi (Windows) installer

---

### Days 111-115 — Python SDK

Build the embeddedai Python package:
```python
# One-line integration for any Python application
import embeddedai

embeddedai.init(project="my-firmware", memory_path="./embeddedai-memory")

@embeddedai.observe
def process_sensor_data(sensor_id: int, value: float):
    # Your existing code unchanged
    ...
```

The @observe decorator automatically:
- Captures any exception with full context
- Sends to the ingestion API
- Retrieves and displays AI diagnosis

---

### Days 116-119 — VS Code Extension

Build a minimal VS Code extension that:
- Shows a status bar item with current crash count
- Opens the crash detail panel inline in the editor
- Highlights the suspected crash location in the source file

**Project 12: EmbeddedAI Developer Interface**
The complete polished interface: Tauri app, Python SDK, VS Code extension.
A developer can install this and have AI-powered firmware debugging in under 5 minutes.

---

## PHASE 6 — PRODUCTION HARDENING AND PORTFOLIO
### Duration: 2 Weeks | Days 120 to 140

---

### Days 120-130 — Production Quality

Topics: Security (API authentication with JWT, secrets management with HashiCorp Vault),
OWASP top 10 for API security, bandit security scanning, dependency vulnerability
scanning with safety, SSL/TLS for all services.

Build: Security hardening for all services, rate limiting, API key authentication,
audit logging for all autonomous healing actions.

---

### Days 131-140 — Complete Documentation and Portfolio

Build the final documentation:
- README.md: 2000-word project overview with architecture diagram, quick start,
  screenshots, and technology justification
- ARCHITECTURE.md: complete system design document explaining every decision
- API.md: complete API reference for all endpoints
- CONTRIBUTING.md: how to contribute, coding standards, testing requirements
- CHANGELOG.md: version history
- 12 Hashnode posts: one per project
- Demo video: 10-minute walkthrough showing a bug being diagnosed and auto-healed
- LinkedIn article: "I Spent 5 Months Building an AI Debugging System for Firmware —
  Here Is What I Learned"

**Final Deliverable: EmbeddedAI v1.0**
A production-grade, fully documented, fully tested, fully containerized open-source
framework. Published on GitHub. The README is good enough that a firmware developer
at Bosch could read it, understand the value, and install it in 10 minutes.

---

## COMPLETE TECHNOLOGY REFERENCE

### All Free Tools — Zero Cost

| Tool | Purpose | How to Get |
|------|---------|-----------|
| Python 3.12 | AI and data layer | python.org |
| STM32CubeIDE | Firmware development IDE | st.com |
| arm-none-eabi-gcc | ARM cross-compiler | apt install gcc-arm-none-eabi |
| OpenOCD | Hardware debug bridge | openocd.org |
| GDB (arm) | Hardware debugger | included with gcc-arm |
| Wokwi | STM32/ESP32 simulator | wokwi.com |
| Renode | Professional firmware emulator | renode.io |
| Docker Desktop | Container runtime | docker.com |
| PostgreSQL | Production database | via Docker |
| pgvector | Vector search for PostgreSQL | via Docker |
| Apache Kafka | Event streaming bus | via Docker |
| Zookeeper | Kafka dependency | via Docker |
| ChromaDB | Development vector database | pip install chromadb |
| FastAPI | Python web framework | pip install fastapi |
| Pydantic | Data validation | pip install pydantic |
| Alembic | Database migrations | pip install alembic |
| asyncpg | Async PostgreSQL client | pip install asyncpg |
| kafka-python | Kafka Python client | pip install kafka-python |
| LangChain | RAG pipeline framework | pip install langchain |
| LangGraph | Agent workflow framework | pip install langgraph |
| Letta | Memory architecture | pip install letta |
| Ollama | Local LLM runner | ollama.ai |
| DeepSeek Coder V2 | Code-specialized LLM | ollama pull deepseek-coder-v2 |
| sentence-transformers | Embedding generation | pip install sentence-transformers |
| tree-sitter | Code AST parser | pip install tree-sitter |
| NetworkX | Graph data structure | pip install networkx |
| GitPython | Programmatic git | pip install gitpython |
| pytest | Testing framework | pip install pytest |
| OpenTelemetry | Distributed tracing | pip install opentelemetry-sdk |
| Prometheus | Metrics collection | via Docker |
| Grafana | Metrics visualization | via Docker |
| Jaeger | Distributed trace UI | via Docker |
| Tauri | Desktop app framework | tauri.app |
| React | Frontend framework | via npm |
| Tailwind CSS | CSS framework | via npm |

---

## COMPLEXITY SPIKE WARNINGS

These are the exact moments where most people stop. Knowing they are coming means
you can plan for them.

**Spike 1 — Day 10: C Pointers.**
Two to three weeks of confusion is normal. The solution is drawing memory diagrams
by hand on paper, not reading more text. Every time you are confused, draw the memory.

**Spike 2 — Days 44-48: GDB + OpenOCD + Real Hardware Connection.**
The GDB bridge freezing when a hard fault occurs will happen. The chip stops
responding. OpenOCD loses connection. You have no information about why.
Plan for three days of debugging this before it works reliably.

**Spike 3 — Day 48: Hard Fault Handler.**
No tutorial covers this cleanly. You will read conflicting information online.
The ARM Cortex-M4 Technical Reference Manual (free from ARM) is the authoritative
source. Section 2.3 covers the exception frame. Read it carefully.

**Spike 4 — Days 65-70: LangGraph Agent Debugging.**
AI agents fail in non-obvious ways: infinite loops, wrong tool calls, plausible
but incorrect answers. You need systematic evaluation — a test set of known bugs
with known correct answers — before you can trust the system. Build the evaluation
framework before building more agent features.

**Spike 5 — Days 76-78: Confidence Threshold Calibration.**
You cannot calibrate this without real data. The numbers will be wrong at first.
Plan to run the system on real bugs for two to three weeks before the thresholds
are correct. Document every case where the confidence was wrong and why.

---

## DOCUMENTATION PLATFORMS AND STRATEGY

| Platform | What to Post | Frequency | Purpose |
|----------|-------------|-----------|---------|
| GitHub (daily commits) | Code, journals, architecture decisions | Every day | Proof of consistent work |
| Hashnode | Project writeups, learning summaries | Weekly | SEO visibility, recruiter discovery |
| LinkedIn | Project milestone updates | Monthly | Professional network visibility |
| YouTube (optional) | Demo videos of working projects | Per major project | Visual proof of working system |

### The 12 Hashnode Posts You Must Write

1. Why I Am Building an AI Debugging System for Firmware
2. Understanding Binary and Memory: The Foundation Nobody Teaches
3. My First C Program That Simulates the Three Most Common Firmware Crashes
4. Building a Production Crash Analytics API: Every Architecture Decision Explained
5. Connecting STM32 Firmware Events to a Python AI System
6. FreeRTOS Trace Hooks: How to Observe Firmware Without Changing It
7. Building a GDB Python Bridge: Giving an AI Agent Eyes on Physical Hardware
8. The SVD Parser: How AI Reads Hardware Register Values as Human Language
9. Why Kafka, pgvector, and Ollama Instead of Simpler Alternatives
10. Semantic Similarity Search for Firmware Bugs: Better Than Keyword Matching
11. Building a Self-Healing Firmware System: When to Trust the AI to Act Alone
12. EmbeddedAI v1.0: A Complete Architecture Retrospective

---

## PHASE AND TIMELINE SUMMARY

| Phase | Weeks | Days | Main Skill | Architecture Layer |
|-------|-------|------|-----------|-------------------|
| Phase 1 | 1-5 | 1-35 | Computer science + C + Python + DevOps | Foundation |
| Phase 2 | 6-8 | 36-56 | Firmware + RTOS + Hardware Debugging | Physical + Observation |
| Phase 3 | 9-10 | 57-70 | AI + Embeddings + Memory + Reasoning | Knowledge + Reasoning |
| Phase 4 | 11-14 | 71-98 | Self-healing + Integration | Healing Layer |
| Phase 5 | 15-17 | 99-119 | Developer Interface + SDK | Interface Layer |
| Phase 6 | 18-20 | 120-140 | Security + Documentation + Portfolio | All layers |

**Total: 20 weeks at 4-6 hours per day.**
**Working prototype demonstrating core concept: end of Phase 3 (Week 10).**
**Deployable production system: end of Phase 5 (Week 17).**
**Portfolio-ready with full documentation: end of Phase 6 (Week 20).**

---

## THE 12 MILESTONE PROJECTS SUMMARY

| Project | Phase | What It Proves |
|---------|-------|---------------|
| Mini-Project 0: Hardware Simulator | Phase 1 | You understand how a CPU, memory, UART, and DMA work |
| Project 1: Crash Simulator + Analyzer | Phase 1 | You understand the three major firmware crash types |
| Project 2: Firmware Event Ingestion API | Phase 1 | You can build production-grade FastAPI services |
| Project 3: Production Crash Analytics | Phase 1 | You can build MNC-standard containerized services |
| Project 4: Hardware Event Logger | Phase 1 | You connected real hardware events to a Python system |
| Project 5: FreeRTOS Execution Observer | Phase 2 | You built non-invasive firmware observation |
| Project 6: Intelligent Hardware Debugger | Phase 2 | You built the complete hardware observation layer |
| Project 7: Complete Observation Pipeline | Phase 2 | You built production firmware → Kafka → PostgreSQL |
| Project 9: EmbeddedAI Reasoning Agent | Phase 3 | You built a local AI that diagnoses firmware bugs |
| Project 10: Safe Self-Healing Agent | Phase 4 | You built autonomous firmware repair |
| Project 11: EmbeddedAI Alpha | Phase 4 | You integrated all seven layers end-to-end |
| Project 12: Developer Interface | Phase 5 | You built a polished product developers can install |

---

## FINAL ARCHITECTURE DECISION RATIONALE

When a company asks you "why did you build it this way," your answer for every
technology is in this document. But the overarching answer is:

Every technology in this stack was chosen because it is:

1. **Free and open source** — no licensing cost, no vendor lock-in, deployable anywhere
2. **Production-proven** — used by major companies in real systems, not a toy
3. **The right tool for the specific job** — not the simplest, the most appropriate
4. **Connected to the next layer** — each technology enables the one above it
5. **Self-hostable** — your firmware customers cannot send their code to the cloud

The architecture separates concerns into seven layers so that:
- Each layer can be improved independently
- Each layer can be tested independently
- Each layer can be replaced if a better tool appears
- A developer can adopt only the layers they need

This is system design at MNC standard. You did not just learn to code. You learned
to architect a production system from first principles — and you documented every
decision along the way.