# AI Cert Drill: Read the Chart & the Metric — ANSWER KEY

**INSTRUCTOR / SELF-CHECK KEY**

---

## Part A
1. **TP = 40** (actual spam, predicted spam)
2. **FN = 10** (actual spam, predicted not-spam — the missed spam)
3. **FP = 5** (actual not-spam, predicted spam — the false alarms)
4. **TN = 45** (actual not-spam, predicted not-spam)
5. **Accuracy = (40 + 45) / 100 = 85 / 100 = 85%**
6. **Precision = 40 / (40 + 5) = 40/45 = 0.889 (~89%)** — when it says 'spam,' it's right 89% of the time
7. **Recall/Sensitivity = 40 / (40 + 10) = 40/50 = 0.80 (80%)** — it catches 80% of the real spam
8. Slightly better at **precision (89%) than recall (80%)**: it rarely mislabels good email, but it lets ~1 in 5 spam through. For a spam filter that's usually the right trade (users hate losing real email more than seeing occasional spam).

## Part B
9. **Overfitting** (high train, low validation, wide gap = memorized the training set)
10. **Underfitting** (both low = model too simple to learn the pattern)
11. **Good fit** (both high and close)
12. **Overfitting**

## Part C
13. **Recall** — you must catch every real case; a false alarm (low precision) is acceptable, a miss (low recall) is not.
14. **Precision** — a false positive (flagging real email) is the costly error; you'd rather let some spam through.
15. A model that always predicts class A scores **95% accuracy** while catching **zero** class-B cases — accuracy hides total failure on the minority class. Look at **precision, recall, and the confusion matrix per class** (and consider stratified sampling / balancing).

> **Teaching note:** precision vs. recall is the exam's favorite trade-off. The one-liner: *precision = 'when it says yes, is it right?'; recall = 'of all the real yeses, how many did it find?'* Which one matters depends on which error is worse.