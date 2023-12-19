# Background: Web Browser

대표적인 소프트웨어인 **웹 브라우저(Web Browser)**에 대해 알아본다.

# 웹브라우저

웹은 인터넷이라는 글로벌 네트워크 위에 구현되어 있으며, 정해진 프로토콜을 기반으로 통신한다.  **웹 브라우저**는 서버와 HTTP 통신을 대신해주고, 수신한 리소스를 시각화하여 일반 사용자도 쉽게 사용할 수 있게 되었다.

웹 브라우저는 뛰어난 이용자 경험(User eXperience, UX)을 제공하는 소프트웨어다. 이용자는 브라우저를 이용하여 쉽게 정보를 검색하고, 동영상을 보고, 파일을 내려받지만 내부에서 어떠한 연산이 일어나는지는 전혀 알지 못한다.

해당 그림은 이용자가 주소창에 `dreamhack.io`를 입력했을 때 웹 브라우저가 하게 되는 기본적인 동작을 나열한 것이다.

1. 웹 브라우저의 주소창에 입력된 주소를 해석 (URL 분석)
2. `dreamhack.io`에 해당하는 주소 탐색 (DNS 요청)
3. HTTP를 통해 `dreamhack.io`에 요청
4. `dreamhack.io`의 HTTP 응답 수신
5. 리소스 다운로드 및 웹 렌더링 (HTML, CSS, Javascript)
    
    ![18b4420593d315da2369a04ecb429034ca8b6b39292b25aa1eef66d2a9573b73.png](Background%20Web%20Browser%20f9b223d3732944bc86316edeba4168c6/18b4420593d315da2369a04ecb429034ca8b6b39292b25aa1eef66d2a9573b73.png)
    

최근에는 브라우저가 보안과 개발에 필요한 다양한 도구들도 제공하고 있다. HTTPS의 적용 여부 및 서버 인증서의 안전성 여부를 식별해주는 것이 있다.

[안전한 인증서]

![b463256c0ea2d3491039d560f3c315d6b944a81b8d875d31cbfdab31e83f762f.png](Background%20Web%20Browser%20f9b223d3732944bc86316edeba4168c6/b463256c0ea2d3491039d560f3c315d6b944a81b8d875d31cbfdab31e83f762f.png)

[안전하지 않은 인증서]

![452197b0adf3afca87de0ab658c2992140329775bb610c665369b206bfb90aee.png](Background%20Web%20Browser%20f9b223d3732944bc86316edeba4168c6/452197b0adf3afca87de0ab658c2992140329775bb610c665369b206bfb90aee.png)

# URL

**URL**은 Uniform Resource Locator의 약자로, 웹에 있는 리소스의 위치를 표현하는 문자열이다. 브라우저로 특정 웹 리소스에 접근할 때는, URL을 사용하여 이를 서버에게 요청한다. 다음은 URL의 예시입니다.

![02d5bc932cca5c42b6a1e07723951a19e9f7e60859e3bd7476e7384a4c9ce863.png](Background%20Web%20Browser%20f9b223d3732944bc86316edeba4168c6/02d5bc932cca5c42b6a1e07723951a19e9f7e60859e3bd7476e7384a4c9ce863.png)

URL은 Scheme, Authority (Userinfo, Host, Port), Path, Query, Fragment 등으로 구성된다. 이 중 자주 사용되는 요소는 다음과 같다.

| 요소 | 설명 |
| --- | --- |
| Scheme | 웹 서버와 어떤 프로토콜로 통신할지 나타낸다. |
| Host | Authority의 일부로, 접속할 웹 서버의 주소에 대한 정보를 가지고 있다. |
| Port | Authority의 일부로, 접속할 웹 서버의 포트에 대한 정보를 가지고 있다. |
| Path | 접근할 웹 서버의 리소스 경로로 '/'로 구분된다. |
| Query | 웹 서버에 전달하는 파라미터이며 URL에서 '?' 뒤에 위치한다. |
| Fragment | 메인 리소스에 존재하는 서브 리소스를 접근할 때 이를 식별하기 위한 정보를 담고 있다. '#' 문자 뒤에 위치한다. |

# ****Domain Name****

URL 구성 요소 중 Host는 웹 브라우저가 접속할 웹 서버의 주소를 나타낸다. Host는 **Domain Name**, **IP** **Address**의 값을 가질 수 있다. IP Address는 네트워크상에서 통신이 이루어질 때 장치를 식별하기 위해 사용되는 주소이다. 불규칙한 숫자로 이루어진 IP Address는 사람이 외우기 어려우므로, 일반적으로는 도메인의 특성을 담은 이름을 정의하여 IP 대신 사용한다.

Domain Name을 Host 값으로 이용할 때, 브라우저는 **Domain Name Server(DNS)**에 Domain Name을 질의하고, DNS가 응답한 IP Address를 사용한다. 예를 들어, 웹 브라우저에서 `http://example.com`에 접속할 경우, DNS에 질의해 얻은 `example.com`의 IP와 통신한다.

Domain Name에 대한 정보는 MacOS/Linux/Windows에서 `nslookup` 명령어를 사용해 확인할 수 있다.

```html
$ nslookup example.com
Server:		8.8.8.8
Address:	8.8.8.8#53

Non-authoritative answer:
Name:	example.com
Address: 93.184.216.34
```

# 웹 렌더링

**웹 렌더링(Web Rendering)**은 서버로부터 받은 리소스를 이용자에게 시각화하는 행위를 말한다. 서버의 응답을 받은 웹 브라우저는 리소스의 타입을 확인하고, 적절한 방식으로 이용자에게 전달한다. 예를 들어, 서버로부터 HTML과 CSS를 받으면 브라우저는 HTML을 파싱하고 CSS를 적용하여 이용자에게 보여준다.

웹 렌더링은 웹 렌더링 엔진에 의해서 이뤄지는데, 브라우저별로 서로 다른 엔진을 사용한다. 사파리는 **웹킷(Webkit)**, 크롬은 **블링크(Blink)**, 파이어폭스는 **개코(Gecko)** 엔진을 사용한다. 각각의 엔진에 따라 렌더링 과정과 순서, 속도의 차이는 있지만, HTML을 파싱하고 시각화하여 이용자에게 보여주는 것은 같다.