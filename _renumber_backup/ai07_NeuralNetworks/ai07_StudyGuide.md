# Lesson 07: Neural Networks - Study Guide

## Vocabulary

### Core Concepts

1. **Neuron (Artificial)** - A mathematical function that mimics biological neurons; takes inputs, applies weights, sums them, and applies an activation function
2. **Weight** - A learned parameter that controls how much an input influences a neuron's output; adjusted during training
3. **Bias** - A learnable offset added before activation; helps shift the decision boundary
4. **Activation Function** - A non-linear function (like ReLU or sigmoid) that decides if a neuron "fires"
5. **Layer** - A collection of neurons operating together; organized into input, hidden, and output layers
6. **Input Layer** - The first layer; represents raw data features (e.g., temperature, humidity)
7. **Hidden Layer** - Middle layers; learn increasingly complex patterns from data
8. **Output Layer** - Final layer; produces the prediction or classification
9. **Forward Pass** - Computing prediction by passing data through all layers from input to output
10. **Backpropagation** - Algorithm that adjusts weights by tracing error backwards through the network
11. **Loss Function** - Measures how wrong a prediction is; goal is to minimize it
12. **Epoch** - One complete pass through the training dataset
13. **Learning Rate** - Controls how much weights adjust per training step; too high = overshooting, too low = too slow
14. **StandardScaler** - Preprocessing technique that scales features to mean 0, standard deviation 1 (required for neural networks)
15. **MLPRegressor** - scikit-learn's Multi-Layer Perceptron Regressor; builds neural networks for continuous predictions
16. **Overfitting** - When a model learns noise in training data instead of true patterns; performs poorly on new data
17. **Deep Learning** - Neural networks with many hidden layers; can learn very complex patterns
18. **Activation** - The output of a neuron after applying the activation function
19. **Gradient Descent** - Optimization algorithm that adjusts weights to minimize loss
20. **Hidden Layer Sizes** - Parameter defining architecture (e.g., `(10, 5)` = two hidden layers with 10 and 5 neurons)
21. **Validation Set** - A slice of the *training* data held out during training; the model is scored on it after every iteration but never trains on it. Lets us watch for overfitting in real time without touching the test set.
22. **Early Stopping** - Automatically halts training when the validation score stops improving for a set number of iterations (`n_iter_no_change`). The model rolls back to the best weights it ever saw.
23. **Train / Validation / Test Split** - The three-way partition of the data: train (weights learn), validation (overfitting watchdog during training), test (final report card, untouched until the end).

---

## Quick Reference: Neural Network Pipeline in scikit-learn

```python
import pandas as pd
from sklearn.preprocessing import StandardScaler
from sklearn.neural_network import MLPRegressor
from sklearn.model_selection import train_test_split
from sklearn.metrics import r2_score, mean_absolute_error

# 1. LOAD DATA
data = pd.read_csv('medina_weather_2024.csv')
X = data[['temp_min', 'humidity', 'wind_speed']]
y = data['temp_max']

# 2. SPLIT DATA
X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)

# 3. SCALE DATA (required for neural networks!)
scaler = StandardScaler()
X_train_scaled = scaler.fit_transform(X_train)
X_test_scaled = scaler.transform(X_test)

# 4. CREATE MODEL with early stopping
#    hidden_layer_sizes: (10, 5) means 2 hidden layers with 10 and 5 neurons
#    max_iter: upper bound on training rounds (epochs)
#    early_stopping: hold out a validation chunk, watch it after each epoch
#    validation_fraction: 15% of training data for the validation watchdog
#    n_iter_no_change: stop if validation hasn't improved in 20 iterations
model = MLPRegressor(
    hidden_layer_sizes=(10, 5),
    max_iter=2000,
    early_stopping=True,
    validation_fraction=0.15,
    n_iter_no_change=20,
    random_state=42
)

# 5. TRAIN
model.fit(X_train_scaled, y_train)
# After fitting, useful diagnostics:
#   model.n_iter_                  -> when training actually stopped
#   model.best_validation_score_   -> best validation R² seen
#   model.loss_curve_              -> training loss per iteration
#   model.validation_scores_       -> validation R² per iteration

# 6. EVALUATE
predictions = model.predict(X_test_scaled)
r2 = r2_score(y_test, predictions)
mae = mean_absolute_error(y_test, predictions)

print(f"R² Score: {r2:.3f}")
print(f"Mean Absolute Error: {mae:.1f}")
```

---

## Comparison Chart: All ML Techniques

| Aspect | Decision Tree | Random Forest | Linear Regression | Neural Network |
|--------|---------------|---------------|--------------------|-----------------|
| **How it works** | Asks yes/no questions | Votes across many trees | Fits a straight line | Weighted connections in layers |
| **Interpretability** | High - you see each decision | Medium - combine trees | High - coefficients matter | Low - "black box" |
| **Training speed** | Fast | Medium | Very fast | Slow (lots of data) |
| **Data scaling needed?** | No | No | Optional | **YES** |
| **Works with images?** | No | No | No | Yes (CNN variant) |
| **Best for** | Categorical targets | Real-world classification | Linear trends | Complex patterns, images |
| **Risk of overfitting** | High | Low | Low | High (if too big) |
| **Requires lots of data?** | No | No | No | Yes |
| **Explainability** | "If humidity > 70..." | Multiple overlapping rules | "y = 2.3x + 5" | Hard to explain |

---

## Key Insights

### Why Scale Data for Neural Networks?
- Inputs with different ranges (0-100 vs 0-30) confuse the network
- StandardScaler puts all features on similar scale (~mean 0, std dev 1)
- Without scaling: training is slower, weights become huge, overfitting is more likely
- Quick check: `print(X_scaled.mean(), X_scaled.std())` should be ~0 and ~1

### When to Use Neural Networks
✓ You have 1000+ training examples
✓ Data has complex, non-linear patterns
✓ Working with images, audio, or text
✓ You have computational resources (training is slow)

✗ Small dataset (< 100 examples)
✗ Need to explain each decision
✗ Linear relationship (use Linear Regression instead)
✗ Simple categorical decisions (use Decision Tree)

### Avoiding Overfitting
- **Use early stopping** — set `early_stopping=True` and let scikit-learn carve out a validation chunk and halt training when the validation score plateaus. Cheapest, most effective fix.
- Plot `model.loss_curve_` and `model.validation_scores_` together. If validation R² peaks and then drops while training loss keeps falling, that's overfitting.
- Reduce layers/neurons if early stopping fires very early — that's a signal your network is too big for the data.
- Always remember the **train / validation / test** split. Validation comes from training data; the test set stays in the vault until the end.

### Train / Validation / Test in scikit-learn

You don't have to manually split a third time — `early_stopping=True` does it for you:

```python
# Step 1: your normal train/test split
X_train, X_test, y_train, y_test = train_test_split(X, y, test_size=0.2)

# Step 2: model with early stopping carves the validation set internally
model = MLPRegressor(
    early_stopping=True,
    validation_fraction=0.15,   # 15% of X_train becomes validation
    n_iter_no_change=20,
)
model.fit(X_train_scaled, y_train)
```

Effective layout:
- 80% of original data → train (of which 85% trains, 15% validates)
- 20% of original data → test (untouched until final scoring)

---

## ODE Competencies Covered

**2.14.1** Distinguish between machine learning, neural networks, and other computational approaches (decision trees, rule-based systems)

**2.14.5** Apply machine learning techniques to solve real-world problems and interpret results

**5.1.1** Use Python to perform data analysis including preprocessing, model building, and evaluation

**5.1.2** Implement scikit-learn algorithms for supervised learning tasks

---

## Review Questions

1. **What is a weight in a neural network?** A learned parameter that controls how much each input influences a neuron's output.

2. **Why do neural networks need scaled data?** Unscaled features with different ranges confuse the network and slow training.

3. **What is backpropagation?** An algorithm that traces error backwards through the network to adjust weights.

4. **When should you use a neural network instead of Linear Regression?** When data has complex non-linear patterns or you have images/audio.

5. **What is overfitting?** When a model learns noise in training data instead of true patterns; performs poorly on new data.

6. **How many hidden layers do you need?** Start with 1-2. More layers = more complex patterns but slower training and overfitting risk.

7. **What's the difference between forward pass and backpropagation?** Forward: predict using current weights. Backprop: adjust weights using error.

8. **How do you reduce overfitting?** Use fewer neurons, stop training earlier (preferably with `early_stopping=True`), use more training data, watch a validation set during training.

9. **What is a validation set, and how is it different from the test set?** A validation set is a chunk of the *training* data held out so we can score the model after each iteration during training. The test set is locked away and only used at the very end for the final report card. Validation is for *tuning*; test is for *grading*.

10. **What does `early_stopping=True` do in MLPRegressor?** It tells scikit-learn to (a) hold out a small validation fraction of the training data, (b) score the model on it after each iteration, and (c) stop training when the validation score hasn't improved for `n_iter_no_change` iterations in a row. The model also rolls back to the best weights it ever saw, not the final ones.

---

## Common Parameter Configurations

All recipes below use early stopping so `max_iter` is just an upper bound — the actual iteration count is decided by the validation watchdog.

### For Simple Problems (Weather Prediction)
```python
MLPRegressor(
    hidden_layer_sizes=(10, 5),
    max_iter=2000,
    early_stopping=True, validation_fraction=0.15, n_iter_no_change=20,
    random_state=42,
)
```

### For Medium Problems
```python
MLPRegressor(
    hidden_layer_sizes=(50, 25, 10),
    max_iter=3000,
    early_stopping=True, validation_fraction=0.15, n_iter_no_change=20,
    random_state=42,
)
```

### For Complex Problems
```python
MLPRegressor(
    hidden_layer_sizes=(100, 50, 25),
    max_iter=5000,
    early_stopping=True, validation_fraction=0.15, n_iter_no_change=30,
    random_state=42,
)
```

---

## Resources
- TensorFlow Playground: playground.tensorflow.org
- scikit-learn MLPRegressor: https://scikit-learn.org/stable/modules/neural_networks_supervised.html
- Medina Weather Data: `medina_weather_2024.csv`
