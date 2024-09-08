# [인프런] 비전공자도 이해할 수 있는 MySQL 성능 최적화 입문/실전 (SQL 튜닝편)

<br><br>
## 사전 준비
### MySQL 설치
- 도커로 설치
  - docker pull mysql
- 컨테이너 실행
  - docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=admin -d -p 3306:3306 mysql
- Ref
  - [MySQL 도커 컨테이너 설치 후 DBeaver 연결하기](https://robomoan.medium.com/mysql-%EB%8F%84%EC%BB%A4-%EC%BB%A8%ED%85%8C%EC%9D%B4%EB%84%88-%EC%84%A4%EC%B9%98-%ED%9B%84-dbeaver-%EC%97%B0%EA%B2%B0%ED%95%98%EA%B8%B0-cf945454cf1e)

<br><br><br>

## 학습정리
### DB 성능 개선할 때 ‘SQL 튜닝’을 가장 먼저 해야 하는 이유
- DB 성능을 개선하는 방법
  - SQL 튜닝
  - 캐싱 서버 활용 (Redis 등)
  - 레플리케이션 (Master/Slave 구조)
  - 샤딩
  - 스케일업 (CPU, Memory, SSD 등 하드웨어 업그레이드)
- ‘SQL 튜닝’을 왜 먼저 고려해야 할까?
  - SQL 튜닝을 제외한 나머지 방법은 추가적인 시스템을 구축해야 한다.
    - 이는 금전적, 시간적 비용이 추가적으로 발생한다.
    - 그에 비해 SQL 튜닝은 기존의 시스템 변경 없이 성능을 개선할 수 있다.
  - 근본적인 문제를 해결하는 방법이 SQL 튜닝일 가능성이 높다.
    - SQL 자체가 비효율적으로 작성됐다면 아무리 시스템적으로 성능을 개선한다고 하더라도 한계가 있다.
    - SQL 튜닝을 통해 기본적으로 성능을 향상시킨다면, 시스템적인 성능 개선이 필요없거나 훨씬 간단한 개선으로 큰 성능 개선 효과를 얻을 수 있다. 

<br>

### 인덱스(Index)란?
- 인덱스(Index)는 데이터베이스 테이블에 대한 검색 성능의 속도를 높여주는 자료 구조를 뜻한다. 
- 데이터를 빨리 찾기 위해 특정 컬럼을 기준으로 미리 정렬해놓은 표.

<br>

### 기본으로 설정되는 인덱스 (PK)
- 기본키 (Primary Key, PK)
  - 테이블에서 특정 데이터를 식별하기 위한 키를 보고 기본키(Primary Key, PK)라고 부른다.
  - PK의 특징 중 하나는 PK를 기준으로 정렬을 해서 데이터를 보관한다.
  - ```
    -- 테이블 생성
    CREATE TABLE users (
        id INT PRIMARY KEY,
        name VARCHAR(100)
    );

    -- 데이터 추가
    INSERT INTO users (id, name) VALUES 
    (1, 'a'),
    (3, 'b'),
    (5, 'c'),
    (7, 'd');

    -- 조회 : 조회결과 PK인 id 순서로 조회된다. (id가 1 > 3 > 5 > 7 순)
    SELECT * FROM users;

    -- id 변경
    UPDATE users
    SET id = 2
    WHERE id = 7;

    -- 조회 : 변경 값에 맞춰 재정렬된 상태로 조회된다. (id가 1 > 2 > 3 > 5 순)
    SELECT * FROM users;
    ```
  - 위의 예시로 봤을 때, id 컬럼을 기준으로 정렬되는 이유는 PK가 인덱스의 일종이기 때문이다.
  - 이렇게 원본 데이터 자체가 정렬되는 인덱스를 보고 클러스터링 인덱스라고 부른다.
- 정리
  - PK에는 인덱스가 기본적으로 적용된다.
  - PK에는 인덱스가 적용되어 있으므로 PK를 기준으로 데이터가 정렬된다.

<br>

### 제약 조건을 추가하면 자동으로 생성되는 인덱스 (UNIQUE)
- MySQL은 UNIQUE 제약 조건을 추가하면 자동으로 인덱스가 생성된다.
- UNIQUE 옵션을 사용하면 인덱스가 같이 생성되기 때문에 조회 성능이 향상된다.
- ```
  -- 테이블 생성 (name에 유니크 설정)
  CREATE TABLE users (
    id INT AUTO_INCREMENT PRIMARY KEY,
    name VARCHAR(100) UNIQUE
  );

  -- 인덱스 확인 (name으로 생성된 인덱스를 확인할 수 있다)
  SHOW INDEX FROM users;
  ```

<br>

### 인덱스를 많이 걸면?
- 인덱스를 사용하면 데이터를 조회할 때의 성능이 향상된다.
- 그러면 인덱스를 무조건적으로 많이 추가하는 게 좋다고 착각할 수도 있다.
- 하지만 인덱스를 추가하면 조회 성능은 올라가지만, 쓰기 작업(삽입, 수정, 삭제)의 성능은 저하된다.
- ```
  -- 테이블 A: 인덱스가 없는 테이블
  CREATE TABLE test_table_no_index (
      id INT AUTO_INCREMENT PRIMARY KEY,
      column1 INT,
      column2 INT,
      column3 INT,
      column4 INT,
      column5 INT,
      column6 INT,
      column7 INT,
      column8 INT,
      column9 INT,
      column10 INT
  );

  -- 테이블 B: 인덱스가 많은 테이블
  CREATE TABLE test_table_many_indexes (
      id INT AUTO_INCREMENT PRIMARY KEY,
      column1 INT,
      column2 INT,
      column3 INT,
      column4 INT,
      column5 INT,
      column6 INT,
      column7 INT,
      column8 INT,
      column9 INT,
      column10 INT
  );

  -- 각 컬럼에 인덱스를 추가
  CREATE INDEX idx_column1 ON test_table_many_indexes (column1);
  CREATE INDEX idx_column2 ON test_table_many_indexes (column2);
  CREATE INDEX idx_column3 ON test_table_many_indexes (column3);
  CREATE INDEX idx_column4 ON test_table_many_indexes (column4);
  CREATE INDEX idx_column5 ON test_table_many_indexes (column5);
  CREATE INDEX idx_column6 ON test_table_many_indexes (column6);
  CREATE INDEX idx_column7 ON test_table_many_indexes (column7);
  CREATE INDEX idx_column8 ON test_table_many_indexes (column8);
  CREATE INDEX idx_column9 ON test_table_many_indexes (column9);
  CREATE INDEX idx_column10 ON test_table_many_indexes (column10);

  -- 데이터 삽입 테스트
  -- 높은 재귀(반복) 횟수를 허용하도록 설정
  SET SESSION cte_max_recursion_depth = 100000; 

  -- 인덱스가 없는 테이블에 데이터 10만개 삽입
  INSERT INTO test_table_no_index (column1, column2, column3, column4, column5, column6, column7, column8, column9, column10)
  WITH RECURSIVE cte AS (
      SELECT 1 AS n
      UNION ALL
      SELECT n + 1 FROM cte WHERE n < 100000
  )
  SELECT
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000)
  FROM cte;

  -- 인덱스가 많은 테이블에 데이터 10만개 삽입
  INSERT INTO test_table_many_indexes (column1, column2, column3, column4, column5, column6, column7, column8, column9, column10)
  WITH RECURSIVE cte AS (
      SELECT 1 AS n
      UNION ALL
      SELECT n + 1 FROM cte WHERE n < 100000
  )
  SELECT
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000),
      FLOOR(RAND() * 1000)
  FROM cte;
  ```

<br>

### 멀티 컬럼 인덱스 (Mulitple-Column Index)란?
- 2개 이상의 컬럼을 묶어서 설정하는 인덱스를 뜻한다.
- 즉, 데이터를 빨리 찾기 위해 2개 이상의 컬럼을 기준으로 미리 정렬해놓은 표이다.
- 예를들어 부서와 이름 컬럼을 활용해 멀티 컬럼 인덱스를 만들었다면, 부서 기준으로 먼저 오름차순으로 정렬한 뒤 부서 내에서 이름을 기준으로 오름차순 정렬을 한다.

<br>

### 멀티 컬럼 인덱스 생성 시 주의점
- 멀티 컬럼 인덱스를 만들어두면 일반 인덱스처럼 활용할 수 있다.
  - id(PK), 부서, 이름을 컬럼으로 가진 테이블에서 '부서', '이름'으로 멀티 컬럼 인덱스를 만들었다고 가정해보자.
  - 위와 같은 멀티 컬럼 인덱스는 부서 인덱스와 동일한 정렬 상태를 갖고 있기 때문에 부서 인덱스를 활용하듯이 쓸 수 있다.
  - 반대로 이름 컬럼 인덱스처럼 활용할 수는 없다.
  - 즉, 멀티 컬럼 인덱스에서 일반 인덱스처럼 활용할 수 있는 건 처음에 배치된 컬럼들뿐이다.
- 멀티 컬럼 인덱스를 구성할 때 ‘대분류 → 중분류 → 소분류’ 컬럼순으로 구성하기
  - 일반적으로 대분류를 먼저 탐색한 뒤, 소분류를 탐색하는 게 빠르기 때문에 위와 같이 컬럼순으로 구성하는 것이 좋다.
  - 멀티 컬럼 인덱스를 구성할 때 데이터 중복도가 높은 컬럼이 앞쪽으로 오는 게 좋다.

<br>

### 커버링 인덱스(Covering Index)란?
- SQL문을 실행시킬 때 필요한 모든 컬럼을 갖고 있는 인덱스를 커버링 인덱스(Covering Index)라고 한다.
- 예시
  - id(PK), name, created_at 컬럼을 가지고 있는 users 테이블이 있다고 가정해보자. (이때 인덱스로는 name을 가지고 있다.)
  - (1) SELECT id, created_at FROM users; 와   
    (2) SELECT id, name FROM users; 를 수행할 때,   
    (1)처럼 id와 create_at 컬럼만 조회한다고 하더라도 실제 테이블의 데이터에 접근해야하지만   
    (2)처럼 id와 name 컬럼만 조회한다고 했을때는 실제 테이블이 아닌 인덱스에만 접근해서 데이터를 알아낼 수 있다.
  - 위와 같은 상황처럼 SQL문을 실행시킬 때 필요한 모든 컬럼을 갖고 있는 인덱스를 보고 커버링 인덱스(Covering Index)라고 표현한다. 

<br>

### 실행 계획
- 실행 계획이란?
  - 옵티마이저가 SQL문을 어떤 방식으로 어떻게 처리할 지를 계획한 걸 의미한다.
  - 이 실행 계획을 보고 비효율적으로 처리하는 방식이 있는 지 점검하고, 비효율적인 부분이 있다면 더 효율적인 방법으로 SQL문을 실행하게끔 튜닝을 하는 게 목표다.
- 실행 계획 확인방법
  - ```
    -- 실행 계획 조회하기
    EXPLAIN [SQL문]

    -- 실행 계획에 대한 자세한 정보 조회하기
    EXPLAIN ANALYZE [SQL문]
    ```
- 실행 계획 조회
  - <img width="1285" alt="image" src="https://github.com/user-attachments/assets/704d33e5-9e0e-404e-b6aa-2dc239cb902a">
  - id : 실행 순서
  - select_type : - (추후 학습)
  - table : 조회한 테이블 명
  - partitions : -
  - type : 테이블의 데이터를 어떤 방식으로 조회하는 지
  - possible keys : 사용할 수 있는 인덱스 목록
  - key : 데이터 조회할 때 실제로 사용한 인덱스 값
  - key_len : -
  - ref : 테이블 조인 상황에서 어떤 값을 기준으로 데이터를 조회했는 지
  - rows : SQL문 수행을 위해 접근하는 데이터의 모든 행의 수 (= 데이터 액세스 수)
    - 이 값을 줄이는 게 SQL 튜닝의 핵심이다
  - filtered : 필터 조건에 따라 어느 정도의 비율로 데이터를 제거했는 지 의미
    - filtered의 값이 30이라면 100개의 데이터를 불러온 뒤 30개의 데이터만 실제로 응답하는데 사용했음을 의미한다.
    - filtered 비율이 낮을 수록 쓸데없는 데이터를 많이 불러온 것.
  - Extra : 부가적인 정보를 제공
    - Ex) `Using where`, `Using index`
- 상세 실행 계획 조회
  - <img width="769" alt="image" src="https://github.com/user-attachments/assets/513274bb-fa2f-4068-831d-4b394f034fb5">
  - 안쪽 레벨(=아래 문장)부터 읽으면 된다.
  - 간략하게 time의 숫자 중 뒤에 위치한 숫자는 해당 쿼리를 실행한 숫자로 이해하면 된다.
    - Table scan이 완료된 시간 = 0.0772ms
    - Filter에는 0.0847이 적혀있는데, 이는 0.0847ms에서 이전 실행시간인 0.0772ms를 빼야지 Filter만 수행할 때 걸린 시간을 구할 수 있다.

<br>

### 실행 계획에서의 Type
- 실행 계획(EXPLAIN)을 조회했을 때 나오는 결과값 중 하나인 type은 성능 최적화에 있어서 굉장히 중요한 값이다.
- 종류
  - ALL
    - ![image](https://github.com/user-attachments/assets/ad3c7a92-bb83-43d6-849d-cc570247408f)
    - 풀 테이블 스캔
    - 풀 테이블 스캔(Full Table Scan)이란 인덱스를 활용하지 않고 테이블을 처음부터 끝까지 전부 다 뒤져서 데이터를 찾는 방식이다.
    - 처음부터 끝까지 전부 다 뒤져서 필요한 데이터를 찾는 방식이다보니 비효율적이다.
  - index
    - ![image](https://github.com/user-attachments/assets/b94546ef-7376-4437-84b1-611159c782a0)
    - 풀 인덱스 스캔
    - 풀 인덱스 스캔(Full Index Scan)이란 인덱스 테이블을 처음부터 끝까지 다 뒤져서 데이터를 찾는 방식이다.
    - 인덱스의 테이블은 실제 테이블보다 크기가 작기 때문에, 풀 테이블 스캔(Full Table Scan)보다 효율적이다.
    - 하지만 인덱스 테이블 전체를 읽어야 하기 때문에 아주 효율적이라고 볼 수는 없다.
  - const
    - ![image](https://github.com/user-attachments/assets/ddef8261-886f-488a-8d5d-915e1b3023d2)
    - 1건의 데이터를 바로 찾을 수 있는 경우
    - 조회하고자 하는 1건의 데이터를 헤매지 않고 단번에 찾아올 수 있을 때 const가 출력된다.
    - 고유 인덱스 또는 기본 키를 사용해서 1건의 데이터만 조회한 경우에 const가 출력된다.
    - 이 방식은 아주 효율적인 방식이다.
  - range
    - ![image](https://github.com/user-attachments/assets/bd1dc195-f615-45a9-9043-727d641e60b0)
    - 인덱스 레인지 스캔(Index Range Scan)은 인덱스를 활용해 범위 형태의 데이터를 조회한 경우를 의미한다.
    - 범위 형태란 `BETWEEN`, `부등호(<, >, ≤, ≥)`, `IN`, `LIKE`를 활용한 데이터 조회를 뜻한다.
    - 이 방식은 인덱스를 활용하기 때문에 효율적인 방식이다.
    - 하지만 인덱스를 사용하더라도 데이터를 조회하는 범위가 클 경우 성능 저하의 원인이 되기도 한다.
  - ref
    - ![image](https://github.com/user-attachments/assets/f00ab948-096b-49a4-a65d-2e3726409e2a)
    - 비고유 인덱스를 사용한 경우 (= UNIQUE가 아닌 컬럼의 인덱스를 사용한 경우) type에 ref가 출력된다.
    - 비고유 인덱스이다보니, 중복되는 값이 있을 수도 있어서 값을 찾고 바로 결과를 반환하는 것이 아니라 계속해서 탐색을 진행하게 된다.
      - 중복되는 값이 있어도 정렬되어있기 때문에 값들이 순차적으로 모여있기는 하다.
  - 그 외
    - eq_ref, index_merge, ref_or_null 등 다양한 타입들이 존재한다.
  - 그림 출처
    - 양바른. 『업무에 바로 쓰는 SQL 튜닝』. 한빛미디어

<br>

### 한 번에 너무 많은 데이터를 조회하는 SQL문 튜닝하기
- ```
  -- 테이블 생성
  CREATE TABLE users (
      id INT AUTO_INCREMENT PRIMARY KEY,
      name VARCHAR(100),
      age INT
  );

  -- 높은 재귀(반복) 횟수를 허용하도록 설정
  SET SESSION cte_max_recursion_depth = 1000000; 

  -- 더미 데이터 삽입 쿼리
  INSERT INTO users (name, age)
  WITH RECURSIVE cte (n) AS
  (
    SELECT 1
    UNION ALL
    SELECT n + 1 FROM cte WHERE n < 1000000
  )
  SELECT 
      CONCAT('User', LPAD(n, 7, '0')),
      FLOOR(1 + RAND() * 1000) AS age
  FROM cte;

  -- 조회
  SELECT * FROM users LIMIT 10000;
  SELECT * FROM users LIMIT 10;
  ```
- 조회결과
  - <img width="616" alt="image" src="https://github.com/user-attachments/assets/62dcaaf1-1576-4f3b-8ed2-92d95177d75e">
  - 10,000건을 조회할 때와 10건을 조회할 때의 시간 차이를 확인해보면 조회하는 데이터의 개수에 따라 성능이 달라지는 것을 볼 수 있다.
  - 조회하는 데이터의 개수가 성능에 많은 영향을 끼치기 때문에 LIMIT, WHERE문 등을 활용해서 한 번에 조회하는 데이터의 수를 줄이는 방법을 고려해볼 필요가 있다.

<br>

### WHERE문이 사용된 SQL문 튜닝하기 - 1
- ```
  CREATE TABLE users (
      id INT AUTO_INCREMENT PRIMARY KEY,
      name VARCHAR(100),
      department VARCHAR(100),
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );

  -- 높은 재귀(반복) 횟수를 허용하도록 설정
  SET SESSION cte_max_recursion_depth = 1000000; 

  -- 더미 데이터 삽입 쿼리
  INSERT INTO users (name, department, created_at)
  WITH RECURSIVE cte (n) AS
  (
    SELECT 1
    UNION ALL
    SELECT n + 1 FROM cte WHERE n < 1000000
  )
  SELECT 
      CONCAT('User', LPAD(n, 7, '0')) AS name,
      CASE 
          WHEN n % 10 = 1 THEN 'Engineering'
          WHEN n % 10 = 2 THEN 'Marketing'
          WHEN n % 10 = 3 THEN 'Sales'
          WHEN n % 10 = 4 THEN 'Finance'
          WHEN n % 10 = 5 THEN 'HR'
          WHEN n % 10 = 6 THEN 'Operations'
          WHEN n % 10 = 7 THEN 'IT'
          WHEN n % 10 = 8 THEN 'Customer Service'
          WHEN n % 10 = 9 THEN 'Research and Development'
          ELSE 'Product Management'
      END AS department,
      TIMESTAMP(DATE_SUB(NOW(), INTERVAL FLOOR(RAND() * 3650) DAY) + INTERVAL FLOOR(RAND() * 86400) SECOND) AS created_at -- 최근 10년 내의 임의의 날짜와 시간 생성
  FROM cte;

  -- 조회
  SELECT * FROM users
  WHERE created_at >= DATE_SUB(NOW(), INTERVAL 3 DAY);

  -- 실행 계획
  EXPLAIN SELECT * FROM users
  WHERE created_at >= DATE_SUB(NOW(), INTERVAL 3 DAY);

  -- 인덱스 생성
  CREATE INDEX idx_created_at ON users (created_at);
  ```
- 조회결과
  - 인덱스 생성 전
    - <img width="1314" alt="image" src="https://github.com/user-attachments/assets/edc4df4d-81a9-416e-b7ae-8a71bc9dff7c">
  - 인덱스 생성 후
    - <img width="1378" alt="image" src="https://github.com/user-attachments/assets/d6ac1db9-863f-4f7d-93b5-846aaba32c7a">
  - created_at으로 인덱스를 생성하여 정렬시킴에 따라 성능이 향상된 것을 볼 수 있다.
    - 소요시간이 단축되었으며, type 또한 ALL에서 range로 변경되었다.
  - WHERE문의 부등호(>, <, ≤, ≥, =), IN, BETWEEN, LIKE와 같은 곳에서 사용되는 컬럼은 인덱스를 사용했을 때 성능이 향상될 가능성이 높다. 

<br>

### WHERE문이 사용된 SQL문 튜닝하기 - 2
- ```
  CREATE TABLE users (
      id INT AUTO_INCREMENT PRIMARY KEY,
      name VARCHAR(100),
      department VARCHAR(100),
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );

  -- 높은 재귀(반복) 횟수를 허용하도록 설정
  SET SESSION cte_max_recursion_depth = 1000000; 
  
  -- 더미 데이터 삽입 쿼리
  INSERT INTO users (name, department, created_at)
  WITH RECURSIVE cte (n) AS
  (
    SELECT 1
    UNION ALL
    SELECT n + 1 FROM cte WHERE n < 1000000
  )
  SELECT 
      CONCAT('User', LPAD(n, 7, '0')) AS name,
      CASE 
          WHEN n % 10 = 1 THEN 'Engineering'
          WHEN n % 10 = 2 THEN 'Marketing'
          WHEN n % 10 = 3 THEN 'Sales'
          WHEN n % 10 = 4 THEN 'Finance'
          WHEN n % 10 = 5 THEN 'HR'
          WHEN n % 10 = 6 THEN 'Operations'
          WHEN n % 10 = 7 THEN 'IT'
          WHEN n % 10 = 8 THEN 'Customer Service'
          WHEN n % 10 = 9 THEN 'Research and Development'
          ELSE 'Product Management'
      END AS department,
      TIMESTAMP(DATE_SUB(NOW(), INTERVAL FLOOR(RAND() * 3650) DAY) + INTERVAL FLOOR(RAND() * 86400) SECOND) AS created_at -- 최근 10년 내의 임의의 날짜와 시간 생성
  FROM cte;
  ```
- 튜닝 전
  - <img width="1309" alt="image" src="https://github.com/user-attachments/assets/f0925eb6-82fb-45d3-9c40-04b61d3c2edd">
    - 대략 200ms 소요.
    - type은 ALL로 풀 테이블 스캔이 일어난 것을 알 수 있다.
  - <img width="1044" alt="image" src="https://github.com/user-attachments/assets/8e6bb177-8b29-4691-9b64-7d1c112baa74">
    - rows의 1e+6은 10의 6승을 의미한다.
- 튜닝 후
  - 성능 향상을 위해 인덱스를 생성할 때, department / created_at / 멀티 컬럼 인덱스(순서도 고려)를 고민해봐야한다.
    - CREATE INDEX idx_created_at ON users (created_at);
      - 30ms 소요
      - type = range
      - rows = 1,000
    - CREATE INDEX idx_department ON users (department);
      - 130ms 소요
      - type = ref
      - rows = 191,000
      - created_at으로 접근했을 때보다 department로 접근했을 때의 데이터가 수가 많다보니 더 많은 시간이 소요된 것이다.
    - created_at와 department 각 각 생성
      - 30ms 소요
      - type = range
      - possible_key = idx_department, idx_created_at : 2개의 인덱스를 사용할 수 있다.
      - key = idx_created_at : 하지만 실제 사용된 인덱스는 idx_created_at다.
      - row = 1,000
      - 실제 성능향상에 도움이 된 인덱스는 idx_created_at이기 때문에, 현재 예시에서는 굳이 2개의 인덱스를 만들 필요가 없다.
        - 불필요하게 2개의 인덱스를 모두 생성할 시, 쓰기 작업에서 성능이 저하될 수 있기 때문에 필요한 인덱스만 만드는 것이 중요하다.
        - 데이터 액세스(rows)를 크게 줄일 수 있는 컬럼은 중복 정도가 낮은 컬럼이다.
        - 따라서 중복 정도가 낮은 컬럼을 골라서 인덱스를 생성하는 것이 좋다.
    - CREATE INDEX idx_created_at_department ON users (created_at, department); -- 멀티 컬럼 인덱스
      - 25ms 소요 (created_at, department 컬럼의 순서를 바꿔 생성하여도 성능은 비슷)
      - type = range
      - rows = 1,000
      - 단일 컬럼 인덱스와의 성능 차이가 크지 않다면, 최소한의 컬럼으로 인덱스를 생성하는 것이 좋으므로 단일 컬럼 인덱스를 선택하는 것이 좋다.

<br>

### 인덱스를 걸었는데도 인덱스가 작동하지 않는 경우 - 1
- ```
  -- 테이블 생성
  CREATE TABLE users (
      id INT AUTO_INCREMENT PRIMARY KEY,
      name VARCHAR(100),
      age INT
  );

  -- 높은 재귀(반복) 횟수를 허용하도록 설정
  SET SESSION cte_max_recursion_depth = 1000000; 

  -- 더미 데이터 삽입 쿼리
  INSERT INTO users (name, age)
  WITH RECURSIVE cte (n) AS
  (
    SELECT 1
    UNION ALL
    SELECT n + 1 FROM cte WHERE n < 1000000
  )
  SELECT 
      CONCAT('User', LPAD(n, 7, '0')),
      FLOOR(1 + RAND() * 1000) AS age
  FROM cte;

  -- 인덱스 생성
  CREATE INDEX idx_name ON users (name);

  -- 실행계획 조회
  EXPLAIN SELECT * FROM users 
  ORDER BY name DESC;
  ```
- 실행결과
  - <img width="1287" alt="image" src="https://github.com/user-attachments/assets/00f6d8c0-fb88-47ce-8fe9-02af02e97c05">
  - type이 ALL 인 것으로 보아 인덱스가 작동하지 않는 것을 볼 수 있다.
  - SELECT * 로 작성했기 때문에 옵티마이저는 넓은 범위의 데이터를 조회할 때는 인덱스를 활용하는 것보다 풀 테이블 스캔이 더 효율적이라 판단하여 이와 같은 계획이 나온 것이다.
    - 즉, 굳이 인덱스를 거쳤다가 각 원래 테이블의 데이터를 일일이 하나씩 찾아내는 것보다, 바로 원래 테이블에 접근해서 모든 데이터를 통째로 가져와서 정렬하는 게 효율적이라고 판단한 것이다.
    - 실제 성능상으로도 풀 테이블 스캔을 통해 데이터를 가져오는 게 효율적이다. 

<br>

### 인덱스를 걸었는데도 인덱스가 작동하지 않는 경우 - 2
- ```
  -- 테이블 생성
  CREATE TABLE users (
      id INT AUTO_INCREMENT PRIMARY KEY,
      name VARCHAR(100),
      salary INT,
      created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP
  );

  -- 높은 재귀(반복) 횟수를 허용하도록 설정
  SET SESSION cte_max_recursion_depth = 1000000; 

  -- 더미 데이터 삽입 쿼리
  INSERT INTO users (name, salary, created_at)
  WITH RECURSIVE cte (n) AS
  (
    SELECT 1
    UNION ALL
    SELECT n + 1 FROM cte WHERE n < 1000000 -- 생성하고 싶은 더미 데이터의 개수
  )
  SELECT 
      CONCAT('User', LPAD(n, 7, '0')) AS name,  -- 'User' 다음에 7자리 숫자로 구성된 이름 생성
      FLOOR(1 + RAND() * 1000000) AS salary,    -- 1부터 1000000 사이의 난수로 급여 생성
      TIMESTAMP(DATE_SUB(NOW(), INTERVAL FLOOR(RAND() * 3650) DAY) + INTERVAL FLOOR(RAND() * 86400) SECOND) AS created_at -- 최근 10년 내의 임의의 날짜와 시간 생성
  FROM cte;

  -- 인덱스 생성
  CREATE INDEX idx_name ON users (name);
  CREATE INDEX idx_salary ON users (salary);
  ```
- 쿼리 실행
  ```
  # User000000으로 시작하는 이름을 가진 유저 조회
  EXPLAIN SELECT * FROM users
  WHERE SUBSTRING(name, 1, 10) = 'User000000';
  
  # 2달치 급여(salary)가 1000 이하인 유저 조회
  SELECT * FROM users
  WHERE salary * 2 < 1000
  ORDER BY salary;
  ```
- 쿼리 실행 결과
  - 2개의 쿼리 모두 인덱스를 활용하지 않고 풀 테이블 스캔으로 탐색하는 걸 확인할 수 있다.
  - SQL문을 작성할 인덱스 컬럼을 가공(함수 적용, 산술 연산, 문자역 조작 등)하면, MySQL은 해당 인덱스를 활용하지 못하는 경우가 많다.
  - 따라서 인덱스를 적극 활용하기 위해서는 인덱스 컬럼 자체를 최대한 가공하지 않아야 한다.
  - 인덱스 컬럼을 가공하지 않고 사용하도록 쿼리를 튜닝하는 것이 해결방법이다.
- 수정된 쿼리 실행
  ```
  # User000000으로 시작하는 이름을 가진 유저 조회
  EXPLAIN SELECT * FROM users
  WHERE name LIKE 'User000000%';

  # 2달치 급여(salary)가 1000 이하인 유저 조회
  EXPLAIN SELECT * FROM users
  WHERE salary < 1000 / 2
  ORDER BY salary;
  ```
