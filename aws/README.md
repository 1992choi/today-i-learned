# AWS
- Inflearn > AWS(Amazon Web Service) 입문자를 위한 강의



<br><br>



## 개념 정리
### AWS란?
- Amazon Web Services의 약자로, 아마존닷컴에서 운영하는 Cloud Computing Platform이다.

<br>

### Cloud Computing
- Cloud Computing이란?
  - 간단하게는 서버 가상화 기술이라고도 한다.
  - 사용자의 직접적인 활발한 관리 없이 특히, 데이터 스토리지(클라우드 스토리지)와 컴퓨팅 파워와 같은 컴퓨터 시스템 리소스를 필요 시 바로 제공(on-demand availability)하는 것을 말한다.
- Cloud Computing의 종류
  - IaaS(Infrastructure as a Service)
    - 클라우드 IT의 기본 구성 요소 (네트워킹, 컴퓨터, 데이터 스토리지 공간)
    - 고객에게 서버, 네트워크, OS, 스토리지를 가상화하여 제공하고 관리한다.
  - PaaS(Platform as a Service)
    - 주로 개발 환경과 관련한 서비스를 제공한다.(OS, DB, WAS, JDK)
    - DB 또는 Application 서버 등의 이미 미들웨어를 제공한다.
  - SaaS(Software as a Service)
    - 고객에게 소프트웨어 또는 애플리케이션의 기능만 제공한다.
    - 웹 메일, ERP 등과 같은 형태의 서비스를 사용자에게 제공한다.

<br>

### IAM(Identity and Access Management)
- IAM이란?
  - AWS 리소스에 대한 액세스를 안전하게 제어할 수 있는 웹 서비스이다.
  - IAM을 사용하여 리소스를 사용하도록 인증 및 권한 부여된 대상을 제어할 수 있다.
- 주요기능 및 특징
  - 세밀한 접근 권한 부여가 가능하다.
  - Multi-Factor 인증 기능을 제공한다.
  - 사용자의 패스워드 정책을 관리한다. (=일정 주기마다 변경)
  - 리전 서비스가 아닌 글로벌 서비스이다.
- 구성요소
  - 사용자(User)
    - 실제 AWS의 기능과 자원을 이용하는 사람 혹은 애플리케이션을 의미한다.
  - 그룹(Group)
    - 다수의 사용자를 모아놓은 개념이다.
    - 하나의 그룹에 여러명의 사용자를 지정해서 공통적으로 권한을 주어야 하는 상황일때 유용하다.
  - 역할(Role)
    - 사용자에 권한을 부여하는 또 다른 방식이다.
    - 그룹에 권한을 바로 부여하는 대신, 역할을 만들고 역할을 그룹이나 사용자에게 주는 방식이다.
  - 정책(Policy)
    - 사용자와 그룹, 역할이 무엇을 할 수 있는지에 대한 Permission 설정 모음 데이터 문서.
    - 하나 이상의 AWS 리소스에 대한 어떤 작업을 수행할 수 있는지 허용 규칙을 JSON 형식으로 작성된다.

<br>

### EC2(Elastic Compute Cloud)
- EC2란?
  - Amazon Elastic Compute Cloud의 줄임말로서 AWS에서 제공하는 클라우드 컴퓨팅이다.
  - Elastic이라는 이름은 가상서버를 사용한 만큼 비용을 탄력적으로 지불하고, 성능과 용량도 자유롭게 조절할 수 있다는 의미를 가지고 있다.
- EC2의 특징
  - Auto Scailing을 통해 사용량에 따라 인스턴스를 조절할 수 있다.
  - 사용한 만큼만 비용 지불한다.
  - 몇 분이면 전세계에 컴퓨터 수백여대를 생성할 수 있다.
  - 여러 다른 AWS 서비스와의 유기적인 연동이 가능하다.
- 지불방식
  - On-Demand
    - 필요할 때 바로 생성해서 사용할 수 있는 방식이다.
    - 과금은 1시간 단위로 이루어진다.
    - 3가지 방식 중 요금이 가장 비싸다.
  - Reserved
    - 일정한 예약금을 선불로 내면 인스턴스를 1년 또는 3년동안 예약할 수 있으며 시간당 요금이 대폭 할인된다.
  - Spot
    - 경매 방식의 인스턴스.
    - 인스턴스의 스펙을 설정하고 원하는 가격을 입력하여 입찰하면 높게 입찰한 사람한테 인스턴스가 할당된다.
    - 만약, 해당 스펙의 인스턴스를 다른 사람이 더 높은 가격으로 입찰했다면 내가 가지고 있는 인스턴스는 종료된다.

<br>

### EBS(Elastic Block Storage)
- EBS란?
  - Elastic Block Store의 약자로 Amazon EC2 인스턴스에서 사용할 수 있는 블록 수준 스토리지 볼륨을 제공하는 서비스이다.
  - EC2 안에 부착되어 있는 일종의 하드 디스크이다.
  - EBS는 특정 Availability Zone에 생성된다.
    - Availability Zone(AZ)
      - 가용 영역이라한다.
      - 하나 이상의 데이터 센터로 구성되어져있는 논리적인 데이터센터이다.
      - 한쪽 서버가 망가져도 서비스를 유지시켜준다.
      - 중심부로부터 그의 복사본들이 AZ로 뿌려지며 한쪽 서버가 망가지거나 셧다운 됐을 경우, AZ라는 백업을 통해 서비스 제공을 가능하게 해주는 일종의 Disaster Recovery라고 볼 수 있다.
- EBS 볼륨 타입
  - SSD군
    - General Purpose SSD(GP2)
      - 최대 10K IOPS 지원하며, 1GB당 3IOPS 속도가 나온다.
    - Provisioned IOPS SSD(IO1)
      - 극도의 I/O률을 요구하는(예시 : 매우 큰 DB 관리) 환경에서 주로 사용된다.
      - 10K이상에서 IOPS 지원한다.
  - Magnetic / HDD군
    - Throughput Optimized HDD(ST1)
      - 빅데이터 Datawarehouse, Log 프로세싱 시 주로 사용된다.
      - Boot volume으로 사용할 수 없다.
    - CDD HDD(SC1)
      - 파일 서버와 같이 드문 volume 접근 시 주로 사용된다.
      - Boot volume으로 사용할 수 없다.
    - Magnetic(Standard)
      - 디스크 1GB당 가장 싼 비용을 자랑한다.
      - Boot volume으로 유일하게 가능하다.

<br>

### ELB(Elastic Load Balancer)
- ELB란?
  - 로드 밸런서(Load Balancer)는 부하(load)를 적절하게 분배해주는 장치이다.
  - AWS에서는 ELB(Elastic Load Balancer)라는 이름으로 로드 밸런서를 제공한다.
  - 이 시스템은 자동으로 로드 밸런싱을 제공하며 시스템이 서버가 죽지 않도록 알아서 관리해준다.
- ELB의 종류
  - Classic Load Balancer
    - OSI Layer 4계층, 7계층에서 동작한다.
    - 현재는 Legacy로 간주되어 거의 사요되지 않는다.
  - Application Load Balancer
    - OSI Layer 7계층에서 동작한다.
    - HTTP, HTTPS와 같은 트래픽의 로드 밸런싱에 가장 적합하다.
    - 라우팅 설정을 통하여 특정 서버로 요청을 보낼 수 있다.
  - Network Load Balancer
    - OSI Layer 4계층에서 동작한다.
    - 매우 빠른 속도를 자랑하며 Production 환경에서 종종 사용된다.
    - 극도의 Performance가 요구되는 TCP 트래픽에서 적합하다.
    - 초당 수백만개의 요청을 아주 미세한 delay로 처리 가능하다.

<br>

### RDS(Relational Database Service)
- RDS란?
  - 데이터 베이스 인프라 및 업데이트들을 AWS 측에서 관리해주고 데이터베이스의 설치, 운영 그리고 관리 등의 서비스들을 지원하는 AWS의 관계형 데이터베이스이다.
  - AWS RDS는 MySQL, Oracle, SQL Server, PostgreSQL, MariaDB, Microsoft SQL Server 그리고 MySQL, PostgreSQL과 호환이 되는 Aurora DB를 제공한다.
- RDS 백업 시스템
  - 종류
    - 자동 백업(Automated Backups, AB)
      - 매일마다 스냅샷과 트랜잭션 로그를 참고하여 자동으로 백업을 해준다.
      - RDS에서는 디폴트로 AB 기능이 설정되어 있다.
      - AB를 통해 데이터베이스를 Retention Period(1~35일) 안의 과거 특정 시간으로 되돌아 갈 수 있다.
      - RDB 백업 정보는 S3에 저장되며, AB동안 약간의 I/O suspension(딜레이)이 존재할 수 있다.
    - 수동 백업 (DB 스냅샷)
      - 수동 백업은 유저 혹은 다른 프로세스로부터 요청에 따라 만들어지는 DB 스냅샷이다.
      - 만약 원본 RDS를 삭제한다고 하더라도, 스냅샷은 S3 버킷에 그대로 존재한다. 따라서 스냅샷만으로 RDS 인스턴스를 복원시킬 수 있다.
  - RDS 백업 복원시 도메인 변경
    - 원본 RDS 인스턴스를 가지고 새로운 DB를 복원시 새로운 인스턴스와 Endpoint가 생성된다.
    - 원본 DNS는 앞에 original인 반면, 복원된 것은 앞에 restored가 붙게된다.
    - <img width="737" alt="image" src="https://github.com/1992choi/aws/assets/27760576/580dfa94-358b-4981-8ce5-ba5732a71d8d">

<br>

### Multi-AZ와 Read Replica
- AWS RDS에는 가용성과 확장성을 위해 Multi-AZ라는 기능과 Read Replica라는 기능을 지원한다.
  - Multi-AZ
    - DR(Disaster Recovery)을 위해 서로 다른 AZ에 2개 이상의 Master DB를 배치하는 것을 의미한다.
    - Active - Standby 방식으로 동작한다.
    - 가용성이 주요 목적이다.
  - Read Replica
    - 서비스에서 읽기 위주의 작업이 많은 경우, Read Replica를 여러개 만들어 부하를 분산할 수 있다.
    - DB는 일반적으로 읽기 작업이 쓰기 작업보다 많다는 점에 기인하여, READ 트랜잭션은 Read Replica에서 처리하도록 애플리케이션을 설계한다.
    - 확장성이 주요 목적이다.

<br>

### ElastiCache
- ElastiCache란?
  - 분산 메모리 캐싱 서비스이다.
  - 주로 인메모리 데이터를 캐싱하여 응용 프로그램의 성능을 향상시킨다.
  - Redis 또는 Memcached와 같은 인메모리 캐시 엔진을 지원한다.
- 종류
  - Memcached
    - 데이터를 문자열 형태로만 저장하고 복잡한 데이터 구조를 지원하지 않는다.
    - Redis만큼 정교하지는 않지만 내부 메모리 관리는 단순한 경우에 매우 뛰어나다.
    - 주로 웹 애플리케이션에서의 세션 스토어나 데이터베이스 쿼리 결과 등을 캐싱하는 데 사용된다.
  - Redis
    - 다양한 데이터 포맷을 지원한다.
    - Multi-AZ를 지원한다.
    - 캐싱, 세션 스토어, 메시지 브로커, 키-값 저장소, 실시간 분석 등 다양한 용도로 활용된다.

<br>

### S3(Simple Storage Service)
- S3란?
  - AWS(Amazon Web Service)에서 제공하는 인터넷 스토리지 서비스이다.
  - 객체 저장공간을 제공한다.
- S3 특징
  - 객체만 업로드 가능하다.(이미지, 텍스트, 동영상 등만 가능. OS 등 불가능)
  - 파일 크기는 0KB ~ 5TB까지 업로드 가능하다.
  - 전제 저장 공간에 대한 제약은 없다.(=무제한 용량)
  - Bucket이라는 단위로 구분된다.(디렉토리의 개념)
- S3 객체의 구성
  - Key: 파일의 이름
  - Value: 파일의 데이터
  - Version ID: 파일의 버전 아이디
  - Metadata: 파일의 정보를 담은 데이터
- S3 일관성 모델
  - Read After Write Consistency(PUT)
    - 파일을 올리고 성공한 즉시 읽기 가능
    - 먼저 PUT한 요청이 우선권을 가진다.
  - Eventual Consistency(Update/Delete)
    - 파일을 삭제하거나 업데이트 이후 일정시간 후에 결과가 반영된다.
    - 원자성 확보 불가능
- S3 Storage Class
  - Standard
    - 가장 보편적으로 사용하는 스토리지 타입이며, 가장 일반적인 요금제이다.
    - 높은 내구성과 가용성을 가진다.
  - Standard IA
    - 자주 접근되지는 않으나 접근시 빠른 접근이 요구되는 파일이 많을시 저렴한 가격에 IA에 보관하면 유용하다.
    - 일반 S3에 비해 비용은 저렴하나 데이터를 불러올때마다 추가 비용 발생한다.
    - Multi AZ를 통한 데이터 저장이 가능하다.
  - One Zone IA
    - 기본적으로 IA와 같지만 하나의 AZ에만 데이터 저장하는 클래스이다.
    - 덜 중요하고 자주 사용되지 않는 데이터를 저장하는데 적합하다.
    - Standard IA와 트래픽 요금은 같지만 저장요금은 더 저렴(20%)하다. 
  - Glacier
    - 거의 접근하지 않을 데이터 저장 시 유용하며 매우 저렴한 비용을 자랑한다.
    - 데이터 접근시 대략 분~시간 소요될 정도로 상당히 오래걸린다.
  - Intelligent Tiering
    - 머신러닝을 통해서 자동으로 파일의 티어(클래스)를 변경 하는 서비스이다.
    - 파일에 자주 접근하면 스탠다드에 옮기고, 접근빈도가 낮으면 IA로 옮기고, 다시 많이 찾으면 스탠다드에 옮기는 형식이다.
- S3 암호화
  - S3에서는 보안을 위해 데이터 저장 및 전송 시 암호화할 수 있는 방식을 제공한다.
  - 암호화를 하는 주체에 따라 '서버측 암호화 / 클라이언트측 암호화 / 전송 중 암호화'로 나뉜다.
    - 서버측 암호화
      - SSE-S3 : AWS 회사 자체에서 관리 되는 keys를 이용해 암호화.
      - SSE-KMS : KMS(아마존 키 매니저 서비스 - AWS의 암호를 관리해주는 서비스)를 이용해 암호화.
      - SSE-C : 사용자에 의해 직접 정의된 keys를 이용해 암호화.
    - 클라이언트측 암호화
      - 데이터 저장 시에 S3에 의해 암호화가 되는 서버측 암호화와는 달리, 클라이언트 측 암호화 방식은 데이터 업로드 전에 암호화를 한 후 전송하는 방식이다.
      - 데이터 인출 시에도 클라이언트 측에서 복호화를 해야한다.
    - 전송 중 암호화(On Transit)
      - 통신 암호화 방식으로 SSL과 TLS가 사용된다.
      - HTTPS를 사용하면 클라이언트와 S3 사이를 이동하는 데이터가 모두 암호화되어 전송되기 때문에 Encryption in transit이라고 부른다.

<br>

### CloudWatch
- CloudWatch란?
  - AWS 리소스와 AWS에서 실시간으로 실행 중인 애플리케이션을 모니터링 하는 서비스이다.
  - 지표를 감시해 알림을 보내거나 임계값을 위반한 경우 모니터링 중인 리소스를 자동으로 변경하는 경보를 생성할 수 있다.
- CloudWatch의 경보(Alarm)
  - 경보란?
    - 수집된 지표값의 변동에 따라 발생하는 알림 생성으로, 지표가 일정 수치에 도달하거나 이상, 이하일 때 이벤트가 발생한다.
  - 경보의 상태
    - OK
      - 정상 상태.(OK일수록 좋은 상태라고 볼 수도 있다.)
    - Alarm
      - 알람이 발생한 상태.
    - Insufficient
      - 알람 상태를 확인하기 위해 정보가 부족함.

<br>

### Lambda
- Lambda란?
  - Lambda는 AWS가 제공하는 서버리스 FaaS 솔루션으로, 함수의 인스턴스를 실행하여 이벤트를 처리한다.
    - 서버리스란?
      - 서버리스란 개발자가 서버를 관리할 필요없이 클라우드에게 서버 관리를 맡기는 것이다.
    - FaaS(Function as a Servcie)
      - 프로그래밍에서 사용하는 메서드와 같이 함수를 서비스로 제공하는 것을 말한다.
      - 다시 말해 실행가능한 코드 덩어리 자체가 서비스이다.
      - 어떠한 이벤트를 받게 되면 등록된 함수를 실행하는 구조이다.
  - 코드를 업로드하기만 하면 Lambda가 자동으로 실행, 스케일링, 모니터링 등을 처리해주기 때문에 개발자는 인프라 관리보다는 비즈니스 로직에 더 집중할 수 있게된다.
- Lambda의 사용예시
  - 서버 띄우지 않고 간단한 코드를 실행시키고 싶은 경우
  - 특정 기간 또는 특정 주기로 코드를 실행시켜야 하는 경우
  - 트리거가 실행될때만 코드를 실행시키고 싶은 경우
- 특징
  - 필요할때만 함수가 호출되어 처리한다는 점에서 항상 서버를 켜두고 있지 않아도 되므로 비용을 절약할 수 있다.
  - 람다는 메모리(최대 10GB), 처리시간(최대900초)으로 제한되어 있다.
  - 람다는 리소스를 효율적으로 사용하기 위해서 오랫동안 사용하지 않고 있을 경우, 잠시 컴퓨팅 파워를 꺼두고 있다가 다시 실행되기 때문에 어느정도 딜레이가 발생(ColdStart)하게 된다.

<br>

### CloudFront
- CloudFront란?
  - CloudFront는 AWS에서 제공하는 CDN서비스이다.
  - 캐싱을 통해 사용자에게 좀 더 빠른 전송 속도를 제공함을 목적으로 한다.
  - CloudFront는 전 세계 이곳저곳에 Edge Location를 두고 Client에 가장 가까운 Edge Location를를 찾아 Latency를 최소화시켜 빠른 데이터를 제공한다.
- CloudFront 관련 용어
  - CDN(Content Delivery Network or Content Distribution Network, 콘텐츠 전송 네트워크)
    - 콘텐츠를 효율적으로 전달하기 위해 여러 노드를 가진 네트워크에 데이터를 저장하여 제공하는 시스템이다.
  - Edge Location
    - AWS에서 실질적으로 제공하는 전 세계에 퍼져있는 서버.
    - 요청받은 데이터에 대해서 같은 요청에 대해서 빠르게 응답해주기 위해 Cache 기능을 제공한다.
  - Origin
    - 원본 데이터를 가지고 있는 서버.
    - 보통 Origin Server에는 S3, EC2 instance 등이 있다.
- 데이터 전달 과정
  - ![image](https://github.com/1992choi/aws/assets/27760576/f4b01eaa-39a8-48b8-a0b9-3358c04368c9)

<br>

### DynamoDB
- DynamoDB란?
  - AWS에서 제공하는 서버리스 기반 Key-Value NoSQL 데이터베이스.
  - Auto-Scaling 기능을 탑재하고 있다.
  - SSD 스토리지 사용하여 읽고 쓰는 속도가 빠르다.
- 구조
  - ![image](https://github.com/1992choi/aws/assets/27760576/0d96cf40-0444-4eb3-90ed-6fa4de3772a5)
  - 아이템(Items)
    - 행(row)과 유사한 개념.
  - 특징(Attributes)
    - 열(column)과 유사한 개념.
  - Key-Value
    - Key : 데이터의 이름
    - Value : 데이터 자신
    - 예시) JSON, XML와 같은 Key-Value 형식
- DynamoDB의 PK
  - DynamoDB에는 두가지의 PK 유형이 있다.
    - 파티션키(Partition Key)
      - 데이터를 나누고 분리시키는 키. (RDB의 PK와 유사한 개념.)
      - 고유 특징 (Unique Attribute)
      - 실제 데이터가 들어가는 위치를 결정해준다.
      - 데이터가 저장될 때 어디로 저장될지 파티션 키 내부에 들어있는 해시함수를 통해 저장될 주소값이 결정된다.
      - 두 개의 데이터가 같은 위치에 저장될 수 없다.(=파티션키 중복 불가)
      - Hash 속성으로 Hash Key라고도 부르며 '같다' 혹은 '같지 않다'와 같은 연산만 가능하다.
    - 복합키(Composite Key)
      - 파티션키(Partition Key) + 정렬키(Sort Key)로 구성된다.
        - 정렬 키(Sort Key)
          - Range 속성으로 Sort Key라고도 부르며 비교대소 혹은 '~로 시작하는'과 같은 연산만 가능하다.
          - DynamoDB에서 데이터 정리를 위해 사용된다.
- Secondary Index(보조 인덱스)
  - Primary Key(Hash Key)만으로 DynamoDB에서 원하는 데이터에 대한 요청을 처리하는 것에 대해 비효율적인 엑세스 패턴이 발생할 수 있다.   
    이를 방지하고자 테이블에 대해 다른 엑세스 패턴을 설계할 수 있는 Secondary Index개념이 존재하며, RDB의 'View'와 비슷한 개념이다.
  - Secondary Index에는 로컬 보조 인덱스(Local Secondary Index, LSI)와 글로벌 보조 인덱스(Global Secondary Index, GSI)가 존재한다.
    - 로컬 보조 인덱스(Local Secondary Index, LSI)
      - 로컬 보조 인덱스는 파티션 키는 동일하지만 정렬 키는 다른 인덱스이다.
      - 파티션 키는 테이블의 기본 키와 동일하다.
      - 테이블을 생성할 때 함께 생성해야 하며, 테이블이 생성된 이후에는 추가, 수정, 삭제가 불가능하다.
    - 글로벌 보조 인덱스(Global Secondary Index, GSI)
      - 글로벌 보조 인덱스는 파티션 키와 정렬 키가 모두 다른 인덱스이다.
      - 테이블과 다른 파티션 키 및 정렬 키를 가질 수 있다.
      - 테이블 생성 후에도 생성할 수 있으며, 생성된 이후에도 추가, 수정, 삭제가 가능하다.
- Query와 Scan
  - DynamoDB에서는 데이터 조회를 위해 Query와 Scan 방식을 제공한다.
    - Query
      - 파티션 키와 정렬 키로 값을 읽어오는 방식.
      - Scan보다 빠르다.
    - Scan
      - 전체 데이터를 모두 읽어오는 방식.
      - Query보다 느리다.
      - 테이블의 크기가 상대적으로 크지않고 PK의 정의가 필요하지 않을 때는 Scan을 사용해도 상관없다. (=Look up Table 시 사용할 수 있다.)
- DAX(DynamoDB Accelerator)
  - In-memory를 사용하여 데이터를 캐시에 보관하는 것.
  - 캐시를 사용하기 때문에 필요한 데이터를 찾을 때, 빠르게 찾을 수 있다.
  - 읽기 요청만 해당하므로 읽기 요청이 많은 작업에 적합하다.
  - 원리
    - 직접 캐시에 데이터를 넣는 것이 아니라, DynamoDB 테이블에 데이터 삽입 & 업데이트 시 DAX에 반영된다.
    - 읽기 요청 시, 해당하는 데이터가 DAX에 있는 경우 DAX에서 데이터를 반환한다.
- DynamoDB Stream
  - DynamoDB 테이블에서 이벤트(삽입, 수정, 삭제 등) 발생 시, 시간 순서에 맞게 Stream에 기록.
  - 주로 이벤트를 기록하고 이벤트 발생을 외부로 알리는 용도.
    - Ex1) 그룹에 속한 친구가 사진을 새로 업로드하면 애플리케이션에서 그룹에 속한 모든 친구들에게 즉시 알림을 전송.
    - Ex2) 새로운 고객이 생기면 DynamoDB 테이블에 데이터가 추가되고, 해당 이벤트가 발생하면 새 고객에게 환영 이메일을 발송하는 애플리케이션 호출.

<br>

### API Gateway
- API Gateway란?
  - API Gateway는 API 서버 앞 단에서 모든 API 서버들의 엔드포인트를 단일화 해주는 또다른 서버이다.
  - API Gateway를 사용하면 RESTful API 및 WebSocket API를 쉽게 작성, 배포, 유지 관리할 수 있으며, 다양한 백엔드 서비스 및 프로토콜에 대한 지원을 제공한다.
- API 유형
  - HTTP API
    - API 프록시 기능정도만 필요할 때 적합.
    - 단순 / 저렴하고 빠르다.
  - REST API
    - API 관리 기능, 요청/응답에 대한 제어가 필요할 경우 적합.
    - 복잡 / 비싸고 느리다.
  - WebSocket API
    - 웹소켓 용도.
    - 실시간 애플리케이션에서 주로 사용한다.
- 주요 기능
  - 인증/인가 및 토큰 발급
  - 공통 로직 처리
  - 로드밸런싱
  - 메디에이션(Mediation)
    - Message Exchange Pattern
      - 동기호출을 비동기호출로 변환 가능.
      - ![image](https://github.com/1992choi/aws/assets/27760576/741d285c-c376-47af-8c56-f0240b620239)
    - Message Format Transformation
      - 클라이언트의 요청을 하위 서비스가 처리할 수 있도록 데이터 형식을 변형하거나, 하위 서비스의 응답 표준 포맷으로 데이터 형식을 변형.

<br>

### CI/CD
- CI/CD란?
  - CI
    - 개발자를 위한 자동화 프로세스인 지속적인 통합(Continuous Integration)을 의미한다.
    - CI가 제대로 구현되면 애플리케이션 코드의 새로운 변경 사항이 정기적으로 빌드 및 테스트를 거쳐 공유 리포지토리에 병합된다.
  - CD
    - 지속적인 서비스 제공(Continuous Delivery) 또는 지속적인 배포(Continuous Deployment)를 의미한다.
    - Downtime(서비스 중단 시간)을 최소화하여 사용자들이 서비스에 대한 연속적인 접근성을 유지하면서도 최신 버전의 소프트웨어를 이용할 수 있게 하는 것을 목적으로 한다.
- CodeCommit
  - CodeCommit이란?
    - 안전한 GIt 기반의 레포지토리를 클라우드 기반으로 제공하는 완전 관리형 소스 제어 서비스이다.
  - CodeCommit의 장점
    - 관리형 서비스
      - 하드웨어, 소프트웨어 관리 부담없이 하드웨어 프로비저닝 및 확장이 가능하다.
      - 소프트웨어 설치, 구성, 업데이트가 필요없다.
    - 높은 보안
      - CodeCommit 레포지토리는 유휴 상태에서도 데이터를 암호화하며, IAM과 통합되어 레포지토리에 사용자별 권한 할당이 가능하다.
    - 공동 작업
      - 브런치 병합 전 코드 변경사항 검토 및 설명 추가가 가능하며, 입력된 설명 내용을 이메일로 전송하는 알림 기능이 있다.
    - 타서비스 통합
      - 타 AWS 서비스와 다른 레포지토리와 함께 사용 가능하다.
    - 손쉬운 이전
      - 타 Git 기반 레포지토리에서 CodeCommit으로 마이그레이션 가능하다.
- CodeDeploy
  - CodeDeploy란?
    - EC2, On-premise, Lambda, ECS로 Application 배포를 자동화하는 배포 서비스이다.
  - 장점
    - AWS S3 버킷, Github Repository, BitBucket 레포지토리 등의 다양한 소스에서 배포할 수 있다.
    - 애플리케이션 업데이트 중에도 서비스 중단 시간을 최소화하여 사용자에게 지속적인 서비스를 제공할 수 있다.
    - 배포 중 실패가 감지되면 이전 버전으로 자동으로 롤백할 수 있어 안정성을 확보할 수 있다.
  - 배포 전략
    - Rolling 배포
      - ![image](https://github.com/1992choi/aws/assets/27760576/8617d592-e4c9-4151-bdfe-11daaf7ea77c)
      - 여러 개의 가동중인 서버 (인스턴스)를 갖춘 환경에서 한 번에 정해진 수만큼의 서버에 새로운 변경 사항이 포함된 어플리케이션을 배포하는 방법.
      - 서버 수의 제약이 있을 경우에는 유용한 방법.
    - Blue/Green 배포
      - ![image](https://github.com/1992choi/aws/assets/27760576/d7ba3a22-df01-4071-b90b-5dd2720657e3)
      - 새로운 변경사항이 포함된 어플리케이션을 위한 새로운 환경을 구축하고 교체하는 방법.
      - 버전 관리 문제를 방지할 수 있고, 운영 환경에 영향을 주지 않고 실제 서비스 환경으로 새 버전 테스트가 가능하다.
      - 롤백도 Rolling 배포에 비해 수월하다.
- CodePipeline
  - CodePipeline이란?
    - 코드 변경이 발생할 때마다 사용자가 정의한 릴리즈 모델을 기반으로 릴리즈 프로세스의 빌드, 테스트 및 배포 단계를 자동화한다.
    - 간단히 말해 CodeCommit, CodeBuild, CodeDeploy를 하나의 프로세스로 통합시켜주는 CI/CD 도구이다.
    - 이를 통해 Application의 변경 사항이나 새로운 기능을 신속하고 안정적으로 제공할 수 있다.
