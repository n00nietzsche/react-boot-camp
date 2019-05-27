# 리액트 시작부터 배포까지

## 왜 리액트?
- SPA
  - 고객의 요구사항 때문에 등장
  - 페이지가 리로드되지 않음 -> 유저경험 업그레이드
  - 가장 대표적인 SPA는 페이스북
- 돈을 더 많이 벌음...
  - 내 회사에서는 Vue, 일할 때는 React
- Virtual DOM
  - 렌더링이 빠름
- Component
  - 높은 재사용성, 빠른 개발
- JSX
  - 선언적, 직관적, 높은 생산성
  - 찬반이 굉장히 나뉘었음
  - MVC 모델을 만들기 위함
  
## 라이벌
- Vue.js

## 시작하기: CRA or Next or Self?
- CRA
  - 사실상 표준 
  - 현업에서도 굉장히 많이 사용
- Next.js
  - 명령어를 순서대로 치면 됨
  - npm install next react react-dom
  - npm init
  - 이후 pages/index.js를 작성하면 됨
  ```
  function Home() {
    return <div>Welcome to Next.js</div>;
  }
  
  export default Home;
  ```
  ```
  "scripts": {
    "dev": "next",
    "build": "next build",
    "start": "next start"
  }
  ```
  - 서버사이드 렌더링이 기본으로 제공
  - 코드 스플리팅이 자동으로 됨
  - 간단한 클라이언트 사이드 라우팅... (ppt 참조)
- Self
  - CRA 앱을 eject 하면 가능
  - 최신 디펜던시 업데이트 등을 자신이 수동으로 해주어야 함


## React의 특성: 통신 구조, 랜더링, 라이프 사이클

## 개발 스택 구성: JS or TS? Redux or MobX?

## 프로젝트 폴더 구성: Components or Molecules?

## React 브라우저 라우팅: react-router

## 높은 생산성을 위한 HMR: react-hot-loader

## 검색 엔진을 위한 SSR (Server side rendering)

## 배포하기: S3 or Github or ECS or Lambda
