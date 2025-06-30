### SQL 개요
#### SQL
- 기능
   - 데이터 절의
   - 데이터 삽입, 갱신 , 삭제
   - 데이터베이스 객체 생성, 변경, 삭제
   - 데이터베이스 및 데이터베이스 객체에 대한 액세스 제어
   - 데이터베이스 일관성 및 무결성 보장
- 특징
   - RDBMS 관리 및 데이터 관리를 위한 AMSI 표준 언어
   - 선언적 언어
   - 인터랙티브 및 인터프리터 언어
   - 
#### SQL 언어 패러다임
<img width="662" alt="image" src="https://github.com/user-attachments/assets/e3d4d28b-6c22-444d-a65f-dfef21ea4aa3" />

#### SQL 처리 단계
<img width="387" alt="image" src="https://github.com/user-attachments/assets/53fb5f23-ba8e-429a-a520-a267445d9ee0" />

#### 공유 풀 체크
<img width="509" alt="image" src="https://github.com/user-attachments/assets/336abe1e-c802-41c2-8adb-f0fa24cd959a" />
- 사용자가 SQL 문 실행
   - 사용자는 클라이언트를 통해 SQL을 날림
- Client Process -> Server Process로 전달
   - 서버 프로세스가 SQL을 받아서 수행 준비를 함.
- PGA에 Private SQL Area 생성
   - PGA 내에 세션별 Private SQL Area가 생기고, 여기에 SQL 문에 대한 정보가 일시적으로 저장됨.
- SGA의 Shared Pool -> Library Cache 확인
   - DB는 SGA의 내부 Shared Pool 내부 Libarary Cache를 조회함.
   - Shared SQL Area에서 동일한 SQL 문이 이미 캐시되어 있는지 확인함.
   - 이 때 SQL의 hash 값을 비교해서 동일 여부를 판단
- Shared SQL Area가 있으면 재사용

#### 비용 기반 옵티마이저
- SQL을 실행하는 최적의 실행 계획 선택
- 실제 일을 계획하고 수행함.
- SQL 처리에 있어서 핵심이다.
- 옵티마이저 구성 요소
   - Query Transformer : 최적화하기 유리한 형태로 SQL문을 변형
   - Estimator : 각 실행계획을 수행하는데 필요한 비용 예측
   - Plan Generator : 주어진 요청을 수행할 수 있는 여러 실행계획을 생성
  
