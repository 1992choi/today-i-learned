# Web

### GET과 POST
> - **GET**   
>   -서버로부터 정보를 조회하기 위해 설계   
>   -URL뒤에 key=value형태로 전달하는 방식    
>   -길이 제한이 있으므로 전송 데이터에 한계가 있음   
>   -불필요한 요청을 제한하기 위해 요청이 캐시될 수 있음   
> - **POST**   
>   -리소스를 생성/변경하기 위해 설계   
>   -GET과 달리 전송해야될 데이터를 HTTP 메세지의 Body에 담아서 전송   

### Session과 Cookie
> -HTTP의 비연결성(Connectionless)과 비상태성(Stateless)이라는 특징을 보완하기 위해서 사용   
> - **Session**   
>   -저장위치 : 웹 서버   
>   -브라우저를 종료하거나, 서버에서 세션을 삭제했을 때만 삭제가 됨   
>   -각 클라이언트에 고유 session ID를 부여하고, 이 session ID로 클라이언트를 구분   
>   -동작순서   
>      1. 클라이언트가 페이지를 요청   
>      2. 서버는 접근한 클라이언트의 Request-Header 필드인 Cookie를 확인하고, 클라이언트가 해당 session ID를 보냈는지 확인   
>      3. session ID가 존재하지 않는다면, 서버는 session ID를 생성해 클라이언트에게 반환   
>      4. 서버에서 클라이언트로 돌려준 session ID를 쿠키를 사용하여 서버에 저장   
>      5. 클라이언트 접속 시, 세션 쿠키를 이용하여 session ID 값을 서버에 전달   
> - **Cookie**   
>   -저장위치 : 클라이언트(=접속자 PC)      
>   -사용자 인증이 유효한 시간을 명시할 수 있으며, 유효 시간이 정해지면 브라우저가 종료되어도 인증이 유지   
>   -동작순서   
>      1. 클라이언트가 페이지를 요청    
>      2. 웹 서버는 쿠키를 생성하고 정보를 담아 HTTP 화면을 돌려줄 때 같이 클라이언트에게 반환    
>      3. 클라이언트가 이후 서버에 요청할 때 요청과 함께 쿠키를 전송   
>      4. 동일 사이트 재방문 시, 클라이언트의 PC에 해당 쿠키가 있을 경우 요청 페이지와 함께 쿠키를 전송     

### TCP(Transmission Control Protocol) vs UDP(User Datagram Protoco)
> - **TCP**   
>   -연결형 서비스를 제공         
>   -높은 신뢰성을 보장      
>   -3-way handshaking(연결의 설정), 4-way handshaking(연결의 해제)   
> - **UDP**   
>   -비연결형 서비스를 제공            
>   -신뢰성이 낮음      
>   -데이터의 전송 순서를 보장하지 않음
>   -TCP보다 전송속도가 빠름   

### MVC1 vs MVC2
> - **MVC1**   
>   -모든 요청과 응답을 JSP가 담당하는 구조      
>   -JSP페이지 안에서 모든 정보를 표현(View), 저장(Model), 처리(Control)   
>   -쉽게 구현 가능하나 복잡해지면 유지보수 문제 발생   
> - **MVC2**   
>   -클라이언트의 요청을 하나의 Servlet이 받아 알맞게 처리한 후 그 결과를 JSP 페이지로 전달         
>   -클라이언트의 요청, 응답, 비즈니스 로직 처리 부분을 모듈화한 구조   
>   -처리작업의 분리로 유지보수와 확장에 용이, 구조 설계를 위한 시간 필요   

### AJAX
> -JavaScript의 라이브러리중 하나이며 전체 페이지를 새로 고치지 않고도 페이지의 일부만을 위한 데이터를 로드하는 기법  

### Spring Framework
> -자바 엔터프라이즈 개발을 편하게 해주는 경량급 애플리케이션 프레임워크  
> - **경량 컨테이너로서 자바 객체를 직접 관리**   
>   -각각의 객체 생성, 소멸과 같은 라이프 사이클을 관리하며 스프링으로부터 필요한 객체를 얻어올 수 있음      
> - **POJO(Plain Old Java Object)방식의 프레임워크**   
>   -일반적인 J2EE 프레임워크에 비해 구현을 위해 특정한 인터페이스를 구현하거나 상속을 받을 필요가 없어 가벼움      
> - **DI(Dependency Injection) 지원**   
>   -각각의 계층이나 서비스들 간에 의존성이 존재할 경우 프레임워크가 서로 연결시켜줌     
> - **IoC(Inversion of Control) 지원**   
>   -컨트롤의 제어권이 사용자가 아니라 프레임워크에 있으며, Ioc를 통해 기술을 통해 애플리케이션의 느슨한 결합을 도모   
> - **AOP(Aspect-Oriented Programming) 지원**   
>   -트랜잭션이나 로깅, 보안과 같이 여러 모듈에서 공통적으로 사용하는 기능의 경우 해당 기능을 분리하여 관리   

### Spring 처리 과정
> <img src="https://github.com/19920731/Interview/blob/main/images/SpringMVC.jpg"  width="600" height="350" />   
> 1. 요청된 URL을 dispatcher-servlet으로 전달   
> 2. 핸들러 매핑은 해당 URL에 매핑된 컨트롤러가 있는지 검사 후 컨트롤러에 전달   
> 3. 해당 컨트롤러가 로직을 처리   
> 4. ModelAndView 객체 생성 후, 로직의 결과를 담아서 dispatcher-servlet에 전달   
> 5. dispatcher-servlet은 전달 받은 뷰가 있는지 검사하기 위해 ViewResolver로 보냄   
> 6. ViewResolver는 받은 뷰가 있는지 검사 후 뷰로 보냄   
> 7. 모델과 같이 뷰를 그린 후에 dispatch-servlet으로 보냄   
> 8. 최종적으로 컨텐츠를 클라이언트에게 전달    

### POJO
> -객체지향 원리에 충실하면서, 특정 환경이나 규약에 종속되지 않는 방식으로 설계된 객체   

### IoC
> -객체에 대한 제어권이 개발자가 아닌 스프링 컨테이너에게 있는 것   
> -객체의 생성부터 소멸까지의 라이프 사이클을 컨테이너가 관리   

### DI
> -각 객체 간의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해주는 것   

### AOP
> -관점 지향 프로그래밍(Aspect Oriented Programming)   
> -애플리케이션의 핵심적인 기능과 부가적인 기능을 분리해 Aspect라는 모듈로 만들어 설계하고 개발하는 방법   
> - **Aspect**   
>   -위에서 설명한 흩어진 관심사를 모듈화 한 것   
>   -주로 부가기능을 모듈화함   
> - **Target**   
>   -Aspect를 적용하는 곳   
> - **Advice**   
>   -실질적인 부가기능을 담은 구현체   
> - **JointPoint**   
>   -Advice가 적용될 위치   
>   -GET과 달리 전송해야될 데이터를 HTTP 메세지의 Body에 담아서 전송   
> - **PointCut**   
>   -JointPoint의 상세한 스펙을 정의한 것   
>   -더욱 구체적(특정 메서드의 진입 시점에 호출)으로 Advice가 실행될 지점을 지정   

### 스프링 필터와 인터셉터의 차이
> -Filter는 Dispatcher servlet의 앞단에서 정보를 처리하고, Interceptor는 Dispatcher servlet에서 Handler(Controller)로 가기 전에 정보를 처리   

### 빈 스코프(Bean Scope)
> -스프링이 관리하는 빈이 생성되고, 존재하고, 적용되는 범위   
> - **Singleton**   
>   -스프링 컨테이너 내에 단 하나의 객체만 존재. 컨테이너가 사라질 때 제거   
> - **Prototype**   
>   -모든 요청에 대해 새로운 객체를 생성. 참조가 사라지면 GC(가비지 컬렉터)에 의해 제거   
> - **Request**   
>   -HTTP 요청이 들어올 때마다 생성  
> - **Session**   
>   -HTTP 세션이 만들어질 때마다 생성   

### REST
> -Representational State Transfer : 자원을 이름(자원의 표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미   
> -HTTP URI를 통해 자원을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD 수행   


### 제목
> 내용<br>
>  ```java
> public class Test {
> 
>	  public static void main(String[] args) {
>		    System.out.println("Hello");
>     }
>
> }
> ```

