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

### 초기화 클래스들
- 스프링 부트는 웹 MVC 초기화와 실행을 위한 여러 빈들을 생성하고 초기 값들을 설정하기 위한 여러 클래스들을 정의하고 있다.
  - WebMvcProperties
    - 스프링 MVC 의 여러 속성들을 환경설정파일(properties, yml) 을 통해 설정할 수 있다.
  - DispatcherServletAutoConfiguration
    - DispatcherServlet 자동 설정 클래스
  - WebMvcAutoConfiguration
    - 메시지 컨버터, 뷰 리졸버, 포맷터, 인터셉터, 리소스 핸들러 등 Web MVC에서 자주 사용하는 Bean들이 이 클래스를 통해 자동 구성된다.
    - 내부적으로 WebMvcAutoConfigurationAdapter와 EnableWebMvcConfiguration 등의 클래스를 가지고 있다.
      - WebMvcAutoConfigurationAdapter
        - WebMvcConfigurer 인터페이스를 구현한 추상 클래스로서 스프링 부트에서 제공하는 여러 기본 MVC 설정을 제공하며, 사용자가 직접 WebMvcConfigurer 인터페이스를 직접 구현하여 커스트 마이징 할 수 있다.
      - EnableWebMvcConfiguration
        - 전통적인 스프링 MVC에서 @EnableWebMvc 를 사용할 때 MVC 구성에 필요한 핵심 Bean 등록(핸들러 매핑, 핸들러 어댑터, 뷰 리졸버 등)을 담당하는 추상 클래스로서 스프링 MVC의 ‘기본 골격’이라고 볼 수 있다
        - 주요 기능
          - 핸들러 매핑 및 핸들러 어댑터 설정
          - 뷰 리졸버(ViewResolver) 설정
          - MessageConverters 설정
          - Validator와 Formatting 설정
          - 인터셉터(Interceptors) 및 기타 커스터마이징 포인트
          - 정적 리소스 제공 설정
  - WebMvcConfigurer
    - WebMvcConfigurer 는 Web MVC 관련 설정을 커스터마이징할 수 있는 다양한 메서드를 정의하고 있으며 스프링 부트가 기본적으로 제공하는 자동 구성을 유지하면서 필요한 부분만 맞춤형으로 설정할 수 있다.
    - 예를 들어 정적 리소스 매핑(addResourceHandlers), CORS 설정(addCorsMappings), 메시지 컨버터 등록(configureMessageConverters), 인터셉터 추가(addInterceptors) 등 MVC 전반에 걸친 세부 설정들을 손쉽게 추가하거나 변경할 수 있다.

### 스프링 웹 MVC 기본 아키텍처
- 구성
  - DispatcherServlet
    - 모든 클라이언트의 요청을 한 곳에서 받아 공통으로 처리하는 객체
  - HandlerMapping
    - 여러 요청 핸들러 중 현재 요청을 처리하기 적합한 핸들러를 탐색하고 선택하는 객체
  - HandlerAdapter
    - 선택한 요청 핸들러를 실제 호출하는 객체
  - Handler
    - 실질적으로 현재 요청을 처리하는 객체
  - ModelAndView
    - 요청 처리 중 생성되거나 전달받은 데이터와 뷰 정보를 저장하는 객체
  - ViewResolver
    - 여러 뷰 중 현재 응답을 처리하기 적합한 뷰를 선택하는 객체
  - View
    - 화면을 렌더링 하는 객체
- 흐름도
  - ![image](https://github.com/user-attachments/assets/d0899653-fa1b-40e1-b155-e0d0581d2ddf)

### DispatcherServlet
- DispatcherServlet 란?
  - 스프링 MVC의 핵심 프론트 컨트롤러로 모든 HTTP 요청을 중앙에서 받아 처리하는 역할을 한다.
  - 요청을 적절한 핸들러(일반적으로 컨트롤러)로 라우팅하고 요청 처리 후에는 적절한 뷰를 선택하여 응답을 반환한다.
  - 핸들러 매핑, 뷰 리졸버, 인터셉터 등을 조정하여 요청 처리 흐름을 관리하고 스프링 MVC 애플리케이션에서 중심적인 역할을 수행한다.
- init() / service()
  - DispatcherServlet 은 요청이 시작되면 서블릿의 생명주기에 따라 init() 메서드와 service() 메서드가 실행되어 초기화 작업 및 실제 요청을 처리하게 된다.
  - init()
    - 요청이 시작되면 DispatcherServlet 의 init() 메서드가 호출되며 최초 한번 실행된다.
      - DispatcherServlet의에는 실제로 init()이라고 구현된 메서드는 없다.
        - 하지만 DispatcherServlet은 HttpServlet을 상속한 FrameworkServlet의 하위 클래스이고, 그 부모 클래스에서 init() 메서드를 오버라이드하고 있다.
        - HttpServlet에는 init() 메서드가 존재하며, FrameworkServlet에서 이 init() 메서드를 오버라이드하여 Spring의 초기화 로직을 처리한다. 
        - DispatcherServlet은 FrameworkServlet의 서브 클래스이기 때문에 init() 메서드를 직접 정의하지 않더라도 상속받아 사용할 수 있다.
        - 즉, DispatcherServlet의 초기화 로직은 실제로 init() → initServletBean() → onRefresh() → initStrategies() 순서로 연결된다.
          - ```
            protected void initStrategies(ApplicationContext context) {
              this.initMultipartResolver(context);
              this.initLocaleResolver(context);
              this.initThemeResolver(context);
              this.initHandlerMappings(context);
              this.initHandlerAdapters(context);
              this.initHandlerExceptionResolvers(context);
              this.initRequestToViewNameTranslator(context);
              this.initViewResolvers(context);
              this.initFlashMapManager(context);
            }          
            ```
    - WebApplicationContext 를 생성 및 초기화하며 HandlerMapping, HandlerAdapter, ViewResolver 등의 필수 구성요소를 초기화하고 모든 요청을 처리할 준비를 완료한다.
  - service()
    - 매 요청 마다 실행되는 메서드로 HTTP 요청을 분석하여 적합한 핸들러(Controller)를 찾고 실행하는 역할을 한다.
    - 실행 결과를 기반으로 뷰(View)를 렌더링하여 클라이언트에게 응답을 반환한다.
    - init()과 비슷하게 실제로 service() 메서드는 없고 doService() 메서드가 존재한다.
- doDispatch()
  - 실제 핸들러로 요청을 디스패치하는 작업을 처리한다.
  - 모든 HTTP 메서드는 doDispatch() 메서드에 의해 처리가 이루어진다.
  - doDispatch()는 doService() 내부에서 호출된다.
    - ```
      protected void doDispatch(HttpServletRequest request, HttpServletResponse response) {
        //현재 요청을 처리할 핸들러 검색
        HandlerExecutionChain mappedHandler = getHandler(request);
          
        // 현재 요청에 대한 핸들러 어댑터를 결정
        HandlerAdapter ha = getHandlerAdapter(mappedHandler.getHandler());
          
        // 전 처리 인터셉터 수행
        if (!mappedHandler.applyPreHandle(request, response)) return;
          
        // 실제 핸들러 호출 후 ModelAndView 반환
        ModelAndView mv = ha.handle(request, response, mappedHandler.getHandler());
          
        // 후 처리 인터셉터 수행
        mappedHandler.applyPostHandle(request, response, mv);
          
        // 뷰 이름 확인
        String viewName = mv.getViewName();
          
        // 뷰 리졸버를 통해 뷰 선택
        View view = resolveViewName(viewName, mv.getModelInternal(), locale, request);
          
        // 뷰 렌더링
        view.render(mv.getModelInternal(), request, response);
      }
      ```
      
### HandlerMapping
- HandlerMapping 이란?
  - 요청 URL과 이를 처리할 핸들러(Handler, 일반적으로 Controller)를 매핑하는 인터페이스이다.
  - 클라이언트 요청이 들어오면 DispatcherServlet 은 등록된 모든 HandlerMapping 구현체를 탐색하여 적합한 핸들러를 찾아 반환하고 이후 적절한 HandlerAdapter 를 통해 실행한다.
  - HandlerMapping 은 핸들러를 검색해서 찾는 역할만 할 뿐 핸들러를 실행하지는 않는다. 핸들러 실행은 HandlerAdapter 가 담당한다.
- HandlerMapping의 종류 중 일부
  - BeanNameUrlHandlerMapping
   - Bean 이름을 URL로 매핑
   - 현재는 잘 사용되지 않는 이전 방식
   - ```
     @Component("/beanHandler") // Bean 이름이 요청 URL과 매핑됨
     public class BeanNameHandler implements Controller {
       @Override
       public ModelAndView handleRequest(HttpServletRequest req, HttpServletResponse res) throws Exception {
         response.getWriter().write("BeanNameUrlHandlerMapping!");
         return null;
       }
     }
     ```
  - SimpleUrlHandlerMapping
    - 명시적으로 URL 패턴을 핸들러와 매핑하는 방식으로서 간단한 URL 매핑에 사용된다.
    - ```
      public class MyHttpRequestHandler implements HttpRequestHandler {
        @Override
        public void handleRequest(HttpServletRequest req, HttpServletResponse resp) throws IOException {
          response.setContentType("text/plain");
          response.getWriter().write("SimpleUrlHandlerMapping!");
        }
      }
      
      // 위 동작을 위해 bean으로 등록이 필요하다.
      @Bean
      public SimpleUrlHandlerMapping simpleUrlHandlerMapping() {
        SimpleUrlHandlerMapping mapping = new SimpleUrlHandlerMapping();
        Properties urlMappings = new Properties();
        urlMappings.setProperty("/simpleUrl", "myHttpRequestHandler");
        mapping.setMappings(urlMappings);
        mapping.setOrder(1);
        return mapping;
      }
      
      @Bean
      public MyHttpRequestHandler myHttpRequestHandler() {
        return new MyHttpRequestHandler();
      }
      ```
  - RequestMappingHandlerMapping
    - 가장 우선순위가 높고 대부분 이 방식을 사용
    - @RequestMapping 또는 @GetMapping, @PostMapping 과 같은 애노테이션을 기반으로 URL과 핸들러를 매핑한다.
- Handler 구현 방식
  - @Controller, @RestController
    - Spring MVC 에서 가장 널리 사용되는 요청 처리 방식으로서 클래스에 @Controller 를 붙이고 메서드에 @RequestMapping 과 같은 어노테이션을 사용하여 요청을 처리한다.
  - Controller 인터페이스
    - Spring 2.5 이전에 사용되던 요청 처리 방식으로서 Controller 인터페이스를 구현하여 요청을 처리한다.
  - HttpRequestHandler
    - HttpRequestHandler 인터페이스를 구현하여 요청을 처리하는 방식으로서 Spring의 가장 저수준 API 중 하나로 서블릿에 가까운 형태로 동작한다.

### @RequestMapping
- 개요
  - @RequestMapping은 특정 URL 경로에 대한 요청을 처리할 메서드를 매핑하는 데 사용되는 어노테이션이다.
  - @RequestMapping은 @Controller 및 @RestController로 선언된 클래스에서 사용되며 내부적으로 RequestMappingHandlerMapping 클래스가 처리하고 있다
- 매핑 종류
  - URL 매핑
    - 경로 매핑 URI 는 예를 들어 "/profile"과 같은 형태를 가진다.
    - Ant 스타일의 경로 패턴("/user/**") 지원한다.
    - 다중 설정({"/user/**“, "/mypage"})도 가능하다.
    - 클래스 레벨에도 작성 가능하다.
      - 클래스에 /user, 메서드에 /edit으로 명명되어있다면, 실제 메서드는 /user/edit으로 호출 가능
    - 매핑 URI는 플레이스홀더(예: "/${profile_path}")를 포함할 수 있다.
  - HTTP 메서드 매핑
    - GET, POST, HEAD, OPTIONS, PUT, PATCH, DELETE, TRACE 메서드를 설정할 수 있다.
      - @RequestMapping(value = "/user", method = RequestMethod.GET) 에서 method = RequestMethod.GET에 해당
    - 클래스 수준에서 사용되는 경우 모든 메서드 수준 매핑은 해당 HTTP 메서드 설정을 상속받는다.
    - 클래스 수준과 메서드 수준이 함께 설정되었을 경우 메서드 수준의 HTTP 메서드 설정이 타입 수준의 설정을 덮어쓴다. 즉, 메서드 수준의 설정이 우선 적용된다.
  - param 매핑
    - 사용예시
      - @RequestMapping(value = "/order", params = "type=pizza")
    - 표현식은 != 연산자를 사용하여 부정할 수 있다.
    - "myParam" 표현식도 지원되며 요청에 존재해야 하지만 어떤 값이라도 가질 수 있다.
    - "!myParam" 표현식은 해당 매개변수가 요청에 포함되지 않아야 함을 나타낸다.
  - headers 매핑
    - 사용예시
      - @RequestMapping(value = "/json", method = RequestMethod.POST, headers = "content-type=application/json")
  - produces 와 consumes
    - produces
      - @RequestMapping(value = "/report", method = RequestMethod.GET, produces = "application/json")
      - 클라이언트가 서버에 요청을 보낼 때 서버가 어떤 형식의 데이터를 반환할지를 지정한다.
    - consumes
      - @RequestMapping(value = "/report", method = RequestMethod.POST, consumes = "application/json")
      - 클라이언트가 서버로 전송하는 데이터의 형식을 제한한다
- @RequestMapping 축약 어노테이션
  - URL 매핑 +  HTTP 메서드 매핑을 아래와 같이 축약한 어노테이션도 제공한다.
    - @GetMapping
    - @PostMapping
    - @PutMapping
    - @DeleteMapping
- 핵심 클래스
  - RequestMappingHandlerMapping
    - @RequestMapping 이 선언된 모든 핸들러를 검사하고 해당 핸들러와 URL 경로를 매핑하여 저장소에 저장한다.
    - 요청이 들어오면 매핑 저장소로부터 URL 패턴과 일치하는 핸들러를 검색하고 적합한 핸들러를 찾아 반환한다.
  - HandlerMethod
    - 핸들러 객체로서 최종 호출할 컨트롤러와 메서드 정보를 포함하고 있다.
    - 메서드의 매개변수, 반환 값, 메서드에 정의된 어노테이션 등에 쉽게 접근할 수 있는 기능을 제공한다.
  - RequestMappingInfo
    - @RequestMapping 에 선언된 여러 속성들의 값들을 추출해서 가지고 있는 객체
    - Map 형태이며 key로는 RequestMappingInfo 클래스를, value로는 HandlerMethod를 사용한다.
    - RequestMappingInfo는 uri path와 method param 등을 정보로 가지고 있다.
      - Ex. path=/api/user, method=POST, param=[]
    - HandlerMethod는 빈, 메서드 등을 정보로 가지고 있다.
      - Ex. bean=RestApiController, method=user(), parameters=AccountDto
  - MappingRegistry
    - 모든 HandlerMethod 및 매핑된 경로를 저장하고 관리하는 클래스로서 요청을 처리할 핸들러를 조회할 수 있다.
  - HandlerExecutionChain
    - HandlerMethod 와 HandlerIntercepter 를 포함하고 있으며 HandlerAdapter에게 전달된다.

### HandlerAdapter
- HandlerAdapter란?
  - HandlerAdapter 는 스프링 MVC에서 핸들러(Handler)를 호출하는 역할을 하는 인터페이스이다.
  - HandlerAdapter 는 다양한 타입의 핸들러들이 일관된 방식으로 호출 될 수 있도록 해 주며 핸들러가 다양한 타입으로 정의되더라도 그에 맞는 호출 방식을 제공해 준다.
  - 요청이 들어왔을 때 어떤 핸들러가 해당 요청을 처리할지 결정하는 것이 HandlerMapping 이라면 HandlerAdapter 는 결정된 핸들러를 호출하여 실행하는 역할을 한다.
- 구조
  - HandlerAdapter는 인터페이스로 아래 메서드를 갖는다.
    - boolean supports(Object handler);
      - 어댑터가 해당 핸들러를 지원하는지 결정
    - ModelAndView handle(HttpServletRequest request, HttpServletResponse response, Object handler) throws Exception
      - supports가 true를 반환하면 해당 메서드가 실행되며, 실제적인 처리를 담당한다.
  - HandlerAdapter는 아래와 같은 구현체를 갖는다.
    - HttpRequestHandlerAdapter
      - HttpRequestHandler 인터페이스를 구현하여 요청을 처리할 수 있도록 해 준다.
    - RequestMappingHandlerAdapter
      - @RequestMapping 어노테이션으로 매핑된 메서드를 처리하는 클래스로서 대부분 이 클래스가 사용된다.
    - SimpleControllerHandlerAdapter
      - 일반적인 Controller 인터페이스를 구현하여 요청을 처리할 수 있도록 해 준다.

### Method Arguments
- Method Arguments란?
  - 스프링의 메서드 매개변수(Method Arguments)는 컨트롤러 메서드에서 HTTP 요청 데이터를 직접 접근하고 처리할 수 있도록 다양한 매개변수를 지원한다
  - 요청의 URL, 헤더, 본문, 쿠키, 세션 데이터 등과 같은 정보를 자동으로 매핑하여 개발자가 이를 쉽게 활용할 수 있도록 제공한다.
- HandlerMethodArgumentResolver
  - HTTP 요청과 관련된 데이터를 컨트롤러 메서드의 파라미터로 변환하는 작업을 담당하는 클래스이다.
  - 다양한 유형의 파라미터 (예: @RequestParam, @PathVariable, @RequestBody 등)를 처리하기 위해 여러 HandlerMethodArgumentResolver 기본 구현체를 제공한다.

### 메서드 기본 매개변수
- 스프링 MVC 에서 메서드 파라미터에 공통적으로 선언할 수 있는 기본 인자들이 있으며 요청 및 응답 처리, 세션 관리, 인증 정보 접근 등 다양한 상황에서 적절하게 사용될 수 있다.
- 종류
  - WebRequest / NativeWebRequest
    - WebRequest 와 NativeWebRequest 는 웹 요청에 대한 다양한 정보를 제공하는 객체로서 HttpServletRequest 보다 더 많은 메서드와 웹 요청 전반에 쉽게 접근한다
    - ```
      @GetMapping("/example")
      public String handleWebRequest(WebRequest webRequest, NativeWebRequest nativeWebRequest) {
        // ...
      }
      ```
  - HttpSession
    - HttpSession은 서버에 저장된 세션 데이터를 다룰 수 있게 해주는 객체로서 사용자의 세션 정보를 읽거나 설정할 수 있다.
    - ```
      @GetMapping("/example")
      public String handleHttpSession(HttpSession session) {
        // ...
      }
      ```
  - Principal
    - Principal은 현재 인증된 사용자의 정보를 나타내는 객체로서 사용자 이름이나 인증된 사용자와 관련된 데이터를 제공해 준다.
    - 스프링 시큐리티와 통합되어 제공하는 기능이다.
    - ```
      @GetMapping("/example")
      public String handlePrincipal(Principal principal) {
        // ...
      }
      ```
  - HttpMethod
    - HttpMethod 는 요청 메서드(GET, POST 등)를 나타내며 현재 요청이 어떤 HTTP 메서드인지 확인할 수 있다.
    - ```
      @PostMapping("/checkMethod")
      public String handleHttpMethod(HttpMethod method) {
        // ...
      }
      ```
  - InputStream&Reader / OutputStream&Writer
    - Reader는 요청 본문을 읽는 데 사용되며 Writer는 응답 본문에 데이터를 작성하는 데 사용된다.
    - ```
      @PostMapping("/readwrite")
      public String handleReader(Reader reader, Writer writer) throws IOException {
        // ...
      }
      ```