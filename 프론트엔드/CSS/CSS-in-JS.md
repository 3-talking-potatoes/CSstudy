# CSS-in-JS

<br/>

### CSS-in-JS에 대해서 설명해주세요⚡️

> CSS-in-JS

JavaScript 코드에서 CSS를 작성하는 방식, 2014에 처음 나오게 되었다.

- Global namespace: 글로벌 공간에 선언된 이름의 명명 규칙 필요
- Dependencies: CSS 간의 의존 관계 관리
- Dead Code Elimination: 미사용 코드 검출
- Minification: 클래스 이름 최소화
- Sharing Constants: JS와 CSS의 상태 공유
- Non-deterministic Resolution: CSS 로드 우선 순위 이슈
- Isolation: CSS와 JS의 상속에 따른 격리 필요 이슈  
  등의 문제를 해결하기 위해 등장하였고 예시로 styled-components, emotion의 라이브러리가 있다.

장점 : CSS 파일 유지보수가 필요 없음, 컴포넌트 레벨로 추상화가 가능해 단일 파일에서 관리 가능, JS 코드 활용 가능, 해당 DOM에서만 활용할 수 있는 것, 스타일링을 위한 코드 사용량이 줄어듦

단점 : 러닝커브가 높다, 라이브러리 용량, CSS 모듈 방식에 느린 성능
