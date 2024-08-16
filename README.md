# Redis
- Inflearn > 실전! Redis 활용



<br><br>



## 개념 정리
### Redis란?
- Redis란 Remote Dictionary Server의 약자로서, "키-값" 구조의 비정형 데이터를 저장하고 관리하기 위한 오픈 소스 기반의 비관계형 데이터베이스 관리 시스템이다.

### Redis 특징
- In-Memory
  - 모든 데이터를 RAM에 저장 (백업 / 스냅샷 제외)
- Single Threaded
  - 단일 thread에서 모든 task 처리
- Cluster Mode
  - 다중 노드에 데이터를 분산 저장하여 안정성 & 고가용성 제공
- Persistence
  - RDB(Redis Database) + AOF(Append only file) 통해 영속성 옵션 제공
- Pub/Sub
  - Pub/Sub 패턴을 지원하여 손쉬운 어플리케이션 개발(e.g 채팅, 알림 등)

### Redis 장점
- 높은 성능
  - 모든 데이터를 메모리에 저장하기 때문에 매우 빠른 읽기/쓰기 속도 보장
- Data Type 지원
  - Redis에서 지원하는 Data type을 잘 활용하여 다양한 기능 구현
- 클라이언트 라이브러리
  - Python, Java, JavaScript 등 다양한 언어로 작성된 클라이언트 라이브러리 지원
- 다양한 사례 / 강한 커뮤니티
  - Redis를 활용하여 비슷한 문제를 해결한 사례가 많고, 커뮤니티 도움 받기 쉬움

### Redis 사용 사례
- Caching
  - 임시 비밀번호(One-Time Password)
  - 로그인 세션(Session)
- Rate Limiter
  - Fixed-Window / Sliding-Window Rate Limiter(비율 계산기)
- Message Broker
  - 메시지 큐(Message Queue)
- 실시간 분석 / 계산
  - 순위표(Rank / Leaderboard)
  - 반경 탐색(Geofencing)
  - 방문자 수 계산(Visitors Count)
- 실시간 채팅
  - Pub/Sub 패턴을 사용한 채팅 프로그램

### Redis의 영속성 옵션
- Persistence(영속성)
  - Redis는 주로 캐시로 사용되지만 데이터 영속성을 위한 옵션 제공
  - SSD와 같은 영구적인 저장 장치에 데이터 저장
- RDB(Redis Database)
  - Point-in-time Snapshot -> 재난 복구(Disaster Recovery) 또는 복제에 주로 사용
  - 일부 데이터 유실의 위험이 있고, 스냅샷 생성 중 클라이언트 요청 지연 발생
- AOF(Append Only File)
  - Redis에 적용되는 Write 작업을 모두 log로 저장
  - 데이터 유실의 위험이 적지만, 재난 복구시 Write 작업을 다시 적용하기 때문에 RDB 보다 느림
- RDB + AOF
  - 함께 사용하는 옵션 제공

### Caching
- 캐싱(Caching)이란?
  - 데이터를 빠르게 읽고 처리하기 위해 임시로 저장하는 기술
  - 계산된 값을 임시로 저장해두고, 동일한 계산 / 요청 발생시 다시 계산하지 않고 저장된 값을 바로 사용
  - 캐시(Cache) = 임시 저장소
- 사용 사례
  - CPU 캐시
    - CPU와 RAM의 속도 차이로 발생하는 지연을 줄이기 위해 L1, L2, L3 캐시 사용
  - 웹 브라우저
    - 캐싱웹 브라우저가 웹 페이지 데이터를 로컬 저장소에 저장하여 해당 페이지 재방문시 사용
  - DNS 캐싱
    - 이전에 조회한 도메인 이름과 해당하는 IP 주소를 저장하여 재요청시 사용
  - 데이터베이스 캐싱
    - 데이터베이스 조회나 계산 결과를 저장하여 재요청시 사용
  - CDN
    - 원본 서버의 컨텐츠를 PoP 서버에 저장하여 사용자와 가까운 서버에서 요청 처리
  - 어플리케이션 캐싱
    - 어플리케이션에서 데이터나 계산결과를 캐싱하여 반복적 작업
    - Redis는 어플리케이션 캐싱에 속한다고 볼 수 있다.
- Cache Hit / Miss
  - Hit
    - 캐시에 데이터가 적재되어 있는 상태
  - Miss
    - 캐시에 데이터가 적재되어 있지 않은 상태
- Cache-Aside pattern
  - 다양한 캐싱 전략 중 널리 사용되고 있는 패턴 중 하나이다.
  - ![image](https://github.com/user-attachments/assets/f48c87b6-68d4-462a-ad27-ce3d62fd64af)
    - 1\. 애플리케이션에서 데이터의 수요가 발생하면 캐시에 먼저 데이터를 찾아 제공한다.
    - 2\. 캐시에 해당 데이터가 존재하지 않으면 DB에서 찾아 제공한다.
    - 3\. DB에서 찾은 데이터를 캐시에 적재한다. 

### 데이터 타입
- Strings
  - 가장 기본적인 데이터 타입.
  - 문자열, 숫자, Serialized Object 등 저장 가능
  - SET : 하나의 문자열을 저장
  - MSET : 다수의 문자열을 저장
  - MGET : 다수의 문자열을 반환
  - INCR : 특정 숫자의 값을 1 올림
  - INCRBY : 특정 숫자의 값에 할당한 값만큼 더함
- Lists
  - String을 Linked List로 저장하는 데이터 타입
  - 레디스의 리스트는 Doubly Linked List이기 때문에 큐나 스택을 쉽게 구현할 수 있다.
  - 간단한 메시지 브로커를 구현할 수도 있다.
- Sets
  - 중복되지 않는 유니크한 String을 저장하는 정렬되지 않은 집합.
  - 집합에 대한 연산 기능을 제공한다.
    - Intersection : 교집합
    - Union : 합집합
    - Difference : 차집합
- Hashes
  - field-value 구조를 갖는 데이터 타입.
  - 다양한 속성을 갖는 객체의 데이터를 저장할 때 유용



<br><hr><br>



## 실습
### Redis 셋팅
- 설치
  - brew install redis
- 실행
  - brew services start redis
- 종료
  - brew services stop redis
- 접속
  - redis-cli

### 기본 실습
- 데이터 저장
  - SET lecture inflearn-redis
- 데이터 조회
  - GET lecture
- 데이터 삭제
  - DEL lecture
 
### Strings
- SET lecture inflearn-redis
  - key가 'lecture'이고 value가 'inflearn-redis'인 문자열을 저장한다.
- MSET price 100 language ko
  - key가 'price'이고 value가 '100'인 문자열과  key가 'language'이고 value가 'ko'인 문자열을 한 번에 저장한다.
- MGET lecture price language
  - key가 'lecture', 'price', 'language'인 값들을 한 번에 가져온다.
- INCR price
  - price 값을 1 증가시킨다.
- INCRBY price 9
  - price 값을 9만큼 증가시킨다.
- SET inflearn-redis '{"price": 100, "language": "ko"}'
  - json 타입으로 문자열을 저장시킨다.
- SET inflearn-redis:ko:price 200
  - key의 구성을 콜론(:)으로 구분하여 사용하기도 한다.
  - Ex) 키의 의미 : inflearn-redis강좌는 한국어로 되어있으며 200원이다.

### List
- LPUSH queue job1 job2 job3
  - key가 'queue'인 항목에 job1, job2, job3을 추가한다.
- RPOP queue
  - 가장 먼저 들어갔던 값을 빼낸다.
  - 위에서 job1, job2, job3 순서로 들어가있으므로 job1이 출력된다.
- LPUSH stack job1 job2 job3
  - key가 'stack'인 항목에 job1, job2, job3을 추가한다.
- LPOP stack
  - 가장 나중에 들어갔던 값을 빼낸다.
  - 위에서 job1, job2, job3 순서로 들어가있으므로 job3이 출력된다.
- LRANGE queue 0 -1
  - LRANGE 전에 데이터 추가를 위해 'LPUSH queue job4 job5' 먼저 수행 (=job2~5까지 들어있는 상태)
  - 첫번째 요소부터 마지막 요소까지 모두 출력한다. (실제 값을 빼내는 것은 아니다. 단순 출력.)
  - job5, job4, job3, job2 순으로 출력된다.
- LRANGE queue -2 -1
  - job3, job2 순으로 출력된다. (=job2~5까지 들어있는 상태)
- LRANGE queue 2 3
  - job3, job2 순으로 출력된다. (=job2~5까지 들어있는 상태)
- LTRIM queue 0 1
  - 0번째 1번째만 남기고 빼낸다. (=job2~5까지 들어있는 상태)
  - job5와 job4만 남기고 job3, job2는 제거된다. (=job4, 5만 들어있는 상태)

### Set
- SADD user:1:fruits apple banana orange orange
  - key가 'user:1:fruits'인 항목에 apple banana orange orange을 저장한다.
  - Set에 특성상 중복되는 orange는 1개만 저장되어, 값을 조회해보면 apple, banana, orange 총 3개가 들어있다.
- SMEMBERS user:1:fruits
  - key가 'user:1:fruits'인 항목의 데이터를 조회한다.
  - orange, apple, banana가 조회된다. (순서가 보장되지 않는다.)
- SCARD user:1:fruits
  - key가 'user:1:fruits'인 항목에 들어있는 데이터의 총 갯수를 조회한다.
- SISMEMBER user:1:fruits banana
  - banana가 들어있는지 조회한다.
  - 1이면 TRUE, 0이면 FALSE를 의미한다.
- SINTER user:1:fruits user:2:fruits
  - user:1:fruits와 user:2:fruits의 공통 원소를 조회한다.
- SDIFF user:1:fruits user:2:fruits
  - user:1:fruits와 user:2:fruits의 차집합을 조회한다. (좌측이 기준)
- SUNION user:1:fruits user:2:fruits
  - user:1:fruits와 user:2:fruits의 합집합을 조회한다.

### Hash
- HSET lecture name inflearn-redis price 100 language ko
  - key가 'lecture'인 Hash에 아래와 같은 field:value 값을 저장한다.
    - name:inflearn-redis
    - price:100
    - language:ko
- HGET lecture name
  - key가 'lecture'인 Hash에서 field가 name인 항목을 조회한다. (= inflearn-redis이 조회된다.)
- HMGET lecture name price
  - 한 번에 여러개의 field를 조회할 수 있다.
  - 만약 존재하지 않은 field가 포함되어 있을 경우, (nil)이 반환된다.
- HINCRBY lecture price 10
  - 숫자형 field에는 연산을 할 수 있다.



