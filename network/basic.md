#### 인터넷

#### 패킷 (packet): 네트워크가 전달하는 데이터의 형식화된 블록

#### LAN (Local Area Network) 

#### WAN (Wide Area Network)

#### ISP (Internet Service Provider): 인터넷 서비스 제공자 (SK브로드밴드, KT, LG U+)

#### DMZ (Demilitarized Zone): 외부에 노출된 네트워크 영역 (웹 서버, 이메일 서버, DNS 서버)

#### DNS (Domain Name System): 영문/한글 주소 -> 네트워크에서 찾아갈 수 있는 IP

---

#### IP 패킷 정보: 출발지 IP, 목적지 IP, 전송 데이터

#### IP 프로토콜의 한계
- 비연결성: 패킷을 받을 대상이 없거나 서비스 불능 상태
- 비신뢰성: 패킷 소실, 패킷 전달 순서 바뀜
- 프로그램 구분: 같은 IP를 사용하는 서버에서 통신하는 애플리케이션이 둘 이상

#### 인터넷 프로토콜 스택의 4계층
- 애플리케이션 계층 - HTTP, FTP
- 전송 계층 - TCP, UDP
- 인터넷 계층 - IP
- 네트워크 인터페이스 계층

#### TCP/IP 패킷 정보: IP 패킷 정보 + 출발지 PORT, 목적지 PORT, 전송 제어, 순서, 검증 정보

#### TCP (Transmission Control Protocol) 특징
- 연결지향 - TCP 3 way handshake `(가상 연결)`
- 데이터 전달 보증
- 순서 보장
- 신뢰할 수 있는 프로토콜
- 대부분 TCP 사용 
- 정형화 됨 (최적화 불가능)
- 시간이 오래 걸림

#### TCP 3 way handshake
1. SYN (client -> server)
2. SYN + ACK (server -> client)
3. ACK (client -> server)
4. 데이터 전송

#### 순서 보장
1. 패킷1, 패킷2, 패킷3 순서로 전송 (client)
2. 패킷1, 패킷3, 패킷2 순서로 도착 (server)
3. 패킷2부터 다시 보내(server -> client)
4. 패킷2, 패킷3 순서로 다시 전송 (client)

#### UDP (User Datagram Protocol) 특징
- 하얀 도화지에 비유
- 연결지향 X
- 데이터 전달 보증 X
- 순서 보장 X
- 단순하고 빠름
- PORT + 체크섬
- 애플리케이션에서 추가 작업 필요
- 최적화 가능

#### PORT
- 애플리케이션 구분
- 몇동 몇호에 해당 (IP는 아파트 단지)
- 0 ~ 65535 할당 가능
- 0 ~ 1023: 잘 알려진 포트, 사용하지 않는 것이 좋음
    - FTP - 20, 21
    - TELNET - 23
    - HTTP - 80
    - HTTPS - 443

#### DNS (Domain Name System)
- IP는 기억하기 어려움
- IP는 변경될 수 있음
- 도메인명을 IP 주소로 변환 (전화번호부)

#### URI (Uniform Resource Identifier)
- URL(~ ~ Locator) + URN(~ ~ Name)

#### URL
- scheme://[userinfo@]host[:port][/path][?query][#fragment]
- https://www.google.com:443/search?q=test&hl=ko

---

- scheme - 주로 프로토콜(어떤 방식으로 자원에 접근할지 약속한 규칙) 사용
  - http, https, ftp
- userinfo
  - 사용자 정보를 포함해서 인증
  - 거의 사용 안 함
- port
  - http 80, https 443 정해진 포트는 생략 가능
- path
  - 리소스 경로
  - 계층적 구조
    - /members
    - /members/50
    - /members/50/thumb.jpg
- query
  - key=value 형태
  - ?로 시작, &로 추가 가능
    - ?keyA=valueA&keyB=valueB
  - query parameter, query string 등으로 불림
- fragment
  - html 내부 북마크 등에 사용
  - 서버로 전송하는 정보 아님
  
#### 웹 브라우저 요청 흐름
1. https://www.google.com/search?q=test&hl=ko 입력
2. https://132.250.196.142:443/search?q=test&hl=ko
   - DNS 조회
   - 생략된 port 확인
3. HTTP 요청 메시지 생성
   - ```text
     GET/search?q=test&hl=ko HTTP/1.1
     Host:www.google.com 
     ```
4. SOCKET 라이브러리를 통해 전달
5. TCP/IP 패킹 생성
6. 웹 브라우저 -> 구글 서버 이동
7. 구글 서버에 패킷 도착
8. TCP/IP 패킷을 까서 버리고 HTTP 메시지 해석
9. /search?q=test&hl=ko 관련 데이터 찾음
10. HTTP 응답 메시지 생성
    - ```shell
      HTTP/1.1 200 OK
      Content-Type: text/html;charset=UTF-8
      Content-Length: 3423
     
      <html>
        <body>...</body>
      </html>
      ```
11. 응답 패킷 전달
12. 응답 패킷 도착
13. TCP/IP 패킷을 까서 버리고 HTTP 메시지 해석
14. HTML 렌더링
