# ai03 Study Guide: Machine Learning with Decision Trees

## Key Vocabulary Terms

### Machine Learning Concepts

1. **Machine Learning**: Computer programs that learn patterns from data without being explicitly programmed
2. **Supervised Learning**: Learning where we have both input data (features) and correct answers (target)
3. **Classification**: Predicting which category something belongs to (e.g., survived or not)
4. **Decision Tree**: A flowchart-like model that makes predictions by asking yes/no questions
5. **Prediction**: Using a trained model to estimate outcomes for new, unseen data

### Data Concepts

6. **DataFrame**: A table of data (like an Excel spreadsheet) in pandas
7. **Feature**: A column in the data used to make predictions (input variable)
8. **Target**: The column we're trying to predict (output variable; e.g., `survived`)
9. **Row**: A single record in a DataFrame (e.g., one passenger)
10. **Column**: A single attribute in a DataFrame (e.g., `age`, `sex`)
11. **Missing Values (NaN)**: Empty cells in data that haven't been filled in
12. **Categorical Data**: Text or categories (e.g., "male", "female") vs. numbers

### Data Preparation

13. **Data Cleaning**: Removing errors, handling missing values, selecting relevant columns
14. **One-Hot Encoding**: Converting categorical text into numeric columns (1 or 0)
15. **get_dummies()**: A pandas function that automatically does one-hot encoding
16. **Dropping Data**: Removing rows or columns we don't need
17. **Encoding**: Converting non-numeric data into numeric form

### Model Training & Evaluation

18. **Training Data**: The data we use to teach the model (typically 80%)
19. **Test Data**: The data we use to evaluate the model (typically 20%)
20. **Train/Test Split**: Dividing data into training and test sets
21. **Accuracy**: Percentage of correct predictions (right answers / total predictions)
22. **Classification Report**: Detailed breakdown of model performance (precision, recall, f1-score)
23. **Precision**: Of positive predictions, how many were actually correct
24. **Recall**: Of actual positives, how many did we find
25. **F1-Score**: Balance between precision and recall

### Decision Tree Specific

26. **Node**: A decision point in the tree (asks a question)
27. **Leaf**: An end point where the tree makes a prediction
28. **Depth**: How many decisions the tree makes before reaching a prediction
29. **Max Depth**: Limiting parameter to prevent overfitting
30. **Feature Importance**: How much each feature helps the model make decisions
31. **Hyperparameter**: A setting we control when building a model (like max_depth)

---

## Titanic Dataset Dictionary

### Original Dataset (891 rows, 15 columns)

| Column | Data Type | Example | Meaning |
|--------|-----------|---------|---------|
| **pclass** | int | 1, 2, 3 | Passenger class (1st=upper, 2nd=middle, 3rd=lower) |
| **survived** | int | 0, 1 | Did passenger survive? (1=yes, 0=no) |
| **sex** | str | male, female | Gender of passenger |
| **age** | float | 22.0, 35.5 | Age in years (many missing values) |
| **sibsp** | int | 0, 1, 2 | Number of siblings or spouses aboard |
| **parch** | int | 0, 1, 2 | Number of parents or children aboard |
| **fare** | float | 7.25, 512.33 | Ticket price in pounds |
| **embarked** | str | C, Q, S | Port where passenger boarded |
| **cabin** | str | A7, B5 | Cabin number (mostly missing) |
| **boat** | str | 1, 2, 3 | Lifeboat number (missing if didn't survive) |
| **name** | str | "Smith, John" | Passenger name |
| **ticket** | str | A/5 21171 | Ticket number |
| **body** | int | 1, 2 | Body ID if recovered (missing if survived) |
| **home.dest** | str | New York, NY | Home destination |

### Features We Use in ai03

After cleaning, we keep these 7 features:

| Feature | Type | Values | Notes |
|---------|------|--------|-------|
| pclass | numeric | 1, 2, 3 | Passenger class |
| sex | categorical → numeric | 0, 1 | Encoded as 0=male, 1=female |
| age | numeric | 0.4–80 years | Removed rows with missing values |
| sibsp | numeric | 0–8 | Siblings/spouses count |
| parch | numeric | 0–9 | Parents/children count |
| fare | numeric | 0–512 pounds | Ticket price |
| embarked | categorical → numeric | 0, 1, 2 | Encoded: C, Q, S → multiple columns |

**Target**: `survived` (0 or 1)

---

## Code Patterns & Functions Reference

### Loading Data
```python
import pandas as pd
titanicData = pd.read_csv('Titanic Dataset.csv')
```

### Exploring Data
```python
titanicData.head()          # First 5 rows
titanicData.tail()          # Last 5 rows
titanicData.info()          # Column types, missing values
titanicData.describe()      # Statistics (mean, std, min, max)
titanicData.columns         # All column names
titanicData.shape           # (rows, columns)
titanicData.isnull().sum()  # Missing value count per column
```

### Cleaning Data
```python
# Select specific columns
titanicData = titanicData[['pclass', 'survived', 'sex', 'age', 'sibsp', 'parch', 'fare', 'embarked']]

# Drop rows with any missing values
titanicData = titanicData.dropna()

# One-hot encode categorical columns
titanicData = pd.get_dummies(titanicData, columns=['sex', 'embarked'], drop_first=True)
```

### Separating Features and Target
```python
X = titanicData.drop('survived', axis=1)  # Features (everything except target)
y = titanicData['survived']               # Target (what we predict)
```

### Train/Test Split
```python
from sklearn.model_selection import train_test_split
xTrain, xTest, yTrain, yTest = train_test_split(X, y, test_size=0.2, random_state=42)
```

### Building and Training
```python
from sklearn.tree import DecisionTreeClassifier
model = DecisionTreeClassifier(max_depth=4, random_state=42)
model.fit(xTrain, yTrain)
```

### Making Predictions
```python
predictions = model.predict(xTest)
```

### Evaluation
```python
from sklearn.metrics import accuracy_score, classification_report
accuracy = accuracy_score(yTest, predictions)
print(classification_report(yTest, predictions))
```

### Visualization
```python
from sklearn.tree import plot_tree
import matplotlib.pyplot as plt

plot_tree(model, feature_names=X.columns, class_names=['Did Not Survive', 'Survived'])
plt.show()

# Feature importance
importances = model.feature_importances_
for feature, importance in zip(X.columns, importances):
    print(f"{feature}: {importance:.4f}")
```

---

## Common Mistakes & How to Avoid Them

| Mistake | Problem | Solution |
|---------|---------|----------|
| Forgetting to drop target from X | Model learns to ignore features | Use `X = titanicData.drop('survived', axis=1)` |
| Including rows with missing values | Model errors or wrong predictions | Use `dropna()` before training |
| Not encoding categorical data | sklearn can't read text data | Use `pd.get_dummies()` |
| Wrong test_size (e.g., 0.5) | Model performance looks artificially good | Use 0.2 (20% test, 80% train) |
| max_depth too high | Model overfits (memorizes training data) | Start with 3-5, test different values |
| max_depth too low | Model underfits (too simple) | Start with 3-5, test different values |
| Using all rows for training | No way to evaluate model | Always split into train/test |

---

## Quick Reference: One-Hot Encoding Example

**Before** (categorical):
```
sex       embarked
male      C
female    S
male      C
```

**After** (encoded with get_dummies):
```
sex_male  sex_female  embarked_C  embarked_Q  embarked_S
0         1           1           0           0
1         0           0           0           1
0         1           1           0           0
```

**Key point**: Categorical data becomes multiple binary (0/1) columns!

---

## Hyperparameter Tuning Notes

### max_depth Parameter

| max_depth | Characteristics | Use When |
|-----------|-----------------|----------|
| 1–2 | Very simple, fast, underfits | Too basic to use |
| 3–5 | Good balance, accurate, interpretable | **RECOMMENDED** |
| 6–10 | More complex, may overfit | Testing/experimenting |
| 15+ | Very deep, overfits heavily | Avoid for small datasets |

Test different values and compare accuracy scores!

### random_state Parameter
- `random_state=42`: Ensures reproducible results (same random split every time)
- Good for teaching and debugging
- Always use it in learning code!

---

## Study Questions

1. What's the difference between features (X) and target (y)?
2. Why do we split data into training and test sets?
3. What does one-hot encoding do to categorical columns?
4. Why must categorical data be encoded before training a decision tree?
5. What does accuracy_score tell us?
6. What happens if max_depth is too high?
7. What are missing values (NaN) and why do we remove them?
8. How does a decision tree make predictions?
9. What does feature importance tell us?
10. Why is data cleaning often the longest part of machine learning?

---

## Competency Alignment

**ODE 2.14.1**: Select and use appropriate machine learning techniques
- ✓ Choosing decision trees for classification
- ✓ Tuning max_depth hyperparameter
- ✓ Evaluating model performance

**ODE 1.1.7**: Apply mathematical reasoning to solve problems
- ✓ Understanding accuracy calculations
- ✓ Interpreting statistics from .describe()
- ✓ Analyzing feature importance

**ODE 5.1.2**: Use data structures and algorithms effectively
- ✓ Working with DataFrames
- ✓ Using sklearn pipeline
- ✓ Implementing train/test split algorithm

---

## Additional Resources

- **sklearn Documentation**: https://scikit-learn.org
- **Pandas Documentation**: https://pandas.pydata.org
- **Decision Trees Explained**: https://en.wikipedia.org/wiki/Decision_tree
- **Titanic Dataset**: https://www.kaggle.com/datasets/titanic

---

**Remember**: The best way to learn ML is by doing. Experiment with different max_depth values, try different features, and always check your results with test data!
