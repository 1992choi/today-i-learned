# docker-devops
- Inflearn > DevOps를 위한 Docker 가상화 기술



<br><br>



## 정리
### 소프트웨어 아키텍처
- 소프트웨어 아키텍처란?
  - 무형의 지식 집합체(=코드)
  - 기능적인 측면보다는 안정적인 운영을 위한 전체적인 구조를 설계한다.
  - SW를 구성하는 요소와 요소 간의 관계를 정의한다.

<br>

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

<br>

### 설치
- 설치 URL
  - https://www.docker.com/products/docker-desktop
- 버전 확인
  - docker --version

<br>

### Docker Image
- Docker Image란?
  - 도커를 통해서 실행하고자 하는 운영체제 / 미들웨어 / 어플리케이션 등을 제공하기 위한 하나의 템플릿으로 볼 수 있다.
  - 이미지 안에는 소스 코드와 라이브러리 등 구동을 위해 필요한 것들을 포함하고 있는 파일로 볼 수 있다.
  - 이미지는 컨테이너 실행에 필요한 파일과 설정 값 등을 포함하고 있지만, 그 자체로는 상태값을 가지고 있지는 않다.
  - 이미지를 토대로 실제로 실행되는 상태를 컨테이너라고 한다.
  - 이미지는 내부적으로 계층형 구조로 되어있으며, 이를 레이어 방식이라고 한다.
    - Ref. https://github.com/1992choi/docker?tab=readme-ov-file#%EC%9D%B4%EB%AF%B8%EC%A7%80-%EB%A0%88%EC%9D%B4%EC%96%B4
- Docker Image 생성 방법
  - Dockerfile을 작성한다.
  - Dockerfile 작성 후 명령어를 사용하여 생성한다.
    - docker image build --tag [tag명] -f 파일명 .
      - Ex) docker image build --tag [first-iamge:0.1] -f Dockerfile .
      - build는 이미지에서만 사용되는 명령어기 때문에 image를 생략할 수 있다.
      - --tage 대신 -t로 사용 가능하다.
      - 태그 번호인 :0.1을 생략하면 최신버전을 뜻하는 latest가 된다.
      - 마지막 온점(.)은 현재 디렉토리를 의미하는 경로이다.
- Docker Image의 생성과 사용 Flow
  - ![image](https://github.com/user-attachments/assets/c2aa8969-e988-4334-9841-6d6c7b8489cd)

<br>

### Dockerfile
- Dockerfile이란?
  - Dockerfile은 docker에서 이미지를 생성하기 위한 용도로 작성하는 스크립트 파일이다.
  - 만들 이미지에 대한 정보를 기술해 둔 템플릿(template) 이라고 보면 된다.
  - 자체 DSL(Domain-Specific Language) 언어를 사용하여 이미지 생성과정을 기술한다.
  - 파일로 만들어지기 때문에 버전관리가 가능하며, 누구나 수정할 수 있기 때문에 공유하거나 유지보수 하는데도 유리하다.
- Dockerfile 작성 명령어
  - FROM
    - Base Image를 지정한다.
  - RUN
    - 특정 Layer를 생성한다.
    - 이 말인 즉슨, 실제 컨테이너 안에서 실행 할 명령어를 기입한다는 것이다.
  - COPY
    - 이미지 파일 생성 시, 호스트 파일을 복사한다.
  - ADD
    - 이미지 파일 생성 시, 호스트 파일을 복사한다.
    - COPY와의 차이점은 ADD는 압축파일을 복사할 수도 있고, 특정 url에서 파일을 가져온 후 복사할 수도 있는 명령어이다.
  - WORKDIR
    - 이미지 파일 생성 시, 명령어가 실행 될 작업 디렉토리를 지정한다.
  - ENTRYPOINT
    - 컨테이너가 실행 될 때, 가장 먼저 실행될 프로그램을 지정한다.
    - 컨테이너 실생 시, 명령어 overwrite 불가능
  - CMD
    - 컨테이너가 실행 될 때, 가장 먼저 실행될 프로그램을 지정한다.
    - 컨테이너 실생 시, 명령어 overwrite 가능
  - ENV
    - 컨테이너 내의 환경변수를 설정한다.
  - EXPOSE
    - 컨테이너의 특정 포트를 외부에 오픈한다.

<br>

### Docker Registry
- Docker Registry란?
  - Docker를 통해 생성하는 Image들을 저장해주는 저장소이다.
  - 모두에게 공개된 Public Registry와 일부만 접근을 허용하는 Private Registry가 존재한다.
  - CI/CD를 위한 자동화 Pipeline을 구축하는데 사용하기도 한다.
- Local Registry 구축
  - Local Registry 실행
    - docker run -d -p 5001:5000 --restart always --name registry registry:2
  - Repositories 리스트 확인
    - curl http://localhost:5001/v2/_catalog
  - Tag
    - 기존 이미지에 태그를 수정하여 새로운 이미지명을 만들 목적
    - Ex) docker tag ubuntu:16.04 localhost:5001/ubuntu:16.04
    - localhost:5001를 생략하면, Docker Hub에서 가져오겠다는 의미이다.
    - <img width="875" alt="image" src="https://github.com/user-attachments/assets/41df8ad5-1dd6-4167-ab3f-4b441e047a9a">
  - 이미지 업로드
    - docker push localhost:5001/ubuntu:16.04
    - 'curl http://localhost:5001/v2/_catalog' 명령어를 수행하면, Repositories 리스트에서 업로드한 이미지를 확인할 수 있다.
  - 이미지 가져오기
    - docker pull localhost:5001/ubuntu:16.04
- Cloud Registry 사용
  - Repository 생성
    - https://hub.docker.com로 접속하여 Repository를 생성한다.
  - TAG
    - docker tag ubuntu:16.04 [계정명]/ubuntu:16.04
  - 이미지 업로드
    - Cloud Registry로 이미지를 업로드한다.
    - docker push [계정명]/ubuntu:16.04
  - 이미지 가져오기
    - docker pull [계정명]/ubuntu:16.04

<br>

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

<br>

### Docker Container 명령어(1)
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

<br>

### Docker Container 명령어(2)
- docker container ls [OPTION]
  - 컨테이너 목록 조회
  - docker ps와 동일
- docker container stop [OPTION] CONTAINER [CONTAINER ...]
  - 컨테이너 중지
- docker container rm [OPTION] CONTAINER [CONTAINER ...]
  - 컨테이너 삭제
- docker container logs ${CONTAINER_ID}
  - 컨테이너 로그 메시지 확인
  - CONTAINER_ID 대신 CONTAINER_NAME을 사용할 수도 있다.
- docker container exec [OPTION] CONTAINER COMMAND [ARG ...]
  - 컨테이너에게 명령어 전달
- docker container inspect ${CONTAINER_ID}
  - 컨테이너의 세부 정보 조회 
- docker image ls [OPTION] CONTAINER [REPOSITORY[:TAG]]
  - 이미지 목록 조회
  - docker images와 동일
- docker image rm [OPTION] IMAGE [IMAGE ...]
  - 이미지 삭제
  - 작동 중인 컨테이너가 있다면, 중지하고 삭제해야한다.
- docker image pull [OPTION] NAME[:TAG|@DIGEST]
  - 이미지를 가져온다.
  - image를 생략하고 docker pull로 사용할 수도 있다.
- docker system prune
  - 사용되지 않는 컨테이너 / 이미지 등을 정리한다.

<br>

### Port Mapping
- Port Mapping이란?
  - 도커 컨테이너에서 사용하고자 하는 Port를 자요롭게 설정하는 기능이다.
  - 호스트 시스템에서 도커 컨테이너 Port를 사용하기 위해서는 Post Mapping이 필요하다.
- 명령어
  - docker run -p host_port:container_port [IMAGE_NAME]
  - Ex) docker run -p 80:8080
    - 도커 컨테이너 내부에서 8080 포트를 사용하는 톰캣이 있다고 가정할 때, HOST PC에서 톰캣을 호출할 때 80 포트로 접근할 수 있다.

<br>

### Docker Network
- Docker Network란?
  - Docker 컨테이너 간의 통신을 관리하고 격리하기 위한 기능을 제공하는 것이다.
- 특징
  - Container Isolation
    - 컨테이너는 격리 된 환경에서 동작하므로 서로 다른 컨테이너끼리는 통신이 불가능하다.
  - 도커 네트워크는 이러한 특징을 보완하기 위하여 다른 컨테이너 간의 통신을 쉽게 설정하고 관리할 수 있도록 도와준다.
- 종류
  - Bridge Network
    - 가장 기본적인 상태의 네트워크이다.
    - 하나의 Host PC에 여러 개의 컨테이너들이 서로 연결 가능한 상태이다.
  - Host Network
    - Host PC와 동일한 네트워크를 사용하는 형태이다.
    - 포트 포워딩 없이 내부 애플리케이션 사용 가능
  - None Network
    - 네트워크를 사용하지 않는 형태이다.
  - Overlay Network
    - 여러 Host에 분산되어있는 컨테이너를 연결할 때 사용하는 형태이다.
- 명령어
  - docker network ls
    - 네트워크 목록을 조회한다.
  - docker network inspect [NETWORK_NAME]
    - 네트워크 상세정보를 조회한다.
  - docker network create [NETWORK_NAME]
    - 네트워크를 생성한다.
  - docker network rm [NETWORK_NAME]
    - 네트워크를 삭제한다.
  - docker network connect [NETWORK_NAME] [CONTAINER]
    - 실행 중인 컨테이너를 Network에 추가한다.
  - docker network disconnect [NETWORK_NAME]}[CONTAINER]
    - Network에 추가된 컨테이너를 삭제한다.

<br>

### Multi Container 구성 예제
- 네트워크 생성
  - ```
    docker network create --driver bridge my-network
    ```
- DB 생성 및 네트워크 설정
  - ```
    docker run -d -p 13306:3306 --network my-network \
    -e MARIADB_ALLOW_EMPTY_ROOT_PASSWORD=true \
    -e MARIADB_DATABASE=mydb \
    --name my-mariadb edowon0623/my-mariadb:1.0
    ```
- Backend 생성 및 네트워크 설정
  - ```
    docker run -d -p 8088:8088 --network my-network \
    -e "spring.datasource.url=jdbc:mariadb://my-mariadb:3306/mydb" \
    --name catalog-service edowon0623/catalog-service:mariadb-demo
    ```
  - 위의 명령어에서 MariaDB Host를 할당받은 IP대신 my-mariadb로 적는 이유는
    - IP를 적으면 네트워크 할당 순서에 따라 MariaDB의 IP가 변경될 수 있기 때문에 컨테이너명을 기재한다.
    - 도커에서는 컨테이너명이 호스트명으로도 쓰이기 때문이다.
- 조회
  - http://localhost:8088/catalogs

<br>

### Docker Volume Storage
- Docker Volume이란?
  - Docker는 개별적인 가상환경이기 때문에 컨테이너가 삭제되면, 작업했던 모든 데이터도 삭제된다.
  - 컨테이너 내부의 데이터를 외부로 연결 시켜주는 기능이 도커 볼륨이다.
- Docker Volume 경로
  - docker volume inspect 명령어를 통해 Mountpoint의 값으로 볼륨의 경로를 알아낼 수 있다.
    - 하지만 Host PC에서 해당 경로를 찾아갈 수는 없다.
    - 리눅스에서는 해당 경로에 접근 가능하지만, 이외의 OS에서는 도커를 직접 설치한 것이 아니라 도커 데스크탑을 통해 설치하여 해당 경로로 이동할 수 없는 것이다.
    - 만약 Host PC에서 접근 가능한 경로로 마운트하고 싶을 때는 v 옵션에 현재 경로를 뜻하는 온점(.)부터 명시하면 된다.
      - Ex) docker run -v ./docker_data:/app/test ubuntu:16.04 bash
        - 현재 경로에 docker_data 디렉토리를 만들고 이를 컨테이너의 /app/test 디렉토리와 마운트 시킨다는 의미. 
- 명령어
  - 생성
    - docker volume create [볼륨명]
  - 목록조회
    - docker volume ls
  - 상세조회
    - docker volume inspect [볼륨명]
  - 삭제
    - docker volume rm [볼륨명]
  - 컨테이너 생성 시 볼륨 연결
    - docker run -v [볼륨명]:[컨테이너 내부 디렉토리 경로] --name [컨테이너명][이미지 이름]
- 실습내용
  - OS 실습
    - OS 실행 시 볼륨 옵션을 통해 파일 등의 데이터를 유지할 수 있다.
      - 볼륨 옵션을 사용한다면, 컨테이너를 지운 후 새로운 컨테이너를 생성하더라도 기존 데이터가 남아있게 운영할 수 있다.
      - Host PC에서 데이터를 생성하면, 컨테이너 경로에도 파일이 만들어진다.
      - 반대로 컨테이너에서 파일을 생성하면 Host PC(=볼륨 경로)에도 파일이 만들어진다.
  - DB 실습
    - DB 실행 시 볼륨 옵션을 통해 테이블 및 데이터를 유지할 수 있다.
      - 볼륨 옵션을 사용한다면, 컨테이너를 지운 후 새로운 컨테이너를 생성하더라도 기존 데이터가 남아있게 운영할 수 있다.

<br>

### Docker Compose
- Docker Compose란?
  - 컨테이너 애플리케이션을 정의하고 실행하는 도구.
  - 여러 개의 컨테이너를 동시에 실행하고 할 때, 각 컨테이너별로 별도의 명령어를 통해 실행해야 한다.
    - 10개의 컨테이너를 실행한다고 가정하면, 10개의 명령어가 필요하며, 네트워크, 볼륨 등 까지 설정해야 한다면 그 이상이 될 수도 있다.
    - 도커 컴포즈는 이러한 명령어를 하나로 묶어 관리할 수 있는 기술을 의미한다.
  - Docker 생성, 설정 관련 된 작업을 작성해 놓은 Script 파일(=Docker Compose 파일)을 사용한다.
- Docker Compose 파일 작성 및 실행
  - 작성
    - 기본적인 파일명은 docker-compose.yml이지만, 다른 이름으로 작성할 수도 있다.
    - 기본 파일명으로 작성하면 실행 명령어에서 파일명을 기재하지 않아도 되지만, 기본 파일명이 아니라면 파일명을 명시해줘야한다.
    - 파일 예시
      - ![image](https://github.com/user-attachments/assets/c32baee4-bbb6-4a72-8969-b5b64a99e400)
  - 실행
    - docker-compose up
      - 파일명이 docker-compose.yml인 경우
    - docker-compose -f docker-compose-dev.yml up
      - 파일명이 docker-compose-dev.yml인 경우에는 기본 파일명이 아니므로 명시해줘야한다.
