# Lesson 09a Task — Playground Exploration Worksheet
**Artificial Intelligence — Medina County Career Center**

Name: ______________________  Date: __________

Fill this in as you run the Walkthrough experiments at https://playground.tensorflow.org.

## Experiment 1 — Easy data (two blobs)
1. Epochs until Test loss < ~0.1: __________
2. Did the output cleanly separate the two colors? (Y/N) __________

## Experiment 2 — Spiral with a tiny network (1 layer, 2 neurons)
3. Could it separate the spiral? (Y/N) __________
4. In 1–2 sentences, why isn't a 2-neuron network enough for the spiral?

## Experiment 3 — Grow the network
5. The setup that finally solved the spiral:
   - Hidden layers: ______  Neurons per layer: ______
   - Extra features turned on: __________________________
6. Lowest Test loss you reached: __________

## Experiment 4 — Learning rate (one change at a time)
7. With learning rate **0.0001**, what happened?

8. With learning rate **3**, what happened?

9. In one sentence: what is the learning rate controlling?

## Experiment 5 — Overfitting
10. With high noise + little training data, was **Training loss** much lower than **Test loss**?
    (Y/N) __________
11. What does that gap tell you about the model?

## Tie it to the code
12. Match each Playground control to its Python setting (draw a line or write the pair):

| Playground | Python (`MLPClassifier`) |
|---|---|
| Neurons/layers | `activation='relu'` |
| Activation | `hidden_layer_sizes=(8, 8)` |
| Learning rate | `max_iter=...` |
| Epochs | `learning_rate_init=...` |
