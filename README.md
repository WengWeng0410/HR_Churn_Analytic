# HR Churn Analytic

## <p align="right">[Portfolio Main Page](https://github.com/WengWeng0410/Weng_Portfolio)</p>

In this project, a model is built to predict if an employee of a company is at risk of leaving the company. It should be noted that it costly for a company to look suitable candidate to replace that employee, especially for the executives or high pay employees. This is due to the amount of time needed to conduct interview, training needed for the new employee as well as reduce of productivity for few months for the employee to get familiar with the new role. 

Hence, understanding why and when an employee is likely to leave can improve the employee retention as well as possibly in planning new hiring in advance. 

**Business Question**: How likely is an employee will churn depending on their workload and experience in a company?

Works done as follows

* Perform data exploratory on the features in the data
* Perform data cleaning on the dataset 
* Construct a dashboard for reporting purpose 
* Develop a model to predict if an existing employee will leave the company, based on department, working hours, number of project etc

## Code and Resources Used

**Python Version:** 3.7 <br>
**Packages:** numpy, pandas, seaborn, matplotlib, sklearn <br>
**IDE:** Google Colab <br>
**Dashboard Software:** Google Data Studio <br>
**Dataset:** from [360 Data Science Programm](https://thelead.io/data-science-360) by The Lead <br>
**Python Script:** [Notebook](https://colab.research.google.com/drive/1jjykwZWvngHiko-Y3ZneIv0AD-iB5rJG?usp=sharing)

## Data Gathering

The dataset used in this project were provided during the 360 Data Science Programme training. It is a real world dataset which consist of features (11 features and 15000 records) listed as follows: <br>
* names - name of an employee
* satisfaction_level - satisfaction level of an employee towards the company
* last_evaluation - performance evaluation mark rated on an employee
* number_project - number of project an employee handle in a month
* average_monthly_hours - average monthly working hours of an employee
* exp_in_company - experience of an employee in the company
* work_accident - work accident during working hour
* left - status of an employee who has left
* promotion_last_5years - promotion given to an employee inthe past 5 years
* role - department of an employee attached to the company
* salary - salary category (low, medium, high)

## Data Cleaning

Based on the given dataset, it is ready to use for analysis. 

## EDA

To understand the patterns and values of the data by using different types of visualizations. <br>
**Dashboard** of HR Churn Analytic is avaiable [here](https://datastudio.google.com/reporting/1774b914-a1c3-4b3b-b537-5534ffbc1889).

#### Heatmap of correlation between the features 
![](/images/HRC_Corr.png)
  
#### Total employee in the company
![](/images/TotalEmp.png)

#### Employee distribution in the company
![](/images/EmpDistribution.png)
<br> Based on the graph, There are 10 departments in the company. Sales department is with the highest number of employee (4140) and followed by Technical (2721) and Support (2229). <br> 

#### Employee for each department (existing and left)
![](/images/Exist_vs_Left_Dept.png)

#### Number of project per employee
![](/images/Emp_vs_proj.png)
<br>**For Left Employee** <br>
Based on the graph, the employee with 2 projects were with the highest number of employee left, (1567 employees), followed by 6 (655 employees) and 5 (613 employees) projects. <br> Also, it can be seen that employees tend to leave if the number of projects increased (from 3 to 6 projects). Suprisingly, all the employees with 7 projects have all left the company. Besides, it is found that employees with 2 project are tend to leave the company as they may feel that their talents are not utilized. <br> 

**For Existing Employee** <br>
Based on the graph, employees with 3 and 4 projects are with the highest number of employees (3983 and 3956, respectively). This is followed by employees with 5, 2 and 6 projects. This can conclude that employees are assigned with 3-4 projects and they are comfortable with the assignment. <br> 

In general, employees are comfortable with 3 or 4 projects. <br> Hence, number of project may also determine if an employee will leave the company <br>

#### Employee with work accident
![](/images/Emp_vs_WorkAcc.png)
<br> Based on the graph, it is found that the number of employees with work accident left the company is low accross all the departments in the company. <br>

#### Years of experience for existing and left employee
![](/images/Emp_vs_exp.png)
<br> **For Existing Employee** <br>
Based on the graph, it can be seen that years 2 to 4 are with the highest number of employees. <br>

**For Left Employee** <br>
For the employees with 2 years experience, it can be seen that there are only 53 employees out of 3244 left the company. This may due to the employees would like to gain more working experience or experience the working environment before leaving. <br>
The year with the highest number of employee left is 3 and slowly decreases to year 6. <br>
For years 7 to 10, there is no employee leaving the company. <br><br>
To summarise, the longer an employee work in the company, the lesser the posibility he/she leaves the company. <br>

#### Promotion in the past 5 years for existing and left employee
![](/images/Emp_vs_promo.png)
<br> Based on the graph, it can be seen that the number of employees that received promotion in the past 5 years is very low. (319 employees out of 15000 promoted) <br>

#### Salary category of existing and left employee
![](/images/Emp_vs_sal.png)
<br> Based on the graph, it can be seen that employees with low salary are with highest number of employee left followed by medium and high salary. <br> 

#### Last performance evaluation of existing and left employee
![](/images/Emp_vs_evaluation.png)
<br> Based on the graph, it can be seen that existing employees are mostly with at least 50% evaluation score. For the employees left, there are with evaluation score of less than 60%. <br> However, there are employees with evaluation score of 70% and above left the company. 
![](/images/Emp_vs_workHours.png) 
![](/images/Emp_vs_workHours_2.png)
<br> Based on the graphs above, employees with good evaluation left the company mainly due to most of them are assigned with 4 - 7 projects, and their average monthly working hours are more than 200 hours. <br><br> **Note**: Average monthly working hours is 184 hours (23 days x 8 hours) <br>

## Model Building

Prior to the model building, the data that is with non numeric type (role and salary) has to be converted to numeric value. **LabelEncoder** from **sklearn.preprocesing** is used to accomplish the conversion task. Besides that, **MinMaxScaler** from **sklearn.preprocesing** is also used to scale the values of average_monthly_hours into range of 0 to 1. Reason being this feature is measured at different scale and do not contribute equally in model training and may ended with creating a bias. <br> 
**train_test_split** from **sklearn.model_selection** is also used to separat the dataset into training and testing set of data. In this project, 80% of the dataset is used as training set and the remaining 20% is used as testing set. <br>
Three models have been selected: <br>
* LogisticRegression
* RandomForestClassifier
* SVC
* KNeighborsClassifier  

## Performane Evaluation

Performance of the model as follows: <br>
* LogisticRegression - 76.30%
* **RandomForestClassifier - 98.08%**
* SVC - 97.96%
* KNeighborsClassifier - 93.92%
![](/images/model_performance_HRC.png)

Based on the result, RandomForestClassifier is able to produce the best accuracy score, which is 98.08%.























