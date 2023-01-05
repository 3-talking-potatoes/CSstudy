# 큐(Queue)

<br>

### 큐(Queue)

> 큐는 양쪽 끝이 열려 있고 작업이 FIFO(First In First Out - 선입선출)전략을 사용하는 선형 자료구조이다. 큐는 모든 추가가 한쪽 끝에서 이루어지고, 모든 삭제가 다른 한쪽 끝에서 이루어진다.

<br/>

![이미지](https://user-images.githubusercontent.com/93918946/210717589-485f369f-5a71-4181-9751-1f6c3743a37d.png)

<br/>

### 소개

큐(Queue)는 대기열이라는 뜻을 가지고 있다. 스택과 반대되는 개념으로, 먼저 들어간 데이터(data)가 먼저 나오는 FIFO(First In First Out)를 특징으로 가지고 있다. 큐는 주로 데이터가 입력된 순서대로 처리할 때 사용한다. 큐는 입력과 출력의 방향이 고정되어 있으며, 두 곳으로 접근이 가능하다. 스택과의 차이점은 제거에 있다. 스택은 가장 최근에 추가된 항목을 제거하고, 큐는 가장 먼저 추가된 항목을 제거한다.

큐의 기본 작업은 다음과 같다.

- enqueue(): 큐의 끝(뒤)에 요소를 삽입한다.
- dequeue(): 큐의 앞쪽 끝에 있는 요소를 제거하고 반환한다.
- front(): 요소를 제거하지 않고 큐의 앞쪽 끝에 있는 요소를 반환한다.
- rear(): 요소를 제거하지 않고 큐의 뒤쪽 끝에 있는 요소를 반환한다.
- isEmpty(): 큐가 비어 있는지 확인한다.
- isFull(): 큐가 가득 차 있는지 확인한다.
- size(): 큐의 크기, 즉 큐에 포함된 요소의 수를 반환한다.

스택은 브라우저의 뒤로 가기, 앞으로 가기 기능을 구현할 때 활용된다.

<br/>

### 시간 복잡도

|   작업    | 시간 복잡도 |
| :-------: | :---------: |
| enqueue() |    O(1)     |
| dequeue() |    O(1)     |
|  front()  |    O(1)     |
|  rear()   |    O(1)     |
| isEmpty() |    O(1)     |
| isFull()  |    O(1)     |

<br/>

## 코드 예시

**배열을 사용하여 큐 구현**

```javascript
class Queue {
  constructor(size) {
    this.queue = new Array(size);
    this.front = -1;
    this.rear = -1;
  }

  enqueue(item) {
    // 큐가 가득 찼는지 확인
    if (this.rear === this.queue.length - 1) {
      console.log('Queue is full');
      return;
    }

    this.queue[++this.rear] = item;
  }

  dequeue() {
    // 큐가 비어있는지 확인
    if (this.front === this.rear) {
      console.log('Queue is empty');
      return;
    }

    return this.queue[++this.front];
  }

  front() {
    // 큐가 비어있는지 확인
    if (this.front === this.rear) {
      console.log('Queue is empty');
      return;
    }

    return this.queue[this.front + 1];
  }

  rear() {
    // 큐가 비어있는지 확인
    if (this.front === this.rear) {
      console.log('Queue is empty');
      return;
    }

    return this.queue[this.rear];
  }

  isEmpty() {
    return this.front === this.rear;
  }
}

const queue = new Queue(3);
queue.enqueue(1);
queue.enqueue(2);
queue.enqueue(3);

console.log(queue.dequeue()); // Output: 1
console.log(queue.dequeue()); // Output: 2
console.log(queue.dequeue()); // Output: 3
```

<br/>

**객체를 사용한 큐 클래스의 예시**

```javascript
class Queue {
  constructor() {
    this.queue = {};
    this.head = 0;
    this.tail = 0;
  }

  enqueue(item) {
    this.queue[this.tail] = item;
    this.tail++;
  }

  dequeue() {
    if (this.head === this.tail) {
      console.log('Queue is empty');
      return;
    }

    const item = this.queue[this.head];
    delete this.queue[this.head];
    this.head++;

    return item;
  }

  front() {
    if (this.head === this.tail) {
      console.log('Queue is empty');
      return;
    }

    return this.queue[this.head];
  }

  rear() {
    if (this.head === this.tail) {
      console.log('Queue is empty');
      return;
    }

    return this.queue[this.tail - 1];
  }

  isEmpty() {
    return this.head === this.tail;
  }
}
```

<br/>

**연결 리스트를 사용하여 큐 구현**

```javascript
class Node {
  constructor(data) {
    this.data = data;
    this.next = null;
  }
}

class Queue {
  constructor() {
    this.front = null;
    this.rear = null;
  }

  enqueue(item) {
    const node = new Node(item);

    if (this.rear) {
      this.rear.next = node;
    }

    this.rear = node;

    if (!this.front) {
      this.front = node;
    }
  }

  dequeue() {
    if (!this.front) {
      console.log('Queue is empty');
      return;
    }

    const item = this.front.data;
    this.front = this.front.next;

    if (!this.front) {
      this.rear = null;
    }

    return item;
  }

  front() {
    if (!this.front) {
      console.log('Queue is empty');
      return;
    }

    return this.front.data;
  }

  rear() {
    if (!this.rear) {
      console.log('Queue is empty');
      return;
    }

    return this.rear.data;
  }

  isEmpty() {
    return !this.front;
  }
}
```

<br/>

---

참고 문서 :  
https://www.geeksforgeeks.org/introduction-to-queue-data-structure-and-algorithm-tutorials/
https://www.geeksforgeeks.org/introduction-and-array-implementation-of-queue/
https://www.geeksforgeeks.org/queue-linked-list-implementation/
https://www.geeksforgeeks.org/implementation-queue-javascript/
