# Interview


* [Java](#java)

* [Web][web_link]

[web_link]: https://github.com/19920731/Interview/blob/main/Web.md


* [Database][db_link]

[db_link]: https://github.com/19920731/Interview/blob/main/Database.md


* [Algorithm][algorithm_link]

[algorithm_link]: https://github.com/19920731/Java/tree/master/src/algorithm



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
