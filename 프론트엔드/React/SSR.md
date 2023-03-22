# SSR

<br/>

### SSR이 뭔가요?⚡️

> SSR이란

SSR(server-side rendering)  
서버에서 사용자에게 보여줄 페이지를 모두 구성하여 사용자에게 페이지를 보여주는 방식

> SSR 단계

1. 서버에서 렌더링 가능한 html 파일 만들어 클라이언트에 전달
2. 브라우저에서 렌더링 해서 페이지 보임, 브라우저 js 다운로드중(화면은 보이지만 상호작용 불가능)
3. 브라우저에서 js 프레임워크 실행
4. js까지 컴파일 되면 상호작용 가능

![ssr](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*jJkEQpgZ8waQ5P-W5lhxuQ.png)
![csr](https://miro.medium.com/v2/resize:fit:1400/format:webp/1*CRiH0hUGoS3aoZaIY4H2yg.png)

출처 : [The Benefits of Server Side Rendering Over Client Side Rendering](https://medium.com/walmartglobaltech/the-benefits-of-server-side-rendering-over-client-side-rendering-5d07ff2cefe8)

> SSR의 장점

- 모든 데이터가 매핑된 서비스 페이지를 브라우저에게 바로 보여줄 수 있다.
- CSR보다 페이지 구성 속도는 느리지만 사용자에게 보여주는 콘텐츠 구성이 완료되는 시점은 빠르다(첫 페이지 로딩 시간이 빠르다)
- SEO(search engine optimization)에 유리하다.

> SSR의 단점

- 화면 깜빡임 현상이 있다.(blinking issue)
- 서버 과부화가 걸리기 쉽다.
- 페이지 이동 속도가 CSR에 비해 느리다
- 화면은 확인되지만 js다운로드가 느려진다면 기능동작이 되지 않아 혼란을 야기할 수 있다.
- 중복되는 컴포넌트도 다시 렌더링하여 받는다.

---

<br/>

### TTV, TTI

웹 사이트 성능 분석 시 중요한 방법으로 사용될 수 있다.

> TTV(Time To View)

사용자가 웹브라우저에서 내용을 볼 수 있는 시점

> TTI(Time To Interact)

사용자가 웹브라우저에서 상호작용할 수 있는 시점

> CSR과 SSR에서 TTV, TTI

- CSR : TTV와 TTI의 시점이 같다.
- SSR : TTV와 TTI의 시점이 다르다.

---

<br/>

출처 : [d2- ssr 도입편](https://d2.naver.com/helloworld/7804182), [CSR과 SSR의 차이점](https://story.pxd.co.kr/1662)

참고하면 좋은 자료 : [드림코딩-서버사이드 렌더링](https://www.youtube.com/watch?v=iZ9csAfU5Os)

<br/>
