# System Design
- Inflearn > 개발자라면 꼭 알아야할 시스템디자인 완벽가이드

<br><br>

## 개념 정리
### Latency
- 요청(Request)을 보낸 시점부터 응답(Response)을 받기까지 걸리는 시간
- 네트워크 지연, 서버 처리 시간, DB 조회 시간 등 여러 구간의 시간이 합쳐진 값
- 값이 낮을수록 사용자 체감 속도가 빠름

### Throughput
- 단위 시간당 처리할 수 있는 요청(Request)의 양 
- 보통 RPS(Requests Per Second), TPS(Transactions Per Second)로 표현 
- 서버의 CPU, 메모리, 스레드 수, DB 성능 등에 영향을 받음 
- 값이 높을수록 같은 시간에 더 많은 요청을 처리 가능 
- Latency(지연 시간)와는 다른 개념으로, “얼마나 많이 처리하느냐”에 초점이 있음

### 수평확장 vs 수직확장 (Vertical vs Horizontal Scaling)
- 수직 확장(Vertical Scaling)
  - 기존 서버의 CPU, 메모리, 스펙을 업그레이드하는 방식 
  - 구조가 단순하고 관리가 쉽지만, 물리적 한계가 존재하며 비용이 급격히 증가할 수 있음 
  - 서버 1대에 의존하는 구조가 되기 쉬워 SPOF(Single Point Of Failure, 단일 장애 지점)가 발생하기 쉬움 
- 수평 확장(Horizontal Scaling)
  - 동일한 서버를 여러 대로 늘려 부하를 분산하는 방식 
  - 로드 밸런서를 통해 트래픽을 분산하며, 트래픽 증가에 유연하게 대응 가능 
  - 여러 대 중 일부가 장애가 나더라도 전체 서비스가 중단되지 않아 SPOF를 완화할 수 있음
- 비교
  - 수직 확장은 “한 대를 강하게”, 수평 확장은 “여러 대로 나누어” 처리하는 전략이며 고가용성(HA) 관점에서는 일반적으로 수평 확장이 더 유리함