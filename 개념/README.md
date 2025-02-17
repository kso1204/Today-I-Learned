# 한번 더 개념 정리

# 의존성 주입 (DI)

1. https://mangkyu.tistory.com/150

# 스프링에서 사용하는 Application Context

1. https://mangkyu.tistory.com/151

# 스프링 빈?

1. https://velog.io/@gillog/Spring-Bean-%EC%A0%95%EB%A6%AC

# static 변수와 static 메소드

1. https://mangkyu.tistory.com/47?category=872426

- static은 객체의 생성 없이 접근, static을 선언하지 않은 변수는 new를 통해 새로운 heap(메모리) 영역에 할당

- static은 모든 메모리가 공유하는 영역에 있다 (static영역)

# REST API

1. https://mangkyu.tistory.com/46?category=925341

- Resource

- Method

- Representation of Resource (json(자바스크립트 데이터 오브젝트))

# GraphQL

1. https://www.redhat.com/ko/topics/api/what-is-graphql

2. https://tech.kakao.com/2019/08/01/graphql-basic/

3. https://hwasurr.io/api/rest-graphql-differences/

# 서버 기반 인증시스템 VS 토큰 기반 인증 시스템

1. https://mangkyu.tistory.com/55?category=925341

# JWT

1. https://mangkyu.tistory.com/56

# SHA, RSA, AES

1. https://stage-loving-developers.tistory.com/23

- 암호화 - 공개키, 복호화 - 개인키

- SHA - 단방향 해싱, RSA - 비대칭키 암호화 방식 (공개키 != 개인키), AES - 대칭키 암호화 방식 (공개키 = 개인키)

# Cache

1. https://mangkyu.tistory.com/69?category=925341

- 캐시는 Cache Hit, Cache miss, Long Tail의 주요 키 포인트

- Long Tail이란 상위 20%의 요구가 리소스의 대부분을 사용하는 것

# SQL 고급 

1. https://mangkyu.tistory.com/25?category=761304

# 트랜잭션, 동시성 제어, 회복

1. https://mangkyu.tistory.com/25?category=761304

- 트랜잭션이란 DBMS에서 데이터를 다루는 논리적인 작업의 단위

- Commit이란 트랜잭션의 수행이 완료됨을 트랜잭션 관리자에게 알려 주는 연산

- 트랜잭션은 전체가 수행되거나 또는 전혀 수행되지 않아야 한다.(All or Nothing)
 
# Stream API

1. https://mangkyu.tistory.com/112

2. 람다식이란? 함수를 하나의 식으로 표현한 것 

3. 함수를 람다식으로 표현하면 메소드의 이름이 필요 없기 때문에, 람다식은 익명 함수의 한 종류라고 볼 수 있다.

4. 함수형 인터페이스의 인스턴스를 생성하여 함수를 변수처럼 사용하는 람다식  

5. 장점 -> 함수를 만드는 과정없이 한번에 처리할 수 있어 생산성이 높아진다.

6. 병렬프로그래밍이 용이하다.

7. 단점 -> 람다를 사용하면서 만든 익명함수는 재사용이 불가능하다.

8. 디버깅이 어렵다.

9. 람다를 남발하면 비슷한 함수가 중복 생성되어 코드가 지저분해질 수 있다.

10. 함수형 인터페이스란? 함수를 1급 객체처럼 다룰 수 있는 어노테이션으로, 인터페이스에 선언하여 단 하나의 추상 메소드만을 갖도록 제한하는 역할

11. Java에서 제공하는 함수형 인터페이스 네 가지

- Supplier<\T>

- 매개변수 없이 반환값 만을 갖는 함수형 인터페이스이다.

- T get()을 추상메소드로 가지고 있다.

- Consumer<\T>

- Function<\T,R>

- Predicate<\T>

- 내용이 너무 어려워서 복습이 필요해보임; https://mangkyu.tistory.com/113

# 디자인 패턴

1. 생성 패턴

- 팩토리 패턴 - 객체를 생성하기 위한 디자인 패턴

- 추상 팩토리 패턴 - 객체를 생성하는 팩토리를 생성하기 위한 디자인 패턴

- 빌더 패턴 - 상황에 따라 동적인 인자를 필요로 하는 객체를 생성하기 위한 디자인 패턴

- 싱글톤 패턴 - 객체를 1개만 생성하여 항상 참조가능하도록 고안된 디자인 패턴

2. 구조 패턴

- 어댑터 패턴 - 호환성이 맞지 않는 두 클래스를 연결하여 사용하기 위한 디자인 패턴

- 프록시 패턴 - 어떤 객체에 접근하기 위해 대리인을 사용하는 패턴

- 퍼사드 패턴 - 어떤 복합적인 기능에 대해 간략화된 인터페이스를 제공하는 디자인 패턴

3. 행위 패턴

- 전략 패턴 - 상황에 따라 다른 전략을 사용하기 위한 디자인 패턴

- 옵저버 패턴 - 값을 관찰하여 빠르게 반영하기 위한 디자인 패턴

- 커맨드 패턴 - 실행될 기능을 캡슐화하여 재사용성이 높은 클래스를 설계하기 위한 디자인 패턴

# 가상화

1. https://mangkyu.tistory.com/86

2. 가상화란 가상화를 관리하는 소프트웨어(주로 HyperVisor)를 사용하여 하나의 물리적 머신에서 가상 머신(VM)을 만드는 프로세스이다.

3. 가상 머신은 물리적 머신과 동일한 역할 및 성능을 수행하지만, cpu와 메모리 및 스토리지와 같은 물리적 머신의 컴퓨팅 리소스를 사용한다.

4. HyperVisor는 필요에 따라 각 가상 머신에 이러한 컴퓨팅 리소스를 할당한다.

5. 최근에는 Docker와 같은 컨테이너 가상화 기술이 등장하기도 하였다. 도커를 윈도우에서 사용하는 경우에는 HyperVisor를 사용하지만,

6. 리눅스에서 사용하는 상황에서는 커널의 특징을 이용하기 때문에 HyperVisor를 사용하지 않는다.

7. 가상화를 이용하면 서버를 통합하고 서버의 자원을 최대한으로 활용함으로써 서버 급증 문제를 해결할 수 있다.

# Nginx Vs Apache

1. Nginx는 동적인 페이지 구현이 어렵기 때문에, 동적인 페이지를 구현하기 위해 외부 프로그램의 도움을 받는다.

2. 웹서버에서 요청을 받아 그 요청을 외부 프로그램에 넘겨주면, 외부 프로그램은 프로그램 파일을 읽어 html로 반환하는 단계를 거치게 됩니다. 

3. 이 과정을 CGI라고 하는데, PHP-FPM(PHP FastCGI Process Manager)도 CGI에 해당 된다.

4. Apache의 경우에는 해당 역할을 하는 모듈이 내장되어 있다. 그럼에도 php-fpm 사용한다.

5. https://cornswrold.tistory.com/429

6. https://sorjfkrh5078.tistory.com/289

# 정규화

1. https://mangkyu.tistory.com/110?category=761304

2. 정규화의 기본 목표는 테이블간에 중복된 데이터를 허용하지 않는 것

3. 제 1정규화란 테이블의 컬럼이 원자값을 갖도록 테이블을 분해하는 것

4. 제 2정규화란 제 1정규화를 진행한 테이블에 대해 완전 함수 종속을 만족하도록 테이블을 분해하는 것이다.

5. 여기서 완전 함수 종속이란 기본키의 부분집합이 결정자가 되어선 안 된다는 것이다.

6. 제 3정규화란 제 2정규화를 진행한 테이블에 대해 이행적 종속을 없애도록 테이블을 분해하는 것이다.

7. 여기서 이행적 종속이라는 것은 A->B, B->C가 성립할 때 A->C가 성립되는 것을 의미한다.

8. BCNF 정규화란 제 3정규화를 진행한 테이블에 대해 모든 결정자가 후보키가 되도록 테이블을 분해하는 것이다.

# 리플리케이션

1. https://mangkyu.tistory.com/97?category=761304

2. 여러 개의 DB를 권한에 따라 수직적인 구조(Master-Slave)로 구축하는 방식이다.

3. Master Node는 쓰기 작업만, Slave Node는 읽기 작업만 처리한다.

4. Master와 Slave간의 데이터 무결성 검사(데이터가 일치하는지)를 하지 않는 비동기방식으로 데이터를 동기화한다.

4. 장점 -> DB 요청의 60 ~ 80% 정도는 읽기 작업이기 때문에 Replication만으로도 충분히 성능을 높일 수 있다.

5. 비동기 방식으로 운영되어 지연 시간이 거의 없다.

6. 단점 -> 노드들 간의 동기화가 보장되지 않아 일관성있는 데이터를 얻지 못할 수 있다.

7. Master 노드가 다운되면 복구 및 대처가 까다롭다.

# 클러스터링

1. 클러스트링이란 여러 개의 DB를 수평적인 구조로 구축하는 방식이다.

2. 클러스트링은 분산 환경을 구성하여 Single point of failure와 같은 문제를 해결할 수 있는 Fail Over 시스템을 구축하기 위해서 사용된다.

3. 클러스트링은 동기 방식으로 노드들 간의 데이터를 동기화 한다.

4. 장점 -> 노드들 간의 데이터를 동기화하여 항상 일관성있는 데이터를 얻을 수 있다.

5. 1개의 노드가 죽어도 다른 노드가 살아 있어 시스템을 계속 장애 없이 운영할 수 있다.

5. 단점 -> 여러 노드들 간의 데이터를 동기화하는 시간이 필요하므로 Replication에 비해 쓰기 성능이 떨어진다.

6. 장애가 전파된 경우 처리가 까다로우며, 데이터 동기화에 의해 스케일링에 한계가 있다.

# IPC

1. https://mangkyu.tistory.com/9?category=761303

1. 내부 프로세스들 끼리 통신을 하는 것

2. 프로세스가 통신 가능하다는 것은 서로 다른 프로세스가 데이터를 주고 받을 수 있다는 것이며, 

3. 동시에 접근 가능한 메모리 즉, 프로세스들이 공유하는 메모리가 필요하다는 뜻입니다.

# 프로세스 Vs 쓰레드

1. 프로세스는 생성되면서 *PC(Program count - 다음에 수행해야 하는 명령어의 주소를 가리키는 레지스터)를 포함하여 메모리 공간등을 복사하여 자원을 할당하지만,

2. 쓰레드는 메모리 공간과 자원들을 공유한다.

3. 즉, 프로세스와 쓰레드를 생성하기 전에 a라는 변수를 선언해 놓았다고 하면 프로세스는 a를 각각 한 개씩, 쓰레드는 a를 공유한다.

4. 그래서 프로세스는 통신을 할 공간이 없기 때문에 별도의 공간을 만들어줘야 해서 프로세스 간의 통신이 쓰레드 간의 통신보다 더 어렵다.

5. 프로세스 -> 메모리에 올라와 실행되고 있는 프로그램의 인스턴스

6. 운영체제로부터 독립된 메모리 영역을 할당 받는다. (다른 프로세스의 자원에 접근 X)

7. 프로세스들은 독립적이기 때문에 IPC를 사용해야 한다.

8. 프로세스는 최소 한 개의 쓰레드를 가지고 있다.

9. 쓰레드 -> 프로세스 내에서 할당받은 자원을 이용해 동작하는 실행 단위

10. 쓰레드는 프로세스 내에서 Stack만 따로 할당 받고, Code, Data, Heap 영역은 공유한다.

11. Stack을 분리한 이유는 Stack에는 함수의 호출 정보가 저장되는데, Stack을 공유하면 LIFO 구조에 의해 실행 순서가 복잡해지기 때문에 실행 흐름을 원활하게 하기 위함이다.

# 컨텍스트 스위칭

1. Context Switching 이란 인터럽트를 발생시켜 CPU에서 실행중인 프로세스를 중단하고, 다른 프로세스를 처리하기 위한 과정입니다.

2. 현재 실행중인 프로세스의 상태(Context)를 먼저 저장하고, 다음 프로세스를 동작시켜 작업을 처리한 후에 이전에 저장된 프로세스의 상태를 다시 복구합니다.

# 도커

1. https://velog.io/@ckstn0777/%EB%8F%84%EC%BB%A4%EB%9E%80-%EB%AC%B4%EC%97%87%EC%9D%B8%EA%B0%80

2. 도커란 리눅스 컨테이너를 기반으로 하여 특정한 서비스를 패키징하고 배포하는데 유용한 오픈소스 프로그램이다.

3. 가상머신은 HyperVisor를 이용해 Guest OS를 만들어낸다.

4. 예를들어, 윈도우 운영체제를 메인으로 쓰고 있다면 이는 Host OS가 되는 것이고 이 위에 Ubuntu를 가상머신위에 구동시킨다면 이는 Guest OS가 되는 것이다. 

5. Guest OS를 구동시키려면 Host OS에서 자원을 일부 사용해야 한다. 따라서 Host OS도 느려지고, Guest OS도 성능이 그리 좋은 편은 아니다.

6. 도커의 컨테이너는? 가상머신에 비해 꼭 필요한 것만 담겨서 구동 된다는 차이가 있다.

7. 즉, 컨테이너에 필요한 커널은 호스트의 커널과 공유해서 사용하고, 컨테이너 안에는 애플리케이션을 구동하는데 필요한 

8. 라이브러리 및 실행파일만 존재하기 때문에 컨테이너를 이미지로 만들 경우 용량이 대폭 줄어든다.

9. 도커의 가장 큰 장점은 애플리케이션 독립성이다. 호스트 OS와도, 다른 컨테이너와도 독립된 공간을 보장 받기 때문에 충돌 발생 염려가 없다.

10. 또한 컨테이너 내부에 작업을 한 후에 배포하려고 한다면 도커 이미지라는 패키지로 만들어서 운영서버에 전달만 하면 된다.

11. 모놀리식 애플리케이션 방식에서 마이크로서비스 구조로 변화가 쉽다. 즉, 컨테이너 하나당 하나의 기능만을 제공하는 모듈로 만들어서 부하가 많은 모듈은 여러개 더 만들고 하는 

12. 조정이 가능해진다.

13. https://tpcable.co.kr/45

14. https://www.44bits.io/ko/keyword/linux-container

# 윈도우 컨테이너

1. https://tech.devsisters.com/posts/intro-windows-container/

2. https://docs.microsoft.com/ko-kr/virtualization/windowscontainers/deploy-containers/linux-containers

# 메모리

1. http://tcpschool.com/c/c_memory_structure

# 컴파일 Vs 런타임

1. https://dd-corp.tistory.com/9

# constant pool (상수 풀)

1. https://devlog-wjdrbs96.tistory.com/248

# SSR or CSR

1. https://d2.naver.com/helloworld/7804182

2. https://tecoble.techcourse.co.kr/post/2021-09-10-ssr/

3. https://bbbyung2.tistory.com/65

# 웹은 어떻게 동작할까?

1. https://devcecy.com/%ec%9b%b9%ec%9d%80-%ec%96%b4%eb%96%bb%ea%b2%8c-%eb%8f%99%ec%9e%91%ed%95%a0%ea%b9%8c/

# 브라우저의 렌더링 과정 ****

1. https://devcecy.com/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EB%A0%8C%EB%8D%94%EB%A7%81-%EB%90%A0%EA%B9%8C/

# 바이트 코드? 바이너리 코드?

1. https://usefultoknow.tistory.com/entry/%EB%B0%94%EC%9D%B4%EB%84%88%EB%A6%AC%EC%99%80-%EB%B0%94%EC%9D%B4%ED%8A%B8-%EC%BD%94%EB%93%9C%EB%9E%80-%EA%B8%B0%EA%B3%84%EC%96%B4%EB%9E%80

# 브라우저와 렌더링 엔진, 자바스크립트 엔진

1. https://jsmokblog.tistory.com/20

# 엘라스틱 서치? TF-IDF

1. https://velog.io/@jakeseo_me/%EC%97%98%EB%9D%BC%EC%8A%A4%ED%8B%B1%EC%84%9C%EC%B9%98-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0-1-%EC%97%98%EB%9D%BC%EC%8A%A4%ED%8B%B1%EC%84%9C%EC%B9%98%EB%8A%94-%EA%B2%80%EC%83%89%EC%97%94%EC%A7%84%EC%9D%B4%EB%8B%A4

2. https://velog.io/@jakeseo_me/%EC%97%98%EB%9D%BC%EC%8A%A4%ED%8B%B1%EC%84%9C%EC%B9%98-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0-2-DB%EB%A7%8C-%EC%9E%88%EC%9C%BC%EB%A9%B4-%EB%90%98%EB%8A%94%EB%8D%B0-%EC%99%9C-%EA%B5%B3%EC%9D%B4-%EA%B2%80%EC%83%89%EC%97%94%EC%A7%84

2. https://webisfree.com/2017-05-24/%EC%97%98%EB%9D%BC%EC%8A%A4%ED%8B%B1%EC%84%9C%EC%B9%98-%EC%95%8C%EC%95%84%EB%B3%B4%EA%B8%B0

```

조금 더 추가 말씀을 드리면,

ES에서는 삭제를 할 때에 해당 document에 delete tag를 붙이고, 새 document를 갈아 끼웁니다.
그 이유는 샤드에 데이터를 저장할 때, immutable lucene segment로 저장하고 refresh하기 때문입니다. 쉽게 말해서 그냥 안바뀌는 값입니다.
JAVA의 String이 그런 것 처럼이요.

그래서 그 document는 실제로 언제 지워지냐면, segment merge가 일어날 때입니다. segment가 무한히 많아지면 찾아야할 segment가 늘어나니 느려지겠죠.
그래서 그걸 주기적으로 merge 하는 merge policy가 default로 있게 됩니다.

그렇다면 merge가 되기 전까지는 memory에 남아있겠죠? 그리고 그걸 검색에서 제외하기 위한 연산이 들어갈 겁니다. 그게 바로 약점입니다.

다양한 걸 설정할 수는 있지만 default로 해놓아도 크게 신경쓰지 않고 잘 merge가 되긴 합니다. 물론 force merge도 할 수 있구요. (반드시 indexing하지 않을 때 merge해야 한다고 합니다)
그래서 document의 진정한 update는 아니다 라는 설명이 맞는 거구요.
그냥 공부하다가 아는게 보여서 들렀습니다.

```



# SEO

1. https://www.hedleyonline.com/ko/blog/seo-guide-2021/

# 이벤트 드리븐 **

1. https://velog.io/@limprove89/%EC%9D%B4%EB%B2%A4%ED%8A%B8-%EA%B8%B0%EB%B0%98-%ED%94%84%EB%A1%9C%EA%B7%B8%EB%9E%98%EB%B0%8D-%EC%93%B0%EB%A0%88%EB%93%9C

2. https://12bme.tistory.com/540

3. https://heeonii.tistory.com/3

# 이벤트 루프

1. https://poiemaweb.com/js-event

# Web Server , WAS

1. https://gmlwjd9405.github.io/2018/10/27/webserver-vs-was.html

2. 웹 서버내에 동적 프로그래밍 기능 추가하는 게 웹 서버 + CGI로 PHP에서 사용하는 것 (인터프리터) - PHP 파서

3. 웹 서버 뒤에 WAS를 연결해서 사용하는 것이 자바에서 사용하는 것 (컴파일 필요)

# PHP

1. https://dev-youngjun.tistory.com/67

# Java?

1. https://jinbroing.tistory.com/205

# MSA?

1. https://prodo-developer.tistory.com/137

2. https://mangkyu.tistory.com/108?category=925341