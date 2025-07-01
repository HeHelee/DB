### select 문
#### 정의
- 재료 집합으로부터 원하는 결과집합을 정의/요청/기술하는 문장
#### 기본구조
<img width="509" alt="image" src="https://github.com/user-attachments/assets/7cf9a486-821f-44b7-884a-21886e8dd8e4" />

#### select-list 
- 정의
   - select 절과 from 절 사이
   - 원하는 것과 요구 사항에 맞게 나열
- select-list 에 가능한 요소
   - * 또는 테이블명.*:모든 컬럼
   - 컬럼 이름
   - 리터럴
   - 수식 또는 표현식
   - 함수
   - 스칼라 서브쿼리
  ```
  select ROWNUM, department_id, department_name, manager_id, location_id from departments;
  select ROWNUM, * from departments; -- 에러 (아스타는 홀로 쓰여야 함)
  select ROWNUM, departments.* from departments; 
  ```

#### 식별자
##### 원하는 것의 이름
  - 정의
     - 데이터베이스 객체 이름
     - 컬럼 이름
     - 컬럼 별칭
  - 식별자 지정자 규칙
     - 영문자로 시작해야 함
     - 30 바이트 이하
     - #, $, _을 제외한 특수문자 불가
     - 키보드/예약어 불가
     - 예외 : quoted name 방식
  ```
  CREATE TABLE “from” (
  no NUMBER);
  ```
  ```
  create view annsalvu
  as select last_name, salary, 12*salary as annual
  from employees;
  ```

##### 컬럼 별칭
- 용도
   - 컬럼 헤딩이 너무 길 경우
   - 컬럼 헤딩에 특수 문자가 포함될 경우
   - 계산식에서 유용
   - 뷰 정의하거나 CTAS 방식으로 테이블 생성 시 유용
- 정의 방식 (3가지)
   - 한칸 띄움
   - AS 키워드
   - 큰 따옴표
- 제한
   - 정의는 SELECT 절에서
   - 사용는 ORDER BY 절에서
   - FROM, WHERE, GROUP BY, HAVING, SELECT 절에서는사용불가
```
create table dept90
as select last_name, salary
   from employees
   where department_id = 90;
```

#### 뷰는 별칭을 안붙이면 오류가 나고 테이블은 별칭을 안붙이면 왜 오류가 날까 ?
- 그 이유는 "일회성 쿼리 vs 영구 객체" 의 차이이기 때문이다.
- 테이블 쿼리 (select 문)에서는 별칭이 없어도 된다.
- 왜냐하면 일회성으로 화면에 보여주는 쿼리이고, DBMS는 잠깐 사용하고 버릴 거니까, 칼럼 이름이 애매해도 괜찮다.
- 다만 뷰는 영구 객체이기 때문에 이름이 꼭 필요하다.
- 뷰는 계속 사용할 가상 테이블이기에 다른 쿼리나 프로그램에서 이 뷰를 참조하게 된다.
- 그래서 각 칼럼의 이름이 명확해야 한다.
```
  create view annsalvu
  as select last_name, salary, 12*salary 
  from employees; -- 에러 발생
```

#### 리터럴
- 문자 리터럴
   - 작은 따옴표로 문자열을 감싼다.
   - SQL에서 문자열은 오직 '작은 따옴표'로 표현됨
   - 작음 따옴표 자체를 표현하려면 작은 따옴표를 두번 연속 기술
- 숫자 리터럴
   - 정수
   - 실수
- 날짜 리터럴
   - 작은 따옴표 -> 자동 형변환
      - 세션의 날짜 포맷에 따라
   - 세션의 날짜 포맷과 무관하게 고정된 형식으로 표현하는 방법
      - DATE 'YYYY-MM-DD'
      - TIMESTAMP 'YYYY-MM-DD HH24:MI:SS.FF9'
   - 변환 함수 TO_DATE 사용 : 원하는 형식으로 변환하고 싶을 때
#### DISTINCT
- 목적
   - 쿼리 결과에서 중복 제거
- 용도 및 제한
   - 중복 제거, 범주형 데이터의 레이블 구하기
   - select절에서만, select-list 제일 앞에서만 사용 가능
   - group by 절을 이용해도 같은 결과


