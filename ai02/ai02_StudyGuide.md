# ai02 Decision Trees — Study Guide

## Vocabulary (15 terms)

1. **Decision Tree** — A flowchart that uses yes/no questions to reach a final answer; used in AI/classification
2. **Root** — The first (top) node in a decision tree; the starting point
3. **Node** — A point in the tree where a yes/no question is asked; can be a root, internal node, or leaf
4. **Branch** — A path from one node to another, labeled with yes/no
5. **Leaf** — A terminal node at the end of a tree branch; the final answer/classification
6. **Binary Decision** — A question with only two possible answers: yes or no
7. **Nested If** — An if statement inside another if statement; used to code tree branches
8. **Elif** — "Else if"; a statement used when multiple conditions are tested in sequence
9. **Condition** — A statement that can be true or false (e.g., `age > 18`, `name == "Alex"`)
10. **Validation** — Checking that user input is in the correct format (e.g., number, lowercase)
11. **.lower()** — Python string method that converts uppercase to lowercase
12. **.isdigit()** — Python string method that checks if a string contains only digits
13. **Logical Operator (AND)** — Combines conditions; both must be true (`if x > 5 and x < 10`)
14. **Logical Operator (OR)** — Combines conditions; at least one must be true (`if x < 0 or x > 100`)
15. **Classification** — The process of sorting data into categories using a decision tree

## Key Concepts

### Tree Anatomy
```
         START (Root)
           |
        Question?
        /        \
      YES        NO
      |          |
   Question?   Answer
   /    \
 YES    NO
  |      |
Answer Answer
```

### Example: Movie Recommender Tree
- **Root question**: "Like action?"
  - YES → "Do you prefer new movies?"
    - YES → Recommend: *Top Gun Maverick*
    - NO → Recommend: *Die Hard*
  - NO → "Do you like comedy?"
    - YES → Recommend: *The Grand Budapest Hotel*
    - NO → Recommend: *Inception*

## Python Patterns

### Pattern 1: Simple If/Else (Two Outcomes)
```python
weather = input("Is it raining? (yes/no): ").lower()

if weather == "yes":
    print("Bring an umbrella")
else:
    print("Sunscreen time!")
```

### Pattern 2: Nested If (Multiple Levels)
```python
temperature = int(input("Enter temp (°F): "))

if temperature > 75:
    if temperature > 85:
        print("Very hot—stay hydrated!")
    else:
        print("Warm—shorts weather!")
else:
    if temperature < 50:
        print("Cold—bring a coat!")
    else:
        print("Mild—light jacket!")
```

### Pattern 3: Multiple Conditions with And/Or
```python
# AND: Both must be true
if age >= 13 and has_parental_consent:
    print("You can create an account")

# OR: At least one must be true
if has_scholarship or score >= 90:
    print("You qualify for the program!")
```

### Pattern 4: Input Validation
```python
# Validate text input
choice = input("Enter choice (A/B/C): ").lower()
if choice in ["a", "b", "c"]:
    print(f"You chose {choice.upper()}")
else:
    print("Invalid choice!")

# Validate number input
ageStr = input("Enter age: ")
if ageStr.isdigit():
    age = int(ageStr)
    if age >= 18:
        print("Adult")
    else:
        print("Minor")
else:
    print("Please enter a valid number!")
```

## When to Use Decision Trees

### Good For ✓
- Categorization (sorting into groups)
- Classification (assigning labels)
- Simple yes/no logic chains
- Systems where the path to the answer is clear
- Educational purposes (easy to visualize)

### Not Good For ✗
- Continuous numerical prediction (use regression instead)
- Very complex logic with many branches
- Real-time decisions requiring immediate speed
- Cases where "maybe" or probability is the answer
- Large datasets (better: random forests or neural networks)

## Common Mistakes

| Mistake | Why It's Wrong | Fix |
|---------|---------------|-----|
| `if age = 18:` | `=` assigns, doesn't compare | Use `if age == 18:` |
| Comparing `"18" > 50` | Comparing strings, not numbers | Convert: `int(input(...))` |
| Not using `.lower()` | User types "YES" but code checks "yes" | Always use `.lower()` for text |
| Wrong indentation | Python relies on indentation for blocks | Consistent 4 spaces inside each `if` |
| Forgetting `elif` | Creates multiple separate `if` statements | Use `elif` for "else if" cases |

## ODE Competencies Aligned

- **5.1.2**: Describe basic structures and applications of computing (decision trees are a basic computing structure)
- **5.1.3**: Write programs using appropriate syntax and logic to solve problems (coding decision trees with if/elif/else)
- **2.14.1**: Gather, organize, and analyze data using appropriate tools and methods (tracing through trees, classifying inputs)

## Quick Reference: Code Template

```python
# ======================
# DECISION TREE TEMPLATE
# ======================

# Step 1: Get user input
userInput = input("Question 1 (yes/no)?: ").lower()

# Step 2: First decision
if userInput == "yes":
    # Step 3: Ask follow-up question
    followUp = input("Question 2 (yes/no)?: ").lower()

    if followUp == "yes":
        # Both yes → outcome A
        print("Result: A")
    else:
        # Yes, then no → outcome B
        print("Result: B")
else:
    # First was no
    followUp = input("Question 2 (yes/no)?: ").lower()

    if followUp == "yes":
        # No, then yes → outcome C
        print("Result: C")
    else:
        # Both no → outcome D
        print("Result: D")
```

## Practice Problems

1. **Draw it**: Create a decision tree for "What shoes should I wear?" (3 levels)
2. **Trace it**: Follow a path through a given tree with specific yes/no answers
3. **Code it**: Convert a simple tree diagram into if/elif/else code
4. **Validate it**: Add input validation to a decision tree program
5. **Combine**: Use `and`/`or` to merge two related conditions

## Resources

- **Slides**: ai02_Slides.md
- **Walkthrough**: ai02_Walkthrough.ipynb (with examples and try-this exercises)
- **Tasks**: ai02a_Task.ipynb, ai02b_Task.ipynb
- **Independent**: ai02_DIYTask.ipynb (build your own)
