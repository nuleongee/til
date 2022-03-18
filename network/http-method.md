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

#### GET, POST

#### PUT, PATCH, DELETE

#### method 속성
