# TIL3
#SQL
-LAG: 선행 로우값(이전 로우값) & LEAD: 후행 로우값(다음 로우값)
SELECT b.department_id, b.department_name,
a.first_name || ' ' || a.last_name as emp_name,
a.hire_date,
LAG(salary, 1, 0) OVER (PARTITION BY b.department_id
ORDER BY a.hire_date ) PrevSal,
a.salary ,
LEAD(salary, 1, 0) OVER (PARTITION BY b.department_id
ORDER BY a.hire_date ) NextSal
FROM employees a,
departments b
WHERE a.department_id = b.department_id
ORDER BY 2, 4 ; 
