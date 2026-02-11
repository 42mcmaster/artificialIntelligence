# Lesson 09: AI Ethics & Data Privacy

**Course:** Applications of Artificial Intelligence (ODE 145130)
**Teacher:** Ryan McMaster
**Medina County Career Center**
**Final Lesson in the AI Course**

---

## Quick Start Guide

### For Teachers

1. **Start with the Slides** (`ai09_Slides.md`)
   - 10 MARP slides covering both sub-lessons
   - Use in classroom presentation
   - Takes 45-60 minutes

2. **Use the Study Guide** (`ai09_StudyGuide.md`)
   - Distribute to students
   - 22 vocabulary terms with definitions
   - Quick reference tables for all laws
   - Study tips for exam prep

3. **Work Through the Walkthrough** (`ai09_Walkthrough.ipynb` + Solutions)
   - Teaches concepts with real-world examples
   - Discussion prompts for engagement
   - Use instructor solutions for reference

4. **Assign Tasks**
   - Task 09a: Bias case study analysis
   - Task 09b: Privacy law scenarios
   - DIY Task: Independent AI impact analysis

5. **Assessment**
   - Use Gimkit (30 practice questions)
   - Give Unit 3 End-of-Unit Quiz (40 questions)

---

## File Structure

### Instructional Content (Students use these)
- `ai09_Slides.md` - Presentation slides
- `ai09_StudyGuide.md` - Study reference guide
- `ai09_Walkthrough.ipynb` - Tutorial with discussion blanks
- `ai09a_Task.ipynb` - Bias case study analysis (student version)
- `ai09b_Task.ipynb` - Privacy scenarios (student version)
- `ai09_DIYTask.ipynb` - Independent analysis (student version)

### Instructor Resources (Answer keys)
- `ai09_Walkthrough_Solutions.ipynb` - Complete walkthrough answers
- `ai09a_Task_Solutions.ipynb` - Case study solutions + grading rubric
- `ai09b_Task_Solutions.ipynb` - Privacy scenario solutions + remediation
- `ai09_DIYTask_Solutions.ipynb` - Example DIY analysis (ChatGPT case)

### Assessment Tools (Ready to use)
- `ai09_Gimkit.csv` - 30 practice questions (import to Gimkit)
- `Unit3_EndOfUnit_GoogleQuiz.csv` - 40-question end-of-unit exam

---

## Learning Objectives

Students will be able to:

**Sub-Lesson 09a: AI Ethics & Bias**
- Explain sources of algorithmic bias
- Analyze real-world bias cases (Amazon, healthcare, facial recognition, predictive policing)
- Apply ethical frameworks (fairness, transparency, accountability, explainability)
- Identify high-stakes domains requiring special care
- Understand responsibility for AI harms

**Sub-Lesson 09b: Data Privacy Laws**
- Distinguish between HIPAA, FERPA, GDPR, and PCI DSS
- Identify Protected Health Information (PHI) and sensitive data
- Apply data privacy principles (minimization, consent, right to deletion)
- Evaluate scenarios for compliance/violations
- Understand consequences of privacy breaches

**Cross-cutting**
- Apply the CIA triad (Confidentiality, Integrity, Availability)
- Think critically about real-world AI systems
- Connect technical skills to ethical responsibility

---

## Lesson Pacing

**Total: 2-3 class periods (90-135 minutes)**

**Day 1: Ethics & Bias (45 minutes)**
- Slides presentation (15 min)
- Walkthrough case studies (20 min)
- Discussion (10 min)

**Day 2: Privacy Laws (45 minutes)**
- Slides review (5 min)
- Walkthrough privacy section (20 min)
- Scenario discussion (20 min)

**Day 3: Student Work & Practice (45 minutes)**
- Task 09a (Bias analysis) - 20 min
- Task 09b (Privacy scenarios) - 20 min
- Gimkit practice - 5 min
- OR assign DIY task for homework

---

## Assessment

### Formative
- Discussion questions in walkthrough
- Task 09a: Case study analysis (4 cases, 6 questions each)
- Task 09b: Privacy scenarios (5 scenarios, 4 questions each)
- Gimkit practice quiz (30 questions)

### Summative
- **Unit 3 End-of-Unit Quiz** (40 questions)
  - 70% from lessons 08-09 (neural networks, ethics, privacy)
  - 30% from lessons 06-07 (prompt engineering, regression, decision trees)
  - Multiple choice format
  - Ready for Google Forms/Canvas/Quizizz

### Advanced
- DIY Task: Independent analysis of a real AI system
- Students choose their own AI (ChatGPT, facial recognition, recommendations, etc.)
- Analyze for bias, privacy, and ethical issues
- Propose safeguards

---

## Key Concepts at a Glance

### Bias in AI
- **Source:** Biased training data
- **Examples:** Amazon (gender), healthcare (race proxy), facial recognition (skin tone), police (arrest records)
- **Prevention:** Diverse data, fairness testing, ethical review, diverse teams

### Ethics Framework (FTAE)
- **Fairness:** Equal treatment across groups
- **Transparency:** Users understand how AI works
- **Accountability:** Someone responsible for harms
- **Explainability:** Understand why decisions made

### Privacy Laws
| Law | Protects | Applies To | Key Requirement |
|-----|----------|-----------|-----------------|
| HIPAA | Health info (PHI) | Hospitals, insurers | Consent + breach notification |
| FERPA | Student records | Schools, universities | Parent/student access rights |
| GDPR | EU resident data | Any company + EU users | Consent + right to deletion |
| PCI DSS | Payment cards | Processors, merchants | Encryption + secure storage |

### Privacy Principles
- **Data minimization:** Collect only what you need
- **Consent:** Users must agree
- **Right to deletion:** Can request data removal
- **Breach notification:** Must tell people if data stolen
- **CIA Triad:** Confidentiality, Integrity, Availability

---

## Common Student Questions

**Q: Is AI inherently biased?**
A: No. But biased *data* creates biased AI. The model learns patterns from training data, including discrimination.

**Q: If the algorithm never explicitly uses race, how is it racist?**
A: Proxy variables. Using correlated data (healthcare cost, ZIP code, name) can produce racial discrimination without explicitly mentioning race. This is called "disparate impact."

**Q: Can we fix bias by adding more data?**
A: Only if the data is less biased. More of the same biased data just amplifies the problem.

**Q: Which privacy law should I use?**
A: Depends on the data:
- Health info → HIPAA
- Student records → FERPA
- EU residents → GDPR
- Credit cards → PCI DSS

**Q: What's the difference between fairness and accuracy?**
A: Accuracy = overall correct predictions. Fairness = equal treatment/error rates across groups. You can have high accuracy but low fairness.

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

## Tips for Teaching

1. **Use real examples:** Students care more about actual harms than hypothetical cases
2. **Invite debate:** Ethics isn't black-and-white. Discuss different perspectives
3. **Make it personal:** Ask, "What if this AI affected you or someone you care about?"
4. **Connect to careers:** This is where CS students add value beyond coding
5. **Guest speakers:** If possible, invite practitioners (ethicist, privacy officer, security professional)
6. **Student-chosen AI:** Let students pick systems they use (TikTok, ChatGPT, Instagram)

---

## Next Steps After This Lesson

- Students complete project portfolio
- Reflective essay: "What does ethical AI mean to me?"
- Group presentation on chosen AI system
- Final exam includes end-of-unit quiz
- Graduation! (This is the last lesson)

---

## Additional Resources

**For Teachers:**
- OpenAI GPT-4 technical report (arxiv.org) - bias discussion
- "Weapons of Math Destruction" by Cathy O'Neill
- MIT Case Studies in Ethical AI
- Stanford AI Index Report

**For Students:**
- ProPublica investigative journalism on AI
- TED talks on AI ethics
- GDPR official text (simplified versions available)
- MIT's online "AI Ethics" course

---

## File Locations

All files in: `/sessions/nice-great-feynman/mnt/artificialIntelligenceForGitHub/ai09_Ethics/`

Download and use all 12 files:
1. ai09_Slides.md
2. ai09_StudyGuide.md
3. ai09_Walkthrough.ipynb
4. ai09_Walkthrough_Solutions.ipynb
5. ai09a_Task.ipynb
6. ai09a_Task_Solutions.ipynb
7. ai09b_Task.ipynb
8. ai09b_Task_Solutions.ipynb
9. ai09_DIYTask.ipynb
10. ai09_DIYTask_Solutions.ipynb
11. ai09_Gimkit.csv
12. Unit3_EndOfUnit_GoogleQuiz.csv

---

**Good luck! This is an important conversation to have with students.** — Your Curriculum Team
