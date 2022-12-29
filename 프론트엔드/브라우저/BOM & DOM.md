# BOM과 DOM

<br/>

### BOM과 DOM에 대해 설명해주세요

> BOM(Browser Object Model)

브라우저의 창이나 프레임을 프로그래밍적으로 제어할 수 있게 해주는 객체 모델  
이를 통해 브라우저의 새 창 열기, 다른 문서 이동 등의 기능 실행 가능, 브라우저 알림창 띄우기, AJAX요청  
전역 객체로 window가 있고 하위 객체로 location, navigator, document, screen, history가 있다.

> DOM(Document Object Model, 문서 객체 구조)

window.document 객체를 DOM이라 분류  
HTML을 브라우저에서 파싱한 후 돔트리를 만드는데 요소 하나하나를 Node라 함 상속의 최상위에는 EventTarget  
웹 페이지를 프로그래밍적으로 제어할 수 있게 해주는 객체모델.  
최상위 인터페이스로 Node가 있고 트리 구조로 되어 있다.

- 브라우저 API에서 제공하는 모든 것 BOM + DOM을 Web API라 부름  
  자바스크립트의 기능은 아니지만 자바스크립트로 제어될 수 있도록 함.

<br/>
