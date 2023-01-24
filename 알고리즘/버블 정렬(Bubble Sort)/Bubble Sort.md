# 버블 정렬(Bubble Sort)

<br>

### 버블 정렬(Bubble Sort)

> 버블 정렬은 정렬되지 않은 배열을 반복적으로 두 요소끼리 비교 후 교환하는 작업을 거쳐 정렬하는 알고리즘입니다.

<br/>

![이미지](https://user-images.githubusercontent.com/93918946/214052895-617a75eb-c389-4740-8114-d00262720ce4.jpg)  
참고 문서 : https://www.lavivienpost.net/bubble-sort-two-solutions/

<br/>

### 소개

버블 정렬은 배열을 오름차순으로 정렬하는 알고리즘으로, 인접한 두 요소를 비교하여 교환하는 작업을 거쳐 배열을 정렬하는 알고리즘이다. 요소의 이동이 거품이 수면으로 올라오는 듯한 모습을 보인다 하여 지어진 이름이다.

<br/>

### 시간 복잡도

| 작업 | 시간 복잡도 |
| :--: | :---------: |
| 평균 |   O(n^2)    |
| 최선 |    O(n)     |
| 최악 |   O(n^2)    |

<br/>

### 코드 작성을 위한 단계

1. 배열의 끝에서부터 i라는 변수를 사용해 배열의 처음을 향해 반복문을 시작한다.
2. j라는 변수로 배열의 처음부터 i-1 까지 내부 반복문을 시작한다.
3. arr[j]가 arr[j+1]보다 크면, 두 값을 교환한다.
4. 정렬된 배열을 반환한다.

<br/>

## 코드 예시

```javascript
function bubbleSort(arr) {
  let noSwaps;
  for (let i = arr.length; i > 0; i--) {
    noSwaps = true;
    for (let j = 0; j < i - 1; j++) {
      if (arr[j] > arr[j + 1]) {
        let temp = arr[j];
        arr[j] = arr[j + 1];
        arr[j + 1] = temp;
        noSwaps = false;
      }
    }
    if (noSwaps) break;
  }
  return arr;
}

bubbleSort([8, 1, 2, 3, 4, 5, 6, 7]);
// Output: [1, 2, 3, 4, 5, 6, 7, 8]
```

<br/>

---
