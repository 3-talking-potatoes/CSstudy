# 선형 탐색(Linear Search)

<br>

### 선형 탐색(Linear Search), 순차 탐색(Sequential Search)

> 선형 탐색은 한쪽 끝에서 시작하여 원하는 요소를 찾을 때까지 목록의 각 요소를 통과하는 순차적 검색 알고리즘이다.

<br/>

![이미지](https://user-images.githubusercontent.com/93918946/210711348-f35c8091-7b96-47b1-82a7-1f15773ed977.png)

<br/>

### 소개

선형 탐색은 N개의 요소를 가진 배열 arr[]가 주어졌을 때 필요한 요소 X를 찾는 함수이다.

<br/>

### 입출력 예시

- Input: arr[] = {10, 20, 80, 30, 50, 110, 100, 170}, x = 110;  
  Output: 6  
  설명: x 요소는 6번째 인덱스에 위치하고 있다.

- Input: arr[] = {10, 20, 80, 30, 60, 50, 100, 130}, x = 175;  
  Output: -1  
  설명: x 요소는 arr[]안에 존재하지 않는다.

<br/>

### 문제 해결을 위한 아이디어

0번째 인덱스부터 N-1번째 인덱스까지 반복하면서 모든 인덱스의 값을 x와 비교하여 일치하는 경우 반환한다.

<br/>

### 코드 작성을 위한 단계

- arr[]의 가장 왼쪽 요소부터 시작하여 x를 arr[]의 각 요소와 하나씩 비교한다.
- x가 요소와 일치하면 인덱스를 반환한다.
- x가 어떤 요소와도 일치하지 않으면 -1을 반환한다.

<br/>

## 코드 예시

```javascript
function linearSearch(array, target) {
  for (let i = 0; i < array.length; i++) {
    if (array[i] === target) {
      return i;
    }
  }
  return -1;
}

// 실행

const array = [1, 2, 3, 4, 5];
console.log(linearSearch(array, 3)); // Output: 2
console.log(linearSearch(array, 7)); // Output: -1
```

<br/>

재귀적 접근법

```javascript
function linearSearch(array, target, index = 0) {
  if (index >= array.length) {
    return -1;
  }
  if (array[index] === target) {
    return index;
  }
  return linearSearch(array, target, index + 1);
}

// 실행

const array = [1, 2, 3, 4, 5];
console.log(linearSearch(array, 3)); // Output: 2
console.log(linearSearch(array, 7)); // Output: -1
```

<br/>

---

참고 문서 : https://www.geeksforgeeks.org/linear-search/
