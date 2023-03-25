# 그래프(Graph)

<br>

### 그래프(Graph)

> 그래프는 정점과 간선으로 구성된 비선형 자료 구조이다. 정점은 노드라고도 하며, 간선은 그래프의 두 정점을 연결하는 선이다.

<br/>

![graph18](https://user-images.githubusercontent.com/93918946/227714038-8e739ca7-9270-4f8f-808b-95ef4ffb96d2.jpg)

<br/>

### 소개

그래프는 정점(vertex)/노드(node)와 간선(edge)으로 구성된 자료구조로, 현실의 복잡한 현상이나 시스템을 모델링하는 데 유용하게 사용된다. 정점과 간선의 수를 각각 V와 E라고 할 때, 그래프는 보통 G=(V,E)로 표현된다. 그래프는 SNS, 지도 기능, 방향 안내, 위치, 최단 경로 찾기, 라우팅 등에 사용된다.

<br/>

그래프의 구성 요소는 다음과 같다.

- Vertex(정점)/Node(노드): 정점은 그래프의 기본 단위로 정점 또는 노드라고도 한다.
- Edge(간선): 간선은 노드와 노드 사이를 연결하는 선이며, 그래프에서 두 개의 노드를 연결하는 역할을 한다.

<br/>

### 그래프의 종류

- **무방향 그래프와 방향 그래프**

![directed](https://user-images.githubusercontent.com/93918946/227714270-fc8466ec-9ec5-4407-aaeb-95a79dcae6fd.jpg)

- 무방향 그래프 (Undirected Graph)  
  무방향 그래프는 간선에 방향성이 없는 그래프다.  
  즉, 간선이 연결된 두 정점 간의 관계가 상호적이며, 두 정점 사이의 간선은 양방향으로 통과할 수 있다.

- 방향 그래프 (Directed Graph)  
  방향 그래프는 간선에 방향성이 있는 그래프다.  
  즉, 간선이 연결된 두 정점 간의 관계가 방향적이며, 하나의 정점에서 다른 정점으로 가는 간선과 반대 방향으로 가는 간선이 다를 수 있다.

  <br/>

- **가중 그래프와 비가중 그래프**

![gfg-300x168](https://user-images.githubusercontent.com/93918946/227714271-225d7274-7aba-4105-8a7f-36f4d54246f7.png)
![gfg2-300x168](https://user-images.githubusercontent.com/93918946/227714272-234adca3-a18f-48dd-8850-9056ab844b35.png)

- 가중 그래프 (Weighted Graph)  
  가중치가 있는 그래프는 간선에 가중치(weight)가 할당된 그래프다.  
  이러한 가중치는 간선을 따라 이동하는 데 필요한 비용이나 거리 등을 나타내는 값으로 사용될 수 있다.

- 비가중 그래프 (Unweighted Graph)
  가중치가 없는 그래프는 모든 간선에 동일한 가중치를 부여하지 않는 그래프다.  
  이러한 경우 간선의 유무만으로 두 정점 간의 관계를 표현한다.

<br/>

### 그래프의 표현

그래프의 표현에는 두 가지 방식이 있다.

- **인접 리스트**  
  ![adjacency_list](https://user-images.githubusercontent.com/93918946/227714580-e01930b4-62d2-4927-9c40-447c8aab8f9f.jpg)

- **인접 행렬**  
  ![adjacency_mat1](https://user-images.githubusercontent.com/93918946/227714578-114346df-7d7a-4206-b03a-0f9f70854a65.jpg)

**인접 리스트 방식의 그래프**는 다음과 같은 특징이 있다.

- 인접 리스트 방식은 배열과 연결 리스트를 활용하여 구현된다.  
  배열의 인덱스는 각 정점을 의미하고, 배열의 각 요소는 해당 정점과 인접한 모든 정점을 연결 리스트로 저장한다. 인접 리스트 방식은 그래프의 크기와는 무관하게 항상 공간을 효율적으로 사용할 수 있다.
- 그래프가 복잡하지 않은 경우라면 인접 행렬 방식보다 빠른 시간 복잡도를 가질 수 있지만, 그래프가 복잡한 경우라면 간선의 존재 여부를 확인하기 위해 연결 리스트를 모두 탐색해야 하므로 인접 행렬 방식에 비해 비교적 느린 시간 복잡도를 가질 수 있다.

**인접 행렬 방식의 그래프**는 다음과 같은 특징이 있다.

- 인접 행렬 방식은 2차원 배열로 구현된다.  
  각 정점을 행과 열로 표시하고, 두 정점 사이의 연결 관계를 배열 요소의 값으로 나타낸다. 연결된 경우 1, 그렇지 않은 경우 0으로 표시할 수 있다. 가중치 그래프라면 배열 요소에 가중치 값을 저장할 수도 있다.
- 간선의 존재 여부를 빠르게 확인할 수 있어 인접 리스트 방식에 비해 더 빠른 시간 복잡도를 가질 수 있다. 하지만 간선의 개수가 적은 경우에는 공간 낭비가 심해질 수 있다.

<br/>

**그래프**의 기본 작업은 다음과 같다.

- Insertion of Nodes/Edges in the graph – 그래프에 노드를 삽입한다.
- Deletion of Nodes/Edges in the graph – 그래프에서 노드를 삭제한다.
- Searching on Graphs – 그래프에서 요소를 탐색한다.
- Traversal of Graphs – 그래프의 모든 노드를 순회한다. **(BFS/DFS)**  
  일반적으로 BFS가 최단 경로를 찾는 데 더 효율적이다. BFS는 레벨 단위로 탐색하기 때문에, 먼저 목표 정점을 발견하면 바로 탐색을 중단할 수 있다.  
  반면에 DFS는 최단 경로를 보장하지 않는다. DFS는 깊이를 우선적으로 탐색하기 때문에, 목표 정점까지 도달하는 경로가 가장 깊은 경로일 경우, 최단 경로를 찾지 못할 수 있다.  
  따라서 DFS는 최단 경로를 보장하는 문제에서는 적합하지 않다.

<br/>

**그래프의 장점**

- 그래프는 광범위한 관계 및 데이터 구조를 나타내는 데 사용할 수 있다.
- 경로 찾기, 네트워크 분석 및 기계 학습 등 광범위한 문제를 모델링하고 해결하는 데 사용할 수 있다.
- 복잡한 데이터 구조를 간단하고 직관적인 방식으로 표현하고 이해하기 쉽다.

**그래프의 단점**

- 그래프의 생성 및 조작은 매우 크거나 복잡한 그래프의 경우 계산 비용이 많이 들어갈 수 있다.
- 매우 크거나 복잡한 그래프의 경우 그래프를 시각화하고 분석하기 어려울 수 있다.

<br/>

### 시간 복잡도

|       작업       | 인접 행렬 | 인접 리스트 |
| :--------------: | :-------: | :---------: |
|   Adding Edge    |   O(1)    |    O(1)     |
| Removing an edge |   O(1)    |    O(N)     |
|   Initializing   | O(N \* N) |    O(N)     |

<br/>

## 코드 예시

```javascript
class Graph {
  constructor() {
    this.adjList = {}; // adjacencyList
  }

  // 정점 추가
  addVertex(vertex) {
    if (!(vertex in this.adjList)) this.adjList[vertex] = [];
  }

  // 간선 추가
  addEdge(v1, v2) {
    this.adjList[v1].push(v2);
    this.adjList[v2].push(v1);
  }

  // 간선 제거
  removeEdge(vertex1, vertex2) {
    const index1 = this.adjList[vertex1].indexOf(vertex2);
    if (index1 !== -1) this.adjList[vertex1].splice(index1, 1);

    const index2 = this.adjList[vertex2].indexOf(vertex1);
    if (index2 !== -1) this.adjList[vertex2].splice(index2, 1);
  }

  // 정점 제거
  removeVertex(vertex) {
    while (this.adjList[vertex].length) {
      const adjacentVertex = this.adjList[vertex].pop();
      this.removeEdge(vertex, adjacentVertex);
    }
    delete this.adjList[vertex];
  }

  // 정점이 그래프에 존재하는지 확인
  hasVertex(vertex) {
    return vertex in this.adjList;
  }

  // 간선이 그래프에 존재하는지 확인
  hasEdge(vertex1, vertex2) {
    return this.adjList[vertex1].includes(vertex2);
  }

  // 정점과 연결된 모든 인접 정점 반환
  getNeighbors(vertex) {
    return this.adjList[vertex];
  }

  // 그래프의 모든 정점 반환
  getAllVertexes() {
    return Object.keys(this.adjList);
  }

  // DFS
  dfs(start) {
    const stack = [start];
    const result = [];
    const visited = {};
    visited[start] = true;

    while (stack.length) {
      const currentVertex = stack.pop();
      result.push(currentVertex);

      this.adjList[currentVertex].forEach((neighbor) => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          stack.push(neighbor);
        }
      });
    }
    return result;
  }

  // BFS
  bfs(start) {
    const queue = [start];
    const result = [];
    const visited = {};
    visited[start] = true;

    while (queue.length) {
      const currentVertex = queue.shift();
      result.push(currentVertex);

      this.adjList[currentVertex].forEach((neighbor) => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          queue.push(neighbor);
        }
      });
    }
    return result;
  }

  // 그래프의 두 정점 사이의 최단 경로를 탐색하고 길이를 반환(BFS 방식)
  shortestPath(start, end) {
    const distances = {};
    const visited = {};
    const queue = [start];
    let currentVertex;

    distances[start] = 0;

    while (queue.length) {
      currentVertex = queue.shift();

      if (currentVertex === end) {
        return distances[end];
      }

      this.adjList[currentVertex].forEach((neighbor) => {
        if (!visited[neighbor]) {
          visited[neighbor] = true;
          distances[neighbor] = distances[currentVertex] + 1;
          queue.push(neighbor);
        }
      });
    }
  }
}
```

<br/>

---

참고 문서 :  
https://www.udemy.com/course/best-javascript-data-structures/  
https://www.geeksforgeeks.org/introduction-to-graphs-data-structure-and-algorithm-tutorials/
