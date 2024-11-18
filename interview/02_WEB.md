## JSP vs Servlet
- JSP
  - html 내에 자바코드를 블록화하여 삽입한 것.
  - JAVA in HTML.
- Servlet
  - Container가 이해할 수 있도록 구성된 자바코드로 이루어진 것.
  - HTML in JAVA.
- Ref.
[effiRin](https://velog.io/@effirin/Servlet%EA%B3%BC-JSP%EC%97%90-%EB%8C%80%ED%95%B4)
<br><br><br>



## Servlet과 Servlet 컨테이너
- Servlet(서블릿)이란?
  - 서블릿(Servlet)이란 동적 웹 페이지를 만들 때 사용되는 자바 기반의 웹 애플리케이션 프로그래밍 기술이다.
  - 서블릿은 WAS내의 서블릿 컨테이너에서 동작하며, 요청(Request)을 받으면 요청에 맞는 로직을 실행하고 클라이언트에게 HTTP 형식으로 응답(Response)하게 된다.
- Servlet(서블릿)의 주요 특징
  - 클라이언트의 요청에 동적으로 응답하는 웹 어플리케이션 컴포넌트이다.
  - HTML을 사용하여 응답한다.
  - JAVA의 스레드를 이용한다.
  - MVC 패턴의 Controller 역할을 맡는다.
- Servlet(서블릿) 동작 과정
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/2efde5cc-ccd1-499e-ac82-3cee4395f600)
    1. 클라이언트 요청
    2. HttpServletRequest, HttpServletResponse 객체 생성
    3. Web.xml이 어느 서블릿에 대해 요청한 것인지 탐색
    4. 해당하는 서블릿에서 service() 메서드 호출 
    5. doGet() 또는 doPost() 호출 
    6. 동적 페이지 생성 후 ServletResponse 객체에 응답 전송
    7. HttpServletRequest, HttpServletResponse 객체 소멸
- Servlet 컨테이너란?
  - 서블릿을 담고 관리해주는 컨테이너이다.
  - 서블릿 컨테이너는 서블릿 객체를 자동으로 생성, 호출, 종료 시켜준다. 즉, 라이프 사이클을 관리해준다.
- Ref.
[NKLCWDT](https://github.com/NKLCWDT/cs/blob/main/Spring/Servlet.md),
[Song's DLog](https://velog.io/@falling_star3/Tomcat-%EC%84%9C%EB%B8%94%EB%A6%BFServlet%EC%9D%B4%EB%9E%80),
[코드 연구소](https://code-lab1.tistory.com/210)
<br><br><br>



## Session과 Cookie
- Session
  - 저장위치 : 웹 서버
  - 브라우저를 종료하거나, 서버에서 세션을 삭제했을 때 삭제된다.
  - 각 클라이언트에 고유 Session ID를 부여하고, 이 Session ID로 클라이언트를 구분한다.
  - 동작순서
    1. 클라이언트가 페이지를 요청한다.
    2. 서버는 접근한 클라이언트의 Request-Header 필드인 Cookie를 확인하고, 클라이언트가 해당 Session ID를 보냈는지 확인한다.
    3. Session ID가 존재하지 않는다면, 서버는 Session ID를 생성한 후 클라이언트에게 전달한다.
    4. 서버에서 클라이언트로 돌려준 Session ID를 쿠키로 사용하여 서버에 저장한다.
    5. 클라이언트 접속 시, 세션 쿠키를 이용하여 Session ID 값을 서버에 전달한다.
- Cookie
  - 저장위치 : 클라이언트(=접속자 PC)
  - 사용자 인증이 유효한 시간을 명시할 수 있으며, 유효 시간이 정해지면 브라우저가 종료되어도 인증이 유지된다.
  - 동작순서
    1. 클라이언트가 페이지를 요청한다.
    2. 웹 서버는 쿠키를 생성하고 정보를 담은 후 HTTP 화면을 돌려줄 때 같이 클라이언트에게 반환한다.
    3. 클라이언트가 이후 서버에 요청할 때 요청과 함께 쿠키를 전송한다.
    4. 동일 사이트 재방문 시, 클라이언트의 PC에 해당 쿠키가 있을 경우 요청 페이지와 함께 쿠키를 전송한다.
- Ref.
[bolee](https://velog.io/@octo__/%EC%BF%A0%ED%82%A4Cookie-%EC%84%B8%EC%85%98Session)
<br><br><br>



## Framework와 Library
- Framework
  - 뼈대가 되는 부분을 미리 구현한 클래스, 인터페이스, 메서드 등의 집합체이다.
  - 개발자가 소프트웨어를 개발함에 있어 코드를 구현하는 개발시간을 줄이고, 코드의 재사용성을 증가시키기 위하여 클래스 묶음이나 뼈대, 틀을 제공하는 것을 말한다.
  - Framework의 특징
    - 개발자가 따라야 하는 가이드를 제공한다.
    - 개발할 수 있는 범위가 정해져있다.
    - 정형화 되어있어 일정수준 이상의 품질을 기대할 수 있다.
- Library
  - 자주 쓰일 만한 기능들을 따로 구현하여 모아 놓은 클래스의 집합체이다.
- 차이점
  - Framework와 Library의 차이는 제어 흐름에 대한 주도성이 누구에게 있는가에 있다.
  - 프레임워크는 그 스스로 제어 흐름의 주도성을 갖는 반면, 라이브러리는 개발자가 가지고 있다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/9cfbb7e6-9208-4f54-b6f2-4fd7121d0bb3)
- Ref.
[Coding Planet](https://sharonprogress.tistory.com/169)
<br><br><br>



## 스프링 개념
- 스프링이란?
  - 자바 엔터프라이즈 개발을 편하게 해주는 오픈소스
  - 경량급 애플리케이션 프레임워크
- 특징
    - 경량 컨테이너로써 자바 객체를 직접 관리한다.
    - 객체 생성, 소멸과 같은 라이프 사이클을 관리하며 스프링으로부터 필요한 객체를 얻어올 수 있다.
  - 스프링은 Plain Old Java Object 방식의 프레임워크이다.
    - 일반적인 J2EE 프레임워크와 비교해봤을 때, 구현을 위하여 특정 인터페이스를 구현하거나 상속 받을 필요가 없기 때문에 기존에 존재하는 라이브러리 등을 지원하기에 용이하고 가볍다.
  - 스프링은 제어 반전(IoC : Inversion of Control)을 지원한다.
    - 컨트롤의 제어권이 사용자가 아니라 프레임워크에 있어서 필요에 따라 스프링에서 사용자의 코드를 호출한다.
  - 스프링은 의존성 주입(DI : Dependency Injection)을 지원한다.
    - 각각의 계층이나 서비스들 간에 의존성이 존재할 경우 프레임워크가 서로 연결시켜준다.
  - 스프링은 관점 지향 프로그래밍(AOP : Aspect-Oriented Programming)을 지원한다.
    - 트랜잭션이나 로깅, 보안과 같이 여러 모듈에서 공통적으로 사용하는 기능의 경우 해당 기능을 분리하여 관리할 수 있다.
- 스프링 구조
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/d38101c3-087a-4248-8a61-1847d11dde7a)
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/5)
<br><br><br>



## 스프링 MVC
- 스프링 MVC란?
  - MVC 패턴에 기반을 둔 웹 프레임워크이다.
- MVC 패턴
  - Model, View, Controller의 약자이며, 클라이언트와 상호작용하는 소프트웨어를 설계함에 있어서 세 가지 요소로 나누어 설계하는 것을 뜻한다.
    - Model
      - Model은 애플리케이션의 정보, 데이터의 가공을 책임지며 데이터베이스와 상호작용하여 비즈니스 로직을 처리하는 모듈.
      - 즉, 컴포넌트를 뜻한다.
    - View
      - View는 클라이언트 단에서 보여지는 결과화면을 반환하는 모듈.
      - 즉, 사용자 인터페이스 요소를 뜻한다.
    - Controller
      - Controller는 클라이언트로부터 요청이 들어왔을 때, 어떤 로직을 실행시킬 것인지 판단하며 Model(모델)과 View(뷰)를 연결해주며 제어하는 모듈.
- 스프링 MVC의 구성요소와 동작순서
  ![image](https://github.com/1992choi/today-i-learned/assets/27760576/e675f1ab-e106-415c-a02a-df22a2bf5112)
  - 구성요소
    - Dispatcher Servlet
      - 클라이언트의 요청을 받아 컨트롤러에게 전달한다.
      - 컨트롤러가 리턴한 결과값을 View에 전달한다.
    - Handler Mapping
      - 클라이언트의 요청 URL을 확인하여 요청을 처리할 컨트롤러를 결정한다.
    - Handler Adapter
      - DispatcherServlet의 처리 요청을 변환해서 컨트롤러에게 전달한다.
    - Controller
      - 클라이언트의 요청에 대한 처리를 하고 결과를 리턴한다.
    - ModelAndView
      - 컨트롤러가 처리한 결과 정보 및 뷰 선택에 필요한 정보를 담고 있다.
    - View Resolver
      - 컨트롤러의 처리 결과를 생성할 뷰를 결정한다.
    - View
      - 컨트롤러의 처리 결과를 보여줄 화면을 생성한다.
  - 동작순서
    - 1.클라이언트로부터 요청이 발생하면 모든 요청은 Dispatcher Servlet으로 전달된다.
    - 2.요청에 대하여 Handler Mapping은 처리를 할 Controller가 있는지 탐색한다. 
    - 3.Controller가 결정되면 Dispatcher Servlet은 Handler Adaptor에게 요청 처리를 위임한다.
    - 4.Handler Adaptor에 의해서 컨트롤러가 호출되고 비즈니스 로직이 수행된다. 
    - 5.Controller는 비즈니스 로직을 처리하고 그 결과를 Model객체에 저장하여 View 페이지명과 함께 응답한다. 
    - 6.Dispatcher Servlet은 view name을 View Resolver에게 전달하여 View 객체를 얻는다.
    - 7.View를 호출하면 템플릿 엔진이 동작하여 HTML을 구성한다.
    - 8.최종적으로 View의 내용이 클라이언트에게 전달된다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/6)
<br><br><br>



## 스프링 DI
- DI란?
  - 의존성 주입(DI)이란, 객체를 직접 생성하는 것이 아니라 외부에서 객체를 생성한 후 주입 시켜주는 방식을 뜻한다.
- 주입 방법
  1. 필드 주입
  2. 수정자 주입(= Setter 주입)
  3. 생성자 주입
- 장점
  - 코드의 재사용성, 유연성이 높아진다.
  - 객체 간 결합도가 낮기 때문에 한 클래스를 수정했을 때, 다른 클래스도 수정해야 하는 상황을 막아준다.
  - 유지보수가 쉬워지며, 테스트가 용이해진다.
  - 확장성을 가진다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/13)
<br><br><br>



## 스프링 IoC
- IoC (Inversion of Control)란?
  - Bean의 생성과 의존 관계 설정, 사용, 제거 등의 작업을 애플리케이션 코드 대신 스프링 컨테이너가 담당한 관리하는 것을 뜻한다.
  - 즉, 객체를 제어하고 관리하는 역할이 개발자로부터 스프링 컨테이너로 역전된다는 뜻이다.
- Bean과 스프링 컨테이너
  - Bean
    - 스프링 컨테이너가 관리하는 자바 객체를 뜻한다.
  - 스프링 컨테이너
    - 스프링에서 빈(Bean)을 관리하는 공간을 뜻한다.
    - 스프링 컨테이너는 IoC 컨테이너 혹은 DI 컨테이너라고도 불리는데, 이는 스프링 컨테이너가 IoC 혹은 DI를 도맡아 진행하기 때문이다.
    - 스프링 컨테이너는 크게 두 종류(BeanFactory, ApplicationContext)로 나눌 수 있다.
    - ApplicationContext 컨테이너가 BeanFactory의 기능을 포괄하면서 추가적인 기능을 제공하기 때문에 대부분의 경우에는 ApplicationContext를 사용한다.
      - BeanFactory와 ApplicationContext 관계
        ![image](https://github.com/1992choi/today-i-learned/assets/27760576/846e9d7f-aa86-464f-8628-560cc2ac2b8a)
      - BeanFactory
        - 스프링 컨테이너의 최상위 인터페이스이다.
        - 스프링 빈을 관리하고 조회하는 역할을 담당한다.
      - ApplicationContext
        - BeanFactory 기능을 모두 상속받아서 제공한다.
        - 다음과 같은 부가기능들을 제공한다.
          1. 메시지 소스를 활용한 국제화 기능
          2. 환경변수 - 로컬, 개발, 운영 등을 구분해서 처리
          3. 애플리케이션 이벤트 관리
          4. 편리한 리소스 조회
- IoC 사용 이점
  - 의존성 관리를 IoC 컨테이너가 하므로 개발자는 비즈니스 로직에만 신경을 쓰면 된다.
  - 객체의 생성과 소멸 등 생명주기를 관리해주므로 메모리를 효율적으로 사용할 수 있다.
  - 라이프사이클 인터페이스를 이용하여 원하는 작업을 할 수 있다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/14)
<br><br><br>



## IoC와 DL/DI
- IoC와 DL/DI 관계도
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/73277fd2-3dfd-42bd-9e8a-cab7add2353d)
- DL(Dependency Lookup)
  - 의존성 검색(DL)이란, Bean에 접근하기 위해 컨테이너가 제공하는 API를 이용하여 Bean을 Lookup하는 것이다.
  - 자신이 필요로하는 오브젝트를 능동적으로 찾지만, 어떤 클래스의 오브젝트를 이용할지는 결정하지 않는다.
  - ApplicationContext를 통해 필요한 빈을 검색할 수 있다.
  - 스프링이 추구하는 개발은 특정 환경과 기술에 종속되지 않은 POJO방식인데, 이 방식은 스프링에 종속성이 생기게 되므로 권고되는 방식은 아니다.
- DI(Dependency Injection)
  - 의존성 주입(DI)이란, 객체를 직접 생성하는 것이 아니라 외부에서 객체를 생성한 후 주입 시켜주는 방식을 뜻한다.
- Ref.
[행복한 백수 개발자](https://happy-playboy.tistory.com/entry/%EB%B0%B1%EC%88%98%EC%9D%98-%EC%8A%A4%ED%94%84%EB%A7%81-IoC%EC%99%80-DI%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C),
[Hong JinHyung](https://hjhng125.github.io/spring/dependency-lookup/)
<br><br><br>



## 스프링 AOP
- AOP(Aspect Oriented Programming)란?
  - Aspect Oriented Programming의 약자로 관점 지향 프로그래밍이라고 불린다.
  - 흩어진 관심사(Crosscutting Concerns)를 모듈화하여 제공하는 프로그래밍 기법이다.
- AOP 핵심 용어
  - Aspect
    - 여러 핵심 기능에 적용될 관심사 모듈을 뜻한다.
    - Aspect는 구체적인 기능을 구현한 Advice와 Advice가 어디에서 적용될지를 결정하는 PointCut의 포괄적인 개념이다.
  - JoinPoint
    - 추상적인 개념으로 Advice가 적용될 수 있는 모든 위치를 뜻한다.
    - 애플리케이션의 어떤 지점에 AOP를 사용하여 추가적인 로직을 삽입할 지 정의한다.
  - Advice
    - JoinPoint에서 실행되는 코드를 말한다.
    - 로그 출력이나 트랜잭션 관리 등의 코드가 기술된다.
  - Target
    - Aspect를 적용할 대상을 뜻한다.
    - 적용 방식에 따라 클래스, 메서드 등이 될 수 있다.
  - Pointcut
    - JoinPoint 중에서 Advice가 적용될 위치를 선별하는 기능이다.
    - 이를통해 메서드명에 'service' 라는 문자열이 있을때만 어드바이스를 호출되도록 기술하는 것이 가능해진다.
  - Advisor
    - 스프링 AOP에서만 사용되는 용어로 Advice + Pointcut 한 쌍을 일컫는다.
  - Weaving
    - Pointcut으로 결정한 타겟의 JoinPoint에 Advice를 적용하는 것을 뜻한다.
- 코드 예시
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/85197023-e16a-482a-8150-3da98f9ae049)
- 적용방식
  - 컴파일 시점
    - .java 파일을 컴파일러를 통해 .class를 만드는 시점에 부가 기능 로직을 추가하는 방식이다.
    - 모든 지점에 적용 가능하다.
    - AspectJ가 제공하는 특별한 컴파일러를 사용해야 하기 때문에 특별할 컴파일러가 필요한 점과 복잡하다는 단점이 있다.
  - 클래스 로딩 시점
    - .class 파일을 JVM 내부의 클래스 로더에 보관하기 전에 조작하여 부가 기능 로직 추가하는 방식이다.
    - 모든 지점에 적용 가능하다.
    - 특별한 옵션과 클래스 로더 조작기를 지정해야하므로 운영하기 까다롭다.
  - 런타임 시점
    - 스프링이 사용하는 방식으로 컴파일이 끝나고 클래스 로더에 이미 다 올라가 자바가 실행된 다음에 동작하는 런타임 방식이다.
    - 실제 대상 코드는 그대로 유지되고 프록시를 통해 부가 기능이 적용된다.
    - 프록시는 메서드 오버라이딩 개념으로 동작하기 때문에 메서드에만 적용 가능하다.
    - 특정 컴파일러, 복잡한 옵션, 클래스 로더 조작기 등을 사용하지 않아도 스프링만 있으면 AOP를 적용할 수 있다.
- 스프링 AOP 특징
  - 순수 자바로 구현되었기 때문에 특별한 컴파일 과정이 필요하지 않다.
  - 프록시 기반 AOP를 지원한다.
  - Spring AOP는 메서드 조인 포인트만 지원한다.
- 스프링 AOP Advice 종류
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/2c3dae3f-f8b6-4f69-b5ec-c54e52a16b29)
  - @Before
    - JointPoint가 실행되기 이전 시점에 실행된다.
  - @After
    - JointPoint의 정상 완료 여부에 상관없이 항상 실행된다.
  - @AfterRetruning
    - JointPoint가 정상 완료된 후 실행된다.
  - @Around
    - 메서드 호출 전후에 실행된다.
  - @AfterThrowing
    - 메서드가 예외를 던지는 경우 실행된다.
- 장점
  - 중복된 코드를 최대한 제외하여 기능이 필요할 때만 호출하여 쓰기 때문에 재사용성이 높다.
  - 애플리케이션 전체에 흩어진 공통 기능이 하나의 장소에서 관리되어 보다 유지보수가 수월하다.
  - 핵심 로직과 부가 기능의 명확한 분리로, 개발자는 핵심 로직에 집중할 수 있게 된다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/17),
[baekgom.log](https://velog.io/@baekgom/Spring-AOP)
<br><br><br>



## 스프링 AOP와 Proxy
- 스프링 AOP와 Proxy
  - 스프링에서는 프록시를 이용해 AOP를 지원한다.
  - 스프링 AOP에서 사용하는 프록시 방식에는 JDK Proxy(=JDK Dynamic Proxy)와 CGLib Proxy가 있다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/3e9696e2-29c2-4b92-a8b3-260b924ad2cb)
  - JDK Dynamic Proxy
    - Interface를 기반으로 Proxy를 생성해주는 방식이다.
    - Reflection을 이용해 Proxy를 생성한다.
  - CGLib Proxy
    - Code Generator Libray의 약자로, JDK Dynamic Proxy와는 다르게 인터페이스가 아닌 클래스 기반으로 바이트코드를 조작하여 프록시를 생성하는 방식이다.
    - Reflection이 아닌 바이트 조작을 사용하며, 타겟에 대한 정보를 알고 있기 때문에 JDK Dynamic Proxy에 비해 성능이 좋다.
- 스프링과 스프링부트에서의 채택
  - 스프링 AOP에서는 기본적으로 JDK Dynamic Proxy를 사용한다. 하지만 JDK Dynamic Proxy는 인터페이스가 있어야만 사용할 수 있기 때문에 인터페이스가 없는 경우에는 CGLIB Proxy를 사용한다.
  - 스프링 부트에서는 설정을 통해 프록시 방식을 선택할 수 있다.
  - JDK 방식은 AOP 적용을 위해 반드시 인터페이스를 구현해야 된다는 점, 리플렉션은 Private에 접근이 가능하다는 점 때문에 스프링 부트 2.0에서는 기본 방식으로 CGLib 방식을 채택하였다.
- Ref.
[펲로그](https://suyeonchoi.tistory.com/81),
[제이온](https://steady-coding.tistory.com/608)
<br><br><br>



## 스프링 PSA
- PSA(Portable Service Abstraction)란?
  - 일관성 있는 서비스 추상화를 뜻한다.
  - 추상화를 통해 하위 시스템을 알지 못하거나 변경이 있더라도 일관된 방식으로 접근할 수 있게 한다.
  - 스프링에서의 대표적 PSA 예로는 트랜잭션이 있다.
- 스프링의 트랜잭션 추상화 계층
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/2b9889f3-3921-44b7-9243-1ae3763c576e)
  - 스프링에서는 위의 그림과 같이 'JDBC/Connection', 'JTA/UserTransaction', 'Hibernate/Transaction' 등 다양한 트랜잭션 기능을 제공하고 있다.   
  - 개발자는 DB와 관련된 기능 개발 시, DB접근 기술에 따라 알맞은 트랜잭션 기술을 선택해야한다.   
    만약 DB접근 기술이 바뀐다면 변경된 기술에 맞는 트랜잭션으로 변경이 필요하다.   
    하지만 PSA가 접목되어 있다면 DB접근 기술과 관계없이 일관된 방식으로 트랜잭션을 제어할 수 있다.
  - Ex) @Transactional은 각 각의 TransactionManager를 구현하고 있는 것이 아니라 최상위 PlatformTransactionManager를 사용하여 필요한 TransactionManager를 DI로 주입받아 사용한다. 이 때문에 @Transactional을 사용하여 트랜잭션을 관리할 경우, DB접근 기술이 JDBC에서 JPA로 변경되어도 트랜잭션에 대한 수정없이 트랜잭션 처리를 보장 받을 수 있는 것이다.
- Ref.
[사바라다는 차곡차곡](https://sabarada.tistory.com/127)
<br><br><br>



## 스프링 POJO
- POJO (Plain Old Java Object)란?
  - '오래된 방식의 간단한 자바 객체' = '단순한 자바 오브젝트' 라는 뜻이다.
  - 객체 지향적인 원리에 충실하면서 환경과 기술에 종속되지 않고 필요에 따라 재활용될 수 있는 방식으로 설계된 객체를 말한다.
- POJO의 조건
  - 특정 규약에 종속되면 안된다.
  - 특정 환경에 종속되면 안된다.
  - 객체 지향적 원리를 지켜야 한다.
- Ref.
[미노드로그](https://onpups.pe.kr/386)
<br><br><br>



## 빈 스코프(Bean Scope)
- 빈 스코프(Bean Scope) 란?
  - 스프링이 관리하는 빈이 생성되고, 존재하고, 적용되는 범위를 뜻한다.
- 종류
  - `* 웹 스코프 : 웹 스코프는 웹 환경에서만 동작한다.`
  - Singleton
    - 기본 스코프, 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프
  - Prototype
    - 스프링 컨테이너는 프로토타입 빈의 생성과 의존관계 주입까지만 관여하고 더는 관리하지 않는 매우 짧은 범위의 스코프
    - Prototype 스코프는 Singleton 스코프와 달리 컨테이너에서 빈을 받아올 때마다 매번 인스턴스를 새로 생성한다.
  - Request (* 웹 스코프)
    - HTTP 요청 하나가 들어오고 나갈 때까지 유지되는 스코프
    - 각각의 HTTP 요청마다 별도의 빈 인스턴스가 생성되고 관리된다.
  - Session (* 웹 스코프)
    - HTTP Session과 동일한 생명주기를 가지는 스코프
  - Application (* 웹 스코프)
    - 서블릿 컨텍스트(ServletContext)와 동일한 생명주기를 가지는 스코프
  - Websocket (* 웹 스코프)
    - 웹 소켓과 동일한 생명주기를 가지는 스코프   
- Ref.
[코드 연구소](https://code-lab1.tistory.com/186)
<br><br><br>



## @Transactional
- 트랜잭션이란?
  - 트랜잭션은 데이터베이스의 상태를 변환시키는 하나의 논리적 기능을 수행하기 위한 작업의 단위 또는 한꺼번에 수행되어야 할 일련의 연산을 의미한다.
- 트랜잭션 특징(ACID)
  - 원자성 (Atomicity)
    - 트랜잭션의 연산은 데이터베이스에 모두 반영되던지 아니면 모두 반영되지 않아야 한다.
    - 트랜잭션 내의 모든 명령은 반드시 완벽히 수행되어야 하며, 하나라도 오류가 발생하면 트랜잭션 전부가 취소되어야 한다. 
  - 일관성 (Consistency)
    - 트랜잭션 처리 전과 처리 후 데이터 모순이 없는 상태를 유지하는 것을 의미한다.
    - 예를 들어서 티스토리 게시판에 글을 쓰는데 제목의 글자 제한이 255 자라고 하자. 트랜잭션이 일어나면 이러한 조건을 만족해야 하는 것이다. 만약 이를 위반하는 트랜잭션이 있다면 거부해야 한다.
  - 독립성 (Isolation)
    - 둘 이상의 트랜잭션이 동시에 실행되는 경우 다른 트랜잭션의 연산이 끼어들 수 없다.
    - 수행 중인 트랜잭션은 완전히 완료될 때까지 다른 트랜잭션에서 수행 결과를 참조할 수 없다.
  - 지속성 (Durability)
    - 성공적으로 완료된 트랜잭션의 결과는 영구적으로 반영되어야 한다.
- @Transactional
  - @Transactional 어노테이션은 스프링에서 많이 사용되는 선언적 트랜잭션 방식이다.
  - 클래스 또는 메서드 위에 @Transactional을 붙이면 트랜잭션 기능이 적용된 프록시 객체가 생성되며, 트랜잭션 성공 여부에 따라 Commit 또는 Rollback 작업이 이루어진다.\
  - @Transactional에는 Spring AOP의 Proxy방식이 사용된다.
- 격리 수준 (Isolation Level)
  - DEFAULT
    - 데이터베이스에서 설정된 기본 격리 수준을 따른다. 
  - READ_UNCOMMITED
    - 트랜잭션이 아직 커밋되지 않은 데이터를 읽을 수 있다.
    - 세 가지 동시성 부작용(Dirty read, Nonrepeatable read, Phantom read)이 모두 발생한다.
  - READ_COMMITED
    - Dirty Read를 방지하기 위해 Commit 된 데이터만 읽을 수 있다.
    - 나머지 부작용(Nonrepeatable read, Phantom read)은 여전히 발생할 수 있다.
  - REPEATABLE READ
    - 트랜잭션이 완료될 때까지 조회한 모든 데이터에 shared lock이 걸리므로 트랜잭션이 종료될 때까지 다른 트랜잭션은 그 영역에 해당하는 데이터를 수정할 수 없다.
    - Phantom read 부작용은 여전히 발생한다.
  - SERIALIZABLE
    - 가장 엄격한 트랜잭션 격리 수준으로, 완벽한 읽기 일관성 모드를 제공한다.
    - 이 격리 수준에서는 PHANTOM READ 상태가 발생하지 않지만 동시성 처리 성능이 급격히 떨어질 수 있다.
- 전파 옵션 (Propagation)
  - REQUIRED
    - 이미 시작된 트랜잭션이 있으면 참여하고, 없으면 새로운 트랜잭션을 시작한다.
  - SUPPORTS
    - 이미 시작된 트랜잭션이 있으면 참여하고, 없으면 트랜잭션 없이 처리한다.
  - MANDATORY
    - 이미 시작된 트랜잭션이 있으면 참여하고, 없으면 예외를 발생시킨다.
    - 독립적으로 트랜잭션을 진행하면 안 되는 경우 사용한다.
  - NEVER
    - 트랜잭션을 사용하지 않도록 강제한다.
    - 이미 진행 중인 트랜잭션 또한 허용하지 않으며, 있다면 예외를 발생시킨다.
  - NOT_SUPPORTED
    - 트랜잭션을 사용하지 않고 처리하도록 합니다. 이미 진행 중인 트랜잭션이 있다면 잠시 보류시킨 후 트랜잭션 없이 진행한다.
  - REQUIRES_NEW
    - 항상 새로운 트랜잭션을 시작한다.
    - 이미 진행 중인 트랜잭션이 있다면 잠시 보류시킨다.
  - NESTED
    - 이미 실행 중인 트랜잭션이 있다면 중첩하여 트랜잭션을 진행한다.
    - 부모 트랜잭션은 중첩 트랜잭션에 영향을 주지만 중첩 트랜잭션은 부모 트랜잭션에 영향을 주지 않는다.
- rollbackFor, noRollbackFor
  - rollbackFor
    - 특정 예외가 발생하면 강제로 Rollback 한다.
  - noRollbackFor
    - 특정 예외가 발생하더라도 Rollback 하지 않는다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/139)
<br><br><br>



## Spring Filter vs Interceptor
- Filter vs Interceptor
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/d84d0e77-2367-4f49-ae76-4c102288cd41)
  - Filter
    - 관리 컨테이너 : 웹 컨테이너
    - DispatcherServlet 이전에 실행된다.
    - 일반적으로 인코딩 변환 처리, XSS방어 등에 대한 처리로 사용된다.
  - Interceptor
    - 관리 컨테이너 : 스프링 컨테이너
    - Dispatcher servlet에서 Handler(Controller)로 가기 전에 정보를 처리한다.
    - 로그인 체크, 권한 체크, 프로그램 실행시간 계산, 로그 확인 등에 대한 처리로 사용된다.
- Ref.
[망나니개발자](https://mangkyu.tistory.com/173)
<br><br><br>



## ORM, JPA, Hibernate, Spring Data JPA 개념
- ORM이란?
  - ORM이란 Object-Relational Mapping의 약자로, 객체(Object)와 관계형 데이터(Relational data)를 매핑하기 위한 기술이다.
- ORM과 SQL Mapper의 차이점
  - ORM
    - Object와 DB테이블을 매핑하여 데이터를 객체화하는 기술이다.
    - SQL 문을 직접 작성하지 않아도 메서드로 데이터를 조작할 수 있다. (객체 간 관계를 바탕으로 SQL문을 자동으로 생성한다.)
    - DBMS에 종속적이지 않다.
    - 관련기술 : JPA, Hibernate
  - SQL Mapper
    - Object와 SQL의 필드를 매핑하여 데이터를 객체화하는 기술이다.
    - SQL 문으로 직접 디비를 조작한다.
    - DBMS에 종속적이다.
    - 관련기술 : Mybatis, jdbcTemplate
- JPA란?
  - JPA는 Java Persistence API의 약자로, 자바 애플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스이다.
  - 여기서 중요하게 여겨야 할 부분은 JPA는 특정 기능을 가지고 있는 라이브러리가 아니고 말 그대로 인터페이스라는 점이다.
  - 따라서 JPA를 사용하기 위해서는 JPA를 구현한 Hibernate, EclipseLink, DataNucleus와 같은 ORM 프레임워크를 사용해야 한다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/27a0e8c2-59de-42fc-bda0-d76fa1957350)
- Hibernate란?
  - JPA 구현체의 한 종류이다. 
  - JPA와 Hibernate는 마치 자바의 interface와 해당 interface를 구현한 class와 같은 관계이다.
- Spring Data JPA란?
  - Spring Data JPA는 Spring Framework에서 제공하는 모듈 중 하나로, 개발자가 JPA를 더 쉽고 편하게 사용할 수 있도록 도와주는 기술이다.
- JPA, Hibernate, Spring Data JPA 관계
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/86508652-90c4-4618-9353-0fe473fcc54b)
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/140)
<br><br><br>



## 단위테스트와 통합테스트
- 테스트의 개념
  - 테스트란?
    - 테스트란 개발자가 작성한 코드가 의도대로 정확히 동작하는지를 검증하는 절차이다.
  - 작성해야하는 이유
    - 개발 과정 중 예상치 못한 문제를 미리 발견할 수 있다.
    - 작성한 코드가 의도한 대로 작동하는지 검증할 수 있다.
    - 코드 수정이 필요한 상황에서 유연하고 안정적인 대응할 할 수 있게 해준다.
    - 리팩토링 시 기능 구현이 동일하게 되었다는 판단을 내릴 수 있다.
    - 문서로서의 역할이 가능하다.
- 테스트의 종류
  - Unit Test(단위 테스트)
    - 하나의 모듈을 기준으로 독립적으로 진행되는 가장 작은 단위의 테스트이다.
    - 단위 테스트는 애플리케이션을 구성하는 하나의 기능, 하나의 함수가 올바르게 동작하는지를 독립적으로 테스트하는 것으로, 각각의 조건에 대한 유효성을 검증한다.
  - Integration Test(통합 테스트)
    - 모듈을 통합하는 과정에서 서로 다른 모듈 혹은 클래스 간 상호작용의 유효성을 검증하는 테스트이다.
    - 단위 테스트보다 더 넓은 범위의 종속성까지 테스트함으로써 단위 테스트보다 좀 더 유의미한 테스트가 되는 경우도 많다.
- 테스트별 장·단점
  - Unit Test(단위 테스트)
    - 장점 1. WebApplication 관련된 Bean들만 등록하기 때문에 통합 테스트보다 빠르다.
    - 장점 2. 통합 테스트가 어려운 테스트를 진행할 수 있다.
    - 단점 1. 요청부터 응답까지 모든 테스트를 Mock 기반으로 테스트하기 때문에 실제 환경에서는 제대로 동작하지 않을 수 있다.
  - Integration Test(통합 테스트)
    - 장점 1. 스프링 부트 컨테이너를 띄워 테스트하기 때문에 운영환경과 가장 유사한 테스트가 가능하다.
    - 장점 2. 전체적인 Flow를 쉽게 테스트할 수 있다.
    - 단점 1. 애플리케이션의 설정, 모든 Bean을 로드하기 때문에 시간이 오래 걸리고 무겁다.
    - 단점 2. 테스트 단위가 커 디버깅이 어렵다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/141)
<br><br><br>



## 단위테스트
- F.I.R.S.T 원칙
  - F.I.R.S.T 원칙이란 좋은 단위 테스트를 하기 위한 5가지 요소를 뜻한다.
    - Fast
      - 빠르게 실행되고 빠르게 결과를 알아야 한다. 이를 위해서는 하는 일의 단위가 최대한 작아야 한다.
      - 빠른 테스트를 위해 실제 서버나 데이터베이스를 이용하지 않고 가짜 데이터(모의 데이터)를 만들어서 테스트를 진행해야 한다.
    - Independent
      - 독립적이어야 하고 다른 테스트에 의존하거나 영향을 주어선 안된다.
    - Repeatable
      - 유닛 테스트는 반복 가능해야 하며, 몇 번을 진행하든 똑같은 결과가 나와야 한다.
    - Self-Validating
      - 자체 검증 가능해야 한다.
      - 테스트 자체로 통과인지 실패인지 결과가 나와야 하며 이것은 자동적으로 이뤄져야 한다.
    - Thorough / Timely
      - 유닛 테스트는 철저하고 적절한 때에 작성되어야 한다.
      - 철저하다는 것은 모든 데이터를 검사해야 하므로 최소에서 최대까지 범위를 포함하고, 역할(사용자일 때 혹은 관리자일 때)에 따라서 바뀌는 데이터를 모두 테스트가 가능해야하며 어떤 케이스가 실패(예외나 오류)하는지도 테스트해야 한다.
- 단위테스트와 JUnit
  - JUnit
    - 자바에는 JUnit이라는 단위 테스트를 위한 테스팅 프레임워크가 존재한다.
    - JUnit을 활용하여 단위테스트를 진행한다면, 테스트 결과를 문서로 남기는 것이 아니라 Test Class 자체를 남기기 때문에 코드에 대한 History를 남길 수 있다는 장점이 있다.
- JUnit 주요 단언(Assertion) 메서드
  - assertEquals(expected, actual) / assertNotEquals(unexpected, actual)
    - 실제 값(actual)이 기대하는 값(expected)과 같은지 / 같지 않은지 검사한다.
  - assertSame(Object expected, Object actual) / assertNotSame(Object unexpected, Object actual)
    - 두 객체가 동일한 / 동일하지 않은 객체인지 검사한다.
  - assertTrue(boolean condition) / assertFalse(boolean condition)
    - 값이 true / false인지 검사한다.
  - assertNull(Object actual) / assertNotNull(Object actual)
    - 값이 null인지 / null이 아닌지 검사한다.
  - assertThrows(Class<T> expectedType, Executable executable)
    - executable을 실행한 결과로 지정한 타입의 익셉션이 발생하는지 검사한다.
- JUnit 주요 어노테이션
  - @Test
    - 해당 메서드를 테스트 대상으로 지정한다.
  - @BeforeAll
    - 모든 테스트 시작 전에 수행되는 로직에 붙는 어노테이션으로 static을 붙여줘야 하며 접근 제어자는 default 이상이어야 한다.
  - @AfterAll
    - 모든 테스트 종료 후에 수행되는 로직에 붙는 어노테이션으로 static을 붙여줘야 하며 접근 제어자는 default 이상이어야 한다.
  - @BeforeEach
    - 모든 @Test 어노테이션이 붙은 테스트 대상 메서드 수행 전마다 수행된다.
  - @AfterEach
    - 모든 @Test 어노테이션이 붙은 테스트 대상 메서드 수행 종료시마다 수행된다.
- Mockito
  - Mock이란 실제 객체를 만들어 사용하기에 시간, 비용 등의 Cost가 높거나 혹은 객체 서로 간의 의존성이 강해 구현하기 힘들 경우 가짜 객체를 만들어 사용하는 방법이다.
  - 이러한 가짜(Mock) 객체를 만들 수 있도록 지원하는 프레임워크 중 Mockito라는 테스트 프레임워크가 있다.
- Mockito 주요 어노테이션
  - @ExtendWith
  - @Mock
  - @Spy
  - @InjectMocks
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/142),
[Caffeine Overflow](https://caffeineoverflow.tistory.com/143)
<br><br><br>



## 테스트 커버리지
- Title
  - Contents
- Ref.
[GwanMtCat](https://velog.io/@xeropise1/%ED%85%8C%EC%8A%A4%ED%8A%B8-%EC%BB%A4%EB%B2%84%EB%A6%AC%EC%A7%80%EB%9E%80)
<br><br><br>



## Private 메소드 테스트
- Private 메소드를 테스트하는 방법
  - Java Reflection API 이용
    - 리플렉션을 이용하면 정적으로 고정된 메소드의 코드를 메타정보로 추상화된 Method를 얻어낼 수 있으며 직접 호출 또한 가능하다.
    - 테스트하고자 하는 클래스로부터 Method를 추출하여 해당 메소드를 직접 invoke해주면 된다.
  - ReflectionTestUtils 이용
    - Spring에 내장되어있는 ReflectionTestUtils를 사용해서 간단히 테스트를 할 수 있다.
- Private 메소드 테스트를 지양해야 하는 이유
  - Private 메소드는 내부를 감추어 클라이언트와의 결합도를 낮춰주는데, 클라이언트인 테스트 클래스가 내부 메소드를 알고 있으니 결합도가 높아진다.
  - 이는 유지보수할 때 테스트에 대한 비용을 증가시키는 요인이 될 수 있는데, 메소드 이름이나 파라미터 등을 변경할 때 실패하게 된다.
  - Private 메소드를 테스트해야 하는 상황이라면 무언가 책임이 이상하거나 설계가 잘못되었다는 신호로 받아들이고 점검을 해볼 필요가 있다. 이는 리팩토링의 신호이다.
- Ref.
[망나니개발자](https://mangkyu.tistory.com/235)
<br><br><br>



## 어노테이션(Annotation)
- 어노테이션(Annotation)이란?
  - Annotation(@)은 사전적 의미로는 주석이라는 뜻이다.
  - 자바에서 Annotation은 코드 사이에 주석처럼 쓰이며 특별한 의미, 기능을 수행하도록 하는 기술이다.
  - 프로그램에게 추가적인 정보를 제공해 주는 메타데이터라고 볼 수 있다.
- 스프링의 주요 어노테이션
  - @ComponentScan
    - 빈으로 등록될 준비를 마친 클래스들을 스캔하여, 빈으로 등록해 주는 어노테이션이다.
    - @Component, @Service, @Repository, @Controller, @Configuration가 그 대상이 된다.
  - @Component
    - 개발자가 생성한 Class를 Spring의 Bean으로 등록할 때 사용하는 어노테이션이다.
  - @Bean
    - 개발자가 직접 제어가 불가능한 외부 라이브러리 등을 Bean으로 만들려 할 때 사용하는 어노테이션이다.
  - @Configuration
    - 설정 클래스임을 명시하거나 Bean을 등록하고자 할 때 사용하는 어노테이션이다.
    - @Configuration을 클래스에 적용하고 @Bean을 해당 Class의 method에 적용하면 @Autowired로 Bean을 부를 수 있다.
  - @Autowired
    - 속성(field), setter method, constructor(생성자)에서 사용하며 Type에 따라 알아서 Bean을 주입해 준다.
  - @Controller
    - Presentation Layer의 MVC Controller에 사용한다.
    - 스프링 웹 서블릿에 의해 웹 요청을 처리하는 컨트롤러 빈으로 선정한다.
  - @RestController
    - @Controller와 유사하나 컨트롤러가 Rest 방식을 처리하기 위한 것임을 명시한다.
    - View로 응답하는 것이 아니라 반환 결과를 JSON 형태로 반환한다.
  - @Service
    - Service Class에서 쓰인다.
    - 비즈니스 로직을 수행하는 Class라는 것을 나타내는 용도이다.
  - @Repository
    - DAO 또는 Repository 클래스에 사용한다.
    - DataAccessException 자동변환과 같은 AOP 적용대상을 선정하기 위해 사용한다.
  - @Value
    - properties와 같은 설정파일에서 값을 가져와 적용할 때 사용한다.
  - @Valid
    - 유효성 검증이 필요한 객체임을 지정한다.
  - @RequestBody
    - 요청 데이터(JSON이나 XML형식)를 바로 Class나 model로 매핑하기 위한 Annotation이다.
  - @ResponseBody
    - HttpMessageConverter를 이용하여 JSON 혹은 xml로 요청에 응답할 수 있게 해주는 Annotation이다.
    - view가 아닌 JSON 형식의 값을 응답할 때 사용하는 Annotation으로, 문자열을 리턴하면 그 값을 http response header가 아닌 response body에 들어간다.
  - @Transactional
    - 데이터베이스 트랜잭션을 설정하고 싶은 method에 Annotation을 적용하면 method 내부에서 일어나는 데이터베이스 로직이 전부 성공하게 되거나 데이터베이스 접근 중 하나라도 실패하면 다시 롤백할 수 있게 해주는 Annotation이다.
  - @Cacheable
    - method 앞에 지정하면 해당 method를 최초에 호출하면 캐시에 적재하고 다음부터는 동일한 method 호출이 있을 때 캐시에서 결과를 가져와서 return 하므로 method 호출 횟수를 줄여주는 Annotation이다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/145)
<br><br><br>



## @Value VS @ConfigurationProperties
- 용도
  - 스프링의 properties나 yaml에 있는 값들을 사용하기 위한 어노테이션이다.
- @Value
  - 단일 값 주입만 할 수 있다.
  - RelaxedBinding이 불가능하다.
  - spEL 적용이 가능하다.
- @ConfigurationProperties
  - 복수의 값을 바인딩할 수 있다.
  - RelaxedBinding이 가능하다.
  - spEL 적용이 불가능하다.
- RelaxedBinding과 spEL
  - RelaxedBinding
    - 프로퍼티 값의 이름이 조금 달라도 유연하게 바인딩을 시켜주는 규칙을 의미한다.
    - Environment 프로퍼티 값과 Bean 프로퍼티 이름을 정확히 일치할 필요가 없다.
    - 프로퍼티와 환경 변수들의 구분을 어느정도 유연한 규칙으로 동일하게 인식하기 때문이다.
    - 프로퍼티의 값이 root.path=/dev 와 같이 정의되어 있다고 가정할 때, Bean 프로퍼티 이름이 String rootPath여도 유연한 규칙을 통해 동일하게 인식해서 값을 매핑시켜준다.
  - spEL
    - Spring Expression Language는 SpEL로 많이 표기한다.
    - SpEL 표현식은 # 기호로 시작하며 중괄호로 묶어서 표현한다. : #{표현식}
    - Ex)
      ``` java
      @Value("#{1 == 1}") // true
      private boolean boolTmp;

      @Value("#{some.property != null ? some.perperty : 'test'}") // null인 경우 test 주입
      private String strTmp;
      ``` 
- Ref.
[dhkim's development blog](https://velog.io/@dhkim1522/SpringBoot-%EC%99%B8%EB%B6%80-%ED%94%84%EB%A1%9C%ED%8D%BC%ED%8B%B0-%EC%A0%81%EC%9A%A9-Value-ConfigurationProperties),
[호준송](https://hojunking.tistory.com/125)
<br><br><br>



## 주요 HTTP 메서드(GET, POST, PUT, PATCH, DELETE)
- GET
  - GET 메서드는 리소스의 조회를 위해 사용한다.
  - 서버에 전달하고 싶은 데이터가 있다면 query(쿼리 파라미터, 쿼리 스트링)에 담아 보낸다.
- POST
  - POST 메서드는 요청 데이터의 처리를 목적으로 사용한다.
  - 메시지 바디를 통해 서버로 요청 데이터를 전달하면, 서버는 정해진 로직에 따라 요청 데이터를 처리한다.
  - 주로, 전달된 데이터를 이용하여 신규 리소스를 등록하거나 프로세스를 처리한다.
- PUT
  - PUT 메서드는 리소스 전체를 대체한다. 즉, 덮어쓰기를 수행한다고 볼 수 있다.
  - 기존 리소스가 없을 경우 새로 생성한다.
  - POST와 차이점은 클라이언트가 리소스의 위치를 알고 URI를 명시해야 한다는 점이다.
- PATCH
  - PATCH 메서드는 리소스를 부분 변경한다.
  - 부분 변경이 필요한 상황에서 PATCH를 사용할 수 없다면 POST를 사용한다.
- DELETE
  - DELETE 메서드는 리소스를 제거한다.
- Ref.
[woply](https://velog.io/@woply/HTTP-%EC%A3%BC%EC%9A%94-%EB%A9%94%EC%84%9C%EB%93%9C-5%EA%B0%80%EC%A7%80-%EC%A0%95%EB%A6%ACGET-POST-PUT-PATCH-DELETE)
<br><br><br>



## REST(Representational State Transfer)와 RESTful
- REST(Representational State Transfer)란?
  - 자원을 이름(자원의 표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미한다.
  - HTTP URI를 통해 자원을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD 수행한다.
- REST의 구성 요소
  - 자원(Resource) : HTTP URI
  - 자원에 대한 행위(Verb) : HTTP Method
  - 자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load
- RESTful이란?
  - REST의 원리를 따르는 시스템을 의미한다.
- RESTful의 제약조건
  - 클라이언트-서버(Client-Server)
    - 관심사의 명확한 분리가 선행되면 서버의 구성요소가 단순화되고, 확장성이 향상되어 여러 플랫폼을 지원할 수 있다.
  - 무상태성(Stateless)
    - 서버에 클라이언트의 상태 정보를 저장하지 않는 것을 말한다.
    - 단순히 들어오는 요청만 처리하여 구현을 더 단순화시킨다.
  - 캐시 가능(Cacheable)
    - 클라이언트의 요청에 대한 응답을 캐시할 수 있어야 한다.
  - 계층화 시스템(Layered System)
    - 서버는 중개서버나 로드 밸런싱, 공유 캐시 등의 기능을 사용하여 확장성 있는 시스템을 구성할 수 있다.
  - 코드 온 디맨드(Code on demand)
    - 클라이언트 서버에서 자바 애플릿, 자바스크립트 실행 코드를 전송받아 기능을 일시적으로 확장할 수 있다.
  - 인터페이스 일관성(Uniform interface)
    - URI로 지정된 리소스에 균일하고 통일된 인터페이스를 제공한다.
    - 아키텍처를 단순하게 분리하여 독립적으로 만들 수 있다.
- Ref.
[soom](https://velog.io/@soom/REST-Representational-State-Transfer),
[슬기로운 개발생활](https://dev-coco.tistory.com/m/97?category=1009704)
<br><br><br>



## Hateoas(Hypermedia As The Engine Of Application State)
- Hateoas란?
  - 클라이언트의 요청으로부터 응답을 할 때, 요청 이외의 관련된 URI를 응답에 추가적으로 포함시켜 반환하는 개념이다.
  - 예를 들어, 클라이언트가 사용자를 조회했을 때 사용자 정보만 응답하는 것이 아니라 '사용자 수정', '사용자 삭제' 등을 처리할 수 있는 링크를 같이 포함하여 응답하는 것을 예시로 들 수 있다.
- 장점
  - 요청 URI가 변경되더라도 클라이언트는 이에 대응하여 코드를 변경하지 않아도 된다.
  - Resource가 포함된 URI를 보여주기 때문에, Resource에 대한 신뢰도를 높일 수 있다.
- 단점
  - 전달되는 data의 크기가 커져서 네트워크 오버헤드가 생길 수 있다.
  - 링크가 복잡해질 수 있다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/28)
<br><br><br>



## CORS
- CORS란?
  - 교차 출처 리소스 공유(Cross-origin Resource Sharing)는 추가 HTTP헤더를 사용하여, 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제이다.
- 출처(Origin)란?
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/ab8e57b2-8ff9-454c-9f3e-d62489c8fe3a)
  - 출처(Origin)란 위의 URL 구조에서 Protocol, Host, Port를 합친 것을 의미한다.
  - 즉, 다른 출처란 Protocol, Host, Port 중 한 개라도 다른 것을 의미한다.
- 동일 출처 정책(Same-Origin Policy)이란?
  - CORS policy 오류가 발생하는 이유는 브라우저가 동일 출처 정책(Same-Origin Policy, SOP)을 지켜서 다른 출처의 리소스 접근을 금지하기 때문이다.
- Ref.
[Beomy](https://beomy.github.io/tech/browser/cors/)
<br><br><br>



## CI/CD
- CI/CD란?
  - CI/CD란 지속적 통합과 지속적 배포가 통합된 방식을 일컫는다.
- CI(Continuous Integration)
  - 어플리케이션에 대한 새로운 코드 변경사항이 주기적으로 빌드 및 테스트되어 공통 저장소에 통합되는 개념이다.
  - 다수의 개발자가 형상관리 툴을 공유하는 경우라면, 자동화된 빌드 및 테스트는 원천 소스코드의 충돌을 방어할 수 있는 장점을 가지고 있다.
- CD(Continuous Delivery 또는 Continuous Deployment)
  - 배포 자동화 과정을 뜻한다.
  - CI가 새로운 소스코드의 빌드, 테스트, 병합을 의미한다면 CD는 개발자의 변경 사항을 넘어 고객의 환경까지 릴리즈 되는 것을 의미한다.
- Ref.
[jung_ho9 개발일지](https://velog.io/@leejungho9/CICD-%EB%9E%80)
<br><br><br>



## 배포 전략
- 인플레이스 배포 (In-place Deployment)
  - 현재 운영중인 인프라에서 변경 사항이 있는 애플리케이션을 그대로 변경하는 방식.
- 롤링 배포(Rolling Update Deployment)
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/3b325f99-d29a-4452-bb3f-cfe768c6a582)
  - 롤링 배포는 사용 중인 인스턴스 내에서 새 버전을 점진적으로 교체하는 방식.
  - 무중단 배포의 가장 기본적인 방식.
  - 운영중인 인스턴스를 순차적으로 재배포 함으로 서비스 운영간 중단없이 기능을 제공할 수 있다.
  - 배포 중간 단계에서 기존 버전/신규 버전이 함께 운영되어 일부 상황에서는 문제가 발생할 수 있다.
- 블루/그린 배포(Blue/Green Deployment)
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/40b3f8cd-b71d-4aa0-b352-9324bedce135)
  - 블루/그린 배포는 동일한 구성의 새로운 인프라를 활용해 변경 사항이 있는 애플리케이션을 실행하는 방식.
  - 로드밸런서의 트래픽을 그린 인프라로 옮겨 변경사항이 적용된 인프라로 트래픽을 한 번에 이동하는 방식.
  - 두 개의 인프라를 구축하여 사용해야 하기 때문에 서버 비용이 추가적으로 발생할 수 있다.
    - 블루 : 기존에 운영되던 인프라.
    - 그린 : 새로운 변경사항이 적용될 인프라.
- 카나리 배포(Canary Deployment)
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/a8ec55ce-a434-42ef-b61c-c73248a7c42f)
  - 카나리 배포는 단계적으로 전환하는 방식.
  - 카나리 배포의 핵심은 일부분에 새로운 버전을 배포한 후에 특정 사용자들에게만 새로운 버전으로 접근되도록 라우팅 하는 것이다.
  - 테스트 후 새로운 버전을 모두 반영한다.
  - 기존 버전/신규 버전이 함께 운영되어 일부 상황에서는 문제가 발생할 수 있다.
- Ref.
[Gelog](https://velog.io/@gehwan96/CICD-%EB%B0%B0%ED%8F%AC-%EC%A0%84%EB%9E%B5-%EC%A0%95%EB%A6%AC),
[뽀뽀이 부부의 IT 이야기](https://jihuni1026.tistory.com/5)
<br><br><br>



## PRG(POST-Redirect-GET) 패턴
- PRG 패턴이란?
  - 웹 디자인 패턴 중 하나로 POST요청에 대한 응답으로 리다이렉트를 통해 GET요청을 할 수 있도록 처리하는 패턴이다.
- 상세 순서
  - 클라이언트는 HTTP POST 요청을 한다.
  - 서버는 클라이언트에게 'URL'과 'GET요청으로 Redirect 할 수 있는 응답코드(302)'를 응답한다.
  - Redirection을 통해 서버에게 응답받은 URL로 GET 요청을 한다.
- 적용하지 않았을 시 문제점
  - 데이터를 POST요청으로 보낸 후 클라이언트가 새로고침을 할 경우, 중복 요청이 발생하여 예기치않은 문제점이 발생할 수 있다.
- Ref.
[Gofo](https://gofo-coding.tistory.com/entry/PRG-%ED%8C%A8%ED%84%B4-Post-%E2%86%92-Redirect-%E2%86%92-Get)
<br><br><br>



## Maven과 Gradle
- 빌드와 빌드 관리 도구
  - Maven과 Gradle은 모두 빌드 관리 도구이다.
  - 빌드(Build)
    - 빌드는 소스코드 파일을 컴퓨터에서 실행할 수 있는 독립적인 형태로 변환하는 과정과 결과를 말한다.
    - 개발자가 작성한 소스코드(.java), 프로젝트에서 쓰인 각 각의 파일 및 자원(.xml, .jpa, .jpg, properties)을 jvm이나 톰캣 같은 WAS가 인식할 수 있도록 패키징하는 과정 및 결과물을 일컫는다.
  - 빌드 관리 도구(Build Tool)
    - 빌드 도구란, 소스코드에서 애플리케이션을 생성하면서 여러가지 외부 라이브러리를 사용하는데, 빌드 관리 도구를 사용하게 되면 사용자가 이를 관리하지 않아도 된다.
    - 필드 관리 도구는 다음과 같은 작업을 수행한다.
      1. 종속성 다운로드 - 전처리(Preprocessing)
      2. 소스코드를 바이너리 코드로 컴파일(Compile)
      3. 바이너리 코드를 패키징(Packaging)
      4. 테스트 실행(Testing)
      5. 프로덕션 시스템에 배포(distribution)
    - 빌드 툴로는 Ant, Maven, Gradle 등이 있다.
- Maven
  - Maven은 Java 전용 프로젝트 관리 도구로써 Lifecycle 관리 목적 빌드 도구이며, Apache Ant의 대안으로 만들어졌다.
  - 정해진 Lifecycle에 의하여 작업을 수행하며, 전반적인 프로젝트 관리 기능을 포함하고 있다.
  - clean - validate - compile - test - package - verify - install - site - deploy의 라이프 사이클을 가진다.
    - clean : 빌드 시 생성되어있었던 파일들을 삭제한다.
    - validate : 프로젝트가 올바른지 확인하고 필요한 모든 정보를 사용할 수 있는지 확인하는 단계
    - compile : 프로젝트 소스코드를 컴파일 하는 단계
    - test : 단위 테스트를 수행하는 단계. 테스트 실패 시 빌드 실패로 처리하며, 스킵이 가능하다.
    - package : 실제 컴파일된 소스 코드와 리소스들을 jar, war 등의 파일의 배포를 위한 패키지로 만든다.
    - verify : 통합 테스트 결과에 대한 검사를 실행하여 품질 기준을 충족하는지 확인한다.
    - site : 프로젝트 문서와 사이트 작성, 생성하는 단계
    - deploy : 만들어진 package를 원격 저장소에 release하는 단계
- Gradle
  - Maven을 대체할 수 있는 프로젝트 구성 관리 및 범용 빌드 툴이며, Ant Builder와 Groovy script를 기반으로 구축되어 기존 Ant의 역할과 배포 스크립의 기능을 모두 사용가능하며 스프링부트와 안드로이드에서 사용된다.
  - 빌드 속도가 Maven에 비해 10~100배 가량 빠르며, Java, C/C++, Python 등을 지원한다.
- Gradle의 장점
  - 가독성
    - 코딩에 의한 간결한 정의가 가능하므로 가독성이 좋다.
  - 재사용 용이
    - 설정 주입 방식(Configuration Injection)을 사용하므로 재사용에 용이하다.
  - 구조적인 장점
    - Build Script를 Groovy기반의 DSL(Domail Specific Language)을 사용하여 코드로서 설정 정보를 구성하므로 구조적인 장점이 있다.
  - 편리함
    - Gradle 설치 없이 Gradle wrapper를 이용하여 빌드를 지원한다.
  - 멀티 프로젝트
    - Gradle은 멀티 프로젝트 빌드를 지원하기 위해 설계된 빌드 관리 도구이다.
  - Maven 지원
    - Maven을 완전 지원한다.
  - 빌드와 테스트 실행 속도
    - 빌드와 테스트 실행 결과 Gradle이 더 빠르다
    - 캐시를 사용하므로 테스트 반복 시 실행 결과 시간의 차이가 더 커진다.
- Ref.
[smlee](https://velog.io/@leesomyoung/Maven%EA%B3%BC-Gradle%EC%9D%98-%EC%B0%A8%EC%9D%B4-%EB%B0%8F-%EB%B9%84%EA%B5%90)
<br><br><br>



## [JPA] 영속성 관리
- 영속성 컨텍스트란?
  - 영속성 컨텍스트는 엔티티를 영구 저장하는 환경이다.
  - 엔티티 매니저를 통해서 영속성 컨텍스트에 접근할 수 있고, 영속성 컨텍스트를 관리할 수 있다.
- 엔티티의 생명주기
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/5ecec14d-0b5e-4fbb-a780-c8581408ff6f)
  - 비영속(new/transient)
    - 영속성 컨텍스트와 전혀 관계가 없는 새로운 상태
  - 영속(managed)
    - 영속성 컨텍스트에 관리되는 상태
  - 준영속(detached)
    - 영속성 컨텍스트에 저장되었다가 분리된 상태
  - 삭제(remove)
    - 삭제된 상태
- 영속성 컨텍스트의 특징
  - 1차 캐시
    - 영속성 컨텍스트에 1차 캐시 존재
    - 캐시는 map 형태로 key-value 저장
  - 동일성 보장
    - 같은 트랜잭션 안에서 같은 객체는 == 비교를 보장한다.
  - 트랜잭션을 지원하는 쓰기 지연
    - 한 트랜잭션 안에서 DB에 보낼 쿼리문을 모았다가 한 번에 보냄으로써 네트워크 부하를 줄 일 수 있다.
  - 변경 감지
    - 영속성 컨텍스트에서 보관하는 데이터에 변경이 일어났는지 확인이 가능하다.
    - 만약 변경이 일어났다면 JPA가 UPDATE 쿼리문을 날려주기 때문에 값을 변경 후에 UPDATE 쿼리를 명시적으로 수행하지 않아도 된다.
  - 지연 로딩
    - 연관된 객체를 바로 조회하지 않고, 값이 사용되는 시점에 DB에서 가져온다.
- Ref.
[공부기록](https://velog.io/@suk13574/JPA-%EC%98%81%EC%86%8D%EC%84%B1-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8%EC%9D%98-%EC%A0%84%EB%B0%98%EC%A0%81%EC%9D%B8-%EC%9D%B4%ED%95%B4%EA%B0%9C%EB%85%90-%EC%9E%A5%EC%A0%90-%EB%8F%99%EC%9E%91-%EB%B0%A9)
<br><br><br>



## [JPA] N+1문제
- Title
  - Content
- Ref.
[말 랑](https://ttl-blog.tistory.com/1135),
[하얀종이개발자](https://jh2021.tistory.com/21)
<br><br><br>



## [JPA] 즉시 로딩과 지연 로딩
- Title
  - Content
- Ref.
[땡글이](https://velog.io/@ddangle/%EC%A6%89%EC%8B%9C-%EB%A1%9C%EB%94%A9%EA%B3%BC-%EC%A7%80%EC%97%B0-%EB%A1%9C%EB%94%A9-%EB%B9%84%EA%B5%90),
[dev john](https://study-easy-coding.tistory.com/137)
<br><br><br>



## [JPA] equals와 hashCode
- 복합키에서 equals() 및 hashCode()를 구현하는 이유
  - 영속성 컨테스트는 엔티티의 식별자를 키로 사용해서 엔티티를 관리한다.   
    그리고 식별자를 비교할 때 equals() 와 hashcode()를 사용한다.   
    따라서, 식별자 객체의 동등성(equals)이 지켜지지 않으면 예상과 다른 엔티티가 조회되거나 엔티티를 찾을 수 없는 등 영속성 컨텍스트가 엔티티를 관리하는 데 문제가 발생하므로, 복합 키는 equals()와 hashCode()를 필수로 구현해야 한다.
- Ref.
[modiday](https://modimodi.tistory.com/14),
[Medium](https://xeounxzxu.medium.com/jpa-about-equals-and-hashcode-9456224253d5)
<br><br><br>



## [JPA] 낙관적 락(Optimistic Lock)과 비관적 락(Pessimistic Lock)
- 낙관적 락(Optimistic Lock)과 비관적 락(Pessimistic Lock)
  - JPA를 사용하여 데이터베이스와 연결된 어플리케이션을 개발할 때, 동시성 처리와 관련된 이슈가 발생할 수 있다.
  - 이러한 이슈를 해결하기 위한 방법 중 하나는 락(lock)을 사용하는 것이고, 락에는 낙관적 락과 비관적 락이 있다.
- 낙관적 락(Optimistic Lock)
  - 낙관적 락은 충돌이 거의 발생하지 않을 것이라고 가정하고, 충돌이 발생한 경우에 대비하는 방식이다.
  - 낙관적 락은 JPA에서 버전(Version) 속성을 이용하여 구현할 수 있다.
  - 낙관적 락의 특징으로는 충돌 발생확률이 낮고, 지속적인 락으로 인한 성능저하를 막을 수 있다.
  - 장단점
    - 장점: 리소스 경쟁이 적고 락으로 인한 성능저하가 적다.
    - 단점: 충돌 발생 시 처리해야 할 외부 요인이 존재한다.
- 비관적 락(Pessimistic Lock)
  - 비관적 락은 충돌이 발생할 확률이 높다고 가정하여, 실제로 데이터에 액세스 하기 전에 먼저 락을 걸어 충돌을 예방하는 방식이다.
  - 비관적 락은 JPA에서 제공하는 LockModeType을 사용하여 구현할 수 있다.
  - 장단점
    - 장점: 충돌 발생을 미연에 방지하고 데이터의 일관성을 유지할 수 있다.
    - 단점: 동시 처리 성능 저하 및 교착상태(Deadlock) 발생 가능성이 있다.
- Ref.
[우당탕탕](https://mozzi-devlog.tistory.com/37)
<br><br><br>



## CQRS
- CQRS란?
  - Command Query Responsibility Segregation의 약자로 도메인 모델을 다음의 두 가지 모델로 분리하는 패턴이다.
    - 상태를 변경하는 명령(Command)을 위한 모델
    - 상태를 제공하는 조회(Query)를 위한 모델
  - 명령을 처리하는 책임과 조회를 처리하는 책임을 분리하는 것이 CQRS의 핵심이다.
- 장점
  - 도메인 로직에만 집중할 수 있게 된다.
    - Command와 Query를 분리했기 때문에 OCP 를 준수하는 도메인 모델을 만들 수 있다.
    - 이를 통해 결국 도메인 로직에 비즈니스 로직을 집중시킬 수 있다.
  - 데이터소스의 독립적인 크기 조정이 가능하다.
    - 보통 Read와 Write의 비율은 1000 : 1 이다.
    - 그러므로 Write DB가 물리적으로 나뉘어져 있다면, 해당 DB 인스턴스는 작게 유지하고 Read DB 인스턴스에 더 높은 투자를 할 수 있다.
  - 단순한 쿼리
    - Query side에서는 Materialized View를 이용할 수 있는데, 이를 통해서 복잡한 조인 쿼리 없이 단순한 쿼리를 이용해서 원하는 정보를 얻어 올 수 있다.
- 단점
  - 복잡성이 올라간다.
    - Command side와 Query side를 명시적으로 분리하기 때문에 복잡성이 올라간다.
  - 즉시적인 일관성이 보장되지 않는다.
    - Command에 따른 데이터의 무결성이 잠시동안 깨질 수 있다.
    - 이 말은 데이터의 일관성이 항상 보장되지 않을 수 있다. (하지만 최종적으로는 데이터가 맞춰질 것이니 Eventual Consistency라고 할 수 있다.)
- Ref.
[Wonit](https://wonit.tistory.com/628),
[JaeHoney](https://jaehoney.tistory.com/255)
<br><br><br>



## lombok
- @Data, @Setter, @AllArgsConstructor 지양
  - 내용
- @Tostring 순환 참조
  - 내용
- Ref.
<br><br><br>



## Spring WebFlux
- Title
  - Content
- Ref.
<br><br><br>



## 웹 브라우저에 URL 입력 시 일어나는 일련의 과정
1. 브라우저 주소창에 maps.google.com을 입력한다.
2. 브라우저가 maps.google.com의 IP 주소를 찾기 위해 캐시에서 DNS 기록을 확인한다.
    - DNS 기록을 찾기 위해서, 브라우저는 네 개의 캐시를 확인한다.
      1. DNS 쿼리는 우선 브라우저 캐시를 확인한다. 브라우저는 내가 이전에 방문한 웹 사이트의 DNS 기록을 일정 기간 동안 저장하고 있다.
      2. 브라우저는 OS 캐시를 확인한다. 브라우저 캐시에 원하는 DNS 레코드가 없다면, 브라우저가 내 컴퓨터 OS에 시스템 호출(ex. 윈도우에서 gethostname 호출)을 통해 DNS 기록을 가져온다.
      3. 브라우저는 라우터 캐시를 확인한다. 만약 컴퓨터에도 원하는 DNS 레코드가 없다면, 브라우저는 라우터에서 DNS 기록을 저장한 캐시를 확인한다.
      4. ISP 캐시를 확인한다. 만약 위 모든 단계에서 DNS 기록을 찾지 못한다면, 브라우저는 ISP에서 DNS 기록을 찾는다. ISP(Internet Service Provider)는 DNS 서버를 가지고 있는데, 해당 서버에서 DNS 기록 캐시를 검색할 수 있다.  
3. 만약 요청한 URL(maps.google.com)이 캐시에 없다면, ISP의 DNS 서버가 DNS 쿼리로 maps.google.com을 호스팅하는 서버의 IP 주소를 찾는다.
4. 브라우저가 해당 서버와 TCP 연결을 시작한다.
    - 브라우저가 올바른 IP 주소를 수신하면 IP 주소와 일치하는 서버와 연결해 정보를 전송한다.
    - 브라우저는 인터넷 프로토콜(IP, Internet Protocol)을 사용하여 이러한 연결을 구축한다.
    - 사용할 수 있는 여러가지의 인터넷 프로토콜이 있지만, 일반적으로 HTTP 요청에서는 TCP(Transmission Control Protocol)라는 전송 제어 프로토콜을 사용한다.
    - TCP 연결은 TCP/IP 3-way handshake라는 연결 과정을 통해 이뤄진다.
      1. 클라이언트는 인터넷을 통해 서버에 SYN 패킷을 보내 새 연결이 가능한지 여부를 묻는다.
      2. 서버에 새 연결을 수락할 수 있는 열린 포트가 있는 경우, SYN/ACK 패킷을 사용하여 SYN 패킷의 ACK(승인)으로 응답한다.
      3. 클라이언트는 서버로부터 SYN/ACK 패킷을 수신하고 ACK 패킷을 전송하여 승인한다.
5. 브라우저가 웹서버에 HTTP 요청을 보낸다.
6. 서버가 요청을 처리하고 응답(response)을 보낸다.
7. 서버가 HTTP 응답을 보낸다.
8. 브라우저가 HTML 컨텐츠를 보여준다.
- Ref.
[khy__.log](https://velog.io/@khy226/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%97%90-url%EC%9D%84-%EC%9E%85%EB%A0%A5%ED%95%98%EB%A9%B4-%EC%96%B4%EB%96%A4%EC%9D%BC%EC%9D%B4-%EB%B2%8C%EC%96%B4%EC%A7%88%EA%B9%8C)
<br><br><br>



## HTTPS 통신
- Title
  - Content
- Ref.
[Computing](https://computing-jhson.tistory.com/117)
<br><br><br>



## Connection Timeout과 Read Timeout
- Connection Timeout
  - Connection Timeout은 종단 간 연결하는데 소요되는 최대 시간을 의미한다.
    - 이 때의 연결이란 TCP 3-way-handshake를 통해 TCP 연결이 생성되는 것을 의미.
  - 이 시간을 넘기게 되면 연결 할 수 없는 것으로 판단하고 에러가 발생한다.
- Read Timeout
  - 연결된 종단 간에 데이터를 주고 받을 때 소요되는 최대 시간을 의미한다.
  - 이 시간을 넘기게 되면 데이터를 받을 수 없는 것으로 판단하고 에러가 발생한다.
- Ref.
  [Alden's Dev Log](https://alden-kang.tistory.com/20)
  <br><br><br>



## 인증(Authentication)과 인가(Authorization)
- 인증(Authentication)
  - 인증은 사용자 또는 디바이스 등의 신원 정보를 확인하는 과정이다.
  - 특정 서비스에 회원 가입을 하고, 로그인하는 과정이 인증에 해당한다.
  - Ex) 어떤 A라는 건물에 출입증이 있어야만 들어갈 수 있는데 신원을 확인하여 출입증을 받는 과정을 뜻한다.
- 인가(Authorization)
  - 인가는 사용자 또는 디바이스 등이 어떤 리소스에 접근할 수 있는지, 어떤 동작을 수행할 수 있는지 등을 검증하는 것이다.
  - Ex) 출입증을 받았더라도 건물 내 모든 장소에 갈 수는 없을 것이다. 특정 장소에 접근할 수 있는 권한이 있는 출입증임을 확인하는 과정을 인가라고 한다.
- Ref.
[JaeHoney](https://ittrue.tistory.com/246),
[Gyunny](https://github.com/wjdrbs96/Today-I-Learn/blob/master/Interview/Network.md#%EC%9D%B8%EC%A6%9Dauthentication)
<br><br><br>



## MSA 환경에서의 분산 트랜잭션 관리
- 2PC
  - Content
- SAGA
  - Content
- Outbox 패턴
  - Content
- Ref.
[dev_hwan.log](https://velog.io/@ch200203/MSA-%ED%99%98%EA%B2%BD%EC%97%90%EC%84%9C%EC%9D%98-%EB%B6%84%EC%82%B0-%ED%8A%B8%EB%9E%9C%EC%9E%AD%EC%85%98-%EA%B4%80%EB%A6%AC2PC-SAGA-%ED%8C%A8%ED%84%B4),
[RIDI](https://ridicorp.com/story/transactional-outbox-pattern-ridi/)
<br><br><br>
