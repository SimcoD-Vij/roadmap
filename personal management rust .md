# Go and Rust: Complete Zero-to-Integration Teaching Guide
## For ACOS — From No Knowledge to Production Implementation

---

> **How this document works.** This is a complete language course built specifically around ACOS. You learn Go and Rust exactly as far as you need to build the components identified in the ACOS roadmap — no further, no less. Every concept is explained from first principles, every example builds toward ACOS, and every chapter ends with a working piece of your system. You do not study these languages in isolation and then try to apply them later. You learn them by building.

---

# PART ONE — GO LANGUAGE
## From Zero to Building the ACOS Reminder Engine and Advisor Orchestrator

---

## CHAPTER 1 — What Go Is and Why Your Brain Will Like It

### The origin story

In 2007, three engineers at Google — Robert Griesemer, Rob Pike, and Ken Thompson — were waiting 45 minutes for a C++ codebase to compile. They decided to build a new language. Their constraints: it must compile in seconds, it must be as fast as C for network services, it must make concurrency feel natural, and it must be so simple that any engineer can read any other engineer's Go code without a style guide.

They succeeded. Go compiles a million lines of code in under a second. A Go HTTP server handles hundreds of thousands of simultaneous connections. And the language has 25 keywords — JavaScript has 64, Java has 52, Python has 35. Go is deliberately small.

### What Go is good at and why it fits ACOS

Go was built for programs that wait for many things simultaneously — network requests, file reads, timer events. Your ACOS Advisor orchestrator fires Reddit, YouTube, Wikipedia, and your knowledge base simultaneously and waits for all of them. In Python this is cooperative: if one search does CPU work, the others pause. In Go, each search is a goroutine on a real OS thread — truly simultaneous. Your Reminder Engine needs to deliver a notification at precisely 9:00 AM — Go's timer fires with millisecond accuracy. Python's Celery beat is accurate to within ±30 seconds.

### The three things that make Go different from Python

**First: Go is statically typed.** You declare what type a variable holds and the compiler checks every use at compile time. `var name string = "ACOS"` — the compiler knows `name` is a string forever. If you try to add a number to it, the code does not compile. This catches entire categories of bugs before your program runs.

**Second: Go has no class inheritance.** Coming from Python where `class Dog(Animal)` is natural, Go feels strange at first. Go uses composition and interfaces instead. You will understand why this is actually simpler once you see it.

**Third: Go's concurrency is built into the language.** `go doSomething()` starts a new goroutine — a function running concurrently. This is not a library feature; it is a language keyword. Channels (`chan`) are typed pipes between goroutines. These two features are why Go exists.

---

## CHAPTER 2 — Go Syntax: Reading and Writing Go for the First Time

### Installing Go

```bash
# Download Go 1.23
wget https://go.dev/dl/go1.23.0.linux-amd64.tar.gz

# Extract to /usr/local
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.23.0.linux-amd64.tar.gz

# Add to PATH permanently
echo 'export PATH=$PATH:/usr/local/go/bin' >> ~/.bashrc
echo 'export GOPATH=$HOME/go' >> ~/.bashrc
source ~/.bashrc

# Verify
go version
# Output: go version go1.23.0 linux/amd64

# VS Code extension (install after opening VS Code)
code --install-extension golang.go
# This gives you: autocomplete, inline errors, format on save, test runner
```

### Your first Go program — reading every line

Create a directory and file:
```bash
mkdir ~/go-learning
cd ~/go-learning
mkdir hello
cd hello
```

Create `main.go`:
```go
// Every Go file begins with a package declaration.
// 'main' is special: it tells Go this file creates an executable program.
// Library packages (like your ACOS components) use a different name.
package main

// import brings in other packages.
// "fmt" is the format package — it handles printing.
// Parentheses group multiple imports.
import (
    "fmt"
)

// func main() is the entry point — the first function Go runs.
// It takes no parameters and returns nothing.
func main() {
    // fmt.Println prints a line to standard output.
    // Note: no semicolons in Go. The compiler infers them.
    fmt.Println("Hello from ACOS")
}
```

Run it:
```bash
go run main.go
# Output: Hello from ACOS
```

Now build it into a binary:
```bash
go build -o hello .
./hello
# Output: Hello from ACOS
```

The binary `./hello` has no dependencies. It runs on any Linux machine without Go installed. This is why Go services deploy as single files — no Python interpreter, no virtualenv, no pip install.

### Variables — five ways to declare them

```go
package main

import "fmt"

func main() {
    // Way 1: var with explicit type
    var name string = "ACOS"

    // Way 2: var with type inference (Go figures out the type from the value)
    var version = 1

    // Way 3: short declaration — most common inside functions
    // := means "declare and assign". Only works inside functions.
    city := "Chennai"

    // Way 4: multiple variables at once
    var (
        host string = "localhost"
        port int    = 8000
    )

    // Way 5: constants — value never changes
    const maxNotes = 1_000_000  // Underscore in numbers is visual only

    fmt.Println(name, version, city, host, port, maxNotes)
}
```

The key rules:
- `var` can be used anywhere (inside or outside functions)
- `:=` only inside functions
- Go **requires** every declared variable to be used — unused variables are compile errors
- Go **requires** every imported package to be used — unused imports are compile errors

This strictness feels annoying at first. You will come to love it — it means every line of Go code you read is intentional.

### Types — what Go knows about your data

```go
package main

import "fmt"

func main() {
    // ── Numeric types ──────────────────────────────────────────
    var i int     = 42          // Platform-dependent: 64-bit on 64-bit systems
    var i8 int8   = 127         // -128 to 127
    var i64 int64 = 9_000_000   // Explicitly 64-bit
    var f32 float32 = 3.14      // 32-bit float
    var f64 float64 = 3.141592  // 64-bit float (default for floating point)

    // For ACOS: use int64 for node IDs (they can grow large)
    // Use float32 for embeddings (saves memory: 384 × 4 bytes vs 384 × 8 bytes)
    // Use float64 for scores and probabilities (precision matters)

    // ── Strings ────────────────────────────────────────────────
    note := "Tried amazing filter coffee near Marina Beach"
    // Strings in Go are immutable byte sequences (UTF-8)
    // len(note) returns bytes, not characters
    length := len(note)  // Returns number of bytes

    // ── Booleans ───────────────────────────────────────────────
    enriched := false
    verified := true
    _ = enriched  // Suppress "unused variable" error for this example
    _ = verified

    // ── Printing types ─────────────────────────────────────────
    // %T prints the type, %v prints the value
    fmt.Printf("i=%v type=%T\n", i, i)
    fmt.Printf("f64=%v type=%T\n", f64, f64)
    fmt.Printf("note length=%d\n", length)

    // Suppress "declared but not used" for demo variables
    _, _, _ = i8, i64, f32
}
```

### Functions — the building blocks of ACOS Go services

```go
package main

import (
    "errors"
    "fmt"
    "strings"
)

// ── Basic function ──────────────────────────────────────────────────────────
// func name(param type, param type) returnType { body }
func greet(name string) string {
    return "Hello, " + name
}

// ── Multiple return values ──────────────────────────────────────────────────
// Go functions commonly return (result, error) — this is the standard pattern
// for anything that can fail. You will see this pattern EVERYWHERE in Go.
func divide(a, b float64) (float64, error) {
    if b == 0 {
        // errors.New creates a simple error value
        return 0, errors.New("cannot divide by zero")
    }
    return a / b, nil  // nil means "no error"
}

// ── Named return values ─────────────────────────────────────────────────────
// Names the return values — they act like pre-declared variables
// Useful for documentation, but avoid "naked returns" (return with no values)
func splitText(text string) (words []string, count int) {
    words = strings.Fields(text)  // Split on whitespace
    count = len(words)
    return  // "naked return" — returns words and count
}

// ── Variadic functions — variable number of arguments ──────────────────────
func sumScores(scores ...float64) float64 {
    total := 0.0
    for _, score := range scores {
        total += score
    }
    return total
}

func main() {
    // Calling basic function
    fmt.Println(greet("ACOS"))

    // Handling errors — the standard Go pattern
    result, err := divide(10, 3)
    if err != nil {
        fmt.Println("Error:", err)
    } else {
        fmt.Printf("10 / 3 = %.4f\n", result)
    }

    // This one will error
    _, err = divide(5, 0)
    if err != nil {
        fmt.Println("Error caught:", err)
    }

    // Multiple return values
    words, count := splitText("Operating system scheduler decides process order")
    fmt.Printf("Words: %v, Count: %d\n", words, count)

    // Variadic
    total := sumScores(0.8, 0.95, 0.72, 0.88)
    fmt.Printf("Total score: %.2f\n", total)
}
```

**The error handling pattern is the most important thing in Go.** Every operation that can fail returns `(result, error)`. You check `if err != nil` immediately. There is no try/catch in Go. This makes every failure point visible in the code — you cannot accidentally ignore an error (well, you can with `_`, but it is explicit and reviewable).

### Control flow — if, for, switch

```go
package main

import "fmt"

func classifyNote(text string, wordCount int) string {
    // ── if / else if / else ────────────────────────────────────────────────
    // Note: no parentheses around the condition (unlike Python's if condition:)
    // Note: braces are required even for single-line bodies
    if wordCount == 0 {
        return "empty"
    } else if wordCount < 5 {
        return "too_short"
    } else if wordCount > 500 {
        return "too_long"
    }

    // ── if with initialisation statement ──────────────────────────────────
    // You can initialise a variable in the if condition
    // The variable 'score' is scoped to this if-else block
    if score := computeScore(text); score > 0.8 {
        return "high_confidence"
    } else if score > 0.5 {
        return "medium_confidence"
    } else {
        return "low_confidence"
    }
}

func computeScore(text string) float64 {
    // Simplified — real version calls the classifier
    if len(text) > 20 {
        return 0.85
    }
    return 0.3
}

func main() {
    // ── for loop — Go's only loop construct ───────────────────────────────
    // Go has no while loop. 'for' covers all looping.

    // Traditional C-style for
    for i := 0; i < 5; i++ {
        fmt.Printf("Step %d\n", i)
    }

    // "While" style — condition only
    count := 0
    for count < 3 {
        fmt.Println("counting:", count)
        count++
    }

    // Infinite loop with break
    attempts := 0
    for {
        attempts++
        if attempts >= 3 {
            break
        }
        fmt.Println("attempt", attempts)
    }

    // ── range — iterate over slices, maps, strings, channels ──────────────
    noteTypes := []string{"place", "technical", "creative", "reminder", "media"}
    for index, noteType := range noteTypes {
        fmt.Printf("%d: %s\n", index, noteType)
    }

    // Ignore index with _
    for _, noteType := range noteTypes {
        fmt.Println(noteType)
    }

    // ── switch — cleaner than long if-else chains ──────────────────────────
    contentType := "place"
    switch contentType {
    case "place":
        fmt.Println("Enriching with Maps API")
    case "technical":
        fmt.Println("Linking to GitHub")
    case "creative":
        fmt.Println("Finding historical parallels")
    default:
        fmt.Println("Standard enrichment")
    }

    // Switch with no condition — replaces long if-else chains
    score := 0.75
    switch {
    case score >= 0.9:
        fmt.Println("Deep understanding")
    case score >= 0.7:
        fmt.Println("Structural understanding")
    default:
        fmt.Println("Surface understanding")
    }

    fmt.Println(classifyNote("Interesting concept about OS scheduling", 6))
}
```

### Slices and Maps — Go's essential data structures

```go
package main

import "fmt"

func main() {
    // ── Slices — dynamic arrays ───────────────────────────────────────────
    // A slice is a view into an underlying array.
    // It has: length (current elements), capacity (allocated space)

    // Create a slice with a literal
    tags := []string{"java", "concurrency", "threads"}

    // Append to a slice
    tags = append(tags, "synchronisation")
    fmt.Println(tags)  // [java concurrency threads synchronisation]

    // Make a slice with initial length and capacity
    embeddings := make([]float32, 384)  // 384 zeros for a 384-dim embedding
    embeddings[0] = 0.123
    fmt.Printf("Embedding dim 0: %.3f, length: %d\n", embeddings[0], len(embeddings))

    // Slice of slices — batch of embeddings
    batch := make([][]float32, 0)  // Empty slice
    for i := 0; i < 3; i++ {
        emb := make([]float32, 384)
        emb[0] = float32(i) * 0.1
        batch = append(batch, emb)
    }
    fmt.Printf("Batch size: %d, each dim: %d\n", len(batch), len(batch[0]))

    // Slicing a slice: [start:end] (end is exclusive)
    firstTwo := tags[0:2]
    fmt.Println("First two tags:", firstTwo)  // [java concurrency]

    // ── Maps — key-value store ─────────────────────────────────────────────
    // map[KeyType]ValueType
    // Go maps are similar to Python dicts

    // Literal initialisation
    noteMetadata := map[string]string{
        "source":       "manual",
        "content_type": "technical",
        "verified":     "false",
    }

    // Read a value
    contentType := noteMetadata["content_type"]
    fmt.Println("Type:", contentType)

    // Read with "ok" pattern — check if key exists
    value, ok := noteMetadata["nonexistent"]
    if !ok {
        fmt.Println("Key not found, value is zero value:", value)
    }

    // Update
    noteMetadata["verified"] = "true"

    // Delete
    delete(noteMetadata, "source")

    // Iterate
    for key, val := range noteMetadata {
        fmt.Printf("  %s: %s\n", key, val)
    }

    // Map with int values — counting note types
    typeCounts := map[string]int{
        "place":     15,
        "technical": 42,
        "creative":  8,
    }
    for noteType, count := range typeCounts {
        fmt.Printf("  %s: %d notes\n", noteType, count)
    }
}
```

### Structs — Go's way of grouping data

```go
package main

import (
    "fmt"
    "time"
)

// A struct groups related data together.
// This is Go's equivalent of a Python class without methods yet.
// Capital letter = exported (usable outside this package)
// Lowercase letter = unexported (private to this package)

type Note struct {
    ID          int64
    PublicID    string
    RawText     string
    ContentType string
    Tags        []string
    Embedding   []float32
    Enriched    bool
    CreatedAt   time.Time
    Metadata    map[string]string
}

// Methods on structs — attach behaviour to data
// (receiver variable) is the "self" equivalent
// The convention is a short lowercase abbreviation of the type name
func (n Note) Summary() string {
    if len(n.RawText) > 50 {
        return n.RawText[:50] + "..."
    }
    return n.RawText
}

// Pointer receiver — use when the method modifies the struct
// Without the *, you get a copy — changes are lost
func (n *Note) AddTag(tag string) {
    n.Tags = append(n.Tags, tag)
}

func (n *Note) MarkEnriched() {
    n.Enriched = true
}

// Constructor function — Go doesn't have constructors
// but by convention you write a function named New{Type}
func NewNote(rawText, contentType string) *Note {
    return &Note{
        RawText:     rawText,
        ContentType: contentType,
        Tags:        make([]string, 0),
        Embedding:   make([]float32, 384),
        CreatedAt:   time.Now(),
        Metadata:    make(map[string]string),
    }
}

type PlaceExtension struct {
    NoteID     int64
    Lat        float64
    Lng        float64
    PlaceName  string
    Address    string
    UserRating int
}

func main() {
    // Creating a struct — struct literal
    note := Note{
        ID:          42,
        RawText:     "Amazing filter coffee near Marina Beach with sunset view",
        ContentType: "place",
        Tags:        []string{"coffee", "view"},
        CreatedAt:   time.Now(),
    }

    // Access fields with dot notation
    fmt.Println("Note ID:", note.ID)
    fmt.Println("Summary:", note.Summary())

    // Using the constructor
    newNote := NewNote("Java virtual threads make millions of connections feasible", "technical")
    newNote.AddTag("java")
    newNote.AddTag("concurrency")
    newNote.MarkEnriched()

    fmt.Printf("New note: %+v\n", newNote)  // %+v prints field names too

    // Pointer to struct
    placeExt := &PlaceExtension{
        NoteID:    42,
        Lat:       13.0499,
        Lng:       80.2730,
        PlaceName: "Filter Coffee Rooftop",
        Address:   "Besant Nagar, Chennai",
        UserRating: 5,
    }
    fmt.Printf("Place: %s at (%.4f, %.4f)\n", placeExt.PlaceName, placeExt.Lat, placeExt.Lng)
}
```

### Interfaces — Go's most powerful abstraction

```go
package main

import (
    "context"
    "fmt"
    "time"
)

// An interface defines behaviour — a set of method signatures.
// Any type that has all these methods automatically implements the interface.
// You never write "implements SearchSource" — it is implicit.

type SearchResult struct {
    Source   string
    Title    string
    Summary  string
    URL      string
    Score    float64
}

// This is the interface all ACOS search tools implement
type SearchSource interface {
    Name() string
    Search(ctx context.Context, query string) ([]SearchResult, error)
}

// ── Concrete type 1: Reddit scraper ────────────────────────────────────────
type RedditSource struct {
    Subreddit string
    client    interface{} // In real code: *http.Client
}

func (r *RedditSource) Name() string {
    return "reddit:" + r.Subreddit
}

func (r *RedditSource) Search(ctx context.Context, query string) ([]SearchResult, error) {
    // Real implementation calls Reddit JSON API
    // For now, simulate with fake data
    fmt.Printf("  [%s] Searching for: %s\n", r.Name(), query)
    time.Sleep(50 * time.Millisecond) // Simulate network latency
    return []SearchResult{
        {
            Source:  r.Name(),
            Title:   "Best resources for: " + query,
            Summary: "Top Reddit recommendations from r/" + r.Subreddit,
            Score:   0.87,
        },
    }, nil
}

// ── Concrete type 2: YouTube search ────────────────────────────────────────
type YouTubeSource struct {
    APIKey string
}

func (y *YouTubeSource) Name() string { return "youtube" }

func (y *YouTubeSource) Search(ctx context.Context, query string) ([]SearchResult, error) {
    fmt.Printf("  [youtube] Searching for: %s\n", query)
    time.Sleep(80 * time.Millisecond)
    return []SearchResult{
        {
            Source:  "youtube",
            Title:   query + " — Complete Tutorial",
            Summary: "Highly rated video tutorial covering " + query,
            Score:   0.82,
        },
    }, nil
}

// ── Concrete type 3: Knowledge base search (calls your ACOS API) ───────────
type KnowledgeBaseSource struct {
    ACOSBaseURL string
}

func (k *KnowledgeBaseSource) Name() string { return "knowledge_base" }

func (k *KnowledgeBaseSource) Search(ctx context.Context, query string) ([]SearchResult, error) {
    fmt.Printf("  [knowledge_base] Searching your notes for: %s\n", query)
    time.Sleep(20 * time.Millisecond)
    return []SearchResult{
        {
            Source:  "knowledge_base",
            Title:   "Your note from 3 weeks ago",
            Summary: "You previously documented related concepts about " + query,
            Score:   0.94,
        },
    }, nil
}

// ── The Orchestrator — uses any SearchSource without knowing the concrete type ─
type AdvisorOrchestrator struct {
    sources []SearchSource  // A slice of the interface type
}

func NewOrchestrator(sources ...SearchSource) *AdvisorOrchestrator {
    return &AdvisorOrchestrator{sources: sources}
}

// This function does not know or care what concrete types are in sources.
// It just calls Name() and Search() — both defined by the interface.
func (o *AdvisorOrchestrator) Search(ctx context.Context, query string) []SearchResult {
    resultsCh := make(chan []SearchResult, len(o.sources))

    // Launch all searches concurrently — this is the core Go advantage
    for _, src := range o.sources {
        src := src // Capture for goroutine (important in older Go versions)
        go func() {
            results, err := src.Search(ctx, query)
            if err != nil {
                fmt.Printf("  Source %s failed: %v\n", src.Name(), err)
                resultsCh <- nil
                return
            }
            resultsCh <- results
        }()
    }

    // Collect all results
    var all []SearchResult
    for i := 0; i < len(o.sources); i++ {
        if results := <-resultsCh; results != nil {
            all = append(all, results...)
        }
    }
    return all
}

func main() {
    // Build the orchestrator with all sources
    orchestrator := NewOrchestrator(
        &RedditSource{Subreddit: "cscareerquestions"},
        &YouTubeSource{APIKey: "your_key"},
        &KnowledgeBaseSource{ACOSBaseURL: "http://localhost:8000"},
    )

    fmt.Println("Starting parallel search...")
    start := time.Now()

    ctx := context.Background()
    results := orchestrator.Search(ctx, "system design interview preparation")

    elapsed := time.Since(start)
    fmt.Printf("\nCompleted in %v (all sources ran in parallel)\n", elapsed)
    fmt.Printf("Total results: %d\n\n", len(results))

    for _, r := range results {
        fmt.Printf("[%s] %.2f — %s\n", r.Source, r.Score, r.Title)
    }
}
```

Run this and observe: all three searches take ~80ms total (the slowest one) rather than 50+80+20=150ms sequentially. That is Go's value for ACOS in one demonstration.

---

## CHAPTER 3 — Go Concurrency: The Goroutine and Channel System

### The goroutine — lighter than a thread, cheaper than a process

```go
package main

import (
    "fmt"
    "sync"
    "time"
)

// A goroutine is a function running concurrently with other functions.
// Starting one costs about 2KB of memory (vs ~1MB for an OS thread).
// You can have millions of goroutines without running out of memory.

func fetchFromReddit(query string, wg *sync.WaitGroup) {
    defer wg.Done()  // Decrement counter when this function returns
    time.Sleep(50 * time.Millisecond)  // Simulate HTTP call
    fmt.Printf("Reddit done: %s\n", query)
}

func fetchFromYouTube(query string, wg *sync.WaitGroup) {
    defer wg.Done()
    time.Sleep(80 * time.Millisecond)
    fmt.Printf("YouTube done: %s\n", query)
}

func fetchFromKnowledgeBase(query string, wg *sync.WaitGroup) {
    defer wg.Done()
    time.Sleep(20 * time.Millisecond)
    fmt.Printf("KB done: %s\n", query)
}

func main() {
    query := "backend engineering job search Chennai"

    // WaitGroup counts running goroutines
    // We start with 3, each Done() decrements by 1
    // Wait() blocks until count reaches 0
    var wg sync.WaitGroup

    start := time.Now()

    wg.Add(3)  // We're starting 3 goroutines
    go fetchFromReddit(query, &wg)
    go fetchFromYouTube(query, &wg)
    go fetchFromKnowledgeBase(query, &wg)

    wg.Wait()  // Block here until all 3 finish

    fmt.Printf("Total time: %v (sequential would be ~150ms)\n", time.Since(start))
    // Output: ~80ms — the time of the SLOWEST goroutine, not the sum
}
```

### Channels — the safe way goroutines communicate

```go
package main

import (
    "context"
    "fmt"
    "time"
)

type SearchResult struct {
    Source  string
    Content string
    Error   error
}

// Channels are typed pipes between goroutines.
// send: ch <- value
// receive: value := <-ch
// A channel blocks the sender until someone reads, and blocks the reader until someone sends
// (unless buffered)

func search(ctx context.Context, source, query string, delay time.Duration) SearchResult {
    // Select lets you wait on multiple channels simultaneously
    select {
    case <-ctx.Done():
        // Context was cancelled (timeout or explicit cancel)
        return SearchResult{Source: source, Error: ctx.Err()}
    case <-time.After(delay):
        // Simulated search completed
        return SearchResult{
            Source:  source,
            Content: fmt.Sprintf("[%s] result for: %s", source, query),
        }
    }
}

func parallelSearch(ctx context.Context, query string) []SearchResult {
    sources := []struct {
        name  string
        delay time.Duration
    }{
        {"reddit", 50 * time.Millisecond},
        {"youtube", 80 * time.Millisecond},
        {"knowledge_base", 20 * time.Millisecond},
        {"arxiv", 120 * time.Millisecond},
        {"web", 60 * time.Millisecond},
    }

    // Buffered channel: holds up to len(sources) results without blocking senders
    resultsCh := make(chan SearchResult, len(sources))

    // Start all searches as goroutines
    for _, src := range sources {
        src := src
        go func() {
            result := search(ctx, src.name, query, src.delay)
            resultsCh <- result  // Send result to channel
        }()
    }

    // Collect exactly len(sources) results
    var results []SearchResult
    for i := 0; i < len(sources); i++ {
        result := <-resultsCh  // Receive from channel
        if result.Error == nil {
            results = append(results, result)
        }
    }
    return results
}

func main() {
    // Context with 500ms timeout — if any search takes longer, it is cancelled
    ctx, cancel := context.WithTimeout(context.Background(), 500*time.Millisecond)
    defer cancel()  // Always defer cancel to free resources

    start := time.Now()
    results := parallelSearch(ctx, "machine learning system design")
    elapsed := time.Since(start)

    fmt.Printf("Got %d results in %v\n", len(results), elapsed)
    // ~120ms — time of slowest (arxiv), not sum of all (330ms)

    for _, r := range results {
        fmt.Println(" ", r.Content)
    }
}
```

### The select statement — wait on multiple channels

```go
package main

import (
    "fmt"
    "time"
)

// select is like a switch for channels.
// It waits until one of the cases is ready, then runs that case.
// If multiple are ready simultaneously, Go picks one at random.

func reminderTimer(message string, delay time.Duration) <-chan string {
    ch := make(chan string, 1)
    go func() {
        time.Sleep(delay)
        ch <- message
    }()
    return ch
}

func main() {
    reminder1 := reminderTimer("Study Java concurrency", 100*time.Millisecond)
    reminder2 := reminderTimer("Review OS scheduling notes", 200*time.Millisecond)
    timeout := time.After(500 * time.Millisecond)

    // Process reminders as they arrive, stop after timeout
    for {
        select {
        case msg := <-reminder1:
            fmt.Println("Reminder 1 fired:", msg)
        case msg := <-reminder2:
            fmt.Println("Reminder 2 fired:", msg)
        case <-timeout:
            fmt.Println("Session complete")
            return
        }
    }
}
```

---

## CHAPTER 4 — Go Error Handling and Project Structure

### Error handling — explicit and exhaustive

```go
package main

import (
    "errors"
    "fmt"
)

// Define custom error types for ACOS
// errors.New creates a simple error value
var (
    ErrNoteEmpty      = errors.New("note text cannot be empty")
    ErrNoteTooLong    = errors.New("note text exceeds maximum length")
    ErrEnrichmentFail = errors.New("enrichment service unavailable")
)

// Wrapping errors preserves context while adding your own message
// Use %w to wrap — then errors.Is() can check the chain
type ValidationError struct {
    Field   string
    Message string
}

func (e *ValidationError) Error() string {
    return fmt.Sprintf("validation error on field '%s': %s", e.Field, e.Message)
}

func validateNote(text string) error {
    if len(text) == 0 {
        return ErrNoteEmpty
    }
    if len(text) > 50_000 {
        return ErrNoteTooLong
    }
    return nil
}

func enrichNote(noteID int64) error {
    // Simulate a wrapped error
    apiErr := fmt.Errorf("maps API returned 429: rate limited")
    return fmt.Errorf("enriching note %d: %w", noteID, ErrEnrichmentFail)
    _ = apiErr
}

func processNote(text string) error {
    if err := validateNote(text); err != nil {
        // Wrap to add context
        return fmt.Errorf("processing note: %w", err)
    }
    return nil
}

func main() {
    // errors.Is checks anywhere in the error chain
    err := processNote("")
    if errors.Is(err, ErrNoteEmpty) {
        fmt.Println("Empty note error detected:", err)
    }

    // Check enrichment error
    err = enrichNote(42)
    if errors.Is(err, ErrEnrichmentFail) {
        fmt.Println("Enrichment failed:", err)
    }

    // Type assertion to get custom error details
    customErr := &ValidationError{Field: "raw_text", Message: "contains banned content"}
    err = fmt.Errorf("note rejected: %w", customErr)

    var valErr *ValidationError
    if errors.As(err, &valErr) {
        fmt.Printf("Validation failed on field: %s\n", valErr.Field)
    }
}
```

### Go project structure and modules

```bash
# Initialise a Go module — do this once per Go service
cd ~/acos/src/workers/reminders
go mod init github.com/yourusername/acos/reminders
# This creates go.mod — tracks your module path and dependencies

# Add a dependency
go get github.com/redis/go-redis/v9
# This updates go.mod and creates go.sum (lockfile)

# Remove unused dependencies
go mod tidy

# The go.sum file is generated automatically — commit it to git
# It contains cryptographic hashes of every dependency version
```

```
src/workers/reminders/        ← One Go module = one service
├── go.mod                    ← Module definition
├── go.sum                    ← Dependency lockfile
├── main.go                   ← Entry point
├── internal/                 ← Private packages (cannot be imported outside this module)
│   ├── reminder/
│   │   ├── reminder.go       ← Reminder struct and business logic
│   │   └── reminder_test.go  ← Tests for reminder package
│   ├── delivery/
│   │   ├── ntfy.go           ← ntfy.sh notification sender
│   │   └── ntfy_test.go
│   └── storage/
│       ├── postgres.go       ← PostgreSQL operations
│       └── redis.go          ← Redis operations
└── Dockerfile
```

### Writing Go tests

```go
// File: internal/reminder/reminder_test.go
package reminder

import (
    "testing"
    "time"
)

// Go tests are in files ending with _test.go
// Test function names start with Test and take *testing.T

func TestNewReminder(t *testing.T) {
    r := Reminder{
        ID:       1,
        Message:  "Study Java threads",
        RemindAt: time.Now().Add(1 * time.Hour),
    }

    if r.ID != 1 {
        t.Errorf("expected ID=1, got %d", r.ID)
    }
    if r.Message == "" {
        t.Error("message should not be empty")
    }
}

func TestIsOverdue(t *testing.T) {
    // Table-driven tests — the Go standard pattern for testing multiple cases
    cases := []struct {
        name     string
        remindAt time.Time
        want     bool
    }{
        {
            name:     "future reminder is not overdue",
            remindAt: time.Now().Add(1 * time.Hour),
            want:     false,
        },
        {
            name:     "past reminder is overdue",
            remindAt: time.Now().Add(-1 * time.Hour),
            want:     true,
        },
        {
            name:     "reminder due exactly now",
            remindAt: time.Now().Add(-1 * time.Millisecond),
            want:     true,
        },
    }

    for _, tc := range cases {
        t.Run(tc.name, func(t *testing.T) {
            r := &Reminder{RemindAt: tc.remindAt}
            got := r.IsOverdue()
            if got != tc.want {
                t.Errorf("IsOverdue() = %v, want %v", got, tc.want)
            }
        })
    }
}

// Run tests: go test ./...
// Run with coverage: go test -cover ./...
// Run specific test: go test -run TestIsOverdue ./internal/reminder/
```

---

# PART TWO — RUST LANGUAGE
## From Zero to Building the ACOS Knowledge Graph Engine and Embedding System

---

## CHAPTER 5 — What Rust Is and Why It Exists

### The problem Rust solves

In 2006, a Mozilla engineer named Graydon Hoare was frustrated. He had just come home to find that his apartment building's elevator was out of service due to a software crash — caused by a memory safety bug in the elevator's C code. He started writing a new language that would make memory bugs impossible.

That language became Rust. In 2023, the US government's National Security Agency officially recommended Rust as a memory-safe alternative to C and C++. Microsoft has been rewriting Windows kernel components in Rust. The Linux kernel now accepts Rust code. Android is migrating security-sensitive code to Rust.

The core promise: Rust programs run as fast as C but cannot have the memory bugs that make C dangerous. No null pointer dereferences. No use-after-free. No data races between threads. These guarantees are checked at compile time — if your code compiles, these bugs are provably absent.

### Why Rust for ACOS

ACOS needs Rust in exactly two situations. First: CPU-bound computation over large datasets. The Knowledge Graph Builder compares a new note against 10,000 existing notes — 10,000 set operations. In Python this takes 2 seconds. In Rust with all CPU cores working in parallel it takes 40 milliseconds. Second: code that needs correctness guarantees. The mobile sync engine handles conflict resolution — if it has a bug, notes disappear. Rust's type system makes certain categories of bugs impossible.

### Rust's single most important concept: ownership

Every other language either uses a garbage collector (Python, Go, Java) or makes you manage memory manually (C, C++). Rust has a third approach: the compiler tracks ownership statically. At compile time, the compiler knows exactly when every piece of memory is no longer needed and inserts the cleanup code automatically. Zero runtime overhead, zero garbage collection pauses, zero manual memory management bugs.

The three rules of ownership:
1. Every value has exactly one owner
2. When the owner goes out of scope, the value is dropped (freed)
3. There can be any number of immutable borrows, OR exactly one mutable borrow, but never both simultaneously

These three rules eliminate the entire class of memory safety bugs. They take 1-2 weeks to fully internalise. Every beginner Rust programmer fights the borrow checker for a while. That is normal. Push through it.

---

## CHAPTER 6 — Rust Syntax: Reading and Writing Rust for the First Time

### Installing Rust

```bash
# Install via rustup — the official Rust toolchain manager
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh

# Follow the prompts — choose "1) Proceed with standard installation"
# Restart your shell or run:
source ~/.cargo/env

# Verify
rustc --version   # rustc 1.81.0 (something similar)
cargo --version   # cargo 1.81.0

# Install VS Code extension
code --install-extension rust-lang.rust-analyzer
# rust-analyzer gives you: autocomplete, inline type hints, error detection while typing

# Install useful tools
rustup component add clippy    # Rust's linter — catches common mistakes
rustup component add rustfmt   # Auto-formatter
```

### Your first Rust program — reading every line

```bash
mkdir ~/rust-learning
cd ~/rust-learning
cargo new hello
# cargo is Rust's build tool and package manager (like pip + setuptools combined)
# 'cargo new hello' creates:
# hello/
# ├── Cargo.toml    ← package manifest (like package.json or pyproject.toml)
# └── src/
#     └── main.rs   ← source file

cd hello
```

`src/main.rs`:
```rust
// fn is how you declare a function in Rust
// main() is the entry point
fn main() {
    // println! is a macro (note the !)
    // Macros in Rust look like functions but do more complex things at compile time
    // {} is the placeholder for format arguments (like Python's {} in f-strings)
    println!("Hello from ACOS");
}
```

```bash
cargo run
# Compiles and runs:
# Compiling hello v0.1.0
# Finished dev [unoptimized + debuginfo] target(s) in 0.42s
# Running `target/debug/hello`
# Hello from ACOS

cargo build --release
# Builds optimised binary to target/release/hello
# This is what you deploy
```

### Variables and mutability — Rust defaults to immutable

```rust
fn main() {
    // Variables in Rust are IMMUTABLE by default
    // This is the opposite of Python and Go
    let note_count = 42;
    // note_count = 43;  // ERROR: cannot assign twice to immutable variable

    // Use 'mut' to make a variable mutable
    let mut tag_list = vec!["java", "concurrency"];
    tag_list.push("threads");  // This works — tag_list is mutable
    println!("Tags: {:?}", tag_list);  // {:?} is the debug format

    // Constants — known at compile time, never change
    // By convention: SCREAMING_SNAKE_CASE
    const MAX_NOTE_LENGTH: usize = 50_000;
    println!("Max note length: {}", MAX_NOTE_LENGTH);

    // Shadowing — redeclaring with let in same scope
    // Different from mutation — creates a new binding
    let score = "0.85";           // score is &str (string slice)
    let score: f64 = score.parse().unwrap();  // score is now f64
    println!("Score: {}", score);  // 0.85

    // Why immutable by default?
    // Prevents accidental modification — makes code easier to reason about
    // For ACOS: embeddings should never be modified after creation
    // The compiler enforces this if you don't use mut
}
```

### Types — Rust's type system

```rust
fn main() {
    // ── Integer types ─────────────────────────────────────────────────────
    let node_id: i64 = 42_000_000;    // Signed 64-bit: -9.2e18 to 9.2e18
    let edge_count: u32 = 500_000;    // Unsigned 32-bit: 0 to 4.3e9
    let layer: u8 = 2;                // Unsigned 8-bit: 0 to 255 (perfect for our 6 layers)
    let dim: usize = 384;             // Platform-size unsigned (use for array indexes and sizes)

    // ── Float types ───────────────────────────────────────────────────────
    let strength: f32 = 0.85_f32;    // 32-bit float — use for embeddings (saves memory)
    let score: f64 = 0.923456789;    // 64-bit float — use for scores needing precision

    // ── Boolean ───────────────────────────────────────────────────────────
    let enriched: bool = false;
    let verified = true;  // Type inferred as bool

    // ── String types — two kinds ──────────────────────────────────────────
    // &str (string slice) — a reference to string data, immutable
    let content_type: &str = "technical";  // Usually string literals

    // String — owned, growable, heap-allocated
    let mut raw_text = String::from("Java virtual threads enable");
    raw_text.push_str(" massive concurrency");  // Can modify because it's String
    raw_text.push(' ');                          // Push single char

    // Convert between them
    let as_slice: &str = &raw_text;    // &String can be used as &str (deref coercion)
    let as_owned: String = content_type.to_string();  // &str → String

    // ── Arrays and Vectors ────────────────────────────────────────────────
    // Array: fixed size, stack-allocated
    let fixed: [f32; 4] = [0.1, 0.2, 0.3, 0.4];  // Exactly 4 f32s, forever

    // Vec: dynamic size, heap-allocated (like Python list)
    let mut embedding: Vec<f32> = Vec::with_capacity(384);
    for i in 0..384 {
        embedding.push(i as f32 * 0.001);
    }
    println!("Embedding length: {}", embedding.len());

    // ── Tuples — fixed-size groups of different types ─────────────────────
    let node_info: (i64, String, f64) = (42, "place".to_string(), 0.9);
    println!("Node: id={}, type={}, score={}", node_info.0, node_info.1, node_info.2);

    // Destructure
    let (id, kind, sc) = node_info;
    println!("Destructured: {} {} {}", id, kind, sc);

    // Suppress unused warnings for this demo
    let _ = (node_id, edge_count, layer, dim, strength, score, enriched, verified, fixed, as_slice, as_owned);
}
```

### Functions and control flow

```rust
fn main() {
    // ── If expressions — note: they return values ─────────────────────────
    let confidence = 0.85_f64;

    // In Rust, if is an expression — it returns a value
    let classification = if confidence > 0.8 {
        "high"
    } else if confidence > 0.5 {
        "medium"
    } else {
        "low"
    };
    println!("Classification: {}", classification);

    // ── Loop ─────────────────────────────────────────────────────────────
    let mut attempts = 0;
    let result = loop {
        attempts += 1;
        if attempts >= 3 {
            break attempts * 10;  // loop can return a value via break
        }
    };
    println!("Loop result: {}", result);

    // ── While ────────────────────────────────────────────────────────────
    let mut count = 0;
    while count < 5 {
        count += 1;
    }

    // ── For — iterate over a range or collection ──────────────────────────
    for i in 0..5 {     // 0, 1, 2, 3, 4 (exclusive end)
        print!("{} ", i);
    }
    println!();

    for i in 0..=5 {    // 0, 1, 2, 3, 4, 5 (inclusive end)
        print!("{} ", i);
    }
    println!();

    let tags = vec!["java", "concurrency", "threads"];
    for tag in &tags {  // & borrows — we don't want to consume the Vec
        println!("Tag: {}", tag);
    }

    // ── Match — Rust's powerful pattern matching ──────────────────────────
    // More powerful than switch in Go — matches patterns, not just values
    let layer: u8 = 2;
    let layer_name = match layer {
        1 => "lexical",
        2 => "semantic",
        3 => "domain",
        4 => "logical",
        5 => "strategic",
        6 => "creative_bridge",
        _ => "unknown",  // _ is the wildcard / catch-all
    };
    println!("Layer: {}", layer_name);

    // Match with multiple patterns and guards
    let score = 0.75_f64;
    let depth = match score {
        s if s >= 0.9 => "deep",
        s if s >= 0.7 => "structural",
        s if s >= 0.5 => "surface",
        _ => "minimal",
    };
    println!("Understanding depth: {}", depth);
}

// ── Function definitions ──────────────────────────────────────────────────
// fn name(param: type, param: type) -> return_type { body }
fn add_vectors(a: &[f32], b: &[f32]) -> Vec<f32> {
    // assert_eq! panics if the condition is false — use for debugging assumptions
    assert_eq!(a.len(), b.len(), "Vectors must have same length");

    // .zip() pairs up elements, .map() transforms each pair
    // .collect() gathers the iterator results into a Vec
    a.iter().zip(b.iter()).map(|(x, y)| x + y).collect()
}

fn cosine_similarity(a: &[f32], b: &[f32]) -> f32 {
    let dot: f32 = a.iter().zip(b.iter()).map(|(x, y)| x * y).sum();
    let norm_a: f32 = a.iter().map(|x| x * x).sum::<f32>().sqrt();
    let norm_b: f32 = b.iter().map(|x| x * x).sum::<f32>().sqrt();

    // Return the last expression — no 'return' keyword needed
    // (but 'return' works too, for early returns)
    if norm_a == 0.0 || norm_b == 0.0 { 0.0 } else { dot / (norm_a * norm_b) }
}
```

### Ownership in depth — the borrow checker

```rust
fn main() {
    // ── Rule 1: One owner ─────────────────────────────────────────────────
    let s1 = String::from("note content");

    // Move: ownership transfers from s1 to s2
    let s2 = s1;

    // println!("{}", s1);  // COMPILE ERROR: s1's value was moved to s2
    println!("{}", s2);     // This works — s2 is the owner

    // For types that implement the Copy trait (integers, floats, bools),
    // assignment copies the value instead of moving ownership
    let x = 42_i64;
    let y = x;
    println!("{} {}", x, y);  // Both work — integers are Copy

    // ── Rule 2: Borrowing — temporary access without taking ownership ──────
    let note = String::from("Java virtual threads are lightweight");

    // Immutable borrow: &T
    // The original owner (note) keeps ownership
    // The borrower (slice) gets read-only access
    let word_count = count_words(&note);
    println!("'{}' has {} words", note, word_count);  // note still valid

    // ── Rule 3: Multiple immutable OR one mutable, never both ─────────────
    let mut tags = vec!["java".to_string(), "threading".to_string()];

    // Multiple immutable borrows are fine
    let first = &tags[0];
    let second = &tags[1];
    println!("Tags: {} and {}", first, second);

    // One mutable borrow
    let tag_ref = &mut tags;
    tag_ref.push("concurrency".to_string());
    println!("Updated tags: {:?}", tags);

    // This would FAIL — cannot have immutable and mutable borrow at same time:
    // let immutable = &tags;
    // let mutable = &mut tags;  // ERROR
    // println!("{} {:?}", immutable, mutable);
}

fn count_words(text: &str) -> usize {
    // Takes a string slice (&str) — borrows the data without owning it
    // When this function returns, the borrow ends — the original String is untouched
    text.split_whitespace().count()
}
```

### Structs and implementations in Rust

```rust
use std::time::{SystemTime, UNIX_EPOCH};

// Struct definition — similar to Go structs
#[derive(Debug, Clone)]  // derive macros add implementations automatically
// Debug: enables {:?} printing
// Clone: enables .clone() to make a deep copy
struct Note {
    id: i64,
    raw_text: String,
    content_type: String,
    tags: Vec<String>,
    embedding: Vec<f32>,
    enriched: bool,
    created_at: u64,  // Unix timestamp
}

// impl block: attach methods to a struct
impl Note {
    // Associated function (no self) — like a static method or constructor
    fn new(raw_text: impl Into<String>, content_type: impl Into<String>) -> Self {
        let now = SystemTime::now()
            .duration_since(UNIX_EPOCH)
            .unwrap()
            .as_secs();

        Note {
            id: 0,  // Will be set by database on insert
            raw_text: raw_text.into(),
            content_type: content_type.into(),
            tags: Vec::new(),
            embedding: vec![0.0_f32; 384],  // 384 zeros
            enriched: false,
            created_at: now,
        }
    }

    // Method taking immutable reference — does not modify self
    fn summary(&self) -> &str {
        let end = std::cmp::min(self.raw_text.len(), 50);
        &self.raw_text[..end]
    }

    fn word_count(&self) -> usize {
        self.raw_text.split_whitespace().count()
    }

    // Method taking mutable reference — can modify self
    fn add_tag(&mut self, tag: impl Into<String>) {
        self.tags.push(tag.into());
    }

    fn mark_enriched(&mut self) {
        self.enriched = true;
    }

    fn set_embedding(&mut self, embedding: Vec<f32>) {
        assert_eq!(embedding.len(), 384, "Embedding must be 384 dimensions");
        self.embedding = embedding;
    }
}

fn main() {
    let mut note = Note::new(
        "Incredible filter coffee at rooftop cafe near Marina Beach",
        "place"
    );

    note.add_tag("coffee");
    note.add_tag("view");
    note.add_tag("chennai");
    note.mark_enriched();

    println!("Summary: {}", note.summary());
    println!("Words: {}", note.word_count());
    println!("Tags: {:?}", note.tags);
    println!("Enriched: {}", note.enriched);

    // Clone makes an independent copy (because of #[derive(Clone)])
    let note_copy = note.clone();
    println!("Copy tags: {:?}", note_copy.tags);

    // Debug print (because of #[derive(Debug)])
    println!("{:?}", note);
}
```

### Enums and Pattern Matching — Rust's most powerful feature

```rust
// Rust enums can carry data — far more powerful than Python or Go enums

#[derive(Debug)]
enum NoteType {
    Place { lat: f64, lng: f64 },
    Technical { language: String, github_repo: Option<String> },
    Creative { themes: Vec<String>, mood: String },
    Reminder { remind_at: u64 },
    Media { title: String, year: u16 },
    Reflection,  // No data needed
}

// Option<T> is a built-in enum:
// Some(value) — contains a value
// None — no value
// This replaces null/None in Python — but Rust forces you to handle both cases
fn find_tag(tags: &[String], target: &str) -> Option<usize> {
    tags.iter().position(|t| t == target)
}

// Result<T, E> — either Ok(value) or Err(error)
// This is how Rust handles errors — no exceptions
#[derive(Debug)]
enum ClassificationError {
    TextTooShort,
    TextTooLong,
    ModelUnavailable(String),
}

fn classify(text: &str) -> Result<NoteType, ClassificationError> {
    if text.len() < 3 {
        return Err(ClassificationError::TextTooShort);
    }
    if text.len() > 50_000 {
        return Err(ClassificationError::TextTooLong);
    }

    // Simplified — real version calls the LLM
    if text.contains("coffee") || text.contains("restaurant") || text.contains("visited") {
        Ok(NoteType::Place { lat: 0.0, lng: 0.0 })
    } else if text.contains("java") || text.contains("python") || text.contains("code") {
        Ok(NoteType::Technical {
            language: "java".to_string(),
            github_repo: None,
        })
    } else {
        Ok(NoteType::Reflection)
    }
}

fn main() {
    let text = "Amazing filter coffee shop near Besant Nagar beach";

    // match on Result — must handle both Ok and Err
    match classify(text) {
        Ok(note_type) => {
            // match on the note type enum — must handle all variants
            match note_type {
                NoteType::Place { lat, lng } => {
                    println!("Place note detected, coords: ({}, {})", lat, lng);
                }
                NoteType::Technical { language, github_repo } => {
                    println!("Technical note in {}", language);
                    // Handle Option — must handle Some and None
                    match github_repo {
                        Some(repo) => println!("  GitHub: {}", repo),
                        None => println!("  No GitHub link"),
                    }
                }
                NoteType::Reflection => println!("Reflection note"),
                _ => println!("Other note type"),
            }
        }
        Err(e) => println!("Classification failed: {:?}", e),
    }

    // The ? operator — shorthand for "return Err if this is Err"
    // Only works in functions that return Result
    fn process(text: &str) -> Result<String, ClassificationError> {
        let note_type = classify(text)?;  // Returns Err immediately if classify fails
        Ok(format!("Processed as {:?}", note_type))
    }

    println!("{:?}", process(text));
    println!("{:?}", process(""));  // Returns Err(TextTooShort)
}
```

### Traits — Rust's abstraction mechanism

```rust
use std::fmt;

// A trait defines behaviour that types must implement
// Similar to Go interfaces but more powerful (they can have default implementations)

trait Classifiable {
    // Required method — every implementing type must provide this
    fn classify(&self) -> String;

    // Method with default implementation — can be overridden
    fn confidence(&self) -> f64 {
        0.5  // Default: medium confidence
    }

    // Default method that uses other methods
    fn summary(&self) -> String {
        format!("Type: {}, Confidence: {:.2}", self.classify(), self.confidence())
    }
}

struct RuleBasedClassifier {
    patterns: Vec<(String, String)>,  // (pattern, label) pairs
}

impl RuleBasedClassifier {
    fn new() -> Self {
        RuleBasedClassifier {
            patterns: vec![
                ("coffee".to_string(), "place".to_string()),
                ("java".to_string(), "technical".to_string()),
                ("story".to_string(), "creative".to_string()),
                ("remind".to_string(), "reminder".to_string()),
            ],
        }
    }
}

impl Classifiable for RuleBasedClassifier {
    fn classify(&self) -> String {
        "rule_based".to_string()
    }

    fn confidence(&self) -> f64 {
        0.72  // Override default
    }
}

struct LLMClassifier {
    model_name: String,
}

impl Classifiable for LLMClassifier {
    fn classify(&self) -> String {
        format!("llm:{}", self.model_name)
    }

    fn confidence(&self) -> f64 {
        0.94
    }
}

// Function that accepts any type implementing Classifiable
// &dyn Classifiable = "dynamic dispatch" — any Classifiable at runtime
fn print_classifier_info(classifier: &dyn Classifiable) {
    println!("{}", classifier.summary());
}

// impl Trait syntax — "static dispatch" — more efficient
fn run_classification(classifier: &impl Classifiable, text: &str) -> String {
    let kind = classifier.classify();
    format!("Classified '{}' as {} (confidence: {:.2})", &text[..20.min(text.len())], kind, classifier.confidence())
}

fn main() {
    let rule_clf = RuleBasedClassifier::new();
    let llm_clf = LLMClassifier { model_name: "llama3".to_string() };

    print_classifier_info(&rule_clf);
    print_classifier_info(&llm_clf);

    let text = "Amazing coffee shop near Marina Beach";
    println!("{}", run_classification(&rule_clf, text));
    println!("{}", run_classification(&llm_clf, text));
}
```

### Rust iterators — functional programming style

```rust
fn main() {
    let texts = vec![
        "Java virtual threads in JDK 21 are revolutionary",
        "Amazing filter coffee at rooftop near Marina Beach",
        "Story idea: the protagonist is the unreliable narrator",
        "Remind me to study OS scheduling tomorrow morning",
        "the",  // Too short to be useful
    ];

    // Iterator chains are lazy — no intermediate allocations
    // They compile into a single optimised loop

    let processed: Vec<(String, usize)> = texts
        .iter()
        // Filter: keep only notes with >= 5 words
        .filter(|text| text.split_whitespace().count() >= 5)
        // Map: transform to (text, word_count) tuples
        .map(|text| {
            let count = text.split_whitespace().count();
            (text.to_string(), count)
        })
        // Collect results into a Vec
        .collect();

    for (text, count) in &processed {
        println!("{} words: {}...", count, &text[..40.min(text.len())]);
    }

    // ── Common iterator methods ────────────────────────────────────────────
    let scores = vec![0.92_f64, 0.45, 0.88, 0.73, 0.61];

    // sum(), product()
    let total: f64 = scores.iter().sum();

    // max_by, min_by (for floats — need partial_cmp because NaN)
    let max = scores.iter().cloned().fold(f64::NEG_INFINITY, f64::max);

    // count()
    let above_threshold = scores.iter().filter(|&&s| s > 0.7).count();

    // any(), all()
    let all_positive = scores.iter().all(|&s| s > 0.0);
    let any_high = scores.iter().any(|&s| s > 0.9);

    // enumerate() — adds index
    for (i, score) in scores.iter().enumerate() {
        println!("Score {}: {:.2}", i, score);
    }

    // zip() — pairs two iterators
    let labels = vec!["technical", "media", "place", "creative", "reminder"];
    for (score, label) in scores.iter().zip(labels.iter()) {
        println!("{}: {:.2}", label, score);
    }

    // flat_map() — flatten nested iterators
    let tag_groups = vec![
        vec!["java", "concurrency"],
        vec!["coffee", "view"],
        vec!["story", "plot"],
    ];
    let all_tags: Vec<&str> = tag_groups.iter().flat_map(|g| g.iter().cloned()).collect();
    println!("All tags: {:?}", all_tags);

    println!("Total: {:.2}, Max: {:.2}, Above 0.7: {}, All positive: {}, Any high: {}",
        total, max, above_threshold, all_positive, any_high);
}
```

### Concurrency in Rust — threads and Arc<RwLock<T>>

```rust
use std::sync::{Arc, RwLock};
use std::thread;
use std::collections::HashMap;

// Arc = Atomically Reference Counted
// Multiple threads can hold an Arc pointing to the same data.
// When all Arcs are dropped, the data is freed.
// RwLock = Reader-Writer Lock
// Multiple threads can read simultaneously.
// Only one thread can write, and only when no readers exist.

type NodeID = i64;

#[derive(Debug, Clone)]
struct Edge {
    target_id: NodeID,
    layer: u8,
    strength: f32,
}

struct KnowledgeGraph {
    // Arc<RwLock<...>> allows shared ownership across threads with interior mutability
    adjacency: Arc<RwLock<HashMap<NodeID, Vec<Edge>>>>,
}

impl KnowledgeGraph {
    fn new() -> Self {
        KnowledgeGraph {
            adjacency: Arc::new(RwLock::new(HashMap::new())),
        }
    }

    fn add_edge(&self, source: NodeID, edge: Edge) {
        // write() acquires exclusive write lock
        // unwrap() panics on poisoned lock (thread panicked while holding it)
        let mut adj = self.adjacency.write().unwrap();
        adj.entry(source).or_default().push(edge);
    }

    fn get_neighbours(&self, node_id: NodeID) -> Vec<Edge> {
        // read() acquires shared read lock — multiple threads can do this simultaneously
        let adj = self.adjacency.read().unwrap();
        adj.get(&node_id).cloned().unwrap_or_default()
    }

    // Clone the Arc — creates a new reference to the same data, not a copy of the data
    fn clone_handle(&self) -> Arc<RwLock<HashMap<NodeID, Vec<Edge>>>> {
        Arc::clone(&self.adjacency)
    }
}

fn main() {
    let graph = Arc::new(KnowledgeGraph::new());

    // Add initial edges
    graph.add_edge(1, Edge { target_id: 2, layer: 2, strength: 0.87 });
    graph.add_edge(1, Edge { target_id: 3, layer: 1, strength: 0.62 });
    graph.add_edge(2, Edge { target_id: 4, layer: 2, strength: 0.73 });

    // Spawn multiple reader threads — they run simultaneously
    let mut handles = vec![];

    for thread_id in 0..4 {
        let graph_clone = Arc::clone(&graph);  // Clone the Arc — cheap reference copy
        let handle = thread::spawn(move || {
            let neighbours = graph_clone.get_neighbours(1);
            println!("Thread {}: found {} neighbours of node 1", thread_id, neighbours.len());
        });
        handles.push(handle);
    }

    // Spawn a writer thread
    let graph_writer = Arc::clone(&graph);
    let writer = thread::spawn(move || {
        graph_writer.add_edge(5, Edge { target_id: 6, layer: 3, strength: 0.45 });
        println!("Writer: added new edge");
    });
    handles.push(writer);

    // Wait for all threads to complete
    for handle in handles {
        handle.join().unwrap();
    }

    println!("Final neighbours of node 1: {:?}", graph.get_neighbours(1));
}
```

---

## CHAPTER 7 — Building the Rust PyO3 Extension for ACOS

### What PyO3 does

PyO3 generates the glue code between Python and Rust. You write a Rust function, annotate it with `#[pyfunction]`, and PyO3 generates a Python-callable `.so` shared library. When Python calls `acos_kg_engine.compute_jaccard_batch(...)`, it goes directly into compiled Rust — no subprocess, no socket, no serialisation overhead. Just a function call across a language boundary.

### Step-by-step setup

```bash
# Install maturin — the tool that builds PyO3 extensions
pip install maturin

# Create the extension project
cd ~/acos/src
cargo new kg-engine --lib
cd kg-engine
```

Update `Cargo.toml`:
```toml
[package]
name = "acos_kg_engine"
version = "0.1.0"
edition = "2021"

# cdylib: compile as a shared library Python can import
[lib]
name = "acos_kg_engine"
crate-type = ["cdylib"]

[dependencies]
pyo3 = { version = "0.22", features = ["extension-module"] }
rayon = "1.10"

[build-dependencies]
pyo3-build-config = "0.22"
```

`pyproject.toml` (for maturin):
```toml
[build-system]
requires = ["maturin>=1.7,<2.0"]
build-backend = "maturin"

[project]
name = "acos_kg_engine"
requires-python = ">=3.11"

[tool.maturin]
features = ["pyo3/extension-module"]
```

### Write the complete KG engine extension

`src/lib.rs`:
```rust
// This is the complete Rust source for the ACOS KG Builder extension.
// Read every line — each section is explained.

use pyo3::prelude::*;
use rayon::prelude::*;
use std::collections::HashSet;

// ── TOKENISATION ──────────────────────────────────────────────────────────

/// Remove stop words and short words, return significant token set.
/// Called from Python before passing to Jaccard computation.
fn tokenise_inner(text: &str, stop_words: &HashSet<String>) -> Vec<String> {
    let mut tokens: Vec<String> = text
        .split_whitespace()
        .map(|w| w.to_lowercase())
        // Keep only alphabetic tokens of length >= 3
        .filter(|w| w.len() >= 3 && w.chars().all(|c| c.is_alphabetic()))
        // Remove stop words
        .filter(|w| !stop_words.contains(w))
        .collect::<HashSet<String>>()  // Deduplicate via HashSet
        .into_iter()
        .collect();

    tokens.sort();  // Sort for reproducibility
    tokens
}

/// Python-callable tokenisation function.
///
/// Args:
///     text: The note text to tokenise
///     stop_words: List of words to exclude
///
/// Returns:
///     List of significant, deduplicated, sorted tokens
#[pyfunction]
fn tokenise_text(text: &str, stop_words: Vec<String>) -> PyResult<Vec<String>> {
    let stop_set: HashSet<String> = stop_words.into_iter().collect();
    Ok(tokenise_inner(text, &stop_set))
}

// ── JACCARD SIMILARITY ────────────────────────────────────────────────────

fn jaccard_similarity(set_a: &HashSet<&str>, set_b: &HashSet<&str>) -> f32 {
    if set_a.is_empty() || set_b.is_empty() {
        return 0.0;
    }
    let intersection = set_a.intersection(set_b).count() as f32;
    let union_count = set_a.union(set_b).count() as f32;
    intersection / union_count
}

/// Compute Jaccard similarity from one note against ALL existing notes.
/// Uses Rayon to run across all CPU cores in parallel.
///
/// Args:
///     new_tokens: Tokens from the new note being processed
///     all_note_tokens: List of (node_id, tokens) for every existing note
///     threshold: Minimum similarity to include in results (e.g., 0.3)
///
/// Returns:
///     List of (node_id, jaccard_score) for all matches above threshold,
///     sorted by score descending.
#[pyfunction]
fn compute_jaccard_batch(
    new_tokens: Vec<String>,
    all_note_tokens: Vec<(i64, Vec<String>)>,
    threshold: f32,
) -> PyResult<Vec<(i64, f32)>> {
    // Convert new tokens to HashSet<&str> for O(1) intersection/union
    // We use &str (references) to avoid allocating new Strings
    let new_set: HashSet<&str> = new_tokens.iter().map(|s| s.as_str()).collect();

    // par_iter() from Rayon — distributes work across all CPU cores
    let mut results: Vec<(i64, f32)> = all_note_tokens
        .par_iter()
        .filter_map(|(node_id, tokens)| {
            // Skip notes with too few tokens (no meaningful comparison possible)
            if tokens.len() < 3 {
                return None;
            }

            let existing_set: HashSet<&str> = tokens.iter().map(|s| s.as_str()).collect();
            let similarity = jaccard_similarity(&new_set, &existing_set);

            if similarity >= threshold {
                Some((*node_id, similarity))
            } else {
                None  // filter_map: None means skip this entry
            }
        })
        .collect();

    // Sort by score descending — highest similarity first
    results.sort_unstable_by(|a, b| b.1.partial_cmp(&a.1).unwrap_or(std::cmp::Ordering::Equal));

    Ok(results)
}

// ── COSINE SIMILARITY ────────────────────────────────────────────────────

/// Compute cosine similarity between two embedding vectors.
///
/// Args:
///     a: First embedding as list of f32
///     b: Second embedding as list of f32
///
/// Returns:
///     Cosine similarity score between 0.0 and 1.0
#[pyfunction]
fn cosine_similarity_pair(a: Vec<f32>, b: Vec<f32>) -> PyResult<f32> {
    if a.len() != b.len() {
        return Err(pyo3::exceptions::PyValueError::new_err(
            format!("Embedding dimensions must match: {} != {}", a.len(), b.len())
        ));
    }

    let dot: f32 = a.iter().zip(b.iter()).map(|(x, y)| x * y).sum();
    let norm_a: f32 = a.iter().map(|x| x * x).sum::<f32>().sqrt();
    let norm_b: f32 = b.iter().map(|x| x * x).sum::<f32>().sqrt();

    if norm_a == 0.0 || norm_b == 0.0 {
        return Ok(0.0);
    }

    Ok(dot / (norm_a * norm_b))
}

/// Find top-k most similar nodes by cosine similarity.
/// Runs across all CPU cores with Rayon.
///
/// Args:
///     query_embedding: The query vector (list of f32)
///     corpus: List of (node_id, embedding) pairs
///     k: Maximum number of results to return
///     threshold: Minimum similarity to include
///
/// Returns:
///     List of (node_id, similarity) sorted by similarity descending
#[pyfunction]
fn top_k_similar(
    query_embedding: Vec<f32>,
    corpus: Vec<(i64, Vec<f32>)>,
    k: usize,
    threshold: f32,
) -> PyResult<Vec<(i64, f32)>> {
    let mut scores: Vec<(i64, f32)> = corpus
        .par_iter()
        .filter_map(|(node_id, embedding)| {
            if embedding.len() != query_embedding.len() {
                return None;
            }
            let dot: f32 = query_embedding.iter().zip(embedding.iter())
                .map(|(x, y)| x * y).sum();
            let norm_q: f32 = query_embedding.iter().map(|x| x * x).sum::<f32>().sqrt();
            let norm_e: f32 = embedding.iter().map(|x| x * x).sum::<f32>().sqrt();

            if norm_q == 0.0 || norm_e == 0.0 {
                return None;
            }
            let sim = dot / (norm_q * norm_e);
            if sim >= threshold { Some((*node_id, sim)) } else { None }
        })
        .collect();

    scores.sort_unstable_by(|a, b| b.1.partial_cmp(&a.1).unwrap_or(std::cmp::Ordering::Equal));
    scores.truncate(k);
    Ok(scores)
}

// ── MODULE REGISTRATION ────────────────────────────────────────────────────

/// This function registers all Python-callable functions in the module.
/// The module name (acos_kg_engine) must match the Cargo.toml [lib] name.
#[pymodule]
fn acos_kg_engine(m: &Bound<'_, PyModule>) -> PyResult<()> {
    m.add_function(wrap_pyfunction!(tokenise_text, m)?)?;
    m.add_function(wrap_pyfunction!(compute_jaccard_batch, m)?)?;
    m.add_function(wrap_pyfunction!(cosine_similarity_pair, m)?)?;
    m.add_function(wrap_pyfunction!(top_k_similar, m)?)?;
    Ok(())
}
```

### Rust unit tests

```rust
// Add at the bottom of src/lib.rs
#[cfg(test)]  // This module only compiles when running tests
mod tests {
    use super::*;  // Import everything from parent module

    // Helper: create a HashSet from a vec of string slices
    fn make_set<'a>(words: &[&'a str]) -> HashSet<&'a str> {
        words.iter().cloned().collect()
    }

    #[test]
    fn test_jaccard_identical_sets() {
        let a = make_set(&["java", "thread", "concurrency"]);
        let b = make_set(&["java", "thread", "concurrency"]);
        let sim = jaccard_similarity(&a, &b);
        assert!((sim - 1.0).abs() < 1e-6, "Identical sets should have similarity 1.0");
    }

    #[test]
    fn test_jaccard_disjoint_sets() {
        let a = make_set(&["java", "thread"]);
        let b = make_set(&["coffee", "beach"]);
        let sim = jaccard_similarity(&a, &b);
        assert_eq!(sim, 0.0, "Disjoint sets should have similarity 0.0");
    }

    #[test]
    fn test_jaccard_partial_overlap() {
        let a = make_set(&["java", "thread", "concurrency"]);  // 3 elements
        let b = make_set(&["java", "thread", "scheduling"]);    // 3 elements
        // Intersection: {java, thread} = 2
        // Union: {java, thread, concurrency, scheduling} = 4
        // Jaccard = 2/4 = 0.5
        let sim = jaccard_similarity(&a, &b);
        assert!((sim - 0.5).abs() < 1e-6, "Expected 0.5, got {}", sim);
    }

    #[test]
    fn test_cosine_similarity_identical() {
        let v = vec![0.1_f32, 0.2, 0.3, 0.4];
        let sim = cosine_similarity_pair(v.clone(), v).unwrap();
        assert!((sim - 1.0).abs() < 1e-5, "Identical vectors: similarity should be ~1.0");
    }

    #[test]
    fn test_cosine_similarity_orthogonal() {
        let a = vec![1.0_f32, 0.0, 0.0];
        let b = vec![0.0_f32, 1.0, 0.0];
        let sim = cosine_similarity_pair(a, b).unwrap();
        assert!(sim.abs() < 1e-5, "Orthogonal vectors: similarity should be ~0.0");
    }

    #[test]
    fn test_tokenise_removes_stop_words() {
        let stops = vec!["the".to_string(), "is".to_string(), "a".to_string()];
        let stops_set: HashSet<String> = stops.into_iter().collect();
        let result = tokenise_inner("the operating system is a scheduler", &stops_set);
        assert!(result.contains(&"operating".to_string()));
        assert!(result.contains(&"system".to_string()));
        assert!(result.contains(&"scheduler".to_string()));
        assert!(!result.contains(&"the".to_string()));
        assert!(!result.contains(&"is".to_string()));
    }

    #[test]
    fn test_tokenise_deduplicates() {
        let stops_set: HashSet<String> = HashSet::new();
        let result = tokenise_inner("java java java threads", &stops_set);
        let java_count = result.iter().filter(|w| w.as_str() == "java").count();
        assert_eq!(java_count, 1, "Tokens should be deduplicated");
    }
}
```

Run tests:
```bash
cargo test
# Output:
# running 7 tests
# test tests::test_cosine_similarity_identical ... ok
# test tests::test_cosine_similarity_orthogonal ... ok
# test tests::test_jaccard_disjoint_sets ... ok
# test tests::test_jaccard_identical_sets ... ok
# test tests::test_jaccard_partial_overlap ... ok
# test tests::test_tokenise_deduplicates ... ok
# test tests::test_tokenise_removes_stop_words ... ok
# test result: ok. 7 passed; 0 failed

cargo clippy  # Linter — checks for common mistakes
cargo fmt     # Auto-formats your code
```

### Build and install the extension into Python

```bash
cd ~/acos/src/kg-engine

# Development build — installs into current Python venv
# Run this after every change during development
maturin develop

# Verify it installed
cd ~/acos/src/api
source .venv/bin/activate
python3 -c "import acos_kg_engine; print(dir(acos_kg_engine))"
# Output: [..., 'compute_jaccard_batch', 'cosine_similarity_pair', 'tokenise_text', 'top_k_similar']

# Production build — creates a .whl file
maturin build --release
# Creates: target/wheels/acos_kg_engine-0.1.0-cp311-cp311-manylinux_2_*.whl
# This .whl installs like any Python package: pip install the_wheel.whl
```

### Use it from Python

```python
# In ~/acos/src/api/acos/intelligence/kg_builder.py

import acos_kg_engine  # Import the Rust extension — same as any Python import

STOP_WORDS = [
    "the", "a", "an", "is", "are", "was", "were", "be", "been", "being",
    "have", "has", "had", "do", "does", "did", "will", "would", "could",
    "should", "may", "might", "to", "of", "in", "on", "at", "for", "from",
    "by", "with", "about", "into", "and", "or", "but", "not", "this", "that",
    "it", "its", "as", "so", "if", "then", "than", "very", "just", "also",
]

class KGBuilder:
    def tokenise(self, text: str) -> list[str]:
        # Calls Rust — ~50x faster than Python equivalent
        return acos_kg_engine.tokenise_text(text, STOP_WORDS)

    async def compute_layer1_connections(
        self,
        node_id: int,
        new_text: str,
        all_notes: list[tuple[int, str]]
    ) -> list[dict]:
        """Compute lexical connections from new note to all existing notes."""

        # Tokenise the new note
        new_tokens = self.tokenise(new_text)
        if len(new_tokens) < 3:
            return []

        # Tokenise all existing notes
        all_token_sets = [
            (node_id, self.tokenise(text))
            for node_id, text in all_notes
        ]

        # This single call runs across ALL CPU cores via Rayon
        # Python waits here, but all CPU cores are working simultaneously
        matches = acos_kg_engine.compute_jaccard_batch(
            new_tokens,       # list[str]
            all_token_sets,   # list[tuple[int, list[str]]]
            0.3               # threshold
        )

        return [
            {
                "source_node_id": node_id,
                "target_node_id": match_id,
                "layer": 1,
                "connection_type": "LEXICAL",
                "strength": score,
                "created_by": "system_auto",
                "evidence": {"jaccard_score": score}
            }
            for match_id, score in matches
        ]
```

---

# PART THREE — INTEGRATED ROADMAP
## Day-by-Day: When to Learn What, When to Build What

---

> **This section merges the Go and Rust learning tracks into the main ACOS 300-day roadmap. Every row tells you: the day, what you are building in ACOS, what Go or Rust concept you need, how long to spend on it, and the exact deliverable. This is your daily action plan.**

---

## INTEGRATED LEARNING SCHEDULE

### Reading the table

**Main track:** Your Python/FastAPI/PostgreSQL/etc. work from the main roadmap.
**Language side track:** Go or Rust learning session (1 hour per day during the relevant phase).
**Integration day:** A full day where the new language component is wired into ACOS.

The side track runs in parallel — it does not replace any main track day. You spend the evening session (normally used for documentation) on language learning during the integration weeks.

---

## PHASE 0 + PHASE 1 — DAYS 1–45: NO Go OR Rust Yet

**Reason:** You are learning fundamentals. Adding Go or Rust now creates cognitive overload. Python is sufficient for everything in Phases 0–1. The Go and Rust sessions begin exactly when you need them for the first integration.

**What to do instead of language learning in evenings:**
Evenings in Phase 0 and 1 are pure documentation and recall. Write your learning journal. Answer conceptual test questions. Make your GitHub commits. Build the habit of consistent daily work — this habit is more valuable than knowing Go syntax.

**Exception:** If you have spare time on weekends, read the first 4 chapters of "The Go Programming Language" book (free at gopl.io) and Chapters 1–4 of The Rust Book (doc.rust-lang.org/book). Passive reading only — no coding yet.

---

## PHASE 2 — DAYS 46–70: Rust Side Track Begins

### The schedule

| Day | Main Track | Rust Side Track (30–45 min evening) | Deliverable |
|-----|-----------|--------------------------------------|-------------|
| 46–50 | SQL fundamentals | Read Rust Book Ch 1–3: Hello World, variables, types, functions | Nothing yet — just reading |
| 51–54 | pgvector setup | Read Rust Book Ch 4: Ownership. Do all three exercises from Chapter 6 of this document | Ownership exercises completed |
| **55** | Redis intro | **Setup PyO3 environment + write tokenise_text function** | `acos_kg_engine.tokenise_text()` callable from Python |
| 56–59 | Redis adaptive feed | Read Rust Book Ch 5–6: Structs and Enums + Pattern Matching | Structs and enums exercises |
| **60** | SQLAlchemy ORM begins | **Write cosine_similarity_pair + tests + cargo test passes** | `acos_kg_engine.cosine_similarity_pair()` tested |
| 61–62 | Repositories | Read Rust Book Ch 9: Error Handling. Rewrite all `.unwrap()` to proper `?` | Error handling in all existing Rust code |
| **63** | **KG Builder — main + integration** | **Write compute_jaccard_batch with Rayon. Benchmark vs Python** | KG Builder Layer 1 runs in Rust |
| 64–66 | KG Builder finalisation | Read Rust Book Ch 10: Traits and Generics | Traits exercises |
| **67** | Pattern Engine foundation | **Write top_k_similar — semantic similarity in Rust** | All four PyO3 functions complete and tested |
| 68–70 | Phase 2 completion | Run `cargo clippy`, fix all warnings. Write ADR-002 | Rust extension polished and documented |

### Day 55 in full detail

**Morning (2 hours) — Main Track: Redis data structures**
Follow Day 55 from the main roadmap (Redis sorted sets for adaptive feed).

**Afternoon (3 hours) — Main Track: Build the Redis feed engine in Python**
Write `acos/storage/redis_client.py` with sorted set operations.

**Evening (45 min) — Rust Side Track:**

Step 1: Navigate to the kg-engine directory:
```bash
cd ~/acos/src/kg-engine
```

Step 2: Open `src/lib.rs`. You currently have the scaffolded PyO3 hello-world from maturin. Replace it entirely with the `tokenise_text` function from Chapter 7 of this document.

Step 3: Build and test:
```bash
maturin develop  # Compile Rust, install into Python venv
cd ~/acos/src/api
source .venv/bin/activate
python3 << 'EOF'
import acos_kg_engine

stops = ["the","a","is","in","on","at","of","to","for","and","or","but","this","that"]
text = "The operating system scheduler decides which process runs next on the CPU"
result = acos_kg_engine.tokenise_text(text, stops)
print("Tokens:", result)
# Expected: ['cpu', 'decides', 'next', 'operating', 'process', 'runs', 'scheduler', 'system', 'which']
EOF
```

Step 4: Write a journal entry answering: What does `iter().map().filter().collect()` do? Why is `HashSet<&str>` used instead of `HashSet<String>`? (Hint: String is owned, &str is borrowed — no allocation in the inner loop)

### Day 63 in full detail

**This is the first day a language other than Python does real work in ACOS.**

**Morning (2 hours) — Learning Track:**
Review Rayon's documentation (https://docs.rs/rayon) specifically:
- `par_iter()` — parallel iterator
- `filter_map()` — filter + transform in one step
- Why `par_iter()` is safe: Rust's type system guarantees no data races

Run this experiment to feel the difference:
```rust
// File: src/kg-engine/examples/benchmark_jaccard.rs
use rayon::prelude::*;
use std::collections::HashSet;
use std::time::Instant;

fn main() {
    // Generate 10,000 fake notes, each with 20 tokens
    let corpus: Vec<Vec<String>> = (0..10_000)
        .map(|i| {
            (0..20).map(|j| format!("word{}_{}", i % 100, j)).collect()
        })
        .collect();

    let new_tokens: Vec<String> = (0..20).map(|j| format!("word5_{}", j)).collect();
    let new_set: HashSet<&str> = new_tokens.iter().map(|s| s.as_str()).collect();

    // Sequential
    let start = Instant::now();
    let seq_results: Vec<usize> = corpus.iter().enumerate()
        .filter(|(_, tokens)| {
            let s: HashSet<&str> = tokens.iter().map(|s| s.as_str()).collect();
            let inter = new_set.intersection(&s).count();
            let uni = new_set.union(&s).count();
            (inter as f32 / uni as f32) >= 0.3
        })
        .map(|(i, _)| i)
        .collect();
    let seq_time = start.elapsed();

    // Parallel with Rayon
    let start = Instant::now();
    let par_results: Vec<usize> = corpus.par_iter().enumerate()
        .filter(|(_, tokens)| {
            let s: HashSet<&str> = tokens.iter().map(|s| s.as_str()).collect();
            let inter = new_set.intersection(&s).count();
            let uni = new_set.union(&s).count();
            (inter as f32 / uni as f32) >= 0.3
        })
        .map(|(i, _)| i)
        .collect();
    let par_time = start.elapsed();

    println!("Sequential: {:?} ({} matches)", seq_time, seq_results.len());
    println!("Parallel:   {:?} ({} matches)", par_time, par_results.len());
    println!("Speedup: {:.1}x", seq_time.as_secs_f64() / par_time.as_secs_f64());
}
```

Run: `cargo run --example benchmark_jaccard --release`

**Afternoon (3 hours) — Building Track:**
Write the complete `compute_jaccard_batch` function (from Chapter 7) with all tests. `maturin develop`. Run from Python and verify correctness on 5 hand-crafted test cases.

Then update `KGBuilder._compute_layer1_lexical()` to call the Rust function instead of the Python loop. Run the integration test from Day 65 and verify the results are identical between Python and Rust implementations.

**Evening (45 min):**
Write benchmark: time Python implementation vs Rust on 100, 1000, 5000, 10000 notes. Record results in `docs/performance/kg-builder-rust-benchmark.md`. This document is your ADR evidence.

---

## PHASE 3 — DAYS 71–100: Go Side Track Begins

### The schedule

| Day | Main Track | Go Side Track (30–45 min evening) | Deliverable |
|-----|-----------|-----------------------------------|-------------|
| 71–75 | FastAPI gateway | Read Go Tour sections 1–8 (https://go.dev/tour) | Understand basic Go syntax |
| 76–80 | Notes API | Read Go Tour sections on concurrency (sections 9–11) | Goroutines and channels understood |
| 81–85 | External APIs | Write the hello-world Go HTTP server. Read about `net/http` | Simple Go HTTP server running |
| 86–90 | YouTube + scraping | Write Go fan-out pattern from Chapter 2 (all 5 sources, parallel, channels) | Fan-out search demo working |
| 91–95 | Auth + rate limiting | Read about `context.Context` — cancellation and timeouts | Context pattern understood |
| 96–100 | API completion | Write Go tests for the fan-out demo | 5 tests passing |

### Day 86 — The fan-out pattern in detail

By Day 86 you have seen goroutines and channels in the Go tutorial. Today you write the pattern that the Advisor Orchestrator is built on.

**Evening session (45 min):**

Create a standalone Go program that demonstrates true parallel search:
```bash
mkdir ~/acos/go-experiments
cd ~/acos/go-experiments
go mod init experiments
touch fanout_demo.go
```

Write `fanout_demo.go` using the `AdvisorOrchestrator` pattern from Chapter 2. Add a `time.Sleep` simulation in each source, run with `go run fanout_demo.go`, verify that 5 sources running at 50ms, 80ms, 20ms, 120ms, 60ms complete in ~120ms total (not 330ms sequential).

This is the moment Go's value becomes visceral. Record the timing in your journal.

---

## PHASE 4 — DAYS 101–140: Go Integration — Reminder Engine and Advisor

### The schedule

| Day | Main Track | Go Work | Deliverable |
|-----|-----------|---------|-------------|
| 101–103 | Celery task queue setup | Read: Go structs, methods, interfaces (Chapter 2 of this doc) | Interfaces exercise complete |
| **104** | **Reminder Engine** | **Write complete Go reminder service** | Go reminder binary running in Docker |
| 105–109 | Core Celery tasks | Read: Go error handling + testing. Write 5 reminder tests | Tests passing |
| **110** | **Advisor Orchestrator** | **Write Go advisor with SearchSource interface** | 3 search sources running in parallel |
| 111–115 | Event bus + WebSocket | Write Reddit, YouTube, KB search sources in Go | All 3 sources implemented + tested |
| 116–120 | Intent classifier LLM | Read Go http.Client + JSON parsing | HTTP client exercise |
| 121–125 | Advisor workflows | Wire Go advisor into ACOS: FastAPI queues advisor task → Go worker executes | End-to-end advisor task working |
| 126–130 | Search strategy memory | Write Go tests for all advisor sources | Full test coverage |
| 131–140 | Pattern Engine | Review all Go code. Write ADR-003 and ADR-004 | Documentation complete |

### Day 104 in full detail

**This is the day the Go reminder service goes live.**

**Morning (2 hours) — Learning Track:**
Study: Go interfaces and the `context.Context` cancellation pattern. Write three exercises:
1. Define a `Notifier` interface with `Send(ctx, message string) error`
2. Implement `NtfyNotifier` that sends to ntfy.sh
3. Implement `LogNotifier` that just prints (for testing)
4. Write a function that takes a `Notifier` and sends a test notification

**Afternoon (3 hours) — Building Track:**
Build the complete reminder service using the reference architecture from the Go Integration Roadmap document. Steps:

```bash
mkdir -p ~/acos/src/workers/reminders/{cmd/reminder,internal/{reminder,storage,delivery}}
cd ~/acos/src/workers/reminders
go mod init github.com/yourusername/acos/reminders
go get github.com/jackc/pgx/v5
go get github.com/redis/go-redis/v9
```

Write in this order:
1. `internal/reminder/reminder.go` — the `Reminder` struct and `IsOverdue()` method
2. `internal/delivery/ntfy.go` — the ntfy.sh sender
3. `internal/storage/postgres.go` — load pending reminders from PostgreSQL
4. `internal/storage/redis.go` — read from Redis sorted set
5. `cmd/reminder/main.go` — wire everything together
6. `Dockerfile` — multi-stage build

Add to `docker-compose.yml` and run: `make up`. Create a test reminder via your Python API for 2 minutes from now. Watch the Go service log when it fires.

**Evening (30 min):**
Write `docs/decisions/ADR-003-go-reminder-engine.md`. Include: the timing precision problem with Celery, the measurement showing Go's ±10ms vs Celery's ±30s, the goroutine-per-reminder design, and the context cancellation pattern for clean shutdown.

### Day 110 in full detail

**This is the day the advisor becomes truly parallel.**

**Morning (2 hours) — Learning Track:**
Review interfaces from yesterday. Specifically study: how `[]SearchSource` (a slice of interface values) allows storing different concrete types. How `for _, src := range sources { go func(src SearchSource) {...}(src) }` starts one goroutine per source. Why you must capture `src` in the goroutine (the loop variable changes — capture by parameter).

Common mistake to understand and avoid:
```go
// WRONG — all goroutines capture the same 'src' variable
// By the time they run, 'src' may be the last element
for _, src := range sources {
    go func() {
        src.Search(ctx, query)  // Bug: src may have changed
    }()
}

// CORRECT — pass src as a parameter to the goroutine
for _, src := range sources {
    src := src  // Redeclare to create a new variable scoped to this iteration
    go func() {
        src.Search(ctx, query)  // Correct: this goroutine owns its own 'src'
    }()
}

// Also correct — pass as function argument
for _, src := range sources {
    go func(s SearchSource) {
        s.Search(ctx, query)  // Correct: s is a parameter
    }(src)
}
```

**Afternoon (3 hours) — Building Track:**
Build the advisor orchestrator:

```bash
mkdir -p ~/acos/src/workers/advisor/{cmd/advisor,internal/{orchestrator,sources,synthesis}}
cd ~/acos/src/workers/advisor
go mod init github.com/yourusername/acos/advisor
```

Implement in this order:
1. `internal/orchestrator/orchestrator.go` — the `SearchSource` interface and `AdvisorOrchestrator`
2. `internal/sources/reddit.go` — Reddit JSON API scraper
3. `internal/sources/youtube.go` — YouTube Data API v3 client
4. `internal/sources/knowledge_base.go` — calls your ACOS `/api/v1/notes/search`
5. `internal/synthesis/synthesis.go` — formats all results and calls Ollama for synthesis
6. `cmd/advisor/main.go` — HTTP server exposing `POST /execute-task`

Wire into Python: when FastAPI receives `POST /api/v1/advisor/task`, it puts the task in a Redis queue. The Go advisor worker polls the queue, executes, writes result back to Redis. FastAPI polls for the result.

---

## PHASE 5 — DAYS 141–175: Rust Deepens — Embedding Engine and Graph Engine

### The schedule

| Day | Main Track | Rust Work | Deliverable |
|-----|-----------|-----------|-------------|
| 141–144 | Embedding system design | Study: Rust traits. Write the `EmbeddingModel` trait | Trait definition complete |
| **145** | **Embedding Engine** | **Set up ONNX model + PyO3 interface. Benchmark** | Rust embedding faster than Python |
| 146–150 | Search quality tuning | Read: Rust's ndarray crate for matrix ops. Write batch_cosine_similarity | Batch similarity function working |
| 151–154 | Hybrid search | Add batch cosine to PyO3 module. Update semantic search to use Rust | Semantic search uses Rust |
| **155** | **In-memory Graph Engine** | **Write Rust Axum server with KnowledgeGraph struct** | Graph traversal <1ms |
| 156–165 | LLM prompting | Write Rust BFS traversal tests. Add graph engine to Docker Compose | Graph engine in production stack |
| 166–175 | KG Layers 3–6 | Add edge update endpoint to graph engine. Wire to KG Builder | Graph engine updates on new edges |

### Day 145 in full detail

**Morning (2 hours) — Learning Track:**
Study: Rust traits with default implementations. The `EmbeddingModel` trait has `embed_single` (required) and `embed_batch` (default implemented using `embed_single`). Types can override the default batch implementation with an optimised version.

Study: ONNX Runtime — what it is (a portable ML inference engine that runs models in `.onnx` format, the standard format for ML models across PyTorch, TensorFlow, etc.). Why it matters: your Python sentence-transformers model can be exported to ONNX format and then run in Rust without Python overhead.

**Afternoon (3 hours) — Building Track:**

```bash
cd ~/acos/src/kg-engine
# Add to Cargo.toml:
# ort = { version = "2", features = ["download-binaries"] }
# tokenizers = "0.19"
```

Export the model from Python:
```bash
cd ~/acos/src/api
source .venv/bin/activate
pip install optimum[onnxruntime]

python3 << 'EOF'
from optimum.exporters.onnx import main_export
import os
os.makedirs("../../models", exist_ok=True)
main_export(
    "sentence-transformers/all-MiniLM-L6-v2",
    output="../../models/all-MiniLM-L6-v2-onnx",
    task="feature-extraction"
)
print("Model exported to ../../models/all-MiniLM-L6-v2-onnx")
EOF
```

Write `src/embeddings.rs`:
```rust
// Reference structure — implement the body yourself
use ort::{Session, inputs};
use tokenizers::Tokenizer;

pub struct OnnxEmbedder {
    session: Session,
    tokenizer: Tokenizer,
}

impl OnnxEmbedder {
    pub fn new(model_path: &str) -> Result<Self, Box<dyn std::error::Error>> {
        let session = Session::builder()?.commit_from_file(model_path)?;
        let tokenizer = Tokenizer::from_pretrained("sentence-transformers/all-MiniLM-L6-v2", None)?;
        Ok(OnnxEmbedder { session, tokenizer })
    }

    pub fn embed(&self, text: &str) -> Result<Vec<f32>, Box<dyn std::error::Error>> {
        // 1. Tokenise: text → input_ids, attention_mask, token_type_ids
        // 2. Run ONNX inference: inputs → last_hidden_state
        // 3. Mean pool: average over token dimension
        // 4. L2 normalise: divide by magnitude
        // 5. Return as Vec<f32>
        todo!("implement ONNX inference")
    }
}
```

**This is intentionally left as `todo!()`.** The learning is in the implementation — use the ort crate documentation (https://docs.rs/ort) to fill in the body. This mirrors real engineering: you have the architecture, you implement it using official documentation.

**Evening (45 min):**
Benchmark: embed 32 texts 100 times each. Python sentence-transformers vs Rust ONNX. Record in `docs/performance/embedding-rust-benchmark.md`.

### Day 155 in full detail

**This day transforms the knowledge graph from a PostgreSQL query to a sub-millisecond in-memory operation.**

**Morning (2 hours) — Learning Track:**
Study: `Arc<RwLock<T>>` from Chapter 6. Write the three exercises:
1. Create a `SharedCounter` struct with `Arc<RwLock<i64>>`, spawn 10 threads that each increment it 1000 times, verify the final count is 10,000.
2. Create a `SharedMap` with `Arc<RwLock<HashMap<String, Vec<String>>>>`, spawn 5 reader threads and 1 writer thread, verify no data races.
3. Add a `try_read()` with timeout — if the write lock is held for more than 100ms, log a warning and return an empty vec rather than blocking.

Study: Axum web framework (https://docs.rs/axum) — specifically how to share state across request handlers using `State<T>`.

**Afternoon (3 hours) — Building Track:**
```bash
mkdir -p ~/acos/src/graph-engine/src
cd ~/acos/src/graph-engine
cargo new . --name acos_graph_engine
# Add to Cargo.toml: axum, tokio (full), serde, serde_json, pgx (for PostgreSQL loading)
```

Write the graph engine in this order:
1. `src/graph.rs` — `KnowledgeGraph` struct with `Arc<RwLock<HashMap<i64, Vec<Edge>>>>`
2. `src/traversal.rs` — BFS traversal returning `Vec<(i64, f32, u8)>`
3. `src/routes.rs` — Axum handlers for `/traverse/:id`, `/neighbours/:id`, `/health`
4. `src/loader.rs` — load all edges from PostgreSQL on startup
5. `src/main.rs` — wire everything with `axum::serve`

Add to `docker-compose.yml`:
```yaml
  graph-engine:
    build: src/graph-engine
    environment:
      DATABASE_URL: postgresql://acos_user:${POSTGRES_PASSWORD}@postgres:5432/acos
    ports:
      - "9000:9000"
    depends_on:
      postgres: {condition: service_healthy}
```

Update `acos/intelligence/kg_queries.py` to call `http://graph-engine:9000/traverse/{node_id}` instead of the recursive CTE. Benchmark: `time curl http://localhost:9000/traverse/1` vs timing the PostgreSQL CTE query. Record both in `docs/performance/graph-engine-benchmark.md`.

---

## PHASE 6 — DAYS 191–210: Rust UniFFI for Mobile Sync

### The schedule

| Day | Main Track | Rust Work | Deliverable |
|-----|-----------|-----------|-------------|
| 191–197 | Expo + React Native | Set up Rust cross-compilation targets | Rust compiles for Android |
| **198** | **Mobile sync engine** | **Write UniFFI sync engine + build for Android** | Kotlin can call resolve_conflict() |
| 199–205 | Mobile features | Write UniFFI tests + integrate into React Native | Sync engine in use on phone |
| 206–210 | Mobile polish | Add WASM build target for PWA | Rust runs in all three platforms |

### Day 198 in full detail

**Morning (2 hours) — Learning Track:**
Study: What is FFI (Foreign Function Interface) — how compiled libraries expose functions to other languages. Study UniFFI specifically: https://mozilla.github.io/uniffi-rs/. Understand: the UDL file (interface definition language), how `#[uniffi::export]` generates bindings, how the generated Kotlin code looks.

**Afternoon (3 hours) — Building Track:**
```bash
cd ~/acos/src
cargo new sync-engine --lib
cd sync-engine

# Install Android NDK (download via Android Studio SDK Manager or standalone)
# Set ANDROID_NDK_HOME environment variable

# Add cross-compilation targets
rustup target add aarch64-linux-android
rustup target add armv7-linux-androideabi

# Install cargo-ndk
cargo install cargo-ndk
```

Write the sync engine from the reference code in Chapter 7. Focus on:
1. `resolve_conflict()` function with clear documented behaviour
2. `sort_sync_queue()` function prioritising reminders
3. Comprehensive tests for edge cases (simultaneous modification, clock drift)

Build for Android:
```bash
cargo ndk -t arm64-v8a -o ../mobile/android/app/src/main/jniLibs build --release
uniffi-bindgen generate src/lib.rs --language kotlin --out-dir ../mobile/android/app/src/main/kotlin/com/acos/sync/
```

Test in Android project:
```kotlin
// In your React Native Android bridge
import com.acos.sync.*

val local = OfflineNote(localId = "abc", rawText = "My note", modifiedAt = 1234567890000L, contentType = "technical")
val server = OfflineNote(localId = "abc", rawText = "My note updated", modifiedAt = 1234567895000L, contentType = "technical")
val resolution = resolveConflict(local, server)
// resolution.winner.rawText == "My note updated" (server is newer)
```

---

## PHASE 7 — DAYS 211–245: Go DevOps Tools

### The schedule

| Day | Main Track | Go Work | Deliverable |
|-----|-----------|---------|-------------|
| 211–217 | Docker Compose production | Read about Prometheus Go SDK | SDK understood |
| **218** | **Prometheus exporter** | **Write complete Go exporter with ACOS metrics** | Custom metrics in Grafana |
| 219–225 | NGINX + SSL | Write Grafana dashboard for ACOS metrics | Dashboard committed |
| 226–235 | GitHub Actions CI | Add Rust and Go build steps to CI | CI builds all three languages |
| 236–245 | Monitoring + alerting | Add Go exporter alerts | Alerts fire in Grafana |

### Day 218 in full detail

**Morning (2 hours) — Learning Track:**
Read the Prometheus Go client documentation: https://pkg.go.dev/github.com/prometheus/client_golang/prometheus. Understand: `Counter`, `Gauge`, `Histogram`, `GaugeVec` (labelled). Write a small program that exposes 3 metrics on port 9100 and verify Prometheus can scrape them.

**Afternoon (3 hours) — Building Track:**
Write the complete ACOS exporter from the reference in the Go/Rust Integration Roadmap. The exporter queries PostgreSQL every 30 seconds for: node counts by content_type, edge counts by layer, notes created today, weekly fingerprint drift (compare last two `fingerprint_snapshots` vectors using cosine distance).

Add to `prometheus.yml`:
```yaml
scrape_configs:
  - job_name: 'acos-custom'
    static_configs:
      - targets: ['acos-exporter:9100']
    scrape_interval: 30s
```

Build and verify in Grafana: create a dashboard panel showing "Knowledge Graph Growth" — nodes and edges over time. Export the dashboard JSON to `docs/monitoring/dashboards/acos-intelligence.json`.

---

## PHASE 8 — DAYS 266–272: Go k6 Load Testing

### Day 267 in full detail

**Morning (2 hours) — Learning Track:**
Install k6:
```bash
sudo gpg -k
sudo gpg --no-default-keyring --keyring /usr/share/keyrings/k6-archive-keyring.gpg --keyserver hkp://keyserver.ubuntu.com:80 --recv-keys C5AD17C747E3415A3642D57D77C6C491D6AC1D69
echo "deb [signed-by=/usr/share/keyrings/k6-archive-keyring.gpg] https://dl.k6.io/deb stable main" | sudo tee /etc/apt/sources.list.d/k6.list
sudo apt-get update && sudo apt-get install k6
```

Write a minimal test (10 lines) that hits `GET /api/v1/health`. Run with `k6 run --vus 10 --duration 30s test.js`. Understand the output metrics: `http_req_duration`, `http_req_failed`, `vus`.

**Afternoon (3 hours) — Building Track:**
Write the complete ACOS load test script from the reference in the Go/Rust Integration Roadmap. Three scenarios: note creation (30%), semantic search (40%), feed loading (30%). Configure threshold checks. Run against your ACOS instance. If any threshold fails, investigate why and fix before Phase 9.

---

## SUMMARY: LANGUAGE LEARNING TIMELINE

```
Days  1– 45  Python only — build the habit of daily work
Days 46– 54  Read Rust Book Chapters 1–4 passively (evenings)
Day      55  First Rust code: tokenise_text PyO3 function
Days 56– 62  Rust evenings: structs, enums, error handling
Day      63  First Rust integration: KG Builder Layer 1 in Rust
Days 64– 70  Rust polish: traits, clippy, ADR documentation
Days 71– 85  Read Go Tour passively (evenings)
Day      86  First Go code: fan-out parallel search demo
Days 87–103  Go evenings: interfaces, channels, testing
Day     104  First Go integration: reminder engine in Docker
Days 105–109  Go testing and polish
Day     110  Second Go integration: advisor orchestrator
Days 111–140  Go and Rust parallel — both in production
Days 141–154  Rust deepens: ONNX embedding engine
Day     155  Major Rust integration: in-memory graph engine
Days 156–175  Rust and Python working together daily
Days 176–197  Mobile development (mostly TypeScript + Python)
Day     198  Rust mobile: UniFFI sync engine for Android
Days 199–217  All three languages in production simultaneously
Day     218  Go DevOps: Prometheus custom exporter
Days 219–266  All components stable — polish and optimise
Day     267  Go load testing: k6 replaces Python Locust
Days 268–300  Production hardening with full polyglot stack
```

---

## LEARNING RESOURCE GUIDE

### For Go

| Resource | What it covers | When to use it | Free? |
|---|---|---|---|
| https://go.dev/tour | Basic syntax, goroutines, channels | Days 71–85 as primer | Yes |
| https://gopl.io (book) | Complete language reference | Reference throughout | Yes PDF |
| https://pkg.go.dev/std | Standard library documentation | Look up specific packages | Yes |
| "Concurrency in Go" by Katherine Cox-Buday | Deep goroutine patterns | After Day 110 | Paid book |
| https://go.dev/blog | Official Go blog — idioms and patterns | Ongoing | Yes |

### For Rust

| Resource | What it covers | When to use it | Free? |
|---|---|---|---|
| https://doc.rust-lang.org/book | Complete Rust book — read Ch 1–10 | Days 46–54, then reference | Yes |
| https://doc.rust-lang.org/rust-by-example | Code examples for every concept | Reference when stuck | Yes |
| https://docs.rs | Documentation for every Rust crate | Look up pyo3, rayon, axum, etc. | Yes |
| https://cheats.rs | Rust cheat sheet — syntax quick reference | Keep open while coding | Yes |
| "Programming Rust" by Jim Blandy | Deep ownership and systems programming | After Day 155 if curious | Paid book |

### The one learning principle for both languages

**Do not read passively.** For every concept you read, immediately write 10–20 lines of code that use it. When the code compiles and produces the expected output, you understand the concept. When it does not compile, the error message tells you exactly what you misunderstood. The compiler is your tutor for both Go (which gives extremely helpful error messages) and Rust (which gives the most detailed compile errors of any language — they are worth reading fully).

---

## FINAL INTEGRATION OVERVIEW

When Phase 9 (Day 300) is complete, your ACOS stack runs three languages simultaneously:

```
Python  ──── FastAPI, Intelligence layer, ML integration, Celery (some tasks)
           FastAPI calls Rust (kg-engine) via PyO3 for Layer 1 KG computation
           FastAPI calls Rust (ml-engine) via PyO3 for batch embeddings
           FastAPI calls Rust (graph-engine) via HTTP for graph traversal
           FastAPI queues tasks for Go (advisor-worker) via Redis

Go      ──── Reminder engine (standalone, goroutine per reminder)
           Advisor orchestrator (parallel search, goroutine per source)
           Prometheus exporter (custom ACOS metrics)
           Load testing (k6 runtime)

Rust    ──── KG Builder Layer 1 (Jaccard, PyO3, Rayon)
           Semantic search top-k (cosine similarity, PyO3, Rayon)
           Embedding engine (ONNX, PyO3)
           In-memory graph traversal (Axum HTTP server)
           Mobile sync engine (UniFFI → Android + iOS + WASM)
```

The result: Python handles what Python is best at (ML integration, rapid development, LLM orchestration). Go handles what Go is best at (concurrent network I/O, scheduling). Rust handles what Rust is best at (maximum CPU throughput, memory-safe systems code, cross-platform native compilation). Each language is used for the 20% of problems where it genuinely outperforms the alternatives — not because it is fashionable to use three languages but because each does something the others cannot do as well.