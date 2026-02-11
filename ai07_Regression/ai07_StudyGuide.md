# Study Guide: Lesson 07 — Linear Regression

## Vocabulary

1. **Linear Regression** — A machine learning algorithm that draws the "best fit" line through data points and uses that line to make predictions.

2. **Pearson r (Correlation)** — A number from -1.0 to +1.0 that measures how strongly two variables are related. Closer to ±1 = stronger relationship.

3. **R-Squared (R²)** — The square of Pearson r; represents the percentage of variation in the output that the input explains. Higher R² = better fit.

4. **Coefficient** — A number that the model learns, representing how much each feature affects the prediction. Positive = pushes prediction up, negative = pushes down.

5. **Intercept** — The starting value in the regression formula y = mx + b (the "b" part). It's the prediction when all features equal zero.

6. **Feature** — An input variable used to make a prediction (e.g., engine size, temperature, humidity).

7. **Target** — The output variable we're trying to predict (e.g., MPG, price, temperature).

8. **Train/Test Split** — Dividing the dataset into two parts: 80% for training the model, 20% for testing its accuracy on data it hasn't seen.

9. **MAE (Mean Absolute Error)** — The average number of units the model's predictions are off by. Lower is better.

10. **Slope (m)** — In y = mx + b, the "m" is the slope; it shows how steeply the line goes up or down.

11. **Scatter Plot** — A graph with points plotted as (x, y) pairs; used to visualize the relationship between two variables.

12. **Overfitting** — When a model memorizes the training data perfectly but fails on new data because it learned the noise, not the true pattern.

13. **Residual** — The difference between what the model predicted and what actually happened. Small residuals = good fit.

14. **Positive Correlation** — When two variables move in the same direction (both go up, or both go down together).

15. **Negative Correlation** — When two variables move in opposite directions (one goes up, the other goes down).

16. **Heatmap** — A color-coded table showing the correlation (Pearson r) between every pair of variables.

17. **One-Hot Encoding** — Converting categorical data (like "FWD", "RWD") into separate 0/1 columns so the model can work with it.

18. **API** — Application Programming Interface; a way for programs to request data from online sources.

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

## Data Dictionary: EPA Cars 2026

The `MY26 FE Guide for DOE.xlsx` file contains real EPA fuel economy data for 2026 model year vehicles.

| Column | Type | Description | Example |
|--------|------|-------------|---------|
| **engine_liters** | number | Engine displacement in liters | 2.0 |
| **cylinders** | integer | Number of engine cylinders | 4 |
| **drive** | string | Drive type (F=FWD, R=RWD, A=AWD, 4=4WD) | "F" |
| **mpg** | number | Combined fuel economy in miles per gallon | 28.5 |

---

## Quick Reference: Regression in Python

### 1. Load and Clean Data
```python
import pandas as pd

# Load data
data = pd.read_csv('file.csv')

# Remove rows with missing values
data = data.dropna()

# Check what you have
print(data.head())
print(data.describe())
```

### 2. Explore Correlations
```python
import matplotlib.pyplot as plt
import seaborn as sns

# Calculate Pearson r for all numeric columns
correlation = data[['feature1', 'feature2', 'target']].corr()

# Visualize as a heatmap
plt.figure(figsize=(8, 6))
sns.heatmap(correlation, annot=True, cmap='coolwarm', center=0, fmt='.2f')
plt.show()

# Check one specific correlation
r_value = data['feature1'].corr(data['feature2'])
r_squared = r_value ** 2
```

### 3. Build a Regression Model
```python
from sklearn.model_selection import train_test_split
from sklearn.linear_model import LinearRegression
from sklearn.metrics import r2_score, mean_absolute_error

# Define features (X) and target (y)
X = data[['feature1', 'feature2']]
y = data['target']

# Train/test split: 80% train, 20% test
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# Create and train the model
model = LinearRegression()
model.fit(X_train, y_train)

# Check accuracy on test data
predictions = model.predict(X_test)
r2 = r2_score(y_test, predictions)
mae = mean_absolute_error(y_test, predictions)

print(f"R²: {r2:.3f}")
print(f"MAE: {mae:.1f}")
```

### 4. Interpret Coefficients
```python
# See what the model learned
coefficients = pd.DataFrame({
    'Feature': X.columns,
    'Coefficient': model.coef_
})
print(coefficients)
print(f"Intercept: {model.intercept_:.2f}")

# The formula is:
# y = (coef[0] * feature1) + (coef[1] * feature2) + ... + intercept
```

### 5. Make Predictions
```python
# Create a row of new data
new_input = pd.DataFrame({
    'feature1': [value1],
    'feature2': [value2]
})

# Get the prediction
prediction = model.predict(new_input)[0]
print(f"Predicted value: {prediction:.1f}")
```

---

## ODE Competencies Covered

**2.14.1** — Demonstrate proficiency with data visualization and statistical analysis tools to interpret and communicate findings.
- We use correlation heatmaps, scatter plots, and metrics like R² to analyze relationships.

**5.1.2** — Apply machine learning algorithms to solve real-world problems.
- We train linear regression models on actual weather and car data.

**1.1.7** — Evaluate AI solutions for effectiveness, bias, and ethical implications.
- We discuss why the weather model is "cheating" and compare realistic vs simplified predictions.

---

## Common Mistakes to Avoid

1. **Using R² from the training data** — Always check R² on test data (data the model hasn't seen). Training R² is always higher and can hide overfitting.

2. **Assuming correlation = causation** — Just because two things are correlated doesn't mean one causes the other. Example: ice cream sales and drowning deaths are correlated (both peak in summer), but ice cream doesn't cause drowning.

3. **Ignoring missing values** — Always check for NaN/null values and handle them (usually with `.dropna()` or `.fillna()`).

4. **Forgetting to convert categorical data** — If you have text columns like "FWD", "RWD", use one-hot encoding before building the model.

5. **Trusting low R² too quickly** — R² below 0.50 isn't necessarily bad; it just means the relationship is weaker. Many real-world problems have low R².

---

## Excel Warmup Review

In ai06, you calculated Pearson r for three datasets:

| Dataset | r value | Interpretation |
|---------|---------|-----------------|
| Height vs Shoe Size | ~0.997 | Nearly perfect positive |
| Study Hours vs Test Score | ~0.972 | Very strong positive |
| Ice Cream Sales vs Temperature | ~0.992 | Very strong positive |

**Key insight:** All three had strong positive correlations, but the study hours dataset had more "scatter" — some students who studied the same amount got different scores. That's real data.

---

## When to Use Linear Regression

**Good fit:**
- You have 50+ data points
- Pearson r > 0.70 or < -0.70
- Relationship is roughly straight-line
- You need an interpretable model (you can explain the formula to others)

**Bad fit:**
- Pearson r between -0.4 and +0.4 (weak relationship)
- Relationship is curved
- You have categorical outcomes (yes/no, A/B/C)
- You need maximum accuracy (then try neural networks)

---
