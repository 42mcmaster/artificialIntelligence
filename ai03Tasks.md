# Week 1 Team Project: Decision Tree Application

## Overview

Work with a partner to design and code a decision tree program that solves a real-world problem. This project combines your Python skills with AI decision-making concepts.

**Team Size:** 2 students per team

**Time:** This project should take approximately 2-3 class periods

---

## Project Requirements

Your decision tree program must include:

### Technical Requirements
- [ ] At least **3 user inputs** (questions to gather information)
- [ ] At least **2 levels of nested if statements**
- [ ] At least **4 different possible outcomes/recommendations**
- [ ] Use `.lower()` to handle text input variations
- [ ] Include comments explaining your logic
- [ ] Professional output with clear formatting
- [ ] A header with program title and team members' names

### Documentation Requirements
- [ ] A **flowchart or diagram** of your decision tree (hand-drawn or digital)
- [ ] A **test plan** showing at least 4 different test cases
- [ ] Brief explanation (3-4 sentences) of what problem your program solves

---

## Team Roles

**Both team members should contribute to all aspects**, but you may divide initial responsibilities:

### Role Option 1: Designer
- Sketch the initial decision tree flowchart
- Design the user experience (questions and output messages)
- Plan test cases
- Help debug code

### Role Option 2: Coder
- Write the initial Python code structure
- Implement the if/elif/else logic
- Add input validation
- Help refine flowchart

**Important:** After initial responsibilities, **swap roles** and review each other's work. Both students should understand all parts of the project.

---

## Project Options

Choose ONE of the following projects (or propose your own with teacher approval):

### Option 1: College Major Advisor 🎓
Help students decide what to study based on their interests and skills.

**Factors to consider:**
- Favorite subjects (math/science/arts/humanities)
- Career goals (help people/make things/solve problems/create art)
- Preferred work environment (office/outdoors/lab/remote)

**Sample outcomes:** Engineering, Business, Education, Nursing, Computer Science, Graphic Design, etc.

---

### Option 2: Video Game Recommender 🎮
Recommend games based on player preferences.

**Factors to consider:**
- Gaming platform (PC/Console/Mobile)
- Preferred genre (Action/RPG/Sports/Strategy/Puzzle)
- Time commitment (casual/regular/hardcore)
- Single-player or multiplayer

**Sample outcomes:** Specific game recommendations with reasons why

---

### Option 3: Workout Plan Generator 💪
Create personalized workout recommendations.

**Factors to consider:**
- Fitness goal (lose weight/build muscle/increase endurance/flexibility)
- Experience level (beginner/intermediate/advanced)
- Time available (15min/30min/60min)
- Equipment available (none/basic/full gym)

**Sample outcomes:** Specific workout plans with exercises listed

---

### Option 4: Study Strategy Advisor 📚
Help students develop effective study plans.

**Factors to consider:**
- Subject difficulty (easy/medium/hard)
- Time until test (tonight/few days/week+)
- Study style (visual/auditory/hands-on)
- Current grade (struggling/average/excelling)

**Sample outcomes:** Customized study plans with specific strategies

---

### Option 5: Career Path Explorer 💼
Guide students toward potential careers.

**Factors to consider:**
- Interests (technology/healthcare/education/business/creative)
- Strengths (math/communication/problem-solving/creativity)
- Work-life balance preference (high/moderate/flexible)
- Education plans (college/trade school/straight to work)

**Sample outcomes:** Career suggestions with brief descriptions

---

### Option 6: Recipe Suggester 🍳
Recommend recipes based on available ingredients and preferences.

**Factors to consider:**
- Main ingredient available (chicken/beef/vegetarian/pasta)
- Cooking time (under 15min/30min/60min+)
- Skill level (beginner/intermediate/advanced)
- Meal type (breakfast/lunch/dinner/snack)

**Sample outcomes:** Specific recipes with brief descriptions

---

### Option 7: Pet Adoption Matcher 🐾
Match people with appropriate pets.

**Factors to consider:**
- Living situation (apartment/house with yard)
- Activity level (low/moderate/very active)
- Time available (limited/moderate/lots)
- Experience with pets (none/some/experienced)

**Sample outcomes:** Pet recommendations (specific breeds/types) with care requirements

---

### Option 8: Weekend Activity Planner 🎉
Suggest activities based on conditions and preferences.

**Factors to consider:**
- Weather (sunny/rainy/cold/hot)
- Budget (free/under $20/under $50/no limit)
- Group size (alone/couple/small group/large group)
- Energy level (low/medium/high)

**Sample outcomes:** Specific activity recommendations

---

### Option 9: Phone/Laptop Purchase Advisor 📱💻
Help people decide which device to buy.

**Factors to consider:**
- Budget (under $500/$500-$1000/over $1000)
- Primary use (gaming/work/social media/creative)
- Brand preference (Apple/Android/Windows/no preference)
- Priority (performance/battery/camera/storage)

**Sample outcomes:** Specific device recommendations

---

### Option 10: Your Own Idea! 💡
**Get teacher approval first!**

Your idea must:
- Solve a real problem
- Have at least 3 factors to consider
- Lead to at least 4 different outcomes
- Be school-appropriate

---

## Code Template

```python
"""
Decision Tree Program: [YOUR TITLE]
Team Members: [Name 1] and [Name 2]
Date: [Date]
Description: [Brief description of what this program does]
"""

print("=" * 60)
print("[YOUR PROGRAM TITLE]")
print("=" * 60)
print()

# Gather information (at least 3 inputs)
input1 = input("Question 1: ").lower()
input2 = input("Question 2: ").lower()
input3 = input("Question 3: ")

print()  # Blank line for formatting
print("-" * 60)
print("RECOMMENDATION:")
print("-" * 60)

# Decision tree logic (at least 2 levels of nesting, 4 outcomes)
if condition1:
    if condition2:
        # Outcome 1
        print("Recommendation: [Outcome 1]")
        print("Reason: [Why this recommendation]")
    else:
        if condition3:
            # Outcome 2
            print("Recommendation: [Outcome 2]")
            print("Reason: [Why this recommendation]")
        else:
            # Outcome 3
            print("Recommendation: [Outcome 3]")
            print("Reason: [Why this recommendation]")
else:
    if condition2:
        # Outcome 4
        print("Recommendation: [Outcome 4]")
        print("Reason: [Why this recommendation]")
    else:
        # You can add more outcomes here
        print("Recommendation: [Another outcome]")
        print("Reason: [Why this recommendation]")

print()
print("=" * 60)
print("Thank you for using [Your Program Name]!")
print("=" * 60)
```

---

## Test Plan Template

Create a document with at least 4 test cases:

```
TEST CASE 1: [Describe the scenario]
Input 1: [value]
Input 2: [value]
Input 3: [value]
Expected Output: [What should happen]
Actual Output: [What actually happened]
Pass/Fail: [Circle one]

TEST CASE 2: [Describe different scenario]
Input 1: [value]
Input 2: [value]
Input 3: [value]
Expected Output: [What should happen]
Actual Output: [What actually happened]
Pass/Fail: [Circle one]

[Continue for at least 4 test cases...]
```

**Make sure your test cases cover:**
- Different paths through your decision tree
- Edge cases (extreme values)
- All possible outcomes

---

## Flowchart Requirements

Draw a flowchart showing your decision tree. Include:
- Rectangular boxes for outputs/actions
- Diamond shapes for decisions/questions
- Arrows showing the flow
- Labels on all arrows (YES/NO or specific values)

**Example flowchart structure:**
```
        ┌─────────────┐
        │   START     │
        └──────┬──────┘
               │
        ┌──────▼──────┐
        │ Question 1? │
        └──────┬──────┘
               │
        ┌──────┴──────┐
        │             │
     [YES]           [NO]
        │             │
  ┌─────▼─────┐ ┌────▼────┐
  │Question 2?│ │Question3?│
  └─────┬─────┘ └────┬────┘
  
  [Continue tree structure...]
```

You can draw this:
- By hand (neatly!)
- Using Google Drawings
- Using diagrams.net (free)
- Using any flowchart tool

---

## Submission Checklist

Submit ONE file per team with:

1. **Python file (.py)** with:
   - Header comment with team members and description
   - Working code meeting all requirements
   - Comments explaining key decisions

2. **Documentation** (can be PDF, Google Doc, or printed):
   - Flowchart/diagram of your decision tree
   - Test plan with 4+ test cases
   - Brief explanation of your program (3-4 sentences)

3. **Demo**: Be prepared to demonstrate your program in class

---

## Grading Rubric

| Category | Points | Criteria |
|----------|--------|----------|
| **Code Functionality** | 30 | Program runs without errors, meets all technical requirements |
| **Decision Tree Logic** | 25 | Proper nesting (2+ levels), 4+ outcomes, logical flow |
| **Code Quality** | 15 | Clean code, comments, proper indentation, good variable names |
| **User Experience** | 10 | Clear questions, helpful output, good formatting |
| **Flowchart** | 10 | Accurate diagram showing all paths through decision tree |
| **Test Plan** | 5 | 4+ test cases covering different scenarios |
| **Teamwork** | 5 | Both partners contributed, can explain all code |
| **TOTAL** | **100** | |

---

## Tips for Success

### Planning Phase (15-20 minutes)
1. **Choose your project** together
2. **Brainstorm factors** - what information do you need to ask?
3. **Sketch the flowchart** on paper first
4. **List all possible outcomes** - aim for 4-6
5. **Decide on roles** for initial work

### Coding Phase (1-2 class periods)
1. **Start with the template** above
2. **Write one branch at a time** - test as you go
3. **Add formatting** (lines, emojis, spacing) to make output clear
4. **Test frequently** - don't wait until the end!
5. **Use comments** to explain complex logic
6. **Ask questions** if you get stuck

### Testing Phase (20-30 minutes)
1. **Each partner runs through different test cases**
2. **Try to break your program** - test extreme values
3. **Make sure all 4+ outcomes are reachable**
4. **Fix any bugs** you discover
5. **Clean up formatting** and add final touches

### Documentation Phase (30 minutes)
1. **Create final flowchart** (digital or neatly hand-drawn)
2. **Write up test cases** with actual results
3. **Write program description** (what it does, why it's useful)
4. **Review code** - add any missing comments
5. **Practice your demo** - both partners should be able to explain

---

## Common Pitfalls to Avoid

❌ **Mistake:** One person does all the work
✅ **Solution:** Divide initial tasks, then review together

❌ **Mistake:** Decision tree is too shallow (only 1 level of if statements)
✅ **Solution:** Add nested conditions for more sophisticated decisions

❌ **Mistake:** Forgot to use .lower() on text input
✅ **Solution:** Add .lower() to all text comparisons

❌ **Mistake:** Not testing all paths
✅ **Solution:** Create test plan BEFORE coding, ensure every outcome is tested

❌ **Mistake:** Poor formatting makes output hard to read
✅ **Solution:** Use print("-" * 60), blank lines, and clear labels

❌ **Mistake:** Confusing variable names (x, y, z)
✅ **Solution:** Use descriptive names (budget, genre, difficulty)

---

## Extensions (Optional - Extra Credit)

Want to go beyond the requirements? Try adding:

1. **Input Validation**: Check if inputs are valid before using them
   ```python
   age = input("Enter age: ")
   if not age.isdigit():
       print("Please enter a number!")
   ```

2. **Multiple Recommendations**: Instead of one outcome, suggest top 3 options
   
3. **Scoring System**: Calculate a score and use it to make recommendations
   
4. **Loop to Run Again**: Let users run the program multiple times
   ```python
   again = "yes"
   while again == "yes":
       # Your decision tree code
       again = input("\nRun again? (yes/no): ").lower()
   ```

5. **Save Results**: Write recommendations to a text file

---

## Example: Simple Movie Night Advisor

Here's a complete example for reference (yours should be more complex!):

```python
"""
Movie Night Advisor
Team: Example Team
Helps choose what movie to watch based on mood and time
"""

print("=" * 50)
print("🎬 MOVIE NIGHT ADVISOR")
print("=" * 50)
print()

# Gather information
mood = input("What's your mood? (happy/sad/excited): ").lower()
time = int(input("How much time do you have? (minutes): "))
alone = input("Watching alone? (yes/no): ").lower()

print()
print("-" * 50)
print("RECOMMENDATION:")
print("-" * 50)

# Decision logic
if mood == "happy":
    if time >= 120:
        print("🎭 Watch: The Grand Budapest Hotel")
        print("   Reason: Whimsical and fun, worth the time!")
    else:
        print("🎪 Watch: Paddington 2")
        print("   Reason: Feel-good movie under 2 hours")
elif mood == "sad":
    if alone == "yes":
        print("🌟 Watch: The Pursuit of Happyness")
        print("   Reason: Uplifting story for reflection")
    else:
        print("😂 Watch: a comedy special")
        print("   Reason: Laughter is best with others")
else:  # excited
    if time >= 150:
        print("🎬 Watch: The Dark Knight")
        print("   Reason: Epic action movie!")
    else:
        print("💥 Watch: Mad Max: Fury Road")
        print("   Reason: Non-stop action, shorter runtime")

print()
print("=" * 50)
print("Enjoy your movie! 🍿")
print("=" * 50)
```

---

## Questions?

Ask your teacher if you need help with:
- Choosing a project
- Planning your decision tree logic
- Debugging your code
- Creating your flowchart
- Understanding the requirements

**Remember:** Both team members should understand and be able to explain all parts of the project!

---

## Due Date: [Teacher fills in]

**Submission Method:** [Teacher fills in - Google Classroom, email, etc.]

Good luck, and have fun building your AI decision tree! 🌳🤖