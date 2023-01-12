# 합병 정렬(Merge Sort)

<br>

### 합병 정렬(Merge Sort)

> 합병 정렬은 배열을 작은 하위 배열로 나누어 각 하위 배열을 정렬한 다음 정렬된 하위 배열을 다시 합쳐 최종 정렬된 배열을 만드는 분할 정복(Divide and Conquer) 알고리즘입니다.

<br/>

![이미지](https://user-images.githubusercontent.com/93918946/212004624-0c7f711b-a2af-477f-bab9-d79a8b53a726.png)

<br/>

### 소개

합병 정렬은 배열을 반으로 나눈 뒤, 각 배열을 정렬하고 정렬된 절반을 병합한다. 이 과정을 전체 배열이 정렬될 때까지 반복한다. 합병 정렬의 주요 이점 중 하나는 시간 복잡도가 O(n log n)이므로 큰 배열을 비교적 빠르게 정렬할 수 있다는 점이다. 또한 안정 정렬(stable sort)이므로 중복된 키 값이 있을 때 이를 순서대로 정렬한다.

<br/>

### 시간 복잡도

|   작업    | 시간 복잡도 |
| :-------: | :---------: |
| 합병 정렬 | O(n log n)  |

<br/>

### 코드 작성을 위한 단계

1. 배열이 비어있거나 하나의 요소만 있으면 이미 정렬된 것으로 본다.
2. 그렇지 않다면 배열을 절반으로 나눈다.
3. 각 부분 배열에서 재귀적으로 합병 정렬을 호출한다.
4. 다시 하나의 정렬된 배열로 합병한다.

<br/>

## 코드 예시

```javascript
function mergeSort(arr) {
  if (arr.length === 1) {
    // 배열의 항목이 하나가 되면 반환한다.
    return arr;
  }

  const middle = Math.floor(arr.length / 2);
  const left = arr.slice(0, middle);
  const right = arr.slice(middle);

  return merge(mergeSort(left), mergeSort(right));
}

// 배열을 항목별로 비교하고 합병한 결과를 반환한다.
function merge(left, right) {
  let result = [];
  let indexLeft = 0;
  let indexRight = 0;

  while (indexLeft < left.length && indexRight < right.length) {
    if (left[indexLeft] < right[indexRight]) {
      result.push(left[indexLeft]);
      indexLeft++;
    } else {
      result.push(right[indexRight]);
      indexRight++;
    }
  }

  return result.concat(left.slice(indexLeft)).concat(right.slice(indexRight));
}

const list = [2, 5, 1, 3, 7, 2, 3, 8, 6, 3];
console.log(mergeSort(list)); // [1, 2, 2, 3, 3, 3, 5, 6, 7, 8]
```

<br/>

---

참고 문서 : https://www.geeksforgeeks.org/merge-sort/
