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

### IAM (Identity and Access Management)
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

### EC2 (Elastic Compute Cloud)
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

### EBS (Elastic Block Storage)
- EBS란?
  - Elastic Block Store의 약자로 Amazon EC2 인스턴스에서 사용할 수 있는 블록 수준 스토리지 볼륨을 제공하는 서비스이다.
  - EC2 안에 부착되어 있는 일종의 하드 디스크이다.
  - EBS는 특정 Availability Zone에 생성된다.
    - Availability Zone (AZ)
      - 가용 영역이라한다.
      - 하나 이상의 데이터 센터로 구성되어져있는 논리적인 데이터센터이다.
      - 한쪽 서버가 망가져도 서비스를 유지시켜준다.
      - 중심부로부터 그의 복사본들이 AZ로 뿌려지며 한쪽 서버가 망가지거나 셧다운 됐을 경우, AZ라는 백업을 통해 서비스 제공을 가능하게 해주는 일종의 Disaster Recovery라고 볼 수 있다.
- EBS 볼륨 타입
  - SSD군
    - General Purpose SSD (GP2)
      - 최대 10K IOPS 지원하며, 1GB당 3IOPS 속도가 나온다.
    - Provisioned IOPS SSD (IO1)
      - 극도의 I/O률을 요구하는(예시 : 매우 큰 DB 관리) 환경에서 주로 사용된다.
      - 10K이상에서 IOPS 지원한다.
  - Magnetic / HDD군
    - Throughput Optimized HDD(ST1)
      - 빅데이터 Datawarehouse, Log 프로세싱 시 주로 사용된다.
      - Boot volume으로 사용할 수 없다.
    - CDD HDD (SC1)
      - 파일 서버와 같이 드문 volume 접근 시 주로 사용된다.
      - Boot volume으로 사용할 수 없다.
    - Magnetic(Sandard)
      - 디스크 1GB당 가장 싼 비용을 자랑한다.
      - Boot volume으로 유일하게 가능하다.

<br>

### ELB
-
















