---
marp: true
theme: default
paginate: true
---

# ai03 Cert Insert: Confusion Matrix, Metric Choice & Data Prep
## Artificial Intelligence
### Medina County Career Center

*(a short add-on to ai03 — only the cert-tested bits ai03 doesn't already cover)*

---

# You Already Know Most of This

In **ai03 (ML Decision Trees)** you already learned — on the Titanic model:
- **accuracy, precision, recall, F1** (from `classification_report`)
- **train/test split** and **overfitting vs. underfitting** (the `max_depth` comparison)
- **one-hot encoding**, dropping missing values, features vs. target

This insert adds just the **few extra things the ITS AI exam tests** that ai03 doesn't spell out.

---

<!-- _header: "Part 1 — The Confusion Matrix (behind the report)" -->

# Where precision & recall come FROM

`classification_report` gave you precision and recall. They're computed from a 2×2 table — the
**confusion matrix** — which the exam shows directly:

| | Predicted YES | Predicted NO |
|---|---|---|
| **Actually YES** | True Positive (TP) | False Negative (FN) — a *miss* |
| **Actually NO** | False Positive (FP) — a *false alarm* | True Negative (TN) |

- **Precision** = TP / (TP + FP) · **Recall (sensitivity)** = TP / (TP + FN)
- `sklearn.metrics.confusion_matrix(y_true, y_pred)` prints it as `[[TN, FP], [FN, TP]]`.

---

<!-- _header: "Part 1 — Pick the Right Metric" -->

# Precision vs. Recall: a Trade-off

The exam asks *which metric matters* for a scenario — because the two errors aren't equal:

| Scenario | Costly error | Optimize |
|---|---|---|
| **Cancer screening** | missing a real case (FN) | **Recall** (a.k.a. sensitivity) |
| **Spam filter** | flagging real email (FP) | **Precision** |
| both matter | — | **F1** |

Pushing recall up usually pushes precision down — you choose based on which mistake is worse.

---

<!-- _header: "Part 1 — The Accuracy Trap" -->

# Why Accuracy Can Lie

On **imbalanced** data, accuracy is misleading. If 95% of cases are class 0, a model that always
predicts 0 scores **95% accuracy** while catching **zero** class-1 cases (recall = 0).

**On imbalanced data, read precision/recall per class — not accuracy.** (This is why your Titanic
model's ~80% is more meaningful than a lazy 62% baseline.)

---

<!-- _header: "Part 2 — Data Prep the cert adds" -->

# Data-Quality as a Named Step

ai03 dropped missing values and encoded categories. The cert also names these checks:

| Check | pandas | Fix |
|---|---|---|
| Duplicates | `df.duplicated().sum()` | `df.drop_duplicates()` |
| Outliers | `df.describe()` / > 3 std devs | investigate/remove if invalid |
| Class balance | `df["target"].value_counts()` | **stratified** split |

Plus two feature techniques beyond one-hot: **scaling** numbers to a common range, and turning
**text into features** (Bag-of-Words / TF-IDF).

---

<!-- _header: "Part 2 — Stratified Split" -->

# Stratified Split (a better train/test split)

Your ai03 split used plain `train_test_split`. On imbalanced data, add `stratify=y` so the train and
test sets keep the **same class balance**:

```python
train_test_split(X, y, test_size=0.2, random_state=42, stratify=y)
```

Without it, a small test set might contain almost none of the rare class — making evaluation meaningless.

---

# Key Takeaways (what's new vs. ai03)

| Concept | The add |
|---|---|
| **Confusion matrix** | TP/FP/FN/TN — the table precision & recall come from |
| **Metric choice** | recall when a miss is worst; precision when a false alarm is worst |
| **Accuracy trap** | accuracy misleads on imbalanced data |
| **Quality checks** | duplicates, outliers, class balance (named) |
| **Stratified split** | keep class balance across train/test |
| **Text → features** | Bag-of-Words / TF-IDF |

---
