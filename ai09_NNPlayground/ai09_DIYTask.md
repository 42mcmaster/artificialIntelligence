# Lesson 09 DIY Challenge — Neural Network Playground
**Artificial Intelligence — Medina County Career Center**

Pick **one** and write a short report with 2–3 screenshots.

## Option A — Minimal solver
For the **spiral** dataset, find the **smallest** network (fewest total neurons) that still gets
Test loss under 0.1. Report your architecture and loss. What's the fewest neurons that works?

## Option B — Feature power
Solve the **circle** dataset using **only** raw features `x1` and `x2` (no squared/sin features).
Then solve it again **with** `x1²` and `x2²` turned on. Which was easier, and why do the extra
features help?

## Option C — Break it on purpose
Create a clear case of **overfitting**: high noise, big network, little training data. Screenshot
the moment Training loss is far below Test loss, and explain in a paragraph what's happening and
how `early_stopping` (next lesson) would help.
