---
marp: true
theme: default
paginate: true
---

# Lesson 09: AI Ethics & Data Privacy
## Artificial Intelligence
### Medina County Career Center

---

<!-- _header: "Sub-Lesson 09a — AI Ethics & Bias" -->

# AI Ethics & Bias

**Real-world bias examples:**
- Amazon hiring AI (2018) → Penalized women candidates
- Healthcare algorithm (2019) → Underestimated care needs for Black patients
- Facial recognition → Disparities across racial groups
- Predictive policing → Self-fulfilling prophecies in over-policed neighborhoods

**How does bias happen?**
- Biased training data reflects historical discrimination
- AI learns and amplifies patterns
- Lack of diverse perspectives in development

---

<!-- _header: "Sub-Lesson 09a — AI Ethics & Bias" -->

# Ethical Frameworks for AI

**Four Core Principles:**

1. **Fairness** → Equal treatment; no discrimination based on protected attributes
2. **Transparency** → Explain how the AI makes decisions
3. **Accountability** → Someone is responsible when AI causes harm
4. **Explainability** → Humans understand the "why" behind predictions

**Who is responsible?**
- Data scientists who train the model
- Engineers who deploy it
- Organizations that use it
- Society that regulates it

---

<!-- _header: "Sub-Lesson 09a — AI Ethics & Bias" -->

# AI's Role in Society

**High-stakes domains:**
- **Hiring** → AI decides who gets a job interview
- **Healthcare** → AI diagnoses diseases
- **Criminal Justice** → AI predicts recidivism
- **Lending** → AI approves loans

**Ethical question:** Should we use AI in these domains? How do we ensure fairness?

---

<!-- _header: "Sub-Lesson 09b — Data Privacy Laws" -->

# Data Privacy Laws Overview

| Law | Protects | Applies To | Key Requirement |
|-----|----------|-----------|-----------------|
| **HIPAA** | Health info (PHI) | Healthcare providers, insurers | Patient consent; breach notification |
| **FERPA** | Student education records | Schools, universities | Parent/student access rights |
| **GDPR** | Personal data of EU residents | Any company processing EU data | Consent; right to be forgotten |
| **PCI DSS** | Payment card data | Card processors, merchants | Encryption; secure storage |

---

<!-- _header: "Sub-Lesson 09b — Data Privacy Laws" -->

# Key Privacy Concepts

**Data Minimization**
→ Collect only what you need

**Consent**
→ Users must agree before data collection

**Right to be Forgotten**
→ People can request data deletion (GDPR)

**Breach Notification**
→ Organizations must tell people if data is stolen

**PHI (Protected Health Information)**
→ Name, DOB, medical record numbers, diagnosis codes

---

<!-- _header: "Sub-Lesson 09b — Data Privacy Laws" -->

# Privacy Laws & AI Systems

**Challenge:** AI systems process sensitive data
- Training data contains PHI, student records, payment info
- Predictions can reveal private information
- Data breaches expose millions

**Your responsibility as developers:**
- Know which laws apply to YOUR data
- Build privacy into the system from the start
- Test for data leaks
- Be transparent about how data is used

---

<!-- _header: "Wrap-Up" -->

# Key Takeaways

1. **AI is not neutral** — It reflects biases in training data
2. **Ethics matter** — Use fairness, transparency, accountability frameworks
3. **Privacy laws exist** — HIPAA, FERPA, GDPR, PCI protect real people
4. **You have power** — As developers, you decide how AI is built and deployed
5. **Think before you code** — Ask: Is this fair? Is this legal? Is this ethical?

---

# Questions?

**Remember:** The AI systems you build will affect real people's lives.
Design with integrity.
