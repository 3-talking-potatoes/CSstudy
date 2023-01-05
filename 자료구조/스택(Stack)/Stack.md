# 스택(Stack)

<br>

### 스택(Stack)

> 스택은 특정 순서대로 작업이 수행되는 자료구조이다. 스택은 마지막에 삽입된 요소가 먼저 나오는 LIFO(Last In First Out - 후입선출)전략을 따른다. 실생활의 예로 쌓여있는 접시 더미를 들 수 있다.

<br/>

![이미지](https://user-images.githubusercontent.com/93918946/210717509-fcf7fbe5-7561-434c-80bb-92fe3195e391.png)

<br/>

### 소개

스택은 데이터를 저장하는 데 사용되는 선형 자료구조이다. 후입선출 방식인 LIFO 전략을 따르며, 배열이나 연결 리스트 등을 통해 구현할 수 있다. 스택은 요소의 최상단에서만 접근할 수 있으므로, 스택을 구현하기 위해서는 최상단인 마지막에 삽입된 요소에 대한 포인터를 유지해야 한다.

스택의 기본 작업은 다음과 같다.

- push(): 스택에 요소를 삽입한다.
- pop(): 스택에서 요소를 제거한다.
- top(): 스택의 맨 위 요소를 반환한다.
- isEmpty(): 스택이 비어 있으면 true를 반환하고, 그렇지 않으면 false를 반환한다.
- size(): 스택의 크기를 반환한다.
- peek(): 스택의 맨 위 요소를 확인한다.

스택은 브라우저의 뒤로 가기, 앞으로 가기 기능을 구현할 때 활용된다.

<br/>

### 시간 복잡도

|   작업    | 시간 복잡도 |
| :-------: | :---------: |
|  push()   |    O(1)     |
|   pop()   |    O(1)     |
| isEmpty() |    O(1)     |
|  size()   |    O(1)     |

<br/>

## 코드 예시

**배열을 사용하여 스택 구현**

배열 구현의 장점

- 구현하기 쉽다.
- 포인터가 없기 때문에 메모리가 절약된다.

배열 구현의 단점

- 동적인 구현이 아니다. 실행 중에 요구 사항에 따라 크기가 커지고 작아지지 않는다.
- 스택의 전체 크기는 사전에 정의되어야 한다.

```javascript
// pointer
var top = array.length - 1;
var MAX = 1000;
var array = Array(MAX).fill(0); // Maximum size of Stack

// isEmpty()
function isEmpty() {
  return top < 0;
}

// push()
function push(x) {
  if (top >= MAX - 1) {
    // Stack Overflow 스택이 가득 찬 상태
    return false;
  } else {
    top += 1;
    array[top] = x;
    return true;
  }
}

// pop()
function pop() {
  if (top < 0) {
    // Stack Underflow 스택이 비어있는 상태
    return null;
  } else {
    let x = array[top];
    top -= 1;
    return x;
  }
}
```

<br/>

**배열을 사용한 스택 클래스의 예시**

```javascript
class Stack {
  constructor() {
    this.stack = [];
  }

  push(item) {
    this.stack.push(item);
  }

  pop() {
    return this.stack.pop();
  }

  peek() {
    return this.stack[this.stack.length - 1];
  }

  isEmpty() {
    return this.stack.length === 0;
  }
}
```

<br/>

**연결 리스트를 사용하여 스택 구현**

연결 리스트 구현의 장점

- 스택의 연결 리스트 구현은 실행 중에 요구 사항에 따라 크기가 커지고 작아질 수 있다.
- JVM과 같은 많은 가상 머신에서 사용된다.

연결 리스트 구현의 단점

- 포인터의 참여로 추가 메모리가 필요하다.
- 랜덤 액세스가 불가능하다.

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.next = null;
  }
}

class Stack {
  constructor() {
    this.top = null;
  }

  push(value) {
    const node = new Node(value);
    node.next = this.top;
    this.top = node;
  }

  pop() {
    if (this.isEmpty()) {
      return null;
    }

    const node = this.top;
    this.top = this.top.next;
    return node.value;
  }

  peek() {
    if (this.isEmpty()) {
      return null;
    }

    return this.top.value;
  }

  isEmpty() {
    return this.top === null;
  }
}

const stack = new Stack();
stack.push(1);
stack.push(2);
stack.push(3);

console.log(stack.peek()); // Output: 3
console.log(stack.pop()); // Output: 3
console.log(stack.isEmpty()); // Output: false
```

<br/>

---

참고 문서 :  
https://www.geeksforgeeks.org/introduction-to-stack-data-structure-and-algorithm-tutorials/  
https://www.geeksforgeeks.org/applications-advantages-and-disadvantages-of-stack/  
https://www.geeksforgeeks.org/implementation-stack-javascript/
