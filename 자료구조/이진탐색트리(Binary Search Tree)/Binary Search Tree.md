# 이진탐색트리(Binary Search Tree)

<br>

### 이진탐색트리(Binary Search Tree)

> 트리는 비선형 구조로 되어있는 자료 구조이다. 본질적으로 선형인 배열, 스택, 대기열 및 연결 목록과 같은 다른 자료 구조와 달리 트리는 계층 구조를 나타낸다. 이진 트리는 하나의 노드가 최대 2개의 자식 노드를 가지고 있는 트리이다.

<br/>

![BST](https://user-images.githubusercontent.com/93918946/226396198-67d22d0f-2d82-4d62-88b9-adef12d9b228.png)

<br/>

### 소개

이진 트리는 각 노드가 최대 두 개의 자식(왼쪽 자식과 오른쪽 자식)을 가질 수 있는 트리 자료 구조이다. 이진 트리의 맨 위에 있는 노드를 루트라고 하고, 맨 아래에 있는 노드를 리프라고 한다. 이진 트리는 루트가 맨 위에 있고 잎이 맨 아래에 있는 계층 구조로 시각화될 수 있다. 이진 트리는 데이터 저장 및 검색, 네트워크 라우팅, 인공지능, 머신 러닝 등에 사용된다. 검색, 정렬, 그래프 알고리즘과 같은 다양한 알고리즘을 구현하는 데도 사용할 수 있다.

<br/>

![TreeDataStructure](https://user-images.githubusercontent.com/93918946/226396188-8a75dba2-8a21-4889-9b96-3719fbaf6c9b.png)

이진 트리의 구성 요소는 다음과 같다.

- Root(루트 노드): 상위 노드가 없는 트리의 최상위 노드. 모든 트리에는 루트 노드가 하나만 있다.
- Parent Node(부모 노드): 노드의 직전 상위 노드를 해당 노드의 부모 노드라고 한다.
- Child Node(자식 노드): 노드의 바로 뒤를 잇는 노드를 해당 노드의 자식 노드라고 한다.
- Sibling(형제 노드): 동일한 부모 노드의 자식을 형제자매라고 한다.
- Edge(간선): 부모 노드와 자식 노드를 이어주는 역할을 한다.
- Leaf(리프 노드): 트리 구조의 최하단에 위치한 노드로 자식 노드가 없는 노드.

- Subtree(서브 트리): 특정 노드를 루트 노드로 간주했을 때 생기는 하위 트리
- Depth(깊이): 특정 노드에서 루트 노드까지 이동하는 데 거치는 간선의 수(루트 노드는 0)
- Height(높이): 루트 노드에서 리프 노드까지의 거리
- Level(레벨): 깊이가 같은 노드의 집합
- Degree(차수): 노드에 연결된 자식 노드의 수

**이진 탐색 트리**는 다음과 같은 특징이 있다.

- 노드의 왼쪽 하위 트리에는 노드의 키보다 작은 키를 가진 노드만 포함된다.
- 노드의 오른쪽 하위 트리에는 노드의 키보다 큰 키가 있는 노드만 포함된다.
- 왼쪽 및 오른쪽 하위 트리도 각각 이진 검색 트리여야 한다.

**이진 탐색 트리**의 기본 작업은 다음과 같다.

- Searching(탐색)
- Insertion(삽입)
- Deletion(삭제)
- Traversals(순회)
  - Preorder(전위 순회)  
    ![Preorder](https://user-images.githubusercontent.com/93918946/226823438-f9321242-f4af-43c2-b356-8c3d1e299d8b.gif)
  - Postorder(후위 순회)  
    ![Postorder](https://user-images.githubusercontent.com/93918946/226823434-1102c4d4-da3b-4085-a41c-31d81894ac83.gif)
  - Inorder(중위 순회 - 오름차순 정렬)  
    ![Inorder](https://user-images.githubusercontent.com/93918946/226823439-64a88ed4-7953-4c06-8386-d1996288e7e2.gif)
  - BFS(너비 우선 탐색)  
    ![BFS](https://user-images.githubusercontent.com/93918946/226823429-5907f8d9-f379-47d8-a4d1-ce8c15c244b7.gif)

**이진 탐색 트리의 장점**

- 검색 속도가 O(log n)으로 빠르다. 이진 탐색 트리는 데이터가 정렬되어 저장되므로, 검색 속도가 매우 빠르다.

- 삽입 및 삭제 연산도 O(log n)으로, 검색과 마찬가지로 빠르다.

- 메모리 절약이 가능하다. 이진 탐색 트리는 연결 리스트보다 메모리를 효율적으로 사용할 수 있다. 연결 리스트는 각 노드마다 포인터를 저장해야 하지만, 이진 탐색 트리는 불필요한 포인터를 제거할 수 있으므로 메모리를 절약할 수 있다.

**이진 탐색 트리의 단점**

- 데이터의 삽입 및 삭제가 빈번하게 일어나면, 이진 탐색 트리의 구조가 불균형해질 수 있다. 이런 경우 검색 속도가 떨어질 수 있다.

- 이진 탐색 트리는 데이터가 무작위로 입력될 때 최적의 성능을 낸다. 이미 정렬되어 있는 데이터를 입력할 경우, 트리가 한쪽으로 치우쳐져서 검색 속도가 떨어질 수 있다.

- 이진 탐색 트리를 구현하는 데에는 많은 구현 비용이 들어갈 수 있다. 예를 들어 균형을 유지하는 AVL 트리나 레드-블랙 트리를 구현하는 데에는 추가적인 구현 비용이 필요하다.

<br/>

### 시간 복잡도

|   작업    | 시간 복잡도 |
| :-------: | :---------: |
| Insertion |  O(log n)   |
| Searching |  O(log n)   |

<br/>

## 코드 예시

```javascript
class Node {
  constructor(value) {
    this.value = value;
    this.left = null;
    this.right = null;
  }
}

class BinarySearchTree {
  constructor() {
    this.root = null;
  }

  // 노드를 삽입
  insert(value) {
    let newNode = new Node(value);
    if (this.root === null) {
      this.root = newNode;
      return this;
    }
    let current = this.root;
    while (true) {
      if (value === current.value) return undefined;
      if (value < current.value) {
        if (current.left === null) {
          current.left = newNode;
          return this;
        }
        current = current.left;
      } else {
        if (current.right === null) {
          current.right = newNode;
          return this;
        }
        current = current.right;
      }
    }
  }

  // 주어진 값을 갖는 노드를 찾는다.
  find(value) {
    if (this.root === null) return false;
    let current = this.root,
      found = false;
    while (current && !found) {
      if (value < current.value) {
        current = current.left;
      } else if (value > current.value) {
        current = current.right;
      } else {
        found = true;
      }
    }
    if (!found) return undefined;
    return current;
  }

  // 주어진 값이 트리 내에 존재하는지 여부를 확인하고 반환한다.
  contains(value) {
    if (this.root === null) return false;
    let current = this.root,
      found = false;
    while (current && !found) {
      if (value < current.value) {
        current = current.left;
      } else if (value > current.value) {
        current = current.right;
      } else {
        return true;
      }
    }
    return false;
  }

  // Preorder Traversal(전위 순회)
  DFSPreOrder() {
    let data = [];
    function traverse(node) {
      data.push(node.value);
      if (node.left) traverse(node.left);
      if (node.right) traverse(node.right);
    }
    traverse(this.root);
    return data;
  }

  // Postorder Traversal(후위 순회)
  DFSPostOrder() {
    let data = [];
    function traverse(node) {
      if (node.left) traverse(node.left);
      if (node.right) traverse(node.right);
      data.push(node.value);
    }
    traverse(this.root);
    return data;
  }

  // Inorder Traversal(중위 순회)
  DFSInOrder() {
    let data = [];
    function traverse(node) {
      if (node.left) traverse(node.left);
      data.push(node.value);
      if (node.right) traverse(node.right);
    }
    traverse(this.root);
    return data;
  }

  // 너비 우선 탐색
  BFS() {
    let node = this.root,
      data = [],
      queue = [];
    queue.push(node);

    while (queue.length) {
      node = queue.shift();
      data.push(node.value);
      if (node.left) queue.push(node.left);
      if (node.right) queue.push(node.right);
    }
    return data;
  }

  // 트리의 높이를 반환한다.
  getHeight(node = this.root) {
    if (node === null) return -1;
    let leftHeight = this.getHeight(node.left);
    let rightHeight = this.getHeight(node.right);
    return Math.max(leftHeight, rightHeight) + 1;
  }

  // 주어진 두 노드의 가장 가까운 공통 조상 노드를 찾아 반환한다. (LowestCommonAncestor)
  findLCA(node1, node2) {
    if (!this.contains(node1) || !this.contains(node2)) {
      return null; // 노드가 존재하지 않을 경우 null 반환
    }

    function traverse(node) {
      if (node.value > node1 && node.value > node2) {
        return traverse(node.left);
      } else if (node.value < node1 && node.value < node2) {
        return traverse(node.right);
      } else {
        return node;
      }
    }

    return traverse(this.root);
  }

  // 특정 노드에서 루트 노드까지의 경로를 반환한다.
  distanceFromRoot(value) {
    if (!this.root) return null;

    let current = this.root;
    let distance = 0;

    while (current) {
      if (value === current.value) {
        return distance;
      } else if (value < current.value) {
        distance++;
        current = current.left;
      } else {
        distance++;
        current = current.right;
      }
    }

    return null;
  }

  // 두 노드 사이의 거리를 반환한다.
  findDistance(node1, node2) {
    if (!this.contains(node1) || !this.contains(node2)) {
      return null; // 노드가 존재하지 않을 경우 null 반환
    }

    // 두 노드의 가장 가까운 공통 조상 노드를 찾는다.
    let lca = this.findLCA(node1, node2);

    // 공통 조상 노드에서 각 노드까지의 거리를 계산한다.
    let distance1 = this.distanceFromRoot(node1);
    let distance2 = this.distanceFromRoot(node2);
    let distanceLCA = this.distanceFromRoot(lca.value);

    // 두 노드 사이의 거리를 계산하여 반환한다.
    return distance1 + distance2 - distanceLCA * 2;
  }
}
```

<br/>

---

참고 문서 :  
https://www.udemy.com/course/best-javascript-data-structures/  
https://www.geeksforgeeks.org/introduction-to-binary-tree-data-structure-and-algorithm-tutorials/  
https://dev.to/jenshaw/binary-trees-discussing-in-depth-first-traversals-4a8n  
https://dev.to/snird/breadth-first-traversal-for-binary-trees-in-js-h9m
