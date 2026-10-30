---
marp: true
theme: default
paginate: true
---

# ai11 Cert Insert: Bias Types, Fairness Audits & Oversight
## Artificial Intelligence
### Medina County Career Center

*(a short add-on to ai11 — the cert's specific bias vocabulary and a hands-on fairness check)*

---

# You Already Know the Ethics

In **ai11 (AI Ethics & Data Privacy)** you already learned:
- **algorithmic bias** and **training-data (historical) bias**
- **fairness, transparency, accountability** as ethical principles
- privacy laws (HIPAA, FERPA, GDPR, PCI DSS)

This insert adds the few extra **cert-tested** items: the **specific names for bias types**, a
**hands-on fairness audit**, and **oversight/monitoring**.

---

<!-- _header: "Part 1 — Name the Bias" -->

# The Bias Taxonomy (know these by name)

The exam asks you to *name the type of bias* in a scenario:

| Type | Where it comes from | Example |
|---|---|---|
| **Sampling bias** | training data doesn't represent the real population | voice model trained mostly on one group |
| **Labeling bias** | the human labels carry prejudice | biased "good hire" labels |
| **Historical / societal** | past inequities are in the data | recruiting tool learns gender bias from old data |
| **Measurement bias** | a feature is a flawed proxy | ZIP code standing in for creditworthiness |

*(ai11 covered "algorithmic" and "training-data" bias — these are the finer distinctions.)*

---

<!-- _header: "Part 1 — Bias in People" -->

# Bias in the Analyst, Too

Not all bias is in the data — some is in how results are used:

- **Motivational bias** — slanting an analysis toward the answer you *want* (e.g., a report that earns a bonus)
- **Confirmation bias** — noticing only the results that fit your belief

Responsible practice guards against **both** the data's bias and the person's.

---

<!-- _header: "Part 2 — Audit for Fairness" -->

# How to DETECT Bias: Compare Across Groups

Ethics (ai11) tells you *why* fairness matters. The cert also wants you to *measure* it:

- A model with good **overall** accuracy can still fail one group badly.
- Split the test set by a sensitive attribute (group A vs. B).
- Compute the **same metric** (recall, error rate) for **each group**.
- A large **gap** between groups is a fairness red flag.

**Overall accuracy hides per-group failure** — so audit by group.

---

<!-- _header: "Part 3 — Oversight" -->

# Human Oversight (Domain 6.1)

Beyond transparency and accountability (ai11), the cert expects **ongoing oversight**:

- Keep a **human in the loop** for high-stakes decisions (hiring, lending, medical)
- **Monitor** the model after launch — accuracy and fairness can drift
- Be able to **override or shut it off**
- Assign someone **accountable**; plan responsible use **before** you build

---

# Key Takeaways (what's new vs. ai11)

| Concept | The add |
|---|---|
| **Bias taxonomy** | sampling · labeling · historical · measurement · motivational · confirmation |
| **Fairness audit** | compare the same metric across groups; a gap = red flag |
| **Overall accuracy** | hides per-group failure |
| **Human oversight** | in-the-loop, monitor, override, accountable |

---
