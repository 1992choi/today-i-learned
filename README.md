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
