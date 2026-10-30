# Lesson 13: Quantum Computing (Bunny Trail) - Study Guide

> **This is an enrichment lesson** — a fun side-trip beyond the core AI course. It requires
> the PennyLane library: `pip install pennylane`.

## The big idea
Classical computers store **bits** (0 or 1). Quantum computers store **qubits**, which can be
in a blend of 0 and 1 at once (**superposition**) and can be **entangled** with each other.
This lets them explore many possibilities in parallel — useful for a few special problems.
PennyLane is special because it can **train** quantum circuits with gradient descent, the same
way you trained neural networks (this field is called **quantum machine learning**).

## Vocabulary
1. **Bit** - Classical unit of information: 0 or 1.
2. **Qubit** - Quantum bit; can be 0, 1, or a superposition of both.
3. **Superposition** - A qubit being a blend of 0 and 1 until measured.
4. **Measurement** - Reading a qubit; it randomly collapses to 0 or 1 with set probabilities.
5. **Quantum circuit** - A sequence of gates applied to qubits.
6. **Gate** - An operation on qubits (the quantum version of AND/OR/NOT).
7. **Hadamard (H)** - Gate that creates an equal superposition (a perfect 50/50 coin).
8. **RY(theta)** - Rotation gate; the angle `theta` controls the 0-vs-1 probabilities.
9. **CNOT** - Two-qubit gate that flips a target qubit based on a control qubit; used to entangle.
10. **Entanglement** - A link between qubits so measuring one reveals the other.
11. **Bell state** - The simplest entangled state; measures only 00 or 11.
12. **Expectation value** - Average measurement outcome; `<Z>` runs +1 (|0>) to -1 (|1>).
13. **Wires** - PennyLane's word for qubits.
14. **Device** - The quantum computer or simulator (e.g., `default.qubit`).
15. **QNode** - A Python function decorated with `@qml.qnode(dev)` that defines a circuit.
16. **Variational circuit** - A circuit with adjustable parameters (like model weights).
17. **Quantum Machine Learning (QML)** - Training quantum circuits with gradient descent.
18. **NISQ** - "Noisy Intermediate-Scale Quantum": today's small, error-prone quantum hardware.

## Quick reference
```python
import pennylane as qml
from pennylane import numpy as np

dev = qml.device('default.qubit', wires=2)   # a 2-qubit simulator

@qml.qnode(dev)
def circuit(theta):
    qml.Hadamard(wires=0)        # superposition
    qml.RY(theta, wires=0)       # rotation (an adjustable "weight")
    qml.CNOT(wires=[0, 1])       # entangle qubit 0 with qubit 1
    return qml.expval(qml.PauliZ(0))   # or qml.probs(wires=[0,1])

# Train it like a neural net:
opt = qml.GradientDescentOptimizer(stepsize=0.3)
theta = np.array(0.1, requires_grad=True)
for _ in range(60):
    theta = opt.step(circuit, theta)
```

## Key facts to remember
- **Hadamard** => 50/50 superposition (`probs` = `[0.5, 0.5]`).
- **RY(theta)** steers the odds: `<Z>` = +1 at theta=0, 0 at theta=pi/2, -1 at theta=pi.
- **Bell state** (H + CNOT) => only `00` and `11` ever occur (`[0.5, 0, 0, 0.5]`).
- PennyLane can compute **gradients of circuits**, so gradient descent trains a **variational
  circuit** exactly like it trains a neural network — the angle is the "weight."
- Real quantum computers are **small and noisy today (NISQ)**; they won't replace classical
  computers for everyday work, but may excel at chemistry simulation and certain optimization.

## How this connects to the rest of the course
The training loop is the **same gradient descent** from ai10 (Neural Networks): a model with
tunable weights, a cost to minimize, and an optimizer that nudges the weights downhill. Here
the "model" is a quantum circuit and the "weight" is a rotation angle.

## Review Questions
1. **How is a qubit different from a bit?** A bit is 0 or 1; a qubit can be a superposition of both.
2. **What does the Hadamard gate do?** Puts a qubit into an equal 50/50 superposition.
3. **What happens when you measure a superposed qubit?** It randomly collapses to 0 or 1.
4. **What does `<Z>` = -1 tell you?** The qubit is (definitely) in state |1>.
5. **What is entanglement?** A link where measuring one qubit reveals the other's value.
6. **Which two outcomes appear for a Bell state?** Only 00 and 11.
7. **What is a variational circuit?** A circuit with adjustable parameters, like model weights.
8. **How is quantum ML like neural-network training?** Both use gradient descent to tune weights.
9. **What does NISQ mean?** Noisy Intermediate-Scale Quantum — today's small, error-prone hardware.
10. **Name a problem quantum computers might help with.** Chemistry/materials simulation, some
    optimization or cryptography tasks.

## Resources
- PennyLane demos: https://pennylane.ai/qml/demonstrations
- PennyLane docs: https://docs.pennylane.ai
- Install: `pip install pennylane`
