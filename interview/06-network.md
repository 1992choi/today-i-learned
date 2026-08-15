## OSI 7계층과 TCP/IP 4계층
- OSI 7계층과 TCP/IP 4계층
  - <img width="837" height="679" alt="image" src="https://github.com/user-attachments/assets/ba9ad29a-efee-4a92-8a4c-7bff30c95d19" />
- OSI 7계층이란?
  - 네트워크 통신이 일어나는 과정을 7단계로 나눈 국제 표준화 기구(ISO)에서 정의한 네트워크 표준 모델이다.
  - 이 모델은 프로토콜을 기능별로 나눈 것이다.
- OSI 7계층 - 계층별 특징
  - 물리 계층(Physical)
    - 전기적, 기계적, 기능적인 특성을 이용하여 통신 케이블로 데이터를 전송한다.
    - 사용되는 통신 단위는 비트(bit)이며, 0또는 1만 나타낼 수 있다.
    - 단지 데이터를 전달만 할 뿐 전송하려는, 또는 받으려는 데이터가 무엇인지는 전혀 신경쓰지 않는다.
    - 대표적인 장치로 통신 케이블, 리피터, 허브 등이 있다.
  - 데이터 링크 계층(Data Link)
    - 물리 계층을 통해 송수신되는 정보의 오류와 흐름을 관리하여 안전한 정보의 수행을 도와주는 역할을 한다.
    - 맥 주소(MAC Address)를 가지고 통신한다.
    - 전송되는 단위를 프레임(frame)이라고 하며, 대표적인 장비로는 브리지, 스위치 등이 있다.
  - 네트워크 계층(Network)
    - 경로를 선택하고 주소를 정하고 경로에 따라 패킷을 전달해주는 역할을 한다.
    - 데이터를 목적지까지 효율적인 경로로 전달하는 기능(라우팅)을 한다.
    - 대표적인 장비로 라우터, (라우팅 기능이 포함된)스위치가 있으며, IP 주소를 사용한다.
    - 데이터를 연결하는 다른 네트워크를 통해 전달함으로써 인터넷이 가능하게 만드는 계층이다.
  - 전송 계층(Transport)
    - 통신을 활성화하기 위한 계층이다. 보통 TCP 프로토콜을 사용하며, 포트를 열어서 응용 프로그램을 전송한다.
    - 양 끝단의 사용자들이 신뢰성 있는 데이터를 주고 받을 수 있게 해 주어, 상위 계층들이 데이터 전달의 유효성이나 효율성을 생각하지 않도록 한다.
  - 세션 계층(Session)
    - 데이터가 통신하기 위한 논리적인 연결을 한다.
    - 세션 설정, 유지, 종료, 전송 중단시 복구 등의 기능이 있다.
    - 양 끝단의 응용 프로세스가 통신을 관리하기 위한 방법을 제공한다.
    - TCP/IP 세션을 만들고 없애는 책임을 진다.
  - 표현 계층(Presentation)
    - 데이터 표현이 상이한 응용 프로세스의 독립성을 제공하고, 암호화한다.
    - 코드 간의 번역을 담당하여 사용자 시스템에서 데이터의 형식상 차이를 다루는 응용 계층의 부담을 덜어준다.
    - 해당 데이터가 텍스트인지, 그림인지, GIF인지, JPG인지의 구분 등의 역할을 한다.
  - 응용 계층(Application)
    - 최종 목적지로서 HTTP, FTP, SMTP, Telnet 등과 같은 프로토콜이 있다.
    - 응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행한다.
- TCP/IP 4계층이란?
  - 네트워크 전송 시 데이터 표준을 정리한 것이 OSI 7계층이었다면, 이 이론을 실제로 사용하는 인터넷 표준이 TCP/IP 4계층이다.
- TCP/IP 4계층 - 계층별 특징
  - 네트워크 인터페이스 계층(Network Access/Network Interface)
    - OSI 계층의 1,2 계층에 해당된다.
    - TCP/IP 패킷을 네트워크 매체로 전달하는 것과 네트워크 매체에서 TCP/IP 패킷을 받아들이는 과정을 담당한다.
    - 에러 검출 기능과 패킷의 프레임화 기능을 수행한다.
    - 트레일러(Trailer)의 CRC를 통해 오류를 검출(Error Control)한다.
  - 인터넷 계층(Internet)
    - OSI 계층에서 3계층에 해당된다.
    - 어드레싱(addressing), 패키징(packaging), 라우팅(routing) 기능을 제공한다.
    - 논리적 주소인 IP를 이용한 노드간 전송과 라우팅 기능을 처리하게 된다.
    - 네트워크상 최종 목적지까지 정확하게 연결되도록 연결성을 제공한다.
    - 핵심 프로토콜은 IP, ARP, ICMP, IGMP 등이 있다.
  - 전송 계층(Transport)
    - OSI 계층에서 4계층에 해당된다.
    - 자료의 송수신을 담당한다.
    - 어플리케이션 계층의 세션과 데이터그램 통신서비스를 제공한다.
    - TCP/UDP가 핵심 프로토콜이다. TCP/UDP에 대한 구분을 하고 데이터에 대한 제어 정보가 여기에 포함된다.
  - 응용 계층(Application)
    - 다른 계층의 서비스에 접근할 수 있게 하는 어플리케이션을 제공한다.
    - 어플리케이션들이 데이터를 교환하기 위해 사용하는 프로토콜을 정의한다.
    - TCP/IP 네트워크를 사용하거나 관리하는 것을 도와주는 프로토콜이다.
- Ref.
[DevOwen](https://devowen.com/344),
[Im-D](https://github.com/im-d-team/Dev-Docs/blob/master/Network/OSI7%20Layer.md)
<br><br><br>

## TCP vs UDP
- TCP(Transmission Control Protocol)
  - TCP는 신뢰성 있는 데이터 전송을 지원하는 연결 지향형 프로토콜이다.
  - 일반적으로 TCP와 IP가 함께 사용되는데, IP가 데이터의 전송을 처리한다면 TCP는 패킷을 추적하고 관리하는 역할을 한다.
  - 연결 지향형인 TCP는 3-way handshaking이라는 과정을 통해 연결 후 통신을 시작하는데, 흐름 제어와 혼잡 제어를 지원하며 데이터의 순서를 보장한다.
  - UDP에 비하여 전송속도가 느리다.
  - 신뢰성이 높다.
- UDP(User Datagram Protocol)
  - UDP는 비연결형 프로토콜이다.
  - 인터넷상에서 서로 정보를 주고받을 때, 신호 절차를 거치지 않고 보내는 쪽에서 일방적으로 데이터를 전달하는 통신 프로토콜이다.
  - TCP와는 다르게 연결 설정이 없으며, 혼잡 제어를 하지 않기 때문에 TCP보다 전송 속도가 빠르다.
  - 데이터 전송에 대한 보장을 하지 않기 때문에 패킷 손실이 발생할 수 있다.
  - 패킷 오버헤드가 적어 네트워크 부하가 감소한다.
  - 신뢰성이 낮다.
- Ref.
[코딩 공부 일지](https://cocoon1787.tistory.com/757)
<br><br><br>

## 3-Way handshake & 4-Way hadnshake
- 3-Way Handshake란?
  - TCP/IP 프로토콜을 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 뜻한다.
- 3-Way Handshake의 동작 순서
  - <img width="965" height="607" alt="image" src="https://github.com/user-attachments/assets/d97c52dd-7bd7-484e-a3b8-f8de155cd69a" />
  - Step1. SYN
    - Client가 Server에게 접속을 요청하는 SYN플래그를 보낸다.
  - Step2. SYN + ACK
    - Server는 Listen상태에서 SYN이 들어온 것을 확인하고 SYN_RECV상태로 바뀌어 SYN + ACK플래그를 Client에게 전송한다.
    - 그 후 Server는 다시 ACK 플래그를 받기 위해 대기상태로 변경된다.
  - Step3. ACK
    - SYN + ACK 상태를 확인한 Client는 서버에게 ACK를 보내고 연결 성립(Established)이 된다.
- 4-Way Handshake란?
  - 3-Way handshake가 연결확립을 위해 진행했다면 4way handshake는 세션을 종료하기 위해 수행되는 절차를 뜻한다.
- 4-Way Handshake의 동작 순서
  - <img width="952" height="800" alt="image" src="https://github.com/user-attachments/assets/c2484c3f-ce09-4eb4-b3ec-cb31000ef53e" />
  - Step1. FIN
    - Client가 연결을 종료하겠다는 FIN플래그를 전송한다.
    - 보낸 후에 FIN-WAIT-1 상태로 변한다.
  - Step2. ACK
    - FIN 플래그를 받은 Server는 확인메세지인 ACK를 Client에게 보내준다.
    - 그 후 CLOSE-WAIT상태로 변한다.
    - Client도 마찬가지로 Server에서 종료될 준비가 됐다는 FIN을 받기위해 FIN-WAIT-2 상태가 된다.
  - Step3. FIN
    - Close준비가 다 된 후 Server는 Client에게 FIN 플래그를 전송한다.
  - Step4. ACK
    - Client는 해지 준비가 되었다는 정상응답인 ACK를 Server에게 보내준다. 이 때, Client는 TIME-WAIT 상태로 변경된다.
    - 여기서 TIME-WAIT 상태는 의도치않은 에러로 인해 연결이 데드락으로 빠지는 것을 방지하기 위해 변경 되는 것인데, 만약 에러로 인해 종료가 지연되다가 타임이 초과되면 CLOSED 상태로 변경된다.
- Ref.
[나의 과거일지](https://jeongkyun-it.tistory.com/180)
<br><br><br>

## HTTP와 HTTPS
- HTTP : 평문 전송, 포트 80
- HTTPS : SSL/TLS 암호화, 포트 443
- 차이 : 보안(암호화), 포트, CA 인증서 필요 여부
<br><br><br>

## HTTP 상태코드
- 2xx : 200 OK / 201 Created / 204 No Content
- 3xx : 301 영구이동 / 302 임시이동 / 304 Not Modified
- 4xx : 400 Bad Request / 401 Unauthorized / 403 Forbidden / 404 Not Found / 429 Too Many Requests
- 5xx : 500 Internal Server Error / 502 Bad Gateway / 503 Service Unavailable
<br><br><br>

## DNS
- 도메인 → IP 변환 시스템
- 동작: 로컬 캐시 → OS 캐시 → DNS 서버 재귀 질의
- 레코드: A(IPv4), AAAA(IPv6), CNAME(별칭), MX(메일)
<br><br><br>

## 로드밸런서
- 알고리즘: 라운드 로빈 / 가중 라운드 로빈 / 최소 연결 / IP 해시
- L4: TCP/UDP 기반 / L7: HTTP 헤더·URL 기반 세밀한 분산
<br><br><br>

## 웹 캐시
- 종류: 브라우저 캐시 / 프록시 캐시 / CDN
- 헤더: Cache-Control(no-cache, no-store, max-age) / ETag / Last-Modified
<br><br><br>

## 소켓
- IP + 포트로 구분되는 통신 엔드포인트
- HTTP: 단방향 요청·응답 / WebSocket: 연결 유지 양방향 실시간 통신
<br><br><br>
