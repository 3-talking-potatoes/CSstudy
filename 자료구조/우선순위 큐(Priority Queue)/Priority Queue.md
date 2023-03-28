# 우선 순위 큐(Priority Queue)

<br>

### 우선 순위 큐(Priority Queue)

> 우선 순위 큐는 각 요소가 그에 해당하는 우선 수위를 가지는 자료구조다. 더 높은 우선 수위를 가진 요소가 더 낮은 우선 수위를 가진 요소보다 먼저 처리된다.

<br/>

![Priority-Queue-min-1024x512](https://user-images.githubusercontent.com/93918946/227706349-4754e536-1ad5-4b1b-a7ac-e7acd22b739d.png)

<br/>

### 소개

우선 순위 큐는 우선 순위 값을 기준으로 요소를 정렬하는 큐다. 큐의 요소에는 우선 순위가 없는 반면, 우선 순위 큐의 요소에는 우선 순위가 있다. 일반적으로 우선 순위 값이 높은 요소는 우선 순위 값이 낮은 요소보다 먼저 검색된다.  
우선 순위 큐를 구현하는 방법에는 배열, 연결 리스트, 힙 또는 이진 검색 트리를 사용하는 방법이 있다.  
우선 순위 큐는 실시간 시스템 등에 사용되며, 그래프에서 가장 짧은 경로를 찾는 데이크스트라 알고리즘(Dijkstra’s algorithm) 등에 사용된다.

<br/>

**우선 수위 큐**는 다음과 같은 특징이 있다.

- 모든 항목에는 우선 순위가 연결되어 있다.
- 우선 순위가 높은 요소는 우선 순위가 낮은 요소보다 먼저 큐에서 제외된다. (보통 낮은 숫자가 더 높은 우선 순위를 의미한다.)
- 두 요소의 우선 순위가 같을 경우 큐의 순서대로 처리된다.

**우선 수위 큐**의 기본 작업은 다음과 같다.

- Insertion(삽입)
- Deletion(삭제)
- Peek(탐색) - 우선순위가 가장 높은 값을 반환한다.

<br/>

**우선 수위 큐의 장점**

- 우선순위 큐는 데이터를 정렬된 상태로 유지할 수 있다. 이를 통해 데이터를 쉽게 추출할 수 있으며, 데이터의 탐색 시간을 줄일 수 있다.
- 데이터가 추가되거나 삭제될 때, 우선순위 큐는 정렬된 상태를 유지하기 위해 자동으로 데이터를 재정렬한다. 따라서 우선순위 큐를 사용하면 데이터 정렬에 대한 복잡성을 줄일 수 있다.
- 우선순위 큐는 다양한 알고리즘에 사용될 수 있습니다. 예를 들어, Dijkstra의 최단 경로 알고리즘에서 우선순위 큐를 사용하면 최단 경로를 빠르게 계산할 수 있다.

**우선 수위 큐의 단점**

- 우선 순위 큐는 배열 및 연결 리스트와 같은 단순한 자료 구조보다 복잡하며 구현 및 유지 관리가 더 어려울 수 있다.
- 메모리 소비가 높다. 각 요소의 우선 순위 값을 우선 순위 큐에 저장하기 위해 추가 메모리를 차지할 수 있으며, 이는 리소스가 제한된 시스템에서 문제가 될 수 있다.

<br/>

### 시간 복잡도

|  작업   | 시간 복잡도 |
| :-----: | :---------: |
| enqueue |  O(log n)   |
| dequeue |  O(log n)   |
|  peek   |    O(1)     |

<br/>

## 코드 예시

```javascript
class Node {
  constructor(val, priority) {
    this.val = val;
    this.priority = priority;
  }
}

class PriorityQueue {
  constructor() {
    this.values = [];
  }

  // 요소 삽입
  enqueue(val, priority) {
    let newNode = new Node(val, priority);
    this.values.push(newNode);
    this.bubbleUp();
  }
  // 우선 순위가 더 높은 요소와 비교를 통해 위치를 변경한다.
  bubbleUp() {
    let idx = this.values.length - 1;
    const element = this.values[idx];
    while (idx > 0) {
      let parentIdx = Math.floor((idx - 1) / 2);
      let parent = this.values[parentIdx];
      if (element.priority >= parent.priority) break;
      if (element.priority === parent.priority && element.val >= parent.val) break;
      this.values[parentIdx] = element;
      this.values[idx] = parent;
      idx = parentIdx;
    }
  }

  // 가장 우선 순위가 높은 요소(루트 노드)를 삭제하고 반환 및 노드들의 위치를 재정렬한다.
  dequeue() {
    const min = this.values[0];
    const end = this.values.pop();
    if (this.values.length > 0) {
      this.values[0] = end;
      this.sinkDown();
    }
    return min;
  }
  sinkDown() {
    let idx = 0;
    const length = this.values.length;
    const element = this.values[0];
    while (true) {
      let leftChildIdx = 2 * idx + 1;
      let rightChildIdx = 2 * idx + 2;
      let leftChild, rightChild;
      let swap = null;

      if (leftChildIdx < length) {
        leftChild = this.values[leftChildIdx];
        if (leftChild.priority < element.priority) {
          swap = leftChildIdx;
        }
      }
      if (rightChildIdx < length) {
        rightChild = this.values[rightChildIdx];
        if ((swap === null && rightChild.priority < element.priority) || (swap !== null && rightChild.priority < leftChild.priority)) {
          swap = rightChildIdx;
        }
      }
      if (swap === null) break;
      this.values[idx] = this.values[swap];
      this.values[swap] = element;
      idx = swap;
    }
  }

  // 특정 요소의 우선순위를 낮춘다.
  decreasePriority(val, newPriority) {
    for (let i = 0; i < this.values.length; i++) {
      if (this.values[i].val === val) {
        if (this.values[i].priority < newPriority) {
          return;
        }
        this.values[i].priority = newPriority;
        let idx = i;
        let element = this.values[idx];
        while (true) {
          let parentIdx = Math.floor((idx - 1) / 2);
          let parent = this.values[parentIdx];
          if (parent && element.priority < parent.priority) {
            this.values[parentIdx] = element;
            this.values[idx] = parent;
            idx = parentIdx;
          } else {
            this.sinkDown(idx);
            break;
          }
        }
        return true;
      }
    }
    return false;
  }

  // 가장 우선 순위가 높은 요소(루트 노드)를 삭제하지 않고 반환
  peek() {
    return this.values[0];
  }
}
// 실행
const pq = new PriorityQueue();
pq.enqueue('A', 4);
pq.enqueue('B', 1);
pq.enqueue('C', 3);
pq.enqueue('D', 2);

console.log(pq.values); // [ Node { val: 'B', priority: 1 },
//   Node { val: 'D', priority: 2 },
//   Node { val: 'C', priority: 3 },
//   Node { val: 'A', priority: 4 } ]

pq.decreasePriority('A', 2);
console.log(pq.values); // [ Node { val: 'B', priority: 1 },
//   Node { val: 'D', priority: 2 },
//   Node { val: 'C', priority: 3 },
//   Node { val: 'A', priority: 2 } ]

console.log(pq.dequeue()); // Node { val: 'B', priority: 1 }
console.log(pq.values); // [ Node { val: 'D', priority: 2 },
//   Node { val: 'A', priority: 2 },
//   Node { val: 'C', priority: 3 } ]

console.log(pq.peek()); // Node { val: 'D', priority: 2 }
```

<br/>

---

참고 문서 :  
https://www.udemy.com/course/best-javascript-data-structures/  
https://www.geeksforgeeks.org/priority-queue-set-1-introduction/
