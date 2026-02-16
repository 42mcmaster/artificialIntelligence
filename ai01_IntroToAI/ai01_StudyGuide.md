# AI Lesson 01: Study Guide
## Introduction to Artificial Intelligence

---

## Vocabulary & Key Terms

### Core AI Concepts

1. **Artificial Intelligence (AI)** - Computer systems that perform tasks typically requiring human intelligence (recognition, reasoning, recommendations)

2. **Traditional Programming** - Writing explicit rules for a computer to follow; programmer specifies exact instructions for every scenario

3. **Rule-Based System** - A system where a programmer writes all the if/then rules explicitly; does NOT learn from data (NOT AI)

4. **Machine Learning (ML)** - AI approach where the computer learns patterns from labeled examples instead of following programmed rules

5. **Supervised Learning** - Training where AI learns from labeled examples (input-output pairs)

### Types of Machine Learning

6. **Regression** - ML approach that predicts continuous numerical values (like prices, temperatures, distances)

7. **Linear Regression** - Finds the best straight line through data points to make predictions

8. **Polynomial Regression** - Uses curved lines to capture complex patterns in numerical data

9. **Classification** - ML approach that predicts categories or labels (like spam/not spam, cat/dog/bird)

10. **Logistic Regression** - Classification method that calculates probability of each category

11. **Decision Trees (Learned)** - AI automatically creates if/then rules by analyzing data (NOT hard-coded)

12. **Random Forest** - Multiple decision trees that vote together to make a prediction

13. **Support Vector Machines (SVM)** - Finds the best boundary line/surface separating different categories

14. **Neural Networks** - Multi-layered system inspired by the brain; learns very complex patterns

15. **Deep Learning** - Neural networks with many layers that can learn abstract patterns

### Important Distinctions

16. **Hard-Coded Decision Trees** - Programmer writes all the rules explicitly (NOT AI, same as traditional programming)

17. **Pattern Recognition** - Identifying similarities and relationships in data (what ML does)

18. **Feature** - An input variable or characteristic used to make a prediction

19. **Label** - The output or target value in supervised learning (what we're trying to predict)

20. **Training Data** - Examples used to teach an AI model

---

## Quick Reference: The Three Approaches

### Approach 1: Traditional Programming
- **Who writes rules?** Human programmer
- **Learns automatically?** No
- **Uses data?** No
- **Example:** Calculator, form validation
- **IS THIS AI?** No

### Approach 2: Rule-Based AI (Expert Systems)
- **Who writes rules?** Human experts encode knowledge
- **Learns automatically?** No
- **Uses data?** No
- **Example:** Medical diagnosis checklist (1980s)
- **IS THIS AI?** No (it's a precursor)

### Approach 3: Machine Learning (TRUE AI)
- **Who writes rules?** Algorithm learns from data
- **Learns automatically?** Yes
- **Uses data?** Yes
- **Example:** Netflix recommendations, spam detection
- **IS THIS AI?** Yes!

---

## Regression vs Classification

### When to Use REGRESSION
- You need to predict a **number**
- Output is continuous (not categories)
- Examples:
  - Predicting house prices
  - Forecasting temperature
  - Estimating car mileage
  - Predicting stock prices

### When to Use CLASSIFICATION
- You need to predict a **category/label**
- Output is one of several choices
- Examples:
  - Is this email spam? (Yes/No)
  - What animal is in this photo? (Cat/Dog/Bird)
  - Will this student pass? (Yes/No)
  - Is this review positive? (Positive/Negative)

---

## Real-World AI Examples

| Technology | What it does | ML Type | Rule-based? |
|------------|------------|---------|-------------|
| **Netflix** | Recommends shows | Classification | No - it learns! |
| **Snapchat Filters** | Recognizes faces | Neural Network | No - it learns! |
| **Google Translate** | Translates languages | Neural Network | No - it learns! |
| **Siri/Alexa** | Understands speech | Neural Network | No - it learns! |
| **Spam Filter** | Detects spam emails | Classification | No - it learns! |
| **YouTube Recommendations** | Suggests videos | Classification | No - it learns! |
| **Thermostat** | Controls temperature | Rule-based | Yes - hard-coded |

---

## Common Misconceptions

### MYTH: AI is magic
**Truth:** AI is mathematics and pattern recognition. It discovers relationships in data.

### MYTH: AI is always smart
**Truth:** AI makes mistakes. It can only work with the data it was trained on.

### MYTH: AI understands like humans
**Truth:** AI recognizes patterns. It doesn't have consciousness or true understanding.

### MYTH: AI can do anything
**Truth:** AI is specialized. A face-detection AI can't translate languages without retraining.

---

## ODE Competencies Covered

**Standard 2.14 - Artificial Intelligence & Machine Learning**
- **2.14.1** Define artificial intelligence and explain the difference between AI and traditional programming
- **2.14.5** Identify and classify different types of machine learning approaches

**Standard 2.4 - Information & Computer Science**
- **2.4.1** Understand how computers process and learn from data
- **2.4.2** Apply programming concepts to solve problems
- **2.4.3** Analyze computer systems and their applications
- **2.4.4** Evaluate the impact of technology on society

---

## Study Questions

### Knowledge Level
1. What is the main difference between traditional programming and AI?
2. Why is a thermostat (if/else rules) NOT AI?
3. Give 3 examples of AI you use daily.
4. What is supervised learning?

### Application Level
5. If you need to predict a house price, would you use regression or classification? Why?
6. If you need to detect if a fruit is ripe or not, would you use regression or classification? Why?
7. Could you solve a spam filter with traditional programming? What would be the problems?

### Analysis Level
8. Why is machine learning better than traditional programming for Netflix recommendations?
9. Compare hard-coded decision trees with decision trees learned from data.
10. Why do neural networks work better than other methods for image recognition?

---

## Key Concepts to Master

Before moving on, you should understand:

- [ ] The difference between traditional programming (rules written by humans) and AI (patterns learned from data)
- [ ] Why rule-based systems are NOT true AI
- [ ] The difference between regression (predicting numbers) and classification (predicting categories)
- [ ] Real-world examples of each ML type
- [ ] Why different problems need different approaches
- [ ] That AI is not magic—it's math, patterns, and training data

---

## Practice Scenarios

### Scenario 1: Predicting Student Grades
- **Goal:** Predict a student's final grade (A, B, C, D, F)
- **Type:** Classification (predicting a category)
- **Features:** Hours studied, attendance, past grades, test scores
- **Why not traditional?** Too many rules to write; patterns change per student

### Scenario 2: Predicting House Prices
- **Goal:** Predict the sale price of a house
- **Type:** Regression (predicting a number)
- **Features:** Square footage, location, age, bathrooms, condition
- **Why not traditional?** Relationships are complex; prices vary by location

### Scenario 3: Identifying Cats in Photos
- **Goal:** Detect if a photo contains a cat
- **Type:** Classification (cat/not cat)
- **ML Type:** Neural Network
- **Why not traditional?** Impossible to write rules for all cat variations!

### Scenario 4: Email Spam Detection
- **Goal:** Is this email spam or legitimate?
- **Type:** Classification (spam/not spam)
- **ML Type:** Logistic Regression or Decision Tree
- **Why not traditional?** Spam changes constantly; spam filters must adapt

---

## Quick Self-Check

**Can you answer these without looking?**

1. What does "supervised learning" mean?
2. What's the difference between regression and classification?
3. Give 2 examples of classification problems.
4. Give 2 examples of regression problems.
5. Why is machine learning better than hard-coded rules for detecting faces?
6. What are three real-world AI applications you use?

---

## Challenge Questions

**Stretch your thinking:**

1. Could you use regression for spam detection? Why or why not?
2. Is a GPS navigation system traditional programming or AI? Explain.
3. Could machine learning help improve a calculator? Why or why not?
4. If Netflix didn't have any training data, could they recommend shows?
5. What would happen if a spam filter was trained only on old spam?

---

## Resources & Next Steps

**What's Next in This Unit:**
- Lesson 01a: Deep dive into traditional vs AI programming with code examples
- Lesson 01b: Types of machine learning and when to use each

**Focus Areas for Practice:**
- Identifying real-world AI vs traditional programming
- Classifying problems as regression or classification
- Understanding why AI learns better than hard-coded rules

---

## Notes Section

Use this space to write your own notes from class:

---

(Add your own observations, questions, and connections here!)

---

**Last Updated:** February 2026
**Teacher:** Ryan McMaster, Medina County Career Center
**ODE Standards:** 2.14.1, 2.14.5, 2.4.1-2.4.4
