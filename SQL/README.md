# SQL — Employees Database Practice

This notebook contains practical SQL exercises executed against a real MySQL `employees` database using `pandas` and `mysql-connector-python`.

## Part 1 — JOIN Operations (10 tasks)

Covers multi-table joins across `employees`, `salaries`, `titles`, `dept_emp`, `departments`, and `dept_manager` tables:

- Joining employees with their current salary
- Joining employees with their current job title
- Joining employees with their current department
- Counting employees per department (sorted by headcount)
- Finding the highest-paid employee in the Development department
- Finding which department the highest-paid employee in the company works in
- Finding the employee with the 3rd highest salary (`OFFSET`)
- Identifying employees who held multiple positions (`GROUP_CONCAT`)
- Tracking department transfers (`GROUP_CONCAT` with chronological ordering)
- Retrieving current manager salary for each department

## Part 2 — Window Functions (7 tasks)

Covers SQL window functions:

- `ROW_NUMBER()` — sequential numbering of employees
- `LAG()` — salary dynamics (previous salary for comparison)
- `RANK()` — salary rank within each department
- `CTE + DATE_SUB` — salary change over the last 2 years
- `LEAD()` — finding the employee with the highest salary increase
- `NTILE()` — dividing employees into salary groups
- Combined CTEs — average salary and first hire per job title

## Tools & Libraries
- `mysql-connector-python` — MySQL connection
- `pandas` — query execution and result display
- `pandasql` — SQL queries on DataFrames


## Files
- `Proj_SQL tasks.ipynb` — all queries with results
