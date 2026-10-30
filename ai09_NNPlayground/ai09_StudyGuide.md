# Lesson 09: Neural Network Playground - Study Guide

## The big idea
A neural network learns by adjusting **weights** and **biases** to reduce **loss** (error). The
TensorFlow Playground lets you *see* this happen and turn every knob yourself — **features,
layers, neurons, activation, learning rate, epochs** — before you set the same knobs in Python
next lesson. The key lesson: too small a network **underfits** (can't learn the pattern), a
too-big network on noisy data **overfits** (memorizes noise), and there's a sweet spot between.

## Vocabulary
1. **Neural network** - Layers of connected "neurons" that learn patterns from data.
2. **Neuron (node)** - A unit that combines inputs, applies weights + bias, and activates.
3. **Weight** - How much an input matters; shown as line thickness in the Playground.
4. **Bias** - A constant nudge added inside a neuron before activation.
5. **Layer** - A row of neurons. **Hidden layers** sit between input and output.
6. **Feature** - An input the network uses (x1, x2, x1², sin(x1), ...).
7. **Activation function** - The non-linear step (ReLU, Tanh, Sigmoid) that lets networks learn
   curves, not just straight lines.
8. **Learning rate** - How big each weight adjustment is per step. Too small = slow; too big =
   unstable.
9. **Epoch** - One full pass through the training data.
10. **Loss** - A number measuring error; training tries to make it small.
11. **Training loss vs. Test loss** - Error on data it learned from vs. new data.
12. **Underfitting** - Model too simple to capture the pattern (both losses high).
13. **Overfitting** - Model memorizes training data/noise; **test loss >> training loss**.
14. **Decision boundary** - The line/curve the network draws to separate classes (the OUTPUT
    picture).

## What each experiment teaches
| Experiment | Lesson |
|---|---|
| Blobs vs. spiral | Some data is easy (linearly separable), some needs a bigger network |
| 2 neurons on spiral | **Underfitting** — too little capacity |
| Add layers/neurons/features | Capacity lets the boundary bend into a spiral |
| Tiny vs. huge learning rate | Too small = crawls; too big = bounces/never settles |
| High noise + big net | **Overfitting** — training loss far below test loss |

## Playground -> Python (next lesson)
| Playground control | scikit-learn argument |
|---|---|
| Hidden layers & neurons | `hidden_layer_sizes=(10, 5)` |
| Activation | `activation='relu'` |
| Learning rate | `learning_rate_init=0.001` |
| Epochs (upper bound) | `max_iter=2000` |
| Test loss climbing | fix with `early_stopping=True` |

## Review Questions
1. **What do the connection lines represent?** Weights (thicker = larger).
2. **What is a hidden layer?** A layer of neurons between input and output.
3. **Why couldn't 2 neurons separate the spiral?** Too little capacity — it can only draw simple
   boundaries; this is underfitting.
4. **What does the learning rate control?** How big each weight-adjustment step is.
5. **What happens if the learning rate is too high?** Training becomes unstable; loss bounces and
   may never settle.
6. **What is an epoch?** One full pass through the training data.
7. **What is overfitting, and how do you spot it here?** The model memorizes noise; **test loss is
   much higher than training loss**.
8. **How do extra features (x1², sin) help?** They give the network more useful inputs, making some
   shapes (circles, spirals) easier to separate.
9. **What is the activation function for?** To add non-linearity so the network can learn curves.
10. **How does each Playground knob map to Python?** layers/neurons -> `hidden_layer_sizes`,
    activation -> `activation`, learning rate -> `learning_rate_init`, epochs -> `max_iter`.

## Resources
- TensorFlow Playground: https://playground.tensorflow.org
- Next up: ai10 Neural Networks — set these same knobs in Python with scikit-learn.
