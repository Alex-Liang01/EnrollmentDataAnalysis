# EnrollmentDataAnalysis

## Introduction
The business objective of this project was to prepare business students with the necessary skills for the real world by ensuring they graduate on time through completing 30 credits per year allowing them to graduate within 4 years. Currently the average business student graduates in 6.5 years with one concentration being required. Our recommendation is to enforce students to take two concentrations when graduating with a DBBA. To address this business problem, we gathered enrollment data from the past year allowing us to define our analytics problem of identifying the most important factors related to the number of credits a student takes in a year. Through feature engineering, model free plots and machine learning we found that people with multiple concentrations tend to take fewer irrelevant courses from other faculties when compared to those with only a single concentration. This results in our recommendation of enforcing students to take two concentrations when graduating with a DBBA.

## Data Cleaning and Wrangling

### Data Gathering

The dataset was queried from a database resulting in the three main csvs Enroll, Student, and Term Concentrations which have the enrollment data with recent enrollments in the past three semesters, student data with their concentrations, and term/concentration data with a dictionary to concentration and term codes. 

These three main datasets were combined with credit information for each course which were webscraped.
This dataset was further enhanced with core courses information and concentration course information so that each course taken by a student could be mapped with whether they are relevant or not to a student's concentration.

With all datasets combined, features were engineered to such as proportions for classes relative to the total amount of courses that a student takes and proportions relative to the total amount of credits taken.

## Machine Learning

A standard random forest, stepwise regression, and xgboost was used to investigate the most important variables related to course concentrations. The RMSE for each of the models are as follows: 5.55, 6.32 for each of the random forest, stepwise regression and xgboost models.

<img width="524" alt="image" src="https://github.com/user-attachments/assets/86aba55e-6cf1-4ca5-b8d6-87675813b37e" />

From the random forest the 5 most important variables found are Thursday classes proportion of total courses, OLC Courses proportion of total, Bus Credit proportion of total, elective credit proportion of total and Friday classes proportion of total classes.

<img width="608" alt="image" src="https://github.com/user-attachments/assets/95391307-0568-48bd-a1d4-5221181d7f52" />

From the stepwise regression model, the most important variables related to the annual course credits taken are the mode of the start time for each student,the number of semesters with at least one concentration course, being in the co-op program, having at least one concentration course per semester enrolled, morning class proportion of total classes, afternoon class proportion of total classes, OLC course proportion of total classes and Concentration Credits Prop of total credits. All of these positively affect the annual course credits taken except for the concentration credits prop of total credits and having at least one concentration course per semester enrolled, and being enrolled in the co-op program.

## Data Visualization

To investigate the trends found from the machine learning models we used partial dependence plots to visualize the findings. 
<img width="520" alt="image" src="https://github.com/user-attachments/assets/ec6b1d59-5984-45e9-8077-2d82f60d50ab" />

<img width="520" alt="image" src="https://github.com/user-attachments/assets/60f926cd-1049-421f-8df6-21494829f53f" />

<img width="523" alt="image" src="https://github.com/user-attachments/assets/0150d814-ed15-4667-8739-691a293ed495" />

<img width="523" alt="image" src="https://github.com/user-attachments/assets/c0523ceb-41dd-42eb-a84b-a76a547f411b" />

<img width="524" alt="image" src="https://github.com/user-attachments/assets/20f96a85-b942-4530-a955-d435e4bdc4b8" />



It is observed that many of the observations found from the machine learning models are for the two tail ends of 1 and 0. At these levels the number of total credits taken annually drastically change when compared to the other proportions. This may be a result of part time students affecting the outcome as these students tend to not have all type of courses on every single day of the week. As a result, we investigated model free plots to come to a conclusion as the sample size of the data was too small to draw any significant conclusion since the dataset only comes from one year of enrollment data. With only one year of data comparisons can't be made across the same semester across different years due to different course offerings depending on the semester. 


The two main model plots we found interesting was the subject distribution by number of concentrations for students that take over 30 credits and the average credits from other concentration courses by number of subplans (excluding core courses).

<img width="486" alt="image" src="https://github.com/user-attachments/assets/33cdab8a-a82a-4c56-8f7c-bcc8de62956e" />

In the plot above on the subject distribution by number of concentrations, the largest light green bars are for the Business courses. It was observed that students with only one concentration tend to take a lot of unrelated electives when compared to those with two or more concentrations.

![Screenshot 2025-01-25 204600](https://github.com/user-attachments/assets/23c064dd-3e98-49b2-9e68-a47f2bcb8ad5)

In the plot above on the average credits from other concentration courses by number of subplans (excluding core courses) it is observed that as the number of concentrations go up, the average amount of business concentration courses that are unrelated to the student's concentration goes down with many of their credits being more related to their concentration choices.

As a result, this helped us come to the conclusion that students often take business concentration courses unrelated to their concentration helping us come up with the recommendation that students should be enforced to graduate with two concentrations.

## Conclusion

Our recommendation to address the problem of preparing business students with the necessary skills for the real world by ensuring they graduate on time through completing 30 credits per year 
is enforcing students to take two concentrations when graduating with a DBBA. This recommendation comes from the data driven fact that students tend to take a lot of courses that are not related to their concentration which does not help preprare them for the real world. By taking two concentrations, DBBA students are prepared for the real world as they will have studied multiple key areas of the business world allowing for them to stand out from their peers.

