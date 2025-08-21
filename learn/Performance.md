# Spring
- Fast Campus > 궁극의 성능 튜닝과 트러블슈팅

<br><br><br>

# 정리
### 성능
- 성능이 중요한 이유
  - 사용자 유지를 좌우
  - 느린 사이트는 수익에 부정적인 영향을 미치고 빠른 사이트는 전환율을 높임
- 성능 측정 지표
  - LCP (Largest Contentful Paint)
    - 로딩 성능을 측정
    - 우수한 사용자 경험을 제공하려면 페이지가 처음으로 로딩된 후 2.5초 이내에 LCP가 발생 해야한다.
  - FID (First Input Delay)
    - 최초 입력 지연
    - 우수한 사용자 경험을 제공하려면 페이지의 FID가 100밀리초 이하여야 함
  - CLS (Cumulative Layout Shift)
    - 시각적 안정성을 측정
    - 우수한 사용자 경험을 제공하려면 페이지에서 0.1 이하의 CLS를 유지
- 성능의 주요 지표
  - 사용자 (Users)
    - 서비스를 사용하는 사용자의 수
    - 성능 테스트 관점에서 사용자는 Active User 와 Concurrent User 로 나눌 수 있다.
      - Active User
        - 서비스에 요청을 하고 기다리는 사용자
        - 메뉴나 링크를 누르고 결과가 나오기를 기다리는 사용자
      - Concurrent User
        - Active User 를 포함
        - 웹 페이지를 띄워 놓은 사용자나 앱을 실행하고 있는 사용자 (아직 직접적인 요청은 없지만 요청을 행할 수 있는 존재)
  - 응답시간 (Response Time)
    - 각 요청에 대한 응답시간
    - Application server 에서 소요되는 시간은 CPU time과 Wait time으로 나뉠 수 있다.
      - CPU time
        - CPU 연산을 하면서 소요되는 시간
      - Wait time
        - DB의 결과를 기다리거나, API 호출한 후 대기하는 등 기다리는 시간을 의미
  - 초당 처리량 (Transactions Per Seconds,TPS)
    - 1초에 처리 가능한 트랜젝션의 수
  - 리소스 사용량 (Resource Usage)
    - CPU, 메모리, 네트워크 등 부하 발생시 리소스 사용량