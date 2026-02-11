---
marp: true
theme: default
paginate: true
---

# Machine Learning with Decision Trees
## Lesson ai03: Complete Walkthrough

**AI/ML Course | Medina County Career Center**
*Building predictive models with the Titanic dataset*

---

# What You'll Learn

By the end of this lesson, you'll know how to:

1. **Load and explore** real-world data
2. **Clean and prepare** data for machine learning
3. **Build a decision tree** model
4. **Evaluate** how well your model predicts
5. **Visualize** your tree and understand feature importance

**Real dataset**: 891 Titanic passengers
**Goal**: Predict who survived

---

# What is a Decision Tree?

A **decision tree** is like a flowchart that makes predictions by asking yes/no questions.

```
            Is fare > $30?
           /               \
         YES               NO
         /                   \
    Is female?          Predict:
    /      \            Did not survive
  YES      NO
   |        |
Predict:  Predict:
Survived  Did not
          survive
```

The computer learns these questions automatically from the data!

---

# The Titanic Dataset

We'll predict survival using **8 features**:

- **pclass**: Passenger class (1st, 2nd, 3rd)
- **sex**: Male or female
- **age**: Age in years
- **sibsp**: # of siblings/spouses aboard
- **parch**: # of parents/children aboard
- **fare**: Ticket price ($)
- **embarked**: Boarding port (C, Q, S)
- **survived**: Outcome (1 = survived, 0 = died) ← TARGET

**Dataset size**: 891 rows

---

# Libraries We'll Use

| Library | Purpose |
|---------|---------|
| **pandas** | Work with tables of data |
| **scikit-learn** | Machine learning tools |
| **matplotlib** | Create visualizations |

Think of these as toolboxes with pre-built functions!

---

# The Complete ML Pipeline

```
1. LOAD      → Read CSV into DataFrame
              ↓
2. EXPLORE   → .head(), .info(), .describe()
              ↓
3. CLEAN     → Drop columns, handle missing values
              ↓
4. ENCODE    → Convert categories to numbers
              ↓
5. SPLIT     → train_test_split (80/20)
              ↓
6. TRAIN     → DecisionTreeClassifier.fit()
              ↓
7. PREDICT   → model.predict()
              ↓
8. EVALUATE  → accuracy_score, classification_report
              ↓
9. VISUALIZE → plot_tree, feature_importance
```

---

# Lesson Structure

**ai03a**: Loading, Exploring, and Cleaning Data
- Load the CSV file
- Inspect with .head(), .info(), .describe()
- Select columns to use
- Drop missing values
- Encode categorical data

**ai03b**: Building, Evaluating, and Visualizing Models
- Train/test split
- Build DecisionTreeClassifier
- Make predictions
- Check accuracy and classification report
- Visualize the tree and feature importance

---

# ODE Competencies Covered

- **2.14.1**: Select and use appropriate machine learning techniques
- **1.1.7**: Apply mathematical reasoning to solve problems
- **5.1.2**: Use data structures and algorithms effectively

---

# Let's Get Started!

Open **ai03_Walkthrough.ipynb** to begin.

**Remember**: Take your time understanding each step. This is your foundation for all future ML work!

Questions? Ask your instructor anytime.
