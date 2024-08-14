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



<br><hr><br>



## 실습
### 제목
- 내용
