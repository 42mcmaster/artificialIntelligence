# ai11 Cert Insert — Study Guide

**Course**: Applications of AI (CTE) | **School**: Medina County Career Center
**Instructor**: Ryan McMaster | **Standards**: ITS AI Domains 1.4, 1.5, 4.4, 6.1

> A short add-on to **ai11 (AI Ethics & Data Privacy)**. ai11 already covers algorithmic/training-data bias,
> fairness, transparency, accountability, and privacy laws. This adds the cert's specific bias *taxonomy*,
> a hands-on *fairness audit*, and *oversight*.

---

## 1. Name the bias (data)
| Type | Comes from | Example |
|---|---|---|
| **Sampling bias** | unrepresentative training data | model trained mostly on one group |
| **Labeling bias** | prejudice in human labels | biased "good hire" labels |
| **Historical / societal** | past inequities in the data | gender bias learned from old hiring data |
| **Measurement bias** | a flawed proxy feature | ZIP code as a stand-in for creditworthiness |

## 2. Name the bias (people)
- **Motivational bias** — slanting analysis toward a desired result.
- **Confirmation bias** — seeing only results that fit your belief.

## 3. Fairness audit (measure it)
Overall accuracy can hide per-group failure. Split the test set by a sensitive attribute, compute the
**same metric per group**, and flag large gaps. (Same idea as the accuracy trap on imbalanced data.)

## 4. Human oversight (Domain 6.1)
Human-in-the-loop for high-stakes decisions; **monitor** after launch (accuracy/fairness drift); be able
to **override/shut off**; assign **accountability**; plan responsible use **before** building.

---

## Study Tips
1. **Match the scenario to the bias type** — sampling (unrepresentative), labeling (biased labels),
   historical (past inequities), measurement (bad proxy); motivational/confirmation are people biases.
2. **Gender bias in a recruiting tool = historical/societal bias** (a real exam example).
3. **Fairness audit = compare the same metric across groups**; overall accuracy hides group failure.
4. **Oversight** = in-the-loop + monitoring + override + accountability, planned before launch.
