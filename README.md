# python


## Proxy 변경을 위한 프로그램 설치
- 설치
  - brew install tor
- 서비스 시작
  - brew services start tor
- 설치 위치 확인
  - brew list tor
- 설정파일 변경
  - cp {torrc.sample 경로} /opt/homebrew/etc/tor/torrc
  - nano /opt/homebrew/etc/tor/torrc
    - 아래 항목 수정
      - ControlPort 9051
      - HashedControlPassword <your_password_hash>
        - 비밀번호 만드는 방법
          -  tor --hash-password {your_password}
          -  ex) tor --hash-password 1234
        - 비밀번호는 '16:CF52A67D0F14C6B160EFC9EC32726D68FBC4B52C61D07DAF8C869E57AF'와 같은 형태임. 
- 서비스 재시작
  - brew services restart tor
