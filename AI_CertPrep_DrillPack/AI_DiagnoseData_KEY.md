# AI Cert Drill: Diagnose the Data & Classify the Problem — ANSWER KEY

**INSTRUCTOR / SELF-CHECK KEY**

---

## Part A
1. `age` = 34 → **ok**
2. `country` = Unknown → **missing / placeholder value** (a text stand-in for missing)
3. `amount_usd` = NaN → **missing value**
4. `signup_date` = 2026-13-02 → **invalid value** (there is no month 13)

## Part B
5. Temperature °F → **numerical (continuous)**
6. Eye color → **categorical** (no order)
7. Number of children → **numerical (discrete/count)**
8. T-shirt size → **ordinal** (categories with a meaningful order)

## Part C
9. Predict temperature → **regression** (a continuous number)
10. Spam or not → **classification** (two labels)
11. Group into undefined segments → **clustering** (unsupervised)
12. Predict sale price → **regression**
13. Cat vs dog → **classification**

## Part D
14. Labeled emails → **supervised**
15. No labels, find groupings → **unsupervised**
16. Trial and error with rewards → **reinforcement**

> **Teaching note:** the exam constantly asks students to CLASSIFY the problem before choosing a model. Rule of thumb: predicting a **number** = regression; predicting a **label** = classification; finding **unknown groups** = clustering.