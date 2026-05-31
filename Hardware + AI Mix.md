# Hardware + AI Mix — Zero to MNC Standard
## Complete Fresher Roadmap | Mental Model | Architecture Layers | Subtopic Tables | Mini Projects | MNC vs Amateur

---

# PART 0 — THE MENTAL MODEL BEFORE ANYTHING ELSE

Before you touch a single component or write a single line of code, you need to understand the complete picture. This section explains the entire hardware-AI system using real-world analogies so your brain has a map before it starts filling in details.

---

## 0.1 — The Hospital Analogy (Read This First)

Imagine a large hospital that monitors hundreds of patients simultaneously.

Each patient has medical devices attached — a heart monitor, a temperature sensor, a blood pressure cuff. These devices measure the patient's condition continuously. Inside each device is a small computer that reads those measurements every second. That small computer runs a program that tells it when to read, how to store the reading, and when to send an alert. When a reading looks dangerous, the device itself can sound a local alarm without waiting for the main hospital computer to respond. All the readings from all devices in one ward are collected at the nurses' station. From the nurses' station, all data goes to the hospital's central server. Doctors view patient history, trends, and alerts on screens. The hospital can update the software on all devices at once without replacing them. Hospital administrators can tell instantly if any device is malfunctioning without physically checking each room.

Now replace the words:

| Hospital Word | Hardware-AI Word |
|---------------|-----------------|
| Patient | Industrial machine (motor, conveyor, pump) |
| Medical device (heart monitor) | Sensor node (SentinelNode) |
| Small computer inside device | Microcontroller (STM32, ESP32) |
| Program inside device | Firmware (Embedded C + FreeRTOS) |
| Device sounding local alarm | Edge AI inference (TFLite Micro) |
| Nurses' station | Gateway (Raspberry Pi) |
| Hospital central server | Cloud (AWS IoT Core + TimescaleDB) |
| Doctor's screen | Dashboard (Grafana) |
| Updating software remotely | OTA (Over-The-Air) firmware update |
| Knowing if device malfunctions | Observability (device health metrics) |

This is SentinelGrid. This is what you are building. Every skill you learn exists because this system needs it.

---

## 0.2 — The 9 Layers of a Hardware-AI System

A complete hardware-AI system has exactly 9 layers. Each layer depends on the one below it. You cannot skip a layer. You cannot understand layer 5 before understanding layer 3.

```
LAYER 9 — FLEET MANAGEMENT
         Managing thousands of devices remotely
         (OTA updates, firmware deployment, device provisioning)
              │
              │ depends on
              ▼
LAYER 8 — CLOUD + BACKEND
         Storing, processing, and analyzing telemetry at scale
         (AWS IoT Core, TimescaleDB, FastAPI, ML training pipeline)
              │
              │ depends on
              ▼
LAYER 7 — GATEWAY
         Aggregating data from all nodes in a zone
         (Raspberry Pi, Mosquitto broker, local buffering)
              │
              │ depends on
              ▼
LAYER 6 — IoT COMMUNICATION
         How data travels from node to gateway to cloud
         (MQTT protocol, WiFi, LoRa, store-and-forward)
              │
              │ depends on
              ▼
LAYER 5 — EDGE AI + SIGNAL PROCESSING
         Intelligence running locally on the node
         (FFT, feature extraction, TFLite Micro, INT8 quantization)
              │
              │ depends on
              ▼
LAYER 4 — RTOS + FIRMWARE ARCHITECTURE
         The software that manages all tasks on the microcontroller
         (FreeRTOS, tasks, queues, semaphores, OTA logic)
              │
              │ depends on
              ▼
LAYER 3 — EMBEDDED C + MICROCONTROLLER
         The programming language and chip that runs firmware
         (C programming, ARM Cortex-M, STM32/ESP32, interrupts, DMA)
              │
              │ depends on
              ▼
LAYER 2 — DIGITAL HARDWARE + PROTOCOLS
         How the microcontroller talks to sensors
         (SPI, I2C, UART, GPIO, ADC, digital logic)
              │
              │ depends on
              ▼
LAYER 1 — ELECTRONICS FUNDAMENTALS + PCB
         The physical world — electrons, components, circuits, boards
         (Voltage, current, resistors, capacitors, schematics, PCB design)
```

---

## 0.3 — Where Each Layer Lives in SentinelGrid

```
[CLOUD — Layer 8+9]
AWS IoT Core ──► Kinesis ──► Lambda ──► TimescaleDB ──► Grafana
      │                                                     │
      │ MQTT over TLS                          FastAPI API  │
      ▼                                                     ▼
[GATEWAY — Layer 7]                              [Dashboard — Layer 8]
Raspberry Pi                                     Engineer's Browser
Mosquitto Broker
Python Pipeline
Local InfluxDB Buffer
      │
      │ MQTT over WiFi/LoRa (Layer 6)
      ▼
[SentinelNode — Layers 1 through 5]
┌─────────────────────────────────────────┐
│  LAYER 5 — Edge AI                      │
│  TFLite Micro → Anomaly Score           │
│           │                             │
│  LAYER 5 — Signal Processing            │
│  FFT → Frequency Features               │
│           │                             │
│  LAYER 4 — FreeRTOS                     │
│  Sensor Task | AI Task | Comms Task     │
│           │                             │
│  LAYER 3 — Embedded C on ESP32-S3       │
│  DMA │ Interrupts │ SPI │ I2C           │
│           │                             │
│  LAYER 2 — Sensor Interfaces            │
│  ADXL355 │ INA226 │ MLX90614           │
│           │                             │
│  LAYER 1 — PCB + Electronics            │
│  Power supply │ Ground planes │ Traces  │
└─────────────────────────────────────────┘
```

---

## 0.4 — What Each Layer Breaks Without

| Layer | If This Layer Is Missing | What Breaks |
|-------|--------------------------|-------------|
| Layer 1 — Electronics | No physical circuit | Nothing exists. The node is not a device. |
| Layer 2 — Digital HW | Cannot read sensors | Microcontroller has no data to process |
| Layer 3 — Embedded C | No program runs | Chip is a piece of silicon doing nothing |
| Layer 4 — RTOS | One task blocks all others | Reading sensor freezes communication |
| Layer 5 — Edge AI | No local intelligence | Network outage = zero anomaly detection |
| Layer 6 — IoT Comms | Data stays on node | Cloud never receives telemetry |
| Layer 7 — Gateway | Each node talks to cloud separately | Cloud overwhelmed, no local aggregation |
| Layer 8 — Cloud | Data never stored or analyzed | No history, no ML, no dashboards |
| Layer 9 — Fleet Mgmt | Cannot update remote devices | A firmware bug in 1000 nodes requires physical access |

---

## 0.5 — How Each Layer Connects to the Next

```
Electronics (Layer 1)
  → defines the physical components on the PCB
  → those components have interfaces (SPI pins, I2C pins)

Digital Hardware (Layer 2)
  → defines how the microcontroller talks to those interfaces
  → SPI driver reads ADXL355 register 0x08 to get X-axis sample

Embedded C + MCU (Layer 3)
  → the C code that implements those drivers
  → also manages interrupts when new data is ready

RTOS (Layer 4)
  → organizes WHEN that C code runs
  → sensor reading task runs every 1ms, comms task runs every 5 seconds
  → without RTOS they would interfere with each other

Edge AI + Signal Processing (Layer 5)
  → takes the raw samples from the sensor task
  → computes FFT → extracts features → runs TFLite model
  → outputs anomaly score

IoT Communication (Layer 6)
  → takes the anomaly score and raw telemetry
  → packages as MQTT message and publishes to gateway

Gateway (Layer 7)
  → receives MQTT messages from all nodes
  → aggregates, buffers locally, forwards to cloud

Cloud (Layer 8)
  → stores every reading in TimescaleDB
  → runs retraining pipeline when model drifts
  → sends alerts to engineers

Fleet Management (Layer 9)
  → pushes new firmware or model to all nodes
  → monitors which nodes are healthy
  → handles staged rollout
```

---

# PART 1 — ELECTRONICS FUNDAMENTALS
## Architecture Position: Layer 1 — The Physical Foundation

**Why This Comes First:** Every component on a PCB, every sensor, every power supply, every trace on the board obeys the laws of electronics. You cannot select components, read datasheets, or understand PCB design without this foundation. This is not optional background knowledge — it is the literal physics that your hardware runs on.

**What SentinelGrid Needs From This:** SentinelNode has a power supply circuit, sensor components, protection circuits, and signal traces. Understanding what each one does and why it is there requires electronics fundamentals.

---

### Subtopic Table — Part 1

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 1.1 | Voltage, Current, Resistance | Ohm's Law (V=IR), what voltage is (electrical pressure), what current is (flow of charge), what resistance does (opposes flow) | Why a 3.3V supply cannot directly power a 5V sensor. Why a resistor limits LED current | If you connect a 3.3V supply to an LED with forward voltage 2V, what happens without a resistor? |
| 1.2 | Power and Energy | P=VI, milliwatts vs watts, why power matters for battery life | Why a WiFi radio transmitting at 200mA from 3.3V drains a battery 10x faster than a sleeping sensor | SentinelNode runs on a 2000mAh battery. WiFi active = 300mA. How many hours does it last at full WiFi? |
| 1.3 | Series and Parallel Circuits | Voltage dividers (series), current sharing (parallel), total resistance calculation | How a resistor voltage divider reads a battery level using an ADC input | Design a voltage divider that reads a 4.2V LiPo battery using a 3.3V ADC input |
| 1.4 | Capacitors | Storing charge, filtering noise, decoupling, bypass capacitors | Why every IC power pin needs a 100nF capacitor right next to it — without it, the chip sees noisy supply voltage and malfunctions | What is a decoupling capacitor and where does it go relative to the IC power pin? |
| 1.5 | Resistors in Practice | Pull-up, pull-down, current limiting, voltage divider | Why I2C lines need pull-up resistors — without them the bus floats and data is corrupted | An I2C bus has no pull-up resistor. What does the logic analyzer show? |
| 1.6 | Inductors and Ferrite Beads | Storing energy in magnetic field, opposing changes in current, filtering high-frequency noise | Why switching regulators use inductors, why a ferrite bead on a power line blocks RF noise | Why does the expert mention a ferrite bead on the power line in the interview question at 00:18? |
| 1.7 | Diodes and ESD Protection | One-way current flow, protection diodes, ESD (ElectroStatic Discharge) protection | Why sensor input pins need ESD protection — static electricity from a human touch destroys unprotected inputs | What happens to an unprotected sensor pin when a technician touches it with a charged finger? |
| 1.8 | Schematic Reading | Standard symbols for all components, how to trace signal flow, power rails, component labels | Read a complete SentinelNode schematic and identify every section: power supply, MCU, sensor interfaces, protection circuits | Given a partial schematic, identify the power regulation section and explain what each component does |
| 1.9 | Power Supply Design | Linear regulators vs switching regulators, LDO regulators, efficiency, noise characteristics | Why the SentinelNode uses an LDO regulator for the analog sensor section but a switching regulator for the main 3.3V rail | A switching regulator creates noise. Why is it used at all instead of a quiet linear regulator? |
| 1.10 | Signal Integrity Basics | What happens when signals travel through wires and PCB traces, reflections, impedance, termination | Why the oscilloscope showed ringing (overshoot) in the interview — and why a series resistor fixes it | A digital signal has significant ringing at each edge. What physical phenomenon causes this? |

---

### Mini Project — Part 1

**Amateur Implementation:**
Breadboard a circuit that lights two LEDs at different brightnesses using resistors. Connect a potentiometer and watch the LED brightness change.

**MNC-Level Difference:**
A professional engineer documents this as a design verification. They calculate the expected current through each LED from V=IR, measure it with a multimeter, record the deviation from expected value, and write a one-paragraph explanation of why the deviation exists (component tolerance). They also add a decoupling capacitor to the power supply line and compare the voltage rail with an oscilloscope with and without it — showing the noise reduction. This is not a different circuit. It is a different way of thinking about and documenting what the circuit does.

**GitHub Proof:** Push a folder called `01-electronics-fundamentals/` with: calculation sheet as markdown, oscilloscope screenshots (with decoupling cap vs without), multimeter readings, and a `LEARNINGS.md` explaining what each reading means physically.

---

### Connection From Part 1 to Part 2

You now understand that components exist, that signals flow through circuits, and that the physical world has constraints. The next question is: how does a microcontroller talk to these physical components? The digital protocols — SPI, I2C, UART — are the language the microcontroller uses to send commands to sensors and receive data from them. Understanding those protocols requires knowing that signals are voltages that change over time, which you now know from Part 1.

---

# PART 2 — DIGITAL HARDWARE AND COMMUNICATION PROTOCOLS
## Architecture Position: Layer 2 — Sensor Interface

**Why This Comes Second:** A microcontroller is useless without input. Sensors produce data in the physical world. The protocols in this part are the agreed-upon electrical languages that microcontrollers and sensors use to exchange information. Without these, Layer 3 has nothing to process.

**What SentinelGrid Needs From This:** The ADXL355 accelerometer connects via SPI. The INA226 current sensor connects via I2C. Debug logging goes over UART. The ADC reads the gas sensor and battery voltage. Every sensor interface on SentinelNode uses one of these protocols.

---

### Subtopic Table — Part 2

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 2.1 | Binary and Digital Logic | Bits, bytes, binary numbers, HIGH/LOW voltage levels, logic 1 vs 0 | Why 0x08 in a sensor register means something specific, why bit manipulation matters in firmware | An accelerometer register reads 0b10110000. What does bit 5 being set mean? |
| 2.2 | GPIO (General Purpose Input/Output) | Digital input and output pins, configuring as input or output, reading and writing pin state | Control an LED from code, read a button press, understand why sensors use dedicated pins for signals | How do you configure a GPIO pin to detect when the accelerometer has new data ready? |
| 2.3 | UART (Universal Asynchronous Receiver Transmitter) | Serial communication, baud rate, TX and RX pins, no clock line, start/stop bits | Send debug messages from firmware over UART to see what your code is doing | Why does UART not need a clock signal? What does asynchronous mean? |
| 2.4 | SPI Protocol | Master-slave, 4 wires (MOSI, MISO, SCK, CS), full-duplex, clock-controlled | Read and write registers on the ADXL355 accelerometer — this is the exact interface used in SentinelNode | Why does SPI need 4 wires while I2C only needs 2? What is the trade-off? |
| 2.5 | I2C Protocol | Two wires (SDA, SCL), device addressing, ACK/NACK, pull-up requirements | Interface multiple sensors on one bus — INA226, MLX90614, and others sharing the same 2 wires | Why does I2C need pull-up resistors? What happens without them? |
| 2.6 | ADC (Analog to Digital Converter) | Resolution (8-bit, 12-bit, 16-bit), reference voltage, sampling rate, quantization error | Convert the analog output of a gas sensor to a digital number the microcontroller can process | A 12-bit ADC with 3.3V reference reads 2048. What voltage is this? |
| 2.7 | PWM (Pulse Width Modulation) | Duty cycle, frequency, controlling power with digital signals | Control motor speed with a PWM signal, understand how switching regulators work | How does PWM allow a digital output to simulate an analog signal? |
| 2.8 | Protocol Selection | When to use SPI vs I2C vs UART vs CAN, trade-offs of each | Understand why SentinelNode uses SPI for the high-speed accelerometer but I2C for the slower temperature sensor | The vibration sensor samples at 4kHz. Why is SPI chosen over I2C for this? |
| 2.9 | Logic Analyzer Usage | Capturing protocol waveforms, decoding SPI and I2C transactions, verifying register writes | Verify that your SPI driver is actually sending the correct bytes to the sensor | You think your driver configures the accelerometer for ±2g range. How do you verify without a datasheet register check? |
| 2.10 | Timing Diagrams | Reading timing requirements from datasheets, setup time, hold time, clock polarity | Understand why an SPI clock that is too fast causes corrupted readings | Your SPI driver reads garbage from the sensor. The datasheet shows a maximum clock of 10MHz. Your SPI clock is 20MHz. What happens? |

---

### Mini Project — Part 2

**Amateur Implementation:**
Connect an I2C temperature sensor (MPU6050 or DHT sensor) to an Arduino. Print temperature readings to serial monitor. Code copied from a tutorial.

**MNC-Level Difference:**
A professional engineer uses a logic analyzer to capture the I2C transaction. They verify the device address byte, the register address byte, and the data bytes match exactly what the datasheet says should happen. They document: the expected waveform from the datasheet, the actual captured waveform, and confirm they match. They then deliberately introduce a fault — remove one pull-up resistor — capture the resulting corrupted waveform on the logic analyzer, and document what a missing pull-up looks like. They write a `DEBUGGING.md` entry titled "I2C bus missing pull-up — symptom and diagnosis." This debugging evidence is the difference between someone who got it working and someone who understands why it works.

**GitHub Proof:** Push `02-digital-protocols/` with: logic analyzer screenshots of SPI and I2C transactions, protocol timing verification against datasheet, a fault injection experiment (missing pull-up), and register read/write verification.

---

### Connection From Part 2 to Part 3

You can now read sensor data using protocols. But reading data in a loop without structure is bare metal programming — one function running sequentially. This breaks the moment you need to read a sensor AND send data AND check for updates AND manage power simultaneously. Part 3 gives you the language (C) and the machine (microcontroller) that makes structured firmware possible. The protocols you just learned become drivers — C functions that implement SPI and I2C in code.

---

# PART 3 — EMBEDDED C AND MICROCONTROLLER ARCHITECTURE
## Architecture Position: Layer 3 — Processing Core

**Why This Comes Third:** The microcontroller is the brain of SentinelNode. Embedded C is the language that runs on that brain. Without this, you have physical sensors producing data that nobody reads. With this, you can read sensors, make decisions, control outputs, and prepare data for everything above.

**What SentinelGrid Needs From This:** All SentinelNode firmware is written in C running on an ESP32-S3. The sensor drivers, DMA configuration, interrupt handlers, sleep mode management, bootloader interaction — all of this is Embedded C.

---

### Subtopic Table — Part 3

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 3.1 | C Language Fundamentals | Variables, data types, operators, control flow, functions, arrays, strings | Write a C function that takes an array of ADC readings and returns the average | What is the difference between `int` and `uint16_t`? Why does embedded code prefer fixed-width types? |
| 3.2 | Pointers and Memory | Pointers, pointer arithmetic, pass by value vs reference, memory layout (stack, heap, global) | Understand why embedded code avoids dynamic memory allocation (malloc) and uses static buffers | Why is `malloc()` dangerous in embedded firmware? What happens if it fails at 3 AM in a factory? |
| 3.3 | Structs and Bit Fields | Grouping related data, bit manipulation, packing sensor register maps into structs | Map the ADXL355 register layout to a C struct — this is exactly how embedded drivers are written | An accelerometer status register has bits [7:4] as reserved, bit 3 as data-ready, bits [2:0] as error flags. Write a C struct for this |
| 3.4 | Volatile Keyword | Why the compiler needs to be told not to optimize certain variables, ISR and main loop sharing data | Understand why every variable shared between an interrupt and main code must be volatile | Without volatile, what does the compiler optimize away and what bug does this create? |
| 3.5 | Interrupts | What an interrupt is, interrupt service routine (ISR), interrupt priority, critical sections | Implement a data-ready interrupt for the ADXL355 — every new sample triggers an ISR that copies data to a buffer | An ISR runs when the sensor has new data. The ISR takes 50 microseconds. Samples arrive every 1 millisecond. What percentage of CPU time is in the ISR? |
| 3.6 | ARM Cortex-M Architecture | Stack, program counter, link register, vector table, fault types (HardFault, BusFault, UsageFault) | Understand crash reports — when firmware crashes, the saved PC and LR tell you exactly where it crashed | Firmware crashes with HardFault. The program counter shows address 0x2001FF00. The MCU RAM ends at 0x20020000. What happened? |
| 3.7 | DMA (Direct Memory Access) | What DMA is, DMA channels, transfer complete interrupt, circular mode for continuous ADC | Configure DMA to move ADC samples to a memory buffer automatically — this is exactly how SentinelNode reads vibration at 1kHz | Without DMA, reading 1000 ADC samples per second at 12 bits each, how many CPU instruction cycles are wasted on data copying? |
| 3.8 | Timers and PWM | Hardware timers, timer interrupt, generating precise time delays, PWM generation | Create a 1kHz timer interrupt that triggers sensor sampling without blocking the main program | Why use a hardware timer for 1kHz sampling instead of a delay loop? |
| 3.9 | Sleep Modes and Power | MCU sleep states, wake-up sources, current consumption in each mode, RTC for periodic wake | Calculate battery life for a node that sleeps for 55 seconds, wakes for 5 seconds, samples sensors, transmits | SentinelNode in active mode draws 80mA. In deep sleep it draws 10µA. It wakes every 60 seconds for 2 seconds. Average current? |
| 3.10 | Debugging with JTAG and GDB | Setting breakpoints, stepping through code, inspecting memory, reading registers | Debug a sensor driver without print statements — see the actual SPI byte sequence in memory while it executes | Print statements change timing and hide race conditions. How do you debug a race condition without printf? |
| 3.11 | JTAG and OpenOCD | Connecting hardware debugger to MCU, loading firmware, setting breakpoints from command line | Debug real hardware from a computer without modifying code timing | What is the difference between a hardware breakpoint and a software breakpoint in embedded systems? |
| 3.12 | ESP-IDF or STM32 HAL | Framework that abstracts hardware registers into C functions, peripheral initialization | Initialize SPI, I2C, ADC, GPIO, UART using framework functions rather than raw register manipulation | Why use HAL functions instead of writing directly to hardware registers? What does HAL trade off? |

---

### Mini Project — Part 3

**Amateur Implementation:**
Blink an LED. Read an accelerometer over SPI. Print values to serial. Everything in one while loop.

**MNC-Level Difference:**
A professional engineer writes a structured sensor driver with: initialization function, data-read function, error return codes (not just printing errors — returning them), interrupt-driven reading using DMA, and a test harness that verifies the driver works correctly by reading a known register value (the device ID register that always returns a fixed value). They write a driver specification document: what the driver expects, what it returns, what happens on error, what it does NOT handle (things the calling code must handle). They measure actual current consumption in active vs sleep mode using a multimeter in series with the power supply and document it in `POWER.md`. This is engineering, not following a tutorial.

**GitHub Proof:** Push `03-embedded-c/` with: structured sensor driver with header file and implementation file, DMA configuration code, power consumption measurements, GDB debugging session logs showing register states, and `DRIVER_SPEC.md` documenting the API.

---

### Connection From Part 3 to Part 4

You can now read sensor data in C code running on a microcontroller. But what happens when you need to read sensors AND communicate over WiFi AND check for OTA updates AND manage a BLE configuration interface simultaneously? If one task blocks, all others stop. This is the problem bare metal solves poorly and RTOS solves cleanly. Part 4 introduces FreeRTOS — the traffic manager that gives each concern its own lane.

---

# PART 4 — RTOS AND FIRMWARE ARCHITECTURE
## Architecture Position: Layer 3–4 — The Operating System of the Node

**Why This Comes Fourth:** Real embedded systems do many things simultaneously. A sensor must be read while data is being transmitted while OTA update status is checked while a watchdog is being fed. Without an RTOS, these concerns fight each other. FreeRTOS gives each concern its own task and manages their execution.

**What SentinelGrid Needs From This:** SentinelNode runs 7 FreeRTOS tasks simultaneously. The architecture of these tasks, how they communicate through queues, and how failures are handled through watchdogs is the core firmware architecture of SentinelGrid.

---

### Subtopic Table — Part 4

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 4.1 | Why RTOS Exists | What preemptive multitasking is, why bare metal loops fail for multi-concern systems, what scheduler does | Explain why a sensor-reading delay blocks WiFi transmission in bare metal and how RTOS prevents this | In bare metal, WiFiTransmit() takes 200ms. SensorRead() must happen every 1ms. What breaks? |
| 4.2 | FreeRTOS Tasks | Creating tasks, task function signature, task priority, task states (running, ready, blocked, suspended) | Create three tasks that run concurrently — sensor reading, LED blinking, and UART logging — with correct priorities | Sensor task has priority 3. Comms task has priority 2. Both are ready. Which runs first? |
| 4.3 | FreeRTOS Queues | Creating queues, sending to queue, receiving from queue, queue full behavior, blocking vs non-blocking reads | Build a producer-consumer pipeline: sensor task puts raw data in a queue, processing task reads from queue | Sensor task fills a queue of 10 items. Processing task is slower. What happens when queue is full? |
| 4.4 | Semaphores and Mutex | Binary semaphore (signal between tasks), counting semaphore, mutex (protect shared resource), priority inversion | Protect a shared SPI bus used by two tasks — without mutex, both tasks corrupt each other's transactions | Two tasks share the SPI bus. Without a mutex, task A's SPI transaction is interrupted halfway by task B. What does the sensor receive? |
| 4.5 | Task Stack and Heap | Stack size per task, stack overflow causes and detection, heap allocation in FreeRTOS | Calculate minimum stack size for a task by running it and measuring actual usage with watermark API | A task has 512 bytes of stack. During development it seems fine. In production it crashes randomly. Stack watermark shows minimum free = 8 bytes. What does this mean? |
| 4.6 | Watchdog Timer | Hardware watchdog, software watchdog, task watchdog in ESP-IDF, feeding watchdog, reset on hang | Implement a watchdog that resets the node if any task hangs for more than 5 seconds — critical for unattended production nodes | A WiFi task hangs waiting for a connection that never comes. The rest of the system still works. Hardware watchdog resets everything. Is this the right behavior? |
| 4.7 | Memory Protection Unit | MPU regions, catching stack overflow immediately, preventing one task from corrupting another's memory | Configure MPU on STM32 to catch stack overflows with a hard fault instead of silent memory corruption | Without MPU, a stack overflow overwrites the memory of an adjacent variable. What symptom does the engineer see? Why is it hard to diagnose? |
| 4.8 | Event Groups and Notifications | Task notification (lightweight signal), event groups (multiple flags), waiting for multiple events | Synchronize the OTA task so it only starts when WiFi is connected AND the current OTA window allows it | OTA task must wait until: WiFi connected AND no active transmission AND battery above 20%. How do you express this with event groups? |
| 4.9 | FreeRTOS Debugging | Stack watermark API, task list printing, heap remaining, runtime statistics, task state inspection | Diagnose a system that reboots randomly by checking stack watermarks and heap free space after 24 hours of operation | After 24 hours, heap free space has decreased from 80KB to 2KB. What type of bug causes this? |
| 4.10 | OTA Architecture (Firmware Level) | A/B partition layout, bootloader logic, download to inactive partition, signature verification, boot count, rollback | Understand the complete OTA flow from receiving a download command to safely applying a new firmware version | New firmware is downloaded and verified. The bootloader switches to it. On first boot, the new firmware crashes. What should happen next? |
| 4.11 | Power Management in RTOS Context | Tickless idle, task-based sleep decisions, preventing sleep when tasks are active | Implement dynamic power management: node sleeps when all tasks are idle, wakes on timer or interrupt | The WiFi transmission task takes 2 seconds every 60 seconds. How does FreeRTOS handle CPU power during the 58-second gap? |

---

### Mini Project — Part 4

**Amateur Implementation:**
Create two FreeRTOS tasks, one blinks an LED, one prints to serial. Observe they run "simultaneously."

**MNC-Level Difference:**
A professional engineer builds the complete SentinelNode task architecture: sensor task (highest priority, interrupt-driven), signal processing task (medium priority, reads from sensor queue), communication task (lower priority, sends results), OTA task (lowest priority, background), watchdog feed task (runs on timer, verifies all other tasks check in). They deliberately induce a task hang by inserting an infinite loop in one task and verify the watchdog resets the system. They document stack watermarks for all tasks in `FIRMWARE.md`. They measure heap usage at startup, after 1 hour, and after 24 hours to verify no memory leak. The document `RTOS_TASK_DESIGN.md` explains why each task has its priority and what happens if any task is delayed.

**GitHub Proof:** Push `04-rtos/` with: complete 5-task firmware, stack watermark measurements, watchdog test (hang injection + reset verification), heap leak test over 24 hours, `RTOS_TASK_DESIGN.md`.

---

### Connection From Part 4 to Part 5

You now have a node that reads sensor data reliably, manages multiple concerns simultaneously, and is resilient to individual task failures. The raw sensor data — 1000 samples per second of vibration — is sitting in a queue. But raw samples from an accelerometer are not useful directly for detecting failures. A bearing failure does not show up as "high acceleration" — it shows up as specific frequencies in the vibration signal. Part 5 teaches you to transform raw data into meaningful features that can feed an AI model.

---

# PART 5 — SIGNAL PROCESSING AND FEATURE EXTRACTION
## Architecture Position: Layer 5 — Intelligence Input

**Why This Comes Fifth:** An AI model cannot be fed raw accelerometer samples and detect bearing failures. The AI model needs pre-processed features — frequency content, energy in specific bands, statistical properties of the signal. Signal processing is the translation layer between raw physics and machine intelligence.

**What SentinelGrid Needs From This:** The SentinelNode processing task takes 1000 vibration samples, applies an FFT, extracts 15 numerical features, and passes them to the edge inference task. This processing pipeline is entirely signal processing.

---

### Subtopic Table — Part 5

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 5.1 | Sampling Theory | Nyquist theorem, aliasing, why sampling rate must be at least 2× the highest frequency of interest | Why SentinelNode samples vibration at 1kHz — to capture frequencies up to 500Hz where bearing damage signatures appear | A bearing fault frequency is 350Hz. What is the minimum sampling rate? What does aliasing look like in an FFT? |
| 5.2 | Time Domain Analysis | Mean, variance, RMS (Root Mean Square), peak, peak-to-peak, kurtosis | Detect sudden impacts (high kurtosis) and overall vibration level (RMS) from raw samples — both useful fault indicators | An accelerometer normally shows RMS of 0.5g. After one week it shows 2.1g. What does this indicate? |
| 5.3 | FFT (Fast Fourier Transform) | What FFT does (converts time-domain to frequency-domain), frequency bins, FFT output interpretation | See a frequency spectrum of vibration data and identify the rotation frequency, its harmonics, and fault frequencies | An FFT of motor vibration shows a spike at 29.5Hz and smaller spikes at 59Hz, 88.5Hz. The motor rotates at 1770 RPM. What do these frequencies represent? |
| 5.4 | Windowing | Why FFT requires windowing (Hann, Hamming, Blackman windows), spectral leakage | Apply a Hann window before FFT to reduce spectral leakage and get cleaner frequency resolution | Without windowing, a pure 100Hz sine wave shows energy at many frequencies in the FFT. Why? What does windowing fix? |
| 5.5 | Frequency Domain Feature Extraction | Energy in frequency bands, dominant frequency, spectral centroid, frequency ratio features | Extract 8 frequency-domain features from an FFT output that capture the characteristics of bearing fault signatures | A bearing fault produces energy at 87Hz. How do you design a feature that captures energy specifically in the 80–95Hz band? |
| 5.6 | Digital Filters | Low-pass filter, high-pass filter, band-pass filter, IIR vs FIR, implementing on microcontroller | Filter high-frequency noise from ADC readings using a low-pass filter — reduces false anomaly detections | An accelerometer is sampling at 1kHz. High-frequency electrical noise above 400Hz contaminates the signal. Design a filter to remove it |
| 5.7 | Normalization and Scaling | Z-score normalization, min-max scaling, why ML models need normalized inputs | Normalize features to zero mean and unit variance — required before feeding data to any ML model | Why does a feature with range 0–1000 dominate a feature with range 0–1 in a neural network? What does normalization fix? |
| 5.8 | Sliding Window | Fixed-size window over streaming data, overlap percentage, computational cost vs temporal resolution | Process a continuous stream of 1kHz samples in 1-second windows with 50% overlap — this is the exact pipeline in SentinelNode | A 1-second window gives frequency resolution of 1Hz. A 0.5-second window gives 2Hz. What do you trade off by using shorter windows? |
| 5.9 | Computing FFT on MCU | Fixed-point FFT libraries (CMSIS-DSP), memory layout, integer vs float FFT, computational cost | Run a 1024-point FFT on an ESP32-S3 and measure how long it takes — this directly determines inference pipeline latency | A 1024-point FFT takes 12ms on your MCU. The sensor produces a new window every 1000ms. Is this computationally feasible? |
| 5.10 | Feature Vector Creation | Combining time-domain and frequency-domain features into a fixed-length vector for ML input | Create a 15-element feature vector from one second of vibration data: 5 time-domain features + 10 frequency features | Your feature vector has 15 elements. The TFLite model expects 15 float inputs. How do you pass the feature vector to the model? |

---

### Mini Project — Part 5

**Amateur Implementation:**
Collect vibration data from an accelerometer, plot the FFT in Python, observe the frequency peaks.

**MNC-Level Difference:**
A professional engineer builds a complete signal processing pipeline in Python first (as a reference implementation), then re-implements the same pipeline in C for the MCU. They verify both implementations produce identical output on the same input data (within floating-point tolerance). They collect vibration data from a real motor in two states — normal operation and with a deliberately introduced bearing fault (a small scratch on a bearing race) — and show that the FFT features distinguish the two states. This validation with real data is what makes the feature extraction design credible. They document the fault frequency calculation from motor shaft speed and bearing geometry in `SIGNAL_PROCESSING.md`.

**GitHub Proof:** Push `05-signal-processing/` with: Python FFT pipeline, C FFT implementation (CMSIS-DSP), validation showing both produce same output, real motor data comparison (normal vs fault), feature vector generator, `SIGNAL_PROCESSING.md` with fault frequency calculation.

---

### Connection From Part 5 to Part 6

You now have a 15-element feature vector produced every second from sensor data. This feature vector needs to be judged by an AI model — is it normal or anomalous? Part 6 teaches you how to build that AI model in Python, train it on historical data, quantize it, and deploy it onto the microcontroller so the judgment happens locally without any cloud connection.

---

# PART 6 — EDGE AI AND TINYML
## Architecture Position: Layer 5 — Local Intelligence

**Why This Comes Sixth:** This is the AI layer that runs on the hardware itself. The model receives the feature vector, produces an anomaly score, and makes a local decision. No network required. This is what makes SentinelGrid functional during network outages and what distinguishes it from a simple data logger.

**What SentinelGrid Needs From This:** SentinelNode runs a quantized INT8 TFLite model that takes the 15-element feature vector and outputs an anomaly score between 0 and 1. When score exceeds 0.75, the node flags the telemetry as critical and triggers a local alert.

---

### Subtopic Table — Part 6

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 6.1 | Python for Data and ML | NumPy arrays, Pandas DataFrames, Matplotlib plotting, scikit-learn basics | Load, clean, visualize, and process the vibration feature dataset | Your vibration CSV has 50,000 rows and 16 columns. How do you load it, check for missing values, and plot the distribution of each feature? |
| 6.2 | Anomaly Detection Concepts | Supervised vs unsupervised anomaly detection, autoencoder concept, reconstruction error | Understand why we train only on normal data — we do not need fault examples to detect faults | Why can you train an anomaly detector without any labeled fault examples? |
| 6.3 | Autoencoder Architecture | Encoder compresses input, decoder reconstructs, high reconstruction error = anomaly | Build a simple autoencoder in PyTorch or TensorFlow that learns to reconstruct normal vibration features | An autoencoder trained on normal data sees a fault feature vector. Why is its reconstruction error high? |
| 6.4 | Training and Evaluation | Train/validation/test split, loss curves, threshold selection on validation set, precision/recall trade-off | Train the autoencoder, select an anomaly threshold, evaluate on both normal and fault data | Your model has 99% anomaly detection rate but 20% false positive rate. What problem does this cause in production? |
| 6.5 | TensorFlow Lite Export | Saving TF model, converting to TFLite format, verifying TFLite output matches original | Export the trained autoencoder as a .tflite file and verify it produces the same anomaly scores | After TFLite export, anomaly scores are slightly different from the original model. What causes this? |
| 6.6 | Model Quantization (INT8) | Why quantize (size, speed on MCU), post-training quantization, representative dataset requirement, accuracy impact | Quantize the autoencoder to INT8, measure model size before and after, measure accuracy degradation | Float32 model: 180KB, 95% detection rate. INT8 model: 47KB, 91% detection rate. Is the 4% accuracy loss acceptable? What factors determine this? |
| 6.7 | TFLite for Microcontrollers | Memory arena, operator registration, input/output tensor handling, running inference | Deploy the quantized model to an ESP32-S3 and run inference on a real feature vector — measure the time it takes | TFLite Micro requires you to allocate a memory arena. You allocate 40KB. Inference fails with "arena too small." How do you find the correct size? |
| 6.8 | Inference Latency Measurement | Timing inference on real hardware, comparing INT8 vs float32 latency, acceptable latency for real-time detection | Measure inference latency precisely using hardware timer — this is a mandatory benchmark for any edge AI deployment | Your inference takes 47ms. Your feature extraction takes 12ms. A new feature window is ready every 1000ms. Is there a bottleneck? |
| 6.9 | Model OTA Architecture | Storing model in dedicated flash partition, updating model without firmware update, model versioning | Design the system where the cloud pushes an improved model to nodes without rebooting firmware | Firmware is at v2.3.1. Model is at v1.0.8. You retrain the model but not the firmware. How does the node receive and apply the new model? |
| 6.10 | Model Drift and Retraining | What model drift is (accuracy degrades when conditions change), monitoring drift, triggering retraining | Set up a system that detects when the edge model's anomaly scores diverge from the cloud model's scores and triggers retraining | After 3 months, the factory changes to a new type of bearing. The anomaly model starts raising false alarms constantly. What happened? What do you do? |

---

### Mini Project — Part 6

**Amateur Implementation:**
Train a neural network on a downloaded vibration dataset, get 90% accuracy, call it done.

**MNC-Level Difference:**
A professional engineer collects their own data from a real motor (using the SentinelNode hardware from Part 3), trains an autoencoder on 2 weeks of normal operation data, quantizes it to INT8, deploys it to the ESP32-S3, and measures: inference latency (47ms), model size (47KB), accuracy compared to cloud model (91% vs 95%). They document the accuracy trade-off in `EDGE_AI.md` and write a section called "Acceptable Accuracy Degradation" explaining why 91% at the edge is acceptable given the cloud model runs on the same data and catches what the edge model misses. They benchmark three different model architectures (autoencoder, 1D-CNN, isolation forest) and document why the autoencoder was chosen.

**GitHub Proof:** Push `06-edge-ai/` with: training pipeline in Python, quantization script, TFLite deployment code in C, inference latency benchmark results, accuracy comparison chart, `EDGE_AI.md` with architecture decision.

---

### Connection From Part 6 to Part 7

SentinelNode can now detect anomalies locally. But telemetry, anomaly scores, and device health data still need to travel from the node to the cloud. Part 7 covers the communication protocols — MQTT, WiFi, LoRa — that form the data highways between node, gateway, and cloud. The design decisions here (MQTT vs HTTP, QoS levels, offline buffering) directly determine whether data is lost during network failures.

---

# PART 7 — IoT COMMUNICATION PROTOCOLS
## Architecture Position: Layer 6 — Data Transport

**Why This Comes Seventh:** Data that stays on the node is useless for cloud analytics, fleet monitoring, or triggering maintenance work orders. The communication layer is what transforms individual smart nodes into a connected system. The choices made here — protocol, QoS, offline handling — determine whether the system is reliable or fragile.

**What SentinelGrid Needs From This:** Nodes publish MQTT messages to a local Mosquitto broker on the gateway. The gateway forwards to AWS IoT Core. QoS 1 ensures no telemetry is lost. SPI flash buffering ensures no data is lost during network outages.

---

### Subtopic Table — Part 7

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 7.1 | WiFi on ESP32 | Station mode, AP mode, connecting to access point, reconnection logic, signal strength (RSSI) | Connect an ESP32 to WiFi, handle disconnection gracefully without blocking other tasks | WiFi drops for 30 seconds. Your communication task is blocking on WiFi. What happens to sensor reading during those 30 seconds? |
| 7.2 | MQTT Protocol Fundamentals | Publish-subscribe model, topics, broker, client, retained messages, will messages | Publish sensor data to an MQTT topic and subscribe to a command topic from another device | HTTP: device asks server "any new data?" every second. MQTT: server pushes to device when new data arrives. What is the bandwidth difference at 1000 devices? |
| 7.3 | MQTT QoS Levels | QoS 0 (fire and forget), QoS 1 (at least once), QoS 2 (exactly once), when to use each | Choose QoS 1 for telemetry (no data loss acceptable) and understand the acknowledgment mechanism | Your factory has intermittent WiFi. You use QoS 0 for vibration data. After a network event, you check the database and 2 hours of data are missing. What caused this? |
| 7.4 | MQTT Topic Design | Hierarchical topics, wildcards, topic structure for multi-device systems | Design the complete SentinelGrid topic hierarchy: `sentinel/node/{id}/telemetry`, `sentinel/node/{id}/alert`, etc. | 500 nodes are publishing to `sentinel/node/+/telemetry`. The gateway subscribes to `sentinel/node/+/telemetry`. How does the broker route messages? |
| 7.5 | Mosquitto Broker Setup | Installing and configuring Mosquitto, access control, TLS configuration, logging | Set up a local MQTT broker that receives data from SentinelNodes — this is the gateway broker | Mosquitto log shows: client sentinel_node_042 disconnected. What information do you need to diagnose why? |
| 7.6 | Store-and-Forward Pattern | Detecting network loss, writing to local flash, reading from flash on reconnect, chronological delivery | Build a node that never loses telemetry data — stores to SPI flash when offline, sends in order when online | Node goes offline for 2 hours. When it reconnects, 7200 messages need to be delivered. What QoS and burst rate are needed to avoid overwhelming the broker? |
| 7.7 | LoRa and LoRaWAN | Long-range radio basics, spreading factor (range vs data rate trade-off), LoRaWAN gateway, duty cycle limits | Understand why factories with metal walls and 500m distances between machines choose LoRa over WiFi | LoRa at SF12 gives 300 bps data rate. Your telemetry message is 50 bytes. How often can you transmit while respecting 1% duty cycle? |
| 7.8 | TLS and Certificate-Based Auth | TLS handshake, X.509 certificates, why device certificates prevent rogue nodes | Configure MQTT over TLS with client certificate — ensures only legitimate SentinelNodes can publish to the broker | A fake device tries to connect to your MQTT broker with a self-signed certificate. What happens and why? |
| 7.9 | Network Failure Design Patterns | Exponential backoff for reconnection, circuit breaker pattern, health check topics | Implement robust reconnection: first retry after 1s, then 2s, 4s, 8s, max 60s — prevents thundering herd | 500 nodes all lose WiFi simultaneously. All reconnect at the same time. What happens to the broker? How does exponential backoff help? |
| 7.10 | AWS IoT Core | MQTT at scale, device shadows, IoT Rules, certificate-based authentication, message routing to cloud services | Understand how Mosquitto on the gateway bridges to AWS IoT Core — the cloud-scale MQTT broker | A SentinelNode publishes a message with QoS 1. AWS IoT Core is temporarily unavailable. Where does the message go? |

---

### Mini Project — Part 7

**Amateur Implementation:**
Publish temperature data to a public MQTT broker like test.mosquitto.org. Subscribe on another terminal. See data appear.

**MNC-Level Difference:**
A professional engineer sets up a local Mosquitto broker with TLS and client certificate authentication. They provision a unique X.509 certificate for each SentinelNode (simulated with 3 nodes). They implement store-and-forward: disconnect the broker for 10 minutes, verify all telemetry is buffered on the nodes in SPI flash, reconnect the broker, verify all buffered messages arrive in chronological order with no gaps. They deliberately send a malformed message and verify the broker rejects it. They load test the broker with 100 simulated nodes and measure maximum message throughput. All results documented in `IOT_PROTOCOLS.md`.

**GitHub Proof:** Push `07-iot-comms/` with: MQTT publisher/subscriber firmware code, TLS certificate setup scripts, store-and-forward implementation, load test results, broker rejection test, `IOT_PROTOCOLS.md`.

---

### Connection From Part 7 to Part 8

Data now flows reliably from nodes to a local gateway broker. Part 8 covers the gateway itself — the Raspberry Pi that aggregates data from all nodes in a facility zone, buffers it locally, runs a first-level analysis, and forwards to the cloud. The gateway is the bridge between the physical world and the digital cloud.

---

# PART 8 — GATEWAY AND CLOUD BACKEND
## Architecture Position: Layers 7–8 — Aggregation and Storage

**Why This Comes Eighth:** Individual nodes generate data. The cloud needs to store and analyze that data at scale. Between them, the gateway aggregates, buffers, and forwards. The cloud stores every measurement in a time-series database, processes streams, trains ML models, and exposes APIs to the dashboard. This is where the data becomes information.

**What SentinelGrid Needs From This:** The Raspberry Pi gateway runs Mosquitto, a Python pipeline, and local InfluxDB. The cloud has AWS IoT Core, Kinesis, Lambda, TimescaleDB, FastAPI, and a Grafana dashboard.

---

### Subtopic Table — Part 8

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 8.1 | Python for Backend | Python beyond scripting: async programming, data processing with NumPy/Pandas, message handling | Write a Python service that subscribes to MQTT, processes messages, and writes to a database | Your Python MQTT consumer processes 100 messages/second. Each message takes 15ms to process. Will messages accumulate faster than they are consumed? |
| 8.2 | Time-Series Database Concepts | Why regular databases are wrong for sensor data, time-series indexing, retention policies, compression | Understand why querying "show me all anomaly events in the last 30 days" on TimescaleDB takes 12ms but on PostgreSQL takes 45 seconds for 10 billion rows | A regular SQL database stores sensor readings with a timestamp column. At 10 billion rows, a time-range query takes 3 minutes. Why? What does a time-series database do differently? |
| 8.3 | InfluxDB or TimescaleDB | Schema design for IoT (measurement, tags, fields), writing data, querying with time filters, continuous aggregates | Design the SentinelGrid telemetry schema and write/query sensor data — this is the production database | Design a TimescaleDB schema for: node_id, timestamp, vibration_rms, temperature, current, anomaly_score. What are the primary key and index choices? |
| 8.4 | AWS IoT Core | Device registration, certificate management, MQTT topics, IoT Rules, message routing | Route MQTT messages from SentinelNodes to Kinesis using IoT Rules — the AWS-managed MQTT broker | 10,000 nodes connect to AWS IoT Core simultaneously. What is AWS IoT Core doing that a self-managed Mosquitto cannot? |
| 8.5 | Stream Processing | Kinesis Data Streams, real-time processing vs batch, Lambda consumers, windowed aggregation | Process a stream of telemetry messages and detect when a node has sent 3 anomaly alerts in 5 minutes | Why process telemetry as a stream rather than querying the database? What latency difference does this make for alert generation? |
| 8.6 | FastAPI Backend | REST API design, async endpoints, database connection pooling, API documentation with Swagger | Build the SentinelGrid device management API: register nodes, get health history, push OTA commands | Your FastAPI endpoint queries TimescaleDB for the last 24 hours of data for 500 nodes simultaneously. What database configuration is needed to handle this? |
| 8.7 | Docker and Containerization | Dockerfile, building images, docker-compose for multi-service setup, environment variables | Run FastAPI + TimescaleDB + Grafana + MQTT subscriber all locally with one `docker-compose up` command | Without Docker, deploying FastAPI to a new server requires 20 manual steps. With Docker, it requires 1 command. What problem does this solve? |
| 8.8 | Terraform (Infrastructure as Code) | Describing AWS resources in code, `terraform plan`, `terraform apply`, state files, modules | Create all SentinelGrid AWS resources (IoT Core, Kinesis, Lambda, RDS TimescaleDB, S3, CloudFront) with Terraform | Your AWS account is deleted accidentally. How long does it take to recreate all infrastructure with Terraform vs manually through the console? |
| 8.9 | Local Buffering on Gateway | Gateway-side InfluxDB, writing during cloud outage, flushing to cloud on reconnect, deduplication | Implement gateway buffering: cloud unavailable for 2 hours, all data saved locally, cloud comes back, data synced | Gateway buffers 2 hours of data from 200 nodes. Cloud connectivity restores. How do you prevent the flush from overloading the cloud ingestion pipeline? |
| 8.10 | ML Training Pipeline | Collecting training data from production, retraining autoencoder on updated data, evaluating before deployment | Build a weekly retraining pipeline: query last 7 days of normal telemetry from TimescaleDB, retrain model, evaluate, push new model to S3 | A retraining pipeline produces a new model. How do you know if it is better than the current model before deploying it to 10,000 nodes? |

---

### Mini Project — Part 8

**Amateur Implementation:**
Flask app that receives POST requests with sensor data and saves to SQLite.

**MNC-Level Difference:**
A professional engineer builds the complete cloud pipeline locally with Docker Compose: Mosquitto → Python subscriber → TimescaleDB → FastAPI → Grafana. They simulate 50 nodes sending MQTT telemetry simultaneously using a Python simulator, measure the pipeline throughput (messages per second), identify the bottleneck (database write speed), and optimize with batch writes. They implement gateway buffering, simulate a 30-minute cloud outage, verify all data is preserved, simulate cloud reconnection, and verify ordered delivery. The final `CLOUD.md` documents throughput benchmarks, bottleneck analysis, and optimization choices.

**GitHub Proof:** Push `08-cloud-backend/` with: docker-compose.yml for full local stack, Python telemetry simulator (50 nodes), TimescaleDB schema file, FastAPI source, Grafana dashboard JSON, throughput benchmark results, buffering test results.

---

### Connection From Part 8 to Part 9

The cloud stores and analyzes data. AI models are trained in the cloud. But those models and new firmware versions need to reach the physical hardware nodes — which may be installed in a factory 1000km away. Part 9 covers PCB design, which is how you design production-grade hardware nodes, and the manufacturing process, which is how you test and certify them before shipping.

---

# PART 9 — PCB DESIGN AND HARDWARE PRODUCTION
## Architecture Position: Layer 1 — Physical Hardware (Production Grade)

**Why This Comes Ninth:** In Phase 1–3 you used development boards (Arduino, ESP32 devkit). These are fine for learning. But SentinelGrid deployed in a factory uses custom PCBs — smaller, more reliable, with proper protection circuits, defined power supply, and test points for manufacturing verification. PCB design is how hardware goes from prototype to product.

**What SentinelGrid Needs From This:** The SentinelNode PCB integrates the ESP32-S3, all sensors, power supply, LoRa module, SPI flash, battery management, and protection circuits on a single custom board that can be manufactured in volume.

---

### Subtopic Table — Part 9

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 9.1 | KiCad Installation and Interface | Schematic editor, symbol library, PCB editor, footprint library, project structure | Navigate KiCad, place components in schematic, understand the schematic → PCB workflow | What is the difference between a symbol (schematic) and a footprint (PCB)? Why are they separate? |
| 9.2 | Schematic Design in KiCad | Drawing connections (nets), power symbols, labels, hierarchical design, ERC (Electrical Rules Check) | Complete the SentinelNode schematic: ESP32-S3 + all sensors + power supply + connectors | ERC reports "pin unconnected: GPIO4". What does this mean and is it always an error? |
| 9.3 | Component Selection and BOM | Reading component datasheets for footprint, package, electrical specs, availability | Select ADXL355 (LFCSP-14 package), INA226 (SOT23-8), LDO regulator (SOT-223) with proper footprints | Your selected capacitor is rated 6.3V. Your power supply is 5V. Why is this a bad choice for production? |
| 9.4 | PCB Layout Fundamentals | Board outline, component placement, routing traces, clearance rules, design rule check (DRC) | Place and route a two-layer PCB for a simple sensor interface circuit | What is a clearance rule? Why does your PCB manufacturer require minimum 0.2mm trace width? |
| 9.5 | Ground Planes | Copper pour for GND, analog vs digital ground, star grounding, ground plane splits | Design SentinelNode PCB with proper ground planes — analog section isolated from digital | Your ADC readings show noise at the switching frequency of the regulator. The PCB has no ground plane. What happens when you add a ground plane? |
| 9.6 | Power Supply Layout | Decoupling capacitor placement (close to IC pin), power trace width, thermal management | Place decoupling capacitors correctly on the SentinelNode PCB — this directly affects ADC noise | Your decoupling capacitor is 5cm from the IC power pin. The datasheet says place within 2mm. What signal does the oscilloscope show on the power pin? |
| 9.7 | Signal Integrity in Layout | High-speed trace routing, impedance control, avoiding parallel runs of clock and data | Route the 20MHz SPI clock trace away from the analog sensor signals | SPI clock trace runs parallel to the ADXL355 analog power trace for 3cm. What does this do to the ADC noise floor? |
| 9.8 | Design for Manufacturing | Test points on every net, fiducial markers, panelization, Gerber file generation | Add test points to all SentinelNode power rails and critical signals so manufacturing ICT jig can probe them | Why do professional PCBs have small circular copper pads that are not connected to any component? |
| 9.9 | Design for Test (ICT Jig) | Bed-of-nails fixture, self-test firmware, automated pass/fail, test coverage | Design a manufacturing test procedure for SentinelNode that verifies all peripherals without human inspection | At 500 boards per month, manual testing takes 10 minutes per board = 83 hours/month. ICT takes 30 seconds per board = 4.2 hours. What does this mean for cost? |
| 9.10 | EMC Design and Certification | EMI sources (switching regulator, MCU clock, radio), filtering, shielding, CE marking process | Understand what changes between revision 1 (EMC failures) and revision 2 (passing CE) of SentinelNode | Why does a switching regulator operating at 2MHz need an LC filter? What frequencies does it radiate? |
| 9.11 | Gerber Generation and PCB Ordering | Generating manufacturing files, stackup selection, minimum feature sizes, ordering from JLCPCB or PCBWay | Generate Gerbers for SentinelNode and order 5 prototype boards from a PCB fab | What files does a PCB manufacturer need? What does "impedance-controlled stackup" mean? |

---

### Mini Project — Part 9

**Amateur Implementation:**
Download a reference design from Adafruit, slightly modify it, order the board.

**MNC-Level Difference:**
A professional engineer designs the SentinelNode PCB from scratch in KiCad: ESP32-S3, ADXL355 (SPI), INA226 (I2C), LDO regulator for analog section, switching regulator for main rail, SPI flash, LoRa module, battery connector with reverse polarity protection, all test points, fiducials. They run DRC (zero errors), generate Gerbers, and order 5 boards. When the boards arrive, they test each one with a multimeter before powering up (shorts check), then power up and verify voltage rails with an oscilloscope, then program firmware and run the self-test sequence. Board 3 fails the ADC noise test — oscilloscope reveals the decoupling capacitor is in the wrong orientation (electrolytic capacitor installed backwards). This failure is documented in `MANUFACTURING.md` as a production quality finding.

**GitHub Proof:** Push `09-pcb-design/` with: complete KiCad project (schematic + PCB), Gerber files, BOM (CSV), manufacturing test procedure, board photos (front and back), test results for all 5 boards, `MANUFACTURING.md` with quality findings.

---

### Connection From Part 9 to Part 10

You now have real hardware that can be manufactured at scale. Part 10 covers OTA (Over-The-Air) updates and fleet management — the system for updating firmware and AI models on thousands of deployed nodes without physical access. This is the system that keeps production nodes current without requiring a technician to visit each one.

---

# PART 10 — OTA UPDATES AND FLEET MANAGEMENT
## Architecture Position: Layer 9 — Remote Management

**Why This Comes Tenth:** After 1000 SentinelNodes are deployed across 20 factories, a firmware bug is discovered. Without OTA, fixing it requires sending a technician to each of 1000 locations — possibly costing millions of dollars. With OTA, the fix is deployed from a laptop in 10 minutes. Fleet management gives you visibility into which nodes are healthy, which are running which firmware version, and which need attention.

**What SentinelGrid Needs From This:** The complete OTA pipeline: GitHub Actions builds and signs firmware, uploads to S3, nodes poll for updates, download to inactive partition, verify signature, bootloader switches partitions on next boot, rollback if boot fails 3 times.

---

### Subtopic Table — Part 10

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 10.1 | Flash Memory Layout | Partition table, bootloader region, application A, application B, data partition, model partition | Design the SentinelNode flash layout: bootloader (64KB), OTA-0 (1MB), OTA-1 (1MB), model (128KB), data (256KB) | Why must the bootloader never be overwritten by OTA? What happens if it is? |
| 10.2 | ESP-IDF OTA API | esp_ota_begin, esp_ota_write, esp_ota_end, esp_ota_set_boot_partition, esp_https_ota | Implement the OTA download and write sequence — download chunks from HTTPS, write to inactive partition | OTA download fails halfway through. The partial binary is in the inactive partition. What must the bootloader do when it sees an incomplete update? |
| 10.3 | Bootloader Logic | Custom bootloader vs framework bootloader, OTA state machine, boot attempt counter, rollback trigger | Understand how the ESP-IDF bootloader tracks boot count and triggers rollback after 3 failed boots | New firmware boots, initializes WiFi, crashes during MQTT connection. This happens 3 times. Bootloader rolls back. What must the new firmware do to prevent this trigger on a successful boot? |
| 10.4 | Firmware Signing | Private key on build server, public key in bootloader, RSA or ECDSA signature verification | Implement signed OTA: build server signs binary with private key, node verifies with embedded public key | A malicious actor gains access to your S3 firmware bucket and uploads a modified firmware binary. What prevents nodes from installing it? |
| 10.5 | Model OTA (Separate from Firmware) | Dedicated flash partition for model, model version tracking, updating model without rebooting firmware | Implement model update: cloud pushes new model, node downloads to model partition, inference switches to new model | Why store the AI model in a separate flash partition from the firmware instead of compiling it into the firmware binary? |
| 10.6 | OTA Pipeline (CI/CD for Firmware) | GitHub Actions workflow, cross-compilation for target, firmware versioning (semantic versioning), S3 upload | Build an automated pipeline: push to main branch → GitHub Actions builds firmware → signs it → uploads to S3 with version metadata | Your OTA pipeline takes 8 minutes from git push to firmware available in S3. A critical security fix is urgent. Is this acceptable? How do you speed it up? |
| 10.7 | Staged Rollout | Canary deployment (5% of fleet), monitoring period, progressive expansion (20%, 50%, 100%), automatic halt | Deploy new firmware to 5% of SentinelNodes, monitor crash rates and anomaly detection accuracy for 2 hours, then expand | During staged rollout to 5% of fleet, crash rate increases from 0.1% to 3.2%. What do you do next? |
| 10.8 | Fleet Dashboard | Device registry, current firmware version per device, last seen timestamp, battery level, crash count | Build a device management dashboard that shows all 1000 SentinelNodes with health status and OTA progress | 47 nodes show "last seen: 4 hours ago." What are the possible causes and how do you distinguish them? |
| 10.9 | Device Provisioning | First boot registration, certificate provisioning at manufacturing time, device identity in cloud registry | Implement first-boot provisioning: node boots, detects it is unprovisioned, requests certificate from provisioning service, saves to flash | Why does each SentinelNode need a unique X.509 certificate? What breaks if all nodes share the same certificate? |
| 10.10 | Production Incident — OTA Crash Loop | Diagnosing the scenario from the expert talk: 800 nodes in crash loop after bad OTA deployment | Work through the crash loop incident: identify root cause (WiFi reconnect timing bug), design emergency hotfix, deploy via staged rollout to 200 affected nodes | 200 nodes are in a crash loop (boot → crash → reboot → repeat). They cannot receive a new OTA while crashing. The rollback mechanism saved them. If rollback had not been implemented, what would be the only option? |

---

### Mini Project — Part 10

**Amateur Implementation:**
Use ESP-IDF's built-in OTA example to download a new firmware from a URL and apply it.

**MNC-Level Difference:**
A professional engineer builds the complete OTA pipeline: GitHub Actions workflow that builds firmware, generates version metadata JSON, signs with a test private key, uploads to S3. Nodes poll an S3 metadata file every 60 minutes, detect new version, download, verify signature, apply to inactive partition. They then deliberately introduce the crash-loop scenario: new firmware that crashes on WiFi connect. Rollback saves the node. They verify that 3 failed boots triggers rollback. They simulate a staged rollout: 1 of 5 test nodes receives update first (canary), crashes, rollback activates, other 4 nodes see canary failure and deployment halts automatically. This scenario is documented as a production incident postmortem in `POSTMORTEMS/001-ota-crash-loop.md`.

**GitHub Proof:** Push `10-ota-fleet/` with: GitHub Actions workflow YAML, firmware signing scripts, S3 upload scripts, OTA firmware code, fleet dashboard (simple Python + Grafana), staged rollout logic, crash loop reproduction and rollback verification, postmortem document.

---

### Connection From Part 10 to Part 11

You can now deploy firmware and models to thousands of nodes remotely. But how do you know when something is going wrong before users report it? Part 11 covers observability — the system that lets you see inside every node without physically accessing it. When a node 500km away starts behaving strangely, observability is how you diagnose it from a laptop.

---

# PART 11 — OBSERVABILITY AND PRODUCTION ENGINEERING
## Architecture Position: All Layers — The Diagnostic Nervous System

**Why This Comes Eleventh:** A deployed system that cannot be observed cannot be maintained. Observability is how engineers see inside running systems, diagnose problems remotely, and catch issues before users report them. It applies to every layer — firmware logs from nodes, MQTT message rates from the broker, query times from the database, inference accuracy from the AI layer.

**What SentinelGrid Needs From This:** Structured logs from every FreeRTOS task, device health metrics (heap, stack watermark, crash count, battery) forwarded to cloud, Grafana dashboards for both sensor telemetry and system health, automated crash reporting that creates GitHub issues, and runbooks that tell engineers exactly what to do when specific alerts fire.

---

### Subtopic Table — Part 11

| # | Subtopic | Key Concepts to Cover | What You Will Know After | Conceptual Check Question |
|---|----------|----------------------|--------------------------|--------------------------|
| 11.1 | Structured Logging (Firmware) | Log levels (DEBUG, INFO, WARN, ERROR), JSON log format, log forwarding over UART to gateway | Write firmware logs that a production engineer can search — not `printf("here")` but `{"level":"ERROR","task":"ota","event":"signature_verify_failed","firmware_version":"2.3.1"}` | What is the difference between `printf("reading sensor")` and structured logging? Why does the difference matter at 1000 devices? |
| 11.2 | Device Health Metrics | Heap free space, task stack watermarks, uptime, crash count, last reset reason, battery voltage, WiFi RSSI | Build a health reporter task that publishes device health as MQTT message every 60 seconds | Heap free space over 7 days: Day 1: 82KB, Day 2: 78KB, Day 3: 74KB, Day 4: 70KB. What is happening? When does the node crash? |
| 11.3 | Crash Dump Capture | Saving CPU registers and stack at crash time, writing to dedicated flash region, transmitting on next boot | Implement crash reporting: firmware crashes, saves registers and last 512 bytes of stack to flash, next boot uploads crash report to cloud | Crash report shows program counter at 0x40081234. How do you find which line of C code this corresponds to? |
| 11.4 | Remote Diagnostics Design | What to log, what not to log, log volume vs diagnostic value, log retention policies | Design a logging strategy: what events are worth logging, what is noise, how to avoid filling flash with logs | Your node has 256KB of log flash storage. At 10 log events per second each 100 bytes, how long before flash is full? What is the solution? |
| 11.5 | Grafana Dashboards | Connecting Grafana to TimescaleDB, creating time-series panels, alert rules, dashboard organization | Build a SentinelGrid operations dashboard: per-node anomaly score timeline, fleet health map, OTA status, battery levels | You receive an alert: "Node 042 anomaly score above 0.85 for 10 minutes." Your Grafana dashboard shows what other information do you immediately check? |
| 11.6 | Metrics and Monitoring (Cloud Side) | Prometheus metrics from FastAPI, Grafana alerting, SLA tracking, uptime monitoring | Monitor the SentinelGrid cloud backend: API response times, database query times, MQTT broker queue depth | FastAPI response time for `/services/health` endpoint increases from 45ms to 3.2 seconds over 2 days. What do you check first? |
| 11.7 | Incident Response Process | Alert → acknowledge → investigate → mitigate → resolve → postmortem | Walk through the 800-node OTA crash loop incident using this process with a timeline | At 2:37 AM an alert fires: "Crash rate above 2% across fleet." You are on call. Write the first 5 actions you take in order. |
| 11.8 | Postmortem Writing | Timeline of events, root cause analysis, contributing factors, corrective actions, action items | Write a complete postmortem for the ADC noise bug discovered in PCB revision 1 | A postmortem says "engineer made a mistake." Why is this not a useful root cause? What is a better root cause statement? |
| 11.9 | Runbook Creation | Step-by-step diagnostic and remediation procedures, conditions that trigger each procedure | Write a runbook for "Node offline for more than 4 hours" — the exact steps an on-call engineer follows | A runbook says "restart the node." What information must come before this step to make the runbook useful? |
| 11.10 | Production Readiness Review | Checklist before deploying to production: observability, alerting, runbooks, OTA rollback, capacity testing | Evaluate SentinelGrid against a production readiness checklist — what is missing before going to 1000 nodes | Your system works perfectly in testing with 10 nodes. What 5 things must you verify before deploying to 1000 nodes? |

---

### Mini Project — Part 11

**Amateur Implementation:**
Add Serial.print() statements throughout the firmware to see what it is doing.

**MNC-Level Difference:**
A professional engineer implements the complete observability stack: structured JSON logs from all FreeRTOS tasks forwarded to the gateway, crash dump capture with automated GitHub issue creation, device health metrics published to MQTT and stored in TimescaleDB, a Grafana dashboard with 6 panels (fleet health map, anomaly score timeline, battery trend, heap free space per node, OTA status, API response times), and 4 alert rules (anomaly score >0.8 for 10+ minutes, heap free <20KB, node offline >2 hours, battery <15%). They deliberately inject a heap memory leak (call malloc in a loop without free), watch the heap metric decline in Grafana, trigger the alert, diagnose using the structured logs, fix the code, and write a postmortem documenting the entire incident from detection to resolution.

**GitHub Proof:** Push `11-observability/` with: structured logging implementation in firmware, device health reporter code, crash dump implementation, Grafana dashboard JSON, alert rule configurations, injected-leak postmortem (`POSTMORTEMS/002-heap-leak.md`), and `RUNBOOK.md` with 5 procedures.

---

# PART 12 — FULL SYSTEM INTEGRATION (SENTINELGRID)
## Architecture Position: All Layers — Complete System

**Why This Comes Last:** Every part learned individually now connects. This phase is not about learning new concepts — it is about assembling all 11 parts into a running production-grade system, documenting every architectural decision, and demonstrating that each component works together as designed.

**What the Final System Looks Like:**

A factory has 10 SentinelNodes installed on motors, conveyors, and pumps. Each node is a custom PCB (Part 9) running FreeRTOS firmware (Part 4) with sensor drivers (Parts 2–3) sampling vibration at 1kHz. A signal processing pipeline (Part 5) extracts features, a TFLite model (Part 6) scores anomalies locally. Telemetry is published via MQTT (Part 7) to a Raspberry Pi gateway (Part 8) which forwards to AWS IoT Core. TimescaleDB stores all readings. Grafana shows the operations team a live dashboard. When the edge model detects an anomaly, a local alert fires immediately. When the cloud model confirms the trend, a maintenance work order is created automatically. Firmware updates deploy through a GitHub Actions pipeline (Part 10), with staged rollout and automatic rollback. When anything fails, structured logs, device health metrics, and crash reports (Part 11) give engineers full diagnostic visibility.

---

### Final Integration Table

| Integration Task | What It Tests | MNC Proof |
|----------------|---------------|-----------|
| 10 nodes running simultaneously for 72 hours | Stability, memory leaks, crash rate | Grafana screenshot showing 72-hour uptime |
| Simulate network outage for 2 hours | Store-and-forward, no data loss | TimescaleDB continuity verification |
| Deploy new firmware with bug, verify rollback | OTA rollback mechanism | Staged rollout log + rollback event in Grafana |
| Inject a bearing fault (modified test motor) | End-to-end anomaly detection | Anomaly score timeline showing detection |
| Push a retrained AI model via model OTA | Model update pipeline | Inference accuracy before vs after in `BENCHMARKS.md` |
| Run manufacturing ICT on 3 fresh PCBs | Manufacturing process | Test results log with pass/fail per peripheral |
| Simulate 500 nodes with Python simulator | Cloud pipeline scalability | Throughput benchmark — messages/second before saturation |
| Write complete architecture documentation | Knowledge transfer | `ARCHITECTURE.md`, all ADRs, `RUNBOOK.md` |

---

# PART 13 — DOCUMENTATION MASTER PLAN (COMPLETE SENTINELGRID REPOSITORY)

```
sentinelgrid/
├── README.md                          → Complete system overview, demo video, architecture diagram
├── ARCHITECTURE.md                    → All 9 layers explained, design decisions
├── HARDWARE.md                        → PCB design, component selection rationale
├── FIRMWARE.md                        → RTOS task design, memory layout, boot sequence
├── SIGNAL_PROCESSING.md              → FFT pipeline, feature extraction, fault frequency calculation
├── EDGE_AI.md                        → Model architecture, quantization, latency benchmarks
├── IOT_PROTOCOLS.md                  → MQTT design, QoS, store-and-forward
├── CLOUD.md                          → AWS architecture, throughput benchmarks
├── OTA.md                            → A/B partition, signing, rollback, staged rollout
├── OBSERVABILITY.md                  → Logging strategy, metrics, alert rules
├── MANUFACTURING.md                  → ICT jig design, test procedure, quality findings
├── BENCHMARKS.md                     → All measured numbers (inference latency, power, throughput)
├── RUNBOOK.md                        → On-call procedures for 5 alert types
│
├── POSTMORTEMS/
│   ├── 001-ota-crash-loop.md         → 800-node rollout incident
│   ├── 002-heap-leak.md              → Memory leak from missing free()
│   ├── 003-adc-noise.md             → Switching regulator noise in ADC
│   └── 004-i2c-missing-pullup.md    → Factory sensor intermittent failure
│
├── ADR/ (Architecture Decision Records)
│   ├── 001-why-freertos-not-bare-metal.md
│   ├── 002-why-lora-not-wifi.md
│   ├── 003-why-mqtt-qos1-not-qos0.md
│   ├── 004-why-ab-ota-partition.md
│   ├── 005-why-int8-quantization.md
│   ├── 006-why-model-partition-separate.md
│   └── 007-why-timescaledb-not-postgresql.md
│
├── 01-electronics-fundamentals/       → Oscilloscope screenshots, calculations
├── 02-digital-protocols/             → Logic analyzer captures, protocol verification
├── 03-embedded-c/                    → Sensor drivers, DMA code, power measurements
├── 04-rtos/                          → Task architecture, watchdog test, heap monitoring
├── 05-signal-processing/             → FFT pipeline (Python + C), vibration data
├── 06-edge-ai/                       → Training pipeline, quantization, TFLite deployment
├── 07-iot-comms/                     → MQTT firmware, store-and-forward, TLS setup
├── 08-cloud-backend/                 → Docker-compose, FastAPI, TimescaleDB, Grafana
├── 09-pcb-design/                    → KiCad project, Gerbers, board photos, test results
├── 10-ota-fleet/                     → OTA pipeline, fleet dashboard, staged rollout demo
├── 11-observability/                 → Structured logging, crash dump, Grafana dashboards
│
├── hardware/                         → Final SentinelNode KiCad project
├── firmware/                         → Complete ESP-IDF firmware
├── ml/                               → Complete ML training pipeline
├── infrastructure/                   → Terraform files for all AWS resources
├── backend/                          → FastAPI application
├── dashboard/                        → Grafana JSON exports
└── .github/workflows/
    ├── firmware-build.yml
    └── model-retrain.yml
```

---

# SUMMARY TABLE — COMPLETE ROADMAP AT A GLANCE

| Part | Layer | Core Topic | Skills Gained | Mini Project | MNC Proof |
|------|-------|-----------|---------------|--------------|-----------|
| 1 | 1 | Electronics Fundamentals | Read schematics, calculate circuits, use oscilloscope | LED + decoupling cap analysis | Oscilloscope screenshots + calculation sheet |
| 2 | 2 | Digital Protocols | SPI, I2C, UART, ADC, logic analyzer | Sensor over I2C with logic analyzer verification | Logic analyzer captures + fault injection |
| 3 | 3 | Embedded C + MCU | Interrupts, DMA, sleep modes, JTAG debugging | Structured sensor driver with DMA + power measurement | Driver spec doc + power measurements |
| 4 | 3–4 | RTOS + Firmware | FreeRTOS tasks, queues, watchdog, OTA architecture | 5-task SentinelNode firmware with watchdog | Stack watermarks + watchdog test + 24h heap |
| 5 | 5 | Signal Processing | FFT, feature extraction, filter design, MCU FFT | FFT pipeline: Python reference + C implementation | Real vibration data normal vs fault |
| 6 | 5 | Edge AI + TinyML | Train autoencoder, quantize to INT8, TFLite Micro | End-to-end: train → quantize → deploy → measure | Latency benchmarks + accuracy comparison |
| 7 | 6 | IoT Communication | MQTT, QoS, store-and-forward, TLS, LoRa | MQTT node with store-and-forward + TLS auth | Offline buffering test + broker load test |
| 8 | 7–8 | Cloud Backend | TimescaleDB, AWS IoT Core, FastAPI, Docker, Terraform | Full cloud stack in Docker + 50-node simulator | Throughput benchmarks + buffering test |
| 9 | 1 | PCB Design | KiCad, component selection, EMC design, manufacturing test | SentinelNode PCB (complete hardware) | Gerbers + board photos + test results |
| 10 | 9 | OTA + Fleet Management | A/B OTA, firmware signing, staged rollout, provisioning | Complete OTA pipeline with crash-loop test | Staged rollout demo + rollback postmortem |
| 11 | All | Observability | Structured logging, crash dump, Grafana, runbooks | Full observability with heap leak injection | Postmortem + Grafana dashboard |
| 12 | All | System Integration | End-to-end production thinking | SentinelGrid running with 10 real nodes | 72-hour uptime + anomaly detection demo video |

---

**Start with Part 1, Subtopic 1.1.**
**Every concept connects upward. Nothing is isolated.**
**When you request teaching for any part, say: "Teach me Part [N], Subtopic [X.Y] using the 10-part framework inside SentinelGrid."**