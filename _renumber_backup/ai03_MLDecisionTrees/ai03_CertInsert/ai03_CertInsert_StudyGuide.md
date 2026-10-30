# ai03 Cert Insert — Study Guide

**Course**: Applications of AI (CTE) | **School**: Medina County Career Center
**Instructor**: Ryan McMaster | **Standards**: ITS AI Domain 2 (data) + Domain 3 (features) + Domain 4 (evaluation)

> A short add-on to **ai03 (ML Decision Trees)**. ai03 already teaches accuracy, precision, recall, F1,
> train/test split, overfitting, and one-hot encoding. This covers only the extra cert-tested bits.

---

## Part 1 — Evaluation extras

### The confusion matrix (where precision/recall come from)
| | Predicted YES | Predicted NO |
|---|---|---|
| **Actually YES** | TP | FN (miss) |
| **Actually NO** | FP (false alarm) | TN |

- **Precision** = TP/(TP+FP) — of predicted-YES, how many were right.
- **Recall / sensitivity** = TP/(TP+FN) — of real-YES, how many caught.
- `confusion_matrix(y_true, y_pred)` prints `[[TN, FP],[FN, TP]]`.

### Pick the metric for the scenario
- **Recall** when a *miss* is worst (cancer screening, fraud).
- **Precision** when a *false alarm* is worst (spam filter).
- **F1** when both matter. Raising recall usually lowers precision (trade-off).

### The accuracy trap
On imbalanced data, always-guess-the-majority scores high accuracy but catches none of the minority
(recall 0). Read precision/recall per class, not accuracy alone.

## Part 2 — Data-prep extras

| Check | pandas | Fix |
|---|---|---|
| Duplicates | `df.duplicated().sum()` | `df.drop_duplicates()` |
| Outliers | `df.describe()` (> 3 std devs) | investigate/remove if invalid |
| Class balance | `df["target"].value_counts()` | stratified split |

- **Scaling** — put numeric features on a common range (0–1 or z-score).
- **Text → features** — Bag-of-Words / TF-IDF (images → grayscale pixel values).
- **Stratified split** — `train_test_split(..., stratify=y)` keeps class balance in train and test.

---

## Study Tips
1. `classification_report` (ai03) gives precision/recall; the **confusion matrix** is the 2×2 table they come from.
2. **Recall = catch every real yes; Precision = don't false-alarm.** Choose by which error is worse.
3. **Accuracy lies on imbalanced data** — the exam tests this.
4. Beyond ai03's `dropna`/`get_dummies`: check **duplicates, outliers, class balance**; use **stratified** splits; know **text→features**.
