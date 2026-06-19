# Complete Interview Packages Reference — Java & Python
### Classes · Methods · MNC Usage · Interview Context

> **Tags:** `[MUST]` = all levels · `[SENIOR]` = 3+ yrs · `[DS/ML]` = data/ML roles · `[OPT]` = situational

---

## WHAT "PACKAGE" MEANS IN AN INTERVIEW

In coding interviews, a "package" or "library" refers strictly to the **language's built-in standard library only**. Top companies — Google, Amazon, Meta, Microsoft — explicitly forbid third-party frameworks (Spring Boot, Django, Flask, Hibernate) in DSA rounds because they want to evaluate your core algorithmic logic, not your framework knowledge.

- **Python:** You do NOT `pip install` anything. Every module listed here is built-in and works on LeetCode, HackerRank, CodeSignal, and HackerEarth without any setup.
- **Java:** You rely entirely on the Java Class Library (JCL). You must manually write `import java.util.*;` in offline IDEs, though platforms like LeetCode hide the imports automatically.
- **Third-party libraries (Spring, Django, Pandas, NumPy)** are only permitted in Data Engineering / Data Science / Machine Coding rounds when the platform **explicitly enables** them.

---

## COMPANY COVERAGE

### Product-Based (High DSA + System Design bar)
Google · Amazon · Microsoft · Meta · Apple · Netflix · Adobe · Flipkart · Razorpay · PhonePe · Swiggy · Zomato · CRED · Atlassian · Uber · Airbnb · LinkedIn · Stripe · Paytm

### Service-Based (OOP + Collections + Scripting)
TCS · Infosys · Wipro · Accenture · Cognizant · Capgemini · HCL · Tech Mahindra · IBM · Mphasis · LTIMindtree · Hexaware · Genpact

---

## PRODUCT-BASED vs SERVICE-BASED — HOW TESTING DIFFERS

| Factor | Product-Based MNCs (Google, Amazon, Uber, Meta) | Service-Based Companies (TCS, Infosys, Wipro, Accenture) |
|--------|------------------------------------------------|----------------------------------------------------------|
| **Platform** | Custom portals, LeetCode, HackerRank. No boilerplate in Machine Coding rounds. | AMCAT, Mettl, HackerEarth. Often strict environments with limited package whitelisting. |
| **Package Mastery** | **Expected.** Using a manual binary search when `bisect` exists, or failing to use `StringBuilder` in Java, signals lack of language fluency to interviewers. | **Basic.** Deep knowledge of `heapq` or `TreeMap` is rarely tested. Focus is on arrays, `HashMap`/`dict`, and basic loops. |
| **Machine Coding / LLD** | Required. Build fully functional CLI apps (e.g., Parking Lot system) in 90 minutes using only standard library and OOP. **No external frameworks allowed.** Requires `java.util.concurrent` or Python OOP natively. | Very rare. Rounds focus on basic output guessing, debugging, fundamental SQL queries. |
| **Data / Specialised Roles** | Platforms explicitly enable third-party packages — **Pandas, NumPy, SciPy** — for data manipulation questions. | Specialised roles often use MCQs for framework knowledge instead of live coding. |
| **I/O Parsing** | Usually pre-parsed (LeetCode style) — you only complete a function or method body. | Often requires reading from `System.in` or `sys.stdin` yourself. Must know `Scanner`/`BufferedReader` or `input().split()`. |

---

---

# PART 1 — JAVA PACKAGES

---

## 1. `java.lang` — Auto-Imported, Core of Everything `[MUST]`

> Automatically available in every Java program. Never needs an import statement. Tested at ALL companies from TCS freshers to Google senior roles.

---

### 1.1 `String`

> **The most tested class in all MNC interviews — string manipulation is the #1 topic across all companies.**

| Method | Signature | What it does |
|--------|-----------|--------------|
| `charAt` | `char charAt(int index)` | Returns char at position |
| `length` | `int length()` | Returns string length |
| `substring` | `String substring(int start, int end)` | Extracts substring [start, end) |
| `indexOf` | `int indexOf(String s)` | First occurrence index (-1 if absent) |
| `lastIndexOf` | `int lastIndexOf(String s)` | Last occurrence index |
| `contains` | `boolean contains(CharSequence s)` | Substring check |
| `startsWith` | `boolean startsWith(String prefix)` | Prefix check |
| `endsWith` | `boolean endsWith(String suffix)` | Suffix check |
| `equals` | `boolean equals(Object o)` | Content equality (use this, never `==`) |
| `equalsIgnoreCase` | `boolean equalsIgnoreCase(String s)` | Case-insensitive equals |
| `compareTo` | `int compareTo(String s)` | Lexicographic comparison |
| `toCharArray` | `char[] toCharArray()` | Converts to char array |
| `split` | `String[] split(String regex)` | Splits on regex |
| `trim` | `String trim()` | Removes leading/trailing ASCII whitespace |
| `strip` | `String strip()` | Unicode-aware trim (Java 11+) |
| `replace` | `String replace(char old, char new)` | Replace all occurrences |
| `replaceAll` | `String replaceAll(String regex, String r)` | Regex replace |
| `toLowerCase` | `String toLowerCase()` | Lowercase |
| `toUpperCase` | `String toUpperCase()` | Uppercase |
| `valueOf` | `static String valueOf(int/long/char/double)` | Primitive to String |
| `isEmpty` | `boolean isEmpty()` | length == 0 check |
| `isBlank` | `boolean isBlank()` | Blank/whitespace-only check (Java 11+) |
| `join` | `static String join(String delim, String... parts)` | Join with delimiter |
| `format` | `static String format(String fmt, Object... args)` | Formatted string |
| `matches` | `boolean matches(String regex)` | Full regex match |
| `intern` | `String intern()` | Canonical representation from string pool |
| `chars` | `IntStream chars()` | Stream of char values (Java 8+) |
| `repeat` | `String repeat(int n)` | Repeat string n times (Java 11+) |

---

### 1.2 `StringBuilder` `[MUST]`

> **MANDATORY for string manipulation.** Using `String` concatenation (`+`) inside a loop creates **O(n²) time complexity** and will fail hidden test cases on large inputs. Always use `StringBuilder` inside loops.

| Method | Signature | What it does |
|--------|-----------|--------------|
| `append` | `StringBuilder append(String/char/int/...)` | Appends value |
| `insert` | `StringBuilder insert(int offset, String s)` | Inserts at position |
| `delete` | `StringBuilder delete(int start, int end)` | Deletes range [start, end) |
| `deleteCharAt` | `StringBuilder deleteCharAt(int index)` | Deletes single char |
| `reverse` | `StringBuilder reverse()` | Reverses the content |
| `replace` | `StringBuilder replace(int s, int e, String str)` | Replaces range |
| `charAt` | `char charAt(int index)` | Gets char |
| `setCharAt` | `void setCharAt(int index, char ch)` | Sets char at index |
| `length` | `int length()` | Current length |
| `toString` | `String toString()` | Converts to String |
| `indexOf` | `int indexOf(String str)` | First occurrence |
| `capacity` | `int capacity()` | Buffer capacity |
| `ensureCapacity` | `void ensureCapacity(int min)` | Ensures minimum capacity |

> `StringBuffer` is the thread-safe version (synchronized methods). In single-threaded interview solutions, always prefer `StringBuilder` — it is faster.

---

### 1.3 `Math` `[MUST]`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `Math.abs` | `int/long/double abs(x)` | Absolute value |
| `Math.max` | `int max(int a, int b)` | Maximum of two |
| `Math.min` | `int min(int a, int b)` | Minimum of two |
| `Math.pow` | `double pow(double a, double b)` | a raised to b |
| `Math.sqrt` | `double sqrt(double a)` | Square root |
| `Math.floor` | `double floor(double a)` | Floor |
| `Math.ceil` | `double ceil(double a)` | Ceiling |
| `Math.round` | `long round(double a)` | Round to nearest long |
| `Math.log` | `double log(double a)` | Natural log |
| `Math.log10` | `double log10(double a)` | Log base 10 |
| `Math.PI` | `static final double` | π constant |
| `Math.E` | `static final double` | e constant |
| `Math.random` | `double random()` | Random [0.0, 1.0) |
| `Math.floorDiv` | `int floorDiv(int x, int y)` | Floor division |
| `Math.floorMod` | `int floorMod(int x, int y)` | Floor modulo (always non-negative) |

---

### 1.4 Wrapper Classes — `Integer`, `Long`, `Double`, `Character` `[MUST]`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `Integer.parseInt` | `int parseInt(String s)` | String to int |
| `Integer.valueOf` | `Integer valueOf(int i)` | int to Integer (boxed) |
| `Integer.toString` | `String toString(int i)` | int to String |
| `Integer.toBinaryString` | `String toBinaryString(int i)` | Binary string representation |
| `Integer.toHexString` | `String toHexString(int i)` | Hex string representation |
| `Integer.bitCount` | `int bitCount(int i)` | Count of set bits |
| `Integer.highestOneBit` | `int highestOneBit(int i)` | Highest set bit as power of 2 |
| `Integer.lowestOneBit` | `int lowestOneBit(int i)` | Lowest set bit as power of 2 |
| `Integer.reverse` | `int reverse(int i)` | Reverses all bits |
| `Integer.MAX_VALUE` | `static final int` | 2,147,483,647 (2³¹ − 1) |
| `Integer.MIN_VALUE` | `static final int` | −2,147,483,648 (−2³¹) |
| `Integer.compare` | `int compare(int x, int y)` | Null-safe int compare |
| `Character.isDigit` | `boolean isDigit(char c)` | Is '0'–'9'? |
| `Character.isLetter` | `boolean isLetter(char c)` | Is a letter? |
| `Character.isLetterOrDigit` | `boolean isLetterOrDigit(char c)` | Is alphanumeric? — critical for palindrome/string problems |
| `Character.isAlphabetic` | `boolean isAlphabetic(int c)` | Alphabetic check (Unicode-aware) |
| `Character.isUpperCase` | `boolean isUpperCase(char c)` | Uppercase check |
| `Character.isLowerCase` | `boolean isLowerCase(char c)` | Lowercase check |
| `Character.isWhitespace` | `boolean isWhitespace(char c)` | Whitespace check |
| `Character.toLowerCase` | `char toLowerCase(char c)` | To lowercase |
| `Character.toUpperCase` | `char toUpperCase(char c)` | To uppercase |
| `Long.parseLong` | `long parseLong(String s)` | String to long |
| `Long.MAX_VALUE` | `static final long` | 9,223,372,036,854,775,807 |
| `Double.parseDouble` | `double parseDouble(String s)` | String to double |
| `Double.isNaN` | `boolean isNaN(double v)` | Is NaN? |
| `Double.isInfinite` | `boolean isInfinite(double v)` | Is infinite? |

---

### 1.5 `Object` `[MUST]`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `equals` | `boolean equals(Object obj)` | Logical equality — override this in custom classes |
| `hashCode` | `int hashCode()` | Hash code — must override together with equals |
| `toString` | `String toString()` | String representation |
| `getClass` | `Class<?> getClass()` | Runtime class |
| `clone` | `protected Object clone()` | Shallow copy (implement Cloneable) |
| `wait` | `void wait()` | Release monitor and wait |
| `notify` | `void notify()` | Wake one waiting thread |
| `notifyAll` | `void notifyAll()` | Wake all waiting threads |

---

### 1.6 `Thread` / `Runnable` `[SENIOR]`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `start` | `void start()` | Starts new OS thread |
| `run` | `void run()` | Thread body (do not call directly) |
| `sleep` | `static void sleep(long ms)` | Pause current thread |
| `join` | `void join()` | Wait for thread to finish |
| `interrupt` | `void interrupt()` | Request thread interruption |
| `isInterrupted` | `boolean isInterrupted()` | Check interrupt flag |
| `currentThread` | `static Thread currentThread()` | Reference to current thread |
| `yield` | `static void yield()` | Hint scheduler to switch |
| `getName` / `setName` | `String getName()` / `void setName(String)` | Thread name |
| `setPriority` | `void setPriority(int p)` | Priority 1 (MIN) to 10 (MAX) |
| `getState` | `State getState()` | NEW / RUNNABLE / BLOCKED / WAITING / TIMED_WAITING / TERMINATED |
| `isDaemon` / `setDaemon` | `boolean isDaemon()` / `void setDaemon(boolean)` | Daemon status |

---

---

## 2. `java.util` — The Interview Backbone `[MUST]`

> Import with `import java.util.*;` — covers everything below.

---

### 2.1 `ArrayList<E>` `[MUST]`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `add(e)` | `boolean add(E e)` | Appends element — O(1) amortised |
| `add(i, e)` | `void add(int index, E element)` | Insert at index — O(n) |
| `get` | `E get(int index)` | Get element — O(1) |
| `set` | `E set(int index, E element)` | Replace element — O(1) |
| `remove(int)` | `E remove(int index)` | Remove by index — O(n) |
| `remove(Object)` | `boolean remove(Object o)` | Remove by value — O(n) |
| `size` | `int size()` | Number of elements |
| `isEmpty` | `boolean isEmpty()` | Size == 0 |
| `contains` | `boolean contains(Object o)` | O(n) membership check |
| `indexOf` | `int indexOf(Object o)` | First index or -1 |
| `lastIndexOf` | `int lastIndexOf(Object o)` | Last index or -1 |
| `clear` | `void clear()` | Remove all |
| `subList` | `List<E> subList(int from, int to)` | View of portion [from, to) |
| `toArray` | `Object[] toArray()` | Convert to array |
| `sort` | `void sort(Comparator<E> c)` | Sort in-place |
| `addAll` | `boolean addAll(Collection<E> c)` | Append all |
| `iterator` | `Iterator<E> iterator()` | Forward iterator |
| `listIterator` | `ListIterator<E> listIterator()` | Bidirectional iterator |
| `trimToSize` | `void trimToSize()` | Shrink capacity to size |

---

### 2.2 `LinkedList<E>` `[MUST]`

> Use as both `Queue` and `Deque`. For pure stack/queue operations, `ArrayDeque` is faster (no node allocation overhead).

| Method | Signature | What it does |
|--------|-----------|--------------|
| `addFirst` | `void addFirst(E e)` | Add to front — O(1) |
| `addLast` | `void addLast(E e)` | Add to back — O(1) |
| `getFirst` | `E getFirst()` | Peek front (throws if empty) |
| `getLast` | `E getLast()` | Peek back (throws if empty) |
| `removeFirst` | `E removeFirst()` | Remove from front (throws if empty) |
| `removeLast` | `E removeLast()` | Remove from back (throws if empty) |
| `peekFirst` | `E peekFirst()` | Front without remove (null if empty) |
| `peekLast` | `E peekLast()` | Back without remove (null if empty) |
| `offerFirst` | `boolean offerFirst(E e)` | Add to front (Queue API) |
| `offerLast` | `boolean offerLast(E e)` | Add to back (Queue API) |
| `pollFirst` | `E pollFirst()` | Remove front (null if empty) |
| `pollLast` | `E pollLast()` | Remove back (null if empty) |
| `push` | `void push(E e)` | Stack push (front) |
| `pop` | `E pop()` | Stack pop (front, throws if empty) |
| `peek` | `E peek()` | Stack peek (front, null if empty) |
| `size` | `int size()` | Size |
| `contains` | `boolean contains(Object o)` | O(n) membership |

---

### 2.3 `HashMap<K, V>` `[MUST]`

> O(1) average for get/put/remove. Used in frequency maps, memoization, graph adjacency, two-sum patterns.

| Method | Signature | What it does |
|--------|-----------|--------------|
| `put` | `V put(K key, V value)` | Insert or update |
| `get` | `V get(Object key)` | Get by key (null if absent) |
| `getOrDefault` | `V getOrDefault(Object key, V def)` | Get with fallback — avoid null checks |
| `remove` | `V remove(Object key)` | Remove entry |
| `containsKey` | `boolean containsKey(Object key)` | Key presence O(1) |
| `containsValue` | `boolean containsValue(Object value)` | Value presence O(n) |
| `size` | `int size()` | Number of entries |
| `isEmpty` | `boolean isEmpty()` | Empty check |
| `keySet` | `Set<K> keySet()` | All keys as Set |
| `values` | `Collection<V> values()` | All values |
| `entrySet` | `Set<Map.Entry<K,V>> entrySet()` | All key-value pairs — use in for-each |
| `putIfAbsent` | `V putIfAbsent(K key, V value)` | Put only if key absent |
| `computeIfAbsent` | `V computeIfAbsent(K key, Function f)` | Compute and insert if absent — builds adjacency lists |
| `compute` | `V compute(K key, BiFunction f)` | Compute new value unconditionally |
| `merge` | `V merge(K key, V val, BiFunction f)` | Merge values — great for frequency counts |
| `forEach` | `void forEach(BiConsumer<K,V> action)` | Iterate all entries |
| `replace` | `V replace(K key, V value)` | Replace if key exists |
| `clear` | `void clear()` | Remove all |

**Frequency count pattern (extremely common):**
```java
map.merge(key, 1, Integer::sum);
// equivalent to: map.put(key, map.getOrDefault(key, 0) + 1)
```

---

### 2.4 `LinkedHashMap<K, V>` `[MUST — LRU Cache]`

> Maintains **insertion order** (or access order). **Vital for LRU Cache design questions** — the most common system design coding problem at Amazon, Google, and Meta.

| Method | What it does |
|--------|--------------|
| All `HashMap` methods | Full HashMap interface |
| `new LinkedHashMap<>(capacity, loadFactor, true)` | Access-order mode (true) — enables LRU behaviour |
| `removeEldestEntry(Map.Entry<K,V>)` | Override to auto-evict oldest entry |

**LRU Cache pattern:**
```java
LinkedHashMap<Integer, Integer> cache = new LinkedHashMap<>(capacity, 0.75f, true) {
    protected boolean removeEldestEntry(Map.Entry<Integer,Integer> eldest) {
        return size() > capacity;
    }
};
```

---

### 2.5 `TreeMap<K, V>` `[MUST]`

> Backed by a Red-Black Tree. O(log n) for all operations. Use when you need **dynamically sorted data** or range queries. Essential for interval, sliding window, and calendar problems.

| Method | Signature | What it does |
|--------|-----------|--------------|
| All `HashMap` methods | — | Sorted by key |
| `firstKey` | `K firstKey()` | Smallest key |
| `lastKey` | `K lastKey()` | Largest key |
| `floorKey` | `K floorKey(K key)` | Greatest key ≤ given (null if none) |
| `ceilingKey` | `K ceilingKey(K key)` | Smallest key ≥ given (null if none) |
| `lowerKey` | `K lowerKey(K key)` | Greatest key < given (null if none) |
| `higherKey` | `K higherKey(K key)` | Smallest key > given (null if none) |
| `headMap` | `SortedMap<K,V> headMap(K toKey)` | View of keys < toKey |
| `tailMap` | `SortedMap<K,V> tailMap(K fromKey)` | View of keys ≥ fromKey |
| `subMap` | `SortedMap<K,V> subMap(K from, K to)` | View of keys in [from, to) |
| `pollFirstEntry` | `Map.Entry<K,V> pollFirstEntry()` | Remove and return smallest entry |
| `pollLastEntry` | `Map.Entry<K,V> pollLastEntry()` | Remove and return largest entry |
| `descendingMap` | `NavigableMap<K,V> descendingMap()` | Reverse-order view |

---

### 2.6 `HashSet<E>` / `LinkedHashSet<E>` / `TreeSet<E>` `[MUST]`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `add` | `boolean add(E e)` | Add element (false if duplicate) |
| `remove` | `boolean remove(Object o)` | Remove element |
| `contains` | `boolean contains(Object o)` | O(1) membership — hash-based |
| `size` | `int size()` | Count |
| `isEmpty` | `boolean isEmpty()` | Empty check |
| `clear` | `void clear()` | Clear all |
| `addAll` | `boolean addAll(Collection<E> c)` | Union |
| `retainAll` | `boolean retainAll(Collection<E> c)` | Intersection (modifies in-place) |
| `removeAll` | `boolean removeAll(Collection<E> c)` | Difference (modifies in-place) |
| **TreeSet only** | — | O(log n), sorted |
| `first` | `E first()` | Smallest element |
| `last` | `E last()` | Largest element |
| `floor` | `E floor(E e)` | Greatest ≤ e (null if none) |
| `ceiling` | `E ceiling(E e)` | Smallest ≥ e (null if none) |
| `lower` | `E lower(E e)` | Greatest < e (null if none) |
| `higher` | `E higher(E e)` | Smallest > e (null if none) |
| `headSet` | `SortedSet<E> headSet(E to)` | Elements < to |
| `tailSet` | `SortedSet<E> tailSet(E from)` | Elements ≥ from |
| `subSet` | `SortedSet<E> subSet(E f, E t)` | Elements in [f, t) |
| `pollFirst` | `E pollFirst()` | Remove and return smallest |
| `pollLast` | `E pollLast()` | Remove and return largest |
| `descendingSet` | `NavigableSet<E> descendingSet()` | Reverse-order view |

---

### 2.7 `ArrayDeque<E>` — Preferred Stack and Queue `[MUST]`

> **Preferred over `Stack` (legacy) and `LinkedList`** for both stack and queue operations. No null elements. Faster than `LinkedList` — no node allocation per element.

| Method | Signature | What it does |
|--------|-----------|--------------|
| `push` | `void push(E e)` | Stack push (front) |
| `pop` | `E pop()` | Stack pop (front, throws if empty) |
| `peek` | `E peek()` | Stack peek (front, null if empty) |
| `offer` | `boolean offer(E e)` | Queue enqueue (back) |
| `poll` | `E poll()` | Queue dequeue (front, null if empty) |
| `offerFirst` | `boolean offerFirst(E e)` | Add to front |
| `offerLast` | `boolean offerLast(E e)` | Add to back |
| `pollFirst` | `E pollFirst()` | Remove from front (null if empty) |
| `pollLast` | `E pollLast()` | Remove from back (null if empty) |
| `peekFirst` | `E peekFirst()` | View front (null if empty) |
| `peekLast` | `E peekLast()` | View back (null if empty) |
| `addFirst` | `void addFirst(E e)` | Add front (throws if full — unbounded so never throws) |
| `addLast` | `void addLast(E e)` | Add back |
| `size` | `int size()` | Size |
| `isEmpty` | `boolean isEmpty()` | Empty check |
| `contains` | `boolean contains(Object o)` | O(n) membership |
| `clear` | `void clear()` | Clear all |
| `iterator` | `Iterator<E> iterator()` | Front-to-back iterator |
| `descendingIterator` | `Iterator<E> descendingIterator()` | Back-to-front iterator |

---

### 2.8 `PriorityQueue<E>` — Min-Heap `[MUST]`

> **Min-Heap by default.** Essential for Top-K problems, Dijkstra's algorithm, merge K sorted lists, and task scheduling.

| Method | Signature | What it does |
|--------|-----------|--------------|
| `offer` | `boolean offer(E e)` | Insert — O(log n) |
| `poll` | `E poll()` | Remove minimum — O(log n) (null if empty) |
| `peek` | `E peek()` | View minimum — O(1) (null if empty) |
| `remove` | `boolean remove(Object o)` | Remove specific element — O(n) |
| `contains` | `boolean contains(Object o)` | Membership — O(n) |
| `size` | `int size()` | Size |
| `isEmpty` | `boolean isEmpty()` | Empty check |
| `toArray` | `Object[] toArray()` | Unordered array snapshot |
| `clear` | `void clear()` | Clear all |

**Constructor patterns:**
```java
// Min-heap (default)
PriorityQueue<Integer> minHeap = new PriorityQueue<>();

// Max-heap using reverse order
PriorityQueue<Integer> maxHeap = new PriorityQueue<>(Collections.reverseOrder());

// Custom comparator — e.g., sort int[] by second element
PriorityQueue<int[]> pq = new PriorityQueue<>((a, b) -> a[1] - b[1]);

// Custom comparator — by string length descending
PriorityQueue<String> pq = new PriorityQueue<>((a, b) -> b.length() - a.length());
```

---

### 2.9 `Collections` — Utility Class `[MUST]`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `sort` | `static <T> void sort(List<T> list)` | Natural sort — O(n log n) |
| `sort(comparator)` | `static <T> void sort(List<T>, Comparator<T> c)` | Custom sort |
| `reverse` | `static void reverse(List<?> list)` | Reverse list in-place |
| `shuffle` | `static void shuffle(List<?> list)` | Random shuffle |
| `min` | `static <T> T min(Collection<T> c)` | Minimum element |
| `max` | `static <T> T max(Collection<T> c)` | Maximum element |
| `frequency` | `static int frequency(Collection<?> c, Object o)` | Count occurrences |
| `binarySearch` | `static int binarySearch(List<T> l, T key)` | Binary search on sorted list |
| `fill` | `static <T> void fill(List<T> list, T obj)` | Fill with single value |
| `copy` | `static <T> void copy(List<T> dest, List<T> src)` | Copy (dest must be ≥ size) |
| `nCopies` | `static <T> List<T> nCopies(int n, T o)` | Immutable list of n copies |
| `disjoint` | `static boolean disjoint(Collection<?> c1, c2)` | True if no common elements |
| `unmodifiableList` | `static <T> List<T> unmodifiableList(List<T> l)` | Immutable view |
| `synchronizedList` | `static <T> List<T> synchronizedList(List<T> l)` | Thread-safe wrapper |
| `emptyList` | `static <T> List<T> emptyList()` | Immutable empty list |
| `singletonList` | `static <T> List<T> singletonList(T o)` | Single-element immutable list |
| `swap` | `static void swap(List<?> list, int i, int j)` | Swap two elements |
| `reverseOrder` | `static <T> Comparator<T> reverseOrder()` | Reverse natural order comparator |

---

### 2.10 `Arrays` — Utility Class `[MUST]`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `sort` | `static void sort(int[] a)` | Sort primitive array — O(n log n) |
| `sort(T[], Comparator)` | `static <T> void sort(T[] a, Comparator<T> c)` | Custom sort on object array |
| `sort(range)` | `static void sort(int[] a, int from, int to)` | Sort sub-array |
| `binarySearch` | `static int binarySearch(int[] a, int key)` | Binary search — must be sorted |
| `fill` | `static void fill(int[] a, int val)` | Fill array with value |
| `copyOf` | `static int[] copyOf(int[] original, int newLen)` | Copy with new length (truncate/pad) |
| `copyOfRange` | `static int[] copyOfRange(int[] a, int from, int to)` | Copy range [from, to) |
| `equals` | `static boolean equals(int[] a, int[] b)` | Element-wise equality |
| `toString` | `static String toString(int[] a)` | "[1, 2, 3]" format |
| `deepToString` | `static String deepToString(Object[] a)` | 2D/nested array as string |
| `deepEquals` | `static boolean deepEquals(Object[] a, b)` | Deep comparison |
| `asList` | `static <T> List<T> asList(T... a)` | Fixed-size List backed by array |
| `stream` | `static IntStream stream(int[] a)` | Convert to IntStream |

---

### 2.11 `Scanner` / Fast I/O `[MUST for service-based / HackerRank]`

> On LeetCode, input is pre-parsed. On HackerRank and in service-based company assessments (AMCAT, Mettl), you must parse `System.in` yourself.

| Method | Signature | What it does |
|--------|-----------|--------------|
| `nextInt` | `int nextInt()` | Read int token |
| `nextLong` | `long nextLong()` | Read long token |
| `nextDouble` | `double nextDouble()` | Read double token |
| `next` | `String next()` | Read one whitespace-delimited token |
| `nextLine` | `String nextLine()` | Read full line |
| `hasNext` | `boolean hasNext()` | More tokens? |
| `hasNextInt` | `boolean hasNextInt()` | Next token is int? |
| `hasNextLine` | `boolean hasNextLine()` | More lines? |
| `close` | `void close()` | Close scanner |
| `useDelimiter` | `Scanner useDelimiter(String pattern)` | Custom delimiter |

**`BufferedReader` + `StringTokenizer` — faster than `Scanner`** (recommended for large inputs):
```java
import java.io.*;
import java.util.StringTokenizer;

BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
StringTokenizer st = new StringTokenizer(br.readLine());
int n = Integer.parseInt(st.nextToken());
int m = Integer.parseInt(st.nextToken());
```

**`StringTokenizer` key methods:**
| Method | What it does |
|--------|--------------|
| `new StringTokenizer(str)` | Tokenize on whitespace |
| `new StringTokenizer(str, delim)` | Tokenize on custom delimiter |
| `hasMoreTokens()` | More tokens? |
| `nextToken()` | Next token as String |
| `countTokens()` | Remaining token count |

---

### 2.12 `Optional<T>` `[MUST — Java 8+]`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `of` | `static <T> Optional<T> of(T value)` | Wrap non-null (throws on null) |
| `ofNullable` | `static <T> Optional<T> ofNullable(T value)` | Wrap possibly-null |
| `empty` | `static <T> Optional<T> empty()` | Empty optional |
| `isPresent` | `boolean isPresent()` | Has value? |
| `isEmpty` | `boolean isEmpty()` | No value? (Java 11+) |
| `get` | `T get()` | Get value (throws `NoSuchElementException` if empty) |
| `orElse` | `T orElse(T other)` | Value or default |
| `orElseGet` | `T orElseGet(Supplier<T> s)` | Value or lazily-computed default |
| `orElseThrow` | `T orElseThrow(Supplier<X> ex)` | Value or throw custom exception |
| `map` | `Optional<U> map(Function<T,U> f)` | Transform value if present |
| `flatMap` | `Optional<U> flatMap(Function<T,Optional<U>> f)` | Flat transform |
| `filter` | `Optional<T> filter(Predicate<T> p)` | Empty if predicate fails |
| `ifPresent` | `void ifPresent(Consumer<T> c)` | Run action if value present |
| `ifPresentOrElse` | `void ifPresentOrElse(Consumer, Runnable)` | Branch on presence (Java 9+) |

---

---

## 3. `java.util.stream` — Functional Data Processing `[MUST — Java 8+]`

---

### 3.1 `Stream<T>` — Intermediate Operations (lazy — not executed until terminal)

| Method | Signature | What it does |
|--------|-----------|--------------|
| `filter` | `Stream<T> filter(Predicate<T> p)` | Keep matching elements |
| `map` | `<R> Stream<R> map(Function<T,R> f)` | Transform each element |
| `flatMap` | `<R> Stream<R> flatMap(Function<T,Stream<R>> f)` | Flatten nested streams |
| `mapToInt` | `IntStream mapToInt(ToIntFunction<T> f)` | Map to IntStream |
| `mapToLong` | `LongStream mapToLong(...)` | Map to LongStream |
| `mapToDouble` | `DoubleStream mapToDouble(...)` | Map to DoubleStream |
| `distinct` | `Stream<T> distinct()` | Remove duplicates (uses equals/hashCode) |
| `sorted` | `Stream<T> sorted()` | Natural sort |
| `sorted(c)` | `Stream<T> sorted(Comparator<T> c)` | Custom sort |
| `peek` | `Stream<T> peek(Consumer<T> c)` | Inspect without consuming — for debugging |
| `limit` | `Stream<T> limit(long n)` | First n elements |
| `skip` | `Stream<T> skip(long n)` | Skip first n elements |
| `takeWhile` | `Stream<T> takeWhile(Predicate<T> p)` | Take while predicate true (Java 9+) |
| `dropWhile` | `Stream<T> dropWhile(Predicate<T> p)` | Drop while predicate true (Java 9+) |

### 3.2 `Stream<T>` — Terminal Operations (trigger execution)

| Method | Signature | What it does |
|--------|-----------|--------------|
| `forEach` | `void forEach(Consumer<T> c)` | Consume all elements |
| `collect` | `<R> R collect(Collector<T,A,R> c)` | Collect into container |
| `toList` | `List<T> toList()` | Unmodifiable list (Java 16+) |
| `count` | `long count()` | Count all elements |
| `reduce(op)` | `Optional<T> reduce(BinaryOperator<T> op)` | Fold to single value |
| `reduce(id, op)` | `T reduce(T identity, BinaryOperator<T> op)` | Fold with identity |
| `min` | `Optional<T> min(Comparator<T> c)` | Minimum element |
| `max` | `Optional<T> max(Comparator<T> c)` | Maximum element |
| `findFirst` | `Optional<T> findFirst()` | First element |
| `findAny` | `Optional<T> findAny()` | Any element (non-deterministic in parallel) |
| `anyMatch` | `boolean anyMatch(Predicate<T> p)` | Short-circuits on first match |
| `allMatch` | `boolean allMatch(Predicate<T> p)` | Short-circuits on first failure |
| `noneMatch` | `boolean noneMatch(Predicate<T> p)` | Short-circuits on first match |
| `toArray` | `Object[] toArray()` | To array |

**Static factory methods:**
```java
Stream.of("a", "b", "c")
Stream.empty()
Stream.generate(() -> 0)          // infinite
Stream.iterate(0, n -> n + 1)     // infinite
Stream.iterate(0, n -> n < 10, n -> n + 1)  // bounded (Java 9+)
Stream.concat(stream1, stream2)
```

---

### 3.3 `Collectors` `[MUST]`

| Collector | What it does |
|-----------|--------------|
| `toList()` | Mutable `ArrayList` |
| `toSet()` | Mutable `HashSet` |
| `toMap(keyFn, valueFn)` | Map from stream elements |
| `toUnmodifiableList()` | Immutable list (Java 10+) |
| `joining(delim, prefix, suffix)` | Concatenate String stream |
| `groupingBy(classifier)` | `Map<K, List<V>>` — group elements |
| `groupingBy(f, downstream)` | Group then aggregate: `groupingBy(f, counting())` |
| `partitioningBy(Predicate)` | `Map<Boolean, List<T>>` — true/false split |
| `counting()` | Count elements per group |
| `summingInt(fn)` | Sum per group |
| `averagingInt(fn)` | Average per group |
| `summarizingInt(fn)` | Count/sum/min/max/avg stats |
| `maxBy(Comparator)` | Max per group |
| `minBy(Comparator)` | Min per group |
| `toCollection(Supplier)` | Custom collection type |
| `mapping(fn, downstream)` | Map then collect |
| `flatMapping(fn, downstream)` | FlatMap then collect (Java 9+) |
| `teeing(c1, c2, BiFunction)` | Two collectors merged (Java 12+) |

---

### 3.4 `IntStream` / `LongStream` / `DoubleStream`

| Method / Factory | What it does |
|-----------------|--------------|
| `IntStream.range(0, n)` | [0, n) — excludes n |
| `IntStream.rangeClosed(1, n)` | [1, n] — includes n |
| `IntStream.of(1, 2, 3)` | From values |
| `sum()` | Sum |
| `average()` | `OptionalDouble` |
| `min()` / `max()` | `OptionalInt` |
| `boxed()` | `Stream<Integer>` |
| `asLongStream()` | Widen to `LongStream` |
| `toArray()` | `int[]` |
| `summaryStatistics()` | `IntSummaryStatistics` — count/sum/min/max/avg |

---

---

## 4. `java.util.function` — Functional Interfaces `[MUST — Java 8+]`

| Interface | Abstract Method | Use case |
|-----------|----------------|----------|
| `Function<T,R>` | `R apply(T t)` | Transform one type to another |
| `BiFunction<T,U,R>` | `R apply(T t, U u)` | Two inputs → one output |
| `Predicate<T>` | `boolean test(T t)` | Filter / test condition |
| `BiPredicate<T,U>` | `boolean test(T t, U u)` | Two-input predicate |
| `Consumer<T>` | `void accept(T t)` | Side-effecting operation |
| `BiConsumer<T,U>` | `void accept(T t, U u)` | Two-input side-effecting |
| `Supplier<T>` | `T get()` | Produce value with no input |
| `UnaryOperator<T>` | `T apply(T t)` | T → T (specialised Function) |
| `BinaryOperator<T>` | `T apply(T t1, T t2)` | T, T → T (specialised BiFunction) |
| `ToIntFunction<T>` | `int applyAsInt(T t)` | Produce primitive int |
| `ToLongFunction<T>` | `long applyAsLong(T t)` | Produce primitive long |
| `IntUnaryOperator` | `int applyAsInt(int op)` | int → int |
| `IntBinaryOperator` | `int applyAsInt(int l, int r)` | int, int → int |

**Composition:**
- `Function`: `andThen(f)`, `compose(f)`, `Function.identity()`
- `Predicate`: `and(p)`, `or(p)`, `negate()`
- `Consumer`: `andThen(c)`

---

---

## 5. `java.util.concurrent` — Concurrency `[SENIOR — Machine Coding / LLD rounds]`

> Rarely used in standard DSA, but **heavily tested in Machine Coding rounds** at product-based companies. You must use these natively without Spring or external frameworks.

---

### 5.1 `ExecutorService`

| Method | Signature | What it does |
|--------|-----------|--------------|
| `submit(Callable)` | `Future<T> submit(Callable<T> task)` | Submit task, get Future |
| `submit(Runnable)` | `Future<?> submit(Runnable task)` | Submit Runnable |
| `execute` | `void execute(Runnable command)` | Fire-and-forget |
| `shutdown` | `void shutdown()` | Graceful shutdown (completes queued tasks) |
| `shutdownNow` | `List<Runnable> shutdownNow()` | Immediate shutdown |
| `awaitTermination` | `boolean awaitTermination(long t, TimeUnit u)` | Block until done or timeout |
| `isShutdown` | `boolean isShutdown()` | Shutdown initiated? |
| `isTerminated` | `boolean isTerminated()` | All tasks done? |
| `invokeAll` | `List<Future<T>> invokeAll(Collection<Callable<T>>)` | Submit all, wait all |
| `invokeAny` | `T invokeAny(Collection<Callable<T>>)` | Return first to complete |

**Factory methods via `Executors`:**
```java
Executors.newFixedThreadPool(int n)
Executors.newCachedThreadPool()
Executors.newSingleThreadExecutor()
Executors.newScheduledThreadPool(int coreSize)
Executors.newWorkStealingPool()
```

---

### 5.2 `CompletableFuture<T>` `[SENIOR]`

| Method | What it does |
|--------|--------------|
| `supplyAsync(Supplier)` | Run supplier async, return CompletableFuture |
| `runAsync(Runnable)` | Run runnable async, no return |
| `thenApply(Function)` | Transform result when done |
| `thenAccept(Consumer)` | Consume result when done |
| `thenRun(Runnable)` | Run action when done |
| `thenCompose(Function)` | Flat-map — chain dependent futures |
| `thenCombine(CF, BiFunction)` | Combine two independent futures |
| `allOf(CF...)` | Future that completes when all complete |
| `anyOf(CF...)` | Future that completes when first completes |
| `exceptionally(Function)` | Handle exceptions (like catch block) |
| `handle(BiFunction)` | Handle both result and exception |
| `join()` | Block for result (unchecked exceptions) |
| `get()` | Block for result (checked exceptions) |
| `complete(T)` | Manually complete with value |
| `completeExceptionally(Throwable)` | Manually complete with exception |
| `isDone()` | Completed? |

---

### 5.3 `ConcurrentHashMap<K,V>` `[SENIOR]`

| Method | What it does |
|--------|--------------|
| All `HashMap` methods | Thread-safe without full synchronization |
| `putIfAbsent` | Atomic put-if-absent |
| `computeIfAbsent` | Atomic compute-and-put |
| `compute` | Atomic update |
| `merge` | Atomic merge |
| `forEach(threshold, BiConsumer)` | Parallel forEach |
| `reduce(threshold, transformer, reducer)` | Parallel reduce |
| `mappingCount()` | Long count (safer than `size()` under concurrency) |

---

### 5.4 `BlockingQueue` Implementations `[SENIOR]`

| Class | Characteristics |
|-------|----------------|
| `LinkedBlockingQueue` | Optionally bounded, linked-node backed |
| `ArrayBlockingQueue` | Strictly bounded, array-backed |
| `PriorityBlockingQueue` | Unbounded priority queue (thread-safe) |
| `SynchronousQueue` | Zero capacity — each put must wait for a take |
| `DelayQueue` | Elements become available after a delay |

| Method | What it does |
|--------|--------------|
| `put(e)` | Insert, blocks if full |
| `take()` | Remove, blocks if empty |
| `offer(e, timeout, unit)` | Insert with timeout |
| `poll(timeout, unit)` | Remove with timeout |
| `drainTo(Collection)` | Drain all to collection |

---

### 5.5 `CountDownLatch` / `CyclicBarrier` / `Semaphore`

| Class | Constructor | Key Methods | Use case |
|-------|-------------|-------------|----------|
| `CountDownLatch` | `CountDownLatch(int n)` | `await()`, `countDown()` | Wait for N events to complete |
| `CyclicBarrier` | `CyclicBarrier(int n)` | `await()`, `reset()` | N threads meet at a point, reusable |
| `Semaphore` | `Semaphore(int permits)` | `acquire()`, `release()`, `tryAcquire()` | Limit concurrent access to resource |

---

### 5.6 `java.util.concurrent.atomic` `[SENIOR]`

| Class | Key Methods |
|-------|-------------|
| `AtomicInteger` | `get()`, `set(v)`, `getAndIncrement()`, `incrementAndGet()`, `compareAndSet(expected, update)`, `addAndGet(delta)`, `getAndAdd(delta)` |
| `AtomicLong` | Same as `AtomicInteger` for `long` |
| `AtomicBoolean` | `get()`, `set(v)`, `compareAndSet(expected, update)`, `getAndSet(v)` |
| `AtomicReference<V>` | `get()`, `set(v)`, `compareAndSet(expected, update)` |

---

### 5.7 `java.util.concurrent.locks` `[SENIOR]`

| Class | Key Methods |
|-------|-------------|
| `ReentrantLock` | `lock()`, `unlock()`, `tryLock()`, `tryLock(timeout, unit)`, `isLocked()`, `getHoldCount()`, `newCondition()` |
| `ReentrantReadWriteLock` | `readLock()` → `Lock`, `writeLock()` → `Lock` |
| `Condition` | `await()`, `awaitNanos(long)`, `signal()`, `signalAll()` |
| `StampedLock` | `writeLock()`, `readLock()`, `tryOptimisticRead()`, `validate(stamp)` |

---

---

## 6. `java.math` `[MUST — BigNumber problems]`

### 6.1 `BigInteger`

| Method | What it does |
|--------|--------------|
| `BigInteger.valueOf(long)` | From primitive long |
| `new BigInteger(String)` | From decimal string |
| `new BigInteger(String, int radix)` | From string in given base |
| `add(BigInteger)` | Addition |
| `subtract(BigInteger)` | Subtraction |
| `multiply(BigInteger)` | Multiplication |
| `divide(BigInteger)` | Integer division |
| `mod(BigInteger)` | Modulo |
| `pow(int)` | Power |
| `gcd(BigInteger)` | Greatest common divisor |
| `abs()` | Absolute value |
| `negate()` | Negation |
| `compareTo(BigInteger)` | Compare (do not use `==` or `.equals` for ordering) |
| `isProbablePrime(int certainty)` | Primality test |
| `bitLength()` | Number of bits in two's complement |
| `testBit(int n)` | Test nth bit |
| `setBit(int n)` | Set nth bit |
| `toString(int radix)` | String in given base |
| `BigInteger.ZERO`, `.ONE`, `.TWO`, `.TEN` | Constants |

### 6.2 `BigDecimal`

| Method | What it does |
|--------|--------------|
| `add`, `subtract`, `multiply`, `divide` | Exact arithmetic |
| `setScale(int scale, RoundingMode)` | Set decimal places with rounding |
| `compareTo(BigDecimal)` | Compare — **use instead of `.equals`** |
| `stripTrailingZeros()` | Remove trailing zeros |
| `toPlainString()` | Without scientific notation |
| `BigDecimal.ZERO`, `.ONE`, `.TEN` | Constants |

---

---

## 7. `java.time` — Modern Date/Time `[MUST — Java 8+]`

| Class | Key Methods |
|-------|-------------|
| `LocalDate` | `now()`, `of(y,m,d)`, `plusDays()`, `minusDays()`, `plusMonths()`, `isBefore()`, `isAfter()`, `isEqual()`, `getYear()`, `getMonthValue()`, `getDayOfWeek()`, `isLeapYear()`, `until()`, `parse()`, `format()` |
| `LocalTime` | `now()`, `of(h,m,s,ns)`, `plusHours()`, `plusMinutes()`, `isBefore()`, `isAfter()`, `getHour()`, `getMinute()`, `getSecond()` |
| `LocalDateTime` | `now()`, `of(date, time)`, `toLocalDate()`, `toLocalTime()`, `plusDays()`, `plusHours()` |
| `ZonedDateTime` | `now(ZoneId)`, `withZoneSameInstant()`, `getZone()` |
| `Duration` | `between(t1, t2)`, `ofHours()`, `ofMinutes()`, `ofSeconds()`, `toMinutes()`, `toSeconds()`, `getSeconds()` |
| `Period` | `between(d1, d2)`, `ofDays()`, `ofMonths()`, `ofYears()`, `getYears()`, `getMonths()`, `getDays()` |
| `DateTimeFormatter` | `ofPattern("dd-MM-yyyy HH:mm")`, `format(temporal)`, `parse(text)` |
| `Instant` | `now()`, `ofEpochMilli(ms)`, `toEpochMilli()`, `compareTo()` |
| `ZoneId` | `of("Asia/Kolkata")`, `systemDefault()`, `getAvailableZoneIds()` |

---

---

## 8. `java.io` — I/O Operations `[MUST for HackerRank / service-based]`

| Class | Key Methods |
|-------|-------------|
| `BufferedReader` | `readLine()`, `read()`, `lines()` (returns `Stream<String>`), `close()` |
| `BufferedWriter` | `write(String)`, `newLine()`, `flush()`, `close()` |
| `InputStreamReader` | Bridges `InputStream` to `Reader` — wrap `System.in` |
| `FileReader` | `read()`, `read(char[])`, `close()` |
| `FileWriter` | `write(String)`, `write(char[])`, `flush()`, `close()` |
| `PrintWriter` | `print()`, `println()`, `printf()`, `flush()`, `close()` |
| `File` | `exists()`, `createNewFile()`, `delete()`, `list()`, `isDirectory()`, `getAbsolutePath()`, `length()`, `mkdir()`, `mkdirs()` |
| `Serializable` | Marker interface — declare `private static final long serialVersionUID` |

**Fastest I/O for large competitive-programming style inputs:**
```java
import java.io.*;
import java.util.StringTokenizer;

public class Main {
    public static void main(String[] args) throws IOException {
        BufferedReader br = new BufferedReader(new InputStreamReader(System.in));
        PrintWriter pw = new PrintWriter(new BufferedWriter(new OutputStreamWriter(System.out)));
        StringTokenizer st = new StringTokenizer(br.readLine());
        int n = Integer.parseInt(st.nextToken());
        pw.println(n);
        pw.flush();
    }
}
```

---

---

## 9. `java.nio` / `java.nio.file` `[SENIOR]`

| Class | Key Methods |
|-------|-------------|
| `Path` | `Paths.get("...")`, `resolve()`, `relativize()`, `getFileName()`, `getParent()`, `toAbsolutePath()`, `toString()` |
| `Files` | `readAllLines()`, `readAllBytes()`, `write()`, `copy()`, `move()`, `delete()`, `exists()`, `createDirectories()`, `walk()`, `lines()`, `size()` |
| `FileChannel` | `open()`, `read(ByteBuffer)`, `write(ByteBuffer)`, `transferTo()`, `position()`, `size()`, `lock()` |
| `ByteBuffer` | `allocate(int)`, `allocateDirect(int)`, `put()`, `get()`, `flip()`, `clear()`, `rewind()`, `remaining()`, `capacity()`, `limit()` |

---

---

## 10. `java.lang.reflect` `[SENIOR]`

| Class | Key Methods |
|-------|-------------|
| `Class<?>` | `forName(String)`, `getFields()`, `getMethods()`, `getConstructors()`, `getDeclaredField()`, `getDeclaredMethod()`, `isAssignableFrom()`, `isInterface()`, `getSuperclass()` |
| `Method` | `invoke(Object, Object...)`, `getName()`, `getParameterTypes()`, `getReturnType()`, `setAccessible(true)` |
| `Field` | `get(Object)`, `set(Object, value)`, `getName()`, `getType()`, `setAccessible(true)` |
| `Constructor<T>` | `newInstance(Object...)`, `getParameterTypes()`, `setAccessible(true)` |

---

---

## 11. `java.util.regex` `[MUST]`

| Class | Key Methods |
|-------|-------------|
| `Pattern` | `compile(String regex)`, `compile(regex, flags)`, `matcher(String)`, `static matches(regex, input)`, `split(input)` |
| `Matcher` | `matches()`, `find()`, `find(int start)`, `group()`, `group(int n)`, `group(String name)`, `start()`, `end()`, `replaceAll(String)`, `replaceFirst(String)`, `reset()` |

**Common flags:** `Pattern.CASE_INSENSITIVE`, `Pattern.MULTILINE`, `Pattern.DOTALL`

---

---

## 12. Spring Framework Packages `[SENIOR — framework / experience interviews only]`

> **Not used in DSA rounds.** Only tested in framework/backend experience interviews at service-based companies or senior product-based interviews.

| Package | Key Annotations / Classes |
|---------|--------------------------|
| `org.springframework.context` | `@Bean`, `@Configuration`, `@Component`, `@Service`, `@Repository`, `ApplicationContext`, `@Autowired`, `@Qualifier`, `@Scope` |
| `org.springframework.web.bind.annotation` | `@RestController`, `@Controller`, `@RequestMapping`, `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`, `@PathVariable`, `@RequestParam`, `@RequestBody`, `@ResponseBody` |
| `org.springframework.http` | `ResponseEntity<T>`, `HttpStatus`, `HttpHeaders`, `MediaType` |
| `org.springframework.data.jpa` | `JpaRepository<T,ID>`, `CrudRepository<T,ID>`, `@Transactional`, `@Query`, `Pageable`, `Page<T>` |
| `org.springframework.security` | `@EnableWebSecurity`, `UserDetails`, `SecurityContextHolder`, `@PreAuthorize`, `BCryptPasswordEncoder` |
| `org.springframework.boot` | `@SpringBootApplication`, `SpringApplication.run()`, `@ConfigurationProperties`, `@Value` |
| Testing | `@SpringBootTest`, `@WebMvcTest`, `@DataJpaTest`, `MockMvc`, `@MockBean`, `@InjectMocks`, `@Mock` |

---

---

# PART 2 — PYTHON PACKAGES

> All modules below are **built-in standard library**. No `pip install` required. All work on LeetCode, HackerRank, CodeSignal, HackerEarth without setup.

---

## 1. `collections` — The Most Critical Module `[MUST]`

> **The single most important Python module for coding interviews.** Provides O(1) data structure operations that replace verbose manual implementations.

---

### 1.1 `deque` — O(1) Queue Operations

> **NEVER use a standard `list` as a queue** — `list.pop(0)` is O(n). `deque.popleft()` is O(1). Essential for **BFS** and **sliding window** problems.

| Method | What it does |
|--------|--------------|
| `deque(iterable, maxlen)` | Create with optional max length |
| `append(x)` | Add to right — O(1) |
| `appendleft(x)` | Add to left — O(1) |
| `pop()` | Remove from right — O(1) |
| `popleft()` | Remove from left — O(1) |
| `extend(iterable)` | Extend right |
| `extendleft(iterable)` | Extend left (reverses order) |
| `rotate(n)` | Rotate n steps right (negative = left) |
| `clear()` | Remove all |
| `count(x)` | Count occurrences |
| `remove(x)` | Remove first occurrence |
| `index(x, start, stop)` | Index of element |
| `reverse()` | Reverse in-place |
| `maxlen` | Read-only max length attribute |

---

### 1.2 `Counter` — Instant Frequency Maps

> **Instantly creates frequency maps** of strings or arrays. Eliminates the common `dict.get(k, 0) + 1` pattern.

| Method | What it does |
|--------|--------------|
| `Counter(iterable)` | Count elements |
| `Counter(string)` | Count characters |
| `Counter({'a': 3, 'b': 1})` | From dict |
| `most_common(n)` | Top n by frequency — O(n log k) |
| `most_common()` | All, sorted by frequency descending |
| `elements()` | Iterator over elements (repeated by count) |
| `update(iterable)` | Add counts |
| `subtract(iterable)` | Subtract counts (can go negative) |
| `total()` | Sum of all counts (Python 3.10+) |
| `counter[key]` | Count for key (returns 0 if absent — no KeyError) |
| `+` | Add counters (keeps positive only) |
| `-` | Subtract counters (keeps positive only) |
| `&` | Intersection (min of each count) |
| `\|` | Union (max of each count) |

---

### 1.3 `defaultdict` — Handles Missing Keys Automatically

> **Crucial for graph adjacency lists** and grouping. Eliminates `if key not in dict` boilerplate.

| Feature | What it does |
|---------|--------------|
| `defaultdict(list)` | Default factory = empty list |
| `defaultdict(int)` | Default factory = 0 |
| `defaultdict(set)` | Default factory = empty set |
| `defaultdict(lambda: value)` | Custom default value |
| `defaultdict(lambda: defaultdict(int))` | Nested defaultdict |
| `__missing__(key)` | Called when key missing (can override) |
| All `dict` methods | Full dict interface |

**Graph adjacency list pattern:**
```python
from collections import defaultdict
graph = defaultdict(list)
for u, v in edges:
    graph[u].append(v)
    graph[v].append(u)
```

---

### 1.4 `OrderedDict`

| Method | What it does |
|--------|--------------|
| `move_to_end(key, last=True)` | Move to back (True) or front (False) |
| `popitem(last=True)` | Remove and return last (True) or first (False) item |
| All `dict` methods | Full dict interface with insertion-order guarantee |

---

### 1.5 `namedtuple`

```python
from collections import namedtuple
Point = namedtuple('Point', ['x', 'y'])
p = Point(1, 2)
p.x                # 1 — field access
p._replace(x=5)   # Point(x=5, y=2) — new instance with changed field
p._asdict()        # {'x': 1, 'y': 2}
p._fields          # ('x', 'y')
```

### 1.6 `ChainMap`

| Method | What it does |
|--------|--------------|
| `ChainMap(*maps)` | Chain multiple dicts — first map wins |
| `maps` | List of underlying maps |
| `new_child(m)` | New ChainMap with m prepended |
| `parents` | ChainMap without first map |

---

---

## 2. `heapq` — Priority Queue / Min-Heap `[MUST]`

> Python's `heapq` is a **min-heap only**. To simulate a max-heap, negate the values (multiply by -1) before pushing and negate again after popping.
> Essential for: Top-K problems, Dijkstra's algorithm, merge K sorted lists.

| Function | Signature | What it does |
|----------|-----------|--------------|
| `heappush` | `heapq.heappush(heap, item)` | Push item onto heap — O(log n) |
| `heappop` | `heapq.heappop(heap)` | Pop and return smallest — O(log n) |
| `heapify` | `heapq.heapify(list)` | Convert list to heap in-place — O(n) |
| `heappushpop` | `heapq.heappushpop(heap, item)` | Push then pop (more efficient than two calls) |
| `heapreplace` | `heapq.heapreplace(heap, item)` | Pop then push (item need not be ≥ popped) |
| `nlargest` | `heapq.nlargest(n, iterable, key)` | n largest elements — O(n log k) |
| `nsmallest` | `heapq.nsmallest(n, iterable, key)` | n smallest elements — O(n log k) |
| `merge` | `heapq.merge(*iterables, key, reverse)` | Merge sorted iterables lazily |

**Max-heap pattern — multiply by -1:**
```python
import heapq
heap = []
heapq.heappush(heap, -value)     # negate to push
max_val = -heapq.heappop(heap)   # negate on pop to restore

# Top-K largest elements (max-heap approach)
heapq.heappush(heap, -num)
if len(heap) > k:
    heapq.heappop(heap)
```

**Heap with tuple (priority, value) — comparison breaks ties by second element:**
```python
heapq.heappush(heap, (priority, value))
priority, value = heapq.heappop(heap)
```

---

---

## 3. `itertools` — Combinatorics and Iterators `[MUST]`

> Used for brute-force and combinatorial problems. Eliminates manual nested loops.

### 3.1 Infinite Iterators

| Function | Signature | What it does |
|----------|-----------|--------------|
| `count` | `count(start=0, step=1)` | Infinite counter: 0, 1, 2, ... |
| `cycle` | `cycle(iterable)` | Cycle elements forever |
| `repeat` | `repeat(object, times=None)` | Repeat object (or forever) |

### 3.2 Combinatorics — most tested

| Function | Signature | What it does |
|----------|-----------|--------------|
| `permutations` | `permutations(iterable, r=None)` | All r-length ordered arrangements |
| `combinations` | `combinations(iterable, r)` | r-length combos, no repeat, sorted |
| `combinations_with_replacement` | `combinations_with_replacement(iterable, r)` | r-length combos, with repeat |
| `product` | `product(*iterables, repeat=1)` | Cartesian product (nested for loops) |

### 3.3 Finite Iterators — most tested

| Function | Signature | What it does |
|----------|-----------|--------------|
| `chain` | `chain(*iterables)` | Chain iterables end-to-end |
| `chain.from_iterable` | `chain.from_iterable(iterable_of_iterables)` | Flatten one level |
| `islice` | `islice(iterable, stop)` / `islice(it, start, stop, step)` | Lazy slice |
| `groupby` | `groupby(iterable, key=None)` | Group **consecutive** equal elements |
| `accumulate` | `accumulate(iterable, func=add, initial=None)` | Running accumulation (prefix sums) |
| `starmap` | `starmap(func, iterable)` | Like `map` but unpacks each element |
| `zip_longest` | `zip_longest(*iterables, fillvalue=None)` | Zip, fill shorter with fillvalue |
| `compress` | `compress(data, selectors)` | Keep data where selector is true |
| `dropwhile` | `dropwhile(predicate, iterable)` | Drop while predicate true, then yield all |
| `takewhile` | `takewhile(predicate, iterable)` | Yield while predicate true, then stop |
| `filterfalse` | `filterfalse(predicate, iterable)` | Keep where predicate is False |
| `pairwise` | `pairwise(iterable)` | Consecutive pairs: (a,b), (b,c), ... (Python 3.10+) |

---

---

## 4. `functools` — Higher-Order Functions `[MUST]`

| Decorator / Function | Signature | What it does |
|---------------------|-----------|--------------|
| `lru_cache` | `@lru_cache(maxsize=None)` | Memoization — converts recursion to Top-Down DP with one line |
| `lru_cache` | `@lru_cache(None)` | Same — `None` means unbounded cache |
| `cache` | `@cache` | Shorthand for `@lru_cache(maxsize=None)` (Python 3.9+) |
| `reduce` | `reduce(function, iterable, initializer=None)` | Left fold — `reduce(lambda a,b: a+b, [1,2,3])` → 6 |
| `partial` | `partial(func, *args, **kwargs)` | Partial function application — fix some arguments |
| `wraps` | `@wraps(wrapped)` | Preserve wrapped function's metadata in decorators |
| `total_ordering` | `@total_ordering` | Implement `__eq__` + one comparison, get all six |
| `cmp_to_key` | `cmp_to_key(mycmp)` | Convert old-style `cmp(a, b)` comparator to key function |
| `singledispatch` | `@singledispatch` | Single-dispatch generic functions |
| `cached_property` | `@cached_property` | Memoized property — computed once then cached (Python 3.8+) |

**Memoization pattern — one decorator converts recursion to DP:**
```python
from functools import lru_cache

@lru_cache(None)  # or @lru_cache(maxsize=None)
def fib(n):
    if n <= 1:
        return n
    return fib(n-1) + fib(n-2)
```

**Custom sort with `cmp_to_key`:**
```python
from functools import cmp_to_key
nums.sort(key=cmp_to_key(lambda a, b: int(str(b)+str(a)) - int(str(a)+str(b))))
```

---

---

## 5. `bisect` — Binary Search on Sorted Lists `[MUST]`

> Eliminates manually writing `while lo <= hi` binary search loops.

| Function | Signature | What it does |
|----------|-----------|--------------|
| `bisect_left` | `bisect_left(a, x, lo=0, hi=len(a))` | Leftmost index to insert x (x would go before any existing x) |
| `bisect_right` | `bisect_right(a, x, lo=0, hi=len(a))` | Rightmost index to insert x (x would go after any existing x) |
| `bisect` | `bisect(a, x)` | Alias for `bisect_right` |
| `insort_left` | `insort_left(a, x, lo, hi)` | Insert x maintaining sort (left of duplicates) |
| `insort_right` | `insort_right(a, x, lo, hi)` | Insert x maintaining sort (right of duplicates) |
| `insort` | `insort(a, x)` | Alias for `insort_right` |

**Usage patterns:**
```python
import bisect
a = [1, 3, 5, 5, 7, 9]

# Find leftmost position where x could be inserted
bisect.bisect_left(a, 5)   # → 2

# Find rightmost position
bisect.bisect_right(a, 5)  # → 4

# Count elements strictly less than x
count_less = bisect.bisect_left(a, x)

# Count elements less than or equal to x
count_leq = bisect.bisect_right(a, x)

# Check if x exists in sorted list
i = bisect.bisect_left(a, x)
exists = (i < len(a) and a[i] == x)
```

---

---

## 6. `math` — Mathematical Functions `[MUST]`

| Function / Constant | What it does |
|--------------------|--------------|
| `math.inf` | Positive infinity — use for boundary initialisation |
| `-math.inf` | Negative infinity |
| `math.pi` | π = 3.14159265... |
| `math.e` | e = 2.71828... |
| `math.tau` | τ = 2π |
| `math.floor(x)` | Floor — rounds down |
| `math.ceil(x)` | Ceiling — rounds up |
| `math.sqrt(x)` | Square root as float |
| `math.isqrt(x)` | Integer square root — no float error (Python 3.8+) |
| `math.log(x)` | Natural log |
| `math.log(x, base)` | Log with specified base |
| `math.log2(x)` | Log base 2 |
| `math.log10(x)` | Log base 10 |
| `math.pow(x, y)` | x^y as float |
| `math.gcd(a, b)` | GCD (Python 3.5+; multiple args in Python 3.9+) |
| `math.lcm(a, b)` | LCM (Python 3.9+) |
| `math.factorial(n)` | n! |
| `math.comb(n, k)` | Combinations nCk (Python 3.8+) |
| `math.perm(n, k)` | Permutations nPk (Python 3.8+) |
| `math.sin(x)` / `cos` / `tan` | Trig (radians) |
| `math.degrees(x)` | Radians → degrees |
| `math.radians(x)` | Degrees → radians |
| `math.fabs(x)` | Absolute value as float |
| `math.copysign(x, y)` | Magnitude of x with sign of y |
| `math.hypot(x, y)` | Euclidean distance √(x²+y²) |
| `math.isfinite(x)` | Not inf and not NaN |
| `math.isinf(x)` | Is infinite |
| `math.isnan(x)` | Is NaN |
| `math.prod(iterable)` | Product of all elements (Python 3.8+) |
| `math.fsum(iterable)` | Accurate floating-point sum |
| `math.trunc(x)` | Truncate toward zero |
| `math.modf(x)` | Returns `(fractional_part, integer_part)` |

---

---

## 7. `sys` — System Interface `[MUST]`

| Attribute / Function | What it does |
|---------------------|--------------|
| `sys.stdin` | Standard input stream |
| `sys.stdout` | Standard output stream |
| `sys.stderr` | Standard error stream |
| `sys.argv` | Command-line arguments list (`argv[0]` = script name) |
| `sys.maxsize` | Platform's maximum int — alternative to `math.inf` for int problems |
| `sys.exit(code)` | Exit program (0 = success) |
| `sys.setrecursionlimit(n)` | Set recursion depth limit. **Mandatory** on HackerRank for deep DFS — Python default is only 1000. Set to `10**6`. |
| `sys.getrecursionlimit()` | Get current limit |
| `sys.path` | Module search path list |
| `sys.modules` | Dict of loaded modules |
| `sys.version` | Python version string |
| `sys.platform` | OS identifier (`'linux'`, `'win32'`, `'darwin'`) |
| `sys.getsizeof(obj)` | Object memory usage in bytes |
| `sys.stdin.readline()` | Read one line — **faster than `input()`** for large inputs |
| `sys.stdin.read()` | Read all of stdin at once |

**Standard contest I/O patterns:**
```python
import sys
input = sys.stdin.readline  # replace input() for speed

# Deep DFS — set recursion limit at the top of every solution
sys.setrecursionlimit(10**6)

# Use sys.maxsize instead of float('inf') for integer comparisons
dist = [sys.maxsize] * n
```

---

---

## 8. `re` — Regular Expressions `[MUST]`

| Function | Signature | What it does |
|----------|-----------|--------------|
| `re.match` | `match(pattern, string, flags)` | Match at start of string |
| `re.search` | `search(pattern, string, flags)` | Match anywhere in string |
| `re.fullmatch` | `fullmatch(pattern, string, flags)` | Match entire string |
| `re.findall` | `findall(pattern, string)` | All non-overlapping matches as list |
| `re.finditer` | `finditer(pattern, string)` | Iterator of Match objects |
| `re.sub` | `sub(pattern, repl, string, count)` | Replace matches |
| `re.subn` | `subn(pattern, repl, string)` | Replace, return `(new_string, count)` |
| `re.split` | `split(pattern, string, maxsplit)` | Split on pattern |
| `re.compile` | `compile(pattern, flags)` | Pre-compile for repeated use |
| `re.escape` | `escape(string)` | Escape all special characters |
| `re.purge` | `purge()` | Clear regex cache |

**Match object methods:**
```python
m = re.search(r'(\d+)-(\w+)', 'abc123-xyz')
m.group()       # '123-xyz' — entire match
m.group(1)      # '123' — capture group 1
m.groups()      # ('123', 'xyz') — all groups
m.groupdict()   # named groups as dict
m.start()       # start index
m.end()         # end index
m.span()        # (start, end)
```

**Flags:** `re.I` (case-insensitive), `re.M` (multiline), `re.S` (dot matches newline), `re.X` (verbose)

---

---

## 9. `string` — String Constants `[MUST]`

| Constant / Function | Value / What it does |
|--------------------|---------------------|
| `string.ascii_lowercase` | `'abcdefghijklmnopqrstuvwxyz'` — useful for trie problems |
| `string.ascii_uppercase` | `'ABCDEFGHIJKLMNOPQRSTUVWXYZ'` |
| `string.ascii_letters` | Lowercase + uppercase combined |
| `string.digits` | `'0123456789'` |
| `string.hexdigits` | `'0123456789abcdefABCDEF'` |
| `string.octdigits` | `'01234567'` |
| `string.punctuation` | All punctuation characters |
| `string.whitespace` | Space, tab, newline, return, formfeed, vertical tab |
| `string.printable` | All printable characters |
| `string.Template(template)` | Template with `$variable` substitution |
| `string.capwords(s)` | Capitalize each word |

---

---

## 10. `copy` — Shallow and Deep Copy `[MUST]`

| Function | What it does |
|----------|--------------|
| `copy.copy(obj)` | **Shallow copy** — one level deep. References inside are shared. |
| `copy.deepcopy(obj)` | **Deep copy** — full recursive copy. Independent at all levels. |
| `copy.deepcopy(obj, memo)` | Deep copy with memo dict — handles circular references in graphs. |

> Critical in graph/grid/tree problems where you need independent state copies between recursive calls or BFS states.

```python
import copy

# Shallow copy — inner lists are still shared
grid_copy = copy.copy(grid)

# Deep copy — fully independent
grid_copy = copy.deepcopy(grid)
```

---

---

## 11. `typing` — Type Hints `[SENIOR]`

> Standard boilerplate on LeetCode. Makes code clearer in interviews, especially for custom classes.

| Type Hint | What it represents |
|-----------|--------------------|
| `List[int]` | List of ints |
| `Dict[str, int]` | Dict with str keys and int values |
| `Tuple[int, str]` | Fixed-length tuple |
| `Set[str]` | Set of strings |
| `Optional[int]` | `int` or `None` (same as `Union[int, None]`) |
| `Union[int, str]` | Either int or str |
| `Any` | Any type — disables type checking |
| `Callable[[int], str]` | Callable taking int, returning str |
| `Iterator[T]` | Iterator yielding T |
| `Generator[Y, S, R]` | Generator type |
| `TypeVar` | Generic type variable: `T = TypeVar('T')` |
| `Generic[T]` | Generic class base |
| `Protocol` | Structural subtyping (duck typing) |
| `Literal['a', 'b']` | Specific allowed values |
| `Final[int]` | Immutable — cannot be reassigned |
| `ClassVar[int]` | Class-level variable |
| `TypedDict` | Dict with typed keys |
| `NamedTuple` | Named tuple with types |
| `overload` | Overloaded function signatures |

---

---

## 12. `dataclasses` — Data Classes `[SENIOR]`

```python
from dataclasses import dataclass, field

@dataclass
class Node:
    val: int
    left: 'Node' = None
    right: 'Node' = None

@dataclass(order=True, frozen=True)   # frozen = hashable, order = comparison operators
class Point:
    x: float
    y: float
```

| Feature | What it does |
|---------|--------------|
| `@dataclass` | Auto-generates `__init__`, `__repr__`, `__eq__` |
| `@dataclass(order=True)` | Also generates `__lt__`, `__le__`, `__gt__`, `__ge__` |
| `@dataclass(frozen=True)` | Immutable — fields cannot be changed after init (enables hashing) |
| `field(default_factory=list)` | Mutable default (cannot use `[]` directly as default) |
| `field(repr=False)` | Exclude from `__repr__` |
| `field(compare=False)` | Exclude from `__eq__` and ordering |
| `fields(obj)` | Get all field descriptors |
| `asdict(obj)` | Convert to dict (recursive) |
| `astuple(obj)` | Convert to tuple (recursive) |
| `replace(obj, **changes)` | Create copy with changes |
| `__post_init__` | Run validation after auto-generated `__init__` |

---

---

## 13. `enum` — Enumerations `[SENIOR]`

```python
from enum import Enum, IntEnum, auto

class Direction(Enum):
    UP = 'U'
    DOWN = 'D'
    LEFT = 'L'
    RIGHT = 'R'

class Priority(Enum):
    LOW = auto()
    MEDIUM = auto()
    HIGH = auto()
```

| Feature | What it does |
|---------|--------------|
| `.name` | Name as string: `Direction.UP.name` → `'UP'` |
| `.value` | Underlying value: `Direction.UP.value` → `'U'` |
| `list(Direction)` | All members |
| `Direction['UP']` | Access by name |
| `Direction('U')` | Access by value |
| `@unique` | Enforce no two members share a value |
| `IntEnum` | Enum that is also an int (comparisons with int work) |
| `Flag` / `IntFlag` | Enum for bitwise operations (`\|`, `&`) |
| `Enum.__members__` | Dict of all member name → member |

---

---

## 14. `abc` — Abstract Base Classes `[SENIOR]`

| Feature | What it does |
|---------|--------------|
| `ABC` | Inherit from this to make abstract class |
| `ABCMeta` | Metaclass alternative to `ABC` |
| `@abstractmethod` | Subclass must override this method |
| `@abstractclassmethod` | Abstract class method |
| `@abstractstaticmethod` | Abstract static method |
| `@abstractproperty` | Abstract property |
| `register(cls)` | Register virtual subclass (duck typing) |
| `__subclasshook__` | Customise `isinstance` checks |

---

---

## 15. `json` — JSON Encoding/Decoding `[MUST]`

| Function | What it does |
|----------|--------------|
| `json.loads(string)` | JSON string → Python object |
| `json.dumps(obj)` | Python object → JSON string |
| `json.dumps(obj, indent=2)` | Pretty-printed JSON |
| `json.dumps(obj, sort_keys=True)` | Sorted keys |
| `json.dumps(obj, default=func)` | Custom serializer for non-standard types |
| `json.load(file)` | JSON file object → Python object |
| `json.dump(obj, file)` | Python object → JSON file object |
| `json.JSONDecodeError` | Exception on malformed JSON |

---

---

## 16. `datetime` — Date and Time `[MUST]`

| Class | Key Methods |
|-------|-------------|
| `datetime.date` | `today()`, `fromisoformat('YYYY-MM-DD')`, `.year`, `.month`, `.day`, `.weekday()` (Mon=0), `.isoweekday()` (Mon=1), `.isoformat()`, `.strftime(fmt)` |
| `datetime.time` | `.hour`, `.minute`, `.second`, `.microsecond`, `.isoformat()` |
| `datetime.datetime` | `now()`, `utcnow()`, `combine(date, time)`, `fromisoformat()`, `strptime(str, fmt)`, `strftime(fmt)`, `.timestamp()` |
| `datetime.timedelta` | `timedelta(days, hours, minutes, seconds)`, `.days`, `.seconds`, `.total_seconds()`, arithmetic with dates |
| `datetime.timezone` | `timezone.utc`, `timezone(timedelta(hours=5, minutes=30))` for IST |

---

---

## 17. `threading` / `concurrent.futures` `[SENIOR]`

### `threading`

| Class | Key Methods |
|-------|-------------|
| `Thread(target=fn, args=())` | `start()`, `join()`, `is_alive()`, `.daemon = True` |
| `Lock()` | `acquire()`, `release()`, `with lock:` context manager |
| `RLock()` | Re-entrant lock — same thread can acquire multiple times |
| `Semaphore(n)` | `acquire()`, `release()`, `with sem:` |
| `Event()` | `set()`, `clear()`, `wait()`, `is_set()` |
| `Condition(lock)` | `wait()`, `notify()`, `notify_all()`, `with cond:` |
| `Timer(t, fn)` | Run fn after t seconds |
| `Barrier(n)` | Wait until n threads arrive |
| `local()` | Thread-local storage |

### `concurrent.futures`

| Class / Function | What it does |
|-----------------|--------------|
| `ThreadPoolExecutor(max_workers=n)` | Thread pool for I/O-bound tasks |
| `ProcessPoolExecutor(max_workers=n)` | Process pool for CPU-bound tasks |
| `executor.submit(fn, *args)` | Submit single task → returns `Future` |
| `executor.map(fn, iterable)` | Map function over iterable |
| `Future.result(timeout)` | Block for result |
| `Future.done()` | Completed? |
| `Future.cancel()` | Cancel if not started |
| `as_completed(futures)` | Yield futures as they complete |
| `wait(futures, return_when)` | Wait with policy (FIRST_COMPLETED, ALL_COMPLETED) |

---

---

## 18. `asyncio` — Async / Await `[SENIOR]`

| Function / Class | What it does |
|-----------------|--------------|
| `asyncio.run(coro)` | Run coroutine — entry point (Python 3.7+) |
| `asyncio.gather(*coros)` | Run coroutines concurrently, collect results |
| `asyncio.create_task(coro)` | Schedule coroutine as Task (non-blocking) |
| `asyncio.sleep(seconds)` | Async sleep (yields control) |
| `asyncio.wait(tasks, return_when)` | Wait with policy |
| `asyncio.timeout(delay)` | Async timeout context manager (Python 3.11+) |
| `asyncio.Queue` | Async FIFO queue |
| `asyncio.Lock` | Async lock |
| `asyncio.Semaphore(n)` | Async semaphore |
| `asyncio.Event` | Async event |
| `asyncio.Condition` | Async condition variable |
| `asyncio.StreamReader/Writer` | Async stream I/O |
| `asyncio.get_event_loop()` | Get running event loop |
| `asyncio.current_task()` | Current running task |
| `asyncio.all_tasks()` | All pending tasks |

---

---

## 19. `copy`, `os`, `random`, `decimal`, `fractions` (Quick Reference)

| Module | Key Functions | Use in interviews |
|--------|--------------|------------------|
| `os` | `os.getcwd()`, `os.listdir()`, `os.makedirs()`, `os.environ`, `os.path.join()`, `os.path.exists()`, `os.path.basename()`, `os.walk()` | File system problems, scripting rounds |
| `random` | `random.random()`, `randint(a,b)`, `choice(seq)`, `choices(seq,k=n)`, `sample(pop,k)`, `shuffle(seq)`, `seed(n)`, `gauss(mu,sigma)` | Randomised algorithms, shuffling |
| `decimal` | `Decimal(str)`, `getcontext()`, `ROUND_HALF_UP`, `ROUND_DOWN` | Exact float arithmetic problems |
| `fractions` | `Fraction(num, denom)`, `.limit_denominator()` | Exact rational arithmetic |
| `statistics` | `mean()`, `median()`, `mode()`, `stdev()`, `variance()`, `quantiles()` | Data analysis questions |
| `pathlib` | `Path()`, `.read_text()`, `.write_text()`, `.glob()`, `.iterdir()`, `.stem`, `.suffix`, `path / 'sub'` | File system / scripting |
| `io` | `StringIO(str)`, `BytesIO(bytes)` | In-memory file-like objects, test input simulation |
| `operator` | `operator.itemgetter(n)`, `attrgetter('attr')`, `add`, `mul` | Sort key functions |
| `hashlib` | `hashlib.md5()`, `.sha256()`, `.hexdigest()` | Hashing problems |
| `struct` | `struct.pack(fmt, *v)`, `unpack(fmt, buf)` | Binary data problems |

---

---

## 20. Data Science & ML Packages `[DS/ML — product-based specialised roles only]`

> These are **third-party packages** (`pip install` required). Only permitted when the interview platform explicitly enables them — typically for Data Engineering, Data Science, or ML Engineer roles. **Not available in standard DSA rounds.**

---

### 20.1 `numpy` `[DS/ML]`

| Category | Key Functions |
|----------|--------------|
| Array creation | `np.array()`, `np.zeros()`, `np.ones()`, `np.eye()`, `np.arange()`, `np.linspace()`, `np.random.rand()`, `np.random.randn()`, `np.full()` |
| Shape | `.shape`, `.reshape()`, `.flatten()`, `.ravel()`, `np.expand_dims()`, `np.squeeze()`, `.T` (transpose) |
| Indexing | Boolean indexing `a[a > 0]`, fancy indexing `a[[0,2,4]]`, `np.where(condition, x, y)` |
| Math | `np.sum()`, `np.mean()`, `np.std()`, `np.min()`, `np.max()`, `np.argmin()`, `np.argmax()`, `np.cumsum()`, `np.diff()` |
| Linear algebra | `np.dot()`, `np.matmul()`, `@` operator, `np.linalg.inv()`, `np.linalg.det()`, `np.linalg.eig()`, `np.linalg.svd()`, `np.linalg.norm()` |
| Combine | `np.concatenate()`, `np.stack()`, `np.vstack()`, `np.hstack()`, `np.split()` |
| Sorting | `np.sort()`, `np.argsort()`, `np.partition()` |
| Special | Broadcasting rules, `np.clip()`, `np.unique()`, `np.bincount()`, `np.histogram()` |

### 20.2 `pandas` `[DS/ML]`

| Category | Key Methods |
|----------|-------------|
| Creation | `pd.DataFrame()`, `pd.Series()`, `pd.read_csv()`, `pd.read_json()`, `pd.read_excel()` |
| Inspection | `.head()`, `.tail()`, `.info()`, `.describe()`, `.shape`, `.dtypes`, `.columns`, `.index` |
| Selection | `.loc[rows, cols]`, `.iloc[rows, cols]`, `.at[row, col]`, `.iat[row, col]` |
| Filtering | `df[df['col'] > 5]`, `.query()`, `.isin()`, `.between()`, `.mask()` |
| Missing data | `.isnull()`, `.notnull()`, `.dropna()`, `.fillna()`, `.interpolate()` |
| Transform | `.apply()`, `.map()`, `.transform()`, `.assign()`, `.pipe()` |
| Aggregation | `.groupby().agg()`, `.pivot_table()`, `.crosstab()`, `.value_counts()`, `.nunique()` |
| Merging | `pd.merge(how='left/right/inner/outer')`, `.join()`, `pd.concat()` |
| Sorting | `.sort_values()`, `.sort_index()`, `.rank()`, `.nlargest()`, `.nsmallest()` |
| String ops | `.str.contains()`, `.str.replace()`, `.str.split()`, `.str.strip()`, `.str.extract()` |
| Time series | `.resample()`, `.rolling()`, `.shift()`, `pd.to_datetime()`, `.dt` accessor |
| Output | `.to_csv()`, `.to_json()`, `.to_dict()`, `.to_numpy()`, `.to_sql()` |

### 20.3 `scikit-learn` `[DS/ML]`

| Category | Key Classes/Functions |
|----------|-----------------------|
| Preprocessing | `StandardScaler`, `MinMaxScaler`, `LabelEncoder`, `OneHotEncoder`, `train_test_split`, `cross_val_score` |
| Classification | `LogisticRegression`, `RandomForestClassifier`, `SVC`, `KNeighborsClassifier`, `DecisionTreeClassifier` |
| Regression | `LinearRegression`, `Ridge`, `Lasso`, `ElasticNet`, `RandomForestRegressor` |
| Clustering | `KMeans`, `DBSCAN`, `AgglomerativeClustering` |
| Metrics | `accuracy_score`, `classification_report`, `confusion_matrix`, `roc_auc_score`, `mean_squared_error`, `f1_score` |
| Pipeline | `Pipeline`, `FeatureUnion`, `ColumnTransformer` |
| Tuning | `GridSearchCV`, `RandomizedSearchCV` |

### 20.4 `torch` (PyTorch) `[DS/ML — product ML teams]`

| Category | Key Classes/Functions |
|----------|-----------------------|
| Tensor ops | `torch.tensor()`, `.shape`, `.dtype`, `.to(device)`, `.cuda()`, `.cpu()`, `.numpy()`, `.item()` |
| Autograd | `.requires_grad`, `.backward()`, `.grad`, `torch.no_grad()`, `.detach()` |
| Neural net | `nn.Module`, `nn.Linear`, `nn.Conv2d`, `nn.ReLU`, `nn.Dropout`, `nn.BatchNorm1d`, `nn.Embedding`, `nn.LSTM`, `nn.Transformer` |
| Loss | `nn.CrossEntropyLoss`, `nn.MSELoss`, `nn.BCELoss`, `nn.NLLLoss`, `nn.BCEWithLogitsLoss` |
| Optimizer | `optim.Adam`, `optim.SGD`, `optim.AdamW`, `.step()`, `.zero_grad()` |
| Data | `Dataset`, `DataLoader`, `TensorDataset`, `random_split` |
| Saving | `torch.save()`, `torch.load()`, `model.state_dict()`, `model.load_state_dict()` |

---

---

## COMPANY-BY-COMPANY QUICK REFERENCE

### Google
- **Java:** Deep `java.util` (all collections), `java.util.stream` (all operators), `java.util.concurrent` (`CompletableFuture`, `ForkJoinPool`), JVM internals, modern Java 17–21 features, `BigInteger` for crypto problems
- **Python:** `collections`, `heapq`, `itertools`, `functools.lru_cache`/`cache`, `bisect`, `sys.setrecursionlimit`, `copy.deepcopy`
- **Focus:** Graph algorithms (BFS/DFS/Dijkstra), DP with memoization, system design with concurrency

### Amazon
- **Java:** `java.util` (`PriorityQueue` patterns, `LinkedHashMap` for LRU Cache), `java.util.concurrent` (`ExecutorService`), `java.util.stream`, exception hierarchy, `java.time`
- **Python:** `collections.defaultdict`, `collections.deque`, `heapq`, `bisect`, `functools.lru_cache`, `json`
- **Focus:** OOP design (LRU Cache, trie, snake game), sliding window, top-K

### Microsoft
- **Java:** All of Google list + OOP design patterns (Singleton, Builder, Observer), `java.lang.reflect`, Spring basics (experience interviews)
- **Python:** Full standard library, `typing`, `dataclasses`, `abc`
- **Focus:** System design, trees and graphs, string manipulation, low-level design

### Meta (Facebook)
- **Java:** `java.util.concurrent` deeply (`CompletableFuture`, parallel streams), `ConcurrentHashMap`, `AtomicInteger`
- **Python:** `collections`, `heapq`, `functools`, `asyncio`, `sys.setrecursionlimit`
- **Focus:** Graph problems (BFS/DFS heavy), union-find, interval merging

### TCS / Infosys / Wipro
- **Java:** `java.lang` (OOP), `java.util` (Collections basics), `java.io` (`BufferedReader`, `Scanner`, `StringTokenizer`), exception handling, JDBC basics, `java.util.Date/Calendar`
- **Python:** `collections`, basic `re`, `json`, `datetime`, `os`, `input().split()`
- **Focus:** Pattern programs, string manipulation, sorting, basic data structures, custom I/O parsing from `System.in` / `sys.stdin`

### Accenture / Cognizant / Capgemini
- **Java:** OOP concepts, `java.util.Collections`, `java.io`, basic multithreading, design patterns
- **Python:** `collections`, `itertools`, `re`, `json`, `csv`, scripting with `os`
- **Focus:** Arrays, strings, recursion, basic SQL integration, output matching

---

---

## DSA PATTERN → PACKAGE CHEAT SHEET

| DSA Pattern | Java Package / Class | Python Package / Function |
|-------------|---------------------|--------------------------|
| Sliding Window | `int[]`, `HashMap` | `collections.defaultdict`, `list` |
| Two Pointers | `int[]`, primitives | `list` |
| Binary Search | `Arrays.binarySearch()`, `TreeMap.floorKey()` | `bisect.bisect_left()`, `bisect.bisect_right()` |
| BFS | `ArrayDeque` as `Queue` | `collections.deque` — **never `list` as queue** |
| DFS | `ArrayDeque` (stack) or recursion | `collections.deque` or recursion + `sys.setrecursionlimit` |
| Min-Heap / Top-K | `PriorityQueue<Integer>` | `heapq` |
| Max-Heap | `PriorityQueue<>(Collections.reverseOrder())` | negate values × −1, use `heapq` |
| Frequency Count | `HashMap<Character, Integer>` | `collections.Counter` |
| Graph Adjacency List | `HashMap<Integer, List<Integer>>` | `collections.defaultdict(list)` |
| Union-Find | `int[] parent`, `int[] rank` | `int[] parent`, `int[] rank` or `{node: parent}` dict |
| Memoization / Top-Down DP | `HashMap`, `int[][]` | `@functools.lru_cache(None)` or `@functools.cache` |
| LRU Cache (design) | `LinkedHashMap` (access-order mode) | `collections.OrderedDict` with `move_to_end` |
| Trie | Custom `TrieNode` class | Custom `dict`-based class or `defaultdict(dict)` |
| Monotonic Stack | `ArrayDeque<Integer>` | `list` as stack |
| Prefix Sum | `int[]` | `list`, `itertools.accumulate()` |
| Permutations / Combos | Backtracking recursion | `itertools.permutations()`, `itertools.combinations()` |
| Bit Manipulation | `Integer.bitCount()`, `>>>` operator | `bin()`, `int.bit_count()` (Python 3.10+) |
| Custom Sort | `Arrays.sort(arr, (a,b) -> ...)` | `sorted(lst, key=lambda x: ...)`, `functools.cmp_to_key` |
| String Parsing | `String.split()`, `java.util.regex.Pattern` | `re.findall()`, `re.split()`, `str.split()` |
| String Building | `StringBuilder` — **never `+` in loops** | `''.join(list)` — **never `str +=` in loops** |
| Concurrency (DSA) | `java.util.concurrent` | `asyncio`, `concurrent.futures` |

