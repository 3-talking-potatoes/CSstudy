# box model

<br/>

### box model이 무엇이며, 브라우저에서 어떻게 동작하는지 설명해주세요

> box model

모든 HTML 요소는 박스모양으로 구성되며, 이것을 박스 모델(box model)이라고 부른다.
박스 모델은 HTML 요소를 패딩(padding), 테두리(border), 마진(margin), 내용(content)로 구분한다.

1. content : 텍스트나 이미지가 들어있는 박스의 실질적 부분
2. padding : 내용과 테두리 사이 간격. 패딩은 눈에 보이지 않음
3. border : 내용과 패딩 주변을 감싸는 테두리
4. margin : 테두리와 이웃하는 요소 사이 간격. 마진은 눈에 보이지 않음

block 레벨의 엘리먼트에서는 content의 width, height 속성이 적용이 잘 되지만 inline 레벨 엘리먼트에서는 width, height 속성이 무시된다.

- block level : `<p>, <div>`, inline level : `<a>`

문서의 레이아웃 계산 시 브라우저 렌더링 엔진은 CSS 기본 박스 모델에 따라 각 요소를 사각형 박스로 표현한다.
