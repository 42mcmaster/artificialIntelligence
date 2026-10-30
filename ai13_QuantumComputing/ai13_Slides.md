---
marp: true
theme: default
paginate: true
---

# Lesson 13: Quantum Computing
## A Bunny Trail — Artificial Intelligence
### Medina County Career Center

*Enrichment side-trip. Requires: `pip install pennylane`*

---

# Bits vs. Qubits

| Classical **bit** | Quantum **qubit** |
|---|---|
| 0 **or** 1 | 0, 1, **or both at once** |
| definite | **superposition** until measured |
| copyable | measuring **collapses** it |

A qubit is like a spinning coin: not heads or tails until it lands.

---

# A Quantum Circuit

Three pieces:

- **Device** — the quantum computer (or a simulator like `default.qubit`)
- **QNode** — the circuit, a Python function with `@qml.qnode(dev)`
- **Gates** — operations on qubits (Hadamard, RY, CNOT, ...)

```python
@qml.qnode(dev)
def superpose():
    qml.Hadamard(wires=0)      # create superposition
    return qml.probs(wires=0)  # -> [0.5, 0.5]
```

The **Hadamard** gate makes a perfect 50/50 coin.

---

# Steering a Qubit: RY(theta)

The **RY** gate rotates a qubit. Read it out as `<Z>` (from +1 to -1):

| theta | `<Z>` | meaning |
|---|---|---|
| 0 | **+1** | definitely 0 |
| pi/2 | **0** | 50/50 |
| pi | **-1** | definitely 1 |

`theta` is a dial from "0" to "1" — remember this, it becomes a trainable **weight** in a minute.

---

# Entanglement

Hadamard + **CNOT** links two qubits — the **Bell state**:

```python
qml.Hadamard(wires=0)
qml.CNOT(wires=[0, 1])
# probs over [00, 01, 10, 11] -> [0.5, 0, 0, 0.5]
```

You only ever measure **00** or **11** — never 01 or 10.
Measure one qubit and you instantly know the other. No classical equivalent.

---

# The Payoff: Quantum Machine Learning

A circuit with an adjustable angle is a **model with a weight**.
PennyLane computes **gradients of circuits**, so we can **train** them:

```python
opt = qml.GradientDescentOptimizer(stepsize=0.3)
theta = np.array(0.1, requires_grad=True)
for _ in range(60):
    theta = opt.step(cost, theta)   # minimize <Z>
# learned theta -> 3.142  (that's pi!)  ->  <Z> = -1.0
```

**Same gradient descent as neural nets** — but the model is a **quantum circuit**.

---

# Reality Check

- Real quantum computers today are **small and noisy** ("NISQ" era)
- They will **not** replace your laptop for everyday work
- But for a few problems — **chemistry/materials simulation**, certain
  **optimization** and **cryptography** — they could someday do what
  classical machines practically can't

You just wrote and trained **real quantum code**.

---

# Your Turn

1. **Walkthrough** — superposition, rotations, entanglement, training a qubit
2. **Task 13a** — build and steer your own circuits
3. **Task 13b** — entangle two qubits, then train one
4. **DIY** — explore a real PennyLane demo or design your own circuit

*A fun glimpse of where computing might go next.*
