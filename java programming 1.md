# ☕ Java Complete Mastery Roadmap
### From Core Fundamentals → MNC Production-Grade Java Engineer
#### *Day-by-Day · Project-by-Project · Interview-Ready*

> **Reference:** Built from Java Programming MNC Interview Guide  
> **Target:** Tier 1 MNC readiness (Google, Amazon, Microsoft, TCS Digital, Infosys SP)  
> **Projects:** 6 brand-new real-world projects — none overlap with other roadmaps

---

## 📐 MASTER ARCHITECTURE

```
╔═══════════════════════════════════════════════════════════════════════╗
║                  JAVA MASTERY — 75-DAY MAP                           ║
╠═══════════════════════════════════════════════════════════════════════╣
║  PHASE 1 (Days 1–12):   CORE JAVA + JVM INTERNALS                   ║
║  PHASE 2 (Days 13–22):  OOP + DESIGN PATTERNS                       ║
║  PHASE 3 (Days 23–32):  COLLECTIONS + STREAMS + JAVA 8+             ║
║  PHASE 4 (Days 33–42):  MULTITHREADING + CONCURRENCY                ║
║  PHASE 5 (Days 43–52):  SPRING BOOT + JPA + SECURITY                ║
║  PHASE 6 (Days 53–65):  TESTING + DEVOPS + MICROSERVICES            ║
║  PHASE 7 (Days 66–75):  DSA IN JAVA + INTERVIEW PREP                ║
╚═══════════════════════════════════════════════════════════════════════╝

PROJECTS:
  P1 — Hospital Appointment Booking System     (Days 10–12) — OOP
  P2 — Multi-Threaded Log File Processor       (Days 38–42) — Concurrency
  P3 — Student Grade Analytics Engine          (Days 30–32) — Streams
  P4 — Blood Bank Management REST API          (Days 50–52) — Spring Boot
  P5 — Real-Time Package Delivery Tracker      (Days 60–62) — WebSocket+Redis
  P6 — Coupon & Discount Microservice Engine   (Days 70–75) — Microservices
```

---

## 🛠️ TECH STACK

| Layer | Tool | Why |
|---|---|---|
| Language | Java 17 LTS | LTS version used in production at MNCs |
| Build | Maven 3.9 | Industry standard for dependency management |
| Framework | Spring Boot 3.x | Powers 80% of MNC Java backends |
| ORM | Spring Data JPA + Hibernate | Standard persistence layer |
| Database | PostgreSQL 16 | Production-grade relational DB |
| Cache | Redis 7 | Session management, rate limiting |
| Messaging | Apache Kafka | Event-driven microservices |
| Testing | JUnit 5 + Mockito | Required in every MNC Java project |
| Docs | Swagger/OpenAPI 3 | API documentation standard |
| Containers | Docker + Docker Compose | Containerised deployment |
| CI/CD | GitHub Actions | Automated build and test pipeline |
| Monitoring | Spring Actuator + Prometheus | Production observability |

---

## 📝 DOCUMENTATION STRATEGY

```
GitHub Structure:
java-mastery/
├── core-java/          ← Phase 1–4 practice code
├── spring-boot/        ← Phase 5–6 framework code
├── dsa-java/           ← Phase 7 DSA solutions
├── projects/
│   ├── 01-hospital-booking/
│   ├── 02-log-processor/
│   ├── 03-grade-analytics/
│   ├── 04-blood-bank-api/
│   ├── 05-delivery-tracker/
│   └── 06-coupon-engine/
└── interview-prep/
    ├── core-java-qa.md
    ├── collections-qa.md
    ├── spring-boot-qa.md
    └── lld-designs/
```

**Daily template:** `core-java/day-XX-topic.md`
- Concept explained in your own words
- Code snippet you wrote
- Interview Q&A for that topic
- Active recall questions

---

---

# 🔵 PHASE 1: CORE JAVA + JVM INTERNALS (Days 1–12)

> **Goal:** Understand how Java actually works — not just syntax. The JVM is tested at every MNC technical interview.

---

## DAY 1: JVM Architecture + Java Compilation

### Why This Matters
Every senior Java interview starts here: "What happens when you run a Java program?" Getting this wrong signals a shallow understanding.

### Core Concepts

```
SOURCE CODE (.java)
      ↓ javac compiler
BYTECODE (.class)          ← Platform-independent intermediate form
      ↓ JVM loads
CLASS LOADER               ← Bootstrap → Extension → Application
      ↓
RUNTIME DATA AREAS:
  Method Area:   Class metadata, static variables, constants
  Heap:          All objects live here (GC managed)
  Stack:         One per thread. Frames = method calls. Local variables.
  PC Register:   Current instruction pointer per thread
  Native Stack:  For native (C/C++) method calls

EXECUTION ENGINE:
  Interpreter: Executes bytecode line by line (slow start)
  JIT Compiler: Compiles hot code to native machine code (fast after warmup)
  GC:          Reclaims unused heap memory

KEY INTERVIEW POINTS:
  "Write once, run anywhere" = bytecode runs on any JVM
  JDK = JRE + development tools (javac, jdb)
  JRE = JVM + standard libraries
  JVM = Just the execution engine
```

### Practical Task
```java
// Day1_JVMDemo.java — Observe JVM memory
public class Day1_JVMDemo {
    static int staticVar = 100;           // → Method Area
    int instanceVar = 200;               // → Heap (with object)

    public static void main(String[] args) {
        Day1_JVMDemo obj = new Day1_JVMDemo(); // obj reference → Stack, obj → Heap

        // Runtime memory info
        Runtime rt = Runtime.getRuntime();
        System.out.println("JVM name: " + System.getProperty("java.vm.name"));
        System.out.printf("Max heap:   %,d bytes%n", rt.maxMemory());
        System.out.printf("Total heap: %,d bytes%n", rt.totalMemory());
        System.out.printf("Free heap:  %,d bytes%n", rt.freeMemory());
        System.out.printf("Used heap:  %,d bytes%n",
                rt.totalMemory() - rt.freeMemory());
    }
}
// Compile: javac Day1_JVMDemo.java
// Run with heap info: java -verbose:gc -Xms64m -Xmx256m Day1_JVMDemo
```

### ✅ Active Recall
1. Where is a static variable stored in JVM memory?
2. What is the difference between JIT and the Interpreter?
3. If a method is called recursively 10,000 times, which JVM area fills up?

---

## DAY 2: Data Types, String Pool, and Memory

### Core Concepts

```java
// STRING POOL — the most common interview trap
String s1 = "hello";            // → goes to String Pool (Method Area)
String s2 = "hello";            // → reuses same Pool object
String s3 = new String("hello");// → NEW object on Heap (different reference)

System.out.println(s1 == s2);   // true  (same pool reference)
System.out.println(s1 == s3);   // false (different heap object)
System.out.println(s1.equals(s3)); // true (same value)

// INTERN — force heap String into pool
String s4 = s3.intern();
System.out.println(s1 == s4);   // true (now in pool)

// IMMUTABILITY — why String is immutable
// 1. Thread-safe (no synchronisation needed)
// 2. String Pool works (can safely share references)
// 3. Hash code can be cached (HashMap keys)

// StringBuilder vs StringBuffer
// StringBuilder: NOT thread-safe, FASTER
// StringBuffer:  Thread-safe (synchronized), SLOWER
StringBuilder sb = new StringBuilder();
for (int i = 0; i < 1000; i++) {
    sb.append(i);           // O(1) amortised — one object, no new allocations
}
String result = sb.toString();
// vs: String s = "" + 0 + 1 + ... — creates 1000 String objects!
```

### Practical Task
```java
// StringBenchmark.java — prove concatenation is slow
public class StringBenchmark {
    public static void main(String[] args) {
        int N = 50_000;

        // BAD: String concatenation — O(n²) time, n objects created
        long start = System.nanoTime();
        String s = "";
        for (int i = 0; i < N; i++) s += "x";
        System.out.printf("String concat:   %,d ms%n",
                (System.nanoTime() - start) / 1_000_000);

        // GOOD: StringBuilder — O(n) time, 1 object
        start = System.nanoTime();
        StringBuilder sb = new StringBuilder();
        for (int i = 0; i < N; i++) sb.append("x");
        sb.toString();
        System.out.printf("StringBuilder:   %,d ms%n",
                (System.nanoTime() - start) / 1_000_000);
    }
}
```

### ✅ Active Recall
1. `"abc" == new String("abc")` — true or false? Why?
2. Why is String immutable in Java? Name two consequences.
3. When would you use StringBuffer over StringBuilder?

---

## DAY 3: OOP — Classes, Objects, Constructors, `this`, `super`

```java
// BankAccount.java — realistic OOP example
public class BankAccount {
    private final String accountNumber;   // final = immutable after construction
    private String ownerName;
    private double balance;

    // Default constructor
    public BankAccount() {
        this("UNKNOWN-000", "Unknown", 0.0); // constructor chaining with this()
    }

    // Parameterised constructor
    public BankAccount(String accountNumber, String ownerName, double initialDeposit) {
        if (initialDeposit < 0)
            throw new IllegalArgumentException("Initial deposit cannot be negative");
        this.accountNumber = accountNumber;   // this disambiguates field vs param
        this.ownerName = ownerName;
        this.balance = initialDeposit;
    }

    // Copy constructor
    public BankAccount(BankAccount other) {
        this(other.accountNumber, other.ownerName, other.balance);
    }

    public void deposit(double amount) {
        if (amount <= 0) throw new IllegalArgumentException("Deposit must be positive");
        this.balance += amount;
    }

    public void withdraw(double amount) {
        if (amount > balance) throw new IllegalStateException("Insufficient funds");
        this.balance -= amount;
    }

    @Override
    public String toString() {
        return String.format("Account[%s | Owner: %s | Balance: ₹%.2f]",
                accountNumber, ownerName, balance);
    }

    // Getters (no setters for accountNumber — immutable)
    public String getAccountNumber() { return accountNumber; }
    public double getBalance() { return balance; }
}
```

---

## DAY 4: Inheritance + Polymorphism + Abstraction

```java
// Shape hierarchy — classic OOP interview example
abstract class Shape {
    protected String color;

    public Shape(String color) { this.color = color; }

    // Abstract: subclasses MUST implement
    public abstract double area();
    public abstract double perimeter();

    // Concrete method: shared behaviour
    public void displayInfo() {
        System.out.printf("%s [color=%s, area=%.2f, perimeter=%.2f]%n",
                getClass().getSimpleName(), color, area(), perimeter());
    }
}

class Circle extends Shape {
    private double radius;
    public Circle(String color, double radius) {
        super(color);
        this.radius = radius;
    }
    @Override public double area()      { return Math.PI * radius * radius; }
    @Override public double perimeter() { return 2 * Math.PI * radius; }
}

class Rectangle extends Shape {
    private double width, height;
    public Rectangle(String color, double width, double height) {
        super(color); this.width = width; this.height = height;
    }
    @Override public double area()      { return width * height; }
    @Override public double perimeter() { return 2 * (width + height); }
}

// RUNTIME POLYMORPHISM in action:
public class PolymorphismDemo {
    public static void main(String[] args) {
        Shape[] shapes = {
            new Circle("red", 5),
            new Rectangle("blue", 4, 6),
            new Circle("green", 3)
        };
        double totalArea = 0;
        for (Shape s : shapes) {
            s.displayInfo();                    // dynamic dispatch — correct method at runtime
            totalArea += s.area();              // each class's own area() is called
        }
        System.out.printf("Total area: %.2f%n", totalArea);
    }
}
```

---

## DAY 5: Interfaces + Functional Interfaces + SOLID

```java
// Interface with default and static methods (Java 8+)
public interface Printable {
    void print();                           // abstract — must implement

    default void printWithBorder() {        // default — can override or use as-is
        System.out.println("═══════════════");
        print();
        System.out.println("═══════════════");
    }

    static Printable of(String text) {      // static factory — use via Printable.of(...)
        return () -> System.out.println(text);
    }
}

// FUNCTIONAL INTERFACE — exactly one abstract method → usable as lambda
@FunctionalInterface
interface Validator<T> {
    boolean validate(T value);
}

// SOLID PRINCIPLES — quick reference
// S — Single Responsibility: One class, one reason to change
// O — Open/Closed: Open for extension, closed for modification
// L — Liskov Substitution: Subclass usable wherever superclass expected
// I — Interface Segregation: Small, specific interfaces > one large interface
// D — Dependency Inversion: Depend on abstractions, not concrete classes

// DIP Example:
interface NotificationService {
    void send(String message, String recipient);
}
class EmailNotification implements NotificationService {
    @Override public void send(String msg, String to) {
        System.out.println("Email to " + to + ": " + msg);
    }
}
class OrderService {
    private final NotificationService notifier;  // depends on interface, not EmailNotification
    public OrderService(NotificationService notifier) { this.notifier = notifier; }
    public void placeOrder(String item, String user) {
        // business logic...
        notifier.send("Your order for " + item + " is confirmed!", user);
    }
}
```

---

## DAY 6: Exception Handling + Custom Exceptions

```java
// Production-grade exception handling
public class ExceptionHandlingDemo {

    // CUSTOM EXCEPTION HIERARCHY
    public static class AppException extends RuntimeException {
        private final String errorCode;
        public AppException(String errorCode, String message) {
            super(message);
            this.errorCode = errorCode;
        }
        public AppException(String errorCode, String message, Throwable cause) {
            super(message, cause);
            this.errorCode = errorCode;
        }
        public String getErrorCode() { return errorCode; }
    }

    public static class ResourceNotFoundException extends AppException {
        public ResourceNotFoundException(String resource, Object id) {
            super("RESOURCE_NOT_FOUND", resource + " with id=" + id + " not found");
        }
    }

    public static class InsufficientFundsException extends AppException {
        public InsufficientFundsException(double required, double available) {
            super("INSUFFICIENT_FUNDS",
                    String.format("Required: %.2f, Available: %.2f", required, available));
        }
    }

    // TRY-WITH-RESOURCES — always use for I/O
    public static String readFile(String path) {
        try (var reader = new java.io.BufferedReader(new java.io.FileReader(path))) {
            var sb = new StringBuilder();
            String line;
            while ((line = reader.readLine()) != null) sb.append(line).append('\n');
            return sb.toString();
        } catch (java.io.FileNotFoundException e) {
            throw new ResourceNotFoundException("File", path);
        } catch (java.io.IOException e) {
            throw new AppException("IO_ERROR", "Failed to read file: " + path, e);
        }
        // reader.close() called automatically — even on exception!
    }

    public static void main(String[] args) {
        try {
            String content = readFile("nonexistent.txt");
        } catch (ResourceNotFoundException e) {
            System.err.printf("[%s] %s%n", e.getErrorCode(), e.getMessage());
        } catch (AppException e) {
            System.err.printf("[%s] Unexpected error: %s%n", e.getErrorCode(), e.getMessage());
        }
    }
}
```

---

## DAY 7: Java Memory Model + Garbage Collection

```java
// GC demonstration
public class GCDemo {
    public static void main(String[] args) throws InterruptedException {
        Runtime rt = Runtime.getRuntime();
        System.out.printf("Before: Used = %,d KB%n",
                (rt.totalMemory() - rt.freeMemory()) / 1024);

        // Allocate objects — will become garbage when references are lost
        for (int i = 0; i < 10_000; i++) {
            new byte[1024 * 10];   // 10KB each — total 100MB
        }
        System.out.printf("After alloc: Used = %,d KB%n",
                (rt.totalMemory() - rt.freeMemory()) / 1024);

        System.gc();   // REQUEST (not force) garbage collection
        Thread.sleep(200);
        System.out.printf("After GC: Used = %,d KB%n",
                (rt.totalMemory() - rt.freeMemory()) / 1024);

        /*
         * GC GENERATIONS:
         * Young Generation (Eden + S0 + S1): New objects here. Minor GC frequent.
         * Old Generation (Tenured): Long-lived objects promoted here. Major GC rare but slow.
         * Metaspace: Class metadata (replaces PermGen in Java 8+)
         *
         * GC ALGORITHMS:
         * Serial GC:   Single thread. For small heaps.
         * Parallel GC: Multiple threads. Throughput-oriented. Default in Java 8.
         * G1 GC:       Predictable pause times. Default in Java 9+.
         * ZGC:         Ultra-low latency (<1ms pauses). Java 15+.
         *
         * JVM TUNING FLAGS:
         * -Xms256m          Minimum heap size
         * -Xmx1g            Maximum heap size
         * -XX:+UseG1GC      Use G1 collector
         * -XX:MaxGCPauseMillis=200   Target max GC pause
         */
    }
}
```

---

## DAYS 8–9: Java I/O + NIO

```java
// NIO.2 (java.nio.file) — the modern way
import java.nio.file.*;
import java.nio.charset.StandardCharsets;
import java.io.*;

public class ModernIO {

    // READ entire file in one line
    public static String readAll(String path) throws IOException {
        return Files.readString(Path.of(path), StandardCharsets.UTF_8);
    }

    // WRITE file
    public static void writeFile(String path, String content) throws IOException {
        Files.writeString(Path.of(path), content, StandardCharsets.UTF_8,
                StandardOpenOption.CREATE, StandardOpenOption.TRUNCATE_EXISTING);
    }

    // WALK directory tree
    public static void listJavaFiles(String dir) throws IOException {
        try (var stream = Files.walk(Path.of(dir))) {
            stream.filter(p -> p.toString().endsWith(".java"))
                  .forEach(p -> System.out.println(p.getFileName()));
        }
    }

    // CSV reading (no external library needed)
    public static void processCSV(String csvPath) throws IOException {
        try (var reader = Files.newBufferedReader(Path.of(csvPath))) {
            reader.lines()
                  .skip(1)                                // skip header
                  .map(line -> line.split(","))
                  .filter(parts -> parts.length >= 3)
                  .forEach(parts -> System.out.printf(
                          "Name: %-20s Score: %s%n", parts[0].trim(), parts[2].trim()));
        }
    }

    // SERIALISATION
    public static void serialise(Object obj, String path) throws IOException {
        try (var oos = new ObjectOutputStream(new FileOutputStream(path))) {
            oos.writeObject(obj);
        }
    }
    public static Object deserialise(String path) throws IOException, ClassNotFoundException {
        try (var ois = new ObjectInputStream(new FileInputStream(path))) {
            return ois.readObject();
        }
    }
}
```

---

## DAYS 10–12: PROJECT 1 — Hospital Appointment Booking System

### Real-World Problem
Hospitals need a system to manage patient registrations, doctor schedules, and appointment bookings — with conflict detection and report generation.

### What This Project Demonstrates
- **OOP Design:** Patient, Doctor, Appointment, Hospital classes with proper encapsulation
- **Collections:** HashMap for doctor lookup, PriorityQueue for appointment scheduling
- **File I/O:** Persistent storage of appointments (CSV + Serialisation)
- **Exception Handling:** Custom exceptions for slot conflicts, invalid data
- **Java 8+ Features:** Streams for reporting, LocalDate/LocalTime for scheduling

### Architecture
```
hospital-booking/
├── src/main/java/com/hospital/
│   ├── model/
│   │   ├── Patient.java          — Patient entity (name, age, contact, medHistory)
│   │   ├── Doctor.java           — Doctor entity (id, name, specialisation, schedule)
│   │   └── Appointment.java      — Appointment (patient, doctor, dateTime, status)
│   ├── service/
│   │   ├── PatientService.java   — Register, find, update patients
│   │   ├── DoctorService.java    — Manage doctors, check availability
│   │   └── AppointmentService.java — Book, cancel, reschedule appointments
│   ├── repository/
│   │   └── FileRepository.java   — Save/load data to CSV and .ser files
│   ├── exception/
│   │   ├── SlotUnavailableException.java
│   │   ├── PatientNotFoundException.java
│   │   └── DoctorNotFoundException.java
│   ├── report/
│   │   └── ReportGenerator.java  — Daily summary, doctor workload stats
│   └── HospitalApp.java          — CLI menu-driven main application
└── pom.xml
```

### Complete Implementation

```java
// model/Patient.java
package com.hospital.model;

import java.io.Serializable;
import java.time.LocalDate;
import java.util.ArrayList;
import java.util.List;
import java.util.UUID;

public class Patient implements Serializable {
    private static final long serialVersionUID = 1L;

    private final String id;
    private String name;
    private int age;
    private String contactNumber;
    private String bloodGroup;
    private final List<String> medicalHistory;
    private final LocalDate registeredOn;

    public Patient(String name, int age, String contactNumber, String bloodGroup) {
        this.id = "PAT-" + UUID.randomUUID().toString().substring(0, 8).toUpperCase();
        this.name = name;
        this.age = age;
        this.contactNumber = contactNumber;
        this.bloodGroup = bloodGroup;
        this.medicalHistory = new ArrayList<>();
        this.registeredOn = LocalDate.now();
    }

    public void addMedicalNote(String note) { medicalHistory.add(note); }

    @Override
    public String toString() {
        return String.format("Patient[%s | %s | Age:%d | Blood:%s | Contact:%s]",
                id, name, age, bloodGroup, contactNumber);
    }

    // Getters
    public String getId()            { return id; }
    public String getName()          { return name; }
    public int getAge()              { return age; }
    public String getContactNumber() { return contactNumber; }
    public String getBloodGroup()    { return bloodGroup; }
    public List<String> getMedicalHistory() { return List.copyOf(medicalHistory); }
    public LocalDate getRegisteredOn(){ return registeredOn; }
}

// model/Doctor.java
package com.hospital.model;

import java.io.Serializable;
import java.time.LocalTime;
import java.util.*;

public class Doctor implements Serializable {
    private static final long serialVersionUID = 1L;

    private final String id;
    private String name;
    private String specialisation;
    private LocalTime shiftStart;
    private LocalTime shiftEnd;
    private int slotDurationMinutes;    // e.g., 30 minutes per patient
    private int maxPatientsPerDay;
    private final Set<String> qualifications;

    public Doctor(String name, String specialisation,
                  LocalTime shiftStart, LocalTime shiftEnd, int slotDurationMinutes) {
        this.id = "DOC-" + UUID.randomUUID().toString().substring(0, 8).toUpperCase();
        this.name = name;
        this.specialisation = specialisation;
        this.shiftStart = shiftStart;
        this.shiftEnd = shiftEnd;
        this.slotDurationMinutes = slotDurationMinutes;
        this.qualifications = new LinkedHashSet<>();
        // Calculate max patients
        long totalMinutes = java.time.Duration.between(shiftStart, shiftEnd).toMinutes();
        this.maxPatientsPerDay = (int) (totalMinutes / slotDurationMinutes);
    }

    public List<LocalTime> getAvailableSlots() {
        List<LocalTime> slots = new ArrayList<>();
        LocalTime slot = shiftStart;
        while (slot.plusMinutes(slotDurationMinutes).compareTo(shiftEnd) <= 0) {
            slots.add(slot);
            slot = slot.plusMinutes(slotDurationMinutes);
        }
        return slots;
    }

    @Override
    public String toString() {
        return String.format("Doctor[%s | Dr. %s | %s | %s–%s | %dmin slots]",
                id, name, specialisation, shiftStart, shiftEnd, slotDurationMinutes);
    }

    public String getId()           { return id; }
    public String getName()         { return name; }
    public String getSpecialisation(){ return specialisation; }
    public LocalTime getShiftStart() { return shiftStart; }
    public LocalTime getShiftEnd()   { return shiftEnd; }
    public int getMaxPatientsPerDay(){ return maxPatientsPerDay; }
}

// model/Appointment.java
package com.hospital.model;

import java.io.Serializable;
import java.time.LocalDate;
import java.time.LocalTime;
import java.util.UUID;

public class Appointment implements Serializable, Comparable<Appointment> {
    private static final long serialVersionUID = 1L;

    public enum Status { SCHEDULED, COMPLETED, CANCELLED, NO_SHOW }

    private final String id;
    private final Patient patient;
    private final Doctor doctor;
    private final LocalDate date;
    private final LocalTime timeSlot;
    private Status status;
    private String notes;

    public Appointment(Patient patient, Doctor doctor, LocalDate date, LocalTime timeSlot) {
        this.id = "APT-" + UUID.randomUUID().toString().substring(0, 8).toUpperCase();
        this.patient = patient;
        this.doctor = doctor;
        this.date = date;
        this.timeSlot = timeSlot;
        this.status = Status.SCHEDULED;
    }

    @Override
    public int compareTo(Appointment other) {
        int dateCmp = this.date.compareTo(other.date);
        return dateCmp != 0 ? dateCmp : this.timeSlot.compareTo(other.timeSlot);
    }

    @Override
    public String toString() {
        return String.format("Apt[%s | %s | Dr.%s | %s %s | %s]",
                id, patient.getName(), doctor.getName(), date, timeSlot, status);
    }

    public String getId()          { return id; }
    public Patient getPatient()    { return patient; }
    public Doctor getDoctor()      { return doctor; }
    public LocalDate getDate()     { return date; }
    public LocalTime getTimeSlot() { return timeSlot; }
    public Status getStatus()      { return status; }
    public void setStatus(Status s){ this.status = s; }
    public void setNotes(String n) { this.notes = n; }
}

// service/AppointmentService.java
package com.hospital.service;

import com.hospital.exception.*;
import com.hospital.model.*;
import java.time.*;
import java.util.*;
import java.util.stream.Collectors;

public class AppointmentService {
    // doctor_id + date → list of booked time slots
    private final Map<String, Map<LocalDate, Set<LocalTime>>> bookedSlots = new HashMap<>();
    private final Map<String, Appointment> appointments = new LinkedHashMap<>();

    public Appointment bookAppointment(Patient patient, Doctor doctor,
                                       LocalDate date, LocalTime timeSlot) {
        validateFutureDate(date, timeSlot);
        if (isSlotBooked(doctor.getId(), date, timeSlot))
            throw new SlotUnavailableException(doctor.getName(), date, timeSlot);

        markSlotBooked(doctor.getId(), date, timeSlot);
        var apt = new Appointment(patient, doctor, date, timeSlot);
        appointments.put(apt.getId(), apt);
        System.out.println("✅ Appointment booked: " + apt);
        return apt;
    }

    public void cancelAppointment(String appointmentId) {
        var apt = findById(appointmentId);
        releaseSlot(apt.getDoctor().getId(), apt.getDate(), apt.getTimeSlot());
        apt.setStatus(Appointment.Status.CANCELLED);
        System.out.println("❌ Cancelled: " + apt.getId());
    }

    public List<Appointment> getAppointmentsByDoctor(String doctorId, LocalDate date) {
        return appointments.values().stream()
                .filter(a -> a.getDoctor().getId().equals(doctorId))
                .filter(a -> a.getDate().equals(date))
                .filter(a -> a.getStatus() == Appointment.Status.SCHEDULED)
                .sorted()
                .collect(Collectors.toList());
    }

    public List<Appointment> getAppointmentsByPatient(String patientId) {
        return appointments.values().stream()
                .filter(a -> a.getPatient().getId().equals(patientId))
                .sorted()
                .collect(Collectors.toList());
    }

    public List<LocalTime> getAvailableSlots(Doctor doctor, LocalDate date) {
        Set<LocalTime> booked = bookedSlots
                .getOrDefault(doctor.getId(), Collections.emptyMap())
                .getOrDefault(date, Collections.emptySet());
        return doctor.getAvailableSlots().stream()
                .filter(slot -> !booked.contains(slot))
                .collect(Collectors.toList());
    }

    private void validateFutureDate(LocalDate date, LocalTime time) {
        if (date.isBefore(LocalDate.now()) ||
            (date.equals(LocalDate.now()) && time.isBefore(LocalTime.now())))
            throw new IllegalArgumentException("Cannot book appointment in the past");
    }

    private boolean isSlotBooked(String doctorId, LocalDate date, LocalTime slot) {
        return bookedSlots.getOrDefault(doctorId, Collections.emptyMap())
                .getOrDefault(date, Collections.emptySet())
                .contains(slot);
    }

    private void markSlotBooked(String doctorId, LocalDate date, LocalTime slot) {
        bookedSlots.computeIfAbsent(doctorId, k -> new HashMap<>())
                   .computeIfAbsent(date, k -> new HashSet<>())
                   .add(slot);
    }

    private void releaseSlot(String doctorId, LocalDate date, LocalTime slot) {
        Optional.ofNullable(bookedSlots.get(doctorId))
                .map(m -> m.get(date))
                .ifPresent(s -> s.remove(slot));
    }

    private Appointment findById(String id) {
        return Optional.ofNullable(appointments.get(id))
                .orElseThrow(() -> new AppointmentNotFoundException(id));
    }
}

// report/ReportGenerator.java — using Streams API
package com.hospital.report;

import com.hospital.model.*;
import java.time.LocalDate;
import java.util.*;
import java.util.stream.*;

public class ReportGenerator {
    private final Collection<Appointment> appointments;

    public ReportGenerator(Collection<Appointment> appointments) {
        this.appointments = appointments;
    }

    public void dailySummary(LocalDate date) {
        System.out.println("\n═══════════════ Daily Report: " + date + " ═══════════════");

        var scheduled = appointments.stream()
                .filter(a -> a.getDate().equals(date))
                .collect(Collectors.toList());

        System.out.printf("Total appointments: %d%n", scheduled.size());

        // Group by doctor using Collectors.groupingBy
        scheduled.stream()
                .collect(Collectors.groupingBy(
                        a -> a.getDoctor().getName(),
                        Collectors.counting()))
                .entrySet().stream()
                .sorted(Map.Entry.<String, Long>comparingByValue().reversed())
                .forEach(e -> System.out.printf("  Dr. %-20s: %2d appointments%n",
                        e.getKey(), e.getValue()));

        // Status breakdown
        System.out.println("\nStatus breakdown:");
        appointments.stream()
                .filter(a -> a.getDate().equals(date))
                .collect(Collectors.groupingBy(Appointment::getStatus, Collectors.counting()))
                .forEach((status, count) ->
                        System.out.printf("  %-12s: %d%n", status, count));
    }

    public void doctorWorkloadReport() {
        System.out.println("\n═══════════════ Doctor Workload ═══════════════");
        appointments.stream()
                .collect(Collectors.groupingBy(
                        a -> a.getDoctor().getName(),
                        Collectors.summingInt(a -> 1)))
                .entrySet().stream()
                .sorted(Map.Entry.<String, Integer>comparingByValue().reversed())
                .forEach(e -> {
                    String bar = "█".repeat(Math.min(e.getValue(), 40));
                    System.out.printf("Dr. %-20s [%3d] %s%n", e.getKey(), e.getValue(), bar);
                });
    }
}
```

---

---

# 🟠 PHASE 2: COLLECTIONS + STREAMS + JAVA 8+ (Days 13–22 → also Days 23–32)

---

## DAY 13: Collections Framework — Internal Architecture

```java
// COLLECTION INTERNAL MECHANICS — what interviewers actually test

// ARRAYLIST: backed by Object[] array
// When full: creates new array of size * 1.5, copies elements
// Access: O(1). Insert at end: O(1) amortised. Insert at index: O(n)

// LINKEDLIST: doubly-linked list of nodes
// Access: O(n) — must traverse from head or tail
// Insert/Delete at ends: O(1). Insert at index: O(n) to find + O(1) to link.
// Use when: frequent insertion/deletion in middle. Rarely preferred vs ArrayList.

// HASHMAP INTERNALS (most tested collection)
// Array of "buckets" (default 16). Each bucket is a LinkedList (Java 7) or
// Red-Black Tree (Java 8+ when bucket size > 8).
// put(key, value):
//   1. hash = key.hashCode() ^ (hash >>> 16)  (spread bits)
//   2. index = hash & (capacity - 1)          (fast modulo for power-of-2 capacity)
//   3. If bucket empty: insert. If not: traverse chain, compare with equals().
//   4. If load factor (0.75) exceeded: RESIZE (double capacity, rehash ALL entries)

import java.util.*;
import java.util.stream.*;

public class CollectionsDeepDive {

    // HashMap load factor and initial capacity tuning
    public static void main(String[] args) {
        // If you know you'll have ~1000 entries:
        // Set initial capacity to avoid resizing: 1000 / 0.75 + 1 ≈ 1335
        Map<String, Integer> wordCount = new HashMap<>(1335, 0.75f);

        String text = "the quick brown fox jumps over the lazy dog the fox";
        for (String word : text.split(" ")) {
            wordCount.merge(word, 1, Integer::sum);  // Java 8 — elegant counting
        }
        System.out.println("Word frequencies: " + wordCount);

        // SORTED MAP — always sorted by key (Red-Black Tree internally)
        TreeMap<String, Integer> sorted = new TreeMap<>(wordCount);
        System.out.println("First word: " + sorted.firstKey());
        System.out.println("Last word:  " + sorted.lastKey());

        // COMPARATOR vs COMPARABLE
        List<String> words = new ArrayList<>(wordCount.keySet());

        // Comparable: Natural order (String implements Comparable → alphabetical)
        Collections.sort(words);
        System.out.println("Natural order: " + words);

        // Comparator: Custom order
        words.sort(Comparator.comparingInt(wordCount::get).reversed()
                             .thenComparing(Comparator.naturalOrder()));
        System.out.println("By frequency (desc): " + words);

        // CONCURRENT COLLECTIONS — for multi-threaded access
        Map<String, Integer> concurrentMap = new java.util.concurrent.ConcurrentHashMap<>();
        // Unlike Collections.synchronizedMap(), segments are locked individually
        // Multiple reads (and writes to different segments) can happen simultaneously
    }
}
```

---

## DAYS 14–18: Java 8+ Features — Streams, Lambdas, Optional, CompletableFuture

```java
import java.util.*;
import java.util.stream.*;
import java.util.function.*;
import java.util.concurrent.CompletableFuture;

public class Java8Features {

    record Employee(String name, String dept, double salary, int yearsExp) {}

    public static void main(String[] args) {
        var employees = List.of(
            new Employee("Alice", "Engineering", 95000, 5),
            new Employee("Bob",   "Engineering", 85000, 3),
            new Employee("Carol", "HR",           60000, 7),
            new Employee("Dave",  "Engineering",  72000, 2),
            new Employee("Eve",   "HR",           55000, 4),
            new Employee("Frank", "Finance",      110000, 8)
        );

        // 1. FILTER + MAP + COLLECT
        List<String> highEarnerNames = employees.stream()
                .filter(e -> e.salary() > 80000)
                .sorted(Comparator.comparingDouble(Employee::salary).reversed())
                .map(e -> e.name() + " (₹" + (int)e.salary() + ")")
                .collect(Collectors.toList());
        System.out.println("High earners: " + highEarnerNames);

        // 2. GROUPINGBY — critical for data aggregation
        Map<String, DoubleSummaryStatistics> statsByDept = employees.stream()
                .collect(Collectors.groupingBy(
                        Employee::dept,
                        Collectors.summarizingDouble(Employee::salary)));
        statsByDept.forEach((dept, stats) ->
                System.out.printf("%-12s avg=₹%.0f min=₹%.0f max=₹%.0f count=%d%n",
                        dept, stats.getAverage(), stats.getMin(), stats.getMax(), stats.getCount()));

        // 3. FLATMAP — flatten nested structures
        List<List<String>> teamRosters = List.of(
                List.of("Alice", "Bob"), List.of("Carol"), List.of("Dave", "Eve", "Frank"));
        List<String> allMembers = teamRosters.stream()
                .flatMap(Collection::stream)
                .distinct()
                .sorted()
                .collect(Collectors.toList());

        // 4. REDUCE — custom aggregation
        double totalPayroll = employees.stream()
                .mapToDouble(Employee::salary)
                .sum();

        // 5. OPTIONAL — null-safe API
        Optional<Employee> topEarner = employees.stream()
                .max(Comparator.comparingDouble(Employee::salary));
        topEarner.ifPresentOrElse(
                e -> System.out.println("Top earner: " + e.name() + " ₹" + (int)e.salary()),
                () -> System.out.println("No employees found")
        );

        // 6. COMPLETABLEFUTURE — async operations
        CompletableFuture<Double> asyncAvgSalary = CompletableFuture
                .supplyAsync(() -> employees.stream()
                        .mapToDouble(Employee::salary).average().orElse(0))
                .thenApply(avg -> Math.round(avg * 100.0) / 100.0);

        asyncAvgSalary.thenAccept(avg -> System.out.println("Avg salary (async): ₹" + avg));

        // Wait for async to complete
        CompletableFuture.allOf(asyncAvgSalary).join();
    }
}
```

---

## DAYS 23–32: PROJECT 3 — Student Grade Analytics Engine

### Real-World Problem
Universities need automated grade analysis: GPA calculation, class ranking, at-risk student detection, department performance reports.

```java
// GradeAnalyticsEngine.java — full Streams-based analytics

import java.util.*;
import java.util.stream.*;
import java.io.*;
import java.nio.file.*;

public class GradeAnalyticsEngine {

    record Student(String id, String name, String dept,
                   Map<String, Double> subjectGrades, int semester) {}

    public static void main(String[] args) throws IOException {
        // Load from CSV
        List<Student> students = loadFromCSV("students.csv");

        // 1. GPA per student (weighted average)
        Map<String, Double> gpaMap = students.stream()
                .collect(Collectors.toMap(
                        Student::id,
                        s -> s.subjectGrades().values().stream()
                               .mapToDouble(Double::doubleValue)
                               .average().orElse(0.0)));

        // 2. Class rank (sorted by GPA descending)
        List<Map.Entry<String, Double>> ranked = new ArrayList<>(gpaMap.entrySet());
        ranked.sort(Map.Entry.<String, Double>comparingByValue().reversed());
        System.out.println("=== TOP 5 STUDENTS ===");
        ranked.stream().limit(5).forEach(e -> {
            String name = students.stream().filter(s -> s.id().equals(e.getKey()))
                    .findFirst().map(Student::name).orElse("?");
            System.out.printf("  %s: %.2f GPA%n", name, e.getValue());
        });

        // 3. At-risk students (GPA < 5.0 / 10)
        List<String> atRisk = gpaMap.entrySet().stream()
                .filter(e -> e.getValue() < 5.0)
                .map(Map.Entry::getKey)
                .collect(Collectors.toList());
        System.out.println("\n=== AT-RISK STUDENTS (" + atRisk.size() + ") ===");
        atRisk.forEach(id -> {
            students.stream().filter(s -> s.id().equals(id)).findFirst()
                    .ifPresent(s -> System.out.printf("  %s — GPA: %.2f%n",
                            s.name(), gpaMap.get(id)));
        });

        // 4. Department performance summary
        System.out.println("\n=== DEPARTMENT PERFORMANCE ===");
        students.stream()
                .collect(Collectors.groupingBy(Student::dept,
                        Collectors.averagingDouble(s -> gpaMap.getOrDefault(s.id(), 0.0))))
                .entrySet().stream()
                .sorted(Map.Entry.<String, Double>comparingByValue().reversed())
                .forEach(e -> System.out.printf("  %-20s avg GPA: %.2f%n",
                        e.getKey(), e.getValue()));

        // 5. Subject pass rate
        System.out.println("\n=== SUBJECT PASS RATES ===");
        students.stream()
                .flatMap(s -> s.subjectGrades().entrySet().stream()
                        .map(e -> Map.entry(e.getKey(), e.getValue() >= 5.0)))
                .collect(Collectors.groupingBy(
                        Map.Entry::getKey,
                        Collectors.partitioningBy(Map.Entry::getValue,
                                Collectors.counting())))
                .forEach((subj, counts) -> {
                    long pass = counts.get(true), fail = counts.get(false);
                    double rate = (double) pass / (pass + fail) * 100;
                    System.out.printf("  %-20s pass: %.1f%%%n", subj, rate);
                });

        // 6. Export report to CSV
        exportReport(students, gpaMap, "grade_report.csv");
    }

    static List<Student> loadFromCSV(String path) throws IOException {
        // In real impl: parse CSV using BufferedReader
        // Returning mock data for demonstration
        return List.of(
            new Student("S001", "Alice Kumar", "CSE",
                Map.of("Maths", 8.5, "OS", 7.0, "DBMS", 9.0, "Java", 8.0), 3),
            new Student("S002", "Bob Raj", "CSE",
                Map.of("Maths", 4.0, "OS", 5.5, "DBMS", 4.5, "Java", 6.0), 3),
            new Student("S003", "Carol Singh", "ECE",
                Map.of("Maths", 7.5, "Signals", 8.0, "Circuits", 6.5), 3)
        );
    }

    static void exportReport(List<Student> students, Map<String, Double> gpaMap,
                             String outputPath) throws IOException {
        var sb = new StringBuilder("ID,Name,Department,Semester,GPA,Grade\n");
        students.stream()
                .sorted(Comparator.comparingDouble(s -> -gpaMap.getOrDefault(s.id(), 0.0)))
                .forEach(s -> {
                    double gpa = gpaMap.getOrDefault(s.id(), 0.0);
                    String grade = gpa >= 9 ? "O" : gpa >= 8 ? "A+" : gpa >= 7 ? "A"
                                 : gpa >= 6 ? "B+" : gpa >= 5 ? "B" : "F";
                    sb.append(String.format("%s,%s,%s,%d,%.2f,%s%n",
                            s.id(), s.name(), s.dept(), s.semester(), gpa, grade));
                });
        Files.writeString(Path.of(outputPath), sb.toString());
        System.out.println("\n✅ Report exported to " + outputPath);
    }
}
```

---

---

# 🟡 PHASE 4: MULTITHREADING + CONCURRENCY (Days 33–42)

---

## DAYS 33–37: Concurrency Core Concepts

```java
import java.util.concurrent.*;
import java.util.concurrent.atomic.*;
import java.util.concurrent.locks.*;

public class ConcurrencyMastery {

    // THREAD LIFECYCLE DEMO
    static void threadLifecycleDemo() throws InterruptedException {
        Thread t = new Thread(() -> {
            System.out.println("Thread state IN run(): " + Thread.currentThread().getState());
            try { Thread.sleep(100); } catch (InterruptedException e) { Thread.currentThread().interrupt(); }
        }, "demo-thread");

        System.out.println("Before start: " + t.getState()); // NEW
        t.start();
        System.out.println("After start: " + t.getState());  // RUNNABLE
        t.join();
        System.out.println("After join: " + t.getState());   // TERMINATED
    }

    // EXECUTOR FRAMEWORK — never use raw Thread in production
    static void executorDemo() throws Exception {
        // ThreadPoolExecutor: corePoolSize=4, maxPoolSize=8, queue capacity=100
        ExecutorService pool = new ThreadPoolExecutor(
                4, 8, 60L, TimeUnit.SECONDS,
                new ArrayBlockingQueue<>(100),
                new ThreadFactory() {
                    int count = 0;
                    public Thread newThread(Runnable r) {
                        return new Thread(r, "worker-" + ++count);
                    }
                },
                new ThreadPoolExecutor.CallerRunsPolicy() // don't drop tasks — caller executes
        );

        // Submit Callable (returns result)
        Future<Integer> future = pool.submit(() -> {
            Thread.sleep(100);
            return 42;
        });
        System.out.println("Result: " + future.get(1, TimeUnit.SECONDS));

        // Batch submit with invokeAll
        List<Callable<String>> tasks = List.of(
                () -> "Task A done",
                () -> "Task B done",
                () -> "Task C done"
        );
        pool.invokeAll(tasks).forEach(f -> {
            try { System.out.println(f.get()); }
            catch (Exception e) { e.printStackTrace(); }
        });

        pool.shutdown();
        pool.awaitTermination(30, TimeUnit.SECONDS);
    }

    // LOCK vs SYNCHRONIZED
    static void lockDemo() throws InterruptedException {
        ReentrantLock lock = new ReentrantLock(true);  // fair=true: FIFO ordering
        long[] counter = {0};

        Runnable task = () -> {
            for (int i = 0; i < 100_000; i++) {
                lock.lock();
                try {
                    counter[0]++;
                } finally {
                    lock.unlock();   // ALWAYS in finally — never forget!
                }
            }
        };

        Thread t1 = new Thread(task), t2 = new Thread(task);
        t1.start(); t2.start();
        t1.join(); t2.join();
        System.out.println("Counter (should be 200000): " + counter[0]);
    }

    // ATOMIC VARIABLES — lock-free for simple operations
    static void atomicDemo() {
        AtomicLong counter = new AtomicLong(0);
        AtomicReference<String> status = new AtomicReference<>("IDLE");

        // Compare-and-Swap (CAS) — hardware-level atomic
        boolean changed = status.compareAndSet("IDLE", "RUNNING");
        System.out.println("State changed: " + changed + " → " + status.get());

        // Atomic increment (no synchronized needed)
        counter.incrementAndGet();
        counter.addAndGet(10);
        System.out.println("Atomic counter: " + counter.get());
    }
}
```

---

## DAYS 38–42: PROJECT 2 — Multi-Threaded Log File Processor

### Real-World Problem
Large-scale systems generate gigabytes of log files. Operations teams need to parse, filter, aggregate, and generate incident reports from them — quickly and reliably.

### What This Demonstrates
- **ExecutorService:** Process multiple log files in parallel
- **BlockingQueue:** Producer-Consumer pattern for log lines
- **CompletableFuture:** Async aggregation
- **Atomic counters:** Thread-safe statistics
- **ConcurrentHashMap:** Thread-safe aggregation map

```java
// LogProcessor.java
package com.logprocessor;

import java.util.concurrent.*;
import java.util.concurrent.atomic.*;
import java.nio.file.*;
import java.time.*;
import java.util.*;
import java.util.regex.*;

public class MultiThreadedLogProcessor {

    // LOG LINE: "2024-01-15 10:23:45 [ERROR] PaymentService - Connection timeout"
    record LogEntry(LocalDateTime timestamp, String level,
                    String service, String message) {}

    static final Pattern LOG_PATTERN = Pattern.compile(
            "(\\d{4}-\\d{2}-\\d{2} \\d{2}:\\d{2}:\\d{2}) \\[(\\w+)] (\\w+) - (.+)");

    // STATISTICS — atomic for thread safety
    private final AtomicLong totalLines    = new AtomicLong();
    private final AtomicLong errorCount    = new AtomicLong();
    private final AtomicLong warnCount     = new AtomicLong();
    private final AtomicLong infoCount     = new AtomicLong();
    private final ConcurrentHashMap<String, AtomicLong> errorsByService = new ConcurrentHashMap<>();
    private final ConcurrentHashMap<String, AtomicLong> errorsByHour    = new ConcurrentHashMap<>();

    // PIPELINE: Reader threads → BlockingQueue → Processor threads → Aggregator
    private final BlockingQueue<String> rawLineQueue    = new LinkedBlockingQueue<>(10_000);
    private final BlockingQueue<LogEntry> parsedEntries = new LinkedBlockingQueue<>(10_000);
    private final String POISON_PILL = "STOP";

    public void processDirectory(Path logDir, int readerThreads, int processorThreads)
            throws InterruptedException, ExecutionException {

        ExecutorService readers    = Executors.newFixedThreadPool(readerThreads);
        ExecutorService processors = Executors.newFixedThreadPool(processorThreads);
        ExecutorService aggregator = Executors.newSingleThreadExecutor();

        long startTime = System.currentTimeMillis();

        // PRODUCER THREADS: Read files, put lines into queue
        List<Path> logFiles = getLogFiles(logDir);
        List<CompletableFuture<Void>> readerFutures = logFiles.stream()
                .map(file -> CompletableFuture.runAsync(() -> readFile(file), readers))
                .collect(java.util.stream.Collectors.toList());

        // Signal parsers when all readers done
        CompletableFuture.allOf(readerFutures.toArray(new CompletableFuture[0]))
                .thenRun(() -> {
                    for (int i = 0; i < processorThreads; i++)
                        rawLineQueue.offer(POISON_PILL);
                });

        // PARSER THREADS: Parse raw lines into LogEntry objects
        List<CompletableFuture<Void>> parserFutures = new ArrayList<>();
        for (int i = 0; i < processorThreads; i++) {
            parserFutures.add(CompletableFuture.runAsync(this::parseLines, processors));
        }

        // AGGREGATOR THREAD: Update statistics
        CompletableFuture<Void> aggregatorFuture = CompletableFuture.allOf(
                parserFutures.toArray(new CompletableFuture[0]))
                .thenRunAsync(this::drainAndAggregate, aggregator);

        aggregatorFuture.get();  // Wait for full pipeline

        long elapsed = System.currentTimeMillis() - startTime;
        printReport(logFiles.size(), elapsed);

        readers.shutdown(); processors.shutdown(); aggregator.shutdown();
    }

    private void readFile(Path file) {
        try {
            Files.lines(file).forEach(line -> {
                try {
                    rawLineQueue.put(line);
                    totalLines.incrementAndGet();
                } catch (InterruptedException e) { Thread.currentThread().interrupt(); }
            });
        } catch (Exception e) {
            System.err.println("Error reading: " + file + " — " + e.getMessage());
        }
    }

    private void parseLines() {
        while (true) {
            try {
                String raw = rawLineQueue.take();
                if (POISON_PILL.equals(raw)) {
                    parsedEntries.put(new LogEntry(null, POISON_PILL, null, null));
                    return;
                }
                parseLogLine(raw).ifPresent(entry -> {
                    try { parsedEntries.put(entry); }
                    catch (InterruptedException e) { Thread.currentThread().interrupt(); }
                });
            } catch (InterruptedException e) { Thread.currentThread().interrupt(); return; }
        }
    }

    private void drainAndAggregate() {
        int poisonsReceived = 0;
        // Count expected poisons from parsers
        // Simplified: drain all entries
        while (true) {
            try {
                LogEntry entry = parsedEntries.poll(500, TimeUnit.MILLISECONDS);
                if (entry == null) break;
                if (POISON_PILL.equals(entry.level())) continue;
                aggregate(entry);
            } catch (InterruptedException e) { Thread.currentThread().interrupt(); break; }
        }
    }

    private void aggregate(LogEntry entry) {
        switch (entry.level()) {
            case "ERROR" -> {
                errorCount.incrementAndGet();
                errorsByService.computeIfAbsent(entry.service(), k -> new AtomicLong()).incrementAndGet();
                String hour = entry.timestamp().getHour() + ":00";
                errorsByHour.computeIfAbsent(hour, k -> new AtomicLong()).incrementAndGet();
            }
            case "WARN"  -> warnCount.incrementAndGet();
            case "INFO"  -> infoCount.incrementAndGet();
        }
    }

    private Optional<LogEntry> parseLogLine(String line) {
        Matcher m = LOG_PATTERN.matcher(line);
        if (!m.matches()) return Optional.empty();
        try {
            return Optional.of(new LogEntry(
                    LocalDateTime.parse(m.group(1).replace(' ', 'T')),
                    m.group(2), m.group(3), m.group(4)));
        } catch (Exception e) { return Optional.empty(); }
    }

    private void printReport(int fileCount, long elapsedMs) {
        System.out.println("\n╔══════════════ LOG ANALYSIS REPORT ══════════════╗");
        System.out.printf("  Files processed:  %,d%n", fileCount);
        System.out.printf("  Total lines:      %,d%n", totalLines.get());
        System.out.printf("  Errors:           %,d%n", errorCount.get());
        System.out.printf("  Warnings:         %,d%n", warnCount.get());
        System.out.printf("  Info:             %,d%n", infoCount.get());
        System.out.printf("  Processing time:  %,d ms%n", elapsedMs);
        System.out.printf("  Throughput:       %,.0f lines/sec%n",
                totalLines.get() / (elapsedMs / 1000.0));

        System.out.println("\n  Top Error Sources:");
        errorsByService.entrySet().stream()
                .sorted(Map.Entry.<String, AtomicLong>comparingByValue(
                        Comparator.comparingLong(AtomicLong::get)).reversed())
                .limit(5)
                .forEach(e -> System.out.printf("    %-20s: %,d errors%n",
                        e.getKey(), e.getValue().get()));

        System.out.println("\n  Errors by Hour:");
        new TreeMap<>(errorsByHour).forEach((hour, count) ->
                System.out.printf("    %s: %s (%,d)%n",
                        hour, "▓".repeat((int)(count.get() / 10)), count.get()));
        System.out.println("╚══════════════════════════════════════════════════╝");
    }

    private List<Path> getLogFiles(Path dir) {
        try (var stream = Files.walk(dir)) {
            return stream.filter(p -> p.toString().endsWith(".log"))
                         .collect(java.util.stream.Collectors.toList());
        } catch (Exception e) { return List.of(); }
    }
}
```

---

---

# 🔴 PHASE 5: SPRING BOOT + JPA + SECURITY (Days 43–52)

## DAYS 43–49: Spring Boot Architecture

```java
// SPRING BOOT FUNDAMENTALS — what every MNC expects

// 1. SPRING IOC + DEPENDENCY INJECTION
@Component         // Generic bean
@Service           // Business logic layer
@Repository        // Data access layer
@Controller/@RestController // Presentation layer
@Configuration     // Configuration class

// 2. THREE LAYER ARCHITECTURE (mandatory pattern at MNCs)
// Controller → Service → Repository

// 3. SPRING DATA JPA — avoid boilerplate SQL
public interface PatientRepository extends JpaRepository<Patient, Long> {
    List<Patient> findByBloodGroup(String bloodGroup);
    Optional<Patient> findByContactNumber(String contact);
    @Query("SELECT p FROM Patient p WHERE p.age BETWEEN :min AND :max")
    List<Patient> findByAgeRange(@Param("min") int min, @Param("max") int max);
    long countByDept(String dept);
}

// 4. GLOBAL EXCEPTION HANDLER
@RestControllerAdvice
public class GlobalExceptionHandler {
    @ExceptionHandler(ResourceNotFoundException.class)
    public ResponseEntity<ErrorResponse> handleNotFound(ResourceNotFoundException ex) {
        return ResponseEntity.status(HttpStatus.NOT_FOUND)
                .body(new ErrorResponse("RESOURCE_NOT_FOUND", ex.getMessage(),
                        LocalDateTime.now()));
    }
    @ExceptionHandler(MethodArgumentNotValidException.class)
    public ResponseEntity<ErrorResponse> handleValidation(MethodArgumentNotValidException ex) {
        String errors = ex.getBindingResult().getFieldErrors().stream()
                .map(e -> e.getField() + ": " + e.getDefaultMessage())
                .collect(Collectors.joining(", "));
        return ResponseEntity.badRequest()
                .body(new ErrorResponse("VALIDATION_FAILED", errors, LocalDateTime.now()));
    }
}
```

---

## DAYS 50–52: PROJECT 4 — Blood Bank Management REST API

### Real-World Problem
Blood banks need digital systems to manage donors, blood inventory (by type and Rh factor), donation camps, and requests from hospitals — with real-time inventory alerts.

```yaml
# application.yml
spring:
  datasource:
    url: jdbc:postgresql://localhost:5432/bloodbank
    username: ${DB_USER:bbuser}
    password: ${DB_PASS:bbpass}
  jpa:
    hibernate:
      ddl-auto: validate
    show-sql: false
  data:
    redis:
      host: ${REDIS_HOST:localhost}
      port: 6379

app:
  jwt:
    secret: ${JWT_SECRET:change-this-in-production}
    expiry-ms: 86400000  # 24 hours
  alerts:
    critical-stock-threshold: 5  # units
```

```java
// BloodInventoryController.java
@RestController
@RequestMapping("/api/v1/inventory")
@RequiredArgsConstructor
@Slf4j
public class BloodInventoryController {

    private final BloodInventoryService inventoryService;

    @GetMapping
    public ResponseEntity<Page<BloodUnitDTO>> getAllInventory(
            @RequestParam(required = false) String bloodType,
            @RequestParam(defaultValue = "0") int page,
            @RequestParam(defaultValue = "20") int size) {
        return ResponseEntity.ok(inventoryService.getInventory(bloodType, page, size));
    }

    @GetMapping("/availability")
    public ResponseEntity<Map<String, Integer>> getAvailability() {
        return ResponseEntity.ok(inventoryService.getAvailabilityByBloodType());
    }

    @PostMapping("/donate")
    @PreAuthorize("hasRole('STAFF')")
    public ResponseEntity<BloodUnitDTO> recordDonation(
            @Valid @RequestBody DonationRequest request) {
        BloodUnitDTO unit = inventoryService.recordDonation(request);
        log.info("New donation recorded: {} units of {} from donor {}",
                request.units(), request.bloodType(), request.donorId());
        return ResponseEntity.status(HttpStatus.CREATED).body(unit);
    }

    @PostMapping("/request")
    @PreAuthorize("hasRole('HOSPITAL')")
    public ResponseEntity<BloodRequestDTO> requestBlood(
            @Valid @RequestBody BloodRequestBody request) {
        return ResponseEntity.ok(inventoryService.processRequest(request));
    }

    @GetMapping("/critical-stock")
    @PreAuthorize("hasRole('ADMIN')")
    public ResponseEntity<List<CriticalStockAlert>> getCriticalAlerts() {
        return ResponseEntity.ok(inventoryService.getCriticalStockAlerts());
    }
}

// BloodInventoryService.java
@Service
@Transactional
@RequiredArgsConstructor
@Slf4j
public class BloodInventoryServiceImpl implements BloodInventoryService {

    private final BloodUnitRepository bloodRepo;
    private final DonorRepository donorRepo;
    private final HospitalRequestRepository requestRepo;
    private final RedisTemplate<String, Object> redisTemplate;
    private final ApplicationEventPublisher eventPublisher;

    @Value("${app.alerts.critical-stock-threshold}")
    private int criticalThreshold;

    @Override
    public Map<String, Integer> getAvailabilityByBloodType() {
        String cacheKey = "blood:availability";
        @SuppressWarnings("unchecked")
        Map<String, Integer> cached = (Map<String, Integer>) redisTemplate.opsForValue().get(cacheKey);
        if (cached != null) return cached;

        Map<String, Integer> availability = bloodRepo.getAvailableUnitsByBloodType()
                .stream()
                .collect(Collectors.toMap(
                        BloodTypeCount::bloodType,
                        BloodTypeCount::count));

        redisTemplate.opsForValue().set(cacheKey, availability, Duration.ofMinutes(5));
        return availability;
    }

    @Override
    public BloodUnitDTO recordDonation(DonationRequest request) {
        Donor donor = donorRepo.findById(request.donorId())
                .orElseThrow(() -> new ResourceNotFoundException("Donor", request.donorId()));

        // Validate donation eligibility (90-day gap)
        donor.getLastDonationDate().ifPresent(last -> {
            if (last.plusDays(90).isAfter(LocalDate.now()))
                throw new DonationNotEligibleException(donor.getName(), last);
        });

        BloodUnit unit = BloodUnit.builder()
                .bloodType(request.bloodType())
                .units(request.units())
                .donor(donor)
                .collectionDate(LocalDate.now())
                .expiryDate(LocalDate.now().plusDays(42)) // blood valid for 42 days
                .status(BloodUnit.Status.AVAILABLE)
                .build();

        BloodUnit saved = bloodRepo.save(unit);
        donor.setLastDonationDate(LocalDate.now());
        donorRepo.save(donor);

        // Invalidate cache
        redisTemplate.delete("blood:availability");

        // Check if this resolves a critical stock situation
        checkAndPublishStockEvent(request.bloodType());

        return BloodUnitMapper.toDTO(saved);
    }

    @Override
    public List<CriticalStockAlert> getCriticalStockAlerts() {
        return bloodRepo.getAvailableUnitsByBloodType().stream()
                .filter(btc -> btc.count() < criticalThreshold)
                .map(btc -> new CriticalStockAlert(btc.bloodType(), btc.count(),
                        criticalThreshold, "CRITICAL"))
                .collect(Collectors.toList());
    }

    private void checkAndPublishStockEvent(String bloodType) {
        int available = bloodRepo.countByBloodTypeAndStatus(bloodType, BloodUnit.Status.AVAILABLE);
        if (available < criticalThreshold) {
            eventPublisher.publishEvent(new CriticalStockEvent(this, bloodType, available));
        }
    }
}
```

---

---

# 🟣 PHASE 6: DEVOPS + MICROSERVICES (Days 53–65)

## DAYS 60–62: PROJECT 5 — Real-Time Package Delivery Tracker

### Real-World Problem
E-commerce customers need real-time package location updates. Delivery agents update location; customers see it live without polling.

### Architecture
```
Mobile App (Agent) → POST /api/location → DeliveryService → Redis PubSub
Web Browser (Customer) → WebSocket /ws/track/{packageId} → Gets live updates
```

```java
// WebSocketConfig.java
@Configuration
@EnableWebSocketMessageBroker
public class WebSocketConfig implements WebSocketMessageBrokerConfigurer {
    @Override
    public void registerStompEndpoints(StompEndpointRegistry registry) {
        registry.addEndpoint("/ws").withSockJS();
    }
    @Override
    public void configureMessageBroker(MessageBrokerRegistry config) {
        config.setApplicationDestinationPrefixes("/app");
        config.enableSimpleBroker("/topic");
    }
}

// LocationUpdateController.java
@RestController
@RequestMapping("/api/v1/delivery")
@RequiredArgsConstructor
public class DeliveryController {
    private final SimpMessagingTemplate messagingTemplate;
    private final PackageService packageService;
    private final RedisTemplate<String, Object> redisTemplate;

    // Delivery agent pushes location update
    @PostMapping("/{packageId}/location")
    @PreAuthorize("hasRole('AGENT')")
    public ResponseEntity<Void> updateLocation(
            @PathVariable String packageId,
            @Valid @RequestBody LocationUpdate update) {

        packageService.updateLocation(packageId, update);

        // Persist to Redis (TTL 24h)
        redisTemplate.opsForValue().set(
                "pkg:location:" + packageId, update, Duration.ofHours(24));

        // Push to all subscribers of this package via WebSocket
        messagingTemplate.convertAndSend(
                "/topic/package/" + packageId,
                new PackageStatusEvent(packageId, update.latitude(),
                        update.longitude(), update.status(), LocalDateTime.now()));

        return ResponseEntity.accepted().build();
    }

    // Customer subscribes to live updates via WebSocket
    // Client JS: const socket = new SockJS('/ws'); stompClient.subscribe('/topic/package/PKG-123', ...)
}
```

---

## DAYS 70–75: PROJECT 6 — Coupon & Discount Microservice Engine

### Real-World Problem
E-commerce platforms need a flexible discount engine: percentage off, fixed discount, buy-X-get-Y, seasonal, user-specific — all evaluated in real-time at checkout.

### Architecture
```
Order Service → gRPC → Coupon Service → Validates coupon
                     → Applies best discount from eligible coupons
                     → Publishes CouponUsed event to Kafka
                     → Analytics Consumer updates stats
```

```java
// CouponEngine.java — Strategy Pattern for discount types
public interface DiscountStrategy {
    BigDecimal calculate(BigDecimal orderAmount, Coupon coupon);
    boolean isEligible(Order order, Coupon coupon);
    String describe();
}

@Component("PERCENTAGE")
public class PercentageDiscountStrategy implements DiscountStrategy {
    @Override
    public BigDecimal calculate(BigDecimal amount, Coupon coupon) {
        BigDecimal discount = amount.multiply(coupon.getValue())
                .divide(BigDecimal.valueOf(100), 2, RoundingMode.HALF_UP);
        // Cap at maxDiscount if set
        if (coupon.getMaxDiscount() != null)
            discount = discount.min(coupon.getMaxDiscount());
        return discount;
    }
    @Override
    public boolean isEligible(Order order, Coupon coupon) {
        return order.getTotal().compareTo(coupon.getMinOrderAmount()) >= 0
                && !coupon.isExpired()
                && coupon.getRemainingUses() > 0;
    }
    @Override public String describe() { return "Percentage discount off total"; }
}

// CouponService.java
@Service
@RequiredArgsConstructor
public class CouponService {
    private final CouponRepository couponRepo;
    private final Map<String, DiscountStrategy> strategies;  // Spring injects by bean name
    private final KafkaTemplate<String, CouponEvent> kafkaTemplate;
    private final RedisTemplate<String, Object> redisTemplate;

    public AppliedDiscountResult applyBestCoupon(Order order, List<String> couponCodes) {
        List<Coupon> eligible = couponCodes.stream()
                .map(code -> couponRepo.findByCode(code).orElse(null))
                .filter(Objects::nonNull)
                .filter(c -> getStrategy(c).isEligible(order, c))
                .collect(Collectors.toList());

        if (eligible.isEmpty())
            return AppliedDiscountResult.noDiscount(order.getTotal());

        // Apply coupon that gives maximum discount
        return eligible.stream()
                .map(coupon -> {
                    BigDecimal discount = getStrategy(coupon).calculate(order.getTotal(), coupon);
                    return new AppliedDiscountResult(coupon, discount, order.getTotal().subtract(discount));
                })
                .max(Comparator.comparing(AppliedDiscountResult::discountAmount))
                .map(result -> {
                    // Mark coupon as used
                    result.coupon().decrementUses();
                    couponRepo.save(result.coupon());

                    // Publish event
                    kafkaTemplate.send("coupon-events",
                            new CouponEvent(result.coupon().getCode(), order.getId(),
                                    result.discountAmount(), LocalDateTime.now()));

                    return result;
                })
                .orElseThrow();
    }

    private DiscountStrategy getStrategy(Coupon coupon) {
        return strategies.getOrDefault(coupon.getType().name(),
                strategies.get("PERCENTAGE")); // default
    }
}
```

---

---

# 🟢 PHASE 7: DSA IN JAVA + INTERVIEW PREP (Days 66–75)

## Essential DSA Patterns in Java

```java
// PATTERN 1: TWO POINTERS
public int[] twoSum(int[] nums, int target) {
    Map<Integer, Integer> seen = new HashMap<>();
    for (int i = 0; i < nums.length; i++) {
        int complement = target - nums[i];
        if (seen.containsKey(complement))
            return new int[]{seen.get(complement), i};
        seen.put(nums[i], i);
    }
    return new int[]{};
}

// PATTERN 2: SLIDING WINDOW
public int maxSumSubarray(int[] arr, int k) {
    int windowSum = 0, maxSum = 0;
    for (int i = 0; i < k; i++) windowSum += arr[i];
    maxSum = windowSum;
    for (int i = k; i < arr.length; i++) {
        windowSum += arr[i] - arr[i - k];
        maxSum = Math.max(maxSum, windowSum);
    }
    return maxSum;
}

// PATTERN 3: BFS on Graph
public int shortestPath(int[][] grid, int[] start, int[] end) {
    int rows = grid.length, cols = grid[0].length;
    boolean[][] visited = new boolean[rows][cols];
    Queue<int[]> queue = new LinkedList<>();
    queue.offer(new int[]{start[0], start[1], 0});
    visited[start[0]][start[1]] = true;
    int[][] dirs = {{0,1},{0,-1},{1,0},{-1,0}};
    while (!queue.isEmpty()) {
        int[] curr = queue.poll();
        if (curr[0] == end[0] && curr[1] == end[1]) return curr[2];
        for (int[] d : dirs) {
            int nr = curr[0]+d[0], nc = curr[1]+d[1];
            if (nr >= 0 && nr < rows && nc >= 0 && nc < cols
                    && !visited[nr][nc] && grid[nr][nc] == 0) {
                visited[nr][nc] = true;
                queue.offer(new int[]{nr, nc, curr[2]+1});
            }
        }
    }
    return -1;
}

// PATTERN 4: LRU CACHE (classic MNC question)
class LRUCache {
    private final int capacity;
    private final Map<Integer, Integer> cache;

    public LRUCache(int capacity) {
        this.capacity = capacity;
        // LinkedHashMap with access-order=true is an LRU cache
        this.cache = new LinkedHashMap<>(capacity, 0.75f, true) {
            @Override
            protected boolean removeEldestEntry(Map.Entry<Integer, Integer> eldest) {
                return size() > capacity;
            }
        };
    }
    public int get(int key)              { return cache.getOrDefault(key, -1); }
    public void put(int key, int value)  { cache.put(key, value); }
}

// PATTERN 5: DYNAMIC PROGRAMMING — Coin Change
public int coinChange(int[] coins, int amount) {
    int[] dp = new int[amount + 1];
    Arrays.fill(dp, amount + 1);  // "infinity"
    dp[0] = 0;
    for (int i = 1; i <= amount; i++)
        for (int coin : coins)
            if (coin <= i)
                dp[i] = Math.min(dp[i], dp[i - coin] + 1);
    return dp[amount] > amount ? -1 : dp[amount];
}
```

---

## 📋 DAILY TIMETABLE

| Day | Phase | Topic | Assignment | Output |
|-----|-------|-------|------------|--------|
| **1** | Core Java | JVM Architecture | JVM memory demo | `day-01-jvm.md` |
| **2** | Core Java | String Pool, immutability | StringBuilder benchmark | `day-02-strings.md` |
| **3** | OOP | Classes, constructors, `this` | BankAccount class | `day-03-oop.md` |
| **4** | OOP | Inheritance, polymorphism | Shape hierarchy + area calculator | `day-04-polymorphism.md` |
| **5** | OOP | Interfaces, SOLID, Design Patterns | NotificationService + DIP | `day-05-solid.md` |
| **6** | Core Java | Exception handling | Custom exception hierarchy | `day-06-exceptions.md` |
| **7** | Core Java | GC + Memory model | GC demo + tuning flags | `day-07-memory.md` |
| **8–9** | Core Java | Java I/O + NIO | File walker + CSV reader | `day-08-io.md` |
| **10–12** | **PROJECT 1** | Hospital Booking System | Full OOP system | GitHub + blog post |
| **13** | Collections | ArrayList vs LinkedList internals | Benchmark ArrayList vs LL | `day-13-list.md` |
| **14** | Collections | HashMap internals, collisions | HashMap probe | `day-14-hashmap.md` |
| **15** | Collections | TreeMap, Comparator vs Comparable | Sort employees 3 ways | `day-15-sortable.md` |
| **16–18** | Java 8+ | Streams API | Employee analytics queries | `day-16-streams.md` |
| **19** | Java 8+ | CompletableFuture | Async product price fetcher | `day-19-async.md` |
| **20** | Java 8+ | Records, Pattern matching (Java 14+) | Refactor classes to records | `day-20-modern.md` |
| **21–22** | Review | Collections + Streams combined | Solve 5 collection problems | Blog post: Streams Deep Dive |
| **23–32** | **PROJECT 3** | Grade Analytics Engine | Streams-based reporting | GitHub + Postman |
| **33** | Threading | Thread lifecycle, states | Thread state observer | `day-33-threads.md` |
| **34** | Threading | Synchronisation, `volatile` | Race condition fix | `day-34-sync.md` |
| **35** | Threading | ExecutorService, thread pools | Worker pool simulation | `day-35-executor.md` |
| **36** | Threading | `Locks`, `AtomicLong`, CAS | Lock vs AtomicLong benchmark | `day-36-atomic.md` |
| **37** | Threading | Deadlock, detection, prevention | Deadlock demo + fix | `day-37-deadlock.md` |
| **38–42** | **PROJECT 2** | Log File Processor | Multi-threaded pipeline | GitHub + demo video |
| **43** | Spring Boot | IoC, DI, Bean lifecycle | DI demo without Spring | `day-43-ioc.md` |
| **44** | Spring Boot | REST API fundamentals | CRUD API with H2 | `day-44-rest.md` |
| **45** | Spring Boot | Spring Data JPA | Repository + JPQL queries | `day-45-jpa.md` |
| **46** | Spring Boot | Spring Security + JWT | Secure endpoints | `day-46-security.md` |
| **47** | Spring Boot | Validation + GlobalExceptionHandler | @Valid + @ControllerAdvice | `day-47-validation.md` |
| **48** | Spring Boot | Redis integration + caching | @Cacheable + cache TTL | `day-48-cache.md` |
| **49** | Spring Boot | Spring Events + Kafka | Event publish/subscribe | `day-49-events.md` |
| **50–52** | **PROJECT 4** | Blood Bank API | Full Spring Boot app + tests | GitHub + Swagger UI |
| **53** | Testing | JUnit 5 annotations | Test all service methods | `day-53-junit.md` |
| **54** | Testing | Mockito — mock, verify, captor | Mock dependencies | `day-54-mockito.md` |
| **55** | Testing | Integration tests with TestContainers | Real DB in tests | `day-55-integration.md` |
| **56** | DevOps | Docker + multi-stage Dockerfile | Containerise Spring app | `day-56-docker.md` |
| **57** | DevOps | GitHub Actions CI pipeline | Auto test + build | Pipeline screenshot |
| **58** | Microservices | Service decomposition + REST comm | Inter-service call demo | `day-58-microservices.md` |
| **59** | Microservices | Circuit Breaker (Resilience4j) | Fallback on service down | `day-59-resilience.md` |
| **60–62** | **PROJECT 5** | Delivery Tracker (WebSocket) | Live location tracking | GitHub + demo video |
| **63** | Observability | Spring Actuator + Prometheus metrics | Custom metric | Grafana screenshot |
| **64** | LLD | Design Patterns: Strategy, Factory, Builder | Refactor discount system | `day-64-lld.md` |
| **65** | LLD | Design Parking Lot (LLD interview) | Class diagram + impl | `designs/parking-lot.md` |
| **66** | DSA in Java | Arrays + Hashing (Two Sum, Group Anagrams) | 5 problems solved | `dsa/week1-arrays.md` |
| **67** | DSA in Java | Two Pointers + Sliding Window | 5 problems solved | `dsa/week1-pointers.md` |
| **68** | DSA in Java | Binary Search patterns | 4 problems solved | `dsa/week1-bsearch.md` |
| **69** | DSA in Java | Trees: Traversals, LCA | 5 problems solved | `dsa/week2-trees.md` |
| **70–75** | **PROJECT 6** | Coupon Microservice Engine | Kafka + Strategy pattern | GitHub + blog post |

---

## 🎯 TOP 30 JAVA INTERVIEW QUESTIONS (With Answers)

### Core Java
1. **What is the difference between `==` and `.equals()`?**  
   `==` compares references (memory addresses). `.equals()` compares content (overridden in String, Integer, etc.).

2. **Why is String immutable in Java?**  
   Security (class loading, passwords), String Pool reuse, thread-safety, hashCode caching.

3. **What happens when HashMap capacity exceeds load factor?**  
   Doubles capacity, rehashes all entries (O(n) operation). Amortised cost per put: O(1).

4. **Explain `volatile` keyword.**  
   Ensures visibility across threads — every read from volatile goes to main memory, not CPU cache.

5. **What is the difference between `Callable` and `Runnable`?**  
   `Runnable.run()` returns void, cannot throw checked exceptions. `Callable.call()` returns a value via `Future`, can throw checked exceptions.

### Spring Boot
6. **Difference between `@Component`, `@Service`, `@Repository`?**  
   All register Spring beans. `@Repository` adds exception translation. `@Service` signals business logic. Semantically distinct.

7. **What is `@Transactional` and what are its propagation types?**  
   Wraps method in a transaction. REQUIRED (default), REQUIRES_NEW, NESTED, SUPPORTS, etc.

8. **How does Spring Security JWT filter work?**  
   `OncePerRequestFilter` intercepts every request, extracts token, validates signature, sets `SecurityContext`.

9. **What is the N+1 problem in Hibernate and how to fix it?**  
   Fetching 10 orders and their customers separately = 1 + 10 = 11 queries. Fix: `JOIN FETCH` or `@EntityGraph`.

10. **Explain Spring Boot auto-configuration.**  
    `@SpringBootApplication` triggers `@EnableAutoConfiguration` → reads `META-INF/spring.factories` → configures beans based on classpath.

---

## ✅ MNC READINESS CHECKLIST

| Skill | Evidence Required | Grade |
|---|---|---|
| Core Java + JVM | Explain GC, String Pool, memory areas from memory | ✅ |
| OOP + SOLID | Design a class hierarchy for a real system | ✅ |
| Collections | Explain HashMap internals, choose right collection | ✅ |
| Java 8+ Streams | Write complex aggregation with groupingBy | ✅ |
| Concurrency | Implement thread-safe counter, fix deadlock | ✅ |
| Spring Boot + JPA | Build full CRUD API with auth and tests | ✅ |
| Testing | JUnit 5 + Mockito + TestContainers | ✅ |
| Docker + CI/CD | Dockerfile + GitHub Actions pipeline | ✅ |
| DSA in Java | Solve Medium LeetCode in 20 min | ✅ |
| 6 Projects | All on GitHub with README + API docs | ✅ |

---

*Java Mastery Roadmap — MNC Production-Grade*  
*Reference: Java Programming MNC Interview Guide*