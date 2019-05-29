# TDD 의 기초

- 테스트란?
  - 무언가가 작동하는지 확인하는 것
  - 사람이 일일히 하기엔 노동력이 너무 많이 필요, 자동화가 필요하다.

- 주요 이점
  - 원활한 협업
  - 자신감 있게 리팩토링

- 테스트코드를 작성한다고 버그가 발생하지 않는 것은 아니다.
  - 원인 분석에 대한 이해속도가 빨라짐
  - 버그가 발생했을 때, 테스트 케이스를 만들면 실수를 하지 않게 됨

- 유닛 테스트와 통합 테스트란?
  - 유닛 테스트는 자그마한 단위로 쪼개서 테스트 하는 것
  - 통합 테스트는 여러가지 기능을, 전체적인 흐름을 테스트
  - GIF그림들...
  - 둘 다 필수적이다

- 테스트 도구?
  - 다양한 도구가 있다..
    - JEST
    - Karma
    - Mocha
    - Chai

- 이번 실습 때 사용 할 도구는 JEST
  - 페북 개발팀이 만듦
  - CRA에 기본 적용
  - 초기 설정이 편함
  
- TDD란?
  - 테스트 주도 개발 (Test Driven Development)
  - 실패(RED), 성공(GREEN), 리팩토링(BLUE)으로 이루어짐
  - 처음에는 실패하는 케이스 작성, 두번째는 테스트 통과시키고, 세번째는 리팩토링
  
  
# JavaScript 테스트

- 간단한 테스트
  ```js
  const sum = require('./sum');

  test('1 + 2 = 3', () => {
    expect(sum(1, 2)).toBe(3);
  })
  ```
  - '1 + 2 = 3'의 경우는 테스트의 이름을 의미하는 것임
  - 뒤에는 콜백함수를 작성한 것이고, expect는 matcher인 toBe와 함께 뒤의 값이 ~가 될 것이다 라는 것
  - script 작성해주어야 함
  - test대신 it이라는 메소드를 사용해도 같은 결과
  ```js
  const sum = require('./sum');

  it('calculates 1 + 2', () => {
    expect(sum(1, 2)).toBe(3);
  })
  ```
  
- 테스트를 묶는 방법 describe
  - 통합 테스트를 만들 때 유용할 수 있다.
  ```js
  const { sum, sumOf } = require('./sum');
  
  describe('sum', () => {
    it('calculates 1 + 2', () => {
      expect(sum(1, 2)).toBe(3);
    });

    it('calculates all numbers', () => {
      const array = [1, 2, 3, 4, 5];
      expect(sumOf(array)).toBe(15);
    });
  });
  ```
  
- TDD 
  - 테스트 케이스 자체가 코드의 이해를 도울 수 있음. 문서가 될 수 있음.
  
# 리액트 컴포넌트 테스트

- Enzyme
  - Airbnb가 밀고있고, 대중화된 테스팅 도구
  - 새로 시작하는 프로젝트에서 사용하기 좋다
  - 컴포넌트 인스턴스에 접근
  - state/props 확인
  - 메소드 직접 호출
  - 무거움, 복잡함, 기능이 엄청 많음

- react-testing-library
  - 렌더링 결과에 집중
  - DOM 기반 테스트
  - UI를 위한 테스트에 최적화
  - 컴포넌트 인스턴스에는 거의 접근 안함

- 둘 다 배워야 한다.
  - 이 강의는 react-testing-library 위주
  
- Hooks를 쓸 땐 shallow말고 mount를 사용하여야 한다. hooks의 기능이 제대로 작동하지 않음.

# React-testing-library

- 벨로퍼트님 의견에는 많이 좋다고 생각
- Variant
  - 앞 부분에 오는 것들을 선택
- Queries
  - 뒷 부분에 오는 것들을 선택

# 리덕스 / 비동기작업의 테스트
# 프로젝트에 CI/CD 도입하기
  
  
