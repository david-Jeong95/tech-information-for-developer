# 브라우저로 웹 사이트에 접속할 때 과정

## 브라우저에서 [www.google.com](https://www.google.com/) 같은 웹사이트를 쳤을 때 어떠한 과정을 거쳐 페이지가 보여지는지 정리

### 요약

    1. 사용자가 브라우저에 url 입력
    2. url에서 도메인 name 부분을 DNS 서버에서 검색한다.
    3. DNS 서버에서 해당 domain name에 해당하는 ip 주소를 찾아 url 정보와 함께 전달.
    4. 웹 페이지 url 정보와 전달받은 ip 주소는 http 프로토콜을 사용해 http 요청 메세지를 생성
    5. 4번에서 생성된 http 요청 메세지를 tcp 프로토콜을 사용해 인터넷을 거쳐 ip 주소의 컴퓨터로 전송
    6. 도착한 http 요청 메세지는 http 프로토콜을 사용해 http 응답을 만든다.
    7. 만들어진 http 메시지를 다시 tcp 프로토콜을 사용해 원래 컴퓨터로 전송한다.
    8. 도착한 http 응답 메세지는 http 프로토콜을 사용해 웹 페이지 데이터로 변환
    9. 변환된 웹 페이지의 데이터는 웹 브라우저에 의해 출력된다.

### URL

위 단계에 제일 처음 등장했던 url을 설명해 보자면, 웹 브라우저는 흔히 우리가 보는 html 문서와 그림, 멀티미디어 파일 등 월드 와이드 웹을 기반으로 한 인터넷 컨텐츠를 검색 및 열람하기 위한 응용 프로그램이다. url은 Uniform Resource Locator의 약자로 파일식별자 정도로 해석할 수 있는데, 네트워크 상에 자원(파일 등)이 어디에 위치하는지를 알려주는 규칙이다. 주소에 접속하려면 url에 맞는 프로토콜을 알아야하고 동일한 프로토콜로 접속해야한다.

https://www.google.com/search?q=korea

url의 맨 첫 부분은 https, http, telnet, ftp 등이 있는데 이를 프로토콜이라 부른다.

프로토콜 이후엔 : 로 구분하고 ip 혹은 domain name 정보가 필요한 프로토콜인 경우 //를 추가해야 한다.

여기서 도메인 name은 www.google.com이고 path는 search, 쿼리는 q=korea의 형태가 된다.

### DNS

이제 dns 서버에 조회할 순서인데 dns란 ip 주소를 192.168...에서 google.com 이런 식으로 사람이 이해하기 쉽게 바꿔주는 서버를 말한다.

만약 브라우저에 캐싱된 url이면 dns 서버에 요청을 보내지 않고, 캐시되어 있지 않으면 로컬에 저장되어 있는 hosts 파일 중 참조할 수 있는 도메인이 있는지 확인

이것도 실패할 경우

    1. 사용자의 PC는 DHCP 서버에서 사용자 자신의 IP 주소, 가장 가까운 라우터의 IP 주소, 가장 가까운 DNS 서버의 IP 주소를 받는다.
    2. 이후, ARP를 이용하여 IP 주소를 기반으로 가장 가까운 라우터의 MAC 주소를 알아낸다.
    3. 외부와 통신할 준비를 마쳤으므로, DNS Query를 DNS 서버에 송신한다. DNS 서버는 이에 대한 결과로 웹 서버의 IP 주소를 사용자 PC에 돌려준다.
    4. 이제 IP를 알았으므로, HTTP Request를 위해 TCP socket을 개방하고 연결한다. (이 과정에서 3-hand-shaking이 일어난다.)
    5. TCP 연결에 성공하면 HTTP Request가 TCP Socket을 통해 보내지고, 응답으로 웹 페이지의 정보가 사용자의 PC로 들어온다.

### DHCP (Dynamic Host Configuration Protocol)

- 호스트의 IP주소 및 TCP/IP 설정을 클라이언트에 자동으로 제공하는 프로토콜

### ARP (Address Resolution Protocol)

- 네트워크 상에서 IP주소를 물리적 네트워크 주소로 대응시키기 위해 사용되는 프로토콜

### 3 Way Handshake

- TCP/IP를 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기 전에, 먼저 정확한 전송을 보장하기 위해 사전에 세션을 수립하는 과정

### 참고

[OSI 7 Layer](https://www.youtube.com/watch?v=1pfTxp25MA8&list=LL&index=1&t=2093s)
