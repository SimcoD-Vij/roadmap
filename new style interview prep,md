# 2026 Software Engineering Interview Skills — Master Roadmap

> Source: Based on the six shifts identified in the interview-trends video transcript — OOP/Low-Level Design, Take-Home Engineering, Raw Coding Fluency, AI System Design, AI Security & Reliability, and Project Depth.

## How to Use This Document

Each skill below has four parts:
1. **What interviewers are actually testing** (not the surface-level topic name)
2. **The exact trap** candidates fall into
3. **A beginner → intermediate → advanced roadmap** with a rough week count
4. **A "what to say in the room" script** — the actual sentences to use when it comes up live

Run all six tracks in parallel, not sequentially. Spend roughly 60% of weekly hours on Track 1 + Track 4 (the two hardest to fake), and rotate the rest.

---

## SKILL MAP (the six things the video flags)

| # | Skill | Old interview version | New interview version |
|---|-------|----------------------|------------------------|
| 1 | Object-Oriented Design | "What is polymorphism?" | "Design the classes for this parking system, live, in a blank editor" |
| 2 | Take-Home Engineering | 30-min algorithm | A repo with bugs — add a feature, explain your PR |
| 3 | Raw Coding Fluency | LeetCode with autocomplete | Blank file, no IDE help, implement from scratch |
| 4 | AI System Design | "Design Netflix" | "Design an agent that can survive production" |
| 5 | AI Security & Reliability | Not asked | Prompt injection, tool permissions, guardrails |
| 6 | Project Depth | 10 CRUD projects | 2–3 projects you can defend under cross-examination |

---

# TRACK 1 — OBJECT-ORIENTED DESIGN & LOW-LEVEL DESIGN (LLD)

## What's actually being tested

Not "do you know the four pillars of OOP." The interviewer wants to see:
- Can you turn a vague sentence ("build a parking system") into classes, in real time?
- Do your classes have single, clear responsibilities?
- What breaks when requirements change, and how cheaply can you absorb that change?
- Can you justify *why* you drew the class boundary where you drew it?

## The trap

You can recite "polymorphism lets a subclass override a parent method" — and still freeze when asked to build a `PaymentProcessor` hierarchy live, because textbook definitions and live design are different muscles.

## THE SCRIPT: How to answer "What is polymorphism?" in an interview

Never answer with the dictionary definition alone. Answer with definition → tiny live example → why it matters for the exact system on the table. Structure:

1. **One-line definition** — "Polymorphism means different classes respond to the same method call in ways specific to themselves, so calling code doesn't need to know which concrete type it's holding."
2. **Immediately ground it in the problem they gave you.** If they said "design a payment system," say: *"For example, here I'd have an abstract `PaymentMethod` with a `charge(amount)` method. `CreditCard`, `UPI`, and `Wallet` each implement `charge()` differently, but the checkout code just calls `payment_method.charge(total)` without an if/else chain checking types."*
3. **Then write it.** Don't just talk — open the editor and sketch the abstract class + two concrete implementations. Interviewers weight code over talk.
4. **Close with the "why it matters" line** — *"This means when we add a new payment method next quarter, I add one new class. I don't touch the checkout function at all — that's the open/closed principle in practice."*

This same four-step pattern (define → ground in their problem → write it → say why it matters) works for **every** OOP concept they ask about: encapsulation, inheritance, abstraction, composition-over-inheritance, SOLID principles. Memorize the *pattern*, not canned answers per concept.

## Beginner (Weeks 1–3): Foundations you must be able to write cold

- Week 1: Classes, constructors, instance vs class variables, `self`/`this`. Build: a `BankAccount` class with `deposit()`, `withdraw()`, and a custom `InsufficientFundsError`.
- Week 2: Inheritance vs composition. Build the same system twice — once using inheritance (`SavingsAccount extends BankAccount`), once using composition (`BankAccount` holds an `InterestStrategy` object) — and write down when each is better.
- Week 3: Encapsulation and access control. Build a `Library` system with private internal state and only method-based access. Learn to explain *why* you hid a field, not just that you hid it.

**Practice site:** Exercism (OOP track in your main language), then rebuild the same exercises with explicit class diagrams on paper/Excalidraw before coding.

## Intermediate (Weeks 4–7): Design under changing requirements

- Week 4: SOLID principles — one violation and one fix per principle, in code you write yourself, not read.
- Week 5: Classic LLD problems, done as **live, timed, blank-editor exercises**:
  - Parking Lot (multiple vehicle types, multiple floors, pricing strategy)
  - Elevator System (multiple elevators, request scheduling)
  - Notification Service (Email/SMS/Push, template + channel abstraction)
- Week 6: Design pattern immersion — but only the ones that show up in real interviews: Strategy, Factory, Observer, Decorator, Singleton (and why Singleton is often criticized). For each: build a mini-project where the pattern is the *only* way to avoid an if/else explosion.
- Week 7: Take one of your Week 5 systems and have someone (or yourself, a day later) hit it with change requests live: "now support hourly AND monthly parking passes," "now support push notifications with retry." Time how fast you adapt the design without a rewrite.

**Practice sites:** "Grokking the Low Level Design Interview" style problem sets, GitHub repos of LLD problems (search "low level design interview questions"), and re-implementing them cold without looking at the reference solution first.

## Advanced (Weeks 8–10): Interview simulation and defense

- Week 8: Do 5 mock LLD interviews (with a peer, mentor, or by recording yourself) where you narrate your thinking out loud the entire time — silence reads as "can't design," even if you're thinking correctly.
- Week 9: Practice the "what happens if..." stress-test format: after you finish a design, force yourself to answer 5 follow-up "what if we add X" questions without redesigning from scratch.
- Week 10: Write 3 short design docs (1 page each) explaining a class hierarchy you built, including "why I chose composition over inheritance here" — this becomes both interview prep and portfolio material.

---

# TRACK 2 — TAKE-HOME ASSIGNMENT ENGINEERING

## What's actually being tested

Not "does the code run." They're evaluating: project structure, test coverage, edge-case handling, API cleanliness, documentation of decisions, and — critically — **can you explain your own submission out loud afterward.**

## Beginner (Weeks 1–2)

- Learn to structure any small project the same repeatable way: `src/`, `tests/`, `README.md`, `.env.example`, a short `DECISIONS.md`.
- Practice writing tests *before* you consider a feature "done" — even 3–4 unit tests per function is enough at this stage.
- Rebuild one of your old personal projects with this structure and a proper README that states: problem, approach, how to run, what you'd improve with more time.

## Intermediate (Weeks 3–5)

- Simulate real take-homes: pick a small open-source repo, deliberately introduce 2 bugs, then fix them and write a PR description explaining root cause + fix + how you verified it.
- Practice integrating a third-party API (any public API) into a small service with proper error handling: timeouts, retries, rate-limit handling, meaningful error messages.
- Learn to write a "what I'd do with another week" section — interviewers explicitly listen for this; it shows you know the limits of your own solution.

## Advanced (Weeks 6–7)

- Time-box yourself: build a small feature-complete service in 3–4 hours, exactly like a real take-home, then do a 10-minute self-recorded "explain your submission" walkthrough — this trains the exact skill of narrating your own code under time pressure.
- Get a second person to review your take-home cold and ask you 5 questions about it — treat every answer as if it were being scored.

**What to say when asked to walk through your submission:** *"Here's the problem I solved, here's the approach I took and why I picked it over the alternative, here's what I tested and why, and here's what I'd improve with another week."* — this exact four-part structure is what the video explicitly calls out as "real engineering."

---

# TRACK 3 — RAW CODING FLUENCY (NO IDE, NO AUTOCOMPLETE, NO COPILOT)

## What's actually being tested

Whether you can *think* while coding, not whether you've memorized syntax. IDEs hide gaps in your knowledge (imports, function signatures, syntax errors) that a browser-based interview editor will expose instantly.

## The self-test (do this weekly)

Open a completely blank file. No autocomplete, no Copilot, no ChatGPT, no docs tab. Implement something non-trivial from scratch (a small parser, a caching decorator, a rate limiter) in one sitting. If you get stuck on syntax rather than logic, that's your signal to drill more.

## Beginner (Weeks 1–3)

- Re-learn your primary language (Python is explicitly emphasized for AI/ML/backend roles) at the "no lookup needed" level: list/dict/set/tuple methods, comprehensions, generators, decorators, context managers, exceptions, and the standard library modules you actually use (`itertools`, `collections`, `functools`).
- Daily 30-minute drill: solve one small problem in a plain text editor with autocomplete disabled.

## Intermediate (Weeks 4–6)

- Move to a **browser-based editor** (CoderPad, HackerRank's plain editor, or even a GitHub Gist in the browser) for all practice — this replicates the real interview environment.
- Practice explaining your code out loud *while* you type it — verbalizing while coding is a distinct skill from silent coding.

## Advanced (Weeks 7–8)

- Timed, no-tool implementation of classic building blocks from memory: an LRU cache, a simple pub/sub system, a basic rate limiter, a small state machine. These come up constantly as "no autocomplete" interview questions because they test real understanding, not memorized algorithms.
- Do at least 3 mock interviews using a shared-document / browser editor with zero tooling assistance.

---

# TRACK 4 — AI SYSTEM DESIGN (FROM ZERO)

## What's actually being tested

Traditional system design asks "how do you scale this." AI system design adds: *which model, single vs. multi-model, where retrieval happens, how you handle wrong answers, how you evaluate and monitor the system, and how you control inference cost* — and for agentic systems, tools, multi-step state, memory, and an LLM making decisions inside the system.

## Starting from absolute zero — do these in order

### Phase 0: Foundational literacy (Weeks 1–2)
You cannot design AI systems without knowing what the pieces are. Learn, in this order:
1. What an LLM actually is at a black-box level (input tokens → probability distribution over next tokens) — you don't need the math, you need the mental model.
2. What "context window" means and why it's a hard constraint on everything you design.
3. What embeddings are (a way to turn text into vectors so "meaning" can be compared numerically).
4. What a prompt is vs. a system prompt vs. a completion.

**Deliverable:** Write a 1-page doc in your own words explaining these 4 concepts as if teaching a junior engineer.

### Phase 1: Retrieval-Augmented Generation — RAG (Weeks 3–5)
This is the single most commonly asked AI system design pattern.
1. Understand *why* RAG exists: LLMs don't know your private/recent data, and fine-tuning is expensive and stale fast — RAG retrieves relevant context at query time instead.
2. Learn the pipeline end to end: document → chunking → embedding → vector store → similarity search → retrieved chunks → prompt assembly → LLM call → answer.
3. Build a tiny RAG system yourself: take 10–20 of your own notes/PDFs, chunk them, embed them with a free embedding model, store in a lightweight vector store (Chroma or FAISS), and query it.
4. Learn to discuss the failure points, because this is what gets asked: bad chunking → irrelevant context; too many chunks → context overflow; stale embeddings → wrong retrieval; no re-ranking → noisy results.

**Deliverable:** A working small RAG project + a written note listing 5 ways it could fail and how you'd detect each.

### Phase 2: Tool Calling and Agents (Weeks 6–8)
1. Learn what "tool calling" means: the model is given a list of available functions with schemas, and instead of answering directly it can output a structured request to call one.
2. Build a tiny agent: an LLM that can call 2–3 simple tools (a calculator function, a weather lookup, a search function) and chain them to answer a multi-step question.
3. Learn agent orchestration patterns: single-agent-with-tools vs. multi-agent (planner + executor) vs. supervisor pattern.
4. Learn what "state" and "memory" mean in an agent context — short-term (conversation history) vs. long-term (persisted facts/embeddings retrieved across sessions).

**Deliverable:** A small working agent + a diagram of its control flow (what decides the next step, where state lives).

### Phase 3: Evaluation, Observability, and Cost (Weeks 9–11)
This is the layer most self-taught candidates skip — and the layer interviewers probe hardest.
1. Evaluation: how do you know if your AI system is actually good? Learn the difference between automated eval (exact match, LLM-as-judge, retrieval precision/recall) and human eval.
2. Observability: what does it mean to "monitor" an LLM system in production — logging prompts/responses, tracking latency per step, tracking token cost per request, catching silent failures (empty/garbage outputs).
3. Model routing: when and why you'd use a cheap/fast model for simple queries and a larger model only when needed.
4. Cost and latency tradeoffs: learn to reason about "more retrieval = better accuracy but slower and costlier" as an explicit design tradeoff, not an afterthought.

**Deliverable:** Add basic logging/cost-tracking to your Phase 2 agent, and write a short doc: "how I'd know if this system degraded in production."

### Phase 4: Full mock AI system design interviews (Weeks 12–14)
Practice designing (on a whiteboard/doc, not code) systems like:
- "Design a customer support AI agent for an e-commerce company"
- "Design a coding assistant that can read a codebase and answer questions about it"
- "Design a RAG system over a company's internal documentation with strict access control"

For each, force yourself to cover: model choice and why, single vs multi-model, where retrieval happens, how wrong answers are caught, how you evaluate, how you monitor, how you control cost — the exact list the video names.

**What to say when they ask "design an AI agent that does X":** Don't jump straight to architecture. Say out loud first: *"Let me clarify — is this single-turn or does it need memory across sessions? Does it need to call external tools? What's an acceptable latency and cost per request? What happens when it's wrong — is there a human in the loop?"* Then draw the pipeline. Asking these questions first is itself part of what's being scored.

---

# TRACK 5 — AI SECURITY & RELIABILITY

## What's actually being tested

Whether you understand AI systems as things that can be *attacked*, not just things that can be *wrong*. This track is explicitly named as one candidates skip entirely, which makes it high-leverage.

## Beginner (Weeks 1–2): Vocabulary and mental models

Learn these concepts conceptually before anything technical:
1. **Prompt injection** — an attacker hides instructions inside content the model processes (a document, a webpage, a user message) to hijack its behavior.
2. **Jailbreaks** — techniques to get a model to bypass its own safety instructions.
3. **Data leakage** — a model exposing information it shouldn't (private data, system prompts, other users' data) through its output.
4. **Excessive tool permissions** — an agent given more access (to databases, file systems, external APIs) than the task actually requires.
5. **Insecure tool calling** — a model being able to trigger a real, damaging action (delete data, send money, send emails) without validation or human approval.
6. **Hallucination as a reliability issue, not just an accuracy issue** — when a wrong answer becomes a wrong *action*.

**Deliverable:** For each of the 6 terms above, write one concrete example scenario in your own words (not copied) using one of your own AI-track projects as the setting.

## Intermediate (Weeks 3–5): Apply it to your own systems

1. Take your Track 4 agent (from RAG/tool-calling phase) and do a self "red team" pass: what's the worst thing someone could make it do by feeding it a malicious input? Write it down.
2. Add basic mitigations to that agent: input validation before tool calls, output filtering, a permissions boundary (the tool function itself refuses actions outside an allow-list), and logging of every tool call made.
3. Learn the concept of "least privilege" for AI agents specifically: if an agent only needs read access to a database, it should never be given write access, even if that's more convenient to build.

## Advanced (Weeks 6–7): Engineering-level answers, not buzzwords

Practice answering these exact style of questions with concrete mechanisms, not definitions:
- *"If your agent has access to your company's internal database, what prevents it from exposing confidential information?"* → Answer with a real mechanism: row-level access scoped to the querying user's permissions, a read-only credential, output redaction rules, and an audit log — not "we'd be careful."
- *"If an LLM is allowed to call external tools, what permissions does it actually have?"* → Answer by describing an explicit allow-list of tools with scoped credentials, not "it can call APIs."
- *"If the model makes a wrong decision, where do you catch it?"* → Answer with a specific layer: validation before the action executes, a confidence threshold that triggers human approval for high-risk actions, and post-hoc monitoring that flags anomalous tool-call patterns.

**Deliverable:** A short `SECURITY.md` for your Track 4 agent project listing: what it can access, what it's explicitly forbidden from doing, what happens on a suspicious input, and what's logged.

---

# TRACK 6 — PROJECT DEPTH (FEWER PROJECTS, DEFENSIBLE UNDER QUESTIONING)

## What's actually being tested

Whether your resume projects are real engineering or resume filler. A to-do app, weather app, calculator, or basic CRUD dashboard signals "tutorial-follower," not "engineer" — and once you claim a project, it becomes fair game for deep questioning.

## The standard to hit

Pick 2–3 projects, not 10. Each project should force you to think about **data, models/logic, APIs, deployment, monitoring, and failure cases** — not just "does the happy path work."

## Roadmap (ongoing, runs alongside Tracks 1–5)

- **Weeks 1–4 — Pick and scope one project** from this tier (not below it):
  - An AI-powered recommendation system (with an actual dataset, not toy data)
  - A RAG application where you *measure* retrieval quality, not just demo it working
  - An AI agent that uses real tools to complete a multi-step task
  - A fraud/anomaly detection pipeline with a real evaluation metric
  - A real-time ML inference API with latency benchmarks

- **Weeks 5–8 — Build the "boring but essential" parts** that most candidates skip: tests, error handling, a README with architecture diagram, basic monitoring/logging, and a short `ADR/` (architecture decision record) folder explaining *why* you made 2–3 key technical choices.

- **Weeks 9–10 — Defend it.** For each project, pre-write answers to the exact style of follow-up questions the video names for a RAG project: *chunking strategy, embedding choice, retrieval method, evaluation approach, why this model, latency and cost.* If you can't answer these cold, the project isn't done yet — treat this list as your project's actual finish line, not the demo working.

**What to say when asked "walk me through this project":** Lead with the problem, not the tech stack: *"The problem was X. I chose approach Y because [tradeoff]. Here's what I measured to know it worked. Here's the part I'd redesign if I did it again."* Never lead with a list of libraries — that's what makes a project read as a tutorial clone instead of engineering judgment.

---

# COMBINED WEEKLY TIME ALLOCATION (running all 6 tracks together)

| Track | % of weekly study time | Notes |
|-------|------------------------|-------|
| 1. OOP / LLD | 25% | Live-coded, not read-only |
| 4. AI System Design | 25% | Build, don't just read about RAG/agents |
| 6. Project Depth | 20% | This is where 1, 4, and 5 get applied together |
| 3. Raw Coding Fluency | 15% | Daily 30-min drills, no tools |
| 5. AI Security | 10% | High leverage, most people skip it entirely |
| 2. Take-Home Engineering | 5% | Mostly habit-building (structure, docs, tests) |

Track 6 (Project Depth) is where everything else converges — your 2–3 defensible projects should be the proving ground for your OOP design, your AI system design choices, and your security thinking, all at once.

---

# THE ONE-SENTENCE VERSION

The interview isn't testing "do you know the terms" anymore — it's testing "can you build it, explain why you built it that way, and defend it when someone pushes back." Every track above is really the same skill practiced in a different context: **think out loud, ground abstractions in a concrete example, write the code, then justify the decision.**
