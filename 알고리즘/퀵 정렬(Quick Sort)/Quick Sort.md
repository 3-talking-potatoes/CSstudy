# 퀵 정렬(Quick Sort)

<br>

### 퀵 정렬(Quick Sort)

> 퀵 정렬은 요소를 피벗으로 선택하고 피벗을 기준으로 배열을 분할 후 다른 요소와 비교를 통해 정렬하는 정렬 알고리즘입니다. 합병 정렬과 마찬가지로 분할 정복(Divide and Conquer) 알고리즘입니다.

<br/>

![이미지](https://user-images.githubusercontent.com/93918946/212001711-3a8c6269-e2d3-471a-82a3-262a959e5063.png)

<br/>

### 소개

퀵 정렬은 평균적으로 가장 빠른 정렬 알고리즘이다. 합병 정렬과 달리 별도의 메모리 공간을 필요로 하지 않으며, 다른 요소와 비교를 통해 정렬하는 정렬 알고리즘이다. 시간 복잡도의 경우 평균적으로 O(n log n), 최악의 경우 O(n^2)의 시간 복잡도를 가진다. 합병 정렬과 달리 불안정 정렬(unstable sort)이므로 입력 순서와 관계없이 무작위로 섞인 상태에서 정렬이 이루어져 동일한 키 값을 가진 요소의 순서가 정렬 후 달라질 수 있다.

<br/>

### 시간 복잡도

| 작업 | 시간 복잡도 |
| :--: | :---------: |
| 평균 | O(n log n)  |
| 최선 | O(n log n)  |
| 최악 |   O(n^2)    |

<br/>

### 코드 작성을 위한 단계

1. 리스트 가운데서 하나의 요소를 골라 피벗으로 지정한다.
2. 피벗의 앞에는 피벗보다 값이 작은 요소들로, 피벗의 뒤에는 피벗보다 값이 큰 요소들이 오도록 피벗을 기준으로 리스트를 분할한다.
3. 분할된 리스트에 대해 리스트의 크기가 0이나 1이 될 때까지 재귀적으로 반복한다.

<br/>

## 코드 예시

```javascript
function quickSort(arr) {
  if (arr.length <= 1) {
    return arr;
  }

  const pivot = arr[0];
  const leftArr = [];
  const rightArr = [];

  for (let i = 1; i < arr.length; i++) {
    if (arr[i] < pivot) {
      leftArr.push(arr[i]);
    } else {
      rightArr.push(arr[i]);
    }
  }

  return [...quickSort(leftArr), pivot, ...quickSort(rightArr)];
}
```

위 방법은 메모리 공간의 낭비가 발생해 in place 방법을 쓰기도 한다.
특징으로는 추가적인 공간을 필요로 하지 않아 메모리 공간이 절약되나 중복값의 위치가 바뀔 수 있는 불안정(Unstable) 정렬이다.

```javascript
function quickSort(arr, left = 0, right = arr.length - 1) {
  if (left < right) {
    let pivotIndex = partition(arr, left, right);
    quickSort(arr, left, pivotIndex - 1);
    quickSort(arr, pivotIndex + 1, right);
  }
  return arr;
}

function partition(arr, left, right) {
  const pivot = arr[right];
  let i = left - 1;
  for (let j = left; j < right; j++) {
    if (arr[j] < pivot) {
      i++;
      [arr[i], arr[j]] = [arr[j], arr[i]];
    }
  }
  [arr[i + 1], arr[right]] = [arr[right], arr[i + 1]];
  return i + 1;
}

const list = [4, 6, 9, 1, 3, 2, 8];
console.log(quickSort(list)); // [1, 2, 3, 4, 6, 8, 9]
```

<br/>

---

참고 문서 : https://www.geeksforgeeks.org/quick-sort/
