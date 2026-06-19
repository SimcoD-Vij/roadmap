In technical interviews, the definition of a "package" or "library" usually refers to the language's **built-in standard libraries**. Top companies explicitly forbid third-party frameworks (like Spring Boot or Django) in core Data Structures and Algorithms (DSA) rounds because they want to evaluate your core logic, not your framework knowledge.

Here is the exhaustive list of packages and modules you are expected to use in Java and Python coding interviews.

## Python: Essential Interview Modules

Python is heavily favored in interviews because its standard library acts like a cheat sheet for DSA. You do not need to `pip install` these; they are built-in and universally supported on platforms like LeetCode, HackerRank, and CodeSignal.

* **`collections` (The most critical module):**
* `deque`: Essential for O(1) queue operations, Breadth-First Search (BFS), and sliding window problems. (Never use standard lists for queues).
* `Counter`: Instantly creates frequency maps of strings or arrays.
* `defaultdict`: Handles missing dictionary keys automatically (crucial for graph adjacency lists).


* **`heapq`:** Provides Min-Heap functions (`heappush`, `heappop`, `heapify`). Essential for Top-K problems, priority queues, and Dijkstra's algorithm. (Multiply by -1 to simulate a Max-Heap).
* **`math`:**
* `math.inf` / `-math.inf`: Used for initializing max/min boundary values.
* `math.gcd`, `math.ceil`, `math.floor`, `math.factorial`.


* **`functools`:**
* `@lru_cache(None)` or `@cache`: Instantly adds memoization to recursive functions, converting standard recursion into Top-Down Dynamic Programming with one line of code.
* `cmp_to_key`: Used for custom sorting logic.


* **`bisect`:** Provides `bisect_left` and `bisect_right` for executing binary search on sorted arrays without writing the `while` loop manually.
* **`itertools`:** Used for brute-force or combinatorial problems (`permutations`, `combinations`, `accumulate` for prefix sums).
* **`sys`:**
* `sys.setrecursionlimit(106)`: Mandatory on platforms like HackerRank if you are doing deep Depth-First Search (DFS) on large trees/graphs, as Python's default recursion limit is 1000.
* `sys.maxsize`: Alternative to `math.inf`.


* **`typing`:** Used for type hinting (`List`, `Dict`, `Optional`), which is the standard boilerplate on LeetCode.
* **`copy`:** `copy.deepcopy()` is used when you need to clone complex objects or graphs.
* **`string`:** `string.ascii_lowercase` and `string.digits` are useful for string manipulation and trie problems.

## Java: Essential Interview Packages

In Java, you rely entirely on the Java Class Library. You must manually import these (e.g., `import java.util.*;`), though platforms like LeetCode hide the imports.

* **`java.util` (The Core Framework):**
* **Lists:** `ArrayList`, `LinkedList`.
* **Maps & Sets:** `HashMap`, `HashSet` (O(1) lookups), `LinkedHashMap` (maintains insertion order, vital for LRU Cache design).
* **Trees:** `TreeMap`, `TreeSet` (Backed by Red-Black trees; essential when you need dynamically sorted data and O(log n) lookups).
* **Queues:** `PriorityQueue` (Min-Heap by default), `Queue`, `Deque`, `ArrayDeque`.
* **Utility Classes:** `Arrays` (`Arrays.sort()`, `Arrays.fill()`, `Arrays.copyOf()`) and `Collections` (`Collections.reverse()`, `Collections.sort()`).


* **`java.lang` (Automatically Imported):**
* `StringBuilder`: **Mandatory** for string manipulation. Using standard `String` concatenation (`+`) inside a loop creates O(n²) time complexity and will fail hidden test cases.
* `Math`: `Math.max()`, `Math.min()`, `Math.abs()`, `Math.pow()`.
* Wrapper classes: `Integer` (`Integer.MAX_VALUE`, `Integer.MIN_VALUE`), `Character` (`Character.isLetterOrDigit()`).


* **`java.io` & `java.util.Scanner`:** Essential for HackerRank or offline IDE interviews where you must parse your own standard input. `BufferedReader` and `StringTokenizer` are highly recommended over `Scanner` for faster I/O execution.
* **`java.util.concurrent` (For Advanced/LLD Rounds):** `ConcurrentHashMap`, `ReentrantLock`, and `AtomicInteger`. Rarely used in standard DSA, but heavily tested in Machine Coding rounds.
* **`java.util.stream`:** The Streams API (`IntStream`, `Collectors`) is increasingly expected for concise mapping and filtering, though standard loops are always acceptable.

---

## Product-Based vs. Service-Based Testing Standards

How these packages are tested varies significantly depending on the tier of the company.

| Factor | Product-Based MNCs (Google, Amazon, Uber, Meta) | Service-Based Companies (TCS, Infosys, Wipro, Accenture) |
| --- | --- | --- |
| **Platform Environment** | Custom portals, LeetCode, or HackerRank. No boilerplate provided in Machine Coding rounds. | Amcat, Mettl, HackerEarth. Often strict environments with limited package whitelisting. |
| **Package Mastery** | **Expected.** If you write a manual binary search when `bisect` exists (unless asked), or fail to use `StringBuilder` in Java, interviewers view it as a lack of language fluency. | **Basic.** Deep knowledge of `heapq` or `TreeMap` is rarely tested. Focus is heavily on standard arrays, `HashMap`/`dict`, and basic loops. |
| **Machine Coding / LLD** | Requires building fully functional CLI apps (e.g., designing a Parking Lot) in 90 minutes. You must use `java.util.concurrent` or Python OOP natively. **No external frameworks allowed.** | Very rare. Rounds focus more on standard debugging, basic output guessing, and fundamental SQL queries. |
| **Data/Specialized Roles** | If interviewing for Data Science/Engineering, platforms will explicitly enable third-party packages like **Pandas**, **NumPy**, and **SciPy** for data manipulation questions. | Specialized roles often rely on multiple-choice questions for framework knowledge rather than live coding. |
| **Custom I/O parsing** | Usually pre-parsed (LeetCode style) where you just complete a function/method. | Often requires you to read from `System.in` or `sys.stdin` manually. You must know `Scanner`/`BufferedReader` or `input().split()`. |
