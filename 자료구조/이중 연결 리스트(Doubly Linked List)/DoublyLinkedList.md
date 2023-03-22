# 이중 연결 리스트(Doubly Linked List)

<br>

### 이중 연결 리스트(Doubly Linked List)

> 이중 연결 리스트는 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료 구조이다. 각 노드는 데이터와 다음 노드와 이전 노드의 주소를 가지고 있다.

<br/>

![Doublylinkedlist](https://user-images.githubusercontent.com/93918946/226185602-60146744-8d14-47c8-8430-5a508cbc529a.png)

<br/>

### 소개

이중 연결 리스트는 각 노드가 다음 노드와 이전 노드의 참조를 가지고 있는 연결 리스트이다. 이전 노드의 참조를 가지고 있기 때문에 양쪽 방향으로 노드 탐색이 가능하다. 이중 연결 리스트는 단일 연결 리스트와 비교하여 삽입, 삭제, 탐색 등의 작업에서 더욱 효율적인 성능을 보인다는 장점이 있다. 그러나 각 노드가 추가적인 포인터를 가지고 있기 때문에 저장공간의 부담이 높아지고, 구현이 복잡해진다는 단점도 있다. 이중 연결 리스트는 웹 브라우저의 뒤로가기/앞으로가기 등의 기능이나 텍스트 편집기의 실행 취소/되돌리기 등에 사용된다.

이중 연결 리스트의 기본 작업은 다음과 같다.

- Deletion(삭제)
  - 리스트의 시작 부분에 삽입
  - 리스트의 끝 부분에 삽입
  - 리스트의 특정 노드 뒤에 삽입
  - 리스트의 특정 노드 앞에 삽입
- Insertion(삽입)
  - 리스트의 시작 부분에서 삭제
  - 리스트의 끝 부분에서 삭제
  - 특정 노드를 삭제
- Display(표시)
  - 연결 리스트의 요소를 표시한다.

**이중 연결 리스트 구현의 장점**

- 양방향으로 순회가 가능하다. 각 노드가 다음 노드와 이전 노드를 가리키기 때문에, 양방향으로 순회할 수 있다.
- 노드 삭제 및 삽입이 쉽다. 이전 노드와 다음 노드를 모두 가리키기 때문에, 특정 노드를 삭제하거나 그 앞이나 뒤에 삽입할 수 있다.

**이중 연결 리스트 구현의 단점**

- 연결 리스트보다 메모리 사용량이 더 많다. 각 노드가 다음 노드와 이전 노드를 가리키기 때문에, 단일 연결리스트보다 메모리를 더 많이 사용한다.

<br/>

### 시간 복잡도

|   작업    | 시간 복잡도 |
| :-------: | :---------: |
| Insertion |    O(1)     |
|  Removal  |    O(1)     |
| Searching |    O(N)     |
|  Access   |    O(N)     |

<br/>

## 코드 예시

```javascript
class Node {
  constructor(val) {
    this.val = val;
    this.next = null;
    this.prev = null;
  }
}

class DoublyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }

  // 리스트의 맨 뒤에 데이터 삽입
  push(val) {
    var newNode = new Node(val);
    if (this.length === 0) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.tail.next = newNode;
      newNode.prev = this.tail;
      this.tail = newNode;
    }
    this.length++;
    return this;
  }

  // 리스트의 맨 뒤의 데이터 삭제
  pop() {
    if (!this.head) return undefined;
    var poppedNode = this.tail;
    if (this.length === 1) {
      this.head = null;
      this.tail = null;
    } else {
      this.tail = poppedNode.prev;
      this.tail.next = null;
      poppedNode.prev = null;
    }
    this.length--;
    return poppedNode;
  }

  // 리스트의 맨 앞의 데이터 삭제
  shift() {
    if (this.length === 0) return undefined;
    var oldHead = this.head;
    if (this.length === 1) {
      this.head = null;
      this.tail = null;
    } else {
      this.head = oldHead.next;
      this.head.prev = null;
      oldHead.next = null;
    }
    this.length--;
    return oldHead;
  }

  // 리스트의 맨 앞에 데이터 삽입
  unshift(val) {
    var newNode = new Node(val);
    if (this.length === 0) {
      this.head = newNode;
      this.tail = newNode;
    } else {
      this.head.prev = newNode;
      newNode.next = this.head;
      this.head = newNode;
    }
    this.length++;
    return this;
  }

  // 요소의 인덱스 반환
  get(index) {
    if (index < 0 || index >= this.length) return null;
    var count, current;
    if (index <= this.length / 2) {
      count = 0;
      current = this.head;
      while (count !== index) {
        current = current.next;
        count++;
      }
    } else {
      count = this.length - 1;
      current = this.tail;
      while (count !== index) {
        current = current.prev;
        count--;
      }
    }
    return current;
  }

  // 특정 위치에 데이터를 덮어쓴다.
  set(index, val) {
    var foundNode = this.get(index);
    if (foundNode != null) {
      foundNode.val = val;
      return true;
    }
    return false;
  }

  // 특정 위치에 데이터 삽입
  insert(index, val) {
    if (index < 0 || index > this.length) return false;
    if (index === 0) return !!this.unshift(val);
    if (index === this.length) return !!this.push(val);

    var newNode = new Node(val);
    var beforeNode = this.get(index - 1);
    var afterNode = beforeNode.next;

    (beforeNode.next = newNode), (newNode.prev = beforeNode);
    (newNode.next = afterNode), (afterNode.prev = newNode);
    this.length++;
    return true;
  }

  // 특정 위치의 데이터 삭제
  remove(index) {
    if (index < 0 || index >= this.length) return undefined;
    if (index === 0) return this.shift();
    if (index === this.length - 1) return this.pop();

    let removedNode = this.get(index);
    let beforeNode = removedNode.prev;
    let afterNode = removedNode.next;

    beforeNode.next = afterNode;
    afterNode.prev = beforeNode;
    removedNode.next = null;
    removedNode.prev = null;
    this.length--;
    return removedNode;
  }

  // 리스트의 요소를 출력
  print() {
    let arr = [];
    let current = this.head;
    while (current) {
      arr.push(current.val);
      current = current.next;
    }
    console.log(arr);
  }
}

// 실행
let list = new DoublyLinkedList();
list.push(30); // [ 30 ]
list.push(50); // [30, 50]
list.push(70); // [ 30, 50, 70 ]
list.insert(2, 90); // [ 30, 50, 90, 70 ]
list.remove(3); // [ 30, 50, 90 ]
```

<br/>

---

참고 문서 :  
https://www.udemy.com/course/best-javascript-data-structures/  
https://www.geeksforgeeks.org/introduction-and-insertion-in-a-doubly-linked-list/
