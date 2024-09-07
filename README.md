# [인프런] 비전공자도 이해할 수 있는 MySQL 성능 최적화 입문/실전 (SQL 튜닝편)

<br><br>
## 사전 준비
### MySQL 설치
- 도커로 설치
  - docker pull mysql
- 컨테이너 실행
  - docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=admin -d -p 3306:3306 mysql

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

### 인덱스(Index)란?
- 인덱스(Index)는 데이터베이스 테이블에 대한 검색 성능의 속도를 높여주는 자료 구조를 뜻한다. 
- 데이터를 빨리 찾기 위해 특정 컬럼을 기준으로 미리 정렬해놓은 표.

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
