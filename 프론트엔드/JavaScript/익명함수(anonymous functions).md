# 익명함수(anonymous functions)

<br/>

### 일반함수와 익명함수의 차이

<br/>

#### 1. 일반함수

일반함수는 function 키워드를 사용하여 정의된 함수이다.

```
function 함수명 () {
    함수 로직
}

function sayHi(){
    console.log("hi")
}

sayHi() // "hi"
```

일반 함수는 호이스팅이 가능하다.

```
sayHi() // "hi"

function sayHi(){
    console.log("hi")
}

sayHi() // "hi"

// 호이스팅 적용

// function sayHi(){
//    console.log("hi")
// }

// sayHi() // "hi"

```

#### 1. 익명함수

익명함수는 말 그대로 이름이 없는 함수이다. 따로 함수의 이름을 갖지 않는 대신에 변수에 함수를 할당한다 (함수의 이름 !== 변수명). 주로 재사용하지 않고 한번만 사용할 때 사용된다.

```
const sayHi = function(){
    console.log("hi")
}

sayHi() // "hi"
```

익명함수는 호이스팅이 불가능하다. 함수를 담는 변수의 선언부만 호이스팅 되고, 익명 함수 자체는 변수가 호출되었을 때 실행되기 때문에, 선언부가 호출 위치보다 위에 있어야 한다.

```
sayHi(); // Uncaught ReferenceError: Cannot access 'sayHello' before initialization

const sayHi = function() {
  console.log("hi");
}

sayHi(); // 위에서 에러가 났으니 출력이 나오지 않음
```

```
// 호이스팅

const sayHi

sayHi()

sayHi = function(){
    console.log("hi")
}

sayHi()
```

<br/>

---

### 익명함수(anonymous functions)는 주로 어떤 상황에서 사용하나요?

<br/>

익명함수는 메모리 관리에 효과적인 방안이 될 수 있다.

일반 함수는 자바스크립트를 초기에 읽어올 때 모두 호이스팅된다. 만약, 전체 자바스크립트 내에서 단 한번만 쓰이는 함수가 일반 함수로 구현된다면 함수가 호출될 때가지 불필요하게 메모리를 차지하고 있는다. 메모리 사용량이 성능에 중요한 영향을 미칠 수 있는 웹 애플리케이션에서, 이는 메모리 낭비라고 볼 수 있다.

따라서 단 한번만 사용되는(재사용이 필요없는) 함수가 익명함수로 구현된다면 불필요한 메모리 낭비를 방지할 수 있다.
