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
- Sorted Sets
  - Set과 유사하지만 score라는 추가적인 기능이 존재하며, score를 통하여 정렬 기능을 지원한다.
  - 내부적으로 Skip List와 Hash Table의 조합으로 이루어져 있다.
  - 값이 저장될 때마다 정렬된다.
  - score가 동일하다면, 사전 편찬 순으로 정렬된다.
  - 순서를 가지기 때문에 리스트와 마찬가지로 인덱스를 통해 특정 범위를 조회할 수 있다.
  - ZSets이라고도 불린다.
- Stream
  - append-only log에 consumer groups과 같은 기능을 더한 자료 구조
  - Kafka와 유사한 기능을 가진다.
  - 엔트리마다 고유 ID를 가지고 있으며, 이러한 특성 때문에 O(1) 시간 복잡도를 갖는다.
  - Consumer Group을 통해 분산 시스템에서 다수의 consumer가 event 처리된다.
- Geospatials
  - 좌표를 저장하고, 검색하는 데이터 타입
  - 거리 계산, 범위 탐색 등을 지원한다.
- Bitmaps
  - 실제 데이터 타입은 아니고, String에 binary operation을 적용한 것.
  - 최대 42억개의 binary 데이터를 표현할 수 있다. (= 2^32)
- HyperLogLog
  - 집합의 cardinality를 추정할 수 있는 확률형 자료구조
  - 정확성을 일부 포기하는 대신 저장공간을 효율적으로 사용(평균 에러 0.81%)
  - 대략적인 근사치를 알아야 할 때 사용한다.
  - Set과 비교해봤을 때, 실제 값을 저장하지 않기 때문에 매우 적은 메모리를 사용한다.
  - 대신 실제 값을 저장하지 않기 때문에 저장한 값을 출력할 수는 없다.
- BloomFilter
  - element가 집합 안에 포함되었는지 확인할 수 있는 확률형 자료 구조
  - 정확성을 일부 포기하는 대신 저장공간을 효율적으로 사용
  - false positive를 반환한다.
    - false positive란 element가 집합에 실제로 포함되지 않은데 포함되었다고 잘못 예측하는 경우를 뜻한다. (포함되었는데 포함되지 않았다고 예측하지는 않는다.)
    - 이는 동작원리 때문에 그렇다.
    - BloomFilter는 값을 저장할 때 해시코드를 이용해서 저장한다.
    - 반대로 값을 찾을 때도 그 값에 해싱을 한 후 해시코드가 있는지 판단을 하게 되는데,
    - A와 B의 해시코드가 같다고 가정하고 A는 저장되어 있는 상태에서 B값을 찾으려 할 때 B의 해시코드로 탐색하면 B가 있는 것으로 조회된다. (실제로는 A가 저장되어 있음.)
  - Set과 비교해봤을 때, 실제 값을 저장하지 않기 때문에 매우 적은 메모리를 사용한다.

### 데이터 만료
- Redis에는 데이터를 특정시간 이후에 만료 시키는 기능이 있다.
- 데이터 조회 요청시에 만료된 데이터는 조회되지 않는다.
- 데이터가 만료되자마자 삭제하지 않고, 만료로 표시했다가 백그라운드에서 주기적으로 삭제한다.
- 데이터가 유효한 시간(초 단위)을 TTL 이라고 한다.

### SET NX/XX
- NX
  - 해당 Key가 존재하지 않는 경우에만 SET
- XX
  - 해당 Key가 이미 존재하는 경우에만 SET

### Pub/Sub
- Publisher와 Subscriber가 서로 알지 못해도 통신이 가능하도록 decoupling 된 패턴.
- Publisher는 Subscriber에게 직접 메시지를 보내지 않고, Channel에 Publish Subscriber는 관심이 있는 Channel을 필요에 따라 Subscribe하며 메시지 수신.
- Stream과의 차이는 메시지가 보관되는 Stream과 달리 Pub/Sub은 Subscribe 하지 않을 때 발행된 메시지 수신 불가.

### Pipeline
- 다수의 commands를 한 번에 요청하여 네트워크 성능을 향상 시키는 기술
- Round-Trip Times를 최소화 시킨다.
  - Round-Trip Times란 Request / Response 모델에서 발생하는 네트워크 지연 시간을 의미한다.

### Transaction
- 다수의 명령을 하나의 트랜잭션으로 처리하여 원자성을 보장할 수 있다.
- 중간에 에러가 발생하면 모든 작업을 Rollback 시킨다.
- 하나의 트랜잭션이 처리되는 동안 다른 클라이언트의 요청이 중간에 끼어들 수 없다.
- 명령어
  - MULTI
    - 트랜잭션을 시작한다.
  - DISCARD
    - Rollback 시킨다.
  - EXEC
    - 변경사항을 적용시킨다.

### 데이터 타입 활용
- One Time Password
  - 인증을 위해 사용되는 임시 비밀번호
  - 'SET USER식별자 OTP번호 EX 180'과 같이 데이터에 만료시간을 주어 OTP를 구현할 수 있다.
- Distributed Lock
  - 분산 환경의 다수의 프로세스에서 동일한 자원에 접근할 때, 동시성 문제를 해결할 수 있다.
  - 'SET lock 1 NX'와 같은 명령어로 구현할 수 있다.
    - NX 옵션의 특징(Key가 존재하지 않는 경우에만 SET)을 사용하여 정상적으로 SET이 되면, 권한을 얻는 것으로 간주하고 이미 SET이 되어있다면 누군가 lock을 건 것으로 간주하여 lock을 획득하지 못하는 프로세스이다.
- Rate Limiter
  - 시스템 안정성/보안을 위해 요청의 수를 제한하는 기술을 뜻한다.
  - Rate Limiter의 구현방식 중 Fixed-window Rate Limiting 방식은 고정된 시간(Ex. 1분) 안에 요청 수를 제한하는 방법이다.
  - 아래의 명령어 조합으로 구현할 수 있다.
    - MULTI (트랜잭션 시작)
    - INCR (요청 수 증가) : INCR 1.1.1.1:10 (포맷예시 - 아이피:요청시간의 분. 1분후 초기화되므로 분으로만 판단해도 충분하다.)
    - EXPIRE 1.1.1.1:10 60 (1.1.1.1 아이피가 10분에 접근했다는 키를 60초 후에 만료시킴)
    - EXEC (트랜잭션 커밋)





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
  - key가 'lecture'인 Hash에서 field가 name인 항목을 조회한다. (= inflearn-redis가 조회된다.)
- HMGET lecture name price
  - 한 번에 여러개의 field를 조회할 수 있다.
  - 만약 존재하지 않은 field가 포함되어 있을 경우, (nil)이 반환된다.
- HINCRBY lecture price 10
  - 숫자형 field에는 연산을 할 수 있다.

### Sorted Set
- ZADD points 10 TeamA 10 TeamB 50 TeamC
  - score, member 순서로 명령어를 입력한다.
  - 10점의 TeamA와 TeamB, 그리고 50점의 TeamC를 저장한다.
- ZRANGE points 0 -1
  - 오름차순 정렬로 조회한다. (TeamA -> TeamB -> TeamC) 
- ZRANGE points 0 -1 REV WITHSCORES
  - REV 옵션에 의해서 역정렬인 내림차순으로 조회된다.
  - WITHSCORES 옵션에 의해서 Score까지 조회된다.
- ZRANK points TeamB
  - 랭킹을 조회한다.
  - 0번부터 채번된다. (TeamB의 경우는 1이 반환된다.)
  - 인덱스 번호와 동일하다고 볼 수 있다.

### Stream
- XADD events * action like user_id 1 product_id 1
  - events라는 Stream에 user_id는 1, product_id는 1이라는 값을 저장한다.
  - action like user_id 1 product_id 1 : 1번 유저가 1번 상품을 좋아요를 눌렀다라고 해석할 수 있다.
    - action like는 옵션은 아니고 문자열 데이터이다. (아래 스크린샷에서 생성된 Stream 데이터 확인 가능)
  - \* 옵션을 통해 유니크ID를 자동 할당한다.
  - 명령어가 실행되면 고유 ID가 반환된다.
- XRANGE events - +
  - 처음 들어간 데이터부터 마지막 들어간 데이터까지 확인 가능하다.
  - <img width="930" alt="image" src="https://github.com/user-attachments/assets/f8eaf2f9-a1ae-4bd0-b4ae-346916208f96">
- XDEL events 1723849452521-0
  - evenets라는 이름의 Stream의 고유 ID에 해당하는 데이터를 삭제한다.

### Geospatial
- GEOADD seoul:station 126.923917 37.556944 hong-dae 127.027583 37.497928 gang-nam
  - 홍대역과 강남역의 좌표 추가
  - 위도 다음에 경도 순서이다.
- GEODIST seoul:station hong-dae gang-nam KM
  - 홍대와 강남역의 거리를 출력하되, KM 단위로 출력한다.

### Bitmaps
- 유저별로 날짜별 로그인 데이터 생성
  - SETBIT user:log-in:23-01-01 123 1
    - 123번 유저가 '23-01-01'에 로그인 시도
    - 마지막 1은 비트 수를 의미한다. (0 또는 1로 표기.)
  - SETBIT user:log-in:23-01-01 456 1
    - 456번 유저가 '23-01-01'에 로그인 시도
  - SETBIT user:log-in:23-01-02 123 1
    - 123번 유저가 '23-01-02'에 로그인 시도
- BITCOUNT user:log-in:23-01-01
  - 23-01-01에 로그인한 유저 숫자를 조회할 수 있다.
- BITOP AND result user:log-in:23-01-01 user:log-in:23-01-02
  - 23-01-01과 23-01-02일에 모두 로그인 한 유저를 반환한다. (=123 유저 반환)
  - AND 옵션을 통해 AND 연산을 수행한다.
  - result 변수에 반환 결과를 받는다.
- BITCOUNT result
  - 위에서 저장한 result 값을 조회한다.
  - 123 유저의 수인 1을 반환한다.
- GETBIT result 123
  - result의 값이 123 유저가 맞는지 확인한다.
  - 맞으므로 1을 반환한다. (GETBIT result 456 명령어를 입력하면 0을 반환. 모두 로그인하지 않았으므로)

### HyperLogLog
- PFADD fruits apple orange grape kiwi
  - 'fruits'라는 키에 apple, orange, grape, kiwi 데이터를 저장한다.
- PFCOUNT fruits
  - fruits에 저장되어 있는 데이터의 갯수를 조회한다. (4를 반환)
  - 만약 PFADD fruits appl 후 PFCOUNT fruits 명령어를 입력해도 4를 반환한다. (= apple의 해시값이 같아 1개로 판단하기 때문)
  - 위와 같은 특성 때문에 SET이랑 비슷할 수도 있지만, 값을 직접 저장하는 것이 아니기 때문에 해시 충돌이 일어날 경우도 동일 카운트로 되어 정확하지 않은 값이 나올 수 있다.
    - 실제로 1만개를 저장하였을 때, 해시충돌이 일어나는 경우가 있다면 1만 보다 적은 값이 저장된 것으로 나올 수도 있다.
    - 반대로 크게 나오는 경우도 존재한다.

### BloomFilter
- BF.MADD fruits apple orange
  - fruits에 apple과 orange를 저장한다.
- BF.EXISTS fruits apple
  - fruits에 apple이 있는지 조회한다.
  - 있다면 1, 없다면 0을 반환한다.

### 데이터 만료
- greeting을 저장 후 10초 후 만료시킨다.
  - SET greeting hello
  - EXPIRE greeting 10
- TTL greeting
  - 남은 만료시간을 확인한다.
  - 남은 만료시간이 반환되며, -1은 만료기한이 없음을, -2는 만료되었음을 뜻한다.
- SETEX greeting 10 hello
  - 저장과 동시에 만료시간을 지정한다.

### SET NX/XX
- SET greeting hello NX
  - 해당 Key가 존재하지 않는 경우에만 SET
  - 이후 SET greeting hi NX 명령어를 입력하더라도 이미 Key가 존재하므로 덮어쓰여지지 않게되어 GET greeting을 입력하면 hello를 반환한다.
- SET a hello XX
  - 해당 Key가 이미 존재하는 경우에만 SET
  - a의 값이 없는 상태에서 SET a hello XX를 입력 후 GET a를 입력하면 (nil)을 반환한다.
 
### Pub/Sub
- SUBSCRIBE order payment
  - order 채널과 payment 채널을 구독한다.
- PUBLISH order msg1
  - order 채널로 msg1을 전송한다.
- PUBLISH payment pay1
  - payment 채널로 pay1을 전송한다.

### Transaction
- MULTI
  - 트랜잭션을 시작한다.
- DISCARD
  - Rollback 시킨다.
- EXEC
  - 변경사항을 적용시킨다.
- 예제
  - MULTI > SET text a > DISCARD > GET text : 롤백되어 값을 조회할 수 없다.
  - MULTI > SET text a > EXEC > GET text : a가 조회된다.
