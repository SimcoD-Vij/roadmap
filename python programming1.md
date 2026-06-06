# 🐍 Python Complete Mastery Roadmap
### From Core Fundamentals → MNC Production-Grade Python Engineer
#### *Day-by-Day · Project-by-Project · Interview-Ready*

> **Reference:** Built from Python Programming MNC Interview Guide  
> **Target:** Tier 1 MNC readiness (Google, Amazon, Microsoft, Infosys, TCS Digital)  
> **Projects:** 6 brand-new real-world projects — none overlap with existing roadmaps

---

## 📐 MASTER ARCHITECTURE

```
╔══════════════════════════════════════════════════════════════════════╗
║                  PYTHON MASTERY — 75-DAY MAP                        ║
╠══════════════════════════════════════════════════════════════════════╣
║  PHASE 1 (Days 1–10):   CORE PYTHON + INTERNALS                    ║
║  PHASE 2 (Days 11–20):  OOP + DESIGN PATTERNS                      ║
║  PHASE 3 (Days 21–30):  ADVANCED PYTHON                            ║
║  PHASE 4 (Days 31–42):  AUTOMATION + SYSTEM INTEGRATION            ║
║  PHASE 5 (Days 43–55):  FASTAPI + DATABASES + TESTING              ║
║  PHASE 6 (Days 56–65):  PERFORMANCE + DEVOPS + PACKAGING           ║
║  PHASE 7 (Days 66–75):  DSA IN PYTHON + INTERVIEW PREP             ║
╚══════════════════════════════════════════════════════════════════════╝

PROJECTS (NEW — not in any other roadmap):
  P1 — Smart Expense Tracker CLI         (Days 8–10)  — OOP + SQLite
  P2 — Network Health Monitor            (Days 25–28) — Async + psutil
  P3 — Resume Parser & Job Match Scorer  (Days 38–42) — NLP + PDF
  P4 — Automated Exam Result Analyzer    (Days 48–52) — pandas + Reports
  P5 — DevUtils: Your Own PyPI Package   (Days 58–62) — Packaging
  P6 — FastAPI + Celery Job Scheduler    (Days 68–75) — Async Tasks
```

---

## 🛠️ TECH STACK

| Layer | Tool | Why |
|---|---|---|
| Language | Python 3.12 | Latest stable, match-case, better performance |
| Web | FastAPI 0.110 | Async, auto OpenAPI docs, used at Uber/Netflix |
| ORM | SQLAlchemy 2.0 | Industry-standard database abstraction |
| DB | PostgreSQL 16 + SQLite | Production + lightweight dev |
| Task Queue | Celery + Redis | Background jobs, used at Instagram |
| Testing | pytest + pytest-cov | MNC standard testing framework |
| HTTP Client | httpx (async) + requests | Both sync and async HTTP |
| PDF/NLP | pdfplumber + spaCy | Document parsing + NLP |
| Data | pandas + polars | Data manipulation + fast analytics |
| Packaging | setuptools + twine | Build and publish your own library |
| Code Quality | ruff + black + mypy | Linting, formatting, type checking |
| CI/CD | GitHub Actions | Automated pipeline |
| Container | Docker | Containerised deployment |

---

## 📝 DOCUMENTATION STRATEGY

```
GitHub Structure:
python-mastery/
├── core-python/          ← Phase 1–3 practice
├── automation/           ← Phase 4 scripts
├── fastapi-apps/         ← Phase 5 web apps
├── dsa-python/           ← Phase 7 solutions
│   ├── arrays/
│   ├── trees/
│   └── dp/
├── projects/
│   ├── 01-expense-tracker/
│   ├── 02-network-monitor/
│   ├── 03-resume-parser/
│   ├── 04-exam-analyzer/
│   ├── 05-devutils-package/
│   └── 06-job-scheduler/
└── interview-prep/
    ├── python-internals-qa.md
    ├── oops-qa.md
    └── async-qa.md
```

**Daily template:** `core-python/day-XX-topic.md`
- Concept in own words
- Code I wrote and ran
- What surprised me
- 3 active recall questions

---

---

# 🔵 PHASE 1: CORE PYTHON + INTERNALS (Days 1–10)

> **Goal:** Go beyond syntax. Understand how Python actually works in memory. This is what MNC interviewers test when they move past "what is a list."

---

## DAY 1: Python Execution Model + Memory Model

### Core Concepts

```python
# HOW PYTHON RUNS YOUR CODE:
# Source (.py) → Tokeniser → Parser → AST → Bytecode (.pyc) → CPython VM

import dis
import sys

def add(a, b):
    return a + b

# See the actual bytecode Python compiles your function to
print("=== Bytecode for add() ===")
dis.dis(add)

# MEMORY: Everything in Python is an OBJECT
# Even integers are objects with a type, value, and reference count
x = 42
print(f"\nid(x):     {id(x)}")           # Memory address
print(f"type(x):   {type(x)}")           # <class 'int'>
print(f"sys.getrefcount(x): {sys.getrefcount(x)}")  # Reference count

# INTEGER CACHING — the interview trap
a = 256
b = 256
print(f"\na = 256, b = 256: a is b → {a is b}")   # True (cached)

a = 257
b = 257
print(f"a = 257, b = 257: a is b → {a is b}")   # False (not cached)
# CPython caches integers -5 to 256 as singletons for performance
# 257+ creates new objects each time

# STRING INTERNING
s1 = "hello"
s2 = "hello"
s3 = "hello world"
s4 = "hello world"
print(f"\ns1 is s2 → {s1 is s2}")   # True (interned — short, no spaces)
print(f"s3 is s4 → {s3 is s4}")   # May be False (spaces break interning)

# MUTABLE vs IMMUTABLE — the most common interview topic
# Immutable: int, float, str, tuple, frozenset, bytes
# Mutable:   list, dict, set, bytearray, custom objects

# Dangerous: mutable default argument
def bad_append(item, lst=[]):      # lst is created ONCE at function definition
    lst.append(item)
    return lst

print(bad_append(1))   # [1]
print(bad_append(2))   # [1, 2] — NOT [2]! lst persists between calls

def good_append(item, lst=None):   # Correct pattern
    if lst is None:
        lst = []
    lst.append(item)
    return lst
```

### ✅ Active Recall
1. What is the difference between `is` and `==`?
2. Why does `[] == []` return `True` but `[] is []` return `False`?
3. What are the integers CPython caches? Why?

---

## DAY 2: Data Structures in Depth

```python
# LIST INTERNALS: Over-allocated dynamic array
import sys
lst = []
prev_size = sys.getsizeof(lst)
print("List growth pattern:")
for i in range(20):
    lst.append(i)
    size = sys.getsizeof(lst)
    if size != prev_size:
        print(f"  len={len(lst):2d}: size={size} bytes (grew)")
        prev_size = size
# You'll see: Python over-allocates to avoid resizing on every append
# Growth: 0→4→8→16→25→35... (roughly 1.125x each time after 8)

# DICT INTERNALS (Python 3.7+: insertion-ordered)
# Backed by a hash table. O(1) average for get/set/delete.
# Collision: open addressing (probe next slot)
d = {'a': 1, 'b': 2, 'c': 3}
print(f"\nDict size: {sys.getsizeof(d)} bytes")

# DICT COMPREHENSION — powerful and fast
squares = {x: x**2 for x in range(1, 11)}
evens_squared = {k: v for k, v in squares.items() if k % 2 == 0}
print(f"Even squares: {evens_squared}")

# SET OPERATIONS — interview favourites
team_a = {'Alice', 'Bob', 'Carol', 'Dave'}
team_b = {'Carol', 'Dave', 'Eve', 'Frank'}

print(f"\nUnion (both teams):         {team_a | team_b}")
print(f"Intersection (overlap):     {team_a & team_b}")
print(f"Difference (A only):        {team_a - team_b}")
print(f"Symmetric diff (not both):  {team_a ^ team_b}")

# TUPLE PACKING AND UNPACKING
point = (3, 4)                          # packing
x, y = point                            # unpacking
first, *rest, last = [1, 2, 3, 4, 5]   # starred unpacking
print(f"\nfirst={first}, rest={rest}, last={last}")

# NAMEDTUPLE — better than plain tuple for structured data
from collections import namedtuple, defaultdict, Counter, deque

Employee = namedtuple('Employee', ['name', 'dept', 'salary'])
emp = Employee('Alice', 'Engineering', 95000)
print(f"Employee: {emp.name} in {emp.dept} earns ₹{emp.salary}")

# DEFAULTDICT — no KeyError on missing key
word_count = defaultdict(int)
for word in "the quick brown fox jumps over the lazy fox".split():
    word_count[word] += 1
print(f"\nWord counts: {dict(word_count)}")

# COUNTER — frequency counting in one line
from collections import Counter
freq = Counter("the quick brown fox jumps over the lazy fox".split())
print(f"Top 3 words: {freq.most_common(3)}")

# DEQUE — O(1) append/pop on BOTH ends (vs list: O(n) on left side)
dq = deque([1, 2, 3], maxlen=5)
dq.appendleft(0)   # O(1) — list.insert(0, x) is O(n)
dq.append(4)
print(f"Deque: {dq}")
```

---

## DAY 3: Functions — Deep Dive

```python
# FIRST-CLASS FUNCTIONS — functions are objects
def greet(name):
    return f"Hello, {name}!"

func_ref = greet            # store function in variable
print(func_ref("Alice"))    # call via reference

funcs = [str.upper, str.lower, str.title]
word = "hElLo wOrLd"
for f in funcs:
    print(f(word))

# CLOSURES — function + its enclosing scope
def make_counter(start=0):
    count = [start]             # use list so it's mutable from inner scope
    def increment(by=1):
        count[0] += by
        return count[0]
    def reset():
        count[0] = start
    return increment, reset     # return TWO functions sharing same closure

inc, rst = make_counter(10)
print(inc())    # 11
print(inc(5))   # 16
rst()
print(inc())    # 11

# ARGS AND KWARGS
def flexible(*args, **kwargs):
    print(f"Positional: {args}")
    print(f"Keyword: {kwargs}")

flexible(1, 2, 3, name="Alice", role="Engineer")

# KEYWORD-ONLY and POSITIONAL-ONLY (Python 3.8+)
def strict(pos_only, /, normal, *, kw_only):
    # pos_only: must be positional
    # normal: either way
    # kw_only: must be keyword
    return f"{pos_only} | {normal} | {kw_only}"

print(strict(1, 2, kw_only=3))         # OK
print(strict(1, normal=2, kw_only=3))  # OK

# FUNCTOOLS
from functools import partial, lru_cache, wraps

@lru_cache(maxsize=128)
def fibonacci(n):
    if n < 2: return n
    return fibonacci(n-1) + fibonacci(n-2)

print(fibonacci(50))       # Instant due to memoisation
print(fibonacci.cache_info())

# partial — pre-fill arguments
def power(base, exp):
    return base ** exp

square = partial(power, exp=2)
cube   = partial(power, exp=3)
print(f"square(5)={square(5)}, cube(3)={cube(3)}")
```

---

## DAY 4: Comprehensions + Functional Tools

```python
# COMPREHENSIONS — the Pythonic way
# List comprehension
squares = [x**2 for x in range(10)]

# Conditional comprehension
even_squares = [x**2 for x in range(10) if x % 2 == 0]

# Nested comprehension (matrix flatten)
matrix = [[1,2,3],[4,5,6],[7,8,9]]
flat = [cell for row in matrix for cell in row]

# Dict comprehension
inv_map = {v: k for k, v in {'a':1,'b':2,'c':3}.items()}

# Generator expression (lazy — no memory allocation upfront)
gen = (x**2 for x in range(1_000_000))  # instant — nothing computed yet
print(next(gen))   # computes ONLY the first value
print(next(gen))   # computes ONLY the second value

# MEMORY COMPARISON
import sys
lst_mem = sys.getsizeof([x**2 for x in range(10000)])
gen_mem = sys.getsizeof(x**2 for x in range(10000))
print(f"List (10k items):      {lst_mem:,} bytes")
print(f"Generator (10k items): {gen_mem} bytes")  # ~104 bytes always!

# MAP, FILTER, REDUCE
from functools import reduce

nums = [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
doubled  = list(map(lambda x: x*2, nums))
evens    = list(filter(lambda x: x%2==0, nums))
total    = reduce(lambda acc, x: acc+x, nums)

# Pythonic alternatives (usually preferred over map/filter):
doubled2 = [x*2 for x in nums]
evens2   = [x for x in nums if x%2==0]
total2   = sum(nums)
```

---

## DAY 5: OOP — Dunder Methods + Property + Class vs Static

```python
# DUNDER METHODS — make your objects feel like Python builtins
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y

    def __repr__(self):
        return f"Vector({self.x}, {self.y})"

    def __str__(self):
        return f"({self.x}, {self.y})"

    def __add__(self, other):         # v1 + v2
        return Vector(self.x + other.x, self.y + other.y)

    def __sub__(self, other):         # v1 - v2
        return Vector(self.x - other.x, self.y - other.y)

    def __mul__(self, scalar):        # v * 3
        return Vector(self.x * scalar, self.y * scalar)

    def __rmul__(self, scalar):       # 3 * v  (reversed)
        return self.__mul__(scalar)

    def __abs__(self):                # abs(v) → magnitude
        return (self.x**2 + self.y**2) ** 0.5

    def __bool__(self):               # bool(v) → False if zero vector
        return bool(abs(self))

    def __eq__(self, other):
        return self.x == other.x and self.y == other.y

    def __hash__(self):               # allow use as dict key or in set
        return hash((self.x, self.y))

    def __iter__(self):               # allow: x, y = vector
        yield self.x
        yield self.y

    def __len__(self):                # len(v) → always 2 for 2D vector
        return 2

    @classmethod
    def from_tuple(cls, t):           # alternative constructor
        return cls(t[0], t[1])

    @staticmethod
    def dot_product(v1, v2):          # utility, no self/cls needed
        return v1.x*v2.x + v1.y*v2.y

    # PROPERTY — controlled attribute access
    @property
    def magnitude(self):
        return abs(self)

    @property
    def unit(self):
        if not self:
            raise ValueError("Cannot normalise zero vector")
        return Vector(self.x / self.magnitude, self.y / self.magnitude)


v1 = Vector(3, 4)
v2 = Vector(1, 2)
print(v1 + v2)              # Vector(4, 6)
print(abs(v1))              # 5.0
print(v1.magnitude)         # 5.0
x, y = v1                   # unpacking via __iter__
print(Vector.dot_product(v1, v2))  # 11
```

---

## DAY 6: Iterators + Generators

```python
# ITERATOR PROTOCOL
class CountDown:
    def __init__(self, start):
        self.current = start

    def __iter__(self):
        return self

    def __next__(self):
        if self.current <= 0:
            raise StopIteration
        val = self.current
        self.current -= 1
        return val

for n in CountDown(5):
    print(n, end=" ")   # 5 4 3 2 1

# GENERATOR FUNCTIONS — cleaner iterator syntax
def countdown(start):
    while start > 0:
        yield start
        start -= 1

# INFINITE GENERATOR — only compute what you need
def fibonacci():
    a, b = 0, 1
    while True:
        yield a
        a, b = b, a + b

from itertools import islice
first_10_fibs = list(islice(fibonacci(), 10))
print(first_10_fibs)   # [0,1,1,2,3,5,8,13,21,34]

# GENERATOR PIPELINE — memory-efficient data processing
def read_large_file(filepath):
    with open(filepath) as f:
        for line in f:
            yield line.strip()

def filter_errors(lines):
    for line in lines:
        if 'ERROR' in line:
            yield line

def parse_timestamps(lines):
    import re
    pattern = re.compile(r'\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}')
    for line in lines:
        match = pattern.search(line)
        if match:
            yield match.group(), line

# Usage: fully lazy — processes one line at a time, regardless of file size
# pipeline = parse_timestamps(filter_errors(read_large_file("app.log")))
# for timestamp, line in pipeline:
#     print(f"{timestamp}: {line[:60]}")

# YIELD FROM — delegate to sub-generator
def chain(*iterables):
    for it in iterables:
        yield from it

result = list(chain([1,2], [3,4], [5,6]))
print(result)   # [1,2,3,4,5,6]
```

---

## DAY 7: Decorators

```python
from functools import wraps
import time
import logging

# BASIC DECORATOR ANATOMY
def timer(func):
    @wraps(func)   # preserve original function metadata (name, docstring)
    def wrapper(*args, **kwargs):
        start = time.perf_counter()
        result = func(*args, **kwargs)
        elapsed = (time.perf_counter() - start) * 1000
        print(f"[TIMER] {func.__name__} took {elapsed:.2f}ms")
        return result
    return wrapper

# PARAMETERISED DECORATOR
def retry(max_attempts=3, exceptions=(Exception,), delay=1.0):
    def decorator(func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            for attempt in range(1, max_attempts + 1):
                try:
                    return func(*args, **kwargs)
                except exceptions as e:
                    if attempt == max_attempts:
                        raise
                    print(f"[RETRY] {func.__name__} attempt {attempt} failed: {e}. Retrying in {delay}s...")
                    time.sleep(delay)
        return wrapper
    return decorator

# CLASS-BASED DECORATOR (when you need state)
class RateLimiter:
    def __init__(self, max_calls_per_second):
        self.interval = 1.0 / max_calls_per_second
        self.last_called = 0.0

    def __call__(self, func):
        @wraps(func)
        def wrapper(*args, **kwargs):
            elapsed = time.time() - self.last_called
            wait = self.interval - elapsed
            if wait > 0:
                time.sleep(wait)
            self.last_called = time.time()
            return func(*args, **kwargs)
        return wrapper

# USAGE
@timer
@retry(max_attempts=3, exceptions=(ConnectionError,), delay=0.5)
def fetch_data(url):
    # Simulates an API call that might fail
    import random
    if random.random() < 0.3:
        raise ConnectionError("Network error")
    return {"data": "result"}

@RateLimiter(max_calls_per_second=2)
def limited_api_call():
    print(f"Called at {time.time():.2f}")

# DECORATOR STACKING: applied bottom-up
# @timer → @retry means: timer wraps retry wraps fetch_data
```

---

## DAY 8-10: PROJECT 1 — Smart Expense Tracker CLI

### Real-World Problem
Individuals and small businesses need a command-line tool to track expenses, categorise spending, set monthly budgets, and generate reports with visual charts.

### What This Demonstrates
- **OOP:** Expense, Category, Budget, Report classes
- **SQLite:** Persistent storage with proper schema
- **argparse:** Professional CLI interface
- **pandas:** Data analysis and reporting
- **Rich library:** Beautiful terminal output
- **pytest:** Unit tests for all business logic

```python
# projects/01-expense-tracker/tracker/models.py
from dataclasses import dataclass, field
from datetime import date
from enum import Enum
from typing import Optional

class Category(Enum):
    FOOD        = "Food & Dining"
    TRANSPORT   = "Transport"
    UTILITIES   = "Utilities"
    HEALTH      = "Health & Medical"
    EDUCATION   = "Education"
    SHOPPING    = "Shopping"
    ENTERTAINMENT="Entertainment"
    RENT        = "Rent & Housing"
    SAVINGS     = "Savings"
    OTHER       = "Other"

@dataclass
class Expense:
    amount: float
    category: Category
    description: str
    date: date = field(default_factory=date.today)
    id: Optional[int] = None
    tags: list = field(default_factory=list)

    def __post_init__(self):
        if self.amount <= 0:
            raise ValueError(f"Amount must be positive, got {self.amount}")
        if not self.description.strip():
            raise ValueError("Description cannot be empty")

@dataclass
class Budget:
    category: Category
    monthly_limit: float
    month: int
    year: int

    @property
    def is_valid_month(self):
        return 1 <= self.month <= 12
```

```python
# projects/01-expense-tracker/tracker/database.py
import sqlite3
from contextlib import contextmanager
from pathlib import Path
from datetime import date
from .models import Expense, Category, Budget

DB_PATH = Path.home() / ".expense_tracker" / "expenses.db"

def init_db():
    DB_PATH.parent.mkdir(parents=True, exist_ok=True)
    with get_connection() as conn:
        conn.executescript("""
            CREATE TABLE IF NOT EXISTS expenses (
                id          INTEGER PRIMARY KEY AUTOINCREMENT,
                amount      REAL NOT NULL CHECK(amount > 0),
                category    TEXT NOT NULL,
                description TEXT NOT NULL,
                date        TEXT NOT NULL,
                tags        TEXT DEFAULT ''
            );
            CREATE TABLE IF NOT EXISTS budgets (
                id          INTEGER PRIMARY KEY AUTOINCREMENT,
                category    TEXT NOT NULL,
                monthly_limit REAL NOT NULL CHECK(monthly_limit > 0),
                month       INTEGER NOT NULL CHECK(month BETWEEN 1 AND 12),
                year        INTEGER NOT NULL,
                UNIQUE(category, month, year)
            );
            CREATE INDEX IF NOT EXISTS idx_expenses_date     ON expenses(date);
            CREATE INDEX IF NOT EXISTS idx_expenses_category ON expenses(category);
        """)

@contextmanager
def get_connection():
    conn = sqlite3.connect(DB_PATH)
    conn.row_factory = sqlite3.Row
    try:
        yield conn
        conn.commit()
    except Exception:
        conn.rollback()
        raise
    finally:
        conn.close()

class ExpenseRepository:
    def add(self, expense: Expense) -> int:
        with get_connection() as conn:
            cur = conn.execute(
                "INSERT INTO expenses (amount, category, description, date, tags) VALUES (?,?,?,?,?)",
                (expense.amount, expense.category.name, expense.description,
                 expense.date.isoformat(), ",".join(expense.tags))
            )
            return cur.lastrowid

    def get_by_month(self, month: int, year: int) -> list[Expense]:
        start = date(year, month, 1).isoformat()
        end   = date(year, month+1 if month < 12 else 1,
                     1 if month < 12 else 1).isoformat() if month < 12 \
                else date(year+1, 1, 1).isoformat()
        with get_connection() as conn:
            rows = conn.execute(
                "SELECT * FROM expenses WHERE date >= ? AND date < ? ORDER BY date DESC",
                (start, end)
            ).fetchall()
        return [self._row_to_expense(r) for r in rows]

    def get_total_by_category(self, month: int, year: int) -> dict:
        start = date(year, month, 1).isoformat()
        end   = date(year+1, 1, 1).isoformat() if month == 12 \
                else date(year, month+1, 1).isoformat()
        with get_connection() as conn:
            rows = conn.execute(
                "SELECT category, SUM(amount) as total FROM expenses "
                "WHERE date >= ? AND date < ? GROUP BY category",
                (start, end)
            ).fetchall()
        return {r["category"]: r["total"] for r in rows}

    def delete(self, expense_id: int) -> bool:
        with get_connection() as conn:
            cur = conn.execute("DELETE FROM expenses WHERE id = ?", (expense_id,))
            return cur.rowcount > 0

    def _row_to_expense(self, row) -> Expense:
        return Expense(
            id=row["id"], amount=row["amount"],
            category=Category[row["category"]],
            description=row["description"],
            date=date.fromisoformat(row["date"]),
            tags=row["tags"].split(",") if row["tags"] else []
        )
```

```python
# projects/01-expense-tracker/tracker/analytics.py
import pandas as pd
from datetime import date
from .database import ExpenseRepository
from .models import Category

class ExpenseAnalytics:
    def __init__(self):
        self.repo = ExpenseRepository()

    def monthly_summary(self, month: int, year: int) -> dict:
        expenses = self.repo.get_by_month(month, year)
        if not expenses:
            return {"total": 0, "by_category": {}, "count": 0}

        df = pd.DataFrame([{
            "amount": e.amount,
            "category": e.category.value,
            "date": e.date,
            "description": e.description
        } for e in expenses])

        summary = {
            "total": df["amount"].sum(),
            "count": len(df),
            "avg_per_day": df["amount"].sum() / df["date"].nunique(),
            "by_category": df.groupby("category")["amount"].agg(
                ["sum", "count", "mean"]).to_dict("index"),
            "largest_expense": df.nlargest(1, "amount").iloc[0].to_dict(),
            "daily_totals": df.groupby("date")["amount"].sum().to_dict()
        }
        return summary

    def spending_trend(self, months: int = 6) -> pd.DataFrame:
        today = date.today()
        records = []
        for i in range(months - 1, -1, -1):
            m = (today.month - i - 1) % 12 + 1
            y = today.year - ((today.month - i - 1) // 12)
            totals = self.repo.get_total_by_category(m, y)
            records.append({"month": f"{y}-{m:02d}", "total": sum(totals.values()),
                            **totals})
        return pd.DataFrame(records).fillna(0)

    def budget_vs_actual(self, month: int, year: int) -> pd.DataFrame:
        actuals = self.repo.get_total_by_category(month, year)
        # Would also fetch budgets from DB in full implementation
        data = [{"category": cat, "actual": actuals.get(cat, 0)}
                for cat in [c.name for c in Category]]
        return pd.DataFrame(data)
```

```python
# projects/01-expense-tracker/cli.py — Main CLI entry point
import argparse
import sys
from datetime import date
from rich.console import Console
from rich.table import Table
from rich.panel import Panel
from rich import print as rprint
from tracker.database import init_db, ExpenseRepository
from tracker.analytics import ExpenseAnalytics
from tracker.models import Expense, Category

console = Console()

def add_expense(args):
    try:
        cat = Category[args.category.upper()]
        expense = Expense(amount=args.amount, category=cat,
                         description=args.description,
                         tags=args.tags.split(",") if args.tags else [])
        repo = ExpenseRepository()
        expense_id = repo.add(expense)
        rprint(f"[green]✅ Expense added (ID: {expense_id})[/green]")
        rprint(f"   ₹{args.amount:.2f} for [bold]{args.description}[/bold] "
               f"in category [cyan]{cat.value}[/cyan]")
    except (KeyError, ValueError) as e:
        rprint(f"[red]❌ Error: {e}[/red]")
        sys.exit(1)

def show_report(args):
    today = date.today()
    month = args.month or today.month
    year  = args.year  or today.year
    analytics = ExpenseAnalytics()
    summary = analytics.monthly_summary(month, year)

    if summary["count"] == 0:
        rprint(f"[yellow]No expenses found for {year}-{month:02d}[/yellow]")
        return

    console.print(Panel.fit(
        f"[bold]Monthly Report: {year}-{month:02d}[/bold]\n"
        f"Total: [red]₹{summary['total']:,.2f}[/red] | "
        f"Transactions: {summary['count']} | "
        f"Avg/day: ₹{summary['avg_per_day']:.2f}",
        border_style="blue"))

    table = Table(title="Spending by Category", show_header=True)
    table.add_column("Category", style="cyan")
    table.add_column("Total", justify="right", style="red")
    table.add_column("Count", justify="right")
    table.add_column("Avg", justify="right")
    table.add_column("% of Total", justify="right")

    for cat, stats in sorted(summary["by_category"].items(),
                              key=lambda x: x[1]["sum"], reverse=True):
        pct = stats["sum"] / summary["total"] * 100
        bar = "█" * int(pct / 5)
        table.add_row(cat, f"₹{stats['sum']:,.2f}", str(int(stats["count"])),
                      f"₹{stats['mean']:,.2f}", f"{pct:.1f}% {bar}")

    console.print(table)

def main():
    init_db()
    parser = argparse.ArgumentParser(description="💰 Smart Expense Tracker")
    subparsers = parser.add_subparsers(dest="command")

    # ADD command
    add_p = subparsers.add_parser("add", help="Add a new expense")
    add_p.add_argument("amount",      type=float, help="Amount in ₹")
    add_p.add_argument("category",    help=f"Category: {[c.name for c in Category]}")
    add_p.add_argument("description", help="Short description")
    add_p.add_argument("--tags",      help="Comma-separated tags")
    add_p.set_defaults(func=add_expense)

    # REPORT command
    rep_p = subparsers.add_parser("report", help="Monthly spending report")
    rep_p.add_argument("--month", type=int, help="Month number (default: current)")
    rep_p.add_argument("--year",  type=int, help="Year (default: current)")
    rep_p.set_defaults(func=show_report)

    args = parser.parse_args()
    if not args.command:
        parser.print_help()
    else:
        args.func(args)

if __name__ == "__main__":
    main()

# Usage:
# python cli.py add 250 FOOD "Lunch at Saravana Bhavan"
# python cli.py add 1500 TRANSPORT "Monthly bus pass" --tags "commute,monthly"
# python cli.py report
# python cli.py report --month 1 --year 2025
```

```python
# projects/01-expense-tracker/tests/test_models.py
import pytest
from datetime import date
from tracker.models import Expense, Category

class TestExpense:
    def test_valid_expense_creation(self):
        exp = Expense(amount=100.0, category=Category.FOOD, description="Lunch")
        assert exp.amount == 100.0
        assert exp.category == Category.FOOD
        assert exp.date == date.today()

    def test_negative_amount_raises(self):
        with pytest.raises(ValueError, match="Amount must be positive"):
            Expense(amount=-50, category=Category.FOOD, description="Test")

    def test_zero_amount_raises(self):
        with pytest.raises(ValueError):
            Expense(amount=0, category=Category.FOOD, description="Test")

    def test_empty_description_raises(self):
        with pytest.raises(ValueError, match="Description cannot be empty"):
            Expense(amount=100, category=Category.FOOD, description="   ")

    def test_default_date_is_today(self):
        exp = Expense(amount=50, category=Category.OTHER, description="Test")
        assert exp.date == date.today()

    def test_tags_default_empty(self):
        exp = Expense(amount=50, category=Category.OTHER, description="Test")
        assert exp.tags == []
```

---

## DAYS 11–20: OOP MASTERY

## DAY 11: Inheritance + MRO + ABC

```python
from abc import ABC, abstractmethod
import inspect

# ABSTRACT BASE CLASS — force subclasses to implement methods
class DataProcessor(ABC):
    def __init__(self, source: str):
        self.source = source
        self._processed = False

    @abstractmethod
    def extract(self) -> list:
        """Extract raw data from source."""
        ...

    @abstractmethod
    def transform(self, data: list) -> list:
        """Transform extracted data."""
        ...

    def load(self, data: list) -> None:
        """Default load — can be overridden."""
        print(f"Loading {len(data)} records from {self.source}")

    # TEMPLATE METHOD PATTERN
    def run(self) -> list:
        raw = self.extract()
        transformed = self.transform(raw)
        self.load(transformed)
        self._processed = True
        return transformed

class CSVProcessor(DataProcessor):
    def extract(self) -> list:
        import csv
        with open(self.source, 'r') as f:
            return list(csv.DictReader(f))

    def transform(self, data: list) -> list:
        return [{k: v.strip() for k, v in row.items()} for row in data if any(row.values())]

# MRO (Method Resolution Order) — DIAMOND PROBLEM solution
class A:
    def greet(self): return "A"

class B(A):
    def greet(self): return f"B→{super().greet()}"

class C(A):
    def greet(self): return f"C→{super().greet()}"

class D(B, C):
    def greet(self): return f"D→{super().greet()}"

d = D()
print(d.greet())           # D→B→C→A
print(D.__mro__)           # (<class 'D'>, <class 'B'>, <class 'C'>, <class 'A'>, ...)
# Python uses C3 linearisation — no ambiguity ever
```

---

## DAYS 21–30: ADVANCED PYTHON

## DAY 21: Context Managers + `__enter__`/`__exit__`

```python
from contextlib import contextmanager, asynccontextmanager
import time

# CLASS-BASED CONTEXT MANAGER
class DatabaseTransaction:
    def __init__(self, connection):
        self.conn = connection
        self.savepoint = None

    def __enter__(self):
        self.savepoint = self.conn.execute("SAVEPOINT sp1")
        print("Transaction started")
        return self.conn

    def __exit__(self, exc_type, exc_val, exc_tb):
        if exc_type is None:
            self.conn.execute("RELEASE SAVEPOINT sp1")
            print("Transaction committed")
        else:
            self.conn.execute("ROLLBACK TO SAVEPOINT sp1")
            print(f"Transaction rolled back due to: {exc_type.__name__}")
        return False   # Don't suppress the exception

# GENERATOR-BASED (simpler for simple cases)
@contextmanager
def timed_block(name: str):
    print(f"[START] {name}")
    start = time.perf_counter()
    try:
        yield                   # code inside `with` block runs here
    finally:
        elapsed = (time.perf_counter() - start) * 1000
        print(f"[END]   {name}: {elapsed:.2f}ms")

with timed_block("Data processing"):
    result = sum(i**2 for i in range(1_000_000))
```

---

## DAY 22: Async/Await + asyncio

```python
import asyncio
import httpx
import time

# ASYNC FUNDAMENTALS
async def fetch_price(ticker: str, client: httpx.AsyncClient) -> dict:
    """Simulate async API call."""
    await asyncio.sleep(0.1)  # Non-blocking wait (vs time.sleep which blocks)
    return {"ticker": ticker, "price": hash(ticker) % 1000 + 100}

async def fetch_all_prices(tickers: list) -> list:
    async with httpx.AsyncClient() as client:
        # CONCURRENT execution — all requests in parallel
        tasks = [fetch_price(t, client) for t in tickers]
        results = await asyncio.gather(*tasks)  # runs ALL concurrently
        return results

# COMPARISON: Sequential vs Concurrent
async def main():
    tickers = ["RELIANCE", "TCS", "INFY", "WIPRO", "HDFC",
               "ICICI", "SBI", "BAJAJ", "ITC", "ONGC"]

    # Sequential: each waits for previous
    start = time.perf_counter()
    sequential = [await fetch_price(t, None) for t in tickers]
    seq_time = time.perf_counter() - start

    # Concurrent: all run simultaneously
    start = time.perf_counter()
    concurrent = await fetch_all_prices(tickers)
    con_time = time.perf_counter() - start

    print(f"Sequential: {seq_time:.2f}s | Concurrent: {con_time:.2f}s")
    print(f"Speedup: {seq_time/con_time:.1f}x faster")

asyncio.run(main())
```

---

## DAYS 25–28: PROJECT 2 — Network Health Monitor Dashboard

### Real-World Problem
DevOps and SRE teams need a lightweight tool to continuously monitor server health — CPU, RAM, disk, active ports, external connectivity — and send alerts when thresholds are breached.

```python
# projects/02-network-monitor/monitor.py
import asyncio
import psutil
import socket
import subprocess
import json
import smtplib
from datetime import datetime
from dataclasses import dataclass, asdict
from email.mime.text import MIMEText
from pathlib import Path
from typing import Optional
import httpx

@dataclass
class SystemMetrics:
    timestamp: str
    hostname: str
    cpu_percent: float
    ram_percent: float
    ram_used_gb: float
    ram_total_gb: float
    disk_percent: float
    disk_used_gb: float
    disk_total_gb: float
    network_sent_mb: float
    network_recv_mb: float
    open_ports: list
    top_processes: list

@dataclass
class Alert:
    level: str       # INFO, WARNING, CRITICAL
    metric: str
    value: float
    threshold: float
    message: str
    timestamp: str

class AlertThresholds:
    cpu_warning    = 70.0
    cpu_critical   = 90.0
    ram_warning    = 75.0
    ram_critical   = 90.0
    disk_warning   = 80.0
    disk_critical  = 95.0

class MetricsCollector:
    def collect(self) -> SystemMetrics:
        cpu    = psutil.cpu_percent(interval=1)
        ram    = psutil.virtual_memory()
        disk   = psutil.disk_usage('/')
        net    = psutil.net_io_counters()
        procs  = sorted(psutil.process_iter(['pid', 'name', 'cpu_percent', 'memory_percent']),
                        key=lambda p: p.info['cpu_percent'], reverse=True)[:5]

        return SystemMetrics(
            timestamp   = datetime.now().isoformat(),
            hostname    = socket.gethostname(),
            cpu_percent = cpu,
            ram_percent = ram.percent,
            ram_used_gb = ram.used  / (1024**3),
            ram_total_gb= ram.total / (1024**3),
            disk_percent= disk.percent,
            disk_used_gb= disk.used  / (1024**3),
            disk_total_gb=disk.total / (1024**3),
            network_sent_mb = net.bytes_sent / (1024**2),
            network_recv_mb = net.bytes_recv / (1024**2),
            open_ports  = self._get_listening_ports(),
            top_processes=[
                {"pid": p.info['pid'], "name": p.info['name'],
                 "cpu": p.info['cpu_percent'], "mem": p.info['memory_percent']}
                for p in procs if p.info['name']
            ]
        )

    def _get_listening_ports(self) -> list:
        try:
            conns = psutil.net_connections(kind='inet')
            return list({c.laddr.port for c in conns if c.status == 'LISTEN'})
        except (psutil.AccessDenied, Exception):
            return []

class AlertEngine:
    def __init__(self, thresholds: AlertThresholds = AlertThresholds()):
        self.t = thresholds
        self.alert_history: list[Alert] = []

    def evaluate(self, metrics: SystemMetrics) -> list[Alert]:
        alerts = []
        checks = [
            ("CPU",  metrics.cpu_percent,  self.t.cpu_warning,  self.t.cpu_critical),
            ("RAM",  metrics.ram_percent,  self.t.ram_warning,  self.t.ram_critical),
            ("DISK", metrics.disk_percent, self.t.disk_warning, self.t.disk_critical),
        ]
        for name, value, warn, crit in checks:
            if value >= crit:
                alerts.append(Alert("CRITICAL", name, value, crit,
                    f"{name} usage {value:.1f}% exceeds critical threshold {crit}%",
                    metrics.timestamp))
            elif value >= warn:
                alerts.append(Alert("WARNING", name, value, warn,
                    f"{name} usage {value:.1f}% exceeds warning threshold {warn}%",
                    metrics.timestamp))
        return alerts

class NetworkMonitor:
    def __init__(self, interval: int = 10, log_file: str = "monitor.log"):
        self.interval  = interval
        self.collector = MetricsCollector()
        self.alerter   = AlertEngine()
        self.log_path  = Path(log_file)
        self._running  = False

    async def _collect_loop(self):
        while self._running:
            metrics = self.collector.collect()
            alerts  = self.alerter.evaluate(metrics)
            self._display(metrics, alerts)
            self._log(metrics)
            await asyncio.sleep(self.interval)

    def _display(self, m: SystemMetrics, alerts: list[Alert]):
        print(f"\n{'='*60}")
        print(f"🖥  {m.hostname} | {m.timestamp[:19]}")
        print(f"{'='*60}")
        cpu_bar  = self._bar(m.cpu_percent)
        ram_bar  = self._bar(m.ram_percent)
        disk_bar = self._bar(m.disk_percent)
        print(f"CPU  [{cpu_bar}] {m.cpu_percent:5.1f}%")
        print(f"RAM  [{ram_bar}] {m.ram_percent:5.1f}% ({m.ram_used_gb:.1f}/{m.ram_total_gb:.1f} GB)")
        print(f"DISK [{disk_bar}] {m.disk_percent:5.1f}% ({m.disk_used_gb:.0f}/{m.disk_total_gb:.0f} GB)")
        print(f"NET  ↑{m.network_sent_mb:.1f} MB  ↓{m.network_recv_mb:.1f} MB")
        print(f"Ports: {sorted(m.open_ports)}")
        if m.top_processes:
            print("\nTop Processes:")
            for p in m.top_processes[:3]:
                print(f"  [{p['pid']:6}] {p['name']:<20} CPU:{p['cpu']:5.1f}% MEM:{p['mem']:4.1f}%")
        for alert in alerts:
            icon = "🔴" if alert.level == "CRITICAL" else "🟡"
            print(f"{icon} {alert.level}: {alert.message}")

    def _bar(self, pct: float, width: int = 20) -> str:
        filled = int(pct / 100 * width)
        color  = "▓" if pct < 70 else "█"
        return color * filled + "░" * (width - filled)

    def _log(self, metrics: SystemMetrics):
        with self.log_path.open("a") as f:
            f.write(json.dumps(asdict(metrics)) + "\n")

    async def run(self):
        self._running = True
        print("🟢 Network Health Monitor started. Press Ctrl+C to stop.")
        try:
            await self._collect_loop()
        except KeyboardInterrupt:
            print("\n🔴 Monitor stopped.")
        finally:
            self._running = False

if __name__ == "__main__":
    monitor = NetworkMonitor(interval=5)
    asyncio.run(monitor.run())
```

---

## DAYS 38–42: PROJECT 3 — Resume Parser & Job Match Scorer

### Real-World Problem
HR teams process hundreds of resumes. An automated tool extracts key information (skills, experience, education) and scores each resume against a job description.

```python
# projects/03-resume-parser/parser/extractor.py
import re
import pdfplumber
from pathlib import Path
from dataclasses import dataclass, field
from typing import Optional

SKILL_KEYWORDS = {
    "languages":   ["python","java","javascript","typescript","go","rust","c++","c#","kotlin","swift"],
    "frameworks":  ["fastapi","django","flask","spring","react","angular","vue","node.js"],
    "databases":   ["postgresql","mysql","mongodb","redis","cassandra","elasticsearch","sqlite"],
    "cloud":       ["aws","azure","gcp","kubernetes","docker","terraform","jenkins"],
    "data":        ["pandas","numpy","spark","kafka","airflow","dbt","tableau","power bi"],
    "ml":          ["tensorflow","pytorch","scikit-learn","xgboost","opencv","huggingface"],
}

EMAIL_PATTERN    = re.compile(r'\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.[A-Z|a-z]{2,}\b')
PHONE_PATTERN    = re.compile(r'(\+91|0)?[\s\-]?[6-9]\d{9}')
LINKEDIN_PATTERN = re.compile(r'linkedin\.com/in/[\w\-]+')
GITHUB_PATTERN   = re.compile(r'github\.com/[\w\-]+')
YEARS_EXP_PATTERN= re.compile(r'(\d+)\+?\s+years?\s+(?:of\s+)?experience', re.IGNORECASE)

@dataclass
class ParsedResume:
    file_path: str
    raw_text: str
    name: Optional[str] = None
    email: Optional[str] = None
    phone: Optional[str] = None
    linkedin: Optional[str] = None
    github: Optional[str] = None
    years_experience: Optional[int] = None
    skills: dict = field(default_factory=dict)
    education: list = field(default_factory=list)
    total_skill_count: int = 0

class ResumeExtractor:
    def extract(self, pdf_path: str) -> ParsedResume:
        path = Path(pdf_path)
        raw_text = self._extract_text(path)
        resume = ParsedResume(file_path=str(path), raw_text=raw_text)
        self._extract_contact(raw_text, resume)
        self._extract_skills(raw_text, resume)
        self._extract_experience(raw_text, resume)
        return resume

    def _extract_text(self, path: Path) -> str:
        if path.suffix.lower() == ".pdf":
            with pdfplumber.open(path) as pdf:
                return "\n".join(page.extract_text() or "" for page in pdf.pages)
        return path.read_text(encoding="utf-8", errors="ignore")

    def _extract_contact(self, text: str, resume: ParsedResume):
        email   = EMAIL_PATTERN.search(text)
        phone   = PHONE_PATTERN.search(text)
        linkedin= LINKEDIN_PATTERN.search(text)
        github  = GITHUB_PATTERN.search(text)
        resume.email    = email.group()    if email    else None
        resume.phone    = phone.group()    if phone    else None
        resume.linkedin = linkedin.group() if linkedin else None
        resume.github   = github.group()   if github   else None

    def _extract_skills(self, text: str, resume: ParsedResume):
        text_lower = text.lower()
        for category, keywords in SKILL_KEYWORDS.items():
            found = [kw for kw in keywords if re.search(r'\b' + re.escape(kw) + r'\b', text_lower)]
            if found:
                resume.skills[category] = found
        resume.total_skill_count = sum(len(v) for v in resume.skills.values())

    def _extract_experience(self, text: str, resume: ParsedResume):
        match = YEARS_EXP_PATTERN.search(text)
        resume.years_experience = int(match.group(1)) if match else None


class JobMatchScorer:
    def score(self, resume: ParsedResume, job_description: str) -> dict:
        jd_lower = job_description.lower()
        scores = {}

        # Skill match (60% weight)
        required_skills = self._extract_required_skills(jd_lower)
        resume_skills_flat = [s for skills in resume.skills.values() for s in skills]
        matched = [s for s in required_skills if s in resume_skills_flat]
        skill_score = (len(matched) / max(len(required_skills), 1)) * 100
        scores["skill_match"]   = round(skill_score, 1)
        scores["matched_skills"]= matched
        scores["missing_skills"]= [s for s in required_skills if s not in matched]

        # Experience match (20% weight)
        exp_match = self._score_experience(resume.years_experience, jd_lower)
        scores["experience_match"] = exp_match

        # Portfolio match (20% weight — GitHub = +20 points)
        portfolio_score = 20 if resume.github else 0
        scores["portfolio_score"]  = portfolio_score

        # FINAL SCORE
        final = (skill_score * 0.60) + (exp_match * 0.20) + (portfolio_score * 0.20)
        scores["final_score"]   = round(final, 1)
        scores["recommendation"] = self._recommend(final)
        return scores

    def _extract_required_skills(self, jd: str) -> list:
        return [kw for cat_skills in SKILL_KEYWORDS.values()
                for kw in cat_skills
                if re.search(r'\b' + re.escape(kw) + r'\b', jd)]

    def _score_experience(self, candidate_years: Optional[int], jd: str) -> float:
        match = YEARS_EXP_PATTERN.search(jd)
        if not match or candidate_years is None:
            return 50.0
        required = int(match.group(1))
        if candidate_years >= required:
            return 100.0
        return max(0, (candidate_years / required) * 100)

    def _recommend(self, score: float) -> str:
        if score >= 80: return "STRONG MATCH — Shortlist immediately"
        if score >= 60: return "GOOD MATCH — Consider for interview"
        if score >= 40: return "PARTIAL MATCH — Review manually"
        return "WEAK MATCH — Does not meet requirements"
```

---

## DAYS 48–52: PROJECT 4 — Automated Exam Result Analyzer

### Real-World Problem
Universities receive exam scores in CSV files and need automated analysis: class performance statistics, subject-wise pass rates, grade distribution, at-risk student identification, and PDF reports with charts.

```python
# projects/04-exam-analyzer/analyzer.py
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib.patches as mpatches
from pathlib import Path
from dataclasses import dataclass
import smtplib
from email.mime.multipart import MIMEMultipart
from email.mime.base import MIMEBase
from email import encoders
import json

@dataclass
class ExamConfig:
    pass_mark: float = 40.0
    distinction: float = 75.0
    first_class: float = 60.0

class ExamResultAnalyzer:
    def __init__(self, csv_path: str, config: ExamConfig = ExamConfig()):
        self.df  = pd.read_csv(csv_path)
        self.cfg = config
        self._preprocess()

    def _preprocess(self):
        subject_cols = [c for c in self.df.columns
                        if c not in ["StudentID", "Name", "Department", "Semester"]]
        self.subject_cols = subject_cols
        self.df["Total"]  = self.df[subject_cols].sum(axis=1)
        max_possible      = len(subject_cols) * 100
        self.df["Percent"]= (self.df["Total"] / max_possible * 100).round(2)
        self.df["Grade"]  = self.df["Percent"].apply(self._assign_grade)
        self.df["Status"] = self.df[subject_cols].apply(
            lambda row: "PASS" if (row >= self.cfg.pass_mark).all() else "FAIL", axis=1)
        self.df["Backlogs"]= self.df[subject_cols].apply(
            lambda row: (row < self.cfg.pass_mark).sum(), axis=1)

    def _assign_grade(self, percent: float) -> str:
        if percent >= 90: return "O"       # Outstanding
        if percent >= 75: return "A+"      # Distinction
        if percent >= 60: return "A"       # First Class
        if percent >= 50: return "B+"      # Second Class Higher
        if percent >= 40: return "B"       # Second Class
        return "F"                         # Fail

    def class_statistics(self) -> dict:
        return {
            "total_students":     len(self.df),
            "pass_count":         (self.df["Status"] == "PASS").sum(),
            "fail_count":         (self.df["Status"] == "FAIL").sum(),
            "pass_rate":          round((self.df["Status"] == "PASS").mean() * 100, 2),
            "class_avg":          round(self.df["Percent"].mean(), 2),
            "highest_scorer":     self.df.loc[self.df["Percent"].idxmax(), "Name"],
            "highest_percent":    self.df["Percent"].max(),
            "lowest_percent":     self.df["Percent"].min(),
            "std_deviation":      round(self.df["Percent"].std(), 2),
            "grade_distribution": self.df["Grade"].value_counts().to_dict(),
            "dept_avg":           self.df.groupby("Department")["Percent"].mean().round(2).to_dict(),
        }

    def at_risk_students(self) -> pd.DataFrame:
        return self.df[
            (self.df["Status"] == "FAIL") | (self.df["Backlogs"] >= 2)
        ][["StudentID","Name","Department","Percent","Grade","Status","Backlogs"]]\
         .sort_values("Backlogs", ascending=False)

    def subject_analysis(self) -> pd.DataFrame:
        rows = []
        for subj in self.subject_cols:
            scores = self.df[subj]
            rows.append({
                "Subject":      subj,
                "Average":      round(scores.mean(), 2),
                "Pass Rate":    f"{(scores >= self.cfg.pass_mark).mean()*100:.1f}%",
                "Highest":      scores.max(),
                "Lowest":       scores.min(),
                "Std Dev":      round(scores.std(), 2),
            })
        return pd.DataFrame(rows).sort_values("Average")

    def generate_charts(self, output_dir: str = "charts"):
        Path(output_dir).mkdir(exist_ok=True)

        # 1. Grade Distribution Pie Chart
        fig, ax = plt.subplots(figsize=(8, 6))
        grade_counts = self.df["Grade"].value_counts()
        colors = {"O":"gold","A+":"limegreen","A":"steelblue",
                  "B+":"cornflowerblue","B":"orange","F":"tomato"}
        ax.pie(grade_counts.values, labels=grade_counts.index, autopct='%1.1f%%',
               colors=[colors.get(g,"grey") for g in grade_counts.index],
               startangle=90, pctdistance=0.85)
        ax.set_title(f"Grade Distribution (n={len(self.df)})", fontsize=14, fontweight="bold")
        plt.tight_layout()
        plt.savefig(f"{output_dir}/grade_distribution.png", dpi=150, bbox_inches="tight")
        plt.close()

        # 2. Subject Performance Bar Chart
        subj_df = self.subject_analysis()
        fig, ax = plt.subplots(figsize=(12, 6))
        bars = ax.bar(subj_df["Subject"], subj_df["Average"],
                      color=["tomato" if a < 50 else "steelblue"
                             for a in subj_df["Average"]])
        ax.axhline(y=self.cfg.pass_mark, color='red', linestyle='--',
                   label=f'Pass Mark ({self.cfg.pass_mark})')
        ax.axhline(y=subj_df["Average"].mean(), color='green', linestyle=':',
                   label=f'Class Avg ({subj_df["Average"].mean():.1f})')
        ax.set_xlabel("Subject"); ax.set_ylabel("Average Score")
        ax.set_title("Subject-wise Average Performance"); ax.legend()
        plt.xticks(rotation=30, ha='right')
        for bar, avg in zip(bars, subj_df["Average"]):
            ax.text(bar.get_x() + bar.get_width()/2, bar.get_height() + 0.5,
                    f'{avg:.1f}', ha='center', va='bottom', fontsize=9)
        plt.tight_layout()
        plt.savefig(f"{output_dir}/subject_performance.png", dpi=150, bbox_inches="tight")
        plt.close()

        # 3. Score Distribution Histogram
        fig, ax = plt.subplots(figsize=(10, 5))
        ax.hist(self.df["Percent"], bins=20, edgecolor='black',
                color='steelblue', alpha=0.7)
        ax.axvline(x=self.df["Percent"].mean(), color='red', linestyle='--',
                   label=f'Mean: {self.df["Percent"].mean():.1f}%')
        ax.set_xlabel("Score (%)"); ax.set_ylabel("Number of Students")
        ax.set_title("Score Distribution"); ax.legend()
        plt.tight_layout()
        plt.savefig(f"{output_dir}/score_distribution.png", dpi=150, bbox_inches="tight")
        plt.close()
        print(f"✅ Charts saved to {output_dir}/")

    def export_report(self, output_path: str = "exam_report.xlsx"):
        with pd.ExcelWriter(output_path, engine='openpyxl') as writer:
            self.df.to_excel(writer, sheet_name="All Results", index=False)
            self.at_risk_students().to_excel(writer, sheet_name="At Risk", index=False)
            self.subject_analysis().to_excel(writer, sheet_name="Subject Analysis", index=False)
            stats = self.class_statistics()
            pd.DataFrame([stats]).T.reset_index().rename(
                columns={"index":"Metric", 0:"Value"}).to_excel(
                writer, sheet_name="Summary", index=False)
        print(f"✅ Excel report exported to {output_path}")

# Usage
if __name__ == "__main__":
    analyzer = ExamResultAnalyzer("exam_scores.csv")
    stats = analyzer.class_statistics()
    print(f"Class Average: {stats['class_avg']}%")
    print(f"Pass Rate: {stats['pass_rate']}%")
    print("\nAt-Risk Students:")
    print(analyzer.at_risk_students().to_string(index=False))
    print("\nSubject Analysis:")
    print(analyzer.subject_analysis().to_string(index=False))
    analyzer.generate_charts()
    analyzer.export_report()
```

---

## DAYS 58–62: PROJECT 5 — DevUtils: Your Own PyPI Package

### Real-World Problem
Build and publish a reusable Python utility library that any developer can install with `pip install devutils-yourname`.

```
devutils/
├── devutils/
│   ├── __init__.py
│   ├── strings.py        ← String utilities
│   ├── dates.py          ← Date helpers
│   ├── files.py          ← File operations
│   ├── validators.py     ← Data validation
│   └── retry.py          ← Retry decorator
├── tests/
│   └── test_all.py
├── pyproject.toml         ← Modern packaging standard
├── README.md
└── .github/workflows/
    └── publish.yml        ← Auto-publish to PyPI on tag
```

```toml
# pyproject.toml — modern Python packaging
[build-system]
requires = ["setuptools>=68", "wheel"]
build-backend = "setuptools.backends.legacy:build"

[project]
name = "devutils-yourname"
version = "0.1.0"
description = "Production-grade Python utility library"
readme = "README.md"
license = {text = "MIT"}
requires-python = ">=3.10"
dependencies = []   # zero runtime dependencies

[project.optional-dependencies]
dev = ["pytest", "pytest-cov", "black", "ruff", "mypy"]

[tool.pytest.ini_options]
testpaths = ["tests"]
addopts = "--cov=devutils --cov-report=term-missing"
```

```python
# devutils/retry.py
import time
import functools
from typing import Type, Tuple

def retry(
    max_attempts: int = 3,
    delay: float = 1.0,
    backoff: float = 2.0,
    exceptions: Tuple[Type[Exception], ...] = (Exception,),
):
    """Retry decorator with exponential backoff."""
    def decorator(func):
        @functools.wraps(func)
        def wrapper(*args, **kwargs):
            current_delay = delay
            for attempt in range(1, max_attempts + 1):
                try:
                    return func(*args, **kwargs)
                except exceptions as e:
                    if attempt == max_attempts:
                        raise
                    time.sleep(current_delay)
                    current_delay *= backoff
        return wrapper
    return decorator

# devutils/validators.py
import re
from typing import Any

def is_valid_email(email: str) -> bool:
    pattern = r'^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$'
    return bool(re.match(pattern, str(email)))

def is_valid_phone_in(phone: str) -> bool:
    cleaned = re.sub(r'[\s\-\(\)]', '', str(phone))
    return bool(re.match(r'^(\+91)?[6-9]\d{9}$', cleaned))

def is_valid_pan(pan: str) -> bool:
    return bool(re.match(r'^[A-Z]{5}[0-9]{4}[A-Z]$', str(pan).upper()))

# GitHub Actions: .github/workflows/publish.yml
# name: Publish to PyPI
# on:
#   push:
#     tags: ['v*.*.*']
# jobs:
#   publish:
#     runs-on: ubuntu-latest
#     steps:
#       - uses: actions/checkout@v4
#       - uses: actions/setup-python@v4
#       - run: pip install build twine
#       - run: python -m build
#       - run: twine upload dist/*
#         env:
#           TWINE_USERNAME: __token__
#           TWINE_PASSWORD: ${{ secrets.PYPI_TOKEN }}
```

---

## DAYS 68–75: PROJECT 6 — FastAPI + Celery Background Job Scheduler

### Real-World Problem
Platforms need to run heavy background tasks (report generation, email campaigns, data exports) without blocking API responses — with job status tracking and retry on failure.

```python
# projects/06-job-scheduler/app/main.py
from fastapi import FastAPI, BackgroundTasks, HTTPException
from fastapi.responses import JSONResponse
from celery.result import AsyncResult
from .celery_app import celery_app
from .tasks import generate_report, send_email_campaign, export_data
from pydantic import BaseModel, EmailStr
from typing import Optional
import uuid

app = FastAPI(title="Async Job Scheduler API")

class ReportRequest(BaseModel):
    report_type: str     # "monthly_sales", "inventory", "user_activity"
    params: dict = {}
    notify_email: Optional[EmailStr] = None

class EmailCampaignRequest(BaseModel):
    template_id: str
    recipient_list: list[EmailStr]
    subject: str

@app.post("/jobs/reports", status_code=202)
async def submit_report_job(request: ReportRequest):
    """Submit a report generation job. Returns immediately with job_id."""
    task = generate_report.delay(
        report_type=request.report_type,
        params=request.params,
        notify_email=request.notify_email
    )
    return {"job_id": task.id, "status": "QUEUED",
            "message": "Report generation started. Poll /jobs/{job_id} for status."}

@app.post("/jobs/email-campaign", status_code=202)
async def submit_email_campaign(request: EmailCampaignRequest):
    task = send_email_campaign.delay(
        template_id=request.template_id,
        recipients=request.recipient_list,
        subject=request.subject
    )
    return {"job_id": task.id, "status": "QUEUED", "recipients": len(request.recipient_list)}

@app.get("/jobs/{job_id}")
async def get_job_status(job_id: str):
    """Poll job status."""
    result = AsyncResult(job_id, app=celery_app)
    response = {
        "job_id": job_id,
        "status": result.status,       # PENDING, STARTED, SUCCESS, FAILURE, RETRY
        "created": None,
        "result": None,
        "error": None,
    }
    if result.successful():
        response["result"] = result.get()
    elif result.failed():
        response["error"] = str(result.result)
    return response

@app.delete("/jobs/{job_id}")
async def cancel_job(job_id: str):
    celery_app.control.revoke(job_id, terminate=True)
    return {"job_id": job_id, "status": "CANCELLED"}

# app/celery_app.py
from celery import Celery

celery_app = Celery(
    "job_scheduler",
    broker="redis://localhost:6379/0",
    backend="redis://localhost:6379/1",
    include=["app.tasks"]
)
celery_app.conf.update(
    task_serializer="json",
    result_serializer="json",
    accept_content=["json"],
    task_acks_late=True,               # ACK after task completes (not before)
    worker_prefetch_multiplier=1,      # One task per worker at a time
    task_track_started=True,
    task_time_limit=300,               # Kill task after 5 minutes
    task_soft_time_limit=240,          # Raise exception after 4 minutes (graceful)
    result_expires=86400,              # Results expire after 24 hours
)

# app/tasks.py
from .celery_app import celery_app
from celery import Task
from celery.utils.log import get_task_logger
import time, random

logger = get_task_logger(__name__)

class BaseTask(Task):
    abstract = True
    def on_failure(self, exc, task_id, args, kwargs, einfo):
        logger.error(f"Task {task_id} failed: {exc}")
    def on_retry(self, exc, task_id, args, kwargs, einfo):
        logger.warning(f"Task {task_id} retrying: {exc}")
    def on_success(self, retval, task_id, args, kwargs):
        logger.info(f"Task {task_id} succeeded")

@celery_app.task(base=BaseTask, bind=True, max_retries=3,
                 default_retry_delay=30, name="generate_report")
def generate_report(self, report_type: str, params: dict, notify_email: str = None):
    """Heavy report generation — runs in background worker."""
    logger.info(f"Generating {report_type} report with params: {params}")
    try:
        self.update_state(state="STARTED", meta={"progress": 0, "step": "Fetching data"})
        time.sleep(2)   # Simulate DB query

        self.update_state(state="STARTED", meta={"progress": 40, "step": "Processing"})
        time.sleep(2)   # Simulate data processing

        # Simulate occasional failures for retry demo
        if random.random() < 0.1:
            raise ConnectionError("Database connection lost")

        self.update_state(state="STARTED", meta={"progress": 80, "step": "Generating PDF"})
        time.sleep(1)

        result = {
            "report_type": report_type,
            "file_path": f"/reports/{report_type}_{int(time.time())}.pdf",
            "rows_processed": random.randint(1000, 10000),
            "generation_time_seconds": 5
        }
        if notify_email:
            logger.info(f"Sending report to {notify_email}")
        return result

    except ConnectionError as exc:
        raise self.retry(exc=exc, countdown=30 * (self.request.retries + 1))
```

---

## PHASE 7: DSA IN PYTHON (Days 66–75)

```python
# THE 14 PATTERNS — Python implementations

# PATTERN 1: SLIDING WINDOW
def longest_substring_no_repeat(s: str) -> int:
    seen = {}
    left = max_len = 0
    for right, ch in enumerate(s):
        if ch in seen and seen[ch] >= left:
            left = seen[ch] + 1
        seen[ch] = right
        max_len = max(max_len, right - left + 1)
    return max_len

# PATTERN 2: TWO POINTERS
def three_sum(nums: list) -> list:
    nums.sort()
    result = []
    for i in range(len(nums) - 2):
        if i > 0 and nums[i] == nums[i-1]:
            continue
        left, right = i + 1, len(nums) - 1
        while left < right:
            total = nums[i] + nums[left] + nums[right]
            if total == 0:
                result.append([nums[i], nums[left], nums[right]])
                while left < right and nums[left]  == nums[left+1]:  left += 1
                while left < right and nums[right] == nums[right-1]: right -= 1
                left += 1; right -= 1
            elif total < 0: left += 1
            else:           right -= 1
    return result

# PATTERN 3: BFS
from collections import deque

def level_order(root) -> list:
    if not root: return []
    result, queue = [], deque([root])
    while queue:
        level_size = len(queue)
        level = []
        for _ in range(level_size):
            node = queue.popleft()
            level.append(node.val)
            if node.left:  queue.append(node.left)
            if node.right: queue.append(node.right)
        result.append(level)
    return result

# PATTERN 4: DYNAMIC PROGRAMMING
def longest_common_subsequence(text1: str, text2: str) -> int:
    m, n = len(text1), len(text2)
    dp = [[0] * (n + 1) for _ in range(m + 1)]
    for i in range(1, m + 1):
        for j in range(1, n + 1):
            if text1[i-1] == text2[j-1]:
                dp[i][j] = dp[i-1][j-1] + 1
            else:
                dp[i][j] = max(dp[i-1][j], dp[i][j-1])
    return dp[m][n]

# PATTERN 5: HEAP — Top K Elements
import heapq

def top_k_frequent(nums: list, k: int) -> list:
    from collections import Counter
    freq = Counter(nums)
    return [item for item, _ in freq.most_common(k)]

# Min-heap for k largest:
def k_largest(nums: list, k: int) -> list:
    heap = []
    for n in nums:
        heapq.heappush(heap, n)
        if len(heap) > k:
            heapq.heappop(heap)
    return sorted(heap, reverse=True)
```

---

## 📋 DAILY TIMETABLE

| Day | Phase | Topic | Assignment | Output |
|-----|-------|-------|------------|--------|
| **1** | Core | Execution model, integer cache, `is` vs `==` | Memory benchmark | `day-01.md` |
| **2** | Core | List/Dict/Set internals, collections module | Frequency counter | `day-02.md` |
| **3** | Core | Functions: closures, functools, `lru_cache` | Counter closure | `day-03.md` |
| **4** | Core | Comprehensions, generators, memory comparison | Generator pipeline | `day-04.md` |
| **5** | OOP | Dunder methods, properties, class/static | Vector class | `day-05.md` |
| **6** | OOP | Iterators, generators, `yield from` | Fibonacci generator | `day-06.md` |
| **7** | OOP | Decorators: timer, retry, rate limiter | Decorator stack | `day-07.md` |
| **8–10** | **PROJECT 1** | Smart Expense Tracker CLI | Full CLI app + tests | GitHub + blog |
| **11** | OOP | Inheritance, MRO, ABC | DataProcessor hierarchy | `day-11.md` |
| **12** | OOP | `dataclasses`, `@property`, `__slots__` | Optimised data class | `day-12.md` |
| **13** | OOP | Design Patterns: Singleton, Factory, Observer | Notification system | `day-13.md` |
| **14** | OOP | Protocol, structural subtyping, typing | Fully typed module | `day-14.md` |
| **15** | Advanced | Context managers: class vs `@contextmanager` | DB transaction CM | `day-15.md` |
| **16** | Advanced | `asyncio` fundamentals, coroutines | Concurrent fetcher | `day-16.md` |
| **17** | Advanced | `asyncio.gather`, semaphores, timeouts | Rate-limited fetcher | `day-17.md` |
| **18** | Advanced | `threading`, `multiprocessing`, GIL | CPU vs I/O demo | `day-18.md` |
| **19** | Advanced | `re` regex deep dive | Log parser | `day-19.md` |
| **20** | Advanced | `pathlib`, `os`, `shutil`, `subprocess` | File automation | `day-20.md` |
| **21** | Advanced | `logging` module, structured logs | Logger setup | Blog post |
| **22** | Advanced | `argparse`, `click` — CLI tools | Advanced CLI | `day-22.md` |
| **23** | Automation | `psutil` — system monitoring | Resource watcher | `day-23.md` |
| **24** | Automation | `httpx` async HTTP, `requests` | API client | `day-24.md` |
| **25–28** | **PROJECT 2** | Network Health Monitor | Async monitoring tool | GitHub + demo video |
| **29** | Data | `pandas` — GroupBy, pivot, merge | Sales analysis | `day-29.md` |
| **30** | Data | `matplotlib` + `seaborn` charts | 5 chart types | `day-30.md` |
| **31** | Data | `sqlite3`, `sqlalchemy` ORM | CRUD with ORM | `day-31.md` |
| **32** | Data | `pdfplumber`, `openpyxl`, `python-docx` | Document parser | `day-32.md` |
| **33** | Data | `spaCy` NLP basics | Entity extraction | `day-33.md` |
| **34** | Data | `scikit-learn` basics | Simple classifier | `day-34.md` |
| **35** | Data | Text processing, regex, tokenisation | Text cleaner | `day-35.md` |
| **36** | Data | `smtplib`, email automation | Alert emailer | `day-36.md` |
| **37** | Data | `schedule`, cron-like automation | Scheduled reporter | Blog post |
| **38–42** | **PROJECT 3** | Resume Parser & Job Matcher | PDF parser + scorer | GitHub + demo |
| **43** | FastAPI | FastAPI fundamentals, Pydantic | CRUD endpoints | `day-43.md` |
| **44** | FastAPI | Dependency Injection, middleware | Auth middleware | `day-44.md` |
| **45** | FastAPI | SQLAlchemy + FastAPI integration | ORM + API | `day-45.md` |
| **46** | FastAPI | JWT auth, OAuth2 | Secure endpoints | `day-46.md` |
| **47** | FastAPI | Background tasks, `asyncio` in FastAPI | Async task | `day-47.md` |
| **48–52** | **PROJECT 4** | Exam Result Analyzer | pandas + matplotlib | GitHub + Excel report |
| **53** | Testing | `pytest` — fixtures, parametrise | 20 tests | `day-53.md` |
| **54** | Testing | Mocking with `unittest.mock` | Mock API calls | `day-54.md` |
| **55** | Testing | Coverage report, CI with pytest | 90%+ coverage | Coverage screenshot |
| **56** | DevOps | Docker for Python apps | Multi-stage image | `day-56.md` |
| **57** | DevOps | GitHub Actions — lint, test, build | Pipeline working | Pipeline screenshot |
| **58–62** | **PROJECT 5** | DevUtils PyPI Package | Published package | PyPI page + blog |
| **63** | Performance | `timeit`, `cProfile`, `line_profiler` | Profile report | `day-63.md` |
| **64** | Performance | Memory profiling with `tracemalloc` | Memory report | `day-64.md` |
| **65** | Advanced | `__slots__`, `__weakref__`, `gc` module | Memory optimisation | Blog post |
| **66** | DSA | Arrays + Hashing — 5 problems | Solutions | `dsa/day-66.md` |
| **67** | DSA | Two Pointers + Sliding Window — 5 problems | Solutions | `dsa/day-67.md` |
| **68–75** | **PROJECT 6** | FastAPI + Celery Job Scheduler | Async job system | GitHub + Swagger demo |

---

## 🎯 TOP 25 PYTHON INTERVIEW QUESTIONS

1. **`is` vs `==`?** — `is` compares identity (memory address), `==` compares value.
2. **Why is `[]` as default arg dangerous?** — Default args evaluated once at definition; mutable defaults are shared across calls.
3. **How do generators save memory?** — They produce values lazily on demand instead of storing the entire sequence in RAM.
4. **What is the GIL?** — Global Interpreter Lock prevents multiple Python threads from executing bytecode simultaneously; I/O-bound threads release it.
5. **Difference between `@classmethod` and `@staticmethod`?** — `classmethod` receives `cls`; `staticmethod` receives neither `self` nor `cls`.
6. **What is a decorator?** — A function that takes a function and returns a modified version; used for cross-cutting concerns.
7. **Shallow vs deep copy?** — `copy.copy()` creates new object, shares nested references; `copy.deepcopy()` recursively copies everything.
8. **What is `__slots__`?** — Prevents `__dict__` creation per instance; saves ~50% memory for classes with many instances.
9. **`async def` vs regular `def`?** — `async def` creates a coroutine; must be `await`ed; non-blocking.
10. **What happens during `dict` collision?** — Python uses open addressing; probes next slot using quadratic probing.

---

## ✅ PYTHON MNC READINESS CHECKLIST

| Skill | Evidence Required | Grade |
|---|---|---|
| Core Python Internals | Explain GIL, integer caching, memory model | ✅ |
| Generators + Decorators | Write custom iterator and parameterised decorator | ✅ |
| OOP + Design Patterns | Full class hierarchy with dunders and ABC | ✅ |
| Async/Await | Write concurrent HTTP fetcher | ✅ |
| Data Handling | pandas GroupBy + matplotlib + SQLAlchemy | ✅ |
| FastAPI + Pydantic | Full REST API with auth, validation, tests | ✅ |
| Testing | pytest with fixtures, mocks, 85%+ coverage | ✅ |
| Packaging | Published library on PyPI | ✅ |
| Docker + CI/CD | Dockerfile + GitHub Actions | ✅ |
| DSA in Python | Solve Medium LeetCode in 20 min | ✅ |
| 6 Projects | All on GitHub with README + docs | ✅ |

---

*Python Mastery Roadmap — MNC Production-Grade*  
*Reference: Python Programming MNC Interview Guide*