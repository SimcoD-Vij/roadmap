# 🧠 THE UNIFIED AI/ML/DL/AGENTIC AI GRANDMASTER ROADMAP
### From Zero → MNC-Grade Production Engineer | 180-Day Complete Blueprint

> **Philosophy:** You are not just learning tools. You are building the *engineering intuition* to understand WHY a system was designed a certain way, HOW it fails, and HOW to fix it at production scale. Every day connects to the next. Nothing is isolated.

---

## 📐 PART 0 — READ THIS FIRST: How to Use This Roadmap

### Who This Is For
You start with **zero knowledge** in programming, databases, hardware, and system design. By the end, you will be capable of designing, building, and deploying production-grade AI systems that meet MNC standards — fully using **free and open-source technologies only**.

### Daily Commitment
- **Morning (2 hrs):** Theory + conceptual study
- **Afternoon (2 hrs):** Hands-on coding + implementation
- **Evening (1 hr):** Documentation + active recall + GitHub commit

### Documentation-First Rule
Every single day ends with a **written log**. This is not optional. Your documentation IS your proof of work.

### Documentation Platforms (Free)
| Platform | What to Document | Link |
|---|---|---|
| **GitHub** | All code, README per project, commit daily | github.com |
| **Hashnode** | Technical blog posts (1 per week minimum) | hashnode.com |
| **Dev.to** | Short daily learnings, concept notes | dev.to |
| **Notion** | Personal notes, architecture diagrams, daily logs | notion.so |
| **LinkedIn** | Weekly milestone posts with GitHub links | linkedin.com |
| **Obsidian** | Linked notes for conceptual recall | obsidian.md |

### GitHub Strategy (Start Day 1)
```
your-github/
├── ai-ml-dl-journey/           ← Main repo, public
│   ├── daily-logs/             ← One .md file per day
│   ├── phase-1-foundations/
│   ├── phase-2-classical-ml/
│   ├── phase-3-deep-learning/
│   ├── phase-4-nlp-transformers/
│   ├── phase-5-agentic-ai/
│   ├── phase-6-mlops-production/
│   └── capstone-projects/
```

**Commit rule:** Even if you only wrote notes today, commit the notes. Recruiters see the green squares. Consistency > quality in early stages.

---

## 🏗️ PART 1 — OVERALL SYSTEM ARCHITECTURE

> Before learning anything, understand the WHOLE MACHINE you are building. This is your north star. Every concept you learn maps to one of these layers.

```
┌─────────────────────────────────────────────────────────────────┐
│                    🌐 USER / CLIENT LAYER                        │
│         Web App  |  Mobile App  |  API Consumer  |  Dashboard   │
└──────────────────────────────┬──────────────────────────────────┘
                               │ HTTPS / gRPC / WebSocket
┌──────────────────────────────▼──────────────────────────────────┐
│                   ⚙️ API GATEWAY LAYER                           │
│        FastAPI / Nginx / Kong / Rate Limiting / Auth             │
└──────────────────────────────┬──────────────────────────────────┘
                               │
┌──────────────────────────────▼──────────────────────────────────┐
│                🤖 AGENTIC AI ORCHESTRATION LAYER                 │
│    LangChain / LangGraph / AutoGen / CrewAI / Custom Agents      │
│    Memory | Planning | Tool Use | Multi-Agent Coordination       │
└────────┬──────────────────────────────────────────┬─────────────┘
         │                                          │
┌────────▼──────────┐                    ┌──────────▼──────────────┐
│  🧠 ML/DL MODEL   │                    │  🔧 TOOL EXECUTION      │
│  SERVING LAYER    │                    │  LAYER                  │
│  TorchServe /     │                    │  Code Executor /        │
│  BentoML /        │                    │  Web Search /           │
│  Triton Inference │                    │  DB Queries /           │
│  vLLM / Ollama    │                    │  File System /          │
└────────┬──────────┘                    │  External APIs          │
         │                               └─────────────────────────┘
┌────────▼──────────────────────────────────────────────────────────┐
│                   📊 DATA & FEATURE LAYER                          │
│  Feature Store (Feast) | Vector DB (ChromaDB/Qdrant) |            │
│  Redis Cache | PostgreSQL | MongoDB | Data Lake (MinIO)           │
└────────┬──────────────────────────────────────────────────────────┘
         │
┌────────▼──────────────────────────────────────────────────────────┐
│                  🔄 DATA PIPELINE LAYER                            │
│   Apache Airflow (Orchestration) | Kafka (Streaming) |            │
│   dbt (Transformation) | Great Expectations (Validation)          │
└────────┬──────────────────────────────────────────────────────────┘
         │
┌────────▼──────────────────────────────────────────────────────────┐
│                  📈 MLOPS / MONITORING LAYER                       │
│   MLflow (Experiment Tracking) | DVC (Data Versioning) |          │
│   Prometheus + Grafana (Monitoring) | Evidently (Drift Detection) │
└────────┬──────────────────────────────────────────────────────────┘
         │
┌────────▼──────────────────────────────────────────────────────────┐
│                  🐳 INFRASTRUCTURE LAYER                           │
│   Docker | Docker Compose | Kubernetes (k3s locally) |            │
│   GitHub Actions (CI/CD) | Terraform (IaC) | Linux (Ubuntu)       │
└───────────────────────────────────────────────────────────────────┘
```

### Why This Architecture Matters
- **Separation of Concerns:** Each layer can be upgraded independently. The ML model can change without touching the API gateway.
- **Scalability:** Each layer scales horizontally. If inference is slow, you scale the model serving layer only.
- **Observability:** Every layer is monitored. Production systems don't just work — they are *observed*.
- **You will build every single layer** from scratch over these 180 days. On Day 1, you don't understand any of this. On Day 180, you will have built it all.

---

## 📅 PART 2 — THE 180-DAY DAY-BY-DAY ROADMAP

---

## 🔵 PHASE 1: FOUNDATIONS (Days 1–30)
### *"Building the Brain Before the Machine"*

**Phase Goal:** Master Python, mathematics for ML, data manipulation, and your development environment. Understand the WHY behind every tool.

**Why This Phase Exists:** You cannot build a skyscraper on sand. Every ML system is just math + code. Without these foundations, you will copy-paste code forever without understanding it.

---

### WEEK 1 — Your Development Environment + Python Foundations (Days 1–7)

---

#### 📅 DAY 1 — Setup + Linux + Git Foundations

**Morning Theory (2 hrs):**
- What is Linux and why do MNCs use it? (Ubuntu is the standard for AI/ML servers)
- Filesystem structure: `/home`, `/etc`, `/var`, `/tmp` — what lives where and why
- Terminal basics: `ls`, `cd`, `mkdir`, `cp`, `mv`, `rm`, `cat`, `grep`, `chmod`
- What is Git? What is version control? Why does it exist?
- Git mental model: working directory → staging area → repository → remote

**Afternoon Hands-On (2 hrs):**
```bash
# Install Ubuntu (WSL2 on Windows, or native)
# Install: git, python3, pip, vscode, jupyter

# Git setup
git config --global user.name "Your Name"
git config --global user.email "your@email.com"

# Create your journey repo
mkdir ai-ml-dl-journey && cd ai-ml-dl-journey
git init
mkdir daily-logs phase-1-foundations
touch README.md daily-logs/day-001.md
git add . && git commit -m "Day 1: Journey begins"
git remote add origin https://github.com/yourusername/ai-ml-dl-journey
git push -u origin main
```

**Evening Documentation (1 hr):**

Write `daily-logs/day-001.md`:
```markdown
# Day 1 Log — [Date]

## What I Learned
- Linux is used because it is stable, free, and production servers run it
- Git tracks changes so you never lose work and can collaborate
- ...

## Commands I Used Today
- git init, git add, git commit, git push

## What Confused Me
- [Write honestly. This builds self-awareness.]

## Tomorrow's Goal
- Python data types and control flow
```

**Active Recall Questions (answer in your log):**
1. Why does Git have a staging area? Why not commit directly?
2. What is the difference between `git pull` and `git fetch`?
3. What does `chmod 755` mean?

**Beginner Mistake to Avoid:** Do NOT skip documentation "because it's just day 1." The habit must start NOW.

---

#### 📅 DAY 2 — Python: Data Types, Control Flow, Functions

**Morning Theory (2 hrs):**
- Python's design philosophy: "Explicit is better than implicit"
- Why Python dominates AI/ML: readability + ecosystem (NumPy, PyTorch, etc.)
- Data types: `int`, `float`, `str`, `bool`, `None`
- Collections: `list`, `tuple`, `dict`, `set` — differences and when to use which
- Control flow: `if/elif/else`, `for`, `while`, `break`, `continue`
- Functions: `def`, arguments, return values, scope, `*args`, `**kwargs`

**Afternoon Hands-On (2 hrs):**
```python
# Create: phase-1-foundations/day02_python_basics.py

# Task 1: Statistics calculator
def calculate_stats(numbers: list) -> dict:
    n = len(numbers)
    mean = sum(numbers) / n
    sorted_nums = sorted(numbers)
    median = sorted_nums[n // 2] if n % 2 else (sorted_nums[n//2-1] + sorted_nums[n//2]) / 2
    from collections import Counter
    mode = Counter(numbers).most_common(1)[0][0]
    variance = sum((x - mean) ** 2 for x in numbers) / n
    std_dev = variance ** 0.5
    return {"mean": mean, "median": median, "mode": mode, "std_dev": std_dev}

# Task 2: FizzBuzz (classic interview warmup)
# Task 3: Dictionary frequency counter from a sentence
# Task 4: List comprehension — squares of even numbers from 1-100
```

**Active Recall Questions:**
1. A `tuple` vs a `list` — give a real-world example of when you'd use each.
2. What happens when you modify a list inside a function? Why?
3. What is a dictionary's time complexity for lookup? Why?

**Mini-Assignment:** Write a function that takes a sentence and returns the top 3 most frequent words as a dictionary. Commit to GitHub.

---

#### 📅 DAY 3 — Python: OOP + File I/O + Error Handling

**Morning Theory (2 hrs):**
- Why OOP? Real systems are organized into objects (a `Model`, a `DataPipeline`, an `Agent`)
- Classes: `__init__`, attributes, methods, `self`
- Inheritance: why it exists (DRY principle — Don't Repeat Yourself)
- `try/except/finally` — production code never crashes silently
- File I/O: reading/writing `.txt`, `.csv`, `.json`
- Context managers: `with open(...) as f:`

**Afternoon Hands-On (2 hrs):**
```python
# Create: phase-1-foundations/day03_oop.py

import json, csv
from pathlib import Path

class DataLogger:
    """A simple logger that writes daily study logs to JSON."""
    
    def __init__(self, log_file: str):
        self.log_file = Path(log_file)
        self.logs = self._load()
    
    def _load(self) -> list:
        if self.log_file.exists():
            with open(self.log_file) as f:
                return json.load(f)
        return []
    
    def add_entry(self, day: int, topics: list, hours: float, notes: str):
        entry = {"day": day, "topics": topics, "hours": hours, "notes": notes}
        self.logs.append(entry)
        self._save()
    
    def _save(self):
        with open(self.log_file, 'w') as f:
            json.dump(self.logs, f, indent=2)
    
    def summary(self) -> dict:
        total_hours = sum(e['hours'] for e in self.logs)
        return {"total_days": len(self.logs), "total_hours": total_hours}

# Use the logger for your own study tracking!
logger = DataLogger("study_log.json")
logger.add_entry(day=3, topics=["OOP", "File I/O"], hours=5, notes="Classes make sense now")
print(logger.summary())
```

**Mini-Project: Build Your Personal Study Tracker CLI**
A command-line tool where you log your daily learning. This will actually be used for the rest of the roadmap.

---

#### 📅 DAY 4 — Python: Modules, Virtual Environments, pip

**Morning Theory (2 hrs):**
- What is a Python module? Package? Namespace?
- Why virtual environments exist: project A needs TensorFlow 2.10, project B needs 2.15 — they conflict
- `pip`, `pip freeze`, `requirements.txt`
- Important built-in modules: `os`, `sys`, `datetime`, `collections`, `itertools`, `functools`
- `__name__ == "__main__"` — why this exists

**Afternoon Hands-On (2 hrs):**
```bash
# Create virtual environment for every project — always
python3 -m venv .venv
source .venv/bin/activate  # Linux/Mac
# .venv\Scripts\activate   # Windows

pip install numpy pandas matplotlib jupyter
pip freeze > requirements.txt
git add requirements.txt && git commit -m "Add Phase 1 dependencies"
```

```python
# Explore collections module
from collections import defaultdict, Counter, deque, namedtuple

# Counter: word frequency (used in NLP pipelines)
text = "to be or not to be that is the question"
word_counts = Counter(text.split())
print(word_counts.most_common(3))

# defaultdict: building adjacency lists (used in graph algorithms)
graph = defaultdict(list)
```

**Active Recall Questions:**
1. What is the difference between a module and a package?
2. Why should you never install packages globally for a project?
3. What does `*` do in `from module import *` and why is it bad practice?

---

#### 📅 DAY 5 — NumPy: The Engine Under ML

**Morning Theory (2 hrs):**
- Why NumPy? Pure Python loops are 100x slower than NumPy vectorized operations
- The `ndarray` object: shape, dtype, strides
- Vectorization: "thinking in arrays" not "thinking in loops"
- Broadcasting rules — how NumPy handles different-shaped arrays
- Why everything in ML is just matrix math: weights, activations, gradients are all NumPy arrays at the core

**Afternoon Hands-On (2 hrs):**
```python
import numpy as np

# Understand shape and dtype
arr_1d = np.array([1, 2, 3, 4, 5])
arr_2d = np.zeros((3, 4))
arr_rand = np.random.randn(100, 50)  # 100 samples, 50 features — like real data

print(arr_rand.shape)   # (100, 50)
print(arr_rand.dtype)   # float64

# Vectorized stats — this is how you compute loss functions in ML
mean = np.mean(arr_rand, axis=0)   # mean of each feature
std  = np.std(arr_rand, axis=0)
normalized = (arr_rand - mean) / std  # This IS feature normalization!

# Matrix multiplication — this is what neural network layers do
weights = np.random.randn(50, 10)    # 50 inputs → 10 neurons
output = arr_rand @ weights           # (100, 50) @ (50, 10) = (100, 10)
print("Layer output shape:", output.shape)
```

**Architecture Insight:** When you write `output = input @ weights` — that IS a neural network layer. One line. The entire complexity of "deep learning" is just many of these stacked.

**Active Recall Questions:**
1. What is broadcasting? Give an example where shape `(100,50)` and `(50,)` interact.
2. Why is matrix multiplication `@` the fundamental operation of deep learning?
3. What is the difference between `np.dot()` and `@` operator?

---

#### 📅 DAY 6 — Pandas: Data as a First-Class Citizen

**Morning Theory (2 hrs):**
- Why Pandas? 80% of ML work is data wrangling, not modeling
- Series vs DataFrame — when to use each
- Index: why Pandas uses labeled indices (not just positions)
- Missing data: `NaN` — why it exists, how it propagates
- The split-apply-combine pattern: `groupby()` — the most important operation

**Afternoon Hands-On (2 hrs):**
```python
import pandas as pd
import numpy as np

# Load a real dataset
df = pd.read_csv('https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv')

# The 5-step EDA ritual (do this for EVERY dataset you encounter)
print("=== STEP 1: Shape ===")
print(df.shape)  # (rows, columns)

print("=== STEP 2: Data Types ===")
print(df.dtypes)

print("=== STEP 3: Missing Values ===")
missing = df.isnull().sum()
missing_pct = (missing / len(df) * 100).round(2)
print(pd.concat([missing, missing_pct], axis=1, keys=['Count', 'Percentage']))

print("=== STEP 4: Statistics ===")
print(df.describe())

print("=== STEP 5: Sample Data ===")
print(df.head(10))

# Groupby — survival rate by class and gender
survival_analysis = df.groupby(['Pclass', 'Sex'])['Survived'].agg(['mean', 'count'])
print("\nSurvival by Class & Gender:")
print(survival_analysis)
```

**Active Recall Questions:**
1. What is the difference between `.loc[]` and `.iloc[]`?
2. When would you use `.apply()` vs vectorized operations? Which is faster?
3. What does `df.groupby('col').transform('mean')` do differently from `.agg('mean')`?

---

#### 📅 DAY 7 — Week 1 Project: Data Analysis CLI Tool

**Project: Personal Expense Analyzer**

**Problem:** Build a command-line tool that reads a CSV of expenses, performs statistical analysis, and generates a text report — documenting it fully on GitHub.

```
expenses.csv format: date, category, amount, description
```

**Requirements:**
- Load and validate the CSV
- Show: total spend, spend by category, top 5 expenses, month-over-month comparison
- Detect anomalies (expenses > 2 std deviations above mean)
- Export a JSON summary report
- Full README with setup instructions, usage examples, and what you learned

**GitHub Documentation for this project:**
```markdown
# Expense Analyzer

## What This Is
A CLI data analysis tool built while learning Python + Pandas fundamentals.

## What I Learned Building This
- Pandas groupby is the equivalent of SQL GROUP BY
- Always validate input data before processing
- Missing values in financial data should be 0, not NaN

## Architecture Decision
Used Pandas over pure Python loops because [explain]

## How to Run
[clear instructions]
```

**Recruiter Signal:** This project shows Python proficiency + data thinking + documentation habit. Commit it with a clean README.

---

### WEEK 2 — Mathematics for ML (Days 8–14)

> **Why Math?** You can copy-paste TensorFlow code forever. But when your model behaves strangely, only math tells you why. Math = debugging superpower.

---

#### 📅 DAY 8 — Linear Algebra Part 1: Vectors and Matrices

**Morning Theory (2 hrs):**
- A vector is just a list of numbers with a direction. In ML, a data point IS a vector.
- A matrix is a 2D array. A dataset IS a matrix (rows=samples, columns=features).
- Vector operations: addition, dot product, magnitude
- The dot product measures **similarity** — this is how recommendation systems work
- Matrix multiplication: dimensions must match: `(m×k) × (k×n) = (m×n)`

**Afternoon Hands-On:**
```python
import numpy as np

# Dot product as similarity (used in cosine similarity, attention mechanisms)
user_preferences = np.array([5, 1, 3, 4, 2])   # movie genre ratings
movie_a = np.array([4, 1, 2, 5, 1])
movie_b = np.array([1, 5, 1, 1, 4])

similarity_a = np.dot(user_preferences, movie_a)
similarity_b = np.dot(user_preferences, movie_b)
print(f"Movie A similarity: {similarity_a}")  # higher = better recommendation
print(f"Movie B similarity: {similarity_b}")

# Matrix multiplication — this IS a neural network forward pass
X = np.random.randn(100, 5)  # 100 data points, 5 features
W = np.random.randn(5, 3)    # 3 neurons in the next layer
b = np.random.randn(3)       # bias
output = X @ W + b           # (100, 3) — 100 predictions with 3 values each
```

**Architecture Insight:** When Transformers compute "attention," they are computing dot products between query and key vectors. The similarity score IS a dot product.

---

#### 📅 DAY 9 — Linear Algebra Part 2: Eigenvalues, Decomposition

**Morning Theory (2 hrs):**
- Eigenvalues/eigenvectors: what directions does a transformation "preserve"?
- PCA (Principal Component Analysis) = eigendecomposition of the covariance matrix
- Why PCA matters: compress 1000 features to 50 while keeping 95% of information
- Covariance matrix: how correlated are your features?

**Afternoon Hands-On:**
```python
import numpy as np

# Manual PCA from scratch — understand what sklearn.PCA does internally
np.random.seed(42)
X = np.random.randn(200, 3)
X[:, 1] = X[:, 0] * 0.8 + np.random.randn(200) * 0.2  # add correlation

# Step 1: Center the data
X_centered = X - X.mean(axis=0)

# Step 2: Compute covariance matrix
cov_matrix = np.cov(X_centered.T)  # (3, 3)
print("Covariance Matrix:\n", cov_matrix)

# Step 3: Eigendecomposition
eigenvalues, eigenvectors = np.linalg.eig(cov_matrix)
print("Eigenvalues:", eigenvalues)  # How much variance each PC explains

# Step 4: Sort by eigenvalue (highest variance first)
idx = eigenvalues.argsort()[::-1]
eigenvalues = eigenvalues[idx]
eigenvectors = eigenvectors[:, idx]

# Step 5: Project to 2D
X_pca = X_centered @ eigenvectors[:, :2]
print("Reduced shape:", X_pca.shape)  # (200, 2) — compressed from 3D to 2D

# Verify: explained variance ratio
explained_variance = eigenvalues / eigenvalues.sum()
print("Variance explained by 2 components:", explained_variance[:2].sum())
```

---

#### 📅 DAY 10 — Calculus: Derivatives and Gradients

**Morning Theory (2 hrs):**
- A derivative measures "how does the output change when I nudge the input?"
- Gradient = derivative of a multi-variable function (a vector of partial derivatives)
- Gradient descent: walk downhill on the loss surface by subtracting the gradient
- Chain rule: how backpropagation works — gradients flow backwards through layers
- Learning rate: step size. Too big = overshoot. Too small = never converge.

**Afternoon Hands-On:**
```python
import numpy as np
import matplotlib.pyplot as plt

# Gradient descent from scratch — this is the core of ALL ML training
def loss_function(w):
    """Simple quadratic loss: L(w) = (w - 3)^2 + 5"""
    return (w - 3)**2 + 5

def gradient(w):
    """dL/dw = 2*(w - 3)"""
    return 2 * (w - 3)

# Training loop — this exact pattern runs inside PyTorch/TensorFlow
w = 10.0          # start far from minimum
learning_rate = 0.1
history = []

for step in range(50):
    loss = loss_function(w)
    grad = gradient(w)
    w = w - learning_rate * grad  # gradient descent update
    history.append({'step': step, 'w': w, 'loss': loss, 'grad': grad})
    if step % 10 == 0:
        print(f"Step {step}: w={w:.4f}, loss={loss:.4f}, gradient={grad:.4f}")

print(f"\nConverged to w ≈ {w:.4f} (true minimum is w=3)")

# Plot convergence
steps = [h['step'] for h in history]
losses = [h['loss'] for h in history]
plt.figure(figsize=(10, 4))
plt.subplot(1, 2, 1)
plt.plot(steps, losses)
plt.title('Loss vs Steps')
plt.xlabel('Step'); plt.ylabel('Loss')
plt.subplot(1, 2, 2)
ws = np.linspace(-2, 12, 100)
plt.plot(ws, loss_function(ws), 'b-', label='Loss surface')
w_history = [h['w'] for h in history]
plt.plot(w_history, [loss_function(w) for w in w_history], 'ro-', label='Gradient descent path')
plt.legend()
plt.title('Descent Path on Loss Surface')
plt.savefig('gradient_descent.png')
```

**Architecture Insight:** PyTorch's `.backward()` computes gradients automatically using the chain rule. When you understand this manually, you can debug training failures that others can't.

---

#### 📅 DAY 11 — Probability and Statistics

**Morning Theory (2 hrs):**
- Probability: how confident is our model? Logistic regression outputs a probability.
- Normal/Gaussian distribution: why it appears everywhere (Central Limit Theorem)
- Bayes' Theorem: `P(A|B) = P(B|A) * P(A) / P(B)` — the foundation of Naive Bayes, Bayesian inference
- Hypothesis testing: is this pattern real or random noise?
- Expected value, variance, standard deviation — the language of uncertainty

**Afternoon Hands-On:**
```python
import numpy as np
from scipy import stats
import matplotlib.pyplot as plt

# Simulate a dataset — imagine these are model prediction errors
np.random.seed(42)
errors = np.random.normal(loc=0, scale=2, size=1000)  # mean=0, std=2

# Hypothesis test: Is our model biased? (mean error should be ~0)
t_stat, p_value = stats.ttest_1samp(errors, popmean=0)
print(f"T-statistic: {t_stat:.4f}")
print(f"P-value: {p_value:.4f}")
if p_value > 0.05:
    print("✅ No significant bias (fail to reject H0)")
else:
    print("⚠️ Model is biased! (reject H0)")

# Confidence interval for the mean
ci = stats.t.interval(0.95, df=len(errors)-1, loc=np.mean(errors), scale=stats.sem(errors))
print(f"95% CI for mean error: [{ci[0]:.4f}, {ci[1]:.4f}]")
```

---

#### 📅 DAY 12 — Data Visualization: Matplotlib + Seaborn

**Morning Theory (2 hrs):**
- Why visualization? "A picture is worth 1000 numbers."
- The Figure/Axes hierarchy in Matplotlib
- When to use: histogram, boxplot, scatter, heatmap, violin plot, pairplot
- Seaborn: statistical visualization library — built on Matplotlib but for stats
- Visualization as communication: charts in reports vs charts for exploration

**Afternoon Hands-On:**
```python
import matplotlib.pyplot as plt
import seaborn as sns
import pandas as pd
import numpy as np

# Load Titanic dataset
df = pd.read_csv('https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv')

fig, axes = plt.subplots(2, 3, figsize=(15, 10))
fig.suptitle('Titanic Dataset — Exploratory Visual Analysis', fontsize=16)

# 1. Age distribution
axes[0,0].hist(df['Age'].dropna(), bins=30, color='steelblue', edgecolor='white')
axes[0,0].set_title('Age Distribution')
axes[0,0].set_xlabel('Age'); axes[0,0].set_ylabel('Count')

# 2. Survival by class
survival_by_class = df.groupby('Pclass')['Survived'].mean()
axes[0,1].bar(survival_by_class.index, survival_by_class.values, color=['#e74c3c','#f39c12','#2ecc71'])
axes[0,1].set_title('Survival Rate by Class')
axes[0,1].set_xlabel('Passenger Class'); axes[0,1].set_ylabel('Survival Rate')

# 3. Age vs Fare scatter
axes[0,2].scatter(df['Age'], df['Fare'], c=df['Survived'], cmap='RdYlGn', alpha=0.5)
axes[0,2].set_title('Age vs Fare (color=Survived)')

# 4. Correlation heatmap
corr = df[['Age','Fare','Pclass','SibSp','Parch','Survived']].corr()
sns.heatmap(corr, annot=True, fmt='.2f', cmap='coolwarm', ax=axes[1,0])
axes[1,0].set_title('Feature Correlation Heatmap')

# 5. Survival by gender
survival_by_gender = df.groupby('Sex')['Survived'].mean()
axes[1,1].bar(survival_by_gender.index, survival_by_gender.values, color=['#3498db','#e91e8c'])
axes[1,1].set_title('Survival Rate by Gender')

# 6. Age boxplot by survival
df.boxplot(column='Age', by='Survived', ax=axes[1,2])
axes[1,2].set_title('Age Distribution by Survival')

plt.tight_layout()
plt.savefig('titanic_eda.png', dpi=150)
print("Saved: titanic_eda.png")
```

---

#### 📅 DAY 13 — SQL and Databases

**Morning Theory (2 hrs):**
- Why SQL? ML engineers spend 40% of their time writing SQL queries
- Relational databases: tables, rows, columns, primary keys, foreign keys
- SQL vs NoSQL: when to use each (structured vs unstructured data)
- Core SQL: `SELECT`, `WHERE`, `GROUP BY`, `ORDER BY`, `JOIN`, `HAVING`
- Window functions: `ROW_NUMBER`, `LAG`, `LEAD` — used for time-series ML features
- SQLite: a serverless database — perfect for learning and small projects

**Afternoon Hands-On:**
```python
import sqlite3
import pandas as pd

# Create a database with ML training metadata (this is what MLflow stores internally)
conn = sqlite3.connect('ml_experiments.db')
cursor = conn.cursor()

cursor.executescript("""
CREATE TABLE IF NOT EXISTS experiments (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    name TEXT NOT NULL,
    model_type TEXT,
    created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
);

CREATE TABLE IF NOT EXISTS runs (
    id INTEGER PRIMARY KEY AUTOINCREMENT,
    experiment_id INTEGER,
    accuracy REAL,
    loss REAL,
    learning_rate REAL,
    epochs INTEGER,
    duration_seconds REAL,
    FOREIGN KEY (experiment_id) REFERENCES experiments(id)
);
""")

# Insert sample data
cursor.execute("INSERT INTO experiments (name, model_type) VALUES (?, ?)", 
               ("titanic-logistic", "logistic_regression"))
exp_id = cursor.lastrowid

runs_data = [
    (exp_id, 0.78, 0.45, 0.01, 100, 12.3),
    (exp_id, 0.81, 0.38, 0.001, 200, 24.1),
    (exp_id, 0.83, 0.35, 0.0001, 500, 61.5),
]
cursor.executemany("INSERT INTO runs VALUES (NULL,?,?,?,?,?,?)", runs_data)
conn.commit()

# Query: find the best run
best_run = pd.read_sql_query("""
    SELECT r.*, e.name as experiment_name
    FROM runs r
    JOIN experiments e ON r.experiment_id = e.id
    ORDER BY accuracy DESC
    LIMIT 1
""", conn)
print("Best run:\n", best_run)
conn.close()
```

---

#### 📅 DAY 14 — Week 2 Project: Mini EDA Report Generator

**Project: Automated EDA Report for Any CSV Dataset**

Build a Python script that:
1. Accepts any CSV file as input
2. Performs full statistical analysis
3. Generates a set of visualizations
4. Writes everything to an HTML report file
5. Documents findings in a Markdown file

**Real-World Application:** Data scientists do this every time they get a new dataset. This tool automates their first 2 hours of work.

**Active Recall Test (must answer before committing):**
1. What does the standard deviation tell you that the mean doesn't?
2. Why does a correlation heatmap help with feature selection?
3. What's the difference between a histogram and a KDE plot?

---

### WEEK 3 — Classical Machine Learning (Days 15–21)

---

#### 📅 DAY 15 — The ML Mindset: From Data to Predictions

**Morning Theory (2 hrs):**
- What IS machine learning? Finding patterns in data that generalize to unseen data.
- Supervised vs Unsupervised vs Reinforcement Learning
- The ML workflow: Data → Features → Model → Evaluate → Deploy
- Overfitting vs Underfitting — the fundamental tradeoff
- Training set, validation set, test set — WHY 3 sets? (common beginner mistake: only 2)
- Cross-validation: why it gives more reliable estimates
- The bias-variance tradeoff: simple models underfit (high bias), complex models overfit (high variance)

**Architecture Decision Insight:**
> "In production, your test set is tomorrow's reality. Your model will see data it has never seen. The entire art of ML is training on the past to predict the future."

---

#### 📅 DAY 16 — Linear Regression: The Foundation

**Morning Theory (2 hrs):**
- Linear regression assumes: output = weighted sum of inputs + noise
- Cost function: Mean Squared Error (MSE) — why squared? (differentiable + penalizes large errors)
- Normal equation vs gradient descent: when to use which (size of data matters)
- Assumptions: linearity, independence, homoscedasticity, normality of residuals
- When linear regression fails and what to do about it

**Afternoon Hands-On — Build From Scratch FIRST:**
```python
import numpy as np
import matplotlib.pyplot as plt

class LinearRegressionFromScratch:
    """Linear Regression using Gradient Descent — built from first principles."""
    
    def __init__(self, learning_rate=0.01, epochs=1000):
        self.lr = learning_rate
        self.epochs = epochs
        self.weights = None
        self.bias = None
        self.loss_history = []
    
    def fit(self, X: np.ndarray, y: np.ndarray):
        n_samples, n_features = X.shape
        self.weights = np.zeros(n_features)
        self.bias = 0.0
        
        for epoch in range(self.epochs):
            # Forward pass
            y_pred = X @ self.weights + self.bias
            
            # Compute MSE loss
            loss = np.mean((y_pred - y) ** 2)
            self.loss_history.append(loss)
            
            # Backward pass — compute gradients
            dW = (2/n_samples) * X.T @ (y_pred - y)
            db = (2/n_samples) * np.sum(y_pred - y)
            
            # Update parameters
            self.weights -= self.lr * dW
            self.bias    -= self.lr * db
        
        return self
    
    def predict(self, X: np.ndarray) -> np.ndarray:
        return X @ self.weights + self.bias
    
    def score(self, X: np.ndarray, y: np.ndarray) -> float:
        y_pred = self.predict(X)
        ss_res = np.sum((y - y_pred) ** 2)
        ss_tot = np.sum((y - np.mean(y)) ** 2)
        return 1 - (ss_res / ss_tot)  # R² score

# Test on synthetic data
np.random.seed(42)
X = np.random.randn(200, 3)
true_w = np.array([2.0, -1.5, 3.0])
y = X @ true_w + 5 + np.random.randn(200) * 0.5

model = LinearRegressionFromScratch(learning_rate=0.05, epochs=500)
model.fit(X, y)
print(f"R² Score: {model.score(X, y):.4f}")
print(f"Learned weights: {model.weights}")
print(f"True weights: {true_w}")
```

---

#### 📅 DAY 17 — Logistic Regression + Classification Metrics

**Morning Theory (2 hrs):**
- Logistic regression for binary classification: output is a probability between 0 and 1
- Sigmoid function: `σ(z) = 1/(1+e^{-z})` — maps any value to [0,1]
- Binary cross-entropy loss (log loss): why not MSE for classification?
- Decision boundary: where probability = 0.5
- Confusion matrix: TP, TN, FP, FN — each quadrant means something real
- Precision vs Recall tradeoff: cancer detection (recall) vs spam filter (precision)
- F1 Score: harmonic mean of precision and recall
- ROC-AUC: how good is the model across all threshold values

**Afternoon Hands-On:**
```python
import numpy as np
from sklearn.linear_model import LogisticRegression
from sklearn.model_selection import train_test_split
from sklearn.metrics import (classification_report, confusion_matrix, 
                             roc_auc_score, roc_curve)
from sklearn.preprocessing import StandardScaler
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

# Load Titanic
df = pd.read_csv('https://raw.githubusercontent.com/datasciencedojo/datasets/master/titanic.csv')

# Feature engineering
df = df[['Survived', 'Pclass', 'Sex', 'Age', 'SibSp', 'Parch', 'Fare']].copy()
df['Sex'] = (df['Sex'] == 'male').astype(int)
df['Age'].fillna(df['Age'].median(), inplace=True)
df.dropna(inplace=True)

X = df.drop('Survived', axis=1).values
y = df['Survived'].values

X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2, random_state=42)
scaler = StandardScaler()
X_train = scaler.fit_transform(X_train)
X_test = scaler.transform(X_test)

model = LogisticRegression(max_iter=1000)
model.fit(X_train, y_train)
y_pred = model.predict(X_test)
y_prob = model.predict_proba(X_test)[:, 1]

print(classification_report(y_test, y_pred, target_names=['Died', 'Survived']))
print(f"ROC-AUC: {roc_auc_score(y_test, y_prob):.4f}")

# Confusion matrix plot
cm = confusion_matrix(y_test, y_pred)
plt.figure(figsize=(6, 5))
sns.heatmap(cm, annot=True, fmt='d', cmap='Blues', 
            xticklabels=['Predicted Died', 'Predicted Survived'],
            yticklabels=['Actual Died', 'Actual Survived'])
plt.title('Confusion Matrix — Titanic Logistic Regression')
plt.savefig('confusion_matrix.png', dpi=150)
```

---

#### 📅 DAY 18 — Decision Trees + Random Forests

**Morning Theory (2 hrs):**
- Decision trees: recursive binary splitting of feature space
- Information gain and Gini impurity — how the tree decides where to split
- Why single decision trees overfit: they memorize training data
- Ensemble learning: wisdom of crowds — many weak learners > one strong learner
- Random Forest: bagging (bootstrap samples) + feature randomness
- Feature importance in Random Forests — actionable insight for business
- XGBoost intuition: boosting = building trees sequentially to fix mistakes

**Afternoon Hands-On:**
```python
from sklearn.ensemble import RandomForestClassifier, GradientBoostingClassifier
from sklearn.tree import DecisionTreeClassifier, export_text
import pandas as pd, numpy as np
from sklearn.model_selection import cross_val_score

# Use prepared Titanic X_train, y_train from Day 17

# Compare models
models = {
    'Decision Tree': DecisionTreeClassifier(max_depth=5, random_state=42),
    'Random Forest': RandomForestClassifier(n_estimators=100, max_depth=7, random_state=42),
    'Gradient Boosting': GradientBoostingClassifier(n_estimators=100, learning_rate=0.1, random_state=42),
}

results = {}
for name, model in models.items():
    cv_scores = cross_val_score(model, X_train, y_train, cv=5, scoring='accuracy')
    results[name] = {'mean': cv_scores.mean(), 'std': cv_scores.std()}
    print(f"{name}: {cv_scores.mean():.4f} ± {cv_scores.std():.4f}")

# Feature importance from Random Forest
rf = RandomForestClassifier(n_estimators=100, random_state=42)
rf.fit(X_train, y_train)
feature_names = ['Pclass', 'Sex', 'Age', 'SibSp', 'Parch', 'Fare']
importances = pd.Series(rf.feature_importances_, index=feature_names).sort_values(ascending=False)
print("\nFeature Importances:")
print(importances)
```

---

#### 📅 DAY 19 — SVM, KNN, Naive Bayes

**Morning Theory:**
- SVM: find the hyperplane that maximizes the margin between classes
- Kernel trick: project to higher dimensions without computing it explicitly (RBF kernel)
- KNN: classify by majority vote of k nearest neighbors — lazy learning
- Naive Bayes: apply Bayes' theorem with "naive" independence assumption
- When to use each: SVM for high-dim text, KNN for small data, NB for text classification

**Afternoon Hands-On:**
```python
from sklearn.svm import SVC
from sklearn.neighbors import KNeighborsClassifier
from sklearn.naive_bayes import GaussianNB
from sklearn.pipeline import Pipeline

# Build a comparison pipeline
pipelines = {
    'SVM (RBF)': Pipeline([('svm', SVC(kernel='rbf', C=1.0, gamma='scale', probability=True))]),
    'KNN (k=5)': Pipeline([('knn', KNeighborsClassifier(n_neighbors=5))]),
    'Naive Bayes': Pipeline([('nb', GaussianNB())]),
}

for name, pipeline in pipelines.items():
    pipeline.fit(X_train, y_train)
    score = pipeline.score(X_test, y_test)
    print(f"{name}: Test Accuracy = {score:.4f}")
```

---

#### 📅 DAY 20 — Unsupervised Learning: Clustering + PCA

**Morning Theory:**
- Unsupervised learning: no labels — discover structure in data
- K-Means: centroid-based clustering — the Elbow method for choosing k
- DBSCAN: density-based — handles non-spherical clusters, detects outliers
- Hierarchical clustering: dendrogram visualization
- PCA: dimensionality reduction for visualization and noise reduction
- When does unsupervised learning appear in production? (customer segmentation, anomaly detection, preprocessing)

**Afternoon Hands-On:**
```python
from sklearn.cluster import KMeans, DBSCAN
from sklearn.decomposition import PCA
from sklearn.preprocessing import StandardScaler
import matplotlib.pyplot as plt
import numpy as np

# Generate customer data
np.random.seed(42)
n = 300
income = np.concatenate([np.random.normal(30, 5, 100), 
                          np.random.normal(60, 8, 100), 
                          np.random.normal(90, 6, 100)])
spending = np.concatenate([np.random.normal(40, 8, 100),
                            np.random.normal(50, 10, 100),
                            np.random.normal(70, 7, 100)])
X_cust = np.column_stack([income, spending])
X_scaled = StandardScaler().fit_transform(X_cust)

# Elbow method
inertias = []
for k in range(2, 11):
    km = KMeans(n_clusters=k, random_state=42, n_init=10)
    km.fit(X_scaled)
    inertias.append(km.inertia_)

plt.plot(range(2, 11), inertias, 'bo-')
plt.title('Elbow Method')
plt.xlabel('k'); plt.ylabel('Inertia')
plt.savefig('elbow_method.png')

# Apply K-Means with k=3
km = KMeans(n_clusters=3, random_state=42, n_init=10)
labels = km.fit_predict(X_scaled)

# Visualize
colors = ['#e74c3c', '#3498db', '#2ecc71']
plt.figure(figsize=(8, 6))
for i in range(3):
    mask = labels == i
    plt.scatter(income[mask], spending[mask], c=colors[i], 
                label=f'Cluster {i} (n={mask.sum()})', alpha=0.7)
plt.xlabel('Annual Income (k$)'); plt.ylabel('Spending Score')
plt.title('Customer Segments')
plt.legend()
plt.savefig('customer_segments.png')
```

---

#### 📅 DAY 21 — Week 3 Capstone Project: End-to-End ML Pipeline

**Project: Credit Card Default Prediction System**

**Real-World Problem:** A bank wants to predict which customers will default on their credit card payment next month. This directly impacts risk management.

**Dataset:** UCI Credit Card Default dataset (free, downloadable)

**Requirements:**
1. Full EDA with 6+ visualizations
2. Feature engineering (create new features from existing ones)
3. Train 4 models: Logistic Regression, Random Forest, GBM, SVM
4. Compare using cross-validation + ROC-AUC
5. Interpret: which features drive defaults? (Feature importance)
6. Document: what would you tell the bank risk team?

**GitHub Documentation:**
- Full README explaining business problem + solution
- `notebooks/eda.ipynb` — exploratory analysis
- `src/train.py` — training script
- `reports/findings.md` — business insights
- Blog post on Hashnode: "How I Built a Credit Default Predictor"

---

### WEEK 4 — Advanced ML + Model Tuning (Days 22–28)

---

#### 📅 DAY 22 — Regularization: L1, L2, Elastic Net

**Morning Theory:**
- Regularization adds a penalty term to the loss function to prevent overfitting
- L2 (Ridge): penalizes large weights → shrinks all weights toward zero
- L1 (Lasso): penalizes absolute weights → drives some weights to exactly zero (feature selection!)
- Elastic Net: combination of L1 + L2
- When to use: L1 when you suspect only a few features matter, L2 when all features contribute
- The regularization parameter λ (alpha): higher = more regularization = simpler model

**Architecture Insight:** In neural networks, L2 regularization is called "weight decay." It's built into most optimizers (AdamW).

---

#### 📅 DAY 23 — Hyperparameter Tuning: Grid Search, Random Search, Optuna

**Morning Theory:**
- Hyperparameters vs parameters: hyperparameters are set before training, parameters are learned
- Grid search: exhaustive — good for small search space
- Random search: better when some hyperparameters matter more than others
- Bayesian optimization (Optuna): learns which regions of the search space are promising
- Why random search often beats grid search: most hyperparameter landscapes have only 2-3 dimensions that actually matter

**Afternoon Hands-On:**
```python
from sklearn.model_selection import GridSearchCV, RandomizedSearchCV
import optuna
from sklearn.ensemble import RandomForestClassifier

# Optuna — the industry standard for hyperparameter tuning
def objective(trial):
    n_estimators = trial.suggest_int('n_estimators', 50, 500)
    max_depth = trial.suggest_int('max_depth', 3, 15)
    min_samples_split = trial.suggest_int('min_samples_split', 2, 20)
    
    model = RandomForestClassifier(
        n_estimators=n_estimators,
        max_depth=max_depth,
        min_samples_split=min_samples_split,
        random_state=42,
        n_jobs=-1
    )
    score = cross_val_score(model, X_train, y_train, cv=5, scoring='roc_auc').mean()
    return score

study = optuna.create_study(direction='maximize')
study.optimize(objective, n_trials=50, show_progress_bar=True)
print("Best params:", study.best_params)
print("Best ROC-AUC:", study.best_value)
```

---

#### 📅 DAY 24 — Feature Engineering (The Most Important Skill)

**Morning Theory:**
- Feature engineering = transforming raw data into representations that algorithms understand
- Domain knowledge beats algorithm choice: a smart feature with a weak model > a weak feature with a strong model
- Techniques: polynomial features, interaction terms, log transforms, binning, target encoding
- For time series: lag features, rolling means, day-of-week, is_holiday
- For text: TF-IDF, character n-grams, length, punctuation count
- Feature selection: remove redundant features that add noise, not signal

**Afternoon Hands-On:**
```python
import pandas as pd
import numpy as np
from sklearn.preprocessing import PolynomialFeatures, LabelEncoder
from category_encoders import TargetEncoder

# Real-world feature engineering on Titanic
df = pd.read_csv('titanic.csv')

# Create meaningful new features
df['FamilySize'] = df['SibSp'] + df['Parch'] + 1
df['IsAlone'] = (df['FamilySize'] == 1).astype(int)
df['Title'] = df['Name'].str.extract(r' ([A-Za-z]+)\.', expand=False)
df['Title'] = df['Title'].replace(['Lady','Countess','Capt','Col','Don','Dr',
                                    'Major','Rev','Sir','Jonkheer','Dona'], 'Rare')
df['Title'] = df['Title'].replace('Mlle', 'Miss')
df['Title'] = df['Title'].replace('Ms', 'Miss')
df['Title'] = df['Title'].replace('Mme', 'Mrs')
df['AgeBin'] = pd.cut(df['Age'], bins=[0,12,18,35,60,100], labels=['Child','Teen','Adult','MidAge','Senior'])
df['FareBin'] = pd.qcut(df['Fare'], q=4, labels=['Low','Mid','High','Premium'])

print("New features:", ['FamilySize', 'IsAlone', 'Title', 'AgeBin', 'FareBin'])
```

---

#### 📅 DAY 25–28 — Scikit-Learn Pipelines + MLflow Tracking

**Core Concept: Production-Grade Pipelines**

In production, preprocessing + model must be packaged together. If you preprocess outside the model, you'll get subtle bugs (leaking test data into training).

```python
from sklearn.pipeline import Pipeline
from sklearn.compose import ColumnTransformer
from sklearn.preprocessing import StandardScaler, OneHotEncoder
from sklearn.impute import SimpleImputer
import mlflow
import mlflow.sklearn

# Define column types
numeric_features = ['Age', 'Fare', 'SibSp', 'Parch']
categorical_features = ['Pclass', 'Sex', 'Embarked']

# Build preprocessing pipeline
numeric_transformer = Pipeline([
    ('imputer', SimpleImputer(strategy='median')),
    ('scaler', StandardScaler()),
])

categorical_transformer = Pipeline([
    ('imputer', SimpleImputer(strategy='most_frequent')),
    ('encoder', OneHotEncoder(handle_unknown='ignore', sparse_output=False)),
])

preprocessor = ColumnTransformer([
    ('num', numeric_transformer, numeric_features),
    ('cat', categorical_transformer, categorical_features),
])

# Full pipeline with model
full_pipeline = Pipeline([
    ('preprocessor', preprocessor),
    ('classifier', RandomForestClassifier(n_estimators=100, random_state=42))
])

# Track with MLflow — this is what production teams use
mlflow.set_experiment("titanic-classification")

with mlflow.start_run(run_name="rf-pipeline-v1"):
    full_pipeline.fit(X_train, y_train)
    y_pred = full_pipeline.predict(X_test)
    
    accuracy = accuracy_score(y_test, y_pred)
    auc = roc_auc_score(y_test, full_pipeline.predict_proba(X_test)[:,1])
    
    mlflow.log_params({"n_estimators": 100, "model_type": "RandomForest"})
    mlflow.log_metrics({"accuracy": accuracy, "roc_auc": auc})
    mlflow.sklearn.log_model(full_pipeline, "model")
    
    print(f"Accuracy: {accuracy:.4f}, ROC-AUC: {auc:.4f}")
    print(f"Model saved to MLflow. Run: mlflow ui to see it.")
```

---

### WEEKS 5–6: PHASE 1 CAPSTONE PROJECT (Days 29–30)

**Capstone Project 1: Churn Prediction System for a Telecom Company**

**Business Problem:** A telecom company is losing customers. They want to know WHO is about to leave (churn) so they can offer retention deals before it happens.

**Deliverables:**
1. EDA notebook with business insights
2. Feature engineering pipeline
3. Model comparison (Logistic, RF, XGBoost, SVM)
4. Best model exported via MLflow
5. Simple API (Flask) that accepts customer data and returns churn probability
6. Complete GitHub repository with README
7. Technical blog post: "End-to-End ML: Churn Prediction from Data to API"

**This project should be on your LinkedIn, GitHub, and blog. It is your first portfolio piece.**

---

## 🔴 PHASE 2: DEEP LEARNING (Days 31–80)
### *"Teaching Machines to See, Hear, and Understand"*

---

### WEEK 5 — Neural Networks from First Principles (Days 31–37)

---

#### 📅 DAY 31 — What IS a Neural Network?

**Morning Theory:**
- A neural network = composition of functions. Layer 1 transforms input, Layer 2 transforms that, etc.
- Each neuron: weighted sum + activation function = `f(w·x + b)`
- Why activation functions? Without them, stacking layers is pointless (just a linear transformation)
- ReLU: `max(0, x)` — simple, works, default choice. Why? Doesn't saturate for positive values.
- Sigmoid: for probabilities. Tanh: centered around 0. ReLU: default for hidden layers.
- Universal Approximation Theorem: a sufficiently wide network can approximate any function

**Architecture Insight:** When you see a neural network, ask: "What function is this approximating?" For image recognition: "What function maps pixel values to class labels?" The network learns this function from data.

---

#### 📅 DAY 32 — Backpropagation: The Heart of Learning

**Morning Theory:**
- Forward pass: input → activations → predictions → loss
- Backward pass: compute dL/dW for every weight using chain rule
- Gradient flow: gradients flow from output layer backward through the network
- Vanishing gradient problem: gradients shrink as they flow through many sigmoid layers
- Why ReLU solves vanishing gradients (for positive values, gradient = 1, doesn't shrink)
- Computational graph: how PyTorch tracks operations for automatic differentiation

**Afternoon Hands-On — Build a 2-layer NN from scratch:**
```python
import numpy as np

class TwoLayerNetwork:
    """A 2-layer neural network built entirely with NumPy — no frameworks."""
    
    def __init__(self, input_dim, hidden_dim, output_dim, lr=0.01):
        # Initialize weights with small random values (Xavier initialization)
        self.W1 = np.random.randn(input_dim, hidden_dim) * np.sqrt(2.0/input_dim)
        self.b1 = np.zeros(hidden_dim)
        self.W2 = np.random.randn(hidden_dim, output_dim) * np.sqrt(2.0/hidden_dim)
        self.b2 = np.zeros(output_dim)
        self.lr = lr
    
    def relu(self, z): return np.maximum(0, z)
    def relu_grad(self, z): return (z > 0).astype(float)
    def sigmoid(self, z): return 1 / (1 + np.exp(-np.clip(z, -500, 500)))
    
    def forward(self, X):
        self.X = X
        self.z1 = X @ self.W1 + self.b1
        self.a1 = self.relu(self.z1)
        self.z2 = self.a1 @ self.W2 + self.b2
        self.a2 = self.sigmoid(self.z2)
        return self.a2
    
    def backward(self, X, y):
        n = X.shape[0]
        # Output layer gradient
        dL_da2 = self.a2 - y.reshape(-1, 1)
        dL_dz2 = dL_da2  # sigmoid + BCE = simple gradient
        dL_dW2 = self.a1.T @ dL_dz2 / n
        dL_db2 = dL_dz2.mean(axis=0)
        # Hidden layer gradient (chain rule)
        dL_da1 = dL_dz2 @ self.W2.T
        dL_dz1 = dL_da1 * self.relu_grad(self.z1)
        dL_dW1 = X.T @ dL_dz1 / n
        dL_db1 = dL_dz1.mean(axis=0)
        # Update weights
        self.W2 -= self.lr * dL_dW2
        self.b2 -= self.lr * dL_db2
        self.W1 -= self.lr * dL_dW1
        self.b1 -= self.lr * dL_db1
    
    def train(self, X, y, epochs=1000):
        for epoch in range(epochs):
            y_pred = self.forward(X)
            loss = -np.mean(y * np.log(y_pred + 1e-8) + (1-y) * np.log(1 - y_pred + 1e-8))
            self.backward(X, y)
            if epoch % 100 == 0:
                print(f"Epoch {epoch}: Loss = {loss:.4f}")
```

---

#### 📅 DAY 33–35 — PyTorch: The Industry Standard

**Why PyTorch?** Favored in research and industry for its dynamic computation graph. TensorFlow is more common in production serving but PyTorch is dominant for training.

```python
import torch
import torch.nn as nn
import torch.optim as optim
from torch.utils.data import DataLoader, TensorDataset

# The same network, now in PyTorch
class MLPClassifier(nn.Module):
    def __init__(self, input_dim, hidden_dims, output_dim, dropout=0.3):
        super().__init__()
        layers = []
        prev_dim = input_dim
        for hidden_dim in hidden_dims:
            layers.extend([
                nn.Linear(prev_dim, hidden_dim),
                nn.BatchNorm1d(hidden_dim),
                nn.ReLU(),
                nn.Dropout(dropout)
            ])
            prev_dim = hidden_dim
        layers.append(nn.Linear(prev_dim, output_dim))
        self.network = nn.Sequential(*layers)
    
    def forward(self, x):
        return self.network(x)

# Training loop — the fundamental pattern in ALL PyTorch training
def train_epoch(model, loader, optimizer, criterion, device):
    model.train()
    total_loss = 0
    correct = 0
    for X_batch, y_batch in loader:
        X_batch, y_batch = X_batch.to(device), y_batch.to(device)
        optimizer.zero_grad()           # Clear previous gradients
        logits = model(X_batch)         # Forward pass
        loss = criterion(logits, y_batch)  # Compute loss
        loss.backward()                 # Backward pass
        optimizer.step()                # Update weights
        total_loss += loss.item()
        correct += (logits.argmax(1) == y_batch).sum().item()
    return total_loss / len(loader), correct / len(loader.dataset)

device = torch.device('cuda' if torch.cuda.is_available() else 'cpu')
model = MLPClassifier(input_dim=6, hidden_dims=[128, 64, 32], output_dim=2).to(device)
optimizer = optim.AdamW(model.parameters(), lr=1e-3, weight_decay=1e-4)
criterion = nn.CrossEntropyLoss()
scheduler = optim.lr_scheduler.CosineAnnealingLR(optimizer, T_max=100)
```

---

#### 📅 DAY 36–37 — Project: Tabular Deep Learning + Comparison

**Project: Compare Deep Learning vs Classical ML on Tabular Data**

Many practitioners blindly use neural networks for tabular data. This project teaches you that Random Forests and XGBoost often *beat* neural networks on tabular data — and why.

Build both, compare, document the tradeoffs in a blog post.

---

### WEEK 6–7 — Computer Vision with CNNs (Days 38–49)

---

#### 📅 DAY 38 — Convolutional Neural Networks: Theory

**Morning Theory:**
- Why CNNs for images? Fully connected networks don't scale: 1 megapixel image = 1M inputs
- Convolution operation: a filter (kernel) slides over the image computing dot products
- What do filters learn? Edge detectors, corner detectors, texture detectors (early layers), object parts (deep layers)
- Stride and padding: controlling output size
- MaxPooling: spatial downsampling — preserve strongest activations, reduce computation
- Parameter sharing: the same filter is applied everywhere → huge parameter reduction
- Receptive field: how much of the original image each neuron "sees"

**Architecture Insight:** VGG-16, ResNet, EfficientNet — all are just CNNs with different arrangements of conv layers, pooling, and connections. The principles are the same.

---

#### 📅 DAY 39–42 — Building CNN in PyTorch + Transfer Learning

```python
import torch
import torch.nn as nn
import torchvision
import torchvision.transforms as transforms
from torchvision import models

# Transfer learning: use pre-trained ResNet18, fine-tune on your data
# Why? ResNet was trained on 1.2M ImageNet images. Its features generalize.
# You only need your dataset to teach the LAST layer.

def build_transfer_model(num_classes: int, freeze_backbone: bool = True):
    """
    ResNet18 with custom head for your classification task.
    Industry standard approach for small datasets.
    """
    model = models.resnet18(weights=models.ResNet18_Weights.IMAGENET1K_V1)
    
    if freeze_backbone:
        for param in model.parameters():
            param.requires_grad = False  # Freeze pretrained weights
    
    # Replace the final classification head
    in_features = model.fc.in_features
    model.fc = nn.Sequential(
        nn.Linear(in_features, 256),
        nn.ReLU(),
        nn.Dropout(0.5),
        nn.Linear(256, num_classes)
    )
    return model

# Data augmentation: artificially expand your dataset
train_transform = transforms.Compose([
    transforms.RandomResizedCrop(224),
    transforms.RandomHorizontalFlip(),
    transforms.ColorJitter(brightness=0.2, contrast=0.2, saturation=0.2),
    transforms.ToTensor(),
    transforms.Normalize(mean=[0.485, 0.456, 0.406], std=[0.229, 0.224, 0.225])
])
```

---

#### 📅 DAY 43–49 — CNN Capstone Project

**Project: Crop Disease Detection System (Real MNC-Level Problem)**

**Business Problem:** Farmers in rural India lose 15-20% of crops to diseases. Early visual detection can save millions. Build a CNN that classifies crop leaf images as healthy or diseased.

**Dataset:** PlantVillage dataset (free, 54,000 images, 38 classes)

**Architecture:**
```
Input Image (224x224) 
    → ResNet50 (pretrained backbone, frozen)
    → Custom head (512 → 256 → 38 classes)
    → Softmax output
    → Class name + confidence
```

**Deliverables:**
1. Training script with MLflow tracking
2. Model achieves >90% accuracy on validation set
3. Inference script: input an image, output top-3 diseases with probabilities
4. Gradio demo: simple web UI for testing
5. GitHub README with architecture diagram and results
6. Docker container: `docker run crop-disease-detector`

**Why This Project?** Agriculture AI is a massive industry. Tata Consultancy Services, IBM, and Microsoft have dedicated teams for this. This project shows you can solve a real-world problem, not just run MNIST.

---

### WEEK 8–10 — NLP: From Text to Meaning (Days 50–65)

---

#### 📅 DAY 50 — Text Fundamentals: Tokenization, Embeddings

**Morning Theory:**
- Text processing pipeline: raw text → tokens → IDs → embeddings → model
- Tokenization: splitting text into units (words, subwords, characters)
- Why subword tokenization (BPE, WordPiece)? "unbelievable" = "un" + "believable" — handles unknown words
- Word embeddings: represent words as dense vectors in semantic space
- Word2Vec: words with similar meanings have similar vectors (`king - man + woman ≈ queen`)
- The embedding dimension: 128, 256, 768 — larger = more expressive but slower
- TF-IDF: classical approach — weight words by importance to document

**Afternoon Hands-On:**
```python
from sklearn.feature_extraction.text import TfidfVectorizer
from sklearn.linear_model import LogisticRegression
from sklearn.pipeline import Pipeline
import datasets  # HuggingFace datasets

# Load IMDB sentiment dataset
dataset = datasets.load_dataset('imdb')
train_texts = dataset['train']['text'][:5000]
train_labels = dataset['train']['label'][:5000]
test_texts = dataset['test']['text'][:1000]
test_labels = dataset['test']['label'][:1000]

# TF-IDF + Logistic Regression baseline
tfidf_pipeline = Pipeline([
    ('tfidf', TfidfVectorizer(max_features=50000, ngram_range=(1,2), min_df=2)),
    ('clf', LogisticRegression(C=1.0, max_iter=1000))
])
tfidf_pipeline.fit(train_texts, train_labels)
baseline_acc = tfidf_pipeline.score(test_texts, test_labels)
print(f"TF-IDF + LR Accuracy: {baseline_acc:.4f}")
# Expect: ~88-90%. Transformers will get 93%+.
```

---

#### 📅 DAY 51–55 — Transformers and BERT

**Morning Theory (Day 51):**
- The attention mechanism: instead of reading sequence left-to-right, look at ALL positions at once
- Self-attention: each word attends to every other word — "The bank can guarantee..." — does "bank" mean financial or riverbank? Attention figures it out from context.
- Multi-head attention: multiple attention heads capture different types of relationships
- BERT: Bidirectional Encoder Representations from Transformers — reads both left-to-right AND right-to-left
- Fine-tuning: take pre-trained BERT, add a task-specific head, train on your data with a small learning rate

**Architecture Insight:**
```
Input: "I loved this movie"
    ↓ Tokenize: [CLS] I loved this movie [SEP]
    ↓ Token IDs: [101, 146, 1374, 1142, 2523, 102]
    ↓ Embeddings: (6, 768) tensor
    ↓ 12 Transformer layers (self-attention + FFN)
    ↓ [CLS] token representation: (768,)
    ↓ Classification head: (768 → 2)
    ↓ Output: [0.05, 0.95] → POSITIVE
```

```python
from transformers import AutoTokenizer, AutoModelForSequenceClassification
from transformers import TrainingArguments, Trainer
import torch

model_name = "distilbert-base-uncased"  # Smaller, faster version of BERT
tokenizer = AutoTokenizer.from_pretrained(model_name)
model = AutoModelForSequenceClassification.from_pretrained(model_name, num_labels=2)

# Tokenize dataset
def tokenize(batch):
    return tokenizer(batch['text'], truncation=True, padding='max_length', max_length=512)

# Training with HuggingFace Trainer (industry standard)
training_args = TrainingArguments(
    output_dir='./results',
    num_train_epochs=3,
    per_device_train_batch_size=16,
    per_device_eval_batch_size=32,
    learning_rate=2e-5,             # Small LR for fine-tuning
    warmup_ratio=0.1,
    weight_decay=0.01,
    evaluation_strategy='epoch',
    save_strategy='epoch',
    load_best_model_at_end=True,
    metric_for_best_model='accuracy',
    fp16=True,                      # Mixed precision: 2x speedup on modern GPUs
    report_to='mlflow',
)
```

---

#### 📅 DAY 56–65 — NLP Capstone Project

**Project: Customer Support Ticket Auto-Router**

**Business Problem:** A tech company receives 10,000 support tickets per day. Routing tickets to the right team manually costs 50+ person-hours per day. Build an NLP system that:
- Classifies ticket category (billing, technical, account, shipping)
- Detects urgency level (critical/high/medium/low)
- Extracts key information (product name, error code, account ID)
- Suggests a response template

**Tech Stack:**
- DistilBERT for classification (HuggingFace)
- spaCy for entity extraction
- FastAPI endpoint: `POST /classify` → returns category + urgency + entities
- Docker container
- MLflow experiment tracking
- GitHub Actions CI/CD: tests run on every push

---

### WEEK 11–12 — Large Language Models (Days 66–80)

---

#### 📅 DAY 66–70 — LLM Architecture Deep Dive

**Morning Theory:**
- GPT architecture: decoder-only transformer (unlike BERT which is encoder-only)
- Autoregressive generation: predict next token, append, predict next token...
- Temperature: controls randomness. 0 = deterministic, 1 = normal, >1 = creative/chaotic
- Top-p (nucleus) sampling: sample from the top p% of probability mass
- Context window: how many tokens the model can "see" at once (GPT-4: 128k, Llama 3: 128k)
- Quantization: run 70B models on your laptop by reducing float32 → int4 (4-bit)
- Ollama: run LLMs locally for free

**Hands-On — Run a local LLM:**
```bash
# Install Ollama
curl -fsSL https://ollama.com/install.sh | sh

# Pull and run Llama 3.1 8B (requires ~8GB RAM)
ollama pull llama3.1:8b
ollama run llama3.1:8b "Explain quantum entanglement in 2 sentences"

# Python API
import ollama

response = ollama.chat(
    model='llama3.1:8b',
    messages=[
        {'role': 'system', 'content': 'You are a helpful data science tutor.'},
        {'role': 'user', 'content': 'What is gradient descent in simple terms?'}
    ]
)
print(response['message']['content'])
```

---

#### 📅 DAY 71–75 — Prompt Engineering

**Morning Theory:**
- Prompt engineering: the skill of designing inputs to get better outputs from LLMs
- Zero-shot: just ask the question
- Few-shot: provide examples in the prompt
- Chain-of-thought: "Let's think step by step" → significantly improves reasoning
- System prompts: set the model's role and constraints
- Structured output: "Respond ONLY in JSON format with keys: category, confidence, reasoning"
- Common failures: hallucination, instruction following, verbosity

**Practical Framework:**
```
SYSTEM: You are an expert [ROLE]. Your task is to [TASK]. 
         Always respond in [FORMAT]. Never [CONSTRAINT].

USER: [CONTEXT] 
      [SPECIFIC REQUEST]
      [OUTPUT SPECIFICATION]

EXAMPLES:
Input: [example_input]
Output: [example_output]
```

---

#### 📅 DAY 76–80 — RAG: Retrieval-Augmented Generation

**Architecture:**
```
User Query
    ↓
Query Embedding (embed the question)
    ↓
Vector Database Search (find similar documents)
    ↓
Retrieved Context (top-k relevant chunks)
    ↓
LLM Prompt: "Given this context: [retrieved], answer: [query]"
    ↓
Grounded Response
```

**Why RAG?** LLMs hallucinate. They also don't know about your private company documents. RAG gives the LLM your specific knowledge + reduces hallucination by grounding answers in retrieved facts.

```python
from langchain_community.vectorstores import Chroma
from langchain_community.embeddings import OllamaEmbeddings
from langchain_community.llms import Ollama
from langchain.text_splitter import RecursiveCharacterTextSplitter
from langchain_community.document_loaders import PyPDFLoader
from langchain.chains import RetrievalQA

# Load and chunk documents
loader = PyPDFLoader("company_policy.pdf")
documents = loader.load()

text_splitter = RecursiveCharacterTextSplitter(
    chunk_size=500, 
    chunk_overlap=50,
    separators=["\n\n", "\n", ".", " "]
)
chunks = text_splitter.split_documents(documents)

# Embed and store in vector database
embeddings = OllamaEmbeddings(model="nomic-embed-text")
vectorstore = Chroma.from_documents(
    documents=chunks,
    embedding=embeddings,
    persist_directory="./chroma_db"
)

# Build RAG chain
llm = Ollama(model="llama3.1:8b", temperature=0)
retriever = vectorstore.as_retriever(search_kwargs={"k": 3})
qa_chain = RetrievalQA.from_chain_type(
    llm=llm,
    retriever=retriever,
    return_source_documents=True
)

result = qa_chain("What is our vacation policy?")
print("Answer:", result['result'])
print("Sources:", [doc.metadata for doc in result['source_documents']])
```

---

## 🟡 PHASE 3: AGENTIC AI (Days 81–120)
### *"From Models that Answer to Systems that Act"*

---

#### 📅 DAY 81 — What is Agentic AI?

**Morning Theory:**
- An AI "agent" = an LLM + tools + memory + planning + action loop
- The agent loop: Observe → Think → Act → Observe → Think → Act...
- Tools: functions the agent can call (search the web, run Python, query a database, send an email)
- Memory: short-term (conversation context) vs long-term (vector database of past interactions)
- Planning: break a complex goal into steps (ReAct, Chain-of-Thought, Tree-of-Thought)
- Multi-agent systems: multiple specialized agents collaborating to solve complex tasks

**Architecture — The ReAct Agent Loop:**
```
User: "Find the latest GDP of India and compare it to China"

Agent Thinks: I need to search for India GDP, then China GDP, then compare.
Agent Acts: web_search("India GDP 2024")
Observation: "India GDP: $3.7 trillion (2024)"
Agent Thinks: Got India. Now need China.
Agent Acts: web_search("China GDP 2024")  
Observation: "China GDP: $18.5 trillion (2024)"
Agent Thinks: I have both. Now compare.
Agent Responds: "China's GDP ($18.5T) is approximately 5x India's GDP ($3.7T)..."
```

---

#### 📅 DAY 82–90 — Building Agents with LangChain/LangGraph

```python
from langchain_community.llms import Ollama
from langchain.agents import AgentExecutor, create_react_agent
from langchain_core.tools import tool
from langchain import hub
import sqlite3, json

@tool
def query_database(sql: str) -> str:
    """Execute a SQL query on the sales database. 
    Use this to answer questions about sales, customers, or products."""
    try:
        conn = sqlite3.connect('sales.db')
        df = pd.read_sql_query(sql, conn)
        conn.close()
        return df.to_json(orient='records')
    except Exception as e:
        return f"Error: {str(e)}"

@tool
def calculate_statistics(data_json: str) -> str:
    """Calculate statistical summaries from JSON data.
    Returns mean, median, std, min, max."""
    import json
    data = json.loads(data_json)
    df = pd.DataFrame(data)
    numeric_cols = df.select_dtypes(include='number').columns
    return df[numeric_cols].describe().to_json()

@tool  
def generate_chart(data_json: str, chart_type: str, title: str) -> str:
    """Generate a chart and save it as PNG. Returns the file path."""
    data = json.loads(data_json)
    df = pd.DataFrame(data)
    plt.figure(figsize=(10, 6))
    if chart_type == 'bar':
        df.plot(kind='bar', ax=plt.gca())
    elif chart_type == 'line':
        df.plot(kind='line', ax=plt.gca())
    plt.title(title)
    path = f"charts/{title.replace(' ','_')}.png"
    plt.savefig(path, dpi=150, bbox_inches='tight')
    plt.close()
    return path

# Create the agent
llm = Ollama(model="llama3.1:8b", temperature=0)
tools = [query_database, calculate_statistics, generate_chart]
prompt = hub.pull("hwchase17/react")

agent = create_react_agent(llm, tools, prompt)
agent_executor = AgentExecutor(
    agent=agent, 
    tools=tools, 
    verbose=True,
    max_iterations=10,
    handle_parsing_errors=True
)

# Use the agent
result = agent_executor.invoke({
    "input": "Analyze our top 10 products by revenue in Q4 2024 and create a bar chart."
})
```

---

#### 📅 DAY 91–100 — Multi-Agent Systems with CrewAI

```python
from crewai import Agent, Task, Crew, Process
from crewai_tools import SerperDevTool, WebsiteSearchTool

# Define specialized agents — each has a role, goal, and backstory
researcher = Agent(
    role='Senior Research Analyst',
    goal='Find accurate and comprehensive information on any topic',
    backstory="""You are an expert researcher with 10 years of experience in data analysis.
    You always verify information from multiple sources and cite your findings.""",
    tools=[SerperDevTool(), WebsiteSearchTool()],
    llm=Ollama(model='llama3.1:8b'),
    verbose=True,
    allow_delegation=False
)

data_analyst = Agent(
    role='Data Analyst',
    goal='Analyze data and extract actionable insights',
    backstory="""You are a senior data analyst specializing in market research and 
    trend analysis. You transform raw data into clear business insights.""",
    llm=Ollama(model='llama3.1:8b'),
    verbose=True,
    allow_delegation=True
)

report_writer = Agent(
    role='Technical Report Writer',
    goal='Create clear, comprehensive reports from research findings',
    backstory="""You write clear, executive-level reports that translate technical 
    findings into business language. Your reports always have: executive summary, 
    key findings, recommendations, and next steps.""",
    llm=Ollama(model='llama3.1:8b'),
    verbose=True,
    allow_delegation=False
)

# Define tasks
research_task = Task(
    description="Research the current state of AI adoption in Indian banking sector. "
                "Find statistics, key players, challenges, and growth trends.",
    agent=researcher,
    expected_output="A detailed research report with statistics, citations, and key findings"
)

analysis_task = Task(
    description="Analyze the research findings and identify: top 3 opportunities, "
                "top 3 risks, and market size estimate for 2025-2028.",
    agent=data_analyst,
    expected_output="Structured analysis with opportunities, risks, and market projections",
    context=[research_task]
)

report_task = Task(
    description="Write an executive report on AI adoption in Indian banking. "
                "Include: executive summary, key findings, market analysis, recommendations.",
    agent=report_writer,
    expected_output="A professional 3-5 page executive report in Markdown format",
    context=[research_task, analysis_task],
    output_file="ai_banking_india_report.md"
)

# Assemble and run the crew
crew = Crew(
    agents=[researcher, data_analyst, report_writer],
    tasks=[research_task, analysis_task, report_task],
    process=Process.sequential,
    verbose=True
)

result = crew.kickoff()
print("Report generated:", result)
```

---

#### 📅 DAY 101–110 — Memory Systems: Short-Term + Long-Term

```python
from langchain.memory import ConversationBufferWindowMemory
from langchain_community.vectorstores import Chroma
from langchain_community.embeddings import OllamaEmbeddings
import json
from datetime import datetime

class AgentMemorySystem:
    """
    Production-grade memory system combining:
    - Short-term: Last N messages (conversation context)
    - Long-term: Vector DB of important facts/summaries
    - Episodic: Key events and decisions
    """
    
    def __init__(self, agent_id: str, window_size: int = 10):
        self.agent_id = agent_id
        self.embeddings = OllamaEmbeddings(model="nomic-embed-text")
        
        # Short-term: sliding window of recent messages
        self.short_term = ConversationBufferWindowMemory(
            k=window_size,
            return_messages=True,
            memory_key="chat_history"
        )
        
        # Long-term: vector store for semantic search
        self.long_term = Chroma(
            collection_name=f"agent_{agent_id}_memory",
            embedding_function=self.embeddings,
            persist_directory=f"./memory/{agent_id}"
        )
    
    def remember(self, content: str, importance: float = 0.5, tags: list = None):
        """Store a memory in long-term storage."""
        metadata = {
            "agent_id": self.agent_id,
            "timestamp": datetime.now().isoformat(),
            "importance": importance,
            "tags": json.dumps(tags or [])
        }
        self.long_term.add_texts([content], metadatas=[metadata])
    
    def recall(self, query: str, k: int = 3, importance_threshold: float = 0.3) -> list:
        """Retrieve relevant memories by semantic similarity."""
        results = self.long_term.similarity_search_with_score(query, k=k*2)
        filtered = [
            (doc, score) for doc, score in results
            if doc.metadata.get('importance', 0) >= importance_threshold
        ]
        return filtered[:k]
    
    def get_context(self, current_input: str) -> str:
        """Build full context: recent conversation + relevant long-term memories."""
        memories = self.recall(current_input, k=3)
        memory_text = "\n".join([
            f"[Memory, relevance={score:.2f}]: {doc.page_content}"
            for doc, score in memories
        ])
        recent = self.short_term.load_memory_variables({})
        return f"Relevant Memories:\n{memory_text}\n\nRecent Conversation:\n{recent}"
```

---

#### 📅 DAY 111–120 — Agentic AI Capstone Project

**Project: AI-Powered Data Analysis Agent**

**Business Problem:** A startup's operations team receives questions about business data daily: "How did we do last month?", "Which customers are at risk of churning?", "What's our runway?" They spend 3 hours/day answering these manually.

**Solution:** A multi-agent system that:
1. **Data Agent:** Queries PostgreSQL for structured business metrics
2. **Analysis Agent:** Performs statistical analysis and trend detection
3. **Visualization Agent:** Generates charts automatically
4. **Report Agent:** Writes natural language summaries

**Full Stack:**
```
FastAPI backend
    ↓
Agent Orchestrator (LangGraph)
    ├── Data Agent (SQL + Pandas)
    ├── Analysis Agent (Stats + ML)
    ├── Viz Agent (Matplotlib)
    └── Report Agent (LLM)
    ↓
PostgreSQL + ChromaDB
    ↓
React Frontend (simple chat UI)
```

**Why This Project?** This is exactly what Accenture, Deloitte, and TCS are building for their enterprise clients in 2025. This project proves you can build it.

---

## 🟢 PHASE 4: MLOPS + PRODUCTION (Days 121–160)
### *"Building Systems That Work in the Real World"*

---

### WEEK 17–18 — Docker + FastAPI (Days 121–133)

---

#### 📅 DAY 121–125 — FastAPI: Production API Development

**Why FastAPI?** Async Python, automatic OpenAPI docs, type validation with Pydantic, 3x faster than Flask. Used by Netflix, Microsoft, Uber.

```python
from fastapi import FastAPI, HTTPException, BackgroundTasks
from pydantic import BaseModel, Field
from typing import Optional, List
import uvicorn
import mlflow
import joblib
import pandas as pd
from contextlib import asynccontextmanager

# Load model at startup
ml_models = {}

@asynccontextmanager
async def lifespan(app: FastAPI):
    # Load ML model from MLflow
    model_uri = "models:/churn-predictor/Production"
    ml_models["churn"] = mlflow.sklearn.load_model(model_uri)
    print("✅ Model loaded")
    yield
    ml_models.clear()

app = FastAPI(
    title="Churn Prediction API",
    description="MNC-grade ML prediction service",
    version="1.0.0",
    lifespan=lifespan
)

class CustomerFeatures(BaseModel):
    tenure_months: int = Field(..., ge=0, le=120, description="Customer tenure in months")
    monthly_charges: float = Field(..., ge=0, description="Monthly charges in USD")
    total_charges: float = Field(..., ge=0)
    contract_type: str = Field(..., pattern="^(month-to-month|one-year|two-year)$")
    tech_support: bool
    online_security: bool
    
    class Config:
        json_schema_extra = {
            "example": {
                "tenure_months": 12, "monthly_charges": 65.0,
                "total_charges": 780.0, "contract_type": "month-to-month",
                "tech_support": False, "online_security": False
            }
        }

class PredictionResponse(BaseModel):
    customer_id: Optional[str]
    churn_probability: float
    churn_prediction: bool
    risk_level: str
    confidence: str
    recommended_action: str

@app.post("/predict", response_model=PredictionResponse, tags=["Predictions"])
async def predict_churn(features: CustomerFeatures):
    try:
        data = pd.DataFrame([features.dict()])
        prob = ml_models["churn"].predict_proba(data)[0][1]
        
        risk_level = "HIGH" if prob > 0.7 else "MEDIUM" if prob > 0.4 else "LOW"
        action_map = {
            "HIGH": "Offer 20% discount and dedicated support call immediately",
            "MEDIUM": "Send retention email with upgrade offer",
            "LOW": "Include in next monthly newsletter"
        }
        
        return PredictionResponse(
            churn_probability=round(prob, 4),
            churn_prediction=prob > 0.5,
            risk_level=risk_level,
            confidence="HIGH" if abs(prob - 0.5) > 0.3 else "LOW",
            recommended_action=action_map[risk_level]
        )
    except Exception as e:
        raise HTTPException(status_code=500, detail=str(e))

@app.get("/health")
async def health():
    return {"status": "healthy", "model_loaded": "churn" in ml_models}

if __name__ == "__main__":
    uvicorn.run("main:app", host="0.0.0.0", port=8000, reload=True)
```

---

#### 📅 DAY 126–130 — Docker: Package Everything

```dockerfile
# Dockerfile — production-grade multi-stage build
FROM python:3.11-slim AS base

WORKDIR /app

# Install dependencies separately for layer caching
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy application code
COPY . .

# Non-root user for security
RUN useradd -m -u 1000 appuser && chown -R appuser:appuser /app
USER appuser

EXPOSE 8000

# Health check
HEALTHCHECK --interval=30s --timeout=10s --start-period=30s --retries=3 \
    CMD curl -f http://localhost:8000/health || exit 1

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000", "--workers", "2"]
```

```yaml
# docker-compose.yml — full stack locally
version: '3.8'

services:
  api:
    build: .
    ports: ["8000:8000"]
    environment:
      - MLFLOW_TRACKING_URI=http://mlflow:5000
      - POSTGRES_URL=postgresql://user:pass@postgres:5432/ml_db
    depends_on: [postgres, mlflow, redis]
    volumes: ["./models:/app/models"]
    
  mlflow:
    image: python:3.11-slim
    command: mlflow server --host 0.0.0.0 --port 5000 --backend-store-uri postgresql://user:pass@postgres:5432/mlflow
    ports: ["5000:5000"]
    depends_on: [postgres]
    
  postgres:
    image: postgres:15
    environment:
      POSTGRES_DB: ml_db
      POSTGRES_USER: user
      POSTGRES_PASSWORD: pass
    volumes: ["postgres_data:/var/lib/postgresql/data"]
    
  redis:
    image: redis:7-alpine
    ports: ["6379:6379"]
    
  prometheus:
    image: prom/prometheus
    volumes: ["./monitoring/prometheus.yml:/etc/prometheus/prometheus.yml"]
    ports: ["9090:9090"]
    
  grafana:
    image: grafana/grafana
    ports: ["3000:3000"]
    environment:
      GF_SECURITY_ADMIN_PASSWORD: admin
    depends_on: [prometheus]

volumes:
  postgres_data:
```

---

#### 📅 DAY 131–135 — CI/CD with GitHub Actions

```yaml
# .github/workflows/ml-pipeline.yml
name: ML Pipeline CI/CD

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Set up Python
        uses: actions/setup-python@v5
        with:
          python-version: '3.11'
          
      - name: Install dependencies
        run: |
          pip install -r requirements.txt
          pip install pytest pytest-cov
          
      - name: Run unit tests
        run: pytest tests/ -v --cov=src --cov-report=xml
        
      - name: Check code quality
        run: |
          pip install ruff black
          ruff check src/
          black --check src/
          
  build-and-push:
    needs: test
    if: github.ref == 'refs/heads/main'
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      
      - name: Build Docker image
        run: docker build -t ml-api:${{ github.sha }} .
        
      - name: Run integration tests
        run: |
          docker run -d --name test-api -p 8000:8000 ml-api:${{ github.sha }}
          sleep 10
          curl -f http://localhost:8000/health
          docker stop test-api
```

---

### WEEK 19–20 — Monitoring + MLOps (Days 136–150)

---

#### 📅 DAY 136–140 — Model Monitoring with Evidently

```python
from evidently.report import Report
from evidently.metric_preset import DataDriftPreset, ClassificationPreset
from evidently.metrics import DatasetDriftMetric, ColumnDriftMetric
import pandas as pd

class ModelMonitor:
    """
    Production model monitoring system.
    Detects: data drift, concept drift, performance degradation.
    """
    
    def __init__(self, reference_data: pd.DataFrame, model_name: str):
        self.reference = reference_data
        self.model_name = model_name
    
    def check_data_drift(self, current_data: pd.DataFrame) -> dict:
        """Check if incoming data distribution has drifted from training data."""
        report = Report(metrics=[
            DataDriftPreset(),
            DatasetDriftMetric(),
        ])
        report.run(reference_data=self.reference, current_data=current_data)
        results = report.as_dict()
        
        drift_detected = results['metrics'][1]['result']['dataset_drift']
        drift_share = results['metrics'][1]['result']['share_drifted_columns']
        
        return {
            "drift_detected": drift_detected,
            "drift_share": drift_share,
            "alert": "CRITICAL" if drift_share > 0.5 else "WARNING" if drift_share > 0.2 else "OK"
        }
    
    def generate_monitoring_report(self, current_data: pd.DataFrame, 
                                    y_true: pd.Series, y_pred: pd.Series):
        report = Report(metrics=[
            DataDriftPreset(),
            ClassificationPreset(),
        ])
        report.run(reference_data=self.reference, current_data=current_data,
                   column_mapping={"target": "label", "prediction": "prediction"})
        report.save_html(f"monitoring_{self.model_name}_{pd.Timestamp.now().date()}.html")
        print(f"Monitoring report saved.")
```

---

#### 📅 DAY 141–150 — Full Production Stack + Kubernetes Basics

```yaml
# kubernetes/deployment.yaml — scale your API to handle thousands of requests
apiVersion: apps/v1
kind: Deployment
metadata:
  name: ml-api
  labels:
    app: ml-api
spec:
  replicas: 3  # 3 instances for high availability
  selector:
    matchLabels:
      app: ml-api
  template:
    metadata:
      labels:
        app: ml-api
    spec:
      containers:
      - name: ml-api
        image: ml-api:latest
        ports: [{containerPort: 8000}]
        resources:
          requests: {memory: "256Mi", cpu: "250m"}
          limits: {memory: "512Mi", cpu: "500m"}
        livenessProbe:
          httpGet: {path: /health, port: 8000}
          initialDelaySeconds: 30
          periodSeconds: 10
        readinessProbe:
          httpGet: {path: /health, port: 8000}
          initialDelaySeconds: 5
          periodSeconds: 5
---
apiVersion: v1
kind: Service
metadata:
  name: ml-api-service
spec:
  selector: {app: ml-api}
  ports: [{port: 80, targetPort: 8000}]
  type: LoadBalancer
---
apiVersion: autoscaling/v2
kind: HorizontalPodAutoscaler
metadata:
  name: ml-api-hpa
spec:
  scaleTargetRef:
    apiVersion: apps/v1
    kind: Deployment
    name: ml-api
  minReplicas: 2
  maxReplicas: 10
  metrics:
  - type: Resource
    resource:
      name: cpu
      target:
        type: Utilization
        averageUtilization: 70
```

---

## 🏆 PHASE 5: CAPSTONE PROJECTS (Days 151–180)

---

### CAPSTONE PROJECT 1: AI-Powered Fraud Detection System (Days 151–162)

**Business Problem:** An e-commerce company processes 500,000 transactions per day. 0.1% are fraudulent. Manual review is impossible. Build a real-time fraud detection system.

**System Architecture:**
```
Transaction Event
    ↓ Kafka (streaming)
    ↓ Feature Engineering Service (real-time + batch features)
    ↓ ML Model (XGBoost + neural network ensemble)
    ↓ Risk Score (0-100)
    ↓ Decision Engine (approve/review/decline)
    ↓ Alert System (if review)
    ↓ Monitoring Dashboard (Grafana)
```

**Technical Requirements:**
- Process transactions in <100ms latency
- Achieve >99% recall (minimize false negatives — missed fraud is costly)
- Model retrained weekly on new data
- Full MLflow tracking
- A/B test new model vs current model before full deployment
- Grafana dashboard showing: fraud rate, model accuracy, latency, drift metrics

**Dataset:** IEEE-CIS Fraud Detection (Kaggle, free, 590k transactions)

**GitHub Structure:**
```
fraud-detection-system/
├── data/                    # DVC tracked
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_feature_engineering.ipynb
│   └── 03_model_selection.ipynb
├── src/
│   ├── features/            # Feature engineering
│   ├── models/              # Model training
│   ├── api/                 # FastAPI service
│   └── monitoring/          # Evidently + Prometheus
├── docker-compose.yml
├── .github/workflows/
├── Makefile                 # `make train`, `make deploy`, `make test`
└── README.md                # Architecture diagram + demo GIF
```

---

### CAPSTONE PROJECT 2: Intelligent Document Processing Agent (Days 163–172)

**Business Problem:** A law firm receives 300+ contracts per day. Lawyers spend 2hrs per contract extracting key terms (parties, dates, clauses, obligations). Build an AI agent that extracts and summarizes contracts.

**Technical Stack:**
- **Document parsing:** PyMuPDF for PDFs, python-docx for Word
- **OCR:** Tesseract + PaddleOCR for scanned documents
- **LLM:** Llama 3.1 8B (local, free) via Ollama
- **Embeddings:** nomic-embed-text
- **Vector DB:** ChromaDB
- **Agent:** LangGraph workflow
- **API:** FastAPI
- **Frontend:** Gradio (rapid demo UI)

**Agent Workflow:**
```
Document Upload
    ↓
Text Extraction (PDF/Word/Image)
    ↓
Document Chunking
    ↓
Entity Extraction (Named Entities, Dates, Amounts)
    ↓
Key Clause Detection (via LLM)
    ↓
Risk Assessment (flag unusual clauses)
    ↓
Structured JSON Output + Summary Report
    ↓
Human Review Queue (if risk_score > threshold)
```

---

### CAPSTONE PROJECT 3: Full-Stack AI SaaS Platform (Days 173–180)

**Build a minimal but complete AI-powered SaaS product that you can show to any recruiter.**

**Product:** "DataChat" — Upload any CSV and chat with your data using natural language.

**Stack:**
- **Backend:** FastAPI + PostgreSQL + Redis
- **AI:** LangChain agent + Ollama (local LLM) + Pandas tools
- **Frontend:** React (simple, functional)
- **Auth:** JWT tokens
- **Deployment:** Docker Compose
- **Monitoring:** Prometheus + Grafana

**Features:**
1. Upload CSV → stored in PostgreSQL
2. Ask questions in natural language → agent generates + executes SQL/Pandas code
3. Auto-generates charts from query results
4. Export conversation + charts as PDF report
5. Basic user auth (login/register)

**Why This Is Portfolio Gold:**
- Shows full-stack capability
- Shows AI integration
- Shows production thinking (auth, DB, monitoring)
- Solves a real problem
- Can be demoed live in interviews

---

## 📚 PART 3 — DOCUMENTATION & PORTFOLIO STRATEGY

---

### GitHub Documentation Standards

**Every Project Must Have:**

```markdown
# Project Name

## 🎯 Problem Statement
What real-world problem does this solve? Who is affected?

## 🏗️ Architecture
[Architecture diagram — use Mermaid or draw.io]

## 🔬 Approach
What methods did you try? What worked? What didn't?

## 📊 Results
| Metric | Score |
|--------|-------|
| Accuracy | 94.2% |
| ROC-AUC | 0.97 |
| Inference latency | 45ms |

## 🛠️ Tech Stack
- Python 3.11, PyTorch 2.1
- FastAPI, PostgreSQL, Redis
- Docker, GitHub Actions
- MLflow, Evidently

## 🚀 How to Run
```bash
git clone ...
docker-compose up
curl http://localhost:8000/predict -d '{"feature": value}'
```

## 📁 Repository Structure
[explain what's in each folder]

## 💡 What I Learned
[be specific — this shows genuine engagement]

## 🔜 Future Improvements
[shows engineering thinking]
```

---

### Weekly Blogging Rhythm

**Every Sunday: Write 1 blog post on Hashnode**

Post types to rotate:
1. **"How I Built X"** — technical walkthrough of your project
2. **"Concept Deep Dive"** — explain a concept you struggled with (helps others + shows mastery)
3. **"Week N Reflection"** — what you learned, what was hard, what clicked
4. **"Architecture Decision"** — why you chose X over Y

**Example titles:**
- "Why I Chose XGBoost Over Neural Networks for Fraud Detection"
- "Building a Multi-Agent Research System with LangGraph and Llama 3"
- "From Zero to Docker: Containerizing My First ML Model"
- "Understanding Attention Mechanisms by Building One from Scratch"

---

### LinkedIn Strategy (Post Every 2 Weeks)

**Post Formula:**
```
Hook: "I built [X] that solves [Y real problem]"

The problem: [1-2 sentences]

My approach: [3-4 bullet points]

Results: [specific numbers]

What I learned: [genuine insight]

Link: [GitHub repo]

Tags: #MachineLearning #Python #AI #BuildInPublic
```

---

### Recruiter Visibility Checklist

By Day 180, you should have:
- [ ] 15+ GitHub repositories with proper READMEs
- [ ] 20+ weekly commit streaks visible on GitHub profile
- [ ] 8+ technical blog posts on Hashnode/Dev.to
- [ ] 5+ LinkedIn posts with project showcases
- [ ] 3 major portfolio projects with live demos (via Docker or Gradio)
- [ ] GitHub profile README with skills, projects, and contact
- [ ] Notion portfolio page (or personal website via GitHub Pages — free)

---

## 🧪 PART 4 — ACTIVE RECALL SYSTEM

### Conceptual Questions Bank (Test Yourself Daily)

**Phase 1 — Foundations:**
1. Explain gradient descent as if teaching a 10-year-old. Now explain why the learning rate matters.
2. If your model has 99% training accuracy and 60% test accuracy, what's wrong? How do you fix it?
3. Why do we split into train/validation/test sets? Why not just train/test?
4. What does a confusion matrix tell you that accuracy doesn't?
5. When would you prefer Precision over Recall? Give a real-world example.

**Phase 2 — Deep Learning:**
6. Why does backpropagation use the chain rule? Draw the computation graph for a 2-layer network.
7. What is the vanishing gradient problem? Why does ReLU help?
8. Explain batch normalization: what problem does it solve?
9. You have 500 labeled images. Should you use CNN from scratch or transfer learning? Why?
10. Why does attention mechanism work better than RNNs for long sequences?

**Phase 3 — Agentic AI:**
11. What is the difference between a tool-using LLM and an AI agent?
12. What is RAG and why does it reduce hallucination?
13. When would you use LangGraph over LangChain? Explain the state machine concept.
14. How do you handle a multi-agent system where Agent A depends on Agent B's output?
15. What is the "context window" of an LLM and why does it matter for agent design?

**Phase 4 — Production:**
16. Your model accuracy drops by 5% in production after 2 months. What are the possible causes?
17. Explain horizontal vs vertical scaling for an ML API. When do you use each?
18. What is a feature store and why does it matter at scale?
19. How does Docker ensure your model works the same on your laptop and the cloud?
20. What is the difference between MLflow experiments and MLflow models?

---

## 📊 PART 5 — PROGRESS TRACKING

### Milestone Checkpoints

| Milestone | Day | What You Should Be Able to Do |
|-----------|-----|-------------------------------|
| Foundation | 14 | Write a full EDA pipeline from scratch |
| ML Basics | 28 | Train, evaluate, and compare 4 ML models |
| Deep Learning | 50 | Build and train a CNN for image classification |
| NLP | 65 | Fine-tune DistilBERT for text classification |
| LLMs | 80 | Run a local LLM, implement RAG from scratch |
| Agents | 100 | Build a multi-agent system with tools and memory |
| Production | 130 | Package an ML model in a Docker container with FastAPI |
| MLOps | 150 | Set up experiment tracking, model monitoring, CI/CD |
| Portfolio | 180 | 3 complete portfolio projects with documentation |

---

## 🔧 PART 6 — COMPLETE FREE TECH STACK REFERENCE

### Every Tool You Will Use (All Free, All Open Source)

| Category | Tool | Why |
|----------|------|-----|
| **Language** | Python 3.11 | Industry standard for AI/ML |
| **IDE** | VS Code | Free, powerful, extensions |
| **Notebooks** | Jupyter Lab | Interactive exploration |
| **Data** | Pandas, NumPy | Core data manipulation |
| **Visualization** | Matplotlib, Seaborn, Plotly | Static and interactive charts |
| **Classical ML** | Scikit-learn, XGBoost, LightGBM | Traditional ML |
| **Deep Learning** | PyTorch | Research and production |
| **NLP** | HuggingFace Transformers, spaCy | State-of-the-art NLP |
| **LLMs (local)** | Ollama, llama.cpp | Run LLMs free locally |
| **Agents** | LangChain, LangGraph, CrewAI | Agent frameworks |
| **Vector DB** | ChromaDB, Qdrant | Semantic search |
| **Experiment Tracking** | MLflow | Track experiments |
| **Data Versioning** | DVC | Version datasets |
| **API** | FastAPI, Uvicorn | Production APIs |
| **Database** | PostgreSQL, SQLite | Structured data |
| **Cache** | Redis | Fast caching |
| **Queue** | Kafka (local) | Event streaming |
| **Container** | Docker, Docker Compose | Package everything |
| **Orchestration** | Kubernetes (k3s) | Scale containers |
| **CI/CD** | GitHub Actions | Automated testing/deploy |
| **Monitoring** | Prometheus, Grafana | Infrastructure metrics |
| **Model Monitoring** | Evidently AI | Data/model drift |
| **UI Demo** | Gradio, Streamlit | Quick ML demos |
| **Documentation** | MkDocs, Sphinx | Code documentation |
| **Version Control** | Git, GitHub | Source control |

---

## 🎯 FINAL WORDS

You are starting from zero. That is an advantage — you have no bad habits to unlearn.

The single biggest difference between people who succeed in AI/ML and those who don't is **consistency**. Not talent. Not IQ. **Consistency.**

Write code every day.
Document every day.
Commit to GitHub every day.

Three hundred days from now, you will look back at Day 1 and not recognize the person who started. The gap between "person who knows about AI" and "person who builds AI systems" is entirely built of daily practice.

**Your documentation is your proof. Build it daily.**

---

*Last updated: 2026 | Stack versions are current as of writing | All tools are free and open-source*