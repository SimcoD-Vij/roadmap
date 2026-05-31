# 🏗️ The Complete Database & Systems Engineering Roadmap
### From Zero Knowledge → Production-Grade MNC-Level Engineer
**Version:** 2025 | **Duration:** 6 Months (180 Days) | **Stack:** 100% Free & Open Source

---

## 📌 HOW TO USE THIS DOCUMENT

> **READ THIS FIRST.** This roadmap is not a list of tutorials. It is a **construction plan**. Every day builds on the previous day. Every project connects to something real. Every concept is explained **why it exists**, not just **what it is**.
>
> You will learn to think like an engineer — not just follow instructions.

### Your Documentation Strategy (Start Day 1)
| Platform | What You Post | Frequency |
|---|---|---|
| **GitHub** | All code, all config files, all project READMEs | Every day you code |
| **Hashnode / Dev.to** | Concept blogs — "What I learned today about X" | 3x per week |
| **LinkedIn** | Project milestones, architecture diagrams, mini-demos | Weekly |
| **Obsidian (local)** | Personal notes, questions, mistakes, breakthroughs | Daily |

> **Recruiter Mindset:** Recruiters at MNCs don't just read your resume. They Google your name. They look at your GitHub. Your documentation IS your portfolio. A well-documented GitHub repo with clear READMEs, commit history, and working code is worth more than any certification.

---

## 🗺️ PART ONE: THE BIG PICTURE — OVERALL SYSTEM ARCHITECTURE

> **Before you write a single line of code, understand what you are building toward.**
> This architecture diagram represents the final destination. Every stage of this roadmap builds one piece of it.

```
┌─────────────────────────────────────────────────────────────────────┐
│                    MNC-GRADE PRODUCTION SYSTEM                       │
│                  "A Real-Time Analytics Platform"                    │
│                  (Like what Netflix/Uber runs in prod)               │
└─────────────────────────────────────────────────────────────────────┘

                          ┌──────────────────┐
                          │   CLIENT APPS    │
                          │  Web / Mobile    │
                          └────────┬─────────┘
                                   │ HTTPS
                          ┌────────▼─────────┐
                          │   API GATEWAY    │◄── Kong / Nginx
                          │  (Rate Limiting) │
                          └────────┬─────────┘
                                   │
              ┌────────────────────▼─────────────────────┐
              │              MICROSERVICES                │
              │  ┌──────────┐  ┌──────────┐  ┌────────┐ │
              │  │  User    │  │  Order   │  │Search  │ │
              │  │ Service  │  │ Service  │  │Service │ │
              │  └────┬─────┘  └────┬─────┘  └───┬────┘ │
              └───────┼─────────────┼─────────────┼──────┘
                      │             │             │
         ┌────────────▼─────────────▼─────────────▼────────────┐
         │                   MESSAGE BROKER                      │
         │                  Apache Kafka                         │
         │         (The backbone of async communication)        │
         └────────────┬─────────────────────────────────────────┘
                      │
       ┌──────────────▼──────────────┐
       │      DATA LAYER             │
       │                             │
       │  ┌─────────┐  ┌──────────┐ │
       │  │Postgres │  │ Redis    │ │
       │  │(Primary │  │ (Cache + │ │
       │  │  OLTP)  │  │Sessions) │ │
       │  └─────────┘  └──────────┘ │
       │                             │
       │  ┌─────────┐  ┌──────────┐ │
       │  │Cassandra│  │ MinIO    │ │
       │  │(Time-   │  │(Object   │ │
       │  │Series)  │  │Storage)  │ │
       │  └─────────┘  └──────────┘ │
       └──────────────┬──────────────┘
                      │
       ┌──────────────▼──────────────┐
       │      DATA WAREHOUSE (OLAP)  │
       │         ClickHouse          │
       │    (Analytical Queries)     │
       └──────────────┬──────────────┘
                      │
       ┌──────────────▼──────────────┐
       │    OBSERVABILITY STACK      │
       │  Prometheus + Grafana       │
       │  + Loki (Logs) + Jaeger     │
       │       (Tracing)             │
       └──────────────────────────────┘

       ┌───────────────────────────────┐
       │      INFRA / DEVOPS           │
       │  Docker → Docker Compose      │
       │  → Kubernetes (K8s)           │
       │  → Terraform (IaC)            │
       │  → GitHub Actions (CI/CD)     │
       └───────────────────────────────┘
```

### Why This Architecture? (The Reasoning You'll Grow Into)

| Component | Why It Exists | When You'll Build It |
|---|---|---|
| **PostgreSQL** | Battle-tested relational DB, gold standard for OLTP | Week 1 |
| **Redis** | Sub-millisecond in-memory cache; reduces DB load by 90% | Month 2 |
| **Kafka** | Decouples services; handles millions of events/sec | Month 3 |
| **Cassandra** | Write-optimized; perfect for time-series & IoT data | Month 3 |
| **ClickHouse** | Columnar storage; 100x faster than Postgres for analytics | Month 4 |
| **MinIO** | S3-compatible free object storage for files/images | Month 3 |
| **Prometheus+Grafana** | Every production system must be observable | Month 4 |
| **Docker + K8s** | Industry standard for deployment and scaling | Month 5 |

> **Key insight for beginners:** You don't need all of this on Day 1. But knowing where you're going helps you understand *why* you're learning each topic. Every day, you'll see how your work fits into this bigger picture.

---

## 🧱 PART TWO: FOUNDATIONAL PREREQUISITES (Week 0 — Days 1–7)

> **Why this week exists:** You cannot learn databases without understanding the machine they run on. This week saves you from confusion for the rest of the roadmap.

### Day 1: How Computers Work (Hardware Foundation)

**Topics:**
- CPU, RAM, Storage (HDD vs SSD vs NVMe) — physical differences
- What "latency" means at hardware level
- How the OS manages files on disk
- What a filesystem is (ext4, NTFS, APFS)

**Why it matters for databases:**
> A database is, at its core, a program that reads and writes files. The speed difference between RAM (nanoseconds), SSD (microseconds), and HDD (milliseconds) is WHY databases have caches, buffers, and write-ahead logs.

**The Latency Numbers Every Engineer Must Know:**
```
L1 Cache:         0.5 ns
Main Memory:    100   ns
SSD Read:       100   µs  (200,000x slower than L1 cache)
HDD Read:        10   ms  (20,000,000x slower than L1 cache)
Network:        150   ms  (cross-continent)
```

**Practical Task:**
```bash
# Install Ubuntu (or WSL2 on Windows — free)
# Check your hardware
lscpu           # CPU info
free -h         # RAM
df -h           # Disk
lsblk           # Block devices

# Measure your disk speed
sudo apt install hdparm
sudo hdparm -Tt /dev/sda
```

**Documentation Task:**
- Open GitHub, create a new repository called `database-engineering-journey`
- Create a file `week-00/day-01-hardware-notes.md`
- Write: what CPU you have, how much RAM, and 3 things you learned about latency

**Active Recall Questions:**
1. Why is RAM much faster than SSD?
2. If a database reads 8KB from disk, does it read *exactly* 8KB from the physical disk? What actually happens?
3. What does "I/O bound" mean vs "CPU bound"?

---

### Day 2: Linux Command Line Basics

**Topics:**
- File system navigation (ls, cd, pwd, find)
- File operations (cat, less, grep, awk, sed)
- Process management (ps, top, htop, kill)
- Permissions (chmod, chown)
- Package management (apt)
- SSH basics

**Why it matters:**
> Every MNC runs their databases on Linux servers. You will SSH into servers, check logs, restart services, and inspect processes. This is non-negotiable.

**Practical Tasks:**
```bash
# Practice these every day
ls -la /var/log       # Look at system logs
ps aux | grep postgres  # Find running processes
tail -f /var/log/syslog  # Watch live logs
grep -r "error" /var/log/  # Search for errors
df -h && free -h      # Check resources
```

**Mini-Assignment:** Write a bash script that:
1. Checks disk space
2. If disk > 80% full, prints a warning
3. Save it as `check_disk.sh` and put it in your GitHub repo

---

### Day 3: Networking Basics for Databases

**Topics:**
- What IP addresses and ports are
- TCP vs UDP — why databases use TCP
- What localhost (127.0.0.1) means
- Firewalls and ports
- DNS basics
- What a client-server model is

**Why it matters:**
> PostgreSQL runs on port 5432. Redis on 6379. Kafka on 9092. When you connect to a database, you are making a TCP connection to a port. Understanding this prevents hours of debugging "connection refused" errors.

**Practical Tasks:**
```bash
# Install net-tools
sudo apt install net-tools
netstat -tulpn          # What's listening on which port?
ss -tulpn               # Modern version
ping google.com         # Basic connectivity
curl http://example.com # HTTP request
```

---

### Days 4–5: Python Fundamentals

> **Why Python and not another language?** Python is the industry standard for data engineering, scripting, and rapid prototyping. All major databases have excellent Python clients. You will use Python to interact with every database in this roadmap.

**Topics:**
- Variables, data types (int, str, list, dict)
- Control flow (if/else, for loops, while)
- Functions
- File I/O (reading/writing files)
- Error handling (try/except)
- Virtual environments (venv)

**Practical Tasks:**
```python
# Day 4: Write a script that reads a CSV file and prints statistics
import csv

with open('data.csv', 'r') as f:
    reader = csv.DictReader(f)
    rows = list(reader)
    print(f"Total rows: {len(rows)}")
    print(f"Columns: {list(rows[0].keys())}")

# Day 5: Add error handling and write output to a new file
try:
    with open('data.csv', 'r') as f:
        ...
except FileNotFoundError:
    print("Error: file not found")
```

**Documentation Task:**
- Post on Hashnode: "Day 5 of my database journey — What I learned about Python file I/O"
- Keep it simple. 200 words. Include one code snippet. This builds your writing habit.

---

### Days 6–7: Git & GitHub — Your Portfolio Foundation

**Topics:**
- What version control is and why it exists
- `git init`, `add`, `commit`, `push`, `pull`
- Branching (`git branch`, `git checkout`, `git merge`)
- Writing good commit messages
- README.md structure
- `.gitignore` files

**The Golden Rule of Git Commits:**
```
# BAD:
git commit -m "stuff"
git commit -m "fix"

# GOOD:
git commit -m "feat: add PostgreSQL connection pooling with psycopg2"
git commit -m "fix: resolve N+1 query issue in user orders endpoint"
git commit -m "docs: add architecture diagram to README"
```

**Your GitHub README Template:**
```markdown
# Project Name

## What Problem Does This Solve?
[1-2 sentences]

## Architecture
[Diagram or description]

## Tech Stack
- PostgreSQL 15
- Python 3.11
- psycopg2

## How to Run
```bash
git clone ...
pip install -r requirements.txt
python main.py
```

## What I Learned
[Key technical insights]
```

**Week 0 Deliverable:**
- [ ] Ubuntu/WSL2 set up
- [ ] GitHub repo created with proper README
- [ ] Bash script for disk checking committed
- [ ] First Hashnode post published

---

## 🗄️ PART THREE: DATABASES PHASE 1 — RELATIONAL FUNDAMENTALS (Weeks 1–4)

### 🔍 WHAT YOU ARE BUILDING IN THIS PHASE

> **Context:** In the final architecture, PostgreSQL is the heart of the OLTP (Online Transaction Processing) system. This phase builds that heart. You will go from "what is a database" to building a production-style e-commerce database schema, complete with indexes, transactions, and query optimization.

---

## WEEK 1: How Databases Actually Work Inside

### Day 8: Installing PostgreSQL & Understanding the RDBMS Architecture

**Topics & Subtopics:**

**1. What is a Database Management System (DBMS)?**
- A DBMS is software that manages data on your behalf
- It handles: storage, retrieval, concurrency, crash recovery, and security
- Without a DBMS, you'd need to manage files manually — and that breaks instantly under concurrent access

**2. RDBMS Architecture Components:**
```
SQL Query (your input)
      │
      ▼
┌─────────────┐
│   PARSER    │  Checks syntax, converts to AST (Abstract Syntax Tree)
└──────┬──────┘
       │
┌──────▼──────┐
│  REWRITER   │  Expands views, applies rules
└──────┬──────┘
       │
┌──────▼──────┐
│  OPTIMIZER  │  Chooses the CHEAPEST execution plan (this is the "brain")
└──────┬──────┘
       │
┌──────▼──────┐
│  EXECUTOR   │  Actually runs the plan, fetches data from storage
└──────┬──────┘
       │
┌──────▼──────┐
│STORAGE MGR  │  Reads/writes pages from disk
└─────────────┘
```

**3. Installing PostgreSQL:**
```bash
sudo apt update
sudo apt install postgresql postgresql-contrib
sudo systemctl start postgresql
sudo systemctl enable postgresql
sudo -u postgres psql    # Enter PostgreSQL shell

# Inside psql:
\l                        # List databases
CREATE DATABASE mydb;
\c mydb                   # Connect to database
\dt                       # List tables
\q                        # Quit
```

**4. psql Essential Commands:**
```sql
-- Create a test table
CREATE TABLE users (
    id SERIAL PRIMARY KEY,
    name VARCHAR(100) NOT NULL,
    email VARCHAR(255) UNIQUE NOT NULL,
    created_at TIMESTAMP DEFAULT NOW()
);

-- Insert data
INSERT INTO users (name, email) VALUES ('Alice', 'alice@example.com');

-- Query data
SELECT * FROM users;
SELECT name, email FROM users WHERE id = 1;
```

**Practical Task — Understanding Query Lifecycle:**
```bash
# Monitor PostgreSQL internals
sudo -u postgres psql -c "SELECT * FROM pg_stat_activity;"
# This shows all active connections and what queries they're running
```

**Documentation Task:**
- GitHub commit: `feat: PostgreSQL installation and first schema`
- Blog post draft: "What actually happens when you run SELECT * FROM users?"

**Active Recall Questions:**
1. What is the difference between a DBMS and a filesystem?
2. What does the Query Optimizer actually optimize for?
3. Why does PostgreSQL need a "Parser" step before execution?

---

### Day 9: Pages, Blocks, and How Data Lives on Disk

**This is the most important concept most beginners never learn.**

**Topics:**
- The concept of a "page" (PostgreSQL default: 8KB)
- How rows (tuples) are packed into pages
- The Slotted Page design
- Random I/O vs Sequential I/O
- Why this matters for query speed

**The Page Structure:**
```
┌─────────────────────────────────────────────┐
│              8KB PAGE                        │
│                                              │
│  [Header][Slot1][Slot2][Slot3]...[Free]      │
│           ↑     ↑     ↑                      │
│           │     │     │                      │
│         [Row3][Row2][Row1]   ← rows grow     │
│                                  from bottom │
└─────────────────────────────────────────────┘
```

**Why This Matters:**
> When you do `SELECT * FROM orders WHERE id = 12345`, PostgreSQL doesn't magically teleport to that row. It must read whole pages from disk. If that row is in page 5000, it reads page 5000 (8KB) into memory. This is why **indexes exist** — they help find which page contains your data without reading all pages.

**Practical Task:**
```sql
-- See PostgreSQL's page structure with pageinspect extension
CREATE EXTENSION pageinspect;

CREATE TABLE test_pages (id INT, data TEXT);
INSERT INTO test_pages SELECT i, 'row_' || i FROM generate_series(1, 100) i;

-- Inspect the first page (page 0)
SELECT * FROM heap_page_items(get_raw_page('test_pages', 0));
-- You'll see the actual slot offsets and tuple data
```

**Active Recall Questions:**
1. If a row is 100 bytes and a page is 8192 bytes, how many rows fit in one page?
2. Why is sequential I/O faster than random I/O on HDDs?
3. What happens when you delete a row? Does PostgreSQL immediately free that space?

---

### Days 10–11: SQL Fundamentals — The Language of Data

**Topics & Subtopics:**

**DDL (Data Definition Language) — Structure:**
```sql
-- Creating tables with proper data types
CREATE TABLE products (
    id          SERIAL PRIMARY KEY,
    name        VARCHAR(255) NOT NULL,
    price       NUMERIC(10, 2) NOT NULL CHECK (price > 0),
    category    VARCHAR(100),
    stock       INTEGER DEFAULT 0,
    created_at  TIMESTAMP WITH TIME ZONE DEFAULT NOW(),
    updated_at  TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);

-- Altering tables (common in real projects)
ALTER TABLE products ADD COLUMN description TEXT;
ALTER TABLE products ALTER COLUMN name SET NOT NULL;

-- Creating relationships
CREATE TABLE orders (
    id          SERIAL PRIMARY KEY,
    user_id     INTEGER REFERENCES users(id) ON DELETE RESTRICT,
    total       NUMERIC(10, 2),
    status      VARCHAR(50) DEFAULT 'pending',
    created_at  TIMESTAMP WITH TIME ZONE DEFAULT NOW()
);
```

**DML (Data Manipulation Language) — Data:**
```sql
-- Insert
INSERT INTO products (name, price, category, stock)
VALUES ('MacBook Pro', 1299.99, 'Electronics', 50);

-- Bulk insert (much faster than one at a time)
INSERT INTO products (name, price, category) VALUES
    ('iPhone 15', 799.99, 'Electronics'),
    ('AirPods', 199.99, 'Electronics'),
    ('iPad', 499.99, 'Electronics');

-- Update
UPDATE products SET stock = stock - 1 WHERE id = 1;

-- Delete (be careful — always use WHERE)
DELETE FROM products WHERE stock = 0;

-- RETURNING clause (PostgreSQL feature — very useful)
INSERT INTO users (name, email) VALUES ('Bob', 'bob@example.com')
RETURNING id, created_at;
```

**DQL (Data Query Language) — Retrieval:**
```sql
-- Basic SELECT with filtering
SELECT name, price, stock
FROM products
WHERE category = 'Electronics' AND price < 1000
ORDER BY price DESC
LIMIT 10;

-- Aggregation
SELECT
    category,
    COUNT(*) as product_count,
    AVG(price) as avg_price,
    SUM(stock) as total_stock
FROM products
GROUP BY category
HAVING COUNT(*) > 5
ORDER BY avg_price DESC;

-- JOINs (the most important SQL concept)
-- INNER JOIN: only rows that match in BOTH tables
SELECT u.name, o.id as order_id, o.total
FROM users u
INNER JOIN orders o ON u.id = o.user_id;

-- LEFT JOIN: all rows from left table, matched rows from right
SELECT u.name, COUNT(o.id) as order_count
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
GROUP BY u.id, u.name;
```

---

### Days 12–13: Advanced SQL — Window Functions & CTEs

**Why these matter at MNCs:**
> Basic SQL gets you an internship. Window functions and CTEs get you a senior role. These are used daily at companies like Netflix, Uber, and Amazon for analytics.

**Window Functions:**
```sql
-- RANK() — find top products per category
SELECT
    name,
    category,
    price,
    RANK() OVER (PARTITION BY category ORDER BY price DESC) as price_rank
FROM products;

-- LAG() — compare to previous row (very common in time-series)
SELECT
    DATE(created_at) as date,
    COUNT(*) as daily_orders,
    LAG(COUNT(*)) OVER (ORDER BY DATE(created_at)) as prev_day_orders,
    COUNT(*) - LAG(COUNT(*)) OVER (ORDER BY DATE(created_at)) as growth
FROM orders
GROUP BY DATE(created_at)
ORDER BY date;

-- RUNNING TOTAL — cumulative sum
SELECT
    created_at,
    total,
    SUM(total) OVER (ORDER BY created_at) as running_revenue
FROM orders;
```

**Common Table Expressions (CTEs):**
```sql
-- CTEs make complex queries readable
WITH
monthly_revenue AS (
    SELECT
        DATE_TRUNC('month', created_at) as month,
        SUM(total) as revenue
    FROM orders
    WHERE status = 'completed'
    GROUP BY 1
),
ranked_months AS (
    SELECT
        month,
        revenue,
        RANK() OVER (ORDER BY revenue DESC) as rank
    FROM monthly_revenue
)
SELECT * FROM ranked_months WHERE rank <= 3;
-- "Give me the top 3 revenue months"
```

---

### Day 14: Mini-Project #1 — E-Commerce Schema

**🏗️ PROJECT: Build a Production-Ready E-Commerce Database**

**Real-World Problem:** An online store needs a database that handles products, users, orders, and inventory. It must be normalized, have proper constraints, and support common business queries.

**Schema Design:**
```sql
-- File: projects/ecommerce/schema.sql

-- Users
CREATE TABLE users (
    id          BIGSERIAL PRIMARY KEY,
    email       VARCHAR(255) UNIQUE NOT NULL,
    password_hash VARCHAR(255) NOT NULL,
    name        VARCHAR(255) NOT NULL,
    phone       VARCHAR(20),
    is_active   BOOLEAN DEFAULT TRUE,
    created_at  TIMESTAMPTZ DEFAULT NOW()
);

-- Address (separate from users — one user can have many addresses)
CREATE TABLE addresses (
    id          BIGSERIAL PRIMARY KEY,
    user_id     BIGINT REFERENCES users(id) ON DELETE CASCADE,
    street      TEXT NOT NULL,
    city        VARCHAR(100) NOT NULL,
    country     VARCHAR(100) NOT NULL,
    is_default  BOOLEAN DEFAULT FALSE
);

-- Product catalog
CREATE TABLE categories (
    id      BIGSERIAL PRIMARY KEY,
    name    VARCHAR(100) UNIQUE NOT NULL,
    parent_id BIGINT REFERENCES categories(id)  -- supports nested categories
);

CREATE TABLE products (
    id          BIGSERIAL PRIMARY KEY,
    category_id BIGINT REFERENCES categories(id),
    name        VARCHAR(255) NOT NULL,
    description TEXT,
    price       NUMERIC(12, 2) NOT NULL CHECK (price >= 0),
    sku         VARCHAR(100) UNIQUE NOT NULL,
    is_active   BOOLEAN DEFAULT TRUE,
    created_at  TIMESTAMPTZ DEFAULT NOW()
);

CREATE TABLE inventory (
    product_id  BIGINT PRIMARY KEY REFERENCES products(id),
    quantity    INTEGER NOT NULL CHECK (quantity >= 0),
    reserved    INTEGER NOT NULL DEFAULT 0,
    updated_at  TIMESTAMPTZ DEFAULT NOW()
);

-- Orders
CREATE TABLE orders (
    id          BIGSERIAL PRIMARY KEY,
    user_id     BIGINT REFERENCES users(id),
    address_id  BIGINT REFERENCES addresses(id),
    status      VARCHAR(50) NOT NULL DEFAULT 'pending'
                CHECK (status IN ('pending','confirmed','shipped','delivered','cancelled')),
    total_amount NUMERIC(12, 2) NOT NULL,
    created_at  TIMESTAMPTZ DEFAULT NOW(),
    updated_at  TIMESTAMPTZ DEFAULT NOW()
);

CREATE TABLE order_items (
    id          BIGSERIAL PRIMARY KEY,
    order_id    BIGINT REFERENCES orders(id) ON DELETE CASCADE,
    product_id  BIGINT REFERENCES products(id),
    quantity    INTEGER NOT NULL CHECK (quantity > 0),
    unit_price  NUMERIC(12, 2) NOT NULL,  -- store price AT TIME OF PURCHASE
    UNIQUE(order_id, product_id)
);
```

**Business Queries to Implement:**
```sql
-- 1. Top 10 best-selling products this month
SELECT
    p.name,
    SUM(oi.quantity) as units_sold,
    SUM(oi.quantity * oi.unit_price) as revenue
FROM order_items oi
JOIN products p ON oi.product_id = p.id
JOIN orders o ON oi.order_id = o.id
WHERE
    o.status = 'delivered'
    AND o.created_at >= DATE_TRUNC('month', NOW())
GROUP BY p.id, p.name
ORDER BY revenue DESC
LIMIT 10;

-- 2. Users who have spent > $1000 lifetime
SELECT
    u.name,
    u.email,
    COUNT(o.id) as order_count,
    SUM(o.total_amount) as lifetime_value
FROM users u
JOIN orders o ON u.id = o.user_id
WHERE o.status = 'delivered'
GROUP BY u.id, u.name, u.email
HAVING SUM(o.total_amount) > 1000
ORDER BY lifetime_value DESC;

-- 3. Products low on stock (< 10 units)
SELECT p.name, i.quantity, i.reserved,
       (i.quantity - i.reserved) as available
FROM inventory i
JOIN products p ON i.product_id = p.id
WHERE (i.quantity - i.reserved) < 10
ORDER BY available ASC;
```

**GitHub Deliverable:**
```
projects/ecommerce/
├── README.md        (what the project is, schema diagram)
├── schema.sql       (all CREATE TABLE statements)
├── seed.sql         (INSERT sample data)
├── queries.sql      (all business queries with comments)
└── ARCHITECTURE.md  (explain your design decisions)
```

**Blog Post:** "Why I stored unit_price in order_items instead of joining to products" — This is a real design decision that shows engineering thinking.

---

## WEEK 2: Indexes and Query Performance

### Day 15: How Indexes Work — The B+ Tree

**The Single Most Important Performance Topic**

**Why indexes exist:**
> Without an index, finding `WHERE user_id = 1234` in a 10-million-row table requires reading ALL 10 million rows. With an index, PostgreSQL jumps directly to the rows for user_id 1234. This is the difference between a 10-second query and a 0.001-second query.

**B+ Tree Structure:**
```
                    [30 | 60]          ← Root Node (Internal)
                   /    |    \
            [10|20]  [40|50]  [70|80]  ← Internal Nodes
           /  |  \     ...      ...
        [5] [15] [25]              ← Leaf Nodes (actual row pointers)
         ↕    ↕    ↕              ← Leaf nodes are LINKED
```

**Key properties:**
1. Leaf nodes contain pointers to actual rows (heap file pointers)
2. Leaf nodes are linked — enables efficient range scans
3. Tree stays balanced — always O(log N) lookups
4. Every write to the table updates the B+ tree = write amplification

**Creating and Using Indexes:**
```sql
-- Single-column index
CREATE INDEX idx_orders_user_id ON orders(user_id);

-- Composite index (order matters!)
CREATE INDEX idx_orders_user_status ON orders(user_id, status);
-- This helps: WHERE user_id = 1 AND status = 'pending'
-- This helps: WHERE user_id = 1
-- This does NOT help: WHERE status = 'pending' (alone)

-- Partial index (only index a subset of rows — very efficient)
CREATE INDEX idx_active_users ON users(email) WHERE is_active = TRUE;

-- Unique index (also enforces constraint)
CREATE UNIQUE INDEX idx_unique_email ON users(email);

-- See all indexes on a table
\d orders

-- EXPLAIN: See if your index is being used
EXPLAIN ANALYZE
SELECT * FROM orders WHERE user_id = 1000;
-- Look for "Index Scan" vs "Seq Scan"
```

**The EXPLAIN ANALYZE Output — How to Read It:**
```
Index Scan using idx_orders_user_id on orders
  (cost=0.43..8.45 rows=1 width=96)
  (actual time=0.021..0.022 rows=1 loops=1)
  Index Cond: (user_id = 1000)
Planning Time: 0.5 ms
Execution Time: 0.1 ms
```
- `cost=X..Y` — estimated cost (X=startup, Y=total)
- `rows=N` — estimated rows to be returned
- `actual time=X..Y` — real execution time
- "Seq Scan" = full table scan = BAD (for large tables)
- "Index Scan" = using index = GOOD

**Practical Experiment:**
```sql
-- Create a test table with 1 million rows
CREATE TABLE perf_test AS
SELECT
    i as id,
    (random() * 1000000)::int as user_id,
    NOW() - (random() * interval '365 days') as created_at
FROM generate_series(1, 1000000) i;

-- Query WITHOUT index
\timing on
EXPLAIN ANALYZE SELECT * FROM perf_test WHERE user_id = 42;

-- Create index
CREATE INDEX idx_perf_user_id ON perf_test(user_id);

-- Query WITH index — compare the time
EXPLAIN ANALYZE SELECT * FROM perf_test WHERE user_id = 42;
```

**Assignment:**
1. Measure and document: query time with no index, 1 index, 3 indexes on same table
2. Try inserting 10,000 rows into the table and measure insert time WITH vs WITHOUT indexes
3. Document your findings: this is the **write amplification** concept in action

---

### Days 16–17: Transactions and ACID Guarantees

**Why this is critical:**
> Every time a user places an order, multiple things must happen atomically: reduce inventory, create order, charge payment. If any step fails halfway, the database must roll back everything. Without transactions, you get corrupted data — products sold without payment, money charged without orders.

**ACID Explained with Real Examples:**

**Atomicity — All or Nothing:**
```sql
BEGIN;
    UPDATE inventory SET quantity = quantity - 1 WHERE product_id = 42;
    INSERT INTO orders (user_id, total_amount) VALUES (1, 99.99);
    INSERT INTO order_items (order_id, product_id, quantity, unit_price)
        VALUES (currval('orders_id_seq'), 42, 1, 99.99);
COMMIT;
-- If ANY of these fail, ALL changes are rolled back
-- The inventory is NOT decremented without a successful order
```

**Isolation — Concurrent Transactions Don't See Each Other's Partial Work:**
```sql
-- Session 1:
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
-- ... (not yet committed)

-- Session 2 (in another psql window):
SELECT balance FROM accounts WHERE id = 1;
-- With READ COMMITTED (default), Session 2 sees the OLD balance
-- It cannot see Session 1's uncommitted change
```

**The Four Isolation Levels:**
| Level | Dirty Read | Non-Repeatable Read | Phantom Read |
|---|---|---|---|
| READ UNCOMMITTED | ✓ Possible | ✓ | ✓ |
| READ COMMITTED | ✗ Protected | ✓ Possible | ✓ |
| REPEATABLE READ | ✗ | ✗ Protected | ✓ Possible |
| SERIALIZABLE | ✗ | ✗ | ✗ Protected |

**Practical Lab — Reproduce a Dirty Read:**
```sql
-- This lab requires TWO terminal windows open with psql

-- === Terminal 1 ===
BEGIN;
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
UPDATE accounts SET balance = 1000000 WHERE id = 1;
-- DO NOT COMMIT YET

-- === Terminal 2 === (at the same time)
SET TRANSACTION ISOLATION LEVEL READ UNCOMMITTED;
SELECT balance FROM accounts WHERE id = 1;
-- You see 1000000! But Terminal 1 hasn't committed!
-- This is a Dirty Read — reading uncommitted data

-- === Terminal 1 ===
ROLLBACK;
-- Now Terminal 2 reads again — the million dollars is gone
-- This is why READ UNCOMMITTED is dangerous
```

---

### Days 18–19: The Write-Ahead Log (WAL) — Durability Explained

**The Most Important File in Your Database**

**What is the WAL:**
> The WAL is PostgreSQL's "black box recorder". Before any change is made to a data page, PostgreSQL first writes the change to the WAL (an append-only log file). If the database crashes, it replays the WAL to recover. This is how ACID's "Durability" is implemented.

**WAL Write Process:**
```
Your UPDATE query
       │
       ▼
1. Write change to WAL buffer (in memory)
       │
       ▼
2. fsync() — force WAL buffer to disk (this is the durability guarantee)
       │
       ▼
3. Update the actual data page (in buffer pool)
       │
       ▼
4. Eventually, checkpoint writes dirty pages to disk
```

**Viewing WAL Activity:**
```bash
# See WAL files
ls -la /var/lib/postgresql/*/main/pg_wal/

# See WAL position
sudo -u postgres psql -c "SELECT pg_current_wal_lsn();"
```

**Assignment — Simulate a Crash:**
```bash
# 1. Start a transaction but don't commit
# 2. Kill PostgreSQL forcefully: sudo kill -9 $(pgrep postgres)
# 3. Restart PostgreSQL: sudo systemctl start postgresql
# 4. Observe: PostgreSQL automatically replays the WAL and recovers!
# 5. The committed transactions are there. The uncommitted one is gone.
# Document what you observe in your GitHub repo.
```

---

### Days 20–21: Mini-Project #2 — Banking Transaction System

**🏗️ PROJECT: Safe Money Transfer System**

**Real-World Problem:** Banks need to transfer money between accounts with zero data loss. A crash during transfer must leave the database in a consistent state.

```sql
-- schema
CREATE TABLE accounts (
    id          BIGSERIAL PRIMARY KEY,
    owner_name  VARCHAR(255) NOT NULL,
    balance     NUMERIC(15, 2) NOT NULL DEFAULT 0
                CHECK (balance >= 0),   -- Can't go negative!
    currency    VARCHAR(3) NOT NULL DEFAULT 'USD',
    created_at  TIMESTAMPTZ DEFAULT NOW()
);

CREATE TABLE transactions (
    id              BIGSERIAL PRIMARY KEY,
    from_account_id BIGINT REFERENCES accounts(id),
    to_account_id   BIGINT REFERENCES accounts(id),
    amount          NUMERIC(15, 2) NOT NULL CHECK (amount > 0),
    status          VARCHAR(20) NOT NULL DEFAULT 'pending',
    description     TEXT,
    created_at      TIMESTAMPTZ DEFAULT NOW()
);

-- The transfer function (this is how real banks do it)
CREATE OR REPLACE FUNCTION transfer_money(
    p_from BIGINT,
    p_to   BIGINT,
    p_amount NUMERIC
) RETURNS BIGINT AS $$
DECLARE
    v_txn_id BIGINT;
BEGIN
    -- Lock both accounts to prevent concurrent transfers
    -- Always lock in consistent order (lower ID first) to prevent deadlocks
    PERFORM 1 FROM accounts WHERE id = LEAST(p_from, p_to) FOR UPDATE;
    PERFORM 1 FROM accounts WHERE id = GREATEST(p_from, p_to) FOR UPDATE;

    -- Debit
    UPDATE accounts SET balance = balance - p_amount WHERE id = p_from;
    -- Credit
    UPDATE accounts SET balance = balance + p_amount WHERE id = p_to;
    -- Record
    INSERT INTO transactions (from_account_id, to_account_id, amount, status)
    VALUES (p_from, p_to, p_amount, 'completed')
    RETURNING id INTO v_txn_id;

    RETURN v_txn_id;
END;
$$ LANGUAGE plpgsql;
```

**Python Integration:**
```python
# transfer.py
import psycopg2
from psycopg2 import sql

conn = psycopg2.connect("dbname=banking user=postgres")

def safe_transfer(from_id, to_id, amount):
    try:
        with conn.cursor() as cur:
            cur.execute("SELECT transfer_money(%s, %s, %s)",
                       (from_id, to_id, amount))
            txn_id = cur.fetchone()[0]
        conn.commit()
        print(f"Transfer successful. Transaction ID: {txn_id}")
        return txn_id
    except psycopg2.Error as e:
        conn.rollback()
        print(f"Transfer failed: {e}")
        return None

# Test it
safe_transfer(1, 2, 50.00)
```

**GitHub Deliverable:**
```
projects/banking/
├── README.md         (problem, solution, architecture decisions)
├── schema.sql
├── transfer.py
├── tests/
│   ├── test_concurrent_transfers.py
│   └── test_crash_recovery.py
└── LEARNINGS.md      (what you discovered about transactions)
```

---

## WEEK 3: Normalization, Modeling & Performance

### Days 22–23: Database Normalization — Data Integrity by Design

**Why normalization matters:**
> Normalization removes redundancy. Redundancy causes update anomalies — if the same data is stored in two places, you can update one and forget the other, creating inconsistency. At MNC scale, this causes real data bugs worth millions of dollars.

**Normal Forms Explained with Examples:**

**1NF — First Normal Form:**
```
❌ BAD (not 1NF):
┌────────┬─────────────┬─────────────────────────┐
│ UserID │ Name        │ PhoneNumbers            │
├────────┼─────────────┼─────────────────────────┤
│   1    │ Alice       │ 555-1234, 555-5678      │ ← multiple values in one cell
└────────┴─────────────┴─────────────────────────┘

✅ GOOD (1NF):
┌────────┬─────────────┬─────────────┐
│ UserID │ Name        │ Phone       │
├────────┼─────────────┼─────────────┤
│   1    │ Alice       │ 555-1234    │
│   1    │ Alice       │ 555-5678    │
└────────┴─────────────┴─────────────┘
Rule: Each column must contain atomic (single) values.
```

**2NF — Second Normal Form:**
```
❌ BAD (not 2NF):
┌─────────┬────────────┬─────────────┬──────────────┐
│ OrderID │ ProductID  │ Quantity    │ ProductName  │
├─────────┼────────────┼─────────────┼──────────────┤
│  1001   │   42       │   2         │ iPhone 15    │ ← ProductName depends only on ProductID
│  1002   │   42       │   1         │ iPhone 15    │   not on the full (OrderID, ProductID) key
└─────────┴────────────┴─────────────┴──────────────┘

✅ GOOD (2NF):
Order_Items: (OrderID, ProductID, Quantity)
Products:    (ProductID, ProductName)
```

**3NF — Third Normal Form:**
```
❌ BAD (not 3NF):
┌─────────┬────────────┬──────────────┬────────────────┐
│ OrderID │ CustomerID │ CustomerName │ CustomerCity   │
└─────────┴────────────┴──────────────┴────────────────┘
CustomerName and CustomerCity depend on CustomerID, not on OrderID.

✅ GOOD (3NF):
Orders:    (OrderID, CustomerID)
Customers: (CustomerID, CustomerName, CustomerCity)
```

**Practical Assignment:**
1. Take this denormalized CSV: `order_id, product_name, product_price, customer_name, customer_email, customer_city, quantity`
2. Normalize it to 3NF
3. Draw the Entity-Relationship (ER) diagram (use draw.io — free)
4. Implement it in PostgreSQL
5. Document your design decisions

---

### Days 24–25: Query Optimization Masterclass

**How to Find Slow Queries:**
```sql
-- Enable query timing
\timing on

-- pg_stat_statements — tracks all queries (needs extension)
CREATE EXTENSION pg_stat_statements;

SELECT
    query,
    calls,
    total_exec_time / calls as avg_ms,
    rows / calls as avg_rows
FROM pg_stat_statements
ORDER BY avg_ms DESC
LIMIT 10;
-- Shows you the TOP 10 SLOWEST queries in your application
```

**Common Performance Anti-Patterns:**
```sql
-- ❌ N+1 Query Problem (kills production systems)
-- This runs 1 + N queries (1 for users, N for each user's orders)
SELECT * FROM users;  -- returns 1000 users
-- Then in your code: for each user, run:
SELECT * FROM orders WHERE user_id = ?;  -- runs 1000 times!

-- ✅ Fix: Use JOIN (runs 1 query)
SELECT u.name, COUNT(o.id) as order_count
FROM users u
LEFT JOIN orders o ON u.id = o.user_id
GROUP BY u.id, u.name;

-- ❌ SELECT * in production (transfers unnecessary data)
SELECT * FROM orders;  -- pulls ALL columns including large TEXT fields

-- ✅ Fix: Select only what you need
SELECT id, user_id, total_amount, status FROM orders;

-- ❌ Leading wildcard (can't use index)
SELECT * FROM users WHERE email LIKE '%@gmail.com';

-- ✅ Fix: Use full-text search or trigram indexes for this use case
CREATE EXTENSION pg_trgm;
CREATE INDEX idx_email_trgm ON users USING gin(email gin_trgm_ops);
```

---

### Days 26–28: Mini-Project #3 — Library Management System

**🏗️ PROJECT: Full Library Database with Advanced Queries**

**Real-World Problem:** A library needs to manage books, members, loans, reservations, and fines. This tests your ability to design a complete normalized schema and write complex business queries.

**Schema:**
```sql
CREATE TABLE books (
    id          BIGSERIAL PRIMARY KEY,
    isbn        VARCHAR(13) UNIQUE NOT NULL,
    title       VARCHAR(500) NOT NULL,
    author      VARCHAR(255) NOT NULL,
    genre       VARCHAR(100),
    total_copies INTEGER NOT NULL DEFAULT 1,
    available_copies INTEGER NOT NULL DEFAULT 1
);

CREATE TABLE members (
    id          BIGSERIAL PRIMARY KEY,
    name        VARCHAR(255) NOT NULL,
    email       VARCHAR(255) UNIQUE NOT NULL,
    membership_type VARCHAR(20) DEFAULT 'standard',
    joined_at   TIMESTAMPTZ DEFAULT NOW(),
    expires_at  TIMESTAMPTZ NOT NULL
);

CREATE TABLE loans (
    id          BIGSERIAL PRIMARY KEY,
    book_id     BIGINT REFERENCES books(id),
    member_id   BIGINT REFERENCES members(id),
    loaned_at   TIMESTAMPTZ DEFAULT NOW(),
    due_date    TIMESTAMPTZ NOT NULL,
    returned_at TIMESTAMPTZ,
    CONSTRAINT no_double_loan UNIQUE (book_id, member_id, loaned_at)
);

CREATE TABLE fines (
    id          BIGSERIAL PRIMARY KEY,
    loan_id     BIGINT REFERENCES loans(id),
    amount      NUMERIC(8,2) NOT NULL,
    reason      TEXT,
    paid        BOOLEAN DEFAULT FALSE,
    created_at  TIMESTAMPTZ DEFAULT NOW()
);
```

**Complex Business Queries to Write:**
1. Members with overdue books right now
2. Books with the highest loan rate over the past 6 months
3. Calculate fines for all overdue books (10 cents/day)
4. Members who have never borrowed a book (marketing opportunity)
5. Average days a book is kept before return by genre

---

## WEEK 4: PostgreSQL Advanced Features

### Days 29–30: Views, Materialized Views, and Stored Procedures

**Views:**
```sql
-- A view is a saved query — not stored data
CREATE VIEW active_loans AS
SELECT
    l.id,
    m.name as member_name,
    b.title as book_title,
    l.due_date,
    NOW() > l.due_date as is_overdue
FROM loans l
JOIN members m ON l.member_id = m.id
JOIN books b ON l.book_id = b.id
WHERE l.returned_at IS NULL;

-- Now query it like a table
SELECT * FROM active_loans WHERE is_overdue = TRUE;
```

**Materialized Views (for performance):**
```sql
-- A materialized view STORES the result — great for expensive analytics
CREATE MATERIALIZED VIEW monthly_revenue_summary AS
SELECT
    DATE_TRUNC('month', created_at) as month,
    COUNT(*) as order_count,
    SUM(total_amount) as revenue
FROM orders
WHERE status = 'delivered'
GROUP BY 1;

-- Refresh when data changes (schedule this with pg_cron)
REFRESH MATERIALIZED VIEW CONCURRENTLY monthly_revenue_summary;

-- Query is now instant (reads from stored result)
SELECT * FROM monthly_revenue_summary ORDER BY month DESC;
```

---

### Days 31–33: PostgreSQL with Python (psycopg2 + SQLAlchemy)

**psycopg2 (low-level, direct control):**
```python
# database.py
import psycopg2
from psycopg2.extras import RealDictCursor
from contextlib import contextmanager

DATABASE_URL = "dbname=ecommerce user=postgres password=secret host=localhost"

@contextmanager
def get_db():
    conn = psycopg2.connect(DATABASE_URL)
    try:
        yield conn
        conn.commit()
    except Exception:
        conn.rollback()
        raise
    finally:
        conn.close()

def get_user_orders(user_id: int):
    with get_db() as conn:
        with conn.cursor(cursor_factory=RealDictCursor) as cur:
            cur.execute("""
                SELECT o.id, o.total_amount, o.status, o.created_at
                FROM orders o
                WHERE o.user_id = %s
                ORDER BY o.created_at DESC
                LIMIT 50
            """, (user_id,))  # Note: always use parameterized queries! Never format strings!
            return cur.fetchall()
```

**SQLAlchemy (ORM — industry standard):**
```python
# models.py
from sqlalchemy import create_engine, Column, Integer, String, Numeric, ForeignKey
from sqlalchemy.orm import DeclarativeBase, Session, relationship
from sqlalchemy.orm import sessionmaker

engine = create_engine("postgresql+psycopg2://postgres:secret@localhost/ecommerce")

class Base(DeclarativeBase):
    pass

class User(Base):
    __tablename__ = "users"
    id = Column(Integer, primary_key=True)
    name = Column(String(255), nullable=False)
    email = Column(String(255), unique=True, nullable=False)
    orders = relationship("Order", back_populates="user")

class Order(Base):
    __tablename__ = "orders"
    id = Column(Integer, primary_key=True)
    user_id = Column(Integer, ForeignKey("users.id"))
    total_amount = Column(Numeric(12, 2))
    status = Column(String(50))
    user = relationship("User", back_populates="orders")

# Using it
with Session(engine) as session:
    user = session.get(User, 1)
    print(user.orders)  # Automatically fetches related orders
```

---

### Days 34–35: Phase 1 Capstone — Production-Grade Inventory API

**🏗️ CAPSTONE PROJECT: Inventory Management REST API**

**Tech Stack:**
- PostgreSQL 15
- Python + FastAPI
- psycopg2
- Docker

**Project Structure:**
```
projects/inventory-api/
├── README.md
├── docker-compose.yml
├── requirements.txt
├── app/
│   ├── main.py
│   ├── database.py
│   ├── models.py
│   └── routes/
│       ├── products.py
│       └── inventory.py
├── sql/
│   ├── schema.sql
│   └── seed.sql
└── tests/
    └── test_api.py
```

```yaml
# docker-compose.yml
version: '3.8'
services:
  postgres:
    image: postgres:15
    environment:
      POSTGRES_DB: inventory
      POSTGRES_USER: admin
      POSTGRES_PASSWORD: secretpassword
    ports:
      - "5432:5432"
    volumes:
      - postgres_data:/var/lib/postgresql/data
      - ./sql:/docker-entrypoint-initdb.d

  api:
    build: .
    ports:
      - "8000:8000"
    depends_on:
      - postgres
    environment:
      DATABASE_URL: postgresql://admin:secretpassword@postgres:5432/inventory

volumes:
  postgres_data:
```

**GitHub Deliverable:** This is your first portfolio-ready project. It has:
- Docker setup (shows DevOps awareness)
- Proper schema with constraints
- REST API with error handling
- README with architecture explanation
- SQL files showing your schema design thinking

---

## 🔴 PART FOUR: REDIS — CACHING & SESSION MANAGEMENT (Week 5)

### Why Redis and Why Now?

> **Context in the architecture:** In a real system, PostgreSQL gets overwhelmed when millions of users hit it for the same data (like a product catalog). Redis sits in front of PostgreSQL as a cache — serving most reads from memory (nanosecond speed) and only going to Postgres for cache misses. This is how Netflix serves 230 million users.

### Days 36–37: Redis Fundamentals

**Installing Redis:**
```bash
sudo apt install redis-server
redis-server
redis-cli ping  # Should return "PONG"
```

**Core Data Structures:**
```bash
# Strings (most common)
SET user:1:name "Alice"
GET user:1:name
SET user:1:session "abc123" EX 3600  # Expires in 1 hour

# Hashes (like a JSON object)
HSET user:1 name "Alice" email "alice@example.com" role "admin"
HGET user:1 name
HGETALL user:1

# Lists (queues, logs)
RPUSH notifications:user:1 "New message from Bob"
LPUSH notifications:user:1 "Your order shipped"
LRANGE notifications:user:1 0 -1  # Get all

# Sets (unique values, fast membership check)
SADD online_users 101 102 103
SISMEMBER online_users 102  # Is user 102 online?
SMEMBERS online_users

# Sorted Sets (leaderboards, rate limiting)
ZADD leaderboard 1500 "alice" 2300 "bob" 980 "charlie"
ZRANGEBYSCORE leaderboard -inf +inf WITHSCORES  # Sorted by score
ZRANK leaderboard "alice"
```

### Days 38–39: Caching Patterns

**Cache-Aside Pattern (most common):**
```python
# cache.py
import redis
import json
import psycopg2
from typing import Optional

r = redis.Redis(host='localhost', port=6379, decode_responses=True)

def get_product(product_id: int) -> Optional[dict]:
    # 1. Check cache first
    cache_key = f"product:{product_id}"
    cached = r.get(cache_key)

    if cached:
        print("Cache HIT")
        return json.loads(cached)

    # 2. Cache miss — go to PostgreSQL
    print("Cache MISS — fetching from DB")
    conn = psycopg2.connect("dbname=inventory user=postgres")
    with conn.cursor() as cur:
        cur.execute("SELECT id, name, price FROM products WHERE id = %s",
                   (product_id,))
        row = cur.fetchone()
        if not row:
            return None
        product = {"id": row[0], "name": row[1], "price": str(row[2])}

    # 3. Store in cache (TTL: 5 minutes)
    r.setex(cache_key, 300, json.dumps(product))

    return product
```

**Cache Invalidation (the hardest problem in CS):**
```python
def update_product(product_id: int, new_price: float):
    # 1. Update in database
    conn.execute("UPDATE products SET price = %s WHERE id = %s",
                (new_price, product_id))
    conn.commit()

    # 2. INVALIDATE the cache — don't leave stale data
    r.delete(f"product:{product_id}")
    # Next request will be a cache miss and fetch fresh data
```

### Days 40–42: Mini-Project #4 — Session & Rate Limiting Service

**🏗️ PROJECT: API Authentication with Redis Sessions + Rate Limiting**

**Real-World Problem:** Build an authentication system where:
1. User logs in → session stored in Redis (not database)
2. Each API endpoint checks Redis for valid session
3. Rate limiting: max 100 requests per user per hour

```python
# auth_service.py
import redis
import uuid
import hashlib
from datetime import datetime

r = redis.Redis(host='localhost', port=6379, decode_responses=True)

def create_session(user_id: int) -> str:
    session_id = str(uuid.uuid4())
    session_key = f"session:{session_id}"

    # Store session data in Redis hash
    r.hset(session_key, mapping={
        "user_id": user_id,
        "created_at": datetime.now().isoformat(),
        "last_active": datetime.now().isoformat()
    })
    r.expire(session_key, 3600)  # Session expires in 1 hour

    return session_id

def validate_session(session_id: str) -> Optional[int]:
    session_key = f"session:{session_id}"
    data = r.hgetall(session_key)
    if not data:
        return None  # Session expired or doesn't exist
    # Refresh TTL on activity
    r.expire(session_key, 3600)
    return int(data["user_id"])

def check_rate_limit(user_id: int, limit: int = 100) -> bool:
    key = f"rate_limit:{user_id}:{datetime.now().strftime('%Y%m%d%H')}"
    count = r.incr(key)
    if count == 1:
        r.expire(key, 3600)  # Reset each hour
    return count <= limit
```

---

## 📨 PART FIVE: APACHE KAFKA — EVENT-DRIVEN ARCHITECTURE (Week 6)

### Why Kafka and Why Now?

> **Context in the architecture:** Imagine a user places an order. The system must: send a confirmation email, reduce inventory, notify the warehouse, update analytics, charge the payment. If we do all this synchronously, the user waits 10 seconds. With Kafka, the order is placed instantly and all downstream systems process asynchronously. This is how Amazon handles millions of orders per day.

### Days 43–44: Kafka Concepts

**Core Concepts:**
```
Producer → [Topic (with Partitions)] → Consumer Groups

Topic: "orders"
├── Partition 0: [order1, order4, order7...]
├── Partition 1: [order2, order5, order8...]
└── Partition 2: [order3, order6, order9...]

Consumer Group A (Order Service):    reads ALL partitions
Consumer Group B (Email Service):    reads ALL partitions independently
Consumer Group C (Analytics):        reads ALL partitions independently

Key insight: Multiple consumer groups can read the SAME topic independently.
Each group maintains its own "offset" (where it last read up to).
```

**Installing Kafka with Docker:**
```yaml
# docker-compose.kafka.yml
version: '3.8'
services:
  zookeeper:
    image: confluentinc/cp-zookeeper:7.5.0
    environment:
      ZOOKEEPER_CLIENT_PORT: 2181

  kafka:
    image: confluentinc/cp-kafka:7.5.0
    depends_on: [zookeeper]
    ports:
      - "9092:9092"
    environment:
      KAFKA_BROKER_ID: 1
      KAFKA_ZOOKEEPER_CONNECT: zookeeper:2181
      KAFKA_ADVERTISED_LISTENERS: PLAINTEXT://localhost:9092
      KAFKA_OFFSETS_TOPIC_REPLICATION_FACTOR: 1

  kafka-ui:
    image: provectuslabs/kafka-ui:latest
    ports:
      - "8080:8080"
    environment:
      KAFKA_CLUSTERS_0_BOOTSTRAPSERVERS: kafka:9092
```

**Python Kafka Producer & Consumer:**
```python
# producer.py
from kafka import KafkaProducer
import json

producer = KafkaProducer(
    bootstrap_servers=['localhost:9092'],
    value_serializer=lambda v: json.dumps(v).encode('utf-8')
)

def publish_order(order: dict):
    producer.send('orders', value=order)
    producer.flush()
    print(f"Published order: {order['id']}")

# consumer.py (run in separate terminal)
from kafka import KafkaConsumer
import json

consumer = KafkaConsumer(
    'orders',
    bootstrap_servers=['localhost:9092'],
    group_id='inventory-service',  # Different group_id = independent consumption
    value_deserializer=lambda m: json.loads(m.decode('utf-8'))
)

for message in consumer:
    order = message.value
    print(f"Processing order {order['id']} — reducing inventory...")
    # Reduce inventory in PostgreSQL
    # Send notification
    # Update analytics
```

### Days 45–47: Mini-Project #5 — Real-Time Order Processing Pipeline

**🏗️ PROJECT: Event-Driven Order Processing**

**Architecture:**
```
[Order API] --publish--> [Kafka: orders topic]
                              │
              ┌───────────────┼───────────────┐
              ▼               ▼               ▼
    [Inventory Service] [Email Service] [Analytics Service]
         │                   │               │
    [PostgreSQL]        [Log file]     [ClickHouse/file]
```

**Deliverables:**
1. Order producer API (FastAPI)
2. Inventory consumer (reduces stock)
3. Email consumer (logs email would be sent)
4. Simple analytics consumer (writes to CSV)
5. Docker Compose file bringing everything up
6. README with architecture diagram

---

## 🌊 PART SIX: CASSANDRA — DISTRIBUTED & TIME-SERIES (Week 7)

### Why Cassandra?

> **Context:** PostgreSQL is a single-node database by default. Cassandra is built from day one for distribution across many machines. It has no single point of failure. Used by Netflix, Discord, Apple, Uber. Perfect for: IoT data, user activity logs, time-series data, anything that needs massive write throughput.

### Days 48–50: Cassandra Fundamentals

**Key Differences from PostgreSQL:**

| Concept | PostgreSQL | Cassandra |
|---|---|---|
| **Architecture** | Single primary + replicas | Ring of equal peers |
| **Consistency** | Strong (ACID) | Tunable (eventual by default) |
| **Query language** | SQL | CQL (Cassandra Query Language) |
| **Schema design** | Model your data | Model your QUERIES |
| **Joins** | Yes | No |
| **Primary key** | Row identity | Partition key + clustering key |

**The Golden Rule of Cassandra:**
> Design your tables based on the queries you need to run, not based on entity relationships. There is NO such thing as JOIN in Cassandra.

**Installing with Docker:**
```bash
docker run --name cassandra -p 9042:9042 -d cassandra:4.1
docker exec -it cassandra cqlsh  # Connect to CQL shell
```

**CQL Fundamentals:**
```sql
-- Create keyspace (like a database)
CREATE KEYSPACE iot_data WITH REPLICATION = {
    'class': 'SimpleStrategy',
    'replication_factor': 1
};

USE iot_data;

-- Cassandra table: primary key is (partition_key, clustering_keys)
-- Partition key determines which node stores the data
-- Clustering keys determine order WITHIN a partition
CREATE TABLE sensor_readings (
    device_id   UUID,         -- Partition key: all readings for a device go together
    recorded_at TIMESTAMP,    -- Clustering key: sorted chronologically
    temperature FLOAT,
    humidity    FLOAT,
    pressure    FLOAT,
    PRIMARY KEY (device_id, recorded_at)  -- (partition, clustering)
) WITH CLUSTERING ORDER BY (recorded_at DESC);  -- newest first

-- Insert
INSERT INTO sensor_readings (device_id, recorded_at, temperature)
VALUES (uuid(), toTimestamp(now()), 22.5);

-- Query — MUST include partition key
SELECT * FROM sensor_readings
WHERE device_id = some-uuid-here
AND recorded_at >= '2025-01-01'
AND recorded_at < '2025-02-01';
```

### Days 51–53: Mini-Project #6 — IoT Sensor Data System

**🏗️ PROJECT: IoT Environmental Monitoring System**

**Real-World Problem:** A factory has 1000 sensors reading temperature, humidity, and pressure every second. Store and query this efficiently.

**This project demonstrates:**
- Why Cassandra beats PostgreSQL for time-series at scale
- How partition keys affect query patterns
- Write throughput comparison (run benchmarks, document results)

```python
# sensor_simulator.py
import uuid
import random
from datetime import datetime
from cassandra.cluster import Cluster
from cassandra.auth import PlainTextAuthProvider

cluster = Cluster(['localhost'])
session = cluster.connect('iot_data')

DEVICES = [uuid.uuid4() for _ in range(100)]

def simulate_readings():
    insert_stmt = session.prepare("""
        INSERT INTO sensor_readings
        (device_id, recorded_at, temperature, humidity, pressure)
        VALUES (?, ?, ?, ?, ?)
    """)

    for device_id in DEVICES:
        session.execute(insert_stmt, (
            device_id,
            datetime.now(),
            random.uniform(18.0, 35.0),
            random.uniform(30.0, 90.0),
            random.uniform(990.0, 1020.0)
        ))

    print(f"Inserted {len(DEVICES)} readings at {datetime.now()}")
```

---

## 📊 PART SEVEN: CLICKHOUSE — ANALYTICS AT SCALE (Week 8)

### Why ClickHouse?

> **Context in the architecture:** PostgreSQL is for transactions (OLTP). ClickHouse is for analytics (OLAP). If you want to run "show me revenue by product category for the last 3 years grouped by month" over 100 billion rows, ClickHouse does it in seconds. PostgreSQL would take hours. Used by Cloudflare, eBay, Uber, and thousands of companies.

### Days 54–56: ClickHouse Fundamentals

**Columnar Storage — Why It's Fast for Analytics:**
```
ROW STORAGE (PostgreSQL):
Row 1: [Alice, 28, New York, F, 90000]
Row 2: [Bob,   32, London,   M, 75000]
Row 3: [Carol, 25, Tokyo,    F, 85000]

When you SELECT AVG(salary), the DB reads ALL fields of ALL rows.
Wasted I/O for columns you didn't ask for.

COLUMNAR STORAGE (ClickHouse):
Name column:   [Alice, Bob, Carol]
Age column:    [28, 32, 25]
City column:   [New York, London, Tokyo]
Salary column: [90000, 75000, 85000]  ← Only this column is read for AVG(salary)!

Result: 10-100x less I/O for analytical queries.
```

**Installing ClickHouse:**
```bash
docker run -d --name clickhouse -p 8123:8123 -p 9000:9000 \
  clickhouse/clickhouse-server:23.8
docker exec -it clickhouse clickhouse-client
```

**ClickHouse for Analytics:**
```sql
-- Create an analytics table
CREATE TABLE page_views (
    event_date  Date,
    user_id     UInt64,
    page_url    String,
    duration_ms UInt32,
    country     LowCardinality(String)
) ENGINE = MergeTree()
PARTITION BY toYYYYMM(event_date)  -- Data partitioned by month
ORDER BY (event_date, user_id);    -- Primary sort key

-- Analytical query: Page views per country per day
SELECT
    event_date,
    country,
    COUNT() as views,
    AVG(duration_ms) as avg_duration,
    uniq(user_id) as unique_users
FROM page_views
WHERE event_date >= '2025-01-01'
GROUP BY event_date, country
ORDER BY event_date, views DESC;
-- On 1 billion rows, this runs in < 1 second in ClickHouse
-- The same query on PostgreSQL could take hours
```

---

## 🔭 PART EIGHT: OBSERVABILITY & MONITORING (Week 9)

### Why Observability?

> **The MNC Standard:** Every production system must be observable. "If you can't measure it, you can't manage it." Teams at Netflix and Google know when a query starts getting slow — before users complain. This is done with metrics (Prometheus), dashboards (Grafana), and logs (Loki).

### Days 57–59: Prometheus + Grafana

**Setup:**
```yaml
# monitoring/docker-compose.yml
version: '3.8'
services:
  prometheus:
    image: prom/prometheus:v2.47.0
    ports:
      - "9090:9090"
    volumes:
      - ./prometheus.yml:/etc/prometheus/prometheus.yml

  grafana:
    image: grafana/grafana:10.2.0
    ports:
      - "3000:3000"
    environment:
      GF_SECURITY_ADMIN_PASSWORD: admin
    volumes:
      - grafana_data:/var/lib/grafana

  postgres-exporter:
    image: prometheuscommunity/postgres-exporter
    environment:
      DATA_SOURCE_NAME: "postgresql://postgres:secret@postgres:5432/mydb?sslmode=disable"
    ports:
      - "9187:9187"

volumes:
  grafana_data:
```

**Key PostgreSQL Metrics to Monitor:**
```yaml
# prometheus.yml
scrape_configs:
  - job_name: 'postgresql'
    static_configs:
      - targets: ['postgres-exporter:9187']
```

**Grafana Dashboard Queries:**
- Active connections: `pg_stat_activity_count`
- Cache hit ratio: `pg_stat_bgwriter_buffers_hit / (pg_stat_bgwriter_buffers_hit + pg_stat_bgwriter_buffers_clean)`
- Transaction rate: `rate(pg_stat_database_xact_commit[1m])`
- Query execution time: use `pg_stat_statements` metrics

---

## 🐳 PART NINE: DOCKER & KUBERNETES (Weeks 10–11)

### Days 60–65: Docker Deep Dive

**Why Docker:**
> "Works on my machine" is not a valid answer at MNCs. Docker packages your application + its dependencies into a container that runs identically everywhere — your laptop, a CI server, and a production cluster.

**Dockerfile for Your API:**
```dockerfile
# Dockerfile
FROM python:3.11-slim

WORKDIR /app

# Install dependencies first (layer caching optimization)
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# Never run as root in production
RUN useradd -m appuser
USER appuser

EXPOSE 8000
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
```

**Docker Best Practices:**
- Use specific image tags (not `latest`) — reproducibility
- Multi-stage builds — keep image size small
- Never store secrets in Dockerfile — use environment variables
- Use `.dockerignore` — like `.gitignore` for Docker

### Days 66–70: Kubernetes Basics

**The Core Concepts:**
```yaml
# deployment.yaml — runs your application
apiVersion: apps/v1
kind: Deployment
metadata:
  name: inventory-api
spec:
  replicas: 3  # Run 3 copies for high availability
  selector:
    matchLabels:
      app: inventory-api
  template:
    metadata:
      labels:
        app: inventory-api
    spec:
      containers:
      - name: api
        image: inventory-api:1.0.0
        ports:
        - containerPort: 8000
        resources:
          requests:
            memory: "128Mi"
            cpu: "100m"
          limits:
            memory: "256Mi"
            cpu: "500m"
        env:
        - name: DATABASE_URL
          valueFrom:
            secretKeyRef:
              name: db-secret
              key: url

---
# service.yaml — exposes your application
apiVersion: v1
kind: Service
metadata:
  name: inventory-api-service
spec:
  selector:
    app: inventory-api
  ports:
  - port: 80
    targetPort: 8000
  type: ClusterIP
```

**Local Kubernetes with Minikube:**
```bash
# Install minikube (free, local K8s)
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube

minikube start
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
kubectl get pods        # See running pods
kubectl logs -f pod-name  # Stream logs
kubectl describe pod pod-name  # Debug
```

---

## 🔄 PART TEN: CI/CD WITH GITHUB ACTIONS (Week 12)

### Days 71–75: Automated Testing and Deployment

**GitHub Actions Pipeline:**
```yaml
# .github/workflows/ci.yml
name: CI Pipeline

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest

    services:
      postgres:
        image: postgres:15
        env:
          POSTGRES_PASSWORD: testpassword
          POSTGRES_DB: test_db
        options: >-
          --health-cmd pg_isready
          --health-interval 10s
          --health-timeout 5s
          --health-retries 5

    steps:
    - uses: actions/checkout@v4

    - name: Set up Python
      uses: actions/setup-python@v4
      with:
        python-version: '3.11'

    - name: Install dependencies
      run: |
        pip install -r requirements.txt
        pip install pytest pytest-cov

    - name: Run database migrations
      run: psql $DATABASE_URL -f sql/schema.sql
      env:
        DATABASE_URL: postgresql://postgres:testpassword@localhost/test_db

    - name: Run tests
      run: pytest tests/ --cov=app --cov-report=xml

    - name: Upload coverage
      uses: codecov/codecov-action@v3

  build:
    needs: test
    runs-on: ubuntu-latest
    steps:
    - uses: actions/checkout@v4
    - name: Build Docker image
      run: docker build -t inventory-api:${{ github.sha }} .
```

---

## 🏆 PART ELEVEN: FINAL CAPSTONE — MNC-GRADE PRODUCTION SYSTEM (Weeks 13–16)

### The Capstone: Real-Time E-Commerce Analytics Platform

**This is the crown jewel of your portfolio.**

**Architecture (Full System):**
```
Users → [Nginx/Kong API Gateway]
              │
    ┌─────────┴─────────┐
    │                   │
[User Service]    [Order Service]
    │                   │
[PostgreSQL]       [PostgreSQL]
                       │
               [Kafka: orders topic]
                       │
          ┌────────────┼────────────┐
          │            │            │
  [Inventory]    [Email Log]   [Analytics]
  [Service]      [Service]     [Consumer]
      │                              │
  [PostgreSQL]               [ClickHouse]
                                     │
                              [Grafana Dashboard]
  [Redis]  ← session cache / product cache
  [MinIO]  ← file/image storage
```

**Tech Stack:**
- **Languages:** Python 3.11
- **Web Framework:** FastAPI
- **Databases:** PostgreSQL 15, Redis 7, Cassandra 4.1, ClickHouse 23.8
- **Message Queue:** Apache Kafka
- **Object Storage:** MinIO
- **Monitoring:** Prometheus + Grafana + Loki
- **Container:** Docker + Docker Compose → Kubernetes (Minikube)
- **CI/CD:** GitHub Actions
- **API Gateway:** Kong (open source)

**All free. All open source. All industry standard.**

---

## 📋 PART TWELVE: DOCUMENTATION & PORTFOLIO STRATEGY

### GitHub Repository Structure (For Recruiters)
```
database-engineering-journey/
├── README.md              ← Clear overview + architecture diagram
├── LEARNING_LOG.md        ← Weekly progress log
├── week-00-foundations/
│   ├── README.md
│   ├── hardware-notes.md
│   └── scripts/
├── week-01-sql-basics/
│   ├── README.md
│   └── queries.sql
├── projects/
│   ├── 01-ecommerce-schema/
│   ├── 02-banking-transactions/
│   ├── 03-library-system/
│   ├── 04-redis-sessions/
│   ├── 05-kafka-orders/
│   ├── 06-iot-cassandra/
│   └── 07-analytics-platform/   ← Your capstone
└── blog-drafts/
    └── *.md
```

**What Recruiters Check:**
1. **Commit history** — consistent commits over months = serious learner
2. **README quality** — can you communicate technically?
3. **Code quality** — comments, error handling, structure
4. **Problem → Solution** framing — does each project solve a real problem?
5. **Architecture decisions** — do you explain WHY, not just WHAT?

### Blog Post Strategy (Hashnode / Dev.to)

**Write these posts (each builds your expertise signal):**
1. "Why I learned hardware before databases" — Week 0 insight
2. "B+ Trees: The data structure that makes databases fast" — Week 1
3. "Transactions saved my fake bank: ACID explained with code" — Week 2
4. "I added Redis to my API and queries went from 100ms to 0.5ms" — Month 2
5. "Why Discord migrated from Cassandra to ScyllaDB (and what I learned)" — Month 3
6. "How I monitor my PostgreSQL database like a Netflix SRE" — Month 4
7. "Deploying a 5-service architecture on Kubernetes for free" — Month 5
8. "6 months from zero to MNC-ready: My complete database engineering journey" — Final

---

## 📅 PART THIRTEEN: THE DAILY TIMETABLE

### Daily Structure (Weekdays — 3 Hours)
```
⏰ Time       | Activity
─────────────────────────────────────────────────
06:30 – 07:00 | Active Recall (review yesterday's questions)
07:00 – 08:00 | New concept study (read + understand)
08:00 – 09:00 | Hands-on coding / lab work
09:00 – 09:15 | Write 3 things learned → GitHub commit
09:15 – 09:30 | Draft blog post paragraph (don't publish yet)
```

### Daily Structure (Weekends — 6 Hours)
```
⏰ Time       | Activity
─────────────────────────────────────────────────
09:00 – 11:00 | Project work (build, code, test)
11:00 – 12:00 | Document the project (README, comments)
13:00 – 14:00 | Write/publish Hashnode post
14:00 – 15:00 | Active recall + conceptual tests
15:00 – 16:00 | Explore one thing that confused you this week
```

### Weekly Deliverables Checklist
```
Week N Checklist:
[ ] All daily code committed to GitHub
[ ] At least 1 Hashnode/Dev.to post published
[ ] Weekly learning summary added to LEARNING_LOG.md
[ ] This week's mini-project completed and documented
[ ] README updated with project instructions
[ ] LinkedIn post with project screenshot/demo
```

---

## 🧠 MASTER ACTIVE RECALL BANK

### After Month 1 — Can You Answer These?
1. What is the difference between a `Seq Scan` and an `Index Scan` in PostgreSQL?
2. Why does an `ORDER BY` query benefit from an index?
3. What is "write amplification" and when does it matter?
4. Explain MVCC in your own words. Why do "readers not block writers"?
5. What is the WAL? What happens if you delete it?
6. What is normalization? Give an example of a 2NF violation.
7. Why is `SELECT *` a bad practice in production?
8. What does `EXPLAIN ANALYZE` tell you that `EXPLAIN` alone doesn't?
9. How does a B+ Tree differ from a B-Tree?
10. What is a "phantom read" and which isolation level prevents it?

### After Month 2 — Can You Answer These?
1. What is the difference between Redis Strings, Hashes, and Sets? When do you use each?
2. What is the Cache-Aside pattern? What are its failure modes?
3. What problem does Redis TTL solve?
4. What is a "cache stampede" and how do you prevent it?
5. Why store sessions in Redis instead of PostgreSQL?
6. What is Redis persistence? What is RDB vs AOF?

### After Month 3 — Can You Answer These?
1. What is the CAP theorem? Give an example of a CP system vs an AP system.
2. What does Kafka's "consumer group" concept solve?
3. Why does Cassandra not support JOINs? What do you do instead?
4. What is a "partition key" in Cassandra and why is it critical for performance?
5. What is "eventual consistency"? Give a real-world example where it's acceptable.

### After Month 4 — Can You Answer These?
1. Why is ClickHouse faster than PostgreSQL for analytical queries?
2. What is columnar storage? Draw the difference.
3. What is OLTP vs OLAP? Name a system for each.
4. What does a "partition" in ClickHouse's MergeTree engine do?
5. How do you decide when to use PostgreSQL vs ClickHouse?

---

## 🔧 DEBUGGING EXERCISES

**Exercise 1: The Slow Query**
```sql
-- This query takes 30 seconds on a 5-million row table. Fix it.
SELECT * FROM orders
WHERE EXTRACT(YEAR FROM created_at) = 2024
AND status = 'completed';

-- Hint: Why can't an index on created_at be used here?
-- Solution clue: Rewrite the WHERE clause to be "sargable"
```

**Exercise 2: The Deadlock**
```python
# Session 1 and Session 2 run simultaneously and deadlock. Why?
# Session 1:
BEGIN;
UPDATE accounts SET balance = balance - 100 WHERE id = 1;
UPDATE accounts SET balance = balance + 100 WHERE id = 2;
COMMIT;

# Session 2:
BEGIN;
UPDATE accounts SET balance = balance - 50 WHERE id = 2;  # Locks id=2
UPDATE accounts SET balance = balance + 50 WHERE id = 1;  # Waits for id=1
COMMIT;
# How do you fix this?
```

**Exercise 3: The N+1 Problem**
```python
# This code makes 1001 database calls for 1000 orders. Rewrite it.
orders = session.query(Order).all()
for order in orders:
    user = session.query(User).get(order.user_id)  # N queries!
    print(f"Order {order.id} by {user.name}")
```

---

## 🎯 SCENARIO-BASED LEARNING

### Scenario 1: Instagram Like Counter
**Problem:** Instagram has 1 billion users. A popular post gets 50,000 likes per second. How do you store this?

**Think through:**
- Can PostgreSQL handle 50,000 `UPDATE` statements per second?
- What is Redis' role here?
- How does this eventually persist to a database?
- What consistency guarantee do you need for a "like count"?

### Scenario 2: Uber Surge Pricing
**Problem:** Uber needs to show surge pricing in real-time based on driver density and ride demand in geographic areas. How would you design the data layer?

**Think through:**
- What database(s) would you use?
- How do you represent "geographic areas"?
- How often does the data change?
- What's the latency requirement (user expects < 200ms)?

### Scenario 3: Netflix Watch History
**Problem:** Netflix has 230 million users, each watching ~2 hours/day. They need to: (a) resume playback at the exact position, (b) show "Recently Watched" list, (c) run ML on watch history.

**Think through:**
- Which database for (a)? (b)? (c)?
- How would you model the data for each use case?
- What happens when a user watches on multiple devices simultaneously?

---

## 📊 PROGRESS TRACKING

### Milestone Badges (Award Yourself)
- 🥉 **Bronze: SQL Foundations** — Complete Week 1-4 + Projects 1-3
- 🥈 **Silver: Multi-Database** — Complete Weeks 5-8 + Projects 4-6
- 🥇 **Gold: Full Stack Data** — Complete Weeks 9-12 + CI/CD working
- 💎 **Diamond: MNC Ready** — Capstone deployed on Kubernetes with monitoring

### The Portfolio Test
> Before applying to any MNC, your GitHub should show:
> - [ ] 7+ projects, all with clear READMEs
> - [ ] Consistent commits spanning 5+ months
> - [ ] At least 5 published technical blog posts
> - [ ] A capstone project with Docker + at least 3 different databases
> - [ ] Evidence of debugging (commit messages like "fix: resolve N+1 in orders endpoint")
> - [ ] Architecture diagrams in at least 2 project READMEs

---

## 📚 FREE RESOURCES REFERENCE

| Topic | Free Resource |
|---|---|
| PostgreSQL | postgresql.org/docs (official, best in class) |
| Redis | redis.io/docs |
| Kafka | kafka.apache.org/documentation |
| Cassandra | cassandra.apache.org/doc |
| ClickHouse | clickhouse.com/docs |
| Docker | docs.docker.com |
| Kubernetes | kubernetes.io/docs/tutorials |
| SQL Practice | pgexercises.com, leetcode.com/study-plan/sql |
| System Design | github.com/donnemartin/system-design-primer |
| Blog Platform | hashnode.com (free), dev.to (free) |
| Architecture | draw.io (free diagramming) |
| Monitoring | grafana.com/oss (all free) |

---

*This roadmap was designed to take you from zero to MNC-level in 6 months. Every concept connects to the next. Every project builds on the previous one. The architecture you learned on Day 1 is the same architecture you'll deploy on Day 180. Trust the process, document everything, and build in public.*

**Remember:** The goal is not to memorize. The goal is to understand so deeply that you could explain it to someone else — and your GitHub, your blog, and your projects prove that you did.

