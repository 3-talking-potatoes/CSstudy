# Virtual DOM

<br/>

### Virtual DOM에 대해서 아나요?⚡️⚡️

> Virtual DOM(VDOM)

Virtual DOM은 실제 DOM의 구조와 비슷한 트리 구조를 갖는 객체이다.

> Virtual DOM의 장점

DOM에 변화가 생기면 렌더트리를 재생성하고 모든 요소의 스타일이 다시 계산 되며, 레이아웃을 만들고 페인팅 하는 과정이 반복된다.

복잡한 SPA에서는 DOM 조작이 많이 발생하는데 이는 변화를 위해 브라우저가 연산을 많이 한다는 의미로 비효율적 프로세스가 이뤄진다.

virtual DOM은 실제 DOM에 변화가 적용되기 전에 virtual DOM에 적용시킨 다음 최종 결과를 실제 DOM에 전달하여 브라우저 내에 발생하는 연산의 양을 줄여 성능을 개선 시킬 수 있다.

virtual DOM에서의 연산은 렌더링이 되는게 아니기 때문에 비용이 적다. 연산이 완료된 최종적인 변화를 실제 DOM에 전달하면 레이아웃 계산과 리렌더링 규모는 커질지 몰라도 딱 한 번의 연산으로 바꿀 수 있다는 점에서 연산의 횟수를 줄였다 할 수 있다.

virtual DOM이 없어도 DOM fragment를 관리할 수도 있지만 virtual DOM을 사용하면 수동으로 작업할 필요없이 자동화와 추상화가 이뤄지므로 생산성을 높일 수 있다.

출처: [React-virtual DOM](https://ko.reactjs.org/docs/faq-internals.html#what-is-the-virtual-dom),[velopert-virtual DOM](https://velopert.com/3236)

참고하면 좋은 자료 : [D2-virtual DOM](https://d2.naver.com/helloworld/9297403)

---

<br/>
