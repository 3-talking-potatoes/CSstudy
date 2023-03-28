# 힙(Heap)

<br>

### 힙(Heap)

> 힙은 트리의 일종이다. 힙은 완전 이진 트리 기반 자료구조이다. 이진 힙은 구조에 따라 최대 또는 최소 요소를 얻기 위해 데이터를 효율적으로 저장하는 데 사용되는 완전 이진 트리이다 .

<br/>

![MinHeapAndMaxHeap](https://user-images.githubusercontent.com/93918946/227586988-8c83e5d0-d7d2-4ab9-93a4-f398a0cefc3f.png)

<br/>

### 소개

힙은 트리의 일종이며, 이진 탐색 트리와 비슷하지만 다른 규칙을 가지고 있다. 이진 힙을 이용해서 [**우선순위 큐**](<https://github.com/3-talking-potatoes/CSstudy/blob/main/%EC%9E%90%EB%A3%8C%EA%B5%AC%EC%A1%B0/%EC%9A%B0%EC%84%A0%EC%88%9C%EC%9C%84%20%ED%81%90(Priority%20Queue)/Priority%20Queue.md>)를 구현할 수 있다. 또한 이진 힙은 그래프 순회에 자주 사용된다. 일반적으로 힙은 최대 힙과 최소 힙 두가지 유형으로 나뉜다.

<br/>

**이진 힙**은 다음과 같은 특징이 있다.

- 최대 힙: 항상 부모 노드가 자식 노드보다 큰 값을 가진다. 왼쪽, 오른쪽은 관계 없이 한 레벨 위의 부모 노드라면 자식 노드보다 큰 값을 갖는다.
- 최소 힙: 항상 자식 노드가 부모 노드보다 큰 값을 가진다.
- **이진** 힙답게 모든 부모 노드는 최대 2개의 자식 노드를 가질 수 있다.
- 항상 최적의 용량(적은 공간)을 가진다. 다음 레벨로 내려가기 전에 left와 right가 모두 채워져야 하기 때문이다.
- 항상 왼쪽 자식 노드가 먼저 채워진다.

**이진 힙**의 기본 작업은 다음과 같다.

- Insertion(삽입)
- Deletion(삭제)
- Peek(탐색) - 최소 혹은 최대값을 가진 루트 노트의 값을 반환

**이진 힙의 장점**

- 배열로 구현되어 메모리 공간의 낭비가 적어 공간 효율성이 좋다.
- 삽입과 삭제 연산의 시간 복잡도가 O(log N)으로 빠른 편이다.

**이진 힙의 단점**

- 최소 혹은 최대값에는 효율적으로 접근할 수 있지만 힙의 특정 요소를 검색하는 데는 적합하지 않다. 힙에서 요소를 검색하려면 전체 트리를 탐색해야 하며 시간 복잡도는 O(n)이 소모된다.

<br/>

### 시간 복잡도

|   작업    | 시간 복잡도 |
| :-------: | :---------: |
| Insertion |  O(log n)   |
|  Removal  |  O(log n)   |
| Searching |    O(n)     |

<br/>

## **최대 힙** 코드 예시(최소 힙의 경우에는 표시한 부분을 부등호를 반대로 구현하면 된다.)

```javascript
class MaxBinaryHeap {
  constructor() {
    this.values = [];
  }

  // 요소 삽입
  insert(element) {
    this.values.push(element);
    this.bubbleUp();
  }
  // 요소가 더 큰 값과 비교를 통해 위치를 변경한다.
  // Heapify라고도 한다.
  bubbleUp() {
    let idx = this.values.length - 1;
    const element = this.values[idx];
    while (idx > 0) {
      let parentIdx = Math.floor((idx - 1) / 2);
      let parent = this.values[parentIdx];
      if (element <= parent) break; // 최소힙으로 변경시 부등호 변경
      this.values[parentIdx] = element;
      this.values[idx] = parent;
      idx = parentIdx;
    }
  }

  // 최대값을 가진 루트 노드를 삭제하고 반환 및 노드들의 위치를 재정렬한다.
  extractMax() {
    const max = this.values[0];
    const end = this.values.pop();
    if (this.values.length > 0) {
      this.values[0] = end;
      this.sinkDown();
    }
    return max;
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
        if (leftChild > element) {
          // 최소힙으로 변경시 부등호 변경
          swap = leftChildIdx;
        }
      }
      if (rightChildIdx < length) {
        rightChild = this.values[rightChildIdx];
        if ((swap === null && rightChild > element) || (swap !== null && rightChild > leftChild)) {
          // 최소힙으로 변경시 부등호 변경
          swap = rightChildIdx;
        }
      }
      if (swap === null) break;
      this.values[idx] = this.values[swap];
      this.values[swap] = element;
      idx = swap;
    }
  }

  // 최대값을 가진 루트 노드를 삭제하지 않고 반환
  peek() {
    return this.values[0];
  }
}

// 실행
let heap = new MaxBinaryHeap();
heap.insert(41); // [41]
heap.insert(39); // [41, 39]
heap.insert(33); // [41, 39, 33]
heap.insert(18); // [41, 39, 33, 18]
console.log(heap.values); // [41, 39, 33, 18]
heap.extractMax(); // 41
console.log(heap.values); // [ 39, 18, 33 ]
```

<br/>

---

참고 문서 :  
https://www.udemy.com/course/best-javascript-data-structures/  
https://www.geeksforgeeks.org/introduction-to-heap-data-structure-and-algorithm-tutorials/
