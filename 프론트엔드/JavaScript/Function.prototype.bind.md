# Function.prototype.bind

<br/>

### Function.prototype.bind에 대해 설명하세요

this 바인딩은 함수 호출 방식에 따라 동적으로 결정되는데 일반 함수에서 호출하면 전역 객체, 메서드 호출시에는 메서드를 호출한 객체, 생성자 함수 호출인 경우에는 생성자 함수가 생성할 인스턴스가 this 바인딩 대상이 된다.  
Function.prototype.apply/call/bind의 경우에는 첫번째 인수로 전달한 객체가 this 바인딩 대상이 된다.

Function.prototype.bind는 this 키워드와 함께 함수를 호출할 때 함수 내에서 this가 참조하는 값을 변경한다.

```javascript
function getThisBinding() {
  return this;
}

//this로 사용할 객체
const thisArg = { a: 1 };

// bind 메서드는 첫 번째 인수로 전달한 thisArg로 this 바인딩이 교체된 getThisBinding 함수를 새롭게 생성해 반환한다.
console.log(getThisBinding.bind(thisArg)); // getThisBinding
// bind 메서드는 함수를 호출하지는 않으므로 명시적으로 호출해야 한다.
console.log(getThisBinding.bind(thisArg)()); // {a: 1}
```

bind 메서드는 메서드의 this와 메서드 내부의 중첩 함수 또는 콜백 함수의 this가 불일치하는 문제를 해결하기 위해 유용하게 사용된다.

```javascript
const person = {
  name: 'Lee',
  sayName() {
    console.log(`Hi, I'm ${this.name}`);
  },
};

person.sayName(); // Hi, I'm Lee

const sayNameNoBind = person.sayName;
sayNameNoBind(); // Hi, I'm undefined

// bind 메서드로 callback 함수 내부의 this 바인딩을 전달
const sayNameBind = person.sayName.bind(person);
sayNameBind(); // Hi, I'm Lee
```

sayNameNoBind를 통해 person.sayName이 일반 함수로서 호출된 시점에서 this는 전역 객체를 가리킨다.  
window.name을 가리키게 되어 undefined를 반환한다.  
콜백 내부 함수의 this를 외부 함수 내부의 this와 일치시켜주기 위해 bind 메서드를 사용하여 this를 일치시켜줄 수 있다.

<br/>

---
