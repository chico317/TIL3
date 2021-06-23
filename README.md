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

# 서브쿼리
종류는 위치에 따른 분류를 사용

스칼라 서브쿼리: 메인쿼리의 SELECT 절에 위치한 서브쿼리....하나의 column or 표현식 역할
특정 코드 명칭을 가져올때 주로 사용.

# 인라인뷰
메인쿼리의 FROM절에 위치... 하나의 테이블처럼 동작... 표현식 수는 1개 이상 가능

# 중첩 서브쿼리
메인쿼리의 WHERE 절에 위치
