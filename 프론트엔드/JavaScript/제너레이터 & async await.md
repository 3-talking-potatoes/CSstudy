# 제너레이터와 async await⚡️

<br/>

### 제너레이터란 뭔가요? 일반 함수와는 어떤 차이가 있나요?

> ES6에서 도입. 코드 블록의 실행을 일시 중지했다 필요한 시점에 재개할 수 있는 특수 함수

- yield 키워드와 next 메서드를 통해 실행을 일시 중지 했다 필요한 시점에 다시 재개할 수 있다.

> 제너레이터와 일반 함수와의 차이

1. 제너레이터 함수는 함수 호출자에게 함수 실행의 제어권을 넘길 수 있다
2. 제너레이터 함수는 함수 호출자와 함수 상태를 주고 받을 수 있다.
3. 제너레이터 함수를 호출하면 제너레이터 객체를 반환

|                              |      제너레이터      |    일반함수    |
| ---------------------------- | :------------------: | :------------: |
| 함수 실행 제어권 양도        |          O           |       X        |
| 함수 호출자와 함수 상태 교환 |          O           |       X        |
| 함수 호출 시                 | 제너레이터 객체 반환 | 함수 코드 실행 |

---

<br/>

### 제너레이터의 구조

> function\* 키워드 + 하나 이상의 yield 표현식

```js
function* genFunc() {
  yield 1;
}

// *(애스터리스크) : function 키워드와 함수 이름 사이, function키워드 바로 뒤에 붙이는 걸 권장
```

> 제너레이터 함수 호출 시 제너레이터 객체 생성 반환

- 제너레이터 객체는 이터러블이면서 이터레이터
- 제너레이터 객체는 next 메서드를 갖는 이터레이이터, return, throw 메서드도 가지고 있다.
- 제너레이터 객체는 value, done 프로퍼티를 갖는 이터레이터 객체 반환, next 메서드를 가지고 있는 이터레이터

```js
function* genFunC() {
  yield 1;
  yield 2;
  yield 3;
}

const generator = genFunC();

console.log(generator.next()); // {value : 1, done : false}
```

---

<br/>

### async/await 가 뭔가요?⚡️

> ES8에서 나온 async await를 사용하면 비동기 처리를 동기처럼 동작할 수 있도록 구현할 수 있다.

- async 함수는 언제나 프로미스를 반환
- async 키워드를 사용해 정의, await 키워드는 반드시 async 함수 내부에서 사용
- await 키워드는 프로미스가 settled 상태가 될 때까지 대기, settled 상태가 되면 프로미스가 resolve한 결과를 반환
- await 키워드는 반드시 프로미스 앞에 사용
- error 처리 시 try...catch문을 사용해 에러 캐치 가능

```js
async function foo() => {
    const response = await fetch('...');
    const result = await response.json();

    return result // 프로미스 객체 반환
}

foo()
.then(res => console.log(res));
.catch(console.error);

```

---

<br/>

### Promise와 async/await의 차이점을 짧게 설명해주세요⚡️

> 기존 Promise와 차이

1. 프로미스의 then/catch/finally 후속 처리 메서드에 콜백 함수를 전달해서 비동기 처리 결과를 후속 처리 할 필요가 없다.
   - async/await 활용 시 가독성이 좋다.
2. 디버그 시 Promise는 어떤 then에서 문제가 생겼는지 알기 어렵지만 async/await는 어떤 지점에서 에러가 생겼는지 알기 쉽다.
3. async/await는 try...catch로 에러 처리가 가능하다.

[참고하면 좋을 사이트](https://dkrnfls.tistory.com/362)

---

<br/>

출처 : 모던 자바스크립트 Deep Dive, https://dkrnfls.tistory.com/362
