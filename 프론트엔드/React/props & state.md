# props & state

<br/>

### props와 state의 차이⚡️

**props** : 부모 컴포넌트가 자식컴포넌트에게 주는 값, 자식 컴포넌트가 받아온 props의 값은 직접 수정할 수는 없다.  
**state** : 컴포넌트 내부에 선언, 내부에서 값 변경 가능

**props와 state의 차이** : props는 컴포넌트에 전달(함수 매개변수처럼)되는 반면, state는 컴포넌트 안에서(함수 내에 선언된 변수처럼) 관리된다.

출처 : [React-Component State](https://ko.reactjs.org/docs/faq-state.html), [velopert-props와 state](https://velopert.com/3629)

---

<br/>

### props가 컴포넌트간에 전달받는 것이라고 했는데 자식에서 부모로도 전달할 수 있나요?⚡️

함수를 사용하면 된다.

```js
// Parent.js
import React, {useState} from 'react'
import Child from './Child'

const Parent = () => {
    const [data, setData] = useState('')

    const getData = (data) => {
        setData(data) // setter 함수 전달
    }

return (
    <div>
        {data}
        <Child data={data} getData={getData}>
    </div>
)

}

```

```js
// Child.js

import React from "react";

const Child = ({ data, getData }) => {
  const onClickButton = () => {
    getData("potato");
  };
};

return (
  <div>
    <button onClick={onClickButton}>누르세요</button>
  </div>
);

export default Child;
```

출처 : [부모-자식 컴포넌트 데이터 전달](https://technicolour.tistory.com/56)

---

<br/>
