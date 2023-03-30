# useLayoutEffect

<br/>

### useLayoutEffect는 무엇인가요?⚡️

useLayoutEffect은 useEffect와 유사하게 작동하지만 실행되는 시점이 다르다.
useEffect는 렌더링 된 이후에 동작하는 hook이고 useLayoutEffect는 렌더링 되기 이전에 동작하는 hook이다.
그렇기 때문에 useEffect 사용 시 렌더링 이후 DOM에 영향을 주는 코드를 호출하면 해당 부분이 적용되며 화면에 깜빡임이 발생할 수 있다.  
이 때, useLayoutEffect를 사용하면 렌더링 되기 이전에 실행되어 화면 깜빡임 없이 부드러운 사용자 경험을 제공할 수 있다.

단점으로는, useLayoutEffect를 사용하는 컴포넌트의 렌더링 시간이 오래 걸릴 경우, 화면 전환 효과나 스크롤링 등의 브라우저의 다른 기능이 지연될 수 있다. 따라서 성능 이슈가 발생할 가능성이 있는 경우에는 useEffect를 사용하는 것이 좋다.

<br/>

---
