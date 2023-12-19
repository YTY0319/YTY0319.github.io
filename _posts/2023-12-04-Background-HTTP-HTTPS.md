# Background: HTTP/HTTPS

# HTTP

HTTP(Hyper Text Transfer Protocol)

서버와 클라이언트의 데이터 교환을 요청과 응답형식으로 정의한 프로토콜

**네트워크 포트(Network Port) :** 네트워크에서 서버와 클라이언트가 정보를 교환하는 추상화된 장소를 의미한다.

**서비스 포트(Service Port) :** 네트워크 포트 중에서 특정 서비스가 점유하고 있는 포트 HTTP가 80번 포트를 점유하고 있다면 HTTP의 서비스 포트는 80번 포트이다.

포트로 데이터를 교환하는 방식은 **전송 계층(Transport Layer)**의 프로토콜을 따른다. 대표적으로는 TCP와 UDP가 있다.

TCP로 데이터를 전송하려는 서비스에 UDP 클라이언트가 접근하면, 데이터가 교환되지 않는다. 그래서 서비스 포트를 표기할 때는 서비스가 사용하는 전송 계층 프로토콜을 같이 표기하기도 한다.

포트의 개수는 운영체제에서 정의하기 나름인데, 현대에는 65536개의 포트가 일반적으로 사용되며 0번 부터 1023번 포트는 잘 알려진 포트(Well-known port) 또는 특권 포트(Privileged port)라고 한다.문자 그대로 각 포트 번호에 유명한 서비스가 등록되어 있다.

# HTTP 메시지

HTTP 메시지에는 요청과 응답이 있는데 기능과 세부 구조에서는 차이가 있지만 크게보면 모두 HTTP 헤드와 바디로 구성된다는 공통점이 있다.

## HTTP 헤드

HTTP 헤드의 각 줄은 CRLF로 구분되며, 첫 줄은 시작 줄(Start-line), 나머지 줄은 헤더(Header)라고 부른다. 헤드의 끝은 CRLF 한 줄로 나타낸다.

시작줄은 요청과 응답간의 큰 차이가 있다.

헤더는 필드와 값으로 구성되며 HTTP 메시지 또는 바디의 속성을 나타낸다. 하나의 HTTP 메시지에는 0개 이상의 헤더가 있을 수 있다.

### **HTTP 바디**

HTTP 바디는 헤드의 끝을 나타내는 CRLF 뒤, 모든 줄을 말합니다. 클라이언트나 서버에게 전송하려는 데이터가 바디에 담깁니다.

CRLF : *Carriage Return (CR)와 Line Feed (LF) 캐리지 리턴과 라인피드 \r\n*

![4434bb5d339e95b7b64167b98571114c011e88bf05143422aa272b8bd943bba2.png](Background%20HTTP%20HTTPS%204d015f7d2d3840ecaa21e6107cc45db7/4434bb5d339e95b7b64167b98571114c011e88bf05143422aa272b8bd943bba2.png)

# HTTP 요청

**HTTP** 요청은 서버에게 특정 동작을 요구하는 메시지이다. 서버는 해당 동작이 실현 가능한지, 클라이언트가 그러한 동작을 요청할 권한이 있는지 등을 검토하고, 적절할 때만 이를 처리한다.

### **시작 줄**

HTTP 요청의 시작 줄은 메소드(Method), 요청 URI(Request-URI), 그리고 HTTP 버전으로 구성된다. 각각은 띄어쓰기로 구분.

**메소드**는 URI가 가리키는 리소스를 대상으로, 서버가 수행하길 바라는 동작을 나타낸다. HTTP 표준에 정의된 메소드는 8개이나, 비교적 자주 사용되는 GET과 POST 메소드만 설명한다.

먼저 GET은 리소스를 가져오라는 메소드입니다. 새로운 페이지를 렌더링하기 위해서는 리소스가 필요하다. 이때 브라우저는 GET 요청을 서버에 전송하여 리소스를 받아온다. 반대로, POST는 리소스로 데이터를 보내라는 메소드이다. 전송할 데이터는 보통 HTTP 바디에 포함된다. 로그인할 때 입력하는 ID와 비밀번호, 게시판에 작성하는 글 등이 POST로 서버에 보내진다.

이 외에 **요청 URI**는 메소드의 대상을, **HTTP** **버전**은 클라이언트가 사용하는 HTTP 프로토콜의 버전을 나타냅니다.

```html
GET /index.html HTTP/1.1 //메소드, 요청 URI, HTTP 버전 
Host: dreamhack.io
Connection: keep-alive
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10_14_6) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/79.0.3945.88 Safari/537.36
```

# HTTP 응답

**HTTP 응답**은 HTTP 요청에 대한 결과를 반환하는 메시지이다. 요청을 수행했는지, 하지 않았는지, 안 했다면 이유는 무엇인지와 같은 상태 정보(Status), 그리고 클라이언트에게 전송할 리소스가 응답에 포함된다.

### **시작 줄**

HTTP 응답의 시작 줄은 HTTP 버전, 상태 코드(Status Code), 그리고 처리 사유(Reason Phrase)로 구성됩니다. 각각은 띄어쓰기로 구분된다.

```html
HTTP/1.1 200 OK Server: Apache/2.4.29 (Ubuntu) //HTTP 버전, 상태코드, 처리사유
Content-Length: 61
Connection: Keep-Alive
Content-Type: text/html

<!doctype html>
<html>
<head>
</head>
<body>
</body>
</html>
```

**HTTP 버전**은 서버에서 사용하는 HTTP 프로토콜의 버전을 나타낸다. 그리고 **상태 코드**는 요청에 대한 처리 결과를 세 자릿수로 나타냅니다. HTTP 표준인 [RFC 2616](https://www.rfc-editor.org/rfc/rfc2616.html#section-6)은 대략 40여개의 상태 코드를 정의하고 있는데, 각각은 첫 번째 자릿수에 따라 5개의 클래스로 분류됩니다. **처리 사유**는 상태 코드가 발생한 이유를 짧게 기술한 것이다.

| 상태코드 | 설명 | 예시 |
| --- | --- | --- |
| 1xx | 요청을 제대로 받았고, 처리가 진행중 |  |
| 2xx | 요청이 제대로 처리됨 | 200(ok) 성공 |
| 3xx | 요청을 처리하려면 클라이언트가 추가 동작을 취해야 함 | 302(found) 다른 URL로 갈것 |
| 4xx | 클라이언트가 잘못된 요청을 보내어 처리에 실패 | 400(Bad Request): 요청이 문법에 맞지 않음

401(Unauthorized): 클라이언트가 요청한 리소스에 대한 인증이 실패함

403(Forbidden): 클라이언트가 리소스에 요청할 권한이 없음

404(Not Found): 리소스가 없음 |
| 5xx | 클라이언트의 요청은 유효하지만 서버에 에러가 발생하여 처리에 실패 | 500(Internal Server Error): 서버가 요청을 처리하다가 에러가 발생함

503(Service Unavailable): 서버가 과부하로 인해 요청을 처리할 수 없음 |

# HTTPS

HTTP의 응답과 요청은 평문으로 전달된다. 만약 누군가 이를 가로챈다면 중요한 정보가 유출될 수 있다. 로그인할 때 전송한 POST 요청에는 대개 이용자의 ID와 비밀번호가 포함된다. 공격자가 중간에 이를 가로채면 이용자의 계정이 탈취당할 수 있다.

**HTTPS(HTTP over Secure socket layer)**는 TLS(Transport Layer Security) 프로토콜을 도입하여 이런 문제점을 보완다. TLS는 서버와 클라이언트 사이에 오가는 모든 HTTP 메시지를 암호화한다. 공격자가 중간에 메시지를 탈취하더라도 이를 해석하는 것은 불가능하며, 결과적으로 HTTP 통신이 도청과 변조로부터 보호된다.

해당 사진은 HTTP 및 HTTPS의 웹 서버와 오가는 메시지를 Wireshark로 확인한 것이다. HTTP 메시지는 쉽게 읽을 수 있지만, HTTPS의 것은 해석할 수 없다.

HTTPS가 제정된 초기에는 금융이나 정부 서비스와 같이 민감한 데이터를 취급하는 웹 서비스들 위주로 HTTPS가 사용되었다. 그러나 현재 개발되는 서비스들은 규모에 상관없이 HTTPS를 사용하는 추세다.

[HTTP의 메시지]

![HTTP](Background%20HTTP%20HTTPS%204d015f7d2d3840ecaa21e6107cc45db7/369350834d418aeb2e990142b6179b8ad90de214b466740dffc673f31c34c75d.png)

HTTP

[HTTPS의 메시지]

![HTTPS](Background%20HTTP%20HTTPS%204d015f7d2d3840ecaa21e6107cc45db7/2c0508f521f62664c3f9250e36033c271ff5e22efdac6260c30e06e2c8383f4e.png)

HTTPS

**TLS 표준**

TLS를 잘 이해하려면 TLS의 기반이 되는 공개 키 암호 시스템(Public Key Crypto Standard, PKCS) 및 대칭 키 암호(Symmetric Key Cryptography)을 알아야 한다.