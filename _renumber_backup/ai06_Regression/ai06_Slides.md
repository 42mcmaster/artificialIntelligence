---
marp: true
theme: default
paginate: true
---

# Lesson 06: Linear Regression
## Artificial Intelligence
### Medina County Career Center

---

<!-- _header: "Sub-Lesson 06a — Correlation & Pearson r" -->

# Measuring Relationships: Pearson r

**Pearson r** = how strongly two things move together

| r value | Meaning | Example |
|---------|---------|---------|
| **+1.0** | Perfect positive | height and shoe size |
| **+0.7** | Strong positive | study hours and test score |
| **0.0** | No relationship | birthday month and GPA |
| **-0.7** | Strong negative | car engine size and MPG |
| **-1.0** | Perfect negative | altitude and air pressure |

**The closer to ±1.0, the stronger the relationship.**

---

<!-- _header: "Sub-Lesson 06a — Correlation & Pearson r" -->

# From r to R-Squared (R²)

R² tells us: **what percentage of the outcome is explained by our predictor?**

**Formula:** R² = r × r

| Pearson r | R² | Interpretation |
|-----------|-----|----------------|
| 0.99 | 0.98 (98%) | Explains almost everything |
| 0.90 | 0.81 (81%) | Explains most of it |
| 0.70 | 0.49 (49%) | Explains about half |
| 0.50 | 0.25 (25%) | Explains a quarter |
| 0.30 | 0.09 (9%) | Barely explains anything |

**Higher R² = the relationship fits better = better predictions**

---

<!-- _header: "Sub-Lesson 06b — Building Regression Models in Python" -->

# Linear Regression: The Algebra

From algebra: **y = mx + b**

| Part | What It Means | Example |
|------|--------------|---------|
| **m** | slope (steepness) | 1.5 |
| **b** | intercept (y-axis crossing) | 10 |
| **x** | the input (what we know) | temperature |
| **y** | the output (what we predict) | ice cream sales |

**Machine learning:** Let the computer find the **best m and b** to fit our data.

---

<!-- _header: "Sub-Lesson 06b — Building Regression Models in Python" -->

# The Regression Pipeline

```
  Get Data  -->  Clean It  -->  Explore (Correlation)
                                       |
                                       v
  Use It  <--  Test It  <--  Build the Model
```

| Step | What Happens |
|------|-------------|
| **Get Data** | Load from CSV or API |
| **Clean** | Remove missing values |
| **Explore** | Calculate r, make scatter plots |
| **Build** | Train the regression model on 80% of data |
| **Test** | Check R² on 20% the model has never seen |
| **Use** | Make predictions on new inputs |

---

<!-- _header: "Sub-Lesson 06b — Building Regression Models in Python" -->

# Coefficients: What the Model Learns

Linear regression gives us a **formula**:

```
Prediction = (coef₁ × feature₁) + (coef₂ × feature₂) + ... + intercept
```

**Example from weather model:**
```
Predicted Temp = (1.03 × morning_low) + (-0.26 × humidity) + intercept
```

| Coefficient | Plain English |
|-------------|--------------|
| **+1.03** | Each 1° warmer morning = ~1° warmer high |
| **-0.26** | Each 1% more humidity = ~0.26° cooler high |

**Positive = pushes prediction up**
**Negative = pushes prediction down**

---

<!-- _header: "Sub-Lesson 06b — Building Regression Models in Python" -->

# When Lines Work vs Don't Work

**Lines work great when:**
- r is above 0.70 or below -0.70 (strong relationship)
- R² is above 0.50 (explains at least half)

**Lines don't work when:**
- Relationship is curved (income vs happiness levels off)
- R² below 0.30 (explains less than 30%)
- Too many unmeasured factors

**Real-world examples:**
- **Works:** Predicting house price from square footage (R² ~0.85)
- **Doesn't work:** Predicting test score from birthday (r ≈ 0.0)

When lines fail, we switch to random forests, neural networks, clustering, or other tools.

---

<!-- _header: "Sub-Lesson 06b — Building Regression Models in Python" -->

# Key Takeaways

| Concept | What It Means |
|---------|--------------|
| **Pearson r** | Correlation: how strong the relationship (-1 to +1) |
| **R²** | r squared: % of variation explained by the model |
| **Coefficient** | How much each feature affects the prediction |
| **Intercept** | Starting point (prediction when all features = 0) |
| **Train/Test Split** | Train on 80%, test on 20% model hasn't seen |
| **MAE** | Mean Absolute Error: average prediction error |

**The Big Idea:** Draw a line through data, use it to predict, test on new data.

---
