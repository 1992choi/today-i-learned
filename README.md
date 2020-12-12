- - -
# Interview

* [Java](#java)

* [Web](#web)

* [Database](#database)

* [Algorithm][algorithm_link]

[algorithm_link]: https://github.com/19920731/Java/tree/master/src/algorithm

- - -

<br><br><br><br><br><br>



# Java

### Java의 특징
> -객체지향 프로그래밍 언어   
> -운영체제에 상관없이 독립적으로 작동하므로 이식성이 높음   
> -객체지향의 특징인 캡슐화, 상속, 다형성이 잘 적용된 언어   
> -Garbage Collector에 의한 자동 메모리 관리   
> -멀티쓰레드 지원     

### 객체지향 프로그래밍의 특징
> -객체지향 프로그래밍(Object-Oriented Programming, OOP) : 객체를 기반으로 프로그래밍을 하는 패러다임   
> - **캡슐화**   
>   -객체의 변수, 메서드 등 실제 구현 내용을 보이지 않게 감싸는 개념   
> - **추상화**   
>   -사물들의 공통적인 특징을 파악해서 하나의 개념으로 다루는 것   
> - **다형성**   
>   -같은 자료형에 여러 가지 객체를 대입하여 다양한 결과를 얻어내는 성질   
> - **상속성**   
>   -클래스로부터 속성과 메서드를 물려받는 것   

### 객체지향 프로그래밍의 5대 원칙(SOLID)
> - **단일 책임 원칙(Single Responsiblity Principle)**   
>   -소프트웨어의 설계 부품(클래스, 함수 등)은 하나의 책임만 가짐   
>   -응집도는 높고 결합도는 낮음을 뜻함   
>   -클래스의 기능(책임)이 많아지면 내부 함수끼리 강한 결합이 발생할 가능성이 높음   
> - **개방-폐쇄 원칙(Open-Closed Principle)**   
>   -기존의 코드를 변경하지 않고 기능을 수정하거나 추가할 수 있도록 함   
>   -이를 위해 인터페이스를 사용   
> - **리스코프 치환 원칙(Liskov Substitution Principle)**   
>   -자식 클래스는 부모 클래스에서 가능한 행위를 수행할 수 있어야 함   
> - **인터페이스 분리 원칙(Interface Segregation Principle)**   
>   -자신이 사용하지 않는 기능(인터페이스)에는 영향을 받지않아야 함   
> - **의존 역적 원칙(Dependency Inversion Principle)**   
>   -의존 관계를 맺을 때, 변화하기 쉬운 것 보다는 변화하기 어려운 것에 의존해야한다는 원칙   

### 클래스, 객체, 인스턴스
> - **클래스**   
>   -객체를 만들어 내기 위한 설계도   
>   -연관되어 있는 변수와 메서드의 집합   
> - **객체**   
>   -클래스로 구현한 모든 대상   
>   -클래스의 타입으로 선언되었을 때, 객체라고 말함   
>   -인스턴스의 포괄적 개념      
> - **인스턴스**   
>   -객체가 메모리에 할당되어 실제 사용될 때를 지칭      

### 자바 메모리 구조
> - **메서드 영역**   
>   -자바 프로그램에서 사용되는 클래스에 대한 정보와 클래스 변수(static variable)가 저장되는 영역   
> - **힙 영역**   
>   -자바에서는 new 키워드를 사용하여 인스턴스가 생성되며, 해당 인스턴스의 정보를 힙 영역에 저장   
> - **스택 영역**   
>   -메서드가 호출되면, 메서드의 지역 변수와 매개변수를 스택 영역에 저장   

### 접근 제한자
> - **public**   
>   -모든 접근 허용   
> - **protected**   
>   -동일 패키지 또는 해당 부모 클래스를 상속받은 자식 클래스에서의 접근 허용   
> - **default**   
>   -같은 패키지 내에서 접근 허용   
> - **private**   
>   -같은 클래스 내에서만 접근 허용   

### Java Collection
> - **Set**   
>   -HashSet, TreeSet   
>   -순서를 유지하지 않는 데이터의 집합으로 데이터의 중복을 허용하지 않음   
> - **List**   
>   -LinkedList, Vector, ArrayList   
>   -순서가 있는 데이터의 집합으로 데이터의 중복을 허용함  
> - **Map**   
>   -Hashtable, HashMap, TreeMap   
>   -Key와 Value의 쌍으로 이루어진 데이터 집합으로, 순서는 유지되지 않으며 Key의 중복을 허용하지 않으나 Value의 중복은 허용   

### Call by Value vs Call by Reference   
> - **Call by Value**   
>   -값을 호출하는 것을 의미      
>   -전달받은 값을 복사하여 처리하기 때문에 전달받은 값을 변경하여도 원본은 변경되지 않음    
> - **Call by Reference**   
>   -참조에 의한 호출을 의미   
>   -전달받은 값을 직접 참조하여 전달받은 값을 변경할 경우 원본도 같이 변경됨   

### Overloading vs Overriding
> - **Overloading**   
>   -같은 이름의 메서드를 여러 개 가지면서 매개 변수를 다르게 정의하는 것   
>   -인자의 수나 자료형을 다르게 정의함   
> - **Overriding**      
>   -상속 관계에 있는 클래스 간에 같은 이름의 메서드를 재정의하는 것   

### Abstract Class vs Interface
> - **Abstract Class**   
>   -상속을 통해서 자손 클래스에서 완성하도록 유도하는 클래스   
>   -추상 클래스는 추상 메서드를 가지지 않아도 상관없지만 추상 메서드가 하나라도 있으면 추상 클래스가 되어야 함   
>   -필드, 생성자, 추상 메서드를 가질 수 있음. 생성자를 가지기 때문에 객체화 가능   
>    ```java
>    abstract class AbstractSample {
>        // Field
>        private int num;
>        
>        // Constructor 
>        public AbstractSample(int num) {
>            this.num = num;
>        }
>        
>        // Abstract Method 	
>        public abstract void calc();
>    }
>    ```
> - **Interface**      
>   -상수(static final)와 추상 메서드(abstract method)의 집합   
>   -생성자를 가질 수 없어서 객체화 불가능   
>   -다른 클래스를 작성하는데 도움을 주는 목적   
>   -다중상속 가능   
>   -자바8부터 디폴트 메서드 지원   
>    ```java
>    interface InterfaceSample {
>        public static final int NUM = 10; // public static final 생략 가능. 컴파일 시에 자동 생성
>        public abstract void calc(); // public abstract 생략 가능. 컴파일 시에 자동 생성
>    }
>    ```

### 디자인 패턴
> - **싱글톤 (Signleton)**   
>   -최초 하나의(Single) 인스턴스만을 생성하고, 이후에는 이 인스턴스를 참조    
> - **프로토타입 (Prototype)**      
>   -기존의 인스턴스를 그대로 복제(clone) 하여 새로운 객체를 생성하는 방법   
> - **팩토리 (Factory)**      
>   -인스턴스를 직접 생성해내지 않고, 공장에서 제공하는 메서드를 통해 생성   
> - **빌더 (Builder)**      
>   -복잡한 객체를 생성하는 방법을 정의하는 클래스와 표현하는 방법을 정의하는 클래스를 별도로 분리하여, 서로 다른 표현이라도 이를 생성할 수 있는 동일한 절차를 제공하는 패턴   

### Reflection
> -이미 로딩이 완료된 클래스에서 또 다른 클래스를 동적으로 로딩하여 생성자, 멤버 필드, 멤버 메서드 등을 사용하는 기법   

### 제네릭(Generic)
> -클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법    
> -다양한 타입의 객체들을 다루는 메서드나 컬렉션 클래스에 컴파일 시의 타입체크를 해주는 기능   

### 래퍼 클래스(Wrapper Class)
> -기본 자료타입(primitive type)을 객체로 다루기 위해서 사용하는 클래스   
> - **박싱(Boxing)**   
>   -기본 자료형을 Wrapper 클래스의 객체로 변경하는 과정   
>   -Boxing : Integer age = new Integer(30);   
>   -AutoBoxing : Integer age = 30;
> - **언박싱(UnBoxing)**      
>   -각각의 객체를 기본 자료형으로 변경하여 사용하는 과정   
>   -UnBoxing : int age = age.intValue();  
>   -AutoUnBoxing : Integer obj = new Integer(30); int age = obj;  

### Reactive Programing
> -데이터의 흐름과 전달에 관한 프로그래밍 패러다임   
> -리액티브 프로그램은 주변의 환경과 끊임없이 상호작용을 하는데 프로그램이 주도하는 것이 아니라 환경이 변하면 이벤트를 받아 동작   

### 직렬화(Serialize)와 역직렬화(Deserialize)
> - **직렬화(Serialize)**   
>   -자바 시스템 내부에서 사용되는 Object 또는 Data를 외부의 자바 시스템에서도 사용할 수 있도록 byte 형태로 데이터를 변환하는 기술      
>   -JVM(Java Virtual Machine 이하 JVM)의 메모리에 상주(힙 또는 스택)되어 있는 객체 데이터를 바이트 형태로 변환하는 기술   
> - **역직렬화(Deserialize)**      
>   -byte로 변환된 Data를 원래대로 Object나 Data로 변환하는 기술     
>   -직렬화된 바이트 형태의 데이터를 객체로 변환해서 JVM으로 상주시키는 형태    

### JDBC(Java Data Base Connection)
> -JAVA언어를 통하여 데이터베이스에 접근할 수 있는 프로그래밍을 의미   

### JVM
> -java 파일을 컴파일한 결과물(.class)을 실행시키는 프로그램   
> -메모리관리 및 Garbage Collection 수행   
> -Stack 기반의 가상머신   

### Garbage Collection
> -메모리 관리 기법 중의 하나로, 프로그램이 동적으로 할당했던 메모리 영역 중에서 필요없게 된 영역을 해제하는 기능   

### Thread
> - **프로세스(Process)와 쓰레드(Thread)**   
>   -프로세스란 실행 중인 프로그램을 지칭   
>   -쓰레드란 프로세스 내에서 동시에 실행되는 독립적인 실행단위   
> - **쓰레드의 장점**   
>   -시스템 처리량 증가(Context Switching이 빠름)   
>    &nbsp;&nbsp;*Context Switching : 동작 중인 프로세스가 대기하면서 해당 프로세스의 상태를 보관하고, 대기하고 있던 다음 순번의 프로세스가 동작하면서 이전에 보관했던 프로세스 상태를 복구하는 과정*   
>   -프로세스 내의 Stack영역을 제외한 모든 메모리를 공유하기 때문에 통신 부담이 적어 프로그램 응답 시간이 단축됨
> - **Thread 클래스와 Runnable 인터페이스**   
>    ```java
>    // 1. Thread 클래스를 상속받아 구현       
>    static class MyThread1 extends Thread {
>        // Thread 클래스의 run()을 오버라이딩
>        public void run() {
>            for (int i = 0; i < 10; i++) {
>                try {
>                    Thread.sleep(1000);
>                } catch (InterruptedException e) {
>                    // ingore
>                }
>	        	
>                System.out.println("MyThread1 run : " + i);
>            }
>        }
>    }
>
>    // 2. Runnable 인터페이스를 구현
>    static class MyThread2 implements Runnable {
>        // Runnable 인터페이스의 run()을 구현
>        public void run() {
>            for (int i = 0; i < 10; i++) {
>                try {
>                    Thread.sleep(1000);
>                } catch (InterruptedException e) {
>                    // ingore
>                }
>	    		
>                System.out.println("MyThread2 run : " + i);
>            }
>        }
>    }
>	 
>    public static void main(String[] args) {
>        MyThread1 t1 = new MyThread1();
>        Thread t2 = new Thread(new MyThread2());
>		
>        t1.start();
>        t2.start();
>    }
>    ```



<br><br><br>
- - -
<br><br><br>



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
> -HTTP의 비연결성(Connectionless)과 무상태(Stateless)이라는 특징을 보완하기 위해서 사용   
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
> <img src="https://github.com/19920731/Interview/blob/main/images/SpringMVC.jpg"  width="600" height="350" /><br>
> 1. 요청된 URL을 dispatcher-servlet으로 전달   
> 2. 핸들러 매핑은 해당 URL에 매핑된 컨트롤러가 있는지 검사 후 컨트롤러에 전달   
> 3. 해당 컨트롤러가 로직을 처리   
> 4. ModelAndView 객체 생성 후, 로직의 결과를 담아서 dispatcher-servlet에 전달   
> 5. dispatcher-servlet은 전달 받은 뷰가 있는지 검사하기 위해 ViewResolver로 보냄   
> 6. ViewResolver는 받은 뷰가 있는지 검사 후 뷰로 보냄   
> 7. 모델과 같이 뷰를 그린 후에 dispatch-servlet으로 보냄   
> 8. 최종적으로 컨텐츠를 클라이언트에게 전달    

### POJO(Plain Old Java Object)
> -객체지향 원리에 충실하면서, 특정 환경이나 규약에 종속되지 않는 방식으로 설계된 객체   

### IoC(Inversion of Control)
> -객체에 대한 제어권이 개발자가 아닌 스프링 컨테이너에게 있는 것   
> -객체의 생성부터 소멸까지의 라이프 사이클을 컨테이너가 관리   

### DI(Dependency Injection)
> -각 객체 간의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해주는 것   

### AOP(Aspect-Oriented Programming)
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

### JSP vs Servlet
> - **JSP**   
>   -html 내에 자바코드를 블록화하여 삽입한 것      
>   -JAVA in Html   
> - **Servlet**   
>   -Container가 이해할 수 있도록 구성된 자바코드로 이루어진 것   
>   -Html in JAVA   

### Framework vs Library
> - **Framework**   
>   -뼈대가 되는 부분을 미리 구현한 클래스, 인터페이스, 메서드 등의 모음     
> - **Library**   
>   -자주 쓰일 만한 기능들을 따로 구현하여 모아 놓은 클래스의 집합    

### Spring Filter vs Interceptor  
> - **Filter**   
>   -DispatcherServlet 이전에 실행   
>   -보통 web.xml에 등록   
>   -일반적으로 인코딩 변환 처리, XSS방어 등의 요청에 대한 처리로 사용   
> - **Interceptor**   
>   -Dispatcher servlet에서 Handler(Controller)로 가기 전에 정보를 처리   
>   -로그인 체크, 권한체크, 프로그램 실행시간 계산작업 로그확인 등에 대한 처리로 사용   

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

### REST(Representational State Transfer)
> -자원을 이름(자원의 표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미   
> -HTTP URI를 통해 자원을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD 수행   



<br><br><br>
- - -
<br><br><br>



# Database

### 데이터베이스 언어
> - **DDL(Data Definition Language)**  
>   -데이터베이스 구조를 정의,수정,삭제하는 언어  
>   -CREATE, ALTER, DROP   
> - **DML(Data Manipulation Language)**   
>   -데이터베이스 내의 자료 검색, 삽입, 갱신, 삭제를 위한 언어   
>   -SELECT, INSERT, UPDATE, DELETE   
> - **DCL(Data Control Language)**   
>   -데이터에 대해 무결성 유지, 병행 수행 제어, 보호와 관리를 위한 언어   
>   -COMMIT, ROLLBACK, GRANT, REVOKE   

### Key
> -데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 유일한 기준이 되는 속성   
> - **후보키(Candidate Key)**  
>   -튜플을 유일하게 식별하기 위해 사용하는 속성들의 부분 집합     
>   -유일성(Key로 하나의 튜플을 유일하게 식별)을 만족해야함   
>   -최소성(꼭 필요한 속성으로만 구성)을 만족해야함   
> - **기본키(Primary Key)**   
>   -후보키 중에서 선택한 메인 키     
>   -Null 값을 가질 수 없음   
>   -동일한 값이 중복되어 저장될 수 없음   
> - **대체키(Alternate Key)**   
>   -후보키가 둘 이상일 때 기본키를 제외한 나머지 후보키   
> - **슈퍼키(Super Key)**   
>   -한 릴레이션 내에 있는 속성들의 집합으로 구성된 키   
>   -유일성은 만족하지만, 최소성은 만족하지 못함   
> - **외래키(Foreign Key)**   
>   -관계(Relation)를 맺고 있는 릴레이션 R1, R2에서 릴레이션 R1이 참조하고 있는 릴레이션 R2의 기본키와 같은 R1 릴레이션의 속성   
>   -릴레이션 간에 참조 관계를 표현하는데 중요한 도구   

### 이상(Anomaly)
> -릴레이션에서 일부 속성들의 종속이나 데이터의 중복으로 인해 데이터 조작시 불일치가 발생하는 것   
> -이상 현상은 정규화(Normalization)을 통해 방지할 수 있음   
> - **삽입 이상(Insertion Anomaly)**   
>   -불필요한 정보를 함께 저장하지 않고서는 어떤 정보를 저장하는 것이 불가능한 현상   
> - **갱신 이상(Update Anomaly)**   
>   -데이터 일부만 변경되어, 데이터가 불일치하는 현상   
> - **삭제 이상(Deletion Anomaly)**   
>   -튜플 삭제로 인하여 꼭 필요한 데이터까지 함께 삭제되는 문제   

### 정규화
> -관계형 데이터베이스의 설계에서 중복을 최소화하게 데이터를 구조화하는 프로세스   
> -삽입, 삭제, 갱신 이상이 있는 관계를 재구성함으로써 바람직한 스키마를 만들기 위함   
> - **1NF**   
>   -도메인 원자값      
> - **2NF**   
>   -부분 함수 종속성 제거   
> - **3NF**  
>   -이행 함수 종속성 제거   
> - **BCNF**   
>   -결정자이면서 후보키가 아닌 것 제거   

### JOIN
> -두 개 이상의 테이블이나 데이터베이스를 연결하여 데이터를 검색하는 행위   
> -일반적으로 Primary key 혹은 Foreign key로 두 테이블을 연결   
> -연결하려면 적어도 하나의 칼럼은 서로 공유되고 있어야함   
> - **INNER JOIN**   
>   -기존테이블과 조인한 테이블의 중복값을 보여주는데 결과값은 교집합만 검색        
> - **LEFT / RIGHT OUTER JOIN**   
>   -기존 테이블 값 + 교집합   
> - **FULL OUTER JOIN**  
>   -합집합      
> - **CROSS JOIN**   
>   -모든 경우의 수 (N * M)    
> - **SELF JOIN**   
>   -하나의 테이블을 여러번 복사해서 조인   

### Index
> -데이터베이스 분야에 있어서 테이블에 대한 동작의 속도를 높여주는 자료 구조      
> -테이블 내의 1개의 컬럼, 혹은 여러 개의 컬럼을 이용하여 생성할 수 있음   
> -고속의 검색 동작뿐만 아니라 레코드 접근과 관련 효율적인 순서 매김 동작에 대한 기초를 제공   

### Transaction
> -데이터베이스의 상태를 변화시키기 해서 수행하는 작업의 단위   
> - **원자성(Atomicity)**   
>   -트랜잭션이 데이터베이스에 모두 반영되던가, 아니면 전혀 반영되지 않아야 한다는 것        
> - **일관성(Consistency)**   
>   -트랜잭션의 작업 처리 결과가 항상 일관성이 있어야 한다는 것      
> - **독립성(Isolation)**  
>   -각각의 트랜잭션은 서로 간섭없이 독립적으로 수행되어야 함           
> - **지속성(Durability)**   
>   -트랜잭션이 성공적으로 완료됬었을 경우, 결과는 영구적으로 반영되어야 함   

### SQL vs NoSQL
> - **SQL**   
>   -관계형 데이터베이스      
>   -데이터는 정해진 스키마에 따라 테이블에 저장됨   
> - **NoSQL**   
>   -비관계형 데이터베이스   
>   -반정형화, 비정형화된 데이터에 적합   
>   -대용량의 데이터 저장에 유리   

### Sharding
> -같은 테이블 스키마를 가진 데이터를 다수의 데이터베이스에 분산하여 저장하는 방법   


