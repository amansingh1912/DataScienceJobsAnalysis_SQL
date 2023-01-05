# Data Science Jobs Analysis Using SQL

I took one dataset from Kaggle which is regarding Data Science Jobs Salary and did a case study on it based on some questions with respect to the dataset.

[Link to Dataset](https://www.kaggle.com/datasets/milanvaddoriya/data-science-job-salary)

## Case Study:

I came up with few questions, and based on that I wrote some SQL queries to come up with insights based on it.

### Tool Used: MYSQL

Q1) Update EUR to USD in salary table.

Ans: Currently 1 EUR = 1.06 USD, so updating salary column in USD currency.
Code:

UPDATE `datascience_salaries`
SET salary= salary*1.06
where salary_currency= "EUR";

Q2) Replace EUR to USD in salary_currency column.
Ans:-

Code:
UPDATE `datascience_salaries`
SET salary_currency="USD"
where salary_currency="EUR";

Q3) Find list of job titles with their total salary and with their employee count per job title.

Ans:
Code:
SELECT job_title, count(*) as TotalEmployees, SUM(salary) as TotalSalary_Amount from `datascience_salaries`
group by job_title
order by TotalSalary_Amount desc;



![job_title with count](https://user-images.githubusercontent.com/72240938/210790108-1a8f001c-7b82-4d30-9e4c-223df8ed7272.jpg)

Maximum employees and salary in the dataset are from Data scientist job title and minimum is from ML Ops.

Q4) Find total salary from different experience levels with their employee count per experience level.
Ans:
Code:
SELECT experience_level, count(*) as TotalEmployees, SUM(salary) as TotalSalary_Amount from `datascience_salaries`
group by experience_level
order by TotalSalary_Amount desc;

Output:

![experience level with count](https://user-images.githubusercontent.com/72240938/210790448-5c8441b7-d104-45c4-962a-a23ada803ae6.jpg)

Q5) Find location with their count in a table.

Ans:
Code:
SELECT location, count(*) as LocationCount from `datascience_salaries`
group by location
order by LocationCount desc
limit 5;

![location with locationcount](https://user-images.githubusercontent.com/72240938/210790616-39ad8efc-a318-4974-8f31-fa3d3a4a9b73.jpg)

Q6) Create a filter for salary column for different ranges of salary amount.

Ans:

Code:
SELECT job_title,salary,
CASE
when salary>=0 and salary<=50000 THEN 'Below 50000'
when salary>=50000 and salary<=100000 THEN 'Above 50000 and below 100000'
ELSE "Above 100000"
END AS salary_criteria
from datascience_salaries;

![salary criteria photo](https://user-images.githubusercontent.com/72240938/210790917-7c87486e-2a82-4386-ad83-824345b896f5.jpg)


### Key Insights:
* Data Scientist is one of the popular jobs among all data science jobs and is highly paid too.
* In India, most of the employees in data science field are in Bengaluru which is also called an IT hub.
* Senior Level Employees are the most worldwide and Executive level are the least.
