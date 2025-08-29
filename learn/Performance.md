# Performance
- Fast Campus > 궁극의 성능 튜닝과 트러블슈팅

<br><br><br>

# 정리
### 성능
- 성능이 중요한 이유
  - 사용자 유지를 좌우한다.
  - 느린 사이트는 수익에 부정적인 영향을 미치고 빠른 사이트는 전환율을 높인다.
- 성능 측정 지표
  - LCP (Largest Contentful Paint)
    - 로딩 성능을 측정한다.
    - 우수한 사용자 경험을 제공하려면 페이지가 처음으로 로딩된 후 2.5초 이내에 LCP가 발생해야 한다.
  - FID (First Input Delay)
    - 최초 입력 지연
    - 우수한 사용자 경험을 제공하려면 페이지의 FID가 100밀리초 이하여야 한다.
  - CLS (Cumulative Layout Shift)
    - 시각적 안정성을 측정한다.
    - 우수한 사용자 경험을 제공하려면 페이지에서 0.1 이하의 CLS를 유지해야 한다.
- 성능의 주요 지표
  - 사용자 (Users)
    - 서비스를 사용하는 사용자의 수
    - 성능 테스트 관점에서 사용자는 Active User 와 Concurrent User 로 나눌 수 있다.
      - Active User
        - 서비스에 요청을 하고 기다리는 사용자다.
        - 메뉴나 링크를 누르고 결과가 나오기를 기다리는 사용자다.
      - Concurrent User
        - Active User 를 포함한다.
        - 웹 페이지를 띄워 놓은 사용자나 앱을 실행하고 있는 사용자 (아직 직접적인 요청은 없지만 요청을 행할 수 있는 존재)다.
  - 응답시간 (Response Time)
    - 각 요청에 대한 응답시간
    - Application server 에서 소요되는 시간은 CPU time과 Wait time으로 나눌 수 있다.
      - CPU time
        - CPU 연산을 하면서 소요되는 시간이다.
      - Wait time
        - DB의 결과를 기다리거나, API 호출한 후 대기하는 등 기다리는 시간을 의미한다.
  - 초당 처리량 (Transactions Per Seconds,TPS)
    - 1초에 처리 가능한 트랜젝션의 수다.
  - 리소스 사용량 (Resource Usage)
    - CPU, 메모리, 네트워크 등 부하 발생시 리소스 사용량이다.

### 병목
- 병목이 발생할 수 있는 지점
  - Database
    - Full scan 문제
      - 가장 흔히 발생하는 유형으로 index가 잡혀 있지 않으면, 테이블 full scan이 일어날 수 있다.
    - N+1 문제
      - JPA를 사용할 경우 N+1 문제가 발생하여, 병목현상이 발생하는 케이스다.
  - Server
    - OS 버전이 낮아 각종 버그를 포함한 상태에서 서비스를 지속할 경우다.
    - OS 내의 각종 설정값들이 기본으로 되어 있어서 서비스의 특성에 맞는 튜닝이 되어 있지 않은 경우다.
    - 리소스가 부족한 경우
      - 먼저 튜닝을 해야하고, 튜닝이 완료 되었는데도 해결이 안되면 서버를 증설 고려한다.
        - 수직(Vertical) 확장
          - CPU clock 이 더 좋은 장비로 변경, 메모리 증설 등 서버 스펙을 올리는 확장이다.
        - 수평(Horizontal) 확장
          - 서버 대수를 증가 시키는 방식의 스펙 확장이다.
  - Network
    - 네트워크 작업이 주가 되는 서비스에서는 네트워크 설정과 장비 구성이 중요한 역할을 하기 때문에, 자바 기반의 네트워크 구성을 관리하는 네트워크 토폴로지(Network Topology)는 항상 확인 가능해야 한다.
  - 연계서버
    - 연계되는 내 외부 서비스에서 성능이 나오지 않으면 우리 서비스의 장애로 이어질 수밖에 없다.
    - 연계서버의 성능 이슈나 장애 발생 시, 전파되지 않도록 연결관련 설정은 필수적으로 하는 것이 좋다.
      - Ex. Timeout 설정

### 성능 측정 도구
- 성능 측정 도구는 아래와 같이 분류할 수 있다.
  - 모니터링 도구
    - 서버 리소스 모니터링 툴
    - 서비스 모니터링 툴
    - 종류
      - Grafana
      - Prometheus
      - Zabbix
      - Observium
      - Cacti
      - Nagios
      - Icinga
  - 성능 분석 도구
    - Profiler
      - CPU, Memory, Thread 등을 분석할 때 유용하게 사용 가능
      - 종류
        - jProfiler
        - YourKit
        - java flight recorder
        - visual vm
    - APM
      - 종류
        - PinPoint
        - scouter
        - Whatap
        - DataDog
        - Dynatrace
        - AppDynamics
        - New Relic
  - 성능 테스트 도구
    - Benchmark 테스트 툴
      - 두개 이상의 대상에 대한 성능을 비교하기 위한 도구
      - 종류
        - SPEC
        - JMH
    - Performance 테스트 툴
      - 성능 위주의 측정 도구
      - 종류
        - WebLoad
        - LoadRunner
        - Rational Performance Tester
        - Gatling
        - Apache
        - Jmeter
        - nGrinder
        - Locust
        - K6

### 서버 성능에 영향을 주는 요소와 명령어
- CPU
  - uptime
    - 서버의 현재 시간, 시스템 가동 시간, 로그인 사용자 수, 평균 부하(load average)를 확인한다.
  - mpstat
    - CPU 사용률을 모니터링하고, CPU별 사용 현황을 확인한다.
- Memory
  - netstat
    - 네트워크 연결 상태, 라우팅 테이블, 인터페이스 상태 등을 확인한다.
  - ss
    - 소켓 통계 정보를 확인하며, netstat보다 더 빠르고 다양한 네트워크 상태를 볼 수 있다.
- Network
- Disk
  - iostat
    - CPU 사용량과 디스크 I/O 통계를 확인한다.
  - du
    - 디렉터리와 파일의 디스크 사용량을 확인한다.
  - df
    - 파일 시스템의 전체 및 남은 디스크 용량을 확인한다.
- OS
  - sysctl
    - 커널 파라미터를 조회하거나 수정한다.
- 정리
  - 모든 서버는 최적화된 상태로 제공되지 않는다.
  - 그렇기 때문에 성능 테스트를 하여 모든 서버의 리소스를 최대한 끌어올려 최적화된 상태로 운영하는 것이 중요하다.

### 성능 테스트
- 성능 테스트의 필요성
  - 서비스 오픈 전 성능 확인
    - 서비스에서 몇 명의 사용자를 처리할 수 있는지 확인
    - 서버의 최대 처리량 확인
  - 인프라 용량 산정
    - 결과를 바탕으로 적정한 인프라 용량(서버 스펙, 대수)을 확인
  - 튜닝 전 후 성능 비교
  - 부하 상황에서의 결함 도출
- 성능 테스트의 대상
  - 성능이 중요한 서비스
    - 사내 서비스의 경우에는 사용자가 거의 정해져있기 때문에 투자한 시간대비 효율이 좋지 않음
    - B2C 서비스, 즉, 불특정 다수를 대상으로 하는 서비스
  - 순간적으로 사용자의 요청이 집중되는 서비스
    - 선착순 서비스
      - 수강 신청, 티켓 신청,상품 구매 등
    - 결과 확인 서비스
      - 입찰 결과 확인, 대회 결과 확인, 면접 결과 확인, 인센티브 확인 등
- 목표 산정시 고려사항
  - 전체 용량
    - 현재 또는 예측되는 업무량은 어느 정도인가?
  - 용량 증가
    - 시간이 지남에 따라 업무량이 어떻게 증가할 것으로 예상되는가?
  - 현재 부하량과 예상되는 최대 부하
    - 현재 또는 예측되는 최대 부하 수준은 어느 정도인가?
  - 최대 부하에 도달하는 시간
    - 최대 부하에 도달하기까지 걸리는 시간은 어느 정도인가?
  - 최대 부하가 지속되는 시간
    - 최대 부하 상태가 얼마나 지속되는가?
- 부하 모델의 종류
  - Ramp-up Load
    - 점진적으로 부하를 증가 시키는 모델
    - 적용 시기
      - 적정 부하량 확인
      - 과부하 시 시스템 오류 발생 지점 식별
      - 병목 구간 식별
  - Cruising Load
    - 지속적으로 부하를 가하는 모델
    - 최소 한시간에서 1주일 이상까지 테스트 수행
    - 적용 시기
      - 메모리나 디스크 등 리소스 부족현상 확인
      - 운영시 발생 가능한 특이사항 식별
  - Spike Load
    - 순간적으로 높은 부하를 가하는 모델
    - 적용 시기
      - 이벤트성 업무
      - 신규 서비스
      - 입찰, 경매, 쿠폰 신청 등 선착순 업무

### 서비스별 특성 분석
- 서비스별 특성을 분석해야하는 이유
  - 서비스의 특성마다 주로 사용하는 리소스들이 달라진다.
  - 그렇기 때문에 주로 사용하는 리소스에 대한 분석과 튜닝을 고려해야한다.
- 서비스별 특성
  - CPU나 GPU를 많이 사용하는 서비스
    - 일반적인 웹 애플리케이션의 경우 CPU 기반의 작업들이 대부분
    - AI 기반의 서비시들은 GPU를 많이 사용
  - Memory를 많이 사용하는 서비스
    - 빠른 응답 또는 대용량 데이터를 한 번에 처리하는 서비스
      - 실시간 정보를 활용하는 내비게이션
  - Disk를 많이 사용하는 서비스
    - 파일을 주로 저장하는 서비스
  - Network를 많이 사용하는 서비스
    - 음악이나 영상을 제공하는 서비스
    - 파일을 제공하는 서비스
    - 여기서 Disk를 많이 사용하는 서비스와 구분되는 점은 이미 서버에 저장되어있는 데이터를 단순 제공

### GC
- GC(Garbage Collection)란?
  - JVM 에서 메모리를 관리해 주기 때문에 더 이상 사용하지 않는 객체를 청소해 주는 작업
- GC
  - GC는 크게 아래와 같이 구분할 수 있다.
    - Minor GC
      - = Young GC
    - Major GC
      - = Full GC
  - 영역
    - GC에는 Young 영역과 Old 영역이 존재한다.
      - Young 영역
        - Eden
        - Survivor
      - Old 영역
        - Old
- GC의 종류
  - Serial Collector
    - GC를 단일 스레드로 실행
      - GC를 단일 스레드로 동작시키기 때문에, GC가 실행되는 동안 애플리케이션의 모든 사용자 스레드가 정지(Stop-The-World, STW) 상태에 들어간다.
      - 즉, GC 이벤트가 발생하면 애플리케이션 로직은 잠시 멈추고, GC가 완료된 후 다시 실행된다는 단점이 있다.
    - 스레드간 GC 오버헤드가 발생하지 않음
    - 단일 프로세서 장비에 적합
  - Parallel Collector
    - GC를 여러 스레드로 실행
    - Compaction 작업을 기본적으로 수행한다.
      - Compaction 작업이란?
        - 메모리가 조각나 있는 것들을 한 곳으로 모으는 작업
        - 시간과 CPU 를 많이 사용한다.
  - G1 GC
    - 대용량 힙에서도 예측 가능한 짧은 GC 지연 시간을 제공
    - 기존의 GC는 Eden, Survivor, Old 영역이 고정된 공간으로 나뉘었지만, G1 GC에서는 힙을 같은 크기의 Region 단위로 나누고, Young/Old 역할을 동적으로 할당하도록 변경되었다.
    - 기존 Young GC 관련 동작과의 차이점
      - Young GC
        - Eden과 Survivor 영역이 고정된 공간으로 나뉘어 있음
        - Minor GC 발생 시
          - Eden 영역의 살아있는 객체를 Survivor로 카피(copy)
          - Survivor가 가득 차면 Old 영역으로 승격(promote)
        - 즉, 객체 이동이 필수적이었음 → 카피 비용 발생
      - G1 GC
        - 힙을 동일한 크기의 Region 단위로 나눔
        - Young 영역 역할을 하는 Region만 Minor GC 대상으로 수집
        - 살아있는 객체를 다른 Region으로 옮기지만, 기존처럼 Eden → Survivor → Old로 고정된 경로를 따르지 않음
        - Region 단위로 필요한 곳에만 객체를 옮김 → 고정된 Young/Old 영역 전체를 복사하지 않는다
          - 기존처럼 Eden과 Survivor가 고정된 공간이어서 항상 복사해야 했던 구조가 사라짐.
  - ZGC
    - 대규모 힙에서도 거의 멈춤 없는 GC를 목표로 설계된 Low-latency GC
    - CPU와 메모리 오버헤드 존재
      - 객체를 계속 추적(확인)하고 참조를 관리하기 때문

### Java 개발 시 유의사항
- String
  - String은 불변(immutable) 객체이기 때문에 새로운 값을 할당할 때마다 새로운 객체가 생성되고, 기존 객체는 메모리에 남아 있게된다.
  - 따라서 문자열 결합 시에 StringBuilder, StringBuffer, StringJoiner를 사용하는게 좋다.
- 반복문
  - for 를 사용할 때에는 메소드 호출은 최대한 자제한다.
    - AS IS
      - ```
        int array[] = new int[10];
        for (int loop = 0; loop < array.length; loop++) {
          ...
        }
        ```
    - AS IS
      - ```
        int array[] = new int[10];
        int arrayLength = array.length;
        for (int loop = 0; loop < arrayLength; loop++) {
          ...
        }
        ```
- JSON
  - 서버간 데이터를 주고 받을 때 JSON을 사용할 경우, 데이터를 받아 분석하는데 CPU만을 사용하며 데이터가 크면 클수록 그 시간은 비례하여 증가한다.
  - JSON 대안으로 Protocol buffers(protobuf, gRPC), Thrift, Finalge, Avro 등을 고려하는 것도 좋은 방법이다.
- Log
  - System.out.println()을 이용한 방식은 지양
  - Logger를 사용은 필수. 불필요한 것은 로그로 남길 필요 없음.

### Troubleshooting
- Troubleshooting이란?
  - 문제의 원인을 파악하여 해결해 나아가는 것
- 문제의 원인을 파악하는 방법
  - 병목으로 인하여 이슈가 발생한 경우
    - APM으로 병목 지점 파악
      - 서버가 문제일 경우 서버 콘솔에 들어가서 파악
      - 애플리케이션이 문제일 경우에는 쓰레드 문제, 메모리 문제, 기능상의 문제인지를 확인
  - 사용자 증가로 이슈가 발생한 경우
    - 근본적인 원인 파악이 필요함
      - 일시적인 증가(=마케팅 혹은 이벤트로 인하여 일시적인 증가)라면,
        - 웨이팅 룸 같은 기능 추가
        - 서버 스펙 확장
      - 절대적인 사용자 수의 증가라면,
        - 튜닝 포인트가 있는지 확인
        - 서버 스펙 확장
  - Thread로 이슈가 발생한 경우
    - Thread dump를 확인할 수 있는 다양한 방법
      - jstack [pid] 명령어를 통해 확인
      - kill -3 [pid]
    - 덤프가 생성되었다면, TDA(Thread Dump Analyzer Tool)로 확인할 수 있다.
  - Memory로 인한 이슈가 발생한 경우
    - 명령어 혹은 jvm 옵션을 통해 다양한 방법으로 확인할 수 있다.
      - jstat -gcutil [pid]
      - -XX:+HeapDumpOnOutOfMemoryError (자동 Heap dump 옵션)
      - jmap -histo [pid] (Heap 점유 객체 종류 확인)
      - jmap -dump:live,format=b,file=heap.hprof [pid] (Memory Dump 생성)