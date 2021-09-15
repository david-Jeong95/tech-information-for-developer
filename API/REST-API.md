# REST API란?

**어떤 제품이나 기술이 아닌 형식이다.**

## API란

Aplication Programming Interface

소프트웨어가 다른 소프트웨어로부터(ex.클라이언트가 서버로부터) 지정된 형식으로 요청, 명령을 받을 수 있는 수단

## REST API

**REST한 형식의 API = RESTful한 API**

REST(Representational State Transfer)

과거의 SOAP(Simple Object Access Protocol)이란 복잡한 형식을 대체한 것

SOAP는 World Wide Web Consortium(W3C)에서 유지관리하는 다른 언어로 다른 플랫폼에서 빌드된 어플리케이션이 통신할 수 있도로고 설계된 최초의 표준 프로토콜이지만,</br>
REST는 프로토콜이 아니라는 점이 주요 차이점이다.

클라이언트, 서버, 리소스로 구성된 클라이언트-서버 아키텍처가 필요하다.

## 가장 중요한 특성

- 각 요청이 어떤 동작이나 정보를 위한 것인지를 그 요청의 모습 자체로 추론 가능</br>
  => 요청을 보내는 주소만으로도 대략 이게 무엇을 하는 요청인지 파악 가능해야 함

EX).

- https://(도메인)/**classes** : 학원의 반들 목록을 받아오는 요청</br>

```js
 {"result" :[
     {"idx": 1, "name": "예비반"},
     {"idx": 2, "name": "초급반"},
     {"idx": 3, "name": "중급반"},
     ]
 }
```

- https://(도메인)/**classes**/**2** : 그 뒤에 idx, 고유번호의 숫자인 반의 정보 요청</br>

```js
 {"result" :[

     {"idx": 2, "name": "초급반"},

     ]
 }
```

- https://(도메인)/**classes**/**2**/**students?page=2&count=10** : 한 페이지에 10명씩 받아오는 정보</br>

```js
 {"result" :[
     {"idx": 1, "name": "최길동"},
     {"idx": 2, "name": "송하나"},
     {"idx": 3, "name": "정현우"},
     ...
     ]
 }
```

**자원을 구조와 함께 나타내는 이런 식의 구문자를 URI라고 한다.**

**조회 작업뿐만이 아니라 정보를 수정하거나 삭제하는 작업도 필요**

=> CRUD 라고 부름 (Create: 생성, Read: 조회, Update: 수정, Delete: 삭제)

**서버에 REST API로 요청을 보낼 때 HTTP란 규약에 따라 신호를 전송한다.**

**HTTP의 다양한 메소드들 중에 4가지 혹은 5가지(GET, POST, PUT, DELETE, PATCH)를 사용한다.**

- GET : 데이터를 Read 조회하는데 사용
- POST : 데이터를 Create, 새로운 정보를 추가하는데 사용
- PUT, PATCH : 데이터를 Update, 기존의 데이터 변경하는데 사용 (PUT은 정보를 통째로, PATCH는 일부분)
- DELETE : 데이터를 Delete, 데이터를 삭제하는데 사용

POST, PUT, PATCH는 BODY라는 곳에 GET, DELETE보다 더 많은 정보를 비교적 안전하게 감춰서 실어보낼 수 있다.

**URI는 동사가 아닌 명사들로 이뤄져야 한다.**

## 즉, REST API란 HTTP 요청을 보낼 때, 어떤 URI에 어떤 메소드를 사용할지 개발자들 사이에 널리 지켜지는 약속이다.
