# FLUX

<br/>

### FLUX에 대해서 아나요?⚡️⚡️

<br/>

### MVC(Model-View-Controller)

컨트롤러는 모델의 데이터를 조회하거나 업데이트 하는 역할을 하며 뷰는 모델의 변화를 반영한다. 뷰에서 사용자의 데이터 입력으로 인한 변경이 발생할 경우 모델에 영향을 준다.

![](https://taegon.kim/wp-content/uploads/2015/10/simple_mvc.png)

그러나 프로젝트 규모가 커지면서 데이터 자료의 양과 화면이 많아져 Model과 View가 급격히 늘어나고 그에 따라 각각의 모듈들이 어떤 식으로 연결되어있는지 파악하기가 어려워졌다.

![](https://taegon.kim/wp-content/uploads/2015/10/complex_mvc.png)

_이미지 출처 : https://taegon.kim/archives/5288_

### FLUX

FLUX 아키텍처는 MVC 모델의 단점을 보완하기 위해 탄생하였다. FLUX는 크게 세가지 부분으로 이루어지는데, 디스패쳐(Dispatcher), 스토어(Store), 뷰(View)이다. Dispatcher는 어플리케이션에서 발생한 action들을 정리해주는 역할을 하며 Store는 어플리케이션의 데이터들이 저장되는 장소이다.

FLUX의 특징은 데이터 단방향 흐름이다. 데이터는 항상 디스패쳐에서 스토어로, 스토어에서 뷰로 이동한다. 뷰에서 사용자의 입력이 있는 경우 뷰는 액션을 호출한다. 이러한 패턴의 가장 큰 장점은 개발 흐름이 단방향으로 흐르기 때문에 훨씬 파악하기 쉽고 코드의 흐름이 예측 가능(Predictable)하다는 것이다.

![](https://img1.daumcdn.net/thumb/R1280x0/?scode=mtistory2&fname=https%3A%2F%2Fblog.kakaocdn.net%2Fdn%2FvnHXq%2FbtqxHsrQtmH%2FwiK7j6pP0SB2waYnhZrvZ1%2Fimg.png)

_이미지 출처 : https://im-developer.tistory.com/158_
<br/>

#### 참고 블로그

> [Flux와 Redux](https://taegon.kim/archives/5288)  
> [리덕스 이해하기](https://im-developer.tistory.com/158)

---
