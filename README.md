# SQL-Lab2

# We will use the Employees and Awards table below:

 <img src="Lab2.png" width="500" height="500">

### Q1: Choose all employees who have received an award (Nested Query)?
Query: SELECT *
FROM employee
WHERE id in (
  SELECT employee_id 
   FROM awards);

Output: <img src="p/1.png">
 

### Q2: Choose all employees who have never received an award (Nested Query)?
Query: SELECT *
FROM employee
WHERE id NOT IN (
    SELECT employee_id
    FROM awards
);

Output: <img src="p/2.png">

 
### Q3: Choose all Developers who make more than all Managers combined (Nested Query)?
Query: SELECT * 
FROM employee 
WHERE role = "Developer" and
salary > (SELECT MAX(salary) 
          FROM employee 
          WHERE role = "Manager");

Output: <img src="p/3.png">

 
### Q4: Choose all Developers who make more money than any Manager (Nested Query)?
Query: SELECT *
FROM employee
WHERE role = 'Developer'
    AND salary > (
        SELECT MIN(salary)
        FROM employee
        WHERE role = 'Manager'
    );

Output: <img src="p/4.png">

 
### Q5: Choose all employees whose salaries are higher than the average for their position. (Nested Query)?
Query: SELECT *
FROM employee e
WHERE salary > (
    SELECT AVG(salary)
    FROM employee ee
    WHERE ee.role = e.role
  );

Output: <img src="p/5.png">
