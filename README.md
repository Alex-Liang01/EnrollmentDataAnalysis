# EnrollmentDataAnalysis

## Introduction
The business objective of this project was to prepare business students with the necessary skills for the real world by ensuring they graduate on time through completing 30 credits per year allowing them to graduate within 4 years. Currently the average business student graduates in 6.5 years with one concentration being required. Our recommendation is to enforce students to take two concentrations when graduating with a DBBA. To address this business problem, we gathered enrollment data from the past year allowing us to define our analytics problem of identifying the most important factors related to the number of credits a student takes in a year. Through feature engineering, model free plots and machine learning we found that people with multiple concentrations tend to take fewer irrelevant courses from other faculties when compared to those with only a single concentration. This results in our recommendation of enforcing students to take two concentrations when graduating with a DBBA.

## Data Cleaning and Wrangling

### Data Gathering

The dataset was queried from a database resulting in the three main csvs Enroll, Student, and Term Concentrations which have the enrollment data with recent enrollments in the past three semesters, student data with their concentrations, and term/concentration data with a dictionary to concentration and term codes. 

These three main datasets were combined with credit information for each course which were webscraped.
This dataset was further enhanced with core courses information and concentration course information so that each course taken by a student could be mapped with whether they are relevant or not to a student's concentration.

With all datasets combined, features were engineered to such as proportions for classes relative to the total amount of courses that a student takes and proportions relative to the total amount of credits taken.

#### Data Dictionary
The resulting data dictionary is as follows:

ID: Student identifying id
HourStartMode:The mode of start times for each student  
MorningClasses: Boolean value for more Morning classes (T) vs more Afternoon classes (F)
Credits.Taken.Annually: Credits taken annually
semesters_with_at_least_one_concentration_course: Number of semesters with at least one concentration course  
Transfer: Boolean value for whether the student is a transfer student
BUSMAJ: Boolean value for whether the student is a business major
BUSJMA: Boolean value for whether the student is a business joint major
MINOR: Boolean value for whether the student is a business minor
FINCON: Boolean value for whether the student is in the financial concentration
MKTGCON: Boolean value for whether the student is in the marketing concentration
BUSCOP: Boolean value for whether the student is in the business co-op program
STANCON: Boolean value for whether the student is in the strategic analysis concentration  
ACCTCON: Boolean value for whether the student is in the accounting concentration
MISCON: Boolean value for whether the student is in the mangement information system concentration
ENTINNCON: Boolean value for whether the student is in the innovation and entrepreneurship concentration
OPERMGTCON: Boolean value for whether the student is in the operation managements concentration
HRMCON: Boolean value for whether the student is in the human resources management concentration
INBUCON: Boolean value for whether the student is in the international business concentration
DeclaredConcentration: Boolean value for whether the student declared their concentration  
At_least_one_concentration_course_per_semester_enrolled: Boolean value for whether the student takes at least one concentration course for every semester in which they are enrolled 
Mon_classes_prop: Proportion of classes on Monday out of total classes  
Tues_classes_prop: Proportion of classes on Tuesday out of total classes    
Wed_classes_prop: Proportion of classes on Wednesday out of total classes    
Thurs_classes_prop: Proportion of classes on Thursday out of total classes    
Fri_classes_prop: Proportion of classes on Friday out of total classes    
MorningClassProp: Proportion of classes in the morning out of total classes    
AfternoonClassProp: Proportion of classes in the afternoon out of total classes    
OLC_courses_prop: Proportion of classes that are online out of total classes    
Concentration.Credits.Prop.of.Total.Credits: Proportion of concentration course credits out of total credits 
Certificate.Credits.Prop: Proportion of certificate course credits out of total credits  
Bus.Credit.Prop: Proportion of business course credits out of total credits    
Elective_credit_prop: Proportion of elective course credits out of total credits    

## Machine Learning

A standard random forest, stepwise regression, and xgboost was used to investigate the most important variables related to course concentrations. The RMSE for each of the models are as follows: 5.55, 6.32 for each of the random forest, stepwise regression and xgboost models.

![image](https://github.com/user-attachments/assets/7cfa9583-0c36-480f-91a0-08ab5bb9ca5f)


From the random forest the 5 most important variables found are Thursday classes proportion of total courses, OLC Courses proportion of total, Bus Credit proportion of total, elective credit proportion of total and Friday classes proportion of total classes.

![image](https://github.com/user-attachments/assets/271da707-f29a-43b2-b464-4dd48fd2b803)


From the stepwise regression model, the most important variables related to the annual course credits taken are the mode of the start time for each student,the number of semesters with at least one concentration course, being in the co-op program, having at least one concentration course per semester enrolled, morning class proportion of total classes, afternoon class proportion of total classes, OLC course proportion of total classes and Concentration Credits Prop of total credits. All of these positively affect the annual course credits taken except for the concentration credits prop of total credits and having at least one concentration course per semester enrolled, and being enrolled in the co-op program.

## Data Visualization

To investigate the trends found from the machine learning models we used partial dependence plots to visualize the findings. 
![image](https://github.com/user-attachments/assets/3875ee3d-c7ca-48b9-8b76-d2d36f4d7324)

![image](https://github.com/user-attachments/assets/de692e61-c760-42c4-aac3-995d0c68832e)

![image](https://github.com/user-attachments/assets/ff227573-c935-433c-b651-ae279b251e5a)

![image](https://github.com/user-attachments/assets/eb45f34c-786f-472c-9130-2bf76696c5cf)

![image](https://github.com/user-attachments/assets/59525aa5-807f-42c3-8261-ed8fa6034d5b)




It is observed that many of the observations found from the machine learning models are for the two tail ends of 1 and 0. At these levels the number of total credits taken annually drastically change when compared to the other proportions. This may be a result of part time students affecting the outcome as these students tend to not have all type of courses on every single day of the week. As a result, we investigated model free plots to come to a conclusion as the sample size of the data was too small to draw any significant conclusion since the dataset only comes from one year of enrollment data. With only one year of data comparisons can't be made across the same semester across different years due to different course offerings depending on the semester. 


The two main model plots we found interesting was the subject distribution by number of concentrations for students that take over 30 credits and the average credits from other concentration courses by number of subplans (excluding core courses).

![image](https://github.com/user-attachments/assets/a1d2e0dd-919b-40ba-abd3-b96e1e3eb23d)


In the plot above on the subject distribution by number of concentrations, the largest light green bars are for the Business courses. It was observed that students with only one concentration tend to take a lot of unrelated electives when compared to those with two or more concentrations.

![image](https://github.com/user-attachments/assets/f6730749-7b70-48dc-ae1b-2e633baff3dd)


In the plot above on the average credits from other concentration courses by number of subplans (excluding core courses) it is observed that as the number of concentrations go up, the average amount of business concentration courses that are unrelated to the student's concentration goes down with many of their credits being more related to their concentration choices.

As a result, this helped us come to the conclusion that students often take business concentration courses unrelated to their concentration helping us come up with the recommendation that students should be enforced to graduate with two concentrations.

## Conclusion

Our recommendation to address the problem of preparing business students with the necessary skills for the real world by ensuring they graduate on time through completing 30 credits per year 
is enforcing students to take two concentrations when graduating with a DBBA. This recommendation comes from the data driven fact that students tend to take a lot of courses that are not related to their concentration which does not help preprare them for the real world. By taking two concentrations, DBBA students are prepared for the real world as they will have studied multiple key areas of the business world allowing for them to stand out from their peers.

