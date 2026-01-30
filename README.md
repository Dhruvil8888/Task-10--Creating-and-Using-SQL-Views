 Task 10: Creating and Using SQL Views

## 📌 Project Overview
This task demonstrates how to create and use **SQL Views** to build reusable and secure query layers.  
Views simplify complex joins, improve data security, and act as virtual tables for reporting and analytics.

---

## 🛠 Tools & Technologies
- **Primary:** MySQL Workbench  
- **Alternatives:** PostgreSQL, BigQuery Sandbox, SQLite  

---

## 📂 Repository Structure
- `task10_views.sql` → SQL script defining and using views  
- `README.md` → Project documentation (this file)

---

## 🎯 Learning Objectives
- Create complex JOIN queries
- Convert queries into reusable SQL views
- Query, filter, and sort data from views
- Understand security and abstraction benefits
- Analyze insert/update limitations
- Drop and recreate views safely
- Map views to reporting dashboards

---

## 🗄 Tables Used
- **employees**
- **departments**

---

## 🧪 SQL Code Examples

### 1. Create a View
```sql
CREATE OR REPLACE VIEW employee_department_view AS
SELECT 
    e.emp_id,
    e.emp_name,
    e.salary,
    d.department_name,
    d.location
FROM employees e
JOIN departments d
ON e.department_id = d.department_id;
2. Query from the View
SELECT * FROM employee_department_view;
3. Filter Using the View
SELECT * 
FROM employee_department_view
WHERE department_name = 'IT';
4. Sort Using the View
SELECT * 
FROM employee_department_view
ORDER BY salary DESC;
5. Attempt Insert into View
INSERT INTO employee_department_view 
(emp_id, emp_name, salary, department_name, location)
VALUES (99, 'Test User', 50000, 'IT', 'Mumbai');
This fails because the view is based on a JOIN.

6. Drop and Recreate View
DROP VIEW IF EXISTS employee_department_view;
