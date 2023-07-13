# DB-SQL-Join
SQL의 조인문

# 조인
조인은 두 개의 테이블을 서로 묶어서 하나의 결과를 만들어 내는 것을 말한다.

## 내부조인
내부 조인은 둘 이상의 테이블에 존재하는 공통 속성의 값이 같은 것을 결과로 추출합니다.

### 예시 ▼ 
SELECT E.EMPLOYEE_ID, E.LAST_NAME, E.SALARY, D.DEPARTMENT_NAME, L.CITY 
FROM EMPLOYEES E, DEPARTMENTS D, LOCATION L
WHERE E.DEPARTMENT_ID = D.DEPARTMENT_ID AND D.LOCATION_ID = L.LOCATION_ID
AND E.SALARY >=3000;
#### 테이블이 2개 이상일때 각 테이블에 다른 이름을 지정하고 연산자를 활용하여 결과를 출력한다 이 쿼리문은 내부조인중에서 등가조인에 해당한다

### 예시 ▼
SELECT E.LAST_NAME, J.JOB_ID FROM EMPLOYEES E, JOBS J
WHERE E.SALARY BETWEEN J.MIN_SALARY AND J.MAX_SALARY;
#### 위의 쿼리문은 연산자를 사용하지 않았으니 내부조인중 비등가조인에 해당한다


## 셀프조인
#### 셀프 조인이란 같은 테이블에 각자 다른SELF JOIN이란, 1개의 테이블(X)에 가상으로 x1, x2라는 별칭을 부여하여 2개의 테이블인 것처럼 간주한 뒤 JOIN하는 것입니다. 

### 예시 ▼
SELECT E.LAST_NAME, J.JOB_ID FROM EMPLOYEES E, JOBS J
WHERE E.SALARY BETWEEN J.MIN_SALARY AND J.MAX_SALARY;


## 왼쪽 외부 조인
###$ 조인문의 왼쪽에 있는 테이블의 모든 결과를 가져 온 후 오른쪽 테이블의 데이터를 매칭하고, 매칭되는 데이터가 없는 경우 NULL로 표시한다.

### 예시 ▼
SELECT E.EMPLOYEE_ID AS 사원번호, E.LAST_NAME AS 사원이름, E.MANAGER_ID AS 사원의매니저번호, 
M.EMPLOYEE_ID AS 매니저의사원번호, M.LAST_NAME AS 매니저이름
FROM EMPLOYEES E, EMPLOYEES M
WHERE E.MANAGER_ID = M.EMPLOYEE_ID(+) ORDER BY E.EMPLOYEE_ID;
