웹은 온 디멘드 방식으로 사용자가 원하는걸 요청할 때 원하는걸 수신한다. 

## 웹 브라우저와 클라이언트

기본적으로 웹 서버는 웹 객체 데이터를 갖고있다. 

클라이언트는 HTTP 메세지에 객체 데이터에 대한 요청을 보내고 서버는 이를 받으면 HTTP 메세지에 객체 데이터를 담아서 응답으로 보낸다. 

HTTP가 TCP 프로토콜을 사용한다고 가정하면 일단 클라이언트는 서버에 TCP와 연결을 한다. 
그럼 클라이언트는 요청 메세지를 소켓 인터페이스를 이용해 서버로 보내고 서버는 응답 메세지를 마찬가지로 소켓 인터페이스를 이용해 보내게 된다. 

#### Stateless 프로토콜

HTTP는 상태를 저장하고 있지 않는다. 그래서 똑같은 요청을 바로 보낸다고 해도 서버는 다시 응답 데이터를 보내준다. 

## 비지속 연결 VS 지속 연결

### 1. 비지속 연결

클라이언트와 서버간에 응답 쌍마다 매번 다른 TCP를 연결해 보내는 방식을 의미한다. 

그래서 요청과 응답의 하나의 cycle이 완료가 되면 TCP 연결을 끊는다. 

HTTP 1.0은 이런 비지속 연결을 지원한다. 

하지만 비지속 연결의 단점은 매번 요청마다 2RTT가 소요가 되고 각 객체를 요청할 때마다 새로운 새로운 TCP 연결이되어야 한다. 
그 과정에서 네트워크 리소스의 낭비가 심해진다. 

### 2. 지속 연결

지속 연결은 HTTP/1.1 버전부터 나왔다. 
같은 클라이언트와 서버간에 한번 TCP 연결을 하면 끊지않고 통신을 하고 일정시간이 지나고 나서 TCP 연결을 끊는다.

## HTTP 포멧

### HTTP 요청 메세지

GET /somedir/page.html HTTP/1.1
Host: www.someschool.edu
Connection: close
User-agent: Mozilla/5.0
Accept-language: fr

Entity Body

- Host는 객체가 존재하는 주소를 의미한다.
- Connection을 통해 비지속, 지속 연결중에 어떤걸 원하는지 알 수 있다.
- User-agent는 서버에게 요청하는 브라우저의 타입을 명시한다.
- Accept-language는 사용자가 객체의 어떤 언어 버전을 원하는지 알 수 있는 부분이다.

### HTTP 응답 메세지

HTTP/1.1 200 OK
Connection: close
Date: Tue, 18 Aug 2015 15:44:04 GMT
Server: Apache/2.2.3 (CentOS)
Last-Modified: Tue, 18 Aug 2015 15:11:03 GMT
Content-Length: 6821
Content-Type: text/html
(data data data data data ...)