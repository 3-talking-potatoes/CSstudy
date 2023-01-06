# 이진 탐색(Binary Search)

<br>

### 이진 탐색(Binary Search)

> 이진 탐색은 정렬된 배열에서 검색 간격을 반복해서 반으로 나누어 탐색하는 알고리즘이다. 정렬된 배열을 사용한 이진 탐색은 기존의 선형 탐색보다 빠르게 원하는 값을 찾을 수 있어, 시간 복잡도를 O(Log n)으로 줄일 수 있다.

<br/>

![이미지](https://user-images.githubusercontent.com/93918946/210711544-65447c62-30cd-4d51-b14a-920d0feb9aa2.png)

<br/>

### 소개

이진 탐색은 N개의 요소를 가진 배열 arr[]가 주어졌을 때 필요한 요소 X를 찾는 함수이다.

<br/>

### 입출력 예시

- Input: arr[] = {10, 20, 50, 60, 80, 110, 130}, x = 110  
  Output: 6  
  설명: x 요소는 6번째 인덱스에 위치하고 있다.

- Input: arr[] = {10, 20, 40, 60, 110, 120, 130}, x = 175  
  Output: -1  
  설명: x 요소는 arr[]안에 존재하지 않는다.

<br/>

### 문제 해결을 위한 아이디어

- 전체 배열의 중간 요소를 검색 키로 시작한다.
- 검색 키의 값이 찾는 요소와 같으면 검색 키의 인덱스를 반환한다.
- 검색 키의 값이 구간 중간의 항목보다 작은 경우, 구간을 절반 아래로 좁힌다. 그렇지 않은 경우, 구간을 위쪽 절반으로 좁힌다.
- 이를 반복하여 값을 찾거나 구간이 비어있을 때까지 검색한다.

<br/>

### 코드 작성을 위한 단계

- x와 중간 요소를 비교한다.
- x가 중간 요소와 일치하면, 중간 인덱스를 반환한다.
- x가 중간 요소보다 크면, x는 중간 요소의 오른쪽 절반 서브 배열에만 있을 수 있다. 따라서 우측 절반을 재귀적으로 검색한다.
- 그렇지 않으면(x가 작으면) 왼쪽 절반을 재귀적으로 검색한다.

<br/>

## 코드 예시

이진 탐색의 재귀 구현

```javascript
function binarySearch(array, target, low = 0, high = array.length - 1) {
  if (low > high) {
    return -1;
  }

  const mid = Math.floor((low + high) / 2);
  if (array[mid] === target) {
    return mid;
  } else if (array[mid] < target) {
    return binarySearch(array, target, mid + 1, high);
  } else {
    return binarySearch(array, target, low, mid - 1);
  }
}

// 실행

const array = [1, 2, 3, 4, 5];
console.log(binarySearch(array, 3)); // Output: 2
console.log(binarySearch(array, 7)); // Output: -1
```

<br/>

반복 구현

```javascript
function binarySearch(array, target) {
  let low = 0;
  let high = array.length - 1;

  while (low <= high) {
    const mid = low + Math.floor((high - low) / 2);
    if (array[mid] === target) {
      return mid;
    } else if (array[mid] < target) {
      low = mid + 1;
    } else {
      high = mid - 1;
    }
  }

  return -1;
}

// 실행

const array = [1, 2, 3, 4, 5];
console.log(binarySearch(array, 3)); // Output: 2
console.log(binarySearch(array, 7)); // Output: -1
```

<br/>

---

참고 문서 : https://www.geeksforgeeks.org/binary-search/
