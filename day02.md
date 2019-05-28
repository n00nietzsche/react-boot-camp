# React Front-End Development
- 장기영
- 오픈소스 기여
  - AXISJ
  - AXBOOT ....
- ANT design이 가장 좋았다...

- CRA로 React-TS 프로젝트 시작하기
- app-rewire를 사용, less-loader 연결
- antd, styled-component
- Style and Theme in React.js
- 효율적인 코드 작성 (destructing, async, await ...)
- 레이아웃 리사이징...  드래그앤 드랍 소팅...

# React + Typescript 프로젝트 셋팅
- CRA는 왜 써야하나..?
  - index.html 형식에 맞게 구성
  - webpack 설치, 설정
  - babel
  - React
  - TypeScript
  - HMR (Hot Module Replacement)
  
- ESLint
  - 분명 사내에선 형식에 맞는 코드가 필요하다.....
  
- CRA
  - npx create-react-app ${appname} --typescript
  - @type/ .... 의 패키지가 추가됨.. type definition
  - index.tsx가 entry point
  
- 기타 설명
  - popover / modal 등은 잠시 DOM을 구성했다가 다시 없애버림
    - body의 맨 끝에 삽입
    - react의 사상과는 맞지 않음...
      - 미리 구성된 DOM이 아님..
      
- react app rewired
  - 업데이트를 중단하게 됨.....
  - 대체재 craco
  
- craco
  - Create React App의 Configuration을 Override 해주는 도구...
  - craco.config.js에 설정을 입력하면 됨....
    - 여기서는 예제로 less 파일을 추가해보았음...
    ```js
    const CracoLessPlugin = require('craco-less');
    module.exports = {
      plugins: [{ plugin: CracoLessPlugin }]
    };
    ```
    - sass파일도 추가 가능하다...
      - 다만 node-sass는 깔아줘야 한다...
    - 모든 css 확장자를 지원하는 것은 중요...
      - 여러 개발자와 협업하는 도중 그들의 스타일에 맞출 필요가 있기 때문....
  
# Ant Design 설치 및 환경 구성



# 데모 프로젝트 만들기



# 스타일링 / 테마다루기



# 효율적인 코드 작성 (구조분해할당, Async / Await, Type)



# 드래그 & 리사이징 (Resizing, ellipsis, Drag & drop, Sub component auto resizing)


