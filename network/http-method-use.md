### http-method 활용


#### 클라이언트 -> 서버 데이터 전송: 데이터 전달 방식
- 쿼리 파라미터
  - GET
  - 정렬 필터
- 메시지 바디
  - POST, PUT, PATCH
  - 리소스 등록, 리소스 변경


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
  - GET, POST만 지원

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
  - form 내용을 메시지 바디를 통해서 전송(key=value, 쿼리 파라미터 형식)
  - 전송 데이터를 url encoding 처리

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
    <form action="/save" method="post" enctype="multipart/form-data">
      <input type="text" name="username" />
      <input type="text" name="age" />
      <input type="file" name="file1" />
      <button type="submit">전송</button>
    </form>
  
    POST /save HTTP/1.1
    Host: localhost:8080
    Content-Type: multipart/form-data; boundary=----XXX
  
    ------XXX
    Content-Disposition: form-data; name="username"
    
    kim
    ------XXX
    Content-Disposition: form-data; name="age"
  
    20
    ------XXX
    Content-Disposition: form-data; name="file1"; filename="intro.png"
    Content-Type: image/png
  
    102838dddk4034823948sdf234sdjfh39sm2lwnen...
    ------XXX--
  ```
  - 파일 업로드 같은 바이너리 데이터 정송시 사용
  - 다른 종류의 여러 파일과 폼의 내용을 함께 전송 가능
  

- HTTP API를 통한 데이터 전송
  - 서버 to 서버
  - 앱 클라이언트
  - 웹 클라이언트
    - HTML에서 Form 전송 대신 자바스크립트를 통한 통신에 사용(ajax)
  - POST, PUT, PATCH: 메시지 바디를 통해 데이터 전송
  - GET: 조회, 쿼리 파라미터로 데이터 전송
  - Content-Type: application/json을 주로 사용
  - `JSON`, XML, TEXT
  ```text
   POST /members HTTP/1.1
   Content-Type: application/json
  
   {
     "username": "young",
     "age": 20    
   }
  ```
