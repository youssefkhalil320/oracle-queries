
#  بِسْمِ اللَّـهِ الرَّحْمَـٰنِ الرَّحِيمِ اللهمّ صلِّ على محمّد وآل محمّد
# Oracle SQL QUeries

## Basic select statment

```
SELECT *
FROM DEPARTMENTS;
```
select all rows and columns in  the table DEPARTMENTS

```
SELECT DEPARTMENT_ID, DEPARTMENT_NAME
FROM DEPARTMENTS;
```
select columns DEPARTMENT_ID, DEPARTMENT_NAME from table DEPARTMENTS

```

SELECT EMPLOYEE_ID, FIRST_NAME, SALARY, SALARY+100, SALARY+(SALARY*0.10)
FROM EMPLOYEES;
```
select columns EMPLOYEE_ID, FIRST_NAME, SALARY from table EMPLOYEES and also create two new columns SALARY+100, which adds 100 to each record in the SALARY column and another column SALARY+(SALARY*0.01) which do the above calculation on each record on SALARY column

```
SELECT LAST_NAME, LAST_NAME AS NAME, LAST_NAME lname, LAST_NAME "Last Name"
FROM EMPLOYEES;
```
showing the column LAST_NAME with three ways to show a new alice for the LAST_NAME

```
SELECT FIRST_NAME, LAST_NAME, FIRST_NAME||LAST_NAME AS FULL_NAME, FIRST_NAME||' ' ||LAST_NAME AS FULL_NAME_SPACE
FROM EMPLOYEES;
```

showing the columns FIRST_NAME, LAST_NAME form table EMPLOYEES and showing two new columns, one concatenating the first name without space with alice FULL_NAME and the other concatinating the FIRST_NAME and LAST_NAME wit space between them with alice name FULL_NAME_SPACE

```

SELECT FIRST_NAME|| 'works in department' || DEPARTMENT_ID
FROM EMPLOYEES;
```
showing the first name and DEPARTMENT_ID and the sentence ' works in department ' between them. for example 'Youssef works in departement 10'

```
SELECT FIRST_NAME|| q'[works in department]' || DEPARTMENT_ID
FROM EMPLOYEES;
```
showing the first name and DEPARTMENT_ID and the sentence ' works in department ' between them. for example 'Youssef works in departement 10'

```
SELECT DISTINCT DEPARTMENT_ID
FROM EMPLOYEES;
```
shows the unique values of the column DEPARTMENT_ID in the table EMPLOYEES

```
DESCRIBE EMPLOYEES;
```
shows a description for the table EMPLOYEES including the data types for each column, if it contains NULL values or not, the percision for each column, the length and if the column is a primary key.

## adding a condition 

```
SELECT *
FROM EMPLOYEES
WHERE DEPARTMENT_ID = 90;
```
showing all the columns for the employees whose the value of their DEPARTMENT_ID column is 90

```
SELECT *
FROM EMPLOYEES
WHERE FIRST_NAME = 'Steven';
```
showing all the columns for the employees whose the value for their FIRST_NAME column is 'Steven'

```
SELECT * 
FROM EMPLOYEES
WHERE SALARY > 10000;
```

show all thre columns for the employees whose the value in the SALARY column is greater than 10000

```
SELECT * 
FROM EMPLOYEES
WHERE SALARY BETWEEN 10000 AND 20000;
```
show all the columns for the employees whose the value of salary in the range between 10000 and 20000. (10000 and 20000 are included)

```
SELECT *
FROM EMPLOYEES 
WHERE SALARY IN (10000, 25000, 17000);
```

show all columns for the employees whose their value of salary equals of of the following (10000, 25000, 17000)

```
SELECT *
FROM EMPLOYEES
WHERE FIRST_NAME LIKE 'S%';
```
shows all the columns for the employees whose trheir first name starts with letter 'S'

```
SELECT * 
FROM EMPLOYEES 
WHERE FIRST_NAME LIKE '%s';
```
shows all the columns for all the employees whose their FIRST_NAME end with the letter 's'

```
SELECT *
FROM EMPLOYEES
WHERE FIRST_NAME LIKE '%am%';
```
show all the columns for all the employees whose their FIRST_NAME includes this string 'am' in order.

```
SELECT *
FROM EMPLOYEES
WHERE FIRST_NAME LIKE '_d%';
```
show all the columns for all the employees whose their FIRST_NAME second letter is 'd'

```
SELECT *
FROM EMPLOYEES
WHERE FIRST_NAME LIKE '__s%';
```

show all the columns for the employees whose FIRST_NAME thirs letter is 's'

```
SELECT *
FROM EMPLOYEES
WHERE FIRST_NAME NOT LIKE 'S%';
```
show all the columns for the employees whose their FIRST_NAME does not start with the letter 's'

```
SELECT JOB_ID
FROM JOBS
WHERE JOB_ID LIKE '%/%%' escape '/';
```

show all the columns for the employeees whose FIRST_NAME contains the symbol '%'

```
SELECT *
FROM EMPLOYEES 
WHERE COMMISSION_PCT IS NULL;
```
show all the columns for the employees whose the value of their COMMISSION_PCT column is NULL

```
SELECT *
FROM EMPLOYEES
WHERE COMMISSION_PCT IS NOT NULL;
```
show all the columns for the employees whose the value of their COMMISSION_PCT column is not NULL

```
SELECT *
FROM EMPLOYEES
WHERE EMPLOYEE_ID NOT IN (100, 101);
```
show all the columns for the employees whose their EMPLOYEE_ID is any value but not 100 or 101

```

SELECT EMPLOYEE_ID, LAST_NAME, JOB_ID, SALARY, DEPARTMENT_ID
FROM EMPLOYEES
WHERE SALARY >= 10000 AND DEPARTMENT_ID=90;
```
show the columns EMPLOYEE_ID, LAST_NAME, JOB_ID, salary and DEPARTMENT_ID for the employees their salary value is greater than or equals 10000 and in the same time their DEPARTMENT_ID is 90


```
SELECT EMPLOYEE_ID, LAST_NAME, JOB_ID, SALARY, DEPARTMENT_ID
FROM EMPLOYEES
WHERE SALARY >= 10000 OR DEPARTMENT_ID=90;
```
show the columns EMPLOYEE_ID, LAST_NAME, JOB_ID, salary and DEPARTMENT_ID for the employees their salary value is greater than or equals 10000 or their DEPARTMENT_ID is 90 (if only one condition is true it is enough)

```
SELECT LAST_NAME, JOB_ID, SALARY
FROM EMPLOYEES
WHERE JOB_ID = 'SA_PRES'
OR JOB_ID = 'AD_PRES'
AND SALARY > 15000;
```
The execution of this query will be 
JOB_ID = 'SA_PRES'
OR (JOB_ID = 'AD_PRES'
AND SALARY > 15000)

because 'and' has high priority than 'or'

```
SELECT * 
FROM EMPLOYEES
ORDER BY HIRE_DATE ASC;
```
show all the colum for all the employees but order them using the HIRE_DATE ascendingly

```
SELECT *
FROM EMPLOYEES
ORDER BY COMMISSION_PCT DESC;
```

show all the colum for all the employees but order them using the HIRE_DATE descendingly

```
SELECT DEPARTMENT_ID, FIRST_NAME, SALARY
FROM EMPLOYEES
ORDER BY DEPARTMENT_ID, FIRST_NAME;
```

show the columns DEPARTMENT_ID, FIRST_NAME, salary for all employees and order them ascendingly using the DEPARTMENT_ID. for the employees whose DEPARTMENT_ID is equal use FIRST_NAME to order them ascendingly

```

SELECT DEPARTMENT_ID, FIRST_NAME, SALARY
FROM EMPLOYEES
ORDER BY DEPARTMENT_ID ASC, FIRST_NAME DESC;
```
show the columns DEPARTMENT_ID, FIRST_NAME, salary for all employees and order them ascendingly using the DEPARTMENT_ID. for the employees whose DEPARTMENT_ID is equal use FIRST_NAME to order them descendingly

```
SELECT DEPARTMENT_ID, FIRST_NAME, SALARY
FROM EMPLOYEES
ORDER BY 1;
```
show the columns DEPARTMENT_ID, FIRST_NAME and SALARY for all employees and order them ascendingly using the first column which is DEPARTMENT_ID

```
SELECT DEPARTMENT_ID, FIRST_NAME, SALARY
FROM EMPLOYEES
ORDER BY 1 ASC,3 DESC;
```
show the columns DEPARTMENT_ID, FIRST_NAME and SALARY for all employees and order them ascendingly using the first column which is DEPARTMENT_ID, if the values of the DEPARTMENT_ID is equal use the third column which is SALARY to ord them descendingly

## Substitution Variables

```
SELECT EMPLOYEE_ID, LAST_NAME, SALARY, DEPARTMENT_ID
FROM EMPLOYEES
WHERE EMPLOYEE_ID = &EMPLOYEE_NUM;
```
shows the columns EMPLOYEE_ID, LAST_NAME, salary and DEPARTMENT_ID for all employeees whose DEPARTMENT_ID equals the variable EMPLOYEE_NUM. when this query is excuted, a windows will apear asks you to enter the values for the variable EMPLOYEE_NUM


```
SELECT EMPLOYEE_ID, LAST_NAME, SALARY, DEPARTMENT_ID
FROM EMPLOYEES
WHERE LAST_NAME = '&lname';
```
shows the columns EMPLOYEE_ID, LAST_NAME, salary and DEPARTMENT_ID for all employeees whose LAST_NAME equals the value of the variable lname. (the variable between '' because they values of LAST_NAME column is always a string. will will do the same if it is date).
a windows will apear asks you to enter the values for the variable lname


```
SELECT EMPLOYEE_ID, LAST_NAME, JOB_ID, &COLUMN_NAME
FROM EMPLOYEES
WHERE &CONDITION
ORDER BY &ORDER_COLUMN;
```
window will appear to ask about COLUMN_NAME then another window will appear to ask about the CONDITION

```
DEFINE EMPLOYEE_NUM = 200;
SELECT EMPLOYEE_ID, LAST_NAME, SALARY, DEPARTMENT_ID
FROM EMPLOYEES
WHERE EMPLOYEE_ID = &EMPLOYEE_NUM;
UNDEFINE EMPLOYEE_NUM;
```
No window will appear to ask for EMPLOYEE_NUM becasue it is already defined using the word DEFINE. UNDEFINE will remove the definition of EMPLOYEE_NUM after this query so you can not use it anymore

```
SELECT EMPLOYEE_ID, LAST_NAME, JOB_ID, &&COLUMN_NAME
FROM EMPLOYEES
ORDER BY &COLUMN_NAME;
UNDEFINE COLUMN_NAME;
```
one window will appear to ask for the value of COLUMN_NAME because the '&&' makes it possible to use it again in the query

```
SET VERFIY ON 
SELECT EMPLOYEE_ID, LAST_NAME, SALARY
FROM EMPLOYEES
WHERE EMPLOYEE_ID = &E_NUM;
```

the command STE VERFIY ON. shows the (old) query before Substitution and the new query after Substitution. by default it is ON.
You can make it OFF


## Single-Row Functions

```
SELECT *
FROM EMPLOYEES
WHERE LOWER(LAST_NAME) = 'higgins'
```
it will convert all the charecters in LAST_NAME to lower case then if it is higgins, it will show it 


```
SELECT *
FROM EMPLOYEES
WHERE UPPER(LAST_NAME) = 'higgins'
```
it will convert all the charecters in LAST_NAME to upper case then if it is higgins, it will show it 

```
SELECT INITCAP(FIRST_NAME)
FROM EMPLOYEES
```
it will show all the emplyees first name but all the names will start with a capital letter

```
SELECT CONCAT(first_name, last_name) NAME, LENGTH(last_name),
INSTR(last_name, 'a') "contains 'a' ?"
FROM EMployees
WHERE SUBSTR(job_id, 4) = 'REP';
```
show a column called NAME which contains the first_name concatenated with the LAST_NAME. show a column called LENGTH(last_name) which contains the number of charcters in the last_name. show column called contains 'a' ? which contains the index of the letter a if it is in the last name.

condition --->  if the substring of JOB_ID starting from the forth letter is 'REP'

```
SELECT last_name, RPAD(salary,10, '*') "Salary"
FROM employees
WHERE department_id = 80
```
Shows The salary values with * on its right side. number of * w will be 10 - the length of the salary values 

```
SELECT last_name, LPAD(salary,10, '*') "Salary"
FROM employees
WHERE department_id = 80
```
Shows The salary values with * on its left side. number of * w will be 10 - the length of the salary values 

```
SELECT REPLACE(LAST_NAME, 'A', '*')
FROM EMPLOYEES
```
show the last_name but replace any 'A' letter with '*' symbol

```
SELECT TRIM('A' FROM LAST_NAME)
FROM EMPLOYEES
```
shows what comes after A in last_name

```
SELECT ROUND(10.499,2) FROM DUAL 
```
round to the 2nd number after the decimal point

output --> 10.50

```
SELECT ROUND(10.493,2) FROM DUAL 
```
round to the 2nd number after the decimal point

output --> 10.49

```
SELECT ROUND(55.993,-1) FROM DUAL 
```
round to the 1nd number before the decimal point

output --> 60

```
SELECT ROUND(570.993,-3) FROM DUAL 
```
round to the 3nd number before the decimal point

output --> 1000

```
SELECT ROUND(470.993,-3) FROM DUAL 
```
round to the 3nd number before the decimal point

output --> 0

```
SELECT TRUNC(10.6565) FROM DUAL 
```
Trunc everything after the decimal point

output --> 10

```
SELECT TRUNC(10.6565, 2) FROM DUAL 
```
Trunc starting from the 2nd place after the decimal point

output --> 10.65

```
SELECT TRUNC(998.6565, -2) FROM DUAL 
```
Trunc starting from the 2nd place before the decimal point and convert the rest to zeros

output --> 900

```
SELECT TRUNC(998.6565, -3) FROM DUAL 
```
Trunc starting from the 2nd place before the decimal point and convert the rest to zeros

output --> 0


```
SELECT MOD(15, 2) FROM DUAL 
```
returns the reminder of dividing 15 over 2 

output --> 1

```
SELECT MOD(15, 3) FROM DUAL 
```
returns the reminder of dividing 15 over 3

output --> 0

```
SELECT SYSDATE FROM DUAL 
```

show the current date and time on your machine

```
SELECT SYSDATE+3 FROM DUAL 
```
adding three days to the current date 


```
SELECT EMPLOYEE_ID, FIRST_NAME, SYSDATE-HIRE_DATE "no of days", (SYSDATE-HIRE_DATE)/7 "no of weeks"
FROM EMPLOYEES
WHERE FIRST_NAME = 'Adam';
```

no of days column will show the number of days between the hire date and the current date.

no of weeeks will shows the number of weeks between the hire date and the current date.

```
SELECT EMPLOYEE_ID, FIRST_NAME, MONTHS_BETWEEN(SYSDATE, HIRE_DATE), (SYSDATE-HIRE_DATE)/30
FROM EMPLOYEES;
```

both the 2nd and 3rd columns supposed to show the number of months between the current date and the hiring date but the first one is more accurate because it consider the months or 28 and 31 days.


```
SELECT EMPLOYEE_ID, FIRST_NAME, HIRE_DATE, ADD_MONTHS(hire_date, 4)
FROM EMPLOYEES;
```
the last column will add 4 months to the current date

```
SELECT SYSDATE, NEXT_DAY(SYSDATE, 'FRIDAY') FROM DUAL;
```
this will show the date of the next friday after the current date


```
SELECT LAST_DAY(SYSDATE) FROM DUAL;
```
this shows the date of the last day in the month of the current date

```
SELECT EMPLOYEE_ID,
FIRST_NAME,
HIRE_DATE,
ROUND(HIRE_DATE, 'MONTH'), TRUNC(HIRE_DATE, 'MONTH')
FROM EMPLOYEES
ORDER BY HIRE_DATE;
```
Round, month --> if the date is from day 1-15 round to the first day in the current month and if the day is 16-31 round to the first day of next month

Trunc, month --> makes the date the first day of the month in the current date

```
SELECT EMPLOYEE_ID,
FIRST_NAME,
HIRE_DATE,
ROUND(HIRE_DATE, 'year'), TRUNC(HIRE_DATE, 'year')
FROM EMPLOYEES
ORDER BY HIRE_DATE;
```

Round, Year --> if the months 1-6 round the date to the first day in JAN of the hire date. if it is 7-12 round to the first day in the next year


TRUNC, Year -> makes the date the first day in the year of current date

```
SELECT TO_CHAR(SYSDATE, 'dd-mm-yyyy') FROM DUAL;
```

the output date will be in the format  22-11-2023

```
SELECT TO_DATE('10-11-2015', 'dd-mm-yyyy') FROM DUAl;
```
the output will be in the format 11/10/2015

```
SELECT * FROM EMPLOYEES
WHERE HIRE_DATE > TO_DATE('10-11-2003', 'dd-mm-yyyy');
```
converting the date to a new formate to compare it with the hire date

```
SELECT TO_CHAR(SYSDATE, 'dd-mm-yyyy hh:mi:ss AM') FROM DUAL;
```
show the data and time 

example -->  22-11-2023 02:00:18 PM

```
SELECT TO_CHAR(HIRE_DATE, 'fmDD Month YYYY')
FROM EMPLOYEES;
```
output --> 17 June 2003

```
SELECT TO_CHAR(HIRE_DATE, 'fmDD "of" Month YYYY')
FROM EMPLOYEES;
```

output --> 17 of June 2003

```
SELECT TO_CHAR(HIRE_DATE, 'fmDDspth "of" Month YYYY')
FROM EMPLOYEES;
```

example --> SEVENTEENTH of June 2003

```
SELECT TO_CHAR(HIRE_DATE, 'fmddspth "of" Month YYYY')
FROM EMPLOYEES;
```

example --> seventeenth of June 2003

```
SELECT * FROM EMPLOYEES 
WHERE TO_CHAR(HIRE_DATE, 'yyyy') = '2003';
```
show employees hired in 2003

```
SELECT TO_CHAR(1598, '9,999') FROM DUAL;
```
output --> 1,598

```
SELECT TO_CHAR(1598, '$9,999') FROM DUAL;
```
output --> $1,598

```
SELECT TO_CHAR(1598, 'L9,999') FROM DUAL;
```

output --> $1,598

```
SELECT last_name, hire_date
FROM
employees
WHERE hire_date = TO_DATE('JUNE 17, 2003', 'fxMonth DD, YYYY');
```
show employees whose their hiring date is JUNE 17, 2003

```
SELECT last_name,
UPPER(CONCAT(SUBSTR (LAST_NAME, 1, 8), '_US'))
FROM
employees
WHERE department_id = 60;
```
SUBSTR will be excuted first then CONCAT then UPPER

```
SELECT
TO_CHAR(NEXT_DAY(ADD_MONTHS
(hire_date, 6), 'FRIDAY'),
'fmDay, Month ddth, YYYY')
"Next 6 Month Review"
FROM
employees
ORDER BY hire_date;
```
Display the date of the next Friday that is six months from the hire date. The
resulting date should appear as Friday, August 13th, 1999. Order the results by
hire date

```
SELECT EMPLOYEE_ID, FIRST_NAME, COMMISSION_PCT, NVL(COMMISSION_PCT, 0)
FROM EMPLOYEES;
```
NVL(COMMISSION_PCT, 0) --> if COMMISSION_PCT is NULL then put 0


```
SELECT EMPLOYEE_ID, FIRST_NAME, COMMISSION_PCT, NVL2(COMMISSION_PCT, COMMISSION_PCT,0)
FROM EMPLOYEES;
```
NVL2(COMMISSION_PCT, COMMISSION_PCT,0) --> if COMMISSION_PCT is not NULL return COMMISSION_PCT if it is NULL return 0


```
SELECT last_name, employee_id,
COALESCE(TO_CHAR(commission_pct),TO_CHAR(manager_id),
'No commission and no manager')
FROM employees;
```
generally, COALESCE  returns the first NON NULL value


```
SELECT last_name, salary, commission_pct,
COALESCE((salary+(commission_pct*salary)), salary+2000, salary) "New Salary"
FROM employees;
```
For the employees who do not get any commission,
your organization wants to give a salary increment of
$2,000 and for employees who get commission, the
query should compute the new salary that is equal to
the existing salary added to the commission amount.

```
SELECT last_name, job_id, salary,
CASE job_id WHEN 'IT_PROG' THEN 1.10*salary
WHEN 'ST_CLERK' THEN 1.15*salary
WHEN 'SA_REP' THEN 1.20*salary
ELSE
salary END
"REVISED_SALARY"
FROM
employees;
```

if job_id equals 'IT_PROG' then return 1.10*salary

if job_id equals 'ST_CLERK' then return 1.15*salary

if job_id equals 'SA_REP' then return 1.20*salary

else return salary 

name the new column REVISED_SALARY


```
SELECT last_name, job_id, salary,
CASE  WHEN job_id='IT_PROG' THEN 1.10*salary
WHEN job_id='ST_CLERK' THEN 1.15*salary
WHEN job_id='SA_REP' THEN 1.20*salary
ELSE salary 
END
"REVISED_SALARY"
FROM
employees;
```

same as the above query but in different style

```
SELECT last_name, job_id, salary,
DECODE(job_id, 'IT_PROG', 1.10*salary,
'ST_CLERK', 1.15*salary,
'SA_REP',
1.20*salary,
salary)
REVISED_SALARY
FROM
employees;
```

same as the above query but using decode instead of CASE

## Group Functions

```
SELECT AVG(salary), MAX(salary),
MIN(salary), SUM(salary)
FROM
employees
WHERE job_id LIKE '%REP%';

```

return the average(mean), maximum,  minimum and the sum of values in salary column for all employes whose job_id contains 'REP'

```
SELECT MIN(hire_date), MAX(hire_date)
FROM
employees;
```
return maximum hiring date and minimum hiring date for employeees

```
SELECT COUNT(*)
FROM
employees
WHERE department_id = 50;
```
return the count of all values in employees table whose their department_id equals 50

```
SELECT COUNT(commission_pct)
FROM
employees
WHERE department_id = 80;
```
return the number of employees whose commission_pct is not equal NULL and their department_id equals 80

```
SELECT COUNT(DISTINCT department_id)
FROM
employees;
```
return the number of unique values in the department_id column 

```
SELECT AVG(commission_pct)
FROM
employees;
```
return the average of values in the commission_pct 

```
SELECT AVG(NVL(commission_pct, 0))
FROM
employees;
```
replace any NULL values in commission_pct column then get the average

```
SELECT
department_id, AVG(salary)
FROM
employees
GROUP BY department_id ;
```

returns the average salaries for the employees in the same department 

```
SELECT
AVG(salary)
FROM
employees
GROUP BY department_id ;
```
as the above query

note: The GROUP BY column does not have to be in the SELECT list.

```
SELECT
department_id dept_id, job_id, SUM(salary)
FROM
employees
GROUP BY department_id, job_id
ORDER BY department_id;
```
show the department_id, job_id, and the average salary for each department  and order them ascendingly using the department_id

note:  job_id must be in the ORDER BY, if not it will give an error


```
SELECT
department_id, AVG(salary)
FROM
employees
WHERE
AVG(salary) > 8000
GROUP BY department_id;
```
this gives an error because WHERE can not be used with a group function. instead of WHERE we should use HAVING


```
SELECT
department_id, MAX(salary)
FROM employees
GROUP BY department_id
HAVING MAX(salary)>10000 ;
```
shows the department_id and the maximum salary for each department_id only for departements whose maximum salary is greater than 10000


```
SELECT
job_id, SUM(salary) PAYROLL
FROM
employees
WHERE
job_id NOT LIKE '%REP%'
GROUP BY job_id
HAVING
SUM(salary) > 13000
ORDER BY SUM(salary);
```
shows the job_id and the sum of salaries for each job_id for all job_ids that do not contain 'REP'
and the maximum salary of the job_id is greater than 13000


```
SELECT
MAX(AVG(salary))
FROM
employees
GROUP BY department_id;
```
you can use nested group by Functions but maximum 2 nested functions 

## Joins

```
SELECT department_id, department_name,
location_id, city
FROM
departments
NATURAL JOIN locations ;
```

NATURAL JOIN will be used to join the two tables using the common tables between departements and locations

```
SELECT employee_id, last_name,
location_id, department_id
FROM
employees JOIN departments
USING (department_id) ;
```
writing USING instead of NATURAL JOIN 


```
SELECT l.city, d.department_name
FROM
locations l JOIN departments d
USING (location_id)
WHERE d.location_id = 1400;
```

it gives an ERROR 

– Do not qualify a column that is used in the USING clause.
– If the same column is used elsewhere in the SQL statement, do not alias it.

```
SELECT e.employee_id, e.last_name, e.department_id,
d.department_id, d.location_id
FROM
employees e JOIN departments d
ON
(e.department_id = d.department_id);
```
Using JOIN ON to join tables using department_id in both tables 

```
SELECT employee_id, city, department_name
FROM
employees e
JOIN
departments d
ON
d.department_id = e.department_id
JOIN
locations l
ON
d.location_id = l.location_id;
```
two joins 
employees-departements using department_id

departements-locations using location_id

```
SELECT e.employee_id, e.last_name, e.department_id,
d.department_id, d.location_id
FROM
employees e JOIN departments d
ON
(e.department_id = d.department_id)
AND
e.manager_id = 149 ;
```

adding a condition using the join which is employee manager id is 149


```
SELECT e.employee_id, e.last_name, e.department_id,
d.department_id, d.location_id
FROM
employees e JOIN departments d
ON
(e.department_id = d.department_id)
WHERE
e.manager_id = 149 ;
```
Sama as above query but using WHERE instead of AND


```
SELECT worker.last_name emp, manager.last_name mgr
FROM
employees worker JOIN employees manager
ON
(worker.manager_id = manager.employee_id);
```
self join 


```
SELECT e.last_name, e.salary, j.grade_level
FROM
employees e JOIN job_grades j
ON
e.salary
BETWEEN j.lowest_sal AND j.highest_sal;
```
Nonequijoins

```
SELECT e.last_name, e.department_id, d.department_name
FROM
employees e LEFT OUTER JOIN departments d
ON
(e.department_id = d.department_id) ;
```

```
SELECT e.last_name, e.department_id, d.department_name
FROM
employees e RIGHT OUTER JOIN departments d
ON
(e.department_id = d.department_id) ;
```

```
SELECT e.last_name, d.department_id, d.department_name
FROM
employees e FULL OUTER JOIN departments d
ON
(e.department_id = d.department_id) ;
```

```
SELECT last_name, department_name
FROM
employees
CROSS JOIN departments ;
```
Cross Joins

## Subqueries

```
SELECT last_name, salary
11000
FROM
employees
WHERE salary >
(SELECT salary
FROM
employees
WHERE last_name = 'Abel');
```

display all employees who earn salary
greater than the salary of employee Abel


```
SELECT last_name, job_id, salary
FROM
employees
SA_REP
WHERE job_id =
(SELECT job_id
FROM
employees
WHERE last_name = ‘Taylor’)
AND
salary >
8600
(SELECT salary
FROM
employees
WHERE last_name = ‘Taylor’);
```


```
SELECT last_name, job_id, salary
FROM
employees
WHERE salary =
(SELECT MIN(salary)
FROM
employees);
```

```
SELECT
department_id, MIN(salary)
FROM
employees
GROUP BY department_id
HAVING
MIN(salary) >
(SELECT MIN(salary)
FROM
employees
WHERE department_id = 50);
```


```
SELECT employee_id, last_name
FROM
employees
WHERE salary =
(SELECT
MIN(salary)
FROM
employees
GROUP BY department_id);
```

gives an error because the inner query do not return a single value 


```
SELECT last_name, job_id
FROM
employees
WHERE job_id =
(SELECT job_id
FROM
employees
WHERE last_name = 'Haas');
```
returns no rows because the inner query returns no rows 

```
SELECT employee_id, last_name, job_id, salary
FROM
employees
WHERE salary < ANY
(SELECT salary
FROM
employees
WHERE job_id = 'IT_PROG')
AND
job_id <> 'IT_PROG';
```
select employee_id, last_name, job_id and salary if (the salary is greater than any salary of employees whose job_id is 'IT_PROG)
and job_id not equal 'IT_PROG'

```
SELECT employee_id, last_name, job_id, salary
9000, 6000, 4200
FROM
employees
WHERE salary < ALL
(SELECT salary
FROM
employees
WHERE job_id = 'IT_PROG')
AND
job_id <> 'IT_PROG';
```

select employee_id, last_name, job_id and salary if (the salary is greater than all salaries of employees whose job_id is 'IT_PROG)
and job_id not equal 'IT_PROG'

```
SELECT emp.last_name
FROM
employees emp
WHERE emp.employee_id NOT IN
(SELECT mgr.manager_id
FROM
employees mgr);
```

returns 0 rows because the inner query returns NULL

## Set Operators

```
SELECT employee_id, job_id
FROM
employees
UNION
SELECT employee_id, job_id
FROM
job_history;
```
show the concatination of rows in both employees and job_history tables without duplicates

```
SELECT employee_id, job_id, department_id
FROM
employees
UNION ALL
SELECT employee_id, job_id, department_id
FROM
job_history
ORDER BY employee_id;
```
show the concatination of rows in both employees and job_history tables with duplicates ordered ascendingly by employee_id


```
SELECT employee_id, job_id
FROM
employees
INTERSECT
SELECT employee_id, job_id
FROM
job_history;
```
Display the employee IDs and job IDs of those employees who currently have a
job title that is the same as their previous one (that is, they changed jobs but
have now gone back to doing the same job they did previously).


```
SELECT employee_id
FROM
employees
MINUS
SELECT employee_id
FROM
job_history;
```

show the records exists in employees and job_history


```
SELECT location_id, department_name "Department",
TO_CHAR(NULL) "Warehouse location"
FROM departments
UNION
SELECT location_id, TO_CHAR(NULL) "Department",
state_province
FROM locations;
```

-Using the UNION operator, display the location ID, department name, and the
state where it is located.


– You must match the data type (using the TO_CHAR function or any other
conversion functions) when columns do not exist in one or the other table.


```
SELECT employee_id, job_id,salary
FROM
employees
UNION
SELECT employee_id, job_id,0
FROM
job_history;
```
## ROLLUP and CUBE

```
SELECT
department_id, job_id, SUM(salary)
FROM
employees
WHERE
department_id < 60
GROUP BY ROLLUP(department_id, job_id);
```

```
SELECT
department_id, job_id, SUM(salary)
FROM
employees
WHERE
department_id < 60
GROUP BY CUBE (department_id, job_id) ;
```

```
SELECT
department_id DEPTID, job_id JOB,
SUM(salary),
GROUPING(department_id) GRP_DEPT,
GROUPING(job_id) GRP_JOB
FROM
employees
WHERE
department_id < 50
GROUP BY ROLLUP(department_id, job_id);
```

```
SELECT
department_id, job_id,
manager_id,AVG(salary)
FROM
employees
GROUP BY GROUPING SETS
((department_id,job_id), (job_id,manager_id));
```

```
SELECT
department_id, job_id, manager_id,
SUM(salary)
FROM
employees
GROUP BY ROLLUP( department_id,(job_id, manager_id));
```

```
SELECT
department_id, job_id, manager_id,
SUM(salary)
FROM
employees
GROUP BY department_id,
ROLLUP(job_id),
CUBE(manager_id);
```

## database objects 

```
CREATE TABLE hire_dates
(id
NUMBER(8),
hire_date DATE DEFAULT SYSDATE);
```

create a table called hire_dates with two columns id ---> number, hire_date ---> date

```
CREATE TABLE dept
(deptno
NUMBER(2),
dname
VARCHAR2(14),
loc
VARCHAR2(13),
create_date DATE DEFAULT SYSDATE);
```

create a table called dept and give the column create default value SYSDATE

```
CREATE TABLE employees(
employee_id NUMBER(6)
CONSTRAINT emp_emp_id_pk PRIMARY KEY,
first_name
VARCHAR2(20),
);
```

creating a table and adding a CONSTRAINT for the column employee_id to be the primary key of the table 


```
CREATE TABLE employees(
employee_id NUMBER(6),
first_name
VARCHAR2(20),
job_id VARCHAR2(10) NOT NULL,
CONSTRAINT emp_emp_id_pk
PRIMARY KEY (EMPLOYEE_ID));
```

the same as the above query but note that adding the CONSTRAINT to the end of the query needs to add the column name


```
CREATE TABLE employees(
employee_id
NUMBER(6),
last_name
VARCHAR2(25) NOT NULL,
email
VARCHAR2(25),
salary
NUMBER(8,2),
commission_pct
NUMBER(2,2),
hire_date
DATE NOT NULL,
CONSTRAINT emp_email_uk UNIQUE(email));
```

adding NOT NULL CONSTRAINT to columns last_name and hire_date.
adding UNIQUE CONSTRAINT to email column


```
CREATE TABLE employees(
employee_id
NUMBER(6),
last_name
VARCHAR2(25) NOT NULL,
email
VARCHAR2(25),
salary
NUMBER(8,2),
commission_pct
NUMBER(2,2),
hire_date
DATE NOT NULL,
department_id
NUMBER(4),
CONSTRAINT emp_dept_fk FOREIGN KEY (department_id)
REFERENCES departments(department_id),
CONSTRAINT emp_email_uk UNIQUE(email));
```

adding FOREIGN KEY CONSTRAINT to the column departement with refrence to column department_id in departments table


```
ON DELETE CASCADE
```

Deletes the dependent rows in the child table when a
row in the parent table is deleted

```
ON DELETE SET NULL
```

Converts dependent foreign key values to null


```
CREATE TABLE employees(
employee_id
NUMBER(6),
last_name
VARCHAR2(25) NOT NULL,
email
VARCHAR2(25),
salary
NUMBER(8,2)
CONSTRAINT emp_salary_min
CHECK (salary > 0) ,
commission_pct
NUMBER(2,2),
hire_date
DATE NOT NULL,
department_id
NUMBER(4),
);
```

adding a check CONSTRAINT to check that the salary value > 0


```
CREATE TABLE employees
( employee_id
NUMBER(6)
CONSTRAINT
emp_employee_id
PRIMARY KEY
, first_name
VARCHAR2(20)
, last_name
VARCHAR2(25)
CONSTRAINT
emp_last_name_nn NOT NULL
, email
VARCHAR2(25)
CONSTRAINT
emp_email_nn
NOT NULL
CONSTRAINT
emp_email_uk
UNIQUE
, phone_number
VARCHAR2(20)
, hire_date
DATE
CONSTRAINT
emp_hire_date_nn NOT NULL
, job_id
VARCHAR2(10)
CONSTRAINT
emp_job_nn
NOT NULL
, salary
NUMBER(8,2)
CONSTRAINT
emp_salary_ck
CHECK (salary>0)
, commission_pct NUMBER(2,2)
, manager_id
NUMBER(6)
CONSTRAINT emp_manager_fk REFERENCES
employees (employee_id)
, department_id NUMBER(4)
CONSTRAINT
emp_dept_fk
REFERENCES
departments (department_id));
```

```
UPDATE employees
SET
department_id = 55
WHERE department_id = 110;
```

updating values in a table 


```
DELETE FROM departments
WHERE department_id = 60;
```

deleting a row

```
CREATE TABLE dept80
AS
SELECT employee_id, last_name,
salary*12 ANNSAL,
hire_date
FROM
employees
WHERE
department_id = 80;
```

creating a table as a Subquery


```
ALTER TABLE employees READ ONLY;
-- perform table maintenance and then
-- return table back to read/write mode
ALTER TABLE employees READ WRITE;
```

using ALTER to edit tables 


```
DROP TABLE dept80;
```

droping / deleting a table 


```
CREATE VIEW empvu80
AS SELECT employee_id, last_name, salary
FROM
employees
WHERE
department_id = 80;
```

creating a view from the table employeees


```
CREATE VIEW salvu50
AS SELECT employee_id ID_NUMBER, last_name NAME,
salary*12 ANN_SALARY
FROM
employees
WHERE
= 50;
```

creating a view using column alias 

```
CREATE OR REPLACE VIEW empvu80
(id_number, name, sal, department_id)
AS SELECT employee_id, first_name || ' '
|| last_name, salary, department_id
FROM
employees
WHERE department_id = 90;
```

editing the view using CREATE or REPLACE view clause


```
CREATE OR REPLACE VIEW dept_sum_vu
(name, minsal, maxsal, avgsal)
AS SELECT
d.department_name, MIN(e.salary),
MAX(e.salary),AVG(e.salary)
FROM
employees e JOIN departments d
ON
(e.department_id = d.department_id)
GROUP BY d.department_name;
```

creating a complex view (using two tables)


```
CREATE OR REPLACE VIEW empvu20
AS SELECT
*
FROM
employees
WHERE departement_id = 20
WITH CHECK OPTION CONSTRAINT empvu20_ck
```

creating a view with check option constriant clause


```
CREATE OR REPLACE VIEW empvu10
(employee_number, employee_name, job_title)
AS SELECT
employee_id, last_name, job_id
FROM
employees
WHERE
department_id = 10
WITH READ ONLY ;
```

creating a READ ONLY view


```
DROP VIEW empvu80;
```

drop/delete a view 

```
CREATE SEQUENCE dept_deptid_seq
INCREMENT BY 10
START WITH 120
MAXVALUE 9999
NOCACHE
NOCYCLE;
```

creating a SEQUENCE 


```
INSERT INTO departments(department_id,
department_name, location_id)
VALUES
(dept_deptid_seq.NEXTVAL,
'Support', 2500);
```

NEXTVAL returns the next available sequence value. It returns a unique value
every time it is referenced, even for different users.

CURRVAL obtains the current sequence value.


```
ALTER SEQUENCE dept_deptid_seq
INCREMENT BY 20
MAXVALUE 999999
NOCACHE
NOCYCLE;
```

editing the squence using ALTER statment 


```
DROP SEQUENCE dept_deptid_seq;
```

drop / delete a squence 


```
CREATE INDEX emp_last_name_idx
ON
employees(last_name);
```

creating an index  


```
DROP INDEX emp_last_name_idx;
```

drop an index


```
CREATE SYNONYM d_sum
FOR dept_sum_vu;
```

create a SYNONYM "d_sum" for the view dept_sum_vu 


```
DROP SYNONYM d_sum;
```
drop a SYNONYM 


## Pairwise Comparison Subquery


```
SELECT employee_id, manager_id, department_id
FROM
empl_demo
WHERE (manager_id, department_id) IN
(SELECT manager_id, department_id
FROM empl_demo
WHERE first_name = 'John')
AND first_name <> 'John';
```

Display the details of the employees who are managed by the same manager
and work in the same department as employees with the first name of “John.”


## Nonpairwise Comparison Subquery


```
SELECT
FROM
WHERE
employee_id, manager_id, department_id
empl_demo
manager_id IN
(SELECT manager_id
FROM empl_demo
WHERE first_name = 'John')
AND department_id IN
(SELECT department_id
FROM empl_demo
WHERE first_name = 'John')
AND first_name <> 'John';
```

Display the details of the employees who are managed by the same manager as
the employees with the first name of “John” and work in the same department
as the employees with the first name of “John.”


##Scalar Subqueries


```
SELECT employee_id, last_name,
(CASE
20
WHEN department_id =
(SELECT department_id
FROM departments
WHERE location_id = 1800)
THEN
'Canada'
ELSE
'USA'
END) location
FROM
employees;
```


```
SELECT
employee_id, last_name
FROM
employees e
ORDER BY (SELECT department_name
FROM departments d
WHERE e.department_id = d.department_id);
```

## Correlated Subqueries


```
SELECT last_name, salary, department_id
FROM
employees outer
WHERE salary >
(SELECT AVG(salary)
FROM
employees
WHERE department_id =
outer.department_id);
```

Find all employees who earn more than the average salary in their department.


```
SELECT e.employee_id, last_name,e.job_id
FROM
employees e
WHERE 2 <= (SELECT COUNT(*)
FROM
job_history
WHERE employee_id = e.employee_id);
```

Display details of those employees who have changed
jobs at least twice.


```
SELECT employee_id, last_name, job_id, department_id
FROM
employees outer
WHERE EXISTS ( SELECT 'X'
FROM
employees
WHERE manager_id =
outer.employee_id);
```

Find Employees Who Have at Least One Person Reporting to
Them


```
SELECT department_id, department_name
FROM departments d
WHERE NOT EXISTS (SELECT 'X'
FROM
employees
WHERE department_id = d.department_id);
```

Find All Departments That Do Not Have Any Employees


```
ALTER TABLE empl6
ADD(department_name VARCHAR2(25));

UPDATE empl6 e
SET
department_name =
(SELECT department_name
FROM
departments d
WHERE e.department_id = d.department_id);
```

Correlated UPDATE

```
DELETE FROM empl6 E
WHERE employee_id =
(SELECT employee_id
FROM
emp_history
WHERE employee_id = E.employee_id);
```

```
WITH
dept_costs AS (
SELECT d.department_name, SUM(e.salary) AS dept_total
FROM
employees e JOIN departments d
ON
e.department_id = d.department_id
GROUP BY d.department_name),
avg_cost
AS (
SELECT SUM(dept_total)/COUNT(*) AS dept_avg
FROM
dept_costs)
SELECT *
FROM
dept_costs
WHERE dept_total >
(SELECT dept_avg
FROM avg_cost)
ORDER BY department_name;
```

## REGEX

```
select * from employees 
where REGEXP_LIKE (first_name, 'a.e');
```

find any first name than contains a then anay character then e


```
select * from employees 
where REGEXP_LIKE(first_name, 'a.e', 'c');
```

find any first name than contains a then anay character then e with case sensitive matching


```
select * from employees 
where REGEXP_LIKE(first_name, 'a.e', 'i');
```

find any first name than contains a then anay character then e with case insensitive matching


```
select * from test 
where REGEXP_LIKE(code, 'c+', 'i');
```

finy any code that contains one character c or more than one with insensative case search


```
select * from test 
where REGEXP_LIKE(code, 'le+', 'i');
```

find any code that contains one l then one e or more with case insensetive search

```
select * from employees
where REGEXP_LIKE(first_name, 'an?c', 'i');
```

select any first name that contains a then n (optionaly) then c with case insensetive search


```
select * from test
where REGEXP_LIKE(code, 'ab*c', 'i')
```

select any code that contains a then zero b or more then one c with case insensetive search


```
select * from employees
where REGEXP_LIKE(first_name, 'l{2}', 'i');
```

select any first name that contains two l letter with case insensetive search


```
select * from employees
where REGEXP_LIKE(first_name, 'l{2,}' , 'i');
```

select any first name that contains two l letters or more -- select any first name that contains two l letter with case insensetive search


```
select * from employees 
where REGEXP_LIKE(first_name, 'b{3,4}', 'i');
```

select any first name that contains three l letters or maximum four


```
select * from employees 
where REGEXP_LIKE(first_name, '[rc]', 'i');
```

select first names that contains r or c


```
select * from employees 
where not REGEXP_LIKE(first_name, '[rc]','i');
```

select any first name that does not contain r or c

```
select * from employees 
where REGEXP_LIKE(first_name, 'z|o', 'i');
```

select * from employees 
where REGEXP_LIKE(first_name, 'z|o', 'i');


```
select * from employees 
where REGEXP_LIKE(first_name, '^s', 'i');
```

select any first name that starts with s , case insenstive


```
select * from employees 
where REGEXP_LIKE(first_name,'n$', 'i')
```

select any first name that ends with n , case insenstive 


```
select * from employees 
where REGEXP_LIKE(first_name, 'on$' , 'i');
```

select any first name that ends with on 


```
select * from employees 
where REGEXP_LIKE(first_name, '(an)?c' , 'i');
```

select any first namne contains an then c optionally 


```
select * from employees 
where REGEXP_LIKE(first_name, '^Ste(v|ph)en$', 'i');
```

select first name that starts with Ste then v or ph the ends with en , case insenstive 


```
select * from test
where REGEX_LIKE(url, '^(f|ht)tps?:$');
```

find urls 


```
select * from test
where REGEXP_LIKE(code, '\*' , 'i');
```

select any code that contains *


```
select * from test 
where REGEXP_LIKE(code, '[0123456789]' , 'i')
```

select any code that conyains any digit


```
select * from test
where  REGEXP_LIKE(code, '[0-9]' , 'i');
```

select any code that contains any digit between 0 and 9


```
select * from employees 
where REGEXP_LIKE(first_name, '[a-c]', 'i');
```

select any first name contains any letters a,b,c 


```
select * from employees 
where REGEXP_LIKE(employee_id, '\d', 'i');
```

select any employee id contains any number


```
SELECT * 
FROM employees
WHERE REGEXP_LIKE(employee_id, '\d{3}');
```

select any employee id where the id contains more than 3 consecutive digits

```
select * from employees
WHERE REGEXP_LIKE(first_name, '[[:upper:]]');
```

select any employee where firs name contains any upperecase letter 


```
select * from employees
WHERE REGEXP_LIKE(first_name, '[[:lower:]]');
```

select any employee where firs name contains any lowreecase letter 


```
select * from employees 
WHERE REGEXP_LIKE(first_name, '[[:alpha:]]');
```

select any employees where first name contains any alphapetic letter


```
SELECT REGEXP_REPLACE('khaledaa', 'a', 'x') FROM DUAL;
```

replace every a with x


```
SELECT REGEXP_REPLACE('khaledalele', 'le', 'x') FROM DUAL;
```

replace every le with x


```
SELECT REGEXP_REPLACE('Tamer     ELgayar', '( ){2,}', ' ') from DUAL;
```

replace any space with more than one space with one space 


```
SELECT REGEXP_REPLACE('xkhaledxalix' , 'x' , 'w' , 2) FROM DUAL;
```

replace every x with w starting from the second occurance of x 

```
SELECT REGEXP_REPLACE('xkhaledxalix' , 'x' , 'w' , 1,2) FROM DUAL;
```

replace every x with w starting from frist letter but only replace the second occurance


```
SELECT REGEXP_REPLACE('1khaled50ali', '[[:digit:]]' , ':)') FROM DUAL;
```

replace every digit with :)

```
SELECT REGEXP_count('my name is ajojo', 'a') from DUAL;
```

count the occurance of a in the sentence 


```
SELECT REGEXP_COUNT('hsldad2dad2dad28', '[[:digit:]]') from DUAL;
```

count the digits in the sentences 


```
SELECT REGEXP_COUNT('fsdf1sf1d5sd8f86sf', '[[:alpha:]]') from DUAL;
```

count the alphapets in the sentence 


```
SELECT REGEXP_INSTR('hsldad2dad2dad28' , 'a') from dual;
```

return the index of the first a in the sentence 


```
SELECT REGEXP_INSTR('hsldad2dad2dad28' , 'a' , 6) from dual;
```

return the index of the first a in the sentence starting from the index 6


```
SELECT REGEXP_INSTR('hsLdad2dad2dad28' , '[[:upper:]]') from dual;
```

return the index of the first a uppercase letter in the sentence 

## User Control 

```
CREATE USER demo
IDENTIFIED BY demo;
```

create a new user with username demo and password demo


```
GRANT
create session, create table,
create sequence, create view
TO demo;
```

granting privilegies to user demo



```
CREATE ROLE manager;
```

creating a role called manager


```
GRANT create table, create view
TO MANAGER;
```

granting privilegies to the role manager


```
GRANT manager TO BELL, KOCHHAR;
```

granting the role manager to users: BELL and KOCHHAR


```
ALTER USER demo
IDENTIFIED BY employ;
```

changing the password of user demo to employ


```
GRANT select
ON
employees
to demo;
```

grant the previlege select on the table employees to the user demo


```
GRANT
ON
TO
update (department_name, location_id)
departments
demo, manager;
```

grant the previlege update on the columns department_name and location_id in the table departments to users demo and manager


```
GRANT
select, insert
ON
departments
TO
demo
WITH 
GRANT OPTION;
```

grant privilegies to user with authority to to pass along privileges


```
GRANT select
ON
alice.departments
TO
PUBLIC;
```

Allow all users on the system to query data from Alice’s DEPARTMENTS table


```
REVOKE
ON
FROM
select, insert
departments
demo;
```

Revoke the SELECT and INSERT privileges given to the demo user on the
DEPARTMENTS table.


```
REVOKE
ON
FROM
select, insert
departments
demo
CASCADE CONSTRAINTS;
```

Revoke the SELECT and INSERT privileges given to the demo user on the
DEPARTMENTS table.

CASCADE
Is required to remove any referential integrity
constraints made to the CONSTRAINTS object by
means of the REFERENCES privilege


## Data Dictionary Views


```
DESCRIBE DICTIONARY;
```

shows names and descriptions of the
dictionary tables and views


```
SELECT *
FROM
dictionary
WHERE table_name = 'USER_OBJECTS';
```
to see all the objects that you own plus data created, date of last modfication and status


```
SELECT object_name, object_type, created, status
FROM
user_objects
ORDER BY object_type;
```


```
DESCRIBE user_tables
```

```
SELECT table_name
FROM
user_tables;
```


```
DESCRIBE user_tab_columns
```

describe the columns of tables 


```
SELECT column_name, data_type, data_length,
data_precision, data_scale, nullable
FROM
user_tab_columns
WHERE table_name = 'EMPLOYEES';
```

```
DESCRIBE user_constraints
```

describes the constraint definitions on your tables


```
SELECT constraint_name, constraint_type,
search_condition, r_constraint_name,
delete_rule, status
FROM
user_constraints
WHERE table_name = 'EMPLOYEES';
```

```
DESCRIBE user_cons_columns
```

```
SELECT constraint_name, column_name
FROM
user_cons_columns
WHERE table_name = 'EMPLOYEES';
```

```
DESCRIBE user_views
```

```
SELECT DISTINCT view_name FROM user_views;
```

```
SELECT text FROM user_views
WHERE view_name = 'EMP_DETAILS_VIEW';
```

```
DESCRIBE user_sequences
```

```
SELECT
FROM
sequence_name, min_value, max_value,
increment_by, last_number
user_sequences;
```

```
DESCRIBE user_indexes
```

```
SELECT index_name, table_name,uniqueness
FROM
WHERE
user_indexes
table_name = 'EMPLOYEES';
```

```
SELECT INDEX_NAME, TABLE_NAME
FROM
WHERE
USER_INDEXES
TABLE_NAME = 'EMP_LIB';
```


```
DESCRIBE user_ind_columns
```

```
SELECT INDEX_NAME, COLUMN_NAME,TABLE_NAME
FROM
user_ind_columns
WHERE INDEX_NAME = 'LNAME_IDX';
```

```
DESCRIBE user_synonyms
```

```
SELECT *
FROM
user_synonyms;
```


```
COMMENT ON TABLE employees
IS 'Employee Information';
```

adding a comment to a table


```
COMMENT ON COLUMN employees.first_name
IS 'First name of the employee';
```

adding a comment to a column 


## PL/SQL 


```
DECLARE
CURSOR c_employees IS SELECT * FROM
employees; BEGIN
FOR c_emp in c_employees
LOOP
IF c_emp.job_id = 'SA_REP' AND c_emp.hire_date <= '05-Feb-2005'
THEN UPDATE employees
SET job_id = 'SR_SA_REP' WHERE employee_id = c_emp.employee_id;
ELSIF c_emp.job_id = 'MK_REP' AND c_emp.hire_date <= '05-Feb-2005'
THEN UPDATE employees
SET job_id = 'SR_MK_REP' WHERE employee_id = c_emp.employee_id;
ELSIF c_emp.job_id = 'ST_CLERK' AND c_emp.hire_date <= '05-Feb-2005'
THEN UPDATE employees
SET job_id = 'SR_ST_CLRK' WHERE employee_id =
c_emp.employee_id; END IF;
END LOOP;
END;
```

creating a for loop with if statment for updating employees data 


```
BEGIN
DBMS_OUTPUT.PUT_LINE('PL/SQL is easy!');
END;
```

to print use DBMS_OUTPUT.PUT_LINE


```
DECLARE
v_date
DATE := SYSDATE;
BEGIN
DBMS_OUTPUT.PUT_LINE(v_date);
END;
```

DECLARE a variable and assigning SYSDATE to it then printing it


```
DECLARE
v_first_name
VARCHAR2(25);
v_last_name
VARCHAR2(25);
BEGIN
SELECT first_name, last_name
INTO v_first_name, v_last_name
FROM employees
WHERE last_name = 'Oswald';
DBMS_OUTPUT.PUT_LINE ('The employee of the month is: '
|| v_first_name || ' ' || v_last_name || '.');
EXCEPTION
WHEN TOO_MANY_ROWS THEN
DBMS_OUTPUT.PUT_LINE ('Your select statement retrieved
multiple rows. Consider using a cursor or changing
the search criteria.');
END;
```

adding EXCEPTION handler 


```
CREATE OR REPLACE PROCEDURE print_date IS
v_date VARCHAR2(30);
BEGIN
SELECT TO_CHAR(SYSDATE,'Mon DD, YYYY')
INTO v_date
FROM DUAL;
DBMS_OUTPUT.PUT_LINE(v_date);
END;
```
defining a functon called print_date that prints today's date 


```
BEGIN
PRINT_DATE;
END;
```

calling the above function


```
CREATE OR REPLACE FUNCTION tomorrow (p_today IN DATE)
RETURN DATE IS
v_tomorrow DATE;
BEGIN
SELECT p_today + 1 INTO v_tomorrow
FROM DUAL;
RETURN v_tomorrow;
END;
```

creating a function called tomorrow that takes a DATE parameter called p_today

```
SELECT TOMORROW(SYSDATE) AS "Tomorrow's Date"
FROM DUAL;
or
BEGIN
DBMS_OUTPUT.PUT_LINE(TOMORROW(SYSDATE));
```
two ways to call and print results of the function tomorrow


```
DECLARE
v_emp_count NUMBER;
BEGIN
DBMS_OUTPUT.PUT_LINE('PL/SQL is easy so far!');
SELECT COUNT(*) INTO v_emp_count FROM employees;
DBMS_OUTPUT.PUT_LINE('There are '||v_emp_count||'
rows in the employees table');
END;
```

creating a variable called NUMBER then assigning a value to it then printing it


```
DECLARE
v_counter INTEGER := 0;
BEGIN
v_counter := v_counter + 1;
DBMS_OUTPUT.PUT_LINE(v_counter);
END;
```

DECLARE an INTEGER variable called v_counter
with intial value 0 then adding 1 to the v_counter then printing it


```
DECLARE
fam_birthdate DATE;
fam_size
NUMBER(2) NOT NULL := 10;
fam_location
VARCHAR2(13) := 'Florida';
fam_bank
CONSTANT NUMBER := 50000;
fam_population
INTEGER;
fam_name
VARCHAR2(20) DEFAULT 'Roberts';
fam_party_size
CONSTANT PLS_INTEGER := 20;
```


```
DECLARE
v_myname VARCHAR2(20);
BEGIN
DBMS_OUTPUT.PUT_LINE('My name is: '||v_myname);
v_myname := 'John';
DBMS_OUTPUT.PUT_LINE('My name is: '||v_myname);
END;
```

DECLARE a VARCHAR2 variable without intial value then assigning a value 'John' to it 


```
DECLARE
v_myname VARCHAR2(20):= 'John';
BEGIN
v_myname := 'Steven';
DBMS_OUTPUT.PUT_LINE('My name is: '|| v_myname);
END;
```

```
DECLARE
VARCHAR2(30);
v_date
BEGIN
SELECT TO_CHAR(SYSDATE) INTO v_date FROM DUAL;
DBMS_OUTPUT.PUT_LINE(v_date);
END;
```

```
CREATE FUNCTION num_characters (p_string IN VARCHAR2)
RETURN INTEGER IS
v_num_characters INTEGER;
BEGIN
SELECT LENGTH(p_string) INTO v_num_characters
FROM DUAL;
RETURN v_num_characters;
END;
```

DECLARE a function called num_characters that takes a parameter p_string ad return an INTEGER value v_num_characters 


```
DECLARE
v_length_of_string INTEGER;
BEGIN
v_length_of_string := num_characters('Oracle
Corporation');
DBMS_OUTPUT.PUT_LINE(v_length_of_string);
END;
```

calling the above function then assigning the returned value in a variable called v_length_of_string then printing it 


# تَمَّتْ بِحَمْدِ اَللَّهِ وَصَلَّى اَللَّهُ عَلَى سَيِّدِنَا مُحَمَّدْ وَعَلَى آلِهِ وَصَحْبِهِ وَسَلَّمَ