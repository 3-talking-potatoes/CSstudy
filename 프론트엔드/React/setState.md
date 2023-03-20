# setState

<br/>

### 리액트에서 setState는 비동기 동작인가요 동기 동작인가요?⚡️

**비동기(Asynchronous)**  
비동기 : 순서가 아닌 이벤트에 따라 처리

참고하면 좋을 자료: [setState가 왜 비동기일까?](https://choonse.com/2022/01/21/677/), [리액트의 setState() 제대로 사용하기](https://www.youtube.com/watch?v=hSdVDBPTT0U), [React의 setState() 제대로 사용하기 - 블로그](https://leehwarang.github.io/2020/07/28/setState.html)

---

<br/>

### setState가 비동기 동작을 취했을 때 얻을 수 있는 이점은 무엇인가요?⚡️

setState는 이벤트 핸들러 내에서 비동기적  
부모 자식 모두 click 이벤트에서 setState 호출 시 자식이 2번 렌더링되지 않음
React는 브라우저 이벤트가 끝날 시점에 state를 **일괄적**으로 업데이트(Batch)
-> 불필요한 재렌더링 방지로 성능향상

출처 : [React-state](https://ko.reactjs.org/docs/faq-state.html)

---

<br/>
