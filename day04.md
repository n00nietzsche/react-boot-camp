React Apollo로 GraphQL 적용하기

최강혁

# GraphQL 설명
- 크게 절차별로 3가지로 나뉜다
  - 타입을 묘사하는 그래프 QL
    - 제공할 데이터를 묘사
    - 서버 사이드
  - 쿼리를 요청하는 그래프 QL
    - 요청할 데이터를 묘사
    - 클라이언트 사이드
  - 결과 JSON
    - 서버가 보내고 클라이언트가 받게 될 결과
- 그래프QL 기본 문법 배우기
  - 쿼리 (데이터를 요청만 함)
    ```graphql
    query getMessage($id: ID!){
      thisismessage: message(id: $id){
        id
        payload
        createdAt
      }
    }
    ```
    - 변수는 왼쪽 아래 Variable에서 JSON의 형태로 지정
    ```js
    {
      "id": "0"
    }
    ```
  - 뮤테이션 (데이터를 변경)
    ```graphql
    mutation( $input: CreateUserInput! ){
      createUser(input:$input){
        id
        name
      }
    }
    ```
    - 변수
    ```js
    {
      "input":{"name": "민수킴"}
    }
    ```

# Apollo Client 기초
- 아폴로 클라이언트
  - 쿼리 등을 요청...

- 아폴로 캐시
  - 쿼리의 결과를 저장
  - 요청을 보내기 전에 필요한 데이터가 있는지 확인

- 아폴로 링크
  - 외부 GraphQL 요청에 대한 인터페이스를 제공
  - 통신 레이어 추상화, 상황에 따라 서버 없이 사용 가능
  - mock, 서버가 있는 것처럼 만드는 것도 가능

- GraphQL 서버
  - 리액트 to 아폴로 to (아폴로 캐시) to 아폴로 링크 to 아폴로 서버

- apollo-link-persisted-queries
  - 쿼리를 보관하고 해쉬로 쿼리 연결
  - 단, variable을 하드코딩하면, 해쉬 값이 계속 변해서 의미 없음
  
- Batch HTTP Link
  - 쿼리를 보내는 횟수를 매우 줄여서 네트워크 부하 작게 가능
  - 느린 Query가 전체에 영향을 준다
  - 네트워크 수준 디버깅이 불편
  - CDN에서 캐시하기 어려움
  - HTTP2 지원하면 의미 없음

- 스키마 링크란 것이 있음
  - 원래는 서버에 있는 것이 자연스러우나 굳이 서버에 있을 필요는 없다.
  - 스키마를 클라이언트에 구현하고, 링크스키마로 링크로 엮어준다.
    - 그럼 아폴로 클라이언트에서 똑같이 사용 가능
  - 서버에서 스키마를 고대로 긁어서 클라이언트로 옮긴다.
  - 그럼 서버가 없어도 GraphQL로 데이터를 가져올 수 있다.

- apollo config에서 다음과 같이 설정해주면 타입스크립트에서 타입을 추론 가능
  ```js
  module.exports = {
    client: {
      service: {
        url: "localhost:8888/graphql"
      }
    }
  }
  ```
  - 아폴로라는 cli 툴을 사용하면 npx apollo client:codegen --target typescript로 타입 추출 가능
    - 명령어 실행 결과로 타입이 전부 들어있는 파일을 획득 가능

- 키워드만 알면 찾아볼 수 있는 것 
  - subscription
  - 스키마 링크 (REST API를 GraphQL서버 없이 마이그레이션이 가능하다.)

# React Apollo로 데이터 바인딩


# Apollo Server 기초


# Apollo CLI로 스키마에서 Typescript 코드 생성


# REST 마이그레이션, SSR

