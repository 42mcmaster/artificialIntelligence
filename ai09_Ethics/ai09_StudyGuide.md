# Lesson 09: AI Ethics & Data Privacy — Study Guide

## Vocabulary (~22 terms)

1. **Algorithmic Bias** — Systematic errors in AI predictions caused by biased training data
2. **Training Data Bias** — Historical discrimination embedded in the data used to train models
3. **Fairness** — Ethical principle: AI systems should treat all groups equally
4. **Transparency** — Ethical principle: Users should understand how AI makes decisions
5. **Accountability** — Ethical principle: Someone is responsible when AI causes harm
6. **Explainability** — Ability to explain WHY an AI model made a specific prediction
7. **Self-Fulfilling Prophecy** — AI prediction becomes reality because of how people respond to it
8. **HIPAA** — Health Insurance Portability and Accountability Act (protects health data)
9. **PHI** — Protected Health Information (names, medical records, diagnosis codes)
10. **FERPA** — Family Educational Rights and Privacy Act (protects student records)
11. **GDPR** — General Data Protection Regulation (EU privacy law)
12. **PCI DSS** — Payment Card Industry Data Security Standard (protects credit card data)
13. **Data Minimization** — Collect only the data you actually need
14. **Consent** — User agreement before collecting or using personal data
15. **Right to be Forgotten** — GDPR right to request deletion of personal data
16. **Breach Notification** — Legal requirement to inform people if their data is stolen
17. **Ethical AI** — AI systems designed with fairness, transparency, and accountability
18. **Confidentiality** — Keeping data secret (part of CIA triad)
19. **Integrity** — Ensuring data is accurate and hasn't been tampered with (part of CIA triad)
20. **Availability** — Ensuring data is accessible when needed (part of CIA triad)
21. **Discrimination** — Treating people unfairly based on protected attributes (race, gender, etc.)
22. **AI Ethics** — Field studying the moral implications and societal impact of AI

---

## Privacy Laws Quick Reference

| Law | What It Protects | Who It Applies To | Enacted | Key Requirements |
|-----|------------------|-----------------|--------|-----------------|
| **HIPAA** | Health Information (PHI) | Healthcare providers, insurers, hospital networks | 1996 | Patient consent for data use; breach notification; 60-day notice |
| **FERPA** | Student Education Records | Schools, universities, educational agencies | 1974 | Parent/student access rights; limited disclosure without consent |
| **GDPR** | Personal data of EU residents | Any organization processing EU citizen data | 2018 | Explicit consent; right to be forgotten; privacy by design |
| **PCI DSS** | Payment Card Data | Card processors, merchants, payment networks | 2004 | Encryption; secure transmission; regular audits |

### HIPAA Example
**What counts as PHI?**
- Patient name
- Social Security number
- Date of birth
- Medical record numbers
- Diagnosis codes
- Prescription information

**Violation:** Sharing a patient's diagnosis with an insurance company without consent

### FERPA Example
**What counts as Protected Student Records?**
- Name, SSN, student ID
- GPA, test scores
- Disciplinary records
- Special education information

**Violation:** Posting student grades on a public bulletin board

### GDPR Example
**Key Rights:**
- Right to access your data
- Right to correct errors
- Right to be forgotten (deletion)
- Right to data portability

**Violation:** Keeping someone's data after they request deletion

### PCI DSS Example
**What needs protection?**
- Credit card numbers
- Card verification codes
- Cardholder names
- Card expiration dates

**Violation:** Storing unencrypted credit card numbers in a database

---

## Ethical Analysis Framework

Use these questions to analyze ANY AI system:

### 1. BIAS CHECK
- What data was used to train this model?
- Could the training data contain historical biases?
- Which groups might be affected differently?
- Has the model been tested for fairness across demographics?

### 2. TRANSPARENCY CHECK
- Can users understand how decisions are made?
- Does the company explain the AI's limitations?
- Are there explanations for individual predictions?

### 3. ACCOUNTABILITY CHECK
- Who is responsible if the AI causes harm?
- Is there a human review process?
- Are there appeals mechanisms for incorrect decisions?

### 4. PRIVACY CHECK
- What personal data does this system collect?
- Which privacy laws apply (HIPAA, FERPA, GDPR, PCI)?
- Is user consent obtained?
- Can people request data deletion?

### 5. IMPACT CHECK
- What are the consequences of wrong predictions?
- Who benefits from this AI? Who might be harmed?
- Is this a high-stakes domain (hiring, healthcare, criminal justice)?

---

## Real-World Case Studies

### Case 1: Amazon Hiring AI (2018)
**Problem:** AI trained on 10 years of hiring data. In tech industry, 60% of hires were men.
**What Happened:** AI learned to penalize women's resumes, downranking female applicants.
**Lesson:** Training data bias → AI bias. Diverse data needed.

### Case 2: Healthcare Algorithm (2019)
**Problem:** Algorithm used to allocate healthcare resources. Trained on historical cost data, which reflected healthcare disparities.
**What Happened:** Black patients received lower care recommendations because they historically spent less on healthcare.
**Lesson:** Biased proxy variables create discrimination even without directly considering race.

### Case 3: Facial Recognition
**Problem:** Tested on mostly white faces. Low accuracy (10-40%) on darker-skinned women.
**What Happened:** AI systems misidentified Black women, leading to false arrests.
**Lesson:** Testing requirements and demographic diversity in data are critical.

### Case 4: Predictive Policing
**Problem:** Police use AI to predict high-crime areas. Training data from past arrests (which are biased).
**What Happened:** AI predicts more crime in over-policed neighborhoods, sending more police, creating more arrests.
**Lesson:** Self-fulfilling prophecy — AI prediction becomes reality through human response.

---

## CIA Triad (Security Foundation)

All privacy laws are built on these three principles:

**Confidentiality**
- Keep data secret
- Only authorized people can access it
- Encrypt sensitive information

**Integrity**
- Data must be accurate and complete
- Prevent unauthorized changes
- Detect tampering

**Availability**
- Data must be accessible when authorized users need it
- System must have backups
- Prevent denial of service attacks

---

## ODE Competencies Covered

- **2.14.2** Understand societal impact and ethical implications of AI
- **2.14.6** Critically analyze AI systems for bias, fairness, transparency
- **2.1.1** Apply CIA triad to secure systems
- **2.1.12** Know HIPAA, PCI, FERPA, GDPR requirements
- **1.3.3** Develop ethical character and integrity
- **1.3.8** Understand intellectual property and data protection laws
- **1.4.3** Implement security and privacy best practices

---

## Study Tips

1. **Memorize the acronyms:** HIPAA, FERPA, GDPR, PCI, PHI, CIA
2. **Know the difference:** HIPAA (health) vs. FERPA (education) vs. GDPR (EU residents)
3. **Bias cycle:** Bad data → Biased model → Unfair predictions → Discriminatory outcomes
4. **Privacy vs. Accuracy:** Adding privacy protections sometimes reduces AI accuracy (tradeoff)
5. **Responsibility chain:** Data scientists, engineers, organizations, regulators ALL have roles
6. **Real examples matter:** Be able to explain Amazon, healthcare, facial recognition cases
