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

### 실행 중인 포트 확인
> lsof -i :포트번호   
> Ex) lsof -i :8084  
>
> netstat -lntp | grep 포트번호   
> Ex) netstat -lntp | grep 8084   

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

<br><br><br><br><br><br><br>

# macOS
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

### RabbitMQ 설치
> - **설치**   
>   \- 1. brew update   
>   \- 2. brew install rabbitmq  
> - **실행**   
>   \- 1. brew services start rabbitmq   
>   \- 2. http://localhost:15672 접속   
>   \- 3. guest / guest 입력 후 로그인   

### Kafka 서버기동
> - **Zookeeper 및 Kafka 기동**   
>   \- ./zookeeper-server-start.sh ../config/zookeeper.properties   
>   \- ./kafka-server-start.sh ../config/server.properties   
> - **Topic 생성**   
>   \- ./kafka-topics.sh --create --topic quickstart-events --bootstrap-server localhost:9092 --partitions 1   
> - **Topic 목록 확인**   
>   \- ./kafka-topics.sh --bootstrap-server localhost:9092 --list   
> - **Topic 정보 확인**   
>   \- ./kafka-topics.sh --describe --topic quickstart-events --bootstrap-server localhost:9092 
> - **메시지 생산**   
>   \- ./kafka-console-producer.sh --broker-list localhost:9092 --topic quickstart-events
> - **메시지 소비**   
>   \- ./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic quickstart-events --from-beginning

### Kafka Connect
> - **실행**   
>   \- ./bin/connect-distributed ./etc/kafka/connect-distributed.properties   
>   \- 단, Kafka 서버기동된 상태여야 한다.   
> - **JDBC Connector 설치**   
>   \- 1. confluentinc-kafka-connect-jdbc-10.0.1.zip 다운로드   
>   \- 2. ./etc/kafka/connect-distributed.properties 파일 내 plugin.path에 파일 경로 명시   
>         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; Ex) plugin.path=/Users/choi/dev/confluentinc-kafka-connect-jdbc-10.7.4/lib   
>   \- 3. JdbcSourceConnector에서 MariaDB를 사용하기 위해 드라이버 복사   
>         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;  ./share/java/kafka 하위에 mariadb-java-client-2.7.2.jar 복사
> - **Source Connect 사용**   
>   \- 1. Kafka Source Connect 추가 (포스트맨 이용)   
>         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 단, Zookeeper, Kafka, Kafka Connect가 모두 실행되어 있어야한다.   
>   ```
>   [POST] localhost:8083/connectors
>   {
>       "name" : "my-source-connect",
>       "config" : {
>           "connector.class":"io.confluent.connect.jdbc.JdbcSourceConnector",
>           "connection.url":"jdbc:mysql://localhost:3306/mydb",
>           "connection.user":"root",
>           "connection.password":"test1357",
>           "mode":"incrementing",
>           "incrementing.column.name":"id",
>           "table.whitelist":"users",
>           "topic.prefix":"my_topic_",
>           "tasks.max":"1"
>       }
>   }
>   ```
>   \- 2. Kafka Source Connect 목록 확인 (포스트맨 이용)   
>   ```
>   [GET] localhost:8083/connectors
>   ```
>   \- 3. Kafka Source Connect 상태 확인 (포스트맨 이용)      
>   ```
>   [GET] localhost:8083/connectors/my-source-connect/status
>   * my-source-connect는 커넥트 추가 시에 설정한 name값
>   ```
>   \- 4. Kafka Source Connect 테스트   
>      - 4.1. 설정한 DB의 테이블에 값 INSERT   
>      - 4.2. Topic 메시지 확인
>        - 4.2.1. ./kafka-console-consumer.sh --bootstrap-server localhost:9092 --topic my_topic_users --from-beginning   
>                  (* my_topic_users는 topic.prefix와 table.whitelist의 값)
> - **Sink Connect 사용**   
>   \- 1. Kafka Sink Connect 추가 (포스트맨 이용)   
>         &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; 단, Zookeeper, Kafka, Kafka Connect가 모두 실행되어 있어야한다.   
>   ```
>   [POST] localhost:8083/connectors
>   {
>       "name" : "my-sink-connect",
>       "config" : {
>           "connector.class":"io.confluent.connect.jdbc.JdbcSinkConnector",
>           "connection.url":"jdbc:mysql://localhost:3306/mydb",
>           "connection.user":"root",
>           "connection.password":"test1357",
>           "auto.create":"true",
>           "auto.evolve":"true",
>           "delete.enabled":"false",
>           "task.max":"1",
>           "topics":"my_topic_users"
>       }
>   }
>   ```
>   \- 2. Kafka Sink Connect 목록 확인 (포스트맨 이용)   
>   ```
>   [GET] localhost:8083/connectors
>   ```
>   \- 3. 테이블 생성 확인
>      - 3.1. show tables; 쿼리를 수행하면, my_topic_users 추가된 것을 확인할 수 있다.    
>      - 3.2. select * from my_topic_users; 쿼리를 수행하면, Kafka를 통해 생성된 데이터들을 확인할 수 있다.

### MariaDB 설치
> - **설치**   
>   \- brew install mariadb
> - **시작, 종료, 상태확인**   
>   \- mysql.server start   
>   \- mysql.server stop   
>   \- mysql.server status      
> - **접속**   
>   \- sudo mysql -u root
> - **데이터베이스 생성**   
>   \- create database mydb;

<br><br><br><br><br><br><br>

# Windows
### Window에서 Tail 명령어
>   \- 명령어 : Get-Content 파일경로 -Wait -Tail 10   
>   \- 단, Window PowerShell을 사용해야 한다.  
