### 데이터 정렬 : ORDER BY 절
#### 정렬 시 고려할 점 3가지
- 오름차순인가 내림차순인가
- NULL 값과 NULL 아닌 값 혼재 시 어떻게 정렬한 것인가
- 컬럼 숫자 위치로 정렬 기준을 삼을 것인가

#### 오름차순 또는 내림차순
- ASC : 오름차순 (기본값)
- DESC : 내림차순
```
SELECT last_name, department_id, hire_date
FROM employees
ORDER BY hire_date;
SELECT last_name, department_id, hire_date
FROM employees
ORDER BY hire_date DESC;
SELECT last_name, department_id, hire_date
FROM employees
ORDER BY last_name DESC;
```
#### NULL 값과 NULL 아닌 값이 혼재 시 정렬
- 정렬 시 NULL 값
   - NULL 값은 비교 불가하므로 정렬이 의미 없음.
   - 뒤에 몰아서 출력 (NULLS LAST), 앞에 몰아서 출력 (NULLS FIRST)
   - 오름차순 시 NULLS FAST, 내림차순 시 NULLS FIRST가 기본
```
SELECT last_name, job_id, commission_pct
FROM employees
ORDER BY commission_pct;
SELECT last_name, job_id, commission_pct
FROM employees
ORDER BY commission_pct DESC;
SELECT last_name, job_id, commission_pct
FROM employees
ORDER BY commission_pct NULLS FIRST;
```
#### 컬럼 별칭 기준으로 정렬
- 컬럼 별칭
   - 컬럼 별칭은 SELECT 절(5)에서 정의되므로 순서상 ORDER BY(6)에서 사용 가능
   - WHERE 절, GROUP BY 절 등에서는 사용 불가
#### 컬럼 위치 기준으로 정렬
- 컬럼 위치
   - ORDER BY 절의 양의 정수는 Select-list에 나타나는 컬럼의 위치
```
SELECT last_name, job_id, salary*12 AS annsal
FROM employees
ORDER BY 3;
```
#### 여러 컬럼을 기준으로 정렬
- 여러 컬럼
   - 컬럼 순서가 바뀌면 정렬 결과가 달라짐
   - 건수는 같음
```
SELECT last_name, job_id, department_id, hire_date
FROM employees
ORDER BY last_name, hire_date;
SELECT last_name, job_id, department_id, hire_date
FROM employees
ORDER BY last_nameDESC, hire_date;
SELECT last_name, job_id, department_id, hire_date
FROM employees
ORDER BY 2 DESC, hire_date
```
#### 함수 결과값을 기준으로 정렬
```
SELECT last_name, job_id, department_id,
hire_date
FROM employees
ORDER BY LENGTH(last_name);
SELECT last_name, job_id, DBMS_RANDOM.value
FROM employees
ORDER BY DBMS_RANDOM.value;
```
