
---

## How This Document Works

This is not a list of topics. It is a **narrative learning sequence** where every day's
learning is a foundation for the next, every week builds on the last, and every
checkpoint project tests whether the foundation is actually solid before you move on.

**The design principles:**
- Theory is never more than 2 days without a hands-on test
- Every project is achievable with components you already own or can buy for under ₹500
- Each day shows exactly what you study, what you build, and how it connects to the next day
- Checkpoint projects are graded: Pass (move on) / Revisit (spend one more day before moving)

---

## Part 0: The Prerequisites — What Must Exist Before Day 1

Before starting the roadmap, you need a foundation in three non-electronics disciplines.
These are not part of the 750-day count. They run BEFORE Day 1 or in parallel during
the first 30 days. Without them, you will hit walls at Day 20, Day 60, and Day 120.

---

### Pre-Track A: Mathematics (21 days, parallel with Days 1–30)

Mathematics is the language hardware runs on. Every circuit analysis formula, every
control system, every DSP algorithm, every signal — all of it is mathematics made
physical. You do not need to be a mathematician. You need enough to read and write
the language fluently at the level hardware engineering requires.

**What you need and why each piece matters:**

**Algebra & Trigonometry (Days P1–P3)**
Every Ohm's Law calculation is algebra. Every AC signal analysis uses trigonometry
(sin and cos waves). Every antenna and RF calculation uses trigonometry. You almost
certainly have this already. Verify by solving: if V=IR and P=IV, express P entirely
in terms of V and R. If you can do this in 30 seconds, you are ready.

**Coordinate systems and vectors (Days P4–P5)**
Electromagnetic fields are vectors. Forces on a motor are vectors. Control systems
use state vectors. You need to be comfortable with: vector addition, dot product,
cross product, unit vectors, 2D and 3D coordinate systems.

**Calculus — derivatives and integrals (Days P6–P10)**
A capacitor's current is I = C × dV/dt. That dV/dt is a derivative. The charge stored
in a capacitor is Q = ∫I dt. That is an integral. Without calculus, every capacitor,
inductor, and filter formula is magic. With calculus, it is obvious. You need:
derivatives (product rule, chain rule), integrals (definite, indefinite, by substitution),
understanding of what a derivative means physically (rate of change) and what an
integral means physically (accumulated area, total quantity).

Resource: Khan Academy Calculus 1 and 2 (free, complete, excellent).
Time: 5 days of 2 hours each = 10 hours. Enough for the fluency needed here.

**Differential equations (Days P11–P13)**
An RC circuit charging is described by: V(t) = Vs × (1 - e^(-t/RC)). This comes from
solving dV/dt = (Vs - V)/RC — a first-order linear ODE. Every filter, every control
system, every transient response requires solving or at least reading differential
equations. You need: first-order ODEs (separable, linear), second-order ODEs
(underdamped, overdamped, critically damped — these describe how every oscillating
system behaves), and the Laplace transform (converts differential equations to algebra
— used in every control system textbook).

**Linear algebra (Days P14–P16)**
A system of three circuit mesh equations is three simultaneous linear equations.
Solve it by hand once; in practice you use matrices. Neural network weights are
matrices. Image processing is matrix operations. You need: matrix multiplication,
determinants, inverse matrix, eigenvectors and eigenvalues (used in control system
stability analysis). One week is enough for practical fluency.

**Probability and statistics (Days P17–P19)**
Every sensor reading has noise. Noise is a probability distribution. Measurement
uncertainty is statistics. Quality control of manufactured hardware uses statistics.
You need: probability distributions (Gaussian/normal is the most important — noise
is Gaussian), mean and standard deviation, confidence intervals, basic hypothesis
testing (is this measurement result real or noise?).

**Complex numbers (Days P20–P21)**
AC circuit impedance is a complex number: Z = R + jX where j = √(-1). The j is not
imaginary in a dismissive sense — it encodes phase angle. Without complex numbers,
you cannot do any AC analysis, any filter design, or any RF work. You need: complex
number arithmetic (add, subtract, multiply, divide), polar form (magnitude and angle),
Euler's formula (e^(jθ) = cos θ + j sin θ — this is the foundation of Fourier analysis).

**Mathematics Resources (all free):**
- Khan Academy (khanacademy.org): Algebra through Calculus 2, Differential Equations,
  Linear Algebra, Statistics — complete video courses with exercises
- 3Blue1Brown (YouTube): "Essence of Calculus" and "Essence of Linear Algebra"
  series — builds intuition better than any textbook in the same time
- Paul's Online Math Notes (tutorial.math.lamar.edu): Complete ODE reference, free

**Mathematics Checkpoint Project (end of Day P21):**
Solve these four problems. If all correct, mathematics prerequisite complete.
1. An RC circuit has R = 10kΩ, C = 100µF, Vs = 5V. Write and solve the ODE for
   V(t) across the capacitor. What is V at t = 1 second?
2. A signal V(t) = 3sin(2π × 1000t + π/4). What is its frequency, amplitude, and
   phase angle? Express the impedance of a 1µF capacitor at this frequency as a
   complex number.
3. A system has transfer function H(s) = 10/(s² + 3s + 10). Is it stable?
   (Check: are all poles in the left half plane?)
4. Five resistance measurements give: 99.8, 100.1, 100.3, 99.9, 100.4 Ω.
   Calculate mean, standard deviation, and 95% confidence interval.

---

### Pre-Track B: Physics (10 days, parallel with Days 1–20)

You need physics at the level where you understand WHY the electronic behaviour
happens, not just HOW the formula predicts it. This is deeper than Ohm's Law.

**Electromagnetism fundamentals (Days P22–P26)**
- Coulomb's Law: charges attract/repel. This is why a capacitor stores charge.
- Electric field E: force per unit charge. Voltage is work done against E field.
- Gauss's Law: total electric flux through a closed surface = enclosed charge / ε₀.
  This is why a parallel plate capacitor formula works.
- Magnetic field B and Ampere's Law: current produces magnetic field. This is why
  inductors store energy in magnetic fields and why motors work.
- Faraday's Law: changing magnetic field induces EMF. This is why transformers work,
  why motors generate back-EMF when spinning, why generators generate electricity.
- Maxwell's equations: the four equations that unify all of electromagnetism. You do
  not need to solve them analytically — you need to read them and know what each says.

**Quantum mechanics basics (Days P27–P29)**
Not the full quantum mechanics course. Only these specific results:
- Energy quantization: electrons in atoms can only have discrete energy levels.
  This is why semiconductors have bandgaps.
- Photoelectric effect: light of sufficient frequency ejects electrons from material.
  This is literally how your camera sensor works (each photon → one electron).
- Tunnelling: quantum particles can pass through energy barriers they classically
  cannot overcome. This is what happens in tunnel diodes and limits transistor
  scaling below ~5nm gate length.
- Pauli exclusion principle: no two electrons can share identical quantum states.
  This is why electron bands form in solids and why conductors, semiconductors,
  and insulators behave differently.

**Thermodynamics for electronics (Days P30–P31)**
- Heat flows from hot to cold (Second Law). This is why you need heatsinks.
- Thermal resistance θ: analogous to electrical resistance. ΔT = P × θ, just as V = I × R.
  You will use this formula to calculate whether a MOSFET will overheat.
- Blackbody radiation: objects emit IR proportional to T⁴. This is how thermal cameras
  measure temperature without contact and how your Sentigrade IR LEDs can be
  distinguished from room temperature thermal IR.

**Physics Resource:** "University Physics" by Young & Freedman, Chapters 21–30
(electromagnetism), or MIT OpenCourseWare 8.02 (Electricity and Magnetism) — free.

---

### Pre-Track C: Materials Science Basics (7 days, parallel with Days 45–65)

This is the chemical/materials knowledge identified as a gap. Here is the minimum
you need and exactly when to learn it.

**Atomic structure and bonding (Days P32–P34)**
- Atomic orbitals and valence electrons: why silicon with 4 valence electrons is a
  semiconductor while copper with 1 is a conductor and sulphur with 6 is an insulator.
- Covalent vs ionic vs metallic bonding: affects conductivity, brittleness, melting point.
- Crystal structure: silicon is a diamond cubic lattice. The regularity of this lattice is
  what gives silicon its predictable electronic properties. Defects in the lattice are
  what create traps that degrade transistor performance over time.

**Band theory (Days P35–P36)**
- When atoms bond in a solid, their discrete energy levels broaden into bands.
- Valence band (filled with electrons) and conduction band (empty at 0K) are separated
  by a bandgap.
- Conductor: no bandgap (bands overlap). Insulator: large bandgap (>5 eV). Semiconductor:
  small bandgap (silicon: 1.1 eV, GaN: 3.4 eV, SiC: 3.26 eV).
- Doping: adding phosphorus (5 valence electrons) to silicon creates an N-type region
  with extra electrons. Adding boron (3 valence electrons) creates P-type with holes.
  This is the basis of every transistor and diode you use.

**Materials properties relevant to hardware (Days P37–P38)**
- Thermal conductivity: copper (385 W/m·K), aluminium (205), FR4 PCB (0.3), air (0.026).
  These numbers tell you exactly how heat flows through your hardware.
- Coefficient of Thermal Expansion (CTE): how much a material expands with temperature.
  Mismatch between PCB (FR4: 14–17 ppm/K) and ceramic chip package (3–7 ppm/K)
  causes solder joint stress. After 1000 power cycles, cracks form. This is why
  industrial boards use ceramic substrates or CTE-matched materials.
- Resistivity: copper (1.7×10⁻⁸ Ω·m), silicon (640 Ω·m — varies hugely with doping).
  These numbers let you calculate trace resistance and understand why silicon is
  not used for wiring.
- Permittivity (dielectric constant): FR4 (Dk ≈ 4.5), Rogers RO4003 (Dk = 3.55 ±0.05),
  air (Dk = 1.0). The higher the Dk, the slower signals travel and the more energy
  the substrate absorbs at high frequency.

**Materials Checkpoint:** Given a thermal path: LED junction → solder (Ag, 60 W/m·K,
0.1mm thick) → copper pad (385 W/m·K, 70µm thick) → FR4 (0.3 W/m·K, 1mm thick) →
ambient air. If the LED dissipates 1W, calculate the temperature rise at the junction
using the thermal resistance network. Answer should be approximately +20°C above
the board temperature from the FR4 layer alone.

---

## Other Disciplines Needed: Complete Gap Audit

Beyond mathematics, physics, and materials, here are every other discipline that
contributes to hardware mastery, with an honest assessment of how much you need:

**Computer Science (Algorithms & Data Structures)** — MEDIUM NEED
Not the full CS curriculum. Specifically: Big-O complexity (why a nested loop
processing 76,800 pixels twice is O(n²) and might be too slow on an ESP32),
linked lists (FreeRTOS uses them for task queues), hash tables (used in protocol
stacks for address lookup), basic graph algorithms (used in PCB autorouting,
network routing protocols). Cover this during Phase 2 (Days 22–45) alongside
microcontrollers. Resource: "Introduction to Algorithms" Ch. 1–6, or
the free MIT 6.006 OCW course (first 10 lectures).

**Technical Writing and Documentation** — HIGH NEED (often ignored)
Every professional hardware project requires: schematics with correct annotation,
BOMs (Bill of Materials) with manufacturer part numbers, assembly drawings, test
procedures, firmware comments and README files. Poor documentation means you
cannot revisit your own project in 6 months and cannot share it. Begin from Day 1:
document every project in a GitHub repository as you build it. This is not an
add-on — it is part of every checkpoint project.

**Economics & Cost Engineering** — LOW-MEDIUM NEED
Understanding component pricing, MOQ (Minimum Order Quantities), PCB fabrication
cost drivers (layer count, board size, via size, finish), and how to read a BOM cost
sheet. Needed for anyone who wants to take hardware from prototype to product.
Cover this during the advanced PCB module (Days 276–300).

**Biology (specifically for bioelectronics track)** — NEEDED IF pursuing Domain 26
If you pursue bioelectronics and medical devices (Domain 26 — Sentigrade's medical
direction), you need basic cell biology (cell membrane potential, ion channels,
action potentials — these are what ECG/EEG measure), basic anatomy (where ECG
electrodes go and why), and basic physiology (the cardiac conduction system that
creates the ECG waveform). This is covered within the bioelectronics module,
not as a separate pre-requisite.

**None of the following are needed:**
Organic chemistry, biochemistry (unless BioMEMS/lab-on-chip), fluid mechanics
(unless hydraulics/pneumatics), civil or structural engineering, economics beyond
basic BOM costing, or any social science.

---

## The Integrated Master Roadmap — Day by Day

### Reading Key:
📖 = Study (read, watch, simulate)
🔧 = Build (physical or software project)
🧪 = Test (measure, verify, compare to prediction)
✅ = Checkpoint (must pass before continuing)
🔗 = Connection (how today's learning feeds tomorrow's)

---

## PHASE 0: PHYSICS FOUNDATION
### Days 1–7 | The Language of Electricity

**The governing question:** Why do electrons move, and how do we control the movement?

---

**Day 1**
📖 AM: Voltage, current, resistance — the water analogy. Read Practical Electronics
   for Inventors Ch. 1–2. Watch "Electricity" EEVblog #1 (YouTube).
📖 PM: Ohm's Law V=IR, power P=IV=I²R=V²/R. Work 15 practice calculations.
🔗 Tomorrow: You will measure these values physically. Today you predict. Tomorrow
   you verify. The gap between prediction and measurement IS the learning.

**Day 2**
📖 AM: Series circuits — same current everywhere, voltages add. Parallel circuits —
   same voltage everywhere, currents add. Kirchhoff's Voltage Law and Current Law.
🔧 PM: Falstad Circuit Simulator (falstad.com/circuit). Build a voltage divider with
   two resistors. Predict midpoint voltage. Adjust values and watch voltage change.
🧪 Verify: Does the simulated voltage match your Ohm's Law calculation exactly?
🔗 Voltage dividers appear in almost every hardware project: sensor signal scaling,
   ADC input protection, bias voltage generation.

**Day 3**
📖 AM: Capacitors — store charge, block DC, pass AC. Capacitor formula C=Q/V.
   Energy stored = ½CV². Time constant τ = RC.
📖 PM: RC charging curve V(t) = Vs(1 - e^(-t/RC)). What does e mean physically?
   At t = τ, the capacitor has charged to 63.2% of Vs. Why 63.2%? (It's 1 - 1/e.)
🔧 Falstad: Build RC circuit. Watch the capacitor charge in real time. Measure
   the voltage at t = τ. Confirm it is 63.2% of supply.
🔗 Capacitors appear in: power supply filtering (keep voltage stable), timing circuits,
   ADC sample-and-hold, RF coupling and bypassing. Every circuit you build will have them.

**Day 4**
📖 AM: Inductors — store energy in magnetic fields, resist current change. L×dI/dt = V.
   RL time constant τ = L/R.
📖 PM: Back-EMF spike: when you cut current through an inductor (like a motor coil),
   the collapsing magnetic field induces a voltage spike that can destroy your MCU pin.
   Protection diode (flyback diode) placed across the inductor clamps this spike.
🔧 Falstad: Build RL circuit. Observe current rise curve. Then add a switch that
   opens suddenly — observe the voltage spike. Add a diode and watch it clamp.
🔗 You will need this knowledge every time you control a motor, relay, or solenoid.

**Day 5**
📖 AM: AC signals. Frequency, period, amplitude, RMS value. Why RMS?
   (RMS voltage of an AC signal delivers same power to resistor as DC of same value.)
   Mains electricity in India: 230V RMS, 50Hz.
📖 PM: Impedance of capacitor: Xc = 1/(2πfC). Impedance of inductor: XL = 2πfL.
   Complex impedance: Z = R + jX. Total impedance of series RLC.
🔧 Falstad: Build series RC circuit with AC source. Observe that current leads voltage
   by 90° in a capacitor. Observe that current lags voltage by 90° in an inductor.
🔗 This phase difference is why power supplies need power factor correction, why
   audio cables have frequency-dependent attenuation, and why antennas must be
   impedance-matched to their feed lines.

**Day 6**
📖 AM: Power in AC circuits. Real power (W), reactive power (VAR), apparent power (VA),
   power factor (cos θ). Why do utilities charge for reactive power? (It flows back and
   forth without doing useful work, but it still loads the cables.)
📖 PM: Transformers — mutual inductance. Turns ratio: Vs/Vp = Ns/Np.
   Step-up and step-down. Why does high-voltage transmission reduce losses?
   (P_loss = I²R; at higher voltage, less current for same power, less I²R loss.)
🔗 Every power adapter in your house is a transformer. Every car charger with a bulky
   ferrite core contains a high-frequency transformer working at 50–200kHz.

**Day 7**
📖 AM: Multimeter operation — voltage, current, resistance, continuity, diode test.
   Understanding floating inputs, probe placement, measurement errors.
📖 PM: Measurement error and precision. Why does a cheap multimeter read differently
   from an expensive one? (Input impedance, ADC resolution, calibration.)

✅ **PHASE 0 CHECKPOINT PROJECT — The Measurement Lab**

Build these three circuits on a breadboard and verify each with a multimeter:
1. Voltage divider: 9V battery, two resistors R1=10kΩ, R2=4.7kΩ. Predict midpoint
   voltage using Ohm's Law. Measure it. Tolerance must be within 5%.
2. LED circuit: Same 9V battery, LED (Vf ≈ 2V), choose resistor so current = 10mA.
   Calculate R = (9-2)/0.01 = 700Ω. Use nearest standard value (680Ω). Measure
   actual current. Document: does the LED brightness match your prediction?
3. RC timer: 5V supply, R=100kΩ, C=100µF. Predict time for capacitor to charge to
   3.15V (63.2% of 5V) = 10 seconds. Charge it and time it with a phone stopwatch.
   Result should be within 20% (component tolerances are wide).

Document everything in a GitHub repository. Take photos. Write a README.
**Pass criteria:** All three circuits work, measurements within tolerance, documented.

---

## PHASE 1: SEMICONDUCTOR FUNDAMENTALS
### Days 8–21 | The Physics of Control

**The governing question:** How does a tiny voltage control a large current?

---

**Day 8**
📖 AM: The P-N junction — why silicon doped with phosphorus (N-type) bonded to
   silicon doped with boron (P-type) creates a one-way valve for current.
   Depletion region, built-in voltage (~0.6V for silicon), forward bias vs reverse bias.
📖 PM: Diode characteristics — forward voltage drop (Vf), reverse breakdown voltage,
   leakage current. Reading a diode datasheet: 1N4007, what does each parameter mean?
🔧 Falstad: Build diode rectifier circuit — convert AC to pulsating DC. Add a capacitor
   after the diode — observe how the capacitor smooths the pulsating DC. This is the
   first stage of every power supply.

**Day 9**
📖 AM: LED physics — when electrons and holes recombine at a P-N junction, the energy
   releases as a photon. Photon energy = bandgap energy = hf (Planck's constant ×
   frequency). Higher bandgap → higher frequency → shorter wavelength → more toward
   blue/UV. Lower bandgap → lower frequency → longer wavelength → red/IR.
   This is why blue LEDs (GaN, 3.4 eV bandgap) were so hard to discover —
   they won the Nobel Prize in Physics 2014.
📖 PM: LED circuit design. Vf varies by color: red ~1.8V, green ~2.0V, blue ~3.2V,
   IR 850nm ~1.3V. Series resistor calculation. What happens if you omit the resistor?
   (LED has negative resistance in forward direction — current runaway → dead LED.)
🔧 Build: LED + resistor circuit on breadboard. Measure LED Vf with multimeter (diode
   test mode). Calculate correct series resistor for 20mA. Verify current with ammeter.

**Day 10**
📖 AM: BJT (Bipolar Junction Transistor) — NPN and PNP types, three regions:
   cutoff (off), active (amplifier), saturation (switch fully on). Current gain β (hFE):
   Ic = β × Ib. A 2N2222 has β ≈ 100 — 1mA base current controls 100mA collector current.
📖 PM: BJT as switch. To saturate: Ib > Ic / β. For LED switching with 50mA through LED
   and β=100, need Ib > 0.5mA. Base resistor: Rb = (Vlogic - 0.7) / 0.5mA ≈ 5.2kΩ.
🔧 Falstad: Build NPN transistor LED switch. Apply 3.3V to base through Rb. Observe
   LED turning on. Vary Rb and observe current control (active region = amplifier).

**Day 11**
📖 AM: MOSFET — Metal Oxide Semiconductor Field Effect Transistor. Gate, Drain, Source.
   N-channel: positive gate voltage creates conductive channel. Vgs(th) is the threshold.
   Key advantage over BJT: gate draws essentially zero current (oxide insulates gate).
📖 PM: IRLZ44N deep dive — read the actual datasheet. Find: Vgs(th) = 1–2V (logic-level),
   Rds(on) = 22mΩ (very low loss), Vds(max) = 55V, Id(max) = 47A. Understand why each
   parameter matters for your Sentigrade MOSFET strobe circuit.
🔧 Build: MOSFET LED switch replacing the BJT from Day 10. Connect gate to 3.3V through
   10kΩ resistor (pull-down keeps gate at 0V when input disconnected). Verify LED switches.
🔗 The MOSFET switch you built today IS the IR strobe control circuit in Sentigrade.
   The only difference in Sentigrade is the input comes from an ESP32 GPIO instead of
   your finger, and the LED is IR instead of visible.

**Day 12**
📖 AM: MOSFET vs BJT — decision framework. Use MOSFET when: high current, fast switching,
   low gate drive power available (3.3V MCU output), need low Rds(on). Use BJT when:
   small signal amplification, need precise current control, high-temperature environments.
📖 PM: Relay — mechanical switch controlled by electromagnetic coil. Advantage: complete
   isolation between control and power circuits. Disadvantage: slow (ms), wears out,
   generates voltage spikes when coil de-energized. Use relay when switching mains
   voltage (230V AC) from a 3.3V logic signal — the high-voltage isolation is essential.
🔧 Falstad: Build relay circuit with flyback diode. Observe the spike that the diode clamps.

**Day 13**
📖 AM: Logic gates — NOT, AND, OR, NAND, NOR, XOR built from MOSFETs in CMOS configuration.
   Truth tables for each. NAND universality: any boolean function from NAND only.
   Boolean algebra: De Morgan's theorems (NOT(A AND B) = NOT A OR NOT B).
📖 PM: Combinational logic design. Design a circuit using NAND gates only that implements
   XOR. Verify with truth table.
🔧 Falstad: Build a CMOS NOT gate from two MOSFETs (one N-channel, one P-channel).
   Build a CMOS NAND gate. Verify truth tables.

**Day 14**
📖 AM: Sequential logic — flip-flops. SR flip-flop (Set-Reset), D flip-flop (Data),
   JK flip-flop. The key idea: sequential logic has memory. Its output depends on
   both current input AND past history. This is the foundation of registers and
   counters inside every MCU.
📖 PM: Registers and shift registers. An 8-bit register stores 8 bits (1 byte) using
   8 D flip-flops clocked simultaneously. A shift register moves bits one position
   per clock — used for serial-to-parallel conversion (SPI protocol uses this).
🔗 The CPU registers inside your ESP32 (R0 through R15) are shift registers made of
   flip-flops. When you write `int x = 5;`, the value 5 (00000101 in binary) is loaded
   into one of these registers.

**Day 15**
📖 AM: LTspice installation and tutorial. LTspice is a free professional circuit
   simulator used at Intel, Nvidia, Texas Instruments. Unlike Falstad, it uses
   real component models from manufacturers. Download from analog.com (free).
📖 PM: Simulate the RC charging circuit from Day 3 in LTspice. Add a realistic
   capacitor model (ESR — Equivalent Series Resistance). Observe that ESR causes
   a voltage jump at the start of charging — this is the resistive component of a
   real (non-ideal) capacitor.
🔗 ESR is what causes old electrolytic capacitors to fail. When you repair an appliance,
   you will measure ESR to find the failing capacitor. Now you know why it matters.

**Day 16**
📖 AM: Analog-to-Digital Conversion. ADC takes a continuous voltage and converts it
   to a binary number. Resolution: a 12-bit ADC produces 2¹² = 4096 discrete levels.
   For a 3.3V reference, resolution = 3.3/4096 = 0.806mV per step.
   Sampling rate and Nyquist theorem: must sample at ≥2× the highest signal frequency.
   For audio (20kHz max): minimum 40,000 samples/second. Standard is 44,100 samples/sec.
📖 PM: DAC — digital to analog. R-2R ladder network converts binary code to voltage.
   PWM as a 1-bit DAC: 50% duty cycle + low-pass filter = 50% of Vcc as DC output.
🔧 Falstad: Build R-2R ladder DAC with 4 inputs. Verify that binary input 1010 produces
   10/16 × Vref output voltage.

**Day 17**
📖 AM: Op-Amp (Operational Amplifier) — the fundamental analog building block.
   Ideal op-amp properties: infinite gain, infinite input impedance, zero output impedance.
   The two golden rules for op-amp circuits with negative feedback:
   1. Output does whatever it must to make V+ = V-
   2. No current flows into input terminals
📖 PM: Op-amp configurations. Non-inverting amplifier: Vout/Vin = 1 + Rf/R1.
   Inverting amplifier: Vout/Vin = -Rf/R1. Voltage follower: gain = 1, used for
   impedance buffering. Comparator: no feedback, output saturates to rail — used
   as threshold detector.
🔧 LTspice: Simulate a non-inverting amplifier with gain = 10. Apply a 100mV sine wave
   input. Verify 1V output. Then apply 500mV input — observe output clipping at supply
   rail. This is amplifier saturation.

**Day 18**
📖 AM: Power supply fundamentals. Linear regulator (LM7805): input 7–35V, output 5V
   stable. Heat dissipated = (Vin - Vout) × Iout. At 12V in, 5V out, 1A: 7W as heat.
   That requires a large heatsink.
   Switching regulator (buck converter): switches MOSFET on/off at ~100–500kHz,
   uses inductor to average. Efficiency 85–95%. Almost no heat for same conversion.
📖 PM: Buck converter operating principle. When MOSFET on: inductor current rises,
   energy stored in field. When MOSFET off: inductor forces current to continue
   through diode (freewheeling), energy releases into output capacitor.
   Duty cycle D = Vout/Vin. For 3.3V from 5V: D = 66%.
🔧 LTspice: Simulate a simple buck converter. Observe inductor current waveform
   (triangular ripple). Observe output voltage ripple. Add output capacitor and
   observe ripple reduction.

**Day 19**
📖 AM: Zener diode — special diode that breaks down at a precise reverse voltage and
   regulates at that voltage. 5.1V Zener holds 5.1V across it regardless of current
   (within limits). Used for: voltage reference, overvoltage protection, signal clamping.
   Schottky diode — lower forward voltage (0.3V vs 0.7V), faster switching, used in
   power supply rectifiers and protection circuits.
📖 PM: ESD (Electrostatic Discharge) protection. When you shuffle your feet on carpet
   and touch a doorknob, you discharge 10,000–30,000V. The same discharge through a
   GPIO pin destroys it. TVS (Transient Voltage Suppressor) diodes clamp ESD spikes
   in nanoseconds. Every external connector on a PCB should have TVS diodes.
🔧 Research: Find the TVS diode on an Arduino board schematic. Identify the PRTR5V0U2X
   or similar dual-rail TVS on USB data lines.

**Day 20**
📖 AM: AC-DC power conversion — the full chain from wall socket to microcontroller:
   230V AC mains → transformer (step down to 12V AC) → bridge rectifier (4 diodes,
   full-wave rectification) → filter capacitor (smooth to DC) → linear or switching
   regulator → clean DC. OR: switched-mode power supply (SMPS) — no transformer at
   mains frequency, switches at high frequency, much smaller and lighter.
📖 PM: Safety. Mains voltage kills. 100mA through the heart is lethal. Every mains-
   connected project must have: fuse (overcurrent protection), isolation (no conductive
   path from mains to touch-safe output), creepage distance (minimum PCB distance
   between mains and low-voltage conductors — IEC 60950 specifies 6mm at 230V).
   For your projects: never design mains circuits until you have passed the advanced
   PCB module (Day 276+). Use a commercial wall adapter to generate DC.

**Day 21**
📖 AM: Semiconductor materials comparison — Silicon vs GaN vs SiC.
   Silicon: bandgap 1.1 eV, max junction temp 150°C, max field 0.3 MV/cm.
   GaN: bandgap 3.4 eV, max junction temp 200°C+, max field 3.3 MV/cm. Used in
   fast phone chargers, 5G amplifiers, future EV inverters.
   SiC: bandgap 3.26 eV, max junction temp 200°C+, max field 2.5 MV/cm. Used in
   Tesla Model 3 inverter, industrial motor drives, EV charging stations.
   Both allow switching 10× faster than silicon at the same voltage rating.

✅ **PHASE 1 CHECKPOINT PROJECT — The Component Investigation**

Build and document on a breadboard:
1. MOSFET-controlled high-current LED string: Use IRLZ44N or any logic-level MOSFET.
   Drive gate with 3.3V signal (from voltage divider from 5V or 3.3V source). Switch
   LEDs at 500mA total (5 LEDs × 100mA, with current-limiting resistors). Verify with
   ammeter that 500mA flows through drain and 0mA flows into gate.
2. Op-amp comparator temperature sensor: Use an LM358 op-amp (₹10), NTC thermistor
   (₹30), and a fixed voltage reference (Zener or voltage divider). Configure as a
   comparator: when temperature exceeds a threshold, output switches LED on. This is
   the control circuit in your fridge's thermostat, simplified.
3. Buck converter investigation: Buy a cheap DC-DC buck module (₹50 from local
   electronics market, the small blue LM2596 board). Input 12V. Set output to 3.3V.
   Measure efficiency: Pout = Vout × Iout / Pin = Vin × Iin. Compare to what a linear
   regulator would waste as heat for the same conversion. Document.

**What this teaches:** You have now physically verified the three most important
power control mechanisms in all of hardware: switched current (MOSFET), analog
threshold detection (op-amp comparator), and efficient voltage conversion (buck).
Every appliance, every car ECU, every server power supply uses these three building
blocks. The fridge thermostat is literally project 2.

---

## PHASE 2: MICROCONTROLLERS — THE BRAIN
### Days 22–45 | Programming Hardware

**The governing question:** How does a chip run code, and how does code control physics?

**Materials knowledge inserted here (Days 45–50 overlap):**
Study PCB substrate materials and solder chemistry (Pre-Track C Days P32–P38)
while doing the hands-on hardware work of this phase.

---

**Day 22**
📖 AM: Microcontroller architecture — CPU, flash, SRAM, peripherals all on one chip.
   Harvard architecture: separate instruction memory and data memory buses allow
   fetching next instruction while reading data — faster than Von Neumann.
   The fetch-decode-execute cycle: every instruction your code runs goes through this.
📖 PM: ESP32-S3 architecture deep dive. Xtensa LX7 dual core at 240MHz. 512KB SRAM +
   8MB PSRAM (external). 8MB flash. LCD_CAM peripheral (your camera interface). Two
   I2C, three SPI, three UART, 45 GPIO. Read the Technical Reference Manual overview
   (Espressif documentation, free PDF).

**Day 23**
📖 AM: Memory in an embedded system. Code (flash) vs data (SRAM). Stack vs heap.
   Stack overflow: when function calls nest too deeply or local arrays too large.
   Common symptom: ESP32 resets randomly with "guru meditation error stack overflow".
   Heap fragmentation: malloc/free over time creates holes — eventually malloc fails.
   Rule: in embedded systems, avoid dynamic allocation. Use static buffers.
📖 PM: The linker script — how the compiler knows where in memory to place your code,
   your initialized data, your BSS (zero-initialized variables). Read a simple ESP-IDF
   linker script to understand section placement: .text (code in flash), .data
   (initialized globals in SRAM), .bss (zero-initialized globals).

**Day 24**
📖 AM: GPIO at the register level. Without a library: a GPIO is just a bit in a
   register. To set GPIO 4 HIGH: write 1 to bit 4 of GPIO_OUT_REG. To configure
   as output: write 1 to bit 4 of GPIO_ENABLE_REG. Libraries like Arduino do this
   for you — but knowing this means you can program any MCU even without a library.
📖 PM: ESP-IDF GPIO driver. `gpio_config()`, `gpio_set_level()`, `gpio_get_level()`,
   `gpio_set_direction()`. Read the ESP-IDF GPIO driver source code on GitHub.
   Find where `gpio_set_level()` eventually writes to the hardware register.
🔧 ESP-IDF project: Blink an LED without using `delay()`. Instead, use `esp_timer_get_time()`
   to check elapsed microseconds. This teaches you non-blocking timing — the foundation
   of real embedded systems programming.

**Day 25**
📖 AM: UART protocol — the simplest serial communication. Asynchronous: both sides
   agree on baud rate (bits per second) beforehand. Format: 1 start bit (always low),
   8 data bits (LSB first), 1 stop bit (always high). At 115200 baud, one byte takes
   1/115200 × 10 bits = 86.8 µs.
📖 PM: UART in ESP-IDF: `uart_driver_install()`, `uart_read_bytes()`, `uart_write_bytes()`.
   The FIFO (First In First Out) buffer: UART hardware stores received bytes in a
   64-byte FIFO so the CPU doesn't have to respond instantly to each byte.
🔧 Project: Connect two ESP32 boards via UART (TX of one to RX of other, shared GND).
   Send sensor data (ADC reading of a potentiometer) from one to the other. Display on
   second board via serial monitor. Document the byte format you chose and why.

**Day 26**
📖 AM: I2C protocol — two-wire, multi-device. SCL (clock) driven by master. SDA (data)
   bidirectional, open-drain (devices pull low, resistor pulls high). Each device has
   7-bit address. Transaction: START → address + R/W bit → ACK → data bytes → ACK → STOP.
   Why open-drain? Allows multiple devices on same bus without shorts — only one device
   drives low at a time.
📖 PM: SSD1306 OLED I2C protocol. Address 0x3C (or 0x3D). Command bytes vs data bytes
   distinguished by control byte (0x00 = command, 0x40 = data). Page addressing mode:
   display is 8 rows of 128 pixels, each row is a "page".
🔧 Project: Drive SSD1306 OLED WITHOUT using a library. Write bare I2C transactions
   using ESP-IDF i2c driver. Implement: init sequence, clear display, write one character.
   This exercises: I2C protocol, datasheet reading, bit manipulation, driver writing.

**Day 27**
📖 AM: SPI protocol — four wires: MOSI, MISO, SCK, CS (Chip Select). Synchronous:
   data clocked on SCK edges. Full-duplex: master sends on MOSI while slave sends on
   MISO simultaneously. Faster than I2C (up to 80MHz on ESP32 vs I2C's max 1MHz).
   Clock polarity (CPOL) and phase (CPHA) — four SPI modes. Must match device.
📖 PM: SD card over SPI. Fat filesystem on SD card: MBR → partition table → FAT32
   header → FAT table → data clusters. ESP-IDF FATFS component wraps this.
🔧 Project: Connect an SD card module via SPI. Write a text file. Read it back.
   Log sensor readings to CSV on the SD card with timestamps. This is how every
   data logger works — from car ECU black boxes to weather stations to your
   future Sentigrade measurement records.

**Day 28**
📖 AM: ADC in depth. ESP32-S3 has 12-bit SAR (Successive Approximation Register) ADC.
   SAR works by binary search: try 2048, is voltage above? Try 2048+1024, is it above?
   Repeat 12 times → 12 bits of result. At 240MHz clock, one conversion takes ~5µs.
   ADC non-linearity: ESP32 ADC has known non-linearity especially near 0V and 3.3V.
   Calibration required for precision measurement.
📖 PM: Signal conditioning before ADC. If your sensor outputs 0–100mV (too small for
   full ADC range), you need an op-amp to scale it up to 0–3.3V. If your sensor outputs
   0–5V (too large for 3.3V ADC), you need a resistive divider to scale it down.
🔧 Project: Read a thermistor (NTC) with ESP32-S3 ADC. Apply Steinhart-Hart equation
   to convert resistance to temperature: 1/T = A + B×ln(R) + C×(ln(R))³. Display
   temperature on OLED. This is literally how your fridge thermostat works internally.

**Day 29**
📖 AM: Hardware timers — the most important peripheral for precise timing. ESP32-S3
   has four 64-bit timers running from the APB clock (80MHz). Each timer count = 12.5ns.
   Timer alarm: fires an interrupt at a precise count. No jitter from software scheduling.
   Compare to software delay: `vTaskDelay(1)` in FreeRTOS has ±1 tick (1ms typical)
   of jitter. Hardware timer has ±12.5ns jitter. This 80,000× difference is why
   Sentigrade uses hardware timer for the IR strobe.
📖 PM: Interrupts vs polling. Polling: CPU constantly checks "is the button pressed?"
   in a loop. Wastes 100% of CPU time waiting. Interrupts: button press triggers
   hardware interrupt → CPU pauses current task → runs ISR → resumes. CPU is free
   to do other work between events.
🔧 Project: Use hardware timer alarm to generate a precise 1kHz square wave on a GPIO.
   Verify frequency with another ESP32 counting pulses via interrupt. Compare to
   software-generated square wave. Measure jitter in both cases.

**Day 30**
📖 AM: PWM (Pulse Width Modulation). Duty cycle = on-time / period. Average voltage =
   duty cycle × Vcc. At 1kHz, 50% duty cycle: LED appears at half brightness (eye
   integrates the flashes). At 20kHz: above hearing, used for motor control (no whine).
   LEDC peripheral in ESP32: hardware PWM generator — no CPU involvement needed.
📖 PM: PWM for motor control — DC motor speed is proportional to average voltage.
   PWM + H-bridge = bidirectional speed control. PWM for servo — pulse width encodes
   angle, not speed. 1ms pulse = 0°, 1.5ms = 90°, 2ms = 180°. Period = 20ms (50Hz).
🔧 Project: PWM-control the brightness of your IR LED (at low power, continuous mode
   for this test — not pulse strobe). Write a fade-in/fade-out loop. Then connect a
   small DC motor via IRLZ44N MOSFET. Control motor speed via PWM.

**Day 31**
📖 AM: DMA (Direct Memory Access) deep dive. DMA descriptor: source address,
   destination address, length, next descriptor pointer (for linked list DMA).
   GDMA (General DMA) in ESP32-S3: can connect to I2S, LCD_CAM, SPI, UART, I2C.
   Cache coherency: if CPU has cached a RAM block and DMA writes to the same RAM block,
   CPU might read stale cached data. Must invalidate cache after DMA write.
📖 PM: ESP32-S3 LCD_CAM peripheral — the hardware that interfaces with the OV3660.
   8 parallel data lines, VSYNC, HREF, PCLK. LCD_CAM samples data on PCLK rising
   edges, writes to DMA buffer. When buffer full, DMA fires interrupt. This is what
   `esp_camera_fb_get()` ultimately waits for.

**Day 32**
📖 AM: FreeRTOS fundamentals. Task: a C function that runs in an infinite loop,
   has its own stack, and a priority (1–24 in ESP-IDF). Scheduler: decides which
   task runs. Preemptive: higher priority task can interrupt lower priority at any time.
   Time-slicing: equal priority tasks get alternating time slices (1 tick = 1ms typical).
📖 PM: FreeRTOS synchronization primitives.
   Binary semaphore: 0 or 1. Used to signal events between tasks. ISR gives semaphore,
   task takes semaphore (blocks until given).
   Mutex: like semaphore but with ownership. Only the task that locked it can unlock it.
   Queue: FIFO buffer of fixed-size messages. Producer puts, consumer gets. Blocks when
   full (producer) or empty (consumer).
🔧 Project: Implement the Sentigrade dual-task architecture from scratch:
   - Task A (Core 1, priority 10): waits for semaphore, toggles LED
   - Task B (Core 0, priority 5): counts and prints to serial
   - Timer ISR (every 100ms): gives semaphore
   Verify that Task A preempts Task B exactly when the ISR fires.

**Day 33**
📖 AM: FreeRTOS task notification — lighter than semaphore for single-reader patterns.
   Priority inversion and priority inheritance. Deadlock: how to detect and prevent.
   Stack overflow detection: FreeRTOS can paint the stack with 0xA5A5A5A5 and check
   if the pattern is overwritten — `configCHECK_FOR_STACK_OVERFLOW = 2`.
📖 PM: Watchdog timers. TWDT (Task Watchdog Timer) in ESP-IDF: each task must call
   `esp_task_wdt_reset()` periodically. If a task hangs and misses its reset for 5
   seconds, TWDT reboots the system. This is how embedded systems recover from hangs
   without human intervention. Essential for unattended devices.
🔧 Project: Create a task that simulates a hang (infinite loop for 10 seconds). Enable
   the watchdog. Observe automatic system reset. Add watchdog reset to the task to
   prevent the reset. Verify normal operation resumes.

**Day 34**
📖 AM: Embedded C idioms — the specific patterns used in hardware programming.
   Bit manipulation: `REG |= (1<<n)` sets bit n. `REG &= ~(1<<n)` clears bit n.
   `REG ^= (1<<n)` toggles bit n. `(REG >> n) & 1` reads bit n.
   Volatile: `volatile uint32_t *reg = (uint32_t*)0x3FF44004` — creates a pointer
   to a hardware register address. Reading/writing through this pointer reads/writes
   the hardware register directly.
   Fixed-width types: always use uint8_t, uint16_t, uint32_t, int8_t, int16_t, int32_t.
   Never use int (size is platform-dependent).
📖 PM: State machine implementation in C. enum defines states. switch() on current
   state, with cases for each state handling events and updating next state.
   This pattern eliminates flag spaghetti and makes embedded code maintainable.
🔧 Code: Implement the Sentigrade state machine:
   STATE_BOOT → STATE_READY → STATE_CAPTURING → STATE_PROCESSING → STATE_DISPLAY → back.
   No hardware yet — just states and transitions printed to serial. Add watchdog reset
   in each state's handler.

**Day 35**
📖 AM: Writing a hardware driver — the right way. Layered architecture:
   Application layer: `oled_print("Temperature: 25.3C")`
   Driver API: `ssd1306_write_string(text, font, x, y)`
   HAL (Hardware Abstraction Layer): `i2c_write_bytes(addr, data, len)`
   Hardware registers: I2C peripheral in ESP32
   This separation means swapping the OLED for a different display requires only
   replacing the driver — the application code is unchanged.
📖 PM: Error handling in embedded C. Never use `void` return for functions that can fail.
   Use `esp_err_t` (ESP-IDF's error type): ESP_OK on success, error codes on failure.
   Always check return values. Use `ESP_ERROR_CHECK()` macro during development —
   it asserts and prints the error if non-OK.

**Day 36–37: The Camera Integration**
📖 Day 36 AM: OV3660 architecture. CMOS sensor: each pixel is a photodiode + capacitor +
   reset transistor + select transistor (this is a 4-transistor pixel cell, the standard
   since ~2005). Image Signal Processor (ISP) inside OV3660: demosaicing, auto-exposure,
   auto-white-balance, gamma correction — all configurable via SCCB (a variant of I2C).
📖 Day 36 PM: esp32-camera component architecture. How it uses LCD_CAM + GDMA.
   camera_config_t: every field's meaning. PIXFORMAT_GRAYSCALE: OV3660 outputs only
   luminance — perfect for Sentigrade (we only need brightness, not color).
🔧 Day 37: Connect OV3660 to ESP32-S3. Initialize with esp32-camera. Capture a frame.
   Find the brightest pixel in the frame. Print its coordinates and value to serial.
   This validates: camera wiring, pin mapping, DMA transfer, basic image access.
   Known issue: check that IRCF is removed (shine phone camera at IR LED to verify).

**Day 38–40: Building Sentigrade v0.1**
📖 Day 38: Review the full Sentigrade signal chain. Plan the FreeRTOS task architecture
   on paper. Write pseudocode for every task and ISR.
🔧 Day 39: Implement VSYNC interrupt → semaphore → strobe task. Test strobe with an
   oscilloscope or logic analyzer (₹400 clone Saleae). Verify: strobe fires within
   100µs of VSYNC rising edge. Measure strobe pulse width with logic analyzer.
🔧 Day 40: Integrate camera capture with strobe. In the dark (floppy disk filter on),
   capture frames with and without strobe. Verify that only strobe-illuminated frames
   show any brightness. This confirms the dark-field + strobe hack is working.

**Day 41**
📖 AM: I2C at the protocol level — timing diagrams. Setup time, hold time, start/stop
   condition timing. What happens when the bus is "stuck" low (a device halfway through
   a transaction when power was cut)? Recovery: 9 manual SCL pulses clears any stuck
   device. ESP-IDF `i2c_master_clear_bus()` does this.
📖 PM: UART at the protocol level — baud rate mismatch effects. At 1% frequency error,
   bits shift by 1% per bit. After 10 bits (one byte), accumulated error is 10% —
   past the ±50% tolerance for UART sampling. Practical limit: 2–3% baud rate mismatch.

**Day 42**
📖 AM: Power management in ESP32-S3. Light sleep: CPU pauses, peripherals off,
   wakes on interrupt in ~300µs. Deep sleep: everything off except RTC, wakes on
   timer or GPIO in ~30ms, RAM contents lost. Modem sleep: WiFi radio off between
   beacon intervals. For Sentigrade: deep sleep between measurements extends battery
   life from 1 hour to potentially 6–8 hours.
📖 PM: Li-Po battery management. TP4056 charger IC: CC-CV charging (Constant Current
   until 4.1V, then Constant Voltage until current tapers). Protection IC: DW01A +
   FS8205 MOSFET combination — protects against overcharge (>4.25V), over-discharge
   (<2.5V), and overcurrent (>3A typically).
🔧 Project: Measure your 1000mAh LiPo discharge curve. Log voltage vs time under
   constant 200mA load (use a resistor: R = 3.7/0.2 = 18.5Ω, nearest: 18Ω).
   Plot the curve. Identify the flat region (3.6–3.9V, stable discharge) and
   the knee (~3.4V where voltage drops steeply — time to cut off and recharge).

**Day 43–44**
📖 Day 43: Debugging embedded systems systematically. Debug hierarchy:
   Level 1: Serial logging (printf to UART). Add log levels: DEBUG/INFO/WARN/ERROR.
   Level 2: GPIO toggling — set a pin HIGH at function entry, LOW at exit. Measure
   execution time with logic analyzer or oscilloscope.
   Level 3: Logic analyzer — capture all bus transactions (I2C, SPI, UART, VSYNC,
   strobe) simultaneously and correlate timing.
   Level 4: JTAG debugging — pause execution, inspect registers, step through code.
   ESP32 supports JTAG via USB (no extra hardware needed on some boards).
📖 Day 44: Common embedded failure modes and how to find them. Deadlock: two tasks
   waiting for each other's mutex — detectable when both tasks stop producing output.
   Stack overflow: ESP32 resets with "stack smashing detected" — increase stack size.
   Heap corruption: random crashes, `assert failed: ... heap_caps.c` — scan for
   buffer overruns, use `heap_caps_check_integrity_all()` to find corruption.

**Day 45**
📖 AM: ESP-IDF build system — CMake, Kconfig, component system. How to add a third-party
   component (esp32-camera, SSD1306 driver) to your project.
📖 PM: Version control for hardware. Git for firmware. Commit every working state.
   Tag releases. Branch for experiments. Never push broken code to main.
   KiCad also has git support — version control your schematics too.
   Hardware changes must be committed alongside the firmware that uses them.

✅ **PHASE 2 CHECKPOINT PROJECT — Sentigrade Prototype Validation**

This is the most important checkpoint so far. Implement and validate:

1. Full dual-task FreeRTOS architecture (strobe task + image task on separate cores)
2. VSYNC-synchronized strobe (measure sync latency with logic analyzer — must be <100µs)
3. Dark-field camera capture with IR strobe (verify no ambient light contamination)
4. Find the pupil in a captured frame (threshold + find centroid of bright blob)
5. Print pupil centroid coordinates to OLED display
6. Document everything in GitHub: schematic, BOM, firmware, README with wiring diagram

**Pass criteria:**
- Strobe fires within 100µs of VSYNC rising edge (measured with logic analyzer)
- In dark field, only strobe-illuminated frames show brightness >50/255
- Pupil centroid is detected in at least 8/10 frames of a test eye model
  (a printed circle on paper illuminated by the IR LED works for this test)
- GitHub repository has complete documentation

**What you now understand:** You have built a hardware-synchronized, dual-core,
DMA-driven imaging system from scratch. That is the core of Sentigrade. Everything
from here is making it more accurate, more reliable, and more capable.

---

## PHASE 3: PCB DESIGN & PHYSICAL HARDWARE
### Days 46–65 | From Breadboard to Real Board

**Materials knowledge checkpoint embedded:** Days 50–52 include PCB material selection
(FR4 vs Rogers vs MCPCB), solder chemistry, and thermal interface materials from
the materials pre-track.

---

**Day 46–47: Schematic Design**
📖 Day 46: KiCad installation and interface. Schematic editor: component placement,
   net labels, power symbols, hierarchical sheets. The difference between a schematic
   and a physical circuit: a schematic is an abstract connectivity diagram, not a
   physical layout.
   Learn schematic conventions: power rails at top, ground at bottom, signal flow
   left to right. Annotate every component with: reference designator (R1, C2, U3),
   value (10kΩ, 100nF, ESP32-S3), and manufacturer part number.
📖 Day 47: Reading the ESP32-S3-WROOM reference schematic (available free from
   Espressif). Identify: decoupling capacitors on each VDD pin (why?), crystal circuit
   (why two capacitors?), boot mode resistors (why must IO0 be low to enter bootloader?),
   RF section (why is there a matching network between the chip and antenna?).

**Day 48–49: PCB Layout**
📖 Day 48: PCB layout fundamentals. KiCad PCB editor. Component placement strategy:
   bypass capacitors next to IC power pins (within 2mm). Connectors at board edges.
   High-current traces short and wide. Ground pour on bottom layer.
📖 Day 49: Design rules. Minimum trace width for 1A: 0.3mm at 1oz copper (from IPC-2221
   current-capacity table). Minimum clearance: 0.2mm for JLCPCB standard process.
   Via size: 0.3mm drill, 0.6mm pad (minimum for JLCPCB). Silkscreen: component
   values and reference designators visible on assembled board.
🔧 Project: Complete KiCad schematic for Sentigrade: ESP32-S3 module, IRLZ44N MOSFET,
   IR LED footprint, TP4056 charger, LiPo connector, OLED header, programming header.
   Run DRC (Design Rule Check) — zero errors before proceeding.

**Day 50: Materials Knowledge — PCB Substrates**
📖 AM: FR4 material. Woven fibreglass (E-glass) + epoxy resin (Tg ≈ 135°C or 170°C
   for high-Tg variant). Dk ≈ 4.5 at 1MHz, rises slightly at high frequency.
   Df (dissipation factor) ≈ 0.02 — determines how much RF energy the board absorbs.
   For Sentigrade: FR4 is perfect. All signals are low-frequency (I2C at 400kHz,
   camera DVP at ~40MHz max) — well within FR4's capability.
📖 PM: When FR4 fails and what replaces it.
   Rogers RO4003C: Dk = 3.55 ±0.05, Df = 0.0027 — 7× lower loss than FR4 at GHz.
   Used for: WiFi antenna matching, automotive radar (77GHz), 5G mmWave.
   MCPCB (Metal Core PCB): aluminium or copper core, thermal conductivity 1–3 W/m·K
   vs FR4's 0.3. Used for: high-power LED arrays, motor drives, power modules.
   Flexible PCB (polyimide/Kapton): Dk = 3.5, temperature range -269°C to +400°C.
   Used for: phone ribbon cables, wearable electronics, aerospace flex circuits.

**Day 51: Materials Knowledge — Soldering and Joint Reliability**
📖 AM: Solder chemistry. SAC305 (96.5%Sn, 3%Ag, 0.5%Cu): eutectic alloy, melts sharply
   at 217°C. Lead-free because EU RoHS directive (2003) banned lead in electronics.
   Flux: organic acids that dissolve copper oxide, allowing solder to wet the copper.
   No-clean flux: low-residue, leaves a clear film safe to leave on board.
   Water-soluble flux: very active, removes all oxides, BUT must be fully washed off or
   it continues corroding copper over months.
📖 PM: Failure modes. Cold joint: solder solidified before wetting — dull, grainy surface.
   Solution: reheat longer. Tombstoning: one end of small component lifts during reflow —
   caused by unequal heating. Solution: thermal balance pad design. Tin whiskers: pure
   tin grows whiskers over years → short circuits. Solution: use SAC alloy, not pure tin.
   Intermetallic growth: re-soldering same pad more than twice makes joint brittle.
   Practical rule: if a pad needs 3+ rework attempts, replace the entire component.

**Day 52: Materials Knowledge — Thermal Management**
📖 AM: Thermal resistance network. Every layer between the heat source (transistor
   junction) and the ambient air has a thermal resistance θ (K/W). Temperature rise:
   ΔT = P × (θ_junction-to-case + θ_case-to-heatsink + θ_heatsink-to-ambient).
   For IRLZ44N at 1A pulse: Pd ≈ I²×Rds(on) = 1²×0.022 = 22mW → ΔT negligible.
   For a motor controller MOSFET at 20A: Pd = 400×0.022 = 8.8W → needs heatsink.
📖 PM: Thermal interface materials. Thermal paste (Arctic MX-4): 8.5 W/m·K, fills
   microscopic gaps between component and heatsink. Thermal pad: 1–6 W/m·K, easier
   to apply than paste, compresses to fill gaps, electrically insulating if needed.
   Liquid metal (Thermal Grizzly Conductonaut): 73 W/m·K — 8× better than paste
   but electrically conductive → catastrophic if it spreads to circuit. Used only for
   bare copper/nickel heatsink surfaces, never aluminium (reacts chemically → corrosion).

**Day 53–55: PCB Layout (continued)**
🔧 Day 53: Route the Sentigrade PCB in KiCad. Apply what you know: bypass caps placed
   first, ground pour last. Document why each routing decision was made in GitHub.
🔧 Day 54: Export Gerber files. Submit to JLCPCB (5 PCBs + shipping ≈ ₹600). While
   waiting for boards (7–10 days): study Phase 3 theory.
📖 Day 55: PCB inspection skills. When boards arrive: inspect with 10× loupe for
   solder mask defects, correct drill sizes, correct copper layer. Use multimeter
   continuity to verify all nets before soldering.

**Day 56–60: Sensors, Actuators, and Advanced Peripherals**

Days 56–58 cover sensors in depth. Days 59–60 cover actuators.
(See original roadmap Phase 3 content — not repeated here for brevity but fully integrated.)

**Day 61–65: Power Systems and Battery Management**

Days 61–63: Li-Po chemistry deep dive, BMS design, TP4056 integration.
Day 64: Reverse polarity protection, overvoltage protection, ESD on external connectors.
Day 65: Measure Sentigrade assembled PCB: all voltage rails correct, all subsystems
   functional. Full system test: capture 100 frames, verify crescent detection rate.

✅ **PHASE 3 CHECKPOINT PROJECT — Sentigrade PCB v1.0**

Assembled Sentigrade PCB must:
1. All power rails within 5% of nominal (3.3V, LiPo charge current, LED current)
2. OLED displays correctly on power-on
3. Camera captures frames with IR strobe synchronized to VSYNC
4. Crescent detection working on at least one test subject
5. Battery life >45 minutes at continuous operation
6. GitHub: complete BOM with Mouser/DigiKey part numbers, assembly instructions,
   test procedure, and test results documented

**What combining Days 46–65 teaches:** You can now take an idea all the way from
concept to a working physical board. That is the full hardware design loop.

---

## PHASE 4: EMBEDDED SOFTWARE ARCHITECTURE
### Days 66–90 | Writing Code That Never Crashes

(Content from original roadmap fully integrated. Key additions:)

**Day 72 addition:** Formal state machine testing. Write unit tests for the Sentigrade
state machine using Unity testing framework (included in ESP-IDF). Test every
state transition. This is what MNC-standard firmware development requires.

**Day 80 addition:** Code review practice. Find a small open-source ESP-IDF project
on GitHub. Read the code systematically. Find at least one bug or improvement.
Submit a pull request. This is how professional engineers work.

---

## PHASE 5: SYSTEMS INTEGRATION
### Days 91–120 | Connecting Everything

(Content from original roadmap fully integrated. Key additions:)

**Day 95 addition:** CAN bus hands-on. Buy an MCP2515 CAN controller module (₹120)
and connect to ESP32. Connect a second one to simulate two ECUs. Send and receive
messages. Use the OBD-II mode on the CAN bus to simulate a car's data network.

**Day 108 addition:** Smart home protocol hands-on. Configure ESP32-H2 (₹500 — has
native Zigbee/Thread radio) as a Zigbee end device. Connect to Home Assistant running
on a Raspberry Pi or old laptop. Control an LED from the app. This is the same
architecture as every commercial smart bulb.

✅ **PHASE 5 CHECKPOINT PROJECT — The Integration Demonstrator**

Build a system that combines EVERYTHING from Phases 0–5:
- Sentigrade captures eye measurement
- Result transmitted via BLE to phone
- Phone app displays measurement
- Measurement logged to SD card with timestamp
- Low battery alert displayed on OLED and sent via BLE notification
- Watchdog timer prevents hangs
- State machine governs all transitions
- Complete documentation in GitHub with video demonstration

---

## MODULES A–H: (Days 121–360)
### Cross-Domain Hardware Expansion

(All content from previous roadmap. Each module now includes a Sentigrade connection.)

**Module A (RF, Days 121–148):**
Sentigrade connection: BLE advertisement of measurement results.
Checkpoint project: Build a BLE beacon that advertises Sentigrade readings.
Phone app (MIT App Inventor or React Native) receives and displays them.

**Module B (Optics, Days 151–175):**
Sentigrade connection: Calculate exact LED offset geometry for your specific
working distance using Bobier-Braddick formula. Build a 3D-printed jig to hold
the LED at exactly 30mm from the lens center.
Checkpoint project: Calibrate Sentigrade against a known prescription (borrow
glasses with labeled prescription, compare measurement to labeled value).

**Smart Home Module (NEW, Days 148–165):**
Day 148–152: Matter protocol stack — read the Matter specification summary
   (available free at csa-iot.org). Thread network topology. OTBR (OpenThread Border
   Router) setup on Raspberry Pi.
Day 153–157: ESP32-H2 development. Build a Matter-over-Thread temperature sensor.
   Commission it into a Home Assistant Matter controller.
Day 158–162: Zigbee coordinator. Set up Zigbee2MQTT on Raspberry Pi. Connect
   commercial Zigbee devices. Understand what packets flow during pairing.
Day 163–165: Teardown a commercial smart device. Identify the MCU, radio chip, and
   power supply IC. Find the UART debug port. Connect to it and read the boot log.
Checkpoint project: Build your own Zigbee-connected temperature/humidity sensor
   using ESP32-H2 and a DHT22. Integrate with Home Assistant. Display on a dashboard.

**Home Appliances Module (NEW, Days 165–180):**
Day 165–168: Fridge teardown (a non-functional unit from a repair shop, or just the
   control board). Identify: compressor relay, thermistor, control MCU, display driver.
   Measure thermistor resistance vs temperature. Identify the hysteresis control algorithm
   from the relay switching pattern.
Day 169–172: Washing machine electronics. VFD (Variable Frequency Drive) for drum motor.
   Water level sensor (pressure transducer). Door interlock microswitch. Control board MCU.
Day 173–175: Common appliance failure modes. Capacitor ESR measurement. How to read
   appliance error codes (usually resistor values on a programming pin or blink patterns).
Day 176–180: Practical repair session. Source a failed appliance from local repair shops
   (many give away boards that need capacitor replacement). Identify failed capacitors
   by ESR measurement and visual inspection. Replace. Document the repair.
Checkpoint project: Successfully repair one appliance control board. Document: failure
   diagnosis method, component identified, replacement sourced, before/after measurements.

**Module F (Measurement & CV, Days 176–210):**
Sentigrade connection: Implement camera calibration for Sentigrade. Use a printed
   checkerboard to calibrate distortion. Apply undistortion to crescent frames.
   Measure how much calibration improves measurement accuracy.
Checkpoint project: Build the photo measurement app described in earlier sessions.
   Use ArUco markers as reference. Measure known objects (coins, credit cards with
   known dimensions) and verify accuracy within 1mm at 50cm distance.

**Automotive Module (Days 180–210, within Phase 5 deep):**
Checkpoint project: OBD-II data logger. ESP32 + MCP2515 + OBD-II connector (₹200).
   Read RPM, coolant temperature, vehicle speed from your own car. Log to SD card.
   Plot on phone app. This is how commercial trip computers work.

**Module D (Linux, Days 211–240):**
Sentigrade connection: Run Sentigrade image processing on a Raspberry Pi Zero 2W
   as a comparison experiment. Compare processing speed (Python + OpenCV on Pi) to
   custom C on ESP32. Quantify the trade-off in measurements/second.
Checkpoint project: Build a Linux-based Sentigrade server. Pi Zero 2W receives
   raw frames from ESP32 via WiFi UDP, runs OpenCV pupil detection, returns result
   to ESP32 for display. This exercises: Linux networking, OpenCV, UDP sockets,
   embedded Linux system design.

**Module E (Computer Architecture, Days 241–275):**
Checkpoint project: Write a cache-friendly version of your crescent detection algorithm
   on a PC. Compare performance to cache-unfriendly version. Measure the difference
   with perf or gprof. Apply the same principles to ESP32 by ensuring pixel processing
   accesses memory sequentially rather than randomly.

**Modules C, G, H (Advanced PCB, Power, Mechanical, Days 276–360):**
Checkpoint project: Design Sentigrade v2.0 PCB — 4-layer board with:
   - Signal integrity analysis of DVP camera lines
   - EMC-conscious layout (ground plane, filtered connectors)
   - Aluminium enclosure with mechanical drawings
   - Custom Li-Po connector with reverse-polarity protection
   - Full DFM review for JLCPCB assembly service (PCBA, not just fabrication)
   Order 5 assembled units. Total cost per unit should be under ₹4,000 at 5-unit
   scale. This is a manufacturable product.

---

## MODULES I–Q + NEW MODULES: (Days 361–750)
### Advanced Domains with Full Daily Schedule

**Module I: Digital Signal Processing (Days 361–390)**

Day 361–363: Discrete Fourier Transform (DFT) — from first principles.
   Start with continuous Fourier series (sum of sines and cosines).
   Discretize: sample at N points, get N frequency components.
   FFT (Fast Fourier Transform): DFT computed in O(N log N) instead of O(N²).
   Implement FFT in Python (use NumPy.fft) on a test signal. Plot the spectrum.

Day 364–366: FIR (Finite Impulse Response) filter design.
   Low-pass filter: passes low frequencies, blocks high. Used to remove noise.
   Filter coefficients from windowed sinc function. Apply to noisy sensor data.
   Implement in C on ESP32 using fixed-point arithmetic (multiply integers,
   shift right to maintain precision — no floating point needed).

Day 367–369: IIR (Infinite Impulse Response) filter — simpler to implement, fewer
   multiplications, but can be unstable. Biquad filter: used in audio equalizers,
   sensor smoothing. Second-order section: 5 coefficients describe the filter.
   Implement a biquad low-pass filter on ESP32 to smooth ADC readings.

Day 370–372: Practical DSP for Sentigrade. Apply a bandpass filter to isolate
   the pupil-frequency spatial content from a row of the crescent image.
   The crescent appears as a step function in pixel intensity — its edge is a
   high-frequency component. Edge-enhanced images allow sub-pixel crescent width
   measurement via interpolation.

Day 373–375: Audio DSP mini-project. Connect INMP441 I2S microphone to ESP32.
   Capture audio. Run FFT. Display frequency spectrum on OLED (a tiny spectrum
   analyzer). This exercises I2S peripheral, real-time FFT, and OLED output.

Day 376–378: Vibration analysis. Connect MPU6050 IMU. Sample accelerometer at 1kHz.
   Run FFT on the data. Identify resonant frequencies. This is how industrial
   predictive maintenance systems detect bearing failure — the bearing's defect
   frequency appears as a peak in the vibration spectrum.

Day 379–381: Signal detection theory. SNR (Signal-to-Noise Ratio): signal power /
   noise power. How many samples must you average to detect a signal 10dB below
   the noise floor? Answer: 10× averaging gives 10dB SNR improvement.
   Apply to Sentigrade: averaging N frames reduces pixel noise by √N — 16 frames
   gives 4× noise reduction, allowing detection of fainter crescents.

Day 382–385: Z-transform and digital filter stability. Poles and zeros in the Z-plane.
   Stability criterion: all poles inside the unit circle. Bilinear transform:
   convert analog filter design (s-domain) to digital (z-domain). Used to convert
   control system designs to digital implementations.

Day 386–390: DSP Checkpoint Project — Sentigrade Noise Analysis.
   Capture 100 frames of the same static test eye model.
   For each pixel in the pupil region, compute: mean, standard deviation, SNR.
   Apply N-frame averaging (N = 1, 4, 9, 16, 25) and measure how SNR improves.
   Verify: SNR ∝ √N. Document: how many frames are needed for reliable crescent
   measurement? This directly answers how fast Sentigrade needs to run to be accurate.

---

**Module J: Control Systems (Days 391–430)**

Day 391–393: Transfer functions and the Laplace domain.
   Why Laplace? A differential equation in the time domain (hard to analyze) becomes
   an algebraic equation in the s-domain (easy to manipulate).
   First-order system: H(s) = 1/(τs + 1). Time constant τ: time to reach 63.2% of
   final value. This is the same τ as the RC circuit from Day 3 — now we have the
   mathematical framework that explains why.

Day 394–396: Bode plots — gain and phase vs frequency.
   Gain margin: how much gain can increase before instability.
   Phase margin: how much phase can lag before instability. 45° phase margin is a
   common design target — gives adequate stability without excessive oscillation.
   Plot Bode diagram for Sentigrade's LED temperature control loop (future feature).

Day 397–400: PID controller design analytically.
   Ziegler-Nichols method: set I and D to zero. Increase P until system oscillates.
   That gain is Ku, that period is Tu. PID gains: Kp = 0.6Ku, Ti = Tu/2, Td = Tu/8.
   Implement on ESP32: a PID temperature controller using a thermistor + PWM heater
   (a resistor dissipating power). This is the exact circuit in a 3D printer hotend.

Day 401–405: State-space representation — the modern control theory language.
   x' = Ax + Bu (state equation). y = Cx + Du (output equation).
   Advantage over transfer functions: handles multiple-input multiple-output (MIMO)
   systems, non-linear systems (linearized around operating point).
   Implement state-space model for a simple second-order system.

Day 406–410: Discrete control — implementing continuous controllers in digital MCUs.
   Tustin (bilinear) transformation converts continuous PID to discrete.
   Sampling rate must be 10–20× faster than the control bandwidth.
   Implement discrete PID on ESP32 at 10Hz control rate for the temperature controller.

Day 411–415: Advanced control — feedforward, cascade, and observer design.
   Feedforward: know the disturbance in advance, compensate before error appears.
   Cascade: outer loop controls setpoint of inner loop (position → velocity → current
   in a motor controller — the standard three-loop architecture in servo drives).
   Luenberger observer: estimate unmeasurable states from measurable outputs.

Day 416–420: Control systems in Sentigrade's context — the measurement stability loop.
   Sentigrade measures the same eye repeatedly. Each measurement has noise. If we
   want to present a stable reading rather than a noisy one, we implement a Kalman
   filter — a state estimator that balances measurement noise against process noise.
   Implement a 1D Kalman filter for Sentigrade's diopter output. Tune the
   measurement noise variance R (from your DSP noise analysis) and process noise
   variance Q (how fast does actual eye power change? Very slowly — Q is small).

Day 421–430: Control Checkpoint Project — Closed-Loop Temperature Control.
   Build a temperature controller: ESP32 reads thermistor, drives PWM heater (50Ω
   resistor as heater element), implements discrete PID.
   Requirements: setpoint 40°C. Rise time <30 seconds. Steady-state error <0.5°C.
   Overshoot <5°C. Tune Kp, Ki, Kd. Plot step response. Verify specs met.
   This is the same control loop in: your 3D printer, your car's cabin temperature
   control, your fridge compressor cycling, your soldering iron temperature.

---

**Module K: FPGA & HDL (Days 431–490)**

Day 431–435: What an FPGA is — an array of LUTs (Look-Up Tables) and flip-flops
   that can be configured to implement any combinational or sequential logic.
   Not a CPU running code — the logic gates themselves are configured in silicon.
   Verilog syntax: module, always block, assign statement, posedge, reg vs wire.

Day 436–440: First Verilog project — LED blinker. `always @(posedge clk)` counter.
   When counter reaches 50,000,000 (at 50MHz = 1 second), toggle LED.
   This is "Hello World" for FPGAs. Synthesize for iCE40 FPGA (Lattice iCEstick,
   ~₹2500 — the cheapest full-featured FPGA board).

Day 441–445: Finite state machines in Verilog. Implement the Sentigrade state machine
   in hardware. Each state transition takes exactly 1 clock cycle — no jitter possible.
   This is how safety-critical systems (automotive, aerospace) implement state machines.

Day 446–450: UART transmitter in Verilog. Design and implement a UART transmitter
   from scratch: load parallel byte → shift out serially at baud rate. Verify with
   logic analyzer that the resulting waveform decodes correctly. This exercises:
   shift registers, timing, synchronous design methodology.

Day 451–460: Image processing pipeline in FPGA. The same threshold-and-blob detection
   from Sentigrade, but implemented in hardware:
   - Pixel comes in serially from camera
   - Threshold comparator: combinational logic, zero latency
   - Pixel counter and sum accumulator for centroid: registered, pipelined
   - Output: centroid coordinates after exactly N clock cycles
   This is how machine vision cameras do real-time processing at 1000+ fps —
   dedicated hardware pipeline with no overhead, no OS, no task switching.

Day 461–470: AXI bus protocol. How IP cores connect inside an FPGA. AXI4-Lite for
   register-mapped control. AXI4-Stream for high-bandwidth data. Implement a simple
   AXI4-Lite register bank to control an LED from a software interface.

Day 471–480: HLS (High-Level Synthesis). Write C code, synthesize to Verilog
   automatically. Tools: Xilinx Vitis HLS (free for student use). Implement the
   Sentigrade crescent detection in C, synthesize to Verilog, compare resource
   usage and timing to hand-written Verilog.

Day 481–490: FPGA Checkpoint Project — Hardware-Accelerated Sentigrade.
   Implement the full Sentigrade processing pipeline in FPGA:
   Camera → pixel stream → hardware threshold → hardware blob detector → centroid
   output → UART to ESP32 for display.
   Compare processing latency to ESP32 software implementation.
   Expected result: FPGA processes one frame in ~0.5ms vs ESP32's ~8ms.
   Document: resource utilization (LUTs, flip-flops, BRAM), timing (max frequency),
   latency comparison.

---

**ASIC Design Module (Days 491–530)**

Day 491–495: Digital design flow — RTL (Register Transfer Level) → synthesis →
   place & route → GDSII (the file format for chip fabrication). Each step is
   performed by a different tool. Open-source flow: Yosys (synthesis) →
   OpenROAD (place & route) → Magic (layout viewer) → KLayout (GDSII viewer).

Day 496–500: OpenLane — the complete open-source RTL-to-GDSII flow.
   Clone the OpenLane repository. Run the included example (a counter design).
   Examine the output: GDS2 file contains the actual polygon shapes that will be
   etched into silicon.

Day 501–505: Skywater 130nm PDK (Process Design Kit). This is the first open-source
   silicon fabrication process, developed by Google and SkyWater Technology.
   It includes: standard cell library (NAND, NOR, DFF, mux, etc. in 130nm CMOS),
   device models for SPICE simulation, design rules.
   Design a simple 4-bit counter using the Skywater cells. Run DRC (Design Rule Check)
   and LVS (Layout vs Schematic) — the two mandatory checks before fabrication.

Day 506–515: Analog circuit design for silicon. Differential pair, current mirror,
   bandgap reference — the building blocks of analog IC design.
   Use SPICE (Ngspice, free) with Skywater device models. Simulate a differential
   amplifier. Verify offset voltage, gain, CMRR (Common Mode Rejection Ratio).

Day 516–525: Mixed-signal IC design. ADC (SAR architecture) implementation in
   Skywater PDK. How the digital SAR logic connects to the analog comparator and
   DAC capacitor array. This is what is inside the ESP32's ADC.

Day 526–530: ASIC Checkpoint Project — Submit a chip design for fabrication.
   The Google/Efabless shuttle program runs periodically (search "efabless chipIgnite").
   Design a small functional block (UART receiver, simple filter, temperature sensor
   read-out circuit) and submit for free fabrication. You will receive real silicon chips
   of your design 4–6 months later. This is the most significant hardware milestone
   possible at the hobby level.

---

**Tesla & AI-in-Vehicle Hardware Module (Days 530–550)**
(See previous roadmap for full content. Daily schedule:)
Day 530–533: FSD chip architecture — systolic arrays, TOPS calculation, memory bandwidth.
Day 534–537: Dojo D1 chip — training vs inference hardware, D1 specifications.
Day 538–541: OTA update architecture for safety-critical firmware — A/B partitioning,
   cryptographic signing, rollback protection.
Day 542–545: Redundant hardware architecture — dual-chip voting, lockstep execution,
   ASIL (Automotive Safety Integrity Level) requirements.
Day 546–550: Tesla Checkpoint: Analyze one FSD system failure report (Tesla publishes
   NHTSA reports). Trace the failure from sensor input → neural network → actuator
   output. Identify which hardware component was involved. Propose a hardware fix.

---

**AI Hardware / NPU Module (Days 550–590)**
(See previous roadmap for full content. Daily schedule:)
Day 550–555: Systolic array deep dive. Implement a 4×4 matrix multiply in Python,
   then in Verilog as a 4×4 MAC array. Compare performance.
Day 556–560: Quantization. Train a small CNN (3-layer) in PyTorch to classify
   MNIST digits. Quantize from FP32 to INT8 using PyTorch quantization toolkit.
   Measure accuracy change and model size change.
Day 561–565: Deploy on ESP32-S3's AI acceleration. Convert the MNIST classifier
   to TensorFlow Lite. Run inference on ESP32-S3. Measure: inference time per image,
   RAM usage, accuracy vs full-precision model.
Day 566–570: Edge AI for Sentigrade — replace threshold-based pupil detection
   with a tiny CNN trained to detect pupil center and radius in dark-field IR images.
   Collect 500 labeled frames (with manually marked pupil centers). Train on PC.
   Deploy to ESP32-S3. Compare accuracy to threshold method.
Day 571–575: Apple Neural Engine analysis. How the ANE in M-series Macs handles
   16-bit matrix multiply, neural engine FLOPS vs GPU FLOPS.
Day 576–580: HW-SW Co-Design Checkpoint: Profile the Sentigrade processing pipeline.
   Identify the most compute-intensive operation. Move it to FPGA (from ASIC module)
   or hardware-accelerated ESP32 instruction. Measure speedup. Document the
   co-design decision: what was moved to hardware, why, and what the trade-off was.

---

**Bioelectronics Module (Days 541–580 — overlaps with AI module by design)**
Day 541–544: Biopotential amplifier design. INA128 instrumentation amplifier:
   CMRR >100dB, differential gain = 1 + 50kΩ/Rg. Configure for ECG: Rg = 500Ω,
   gain = 101. Bandwidth: 0.05–150Hz (IEC standard for ECG).
Day 545–548: Electrode-skin interface. Ag/AgCl electrode chemistry. Electrode gel:
   ionic solution that reduces electrode impedance from MΩ (dry) to kΩ (wet).
   Motion artifact: electrode moves → electrode potential changes → artifact in signal.
   Mitigation: flexible electrode mounting, signal processing (adaptive filtering).
Day 549–552: Build a simple pulse monitor (photoplethysmography, PPG, not ECG).
   IR LED + photodiode placed on fingertip. The transmitted/reflected light varies
   with blood volume changes. Much simpler than ECG — no skin preparation needed.
   This is how every smartwatch pulse sensor works.
Day 553–556: Safety isolation for body-contact electronics. Optocoupler provides
   electrical isolation: infrared LED on input side, photodiode on output side,
   no electrical connection. VRMS isolation = 3kV typical. Essential for anything
   connecting to mains-powered equipment while also touching a human.
Day 557–580: Bioelectronics Checkpoint — Build the pulse monitor to medical-device
   standard. Requirements: displays pulse rate accurate to ±2 BPM, filters motion
   artifacts, runs on Li-Po battery (isolated from mains), data logged to SD card.
   Verify against a commercial pulse oximeter. Document clinical accuracy.

---

## Days 581–750: Remaining Modules
(Industrial, MEMS, Aerospace, Energy Harvesting, Neuromorphic, Quantum Awareness)

Each follows the same daily structure: 2 hours theory → 1 hour simulation → 1 hour
hands-on → 30 minutes documentation → Sentigrade connection noted.

Full daily schedules available on request for any specific module.

---

## The Combinatorial Learning Map
### How Each Day's Learning Feeds Every Other

This is the mental model you asked for — how combining domains creates capabilities
greater than the sum of parts.

```
        MATHEMATICS
        (Days P1-P21)
              │
    ┌─────────┼──────────┐
    │         │          │
PHYSICS   SIGNALS    CONTROL
(P22-P31) (DSP I)   (Mod J)
    │         │          │
    └────┬────┘          │
         │               │
   SEMICONDUCTORS   STATE MACHINES
   (Phase 1)        (Phase 2+4)
         │               │
    ┌────┴────────────────┤
    │                    │
 ANALOG              DIGITAL
 ELECTRONICS         ELECTRONICS
 (op-amps,           (MCUs, FPGAs,
 filters, power)     protocols, OS)
    │                    │
    └────────┬───────────┘
             │
      SYSTEM DESIGN
      (trade-offs, architecture)
             │
    ┌────────┼───────────┬──────────────┐
    │        │           │              │
HARDWARE  EMBEDDED   AI-HARDWARE   MATERIALS
PRODUCTS  SYSTEMS    INTEGRATION   KNOWLEDGE
(PCBs,    (RTOS,     (NPUs, Edge   (reliability,
 power,    drivers,   AI, Tesla     substrates,
 sensors)  debug)     hardware)     failure modes)
    │        │           │              │
    └────────┴───────────┴──────────────┘
                         │
                 CREATION CAPABILITY
                 ┌───────┴────────┐
         You can build:    You can understand:
         Any hardware      Any hardware
         system            system
         from scratch.     you encounter.
```

**The key combinatorial gains:**

**Physics + Semiconductors → You understand WHY components fail**
Not just "capacitor failed" but "the electrolyte decomposed at elevated temperature
because the ESR increased, the ripple current caused I²R heating, the temperature
exceeded the capacitor's rated temperature..."

**DSP + Control + AI Hardware → You can design intelligent sensing systems**
Not just "sensor outputs a number" but "sensor outputs a noisy signal → Kalman filter
estimates true value → controller minimizes error → neural network adapts to changing
conditions → hardware accelerator makes this real-time."

**Materials + PCB Design → Your boards work in real environments, not just on a desk**
Not just "board works at room temperature" but "board will survive 100 thermal cycles
between -20°C and +85°C because I matched solder pad thermal mass, chose a Tg=170°C
FR4, and used conformal coating on exposed traces."

**FPGA + ASIC + AI Hardware → You can design custom chips**
Starting from your Sentigrade FPGA image processing pipeline → extending to a full
custom ASIC with integrated NPU for the crescent detection → designing the chip's
power management and I/O → submitting for fabrication. This is the complete path.

**All domains together → The five questions you can answer about anything:**
1. What physics does this exploit?
2. What is the signal chain from physics to number?
3. What are the constraints and trade-offs in this design?
4. Where will it fail and how will I detect it before it does?
5. How would I build this myself at minimum cost with maximum accuracy?

---

## What You Are Capable of After Each Milestone

| Milestone | Days | Specific capabilities unlocked |
|-----------|------|-------------------------------|
| Prerequisites | P1–P38 | Read and derive every circuit formula. Understand WHY before memorizing HOW. |
| Phase 0 complete | 7 | Predict circuit behavior. Use a multimeter professionally. |
| Phase 1 complete | 21 | Understand and design transistor circuits. Explain how every power supply works. |
| Phase 2 complete | 45 | Build Sentigrade prototype. Write production-quality RTOS firmware. |
| Phase 3 complete | 65 | Design and order custom PCBs. Repair appliances at component level. Understand material choices. |
| Phase 4 complete | 90 | Write firmware that never crashes. Implement state machines and drivers to MNC standard. |
| Phase 5 complete | 120 | Build networked systems. Understand CAN bus, smart home protocols, full system integration. |
| Modules A+B+Home+Appliance | 180 | Understand and modify any consumer wireless device. Repair any home appliance. Build smart home sensors. |
| Module F+Automotive | 210 | Build the photo measurement app. Read OBD-II data from any car. |
| Modules D+E | 275 | Repair laptops at component level. Administer Linux servers. Write kernel drivers. |
| Modules C+G+H | 360 | Design a manufacturable product. Full product: PCB+firmware+enclosure+power. |
| Modules I+J | 430 | Design provably stable control systems. Implement real-time signal processing on MCUs. |
| Module K+ASIC | 530 | Design hardware in Verilog. Submit a chip for real fabrication. |
| Tesla+AI Hardware | 580 | Understand every AI hardware product. Optimize neural networks for specific hardware. |
| All modules | 750 | Open any manufactured hardware object and understand, diagnose, modify, or rebuild it. |

---
