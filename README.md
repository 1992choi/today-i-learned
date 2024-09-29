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
    - 만약 Host PC에서 접근 가능한 경로로 마운트하고 싶을 때는 v 옵션에 접근가능한 경로를 명시하면 된다.
      - Ex) docker run -v /User/choi/docker_data:/app/test ubuntu:16.04 bash
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
    - 명령어
      - image
        - Docker Image를 지정한다.
      - build
        - Dockerfile을 이용하여 이미지를 빌드할 때 사용할 수 있다.
      - command 또는 entrypoint
        - 컨테이너 안에서 작동하는 명령어 지정
      - ports 또는 expose
        - 컨테이너 간 통신을 위한 포트 설정
      - depends on
        - 서비스의 의존 관계를 정의한다.
        - 컴포즈를 통해서 컨테이너가 기동될 때, 순차적으로 기동되는 것이 아니라 병렬로 기동된다.
          - 만약 B 컨테이너는 A 컨테이너 이후에 기동되야한다면, 이때 사용할 수 있는 명령어이다.
          - 하지만 해당 명령어는 절대적으로 순서를 보장해주지는 않는다.
      - environment 또는 env_file
        - 컨테이너 환경변수 지정
      - container_name 또는 labels
        - 컨테이너 정보 설정
        - docker ps 명령어에서 나오는 컨테이너 이름을 명시할 용도로 사용할 수 있다.
      - volumes 또는 volumes_from
        - 컨테이너 데이터 관리
  - 실행
    - docker-compose up
      - 파일명이 docker-compose.yml인 경우
    - docker-compose -f docker-compose-dev.yml up
      - 파일명이 docker-compose-dev.yml인 경우에는 기본 파일명이 아니므로 명시해줘야한다.
  - 목록 조회
    - docker-compose.yml 파일이 있는 동일 경로에서만 가능하다.
    - docker compose 내에서 관리하는 컨테이너의 상태만 조회 가능하다.
      - docker-compose ps
      - docker-compose -f docker-compose-dev.yml ps
  - 중지
    - docker-compose down
    - docker-compose -f docker-compose-dev.yml down
  - 그 외 실행 명령어
    - docker-compose logs
      - 컨테이너 로그를 출력한다.
    - docker-compose run
      - 컨테이너 실행
      - docker-compose up 이후에 실행되지 않은 컨테이너를 개별적으로 제어하기 위해 사용할 수 있다.
    - docker-compose stop
      - 컨테이너 중지
      - 컨테이너를 개별적으로 제어하기 위해 사용할 수 있다.
    - docker-compose port
      - 공개 포트 번호 표시
    - docker-compose rm
      - 컨테이너 삭제
    - docker-compose config
      - 구성 확인

<br>

### Docker Compose를 활용한 IT 서비스 구축
- 강의내용
  - Docker Compose를 활용하여 DB, BE, FE를 구축한다.
  - section5 > Docker Compose를 활용한 IT 서비스 구축 ②
- 실습파일 경로
  - /docker-devops/section5/docker-compose.yml
- 실습내용
  - 실행
    - docker-compose.yml 파일이 있는 경로에서 실행한다.
    - docker-compose -f docker-compose.yml up -d my-db
      - 백엔드 컨테이너 실행 전에 DB가 실행되야하므로 위의 명령어를 통해 DB부터 실행한다.
      - 백엔드 실행옵션에 depends_on이 명시되어 있기는 하지만, 절대적인 것이 아니므로 위와 같이 DB를 먼저 실행하는 것도 가능하다.
    - docker-compose -f docker-compose.yml up -d
      - DB실행 이후 다시 명령어를 수행해서 전체를 다 실행시킨다.
      - 이 때, 이전에 DB는 실행된 상태이므로 중복되서 실행되지 않고, 백엔드 컨테이너와 프론트엔드 컨테이너만 실행된다.
  - 중지 및 삭제
    - docker-compose -f  docker-compose.yml stop my-backend
      - 만약 백엔드를 중지해야한다면, 위와 같은 명령어로 특정 컨테이너만 중지할 수 있다.
    - docker-compose -f  docker-compose.yml rm my-backend
      - 특정 컨테이너만 삭제할 수 있다.
  - 로그
    - 모든 컨테이너 확인
      - docker-compose -f  docker-compose.yml logs
    - 특정 컨테이너 확인
      - docker-compose -f  docker-compose.yml logs my-db

<br>

### 컨테이너 오케스트레이션 도구
- 컨테이너 오케스트레이션 도구란?
  - 컨테이너의 배포, 관리, 확장, 네트워킹을 자동화 해주는 도구
  - 수백, 수천 개의 컨테이너와 호스트를 배포하고 스케줄링하기 위해 사용되는 도구
- 컨테이너 오케스트레이션 활용 예시
  - 프로비저닝 및 배포
  - 구성 및 일정 조정
  - 리소스 할당
  - 컨테이너 가용성
  - 컨테이너 스케일링
  - 로드밸런싱 및 트래픽 라우팅
  - 컨테이니ㅓ 상태 모니터링

<br>

### Docker Swarm
- Docker Swarm
  - 여러 Docker host를 클러스터로 묶어주는 컨테이너 오케스트레이션
  - 여러 컨테이너를 관리한다는 측면에서는 docker compose와 유사하나, compose는 주로 단일 호스트에서 이용하는 반면에 Swarm은 멀티 호스트에서 사용된다.
- 멀티 노드의 Swarm Cluster 구성
  - Swarm Cluster의 초기화를 담당하는 노드를 Manager 노드라고 한다.
  - Manager 노드에 등록되어 컨테이너를 배포하는 등의 실제 일을하는 노드를 Worker 노드라고 한다.
  - 구성예시
    -  총 3대의 PC인 A, B, C가 있다고 가정할 때, A PC에서 docker swarm init 명령어를 입력하면 Swarm 모드가 활성화되며 A PC가 Manager 노드가 된다.
    -  이 때 토큰이 발행되는데, 이 토큰을 사용하여 Worker 노드들을 Manager 노드에 등록할 수 있다.
    -  토큰을 사용하여 B, C를 등록하면 B와 C는 Worker 노드가 된다.
- Docker Swarm을 이용한 시스템 구축
  - 구축 방법
    - 2대 이상의 PC 환경에서 구축이 가능하기 때문에, 아래의 방법으로 환경 구축이 가능하다.
      - 2대 이상의 PC 사용
      - 1대의 PC와 VM을 활용한 구축 방법
      - 1대의 PC와 Docker in Docker(=dind)를 활용한 구축 방법
        - 도커 컨테이너 안에서 도커 호스트를 실행하는 방법
        - 도커 컨테이너로 Linux를 실행 후, 도커를 설치
  - 명령어 예시
    - docker exec -it manager docker swarm init
      - Manager 컨테이너에 Swarm 모드를 활성화한다.
    - docker exec -it worker01 docker swarm join --token [JOIN TOKEN] manager:2377
      - Worker 컨테이너를 Manager 컨테이너에 등록한다.
  - Swarm에서 사용되는 주요 포트
    - 2377
      - cluster managerment 통신에 사용되는 포트번호
    - 7946
      - node간의 통신에 사용되는 포트번호
    - 4789
      - overlay network 트래픽에 사용되는 포트번호
  - 실습
    - Manager 노드 생성
      - ```
        docker run --privileged --name manager -itd -p 10022:22 -p 8081:8080 -e container=docker -v /sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host edowon0623/docker-server:m1 /usr/sbin/init
        ```
    - Manager 노드 접속
      - ```
        docker exec -it manager bash
        ```
    - Manager 노드 접속 후 데몬 실행
      - ```
        # 자동실행되도록 설정
        $ systemctl enable docker

        # 도커 데몬 실행
        $ systemctl start docker

        # 도커 실행 후 상태 확인
        $ systemctl status docker
        ```
    - Manager 노드에서 swarm 초기화
      - ```
        docker swarm init
        ```
      - init이 정상적으로 실행되면, 콘솔창에서 join 명령어를 확인할 수 있다.
        - docker swarm join --token SWMTKN-1-0a1c95nj0c83nerwcmiddrwlqzbag25vg2jdxthfgorr01lc82-71rslfxwxy0si2oqs443sl2wo 172.17.0.2:2377
    - Worker 노드 생성
      - ```
        docker run --privileged --name worker1 -itd -p 20022:22 -p 8082:8080 -e container=docker -v /sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host edowon0623/docker-server:m1 /usr/sbin/init

        docker run --privileged --name worker2 -itd -p 30022:22 -p 8083:8080 -e container=docker -v /sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host edowon0623/docker-server:m1 /usr/sbin/init
        ```
    - Worker 노드 접속
      - ```
        docker exec -it worker1 bash
        docker exec -it worker2 bash
        ```
    - Worker 노드 접속 후 데몬 실행
      - ```
        # 자동실행되도록 설정
        $ systemctl enable docker

        # 도커 데몬 실행
        $ systemctl start docker

        # 도커 실행 후 상태 확인
        $ systemctl status docker
        ```
    - Worker 노드에서 Manager 노드로 JOIN
      - ```
        docker swarm join --token SWMTKN-1-0a1c95nj0c83nerwcmiddrwlqzbag25vg2jdxthfgorr01lc82-71rslfxwxy0si2oqs443sl2wo 172.17.0.2:2377
        ```
    - Manager 노드에서 노드 목록 확인
      - ```
        docker node ls
        ```

<br>

### Docker Swarm Service
- Docker Swarm Service
  - 애플리케이션을 구성하는 일부 컨테이너를 제어하기 위한 단위
  - Manager 노드에서 수행하면, Worker 노드로 명령어가 전달되어 실행되게 된다.
- 실습
  - docker service create --replicas 1 --publish 80:80 --name my-nginx nginx:latest
    - 서비스를 배포한다. (현재는 nginx로 예시로 실습)
    - replicas : 컨테이너 실행 갯수를 지정하는 옵션
      - Manager 노드도 Worker 노드처럼 동작하므로, 현재 3개의 노드를 생성한 것과 마찬가지이다.
      - 이 때 갯수가 1개이므로 Manager 노드와 Worker 노드 2개 중에 랜덤으로 1개에서 nginx가 생성된다.
      - 옵션을 통해 노드를 지정할 수도 있다.
      - scale 명령어로 갯수를 늘릴 수도 있다.
        - docker service scale my-nginx=3
  - docker service ls
    - 서비스 목록을 조회한다.
  - docker service scale my-nginx=3
    - 컨테이너 수평 확장을 한다.
    - 만약 Worker 노드에서 nginx를 중지 후 삭제한 후, docker ps -a 명령어를 입력하면 그대로 1개가 조회된다.
      - 그 이유는 scale 옵션을 3으로 주었기 때문에, Manager 노드에서 자동으로 다시 서비스를 실행시키기 때문이다.

<br>

### Docker Swarm Stack
- Docker Swarm Stack
  - 하나 이상의 서비스를 그룹으로 묶은 단위이다.
  - Docker Swarm Service는 애플리케이션 이미지를 하나 밖에 다루지 못하는 반면에 Stack은 여러 서비스를 한꺼번에 다룰 수 있다.
  - Docker Swarm Stack을 사용하여 배포 된 Service 그룹은 overlay 네트워크에 속한다.
- Stack 활용
  - Stack 배포
    - Manager에서 실행한다.
    - docker stack deploy -c /stack/stack sample.yml my-stack
  - 배포 확인
    - docker stack services my-stack
  - Stack에 배포 된 컨테이너 확인
    - docker stack ps my-stack
  - Stack 삭제
    - docker stack rm my-stack
- 실습
  - 실습파일
    - section6/docker-compose.yml
      - manager / worker 노드를 조금 더 쉽게 생성하기 위함.
      - 이전 실습에서는 노드 생성을 위해 비슷한 docker run 명령어를 3번 반복하였는데, 이를 줄이고자 docker-compose 활용. 
    - section6/stack/haproxy.cfg
      - proxy 설정을 위한 파일.
      - 기본 설정을 대체할 용도.
    - section6/stack/stack_sample.yml
      - network 및 프록시 설정을 담고 있다.
      - replica의 정보(= 컨테이너의 scale 관련 옵션)를 담고 있다.
      - deploy.placement.constraints: [node.role == worker]의 의미는 manager가 아닌 worker 노드에만 배포하겠다는 의미.
  - 실습진행
    - docker-compose up -d
      - docker-compose.yml 경로에서 실행
      - manager 노드와 worker 노드를 생성한다.
    - 노드 접속 / 도커 데몬 실행 / Swarm 실행 및 JOIN
      - 앞서 실습했던 내용과 동일하게 진행한다.
      - 노드 접속 > 노드 접속 후 도커 데몬 실행 > Swarm 실행 및 JOIN
    - overlay network 생성
      - docker network create --driver overlay my-overlay-network
    - stack 파일 실행
      - cd /stack
        - volume 옵션을 통해 stack 디렉토리 내에 파일이 이미 옮겨졌을 것이다.
      - docker stack deploy -c /stack/stack_sample.yml my-stack
        - stack을 실행한다.
    - 서비스 확인
      - localhost:8000 실행
        - manager 노드의 nginx 80포트와 8000포트를 매핑시켜 놓았다.
        - 웹의 요청을 받은 manager는 HAProxys를 사용하여 worker 1번 또는 2번의 nginx을 호출한다.

<br>

### Rolling Updates & Rollback
- Rolling Updates
  - 무중단 배포의 종류 중 하나이다.
  - 서비스의 각 태스크를 한 번에 업데이트하지 않고, 지연 시간을 설정하여 태스크를 순차적으로 업데이트한다.
  - ![image](https://github.com/user-attachments/assets/2c92e28d-ce5a-46ed-b6c3-cd8787ba1f3d)
- Rollback
  - 이전 버전으로 돌아가기 위한 작업이다. 
- Updates 실습
  - 서비스 생성
    - docker service create --replicas 4 --name myweb --update-delay 10s --update-parallelism 2 nginx:latest
      - replicas 4 : 4대를 생성
      - update-delay 10s : 업데이트 시, 10초 간격으로 업데이트
      - update-parallelism 2 : 2대씩 처리
  - 업데이트
    - docker service update --image nginx:1.24 myweb
      - nginx 버전을 1.24로 업데이트 한다.
      - 위에서 설정한 옵션으로 인하여 2대씩 처리되며, 10초 간격으로 업데이트 된다.
        - docker service ps myweb 명령어로 중지, 실행 시간으로 확인 가능하다.
- Rollback 실습
  - 서비스 생성
    - docker service create --name myweb3 --replicas 4 --rollback-delay 10s --rollback-parallelistm 1 --rollback-failure-action pause nginx:latest
      - rollback-delay 10s : 10초 주기로 롤백 진행
      - rollback-parallelistm 1 : 1개씩 롤백 진행
      - rollback-failure-action pause : 롤백 실패 시, 중지
  - 업데이트
    - docker service update --image nginx:1.24 myweb
      - 롤백 테스트를 위해 업데이트를 진행한다.
  - 롤백
    - docker service update --rollback myweb3
      - 롤백을 진행한다.
      - 롤백은 직전 단계로만 되돌릴 수 있다. (이전 몇 단계를 롤백하는 것은 불가능하다.)

<br>

### Docker 이미지 관리
- Docker 이미지 관리
  - 작업 중인 커테이너를 이미지로 저장할 수 있다.
    - docker commit
  - 이미지를 백업할 수 있다.
    - docker save 명령어를 통해 이미지를 tar 파일 형태로 export할 수 있다.
  - 이미지를 복원할 수 있다.
    - 백업된 파일을 docker load 명령어를 통해 이미지를 복원할 수 있다.
- 실습
  - commit
    - docker commit [CONTAINER_ID] [IMAGE_NAME:TAG]
    - Ex) docker commit 73caca0e41bd 1992choi/docker-server:1.0
  - save
    - dokcer save [OPTION] [TAR_FILE_NAME] [IMAGE_NAME:TAG]
    - Ex) docker save -o docker-server.tar 1992choi/docker-server:1.0
  - load
    - docker load -i [TAR_FILE_NAME]
    - Ex) docker load -i docker-server.tar

<br>

### Docker 보안
- Docker 보안
  - 도커 보안은 크게 4가지 범주로 나눌 수 있다.
    - Docker Daemon Security
      - 컨테이너 실행을 위한 도커 엔진에 대한 보안
    - Container Image Security
      - 컨테이너 이미지가 안전하게 생성 되었는지 검증
    - Container Isolation
      - 컨테이너의 실행이 다른 컨테이너나 호스트에 영향을 주지 않는 독립적인 실행 환경 구성
    - Runtime Security
      - 컨테이너 실행동안 지속적인 모니터링과 관리
- Docker Daemon Security
  - Docker daemon은 Root 권한을 가지고 실행되기 때문에 주의 깊은 보안 관리가 필요하다.
  - 루트의 접근 권한을 제한한다.
    - 루트 대신에 일반 사용자 계정 사용 검토
  - TLS를 활성화한다.
  - API Access를 제한한다.
- Container Image Security
  - 취약점이 없는 컨테이너 이미지를 사용한다.
    - 검증된 기본 이미지를 사용한다.
  - 보안 취약점 점검
    - clair, Trivy, Docker Security Scanning과 같은 툴을 사용하여 취약점 점검을 주기적으로 수행한다.
  - 이미지 크기 최소화
    - 필요한 것만 최소화하여 이미지를 사용한다.
      - Ex) alpine 이미지 사용
  - Docker Scout
    - Docker Desktop에서 기본으로 제공하는 이미지 분석 툴이다.
    - 다양한 옵션으로 분석이 가능하다.
      - docker scout quickview 1992choi/docker:latest
      - docker scout recommendations 1992choi/docker:latest
- Container Isolation
  - 컨테이너와 호스트는 기본적으로 격리된 상태이다.
  - 무단 액세스 방지 및 위험을 최소화 하기 위해 격리를 강화하면 좋다.
    - 프로세스, 네트워킹, 파일 시스템을 격리한다.
    - 리소스를 보호하기 위해 CPU, Memory, I/O 리소스를 제한한다.
  - 컨테이너 간의 트래픽을 제한하기 위해 네트워크 세분화 및 방화벽 규칙을 도입하면 좋다.
    - 사용자 정의 브리지 네트워크를 생성하여, 컨테이너 통신을 격리한다.
      - 격리된 네트워크 생성
        - docker network create --driver bridge isolated_network
      - 격리된 네트워크에 컨테이너 연결
        - docker run --network=isolated_network [이미지명]
- Runtime Security
  - 실행 중인 컨테이너의 보안을 강화하고, 지속적인 모니터링 진행한다.
  - Security Prifiles를 적용한다.
    - AppArmor, SELinux, seccomp profiles 사용 등
  - 컨테이너를 최소 권한으로 실행한다.
    - root 사용자는 운영체제 전반적인 권한을 가지기 때문에 보안상 고려해야할 점이 많다.
    - Linux의 Capabilities를 제어하여, root 사용자의 권한을 세분화할 수 있다.
      - Ex) docker run --cap-drop=ALL --cap-add=SETGID --cap-add=SETUID --cap-add=CHOWN first-image:0.1 bash
        - --cap-drop=ALL : 모든 Capabilities을 제거한다. (Capabilities에 해당하는 권한은 레퍼런스 알아서 찾아보기)
        - --cap-add=SETGID : 모든 권한을 삭제했기 때문에 필요한 권한을 add 해준다.
  - Dockerfile에서의 권한 조정
    - Dockerfile로 이미지를 빌드할 때는 높은 권한으로 실행되기 때문에 제한이 필요없다.
    - 하지만 컨테이너 이미지를 이용하여 컨테이너를 실행할 때는 제한이 필요하다.
    - 위와 동일하게 'docker run --cap-drop=ALL --cap-add=SETGID ...' 명령어로 컨테이너 실행 시 권한 조정이 가능하다.
  - 일반 유저로 컨테이너 실행
    - 가능한 상황이라면 root 유저보다는 일반 유저로 컨테이너를 실행한다.
    - Dockerfile에서 USER 지시어를 사용하면, 일반 사용자로 실행하도록 지정할 수 있다.

<br>

### Secrets Management
- Secret
  - Secret은 보안이 필요한 민감한 데이터를 클러스터 단위에서 안전하게 관리할 수 기술이다.
  - Docker Swarm Mode에서 생성 된 Service에서 사용 가능하다.
  - Docker Swarm의 Secret에 있는 데이터는 항상 암호화 되어있다.
  - Secret은 파일 형태로 컨테이너에 마운트된다.
  - Secret의 데이터는 해당 Sercret이 삽입된 Service와 이에 속하여 구동 중인 컨테이너에서만 접근이 가능하다.
- 명령어
  - 목록 조회
    - docker secret ls
  - 상세 조회
    - docker secret inspect [secret]
- 실습
  - secret 생성
    - echo "qwer1234" | docker secret create my_db_password -
    - 암호화가 되어있다지만 실제로 암호를 secret으로 사용하는 것은 좋은 방법이 아니다.
  - secret을 사용한 DB 컨테이너 실행
    - docker service create --name my-db --replicas 1 --secret source=my_db_password, target=mariadb_root_password -e MARIADB_ROOT_PASSWORD_FILE="/run/secrets/mariadb_root_password" mariadb:latest
    - 생성한 secret을 사용하여 MariaDB의 패스워드를 설정한다.
  - MariaDB 접속
    - mariadb -h127.0.0.1 -uroot -p 명령어를 실행하면, 비밀번호를 입력하는 콘솔이 나타나며 이 때 qwer1234를 입력한다.
    - 패스워드를 통해 정상적으로 접속을 했다는 것은 qwer1234가 secret 기반으로 정상적으로 사용되었다는 것을 의미한다.

<br>

### Docker Container Logging
- Docker Container Logging 이란?
  - 도커 컨테이너 내부에서 발생되는 다양한 기록들을 의미한다.
  - 로그 메시지를 파악해줌으로써 장애 시, 어떠한 문제가 생겼는지 등에 대한 추적이 가능하다.
- 로그 확인 방법
  - docker logs 명령어 활용
    - docker logs [컨테이너ID 또는 컨테이너명]
  - 컨테이너 로그 파일 확인
    - 리눅스의 경우에만 사용 가능한 방법이다.
    - docker inspect 명령어를 통해 LogPath 확인
    - LogPath의 경로로 접근하여 파일을 확인한다.
      - LogPath의 경로는 보통 /var/lib/docker/containers/[컨테이너ID]/[컨테이너ID]-json.log 이다.
      - 윈도우와 Mac의 경우 해당 경로에 실제 파일이 없어 직접 접근하여 로그 파일을 볼 수 없다.
  - syslog 활용
    - syslog는 유닉스 계열의 운영체제에서 로그를 수집하는 도구이다. 이 때문에 리눅스에서만 사용 가능한 방법이다.
      - 도커 컨테이너 뿐만 아니라 커널 및 응용프로그램에 의해 발생하는 로그 모두가 생성된다.
    - docker run 명령어에 '--log-driver syslog'를 추가하여 사용할 수 있다.
      - 컨테이너에서 발생한 로그가 syslog에 모이게 된다.
      - 이렇게 syslog를 확인하는 방법은
        - journalctl -u docker.service | grep [컨테이너ID]
          - syslog에 출력된 모든 로그 중에 컨테이너의 로그만 필터링해서 볼 수 있다.

<br>

### Docker Container Monitoring
- Monitoring이란?
  - 일반적인 Monitoring
    - 서버의 CPU, 메모리 사용량, 디스크 공간 등의 기본 지표를 추적한다.
  - 컨테이너 Monitoring
    - 컨테이너의 생명 주기가 짧고, 여러 개의 컨테이너가 동시에 작동되고 있다 보니 다수의 컨테이너를 관리하기 위한 목적으로 모니터링을 하는 것이 일반적이다.
- Prometheus
  - 특징
    - 모니터링 기능을 제공해주는 서비스 중 하나이다.
    - 여러 개의 컨테이너의 상태를 추적할 수 있다.
    - 마이크로 서비스로 작성되어 있는 서비스 구조에서 여러개로 분산되어 있는 서비스들에 대한 모니터링을 가능하게 지원해준다.
  - 적용
    - 리눅스 환경이라면 /etc/docker/daemon.json 파일에 메트릭스 정보를 추가한다.
    - ```
      {
        "metrics-addr": "0.0.0.0:9323", # 0.0.0.0의 뜻은 Prometheus를 호출하는 모든 서비스에 대해 메트릭스를 수집하겠다는 설정.
        "experimental": true
      }
      ```
    - 도커를 재실행한다.
    - Prometheus를 도커 형태로 기동한다.
      - Ex) docker container run -e DOCKER_HOST=[HOST IP] -d -p 9090:9090 diamol/prometheus:2.13.1

<br>

### Docker Buildx
- Docker Buildx란?
  - 멀티 플랫폼에서 사용할 수 있는 이미지를 만들기 위한 기술이다.
  - 만약 macOS에서 이미지 빌드를 한 후, 리눅스에서 사용할 경우 OS가 달라 이미지를 사용할 수 없을 수도 있다.
  - 이 때 사용할 수 있는 기술이 Docker Buildx이다.
- 지원 가능한 플랫폼 확인
  - 'docker buildx ls' 명령어를 사용하여 지원가능한 플랫폼을 확인할 수 있다.
- Cross Platform Build 테스트
  - 이미지 생성 (macOS에서 실행)
    - Dockerfile 작성 및 실행
    - 빌드
      - docker build --tag 1992choi/my-node:m1 -f Dockerfile .
    - 업로드
      - docker push 1992choi/my-node:m1
  - 이미지 사용 (Linux 등 타 OS 환경)
    - 이미지 다운로드
      - docker pull 1992choi/my-node:m1
    - 컨테이너 실행
      - docker run -it 1992choi/my-node:m1 bash
      - 위의 명령어 실행 시, 오류가 발생한다.
        - 플랫폼이 다르기 때문
  - 해결방법
    - Buildx를 사용하여 멀티 플랫폼을 위한 이미지를 생성한다.
      - 지원하는 플랫폼 확인
        - docker buildx imagetools inspect node:alpine
      - 이미지 생성
        - docker buildx build --platform linux/amd64 --tag 1992choi/my-node:amd64 -f Dockerfile .
      - 결과
        - macOS에서 amd64로 이미지를 생성해서 실행하면,
          - macOS에서 오류가 발생한다.
          - 반대로 Linux에서는 사용할 수 있게 된다.

<br>

### Docker를 대신하는 기술
- Docker를 대체할 수 있는 기술에 대한 학습 내용
  - Docker Runtime을 대신하는 기술
    - Docker의 한계점
      - Docker 서버에 너무 많은 기능이 집중되어 있다.
      - Docker 명령어는 root 권한이 필요하다.
      - 대체재로 CRI-O와 Podman이라는 기술이 있다.
    - CRI-O
      - 컨테이너 간의 이식성에 대한 표준안을 가지고 있다.
      - Container Runtime 기능만 지원하기 때문에 이미지 빌드, cli, Registry 등의 기능은 사용이 불가능하다.
    - Podman
      - Docker cli와 유사한 툴이다.
      - 컨테이너 생성, 유지 및 관리를 위해 사용하는 툴이다.
      - daemon-less로 동작한다.
      - root 권한이 필요없다.
  - Docker Registry를 대신하는 기술
    - Harbor
      - 특징
        - 웹 대시보드를 지원한다.
        - Role 기반의 접근을 제어할 수 있다.
        - 스캐닝을 통한 취약점 검사 기능을 지원한다.
        - 인증서 설치가 필요하다.
          - CA Certificates 생성
          - Server Certificates 생성
          - SAN(Subject Alternative Name) 등록
          - Docker Engine Certificate 업데이트
      - 설치
        - Harbor 다운로드
        - harbor.yml 파일 생성 및 설정
          - cp harbor.yml.tmp harbor.yml
          - vi harvor.yml
            - hostname(=IP)과 만들었던 인증서 관련 설정을 추가한다.
        - Deploy
          - ./prepare
          - ./install.sh
            - 파일 내부에는 docker compose를 기동하는 스크립트가 작성되어 있다.
      - 실습
        - 컨테이너 실행 (Dind 형태)
          - docker run --privileged --name my-harbor -itd -p 10022:22 -p 8081:8080 -p 80:80 -p 443:443 -e container=docker -v /sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host edowon0623/docker-server:m1 /usr/sbin/init
        - OpenSSL 설치 (my-harbor 컨테이너에서 실행)
          - Key를 보관할 디렉토리 생성
            - mkdir ~/certs
          - CA Certificates 생성
            - openssl genrsa -out ca.key 4096
            - openssl req -x509 -new -nodes -sha512 -days 365 -key ca.key -out ca.crt
          - Server Certificates 생성
            - openssl genrsa -out server.key 4096
            - openssl req -new -sha512 -key server.key -out server.csr
          - SAN 등록
            - vi v3ext.cnf
              - Key와 동일한 위치에서 작업
              - subjectAltName = IP:192.168.0.33, IP:127.0.0.1
                - havor가 설치되고자하는 호스트 PC의 IP를 입력하면 된다.
          - Cert파일 생성
            - openssl x509 -req -sha512 -days 365 -extfile v3ext.cnf -CA ca.crt -CAkey ca.key -CAcreateserial -in server.csr -out server.crt
            - openssl x509 -inform PEM -in server.crt -out server.cert
          - Docker Engine에 인증서 관련 파일 옮기기
            - mkdir -p /etc/docker/certs.d/server
            - cp server.cert /etc/docker/certs.d/server/
            - cp server.key /etc/docker/certs.d/server/
            - cp ca.crt /etc/docker/certs.d/server/
        - Container에 docker-compose 설치 (my-harbor 컨테이너에서 실행)
          - curl -L "https://github.com/docker/compose/releases/download/v2.6.0/docker-compose-$(uname -s)-$(uname -m)" -o /usr/local/bin/docker-compose
          - chmod +x /usr/local/bin/docker-compose
        - Harbor 설치 (my-harbor 컨테이너에서 실행)
          - 다운로드
            - wget https://github.com/goharbor/harbor/releases/download/v2.2.2/harbor-offline-installer-v2.2.2.tgz
            - tar -xf harbor-offline-installer-v2.2.2.tgz
          - 설정
            - cp harbor.yml.tmpl harbor.yml
            - vi harbor.yml
              - hostname과 인증서 경로 재설정
          - 설치 및 실행
            - ./prepare
            - ./install.sh
        - Dind에서 registry 사용 설정 (my-harbor 컨테이너에서 실행)
          - /etc/docker/daemon.json 파일에 아래 내용 추가
          - ```
            {
                "insecure-registries": ["192.168.0.33", "127.0.0.1"]
            }
            ```
        - 도커 재실행 및 Harbor 재실행 (my-harbor 컨테이너에서 실행)
          - systemctl restart docker
          - ./install.sh
        - Harbor 접속 및 사용
          - 브라우저로 192.168.0.33 접속
          - 계정정보 : admin / Harbor12345
            - 계정정보는 harbor.yml 파일에 명시되어 있다.
          - Project 생성
          - docker와 Harbor 연결 (my-harbor 컨테이너에서 실행)
            - $ docker login 192.168.0.33
            - 위의 명령어 입력 후 나오는 로그인 ID와 PW는 위의 계정정보와 동일하게 입력하면 된다.
          - Harbor에 이미지 올리기 (my-harbor 컨테이너에서 실행)
            - 이미지 받기
              - 현재 작업하는 컨테이너에는 이미지가 없기 때문에 이미지 업로드를 위해 이미지를 다운로드 받는다.
              - docker pull edowon0623/catalog-service:1.0
            - 이미지 올리기
              - docker tag edowon0623/catalog-service:1.0 192.168.0.33/[Project명]/catalog-service:1.0
        - Harbor 사용하기 (myapp 컨테이너에서 실행)
          - 추가적으로 별도 컨테이너를 실행한다.
            - docker run --privileged --name myapp -itd -p 20022:22 -p 8082:8080 -e container=docker -v /sys/fs/cgroup:/sys/fs/cgroup:rw --cgroupns=host edowon0623/docker-server:m1 /usr/sbin/init
          - 로그인 계정 만들기 및 권한 추가
            - 추가적으로 기동한 컨테이너에서 Harbor를 사용하기 위해서는 로그인이 필요하다.
            - 로그인할 수 있도록 Harbor 홈페이지에서 사용자를 추가해준다.
              - 192.168.0.33 > Administration > Users 메뉴에서 사용자 생성
                - 신규 사용자 계정 : user1 / Harbor12345
            - 생성한 프로젝트의 권한에 해당 계정을 추가해준다.
          - 로그인
            - myapp 컨테이너로 돌아가서 로그인을 시도한다.
              - 'docker login -u user1 192.168.0.33' 입력 후 패스워드(=Harbor12345) 입력
          - registry 사용을 위한 설정
            - Harbor를 실행한 컨테이너와 동일하게 myapp 컨테이너에 아래 설정을 추가해준다.
              - /etc/docker/daemon.json
              - ```
                {
                    "insecure-registries": ["registry:5000"]
                }
                ```
          - 이미지 Pull
            - docker pull 192.168.0.33/[Project명]/catalog-service:1.0



<br><br>



## 최종 실습
### Docker Compose를 이용한 멀티컨테이너 환경 구축
- 네트워크 생성
  - docker network create --driver bridge my-network
- docker-compose
  - docker-compose 파일 생성
    - /section11/docker-compose/docker-compose.yml
  - DB
    - 실행
      - docker-compose up my-db -d
        - depends_on 설정이 있지만, 100% 보장되는 것이 아니기 때문에 DB부터 개별 실행
    - DB 확인
      - docker ps -a | grep my-db
    - DB 접속
      - docker exec -it docker-compose-my-db-1 bash
      - mariadb -h127.0.0.1 -uroot
    - DB 조회
      - show databases;
      - use mydb;
      - show tables;
  - Backend
    - 실행
      - docker-compose up my-backend -d
    - 확인
      - http://localhost:8088/catalogs
  - Frontend
    - 실행
      - docker-compose up my-frontend -d
    - 확인
      - http://localhost/
