---
marp: true
theme: default
paginate: true
---

# Lesson 08: Natural Language Processing
## Artificial Intelligence
### Medina County Career Center

---

# Computers Read Numbers, Not Words

Every NLP task has the same two-step shape:

1. **Text -> numbers** so a model can learn from it
2. (for generation) **numbers -> text** so humans can read the output

Today: two classic tasks —
- **Sentiment analysis**: is this review positive or negative?
- **Text generation**: write new sentences from a sample of text

---

# Tokenization & Bag-of-Words

**Tokenize** = split text into words (tokens).
**Bag-of-Words** = represent a sentence as word **counts**, ignoring order.

| Review | great | boring | movie |
|---|---|---|---|
| "a great movie" | 1 | 0 | 1 |
| "a boring movie" | 0 | 1 | 1 |

`CountVectorizer` does this for you. You already met this as *text -> features* in **ai04**.

---

# Sentiment Pipeline (you already know the shape)

```python
X_train, X_test, y_train, y_test = train_test_split(
    reviews, labels, test_size=0.25, stratify=labels)

vec = CountVectorizer()
X_train_vec = vec.fit_transform(X_train)   # fit on TRAIN only
X_test_vec  = vec.transform(X_test)

model = LogisticRegression().fit(X_train_vec, y_train)
```

Split -> vectorize -> train -> evaluate. Same recipe as decision trees, new data type.

---

# Our Result: 94% Accuracy

```
confusion: [[24, 1], [2, 22]]   # [[TN, FP], [FN, TP]]
```

Only **3 wrong out of 49** — and they're the **ambiguous** reviews
("a great film but a bit boring").

**Why the misses?** Bag-of-Words ignores order, so it can't tell
**"not good"** from **"good."** Negation and sarcasm are genuinely hard.

---

# Text Generation: The Markov Chain

The simplest generator — no neural network, just counting:

> Look at the current word. Pick the next word from the ones that
> **actually followed it** in the training text.

```
"the" -> [movie, story, plot, pacing, ending, ...]
```

- **Order-1** (1 word of memory): grammatical but wanders
- **Order-2** (2 words of memory): more coherent, but replays the source

Coherence vs. originality — the central trade-off of every language model.

---

# From Markov to ChatGPT

Your 20-line Markov chain and ChatGPT do the **same core job**:

> **Predict the next token from the ones before it.**

| | Memory | How it works |
|---|---|---|
| **Markov chain** | 1–2 words | counts what followed what |
| **RNN / LSTM** (CodeHS) | a sentence | learns patterns in sequence |
| **Transformer** (ChatGPT) | hundreds of words | learns patterns, huge scale |

Same idea — the difference is **scale and memory**.

---

# Bias Lives in the Text

An NLP model is only as fair as the language it learned from.

- Reviews, resumes, and posts carry human bias
- A model trained on them **absorbs** that bias
- More on this in **ai11 (Ethics)**

---

# Your Turn

1. **Walkthrough** — build the sentiment model + a Markov generator
2. **Task 8a** — train sentiment, test your own sentences
3. **Task 8b** — generate text, compare order-1 vs order-2
4. **DIY** — a better classifier and/or your own generator

**Next up: Neural Networks — where these ideas get their "grown-up" engine.**
