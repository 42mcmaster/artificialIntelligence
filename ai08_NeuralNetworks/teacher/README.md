# Lesson 08: Neural Networks
## Applications of Artificial Intelligence - Medina County Career Center

**Teacher:** Ryan McMaster, CTE Instructor
**Course:** Applications of Artificial Intelligence (ODE 145130)
**Duration:** 4 days (1-2 hours per day)
**Prerequisites:** ai01-ai07 (Linear Regression, Decision Trees, Random Forest, etc.)

---

## Overview

This lesson teaches students how neural networks work, how to build them using scikit-learn, and when to use them compared to simpler models. A key insight: **simpler models often outperform complex ones on simple problems**.

### Learning Objectives

By the end of this lesson, students will:
- Explain what an artificial neuron is and how it differs from biological neurons
- Understand weights, bias, activation functions, and network layers
- Explain forward pass and backpropagation conceptually
- Build a neural network using scikit-learn's `MLPRegressor`
- Compare neural networks to Linear Regression and Random Forest
- Identify when neural networks are the best choice vs simpler alternatives
- Understand why data scaling is critical for neural networks

### ODE Competencies Covered

- **2.14.1** Distinguish between machine learning, neural networks, and other computational approaches
- **2.14.5** Apply machine learning techniques to solve real-world problems and interpret results
- **5.1.1** Use Python to perform data analysis including preprocessing, model building, and evaluation
- **5.1.2** Implement scikit-learn algorithms for supervised learning tasks

---

## Files in This Folder

### Instructor Materials

| File | Purpose | Format |
|------|---------|--------|
| `ai08_Slides.md` | 10-slide presentation covering neural network fundamentals | MARP markdown |
| `ai08_StudyGuide.md` | 20 vocabulary terms, quick reference guide, comparison chart | Markdown |
| `ai08_Walkthrough_Solutions.ipynb` | Complete walkthrough with all code filled in and instructor notes | Jupyter notebook |
| `ai08a_Task_Solutions.ipynb` | Solutions to TensorFlow Playground experiments | Jupyter notebook |
| `ai08b_Task_Solutions.ipynb` | Solutions to architecture exploration task | Jupyter notebook |
| `ai08_DIYTask_Solutions.ipynb` | Solutions to model comparison challenge | Jupyter notebook |

### Student Materials

| File | Purpose | Format |
|------|---------|--------|
| `ai08_Walkthrough.ipynb` | Step-by-step walkthrough with blanks to fill | Jupyter notebook |
| `ai08a_Task.ipynb` | Guided experiments on TensorFlow Playground | Jupyter notebook |
| `ai08b_Task.ipynb` | Build and compare architectures on weather data | Jupyter notebook |
| `ai08_DIYTask.ipynb` | Model comparison challenge (LR vs RF vs NN) | Jupyter notebook |

### Assessment Materials

| File | Purpose | Format |
|------|---------|--------|
| `ai08_Gimkit.csv` | 25 review questions for Gimkit game | CSV |
| `ai08_GoogleQuiz.csv` | 30 assessment questions for Google Forms | CSV |

---

## Lesson Flow (4 Days)

### Day 1: Introduction (45-60 minutes)

**Materials:** `ai08_Slides.md`, `ai08_Walkthrough.ipynb`

1. **Presentation (20 min):** Use slides to introduce:
   - What neurons are (biological vs artificial analogy)
   - How weights and bias work
   - Network architecture (layers)
   - Training process (forward pass → loss → backpropagation)

2. **Walkthrough (40 min):** Code along with students:
   - Load Medina weather data (same as Lesson 07)
   - Explain why neural networks need scaled data
   - Build a `MLPRegressor` with 2 hidden layers (10, 5)
   - Train and evaluate on test set
   - **Compare to Linear Regression from Lesson 07** ← KEY LESSON
   - Show results are similar! Linear Regression often wins!

**Learning outcome:** Students understand how neural networks work and know that complexity isn't always better.

---

### Day 2: Sub-Lesson 08a — Depth vs Width Exploration (30-40 minutes)

**Materials:** `ai08a_Task.ipynb`

**Activity:** TensorFlow Playground Experiments

1. Have students visit [playground.tensorflow.org](https://playground.tensorflow.org)
2. Run 6 experiments:
   - Circle dataset with 2 neurons → struggles
   - Circle dataset with 8 neurons → works better
   - 2 layers (8 neurons each) → even better
   - Spiral with 1 layer → struggles
   - Spiral with 3 layers (16 neurons each) → works!
   - Student's own architecture experiment

3. Record observations in notebook
4. Discuss: Why do spirals need deep networks?

**Learning outcome:** Students empirically discover that depth and width matter, but depth is crucial for non-linear problems.

---

### Day 3: Sub-Lesson 08b — Architecture Exploration (30-40 minutes)

**Materials:** `ai08b_Task.ipynb`

**Activity:** Test 5 Different Architectures on Weather Data

Students build and compare:
1. Single layer with 5 neurons (underfitting baseline)
2. Two layers (10, 5) (good balance)
3. Single layer with 20 neurons (wide but shallow)
4. Three layers (15, 10, 5) (deep)
5. Student's choice

Results: All architectures perform similarly! R² scores differ by ~0.01-0.02.

**Key insight:** For this simple problem, complexity doesn't help. Simpler is better!

**Learning outcome:** Students learn that model complexity isn't always worth it.

---

### Day 4: DIY Task — Model Comparison Challenge (30-40 minutes)

**Materials:** `ai08_DIYTask.ipynb`

**Activity:** Build Three Models on Same Data

Students build and compare:
1. **Linear Regression** (from Lesson 07)
2. **Random Forest** (from earlier lessons)
3. **Neural Network** (this lesson)

On the Medina weather data (predicting max temperature).

**Expected results:**
- Linear Regression: R² ≈ 0.83, MAE ≈ 2.3°F
- Random Forest: R² ≈ 0.81, MAE ≈ 2.6°F
- Neural Network: R² ≈ 0.83, MAE ≈ 2.3°F

**Students write:** Which model would you deploy to production and why?

**Learning outcome:** Model selection depends on the problem. The simplest model that works is often best.

---

## Key Teaching Points

### 1. **Scaling is Not Optional**
Neural networks fail without scaled data. Use `StandardScaler` to transform features to mean=0, std=1.

### 2. **Simpler is Often Better**
Don't use a neural network if Linear Regression works. Compare multiple models on the same problem.

### 3. **Depth Matters for Complex Patterns**
- TensorFlow Playground shows this visually
- Spirals need multiple layers
- Circles need more neurons
- But on simple linear problems, extra depth hurts (overfitting)

### 4. **Model Capacity vs Data**
- More parameters = risk of overfitting on small datasets
- 365 examples is small → use simpler models
- With millions of examples, deep networks shine

### 5. **Forward Pass → Loss → Backpropagation**
The training cycle:
1. Make a prediction (forward pass)
2. Calculate how wrong (loss)
3. Adjust weights to be less wrong (backpropagation)
4. Repeat thousands of times

### 6. **Neural Networks vs Decision Trees**
- Decision Trees: Simple, interpretable, ask yes/no questions
- Neural Networks: Complex, black box, learn weights from data

---

## Code Style Standards Used

All notebooks follow these standards:

**Imports with comments:**
```python
import pandas as pd  # pandas = data tables (like Excel in Python)
from sklearn.preprocessing import StandardScaler  # scale features to mean=0, std=1
```

**camelCase variables:**
```python
weatherData = pd.read_csv('...')
X_train_scaled = scaler.fit_transform(X_train)
nnModel = MLPRegressor(hidden_layer_sizes=(10, 5))
nnPredictions = nnModel.predict(X_test_scaled)
```

**Heavy comments:**
```python
# Create a neural network model
# MLPRegressor = Multi-Layer Perceptron Regressor
nnModel = MLPRegressor(
    hidden_layer_sizes=(10, 5),  # 2 hidden layers: 10 and 5 neurons
    max_iter=1000,               # Train for up to 1000 epochs
    random_state=42              # for reproducibility
)
```

---

## Data Used

**Source:** `medina_weather_2024.csv`

**Columns:**
- `date` - Day of the year
- `temp_max` - Maximum temperature (°F) — TARGET
- `temp_min` - Minimum temperature (°F) — FEATURE
- `precipitation` - Rain/snow (inches)
- `wind_speed` - Wind speed (mph) — FEATURE
- `humidity` - Relative humidity (%) — FEATURE

**Purpose:** Direct comparison with Lesson 07 (Linear Regression) using the same data.

---

## Assessment Ideas

### Formative Assessment (During Lesson)
- Observe student notebook work and code comments
- Ask questions: "Why do we scale data?" "Why did the spiral need depth?"
- Review filled-in observation blanks in tasks

### Summative Assessment
- **Gimkit Quiz** (25 questions, game format)
- **Google Quiz** (30 questions, individual)
- **DIY Task Report** (written recommendation with analysis)

### Rubric for DIY Task Report
- **Model Building (40%):** Did they successfully build all 3 models?
- **Comparison (30%):** Did they compare fairly and identify winner?
- **Justification (30%):** Was the recommendation well-reasoned?

---

## Extension Activities

**If students finish early:**

1. **Try different activation functions:** Change from 'relu' to 'tanh' or 'logistic'
2. **Experiment with learning rates:** Test how different learning_rate values affect training
3. **Build a classifier:** Use MLPClassifier instead of Regressor on iris or wine dataset
4. **Deeper networks:** Build a 4-5 layer network and compare to shallower ones
5. **Visualization:** Use matplotlib to plot predictions vs actual values

---

## Common Student Misconceptions

1. **"Neural networks are always better"**
   → WRONG! This lesson shows Linear Regression often wins.

2. **"More neurons = more accuracy"**
   → WRONG! Can cause overfitting. Simpler architecture often generalizes better.

3. **"Deep learning means lots of layers"**
   → HALF RIGHT! Deep learning uses multiple layers, but not every problem needs them.

4. **"You have to scale data for all models"**
   → WRONG! Only neural networks absolutely require it. Decision trees and Linear Regression are fine without.

---

## Troubleshooting

### Issue: "ConvergenceWarning: Stalled for 10+ iterations"
**Solution:** Model is having trouble converging. Try:
- Increase `max_iter` to 2000 or 5000
- Check that data is properly scaled
- Simplify the architecture (fewer neurons/layers)

### Issue: Linear Regression performs better than Neural Network
**Solution:** This is EXPECTED! The weather data is mostly linear. This is the KEY lesson!

### Issue: Random Forest uses different data format
**Solution:** Random Forest doesn't need scaled data. Use original X_train, not X_train_scaled.

### Issue: Student model overfits (high training R², low test R²)
**Solution:**
- Reduce number of neurons/layers
- Use smaller `max_iter`
- Get more training data

---

## Connection to Broader Curriculum

- **Lesson 07 (Linear Regression):** This lesson shows when to use NN instead of LR
- **Earlier lessons (Decision Trees, Random Forest):** NN is another classification/regression tool
- **Future lessons:** More sophisticated NN architectures (CNN for images, RNN for sequences)

---

## References & Resources

**TensorFlow Playground:** [playground.tensorflow.org](https://playground.tensorflow.org)
**scikit-learn MLPRegressor:** https://scikit-learn.org/stable/modules/neural_networks_supervised.html
**Neural Networks Conceptually:** 3Blue1Brown playlist on deep learning

---

## Questions?

If students ask "When should I use neural networks?"

**Answer:** When you have:
1. **Lots of data** (1000s or millions of examples)
2. **Complex patterns** (images, text, audio, non-linear relationships)
3. **Time and compute** to train for hours
4. **Expert help** to tune hyperparameters

If you have 300 examples and a linear relationship, use Linear Regression!
