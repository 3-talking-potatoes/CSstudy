# CORS ⚡️⚡️⚡️

<br/>

### CORS가 무엇이며 어떻게 해결할 수 있는지 설명해주세요 ⚡️⚡️⚡️

> CORS(Cross-Origin Resource Sharing)

CORS는 Cross-Origin Resource Sharing의 줄임말로
다른 출처의 리소스 공유에 대한 허용/비허용 정책을 뜻한다.

CORS 정책을 지킨 리소스 요청은 SOP 정책의 예외 사항에 들어가 다른 출처의 리소스 공유가 가능하다.

CORS 오류를 해결하는 방법으로는

1. 서버에서 Access-Control-Allow-Origin 헤더에 알맞은 값 세팅
2. 프록시를 사용하여 우회하기
3. 크롬 확장 프로그램 설치

---

<br/>

### JavaScript와 관련하여 same-origin 정책을 설명하세요.⚡️⚡️

> SOP(Same-Origin Policy)

SOP(Same Origin Policy)는 동일한 출처에서만 리소스를 공유할 수 있다는 정책이다.

동일한 출처 서버에 있는 리소스는 자유롭게 가져올 수 있지만 다른 출처에 있는 리소스는 상호작용이 불가하다는 웹 브라우저에 적용되는 정책이다.

- 필요한 이유 : 제약이 없다면 해커가 CSRF(Cross-Site Request Forgery)나 XSS(Cross-Site Scripting)의 방법으로 개인 정보 탈취가 일어날 수 있다.

---

<br/>

### 💫 동일한 출처란 무엇인가요?

> 동일한 출처

출처(Origin) = Protocol(Scheme) + Host + 포트번호

ex) https://localhost:3000

URL의 속성 중 출처에 해당되는 3가지 속성 모두 일치해야 동일한 출처라 할 수 있다.

---

<br/>

### 💫 CORS 기본동작을 알고 있나요?

> CORS 기본동작

1. 클라이언트에서 HTTP요청의 헤더에 Origin을 담아서 전달
2. 서버 응답헤더에 Access-Control-Allow-Origin을 담아 클라이언트로 전달
3. 클라이언트에서 자신이 보냈던 요청의 Origin과 서버가 보내준 Access-Control-Allow-Origin을 비교

---

<br/>

### 💫 CORS의 작동 방식 3가지를 설명하세요

> 예비요청(Preflight Request), 단순 요청(Simple Request), 인증된 요청(Credentialed Request)

1. 예비요청(Preflight Request)  
   브라우저에서 요청 시 예비 요청을 보내고 본 요청을 보내는 방법. 이 때 브라우저가 예비요청을 보내는 것을 Preflight라고 부르며 HTTP 메소드로 OPTIONS이 사용된다.

2. 단순 요청(Simple Request)  
   예비 요청을 생략하고 서버로 바로 본 요청을 보내는 방법. 서버가 응답 헤더로 Access-Control-Allow-Origin 헤더를 보내주면 브라우저에서 CORS정책 위반 여부 검사하는 방식. 특정 조건을 만족하는 경우에만 예비 요청 생략 가능

3. 인증된 요청(Credentialed Request)  
   클라이언트에서 서버로 Credential(자격 인증 정보)를 실어 요청할 때 사용  
   Credential : 세션 ID가 저장된 쿠키, Authorization 헤더에 설정하는 토큰 등등  
   이 때 서버에서 응답 헤더의 Access-Control-Allow-Origin 값에 와일드카드 문자를 사용할 수 없으며, Access-Control-Allow-Credentials 항목을 true로 설정해줘야 한다.
