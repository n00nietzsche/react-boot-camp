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
- Ant Design 세팅하기
  - `"@types/styled-components": "^4.1.15",`
  - type 스크립트를 이용하여 미리 정의된 데피니션 확인 가능 (자동완성 기능 업그레이드)
  ```js
  const CracoLessPlugin = require('craco-less');

  module.exports = {
    plugins: [
      {
        plugin: CracoLessPlugin,
        options: {
          lessLoaderOptions: {
            javascriptEnabled: true
          }
        }
      }
    ]
  };
  ```
- JoinForm 만들기...
  - react의 form에는 뭔가 귀찮은 것이 있음
    - 모든 form의 input들을 state화 시켜야 한다?
    - 입력 사항이 굉장히 많은데 어떻게?
    - ant design의 자동화를 이용하자
      - 자동 state 바인딩을 이용하자
  - TS에서 `<Prop>`처럼 제네릭 타입을 이용
  - 에러 + 라이브코딩 안하시고 갑자기 넘어가셔서 무슨 내용인지 잘 못들음.. 혼자 antd form 공부하면 될 것 같음...
- 마크다운 tsx 만들기
  - 패키지를 고를 때, 디펜던시를 잘 봐야 함 ...
  - 절차
    1. markdown-to-jsx를 설치 후 MarkdownView.tsx 작성
    ```js
    import React from "react";
    import Markdown from "markdown-to-jsx";
    import mdContents from "./README.md";
    interface IProps {}

    class MarkdownView extends React.Component<IProps> {
      render() {
        return (
          <div>
            <Markdown>{mdContents}</Markdown>
          </div>
        );
      }
    }

    export default MarkdownView;
    ```
    2. craco-raw-loader를 설치 
    3. craco.config.js에서 craco-raw-loader를 import
    4. 설정 `{ plugin: rawLoader, options: { test: /\.(md|txt)$/ } }`
    5. 임포트하여 쓰면 됨

- Destructuring 비구조화 할당, async/await

# 스타일링 / 테마다루기
- 기타 여러가지 Antd 컴포넌트들 사용법 배웠음
- 내용이 방대해 적진 않음 
- Antd 문서보며 혼자 공부할 수 있음... 


# 효율적인 코드 작성 (구조분해할당, Async / Await, Type)
- 각종 구조분해 할당을 이용하여 자바스크립트 코드 간결화 .... 이미 알던 내용


# 드래그 & 리사이징 (Resizing, ellipsis, Drag & drop, Sub component auto resizing)
- resizing 해보았음
- throttle
- debounce 는 알아봐야 함
- 많은 데이터를 다룰 때 응용 가능
  - ex) 500만개의 데이터를 다룰 때는 보여지는 부분만 DOM을 넣자...

# Q&A
- 인터페이스 선언은 어디에? 공통적인 영역? 컴포넌트 안에?
  - 인터페이스가 재사용 될 일이 많이 없다...
    - 대부분의 경우에서 컴포넌트 안에 쓴다
  - 가끔 재사용 하기도 한다..
    - 그럴 때는 공통적인 영역
- Form에서 라디오, 체크박스는 처리하기가 까다롭다.. 어떤식으로 해결? Formeik을 사용해본적이 있는가?
  - Antd로 처리한다. 모든 Form의 내용을 Json으로 전부 뽑아준다... 그런 이유로 Formeik을 써본적이 없다.
- 많은 Key값 들의 전략을 어떻게 가져가는가?, 데이터가 엄청나게 많을 때
  - 단순히 시작점과 끝점을 공식으로 만들어서 for문으로 처리, key에 따라 성능이 좌우되지 않는다고 생각
  - 오히려 많은 데이터를 화면에 표시하며 style 이슈를 겪었음... 너무나 큰 픽셀을 스타일화 하니 이슈 발생
    - 그럼에 있어서 너무 큰 숫자를 key로 넣는 것은 적합하지 않을 수도 있따는 생각을 함
