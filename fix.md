# 🎯 Tier 1 MNC Complete Gap Filler
### Every Missing Dimension — From 6/10 → 10/10 Readiness
#### DSA · Behavioral · SQL · LLD · Resume · Mock Interviews · Communication

---

> **Purpose:** This file closes every gap identified in the MNC Readiness Audit. Combined with the OS, Database, Data Engineering, System Design, Java, and Python roadmaps, this document brings your Tier 1 MNC readiness to 9–10/10 across ALL evaluation dimensions.
>
> **Audit Gaps Addressed:**
> - DSA / Algorithmic Problems: 2/10 → **10/10**
> - Behavioral Interview: 1/10 → **9/10**
> - SQL Under Pressure: 5/10 → **9/10**
> - Low-Level Design (LLD): 3/10 → **9/10**
> - Resume & Portfolio Presentation: 5/10 → **10/10**
> - Mock Interview Practice: 3/10 → **9/10**
> - Communication & Soft Skills: unscored → **9/10**

---

## 📊 FINAL READINESS DASHBOARD (After This File)

| Dimension | Before | After | Evidence You'll Have |
|---|---|---|---|
| System Design Knowledge | 9/10 | **10/10** | 7 designed systems + ADRs |
| DSA / LeetCode | 2/10 | **10/10** | 100+ solved, tracked on GitHub |
| Core Java + Spring Boot | 2/10 | **9/10** | 6 projects including production API |
| Core Python + FastAPI | 2/10 | **9/10** | 6 projects including PyPI package |
| Database Engineering | 9/10 | **10/10** | Deep internals + projects |
| OS + Networking | 9/10 | **10/10** | Shell, thread lib, packet analyzer |
| Data Engineering | 9/10 | **10/10** | ETL pipelines + Kafka + Airflow |
| SQL Under Pressure | 5/10 | **9/10** | 50 timed SQL problems tracked |
| Low-Level Design (LLD) | 3/10 | **9/10** | 6 LLD designs documented |
| Behavioral Interview | 1/10 | **9/10** | 8 STAR stories + recorded practice |
| Resume & Presentation | 5/10 | **10/10** | Polished resume + GitHub portfolio |
| Mock Interview Practice | 3/10 | **9/10** | 20+ timed sessions logged |
| Communication & Clarity | unscored | **9/10** | Recorded explanations + blog posts |

---

---

# 🔴 DIMENSION 1: DSA — DATA STRUCTURES & ALGORITHMS

> **Why this is the gate:** Every Tier 1 MNC (Google, Amazon, Microsoft, Meta) eliminates candidates in Round 1 with algorithmic coding problems. No system design knowledge helps you if you cannot pass this gate.
>
> **Daily commitment:** 45 minutes every day. No exceptions. Parallel to all other roadmaps.

---

## The 14 Patterns — Master These, Not Random Problems

```
PATTERN MAP — Learn the pattern first, then the problems under it

Pattern 1:  Arrays + Hashing          → Two Sum, Group Anagrams, Top K Frequent
Pattern 2:  Two Pointers              → 3Sum, Container With Most Water, Palindrome
Pattern 3:  Sliding Window            → Longest Substring, Min Window Substring
Pattern 4:  Stack (Monotonic)         → Daily Temperatures, Largest Rectangle Histogram
Pattern 5:  Binary Search             → Search Rotated Array, Koko Eating Bananas
Pattern 6:  Linked List               → Reverse, Detect Cycle, Merge K Sorted
Pattern 7:  Trees (BFS/DFS)           → Level Order, LCA, Serialize/Deserialize
Pattern 8:  Tries                     → Word Search II, Implement Trie, Autocomplete
Pattern 9:  Heap / Priority Queue     → Find Median Stream, K Closest Points
Pattern 10: Backtracking              → Permutations, N-Queens, Word Search
Pattern 11: Graphs                    → Number of Islands, Course Schedule, Clone Graph
Pattern 12: Dynamic Programming       → Coin Change, LCS, Word Break, House Robber
Pattern 13: Greedy                    → Jump Game, Interval Scheduling, Gas Station
Pattern 14: Bit Manipulation          → Single Number, Power of Two, Counting Bits
```

---

## 8-Week DSA Curriculum (45 min/day)

### WEEK 1: Arrays + Hashing + Two Pointers

**Goal:** Solve 15 problems. By end of week: solve any Easy in 10 min, Medium in 20–25 min.

| Day | Problems | Pattern | Difficulty |
|-----|----------|---------|------------|
| Mon | Two Sum (LC 1), Contains Duplicate (LC 217) | Hashing | Easy |
| Tue | Valid Anagram (LC 242), Group Anagrams (LC 49) | Hashing | Easy/Med |
| Wed | Top K Frequent Elements (LC 347), Product Except Self (LC 238) | Hashing | Medium |
| Thu | Longest Consecutive Sequence (LC 128), Valid Palindrome (LC 125) | Hash/Pointer | Medium/Easy |
| Fri | 3Sum (LC 15), Container With Most Water (LC 11) | Two Pointers | Medium |
| Sat | Trapping Rain Water (LC 42) | Two Pointers | Hard |
| Sun | Re-solve all 7 from memory. Time yourself. | Review | — |

**How to solve each problem:**
```
Step 1 (3 min):  Read problem. Write edge cases on paper/screen.
Step 2 (5 min):  Think out loud: "Brute force would be... The better approach is..."
Step 3 (15 min): Write working code
Step 4 (5 min):  Test with provided examples + your own edge cases
Step 5 (5 min):  Analyze: O(?) time, O(?) space. Can you do better?
Step 6 (2 min):  Document in GitHub: pattern used, time complexity, key insight
```

### WEEK 2: Sliding Window + Stack

| Day | Problems | Pattern |
|-----|----------|---------|
| Mon | Best Time to Buy/Sell Stock (LC 121), Sliding Window Maximum (LC 239) | Sliding Window |
| Tue | Longest Substring Without Repeating (LC 3), Longest Repeating Char Replace (LC 424) | Sliding Window |
| Wed | Minimum Window Substring (LC 76) | Sliding Window |
| Thu | Valid Parentheses (LC 20), Min Stack (LC 155) | Stack |
| Fri | Evaluate Reverse Polish Notation (LC 150), Daily Temperatures (LC 739) | Stack |
| Sat | Largest Rectangle in Histogram (LC 84) | Monotonic Stack |
| Sun | Review + re-solve 3 hardest from the week | Review |

### WEEK 3: Binary Search + Linked Lists

| Day | Problems | Pattern |
|-----|----------|---------|
| Mon | Binary Search (LC 704), Search in Rotated Sorted Array (LC 33) | Binary Search |
| Tue | Find Minimum in Rotated Sorted Array (LC 153), Time Based Key-Value (LC 981) | Binary Search |
| Wed | Koko Eating Bananas (LC 875) — learn the template | Binary Search |
| Thu | Reverse Linked List (LC 206), Merge Two Sorted Lists (LC 21) | Linked List |
| Fri | Reorder List (LC 143), Remove Nth Node From End (LC 19) | Linked List |
| Sat | Copy List with Random Pointer (LC 138), LRU Cache (LC 146) | Linked List |
| Sun | LRU Cache deep dive — implement with HashMap + DLL | Review |

**LRU Cache Template (Most Important)**
```python
class LRUCache:
    def __init__(self, capacity: int):
        self.cap = capacity
        self.cache = {}                          # key → node
        # Dummy head and tail — avoids null checks
        self.head = Node(0, 0)
        self.tail = Node(0, 0)
        self.head.next = self.tail
        self.tail.prev = self.head

    def get(self, key: int) -> int:
        if key not in self.cache: return -1
        self._move_to_front(self.cache[key])
        return self.cache[key].val

    def put(self, key: int, value: int) -> None:
        if key in self.cache:
            self._remove(self.cache[key])
        node = Node(key, value)
        self.cache[key] = node
        self._insert_at_front(node)
        if len(self.cache) > self.cap:
            lru = self.tail.prev
            self._remove(lru)
            del self.cache[lru.key]

    def _remove(self, node):
        node.prev.next = node.next
        node.next.prev = node.prev

    def _insert_at_front(self, node):
        node.next = self.head.next
        node.prev = self.head
        self.head.next.prev = node
        self.head.next = node

    def _move_to_front(self, node):
        self._remove(node)
        self._insert_at_front(node)
```

### WEEK 4: Trees

| Day | Problems | Pattern |
|-----|----------|---------|
| Mon | Invert Binary Tree (LC 226), Max Depth (LC 104) | DFS |
| Tue | Diameter of Binary Tree (LC 543), Balanced Binary Tree (LC 110) | DFS |
| Wed | Same Tree (LC 100), Subtree of Another Tree (LC 572) | DFS |
| Thu | Lowest Common Ancestor (LC 236), Binary Tree Level Order (LC 102) | BFS |
| Fri | Binary Tree Right Side View (LC 199), Count Nodes in Complete Tree (LC 222) | BFS |
| Sat | Validate BST (LC 98), Kth Smallest in BST (LC 230) | BST |
| Sun | Serialize and Deserialize Binary Tree (LC 297) — Hard | Review |

**Tree DFS Template (Memorise)**
```python
def dfs(node):
    if not node: return base_case
    left  = dfs(node.left)
    right = dfs(node.right)
    return combine(left, right, node.val)

# BFS Template
from collections import deque
def bfs(root):
    if not root: return []
    result, queue = [], deque([root])
    while queue:
        level = []
        for _ in range(len(queue)):
            node = queue.popleft()
            level.append(node.val)
            if node.left:  queue.append(node.left)
            if node.right: queue.append(node.right)
        result.append(level)
    return result
```

### WEEK 5: Graphs

| Day | Problems | Pattern |
|-----|----------|---------|
| Mon | Number of Islands (LC 200), Clone Graph (LC 133) | BFS/DFS |
| Tue | Pacific Atlantic Water Flow (LC 417) | Multi-source BFS |
| Wed | Course Schedule (LC 207) — detect cycle | Topological Sort |
| Thu | Course Schedule II (LC 210) — find order | Topological Sort |
| Fri | Number of Connected Components (LC 323) | Union-Find |
| Sat | Redundant Connection (LC 684), Graph Valid Tree (LC 261) | Union-Find |
| Sun | Word Ladder (LC 127) — Hard | BFS |

**Union-Find Template**
```python
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank   = [0] * n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])  # path compression
        return self.parent[x]

    def union(self, x, y) -> bool:
        px, py = self.find(x), self.find(y)
        if px == py: return False  # already connected
        if self.rank[px] < self.rank[py]: px, py = py, px
        self.parent[py] = px
        if self.rank[px] == self.rank[py]: self.rank[px] += 1
        return True
```

### WEEK 6: Dynamic Programming

| Day | Problems | Pattern |
|-----|----------|---------|
| Mon | Climbing Stairs (LC 70), House Robber (LC 198) | 1D DP |
| Tue | House Robber II (LC 213), Longest Palindromic Substring (LC 5) | 1D DP |
| Wed | Coin Change (LC 322), Minimum Cost Climbing Stairs (LC 746) | Unbounded DP |
| Thu | Longest Common Subsequence (LC 1143), Edit Distance (LC 72) | 2D DP |
| Fri | Unique Paths (LC 62), Maximal Square (LC 221) | 2D DP |
| Sat | Word Break (LC 139), Jump Game (LC 55) | DP |
| Sun | Jump Game II (LC 45) — Greedy approach | Review |

**DP Problem-Solving Framework**
```
Step 1: Define the state — what does dp[i] or dp[i][j] represent?
Step 2: Write the recurrence — how does dp[i] relate to dp[i-1]?
Step 3: Identify the base case — what is dp[0] or dp[0][0]?
Step 4: Determine traversal order — left to right, or right to left?
Step 5: Space optimise — can you reduce from O(n²) to O(n)?
```

### WEEK 7: Heap + Backtracking + Trie

| Day | Problems | Pattern |
|-----|----------|---------|
| Mon | Kth Largest Element (LC 215), K Closest Points to Origin (LC 973) | Heap |
| Tue | Find Median from Data Stream (LC 295) | Two Heaps |
| Wed | Subsets (LC 78), Combination Sum (LC 39) | Backtracking |
| Thu | Permutations (LC 46), Letter Combinations of Phone (LC 17) | Backtracking |
| Fri | Word Search (LC 79) | Backtracking |
| Sat | Implement Trie (LC 208), Add and Search Word (LC 211) | Trie |
| Sun | Word Search II (LC 212) — Hard | Trie + Backtrack |

**Backtracking Template**
```python
def backtrack(state, choices):
    if is_complete(state):
        result.append(state[:])   # add a copy
        return
    for choice in choices:
        if is_valid(state, choice):
            state.append(choice)           # choose
            backtrack(state, choices)      # explore
            state.pop()                    # un-choose
```

### WEEK 8: Mixed Hard Problems + Mock Interviews

| Day | Activity |
|-----|----------|
| Mon | 2 Hard problems of your choice (timed 35 min each) |
| Tue | 1 Hour mock interview (simulate: explain while coding) |
| Wed | Revisit your 5 weakest patterns |
| Thu | Company-specific problems: Amazon OA style (2 Medium, 75 min) |
| Fri | Company-specific: Google style (1 Hard, discuss approach first) |
| Sat | Full mock: 45 min, 2 problems, explain aloud, reviewer gives feedback |
| Sun | Final review: can you solve each pattern's core problem from memory? |

---

## DSA Documentation in GitHub

```
dsa-solutions/
├── README.md               ← Progress tracker table
├── patterns/
│   ├── 01-sliding-window/
│   │   ├── notes.md        ← Pattern explanation in own words
│   │   ├── template.py     ← The reusable template
│   │   └── problems/
│   │       ├── lc003_longest_substring.py
│   │       └── lc076_minimum_window.py
│   ├── 02-two-pointers/
│   └── ...
└── progress.md             ← Weekly progress log
```

**Each solution file format:**
```python
"""
Problem: Longest Substring Without Repeating Characters (LC 3)
Pattern: Sliding Window
Difficulty: Medium
Date Solved: YYYY-MM-DD
Time: 18 minutes
Attempts: 1

Approach:
  Use a sliding window [left, right].
  Maintain a dict of {char → last seen index}.
  When we see a char already in window: move left past its last occurrence.
  Window size = right - left + 1 is the answer at each step.

Time Complexity:  O(n) — each character visited at most twice
Space Complexity: O(min(n, alphabet_size)) — dict stores at most 26 or 128 chars

Key Insight:
  Unlike simple sliding window (fixed size), here window is variable.
  The trick is storing the INDEX (not just presence) so we can jump left directly.
"""

def length_of_longest_substring(s: str) -> int:
    seen = {}      # char → last index
    left = 0
    max_len = 0
    for right, ch in enumerate(s):
        if ch in seen and seen[ch] >= left:
            left = seen[ch] + 1
        seen[ch] = right
        max_len = max(max_len, right - left + 1)
    return max_len

# Tests
assert length_of_longest_substring("abcabcbb") == 3
assert length_of_longest_substring("bbbbb")    == 1
assert length_of_longest_substring("pwwkew")   == 3
assert length_of_longest_substring("")          == 0
assert length_of_longest_substring("a")         == 1
print("All tests passed")
```

---

---

# 🟡 DIMENSION 2: SQL UNDER PRESSURE

> **Format it's actually tested in:** You get a schema, a question in plain English, and 10–15 minutes to write correct SQL from scratch.

---

## 30-Problem SQL Interview Track

### Schema Used Throughout (Memorise This)

```sql
-- Standard interview schema — appears in 80% of SQL questions
CREATE TABLE employees (
    emp_id      INT PRIMARY KEY,
    name        VARCHAR(100),
    dept_id     INT,
    salary      DECIMAL(10,2),
    manager_id  INT,          -- self-referencing (NULL for top-level managers)
    hire_date   DATE,
    job_title   VARCHAR(50)
);

CREATE TABLE departments (
    dept_id     INT PRIMARY KEY,
    dept_name   VARCHAR(100),
    location    VARCHAR(100)
);

CREATE TABLE orders (
    order_id    INT PRIMARY KEY,
    customer_id INT,
    order_date  DATE,
    total_amt   DECIMAL(10,2),
    status      VARCHAR(20)   -- 'PENDING','COMPLETED','CANCELLED'
);

CREATE TABLE customers (
    customer_id INT PRIMARY KEY,
    name        VARCHAR(100),
    email       VARCHAR(100),
    city        VARCHAR(50),
    joined_date DATE
);

CREATE TABLE products (
    product_id  INT PRIMARY KEY,
    name        VARCHAR(100),
    category    VARCHAR(50),
    price       DECIMAL(10,2)
);

CREATE TABLE order_items (
    item_id     INT PRIMARY KEY,
    order_id    INT,
    product_id  INT,
    quantity    INT,
    unit_price  DECIMAL(10,2)
);
```

### THE 30 PROBLEMS (Solve each in ≤15 minutes)

**TIER 1 — Basic (Days 1–10)**

```sql
-- Q1: List all employees earning more than the company average
SELECT name, salary
FROM employees
WHERE salary > (SELECT AVG(salary) FROM employees)
ORDER BY salary DESC;

-- Q2: Find the second highest salary
-- Method 1: Using OFFSET
SELECT salary FROM employees ORDER BY salary DESC LIMIT 1 OFFSET 1;
-- Method 2: Using subquery (handles ties correctly)
SELECT MAX(salary) FROM employees
WHERE salary < (SELECT MAX(salary) FROM employees);
-- Method 3: Using DENSE_RANK (most robust)
SELECT salary FROM (
    SELECT salary, DENSE_RANK() OVER (ORDER BY salary DESC) AS rnk
    FROM employees
) ranked WHERE rnk = 2 LIMIT 1;

-- Q3: Count employees per department, include departments with 0 employees
SELECT d.dept_name, COUNT(e.emp_id) AS employee_count
FROM departments d
LEFT JOIN employees e ON d.dept_id = e.dept_id
GROUP BY d.dept_id, d.dept_name
ORDER BY employee_count DESC;

-- Q4: Find employees who earn more than their manager
SELECT e.name AS employee, e.salary AS emp_salary,
       m.name AS manager,  m.salary AS mgr_salary
FROM employees e
JOIN employees m ON e.manager_id = m.emp_id
WHERE e.salary > m.salary;

-- Q5: Find duplicate email addresses
SELECT email, COUNT(*) AS occurrences
FROM customers
GROUP BY email
HAVING COUNT(*) > 1;

-- Q6: Find customers who have NEVER placed an order
SELECT c.name, c.email
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;

-- Q7: Top 3 products by total revenue
SELECT p.name, SUM(oi.quantity * oi.unit_price) AS revenue
FROM products p
JOIN order_items oi ON p.product_id = oi.product_id
GROUP BY p.product_id, p.name
ORDER BY revenue DESC
LIMIT 3;

-- Q8: Monthly order count and revenue for the last 12 months
SELECT DATE_FORMAT(order_date, '%Y-%m') AS month,  -- MySQL syntax
       COUNT(*) AS order_count,
       SUM(total_amt) AS monthly_revenue
FROM orders
WHERE order_date >= DATE_SUB(CURDATE(), INTERVAL 12 MONTH)
  AND status = 'COMPLETED'
GROUP BY DATE_FORMAT(order_date, '%Y-%m')
ORDER BY month;

-- PostgreSQL syntax:
SELECT TO_CHAR(order_date, 'YYYY-MM') AS month,
       COUNT(*) AS order_count,
       SUM(total_amt) AS monthly_revenue
FROM orders
WHERE order_date >= CURRENT_DATE - INTERVAL '12 months'
  AND status = 'COMPLETED'
GROUP BY TO_CHAR(order_date, 'YYYY-MM')
ORDER BY month;

-- Q9: Department with the highest average salary
SELECT d.dept_name, ROUND(AVG(e.salary), 2) AS avg_salary
FROM departments d
JOIN employees e ON d.dept_id = e.dept_id
GROUP BY d.dept_id, d.dept_name
ORDER BY avg_salary DESC
LIMIT 1;

-- Q10: Employees hired in the last 90 days
SELECT name, hire_date, dept_id
FROM employees
WHERE hire_date >= CURRENT_DATE - INTERVAL '90 days'
ORDER BY hire_date DESC;
```

**TIER 2 — Window Functions (Days 11–20)**

```sql
-- Q11: Rank employees by salary within each department
SELECT name, dept_id, salary,
       RANK()       OVER (PARTITION BY dept_id ORDER BY salary DESC) AS dept_rank,
       DENSE_RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS dept_dense_rank,
       ROW_NUMBER() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS row_num
FROM employees;

-- Q12: Top 2 earners per department
WITH ranked AS (
    SELECT name, dept_id, salary,
           RANK() OVER (PARTITION BY dept_id ORDER BY salary DESC) AS rnk
    FROM employees
)
SELECT r.name, d.dept_name, r.salary
FROM ranked r
JOIN departments d ON r.dept_id = d.dept_id
WHERE r.rnk <= 2
ORDER BY d.dept_name, r.salary DESC;

-- Q13: Running total of orders by date
SELECT order_date, total_amt,
       SUM(total_amt) OVER (ORDER BY order_date
                             ROWS UNBOUNDED PRECEDING) AS running_total
FROM orders
WHERE status = 'COMPLETED'
ORDER BY order_date;

-- Q14: Day-over-day sales change
WITH daily AS (
    SELECT order_date,
           SUM(total_amt) AS daily_sales
    FROM orders
    WHERE status = 'COMPLETED'
    GROUP BY order_date
)
SELECT order_date, daily_sales,
       LAG(daily_sales) OVER (ORDER BY order_date) AS prev_day,
       daily_sales - LAG(daily_sales) OVER (ORDER BY order_date) AS change_abs,
       ROUND(100.0 * (daily_sales - LAG(daily_sales) OVER (ORDER BY order_date))
             / NULLIF(LAG(daily_sales) OVER (ORDER BY order_date), 0), 2) AS change_pct
FROM daily
ORDER BY order_date;

-- Q15: 7-day moving average of daily sales
WITH daily AS (
    SELECT order_date, SUM(total_amt) AS daily_sales
    FROM orders WHERE status = 'COMPLETED'
    GROUP BY order_date
)
SELECT order_date, daily_sales,
       ROUND(AVG(daily_sales) OVER (
           ORDER BY order_date
           ROWS BETWEEN 6 PRECEDING AND CURRENT ROW
       ), 2) AS moving_avg_7d
FROM daily;

-- Q16: Percent of total per category
SELECT category,
       SUM(price) AS category_total,
       ROUND(100.0 * SUM(price) / SUM(SUM(price)) OVER (), 2) AS pct_of_total
FROM products
GROUP BY category;

-- Q17: Employees in top 25% salary within their department
SELECT name, dept_id, salary,
       NTILE(4) OVER (PARTITION BY dept_id ORDER BY salary) AS quartile
FROM employees
HAVING quartile = 4;  -- Won't work! NTILE in WHERE needs a subquery

-- Correct:
SELECT name, dept_id, salary FROM (
    SELECT name, dept_id, salary,
           NTILE(4) OVER (PARTITION BY dept_id ORDER BY salary) AS quartile
    FROM employees
) t WHERE quartile = 4;

-- Q18: Customer's first and latest order dates
SELECT c.name,
       MIN(o.order_date) AS first_order,
       MAX(o.order_date) AS latest_order,
       DATEDIFF(MAX(o.order_date), MIN(o.order_date)) AS days_as_customer,
       COUNT(o.order_id) AS total_orders
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.name
ORDER BY total_orders DESC;

-- Q19: Products bought by customer A but NOT customer B
SELECT DISTINCT oi.product_id, p.name
FROM order_items oi
JOIN products p ON oi.product_id = p.product_id
JOIN orders o ON oi.order_id = o.order_id
WHERE o.customer_id = 101  -- Customer A
AND oi.product_id NOT IN (
    SELECT oi2.product_id
    FROM order_items oi2
    JOIN orders o2 ON oi2.order_id = o2.order_id
    WHERE o2.customer_id = 102  -- Customer B
);

-- Q20: Consecutive login days (streak calculation)
-- Given: user_logins(user_id, login_date)
WITH numbered AS (
    SELECT user_id, login_date,
           ROW_NUMBER() OVER (PARTITION BY user_id ORDER BY login_date) AS rn
    FROM user_logins
),
grouped AS (
    SELECT user_id, login_date,
           login_date - CAST(rn AS INT) * INTERVAL '1 day' AS grp
    FROM numbered
)
SELECT user_id, MIN(login_date) AS streak_start,
       MAX(login_date) AS streak_end,
       COUNT(*) AS streak_length
FROM grouped
GROUP BY user_id, grp
ORDER BY streak_length DESC;
```

**TIER 3 — Advanced & Tricky (Days 21–30)**

```sql
-- Q21: Median salary per department
SELECT dept_id,
       PERCENTILE_CONT(0.5) WITHIN GROUP (ORDER BY salary) AS median_salary
FROM employees
GROUP BY dept_id;

-- Q22: Find gaps in order IDs (missing numbers)
SELECT prev_id + 1 AS gap_start,
       curr_id - 1 AS gap_end,
       curr_id - prev_id - 1 AS missing_count
FROM (
    SELECT order_id AS curr_id,
           LAG(order_id) OVER (ORDER BY order_id) AS prev_id
    FROM orders
) t
WHERE curr_id - prev_id > 1;

-- Q23: Self-join — Manager hierarchy (2 levels deep)
SELECT e.name AS employee,
       m.name AS manager,
       gm.name AS grand_manager
FROM employees e
LEFT JOIN employees m  ON e.manager_id  = m.emp_id
LEFT JOIN employees gm ON m.manager_id  = gm.emp_id;

-- Q24: Recursive CTE — Full hierarchy tree
WITH RECURSIVE org_tree AS (
    -- Base: top-level managers (no manager)
    SELECT emp_id, name, manager_id, 0 AS level, name AS path
    FROM employees WHERE manager_id IS NULL
    UNION ALL
    -- Recursive: add employees whose manager is in the CTE
    SELECT e.emp_id, e.name, e.manager_id,
           ot.level + 1,
           ot.path || ' → ' || e.name
    FROM employees e
    JOIN org_tree ot ON e.manager_id = ot.emp_id
)
SELECT level, name, path FROM org_tree ORDER BY path;

-- Q25: Pivot — Dept salary by job_title (dynamic is DB-specific; static here)
SELECT dept_id,
       SUM(CASE WHEN job_title = 'Engineer'  THEN salary ELSE 0 END) AS engineer_total,
       SUM(CASE WHEN job_title = 'Manager'   THEN salary ELSE 0 END) AS manager_total,
       SUM(CASE WHEN job_title = 'Analyst'   THEN salary ELSE 0 END) AS analyst_total
FROM employees
GROUP BY dept_id;

-- Q26: Identify churned customers (ordered 6+ months ago, not since)
SELECT c.customer_id, c.name,
       MAX(o.order_date) AS last_order,
       CURRENT_DATE - MAX(o.order_date) AS days_since
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.name
HAVING MAX(o.order_date) < CURRENT_DATE - INTERVAL '180 days';

-- Q27: Month-over-month growth rate
WITH monthly AS (
    SELECT DATE_TRUNC('month', order_date) AS month,
           SUM(total_amt) AS revenue
    FROM orders WHERE status = 'COMPLETED'
    GROUP BY DATE_TRUNC('month', order_date)
)
SELECT month, revenue,
       LAG(revenue) OVER (ORDER BY month) AS prev_month,
       ROUND(100.0 * (revenue - LAG(revenue) OVER (ORDER BY month))
             / NULLIF(LAG(revenue) OVER (ORDER BY month), 0), 1) AS mom_growth_pct
FROM monthly ORDER BY month;

-- Q28: Find all pairs of products frequently bought together
SELECT oi1.product_id AS product_a,
       oi2.product_id AS product_b,
       COUNT(*) AS times_bought_together
FROM order_items oi1
JOIN order_items oi2
    ON oi1.order_id = oi2.order_id
    AND oi1.product_id < oi2.product_id    -- avoid duplicates + self-pairs
GROUP BY oi1.product_id, oi2.product_id
HAVING COUNT(*) >= 5
ORDER BY times_bought_together DESC;

-- Q29: Customers who upgraded spending (last 3 months > first 3 months)
WITH customer_periods AS (
    SELECT customer_id,
           SUM(CASE WHEN order_date <= (SELECT MIN(order_date) FROM orders o2
                                       WHERE o2.customer_id = o.customer_id)
                                       + INTERVAL '90 days'
                    THEN total_amt ELSE 0 END) AS first_90_days,
           SUM(CASE WHEN order_date >= CURRENT_DATE - INTERVAL '90 days'
                    THEN total_amt ELSE 0 END) AS last_90_days
    FROM orders o
    WHERE status = 'COMPLETED'
    GROUP BY customer_id
)
SELECT cp.customer_id, c.name, cp.first_90_days, cp.last_90_days,
       cp.last_90_days - cp.first_90_days AS spending_growth
FROM customer_periods cp
JOIN customers c ON cp.customer_id = c.customer_id
WHERE cp.last_90_days > cp.first_90_days
ORDER BY spending_growth DESC;

-- Q30: Real-time inventory alert (products with <10 stock sold more than reorder threshold)
-- Assume: inventory(product_id, stock_quantity, reorder_point)
SELECT p.name, i.stock_quantity, i.reorder_point,
       COALESCE(recent.units_sold_7d, 0) AS units_sold_7d,
       CEIL(recent.units_sold_7d / 7.0 * 30) AS projected_30d_demand
FROM products p
JOIN inventory i ON p.product_id = i.product_id
LEFT JOIN (
    SELECT oi.product_id, SUM(oi.quantity) AS units_sold_7d
    FROM order_items oi
    JOIN orders o ON oi.order_id = o.order_id
    WHERE o.order_date >= CURRENT_DATE - INTERVAL '7 days'
      AND o.status = 'COMPLETED'
    GROUP BY oi.product_id
) recent ON p.product_id = recent.product_id
WHERE i.stock_quantity <= i.reorder_point
ORDER BY i.stock_quantity ASC;
```

**SQL Practice Platforms (Ranked):**
1. **StrataScratch** — Real MNC SQL questions from Google, Amazon, Airbnb. Free tier has 50+ questions.
2. **DataLemur** — SQL + ML questions from tech companies. Excellent explanations.
3. **HackerRank SQL** — Good for basics → intermediate. Free.
4. **Mode Analytics Tutorial** — Free, teaches analytics SQL with real datasets.

---

---

# 🟠 DIMENSION 3: LOW-LEVEL DESIGN (LLD)

> **What LLD tests:** Can you design a class structure that is extensible, maintainable, and correct? Tested at Amazon, Microsoft, Flipkart, and Tier 2 MNCs.
>
> **Format:** "Design a Parking Lot / ATM / Library System / Elevator / Chess Game" — you have 45 minutes to draw a class diagram and write key classes.

---

## The LLD Framework (Apply to Every Problem)

```
STEP 1 — REQUIREMENTS (5 min)
  Ask: What types of X exist? What operations are needed?
  Define: Entities, Actors, Key Flows

STEP 2 — IDENTIFY ENTITIES (5 min)
  Nouns in the problem = potential classes
  "Parking Lot has Floors, each Floor has Spots, Spots have Vehicles"
  → ParkingLot, Floor, ParkingSpot, Vehicle

STEP 3 — RELATIONSHIPS (5 min)
  Aggregation: ParkingLot HAS-A Floor
  Inheritance: Car IS-A Vehicle
  Association: Ticket BELONGS-TO Vehicle

STEP 4 — APPLY DESIGN PATTERNS (10 min)
  Identify which pattern fits:
  Strategy: variable algorithms (pricing strategies)
  Observer: notifications (email when slot available)
  Singleton: single instance (ParkingLotManager)
  Factory: create objects without knowing exact class (VehicleFactory)
  State: object changes behaviour based on state (Slot: AVAILABLE/OCCUPIED)

STEP 5 — CODE KEY CLASSES (20 min)
  Focus on: interfaces, key methods, relationships
  Not required: complete implementation of every method
```

---

## LLD 1: Parking Lot System

```python
from enum import Enum, auto
from abc import ABC, abstractmethod
from datetime import datetime
from typing import Optional
import threading

class VehicleType(Enum):
    BIKE = auto()
    CAR  = auto()
    TRUCK= auto()

class SpotSize(Enum):
    SMALL  = auto()   # Bikes
    MEDIUM = auto()   # Cars
    LARGE  = auto()   # Trucks

class SpotStatus(Enum):
    AVAILABLE = auto()
    OCCUPIED  = auto()
    RESERVED  = auto()

class Vehicle(ABC):
    def __init__(self, plate: str, vtype: VehicleType):
        self.plate = plate
        self.type  = vtype

    @property
    @abstractmethod
    def required_spot_size(self) -> SpotSize: ...

class Car(Vehicle):
    def __init__(self, plate): super().__init__(plate, VehicleType.CAR)
    @property
    def required_spot_size(self): return SpotSize.MEDIUM

class Bike(Vehicle):
    def __init__(self, plate): super().__init__(plate, VehicleType.BIKE)
    @property
    def required_spot_size(self): return SpotSize.SMALL

class Truck(Vehicle):
    def __init__(self, plate): super().__init__(plate, VehicleType.TRUCK)
    @property
    def required_spot_size(self): return SpotSize.LARGE

class ParkingSpot:
    def __init__(self, spot_id: str, size: SpotSize, floor: int):
        self.spot_id = spot_id
        self.size    = size
        self.floor   = floor
        self.status  = SpotStatus.AVAILABLE
        self.vehicle: Optional[Vehicle] = None

    def is_available(self) -> bool:
        return self.status == SpotStatus.AVAILABLE

    def park(self, vehicle: Vehicle):
        if not self.is_available():
            raise ValueError(f"Spot {self.spot_id} is not available")
        self.vehicle = vehicle
        self.status  = SpotStatus.OCCUPIED

    def free(self):
        self.vehicle = None
        self.status  = SpotStatus.AVAILABLE

class Ticket:
    def __init__(self, ticket_id: str, vehicle: Vehicle, spot: ParkingSpot):
        self.ticket_id = ticket_id
        self.vehicle   = vehicle
        self.spot      = spot
        self.entry_time= datetime.now()
        self.exit_time : Optional[datetime] = None

class PricingStrategy(ABC):
    @abstractmethod
    def calculate(self, ticket: Ticket) -> float: ...

class HourlyPricing(PricingStrategy):
    RATES = {SpotSize.SMALL: 20, SpotSize.MEDIUM: 40, SpotSize.LARGE: 80}
    def calculate(self, ticket: Ticket) -> float:
        hours = (ticket.exit_time - ticket.entry_time).seconds / 3600
        return max(1, hours) * self.RATES[ticket.spot.size]

class ParkingLot:
    """Singleton — only one parking lot manager."""
    _instance = None
    _lock = threading.Lock()

    def __new__(cls, *args, **kwargs):
        with cls._lock:
            if not cls._instance:
                cls._instance = super().__new__(cls)
        return cls._instance

    def __init__(self, name: str, floors: int, spots_per_floor: dict):
        if hasattr(self, '_initialized'): return
        self.name    = name
        self.spots   : dict[str, ParkingSpot] = {}
        self.tickets : dict[str, Ticket]      = {}
        self._ticket_counter = 0
        self._lock = threading.Lock()
        self.pricing_strategy: PricingStrategy = HourlyPricing()
        self._initialise_spots(floors, spots_per_floor)
        self._initialized = True

    def _initialise_spots(self, floors, spots_per_floor):
        for floor in range(1, floors + 1):
            for size, count in spots_per_floor.items():
                for i in range(1, count + 1):
                    sid = f"F{floor}-{size.name[0]}{i:02d}"
                    self.spots[sid] = ParkingSpot(sid, size, floor)

    def park(self, vehicle: Vehicle) -> Ticket:
        with self._lock:
            spot = self._find_spot(vehicle.required_spot_size)
            if not spot:
                raise ValueError(f"No available spot for {vehicle.type.name}")
            spot.park(vehicle)
            self._ticket_counter += 1
            ticket = Ticket(f"TKT-{self._ticket_counter:06d}", vehicle, spot)
            self.tickets[ticket.ticket_id] = ticket
            return ticket

    def exit(self, ticket_id: str) -> float:
        with self._lock:
            ticket = self.tickets.get(ticket_id)
            if not ticket: raise ValueError(f"Invalid ticket: {ticket_id}")
            ticket.exit_time = datetime.now()
            fee = self.pricing_strategy.calculate(ticket)
            ticket.spot.free()
            del self.tickets[ticket_id]
            return fee

    def _find_spot(self, required: SpotSize) -> Optional[ParkingSpot]:
        # Prefer same floor, then nearest floor
        for spot in sorted(self.spots.values(), key=lambda s: s.floor):
            if spot.size == required and spot.is_available():
                return spot
        return None

    def availability(self) -> dict:
        result = {}
        for spot in self.spots.values():
            key = spot.size.name
            if key not in result: result[key] = {"total": 0, "available": 0}
            result[key]["total"] += 1
            if spot.is_available(): result[key]["available"] += 1
        return result
```

---

## LLD 2: Library Management System

```python
from datetime import date, timedelta
from typing import Optional
from enum import Enum

class BookStatus(Enum):
    AVAILABLE = "available"
    BORROWED  = "borrowed"
    RESERVED  = "reserved"

class Book:
    def __init__(self, isbn: str, title: str, author: str, copies: int = 1):
        self.isbn   = isbn
        self.title  = title
        self.author = author
        self.total_copies    = copies
        self.available_copies= copies
        self.status = BookStatus.AVAILABLE

    def borrow(self):
        if self.available_copies == 0:
            raise ValueError(f"No copies available for '{self.title}'")
        self.available_copies -= 1
        if self.available_copies == 0:
            self.status = BookStatus.BORROWED

    def return_book(self):
        self.available_copies = min(self.available_copies + 1, self.total_copies)
        self.status = BookStatus.AVAILABLE

class Member:
    MAX_BORROW = 5
    LOAN_DAYS  = 14

    def __init__(self, member_id: str, name: str, email: str):
        self.member_id  = member_id
        self.name       = name
        self.email      = email
        self.borrowed   : list[BorrowRecord] = []
        self.fines      : float = 0.0

    def can_borrow(self) -> bool:
        active = [r for r in self.borrowed if not r.returned]
        return len(active) < self.MAX_BORROW and self.fines == 0

class BorrowRecord:
    FINE_PER_DAY = 5.0

    def __init__(self, record_id: str, member: Member, book: Book):
        self.record_id   = record_id
        self.member      = member
        self.book        = book
        self.borrow_date = date.today()
        self.due_date    = date.today() + timedelta(days=Member.LOAN_DAYS)
        self.return_date : Optional[date] = None
        self.returned    = False

    def calculate_fine(self) -> float:
        check_date = self.return_date or date.today()
        if check_date > self.due_date:
            overdue = (check_date - self.due_date).days
            return overdue * self.FINE_PER_DAY
        return 0.0

class Library:
    def __init__(self, name: str):
        self.name    = name
        self.books   : dict[str, Book]   = {}
        self.members : dict[str, Member] = {}
        self._counter = 0

    def add_book(self, book: Book):   self.books[book.isbn] = book
    def add_member(self, m: Member):  self.members[m.member_id] = m

    def borrow(self, member_id: str, isbn: str) -> BorrowRecord:
        member = self._get_member(member_id)
        book   = self._get_book(isbn)
        if not member.can_borrow():
            raise ValueError(f"Member {member.name} cannot borrow: check limits/fines")
        book.borrow()
        self._counter += 1
        record = BorrowRecord(f"BRW-{self._counter:05d}", member, book)
        member.borrowed.append(record)
        return record

    def return_book(self, record_id: str) -> float:
        record = self._find_record(record_id)
        record.return_date = date.today()
        record.returned = True
        fine = record.calculate_fine()
        record.member.fines += fine
        record.book.return_book()
        return fine

    def search(self, query: str) -> list[Book]:
        q = query.lower()
        return [b for b in self.books.values()
                if q in b.title.lower() or q in b.author.lower()]

    def _get_member(self, mid): 
        m = self.members.get(mid)
        if not m: raise ValueError(f"Member {mid} not found")
        return m
    def _get_book(self, isbn):
        b = self.books.get(isbn)
        if not b: raise ValueError(f"Book {isbn} not found")
        return b
    def _find_record(self, rid):
        for m in self.members.values():
            for r in m.borrowed:
                if r.record_id == rid: return r
        raise ValueError(f"Record {rid} not found")
```

---

## 4 More LLD Designs (Architecture Only — Implement for Practice)

```
LLD 3: ATM Machine
  Entities: ATM, Account, Card, Transaction, CashDispenser, Receipt
  States: IDLE, CARD_INSERTED, PIN_ENTERED, TRANSACTION_IN_PROGRESS
  Pattern: State Machine + Chain of Responsibility (PIN→Balance→Dispense)
  
LLD 4: Chess Game
  Entities: Board, Piece (King, Queen, Rook, Bishop, Knight, Pawn), Player, Move
  Pattern: Strategy (each Piece has its own move validation)
  Key methods: isValidMove(), applyMove(), isCheck(), isCheckmate()

LLD 5: Food Ordering System (McDonald's Kiosk)
  Entities: Menu, MenuItem, Order, OrderItem, Payment, Receipt
  Pattern: Builder (for complex Order construction)
  States: ORDERING, PAYMENT, PREPARATION, READY, COLLECTED

LLD 6: Ride-Sharing System (Uber-lite)
  Entities: Driver, Rider, Trip, Location, Vehicle, Pricing
  Pattern: Observer (ride status changes notify rider + driver)
  Key: matching algorithm, surge pricing strategy, route estimation
```

---

---

# 🟢 DIMENSION 4: BEHAVIORAL INTERVIEW

> **Why it matters:** Amazon has 16 Leadership Principles. Every interview question maps to one. Google and Microsoft have similar "Googliness" and "Growth Mindset" evaluations. These are eliminators — not fillers.

---

## Your 8 STAR Stories (Extract from Your Projects)

Each story covers a different competency. Write each out in full, then record yourself telling it in under 2 minutes.

```
STORY EXTRACTION TEMPLATE:
  Situation:  [Context — what was the project/task/role?]
  Task:       [What was your specific responsibility?]
  Action:     [What did YOU specifically do? Use "I", not "we"]
  Result:     [Quantified outcome — what improved and by how much?]

Write 8 stories covering:
  Story 1: Technical challenge you overcame independently
  Story 2: Time you delivered under a tight deadline
  Story 3: Time you identified and fixed a problem nobody else noticed
  Story 4: Time you learned something new quickly to solve a problem
  Story 5: Time a design decision failed and what you did
  Story 6: Time you simplified a complex problem
  Story 7: Time you went beyond what was asked
  Story 8: Time you disagreed with an approach (and what happened)
```

**Example Story 1 — From the Log Processor Project:**
```
SITUATION:
I was building a multi-threaded log file processor to analyse
server logs for error patterns. The system needed to process
500MB log files in under 30 seconds.

TASK:
Design and implement the concurrent processing pipeline with
correct thread safety — no duplicate counting, no missed entries.

ACTION:
I identified that using a naive shared list with a regular lock
would cause thread contention. I replaced it with a
ConcurrentHashMap of AtomicLong counters, eliminating lock
contention on reads entirely. I also implemented a
BlockingQueue-based producer-consumer pipeline separating
file reading from line parsing.

RESULT:
Processing time dropped from 45 seconds (sequential) to
8 seconds (4 threads), a 5.6x improvement. The solution
processed 2.1 million lines per second on test hardware,
verified by benchmarks I documented in the README.

COMPANY MAPPING:
  Amazon: "Delivers Results" + "Dive Deep"
  Google: Technical problem-solving + performance focus
  Microsoft: "Growth Mindset" (learned concurrent patterns to solve it)
```

**Example Story 5 — Technical Failure:**
```
SITUATION:
When building the Blood Bank Management API, I initially used
eager loading for all relationships (donors, blood units,
hospital requests) in every API response.

TASK:
Identify why the API was slow and fix it without breaking
existing functionality.

ACTION:
I ran EXPLAIN ANALYZE on the PostgreSQL queries and found that
fetching one blood unit was triggering 4 extra queries due to
Hibernate's N+1 problem. I switched to lazy loading with
@EntityGraph for specific endpoints that actually needed the
related data, and added Redis caching for the blood availability
endpoint (most frequently called, rarely changing data).

RESULT:
Blood availability endpoint latency reduced from 340ms to 12ms
(97% improvement). N+1 queries eliminated — verified by enabling
Hibernate SQL logging and comparing before/after query counts.
I documented the debugging process in the project README as a
learning resource.

COMPANY MAPPING:
  Amazon: "Are Right a Lot" — recognises own mistakes and corrects
  Microsoft: "Growth Mindset" — failed and learned
  Google: Technical depth in performance debugging
```

---

## Amazon Leadership Principles — Question Bank

```
PRINCIPLE              SAMPLE QUESTION               YOUR STORY #
Customer Obsession     "Tell me about a time you       Story 8 or 7
                        prioritised user needs over
                        technical preferences."
Ownership              "Tell me about taking the lead  Story 1 or 6
                        without being asked."
Invent & Simplify      "Tell me about a time you       Story 6
                        simplified something complex."
Are Right a Lot        "Tell me about a decision you   Story 5
                        reversed after new information."
Learn & Be Curious     "Tell me about something new    Story 4
                        you taught yourself recently."
Hire/Develop the Best  "Tell me about helping others." (pair programming, code review)
Insist on High Std     "Tell me about refusing to      Story 7
                        compromise on quality."
Think Big              "Tell me about a project that   System Design projects
                        required big-picture thinking."
Bias for Action        "Tell me about deciding with    Story 2
                        incomplete information."
Dive Deep              "Tell me about debugging a      Story 1 or 5
                        difficult technical problem."
Deliver Results        "Tell me about completing       Story 2
                        something despite obstacles."
```

---

## Behavioral Practice Protocol

**Week 1:** Write all 8 stories in the STAR format in `interview-prep/star-stories.md`

**Week 2:** Record yourself answering each one. Rules:
- Under 2 minutes per answer
- No more than 30 seconds on Situation + Task combined
- At least 60 seconds on Action (this is where depth lives)
- Always end with a quantified Result

**Week 3:** Practice with another person. They pick a company's principle at random, you answer with the appropriate story.

**Week 4:** Do 3 full mock behavioral interviews. Use Pramp.com (free) or find a study partner.

---

---

# 🔵 DIMENSION 5: RESUME & PORTFOLIO STRATEGY

---

## Resume — The Correct Format

```
[YOUR NAME]                                    [City, India]
[Email] | [Phone] | [LinkedIn URL] | [GitHub URL]

═══════════════════════════════════════════════════════
TECHNICAL SKILLS
  Languages:   Python (Advanced), Java (Intermediate), SQL
  Frameworks:  FastAPI, Spring Boot, Django
  Databases:   PostgreSQL, Redis, MongoDB, Cassandra
  Cloud/DevOps: Docker, Kubernetes, GitHub Actions, Prometheus
  Data/AI:     Pandas, Airflow, Kafka, pgvector, Ollama

═══════════════════════════════════════════════════════
PROJECTS (Most Recent First)

FastAPI + Celery Background Job Scheduler                [GitHub Link]
Python · FastAPI · Celery · Redis · Docker
• Built async job processing system handling report generation,
  email campaigns, and data exports without blocking API responses
• Implemented job status polling, automatic retry (exponential backoff),
  and task time limits; processed 500+ concurrent jobs in load tests
• Deployed with Docker Compose; CI/CD via GitHub Actions (pytest → build → push)

Blood Bank Management REST API                           [GitHub Link]
Java 17 · Spring Boot 3 · PostgreSQL · Redis · JUnit 5 · Swagger
• Designed RESTful API managing donors, blood inventory (8 blood types),
  and hospital requests with real-time low-stock alerts via Spring Events
• Implemented JWT authentication, role-based access (Admin/Staff/Hospital)
• 87% test coverage (JUnit 5 + Mockito); API documented with Swagger UI
• Reduced blood availability query latency from 340ms to 12ms with Redis cache

Multi-Threaded Log File Processor                        [GitHub Link]
Java 17 · ExecutorService · BlockingQueue · ConcurrentHashMap
• Processed 2.1M log lines/second using producer-consumer pipeline
  (reader threads → BlockingQueue → parser threads → aggregator)
• 5.6x faster than sequential processing; benchmarked with 500MB test files
• Generated incident reports: top error services, hourly error heatmaps

Distributed Key-Value Store                              [GitHub Link]
Python · Raft Consensus · Consistent Hashing · Docker
• 3-node cluster with Raft leader election (sub-300ms failover on crash)
• Quorum reads (R=2, N=3) guarantee consistency across all replicas
• Consistent hashing with 150 virtual nodes; data movement <25% on node add

[2 more projects...]

═══════════════════════════════════════════════════════
EDUCATION
B.E./B.Tech [Branch], [University], [City] — [CGPA] — [Year]

═══════════════════════════════════════════════════════
CERTIFICATIONS (Optional but adds signal)
  AWS Cloud Practitioner (if pursued)
  GitHub Actions CI/CD (free — GitHub Learning Lab)
```

**The Formula for Every Bullet Point:**
```
[Action Verb] + [What you built] + [How] + [Metric/Result]

BAD:  "Built an API using Python"
GOOD: "Designed REST API handling 8,500 requests/second with <10ms p99 latency,
       backed by PostgreSQL with Redis caching layer"

BAD:  "Used multithreading"
GOOD: "Reduced log processing time from 45s → 8s (5.6x) using ExecutorService
       with 4 threads and BlockingQueue-based producer-consumer pipeline"
```

---

## GitHub Portfolio — What Recruiters Actually Check

```
CHECK 1: Is the profile active? (Green squares on contribution graph)
  → Commit something every day. Even a small fix.
  → Consistency signals work ethic.

CHECK 2: Are the READMEs good?
  → Every project needs: What it is, Why it exists, Architecture diagram,
    How to run it locally (one-command preferred), Screenshots/demo GIF

CHECK 3: Do the projects actually run?
  → Every project must have a working Docker Compose or Makefile
  → README setup must work in < 5 minutes
  → Broken projects = immediate credibility loss

CHECK 4: Is there a pinned project showcase?
  → Pin your 6 best projects (Settings → Pinned)
  → These appear first on your profile

PERFECT README STRUCTURE:
  # Project Name
  > One-sentence description of what it does and why it exists.

  ## Live Demo / Architecture
  [Screenshot or architecture diagram]

  ## What This Solves
  [Real-world problem in 2-3 sentences]

  ## Tech Stack
  [Table: Layer | Technology | Why]

  ## Key Features
  [3-5 bullet points: specific, metric-driven]

  ## Quick Start
      git clone ...
      docker-compose up
      # API available at http://localhost:8000
      # Swagger UI at http://localhost:8000/docs

  ## Architecture Decisions
  [Link to ADR files]

  ## Benchmark Results
  [Table or screenshot]

  ## Blog Post
  [Link to detailed write-up]
```

---

---

# 🟣 DIMENSION 6: MOCK INTERVIEW FRAMEWORK

---

## 20-Session Mock Interview Plan

### Coding Rounds (10 Sessions)

```
SESSION FORMAT (45 minutes each):
  0:00–5:00   Read the problem. Ask clarifying questions aloud.
  5:00–10:00  State your approach before coding. Discuss trade-offs.
  10:00–35:00 Write code. Explain every significant line as you write it.
  35:00–40:00 Test with provided examples + at least 2 edge cases.
  40:00–45:00 Discuss time and space complexity. Suggest optimisations.

RULE: You must talk the entire time. Silence = fail signal.
RULE: If stuck, say "I'm going to start with a brute force approach 
      to validate my understanding, then optimise."
RULE: Always mention edge cases before starting: null input, empty,
      single element, all same elements, negative numbers.
```

**Sessions 1–5: Self-timed (use a timer)**
- Pick 2 Medium problems from your weakest patterns
- Set a 45-minute timer
- Record yourself on phone/screen (review later)
- After: review what you said, identify silence gaps

**Sessions 6–10: With a partner**
- Use **Pramp.com** (free peer mock interviews — real people)
- Use **Interviewing.io** (free practice with engineers)
- After each: fill in `interview-prep/mock-interview-log.md`

### System Design Rounds (5 Sessions)

```
Pick one system per session. 45 minutes. One pen + Excalidraw.

Session 1: Design Twitter
Session 2: Design YouTube
Session 3: Design Uber
Session 4: Design WhatsApp
Session 5: Design Google Search Autocomplete

After each: photograph your diagram. Write a 500-word
design decision document. Push to GitHub.
```

### Behavioral Rounds (5 Sessions)

```
Session 1: Amazon LP round simulation (2 questions, 30 min each)
Session 2: Google Googliness round (3 questions, 20 min each)
Session 3: Microsoft values round
Session 4: Mixed company simulation
Session 5: Full interview with partner — all 3 rounds in sequence
```

---

## Mock Interview Log Template

```markdown
# Mock Interview Log — Session XX

**Date:** YYYY-MM-DD
**Format:** Coding / System Design / Behavioral
**Partner:** Self-timed / Pramp / Friend

## Problem(s)
1. [Problem name and source]

## What Went Well
[2-3 specific things]

## What to Improve
[2-3 specific things]

## Time Analysis
- Time to first idea: X minutes
- Time to working code: Y minutes
- Time spent silent: Z minutes (target: 0)

## Pattern Gaps Revealed
[Which pattern did this expose as weak?]

## Next Action
[What will I practice this week as a result?]
```

---

---

# 📋 DIMENSION 7: THE DAILY SCHEDULE — ALL TRACKS COMBINED

## How to Run All Tracks in Parallel

```
THIS IS YOUR DAILY SCHEDULE (4.5 hours total — non-negotiable):

6:00–6:45  DSA (45 min)
  → NeetCode.io, timed, document solution afterward
  → This runs EVERY SINGLE DAY for the entire 75-day journey

7:00–9:00  Main Roadmap Topic (2 hours)
  → Whichever phase of Java/Python/System Design/OS/DB you're in
  → Build the day's code, push to GitHub

9:00–9:30  SQL Practice (30 min, 3x per week)
  → Monday/Wednesday/Friday only
  → HackerRank SQL or StrataScratch

Evening:
19:00–19:30  Documentation (30 min daily)
  → Write day's .md file, push to GitHub
  → Post LinkedIn TIL update

19:30–20:00  Behavioral (30 min, twice a week)
  → Tuesday/Thursday: practice one STAR story out loud

Weekend:
Saturday:  Mock interview session (45–60 min)
Sunday:    ADR + weekly review + blog post draft
```

---

## Weekly Progress Tracker

Track this every Sunday in `progress/week-XX.md`:

```markdown
# Week XX Progress Report
**Date range:** YYYY-MM-DD to YYYY-MM-DD

## DSA
- Problems solved this week: X/7
- New patterns learned: [list]
- Hardest problem: [name] — approach: [one sentence]
- Weakness identified: [pattern]

## Main Roadmap
- Phase: [current phase]
- Days completed: X/7
- Code committed: [Y commits]
- Project progress: [status]

## SQL
- Problems solved: X/3
- Hardest concept this week: [topic]

## Behavioral
- Stories practiced: X/2
- New story refined: [story #]

## Mock Interviews
- Sessions done: X
- Key feedback: [one insight]

## Blog/Documentation
- Blog posts published: X
- LinkedIn posts: X

## Next Week Priorities
1.
2.
3.
```

---

---

# 🎯 THE COMPLETE READINESS CHECKLIST — All 13 Dimensions

Print this and check off each item as you complete it:

## Tier 1 MNC Entry-Level — Full Checklist

```
DIMENSION 1: DSA
  [ ] 100+ LeetCode problems solved (Easy: fluent, Medium: comfortable)
  [ ] All 14 patterns practiced with template memorised
  [ ] LRU Cache implemented from scratch without reference
  [ ] Can solve Easy in 10 min, Medium in 20–25 min consistently
  [ ] 10+ timed sessions completed
  [ ] Solutions documented on GitHub with complexity analysis

DIMENSION 2: CORE JAVA
  [ ] JVM memory model: can explain without notes
  [ ] HashMap internals: hash → index → collision → resize
  [ ] Streams API: GroupingBy, flatMap, reduce used in real project
  [ ] ExecutorService: built multi-threaded app that works correctly
  [ ] Spring Boot API with JPA, JWT, and tests running on Docker
  [ ] 6 projects on GitHub with READMEs

DIMENSION 3: CORE PYTHON
  [ ] GIL, generators, decorators: can explain to a 10-year-old
  [ ] asyncio: written concurrent HTTP fetcher that actually works
  [ ] FastAPI + Celery app deployed with Docker
  [ ] Published at least one package (even to TestPyPI)
  [ ] 6 projects on GitHub with READMEs

DIMENSION 4: SYSTEM DESIGN
  [ ] Can design Twitter from scratch in 45 min
  [ ] Can design YouTube, Uber, WhatsApp similarly
  [ ] 7+ Excalidraw diagrams in GitHub designs/ folder
  [ ] 5+ ADRs documenting design decisions with tradeoffs

DIMENSION 5: OS + NETWORKING
  [ ] OSI model: can explain each layer with a real tool that uses it
  [ ] TCP 3-way handshake: can draw it and explain why HOL blocking happens
  [ ] Built working Unix shell (fork/exec/pipe)
  [ ] Built working HTTP load balancer

DIMENSION 6: DATABASE ENGINEERING
  [ ] B-Tree vs LSM Tree: can explain write/read amplification tradeoff
  [ ] MVCC: can explain how PostgreSQL handles concurrent reads/writes
  [ ] EXPLAIN ANALYZE: ran it, understood the output, created an index

DIMENSION 7: DATA ENGINEERING
  [ ] Apache Airflow DAG: built one that runs on schedule
  [ ] Kafka producer + consumer: built real event pipeline
  [ ] Real-Time ETL project documented and working

DIMENSION 8: SQL UNDER PRESSURE
  [ ] 30 timed SQL problems solved (15 min each)
  [ ] Window functions: RANK, LAG, LEAD, RUNNING TOTAL used in project
  [ ] Recursive CTE: written and understood
  [ ] StrataScratch or HackerRank SQL track completed

DIMENSION 9: LOW-LEVEL DESIGN
  [ ] Parking Lot: designed and implemented
  [ ] Library System: designed and implemented
  [ ] 4 additional LLD designs documented (ATM, Chess, Food Order, Ride Share)
  [ ] SOLID principles applied visibly in at least 2 projects

DIMENSION 10: BEHAVIORAL
  [ ] 8 STAR stories written, each under 2 minutes when spoken
  [ ] Amazon LP mapping: each story mapped to a principle
  [ ] Recorded yourself 3+ times answering behavioral questions
  [ ] 5 mock behavioral interviews completed

DIMENSION 11: DEVOPS/CLOUD
  [ ] Every project has a working Dockerfile
  [ ] GitHub Actions CI pipeline running (lint → test → build)
  [ ] Kubernetes deployment manifests written for at least 1 project
  [ ] Prometheus + Grafana dashboard screenshot in at least 1 README

DIMENSION 12: RESUME + PORTFOLIO
  [ ] Resume reviewed and formatted with metric-driven bullets
  [ ] GitHub pinned repos showing 6 best projects
  [ ] Every pinned project has a complete README
  [ ] LinkedIn profile matches resume, has project links
  [ ] At least 5 blog posts published (Dev.to or Hashnode)

DIMENSION 13: COMMUNICATION
  [ ] 1 recorded "project walkthrough" video per major project
  [ ] Technical writing: blog posts show you can explain concepts clearly
  [ ] Can explain: CAP Theorem, ACID, Raft, MVCC in simple English
  [ ] Active Recall: fill out the daily template every single day
```

---

## Final Score After Completing This Plan

| Dimension | Target | How It's Proven |
|---|---|---|
| DSA / LeetCode | **10/10** | 100+ problems, GitHub solutions, timed results |
| Core Java + Spring Boot | **9/10** | 6 projects + Spring Boot API with auth and tests |
| Core Python + FastAPI | **9/10** | 6 projects + published PyPI package |
| System Design | **10/10** | 7 designed systems + diagrams + ADRs |
| OS + Networking | **10/10** | Shell + Load Balancer + OS roadmap |
| Database Engineering | **10/10** | DB roadmap + internals + custom malloc |
| Data Engineering | **10/10** | ETL + Kafka + Airflow + ClickHouse |
| SQL Under Pressure | **9/10** | 30 timed problems + window functions in projects |
| Low-Level Design | **9/10** | 6 LLD designs documented and coded |
| Behavioral Interview | **9/10** | 8 STAR stories + 5 mock sessions |
| DevOps / Cloud | **9/10** | Docker + K8s + CI/CD across all projects |
| Resume + Portfolio | **10/10** | Polished resume + active GitHub + blog |
| Communication | **9/10** | Blog posts + recordings + daily documentation |
| **OVERALL TIER 1 MNC READINESS** | **9.5/10** | Documented, verifiable, comprehensive |

---

> ## 🔑 The One Truth About This Entire Journey
>
> Most candidates who fail Tier 1 MNC interviews are not unintelligent. They either:
> (a) Prepared only DSA with no real projects, or
> (b) Built impressive projects but cannot solve algorithmic problems under pressure.
>
> You will be the rare candidate who does both — deeply.
>
> **The portfolio proves you can build. The DSA proves you can think algorithmically under pressure. The behavioral stories prove you can work in a team. The system design proves you can think at scale. Together, they make a candidate that any engineering team would want.**
>
> Document every day. Every commit tells the story. Every blog post adds a chapter.
> The journey IS the proof.

---

*Tier 1 MNC Gap Filler — Complete Readiness Plan*  
*Covers: DSA (14 patterns, 8 weeks) · SQL (30 timed problems) · LLD (6 designs) · Behavioral (8 STAR stories) · Resume · Mock Interviews · Daily Schedule*  
*Target: 9–10/10 across all evaluation dimensions for Google, Amazon, Microsoft, Meta, Uber*