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
