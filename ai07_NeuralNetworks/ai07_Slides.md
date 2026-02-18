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
4. **Repeat** for many epochs (full passes through data)

It's like taking practice tests and learning from every mistake!

```
Data → Network → Prediction → Compare → Adjust Weights → Repeat
```

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
