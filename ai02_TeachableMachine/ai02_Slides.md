---
marp: true
theme: default
paginate: true
---

# Lesson 02: Train Your First AI
## Teachable Machine — Artificial Intelligence
### Medina County Career Center

*No code required — you'll train a real machine-learning model in your browser.*

---

# You're About to Train a Model

Before we write a single line of Python, you'll build a working AI **by hand** using
Google's **Teachable Machine**.

You'll teach a computer to tell two things apart — just by showing it **examples**.
That's the core of **supervised learning**: learn from labeled examples.

**Tool:** https://teachablemachine.withgoogle.com

---

# Supervised Learning in One Picture

```
  Labeled examples            Model             New input -> Prediction
  -----------------          -------            ----------------------
  [cat pics]  -> "cat"   =>  TRAIN  =>  [new pic] -> "87% cat, 13% dog"
  [dog pics]  -> "dog"
```

- Each group of examples is a **class** (a label).
- The model finds patterns that separate the classes.
- You test it on **new** images it has never seen.

---

# Today's Build

1. Create two **classes** (e.g., two animals)
2. Give each class **3–5 example images**
3. Click **Train Model**
4. **Test** it with brand-new images — read the confidence %
5. Add **more** training images, retrain, and see if it improves
6. Reflect: when was it accurate, and why?

---

# The Big Questions to Watch For

- Was the model **accurate** on new images?
- Which images did it **struggle** with? Why?
- What happened to accuracy when you added **more training data**?
- How could you make it **even better**?

These same questions come back in every ML lesson this year — decision trees, neural
networks, all of it. Teachable Machine is where the intuition starts.

---

# From Here to Python

Teachable Machine hides all the code. Over the next lessons you'll do the **same job in
Python** — split data, train a model, test it, measure accuracy — but you'll see every step.

**Today: the intuition. Soon: the controls.**

Head to the Walkthrough and train your first model!
