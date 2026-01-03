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
