# Using Prompts and Agents in LangChain

This notebook demonstrates how to build LLM-powered pipelines using LangChain and Claude (Anthropic).

## Tasks Overview

**Task 1 — Basic LLM Call**
Simple prompt to get a structured explanation of a topic (Quantum Computing) with a response length limit.

**Task 2 — Parameterized Prompt Template**
Using `PromptTemplate` to dynamically pass topics to the model. Tested on Bayesian Methods, Transformers, and Explainable AI.

**Task 3 — ReAct Agent for Scientific Publications**
A ReAct-type agent with Tavily search that automatically finds 5 recent AI research papers, returning title, authors, and description for each.

**Task 4 — Business Analytics Agent**
An agent combining web search (Tavily) and Python execution (PythonREPLTool) to generate a sales forecast for a Brazilian orange exporter, incorporating real-time weather data, inflation rates, and global demand trends.

## Tools & Libraries
- `langchain`, `langchain-anthropic`, `langchain-tavily`
- `langchain-experimental` (PythonREPLTool)
- `Claude Sonnet` (Anthropic API)
- `scipy`, `numpy`, `pandas`, `matplotlib`

# SQL Tasks — Employees Database

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
