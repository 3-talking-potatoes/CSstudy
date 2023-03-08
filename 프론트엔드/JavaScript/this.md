# this⚡️

<br/>

### this가 뭔가요?⚡️

> 자신이 속한 객체 또는 자신이 생성할 인스턴스를 가리키는 자기 참조 변수(self-referencing variable)

this를 통해 자신이 속한 객체 또는 자신이 생성할 인스턴스의 프로퍼티나 메서드를 참조할 수 있다.

객체 리터럴에서는 this 없이 재귀적으로 선언된 변수를 참조할 수 있지만 생성자 함수에서는 자신이 생성할 인스턴스를 가리키는 식별자를 알 수 없다.  
자기 자신이 속한 객체를 재귀적으로 참조하는 방식은 바람직 하지 않다.

```js
// 1. 객체 리터럴 방식 (재귀적 참조)
// 객체 리터럴은 potato 변수에 할당되기 전 평가가 이루어진다 -> 참조 가능

const potato = {
    color:'red',
    getPotatoColor(){
        return `${potato.color} 감자`
    }
}

console.log(potato.getPotatoColor()); // 'red 감자'

// 2. 생성자 함수 방식 (this가 없다면)

function Potato(color){
    ???.color = color;
}

Potato.prototype.getPotatoColor = function(){
    return `${???.color} 감자`;
}

const redPotato = new Potato('red');

// 2. 생성자 함수 방식 (this가 있다면)

function Potato(color){
    this.color = color;
}

Potato.prototype.getPotatoColor = function(){
    return `${this.color} 감자`;
}

const redPotato = new Potato('red');
console.log(redPotato.getPotatoColor()); // 'red 감자'


```

---

<br/>

### this 바인딩이란?⚡️

> this와 this가 가리킬 객체를 바인딩하는 것

- 바인딩 : 식별자와 값을 연결하는 과정을 의미
- this는 키워드로 분류되지만 식별자 역할을 한다

---

<br/>

### this는 동적으로 바인딩이 된다고 하는데 바인딩되는 객체가 어떻게 다르나요?

> this 바인딩은 함수 호출 방식에 의해 동적으로 결정된다

| 함수 호출 방식                                             | this 바인딩                                                           |
| ---------------------------------------------------------- | --------------------------------------------------------------------- |
| 일반 함수 호출                                             | 전역 객체                                                             |
| 메서드 호출                                                | 메서드를 호출한 객체                                                  |
| 생성자 함수 호출                                           | 생성자 함수가(미래에) 생성할 인스턴스                                 |
| Function.prototype.apply/call/bind 메서드에 의한 간접 호출 | Function.prototype.apply/call/bind 메서드에 첫번째 인수로 전달한 객체 |

> 일반 함수 호출

기본적으로 this에 전역 객체가 바인딩된다.

```js
function potato() {
  console.log(this); // window
}
// strict mode
function potato() {
  "use strict";

  console.log(this); // undefined
}
// 메서드 내에서 중첩함수를 일반 함수로 호출 시에도 전역 객체 바인딩
var value = 3;

const object = {
  value: 100,
  foo() {
    console.log(this); // {value: 100, foo: f}

    function potato() {
      console.log(this); // window
      console.log(this.value); // 1
    }
  },
};
```

콜백 함수도 일반 함수로 호출된다면 콜백 함수 내부의 this도 전역 객체 바인딩

- 일반 함수로 호출된 모든 함수 내부의 this에는 전역 객체가 바인딩
- 외부 함수 메서드의 중첩 함수, 콜백 함수는 대부분 헬퍼 함수인데 this가 일치하지 않는다면 함수 이해가 어려워진다.

✨ 메서드 내부의 중첩 함수나 콜백 함수의 this 바인딩을 메서드의 this 바인딩과 일치시키기 위한 방법

1️⃣ 변수에 this 할당

```js
const object = {
  value: 100,
  foo() {
    const that = this;

    setTimeout(function () {
      console.log(that.value); // 100
    }, 100);
  },
};
```

2️⃣ this를 명시적으로 바인딩할 수 있는 Function.prototype.apply/call/bind 메서드 이용

3️⃣ 화살표 함수 이용 : 화살표 함수 내부의 this는 상위 스코프의 this를 가리키기 때문

> 메서드 호출

- 메서드 내부의 this는 메서드를 호출한 객체에 바인딩
- 메서드를 소유한 객체가 아닌 **메서드를 호출한 객체**에 바인딩!!

```js
const potato = {
    name='Choi',
    getName(){
        return `감자 ${this.name}`;
    }
}
```

getName 프로퍼티가 가리키는 함수 객체는 potato에 포함된 게 아닌 독립적으로 존재하는 별도의 객체 getName 프로퍼티가 함수 객체를 가리키고 있을 뿐

- 프로토타입 메서드 내부에서 사용된 this도 일반 메서드와 마찬가지로 해당 메서드를 호출한 객체에 바인딩

> 생성자 함수 호출

생성자 함수 내부의 this는 생성자 함수가 미래에 생성할 인스턴스가 바인딩된다.

```js
function Potato(color) {
  this.color = color;
  this.getColor = function () {
    return `${this.color} 감자`;
  };
}

const redPotato = new Potato("red");

console.log(redPotato.getColor()); // 'red 감자'
```

- new 연산자와 함께 생성자 함수를 호출하지 않으면 일반 함수로 동작한다.

> Function.prototype.apply/call/bind 메서드에 의한 간접 호출

apply, call, bind 메서드는 Function.prototype의 메서드라 모든 함수가 상속 받아 사용할 수 있다.

첫번째 인수로 전달한 객체에 this가 바인딩 된다.

---

<br/>

출처 : 모던 자바스크립트 Deep Dive
