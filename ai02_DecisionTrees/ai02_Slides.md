---
marp: true
theme: default
paginate: true
---

# Decision Trees: Concepts & Coding
## Unit 1 — Lesson ai02

---

## What Is a Decision Tree?

A **decision tree** is a simple flowchart that asks yes/no questions to reach a final answer.

```
         START
          |
       Is it hot? (yes/no)
       /              \
     YES              NO
     |                |
   Wear shorts?    Wear coat?
    / \              / \
  YES NO            YES NO
  |   |             |   |
 🩳  👕            🧥  👔
```

Real-world examples:
- **Jacket Advisor**: Recommend clothing based on weather
- **Movie Rating Filter**: Suggest movies by genre and rating
- **Video Game AI**: Guide NPC behavior (chase player? search? flee?)

---

## Anatomy of a Decision Tree

Every tree has these parts:

| Part | Definition |
|------|-----------|
| **Root** | Starting point (first question) |
| **Node** | A decision point (asks a yes/no question) |
| **Branch** | Path from one node to another (yes/no) |
| **Leaf** | End point—the final answer (no more questions) |

**Example:**
```
    Is it cold?  ← ROOT (first decision)
    /        \
  YES        NO  ← BRANCHES
  |          |
Coat?      Tee?  ← NODES (more decisions)
/ \        / \
YES NO   YES NO  ← LEAVES (final answers)
```

---

## Tracing Through a Tree

To **trace** a tree, follow the branches based on yes/no answers.

**Example: Restaurant Recommender**
```
          Like spicy food?
          /              \
        YES              NO
        |                |
     Price < $15?      Price < $15?
     /        \         /        \
   YES       NO       YES        NO
   |         |        |          |
  Thai    Indian    Italian   French
 Bistro   Palace   Kitchen    Bistro
```

**Trace: "Yes to spicy, No to budget"**
- Start: Like spicy food? → YES
- Follow right branch: Price < $15? → NO
- Leaf: **Indian Palace**

---

## Why Use Decision Trees?

### Advantages ✓
- Easy to understand and explain
- Good for yes/no (binary) decisions
- Can be drawn or coded
- Works well for categorization & classification
- Natural way to handle multiple conditions

### Limitations ✗
- Only works for discrete yes/no questions (not continuous values)
- Can become very complex with many branches
- Not great for numerical prediction (use regression instead)
- Requires clear, distinct categories

---

## Coding Decision Trees: If/Elif/Else

Decision trees become Python code using **if/elif/else**.

```python
# Example: Jacket Advisor
temperature = int(input("Enter temperature (°F): "))

# First decision: Is it cold?
if temperature < 50:
    # Yes → cold, ask next question
    if temperature < 30:
        # Very cold
        print("Wear a heavy winter coat")
    else:
        # Just cold
        print("Wear a light jacket")
else:
    # No → warm, ask next question
    if temperature > 75:
        # Very warm
        print("Wear shorts")
    else:
        # Mild
        print("Wear a light shirt")
```

---

## Input Validation

Always validate user input before using it!

```python
# Problem: User might type "YES" or "yes" or "Yes"
# Solution: Use .lower() to convert to lowercase

userChoice = input("Do you like action movies? (yes/no): ").lower()

if userChoice == "yes":
    print("Here are action movies!")
elif userChoice == "no":
    print("Try drama instead!")
else:
    print("Please type 'yes' or 'no'")

# For numbers: Use .isdigit() to check if it's a valid number
ageString = input("Enter your age: ")

if ageString.isdigit():
    age = int(ageString)
    if age >= 13:
        print("You can watch PG-13 movies")
    else:
        print("Stick to G-rated movies")
else:
    print("Please enter a valid number")
```

---

## Complex Conditions: And/Or

Combine multiple questions with **and** and **or**.

```python
# Using AND: Both conditions must be true
if temperature < 50 and wind_speed > 20:
    print("Stay inside! It's cold AND windy")

# Using OR: At least one condition must be true
if temperature < 32 or has_snow_warning:
    print("School might be canceled!")

# Nested conditions (same as AND)
if temperature < 50:
    if wind_speed > 20:
        print("Stay inside!")
```

### Example: Study Plan Advisor
```python
studyHours = int(input("Hours studying per week? "))
classesAttended = int(input("Classes attended this month? "))

if studyHours >= 10 and classesAttended >= 8:
    print("You're set! Keep it up!")
elif studyHours >= 10 or classesAttended >= 8:
    print("Good effort—try to improve the other one")
else:
    print("Increase both study time and attendance")
```

---

## Common Debugging Issues

| Problem | Fix |
|---------|-----|
| **Indentation error** | Check spaces/tabs under `if` (must be consistent) |
| **Logic error** | Use `==` to compare, not `=` (which assigns) |
| **Case sensitivity** | Use `.lower()` to handle "YES" vs "yes" |
| **Type error** | Convert input with `int()` before math operations |

**Example:**
```python
# WRONG: Using = instead of ==
if age = 18:  # SyntaxError!
    print("Adult")

# CORRECT:
if age == 18:  # Comparison
    print("Adult")

# WRONG: Not converting input to int
temperature = input("Enter temp: ")
if temperature > 50:  # Comparing strings, not numbers!
    print("Warm")

# CORRECT:
temperature = int(input("Enter temp: "))
if temperature > 50:
    print("Warm")
```

---

## Summary

✓ Decision trees = flowcharts of yes/no questions
✓ Anatomy: root, nodes, branches, leaves
✓ Code with nested **if/elif/else**
✓ Validate input with **.lower()** and **.isdigit()**
✓ Combine conditions with **and/or**
✓ Use **==** to compare, **=** to assign

**Next: Build your own decision tree program!**
