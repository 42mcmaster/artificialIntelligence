---
marp: true
theme: default
paginate: true
---

# What is Artificial Intelligence?

**Lesson 01: Introduction to AI**

Medina County Career Center | Ryan McMaster, CTE Instructor

---

## Learning Objectives

- Define artificial intelligence and distinguish it from traditional programming
- Identify examples of AI in everyday life
- Understand the difference between rule-based systems and learning systems
- Recognize the three main types of AI approaches

---

## What is Artificial Intelligence?

**Artificial Intelligence (AI)** is when computers perform tasks that typically require human intelligence:

- Recognizing faces in photos
- Understanding spoken language
- Making recommendations
- Playing games
- Driving cars
- Answering questions

---

## The Key Difference

**Traditional Programming:**
```
Input → Rules (written by programmer) → Output
```

**Artificial Intelligence:**
```
Input + Output Examples → AI learns patterns → Can handle new inputs
```

---

## Example: Spam Filter

### Traditional Programming Approach

```python
def is_spam(email):
    if "FREE MONEY" in email:
        return True
    if "CLICK HERE NOW" in email:
        return True
    if "You won" in email:
        return True
    return False
```

**Problem:** What if spam gets creative?

---

## Example: Spam Filter (continued)

### AI Approach

```
AI examines thousands of spam and non-spam emails
↓
AI learns patterns (without explicit rules)
↓
AI can identify NEW spam it's never seen before
```

**Key Insight:** The programmer doesn't write the rules—the AI discovers them!

---

## Real-World AI Examples

### 1. Netflix Recommendations
- **What:** Suggests shows you might like
- **How:** Analyzes watch history and learns patterns
- **Why AI:** Impossible to program rules for millions of users!

### 2. Snapchat Filters
- **What:** Recognizes your face and adds effects
- **How:** Learned from millions of face images
- **Why AI:** Can't code every face variation!

---

## Real-World AI Examples (continued)

### 3. Google Translate
- **What:** Translates between 100+ languages
- **How:** Learned from millions of translated documents
- **Why AI:** Can't program every grammar rule!

### 4. Siri / Alexa
- **What:** Understands spoken commands
- **How:** Learned speech patterns from recordings
- **Why AI:** Can't code every accent and phrase!

---

## From Traditional Programming to AI

1. **Rule-Based Systems** (NOT AI - The Precursor)
2. **Machine Learning** (THIS IS AI!)
3. **Neural Networks** / Deep Learning

---

## 1. Rule-Based Systems (NOT AI)

**Hard-coded decision trees and expert systems**

- Programmer writes explicit rules
- Computer follows them exactly—no learning happens

**Example:**
"If temperature > 80°F, predict shorts."

**Key Point:** These are **NOT AI** because they don't learn from data.

---

## 2. Machine Learning (THIS IS AI)

The programmer provides **labeled examples**, not rules.
The AI **learns the relationship** between inputs and outputs from data.

Two main types:
- **Regression Models** (predicting numbers)
- **Classification Models** (predicting categories)

---

## Machine Learning: Regression

**Predicts numbers**

- **Linear Regression** - Best straight line through data
- **Polynomial Regression** - Curved line for complex patterns
- **Random Forest Regression** - Many trees vote on prediction

**Example:** Predict tomorrow's temperature

---

## Machine Learning: Classification

**Predicts categories**

- **Logistic Regression** - Probability-based categories
- **Decision Trees** - Automatic if/then rules from data
- **Random Forests** - Many trees vote on category
- **Support Vector Machines** - Best boundary lines

**Example:** Spam or not spam?

---

## 3. Neural Networks / Deep Learning

Inspired by the human brain, learns complex patterns through layers.

**What:** Handles very complex tasks
- Image recognition
- Language translation
- Voice recognition
- Self-driving cars

---

## Summary

- **Hard-coded rules** = NOT AI
- **Machine Learning** = AI learns from data
- **Regression** predicts numbers
- **Classification** predicts categories
- **Neural networks** handle complex tasks

**The big idea:** AI learns from data; rules are discovered, not written.

---

## When to Use Each Approach

| Approach | Best For | Example |
|----------|----------|---------|
| **Traditional Programming** | Simple, clear rules | Calculator, login system |
| **Rule-Based AI** | Multiple conditions | Medical diagnosis, game AI |
| **Machine Learning** | Pattern recognition | Face recognition, spam detection |

---

## AI is Already Everywhere

**Social Media:**
- Feed recommendations? AI
- Face tagging? AI
- Content moderation? AI

**Shopping:**
- Product suggestions? AI
- Fraud detection? AI

**Entertainment:**
- YouTube suggestions? AI
- Spotify playlists? AI

---

## What AI is NOT

❌ **AI is not magic** - It's math and patterns

❌ **AI is not always "smart"** - It can make mistakes

❌ **AI doesn't "understand" like humans** - It recognizes patterns

❌ **AI can't do everything** - It's trained for specific tasks

---

## Key Takeaways

1. AI makes computers act intelligently without programming every rule
2. Traditional programming requires explicit instructions
3. Machine Learning (AI) discovers patterns from data automatically
4. AI is everywhere in modern technology
5. Different problems need different AI approaches

---

## Discussion Questions

**Think about these:**

1. Can you identify 3 places you used AI today without realizing it?

2. When would traditional programming be BETTER than AI?

3. What's something hard to program traditionally but easy for AI?

---

## Next Steps

We'll explore AI concepts deeper through code and real examples.

**Stay curious—AI is the future!**
