# Database
### Oracle Alias의 큰 따옴표 
> \- 공백을 포함할 때 사용할 수 있다.   
> \- 특수문자를 포함할 때 사용할 수 있다.   
> \- 대소문자를 구분할 때 사용할 수 있다.   

### Oracle ESCAPE
> \- LIKE 연산으로 '%' 나 '_' 가 포함된 문자를 검색하고자 할때 사용한다.   
> \- Ex) SELECT * FROM BOARD WHERE TITLE LIKE '%\\%%' ESCAPE '\\'   
> \- Ex) SELECT * FROM BOARD WHERE TITLE LIKE '%\\_%' ESCAPE '\\'   

### Oracle 테이블 및 컬럼 조회
> - **테이블 목록 조회(전체계정)**   
>   \- SELECT * FROM all_all_tables   
>   \- SELECT * FROM dba_tables   
>   \- SELECT * FROM all_objects WHERE object_type = 'TABLE'   
> - **테이블 목록 조회(접속계정)**   
>   \- SELECT * FROM tabs   
>   \- SELECT * FROM user_tables   
>   \- SELECT * FROM user_objects WHERE object_type = 'TABLE'   
> - **테이블 코멘트 조회(전체계정)**   
>   \- SELECT * FROM all_tab_comments   
> - **테이블 코멘트 조회(접속계정)**   
>   \- SELECT * FROM user_tab_comments   
> - **컬럼 목록 조회(전체계정)**   
>   \- SELECT * FROM all_tab_columns   
> - **컬럼 목록 조회(접속계정)**   
>   \- SELECT * FROM user_tab_columns   
> - **컬럼 코멘트 조회(전체계정)**   
>   \- SELECT * FROM all_col_comments   
> - **컬럼 코멘트 조회(접속계정)**   
>   \- SELECT * FROM user_col_comments   

### Oracle 시퀀스 조회
> - **생성된 시퀀스 조회**   
>   \- SELECT * FROM user_sequences   
> - **현재 시퀀스 조회**   
>   \- SELECT 시퀀스명.currval FROM dual   
>   \- (*참고. nextval을 실행 후, 같은 세션동안만 사용 가능하다.)   
> - **다음 시퀀스 확인**   
>   \- SELECT 시퀀스명.nextval FROM dual   

### MySQL 테이블 및 컬럼 조회
> - **테이블 코멘트 조회**   
>   \- SELECT TABLE_NAME, TABLE_COMMENT FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = '스키마 이름' AND TABLE_NAME = '테이블 이름'   
> - **컬럼 코멘트 조회**   
>   \- SELECT TABLE_NAME, COLUMN_NAME, COLUMN_COMMENT FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_SCHEMA = '스키마 이름' AND TABLE_NAME = '테이블 이름';   

### H2 데이터베이스 모든 테이블 삭제
> \- drop all objects   

### [Windows] 오라클 클라이언트 버전 확인
>   \- Command > tnsping      

### INDEX 조회 
> - **Oracle**   
>   \- SELECT index_name FROM user_indexes WHERE table_name = '테이블명';   
> - **MariaDB**   
>   \- SHOW index FROM 테이블명;   

### 최대값을 사용한 시퀀스 생성
>   \- SELECT LPAD(TO_CHAR(NVL(MAX(컬럼명), 0) + 1), 5, '0') FROM 테이블명  

### 중복 데이터조회
> \- SELECT COL1, COUNT(\*) FROM TABLE_NAME GROUP BY COL1 HAVING COUNT(\*) > 1;   
> \- SELECT COL1, COL2, COUNT(\*) FROM TABLE_NAME GROUP BY COL1, COL2 HAVING COUNT(\*) > 1;   

### Oracle 난수 생성
> - **랜덤 숫자**   
>   \- SELECT TRUNC(DBMS_RANDOM.VALUE(1, 1000)) FROM DUAL      
> - **랜덤 문자**   
>   \- SELECT DBMS_RANDOM.STRING('U', 10) FROM DUAL   
>   \- U=(대문자), L=(소문자), A=(대, 소문자 혼용), X=(영어, 숫자 혼용), P=(특수문자 포함 모두 혼용)   

### 날짜 구하기
> - **오늘 날짜**   
>   \- Oracle : SELECT SYSDATE FROM DUAL   
>   \- MySQL : SELECT NOW()   
> - **어제 날짜**   
>   \- Oracle : SELECT SYSDATE-1 FROM DUAL   
>   \- MySQL : SELECT NOW()- INTERVAL 1 DAY    

### 해당월의 전체날짜 구하기
>   \- 202205를 입력하면 2022-05-01부터 2022-05-31까지 얻을 수 있다.   
> ```
> SELECT  TO_CHAR(DT + LEVEL -1, 'yyyy-MM-dd') AS YYYYMMDD
> FROM (
>        SELECT TO_DATE(:yyyymm, 'YYYYMM') AS DT 
>        FROM DUAL
>      )
> CONNECT BY LEVEL <= LAST_DAY(DT) -DT +1;
> ```

### 테이블 COPY
>   \- 테이블을 생성한 이후에 데이터를 복사할 수 있다.   
> ```
> CREATE TABLE MEMBER_TMP AS
> SELECT * FROM MEMBER;
> ```

### 휴지통 관리
> - **휴지통 내용 조회**   
>   \- show recyclebin   
> - **휴지통 비우기**   
>   \- purge recyclebin   
> - **삭제된 테이블 복구**   
>   \- flashback table [ 테이블명 ] to before drop   

### COUNT(*) vs COUNT(1) vs COUNT(column)
>   \- COUNT(*)과 COUNT(1)은 동일한 수의 블록 읽기 / 쓰기 / 처리 시에 같은 CPU 사용시간, 수행 시간을 갖는다.   
>   \- COUNT(column)은 NULL 값이 들어간 행은 카운트하지 않는다.(*과 1은 카운트 한다.)
