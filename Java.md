# Java

### JVM
> 내용   

### Garbage Collection
> 내용   

### Thread
> - **프로세스(Process)와 쓰레드(Thread)**   
>   -프로세스란 실행 중인 프로그램을 지칭   
>   -쓰레드란 프로세스의 자원을 이용해서 실제로 작업을 수행하는 것을 지칭   
> - **Thread 클래스와 Runnable 인터페이스**   
>    ```java
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

### OOP의 특징
> - **캡슐화**   
>   -객체의 변수, 메서드 등 실제 구현 내용을 보이지 않게 감싸는 개념   
> - **추상화**   
>   -사물들의 공통적인 특징을 파악해서 하나의 개념으로 다루는 것   
> - **다형성**   
>   -같은 자료형에 여러 가지 객체를 대입하여 다양한 결과를 얻어내는 성질   
> - **상속성**   
>   -클래스로부터 속성과 메서드를 물려받는 것   

### OOP의 5대 원칙 (SOLID)
> - **단일 책임 원칙(Single Responsiblity Principle)**   
>   -소프트웨어의 설계 부품(클래스, 함수 등)은 하나의 책임만 가짐   
>   -응집도는 높고 결합도는 낮음을 뜻함   
>   -클래스가 기능(책임)이 많아지면 내부의 함수끼리 강한 결합이 발생할 가능성이 높음   
> - **개방-폐쇄 원칙(Open-Closed Principle)**   
>   -기존의 코드를 변경하지 않고 기능을 수정하거나 추가할 수 있도록 함   
>   -이를 위해 인터페이스를 사용   
> - **리스코프 치환 원칙(Liskov Substitution Principle)**   
>   -자식 클래스는 부모 클래스에서 가능한 행위를 수행할 수 있어야 함   
> - **의존 역적 원칙(Dependency Inversion Principle)**   
>   -의존 관계를 맺을 때, 변화하기 쉬운 것 보다는 변화하기 어려운 것에 의존해야한다는 원칙   
> - **인터페이스 분리 원칙(인터페이스 분리 원칙)**   
>   -자신이 사용하지 않는 기능(인터페이스)에는 영향을 받지않아야 함   

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
>   -동일 패키지 또는 자식 클래스에서 접근 허용   
> - **default**   
>   -동일 패키지 접근 허용   
> - **private**   
>   -오로지 현재 객체 내에서만 접근 허용   

### Java Collection
> - **Set**   
>   -HashSet, TreeSet   
>   -순서를 유지하지 않는 데이터의 집합으로 데이터의 중복을 허용하지 않음   
> - **List**   
>   -LinkedList, Vector, ArrayList   
>   -순서가 있는 데이터의 집합으로 데이터의 중복을 허용함  
> - **Map**   
>   -Hashtable, HashMap, TreeMap   
>   -키(Key), 값(Value)의 쌍으로 이루어진 데이터으 집합으로, 순서는 유지되지 않으며 키(Key)의 중복을 허용하지 않으나 값(Value)의 중복은 허용   

### Call by Value, Call by Reference   
> - **Call by value**   
>   -값을 호출하는 것을 의미      
>   -전달받은 값을 복사하여 처리하기 때문에 전달받은 값을 변경하여도 원본은 변경되지 않음    
> - **Call by reference**   
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
>   -추상 메서드를 하나라도 가지는 클래스는 추상 클래스가 되어야 함   
>   -추상 클래스는 추상메서드를 가지지 않아도 상관없음   
>   -필드, 생성자, 추상메서드를 가질 수 있음. 생성자를 가지기 때문에 객체화 가능   
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

### Reflection
> -이미 로딩이 완료된 클래스에서 또 다른 클래스를 동적으로 로딩하여 생성자, 멤버 필드, 멤버 메서드 등을 사용하는 기법   
> -스프링 DI와 유사하게 구현 가능   

### 객체 직렬화(Serialization)와 역직렬화(Deserialization)
> 내용<br>


