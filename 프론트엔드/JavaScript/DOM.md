# DOM⚡️

<br/>

### DOM이 뭔가요?

DOM은 HTML 문서의 계층적 구조와 정보를 표현하며 이를 제어할 수 있는 API, 즉 프로퍼티와 메서드를 제공하는 트리 자료구조다.

<br/>

---

### DOM을 구성하는 건 뭐가 있나요?

HTML 요소는 렌더링 엔진에 의해 파싱되어 DOM을 구성하는 요소 노드 객체로 변환된다.  
이때 HTML 요소의 어트리뷰트는 어트리뷰트 노드로, HTML 요소의 텍스트 콘텐츠는 텍스트 노드로 변환된다.

노드 객체들로 구성된 트리 자료구조를 DOM(Document Object Model)이라 한다.  
노드 객체의 트리로 구조화되어 있기 때문에 DOM을 DOM 트리라고 부르기도 한다.

DOM은 노드 객체의 계층적인 구조로 구성된다. 노드 객체는 종류가 있고 상속 구조를 갖는다.  
노드 객체는 총 12개의 종류(노드 타입)가 있다. 이 중에서 중요한 노드 타입은 다음과 같이 4가지다.

1. 문서 노드
2. 요소 노드
3. 어트리뷰트 노드
4. 텍스트 노드

- 문서 노드

  ```javascript
  <!DOCTYPE>
  ```

  문서 노드는 DOM 트리의 최상위에 존재하는 루트 노드로서 document 객체를 가리킨다.  
  document 객체는 브라우저가 렌더링한 HTML 문서 전체를 가리키는 객체로서 전역 객체 window의 document 프로퍼티에 바인딩되어 있다. 따라서 문서 노드는 window.document 또는 document로 참조할 수 있다.  
  브라우저 환경의 모든 자바스크립트 코드는 script 태그에 의해 분리되어 있어도 하나의 전역 객체 window를 공유한다.  
  따라서 모든 자바스크립트 코드는 전역 객체 window의 document 프로퍼티에 바인딩되어 있는 하나의 document 객체를 바라본다. 즉, HTML 문서당 document 객체는 유일하다.

- 요소 노드

  ```javascript
  <html> <head> <meta> <link> <body> <ul> <li> <script>
  ```

  요소 노드는 HTML 요소를 가리키는 객체다.  
  요소 노드는 HTML 요소 간의 중첩에 의해 부자 관계를 가지며, 이 부자 관계를 통해 정보를 구조화한다.  
  따라서 요소 노드는 문서의 구조를 표현한다고 할 수 있다.

- 어트리뷰트 노드

  ```javascript
  charset = 'UTF-8';

  rel = 'stylesheet';

  href = 'style.css';
  ```

  어트리뷰트 노드는 HTML 요소의 어트리뷰트를 가리키는 객체다. 어트리뷰트 노드는 어트리뷰트가 지정된 HTML 요소의 요소 노드와 연결되어 있다.  
  단, 요소 노드는 부모 노드와 연결되어 있지만 어트리뷰트 노드는 부모 노드와 연결되어 있지 않고 요소 노드에만 연결되어 있다.  
  따라서 어트리뷰트 노드에 접근하여 어트리뷰트를 참조하거나 변경하려면 먼저 요소 노드에 접근해야 한다.

- 텍스트 노드

  ```javascript
  Apple;
  Banana;
  Orange;
  ```

  텍스트 노드는 HTML 요소의 텍스트를 가리키는 객체다.  
   요소 노드가 문서의 구조를 표현한다면 텍스트 노드는 문서의 정보를 표현한다고 볼 수 있다.  
   텍스트 노드는 요소 노드의 자식 노드이며, 자식 노드를 가질 수 없는 리프 노드다.  
   즉, 텍스트 노드는 DOM 트리의 최종단이다.

<br/>

---
