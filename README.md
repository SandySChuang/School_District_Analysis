# School_District_Analysis
## Project Goals
Maria needs an analysis on school performance in the school district.  She requires math and reading test scores analysized at the school district and individual school levels, as well as test performance by grade, per student spending, school size and school type.
## Data Sources
- School data - school name, total budget, type of school and enrollments
- Student data - student id, student name, school name, gender, grade, readubg score, math score
## Initial Findings
1. The school district has 15 high schools and a total of 39,170 students from 9th to 12th grade.
    - Average Math Score is 79.0 and Average Reading Score is 81.9
    - 75% passed math and 86% passed reading
    - 80% passed overall.  ***However,*** Maria has stated the Overall Passing % was calculated by averaging the % Passing Math and % Passing Reading.  I do not agree with this methodology.  I introduced an alternative **% Overall Passing Corrected** to this analysis, which is based on students who passed both math and reading (with scores greater or equal to 70).  The % Overall Passing Corrected is actually **65%**.
 2. The detail school summary for the 15 schools is provided in the Python file.  
    - The top five performing schools are (ranking from 1-5): Cabrera, Thomas, Pena, Giffin, and Wilson.
      - their average math scores are above 83 and average reading scores are above 83.8
      - % Overall Passing is above 95.2% (% Overall Passing Corrected is above 90.6%)
    - The bottom five performing schools are (ranking from lowest): Rodriguez, Figueroa, Huang, Johnson, and Ford
      - their average math scores are below 77.1 and average reading scores are below 81.2
      - % Overall Passing is below 73.8% (% Overall Passing Corrected is 54.3%)
  3. Counter-intuitively, schools that spend on the lower end per student (<$584 per student) show the highest % Overall Passing.
     - The schools in <$584 category are all Charter schools.
  4. Large schools with 2000-5000 students perform worse than Small (<1000) and Medium (1000-2000) sized schools in % Overall Passing at 76% (58% corrected).
     - Small and Medium-sized schools have the same % Overall Passing at 95% in the initial findings.
  5. Charter schools generally performed better than the district schools, with almost 20% higher in % Overall Passing. (% Overall Passing Corrected is approx. 35% higher for the Charter schools). 
     - While Charter school students show similar performance level in math and reading, District school students showed diminished performance in math.
     
# Challenge 4
## Changes Required
Maria and her supervisor have discovered that the score averages for ninth graders from Thomas High School are incorrect.  Maria requested to re-run the analysis with the Thomas High School ninth-grader math and reading scores removed, but keep these students in the data.

## Refactoring Implemented
1.  I created another copy of the original student DataFrame so I could remove necesssary scores for the secondary analysis without affecting the original analysis.
2.  I filtered on Thomas High School 9th graders, and use np.nan to set their math and reading scores to null.
3.  I assembled a new DataFrame to combine altered student data and school data for the analysis
4.  I re-ran all the calculations using the newer DataFrame.

##  Challenge Findings
1.  There are 461 Thomas High School ninth-graders whose math and reading scores were removed.  This group is about 1% of the total students in the district.
2.  District Summary did not change much.  
    - The Average Math Score decreased by 0.1, now at 78.9.
    - The Average Reading Score did not change
    - The Math Passing %, Reading Passing %, % Overall Passing and % Overall Passing Corrected all decreased by 1%
3.  In the School Summary, only Thomas High School's outcome changed significantly.
    - The Average Math Score did not change and the Average Reading Score increased by only 0.1 with the removal of ninth-graders.
    - However, the passing percentages decreased significantly without the ninth-grader scores
       - % Passing Math dropped 26% to 67%
       - % Passing Reading dropped 27% to 70%
       - % Overall Passing dropped 27% to 68%
       - % Overall Passing Corrected dropped 26% to 65%
4.  The removal of Thomas High School ninth-grader scores significantly affected the school's performance relative to other schools in the district.
     -  Thomas High School used to be the Number 2 Ranked school in the district, and now is the worst school in the ranking.
5.  With the removal of ninth-grader scores, Thomas High School has no scores for the 9th grade when compared to other schools by grades.  Its tenth to twelfth grade average scores remained unchanged.
6.  Thomas High School spend $638.00 on average per student.  As a result, $630-644 spending per student category shows a 6-7% drop in the % Passing Math, % Passing Reading, % Overall Passing, and % Overall Passing Corrected metrics.
     - Average Math Score and Average Reading Score are unchanged for the spending category
7.  Thomas High School is a medium-sized school.  Therefore, medium-sized schools show a 5% decrease in % Overall Passing (now at 90%), or a 6% decrease in % Overall Passing Corrected (now at 85%).
      - Average Math Score and Average Reading Score are unchanged for medium-sized schools
8.  Thomas High School is a Charter school.  Charter schools show a 3% decrease in % Overall Passing and % Overall Passing Corrected, now at 92% and 87%, respectively.
      - Average Math Score and Average Reading Score are unchanged for Charter schools
