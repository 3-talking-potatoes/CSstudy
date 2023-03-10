# attribute vs property

### attribute와 property 의 차이점은 무엇인가요?

</br>

attribute는 **HTML 문서**에서 element에 추가적인 정보를 넣을 때 사용되는 **정적**인 요소이다.

```javascript
<div class="star"></div>
```

1. div는 element(요소)
2. class는 attribute
3. star는 class attribute의 value

property는 **HTML DOM**에서 attribute를 가리키는 **동적**인 요소이다. JavaScript는 정적인 문서인 HTML을 동적으로 동작하게 하는데, 그러한 동적인 속성을 부여하는 것이 property이다.

`<div class="star"></div>`를 DOM으로 표현하면

```javascript
Our DIV node
 | - nodeName = "DIV"
 | - className = "star"
 | - style
 ...
```

여기서 className이 property이다. HTML 문서 안에서 class는 attribute를 의미하지만 HTML DOM 안에서는 property를 의미한다고 볼 수 있다.

attribute는 HTML 문서에, property는 HTML DOM tree에 존재한다. attribute는 정적이며 변하지 않고 property는 동적으로 그 값이 변할 수 있다. 예를 들어 체크박스 태그가 있을 때 체크박스에 체크를 하면 attribute의 상태는 변하지 않지만 property의 상태는 checked로 변한다.

#### 참고 표

| attribute | property |
| --------- | -------- |
| HTML 문서 | HTML DOM |
| 정적      | 동적     |

#### 참고 사이트

> [attribute와 property의 차이점](https://velog.io/@kysung95/%EC%A7%A4%EB%A7%89%EA%B8%80-attribute%EC%99%80-property%EC%9D%98-%EC%B0%A8%EC%9D%B4%EC%A0%90)  
> [[DOM] attribute 와 property 차이](https://inpa.tistory.com/entry/JS-%F0%9F%93%9A-DOM-attribute-%EC%99%80-property-%EC%B0%A8%EC%9D%B4)
