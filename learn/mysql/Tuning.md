# [인프런] 업무에 바로 쓰는 SQL 튜닝

<br><br>
## 사전 준비
### MySQL 설치
- 도커로 설치
    - docker pull mysql
- 컨테이너 실행
    - docker run --name mysql-container -e MYSQL_ROOT_PASSWORD=1234 -d -p 3306:3306 mysql
- 파일 실행을 위한 환경설정
  - ```
    -- 컨테이너 접속
    docker exec -it mysql-container bash
    
    -- 계정 접속
    mysql -uroot -p

    -- 권한 설정
    GRANT ALL PRIVILEGES ON *.* TO 'root'@'%' IDENTIFIED BY 'admin' WITH GRANT OPTION;
    
    -- 설정 적용
    FLUSH PRIVILEGES;
    ```
### 실습 데이터 추가
- 실습 데이터 경로
  - https://github.com/7e7ey/Lecture-SQLtune.kit/tree/main/ch01-실습환경
- 데이터 추가
  - ```
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/data_setting.sql
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/dept.sql
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/emp.sql
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/grade.sql
    
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/emp_hist1.sql
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/emp_hist2.sql
    
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/sal1.sql
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/sal2.sql
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/sal3.sql
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/sal4.sql
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/sal5.sql
    docker exec -i mysql-container mysql -uroot -p1234 < /Users/choi/Downloads/tmp/sal6.sql
    ```

<br>

## 학습정리
### 물리엔진
- ![engine.png](img/engine.png)
  - 구성
    - MySQL의 엔진은 크게 MySQL 엔진과 스토리지 엔진으로 구분된다.
    - MySQL 엔진
      - MySQL 엔진은 사용자가 요청한 SQL문을 넘겨받은 뒤 SQL 문법 검사와 적절한 오브젝트 활용 검사를 한다.
      - SQL 문을 최소 단위로 분리하여 원하는 데이터를 빠르게 찾는 경로를 모색하는 역할을 수행한다.
    - 스토리지 엔진
      - 사용자가 요청한 SQL문을 토대로 DB에 저장된 디스크나 메모리에서 필요한 데이터를 가져오는 역할을 수행한다.
      - 일반적으로 온라인상의 트랜잭션 발생으로 데이터를 처리하는 OLTP(online transaction processing) 환경이 대다수인 만큼 주로 InnoDB 엔진을 사용한다.

### SQL문 수행 절차
- ![process.png](img/process.png)
  - 실행순서
    1. 파서
      - 파서는 MySQL 엔진에 포함되는 오브젝트로, SQL문을 최소 단위로 분리하고 트리를 만든다.
      - 문법 검사도 수행한다.
    2. 전처리기
      - 파서에서 생성한 트리를 토대로 SQL문의 구조적 문제를 파악한다.
    3. 옵티마이저
      - 전달된 파서 트리를 토대로 필요하지 않은 조건 제거, 연산 과정 단순화한다.
      - 테이블 접근 순서, 인덱스 사용 여부, 사용 인덱스 선택, 정렬시 인덱스/임시 테이블 중 사용 결정과 같은 실행 계획 수립한다.
    4. 엔진 실행기
      - MySQL 엔진과 스토리지 엔진 영역 모두에 걸치는 오브젝트로, 옵티마이저에서 수립한 실행 계획을 참고하여 스토리지 엔진에서 데이터를 가져온다.
      - 데이터 가공(필터링 등) 작업을 수행한다.
      - MySQL 엔진의 부하를 줄이려면 스토리지 엔진에서 가져오는 데이터양을 줄이는 게 중요하다.

### 서브쿼리
- 서브쿼리란?
  - 쿼리 안에 포함된 쿼리를 일컫는다.
- 위치에 따른 서브쿼리
  - ```
    SELECT (SELECT ... FROM ...) -- 스칼라 서브 쿼리 (SELECT 절)
    FROM (SELECT ... FROM ...) -- 인라인 뷰 (FROM 절)
    WHERE 컬럼명 IN (SELECT ... FROM ...) -- 중첩 서브 쿼리 (WHERE 절)
    ```
- 관계성에 따른 서브쿼리
  - 비상관 서브쿼리
    - 메인쿼리와 서브쿼리의 관계가 없는 경우를 지칭
    - ```
      SELECT ...
      FROM 학생
      WHERE ... IN (SELECT ... FROM 지도교수)
      ```
  - 상관 서브쿼리
    - 메인쿼리와 서브쿼리의 관계가 있는 경우를 지칭
    - ```
      SELECT ...
      FROM 학생
      WHERE ... IN (SELECT ... FROM 지도교수 WHERE 학생.학번 = ...)
      
      // 지도교수 테이블의 WHERE 절에 학생 테이블의 컬럼이 사용된다.
      ```
- 반환결과에 따른 서브쿼리
  - 단일행 서브쿼리
    - ```
      SELETE ...
      FROM 학생
      WHERE 학번 = (SELECT MAX(학번) 최대학번 FROM 학생)
      ```
  - 다중행 서브쿼리
    - ```
      SELETE ...
      FROM 학생
      WHERE 학번 IN (SELECT MAX(학번) 전공별 최대학번 FROM 학생 GROUP BY 전공코드)
      ```
  - 다중열 서브쿼리
    - ```
      SELETE ...
      FROM 학생
      WHERE (이름, 전공코드) IN (SELECT 이름, 전공코드 FROM 학생 WHERE 이름 LIKE '김%')
      ```

### 테이블에 접근하는 선후 관계(Driving, Driven Table)
- 기본개념
  - 아래와 같이 조인하는 테이블이 있을 때, DB엔진은 동시에 여러 테이블에 접근을 할 수가 없다. 때문에 DB엔진은 여러 개의 테이블들을 내부적으로 순서를 정한 후 순차적으로 접근하여 데이터를 조회하고 이후 그 결과를 다음 테이블로 전달해서 조인을 수행하게 된다.
  - 이 때, 가장 먼저 접근하는 테이블을 Driving 테이블이라고 하고 나중에 접근하게 되는 테이블을 Driven 테이블이라고 한다.
- Driving 테이블이 중요한 이유
  - Driving 테이블에서 추출된 결과를 가지고 Driven 테이블에 접근하기 때문에, Driving 테이블에서 추출된 결과가 작을수록 성능상 유리하다.

### 조인 알고리즘
- 두 개의 테이블을 결합하는 조인의 원리는 크게 2가지로 나눌 수 있다.
  - Nested Loop Join(=NL)
    - 가장 기본적인 조인 방식
    - 드라이빙 테이블의 각 행마다 드리븐 테이블을 탐색
    - 인덱스가 있으면 효율적, 소량 데이터에 유리
    - 일반적으로 중첩 반복 구조
  - Hash Join
    - 해시 테이블을 만들어 조인
    - 주로 등가 조인(=)에 사용
    - 대량의 데이터를 처리할 때 효율적
    - 인덱스가 없어도 빠름

### 오브젝트 스캔의 유형
- 원하는 데이터를 찾기위한 스캔 유형에는 테이블 스캔과 인덱스 스캔이 있다.
  - 테이블 스캔
    - Table Full Scan
      - 인덱스를 거치지 않고 테이블로 접근하여, 처음부터 끝까지 데이터를 접근하는 방식
  - 인덱스 스캔
    - Index Range Scan
      - 인덱스를 특정한 범위까지 스캔한 뒤, 스캔 결과를 토대로 테이블의 데이터를 접근하는방식
      - BETWEEN, <, >, <=, >=, LIKE 등이 사용되면 Range Scan이 적용될 수도 있다.
    - Index Full Scan
      - 인덱스만 처음부터 끝까지 스캔하는 방식
      - 테이블은 접근하지 않는다.
      - 조회에 사용되는 쿼리가 인덱스를 구성하는 컬럼만 사용될 경우 이 방식이 적용될 수 있다.
    - Index Unique Scan
      - 기본키나 유니크 인덱스를 통해 테이블을 스캔하는 방식
      - WHERE절에 = 조건인 경우
      - 조인 컬럼 또는 조건절의 컬럼이 PK 또는 UI의 선두 컬럼으로 사용되는 경우
    - Index Loose Scan
      - 인덱스의 필요한 부분만 골라 스캔하는 방식
      - WHERE절 조건문 기준으로 필요한 부분과 그렇지 않은 부분을 구분하여 선택적으로 스캔
    - Index Merge Scan
      - 생성된 2개의 인덱스를 통합한 후, 테이블을 스캔하는 방식
      - WHERE절 조건문에 서로 다른 인덱스를 구성하는 컬럼들로 구성되어 있는 경우

### 액세스 조건과 필터 조건
- 액세스 조건
  - 디스크에 있는 데이터에 접근할 때, 검색 범위를 줄여주는 조건 
  - 일반적으로 인덱스를 활용해 특정 레코드를 찾아가는 데 사용됨 
  - 스토리지 엔진 단계에서 조건이 적용되어, 불필요한 데이터 I/O를 줄일 수 있음
- 필터 조건
  - 액세스 조건에 의해 조회된 데이터 중에서, 추가적으로 걸러내는 조건 
  - MySQL 엔진(서버 레이어)에서 처리되며, 메모리 상의 필터링 단계에서 적용됨
- 액세스 조건 VS 필터 조건
  - 액세스 조건을 잘 활용하면 스토리지 엔진에서부터 필요한 데이터만 가져오므로 성능에 유리 
  - 반면, 필터 조건만 사용하는 경우 불필요한 데이터를 디스크에서 읽고 난 후 필터링하게 되어 리소스 낭비가 발생함 
  - 따라서 필터 조건으로 걸러지는 데이터가 많다면, 인덱스 설계나 SQL 조건 재구성이 필요한 튜닝 포인트로 볼 수 있음

