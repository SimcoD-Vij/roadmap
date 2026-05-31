# MASTER ROADMAP — ALL FOUR DOMAINS
## InfraMesh | SentinelGrid | PulseGrid | MemCore (Embedded AI)
## Part 1: Mental Model + Architecture + Master Skill Table

---

# CHAPTER 0 — READ THIS BEFORE ANYTHING ELSE

## 0.1 The One Mental Model That Covers Everything

Everything you will learn fits inside one sentence:

**"Data is produced by a system, moved through a pipeline, stored in a database, analyzed by AI, and acted upon by automation — and this happens at every layer from silicon to cloud."**

Every skill, every project, every day of learning is just a variation of this sentence at a different layer.

```
LAYER          WHAT PRODUCES DATA     HOW IT MOVES      WHERE IT IS STORED    WHAT ANALYZES IT
─────────────────────────────────────────────────────────────────────────────────────────────
Silicon        Transistors/Registers  Bus/DMA            SRAM/Flash            Firmware logic
Firmware       Sensors/Interrupts     UART/SPI/I2C       Flash/EEPROM          FreeRTOS tasks
Edge Device    FFT/Feature extract    MQTT/LoRa          SPI Flash buffer      TFLite model
Gateway        Node aggregation       MQTT Bridge        InfluxDB (local)      Python pipeline
Cloud          All device telemetry   Kafka/Kinesis      TimescaleDB           ML model
Application    User actions/API calls HTTP/REST          PostgreSQL            Risk classifier
Intelligence   All engineering signals Graph traversal  Neo4j/Vector DB       LLM + embeddings
```

**SentinelGrid lives at rows 1–5.**
**InfraMesh lives at rows 6.**
**PulseGrid lives at rows 6–7.**
**MemCore lives at rows 1–7 (the intelligence layer at every row).**

---

## 0.2 Individual Architecture of Each Project

### PROJECT 1 — InfraMesh
```
DEVELOPER
    │ POST /api/v1/services (register a service)
    ▼
[FastAPI API Server]
    │ writes service record
    ├──────────────────────────────► [PostgreSQL — service registry]
    │ drops task into queue
    ▼
[AWS SQS Queue]
    │ worker picks up task
    ▼
[Python Worker]
    ├── Creates Route53 DNS record
    ├── Configures ALB load balancer rule
    ├── Provisions ACM TLS certificate
    ├── Sets up CloudFront edge protection
    ├── Writes status to DynamoDB
    │
    ▼
[Nginx/Envoy Proxy — Edge Layer]
    ├── Rate limiting (Redis counters)
    ├── JWT authentication
    ├── Access logging
    │
    ▼
[Developer's Service — now live]
    │ health check every 30s
    ▼
[Health Check Worker]
    ├── Writes results to TimescaleDB
    ├── Fires alert on 3 consecutive failures
    │
    ▼
[Grafana Dashboard]
    ├── Service health map
    ├── Provisioning queue depth
    └── Cost attribution per team
```

### PROJECT 2 — SentinelGrid
```
PHYSICAL WORLD (Factory)
    │
[SentinelNode PCB — ESP32-S3]
    ├── ADXL355 (vibration, SPI, 1kHz, DMA)
    ├── INA226 (current, I2C, 100Hz)
    ├── MLX90614 (temperature, I2C, 1Hz)
    ├── INMP441 (acoustic, I2S)
    ├── MQ-135 (gas, ADC)
    │
    [FreeRTOS Tasks]
    ├── Sensor Task → ring buffer
    ├── FFT + Feature Task → 15-element vector
    ├── Inference Task → TFLite INT8 → anomaly score
    ├── Comms Task → MQTT publish
    ├── OTA Task → checks S3 for updates
    ├── Watchdog Task → feeds HW watchdog
    └── Health Reporter → heap/stack/uptime
    │
    │ MQTT over WiFi (QoS 1, TLS)
    ▼
[Raspberry Pi Gateway]
    ├── Mosquitto broker (local)
    ├── Python aggregation pipeline
    ├── Local InfluxDB (offline buffer)
    └── Gateway-level anomaly detection
    │
    │ MQTT Bridge (AWS IoT Core)
    ▼
[AWS Cloud]
    ├── AWS IoT Core (MQTT at scale)
    ├── Kinesis Data Stream (ingestion)
    ├── Lambda (stream processing)
    ├── TimescaleDB (telemetry storage)
    ├── SageMaker (model retraining)
    ├── S3 + CloudFront (OTA artifacts)
    └── FastAPI (device management API)
    │
    ▼
[Grafana Dashboard]
    ├── Fleet health map
    ├── Per-machine anomaly timeline
    ├── OTA deployment status
    └── Worker safety zone map
```

### PROJECT 3 — PulseGrid
```
ENGINEERING SIGNALS (From Every Tool)
    │
    ├── GitHub webhooks (PR events, commits, reviews)
    ├── GitHub Actions / Jenkins (build + deploy events)
    ├── PagerDuty webhooks (incident open/resolve)
    ├── Sentry webhooks (error rate events)
    ├── Prometheus remote_write (metrics)
    └── OpenTelemetry OTLP (distributed traces)
    │
    ▼
[FastAPI — Webhook Ingestion API]
    │ validates + enriches each event
    ▼
[Apache Kafka — Event Stream]
    ├── Topic: events.github
    ├── Topic: events.incidents
    ├── Topic: events.metrics
    └── Topic: events.traces
    │
    ▼
[Python Stream Processor — Kafka Consumer]
    ├── Dependency Graph Updater → Neo4j
    ├── Risk Feature Extractor → TimescaleDB
    └── Incident Timeline Assembler → PostgreSQL
    │
    ├──────────────────────────┐
    ▼                          ▼
[Neo4j — Dependency Graph]  [TimescaleDB — All Events]
Service A → Service B       Every signal with timestamp
Blast radius queries        Risk model training data
    │                          │
    ▼                          ▼
[Risk Scoring Worker]       [Postmortem Generator]
XGBoost classifier          Queries all signals
Trained on YOUR incidents   Passes to Claude/GPT API
Posts score to GitHub PR    Posts draft to Confluence
    │
    ▼
[Grafana + React Dashboard]
├── High-risk open PRs
├── Live dependency map
├── DORA metrics
└── Reliability trends
```

### PROJECT 4 — MemCore (Embedded AI SDK)
```
ANY SYSTEM (Software App, Firmware, Microservice)
    │ imports MemCore
    ▼
[MemCore Observation Layer]
    ├── Static Analyzer — AST parser, call graph builder
    ├── Runtime Hook — exception interceptor, log streamer
    └── Change Tracker — git diff processor
    │
    ▼
[MemCore Memory Layer]
    ├── Short-term: Redis (current session events)
    ├── Long-term: ChromaDB (vector embeddings of past bugs)
    └── Episodic: PostgreSQL (structured incident history)
    │
    ▼
[MemCore Vocabulary Engine]
    ├── Builds semantic map of what each function MEANS
    ├── Detects when meaning has drifted from historical norm
    └── Creates new vocabulary entries for new patterns
    │
    ▼
[MemCore Reasoning Layer]
    ├── Assembles context: current error + similar past bugs + relevant code
    ├── Calls LLM with structured prompt
    ├── Returns ranked fix suggestions with explanations
    └── Optionally stages auto-fix as a PR
    │
    ▼
[MemCore learns from outcome]
    └── Developer accepts/rejects → stored → model improves
```

---

## 0.3 How All Four Projects Integrate

```
THE UNIFIED SYSTEM

MemCore SDK (intelligence layer)
    │ used by         │ used by         │ used by
    ▼                 ▼                 ▼
SentinelGrid      InfraMesh         PulseGrid
(Hardware-AI)     (Infra Platform)  (Eng Intelligence)
    │                 │                 │
    └─────────────────┴─────────────────┘
                      │
              Shared Infrastructure
              ├── AWS (IoT Core, Kinesis, RDS, S3, Lambda)
              ├── Terraform (all infra as code)
              ├── Docker (all services containerized)
              ├── Grafana (all dashboards)
              ├── FastAPI (all backend APIs)
              ├── PostgreSQL (all structured data)
              └── TimescaleDB (all time-series data)
```

**What this means for learning:**
Every skill you learn appears in multiple projects. Python is used in all four. FastAPI is used in all four. TimescaleDB is used in all four. Docker is used in all four. The skill is learned once. The application varies by project. This is why the master roadmap teaches skills, not projects. Projects are where skills are applied.

---

# CHAPTER 1 — MASTER SKILL TABLE

## How to Read This Table

Each row is one skill. The columns tell you:
- **Skill**: The specific thing you learn
- **Level**: Phase 0 (foundation) to Phase 5 (advanced)
- **Outcome**: What you can do after learning this
- **Interview Statement**: Exact words to use in an interview
- **InfraMesh Use**: How this skill appears in InfraMesh
- **SentinelGrid Use**: How this skill appears in SentinelGrid
- **PulseGrid Use**: How this skill appears in PulseGrid
- **MemCore Use**: How this skill appears in MemCore

---

## PHASE 0 — MENTAL FOUNDATIONS (Days 1–14)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 0.1 | How the Internet Works (DNS, HTTP, TCP/IP) | Trace any data packet from browser to server and back. Explain what DNS does, what TCP handshake is, what HTTP methods mean | "I understand the full request lifecycle from DNS resolution through TCP handshake to HTTP response, and I applied this when designing InfraMesh's API routing and SentinelGrid's MQTT communication" | DNS records provisioned by worker. HTTP REST API for developers | MQTT runs over TCP/IP. DNS resolves gateway hostname | HTTP webhooks received from GitHub/PagerDuty | MemCore calls LLM API over HTTPS |
| 0.2 | Linux Command Line | SSH into any server, navigate filesystem, read logs, run processes, write shell scripts | "I work entirely in Linux environments. I debug production services by SSH-ing into EC2 instances, reading structured logs with grep/awk, and using shell scripts for automation" | EC2 deployment via SSH. Shell scripts for provisioning | SSH into gateway Pi. Shell scripts for OTA deployment | All Kafka/Neo4j services run on Linux | MemCore runs as Linux daemon |
| 0.3 | Git and GitHub | Version control all code, write meaningful commits, create branches, open PRs, understand git history | "I use Git as the source of truth for everything — code, Terraform, firmware, documentation. My GitHub shows a consistent commit history and ADR documents for every major decision" | All InfraMesh code in GitHub. CI/CD triggered on push | Firmware + Terraform in GitHub. CI/CD builds firmware binary | PulseGrid ingests GitHub events — must understand the data it processes | MemCore tracks git diffs to detect what changed before a bug |
| 0.4 | How Computers Work (CPU, Memory, OS) | Explain stack vs heap, what the OS does, how processes work, what system calls are | "I understand memory architecture from stack/heap at the application level down to SRAM/flash at the firmware level — which helped me design SentinelGrid's memory management and MemCore's vocabulary system" | Python processes run on OS with managed heap | Firmware runs without OS on bare metal, manually managing stack and heap | Python services run as OS processes | MemCore intercepts OS-level signals |
| 0.5 | Systems Thinking (How Systems Fail) | Explain what happens when one component in a distributed system fails. Understand cascading failures, partial failures, timeout propagation | "I design every system assuming components will fail. I've documented failure modes for all four projects in postmortem format, and I use this thinking to design resilient architectures" | If SQS fails, provisioning stops. API must return 503 gracefully | If WiFi fails, nodes buffer to flash and continue local inference | If Kafka consumer lags, alerts are delayed. Need backpressure handling | If LLM API fails, MemCore degrades to suggestion-only mode |

---

## PHASE 1 — PROGRAMMING FOUNDATIONS (Days 15–60)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 1.1 | Python Core (variables, functions, loops, classes) | Write Python programs that process data, handle errors, and are organized into classes and modules | "Python is my primary language for backend systems, AI pipelines, and automation scripts across all four projects" | API, worker, tests | Gateway pipeline, ML training | All backend services | Vocabulary engine, reasoning layer |
| 1.2 | Python Data Structures | Use lists, dicts, sets, tuples correctly. Understand time complexity of operations | "I understand when to use a dict vs list vs set based on O(1) vs O(n) lookup requirements — critical when processing thousands of events per second in PulseGrid" | Service registry queries | Feature vector as list | Risk feature dict | Bug memory as dict |
| 1.3 | Python File I/O and Error Handling | Read/write files, handle exceptions gracefully, use context managers | "I write all code assuming failures will happen. Every file operation, API call, and database query has explicit error handling with meaningful error messages" | Log file processing | Gateway reads node logs | Webhook payload parsing | Bug report file writing |
| 1.4 | Python Async (asyncio, await) | Write async Python code that handles thousands of concurrent operations without blocking | "InfraMesh's API handles 100 concurrent provisioning requests. Without async, each request would block. With asyncio, all 100 proceed simultaneously" | FastAPI is async. SQS consumer async | Gateway MQTT subscriber async | Kafka consumer async. Webhook handler async | LLM call is async (slow API) |
| 1.5 | Python OOP (Classes, Inheritance) | Design Python classes with clear responsibilities, use inheritance and composition correctly | "I design Python classes following single responsibility principle. MemCore's memory layer has separate classes for short-term cache, long-term vector store, and vocabulary engine" | Service class, Worker class | Sensor driver class, OTA manager class | EventProcessor class, RiskScorer class | MemoryController class, VocabularyEngine class |
| 1.6 | C Language Fundamentals | Write C programs with pointers, structs, bit manipulation, manual memory management | "I write embedded firmware in C. Understanding pointers and manual memory management is what allows me to write efficient firmware that runs in 256KB of RAM" | Not used (Python only) | All firmware in C. Sensor drivers in C | Not used directly | Lightweight MemCore agent in C for firmware |
| 1.7 | C Pointers and Memory | Deeply understand pointer arithmetic, stack vs heap in C, memory alignment | "I can trace memory corruption bugs in C by understanding exactly what's in each memory address. This is how I designed SentinelGrid's crash dump capture — it saves the exact memory state at fault time" | Not used | DMA transfers use pointer arithmetic | Not used | MemCore C agent uses static memory pools |
| 1.8 | C Structs and Bit Fields | Map hardware registers to C structs, use bit manipulation to set/clear individual bits | "Sensor register maps are represented as C structs in firmware. When the ADXL355 data register returns 0xB4A2, I can immediately decode each field by looking at the struct definition" | Not used | All sensor drivers use register structs | Not used | MemCore C agent packs data efficiently with structs |
| 1.9 | Rust Fundamentals (ownership, borrowing) | Write safe Rust code without data races or memory errors | "Rust's ownership system caught data races at compile time that would have caused intermittent crashes in production firmware. SentinelGrid's auth sidecar is in Rust for this reason" | Not used | Auth sidecar in Rust | Not used | MemCore sidecar agent in Rust for safety |
| 1.10 | Rust no_std for Embedded | Write Rust code that runs on microcontrollers without standard library | "I can write Rust firmware for STM32/ESP32 using the Embassy framework. This gives me memory safety guarantees that C cannot provide, critical for long-running unattended industrial devices" | Not used | Optional: Rust firmware with Embassy | Not used | MemCore embedded agent in Rust |

---

## PHASE 2 — DIGITAL HARDWARE AND PROTOCOLS (Days 61–90)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 2.1 | Digital Logic and Binary | Read binary, hex. Understand gates, flip-flops, registers | "I debug sensor communication by reading binary register values directly. When the ADXL355 returns 0x40, I know bit 6 is the data-ready flag without looking up the datasheet" | Not hardware | Sensor register decoding | Not hardware | Not directly |
| 2.2 | SPI Protocol | Configure SPI master, read/write sensor registers, handle CS timing | "I wrote the ADXL355 vibration sensor driver from scratch using SPI. The driver reads 6 bytes of raw X/Y/Z data in one transaction using DMA, achieving 1kHz sampling without CPU intervention" | Not hardware | ADXL355 vibration sensor | Not hardware | Not directly |
| 2.3 | I2C Protocol | Configure I2C master, handle multi-device addressing, implement pull-up design | "I debugged an intermittent I2C failure on SentinelNode by capturing the bus with a logic analyzer. The missing ACK showed the INA226 was in a bad state — the fix was a power-cycle sequence in the driver" | Not hardware | INA226 current, MLX90614 temperature | Not hardware | Not directly |
| 2.4 | UART/Serial | Configure UART, implement structured logging over serial | "I use UART for structured JSON logging from all FreeRTOS tasks. The gateway collects these logs and forwards to cloud — giving visibility into nodes 500km away without physical access" | Not hardware | Debug logs, firmware to gateway | Not hardware | MemCore C agent logs over UART |
| 2.5 | ADC (Analog to Digital) | Configure ADC, understand resolution, noise, sampling rate, DMA transfer | "I configured DMA-driven ADC sampling at 1kHz on the ESP32-S3. Without DMA, the CPU would waste 30% of its cycles copying ADC values. With DMA, it's zero CPU cost" | Not hardware | Gas sensor, battery voltage | Not hardware | Not directly |
| 2.6 | Oscilloscope | Probe signals, measure timing, identify ringing/noise | "I used an oscilloscope to identify switching regulator noise coupling into the ADC on SentinelNode revision 1. The FFT of the noise matched the switcher frequency exactly — fixed in revision 2 with ground plane separation" | Not hardware | PCB debugging, signal integrity | Not hardware | Not directly |
| 2.7 | Logic Analyzer | Capture SPI/I2C/UART transactions, verify protocol timing | "I verify every new sensor driver by capturing its transactions on a logic analyzer before testing on hardware. This caught a wrong SPI clock polarity that would have caused random reads" | Not hardware | Sensor driver verification | Not hardware | Not directly |

---

## PHASE 3 — MICROCONTROLLERS AND FIRMWARE (Days 91–140)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 3.1 | ESP32-S3 Architecture | Understand dual-core, memory layout, peripherals, clock configuration | "I chose ESP32-S3 for SentinelNode specifically because its vector extensions accelerate INT8 inference by 4x compared to standard Cortex-M4. I benchmarked both and documented the comparison" | Not hardware | Core MCU of SentinelNode | Not hardware | MemCore embedded agent target |
| 3.2 | Interrupt Handling | Write ISRs, understand interrupt latency, implement data-ready interrupt pattern | "The ADXL355 pulls its interrupt pin high when a new sample is ready. My ISR runs in under 2 microseconds, copies the data to a ring buffer, and returns. No samples are missed even at 4kHz" | Not hardware | Sensor data-ready interrupt | Not hardware | MemCore C agent uses interrupt-driven event capture |
| 3.3 | DMA Configuration | Configure DMA channels, use circular mode for continuous sampling | "I configured ESP32-S3 DMA to continuously move ADC samples to a circular buffer. The sensor task reads from this buffer without any coordination with the ADC hardware — true zero-copy" | Not hardware | 1kHz vibration sampling | Not hardware | Not directly |
| 3.4 | Sleep Modes and Power | Implement light sleep, deep sleep, measure current in each mode | "I measured SentinelNode's current consumption in each mode: active 82mA, light sleep 14mA, deep sleep 48µA. The duty cycle calculation showed 6.2 months battery life on a 3000mAh cell" | Not hardware | Battery life optimization | Not hardware | Not directly |
| 3.5 | Flash Memory Programming | Read and write STM32/ESP32 flash, implement wear leveling | "I implemented the offline telemetry buffer using SPI flash. When WiFi is unavailable, telemetry is written sequentially to flash with a FIFO pointer. On reconnect, chronological delivery is guaranteed" | Not hardware | Offline buffer, OTA partitions | Not hardware | MemCore firmware stores bug vocabulary in flash |
| 3.6 | Hardware Watchdog | Configure external watchdog, implement FreeRTOS task watchdog | "SentinelNode has an external hardware watchdog fed by a dedicated FreeRTOS task. If any task hangs for 5 seconds, the external watchdog resets the device independent of the MCU — even if the MCU itself is hung" | Not hardware | Production resilience | Not hardware | MemCore monitors its own watchdog |
| 3.7 | JTAG Debugging | Connect hardware debugger, set breakpoints, inspect memory without print statements | "Print statements change interrupt timing and hide race conditions. I debug firmware exclusively with JTAG — I can set a breakpoint inside an ISR, inspect register state, and step through code without affecting timing" | Not hardware | Firmware debugging | Not hardware | MemCore C agent debugged with JTAG |
| 3.8 | Hard Fault Handler | Write a hard fault handler that captures CPU state at crash | "When SentinelNode crashes, my hard fault handler saves program counter, link register, stack pointer, and the last 512 bytes of stack to a reserved flash region. On next boot, this crash report is transmitted to cloud and a GitHub issue is automatically created" | Not hardware | Crash reporting | Not hardware | MemCore captures crash context |

---

## PHASE 4 — RTOS AND FIRMWARE ARCHITECTURE (Days 141–180)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 4.1 | FreeRTOS Task Design | Create tasks with correct priorities, stack sizes, and scheduling behavior | "SentinelNode runs 7 concurrent FreeRTOS tasks. I designed the priority hierarchy so the sensor task (highest) never starves the watchdog task (timer-driven). I documented stack watermarks for all 7 tasks" | Not hardware | Core firmware architecture | Not hardware | MemCore C agent uses task-based architecture |
| 4.2 | FreeRTOS Queues | Build producer-consumer pipelines between tasks | "The sensor task puts raw samples into a queue. The FFT task reads from it. The inference task reads from the FFT output queue. Each task runs independently — if inference is slow, only the queue fills up; sensor reading never stops" | Not hardware | Data pipeline between tasks | Not hardware | MemCore event pipeline |
| 4.3 | FreeRTOS Semaphores and Mutex | Protect shared resources, signal between tasks | "The SPI bus is shared between the ADXL355 driver and the SPI flash driver. Without a mutex, simultaneous access corrupts both transactions. I measured: with mutex, zero corruption across 72 hours" | Not hardware | SPI bus sharing | Not hardware | MemCore shared vocabulary access |
| 4.4 | Stack Overflow Detection | Use watermark API, configure MPU for hard fault on overflow | "I discovered a stack overflow in the OTA task by checking the FreeRTOS stack watermark after 24 hours of operation. Minimum free was 8 bytes. I increased the stack from 2048 to 4096 bytes and re-verified" | Not hardware | Memory safety | Not hardware | MemCore agent stack safety |
| 4.5 | OTA A/B Partition Design | Implement A/B partition scheme with bootloader rollback | "SentinelGrid's OTA system has saved production three times. The most dramatic: a bad firmware update caused 200 nodes to crash-loop. The automatic rollback after 3 failed boots prevented all 200 from bricking. I documented this incident as a postmortem" | Not hardware | Remote firmware updates | Not hardware | MemCore can update itself via OTA |
| 4.6 | Firmware Signing | Sign firmware with RSA key, verify in bootloader | "Every firmware binary is signed by the CI/CD build server with a 2048-bit RSA key. The bootloader verifies the signature before applying any update. A rogue actor who gained S3 access could upload a modified binary — it would be rejected by every node" | Not hardware | Security of OTA | Not hardware | MemCore verifies update signatures |
| 4.7 | CI/CD for Firmware | Build GitHub Actions workflow that compiles, signs, and uploads firmware | "My firmware CI/CD pipeline runs on every push to main: compile for all hardware variants, run unit tests on host, sign binary, upload to S3 with version metadata. A developer pushes code — 8 minutes later it's available for OTA" | Not hardware | Firmware release pipeline | Not hardware | MemCore agent release pipeline |

---

## PHASE 5 — SIGNAL PROCESSING AND EDGE AI (Days 181–240)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 5.1 | Sampling Theory and Nyquist | Calculate minimum sampling rate, explain aliasing | "I chose 1kHz sampling for SentinelGrid because bearing fault frequencies in the motors we monitor reach 450Hz. Nyquist requires at least 900Hz, so 1kHz gives a margin with an anti-aliasing filter at 480Hz" | Not applicable | Core of sensor design | Not applicable | Not directly |
| 5.2 | FFT (Fast Fourier Transform) | Compute FFT in Python and in C using CMSIS-DSP | "I implemented a reference FFT pipeline in Python and then ported it to C using CMSIS-DSP on the ESP32-S3. I verified both produce identical output (within floating point tolerance) on the same input data. The C implementation runs in 12ms" | Not applicable | Vibration analysis | Not applicable | MemCore signal analysis for hardware |
| 5.3 | Feature Extraction from Signals | Extract RMS, kurtosis, spectral energy in frequency bands | "The TFLite model on SentinelNode receives a 15-element feature vector: 5 time-domain features (RMS, kurtosis, peak, crest factor, skewness) and 10 frequency-band energy features. I selected these features by analyzing which correlated most strongly with bearing faults in the training data" | Not applicable | Core of edge AI pipeline | Not applicable | MemCore extracts semantic features from code |
| 5.4 | Digital Filters (IIR, FIR) | Design and implement low-pass filter in firmware | "I designed a 4th-order IIR Butterworth low-pass filter at 480Hz to remove aliasing before 1kHz sampling. Implemented in fixed-point arithmetic on ESP32-S3 — zero floating point operations, maximum performance" | Not applicable | Anti-aliasing | Not applicable | MemCore filters noise from log streams |
| 5.5 | Sensor Fusion | Combine multiple sensor signals for higher-confidence detection | "SentinelGrid's fault classifier achieves 91% accuracy on vibration alone. By fusing vibration + current + temperature, accuracy improves to 96%. The fusion uses a weighted ensemble: if vibration score is 0.8 AND current anomaly is confirmed AND temperature is rising, confidence in fault classification is 0.97" | Not applicable | Multi-sensor anomaly | Not applicable | MemCore fuses multiple signal sources |
| 5.6 | ML for Time Series (Python) | Train LSTM/CNN on time-series data, evaluate, interpret results | "I trained an LSTM autoencoder on 6 weeks of normal motor vibration. The reconstruction error distribution on normal data had mean 0.08 and std 0.02. I set the anomaly threshold at mean + 3*std = 0.14. This gives less than 0.3% false positive rate on validation data" | Traffic anomaly detection | Cloud anomaly model | Incident pattern classification | MemCore bug pattern model |
| 5.7 | Model Quantization (INT8) | Convert float32 model to INT8, measure accuracy and size tradeoff | "Float32 model: 182KB, 95.1% detection rate. INT8 quantized: 46KB, 91.4% detection rate. Size reduction: 4x. Latency reduction: 6.7x on ESP32-S3. I documented this tradeoff in EDGE_AI.md and justified why 91.4% at the edge is acceptable given the cloud model validates all edge detections" | Not directly | Edge model deployment | Not directly | MemCore lightweight local model |
| 5.8 | TFLite for Microcontrollers | Deploy quantized model to ESP32-S3, measure inference latency | "SentinelNode's inference pipeline: FFT 12ms + feature extraction 3ms + INT8 model inference 47ms = 62ms total. A new feature window arrives every 1000ms. The pipeline has 938ms of headroom. I benchmarked this on actual hardware and documented in BENCHMARKS.md" | Not hardware | Core edge intelligence | Not hardware | MemCore embedded reasoning |
| 5.9 | Model OTA (Separate from Firmware) | Implement model update without firmware reboot | "The ML model is stored in a dedicated 256KB flash partition separate from firmware. When SageMaker produces an improved model, it's pushed to all nodes via OTA without disrupting the monitoring loop. Firmware reboot: not required. Monitoring downtime: zero" | Not hardware | AI model deployment | Not hardware | MemCore updates its vocabulary model |

---

## PHASE 6 — DATABASES AND DATA SYSTEMS (Days 241–280)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 6.1 | SQL and PostgreSQL | Design schemas, write complex queries, understand indexes, transactions | "I designed the InfraMesh service registry in PostgreSQL with row-level security so teams cannot see each other's services. The service_id + created_at index makes the service list endpoint return in under 10ms even with 10,000 registered services" | Primary database | Not primary (TimescaleDB used) | Organization config, incidents | Bug history, incident records |
| 6.2 | TimescaleDB | Design time-series schema, use continuous aggregates, set retention policies | "SentinelGrid stores every sensor reading in TimescaleDB. I partitioned the hypertable by 1-week intervals. Before partitioning: query for 30-day anomaly history took 3.2 seconds. After: 45ms. I documented this optimization in CLOUD.md" | Health check history | All telemetry | All engineering events | Not primary |
| 6.3 | Vector Databases (ChromaDB) | Store embeddings, query by semantic similarity | "MemCore stores every past bug as a vector embedding using CodeBERT. When a new error occurs, it retrieves the 5 most semantically similar past bugs — not by keyword match but by meaning. A null pointer exception in a new function retrieves similar null checks from different functions" | Not primary | Not primary | Not primary | Core memory store |
| 6.4 | Graph Databases (Neo4j) | Create nodes and edges, write Cypher queries, traverse graphs | "PulseGrid's blast radius calculator uses a Neo4j graph. When payment-service fails, it traverses all upstream dependencies in 3 hops and weights each by call frequency from trace data. A query that would take 45 SQL joins takes 12ms in Cypher" | Not used | Not used | Core dependency graph | Vocabulary relationship graph |
| 6.5 | Redis | Use as cache and rate limiter | "InfraMesh uses Redis for rate limiting: each service's request count is incremented in Redis with a 1-second TTL. If count exceeds limit, the request is rejected at the edge proxy without touching the backend. 1 million rate-limit checks per second with sub-millisecond latency" | Rate limiting, status cache | Not primary | Risk score cache | Short-term event cache |
| 6.6 | InfluxDB | Write time-series data, query with Flux, set retention | "SentinelGrid's gateway runs local InfluxDB as an offline buffer. During a 4-hour cloud outage, the gateway stored 720,000 sensor readings locally. On reconnect, they were flushed to cloud TimescaleDB in chronological order in under 8 minutes" | Not used | Gateway offline buffer | Not used | Not used |
| 6.7 | Database Indexing and Optimization | Explain indexes, explain plans, optimize slow queries | "I ran EXPLAIN ANALYZE on every PulseGrid query. The incident correlation query was scanning 10 million rows without an index. Adding a composite index on (service_id, timestamp, severity) reduced it from 4.1 seconds to 23ms. I documented this in CLOUD.md with before/after explain plans" | All databases | TimescaleDB time index | All databases | Vector index tuning |

---

## PHASE 7 — WEB APIs AND BACKEND (Days 281–320)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 7.1 | HTTP and REST API Design | Design RESTful APIs with correct methods, status codes, versioning | "I design APIs with explicit versioning (/api/v1/), correct status codes (201 for creation, 202 for async operations, 409 for conflicts), and consistent error response schemas. InfraMesh's API spec is fully documented in Swagger before any code is written" | Core interface | Device management API | Webhook ingestion API | Suggestion delivery API |
| 7.2 | FastAPI Framework | Build async APIs with Pydantic validation, dependency injection, background tasks | "InfraMesh's provisioning API receives 100 concurrent registration requests. FastAPI with asyncio handles all 100 simultaneously. Pydantic rejects malformed requests before they reach the database. Background tasks start the SQS publish without blocking the response" | Core framework | Backend API | Core framework | REST interface |
| 7.3 | Pydantic Validation | Define models with type validation, custom validators, nested models | "Every InfraMesh service registration request is validated by Pydantic before processing. A request with an invalid domain format or missing health check endpoint is rejected with a clear error message. No invalid data reaches the provisioning worker" | Request validation | Device registration | Webhook payload validation | Fix suggestion schema |
| 7.4 | JWT Authentication | Implement JWT issuance and validation, understand claims, expiry | "InfraMesh uses JWT for developer authentication. The JWT claim includes team_id, which is used for row-level security in PostgreSQL — a developer from team-payments cannot accidentally see or modify team-analytics services" | Developer auth | Not applicable | Dashboard auth | Developer API auth |
| 7.5 | OAuth2 | Implement OAuth2 authorization code flow | "PulseGrid uses GitHub OAuth2 for authentication. When a developer logs in with GitHub, PulseGrid receives a token with access to their repositories — the same access it needs to post risk score comments on their PRs" | Not used | Not used | GitHub integration auth | Not applicable |
| 7.6 | WebSockets | Implement real-time bidirectional communication | "PulseGrid's dependency graph dashboard updates in real time as new traces arrive. WebSocket connection from browser to FastAPI backend receives graph update events as they are processed. No polling required" | Dashboard real-time | Dashboard real-time | Core real-time feature | Real-time suggestions |
| 7.7 | API Documentation (Swagger/OpenAPI) | Write complete API documentation that serves as a contract | "Every API I build has Swagger documentation generated automatically by FastAPI. The documentation includes example requests and responses, error codes, and authentication requirements. Any developer can test the API from the Swagger UI without reading the source code" | Complete API docs | Device management API | Webhook API docs | SDK documentation |

---

## PHASE 8 — MESSAGE QUEUES AND ASYNC SYSTEMS (Days 321–360)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 8.1 | Why Async/Queue Systems Exist | Explain why synchronous processing fails at scale | "Without a queue, InfraMesh's API would block for 30 seconds on each provisioning request. With SQS, the API responds in 50ms and the worker handles provisioning asynchronously. This allows 100 concurrent registrations without any API timeout" | Core pattern | Gateway buffer | Core event stream | Async fix generation |
| 8.2 | AWS SQS | Configure queues, dead letter queues, visibility timeout, message attributes | "InfraMesh's SQS dead letter queue captures provisioning tasks that failed after 3 retries. A daily Lambda function inspects the DLQ, sends an alert, and retries with exponential backoff. Zero provisioning requests are silently lost" | Core queue | Not primary | Not used | Task queue |
| 8.3 | MQTT Protocol | Configure broker, publish/subscribe, design topic hierarchy, understand QoS levels | "I designed SentinelGrid's MQTT topic hierarchy: sentinel/node/{id}/telemetry for sensor data, sentinel/node/{id}/alert for anomaly alerts, sentinel/node/{id}/health for device health. QoS 1 guarantees no telemetry is lost even during brief WiFi interruptions" | Not primary | Core IoT protocol | Not used | Not primary |
| 8.4 | Apache Kafka | Configure topics, partitions, consumer groups, offset management | "PulseGrid's Kafka has 6 topics, each partitioned by organization_id. This means all events from one organization are processed by one consumer, guaranteeing in-order processing per organization. The risk model always sees events in the correct temporal order" | Not used | Not used | Core event stream | Not primary |
| 8.5 | Store-and-Forward Pattern | Implement local buffering with guaranteed delivery on reconnect | "SentinelGrid nodes use SPI flash as a store-and-forward buffer. During a 4-hour network outage, 14,400 telemetry messages were buffered. On reconnect, they were delivered in chronological order with no gaps. I verified this by checking the TimescaleDB timestamp sequence after reconnect" | Not primary | Core resilience pattern | Not used | MemCore buffers when LLM is unavailable |
| 8.6 | Dead Letter Queues | Design DLQ pattern, implement retry logic, monitor failure rates | "Every queue in every project has a DLQ. PulseGrid's webhook ingestion DLQ catches malformed events. InfraMesh's provisioning DLQ catches failed AWS API calls. SentinelGrid's telemetry DLQ catches messages the stream processor cannot parse" | Provisioning failures | Telemetry parse failures | Webhook parse failures | Failed fix attempts |
| 8.7 | Event-Driven Architecture | Design systems where components communicate through events, not direct calls | "PulseGrid is fully event-driven. GitHub sends a webhook event → Kafka topic → stream processor updates Neo4j graph → risk scorer reads new graph → posts comment to GitHub. No component calls another directly. This means any component can be replaced without changing others" | Partial | Partial | Core architecture | Core architecture |

---

## PHASE 9 — CLOUD AND DEVOPS (Days 361–420)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 9.1 | AWS Core Services (EC2, S3, IAM) | Launch EC2, configure S3 buckets, design IAM roles with least privilege | "I follow least-privilege IAM. SentinelGrid's Lambda function has exactly one permission: write to the specific TimescaleDB RDS instance. Nothing else. A compromised Lambda cannot access S3, SQS, or any other service" | EC2, S3, IAM | EC2, S3, IAM | EC2, S3, IAM | EC2, S3, IAM |
| 9.2 | AWS IoT Core | Register devices, manage certificates, configure IoT Rules | "AWS IoT Core handles 10,000 simultaneous SentinelNode connections. Each node has a unique X.509 certificate provisioned at manufacturing time. A node without a valid certificate cannot connect — preventing rogue devices from injecting fake sensor data" | Not primary | Core cloud IoT | Not used | Not directly |
| 9.3 | AWS Kinesis | Configure streams, set shard count based on throughput, implement consumer | "SentinelGrid's Kinesis stream has 10 shards, each handling 1MB/second. At 10,000 nodes sending 50-byte messages every 5 seconds, peak throughput is 100KB/second — well within capacity. I provisioned with 10x headroom for burst traffic" | Not used | Core ingestion | Not used | Not directly |
| 9.4 | AWS Lambda | Write Lambda functions, configure triggers, manage cold start | "PulseGrid's incident correlation Lambda runs within 300ms of a PagerDuty webhook. Cold start is under 800ms because I use Lambda SnapStart. The function queries TimescaleDB for the preceding 2 hours of events and enriches the incident record" | Not primary | Telemetry processing | Incident correlation | Not primary |
| 9.5 | Docker | Write Dockerfiles, build images, understand layers, push to ECR | "Every service in all four projects runs in Docker. I write multi-stage Dockerfiles: builder stage installs dependencies, final stage copies only what's needed. The FastAPI image is 180MB instead of 1.2GB. Any developer can run the full stack with one docker-compose up command" | All services | Gateway + backend services | All services | SDK runs in Docker |
| 9.6 | Docker Compose | Write docker-compose.yml for local development with all dependencies | "Every project has a docker-compose.yml that brings up the complete local stack: database, cache, queue simulator, API, and worker. A new developer runs git clone + docker-compose up and has a working system in under 5 minutes" | Full local stack | Gateway + cloud sim | Full local stack | Full local stack |
| 9.7 | Terraform | Write .tf files for all AWS resources, use modules, manage state | "SentinelGrid's entire AWS infrastructure is defined in Terraform: IoT Core policies, Kinesis streams, Lambda functions, RDS instance, S3 buckets, CloudFront distribution, IAM roles. If the AWS account is lost, I run terraform apply and everything is recreated in 12 minutes" | All AWS resources | All AWS resources | All AWS resources | Not primary |
| 9.8 | GitHub Actions (CI/CD) | Write workflows for build, test, deploy pipelines | "PulseGrid deploys itself through its own CI/CD pipeline — a form of dogfooding that immediately reveals if the pipeline is broken. On push to main: run tests, build Docker image, push to ECR, update ECS service. Deployment takes 4 minutes" | Code + infra deploy | Firmware CI/CD | Full CI/CD | SDK release pipeline |
| 9.9 | Kubernetes Basics | Understand pods, services, deployments, why K8s exists | "I understand when Kubernetes is and is not the right choice. PulseGrid uses ECS because it has 8 services and ECS is simpler to operate. A system with 50+ services and complex networking requirements would warrant Kubernetes. I documented this decision in ADR/004" | ECS used | Not used | ECS used | Not primary |

---

## PHASE 10 — OBSERVABILITY (Days 421–450)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 10.1 | Structured Logging | Write JSON-format logs with consistent fields | "I write logs as JSON: {level, timestamp, service, function, event, duration_ms, error}. When I search CloudWatch for all errors in the payment provisioning flow in the last hour, I get exactly those records in under 1 second because every log has the same schema" | All services | All firmware tasks | All services | All MemCore components |
| 10.2 | Prometheus Metrics | Expose metrics endpoint, define counters/gauges/histograms | "Every FastAPI service exposes /metrics. InfraMesh tracks: provisioning_requests_total, provisioning_duration_seconds (histogram), queue_depth_current, health_check_failure_rate. When provisioning_duration_seconds p99 exceeds 45 seconds, an alert fires before any developer notices" | All services | Not firmware (logs used) | All services | SDK metrics |
| 10.3 | Grafana Dashboards | Build dashboards from TimescaleDB/Prometheus data sources | "I built separate Grafana dashboards for each audience: operations team (service health), engineering team (DORA metrics and deployment risk), management (cost attribution and reliability trends). Each dashboard tells a different story from the same underlying data" | Service health | Fleet health + machine health | Engineering intelligence | Debugging activity |
| 10.4 | Distributed Tracing (OpenTelemetry) | Instrument services with traces, visualize in Jaeger | "PulseGrid ingests OpenTelemetry traces from customer services to build the dependency graph. But PulseGrid itself is also instrumented with OpenTelemetry — so I can trace a single GitHub webhook event as it flows through Kafka, the stream processor, the risk scorer, and back to GitHub as a PR comment" | Partial | Not firmware | Core data source + self-instrumented | Traces through fix generation |
| 10.5 | Alert Design | Write meaningful alerts that are actionable and not noisy | "I follow the SRE alert design principle: only alert when a human needs to take action. SentinelGrid has 4 alerts: anomaly score above 0.8 for 10+ minutes (maintenance needed), node offline for 4+ hours (network or power issue), heap free below 20KB (memory leak developing), OTA failure rate above 5% (bad firmware). All others are dashboard information only" | 3 alert rules | 4 alert rules | 5 alert rules | 2 alert rules |
| 10.6 | Postmortem Writing | Write structured postmortem with timeline, root cause, action items | "I have written 4 postmortems across the projects I built. The OTA crash loop postmortem for SentinelGrid is the most detailed — it includes a 10-minute timeline, the root cause (WiFi reconnect timing bug), the contributing factor (no staged rollout), and 3 corrective actions with owners and deadlines" | Service failure postmortems | OTA crash loop postmortem | Deployment incident postmortems | Fix failure postmortems |
| 10.7 | Runbook Creation | Write step-by-step on-call procedures | "Every alert in every project has a corresponding runbook. The runbook tells the on-call engineer: what the alert means, what to check first (link to specific Grafana panel), what to check second, what to do to mitigate, how to escalate. A junior engineer should be able to follow it at 3 AM" | 3 runbooks | 5 runbooks | 4 runbooks | 2 runbooks |

---

## PHASE 11 — AI AND INTELLIGENCE LAYER (Days 451–510)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 11.1 | Vector Embeddings | Understand what embeddings are, how semantic search works | "MemCore converts every bug report into a 768-dimensional vector using CodeBERT. When a new bug arrives, it computes cosine similarity between the new bug vector and all stored bug vectors. The top 5 matches are retrieved and included in the LLM context — not by keyword, but by meaning" | Not primary | Not primary | Not primary | Core memory mechanism |
| 11.2 | RAG (Retrieval Augmented Generation) | Build a pipeline that retrieves relevant context before calling LLM | "PulseGrid's postmortem generator uses RAG: given an incident, it retrieves the 3 most similar past incidents from vector memory, the deployment diff, the error pattern, and the metric anomaly. This structured context is passed to the LLM. The output cites specific past incidents — it cannot hallucinate because every fact comes from a retrieved document" | Traffic explanation | Failure explanation | Core postmortem feature | Core debugging feature |
| 11.3 | LLM Integration (Claude/GPT API) | Call LLM APIs, design prompts, handle rate limits, parse responses | "I spent 2 weeks on prompt engineering for PulseGrid's postmortem generator. The prompt is a structured template with 8 slots: incident timeline, deployment diff, similar past incidents, affected services, error pattern, metric anomaly, team context, output format. The structure prevents hallucination by constraining the LLM to reason only over provided facts" | Not primary | Not primary | Core feature | Core reasoning engine |
| 11.4 | Prompt Engineering | Design prompts that produce consistent, accurate, structured output | "I use chain-of-thought prompting for MemCore's fix suggestions: the prompt asks the LLM to first identify the error type, then recall the function's contract, then identify the contract violation, then suggest a fix. This structured reasoning produces more accurate fixes than asking for a fix directly" | Not primary | Not primary | Postmortem generation | Fix suggestion generation |
| 11.5 | ML Model Training Pipeline | Build end-to-end pipeline from data collection to model deployment | "SentinelGrid's cloud retraining pipeline runs weekly: query 14 days of telemetry from TimescaleDB, compute features, label as normal/anomaly based on confirmed incidents, train LSTM autoencoder, evaluate on holdout set, if improvement > 2%, export to TFLite, quantize to INT8, upload to S3, push to nodes via model OTA" | Traffic anomaly model | Machine anomaly model | Risk classifier model | Bug pattern model |
| 11.6 | XGBoost / Gradient Boosting | Train and evaluate gradient boosted classifiers | "PulseGrid's risk scorer uses XGBoost trained on 18 months of the organization's deployment and incident history. Features: 23 PR attributes, 8 deployment context signals, 12 historical signals. XGBoost outperformed logistic regression (0.79 AUC vs 0.71) and random forest (0.82 vs 0.79) on cross-validation" | Not primary | Not primary | Core risk model | Bug priority classification |
| 11.7 | Model Monitoring and Drift Detection | Monitor model accuracy over time, detect when model needs retraining | "SentinelGrid's edge model is monitored for drift by comparing its anomaly scores to the cloud model's scores on the same data. If they diverge by more than 15% consistently, a retraining trigger fires. After 3 months, when a factory upgraded to new bearings, the drift detector fired and retraining completed before any false alarms accumulated" | Traffic baseline drift | Machine anomaly drift | Risk model drift | Bug vocabulary drift |

---

## PHASE 12 — PCB DESIGN AND MANUFACTURING (Days 511–570)

*(SentinelGrid and MemCore hardware only — InfraMesh and PulseGrid skip this phase)*

| # | Skill | Outcome After Learning | Interview Statement | SentinelGrid | MemCore |
|---|-------|----------------------|--------------------|----|-----|
| 12.1 | KiCad Schematic | Design complete schematic with all components and connections | "I designed the SentinelNode schematic from scratch: ESP32-S3, 5 sensors, power management, wireless modules, protection circuits. Every component was selected by reading its datasheet, not by following a tutorial" | Complete PCB | Optional hardware version |
| 12.2 | PCB Layout | Route a 4-layer PCB with proper ground planes and signal integrity | "SentinelNode revision 1 had EMI problems — ADC noise matched the switching regulator frequency. Revision 2 separated analog and digital ground planes, added LC filter, moved the regulator away from the sensor interface. ADC noise floor improved by 18dB" | Production hardware | Optional |
| 12.3 | EMC Design | Design for CE/FCC certification from the beginning | "I brought an EMC consultant into the PCB design phase for revision 3. We pre-tested with a near-field probe before going to an accredited lab. Passed CE certification on first attempt, saving 6 weeks of redesign" | CE certification | Optional |
| 12.4 | Manufacturing Test (ICT) | Design test jig and self-test firmware for production testing | "SentinelNode's manufacturing test: bed-of-nails fixture powers the board, self-test firmware exercises every peripheral (SPI flash read/write, I2C sensor register check, ADC linearity, WiFi scan, LoRa register), logs pass/fail per peripheral, prints result in under 30 seconds" | Production scale | Optional |

---

## PHASE 13 — SYSTEM DESIGN AND ARCHITECTURE (Days 571–600)

| # | Skill | Outcome After Learning | Interview Statement | InfraMesh | SentinelGrid | PulseGrid | MemCore |
|---|-------|----------------------|--------------------|-----------|--------------|-----------| -------|
| 13.1 | Architecture Decision Records | Document why every major technical decision was made | "Every project has an ADR/ folder. ADR/003-why-mqtt-qos1.md explains: we chose QoS 1 over QoS 0 because in a factory with intermittent WiFi, dropped telemetry during a failure event is unacceptable. QoS 0 dropped 2.3% of messages in our load test. QoS 1 dropped 0%" | ADR folder | ADR folder | ADR folder | ADR folder |
| 13.2 | Scaling Design | Design for 10x current load, identify bottlenecks before they appear | "When I load tested InfraMesh with k6 at 10x expected load, the PostgreSQL connection pool exhausted at 800 concurrent requests. I increased the pool and added PgBouncer. The bottleneck moved to the SQS worker throughput. I documented the bottleneck sequence in SCALING.md" | Scaling analysis | Fleet scaling | Event stream scaling | Memory scaling |
| 13.3 | Security Design | Design authentication, authorization, encryption, audit trails | "Every project follows the same security principles: TLS everywhere, least-privilege IAM, JWT with team-scoped claims, audit log for all state changes, no secrets in code (all in Secrets Manager). I run OWASP ZAP against every public API before launch" | Full security design | Device security | Webhook security | Fix application audit |
| 13.4 | Multi-Tenancy Design | Isolate data between tenants at database and application level | "InfraMesh uses PostgreSQL row-level security: every table has a team_id column and a row-level policy that filters automatically based on the JWT claim. A developer from team-payments cannot even accidentally query team-analytics data — the database enforces it, not the application" | Row-level security | Zone isolation | Organization isolation | Team isolation |

# MASTER ROADMAP — DAILY TIMETABLE
## Part 2: Day-by-Day Plan | Practice Sites | Documentation | Mental Picture
## Days 1–90 (Phase 0 + Phase 1 + Phase 2 Start)

---

# HOW EACH DAY IS STRUCTURED

Every day has 4 blocks:
- **MORNING (2 hours)** — Theory and concept understanding
- **AFTERNOON (2 hours)** — Hands-on practice on the specific site
- **EVENING (1 hour)** — Documentation and reflection
- **END OF DAY** — Mental picture check and connection to projects

**Documentation Rule:** Every evening, open your GitHub repository and commit one file. Even if it is just a paragraph. The commit history is your proof.

**Practice Rule:** Do not copy-paste code. Type everything by hand. Understand every line before moving to the next.

---

# PHASE 0 — MENTAL FOUNDATIONS
## Days 1–14

---

### DAY 1
**Topic:** How the Internet Works — DNS and HTTP
**Subtopics:** DNS resolution, IP addresses, TCP handshake, HTTP request/response cycle

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: "How DNS Works" — dnsimple.com/dns (comic format, very clear) | dnsimple.com/support/articles/dns-defined |
| MORNING | Read: "HTTP Fundamentals" — MDN Web Docs | developer.mozilla.org/en-US/docs/Web/HTTP/Overview |
| AFTERNOON | Practice: Open browser DevTools → Network tab → load any website → trace every request. Identify: DNS lookup time, TCP connect time, Time to First Byte | Any website |
| AFTERNOON | Practice: On Linux terminal, run `dig google.com` and `curl -v https://google.com`. Read every line of the output | Linux terminal |
| EVENING | Document: Create `mental-models/01-internet.md` in GitHub. Write: "DNS converts domain names to IP addresses. HTTP is the language browsers and servers use. TCP ensures packets arrive in order." Draw the flow: Browser → DNS → Server → Response | GitHub |

**End of Day Mental Picture:**
You should be able to close your eyes and trace: User types URL → Browser asks DNS server for IP → DNS returns IP → Browser opens TCP connection to that IP → Browser sends HTTP GET request → Server sends HTTP response with HTML → Browser renders page. This happens every time anyone uses any of your four projects.

**Connection to Projects:**
- InfraMesh: When a developer registers a service, InfraMesh creates a DNS record. Now you know what that means.
- SentinelGrid: MQTT runs over TCP. Now you know what TCP is.
- PulseGrid: GitHub sends HTTP webhooks. Now you know what HTTP is.
- MemCore: Calls LLM API over HTTPS. Now you know the protocol.

---

### DAY 2
**Topic:** How the Internet Works — Load Balancers and Proxies
**Subtopics:** What a proxy does, forward vs reverse proxy, load balancing algorithms, health checks

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: "What is a reverse proxy?" — nginx.com/resources/glossary | nginx.com/resources/glossary/reverse-proxy-server |
| MORNING | Read: "Load Balancing Algorithms" — AWS docs on ALB | docs.aws.amazon.com/elasticloadbalancing/latest/application/introduction |
| AFTERNOON | Practice: Install nginx locally with brew or apt. Configure it as a reverse proxy to a simple Python http.server. Test with curl | nginx + Python |
| AFTERNOON | Practice: Add a health check endpoint to the Python server. Watch nginx mark the upstream as healthy/unhealthy when you stop/start the Python server | nginx + Python |
| EVENING | Document: `mental-models/02-proxies.md`. Write: "A reverse proxy sits in front of services. Clients talk to the proxy, not the service. Benefits: hide service locations, load balance, add auth, rate limit. InfraMesh configures an ALB (AWS load balancer) for every registered service." | GitHub |

**End of Day Mental Picture:**
A load balancer receives a request, decides which of 3 backend servers to send it to (round-robin or least-connections), forwards the request, receives the response, and returns it to the client. If a server fails its health check, the load balancer stops sending it traffic. This is the fundamental mechanism InfraMesh automates.

---

### DAY 3
**Topic:** Linux Command Line — Navigation and Files
**Subtopics:** Filesystem hierarchy, navigation commands, file operations, permissions

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Tutorial: OverTheWire Bandit levels 0–5 | overthewire.org/wargames/bandit |
| AFTERNOON | Practice: OverTheWire Bandit levels 6–12 | overthewire.org/wargames/bandit |
| EVENING | Document: `linux-learning/bandit-levels.md`. For each level completed, write: what the challenge was, what command you used, what you learned. Screenshot the final password for each level. | GitHub |

**End of Day Mental Picture:**
You can open a terminal and feel comfortable. You know: `ls` lists files, `cd` changes directory, `cat` reads files, `grep` searches inside files, `chmod` changes permissions. More importantly: on a production server at 2 AM during an incident, this terminal is your only window into what is happening.

---

### DAY 4
**Topic:** Linux Command Line — Processes and Networking
**Subtopics:** Process management, ps, kill, netstat, curl, SSH

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Tutorial: OverTheWire Bandit levels 13–20 | overthewire.org/wargames/bandit |
| AFTERNOON | Practice: Run a Python HTTP server. Use `ps aux | grep python` to find it. Use `netstat -tlnp` to see what port it is on. Use `curl` to call it. Kill it with `kill -9`. | Linux terminal |
| AFTERNOON | Practice: SSH into any Linux machine (use a free EC2 t2.micro on AWS Free Tier if you have no other option). Navigate the filesystem. Read /etc/os-release, /proc/meminfo, /proc/cpuinfo | AWS Free Tier or Linux VM |
| EVENING | Document: `linux-learning/process-networking.md`. Write: "Every running program is a process with a PID. `ps aux` shows all processes. `kill -9 PID` force-stops a process. `netstat -tlnp` shows which process is listening on which port. This is how I debug: 'Why is port 8080 already in use?'" | GitHub |

**End of Day Mental Picture:**
When SentinelGrid's gateway MQTT broker stops working, you SSH into the Raspberry Pi and type `ps aux | grep mosquitto` to see if it's running, `netstat -tlnp | grep 1883` to see if the port is listening, `cat /var/log/mosquitto/mosquitto.log` to read why it stopped.

---

### DAY 5
**Topic:** Git and GitHub — Core Workflow
**Subtopics:** init, clone, add, commit, push, pull, status, log, diff

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Interactive tutorial: learngitbranching.js.org — complete "Introduction Sequence" (levels 1–4) | learngitbranching.js.org |
| AFTERNOON | Practice: Create a real GitHub repository called `learning-journal`. Add a README. Make 5 commits with meaningful messages (not "update" or "fix"). Each commit should document one thing you learned today | GitHub |
| AFTERNOON | Practice: learngitbranching.js.org — complete "Ramping Up" (levels 1–4) | learngitbranching.js.org |
| EVENING | Document: `learning-journal/git-workflow.md`. Write: "Every skill I learn is committed here. Commits should read like a story: 'Add DNS explanation to mental models', 'Discover netstat shows bound ports not connected ports'. Future me (or a future employer) should be able to read this commit history and understand my learning" | GitHub |

**End of Day Mental Picture:**
Git tracks every change to every file. Each commit is a snapshot. Branches let you work on features without affecting the main code. Pull requests let others review your changes. Every project (InfraMesh, SentinelGrid, PulseGrid, MemCore) lives in Git — including firmware, Terraform, ML pipelines, and documentation.

---

### DAY 6
**Topic:** Git — Branching, Merging, and Collaboration
**Subtopics:** branch, checkout, merge, rebase, conflict resolution, pull requests

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Interactive tutorial: learngitbranching.js.org — complete "Moving Work Around" | learngitbranching.js.org |
| AFTERNOON | Practice: Create a branch called `feature/git-practice`. Make 3 commits on it. Create a PR on GitHub. Review it. Merge it. Delete the branch. Practice the exact workflow you will use every day in all projects | GitHub |
| AFTERNOON | Practice: Simulate a merge conflict: change the same line in two branches, try to merge. Resolve the conflict manually by editing the file. Commit the resolution | GitHub |
| EVENING | Document: `learning-journal/git-branching.md`. Write the branching strategy you will follow for all projects: main branch (always deployable), feature branches (one feature per branch), PR required for merge, meaningful commit messages | GitHub |

---

### DAY 7
**Topic:** Systems Thinking — How Systems Fail
**Subtopics:** Single point of failure, cascading failures, graceful degradation, circuit breaker, timeout

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: Google's SRE book Chapter 3 "Embracing Risk" (free online) | sre.google/sre-book/embracing-risk |
| MORNING | Read: Netflix Tech Blog "5 Lessons Learned from Netflix's Chaos Monkey" | netflixtechblog.com (search "Chaos Monkey") |
| AFTERNOON | Practice: Draw (on paper or excalidraw.com) the failure modes for each project. For InfraMesh: what fails if SQS is down? If PostgreSQL is down? If the worker crashes? For SentinelGrid: what fails if WiFi is down? If the gateway crashes? | excalidraw.com |
| EVENING | Document: `mental-models/03-failure-modes.md`. For each of the four projects, list 3 failure scenarios with what the user experiences and how the system should degrade gracefully | GitHub |

**End of Day Mental Picture:**
Every system will fail. The question is not whether but when and how. A well-designed system fails gracefully: SentinelGrid without WiFi still detects anomalies locally. InfraMesh without SQS returns an error rather than hanging for 30 seconds. PulseGrid without the LLM API still scores risk from the ML model. MemCore without the vector DB still shows the raw error.

---

### DAYS 8–10: REST AND BUFFER
**Use these 3 days to:**
- Re-read everything from Days 1–7
- Complete any incomplete practice from those days
- Start drawing the master architecture diagram on excalidraw.com
- Write `ARCHITECTURE.md` in your main GitHub repository with your current understanding of all 4 projects

---

### DAY 11
**Topic:** How Computers Work — Memory and CPU
**Subtopics:** Stack vs heap, CPU registers, process memory layout, what the OS manages

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Interactive: pythontutor.com — run simple Python programs and watch the stack/heap visualization. Run a recursive function. Watch the stack grow and shrink | pythontutor.com |
| AFTERNOON | Read: CS50 Week 4 lecture notes on memory (free) | cs50.harvard.edu/x — Week 4 Memory |
| AFTERNOON | Practice: Write a Python function that recursively calls itself with no base case. Watch it throw RecursionError (stack overflow). Now write one with a base case. Understand why the first fails | Python REPL |
| EVENING | Document: `mental-models/04-memory.md`. Write: "The stack stores function calls and local variables. It grows as functions call each other and shrinks as they return. FreeRTOS gives each task its own stack — that is why stack overflow is a real firmware problem. The heap is where dynamically allocated memory goes — that is why memory leaks cause heap exhaustion" | GitHub |

---

### DAYS 12–14: PROJECT ARCHITECTURE MAPPING
**Use these 3 days to:**

**Day 12:** Create architecture diagrams for all 4 projects in excalidraw.com. Export as PNG and commit to GitHub.

**Day 13:** Read all previous documents in this series:
- atlassian_skills_master_roadmap.md
- hardware_ai_fresher_complete_roadmap.md
- pulsegrid_original_project.md
- embedded_ai_connection_map.md

**Day 14:** Write `MASTER_PLAN.md` in your main GitHub repository. Include:
- Your learning goal (one sentence)
- The four projects and what problem each solves
- The master architecture diagram (link to excalidraw)
- Your start date and target date for each phase

---

# PHASE 1 — PROGRAMMING FOUNDATIONS
## Days 15–60

---

### DAY 15
**Topic:** Python Core — Variables, Data Types, Operators
**Subtopics:** int, float, str, bool, list, dict, type() function, arithmetic and comparison operators

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: docs.python.org/3/tutorial/introduction.html (official Python tutorial, Chapter 3) | docs.python.org/3/tutorial |
| AFTERNOON | Practice: HackerRank Python (Easy) — complete "Python If-Else", "Arithmetic Operators", "Python: Division" | hackerrank.com/domains/python |
| AFTERNOON | Practice: Exercism Python track — complete "Hello World" and "Two Fer" | exercism.org/tracks/python |
| EVENING | Document: `python-learning/day15-basics.md`. Write: "In InfraMesh, service configuration is stored as a Python dict: `{name: str, domain: str, port: int, public: bool}`. Pydantic validates these types before the data reaches the database. Understanding Python types is the foundation of this validation" | GitHub |

**Project Connection:**
```python
# This is InfraMesh's service registration — Python types you learned today
service = {
    "name": "payment-service",      # str
    "domain": "payment.company.com", # str
    "port": 8080,                    # int
    "public": False,                 # bool
    "health_check": "/health"        # str
}
```

---

### DAY 16
**Topic:** Python Core — Control Flow
**Subtopics:** if/elif/else, for loops, while loops, break, continue, range()

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: docs.python.org/3/tutorial/controlflow.html | docs.python.org/3/tutorial |
| AFTERNOON | Practice: HackerRank Python — complete "Python: Print Function", "Loops", "Write a function" | hackerrank.com/domains/python |
| AFTERNOON | Practice: LeetCode Easy — "Two Sum" (problem 1) and "FizzBuzz" (problem 412) — focus on understanding loops | leetcode.com |
| EVENING | Document: `python-learning/day16-control-flow.md`. Write how control flow is used in each project: "InfraMesh worker loops over SQS messages: `for message in queue.receive()`. SentinelGrid gateway loops over MQTT messages: `while True: msg = broker.receive()`. PulseGrid stream processor loops over Kafka events: `for event in consumer.poll()`" | GitHub |

---

### DAY 17
**Topic:** Python Core — Functions and Scope
**Subtopics:** def, return, arguments, default arguments, *args, **kwargs, local vs global scope

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: docs.python.org/3/tutorial/controlflow.html#defining-functions | docs.python.org/3/tutorial |
| AFTERNOON | Practice: Exercism Python — complete "Resistor Color", "Bob", "Space Age" | exercism.org/tracks/python |
| AFTERNOON | Practice: Write a Python function `calculate_risk_score(pr_size, reviewer_count, files_changed, historical_incident_rate)` that returns a float between 0 and 100. No ML yet — use a weighted formula. This is a simplified version of PulseGrid's risk scorer | Python file, commit to GitHub |
| EVENING | Document: `python-learning/day17-functions.md`. Write the function you created. Explain: "A function is a named, reusable block of logic. MemCore's vocabulary engine is a class with functions: `build_vocabulary()`, `detect_drift()`, `retrieve_similar_bugs()`. Each function has one job" | GitHub |

---

### DAY 18
**Topic:** Python Core — Lists and Dicts (Deep)
**Subtopics:** List comprehensions, dict methods, sorting, filtering, nested data structures

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: realpython.com/python-lists-tuples and realpython.com/python-dicts | realpython.com |
| AFTERNOON | Practice: HackerRank Python — "List Comprehensions", "Find the Runner-Up Score!", "Nested Lists" | hackerrank.com/domains/python |
| AFTERNOON | Practice: Write a Python script that processes a list of 10 SentinelGrid telemetry readings (dicts with keys: node_id, timestamp, vibration_rms, anomaly_score). Filter to only anomalous readings (score > 0.7). Sort by anomaly_score descending. Print the top 3 | Python file, commit to GitHub |
| EVENING | Document: `python-learning/day18-data-structures.md`. Include your telemetry processing script. Write: "SentinelGrid's stream processor receives telemetry as a list of dicts. It filters anomalies with list comprehension: `anomalies = [r for r in readings if r['anomaly_score'] > 0.7]`. This is production code" | GitHub |

---

### DAY 19
**Topic:** Python Core — Error Handling
**Subtopics:** try/except/finally, custom exceptions, raising exceptions, context managers (with)

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: docs.python.org/3/tutorial/errors.html | docs.python.org/3/tutorial |
| AFTERNOON | Practice: Exercism Python — "Grains", "Hamming", "Raindrops" (these require error handling) | exercism.org/tracks/python |
| AFTERNOON | Practice: Rewrite your Day 18 script with proper error handling: what if a reading is missing the anomaly_score key? What if the timestamp is malformed? Write a custom exception `InvalidTelemetryError`. Use `try/except` to catch it and log a structured error | Python file, commit to GitHub |
| EVENING | Document: `python-learning/day19-error-handling.md`. Write: "In production, every external call can fail: database queries, API calls, file reads. The InfraMesh worker wraps every AWS API call in try/except. If Route53 returns a throttling error, the worker catches it, waits 5 seconds (exponential backoff), and retries. Unhandled exceptions crash the worker — SQS messages go to the dead letter queue" | GitHub |

---

### DAYS 20–25: Python OOP and Modules

**Day 20:** Classes and objects (realpython.com/python3-object-oriented-programming)
- Practice: HackerRank OOP challenges
- Build: `ServiceRegistry` class with methods `register()`, `get_status()`, `deregister()`
- Document: How InfraMesh's service registry is a class

**Day 21:** Inheritance and composition
- Practice: Exercism Python — "Simple Linked List", "Clock"
- Build: `SentinelNode` class that extends a base `Device` class
- Document: SentinelGrid's device hierarchy

**Day 22:** Python modules and packages
- Practice: Create a Python package structure for InfraMesh: `inframesh/api/`, `inframesh/worker/`, `inframesh/models/`
- Build: Import between modules, understand `__init__.py`
- Document: How professional Python projects are structured

**Day 23:** File I/O and JSON
- Practice: Read and write JSON files (telemetry data simulation)
- Build: A script that reads SentinelGrid telemetry from a JSON file, processes it, writes anomalies to a new JSON file
- Document: JSON is the universal data format across all four projects

**Day 24:** Python standard library (datetime, os, logging, pathlib)
- Practice: Implement structured logging with Python's `logging` module
- Build: Add logging to your Day 22 InfraMesh package
- Document: Structured logging standards

**Day 25:** REST AND REVIEW
- Review Days 15–24
- Commit all pending documentation
- Update `MASTER_PLAN.md` with progress

---

### DAYS 26–35: Python Async and HTTP

**Day 26:** Async programming concepts
- Read: realpython.com/async-io-python
- Build: A simple async Python script that "fetches" 5 telemetry readings concurrently
- Document: Why InfraMesh's API must be async

**Day 27:** FastAPI introduction
- Tutorial: fastapi.tiangolo.com — "First Steps" and "Path Parameters"
- Build: First InfraMesh endpoint: `GET /health` returns `{"status": "ok"}`
- Document: Your first API endpoint

**Day 28:** FastAPI — POST requests and Pydantic
- Tutorial: fastapi.tiangolo.com — "Request Body" and "Data Validation"
- Build: `POST /api/v1/services` endpoint with Pydantic model validation
- Document: Pydantic schema for InfraMesh service registration

**Day 29:** FastAPI — Response models and error handling
- Build: Add proper HTTP status codes (201 for creation, 422 for validation error, 500 for server error)
- Practice: Test your API with Postman — save all requests as a Postman collection in GitHub
- Document: Postman collection as API documentation

**Day 30:** HTTP Requests with Python (calling external APIs)
- Read: realpython.com/python-requests
- Build: A Python script that calls a public API (OpenWeatherMap or similar). Add error handling for timeout, 404, 500
- Practice: HackerRank API challenges
- Document: How MemCore calls the LLM API

---

### DAYS 31–45: C Programming (for SentinelGrid and MemCore)

**Day 31:** C fundamentals — compilation, variables, types
- Resource: CS50 Week 1 (cs50.harvard.edu/x) — Week 1 is in C
- Practice: Write and compile your first C program: read an ADC value (simulated as user input) and print it
- Document: Why firmware is in C, not Python

**Day 32:** C — Functions, arrays, strings
- Practice: CS50 Problem Set 1
- Build: A C function `float calculate_rms(float* samples, int count)` that takes an array of vibration samples and returns RMS value
- Document: This exact function runs in SentinelGrid's signal processing task

**Day 33:** C — Pointers (critical for embedded)
- Resource: CS50 Week 4 (Memory section)
- Practice: Write programs that use pointers to modify values, traverse arrays
- Build: Rewrite calculate_rms to accept pointer instead of array. Understand they are the same
- Document: "Pointers are how embedded C accesses hardware registers: `*(uint32_t*)0x40020018 = 0x01` writes directly to a GPIO register"

**Day 34:** C — Structs and Bit Fields
- Practice: Define a C struct that mirrors the ADXL355 status register (8 bits with specific field meanings)
- Build: A C function that reads this struct and returns a human-readable status string
- Document: "Every sensor register is a C struct in firmware. Without structs, you would manually shift and mask every bit. With structs, the compiler does it"

**Day 35:** C — Memory (malloc, free, stack vs heap)
- Practice: Write a C program that malloc's a buffer, fills it with sensor data, processes it, and frees it correctly
- Build: A memory allocator test that shows heap exhaustion — malloc returns NULL
- Document: "Embedded firmware avoids malloc because heap fragmentation causes unpredictable failures. SentinelGrid uses static buffers only: `static float sample_buffer[1024]` lives in memory forever but never fragments"

**Days 36–40:** C — Advanced (interrupts simulation, volatile, state machines)
**Days 41–45:** Introduction to Rust (ownership, borrowing)

---

### DAYS 46–60: Python Advanced + ML Foundations

**Day 46:** NumPy (arrays, vectorized operations)
- Resource: numpy.org/doc/stable/user/quickstart
- Practice: Represent 1000 vibration samples as a NumPy array. Compute mean, std, RMS, kurtosis using NumPy functions
- Document: NumPy is the foundation of all signal processing in Python

**Day 47:** Pandas (DataFrames, time series)
- Resource: pandas.pydata.org/docs/getting_started
- Practice: Load a CSV of simulated SentinelGrid telemetry into a Pandas DataFrame. Filter, sort, group by node_id
- Document: Pandas handles the training data for all ML models

**Day 48:** Matplotlib and visualization
- Practice: Plot 1000 vibration samples as a time-domain signal. Compute FFT in NumPy (np.fft.fft) and plot the frequency spectrum
- Document: "Looking at the FFT of a bearing fault shows a clear spike at the fault frequency. This is how I validated that FFT features are meaningful before building the ML model"

**Days 49–55:** scikit-learn, model training, evaluation
**Days 56–60:** Vector embeddings, ChromaDB, RAG basics

---

# PHASE 2 — DIGITAL HARDWARE AND PROTOCOLS
## Days 61–90

---

### DAY 61
**Topic:** Digital Logic and Binary
**Subtopics:** Binary number system, hexadecimal, bitwise operators in C

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: "Binary and Hexadecimal" — learn.sparkfun.com/tutorials/binary | learn.sparkfun.com |
| AFTERNOON | Practice: In Python, convert decimal to binary and hex manually using bin() and hex(). Then do it without these functions using bitwise operators | Python REPL |
| AFTERNOON | Practice: Write a C program that tests each bit of a byte using bitwise AND: `if (status_byte & 0x08)` means bit 3 is set. Practice reading the ADXL355 status byte from the datasheet | C compiler (use onlinegdb.com) |
| EVENING | Document: `hardware-learning/day61-binary.md`. Include: "The ADXL355 status register is one byte. Bit 3 is DATA_READY (1 = new sample available). To check it in C: `if (status_reg & (1 << 3)) { read_sample(); }`. This is why I must understand binary — every hardware interaction is bit manipulation" | GitHub |

---

### DAY 62
**Topic:** SPI Protocol — Theory
**Subtopics:** Master/slave topology, 4-wire SPI, clock polarity, clock phase, transaction timing

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: ADXL355 datasheet — Section 7 (SPI Interface). Find it at analog.com by searching ADXL355 | analog.com/en/products/adxl355 |
| MORNING | Read: learn.sparkfun.com/tutorials/serial-peripheral-interface-spi | learn.sparkfun.com |
| AFTERNOON | Practice: On sigrok.org/wiki/PulseView — open any SPI example capture. Decode the transactions. Identify CS assertion, clock edges, MOSI/MISO data | sigrok.org/wiki/Downloads |
| AFTERNOON | Simulate: Write a Python function that simulates an SPI transaction: takes register address and data, returns expected response byte. Based on ADXL355 register map | Python file |
| EVENING | Document: `hardware-learning/day62-spi.md`. Draw a timing diagram (use ASCII art or excalidraw). Write: "SPI is synchronous — the clock controls when data is sampled. MOSI is master-to-slave data. MISO is slave-to-master data. CS goes low to select the device, high to deselect. SentinelNode reads ADXL355 over SPI at 4MHz — 6 bytes per transaction, DMA-transferred" | GitHub |

---

### DAY 63
**Topic:** SPI Protocol — Implementation
**Subtopics:** ESP32-S3 SPI HAL, DMA configuration, interrupt vs DMA vs polling

| Block | Activity | Specific Resource |
|-------|----------|-------------------|
| MORNING | Read: ESP-IDF SPI Master documentation | docs.espressif.com/projects/esp-idf — search "SPI Master" |
| AFTERNOON | Practice: Set up ESP-IDF development environment on your computer. Write the Hello World firmware first | docs.espressif.com/projects/esp-idf/en/latest/esp32s3/get-started |
| AFTERNOON | Code: Write a SPI driver that initializes the SPI bus and reads the ADXL355 DEVID register (should return 0xAD). Even without hardware, write the code and get it to compile | ESP-IDF + GCC |
| EVENING | Document: `hardware-learning/day63-spi-implementation.md`. Commit your SPI driver code even if it has not been tested on hardware. Write: "This SPI driver will be tested when my ADXL355 arrives. Right now the code compiles. The test procedure is: read DEVID register, expect 0xAD. If not 0xAD, the SPI clock speed or polarity is wrong" | GitHub |

---

### DAYS 64–70: I2C, UART, ADC, Logic Analyzer

**Day 64:** I2C protocol theory — learn.sparkfun.com/tutorials/i2c
- Write I2C driver for INA226 (read device ID register)
- Document: I2C pull-up resistor requirement and why missing it causes intermittent failures

**Day 65:** UART and serial communication
- Practice: Write firmware that logs over UART in JSON format
- Document: How SentinelGrid's gateway collects UART logs from nodes

**Day 66:** ADC configuration
- Practice: Configure ESP32-S3 ADC to read a potentiometer (or simulated value)
- Configure DMA to read 1000 samples continuously
- Document: ADC resolution, sampling rate, DMA setup

**Day 67:** Logic analyzer usage (virtual)
- Practice: Download Sigrok PulseView. Open example SPI/I2C captures and decode them
- Document: "A logic analyzer captures the actual bits on the wire. When an SPI transaction returns garbage, the logic analyzer shows whether the clock speed is wrong, the CS timing is off, or the data line is floating"

**Day 68:** Oscilloscope fundamentals
- Watch: "EEVblog #279 - How To Use An Oscilloscope" (YouTube, EEVblog channel)
- Practice: Use a simulation oscilloscope at falstad.com/circuit if no hardware available
- Document: How to identify switching regulator noise coupling into ADC

**Day 69:** Interrupt handling theory and implementation
- Resource: CS50 Week 4 + ESP-IDF interrupt documentation
- Build: Data-ready interrupt handler for ADXL355
- Document: ISR rules — no blocking, no dynamic allocation, keep it short

**Day 70:** REST AND REVIEW
- Update all documentation
- Draw the SentinelNode hardware architecture on excalidraw.com
- Commit to GitHub

---

### DAYS 71–90: FreeRTOS and Firmware Architecture

**Day 71:** Why RTOS exists — freertos.org/RTOS.html
- Practice: FreeRTOS simulator on Wokwi (wokwi.com) — it simulates ESP32
- Build: Two tasks blinking LEDs at different rates
- Document: "Without RTOS, one slow operation blocks everything. With RTOS, the scheduler switches between tasks hundreds of times per second"

**Day 72:** FreeRTOS tasks — priorities and stack
- Build: SentinelNode task skeleton: sensor task (priority 5), FFT task (priority 4), inference task (priority 3), comms task (priority 2), OTA task (priority 1)
- Measure: Task stack watermarks after running for 10 minutes
- Document: Task priority reasoning

**Day 73:** FreeRTOS queues
- Build: Sensor task → queue → FFT task pipeline
- Simulate: Fill the queue faster than it is consumed. Watch what happens
- Document: Queue depth sizing — how to calculate

**Day 74:** FreeRTOS semaphores and mutex
- Build: Two tasks sharing one SPI bus, protected by mutex
- Simulate: Remove mutex. Show data corruption
- Document: "Without mutex: task A starts SPI transaction, task B preempts and starts another SPI transaction, chip select corruption, garbage data. With mutex: task B blocks until task A releases. Zero corruption"

**Days 75–80:** Watchdog, sleep modes, power measurement
**Days 81–85:** Flash memory, OTA implementation, A/B partitions
**Days 86–90:** Complete SentinelNode firmware v1 — compile, simulate on Wokwi, document

---

# PHASE 2 COMPLETION CHECKPOINT (Day 90)

**By Day 90, you must be able to say in an interview:**

*"I can write embedded C firmware running on FreeRTOS on an ESP32-S3. I have implemented interrupt-driven sensor reading with DMA, inter-task communication with queues and mutexes, power management with sleep modes, and OTA firmware updates with A/B partition rollback. I have measured stack watermarks for all tasks, documented the task priority design, and written a hard fault handler that captures crash state to flash for remote diagnosis."*

**Your GitHub by Day 90 must contain:**
```
sentinelgrid-firmware/
├── README.md (architecture overview)
├── FIRMWARE.md (task design, stack sizes, priorities)
├── HARDWARE.md (sensor interfaces, pin mapping)
├── main/
│   ├── sensor_task.c
│   ├── fft_task.c
│   ├── comms_task.c
│   ├── ota_task.c
│   └── watchdog_task.c
├── components/
│   ├── adxl355/ (SPI driver)
│   ├── ina226/ (I2C driver)
│   └── spi_flash/ (offline buffer)
└── BENCHMARKS.md (FFT timing, stack watermarks, power consumption)
```

**Mental picture at Day 90:**
You can trace a vibration sample from the moment the ADXL355's interrupt pin goes high, through the ISR that reads it via DMA into a ring buffer, to the FreeRTOS sensor task that picks it up, to the FFT task that computes frequency features, to the inference task that runs TFLite and outputs an anomaly score, to the comms task that publishes the result via MQTT. Every step is in your head clearly.

---

# DAYS 91–180 PREVIEW (Signal Processing + Edge AI + Backend)

**Days 91–110:** Signal Processing
- FFT theory and implementation in Python
- Feature extraction (RMS, kurtosis, spectral bands)
- Digital filter design
- Sensor fusion basics
- Practice: kaggle.com — "Bearing Dataset" or "Motor Vibration" datasets

**Days 111–140:** Edge AI and TinyML
- ML model training (autoencoder for anomaly detection)
- TFLite export and quantization
- Deploy to ESP32-S3 on Wokwi
- Measure inference latency
- Practice: paperswithcode.com — read "TinyML" papers

**Days 141–180:** Backend and Databases
- PostgreSQL and TimescaleDB
- FastAPI complete (all endpoints for InfraMesh and SentinelGrid backend)
- Redis for caching
- Docker and docker-compose
- Practice: SQLZoo, HackerRank SQL, LeetCode database problems

---

# DAYS 181–360 OVERVIEW (Cloud + IoT + Intelligence)

**Days 181–240:** AWS and IoT
- AWS IoT Core, Kinesis, Lambda, RDS
- MQTT at scale
- Terraform for all infrastructure
- OTA pipeline (CI/CD for firmware)

**Days 241–300:** PulseGrid Core
- Kafka stream processing
- Neo4j graph database
- XGBoost risk model
- LLM API integration (Claude)
- GitHub Apps and webhooks

**Days 301–360:** MemCore and Observability
- Vector databases and RAG
- Structured logging across all projects
- Grafana dashboards
- Crash dump analysis
- Postmortem writing practice

---

# DAYS 361–480 OVERVIEW (Advanced + Integration)

**Days 361–420:** PCB Design (SentinelGrid hardware)
- KiCad schematic
- PCB layout
- EMC design
- Manufacturing test

**Days 421–480:** Full System Integration
- All four projects running together
- Load testing
- Incident simulation
- End-to-end postmortems
- Interview preparation

---

# REFERENCE: PRACTICE WEBSITES BY SKILL

| Skill | Primary Practice Site | Secondary Site | Research Papers |
|-------|----------------------|----------------|-----------------|
| Python logic | exercism.org/tracks/python | hackerrank.com/domains/python | — |
| Algorithms | leetcode.com (Easy→Medium) | codeforces.com (Div 4→3) | — |
| SQL | sqlzoo.net | hackerrank.com/domains/sql | — |
| System Design | systemdesign.school | pramp.com | — |
| Linux | overthewire.org/wargames/bandit | cmdchallenge.com | — |
| Git | learngitbranching.js.org | — | — |
| Embedded C | wokwi.com (ESP32 simulator) | onlinegdb.com | ARM Cortex-M reference |
| FreeRTOS | wokwi.com + freertos.org demos | — | FreeRTOS Reference Manual |
| Signal Processing | numpy.org FFT tutorial | kaggle.com bearing datasets | "FFT-based bearing fault detection" on arXiv |
| Edge AI | edgeimpulse.com (guided tutorials) | tinyml.org summit videos | "TinyML survey 2023" on arXiv |
| ML/Python AI | kaggle.com learn | fast.ai | paperswithcode.com |
| MQTT | hivemq.com/mqtt-guide | mosquitto.org docs | — |
| Docker | docs.docker.com get-started | play-with-docker.com | — |
| AWS | aws.amazon.com/getting-started | cloudcraft.co (architecture diagrams) | — |
| Terraform | developer.hashicorp.com/terraform | — | — |
| Neo4j | graphacademy.neo4j.com | — | — |
| Vector DB | docs.trychroma.com | — | "Retrieval Augmented Generation" (Lewis 2020) |
| LLM Integration | platform.anthropic.com/docs | — | "Chain of Thought Prompting" (Wei 2022) |
| Debugging | interrupt.memfault.com | stackoverflow.com | — |
| Architecture | excalidraw.com | draw.io | Google SRE Book (free) |
| PCB Design | kicad.org tutorials | learn.sparkfun.com | IPC-A-610 standard |

---

# DOCUMENTATION TEMPLATES

## Template 1: Daily Documentation (commit every day)
```markdown
# Day [N] — [Topic]
Date: [date]

## What I Learned
[2-3 sentences in your own words]

## Code I Wrote
[paste key code snippet]

## Where This Is Used
- InfraMesh: [specific use]
- SentinelGrid: [specific use]  
- PulseGrid: [specific use]
- MemCore: [specific use]

## What Confused Me
[honest reflection]

## What I Will Practice Tomorrow
[specific next step]
```

## Template 2: Interview Statement (write this after each phase)
```
"I [action verb] [specific thing] for [project name].
This solved [specific problem].
I measured [specific metric].
The result was [specific outcome].
I documented this in [specific file] in my GitHub repository."
```

## Template 3: Architecture Decision Record (write for every major choice)
```markdown
# ADR-[number]: [Decision Title]
Date: [date]
Status: Accepted

## Context
[What problem required this decision?]

## Options Considered
1. [Option A] — pros/cons
2. [Option B] — pros/cons
3. [Option C] — pros/cons

## Decision
[Which option and why]

## Consequences
[What this makes easier and what it makes harder]
```

---

# END OF PART 2

**Part 3 (Days 91–480 detailed daily plan) follows the same structure as Days 1–90.**

**The daily pattern never changes:**
- MORNING: Theory from a specific resource
- AFTERNOON: Hands-on practice on a specific site
- EVENING: Document in GitHub
- END OF DAY: Mental picture check + project connection

**The GitHub repository structure grows every day:**
Every day you commit. After 480 days, your GitHub shows 480+ commits across all four projects with documentation, code, benchmarks, postmortems, and ADRs. This is not just a portfolio. It is evidence of 480 days of consistent engineering practice. No interviewer can fake their way through that history.
# MASTER ROADMAP — PART 3
## Days 91–480 | MemCore Complete Roadmap | Interview Statements | GitHub Structure

---

# PHASE 3 — SIGNAL PROCESSING AND EDGE AI
## Days 91–180

---

### DAY 91
**Topic:** Sampling Theory and Nyquist Theorem
**Subtopics:** Sample rate, aliasing, anti-aliasing filter, why 1kHz matters for bearings

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: "Understanding the Nyquist Theorem" — ni.com/en/shop/data-acquisition/measurement-fundamentals/analog-digital-conversion/the-nyquist-theorem | ni.com |
| MORNING | Read: Bearing fault frequency calculation. Search: "bearing defect frequency calculation BPFO BPFI" | skf.com/en/industry-solutions/condition-monitoring |
| AFTERNOON | Practice: In Python, generate a 50Hz sine wave sampled at 200Hz. Plot with matplotlib. Then sample the same 50Hz sine at 80Hz (below Nyquist). Plot. Observe aliasing — the 50Hz appears as a different frequency | Python + matplotlib |
| AFTERNOON | Calculate: A motor runs at 1800 RPM (30Hz). It has a bearing with 8 ball elements, contact angle 15°, pitch diameter 40mm, ball diameter 8mm. Calculate the BPFO (Ball Pass Frequency Outer race). This is the fault frequency SentinelGrid monitors | Python calculation |
| EVENING | Document: `signal-processing/day91-sampling.md`. Write: "SentinelGrid samples at 1kHz because the highest bearing fault frequency for our motors is 430Hz. Nyquist requires minimum 860Hz, so 1kHz with a 480Hz anti-aliasing filter gives adequate margin. The anti-aliasing IIR filter is implemented in firmware before the DMA buffer" | GitHub |

**Interview Statement:**
*"I selected the 1kHz sampling rate for SentinelGrid by calculating the ball pass frequencies for every motor type in the facility. The highest was 430Hz, so Nyquist required minimum 860Hz sampling. I chose 1kHz and implemented a 4th-order Butterworth low-pass filter at 480Hz in fixed-point arithmetic on the ESP32-S3."*

**Project Connections:**
- SentinelGrid: Direct application — sampling rate and anti-aliasing design
- MemCore: Sampling theory applied to log event streams — sample rate determines detection latency
- InfraMesh: Traffic anomaly — sampling rate of health check metrics determines alert latency
- PulseGrid: Event stream sampling — how often to compute risk score recalculation

---

### DAY 92
**Topic:** FFT Theory and Implementation in Python
**Subtopics:** DFT → FFT, frequency bins, resolution, windowing functions, spectral leakage

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: "FFT Tutorial" — pythonnumericalmethods.berkeley.edu/notebooks/chapter24.03-Fast-Fourier-Transform.html | Berkeley Python Numerical Methods |
| AFTERNOON | Practice: Generate a signal with two sine waves (100Hz and 250Hz) mixed together. Sample at 1kHz for 1 second (1000 samples). Compute FFT with numpy.fft.fft. Plot the magnitude spectrum. Verify the two peaks appear at exactly 100Hz and 250Hz | Python + numpy + matplotlib |
| AFTERNOON | Practice: Apply a Hann window before FFT. Compare the frequency spectrum with and without windowing. Observe spectral leakage reduction | Python |
| EVENING | Document: `signal-processing/day92-fft.md`. Include plots. Write: "Without windowing, a 100Hz signal leaks energy into adjacent frequency bins. With a Hann window, the peak is clean. SentinelGrid applies a Hann window to every 1024-sample frame before FFT. This makes the frequency features more discriminative for the ML model" | GitHub |

---

### DAY 93
**Topic:** FFT Implementation in C (CMSIS-DSP)
**Subtopics:** CMSIS-DSP library, fixed-point FFT, memory layout, timing measurement

| Block | Activity | Resource |
|-------|----------|----------|
| MORNING | Read: ARM CMSIS-DSP documentation — arm-software.github.io/CMSIS-DSP/latest | arm-software.github.io/CMSIS-DSP |
| AFTERNOON | Code: In ESP-IDF, write a C function that takes 1024 float32 samples and returns the magnitude spectrum using arm_rfft_fast_f32. Measure execution time with esp_timer_get_time() before and after | ESP-IDF + wokwi.com simulation |
| AFTERNOON | Verify: Pass the same 100Hz + 250Hz synthetic signal through your C FFT. Compare with your Python FFT output. They must match within floating point tolerance | Both environments |
| EVENING | Document: `signal-processing/day93-fft-c.md`. Write execution time measured on ESP32-S3. Write: "Python reference FFT: 0.8ms (not real-time constraint). C CMSIS-DSP FFT on ESP32-S3: 12ms. This 12ms is the dominant cost in the SentinelNode signal processing pipeline. A new 1024-sample window arrives every 256ms at 4kHz or every 1000ms at 1kHz. Both give adequate headroom" | GitHub + BENCHMARKS.md |

---

### DAYS 94–100: Feature Extraction and Signal Processing Pipeline

**Day 94:** Time-domain features
- Implement in Python: RMS, kurtosis, crest factor, skewness, peak-to-peak
- Test on simulated normal vs fault vibration signals
- Document: "Kurtosis > 3 indicates impulsive events consistent with bearing faults"

**Day 95:** Frequency-domain features
- Implement: Energy in 10 frequency bands (0-50Hz, 50-100Hz, ... 450-500Hz)
- Test: Show that fault signals have higher energy in specific bands
- Document: "The frequency band 400-450Hz has 0.003 energy during normal operation and 0.89 during a bearing fault in our test motor"

**Day 96:** Complete feature extraction pipeline
- Build: Function `extract_features(samples: np.array) -> np.array` that returns 15-element vector
- Test: Process 100 synthetic windows (50 normal, 50 fault). Visualize feature distributions
- Document: Feature importance analysis — which of the 15 features best separates normal from fault?

**Day 97:** C implementation of feature extraction
- Port: Python feature extractor to C. Must produce identical output
- Test: Pass same data through Python and C versions. Verify within 0.001 tolerance
- Document: "The C feature extractor runs in 3ms on ESP32-S3. Total pipeline: 12ms FFT + 3ms features = 15ms per window"

**Day 98:** Sensor fusion theory
- Read: "Sensor Fusion Explained" — towardsdatascience.com
- Design: How to combine vibration score + temperature trend + current anomaly
- Document: "A weighted ensemble: score = 0.6 * vibration + 0.25 * current + 0.15 * temperature. Weights determined by cross-validation on labeled fault data"

**Day 99:** Digital filter design
- Practice: Design a Butterworth IIR low-pass at 480Hz in Python using scipy.signal.butter
- Port: IIR filter coefficients to fixed-point C implementation
- Document: Filter design, coefficients, implementation

**Day 100:** REST AND CHECKPOINT
- Update all documentation
- Commit complete signal processing pipeline to GitHub
- Write interview statement for signal processing phase

---

### DAYS 101–140: Machine Learning and Edge AI

**Day 101:** Anomaly Detection Theory
- Read: scikit-learn.org/stable/modules/outlier_detection.html
- Read: "A survey of anomaly detection techniques" — search on scholar.google.com
- Document: "SentinelGrid uses an LSTM autoencoder because it learns temporal patterns, not just statistical thresholds. A statistical threshold (RMS > 2.5g) would miss slow-developing faults"

| # | Day | Topic | Practice Site | Build | Document |
|---|-----|-------|---------------|-------|----------|
| 1 | 101 | Anomaly detection concepts | scikit-learn docs | Compare: IsolationForest vs Autoencoder on synthetic data | Why autoencoder was chosen (ADR) |
| 2 | 102 | Python ML setup (PyTorch/TensorFlow) | pytorch.org tutorials | Install PyTorch. Train linear regression first | ML environment setup |
| 3 | 103 | Neural network fundamentals | fast.ai Lesson 1 | Train a simple classifier on MNIST | "A neural network is..." explanation |
| 4 | 104 | Autoencoder architecture | towardsdatascience.com autoencoder tutorial | Build autoencoder for 15-element feature vector | Architecture diagram in EDGE_AI.md |
| 5 | 105 | Training on normal data only | kaggle.com bearing dataset | Download Case Western Reserve Bearing Dataset. Extract normal-operation samples | Dataset exploration notebook |
| 6 | 106 | Reconstruction error and threshold | Custom experiment | Plot reconstruction error distribution. Set threshold at mean + 3*std | Threshold selection methodology |
| 7 | 107 | Model evaluation (precision, recall, F1) | sklearn.metrics docs | Evaluate on fault samples. Measure false positive and detection rates | Evaluation results table |
| 8 | 108 | 1D-CNN for vibration | PyTorch 1D Conv tutorial | Build 1D-CNN alternative. Compare with autoencoder | Model comparison table |
| 9 | 109 | TensorFlow Lite export | tensorflow.org/lite/guide | Convert trained autoencoder to .tflite format | Export script in ml/export/ |
| 10 | 110 | Post-training quantization | tensorflow.org/model_optimization | Quantize to INT8. Measure accuracy before/after | BENCHMARKS.md — accuracy vs size |
| 11 | 111 | TFLite Micro on ESP32-S3 | tensorflow.org/lite/microcontrollers | Deploy to Wokwi simulation. Run inference on synthetic data | Inference latency measurement |
| 12 | 112 | Memory arena sizing | TFLite Micro docs | Find minimum arena size. Add 20% margin | "Arena sizing methodology" in EDGE_AI.md |
| 13 | 113 | Edge-cloud split design | Design document | Define which anomaly types edge handles vs cloud | Split inference ADR |
| 14 | 114 | Model drift detection | Custom Python | Compute KL divergence between edge and cloud scores weekly | Drift detection algorithm |
| 15 | 115 | Model OTA implementation | ESP-IDF OTA docs | Implement model partition update without firmware reboot | Model OTA postmortem simulation |
| 16 | 116 | Federated learning concepts | Google AI blog "Federated Learning" | Simulate: compute gradient locally, aggregate without raw data | Federated learning architecture doc |
| 17 | 117 | Cloud retraining pipeline | Python + sklearn | Weekly pipeline: query TimescaleDB → train → evaluate → export | Retraining pipeline code |
| 18 | 118 | End-to-end edge AI test | Complete system | Vibration sample → FFT → features → TFLite → score → MQTT | End-to-end latency: measured |
| 19 | 119 | Performance benchmarking | Custom harness | 1000 inference runs. Measure min/max/avg/p99 latency | BENCHMARKS.md final entry |
| 20 | 120 | REST AND DOCUMENTATION | — | Update all docs. Write edge AI interview statement | EDGE_AI.md complete |

---

**Interview Statement after Day 120:**
*"I built the complete edge AI pipeline for SentinelGrid: FFT feature extraction in C using CMSIS-DSP (12ms), INT8 quantized LSTM autoencoder in TFLite Micro (47ms inference), deployed on ESP32-S3. Float32 model: 182KB, 95.1% detection rate. INT8 model: 46KB, 91.4% detection rate. I documented this 4-point accuracy tradeoff in EDGE_AI.md and justified it: the cloud model running on the same data compensates for the 3.7% edge accuracy loss. I also implemented model OTA — the ML model updates without firmware reboot, zero monitoring downtime."*

---

### DAYS 121–180: Backend and Databases

**Full daily table Days 121–180:**

| Day | Topic | AM Resource | PM Practice | Build | Document |
|-----|-------|-------------|-------------|-------|----------|
| 121 | PostgreSQL fundamentals | postgresql.org tutorial | sqlzoo.net | Create service_registry schema | DATABASE.md |
| 122 | SQL — JOINs and complex queries | mode.com/sql-tutorial | HackerRank SQL Intermediate | Query: "all services owned by team X that failed health check in last 24h" | Query library |
| 123 | SQL — Indexes and performance | use-the-index-luke.com | EXPLAIN ANALYZE on your queries | Add indexes. Measure before/after | BENCHMARKS.md — query times |
| 124 | SQL — Transactions and ACID | postgresql.org/docs/current/tutorial-transactions | Write a transaction that registers service + creates DNS record atomically | "Why InfraMesh uses transactions" | ADR-009 |
| 125 | TimescaleDB fundamentals | docs.timescale.com/getting-started | Install TimescaleDB. Create telemetry hypertable | SentinelGrid telemetry schema | DATABASE.md |
| 126 | TimescaleDB — Hypertables and partitioning | docs.timescale.com/use-timescale/hypertables | Benchmark: query 1M rows with vs without time partitioning | Partitioning improvement measured | BENCHMARKS.md |
| 127 | TimescaleDB — Continuous aggregates | docs.timescale.com/use-timescale/continuous-aggregates | Create hourly_anomaly_summary view | "5-second query becomes 50ms with continuous aggregate" | BENCHMARKS.md |
| 128 | Redis fundamentals | redis.io/docs/get-started | Install Redis. Implement rate limiting counter in Python | InfraMesh rate limiter | IOT_PROTOCOLS.md |
| 129 | Redis — Pub/Sub and Streams | redis.io/docs/data-types/streams | Simulate MQTT-like pub/sub with Redis Streams | Gateway simulation | Architecture doc |
| 130 | ChromaDB and vector embeddings | docs.trychroma.com | Store 100 bug descriptions as embeddings. Query by similarity | MemCore memory prototype | MEMCORE.md |
| 131 | FastAPI — Full application | fastapi.tiangolo.com advanced | Build complete InfraMesh API: register, status, list, delete | All InfraMesh endpoints | API.md |
| 132 | FastAPI — Background tasks and lifespan | fastapi.tiangolo.com/advanced/background-tasks | Add background SQS publish to registration endpoint | Async provisioning flow | ARCHITECTURE.md |
| 133 | FastAPI — Database connection (SQLAlchemy) | sqlalchemy.org/docs | Connect FastAPI to PostgreSQL via SQLAlchemy async | InfraMesh database layer | DATABASE.md |
| 134 | FastAPI — Authentication (JWT) | fastapi.tiangolo.com/tutorial/security | Add JWT auth to all InfraMesh endpoints | Authenticated API | SECURITY.md |
| 135 | FastAPI — Testing | fastapi.tiangolo.com/tutorial/testing | Write pytest tests for all InfraMesh endpoints | Test suite — 90% coverage | Test report |
| 136 | Docker fundamentals | docs.docker.com/get-started | Dockerize InfraMesh FastAPI app | Multi-stage Dockerfile, 180MB image | DOCKER.md |
| 137 | Docker Compose | docs.docker.com/compose | docker-compose.yml: FastAPI + PostgreSQL + Redis | One-command local stack | RUNNING.md |
| 138 | Docker — Production considerations | realpython.com/dockerizing-flask-with-compose | Non-root user, health check in Dockerfile, .dockerignore | Production-ready image | DOCKER.md |
| 139 | SentinelGrid backend API | Building on days 131-138 | FastAPI API for device management: register node, get health, push OTA command | SentinelGrid management API | API.md |
| 140 | REST AND CHECKPOINT | — | Complete all documentation | All 3 APIs (InfraMesh, SentinelGrid, PulseGrid skeleton) | API.md for all projects |

---

# PHASE 4 — CLOUD AND IOT
## Days 141–240

### Daily Table Format (Condensed — follows same morning/afternoon/evening structure)

| Day | Topic | Build This Day | Document | Interview Proof |
|-----|-------|----------------|----------|-----------------|
| 141 | AWS Account Setup + IAM | Create IAM user with minimal permissions. Enable MFA | SECURITY.md — IAM policy design | "I follow least-privilege. Show any IAM role in my Terraform" |
| 142 | AWS EC2 | Launch t2.micro. SSH in. Deploy InfraMesh FastAPI via Docker | INFRASTRUCTURE.md — EC2 setup | "EC2 is where all backend services run" |
| 143 | AWS S3 | Create buckets for firmware (SentinelGrid), postmortems (PulseGrid), logs | INFRASTRUCTURE.md — S3 structure | "S3 stores firmware binaries with version metadata" |
| 144 | AWS RDS PostgreSQL | Launch RDS PostgreSQL. Connect from FastAPI. Migrate schema | DATABASE.md — RDS config | "RDS manages backups and failover automatically" |
| 145 | AWS SQS | Create SQS queue + DLQ. Publish from FastAPI. Consume in Python worker | ARCHITECTURE.md — queue design | "InfraMesh's provisioning is SQS-based" |
| 146 | AWS Lambda | Write Lambda that processes SQS message, calls Route53 | INFRASTRUCTURE.md — Lambda | "Lambda provisions DNS records serverlessly" |
| 147 | AWS Route53 | Programmatically create A record from Python | INFRASTRUCTURE.md — DNS | "InfraMesh creates DNS records in under 5 seconds" |
| 148 | AWS ALB | Configure ALB rules for registered services programmatically | INFRASTRUCTURE.md — ALB | "Each registered service gets an ALB rule" |
| 149 | AWS CloudFront | Configure CloudFront distribution for a service | INFRASTRUCTURE.md — Edge | "CloudFront provides DDoS protection at the edge" |
| 150 | AWS ACM | Request and validate TLS certificate programmatically | SECURITY.md — TLS | "Every service gets free TLS via ACM" |
| 151 | Terraform — Introduction | terraform init, plan, apply on simple S3 bucket | TERRAFORM.md start | "All infrastructure is code" |
| 152 | Terraform — Variables and outputs | Extract hardcoded values to variables.tf | TERRAFORM.md — variables | "terraform.tfvars separates config from code" |
| 153 | Terraform — AWS Provider | Write VPC, subnets, security groups in Terraform | infrastructure/vpc.tf | "VPC created in < 3 minutes with Terraform" |
| 154 | Terraform — RDS Module | RDS PostgreSQL as Terraform module | infrastructure/rds.tf | "Database reproduced from code" |
| 155 | Terraform — Complete InfraMesh infra | All InfraMesh AWS resources in one terraform apply | infrastructure/ complete | "12 minutes to recreate from scratch" |
| 156 | AWS IoT Core — Device registration | Register SentinelNode in IoT Core. Create certificate | IOT.md — device provisioning | "Each node has unique certificate" |
| 157 | AWS IoT Core — MQTT at scale | Connect 100 simulated nodes using Python MQTT client | IOT.md — scale test | "IoT Core handles 10,000 connections" |
| 158 | AWS IoT Core — IoT Rules | Route telemetry topic to Kinesis via IoT Rule | ARCHITECTURE.md — IoT pipeline | "IoT Rules route without custom code" |
| 159 | AWS Kinesis — Setup | Create Kinesis stream, publish from IoT Rule, consume in Lambda | INFRASTRUCTURE.md — Kinesis | "Kinesis buffers 24h of telemetry" |
| 160 | AWS Kinesis — Python consumer | Python Kinesis consumer that writes to TimescaleDB | Cloud pipeline complete | "End-to-end: node → IoT Core → Kinesis → Lambda → TimescaleDB" |
| 161 | MQTT Deep Dive — QoS 0/1/2 | Test QoS 0 vs QoS 1 under network interruption. Measure message loss | IOT_PROTOCOLS.md | "QoS 0 lost 2.3% of messages. QoS 1: 0%" |
| 162 | MQTT Topic Design | Complete SentinelGrid topic hierarchy documented | IOT_PROTOCOLS.md | "Topic design determines routing efficiency" |
| 163 | Store-and-Forward Implementation | SPI flash buffer on Wokwi + Python test of delivery guarantee | IOT_PROTOCOLS.md | "4-hour outage test: 0 messages lost" |
| 164 | MQTT Security (TLS + Client Cert) | Configure Mosquitto with TLS. Test client certificate rejection | SECURITY.md | "Rogue device rejected at TLS handshake" |
| 165 | MQTT Broker Load Testing | Python script: 200 simulated nodes, 1 msg/5sec. Measure broker CPU | BENCHMARKS.md | "200 nodes: Mosquitto uses 12% CPU on Pi 4" |
| 166 | LoRa Theory | Read SX1276 datasheet. Understand spreading factor vs data rate | HARDWARE.md | "LoRa SF12 = 300bps but 15km range" |
| 167 | LoRa Implementation (simulation) | Simulate LoRa packet in Python (no hardware needed) | HARDWARE.md — LoRa | "LoRa is the fallback when WiFi fails in factory" |
| 168 | OTA Pipeline — GitHub Actions | Firmware CI/CD: compile → sign → upload S3 | .github/workflows/firmware.yml | "8 minutes from push to OTA available" |
| 169 | OTA Pipeline — Staged Rollout | Python script: deploy to 5% of fleet, monitor, expand | OTA.md — staged rollout | "5%→20%→100% with 2h monitoring windows" |
| 170 | OTA Incident Simulation | Inject bug. Watch rollback. Document as postmortem | POSTMORTEMS/001-ota-crash-loop.md | "Rollback mechanism saved 200 nodes" |
| 171 | Device Provisioning (first boot) | First-boot certificate request and installation flow | OTA.md — provisioning | "Zero-touch provisioning at manufacturing" |
| 172 | Fleet Management Dashboard | Grafana: node online/offline, firmware versions, battery levels | Dashboard JSON | "At a glance: 187/200 nodes healthy" |
| 173 | TimescaleDB at Scale | Load 10M rows. Test query performance. Add continuous aggregates | BENCHMARKS.md | "10M rows, 45ms for 30-day query" |
| 174 | SageMaker — Model Training Pipeline | Weekly retraining job: query TimescaleDB → train → evaluate → S3 | ml/retraining-pipeline/ | "Model improves weekly from production data" |
| 175 | CloudFront for OTA | Configure CloudFront in front of S3 firmware bucket | INFRASTRUCTURE.md | "1000 nodes downloading simultaneously: no S3 throttling" |
| 176 | Load Testing the Full Stack | k6 load test: 1000 simulated nodes, 10 events/second | BENCHMARKS.md — cloud scale | "System handles 10,000 events/minute" |
| 177 | Security Audit — All Projects | OWASP ZAP against all APIs. Fix findings | SECURITY.md — penetration test | "Zero high-severity findings after remediation" |
| 178 | Disaster Recovery Drill | Delete RDS instance. Restore from backup. Measure RTO | RUNBOOK.md — disaster recovery | "RTO: 23 minutes for full restore" |
| 179 | Complete SentinelGrid Cloud Documentation | All docs finalized | CLOUD.md complete | "Complete system documented" |
| 180 | REST AND PHASE 4 CHECKPOINT | Review + interview prep | All docs reviewed | See checkpoint below |

---

**Phase 4 Interview Statement:**
*"I designed and deployed SentinelGrid's complete cloud pipeline: ESP32-S3 nodes → AWS IoT Core → Kinesis → Lambda → TimescaleDB. The entire infrastructure is Terraform — I can destroy and recreate it in 12 minutes. I load tested with 1000 simulated nodes at 10 events/second and measured the bottleneck at the Kinesis Lambda consumer (fixed with batching). I implemented OTA with a staged rollout system and documented a production incident where a bug in firmware caused 200 nodes to crash-loop — the rollback mechanism prevented them from bricking."*

---

# PHASE 5 — PULSEGRID (ENGINEERING INTELLIGENCE)
## Days 181–300

| Day | Topic | Build | Document | Interview Proof |
|-----|-------|-------|----------|-----------------|
| 181 | Kafka — Why it exists | Read: kafka.apache.org/documentation — "Introduction" | PULSEGRID.md — event stream design | "Kafka gives us replayable, ordered events" |
| 182 | Kafka — Setup and first producer/consumer | Install Kafka locally. Produce 100 events. Consume all | PULSEGRID.md — Kafka setup | "Kafka retains messages for 7 days for replay" |
| 183 | Kafka — Topics, partitions, consumer groups | Create 6 PulseGrid topics. Partition by org_id | ARCHITECTURE.md — Kafka | "Partitioning by org guarantees in-order processing per org" |
| 184 | GitHub Apps — Setup | Create GitHub App. Configure webhooks. Receive first PR event | PULSEGRID.md — GitHub integration | "GitHub App gets webhook on every PR, push, and deployment" |
| 185 | GitHub Webhooks — Parse PR payload | Parse GitHub PR webhook JSON. Extract: files changed, reviewer list, PR size | PULSEGRID.md — feature extraction | "PR payload contains all risk features" |
| 186 | GitHub API — Read PR diff | Call GitHub API to get the actual diff for a PR | Code — github_client.py | "I read the actual diff to know which files changed" |
| 187 | PagerDuty Webhooks | Configure PagerDuty test account. Receive incident webhooks | PULSEGRID.md — incident integration | "PagerDuty tells us when and how incidents resolve" |
| 188 | Sentry Webhooks | Configure Sentry test account. Receive error rate webhooks | PULSEGRID.md — error integration | "Error rate spike is a leading indicator of incident" |
| 189 | OpenTelemetry — Theory | Read: opentelemetry.io/docs/concepts | PULSEGRID.md — observability | "OpenTelemetry traces show service call relationships" |
| 190 | OpenTelemetry — Instrument a service | Instrument the InfraMesh FastAPI with OpenTelemetry | infrastructure/otel-collector.yml | "Every service call is a span in a trace" |
| 191 | Neo4j — Introduction | graphacademy.neo4j.com — Fundamentals course (free) | PULSEGRID.md — graph DB | "Graph traversal finds blast radius in 12ms" |
| 192 | Neo4j — Cypher queries | Write Cypher: create service nodes, create dependency edges, traverse 3 hops | queries/blast-radius.cypher | "MATCH (s)-[*1..3]->(dep) WHERE s.name = 'payment-service'" |
| 193 | Dependency Graph from Traces | Parse OTel spans to extract service → service calls. Write to Neo4j | Code — graph_updater.py | "Graph updates in real-time as traces arrive" |
| 194 | Blast Radius Calculator | Traverse Neo4j graph. Weight by call frequency. Calculate user impact | Code — blast_radius.py | "payment-service blast radius: 34% of active users" |
| 195 | Blast Radius API | FastAPI endpoint: GET /api/v1/blast-radius/{service_id} | API.md — PulseGrid | "3-second response for any service" |
| 196 | Risk Feature Engineering | Extract 23 PR features from GitHub API | Code — risk_features.py | "23 features: PR size, reviewer experience, file history..." |
| 197 | Historical Incident Correlation | Match PRs to incidents by deployment time proximity | Code — incident_correlator.py | "PR deployed 2h before incident = labeled positive example" |
| 198 | XGBoost Risk Model Training | Train on correlated PR-incident data. Measure AUC | ml/risk-model/train.py | "AUC: 0.82 on holdout set (18 months of data)" |
| 199 | Risk Score API | POST risk score as GitHub PR comment within 60 seconds | Code — github_commenter.py | "Comment appears on PR within 60 seconds" |
| 200 | Risk Model Validation | Backtest: would the model have flagged the last 5 real incidents? | PULSEGRID.md — validation | "4 of 5 incidents had risk score > 65" |
| 201 | Incident Timeline Assembly | Correlate events across Kafka topics for incident window | Code — timeline_assembler.py | "Timeline built from 6 data sources in 30 seconds" |
| 202 | Claude/LLM API Integration | Call Anthropic API with structured prompt. Parse response | Code — llm_client.py | "LLM receives structured context, not raw text" |
| 203 | Postmortem Prompt Engineering | Design 8-slot structured prompt for postmortem generation | prompts/postmortem.txt | "Every fact in the postmortem comes from retrieved data" |
| 204 | Postmortem RAG Implementation | Retrieve similar past incidents from ChromaDB for context | Code — postmortem_rag.py | "Similar past incidents provide historical context" |
| 205 | Postmortem Generation End-to-End | PagerDuty resolves → timeline assembled → LLM generates → Confluence posted | Code — postmortem_generator.py | "Postmortem draft ready 5 minutes after resolution" |
| 206 | Confluence API Integration | POST generated postmortem to Confluence page automatically | Code — confluence_client.py | "Zero copy-paste. Draft appears automatically" |
| 207 | DORA Metrics Calculation | Deployment frequency, lead time, MTTR, change failure rate | Code — dora_calculator.py | "Real DORA metrics, not estimates" |
| 208 | React Dashboard — Setup | Create React app. Configure Recharts and D3 | dashboard/ | "Dashboard updates in real-time" |
| 209 | React Dashboard — Risk PR list | List high-risk open PRs with risk score and factors | dashboard/RiskPRList.jsx | "Engineers see risk before merging" |
| 210 | React Dashboard — Dependency graph | D3 or Cytoscape.js interactive graph with blast radius highlight | dashboard/DependencyGraph.jsx | "Click any service to see blast radius live" |
| 211 | React Dashboard — DORA metrics | Time-series charts for all 4 DORA metrics per team | dashboard/DORAdashboard.jsx | "Management view: elite vs needs improvement" |
| 212 | Kafka Consumer — Scale Testing | 10 orgs, 1000 PRs/day each. Measure consumer lag | BENCHMARKS.md — PulseGrid | "10,000 events/minute, consumer lag < 2 seconds" |
| 213 | PulseGrid Dogfooding | Instrument PulseGrid itself with OpenTelemetry. Monitor with PulseGrid | OBSERVABILITY.md | "PulseGrid monitors PulseGrid" |
| 214 | PulseGrid Security | Webhook signature verification. HMAC validation of GitHub payloads | SECURITY.md | "Reject webhooks without valid HMAC signature" |
| 215 | PulseGrid Terraform | All AWS resources for PulseGrid in Terraform | infrastructure/pulsegrid/ | "Recreate PulseGrid in 15 minutes" |
| 216-220 | PulseGrid Load Testing + Documentation | k6 load test. All docs finalized | All PulseGrid docs | "Production-ready documentation" |

---

**PulseGrid Interview Statement:**
*"PulseGrid ingests events from GitHub, PagerDuty, Sentry, Prometheus, and OpenTelemetry into a Kafka stream. A Python processor builds a live service dependency graph in Neo4j from distributed traces — the graph reflects actual service calls, not manual documentation. An XGBoost classifier trained on 18 months of our incident history scores every PR for risk and posts the result as a GitHub comment within 60 seconds. When an incident resolves, PulseGrid assembles the timeline from 6 data sources and generates a postmortem draft via the Claude API in under 5 minutes. The risk model has an AUC of 0.82 and correctly flagged 4 of the 5 most recent production incidents."*

---

# PHASE 6 — MEMCORE (EMBEDDED AI SDK)
## Days 221–300

*Note: MemCore development runs parallel with PulseGrid — learn MemCore concepts while building PulseGrid, then implement MemCore separately*

### MemCore Full Roadmap (this is the fourth project, previously undocumented)

**What MemCore Is:**
An SDK (library) that any application imports to get persistent debugging intelligence. It observes the application, builds a vocabulary of its behavior, stores this in a vector database, and when bugs occur, retrieves relevant historical context and generates fix suggestions.

**MemCore Architecture (detailed):**

```
APPLICATION (any Python app or C firmware)
    │ imports memcore
    ▼
┌─────────────────────────────────────────┐
│  MEMCORE OBSERVATION LAYER              │
│  ├── Python: sys.settrace() hooks       │
│  ├── Python: logging.Handler intercept  │
│  ├── Python: sys.excepthook override    │
│  └── C: Hard fault handler injection    │
└─────────────────────────────────────────┘
    │ raw events (exceptions, log lines, crashes)
    ▼
┌─────────────────────────────────────────┐
│  MEMCORE AST ANALYZER                   │
│  ├── tree-sitter: parse Python/C AST    │
│  ├── Build call graph from source       │
│  ├── Extract function signatures        │
│  └── Index function semantics           │
└─────────────────────────────────────────┘
    │ structured code understanding
    ▼
┌─────────────────────────────────────────┐
│  MEMCORE VOCABULARY ENGINE              │
│  ├── CodeBERT embeddings for each func  │
│  ├── Store in ChromaDB with metadata    │
│  ├── Track vocabulary drift (weekly)    │
│  └── Create new entries for new patterns│
└─────────────────────────────────────────┘
    │ vocabulary + embeddings
    ▼
┌─────────────────────────────────────────┐
│  MEMCORE MEMORY LAYER                   │
│  ├── Short-term: Redis (current session)│
│  ├── Long-term: ChromaDB (past bugs)    │
│  └── Episodic: PostgreSQL (structured)  │
└─────────────────────────────────────────┘
    │ context assembled
    ▼
┌─────────────────────────────────────────┐
│  MEMCORE REASONING ENGINE               │
│  ├── Retrieves: top-5 similar past bugs │
│  ├── Retrieves: relevant code context   │
│  ├── Assembles structured prompt        │
│  ├── Calls LLM API (Claude/local model) │
│  └── Returns: ranked fix suggestions   │
└─────────────────────────────────────────┘
    │ suggestions
    ▼
DEVELOPER (via CLI, IDE plugin, or API)
```

| Day | Topic | Build | Document | Interview Proof |
|-----|-------|-------|----------|-----------------|
| 221 | AST Parsing (Python) | Use tree-sitter to parse a Python function into AST. Extract: function name, parameters, called functions, return type | MEMCORE.md — static analysis | "MemCore understands code structure before it runs" |
| 222 | Call Graph Construction | Parse entire InfraMesh codebase. Build call graph: which function calls which | Code — call_graph_builder.py | "Call graph shows: if payment_service.create_dns() fails, it affects register_service()" |
| 223 | Code Embeddings with CodeBERT | Install sentence-transformers. Embed 100 Python functions. Query by similarity | Code — code_embedder.py | "Similar functions by meaning, not by name" |
| 224 | ChromaDB — Store and Query | Store 100 function embeddings in ChromaDB. Query: 'find functions similar to create_dns_record' | Code — vocabulary_store.py | "Semantic search over codebase in 50ms" |
| 225 | Exception Hooking | Override sys.excepthook in Python. Capture: traceback, local variables, timestamp | Code — exception_hook.py | "Every unhandled exception is captured with full context" |
| 226 | Log Interception | Custom Python logging.Handler that routes all logs to MemCore | Code — log_interceptor.py | "MemCore sees all logs without code changes" |
| 227 | Episodic Memory Design | PostgreSQL schema for bug history: bug_id, timestamp, error_type, affected_function, fix_applied, outcome | DATABASE.md — MemCore | "Every bug and its fix stored permanently" |
| 228 | Short-Term Memory (Redis) | Redis session: current errors, recent function calls, active changes | Code — short_term_memory.py | "Current session context in < 1ms retrieval" |
| 229 | Long-Term Memory (ChromaDB) | Store bug embeddings. Retrieve by semantic similarity | Code — long_term_memory.py | "Bug from 6 months ago retrieved in 80ms" |
| 230 | Context Assembly | When new bug occurs: retrieve top-5 similar, get relevant code, recent changes | Code — context_assembler.py | "LLM receives: current error + 5 past similar + relevant code + recent git diff" |
| 231 | LLM Integration for Fix Suggestion | Structured prompt → Claude API → parse ranked suggestions | Code — reasoning_engine.py | "Fix suggestion with explanation in 3 seconds" |
| 232 | Vocabulary Drift Detection | Weekly: recompute function embeddings. Compare to stored. Flag changed semantics | Code — drift_detector.py | "fetchUser() contract changed 2 weeks ago — vocabulary updated" |
| 233 | New Vocabulary Entry Creation | When new pattern appears 3+ times: create named vocabulary entry | Code — vocabulary_creator.py | "MemCore learned: payment_timeout pattern = network issue, not code bug" |
| 234 | Developer Feedback Loop | Accept/reject/modify suggestion. Store outcome. Update model weights | Code — feedback_handler.py | "After 30 days, suggestion acceptance rate: 73%" |
| 235 | MemCore as SDK | Package as Python library: `pip install memcore`. Single-line integration | Code — setup.py | "Any developer installs and uses in 5 minutes" |
| 236 | MemCore CLI | `memcore diagnose` command that shows current system health + recent bugs | Code — cli.py | "Developers run memcore from terminal" |
| 237 | MemCore for InfraMesh | Integrate MemCore into InfraMesh. Let it learn InfraMesh's bugs | Integration test | "MemCore knows InfraMesh's provisioning patterns" |
| 238 | MemCore for SentinelGrid Gateway | Lightweight MemCore variant for Python gateway code | Code — memcore_lite.py | "Gateway MemCore monitors its own Python pipeline" |
| 239 | MemCore for PulseGrid | MemCore monitors PulseGrid's stream processor. Detects Kafka consumer lag patterns | Integration | "MemCore diagnoses PulseGrid's own failures" |
| 240 | MemCore C Agent (firmware) | Minimal C implementation: crash capture → flash storage → UART output | Code — memcore_agent.c | "Firmware MemCore captures crash context" |

---

**MemCore Interview Statement:**
*"MemCore is an SDK that gives any application persistent debugging intelligence. You import it into your codebase — one line. It hooks into Python's exception system, intercepts logs, parses your AST with tree-sitter to build a call graph, and stores function semantics as CodeBERT embeddings in ChromaDB. When a bug occurs, it retrieves the 5 most semantically similar past bugs, assembles context with the current error and recent git diff, and generates a ranked fix suggestion via the Claude API. The suggestion acceptance rate after 30 days of use on InfraMesh reached 73%. I also built a 400-line C version that runs on the SentinelGrid gateway — it captures crash dumps from firmware and stores the vocabulary of what the gateway Python pipeline normally does."*

---

# PHASE 7 — OBSERVABILITY AND PRODUCTION ENGINEERING
## Days 301–360

| Day | Topic | Build | Document | Site |
|-----|-------|-------|----------|------|
| 301 | Structured Logging Standards | Implement JSON logging in all 4 projects. Consistent schema | OBSERVABILITY.md | structlog.readthedocs.io |
| 302 | Prometheus Metrics | Expose /metrics from all FastAPI services | Prometheus config | prometheus.io/docs |
| 303 | Grafana Setup | Connect all data sources: TimescaleDB, Prometheus, InfluxDB | Dashboard JSON | grafana.com/docs |
| 304 | InfraMesh Dashboard | Service health, provisioning queue, cost attribution | Dashboard exported to GitHub | Grafana |
| 305 | SentinelGrid Dashboard | Fleet health, anomaly timeline, OTA status, battery map | Dashboard exported | Grafana |
| 306 | PulseGrid Dashboard | Risk PRs, DORA metrics, dependency graph panel | Dashboard exported | Grafana |
| 307 | MemCore Dashboard | Bug frequency, suggestion acceptance rate, vocabulary growth | Dashboard exported | Grafana |
| 308 | Alert Rules Design | Write alert conditions for all 4 projects | RUNBOOK.md | grafana.com/docs/alerting |
| 309 | Runbook — InfraMesh | 5 runbooks: SQS depth, provisioning failure, health check failure, API latency | RUNBOOK.md InfraMesh | SRE book sre.google |
| 310 | Runbook — SentinelGrid | 5 runbooks: node offline, OTA failure, battery critical, anomaly confirmed | RUNBOOK.md SentinelGrid | SRE book |
| 311 | Runbook — PulseGrid | 4 runbooks: Kafka consumer lag, Neo4j unreachable, risk model drift, LLM API failure | RUNBOOK.md PulseGrid | SRE book |
| 312 | Distributed Tracing — Setup | OpenTelemetry collector + Jaeger for all projects | infrastructure/otel.yml | opentelemetry.io |
| 313 | Trace a request end-to-end | Trace GitHub webhook → Kafka → processor → Neo4j → risk score → GitHub comment | OBSERVABILITY.md | Jaeger UI |
| 314 | Postmortem Practice 1 | Simulate: InfraMesh SQS failure. Write full postmortem | POSTMORTEMS/002-sqs-failure.md | Google SRE postmortem template |
| 315 | Postmortem Practice 2 | Simulate: SentinelGrid model drift causing false alarms | POSTMORTEMS/003-model-drift.md | — |
| 316 | Postmortem Practice 3 | Simulate: PulseGrid Kafka partition assignment failure | POSTMORTEMS/004-kafka-rebalance.md | — |
| 317 | Postmortem Practice 4 | Simulate: MemCore LLM API rate limit causing suggestion timeout | POSTMORTEMS/005-llm-ratelimit.md | — |
| 318 | On-Call Simulation | 2-hour on-call exercise: intentionally break 2 things. Diagnose using only runbooks + dashboards | On-call report | PagerDuty free trial |
| 319 | Load Testing All Projects | k6 load test all APIs simultaneously | BENCHMARKS.md — final | k6.io |
| 320 | Security Audit Final | OWASP ZAP all public APIs. Document findings and remediations | SECURITY.md final | owasp.org/www-project-zap |
| 321-330 | PCB Design Phase (SentinelGrid) | KiCad schematic + PCB layout | hardware/kicad/ | kicad.org |
| 331-340 | EMC Design and Manufacturing Test | Manufacturing test firmware | MANUFACTURING.md | learn.sparkfun.com |
| 341-350 | System Integration Testing | All 4 projects running together for 72 hours | Integration test report | — |
| 351-360 | Documentation Final Pass | Every document reviewed, updated, linked | All docs complete | — |

---

# PHASE 8 — FULL INTEGRATION AND INTERVIEW PREPARATION
## Days 361–420

### Complete GitHub Repository Structure (Final State)

```
github.com/[yourname]/
│
├── sentinelgrid/                         ← Hardware + AI project
│   ├── README.md
│   ├── ARCHITECTURE.md
│   ├── HARDWARE.md (KiCad, BOM)
│   ├── FIRMWARE.md (RTOS task design)
│   ├── SIGNAL_PROCESSING.md
│   ├── EDGE_AI.md
│   ├── IOT_PROTOCOLS.md
│   ├── CLOUD.md
│   ├── OTA.md
│   ├── OBSERVABILITY.md
│   ├── MANUFACTURING.md
│   ├── BENCHMARKS.md
│   ├── RUNBOOK.md
│   ├── POSTMORTEMS/ (4 postmortems)
│   ├── ADR/ (8 decisions)
│   ├── firmware/ (complete ESP-IDF)
│   ├── ml/ (training + quantization)
│   ├── hardware/ (KiCad project)
│   ├── infrastructure/ (Terraform)
│   ├── backend/ (FastAPI)
│   └── dashboard/ (Grafana JSON)
│
├── pulsegrid/                            ← Engineering intelligence project
│   ├── README.md
│   ├── ARCHITECTURE.md
│   ├── API.md
│   ├── DATABASE.md
│   ├── CLOUD.md
│   ├── OBSERVABILITY.md
│   ├── RUNBOOK.md
│   ├── POSTMORTEMS/ (3 postmortems)
│   ├── ADR/ (7 decisions)
│   ├── BENCHMARKS.md
│   ├── api/ (FastAPI webhook ingestion)
│   ├── processor/ (Kafka stream processor)
│   ├── risk_model/ (XGBoost + training)
│   ├── postmortem_gen/ (RAG + LLM)
│   ├── dashboard/ (React + Grafana)
│   ├── infrastructure/ (Terraform)
│   └── .github/workflows/
│
├── memcore/                              ← Embedded AI SDK project
│   ├── README.md
│   ├── ARCHITECTURE.md
│   ├── API.md (SDK documentation)
│   ├── BENCHMARKS.md
│   ├── POSTMORTEMS/ (2 postmortems)
│   ├── ADR/ (5 decisions)
│   ├── memcore/ (Python package)
│   │   ├── __init__.py
│   │   ├── observer.py
│   │   ├── ast_analyzer.py
│   │   ├── vocabulary.py
│   │   ├── memory.py
│   │   ├── reasoning.py
│   │   └── cli.py
│   ├── memcore_c/ (C firmware agent)
│   ├── examples/ (integration with InfraMesh, SentinelGrid, PulseGrid)
│   └── tests/ (90%+ coverage)
│
└── learning-journal/                     ← Your daily documentation
    ├── README.md (this is your story)
    ├── mental-models/ (Days 1-14 docs)
    ├── python-learning/ (Days 15-60)
    ├── hardware-learning/ (Days 61-90)
    ├── signal-processing/ (Days 91-120)
    ├── edge-ai/ (Days 101-140)
    ├── backend-databases/ (Days 121-180)
    ├── cloud-iot/ (Days 141-240)
    ├── pulsegrid-build/ (Days 181-260)
    ├── memcore-build/ (Days 221-300)
    ├── observability/ (Days 301-340)
    └── interview-prep/ (Days 361-420)
```

---

# MASTER INTERVIEW STATEMENT TABLE

This table gives you the exact words to use in an interview for every skill domain:

| Domain | Statement |
|--------|-----------|
| **Overall** | "I built four interconnected MNC-standard projects over 14 months: SentinelGrid (distributed edge AI monitoring system), PulseGrid (engineering intelligence platform), MemCore (embedded AI debugging SDK), and contributed to InfraMesh design. Every project has full documentation, ADRs, postmortems, and Terraform infrastructure. My GitHub commit history spans 420+ days of consistent engineering practice." |
| **Embedded Firmware** | "I wrote production FreeRTOS firmware for ESP32-S3. Seven concurrent tasks: sensor reading via DMA interrupt, FFT processing, INT8 TFLite inference, MQTT communication, OTA management, hardware watchdog feeding, and device health reporting. All tasks have measured stack watermarks documented in BENCHMARKS.md. The system has run for 72 consecutive hours in stability testing with zero unplanned resets." |
| **Edge AI** | "I trained an LSTM autoencoder on Case Western Reserve Bearing Dataset, exported to TFLite, quantized to INT8 (4x size reduction, 6.7x faster inference). Deployed on ESP32-S3: 47ms inference latency. Accuracy: 91.4% detection rate at 0.3% false positive rate. I also implemented model OTA — AI models update independently from firmware, zero monitoring downtime during model updates." |
| **Signal Processing** | "I designed the complete vibration analysis pipeline for SentinelGrid: 4th-order Butterworth IIR anti-aliasing at 480Hz, 1024-point Hann-windowed FFT using CMSIS-DSP (12ms on ESP32-S3), 15-element feature vector (5 time-domain + 10 frequency-band features). Both Python reference and C production implementations produce identical output within floating-point tolerance." |
| **IoT + MQTT** | "SentinelGrid uses MQTT QoS 1 with TLS client certificate authentication. I designed the topic hierarchy, tested QoS 0 vs QoS 1 under simulated network interruption (QoS 0: 2.3% message loss, QoS 1: 0%), and implemented store-and-forward using SPI flash. A 4-hour outage test confirmed zero message loss with chronological delivery on reconnect." |
| **AWS Cloud** | "SentinelGrid's cloud infrastructure is fully Terraform: IoT Core, Kinesis, Lambda, RDS TimescaleDB, S3, CloudFront, VPC. I load tested with 1000 simulated nodes and identified the Lambda consumer as bottleneck under burst. Fixed with batching — throughput increased from 2,000 to 18,000 events/minute. All AWS resources follow least-privilege IAM." |
| **Databases** | "I use three database types across projects: PostgreSQL for structured relational data (service registry, incident records), TimescaleDB for time-series telemetry (10M rows, 45ms for 30-day queries with time partitioning and continuous aggregates), and Neo4j for service dependency graphs (blast radius traversal in 12ms vs 45+ SQL joins). ChromaDB stores code embeddings for MemCore's semantic memory." |
| **Stream Processing** | "PulseGrid processes 10,000 engineering events per minute through Kafka. I partitioned topics by organization_id to guarantee in-order processing per organization. The Python consumer uses async Kafka client — I measured consumer lag under load: peak 1.8 seconds, steady state 0.2 seconds. I documented the lag spike during Kafka consumer group rebalance as a postmortem." |
| **ML Engineering** | "I built three ML pipelines: SentinelGrid's anomaly detector (LSTM autoencoder, weekly retraining from TimescaleDB), PulseGrid's risk classifier (XGBoost, AUC 0.82, trained on 18 months of incident history), and MemCore's bug pattern model (CodeBERT embeddings + ChromaDB). All pipelines include data collection, training, evaluation, and automated deployment." |
| **LLM Integration** | "I integrated the Claude API into PulseGrid's postmortem generator. The key insight: LLMs hallucinate when asked open questions. I structured the prompt as a template with 8 slots pre-filled from retrieved data sources — the LLM only reasons and writes, it does not retrieve. This eliminated factual errors in postmortems. I also use chain-of-thought prompting in MemCore's fix suggestion engine." |
| **Observability** | "All four projects use structured JSON logging, Prometheus metrics, and Grafana dashboards. I wrote 15 runbooks across all projects. I ran 4 postmortem exercises, simulating production incidents and writing full postmortems with timelines, root causes, and corrective actions. I also ran an on-call simulation: intentionally broke 2 systems and diagnosed them using only runbooks and dashboards, without looking at source code." |
| **PCB Design** | "I designed SentinelNode's 4-layer PCB in KiCad. Revision 1 had EMI problems — switching regulator noise at 2MHz coupled into the ADC. Identified with oscilloscope FFT function. Revision 2: separated analog/digital ground planes, added LC filter, repositioned regulator. ADC noise floor improved 18dB. I designed manufacturing test points for ICT jig from revision 1." |
| **MemCore SDK** | "MemCore is a Python SDK that gives any application persistent debugging intelligence. It hooks Python's exception system, intercepts logs, parses source code AST with tree-sitter, embeds function semantics with CodeBERT, stores in ChromaDB, and when bugs occur, retrieves similar past bugs and generates fix suggestions via Claude API. On InfraMesh, suggestion acceptance rate reached 73% after 30 days. I also built a 400-line C version for firmware systems." |
| **Documentation** | "Every project has: README with architecture diagram, ARCHITECTURE.md with system design, API.md with Swagger link, DATABASE.md with schema decisions, BENCHMARKS.md with measured numbers, RUNBOOK.md with on-call procedures, ADR/ folder with technical decisions, and POSTMORTEMS/ with incident analyses. My GitHub commit history shows 420+ daily commits across all projects." |

---

# FINAL MENTAL PICTURE (Day 420)

When you close your eyes after completing this roadmap, this is the complete picture you should see:

**Physical Layer:** A matchbox-sized PCB (SentinelNode) mounted on a motor in a factory. Four sensors connected via SPI and I2C to an ESP32-S3. A LiPo battery. A LoRa antenna. Power LED.

**Firmware Layer:** Seven FreeRTOS tasks running simultaneously on two CPU cores. Sensor data flowing through DMA into ring buffers. FFT computed on raw vibration. 15 features extracted. INT8 model producing anomaly score in 47ms. All of this happening while MQTT publishes, OTA checks for updates, and the hardware watchdog is fed.

**Communication Layer:** MQTT messages flowing over WiFi with QoS 1 and TLS to a Raspberry Pi gateway. If WiFi fails, messages stored in SPI flash. On reconnect, chronological delivery. Gateway bridges to AWS IoT Core.

**Cloud Layer:** Kinesis ingesting 10,000 events per minute. Lambda processing and writing to TimescaleDB. SageMaker retraining the model weekly. CloudFront distributing new firmware to 1000 nodes simultaneously. Grafana showing the operations team which machines need attention.

**Engineering Intelligence Layer:** PulseGrid watching every PR, every deployment, every incident across the engineering organization. Risk scores posted to PRs. Dependency graph updating from live traces. Postmortem drafts appearing 5 minutes after incidents resolve.

**Self-Healing Layer:** MemCore embedded in all three projects. Learning what normal looks like. Storing bug vocabulary. When something breaks, retrieving similar past bugs and suggesting fixes with historical context.

**Documentation Layer:** 420 days of daily commits. Every decision documented in ADRs. Every incident documented in postmortems. Every benchmark measured and recorded. Every API documented in Swagger.

**This is not a student project. This is engineering.**

---

# THE DAILY HABIT (Never Skip)

```
Every single day, regardless of what you learned:

1. Open GitHub
2. Write something — even one sentence — about what you learned
3. Commit it with a meaningful message
4. Push

After 420 days, your GitHub shows 420 consecutive commits.
No interviewer can fake 420 days of consistent work.
That history is your most valuable credential.
```