# Certiport AI Fundamentals — Student Study Guide

A self-paced review for the Certiport / GMetrix AI Fundamentals certification exam.

---

## How to Use This Guide

This guide is structured as **twelve short modules**, building from the most foundational ideas (what AI actually *is*) up through the most technical (how data is encoded for a model) and finishing with test-taking strategy. Work through them in order — each module assumes the ones before it.

Every module follows the same rhythm:

1. **Concept** — read the explanation.
2. **Anchor** — a small diagram, table, or rule of thumb you should be able to redraw from memory.
3. **Self-check** — exam-style question(s) plus "explain the distractor" practice.

The single most powerful study habit for this exam is **explaining why the wrong answers are wrong**. If you can do that, the right answer takes care of itself.

---

## Table of Contents

1. [What AI Is (and What It Isn't)](#module-1--what-ai-is-and-what-it-isnt)
2. [The Three Families of Machine Learning](#module-2--the-three-families-of-machine-learning)
3. [Measuring Relationships: Correlation](#module-3--measuring-relationships-correlation)
4. [The AI Technique Zoo](#module-4--the-ai-technique-zoo)
5. [Data Foundations: Features, Labels, and Representativeness](#module-5--data-foundations-features-labels-and-representativeness)
6. [Data Quality and ETL](#module-6--data-quality-and-etl)
7. [Encoding Data for an AI Model](#module-7--encoding-data-for-an-ai-model)
8. [Securing AI Systems](#module-8--securing-ai-systems)
9. [Choosing and Validating a Model](#module-9--choosing-and-validating-a-model)
10. [Ethics, Bias, and Proxy Features](#module-10--ethics-bias-and-proxy-features)
11. [AI Project Management: Scope Creep](#module-11--ai-project-management-scope-creep)
12. [Test-Taking Strategy and Final Review](#module-12--test-taking-strategy-and-final-review)
13. [Exam-Day Cheat Card](#exam-day-cheat-card)
14. [Master Glossary](#master-glossary)

---

## Module 1 — What AI Is (and What It Isn't)

### Concept

The first thing the exam tests is whether you understand what AI fundamentally is. Most wrong answers in this section come from confusing AI with two things it is not: a hard-coded rule system and a magic general-purpose solver.

**AI is, at its core, a function approximator.** It takes inputs and produces outputs by learning a mathematical approximation of the relationship between them. To do this, it needs three things:

- **Data** — examples to learn from.
- **Dynamic data** — the relationship can shift, and the model can adapt.
- **A function-approximation method** — an algorithm that can learn the input-output mapping.

**AI is NOT:**

- A general solution to every problem (it is built for specific tasks).
- A system that only works on static data (the data and model evolve).
- A set of human-written `if/then` rules (that's traditional programming).

### Anchor: The Turing Test

The **Turing Test** is one of the most-tested footnote topics. Memorize this exact framing:

> The Turing Test is a method to **measure** whether a machine exhibits human-like intelligence. It is not a method to *build*, *design*, or make AI more *efficient*.

If a question asks "what is the Turing Test for?" the answer is **measuring** intelligence — never building it.

### Self-Check

> Which of the following are required for an AI system? (Choose 3)
> A) A general solution to all problems
> B) Data
> C) Dynamic data
> D) Static data only
> E) Function approximation

**Answer:** B, C, E.
**Why the others are wrong:** A is wrong because AI is task-specific. D is wrong because static-only data can't capture changing patterns; AI needs dynamic data.

---

## Module 2 — The Three Families of Machine Learning

### Concept

Almost every "what kind of problem is this?" question on the exam can be answered by walking down a single decision tree. Memorize this tree — it unlocks a huge fraction of the question bank.

### Anchor: The Problem Classification Tree

```
Is the data labeled?
├── YES → SUPERVISED LEARNING
│          ├── Continuous numeric output? → REGRESSION
│          │     (e.g., predicting salary, house price, temperature)
│          └── Category output?            → CLASSIFICATION
│                (e.g., spam / not spam, cat / dog / bird)
└── NO  → UNSUPERVISED LEARNING
           └── Grouping similar things?   → CLUSTERING
                 (e.g., customer segmentation, recommendations)

Separate branch:
Learning from rewards and penalties?       → REINFORCEMENT LEARNING
      (e.g., self-improving chatbot, game-playing agents)
```

A few clarifications students often miss:

- **Supervised** = labeled training data. The "supervisor" is the label.
- **Unsupervised** = no labels. You're discovering structure.
- **Reinforcement** = no labeled examples; the model gets rewards for good behavior and learns by trial and error.
- **Clustering is unsupervised**, even though it produces groups. It does not predict a *known* class — it discovers groups.

### Self-Check

> What is the goal of clustering a set of data?
> A) To split data into groups based on similarities
> B) To predict the class of data
> C) To measure relationships between variables
> D) To label data for supervised learning

**Answer:** A.
**Why the others are wrong:**

- B is *classification* (supervised), not clustering.
- C is *correlation analysis* — a different concept entirely.
- D sounds plausible but clustering doesn't *create* labels; it groups by similarity.

> A self-improving chatbot that gets better as people interact with it is using which approach?
> A) Supervised learning
> B) Clustering
> C) Reinforcement learning
> D) Linear regression

**Answer:** C. Rewards/feedback loop = reinforcement learning.

---

## Module 3 — Measuring Relationships: Correlation

### Concept

The exam asks about the **correlation coefficient** — a number that describes how strongly two variables are related and in which direction.

### Anchor: The Correlation Ruler

```
   −1 ─────────── 0 ─────────── +1
   strong         no            strong
   negative       relationship  positive
```

Rules to memorize:

- **Range:** −1 to +1.
- **Sign tells you direction.** Negative means as one goes up the other goes down; positive means they move together.
- **Magnitude tells you strength.** Closer to ±1 = stronger; closer to 0 = weaker.
- **0 means no linear relationship.**

So **−0.94** is a *strong negative* relationship, and **+0.94** is a *strong positive* relationship — both are equally strong, just opposite directions. **0.05** is essentially no relationship.

### Self-Check

> A dataset has a correlation coefficient of −0.91 between hours of sleep and reported stress. What does this tell you?
> A) There is no relationship.
> B) Sleep causes lower stress.
> C) There is a strong negative relationship.
> D) The data is incorrect because correlation can't be negative.

**Answer:** C.
**Why the others are wrong:** A ignores the magnitude. B confuses correlation with causation (correlation never proves causation). D is factually wrong — correlation can absolutely be negative.

---

## Module 4 — The AI Technique Zoo

### Concept

The exam gives you a real-world scenario and ask "which AI technique is this?" Memorize this matching list — there are only a handful, and they reappear constantly.

### Anchor: Technique → Use Case

| Technique                              | Canonical Use Case                                    |
| -------------------------------------- | ----------------------------------------------------- |
| ML-based time series analysis          | Business forecasts, weather, stock predictions        |
| Conversational AI                      | AI text generators, chat assistants                   |
| Generative Adversarial Network (GAN)   | Creating new data that resembles existing data        |
| Reinforcement Learning                 | A self-improving chatbot or game AI                   |
| Real-Time Object Recognition           | Detecting that a bus is arriving                      |
| Optical Character Recognition (OCR)    | Reading the license plate on the bus                  |
| Automatic Alternative Text             | Describing a photo for a visually impaired user       |
| Speech Recognition                     | Asking your phone for directions                      |
| Clustering                             | Grouping similar customers / building recommendations |
| Regression                             | Predicting a continuous number                        |
| Classification                         | Predicting a category                                 |

### Self-Check

> A blind student wants their phone to describe what's in a photograph. Which AI technique is most appropriate?
> A) OCR
> B) Automatic Alternative Text
> C) Speech Recognition
> D) Real-Time Object Recognition

**Answer:** B.
**Why the others are wrong:**

- A (OCR) reads *text* from images, not scenes.
- C converts *speech to text*, the opposite direction.
- D is for live objects in motion (cameras, video), not still photos.

---

## Module 5 — Data Foundations: Features, Labels, and Representativeness

### Concept

If AI is a function approximator, then **data is what the function is approximated from**. Understanding the data side of AI is the most heavily tested topic on the exam.

### Anchor: Features vs. Labels

```
FEATURES (X) → what you observe → INPUTS  to the model
LABELS   (Y) → what you predict  → OUTPUTS from the model

Training data needs BOTH.
Only labels = useless. Only features = unsupervised at best.
```

Example: predicting whether it will rain tomorrow.

- **Features:** temperature, humidity, barometric pressure, wind speed.
- **Label:** rained / didn't rain.

If you only have *precipitation* records, you have a label history but no predictive features — you can't train a model.

### Anchor: The Representative Data Checklist

A model is only as fair and accurate as the data it learns from. Good training data should include:

- **Varied conditions** — different lighting, exposure, angles, times of day.
- **Demographic diversity** — all genders, all skin tones, all ages.
- **Varied backgrounds and contexts.**
- **Honest, informed-consent participants.** (This phrase appears frequently as a correct answer — memorize it.)

Bad training data is collected under a single condition (e.g., one lighting setup, one demographic), or labeled too coarsely for the task.

### Anchor: Data Collection Method by Data Type

| Data Type           | Best Collection Method                    |
| ------------------- | ----------------------------------------- |
| Narrative data      | Interviews                                |
| Structured ratings  | Questionnaires / NPS surveys              |
| Sensor data         | Devices (e.g., autonomous-car sensors)    |
| Voice data          | Smart speakers / smart-home devices       |

### Self-Check

> A team is training a face detector for security cameras. Which of the following would most improve the dataset?
> A) Collect images from a single high-quality studio with consistent lighting.
> B) Collect images across many lighting conditions, ages, skin tones, and angles, with informed consent.
> C) Use binary "face / no face" labels only and collect mostly daytime images.
> D) Use only volunteer images without consent forms.

**Answer:** B.
**Why the others are wrong:** A creates a fragile model that fails in real conditions. C oversimplifies labels. D is an ethics violation.

---

## Module 6 — Data Quality and ETL

### Concept

Before data can train a model, it has to be cleaned. The exam tests whether you know which cleaning actions to take in which order.

### Anchor: The Data Cleaning Hierarchy

When you find a problem in your dataset, **prefer fixing over deleting**, and **prefer column-level decisions over row-level deletion**.

| Problem                                       | Best Action                                          |
| --------------------------------------------- | ---------------------------------------------------- |
| Duplicate rows                                | Remove the duplicates                                |
| Missing values                                | Impute (fill in) OR drop the *column* if too sparse  |
| Out-of-range values (e.g., 0 where min is 1)  | Replace with the lower bound; do not drop the row    |
| Scrambled / incomprehensible values           | Flag and clean during validation                     |

### Anchor: Validation Priorities

When doing **upfront** or **holistic** validation (the kind the exam asks about), focus your time on issues that are:

- **Easy to detect** — patterns you can find quickly.
- **High-impact** — they affect many rows or distort the model.

Examples worth prioritizing: scrambled values, incomprehensible values, age/freshness of the data.

**Deprioritize** individual one-off errors and very small groups of errors at this stage — they take a long time to fix and have low impact early on.

### Self-Check

> While preparing a dataset, you find 12 duplicate rows, 200 rows missing one of 30 columns, and a few rows where age is recorded as 0 but minimum age should be 1. What should you do first?
> A) Delete every row with any issue.
> B) Remove duplicates, impute missing values (or drop the column if needed), and replace out-of-range ages with 1.
> C) Leave the data as-is and rely on the model to figure it out.
> D) Manually review every individual row.

**Answer:** B. Apply the hierarchy. D wastes time on low-impact details before high-impact ones are addressed.

---

## Module 7 — Encoding Data for an AI Model

### Concept

Models don't read raw photos, raw text, or raw spreadsheets — they need data in a numeric form that matches the kind of data it is. Picking the wrong encoding is the most common technical error the exam tests.

### Anchor: The Data Format Triage Chart

```
Numeric AND ordered (price, age, temperature)   → use as-is (often normalized)
Numeric but actually CATEGORICAL (ZIP code)     → ONE-HOT ENCODE
Images                                          → tensor of shape H × W × channels
Text                                            → tokenize / embed
Time-ordered sequences                          → time series structure
```

Key rules to memorize:

- **An RGB image of size H × W → tensor of shape H × W × 3.** A 224×224 RGB image becomes a 224 × 224 × 3 tensor. Grayscale images become H × W × 1.
- **ZIP codes are categories, not quantities.** 90210 is not "greater than" 10001. Numeric-looking but categorical fields must be one-hot encoded (or embedded), never fed in as raw integers.
- **Time series data has order.** Don't shuffle it like normal tabular data.

### Self-Check

> What shape is the input tensor for a 128 × 128 color (RGB) image?
> A) 128 × 128
> B) 128 × 128 × 1
> C) 128 × 128 × 3
> D) 128 × 3

**Answer:** C. Three color channels = the third dimension is 3.

> A dataset includes a "ZIP code" column with values like 44256 and 10001. How should this column be encoded?
> A) Use the raw integers — they're already numbers.
> B) One-hot encode them as categorical values.
> C) Sort them and replace with their rank.
> D) Drop the column.

**Answer:** B. ZIP codes look numeric but represent unordered categories.

---

## Module 8 — Securing AI Systems

### Concept

AI projects often need API keys, source code, and external services. The exam tests whether you can match each security concern to the right tool.

### Anchor: The Security Layer Stack

| Concern                                      | Correct Tool         |
| -------------------------------------------- | -------------------- |
| Granting permission with implicit usage policy | Trust Factoring    |
| Storing source code privately                | GitHub (private repo) |
| Holding API keys outside the codebase        | Environmental variables |
| Encrypted, managed secret storage            | AWS Secrets Manager  |

The biggest mistake students make is hard-coding API keys directly into a script. Don't. Keys belong in environment variables at minimum, or — better — a managed secrets service like AWS Secrets Manager.

### Self-Check

> Where is the *worst* place to store a production API key?
> A) An AWS Secrets Manager entry
> B) An environment variable on the server
> C) Hard-coded as a string in your Python file checked into GitHub
> D) A `.env` file excluded by `.gitignore`

**Answer:** C. Anything that ends up in version control is a leak waiting to happen.

---

## Module 9 — Choosing and Validating a Model

### Concept

Not every model is the right fit for every problem. The exam asks both *how to pick a model* and *how to know when a model has gone wrong*.

### Anchor: Model Selection Criteria

A good model is:

- **Skillful enough** given the time and resources available.
- **Compliant with stakeholder constraints** (latency, cost, interpretability, fairness).

A model is **NOT** chosen because it has high bias. High bias is a *problem*, not a goal.

### Anchor: Underfitting vs. Overfitting

```
UNDERFITTING → model too simple → misses patterns → bad on training AND test data
OVERFITTING  → model too complex → memorizes noise → great on training, bad on test
```

Memorize this one-liner: **Overfitting means the model fits the training data too closely — it has learned the noise rather than the signal.**

### Self-Check

> A model achieves 99% accuracy on training data but only 62% on test data. What is most likely happening?
> A) Underfitting
> B) Overfitting
> C) The data is perfectly clean
> D) The model has high bias

**Answer:** B. The huge gap between training and test performance is the textbook sign of overfitting.

---

## Module 10 — Ethics, Bias, and Proxy Features

### Concept

This is the single most important conceptual topic on the exam. Get this one right and you'll pick up several questions.

**Removing a biased feature does not remove bias if correlated proxy features remain.**

A "proxy feature" is a column that is correlated with the sensitive attribute you removed. Even if you delete the obvious one, the model can learn the same pattern through other columns.

### Anchor: The Proxy Bias Problem

Imagine a hiring model where you remove "gender" from the resume to make hiring fair. But you leave in:

- First name (often gendered)
- College sports played (e.g., women's volleyball)
- ZIP code (correlated with demographics)
- Hobbies, school clubs, pronouns in narrative sections

The model can still infer gender from these proxies and reproduce the original bias. Removing one column is **fairness theater** — it doesn't fix the underlying problem.

### What Actually Helps

- **Identify and address all proxy features**, not just the obvious one.
- **Audit model outputs across demographic groups** to detect disparate impact.
- **Use consented, representative data** in the first place.
- **Continuously monitor** the model after deployment, since bias can re-emerge.

### Self-Check

> A company removes "gender" from its hiring model. The model still produces gender-biased outcomes. What is the most likely explanation?
> A) The model is broken and should be retrained.
> B) Other features in the dataset (such as name, college club, ZIP code) act as proxies for gender.
> C) AI cannot be biased.
> D) The model needs more training data of any kind.

**Answer:** B. This is the proxy-bias problem in one sentence.
**Why the others are wrong:** A misdiagnoses the issue. C is factually false. D doesn't address the root cause; more biased data makes things worse, not better.

> Exit-ticket sentence to memorize:
> *A "fairness-washed" AI is worse than an obviously biased one because users assume it's safe to trust.*

---

## Module 11 — AI Project Management: Scope Creep

### Concept

The exam includes several questions about running an AI project as a *project* — managing client requests, schedules, and budgets.

### Anchor: Key Definitions

- **Scope creep** — adding features beyond the agreed-upon scope. Causes missed deadlines and blown budgets.
- **Gold-plating** — adding extras the client didn't ask for. A specific form of scope creep.
- **Constraints** — limits placed on a project (time, budget, features). The correct *prevention* for scope creep is **placing constraints** on the project.

### What to Do When Mid-Project Changes Are Proposed

If a stakeholder mid-project asks for "just one more feature" that would increase the schedule and budget:

- ✅ **Place constraints** on the project — say no, or require formal change control.
- ❌ Don't silently accept the change.
- ❌ Don't add gold-plated extras to "be helpful."
- ❌ Terminating the project doesn't *prevent* scope creep — it only reacts to it.

### Self-Check

> Three weeks into an AI project, the client asks for an additional dashboard. What is the best response?
> A) Add it quietly to keep the client happy.
> B) Terminate the project to prevent further changes.
> C) Place constraints on the project — defer or formally negotiate the addition.
> D) Replace an existing feature with the new one without telling anyone.

**Answer:** C.

---

## Module 12 — Test-Taking Strategy and Final Review

### The Distractor-Autopsy Method

For every practice question, do this:

1. Pick your answer.
2. **For each *wrong* option, write one sentence explaining why it is wrong.**
3. Only then check the answer key.

If you can articulate why every distractor is wrong, you have actually mastered the concept. If you can't, that's where to study next.

### One Sentence to Repeat During the Exam

Pick one of these and repeat it under your breath whenever you get stuck:

- *"AI approximates a function and needs data."*
- *"Removing a biased column doesn't remove bias."*
- *"ZIP codes are categories."*
- *"The Turing Test measures intelligence — it doesn't build it."*

### Mock Quiz (10 Questions Across the Whole Exam)

Try these timed — about 2 minutes per question. Answers and explanations follow.

1. Which three things does an AI system require? (Choose 3) A) A general solution B) Data C) Dynamic data D) Static data only E) Function approximation
2. What does a correlation coefficient of −0.94 indicate?
3. A self-improving chatbot uses which approach: supervised, unsupervised, or reinforcement learning?
4. Which AI technique is used to read a license plate from a photo of a car?
5. A face-detection dataset uses photos taken under one lighting condition only. What's the main risk?
6. You discover duplicate rows, missing values, and a few out-of-range entries. What's the right cleaning order?
7. What is the input tensor shape for a 224 × 224 RGB image?
8. Where should production API keys *not* be stored?
9. A company removes "gender" from its hiring model but bias persists. Why?
10. A client asks mid-project for a new dashboard. What should the team do?

#### Answer Key (cover until done)

1. **B, C, E** — see Module 1.
2. **Strong negative relationship** — Module 3.
3. **Reinforcement learning** — Module 2.
4. **OCR (Optical Character Recognition)** — Module 4.
5. **The model becomes fragile and fails under different real-world lighting** — Module 5.
6. **Remove duplicates → impute missing values (or drop the column) → replace out-of-range values with the lower bound. Avoid mass row deletion.** — Module 6.
7. **224 × 224 × 3** — Module 7.
8. **Hard-coded as strings in source files committed to a repository.** — Module 8.
9. **Proxy features (name, ZIP, school, etc.) still encode gender.** — Module 10.
10. **Place constraints on the project — defer or negotiate formally.** — Module 11.

---

## Exam-Day Cheat Card

Read this on the morning of the exam. It's the whole guide compressed into a single paragraph:

> AI needs data, works on dynamic data, and is a function approximation — it is not a general solution and is not a hard-coded rule system. The Turing Test *measures* intelligence; it does not build it. Supervised learning uses labeled data — regression predicts continuous values, classification predicts categories. Unsupervised clustering groups unlabeled data by similarity. Reinforcement learning improves from rewards. Correlation coefficients near ±1 are strong; near 0 is none. Removing a biased feature does not eliminate bias if correlated proxy features remain. In upfront data validation, prioritize easy-to-detect, high-impact issues like scrambled or incomprehensible values and stale data; deprioritize one-off individual errors. Choose models that are skillful enough given resources and meet stakeholder constraints; overfitting means the model fits training data too closely. Prevent scope creep by placing constraints on the project, not by gold-plating or silently accepting changes. RGB images encode as H × W × 3 tensors. ZIP codes are categorical, not numerical. Secure API keys with a secrets manager — never inline in code committed to a repo.

---

## Master Glossary

**AI (Artificial Intelligence)** — a function-approximation system that learns patterns from data, as opposed to following hard-coded rules.

**Automatic Alternative Text** — AI feature that generates text descriptions of images for accessibility.

**Bias (in ML)** — systematic error in model predictions, often resulting from biased training data or proxy features.

**Classification** — supervised learning that predicts a category (spam / not spam).

**Clustering** — unsupervised learning that groups unlabeled data by similarity.

**Conversational AI** — text-generation systems used for chat assistants.

**Correlation Coefficient** — a number from −1 to +1 measuring the strength and direction of a linear relationship between two variables.

**ETL (Extract, Transform, Load)** — the process of preparing raw data for analysis or model training.

**Feature** — an input variable used by a model.

**GAN (Generative Adversarial Network)** — model architecture for generating new data that resembles training data.

**Gold-Plating** — adding unrequested extras to a project; a form of scope creep.

**Informed Consent** — agreement from data subjects to participate, with full understanding of the use of their data.

**Label** — the output value the model is trained to predict.

**OCR (Optical Character Recognition)** — extracting text from images.

**One-Hot Encoding** — converting categorical values into a set of binary columns.

**Overfitting** — when a model fits training data too closely and fails to generalize.

**Proxy Feature** — a feature correlated with a sensitive attribute, allowing bias to leak in even when the sensitive attribute is removed.

**Regression** — supervised learning that predicts a continuous numeric value.

**Reinforcement Learning** — learning through rewards and penalties from interaction.

**Scope Creep** — uncontrolled expansion of project requirements beyond the original agreement.

**Supervised Learning** — learning from labeled data.

**Tensor** — a multi-dimensional array used to represent inputs to a model (e.g., images as H × W × 3).

**Time Series Analysis** — modeling data with a temporal order, used for forecasting.

**Trust Factoring** — granting permission with implicit usage policy.

**Turing Test** — a method for *measuring* whether a machine exhibits human-like intelligence (not for building it).

**Unsupervised Learning** — learning patterns from unlabeled data.
