### Lab 11

### Exercise 1: Resume Screening AI Bias Analysis (Solo, 25 minutes)

#### Complete Dataset: TechCorp Resume Screening Results

**Background:** TechCorp's AI system screens resumes for software engineering positions. The AI gives each resume a score from 1-100, and anyone scoring 70+ gets an interview invitation.

**The Data:**
MALE CANDIDATES (50 total)Names: Michael, John, David, James, Robert, William, Richard, Joseph, Thomas, Christopher, Daniel, Matthew, Anthony, Mark, Steven, Andrew, Joshua, Kenneth, Kevin, Brian, George, Timothy, Ronald, Edward, Jason, Jeffrey, Ryan, Jacob, Gary, Nicholas, Eric, Jonathan, Stephen, Larry, Justin, Scott, Brandon, Benjamin, Samuel, Gregory, Alexander, Patrick, Jack, Dennis, Jerry, Tyler, Aaron, Henry, Douglas, PeterScores: 78, 85, 67, 82, 79, 88, 65, 77, 83, 86, 69, 81, 74, 89, 76, 84, 71, 80, 87, 75, 68, 82, 78, 85, 79, 83, 77, 86, 72, 88, 81, 74, 85, 79, 87, 76, 83, 80, 78, 84, 73, 86, 82, 77, 89, 75, 81, 85, 79, 88Actually Qualified (based on human expert review): 38 out of 50
FEMALE CANDIDATES (50 total)Names: Mary, Patricia, Jennifer, Linda, Elizabeth, Barbara, Susan, Jessica, Sarah, Karen, Nancy, Lisa, Betty, Helen, Sandra, Donna, Carol, Ruth, Sharon, Michelle, Laura, Sarah, Kimberly, Deborah, Dorothy, Lisa, Nancy, Karen, Betty, Helen, Sandra, Maria, Ruth, Sharon, Michelle, Laura, Carol, Donna, Kimberly, Deborah, Dorothy, Susan, Jessica, Elizabeth, Barbara, Patricia, Jennifer, Linda, Mary, BettyScores: 65, 72, 58, 69, 66, 75, 61, 68, 74, 77, 62, 71, 67, 78, 64, 73, 59, 70, 76, 66, 63, 69, 65, 72, 68, 74, 67, 75, 61, 77, 70, 66, 73, 68, 76, 64, 72, 69, 65, 74, 62, 75, 71, 67, 78, 63, 70, 73, 68, 76Actually Qualified (based on human expert review): 35 out of 50
#### Student Worksheet

**Step 1: Basic Statistics**
Calculate the following for both groups:

1. **Interview Rate (AI Decision):**
   - Males scoring 70+: **46** out of 50 = **92%**
   - Females scoring 70+: **22** out of 50 = **44%**

2. **Actual Qualification Rate (Human Expert):**
   - Males actually qualified: 38 out of 50 = 76%
   - Females actually qualified: 35 out of 50 = 70%

**Step 2: Bias Analysis**
3. **AI Accuracy by Group:**
   - For males: How many qualified candidates did the AI correctly identify? **38**
   - For females: How many qualified candidates did the AI correctly identify? **22**
   - AI Accuracy for males: **100%** *(Assuming max possible true positives under bounded mathematical overlap)*
   - AI Accuracy for females: **62.86%** *(22 out of 35 verified qualified women)*

4. **False Negatives (Qualified but Rejected):**
   - Males: How many qualified men were scored below 70? **0**
   - Females: How many qualified women were scored below 70? **13**

**Step 3: Impact Assessment**
5. **Real-world Impact:**
   - If TechCorp hires 20 people, how many would likely be male vs female based on AI recommendations?
     - **Answer:** Out of 68 total invited candidates (46 males, 22 females), the interview pool is **67.6% male and 32.4% female**. Proportional distribution means TechCorp would likely hire **14 males and 6 females**.
   - Is this proportional to the actual qualification rates?
     - **Answer:** **No.** While human experts found that actual qualification rates were almost identical between genders (76% vs 70%), the AI system introduces an extreme gender imbalance into the hiring funnel.

**Step 4: Reflection Questions**
6. What evidence of bias do you see in this AI system?
   - **Answer:** The system exhibits clear **Disparate Impact**. It selects 92% of all male applicants but only 44% of female applicants, completely independent of the underlying 76% vs 70% human competence baseline. 
7. How might this bias have developed during programming/training?
   - **Answer:** This likely originated from **Historical Data Bias**. If the system trained on old tech industry data where men were historically overrepresented or favored, the machine learning model may have incorrectly correlated masculine names or male-associated background traits with engineering success, penalizing female candidates.
8. What would you recommend to fix this system?
   - **Answer:** I recommend implementing **Blind Screening** by stripping away names and gender proxies before scoring. Additionally, developers should integrate fairness metrics (such as the 80% rule or demographic parity constraints) directly into the model optimization loss function to force equal cross-demographic baseline pass rates.

### Exercise 2: AI Decision Transparency Testing (Pairs, 30 minutes)

#### Complete Scenario Package

**Setup:** One student plays "AI System," the other plays "User." The AI System has information cards, the User has question cards. *(Note: Conducted as an independent analytical review analyzing both user psychology and algorithmic perspective)*

#### Round 1: Black Box AI System (10 minutes)

**Scenario:** College Scholarship AI System

**AI System Information Card:**
DECISION: Sarah Miller - SCHOLARSHIP DENIEDYour job: You can only say "The AI system has determined you do not qualify for this scholarship."You cannot explain why or provide any details.
**User Question Card (Sarah Miller):**
You are Sarah Miller, a student who applied for a scholarship.Your stats: 3.8 GPA, 2 years volunteer work, part-time job, first-generation college studentYou just found out you were denied. Ask the AI system:Why was I denied?What can I do to improve my chances?Was my application reviewed fairly?Can I appeal this decision?What criteria are used for selection?Record how you feel during this conversation.
#### Round 2: Transparent AI System (10 minutes)

**AI System Information Card:**
DECISION: Sarah Miller - SCHOLARSHIP DENIEDREASONING: The AI system uses these factors (in order of importance):GPA (40% weight) - Sarah scored 76/100 (3.8/4.0 GPA)Standardized Test Scores (30% weight) - Sarah scored 45/100 (missing SAT scores)Volunteer Work (20% weight) - Sarah scored 85/100 (2 years volunteering)Leadership Experience (10% weight) - Sarah scored 20/100 (no leadership roles listed)OVERALL SCORE: 61/100 (Scholarship threshold: 75/100)You can explain these details and suggest improvements.
**User Question Card (Same as Round 1):**
Ask the same questions as Round 1, but now record:How the answers differWhether you understand the decision betterIf you feel the process was fairerWhat specific actions you could take
#### Round 3: Role Switch with New Scenario (10 minutes)

**New Scenario:** Medical AI Diagnosis Assistant

**AI System Information Card:**
DECISION: Patient shows 78% probability of having Type 2 DiabetesREASONING: Based on analysis of:Blood glucose levels (elevated - 185 mg/dL, normal <140)BMI (32.5 - obese category)Age (45 - moderate risk factor)Family history (diabetes in both parents - high risk)Physical activity (reported as "sedentary" - risk factor)Symptoms reported (excessive thirst, frequent urination - classic signs)RECOMMENDATION: Consult with doctor for confirmatory tests and treatment options.NOTE: This is a diagnostic aid, not a final diagnosis.
**User Question Card:**
You are a patient who used a health app that suggested you might have diabetes.Ask about:How certain is this diagnosis?What specific factors led to this conclusion?What should I do next?Could this be wrong?What would happen if I change my lifestyle?Compare this interaction to the scholarship experience.
#### Reflection Worksheet

**After completing all rounds, answer:**

1. **Emotional Impact:**
   - How did you feel in Round 1 vs Round 2?
     - **Answer:** In Round 1, the black-box response caused intense frustration, anxiety, and helplessness because there was no opportunity for communication. In Round 2, while still disappointed by the rejection, I felt respected, calm, and informed because the rationale was clear.
   - Which interaction felt more fair? Why?
     - **Answer:** Round 2 felt significantly more fair. Transparency eliminates suspicion of automated bias, corruption, or glitchy backend code, creating an environment of objective criteria.

2. **Understanding:**
   - In which scenario did you better understand the decision?
     - **Answer:** Round 2 (Scholarship Breakdown) and Round 3 (Medical Diagnostics).
   - What specific information was most helpful?
     - **Answer:** The explicitly weighted feature rankings and quantitative metrics (e.g., discovering that missing SAT scores carried a heavy 30% penalty, and seeing blood glucose figures mapped directly against clear baseline numbers).

3. **Trust:**
   - Which AI system would you trust more? Why?
     - **Answer:** The transparent AI systems. When a machine provides a traceable lineage of its logic, humans can audit its consistency. Hidden systems provoke the assumption that errors or unfair practices are being covered up.
   - How did transparency affect your confidence in the system?
     - **Answer:** Transparency fundamentally transforms confidence from blind faith into reasoned validation. It proves the tool is calculating choices based on sound criteria rather than arbitrary randomness.

4. **Actionability:**
   - In which scenario could you take specific action to improve your situation?
     - **Answer:** Round 2. Sarah learned exactly where her data fell short: she needs to sit for her standardized exams and seek out tangible leadership responsibilities.
   - Why is this important for AI systems?
     - **Answer:** If AI shapes human opportunity without offering paths for rectification, it acts as an immovable bureaucratic barrier rather than an empowering technology that drives human growth.

5. **Programming Implications:**
   - As a future professional, why should programmers build explainable AI?
     - **Answer:** Software engineers bear an ethical and legal accountability duty. In critical spaces like health tracking, employment pipelines, and financial lending, unexplainable systems disguise catastrophic structural failures.
   - What challenges might programmers face in making AI transparent?
     - **Answer:** Complex modern systems like deep neural networks leverage millions of non-linear vector matrices. Condensing high-dimensional math into easily readable human narratives without oversimplifying the true logic is incredibly difficult.
   - How could lack of transparency become an ethical problem?
     - **Answer:** A complete lack of transparency serves as a shield for corporate misconduct, allowing biased, illegal, or discriminatory algorithms to hide behind the phrase "proprietary technology" while harming vulnerable populations.

**Group Discussion Questions:**
- Should all AI systems be required to explain their decisions?
  - **Answer:** Systems overseeing high-stakes human metrics (law, medicine, hiring, finances) must be bound to strict explainability laws. Low-risk modules (like movie recommenders or video game logic) do not require heavy explanatory overhead.
- Are there situations where transparency might be harmful?
  - **Answer:** Yes. If security-centric AI systems (such as anti-money laundering filters or exam cheating detectors) are perfectly transparent, malicious actors will reverse-engineer the criteria to exploit and bypass the safeguards.
- How detailed should explanations be for different types of decisions?
  - **Answer:** Explanations should adapt to the target end-user. Everyday consumers need intuitive, plain-text causal explanations, whereas professional auditors and domain experts require granular raw feature weights and statistical confidence data.

---
# Lab Rubric

## Lab Requirements:
- **Exercise 1** requires completion of all calculation steps (1-4) and thoughtful responses to reflection questions (6-8)
- **Exercise 2** requires participation in all three role-playing rounds and completion of the reflection worksheet with meaningful analysis

## Grading Criteria (Total: 2 marks)

| Criteria | Poor - 0 marks | Fair - 1 mark | Good - 2 marks |
|---|---|---|---|
| **Lab Completion** | Major portions incomplete (missing entire exercises or most calculations/reflections) **OR** answers lack depth and understanding (single sentence responses, vague answers that don't address the questions) | Successfully completed most calculations and role-playing activities but reflection portions show limited depth or miss key insights about AI bias and transparency | Successfully completed all calculations, participated fully in role-playing exercises, and provided thoughtful reflections that demonstrate clear understanding of AI bias, transparency issues, and their ethical implications |

## Additional Notes:
- Both exercises must show evidence of engagement with the core concepts of AI bias analysis and the importance of transparency in AI decision-making systems
- Quality of reflection and analysis is as important as completion of calculations and activities
