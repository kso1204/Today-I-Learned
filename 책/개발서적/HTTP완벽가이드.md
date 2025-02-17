# HTTP

1. HTTP 개관

- 대부분의 URL은 세 부분으로 이루어진 표준 포맷을 따른다.
- URL의 첫 번째 부분은 스킴이라고 불리는데, 리소스에 접근하기 위해 사용되는 프로토콜을 서술한다. 보통 HTTP 프로토콜(http://)이다.
- 두 번째 부분은 서버의 인터넷 주소를 제공한다. (예: www.joes-hardware.com)
- 마지막은 웹 서버의 리소스를 가리킨다 (예: /specials/saw-blade.gif)
- 오늘날 대부분의 URI는 URL이다.
- HTTP 트랜잭션은 요청 명령(클라이언트에서 서버로 보내는)과 응답 결과(서버가 클라이언트에게 돌려주는)로 구성되어 있다.
- HTTP는 네트워크 통신의 핵심적인 세부사항에 대해서 신경 쓰지 않는다.
- 대신 대중적이고 신뢰성 있는 인터넷 전송 프로토콜인 TCP/IP에게 맡긴다.
- TCP는 다음을 제공한다.
- 오류 없는 데이터 전송
- 순서에 맞는 전달(데이터는 언제나 보낸 순서대로 도착한다.)
- 조각나지 않는 데이터 스트림(언제든 어떤 크기로든 보낼 수 있다.)

```

HTTP - 애플리케이션 계층

TCP - 전송 계층

IP - 네트워크 계층

네트워크를 위한 링크 인터페이스 - 데이터 계층

물리적인 네트워크 하드웨어 - 물리 계층

HTTP 네트워크 프로토콜 스택

```

- URL 예:

```

http://207.200.83.29:80/index.html

http://www.netscape.com:80/index.html

http://www.netscape.com/index.html

첫 번째 URL은 IP 주소 '207.200.83.29' 와 포트번호 '80'을 갖고 있다.

두 번째 URL에는 숫자로 된 IP 주소가 없다. 대신 글자로 된 도메인 이름 혹은 호스트 명 ("www.netscape.com")을 갖고 있다.

호스트 명은 IP 주소에 대한 이해하기 쉬운 형태의 별명이다.

호스트 명은 도메인 이름 서비스(Domain Name Service, DNS)라 불리는 장치를 통해 쉽게 IP로 변환될 수 있다.

```


- HTTP 클라이언트가 서버에 메시지를 전송할 수 있게 되기 전에, 인터넷 프로토콜(Internet Protocol, IP) 주소와 포트번호를 사용해 클라이언트와 서버 사이에 TCP/IP 커넥션을 맺어야 한다.
- 웹 브라우저가 어떻게 HTTP를 이용해서 멀리 떨어진 곳에 있는 서버의 단순한 HTML 리소스를 사용자에게 보여주는지? - 15Page

```

웹브라우저는 서버의 URL에서 호스트 명을 추출한다.

웹브라우저는 서버의 호스트 명을 IP로 변환한다.

웹브라우저는 URL에서 포트번호(있다면)를 추출한다.

웹브라우저는 웹 서버와 TCP 커넥션을 맺는다.

웹브라우저는 서버에 HTTP 요청을 보낸다.

서버는 웹브라우저에 HTTP 응답을 돌려준다.

커넥션이 닫히면, 웹브라우저는 문서를 보여준다.

```

- 웹의 구성요소 
- 프락시 - 클라이언트와 서버 사이에 위치한 HTTP 중개자
- 캐시 - 많이 찾는 웹페이지를 클라이언트 가까이에 보관하는 HTTP 창고
- 게이트웨이 - 다른 애플리케이션과 연결된 특별한 웹 서버
- 터널 - 단순히 HTTP 통신을 전달하기만 하는 특별한 프락시
- 에이전트 - 자동화된 HTTP 요청을 만드는 준지능적 웹클라이언트

2. URL과 리소스

- URL은 브라우저가 정보를 찾는데 필요한 리소스의 위치를 가리키며, URL을 이용해 사람과 애플리케이션이 인터넷상의 수십억 개의 리소스를 찾고 사용하며 공유 할 수 있다.
- URL은 통합 자원 식별자 (Uniform Resource Identifter, URI) 라고 불리는 더 일반화된 부류의 부분집합이다.
- 대부분의 URL은 동일하게 '스킴://서버위치/경로' 구조로 이루어져 있다.
- 상대 참조 해석하기 P39
- 기저(base)URL 과 절대 URL

3. HTTP 메시지

- 메시지는 원 서버 방향을 인바운드로 하여 송신된다.
- HTTP는 인바운드와 아웃바운드라는 용어를 트랜잭션 방향을 표현하기 위해 사용한다.
- 메시지가 원 서버로 향하는 것은 인바운드로 이동하는 것이고, 모든 처리가 끝난 뒤에 메시지가 사용자 에이전트로 돌아오는 것은 아웃바운드로 이동하는 것이다.
- 메시지는 시작줄, 헤더 블록, 본문 이렇게 세 부분으로 이루어진다.
- 시작줄과 헤더는 그냥 줄 단위로 분리된 아스키 문자열이다.
- 각 줄은 캐리지 리턴과 개행 문자로 구성된 두 글자의 줄바꿈 문자열로 끝난다.
- 이 줄바꿈 문자열은 'CRLF'라고 쓴다.
- HTTP 요청 메시지는 명령과 URL을 포함한다.
- HTTP 응답 메시지는 트랜잭션의 결과를 포함한다.
- 모든 HTTP 메시지는 시작줄로 시작한다. 요청 메시지의 시작줄은 무엇을 해야 하는지 말해준다. 응답 메시지의 시작줄은 무슨 일이 일어났는지 말해준다.
- 요청 메시지는 서버에게 리소스에 대해 무언가를 해달라고 부탁한다. 요청 메시지의 시작줄, 혹은 요청줄에는 서버에서 어떤 동작이 일어나야 하는지 설명해주는 메서드와 그 동작에 대한 대상을 지칭하는 요청 URL이 들어있다.
- 응답 메시지는 수행 결과에 대한 상태 정보와 결과 데이터를 클라이언트에게 돌려준다. 응답 메시지의 시작줄 혹은 응답줄에는 응답 메시지에서 쓰인 HTTP의 버전, 숫자로 된 상태 코드, 수행 상태에 대해 설명해주는 텍스트로 된 사유 구절이 들어있다.
- 메서드
- 요청의 시작줄은 메서드로 시작하며, 서버에게 무엇을 해야 하는지 말해준다. P55 메서드

```

메서드 - 설명 - 메시지 본문이 있는가?

GET - 서버에서 어떤 문서를 가져온다 - 없음

HEAP - 서버에서 어떤 문서에 대한 헤더만 가져온다 - 없음

POST - 서버가 처리해야 할 데이터를 보낸다 - 있음

PUT - 서버에 요청 메시지의 본문을 저장한다 - 있음

TRACE - 메시지가 프락시를 거쳐 서버에 도달하는 과정을 추적한다 - 없음

OPTIONS - 서버가 어떤 메서드를 수행할 수 있는지 확인한다 - 없음

DELETE - 서버에서 문서를 제거한다 - 없음

```

4. 커넥션 관리

- TCP 커넥션 P86
- 신뢰할 수 있는 데이터 전송 통로인 TCP
- TCP 스트림은 세그먼트로 나뉘어 IP 패킷을 통해 전송된다.
- TCP는 IP 패킷(혹은 IP 데이터그램)이라고 불리는 작은 조각을 통해 데이터를 전송한다.

```

1. HTTP

HTTP 애플리케이션 계층

TCP 전송 계층

IP 네트워크 계층

Network Interface 데이터 링크 계층

2. HTTPS

HTTP 애플리케이션 계층

TLS or SSL 보안 계층

TCP 전송 계층

IP 네트워크 계층

Network Interface 데이터 링크 계층

```

- HTTP가 메시지를 전송하고자 할 경우, 현재 연결되어 있는 TCP 커넥션을 통해 메시지 데이터의 내용을 순서대로 보낸다.
- TCP는 세그먼트라는 단위로 데이터 스트림을 잘게 나누고, 세그먼트를 IP 패킷이라고 불리는 봉투에 담아서 인터넷을 통해 데이터를 전달한다.
- 각 TCP 세그먼트는 하나의 IP 주소에서 다른 IP 주소로 IP 패킷에 담겨 전달된다.
- 이 IP 패킷들 각각은 다음을 포함한다.

```

IP 패킷 헤더 (보통 20바이트)

TCP 세그먼트 헤더 (보통 20바이트)

TCP 데이터 조각(0혹은 그 이상의 바이트)

```

- IP 헤더는 발신지와 목적지 IP 주소, 크기, 기타 플래그를 가진다.
- TCP 세그먼트 헤더는 TCP 포트번호, TCP 제어 플래그, 그리고 데이터의 순서와 무결성을 검사하기 위해 사용되는 숫자 값을 포함한다.
- 컴퓨터는 항상 TCP 커넥션을 여러 개 가지고 있다. TCP는 포트 번호를 통해서 이런 여러 개의 커넥션을 유지한다.
- 포트 번호는 회사 직원의 내선전화와 같다.
- 회사의 대표전화번호는 안내 데스크로 연결되고 내선전화는 해당 직원으로 연결되듯이 IP 주소는 해당 컴퓨터에 연결되고 포트 번호는 해당 애플리케이션으로 연결된다.
- TCP 커넥션은 네 가지 값으로 식별한다.
- <발신지IP주소, 발신지 포트, 수신지 IP주소, 수신지 포트>
- 이 네 가지 값으로 유일한 커넥션을 생성한다.
- 서로 다른 두 개의 TCP 커넥션은 네 가지 주소 구성요소의 값이 모두 같을 수 없다.
- TCP 소켓 프로그래밍
- 운영체제는 TCP 커넥션의 생성과 관련된 여러 기능을 제공한다.

```

소켓 API 호출 - 설명

s = socket(<parameters>) - 연결이 되지 않은 익명의 새로운 소켓 생성

bind(s, <local IP:Port>) -  소켓에 로컬 포트 번호와 인터페이스 할당

connect(s, <remote IP:port>) - 로컬의 소켓과 원격의 호스트 및 포트 사이에 TCP 커넥션 생성

listen(s, ...) - 커넥션을 받아들이기 위해 로컬 소켓에 허용함을 표시

s2 = accept(s) - 누군가 로컬 포트에 커넥션을 맺기를 기다림

n = read(s, buffer, n) - 소켓으로부터 버퍼에 n바이트 읽기 시도

n = write(s, buffer, n) - 소켓으로부터 버퍼에 n바이트 쓰기 시도

close(s) - TCP 커넥션을 완전히 끊음

shutdown(s, <side>) - TCP 커넥션의 입출력만 닫음

getsockopt(s, ...) - 내부 소켓 설정 옵션값을 읽음

setsockopt(s, ...) - 내부 소켓 설정 옵션값을 변경

```

- TCP 커넥션 핸드셰이크 지연
- TCP 커넥션이 핸드 셰이크를 하는 순서

```

1. 클라이언트는 새로운 TCP 커넥션을 생성하기 위해 작은 TCP 패킷을 서버에 보낸다.

그 패킷은 'SYN'라는 특별한 플래그를 가지는데, 이 요청이 커넥션 생성 요청이라는 뜻이다.

2. 서버가 그 커넥션을 받으면 몇 가지 커넥션 매개변수를 산출하고, 커넥션 요청이 받아들여졌음을 의미하는 'SYN'과 'ACK' 플래그를 포함한 TCP 패킷을 클라이언트에게 보낸다.

3. 마지막으로 클라이언트는 커넥션이 잘 맺어졌음을 알리기 위해서 서버에게 다시 확인응답('ACK') 신호를 보낸다.

```

- 결국, 크기가 작은 HTTP 트랜잭션은 50% 이상의 시간을 TCP를 구성하는 데 쓴다.
- 이후에 이러한 TCP 구성으로 인한 지연을 제거하기 위해서 HTTP가 이미 존재하는 커넥션을 어떻게 재활용하는지 알아볼 것이다.
- 확인응답 지연
- 인터넷 자체가 패킷 전송을 완벽히 보장하지는 않기 때문에, TCP는 성공적인 데이터 전송을 보장하기 위해서 자체적인 확인 체계를 가진다.
- 각 TCP 세그먼트는 순번과 데이터 무결성 체크섬을 가진다.
- TCP 느린 시작(slow start)
- TCP 커넥션은 시간이 지나면서 자체적으로 '튜닝'되어서, 처음에는 커넥션의 최대 속도를 제한하고 데이터가 성공적으로 전송됨에 따라서 속도 제한을 높여나간다.
- 이렇게 조율하는 것은 TCP 느린시작이라고 부르며, 이는 인터넷의 급자스러운 부하와 혼잡을 방지하는 데 쓰인다.
- 네이글(Nagle) 알고리즘과 TCP_NODELAY
- 애플리케이션이 어떤 크기의 데이터든지(심지어 1바이트라도) TCP 스택으로 전송할 수 있도록, TCP는 데이터 스트림 인터페이스를 제공한다.
- 하지만 각 TCP 세그먼트는 40바이트 상당의 플래그와 헤더를 포함하여 전송하기 때문에, TCP가 작은 크기의 데이터를 포함한 많은 수의 패킷을 전송한다면 네트워크 성능은 크게 떨어진다.
- 네이글 알고리즘은 세그먼트가 최대 크기(패킷의 최대 크기는 LAN상에서 1,500 바이트 정도, 인터넷상에서는 수백 바이트 정도다)가 되지 않으면 전송을 하지 않는다.
- 다만 다른 모든 패킷이 확인응답을 받았을 경우에는 최대 크기보다 작은 패킷의 전송을 허락한다.
- 네이글 알고리즘은 HTTP 성능 관련해 여러 문제를 발생시킨다. HTTP 애플리케이션은 성능 향상을 위해서 HTTP 스택에 TCP_NODELAY 파라미터 값을 설정하여 네이글 알고리즘을 비활성화하기도 한다.
- TIME_WAIT의 누적과 포트 고갈
- TCP 커넥션의 종단에서 TCP 커넥션을 끊으면, 종단에서는 커넥션의 IP 주소와 포트 번호를 메모리의 작은 제어영역에 기록해 놓는다.
- 이 정보는 같은 주소와 포트 번호를 사용하는 새로운 TCP 커넥션이 일정 시간 동안에는 생성되지 않게 하기 위한 것으로, 보통 세그먼트의 최대 생명주기에 두 배 정도의 시간 동안만 유지된다.
- HTTP 커넥션 관리
- 멱등성 - 한 번 혹은 여러 번 실행됐는지에 상관없이 같은 결과를 반환한다면 그 트랜잭션은 멱등하다고 한다.
- GET, HEAD, PUT, DELETE, TRACE 그리고 OPTIONS 메서드들은 멱등하다고 이해하면 된다.
- 클라이언트는 POST와 같이 멱등이 아닌 요청은 파이프라인을 통해 요청하면 안 된다.
- 전체 끊기(close), 입력과 출력 중 하나만 끊기(shutdown)

5. 웹 서버

```

 여러 종류의 소프트웨어 및 하드웨어 웹 서버에 대해 조사한다.

 HTTP 통신을 전달해주는 간단한 웹 서버를 펄(perl)로 작성해본다.

 어떻게 웹 서버가 HTTP 트랜잭션을 처리하는지 단계별로 설명한다.

```

- 웹 서버는 HTTP 및 그와 관련된 TCP 처리를 구현한 것이다.
- 웹 서버는 자신이 제공하는 리소스를 관리하고 웹 서버를 설정, 통제, 확장하기 위한 관리 기능을 제공한다.
- 웹 서버는 여러 가지 형태가 가능하다.
- 다목적 소프트웨어 웹 서버를 표준 컴퓨터 시스템에 설치하고 실행할 수 있다.
- 마이크로프로세서의 기적으로, 어떤 회사들은 사용자에게 판매할 전자기기 안에 몇 개의 컴퓨터 칩만으로 구현된 웹 서버를 내장시켜서 완전한 관리 콘솔로 제공한다.
- 2014년 기준 순위 마이크로소프트 IIS(37%), 아파치(35%), 엔진엑스(14%)
- 2017년 10월 기준으로 실질적으로 작동하는 웹 사이트(active site)들에서 쓰이는 웹 서버 소프트웨어 순위는 아파치(44.89%), 엔진엑스(20.65%), 구글 웹 서버(7.86%), 마이크로소프트 IIS(7.32%)순이다 
- 2021년 아파치 (41%), 엔진엑스 (27%), 마이크로소프트 (11%)
- 웹 서버가 하는일
- 커넥션을 맺는다 - 클라이언트의 접속을 받아들이거나, 원치 않는 클라이언트라면 닫는다.
- 요청을 받는다 - HTTP 요청 메시지를 네트워크로부터 읽어 들인다
- 요청을 처리한다 - 요청 메시지를 해석하고 행동을 취한다
- 리소스에 접근한다 - 메시지에서 지정한 리소스에 접근한다.
- 응답을 만든다 - 올바른 헤더를 포함한 HTTP 응답 메시지를 생성한다.
- 응답을 보낸다 - 응답을 클라이언트에게 돌려준다.
- 트랜잭션을 로그로 남긴다 - 로그파일에 트랜잭션 완료에 대한 기록을 남긴다. P131
- 대부분의 웹 서버는 '역방향 DNS(reverse DNS)'를 사용해서 클라이언트의 IP 주소를 클라이언트의 호스트 명으로 변환하도록 설정되어 있다.
- docroot의 활용
- DocumentRoot - 아파치 웹 서버의 문서 루트를 설정한다. 가상호스트에서 DocumentRoot를 이용해 웹 서버에서 두 웹 사이트를 분리할 수 있다.
- DirectoryIndex - 디렉터리 색인 파일로 사용될 모드 파일의 이름을 우선순위로 나열한다. 
- 사용자가 디렉터리 URI를 요청했을 때 기본 색인 파일이 없고 디렉터리 색인 기능이 꺼져있지 않다면, 많은 웹 서버는 자동으로 그 디렉터리의 파일들을 크기, 벼경일 및 그 파일에 대한 링크와 함께 열거한 HTML 파일을 반환한다
- 다음과 같은 아파치 지시자로 디렉터리 색인 파일 자동 생성을 끌 수 있다.
- Options -indexes

```

 아파치는 URI의 경로명이 실행 가능한 프로그램이 위치한 디렉터리로 매핑되도록 설정하는 기능을 제공한다.

 URL의 경로가 /cgi-bin/으로 시작한다면 /usr/local/etc/httpd/cgi-progrmas/에서 프로그램을 찾아 실행하라

 ScriptAlias /cgi-bin/ /usr/local/etc/httpd/cgi-programs/ 

```

```

 특정 확장자의 파일만 실행다로고 설정할 수 있다.

 .cgi로 끝나는 모든 웹 리소스는 실행되어야 함

 AddHandler cgi-script .cgi

```
- 웹 초창기에 널리 쓰였던 CGI는 서버사이드 애플리케이션을 실행하기 위한 간단한 인터페이스다.
- 오늘날의 애플리케이션 서버는, 마이크로소프트의 액티브 서버 페이지와 자바 서블릿과 같은 한층 더 강력하고 효과적인 동적 컨텐츠 지원 기능을 갖고 있다.

6. 프락시

```

HTTP 프락시와 웹 게이트웨이를 비교하고 HTTP 프락시가 어떻게 배치되는지 그림으로 보여주면서 설명한다.

몇 가지 유용한 활용방법을 보여준다.

프락시가 실제 네트워크에 어떻게 배치되어 있는지 그리고 트래픽이 어떻게 프락시 서버로 가게 되는지 설명한다.

브라우저에서 프락시를 사용하려면 어떻게 설정해야 하는지 보여준다.

HTTP 프락시 요청이 서버 요청과 어떻게 다른지, 그리고 프락시가 어떻게 부라우저의 동작을 미묘하게 바꾸는지 보여준다.

일련의 프락시 서버들을 통과하는 메시지의 경로를, Via 헤더와 TRACE 메서드를 이용해 기록하는 방법을 설명한다.

프락시에 기반한 HTTP 접근 제어를 설명한다.

어떻게 프락시가 클라이언트와 서버 사이에서 각각의 다른 기능과 버전 들을 지원하면서 상호작용 할 수 있는지 설명한다.

```

- 웹 프락시 서버는 클라이언트의 입장에서 트랜잭션을 수행하는 중개인이다.
- 웹 프락시가 없다면, 클라이언트는 HTTP 서버와 직접 이야기한다.
- HTTP 프락시 서버는 웹 서버이기도 하고 웹 클라이언트이기도 하다.
- 프락시는 HTTP 클라이언트의 요청을 받게 되므로, 반드시 웹 서버처럼 요청과 커넥션을 적절히 다루고 응답을 돌려줘야 한다.
- 동시에 프락시는 요청을 서버로 보내기도 하므로 요청을 보내고 응답을 받는 올바른 HTTP 클라이언트처럼 동작해야 한다.
- 엄밀하게 말하면, 프락시는 같은 프로토콜을 사용하는 둘 이상의 애플리케이션을 연결하고, 게이트웨이는 서로 다른 프로토콜을 사용하는 둘 이상을 연결한다.
- 왜 프락시를 사용하는가? 어린이필터 or 동시 접근 제어 or 보안 방화벽
- 프락시 서버 배치 네 가지
- 출구 프락시
- 접근(입구) 프락시
- 대리 프락시
- 네트워크 교환 프락시 
- 프락시 URI는 서버 URI와 다르다.
- 클라이언트가 프락시를 사용하지 않도록 설정되어 있다면, 부분 URI를 보낸다.
- 클라이언트가 프락시를 사용하도록 설정되어 있다면, 완전한 URI를 보낸다.
- Via 헤더 필드는 메시지가 지나는 각 중간 노드(프락시나 게이트웨이)의 정보를 나열한다.
- Via 문법 - Via 헤더 필드는 쉼표로 구분된 경유지의 목록이다.
- Via: 1.1 proxy-62.irenes-isp.net, 1.0 cache.joes-hardware.com
- 프로토콜의 버전은 필수이다.
- 응답 Via 헤더는 보통 요청 Via의 반대다.
- HTTP/1.1의 TRACE 메서드는 요청 메시지를 프락시의 연쇄를 따라가면서 어떤 프락시를 지나가고 어떻게 각 프락시가 요청 메시지를 수정하는지 관찰/추적할 수 있도록 해준다.
- TRACE 요청이 목적지 서버에 도착했을 때, 서버는 전체 요청 메시지를 HTTP 응답 메시지의 본문에 포함시켜 송신자에게 그대로 돌려보낸다.
- TRACE 응답이 도착했을 때, 클라이언트는 서버가 받은 메시지와 그 메시지가 지나간 프락시들의 목록(Via 헤더 안에 있다)을 검사할 수 있다.

7. 캐시

```

캐시는 불필요한 데이터 전송을 줄여서, 네트워크 요금으로 인한 비용을 줄여준다.

캐시는 네트워크 병목을 줄여준다. 대역폭을 늘리지 않고도 페이지를 빨리 불러올 수 있게 된다.

캐시는 원 서버에 대한 요청을 줄여준다. 서버는 부하를 줄일 수 있으며 더 빨리 응답할 수 있게 된다.

페이지를 먼 곳에서 불러올수록 시간이 많이 걸리는데, 캐시는 거리로 인한 지연을 줄여준다.

```

- 불필요한 데이터 전송 - 복수의 클라이언트가 자주 쓰이는 원 서버 페이지에 접근할 때, 서버는 같은 문서를 클라이언트들에게 각각 한 번씩 전송하게 된다.
- 똑같은 바이트들이 네트워크를 통해 계속 반복해서 이동한다.
- 이 불필요한 데이터 전송은 값비싼 네트워크 대역폭을 잡아먹고, 전송을 느리게 만들며, 웹 서버에 부하를 준다.
- 캐시를 이용하면, 첫 번째 서버 응답은 캐시에 보관된다.
- 캐시된 사본이 뒤이은 요청들에 대한 응답으로 사용될 수 있기 때문에, 원 서버가 중복해서 트래픽을 주고받는 낭비가 줄어들게 된다.
- 대역폭 병목 - 캐시는 또한 네트워크 병목을 줄여준다.
- 많은 네트워크가 원격 서버보다 로컬 네트워크 클라이언트에 더 넓은 대역폭을 제공한다.
- 클라이언트들이 서버에 접근할 때의 속도는, 그 경로에 있는 가장 느린 네트워크의 속도와 같다.
- 만약 클라이언트가 빠른 LAN에 있는 캐시로부터 사본을 가져온다면, 캐싱은 성능을 대폭 개선할 수 있을 것이다.
- EX) 죠의 하드웨어 주식회사의 샌프란시스코 지사에 있는 사용자는 애틀랜타의 본사로부터 5MB 크기의 물품 목록 파일을 받는데 30초가 걸릴 수 있다.
- 만약 문서가 샌프란시스코의 사무실에 캐시되어 있따면, 로컬 사용자는 같은 문서를 이더넷 접속을 통해 1초 미만의 시간에 가져올 수 있을 것이다.
- 재검사(Revalidation) - 원 서버 콘텐츠는 변경될 수 있기 때문에, 캐시는 반드시 그들이 갖고 있는 사본이 여전히 최신인지 서버를 통해 때때로 점검해야 한다.
- 이러한 '신선도 검사'를 HTTP 재검사라 부른다. 효과적인 재검사를 위해, HTTP는 서버로부터 전체 객체를 가져오지 않고도 콘텐츠가 여전히 신선한지 빠르게 검사할 수 있는 특별한 요청을 정의했다.
- HTTP는 캐시된 객체를 재확인하기 위한 몇 가지 도구를 제공하는데, 그중에서 가장 많이 쓰이는 것은 If-Modified-Since 헤더다.
- 서버에게 보내는 GET 요청에 이 헤더를 추가하면 캐시된 시간 이후에 변경된 경우에만 사본을 보내달라는 의미가 된다.
- 캐시 처리 단계 7 단계
- 요청받기 - 캐시는 네트워크로부터 도착한 요청 메시지를 읽는다.
- 파싱 - 캐시는 메시지를 파싱하여 URL과 헤더들을 추출한다.
- 검색 - 캐시는 로컬 복사본이 있는지 검사하고, 사본이 없다면 사본을 받아온다
- 신선도 검사 - 캐시는 캐시된 사본이 충분히 신선한지 검사하고, 신선하지 않다면 변경사항이 있는지 서버에게 물어본다.
- 응답 생성 - 캐시는 새로운 헤더와 캐시된 본문으로 응답 메시지를 만든다.
- 발송 - 캐시는 네트워크를 통해 응답을 클라이언트에게 돌려준다.
- 로깅 - 선택적으로, 캐시는 로그파일에 트랜잭션에 대해 서술한 로그 하나를 남긴다.
- HTTP/1.1은 신선도를 관리하기 위해, 객체를 캐시하는 것을 제한하거나 캐시된 객체를 제공하는 여러 가지 방법을 제공한다.
- no-store와 no-cache 헤더는 캐시가 검증되지 않은 캐시된 객체로 응답하는 것을 막는다.

```

Cache-Control: no-store
Cache-Control: no-cache
Pragma: no-cache

```

- 'no-cache'가 표시된 응답은 캐시가 그 응답의 사본으 만드는 것을 금지한다.
- 캐시는 보통, 캐시가 아닌 프락시 서버가 그러는 것처럼, 클라이언트에게 no-store 응답을 전달하고 나면 객체를 삭제할 것이다.
- 이 헤더의 더 나은 이름은 "Do-Not-Servce-From-Cache-Without-Revalidation(재검사 없이 캐시에서 제공하지 마라)"일 것이다.

```

Cache-Control: max-age=3600

```

- Cache-Control:max-age 헤더는 신선하다고 간주되었던 문서가 서버로부터 온 이후로 흐른 시간이고, 초로 나타낸다.
- 서버는 최대 나이먹음(Maximum aging)을 0으로 설정함으로써, 캐시가 매 접근마다 문서를 캐시하거나 리프레시하지 않도록 요청할 수 있다.


- 캐시는 성능을 개선하기 위해 신선하지 않은(만료된) 객체를 제공하도록 설정될 수 있다.
- 만약 캐시가 만료 ㅈ어보를 엄격하게 따르길 원한다면, 다음과 같은 Cache-Control을 붙일 수 있다.

```

Cache-Control - must-revalidate

```

- Cache-Control: must-revalidate 응답 헤더는 캐시가 이 객체의 신선하지 않은 사본을 원 서버와의 최초의 재검사 없이는 제공해서는 안 됨을 의미한다.
- 캐시는 자유롭게 신선한 사본을 제공할 수 있다.
- 아파치로 HTTP 헤더 제어하기
- 아파치 웹 서버는 HTTP 캐시 제어 헤더를 설정할 수 있는 여러 가지 메커니즘을 제공한다.
- mod-headers 모듈은 개별 헤더들을 설정할 수 있게 해준다. 한번 이 모듈이 로드되면, 개별 HTTP 헤더를 설정할 수 있는 지시어를 이용해 아파티 설정 파일에 설정을 추가할 수 있다.

8. 통합점: 게이트웨이, 터널, 릴레이

```

게이트웨이: 서로 다른 프로토콜과 애플리케이션 간의 HTTP 인터페이스다.

애플리케이션 인터페이스: 서로 다른 형식의 웹 애플리케이션이 통신하는 데 사용한다.

터널: HTTP 커넥션을 통해서 HTTP가 아닌 트래픽을 전송하는 데 사용한다.

릴레이: 일종의 단순한 HTTP 프락시로, 한 번에 한 개의 홉에 데이터를 전달하는데 사용한다.

```

- 웹 게이트웨이는 한쪽에서는 HTTP로 통신하고 다른 한쪽에서는 HTTP가 아닌 다른 프로토콜로 통신한다.
- 게이트웨이는 클라이언트 측 프로토콜과 서버 측 프로토콜을 빗금(/)으로 구분해 기술한다.
- <클라이언트 프로토콜>/<서버 프로토콜>
- 서버 측 게이트웨이는 클라이언트와 HTTP로 통신하고, 서버와는 외래 프로토콜로 통신한다.
- 클라이언트 측 게이트웨이는 클라이언트와 외래 프로토콜로 통신하고, 서버와는 HTTP로 통신한다.
- 애플리케이션 게이트웨이에서 유명했던 최초의 API는 공용 게이트웨이 인터페이스(Common Gateway Interface, CGI)였다.
- CGI는 특정 URL에 대한 HTTP 요청에 따라 프로그램을 실행하고, 프로그램의 출력을 수집하고, HTTP 응답으로 회산하는데 웹 서버가 사용하는 표준화된 인터페이스 집합이다.
- 웹 터널은 HTTP 프로토콜을 지원하지 않는 애플리케이션에 HTTP 애플리케이션을 사용해 접근하는 방법을 제공한다.
- 웹 터널을 사용하면 HTTP 커넥션을 통해서 HTTP가 아닌 트래픽을 전송할 수 있고, 다른 프로토콜을 HTTP 위에 올릴 수 있다.
- 웹 터널은 HTTP의 CONNECT 메서드를 사용하여 커넥션을 맺는다.
- HTTP 릴레이는 HTTP 명세를 완전히 준수하지는 않는 간단한 HTTP 프락시다.
- 릴레이는 커넥션을 맺기 위한 HTTP 통신을 한 다음, 바이트를 맹목적으로 전달한다.

9. 웹 로봇

```

주식시장 서버에 매 분 HTTP GET 요청을 보내고, 여기서 얻은 데이터를 활용해 주가 추이 그래프를 생성하는 주식 그래프 로봇

월드 와이드 웹의 규모와 진화에 대한 통계 정보를 수집하는 웹 통계 조사 로봇, 이것들은 웹을 떠돌면서 페이지의 개수를 세고, 각 페이지의 크기, 언어, 미디어 타입을 기록한다.

검색 데이터베이스를 만들기 위해 발견한 모든 문서를 수집하는 검색엔진 로봇.

상품에 대한 가격 데이터베이스를 만들기 위해 온라인 쇼핑몰의 카탈로그에서 웹페이지를 수집하는 가격 비교 로봇

```

- 크롤러와 크롤링
- 웹 크롤러는, 먼저 웹페이지를 한 개 가져오고, 그 다음 그 페이지가 가리키는 모든 웹페이지를 가져오고, 다시 그 페이지들이 가리키는 모든 웹페이지들을 가져오는, 이러한 일을 재귀적으로 반복하는 방식으로 웹을 순회하는 로봇이다.
- 웹 링크를 재귀적으로 따라가는 로봇을 크롤러 혹은 스파이더라고 부르는데, HTML 하이퍼링크들로 만들어진 웹을 따라 '기어다니기(crawl)' 때문이다.
- 로봇의 HTTP

```

User-Agent 서버에게 요청을 만든 로봇의 이름을 말해준다.

From 로봇의 사용자/관리자의 이메일 주소를 제공한다.

Accept 서버에게 어떤 미디어 타입을 보내도 되는지 말해준다. 이 헤더는 로봇이 관심있는 유형의 콘텐츠(텍스트, 이미지 등)만 받게 될 것임을 확신하는 데 도움을 준다

Referer 현재의 요청 URL을 포함한 문서의 URL을 제공한다.

```

- robots.txt - 어떤 로봇이 서버의 어떤 부분에 접근할 수 있는지에 대한 정보가 담겨있다. 
- 로봇은 어떤 웹 사이트든 반드시 robots.txt를 찾아본다. 로봇은 robots.txt의 검색결과에 따라 다르게 동작한다.
- robots.txt 파일 포맷
- robots.txt 파일은 매우 단순한 줄 기반 문법을 갖는다.
- robots.txt 파일의 각 줄은 빈줄, 주석 줄, 규칙 줄의 세가지 종류가 있다.

```

User-Agent: slurp
User-Agent: webcrawler
Disallow: /private

User-Agent: *
Disallow: 

```

- 레코드는 어떤 로봇이 이 레코드에 영향을 받는지 지정하는 하나 이상의 User-Agent 줄로 시작하며 뒤이어 이 로봇들이 접근할 수 있는 URL들을 말해주는 Allow 줄과 Disallow 줄이 온다.

10. HTTP/2.0

- 웹을 더 빠르게 하겠다.

11. 클라이언트 식별과 쿠키

- HTTP 헤더
- From 헤더는 사용자의 이메일 주소를 포함한다.
- User-Agent 헤더는 사용자가 쓰고 있는 브라우저의 이름과 버전 정보, 어떤 경우에는 운영체제에 대한 정보까지 포함하여 서버에게 알려준다.
- Referer 헤더는 사용자가 현재 페이지로 유입하게 한 웹페이지의 URL을 가리킨다.
- 쿠키의 타입 - 세션 쿠키와 지속 쿠키
- 세션 쿠키는 사용자가 사이트를 탐색할 때, 관련한 설정과 선호 사항들을 저장하는 임시 쿠키다.
- 세션 쿠키는 사용자가 브라우저를 닫으면 삭제된다.
- 지속 쿠키는 삭제되지 않고 더 길게 유지될 수 있다.
- 지속 쿠키는 디스크에 저장되어, 브라우저를 닫거나 컴퓨터를 재시작하더라도 남아있다.
- 세션 쿠키와 지속 쿠키가 다른 점은 파기되는 시점 뿐이다.
- 뒤에서 다룰 것이지만, 쿠키는 Discard 파라미터가 설정되어 있거나, 파기되기까지 남은 시간을 가리키는 Expires 혹은 Max-Age 파라미터가 없으면 세션 쿠키가 된다.
- 처음에 사용자가 웹 사이트에 방문하면 웹 서버는 사용자에 대해서 아무것도 모른다.
- 웹 서버는 사용자가 다시 돌아왔을 때, 해당 사용자를 식별하기 위한 유일한 값을 쿠키에 할당한다.
- 쿠키는 임의의 이름=값 형태의 리스트를 가지고, 그 리스트는 Set-Cookie 호은 Set-Cookie2(확장 헤더)같은 HTTP 응답 헤더에 기술되어 사용자에게 전달한다.
- Version 0(넷스케이프) 쿠키
- 최초의 쿠키 명세는 넷스케이프가 정의했다.
- 이 'Version 0' 쿠키는 Set-Cookie 응답 헤더와 Cookie 요청 헤더와 쿠키를 조작하는 데 필요한 필드들을 정의하였다.

```

Set-Cookie: name=vlue [; expires=date] [; path=path] [; domain=domain] [; secure]

name = 필수 속성. 이름=값 으로 만든 사용자 식별 코드

expires = 선택적인 속성. 쿠키의 생명주기를 가리키는 날짜 문자열

domain = 선택적인 속성. 브라우저는 이 속성에 기술된 도메인을 사용하는 서버 호스트명으로만 쿠키를 전송한다.

path = 선택적인 속성. 이 속성으로 서버에 있는 특정 문서에만 쿠키를 할당할 수 있다.

secure = 선택적인 속성. 이 속성이 포함되어 있으면, 쿠키는 HTTP가 SSL 보안 연결을 사용할 때만 쿠키를 전송한다.

```

- Version 1 쿠키 P313

```

쿠키마다 그 목적을 설명하는 설명문이 있다.

파기 주기에 상관없이 브라우저가 닫히면 쿠키를 강제로 삭제할 수 있다.

절대 날짜 값 대신에 초 단위의 상대 값으로 쿠키의 생명 주기를 결정할 수 있는 Max-Age

단순히 도메인과 경로뿐 아니라 URL의 포트번호로도 쿠키를 제어할 수 있다.

도메인, 포트, 경로 필터가 있으면 Cookie 헤더에 담겨 되돌려보낸다.

호환되는 버전 번호.

사용자 이름과 추가적인 키워드를 구별하기 위해 Cookie 헤더에 $ 접두어가 있다.

Version = 필수 속성. 이 속성의 값은 쿠키 명세의 버전을 가리키는 정수 값이다. RFC2955의 버전은 1이다.

Comment = 선택적인 속성. 이 속성에는 서버가 쿠키를 사용하려는 의도를 기술한다.

CommentUrl = 선택적인 속성. 이 속성은 쿠키를 사용하는 목적과 정책에 대해 상세히 기술된 웹페이지 URL 링크를 제공한다.

Discard = 선택적인 속성. 이 속성이 기술되어 있으면, 클라이언트 프로그램이 종료될 때 클라이언트가 해당 쿠키를 삭제한다.

Max-Age = 선택적인 속성. 이 속성의 값은 쿠키의 생명주기를 초 단위로 산정한 정수 값이다. 값이 0이면 해당 이름을 가진 쿠키를 즉시 지워야 함을 의미한다.

Port= 선택적인 속성. 이 속성은, 값이 없이 속성의 키워드(Port)만 기술할 수도 있고, 쿠키가 적용될 포트 한 개 이상을 콤마로 구분하여 기술할 수 있다.

Port 키워드만 독립적으로 기술하면, 쿠키는 현재 응답 서버의 포트에 대해서만 전송된다.

ex) Set-Cookie2: foo="bar"; Version="1"; Port="80,81,8080"
    Set-Cookie2: foo="bar"; Version="1"; Port

```

12. 기본 인증

- HTTP에는 기본 인증과 다이제스트 인증이라는 두 가지 공식적인 인증 프로토콜이 있다.
- Base-64 인코딩 메서드를 사용해 인코딩을 하기 때문에 보안에 문제가 있다.
- Base-64 인코딩은 바이너리, 텍스트, 국제 문자 데이터(어떤 시스템에서는 문제를 일으킬 수 있는) 문자열을 받아서 전송할 수 있게, 그 문자열을 전송 가능한 문자인 알파벳으로 변환하기 위해 발명됐다.
- Base-64 디코딩을 통해 원본 문자열을 얻을 수 있다.

13. 다이제스트 인증

- 다이제스트 인증은 기본 인증과 호환되는 더 안전한 대체재로서 개발되었다.

```

비밀번호를 절대로 네트워크를 통해 평문으로 전송하지 않는다.

인증 체결을 가로채서 재현하려는 악의적인 사람들을 차단한다.

구현하기에 따라서, 메시지 내용 위조를 막는 것도 가능하다.

그 외 몇몇 잘 알려진 형태의 공격을 막는다.

```

- 다이제스트 인증은 다른 인터넷 서비스를 위해 제안된 많은 인기 있는 보안 체계들(예: LDAP, POP, IMAP을 위한 CRAM-MD5)보다 더 강력하다.
- 아직까지 다이제스트 인증은 널리 쓰이고 있지 않다. (2012년에도..? 지금도?)
- "절대로 비밀번호를 네트워크를 통해 보내지 않는다" - 지문(fingerprint) 혹은 요약(digest)을 보낸다.
- 요약(digest)은 '정보 본문의 압축'이다. 요약은 단방향 함수로 동작하고, 일반적으로 입력 가능한 무한 가지의 모든 입력값들을 유한한 범위의 압축으로 변환한다.
- 인기 있는 요약 함수 중 하나인 MD5는 임의의 바이트 배열을 원래 길이와 상관없이 128비트 요약으로 변환한다.
- 재전송 방지를 위한 난스(nonce) 사용
- 단방향 요약은 비밀번호를 그대로 전송해야 할 필요성에서 우리를 해방시켜 준다.
- 우리는 그 대신 그냥 비밀번호에 대한 요약을 보내주고, 악의집단이 쉽게 요약에서 원래 비밀번호를 해독할 수 없음을 보장받기만 하면 된다.
- 재전송 공격을 방지하기 위해서 서버는 클라이언트에게 난스라고 불리는 특별한, 그리고 자주 바뀌는 증표를 건네준다.
- 난스를 비밀번호에 섞으면 난스가 바뀔 때마다 요약도 바뀌게 만들어준다.
- 보호 수준(Quality of Protection) 향상
- qop 필드는 요약 헤더의 세 가지 헤더 WWW-Authenticate, Authorization, Authentication-Info 에 모두 존재할 수 있다.
- RFC 2617은 기본적으로 두 가지 초기 보호수준 값을 정의하고 있다. 하나는 인증을 의미하는 "auth"이고 다른 하나는 이증 및 메시지 무결성 보호를 의미하는 "auth-int"이다.
- 다이제스트 인증이 기본 인증에 비해 훨씬 탄탄하고 안전한 해결책을 제공함에도 불구하고, 여전히 콘텐츠에 대한 보안 측면에서는 어떠한 보호도 제공하지 못한다.
- 진정한 보안 트랜잭션은 SSL을 통해서만 가능하다.

14. 보안 HTTP

- 보안 기술

```

서버 인증 - 클라이언트는 자신이 위조된 서버가 아닌 진짜와 이야기하고 있음을 알 수 있어야 한다.

클라이언트 인증 - 서버는 자신이 가짜가 아닌 진짜 사용자와 이야기하고 있음을 알 수 있어야 한다.

무결성 - 클라이언트와 서버는 그들의 데이터가 위조되는 것으로부터 안전해야 한다.

암호화 - 클라이언트와 서버는 도청에 대한 걱정 없이 서로 대화할 수 있어야 한다.

효율 - 저렴한 클라이언트나 서버도 이용할 수 있도록 알고리즘은 충분히 빨라야 한다.

편재성(Ubiquity) - 프로토콜은 거의 모든 클라이언트와 서버에서 지원되어야 한다.

관리상 확장성 - 누구든 어디서든 즉각적인 보안 통신을 할 수 있어야 한다.

적응성 - 현재 알려진 최선의 보안 방법을 지원해야 한다.

사회적 생존성 - 사회의 문화적, 정치적 요구를 만족시켜야 한다.

```

- HTTPS는 HTTP를 안전하게 만드는 방식 중에서 가장 인기 있는 것이다.
- HTTPS를 사용할 때, 모든 HTTP 요청과 응답 네이터는 네트워크로 보내지기 전에 암호화된다.
- HTTPS는 HTTP의 하부에 전송 레벨 암호 보안 계층을 제공함으로써 동작하는데, 
- 이 보안 계층은 안전 소켓 계층(Secure Sockets Layer, SSL) 혹은 그를 계승한
- 전송 계층 보안(Transport Layer Security, TLS)을 이용하여 구현된다.
- SSL과 TLS는 매우 비슷하다.
- 디지털 암호
- 디지털 계산의 도래로, 두 가지 중요한 발전이 있었다.
- 속도 및 기능에 대한 기계 장치의 한계에서 벗어남으로써, 복잡한 인코딩과 디코딩 알고리즘이 가능해졌다.
- 매우 큰 키를 지원하는 것이 가능해져서, 단일 암호 알고리즘으로 키의 값마다 다른 수조 개의 가상 암호 알고리즘을 만들어낼 수 있게 되었다.
- 공개키 암호법
- 한 쌍의 호스트가 하나의 인코딩/디코딩 키를 사용하는 대신, 공개키 암호 방식은 두 개의 비대칭 키를 사용한다.
- 하나는 호스트의 메시지를 인코딩하기 위한 것이며, 다른 하나는 그 호슽의 메시지를 디코딩하기 위한 것이다.
- 인코딩 키는 모두를 위해 공개되어 있다(그래서 공개키 암호 방식이라는 이름이 붙었다.)
- 하지만 호스트만이 개인 디코딩 키를 알고 있다.
- 공개키 암호화 방식의 알고리즘은 계산이 느린 경향이 있다.
- 실제로는 대칭과 비대칭 방식을 섞은 것이 쓰인다.
- 노드들 사이의 안전한 의사소통 채널을 수립할 때는 편리하게 공개 키 암호를 사용하고, 
- 이렇게 만들어진 안전한 채널을 통해 임시의 무작위 대칭 키를 생성하고 교환하여 이후의 나머지 데이터를 암호화 할 때는 빠른 대칭 키를 사용하는 방식이 흔히 쓰인다.
- 디지털 서명은 메시지에 붙어있는 특별한 암호 체크섬이다.
- 서명은 메시지를 작성한 저자가 누군지 알려준다.
- 저자는 저자의 극비 개인키를 갖고 있기 때문에, 오직 저자만이 이 체크섬을 계산할 수 있다.
- 체크섬은 저자의 개인'서명'처럼 동작한다.
- 서명은 메시지 위조를 방지한다.
- 만약 악의적인 공격자가 송신 중인 메시지를 수정했다면, 체크섬은 더 이상 그 메시지와 맞지 않게 될 것이다.
- 그리고 체크섬은 저자의 비밀 개인 키에 관련되어 있기 때문에, 침입자는 그 위조된 메시지에 대한 올바른 체크섬을 날조해낼 수 없을 것이다.
- 디지털 서명은 보통 비대칭 공개키에 의해 생성된다.
- 개인 키는 오직 소유자만이 알고 있기 때문에, 저자의 개인 키는 일종의 '지문'처럼 사용된다.
- 디지털 인증서 X.509 v3

```

버전 - X.509 인증서 버전의 번호. 요즘은 보통 버전 3이다.

일련번호 - 인증기관에 의해 생생된 고유한 정수. CA로부터의 각 인증서는 반드시 고유한 일련번호를 가져야 한다.

서명 알고리즘 ID - 서명을 위해 사용된 암호 알고리즘. 예를 들면, "RSA 암호화를 이용한 MD2 요약"

인증서 발급자 - 인증서를 발급하고 서명한 기관의 이름. 

유효 기간 - 인증서가 유효한 기간

대상의 이름 - 인증서에 기술된, 사람이나 조직과 같은 엔터티

대상의 공개 키 정보 - 인증 대상의 공개 키, 공개 키에 사용된 알고리즘, 추가 매개변수

발급자의 고유 ID (선택적) - 발급자의 이름이 겹치는 경우를 대비한, 인증서 발급자에 대한 선택적인 고유한 식별자

대상의 고유 ID (선택적) - 대상의 이름이 겹치는 경우를 대비한, 인증 대상에 대한 선택적인 고유한 식별자

확장 - 선택적인 확장 필드의 집합 (기본 제약, 인증서 정책, 키 사용, ...)

인증기관 서명 - 위의 모든 필드에 대한 인증기관의 디지털 서명, 명시된 서명 알고리즘을 사용한다.

```

- SSL 핸드셰이크

```

프로토콜 버전 번호 교환

양쪽이 알고 있는 암호 선택

양쪽의 신원을 인증

채널을 암호화하기 위한 임시 세션 키 생성

1. 클라이언트가 암호 후보들을 보내고 인증서를 요구한다.

2. 서버는 선택된 암호와 인증서를 보낸다.

3. 클라이언트가 비밀정보를 보낸다. 클라이언트와 서버는 키를 만든다.

4. 클라이언트와 서버는 서로에게 암호화를 시작한다고 말해준다.

```

- Web Security, Privacy & Commerce 웹 보안 및 SSL/TLS와 디지털 서명의 사용에 대한 입문서 중 하나

15. 엔터티와 인코딩


```

HTTP는 메시지가 올바르게 수송되고, 식별되고, 추출되고, 처리되는 것을 보장한다.

객체는 올바르게 식별되므로(Content-Type 미디어 포멧과 Content-Language 헤더를 이용해서) 브라우저나 다른 클라이언트는 콘텐츠를 바르게 처리할 수 있다.

객체는 올바르게 압축이 풀릴 것이다(Content-Length와 Content-Encoding 헤더를 이용해서).

객체는 항상 최신이다(엔터티 검사기와 캐시 만료 제어를 이용해서).

사용자의 요구를 만족할 것이다(내용 협상을 위한 Accept 관련 헤더들에 기반하여).

네트워크 사이를 빠르고 효율적으로 이동할 것이다(범위 요청, 델타 인코딩, 그외의 데이터 압축을 이용해서).

조작되지 않고 온전하게 도착할 것이다(전송 인코딩 헤더와 Content-MD5 체크섬을 이용해서).

```

- HTTP/1.1의 10가지 주요 엔터티 헤더 필드

```

Content-Type - 엔터티에 의해 전달된 객체의 종류

Content-Length - 전달되는 메시지의 길이나 크기

Content-Language - 전달되는 객체와 가장 잘 대응되는 자연어

Content-Encoding - 객체 데이터에 대해 행해진 변형(압축 등)

Content-Location - 요청 시점을 기준으로, 객체의 또 다른 위치

Content-Range - 만약 이 엔터티가 부분 엔터티라면, 이 헤더는 이 엔터티가 전체에서 어느 부분에 해당하는지 정의한다.

Content-MD5 - 엔터티 본문의 콘텐츠에 대한 체크섬

Last-Modified - 서버에서 이 콘텐츠가 생성 혹은 수정된 날

Expires - 이 엔터티 데이터가 더 이상 신선하지 않은 것으로 간주되기 시작하는 날짜와 시각

Allow - 이 리소스에 어떤 요청 메서드가 허용되는지. 예) GET와 HEAD

ETag - 이 인스턴스에 대한 고유한 검사기. 엄밀히 말해 ETag 헤더는 엔터티 헤더로 정의되어 있지는 않지만 엔터티와 관련된 많은 동작을 위해 중요한 헤더이다.

Cache-Control - 어떻게 이 문서가 캐시될 수 있는지에 대한 지시자. ETag 헤더와 마찬가지로 Cache-Control 헤더도 엔터티 헤더로 정의되어 있지는 않다.

```

- 엔터티 본문은 가공되지 않은 데이터만을 담고 있다. 다른 정보들은 모두 헤더에 담겨 있다.
- 엔터티 본문은 헤더 필드의 끝을 의미하는 빈 CRLF 줄 바로 다음부터 시작한다. (Ox0A(LF) 바로 다음부터)
- 콘텐츠가 텍스트든 바이너리든, 문서든 이미지든, 압축되었든 안 되었든, 영어든 프랑스어든 일본어든 상관없이 항상 CRLF 바로 다음에 위치한다.
- Content-Length는 지속 커넥션을 위해 필수다. 만약 응답이 지속 커넥션을 통해서 온 것이라면, 또 다른 HTTP 응답이 즉시 그 뒤를 이을 것이다.
- Content-Length 헤더는 클라이언트에게 메시지 하나가 어디서 끝나고 다음 시작은 어디인지 알려준다.
- 만약 본문의 콘텐츠가 인코딩되어 있다면, Content-Length 헤더는 인코딩되지 않은 원본의 길이가 아닌 인코딩된 본문의 길이를 바이트 단위로 정의한다.
- Content-Type 헤더필드는 엔터티 본문의 MIME 타입을 기술한다.

```

text/html - 엔터티 본문은 HTML 문서

text/plain - 엔터티 본문은 플레인 텍스트 문서

image/gif - 엔터티 본문은 GIF 이미지

image/jpeg - 엔터티 본문은 JEPG 이미지

audio/x-wav - 엔터티 본문은 WAV 음향 데이터를 포함

model/vml - 엔터티 본문은 삼차원 VRML 모델

application/vnd.ms-powerpoint - 엔터티 본문은 마이크로소프트 파워포인트 프레젠테이션

multipart/byteranges - 엔터티 본문은 여러 부분으로 나뉘는데, 각 부분은 전체 문서의 특정 범위(바이트 단위)를 담고 있다.

message/http - 엔터티 본문은 완전한 HTTP 메시지를 담고 있따.

```

- 콘텐츠 인코딩은 콘텐츠 포맷과 긴밀하게 연관되어 있다. 예를 들어 텍스트 파일은 흔히 gzip으로 압축하지만 JPEG 파일은 그렇게 하지 않는다.
- 왜냐하면 JPEG는 gzip으로 잘 압축되지 않기 때문이다.
- 콘텐츠 인코딩과 전송 인코딩
- 콘텐츠 인코딩된 메시지는 단지 메시지의 엔터티 부분만 인코딩한다.
- 전송 인코딩된 메시지에서는, 인코딩은 전체 메시지에 대해 적용되어 메시지 자체의 구조를 바꾼다.
- HTTP에서 전송된 메시지의 본문이 문제를 일으킬 수 잇는 이유는 몇 가지 밖에 없다. (알 수 없는 크기와 보안)
- 전송 인코딩을 제어하고 서술하기 위해 정의된 헤더는 단 두 개 뿐이다.
- Transfer-Encoding - 안전한 전송을 위해 어떤 인코딩이 메시지에 적용되었는지 수신자에게 알려준다.
- TE - 어떤 확장된 인코딩을 사용할 수 있는지 서버에게 알려주기 위해 요청 헤더에서 사용한다.
- 청크 인코딩은 메시지를 일정 크기의 청크 여럿으로 쪼갠다.
- 서버는 각 청크를 순차적으로 보낸다. 청크 인코딩을 이용하면 메시지를 보내기 전에 전체 크기를 알 필요가 없어진다.
- 청크 데이터의 길이는 바이트 단위로 측정되고 청크 끝의 CRLF 문자열뿐 아니라 길이 값과 데이터 사이의 CRLF 문자열도 길이에 포함하지 않는다.
- 마지막 청크는 특별하다. 그것은 '본문의 끝'을 의미하기 위해 길이가 0이다.
- 전송 인코딩 규칙
- 전송 인코딩이 메시지 본문에 적용될 때, 몇가지 규칙이 반드시 적용되어야 한다.

```

전송 인코딩의 집합은 반드시 'chunked'를 포함해야 한다. 유일한 예외는 메시지가 커넥션의 종료로 끝나는 경우뿐이다.

청크 전송 인코딩이 사용되었다면, 메시지 본문에 적용된 마지막 전송 인코딩이 존재해야 한다.

청크 전송 인코딩은 반드시 메시지 본문에 한 번 이상 적용되어야 한다.

이 규칙은 수신자가 메시지의 전송 길이를 알아낼 수 있게 해준다.

```

- 검사기와 신선도
- 클라이언트는 처음에 리소스의 사본을 갖고 있지 않으므로, 서버에게 달라고 요청을 보낸다.
- 서버는 그 리소스의 버전 1로 응답한다.
- 클라이언트는 이제 이 사본을 캐시한다. 그런데 얼마나 오랫동안 캐시해야 하는가?
- 일단 문서가 클라이언트에서 '만료'되면, 클라이언트는 반드시 서버에게 최신 사본을 요구해야 한다.
- 만약 서버에서도 문서가 변경되지 않았다면 클라이언트는 다시 받을 필요가 없다.
- 조건부 요청이라고 불리는 이 특별한 요청은, 클라이언트가 서버에게 자신이 갖고 있는 버전을 말해주고 검사기를 사용해 자신의 사본 버전이 더 이상 유효하지 않을 때만 사본을 보내달라고 요청하는 것이다.
- 세 가지 주요 개념(신선도, 검사기, 조건)에 대해 알아보자
- 신선도 - 서버는 클라이언트에게 얼마나 오랫동안 콘텐츠를 캐시하고 그것이 신선하다고 가정할 수 있는지에 대한 정보를 줄 것이다.
- 서버는 Expires나 Cache-Control 헤더를 통해 이러한 정보를 제공할 수 있다. 
- P416 Cache-Control 헤더에 동반될 수 있는 지시자
- 캐시의 사본이 요청되었을 때 그것이 더 이상 신선하지 않다면 캐시는 자신이 갖고 있는 사본을 신선한 것으로 만들 필요가 있다.
- 조건부 요청은 'If-'로 시작하는 조건부 헤더에 의해 구현된다. 예:) IF-Modified-Since 
- 각 조건부 요청은 특정 검사기 위에서 동작한다. 

```

요청 유형 / 검사기 / 설명

If-Modified-Since / Last-Modified / 지난번 Last-Modified 응답 헤더에 들어있었던 시간에 마지막으로 수정된 버전이 더 이상 최신 버전이 아니라면, 그 리소스의 사본을 보내라

If-Unmodified-Since / Last-Modified / 지난번 Last-Modified 응답 헤더에 들어있었던 시각에 마지막으로 수정된 버전에서 변한 것이 없다면, 그 리소스의 사본을 보내라

If-Match / Etag / 지난번 ETag 응답 헤더에 들어있었던 것과 엔터티 태그가 같다면, 그 리소스의 사본을 보내라

If-None-Match / Etag / 지난번 ETag 응답 헤더에 들어있었던 것과 엔터티 태그가 다르다면, 그 리소스의 사본을 보내라

```

- 델타 인코딩
- 지금까지 어떤 웹 페이지의 각기 다른 버전들은 그 페이지에 대한 각기 다른 인스턴스라고 설명했다.
- 만약 클라이언트가 어떤 페이지의 만료된 사본을 갖고 있다면, 클라이언트는 그 페이지에 대한 최신 인스턴스를 요청한다.
- 만약 서버가 그 페이지에 대해 더 새로운 인스턴스를 갖고 있다면 서버는 클라이언트에게 그 페이지를 보낼 것이고 설령 그 페이지가 실제로 아주 일부분만 변경되었다 할지라도 전체 인스턴스를 보낼 것이다.
- 새 페이지 전체를 보내는 대신, 페이지에 대한 클라이언트의 사본(변경량이 작은)에 대해 변경된 부분만을 서버가 보낸다면 클라이언트는 더 빨리 페이지를 얻을 수 있을 것이다.
- 델타 인코딩은 객체 전체가 아닌 변경된 부분에 대해서만 통신하여 전송량을 최적화하는, HTTP 프로토콜의 확장이다.

16. 국제화

```

HTTP가 어떻게 여러 언어 문자들의 체계 및 표준과 상호작용하는지 설명한다.

HTTP 프로그래머가 올바르게 업무를 수행하는데 도움이 될 수 있도록 전문용어, 기술, 표준의 간략한 개요를 제공한다.

언어를 위한 표준 명명 체계와, 어떻게 표준화된 언어 태그가 선택한 콘텐츠를 서술하는지에 대해 설명한다.

국제화된 URI의 규칙과 주의사항을 개괄적으로 서술한다.

날짜와 그 외 다른 국제화 이슈에 대해 간단히 논의한다.

```

- 차셋(Charset)은 글자를 비트로 변환하는 인코딩이다
- 비트들을 문자로 변환하는 것은 두 단계에 걸쳐 일어난다.

```

문서를 이루는 비트들은, 특정 코딩된 문자집합의 특정 문자(각각 번호가 매겨져 있다)로 식별될 수 있는 문자 코드로 변환된다. 이 예에서, 디코딩된 문자 코드는 225로 번호가 붙어있다.

문자 코드는 코딩된 문자집합의 특정 요소를 선택하기 위해 사용된다. iso-8859-6에서, 값 225는 'ARABIC LETTER FEH'에 해당한다.

단계 a와 b에서 사용되는 알고리즘은 MIME 차셋 태그를 통해 결정된다.

```

- 국제화된 문자 시스템의 핵심 목표는 표현(시각적인 표현 방식)에서 의미(글자들)를 분리하는 것이다.

- 문자집합 용어

```

문자 - 알파벳 글자, 숫자, 구두점, 표의문자, 기호 등 글쓰기의 최소 단위. 약식으로 유니코드라고 불리는 국제 문자 세트 계획에 따라 여러 언어의 여러 글자에게 알맞고 유일한 이름을 부여하기 위한 표준화된 이름 집합이 개발되어 왔다.

글리프(glyph) - 하나의 글자를 표현하기 위한, 획의 패턴이나 다른 것과 구분되는 유일한 시각적 형태

코딩된 문자(coded character) - 우리가 글자를 다룰 수 있도록 각 글자에 할당된 유일한 숫자

코드 공간(coding space) - 문자 코드 값으로 사용하려고 계획해 둔 정수의 범위

코드 너비(code width) - 각 문자 코드의 (고정된 크기의) 비트 개수

사용 가능 문자집합(character repertoire) - 글자들에 대한 특정한 작업 집합(세상에 존재하는 모든 글자의 부분집합)

코딩된 문자집합(coded character set) - 사용 가능 문자집합(세상의 모든 글자에서 일부분을 선택한 것)을 받아서 각 글자에 코드 공간의 코드를 할당해주는 코딩된 문자들의 집합.

문자 인코딩 구조 - 숫자로 된 문자 코드들을 콘텐츠 비트의 연속으로 인코딩하는(그리고 원래대로 디코딩하는) 알고리즘.
 
```




17. 내용 협상과 트랜스코딩

- 내용 협상 헤더

```

Accept - 서버가 어떤 미디어 타입으로 보내도 되는지 알려준다.

Accept-Language - 서버가 어떤 언어로 보내도 되는지 알려준다.

Accept-Charset - 서버가 어떤 차셋으로 보내도 되는지 알려준다.

Accept-Encoding - 서버가 어떤 인코딩으로 보내도 되는지 알려준다.

```

- 엔터티 헤더는 메시지를 서버에서 클라이언트로 전송 할 때 필요한 메시지 본문의 속성을 가리킨다.
- 내용 협상 헤더는 클라이언트와 서버가 선호 정보를 서로 교환하고 문서들의 여러 버전 중 하나를 선택하는 것을 돕는다.
- 클라이언트와 서버가 협상을 통해 어떤 URL이 가리키는 문서들 중에서 클라이언트의 요구에 가장 잘 맞는 것 하나를 선택해 보내줄 수 있는 매커니즘(내용 협상)에 대해 이야기했다.
- 이 메커니즘은 클라이언트의 요구에 맞는 문서가 존재해야 동작한다.
- 그러나 서버가 클라이언트의 요구에 맞는 문서를 아예 갖고 있지 않다면? 서버는 에러로 응답해야겠지만,
- 이론적으로 서버는 기존의 문서를 클라이언트가 사용할 수 있는 무언가로 변환할 수도 있다.
- 트랜스코딩에는 포맷 변환, 정보 합성, 내용 주입의 세 종류가 있다.
- 포맷 변환은 데이터를 클라이언트가 볼 수 있도록 한 포맷에서 다른 포맷으로 변환하는 것이다. 

```

HTML 문서 - WML 문서

고해상도 이미지 - 저해상도 이미지

64K색 이미지 - 흑백 이미지

프레임을 포함한 복잡한 페이지 - 프레임이나 이미지가 없는 단순한 텍스트 페이지

자바 애플릿이 있는 HTML 페이지 - 자바 애플릿이 없는 페이지

광고가 있는 페이지 - 광고가 없는 페이지

```

18. 웹 호스팅

```

여러 웹 사이트를 같은 서버에 "가상 호스팅"하는 방법. 그리고 그것이 HTTP에 끼치는 영향

트래픽이 많은 상황에서 안정적인 사이트를 구축하는 방법

웹 사이트 로딩을 더 빠르게 하는 방법

```

- 가상 호스팅 동작하게 하기
- 호스트 정보를 HTTP 요청 명세에 넣지 않은 것은, 각 웹 서버가 정확히 한 웹 사이트만 호스팅할 것이라고 잘못 예측한 HTTP 명세의 실수였다.
- HTTP 설계자들은 공유 서버인 가상 호스팅을 고려하지 않았다.
- 가상 호스팅 기술 네 가지

```

URL 경로를 통한 가상 호스팅 - 서버가 어떤 사이트를 요청하는 것인지 알 수 있게 URL에 특별한 경로 컴포넌트를 추가한다. (거의 사용하지 않는다)

포트번호를 통한 가상 호스팅 - 각 사이트에 다른 포트번호를 할당하여, 분리된 웹 서버의 인스턴스가 요청을 처리한다. (비표준 포트를 쓰지 않고 싶어한다. 예:83포트 )

IP 주소를 통한 가상 호스팅 - 각 가상 사이트에 별도의 IP 주소를 할당하고 모든 IP 주소를 장비 하나에 연결한다. 웹 서버는 IP 주소로 사이트 이름을 식별한다. (규모가 아주 큰 호스팅 업자에게는 약간 어렵지만 널리 쓰인다.)

HOST 헤더를 통한 가상 호스팅 - 웹 서버는 Host 헤더로 가상 사이트를 식별할 수 있다. 

```

- Host 헤더 해석하기

```

HTTP 요청 메시지에 전체 URL이 기술되어 있으면(예를 들어 스킴과 호스트 컴포넌트가 기술되어 있을 때), Host 헤더에 있는 값은 무시하고 URL을 사용한다.

HTTP 요청 메시지에 있는 URL에 호스트 명이 기술되어 있지 않고 요청에 Host 헤더가 있으면, 호스트 명과 포트를 Host 헤더에서 가져온다.

1단계나 2단계에서 호스트를 결정할 수 없으면 클라이언트에 400 Bad Request를 반환한다.

```

- 미러링 된 서버 팜
- 서버 팜은 서로 대신할 수 있고 식별할 수 있게 설정된 웹 서버들의 집합이다.
- 미러링 된 웹 서버에는 다른 위치에 있는 콘텐츠와 정확히 같은 복제본이 있다.
- 클라이언트의 요청이 특정 서버로 가는 두 가지 방법

```

HTTP 리다이렉션 - 콘텐츠에 대한 URL은 마스터 서버의 IP를 가리키고, 마스터 서버는 요청을 받는 즉시 복제 서버로 리다이렉트시킨다.

DNS 리다이렉션 - 콘텐츠의 URL은 네 개의 IP 주소를 가리킬 수 있고, DNS 서버는 클라이언트에게 전송할 IP 주소를 선택할 수 있다.

```

- 콘텐츠 분산 네트워크(CDN)는 특정 콘텐츠의 분산을 목적으로 하는 단순한 네트워크이다.
- 네트워크의 노드는 서버, 대리 서버, 혹은 프락시 서버가 될 수 있다.
- CDN의 대리 캐시
- 대리 캐시는 복제 원 서버를 대신해 사용될 수 있다.
- 리버스 프락시라고도 불리는 대리 서버는 미러링 된 웹 서버처럼 콘텐츠에 대한 요청을 받는다.
- 대리 서버와 미러링 서버의 차이점은, 대리 서버는 보통 수요에 따라서 동작한다는 것이다.
- 대리 서버는 원 서버의 전체 콘텐츠를 복사하지는 않는다. 클라이언트가 요청하는 콘텐츠만 저장할 뿐이다.
- 서버 팜이나 분산 프락시 캐시나 대리 서버는 혼잡을 조절하고 네트워크 트래픽을 분산시킨다.
- 콘텐츠를 분산시키면, 그 콘텐츠를 사용자에게 더 가깝게 만들어 주므로 콘텐츠를 서버에서 클라이언트로의 전송하는 시간이 단축된다.

19. 배포 시스템

- FrontPage(보통 FP라 부르는)는 다양한 기능을 제공하는 마이크로소프트사의 웹 개발 및 배포 도구 집합이다.
- "어디서든 배포한다"라는 전략ㄹ의 하나로, 마이크로소프트는 FrontPage 서버 확장(FrontPage Server Extensions, FPSE)이라는 서버 측 소프트웨어 제품군을 출시했다.
- 서버 측 컴포넌트는 웹 서버와 통합되어 웹 사이트와 FrontPage를 구동시키는 클라이언트 사이에서 필요한 변환 작업을 수행한다.
- 여기서 초점을 맞춰야 할 부분은 FP 클라이언트와 FPSE 사이에서 사용하는 배포 프로토콜이다.
- 이 프로토콜은 HTTP의 기본 의미를 바꾸지 않고서도 핵심 서비스에서 HTTP를 그대로 사용할 수 있게 확장을 설계한 좋은 사례다.
- FrontPage 배포 프로토콜은 HTTP POST 요청 위에 RPC 계층을 구현했다.
- FrontPage 용어

```

가상 서버 - 같은 서버에 올라가 있는 여러 웹 사이트는 각각 유일한 도메인 이름과 IP 주소를 가진다. 

가상 서버는 웹 서버 한 개에서 웹사이트 여러 개를 호스팅하며, 각 사이티는 브라우저에서 자체 전용 서버가 있는 것처럼 보인다.

루트 웹 - 루트 웹은 보통 웹 서버의 최상위 콘텐츠 디렉터리이거나 다중 호스팅 환경에서 가상 웹 서버의 최상위 콘텐츠 디렉터리이다. 웹 서버에는 오직 한 개의 루트 웹만 있다.

서브 웹 - 서브 웹은 루트 웹의 하위디렉터리거나 완전한 FPSE 확장 웹인 다른 서브 웹의 하위디렉터리다.

```

- FrontPage 클라이언트와 FPSE는 자체 RPC 프로토콜을 사용해 통신한다.
- 이 프로토콜은 RPC 메서드와 그와 관련한 변수를 POST 요청의 본문에 기술해서 HTTP POST를 감싼다.
- 통신을 시작하려면, 클라이언트는 서버에 있는 대상 프로그램의 이름과 위치를 결정해야 한다(POST 요청을 실행시킬 수 있는 FPSE 패키지의 일부).
- 이를 위해 클라이언트는 특별한 GET 요청을 보낸다.
- 파일이 반환되면, FrontPage 클라이언트는 응답을 읽고 FPShtmlScriptUrl, FPAuthorScriptUrl, FPAdminScriptUrl과 관련된 값을 찾는다. 그곳에는 보통 다음과 같은 값이 기술되어 있다.

```

FPShtmlScriptUrl = "_vti_bin/_vti_rpc/shtml.dll" - '탐색 시간(browse time)' 명령에 관한 POST 요청을 보낼 위치를 클라이언트에게 알려준다.

FPAuthorScriptUrl = "_vti_bin/_vti_aut/author.dll" - '저작 시간(authoring time)' 명령에 관한 POST 요청을 보낼 위치를 클라이언트에게 알려준다.

FPAdminScriptURl="_vti_bin/_vti_adm/admin.dll" - 관리 동작 명령에 관한 POST 요청을 보낼 위치를 클라이언트에게 알려준다.

```

- 직접 웹 서버 콘텐츠에 접근하는 모든 배포 시스템은 배포하는 과정에서 보안에 신경 써야 한다.
- 대부분의 경우 FPSE의 보안은 웹 서버에 의존한다.
- FPSE 보안 모델은 사용자를 세 가지로 정의한다.
- 모든 제어 권한을 가지고 있는 관리자, 저작자, 브라우징 하는 일반 사용자다.
- 모든 권한은 누적된다.
- 모든 관리자는 저작할 수 있고 FrontPage 웹을 브라우징 할 수 있다.
- 저작자는 브라우징 권한을 가진다.
- IIS가 아닌 서버의 웹 서버 접근 제어 메커니즘에서는, 주어진 프로그램에 접근할 수 있게 허가된 사용자들을 따로 기술한다.
- 아파치 웹 서버에서는 .htaccess 파일에 기술한다. 넷스케이프 서버에서는 .nsconfig에 기술한다.
- 웹 분산 저작과 버저닝(Web Distributed Authoring and Versioning, WebDAV)은 웹 배포 공동 작업에 대한 또 다른 영역을 개척했다.
- WebDAV는 공동 저작에 적합한 플랫폼을 제공하려고 HTTP를 확장하는 데 집중하였다.
- WebDAV가 추가한 메서드

```

PROPFIND - 리소스의 속성을 읽는다.

PROPPATCH - 한 개 이상의 리소스에 대해 한 개 이상의 속성을 설정한다.

MKCOL - 콜렉션을 생성한다.

COPY - 특정 원본지에서 특정 목적지로 리소스나 리소스의 집합을 복사한다. 목적지가 같은 기기에 있을 필요는 없다.

MOVE - 특정 소스에서 특정 목적지에 리소스나 리소스의 집합을 이동시킨다. 목적지가 같은 기기에 있을 필요는 없다.

LOCK - 하나 이상의 리소스를 잠근다.

UNLOCK - 기존에 잠겨있는 리소스를 잠금 해제한다.

```

- WebDAV의 메서드는 요청과 응답 관련 정보를 모두 잘 다루어야 한다.
- HTTP는 보통 이 정보를 메시지 헤더에 담아 전달한다.
- 하지만 헤더에만 정보를 담아 전송하는 것은, 하나의 요청에 있는 여러 개의 리소스나 계층 관계에 있는 리소스들에 대한 정보를 헤더에 선택적으로 기술하기 어려운 점 등의 한계가 있다.
- WebDAV는 이 문제를 해결하려고 XML을 지원한다. XML의 용도


```

데이터를 어떻게 처리할 것인지 설명하는 명령 포맷

서버의 복잡한 응답을 표현하는 데 사용하는 포맷

콜렉션과 리소스를 처리하는 데 사용하는 커스텀 정보 포맷

데이터 자체를 표현할 수 있는 유연한 포맷

대부분의 국제화 관련 문제에 대한 훌륭한 해결책

```

- WebDAV는 새로운 메서드들의 기능을 더 넓혀주는 여러 HTTP 헤더를 도입했다. 추가된 헤더들은 다음과 같다.

```

DAV - WebDAV를 제공하는 서버와 통신할 때 사용한다. WebDAV에서 지원하는 모든 리소스는 OPTIONS 요청에 대한 응답에 이 헤더를 포함해야 한다.

Depth - 여러 수준의 계층 구조로 분류된 리소스에 WebDAV를 사용하기 위한 중요한 요소다.

Destination - COPY나 MOVE 메서드가 목적지 URI를 식별하는 데 쓰인다.

If - 정의되어 있는 상태 토큰은 lock 토큰뿐이다. If 헤더는 조건 집합을 정의한다.

Lock-Token - 제거되어야 할 잠금(lock)을 명시하는 용도로 UNLOCK 메서드에서 사용한다.

Owerwrite - 대상을 덮어쓸 것인지 아닌지를 기술하는 데 쓰이며 COPY나 MOVE 메서드에서 사용한다.

Timeout - 클라이언트가 필요한 잠금 타임아웃 값을 기술하는 데 사용하는 요청 헤더다.

```

- 공동 작업이란 주어진 문서에 한 명 이상의 사람이 붙어서 작업한다는 뜻이다. 
- 저자 A와 B는 명세를 함께 작성한다.
- A와 B는 독립적으로 문서를 변경한다.
- A는 저장소에 수정된 문서를 밀어 넣고, 그 다음 B는 그녀가 작업한 새로운 버전의 문서를 저장소에 밀어 넣는다.
- 안타깝게도, B는 A가 변경했다는 것을 몰라서 그녀의 버전을 A의 버전과 통합하지 않고 결국 A가 작업한 것을 잃어버리게 된다.
- 그 문제를 개선하려고 WebDAV는 잠금(lock)이라는 개념을 지원한다.
- 잠금 자체는 그 문제에 대한 완벽한 해결책은 아니다.
- 완벽한 해결책을 만들려면 버저닝과 메시징을 지원해야 한다.
- WebDAV는 두 가지 형식의 잠금을 지원한다.
- 리소스나 콜렉션에 대한 배타적 쓰기 잠금 - 잠금 소유자만 쓸 수 있게 보장한다
- 리소스나 콜렉션에 대한 공유된 쓰기 잠금- 여러 사람으로 이루어져 있는 그룹이 하나의 문서에만 작업할 수 있게 한다.

20. 리다이렉션과 부하 균형

```

HTTP 리다이렉션

DNS 리다이렉션

임의 캐스트 라우팅

정책 라우팅

아이피 맥 포워딩

아이피 주소 포워딩

웹 캐시 조직 프로토콜(WCCP)

인터캐시 커뮤니케이션 프로토콜(ICP)

하이퍼텍스트 캐싱 프로토콜(HTCP)

네트워크 요소 제어 프로토콜(NECP)

캐시 배열 라우팅 프로토콜(CARP)

웹 프락시 자동발견 프로토콜(WPAD)

```

- 리다이렉션은 현대의 웹에서는 피할 수 없는 현실이다. 왜냐햐면 HTTP 애플리케이션은 언제나 다음 세 가지를 원하기 때문이다.

```

신뢰할 수 있는 HTTP 트랜잭션의 수행

지연 최소화

네트워크 대역폭 절약

```

- 이러한 이유들 때문에, 웹 콘텐츠는 흔히 여러 장소에 배포된다. 이렇게 하면 한 곳에서 실패한 경우 다른 곳을 이용할 수 있으므로 신뢰성이 개선된다.

- 리다이렉트 할 곳
- 서버, 프락시, 캐시, 게이트웨이는 클라이언트가 그들에게 HTTP 요청을 보내고 그들이 그것을 처리한다는 관점에서 보면, 클라이언트에게 있어 모두 서버라고 할 수 있다.
- 서버, 프락시, 캐시, 게이트웨이가 모두 공통적으로 서버의 특성을 갖고 있기 때문에, 많은 리다이렉션 기법이 그들 모두에서 동작한다.
- 웹 서버는 IP별로 요청을 다룬다. 똑같이 복제된 서버들로 요청을 분산한다는 것은 같은 URL에 대해 여러 곳에서 온 요청들을 각각 최적의 웹 서버로 보내겠다는 것을 의미한다.
- 프락시는 프로토콜별로 요청을 다룬다. 이상적으로, 프락시 이웃의 모든 HTTP 트래픽은 프락시를 거쳐야 한다. 
- 예를 들어 클라이언트 근처에 프락시 캐시가 있다면, 모든 요청이 프락시 캐시로 흘러 들어가는 것이 이상적이다.
- 리다이렉션의 목표는 HTTP 메시지를 가용한 웹 서버로 가급적 빨리 보내는 것이다.
- HTTP 메시지가 인터넷을 통해 나아가는 방향은 그 메시지가 오고, 거쳐가고, 향하는 HTTP 애플리케이션과 라우팅 장치에 영향을 받는다. 예를 들면 다음과 같다.

```

브라우저 애플리케이션의 사용자는 브라우저가 클라이언트 메시지를 프락시 서버로 보내도록 설정할 수 있다.

DNS 분석자(DNS resolver)는 메시지의 주소를 지정할 때 사용될 아이피 주소를 선택한다. 이 아이피 주소는 클라이언트의 지리적 위치에 따라 달라질 수 있다.

메시지는 주소가 지정된 여러 개의 패킷으로 나뉘어 네트워크를 통과한다. 스위치와 라우터들은 패킷의 TCP/IP 주소를 검증하고 그에 근거하여 패킷을 어떻게 라우팅 할 것인지를 결정한다.

웹 서버는 HTTP 리다이렉트를 이용해 요청이 다른 웹 서버로 가도록 할 수 있다.

```

- 브라우저 설정, DNS, TCP/IP 라우팅, 그리고 HTTP는 모두 메시지를 리다이렉트하는 메커니즘을 제공한다.
- DNS 리다이렉션을 비롯한 대부분의 기법들이 트래픽을 보내려는 곳이 어떤 서버냐에 상관없이 사용될 수 있는 것에 반해
- 브라우저 설정과 같은 방법은 프락시로 향하는 리다이렉트 트래픽에 대해서만 사용할 수 있다는 점에 주의하라.

- HTTP 리다이렉션 단점

```

어떤 서버로 리다이렉트할지 결정하려면 원 서버는 상당히 많은 처리를 해야 한다. 때로는 거의 페이지 자체를 제공할 때 필요한 것과 거의 같은 양의 처리가 필요하다.

페이지에 접근할 때마다 두 번의 왕복이 필요하기 때문에, 사용자가 더 오래 기다리게 된다.

만약 리다이렉트 서버가 고장 나면, 사이트도 고장 난다.

이러한 약점 때문에, HTTP 리다이렉션은 보통 몇몇 다른 리다이렉션 기법과 함께 조합하여 사용된다.

```

- DNS 리다이렉션
- 클라이언트가 죠의 하드웨어 웹 사이트로 접근하려고 시도할 때마다, 도메인 이름 www.joes-jardware.com은 반드시 아이피 주소로 분석되어야 한다.
- DNS 분석자는 클라이언트의 운영체제일 수도 있고, 클라이언트의 네트워크에 있는 DNS 서버이거나 혹은 더 원격에 있는 DNS 서버일 수도 있다.
- DNS는 부하 균형을 위해 라운드 로빈을 사용한다.
- 임의 캐스트 어드레싱은 여러 지리적으로 흩어진 웹 서버들을 정확히 같은 아이피 주소를 갖고 클라이언트의 요청을 클라이언트에서 가장 가까운 서버로 보내주기 위해 백본 라우터의 '최단거리' 라우팅 능력에 의지한다.
- 임의 캐스트 어드레싱은 여전히 실험적인 기법이다.
- 아이피 맥 포워딩 (P534) 2계층에서 4계층으로 통신하는 부분에 관한 그림 설명
- 이더넷 네트워크에서, HTTP 메시지는 주소가 붙은 데이터 패킷의 형태로 보내진다. 
- 각 패킷은 출발지와 목적지의 아이피 주소와 TCP 포트번호로 이루어진 레이어-4 주소를 갖고 있다.
- 각 패킷은 또한 레이어-2 장비(보통 스위치나 허브)가 주의를 기울여야 하는 레이어-2 주소인 미디어 접근 컨트롤(Media Access Control, MAC) 주소도 갖고 있다.
- 아이피 주소 포워딩에서, 스위치나 다른 레이어 4를 이해하는 장비는 들어오는 패킷에 대해 TCP/IP 어드레싱을 검증하고 패킷을 목적지 맥 주소가 아니라 목적지 아이피 주소의 변경에 따라 라우팅한다.
- 맥 포워딩보다 좋은 점 하나는 목적지 서버가 한 홉 거리에 있을 필요가 없다는 것이다.
- 그저 스위치에서 업스트림의 위치를 판별할 수만 있으면 일반적인 레이어-3 종단간(end-to-end) 인터넷 라우팅이 패킷을 올바른 위치로 보내준다.
- 이러한 종류의 전달은 네트워크 주소 변환(Network Address Translation, NAT)이라고도 불린다.
- 그러나 여기에는 라우팅 대칭성이라는 문제가 있다.
- 클라이언트로부터 들어오는 TCP 커넥션을 받아주는 스위치는 그 커넥션을 관리하고 있다.
- 스위치는 반드시 그 커넥션을 통해 클라이언트에게 응답을 돌려주어야 한다.
- 그러므로 목적지 서버나 프락시로부터의 모든 응답은 반드시 그 스위치에게 돌아가야 한다. (P536 NAT그림 설명)
- 네트워크 구성요소 제어 프로토콜(Network Element Control Protocol, NECP)은
- 아이피 패킷을 전달하는 라우터나 스위치 같은 네트워크 구성요소들(NE)이
- 웹 서버나 프락시 캐시와 같이 애플리케이션 계층 요청을 처리하는 서버 구성요소들(SE)과 대화할 수 있게 해준다.
- 프락시 리다이렉션 방법 - 웹브라우저와 같은 클라이언트들이 어떻게 프락시로 가는 길을 아는가? 여기에는 세 가지 방법이 있다. 
- 명시적인 브라우저 설정 - 대부분의 브라우저에는 프락시 서버에 접촉하기 위해 프락시 이름, 아이피 주소, 포트번호를 설정할 수 있는 풀다운 메뉴가 존재한다.
- 사용자가 이를 설정하면 브라우저는 모든 요청에 대해 프락시와 접촉한다.
- 프락시 설정에는 두 가지 단점이 존재한다.
- 프락시들을 사용하도록 설정된 브라우저들은 프락시가 응답하지 않더라도 원 서버와 접촉하지 않는다.
- 만약 프락시가 다운되었거나 브라우저가 잘못 설정되었다면, 사용자는 접속 문제를 경험할 것이다.
- 네트워크 아키텍처를 변경했을 때 그 변경사항을 모든 최종사용자에게 전파하는 것이 어렵다.

- 동적인 자동 설정 - 특정 프락시에 접촉하기 접촉하기 위한 브라우저의 명시적인 설정은 네트워크 아키텍처의 변화를 제한하는데,
- 그 이유는 브라우저에 개입하여 설정을 변경하는 주체가 사용자이기 때문이다.
- 올바른 프락시 서버에 접촉하기 위해 브라우저가 동적으로 자신을 설정할 수 있게 하는 자동 설정 방법은 이 문제를 해결한다.
- 이 방법은 실제로 존재하며 프락시 자동설정(Proxy Auto-Configuration, PAC) 프로토콜이라고 불린다.
- PAC는 넷스케이프 사에 의해 정의되었으며, 거의 모든 브라우저가 지원한다.
- PAC에 깔려있는 기본 아이디어는, 브라우저들이 URL별로 접촉해야 할 프락시를 지정한 PAC파일이라 불리는 특별한 파일을 찾도록 하는 것이다.
- 브라우저는 반드시 PAC파일을 얻기 위해 지정된 서버에 접촉하도록 설정되어야 한다.
- 그런 뒤에 브라우저는 재시작할 때마다 PAC 파일을 가져온다.
- 자연스러운 가로채기 - 웹 프락시 자동발견(Web Proxy Auto-Discovery, WPAD) 프로토콜은 최종 사용자가 수동으로 프락시 설정을 할 필요도,
- 투명한 트래픽 인터셉트테 의존할 필요도 없이 웹브라우저가 근처의 프락시를 찾아내어 사용할 수 있게 해주는 방법을 제공하는 것을 목저긍로 하고 있다.
- WPAD는 HTTP 클라이언트가 PAC 파일의 위치를 알아내고 그 파일을 이용해서 적절한 프락시 서버의 이름을 알아낼 수 있게 해준다.
- WPAD 프로토콜은 설정 URL(Configuration-URL, CURL)이라고도 알려진 PAC 파일 URL을 발견한다.
- 이 PAC 파일은 적절한 프락시 서버의 주소를 반환하는 자바스크립트 프로그램을 실행한다.

```

WPAD를 이용해 PAC 파일 CURL을 찾는다.

URL에 해당하는 PAC 파일(설정파일 혹은 CFILE이라고도 알려진)을 가져온다.

프락시 서버를 알아내기 위해 그 PAC파일을 실행한다.

PAC파일이 반환한 프락시 서버에게 HTTP 요청을 보낸다.

```

- WPAD는 적절한 PAC 파일 CURL을 결정하기 위해 여러 가지 리소스 발견 기법들을 사용한다.
- 오늘날의 WPAD 명세는 다음의 기법을 순서대로 정의하고 있다.

```

동적 호스트 설정 프로토콜(Dynamic Host Configuration Protocol, DHCP)

서비스 위치 프로토콜(Service Location Protocol, SLP)

DNS에게 잘 알려진 호스트 명

DNS의 SRV 레코드

TXT 레코드의 DNS 서비스 URL들

```

- 이 다섯 메커니즘 중에서, WPAD 클라이언트에게는 오직 DHCP와 DNS에게 잘 알려진 호스트 명 기법만이 요구된다.
- WPAD 클라이언트는 DHCP 질의를 DHCP 서버에 보냄으로써 CURL을 얻는다.
- WPAD 클라이언트는 A 레코드 룩업을 DNS 서버로 보내 CURL을 얻는다.


21. 로깅과 사용 추적

- 로깅하는 필드

```

HTTP 메서드

클라이언트와 서버의 HTTP 버전

요청받은 리소스의 URL

응답의 HTTP 상태 코드

요청과 응답 메시지의 크기(모든 엔터티 본문을 포함)

트랜잭션이 일어난 시간

Referer와 User-Agent 헤더 값

```

- HTTP 메서드와 URL은 어떤 요청이 어떤 일을 하려고 했는지 가리킨다.
- 버전 정보는 클라이언트와 서버 간에 문제가 생겼을 때 디버깅하는 데 도움이 될 클라이언트와 서버에 관한 정보를 제공한다.
- HTTP 상태 코드는 요청이 성공적으로 이루졌는지, 인증 시도가 실패했는지, 리소스를 찾았는지 등 어떤 일이 일어났었는지를 알려준다.
- 요청/응답의 크기와 타임스탬프는 주로 계측하는 데 쓴다.
- 일반 로그포맷

```

remotehost - 요청한 컴퓨터의 호스트 명 혹은 IP주소

username - ident 검색을 수행했다면, 인증된 요청자의 사용자 이름이 있다.

auth-username - 인증을 수행했다면, 인증된 요청자의 이름이 있다.

timestamp - 요청 날짜와 시간

request-line - HTTP 요청의 행을 그대로 기술한다. 예를 들어 "GET /index.html HTTP/1.1"

response-code - 응답으로 보내는 HTTP 상태 코드

response-size - 응답 엔터티의 Content-Length. 응답으로부터 아무런 엔터티도 반환하지 않으면 값이 0이 된다.

예:) 209.1.32.44 - dg [03/Oct/1999:14:16:00 -0400] "GET /HTTP/1.0" 200 1724

```
- 혼합 로그포맷 = 일반 로그포맷 + Referer, User-Agent

```

Referer - Referer HTTP 헤더의 값

User-Agent - User-Agent Referer HTTP 헤더의 값

예:) 209.1.32.44 - dg [03/Oct/1999:14:16:00 -0400] "GET /HTTP/1.0" 200 1724 "http://www.joes-hardware.com/" "5.0: Mozilla/4.0 ~"

```


