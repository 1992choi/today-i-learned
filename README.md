- - -
<br><br><br>



# INDEX

* [Java](#java)

* [Web](#web)

* [Database](#database)



<br><br><br>
- - -
<br><br><br>



# Java

### Java의 특징
> \- 객체 지향 언어로써 캡슐화, 상속, 다형성 기능을 완벽하게 지원한다.   
> \- 운영체제에 상관없이 독립적으로 작동하여 이식성이 높다.   
> \- Garbage Collector에 의해 메모리가 관리된다.      
> \- 멀티 스레드를 쉽게 구현할 수 있다.   
> \- 동적 로딩을 지원한다.   

### 객체 지향 프로그래밍의 특징
> \- 객체 지향 프로그래밍(Object-Oriented Programming)이란 프로그래밍에서 필요한 데이터를 추상화시켜 '객체'라는 기본 단위로 정의하고, 이 객체를 주된 관심으로 삼는 프로그래밍 방법론이다.   
> - **캡슐화**   
>   \- 객체의 필드와 메서드를 하나로 묶는 것이며, 이를 통해 정보은닉 효과를 얻을 수 있다.      
> - **추상화**   
>   \- 사물들의 공통적인 특징을 파악해서 하나의 개념으로 다루는 것을 뜻한다.      
> - **다형성**   
>   \- 하나의 타입에 여러 객체를 대입함으로써 다양한 기능을 사용할 수 있도록 해준다.   
> - **상속성**   
>   \- 상위 객체의 필드와 메서드를 하위 객체에게 물려주어 하위 객체에서 사용할 수 있도록 해준다.      

### 객체지향 프로그래밍의 5대 원칙(SOLID)
> - **단일 책임 원칙(Single Responsiblity Principle)**   
>   \- 소프트웨어의 설계 부품(클래스, 함수 등)은 하나의 책임만 가진다.   
>   \- 클래스의 기능(책임)이 많아지면 내부 함수끼리 강한 결합이 발생할 가능성이 높으므로 응집도는 높이고 결합도는 낮춰야 한다.   
> - **개방-폐쇄 원칙(Open-Closed Principle)**   
>   \- 소프트웨어 엔티티(클래스, 모듈, 함수 등)는 확장에 대해서는 열려 있어야 하지만 변경에 대해서는 닫혀 있어야 한다.   
>   \- 이를 위해 인터페이스를 사용하기도 한다.      
> - **리스코프 치환 원칙(Liskov Substitution Principle)**   
>   \- 자식 클래스는 부모 클래스의 기능을 대체해서 수행할 수 있어야 한다.   
>   \- 부모 클래스의 인스턴스 대신에 자식 클래스의 인스터스를 사용해도 문제가 없어야 한다는 것을 의미한다.   
> - **인터페이스 분리 원칙(Interface Segregation Principle)**   
>   \- 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안된다.   
>   \- 큰 덩어리의 인터페이스들을 작은 단위들로 분리시키고, 꼭 필요한 메서드들만 사용하여 내부 의존성 관계를 느슨하게 한다.   
> - **의존 역적 원칙(Dependency Inversion Principle)**   
>   \- 상위 모듈은 하위 모듈에 종속되어서는 안된다.   
>   \- 의존 관계를 맺을 때, 구체적인 클래스보다는 인터페이스나 추상 클래스와 관계를 맺어야 한다.   

### 결합도와 응집도
> - **결합도**   
>   \- 모듈(클래스) 간의 상호 의존 정도로서 결합도가 낮으면 상호 의존성이 줄어들어 객체의 재사용이나 수정, 유지보수가 용이해진다.   
> - **응집도**   
>   \- 하나의 모듈 내부에 존재하는 구성 요소들의 기능적 관련성으로, 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져 재사용이나 기능의 수정, 유지보수가 용이해진다.   

### 클래스, 객체, 인스턴스
> - **클래스**   
>   \- 객체를 만들어 내기 위한 설계도로써 객체의 상태를 나타내는 필드(field)와 객체의 행동을 나타내는 메서드(method)로 구성된다.   
> - **객체**   
>   \- 클래스로 구현할 모든 대상을 뜻한다.     
> - **인스턴스**   
>   \- 객체가 메모리에 할당되어 실제 사용될 때를 지칭한다.      

### JVM(Java Virtual Machine)
> - **JVM이란?**   
>   \- Java로 개발한 프로그램을 컴파일하여 만들어지는 바이트코드를 실행시키기 위한 가상머신이다.   
>   \- Java와 OS사이에서 중개자 역할을 하여, OS의 종류와 무관하게 동일한 동작을 보장한다.   
>   \- 메모리 관리 및 Garbage Collection 수행한다.   
>   \- Stack 기반의 가상머신이다.   
> - **JVM 구성**   
>   \- 클래스 로더(Class Loader)   
>   \- 실행 엔진(Excution Engine)   
>   \- Garbage Collector   
> - **실행과정**   
>      1. 프로그램이 실행되면 JVM은 OS로부터 메모리를 할당 받는다.   
>      2. 컴파일러가 소스코드(.java)를 읽어 바이트코드(.class)로 변환시킨다.   
>      3. 클래스 로더를 통해 class파일들을 JVM에 로딩시킨다.   
>      4. 실행 엔진을 통해 로딩된 class파일들을 해석한다.   
>      5. 해석된 바이트코드는 Runtime Data Areas에 배치된 후 실행된다.   
> <img src="https://github.com/Young-Geun/Interview/blob/main/images/JVM.png"  width="600" height="350" />

### Garbage Collection
> \- 메모리 관리 기법 중의 하나로, 프로그램이 동적으로 할당했던 메모리 영역 중에서 필요없게 된 영역을 해제한다.   
> \- 상세내용 : https://d2.naver.com/helloworld/1329   

### 자바 메모리 구조
> - **메서드 영역**   
>   \- 클래스에 대한 정보와 클래스 변수(static variable)가 저장되는 영역이다.   
> - **힙 영역**   
>   \- new 키워드를 통해 생성된 인스턴스의 정보가 저장되는 영역이다.   
> - **스택 영역**   
>   \- 메서드가 호출되면, 메서드의 지역 변수와 매개변수가 저장되는 영역이다.   

### 접근 제한자
> - **public**   
>   \- 모든 접근을 허용한다.   
> - **protected**   
>   \- 같은 패키지 또는 해당 부모 클래스를 상속 받은 자식 클래스에서의 접근을 허용한다.   
> - **default**   
>   \- 같은 패키지 내에서의 접근을 허용한다.   
> - **private**   
>   \- 같은 클래스 내에서의 접근만 허용한다.<br><br>   
> \* 클래스에서의 접근제한자 사용   
>      \- 클래스에는 'public'과 'default'만 사용할 수 있다.      
>      \- 'default'를 사용할 경우, 다른 패키지에서 클래스를 사용할 수 없다.   

### final
> \- Java에서는 불변성을 확보할 수 있도록 final 키워드를 제공하고 있다.   
> \- final 키워드는 변수(variable), 메서드(method), 클래스(class)에 사용될 수 있다.   
> - **변수에 사용**   
>   \- 변수에 final을 붙이면 이 변수는 수정할 수 없다는 의미를 가진다.   
> - **메서드에 사용**   
>   \- 메서드에 final을 붙이면 override를 제한하게 된다.   
> - **클래스에 사용**   
>   \- final 키워드를 클래스에 붙이면 상속 불가능 클래스가 된다.   

### 컬렉션 프레임워크(Collection Framework)
> \- 다수의 데이터를 처리할 수 있도록 표준화된 방법을 제공하는 클래스의 집합을 의미한다.   
> - **List**   
>   \- 순서가 있는 데이터의 집합으로 데이터의 중복을 허용한다.   
>   \- Vector : ArrayList와 구현 원리와 기능적인 측면에서 동일하며, 동기화를 지원한다.   
>   \- ArrayList : 단방향 포인터 구조로 인덱스로 접근하므로 조회할 때 유리하지만, 데이터의 삽입이나 삭제가 발생할 경우 인덱스를 조정하는 추가 작업이 필요하다.   
>   \- LinkedList : 양방향 포인터 구조로 데이터의 삽입, 삭제에 유리하다.   
> - **Set**   
>   \- 순서를 유지하지 않는 데이터의 집합으로 데이터의 중복을 허용하지 않는다.   
>   \- HashSet : 가장 빠르게 접근할 수 있으나 순서를 보장하지 않는다.   
>   \- TreeSet : 입력한 순서대로 값을 저장하지 않지만, 기본적으로 오름차순으로 정렬한다.   
>   \- LinkedHashSet : 입력한 순서대로 값을 저장한다.   
> - **Map**   
>   \- Key와 Value의 쌍으로 이루어진 데이터 집합으로, 순서는 유지되지 않으며 Key의 중복을 허용하지 않으나 Value의 중복은 허용한다.   
>   \- TreeMap : 데이터를 이진 검색 트리(binary search tree)의 형태로 저장하므로 데이터의 삽입이나 삭제가 빠르다.   
>   \- HashMap : 가장 많이 사용되는 클래스 중 하나이며, 해시 알고리즘(hash algorithm)을 사용하여 검색 속도가 매우 빠르다.      
>   \- Hashtable : HashMap과 다르게 동기화를 보장한다.   

### 스트림 API
> \- 자바8부터 추가된 반복자이며, 컬렉션에 저장된 요소를 하나씩 참조하여 람다식으로 처리할 수 있도록 해주는 기능이다.   
> \- Iterator와 비슷한 역할을 하지만 내부 반복자를 통해 병렬 처리가 가능하다는 장점이 있다.   

### Call by Value vs Call by Reference   
> - **Call by Value**   
>   \- 값에 의한 호출을 의미한다.      
>   \- 전달받은 값을 복사하여 처리하기 때문에 전달받은 값을 변경하여도 원본의 값은 변경되지 않는다.   
> - **Call by Reference**   
>   \- 참조에 의한 호출을 의미한다.   
>   \- 전달받은 값을 직접 참조하기 때문에 전달받은 값을 변경하면 원본도 같이 변경된다.   

### Overloading vs Overriding
> - **Overloading**   
>   \- 매개변수의 개수나 자료형을 다르게하여 같은 이름의 메서드를 사용하는 것을 뜻한다.   
> - **Overriding**      
>   \- 상속 관계에 있는 클래스 간에 같은 이름의 메서드를 재정의하는 것을 뜻한다.   

### Abstract Class vs Interface
> - **Abstract Class**   
>   \- 상속을 통해서 자손 클래스에서 완성하도록 유도하는 클래스이다.   
>   \- 추상 클래스는 추상 메서드를 가지지 않아도 상관없지만 추상 메서드가 하나라도 있으면 추상 클래스가 되어야 한다.   
>   \- 필드, 생성자, 추상 메서드를 가질 수 있으며, 생성자를 가지기 때문에 객체화가 가능하다.   
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
>   \- 구현 객체가 같은 동작을 한다는 것을 보장하기 위한 목적이다.   
>   \- 상수(static final)와 추상 메서드(abstract method)의 집합이다.   
>   \- 생성자를 가질 수 없어서 객체화가 불가능하다.   
>   \- 다중상속이 가능하다.   
>   \- 자바8부터 디폴트 메서드 지원한다.   
>    ```java
>    interface InterfaceSample {
>        public static final int NUM = 10; // public static final 생략 가능. 컴파일 시에 자동 생성
>        public abstract void calc(); // public abstract 생략 가능. 컴파일 시에 자동 생성
>    }
>    ```

### 디자인 패턴
> - **싱글톤 (Signleton)**   
>   \- 최초 하나의(Single) 인스턴스만을 생성하고, 이후에는 이 인스턴스를 참조한다.    
> - **프로토타입 (Prototype)**      
>   \- 기존의 인스턴스를 그대로 복제(clone)하여 새로운 객체를 생성한다.   
> - **팩토리 (Factory)**      
>   \- 인스턴스를 직접 생성해내지 않고, 공장에서 제공하는 메서드를 통해 생성한다.   
> - **빌더 (Builder)**      
>   \- 복잡한 객체에 대하여 생성하는 방법을 정의하는 클래스와 표현하는 방법을 정의하는 클래스를 별도로 분리하여, 서로 다른 표현이라도 이를 생성할 수 있는 동일한 절차를 제공한다.   

### 빌더 패턴(Builder pattern)
> \- 객체를 정의하는 클래스와 표현하는 클래스를 별도로 분리하는 방식이다.   
> - **장점**   
>   \- 필요한 데이터만 설정할 수 있다.   
>   \- 유연성을 확보할 수 있다.   
>   \- 가독성을 높일 수 있다.   
>   \- 변경 가능성을 최소화할 수 있다.   

### 템플릿 메서드 패턴(Template Method pattern)
> \- 동일한 기능은 상위 클래스에서 정의하, 확장/변화가 필요한 부분은 하위 클래스에서 구현하는 패턴이다.   
> \- 즉, 특정 코드를 제외한 전반적인 코드의 형태가 비슷한 메서드의 코드중복을 최소화 할 때 유용하다.   
> - **장점**   
>   \- 중복코드를 줄일 수 있다.   
>   \- 자식 클래스에서는 비즈니스 로직에만 집중할 수 있다(SRP).   
>   \- 새로운 비즈니스 로직이 추가되어도 기존 코드를 수정하지 않아도 된다(OCP).   
> - **단점**   
>   \- 부모 클래스와 자식 클래스가 강하게 연결되어 있다.   
>   \- 자식 클래스는 부모 클래스의 사용하지 않는 메서드도 패턴 구현을 위해 상속 받아야한다.   

### 전략 패턴(Strategy pattern)
> \- 객체의 행위를 바꾸고 싶은 경우, 직접 수정하지 않고 상호 교체가 가능한 '캡슐화된 알고리즘'으로 교체 가능하도록 만드는 패턴이다.   
> - **장점**   
>   \- 중복코드를 줄일 수 있다.   
>   \- 런타임시에 타겟 메서드 변경이 가능하다.   
>   \- 컨텍스트 코드의 변경 없이 새로운 전략을 추가할 수 있다(OCP).   
> - **단점**   
>   \- Strategy들로 생성하는 객체 수가 증가한다.   

### 프록시 패턴(Proxy pattern)
> \- 어떤 객체를 사용하고자 할 때, 객체를 직접적으로 참조하는 것이 아니라, 해당 객체를 대행할 객체를 생성하고 이를 통해 대상 객체에 접근하는 방식의 패턴이다.   
> - **장점**   
>   \- 원래 객체의 접근에 대해 사전처리를 할 수 있다.   
>   \- 실제 객체를 수정하지 않고 추가적인 기능을 삽입할 수 있다.   
> - **단점**   
>   \- 빈번한 객체 생성으로 인하여 성능이 저하될 수 있다.   
>   \- 프록시 내부에서 객체 생성을 위해 스레드가 생성되고, 동기화가 구현되어야 하는 경우 성능이 저하될 수 있다.   
>   \- 로직이 난해해져 가독성이 떨어질 수 있다.   

### 제네릭(Generic)
> \- 클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법이다.    
> \- 다양한 타입의 객체들을 다루는 메서드나 컬렉션 클래스를 컴파일할 시에 타입 체크를 할 수 있다.   

### 래퍼 클래스(Wrapper Class)
> \- 기본 자료타입(primitive type)을 객체로 다루기 위해서 사용하는 클래스이다.   
> - **박싱(Boxing)**   
>   \- 기본 자료형을 Wrapper 클래스의 객체로 변경하는 과정을 뜻한다.   
>   \- Boxing : Integer age = new Integer(30);   
>   \- AutoBoxing : Integer age = 30;
> - **언박싱(UnBoxing)**      
>   \- 각각의 객체를 기본 자료형으로 변경하여 사용하는 과정을 뜻한다.   
>   \- UnBoxing : int age = age.intValue();  
>   \- AutoUnBoxing : Integer obj = new Integer(30); int age = obj;  

### Thread
> - **프로세스(Process)와 스레드(Thread)**   
>   \- 프로세스란 실행 중인 프로그램을 뜻한다.   
>   \- 스레드란 프로세스 내에서 동시에 실행되는 독립적인 실행단위를 뜻한다.   
> - **스레드의 장점**   
>   \- Context Switching이 빠르기 때문에 시스템 처리량이 증가한다.   
>   \- 프로세스 내의 Stack영역을 제외한 모든 메모리를 공유하기 때문에 통신 부담이 적어 프로그램 응답 시간이 단축된다.   
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
>        t2.start(); // 또는 new Thread(new MyThread2()).start();
>    }
>    ```

### JDBC(Java Data Base Connection)
> \- JAVA언어를 통하여 데이터베이스에 접근할 수 있는 프로그래밍을 의미한다.  

### Reactive Programing
> \- 데이터의 흐름과 전달에 관점을 둔 프로그래밍이다.   
> \- 데이터 흐름을 먼저 정의하고 데이터가 변경되었을 때 연관되는 함수나 수식이 업데이트 되는 방식의 프로그래밍이다.   

### Reflection
> \- 이미 로딩이 완료된 클래스에서 또 다른 클래스를 동적으로 로딩하여 생성자, 멤버 필드, 멤버 메서드 등을 사용하는 기법이다.  

### 직렬화(Serialize)와 역직렬화(Deserialize)
> - **직렬화(Serialize)**   
>   \- 자바 시스템 내부에서 사용되는 Object 또는 Data를 외부의 자바 시스템에서도 사용할 수 있도록 byte 형태로 데이터를 변환하는 기술을 뜻한다.      
>   \- JVM(Java Virtual Machine 이하 JVM)의 메모리에 상주(힙 또는 스택)되어 있는 객체 데이터를 바이트 형태로 변환한다.   
> - **역직렬화(Deserialize)**      
>   \- byte로 변환된 Data를 원래대로 Object나 Data로 변환하는 기술을 뜻한다.     
>   \- 직렬화된 바이트 형태의 데이터를 객체로 변환해서 JVM으로 상주시킨다.   

### TDD(Test Driven Development)
> \- 테스트 코드를 먼저 작성한 후, 구현 코드 작성 단계와 리팩토링 단계를 짧은 주기로 반복하여 개발하는 '테스트 주도 개발 방법론'이다.   
> \- 기능별로 철저한 모듈화가 이루어져 종속성과 의존성이 낮아 기능이 추가되거나 제거되어도 전체 구조에 영향을 미치지 않게 된다.   
> \- 자동화된 유닛테스팅을 전제로 하므로 특정 버그를 손쉽게 찾아낼 수 있어서 디버깅 시간이 단축된다.   

### Checked Exception VS Unchecked Exception   
> <img src="https://github.com/Young-Geun/Interview/blob/main/images/Types_of_exception.png"  width="600" height="350" />      
>   
> - **Checked Exception**   
>   \- 처리여부 : 반드시 에러를 처리해야한다.   
>   \- 확인시점 : 컴파일 단계   
>   \- 트랜잭션 처리 : ROLLBACK 하지 않는다.   
>   \- 체크예외는 컴파일러가 오류를 체크해주기 때문에 개발자가 예외를 놓치는 실수를 막아준다.   
&nbsp;&nbsp;&nbsp;하지만 이러한 장점 때문에 체크예외를 무분별하게 사용하게 된다면, 예외에 종속된 코드가 될 수 있다는 단점이 존재한다.   
> - **Unchecked Exception**   
>   \- 처리여부 : 명시적인 처리를 강제하지 않는다.   
>   \- 확인시점 : 실행 단계   
>   \- 트랜잭션 처리 : ROLLBACK 한다.   

### Annotation
> - **표준 Annotation**   
>   \- @Override : 컴파일러에게 오버라이딩하는 메서드라는 것을 알린다.   
>   \- @Deprecated : 해당 메서드가 더 이상 사용되지 않음을 표시한다.   
>   \- @SuppressWarnings : 컴파일 경고를 무시하도록 한다.   
>   \- @SafeVarargs : Java7부터 지원하며, 제너릭 같은 가변인자의 매개변수를 사용할 때의 경고를 무시한다.   
>   \- @FunctionalInterface : 함수형 인터페이스라고 정의하는 어노테이션으로, 만약 메서드가 존재하지 않거나 1개 이상의 메서드(default 메서드 제외)가 존재할 경우 컴파일 오류를 발생시킨다.   
> - **메타 Annotation**      
>   \- @Target : 어노테이션이 적용가능한 대상을 지정하는데 사용한다.   
>   \- @Documented : 해당 어노테이션을 Javadoc에 포함시킨다.   
>   \- @Inherited : 어노테이션이 상속되도록 한다.   
>   \- @Retention : 어노테이션이 유지되는 범위를 지정한다.   
>   \- @Repeatable : Java8부터 지원하며, 연속적으로 어노테이션을 선언할 수 있게 해준다.   

<br><br><br>
- - -
<br><br><br>



# Web

### GET과 POST
> - **GET**   
>   \- 서버로부터 정보를 조회하기 위한 목적으로 설계되었다.   
>   \- URL뒤에 key=value 형태로 전달하는 방식이다.    
>   \- 길이 제한이 있어 전송 데이터에 한계가 있다.   
>   \- 불필요한 요청을 줄이기 위하여 요청을 캐시 처리한다.   
> - **POST**   
>   \- 리소스를 생성/변경하기 위한 목적으로 설계되었다.   
>   \- GET과 달리 전송할 데이터를 HTTP 메세지의 Body에 담아서 전송한다.   

### Session과 Cookie
> \- HTTP의 비연결성(Connectionless)과 무상태(Stateless)이라는 특징을 보완하기 위해서 사용한다.   
> - **Session**   
>   \- 저장위치 : 웹 서버   
>   \- 브라우저를 종료하거나, 서버에서 세션을 삭제했을 때 삭제된다.   
>   \- 각 클라이언트에 고유 Session ID를 부여하고, 이 Session ID로 클라이언트를 구분한다.   
>   \- 동작순서   
>      1. 클라이언트가 페이지를 요청한다.   
>      2. 서버는 접근한 클라이언트의 Request-Header 필드인 Cookie를 확인하고, 클라이언트가 해당 Session ID를 보냈는지 확인한다.   
>      3. Session ID가 존재하지 않는다면, 서버는 Session ID를 생성한 후 클라이언트에게 전달한다.   
>      4. 서버에서 클라이언트로 돌려준 Session ID를 쿠키로 사용하여 서버에 저장한다.   
>      5. 클라이언트 접속 시, 세션 쿠키를 이용하여 Session ID 값을 서버에 전달한다.   
> - **Cookie**   
>   \- 저장위치 : 클라이언트(=접속자 PC)      
>   \- 사용자 인증이 유효한 시간을 명시할 수 있으며, 유효 시간이 정해지면 브라우저가 종료되어도 인증이 유지된다.   
>   \- 동작순서   
>      1. 클라이언트가 페이지를 요청한다.    
>      2. 웹 서버는 쿠키를 생성하고 정보를 담은 후 HTTP 화면을 돌려줄 때 같이 클라이언트에게 반환한다.   
>      3. 클라이언트가 이후 서버에 요청할 때 요청과 함께 쿠키를 전송한다.   
>      4. 동일 사이트 재방문 시, 클라이언트의 PC에 해당 쿠키가 있을 경우 요청 페이지와 함께 쿠키를 전송한다.     

### TCP(Transmission Control Protocol) vs UDP(User Datagram Protoco)
> - **TCP**   
>   \- 연결형 서비스를 제공한다.         
>   \- 높은 신뢰성을 보장한다.      
>   \- 3-way handshaking(연결의 설정), 4-way handshaking(연결의 해제)   
> - **UDP**   
>   \- 비연결형 서비스를 제공한다.            
>   \- 신뢰성이 낮다.      
>   \- 데이터의 전송 순서를 보장하지 않는다.   
>   \- TCP보다 전송속도가 빠르다.   

### SSR(Server Side Rendering) vs CSR(Client Side Rendering)
> - **SSR**   
>   \- 서버에서 렌더링 후, Data가 결합된 HTML파일을 클라이언트에 전달하는 방식이다.    
> - **CSR**   
>   \- SSR과 반대로 클라이언트에서 렌더링을 하는 방식이다.    

### SPA(Single Page Application)
>   \- SPA란 서버로부터 새로운 페이지를 불러오지 않고, 현재의 페이지 중 필요한 부분만 동적으로 렌더링하는 방식이다.   
> - **장점**   
>   \- 페이지 로딩속도가 빠르다.   
>   \- 사용자 경험이 우수하다.   
> - **단점**   
>   \- 최초 페이지 로딩속도가 느리다.   
>   \- SEO에 적합하지 않을 수 있다.   

### MVC1 vs MVC2
> - **MVC1**   
>   \- 모든 요청과 응답을 JSP가 담당하는 구조이다.      
>   \- JSP페이지 안에서 모든 정보를 표현(View), 저장(Model), 처리(Control)한다.   
>   \- 쉽게 구현 가능하나 복잡해지면 유지보수 문제가 발생한다.   
> - **MVC2**   
>   \- 클라이언트의 요청을 하나의 Servlet이 받아 알맞게 처리한 후 그 결과를 JSP 페이지로 전달한다.         
>   \- 클라이언트의 요청, 응답, 비즈니스 로직 처리 부분을 모듈화한 구조이다.   
>   \- 처리작업의 분리로 유지보수와 확장에 용이하지만, 구조 설계를 위한 시간 필요하다.   

### AJAX
> \- JavaScript의 라이브러리중 하나이며 전체 페이지를 새로 고치지 않고도 페이지의 일부만을 위한 데이터를 로드하는 기술이다.  

### Spring Framework
> \- 자바 엔터프라이즈 개발을 편하게 해주는 경량급 애플리케이션 프레임워크.  
> - **경량 컨테이너로서 자바 객체를 직접 관리**   
>   \- 각각의 객체 생성, 소멸과 같은 라이프 사이클을 관리하며 스프링으로부터 필요한 객체를 얻어올 수 있다.      
> - **POJO(Plain Old Java Object)방식의 프레임워크**   
>   \- 일반적인 J2EE 프레임워크에 비해 구현을 위해 특정한 인터페이스를 구현하거나 상속을 받을 필요가 없어 가볍다.      
> - **DI(Dependency Injection) 지원**   
>   \- 각각의 계층이나 서비스들 간에 의존성이 존재할 경우 프레임워크가 서로 연결시켜준다.     
> - **IoC(Inversion of Control) 지원**   
>   \- 컨트롤의 제어권이 사용자가 아니라 프레임워크에 있으며, IoC를 통해 애플리케이션의 느슨한 결합을 도모한다.   
> - **AOP(Aspect-Oriented Programming) 지원**   
>   \- 트랜잭션이나 로깅, 보안과 같이 여러 모듈에서 공통적으로 사용하는 기능을 분리하여 관리한다.   

### Spring 처리 과정
> <img src="https://github.com/Young-Geun/Interview/blob/main/images/SpringMVC.jpg"  width="600" height="350" /><br>
> 1. 요청받은 URL을 dispatcher-servlet으로 전달한다.   
> 2. 핸들러 매핑은 해당 URL에 매핑된 컨트롤러가 있는지 검사 후 컨트롤러에 전달한다.   
> 3. 해당 컨트롤러가 로직을 처리한다.   
> 4. ModelAndView 객체 생성 후, 결과를 담아서 dispatcher-servlet에 전달한다.   
> 5. dispatcher-servlet은 전달 받은 뷰가 있는지 검사하기 위해 ViewResolver로 보낸다.   
> 6. ViewResolver는 받은 뷰가 있는지 검사 후 뷰로 보낸다.   
> 7. 모델과 같이 뷰를 그린 후에 dispatch-servlet으로 보낸다.   
> 8. 최종적으로 컨텐츠를 클라이언트에게 전달한다.    

### POJO(Plain Old Java Object)
> \- 객체지향 원리에 충실하면서, 특정 환경이나 규약에 종속되지 않는 방식으로 설계된 객체를 뜻한다.   

### IoC(Inversion of Control)
> \- 객체에 대한 제어권이 개발자가 아닌 스프링 컨테이너에게 있다.   
> \- 객체의 생성부터 소멸까지의 라이프 사이클을 컨테이너가 관리한다.   

### DI(Dependency Injection)
> \- 각 객체 간의 의존관계를 빈 설정 정보를 바탕으로 컨테이너가 자동으로 연결해준다.   

### AOP(Aspect-Oriented Programming)
> \- 애플리케이션의 핵심적인 기능과 부가적인 기능을 분리해 Aspect라는 모듈로 만들어 설계하고 개발하는 프로그래밍 기법이다.   
> - **Aspect**   
>   \- 여러 핵심 기능에 적용될 관심사 모듈.   
>   \- Aspect는 구체적인 기능을 구현한 Advice와 Advice가 어디에서 적용될지를 결정하는 PointCut의 포괄적인 개념이다.   
> - **Advice**   
>   \- 공통 기능을 담고 있는 모듈.   
> - **Target**   
>   \- Aspect를 부여할 대상.   
> - **JointPoint**   
>   \- Advice가 적용될 위치.   
>   \- 애플리케이션의 어떤 지점에 AOP를 사용하여 추가적인 로직을 삽입할 지 정의한다.   
> - **PointCut**   
>   \- 필터링된 JointPoint.   
>   \- 정규표현식을 사용하여 Advice를 적용할 타겟의 메서드를 선별.   

### Spring AOP Advice 종류
> - **@Around**   
>   \- 메서드 호출 전후에 실행된다.   
> - **@Before**   
>   \- JointPoint가 실행되기 이전 시점에 실행된다.   
> - **@AfterRetruning**   
>   \- JointPoint가 정상 완료된 후 실행된다.   
> - **@AfterThrowing**   
>   \- 메서드가 예외를 던지는 경우 실행된다.   
> - **@After**   
>   \- JointPoint의 정상 완료 여부에 상관없이 항상 실행된다.   

### Spring AOP VS AspectJ
> - **Spring AOP**   
>   \- 런타임 위빙(다이나믹 프록시)을 사용한다.   
> - **AspectJ**   
>   \- AspectJ는 위빙 시점에 따라 Compile Time Weaving(CTW), Post Compile Weaving(PCW), Load Time Weaving(LTW) 로 분류된다.   
>   \- Compile Time Weaving(CTW) : AJC(AspectJ Compiler)를 이용해서, 소스 코드가 컴파일할 때 위빙   
>   \- Post Compile Weaving(PCW) : 이미 컴파일된 바이너리 클래스에 위빙   
>   \- Load Time Weaving(LTW) : Class Loader가 클래스를 로딩할 때 위빙   

### PSA(Portable Service Abstraction)
> \- 환경의 변화와 관계없이 일관된 방식의 기술 접근 환경을 제공하려는 추상화 구조를 뜻한다.   
> \- 트랜잭션 처리를 위해 Platform TransactionManager의 구현체들인 JpaTransactionManager, DatasourceTransactionManager, HibernateTransactionManager을 사용하는데 구현체가 바뀌어도 트랜잭션을 처리하는 코드는 변경되지 않는다.   

### JSP vs Servlet
> - **JSP**   
>   \- html 내에 자바코드를 블록화하여 삽입한 것.      
>   \- JAVA in Html.   
> - **Servlet**   
>   \- Container가 이해할 수 있도록 구성된 자바코드로 이루어진 것.   
>   \- Html in JAVA.   

### Framework vs Library
> - **Framework**   
>   \- 뼈대가 되는 부분을 미리 구현한 클래스, 인터페이스, 메서드 등의 집합체이다.     
> - **Library**   
>   \- 자주 쓰일 만한 기능들을 따로 구현하여 모아 놓은 클래스의 집합체이다.    

### Spring Filter vs Interceptor  
> - **Filter**   
>   \- DispatcherServlet 이전에 실행된다.   
>   \- 보통 web.xml에 등록된다.   
>   \- 일반적으로 인코딩 변환 처리, XSS방어 등에 대한 처리로 사용된다.   
> - **Interceptor**   
>   \- Dispatcher servlet에서 Handler(Controller)로 가기 전에 정보를 처리한다.   
>   \- 로그인 체크, 권한 체크, 프로그램 실행시간 계산, 로그 확인 등에 대한 처리로 사용된다.   

### 빈 스코프(Bean Scope)
> \- 스프링이 관리하는 빈이 생성되고, 존재하고, 적용되는 범위를 뜻한다.   
> - **Singleton**   
>   \- 스프링 컨테이너 내에 단 하나의 객체만 존재하며, 컨테이너가 사라질 때 제거된다.   
> - **Prototype**   
>   \- 모든 요청에 대해 새로운 객체를 생성하며, 참조가 사라지면 GC에 의해 제거된다.   
> - **Request**   
>   \- HTTP 요청이 들어올 때마다 생성된다.  
> - **Session**   
>   \- HTTP 세션이 만들어질 때마다 생성된다.   

### REST(Representational State Transfer)
> \- 자원을 이름(자원의 표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미한다.   
> \- HTTP URI를 통해 자원을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD 수행한다.   
> - **구성 요소**   
>   \- 자원(Resource) : HTTP URI   
>   \- 자원에 대한 행위(Verb) : HTTP Method   
>   \- 자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load   
> - **REST에서의 CRUD Operation**   
>   \- Create : 데이터 생성(POST)   
>   \- Read : 데이터 조회(GET)   
>   \- Update : 데이터 수정(PUT)   
>   \- Delete : 데이터 삭제(DELETE)  

### RESTful
> \- REST의 원리를 따르는 시스템을 의미한다.   
> - **제약조건**   
>   \- 클라이언트-서버(Client-Server)   
&nbsp;&nbsp;&nbsp;: 관심사의 명확한 분리가 선행되면 서버의 구성요소가 단순화되고, 확장성이 향상되어 여러 플랫폼을 지원할 수 있다.   
>   \- 무상태성(Stateless)   
&nbsp;&nbsp;&nbsp;: 서버에 클라이언트의 상태 정보를 저장하지 않는 것을 말한다. 단순히 들어오는 요청만 처리하여 구현을 더 단순화시킨다.   
>   \- 캐시 가능(Cacheable)   
&nbsp;&nbsp;&nbsp;: 클라이언트의 응답을 캐시할 수 있어야한다.   
>   \- 계층화 시스템(Layered System)   
&nbsp;&nbsp;&nbsp;: 서버는 중개서버나 로드 밸런싱, 공유 캐시 등의 기능을 사용하여 확장성 있는 시스템을 구성할 수 있다.   
>   \- 코드 온 디맨드(Code on demand)   
&nbsp;&nbsp;&nbsp;: 클라이언트 서버에서 자바 애플릿, 자바스크립트 실행 코드를 전송받아 기능을 일시적으로 확장할 수 있다.   
>   \- 인터페이스 일관성(Uniform interface)   
&nbsp;&nbsp;&nbsp;: URI로 지정된 리소스에 균일하고 통일된 인터페이스를 제공한다. 아키텍처를 단순하게 분리하여 독립적으로 만들 수 있다.   

### Hateoas(Hypermedia As The Engine Of Application State)
> \- 클라이언트의 요청으로부터 응답을 할 때, 요청 이외의 관련된 URI를 응답에 추가적으로 포함시켜 반환하는 개념이다.   
> - **장점**   
>   \- 요청 URI가 변경되더라도 클라이언트는 이에 대응하여 코드를 변경하지 않아도 된다.   
>   \- Resource가 포함된 URI를 보여주기 때문에, Resource에 대한 신뢰도를 높일 수 있다.   
> - **단점**   
>   \- 전달되는 data의 크기가 커져서 네트워크 오버헤드가 생길 수 있다.   
>   \- 링크가 복잡해질 수 있다.   

### @Value VS @ConfigurationProperties
> \- 스프링의 properties나 yaml에 있는 값들을 사용하기 위한 어노테이션이다.     
> - **@Value**   
>   \- 단일 값 주입만 할 수 있다.   
>   \- RelaxedBinding이 불가능하다.   
>   \- spEL 적용이 가능하다.   
> - **@ConfigurationProperties**   
>   \- 복수의 값을 바인딩할 수 있다.   
>   \- RelaxedBinding이 가능하다.   
>   \- spEL 적용이 불가능하다. 

### @Transactional
> \- 트랜잭션 처리를 위한 어노테이션이다.   
> \- 선언적 트랜잭션이라 부른다.   
> \- 예제코드 : https://github.com/Young-Geun/SpringBoot/tree/master/src/test/java/choi/web/springboot/tx   
> - **적용 대상**   
>   \- 클래스  
>   \- 메서드 (단, public에서만 적용된다. public이 아닌 메서드에 적용할 경우, 예외는 발생하지 않으나 트랜잭션 적용이 무시된다.)   
>   \- 인터페이스 (단, 스프링 공식 매뉴얼에서 권장하지 않는 방식이다. AOP를 적용하는 방식에 따라서 트랜잭션 어노테이션이 적용되지 않을 때가 있다.)   
> - **트랜잭션 AOP 주의사항**   
>   \- 내부호출(프록시를 거치지 않고 호출)의 경우 트랜잭션이 적용되지 않는다.   
>   \- 초기화 시점에는 적용되지 않는다.(예시로 @PostConstruct를 사용한 메서드에서 트랜잭션을 시작할 경우, 올바르게 동작하지 않는다.)   
> - **TransactionlManager 옵션**   
>   \- Transaction Manager가 다수일 경우, 설정한 Bean의 id 혹은 qualifier 값을 아래와 같이 옵션 값으로 사용하여 트랜잭션 매니저를 설정할 수 있다.   
>   \- Ex) @Transactional("subDbTx")   
>   \- Ex) @Transactional(value = "subDbTx")   
>   \- Ex) @Transactional(transactionManager = "subDbTx")   
> - **전파 설정 옵션**   
>   \- REQUIRED(기본값) : 기존 트랜잭션이 존재한다면 기존 트랜잭션으로 참여하고, 없다면 새로 생성한다.   
>   \- REQUIRES_NEW : 항상 새로운 트랜잭션을 생성한다.   
>   \- MANDATORY : 기존 트랜잭션에 참여하며, 기존 트랜잭션이 없다면 예외를 발생시킨다.   
>   \- SUPPORTS : 기존 트랜잭션이 존재한다면 참여하고, 없다면 생성하지 않는다.   
>   \- NOT_SUPPORTED : 기존 트랜잭션이 존재하면 보류시키고, 없다면 생성하지 않는다.   
>   \- NEVER : 트랜잭션을 허용하지 않는다. 기존 트랜잭션이 존재하면 예외를 발생시킨다.   
>   \- NESTED : 기존 트랜잭션이 없다면 생성하고, 있다면 중첩 트랜잭션을 생성한다.   

### PRG(POST-Redirect-GET) 패턴
> \- 웹 디자인 패턴 중 하나로 POST요청에 대한 응답으로 리다이렉트를 통해 GET요청을 할 수 있도록 처리하는 패턴이다.      
> - **상세 순서**   
>   \- 클라이언트는 HTTP POST 요청을 한다.   
>   \- 서버는 클라이언트에게 'URL'과 'GET요청으로 Redirect 할 수 있는 응답코드(302)'를 응답한다.   
>   \- Redirection을 통해 서버에게 응답받은 URL로 GET 요청을 한다.     
> - **적용하지 않았을 시 문제점**   
>   \- 데이터를 POST요청으로 보낸 후 클라이언트가 새로고침을 할 경우, 중복 요청이 발생하여 예기치않은 문제점이 발생할 수 있다.   

### Gradle
> \- Gradle은 그루비(Groovy)를 이용한 빌드 도구로써, Ant와 Maven과 같은 이전 세대의 빌드 도구의 단점을 보완하고 장점을 취합하여 만들어졌다.   
> - **특징**   
>   \- Ant처럼 매우 유연한 범용 빌드 도구이다.   
>   \- 멀티 프로젝트 빌드를 지원한다.   
>   \- 빌드 스크립트를 간단하게 작성할 수 있다.   

### CI/CD
> \- CI/CD란 지속적 통합과 지속적 배포가 통합된 방식을 일컫는다.   
> - **CI(Continuous Integration)**   
>   \- 애플리케이션에 대한 새로운 코드 변경사항이 주기적으로 빌드 및 테스트되어 공통 저장소에 통합되는 개념이다.   
>   \- 다수의 개발자가 형상관리 툴을 공유하는 경우라면, 자동화된 빌드 및 테스트는 원천 소스코드의 충돌을 방어할 수 있는 장점을 가지고 있다.   
> - **CD(Continuous Delivery 또는 Continuous Deployment)**   
>   \- 배포 자동화 과정을 뜻한다.   
>   \- CI가 새로운 소스코드의 빌드, 테스트, 병합을 의미한다면 CD는 개발자의 변경 사항을 넘어 고객의 환경까지 릴리즈 되는 것을 의미한다.   


<br><br><br>
- - -
<br><br><br>



# Database

### 데이터베이스 언어
> - **DDL(Data Definition Language)**  
>   \- 데이터베이스 구조를 정의, 수정, 삭제하기 위한 언어.   
>   \- CREATE, ALTER, DROP   
> - **DML(Data Manipulation Language)**   
>   \- 데이터베이스 내의 자료를 검색, 삽입, 갱신, 삭제하기 위한 언어.   
>   \- SELECT, INSERT, UPDATE, DELETE   
> - **DCL(Data Control Language)**   
>   \- 데이터의 무결성, 보안 및 권한 제어, 복구 등을 하기 위한 언어.   
>   \- COMMIT, ROLLBACK, GRANT, REVOKE   

### Key
> \- 데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 유일한 기준이 되는 속성.   
> - **후보키(Candidate Key)**  
>   \- 튜플을 유일하게 식별하기 위해 사용하는 속성들의 부분 집합.     
>   \- 유일성(Key로 하나의 튜플을 유일하게 식별)을 만족해야 한다.   
>   \- 최소성(꼭 필요한 속성으로만 구성)을 만족해야 한다.   
> - **기본키(Primary Key)**   
>   \- 후보키 중에서 선택한 메인 키.     
>   \- Null 값을 가질 수 없다.   
>   \- 동일한 값이 중복되어 저장될 수 없다.   
> - **대체키(Alternate Key)**   
>   \- 후보키가 둘 이상일 때 기본키를 제외한 나머지 후보키.   
> - **슈퍼키(Super Key)**   
>   \- 한 릴레이션 내에 있는 속성들의 집합으로 구성된 키.   
>   \- 유일성은 만족하지만, 최소성은 만족하지 못한다.   
> - **외래키(Foreign Key)**   
>   \- 관계(Relation)를 맺고 있는 릴레이션 R1, R2에서 릴레이션 R1이 참조하고 있는 릴레이션 R2의 기본키와 같은 R1 릴레이션의 속성.   
>   \- 릴레이션 간에 참조 관계를 표현하는데 중요한 도구.   

### 이상(Anomaly)
> \- 릴레이션에서 일부 속성들의 종속이나 데이터의 중복으로 인해 데이터 조작시 불일치가 발생하는 것.   
> \- 이상 현상은 정규화(Normalization)을 통해 방지할 수 있다.   
> - **삽입 이상(Insertion Anomaly)**   
>   \- 불필요한 정보를 함께 저장하지 않고서는 어떤 정보를 저장하는 것이 불가능한 현상.   
> - **갱신 이상(Update Anomaly)**   
>   \- 데이터 일부만 변경되어, 데이터가 불일치하는 현상.   
> - **삭제 이상(Deletion Anomaly)**   
>   \- 튜플 삭제로 인하여 꼭 필요한 데이터까지 함께 삭제되는 현상.   

### 정규화
> \- 관계형 데이터베이스의 설계에서 중복을 최소화하게 데이터를 구조화하는 프로세스.   
> \- 삽입, 삭제, 갱신 이상이 있는 관계를 재구성함으로써 바람직한 스키마를 만들기 위함이다.   
> - **1NF**   
>   \- 도메인 원자값      
> - **2NF**   
>   \- 부분 함수 종속성 제거   
> - **3NF**  
>   \- 이행 함수 종속성 제거   
> - **BCNF**   
>   \- 결정자이면서 후보키가 아닌 것 제거   

### JOIN
> \- 두 개 이상의 테이블이나 데이터베이스를 연결하여 데이터를 검색하는 행위.   
> \- 일반적으로 Primary key 혹은 Foreign key로 두 테이블을 연결한다.   
> \- 연결하려면 적어도 하나의 칼럼은 서로 공유되고 있어야 한다.   
> - **INNER JOIN**   
>   \- 기존테이블과 조인한 테이블의 중복값을 보여주는데 결과값은 교집합만 검색        
> - **LEFT / RIGHT OUTER JOIN**   
>   \- 기존 테이블 값 + 교집합   
> - **FULL OUTER JOIN**  
>   \- 합집합      
> - **CROSS JOIN**   
>   \- 모든 경우의 수 (N * M)    
> - **SELF JOIN**   
>   \- 하나의 테이블을 여러번 복사해서 조인   

### Index
> \- 테이블에 대한 동작의 속도를 높여주는 자료 구조를 일컫는다.   
> \- 테이블 내의 1개의 컬럼 혹은 여러 개의 컬럼을 이용하여 생성될 수 있다.   

### Transaction
> \- 데이터베이스의 상태를 변화시키기 해서 수행하는 작업의 단위.   
> - **원자성(Atomicity)**   
>   \- 트랜잭션이 데이터베이스에 모두 반영되던가, 아니면 전혀 반영되지 않아야 한다.   
> - **일관성(Consistency)**   
>   \- 트랜잭션의 작업 처리 결과가 항상 일관성이 있어야 한다.   
> - **독립성(Isolation)**  
>   \- 각각의 트랜잭션은 서로 간섭없이 독립적으로 수행되어야 한다.   
> - **지속성(Durability)**   
>   \- 트랜잭션이 성공적으로 완료됬었을 경우, 결과는 영구적으로 반영되어야 한다.   

### SQL vs NoSQL
> - **SQL**   
>   \- 관계형 데이터베이스.      
>   \- 데이터는 정해진 스키마에 따라 테이블에 저장된다.   
> - **NoSQL**   
>   \- 비관계형 데이터베이스.   
>   \- 반정형화, 비정형화된 데이터에 적합하다.   
>   \- 대용량의 데이터 저장에 유리하다.   

### Sharding
> \- 같은 테이블 스키마를 가진 데이터를 다수의 데이터베이스에 분산하여 저장하는 방법   

### [Oracle] SID vs Service Name
> - **SID**   
>   \- 인스턴스의 유니크한 이름으로 단 하나의 인스턴스를 지칭한다.   
> - **Service Name**   
>   \- 여러 개의 인스턴스를 모아 하나의 시스템을 구성할 때 사용되는 TNS alias이다.   
