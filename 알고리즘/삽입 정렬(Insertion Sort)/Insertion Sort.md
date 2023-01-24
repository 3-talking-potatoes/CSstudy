# 삽입 정렬(Insertion Sort)

<br>

### 삽입 정렬(Insertion Sort)

> 삽입 정렬은 각 요소를 앞에 있는 요소와 비교하여 올바른 위치에 삽입하여 최종 정렬된 배열을 만드는 간단한 정렬 알고리즘입니다.

<br/>

![이미지](https://user-images.githubusercontent.com/93918946/214071455-5ac5748d-527d-451d-835d-f481c84d7a9c.png)

<br/>

### 소개

삽입 정렬은 배열의 모든 요소를 앞에서부터 차례대로 이미 정렬된 배열 부분과 비교하여, 자신의 위치를 찾아 삽입함으로써 정렬을 완성하는 알고리즘이다. 손에 든 카드를 정렬하는 방식과 유사하게 작동하며, 퀵 정려르 합병 정렬등과 비교하여 덜 효율적이지만 버블 정렬, 선택 정렬보다는 효율적이며, 간단하게 구현 가능한 장점이 있다.

<br/>

### 시간 복잡도

| 작업 | 시간 복잡도 |
| :--: | :---------: |
| 평균 |   O(n^2)    |
| 최선 |    O(n)     |
| 최악 |   O(n^2)    |

<br/>

### 코드 작성을 위한 단계

1. 배열에서 두 번째 요소를 선택하여 시작한다.
2. 두 번째 요소를 이전 요소와 비교하고 필요한 경우 교환한다.
3. 다음 요소로 계속 진행하여 해당 요소가 올바른 위치에 있는지 확인한다. 왼쪽에 있는 정렬된 부분을 거치며 반복하여 올바른 위치에 요소를 배치한다.

<br/>

## 코드 예시

```javascript
function insertionSort(arr) {
  for (let i = 1; i < arr.length; i++) {
    let currentValue = arr[i];
    let j;
    for (j = i - 1; j >= 0 && arr[j] > currentValue; j--) {
      arr[j + 1] = arr[j];
    }
    arr[j + 1] = currentValue;
  }
  return arr;
}

insertionSort([2, 1, 9, 76, 4]);
// Output: [ 1, 2, 4, 9, 76 ]
```

<br/>

---

참고 문서 : https://www.geeksforgeeks.org/insertion-sort/
