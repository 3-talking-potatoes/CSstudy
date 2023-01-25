# 선택 정렬(Selection Sort)

<br>

### 선택 정렬(Selection Sort)

> 선택 정렬은 정렬되지 않은 부분에서 최소값인 요소를 반복적으로 찾아 맨 앞에 놓는 방식으로 작동하는 단순 정렬 ​​알고리즘입니다.

<br/>

![이미지](https://user-images.githubusercontent.com/93918946/214066485-d89e7fc4-eace-46c3-b21b-842bc14689ef.png)  
참고 문서 : https://www.w3resource.com/python-exercises/data-structures-and-algorithms/python-search-and-sorting-exercise-5.php

<br/>

### 소개

선택 정렬은 정렬 알고리즘으로, 주어진 배열을 탐색하면서 최소값을 찾고, 해당 최소값을 맨 앞에 위치한 요소와 교환하는 것을 반복하여 배열을 정렬하는 알고리즘이다.

<br/>

### 시간 복잡도

| 작업 | 시간 복잡도 |
| :--: | :---------: |
| 평균 |   O(n^2)    |
| 최선 |   O(n^2)    |
| 최악 |   O(n^2)    |

<br/>

### 코드 작성을 위한 단계

1. 첫 번째 요소를 현재까지 본 최소 값으로 저장한다.
2. 더 작은 숫자를 찾을 때까지 이 항목을 배열의 다음 항목과 비교한다.
3. 더 작은 숫자가 발견되면 해당 숫자를 새로운 "최소값"으로 지정하고 배열이 끝날 때까지 계속한다.
4. "최소값"이 처음 시작했던 값(인덱스)과 다르면 두 값을 교환한다.
5. 배열이 정렬될 때까지 다음 요소에 대해 이 과정을 반복한다.

<br/>

## 코드 예시

```javascript
function selectionSort(arr) {
  for (let i = 0; i < arr.length; i++) {
    let lowest = i;
    for (let j = i + 1; j < arr.length; j++) {
      if (arr[j] < arr[lowest]) {
        lowest = j;
      }
    }
    if (i !== lowest) {
      let temp = arr[i];
      arr[i] = arr[lowest];
      arr[lowest] = temp;
    }
  }
  return arr;
}

selectionSort([8, 1, 2, 3, 4, 5, 6, 7]);
// Output: [1, 2, 3, 4, 5, 6, 7, 8]
```

<br/>

---
