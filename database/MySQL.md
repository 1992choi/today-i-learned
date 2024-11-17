# MySQL
### 테이블 및 컬럼 조회
- 테이블 코멘트 조회   
  - SELECT TABLE_NAME, TABLE_COMMENT FROM INFORMATION_SCHEMA.TABLES WHERE TABLE_SCHEMA = '스키마 이름' AND TABLE_NAME = '테이블 이름'   
- 컬럼 코멘트 조회   
  - SELECT TABLE_NAME, COLUMN_NAME, COLUMN_COMMENT FROM INFORMATION_SCHEMA.COLUMNS WHERE TABLE_SCHEMA = '스키마 이름' AND TABLE_NAME = '테이블 이름';   

### INDEX 조회 
- SHOW index FROM 테이블명;   

### 날짜 구하기
- 오늘 날짜   
  - MySQL : SELECT NOW()   
- 어제 날짜   
  - MySQL : SELECT NOW()- INTERVAL 1 DAY