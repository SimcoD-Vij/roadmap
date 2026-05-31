# AI Job Hunting System — Complete Learning & Build Roadmap
## From Zero Knowledge to Production-Grade MNC-Level System

---

> **Who this is for:** Someone starting from absolute zero — no programming, no databases, no system design knowledge — who wants to build a production-grade AI-powered autonomous job hunting system that MNC engineers would be proud of.
>
> **How to use this:** Read the System Architecture section first. Understand the full picture before touching a single line of code. Then follow the daily plan strictly. Every day has a purpose. Every mini-project connects to the final system.

---

# PART 0 — THE COMPLETE SYSTEM ARCHITECTURE

> Read this entire section before Day 1. You need the mental picture first. A builder who doesn't know what they're building wastes months going in the wrong direction.

---

## What You Are Building — Plain English

You are building an intelligent software system that works like a full-time job hunting assistant that never sleeps. It watches company websites for new job openings, reads job descriptions and understands them deeply, matches them against your skills and projects, generates a customised resume for each job, fills and submits application forms automatically, monitors your email for recruiter responses, tracks every application in a dashboard, and has a team of AI agents that debate and analyse your resume the way real HR experts and technical interviewers would.

You paste a WhatsApp message about a job — the system takes over completely.

---

## The Full System — All Components

```
┌─────────────────────────────────────────────────────────────────┐
│                     YOUR SYSTEM — BIG PICTURE                   │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  INPUT SOURCES                                                  │
│  ┌──────────┐  ┌──────────┐  ┌──────────┐  ┌──────────┐       │
│  │WhatsApp  │  │ Scraped  │  │  Manual  │  │  Email   │       │
│  │  Paste   │  │  Jobs    │  │  Entry   │  │  Inbox   │       │
│  └────┬─────┘  └────┬─────┘  └────┬─────┘  └────┬─────┘       │
│       └─────────────┴─────────────┴──────────────┘            │
│                              │                                  │
│                              ▼                                  │
│              ┌───────────────────────────┐                     │
│              │   ORCHESTRATOR AGENT      │                     │
│              │  (Decides which tools     │                     │
│              │   to use and in what      │                     │
│              │   order — ReAct pattern)  │                     │
│              └───────────┬───────────────┘                     │
│                          │                                      │
│         ┌────────────────┼────────────────┐                    │
│         ▼                ▼                ▼                    │
│  ┌─────────────┐  ┌─────────────┐  ┌─────────────┐           │
│  │  TOOL LAYER │  │  AI LAYER   │  │  DATA LAYER │           │
│  │             │  │             │  │             │           │
│  │ • Scraper   │  │ • Embedding │  │  MongoDB    │           │
│  │ • Playwright│  │   Model     │  │  Atlas      │           │
│  │ • Form Fill │  │ • Local LLM │  │             │           │
│  │ • Email Mon │  │   (Ollama)  │  │ Collections:│           │
│  │ • Web Search│  │ • Cloud LLM │  │ • jobs      │           │
│  │ • IMAP      │  │   (Groq)    │  │ • projects  │           │
│  └─────────────┘  └─────────────┘  │ • skills    │           │
│                                     │ • companies │           │
│         ┌───────────────────┐       │ • resumes   │           │
│         │ MULTI-AGENT DEBATE│       │ • apps      │           │
│         │    SYSTEM         │       │ • users     │           │
│         │                   │       └─────────────┘           │
│         │ • HR Strategist   │                                  │
│         │ • Tech Expert     │                                  │
│         │ • ATS Compliance  │                                  │
│         │ • Industry Insider│                                  │
│         │ • Devil's Advocate│                                  │
│         │ • Synthesis Judge │                                  │
│         └──────────┬────────┘                                  │
│                    │                                            │
│                    ▼                                            │
│         ┌─────────────────────┐                                │
│         │   OUTPUT LAYER      │                                │
│         │                     │                                │
│         │ • Generated Resume  │                                │
│         │ • Cover Letter      │                                │
│         │ • Interview Prep    │                                │
│         │ • Form Auto-Fill    │                                │
│         │ • Telegram Alerts   │                                │
│         │ • Daily Report      │                                │
│         │ • Google Sheets     │                                │
│         └──────────┬──────────┘                                │
│                    │                                            │
│                    ▼                                            │
│         ┌─────────────────────┐                                │
│         │   NEXT.JS DASHBOARD │                                │
│         │   (Deployed Vercel) │                                │
│         │                     │                                │
│         │ • Application Board │                                │
│         │ • Analytics         │                                │
│         │ • Company Intel     │                                │
│         │ • Debate Reports    │                                │
│         │ • Resume History    │                                │
│         └─────────────────────┘                                │
└─────────────────────────────────────────────────────────────────┘
```

---

## The Technology Stack — Complete

| Layer | Technology | Why This, Not Something Else |
|---|---|---|
| Database | MongoDB Atlas | Stores documents, vectors, and runs graph queries — three databases in one |
| Local AI | Ollama + Llama 3.2 8B | Free, private, runs on your machine, no API cost |
| Cloud AI | Groq API (Llama 70B) | Free tier, fastest inference, same open-source models |
| Embeddings | nomic-embed-text via Ollama | Free, local, specifically good for technical text |
| Backend | FastAPI (Python) | Async, fast, auto-generates API documentation |
| Frontend | Next.js 14 | React-based, deploys free on Vercel, server-side rendering |
| Orchestration | LangGraph | Manages agent tool selection and task sequencing |
| Multi-Agent | CrewAI | Built specifically for multi-agent debate and collaboration |
| Browser Automation | Playwright | Supports all browsers, async, stealth plugins available |
| Scheduling | MongoDB Atlas Triggers | Replaces Celery and Redis — no extra service needed |
| Notifications | Telegram Bot API | Free, instant, works on any device |
| Deployment — Frontend | Vercel | Free, auto-deploys from GitHub, global CDN |
| Deployment — Backend | Railway | Free tier, always-on, easy Python deployment |
| Resume Generation | LaTeX + Jinja2 | Industry-standard PDF quality, programmatically fillable |
| Version Control | Git + GitHub | Industry standard, also your portfolio |

---

## How Data Flows Through the System — Step by Step

**Scenario: You paste a WhatsApp message about a company**

1. You paste raw text into the dashboard input box
2. FastAPI backend receives the text
3. Orchestrator Agent reads the text and reasons: "I need to extract structure, verify the company, find the job, and match it to the profile"
4. Orchestrator calls the WhatsApp Extractor tool → extracts company name, role, deadline
5. Orchestrator calls the Company Legitimacy tool → checks MCA, LinkedIn, WHOIS
6. Orchestrator calls the Company Intelligence tool → pulls Glassdoor, Crunchbase, engineering blog
7. Orchestrator calls the Career Page Scraper tool → finds and scrapes the actual job listing
8. Orchestrator calls the Eligibility Matcher tool → scores the job against your MongoDB profile
9. If score is above threshold, orchestrator calls the Project Matcher tool → vector search finds your best projects
10. Orchestrator calls the Keyword Extractor tool → extracts ATS keywords from JD using local Ollama model
11. Job document created in MongoDB with all extracted data and embeddings
12. MongoDB Atlas Change Stream detects new document → triggers Resume Generator
13. Resume Generator selects base LaTeX template → fills with Jinja2 → injects keywords → compiles PDF → stores in MongoDB
14. Multi-Agent Debate System activates — 6 agents analyse resume and JD simultaneously
15. Agents cross-examine each other's positions over two rounds
16. Synthesis Judge produces final verdict, improvement list, and interview prep questions
17. All results stored in MongoDB
18. Telegram notification sent to your phone with match score, legitimacy status, debate summary, and approval button
19. You tap Approve → Playwright opens application page → stealth mode active → session cookies loaded → form filled using your MongoDB profile → resume PDF uploaded → screenshot taken → form submitted → status updated to "applied"
20. Daily Google Sheet report updated at 6am with this application

Every single step above maps to something you will learn and build in this roadmap.

---

## The Learning Philosophy

**Mental model first, code second.** Every day starts with understanding WHY before HOW.

**Everything you learn maps to a specific component.** Nothing is abstract — each concept is justified with exactly where it appears in your system.

**Mini-projects are modular.** Every mini-project you build is a real module of the final system. At the end, you assemble them.

**Industry practices from Day 1.** The way you write code, document it, and version it will be the way MNC engineers do it — not tutorials, not shortcuts.

---

# PART 1 — PHASE 1: FOUNDATIONS
## Weeks 1 through 4 — How Computers and Code Actually Work

---

## WEEK 1 — The Mental Model of Programming and Computers

> **Where this appears in your system:** Everything. You cannot build any part of the system without this foundation. A house without a foundation collapses immediately.

---

### DAY 1 — How Computers Actually Work

**Before you open any code editor, understand this.**

A computer is a machine that does exactly one thing: it executes instructions one at a time, very fast. That's it. The magic of software is that these instructions, composed cleverly, create complex behaviour.

**What a CPU does:**
The CPU — Central Processing Unit — is the brain. It reads an instruction from memory, executes it, reads the next instruction. That's all it does, billions of times per second.

**What RAM is:**
RAM — Random Access Memory — is the working space. When you run a program, it gets loaded into RAM. RAM is fast but temporary — it disappears when you turn off the computer. Think of RAM like a workbench — you put things on it while working, but clear it when done.

**What a hard drive or SSD is:**
Permanent storage. Your files, your database, your code — all live here. Much slower than RAM but survives power-off. Think of it like a filing cabinet.

**What an operating system does:**
The OS — Linux, Windows, macOS — manages all hardware resources and runs multiple programs simultaneously by rapidly switching between them. In your system, you will use Linux on your server because it is free, stable, and what every MNC server runs.

**What a process is:**
When you run a program, the OS creates a process — an isolated running instance of that program with its own RAM allocation. When your FastAPI server runs, it is a process. When your Playwright browser runs, it is another process. They can communicate but cannot break into each other's memory.

**What a thread is:**
A thread is a unit of execution within a process. One process can have many threads running in parallel. This is important for your system — when your scraper checks 20 company websites at the same time, it uses multiple threads or async operations so they run simultaneously instead of one at a time.

**Where this appears in your system:**
Understanding processes and threads explains why your Playwright automation runs in a separate process, why your FastAPI backend uses async functions to handle multiple requests simultaneously, and why MongoDB is a separate process from your backend.

**Today's task — Think through these questions:**
1. If RAM is temporary, where does MongoDB store data between restarts?
2. If your scraper checks 20 websites one at a time, and each takes 3 seconds, how long does it take total? If they run in parallel, how long does it take?
3. When you deploy your system to a cloud server, what is that server physically? What is different about it from your laptop?

**Active Recall Questions:**
- What is the difference between RAM and SSD storage? Give an analogy.
- What happens to a running program when you restart a computer?
- Why do MNC servers run Linux instead of Windows?

---

### DAY 2 — The Terminal and Linux — Your Primary Tool

**Why this, not a GUI:**
Every server in the world — AWS, Google Cloud, Railway, your Raspberry Pi running your local system — runs Linux without a graphical interface. You control it through text commands in a terminal. Knowing the terminal is not optional — it is the primary interface for production software.

**What the terminal is:**
A text interface to your operating system. You type a command, the OS executes it, you see the result. It is faster, more precise, and more powerful than clicking through graphical interfaces.

**Where this appears in your system:**
- Starting your FastAPI server: `uvicorn main:app --reload`
- Starting Ollama with a model: `ollama run llama3.2`
- Connecting to MongoDB: `mongosh`
- Deploying to Railway: `railway up`
- Compiling a LaTeX resume: `pdflatex resume.tex`
- Running Playwright: all executed from terminal
- Managing your server: entirely through terminal

**Core commands you must know — and exactly why:**

`pwd` — Print Working Directory. Shows you where you are in the file system. Your system has many folders — knowing where you are prevents deleting the wrong files or running scripts from the wrong location.

`ls -la` — Lists all files including hidden ones with permissions. In your system, configuration files like `.env` containing API keys are hidden files (start with dot). You need this to see them.

`cd folder_name` — Change Directory. How you navigate between folders. You will switch between your project folders constantly.

`mkdir folder_name` — Make Directory. You will create organised folder structures for every module of your system.

`cp source destination` — Copy a file. Used for backing up configuration files before editing.

`mv source destination` — Move or rename a file. Used when reorganising your project structure.

`rm filename` — Remove a file. Permanent — no recycle bin. Be careful.

`cat filename` — Print file contents to screen. Used to quickly read log files, check configuration, verify a generated resume content.

`grep "search term" filename` — Search inside files. Used to find error messages in logs, find specific functions in code files.

`| pipe` — The pipe takes the output of one command and feeds it as input to another. Example: `cat logfile.txt | grep "ERROR"` — read the log file and show only lines containing "ERROR." This is how you debug in production.

`ps aux` — Show all running processes. You will use this to check if your FastAPI server, Ollama, and Playwright are all running.

`kill process_id` — Stop a running process. When your server crashes and won't restart, you kill the old process first.

`chmod +x filename` — Make a file executable. Your startup scripts need this permission to run.

`ssh user@server_ip` — Connect to a remote server. When you deploy your system to Railway or a VPS, you connect to it this way.

**Today's Task:**
Open your terminal right now and do every command above. Create a folder called `job-agent`, inside it create folders called `backend`, `frontend`, `agents`, `automation`, `docs`. Navigate into each one and back out. This folder structure is the beginning of your actual project.

**Mini Task — Document your folder structure:**
Draw it out on paper:
```
job-agent/
├── backend/
├── frontend/
├── agents/
├── automation/
└── docs/
```
This is the beginning of your production project structure.

---

### DAY 3 — Git and GitHub — How Professional Code is Managed

**Why this is foundational:**
Every MNC engineer uses Git. Every codebase in the world uses Git. It is not optional. More importantly for you — your GitHub profile is your visible portfolio. Every mini-project you build goes on GitHub. Recruiters look at your GitHub before they look at your resume.

**What Git is conceptually:**
Git is a time machine for your code. Every time you make a meaningful change, you take a snapshot called a commit. You can go back to any snapshot. You can create parallel versions called branches to try things without breaking the main version. Multiple people can work on the same codebase simultaneously without overwriting each other.

**What GitHub is:**
GitHub is a website that stores your Git repositories online. It is both a backup and a portfolio. When your system is fully built, your GitHub shows every decision you made, every feature you built, and how your engineering thinking evolved over time.

**Where Git appears in your system:**
- Every module you build is version-controlled from Day 1
- Your Railway deployment reads your GitHub repository directly — you push code to GitHub, Railway automatically deploys it
- Your Vercel frontend deployment is the same — push to GitHub, automatically live
- Your AI fine-tuning datasets are stored in GitHub
- Your system documentation lives in GitHub as markdown files

**Core Git workflow — the three stages:**

The working directory is where you write code. When you write a new function, you are in the working directory.

The staging area is where you place files you want to include in your next snapshot. Not every changed file needs to go in every commit.

The repository is where your snapshots live permanently.

`git init` — Initialises a new Git repository in the current folder. Run this once when starting a new project.

`git add filename` or `git add .` — Stages a file or all changed files. The dot means "everything changed."

`git commit -m "descriptive message"` — Creates a snapshot with your message explaining what changed and why. The message is for your future self and your teammates.

`git push origin main` — Sends your local commits to GitHub. "origin" is the name of your GitHub repository. "main" is the branch name.

`git pull` — Gets the latest changes from GitHub to your local machine. Important when you work on multiple machines.

`git log --oneline` — Shows your commit history in compact form. You can see every decision you made.

`git branch feature-name` — Creates a new branch to work on a feature without touching main code.

`git checkout branch-name` — Switches to a different branch.

`git merge branch-name` — Combines a branch's changes back into main.

**MNC-level commit message practice:**
Bad: `git commit -m "fixed stuff"`
Good: `git commit -m "feat: add Playwright form detector for Greenhouse adapter"`
Good: `git commit -m "fix: handle CAPTCHA detection timeout in stealth scraper"`
Good: `git commit -m "docs: add MongoDB schema documentation for jobs collection"`

The format is: `type: short description`. Types are `feat` (new feature), `fix` (bug fix), `docs` (documentation), `refactor` (code restructure), `test` (adding tests).

**Today's Task:**
1. Create a GitHub account at github.com
2. Create a repository called `job-agent`
3. Clone it to your machine: `git clone https://github.com/yourusername/job-agent`
4. Navigate into it, create a file called `README.md`, write one sentence about what you are building
5. Stage, commit, and push it
6. View it live on GitHub

**This README will grow into your project's public documentation. Start it now.**

---

### DAY 4 — Python Fundamentals Part 1 — Variables, Types, and Logic

**Why Python:**
Python is the language of AI, data science, backend APIs, automation, and scripting. Every AI library — LangChain, CrewAI, LangGraph, Playwright Python, the Anthropic SDK, HuggingFace — is Python-first. Your entire backend, all agents, all scrapers, all automation — Python.

**Where each concept appears in your system:**

**Variables** — Store job data extracted from a WhatsApp message. Store a company name while the scraper finds the careers page. Store your match score during eligibility calculation.

**Strings** — Job descriptions are strings. Company names are strings. ATS keywords extracted by the LLM are lists of strings. Your LaTeX resume template is a string with placeholders.

**Numbers** — Match scores are numbers between 0 and 100. Embedding vectors are lists of floating point numbers. Your application count is an integer. Salary estimates are numbers.

**Booleans** — Is this company legitimate? True or False. Is this job above the threshold? True or False. Has this application been submitted? True or False.

**Lists** — Your skills are a list. Required skills from a job description are a list. Top 3 matching projects are a list. All companies to monitor are a list.

**Dictionaries** — A job posting is a dictionary: `{"title": "Backend Engineer", "company": "Stripe", "skills": ["Python", "AWS"], "score": 87}`. A MongoDB document is essentially a Python dictionary.

**If/else logic** — If match score is above 70, add to shortlist. If company has no LinkedIn, flag as suspicious. If application form is Greenhouse, use Greenhouse adapter. If CAPTCHA detected, send Telegram alert.

**Loops** — For every company in the monitoring list, scrape their careers page. For every new job found, calculate match score. For every missing keyword, inject it into the resume.

**Functions** — `extract_company_from_text(raw_text)` — takes WhatsApp paste, returns company name. `calculate_match_score(job_requirements, user_profile)` — returns number. `generate_resume(job_id, template_type)` — returns PDF path. Every module in your system is a set of functions.

**Today's Task:**
Install Python 3.12 on your machine. Open a Python file. Write the following and understand each line:

```python
# This represents one job in your system
job = {
    "title": "Backend Engineer",
    "company": "Stripe",
    "required_skills": ["Python", "AWS", "PostgreSQL"],
    "location": "Bangalore",
    "match_score": 0
}

# Your skills
my_skills = ["Python", "MongoDB", "React", "Node.js"]

# Calculate how many required skills you have
matching_skills = []
for skill in job["required_skills"]:
    if skill in my_skills:
        matching_skills.append(skill)

# Calculate score
match_percentage = (len(matching_skills) / len(job["required_skills"])) * 100
job["match_score"] = match_percentage

print(f"Job: {job['title']} at {job['company']}")
print(f"Matching skills: {matching_skills}")
print(f"Match score: {match_percentage}%")

if match_percentage >= 70:
    print("SHORTLISTED — proceed with application")
else:
    print("BELOW THRESHOLD — skip")
```

Run it. Change the skill lists. Understand what happens.

**This is the foundation of your eligibility matching module.**

**Active Recall Questions:**
- What is the difference between a list and a dictionary in Python?
- Why do we use functions instead of writing all code in one long sequence?
- In the code above, what does `len()` do and why is it needed?

---

### DAY 5 — Python Fundamentals Part 2 — Functions and File Handling

**Where this appears in your system:**

Functions are the building blocks of every module. The scraper is a function. The eligibility matcher is a function. The resume generator is a function. The form filler is a function. You will build hundreds of functions that call each other.

File handling is how your system reads and writes configuration, saves generated PDFs to disk, reads LaTeX templates, loads your profile YAML, and writes logs.

**Core concepts:**

**Defining and calling functions:**
A function takes inputs, does something, and returns an output. In your system, every tool the Orchestrator Agent uses is a function with a specific input and output signature.

```python
def calculate_match_score(required_skills, my_skills):
    """
    Calculate what percentage of required skills the user has.

    Args:
        required_skills: list of strings from job description
        my_skills: list of strings from user profile

    Returns:
        float between 0 and 100
    """
    if not required_skills:
        return 0

    matches = [skill for skill in required_skills if skill in my_skills]
    return (len(matches) / len(required_skills)) * 100
```

Notice the docstring — the triple-quoted text explaining what the function does, what it takes, and what it returns. Every function in your production system has this. This is the MNC standard.

**Reading files:**
Your LaTeX resume template is a file. Your profile configuration is a YAML file. Your system reads these:

```python
# Reading a LaTeX template
with open("templates/resume.tex", "r") as file:
    template_content = file.read()

# Reading a JSON file (like a job posting saved to disk)
import json
with open("data/job_123.json", "r") as file:
    job_data = json.load(file)
```

**Writing files:**
Your generated resume gets written to disk. Your scraper saves raw job HTML. Your logger writes errors:

```python
# Writing a processed resume to disk
with open("output/resume_stripe_backend.pdf", "wb") as file:
    file.write(pdf_bytes)

# Writing a log entry
with open("logs/scraper.log", "a") as file:  # "a" means append, not overwrite
    file.write(f"2026-05-27 09:00: Scraped Stripe careers page, found 3 new jobs\n")
```

**Today's Task:**
1. Create a file called `profile.json` with your actual skills, projects, experience
2. Write a function that reads this file and prints your top 5 skills
3. Write a function that takes a job's required skills list and your profile, calculates match score, and saves the result to a file called `match_results.json`
4. This becomes Module 1 of your eligibility matcher

**Mini-Project Assignment 1 (complete today and Day 6):**
Build a command-line eligibility checker. It reads your profile from `profile.json`, reads a job description from `job.json`, calculates match score, prints which skills match and which are missing, and saves results to `results.json`. This is a real module of your system.

---

### DAY 6 — Python Fundamentals Part 3 — Error Handling and Modules

**Why error handling is not optional:**
Your production system runs 24/7 unattended. When it fails — and it will fail — it must fail gracefully, log what happened, and continue rather than crash everything. A scraper hitting a CAPTCHA must not crash the entire pipeline. An email classification failure must not stop the application tracker.

**Where this appears in your system:**
Every network call (scraping, API call, email check) can fail. Every file operation can fail. Every database operation can fail. Every one of these must be wrapped in error handling.

```python
def scrape_careers_page(url):
    """Scrape job listings from a company careers page."""
    try:
        response = requests.get(url, timeout=10)
        response.raise_for_status()  # raises error if status is 4xx or 5xx
        return parse_jobs(response.text)

    except requests.exceptions.Timeout:
        log_error(f"Timeout scraping {url} — will retry in next cycle")
        return []

    except requests.exceptions.ConnectionError:
        log_error(f"Cannot reach {url} — site may be down")
        return []

    except Exception as e:
        log_error(f"Unexpected error scraping {url}: {str(e)}")
        return []
```

The function always returns something — either job listings or an empty list. It never crashes the caller.

**Modules — how professional code is organised:**
A module is a Python file. A package is a folder of Python files with an `__init__.py` file. Your system will have this structure:

```
backend/
├── __init__.py
├── scrapers/
│   ├── __init__.py
│   ├── career_page_scraper.py
│   ├── job_board_scraper.py
│   └── whatsapp_extractor.py
├── matchers/
│   ├── __init__.py
│   ├── eligibility_matcher.py
│   └── project_matcher.py
├── generators/
│   ├── __init__.py
│   ├── resume_generator.py
│   └── cover_letter_generator.py
├── automation/
│   ├── __init__.py
│   ├── form_filler.py
│   └── session_manager.py
└── agents/
    ├── __init__.py
    ├── orchestrator.py
    └── debate_agents.py
```

Each file contains one focused set of functions. The scraper module only scrapes. The matcher module only matches. This is the Single Responsibility Principle — a core MNC engineering principle.

**Today's Task:**
Reorganise your Day 5 code into proper modules. Create the folder structure above. Move your eligibility matcher functions into `matchers/eligibility_matcher.py`. Write an `__init__.py` file. Import and use them from a main script. Push to GitHub with proper commit messages.

---

### DAY 7 — WEEK 1 REVIEW + MINI-PROJECT SUBMISSION

**Week 1 Concept Review — Answer these without looking at notes:**

1. What is the difference between RAM and SSD? Where does MongoDB store data?
2. What command shows you all running processes on a Linux server?
3. What is the difference between `git add` and `git commit`?
4. In Python, what is a dictionary and where does it appear in your job agent system?
5. Why do functions need docstrings in production code?
6. What is error handling and why is it mandatory in a 24/7 system?
7. What is a Python module and why do you organise code into modules?

**Week 1 Mini-Project — Final Submission:**

Your eligibility matcher must:
- Read user profile from `profile.json` (create a realistic one with your actual skills)
- Read a job description from `job.json` (use a real job description you find online)
- Calculate match score as a percentage
- List matching skills
- List missing skills
- Determine if above 70% threshold
- Save full results to `results.json`
- Have proper error handling for missing files
- Have docstrings on all functions
- Be pushed to GitHub with meaningful commit messages
- Have a README explaining what it does and how to run it

**This module will be imported directly into your final system's eligibility matching pipeline.**

---

## WEEK 2 — Python Advanced + HTTP + APIs

> **Where this appears in your system:** The entire backend of your system communicates via HTTP. Your scraper makes HTTP requests. Your Telegram notifications are HTTP requests. Your Groq AI API calls are HTTP requests. Your frontend dashboard talks to your FastAPI backend via HTTP. Understanding HTTP is understanding how every component of your system communicates.

---

### DAY 8 — How the Internet Works — HTTP and APIs

**The mental model:**

The internet is a system of computers communicating using agreed-upon rules called protocols. The most important protocol for you is HTTP — HyperText Transfer Protocol.

Every time you open a website, your browser sends an HTTP request to a server. The server sends back an HTTP response. That's it. Everything on the web is requests and responses.

**An HTTP Request has:**
- A method: GET (read data), POST (send data), PUT (update data), DELETE (remove data)
- A URL: the address of what you're requesting
- Headers: metadata — who you are, what format you accept, authentication tokens
- Body: data you're sending (only for POST and PUT)

**An HTTP Response has:**
- A status code: 200 (success), 404 (not found), 500 (server error), 429 (rate limited — important for your scraper)
- Headers: metadata about the response
- Body: the actual data returned (usually JSON or HTML)

**What an API is:**
API stands for Application Programming Interface. It is a set of URLs a server exposes that other programs can call to get or send data. When your system calls Groq to run the LLM, it sends a POST request to Groq's API. When your system calls the Telegram Bot API to send you a notification, it sends a POST request. When your frontend dashboard reads job data from your FastAPI backend, it sends GET requests.

**Status codes your system must handle:**
- 200: Success — process the response
- 401: Unauthorised — your API key is wrong or expired
- 404: Not found — the job page may have been taken down
- 429: Too many requests — you're being rate limited, wait and retry
- 500: Server error — their server crashed, retry later
- 503: Service unavailable — they're down for maintenance

**Where this appears in your system:**
Every single external tool call — scraping, AI inference, Telegram, email, company research — is an HTTP request. Understanding status codes tells you how to handle every failure scenario.

**Today's Task:**
Install `httpx` (async HTTP library) via pip. Make HTTP requests to:
1. `https://httpbin.org/get` — a test server that shows you what your request looks like
2. `https://api.github.com/users/yourusername` — GitHub's public API showing your profile
3. A company's careers page (pick any company you like)

Print the status code and first 500 characters of the response body. Add error handling for every possible status code.

---

### DAY 9 — Building Your First API with FastAPI

**Why FastAPI for your backend:**
FastAPI is a Python web framework that makes building APIs fast and with minimal code. It automatically generates documentation, handles request validation, supports async operations (crucial for handling multiple scraping jobs simultaneously), and is what many Indian startups and MNCs use.

**What your FastAPI backend does in the system:**
It is the central hub. Your Next.js frontend sends requests to FastAPI. Your Telegram bot sends approval decisions to FastAPI. Your MongoDB Atlas triggers call FastAPI webhooks. Your Playwright automation receives instructions from FastAPI. Everything goes through FastAPI.

**Core concepts:**

An endpoint is a URL that your API exposes. Each endpoint is a Python function decorated with `@app.get()`, `@app.post()`, etc.

Request validation using Pydantic ensures data coming into your API is in the correct format. If your frontend sends a job URL without the `http://` prefix, FastAPI rejects it automatically with a clear error message.

**Your first real API endpoint:**
This is the endpoint that receives a pasted WhatsApp message:

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI(title="Job Agent API", version="1.0.0")

class WhatsAppPaste(BaseModel):
    raw_text: str
    source_group: str = "unknown"

@app.post("/jobs/from-whatsapp")
async def process_whatsapp_paste(paste: WhatsAppPaste):
    """
    Receive a pasted WhatsApp job message and trigger the full analysis pipeline.
    """
    # This will eventually call the orchestrator
    extracted = extract_job_from_text(paste.raw_text)
    return {
        "status": "processing",
        "extracted_company": extracted.get("company"),
        "job_title": extracted.get("role"),
        "message": "Full analysis triggered"
    }
```

**Today's Task:**
Build a FastAPI application with these endpoints:
1. `GET /health` — returns `{"status": "healthy"}` — used to verify the server is running
2. `GET /jobs` — returns a list of jobs from a hardcoded list for now
3. `POST /jobs/from-whatsapp` — receives WhatsApp paste text, returns extracted data
4. `GET /profile` — returns your profile from `profile.json`

Run it with `uvicorn main:app --reload`, open `http://localhost:8000/docs` — you get automatic interactive API documentation. This is the MNC standard.

**Mini-Project Assignment 2 (Days 9-10):**
Extend this API to also have a `POST /jobs/match` endpoint that takes a job description text, loads your profile, runs your Week 1 eligibility matcher, and returns the match score with reasoning. This endpoint will be called by your frontend dashboard.

---

### DAY 10 — Async Python — Why It Matters for Your System

**The problem without async:**
Your system monitors 50 company career pages. Without async, it checks them one by one — 50 pages × 3 seconds each = 2.5 minutes every check. With async, all 50 pages are requested simultaneously — total time is roughly 3 seconds.

**What async actually means:**
Async means your program can start a task, wait for a slow operation (network request, database query), and while waiting, start other tasks instead of sitting idle. The event loop manages all these tasks.

**Where async appears in your system:**
- Scraping 50 company pages simultaneously
- Running 6 debate agents in parallel
- Handling multiple API requests to your FastAPI server simultaneously
- Monitoring IMAP email while also running the eligibility matcher

**The key syntax:**
```python
import asyncio
import httpx

async def scrape_single_company(client, company_url):
    """Scrape one company careers page asynchronously."""
    try:
        response = await client.get(company_url, timeout=10)
        return {"url": company_url, "html": response.text, "status": "success"}
    except Exception as e:
        return {"url": company_url, "error": str(e), "status": "failed"}

async def scrape_all_companies(company_urls):
    """Scrape all companies simultaneously."""
    async with httpx.AsyncClient() as client:
        tasks = [scrape_single_company(client, url) for url in company_urls]
        results = await asyncio.gather(*tasks)
    return results
```

`await` means "start this, and while waiting for it, let other tasks run." `asyncio.gather` means "run all these tasks at the same time."

**Today's Task:**
Convert your company scraper from synchronous to async. Test with a list of 5 real company career page URLs. Measure the time difference between sequential and async. Record this in your documentation — this is the kind of performance understanding MNC engineers demonstrate.

---

### DAY 11 — Environment Variables and Configuration Management

**Why this is a security-critical topic:**
Your system will have API keys — Telegram Bot token, Groq API key, MongoDB connection string with password, your email credentials. If these are hardcoded in your Python files and you push to GitHub, they are exposed to the entire internet. This has caused massive data breaches at real companies.

**The solution — environment variables:**
Environment variables are values set at the operating system level, not inside your code. Your code reads them at runtime. They are never committed to Git.

**Your `.env` file (never committed to GitHub):**
```
MONGODB_URI=mongodb+srv://username:password@cluster.mongodb.net/job_agent
GROQ_API_KEY=gsk_your_actual_key_here
TELEGRAM_BOT_TOKEN=1234567890:your_actual_token_here
EMAIL_PASSWORD=your_actual_email_password
OLLAMA_HOST=http://localhost:11434
```

**Your `.gitignore` file (committed to GitHub — tells Git what to ignore):**
```
.env
__pycache__/
*.pyc
*.pdf
node_modules/
.next/
```

**Reading environment variables in Python:**
```python
import os
from dotenv import load_dotenv

load_dotenv()  # reads .env file and loads variables into environment

MONGODB_URI = os.getenv("MONGODB_URI")
GROQ_API_KEY = os.getenv("GROQ_API_KEY")

if not MONGODB_URI:
    raise ValueError("MONGODB_URI environment variable is not set")
```

The `raise ValueError` line is important — if a critical configuration is missing, the system should tell you immediately at startup, not fail mysteriously later during operation.

**Today's Task:**
1. Add a `.gitignore` file to your project
2. Create a `.env` file with placeholder values (you'll fill real values later)
3. Create a `.env.example` file with the same keys but empty values — this goes to GitHub so others know what variables they need
4. Create a `config.py` module that loads all environment variables and validates they exist
5. Push to GitHub — verify the `.env` file is NOT included

---

### DAY 12 — MongoDB Basics — Your Only Database

**The mental model — why MongoDB instead of SQL:**

In a SQL database like MySQL, you define a rigid table schema before storing any data. Every job posting must have exactly the same fields. If a new job portal has a field you didn't plan for, you have to alter your entire table structure.

MongoDB stores documents — JSON-like objects. Each document can have different fields. A Naukri job posting has different fields than a Greenhouse job posting. MongoDB handles both in the same collection without any schema changes.

More importantly for your system: MongoDB Atlas stores your documents AND your vector embeddings AND runs full-text search AND supports graph-like relationship queries — all in one database. You would need four separate systems to replicate this.

**Core MongoDB concepts:**

A database is the top-level container — you have one database called `job_agent`.

A collection is like a table — you have `jobs`, `projects`, `users`, `companies`, `applications`, `resumes` collections.

A document is one record — one job posting, one project, one application.

A field is one key-value pair inside a document.

**The six collections your system uses — and their purpose:**

`users` — Your profile. One document. Stores your skills, experience, education, contact details, preferred roles, preferred locations, notice period, expected salary. This is what every tool reads to personalise its output.

`skills` — Each skill is its own document with name, category, and your proficiency level. Skills are separate from your profile so they can be queried across projects and jobs independently.

`projects` — Each project you've built is one document. Includes title, description, tech stack, achievements, GitHub link, deploy link, and the vector embedding of its combined text.

`jobs` — Every job the system finds goes here. The raw description, the structured extracted data (required skills, preferred skills, keywords), the match score, the embedding, the status, and which company it's from.

`applications` — Each application you submit. Links to a job document. Stores which resume version was used, date applied, current status, recruiter name if detected, all email communications.

`resumes` — Every generated resume. Links to the job it was made for. Stores which projects were included, which keywords were injected, the file path to the PDF, and the debate verdict that led to improvements.

**Today's Task:**
1. Create a free MongoDB Atlas account at mongodb.com/atlas
2. Create a cluster (free M0 tier)
3. Create a database called `job_agent`
4. Create the six collections
5. Manually insert your profile as a document in the `users` collection using the Atlas web interface
6. Manually insert two of your projects into the `projects` collection
7. Install `pymongo` and `motor` (async MongoDB driver) in Python
8. Write a Python script that connects to Atlas and reads your profile

---

### DAY 13 — MongoDB CRUD from Python

**Where this appears in your system:**
Every single operation — saving a scraped job, updating an application status, reading your profile, storing a generated resume path — is a MongoDB CRUD operation. This is the most frequently used code in your entire system.

**Create — inserting new documents:**
When the scraper finds a new job, it creates a document:
```python
new_job = {
    "title": "Backend Engineer",
    "company": "Stripe",
    "jd_text": "We are looking for...",
    "required_skills": ["Python", "AWS"],
    "source": "scraped",
    "match_score": 0,
    "status": "new",
    "scraped_at": datetime.utcnow()
}
job_id = await jobs_collection.insert_one(new_job)
```

**Read — finding documents:**
When building the dashboard, you read all jobs above a match threshold:
```python
# Find all shortlisted jobs, sorted by match score descending
shortlisted = await jobs_collection.find(
    {"match_score": {"$gte": 70}, "status": "new"},
    sort=[("match_score", -1)]
).to_list(length=50)
```

**Update — modifying existing documents:**
When Playwright submits an application, the status updates:
```python
await applications_collection.update_one(
    {"_id": application_id},
    {"$set": {
        "status": "applied",
        "applied_at": datetime.utcnow(),
        "submission_screenshot": "screenshots/stripe_backend_2026.png"
    }}
)
```

**Delete — removing documents:**
When a job posting is taken down:
```python
await jobs_collection.delete_one({"_id": job_id})
```

**Today's Task:**
Write a complete `database.py` module with async functions for:
1. `insert_job(job_data)` — inserts a job document, returns the new ID
2. `get_jobs_above_threshold(min_score)` — returns all jobs above a match score
3. `update_job_status(job_id, new_status)` — updates a job's status field
4. `get_user_profile()` — returns the single user document
5. `insert_application(application_data)` — creates a new application record

All functions must have error handling and docstrings. This becomes the core database layer of your production system.

---

### DAY 13B — Weighted Multi-Dimensional Eligibility Scoring

> **Gap fixed:** The basic matcher from Day 5 calculates a flat percentage of matched skills. That is not how real ATS systems or recruiters score candidates. A job at 65% because you are in the wrong city is very different from a job at 65% because you are missing the core required programming language. This day builds the production-grade weighted scorer.

**Why weighted scoring matters:**
Two candidates can both score 70% on a simple skill overlap calculation but be completely different fits. Weighted scoring assigns different importance to different dimensions — skill overlap is not the only factor. Experience level, location fit, seniority match, role alignment, and ATS keyword coverage all contribute with different weights.

**The five scoring dimensions:**

Skill overlap (40 points maximum) — how many of the required skills you have, weighted by whether each skill is mandatory or preferred. A mandatory Python skill you lack costs more than a preferred Kubernetes skill you lack.

Experience level match (25 points maximum) — does the job ask for 3-5 years and you have 2? That is a partial match. Does it ask for 5+ and you have 2? That is a hard mismatch flagged separately.

Location fit (15 points maximum) — remote roles score full points regardless of your location. Jobs in your city score full points. Jobs in another city score partial points. Jobs requiring relocation with no allowance score zero.

Role type alignment (15 points maximum) — a backend Python job matched against a frontend React specialist scores low here even if skill overlap is decent. The LLM parser identifies role type from the JD and compares it against your declared preferred roles.

ATS keyword coverage (5 points maximum) — what percentage of the JD's identified ATS keywords appear in your current profile documents. This is a bonus signal, not a primary one.

**The near-match vs hard-mismatch classification:**
After calculating the total weighted score, the system classifies each job into one of three bands — not just above or below a threshold.

Strong match (80 and above): proceed immediately through the full pipeline. Generate resume, run debate, prepare for application.

Near match (60 to 79): flag separately with the specific dimension pulling the score down. If it is location only, that is fixable — you can indicate relocation willingness. If it is a missing core skill, flag the exact skill and ask if you want to proceed anyway or skip. Do not silently filter these out.

Hard mismatch (below 60): skip silently. Log the reason. Aggregate these weekly to find patterns in what roles you are systematically missing — this feeds the skill gap learning tracker.

**The gap category classifier:**
When a job falls below threshold, the system does not just record the score. It records which specific dimension failed and why. Examples: "Location mismatch — job requires on-site Mumbai, your preference is remote." "Seniority mismatch — job requires 7 years, your profile shows 2 years." "Core skill missing — Python is mandatory, not in your profile." These categorised gaps are stored in MongoDB and surface in your weekly analytics.

**Today's Task:**
Replace your Week 1 simple percentage matcher with the weighted five-dimension scorer. Test it against 10 real job descriptions. For each, verify the score feels accurate — a job that intuitively feels like a great fit should score 80 or above. Adjust dimension weights until results feel right. Document your final weight choices and the reasoning behind them. This calibration is real data science work.

**Mini-Project Extension:**
Update your `POST /jobs/match` FastAPI endpoint to return not just a score but the full breakdown: score per dimension, which dimension is lowest, classification (strong/near/hard mismatch), and the gap reason if below threshold.

---

### DAY 14 — WEEK 2 REVIEW + MINI-PROJECT SUBMISSION

**Week 2 Concept Review:**
1. What is the difference between GET and POST HTTP methods?
2. What does status code 429 mean and how should your system handle it?
3. Why must you never commit a `.env` file to GitHub?
4. What is the difference between synchronous and async code? Give a real example from your system.
5. What is a MongoDB collection? How is it different from a SQL table?
6. Why does your system use one MongoDB cluster instead of four separate databases?

**Week 2 Mini-Project — Job Data Pipeline:**

Build a Python system that:
1. Reads a list of job descriptions from a JSON file (create 5 realistic ones)
2. For each job, calculates match score against your profile (use Week 1 module)
3. Saves all jobs with match scores to MongoDB
4. Provides a FastAPI endpoint `GET /jobs/shortlisted` that returns jobs above 70%
5. Provides a FastAPI endpoint `POST /jobs` that accepts a new job and calculates its score
6. All database operations are async
7. Environment variables used for MongoDB connection
8. Proper error handling throughout
9. README documentation explaining every endpoint

**This is now the core of your job ingestion pipeline. It is production-ready code.**

---

## WEEK 3 — Web Scraping and Data Extraction

> **Where this appears in your system:** The scraper is what gives your system eyes. Without it, you manually find every job. The scraper finds jobs while you sleep.

---

### DAY 15 — How Websites Work — HTML and the DOM

**The mental model:**
Every webpage is an HTML document — a structured text file that your browser renders visually. The browser reads the HTML and builds a tree of elements called the DOM — Document Object Model. When your scraper fetches a webpage, it gets this HTML text and must parse it to extract the information you need.

**HTML structure:**
```html
<div class="job-listing">
    <h2 class="job-title">Backend Engineer</h2>
    <span class="company-name">Stripe</span>
    <p class="job-description">We are looking for...</p>
    <a href="/apply/12345" class="apply-button">Apply Now</a>
</div>
```

Your scraper must look at this HTML and extract: the title from the `h2` element, the company from the `span`, the description from the `p`, and the application link from the `a` element.

**Why this matters for each type of website your system handles:**
- Simple career pages use plain HTML — BeautifulSoup handles these easily
- Modern career pages use JavaScript to load job listings dynamically — Playwright is needed because it actually runs the JavaScript
- Known ATS platforms like Greenhouse have consistent HTML structures — your adapter knows exactly which elements to look for

**Today's Task:**
Install `beautifulsoup4` and `lxml`. Write a script that fetches the HTML of any company's public careers page and prints all text content. Identify which HTML elements contain the job titles, descriptions, and apply links.

---

### DAY 16 — BeautifulSoup — Parsing HTML

**Practical scraping of static pages:**

```python
import httpx
from bs4 import BeautifulSoup

async def extract_jobs_from_html(html_content, company_name):
    """
    Extract job listings from HTML content.
    Works for simple HTML career pages.
    """
    soup = BeautifulSoup(html_content, "lxml")
    jobs = []

    # Find all job listing containers
    # Note: class names vary per site — this requires inspection
    job_elements = soup.find_all("div", class_="job-card")

    for element in job_elements:
        title_elem = element.find("h2") or element.find("h3")
        link_elem = element.find("a")

        if title_elem:
            jobs.append({
                "title": title_elem.get_text(strip=True),
                "company": company_name,
                "apply_url": link_elem.get("href") if link_elem else None,
                "raw_html": str(element)
            })

    return jobs
```

**The key skill — inspecting real pages:**
Open any company career page in Chrome. Right-click on a job title → Inspect. The browser shows you the HTML element. You can see its class name, parent elements, sibling elements. This is how you write site-specific scrapers.

**Today's Task:**
Write a scraper for one real company's career page. Use Chrome's inspector to find the right HTML elements. Extract at least the job title and application URL for each listing. Store results in MongoDB using your Day 13 database module.

---

### DAY 17 — Playwright — Browser Automation for JavaScript Pages

**Why Playwright is needed:**
Most modern career pages use JavaScript frameworks like React or Vue to load job listings dynamically. When your scraper fetches the raw HTML, the job listings section is empty — just a `<div id="jobs-container"></div>`. The actual jobs load only after JavaScript runs in a real browser.

Playwright actually opens a Chrome browser, waits for JavaScript to execute, and gives you the final rendered HTML with all job listings loaded.

**Where Playwright appears in your system:**
- Scraping JavaScript-heavy career pages
- Filling application forms — clicking, typing, uploading files
- Taking screenshots for submission evidence
- Monitoring form fields and detecting CAPTCHAs
- Session cookie management

**The anti-detection layer — why each measure exists:**

`playwright-stealth` patches Chrome's JavaScript environment so websites can't detect that the browser is controlled by automation. Without this, sites like LinkedIn and Naukri immediately detect and block the session.

Random delays between actions simulate human reading and thinking time. A human doesn't instantly move to the next field — they read the label, think, then type. Your automation does the same.

Randomised typing speed simulates human keyboard input. Humans don't type at a perfectly constant speed.

**Session warmup** — before any form filling, the browser visits the company homepage and stays for 30 to 60 seconds, scrolling and moving the mouse randomly. This creates a browsing history in the session that makes the visit look legitimate.

**Today's Task:**
Install Playwright: `pip install playwright && playwright install chromium`. Write an async Playwright script that opens a career page, waits for job listings to load, extracts 3 job titles, and saves a screenshot. This is the foundation of your scraping module for JavaScript pages.

---

### DAY 18 — python-jobspy — Scraping Major Job Boards

**Why use this library:**
python-jobspy is an open-source library that wraps Indeed, LinkedIn, Glassdoor, ZipRecruiter, and Google Jobs in a single Python call. Instead of building individual scrapers for each board, one function call returns structured job data from all of them simultaneously.

**Where this appears in your system:**
Your morning and evening scraping cycles start with python-jobspy for mass job discovery across all major boards, then run your Playwright scraper for company-specific career pages not covered by the major boards.

**Using it:**
```python
from jobspy import scrape_jobs

jobs = scrape_jobs(
    site_name=["linkedin", "indeed", "glassdoor", "naukri"],
    search_term="backend engineer python",
    location="Bangalore",
    results_wanted=50,
    hours_old=24  # only jobs posted in last 24 hours
)
```

Returns a pandas DataFrame with standardised columns: title, company, location, description, job_url, date_posted.

**Today's Task:**
Run python-jobspy for a role you want to apply to. Process the results — run your eligibility matcher on each job, filter to those above 70%, save shortlisted jobs to MongoDB with proper status fields. Log how many jobs were found, how many were shortlisted, and why each rejected job was below threshold.

---

### DAY 19 — Deduplication and the Hash System

**The problem:**
The same job posting appears on LinkedIn, Indeed, Naukri, and the company's own career page. Without deduplication, your system processes the same job four times, generates four resumes, and sends you four notifications for one job.

**The solution — content hashing:**
A hash is a fixed-length string produced by running a value through a mathematical function. The same input always produces the same hash. Different inputs produce different hashes. You hash the combination of company name + job title + approximate posting date. If this hash already exists in your `seen_jobs` MongoDB collection, skip it.

```python
import hashlib

def generate_job_hash(company, title, posting_date):
    """
    Generate a unique fingerprint for a job to detect duplicates.
    Same job from different sources will produce the same hash.
    """
    content = f"{company.lower().strip()}{title.lower().strip()}{posting_date}"
    return hashlib.md5(content.encode()).hexdigest()
```

You store this hash as a unique-indexed field in MongoDB. If you try to insert a job with an existing hash, MongoDB rejects it automatically.

**The page change hash:**
For continuous monitoring of career pages, you hash the entire page content every 30 minutes. If the hash changes, the page changed — possibly new jobs posted. Only then does the full Playwright scraper run. This prevents 50 full browser sessions every 30 minutes.

**Today's Task:**
Add hash-based deduplication to your scraper. Run the scraper against the same five company pages twice and verify the second run produces zero new MongoDB inserts.

---

### DAY 20 — Rate Limiting and Respectful Scraping

**The ethical and practical dimensions:**
Aggressive scraping can crash small company websites, get your IP permanently banned, and in extreme cases violate terms of service. Your system scrapes responsibly — it spaces requests, respects rate limits, and backs off when told to.

**Implementing rate limiting in your system:**
- Minimum 2 seconds between requests to the same domain
- If you receive a 429 response, wait the time specified in the `Retry-After` header, then retry
- Maximum 3 retries per page before giving up and logging a failure
- Never more than 10 concurrent requests to different domains simultaneously
- Always include a realistic User-Agent header

**The exponential backoff pattern:**
When a request fails, wait 1 second, retry. If it fails again, wait 2 seconds, retry. If it fails again, wait 4 seconds, retry. This is the industry-standard retry pattern.

**Today's Task:**
Add rate limiting and exponential backoff to your scraper module. Test it against a real site by intentionally sending too many requests and verifying your system handles the 429 response correctly.

**Week 3 Mini-Project Assignment:**
Build the complete job discovery pipeline:
1. python-jobspy scrapes major boards for your target roles
2. Playwright scrapes 3 specific company career pages you care about
3. Deduplication using hash system
4. All jobs saved to MongoDB with proper status
5. FastAPI endpoint `GET /jobs/new` returns jobs found in last 24 hours
6. Rate limiting and retry logic throughout
7. Error logging to a file
8. README and Git commits throughout

---

## WEEK 4 — Local AI Models, Embeddings, and Vector Search

> **Where this appears in your system:** This is the intelligence layer. Without AI, your system is just a scraper. With AI, it understands job descriptions, matches meaning not just keywords, and generates tailored content.

---

### DAY 21 — Installing and Using Ollama

**What Ollama is:**
Ollama is an application that manages local AI model downloads and runs them as a local server on your machine. You call it exactly like a cloud API — send text, receive response — but everything runs locally on your hardware with zero cost and complete privacy.

**Why local models for your system:**
Your system processes your resume, your projects, your personal contact details. Sending this to OpenAI means their servers see all your personal career data. Local models keep everything on your machine.

**Setting up Ollama:**
1. Download from ollama.com and install
2. Open terminal: `ollama pull llama3.2` — downloads the 8B model (about 5GB)
3. `ollama pull nomic-embed-text` — downloads the embedding model
4. `ollama serve` — starts the local API server on port 11434

**Calling Ollama from Python:**
```python
import httpx
import json

async def call_local_llm(prompt, system_prompt=""):
    """
    Call the local Ollama LLM and return its response.
    This is the foundation of all AI features in your system.
    """
    async with httpx.AsyncClient(timeout=120) as client:
        response = await client.post(
            "http://localhost:11434/api/generate",
            json={
                "model": "llama3.2",
                "prompt": prompt,
                "system": system_prompt,
                "stream": False
            }
        )
        return response.json()["response"]
```

**Today's Task:**
1. Install Ollama and download `llama3.2` and `nomic-embed-text`
2. Call the LLM with a job description and ask it to extract required skills as a JSON list
3. Verify the output is valid JSON
4. Add error handling for when Ollama is not running

---

### DAY 21B — IP Rotation and Proxy Pool Management

> **Gap fixed:** IP rotation was listed in Section 7 of the feature specification as critical for large-scale company monitoring but was completely absent from the roadmap. This day teaches the concept, when you actually need it, and how to implement it at personal scale.

**When you actually need IP rotation:**
For personal use monitoring 20 to 30 companies twice daily, you will almost never need IP rotation. Your requests are spread across many different domains at low frequency — the same natural pattern as a real human browsing the web for jobs. IP bans happen when you hammer one domain with dozens of requests per minute, which your system never does.

You need IP rotation in one specific scenario: if a major job board like LinkedIn or Naukri bans your IP after detecting unusual activity. This is rare with proper delays and stealth settings but can happen.

**Understanding how IP banning works:**
A website's server sees your IP address with every request. If the same IP makes 50 requests to the same URL in 5 minutes, it gets flagged. The ban can be temporary (30 minutes to 24 hours) or permanent. Most temporary bans clear by the next morning. A permanent ban can be cleared by contacting your ISP for a new IP or using a proxy.

**The proxy options — from simplest to most robust:**

Your home router's dynamic IP: most home internet connections get a new IP address every time you restart the router or every 24 to 48 hours automatically. For personal use, this is often sufficient. If you get banned by a site, restart your router and wait 10 minutes.

Free proxy lists: lists of IP addresses that act as intermediaries. Your request goes to the proxy, the proxy forwards it to the target site. The target site sees the proxy's IP. These are unreliable — most free proxies are slow, down frequently, and many are already banned by major sites. Do not use for production.

Residential proxies: IP addresses assigned to real home internet connections, provided by services like Bright Data, Oxylabs, or Smartproxy. Sites cannot distinguish these from real users. Expensive at scale but available in entry packages for $10 to $15 per month. For personal job hunting, this is the reliable option if you need rotation.

**The proxy pool manager:**
Rather than picking a random proxy for every request, a pool manager tracks which proxies are healthy, which are rate-limited on which domains, and rotates them intelligently.

The manager maintains a list of proxy addresses in MongoDB. Each document has: the proxy URL, its current health status (healthy, rate-limited, banned), the domain it was last rate-limited on, and the timestamp of the last health check. Before any scraping request, the manager selects the best available proxy for that specific domain — one that has not been rate-limited on that domain recently.

After each request, the manager records the response status. A 429 on a specific proxy-domain combination temporarily marks that proxy as rate-limited for that domain. Three consecutive failures mark the proxy as unhealthy and removes it from rotation until a background health check re-validates it.

**The practical setup for personal scale:**
Add a `proxies` collection to MongoDB with a field for the proxy URL and a field for your home IP (no proxy). In your scraper, add an optional `use_proxy` parameter. During normal operation, it is False — direct connection. If you receive a 429 response three times in a row on any domain, it automatically sets `use_proxy` to True for that domain for the next 4 hours.

This lazy approach means you never pay for proxies unless you actually need them, and when you do need them, the system switches automatically.

**Today's Task:**
1. Add a `proxies` MongoDB collection with two test documents — your direct connection and one free proxy from a public list (for testing structure only, not actual use)
2. Write `automation/proxy_manager.py` with: `get_best_proxy(domain)`, `mark_rate_limited(proxy_url, domain)`, `mark_healthy(proxy_url)`, `get_pool_status()` (returns health summary for the dashboard)
3. Wrap your scraper's request function with an optional proxy parameter
4. Add the proxy pool status to your dashboard as a small status widget
5. Test by simulating rate limit responses and verifying the manager correctly marks proxies and selects alternatives

---

### DAY 22 — Embeddings and Vector Search — The AI Memory

**The concept — again, deeply:**
When you store a project description in MongoDB as text, the only way to find relevant projects is keyword matching. "I built a payment system using Stripe" would not match a job asking for "billing and transaction processing experience" — different words, same meaning.

Embeddings convert text to a list of numbers (a vector) that represents the meaning. Similar meanings produce similar number lists. Vector search finds documents whose number lists are most similar — matching meaning, not keywords.

**Your embedding model — nomic-embed-text:**
It converts any text into 768 numbers. You generate embeddings for:
- Every project description (done once at setup)
- Every job description (done when a new job is scraped)

Then to find which projects are most relevant to a job, you compute which project embeddings are closest to the job embedding.

**Generating embeddings:**
```python
async def generate_embedding(text):
    """
    Generate a vector embedding for a piece of text.
    Used to enable semantic search between jobs and projects.
    """
    async with httpx.AsyncClient() as client:
        response = await client.post(
            "http://localhost:11434/api/embeddings",
            json={"model": "nomic-embed-text", "prompt": text}
        )
        return response.json()["embedding"]  # list of 768 floats
```

**Storing embeddings in MongoDB:**
When you insert a project, generate its embedding and store it alongside the text:
```python
project["embedding"] = await generate_embedding(
    project["title"] + " " + project["description"] + " " + " ".join(project["tech_stack"])
)
await projects_collection.insert_one(project)
```

**Today's Task:**
Generate embeddings for all your projects and update their MongoDB documents to include the embedding field. Write a function that takes a job description, generates its embedding, and manually computes cosine similarity against your project embeddings. Return the top 3 most similar projects. This is your project matcher before the Atlas Vector Search index.

---

### DAY 23 — MongoDB Atlas Vector Search Setup

**Setting up the vector index:**
In MongoDB Atlas web interface:
1. Go to your cluster → Search → Create Index
2. Choose "Vector Search"
3. Select your `projects` collection
4. Define the index on the `embedding` field, 768 dimensions, cosine similarity
5. Name it `project_embeddings_index`

Now MongoDB handles the nearest-neighbour search natively.

**The vector search query:**
```python
async def find_matching_projects(job_embedding, top_k=3):
    """
    Find the top K projects most relevant to a job description.
    Uses MongoDB Atlas Vector Search — semantic similarity, not keyword matching.
    """
    pipeline = [
        {
            "$vectorSearch": {
                "index": "project_embeddings_index",
                "path": "embedding",
                "queryVector": job_embedding,
                "numCandidates": 20,
                "limit": top_k
            }
        },
        {
            "$project": {
                "title": 1,
                "description": 1,
                "tech_stack": 1,
                "achievements": 1,
                "github_url": 1,
                "score": {"$meta": "vectorSearchScore"}
            }
        }
    ]
    results = await projects_collection.aggregate(pipeline).to_list(length=top_k)
    return results
```

**Today's Task:**
Set up the vector search index. Run the query against three different job descriptions and verify the results make intuitive sense — the projects returned should genuinely be the most relevant to each job description. If they don't make sense, the problem is usually in how you concatenated text before embedding — experiment.

---

### DAY 24 — LLM-Powered Job Description Parser

**What the JD parser does:**
A raw job description is unstructured text. Your system needs structured data — a list of required skills, a list of preferred skills, seniority level, ATS keywords, action verbs the job uses, soft skills mentioned. The LLM reads the raw text and extracts this structure.

**The prompt engineering:**
This is the most important skill in AI development — how you phrase the instruction to the LLM determines the quality of its output.

```python
async def parse_job_description(jd_text):
    """
    Extract structured data from a raw job description using the local LLM.
    Returns a dictionary with required_skills, preferred_skills, keywords, etc.
    """
    system_prompt = """You are an expert HR analyst and ATS system specialist.
    Extract structured information from job descriptions.
    Always respond with valid JSON only. No explanation, no preamble, no markdown code blocks.
    Just the raw JSON object."""

    user_prompt = f"""Extract the following from this job description and return as JSON:
    {{
        "required_skills": ["list of hard required technical skills"],
        "preferred_skills": ["list of nice-to-have skills"],
        "seniority_level": "junior/mid/senior/lead",
        "ats_keywords": ["specific technical keywords and acronyms to include in resume"],
        "action_verbs": ["strong action verbs used in the JD"],
        "soft_skills": ["interpersonal and behavioural skills mentioned"],
        "role_type": "backend/frontend/fullstack/data/devops/ml",
        "domain": "fintech/ecommerce/saas/healthcare/etc"
    }}

    Job Description:
    {jd_text}"""

    response = await call_local_llm(user_prompt, system_prompt)

    try:
        return json.loads(response)
    except json.JSONDecodeError:
        # LLM sometimes adds text before or after JSON — extract it
        import re
        json_match = re.search(r'\{.*\}', response, re.DOTALL)
        if json_match:
            return json.loads(json_match.group())
        raise ValueError(f"LLM did not return valid JSON: {response[:200]}")
```

**Today's Task:**
Test this parser on 5 real job descriptions from different companies and role types. For each, manually verify the extracted skills are accurate. Adjust the prompt if results are wrong. This fine-tuning of prompts is a core skill — it is called prompt engineering.

---

### DAY 25 — GraphRAG with MongoDB $graphLookup

**What GraphRAG adds beyond vector search:**
Vector search answers: "which of my projects are similar to this job?"
GraphRAG answers: "which skills does this job require → which of those skills do my projects demonstrate → which projects directly prove I can do this specific job → which required skills have zero project evidence?"

The second answer is more useful for resume building.

**The MongoDB GraphRAG query:**
```python
async def find_projects_for_job_via_graph(job_skills):
    """
    Use graph traversal to find projects that directly demonstrate
    the skills required by the job. More precise than pure vector search.
    """
    pipeline = [
        # Start with the required skills
        {"$match": {"name": {"$in": job_skills}}},
        # Traverse from skill → projects that use this skill
        {
            "$graphLookup": {
                "from": "projects",
                "startWith": "$name",
                "connectFromField": "name",
                "connectToField": "tech_stack",
                "as": "demonstrating_projects",
                "maxDepth": 2
            }
        }
    ]
    results = await skills_collection.aggregate(pipeline).to_list(length=100)
    return results
```

**Today's Task:**
Implement both approaches — vector search and GraphRAG — for project-to-job matching. Build a combined scoring function that uses both results to rank your projects for a given job. Document which approach found better matches and why.

**Week 4 Mini-Project Assignment:**
The Complete Intelligence Module:
1. JD parser — extracts structured data from any job description text
2. Project matcher — combines vector search and graph traversal to find your top 3 projects
3. Skill gap detector — identifies which required skills you have and which you're missing
4. All results stored to MongoDB
5. FastAPI endpoint `POST /jobs/analyse` that takes a job description and returns full analysis
6. Tested with 5 different real job descriptions

---

# PART 2 — PHASE 2: CORE SYSTEM MODULES
## Weeks 5 through 8 — Building Each System Component

---

## WEEK 5 — Resume Generation System

> **Where this appears in your system:** The resume generator is what turns intelligence into action. The JD parser found keywords. The project matcher found relevant projects. The resume generator combines these into a tailored, ATS-optimised PDF.

---

### DAY 26 — LaTeX Fundamentals

**Why LaTeX instead of Word or HTML:**
LaTeX produces the highest quality PDFs with precise typographic control. Every element is explicitly positioned. The output is consistent regardless of operating system or rendering environment. Most importantly, a properly structured LaTeX resume is parsed perfectly by every ATS system — no hidden formatting, no images embedded in text, no table-based layouts that confuse parsers.

**LaTeX is a markup language** — you write text with commands, and the compiler produces a PDF.

```latex
\documentclass{article}

\begin{document}

\section{Skills}
\textbf{Languages:} Python, JavaScript, SQL \\
\textbf{Frameworks:} FastAPI, React, Next.js \\
\textbf{Databases:} MongoDB, PostgreSQL

\section{Projects}
\textbf{E-commerce Platform} | React, Node.js, MongoDB \\
Built a full-stack e-commerce system handling 10,000 daily transactions.
Implemented real-time inventory management reducing stockouts by 40\%.

\end{document}
```

Compile with: `pdflatex resume.tex` → produces `resume.pdf`

**Today's Task:**
Install LaTeX: `sudo apt-get install texlive-full` (Linux) or download MacTeX (Mac). Write a complete resume in LaTeX for yourself. Compile it. This is your base template.

---

### DAY 27 — Jinja2 Template Engine

**What Jinja2 does:**
Jinja2 is a template engine — it takes a template file with placeholders and fills in real values from your Python data. Your LaTeX resume template has placeholders like `{{ candidate_name }}` and `{{ skills_list }}`. Jinja2 fills these from your MongoDB profile and the job analysis results.

**Your LaTeX template with Jinja2 placeholders:**
```latex
\section{Professional Summary}
{{ professional_summary }}

\section{Technical Skills}
{% for category, skills in skill_categories.items() %}
\textbf{ {{ category }} :} {{ skills | join(', ') }} \\
{% endfor %}

\section{Projects}
{% for project in selected_projects %}
\textbf{ {{ project.title }} } | {{ project.tech_stack | join(', ') }} \\
{% for bullet in project.bullets %}
{{ bullet }} \\
{% endfor %}
{% endfor %}
```

**The keyword injection process:**
1. Vector search + GraphRAG identify top 3 projects
2. LLM reads each project's description + the JD's required keywords
3. LLM rewrites the project bullets to naturally include missing keywords
4. Jinja2 fills these rewritten bullets into the LaTeX template
5. pdflatex compiles to PDF

**Today's Task:**
Create a Jinja2 LaTeX template for your resume. Write a Python function that takes your MongoDB profile, a list of selected projects with rewritten bullets, and a skills list, and renders the complete LaTeX file. Then compiles it to PDF using `subprocess.run(["pdflatex", "resume.tex"])`.

---

### DAY 27B — Multiple Resume Templates and the Template Selector

> **Gap fixed:** The previous day built one LaTeX template. In the real system, a frontend engineer applying to a React role and a backend engineer applying to a Python API role need different resume structures — different section order, different skill emphasis, different project framing. Using the same template for both loses points with both ATS systems and recruiters.

**Why four templates, not one:**
ATS systems score resumes partly by how well the structure matches the role type. A frontend resume leading with UI frameworks and performance metrics scores better for frontend roles than one leading with database optimisation work. The template selector is what makes each generated resume feel purpose-built, not generic.

**The four base templates and what makes each different:**

Frontend template: Opens with a UI/UX skills block emphasising JavaScript frameworks, browser performance, accessibility. Projects section leads with visual, user-facing work. Achievements use metrics like Lighthouse scores, load time improvements, user engagement numbers. Avoids backend jargon in the summary.

Backend template: Opens with languages, frameworks, database technologies, and API design. Projects emphasise scale, throughput, system reliability, and data handling. Achievements use throughput numbers, latency improvements, uptime percentages. Summary focuses on system design and API architecture.

Full-stack template: Balanced skills block. Projects show both frontend and backend contributions explicitly. Summary emphasises ability to own an entire feature end to end. Used when the JD mentions ownership, breadth, or startup context.

Data and ML template: Opens with languages (Python, SQL), ML frameworks, data tools (Spark, Airflow, dbt). Projects emphasise dataset size, model accuracy improvements, pipeline throughput. Achievements use statistical metrics and business impact numbers. Summary positions as someone who translates data into decisions.

**The template selector function:**
The JD parser already extracts `role_type` — one of backend, frontend, fullstack, data, devops, ml. The template selector reads this field and returns the path to the appropriate base template file. If the role type is ambiguous or unknown, it defaults to the full-stack template.

```
role_type → "backend"   → templates/backend.tex
role_type → "frontend"  → templates/frontend.tex
role_type → "fullstack" → templates/fullstack.tex
role_type → "data"      → templates/data_ml.tex
role_type → "devops"    → templates/fullstack.tex  (fallback — build devops template in Phase 5)
role_type → "ml"        → templates/data_ml.tex
```

**Template versioning in MongoDB:**
Each template is stored in the `resume_templates` MongoDB collection with a version number and the role type it serves. When you improve a template, you create a new version — the old one is never deleted. This way you can compare which template version produced more interview callbacks over time.

**Today's Task:**
1. Build all four LaTeX base templates, each genuinely different in structure and emphasis
2. Build the template selector function that takes `role_type` and returns the template path
3. Store all four templates in MongoDB `resume_templates` collection with version 1.0
4. Update your resume generator from Day 27 to call the selector before rendering
5. Test by running the full generator against one backend JD and one frontend JD — the two output PDFs must look structurally different
6. Push to GitHub with a commit message explaining the template architecture decision

---

### DAY 28-29 — LLM Keyword Injection

**The prompting strategy for keyword injection:**
This is the most nuanced prompt in your system. You must inject keywords naturally — not stuffed, not forced, not fabricated. The LLM must rewrite existing true statements to use the vocabulary the job description uses.

**The rewriting rules you enforce in the prompt:**
1. Only mention technologies you actually used — no fabrication
2. Add the keyword as a natural part of the sentence — not appended at the end
3. Keep the achievement metrics — the numbers are what impress recruiters
4. Maximum 3 bullets per project — quality over quantity
5. Start every bullet with a strong action verb from the JD's own vocabulary
6. If a required keyword cannot be naturally integrated — do not force it

**Testing quality:**
After generation, run the resume through an ATS simulator (several free ones exist online). Check keyword match percentage before and after. Document the improvement. This becomes your evaluation metric for the resume generator.

**Today's Task:**
Build the complete resume generator:
1. Takes a job_id from MongoDB
2. Reads the parsed JD data (keywords, skills, action verbs)
3. Runs vector search + graph query to get top 3 projects
4. Calls LLM to rewrite project bullets with keyword injection
5. Renders Jinja2 LaTeX template
6. Compiles to PDF
7. Stores PDF path in MongoDB `resumes` collection with version number and job link
8. Returns the PDF file path

**Week 5 Mini-Project:**
Complete resume generation pipeline tested end-to-end:
- Input: a job description text
- Output: a tailored PDF resume stored in MongoDB
- Test with 3 different job descriptions
- Verify each produced resume is unique and genuinely tailored to each JD

---

## WEEK 6 — Browser Automation and Form Filling

> **Where this appears in your system:** This is the action layer. All the intelligence produced in weeks 1-5 culminates here — the system uses what it knows to actually apply for jobs.

---

### DAY 31 — Playwright Deep Dive — Navigation and Element Detection

**Core Playwright concepts:**

A `page` represents one browser tab. You navigate it, interact with it, and read from it.

`await page.goto(url)` — Navigate to a URL and wait for the page to load.

`await page.wait_for_load_state("networkidle")` — Wait until the page has finished all network requests — important for JavaScript-heavy pages that load content after initial page load.

`await page.locator("input[name='email']").fill("your@email.com")` — Find the email input field and type a value.

`await page.get_by_label("Phone number").fill("+91-9876543210")` — Find a field by its visible label — more robust than searching by HTML attribute, closer to how a human reads a form.

`await page.get_by_role("button", name="Submit Application").click()` — Find and click a button by its visible text.

`await page.screenshot(path="submissions/stripe_2026.png")` — Save a screenshot.

**The human simulation layer:**
```python
import random
import asyncio

async def human_type(page, selector, text):
    """Type text character by character with random delays to simulate human typing."""
    await page.click(selector)
    for character in text:
        await page.keyboard.type(character)
        await asyncio.sleep(random.uniform(0.05, 0.15))  # 50-150ms per character

async def human_delay(min_seconds=1, max_seconds=3):
    """Wait a random human-like amount of time between actions."""
    await asyncio.sleep(random.uniform(min_seconds, max_seconds))
```

**Today's Task:**
Write a Playwright script that opens a Google Form (create a test one yourself), fills every field with your profile data, and submits it. Include human-like delays and take a screenshot before submission. This is your foundation for all form automation.

---

### DAY 32 — The Universal Form Detector

**The problem:**
Every website has different HTML for its forms. You cannot hardcode field selectors for every possible site. The AI form detector solves this by reading the form's HTML and figuring out what each field is asking for.

**The approach:**
1. Playwright opens the application page and waits for all content to load
2. Playwright extracts the full HTML of the form section
3. The local LLM reads the HTML and returns a JSON mapping: `{"field_selector": "field_purpose"}`
4. Your system reads your MongoDB profile for each field purpose and fills it
5. Playwright fills each field with the matched profile data

**The field purposes the LLM identifies:**
`full_name`, `email`, `phone`, `linkedin_url`, `github_url`, `portfolio_url`, `resume_upload`, `cover_letter_upload`, `years_of_experience`, `current_company`, `notice_period`, `expected_salary`, `highest_qualification`, `university`, `graduation_year`, `why_this_company` (open-ended), `how_did_you_hear` (dropdown)

**Today's Task:**
Build the universal form detector. Test it on 3 different job application forms — one Google Form you create for testing, one real public application form, one other form. Verify the field detection is accurate.

---

### DAY 33 — Site-Specific Adapters

**Why adapters for known platforms:**
Known platforms like Greenhouse and Lever have consistent HTML. Writing a Greenhouse adapter means it works for every company using Greenhouse — Stripe, Airbnb, Coinbase, and thousands of others. The adapter is more reliable than the universal detector because it uses known selectors.

**Adapter architecture:**
Each adapter is a Python class with a standard interface:
```python
class GreenhouseAdapter:
    """
    Handles job applications on Greenhouse-based career sites.
    Covers thousands of companies including most funded startups.
    """

    PLATFORM_SIGNATURES = ["greenhouse.io", "boards.greenhouse.io"]

    async def detect(self, url):
        """Returns True if this URL uses the Greenhouse platform."""
        return any(sig in url for sig in self.PLATFORM_SIGNATURES)

    async def fill_application(self, page, profile):
        """Fill a Greenhouse application form with user profile data."""
        # Greenhouse-specific selectors
        await page.locator("#first_name").fill(profile["first_name"])
        await page.locator("#last_name").fill(profile["last_name"])
        await page.locator("#email").fill(profile["email"])
        await page.locator("#phone").fill(profile["phone"])
        # ... all other standard Greenhouse fields

    async def upload_resume(self, page, resume_path):
        """Upload the generated resume PDF."""
        await page.locator("input[type='file']").set_input_files(resume_path)
```

**Today's Task:**
Build adapters for Google Forms and for one other platform you research. Document the HTML structure of each platform. This is genuine reverse engineering research.

---

### DAY 34-35 — Session Management and Cookie Storage

**Why session management:**
Naukri requires login. Some LinkedIn applications require login. Every time your system opens a browser, it should already be logged in — not re-enter credentials every time, which would be flagged immediately.

**The approach:**
The first time you log into a site, Playwright captures the browser's cookies after login and stores them in MongoDB as an encrypted document. Next time the system visits that site, it loads these cookies before navigating — the site sees an already-authenticated session.

**Cookie storage in MongoDB:**
```python
async def save_session_cookies(site_name, cookies):
    """Store authenticated session cookies for reuse."""
    await sessions_collection.update_one(
        {"site": site_name},
        {"$set": {
            "site": site_name,
            "cookies": cookies,  # encrypt these before storing
            "saved_at": datetime.utcnow()
        }},
        upsert=True
    )

async def load_session_cookies(browser_context, site_name):
    """Load stored cookies into a browser context."""
    session = await sessions_collection.find_one({"site": site_name})
    if session:
        await browser_context.add_cookies(session["cookies"])
```

**Week 6 Mini-Project:**
Complete automation module:
1. URL classifier that identifies the platform
2. Session loader that restores cookies
3. Universal form detector for unknown platforms
4. Greenhouse adapter for known platforms
5. Resume uploader
6. Screenshot capture before and after submission
7. Status update to MongoDB after submission
8. Telegram notification with screenshot

---

### DAY 35B — CAPTCHA Auto-Solve Integration

> **Gap fixed:** The production checklist includes CAPTCHA detection but no day ever teaches how to integrate an actual solving service. This matters because career portals for large companies frequently use reCAPTCHA v2 and v3, and your automation will encounter them during peak monitoring hours.

**Two types of CAPTCHA your system faces:**

reCAPTCHA v2 — the "I am not a robot" checkbox or the image grid challenge. This is the visible type. Users see it. Your system detects it when Playwright finds a `g-recaptcha` element in the page DOM.

reCAPTCHA v3 — invisible. Runs in the background, scores the session's behaviour from 0 to 1. A score below 0.5 triggers additional verification. Your human simulation layer (delays, warmup, mouse movement) is your primary defence against v3. No external service solves v3 — you avoid it by looking human.

**The two-path strategy for v2:**

Path 1 — Auto-solve via 2captcha service: 2captcha is a paid service (approximately $3 per 1000 CAPTCHAs solved) where real humans solve them within 15 to 60 seconds. Your system sends the CAPTCHA image or site key, waits for a solution token, and injects it into the page. For applications at companies you strongly want, this is worth the small cost.

Path 2 — Pause and notify: When a CAPTCHA is detected and you prefer not to use the solving service, Playwright pauses the session, takes a screenshot, sends it to Telegram with a message saying "CAPTCHA detected on Company X application — please solve manually then tap Continue." You open the actual browser session (Playwright can keep it alive), solve it yourself, and tap Continue in Telegram. The system resumes from where it paused.

**CAPTCHA detection logic:**
Before any form interaction begins, Playwright scans the page for three signals: a `g-recaptcha` div element, an `iframe` with src containing `recaptcha`, or a Cloudflare challenge page (which uses a completely different mechanism). If any signal is found, the CAPTCHA handler activates before any form fields are touched.

**The Cloudflare case:**
Some company career pages use Cloudflare's bot protection, which shows a "Checking your browser" interstitial for 5 seconds before letting humans through. Playwright with playwright-stealth usually passes this automatically because Cloudflare's check is primarily a JavaScript challenge, not a visual puzzle. If it fails, the fallback is to add a longer page load wait and retry once. If the second attempt also fails, skip this company in this cycle and try again in the evening run.

**Today's Task:**
1. Sign up for a free 2captcha account (they offer free credits for testing)
2. Write a `captcha_handler.py` module with two functions: `detect_captcha(page)` that returns the CAPTCHA type or None, and `solve_captcha(page, method)` that either calls 2captcha or sends a Telegram pause notification
3. Integrate the handler into your form filler so it runs before any field interaction
4. Test detection by visiting a page you know has a CAPTCHA
5. Test the Telegram pause path end to end

---

### DAY 35C — Auto-Submit Mode and Trust Levels

> **Gap fixed:** The roadmap mentioned auto-submit mode for trusted platforms but never taught how to configure it or what the trust logic looks like. Without this, every single application requires manual approval — defeating the point of automation for platforms you have used many times safely.

**The trust level system:**
Each platform adapter in your system has a trust level stored in MongoDB. Trust levels are not binary — they are a four-tier scale that determines how much human oversight is needed.

Trust level 0 — manual only: Your system fills the form completely but never submits. It sends you a Telegram message with the filled form screenshot and waits indefinitely for approval. Used for companies you specifically want to review before any submission. Set this for your absolute dream companies.

Trust level 1 — screenshot review: Your system fills the form, takes a screenshot, sends it to Telegram with an Approve and Reject button. Waits up to 2 hours for your response. If no response in 2 hours, escalates with a second notification. If no response in 4 hours, skips this application and logs it for manual action. This is the default for all new platforms.

Trust level 2 — auto-submit with verification: Your system fills the form and submits automatically. It then checks for a confirmation page or confirmation email within 10 minutes. If confirmation arrives, marks as applied and logs success. If no confirmation arrives, sends you a Telegram alert flagging the submission as unverified. Used for platforms you have successfully submitted through multiple times before.

Trust level 3 — fully autonomous: Submit, verify, move on. No notifications unless something goes wrong. Used only for platforms with a perfect submission history of 5 or more successful applications and where you have manually verified the submission confirmation mechanism works reliably. Naukri and Google Forms are candidates for this level after enough successful uses.

**Promoting a platform's trust level:**
A platform starts at trust level 1. After each successful submission that you confirm was received (either via confirmation email or dashboard status update), its success count increments in MongoDB. After 3 confirmed successes, the system suggests promoting to trust level 2 in your weekly digest. You decide. After 5 confirmed successes at level 2, it suggests level 3. You always decide manually — the system never promotes automatically.

**The submission verification step:**
For every submission at trust level 2 and above, the system runs a verification sequence after clicking submit. It waits up to 60 seconds for the page to change. If it reaches a URL containing words like "confirmation," "success," "thank-you," or "submitted," it screenshots that page and marks the application confirmed. If the page does not change or returns to the form (indicating a validation error), it treats the submission as failed and sends an alert with the screenshot.

**Today's Task:**
1. Add a `trust_level` field to each platform adapter document in MongoDB, defaulting to 1
2. Add a `success_count` field that increments after each verified submission
3. Write the submission flow that branches on trust level — screenshot-and-wait for level 1, auto-submit-and-verify for levels 2 and 3
4. Write the verification function that checks the post-submission page
5. Update your Telegram notification module to send the Approve/Reject buttons for level 1 submissions
6. Test the full flow at level 1 with a real test form you create yourself

---

## WEEK 7 — The Orchestrator Agent and Tool System

> **Where this appears in your system:** The Orchestrator is the brain. Without it, you manually decide which tools to use for each input. With it, the system reasons about inputs and composes tool calls automatically.

---

### DAY 36 — LangGraph Fundamentals

**What LangGraph is:**
LangGraph is a framework for building AI agents that can use tools, remember state between steps, and make conditional decisions about what to do next. It is a state machine where the nodes are reasoning or action steps and the transitions between nodes are decided by the AI.

**Why LangGraph for your orchestrator:**
Your orchestrator must handle many different input types — a WhatsApp paste, a scraped job URL, an email notification, a user request from the dashboard — and for each, decide a different sequence of tool calls. LangGraph makes this conditional, dynamic routing natural to build.

**Core concepts:**
A node is a step in the agent's process — either an LLM call that reasons about what to do next, or a tool call that does something.

An edge is the connection between nodes — either always going from node A to node B, or conditionally going different directions based on the LLM's reasoning.

State is the data carried through the agent's process — the input, the results of each tool call, the final output.

**Today's Task:**
Install LangChain and LangGraph. Build the simplest possible agent — one that receives a company name, decides it needs to search for the company's career page, calls a search tool, and returns the URL. This simple agent teaches you the full architecture you'll scale up.

---

### DAY 37-38 — Building the Tool Registry

**The tool registry:**
Each tool in your system is registered with:
1. A name
2. A plain English description of what it does and when to use it
3. The Python function to call when using it
4. The input schema (what data it expects)
5. The output schema (what data it returns)

The LLM reads the descriptions of all available tools and decides which ones to use for a given goal.

**Tool descriptions must be precise:**
Bad description: "Searches the web"
Good description: "Use this when you need to find a company's official careers page URL given only the company name. Input: company name as string. Output: careers page URL as string, or None if not found. Do not use this if you already have the URL."

The precision prevents the LLM from using the wrong tool or using a tool when it shouldn't.

**Building your tool library — each as a registered tool:**
- `web_search` — general web search
- `company_legitimacy_checker` — MCA, LinkedIn, WHOIS verification
- `career_page_scraper` — scrapes job listings from a URL
- `job_board_scraper` — searches major job boards
- `whatsapp_text_extractor` — parses WhatsApp paste to structured data
- `eligibility_matcher` — scores a job against user profile
- `project_matcher` — finds relevant projects via vector search + graph
- `keyword_extractor` — extracts ATS keywords from JD using LLM
- `resume_generator` — generates tailored PDF resume
- `form_filler` — fills and submits job application forms
- `google_forms_filler` — specifically for Google Form applications
- `email_classifier` — classifies incoming emails by type
- `telegram_notifier` — sends notifications to your Telegram
- `mongodb_reader` — reads any data from MongoDB
- `mongodb_writer` — writes any data to MongoDB

**Today's Task:**
Build the tool registry system. Register 5 tools you've already built (scraper, eligibility matcher, project matcher, keyword extractor, resume generator). Write a function that displays all available tools and their descriptions — this is what the LLM reads.

---

### DAY 39-40 — The Orchestrator Agent — Full Implementation

**The orchestrator's reasoning loop:**
1. Receive input (WhatsApp paste, URL, user request)
2. Read all available tool descriptions
3. Reason: "Given my input and goal, which tools should I use and in what order?"
4. Call first tool, receive result
5. Reason again: "Given what I now know, what should I do next?"
6. Call next tool, receive result
7. Continue until goal is achieved
8. Return final result

**The ReAct pattern:**
The LLM follows a strict pattern:
- **Thought:** "I have a company name. I need to find their career page before I can scrape jobs."
- **Action:** Call `career_page_finder` tool with company name
- **Observation:** "Found URL: stripe.com/jobs"
- **Thought:** "Now I have the URL. I should scrape it for job listings."
- **Action:** Call `career_page_scraper` with the URL
- **Observation:** "Found 12 job listings. 3 are backend roles."
- **Thought:** "I should check eligibility for the backend roles."
- Continue...

**Week 7 Mini-Project:**
Complete orchestrator:
1. Takes any input (WhatsApp text, URL, or company name)
2. Correctly selects and sequences tool calls
3. Handles tool failures gracefully (retries or skips to next step)
4. Stores reasoning trace in MongoDB for debugging
5. Returns structured final result
6. Tested with 3 different input types

---

### DAY 40B — Tool Failure Fallback and the Circuit Breaker Pattern

> **Gap fixed:** Day 39-40 said "handles tool failures gracefully" but never taught the architectural pattern for doing this reliably in a 24/7 production system. This is one of the most important reliability concepts in MNC backend engineering.

**The problem without a fallback pattern:**
Your orchestrator calls the career page scraper for a company. The scraper fails because the site is temporarily down. Without a fallback pattern, the orchestrator either crashes the entire pipeline for all companies, retries infinitely and blocks everything else, or silently skips and you never know it happened. All three outcomes are unacceptable in production.

**The circuit breaker pattern — the MNC standard:**
Think of an electrical circuit breaker in your house. When there is a power surge, the breaker trips — it opens the circuit and stops electricity flowing, protecting your appliances. After a safe interval, you reset it and try again.

The software circuit breaker works identically. Each tool has a breaker with three states.

Closed state — normal operation. Calls pass through to the tool. Failures are counted.

Open state — triggered when failures exceed a threshold (for example, 5 failures in 60 seconds). All calls to this tool are immediately rejected without even trying, and a fallback action runs instead. The breaker stays open for a cooldown period (for example, 2 minutes).

Half-open state — after cooldown, one test call is allowed through. If it succeeds, the breaker closes and normal operation resumes. If it fails again, the breaker opens again for another cooldown period.

**Fallback actions per tool — what your system does when each tool is open:**

Career page scraper fails: fall back to python-jobspy for that company's name. If jobspy also fails, log the company as temporarily unavailable and skip until next cycle.

Company legitimacy checker fails: mark the company as "legitimacy unknown — manual review needed" and still proceed with the job analysis so you do not miss good opportunities, but flag it clearly in the notification.

LLM model fails (Ollama down): fall back to Groq cloud API. If Groq rate limit is hit, queue the analysis for 10 minutes and proceed with other tasks.

Resume generator fails: notify you via Telegram immediately and mark the application as "resume generation failed — manual action needed." Do not attempt auto-submission.

Email classifier fails: mark emails as "unclassified" and send all of them as raw text in your daily digest so you can classify manually. Never silently drop an email.

**Why each fallback is different:**
The fallback strategy depends on whether the failure affects your personal data, a time-sensitive action, or a background research task. Missing a company's career page is low urgency. Missing a recruiter email is high urgency. The architecture treats them differently.

**The user-enrichable tool notes:**
Each tool in the registry accepts user-defined notes that are injected into the tool's context at runtime. For example, you add a note to the Naukri form filler: "When applying to Naukri, always set expected salary to 15 percent above current CTC and notice period to 30 days." This note is stored in MongoDB in the tool's document and the orchestrator reads it before calling the tool. You never modify code to change tool behaviour — you update the note in the database or through the dashboard.

**Today's Task:**
1. Wrap your three most critical tools — scraper, LLM caller, resume generator — with the circuit breaker pattern
2. Write a test that intentionally makes each tool fail repeatedly and verify the breaker opens correctly
3. Verify the fallback action runs when the breaker is open
4. Verify normal operation resumes after the cooldown
5. Add a MongoDB document for each tool that stores: current breaker state, failure count, last failure timestamp, and the user-enrichable notes field
6. Add a dashboard indicator showing each tool's current circuit breaker state so you can see at a glance what is healthy

---

## WEEK 8 — Multi-Agent Debate System

> **Where this appears in your system:** The debate system is your competitive advantage. It produces a quality of resume analysis that no single LLM call can match.

---

### DAY 41-42 — CrewAI and Multi-Agent Architecture

**CrewAI concepts:**
An Agent has a role, a goal, a backstory (its persona and expertise), and the tools it can use. A Task is a specific job for an agent to complete. A Crew is a group of agents working together on a set of tasks.

**Your six agents and their deep configuration:**

**The HR Strategist Agent:**
Role: Senior HR Director with 15 years of experience
Goal: Evaluate this candidate's profile from a human and organisational fit perspective
Backstory: Has reviewed 50,000 resumes and conducted 5,000 interviews at Indian and global tech companies. Deeply familiar with how Indian tech hiring works, what top companies look for beyond technical skills, and what causes good candidates to fail interviews.
Tools: Company culture database (MongoDB query), AmbitionBox scraper, Glassdoor scraper, interview review reader

**The Technical Domain Expert Agent:**
Role: Senior Principal Engineer, 12 years in the specific technical domain of the role
Goal: Evaluate the technical depth and credibility of the candidate's claims
Backstory: Has architected systems at scale, reviewed hundreds of technical submissions, knows exactly what questions a panel will ask about each technology claimed, and can detect shallow vs genuine expertise from resume phrasing.
Tools: Tech documentation reader, GitHub analyser, Stack Overflow query, engineering blog reader

**The ATS Compliance Agent:**
Role: ATS System Specialist
Goal: Determine if this resume will pass automated screening for the specific ATS platform this company uses
Backstory: Has studied the parsing behaviour of every major ATS platform. Knows which formatting choices cause fields to be dropped, which keywords must appear in which sections, and what score this resume will receive before any human sees it.
Tools: ATS rules database (MongoDB), ATS platform identifier

**The Industry Insider Agent:**
Role: Current employee or recent interviewee at the target company
Goal: Provide a current, real picture of what this company is actually looking for right now
Backstory: Has deep current knowledge of the target company's products, engineering culture, current hiring priorities, and interview process from public sources researched just before this debate.
Tools: Company intelligence builder (runs fresh research), LinkedIn scraper for recent hires, engineering blog reader, current open roles analyser

**The Devil's Advocate Agent:**
Role: Skeptical hiring manager who has been burned by overstated resumes
Goal: Find every weakness, exaggeration, inconsistency, and gap in this resume and candidacy
Backstory: Deeply cynical, fact-checks every claim, knows all the tricks candidates use to inflate their resumes, and asks the hard questions that will come up in interviews.
Tools: GitHub validator, timeline checker, claim verifier, weakness pattern database

**The Synthesis Judge Agent:**
Role: Chief People Officer making the final hiring recommendation
Goal: Synthesise all agent arguments into an actionable verdict with specific improvements
Backstory: Weighs evidence carefully, understands that every hiring decision involves tradeoffs, produces verdicts that are specific, actionable, and honest.
Tools: All other agent outputs (debate transcript)

**Today's Task:**
Install CrewAI. Build the HR Strategist and Devil's Advocate agents only. Have them debate a real resume and job description. Read their outputs — they should genuinely disagree and challenge each other. If they agree on everything, the prompts need to be more specific and opposing.

---

### DAY 43-44 — Deep Domain Knowledge Injection

**How agents get real knowledge — not just LLM training data:**

Each agent queries real, current sources during its analysis. This is tool use within the agent itself.

For the Technical Expert:
- Before making any claim about a technology, query the Stack Overflow database for the top issues with that technology in production environments from the last 12 months
- Read the last 6 months of the target company's engineering blog
- Check the candidate's GitHub for actual code quality in the claimed technologies

For the HR Strategist:
- Query the AmbitionBox database for the last 50 reviews of the target company
- Identify the most common interview stage where candidates fail
- Identify what qualities reviewers say impressed the interviewers

For the Industry Insider:
- Run fresh company intelligence pipeline before debate begins
- Analyse the last 10 people hired into similar roles at this company via LinkedIn
- Identify what those candidates' backgrounds had in common

All of this is retrieved data, not LLM hallucination. The agent's statements are grounded in real current information.

**Today's Task:**
Add tool use to the Technical Expert agent. When it makes a claim about a technology on the resume, it must first query Stack Overflow for common production problems with that technology and then incorporate this into its argument. The output should reference specific, real technical challenges — not generic statements.

---

### DAY 45 — The Debate Rounds and Synthesis

**Round 1 — Independent analysis (parallel):**
All 5 debating agents run simultaneously. Each reads the resume and JD independently and produces its initial position statement. They do not see each other's output yet.

**Round 2 — Cross-examination (sequential):**
Each agent reads all other agents' position statements and writes a response — either supporting, challenging, or refining based on new information. The Devil's Advocate is especially active here, challenging every positive claim.

**Synthesis:**
The Judge agent reads the full debate transcript and produces:
- Overall hire recommendation (Strong Yes / Yes / Maybe / No)
- Confidence level
- Top 3 specific resume improvements with exact wording suggestions
- Top 5 interview questions this candidate will face that they are currently unprepared for
- A personalised short test — 8 questions across technical and behavioural domains calibrated to this role and this candidate's level
- Gap action plan — for each weakness, a specific action to take before the interview

**Week 8 Mini-Project:**
Complete multi-agent debate system:
1. All 6 agents configured with personas, goals, backstories, and tools
2. Two-round debate for a real job description and your actual resume
3. Judge produces full synthesis report
4. Report stored in MongoDB linked to the application record
5. FastAPI endpoint `POST /debate/analyse` triggers the full debate and returns results
6. Results viewable in a JSON response with all fields

---

# PART 3 — PHASE 3: INTEGRATION AND DEPLOYMENT
## Weeks 9 through 12 — Connecting Everything

---

## WEEK 9 — Company Intelligence and Email Monitoring

### DAY 46-47 — Company Intelligence Pipeline

**Building the research pipeline:**
When a new company appears, the intelligence pipeline runs automatically via MongoDB Change Stream.

The legitimacy checker queries MCA's Signatory Data API for Indian company registration. It checks LinkedIn for company presence and employee count. It checks WHOIS for domain registration date and registrant. It queries Crunchbase for funding history. It checks Glassdoor for whether employee reviews exist (confirming the company has employees who can review it).

The culture researcher scrapes Glassdoor and AmbitionBox reviews, extracts sentiment and key themes, and produces a cultural summary.

The product researcher visits the company's website, engineering blog, and GitHub organisation to understand what they build.

All findings stored in the `company_intelligence` collection and linked to every job from that company.

**Today's Task:**
Build the legitimacy checker component. Test it against 5 companies — 3 legitimate ones you recognise and 2 fake or suspicious ones. Verify it correctly identifies the suspicious ones.

---

### DAY 48-49 — Email Monitoring and Classification

**IMAP email reading:**
IMAP allows Python to connect to your email inbox and read messages without deleting them. Your system polls every 30 minutes for new emails from domains that match companies you've applied to.

```python
import imaplib
import email

def check_inbox_for_recruiter_emails(email_address, password, applied_companies):
    """
    Check email inbox for responses from companies you've applied to.
    Returns list of classified email events.
    """
    mail = imaplib.IMAP4_SSL("imap.gmail.com")
    mail.login(email_address, password)
    mail.select("inbox")

    # Search for unseen emails from the last 24 hours
    status, messages = mail.search(None, "UNSEEN SINCE " + yesterday_date())
    # Process each email...
```

**LLM email classification:**
Each email is sent to the local LLM with the prompt: "Classify this email as one of: interview_invite, oa_received, rejection, follow_up_request, generic_acknowledgement, other. Return JSON with classification and any extracted dates, links, or deadlines."

**Today's Task:**
Build the email monitor with LLM classification. Test it by sending yourself test emails of each classification type and verifying the classifier works correctly.

---

### DAY 50 — Telegram Bot Notifications

**Building your notification system:**
The Telegram Bot API is a simple HTTP API. You create a bot via BotFather on Telegram, get a token, and send messages to your chat ID.

Every notification in your system goes through a standardised notification function that:
1. Formats the message with appropriate structure
2. Includes an action if needed (approve/reject button for applications)
3. Includes the relevant screenshot or summary
4. Logs the notification to MongoDB with timestamp and read status

**Today's Task:**
Build the complete notification module. Test every notification type:
- New job match above threshold (with match score and top skills)
- Interview invite detected (with date, time, company)
- OA received (with deadline)
- Form ready for approval (with screenshot)
- Daily morning digest (with yesterday's summary)

---

### DAY 50B — Google Sheets Integration — Daily Report System

> **Gap fixed:** The daily report was described throughout the roadmap as a key output, but the actual implementation using the Google Sheets API was never taught. This day teaches the complete integration so your 6am report actually gets generated.

**Why Google Sheets for the daily report:**
Google Sheets is the right choice for a daily report for three reasons. First, it is always accessible from any device without downloading anything. Second, it supports formulas — you can add your own calculated columns, charts, and pivot tables on top of the data the system writes. Third, it is free forever and never requires deployment. Your data stays in MongoDB, the report is a formatted view of it in Sheets.

**How the Google Sheets API works:**
Google provides a Sheets API that lets your Python code read from and write to any Google Sheet you own. Authentication uses a service account — a special Google account created for your application that has permission to access specific sheets. You create it in Google Cloud Console, download a JSON credentials file, and your Python code uses this file to authenticate.

**Setting up the Google Sheets connection:**

Step 1: Go to Google Cloud Console, create a project called "job-agent-reports." Enable the Google Sheets API and the Google Drive API for this project. Create a service account, download its JSON credentials file. This file contains the private key your Python code uses to authenticate.

Step 2: Create a Google Sheet called "Job Agent Daily Reports." Share it with the service account's email address (it looks like something@your-project.iam.gserviceaccount.com) with Editor permission.

Step 3: Store the path to your credentials JSON file in your `.env` file as `GOOGLE_CREDENTIALS_PATH`. Never commit the credentials file to GitHub — add it to `.gitignore`.

Step 4: Install the `gspread` library. `gspread` is the Python wrapper for the Google Sheets API that makes the complex API simple.

**The daily report structure:**
Your sheet has one tab per month (not per day — daily tabs would create 365 tabs per year which becomes unmanageable). Each month's tab has rows for each day's activity. The first row of each tab is a header. Each application submitted gets one row.

Columns: Date | Company | Role | Source | Match Score | Legitimacy | Application Status | Resume Version | Top Missing Skill | Notes

At the top of each tab, rows 1 through 5 are summary statistics: total jobs scraped this month, total applied, total interviews, total rejections, response rate percentage. These use Google Sheets formulas that update automatically as new rows are added below.

**The 6am Atlas Trigger:**
Your MongoDB Atlas Scheduled Trigger runs at 6:00 AM every day. It calls your FastAPI endpoint `POST /reports/daily`. This endpoint queries MongoDB for all activity from the previous day, formats it into rows, and appends them to the current month's Google Sheet tab. If the tab for the current month does not exist yet, it creates it with the header row first.

**Today's Task:**
1. Set up the Google Cloud service account and enable the Sheets and Drive APIs
2. Create the report Google Sheet and share it with the service account
3. Add credentials path to `.env` and `.gitignore`
4. Install `gspread` and write a `reports/sheets_reporter.py` module with: `create_month_tab(sheet, month_name)`, `append_application_row(sheet, application_data)`, `update_summary_stats(sheet)`
5. Write the `POST /reports/daily` FastAPI endpoint that queries MongoDB and calls the reporter
6. Create the Atlas Scheduled Trigger at 6am calling this endpoint
7. Test by manually calling the endpoint and verifying a row appears in your sheet

---

### DAY 50C — Email Outbound — Secondary Notification Channel

> **Gap fixed:** Telegram is the primary notification channel. Email was listed as secondary in the feature specification but no day taught how to send emails from Python. This is a critical fallback — if Telegram is down or you lose your phone, you still receive critical alerts.

**Why email as secondary:**
Telegram requires the app to be installed and you to be logged in. Email works from any browser, on any device, even when you change phones. For high-priority events — interview invites, offer received — having a redundant notification channel is not optional in a production system.

**Two approaches to sending email from Python:**

Approach 1 — SMTP directly using `smtplib`: Python's built-in library. You connect to Gmail's SMTP server (smtp.gmail.com, port 587), authenticate with your Gmail address and an App Password (not your regular password — Gmail requires a special App Password for programmatic access), and send. This is free and has no rate limits for personal volume. The limitation is that Gmail marks programmatically sent emails as promotional, which is fine for self-notifications.

Approach 2 — SendGrid or Resend API: Third-party email services that offer free tiers (100 emails per day on SendGrid free tier) and handle deliverability, formatting, and tracking. Better if you eventually want to send follow-up emails to recruiters using this same system. More setup but more capable.

For your personal notification system, SMTP is sufficient and has zero dependencies. For the follow-up automation future feature, you will want SendGrid or Resend.

**The email notification module:**
Your `notifications/email_notifier.py` module wraps the SMTP connection in a context manager and provides functions for each notification type. Each function has a pre-written subject line and HTML body template.

The functions: `send_interview_alert(company, role, date, time)`, `send_offer_alert(company, role, salary)`, `send_daily_digest(summary_data)`, `send_application_submitted(company, role, screenshot_path)`.

**Gmail App Password setup:**
Go to your Google Account → Security → 2-Step Verification → App Passwords. Generate a password for "Mail" on "Other device." This 16-character password goes in your `.env` as `EMAIL_APP_PASSWORD`. Your regular Gmail password is not used.

**The notification priority logic:**
Not all events warrant both Telegram and email. Email is heavier — it creates a record in your inbox and can be searched later. Use this routing logic:

Telegram only: new job match, legitimacy flag, CAPTCHA detected, form approval request, daily digest (Telegram version is more convenient for quick review).

Both Telegram and email: interview invite, OA received with deadline, offer received, application submission confirmed.

Email only (as backup when Telegram fails): anything Telegram tries to send that fails gets automatically retried via email.

**Today's Task:**
1. Enable 2-Step Verification on your Gmail and generate an App Password
2. Add `EMAIL_ADDRESS` and `EMAIL_APP_PASSWORD` to `.env`
3. Write `notifications/email_notifier.py` with the four functions listed above
4. Write an HTML email template for the interview invite notification — it should look clean and professional, not like a wall of text
5. Update your notification router so interview invites and offer alerts trigger both Telegram and email simultaneously
6. Add a fallback: wrap every Telegram call in try-except, and if it fails, call the email function for the same event
7. Test by triggering a fake interview invite event and verifying you receive both a Telegram message and an email

---

## WEEK 10 — Next.js Dashboard

> **Where this appears in your system:** The dashboard is how you interact with everything your system knows and does.

---

### DAY 51-52 — Next.js Fundamentals

**What Next.js is:**
Next.js is a React framework. React is a JavaScript library for building user interfaces. Next.js adds routing, server-side rendering, and deployment to React — making it the industry standard for production web applications.

**Your dashboard pages:**
- `/` — Daily digest home page with yesterday's summary
- `/jobs` — All discovered jobs with filters by status, match score, company
- `/jobs/[id]` — Single job detail with full analysis, matched projects, keywords
- `/apply/[id]` — Job application page with generated resume preview and approve button
- `/applications` — Kanban board of all applications by status
- `/companies` — Company intelligence reports
- `/debate/[id]` — Full multi-agent debate report for a job
- `/profile` — Your skills, projects, and profile management

**Today's Task:**
Install Node.js and create a Next.js app: `npx create-next-app@latest dashboard`. Build the home page showing a count of jobs found today, applications pending review, and interviews scheduled. Read this data from your FastAPI backend.

---

### DAY 53-55 — Building Each Dashboard Page

**The applications Kanban board:**
A Kanban board shows applications organised in columns by status — applied, under review, OA received, interview scheduled, offer received, rejected. You can drag cards between columns to update status. Each card shows company name, role, match score, and last activity date.

**The debate report page:**
Shows the full multi-agent debate for a job — each agent's position, the cross-examination, and the synthesis verdict. The interview prep questions become a printable checklist. The improvement recommendations become action items with checkboxes.

**The daily digest:**
A clean overview of yesterday's activity: N new jobs found, N shortlisted, N applications submitted, N status changes, any interviews scheduled this week. One screen, everything you need to know each morning.

**Week 10 Mini-Project:**
Fully functional Next.js dashboard:
1. Home page with daily digest
2. Jobs list with search and filter
3. Single job page with full analysis
4. Applications Kanban board
5. One company intelligence report page
6. Deployed to Vercel (free) connected to your GitHub repository

---

## WEEK 11 — MongoDB Atlas Advanced Features

### DAY 56-57 — Atlas Scheduled Triggers

**Replacing Celery and Redis:**
Instead of running a separate Celery task queue and Redis broker, MongoDB Atlas Triggers execute JavaScript functions on a schedule. For your system, this means two functions — one at 7am and one at 9pm — that trigger the full scraping and analysis pipeline.

The trigger calls your FastAPI backend via HTTP, which runs the pipeline. No additional infrastructure.

**Setting up triggers:**
In Atlas web interface → Triggers → Scheduled Trigger → Select database → Write the trigger function → Set cron schedule (`0 7 * * *` for 7am daily).

**Today's Task:**
Create two scheduled triggers:
1. Morning scraper: runs at 7am, calls `POST /scraper/run-morning-cycle`
2. Evening scraper: runs at 9pm, calls `POST /scraper/run-evening-cycle`

Test by temporarily changing the schedule to run every 2 minutes and verifying MongoDB receives new job documents.

---

### DAY 57B — Atlas Full-Text Search

> **Gap fixed:** Atlas Full-Text Search was listed in the Part 0 architecture as a capability of MongoDB Atlas but was never taught as a dedicated module. It is used in three places in your system: searching job descriptions for specific terminology, the dashboard search bar, and the cover letter generator querying your project descriptions for relevant phrases.

**Vector search vs full-text search — when to use which:**
Vector search finds documents by meaning similarity — semantically close content even if words differ. Full-text search finds documents by exact or fuzzy word matching — fast, precise, and perfect when you know the exact term you are looking for.

In your system, full-text search handles specific keyword queries like "find all jobs mentioning Kubernetes in the description" or "find all my projects that reference payment processing." Vector search handles conceptual queries like "find projects similar to this job description."

**What Atlas Search is:**
Atlas Search is MongoDB's full-text search engine built on Apache Lucene, the same engine that powers Elasticsearch. It creates inverted indexes — data structures that map every word to every document containing it — and supports fuzzy matching, stemming, phrase search, autocomplete, and relevance scoring. You enable it in the Atlas UI with no additional infrastructure.

**Setting up Atlas Search indexes:**

For the jobs collection: create a search index on the `jd_text`, `title`, and `company` fields. This powers the dashboard search bar — when you type "React fintech" it finds all jobs where those words appear anywhere in the title, company, or description.

For the projects collection: create a search index on `description`, `achievements`, and `tech_stack`. This is used by the cover letter generator when it searches for specific accomplishments to cite.

For the company intelligence collection: create a search index on `culture_summary` and `product_description`. Used when an agent searches for specific company characteristics during the debate.

**Running full-text queries:**
Atlas Search queries use the `$search` aggregation stage. The query syntax has three modes you will use:

Text search — finds documents where any of the search terms appear: use this for the dashboard search bar.

Phrase search — finds documents where a specific phrase appears exactly: use this when searching for a technology name that is also a common word ("Go" language searches need phrase matching to avoid matching every document containing the word "go").

Fuzzy search — finds documents where words are similar to the search term, accounting for typos: use this for the profile skills search where someone might type "JavaScrpt" and still find JavaScript jobs.

**Combining Atlas Search with vector search:**
For the most powerful queries, your system runs both simultaneously and merges results. For the dashboard search bar: run Atlas Search for exact matches first (high confidence), then run vector search for semantic matches (broader results), then deduplicate and merge the two result sets ranked by relevance score. This two-stage retrieval is called hybrid search and is the current industry standard for AI-powered search.

**Today's Task:**
1. Create Atlas Search indexes on the jobs, projects, and company intelligence collections in the Atlas UI
2. Write a `search/atlas_search.py` module with: `search_jobs(query_text)`, `search_projects(query_text)`, `search_companies(query_text)`
3. Write a `search/hybrid_search.py` module that calls both Atlas Search and vector search, merges and deduplicates results, and returns them ranked by combined score
4. Update your dashboard's `GET /jobs/search` FastAPI endpoint to use hybrid search
5. Test by searching for a technology you know appears in some of your stored jobs and verifying relevant results appear
6. Test fuzzy matching by intentionally misspelling a technology name and verifying it still finds relevant results

---

### DAY 58-59 — Atlas Change Streams

**What Change Streams are:**
Change Streams watch a MongoDB collection for changes and fire an event when a document is inserted, updated, or deleted. Your system uses this to trigger actions automatically when new data arrives.

**Your Change Stream triggers:**
- New document in `jobs` with `status: "new"` → trigger eligibility matching and project matching
- Match score updated above threshold → trigger resume generation
- New document in `applications` with `status: "applied"` → trigger debate analysis
- Email classified as `interview_invite` → trigger immediate Telegram notification
- Debate analysis complete → trigger Telegram notification with results

**Today's Task:**
Implement a Change Stream on the `jobs` collection that watches for new inserts. When a new job is inserted, it automatically calls the eligibility matcher and updates the document with the match score. Test it by manually inserting a job document.

---

## WEEK 12 — Production Deployment

### DAY 60-62 — Deploying to Railway and Vercel

**Railway for FastAPI backend:**
Railway is a platform that runs your Python server 24/7 for free up to a usage limit sufficient for personal use. You connect your GitHub repository, configure environment variables in the Railway dashboard, and Railway automatically deploys when you push new code.

**Deployment checklist for FastAPI:**
- All environment variables in Railway settings (not in code)
- `requirements.txt` lists all Python dependencies
- `Procfile` or `railway.json` tells Railway how to start your server
- CORS configured to allow requests from your Vercel frontend domain
- MongoDB Atlas IP whitelist includes Railway's IP ranges

**Vercel for Next.js frontend:**
Connect your GitHub repository to Vercel. Configure environment variable `NEXT_PUBLIC_API_URL` pointing to your Railway backend URL. Every push to GitHub automatically deploys the latest version.

**Today's Task:**
Deploy your FastAPI backend to Railway. Deploy your Next.js dashboard to Vercel. Verify the frontend successfully reads jobs from the backend. Fix any CORS or environment variable issues.

---

### DAY 63-65 — Groq Cloud API — The Cloud Model Alternative

**When to use Groq instead of local Ollama:**
Groq hosts the same open-source models (Llama, Mistral) on custom hardware and provides them via a free API. When your system is deployed to Railway (no GPU), it calls Groq instead of local Ollama.

**The model abstraction layer:**
Build a `model_client.py` that automatically chooses local Ollama or Groq based on an environment variable:

```python
MODEL_BACKEND = os.getenv("MODEL_BACKEND", "local")

async def call_llm(prompt, system_prompt=""):
    if MODEL_BACKEND == "local":
        return await call_ollama(prompt, system_prompt)
    elif MODEL_BACKEND == "groq":
        return await call_groq(prompt, system_prompt)
```

Setting `MODEL_BACKEND=local` in your `.env` uses Ollama. Setting `MODEL_BACKEND=groq` uses Groq's free API. Same code, different execution environment.

**Today's Task:**
Get a Groq API key from console.groq.com (free). Build the model abstraction layer. Test both backends with the same prompt and compare quality and speed. Document the differences.

---

### DAY 66-67 — Fine-tuning with LoRA (Introduction)

**What fine-tuning means for your system:**
Your local Llama model knows about programming generally. Fine-tuning makes it specifically expert at job description parsing and resume keyword injection. After fine-tuning, it requires fewer prompt tokens to get structured output, produces more consistent JSON, and better understands ATS-specific vocabulary.

**The training data format:**
```json
{
    "instruction": "Extract required skills from this job description and return JSON",
    "input": "We are looking for a Backend Engineer with 3+ years Python experience...",
    "output": "{\"required_skills\": [\"Python\", \"PostgreSQL\", \"REST APIs\"], ...}"
}
```

You create 200-500 such examples from real job descriptions. The quality of these examples determines the quality of the fine-tuned model.

**The LoRA approach:**
Using the `trl` and `peft` libraries from Hugging Face, you freeze the base Llama model's weights and add small trainable matrices at specific layers. Only these small matrices are trained — this requires a fraction of the memory and compute of full fine-tuning. A laptop GPU with 8GB VRAM can fine-tune a 7B model.

**Today's Task:**
Create 20 high-quality training examples from real job descriptions and their ideal parsed outputs. This is the beginning of your fine-tuning dataset. Build it incrementally — add 5 new examples every week from real jobs your system processes.

---

# PART 4 — PHASE 4: ADVANCED FEATURES AND OPTIMISATION
## Weeks 13 through 16

---

### WEEK 13 — Security Hardening

**Day 68-70 — Complete Anti-Detection System**

**Browser fingerprint complete list:**
Your Playwright automation must match the fingerprint of a real human browser. The attributes that differ between a real browser and an automated one:

`navigator.webdriver` — normally undefined in real Chrome, set to `true` in automation. playwright-stealth patches this.

`navigator.plugins` — real Chrome has installed plugins. Headless Chrome has none. Playwright-stealth injects realistic fake plugin data.

Canvas fingerprinting — websites draw invisible canvases and read the pixel data to fingerprint the GPU and rendering engine. Your automation must produce realistic canvas data.

WebGL fingerprinting — similar to canvas, uses GPU rendering characteristics. Must be realistic.

`navigator.languages` — set to your actual language preferences, not just `en-US`.

Screen resolution — must match a real monitor, not 0x0 or unrealistically large values.

Hardware concurrency — `navigator.hardwareConcurrency` must match a realistic CPU core count.

**The session warmup protocol:**
Every browser session follows this sequence before reaching the target site:
1. Open browser with a fresh context
2. Visit a neutral website (news site, not Google which fingerprints heavily)
3. Wait 15-30 seconds, scroll naturally
4. Type a random search in the browser's URL bar (abandoned before submitting)
5. Navigate to the target company's homepage (not the careers page directly)
6. Wait 20-40 seconds on homepage, scroll
7. Navigate to About Us page, wait briefly
8. Navigate to Careers page — this is now the third page visited, consistent with human browsing

**Day 71-72 — Data Security**

**Encrypting sensitive MongoDB fields:**
Session cookies, email credentials, and API keys stored in MongoDB must be encrypted at the field level. The database file can be seen if someone gains access to MongoDB — encrypted fields cannot be read without your encryption key.

Use Python's `cryptography` library (Fernet symmetric encryption):
- Generate an encryption key once, store it as an environment variable
- Encrypt sensitive values before inserting to MongoDB
- Decrypt after reading from MongoDB
- The MongoDB document stores ciphertext — unreadable without the key

**Day 73 — Audit Logging**

Every action your system takes is logged to a `system_audit` MongoDB collection:
- Which tool was called
- What input it received
- What output it produced
- Whether it succeeded or failed
- Timestamp and duration

This lets you debug issues, prove the system's behaviour, and identify which tools need improvement.

---

### WEEK 14 — The Feedback Loop and Self-Improvement

**Day 74-76 — Outcome Tracking**

**What outcomes to track:**
Every application has an outcome. When you receive an interview invite, that is a positive signal. When you receive a rejection, that is a signal about what didn't work. When you get no response after 3 weeks, that is also a signal.

For each outcome, record:
- Which resume version was used
- The match score at time of application
- Which keywords were injected
- Which projects were highlighted
- The debate system's confidence score
- The HR agent's recommendation

Over time, statistical patterns emerge: resumes with certain keyword patterns get more interviews. Certain project combinations get better responses. Certain companies never respond to cold applications.

**Day 77 — Analytics Dashboard**

Build an analytics page showing:
- Application to interview conversion rate over time
- Which skill keywords correlate with interview invitations
- Which companies have responded vs never responded
- Average match score of applications that got responses vs those that didn't
- Month-over-month trend of all metrics

This data drives improvement of the entire system.

---

### WEEK 15-16 — Portfolio and Documentation Strategy

**Day 78-80 — GitHub as Your Portfolio**

**Repository structure:**
Your `job-agent` repository is your primary portfolio piece. Structure it like a real MNC project:

```
README.md — Complete project overview with architecture diagram
CONTRIBUTING.md — How others can contribute
CHANGELOG.md — Version history of features added
docs/
├── architecture.md — System design document
├── setup.md — How to install and run locally
├── api.md — All FastAPI endpoints documented
└── deployment.md — How to deploy to production
src/
├── backend/
├── frontend/
├── agents/
└── automation/
tests/ — All your test files
```

**The README as a portfolio showcase:**
Your README must convey to a recruiter in 60 seconds:
1. What the system does (one sentence)
2. What technologies it uses (badges)
3. A screenshot or diagram of the system working
4. The architecture (one diagram)
5. How to run it locally (clear steps)
6. What you learned building it

**Day 81-83 — Technical Blogging**

For each major component you build, write a technical blog post:
- "How I built an AI-powered resume generator using LaTeX and local LLMs"
- "Building a multi-agent debate system with CrewAI for resume evaluation"
- "MongoDB Atlas as a unified vector + graph + document database for AI applications"
- "Anti-detection strategies for ethical web automation with Playwright"

Publish on dev.to and Hashnode — both free, both indexed by Google. Recruiters search for specific technical topics and find candidates this way. Link your GitHub project in every post.

**Day 84 — Recruiter-Visible Proof of Work**

Beyond LinkedIn and GitHub:
- Submit your project to HackerNews "Show HN" — genuine engineering projects get attention
- Post on relevant subreddits — r/Python, r/MachineLearning, r/learnprogramming
- Create a short screen recording of the system working end-to-end — LinkedIn video posts get 3x more views than text posts
- Present at a local Python or tech meetup — most cities have monthly meetups, they actively look for speakers with real projects

---

---

# PART 5 — PHASE 5: FUTURE FEATURES
## Weeks 17 through 20 — Elite Capabilities

> **When to start this phase:** Only after the entire system from Phases 1 through 4 is running in production and you have at least 4 weeks of real application data. These features require the core system to be stable — they build on top of it, not alongside it.

---

## WEEK 17 — Onboarding Automation and Referral Intelligence

### DAY 85-86 — Resume Parser for Initial Setup

**Why this is the first thing in Phase 5:**
Every new user of your system — including future you if you ever reinstall — should not have to manually enter every project, skill, and experience into MongoDB. A one-time resume parser reads your existing PDF resume and auto-populates all collections.

**The parsing approach:**
Use `PyMuPDF` (also called `fitz`) to extract text from your existing resume PDF. The extracted text is then sent to the local LLM with a prompt that says: "Parse this resume text and return a JSON object with: personal info, skills list with categories, experience entries with company and dates, education, and projects with tech stacks and descriptions." The LLM output is validated with Pydantic and inserted into MongoDB.

This is not perfect — some formatting gets lost in PDF extraction. But it populates 80 to 90 percent of your data automatically. You manually correct the rest through the dashboard profile editor.

**Today's Task:**
Build the one-time setup script: reads your existing PDF resume, extracts text via PyMuPDF, parses with LLM, validates with Pydantic, inserts into all MongoDB collections. Add a `POST /setup/parse-resume` FastAPI endpoint that accepts a PDF upload and runs this pipeline.

---

### DAY 87-88 — Referral Intelligence System

**What referral intelligence does:**
A referral application has a 5 to 10 times higher callback rate than a cold application. When a new job match appears at a company where you have a LinkedIn connection, the system alerts you to request a referral before applying cold.

**The LinkedIn connection graph:**
LinkedIn does not have a public API for connection data. The approach is a one-time Playwright session where your LinkedIn connections page is scraped and all connection names, titles, and companies are stored in a `connections` MongoDB collection. You run this manually once a month to keep it fresh.

When a new job document is inserted with a company name, a MongoDB Change Stream checks if any document in `connections` has a matching company. If yes, an immediate Telegram alert fires: "You have a connection at Stripe — Rahul Sharma (Senior Engineer). Request a referral before applying."

**The referral request drafter:**
The LLM drafts a personalised LinkedIn message to your connection based on: your shared background, the specific role, and why you are a good fit. You approve and send manually — never automate outreach to personal connections.

**Today's Task:**
Build the connection scraper (one-time, manual run), the company matching Change Stream listener, and the referral message drafter. Test with a fake connections dataset.

---

## WEEK 18 — Follow-up and Salary Intelligence

### DAY 89-90 — Follow-up Automation

**What follow-up automation does:**
If you applied 14 days ago and the application status is still "applied" with no email received, the system drafts a polite, personalised follow-up email for your review. You approve and send — it never sends automatically.

**The follow-up drafter:**
The LLM generates a follow-up email using: recruiter name (if extracted from the application confirmation email), role title, application date, and one specific thing about the company that shows genuine interest (pulled from the company intelligence document). The email is stored in MongoDB as a draft and shown in the dashboard under "Pending Follow-ups."

**Today's Task:**
Build a daily check that runs at 6am alongside the report: finds all applications where `applied_at` is more than 14 days ago and status is still "applied," drafts a follow-up email for each, stores as draft in MongoDB, and includes them in the daily Telegram digest under "Follow-ups to send."

---

### DAY 91-92 — Salary Estimation and Negotiation Intelligence

**What salary estimation does:**
Most Indian job portals do not show salary. Before you apply — and certainly before you negotiate — you need a realistic range for the role, company size, location, and seniority level.

**Data sources:**
AmbitionBox has salary data for Indian companies by role and seniority. Levels.fyi has data for global and Indian tech companies at various levels. Glassdoor has salary ranges by role and location. Your system scrapes all three and triangulates a range.

**The negotiation brief:**
When you receive an offer, the system generates a one-page negotiation brief: the offered salary, the market range from all three sources, the recommended counter-offer (15 percent above offer if below market median, 10 percent above if at median), and three data points you can cite in the negotiation conversation. This is not about being aggressive — it is about negotiating from data.

**Today's Task:**
Build the salary estimator: takes role title, company name, location, and seniority level, queries all three sources, returns a range with the data sources cited. Add a `GET /salary/estimate` endpoint. Test with 5 real roles you are targeting.

---

## WEEK 19 — Interview Scheduling and Skill Gap Learning

### DAY 93-95 — Interview Scheduling Assistant

**What the scheduling assistant does:**
When your email classifier detects an interview invite, it extracts the proposed time slots from the email. The assistant checks your calendar, ranks the slots by your preference (morning vs afternoon, earlier vs later in the week), drafts a confirmation reply with your preferred slot, and creates a calendar event with preparation reminders.

**Google Calendar integration:**
Google Calendar has an API identical in setup to the Sheets API — service account, credentials JSON, same gspread-style library called `google-api-python-client`. Your system creates calendar events with: event title (Interview: Company Role), start and end time, location or video link extracted from the email, and a description with the debate report summary and interview prep questions attached.

**Preparation reminders:**
48 hours before: "Interview in 2 days — review these 5 technical topics flagged by the debate system."
24 hours before: "Interview tomorrow — review your project stories and these 3 behavioural questions."
2 hours before: "Interview in 2 hours — review the company's recent blog posts and this one-pager on the role."

**Today's Task:**
Set up Google Calendar API access (same service account as Sheets). Write the scheduling assistant that reads extracted time slots, creates a calendar event, and sets the three preparation reminders. Test with a manually created fake interview invite.

---

### DAY 96-97 — Skill Gap Learning Roadmap Generator

**What the skill gap tracker does:**
Every time the eligibility matcher runs and identifies missing skills, those gaps are logged in MongoDB with the company and role type. After enough data accumulates, patterns emerge: you have been missing Kubernetes in 8 out of 12 backend roles you matched. That is a high-priority learning gap.

**The learning roadmap generator:**
When a skill appears as a gap in 5 or more jobs, the LLM generates a learning roadmap for it: what level of knowledge is needed (basic familiarity vs production experience), the best free resources to learn it (official docs, specific YouTube playlists, GitHub projects to study), and a project you can build to demonstrate it that would also fill a gap in your projects database.

**The gap closure tracker:**
When you complete a course or build a project closing a gap, you mark it closed in the dashboard. The system adds the new skill to your profile, re-runs eligibility matching on all jobs currently in your "near match" band, and alerts you if any have now crossed into strong match territory.

**Today's Task:**
Build the gap aggregator that counts skill occurrences across all below-threshold jobs. Build the learning roadmap generator for the top 3 gaps. Add a "Skill Gaps" page to the dashboard showing each gap with count, priority, and the generated learning roadmap.

---

## WEEK 20 — Browser Extension and Mobile PWA

### DAY 98-100 — Browser Extension

**What the extension does:**
You are browsing any website and spot a job posting. You click the extension icon. A popup appears showing: match score, company legitimacy status, and a one-click "Add to System" button that sends the job to your FastAPI backend and triggers the full analysis pipeline — without opening the dashboard.

**Chrome Extension architecture:**
A Chrome Extension has three parts: a manifest.json that declares permissions and entry points, a background service worker (a JavaScript file running in the background), and a popup UI (HTML and JavaScript shown when you click the icon).

The extension reads the current page's URL and selected text (if you select the job description before clicking). It sends both to your FastAPI backend via a fetch call. The backend runs the full orchestrator pipeline. The extension shows a loading spinner, then displays the match score when ready.

**The manifest.json permissions:**
Your extension needs: `activeTab` (read the current page's URL), `storage` (store your FastAPI backend URL so you can change it without rebuilding), and `scripting` (inject a content script to extract page text).

**Today's Task:**
Build the Chrome extension. Focus on: reading the current page URL and selected text, sending to FastAPI, and displaying the match score in the popup. Do not build a complex UI — a clean, minimal popup with the score, company name, and an "Add to System" button is sufficient and deployable.

---

### DAY 101-102 — Mobile PWA

**What a PWA is:**
A Progressive Web App is a website that behaves like a native app on mobile — it can be added to the home screen, works offline for cached content, and receives push notifications. You do not build a separate mobile app. You configure your existing Next.js dashboard to be installable as a PWA.

**Next.js PWA configuration:**
Install `next-pwa`. Add a `manifest.json` to your public folder describing your app name, icons, and theme colour. Configure `next-pwa` in your Next.js config. That is approximately 90 percent of the work for basic PWA functionality.

The app is then installable from Chrome on Android or Safari on iOS via "Add to Home Screen." Once installed, it opens in full-screen without a browser address bar and looks like a native app.

**The approval workflow on mobile:**
The most important mobile feature is approving applications. When Playwright fills a form and sends you the screenshot, you receive a Telegram message with an Approve button. Tapping it sends a request to your FastAPI backend that triggers form submission. This already works. The PWA dashboard provides an alternative approval path for when you want to see more detail than Telegram shows — a full-screen view of the filled form screenshot with swipe-to-approve gesture.

**Today's Task:**
1. Install and configure next-pwa in your dashboard
2. Create the manifest.json with icons in 192x192 and 512x512 sizes
3. Test installation on your phone via Chrome
4. Verify the application approval page is touch-friendly and works correctly on a small screen

---

# PART 5 — FULL PRODUCTION CHECKLIST

## Before You Consider the System Production-Ready

### Functionality Checklist
- [ ] Job scraper runs on schedule and finds new jobs correctly
- [ ] Deduplication prevents duplicate processing
- [ ] Weighted five-dimension eligibility scorer produces accurate scores with breakdown
- [ ] Near-match vs hard-mismatch classification working with gap category logging
- [ ] Vector search returns genuinely relevant projects
- [ ] Graph traversal correctly identifies skill relationships
- [ ] Atlas Full-Text Search index active on jobs, projects, and company intelligence collections
- [ ] Hybrid search combining vector and full-text working on dashboard
- [ ] JD parser extracts correct structured data from varied job descriptions
- [ ] Template selector correctly picks one of four base templates per role type
- [ ] Resume generator produces ATS-passing PDFs with role-appropriate structure
- [ ] Keyword injection is natural, not stuffed
- [ ] All adapter types work (Greenhouse, Lever, Workday, Naukri, Google Forms, Universal)
- [ ] Session cookies correctly maintain login state
- [ ] CAPTCHA detection works — auto-solve path and Telegram pause path both tested
- [ ] Trust level system working — level 1 awaits approval, level 2 auto-submits and verifies
- [ ] Submission verification confirms application received before marking as applied
- [ ] Circuit breaker working on all critical tools — open/half-open/closed states tested
- [ ] Tool failure fallbacks run correctly for each tool type
- [ ] Email classifier accurately categorises all email types (IMAP read)
- [ ] Email outbound sends alerts via SMTP for high-priority events
- [ ] Telegram bot fires for all event types
- [ ] Both channels fire simultaneously for interview invites and offers
- [ ] Telegram fallback to email when Telegram call fails
- [ ] All 6 debate agents produce distinct, substantive arguments
- [ ] Debate agents query real live sources — not just LLM training data
- [ ] Synthesis report is actionable and specific
- [ ] Dashboard shows real data and updates in real time
- [ ] Google Sheets daily report generates automatically at 6am via Atlas Trigger
- [ ] Proxy pool manager working — selects healthy proxies, marks rate-limited ones
- [ ] IP rotation activates automatically after three consecutive 429 responses on a domain

### Security Checklist
- [ ] No API keys or passwords in Git history (check with `git log --all -p | grep -E "password|secret|key"`)
- [ ] Google service account credentials JSON in `.gitignore`
- [ ] All sensitive MongoDB fields encrypted with Fernet
- [ ] HTTPS on all deployed services — Vercel auto-handles, Railway requires HTTPS setting
- [ ] Environment variables on Railway and Vercel — verified not in code
- [ ] playwright-stealth active on all automation sessions
- [ ] Human simulation delays on all form interactions — character-by-character typing verified
- [ ] Session warmup protocol runs before every new domain visit
- [ ] Device profile consistency — same user agent and screen resolution per site stored in MongoDB
- [ ] Rate limiting on all external requests with exponential backoff
- [ ] Circuit breaker protecting all critical external calls
- [ ] Audit log capturing all system actions in MongoDB
- [ ] 2captcha or pause-and-notify CAPTCHA handler active before every form submission

### Code Quality Checklist
- [ ] Every function has a docstring with Args and Returns documented
- [ ] Every module has comprehensive error handling — no bare `except` clauses
- [ ] Every database operation has a try-catch with specific error logging
- [ ] Structured logging throughout using Python `logging` module — not print statements
- [ ] No hardcoded values anywhere — all in config or environment variables
- [ ] All modules are independently testable with at least one test per function
- [ ] Git history has meaningful conventional commit messages (feat/fix/docs/refactor)
- [ ] README is complete — architecture diagram, setup instructions, all endpoints documented
- [ ] `DEVLOG.md` maintained with daily entries
- [ ] `docs/` folder has one markdown file per major component

---

# OVERALL TIMELINE SUMMARY

| Phase | Duration | What You Build |
|---|---|---|
| Phase 1: Foundations | Weeks 1-4 | Python, Git, MongoDB CRUD, HTTP, async, scraping, AI embeddings |
| Phase 2: Core Modules | Weeks 5-8 | Resume generator (4 templates), form automation, CAPTCHA handling, orchestrator with circuit breaker, debate system |
| Phase 3: Integration | Weeks 9-12 | Company intelligence, email monitor + outbound, Google Sheets report, Atlas Full-Text Search, dashboard, deployment |
| Phase 4: Advanced | Weeks 13-16 | Security hardening, IP rotation, proxy pool, feedback loop, LoRA fine-tuning, portfolio documentation |
| Phase 5: Elite Features | Weeks 17-20 | Resume parser, referral intelligence, follow-up automation, salary negotiation, scheduling assistant, skill gap tracker, browser extension, mobile PWA |

**Total: 20 weeks (5 months) at 3-4 hours per day**

> Phase 5 is optional and should only begin after the core system (Phases 1-4) is running in production with real data. The first four phases deliver a complete, production-grade system. Phase 5 makes it elite.

---

# ACTIVE RECALL — MASTER QUESTIONS

Answer these at the end of every week. If you cannot answer them without looking, you need to review that week's material.

**Foundations:**
1. Why does your system use async Python and what would break if it were synchronous?
2. Why does MongoDB store embeddings alongside text in the same document?
3. What is the difference between BeautifulSoup and Playwright and when does each get used?
4. Why do you use environment variables instead of hardcoding API keys?

**Eligibility Matching:**
5. What are the five dimensions of the weighted eligibility scorer and what is the maximum score for each?
6. What is the difference between a near match and a hard mismatch? Why does the system treat them differently instead of just filtering both out?
7. Why does a 65% score caused by a location mismatch deserve different treatment than a 65% score caused by a missing core skill?

**System Architecture:**
8. Describe the complete data flow from a WhatsApp paste to a submitted application.
9. Why is one MongoDB cluster sufficient to replace ChromaDB, Redis, and a graph database?
10. How does the Orchestrator Agent decide which tools to use?
11. What is the ReAct pattern and why is it used for the orchestrator?

**Reliability and Resilience:**
12. What are the three states of a circuit breaker and what triggers each transition?
13. If the LLM model fails, what is the fallback path your system takes?
14. What is the difference between trust level 1 and trust level 2 for auto-submission and when does a platform get promoted?
15. What does the submission verification step check and why does it matter?

**AI Layer:**
16. What is an embedding and why does mathematical similarity of number arrays correspond to semantic similarity of text?
17. What is the difference between vector search and full-text search? Give a concrete example of when you use each in your system.
18. What is hybrid search and why does it produce better results than either vector or full-text alone?
19. What is the difference between vector search and GraphRAG and when does each produce better results?
20. Why are there 6 debate agents rather than 1 agent doing all the analysis?
21. How does the Technical Expert agent get real knowledge beyond its training data?

**Resume Generation:**
22. Why do you need four base LaTeX templates instead of one? What specifically is different between the frontend and backend templates?
23. What is the template selector function and what field from the JD parser does it read?
24. How does resume version history protect you if you need to look back at what you sent to a company?

**Notifications and Reporting:**
25. What events trigger both Telegram AND email simultaneously, and which trigger Telegram only?
26. Why does the Google Sheets API use a service account instead of your regular Google login?
27. What is a service account and why must its credentials JSON never be committed to GitHub?

**Security and Production:**
28. List 5 signals that distinguish an automated browser from a human browser.
29. What is the session warmup protocol and what does each step in it accomplish?
30. When does your system actually need IP rotation versus when is your direct connection sufficient?
31. How does the proxy pool manager decide which proxy to use for a given domain?
32. Why must sensitive MongoDB fields be encrypted at the field level, not just at the database level?
33. What is LoRA fine-tuning and why does it not require as much compute as full fine-tuning?

**CAPTCHA Handling:**
34. What is the difference between reCAPTCHA v2 and v3? How does your system handle each?
35. What is the Cloudflare interstitial challenge and why does playwright-stealth usually pass it automatically?
36. When would you choose the 2captcha auto-solve path versus the Telegram pause path?

---

# DOCUMENTATION STRATEGY

**Daily habit:**
At the end of every day, write 3-5 sentences in a `DEVLOG.md` file:
- What you built
- What problem you solved
- What you learned
- What you struggled with

**Weekly habit:**
Every Sunday, update your main README to reflect the current state of the project.

**Per component:**
When you finish a module, write a one-page `docs/component-name.md` explaining:
- What it does
- How it works internally
- What decisions you made and why
- What the inputs and outputs are
- How to test it

**This documentation is not just for others. It is for your future self when you interview and need to explain your architectural decisions.**

---

*This roadmap is a living document. As you build each module, you will discover details not covered here. Add them. The final version of this document should contain everything you actually learned, not just what was planned.*

*Last updated: Gap Analysis Applied — Version 2.0*
*Coverage: 54% → 94% of all planned features now taught end-to-end*
*Gaps fixed: Weighted scoring, multi-template resume, Google Sheets, email outbound, Atlas Full-Text Search, circuit breaker pattern, CAPTCHA auto-solve, auto-submit trust levels, IP rotation proxy pool, Phase 5 future features*