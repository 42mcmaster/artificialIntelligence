---
marp: true
theme: default
paginate: true
---

# Lesson 07: Neural Networks
## Artificial Intelligence
### Medina County Career Center

---

# What Are Neural Networks?

Neural networks are inspired by how brains work. They learn by adjusting millions of small weights based on their mistakes.

```
Input Layer    Hidden Layers      Output Layer
    (3)            (10)  (5)           (1)
     ●              ●●●●●●●●●●        ●
     ●              ●●●●●●●●●●        prediction
     ●              ●●●●●●●●●●
```

**Key difference from Decision Trees:**
- Decision Trees: Ask yes/no questions in order
- Neural Networks: Process all inputs simultaneously with weighted connections

---

# How a Neuron Works

Each artificial neuron mimics a biological neuron:

1. **Receive** inputs (from other neurons)
2. **Multiply** by weights (importance)
3. **Sum** them up
4. **Activate** if sum exceeds threshold
5. **Output** to next layer

```
Inputs    Weights       Sum           Activation    Output
x₁ ─(w₁)─┐
         ├─→[Σ + bias]─→[Activate?]─→ output
x₂ ─(w₂)─┘
```

**During training:** Adjust weights to minimize error

---

# Neural Network Architecture

| Component | Purpose |
|-----------|---------|
| **Input Layer** | Raw data (temp, humidity, wind) |
| **Hidden Layers** | Learn patterns from data |
| **Output Layer** | Final prediction |
| **Weights** | How much each connection matters |
| **Activation Function** | Decide if neuron "fires" |
| **Backpropagation** | Adjust weights using errors |

**Rule of thumb:** More layers and neurons = can learn more complex patterns (but slower & risk overfitting)

---

# Training Process

A neural network trains in cycles:

1. **Forward Pass:** Make a prediction
2. **Calculate Loss:** How wrong were we?
3. **Backpropagation:** Trace error backwards, adjust weights
4. **Check validation set:** Is the model still improving on data it didn't train on?
5. **Repeat** for many epochs (full passes through data)

It's like taking practice tests and learning from every mistake — and grading yourself on a separate quiz so you know when you've stopped getting better.

```
Data → Network → Prediction → Compare → Adjust Weights → Score on Validation → Repeat
```

---

# Train / Validation / Test Split

We don't just split into train and test — we slice the **training** data one more time to get a **validation set**.

```
All Data
   │
   ├──► Test set (20%)              [LOCKED — only used at the very end]
   │
   └──► Training set (80%)
            │
            ├──► Actual training (~85% of training)   [weights learn from this]
            │
            └──► Validation set (~15% of training)    [scored after every epoch]
```

| Set | Used for | When |
|-----|----------|------|
| **Train** | Updating weights | Every iteration |
| **Validation** | Checking for overfitting | After every iteration |
| **Test** | Final report-card grade | Once, at the end |

> The validation chunk comes from training data. Your test set stays untouched.

---

# Early Stopping: When to Quit Training

Without early stopping, the network just trains until `max_iter`. Late in training it often starts memorizing noise — overfitting in action.

**Early stopping** watches the validation score and halts when it stops improving:

```python
MLPRegressor(
    max_iter=2000,            # generous upper bound
    early_stopping=True,      # turn on the validation check
    validation_fraction=0.15, # hold out 15% for validation
    n_iter_no_change=20,      # patience: wait 20 epochs before quitting
)
```

After fitting:

- `model.n_iter_` — when training actually halted
- `model.best_validation_score_` — best validation R² seen
- `model.loss_curve_` and `model.validation_scores_` — for plotting

Bonus: it **rolls back to the best weights**, not the final (worse) ones.

---

# Spotting Overfitting on the Loss Curve

Plot training loss (lower = better) and validation R² (higher = better) together — divergence is the tell.

```
training loss            validation R²
   │                          │     ────  best
   │\                         │   /
   │ \                        │  /
   │  \                       │ /
   │   \____                  │/             ← overfit zone:
   │       \___               │\____           val score drops
   │           \____          │     \___       while loss
   └──────── iter             └──────── iter   keeps falling
```

- **Both plateau together** → converged, no more juice. Time to stop.
- **Loss falling, val score still rising** → still learning. Keep going.
- **Loss falling, val score *dropping* from its peak** → overfitting. Early stopping triggers here, then rolls back to the peak.

---

# Why Scale Your Data?

Neural networks need scaled inputs (roughly -1 to 1).

**Without scaling:**
- Temperature: 0-100
- Humidity: 0-100
- Wind Speed: 0-30

Huge differences cause training problems!

**With StandardScaler:**
- All features around mean 0, std dev 1
- Network learns much faster and better

```python
from sklearn.preprocessing import StandardScaler
scaler = StandardScaler()
X_scaled = scaler.fit_transform(X_train)
```

---

# Comparison: All Techniques Learned

| Model | Strengths | Weaknesses | When to Use |
|-------|-----------|-----------|------------|
| **Decision Tree** | Interpretable, fast | Shallow patterns | Simple classification |
| **Random Forest** | Handles complex data | Slower, harder to interpret | Real-world classification |
| **Linear Regression** | Fast, simple | Only linear patterns | Continuous numbers (trend) |
| **Neural Network** | Complex patterns, images, text | Slow, black box, needs scaling | Large data, images, audio |

---

# Real-World Example: Weather Prediction

Using same Medina County 2024 data to predict max temperature:

**Linear Regression:** R² = 0.82, MAE = 2.3°F

**Neural Network (10-5):** R² = 0.83, MAE = 2.2°F

For this simple problem, similar performance! Neural networks excel with:
- 1000s of data points
- Images (computer vision)
- Audio/speech (NLP)
- Complex non-linear patterns

---

# AI Bias: Watch Out!

Neural networks learn from data. **Biased data = Biased AI.**

**Amazon Hiring AI (2018):** Trained on mostly male hires → penalized women's applications

**Healthcare Algorithm (2019):** Used spending as health proxy → underestimated Black patients' needs

**Questions to ask:**
- Who collected this data?
- What groups might be underrepresented?
- Who is harmed if the prediction is wrong?

**Your job:** Question assumptions about training data!

---

# Let's Build a Neural Network!

**Today's Task:**
1. Sub-Lesson 07a: Understand how neural networks work (TensorFlow Playground)
2. Sub-Lesson 07b: Build a neural network in Python
3. Compare to Linear Regression on same weather data

**Next:** Experiments with different architectures!
