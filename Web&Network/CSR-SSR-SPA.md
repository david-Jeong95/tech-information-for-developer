# SPA 그리고 SSR과 CSR

## SPA (Single Page Application)

`SPA`란 말 그대로 한개의 페이지를 가진 어플리케이션이다.

**SPA로 개발하는 이유**

- 사용자 친화적
- 초기 렌더링 후 데이터만 받아오기 때문에, 상대적으로 서버 요청이 적음
- Virtual DOM (DOM 조작에 의한 렌더링이 비효율적이라 DOM을 추상화한 가상의 객체를 메모리에 만들어 놓는 방식)<br>
  => DOM을 반복적으로 직접 조작하면 그 만큼 브라우저가 렌더링을 자주하게 되고, 그 만큼 PC 자원을 많이 소모하게 되는 문제를 해결하기 위해서
- 프론트 엔드와 백엔드 분리로 개발업무 분업화 및 협업이 용이
- 개발이 상대적으로 효율적

기본적으로 `SPA`는 클라이언트 사이드 렌더링이지만 그렇다고 `SPA === CSR`은 아니다.

## SSR (Server Side Rendering)

`SSR`이란 서버에서 사용자에게 보여줄 페이지를 모두 구성하여 사용자에게 페이지를 보여주는 방식이다(서버에서 렌더링을 마치고, Data가 결합된 HTML 파일을 내려주는 방식).

새로운 페이지로 이동할 때마다 서버에 요청하여 페이지를 받아야 하기 때문에, 받아오는 시간동안 깜빡거리는 현상을 마주할 수 있다.

한편, SPA(Single Page Application) 기법이 대두 되면서, `CSR` 방식이 각광 받기 시작했다.

## CSR (Client Side Rendering)

`CSR` 방식은 최초 요청시에 HTML을 비롯해 CSS, JavaScript 등 각종 리소스를 받아온다. 이후에는 서버에 데이터만 요청하고, 자바스크립트로 뷰(view)를 컨트롤 한다.

당연히 초기 요청 때 `SSR`보다 많은 리소스를 요청하기 때문에, 렌더링 속도는 `SSR`이 더 빠르다. 하지만 이후 다른 페이지로의 이동시에는 `SSR`보다 빠른 페이지 전환 속도와 더 나은 사용자 경험을 제공한다.

만약 인터넷 속도가 엄청 느리다면, 유저는 제대로 된 화면을 한참 후에 만나볼 수 있을 것이다. 일단 처음 받게 될 HTML은 빈페이지이기 때문이다.

## SEO (Search Engine Optimization) 문제

리액트나 뷰를 사용하면서, `CSR`로 할지 `SSR`로 할지 고민하게 되는 이유는 SEO 때문이다.

> 렌더링 퍼포먼스 외적인 측면도 다루었다. 흔히 많이들 하는 오해가 CSR은 SEO가 잘 되지 않는다라는 것인데, 많은 크롤러들이 JavaScript를 지원하지 않기 때문에 발생한 오해다. Google Bot(크롤러)은 JavaScript를 지원하기 때문에 CSR 사이트도 SEO가 잘 된다. 특히, 최신 버전의 Google Bot은 ES2015 이상의 최신 JavaScript도 지원한다. 또한 Full SSR 없이도 메타 태그들을 잘 활용하면 SEO를 잘 지원할 수 있다.
> https://hyunseob.github.io/2019/05/26/google-io-2019-day-3/

[더 자세히 알고 싶다면](https://d2.naver.com/helloworld/7804182)
