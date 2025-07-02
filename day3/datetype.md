### 데이터 타입 및 변환 함수
#### 데이터 타입이란 ?
- 데이터 베이스를 저장/표현할 때 적합한 데이터 타입을 지정해야 함.
- 데이터 형, 데이터 유형, 자료형
- 같은 종류의 데이터가 갖는 공통 성질 / 특성
- 데이터 타입이 같은 데이터
   - 성질 / 특성이 같다.
   - 같은 방법으로 다룰 수 있다.
#### 오라클이 지원하는 데이터 타입
<img width="671" alt="image" src="https://github.com/user-attachments/assets/1ef75b3f-612a-47b5-a78e-c7bc4b458450" />

#### 오라클 내장 데이터 타입
##### Character Data Type
- char, varchar2, nchar, nvarchar2
- 고정 길이 vs 가변 길이
   - char 보다는 varchar2 사용 권장
- VARCHAR vs VARCHAR2
   - ANSI 표준 vs 오라클 전용
- National Language Support
   - 유니코드를 지원하지 않는 문자셋을 가진 데이터베이스에서 유니코드를 지원하기 위한 부가적인 문자셋
   - NCHAR, NVARCHAR2, NCLOB
- CHAR
   - 기본 크기 1 byte
- VARHCHAR2
   - 반드시 최대 길이 명시
---
- LONG
- 가변 길이의 텍스트 저장
   - 최대 2기가바이트
- LONG 형의 한계 -> LOB형으로 한계 극복
   - 테이블 당 하나의 칼럼만
   - WHERE 절 및 제약조건에 나타날 수 없음. (NULL, NOT NULL, 제약 조건 예외)
   - GROUP BY, ORDER BY, CONNECT BY, DISTINCT와 같이 사용 불가
   - 함수의 인자, 표현식, 조건식에 사용 불가
   - 정규표현식에 사용불가
   - 인덱스 생성 불가
   - ALTER TABLE ... MOVE 불가
 ---
 ##### Binary Data Types
 - RAW, LONG RAW
   - RAW
      - CHAR 형의 바이너리 버전
      - 크기 지정 필요
      - 최대 크기 : 2000 바이트
   - LONG RAW
      - LONG 형의 바이너리 버전
      - LONG 형의 한계도 그대로 적용
---
##### Number Data Types
<img width="658" alt="image" src="https://github.com/user-attachments/assets/eea0b135-259c-4a2f-a747-0b5fc3ce792d" />

---

##### Datetime Data Types
<img width="623" alt="image" src="https://github.com/user-attachments/assets/92143306-df21-43cc-8ad9-e7003a1f488b" />



