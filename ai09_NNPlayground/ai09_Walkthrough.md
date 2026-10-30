# Lesson 09 Walkthrough: Neural Network Playground
**Artificial Intelligence — Medina County Career Center**

> No coding today — you'll drive a live neural network at **https://playground.tensorflow.org**
> and record what you see in the Task worksheet. Do the steps in order.

---

## Orientation (2 minutes)
Open **https://playground.tensorflow.org**. Find these pieces:
- **Left:** the **Data** panel — pick which dataset to learn (blobs, circle, XOR, **spiral**) and
  a **Noise** slider.
- **Middle:** **FEATURES** (the inputs) and the **hidden layers** with **neurons** (dots). Use the
  **+ / -** buttons to add/remove layers and neurons.
- **Top bar:** the **Play** button, the **Epoch** counter, **Learning rate**, **Activation**.
- **Right:** the **OUTPUT** picture and the **Test loss / Training loss** numbers.

The lines between neurons are **weights** — thicker/brighter = larger weight.

---

## Experiment 1 — Easy data
1. Pick the **two-blob** dataset (top-left, two separated clusters).
2. Set: **1 hidden layer, 2 neurons**, Activation **Tanh**, Learning rate **0.03**.
3. Press **Play**. Watch the OUTPUT panel and the **Test loss**.

**Record:** About how many epochs until Test loss drops below ~0.1? Did the output cleanly split
the two colors?

---

## Experiment 2 — Hard data (the spiral)
1. Stop, then choose the **spiral** dataset (bottom-right).
2. Keep **1 hidden layer, 2 neurons**. Press **Play** and let it run to ~300 epochs.

**Record:** Can this tiny network separate the spiral? What does the output look like? Why do you
think 2 neurons isn't enough?

---

## Experiment 3 — Grow the network
1. Still on the spiral, **add neurons and layers** (try **2 hidden layers, 6–8 neurons each**).
2. Turn on more **FEATURES** (e.g., add `x1²`, `x2²`, and `sin(x1)`).
3. Press **Play** and run until Test loss stops improving.

**Record:** What layer/neuron/feature combination finally separated the spiral? What was your
lowest Test loss?

---

## Experiment 4 — Learning rate
Reset the spiral with your working network from Experiment 3. One change at a time:
1. Set **Learning rate = 0.0001** (tiny). Play ~200 epochs.
2. Set **Learning rate = 3** (huge). Play ~200 epochs.

**Record:** What happens with a tiny rate? With a huge rate? (Look for "learns very slowly" vs.
"loss bounces around / never settles.")

---

## Experiment 5 — Overfitting
1. Keep a **large** network (2+ layers, 8 neurons each).
2. Slide **Noise** up to ~30–40 and set the **Ratio of training to test data** to a small
   training amount (e.g., 20%).
3. Press **Play** and let it run a long time.

**Record:** Does **Training loss** get much lower than **Test loss**? That gap is **overfitting** —
the network memorized the noisy training points instead of the real pattern. (Next lesson,
`early_stopping=True` fixes exactly this.)

---

## Wrap-up
You just controlled, by hand, every dial you're about to set in Python:
layers, neurons, activation, learning rate, epochs — and you **saw** underfitting (too small),
good fit, and overfitting (too big + noisy). Fill in the **Task worksheet** with your recorded
answers.
