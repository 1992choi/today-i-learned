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
  2. ServletContainerInitializer 구현체는 @HandlesTypes(MyWebAppInitializer.class)와 같이 설정을 할 수 있으며, MyWebAppInitialize를 호출하여 스프링 애플리케이션을 초기화 한다.
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
  - SpringServletContainerInitializer는 @HandlesTypes 어노테이션에 WebApplicationInitializer 타입이 선언되어 있으며 이는 WebApplicationInitializer 인터페이스를 구현한 클래스를 자동으로 탐색하고 이를 호출하여 스프링 애플리케이션을 초기화 한다.
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
      
### @RquestParam
- @RquestParam이란?
  - @RequestParam 어노테이션은 HTTP 요청의 파라미터를 메서드의 매개변수에 바인딩 되도록 해준다.
  - @RequestParam 은 URL 쿼리 파라미터, 폼 데이터, 그리고 멀티파트 요청을 매핑하며 HTTP 본문 요청은 처리하지 않는다.
    - HTTP 본문 요청은 HttpMessageConvertter가 처리
  - 주로 int, long 과 같은 기본형, 기본형 래퍼 클래스, String 형 매개변수를 바인딩할 때 사용하며 대부분의 객체 타입은 처리하지 않는다.
    - 객체 타입은 @ModelAttribute가 처리
  - 내부적으로 RequestParamMethodArgumentResolver 구현체가 사용되며, request.getParameterValues() 와 같은 API 를 사용하여 바인딩을 해결하고 있다.
- 속성
  - required
    - 요청 시 파라미터를 반드시 포함해야하는지를 설정한다.
      - Ex. @RequestParam(name = "param", required = true) String param
        - 요청 파라미터에 param가 없으면 오류 발생
  - defaultValue
    - 요청 시 파라미터가 없는 경우의 기본 값으로 설정할 때 사용할 수 있다.
      - Ex. @RequestParam(name = "param", defaultValue = "default") String param
        - param이 없다면, 기본값으로 default로 셋팅.
  - Map과 MultiValueMap
    - 모든 요청을 Map 또는 MultiValueMap으로 받고 싶을 때 사용한다.
    - Map과 MultiValueMap의 차이는 동일한 key에 value가 1개인지 2개 이상인지의 차이이다.
      - Ex. @RequestParam Map<String, String> params
        - 요청 : /map?key1=value1&key2=value2
        - 결과 : {key1=value1, key2=value2}
      - Ex. @RequestParam MultiValueMap<String, String> params
        - 요청 : /multivalue-map?key1=value1&key1=value2
        - 결과 : {key1=[value1, value2]}

### @PathVariable
- @PathVariable이란?
  - @PathVariable 은 @RequestMapping 에 지정한 URI 템플릿 변수에 포함된 값을 메서드의 매개변수로 전달하기 위해 사용하는 어노테이션이다.
  - @PathVariable 은 GET, DELETE, PUT, POST 요청에서 사용 할 수 있다.
- 사용 예시
  - 기본 예시
    - ```
      @GetMapping("/projects/{project}")
      public String getProjectVersions(@PathVariable("project") String project) {
      }
      ```
  - 여러 군데 지정
    - ```
      @GetMapping("/projects/{project}/versions/{version}")
      public String getProjectVersions(@PathVariable("project") String project, @PathVariable("version") String version) {
      }
      ```
  - 정규 표현식과 함께 사용
    - ```
      @GetMapping("/projects/{projectId:[a-z]+}/details")
      public String getProjectDetails(@PathVariable("projectId") String projectId) {
      }
      ``` 
      
### @ModelAttribute
- @ModelAttribute란?
  - @ModelAttribute는 스프링 MVC에서 주로 폼 데이터나 요청 파라미터를 모델 객체에 바인딩할 때 사용하는 어노테이션이다.
  - 이 어노테이션은 요청 파라미터를 특정 객체의 각 필드(요청 파라미터명과 일치)에 바인딩하고 이후 자동으로 모델에 추가하여 뷰에서 사용할 수 있게 한다.
  - 일반적으로 기본형 타입(int, long, String ..)의 바인딩은 @RequestParam이 처리하고 객체 타입은 @ModelAttribute가 처리한다고 보면 된다.
- @BindParam
  - @ModelAttribute 는 요청 파라미터와 일치하는 생성자를 통해 객체를 생성할 수도 있으며, 생성자 바인딩을 사용할 때는 @BindParam을 이용해 요청 파라미터의 이름을 매핑할 있다.
  - Ex. 요청이 /account?first-name=leaven 일 때
    - ```
      // DTO
      public class Account {
        private final String firstName;
        
        public Account(@BindParam("first-name") String firstName) {
          this.firstName = firstName;
        }
      }
      
      // Controller
      @PostMapping("/account")
      public String processAccount(@ModelAttribute Account account) {
      }
      ```

### @RequestBody
- @RequestBody란?
  - HTTP 요청 본문(HTTP Body)을 자동으로 객체로 매핑하는데 사용되며, 내부적으로 HttpMessageConverter 객체가 작동되어 본문을 처리한다.
  - @Valid 애너테이션과 함께 사용하면 요청 본문의 유효성을 쉽게 검증할 수 있다.
  - @RequestBody는 반드시 요청 본문이 있어야 하며 요청 본문이 없을 경우 HttpMessageNotReadableException 이 발생한다.
  - @RequestBody는 요청의 Content-Type 헤더를 기반으로 적절한 HttpMessageConverter를 선택하기 때문에 Content-Type 헤더가 올바르게 설정되어야 한다.
  - @RequestBody 는 생략하면 안된다.
    - 생략할 경우 기본형은 @RequestParam, 객체 타입은 @ModelAttribute가 작동하게 되지만 정확한 결과를 보장할 수 없다.

### HttpMessageConverter
- 개요
  - HttpMessageConverter는 HTTP 요청과 응답의 바디(body) 내용을 객체로 변환하고 객체를 HTTP 메시지로 변환하는데 사용되는 인터페이스이다.
  - HttpMessageConverter는 클라이언트와 서버 간의 데이터를 직렬화/역직렬화하는 기능을 담당하며, 주로 JSON, XML, Plain Text와 같은 다양한 데이터 포맷을 지원한다.
  - HttpMessageConverter는 주로 Rest API 통신에서 사용된다.
- HttpMessageConverter 요청 처리 흐름
  1. 클라이언트의 Content-Type 헤더
     - 클라이언트가 서버로 데이터를 전송한다. 이때 HTTP 헤더에 Content-Type 을 포함하여 서버에 데이터 형식을 알린다.
     - Ex. Content-type=application/json
  2. ArgumentResolver 실행
     - Spring은 컨트롤러의 메서드 매개변수에 @RequestBody 혹은 HttpEntity 등이 선언 되었는지 확인한다.
     - 선언이 되었다면 HTTP 요청 본문 ArgumentResolver가 선택되고, ArgumentResolver는 HttpMessageConverter 를 실행한다.
  3. HttpMessageConverter 작동
     - HttpMessageConverter는 클라이언트의 Content-Type 헤더를 기준으로 요청 본문 데이터를 특정 객체로 변환한다.
     - Ex. Text는 StringHttpMessageConverter, JSON은 MappingJackson2HttpMessageConverter
- HttpMessageConverter 응답 처리 흐름
  1. 클라이언트의 Accept 헤더
    - 클라이언트는 Accept 헤더를 통해 서버가 어떤 형식의 데이터를 반환해야 하는지 명시한다.
    - Ex. Accept: application/json
  2. ReturnValueHandler 실행
    - Spring은 컨트롤러의 반환 타입에 @ResponseBody 또는 ResponseEntity가 선언되었는지 확인한다.
    - 선언이 되었다면 HTTP 응답 본문 ReturnValueHandler가 선택되고 ReturnValueHandler는 HttpMessageConverter 를 실행한다.
  3. HttpMessageConverter 작동
    - HttpMessageConverter는 클라이언트의 Accept 헤더를 기준으로 데이터를 응답 본문에 기록한다.
    - Ex. Text는 StringHttpMessageConverter, JSON은 MappingJackson2HttpMessageConverter
- HttpMessageConverter 주요 구현체
  - ByteArrayHttpMessageConverter
    - application/octet-stream 과 같은 바이너리 데이터를 처리하며 주로 파일 전송에 사용된다.
  - StringHttpMessageConverter
    - text/plain 과 같은 문자열 데이터를 String 객체로 변환하거나 String 객체를 text/plain 형식으로 변환하여 HTTP 본문에 넣는다.
  - ResourceHttpMessageConverter
    - Resource 타입의 데이터를 HTTP 요청과 응답으로 변환하거나 처리하는데 사용된다.
  - MappingJackson2HttpMessageConverter
    - application/json 형식의 데이터를 파싱하여 Java 객체를 JSON으로 변환하거나 JSON을 Java 객체로 변환한다.
  - FormHttpMessageConverter
    - MultiValueMap + application/x-www-form-urlencoded 형식의 데이터를 파싱하여 MultiValueMap 형태로 변환한다.
- HttpMessageConverter 가 작동하지 않는 요청
  - GET 요청과 같은 본문이 없는 요청
    - GET, DELETE와 같은 HTTP 메서드는 일반적으로 본문을 포함하지 않으므로 HttpMessageConverter가 작동하지 않는다.
  - Content-Type 헤더가 지원되지 않는 요청
    - POST, PUT 등의 본문이 포함된 HTTP 요청이라도 Content-Type 헤더가 지원되지 않는 미디어 타입일 경우 HttpMessageConverter가 작동하지 않는다.
  - @RequestParam, @ModelAttribute를 사용하는 경우
    - @RequestParam, @ModelAttribute 와 같은 어노테이션을 사용하여 쿼리 파라미터를 처리하는 경우에는 HttpMessageConverter가 필요하지 않다.
  - 파일 업로드 요청 중 @RequestPart 또는 MultipartFile을 사용한 경우
    - MultipartFile 이나 @RequestPart 를 사용하면 HttpMessageConverter가 작동하지 않으며, 이 경우에는 MultipartResolver가 요청을 처리한다.
  - 컨트롤러에서 단순 문자열(String) 반환 시 @ResponseBody나 @RestController가 없는 경우
    - @ResponseBody나 @RestController가 없는 경우, 반환된 String은 뷰 이름으로 간주되며 이 경우에는 ViewResolver가 요청을 처리한다.

### @RequestHeader / @RequestAttribute / @CookieValue
- @RequestHeader
  - 클라이언트의 요청 헤더를 컨트롤러의 메서드 인자에 바인딩 하기 위해 @RequestHeader 애노테이션을 사용할 수 있다.
  - RequestHeaderMethodArgumentResolver 클래스가 사용된다.
  - ```
    @RequestHeader("Accept-Encoding") String encoding // 기본 예시
    @RequestHeader("Accept-Encoding", required=false, defaultValue="none") String encoding // 옵션 사용
    @RequestHeader Map<String, String> headers // 맵 사용
    @RequestHeader MultiValueMap<String, String> headers // MultiValueMap 사용
    @RequestHeader("Accept") List<String> acceptHeaders // 리스트 사용
    ```
- @RequestAttribute
  - HTTP 요청 속성(request attribute)을 메서드 파라미터에 바인딩할 때 사용하는 어노테이션.
  - 주로 필터나 인터셉터에서 설정한 값을 컨트롤러 메서드에서 사용할 때 유용하다.
  - RequestAttributeMethodArgumentResolver 클래스가 사용 된다.
  - ```
    @RequestAttribute("myAttribute") String myAttribute
    ```
- @CookieValue
  - HTTP 요청의 쿠키 값을 메서드 파라미터에 바인딩할 때 사용하는 어노테이션.
  - 클라이언트에서 전송한 쿠키 값을 쉽게 받아 처리할 수 있다.
  - ```
    @CookieValue(value = "userSession", defaultValue = "defaultSession") String session
    ```
    
### Model
- Model이란?
  - Model은 컨트롤러와 뷰 사이의 데이터를 전달하는 역할을 하며, 컨트롤러에서 데이터를 Model 객체에 추가하면 그 데이터는 뷰에서 접근할 수 있게 된다.
  - Model 인터페이스는 주로 HTML 렌더링을 위한 데이터 보관소 역할을 하며 Map과 유사한 방식으로 동작한다.
  - 내부적으로 ModelMethodProcessor 클래스가 사용된다.
- 주요 메서드
  - addAttribute(String attributeName, Object attributeValue)
    - 모델에 데이터를 추가할 때 사용한다.
  - addAllAttributes(Map<String, ?> attributes)
    - 여러 개의 속성을 한 번에 추가할 수 있다.
  - asMap()
    - 모델 데이터를 Map으로 변환하여 반환한다.
- BindingAwareModelMap
  - BindingAwareModelMap은 Model 구현체이다.
  - @ModelAttribute로 바인딩된 객체를 가지고 있으며, 바인딩 결과를 저장하는 BindingResult를 생성하고 관리한다.

### @SessionAttributes
- @SessionAttributes란?
  - @SessionAttributes는 세션(Session)에 속성 값을 저장하고 그 값을 다른 요청에서도 사용할 수 있도록 하기 위해 사용되는 어노테이션이다.
  - @SessionAttributes는 컨트롤러 클래스 레벨에 선언되며, 특정 모델 속성 이름을 지정하면 세션에 자동으로 저장된다.
  - @SessionAttributes는 모델에 저장된 객체를 세션에 저장하는 역할과 세션에 저장된 객체를 모델에 저장하는 역할을 한다.
- 예시
  - ```
    @Controller
    @SessionAttributes("user") // 클래스 레벨에 선언
    public class UserController {
    
    @GetMapping("/users")
    public String users (Model model) {
      model.addAttribute("user",new User("springmvc","a@a.com")); // 모델에 담기는 동시에 속성명(="user")과 동일하다면, 클래스 레벨에 선언된 세션에 담긴다. 
      return "redirect:/getUser";
    }
    
    @GetMapping("/getUser")
      public String getUser(@ModelAttribute("user") User user) { // 세션에 있는 값을 가져온다. 만약 지금처럼 @ModelAttribute와 @SessionAttributes의 속성명이 같다면, 모델에서 먼저 찾고 없다면 세션에서 찾는다. 하지만 둘다 없다면 오류를 발생시킨다.
      return "redirect:/getUser2";
    }
    ```
- 세션 초기화 예시
  - ```
    @Controller
    @SessionAttributes("user")
    public class UserController {
    
      @PostMapping("/clearSession")
      public String clearSession(SessionStatus sessionStatus) {
        sessionStatus.setComplete(); // 세션 초기화 범위는 컨트롤러에서 @SessionAttributes로 선언된 세션 속성들에 한정된다.
        return "redirect:/userForm";
      }
    }
    ```
- @SessionAttribute
  - @SessionAttribute는 세션에 저장된 특정 속성을 메서드 파라미터로 가져오기 위해 사용되는 어노테이션이다.
  - 세션에 저장된 속성 값을 컨트롤러의 메서드에서 직접 접근할 수 있도록 해주며 전역적으로 관리되는 세션 속성에 접근할 때 유용하게 사용할 수 있다.
  - required = true(기본값)로 설정하면 해당 속성이 세션에 반드시 있어야 하며 없으면 예외가 발생한다.
  - 사용 예시
    - ```
      @GetMapping("/getUser")
      public String getUser(@SessionAttribute(name = "user", required = false) User user) {
        // ...
      }
      ```

### RedirectAttributes & Flash Attributes
- 개요
  - 리다이렉트를 사용하여 다른 URL로 이동시키는 동시에 데이터를 전달해야 하는 상황에 사용할 수 있다.
  - URL에 포함하거나 세션을 이용해서 데이터를 전달할 수 있지만, 실용적이지 못하다.
- RedirectAttributes와 Flash Attributes의 등장
  - 위와 같은 상황을 위하여 등장한 기술.
  - RedirectAttributes는 리다이렉트 요청 시 데이터를 안전하고 효율적으로 전달할 수 있도록 돕는 인터페이스로서, 리다이렉트에서 필요한 데이터를 URL에 포함할 수 있으며 Flash Attributes를 통해 URL에 표시되지 않도록 임시 데이터를 세션을 통해 전달할 수 있다.
    - 실제 세션을 사용해서 구현하면 세션 데이터가 방대해지며 이를 해결하기 위해서는 개발자가 세션을 모두 관리해야하는데, `RedirectAttributes & Flash Attributes`을 사용한다면 쉽게 해결할 수 있게 되는 것이다.

### 검증 (Validation)
- 기존의 Java 검증 방식
  - 전통적인 Java에서는 데이터를 검증하기 위해 보통 조건문(if-else)과 예외(Exception)를 사용하여 각 필드에 대해 수동으로 검증 로직을 작성해야했다.
  - 복잡한 객체나 컬렉션의 검증을 위해서는 로직이 반복적으로 중첩되거나 별도의 검증 메서드를 생성해야 한다.
  - 이러한 방식은 검증 로직의 일관성이 부족하고 코드의 양이 많아 유지보수성이 떨어진다.
- 스프링 검증 방식
  - Spring 은 다양한 방법과 도구를 통해 클라이언트로부터 입력된 데이터를 유효성 검증하고 데이터 무결성을 보장하고 있으며 어노테이션 기반 검증부터 커스텀 검증 구현까지 유연하고 강력한 검증 기능을 제공한다.
  - 검증을 위한 도구로서 BindingResult, Errors, FieldError, ObjectError, MessageCodesResolver 등의 클래스를 제공하고 있다.
- 스프링 검증 방식의 종류
  - 폼 검증 (Form Validation)
    - @ModelAttribute 로 폼 객체를 바인딩하고 해당 객체의 유효성을 검사하며 검증 오류가 발생하면 BindingResult 객체에 오류 정보가 저장되며 뷰에 오류 메시지를 전달한다.
    - 스프링의 메시지 소스(MessageSource)를 활용하여 다국어 지원이나 커스텀 오류 메시지를 쉽게 관리할 수 있다.
  - Validator 인터페이스를 이용한 검증
    - Validator 인터페이스를 구현하여 커스텀 검증 로직을 작성할 수 있으며 이 방법은 어노테이션 기반 검증만으로는 처리할 수 없는 복잡한 검증 로직이 필요할 때 유용하다.
    - 검증 로직을 별도의 클래스로 분리하여 코드의 재사용성과 확장성을 높일 수 있다.
  - Bean Validation
    - 객체의 필드에 어노테이션을 적용하여 유효성을 검사한다.
    - 스프링에서는 컨트롤러에서 @Valid 및 @Validated 어노테이션을 사용해 자동으로 검증을 수행할 수 있다.
  - 커스텀 검증 어노테이션 (Custom Validation Annotations)
    - 스프링은 기본 제공 어노테이션 외에도 커스텀 검증 어노테이션을 구현할 수 있는 기능을 제공하며, ConstraintValidator 인터페이스를 구현하여 적용할 수 있다.

### BindingResult
- 스프링의 검증
  - 스프링의 검증은 데이터 바인딩 과정과 밀접하게 연관되어 있다.
  - 데이터 바인딩은 요청 데이터를 객체로 변환하는 과정인데, 이 과정에서 데이터를 검증함으로써 애플리케이션의 안정성과 데이터 무결성을 보장하게 된다.
  - 스프링에서는 크게 두 가지로 구분해서 검증이 이루어진다.
    - 스프링은 데이터 바인딩 시 검증 로직을 자동으로 실행하도록 설계되었으며 BindingResult 통해 오류 정보 및 검증 결과를 저장하고 관리한다.
    - 컨트롤러에서 사용자가 직접 BindingResult 를 통해 오류 데이터를 추가하고 검증을 진행할 수 있다.
- Errors / BindingResult 구조
  - Errors
    - 검증 과정에서 기본적인 오류를 추가하고 확인하는 인터페이스이다.
  - BindingResult
    - Errors 인터페이스를 상속받은 인터페이스이다.
    - 컨트롤러에서 데이터 바인딩과 검증을 동시에 처리해야 하는 상황에서 주로 사용된다.
    - 메시지 코드 해석과 세부적인 오류 관리 기능 등 보다 정교하고 확장된 기능을 제공한다.
- BindingResult 기본 전략
  - 스프링의 BindingResult 는 세 가지 기본 전략을 가진다.
    - 스프링은 데이터 바인딩 시 발생하는 모든 오류 정보를 자동으로 BindingResult 의 errors 속성에 저장 한다.
    - 사용자가 BindingResult 의 오류 정보를 활용하기 위해서는 컨트롤러 메서드 매개변수로 지정 해야 한다.
      - Ex. public String method(@ModelAttribute User user, BindingResult bindingResult)
        - 매개변수로 지정 시 BindingResult 는 @ModelAttribute 객체 바로 뒤에 위치해야 한다.
    - BindingResult API 를 사용해서 추가적인 검증을 진행하거나 검증 결과를 클라이언트에게 전달할 수 있다.
- BindingResult 선언 여부에 따른 동작 방식
  - BindingResult를 메서드에 선언하지 않는 경우
    - 스프링은 MethodArgumentNotValidException 예외를 발생시키고 요청한 컨트롤러는 실행되지 않는다. 
  - BindingResult를 메서드에 선언한 경우
    - MethodArgumentNotValidException 예외를 건너뛰고 컨트롤러 메서드가 호출된다.
  - 정리
    - 스프링은 BindingResult의 메서드 선언 여부에 따라 요청을 계속 진행시킬지 아니면 MethodArgumentNotValidException 예외로 요청을 중단할지 결정한다.
- 객체 오류(글로벌 오류) 와 필드 오류
  - 스프링은 오류를 추가할 때 객체 오류(= 글로벌 오류)와 필드 오류로 구분하도록 API 를 설계했다.
  - 객체 오류라는 것은 말 그대로 객체 수준에서 오류를 표현한다는 의미이고, 필드 오류라는 것은 객체 보다 좀 더 구체적인 필드 수준에서 오류를 표현한다는 의미이다.
  - 필드 수준 오류
    - 구체적으로 어떤 객체의 어떤 필드에서 오류가 났는지를 표현한다.
    - FieldError를 사용한다.
      - FieldError(String objectName, String field, Object rejectedValue, boolean bindingFailure, String[] codes, Object[] arguments, String defaultMessage)
        - objectName
          - 오류가 발생한 객체 이름
        - field
          - 오류가 발생한 필드 이름
        - rejectedValue
          - 클라이언트가 입력한 잘못된 값
          - 오류가 발생하면 클라이언트가 입력한 값이 다 사라지는데, FieldError 객체의 rejectedValue 속성을 활용하면 이 문제를 해결할 수 있다.
        - bindingFailure
          - 데이터 바인딩 실패 여부 (true면 바인딩 실패)
          - 스프링에서 바인딩 하다가 발생한 오류인지 아닌지를 구분할 수 있다.
        - codes
          - 오류 코드 목록
          - 메시지 소스에서 사용
        - arguments
          - 메시지에 사용될 인자 목록
        - defaultMessage
          - 기본 오류 메시지
  - 객체 수준 오류
    - 필드가 아닌 객체 혹은 전역 수준에서의 오류 사항을 표현한다.
    - ObjectError를 사용한다.
- MessageSource 연동
  - BindingResult의 유효성 검증 오류가 발생했을 때, MessageSource를 사용해서 해당 오류메시지를 사용자에게 제공할 수 있다.
  - 사용 예시
    - 오류 메시지 직접 입력
      - bindingResult.addError(new FieldError("order", "productName", "상품명은 필수입니다.");
    - message properties 사용
      - Ex 1. bindingResult.addError(new FieldError("order", “item", null, false, new String[]{"required.order.item"}, null, null));
        - required.order.item=상품명은 필수입니다
      - Ex 2. bindingResult.addError(new FieldError("order", "price", order.getPrice(), false, new String[]{"range.order.price"}, new Object[]{100, 10000}, "가격은 100 이상 10000 이하여야 합니다."));
        - range.order.price=가격은 {0} 이상 {1} 이하여야 합니다.
  - reject() / rejectValue()를 사용하면, 조금 더 간편하게 조작할 수 있다.
    - Ex 1. bindingResult.rejectValue("price", "range", new Object[]{100, 10000}, "가격은 100 이상 10000 이하여야 합니다.");
      - range.order.price=가격은 {0} 이상 {1} 이하여야 합니다.
      rejectValue에 설정한 오류 코드 'range'와 메시지 파일에 입력한 오류 코드 'range.order.price' 의 값이 서로 일치하지 않는데, 정상동작 하는 이유는 MessageCodesResolver 덕분이다.
        - MessageCodesResolver 오류 메시지 전략은 기록 생략.

### Validator
- Validator란?
  - Spring 의 Validator 는 객체의 유효성을 검증하기 위해 설계된 인터페이스로 데이터 유효성 검증을 단순화하면서 비즈니스 로직과 검증 로직을 분리하는 데 사용된다.
- 구조
  - supports()
    - 해당 Validator가 특정 객체 타입을 지원하는지 확인하는 메서드이다.
  - validate()
    - 주어진 대상 객체가 supports(Class) 메서드에서 true를 반환하는 클래스여야만 검증할 수 있다.
    - 실제 유효성 검사를 수행하는 메서드이며, 유효성 검사에 실패한 경우 Errors 객체를 사용하여 오류를 추가한다.
- 사용이점
  - 검증 로직과 비즈니스 로직을 완벽하게 분리할 수 있다.
    - 사용 전
      - ```
        @PostMapping("/order")
        public String submitOrder(@ModelAttribute("order") Order order, BindingResult bindingResult) {
          if (!StringUtils.hasText(order.getProductName())) {
            bindingResult.addError(new FieldError("order", “item", null, false, new String[]{"required.order.item"}, null, null));
          }
          if (... 다양한 검증 로직 ...) {
          }
        
          if (bindingResult.hasErrors()) {
            // ...
          }
        
          // 비즈니스 로직
        }
        ```
    - 사용 후
      - ```
        @PostMapping("/order")
        public String submitOrder(@ModelAttribute("order") Order order, BindingResult bindingResult) {
          orderValidator.validate(order, result); // validate에서 검증로직은 수행한다.
        
          if (bindingResult.hasErrors()) {
            // ...
          }
          
          // 비즈니스 로직
        }
        ```

### Bean Validation
- Bean Validation이란?
  - Bean Validation은 Java 애플리케이션에서 객체의 유효성 검증을 위해 도입된 기술로서, 데이터 검증 로직을 일관되게 적용할 수 있도록 하는 표준화 된 API를 제공한다.
- Spring 폼 검증과 Bean Validation
  - Spring 폼 검증
    - 개발자가 직접 검증 로직을 작성해야 하며, 각각의 필드에 대한 조건을 수동으로 명시해야한다.
    - 검증 중 발생한 오류는 Errors 객체에 기록되며 사용자는 어떤 필드에서 어떤 오류가 발생했는지 확인할 수 있다.
    - 검증 조건이 복잡하거나 커스텀 검증이 필요할 때 유용하다.
    - Ex.
      - ```
        if (user.getUsername() == null) {
          errors.rejectValue("username", "required ");
        }
        if (user.getAge() <= 0 || user.getAge() > 120) {
          errors.rejectValue("age", “range");
        }
        ```
  - Bean Validation
    - 어노테이션을 사용해 검증 규칙을 선언적으로 정의할 수 있으며 개발자는 별도로 검증 로직을 작성할 필요가 없다.
    - 객체의 필드에 선언된 어노테이션을 기반으로 자동으로 검증이 수행된다.
    - 객체가 중첩된 경우에도 중첩된 객체에 대한 검증을 함께 수행할 수 있다.
    - Ex.
      - ```
        @NotNull(message = "Username is required")
        private String username;
        
        @Range(min = 1, max = 120, "Age must be between 1 and 120")
        private Integer age;
        ```
        
### Bean Validation + Spring
- 개요
  - org.springframework.validation.Validator를 통해 Spring 의 자체 검증 메커니즘과 Java Bean Validation을 통합하고 이를 통해 Bean Validation 표준 검증을 Spring에서 바로 활용할 수 있다.
  - Spring MVC 는 컨트롤러 계층에서 @Valid 또는 @Validated 를 사용하여 자동으로 Bean Validation 을 수행하며 검증 실패 시 발생하는 오류를 BindingResult 를 통해 보관하고 프로그램적으로 처리할 수 있다.
  - Bean Validation 표준의 그룹(Group)화를 지원하여 특정 조건에서만 검증을 수행할 수 있으며, Bean Validation을 확장하여 커스텀 Validator를 생성할 수 있다.
- @Valid와 @Validated
  - @Valid
    - 기본적인 검증 어노테이션으로서 객체의 필드뿐만 아니라 중첩된 객체(nested object)에서도 유효성 검사를 수행할 수 있다.
    - 주로 단순한 유효성 검사를 수행하는데 사용되며 jakarta.validation 패키지에 속해 있다.
    - @RequestBody와 함께 사용할 수 있다.
      - ```
        @PostMapping("/users")
        public String addUser(@Valid @RequestBody User user, BindingResult result, Model model) {
        }
        ```
  - @Validated
    - Spring 프레임워크에서 제공하는 어노테이션으로서 그룹 기반 검증(validation group)을 지원하며 복잡한 검증 요구사항이 있는 경우 유용하다.
      - ```
        public interface Vgroups {
          interface CreateGroup {}
          interface UpdateGroup {}
        }
        
        public class User {
          @NotEmpty(message = "Username is required", groups = VGroups.CreateGroup.class)
          private String username;
          
          @Email(message = "Email should be valid", groups = {VGroups.CreateGroup.class, VGroups.UpdateGroup.class})
          private String email;
        }
        
        @PostMapping("/users")
        public String addUser(@Validated(VGroups.CreateGroup.class) @ModelAttribute User user, BindingResult result, Model model) {
        }
        
        @PutMapping("/users")
        public String modUser(@Validated(VGroups.UpdateGroup.class) @ModelAttribute User user, BindingResult result, Model model) {
        }
        ```

### Return Values
- 스프링에서의 응답
  - 스프링 MVC 에서 컨트롤러 메서드의 반환 방식은 크게 View 와 HTTP 본문 응답으로 나눌 수 있으며, 각 방식은 클라이언트에게 반환하는 응답의 형태를 결정한다.
    - View 렌더링
      - HTML 과 같은 페이지를 클라이언트에게 반환하는 방식으로서 컨트롤러가 뷰 이름을 반환하고 뷰 레이어에서 해당 이름을 해석하여 적절한 HTML을 생성한다.
    -  HTTP 본문 응답
      - JSON, XML 등 데이터 형식으로 응답을 직접 반환하는 방식으로서 REST API 와 같은 데이터 중심의 애플리케이션에서 주로 사용된다.
- HandlerMethodReturnValueHandler
  - 컨트롤러로부터 응답결과를 받아 응답처리를 위한 작업을 담당하는 클래스이다.
  - 다양한 유형의 파라미터 (예: String, View, @ResponseBody 등)를 처리하기 위해 여러 HandlerMethodReturnValueHandler 기본 구현체를 제공한다.
- View 렌더링 반환 타입
  - String 
    - 문자열로 뷰 이름을 반환하면 ViewResolver에 의해 해당 이름에 맞는 뷰가 렌더링 된다.
  - ModelAndView
    - 뷰와 모델 데이터를 함께 담아 반환하는 객체이다.
    - 뷰 이름뿐만 아니라 모델 데이터를 함께 설정하여 전달할 수 있다.
  - View
    - View 인터페이스를 구현한 객체를 직접 반환할 수 있다.
    - 이 경우 ViewResolver 에 의존하지 않고 특정 View 인스턴스를 직접 렌더링 한다.
  - Model 또는 Map
    - 모델 데이터를 반환하면 뷰 이름은 요청 경로에 따라 자동으로 결정된다.
    - Model이나 Map 은 뷰에 전달할 데이터로만 사용된다.
- ModelAndView 클래스
  - 최종적으로 뷰를 렌더링하기 위한 모델과 뷰의 정보를 제공하는 클래스이다.
  - ModelAndView 객체를 직접 반환해도 되고, 뷰 이름이나 뷰 객체를 반환하게 되면 내부적으로 ModelAndView 객체가 생성되어 응답을 구성한다.
- HTTP 본문 응답 반환 타입
  - @ResponseBody
    - 컨트롤러 메서드의 반환 값을 HttpMessageConverter 를 통해 JSON, XML 등으로 변환하여 응답 본문에 직접 작성한다.
  - HttpEntity<T>, ResponseEntity<T>
    - HTTP 응답(헤더와 본문 모두)을 구성할 수 있다. ResponseEntity는 상태 코드, 헤더, 본문을 모두 포함할 수 있어 더 정밀한 응답 구성이 가능하다.
  - Callable<V>, ListenableFuture<V>, CompletableFuture<V>
    - 비동기 작업의 결과로 반환되는 타입을 사용할 수 있다.

### @ResponseBody
- 개요
  - @ResponseBody 는 메서드의 반환 값을 HTTP 응답 본문에 직접 직렬화하여 클라이언트에 전송하며 HttpMessageConverter 를 사용하여 변환이 이루어진다.
  - 일반적으로 컨트롤러는 HTTP 요청을 처리하고 뷰(View)를 반환하는 방식으로 동작하는데, @ResponseBody 를 사용하면 뷰를 반환하는 대신 메서드가 반환하는 객체를 바로 HTTP 응답 본문에 직렬화하여 전송한다.
- @ResponseBody & @RestController
  - ResponseBody 는 메서드뿐만 아니라 클래스 수준에서도 사용될 수 있으며 이와 같은 효과를 가진 것이 바로 @RestController 라 할 수 있다.
  - @RestController는 @Controller 와 @ResponseBody 를 결합한 메타 어노테이션으로서 @RestController 가 선언된 클래스는 모든 메서드에서 반환되는 값이 자동으로 @ResponseBody 처럼 처리가 이루어진다.

### ResponseEntity<T>
- 개요
  - ResponseEntity<T>는 HTTP 응답을 나타내는 클래스로서 주로 응답 상태 코드, 헤더, 본문을 제어하고 반환하는데 사용되며 HttpEntity<T>를 상속하고 있다.
  - ResponseEntity<T>는 @ResponseBody와 비슷하지만 @ResponseBody는 메서드 반환 값을 HTTP 응답 본문으로 기록하는 반면, ResponseEntity는 상태 코드와 헤더 그리고 본문까지 세밀하게 제어할 수 있는 기능을 제공한다.
  - ResponseEntity<T>는 @RestController 나 @ResponseBody 가 없어도 적절한 HTTP 응답을 반환할 수 있다.

### View / ViewResolver
- View
  - 스프링 MVC 에서 View 는 웹 페이지를 사용자에게 보여주는 역할을 한다.
  - View 는 컨트롤러가 처리한 데이터를 사용자에게 보여주는 화면이며 사용자가 볼 수 있는 HTML, JSON 같은 결과물을 만들어주는 역할을 한다.
- ViewResolver
  - ViewResolver는 특정 URL 요청에 따라 어떤 View를 사용할지를 결정하는 역할을 한다. (View는 최종적으로 데이터를 렌더링하여 클라이언트에 반환한다.)
- ViewResolver의 View 결정 기준
  - ContentNegotiatingViewResolver(=ViewResolver의 구현체 중 하나)는 각 ViewResolver 에 의해 생성된 View 객체들을 순회하며 가장 적합한 View 를 결정해서 반환한다.
  - 결정 순서
    1. 클라이언트의 요청 헤더에 포함된 MediaType (Accept 헤더) 목록과 View 의 Content-Type 을 비교해서 서로 호환이 되는 MediaType 이 존재하는지 확인한다
    2. MediaType 이 호환되는 첫 번째 View 가 최종 선택되어 반환되고 적합한 View 가 없으면 다음 View 로 넘어간다. 만약 View 가 없으면 예외가 발생한다
    3. 만약 ThymeleafView 와 InternalResourceView 모두 선택 대상인데 ThymeleafView 가 먼저 선택되면 InternalResourceView 는 호환 여부를 검사하지 않는다

### Interceptor
- 개요
  - 인터셉터(Interceptor)는 핸들러의 실행 전후 또는 뷰 렌더링 이후 특정 로직을 실행할 수 있으며, HandlerInterceptor 인터페이스를 구현하여 사용할 수 있다.
  - 주로 여러 컨트롤러에서 공통으로 사용하는 기능을 구현하거나 재사용성을 높이고자 할 때 사용한다.
- 주요 메서드
  - preHandle
    - 컨트롤러 실행 전에 호출되며, 호출 할 Handler 객체가 인자로 전달된다.
    - Boolean 반환값으로 True를 반환하면 다음 단계로 진행하고,  false 를 반환하면 요청 처리를 즉시 중단한다.
  - postHandle
    - 컨트롤러 실행 후 뷰 렌더링 전에 호출되며, 호출된 Handler 및 ModelAndView 객체가 인자로 전달된다.
  - afterCompletion
    - 뷰 렌더링이 완료된 후 호출되며, 호출된 Handler 및 예외 발생 시 예외타입이 인자로 전달된다.
    - afterCompletion 은 예외가 발생해도 무조건 호출되므로, 반드시 해야 할 공통 작업이 있다면 여기서 수행하도록 한다.
- Interceptor 사용 방법
  - HandlerInterceptor 인터페이스 또는 HandlerInterceptorAdapter 클래스를 상속하여 구현한다.
  - WebMvcConfigurer 를 사용하여 인터셉터를 등록한다.
    - 특정 URL 패턴에만 인터셉터를 적용하거나 제외 할 수 있다.
    - order 속성을 통해 인터셉터의 호출 순서를 지정할 수 있다.
- 다중 인터셉터 실행 호출 순서
  - 가정
    - firstInterceptor와 secondInterceptor가 존재하며, firstInterceptor의 우선순위가 높음.
  - 호출 순서
    - 여러 개의 인터셉터를 등록할 경우 등록된 순서대로 preHandle이 호출되고, 등록된 역순으로 postHandle 및 afterCompletion이 호출된다.
      1. firstInterceptor의 preHandle
      2. SecondHandlerInterceptor의 preHandle
      3. (Controller)
      4. SecondHandlerInterceptor의 postHandle
      5. FirstHandlerInterceptor의 postHandle
      6. (View)
      7. SecondHandlerInterceptor의 afterCompletion
      8. FirstHandlerInterceptor의 afterCompletion

### @ControllerAdvice
- 개요
  - 특정 컨트롤러 또는 전체 컨트롤러에서 발생하는 예외를 전역적으로 처리하거나 컨트롤러와 관련된 공통적인 기능을 구현하는데 사용된다.
  - 클래스 레벨에 선언하며 메서드 레벨에 선언하는 어노테이션(@ExceptionHandler, @ModelAttribute, @InitBinder)과 함께 사용할 수 있다.
- 주요 어노테이션
  - @ExceptionHandler
    - 컨트롤러에서 발생한 예외를 전역적으로 처리할 수 있으며, 적절한 응답을 생성할 수 있다.
    - 메서드 실행 후에 적용된다.
  - @ModelAttribute
    - 컨트롤러의 모든 요청에 공통적으로 필요한 데이터를 추가할 수 있다.
    - 메서드 실행 전에 적용된다.
  - @InitBinder
    - 요청 파라미터를 특정 형식으로 변환하거나 검증 로직을 적용할 수 있다.
    - 메서드 실행 전에 적용된다.
- @ControllerAdvice와 @RestControllerAdvice
  - @ControllerAdvice 
    - 적용대상
      - @Controller
    - 기본 응답 형식
      - View 이름 반환 또는 HTML 렌더링
    - 내부 메타 어노테이션
      - @Component
  - @RestControllerAdvice
    - 적용대상
      - @RestController
    - 기본 응답 형식
      - JSON 또는 XML
    - 내부 메타 어노테이션
      - @ControllerAdvice + @ResponseBody
- 여러 @ControllerAdvice 적용 순서
  - @Order 어노테이션을 사용하여 순서를 지정할 수 있다.
    - ```
      @RestControllerAdvice
      @Order(1) // 우선순위 높음
      public class RestGlobalExceptionHandler {
        // 생략
      }
      
      @ControllerAdvice
      @Order(2) // 우선순위 낮음
      public class GlobalExceptionHandler {
        // 생략
      }
      ```
  - 다중 @ControllerAdvice 가 있을 경우 @Order 숫자가 낮을수록 높은 우선순위를 가진다.

### 예외 처리
- 서블릿에서의 예외처리 방식
  - 클라이언트 요청 처리 중 발생한 예외는 컨트롤러, 필터, 서블릿, DispatcherServlet 등에서 처리되지 않을 경우 상위 계층으로 전파되어 최종 WAS까지 전달된다.
- WAS 표준 오류 정책과 ErrorPage
  - ErrorPage 는 WAS 에서 발생하는 예외나 특정 HTTP 상태 코드에 대해 오류 페이지를 설정하고 렌더링하는 기능을 제공하는 클래스이다.
  - 애플리케이션이 초기화 되면 스프링의 ErrorPage와 WAS의 ErrorPage를 각각 생성하고 기본값들로 채우게 되며, WAS에는 기본 오류 페이지 한 개가 생성된다.
  - 스프링 부트에서는 Java Config 방식 또는 빈으로 만들어 추가할 수 있다.
  - 오류 페이지 기본 이동 위치는 /error 이다.
    - 설정을 통해 /error 이외의 값들을 설정할 수 있다.
      - /error/401 or /error/404 or /error/500 등
- 스프링의 기본 오류 처리
  - BasicErrorController는 Spring Boot 에서 제공하는 기본적인 오류 처리 컨트롤러로, 애플리케이션에서 발생하는 예외 또는 오류를 처리하고 기본적인 오류 페이지 및 JSON 형식의 오류 응답을 반환한다.
  - BasicErrorController는 기본적으로 /error 경로로 요청하는 모든 오류를 처리하고 있으며 이는 WAS 에서 오류 페이지를 요청하는 기본 경로인 /error 와 일치한다.
  - 오류 처리 방식
    - View 방식의 오류 처리
      - ErrorViewResolver는 오류가 발생했을 때 보여줄 화면(오류 페이지)을 찾는 역할을 한다.
      - 기본적으로 /error/ 경로 아래에서 오류 코드(예: 404, 500) 나 오류의 종류에 맞는 템플릿 파일이나 정적 리소스를 찾아서 적절한 화면을 보여주는 역할을 한다.
      - 오류 화면 우선 순위
        1. 뷰 템플릿
           - resources/templates/error/400.html
           - resources/templates/error/4xx.html (400과 2개가 있다고 가정할 때 400 오류가 발생하면 400.html이 호출된다. 구체적일수록 우선순위가 높음.)
        2. 정적 리소스
           - resources/static/error/400.html
           - resources/static/error/4xx.html
        3. 적용 대상이 없을 때
           - resources/templates/error.html
    - Rest API 방식의 오류 처리
      - Spring Boot 는 REST 요청(Accept: application/json)이 발생했을 때, BasicErrorController를 사용해 JSON 형식의 오류 응답을 자동으로 생성해 준다.
      - BasicErrorController 는 기본적인 화면 오류 처리에는 매우 유용하지만 API 오류 처리를 위한 세밀한 요구사항을 충족하는 데는 한계가 있다.
        - 이를 보완하기 위하여 @ExceptionHandler를 사용할 수 있다.
- 스프링의 통합 예외 전략
  - ErrorPage & BasicErrorController 한계점
    - WAS 의 ErrorPage 는 주로 정적인 HTML 페이지 또는 JSP로 연결되며 동적인 데이터나 사용자 정의 응답을 제공하기 어렵다.
    - BasicErrorController 는 예외를 전역적으로 처리하지만 특정 컨트롤러나 요청 경로에 따른 세분화된 처리 로직을 구현하기 어렵다.
    - REST API에서 특정 예외(예: 인증 오류, 회원 오류, 주문 오류)에 대해 메시지와 상태 코드를 반환 하려면 개별적인 오류 형태 구현이 필요하다.
  - 더 강력한 스프링 예외 전략 제공
    - 특정 예외마다 다른 처리 로직을 구현할 수 있으며 예외 유형별로 HTTP 상태 코드, 응답 메시지, 추가 데이터 등을 원하는 대로 설정할 수 있다.
    - WAS 의 오류 처리 메커니즘에 의존하지 않고 애플리케이션 코드 내에서 예외를 처리하고 응답을 반환할 수 있다.
    - 스프링 MVC 에서 발생한 예외는 `HandlerExceptionResolver` 클래스가 해결하도록 한다.

### HandlerExceptionResolver
- 개요
  - HandlerExceptionResolver 인터페이스는 요청 처리 중에 발생한 예외를 처리하고 그 결과를 사용자에게 보여줄 수 있는 에러 페이지로 연결해 주는 역할을 한다.
  - 즉 컨트롤러나 핸들러 실행 중에 문제가 생기면 이 문제를 어떻게 해결하고 어떤 에러 화면을 보여줄지를 정해주는 역할을 한다.
- HandlerExceptionResolver의 예외 전략
  - HandlerExceptionResolver 는 RequestMappingHandleAdapter 가 핸들러 실행 후 ModelAndView 객체를 반환하는 것과 동일한 구조를 가지고 있다.
  - 즉 예외 상황에서도 기존의 MVC 처리 흐름을 벗어나지 않고 정상적인 흐름 안에서 예외 처리를 구현할 수 있다.
- HandlerExceptionResolver 기본 구현체들
  - 구현체는 ExceptionHandlerExceptionResolver, ResponseStatusExceptionResolver, DefaultHandlerExceptionResolver, SimpleMappingExceptionResolver 로서 총 4개의 클래스가 제공된다.
    - ResponseStatusExceptionResolver
      - ResponseStatusExceptionResolver 는 예외에 대해 HTTP 상태 코드와 메시지를 매핑하여 클라이언트에게 반환할 수 있도록 설계된 예외 처리 전략이다.
      - 이 구현체는 두 가지 방식으로 예외 및 HTTP 상태 코드를 처리하는데 @ResponseStatus 와 ResponseStatusException 를 사용하여 구현한다.
      - 이 클래스는 예외를 sendError(code, msg) 로 처리하기 때문에 뷰 렌더링 없이 WAS 의 ErrorPage 전략에 의해 예외 처리가 이루어지도록 한다.
    - DefaultHandlerExceptionResolver
      - DefaultHandlerExceptionResolver 는 Spring 의 표준 예외와 HTTP 상태 코드를 자동으로 매핑하여 처리하는 클래스다.
      - 주로 Spring MVC 내부에서 발생하는 예외들을 처리하며 특정 예외를 HTTP 상태 코드에 매핑시켜 클라이언트로 반환하는 역할을 한다.
      - 이 클래스는 예외를 sendError(code, msg) 로 처리하기 때문에 뷰 렌더링 없이 WAS 의 ErrorPage 전략에 의해 예외 처리가 이루어지도록 한다.
    - SimpleMappingExceptionResolver
      - SimpleMappingExceptionResolver 는 특정 예외와 View 이름을 매핑하여 예외 발생 시 지정된 뷰(View)로 전환해 주는 클래스로서 애플리케이션 전역적으로 작동하며 모든 컨트롤러에 동일한 예외 처리 로직을 적용할 수 있다.
      - REST API 보다는 주로 HTML 기반의 전통적인 웹 애플리케이션에서 사용하기 적합하다.
    - ExceptionHandlerExceptionResolver
      - 가장 많이 사용되어 별도로 요약.

### ExceptionHandlerExceptionResolver
- 개요
  - ExceptionHandlerExceptionResolver 는 Spring MVC 의 예외 처리 메커니즘 중 가장 널리 사용되는 구현체로 컨트롤러 내부 또는 전역에서 @ExceptionHandler 로 정의된 메서드를 호출하여 예외를 처리한다.
  - REST API 에서는 요청 데이터나 비즈니스 로직에 따라 오류 정보를 세밀하게 제어해야 할 경우가 많은데 이런 동적이고 유연한 예외 처리가 가능하다.
  - 특정 컨트롤러와 밀접하게 연결된 예외 처리 뿐 아니라 @ControllerAdvice 를 사용하면 모든 컨트롤러에서 공통적인 예외 처리 로직을 적용할 수 있다.
- @ExceptionHandler
  - @ExceptionHandler 는 컨트롤러에 특정 예외를 처리하기 위한 메서드를 정의할 때 사용하는 어노테이션이다.
  - ExceptionHandlerExceptionResolver 를 통해 실행되며, 컨트롤러 클래스에서만 작동하거나 @ControllerAdvice 와 함께 사용하여 애플리케이션 전역적으로 동작하도록 설정할 수도 있다.
- 특징
  - 우선 순위에 따른 예외 처리
    - 예외가 발생했을 때 자식 클래스 예외 처리 메서드는 항상 상위 클래스 예외 처리 메서드보다 우선적으로 호출된다.
    - 즉 구체적인 예외 클래스가 선언된 @ExceptionHandler 가 우선적으로 호출되며 덜 구체적인 예외 처리 메서드는 그 다음 순위로 처리된다.
  - 여러 개의 예외를 지정
    - 하나의 @ExceptionHandler 에서 여러 예외를 동시에 처리할 수 있다.
    - ```
      @ExceptionHandler({Exception1.class, Exception2.class, Exception3.class})
      public String handleException (Exception ex) {
        // ...
      }
      ```
  - 예외를 지정하지 않는 경우
    - 파라미터로 전달된 예외와 매핑된다.
    - ```
      @ExceptionHandler
      public String handleIllegalStateException(IllegalStateException ex) { // IllegalStateException 예외가 지정됨
        // ...
      }
      ```
  - HTML 오류 화면 응답
    - return에 명시된 페이지에서 예외화면을 처리할 수 있다.
    - ```
      @ExceptionHandler(IllegalStateException.class)
      public String argumentException(IllegalStateException ex, Model model) {
        model.addAttribute("message", ex.getMessage());
        return "error";
      }
      ```
  - HTTP 본문 응답
    - 리턴타입을 ResponseEntity<ErrorResponse>로 선언하거나 @ResponseBody 어노테이션을 사용하여 본문 응답을 처리할 수 있다.
    - ```
      @ExceptionHandler(CustomException.class)
      // @ResponseBody // ResponseEntity대신 해당 어노테이션 사용 가능
      public ResponseEntity<ErrorResponse> handleException(CustomException ex) {
        ErrorResponse errorResponse = new ErrorResponseException(HttpStatus.BAD_REQUEST, ex);
        return ResponseEntity.status(HttpStatus.BAD_REQUEST).body(errorResponse);
      }
      ```
- ExceptionHandlerExceptionResolver와 @ControllerAdvice
  - @ControllerAdvice 는 여러 컨트롤러에서 발생하는 예외를 전역적으로 처리할 수 있는 어노테이션으로 ExceptionHandlerExceptionResolver 와 결합하여 작동한다.
  - @ControllerAdvice 를 사용하면 애플리케이션의 모든 컨트롤러에서 발생하는 예외를 하나의 클래스에서 통합적으로 처리할 수 있으며 이를 통해 중복 코드를 제거하고 예외 흐름을 컨트롤러로부터 분리할 수 있어 유지보수에도 유리하다.
    - 특정 영역에서만 @ControllerAdvice를 적용할 수도 있다.

### Multipart
- 개요
  - Multipart 는 일반 텍스트 형식이 아니라 하나의 HTTP 요청/응답 바디 내에서 여러 개의 파트를 나누어 전송하는 형식으로서, 파일 업로드나 여러 데이터 파트(텍스트 파트, 바이너리 파트 등)를 함께 전송해야 할 때 주로 사용한다.
  - 웹 브라우저에서 <form> 태그에 enctype="multipart/form-data" 를 지정하고 파일 업로드를 수행하면 ‘multipart/form-data’ 형식의 HTTP 요청이 전송된다.
- MultiPart 지원 도구
  - Spring(특히 Spring Boot 3.x 기준)에서 Multipart(파일 업로드)를 처리하기 위한 도구로서 MultipartResolver, MultipartFile, MultipartHttpServletRequest 그리고 이를 사용하는 Controller/Service 구조가 유기적으로 연결되어 있다.
    - MultipartAutoConfiguration
      - Spring Boot 에서 multipart/form-data 요청 처리를 자동으로 구성해주는 설정 클래스로서 추가적인 설정 없이도 @RequestParam("file") MultipartFile file 을 사용하면 자동으로 멀티파트 요청을 처리하도록 구성된다.
    - MultipartHttpServletRequest
      - HttpServletRequest를 상속(혹은 래핑)하여 멀티파트 폼 데이터를 처리할 수 있는 추가 메서드를 제공하는 인터페이스로서 기본 구현제로 StandardMultipartHttpServletRequest 클래스가 제공된다.
    - MultipartResolver
      - multipart/form-data 요청을 해석하여 MultipartHttpServletRequest 를 만들어주는 인터페이스로서 기본 구현제로 StandardServletMultipartResolver 가 제공된다.
    - MultipartFile
      - 업로드된 파일을 다루기 위한 인터페이스로서 getName(), getOriginalFilename(), getSize(), transferTo(File dest) 와 같은 API 가 있다.
    - MultipartProperties
      - Spring Boot 에서 멀티파트 설정을 위한 구성 설정 클래스이다.
    - @RequestPart
      - multipart 요청의 특정 파트를 직접 바인딩하기 위한 어노테이션으로서, @RequestParam 보다 좀 더 확장된 기능을 제공한다.
- Multipart Process
  1. MultiPart 요청 체크
     - 사용자가 multipart/form-data 형식으로 파일을 업로드 하면 MultipartResolver 를 통해 'multipart' 형태인지 판단한다.
  2. MultipartResolver 파싱
     - MultipartResolver 가 MultipartHttpServletRequest 를 생성하고 이 클래스는 요청 바디를 분석하여 각 파일 파트(바이너리 데이터)와 일반 Form 필드를 분리하고 파일 파트는 MultipartFile 맵에 저장한다.
  3. ArgumentResolver 요청 처리
     - 각 ArgumentResolver 클래스는 MultipartHttpServletRequest 의 MultipartFile 맵으로부터 MultipartFile 객체를 가져와서 반환한다.
  4. Controller 에서 MultipartFile 접근
     - @RequestParam, @ModelAttribute, @RequestPart 로 컨트롤러 메서드의 파라미터(MultipartFile, List<MultipartFile>)를 선언하고 파일 데이터에 접근 및 업로드 처리한다.

### RestClient
- 개요
  - RestClient는 Spring 6에서 새롭게 도입된 동기식 HTTP 클라이언트로서, 기존의 RestTemplate 을 대체하거나 보완할 수 있는 보다 모던한 API를 제공한다.
  - 내부적으로 다양한 HTTP 클라이언트 라이브러리위에 추상화를 제공하며 개발자가 손쉽게 HTTP 요청과 응답을 다룰 수 있도록 지원한다.
- 특징
  - 메서드 체이닝 방식의 API
    - get(), post(), put() 등 HTTP 메서드를 코드상에서 직관적으로 체이닝할 수 있으며, retrieve(), exchange() 등을 통해 설정 → 요청 → 응답 흐름을 명확히 표현할 수 있다.
  - 동기식 처리
    - 내부 동작이 동기식이므로 블로킹 모델을 따른다.
  - Builder 기반 설정
    - RestClient.builder()에서 baseUrl, 기본 헤더, 인터셉터, requestFactory 등을 간편하게 설정할 수 있으며, 한 번 만들어진 RestClient 는 여러 스레드에서 안전하게 사용할 수 있다.
  - 다양한 HTTP 라이브러리 연동
    - 자동으로 Apache HttpClient, Jetty HttpClient, java.net.http 등을 감지하여 활용하며 직접 requestFactory(…)를 지정하여 원하는 라이브러리를 명시적으로 선택할 수도 있다.
  - 편리한 메시지 변환
    - body(Object), body(ParameterizedTypeReference) 등을 제공해 제네릭 구조를 포함한 다양한 타입 변환을 지원하며 accept(), contentType() 등으로 헤더를 설정할 수 있다.
  - 유연한 오류 처리
    - 4xx, 5xx 상태 코드를 받으면 기본적으로 RestClientException 계열 예외를 던지지만, onStatus()를 사용해 특정 상태 코드에 대한 맞춤 예외 처리가 가능하다.
    - exchange() 메서드를 사용하면 요청과 응답을 더 세밀하게 다루면서 상태 코드별로 직접 처리를 구성할 수 있다.
- Exchange
  - exchange()는 retrieve()와 달리 HTTP 요청(Request)과 응답(Response)을 모두 직접 제어할 수 있게 해 주는 기능으로서, 람다 형태의 콜백 함수를 인자로 받는다.
- 오류처리
  - RestClient 에서 오류 처리는 기본적으로 retrieve() 또는 exchange() 메서드에서 수행할 수 있으며, HTTP 4xx 및 5xx 오류 발생 시 자동으로 예외(RestClientException)를 던진다.
  - 기본 동작을 커스터마이징 하려면 onStatus() 또는 exchange()를 활용하여 오류 상태 코드를 직접 처리해야 한다.