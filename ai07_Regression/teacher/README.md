# Lesson 07: Linear Regression
## Applications of Artificial Intelligence (ODE 145130)
### Medina County Career Center — Instructor: Ryan McMaster

---

## Overview

This lesson covers **linear regression**: using a line of best fit through data to predict continuous values. Students will learn about correlation (Pearson r), R-squared, regression coefficients, and building predictive models.

**Duration:** 2-3 class periods
**Prerequisites:** ai01-ai06 (AI intro, ML fundamentals, SQL, APIs, random forest, prompt engineering)

---

## Learning Objectives

By the end of this lesson, students will be able to:
- Calculate Pearson r correlation and interpret its strength/direction
- Understand R² as the percentage of variation explained
- Build linear regression models using sklearn
- Perform train/test split to evaluate models honestly
- Interpret regression coefficients in plain English
- Recognize when linear regression is appropriate vs. when it isn't
- Distinguish between "too easy" predictions (cheating) and realistic ones

**ODE Competencies Addressed:**
- **2.14.1** — Demonstrate proficiency with data visualization and statistical analysis tools
- **5.1.2** — Apply machine learning algorithms to solve real-world problems
- **1.1.7** — Evaluate AI solutions for effectiveness, bias, and ethical implications

---

## File Structure & Usage

### 1. **ai07_Slides.md**
MARP presentation with 10 slides covering:
- Pearson r and what it means
- R² = r squared (percentage explained)
- Linear regression formula (y = mx + b)
- The regression pipeline (collect → clean → explore → build → test → use)
- Coefficients and intercepts
- The "cheating" weather example
- When regression works vs. doesn't work
- Real-world applications

**Use:** Display in class, ask students to follow along. Pause for discussion on the "cheating" concept (same-day temperatures).

---

### 2. **ai07_StudyGuide.md**
Reference document with:
- **Vocabulary** (15-20 terms): correlation, Pearson r, R², coefficient, intercept, feature, target, train/test split, MAE, overfitting, etc.
- **Data dictionaries** for the two datasets used (medina_weather_2024.csv, EPA cars data)
- **Quick reference** for regression code in Python (load, clean, explore, build, evaluate)
- **ODE Competencies** explained
- **Common mistakes** to avoid
- **When to use linear regression**

**Use:** Distribute as a handout. Students reference during tasks. Include on assessments (open-note).

---

### 3. **ai07_Walkthrough.ipynb** (Student Version)
30-cell notebook following the entire workflow on weather data:

**Sub-Lesson 07a — Correlation & Pearson r:**
- Load Medina weather data (365 days, 5 variables)
- Check for missing values
- Calculate Pearson r between all pairs
- Visualize as a heatmap
- Make scatter plot of strongest relationship (temp_min vs temp_max)
- **Discuss the "cheating"**: These are nearly the same measurement, so correlation is suspiciously high

**Sub-Lesson 07b — Building Regression Models:**
- Define features (X) and target (y): predict temp_max from temp_min, humidity, wind_speed
- Train/test split (80/20)
- Train LinearRegression model
- Evaluate with R² ≈ 0.92 and MAE ≈ 2.5°F
- Visualize predictions vs actual
- Extract and interpret coefficients
- Make a prediction on hypothetical day conditions
- **Try This** cell for students to experiment

**Note:** Includes heavy code comments and markdown explanations. Each step asks "why" not just "what."

**Use:** Teacher codes along live. Students follow in their own notebooks (fill-in-the-blank version). Discuss the "cheating" moment deeply — it's the key insight.

---

### 4. **ai07_Walkthrough_Solutions.ipynb**
Complete solution version with:
- All code filled in
- **Instructor Notes** at key points (blue markdown cells)
- Teaching tips: what to emphasize, common student confusions, response strategies
- Extended explanations in notes

**Use:** For teacher prep and answer key. Hide from students.

---

### 5. **ai07a_Task.ipynb** (Student Version)
Hands-on task: Students calculate Pearson r for three real datasets and interpret correlations.

**Tasks:**
- Load three Excel warmup datasets (height/shoe size, study hours/test score, ice cream/temperature)
- Calculate r and R² for each
- Make scatter plots
- Rank by strength of relationship
- Challenge: Pick two variables from weather data and calculate their correlation with temp_max

**Format:** Blanks for code (`# Your code here`) and fill-in interpretation questions.

**Expected Outcomes:**
- Height/Shoe: r ≈ 0.99 (nearly perfect)
- Study/Score: r ≈ 0.97 (very strong, but more scatter)
- Ice Cream/Temp: r ≈ 0.99 (very strong)
- Weather challenge: Weaker correlations (r < 0.5) showing complexity of real data

**Use:** Students work individually or pairs. ~30-40 minutes.

---

### 6. **ai07a_Task_Solutions.ipynb**
Complete solution with:
- All code for each task
- Expected r and R² values
- Instructor notes on what to look for when grading
- Common mistakes students make

---

### 7. **ai07b_Task.ipynb** (Student Version)
Build a regression model predicting car MPG from engine specs.

**Tasks:**
- Load EPA cars data
- Explore: basic stats, drive types
- Correlation heatmap
- **Choose features** (Option A: engine only / Option B: engine + cylinders / Option C: + drive type)
- Train/test split and build model
- Evaluate R² and MAE
- Interpret coefficients
- Make predictions
- **Challenge:** Try different feature combinations

**Format:** Multiple-choice for feature selection (uncomment one), blanks for calculations and interpretation.

**Expected Results (Option B):**
- R² ≈ 0.68 (realistic)
- MAE ≈ 3.5 MPG
- engine_liters coefficient: ≈ -6 (bigger engine → worse MPG)
- cylinders coefficient: ≈ -0.5 (more cylinders → worse MPG)

**Use:** Students work individually. ~45-60 minutes. This is more complex than 07a.

---

### 8. **ai07b_Task_Solutions.ipynb**
Complete solutions with:
- All code for each option
- Sample student interpretation answers
- Comparison of all three feature options and their R² values
- Grading rubric (80 points total)

---

### 9. **ai07_DIYTask.ipynb** (Student Version)
Independent challenge: Build your own regression model.

**Requirements:**
1. Choose a DIFFERENT target than the walkthrough (NOT temp_max)
2. Choose at least 2 features to predict it
3. Build model, calculate R² and MAE
4. Visualize and interpret
5. Compare to walkthrough results
6. Write analysis (6 questions, 5-7 sentences each)

**Available targets:**
- temp_min (daily low)
- humidity (average %)
- wind_speed (max mph)
- precipitation (rainfall)

**Format:** Structured with blanks and prompts, but largely open-ended.

**Use:** Assessment task after all other lessons. ~90-120 minutes. Can be homework.

---

### 10. **ai07_DIYTask_Solutions.ipynb**
Example solution (predicting temp_min from humidity/wind_speed) with:
- Complete code
- Student response example (shows what good analysis looks like)
- Other valid target/feature combinations and their expected R² values
- Comprehensive grading rubric (90 points)
  - 25 pts: Model building
  - 15 pts: Visualization
  - 35 pts: Analysis and interpretation
  - 15 pts: Writing quality
  - Deductions for violating requirements or leaving work incomplete

---

### 11. **ai07_Gimkit.csv**
26 questions for Gimkit live quiz game:
- Multiple choice format
- Covers correlation, R², coefficients, train/test, model evaluation
- Mix of conceptual and practical
- Range of difficulty

**Use:**
- After walkthrough for formative assessment
- Before task notebooks to check understanding
- Post-lesson review/competition game

**Suggested settings:**
- 2 minutes per question
- 10-15 minute session
- Award points for both speed and accuracy

---

### 12. **ai07_GoogleQuiz.csv**
30 questions for Google Forms assessment:
- Same topics as Gimkit but higher rigor
- All multiple choice (A/B/C/D)
- Each question worth 1 point
- Covers all lesson objectives

**Use:**
- Pre-lesson diagnostic (5-10 questions)
- Post-lesson summative assessment (all 30)
- Can be auto-graded in Google Classroom

**Format:** Import CSV into Google Forms (Form → Create from template → Google Sheets → Upload CSV)

---

## Teaching Flow (Recommended)

### Period 1: Correlation & Understanding Relationships
1. **Opener** (5 min): Show slides 1-6 (Pearson r, R², formula)
2. **Walkthrough Part A** (25 min): Live code the weather data correlation section
   - Load → clean → calculate → heatmap → scatter → "cheating" discussion
3. **Task 07a** (20 min): Students calculate correlations for Excel datasets
4. **Debrief** (5 min): Discuss findings. Height/shoe ≈ perfect; study/score ≈ noise exists

### Period 2: Building Models (Longer Period Recommended)
1. **Review** (5 min): Slides 7-8, recap train/test split
2. **Walkthrough Part B** (35 min): Live code the weather model
   - Features/target → split → train → evaluate R²/MAE → coefficients → prediction
3. **Task 07b** (30 min): Students build cars model
4. **Debrief** (5 min): Compare to weather. Discuss why R² is lower but that's OK

### Period 3: Independent Challenge + Assessment
1. **DIY Task** (60-90 min): Students build own model, write analysis
   - ~20 min: Explore and plan
   - ~20 min: Code
   - ~30 min: Analysis and visualization
2. **Optional:** Gimkit quiz game (10 min) for fun review
3. **Homework:** GoogleQuiz for formative feedback

---

## Key Datasets

All data is referenced with relative paths (e.g., ``):

### medina_weather_2024.csv
- **Location:**medina_weather_2024.csv`
- **Records:** 365 (full year 2024)
- **Variables:** date, temp_max, temp_min, humidity, wind_speed, precipitation
- **Use:** Walkthrough example; good for teaching because relationships are clear
- **Caution:** "Cheating" example (temp_min/max too similar)

### MY26 FE Guide for DOE.xlsx
- **Location:**MY26 FE Guide for DOE.xlsx`
- **Sheet:** 'FEguide'
- **Records:** 700+ vehicles
- **Variables:** manufacturer, brand, model, engine_liters, cylinders, drive (F/R/A/4/P), mpg
- **Use:** Realistic regression problem; R² ≈ 0.65-0.75
- **Advantage:** Multiple features to choose from; categorical variable (drive type)

### Excel Warmup Files (for Task 07a)
-ai06_excel_height_shoe.xlsx`
-ai06_excel_study_scores.xlsx`
-ai06_excel_ice_cream_temp.xlsx`

---

## Technical Requirements

**Python Packages:**
```python
pandas          # Data manipulation
numpy           # Math/arrays
matplotlib      # Plotting
seaborn         # Pretty statistical plots
scikit-learn    # Machine learning (LinearRegression, train_test_split, r2_score)
openpyxl        # Reading Excel files
```

**Installation:**
```bash
pip install pandas numpy matplotlib seaborn scikit-learn openpyxl
```

**Environment Notes:**
- Jupyter Notebook or JupyterLab
- Python 3.7+
- All notebooks use relative paths (``), so folder structure must be maintained

---

## Common Student Misconceptions

1. **"Higher R² is always better"**
   - Reality: R² depends on the problem. r=0.7 for predicting real-world messy data is good. r=0.99 for same-day temps is suspicious.

2. **"If R² is low, the model is broken"**
   - Reality: Low R² might mean the problem is hard or you need more features. It's not a failure; it's data telling you something.

3. **"Correlation means causation"**
   - Reality: Ice cream ↔ drowning deaths (both peak in summer) but ice cream doesn't cause drowning. Always think about whether causation makes sense.

4. **"Bigger coefficients mean more important features"**
   - Reality: Coefficients depend on the scale of the feature. A coefficient of 0.001 for a feature ranging 0-10,000 might be bigger than 50 for a 0-1 feature.

5. **"You should always use all available features"**
   - Reality: More features doesn't always help. Can cause overfitting. Use domain knowledge to choose.

---

## Assessment Strategies

### Formative (During Learning)
- **Live coding checks**: Stop walkthrough and ask "what comes next?"
- **Task completion**: Walk around while students work, ask clarifying questions
- **Gimkit game**: Quick formative feedback, fun competition element

### Summative (Grade)
- **Task 07a:** 10-15 points (calculation accuracy + interpretation)
- **Task 07b:** 20-25 points (model building + analysis)
- **DIY Task:** 30-40 points (grading rubric in solutions)
  - Model building: 25 pts
  - Visualization: 15 pts
  - Analysis: 35 pts
  - Writing: 15 pts
- **GoogleQuiz:** 0-30 points (optional formal assessment)

**Total:** 60-100 points possible (scale as needed)

---

## Extensions & Differentiation

### For Advanced Students
- Try polynomial regression (curved lines)
- Add more features to cars model; check for multicollinearity
- Build a model on different data (weather for a different location, different car dataset)
- Calculate confidence intervals on predictions
- Use cross-validation instead of simple train/test
- Compare linear regression to other models (random forest, neural networks)

### For Struggling Students
- Provide partially filled code for Task 07b (copy/paste less code)
- Scaffold DIY task with decision flowchart (which target? why?)
- Pair program during tasks
- Reduce DIY task to 3 questions instead of 6
- Offer pre-built models to interpret (skip the "build" part)

### For ELL Students
- Provide vocabulary card for key terms (in English + primary language if possible)
- Pair with peer mentor during coding
- Accept written analysis in shorter form
- Use visual explanations (heatmaps, scatter plots) over text

---

## Common Pitfalls & Fixes

| Issue | Cause | Fix |
|-------|-------|-----|
| Students can't find datasets | Wrong relative paths | Check folder structure; use `` from ai07_Regression/ |
| R² comes out negative | Using training R² instead of test | Remind: Always evaluate on test set (`y_test`, not `y_train`) |
| Coefficients seem backwards | Feature scale issue | Explain: Coefficients depend on units. Don't compare magnitudes across features. |
| Students don't understand "cheating" | Skip that discussion | MUST stop and explain: same-day temps aren't real prediction |
| DIY tasks have weak analysis | Students rush to get R² number | Require: Write 2-3 sentences explaining WHY the model works/doesn't work |

---

## Connections to Prior & Future Lessons

**Prior lessons (ai01-ai06):**
- Decision trees: used single features for predictions
- Random forest: combined multiple features (we're doing that here too)
- SQL/APIs: loading data (we use both weather API and Excel export)

**Future lessons (ai08+):**
- Classification: same idea but predicting categories (yes/no) instead of continuous numbers
- Neural networks: more complex models but same train/test/evaluate workflow
- Deep learning: high-dimensional regression

---

## References & Resources

**For Teachers:**
- sklearn documentation: https://scikit-learn.org/stable/modules/generated/sklearn.linear_model.LinearRegression.html
- Pearson r explained: https://en.wikipedia.org/wiki/Pearson_correlation_coefficient
- R² interpretation: https://en.wikipedia.org/wiki/Coefficient_of_determination

**For Students (Optional Enrichment):**
- StatQuest with Josh Starmer: "Linear Regression" (YouTube)
- 3Blue1Brown: "Essence of Algebra" (explains y=mx+b intuitively)

---

## File Manifest

```
ai07_Regression/
├── README.md                          # This file
├── ai07_Slides.md                     # MARP presentation (10 slides)
├── ai07_StudyGuide.md                 # Reference guide (vocabulary, data dicts, code snippets)
├── ai07_Walkthrough.ipynb             # Walkthrough (student version, fill-in-the-blank)
├── ai07_Walkthrough_Solutions.ipynb   # Walkthrough (solution + instructor notes)
├── ai07a_Task.ipynb                   # Task 07a (student version, correlations)
├── ai07a_Task_Solutions.ipynb         # Task 07a (solutions + grading notes)
├── ai07b_Task.ipynb                   # Task 07b (student version, cars model)
├── ai07b_Task_Solutions.ipynb         # Task 07b (solutions + grading rubric)
├── ai07_DIYTask.ipynb                 # DIY task (student version, open-ended)
├── ai07_DIYTask_Solutions.ipynb       # DIY task (example solution + grading)
├── ai07_Gimkit.csv                    # 26 questions for Gimkit game
└── ai07_GoogleQuiz.csv                # 30 questions for Google Forms
```

---

## Version History

- **v1.0** (Feb 2025): Initial release
  - Adapted from ai06 draft notebooks (ai06a1, ai06a2)
  - Created slides, study guide, tasks, assessment tools
  - Heavy code comments for CTE students
  - "Cheating" narrative to teach critical thinking

---

## Contact & Support

**Lesson Creator:** [AI Curriculum Team]
**Course Instructor:** Ryan McMaster
**School:** Medina County Career Center
**Subject:** Applications of Artificial Intelligence (ODE 145130)

For questions or updates, contact the curriculum team.

---

**Last Updated:** February 2025
**Status:** Ready for classroom use

