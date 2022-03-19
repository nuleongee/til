### http-method
- 

#### HTTP API
- 회원 정보 관리 API URI 설계
  - 회원 목록 조회 ~~/read-member-list~~ /members
  - 회원 조회 ~~/read-member-by-id~~ /members/{id} `중복`
  - 회원 등록 ~~/create-member~~ /members/{id} `중복`
  - 회원 수정 ~~/update-member~~ /members/{id} `중복`
  - 회원 삭제 ~~/delete-member~~ /members/{id} `중복`
  - 리소스와 행위를 분리
    - URI는 리소스만 식별
    - 리소스: 회원 / 명사
    - 행위: 조회, 등록, 삭제, 변경 / 동사

#### method 종류
- GET: 리소스 조회
- POST: 요청 데이터 처리, 주로 등록에 사용
- PUT: 리소스를 대체, 해당 리소스가 없으면 생성
- PATCH: 리소스 부분 변경
- DELETE: 리소스 삭제
- HEAD: GET과 동일하지만 메시지 부분 제외, 상태 줄과 헤더만 반환
- OPTIONS: CORS에서 사용
- CONNECT
- TRACE

#### GET, POST
- GET
  - 리소스 조회
  - 전달하고 싶은 데이터는 query를 통해 전달
  - 메시지 바디 사용 가능하지만, 권장하지 않음
  - 예시
    - 메시지 전달
    ```text
      GET /members/100 HTTP/1.1
      Host: localhost:8080
    
    ```
    - 서버 도착
    - 응답 데이터
    ```text
      HTTP/1.1 200 OK
      Content-Type: application/json
      Content-Length: 31
    
      {
        "username": "Im",
        "age": 31
      }
    ```
- POST
  - 요청 데이터 처리
    - 새 리소스 생성
    - 요청 데이터 처리: 데이터 생성이나, 변경을 넘어 프로세스를 처리하는 경우
      - 결제 완료 -> 배달 시작 -> 배달 완료
      - POST의 결과로 새로운 리소스가 생성되지 않을 수 있음
        - POST /orders/{oderId}/start-delivery(컨트롤 URI: 동사 형태의 URI)
    - 다른 메서드로 처리하기 애매한 경우
  - `메시지 바디를 통해 서버로 요청 데이터 전달`
  - 주로 전달한 데이터로 신규 리소스 등록, 프로세스 처리에 사용
  - 예시
    - 메시지 전달
    ```text
      POST /members HTTP/1.1
      Content-Type: application/json
    
      {
        "username": "sb",
        "age": 20    
      }
    ```
    - 신규 리소스 생성
    - 응답 데이터
    ```text
      HTTP/1.1 201 Created
      Content-Type: application/json
      Content-Length: 31
      Location: /members/100
    
      {
        "username": "sb",
        "age": 20
      }
    ```
  
#### PUT, PATCH, DELETE
- PUT
  - 리소스가 있으면 완전 대체
  - 리소스가 없으면 생성
  - `클라이언트가 리소스를 식별`
  ```text
      PUT /members/100 HTTP/1.1
      Content-Type: application/json
    
      {
        "username": "ls",
        "age": 22
      }
    ```
- PATCH
  - 리소스 부분 변경
  ```text
      PATCH /members/100 HTTP/1.1
      Content-Type: application/json
    
      {
        "age": 30
      }
    ```
- DELETE
  - 리소스 제거
  ```text
      DELETE /members/100 HTTP/1.1
      Host: localhost:8080

    ```
#### method 속성
