# Study Guide: Lesson 06 — Linear Regression

## Vocabulary (Plain English)

1. **Linear Regression** — A machine learning algorithm that draws the "best fit" line through data points and uses that line to make predictions. Think of it like drawing a trend line through a scatter plot — the computer just does it way more precisely than you could by hand.

2. **Feature** — An input variable you give the model so it can make a prediction. These are the things you *know* ahead of time. Example: if you're predicting salary, your features might be education level and years of experience.

3. **Target** — The output variable you're trying to predict. This is the thing you *want to know*. Example: salary, test score, house price.

4. **Pearson r (Correlation)** — A number from -1.0 to +1.0 that measures how strongly two variables are connected.
   - **+1.0** = they move perfectly together (one goes up, the other always goes up)
   - **0.0** = no connection at all
   - **-1.0** = they move perfectly opposite (one goes up, the other always goes down)

   Example: Height and shoe size have a Pearson r around +0.95 — taller people almost always have bigger feet.

5. **R² (R-Squared)** — A score from 0 to 1 that tells you how well your model's features predict the target. Think of it as a percentage grade for your model.

   **Simple way to think about it:** If R² = 0.60, your model's features explain 60% of *why the target values are different from each other*. The other 40% is caused by things your model doesn't know about.

   **Example:** You build a model to predict salary using education level. R² = 0.42. That means education level explains 42% of why some jobs pay more than others. The remaining 58%? That's stuff like the industry, location, demand, and other things your model can't see.

   | R² Score | What it means |
   |----------|--------------|
   | 0.90+ | Excellent — model predicts almost perfectly |
   | 0.70–0.89 | Good — model catches most of the pattern |
   | 0.50–0.69 | Decent — model helps but misses a lot |
   | Below 0.50 | Weak — features don't explain much |

6. **MAE (Mean Absolute Error)** — The average amount the model's predictions are off by. Lower is better.

   Example: If MAE = $18,000 for a salary prediction model, that means on average, the model's guess is about $18,000 too high or too low. Whether that's "good" depends on context — $18K off on a $200K salary is decent; $18K off on a $35K salary is bad.

7. **Coefficient** — A number the model learns that tells you how much each feature affects the prediction.
   - **Positive coefficient** = when this feature goes up, the prediction goes up
   - **Negative coefficient** = when this feature goes up, the prediction goes down

   Example: If the Education_Level coefficient is +11,434, that means each step up on the education scale adds about $11,434 to the predicted salary.

8. **Intercept** — The starting point of the prediction when all features are zero. It's the "b" in y = mx + b from algebra.

9. **Train/Test Split** — Dividing your data into two groups: one to teach the model (training set, usually 80%) and one to quiz the model on data it hasn't seen (test set, usually 20%). This tells you if the model actually learned patterns or just memorized answers.

10. **Overfitting** — When a model memorizes the training data too well and then fails on new data. Like a student who memorizes practice test answers word-for-word but can't handle slightly different questions on the real exam.

11. **Scatter Plot** — A graph where each data point is a dot plotted by its (x, y) values. Used to visually see if two variables have a relationship.

12. **Heatmap** — A color-coded grid that shows the Pearson r correlation between every pair of variables at once. Red/blue colors show strong relationships; white/pale shows weak ones.

13. **Positive Correlation** — When two variables move in the same direction. As one goes up, the other goes up too. Example: education level and salary.

14. **Negative Correlation** — When two variables move in opposite directions. As one goes up, the other goes down. Example: car engine size and fuel economy (bigger engines = fewer MPG).

---

## Data Dictionary: BLS Occupation Wages

The `BLS_Occupation_Wages.csv` file contains data on 826 U.S. occupations from the Bureau of Labor Statistics.

| Column | Type | Description | Example |
|--------|------|-------------|---------|
| **Occupation** | text | Job title | "Registered nurses" |
| **Education_Level** | number | Typical education (1=none, 2=HS, 5=Associate's, 6=Bachelor's, 8=Doctoral) | 6 |
| **Experience_Required** | number | Work experience needed (1=None, 2=<5 years, 3=5+ years) | 2 |
| **Training_Required** | number | On-the-job training (1=None, 6=Internship/residency) | 1 |
| **Workers_Thousands** | number | People employed in thousands | 3,175.8 |
| **Growth_Rate_Pct** | number | Projected growth 2024–2034 | 6.0 |
| **Annual_Openings_Thousands** | number | Yearly job openings in thousands | 193.1 |
| **Median_Annual_Wage** | number | Median salary in dollars (2024) | 86,070 |

---

## Data Dictionary: Medina Weather 2024

The `medina_weather_2024.csv` file contains daily weather measurements for Medina, Ohio throughout 2024.

| Column | Type | Description | Example |
|--------|------|-------------|---------|
| **date** | string | The date in YYYY-MM-DD format | "2024-01-01" |
| **temp_max** | number | Daily high temperature in Fahrenheit | 36.5 |
| **temp_min** | number | Daily low temperature in Fahrenheit | 23.2 |
| **precipitation** | number | Total rainfall/snowfall in inches | 0.0 |
| **wind_speed** | number | Maximum wind speed in mph | 7.4 |
| **humidity** | number | Average relative humidity as a percentage | 38.3 |

---

## Quick Reference: Regression in Python

### 1. Load and Explore Data
```python
import pandas as pd

data = pd.read_csv('file.csv')
data = data.dropna()

print(data.head())
print(data.describe())
```

### 2. Check Correlations
```python
import matplotlib.pyplot as plt
import seaborn as sns

correlation = data[['feature1', 'feature2', 'target']].corr()

plt.figure(figsize=(8, 6))
sns.heatmap(correlation, annot=True, cmap='coolwarm', center=0, fmt='.2f')
plt.show()
```

### 3. Build the Model
```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_absolute_error

X = data[['feature1', 'feature2']]
y = data['target']

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

model = LinearRegression()
model.fit(X_train, y_train)

predictions = model.predict(X_test)
r2 = r2_score(y_test, predictions)
mae = mean_absolute_error(y_test, predictions)

print(f"R²: {r2:.3f}")
print(f"MAE: {mae:.1f}")
```

### 4. Interpret Coefficients
```python
coefficients = pd.DataFrame({
    'Feature': X.columns,
    'Coefficient': model.coef_
})
print(coefficients)
print(f"Intercept: {model.intercept_:.2f}")

# The formula is:
# predicted target = (coef1 × feature1) + (coef2 × feature2) + intercept
```

### 5. Make a Prediction
```python
new_input = pd.DataFrame({
    'feature1': [value1],
    'feature2': [value2]
})

prediction = model.predict(new_input)[0]
print(f"Predicted value: {prediction:.1f}")
```

---

## ODE Competencies Covered

**2.14.1** — Demonstrate proficiency with data visualization and statistical analysis tools to interpret and communicate findings.

**5.1.2** — Apply machine learning algorithms to solve real-world problems.

**1.1.7** — Evaluate AI solutions for effectiveness, bias, and ethical implications.

---

## Common Mistakes to Avoid

1. **Using R² from the training data** — Always check R² on test data. Training R² is always higher and can hide overfitting.

2. **Assuming correlation = causation** — Just because two things are correlated doesn't mean one causes the other. Ice cream sales and drowning deaths are correlated (both peak in summer), but ice cream doesn't cause drowning.

3. **Using features that "cheat"** — If your feature is just another version of your target (like using City_MPG to predict Combined_MPG), the model isn't learning anything useful.

4. **Ignoring missing values** — Always check for NaN/null values and handle them before building a model.

---

## When to Use Linear Regression

**Good fit:**
- You have 50+ data points
- Relationship looks roughly like a straight line
- R² is above 0.50
- You want a model you can explain to someone

**Bad fit:**
- Relationship is curved
- R² below 0.30
- You need maximum accuracy (try neural networks instead)
- Your target is a category (yes/no) rather than a number

---
