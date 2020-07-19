# Gazi-University-Student-Evaluations---Clustering-Project
A clustering project to visualize and analyze how a university performed according to student evaluations. A breakdown to analyze how students evaluated instructors and courses.

# Problem Description:
5860 students of Gazi Univeristy are asked to rate 28 Questions on Instructor performance, Course content, Grading Methods etc.
Students can rate for every question from 1 to 5, 1 is the lowest rating while 5 is the highest rating.
The aim is to segment the data into groups to know how differently students reveiwed for all the questions.

# Data Description:
There are 5820 rows with 33  numerical features which are ordinal or simply discrete.
instr: Instructor's identifier; values taken from {1,2,3}
class: Course code (descriptor); values taken from {1-13}
repeat: Number of times the student is taking this course; values taken from {0,1,2,3,...}
attendance: Code of the level of attendance; values from {0, 1, 2, 3, 4}
difficulty: Level of difficulty of the course as perceived by the student; values taken from {1,2,3,4,5}
Q1: The semester course content, teaching method and evaluation system were provided at the start.
Q2: The course aims and objectives were clearly stated at the beginning of the period.
Q3: The course was worth the amount of credit assigned to it.
Q4: The course was taught according to the syllabus announced on the first day of class.
Q5: The class discussions, homework assignments, applications and studies were satisfactory.
Q6: The textbook and other courses resources were sufficient and up to date.
Q7: The course allowed field work, applications, laboratory, discussion and other studies.
Q8: The quizzes, assignments, projects and exams contributed to helping the learning.
Q9: I greatly enjoyed the class and was eager to actively participate during the lectures.
Q10: My initial expectations about the course were met at the end of the period or year.
Q11: The course was relevant and beneficial to my professional development.
Q12: The course helped me look at life and the world with a new perspective.
Q13: The Instructor's knowledge was relevant and up to date.
Q14: The Instructor came prepared for classes.
Q15: The Instructor taught in accordance with the announced lesson plan.
Q16: The Instructor was committed to the course and was understandable.
Q17: The Instructor arrived on time for classes.
Q18: The Instructor has a smooth and easy to follow delivery/speech.
Q19: The Instructor made effective use of class hours.
Q20: The Instructor explained the course and was eager to be helpful to students.
Q21: The Instructor demonstrated a positive approach to students.
Q22: The Instructor was open and respectful of the views of students about the course.
Q23: The Instructor encouraged participation in the course.
Q24: The Instructor gave relevant homework assignments/projects, and helped/guided students.
Q25: The Instructor responded to questions about the course inside and outside of the course.
Q26: The Instructor's evaluation system (midterm and final questions, projects, assignments, etc.) effectively measured the course objectives.
Q27: The Instructor provided solutions to exams and discussed them with students.
Q28: The Instructor treated all students in a right and objective manner.

Q1-Q28 are all Likert-type, meaning that the values are taken from {1,2,3,4,5}

# Approach to our Problem:
1) Figure which variables are categorical or numerical.
2) We remove instructor code and course code since they are categorical variables, and we assume they won't be a deciding factor for clustering, as we only want to cluster on the ratings the students gave.
3) We plot a heatmap to check for multicollinearity, as there are a lot of features.
4) Since there is a strong presence of multicollinearity, we will be applying PCA to reduce multicollinearity. If multicollinearity has a strong  presence in the dataset then the algorithm wont be able to differentiate between the datset points as clearly. A features' indivudual impact is extracted when we apply PCA. We want the algorithm to see the differences and no the similarities between two higly correlated features.
5) We scaled the data and then fit transformed the datset to 2 features using PCA.
6) We use Elbow Method, Agolomerative heirarchy method and silhoutte method to decide on the optimal clusters.
7) At last we fit the cluster lables and the predictor varibles, to see the performance in a supervised setting.

# Observations:
1) For label 0: From Q1 - Q28, the mean rating was approx 4. So it means that 2249 students out of 5680, rated the overall performnace of course and intsructor as good. We will name label '0' as 'good', since the overall evaluations stood at the rating: 4/5.
2) For label 1: From Q1 - Q28, the mean rating was approx 1.4. So it means that 1222 students out of 5680, rated the overall performnace of course and intsructor as bad. We will name label '1' as 'bad' in term of performance, since the overall evaluation stood at the rating: 1.4/5
3) For label 2: From Q1 - Q28, the mean rating was approx 3. So it means that 2349 students out of 5680, rated the overall performnace of course and intsructor as average. We will name label '2' as 'average' in term of performance, since the overall evaluation stood at the rating: 3/5.

4) % of students who reviewed the college as per the cluster labels and under which instructor they studied:
      Instructor code	      Good	     Average	      Bad
          1	              48.903226	  32.258065	  18.838710
          2	              46.675900	  38.157895	  15.166205
          3	              33.212996	  42.988059	  23.798945
          
          Instructor 3 has to improve a lot since the 43% of the students who studied from him/her, found the university average.
          Instructor 1 performed the best among all the instructors, as students who studied from him/her, found the university good.
          
5) % of students who reviewed the college as per the cluster labels and which course they took for studying:

      class	    Good	     Average	     Bad
        2	    57.857143	  23.571429	  18.571429
        10	  52.232143	  30.133929	  17.633929
        1	    49.834983	  36.633663	  13.531353
      	6	    46.953405	  36.559140	  16.487455
      	11	  45.247934	  39.876033	  14.876033
      	8	    39.400000 	46.800000	  13.800000
      	5	    37.652439	  42.835366	  19.512195
      	7	    34.224599	  43.850267	  21.925134
      	12	  34.146341	  36.585366	  29.268293
      	9	    33.975482	  47.985989	  18.038529
     	  3	    31.858407	  41.150442	  26.991150
      	13	  30.439952	  37.098692	  32.461356
      	4	    22.459893	  55.080214	  22.459893
        
        Course 2's course content, grading method, objectives had a positive impact - as 57% of students who took that course found the university  good.
        
 6) The average number of times a student had to repeat: 1.21 ~ 1. Also the minimum number of times a students had to repeat: 1. This means that the college's course content or instructor's teaching is not up to the mark. Students have to repeat the course again, which means teaching style has to be improved.

The average attendance code for the students was also dismal, almost at code 2.

From Q1 - Q28, the average rating hovers between 2.7 - 3.3 out 5, which means that the overall performance of the university was strictly above average.
