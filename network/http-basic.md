## HTTP (Hyper Text Transfer Protocol)

#### 모든 것이 HTTP: HTTP 메시지에 모든 것을 전송
- html, text
- 이미지, 음성, 영상, 파일
- JSON, XML
- 서버간 통신

#### HTTP 역사
- HTTP/0.9 1991년: GET 메서드만 지원, HTTP 헤더 없음
- HTTP/1.0 1996년: 메서드, 헤더 추가
- `HTTP/1.1` 1997년: 가장 많이 사용
- HTTP/2 2015년: 성능 개선
- HTTP/3 진행중: TCP 대신 UDP 사용

#### 기반 프로토콜
- TCP: HTTP/1.1, HTTP/2
- UDP: HTTP/3
- HTTP/1.1 주로 사용

#### HTTP 특징
- 클라이언트 서버 구조
  - Request / Response 구조
  - 클라이언트는 서버에 요청 보내고, 응답 대기
  - 서버는 요청에 대한 결과를 응답
  - `클라이언트와 서버 양쪽이 독립적으로 진화 가능`
- 무상태 프로토콜(stateless), 비연결성
- HTTP 메시지
- 단순함, 확장 가능

#### 무상태 프로토콜: stateless
- 서버가 클라이언트의 상태를 보전하지 않음
- 장점: 서버 확장성 높음(스케일 아웃)
- 단점: 클라이언트가 추가 데이터 전송

|   stateful   |  stateless   |
|:------------:|:------------:|
|     애플워치     |     애플워치     |
|      2개      |   애플워치 2개    |
|     신용카드     | 애플워치 2개 신용카드 |
| 고객 증가에 대응 힘듬 | 고객 증가에 대응 쉬움 |

#### 비 연결성: connectionless
- HTTP는 기본적으로 연결을 유지하지 않음
- 초 단위의 빠른 속도로 응답
- 동시에 처리하는 요청의 수는 적음
- 서버 자원을 효율적으로 사용

---

- TCP/IP 연결을 새로 맞어야 하는 한계 - 3 way handshake 시간 추가
- HTTP 지속연결(Persistent Connections)로 문제 해결
  - 연결/종료 낭비 줄임

|기존|지속연결|
|:---:|:---:|
|연결|연결|
|요청/HTML 응답|요청/HTML 응답|
|종료|요청/JS 응답|
|연결|요청/이미지 응답|
|요청/JS 응답|종료|
|종료||
|연결||
|요청/이미지 응답||
|종료||

#### HTTP 메시지
- HTTP 요청 메시지
  ```text
    GET/search?q=test&hl=ko HTTP/1.1
    Host:www.google.com 
  ```
  
- HTTP 응답 메시지
  ```text
    HTTP/1.1 200 OK
    Content-Type: text/html;charset=UTF-8
    Content-Length: 3423
    
    <html>
      <body>...</body>
    </html>
  ```
  
- HTTP 메시지 구조
  ```text
    start-line 시작 라인
    header 헤더
    empty line 공백라인(CRLF)
    message body
  ```
  
- 공식 스펙(rfc7230)
  ```text
    start-line
    *( header-field CRLF )
    CRLF
    [ message-body ]
  ```

- 시작 라인(요청 메시지)
  - `request-line` = method SP(공백) request-target SP HTTP-version CRLF(엔터)
    - method: 서버가 수행햐애 할 동작 지정
      - GET, POST, PUT, DELETE
    - request-target
      - 절대경로 `/`로 시작하는 경로
    - HTTP-version

- 시작 라인(응답 메시지)
  - `status-line` = HTTP-version SP status-code SP reason-phrase CRLF
    - HTTP-version
    - status-code: 요청 성공, 실패를 나타냄
      - 200: 성공
      - 400: 클라이언트 요청 오류
      - 500: 서버 내부 오류
    - reason-phrase: 사람이 이해할 수 있는 짦은 설명

- HTTP 헤더
  - `header-field` = field-name":" OWS(띄어쓰기 허용) field-value OWS
    - field-name
      - 대소문자 구분 없음
    - field-value
      - 대소문자 구분 있음
  - HTTP 전송에 필요한 모든 부가정보
  - 수 많은 표준 헤더
  - 임의의 헤더 추가 가능

- HTTP 메시지 바디
  - 실제 전송할 데이터
  - HTML 문서, 이미지, 영상, JSON 등 byte로 표현할 수 있는 모든 데이터 전송 가능
