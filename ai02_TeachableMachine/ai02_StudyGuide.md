# Lesson 02: Train Your First AI (Teachable Machine) - Study Guide

## The big idea
**Supervised learning** = teaching a model from **labeled examples**. In Teachable Machine you
give the model groups of labeled images (**classes**), it **trains** to find patterns that tell
them apart, and then you **test** it on new images. This is the same idea behind every model you'll
build in Python this year — decision trees, random forests, neural networks — just with the code
hidden.

## Vocabulary
1. **Artificial Intelligence (AI)** - Computers doing tasks that normally need human intelligence.
2. **Machine Learning (ML)** - AI that learns patterns from data instead of being explicitly programmed.
3. **Supervised Learning** - Learning from **labeled** examples (each example has a known answer).
4. **Class** - A labeled category the model learns (e.g., "cat", "dog").
5. **Training data** - The labeled examples used to teach the model.
6. **Training** - The process of finding patterns in the training data.
7. **Model** - The trained system that makes predictions.
8. **Prediction** - The model's guess for a new input.
9. **Confidence** - How sure the model is, shown as a percentage per class.
10. **Test data** - New examples (not used in training) used to check the model.
11. **Generalization** - How well a model does on **new**, unseen data.
12. **Teachable Machine** - Google's free browser tool for training simple models with no code.
13. **Epoch** - One full pass through the training data (you'll see this again in neural nets).

## Key insights
- **More and more varied training data usually improves accuracy.** Few or one-sided examples make
  a weak, biased model.
- **Always test on NEW images.** Scoring on the training images would be like grading a test with
  the answer key — it tells you nothing about real performance.
- **Confidence is not truth.** A model can be confidently wrong. High % just means the model is
  sure, not that it's correct.
- The model only knows what you showed it. Show it only orange cats and it may fail on a black cat —
  that's **biased training data** (more in ai11 Ethics).

## How this connects to the rest of the course
| Teachable Machine (today) | In Python (soon) |
|---|---|
| Groups of labeled images | `X` (features) and `y` (labels) |
| "Train Model" button | `model.fit(X_train, y_train)` |
| Testing new images | `model.predict(X_test)` |
| Confidence bars | probabilities / accuracy |

## Review Questions
1. **What is supervised learning?** Learning from labeled examples.
2. **What is a "class" in Teachable Machine?** A labeled category the model learns.
3. **Why must you test on new images?** To measure how well it generalizes, not memorizes.
4. **What usually happens when you add more training data?** Accuracy/confidence usually improves.
5. **What does the confidence percentage mean?** How sure the model is — not a guarantee it's right.
6. **Why might a model struggle on some images?** Unusual angle/lighting/background, look-alikes, or
   too few/one-sided training examples.
7. **What is generalization?** Performing well on new, unseen data.
8. **How can biased training data hurt a model?** It learns a narrow pattern and fails on examples
   outside it.
9. **What is the Python equivalent of clicking "Train Model"?** `model.fit(...)`.
10. **What is an epoch?** One full pass through the training data.

## Resources
- Teachable Machine: https://teachablemachine.withgoogle.com
- Next up: ai03 Decision Trees — the same idea, now in Python.
