---
marp: true
theme: default
paginate: true
---

# Lesson 09: Neural Network Playground
## Artificial Intelligence
### Medina County Career Center

*Build intuition for how neural networks learn — by turning the knobs yourself.*

---

# Before We Code a Neural Network...

Next lesson you'll build one in Python. Today you'll **feel** how it works by playing with a
live, visual neural network in your browser:

**https://playground.tensorflow.org**

You'll adjust the network's **parameters** and watch — in real time — whether it learns to
separate the data.

---

# The Parameters You'll Control

| Parameter | What it does |
|---|---|
| **Features** | Which inputs the network sees (x1, x2, x1², ...) |
| **Hidden layers** | How many layers between input and output |
| **Neurons per layer** | How many nodes in each hidden layer |
| **Activation** | The non-linear function (ReLU, Tanh, Sigmoid) |
| **Learning rate** | How big each weight adjustment is |
| **Epochs** | How many passes through the data (the counter at top) |

More layers/neurons = can learn more complex shapes, but slower and can **overfit**.

---

# Weights, Biases, and Learning

Inside the network:
- Each connection has a **weight** (how much that input matters) — shown as line **thickness**.
- Each neuron has a **bias** (a constant nudge).
- **Training** adjusts weights and biases to reduce the **loss** (the error).

Watch the **Test loss** number fall as it learns. If test loss stays high, the model can't
separate the data — yet.

---

# The Experiments (in your worksheet)

1. **Easy vs hard data:** try the two-blob dataset, then the **spiral**.
2. **Too small a network:** can 1 neuron separate the spiral? Why not?
3. **Grow the network:** add layers/neurons until the spiral is solved.
4. **Learning rate:** set it tiny, then huge — what breaks?
5. **Overfitting:** crank up noise and size — does test loss get *worse* than training loss?

Record what you see. You're discovering the same trade-offs you'll code next lesson.

---

# Why This Matters

Everything here returns in Python next lesson:

| Playground | ai10 in Python (`MLPRegressor`/`MLPClassifier`) |
|---|---|
| Hidden layers / neurons | `hidden_layer_sizes=(10, 5)` |
| Activation | `activation='relu'` |
| Learning rate | `learning_rate_init=...` |
| Epochs | `max_iter=...` |
| Test loss rising | overfitting (early stopping) |

**Turn the knobs today so the code makes sense tomorrow.** Head to the Walkthrough.
