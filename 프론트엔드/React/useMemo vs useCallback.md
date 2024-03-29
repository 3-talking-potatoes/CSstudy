# useMemo vs useCallback

<br/>

### useMemo와 useCallback의 차이를 아나요?⚡️⚡️

useMemo와 useCallback은 모두 성능 최적화를 위해 사용되는 리액트의 훅이다.
공통점으로 두 훅 모두 메모이제이션을 통해 불필요한 자식 컴포넌트의 리렌더링을 방지할 수 있다.

useMemo는 계산 결과를 캐시하여, 동일한 계산이 반복되어도 성능 저하를 막을 수 있다. useMemo는 의존성 배열을 갖고, 이 배열의 값이 변경될 때만 계산이 실행된다.

useCallback은 이벤트 핸들러나 콜백 함수 등의 함수를 메모이제이션하여, 해당 함수를 새로 생성하지 않고 이전 함수를 재사용한다. useCallback도 의존성 배열을 갖고, 이 배열의 값이 변경될 때만 새로운 함수를 생성한다.

즉, useMemo는 값을 캐시하고, useCallback은 함수를 캐시한다.  
useMemo는 계산된 결과를 재사용할 때 사용하고, useCallback은 새로운 함수를 생성하지 않고 이전 함수를 재사용할 때 사용한다.

이와 같은 훅을 사용하면 불필요한 리렌더링을 방지해 성능을 최적화할 수 있다는 장점이 있지만, 브라우저의 메모리에 함수를 저장하고 있기 때문에 훅을 무분별하게 사용하면 메모리 사용량이 비례해서 커진다는 단점이 있다.

<br/>

---
