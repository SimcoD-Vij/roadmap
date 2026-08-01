# ⚙️ C Programming Complete Mastery Roadmap
### From Absolute Zero → Systems Programmer at MNC Level
#### *Day-by-Day · Topic-by-Topic · Project-by-Project*
##### *Think in C: No garbage collector, no safety net — pure engineering discipline*

---

> **Reference:** Built from C Programming MNC Interview Guide — *"C isn't just another language — it's the root of modern programming"*
> **Target:** Tier 1 MNC readiness for Systems, Embedded, DevOps, Backend, and Kernel roles
> **Projects:** 6 brand-new real-world projects — none overlap with Java/Python/OS roadmaps
> **Key Principle:** Every line of C you write must be mentally traceable to what the CPU does

---

## 📐 MASTER ARCHITECTURE

```
╔═══════════════════════════════════════════════════════════════════════╗
║                  C MASTERY — 75-DAY MAP                              ║
╠═══════════════════════════════════════════════════════════════════════╣
║  PHASE 1 (Days 1–10):  FOUNDATIONS + COMPILATION MODEL              ║
║  PHASE 2 (Days 11–20): POINTERS + MEMORY MANAGEMENT                 ║
║  PHASE 3 (Days 21–30): DATA STRUCTURES IN C                         ║
║  PHASE 4 (Days 31–42): SYSTEMS PROGRAMMING + FILE I/O               ║
║  PHASE 5 (Days 43–55): ADVANCED C + CONCURRENCY                     ║
║  PHASE 6 (Days 56–65): DEBUGGING + TOOLCHAIN MASTERY                ║
║  PHASE 7 (Days 66–75): DSA IN C + INTERVIEW PREP                    ║
╚═══════════════════════════════════════════════════════════════════════╝

PROJECTS (NEW — upgraded, real-world, none in other roadmaps):
  P1 — In-Memory Key-Value Cache Engine     (Days 18–22) — Hash + Pointers
  P2 — Student Records Database (File-Based)(Days 30–34) — Structs + File I/O
  P3 — Custom Shell with Pipe Support       (Days 38–42) — Process + POSIX
  P4 — Multi-Client TCP Chat Server         (Days 48–52) — Sockets + select()
  P5 — Memory Leak Detector (Malloc Tracer) (Days 57–62) — Debug + Hooks
  P6 — Real-Time System Resource Monitor    (Days 68–75) — /proc + ncurses
```

---

## 🛠️ TECH STACK

| Tool | Version | Why |
|---|---|---|
| Compiler | GCC 13 + Clang 17 | Both used in industry; Clang gives better error messages |
| Build System | GNU Make + CMake 3.28 | Make for learning, CMake for multi-file production projects |
| Debugger | GDB 14 + LLDB | GDB for Linux, LLDB for macOS; both used in MNC development |
| Memory Check | Valgrind + AddressSanitizer | Valgrind for runtime leak detection; ASan for compile-time checking |
| Static Analysis | clang-tidy + cppcheck | Catch bugs before running code |
| Format | clang-format | Industry standard C code formatting |
| Profiler | gprof + perf | Performance measurement and hot-path identification |
| Networking | POSIX Sockets (BSD API) | Foundation of all C networking — used in embedded + servers |
| Terminal UI | ncurses | Standard for terminal dashboard applications |
| OS Interface | POSIX (unistd.h, sys/) | Everything Linux/Unix system programming |
| Version Control | Git + GitHub | Non-negotiable |

```bash
# Install everything on Ubuntu 24.04
sudo apt install -y \
  gcc clang gdb lldb cmake make \
  valgrind libasan6 \
  clang-tidy cppcheck clang-format \
  libncurses-dev \
  strace ltrace perf-tools-unstable \
  linux-tools-generic
```

---

## 📝 DOCUMENTATION STRATEGY

```
GitHub Structure:
c-mastery/
├── README.md                 ← Portfolio landing page
├── phase-1-foundations/      ← Days 1–10 code + notes
├── phase-2-pointers/         ← Days 11–20 code + notes
├── phase-3-data-structures/  ← Days 21–30 code + notes
├── phase-4-systems/          ← Days 31–42 code + notes
├── phase-5-advanced/         ← Days 43–55 code + notes
├── phase-6-debugging/        ← Days 56–65 code + notes
├── phase-7-dsa/              ← Days 66–75 DSA solutions
├── projects/
│   ├── 01-kv-cache-engine/
│   ├── 02-student-records-db/
│   ├── 03-custom-shell/
│   ├── 04-tcp-chat-server/
│   ├── 05-malloc-tracer/
│   └── 06-system-monitor/
└── interview-prep/
    ├── pointers-qa.md
    ├── memory-qa.md
    ├── systems-qa.md
    └── tricky-programs.md
```

**Each day template: `phase-X/day-XX-topic.md`**
```markdown
# Day XX — [Topic]
## Core Concept (In My Own Words)
## Code I Wrote Today
## Memory Diagram (ASCII art of what happens in RAM)
## Compiler Output Observed
## Valgrind / GDB Finding
## Active Recall Questions
```

---

---

# 🔵 PHASE 1: FOUNDATIONS + COMPILATION MODEL (Days 1–10)

> **The interviewer's view:** *"If you mess this up, I know you memorized tutorials instead of understanding the compiler's flow."*
>
> **Goal:** Understand not just what C code does, but what the preprocessor, compiler, assembler, and linker each do — and why.

---

## DAY 1: How C Becomes a Running Program

### The Four-Stage Compilation Pipeline

```
YOUR .c FILE
     │
     ▼  gcc -E  (Preprocessing)
PREPROCESSED (.i)    ← #include expanded, macros substituted, comments removed
     │
     ▼  gcc -S  (Compilation)
ASSEMBLY (.s)        ← Human-readable CPU instructions (mov, push, call, ret)
     │
     ▼  gcc -c  (Assembly)
OBJECT FILE (.o)     ← Machine code, but NOT yet a complete program
     │
     ▼  gcc (Linking)
EXECUTABLE (a.out)   ← All .o files + library functions combined → runnable
```

```bash
# Observe each stage manually
cat > hello.c << 'EOF'
#include <stdio.h>
#define GREETING "Hello, C World!"

int main(void) {
    printf("%s\n", GREETING);
    return 0;
}
EOF

# Stage 1: Preprocessing — see what #include actually becomes
gcc -E hello.c -o hello.i
wc -l hello.i          # You'll see hundreds of lines from stdio.h expansion
tail -10 hello.i        # Only the last 10 lines are YOUR code

# Stage 2: Compilation — see the assembly your code generates
gcc -S hello.c -o hello.s
cat hello.s             # Read the assembly instructions

# Stage 3: Assemble — create object file
gcc -c hello.c -o hello.o
file hello.o            # ELF 64-bit relocatable

# Stage 4: Link — create executable
gcc hello.o -o hello
./hello

# All at once, with warnings:
gcc -Wall -Wextra -pedantic -std=c17 hello.c -o hello
```

### The Memory Layout of a Running Program

```
HIGH ADDRESS (Stack grows DOWN ↓)
┌─────────────────────────────────────────────────┐
│         STACK                                    │
│  Local variables, function call frames           │
│  Function arguments, return addresses            │
│  Grows downward from high to low address         │
│  Automatically freed when function returns       │
├─────────────────────────────────────────────────┤
│         (unmapped — guard for stack overflow)    │
├─────────────────────────────────────────────────┤
│         HEAP                                     │
│  malloc(), calloc(), realloc() live here         │
│  Grows upward from low to high address           │
│  YOU must free() it — no garbage collector       │
├─────────────────────────────────────────────────┤
│         BSS SEGMENT                              │
│  Uninitialized global variables                  │
│  int g;  (outside main) → BSS, initialized to 0 │
├─────────────────────────────────────────────────┤
│         DATA SEGMENT                             │
│  Initialized global and static variables         │
│  int g = 5;  →  DATA segment                    │
├─────────────────────────────────────────────────┤
│         TEXT SEGMENT (CODE)                      │
│  Your compiled machine code instructions         │
│  Read-only — writing here causes SIGSEGV         │
│  char *s = "hello" → string literal lives HERE  │
LOW ADDRESS
```

### Practical Exercise: Map Your Variables

```c
/* day01_memory_layout.c — verify where each variable lives */
#include <stdio.h>
#include <stdlib.h>

int global_uninit;              /* BSS */
int global_init = 42;           /* DATA */
static int static_var = 100;    /* DATA */

void show_addresses(void) {
    int local_var = 1;          /* STACK */
    static int func_static = 2; /* DATA */
    int *heap_var = malloc(sizeof(int)); /* HEAP */
    *heap_var = 99;

    printf("Text  (code):    %p  [main function]\n", (void*)main);
    printf("Data  (init):    %p  [global_init]\n", (void*)&global_init);
    printf("Data  (static):  %p  [static_var]\n", (void*)&static_var);
    printf("BSS   (uninit):  %p  [global_uninit]\n", (void*)&global_uninit);
    printf("Heap  (malloc):  %p  [heap_var]\n", (void*)heap_var);
    printf("Stack (local):   %p  [local_var]\n", (void*)&local_var);

    /* Observe: stack address > heap address (they grow toward each other) */

    free(heap_var);
}

int main(void) {
    show_addresses();
    return 0;
}
/* Compile: gcc -o memory_layout day01_memory_layout.c
   Run and observe the addresses — TEXT lowest, STACK highest */
```

### ✅ Active Recall
1. What is the difference between the BSS and Data segment? Give a code example.
2. If `char *s = "hello"`, where does `"hello"` actually live in memory?
3. Why does writing to a string literal cause a segfault?

---

## DAY 2: Data Types, Operators, and the Trap of Undefined Behaviour

```c
/* day02_types_and_ub.c */
#include <stdio.h>
#include <limits.h>    /* INT_MAX, INT_MIN, CHAR_MAX etc */
#include <stdint.h>    /* int32_t, uint64_t — exact-width types */

int main(void) {

    /* SIZES — know these, interviewers test them */
    printf("=== Type Sizes on This Platform ===\n");
    printf("char:       %zu bytes\n", sizeof(char));      /* always 1 */
    printf("short:      %zu bytes\n", sizeof(short));     /* usually 2 */
    printf("int:        %zu bytes\n", sizeof(int));       /* usually 4 */
    printf("long:       %zu bytes\n", sizeof(long));      /* 4 or 8 */
    printf("long long:  %zu bytes\n", sizeof(long long)); /* always 8 */
    printf("float:      %zu bytes\n", sizeof(float));     /* always 4 */
    printf("double:     %zu bytes\n", sizeof(double));    /* always 8 */
    printf("pointer:    %zu bytes\n", sizeof(void*));     /* 4 (32-bit) or 8 (64-bit) */

    /* LIMITS */
    printf("\nINT_MAX = %d\n", INT_MAX);   /* 2,147,483,647 */
    printf("INT_MIN = %d\n", INT_MIN);     /* -2,147,483,648 */

    /* EXACT-WIDTH TYPES — use these in embedded/systems code */
    int32_t  i32 = INT32_MAX;
    uint64_t u64 = UINT64_MAX;
    printf("\nint32_t max:  %d\n", i32);
    printf("uint64_t max: %llu\n", (unsigned long long)u64);

    /* UNDEFINED BEHAVIOUR EXAMPLES — the C programmer's landmines */

    /* UB 1: Integer overflow (signed) — behaviour is UNDEFINED */
    int x = INT_MAX;
    /* x + 1 is UB — compiler may assume it never happens and optimize away checks */
    printf("\nINT_MAX + 1 (UB!): %d\n", x + 1);    /* "works" but is undefined */

    /* UB 2: Reading uninitialized variable */
    int uninit;
    /* printf("%d\n", uninit); */  /* UB — could be anything */

    /* UB 3: Signed integer shift */
    int s = -1;
    /* int bad = s >> 31; */  /* UB for negative values */

    /* SAFE: Unsigned overflow is DEFINED (wraps around) */
    unsigned int u = UINT_MAX;
    printf("UINT_MAX + 1 (wraps): %u\n", u + 1);  /* Always 0 — guaranteed */

    /* BITWISE OPERATORS — critical for embedded/systems */
    unsigned char flags = 0x00;
    flags |= (1 << 3);   /* Set bit 3: flags = 0b00001000 */
    flags |= (1 << 6);   /* Set bit 6: flags = 0b01001000 */
    printf("\nflags after setting bits 3 and 6: 0x%02X\n", flags);

    flags &= ~(1 << 3);  /* Clear bit 3 */
    printf("flags after clearing bit 3:       0x%02X\n", flags);

    int bit3_set = (flags >> 3) & 1;  /* Test bit 3 */
    printf("Is bit 3 set? %s\n", bit3_set ? "YES" : "NO");

    return 0;
}
```

---

## DAY 3: Functions — Stack Frames and Execution

```c
/* day03_functions_stack.c — visualise the stack */
#include <stdio.h>

/* Forward declaration */
long long factorial(int n);
void swap_by_value(int a, int b);
void swap_by_pointer(int *a, int *b);

/* RECURSIVE FACTORIAL — understand stack frame depth */
long long factorial(int n) {
    printf("  factorial(%d) — stack frame at %p\n", n, (void*)&n);
    if (n <= 1) return 1;
    return n * factorial(n - 1);
    /* Each call pushes: return address, parameter n, return value slot */
    /* Stack grows DOWN on x86-64 — each frame is lower address than caller */
}

/* PASS BY VALUE — copy is made, original unchanged */
void swap_by_value(int a, int b) {
    int tmp = a; a = b; b = tmp;
    printf("Inside swap_by_value: a=%d, b=%d (local copies changed)\n", a, b);
}

/* PASS BY POINTER (reference semantics) — can modify caller's variables */
void swap_by_pointer(int *a, int *b) {
    int tmp = *a;  /* dereference: read value AT address a points to */
    *a = *b;
    *b = tmp;
    printf("Inside swap_by_pointer: *a=%d, *b=%d (originals changed)\n", *a, *b);
}

int main(void) {
    printf("=== Stack Frame Demo ===\n");
    printf("factorial(5) = %lld\n\n", factorial(5));

    int x = 10, y = 20;
    printf("Before swap_by_value: x=%d, y=%d\n", x, y);
    swap_by_value(x, y);
    printf("After  swap_by_value: x=%d, y=%d (unchanged!)\n\n", x, y);

    printf("Before swap_by_pointer: x=%d, y=%d\n", x, y);
    swap_by_pointer(&x, &y);  /* & = "address of" */
    printf("After  swap_by_pointer: x=%d, y=%d (changed!)\n", x, y);

    return 0;
}
```

---

## DAY 4: Control Flow — The Traps Interviewers Use

```c
/* day04_control_flow.c */
#include <stdio.h>

int main(void) {

    /* SWITCH FALLTHROUGH — the most common interview trap */
    int val = 2;
    printf("Switch fallthrough demo (val=2):\n");
    switch (val) {
        case 1:
            printf("  case 1\n");
            break;
        case 2:
            printf("  case 2\n");
            /* NO BREAK — falls through to case 3! */
        case 3:
            printf("  case 3 (fallthrough from 2!)\n");
            break;
        default:
            printf("  default\n");
    }

    /* LOOP MODIFICATION TRAPS */
    printf("\nLoop modification — changing the variable mid-loop:\n");
    for (int i = 0; i < 5; i++) {
        printf("  i = %d\n", i);
        if (i == 2) i++;  /* Skip 3 — interviewer trap */
    }
    /* Output: 0, 1, 2, 4 — not 0,1,2,3,4 */

    /* DO-WHILE — executes at least once */
    int count = 10;
    do {
        printf("do-while runs at least once even though count=%d > 0\n", count);
        count++;
    } while (count < 5);  /* Condition is false first check, but body ran! */

    /* GOTO — rare but valid use: cleanup in error paths */
    FILE *f = fopen("/etc/hostname", "r");
    int *buf = malloc(1024);
    if (!f)   { fprintf(stderr, "fopen failed\n"); goto cleanup; }
    if (!buf) { fprintf(stderr, "malloc failed\n"); goto cleanup; }
    /* ... do real work ... */
cleanup:
    if (f)   fclose(f);
    if (buf) free(buf);

    return 0;
}
```

---

## DAY 5: Arrays, Strings, and Memory Layout

```c
/* day05_arrays_strings.c */
#include <stdio.h>
#include <string.h>
#include <stdlib.h>

int main(void) {

    /* ============================================
       ARRAY — MEMORY LAYOUT
       int arr[5] occupies 5 × 4 = 20 consecutive bytes
       arr[0] at lowest address, arr[4] at highest
    ============================================ */
    int arr[5] = {10, 20, 30, 40, 50};
    printf("=== Array Memory ===\n");
    for (int i = 0; i < 5; i++) {
        printf("arr[%d] = %d  at address %p\n", i, arr[i], (void*)&arr[i]);
    }
    /* You'll see addresses differ by exactly 4 (sizeof int) */

    /* ARRAY NAME IS A POINTER TO FIRST ELEMENT */
    printf("\narr    = %p\n", (void*)arr);
    printf("&arr[0]= %p\n", (void*)&arr[0]);  /* Same! */
    printf("*arr   = %d\n", *arr);             /* Dereference = arr[0] = 10 */
    printf("*(arr+2)= %d\n", *(arr + 2));       /* arr[2] = 30 */

    /* 2D ARRAY — ROW-MAJOR storage */
    int matrix[3][4] = {{1,2,3,4},{5,6,7,8},{9,10,11,12}};
    /* In memory: 1,2,3,4,5,6,7,8,9,10,11,12 — all in a row */
    printf("\nMatrix[1][2] = %d (row 1, col 2)\n", matrix[1][2]);
    /* Address of matrix[r][c] = base + (r * 4 + c) * sizeof(int) */

    /* ============================================
       STRINGS IN C — two completely different things
    ============================================ */

    /* Type 1: char array — string is on STACK, MODIFIABLE */
    char arr_str[] = "hello";        /* compiler allocates 6 bytes on stack */
    arr_str[0] = 'H';                /* OK — modifiable */
    printf("\nModified arr_str: %s\n", arr_str);

    /* Type 2: char pointer — string literal is in TEXT segment, READ-ONLY */
    char *ptr_str = "hello";         /* pointer to read-only memory */
    /* ptr_str[0] = 'H'; */          /* SEGFAULT — do not do this! */
    printf("ptr_str: %s (cannot modify!)\n", ptr_str);

    /* SAFE STRING OPERATIONS */
    char src[] = "Hello, World!";
    char dst[50];

    /* strncpy — always use n-version, never strcpy (buffer overflow risk) */
    strncpy(dst, src, sizeof(dst) - 1);
    dst[sizeof(dst) - 1] = '\0';     /* ALWAYS null-terminate manually! */

    /* strnlen, strncmp — always use n-versions */
    printf("Length: %zu\n", strnlen(src, sizeof(src)));
    printf("Compare: %d\n", strncmp("abc", "abd", 3));  /* negative — 'c' < 'd' */

    /* BUFFER OVERFLOW — the most famous C vulnerability */
    char small[5];
    /* strcpy(small, "Hello, World!"); */  /* Buffer overflow — DO NOT DO THIS */
    /* Instead: */
    strncpy(small, "Hello, World!", sizeof(small) - 1);
    small[sizeof(small) - 1] = '\0';
    printf("Safe copy into small[5]: '%s'\n", small);  /* "Hell" (truncated) */

    return 0;
}
```

---

## DAY 6: Preprocessor — Power and Pitfalls

```c
/* day06_preprocessor.c */
#include <stdio.h>

/* OBJECT MACRO — simple constant replacement */
#define MAX_SIZE    100
#define PI          3.14159265358979

/* FUNCTION MACRO — dangerous if misused! */
#define SQUARE(x)   ((x) * (x))      /* ALWAYS parenthesise args AND result */
#define WRONG_SQ(x) x * x            /* TRAP: WRONG_SQ(a+b) = a + b*b + a! */
#define MAX(a,b)    ((a) > (b) ? (a) : (b))

/* STRINGIFICATION and TOKEN PASTING */
#define TOSTRING(x) #x               /* converts token to string literal */
#define CONCAT(a,b) a ## b           /* pastes tokens together */

/* VARIADIC MACRO (C99+) */
#define LOG(fmt, ...) fprintf(stderr, "[LOG] " fmt "\n", ##__VA_ARGS__)

/* HEADER GUARD — prevents double inclusion */
#ifndef MY_HEADER_H
#define MY_HEADER_H
/* ... declarations ... */
#endif

/* CONDITIONAL COMPILATION */
#ifdef DEBUG
    #define DPRINT(fmt, ...) printf("[DEBUG] " fmt "\n", ##__VA_ARGS__)
#else
    #define DPRINT(fmt, ...) /* nothing — compiled out in release */
#endif

int main(void) {
    int a = 3;

    /* Macro trap demo */
    printf("SQUARE(3) = %d\n", SQUARE(3));          /* 9 — correct */
    printf("SQUARE(a+1) = %d\n", SQUARE(a+1));      /* (3+1)*(3+1) = 16 — correct */
    printf("WRONG_SQ(a+1) = %d\n", WRONG_SQ(a+1)); /* 3+1*1+3 = 7 — WRONG! */

    /* Double evaluation trap */
    int i = 5;
    printf("MAX(i++, 3) = %d, i = %d\n", MAX(i++, 3), i);
    /* i++ evaluated TWICE inside macro — UB / wrong result */

    /* Stringification */
    printf("TOSTRING(MAX_SIZE) = \"%s\"\n", TOSTRING(MAX_SIZE));  /* "MAX_SIZE" */

    /* Token pasting */
    int xy = 99;
    printf("CONCAT(x,y) = %d\n", CONCAT(x,y));  /* creates variable name `xy` */

    LOG("Starting application version %d", 1);
    DPRINT("This only appears in DEBUG builds");  /* compile with -DDEBUG to see */

    /* COMPILE-TIME ASSERTION (C11) */
    _Static_assert(sizeof(int) == 4, "int must be 4 bytes on this platform");

    return 0;
}
```

---

## DAYS 7–9: Structures, Unions, and Bit Fields

```c
/* day07_structs_unions.c */
#include <stdio.h>
#include <string.h>
#include <stdint.h>

/* ============================================
   STRUCTURE PADDING AND ALIGNMENT
   The compiler adds padding to align fields
   to their natural alignment boundary
============================================ */
struct Padded {
    char   a;      /* 1 byte  + 3 bytes padding */
    int    b;      /* 4 bytes (must be 4-byte aligned) */
    char   c;      /* 1 byte  + 7 bytes padding */
    double d;      /* 8 bytes (must be 8-byte aligned) */
};                 /* Total: 24 bytes (not 14!) */

struct Packed {
    char   a;      /* 1 byte */
    char   c;      /* 1 byte (group same-size together) */
    int    b;      /* 4 bytes */
    double d;      /* 8 bytes */
};                 /* Total: 16 bytes (optimised order) */

/* NESTED STRUCT */
typedef struct {
    char name[64];
    int  age;
} Person;

typedef struct {
    Person  person;      /* nested struct */
    char    dept[32];
    float   salary;
    Person *manager;     /* pointer to another Employee (linked) */
} Employee;

/* UNION — all members share the same memory */
union Data {
    int    i;       /* 4 bytes */
    float  f;       /* 4 bytes */
    char   bytes[4];/* 4 bytes */
};
/* All three are the SAME 4 bytes in memory — writing one reads another */

/* BIT FIELDS — pack flags into minimal space */
struct NetworkFlags {
    uint8_t ack  : 1;   /* 1 bit  — TCP ACK flag */
    uint8_t syn  : 1;   /* 1 bit  — TCP SYN flag */
    uint8_t fin  : 1;   /* 1 bit  — TCP FIN flag */
    uint8_t rst  : 1;   /* 1 bit  — TCP RST flag */
    uint8_t psh  : 1;   /* 1 bit */
    uint8_t urg  : 1;   /* 1 bit */
    uint8_t      : 2;   /* 2 bits padding — unused */
};  /* Total: 1 byte instead of 6 separate uint8_t = 6 bytes */

int main(void) {
    printf("=== Structure Sizes ===\n");
    printf("Padded: %zu bytes\n", sizeof(struct Padded));  /* 24 */
    printf("Packed: %zu bytes\n", sizeof(struct Packed));  /* 16 */
    printf("NetworkFlags: %zu bytes\n", sizeof(struct NetworkFlags)); /* 1 */

    /* Initialize struct */
    Employee emp = {
        .person  = {.name = "Alice Kumar", .age = 28},
        .dept    = "Engineering",
        .salary  = 95000.0f,
        .manager = NULL
    };
    printf("\nEmployee: %s, Dept: %s, Salary: %.0f\n",
           emp.person.name, emp.dept, emp.salary);

    /* UNION: See the same bytes as different types */
    union Data d;
    d.i = 0x41424344;    /* ASCII: 'A'=0x41, 'B'=0x42, 'C'=0x43, 'D'=0x44 */
    printf("\nUnion demo:\n");
    printf("As int:   0x%08X\n", d.i);
    printf("As float: %f\n",     d.f);     /* completely different interpretation */
    printf("As bytes: '%c' '%c' '%c' '%c'\n",  /* endian-dependent */
           d.bytes[0], d.bytes[1], d.bytes[2], d.bytes[3]);

    /* BIT FIELDS */
    struct NetworkFlags tcp = {.ack=1, .syn=1, .fin=0, .rst=0};
    printf("\nTCP flags: ACK=%d SYN=%d FIN=%d RST=%d\n",
           tcp.ack, tcp.syn, tcp.fin, tcp.rst);
    /* This is how TCP/IP headers are actually parsed in kernel code! */

    return 0;
}
```

---

---

# 🟠 PHASE 2: POINTERS + MEMORY MANAGEMENT (Days 11–20)

> **The interviewer says:** *"Pointers are the soul of C. If you can visualise what happens at memory address 0x7ffeefbff..., you're not just coding — you're thinking like the compiler."*

---

## DAY 11: Pointer Fundamentals — Every Type

```c
/* day11_pointers.c */
#include <stdio.h>
#include <stdlib.h>

void demonstrate_pointer_types(void) {

    /* BASIC POINTER */
    int x = 42;
    int *p = &x;       /* p holds address of x */
    printf("x=%d, &x=%p, p=%p, *p=%d\n", x, (void*)&x, (void*)p, *p);
    *p = 100;          /* dereference: change value at address p points to */
    printf("After *p=100: x=%d\n", x);

    /* POINTER ARITHMETIC */
    int arr[5] = {10,20,30,40,50};
    int *ap = arr;
    printf("\nPointer arithmetic:\n");
    printf("ap+0=%d, ap+1=%d, ap+2=%d\n", *ap, *(ap+1), *(ap+2));
    ap++;             /* moves 4 bytes forward (sizeof int) */
    printf("After ap++: *ap = %d (was arr[1])\n", *ap);

    /* POINTER TO POINTER */
    int **pp = &p;    /* pp holds address of p */
    printf("\nDouble pointer: **pp = %d\n", **pp);  /* same as x */

    /* VOID POINTER — generic pointer, must cast before dereferencing */
    void *vp = &x;
    printf("void* to int: %d\n", *(int*)vp);  /* cast required */

    /* CONST WITH POINTERS — three different meanings */
    const int *cp  = &x;       /* pointer to const int: can't change *cp */
    int *const pc  = &x;       /* const pointer to int: can't change pc itself */
    const int *const cpc = &x; /* const pointer to const int: neither changeable */

    /* *cp = 5; */  /* ERROR: can't modify through cp */
    cp = &arr[0];   /* OK: pointer itself can change */

    /* pc = &arr[0]; */  /* ERROR: pointer itself is const */
    *pc = 5;            /* OK: value it points to can change */

    /* FUNCTION POINTER */
    int (*fp)(int, int);  /* pointer to function taking 2 ints, returning int */

    /* The C interviewer question: what is int *p[10] vs int (*p)[10]? */
    int *pa[10];       /* array of 10 pointers to int */
    int (*pb)[10];     /* pointer to array of 10 ints */

    printf("\nint *pa[10]:  sizeof = %zu (10 pointers)\n", sizeof(pa));
    int dummy[10];
    pb = &dummy;
    printf("int (*pb)[10]: sizeof = %zu (one pointer)\n", sizeof(pb));
}

/* DANGLING, WILD, AND NULL POINTERS */
int *create_dangling(void) {
    int local = 5;
    return &local;  /* DANGER: local is gone after return */
    /* This is a dangling pointer — points to freed stack frame */
}

int main(void) {
    demonstrate_pointer_types();

    /* NULL POINTER — safe "nothing" */
    int *null_p = NULL;
    if (null_p == NULL) {
        printf("\nNull pointer check: safe!\n");
    }
    /* *null_p = 5; */  /* SEGFAULT — never dereference NULL */

    /* WILD POINTER — uninitialized, points to random memory */
    int *wild;         /* wild = garbage address — DANGEROUS */
    /* *wild = 5; */   /* SEGFAULT or silent data corruption */
    wild = NULL;       /* ALWAYS initialise pointers! */

    return 0;
}
```

---

## DAY 12: Dynamic Memory — malloc, calloc, realloc, free

```c
/* day12_dynamic_memory.c */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>

/* CORRECT PATTERN: always check malloc return value */
void *safe_malloc(size_t size) {
    void *ptr = malloc(size);
    if (!ptr) {
        fprintf(stderr, "malloc(%zu) failed — out of memory!\n", size);
        exit(EXIT_FAILURE);
    }
    return ptr;
}

/* DYNAMIC ARRAY — grows as needed */
typedef struct {
    int   *data;
    size_t size;
    size_t capacity;
} DynArray;

DynArray *dynarray_create(size_t initial_cap) {
    DynArray *da = safe_malloc(sizeof(DynArray));
    da->data     = safe_malloc(initial_cap * sizeof(int));
    da->size     = 0;
    da->capacity = initial_cap;
    return da;
}

void dynarray_push(DynArray *da, int val) {
    if (da->size == da->capacity) {
        /* GROW: double the capacity (amortised O(1) push) */
        da->capacity *= 2;
        int *new_data = realloc(da->data, da->capacity * sizeof(int));
        if (!new_data) {
            fprintf(stderr, "realloc failed\n");
            free(da->data);
            free(da);
            exit(EXIT_FAILURE);
        }
        da->data = new_data;
        printf("  [realloc] capacity doubled to %zu\n", da->capacity);
    }
    da->data[da->size++] = val;
}

void dynarray_destroy(DynArray *da) {
    free(da->data);   /* free the array first */
    free(da);         /* then free the struct */
    /* NOTE: do NOT access da after this point */
}

int main(void) {
    printf("=== malloc vs calloc ===\n");

    /* malloc: allocates size bytes, UNINITIALISED (contains garbage) */
    int *m_arr = malloc(5 * sizeof(int));
    printf("malloc (uninit): ");
    for (int i = 0; i < 5; i++) printf("%d ", m_arr[i]);  /* garbage values */
    printf("\n");

    /* calloc: allocates AND zero-initialises */
    int *c_arr = calloc(5, sizeof(int));
    printf("calloc (zeroed): ");
    for (int i = 0; i < 5; i++) printf("%d ", c_arr[i]);  /* all zeros */
    printf("\n");

    free(m_arr);
    free(c_arr);

    printf("\n=== Dynamic Array Growth ===\n");
    DynArray *da = dynarray_create(4);
    for (int i = 1; i <= 12; i++) {
        dynarray_push(da, i * 10);
    }
    printf("Final array (size=%zu, cap=%zu): ", da->size, da->capacity);
    for (size_t i = 0; i < da->size; i++) printf("%d ", da->data[i]);
    printf("\n");
    dynarray_destroy(da);

    printf("\n=== Common Memory Mistakes ===\n");

    /* MISTAKE 1: Double free */
    int *bad = malloc(sizeof(int));
    free(bad);
    /* free(bad); */  /* DOUBLE FREE — undefined behaviour, heap corruption */
    bad = NULL;       /* Set to NULL after free — prevents double free */

    /* MISTAKE 2: Memory leak */
    int *leaked = malloc(1024 * 1024);  /* 1MB allocated */
    /* forgot to free(leaked); */        /* This memory is gone until program exits */
    free(leaked);

    /* MISTAKE 3: Use after free */
    int *uaf = malloc(sizeof(int));
    *uaf = 42;
    free(uaf);
    /* printf("%d\n", *uaf); */  /* USE AFTER FREE — undefined behaviour */

    return 0;
}
```

---

## DAYS 18–22: PROJECT 1 — In-Memory Key-Value Cache Engine

### Real-World Problem
Every high-performance system needs a fast in-memory cache. This project builds a production-quality hash map with separate chaining collision resolution, configurable load factor, and LRU eviction — from scratch in pure C.

### What This Demonstrates
- **Hash function:** djb2 algorithm used in real databases
- **Separate chaining:** linked list buckets for collision handling
- **Dynamic resizing:** automatic rehash when load factor exceeded
- **LRU eviction:** doubly-linked list + hash map (same structure as the LeetCode problem)
- **Memory discipline:** zero leaks verified by Valgrind

```c
/* projects/01-kv-cache-engine/cache.h */
#ifndef CACHE_H
#define CACHE_H

#include <stddef.h>
#include <stdint.h>
#include <time.h>

#define CACHE_INITIAL_BUCKETS  16
#define CACHE_MAX_LOAD_FACTOR  0.75
#define CACHE_GROW_FACTOR      2

typedef struct CacheEntry {
    char              *key;
    void              *value;
    size_t             value_size;
    time_t             expiry;       /* 0 = never expires */
    uint64_t           access_count;
    struct CacheEntry *next;         /* collision chain */
    struct CacheEntry *lru_prev;     /* LRU doubly linked list */
    struct CacheEntry *lru_next;
} CacheEntry;

typedef struct {
    CacheEntry **buckets;      /* array of bucket head pointers */
    size_t       num_buckets;
    size_t       count;        /* number of stored entries */
    CacheEntry  *lru_head;     /* Most recently used */
    CacheEntry  *lru_tail;     /* Least recently used */
    size_t       max_entries;  /* 0 = unlimited */
} Cache;

/* API */
Cache     *cache_create(size_t max_entries);
int        cache_set(Cache *c, const char *key, const void *val, size_t vsz, int ttl_secs);
void      *cache_get(Cache *c, const char *key, size_t *out_size);
int        cache_delete(Cache *c, const char *key);
int        cache_exists(Cache *c, const char *key);
size_t     cache_size(const Cache *c);
void       cache_purge_expired(Cache *c);
void       cache_print_stats(const Cache *c);
void       cache_destroy(Cache *c);

#endif /* CACHE_H */
```

```c
/* projects/01-kv-cache-engine/cache.c */
#include "cache.h"
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <time.h>

/* ---- djb2 hash function (used in Linux kernel and many DBs) ---- */
static uint64_t hash_key(const char *key, size_t num_buckets) {
    uint64_t hash = 5381;
    unsigned char c;
    while ((c = (unsigned char)*key++)) {
        hash = ((hash << 5) + hash) ^ c;  /* hash * 33 XOR c */
    }
    return hash % num_buckets;
}

/* ---- LRU List Operations ---- */
static void lru_move_to_front(Cache *c, CacheEntry *entry) {
    if (entry == c->lru_head) return;

    /* Remove from current position */
    if (entry->lru_prev) entry->lru_prev->lru_next = entry->lru_next;
    if (entry->lru_next) entry->lru_next->lru_prev = entry->lru_prev;
    if (entry == c->lru_tail) c->lru_tail = entry->lru_prev;

    /* Insert at front */
    entry->lru_prev = NULL;
    entry->lru_next = c->lru_head;
    if (c->lru_head) c->lru_head->lru_prev = entry;
    c->lru_head = entry;
    if (!c->lru_tail) c->lru_tail = entry;
}

static void lru_append(Cache *c, CacheEntry *entry) {
    entry->lru_prev = NULL;
    entry->lru_next = c->lru_head;
    if (c->lru_head) c->lru_head->lru_prev = entry;
    c->lru_head = entry;
    if (!c->lru_tail) c->lru_tail = entry;
}

static void lru_remove(Cache *c, CacheEntry *entry) {
    if (entry->lru_prev) entry->lru_prev->lru_next = entry->lru_next;
    else                  c->lru_head = entry->lru_next;
    if (entry->lru_next) entry->lru_next->lru_prev = entry->lru_prev;
    else                  c->lru_tail = entry->lru_prev;
    entry->lru_prev = entry->lru_next = NULL;
}

/* ---- Evict LRU entry when cache is full ---- */
static void evict_lru(Cache *c) {
    if (!c->lru_tail) return;
    CacheEntry *victim = c->lru_tail;
    uint64_t bucket = hash_key(victim->key, c->num_buckets);

    /* Remove from hash chain */
    CacheEntry **pp = &c->buckets[bucket];
    while (*pp && *pp != victim) pp = &(*pp)->next;
    if (*pp) *pp = victim->next;

    lru_remove(c, victim);
    free(victim->key);
    free(victim->value);
    free(victim);
    c->count--;
}

/* ---- Rehash when load factor exceeded ---- */
static int rehash(Cache *c) {
    size_t new_count = c->num_buckets * CACHE_GROW_FACTOR;
    CacheEntry **new_buckets = calloc(new_count, sizeof(CacheEntry*));
    if (!new_buckets) return -1;

    /* Re-insert all entries into new bucket array */
    for (size_t i = 0; i < c->num_buckets; i++) {
        CacheEntry *e = c->buckets[i];
        while (e) {
            CacheEntry *next = e->next;
            uint64_t new_idx = hash_key(e->key, new_count);
            e->next = new_buckets[new_idx];
            new_buckets[new_idx] = e;
            e = next;
        }
    }

    free(c->buckets);
    c->buckets     = new_buckets;
    c->num_buckets = new_count;
    return 0;
}

/* ---- Public API ---- */
Cache *cache_create(size_t max_entries) {
    Cache *c = calloc(1, sizeof(Cache));
    if (!c) return NULL;
    c->buckets = calloc(CACHE_INITIAL_BUCKETS, sizeof(CacheEntry*));
    if (!c->buckets) { free(c); return NULL; }
    c->num_buckets = CACHE_INITIAL_BUCKETS;
    c->max_entries = max_entries;
    return c;
}

int cache_set(Cache *c, const char *key, const void *val, size_t vsz, int ttl_secs) {
    if (!c || !key || !val) return -1;

    /* Check load factor — rehash if needed */
    if ((double)c->count / c->num_buckets > CACHE_MAX_LOAD_FACTOR) {
        if (rehash(c) != 0) return -1;
    }

    uint64_t bucket = hash_key(key, c->num_buckets);

    /* Update if key exists */
    for (CacheEntry *e = c->buckets[bucket]; e; e = e->next) {
        if (strcmp(e->key, key) == 0) {
            free(e->value);
            e->value = malloc(vsz);
            if (!e->value) return -1;
            memcpy(e->value, val, vsz);
            e->value_size  = vsz;
            e->expiry      = ttl_secs > 0 ? time(NULL) + ttl_secs : 0;
            e->access_count++;
            lru_move_to_front(c, e);
            return 0;
        }
    }

    /* Evict if at capacity */
    if (c->max_entries > 0 && c->count >= c->max_entries) {
        evict_lru(c);
    }

    /* Create new entry */
    CacheEntry *entry = calloc(1, sizeof(CacheEntry));
    if (!entry) return -1;

    entry->key = strdup(key);
    if (!entry->key) { free(entry); return -1; }

    entry->value = malloc(vsz);
    if (!entry->value) { free(entry->key); free(entry); return -1; }
    memcpy(entry->value, val, vsz);

    entry->value_size = vsz;
    entry->expiry     = ttl_secs > 0 ? time(NULL) + ttl_secs : 0;
    entry->access_count = 1;

    /* Insert into bucket chain (front) */
    entry->next       = c->buckets[bucket];
    c->buckets[bucket]= entry;

    /* Insert into LRU list (most recent = head) */
    lru_append(c, entry);
    c->count++;

    return 0;
}

void *cache_get(Cache *c, const char *key, size_t *out_size) {
    if (!c || !key) return NULL;
    uint64_t bucket = hash_key(key, c->num_buckets);

    for (CacheEntry *e = c->buckets[bucket]; e; e = e->next) {
        if (strcmp(e->key, key) == 0) {
            /* Check TTL */
            if (e->expiry != 0 && time(NULL) > e->expiry) {
                cache_delete(c, key);
                return NULL;  /* Expired */
            }
            e->access_count++;
            lru_move_to_front(c, e);
            if (out_size) *out_size = e->value_size;
            return e->value;
        }
    }
    return NULL;  /* Not found */
}

int cache_delete(Cache *c, const char *key) {
    if (!c || !key) return -1;
    uint64_t bucket = hash_key(key, c->num_buckets);

    CacheEntry **pp = &c->buckets[bucket];
    while (*pp) {
        CacheEntry *e = *pp;
        if (strcmp(e->key, key) == 0) {
            *pp = e->next;
            lru_remove(c, e);
            free(e->key);
            free(e->value);
            free(e);
            c->count--;
            return 0;
        }
        pp = &(*pp)->next;
    }
    return -1;  /* Not found */
}

void cache_print_stats(const Cache *c) {
    printf("=== Cache Stats ===\n");
    printf("  Entries:   %zu\n", c->count);
    printf("  Buckets:   %zu\n", c->num_buckets);
    printf("  Load:      %.2f%%\n", 100.0 * c->count / c->num_buckets);
    printf("  Max:       %zu (%s)\n", c->max_entries,
           c->max_entries == 0 ? "unlimited" : "LRU eviction active");

    if (c->lru_head) {
        printf("  MRU key:   %s\n", c->lru_head->key);
        printf("  LRU key:   %s\n", c->lru_tail->key);
    }
}

void cache_destroy(Cache *c) {
    if (!c) return;
    for (size_t i = 0; i < c->num_buckets; i++) {
        CacheEntry *e = c->buckets[i];
        while (e) {
            CacheEntry *next = e->next;
            free(e->key);
            free(e->value);
            free(e);
            e = next;
        }
    }
    free(c->buckets);
    free(c);
}

/* ---- Test Main ---- */
int main(void) {
    Cache *c = cache_create(5);  /* Max 5 entries — will trigger LRU eviction */

    /* Store various types */
    int    score  = 95;
    double gpa    = 3.87;
    char   name[] = "Alice Kumar";

    cache_set(c, "score", &score,  sizeof(score),  0);
    cache_set(c, "gpa",   &gpa,    sizeof(gpa),    0);
    cache_set(c, "name",  name,    strlen(name)+1, 10); /* TTL: 10 seconds */
    cache_set(c, "k1",    "val1",  5,              0);
    cache_set(c, "k2",    "val2",  5,              0);

    cache_print_stats(c);

    /* Access some keys (moves to MRU) */
    size_t sz;
    int *retrieved_score = cache_get(c, "score", &sz);
    printf("\nRetrieved score: %d (size=%zu)\n", *retrieved_score, sz);

    /* Add one more — should evict LRU (k1 or k2 depending on access) */
    cache_set(c, "k3", "val3", 5, 0);
    printf("\nAfter inserting k3 (triggers LRU eviction):\n");
    cache_print_stats(c);

    cache_destroy(c);
    printf("\nCache destroyed cleanly.\n");

    /* Verify with: valgrind --leak-check=full ./cache_engine */
    return 0;
}
```

```makefile
# projects/01-kv-cache-engine/Makefile
CC      = gcc
CFLAGS  = -Wall -Wextra -Wpedantic -std=c17 -g -fsanitize=address,undefined
LDFLAGS = -fsanitize=address,undefined

TARGET  = cache_engine
SRC     = cache.c

.PHONY: all clean test valgrind

all: $(TARGET)

$(TARGET): $(SRC) cache.h
	$(CC) $(CFLAGS) -o $@ $< $(LDFLAGS)

clean:
	rm -f $(TARGET) *.o

valgrind: $(TARGET)
	valgrind --leak-check=full --error-exitcode=1 ./$(TARGET)

# Run with address sanitizer (faster than valgrind)
test: all
	./$(TARGET)
```

---

## DAYS 30–34: PROJECT 2 — Student Records Database (File-Based)

### Real-World Problem
Build a persistent student record management system using binary file I/O — simulating how embedded systems and simple databases store structured data on disk.

```c
/* projects/02-student-records-db/student_db.c */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <errno.h>

#define DB_FILENAME   "students.db"
#define MAX_NAME      64
#define MAX_DEPT      32
#define RECORD_MAGIC  0xDEAD0042U   /* Identifies valid records */

/* ON-DISK RECORD FORMAT — binary, fixed-size for O(1) random access */
typedef struct __attribute__((packed)) {
    uint32_t magic;           /* 4 bytes — validity check */
    uint32_t id;              /* 4 bytes — unique student ID */
    char     name[MAX_NAME];  /* 64 bytes */
    char     dept[MAX_DEPT];  /* 32 bytes */
    float    gpa;             /* 4 bytes */
    uint32_t year;            /* 4 bytes — admission year */
    uint8_t  active;          /* 1 byte  — soft delete flag */
    uint8_t  _pad[3];         /* 3 bytes — alignment */
} StudentRecord;              /* Total: 116 bytes per record */

/* ---- DATABASE HANDLE ---- */
typedef struct {
    FILE   *fp;
    size_t  record_count;
} StudentDB;

/* ---- OPEN / CREATE ---- */
StudentDB *db_open(const char *path) {
    StudentDB *db = malloc(sizeof(StudentDB));
    if (!db) return NULL;

    db->fp = fopen(path, "r+b");   /* Open existing */
    if (!db->fp) {
        db->fp = fopen(path, "w+b"); /* Create if not exists */
        if (!db->fp) { free(db); return NULL; }
    }

    /* Count existing records */
    fseek(db->fp, 0, SEEK_END);
    long sz = ftell(db->fp);
    db->record_count = (sz > 0) ? (size_t)(sz / sizeof(StudentRecord)) : 0;
    return db;
}

/* ---- INSERT ---- */
int db_insert(StudentDB *db, const StudentRecord *rec) {
    fseek(db->fp, 0, SEEK_END);
    if (fwrite(rec, sizeof(StudentRecord), 1, db->fp) != 1) {
        perror("fwrite"); return -1;
    }
    fflush(db->fp);    /* Force write to disk */
    db->record_count++;
    return 0;
}

/* ---- GET BY ID (O(n) scan — production would use an index file) ---- */
int db_find_by_id(StudentDB *db, uint32_t id, StudentRecord *out) {
    StudentRecord rec;
    rewind(db->fp);
    while (fread(&rec, sizeof(StudentRecord), 1, db->fp) == 1) {
        if (rec.magic == RECORD_MAGIC && rec.id == id && rec.active) {
            *out = rec;
            return 0;
        }
    }
    return -1;  /* Not found */
}

/* ---- SEARCH BY DEPT ---- */
void db_search_by_dept(StudentDB *db, const char *dept) {
    StudentRecord rec;
    int found = 0;
    rewind(db->fp);
    printf("\n%-6s %-30s %-15s %-5s %-5s\n",
           "ID","Name","Dept","GPA","Year");
    printf("%s\n", "----------------------------------------------");
    while (fread(&rec, sizeof(StudentRecord), 1, db->fp) == 1) {
        if (rec.magic == RECORD_MAGIC && rec.active &&
            strncmp(rec.dept, dept, MAX_DEPT) == 0) {
            printf("%-6u %-30s %-15s %-5.2f %-5u\n",
                   rec.id, rec.name, rec.dept, rec.gpa, rec.year);
            found++;
        }
    }
    if (!found) printf("No students found in department '%s'\n", dept);
}

/* ---- UPDATE GPA (in-place) ---- */
int db_update_gpa(StudentDB *db, uint32_t id, float new_gpa) {
    StudentRecord rec;
    long offset = 0;
    rewind(db->fp);
    while (fread(&rec, sizeof(StudentRecord), 1, db->fp) == 1) {
        if (rec.magic == RECORD_MAGIC && rec.id == id && rec.active) {
            rec.gpa = new_gpa;
            fseek(db->fp, offset, SEEK_SET);  /* Seek back to record start */
            fwrite(&rec, sizeof(StudentRecord), 1, db->fp);
            fflush(db->fp);
            return 0;
        }
        offset += sizeof(StudentRecord);
    }
    return -1;
}

/* ---- SOFT DELETE ---- */
int db_delete(StudentDB *db, uint32_t id) {
    StudentRecord rec;
    long offset = 0;
    rewind(db->fp);
    while (fread(&rec, sizeof(StudentRecord), 1, db->fp) == 1) {
        if (rec.magic == RECORD_MAGIC && rec.id == id && rec.active) {
            rec.active = 0;   /* Mark as deleted */
            fseek(db->fp, offset, SEEK_SET);
            fwrite(&rec, sizeof(StudentRecord), 1, db->fp);
            fflush(db->fp);
            db->record_count--;
            return 0;
        }
        offset += sizeof(StudentRecord);
    }
    return -1;
}

void db_close(StudentDB *db) {
    if (db->fp) fclose(db->fp);
    free(db);
}

/* ---- MAIN — Demo ---- */
int main(void) {
    StudentDB *db = db_open(DB_FILENAME);
    if (!db) { perror("db_open"); return 1; }

    /* Insert records */
    StudentRecord students[] = {
        {RECORD_MAGIC, 1001, "Alice Kumar",   "CSE",  9.1f, 2022, 1, {0}},
        {RECORD_MAGIC, 1002, "Bob Rajan",     "ECE",  7.8f, 2021, 1, {0}},
        {RECORD_MAGIC, 1003, "Carol Sharma",  "CSE",  8.5f, 2022, 1, {0}},
        {RECORD_MAGIC, 1004, "David Nair",    "MECH", 6.9f, 2020, 1, {0}},
        {RECORD_MAGIC, 1005, "Eve Pillai",    "CSE",  9.5f, 2023, 1, {0}},
    };

    for (size_t i = 0; i < sizeof(students)/sizeof(students[0]); i++) {
        if (db_insert(db, &students[i]) == 0)
            printf("Inserted: %s (ID=%u)\n", students[i].name, students[i].id);
    }

    /* Search by department */
    db_search_by_dept(db, "CSE");

    /* Find by ID */
    StudentRecord found;
    if (db_find_by_id(db, 1003, &found) == 0)
        printf("\nFound: %s, GPA=%.2f\n", found.name, found.gpa);

    /* Update GPA */
    db_update_gpa(db, 1002, 8.2f);
    db_find_by_id(db, 1002, &found);
    printf("Updated Bob's GPA: %.2f\n", found.gpa);

    /* Delete a record */
    db_delete(db, 1004);
    printf("Deleted record 1004 (soft delete)\n");

    printf("\nDatabase has %zu active records\n", db->record_count);
    printf("Record size: %zu bytes → O(1) random access by record number\n",
           sizeof(StudentRecord));

    db_close(db);
    return 0;
}
```

---

## DAYS 38–42: PROJECT 3 — Custom Shell with Pipe Support

### Real-World Problem
Build a POSIX-compliant shell that supports command execution, pipe chaining (`ls | grep .c | wc -l`), I/O redirection, background execution (`&`), and basic builtins.

```c
/* projects/03-custom-shell/shell.c — full featured mini shell */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/wait.h>
#include <fcntl.h>
#include <errno.h>
#include <pwd.h>
#include <signal.h>

#define MAX_LINE    2048
#define MAX_ARGS    128
#define MAX_PIPES   16

typedef struct {
    char **argv;       /* null-terminated argument array */
    char  *infile;     /* < input.txt */
    char  *outfile;    /* > output.txt */
    int    append;     /* >> instead of > */
    int    background; /* & */
} Command;

/* ---- TOKENISER ---- */
static int tokenise(char *line, char *tokens[], int max_tokens) {
    int count = 0;
    char *tok = strtok(line, " \t\n");
    while (tok && count < max_tokens - 1) {
        tokens[count++] = tok;
        tok = strtok(NULL, " \t\n");
    }
    tokens[count] = NULL;
    return count;
}

/* ---- PARSE SINGLE COMMAND for redirections ---- */
static Command *parse_command(char *segment) {
    Command *cmd = calloc(1, sizeof(Command));
    char *parts[MAX_ARGS];
    int n = tokenise(segment, parts, MAX_ARGS);
    cmd->argv = calloc(n + 1, sizeof(char*));

    int argc = 0;
    for (int i = 0; i < n; i++) {
        if (strcmp(parts[i], ">") == 0 && i+1 < n) {
            cmd->outfile = parts[++i];
        } else if (strcmp(parts[i], ">>") == 0 && i+1 < n) {
            cmd->outfile = parts[++i];
            cmd->append  = 1;
        } else if (strcmp(parts[i], "<") == 0 && i+1 < n) {
            cmd->infile = parts[++i];
        } else if (strcmp(parts[i], "&") == 0) {
            cmd->background = 1;
        } else {
            cmd->argv[argc++] = parts[i];
        }
    }
    cmd->argv[argc] = NULL;
    return cmd;
}

/* ---- BUILT-IN COMMANDS (cannot be external processes) ---- */
static int handle_builtin(Command *cmd) {
    if (!cmd->argv[0]) return 0;

    if (strcmp(cmd->argv[0], "exit") == 0) {
        printf("Goodbye!\n");
        exit(cmd->argv[1] ? atoi(cmd->argv[1]) : 0);
    }
    if (strcmp(cmd->argv[0], "cd") == 0) {
        const char *dir = cmd->argv[1];
        if (!dir) dir = getpwuid(getuid())->pw_dir;  /* HOME */
        if (chdir(dir) != 0) perror("cd");
        return 1;
    }
    if (strcmp(cmd->argv[0], "pwd") == 0) {
        char cwd[1024];
        if (getcwd(cwd, sizeof(cwd))) printf("%s\n", cwd);
        return 1;
    }
    if (strcmp(cmd->argv[0], "export") == 0 && cmd->argv[1]) {
        char *eq = strchr(cmd->argv[1], '=');
        if (eq) { *eq = '\0'; setenv(cmd->argv[1], eq+1, 1); }
        return 1;
    }
    return 0;  /* Not a builtin */
}

/* ---- SETUP I/O REDIRECTIONS in child process ---- */
static void setup_redirections(Command *cmd) {
    if (cmd->infile) {
        int fd = open(cmd->infile, O_RDONLY);
        if (fd < 0) { perror(cmd->infile); exit(1); }
        dup2(fd, STDIN_FILENO);
        close(fd);
    }
    if (cmd->outfile) {
        int flags = O_WRONLY | O_CREAT | (cmd->append ? O_APPEND : O_TRUNC);
        int fd = open(cmd->outfile, flags, 0644);
        if (fd < 0) { perror(cmd->outfile); exit(1); }
        dup2(fd, STDOUT_FILENO);
        close(fd);
    }
}

/* ---- EXECUTE PIPELINE: cmd1 | cmd2 | cmd3 ---- */
static void execute_pipeline(char *pipe_segments[], int num_cmds) {
    int pipes[MAX_PIPES][2];
    pid_t pids[MAX_PIPES];

    /* Parse all commands */
    Command *cmds[MAX_PIPES];
    for (int i = 0; i < num_cmds; i++)
        cmds[i] = parse_command(pipe_segments[i]);

    /* Single command: handle builtins and background */
    if (num_cmds == 1) {
        if (handle_builtin(cmds[0])) goto cleanup;

        pid_t pid = fork();
        if (pid == 0) {
            setup_redirections(cmds[0]);
            execvp(cmds[0]->argv[0], cmds[0]->argv);
            fprintf(stderr, "mysh: %s: command not found\n", cmds[0]->argv[0]);
            exit(127);
        }
        if (!cmds[0]->background) waitpid(pid, NULL, 0);
        else printf("[%d] running in background\n", pid);
        goto cleanup;
    }

    /* Create pipes */
    for (int i = 0; i < num_cmds - 1; i++) {
        if (pipe(pipes[i]) < 0) { perror("pipe"); goto cleanup; }
    }

    /* Fork and exec each command */
    for (int i = 0; i < num_cmds; i++) {
        pids[i] = fork();
        if (pids[i] == 0) {
            /* Set up pipe connections */
            if (i > 0) {
                dup2(pipes[i-1][0], STDIN_FILENO);
            }
            if (i < num_cmds - 1) {
                dup2(pipes[i][1], STDOUT_FILENO);
            }
            /* Close all pipe fds in child */
            for (int j = 0; j < num_cmds - 1; j++) {
                close(pipes[j][0]); close(pipes[j][1]);
            }
            setup_redirections(cmds[i]);
            execvp(cmds[i]->argv[0], cmds[i]->argv);
            fprintf(stderr, "mysh: %s: command not found\n", cmds[i]->argv[0]);
            exit(127);
        }
    }

    /* Parent closes all pipe fds */
    for (int i = 0; i < num_cmds - 1; i++) {
        close(pipes[i][0]); close(pipes[i][1]);
    }
    /* Wait for all children */
    for (int i = 0; i < num_cmds; i++)
        waitpid(pids[i], NULL, 0);

cleanup:
    for (int i = 0; i < num_cmds; i++) {
        free(cmds[i]->argv);
        free(cmds[i]);
    }
}

/* ---- MAIN LOOP ---- */
int main(void) {
    char line[MAX_LINE];
    signal(SIGCHLD, SIG_DFL);  /* Reap background children */

    printf("MyShell v1.0 | Type 'exit' to quit\n");

    while (1) {
        char cwd[512];
        getcwd(cwd, sizeof(cwd));
        printf("[mysh %s]$ ", cwd);
        fflush(stdout);

        if (!fgets(line, sizeof(line), stdin)) break;

        /* Strip newline */
        line[strcspn(line, "\n")] = '\0';
        if (!line[0]) continue;

        /* Split on pipe | */
        char *pipe_segs[MAX_PIPES];
        int num = 0;
        char line_copy[MAX_LINE];
        strncpy(line_copy, line, sizeof(line_copy) - 1);

        char *seg = strtok(line_copy, "|");
        while (seg && num < MAX_PIPES) {
            pipe_segs[num++] = seg;
            seg = strtok(NULL, "|");
        }

        execute_pipeline(pipe_segs, num);
    }
    return 0;
}
```

---

## DAYS 48–52: PROJECT 4 — Multi-Client TCP Chat Server

```c
/* projects/04-tcp-chat-server/server.c */
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <sys/socket.h>
#include <sys/select.h>
#include <netinet/in.h>
#include <arpa/inet.h>
#include <fcntl.h>

#define PORT        9000
#define MAX_CLIENTS 64
#define BUF_SIZE    1024

typedef struct {
    int  fd;
    char nickname[32];
    char ip[INET_ADDRSTRLEN];
    int  port;
} Client;

static Client clients[MAX_CLIENTS];
static int    num_clients = 0;

static void broadcast(const char *msg, int exclude_fd) {
    for (int i = 0; i < num_clients; i++) {
        if (clients[i].fd != exclude_fd) {
            if (send(clients[i].fd, msg, strlen(msg), MSG_NOSIGNAL) < 0) {
                perror("send");
            }
        }
    }
}

static void remove_client(int fd) {
    for (int i = 0; i < num_clients; i++) {
        if (clients[i].fd == fd) {
            char msg[BUF_SIZE];
            snprintf(msg, sizeof(msg), "[SERVER] %s has left the chat\n",
                     clients[i].nickname);
            broadcast(msg, fd);
            printf("%s", msg);
            close(fd);
            clients[i] = clients[--num_clients];  /* Swap with last */
            return;
        }
    }
}

int main(void) {
    int server_fd = socket(AF_INET, SOCK_STREAM, 0);
    if (server_fd < 0) { perror("socket"); return 1; }

    int opt = 1;
    setsockopt(server_fd, SOL_SOCKET, SO_REUSEADDR, &opt, sizeof(opt));

    struct sockaddr_in addr = {
        .sin_family      = AF_INET,
        .sin_port        = htons(PORT),
        .sin_addr.s_addr = INADDR_ANY
    };
    if (bind(server_fd, (struct sockaddr*)&addr, sizeof(addr)) < 0) {
        perror("bind"); return 1;
    }
    listen(server_fd, 10);
    printf("Chat server listening on port %d\n", PORT);
    printf("Connect with: nc localhost %d\n\n", PORT);

    fd_set master_fds, read_fds;
    FD_ZERO(&master_fds);
    FD_SET(server_fd, &master_fds);
    int max_fd = server_fd;

    while (1) {
        read_fds = master_fds;
        /* select() blocks until any fd is ready for reading */
        if (select(max_fd + 1, &read_fds, NULL, NULL, NULL) < 0) {
            perror("select"); break;
        }

        for (int fd = 0; fd <= max_fd; fd++) {
            if (!FD_ISSET(fd, &read_fds)) continue;

            if (fd == server_fd) {
                /* New connection */
                struct sockaddr_in client_addr;
                socklen_t len = sizeof(client_addr);
                int new_fd = accept(server_fd, (struct sockaddr*)&client_addr, &len);
                if (new_fd < 0) { perror("accept"); continue; }

                if (num_clients >= MAX_CLIENTS) {
                    send(new_fd, "Server full\n", 12, 0);
                    close(new_fd);
                    continue;
                }

                FD_SET(new_fd, &master_fds);
                if (new_fd > max_fd) max_fd = new_fd;

                Client *c = &clients[num_clients++];
                c->fd = new_fd;
                c->port = ntohs(client_addr.sin_port);
                inet_ntop(AF_INET, &client_addr.sin_addr, c->ip, INET_ADDRSTRLEN);
                snprintf(c->nickname, sizeof(c->nickname), "user%d", new_fd);

                char welcome[BUF_SIZE];
                snprintf(welcome, sizeof(welcome),
                         "[SERVER] Welcome! Your nickname: %s. "
                         "Say /nick NAME to change it.\n", c->nickname);
                send(new_fd, welcome, strlen(welcome), 0);

                char notify[BUF_SIZE];
                snprintf(notify, sizeof(notify),
                         "[SERVER] %s joined from %s\n", c->nickname, c->ip);
                broadcast(notify, new_fd);
                printf("New client: %s (%s:%d)\n", c->nickname, c->ip, c->port);

            } else {
                /* Data from existing client */
                char buf[BUF_SIZE];
                ssize_t n = recv(fd, buf, sizeof(buf)-1, 0);

                if (n <= 0) {
                    FD_CLR(fd, &master_fds);
                    remove_client(fd);
                    continue;
                }

                buf[n] = '\0';
                buf[strcspn(buf, "\r\n")] = '\0';

                /* Find sender */
                Client *sender = NULL;
                for (int i = 0; i < num_clients; i++) {
                    if (clients[i].fd == fd) { sender = &clients[i]; break; }
                }
                if (!sender) continue;

                /* Handle /nick command */
                if (strncmp(buf, "/nick ", 6) == 0) {
                    strncpy(sender->nickname, buf+6, sizeof(sender->nickname)-1);
                    char msg[BUF_SIZE];
                    snprintf(msg, sizeof(msg),
                             "[SERVER] Nickname changed to %s\n", sender->nickname);
                    send(fd, msg, strlen(msg), 0);
                    continue;
                }

                /* Broadcast message */
                char msg[BUF_SIZE + 64];
                snprintf(msg, sizeof(msg), "[%s]: %s\n", sender->nickname, buf);
                printf("%s", msg);
                broadcast(msg, fd);
            }
        }
    }

    close(server_fd);
    return 0;
}
```

---

## DAYS 57–62: PROJECT 5 — Memory Leak Detector (malloc Tracer)

### Real-World Problem
Build a malloc/free interceptor using `LD_PRELOAD` hooks that tracks every allocation, detects leaks, and generates a report with stack context.

```c
/* projects/05-malloc-tracer/malloc_tracer.c
   Compile: gcc -shared -fPIC -o malloc_tracer.so malloc_tracer.c -ldl
   Use:     LD_PRELOAD=./malloc_tracer.so ./your_program
*/
#define _GNU_SOURCE
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <dlfcn.h>
#include <pthread.h>
#include <execinfo.h>

#define MAX_ALLOCS  65536
#define STACK_DEPTH 8

typedef struct {
    void   *ptr;
    size_t  size;
    void   *stack[STACK_DEPTH];
    int     stack_depth;
} AllocRecord;

static AllocRecord  records[MAX_ALLOCS];
static size_t       num_records = 0;
static pthread_mutex_t lock = PTHREAD_MUTEX_INITIALIZER;
static int          initialized = 0;
static int          tracing_active = 0;

/* Original function pointers */
static void *(*real_malloc)(size_t)          = NULL;
static void  (*real_free)(void*)             = NULL;
static void *(*real_realloc)(void*, size_t)  = NULL;
static void *(*real_calloc)(size_t, size_t)  = NULL;

static void init(void) {
    real_malloc  = dlsym(RTLD_NEXT, "malloc");
    real_free    = dlsym(RTLD_NEXT, "free");
    real_realloc = dlsym(RTLD_NEXT, "realloc");
    real_calloc  = dlsym(RTLD_NEXT, "calloc");
    initialized  = 1;
    tracing_active = 1;
}

void *malloc(size_t size) {
    if (!initialized) init();
    void *ptr = real_malloc(size);

    if (ptr && tracing_active && size > 0) {
        pthread_mutex_lock(&lock);
        if (num_records < MAX_ALLOCS) {
            AllocRecord *r = &records[num_records++];
            r->ptr        = ptr;
            r->size       = size;
            r->stack_depth= backtrace(r->stack, STACK_DEPTH);
        }
        pthread_mutex_unlock(&lock);
    }
    return ptr;
}

void free(void *ptr) {
    if (!initialized) init();
    if (!ptr) return;

    if (tracing_active) {
        pthread_mutex_lock(&lock);
        /* Remove from tracking */
        for (size_t i = 0; i < num_records; i++) {
            if (records[i].ptr == ptr) {
                records[i] = records[--num_records];  /* Swap with last */
                break;
            }
        }
        pthread_mutex_unlock(&lock);
    }
    real_free(ptr);
}

void *calloc(size_t n, size_t size) {
    if (!initialized) init();
    void *ptr = real_calloc(n, size);
    if (ptr && tracing_active) {
        pthread_mutex_lock(&lock);
        if (num_records < MAX_ALLOCS) {
            records[num_records++] = (AllocRecord){
                .ptr = ptr, .size = n * size,
                .stack_depth = backtrace(records[num_records].stack, STACK_DEPTH)
            };
        }
        pthread_mutex_unlock(&lock);
    }
    return ptr;
}

/* Called at program exit — reports leaks */
__attribute__((destructor))
static void leak_report(void) {
    tracing_active = 0;
    if (num_records == 0) {
        fprintf(stderr, "\n✅ MALLOC TRACER: No memory leaks detected!\n");
        return;
    }

    size_t total_leaked = 0;
    fprintf(stderr, "\n❌ MALLOC TRACER: %zu LEAK(S) DETECTED!\n", num_records);
    fprintf(stderr, "═══════════════════════════════════════\n");

    for (size_t i = 0; i < num_records; i++) {
        fprintf(stderr, "\nLeak #%zu: %zu bytes at %p\n",
                i+1, records[i].size, records[i].ptr);
        /* Print backtrace symbols for call site */
        char **syms = backtrace_symbols(records[i].stack, records[i].stack_depth);
        if (syms) {
            for (int j = 2; j < records[i].stack_depth; j++) {  /* skip our hooks */
                fprintf(stderr, "  [%d] %s\n", j-2, syms[j]);
            }
            real_free(syms);
        }
        total_leaked += records[i].size;
    }

    fprintf(stderr, "\n═══════════════════════════════════════\n");
    fprintf(stderr, "Total leaked: %zu bytes (%zu allocation(s))\n",
            total_leaked, num_records);
}
```

---

## DAYS 68–75: PROJECT 6 — Real-Time System Resource Monitor

### Real-World Problem
Build a live `top`-like system monitor using `/proc` filesystem and ncurses — showing CPU, RAM, disk, and top processes with colour-coded alerts.

```c
/* projects/06-system-monitor/monitor.c
   gcc -Wall -O2 -o monitor monitor.c -lncurses -lm
   Run: ./monitor
*/
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#include <unistd.h>
#include <ncurses.h>
#include <time.h>
#include <math.h>
#include <dirent.h>
#include <sys/sysinfo.h>

#define REFRESH_MS  1000   /* Update every 1 second */
#define MAX_PROCS   256
#define BAR_WIDTH   40

typedef struct {
    int    pid;
    char   name[64];
    float  cpu_pct;
    float  mem_pct;
    long   vsz_kb;
    char   state;
} ProcessInfo;

typedef struct {
    float cpu_user, cpu_sys, cpu_idle;
    unsigned long total_ram, free_ram, used_ram;
    unsigned long total_swap, free_swap;
    float disk_used_pct;
    ProcessInfo procs[MAX_PROCS];
    int num_procs;
    struct timespec ts;
} SystemSnapshot;

/* ---- READ CPU FROM /proc/stat ---- */
static void read_cpu(SystemSnapshot *s) {
    FILE *f = fopen("/proc/stat", "r");
    if (!f) return;
    unsigned long user, nice, sys, idle, iowait, irq, softirq;
    fscanf(f, "cpu %lu %lu %lu %lu %lu %lu %lu",
           &user, &nice, &sys, &idle, &iowait, &irq, &softirq);
    fclose(f);

    unsigned long total = user + nice + sys + idle + iowait + irq + softirq;
    if (total == 0) return;
    s->cpu_user  = 100.0f * (user + nice) / total;
    s->cpu_sys   = 100.0f * sys / total;
    s->cpu_idle  = 100.0f * idle / total;
}

/* ---- READ MEMORY FROM sysinfo ---- */
static void read_memory(SystemSnapshot *s) {
    struct sysinfo info;
    sysinfo(&info);
    unsigned long unit = info.mem_unit;
    s->total_ram  = info.totalram  * unit / 1024;  /* KB */
    s->free_ram   = info.freeram   * unit / 1024;
    s->used_ram   = s->total_ram - s->free_ram;
    s->total_swap = info.totalswap * unit / 1024;
    s->free_swap  = info.freeswap  * unit / 1024;
}

/* ---- RENDER A PROGRESS BAR ---- */
static void draw_bar(WINDOW *w, int row, int col, float pct, int width,
                     int low_colour, int high_colour) {
    int filled = (int)(pct / 100.0f * width);
    int colour = pct > 80 ? high_colour : low_colour;

    wmove(w, row, col);
    wattron(w, COLOR_PAIR(colour));
    for (int i = 0; i < filled; i++) waddch(w, '|');
    wattroff(w, COLOR_PAIR(colour));
    for (int i = filled; i < width; i++) waddch(w, ' ');
    wprintw(w, " %.1f%%", pct);
}

/* ---- MAIN NCURSES LOOP ---- */
int main(void) {
    /* Ncurses init */
    initscr();
    cbreak(); noecho(); curs_set(0);
    timeout(REFRESH_MS);
    start_color();

    /* Colour pairs */
    init_pair(1, COLOR_GREEN,  COLOR_BLACK);  /* Normal */
    init_pair(2, COLOR_RED,    COLOR_BLACK);  /* Warning */
    init_pair(3, COLOR_CYAN,   COLOR_BLACK);  /* Header */
    init_pair(4, COLOR_YELLOW, COLOR_BLACK);  /* Info */

    while (1) {
        SystemSnapshot s = {0};
        clock_gettime(CLOCK_REALTIME, &s.ts);
        read_cpu(&s);
        read_memory(&s);

        clear();
        int row = 0;

        /* Header */
        attron(COLOR_PAIR(3) | A_BOLD);
        mvprintw(row++, 0, "  MyTop — System Resource Monitor  "
                           "(q=quit, r=refresh)");
        attroff(COLOR_PAIR(3) | A_BOLD);

        struct tm *tm_info = localtime(&s.ts.tv_sec);
        char timebuf[32];
        strftime(timebuf, sizeof(timebuf), "%Y-%m-%d %H:%M:%S", tm_info);
        mvprintw(row++, 0, "  Time: %s", timebuf);
        row++;

        /* CPU bars */
        mvprintw(row++, 2, "CPU Usage:");
        mvprintw(row,   4, "User [");
        draw_bar(stdscr, row++, 10, s.cpu_user, BAR_WIDTH, 1, 2);
        mvprintw(row,   4, "Sys  [");
        draw_bar(stdscr, row++, 10, s.cpu_sys,  BAR_WIDTH, 4, 2);
        mvprintw(row,   4, "Idle [");
        draw_bar(stdscr, row++, 10, s.cpu_idle, BAR_WIDTH, 1, 1);
        row++;

        /* RAM bar */
        float ram_pct = (s.total_ram > 0)
                        ? 100.0f * s.used_ram / s.total_ram : 0;
        mvprintw(row++, 2, "Memory:  %lu MB used / %lu MB total",
                 s.used_ram/1024, s.total_ram/1024);
        mvprintw(row,   4, "RAM  [");
        draw_bar(stdscr, row++, 10, ram_pct, BAR_WIDTH, 1, 2);
        row++;

        /* Process table */
        attron(COLOR_PAIR(3) | A_BOLD);
        mvprintw(row++, 2, "%-7s %-20s %-8s %-8s %s",
                 "PID", "NAME", "CPU%", "MEM%", "STATE");
        attroff(COLOR_PAIR(3) | A_BOLD);

        /* Read processes from /proc */
        DIR *proc_dir = opendir("/proc");
        if (proc_dir) {
            struct dirent *ent;
            int count = 0;
            while ((ent = readdir(proc_dir)) && count < 15) {
                /* Check if directory name is a number (PID) */
                int is_pid = 1;
                for (char *p = ent->d_name; *p; p++)
                    if (*p < '0' || *p > '9') { is_pid = 0; break; }
                if (!is_pid) continue;

                char path[128];
                snprintf(path, sizeof(path), "/proc/%s/stat", ent->d_name);
                FILE *sf = fopen(path, "r");
                if (!sf) continue;

                int pid; char name[64]; char state;
                if (fscanf(sf, "%d (%63[^)]) %c", &pid, name, &state) == 3) {
                    mvprintw(row++, 2, "%-7d %-20s %-8s %-8s %c",
                             pid, name, "-", "-", state);
                    count++;
                }
                fclose(sf);
            }
            closedir(proc_dir);
        }

        /* Footer */
        attron(COLOR_PAIR(4));
        mvprintw(LINES-1, 0, "  Press 'q' to quit | Updates every 1 second");
        attroff(COLOR_PAIR(4));

        refresh();

        int ch = getch();
        if (ch == 'q' || ch == 'Q') break;
    }

    endwin();
    return 0;
}
```

---

## 📋 COMPLETE DAILY TIMETABLE

| Day | Phase | Topic | Practical Task | Output |
|-----|-------|-------|----------------|--------|
| **1** | Foundations | Compilation pipeline (4 stages) | See each stage with gcc flags | `day-01-compilation.md` |
| **2** | Foundations | Memory layout (text/data/bss/heap/stack) | Map variables to segments | `day-02-memory-layout.md` |
| **3** | Foundations | Data types, UB, bitwise operators | Type sizes + bit manipulation | `day-03-types.md` |
| **4** | Foundations | Functions + stack frames | Recursive factorial, pass by value vs pointer | `day-04-functions.md` |
| **5** | Foundations | Arrays + strings + buffer overflow | Array vs pointer string | `day-05-arrays-strings.md` |
| **6** | Foundations | Preprocessor — macros and traps | SQUARE(a+b) trap demo | `day-06-preprocessor.md` |
| **7** | Foundations | Structures + padding + alignment | sizeof before/after reorder | `day-07-structs.md` |
| **8** | Foundations | Unions + bit fields | TCP flags in 1 byte | `day-08-unions.md` |
| **9** | Foundations | File handling (text + binary) | Read/write binary struct | `day-09-files.md` |
| **10** | Foundations | Error handling + errno + perror | Proper error-checking program | `day-10-errors.md` |
| **11** | Pointers | All pointer types + const variants | Address mapping program | `day-11-pointers.md` |
| **12** | Pointers | malloc/calloc/realloc/free | Dynamic array implementation | `day-12-malloc.md` |
| **13** | Pointers | Function pointers | Callback-based sort | `day-13-func-ptrs.md` |
| **14** | Pointers | Pointer to struct + arrow operator | Linked list traversal | `day-14-struct-ptrs.md` |
| **15** | Pointers | Common bugs (dangling, wild, double free) | Trigger + fix each bug | `day-15-ptr-bugs.md` |
| **16** | Pointers | Void pointers + generic programming | Generic swap function | `day-16-void-ptrs.md` |
| **17** | Pointers | 2D array vs pointer-to-pointer | Matrix operations | `day-17-2d-arrays.md` |
| **18–22** | **PROJECT 1** | KV Cache Engine | LRU + hash map + TTL | GitHub + Valgrind report |
| **21** | Data Structs | Linked list (singly + doubly) | Full insert/delete/reverse | `day-21-linked-list.md` |
| **22** | Data Structs | Stack + Queue in C | Array-based + linked-based | `day-22-stack-queue.md` |
| **23** | Data Structs | Hash map (chaining) | Word frequency counter | `day-23-hashmap.md` |
| **24** | Data Structs | Binary search tree | Insert + search + inorder | `day-24-bst.md` |
| **25** | Data Structs | Graph (adjacency list) | BFS + DFS implementation | `day-25-graph.md` |
| **26** | Data Structs | Sorting algorithms | Merge sort + Quick sort | `day-26-sorting.md` |
| **27** | Data Structs | Searching algorithms | Binary search + linear | `day-27-searching.md` |
| **28** | Data Structs | Memory pool allocator | Pool of fixed-size blocks | `day-28-pool.md` |
| **29–30** | Data Structs | Circular buffer (ring buffer) | Producer-consumer ring | `day-29-ringbuffer.md` |
| **30–34** | **PROJECT 2** | Student Records DB | Binary file + struct I/O | GitHub + blog post |
| **31** | Systems | POSIX file I/O (open/read/write/close) | Low-level file copy | `day-31-posix-io.md` |
| **32** | Systems | Process creation (fork/exec/wait) | Process tree display | `day-32-processes.md` |
| **33** | Systems | Signals (signal/sigaction) | Graceful shutdown handler | `day-33-signals.md` |
| **34** | Systems | Pipes (anonymous + named) | Parent-child comm via pipe | `day-34-pipes.md` |
| **35** | Systems | Shared memory + mmap | Inter-process counter | `day-35-shm.md` |
| **36** | Systems | Sockets (TCP client + server) | Echo server | `day-36-sockets.md` |
| **37** | Systems | select() / poll() multiplexing | Multi-client echo | `day-37-multiplexing.md` |
| **38–42** | **PROJECT 3** | Custom Shell + Pipe | Full shell implementation | GitHub + demo video |
| **43** | Advanced | const, volatile, restrict keywords | Embedded use cases | `day-43-qualifiers.md` |
| **44** | Advanced | static, extern, register | Scope and linkage demo | `day-44-storage.md` |
| **45** | Advanced | Inline assembly (basic) | Read CPUID instruction | `day-45-asm.md` |
| **46** | Advanced | Multithreading (pthreads) | Thread-safe counter | `day-46-pthreads.md` |
| **47** | Advanced | Mutex + condition variables | Producer-consumer sync | `day-47-mutex.md` |
| **48–52** | **PROJECT 4** | TCP Chat Server | select() + multi-client | GitHub + demo video |
| **53** | Advanced | Endianness + byte order | htons/ntohl demo | `day-53-endian.md` |
| **54** | Advanced | Alignment + packed structs | Network packet parsing | `day-54-alignment.md` |
| **55** | Advanced | Callback patterns + generic code | Event system in C | `day-55-callbacks.md` |
| **56** | Debugging | GDB: breakpoints, watchpoints, backtrace | Debug the KV cache | `day-56-gdb.md` |
| **57–62** | **PROJECT 5** | Malloc Tracer (LD_PRELOAD) | Hook malloc + detect leaks | GitHub + example report |
| **58** | Debugging | Valgrind: memcheck, helgrind | Fix a leaky program | Valgrind report |
| **59** | Debugging | AddressSanitizer + UBSan | Compile-time detection | `day-59-asan.md` |
| **60** | Debugging | clang-tidy + cppcheck | Static analysis findings | Analysis report |
| **61** | Debugging | gprof + perf profiling | Hot path in sort | Profile chart |
| **62** | Debugging | Makefiles deep dive + CMake | Multi-file project | Full Makefile |
| **63** | Debugging | strace + ltrace | Trace shell project | strace output |
| **64** | Debugging | Core dumps analysis | Cause + analyse segfault | `day-64-coredump.md` |
| **65** | Debugging | Common C bugs (review + quiz) | Fix 10 buggy programs | Bug list doc |
| **66** | DSA in C | Arrays + two pointers | 5 problems solved | `dsa/arrays.c` |
| **67** | DSA in C | Linked list problems | Reverse + detect cycle | `dsa/linked-list.c` |
| **68–75** | **PROJECT 6** | System Resource Monitor | /proc + ncurses dashboard | GitHub + screenshot |
| **69** | DSA in C | Trees (BST + traversals) | 5 tree problems | `dsa/trees.c` |
| **70** | DSA in C | Sorting algorithms (all) | Comparison benchmark | `dsa/sorting.c` |
| **71** | DSA in C | Dynamic programming in C | Coin change + LCS | `dsa/dp.c` |
| **72** | DSA in C | Graph algorithms (BFS/DFS) | Shortest path | `dsa/graphs.c` |
| **73** | DSA in C | Bit manipulation problems | 10 bit problems | `dsa/bits.c` |
| **74** | Interview | Top 30 C interview questions | Answer all without notes | `interview-prep/` |
| **75** | Interview | Mock interview simulation | 2 coding + 10 theory Q | Blog post: C journey |

---

## 🎯 TOP 30 C INTERVIEW QUESTIONS WITH ANSWERS

### Memory & Pointers
1. **`int *p[10]` vs `int (*p)[10]`?** — `int *p[10]`: array of 10 pointers to int. `int (*p)[10]`: pointer to an array of 10 ints.
2. **Dangling pointer vs wild pointer?** — Dangling: pointer to freed/out-of-scope memory. Wild: uninitialized pointer with garbage address.
3. **Why is `SQUARE(x+1)` wrong with `#define SQUARE(x) x*x`?** — Expands to `x+1*x+1` = `x + x + 1`. Use `((x)*(x))`.
4. **Can you increment a pointer to an array? `int a[5]; a++;`** — No. Array name is not an lvalue; `a++` is a compile error.
5. **`char *s = "hello"` vs `char s[] = "hello"`?** — Pointer: literal in read-only text segment, modifying causes UB/segfault. Array: copy on stack, modifiable.
6. **What is `void *` and when to use it?** — Generic pointer; cannot be dereferenced without casting; used for generic functions like `memcpy`, `qsort`.
7. **Explain `const int *p`, `int *const p`, `const int *const p`.** — (1) Value is const, pointer can change. (2) Pointer is const, value can change. (3) Both const.
8. **What happens when `malloc` returns `NULL`?** — Heap is exhausted; must check return value; using NULL pointer causes segfault.

### Memory Management
9. **Difference between `malloc` and `calloc`?** — `malloc` allocates uninitialised memory. `calloc` allocates and zeroes the memory.
10. **What is a memory leak?** — Allocated memory that is never freed. Program's RSS grows until OOM killer terminates it.
11. **What is double free?** — Calling `free()` on an already-freed pointer. Causes heap corruption; UB.
12. **What happens to memory when a process exits?** — OS reclaims all memory (even leaks). But within a long-running server, leaks accumulate.

### Structures & Compilation
13. **Why does struct padding exist?** — CPU requires types to be aligned to their natural boundary (int at 4-byte, double at 8-byte). Padding ensures this.
14. **How to eliminate struct padding?** — `__attribute__((packed))` (GCC) or `#pragma pack(1)`. Warning: may cause unaligned access faults on some architectures.
15. **Difference between `struct` and `union`?** — Struct: each member has its own memory. Union: all members share the same memory location.
16. **What does `static` mean in different contexts?** — (1) Local variable: preserves value between calls. (2) File-scope: limits linkage to this translation unit. (3) Function parameter: not meaningful.
17. **What is the difference between `#include <file>` and `#include "file"`?** — Angle brackets search system directories first. Quotes search current directory first.
18. **What is a header guard?** — `#ifndef / #define / #endif` prevents a header from being included multiple times in one translation unit.

### Tricky Programs
19. **What does `printf("%d", sizeof(int))` print?** — Warning! `sizeof` returns `size_t` (unsigned). Should use `%zu`. With `%d`: implementation-dependent but usually 4.
20. **What is the output of this?**
    ```c
    int a = 1, b = 2;
    printf("%d %d\n", a++, ++b);
    ```
    Answer: `1 3` — `a++` post-increment returns 1, `++b` pre-increment returns 3.
21. **What is the output?** `printf("%d\n", 1 << 31);` — UB for signed int. Result is implementation-defined.
22. **Is `sizeof` a function?** — No. It is a compile-time operator. `sizeof(int)` is evaluated at compile time.

---

## ✅ C MNC READINESS CHECKLIST

| Skill | Evidence Required | Grade |
|---|---|---|
| Compilation model | Explain all 4 stages + linker errors | ✅ |
| Memory model | Map any code to text/data/bss/heap/stack | ✅ |
| Pointer mastery | Pointer-to-pointer, function pointers, const variants | ✅ |
| Memory management | Zero-leak programs verified by Valgrind | ✅ |
| Struct + alignment | Explain and optimise struct padding | ✅ |
| File I/O | Binary file with O(1) random access | ✅ |
| POSIX systems | fork/exec/pipe/socket/select used in projects | ✅ |
| Debugging toolchain | GDB + Valgrind + ASan + strace used | ✅ |
| Preprocessor | Macro safety, header guards, conditional compilation | ✅ |
| Multithreading | pthreads + mutex + condition variables | ✅ |
| 6 Projects | All on GitHub with README + Valgrind reports | ✅ |
| DSA in C | Linked list, BST, hash map — all from scratch | ✅ |

---

*C Programming Mastery Roadmap — MNC Production-Grade*
*Reference: C Programming MNC Interview Guide — "Think like the compiler"*
*Tools: GCC · Clang · GDB · Valgrind · AddressSanitizer · ncurses · POSIX*
