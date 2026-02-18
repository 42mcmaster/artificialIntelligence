# Lesson 06: Exploring the Data in Excel
## Before We Code — Let's See What the Data Tells Us

**AI/ML Course | Medina County Career Center**

Before we build a regression model in Python, let's explore the same dataset in Excel first. This helps us understand the data and spot patterns *before* we ask the computer to find them for us.

**Data source:** [U.S. Bureau of Labor Statistics — Employment Projections](https://data.bls.gov/projections/occupationProj)

---

## Getting Started

1. Open `BLS_Occupation_Wages.csv` in Excel
2. The data should fill columns **A through H**, with 826 rows of occupations plus a header row
3. Take a quick look — each row is a real U.S. occupation with its education requirements, experience, training, and median salary

> **Reminder:** The `Education_Level` column uses a 1–8 scale:
> 1 = No credential, 2 = High school, 3 = Some college, 4 = Postsecondary award, 5 = Associate's, 6 = Bachelor's, 7 = Master's, 8 = Doctoral

---

## Part 1: Formulas (Follow Along)

For each formula below, pick an empty cell to the right of your data (columns **J–K** work well). Type the formula, then record your answer.

### 1. AVERAGE — What's the average salary across all occupations?

```
=AVERAGE(H2:H827)
```

**My answer:** $__________

---

### 2. MAX and MIN — What's the highest and lowest salary?

```
=MAX(H2:H827)
```
```
=MIN(H2:H827)
```

**Highest:** $__________
**Lowest:** $__________

> **Bonus:** Can you find which occupations those are? Try scrolling, or use **Ctrl+F** to search for the dollar amount.

---

### 3. COUNTIF — How many occupations require a Bachelor's degree?

Education Level 6 = Bachelor's degree:

```
=COUNTIF(B2:B827, 6)
```

**My answer:** __________ occupations

---

### 4. AVERAGEIF — What's the average salary for Bachelor's degree jobs?

```
=AVERAGEIF(B2:B827, 6, H2:H827)
```

This says: "Look at column B. For every row where Education_Level = 6, average the values in column H."

**My answer:** $__________

---

### 5. Build a Wage Table — Average salary at EVERY education level

Now do the same thing for each education level. Set up a small table:

| Cell | Label | Formula |
|------|-------|---------|
| J2 | `Education Level` | *(just type the header)* |
| K2 | `Avg Salary` | *(just type the header)* |
| J3 | `1 - No credential` | |
| K3 | | `=AVERAGEIF(B2:B827, 1, H2:H827)` |
| J4 | `2 - High school` | |
| K4 | | `=AVERAGEIF(B2:B827, 2, H2:H827)` |
| J5 | `3 - Some college` | |
| K5 | | `=AVERAGEIF(B2:B827, 3, H2:H827)` |
| J6 | `4 - Postsecondary award` | |
| K6 | | `=AVERAGEIF(B2:B827, 4, H2:H827)` |
| J7 | `5 - Associate's` | |
| K7 | | `=AVERAGEIF(B2:B827, 5, H2:H827)` |
| J8 | `6 - Bachelor's` | |
| K8 | | `=AVERAGEIF(B2:B827, 6, H2:H827)` |
| J9 | `7 - Master's` | |
| K9 | | `=AVERAGEIF(B2:B827, 7, H2:H827)` |
| J10 | `8 - Doctoral` | |
| K10 | | `=AVERAGEIF(B2:B827, 8, H2:H827)` |

**What pattern do you see?** _______________________________________________

---

### 6. COUNTIF for each level — Add a count column

In column **L**, add a `Count` header and use COUNTIF to see how many occupations are at each level:

```
=COUNTIF(B2:B827, 1)
```

*(Change the 1 to 2, 3, 4, etc. for each row)*

**Which education level has the MOST occupations?** __________
**Which has the FEWEST?** __________

---

### 7. AVERAGEIFS — Average salary with TWO conditions

AVERAGEIFS lets you filter on multiple columns at once. What's the average salary for jobs that require a **Bachelor's degree AND 5+ years of experience**?

```
=AVERAGEIFS(H2:H827, B2:B827, 6, C2:C827, 3)
```

This says: "Average column H, but only where column B = 6 (Bachelor's) AND column C = 3 (5+ years experience)."

**My answer:** $__________

Now try: **High school diploma + no experience required:**

```
=AVERAGEIFS(H2:H827, B2:B827, 2, C2:C827, 1)
```

**My answer:** $__________

**What's the difference?** $__________

---

### 8. MEDIAN — Is the average misleading?

The average can be pulled up by a few very high salaries. Let's check the median:

```
=MEDIAN(H2:H827)
```

**Median salary:** $__________
**Average salary (from #1):** $__________
**Which is higher?** __________

> **Think about it:** Why would the average be higher than the median? What does that tell you about the shape of the salary data?

---

## Part 2: Charts

### Chart 1: Average Salary by Education Level (Bar Chart)

1. Select your wage table from step 5 (J2:K10)
2. **Insert → Bar Chart** (or Column Chart)
3. Give it a title: **"Average Salary by Education Level"**
4. Make sure the education levels are readable on the axis

**What story does this chart tell?** _______________________________________________

---

### Chart 2: Education Level vs. Wage (Scatter Plot)

This one uses the raw data to show every individual occupation:

1. Select **column B** (Education_Level) and **column H** (Median_Annual_Wage)
   - Click the **B** column header, then hold **Ctrl** and click the **H** column header
2. **Insert → Scatter Plot** (the one with just dots, no lines)
3. Title it: **"Does More Education = Higher Pay?"**

**What do you notice?** _______________________________________________
**Is there a clear upward trend, or is it messy?** _______________________________________________

> **Key insight:** This scatter plot is basically what the Python model will try to draw a line through. The "messiness" you see is why the model won't be perfect — education level alone doesn't tell the whole story.

---

## Wrap-Up

Before moving on to the Python notebook, think about what you've learned:

1. **Does education level affect salary?** What did the AVERAGEIF table show you?
2. **Is the relationship perfect?** What did the scatter plot show you?
3. **What else matters?** Experience made a big difference in the AVERAGEIFS formula — what other factors might explain why two Bachelor's-level jobs pay very differently?

These are the same questions the regression model will try to answer — but with math instead of formulas and charts.

**Next up:** Open `ai06_Task.ipynb` and build the model!

---
