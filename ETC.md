# WEB
### SpringBoot에서 application.properties 설정 재정의
> @SpringBootTest(properties = "spring.aop.proxy-target-class=false")   

### Gradle 명령어
> - **클린 및 빌드**   
>   \- ./gradlew clean build   
> - **버전 변경**   
>   \- ./gradlew wrapper --gradle-version=6.5   
> - **버전 확인**   
>   \- gradle -v   

### 서비스 실행 및 프로필 선택 방법
> java -jar -Dspring.profiles.active=[프로필명] [jar명]   
> Ex) java -jar -Dspring.profiles.active=dev web-0.0.1-SNAPSHOT.jar   
> Ex) nohup java -jar -Dspring.profiles.active=dev web-0.0.1-SNAPSHOT.jar & (사용자가 로그아웃해도 백그라운드로 실행)  

### <input> 태그 자동완성 제거
> \- autocomplete="off" 추가    
> ```
> <input type="text" autocomplete="off" />   
> ```

### 툴팁 줄바꿈
> \- 줄바꿈하고자 하는 문장 사이에 엔티티 숫자를 삽인한다.   
> ```
> <span title="줄바꿈이&#10;필요한&#13;문장">툴팁</span>  
> ```
> \- 출력결과  
> 줄바꿈이   
> 필요한   
> 문장   

### <script> 태그의 defer 속성
> \- script 태그의 defer 속성은 페이지가 모두 로드된 후에 해당 외부 스크립트가 실행됨을 명시   
> \- 브라우저가 페이지의 파싱을 모두 끝내면 스크립트가 실행   
> ```
> <script src="/examples/common.js" defer></script>   
> ```


<br><br><br><br><br><br><br><br><br><br>


# LINUX
### JDK 설치
> sudo yum install java-1.8.0-openjdk-devel   

### OS 버전 확인
>   \- cat /etc/issue   
>   \- cat /etc/os-release   

### 대상 서버 포트 확인
> telnet [IP] [port]   
> Ex) telnet 192.0.0.1 8084       

### 포트 정리
>   \- 20, 21 : FTP   
>   \- 22 : SSH   
>   \- 23 : Telnet   
>   \- 25 : SMTP   
>   \- 80 : HTTP   
>   \- 443 : HTTPS   

### 도메인명으로 IP확인
> ping [Domain]   
> Ex) ping google.com    

### 포트 개방
> sudo iptables -I INPUT 1 -p tcp --dport [포트번호] -j ACCEPT   
> Ex) sudo iptables -I INPUT 1 -p tcp --dport 80 -j ACCEPT   
> Ex) sudo iptables -I INPUT 1 -p tcp --dport 443 -j ACCEPT   

### 방화벽
> - **시작**   
>   \- systemctl start firewalld   
> - **중지**   
>   \- systemctl stop firewalld    
> - **재시작**   
>   \- firewall-cmd --reload   
> - **구동 확인**   
>   \- systemctl status firewalld   
> - **서비스 추가**   
>   \- firewall-cmd --permanent --zone=public --add-service=http   
>   \- firewall-cmd --permanent --zone=public --add-service=https   
> - **포트 추가**   
>   \- firewall-cmd --permanent --zone=public --add-port=8073/tcp   
> - **확인**   
>   \- firewall-cmd --zone=public --list-all   

### MySQL 설치
> - **설치**   
>   \- yum -y install mysql-server   
> - **실행**   
>   \- systemctl start mysqld   
> - **실행 후 상태 확인**   
>   \- systemctl status mysqld   
> - **접속**   
>   \- mysql -u root -p   
> - **데이터베이스 목록 출력**   
>   \- show databases   
> - **데이터베이스 사용**   
>   \- use database_name   

### Maria DB 설치
> - **설치**   
>   \- yum install mariadb mariadb-server   
> - **설치확인**   
>   \- rpm -qa | grep -i mariadb   
> - **실행**   
>   \- systemctl start mariadb   
> - **실행 후 상태 확인**   
>   \- systemctl status mariadb      
> - **ROOT 비밀번호 설정**   
>   \- mysqladmin -u root password   
> - **부팅시 자동실행 설정**   
>   \- systemctl enable mariadb   
> - **접속**   
>   \- mysql -u root -p   
> - **Database 확인**   
>   \- show databases;   
> - **Database 사용**   
>   \- use 데이터베이스명;
> - **Table 확인**   
>   \- show tables;  

### MacOS 자바 설치 및 환경변수 설정
> - **설치**   
>   \- 생략   
> - **경로 복사**   
>   \- /Library/Java/JavaVirtualMachines/설치된 JDK버전/Contents/Home   
> - **경로 설정**   
>   \- vi ~/.bash_profile 입력 후  
>   \- export JAVA_HOME=/Library/Java/JavaVirtualMachines/설치된 JDK버전/Contents/Home   
> - **변경한 환경변수 적용**   
>   \- source ~/.bash_profile   
> - **확인**   
>   \- java -version   

### MacOS에서 SSH접속
> - **keygen 추가 생성**   
>   \- ssh-keygen -b 2048 -t rsa      
> - **생성된 키젠 추가**   
>   \- 생성된 키젠 중 xxx.pub파일의 내용을 클라우드 서버에 존재하는 .ssh/authorized_keys에 키 추가   
> - **개인키 권한 변경**   
>   \- chmod 600 [키경로]/[키이름]         
>   \- Ex) chmod 600 .ssh/id_rsa   
> - **접속**   
>   \- ssh -i [키경로]/[키이름] [유저명]@IP   
>   \- Ex) ssh -i /Users/choi/.ssh/id_rsa opc@123.123.123.123

### 실행 중인 포트 확인
> lsof -i :포트번호   
> Ex) lsof -i :8084  

### ls(파일 조회) 명령어 옵션   
>   \- l : 상세 조회   
>   \- a : 모든 파일 조회(숨김파일 확인 가능)   
>   \- r : 역순으로 조회   
>   \- R : 하위 디렉토리까지 조회   
>   \- t : 시간순으로 조회   
>   \- ltr : 날짜순으로 상세 조회   

### Alias 설정방법
> - **명령어를 통한 생성**   
>   \- alias 별명='명령어'   
>   \- Ex) alias boot_start='/home/opc/start.sh'   
>   \- * 명령어를 통한 생성은 시스템 재시작을 하게되면 초기화된다.   
>   \- * 'unalias 별명' 명령어를 통하여 삭제 가능하다.   
> - **.bash_profile에 정의하여 생성**   
>   \- ~/.bash_profile에 등록한다.   
>   \- Ex) vi .bash_profile 후에 alias boot_start='/home/opc/start.sh' 작성   
>   \- * 명령어 등록 후, 'source .bash_profile' 또는 '. .bash_profile' 명령어를 통해 적용 완료시킨다.   

### Apache 버전 확인
>   \- httpd -v (단, 설치된 경로에서 유효한 명령어. 설치된 경로를 확인하기 위해서는 'ps -ef | grep -i httpd' 명령어 실행하여 확인가능하다.)   
>   \- rpm -qa httpd   

### vi 편집기 단축키
> - **라인번호 표시**   
>   \- :set number   
> - **문자 검색**   
>   \- :/찾을 문자   
> - **문자 치환**   
>   \- :%s/[변경 대상 문자]/[변경할 문자]   
>   \- Ex) :%s/foo/bar (foo가 bar로 변경된다.)     

### tail
> - **실시간 표시**   
>   \- tail -f [파일명]   
>   \- Ex) tail -f exception.log   
>   \- Ex) tail -100f exception.log   
> - **여러 파일을 동시에 표시**   
>   \- tail -f [첫 번째 파일명] [두 번째 파일명]   
>   \- Ex) tail -f exception_admin.log exception_user.log   

### 문자가 포함된 파일 찾기
>   \- find [대상폴더] -name "[파일명].[확장자]" | xargs grep "[문자열]"   
>   \- Ex) find . -name "\*.\*" | xargs grep "123" (현재 디렉토리에서 문자 '123'이 포함된 파일 검색)   

### 파일 내 문자 변경
>   \- sed -i 's/변경전 내용/변경할 내용/g' 파일명   
>   \- Ex) sed -i 's/1000000/1,000,000/g' price.txt   

### 디스크 용량 확인
> - **디렉토리에 속한 파일용량 확인**   
>   \- du -ah   
> - **디스크 사용량 확인**   
>   \- df -h   

### Session Timeout설정
> - **환경변수로 등록**   
>   \- .bash_profile에 'export TMOUT=600' 추가한다.(단위는 초이며, 0을 입력할 경우 계속 유지된다.)   
> - **일회성 처리**   
>   \- 콘솔에 'TMOUT=600'을 입력한다.(단위는 초이며, 0을 입력할 경우 계속 유지된다.)   
> - **세션 타임아웃 확인**   
>   \- echo $TMOUT

### 시스템 종료 및 재부팅
> - **종료**   
>   \- shutdown -h now   
> - **재부팅**   
>   \- shutdown -r now

### 시간변경 
>   \- date -s "시:분:초"   
>   \- Ex) date -s "07:31:00"   

### 프롬프트(prompt) 색상 변경
>   \- .bash_profile에 아래 문구 추가   
>   \- export PS1="\[\e[36;1m\]\u@\[\e[32;1m\]\h:\[\e[31;1m\]\w:> \[\e[0m\]"   

### Crontab
>   \- 리눅스 작업 스케줄러로 특정 시각에 특정 명령어가 수행시키는 프로그램이다.   
> - **리스트 확인**   
>   \- crontab -l   
> - **등록 및 수정**   
>   \- crontab -e   
> - **표현식**   
>   \- 분(0-59) 시(0-23) 일(0-31) 월(0-12) 요일(0-7 -> 0=일, 1=월, ... 7=일) 명령어   
>   \- Ex) * * * * * remove.sh (매분 수행)   
>   \- Ex) */10 * * * * remove.sh (10분마다 수행)   
>   \- Ex) 0 5 * * * remove.sh (매일 5시에 수행)   
>   \- Ex) */10 * * * * remove.sh (10분마다 수행)   
>   \- Ex) 0 9 1 * * remove.sh (매월 1일 9시마다 수행)   
>   \- Ex) 0 9 * * 1 remove.sh (매주 월요일 9시마다 수행)   

### 파일 인코딩
> - **인코딩 확인**   
>   \- file -bi test.log   
> - **인코딩 변경 후 다른이름으로 저장**   
>   \- iconv -c -f utf-8 -t euc-kr test.log > test2.log   


<br><br><br><br><br><br><br><br><br><br>


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


<br><br><br><br><br><br><br><br><br><br>


# ISSUE
### Mybatis Cache 이슈
>   \- 이슈내용 : 반복문 내에서 Sequence를 채번하여 Insert하려고 하였으나, 동일한 Sequence가 생성되는 이슈 발생   
>   \- 수정사항 : MyBatis XML에서 캐싱되지 않도록 옵션(useCache="false" flushCache="true") 추가   
>    ```java
>    <select id="QueryId" useCache="false" flushCache="true">
>       SELECT ...
>    </select>

### Mybatis 0 비교
>   \- 이슈내용 : 실수형 column1, column2의 값이 0일 때, column1 != ''와 column2 != '' 조건을 만족하여 0으로 업데이트 불가   
>    ```java
>    <update id="update">
>       update table
>       <set>
>           <if test="column1 != null and column1 != ''">
>               column1 = #{column1},
>           </if>
>           <if test="column2 != null and column2 != ''">
>               column2 = #{column2},
>           </if>
>       </set>
>       where column0 = #{column0}
>   </update>
>    ```
>   \- 수정사항 :  column1 != '' 대신에 column1.equals("") 사용 

### Mybatis - Invalid bound statement (not found)
>   \- 오류메시지 : org.apache.ibatis.binding.BindingException: Invalid bound statement (not found)   
>   \- 원인 1.  Repository의 메서드명과 Mapper.xml의 id가 일치하지 않는 경우  
>   \- 원인 2.  Mapper.xml의 경로가 잘못된 경우   

### org.springframework.web.HttpMediaTypeNotAcceptableException: Could not find acceptable representation
>   \- 원인 : 스프링부트에서 'return ResponseEntity.ok().body(ResponseObject);' 의 형태로 작성된 부분 중 'ResponseObject' 객체에 @Getter가 없어서 발생한 이슈   
>   \- 수정사항 : ResponseObject클래스에 @Getter 어노테이션 추가   

### POST 방식 데이터 소실 이슈   
>   \- 현상 : 다수의 데이터를 POST 방식으로 전달하여 처리하는 과정에서 일부 데이터가 처리되지 않는 현상 발생   
>   \- 오류메시지 : More than the maximum number of request parameters (GET plus POST) for a single request ([10,000]) were detected. Any parameters beyond this limit have been ignored.   
>   \- 원인 : 파라미터 갯수 또는 사이즈를 초과한 경우 발생   
>   \- 해결방안 : 톰캣 설정 중 maxPostSize와 maxParameterCount를 변경한다.(톰캣 버전에 따라 설정 값이 상이할 수 있다.)   
>    ```java
>    <Connector ...생략... maxPostSize="-1" maxParameterCount="-1" />
>    ```

### \<button> 태그의 Default type   
>   \- 현상 : 버튼을 클릭하였을 때, 자바스크립트의 유효성검사를 만족하지 않아도 submit되는 현상 발생      
>   \- 원인코드   
>   ```java
>   <button id="saveBtn">저장</button>   
>   ... 생략 ...     
>   <script>   
>   $('#saveBtn').click(function() {   
>       if(isValid()) { // isValid() -> false     
>           $('#saveForm').submit();   
>       }   
>   });   
>   </script>     
>   ```
>   \- 해결방안 : \<button> 태그의 type속성에 button을 추가한다.(type이 지정안되면 submit이 Default)   

### MariaDB 실행 시 오류 \#1
>   \- 현상 : systemctl start mariadb 명령어 입력 시 아래의 오류메시지 발생   
>   \- 오류메시지 : Job for mariadb.service failed because the control process exited with error code.      
>   \- 해결방안 : /var/lib/mysql 디렉토리에서 ib_logfile0, ib_logfile1, ibdata1 삭제   

### MariaDB 실행 시 오류 \#2
>   \- 현상 : MariaDB가 죽어있어서 재기동을 위하여 'systemctl start mariadb' 명령어를 입력하였을 때, 아래의 오류메시지 발생   
>   \- 오류메시지 : [ERROR] Can't open and lock privilege tables: Table 'mysql.servers' doesn't exist        
>   \- 해결방안 : /etc/my.cnf 파일에 skip-grant-tables 추가     

### MariaDB 인코딩 이슈
>   \- 오류메시지 : Cause: java.sql.SQLSyntaxErrorException: (conn=4981) Incorrect string value   
>   \- 원인 : Insert하려는 데이터에 한글이 포함되어 있어서 발생.   
>   \- 해결방안 : ALTER TABLE 테이블명 convert to charset UTF8;(테이블의 언어셋을 변경)   

### MariaDB 대소문자 구분 이슈
>   \- 현상 : 테이블 조회 시, 다음의 오류메시지 발생 -> Table '테이블명' doesn't exist   
>   \- 원인 : MariaDB에서 대소문자를 구분하고 있기 때문   
>   \- 해결방안   
>    * 옵션 값 확인    
>       + show variables like 'lower_case_table_names';   
>           + lower_case_table_names=0 : 테이블 생성 및 조회 시 대/소문자 구분   
>           + lower_case_table_names=1 : 입력 값을 모두 소문자로 인식. 즉, 대소문자 구분하지 않음   
>           + lower_case_table_names=2 : 윈도우에서 대/소문자를 구분해서 테이블 생성   
>    * 설정 값 변경    
>       + vi /etc/my.cnf.d/server.cnf      
>           + lower_case_table_names=1   

### @JsonIgnore 이슈
> - **이슈사항**   
>   \- 사용자 조회 API(RESTful API)에서 응답 값 중 '비밀번호' 필드를 제거하기 위하여 도메인 중 '패스워드'에 해당하는 변수에 @JsonIgnore를 사용하였는데 이로인하여 사용자를 등록하는 API에서도 패스워드가 제외되어 이슈가 발생하였다.   
> - **해결방안**   
>   \- 1. 조회용 도메인과 등록용 도메인을 분리한다.   
>   \- 2. @JsonIgnore 어노테이션 대신에 @JsonProperty 어노테이션 사용한다.   

### java.net.BindException : Address already in use : bind 
>   \- 이슈내용 : 스프링부트 시작 시, 'java.net.BindException : Address already in use : bind' 발생   
>   \- 이슈원인 : 포트 번호가 이미 다른 프로세스에서 사용중일 때 발생한다.   
> - **해결방안(Windows 기준)**   
>   \- 1. cmd 실행   
>   \- 2. netstat -ano 입력   
>   \- 3. 서버의 포트번호의 PID 확인   
>   \- 4. taskkill /f /pid 프로세스ID   

### 엔터키 입력 시 submit 이슈
>   \- 이슈내용 : \<input type="text"> 태그에 값을 입력 후, 엔터키를 입력하면 전송되는 이슈.   
>   \- 이슈상세 : 엔터키 이벤트를 정의한적이 없으나, 엔터키를 입력하면 폼이 get으로 전송되어 한글 깨짐 발생.   
>   \- 이슈원인 : \<form> 태그 안에 \<input type="text"> 태그가 1개인 경우, 엔터키를 누르면 자동으로 submit이 된다.   
> - **해결방안**   
>   \- 1) \<form> 태그에 onsubmit 속성 추가 : onsubmit="return false;"   
>   \- 2) \<form> 태그에 onsubmit 속성 추가 : onsubmit="검증함수();"   
>   \- 3) \<form> 태그의 method를 post로 지정   
>   \- 4) 자바스크립트에서 엔터키 입력 시, 제어하는 로직 추가   


<br><br><br><br><br><br><br><br><br><br>


# 기타
### IntelliJ 단축키
> - **전체 검색**   
>   \- macOS : ⇧ + ⇧      
>   \- Windows : Shift + Shift     
> - **키워드가 포함된 파일 검색**   
>   \- macOS : ⌘ + ⇧ + F     
>   \- Windows : Ctrl + Shift + F   
> - **최근 실행한 파일 확인**   
>   \- macOS : ⌘ + E   
>   \- Windows : Ctrl + E   
> - **최근 수정한 파일 확인**   
>   \- macOS : ⌘ + ⇧ +E   
>   \- Windows : Ctrl + Shift + E   
> - **페이지 내 오류를 발행하는 코드로 이동**   
>   \- macOS : f2   
>   \- Windows : f2   
> - **리팩토링 관련 전체 항목 조회**   
>   \- macOS : ^ + ^   
>   \- Windows : Ctrl + Alt + Shift + T   
> - **코드 정렬**   
>   \- macOS : ⌥ + ⌘ + L      
>   \- Windows : Ctrl + Alt + L  
> - **Import 정리**   
>   \- macOS : ^ + ⌥ + O   
>   \- Windows : Ctrl + Alt + O   
> - **라인 주석**   
>   \- macOS : ⌘ + /   
>   \- Windows : Ctrl + /   
> - **블럭 주석**   
>   \- macOS : ⌘ + ⌥ + /   
>   \- Windows : Ctrl + Shift + /   
> - **Override 메소드 자동 생성**   
>   \- macOS : ⌘ + O   
>   \- Windows : Ctrl + O   
> - **Implement 가능한 메서드 자동 생성**   
>   \- macOS : ⌘ + I   
>   \- Windows : Ctrl + I   

### IntelliJ 플러그인
> - **CamelCase**   
>   \- macOS : Preference > Plugins > CamelCase > Shift + Alt + U   
>   \- Windows : Settings > Plugins > CamelCase > ⇧ + ⌥ + U   

### Window10 키배열 맥북처럼 변경   
> - **Caps Lock키 <> 한영키 위치변경 및 Ctrl키 <> Alt키 위치변경**   
>   \- 레지스트리 편집기 > HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Keyboard Layout로 이동   
>   \- 이진파일 생성(파일명 : Scancode Map)   
>   \- Scancode Map 편집   
>   ```java
>    00 00 00 00 00 00 00 00
>    02 00 00 00 72 00 3A 00
>    3A 00 38 E0 1D 00 38 00
>    38 00 1D 00 00 00 00 00
>   ```

### Window에서 Tail 명령어
>   \- 명령어 : Get-Content 파일경로 -Wait -Tail 10   
>   \- 단, Window PowerShell을 사용해야 한다.   

### Github 이모지 
>   \- Commit 코멘트에 이모지를 사용하고자 할 때, :이모지명: 의 형태로 사용할 수 있다.   
>   \- Ex) 쿼리 :bug:버그 수정   
>   \- 이모지 시트 : https://www.webfx.com/tools/emoji-cheat-sheet/   

### 크롬 강력 새로고침
>   \- 개발자도구를 실행시킨 상태에서 새로고침 버튼을 우클릭할 경우, '강력한 새로고침' 기능을 사용할 수 있다.   
>   \- macOS : ⌘ + ⇧ + R     
>   \- Windows : Ctrl + Shift + R   

### Homebrew
>   \- 홈브류(Homebrew)란, 맥OS 용 패키지 관리자이다.   
> - **설치방법**   
>   \- 1. Homebrew 홈페이지에 접속하여 설치 명령어를 복사한다.   
>   \- 2. 터미널에 복사한 명령어 입력한다.      
>   \- 3. [2]번 명령어에 대한 실행이 완료되면 콘솔창에 나오는 'Next steps:'에 명시되어 있는 명령어를 순차적으로 실행한다.   
> - **명령어**   
>   \- 업데이트 : brew update   
>   \- 버전확인 : brew --version   


### Prometheus 설치
>   \- 맥 OS에 프로메테우스(Prometheus) 설치하기
> - **설치방법**   
>   \- 1. 터미널에 'brew install prometheus'를 입력하여 다운로드한다.   
>   \- 2. 터미널에 'brew service start prometheus'를 입력하여 실행한다.   
>   \- 3. 브라우저에서 'localhost:9090'으로 접속하여 정상 실행되는지 확인한다.   
> - **스프링부트와 연동하여 데이터 수집**   
>   \- 1. prometheus.yml 파일에 아래의 내용(스프링부트에 대한 설정 내용)을 추가한다.   
>    ```java
>       - job_name: "spring-actuator"
>         metrics_path: '/actuator/prometheus'
>         scrape_interval: 5s
>         static_configs:
>         - targets: ["localhost:8084"]
>    ```
>   \- 2. 'brew service stop prometheus'으로 정지 후, 'brew service start prometheus'으로 재시작한다.   

### Grafana 설치
>   \- 맥 OS에 Grafana 설치하기
> - **설치방법**   
>   \- 1. 터미널에 'brew install grafana'를 입력하여 다운로드한다.   
>   \- 2. 터미널에 'brew services start grafana'를 입력하여 실행한다.   
>   \- 3. 브라우저에서 'localhost:3000'으로 접속하여 정상 실행되는지 확인한다.   



