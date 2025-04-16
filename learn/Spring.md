# Spring
- Inflearn > 스프링 웹 MVC 완전정복

<br><br><br>

# 정리
### Servlet
- Servlet 이란?
  - 서블릿은 자바 기반의 웹 애플리케이션 개발 초기 단계에서 사용된 기술.
  - 클라이언트의 요청을 처리하고 동적 콘텐츠를 생성하는데 사용되었으며, HTTP 요청과 응답을 처리.
    - 자바 클래스 형태로 HTTP 요청을 처리한다.
  - 서블릿은 서블릿 컨테이너에서 실행된다.
- 특징
  - 자바 중심
    - 자바 기반으로 HTML을 사용하여 화면을 그리는 방식.
  - 클래스 단위로 직접적인 HTTP 요청/응답 처리를 세밀하게 제어할 수 있다는 장점이 있다.
  - HTML과 비즈니스 로직이 하나의 서블릿 클래스 안에 혼재되어 있어서, 코드가 복잡하고 그로인하여 유지보수가 어렵다.

### 모델1 방식 - JSP
- JSP(Java Server Page) 란?
  - HTML 내에 Java 코드를 삽입하여 동적 웹 페이지를 생성하는 기술로서 서블릿의 단점을 보완하기 위해 등장한 서블릿 기반의 스크립트 언어이다.
  - 모든 처리 로직이 하나의 JSP 파일에 존재한다.
- 특징
  - HTML 중심
    - HTML 내에 자바 코드를 사용하여 비즈니스 로직을 처리하는 방식.
  - HTML 내에 Java 코드를 직접 삽입할 수 있어 화면 로직을 작성하는 데 매우 편리하고, JSTL 과 같은 태그 라이브러리를 사용하여 반복, 조건, 포맷 등 다양한 작업을 쉽게 처리할 수 있다.

### 모델2 방식 - MVC
- MVC (Model-View-Controller) 패턴을 따르는 구조로, 서블릿과 JSP를 결합하여 웹 애플리케이션을 개발하는 방식.
- MVC 패턴
  - Model (Java Bean)
    - 비즈니스 로직과 데이터 관리
  - View (JSP)
    - 사용자 인터페이스
  - Controller (Servlet)
    - 사용자 요청을 처리하고 모델과 뷰를 연결
- 특징
  - 화면은 JSP가 담당하고 비즈니스 로직은 Servlet이 담당하는 구조로 진화함으로서, 코드의 분리가 명확하여 유지보수가 용이하고 확장성이 높아졌다.
    - 요청이 들어오면 Servlet에서 비즈니스 로직을 처리하고, 결과만 JSP로 전달하여 JSP에서는 화면만 출력하는 형태.

### 프론트 컨트롤러 패턴
- 프론트 컨트롤러 패턴
  - 웹 애플리케이션이 점점 복잡해지고 유지보수와 확장성을 필요로 하게 되면서 모델2 방식을 개선한 프론트 컨트롤러 패턴이 등장하게 되었다.
  - 프론트 컨트롤러 패턴은 모델2 방식의 단점을 보완하고 서블릿의 요청과 응답을 좀 더 구조적이고 체계적으로 관리하기 위해 탄생한 패턴이다.
- 특징
  - 모든 클라이언트 요청을 무조건 단일 진입점을 거치도록 강제함으로서 요청 처리의 일관성을 유지할 수 있고 중앙에서 관리할 수 있게 된다.
  - 인증, 권한 부여, 로깅, 예외 처리 등의 공통 기능을 프론트 컨트롤러에서 일괄 처리해서 코드 중복을 줄이고, 유지보수를 용이하게 할 수 있다.
  - 공통 기능을 수정할 때 프론트 컨트롤러에서만 변경하면 되므로 수정이 용이하고 필요 시 각 서블릿을 쉽게 추가하고 확장 할 수 있다.

### 서블릿(Servlet)
- 서블릿이란?
  - 서블릿은 Jakarta EE (Enterprise Edition) 플랫폼의 핵심 기술 중 하나로 클라이언트-서버 모델에서 서버 측에서 실행되는 작은 자바 프로그램이다.
  - 주로 HTTP 요청과 응답을 처리하기 위해 사용되며 자바 서블릿 API를 통해 웹 애플리케이션 개발을 쉽게 할 수 있도록 해준다.
- 서블릿 생명 주기(Servlet Lifecycle)
  - 서블릿은 서블릿 컨테이너에 의해 클래스 로드 및 객체 생성이 이루어지며 서블릿의 생명주기는 init, service, destroy 과정을 거친다.
    - init
      - 초기화 작업
      - 서블릿이 생성되고 init 메서드를 통해 초기화 되며 최초 한 번만 호출된다
      - 주로 초기화 파라미터를 읽거나 DB 연결 설정 등 초기 설정 작업을 수행한다
    - service
      - 요청 처리 작업
      - 클라이언트로부터의 모든 요청은 service 메서드를 통해 처리되며 HttpServletRequest 와 HttpServletResponse 객체가 생성되어 전달된다
      - HTTP 메서드(GET, POST 등) 에 따라 doGet, doPost 등의 메서드를 호출한다
    - destroy
      - 종료 작업
      - 서블릿이 서비스에서 제외되면 destroy() 메서드를 통해 종료되고 이후 가비지 컬렉션 및 finalize 과정을 거친다
- 서블릿 로드 및 생성
  - 서블릿 로드란?
    - 서블릿 컨테이너는 서블릿을 처음으로 요청받거나 혹은 애플리케이션이 시작될 때 서블릿을 메모리에 로드한다.
    - 지연로딩과 즉시로딩 두 가지 방식이 있다.
      - 지연 로딩 (Lazy Loading)
        - 첫 번째 클라이언트 요청이 들어올 때 서블릿이 로드되고 서블릿 객체를 생성한다.
      - 즉시 로딩 (Eager Loading)
        - 애플리케이션이 시작될 때 서블릿이 로드되고 객체가 생성된다.
    - 이를 위해 <load-on-startup> 속성을 사용한다.
      - 음수 값 또는 설정하지 않은 경우
        - 서블릿은 지연 로딩된다.
      - 양수 값
        - 즉시 서블릿이 로딩되면 값이 낮을수록 더 높은 우선 순위를 가지며 1이 가장 먼저 로된다.
      - 0 값
        - 애플리케이션 시작 시 서블릿을 로드하지만 양수 값들보다 우선하지 않을 수 있다.

### HttpServletRequest
- HttpServletRequest 란?
  - HttpServletRequest 는 클라이언트로부터 Http 요청이 들어오면 요청 데이터를 분석하고, 분석한 정보들이 저장되어 HttpServletResponse 와 함께 서블릿으로 전달되는 객체이다.
- HttpServletRequest 구조
  - HTTP 메서드
  - 요청 URI
  - 요청 프로토콜
  - 요청 파라미터
  - 헤더 정보 등으로 구성된다.
- HttpServletRequest 생성
  - HTTP 요청이 시작되면 총 3개의 Request 객체가 순서대로 생성된다.
    - org.apache.coyote.Request 객체 생성
      - 낮은 수준의 HTTP 요청 처리를 담당하여 서블릿 컨테이너와 독립적으로 동작.
    - org.apache.catalina.connector.Request 객체 생성
      - 서블릿 API 규격을 구현하여 고수준 요청 데이터를 처리
      - 서블릿 컨테이너에서는 coyote.Request를 직접 사용할 수 없어서, 그것보다 고수준의 Request가 필요하고 이러한 이유로 생성되는 객체이다.
    - org.apache.catalina.connector.RequestFacade 객체 생성
      - 캡슐화를 통해 서블릿 API 사용을 표준화하고 내부 구현을 보호
      - org.apache.catalina.connector.Request 객체를 한 번 더 감싸고 있는 개념이다.
- 스프링의 Request
  - 앞서 살펴본 Request 이외에도 스프링에서만 특화된 Request 객체가 존재한다. (하지만 스프링에서도 위 Request 객체들을 주로 사용한다.)
    - WebRequest
      - HTTP 요청의 파라미터, 헤더 등 메타데이터에 대한 추상화된 접근을 제공하는 인터페이스
    - NativeWebRequest
      - 네이티브 서블릿 객체(HttpServletRequest) 에 접근할 수 있는 인터페이스
    - ServletWebRequest
      - HttpServletRequest 와 HttpServletResponse 를 감싸며 Spring 자체 추상화된 요청/응답 기능을 제공하는 구현체

### HttpServletRequest - 요청 처리
- HttpServletRequest는 클라이언트의 다양한 데이터 포맷과 요청 유형에 따라 정보를 읽고 처리할 수 있는 API를 제공한다.
- 요청을 처리하는 방식으로 URL 쿼리 파라미터, 폼 데이터(GET/POST), REST API 처리 등 세 가지로 나누어 구분 할 수 있다.
  - URL 쿼리 파라미터
    - URL 쿼리 파라미터는 HTTP 요청의 쿼리 문자열(Query String)에 포함되어 전달되며, 이는 보통 GET 요청에서 사용된다.
    - 주요 API
      - request.getParameter(String name)
        - 단일 파라미터 값을 반환한다.
      - request.getParameterValues(String name)
        - 다중 파라미터 값을 배열로 반환한다.
      - request.getParameterMap()
        - 모든 파라미터를 Map<String, String[]> 형식으로 반환한다.
  - FORM 데이터 처리
    - FORM 데이터는 HTML <form> 태그를 통해 클라이언트에서 서버로 전달되며 데이터는 요청 메서드에 따라 다르게 처리된다.
      - GET 방식
        - 요청 데이터가 URL의 쿼리 문자열에 포함된다
        - 전송 데이터의 크기는 URL 길이 제한에 의해 제약을 받지 않고 URL이 노출되므로 민감한 데이터 전송에 적합하지 않다
      - POST 방식
        - 요청 데이터가 HTTP 요청 본문에 포함된다
    - 주요 API
      - 위의 'URL 쿼리 파라미터'와 동일
  - REST API 데이터 처리
    - REST API 요청은 클라이언트가 JSON 또는 Plain Text 형태의 데이터를 HTTP 요청 본문에 포함하여 서버로 전송하는 방식으로서 getParameter() 와 같은 방법이 아닌 InputStream 으로부터 본문 데이터를 직접 읽어야 한다.
    - 주요 API
      - request.getReader()
        - 요청 본문을 문자 스트림으로 읽는다
      - request.getInputStream()
        - 요청 본문을 바이너리 스트림으로 읽는다

### HttpServletResponse
- HttpServletResponse 란?
  - 서버가 클라이언트의 요청에 대한 응답을 생성하고 반환할 때 사용되며, HTTP 응답의 상태 코드, 헤더, 본문 데이터를 설정하고 제어하는 다양한 메서드를 제공한다.
- 주요 API
  - setStatus(int sc)
    - 응답 상태 코드를 설정
  - sendError(int sc, String msg)
    - 상태 코드와 메시지를 설정하여 에러 응답을 전송
  - setHeader(String name, String value)
    - 응답 헤더 설정
    - name이 동일할 경우, 덮어써진다.
  - addHeader(String name, String value)
    - 응답 헤더 추가
  - setContentType(String type)
    - 응답 본문의 콘텐츠 타입 설정
  - getWriter()
    - 응답 본문 작성을 위한 PrintWriter 반환
  - sendRedirect(String location)
    - 클라이언트를 다른 URL로 리다이렉트
  - addCookie(Cookie cookie)
    - 쿠키 추가
- HttpServletResponse 생성
  - HTTP 요청이 시작되면 총 3 개의 Response 객체가 순서대로 생성된다.
    - org.apache.coyote.Response 객체 생성
      - 낮은 수준의 HTTP 응답 처리를 담당하여 서블릿 컨테이너와 독립적으로 동작
    - org.apache.catalina.connector.Response 객체 생성
      - 서블릿 API 규격을 구현하여 고수준 응답 데이터를 처리
    - org.apache.catalina.connector.ResponseFacade 객체 생성
      - 캡슐화를 통해 서블릿 API 사용을 표준화하고 내부 구현을 보호

### HttpServletResponse – 응답 처리
- HttpServletResponse는 응답을 처리하는 방식으로 단순 텍스트 응답, HTML 화면 처리 응답, HTTP 본문 응답 등 세 가지로 나누어 구분 할 수 있다
- 스프링에서도 응답 패턴이 이 세 가지 범주에서 크게 벗어나지 않으며 사용하기 쉽게 추상화해서 제공하고 있다
  - 단순 텍스트 응답
    - 간단한 문자열 데이터를 응답 본문으로 클라이언트에 전송
  - HTML 화면 처리 응답
    - HTML 컨텐츠를 렌더링하여 브라우저가 화면에 표시하도록 전송
  - HTTP 본문 응답
    - JSON, XML, 바이너리 데이터 등 다양한 형식의 HTTP 응답 본문 데이터를 전송
   
### 서블릿 컨테이너 & 스프링 컨테이너
- 서블릿 컨네이너 & 스프링 컨테이너 연결
  1. WAS 가 구동되면 서블릿 컨테이너가 META-INF/services/jakarta.servlet.ServletContainerInitializer 파일을 검색하여 ServletContainerInitializer 인터페이스를 구현한 클래스(ex. MyServletContainerInitializer)를 로드한다.
    - jakarta.servlet.ServletContainerInitializer 파일의 내용에는 study.choi.MyServletContainerInitializer 와 같이 기술되어있다.
  2. ServletContainerInitializer 구현체는 @HandlesTypes(MyWebAppInitializer.class)와 같이 설정을 할 수 있으며, MyWebAppInitialize를 호출하여 스프링 어플리케이션을 초기화 한다.
- ServletContainerInitializer
  - 웹 애플리케이션이 시작될 때 자동으로 실행되는 초기화 코드를 작성하고 싶을 때 사용하는 인터페이스이다.
  - 동작방식
    1. /META-INF/services/jakarta.servlet.ServletContainerInitializer 에 클래스 정보를 입력 하면 초기화 시 해당 파일이 있는지 검색한 후 실행한다.
       - META-INF/services/javax.servlet.ServletContainerInitializer 파일 내용에는 study.choi.MyServletContainerInitializer 와 같이 기술되어 있음.
    2. ServletContainerInitializer 클래스(이 때 구현체는 MyServletContainerInitializer라 가정)에 @HandlesTypes 어노테이션을 붙이면 주어진 타입에 대해 컨테이너가 자동으로 스캐닝을 수행한다.
       - ```
         @HandlesTypes(MyWebAppInitializer.class) // 여기서 선언되었기 때문에 아래 메서드인 onStartup()에 의해서 MyWebAppInitializer를 구현한 서블릿이 로드 된다.
         public class MyServletContainerInitializer implements ServletContainerInitializer {
           @Override
           public void onStartup(Set<Class<?>> c, ServletContext ctx) throws ServletException {
             for (Class<?> initClass : c) {
               MyWebAppInitializer initializer
                 = (MyWebAppInitializer) initClass.getDeclaredConstructor().newInstance();
               initializer.onStartup(ctx);
              }
           }
         }
         ```
- SpringServletContainerInitializer
  - 스프링은 SpringServletContainerInitializer 라는 구현체를 제공하며 이는 스프링 애플리케이션에서 서블릿 컨테이너와의 초기 상호작용을 담당한다.
  - SpringServletContainerInitializer는 @HandlesTypes 어노테이션에 WebApplicationInitializer 타입이 선언되어 있으며 이는 WebApplicationInitializer 인터페이스를 구현한 클래스를 자동으로 탐색하고 이를 호출하여 스프링 어플리케이션을 초기화 한다.
- WebApplicationInitializer
  - 스프링 애플리케이션이 구동되면 WebApplicationInitializer 타입의 클래스가 실행되고 여기서 스프링 컨테이너 초기화 및 설정 작업이 이루어진다.
- 전체 구성도
  - <img width="1047" alt="image" src="https://github.com/user-attachments/assets/47755dbb-7c38-496f-9f36-092ec0ebb50f" />
