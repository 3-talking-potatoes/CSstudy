# const & let & var⚡️⚡️⚡️⚡️

<br/>

### var 키워드는 뭔가요?

> var

변수를 선언할 때 사용하는 키워드  
var 키워드를 사용한 변수 선언은 선언 단계와 초기화 단계가 동시에 진행되고, 초기화 단계에서 undefined를 할당한다.

- 키워드(keyword) : 자바스크립트 엔진이 수행할 동작을 규정한 일종의 명령어. 자바스크립트 엔진은 키워드를 만나면 자신이 수행해야할 동작을 수행

- 초기화(initialization) : 변수가 선언된 이후 최초로 값을 할당하는 것

- 자바스크립트 엔진의 변수 선언
  1. 선언 단계 : 변수 이름을 등록, 자바스크립트 엔진에 변수의 존재를 알림
  2. 초기화 단계 : 값을 저장하기 위한 메모리 공간 확보, 암묵적으로 undefined를 할당해 초기화
  - 초기화 단계를 거치지 않으면 확보된 메모리 공간에 값이 남아 있는 경우가 있음 이를 쓰레기 값(garbage value)라 한다.

---

<br/>

### var 키워드의 문제점은 무엇이 있나요?⚡️⚡️

> var 키워드의 문제점

1. 함수 레벨 스코프(function-level-scope)지원 : 전역 변수의 역할로 사용되게 됨

```js
for (var i = 0; i < 5; i++) {
  console.log(i);
}

console.log(i); // 5
```

2. 변수의 중복 선언 허용

```js
var foo = 1;
var foo = 2;
```

3. 변수 호이스팅

```js
console.log(foo); //undefined
var foo = 2;
```

---

<br/>

### let 키워드는 var 키워드와 어떤 점이 다른가요?⚡️⚡️⚡️

> let vs var

|           |                                        let                                         |                   var                   |
| :-------- | :--------------------------------------------------------------------------------: | :-------------------------------------: |
| 중복 선언 |                                         x                                          |                    o                    |
| 재할당    |                                         o                                          |                    o                    |
| 스코프    |                        블록 레벨 스코프 (block level scope)                        | 함수 레벨 스코프 (function level scope) |
| 호이스팅  | 선언과 초기화 단계 **분리** (초기화 단계가 실행되지 않을 때 변수 접근 시 참조에러) |         선언과 초기화 단계 동시         |

- 함수 레벨 스코프 : 함수의 코드 블록만을 지역 스코프로 인정
- 블록 레벨 스코프 : 모든 코드 블록(함수, if 문, for 문, while 문, try/catch 문)을 지역 스코프로 인정

- let은 호이스팅이 발생하지 않는가? No 호이스팅이 발생하나 발생하지 않는 것처럼 동작 TDZ 참조

---

<br/>

### TDZ⚡️⚡️⚡️

> 일시적 사각지대 TDZ(Temporal Dead Zone)⚡️⚡️⚡️

스코프 시작 지점부터 초기화 시작 지점까지 변수를 참조할 수 없는 구간을 의미

let 키워드는 선언과 초기화 단계가 분리돼서 진행되는데 자바스크립트 엔진에 의해 선언 단계가 먼저 진행되나 초기화 단계는 변수 선언문에 도달했을 때 실행된다. 이 사이의 간격동안 변수를 참조할 수 없는데 이것을 일시적 사각지대(TDZ)라고 한다.

- let의 호이스팅

```js
let potatoes = 3; // 전역 변수

{
  console.log(potatoes); // ReferenceError: Cannot access 'potatoes' before initialization
  let potatoes = 100; // 지역 변수
}
```

호이스팅이 되지 않는다면 `console.log(potatoes)`가 오류 없이 3으로 나와야하나 참조에러가 발생한다(호이스팅이 된다).

---

<br/>

### const 키워드는 어떤 특징이 있나요?⚡️⚡️

> const 특징

1. 선언과 초기화를 반드시 동시에 한다.

```js
const potatoes = 3; // o

const potato // SyntaxError : Missing initializer in const declaration

```

2. 재할당 금지  
   const 키워드로 선언한 변수는 재할당이 금지된다.

```js
const foo = 1;
foo = 2; // TypeError: Assignment to constant variable

// 객체의 경우

const potatoes = {
  potato: 0,
};

potatoes.potato = 3; // 가능 객체의 주소 값을 변경한 건 아니기 때문
```

3. 블록 레벨 스코프를 가진다.
