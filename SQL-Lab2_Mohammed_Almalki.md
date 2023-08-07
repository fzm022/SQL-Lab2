# Q1: Choose all employees who have received an award (Nested Query)?


```SQL
SELECT * FROM employee
WHERE employee.id in (SELECT awards.employee_id 
                      from awards)
```

# Q2: Choose all employees who have never received an award (Nested Query)?


```SQL
SELECT * FROM employee
WHERE employee.id NOT in (SELECT awards.employee_id 
                      from awards);
```

# Q3: Choose all Developers who make more than all Managers combined (Nested Query)?

```SQL
SELECT * FROM employee
WHERE role ='Developer' AND salary > (
SELECT MAX(salary) FROM employee 
WHERE role ='Manager'
);
```

# Q4: Choose all Developers who make more money than any Manager (Nested Query)?
```SQL
SELECT * FROM employee
WHERE role ='Developer' AND salary > (
SELECT salary FROM employee 
WHERE role ='Manager'
);
```

# Q5: Choose all employees whose salaries are higher than the average for their position. (Nested Query)?
```SQL
SELECT * FROM employee
WHERE salary > (
SELECT AVG(salary) FROM employee 
GROUP BY role);
```
