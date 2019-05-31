5월 31일 (금) 13:00 - 17:00

컴포넌트 디자인 패턴

이현섭

# 인트로
  - 디자인패턴 -> 제대로 짜는 방법
  - 리액트 기본에 집중
  - 컴포넌트가 왜 중요?
    - 리액트의 기본 단위
    - 잘 만든 리액트 앱이란 결국 작고 단단한 컴포넌트를 유기적으로 연결하는 것
  - 컴포넌트란?
    - 결국 자바스크립트 함수다
      - 뷰를 렌더링하는 자바스크립트 함수
  - 강의에서 다루는 것
    - State를 분리하고 컴포넌트를 추상화하기
    - React.memo와 PureComponent
    - Controlled / Uncontrolled 컴포넌트
    - Functional Component with Hooks
    - Portal Component
    - Component Composition
  - HOC는 왜 다루지 않나요?
    - HOC는 Hooks로 대체 가능
    - Making Sense of React Hooks라는 글을 읽어보는 것을 추천
# State 캡슐화 / 컴포넌트 추상화
  - 첫 링크 https://stackblitz.com/edit/react-bootcamp-form?file=JoinForm.js
    - 이메일과 패스워드가 state가 아닌데, 어떻게 바꿔야 하는가?
    - state는 왜 필요한가?
    - 이 패턴(no state)의 장점
      - 랜더가 발생하지 않는다.
      - 만일 Reset이 필요하다면?
    - no state = uncontrolled / state = controlled
    - controlled = 상태를 관리하기 용이하다. / 리액트도 권장
    - PureComponent 
      - 바뀐 것만 로직으로 검사
      - Pure 컴포넌트 사용 시에도 주의필요!
        - 부작용 있음
        - 항상 Shallow Compare로 비교하기 때문에, 엘리먼트 내부에 화살표 함수로 기재 시에 계속 다른 함수로 인식하여 비효율
        - Shallow Compare의 특성을 잘 고려해야 한다.
  - Position fixed를 하위 컴포넌트에서 하고 싶은데 어떻게 해야 할까?
    - transform이 있는 경우 이상한 버그 발생
      - transform을 유지하면서 어떻게 원했던대로 진행?
        - 포탈컴포넌트
          - 포탈컴포넌트는 index.html 에서 엘리먼트 하나 추가해주고,
          - react-dom 의존성을 이용, createPortal 메소드를 이용한다.
          - 리액트 어디서 렌더링 되던간에 최상위로 뽑아낼 수 있다.
          - modal, 툴팁, 드롭다운과 같은 것들에 이용 가능...
  - 컴포지션(합성) 패턴
    - children, props 만들 수 있음
    - pure 컴포넌트로는 안만드는게 좋다 (렌더링 시에 성능만 떨어짐, 다른 객체로 인식하여 계속 새로 렌더)
      - 단 다른 컴포넌트 하나로 다시 감싸게 되면, 이러한 현상을 방지할 수 있다. (같은 Props를 받아서 주소값 같음)
        - 이러한 기법을 Specialization이라고 부름
# Presentational / Container Component
# Controlled / Uncontrolled Component
# Hooks
  - 함수형 컴포넌트 사용
    - 기본적으로 리액트의 컴포넌트는 함수
    - 공식 문서에서 화살표 함수보다는 function을 많이 써서 function 방식을 선호
  - react.memo는 함수형 컴포넌트의 pure 컴포넌트임
    - memo는 memoization에서 따온 이름임
      - 하지만 사실 memoization을 하진 않는다
      - 순수함수의 입력이 같으면 return하는 결과도 같다. props가 같으면 렌더링할 값도 항상 같다. 그런 의미로 purecomponent라고 부르는 것임
  - useState 로 state 사용 가능
  - useCallback 으로 callback 함수 사용 가능
    - useCallback 의 두번째 인자는 의존성 목록, 의존하는 state 값
      - 의존성 목록이 필요한 이유는, hooks의 state는 closure와 같은 개념이기 때문에, 가져오려면 의존성을 작성해야 한다.
      - 훅스는 의존성 목록을 보고 콜백 함수를 새로 작성해야 하는지 결정한다.
  - useRef
    - 기본적으로는 DOM 요소를 가져오기 위함
    - 렌더링과 관련 없는 어떤 값이 필요할 때
      - useState와 가장 큰 차이는 바뀌어도 렌더링이 일어나지 않는다.
  - useEffect
    - 빈배열 1번만
    - 렌더가 완료된 타이밍에 호출됨
# Form Component + Formik
