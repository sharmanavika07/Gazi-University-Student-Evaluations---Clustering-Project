# Gazi-University-Student-Evaluations---Clustering-Project
A clustering project to visualize and analyze how a university performed according to student evaluations. A breakdown to analyze how students evaluated instructors and courses.

# Problem Description:
5860 students of Gazi Univeristy are asked to rate 28 Questions on Instructor performance, Course content, Grading Methods etc.
Students can rate for every question from 1 to 5, 1 is the lowest rating while 5 is the highest rating.
The aim is to segment the data into groups to know how differently students reveiwed for all the questions.

# Data Description:
1) There are 5820 rows with 33  numerical features which are ordinal or simply discrete.
2) instr: Instructor's identifier; values taken from {1,2,3}
3) class: Course code (descriptor); values taken from {1-13}
4) repeat: Number of times the student is taking this course; values taken from {0,1,2,3,...}
5) attendance: Code of the level of attendance; values from {0, 1, 2, 3, 4}
6) difficulty: Level of difficulty of the course as perceived by the student; values taken from {1,2,3,4,5}
7) Q1: The semester course content, teaching method and evaluation system were provided at the start.
8) Q2: The course aims and objectives were clearly stated at the beginning of the period.
9) Q3: The course was worth the amount of credit assigned to it.
10) Q4: The course was taught according to the syllabus announced on the first day of class.
11) Q5: The class discussions, homework assignments, applications and studies were satisfactory.
12) Q6: The textbook and other courses resources were sufficient and up to date.
13) Q7: The course allowed field work, applications, laboratory, discussion and other studies.
14) Q8: The quizzes, assignments, projects and exams contributed to helping the learning.
15) Q9: I greatly enjoyed the class and was eager to actively participate during the lectures.
16) Q10: My initial expectations about the course were met at the end of the period or year.
17) Q11: The course was relevant and beneficial to my professional development.
18) Q12: The course helped me look at life and the world with a new perspective.
19) Q13: The Instructor's knowledge was relevant and up to date.
20) Q14: The Instructor came prepared for classes.
21) Q15: The Instructor taught in accordance with the announced lesson plan.
22) Q16: The Instructor was committed to the course and was understandable.
23) Q17: The Instructor arrived on time for classes.
24) Q18: The Instructor has a smooth and easy to follow delivery/speech.
25) Q19: The Instructor made effective use of class hours.
26) Q20: The Instructor explained the course and was eager to be helpful to students.
27) Q21: The Instructor demonstrated a positive approach to students.
28) Q22: The Instructor was open and respectful of the views of students about the course.
29) Q23: The Instructor encouraged participation in the course.
30) Q24: The Instructor gave relevant homework assignments/projects, and helped/guided students.
31) Q25: The Instructor responded to questions about the course inside and outside of the course.
32) Q26: The Instructor's evaluation system (midterm and final questions, projects, assignments, etc.) effectively measured the course objectives.
33) Q27: The Instructor provided solutions to exams and discussed them with students.
34) Q28: The Instructor treated all students in a right and objective manner.

**Q1-Q28 are all Likert-type, meaning that the values are taken from {1,2,3,4,5}**

# Approach to our Problem:
1) Figure which variables are categorical or numerical.
2) We remove instructor code and course code since they are categorical variables, and we assume they won't be a deciding factor for clustering, as we only want to cluster on the ratings the students gave.
3) We plot a heatmap to check for multicollinearity, as there are a lot of features.
4) Since there is a strong presence of multicollinearity, we will be applying PCA to reduce multicollinearity. If multicollinearity has a strong  presence in the dataset then the algorithm wont be able to differentiate between the datset points as clearly. A features' indivudual impact is extracted when we apply PCA. We want the algorithm to see the differences and no the similarities between two higly correlated features.
5) We scaled the data and then fit transformed the datset to 2 features using PCA.
6) We use Elbow Method, Agolomerative heirarchy method and silhoutte method to decide on the optimal clusters.
7) At last we fit the cluster lables and the predictor varibles, to see the performance in a supervised setting.

# Observations:
**1) For label 0: From Q1 - Q28, the mean rating was approx 4. So it means that 2249 students out of 5680, rated the overall performnace of course and intsructor as good. We will name label '0' as 'good', since the overall evaluations stood at the rating: 4/5.

**2) For label 1: From Q1 - Q28, the mean rating was approx 1.4. So it means that 1222 students out of 5680, rated the overall performnace of course and intsructor as bad. We will name label '1' as 'bad' in term of performance, since the overall evaluation stood at the rating: 1.4/5

**3) For label 2: From Q1 - Q28, the mean rating was approx 3. So it means that 2349 students out of 5680, rated the overall performnace of course and intsructor as average. We will name label '2' as 'average' in term of performance, since the overall evaluation stood at the rating: 3/5.

**4) Instructor 3 has to improve a lot since the 43% of the students who studied from him/her, found the university average.
   Instructor 1 performed the best among all the instructors, as students who studied from him/her, found the university good.
          
**5)  Course 2's course content, grading method, objectives had a positive impact - as 57% of students who took that course found the university  good.
        
**6) The average number of times a student had to repeat: 1.21 ~ 1. Also the minimum number of times a students had to repeat: 1. This means that the college's course content or instructor's teaching is not up to the mark. Students have to repeat the course again, which means teaching style has to be improved.

**The average attendance code for the students was also dismal, almost at code 2.

    From Q1 - Q28, the average rating hovers between 2.7 - 3.3 out 5, which means that the overall performance of the university was strictly above  average.
    
 **7) When we fit the dataset with the cluster labels in a Supervised Setting:
 
Without PCA
Training Accuracy
1.0
Testing Accuracy
0.981672394043528

With PCA
Training Accuracy
1.0
Testing Accuracy
1.0
