### where 절과 비교 연산자
#### where 절을 이용하여 반환하는 행을 제한
- 후보행을 평가하여 그 결과가 TRUE인 후보행만 허용
- 재료 집합의 모든 행이 후보행으로 평가될 때까지 처리
- 후보행 평가를 위한 조건식 필요

#### 문자열과 날짜값 모두 작은 따옴표로 묶어야 함.
- 문자 : 대소문가 구별
- 날짜/시간
   - DATE 형
     - 세기, 년, 월, 일, 시, 분 초를 나타내는 내부 정수 숫자 형식으로 저장
   - 대소문자 구별 X
   - 날짜(표현) 형식 구별
   - 세션의 날짜 형식에 맞춰 자동 변환 시도
   - 날짜 변환함수 : TO_DATE
- 세션의 날짜/시간 형식 확인
  ```
  SELECT *
  FROM NLS_SESSION_PARAMETERS
  WHERE parameter LIKE ‘%FORMAT%’;
  ```
- 세션의 날짜/시간 형식 변환
  ```
  ALTER SESSION SET nls_date_format= ‘YYYY-MM-DD’;
  ALTER SESSION SET nls_date_format= ‘YYYY-MM-DD 
  HH24:MI:SS’;
  ALTER SESSION SET nls_timestamp_format= ‘YYYY
  MM-DD HH:MI:SS.FF’;
  ALTER SESSION SET nls_timestamp_tz_format = 
  ‘YYYY-MM-DD HH:MI:SS.FF TZH:TZM’;
  ```
#### 비교 연산자
<img width="357" alt="image" src="https://github.com/user-attachments/assets/bb031255-a160-4efe-800a-a5d25d1913d0" />

### 데이터 제한 : 논리 연산자
#### NULL 값 비교
##### NULL 값 직접 비교
- 결과는 무조건 NULL
```
 SELECT last_name, salary
 FROM employees
 WHERE commission_pct = NULL;
```
##### NULL 값 비교 시 무조건 NULL이 아닌 예외
- 예외 1
   - IS [NOT] NULL 비교 연산자 -> 결과는 T,F 뿐
   ```
   SELECT last_name, salary, commission_pct
   FROM employees
   WHERE commission_pct IS NULL;
   ```
- 예외 2
   - IN 연산자의 멤버 값 중 적어도 하나는 NULL아닌 경우
   ```
   SELECT last_name, salary, commission_pct
   FROM employees
   WHERE commission_pct IN(0.1,NULL,NULL);
   ```
#### 논리 연산자
<img width="393" alt="image" src="https://github.com/user-attachments/assets/eddd1995-2799-4338-9e60-be5d4cb1a64a" />

##### AND 연산자
```
 SELECT last_name, salary, commission_pct
 FROM employees
 WHERE commission_pct IS NULL;
```
##### OR 연산자
```
SELECT employee_id, last_name, job_id, salary
FROM employees
WHERE salary >= 10000
OR job_idLIKE ‘%MAN%’;
```
##### NOT 연산자

```
SELECT employee_id, last_name, job_id, salary
FROM employees
WHERE job_idNOT IN (‘IT_PROG’, ‘ST_CLERK’, ‘SA_REP’);
```

##### BETWEEN ... AND ... 연산자
<img width="464" alt="image" src="https://github.com/user-attachments/assets/636b7c6c-96c5-4340-8d5a-8486634675d0" />

##### IN... 연산자
<img width="433" alt="image" src="https://github.com/user-attachments/assets/ca754c97-1dfe-49eb-8332-3e07a2db2b69" />

##### 연산자 우선 순위 : NOT > AND > OR
<img width="398" alt="image" src="https://github.com/user-attachments/assets/45d4a881-6996-494d-b36e-13fa7da5bda9" />

### NULL과 연산자
#### NULL 이란 ?
- 정의
   - Absence of Value
   - 값의 부재 : 값 자체가 없는 상태
      - Unavailable
      - Inapplicable
      - Unassigned
      - Unknown
   - NOT zero, NOT space
- NULL 리터럴
   - Null
   - INSERT, UPDATE에서 주로 사용
   - 문자형 NULL, 날짜형 NULL, 숫자형 NULL
#### NULL 에 대한 연산
##### 산술 및 논리 연산
<img width="669" alt="image" src="https://github.com/user-attachments/assets/7da5cff6-c88f-4b40-8102-a83171b42e83" />

- 비교 연산도 마찬가지로 모두 NULL
- 예외 1
   - IS [NOT] NULL 비교 연산자
      - 값의 유무, 즉 NULL인지 아닌지 판단 -> 결과는 T,F 뿐
      ```
      SELECT last_name, salary, commission_pct
      FROM employees
      WHERE commission_pct IS NULL;
      ```
        
- 예외 2
   - IN 연산자의 멤버 값 중 적어도 하나의 NULL 아닌 경우
     ```
     SELECT last_name, salary, commission_pct
     FROM employees
     WHERE commission_pct IN(0.1,NULL,NULL);
     ```
