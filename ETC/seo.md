#### SEO
`Search Engine Optimization`

#### SSR
`browser -> front -> back -> db -> back -> front -> browser`
#####  장점
- 초기 로딩 속도 빠름
- SEO 유리
- 로딩 없음
##### 단점
- 서버 부담

#### CSR
`browser -> front -> browser` (js, html, css, img)  
`browser -> back -> db -> back -> browser` ()
#####  장점
- 빠른 화면 전환
##### 단점
- 초기 로딩 속도 느림: 바뀔 페이지 데이터까지 로딩 
- SEO 불리
- back 응답 전까지 로딩

#### Next.js
- 첫 실행: SSR
- 이후: CSR
