# Method Overlap Comparison — Which One to Use, and Why
### Java & Python — Same Job, Different Methods, Different Trade-offs

> This file groups methods **by the task they perform**, not by class. Many classes offer near-duplicate functionality with different time complexity, null/exception behavior, or mutability. Picking the wrong one is a common silent bug or a "why did you not use X" interview follow-up.

---

# PART 1 — JAVA

---

## 1. Stack / Queue / Deque — "Which class for push/pop/peek?"

| Need | Method/Class options | Use | Why | Exception behavior |
|------|----------------------|-----|-----|---------------------|
| Stack (LIFO) | `Stack<E>` (legacy, extends Vector) vs `ArrayDeque<E>` vs `LinkedList<E>` | **`ArrayDeque`** | `Stack` is synchronized (legacy, every op pays a lock cost you don't need single-threaded). `ArrayDeque` is unsynchronized, backed by a resizable array, faster, and is the class the Java docs themselves recommend over `Stack`. `LinkedList` works but allocates a node object per element — more GC pressure. | `ArrayDeque.pop()`/`.peek()` throw `NoSuchElementException` if empty — always check `isEmpty()` first or use `poll()`/`peek()` (queue-style, returns `null`) when you want a null instead of an exception. |
| Queue (FIFO) | `LinkedList<E>` vs `ArrayDeque<E>` vs `java.util.Queue` interface | **`ArrayDeque`** | Same reasoning — `ArrayDeque` beats `LinkedList` for queue ops because there's no per-node allocation; only resize the backing array occasionally (amortized O(1)). | `offer()`/`poll()` never throw — return `false`/`null`. `add()`/`remove()`/`element()` throw on failure. In interviews, prefer `offer`/`poll`/`peek` (the "doesn't throw" family) unless you specifically want a fail-fast signal. |
| Double-ended ops | `Deque<E>` interface — multiple implementing classes | **`ArrayDeque`** | Same as above; `ArrayDeque` implements `Deque` and is the standard choice. | `addFirst`/`addLast` throw `IllegalStateException` if the deque is capacity-restricted and full (rare — `ArrayDeque` is unbounded by default, so this won't fire in practice). |

**Rule of thumb:** Whenever you'd reach for `Stack` or `LinkedList` purely as a stack/queue, reach for `ArrayDeque` instead. The only reason to keep using `LinkedList` is if you need `List` operations (random access by index, `subList`) alongside queue behavior, which `ArrayDeque` does not give you.

---

## 2. "Does this exist / get me the value" — Map lookups

| Need | Method options | Use | Why | Exception/null behavior |
|------|----------------|-----|-----|--------------------------|
| Read a value that might be absent | `get(key)` vs `getOrDefault(key, default)` | **`getOrDefault`** when you have a sensible fallback (e.g., counting: `getOrDefault(k, 0) + 1`); **`get`** when absence is meaningful and you want to branch on `null` explicitly | `getOrDefault` removes a null-check branch and is the standard idiom in frequency-count / graph-adjacency interview code. `get` is correct when you later need to distinguish "key absent" from "value is the default" (e.g., default is also a valid stored value). | `get` returns `null` on a missing key (never throws). `getOrDefault` never returns `null` unless you pass `null` as the default. Neither throws `NullPointerException` for a missing key — that's a common misconception. |
| Insert only if absent | `put(key, val)` vs `putIfAbsent(key, val)` | **`putIfAbsent`** when you don't want to clobber an existing entry (e.g., "first occurrence wins") | `put` always overwrites. `putIfAbsent` is atomic-equivalent and reads cleaner than `if (!map.containsKey(k)) map.put(k, v)`. In `ConcurrentHashMap`, `putIfAbsent` is genuinely atomic — `containsKey` + `put` is not, and is a race condition under concurrency. | `putIfAbsent` returns the *existing* value if the key was present (and does not overwrite); returns `null` if the key was absent and the new value was inserted. |
| Build-or-append into a collection value | `computeIfAbsent(key, k -> new ArrayList<>())` vs manual `if (!map.containsKey(k)) map.put(k, new ArrayList<>()); map.get(k).add(v);` | **`computeIfAbsent`** | One line, no double lookup, no risk of overwriting an existing list. This is *the* standard pattern for building graph adjacency lists in interviews. | If the key exists, the mapping function is never called (so you don't pay for a wasted `new ArrayList<>()`, important to know but rarely asked). |
| Update an existing numeric value | `merge(key, 1, Integer::sum)` vs `put(key, getOrDefault(key,0)+1)` vs `compute(key, (k,v) -> v==null?1:v+1)` | **`merge`** for simple frequency-style accumulation | `merge` is the shortest, most idiomatic, and the one experienced interviewers expect to see for "count frequency" problems. `compute` is more general (use it when the update logic is more complex than a simple combine). `getOrDefault`+`put` is fine but verbose and does two map operations under the hood vs `merge`'s one (technically still O(1), but it's the less idiomatic choice in a senior interview). | `merge` removes the key entirely if the remapping function returns `null` — a subtlety worth knowing if you use `merge` for decrementing counts to zero. |

---

## 3. Sorting — `Collections.sort` vs `Arrays.sort` vs `Stream.sorted`

| Need | Method options | Use | Why | Notes |
|------|----------------|-----|-----|-------|
| Sort a `List<T>` | `Collections.sort(list)` vs `list.sort(comparator)` | **`list.sort(comparator)`** (instance method, Java 8+) | `Collections.sort` is the older static-utility style; `list.sort()` is the modern idiom and reads better when chaining. Functionally identical under the hood — `Collections.sort` literally delegates to `list.sort(null)`. | No real performance difference; this is a style/modernity preference, not a correctness one. |
| Sort a primitive array (`int[]`) | `Arrays.sort(arr)` | **`Arrays.sort`** — there is no real alternative for primitive arrays | Primitive array sort uses a **dual-pivot Quicksort** — O(n log n) average, **not stable**, and can degrade in adversarial cases (rare in interviews but a known LeetCode "TLE on sorted array" gotcha for hand-rolled quicksort, not relevant to `Arrays.sort` itself). | If you need *guaranteed* O(n log n) worst case for primitives, you'd need to implement your own (e.g., merge sort) — `Arrays.sort(int[])` does not guarantee this, unlike object array sort. |
| Sort an object array / `List<T>` | `Arrays.sort(T[] a, Comparator)` / `list.sort(Comparator)` | Either, **prefer `list.sort`** for `List`s | Object array and `List` sorts use a modified **TimSort** — O(n log n) worst case, **stable** (preserves relative order of equal elements). This matters for multi-key sort problems (sort by one field, ties broken by insertion order). | Primitive array sort (Quicksort) is NOT stable; object/List sort (TimSort) IS stable. This is the single most-confused fact in Java sorting and worth knowing cold. |
| Sort via Stream | `stream().sorted()` | Use only when you're already in a stream pipeline (e.g., `map().filter().sorted().collect()`) | `sorted()` returns a *new* stream/collection — doesn't mutate the source. Use this when you want immutability or are mid-pipeline; use `list.sort()` when you just want to sort in place and move on. | Creates a new object, slightly more overhead than in-place sort if you don't need a stream elsewhere. |

---

## 4. String building — `StringBuilder` vs `String` vs `StringBuffer`

| Need | Options | Use | Why | Exception cases |
|------|---------|-----|-----|------------------|
| Build a string in a loop | `String s += x` vs `StringBuilder.append(x)` | **`StringBuilder`**, always, inside any loop | `String` is immutable — every `+=` creates an entirely new String object, copying all prior characters. In a loop of n iterations this is **O(n²)** total work and is a textbook reason for "TLE" / hidden-test failure on large inputs. `StringBuilder` mutates an internal buffer — O(1) amortized per append, O(n) total. | None — `StringBuilder` never throws for normal append usage. `charAt`/`deleteCharAt` throw `StringIndexOutOfBoundsException` on bad indices, same as `String`. |
| Build a string from multiple threads | `StringBuilder` vs `StringBuffer` | **`StringBuilder`** unless genuinely multi-threaded | `StringBuffer` is `StringBuilder`'s synchronized twin — every method call pays a lock acquisition cost even when you're single-threaded (which is 99% of interview code). Use `StringBuffer` only if multiple threads truly append to the same buffer concurrently — exceedingly rare in DSA/interview contexts. | Same exception profile as `StringBuilder`. |

---

## 5. Equality and Comparison — `equals` vs `==` vs `compareTo` vs `Comparator`

| Need | Options | Use | Why | Gotcha |
|------|---------|-----|-----|--------|
| Compare two objects for logical equality | `==` vs `.equals()` | **`.equals()`** for any boxed type (`Integer`, `String`, `Long`...) or custom object; **`==`** only for primitives | `==` on objects compares **reference identity**, not content. `Integer` caches values -128 to 127, so `Integer a=100, b=100; a==b` is `true` by accident of caching, but `Integer a=200,b=200; a==b` is `false` — a classic interview trap. `.equals()` always compares logical value. | Forgetting to override `equals`/`hashCode` together on a custom class breaks `HashMap`/`HashSet` membership checks silently — they'll compile and run, just always return "not found." |
| Compare two `BigDecimal` values | `.equals()` vs `.compareTo()` | **`.compareTo()`**, always | `BigDecimal.equals()` considers scale significant — `new BigDecimal("1.0").equals(new BigDecimal("1.00"))` is **`false`**, because the scale (decimal places) differs even though the numeric value is identical. `compareTo()` compares numeric value only, ignoring scale. | This is one of the most commonly cited "gotchas" in Java technical interviews for finance-adjacent roles. |
| Natural ordering vs custom ordering | `Comparable<T>` (`compareTo`) vs `Comparator<T>` (`compare`) | **`Comparable`** when there's one obvious natural order owned by the class itself (e.g., `Integer` sorts numerically); **`Comparator`** when you need multiple orderings or don't own the class | `Comparable` is implemented once, inside the class, and is "the" default order (`Collections.sort(list)` uses it). `Comparator` is external, passed in, and lets you define as many orderings as you want without modifying the class — essential when sorting by different fields in different contexts. | A class can implement `Comparable` AND have several different `Comparator`s defined elsewhere for alternate sort orders — they coexist. |

---

## 6. Iteration — `for` loop vs `Iterator` vs `forEach` vs `Stream`

| Need | Options | Use | Why | Exception/mutation caveat |
|------|---------|-----|-----|----------------------------|
| Remove elements while iterating | `for-each` loop vs explicit `Iterator.remove()` | **`Iterator.remove()`** (or `removeIf`) | Removing from a `List`/`Set`/`Map` *during* a for-each loop throws `ConcurrentModificationException` — the for-each loop is sugar over an `Iterator` that detects structural modification and fails fast. `Iterator.remove()` is the only safe in-loop removal method; it updates the iterator's internal state correctly. | `ConcurrentModificationException` is thrown on the *next* call to `next()`/`hasNext()` after an unsafe structural change — not immediately at the point of modification, which can be confusing when debugging. |
| Remove by condition, no manual loop | `Iterator.remove()` vs `Collection.removeIf(Predicate)` | **`removeIf`** when the condition can be expressed as a simple predicate | Shorter, equally safe (implemented internally with a correct iterator), and more readable. Reach for manual `Iterator` only when you need to do something else (like collect removed items) during the same pass. | None beyond standard `ConcurrentModificationException` rules, which `removeIf` itself is exempt from since it manages its own safe iteration. |

---

## 7. Multithread-safe collections — three different strategies

| Need | Options | Use | Why | Trade-off |
|------|---------|-----|-----|-----------|
| Thread-safe Map | `Hashtable` (legacy) vs `Collections.synchronizedMap(new HashMap<>())` vs `ConcurrentHashMap` | **`ConcurrentHashMap`** | `Hashtable` is legacy, synchronizes the entire map on every operation (coarse locking) and doesn't allow null keys/values. `synchronizedMap` wraps any map with a single lock — same coarse-locking problem, plus you must manually synchronize during iteration. `ConcurrentHashMap` uses fine-grained internal locking (bucket-level in modern JDKs) — much better throughput under contention, and provides atomic compound operations (`putIfAbsent`, `computeIfAbsent`, `merge`) that are genuinely thread-safe, unlike a check-then-act pattern on a synchronized map. | `ConcurrentHashMap` does *not* allow `null` keys or values (throws `NullPointerException`) — this is a deliberate design choice to avoid ambiguity between "absent" and "present but null" under concurrent access. |
| Thread-safe List | `Vector` (legacy) vs `Collections.synchronizedList` vs `CopyOnWriteArrayList` | **`CopyOnWriteArrayList`** for read-heavy/write-rare; `synchronizedList` for balanced read/write | `Vector` is legacy, same coarse-lock-everything cost as `Hashtable`. `CopyOnWriteArrayList` copies the entire backing array on every write — expensive writes, but reads need no locking at all and iteration never throws `ConcurrentModificationException`. Use it for things like a list of event listeners (read constantly, modified rarely). | If writes are frequent, `CopyOnWriteArrayList`'s O(n) copy-per-write cost makes it the wrong choice — fall back to `synchronizedList` or restructure the problem. |

---

## 8. Reading input — `Scanner` vs `BufferedReader`+`StringTokenizer`

| Need | Options | Use | Why | When `Scanner` is fine |
|------|---------|-----|-----|--------------------------|
| Parse competitive-programming-scale input (HackerRank, large n) | `Scanner` vs `BufferedReader` + `StringTokenizer` | **`BufferedReader` + `StringTokenizer`** for anything beyond small/medium input sizes | `Scanner` uses regex internally for tokenizing (`nextInt()`, `next()`), which carries real overhead — on inputs with 10⁵–10⁶ tokens this can be the difference between passing and timing out. `BufferedReader.readLine()` + `StringTokenizer` is dramatically faster because it avoids regex matching entirely. | For LeetCode-style problems (parsed function args, no manual I/O) or small/casual inputs in interviews where performance of I/O parsing itself is not the point being tested, `Scanner` is perfectly fine and more readable. |

---

---

# PART 2 — PYTHON

---

## 1. Queue/Stack — `list` vs `collections.deque`

| Need | Options | Use | Why | Exception/return behavior |
|------|---------|-----|-----|----------------------------|
| Stack (LIFO) | `list.append()`/`list.pop()` vs `deque.append()`/`deque.pop()` | **Either is fine** — both are O(1) at the *right* end | `list.pop()` (no index, i.e. pops the last element) is O(1) amortized, same as `deque.pop()`. There's no meaningful performance difference for stack-only use. `list` is the more common/idiomatic choice for a stack in Python interview code. | `list.pop()` on an empty list raises `IndexError`. `deque.pop()` on an empty deque also raises `IndexError`. Identical failure mode. |
| Queue (FIFO) | `list.pop(0)` vs `deque.popleft()` | **`deque.popleft()`**, never `list.pop(0)` | `list.pop(0)` removes the first element by shifting every remaining element left by one index — **O(n)** per call. `deque.popleft()` is a true **O(1)** operation because `deque` is implemented as a doubly-linked block structure under the hood. Using `list` as a queue is one of the most common silent-performance-bug patterns in Python interview code — it'll pass small test cases and time out on large ones. | Neither throws differently; `deque.popleft()` on empty raises `IndexError`, same as `list.pop(0)`. The issue is purely complexity, not correctness. |
| BFS frontier | `list` vs `deque` | **`deque`**, always | BFS repeatedly removes from the front — exactly the O(n) trap above, compounded across every level of the BFS. This silently turns an O(V+E) BFS into O(V²) in the worst case. | — |

---

## 2. Dict lookups — `dict[key]` vs `.get()` vs `defaultdict` vs `setdefault`

| Need | Options | Use | Why | Exception/return behavior |
|------|---------|-----|-----|----------------------------|
| Read a value that might be absent | `d[key]` vs `d.get(key, default)` | **`.get(key, default)`** when absence is expected and recoverable; **`d[key]`** when absence indicates a bug and you *want* the program to fail loudly | `d[key]` raises `KeyError` on a missing key — sometimes that's exactly the behavior you want (fail fast on a programming error). `.get()` silently returns `None` (or your default) — appropriate for "this key may or may not exist, and that's a normal case." | `KeyError` vs silent `None` — choosing wrong means either an unexpected crash (using `[]` on uncertain data) or a silently wrong answer (using `.get()` and accidentally treating `None` as valid data downstream). |
| Build-or-append into a dict-of-lists | `defaultdict(list)` vs `dict.setdefault(key, [])` vs manual `if key not in d` | **`defaultdict(list)`** for repeated heavy use (e.g., building a whole graph); **`setdefault`** for a single one-off insert | `defaultdict` sets the default factory once at creation and every subsequent missing-key access is automatic — cleanest for graph-building loops. `setdefault(key, [])` does the same job per-call but **always constructs the empty list as the default argument**, even when the key already exists and the default is discarded — a real (if small) wasted allocation on every call, and easy to forget the second argument and get a `TypeError`. For a single conditional insert, `setdefault` avoids importing `defaultdict` and is fine. | `defaultdict` will silently create an entry for a key the moment you even *read* `d[some_missing_key]` (not just write) — this can be a subtle bug if you're checking existence elsewhere and didn't intend to create the entry. `dict.get()` does not have this side effect. |
| Count frequency | `Counter(iterable)` vs `defaultdict(int)` + manual increment vs plain `dict` + `.get(k,0)+1` | **`Counter`** for a one-shot frequency map from an iterable; **`defaultdict(int)`** when you're accumulating counts incrementally across a more complex loop | `Counter(iterable)` builds the entire frequency map in one C-optimized call — fastest and shortest for "count all elements" as a single step. `defaultdict(int)` is better when the counting is interleaved with other per-element logic in the loop body. Plain `dict.get(k,0)+1` works but is the most verbose and is rarely the "best" choice in an interview unless you deliberately want to avoid imports. | `Counter[missing_key]` returns `0` (does NOT raise `KeyError`, unlike a plain `dict`) — but unlike `defaultdict`, this lookup does **not** insert the key into the Counter. This is a genuinely useful, non-obvious distinction. |

---

## 3. Sorting — `list.sort()` vs `sorted()` vs `heapq.nlargest/nsmallest`

| Need | Options | Use | Why | Notes |
|------|---------|-----|-----|-------|
| Sort a list in place | `list.sort()` vs `sorted(list)` | **`list.sort()`** when you don't need the original order preserved and want to avoid an extra copy | `list.sort()` mutates in place, returns `None`, O(n log n), no extra memory beyond Timsort's working space. `sorted()` returns a **new** list, leaving the original untouched, and works on any iterable (not just lists — e.g., you can `sorted(some_dict.items())`). | If you accidentally write `arr = arr.sort()` you get `None` — a very common beginner bug since `.sort()` returns `None` by design (mutates in place, doesn't return self). |
| Get just the top-K largest/smallest | `sorted(list)[-k:]` vs `heapq.nlargest(k, list)` | **`heapq.nlargest`/`nsmallest`** when `k` is small relative to `n` | `sorted()` is O(n log n) regardless of k. `heapq.nlargest(k, iterable)` is O(n log k) — meaningfully faster when k is small (e.g., top-10 of a million elements). When k approaches n, the gap closes and `sorted()` is simpler to reach for. | `heapq.nlargest`/`nsmallest` accept a `key` parameter just like `sorted()`, so they're drop-in replacements for the "give me top-k" use case specifically. |
| Both ascending and descending need | `sorted(list, reverse=True)` vs `sorted(list)[::-1]` | **`sorted(..., reverse=True)`** | Doing `reverse=True` is computed correctly during the sort (stable, same comparisons) and is O(n log n) total. `[::-1]` after an ascending sort does an *additional* O(n) reversal pass — strictly more work, and changes stability semantics for equal elements (their relative order flips too, which `reverse=True` actually preserves correctly per Python's documented stable-sort behavior). | For most interview-sized inputs the performance difference is invisible, but `reverse=True` is the textbook-correct idiom and signals familiarity with the language to an interviewer. |

---

## 4. Binary search — `bisect` vs manual `while lo <= hi`

| Need | Options | Use | Why | Gotcha |
|------|---------|-----|-----|--------|
| Find insertion point / first occurrence in a sorted list | `bisect.bisect_left` vs hand-rolled binary search | **`bisect_left`/`bisect_right`** whenever the problem is genuinely "search a sorted array" | Standard library binary search is implemented in C (in CPython), correctly handles all edge cases (empty list, all-equal elements, value not present), and removes an entire class of off-by-one bugs that hand-rolled binary search is notorious for in interviews. | Interviewers sometimes *explicitly* want you to hand-roll binary search to demonstrate you understand the mechanics — read the question. If the prompt says "implement binary search," don't import `bisect`; if it says "find the number of elements less than X in a sorted array," `bisect` is the expected, idiomatic tool. |
| `bisect_left` vs `bisect_right` for duplicates | Both exist for a reason | **`bisect_left`** = first valid insertion point before any equal elements (= count of elements strictly less than x). **`bisect_right`** = insertion point after all equal elements (= count of elements ≤ x). | Mixing these up is the single most common `bisect`-related interview bug — e.g., counting "elements less than or equal to x" using `bisect_left` undercounts by the number of exact matches. | Memorize: `bisect_left` → "less than", `bisect_right` → "less than or equal to", when counting. |

---

## 5. Memoization — `functools.lru_cache`/`@cache` vs manual `dict`

| Need | Options | Use | Why | Limitation |
|------|---------|-----|-----|------------|
| Memoize a recursive function | `@lru_cache(maxsize=None)` / `@cache` vs manual `memo = {}` dict passed through recursive calls | **`@cache`/`@lru_cache(None)`** whenever the function's arguments are hashable | One decorator line replaces an entire manual memo-dict pattern, is implemented in C, and is faster than a hand-rolled dict-based memo in most cases. This is the single highest-leverage Python interview trick for converting brute-force recursion into Top-Down DP. | **Arguments must be hashable** — `@lru_cache` will raise `TypeError: unhashable type` if you pass a `list` or `dict` as an argument. For problems with mutable/unhashable state (e.g., a grid passed as a list of lists), you must either convert to a tuple of tuples first, or fall back to a manual `dict` keyed by a hashable representation of the state. |
| Memoize with size control | `@lru_cache(maxsize=128)` (default) vs `@lru_cache(maxsize=None)`/`@cache` | **`maxsize=None`/`@cache`** for interview/competitive problems (you generally want every computed subproblem retained); bounded `maxsize` is for production code managing memory | The *default* `maxsize` if you just write `@lru_cache()` with no argument is 128 — silently evicting old entries via LRU policy once you exceed it. In a DP problem with more than 128 distinct subproblems, this silently breaks memoization (recomputation happens again, function still "works" but is slow) — an easy and dangerous-because-silent mistake. | Always explicitly write `@lru_cache(maxsize=None)` or `@cache` (3.9+) in interview code — never rely on the bare `@lru_cache()` default. |

---

## 6. Copying — `copy.copy` vs `copy.deepcopy` vs slicing `[:]` vs `list(x)`

| Need | Options | Use | Why | Failure mode if wrong choice |
|------|---------|-----|-----|-------------------------------|
| Copy a flat list of immutables (ints, strings) | `lst[:]` vs `list(lst)` vs `copy.copy(lst)` | **Any of `lst[:]` or `list(lst)`** — both are idiomatic, equally fast, shallow | For a list of immutable elements, "shallow" and "deep" copy are equivalent in effect since the elements can't be mutated in place anyway. `copy.copy()` works too but is more typing for no benefit here. | None — all three are correct and equally safe for this case. |
| Copy a 2D grid / nested list (mutable inner lists) | `grid[:]` vs `copy.copy(grid)` vs `copy.deepcopy(grid)` vs `[row[:] for row in grid]` | **`copy.deepcopy(grid)`** for correctness in general, **`[row[:] for row in grid]`** for speed when you know the nesting is exactly 2 levels | `grid[:]` and `copy.copy(grid)` are **shallow** — they copy the outer list, but the inner row lists are still the *same objects*, shared between original and "copy." Mutating `copy[0][0]` will also mutate `original[0][0]` — a classic, silent graph/grid-traversal bug. `copy.deepcopy` recursively copies every level and is always correct but slower (works for arbitrary nesting depth and even handles cycles via internal memo). The list-comprehension version is faster than `deepcopy` because it skips `deepcopy`'s generality overhead, but only works correctly if you know there are exactly 2 levels of nesting. | Using a shallow copy when you needed a deep one is a textbook silent-bug — code runs, produces a *plausible-looking* but wrong answer, because both "copies" of the grid actually point to the same mutable rows. |

---

## 7. Iteration with index — `range(len(x))` vs `enumerate(x)`

| Need | Options | Use | Why | — |
|------|---------|-----|-----|---|
| Need both index and value | `for i in range(len(lst)): x = lst[i]` vs `for i, x in enumerate(lst)` | **`enumerate(lst)`** | `enumerate` is more Pythonic, avoids a separate indexing operation per iteration (`lst[i]` is itself a lookup; `enumerate` yields the value directly during iteration), and is what interviewers expect from someone fluent in the language. | `enumerate(lst, start=1)` lets you start the index at any value — useful for 1-indexed problems without manual `+1` everywhere. |

---

## 8. String building — `+=` in a loop vs `''.join(list)`

| Need | Options | Use | Why | Exception cases |
|------|---------|-----|-----|------------------|
| Build a string incrementally in a loop | `s += char` repeatedly vs append to a `list` and `''.join(list)` at the end | **Append to a list, `''.join()` once at the end** | Python strings are immutable, same root cause as Java. Repeated `+=` in a loop is **O(n²)** in the worst case across many implementations/versions (CPython has some internal optimizations for the single-threaded, single-reference case that can make this closer to amortized O(n) in practice for `str +=` specifically — but this optimization is an implementation detail, not a language guarantee, and does not apply to other approaches like building a string by concatenating in a comprehension). `list.append()` + `''.join()` is **guaranteed O(n)** regardless of implementation, and is the portable, always-correct idiom taught for interviews. | None directly, but relying on CPython's `str +=` optimization is risky — it does not apply on every Python implementation (e.g., PyPy, Jython) and an interviewer testing your fundamentals understanding will expect you to know `join` is the textbook-correct answer. |

---

## 9. Recursion depth — when default Python recursion silently fails

| Need | Options | Use | Why | Gotcha |
|------|---------|-----|-----|--------|
| Deep recursion (deep tree, long linked list, large grid DFS) | Default recursion limit (1000) vs `sys.setrecursionlimit(10**6)` | **Set `sys.setrecursionlimit(10**6)`** at the top of any solution involving DFS/recursion on inputs that could be large (n > ~900) | Python's default recursion limit is only 1000 frames — far lower than Java's effective stack depth for equivalent code, and far lower than what many "medium" sized interview inputs require (e.g., DFS on a skewed binary tree with 10,000 nodes, or a linked list of length 10,000). Hitting the limit raises `RecursionError`, which silently looks like a correctness bug rather than a depth-limit issue if you don't already know to suspect it. | Raising the recursion limit does NOT raise the actual OS thread stack size — for extremely deep recursion (100,000+ frames) you can still get a hard **segmentation fault** (not even a catchable Python exception) regardless of `setrecursionlimit`. For very deep recursion, converting to an **iterative** approach with an explicit stack (`collections.deque` or `list`) is the truly safe fix, not just raising the limit. |

---

---

## QUICK-SCAN SUMMARY TABLE — Java

| Task | Pick this | Skip this | One-line reason |
|------|-----------|-----------|------------------|
| Stack/Queue | `ArrayDeque` | `Stack`, `LinkedList` | No sync overhead, no per-node allocation |
| Frequency count | `map.merge(k, 1, Integer::sum)` | `get`+`put` manually | Shortest, idiomatic, single map op |
| Build adjacency list | `map.computeIfAbsent(k, x -> new ArrayList<>())` | manual containsKey check | One line, no double lookup |
| LRU Cache | `LinkedHashMap` (access-order) | manual list+map combo | Built-in eviction via `removeEldestEntry` |
| String building in loop | `StringBuilder` | `String +=` | O(n) vs O(n²) |
| Decimal comparison | `BigDecimal.compareTo()` | `BigDecimal.equals()` | `.equals()` is scale-sensitive |
| Sort a `List` | `list.sort(comparator)` | `Collections.sort` | Same result, modern idiom |
| Remove while iterating | `Iterator.remove()` / `removeIf` | for-each + `list.remove()` | Avoids `ConcurrentModificationException` |
| Thread-safe Map | `ConcurrentHashMap` | `Hashtable`, `synchronizedMap` | Fine-grained locking, atomic compound ops |
| Large input parsing | `BufferedReader`+`StringTokenizer` | `Scanner` | No regex overhead |

---

## QUICK-SCAN SUMMARY TABLE — Python

| Task | Pick this | Skip this | One-line reason |
|------|-----------|-----------|------------------|
| Queue / BFS | `collections.deque` | `list.pop(0)` | O(1) vs O(n) per pop |
| Frequency count | `collections.Counter` | manual `dict` + `get(k,0)+1` | One-shot, C-optimized |
| Graph adjacency list | `collections.defaultdict(list)` | `dict.setdefault` in a loop | No wasted default-arg allocation each call |
| Memoize recursion | `@functools.cache` / `@lru_cache(None)` | manual memo dict | One line, faster, less code |
| Top-K elements | `heapq.nlargest(k, ...)` | `sorted(...)[-k:]` | O(n log k) vs O(n log n) |
| Binary search | `bisect.bisect_left/right` | hand-rolled `while` loop | No off-by-one bugs |
| Copy nested grid | `copy.deepcopy(grid)` | `grid[:]`, `copy.copy(grid)` | Shallow copy shares inner row references |
| String building in loop | `''.join(list)` | `s += char` repeatedly | Guaranteed O(n), portable |
| Index + value iteration | `enumerate(lst)` | `range(len(lst))` + indexing | Cleaner, avoids extra lookup |
| Deep recursion | raise `sys.setrecursionlimit` (or go iterative) | default limit (1000) | Avoids silent `RecursionError` |

---

*Companion file to: `interview_packages.md`*
*Last updated: June 2026*
