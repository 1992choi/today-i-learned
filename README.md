# docker-devops
- Inflearn > DevOps를 위한 Docker 가상화 기술



<br><br>



## 정리
### 소프트웨어 아키텍처
- 소프트웨어 아키텍처란?
  - 무형의 지식 집합체(=코드)
  - 기능적인 측면보다는 안정적인 운영을 위한 전체적인 구조를 설계한다.
  - SW를 구성하는 요소와 요소 간의 관계를 정의한다.

### 가상화 방식의 변화
- ![image](https://github.com/user-attachments/assets/e9568a0d-9f8e-46ca-ab6c-b60d1cfdade5)
- 하이퍼바이저와 컨테이너
  - 하이퍼바이저
    - 하나의 컴퓨터에서 다수의 독립적인 OS를 운영한다.
    - Host OS 위에 다수의 Guest OS를 가상화하여 사용하는 방식이다.
    - 대표적으로 VMware, VirtualBox가 존재한다.
  - 컨테이너
    - 추가적인 Guest OS를 설치하여 가상화하는 방식은 성능면에서 이슈가 있고, 이를 개선하기 위해 프로세스를 격리된 환경에서 실행하는 기술, 즉 컨테이너 가상화 기술이 등장했다.
    - 운영체제 수준의 가상화 기술로 리눅스 커널을 공유함과 동시에 프로세스를 격리된 환경에서 실행한다.
    - 때문에 하이퍼바이저 가상화 방식보다 더욱 가볍고 빠르게 동작한다.

### 설치
- 설치 URL
  - https://www.docker.com/products/docker-desktop
- 버전 확인
  - docker --version

### Docker Image
- Docker Image란?
  - 도커를 통해서 실행하고자 하는 운영체제 / 미들웨어 / 어플리케이션 등을 제공하기 위한 하나의 템플릿으로 볼 수 있다.
  - 이미지 안에는 소스 코드와 라이브러리 등 구동을 위해 필요한 것들을 포함하고 있는 파일로 볼 수 있다.
  - 이미지를 토대로 실제로 실행되는 상태를 컨테이너라고 한다.
  - 이미지는 내부적으로 계층형 구조로 되어있으며, 이를 레이어 방식이라고 한다.
    - Ref. https://github.com/1992choi/docker?tab=readme-ov-file#%EC%9D%B4%EB%AF%B8%EC%A7%80-%EB%A0%88%EC%9D%B4%EC%96%B4

### Docker Container
- Docker Container란?
  - 도커 이미지를 실행한 상태
  - 인스턴스화 되어있는 상태
- Lifecycle
  - 컨테이너의 실행과 중지에 따른 상태 변화를 의미한다.
  - ![image](https://github.com/user-attachments/assets/f5aea19a-ed4e-4def-8ee6-905bc4f56b9d)
  - create
    - 컨테이너를 생성하는 명령어.
    - 아직 실행상태는 아니다.
  - start
    - 생성된 컨테이너를 실행상태로 만든다.
  - run
    - 컨테이너 생성과 동시에 실행 시킨다.
    - create와 start의 결합된 명령어
  - pause
    - 사용 중인 컨테이너를 일시중지한다.
  - unpause
    - 일시중지 시킨 컨테이너를 다시 실행한다.
  - stop
    - 컨테이너를 중지한다.
    - 컨테이너가 삭제되면, 다시 실행 상태로 돌아갈 수 없다.
  - start(Stopped 상태에서)
    - 중지한 컨테이너를 다시 실행한다.
  - rm
    - 컨테이너를 삭제한다.
- run 명령어
  - docker run [OPTION] IMAGE:[:TAG|@DIGEST][COMMAND][ARG..]
  - OPTION
    - -d / --detach
      - Detached mode(=background mode)로 실행
    - -p / --publish
      - 호스트와 컨테이너의 포트를 연결(포워딩)
    - -v / --volume
      - 호스트와 컨테이너의 디렉토리를 연결(마운트)
    - -e / --env
      - 컨테이너 내에서 사용할 환경변수 설정
    - --name
      - 컨테이너 이름 설정
    - --rm
      - 프로세스 종료 시 컨테이너 자동 제거
    - -it
      - -i와 -t를 동시에 사용한 것으로 터미널 입력을 위한 옵션
      - 키보드에 의해서 입력된 명령어가 컨테이너 내부로 전달될 때 사용한다.
    - -link
      - 컨테이너끼리 연결[컨테이너명:별칭]
