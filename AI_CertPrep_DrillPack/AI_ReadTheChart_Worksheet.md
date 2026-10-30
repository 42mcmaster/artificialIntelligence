# AI Cert Drill: Read the Chart & the Metric

**Course**: Applications of AI (CTE) | **Instructor**: Ryan McMaster — Medina County Career Center  
**Rehearses the ITS AI exam's most technical format: interpreting a confusion matrix, a learning curve, and evaluation metrics (accuracy / precision / recall / sensitivity).**

Work each item by hand. This is the #1 skill the exam tests that classroom ML often skips.

---

## Part A — The Confusion Matrix

A spam classifier was tested on 100 emails. Here are the results:

```
                 Predicted SPAM   Predicted NOT-SPAM
  Actual SPAM          40                10          (50 real spam)
  Actual NOT-SPAM       5                45          (50 real not-spam)
```
Fill in the blanks (formulas provided):

1. **True Positives (TP)** = spam correctly caught = `____`
2. **False Negatives (FN)** = spam missed = `____`
3. **False Positives (FP)** = good email wrongly flagged = `____`
4. **True Negatives (TN)** = good email correctly kept = `____`
5. **Accuracy** = (TP + TN) / total = `____ / 100 = ____%`
6. **Precision** = TP / (TP + FP) = *of the emails we called spam, how many were?* = `____`
7. **Recall / Sensitivity** = TP / (TP + FN) = *of the real spam, how much did we catch?* = `____`
8. In one sentence: is this model better at **precision** or **recall**, and what does that mean for the user?

## Part B — The Learning Curve

For each described learning curve, name the condition — **overfitting**, **underfitting**, or **good fit**:

9. Training accuracy is very high (98%) but validation accuracy is much lower (70%), and the gap stays wide. → `____________`
10. Both training and validation accuracy are low (~60%) and close together. → `____________`
11. Training and validation accuracy are both high (~90%) and close together. → `____________`
12. A model memorizes the training data but fails on new data. This is called → `____________`

## Part C — Pick the Right Metric

13. A cancer-screening model must **not miss** real cases (a miss is deadly). Which metric matters most? → `precision` or `recall`?
14. A spam filter must **not flag** important real email as spam. Which metric matters most? → `precision` or `recall`?
15. A dataset is 95% class A, 5% class B. Why is **accuracy** a misleading metric here, and what should you look at instead?
