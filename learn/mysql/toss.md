# [인프런] 5천억건이 넘는 금융 데이터를 처리하는 토스 개발자에게 배우는 MySQL

<br><br>

## 학습정리
### 글로벌 환경설정
- ```
  -- 문자셋 관련 설정 전체 조회 (server, database, client, connection 등)
  SHOW VARIABLES LIKE 'character_set%';
  
  -- 문자열 정렬 및 비교 규칙(collation) 관련 설정 조회
  SHOW VARIABLES LIKE 'collation%';

  -- InnoDB 스토리지 엔진이 사용하는 버퍼 풀 크기 조회
  SHOW VARIABLES LIKE 'innodb_buffer_pool_size';
  
  -- 동시에 접속 가능한 최대 클라이언트 수 조회
  SHOW VARIABLES LIKE 'max_connections'; 
  
  -- 현재 MySQL 서버에 접속해 있는 클라이언트의 수
  SHOW STATUS LIKE 'Threads_connected';
  
  -- 서버가 마지막으로 시작 된 후부터 지금까지 경과된 시간 (초단위)
  SHOW STATUS LIKE 'Uptime';
  
  -- InnoDB / MyISAM 메모리 설정 값을 MB 단위로 조회
  SELECT
      (@@innodb_buffer_pool_size / 1024 / 1024) AS buffer_pool_mb,
      (@@key_buffer_size / 1024 / 1024) AS key_buffer_mb;
  
  -- 연결 수 조정 (즉시 적용, 재시작 시 my.cnf 설정이 우선)
  SET GLOBAL max_connections = 1000;
  
  -- InnoDB 버퍼 풀 크기 설정 (일반적으로 재시작 필요)
  SET GLOBAL innodb_buffer_pool_size = 4294967296;  -- 4GB
  
  -- max_connections 설정 변경 여부 확인
  SHOW VARIABLES LIKE 'max_connections';
  
  -- 글로벌 타임존과 현재 세션 타임존 확인
  SELECT @@global.time_zone, @@session.time_zone;
  
  -- MySQL 서버 글로벌 타임존을 KST(+09:00)로 설정 (신규 세션부터 적용)
  SET GLOBAL time_zone = '+09:00';  -- KST
  
  -- 데이터베이스별 기본 문자셋 및 콜레이션 조회
  SELECT
      SCHEMA_NAME,
      DEFAULT_CHARACTER_SET_NAME,
      DEFAULT_COLLATION_NAME
  FROM information_schema.SCHEMATA;
  
  -- 슬로우 쿼리 로그 활성화
  SET GLOBAL slow_query_log = 'ON';
  
  -- 실행 시간이 2초 이상인 쿼리를 슬로우 쿼리로 기록
  SET GLOBAL long_query_time = 2; -- 2초 이상
  
  -- 에러 로그, 일반 로그, 슬로우 로그 등 로그 관련 설정 전체 확인
  SHOW VARIABLES LIKE '%log%';
  ```

### 접근관리
- ```
  -- 데이터 베이스 생성
  -- utf8mb4: 이모지 및 다국어(한글, 영어, 특수문자)까지 모두 지원
  -- utf8mb4_unicode_ci: 유니코드 표준 기반 정렬 규칙 (대소문자/악센트 구분 없음)
  CREATE DATABASE financial_app
      CHARACTER SET utf8mb4
      COLLATE utf8mb4_unicode_ci;
  
  -- 데이터 베이스 확인
  -- 현재 MySQL 서버에 존재하는 모든 데이터베이스 목록 조회
  SHOW DATABASES;
  
  -- 데이터베이스 정보 상세 확인
  -- 생성된 데이터베이스의 기본 문자셋과 콜레이션이
  -- 애플리케이션 요구사항(utf8mb4 / utf8mb4_unicode_ci)과 일치하는지 검증
  SELECT
      SCHEMA_NAME,
      DEFAULT_CHARACTER_SET_NAME,
      DEFAULT_COLLATION_NAME
  FROM information_schema.SCHEMATA
  WHERE SCHEMA_NAME = 'financial_app';
  
  -- 데이터베이스 사용
  -- 이후 실행되는 쿼리의 기본 대상 데이터베이스 지정
  USE financial_app;
  
  -- 현재 세션의 기본 문자셋 / 콜레이션 설정
  -- DB, 테이블, 컬럼 생성 시 별도 지정이 없을 경우 기본값으로 사용됨
  SET NAMES utf8mb4 COLLATE utf8mb4_unicode_ci;
  
  -- 애플리케이션용 사용자 생성
  -- localhost: DB 서버 내부에서만 접속 가능한 계정 (보안 강화 목적)
  CREATE USER 'app_user'@'localhost' IDENTIFIED BY 'secure_password';
  
  -- % : 모든 외부 IP에서의 원격 접속 허용
  -- 실제 운영 환경에서는 특정 IP(예: '10.0.0.%', '123.123.123.10')로 제한하는 것이 권장됨
  -- 방화벽 / 보안 그룹 설정과 함께 사용해야 안전함
  CREATE USER 'app_user'@'%' IDENTIFIED BY 'secure_password';

  -- 사용자 목록 확인
  -- 생성된 사용자와 허용된 접속 Host 확인
  SELECT User, Host FROM mysql.user;
  
  -- 애플리케이션 사용자 권한 부여
  -- financial_app 데이터베이스에 대해서만 CRUD 권한 부여
  -- DDL(CREATE, DROP, ALTER) 권한은 포함하지 않아 운영 안정성 확보
  GRANT SELECT, INSERT, UPDATE, DELETE
  ON financial_app.*
  TO 'app_user'@'%';

  -- 권한 확인
  -- 실제로 부여된 권한을 SQL 형태로 확인
  SHOW GRANTS FOR 'app_user'@'%';
  
  -- 권한 적용
  -- 사용자 및 권한 변경 사항을 즉시 반영
  FLUSH PRIVILEGES; 
  ```

### 성능지표
- ```
  -- 연결 상태 상세 정보
  SELECT ID, USER, HOST, DB, COMMAND, TIME, STATE, LEFT(INFO, 100) as QUERY_SNIPPET
  FROM information_schema.PROCESSLIST
  WHERE COMMAND != 'Sleep'
  ORDER BY TIME DESC;

  /*
      버퍼 풀 히트율(Buffer Pool Hit Ratio) 설명
  
      - 버퍼 풀(Buffer Pool)이란?
        InnoDB 스토리지 엔진이 자주 사용하는 데이터 페이지와 인덱스를
        디스크가 아닌 메모리에 캐싱해두는 영역이다.
        메모리에서 데이터를 읽을 수 있으면 디스크 I/O를 피할 수 있어
        쿼리 성능에 매우 큰 영향을 준다.
  
      - 히트(Hit)와 미스(Miss)
        Hit  : 필요한 데이터가 이미 Buffer Pool에 존재하여 메모리에서 바로 조회되는 경우
        Miss : Buffer Pool에 데이터가 없어 디스크에서 직접 읽어오는 경우 (I/O 발생)
  
      - 사용되는 상태 변수 의미
        Innodb_buffer_pool_read_requests
          : InnoDB가 데이터를 읽기 위해 Buffer Pool을 조회한 전체 요청 횟수
  
        Innodb_buffer_pool_reads
          : Buffer Pool에 데이터가 없어 실제 디스크에서 읽은 횟수
  
      - 히트율 계산 방식
        Hit Ratio = 1 - (디스크 읽기 횟수 / 전체 읽기 요청 횟수)
  
      - 수치 해석 기준 (일반적인 운영 환경)
        99% 이상 : 매우 양호, 메모리 캐시가 충분히 동작 중
        95~99%   : 정상 범위, 대부분의 서비스에서 목표로 하는 수준
        90~95%   : 트래픽 증가 시 성능 저하 가능성 존재
        90% 미만 : Buffer Pool 크기 조정 또는 쿼리 튜닝 필요
  
      - 주의 사항
        서버 기동 직후나 트래픽이 적은 상태에서는 수치가 낮게 나올 수 있다.
        충분한 트래픽이 유입된 이후의 값을 기준으로 판단해야 한다.
  */
  SELECT ROUND(
     (1 - (
         (SELECT VARIABLE_VALUE FROM performance_schema.global_status WHERE VARIABLE_NAME = 'Innodb_buffer_pool_reads') /
         (SELECT VARIABLE_VALUE FROM performance_schema.global_status WHERE VARIABLE_NAME = 'Innodb_buffer_pool_read_requests')
         )) * 100, 2
  ) AS buffer_pool_hit_ratio_percent; 
  ```

### Database 설계
- 실무에서는 정규화된 설계보다 성능을 위하여 비정규화된 설계를 선택하기도한다.
  - ```
    /*
        완전 정규화된 주문 설계 (조인이 많이 필요)
    
        - 데이터 중복을 최소화한 정규화 구조
        - 주문(order)과 주문 항목(order_items)을 분리
        - 데이터 정합성은 높지만
          → 조회 시 조인이 많아져 성능 비용 발생
        - 데이터 분석, 관리 중심 시스템에 적합
    */
    CREATE TABLE orders (
        order_id BIGINT AUTO_INCREMENT PRIMARY KEY,
        user_id BIGINT NOT NULL,
        status ENUM('PENDING', 'CONFIRMED', 'SHIPPED', 'DELIVERED') NOT NULL,
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,

        FOREIGN KEY (user_id) REFERENCES users(id)
    );
    
    CREATE TABLE order_items (
        item_id BIGINT AUTO_INCREMENT PRIMARY KEY,
        order_id BIGINT NOT NULL,
        product_id BIGINT NOT NULL,
        quantity INT NOT NULL,
        unit_price DECIMAL(10,2) NOT NULL,

        FOREIGN KEY (order_id) REFERENCES orders(order_id)
    );
    
    
    
    /*
        실무에서 자주 사용하는 비정규화 주문 설계 (성능 우선)
    
        - 조회 성능과 운영 편의성을 우선
        - 주문 시점의 데이터를 스냅샷 형태로 저장
        - 사용자 정보 변경과 무관하게 주문 이력 유지 가능
        - 조인 없이 주문 단독 조회가 가능하여 트래픽에 유리
    */
    CREATE TABLE orders (
        order_id BIGINT AUTO_INCREMENT PRIMARY KEY,
        user_id BIGINT NOT NULL,
    
        -- 주문 정보 (변경 불가능한 스냅샷)
        total_amount DECIMAL(12,2) NOT NULL,
        item_count INT NOT NULL,
    
        -- 사용자 정보 복제 (배송용)
        customer_name VARCHAR(100) NOT NULL,
        customer_email VARCHAR(255) NOT NULL,
        shipping_address TEXT NOT NULL,
    
        -- 상태 관리
        status ENUM('PENDING', 'CONFIRMED', 'SHIPPED', 'DELIVERED') NOT NULL,
    
        -- 시간 정보
        created_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP,
        updated_at TIMESTAMP DEFAULT CURRENT_TIMESTAMP ON UPDATE CURRENT_TIMESTAMP,
    
        -- 성능 최적화 인덱스
        INDEX idx_user_status (user_id, status),
        INDEX idx_created_at (created_at),
        INDEX idx_status (status)
    ) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_unicode_ci; 
    ```

### 파티셔닝 전략
- 정리
  - MySQL 파티셔닝(Partitioning)
    - 하나의 테이블을 논리적으로 유지하면서 물리적으로는 여러 파티션으로 나누어 데이터를 저장하는 기능
    - 애플리케이션 관점에서는 하나의 테이블로 보이고 내부적으로만 데이터가 분리되어 저장됨
  
  - 파티셔닝을 사용하는 이유
    - 대용량 테이블에서 불필요한 데이터 스캔을 줄이기 위함
    - 인덱스 크기 증가로 인한 성능 저하를 완화하기 위함
    - 오래된 데이터의 삭제 및 아카이빙을 쉽게 관리하기 위함
  
  - 파티션 키(Partition Key)
    - 데이터를 나누는 기준이 되는 컬럼
    - 대표적인 예시는 created_at, order_date, user_id
    - 파티션 키를 기준으로 데이터가 특정 파티션에 저장됨
  
  - 파티션 프루닝(Partition Pruning)
    - 파티셔닝의 핵심 성능 최적화 기능
    - 쿼리 조건을 분석하여 불필요한 파티션은 읽지 않고 필요한 파티션만 접근하는 방식
  
  - 프루닝이 동작하는 경우
    - WHERE 조건에 파티션 키가 직접 사용됨
    - MySQL이 조건을 보고 접근해야 할 파티션을 사전에 판단 가능
    - 디스크 I/O 감소와 조회 성능 향상 효과 발생
  
  - 프루닝이 동작하지 않는 경우
    - 파티션 키에 함수가 적용된 경우 예 DATE(created_at), YEAR(created_at)
    - 파티션 키가 WHERE 조건에 포함되지 않은 경우
    - 모든 파티션을 스캔하게 되어 성능 이점이 사라짐
  
  - 파티셔닝 방식 예시
    - RANGE 파티셔닝은 날짜나 숫자 범위 기준으로 분할
    - LIST 파티셔닝은 특정 값 목록 기준으로 분할
    - HASH 파티셔닝은 데이터 균등 분산 목적
  
  - 파티셔닝이 효과적인 경우
    - 로그 테이블
    - 주문 및 결제 이력 테이블
    - 이벤트성 데이터
    - 기간 조건이 항상 포함되는 조회 패턴
- ```
  -- 현재 파티션 상태 확인
  SELECT
      PARTITION_NAME,
      PARTITION_EXPRESSION,
      PARTITION_DESCRIPTION,
      TABLE_ROWS,
      ROUND(DATA_LENGTH / 1024 / 1024, 2) as data_size_mb,
      ROUND(INDEX_LENGTH / 1024 / 1024, 2) as index_size_mb
  FROM information_schema.partitions
  WHERE table_schema = 'financial_master_class'
    AND table_name = 'stock_trades'
    AND PARTITION_NAME IS NOT NULL
  ORDER BY PARTITION_ORDINAL_POSITION;
    
  -- 파티션별 성능 분석
  SELECT
      PARTITION_NAME,
      ROUND(DATA_LENGTH / (1024 * 1024 * 1024), 2) as data_size_gb,
      TABLE_ROWS,
      ROUND(TABLE_ROWS / (DATA_LENGTH / 1024), 2) as rows_per_kb,
      CASE
          WHEN TABLE_ROWS > 50000000 THEN 'VERY_LARGE'
          WHEN TABLE_ROWS > 10000000 THEN 'LARGE'
          WHEN TABLE_ROWS > 1000000 THEN 'MEDIUM'
          ELSE 'SMALL'
          END as partition_size_category
  FROM information_schema.partitions
  WHERE table_schema = 'financial_master_class'
    AND table_name = 'stock_trades'
    AND PARTITION_NAME IS NOT NULL;
  ```

### 인덱스 최적화 설계기법
- ```
  /*
    좋은 인덱스 설계

    - 선택도(selectivity)가 높은 user_id를 인덱스의 첫 컬럼으로 배치하여
      특정 사용자 기준 조회 시 검색 범위를 가장 빠르게 줄일 수 있음

    - 자주 사용되는 동등 조건(=) 컬럼(user_id, status)을 앞에 두고
      범위 조건으로 사용되는 created_at을 뒤에 배치함으로써
      Left-most prefix rule을 최대한 활용할 수 있는 구조

    - 이 인덱스 하나로 다음 조회 패턴들을 모두 효율적으로 처리 가능
      user_id 단독 조회
      user_id + status 조회
      user_id + status + created_at 범위 조회

    - 실제 서비스에서 가장 빈도가 높은 조회 패턴을 기준으로 한
      실무 친화적인 인덱스 설계 예시
  */
  CREATE INDEX idx_orders_user_status ON orders(user_id, status, created_at);
  
  
  /*
    email + status 복합 인덱스 설명 (카디널리티 개념 포함)

    - 카디널리티(cardinality)란
      컬럼이 가질 수 있는 값의 "서로 다른 값의 개수"를 의미함
      값의 종류가 많을수록 카디널리티가 높고
      값의 종류가 적을수록 카디널리티가 낮다고 표현함

    - email은 사용자마다 고유하거나 거의 겹치지 않는 값이므로
      매우 높은 카디널리티를 가지는 컬럼임
      → 조건에 사용되면 전체 데이터 중 극히 일부 행만 빠르게 좁힐 수 있음

    - status는 active / inactive / pending 처럼
      값의 종류가 제한적인 낮은 카디널리티 컬럼임
      → 단독으로는 필터링 효과가 약함

    - 따라서 복합 인덱스에서는
      높은 카디널리티 컬럼(email)을 선두 컬럼으로 두어
      먼저 검색 범위를 크게 줄이고
      그 다음 낮은 카디널리티 컬럼(status)으로 추가 필터링하는 구조가 가장 효율적임

    - 이 인덱스 구성은
      email 단독 조건
      email + status 조건
      두 경우 모두 인덱스를 효과적으로 활용할 수 있음

    - 반대로 status를 앞에 두면
      인덱스 스캔 범위가 넓어져
      디스크 I/O 증가 및 성능 저하로 이어질 수 있음
  */
  CREATE INDEX idx_users_email_status ON users(email, status);
  
  /*
    title 접두사(prefix) 인덱스 설명

    - title 컬럼이 VARCHAR/TEXT 처럼 길이가 긴 경우
      전체 길이를 인덱싱하면 인덱스 크기가 커지고 성능 및 메모리 효율이 저하됨

    - 자주 검색에 사용되는 앞부분만 잘라 인덱싱하면
      인덱스 크기를 줄이면서도 검색 성능을 확보할 수 있음

    - (title(20))은 title의 앞 20자만 인덱스로 사용한다는 의미이며
      실제 데이터 분포를 기준으로 중복이 과도하지 않은 길이를 선택하는 것이 중요함

    - LIKE 'prefix%' 형태의 검색에서 특히 효과적이며
      '%keyword%' 와 같은 중간 검색에는 인덱스 활용이 제한됨
  */
  CREATE INDEX idx_articles_title_prefix ON articles(title(20));
  ```

### 복잡한 서비스 데이터를 위한 SELECT 고급화 기법
- EXISTS와 IN의 차이
  - ```
    -- EXISTS
    SELECT username
    FROM users u
    WHERE EXISTS (
        SELECT 1 FROM posts p WHERE p.user_id = u.user_id
    );
    
    -- IN
    SELECT username
    FROM users u
    WHERE u.user_id IN (
        SELECT user_id FROM posts
    );
    ```
  - EXISTS
    - 서브쿼리에서 값이 존재하는지만 확인
    - 조건을 만족하는 행을 하나라도 찾으면 `즉시 종료`
    - 대용량 데이터에서 유리
    - NULL 값의 영향을 받지 않음
    - 옵티마이저가 세미 조인으로 최적화하기 쉬움
  - IN
    - 서브쿼리 결과를 집합으로 생성 후 비교
    - 결과 집합이 클수록 메모리 및 처리 비용 증가
    - 서브쿼리에 NULL 이 포함되면 결과가 달라질 수 있음
    - 소량의 고정된 결과일 때는 큰 문제 없음
  - 성능 관점 정리
    - 데이터가 많고 중복이 많을수록 EXISTS 가 유리
    - 실무에서는 EXISTS 를 기본 선택으로 사용하는 것이 안전함

### UPDATE & DELETE 완벽 가이드
- ALTER TABLE logs DROP PARTITION p_202301;
  - 파티셔닝된 테이블에서 특정 파티션을 제거하는 DDL 쿼리
- DELETE와의 차이
  - DELETE
    - 조건에 맞는 행을 하나씩 삭제
    - 트랜잭션 로그(undo/redo) 발생
    - 대용량 데이터에서 매우 느림
  - DROP PARTITION
    - 파티션 단위로 즉시 제거
    - 내부 데이터 파일 자체를 제거
    - 대용량 데이터에서도 매우 빠름
- 주의 사항
  - DDL이므로 롤백 불가

### MySQL의 내부 아키텍처와 스토리지 엔진
- 내부 아키텍처
  - Client / Connection Layer (접속 계층)
    - 클라이언트 연결 요청 처리
    - 사용자 인증 및 권한 확인
    - 세션 생성 및 연결 관리
  - SQL Interface Layer (SQL 처리 계층)
    - SQL 문법 파싱
    - 쿼리 유효성 검사
    - 접근 권한 체크
  - Optimizer Layer (쿼리 최적화 계층)
    - 실행 계획(Execution Plan) 생성
    - 인덱스 선택
    - 조인 순서 및 방식 결정
  - Execution Engine Layer (실행 엔진 계층)
    - 실행 계획에 따라 쿼리 수행
    - 스토리지 엔진에 데이터 요청
  - Storage Engine Layer (스토리지 엔진 계층)
    - 실제 데이터 저장 및 조회
    - 인덱스 관리
    - 트랜잭션 및 락 처리
  - OS / File System Layer (운영체제 계층)
    - 디스크 I/O 처리
    - 파일 시스템 관리
    - 메모리 및 캐시 관리
- 스토리지 엔진
  - InnoDB
    - 기본 스토리지 엔진
    - 트랜잭션 지원 (ACID)
    - Row-level Lock 지원
  - MyISAM
    - 트랜잭션 미지원
    - Table-level Lock 사용
  - 사용 중인 스토리지 엔진 확인
    ```
    SELECT
        TABLE_SCHEMA as 데이터베이스,
        TABLE_NAME as 테이블명,
        ENGINE as 스토리지엔진,
        ROUND((DATA_LENGTH + INDEX_LENGTH) / 1024 / 1024, 2) as 크기_MB
    FROM information_schema.TABLES
    WHERE TABLE_SCHEMA = DATABASE()
    ORDER BY (DATA_LENGTH + INDEX_LENGTH) DESC;
    ```
- InnoDB 버퍼 풀
  - InnoDB 스토리지 엔진에서 사용하는 핵심 메모리 영역
  - 데이터와 인덱스 페이지를 메모리에 캐시하여 디스크 I/O를 최소화
  - 조회 성능에 직접적인 영향을 미침
  - 디스크에서 읽은 페이지를 버퍼 풀에 적재 후 재사용
  - 변경된 데이터는 즉시 디스크에 쓰지 않고 버퍼 풀에서 관리
  - 주요 지표
    - HIT RATE
      - 메모리에서 바로 조회된 비율
      - 값이 높을수록 디스크 접근이 적음
    - FREE BUFFERS
      - 사용되지 않은 여유 페이지 수
    - MODIFIED DATABASE PAGES
      - 수정되었지만 아직 디스크에 반영되지 않은 페이지 수
  - 관련 설정
    - innodb_buffer_pool_size
      - 버퍼 풀 전체 크기 설정
  - 버퍼 풀 기본 정보 확인하기
    - ```
      SELECT
          POOL_SIZE as 전체페이지수,
          ROUND(POOL_SIZE * 16384 / 1024 / 1024, 0) as 전체크기_MB,
          FREE_BUFFERS as 빈페이지수,
          DATABASE_PAGES as 데이터페이지수,
          MODIFIED_DATABASE_PAGES as 수정된페이지수,
          ROUND(HIT_RATE, 2) as 히트율_퍼센트
      FROM information_schema.INNODB_BUFFER_POOL_STATS;
      ```
- 로그 버퍼
  - 트랜잭션 변경 로그(Redo Log)를 임시로 저장하는 메모리 영역
  - 디스크에 바로 기록하지 않고 메모리에 먼저 저장
  - 디스크 I/O 감소를 통한 성능 향상 목적 
  - 로그 버퍼 상태 확인
    - ```
      SELECT
          '로그 버퍼 크기(MB)' as 항목,
          @@innodb_log_buffer_size / 1024 / 1024 as 값
      
      UNION ALL
      
      SELECT
          '로그 대기 횟수',
          (SELECT VARIABLE_VALUE FROM performance_schema.global_status
           WHERE VARIABLE_NAME = 'Innodb_log_waits')
      
      UNION ALL
      
      SELECT
          '로그 쓰기 요청',
          (SELECT VARIABLE_VALUE FROM performance_schema.global_status
           WHERE VARIABLE_NAME = 'Innodb_log_write_requests')
      
      UNION ALL
      
      SELECT
          '실제 로그 쓰기',
          (SELECT VARIABLE_VALUE FROM performance_schema.global_status
           WHERE VARIABLE_NAME = 'Innodb_log_writes');
      ```

### 메모리와 트랜잭션 및 락 메커니즘
- 성능의 핵심은 메모리
  - 디스크보다 메모리 접근 속도가 압도적으로 빠름
  - InnoDB는 버퍼 풀을 통해 메모리에서 데이터 조회를 우선 시도
  - 버퍼 풀 히트율이 높을수록 디스크 I/O가 줄어들어 성능이 향상됨
  - 히트율 하락은 성능 저하의 직접적인 신호
  - ```
    -- 버퍼 풀 히트율 확인하기 (95% 이상이면 좋음)
    SELECT
        '버퍼 풀 성능 분석' as 분석항목,
        bp_read_requests.VARIABLE_VALUE as 전체요청수,
        bp_reads.VARIABLE_VALUE as 디스크읽기수,
        ROUND(
                (1 - bp_reads.VARIABLE_VALUE / bp_read_requests.VARIABLE_VALUE) * 100, 2
        ) as 히트율_퍼센트,
        CASE
            WHEN (1 - bp_reads.VARIABLE_VALUE / bp_read_requests.VARIABLE_VALUE) * 100 >= 95
                THEN '👍 매우 좋음'
            WHEN (1 - bp_reads.VARIABLE_VALUE / bp_read_requests.VARIABLE_VALUE) * 100 >= 90
                THEN '😊 양호'
            WHEN (1 - bp_reads.VARIABLE_VALUE / bp_read_requests.VARIABLE_VALUE) * 100 >= 80
                THEN '😐 보통'
            ELSE '😱 개선 필요'
            END as 상태
    FROM
        (SELECT VARIABLE_VALUE FROM performance_schema.global_status
         WHERE VARIABLE_NAME = 'Innodb_buffer_pool_reads') bp_reads,
        (SELECT VARIABLE_VALUE FROM performance_schema.global_status
         WHERE VARIABLE_NAME = 'Innodb_buffer_pool_read_requests') bp_read_requests;
    ```
- 락 메커니즘
  - 테이블 락 (Table Lock)
    - 테이블 전체에 락을 설정
    - 동시성은 낮지만 구조가 단순함
  - 갭 락 (Gap Lock)
    - 인덱스의 범위(값과 값 사이)에 락을 설정
    - 동일 범위에 새로운 데이터 삽입을 방지
  - Exclusive Lock (X Lock)
    - 데이터 수정 시 사용하는 락
    - 다른 트랜잭션의 읽기/쓰기 접근을 차단
  - 읽기 락 (Shared Lock, S Lock)
    - 데이터 조회 시 사용하는 락
    - 다른 트랜잭션의 읽기는 허용, 쓰기는 차단

### Replication & Distribution
- Replication
  - 읽기 성능 관점에서의 Replication 
    - 읽기 요청의 부하를 분산하기 위해 사용
    - Master는 쓰기(INSERT, UPDATE, DELETE) 처리
    - Replica(Slave)는 읽기(SELECT) 요청 처리
    - 읽기 트래픽을 여러 Replica로 분산하여 응답 속도 향상
    - 읽기 부하 증가 시 Replica를 추가하여 수평 확장 가능
    - 읽기와 쓰기를 분리하여 Master의 부하 감소
  - Replication 지연
    - Master와 Replica 간 데이터 반영 시점 차이 발생 가능
    - 비동기 복제 구조로 인해 최신 데이터 조회가 보장되지 않을 수 있음
    - 읽기 성능은 향상되지만, 데이터 정합성은 일부 포기해야 함
  - Replication 지연 대응
    - Master 직접 읽기 (비추천)
      - 쓰기 직후 최신 데이터가 필요한 경우 Master에서 조회
      - Replication 지연 문제는 해결되지만
      - 읽기 부하가 Master로 집중되어 Replication의 장점이 사라짐
    - 캐싱 활용
      - 데이터 추가/수정/삭제 시 캐시에 함께 반영
      - 조회 시 Replica 대신 캐시에서 읽도록 구성
      - Replication 지연이 있어도 최신 데이터 조회 가능
      - 읽기 성능과 데이터 정합성을 동시에 보완 가능 

### Partitioning & Sharding
- Partitioning
  - 거대한 파일을 논리적인 기준을 잡고 나눠서 저장하는 기법
  - 위에서 정리한 내용 참고
- Sharding
  - Sharding 이란?
    - 데이터를 여러 DB로 수평 분할하여 저장하는 방식
    - 단일 DB의 용량 한계 및 쓰기 성능 한계를 해결하기 위한 확장 전략
    - Scale-up이 아닌 Scale-out을 가능하게 함
    - 주로 대규모 트래픽, 대량 데이터 환경에서 사용됨
  - Shard Key 선정
    - 데이터가 여러 Shard에 균등하게 분산되는 값
    - 특정 Shard에 트래픽이 몰리는 핫스팟 현상을 방지하는 것이 핵심
    - 변경되지 않는 값이어야 하며, 변경 시 데이터 이동 비용이 매우 큼
    - 주요 조회 조건과 잘 맞는 값이어야 Cross Shard 쿼리를 줄일 수 있음
    - 보통 user_id, order_id 같은 고유 값이 적합
  - Cross Shard
    - 하나의 요청이 여러 Shard를 동시에 조회하거나 수정하는 문제
    - 모든 Shard를 조회해야 하므로 성능 저하가 발생
    - 분산 트랜잭션 처리로 인해 구현 난이도와 장애 대응 복잡도 증가
    - 샤딩 설계의 핵심 목표는 Cross Shard 발생을 최소화하는 것
  - 일관성 처리
    - 샤딩 환경에서는 단일 DB 트랜잭션 보장이 불가능
    - 여러 Shard에 걸친 데이터 변경 시 일관성 전략이 필요
    - 일관성을 위한 전략의 종류
      - 2PC (Two-Phase Commit)
        - 여러 Shard의 트랜잭션을 하나의 트랜잭션처럼 처리
        - 강한 일관성을 보장
        - 락 유지 시간이 길고 성능 저하가 큼
        - 장애 발생 시 복구가 어렵고 실무에서는 잘 사용하지 않음
      - Saga 패턴
        - 트랜잭션을 여러 로컬 트랜잭션으로 분리하여 처리
        - 실패 시 보상 트랜잭션을 실행하여 상태를 되돌림
        - 최종적 일관성(Eventual Consistency)을 허용
        - 분산 환경과 마이크로서비스에서 현실적인 선택

### 데이터 압축과 아카이빙
- 목적
  - 저장 공간 절약
  - 디스크 I/O 감소를 통한 성능 개선
  - 운영 데이터와 장기 보관 데이터의 분리
- 데이터 압축
  - 데이터를 디스크에 저장할 때 압축하여 저장하는 방식
  - 디스크 사용량을 줄이고 I/O 비용을 감소시킴
  - 읽기 시 압축 해제가 필요하므로 CPU 사용량은 증가
  - 자주 조회되지 않는 데이터일수록 효과적
  - InnoDB는 테이블/페이지 단위 압축을 지원
  - 압축 테이블 사용예시
    - ```
      -- 압축 기능을 활성화하여 테이블 생성
      CREATE TABLE logs_compressed (
           log_id BIGINT AUTO_INCREMENT PRIMARY KEY,
           user_id INT,
           message TEXT,
           created_at TIMESTAMP
      )
          ROW_FORMAT=COMPRESSED
          KEY_BLOCK_SIZE=8;
      ```
      - 장점
        - 디스크 I/O 감소
          - SELECT 시 읽어야 할 데이터 양이 줄어들어 디스크 접근 횟수 감소
        - 버퍼 풀 히트율 개선
          - 압축된 페이지 기준으로 더 많은 데이터가 메모리에 적재됨
          - 동일한 버퍼 풀 크기에서도 캐시 효율 증가
        - 대용량 조회 쿼리에 유리
          - 로그 조회, 기간 조건 검색 등에서 효과적
        - 스토리지 비용 절감
          - 테이블 크기 감소로 백업 및 복제 비용도 함께 감소

      - 단점
        - 쿼리 실행 시 CPU 부담 증가
          - SELECT 시 압축 해제 과정이 필요
        - 쓰기 쿼리 성능 저하
          - INSERT / UPDATE / DELETE 시 압축 처리 비용 발생
        - 인덱스 효율 저하 가능
          - 페이지 압축으로 인해 페이지 분할 및 재압축 발생 가능
        - OLTP 성격 쿼리에 부적합
          - 짧고 빈번한 트랜잭션 환경에서는 오히려 성능 저하
- 아카이빙
  - 오래된 데이터를 운영 DB에서 분리하여 별도 저장소로 이동
  - 운영 DB의 데이터 크기를 줄여 성능과 관리성을 개선
  - 주로 과거 로그, 이력성 데이터에 적용
  - 읽기 빈도가 매우 낮은 데이터를 대상으로 함

### 섹션 7
- MySQL 보다 설계 관점의 강의내용이라 정리하지 않음