### http-method 활용


#### 클라이언트 -> 서버 데이터 전송: 데이터 전달 방식
- 쿼리 파라미터
  - GET
  - 정렬 필터
- 메시지 바디
  - POST, PUT, PATCH
  - 리소스 등록, 리소스 변경
- 

#### 클라이언트 -> 서버 데이터 전송: 4가지 상황
- 정적 데이터 조회
  ```text
    GET /static/start.jpg HTTP/1.1
    Host: localhost:8080
    
  ```
  - 이미지, 정적 텍스트 문서
  - GET 사용
  - 쿼리 파라미터 없이 리소스 경로로 단순하게 조회
- 동적 데이터 조회
  ```text
    GET /search?q=test&hl=ko HTTP/1.1
    Host: www.google.com
    
  ```
  - 검색, 게시판 목록 정렬 필터
  - GET 사용
  - 쿼리 파라미터를 사용해서 데이터 전달
- HTML Form을 통한 데이터 전송
  ```html
    <form action="/save" method="post">
      <input type="text" name="username" />
      <input type="text" name="age" />
      <button type="submit">전송</button>
    </form>
    
    POST /save HTTP/1.1
    Host: localhost:8080
    Content-Type: application/x-www-form-urlencoded
  
    username=kim&age=20
  ```
  ```html
    <form action="/save" method="get">
      <input type="text" name="username" />
      <input type="text" name="age" />
      <button type="submit">전송</button>
    </form>
    
    GET /save?username=kim&age=20 HTTP/1.1
    Host: localhost:8080
  
  ```
  ```html
    <form action="/save" method="get">
      <input type="text" name="username" />
      <input type="text" name="age" />
      <button type="submit">전송</button>
    </form>
    
    GET /save?username=kim&age=20 HTTP/1.1
    Host: localhost:8080
  
  ```
- HTTP API를 통한 데이터 전송
