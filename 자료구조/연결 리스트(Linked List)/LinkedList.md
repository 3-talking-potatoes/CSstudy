# 연결 리스트(Linked List)

<br>

### 연결 리스트(Linked List)

> 연결 리스트, 링크드 리스트(linked list)는 각 노드가 데이터와 포인터를 가지고 한 줄로 연결되어 있는 방식으로 데이터를 저장하는 자료 구조이다. 각 노드는 데이터와 다음 노드의 주소를 가지고 있다.

<br/>

![Singlelinkedlist](https://user-images.githubusercontent.com/93918946/226120569-7cdd6144-6335-44f3-9398-c63727e18008.png)

<br/>

### 소개

연결 리스트는 데이터 요소들을 일렬로 연결한 자료구조이다. 각 요소는 자신의 데이터와 다음 요소를 가리키는 포인터(주소)를 가지고 있다. 이러한 구조를 통해 삽입, 삭제 작업이 배열과 달리 효율적으로 수행될 수 있다. 또한 크기가 동적으로 조절될 수 있어 메모리를 효율적으로 사용할 수 있다. 데이터의 추가, 삽입, 삭제에 용이해 데이터베이스, 캐시 등에 사용되고, 그래프 알고리즘과 같은 데이터를 차례대로 처리하는 알고리즘 구현등에 사용된다.

연결 리스트의 기본 작업은 다음과 같다.

- Deletion(삭제)
  - 리스트의 시작 부분에 삽입
  - 리스트의 끝 부분에 삽입
  - 리스트의 특정 위치에 삽입
- Insertion(삽입)
  - 리스트의 시작 부분에서 삭제
  - 리스트의 끝 부분에서 삭제
  - 특정 노드를 삭제
- Search(탐색)
  - 연결 리스트의 특정 노드를 탐색한다.
- Display(표시)
  - 연결 리스트의 요소를 표시한다.

**연결 리스트 구현의 장점**

- 전체 데이터 구조를 재구성하지 않고 연결 목록에서 노드를 쉽게 제거하거나 추가할 수 있으므로, 일반적으로 삽입, 삭제 시간이 배열보다 빠르다.
- 메모리를 동적으로 할당하기 때문에, 배열과 달리 크기가 고정되어 있지 않아서 유연하다.

**연결 리스트 구현의 단점**

- 랜덤 엑세스(임의 접근)가 불가능하다. 원하는 인덱스의 요소를 접근하기 위해서는 처음부터 선형 탐색을 해야 하기 때문에 배열보다 접근 시간이 느리다.
- 배열과 달리 각 노드를 위한 포인터를 유지해야 하므로 메모리를 더 사용한다. 이로 인해 캐시 효율이 떨어져서 성능이 느려질 수 있다.

<br/>

### 시간 복잡도

|   작업    | 시간 복잡도  |
| :-------: | :----------: |
| Insertion |     O(1)     |
|  Removal  | O(1) or O(N) |
| Searching |     O(N)     |
|  Access   |     O(N)     |

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

class SinglyLinkedList {
  constructor() {
    this.head = null;
    this.tail = null;
    this.length = 0;
  }

  // 리스트의 맨 뒤에 데이터 삽입
  push(val) {
    let newNode = new Node(val);
    if (!this.head) {
      this.head = newNode;
      this.tail = this.head;
    } else {
      this.tail.next = newNode;
      this.tail = newNode;
    }
    this.length++;
    return this;
  }

  // 리스트의 맨 뒤의 데이터 삭제
  pop() {
    if (!this.head) return undefined;
    let current = this.head;
    let newTail = current;
    while (current.next) {
      newTail = current;
      current = current.next;
    }
    this.tail = newTail;
    this.tail.next = null;
    this.length--;
    if (this.length === 0) {
      this.head = null;
      this.tail = null;
    }
    return current;
  }

  // 리스트의 맨 앞의 데이터 삭제
  shift() {
    if (!this.head) return undefined;
    let currentHead = this.head;
    this.head = currentHead.next;
    this.length--;
    if (this.length === 0) {
      this.tail = null;
    }
    return currentHead;
  }

  // 리스트의 맨 앞에 데이터 삽입
  unshift(val) {
    let newNode = new Node(val);
    if (!this.head) {
      this.head = newNode;
      this.tail = this.head;
    }
    newNode.next = this.head;
    this.head = newNode;
    this.length++;
    return this;
  }

  // 요소의 인덱스 반환
  get(index) {
    if (index < 0 || index >= this.length) return null;
    let counter = 0;
    let current = this.head;
    while (counter !== index) {
      current = current.next;
      counter++;
    }
    return current;
  }

  // 특정 위치에 데이터를 덮어쓴다.
  set(index, val) {
    let foundNode = this.get(index);
    if (foundNode) {
      foundNode.val = val;
      return true;
    }
    return false;
  }

  // 특정 위치에 데이터 삽입
  insert(index, val) {
    if (index < 0 || index > this.length) return false;
    if (index === this.length) return !!this.push(val);
    if (index === 0) return !!this.unshift(val);

    let newNode = new Node(val);
    let prev = this.get(index - 1);
    let temp = prev.next;
    prev.next = newNode;
    newNode.next = temp;
    this.length++;
    return true;
  }

  // 특정 위치의 데이터 삭제
  remove(index) {
    if (index < 0 || index >= this.length) return undefined;
    if (index === 0) return this.shift();
    if (index === this.length - 1) return this.pop();
    let previousNode = this.get(index - 1);
    let removed = previousNode.next;
    previousNode.next = removed.next;
    this.length--;
    return removed;
  }

  // 리스트를 역방향순으로 배치
  reverse() {
    let node = this.head;
    this.head = this.tail;
    this.tail = node;
    let next;
    let prev = null;
    for (let i = 0; i < this.length; i++) {
      next = node.next;
      node.next = prev;
      prev = node;
      node = next;
    }
    return this;
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
let list = new SinglyLinkedList();
list.push(30); // [ 30 ]
list.push(50); // [30, 50]
list.push(70); // [ 30, 50, 70 ]
list.insert(2, 90); // [ 30, 50, 90, 70 ]
list.remove(3); // [ 30, 50, 90 ]
```

<br/>

---

참고 문서 :  
https://ko.wikipedia.org/wiki/%EC%97%B0%EA%B2%B0_%EB%A6%AC%EC%8A%A4%ED%8A%B8
https://www.geeksforgeeks.org/introduction-to-linked-list-data-structure-and-algorithm-tutorial/
https://www.udemy.com/course/best-javascript-data-structures/
