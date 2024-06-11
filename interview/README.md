- - -
<br><br><br>





# INDEX

* [Java](#java)

* [Web](#web)

* [Design Patterns](#designpatterns)

* [Database](#database)

* [CS](#cs)





<br><br><br>
- - -
<br><br><br>





# Java
## Java의 특징
- 객체 지향 언어로써 캡슐화, 상속, 다형성 기능을 완벽하게 지원한다.
- JVM에서 동작하기 때문에 운영체제에 상관없이 독립적으로 작동하여 이식성이 높다.
- Garbage Collector에 의해 메모리가 관리된다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/37)
<br><br><br>



## 객체지향 프로그래밍이란?
- 프로그래밍에 필요한 데이터와 행위를 객체로 만들고, 객체 간의 상호작용을 통해 비즈니스 로직을 구성하는 프로그래밍 기법.
<br><br><br>



## 객체지향의 4대 특징
- 캡슐화
  - 데이터(변수)와 관련된 기능(메서드)을 하나의 클래스로 묶어서 사용할 수 있으며, 이를 통해 정보은닉 효과를 얻을 수 있다.
- 상속성
  - 부모 클래스의 변수나 메서드를 자식 클래스에게 물려줄 수 있다.
  - 자식 클래스는 부모 클래스에게 상속받음으로써 변수나 메서드를 다시 선언하지 않고 사용할 수 있다.
- 추상화
  - 사물들의 공통적인 특징을 파악해서 하나의 개념으로 다루는 것을 뜻한다.
  - 가령 클래스들의 공통적인 요소를 뽑아내서 상위 클래스로 만들어낼 수 있다.
- 다형성
  - 하나의 객체나 메서드가 여러가지 다른 형태를 가질 수 있는 것을 뜻한다.
  - 오버라이딩과 오버로딩 그리고 상속받은 객체의 참조변수 형변환 등이 있다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/38)
<br><br><br>



## 객체지향의 5대 원칙(SOLID)
- 단일 책임 원칙(Single Responsiblity Principle)
  - 소프트웨어의 설계 부품(클래스, 함수 등)은 하나의 책임만 가진다.
  - 클래스의 기능(책임)이 많아지면 내부 함수끼리 강한 결합이 발생할 가능성이 높으므로 응집도는 높이고 결합도는 낮춰야 한다.
    - `결합도 : 모듈(클래스) 간의 상호 의존 정도로써, 결합도가 낮으면 상호 의존성이 줄어들어 객체의 재사용이나 수정, 유지보수가 용이해진다.`
    - `응집도 : 하나의 모듈 내부에 존재하는 구성 요소들의 기능적 관련성으로, 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져 재사용이나 기능의 수정, 유지보수가 용이해진다.`
- 개방-폐쇄 원칙(Open-Closed Principle)
  - 소프트웨어 엔티티(클래스, 모듈, 함수 등)는 확장에 대해서는 열려 있어야 하지만 변경에 대해서는 닫혀 있어야 한다.
  - 이를 위해 인터페이스를 사용하기도 한다.
- 리스코프 치환 원칙(Liskov Substitution Principle)
  - 자식 클래스는 부모 클래스의 기능을 대체해서 수행할 수 있어야 한다.
  - 부모 클래스의 인스턴스 대신에 자식 클래스의 인스터스를 사용해도 문제가 없어야 한다는 것을 의미한다.
- 인터페이스 분리 원칙(Interface Segregation Principle)
  - 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안된다.
  - 큰 덩어리의 인터페이스들을 작은 단위들로 분리시키고, 꼭 필요한 메서드들만 사용하여 내부 의존성 관계를 느슨하게 한다.
- 의존 역전 원칙(Dependency Inversion Principle)
  - 상위 모듈은 하위 모듈에 종속되어서는 안된다.
  - 의존 관계를 맺을 때, 구체적인 클래스보다는 인터페이스나 추상 클래스와 관계를 맺어야 한다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/39)
<br><br><br>



## 클래스, 객체, 인스턴스 비교
- 클래스
  - 객체를 만들어내기 위한 설계도로써 객체의 상태를 나타내는 필드(field)와 객체의 행동을 나타내는 메서드(method)로 구성된다.
- 객체
  - 클래스로 구현할 모든 대상을 뜻한다.
- 인스턴스
  - 객체가 메모리에 할당되어 실제 사용될 때를 지칭한다.
- 예제코드
  ```java
  public class Animal { // 클래스
      ...
  }
   
  public class Main {
       public static void main(String[] args) {
           Animal cat, dog; // 객체
  
           // 인스턴스화
           cat = new Animal();
           dog = new Animal();
       }
  }
  ```
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/40)
<br><br><br>



## 동일성과 동등성
- 동일성
  - 동일성(Identity)은 두 객체의 메모리 주소가 같음을 의미한다.
- 동등성
  - 동등성(Equality)은 두 객체의 값이 같음을 의미한다.
- JAVA에서의 동일성과 동등성
  - 동일성은 '=='로, 동등성은 'equals'로 확인 가능하다.
- Ref.
[도둑탈을 쓴 애쉬](https://xxeol.tistory.com/15)
<br><br><br>



## String, StringBuffer, StringBuilder 비교
- String
  - 불변(immutable)의 속성을 갖는다.
  - 변경 연산을 자주 사용할 경우, 힙 메모리에 많은 가비지(Garbage)가 생성되어 힙 메모리 부족으로 이어질 수 있다.
  - 불변성을 가지기 때문에 멀티스레드 환경에서 thread-safe하다.
- StringBuffer
  - String 클래스와 다르게 가변성을 갖는다.
  - 동기화를 지원하여 멀티 스레드 환경에서도 안전하게 동작할 수 있다.
- StringBuilder
  - String 클래스와 다르게 가변성을 갖는다.
  - 동기화를 지원하지 않는다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/42)
<br><br><br>



## String Pool
- String Pool이란?
  - String Pool은 String 문자열이 존재하는 영역(JVM 힙 메모리에 존재)을 뜻한다.
  - 문자열 객체라고 모두 String Pool에 저장되는 것은 아니다. 리터럴 문자열(= 쌍 따옴표를 이용해 선언한 문자)은 저장 대상이지만 String 클래스 생성자를 통해 만들어진 문자열은 대상이 아니다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/a77b2b23-7a2b-4b73-aaf3-b2352f955329)
    - s1과 s2는 리터럴로 생성되었기에 String Pool에 저장되어 재사용되므로 동일성을 보장한다.
    - s3은 String 클래스의 생성자를 통해 만들어진 문자이기 때문에 Heap영역에 저장되어 s1과 s2와 동일비교(==)를 하면 false를 반환한다. 이 때는 동등비교(equals)를 진행해야한다.
    - ```java
      public static void main(String... args) {
        String s1 = "Cat";
        String s2 = "Cat";
        String s3 = new String("Cat");
        
        // 객체의 주소값을 비교
        System.out.println(s1 == s2); // true
        System.out.println(s1 == s3); // false
        
        // equals는 문자열을 비교하기 때문에 true
        System.out.println(s1.eqauls(s3)); // true
      }
      ```
  - 리터럴을 사용해서 만든 문자열에 추가 연산을 할 경우에는 String Pool이 아닌 Heap영역에 저장되기 때문에 문자열 연산이 필요한 경우에는 StringBuffer 또는 StringBuilder를 사용해야한다.
- Ref.
[hjtree.log](https://velog.io/@jeb1225/JAVA-String-Pool)
<br><br><br>



## 접근 제어자
- public
  - 모든 접근을 허용한다.
  - 적용대상 : 필드, 생성자, 메서드, 클래스
- protected
  - 같은 패키지 또는 다른 패키지이지만 해당 클래스를 상속받은 자식 클래스에서의 접근을 허용한다.
  - 적용대상 : 필드, 생성자, 메서드
- default
  - 같은 패키지 내에서의 접근을 허용한다.
  - 적용대상 : 필드, 생성자, 메서드, 클래스
- private
  - 같은 클래스 내에서의 접근만 허용한다.
  - 적용대상 : 필드, 생성자, 메서드
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/46)
<br><br><br>



## final 제어자
- final 이란?
  - Java에서는 불변성을 확보하거나 동작을 제한할 수 있는 final 키워드를 제공한다.
  - final 키워드는 변수(variable), 메서드(method), 클래스(class)에 사용할 수 있다.
- final 변수
  - 변수에 final 키워드를 사용할 경우, 더 이상 값을 변경하지 못하도록 제한할 수 있다.
- final 메서드
  - 메서드에 final 키워드를 사용할 경우, 재정의를 제한할 수 있다.
- final 클래스
  - 클래스에 final 키워드를 사용할 경우, 상속을 제한할 수 있다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/44)
<br><br><br>



## 래퍼클래스(Wrapper Class)와 박싱(Boxing), 언박싱(Unboxing)
- 래퍼클래스란?
  - 자바의 자료형은 크게 기본 타입(Primitive type)과 참조 타입(Reference type)으로 나누어진다.
  - 기본 타입을 객체로 다루기 위해서 사용하는 클래스들을 래퍼 클래스(Wrapper class)라고 한다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/e2f5b643-d1e3-4b43-9695-9b5c91fc4620)
- 박싱(Boxing) / 언박싱(UnBoxing)
  - Boxing은 원시 타입의 값을 래퍼 클래스(Wrapper class)로 변환하는 것을 의미한다.
  - Unboxing은 래퍼 클래스를 원시 타입으로 변환하는 것을 의미한다.
  - ```java
    int n = 10;
    
    // 박싱
    Integer boxingNum = new Integer(n);
    System.out.println("boxingNum = " + boxingNum); // 10
    
    // 언박싱
    int unbonxingNum = boxingNum.intValue();
    System.out.println("unbonxingNum = " + unbonxingNum); // 10
    ```
- 오토 박싱(Auto Boxing) / 오토 언박싱(Auto UnBoxing)
  - JDK 1.5부터 지원하는 기능으로써, 명시적으로 표현하지 않아도 컴파일러가 자동으로 박싱과 언박싱을 처리를 해준다.
  - ```java
    int n = 10;
    
    // 오토 박싱
    Integer autoBoxingNum = n;
    System.out.println("autoBoxingNum = " + autoBoxingNum); // 10
    
    // 오토 언박싱
    int autoUnbonxingNum = autoBoxingNum;
    System.out.println("autoUnbonxingNum = " + autoUnbonxingNum); // 10
    ```
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/123)
<br><br><br>



## 추상클래스
- 추상클래스란?
  - 추상 메서드를 선언해 놓고 상속을 통해 자식 클래스에서 메서드를 완성하도록 유도하는 클래스이다.
  - 반드시 사용되어야 하는 메서드를 추상 클래스에 추상 메서드로 선언해 놓으면, 이 클래스를 상속받는 모든 클래스에서는 이 추상 메서드를 반드시 재정의해야 한다.
  - 추상클래스는 abstract 키워드를 붙여 선언할 수 있다.
  - ```java
    abstract class Animal {
        abstract void cry();
    }
    ```
  - ```java
    class Bird extends Animal {
        @Override
        void cry() { // 반드시 cry()를 구현해야한다.
            System.out.println("짹짹");
        }
    }
    
    class Cat extends Animal {
        @Override
        void cry() { // 반드시 cry()를 구현해야한다.
            System.out.println("야옹");
        }
    }
    
    class Dog extends Animal {
        @Override
        void cry() { // 반드시 cry()를 구현해야한다.
            System.out.println("멍멍");
        }
    }
    ```
- 추상클래스 특징
  - 구현해야 하는 메서드들은 상위클래스에서 선언을 해놓고, 구현의 책임을 하위클래스에 위임한다.
  - 메서드와 클래스에 abstract 예약어를 사용한다.
  - 추상메서드가 없어도 abstract 키워드를 사용하면 추상클래스가 된다. 단, 추상메서드가 하나라도 존재한다면 그 클래스는 반드시 추상 클래스가 돼야 한다.
  - 생성자를 가질 수 있고, 일반 메서드도 가질 수 있다. (단, 생성자를 갖지만 객체 생성은 불가능하다.)
- 추상클래스 장점
  - 추상클래스를 만든 후 상속을 받는다면 중복코드 제거 및 코드 재사용성 증대 효과를 얻을 수 있다.
  - 추상클래스를 사용하여 상속을 통해 자식클래스를 구현한다면, 각 각의 클래스들을 그룹화하여 제어할 수 있다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/124)
<br><br><br>



## 인터페이스
- 인터페이스란?
  - 자바에서 클래스들이 구현해야 하는 동작을 지정하는 용도로 사용되는 추상 자료형이다.
  - 인터페이스는 interface 키워드를 붙여 선언할 수 있으며, 기본적으로는 상수와 추상메서드로 구성된다. 하지만 자바8부터는 default 메서드와  static 메서드를 지원한다.
  - ```java
    interface InterfaceSample {
    
        public static final int NUM = 10; // public static final 생략 가능. 컴파일 시에 자동 생성
        public abstract void calc(); // public abstract 생략 가능. 컴파일 시에 자동 생성
   
        default void defaultMethod() { // Java8부터 사용 가능한 default 메서드
            // ...
        }
    
        static void staticMethod() { // Java8부터 사용 가능한 static 메서드
            // ...
        }
      
    }
    ```
- 인터페이스 특징
  - 인터페이스는 interface 키워드를 사용하여 정의한다.
  - 인터페이스는 상수와 추상메서드로 구성되어 있다. (자바8부터 default와  static 메서드 사용 가능)
  - 인터페이스 안의 모든 상수는 public static final 타입이다. (생략 가능)
  - 인터페이스 안의 모든 추상메서드는 abstract public 타입이다. (생략 가능)
  - 추상클래스와 마찬가지로 인스턴스를 생성할 수 없다.
  - 인터페이스는 다른 인터페이스를 extends 키워드로 상속받을 수 있으며, 다중 상속이 가능하다.
  - 클래스에서 인터페이스의 구현은 implements 키워드를 사용하여 구현할 인터페이스를 지정 후, 추상메서드를 모두 오버라이드하여 내용을 완성해야 한다.
- 인터페이스 장점
  - 개발시간을 단축시킬 수 있다.
    - 인터페이스가 작성되면, 메서드를 호출하는 쪽에서는 내용 관계 없이 선언부만 알면 되기때문에 기다릴 필요가 없이 작업을 양쪽에서 동시에 진행할 수 있다.
  - 표준화가 가능하다.
    - 기본 틀을 기준으로 개발하기때문에 일관성있고 정형화된 프로그램 개발이 가능하다.
  - 서로 관계없는 클래스들에게 관계를 맺어줄 수 있다.
    - 서로 상속관계 있지 않으며, 같은 조상클래스를 가지고 있지 않더라도 서로 아무런 관계없는 클래스에게 하나의 인터페이스를 공통적으로 구현함으로써 관계를 맺어줄 수 있다.
  - 독립적인 프로그래밍이 가능하다.
    - 인터페이스를 이용하면 클래스의 선언과 구현을 분리시킬 수 있기 때문에 실제 구현에 독립적인 프로그램을 작성하는 것이 가능하다.
    - 클래스와 클래스간에 직접적인 관계를 인터페이스를 통해 간접적인 관계로 변경하면, 한 클래스에서 변경되어도 다른 클래스에게 영향을 미치지 않는 독립적인 프로그래밍이 가능하게 된다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/125)
<br><br><br>



## 추상클래스와 인터페이스의 차이
- 추상클래스와 인터페이스의 차이점
  - 추상클래스와 인터페이스의 관계도
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/960f18b5-d588-4ddc-ac10-c1998b383bb1)
  - 추상클래스
    - 자식클래스 is kind of 부모클래스
  - 인터페이스
    - 자식클래스 is able to 부모인터페이스
  - 차이점
    - 추상클래스는 계층 구조에서 공통된 속성들을 뽑아서 하나의 클래스로 만들고 자신의 기능들을 하위로 확장시키는 것으로 볼 수 있으며, 인터페이스는 계층 구조는 아니지만 같은 기능이 필요한 경우 사용하는 것으로 볼 수 있다.
    - 추상클래스는 코드 재사용과 일관된 구현이 목적이고, 인터페이스는 느슨한 결합이 목적이다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/126)
<br><br><br>



## Overloading vs Overriding
- 오버로딩(Overloading)
  - 매개변수의 개수나 자료형을 다르게하여 같은 이름의 메서드를 사용하는 것을 뜻한다.
  - ``` java
    int sum(int num1, int num2) {
        return num1 + num2;
    }

    // 새로 추가된 sum() 메서드 - OverLoading이 적용되었다.
    double sum(double num1, double num2) {
        return num1 + num2;
    }
    ```
- 오버라이딩(Overriding)
  - 오버라이딩이란 부모클래스로부터 상속받은 메서드의 내용을 변경(=재정의)하여 사용하는 것을 뜻한다.
  - 오버라이딩 적용X
    - ``` java
      class ParentClass {
          void sayName(String name) {
              System.out.println("[부모클래스] name=" + name);
          }
      }
       
      class ChildClass extends ParentClass {
      }
       
      public class OverridingTest {
      
          public static void main(String[] args) {
              ChildClass child = new ChildClass();
              child.sayName("choi"); // [부모클래스] name=choi
          }
       
      }
      ```
  - 오버라이딩 적용O
    - ``` java
      class ParentClass {
          void sayName(String name) {
              System.out.println("[부모클래스] name=" + name);
          }
      }
      
      class ChildClass extends ParentClass {
          @Override
          void sayName(String name) {
              System.out.println("[자식클래스] name=" + name);
          }
      }
      
      public class OverridingTest {
      
          public static void main(String[] args) {
              ChildClass child = new ChildClass();
              child.sayName("choi"); // [자식클래스] name=choi
          }
      
      }
      ```
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/127)
<br><br><br>



## 제네릭(Generic)
- 제네릭(Generic)이란
  - 제네릭이란 클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법을 의미한다.
  - ``` java
    // String 타입으로 선언 및 생성
    List<String> stringList = new ArrayList<>();
    
    // Integer 타입으로 선언 및 생성
    List<Integer> integerList = new ArrayList<>();
    ```
- 제네릭(Generic)의 장점
  - 컴파일 시점에 타입 검사를 통한 예외 방지
  - 불필요한 캐스팅 제거
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/128)
<br><br><br>



## 컬렉션 프레임워크(Collection Framework)
- 컬렉션 프레임워크(Collection Framework)란?
  - 다수의 데이터를 쉽고 효과적으로 처리할 수 있는 표준화된 방법을 제공하는 클래스의 집합을 의미한다.
  - 컬렉션 프레임워크의 주요 인터페이스에는 List, Set, Map이 있으며 각 각의 인터페이스들은 구현체를 가지고 있다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/c00b20fb-2031-4b27-ae67-1c0efa18e549)
- 컬렉션 프레임워크의 종류
  - List
    - 순서가 있는 데이터 집합이다.
    - 데이터의 중복을 허용한다.
    - 종류
      - ArrayList
        - 단방향 포인터 구조이기 때문에 인덱스로 접근하므로 조회할 때는 유리하지만, 데이터의 삽입이나 삭제가 발생할 경우 인덱스를 조정하는 추가 작업이 필요하다.
      - LinkedList
        - 순차 접근만 가능하여 조회할 때는 불리하지만, 양방향 포인터 구조이기 때문에 데이터의 삽입, 삭제 시에는 유리하다.
      - Vector
        - ArrayList와 구현 원리와 기능적인 측면에서 동일하며, 동기화를 지원한다.
  - Set
    - 순서가 없는 데이터 집합이다.
    - 데이터의 중복을 허용하지 않는다.
    - 종류
      - HashSet
        - 가장 빠르게 접근할 수 있으나 순서를 보장하지 않는다.
      - TreeSet
        - 입력한 순서대로 값을 저장하지 않지만, 기본적으로 오름차순으로 정렬한다.
      - LinkedHashSet
        - 입력한 순서대로 값을 저장한다.
  - Map
    - 키와 값의 한 쌍으로 이루어진 데이터 집합으로 순서가 없다.
    - 키의 중복은 허용하지 않고, 값의 중복은 허용한다.
    - 종류
      - TreeMap
        - 데이터를 이진 검색 트리(binary search tree)의 형태로 저장하므로 데이터의 삽입이나 삭제가 빠르다.
      - HashMap
        - 가장 많이 사용되는 클래스 중 하나이며, 해시 알고리즘을 사용하여 검색 속도가 매우 빠르다.
      - Hashtable
        - HashMap과 다르게 동기화를 보장한다.
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/129)
<br><br><br>



## 람다식(Lambda Expression)
- 람다식(Lambda Expressions) 이란?
  - 람다식이란 프로그래밍 언어에서 사용되는 개념으로 익명 함수를 지칭하는 용어이다.
  - 함수를 람다식으로 표현하면 메서드의 이름 없이 사용할 수 있게 되는데, 이 때문에 익명 함수라고도 불린다.
  - 람다식은 자바 8부터 사용 가능하며, 이로 인하여 자바에서도 함수형 프로그래밍이 가능하게 되었다.
- 장/단점
  - 장점
    - 코드를 간결하게 만들 수 있다.
    - 식에 개발자의 의도가 명확히 드러나기 때문에 가독성이 높아진다.
    - 함수를 만드는 과정없이 한 번에 처리할 수 있기 때문에 생산성이 높아진다.
    - 병렬프로그래밍이 용이하다.
  - 단점
    - 람다를 사용하면서 만든 익명 함수는 재사용이 불가능하다.
    - 디버깅이 어렵다.
    - 람다를 무분별하게 사용할 경우, 비슷한 함수가 중복 생성될 수 있다.
- 예제코드
  - ``` java
    interface SquareIF {
        int square(int num);
    }
    
    public class LambdaSample {
    
        public static void main(String[] args) {
    
            /*
             *  추상 메서드를 하나만 갖는 인터페이스를 자바 8부터는 함수형 인터페이스라고 하며,
             *  이런 함수형 인터페이스만을 람다식으로 표현 가능하다.
             */
            SquareIF sif1 = (int a) -> {
                return a * a;
            };
            System.out.println(sif1.square(1)); // 1
    
    
            /*
             *  1. 매개변수의 타입을 추론할 수 있는 경우에는 타입을 생략할 수 있다.
             *     - Square(int num)를 통해 a가 int일 수 밖에 없으므로 int를 생략할 수 있다.
             *     - (int a)가 (a)로 변경되었다.
             */
            SquareIF sif2 = (a) -> {
               return a * a;
            };
            System.out.println(sif2.square(2)); // 4
    
    
            /*
             *  2. 매개변수가 하나인 경우는 소괄호를 생략할 수 있다.
             *     - 1번 규칙에 의해 (a)로 변경되었으며, 매개변수가 1개이기 때문에 소괄호도 생략 가능하여 a가 되었다.
             */
            SquareIF sif3 = a -> {
                return a * a;
            };
            System.out.println(sif3.square(3)); // 9
    
    
            /*
             *  3. 함수의 몸체가 하나의 명령문만 있을 경우, 중괄호도 생략가능하다. 단, return구문은 생략해야한다.
             */
            SquareIF sif4 = a -> a * a;
            System.out.println(sif4.square(4)); // 16
    
        }
    }
    ``` 
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/130)
<br><br><br>



## 함수형 인터페이스
- 함수형 인터페이스란?
  - 함수형 인터페이스(functional interface)는 추상메서드가 1개만 정의된 인터페이스를 통칭하여 일컫는다.
  - 이 인터페이스 형태의 목적은 자바에서 람다 표현식(Lambda Expression)Visit Website을 이용해 함수형 프로그래밍을 구현하기 위함이다.
  - 함수형 인터페이스를 표현하기 위하여 @FunctionalInterface 어노테이션을 사용할 수 있다. 해당 어노테이션을 붙여주면 두 개 이상의 메소드 선언 시 컴파일 오류를 발생시켜 개발자의 실수를 줄일 수 있다.
  - 자주 사용할 것 같은 람다 함수 형태를 함수형 인터페이스 표준 API로 미리 만들어 제공해준다.
- 종류
  - Consumer<T>
    - 한 개의 입력을 받아서 결과를 반환하지 않는 함수를 정의한다.
    - void accept(T t) 메서드를 가지며, 이 메서드는 매개변수 T를 받아서 아무런 결과도 반환하지 않는다.
    - 주로 입력값을 이용한 연산이나 출력 등의 동작에 사용된다.
  - Supplier<T>
    - 입력 없이 결과를 반환하는 함수를 정의한다.
    - T get() 메서드를 가지며, 이 메서드는 아무런 매개변수를 받지 않고 결과 T를 반환한다.
    - 주로 입력 받는 방식을 경정해 파라미터 없이 특정 결과를 생성하는데 사용된다.
  - Function<T, R>
    - 한 개의 입력을 받아서 결과를 매핑하여 반환하는 함수를 정의한다.
    - R apply(T t) 메서드를 가지며, 이 메서드는 매개변수 T를 받아서 R타입의 결과를 반환한다.
    - 주로 T 타입의 객체를 받아 다른 형태R로 변환하는데 사용된다.
  - Predicate<T>
    - 한 개의 입력을 받아서 boolean 결과를 반환하는 함수를 정의한다.
    - boolean test(T t) 메서드를 가지며, 이 메서드는 매개변수 T를 받아서 boolean 결과를 반환한다.
    - 주로 객체를 조건에 따른 필터링이 필요할 때 사용한다.
- Ref.
[< Hyun / Log >](https://hstory0208.tistory.com/entry/Java-%ED%95%A8%EC%88%98%ED%98%95-%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%9E%80-%ED%99%9C%EC%9A%A9-%EB%B0%A9%EB%B2%95%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)
<br><br><br>



## 스트림 API(Stream API)
- 스트림 API(Stream API) 란?
  - Java 8에서 추가된 기능으로써 배열 또는 컬렉션 등을 함수형 프로그래밍 기법으로 처리할 수 있도록 도와주는 API이다.
- 스트림 API(Stream API)의 특징
  - 원본 데이터를 변경하지 않는다.
  - 컬렉션과 달리 재사용이 불가하여 단 1번만 사용할 수 있다.
  - 내부 반복을 통해 작업을 처리한다.
  - parallelStream() 메서드를 통한 병렬처리를 지원한다.
- 스트림 API(Stream API)의 연산
  - 생성
  - 중간 연산(Intermediate Operation)
    - filter()
      - 스트림 요소마다 조건문을 만족하는 요소로 구성된 스트림을 반환
    - distinct()
      - 스트림 요소들의 중복을 제거한 스트림을 반환
    - map()
      - 스트림의 각 요소마다 수행할 연산을 구현할 때 사용
    - flatMap()
      - 스트림 요소를 새로운 요소로 대체한 스트림을 생성
    - limit()
      - 스트림의 시작 요소로 부터 인자로 전달된 인덱스까지의 요소를 추출해 새로운 스트림을 생성
    - skip()
      - 스트림의 시작 요소로 부터 인자로 전달된 인덱스 까지를 제외하고 새로운 스트림을 생성
    - sorted()
      - 스트림 요소를 정렬하는 method로 기본적으로 오름차순으로 정렬
    - peek()
      - 결과 스트림의 요소를 사용해 추가로 동작을 수행 
  - 최종 연산(Terminal Operation)
    - forEach()
      - 트림의 요소들을 순환하면서 반복해서 처리해야 하는 경우 사용
    - reduce()
      - map과 비슷하게 동작하지만 개별연산이 아니라 누적연산이 이루어진다는 차이 존재
    - findFirst()
      - 스트림에서 지정한 첫 번째 요소를 찾는 메서드
    - findAny()
      - 스트림에서 지정한 첫 번째 요소를 찾는 메서드. parallelStream()와 함께 사용
    - anyMatch()
      - 스트림의 요소 중 특정 조건을 만족하는 요소가 하나라도 있는지 검사
    - allMatch()
      - 스트림의 요소 중 특정 조건을 모두 만족하는지 검사
    - noneMatch()
      - 스트림의 요소 중 특정 조건을 만족하는 요소가 하나도 없는지 검사
    - count()
      - 스트림의 원소들로부터 전체 개수 구하기 위한 메서드
    - min() / max()
      - 스트림의 원소들로부터 최솟값 / 최댓값을 구하기 위한 메서드
    - sum() / average()
      - 스트림 원소들의 합계 / 평균을 구하는 메서드
    - collect()
      - 스트림의 결과를 모으기 위한 메서드
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/135)
<br><br><br>



## Checked Exception과 Unchecked Exception
- Checked Exception과 Unchecked Exception
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/569aa4c7-5107-4345-86b5-3902fce637c9)
  - Checked Exception
    - 확인시점 : Compile 시점
    - 처리여부 : 반드시 예외 처리 필요
    - 롤백여부 : 예외 발생 시, Rollback 수행 안함
  - Unchecked Exception
    - 확인시점 : Runtime 시점
    - 처리여부 : 명시적으로 하지 않아도 무관
    - 롤백여부 : 예외 발생 시, Rollback 수행
- Checked Exception 문제점
  - Checked Exception은 반드시 예외를 처리한다는 특성 때문에 Exception을 던지게(throw)되면, 계층 간 종속이 발생할 수 있다.
  - 만약 아래의 그림과 같이 사용중인 JDBC를 JPA로 변경한다고 가정했을 때, 종속된 모든 계층을 수정해야 하는 상황이 발생한다.
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/afeccd8d-ee1d-4c9b-8d00-ca099595cb17)
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/59b48da0-1c3f-4107-bf91-d39df636f39f)
  - 해결방안
    - Checked Exception을 Unchecked Exception으로 전환한다.
    - ```java
      static class Repository {
          public void call() {
              try {
                  runSQL();
              } catch (SQLException e) {
                  /*
                      Checked Exception인 SQLException 대신에 
                      Unchecked Exception인 RuntimeSQLException 던진다.
                   */    
                  throw new RuntimeSQLException(e);
              }
          }
      
          private void runSQL() throws SQLException {
              // SQL 수행 중 오류가 발생했다고 가정.
              throw new SQLException("ex");
          }
      
      }
      
      // RuntimeSQLException은 RuntimeException을 상속받았으므로 Unchecked Exception이 된다.
      static class RuntimeSQLException extends RuntimeException {
          public RuntimeSQLException(Throwable cause) {
              super(cause);
          }
      }
      ```
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/138)
<br><br><br>



## 스레드
- 프로세스(Process)와 스레드(Thread)
  - 프로세스란 실행 중인 프로그램을 뜻한다.
  - 스레드란 프로세스 내에서 동시에 실행되는 독립적인 실행단위를 뜻한다.
- 스레드의 장점
  - Context Switching이 빠르기 때문에 시스템 처리량이 증가한다.
  - 프로세스 내의 Stack영역을 제외한 모든 메모리를 공유하기 때문에 통신 부담이 적어 프로그램 응답 시간이 단축된다.
- Thread 클래스와 Runnable 인터페이스 구현 비교
  - ```java
    // 1. Thread 클래스를 상속받아 구현       
    static class MyThread1 extends Thread {
        // Thread 클래스의 run()을 오버라이딩
        public void run() {
            for (int i = 0; i < 10; i++) {
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    // ingore
                }
	        	
                System.out.println("MyThread1 run : " + i);
            }
        }
    }

    // 2. Runnable 인터페이스를 구현
    static class MyThread2 implements Runnable {
        // Runnable 인터페이스의 run()을 구현
        public void run() {
            for (int i = 0; i < 10; i++) {
                try {
                    Thread.sleep(1000);
                } catch (InterruptedException e) {
                    // ingore
                }
	    		
                System.out.println("MyThread2 run : " + i);
            }
        }
    }
	 
    public static void main(String[] args) {
        MyThread1 t1 = new MyThread1();
        Thread t2 = new Thread(new MyThread2());
		
        t1.start();
        t2.start(); // 또는 new Thread(new MyThread2()).start();
    }
    ```
- Ref.
[wnajsldkf.log](https://velog.io/@wnajsldkf/Java%EC%9D%98-Thread%EC%97%90-%EB%8C%80%ED%95%B4-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90)
<br><br><br>



## 멀티스레드와 Thread-Safety
- Title
  - Content
- Ref.
[mangoo.log](https://velog.io/@mangoo/java-thread-safety)
[jammmm](https://jammdev.tistory.com/191)
<br><br><br>



## JVM
- JVM이란
  - Java로 개발한 프로그램을 컴파일하여 만들어지는 바이트코드를 실행시키기 위한 가상머신이다.
  - Java와 OS사이에서 중개자 역할을 하여, OS의 종류와 무관하게 동일한 동작을 보장한다.
  - 메모리 관리 및 Garbage Collection을 수행한다.
  - Stack 기반의 가상머신이다.
- JVM 구성
  - 클래스 로더(Class Loader)
  - 실행 엔진(Excution Engine)
  - Garbage Collector
- 실행과정
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/d24ea6ce-6f74-4da1-b6d5-3a931e0e7df7)
    1. 프로그램이 실행되면 JVM은 OS로부터 메모리를 할당 받는다.
    2. 컴파일러가 소스코드(.java)를 읽어 바이트코드(.class)로 변환시킨다.
    3. 클래스 로더를 통해 class파일들을 JVM에 로딩시킨다.
    4. 실행 엔진을 통해 로딩된 class파일들을 해석한다.
    5. 해석된 바이트코드는 Runtime Data Areas에 배치된 후 실행된다. 
- Ref.
[jomminii](https://doozi0316.tistory.com/entry/1%EC%A3%BC%EC%B0%A8-JVM%EC%9D%80-%EB%AC%B4%EC%97%87%EC%9D%B4%EB%A9%B0-%EC%9E%90%EB%B0%94-%EC%BD%94%EB%93%9C%EB%8A%94-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%8B%A4%ED%96%89%ED%95%98%EB%8A%94-%EA%B2%83%EC%9D%B8%EA%B0%80),
[doozi](https://velog.io/@jomminii/whiteship-java-01-what-is-jvm)
<br><br><br>



## 자바의 메모리 구조
- 메서드 영역
  - 클래스에 대한 정보와 클래스 변수(static variable)가 저장되는 영역이다.
  - 모든 스레드에서 정보가 공유된다.
- 힙 영역
  - new 키워드를 통해 생성된 인스턴스의 정보, Array와 같이 동적으로 생성된 데이터가 저장되는 영역이다.
  - Reference Type의 데이터가 저장되는 공간이다.
  - 모든 스레드에서 정보가 공유된다.
- 스택 영역
  - 메서드가 호출되면, 메서드의 지역 변수와 매개변수가 저장되는 영역이다.
  - 만약, 지역변수이지만 Reference Type일 경우에는 Heap에 저장된 데이터의 주소값을 Stack에 저장해서 사용하게 된다.
  - 스레드마다 하나씩 존재한다.
- Ref.
[내가 보려고 만든 개발 (Tech) blog](https://lucas-owner.tistory.com/38)
<br><br><br>



## GC
- GC(Garbage Collection) 란?
  - JVM의 메모리 영역에서 더 이상 참조하지 않는 데이터를 JVM이 자동으로 정리를 해주는 것을 뜻한다.
  - 주로 동적 메모리 영역인 Heap 영역을 대상으로 동작한다.
- JVM Heap 메모리 구성
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/005dc2f5-884b-4b80-9216-90072bdf1fef)
  - Young Generation
    - 새롭게 객체가 생성되는 영역이다.
    - 대부분의 객체는 unreachable 상태가 되기 때문에 Young 영역에서 사라진다.
    - Young 영역에서 사라질 때를 Minor CG라 한다.
  - Old Generation
    - Young 영역에서 생존한 객체가 이 영역으로 이동된다.
    - Young 영역보다 크게 할당되고, 적은 GC가 발생한다.
    - Major GC라 한다. (Full GC는 Young, Old 전체 영역에 대한 GC)
- GC의 동작원리
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/297b7d1a-e8b8-4fb2-90ee-c82ea1a204c0)
    - 객체가 생성되면 Eden 영역에 위치하게 된다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/fb765809-ccf5-4651-8de0-f09a03e3b185)
    - Eden영역이 가득차게 되면 Minor GC가 발생하여 참조가 없는 객체는 삭제되고, 참조 중인 객체는 Survivor 영역으로 이동한다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/49564f31-3a34-4919-831b-e2f17af1d4d1)
    - Survivor 영역이 가득차게 되면 Minor GC가 발생하여 참조가 없는 객체는 삭제되고, 참조 중인 객체는 다른 Survivor 영역으로 이동한다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/0547519e-ff1f-4e4c-b37a-a3e8c2d4f56f)
    - Survivor영역에서의 GC과정을 반복 하며, 계속 참조 중인 객체는 Old Generation으로 이동한다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/c119c549-515b-41c5-a1b2-6b74bbbc2ca5)
    - Eden 영역에서 Survivor 영역으로 이동 할 때 객체가 남아있는 영역보다 큰 경우 Old Generation으로 이동한다.
- GC의 종류
  - Serial GC
    - 가장 단순한 방식의 GC로써, 싱글 스레드로 동작한다.
    - 싱글 스레드로 동작하여 느리고, 그만큼 Stop The World 시간이 다른 GC에 비해 길다.
  - Parallel GC
    - Java 8의 default GC이다.
    - Young 영역의 GC를 멀티 스레드 방식을 사용하기 때문에, Serial GC에 비해 상대적으로 Stop The World 가 짧다.
  - Parallel Old GC
    - Parallel GC는 Young 영역에 대해서만 멀티 스레드 방식을 사용했다면, Parallel Old GC는 Old 영역까지 멀티스레드 방식을 사용한다.
  - CMS(Concurrent Mark Sweep) GC
    - Stop The World로 Java Application이 멈추는 현상을 줄이고자 만든 GC이다.
    - 접근가능한(Reachable) 객체를 한번에 찾지 않고 나눠서 찾는 방식을 사용한다.
  - G1 GC
    - Java 9+ 의 default GC이다.
    - 전체 Heap에 대해서 탐색하지 않고 부분적으로 Region 단위로 탐색하여, 각각의 Region에만 GC가 발생한다.
- Ref.
[오리엔탈킴의 대충 IT 지식과 일상](https://kim-oriental.tistory.com/48),
[DannyJae](https://jhyonhyon.tistory.com/20)
<br><br><br>



## HashMap 충돌
- HashMap 특징 및 동작원리
  - HashMap은 KEY - VALUE가 1:1로 매핑되는 자료구조이다.
  - 위와 같은 특성으로 인하여 삽입, 삭제, 검색이 평균적으로 O(1) 시간복잡도를 갖는다.
  - HashMap의 내부구조는 배열로 되어있으며 배열의 인덱스는 hashcode() % M로 산출한다.
  - 하지만 동일 값이 발생하여 해시충돌이 일어날 수 있으며, 이를 방지하기 위한 방법에는 Open Addressing 방식과 Separate Chaining 방식이 있는데 자바에서는 Separate Chaining 방식을 채택했다.
- Open Addressing
  - Open addressing 방식에도 여러가지 구현 방식이 존재한다.
  - 다양한 방식 중 가장 간단한 Linear probing 방식을 예로 들자면, 충돌이 일어났을 경우 빈 버킷이 나올 때까지 순차적으로 다음 인덱스를 탐색한다.
- Separate Chaining
  - 동일 index로 인해서 충돌이 발생하면 그 index가 가리키고 있는 Linked list에 노드를 추가하여 값을 추가한다.
  - JDK 1.8의 경우에는 index에 노드가 8개 이하일 경우에는 Linked List를 사용하며, 8개 이상으로 늘어날 때는 Tree 구조로 바꾸도록 되어 있다.
- Ref.
[JuHyeong.dev](https://dkswnkk.tistory.com/679)
<br><br><br>



## non-static 멤버와 static 멤버 차이
- non-static 멤버
  - 멤버는 객체마다 별도로 존재한다.
  - 인스턴스 멤버라고도 불린다.
  - 객체 생성 시에 멤버가 생성된다.
  - 객체 생성 후 멤버 사용이 가능하다.
  - 객체가 사라지면 멤버도 사라진다.
  - 공유되지 않는다.
  - 멤버는 객체 내에 각각의 공간을 유지한다.
- static 멤버
  - 멤버는 클래스당 하나가 생성된다.
  - 멤버는 별도의 공간에 생성된다.
  - 클래스 멤버라고도 불린다.
  - 클래스 로딩 시에 멤버가 생성된다.
  - 객체가 생기기 전에 사용이 가능하다.(즉, 객체를 생성하지 않고도 사용가능)
  - 객체가 사라져도 멤버는 사라지지 않는다.
  - 멤버는 프로그램이 종료될 때 사라진다.
  - 동일한 클래스의 모든 객체들에 의해 공유된다.
- Ref.
[Break Out of Your Comfort Zone](https://sujinhope.github.io/2021/03/03/Java-%ED%81%B4%EB%9E%98%EC%8A%A4%EB%B3%80%EC%88%98,-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4-%EB%B3%80%EC%88%98-%EC%B0%A8%EC%9D%B4(Static%EB%B3%80%EC%88%98%EC%99%80-Non-Static%EB%B3%80%EC%88%98).html)
<br><br><br>



## 직렬화와 역직렬화
- 직렬화와 역직렬화
  - 직렬화(serialize)란 자바 언어에서 사용되는 Object 또는 Data를 다른 컴퓨터의 자바 시스템에서도 사용할 수 있도록 바이트 스트림 형태의 연속적인 데이터로 변환하는 포맷 변환 기술을 일컫는다.
  - 그 반대 개념인 역직렬화는(Deserialize)는 바이트로 변환된 데이터를 원래대로 자바 시스템의 Object 또는 Data로 변환하는 기술이다.
- 직렬화 사용처
  - 서블릿 세션(Servlet Session)
    - 단순히 세션을 서블릿 메모리 위에서 운용한다면 직렬화를 필요로 하지 않지만, 만일 세션 데이터를 저장하거나 공유가 필요할 때는 직렬화를 이용할 수 있다.
    - 세션 데이터를 데이터베이스에 저장할 때 사용된다.
    - 톰캣의 세션 클러스터링을 통해 각 서버 간의 데이터를 공유할 수 있다.
  - 캐시(Cache)
    - 데이터베이스로부터 조회한 객체 데이터를 다른 모듈에서도 필요할 때 재차 DB를 조회하는 것이 아닌 객체를 직렬화하여 메모리나 외부 파일에 저장해 두었다가 역직렬화하여 사용하는 캐시 데이터로써 이용이 가능하다.
  - 자바 RMI(Remote Method Invocation)
    - 자바 RMI는 원격 시스템 간의 메시지 교환을 위해서 사용하는 자바에서 지원하는 기술이다.
    - 이 메세지에 객체 데이터를 직렬화하여 송신하는 것이다.
    - 최근에는 소켓을 이용하기 때문에 안쓰이는 기술이다.
- 직렬화 사용법
  - Serializable 인터페이스
    - 우선 객체를 직렬화하기 위해선 java.io.Serializable 인터페이스를 implements 해야 된다. 그렇지 않으면 NotSerializableException 런타임 예외가 발생된다.
  - ObjectOutputStream / ObjectInputStream 클래스
    - 직렬화(스트림에 객체를 출력) 에는 ObjectOutputStream을 사용한다.
    - 역직렬화(스트림으로부터 객체를 입력)에는 ObjectInputStream을 사용한다.
- 자바 직렬화 버전 관리
  - SerialVersionUID
    - Serializable 인터페이스를 구현하는 모든 직렬화된 클래스는 serialVersionUID(이하 SUID) 이라는 고유 식별번호를 부여 받는다.
    - 이 식별 ID는 클래스를 직렬화, 역직렬화 과정에서 동일한 특성을 갖는지 확인하는데 사용된다.
    - 클래스 내부 구성이 수정될 경우, 기존에 직렬화한 SUID와 현재 클래스의 SUID 버전이 다르기 때문에 이를 인지하고 InvalidClassException 예외가 발생시켜 값 불일치 되는 현상을 미연에 방지할 수 있다.
    - 위와 같은 특징으로 인해 클래스에 조그만한 변경사항이라도 있으면, 모든 사용자에게 재배포를 해야하는 애로사항이 있지만, serialVersionUID를 직접 명시해주어 클래스 버전을 수동으로 관리하게되면 이를 해결할 수 있다.
- Ref.
[인파](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%A7%81%EB%A0%AC%ED%99%94Serializable-%EC%99%84%EB%B2%BD-%EB%A7%88%EC%8A%A4%ED%84%B0%ED%95%98%EA%B8%B0)
<br><br><br>



## 리플렉션(Reflection)
- 리플렉션이란?
  - 구체적인 클래스 타입을 알지 못하더라도 그 클래스의 메서드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API이다.
  - 컴파일 시간이 아닌 실행시간에 동적으로 클래스의 정보를 추출할 수 있는 프로그래밍 기법이다.
- 리플렉션의 사용용도
  - 리플렉션은 프레임워크나 라이브러리에서 주로 사용된다.   
    프레임워크나 라이브러리에서는 들어오는 클래스의 정보를 모르기 때문이다.   
    코드를 작성한 개발자는 당연히 내가 작성한 클래스의 정보를 알 수 있지만, 프레임워크 입장에서 보면 모르는게 당연하다.   
    이때, 리플렉션을 통해 런타임 시 클래스의 정보를 얻고 이를 기반으로 하여 프레임워크나 라이브러리가 지원하는 기능을 수행하는 것이다.   
    스프링의 주요 기능인 DI도 리플렉션의 원리가 들어있다.
- 리플렉션의 사용예시
  - 메서드를 직접 호출할 경우, 기능이 추가되면 조건식을 추가하기 위해 매번 코드를 변경해야한다는 단점이 있지만, 리플렉션을 사용할 경우 이러한 단점을 극복할 수 있다.
  - ```java
    import java.lang.reflect.Method;
    
    public class ReflectionEx {
    
        public static void main(String[] args) throws Exception {
            Theme theme = new Theme();
            String userSelectTheme = "Blue";
    
            // 직접 호출하는 경우 : 항목이 추가될 때마다 코드 변경이 필요하다.
            if ("Blue".equals(userSelectTheme)) {
                theme.changeBlue(); // 파란 테마로 변경
            } else if ("Red".equals(userSelectTheme)) {
                theme.changeRed(); // 빨간 테마로 변경
            }
    
            // Reflection을 사용하는 경우 : 클래스나 메서드 정보를 동적으로 변경할 수 있다는 장점이 있다.
            //                          '직접 호출하는 경우'와 다르게 메서드를 실행하는 로직을 공통으로 만들 수 있다.
            Class clazz = Class.forName("basic.reflection.Theme");
            Method method = clazz.getMethod("change" + userSelectTheme);
            method.invoke(theme); // 파란 테마로 변경
        }
    
    }
    
    class Theme {
        public void changeBlue() {
            System.out.println("파란 테마로 변경");
        }
    
        public void changeRed() {
            System.out.println("빨간 테마로 변경");
        }
    }
    ```
- 리플렉션의 장단점
  - 장점
    - 유연성과 확장성
      - 구체적인 클래스를 알지 못해도 동적으로 클래스를 만들어서 의존 관계를 맺어줄 수 있다.
      - 개발 규모가 큰 스프링인 경우, 리플렉션을 이용한 Dynamic proxy를 통해서 @AutoWired, @Service, @Controller, @Repository와 같은 DI 어노테이션을 활용할 수 있다.
    - 접근 제어자에 상관없이 테스트 가능
      - 접근 제어자가 private이더라도 얼마든지 접근해서 조작할 수 있다.
  - 단점
    - 캡슐화 저해
      - private한 데이터에도 접근이 가능하기 때문에 캡슐화가 깨질 위험성이 존재한다.
    - 성능
      - 런타임에 클래스를 분석하므로 속도가 느리다.
    - 컴파일 시 타입 체크가 불가능
      - 컴파일 시점이 아닌 런타임 시점에 에러가 발생하기 때문에 주의가 필요하다.
- Ref.
[영암사는 승경이네](https://tlatmsrud.tistory.com/112)
<br><br><br>



## equals()와 hashCode()
- equals()
  - 두 참조 변수의 값이 같은지 다른지에 대한 동등 여부를 비교할 때 사용하는 메서드이다.
  - 객체 비교에 있어서 equals() 메서드는 기본적으로 == 비교인 객체 주소를 비교한다.
  - 즉, 값이 같은 두 개의 객체를 equals()로 비교하면, 값이 같더라도 주소 비교이기 때문에 false를 반환한다.
  - 객체의 값을 기준으로 동등 비교를 하기 원한다면 equals()를 오버라이딩하여 주소 비교가 아닌 필드값을 비교하도록 변경해야한다.
  - [샘플코드](https://github.com/1992choi/java/blob/master/src/basic/clazz/object/EqualsEx.java)
- hashCode()
  - 객체의 주소 값을 이용해서 해싱(hashing) 기법을 통해 해시 코드를 만든 후 반환한다.
  - 해시코드는 주소값으로 기반으로 만든 고유한 숫자값이다. 이렇기 때문에 서로 다른 객체는 같은 해시 코드를 가질 수 없다.
  - [샘플코드](https://github.com/1992choi/java/blob/master/src/basic/clazz/object/HashCodeEx.java)
- equals()와 hashCode() 재정의의 필요성
  - 앞서 equals()를 재정의하면 값이 같은 객체는 동등한 객체로 판단되는 것을 확인할 수 있었다.
  - 하지만 equals() 재정의로는 부족하며, hashCode()도 같이 재정의가 필요하다.
  - 그 이유는 Collection은 객체가 논리적으로 같은지 비교할 때 아래 그림과 같은 과정을 거치기 때문이다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/4925f518-7bd6-42d1-a2f6-0e061bd179e2)
  - 위의 과정을 기반으로 볼 때 equals()만 재정의하게 된다면, 값이 동일한 두 객체를 Set에 담을 경우, 중복제거가 되어 1개만 적재되기를 기대하겠지만 실제로는 2개의 객체가 모두 적재되는 상황이 발생할 것이다. 이는 hashCode가 다르기 때문에 서로 다른 객체로 판단되기 때문이다.
  - [샘플코드](https://github.com/1992choi/java/blob/master/src/basic/clazz/object/EqualsAndHashCodeEx.java)
- Ref.
[인파](https://inpa.tistory.com/entry/JAVA-%E2%98%95-equals-hashCode-%EB%A9%94%EC%84%9C%EB%93%9C-%EA%B0%9C%EB%85%90-%ED%99%9C%EC%9A%A9-%ED%8C%8C%ED%97%A4%EC%B9%98%EA%B8%B0)
<br><br><br>



## Call by Value와 Call by Reference
- Call by Value
  - 값에 의한 호출을 의미한다.
  - 전달받은 값을 복사하여 처리하기 때문에 전달받은 값을 변경하여도 원본의 값은 변경되지 않는다.
- Call by Reference
  - 참조에 의한 호출을 의미한다.
  - 전달받은 값을 직접 참조하기 때문에 전달받은 값을 변경하면 원본도 같이 변경된다.
- 자바에서는?
  - Java 는 오직 Call by Value 로만 동작한다.
  - 자바에서의 파라미터는 call by value로서만 동작되며, 원시값이 복사 되느냐 주소값이 복사되느냐 차이가 있을뿐이다.
- Ref.
[그릿 속의 해빗](https://loosie.tistory.com/486),
[뱀귤 블로그](https://bcp0109.tistory.com/360)
<br><br><br>



## 블로킹과 논블로킹, 동기와 비동기
- Blocking(블로킹)과 Non-blocking(논블로킹)
  - 블로킹과 논블로킹은 A 함수가 B 함수를 호출했을 때, 제어권을 어떻게 처리하느냐에 따라 달라진다.
  - 블로킹
    - 블로킹은 A 함수가 B 함수를 호출하면, 제어권을 A가 호출한 B 함수에 넘겨준다.
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/a4dd1457-5b09-44b9-bbf9-4962fc82f302)
      - A함수가 B함수를 호출하면 B에게 제어권을 넘긴다.
      - 제어권을 넘겨받은 B는 함수를 실행한다.
      - A는 B에게 제어권을 넘겨주었기 때문에 함수 실행을 잠시 멈춘다.
      - B함수는 실행이 끝나면 자신을 호출한 A에게 제어권을 돌려준다.
  - 논블로킹
    - 논블로킹은 A함수가 B함수를 호출해도 제어권은 그대로 자신이 가지고 있는다.
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/6eebf1c0-99db-4550-a7a8-63827ba5aaa0)
     - A함수가 B함수를 호출하면, B 함수는 실행되지만, 제어권은 A 함수가 그대로 가지고 있는다.
     - A함수는 계속 제어권을 가지고 있기 때문에 B함수를 호출한 이후에도 자신의 코드를 계속 실행한다.
- Synchronous(동기)와 Asynchronous(비동기)
 - 동기와 비동기의 차이는 호출되는 함수의 작업 완료 여부를 신경쓰는지의 여부의 차이이다.
 - 동기
   - 함수 A가 함수 B를 호출한 뒤, 함수 B의 리턴값을 계속 확인하면서 신경쓰는 것이 동기이다.
 - 비동기
   - 함수 A가 함수 B를 호출할 때 콜백 함수를 함께 전달해서, 함수 B의 작업이 완료되면 함께 보낸 콜백 함수를 실행한다.
   - 함수 A는 함수 B를 호출한 후로 함수 B의 작업 완료 여부에는 신경쓰지 않는다.
- 블로킹과 논블로킹, 동기와 비동기
  - Sync-Blocking
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/763a2cbd-eb90-450d-bcf5-d6fa41d5fb0b)
    - 함수 A는 함수 B의 리턴값을 필요로 한다(=동기).
    - 함수 A는 제어권을 함수 B에게 넘겨주고, 함수 B가 실행을 완료하여 리턴값과 제어권을 돌려줄때까지 기다린다(=블로킹).
  - Sync-Nonblocking
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/bbce3cca-c3a9-4e83-a467-6cd981214f87)
    - A 함수는 B 함수를 호출한다. 이 때 A 함수는 B 함수에게 제어권을 주지 않고, 자신의 코드를 계속 실행한다(=논블로킹).
    - A 함수는 B 함수의 리턴값이 필요하기 때문에, 중간중간 B 함수에게 함수 실행을 완료했는지 물어본다(=동기).
  - Async-Nonblocking
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/550cec44-39f8-42fb-a7ea-bb273f66288d)
    - A 함수는 B 함수를 호출한다. 이 때 제어권을 B 함수에 주지 않고, 자신이 계속 가지고 있는다.(=논블로킹)
    - A 함수는 B 함수를 호출한 이후에도 멈추지 않고 자신의 코드를 계속 실행한다.
    - B 함수는 자신의 작업이 끝나면 A 함수가 준 콜백 함수를 실행한다(=비동기).
  - Async-blocking
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/94018b89-dc17-4b48-bf74-35e08462fd47)
    - 거의 사용되지 않는 방식이다.
    - A 함수는 B 함수의 리턴값에 신경쓰지 않고, 콜백함수를 보낸다(비동기).
    - B 함수의 작업에 관심없음에도 불구하고, A 함수는 B 함수에게 제어권을 넘긴다(블로킹).
    - 비동기이지만 A 함수는 제어권을 넘겨줬기 때문에 B 함수의 작업이 끝날 때까지 기다려야 한다.
- Ref.
[유진](https://velog.io/@nittre/%EB%B8%94%EB%A1%9C%ED%82%B9-Vs.-%EB%85%BC%EB%B8%94%EB%A1%9C%ED%82%B9-%EB%8F%99%EA%B8%B0-Vs.-%EB%B9%84%EB%8F%99%EA%B8%B0)
<br><br><br>



## 자바 어노테이션(Annotation)
- 어노테이션이란?
  - 자바에서 어노테이션은 사전적 의미로 주석이라는 뜻을 가지고 있다.
  - 자바에서 어노테이션은 소스코드에 추가해서 사용할 수 있는 메타 데이터의 일종이다.
  - 어노테이션은 보통 골뱅이(@) 기호를 앞에 붙여서 사용하며, JDK1.5 버전 이상부터 사용 가능하다.
- 어노테이션의 역할
  - 코드에 대한 문서화 기능을 제공한다.
  - 컴파일러에게 정보를 제공한다.
  - 런타임 시 동작을 제어한다.
  - 코드 생성을 위한 정보를 제공한다.
- 어노테이션의 종류
  - 어노테이션은 크게 Built-in 어노테이션, Meta 어노테이션, Custom 어노테이션으로 나뉜다.
  - Built-in 어노테이션
    - 이미 JAVA에 내장되어있는 컴파일러를 위한 어노테이션이다.
      - @Override
        - 메서드 앞에 붙임으로서 현재 메서드가 수퍼클래스의 메서드를 재정의 했음을 컴파일러에게 명시하고, 재정의 시 메서드명의 오탈자를 막아준다.
      - @Deprecated
        - 더 이상 사용하지 말아야 할 메서드를 표시한다.
      - @SupressWarning
        - 컴파일러가 주는 경고 메세지를 프로그래머가 의도적으로 무시하고자 할 때 사용한다.
        - 개발자가 경고 내용을 알고 있다는 가정하에 컴파일 로그로 인하여 지저분해진 로그에서 중요한 로그를 놓칠 수 있기에 사용하기도 한다.
      - @NonNull
        - 파라미터로 Null을 넣지 못하게 경고하는 의미에서 사용되는 어노테이션.
        - 파라미터에 NonNull이 붙어있는 메서드를 호출 할 때 인자로 null을 넣으면 컴파일러가 경고를 표시한다.
      - @FunctionalInterace
        - 컴파일러에게 함수형 인터페이스라는 것을 알려 입력 실수를 방지한다.
  - Meta 어노테이션
    - 어노테이션 정의시에 사용되는 어노테이션으로 어노테이션을 위한 어노테이션이라고 할 수 있다.
      - @Target
        - 어노테이션이 적용되는 대상을 지정한다.
        - 여러 대상을 지정해야 할 때 { }로 묶어서 사용한다.
        - 클래스, 필드, 생성자, 메서드 등 적용 대상을 지정할 수 있다.
      - @Retention
        - 어노테이션의 유지기간(라이프사이클)을 지정하기 위해 사용한다.
        - 3가지 정책이 존재한다.
          - SOURCE
            - 소스파일에만 존재하는 어노테이션.
            - 컴파일 타임에 컴파일러에 의해 삭제된다.
          - CLASS
            - 클래스 파일에는 존재하지만, 실질적으로 런타임까지 유지되진 않는다.
            - 클래스 파일에는 포함되지만, 런타임 전 사라지기 때문에 리플렉션으로 어노테이션을 참조 할 수 없다.
            - 정책의 default 값이다.
          - RUNTIME
            - 클래스 파일에 존재하며, 런타임의 종료 시점까지 유지된다.
      - @Documented
        - 어노테이션에 대한 정보가 javadoc으로 작성한 문서에 포함 되도록 할 때 사용하는 어노테이션.
      - @Inherited
        - 어노테이션을 자식 클래스에게도 붙이기 위해(상속) 사용하는 어노테이션.
        - 해당 어노테이션을 부모클래스에 붙이면 자식클래스에서도 이 어노테이션이 붙은 것과 같이 인식된다.
  - Custom 어노테이션
    - 사용자가 개발의 편의를 위해 정의하는 어노테이션이다.
    - 어노테이션은 특별한 종류의 인터페이스이며, 일반 인터페이스와 타입 구분을 위해 @를 앞에 붙여 선언한다.
- Ref.
[algml0703](https://mihee0703.tistory.com/207),
[A6K 개발노트](https://hbase.tistory.com/169),
[eia51.log](https://velog.io/@eia51/Annotation-%EC%99%84%EC%A0%84-%EC%A0%95%EB%B3%B5%EA%B8%B0)
<br><br><br>



## 상속과 합성
- 상속(Inheritance)과 합성(Composition)
  - 상속과 합성은 객체지향 프로그래밍에서 가장 널리 사용되는 코드 재사용 기법이다.
  - 상속
    - 상속이란 부모 클래스의 기능을 자식 클래스에서 재사용할 수 있도록 물려주는 것을 말한다.
    - 코드의 중복을 줄이고, 재사용성을 높이기 위해 자바에서 사용하는 기능이다.
    - is-a 관계
  - 합성
    - 합성이란 기능을 가진 객체 여러개를 묶어서 조합한 것을 말한다.
    - 상속에 의해 코드를 재사용하는 것 대신, 객체의 기능을 호출하는 방식을 통해 코드를 재사용하는 것이다.
    - has-a 관계
- 상속의 문제점
  - 결합도가 높아짐
    - 부모 클래스와 자식 클래스의 관계가 컴파일 시점에 결정되어 결합도가 높아진다.
  - 불필요한 기능 상속
    - 부모 클래스에 메서드를 추가했을 때, 자식 클래스에는 적합하지 않는 메서드가 상속되는 문제가 발생할 수 있다.
  - 부모 클래스의 기능 변경에 의한 자식 클래스의 영향도
    - 부모 클래스의 기능을 자식 클래스에서 그대로 사용하고 있는 경우, 부모의 기능이 변경되면 자식 클래스에도 영향을 미친다.
    - 부모 클래스의 메서드를 재정의하였는데 해당 메서드의 매개변수나 리턴타입이 변경된 경우, 자식 클래스에서 대응하여 변경을 해줘야한다.
  - 단일 상속의 한계
    - 자바에서는 클래스 다중 상속을 허용하지 않는다.
    - 만약 이미 상속 중인데 추가 상속이 필요하다면, 클래스를 다시 나누어서 구성해야하는데 결국 클래스 폭발로 이어지게 된다.
- 합성을 사용해야하는 이유
  - 상속 관계는 변경이 불가능하지만(컴파일 타임), 합성 관계는 실행 시점에 동적으로 변경할 수 있다(런타임).
  - 구현에 대한 의존성을 인터페이스에 대한 의존성으로 변경하여 결합도를 낮출 수 있다.
  - 단일 상속 문제가 해소된다.
- Ref.
[Manta Ray's](https://mantaray.tistory.com/69)
<br><br><br>





<br><br><br>
- - -
<br><br><br>





# Web
## JSP vs Servlet
- JSP
  - html 내에 자바코드를 블록화하여 삽입한 것.
  - JAVA in Html.
- Servlet
  - Container가 이해할 수 있도록 구성된 자바코드로 이루어진 것.
  - Html in JAVA.
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
    4. 해당하는 서블릿에서 service() 메소드 호출 
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



## Framework vs Library
- Framework
  - 뼈대가 되는 부분을 미리 구현한 클래스, 인터페이스, 메서드 등의 집합체이다.
- Library
  - 자주 쓰일 만한 기능들을 따로 구현하여 모아 놓은 클래스의 집합체이다.
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
  - 클래스 또는 메서드 위에 @Transactional을 붙이면 트랜잭션 기능이 적용된 프록시 객체가 생성되며, 트랜잭션 성공 여부에 따라 Commit 또는 Rollback 작업이 이루어진다.
- JDK Proxy(Dynamic Proxy) VS CGLib
  - 스프링에서 사용하는 프록시 구현체는 JDK Proxy(Dynamic Proxy), CGLib가 있다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/3e9696e2-29c2-4b92-a8b3-260b924ad2cb)
  - JDK Dynamic Proxy
    - Interface를 기반으로 Proxy를 생성해주는 방식이다.
  - CGLib Proxy
    - JDK Dynamic Proxy와는 다르게 인터페이스가 아닌 클래스 기반으로 바이트코드를 조작하여 프록시를 생성하는 방식이다.
    - JDK 방식은 java.lang.Reflection을 이용해서 동적으로 프록시를 생성해 준다. 해당 방식의 단점은 AOP 적용을 위해 반드시 인터페이스를 구현해야 된다는 점, 리플렉션은 private 접근이 가능하다는 점 때문에 스프링 부트에서는 기본 방식으로 CGLib 방식을 채택하였다.
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



## JDK Dynamic Proxy VS CGLIB Proxy
- Title
  - Content
- Ref.
[펲로그](https://suyeonchoi.tistory.com/81)
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
  - PUT 메서드는 리소스 전체를 대체한다.
  - 기존 리소스가 없을 경우 새로 생성한다. 즉, 덮어쓰기를 수행한다고 볼 수 있다.
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





<br><br><br>
- - -
<br><br><br>





# DesignPatterns
## [GoF] 디자인 패턴
- GoF(Gang of Four)란?
  - 이 분야의 4인방(Gang of Four)의 의미로 소프트웨어 설계에 있어 공통된 문제들에 대한 표준적인 해법과 작명법을 제안한 "Design Patterns"의 저자들을 지칭한다.
  - 여러 가지 문제에 대한 설계 사례를 분석하여 서로 비슷한 문제를 해결하기 위한 설계들을 분류하고, 각 문제 유형별로 가장 적합한 설계를 일반화해 패턴으로 정립하였다.
- GoF 디자인 패턴의 유형
  - GoF(Gang of Four)에서는 23가지 디자인 패턴을 다음의 3가지 유형으로 분류한다.
    - 생성 패턴(Creational Pattern)
      - 객체 생성과 관련된 패턴
      - 객체가 생성되는 과정의 유연성을 높이고 손쉬운 코드의 유지
      - 종류
        - 싱글톤 (Singleton)
        - 추상 팩토리 (Abstract Factory)
        - 빌더 (Builder)
        - 팩토리 메서드 (Factory Method)
        - 프로토타입 (Prototype)
    - 구조 패턴(Structural Pattern)
      - 프로그램 구조와 관련된 패턴
      - 프로그램 구조를 설계할 때 활용 가능한 패턴
      - 클래스나 객체를 조합해 더 큰 구조를 만드는 패턴
      - 종류
        - 어댑터 (Adapter)
        - 브릿지 (Bridge)
        - 합성 (Composite)
        - 데코레이터 (Decorator)
        - 파사드 (Facade)
        - 플라이웨이트 (Flyweight)
        - 프록시 (Proxy)
    - 행동 패턴(Behavioral Pattern)
      - 반복적으로 사용되는 객체들의 상호작용을 패턴화
      - 결합도를 최소화하는 것에 중점
      - 객체(클래스) 사이에 알고리즘이나 책임 분배에 관련된 패턴
      - 종류
        - 책임연쇄 (Chain of Responsibility)
        - 커맨드 (Command)
        - 인터프리터 (Interpreter)
        - 반복자 (Iterator)
        - 중재자 (Mediator)
        - 메멘토 (Memento)
        - 옵저버 (Observer)
        - 상태 (State)
        - 전략 (Strategy)
        - 템플릿 메서드 (Template Method)
        - 방문자 (Visitor)
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/41)
<br><br><br>



## [GoF] 싱글톤 패턴
- 싱글톤 패턴이란?
  - 싱글톤 패턴은 '하나'의 인스턴스만 생성하여 사용하는 디자인 패턴이다.
- 싱글톤 패턴의 장점
  - 한 개의 인스턴스만을 생성하고 공유하기 때문에 메모리 낭비를 방지할 수 있다.
  - 인스턴스를 매번 생성하는 것이 아니므로 속도 측면에서 이점이 있다.
  - 전역으로 사용하는 인스턴스이기 때문에 다른 여러 클래스에서 데이터를 공유하며 사용할 수 있다.
- 싱글톤 패턴의 단점
  - 의존성이 높아진다.
  - 멀티스레드 환경에서 동시성 문제가 발생할 수 있다.
- 구현 예시
  - 싱글톤 패턴의 구현 방법은 매우 다양하지만 다음과 같은 공통사항을 가지고 있다.
    - private 생성자만을 정의하여 외부 클래스로부터 인스턴스 생성을 막는다.
    - 싱글톤을 구현하고자 하는 클래스 내부에 멤버 변수로써 private static 객체 변수를 만든다.
    - public static 메서드를 통해 외부에서 싱글톤 인스턴스에 접근할 수 있도록 접점을 제공한다.
  - ```
    public class Singleton {
    
        private static Singleton instance;
        
        // 생성자를 private으로 하여 다른 클래스에서는 인스턴스를 만들지 못하게 한다. 
        private Singleton() {}
    
        public static Singleton getInstance() {
            /* 
                인스턴스를 사용하기 위하여 getInstance()를 호출하는데,
                최초 접근으로 아직 만들어지지 않았다면 인스턴스를 만들고
                그렇지 않다면 만들어진 인스턴스를 반환한다.            
            */
            if (instance == null) {
                instance = new Singleton();
            }
    
            return instance;
        }
        
    }
    ```
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/50)
<br><br><br>



## [GoF] 팩토리 메서드 패턴
- 팩토리 메서드 패턴이란?
  - 팩토리 메서드 패턴은 객체의 생성 과정을 서브 클래스에 위임하는 디자인 패턴이다.
  - 이를 통해 클라이언트 코드는 구체적인 클래스의 인스턴스화 과정을 알 필요없이 객체를 생성할 수 있다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/1abff890-6371-41a2-8d87-8b760a6d39ab)
- 팩토리 메서드 패턴의 장점
  - 객체 생성 과정의 캡슐화
    - 클라이언트는 객체 생성 방법을 몰라도 된다.
  - 유연성과 확장성
    - 객체 생성 방법을 변경하거나 확장하기 쉽다.
    - 기존의 코드를 수정하지 않고 확장이 가능하여, 개방 폐쇄 원칙을 위반하지 않는다.
  - 의존성 관리
    - 스프링과 같은 프레임워크에서는 의존성 주입을 통해 더 깔끔한 코드 관리가 가능하다.
- 팩토리 메서드 패턴의 단점
  - 코드 복잡성 증가
    - 추가적인 코드와 추상화 레이어가 필요하다.
  - 디자인의 오버헤드
    - 간단한 객체 생성에는 오버엔지니어링일 수 있다.
- 구현 예시
  ``` java
  public class Client {
      public static void main(String[] args) {
          LaptopFactory myLaptopFactory1 = new NormalLaptopFactory();
          Laptop myLaptop1 = myLaptopFactory1.newInstance();
          myLaptop1.runTests(); // Running tests on a NormalLaptop...
  
          LaptopFactory myLaptopFactory2 = new GamingLaptopFactory();
          Laptop myLaptop2 = myLaptopFactory2.newInstance();
          myLaptop2.runTests(); // Running tests on a GamingLaptop...
      }
  }
  ```
  ``` java
  public interface Laptop {
      void runTests();
  }
  
  public class NormalLaptop implements Laptop {
      @Override
      public void runTests() {
         System.out.println("Running tests on a NormalLaptop...");
      }
  }
  
  public class GamingLaptop implements Laptop {
      @Override
      public void runTests() {
         System.out.println("Running tests on a GamingLaptop...");
      }
  }
  ```
  ``` java
  public abstract class LaptopFactory {
      public Laptop newInstance(){
          return createLaptop();
      }
      protected abstract Laptop createLaptop();
  }
  
  public class NormalLaptopFactory extends LaptopFactory {
      @Override
      protected Laptop createLaptop() {
          return new NormalLaptop();
      }
  }
  
  public class GamingLaptopFactory extends LaptopFactory {
      @Override
      protected Laptop createLaptop() {
          return new GamingLaptop();
      }
  }
  ```
- Ref.
[멋쟁이코더](https://curiousjinan.tistory.com/entry/factory-method-pattern-spring),
[뱀귤 블로그](https://bcp0109.tistory.com/367),
[da-in](https://github.com/da-in/tech-interview-study/blob/main/CS%20Deep%20Dive/Design%20Pattern/Factory%20Method%20Pattern.md)
<br><br><br>



## [GoF] 프록시 패턴
- 프록시 패턴이란?
  - 프록시 (Proxy)란 대리자, 대변인의 의미를 가지고 있다. 말 그대로 원본 객체를 바로 호출하는 것이 아니라, 원본 객체에 접근할 수 있는 대리자를 호출하는 패턴이다.
  - 객체 간의 간접적인 접근을 가능하게 하는 구조를 제공하는 패턴이다.
  - 어떤 객체를 호출할 때, 객체를 직접 호출하는 것이 아니라 대리자 객체를 호출하는 방식을 사용하면 해당 객체가 메모리에 존재하지 않아도 기본적인 정보를 참조하거나 설정할 수 있다.
  - 실제 객체의 필요 시점까지 객체 생성을 미루는 지연 초기화(Lazy Initializing)가 가능하다.
- 프록시 패턴의 구조
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/7daa8c4d-da53-44de-9fd4-820542823e26)
  - Subject
    - Proxy와 RealSubject가 모두 구현하는 인터페이스로 클라이언트가 프록시와 실제 대상을 동일하게 다룰 수 있도록 정의한다.
  - RealSubject
    - 클라이언트가 직접 상호작용하는 실제 객체다.
  - Proxy
    - RealSubject를 감싸며 실제 작업을 수행하는 주체로 클라이언트와 RealSubject 사이에 위치한 중간 객체다.
    - RealSubject의 같은 이름의 메서드를 호출하며, 클라이언트의 요청을 처리하기 전이나 후에 추가적인 작업을 수행할 수 있다.
- 프록시 패턴의 장점
  - 보안성 향상
    - 원본 객체에 직접 접근하지 않기 때문에 보안성이 향상된다.
    - 프록시 객체를 사용하여 원본 객체 접근 권한을 제한할 수 있다.
    - 접근 로그를 남기는 등 보안적인 추가 기능을 적용할 수 있다.
  - 유연성 향상
    - 원본 객체에 간접적으로 접근하므로, 객체 간의 결합도를 줄일 수 있다.
  - 성능 향상
    - 지연 초기화를 통해 객체가 필요한 순간에 필요한 객체만 초기화하여 사용하므로, 불필요한 객체 생성을 줄일 수 있다.
- 프록시 패턴의 단점
  - 복잡성 증가
    - 객체 간의 중간 계층이 추가되어 코드의 복잡성이 증가한다.
  - 성능 저하
    - 프록시 객체를 추가로 사용하므로, 객체 생성이 빈번한 경우 성능이 저하될 수 있다.
- 프록시 패턴과 데코레이터 패턴
  - 둘다 프록시를 사용하는 패턴이지만 의도에 따라 구분된다.
  - 프록시 패턴
    - 접근 제어가 목적
  - 데코레이터 패턴
    - 새로운 기능 추가가 목적
- Ref.
[Hyun/Log](https://hstory0208.tistory.com/entry/Spring-%ED%94%84%EB%A1%9D%EC%8B%9C-%ED%8C%A8%ED%84%B4%EA%B3%BC-%EB%8D%B0%EC%BD%94%EB%A0%88%EC%9D%B4%ED%84%B0-%ED%8C%A8%ED%84%B4),
[장쫄깃](https://jangjjolkit.tistory.com/59),
[잇트루](https://ittrue.tistory.com/555)
<br><br><br>



## [GoF] 템플릿 메서드 패턴
- 템플릿 메서드 패턴이란?
  - 여러 클래스에서 공통으로 사용하는 메서드를 템플릿화하여 상위 클래스로 정의하고, 하위 클래스마다 세부 동작 사항을 다르게 구현하는 패턴이다.
- 템플릿 메서드 패턴의 구조
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/a69e3088-9ff8-4b65-bd51-3ee2cc4d3981)
  - 상위 클래스(AbstractClass)는 템플릿을 제공하고 이를 상속받는 하위 클래스(SubClass)가 구체적인 로직을 작성한다.
- 템플릿 메서드 패턴의 장점
  - 중복된 코드를 없애고 SubClass 에서는 비즈니스 로직에만 집중할 수 있다. (SRP)
  - 나중에 새로운 비즈니스 로직이 추가되어도 기존 코드를 수정하지 않아도 된다. (OCP)
- 템플릿 메서드 패턴의 단점
  - 상위 클래스 변화가 생길 경우, 모든 하위 클래스를 수정해야 할 수도 있다.
  - 부모 클래스의 기능을 사용하지 않더라도 상속관계가 되기 때문에 부모 클래스와 강한 의존관계가 형성된다.
- 템플릿 메서드 패턴과 전략 패턴
  - 전략 패턴은 합성(composition)을 통해 해결책을 강구하며, 템플릿 메서드 패턴은 상속(inheritance)을 통해 해결책을 제시한다.
  - 전략 패턴은 클라이언트와 객체 간의 결합이 느슨한 반면, 템플릿 메서드 패턴에서는 두 모듈이 더 밀접하게 결합된다.
  - 전략 패턴에서는 대부분 인터페이스를 사용하지만, 템플릿 메서드 패턴서는 주로 추상 클래스나 구체적인 클래스를 사용한다.
  - 단일 상속만이 가능한 자바에서 상속 제한이 있는 템플릿 메서드 패턴보다는, 다양하게 많은 전략을 implements 할 수 있는 전략 패턴이 협업에서 많이 사용되는 편이다.
- Ref.
[Hudi](https://hudi.blog/template-method-pattern/),
[뱀귤 블로그](https://bcp0109.tistory.com/369),
[밝은별 개발자](https://brightstarit.tistory.com/38)
<br><br><br>



## [GoF] 전략 패턴
- 전략 패턴이란?
  - 실행(런타임) 중에 알고리즘 전략을 선택하여 객체 동작을 실시간으로 변경 가능케하는 디자인 패턴이다.
  - 전략 패턴을 활용하면 OCP를 위반하지 않고 새로운 전략을 추가하여 코드 수정없이 기능을 추가할 수 있다는 장점이 있다.
- 전략 패턴의 구조
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/d1570ebd-04da-43da-a399-b184ba9dffe1)
  - Context
    - 전략 패턴을 이용하는 역할을 수행한다.
    - 필요에 따라 동적으로 구체적인 전략을 바꿀수 있도록 setter() 메서드를 제공한다.
  - Strategy
    - 인터페이스나 추상 클래스로 외부에서 동일한 방식으로 알고리즘을 호출하는 방법을 명시한다.
  - Strategy1, Strategy2, Strategy3
    - 전략 패턴에서 명시한 알고리즘을 실제로 구현한 클래스이다.
- 전략 패턴의 장점
  - 알고리즘과 클라이언트 코드가 독립적으로 변화할 수 있어 유지보수와 확장성이 용이하다.
  - 새로운 알고리즘을 추가하거나 기존 알고리즘을 변경하더라도 클라이언트 코드를 수정하지 않아도 된다.
  - 코드의 재사용성이 높아진다.
- 전략 패턴의 단점
  - Strategy 객체를 생성하고 관리하는데 추가적인 비용이 발생할 수 있다.
  - 클라이언트 코드에서 적절한 알고리즘을 선택하는 로직이 복잡해질 수 있다.
- Ref.
[DevSeoRex](https://velog.io/@ch4570/%EC%A0%84%EB%9E%B5-%ED%8C%A8%ED%84%B4Strategy-Pattern-%EC%96%B4%EB%96%BB%EA%B2%8C-%EC%A0%81%EC%9A%A9%ED%95%A0-%EC%88%98-%EC%9E%88%EC%9D%84%EA%B9%8C),
[카일](https://velog.io/@kyle/%EB%94%94%EC%9E%90%EC%9D%B8-%ED%8C%A8%ED%84%B4-%EC%A0%84%EB%9E%B5%ED%8C%A8%ED%84%B4%EC%9D%B4%EB%9E%80),
[밝은별 개발자](https://brightstarit.tistory.com/39)
<br><br><br>





<br><br><br>
- - -
<br><br><br>





# Database
## DDL, DML, DCL, TCL
- DDL (Data Definition Language)
  - 데이터베이스의 구조를 정의할 때 사용하는 언어이다.
  - DDL은 명령어를 입력하는 순간 작업이 즉시 반영(Auto Commit)되기 때문에 사용할 때 주의해야 한다.
  - 종류
    - CREATE : 테이블, 뷰 또는 인덱스와 같은 새 데이터베이스 개체를 생성
    - ALTER : 기존 데이터베이스 개체를 수정
    - DROP : 테이블, 뷰 또는 인덱스와 같은 데이터베이스 개체 삭제
    - TRUNCATE : 테이블의 모든 행을 삭제(DROP과 달리 테이블의 구조와 인덱스는 그대로 유지)
    - RENAME : 기존 데이터베이스 개체의 이름을 변경
- DML (Data Manipulation Language)
  - 데이터베이스 내의 데이터를 조작하는 데 사용하는 언어이다.
  - 종류
    - SELECT : 데이터를 조회하는 명령어
    - INSERT : 데이터를 생성하는 명령어
    - UPDATE : 데이터를 수정하는 명령어
    - DELETE : 데이터를 삭제하는 명령어
- DCL (Data Control Language)
  - 데이터베이스에 접근하고 객체들을 사용하도록 권한을 주고 회수하는 데 사용되는 언어이다.
  - 종류
    - GRANT : 권한 부여
    - REVOKE : 권한을 제한하거나 회수
- TCL (Transaction Control Language)
  - 데이터베이스의 구조를 정의할 때 사용하는 언어이다.
  - DDL은 명령어를 입력하는 순간 작업이 즉시 반영(Auto Commit)되기 때문에 사용할 때 주의해야 한다.
  - 종류
    - COMMIT : 논리적인 작업의 단위를 묶어서 DML에 의해 조작된 결과를 영구적으로 반영
    - ROLLBACK : 논리적인 작업의 단위를 묶어서 DML에 의해 조작된 결과를 작업 이전의 상태로 복구
    - SAVEPOINT : 저장점을 정의하면 롤백할 때 트랜잭션에 포함된 전체 작업을 롤백하는 것이 아니라 현시점에서 SAVEPOINT까지 트랜잭션의 일부만 롤백
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/121)
<br><br><br>



## Key의 종류와 특징
- Key란?
  - 데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 유일한 기준이 되는 속성이다.
- Key의 종류
  - Candidate Key (후보키)
    - 튜플을 유일하게 식별할 수 있는 속성들의 부분 집합
    - 모든 릴레이션은 반드시 하나 이상의 후보키를 가져야 한다.
    - 유일성과 최소성을 만족해야 한다.
      - `유일성 : 하나의 키값으로 튜플을 유일하게 식별할 수 있는 성질` 
      - `최소성 : 키를 구성하는 속성들 중 꼭 필요한 최소한의 속성들로만 키를 구성하는 성질`
  - Primary Key (기본키)
    - 후보키 중에서 선택한 메인이 되는 키
    - Null 값을 가질 수 없다.
    - 동일한 값이 중복될 수 없다.
  - Alternate Key (대체키)
    - 후보키 중 기본키를 제외한 나머지 키
  - Super Key (슈퍼키)
    - 유일성은 만족하지만, 최소성은 만족하지 못하는 키
    - 릴레이션을 구성하는 모든 튜플에 대해 유일성은 만족하지만, 최소성은 만족시키지 못한다.
  - Foreign Key (외래키)
    - 다른 릴레이션의 기본키를 그대로 참조하는 속성의 집합
    - 외래키는 참조되는 릴레이션의 기본키와 대응되어 릴레이션 간에 참조 관계를 표현하는데 중요한 도구로 사용된다.
    - 외래키로 지정되면 참조 테이블의 기본키에 없는 값은 입력할 수 없다. (참조 무결성 조건)
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/122)
<br><br><br>



## 자연키와 인조키
- 자연키
  - 비즈니스 모델에서 자연스럽게 나오는 속성
  - Ex) 회원 테이블의 사용자ID
- 인조키
  - 비즈니스 모델과 상관없이 오로지 키 역할을 하기 위해 인조적으로 만든 속성
  - Ex) UUID, Auto Increment의 값
- 자연키와 인조키의 특징
  - 자연키는 변할 위험이 존재한다.
    - Ex) 가령 회원 테이블의 자연키를 주민번호로 지정했는데 정책에 따라 주민번호를 저장하지 못하게 된다면 다른 속성으로 변경이 필요하다.
  - 인조키를 사용하면 성능을 향상시킬 수 있다.
    - 자연키를 PK로 사용하는 경우 일반적으로 문자열로 사용할 가능성이 높은데, 문자열을 사용하는 것은 숫자를 사용하는 것보다 느리다.
    - PK의 크기는 작을수록, 원시 타입일수록 성능상 유리하다.
- Ref.
[빛나자](https://warmth424.tistory.com/14),
[망나니개발자](https://mangkyu.tistory.com/287)
<br><br><br>



## 이상(Anomaly)
- 이상(Anomaly)이란?
  - 릴레이션에서 일부 속성들의 종속이나 데이터의 중복으로 인해 데이터 조작시 불일치가 발생하는 것을 의미한다.
  - 이상 현상은 정규화(Normalization)을 통해 방지할 수 있다.
- 이상의 종류
  - 삽입 이상(Insertion Anomaly)
    - 불필요한 정보를 함께 저장하지 않고서는 어떤 정보를 저장하는 것이 불가능한 현상.
  - 갱신 이상(Update Anomaly)
    - 데이터 일부만 변경되어, 데이터가 불일치하는 현상.
  - 삭제 이상(Deletion Anomaly)
    - 튜플 삭제로 인하여 꼭 필요한 데이터까지 함께 삭제되는 현상.
- Ref.
[TTOII](https://nice-engineer.tistory.com/entry/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-Anomaly-%EC%9D%B4%EC%83%81-%ED%98%84%EC%83%81)
<br><br><br>



## 정규화
- 정규화란?
  - 관계형 데이터베이스의 설계에서 중복을 최소화하기 위하여 데이터를 구조화하는 프로세스를 뜻한다.
  - 삽입, 삭제, 갱신 이상이 있는 관계를 재구성함으로써 바람직한 스키마를 만들수 있다.
- 정규화의 종류
  - 1NF
    - 모든 도메인이 원자값으로만 구성된다.
  - 2NF
    - 모든 속성의 부분적 종속이 없이 완전 함수 종속을 만족한다.
  - 3NF
    - 기본키를 제외한 속성들 간에 이행 종속성이 없다.
  - BCNF
    - 모든 결정자가 후보키일 때, 결정자이면서 후보키가 아닌 것을 제거한다.
  - 4NF
    - 다치 종속을 제거한다.
  - 5NF
    - 모든 조인 종속이 후보키를 통해서만 성립한다. 
- Ref.
[star가 되고나서](https://star7sss.tistory.com/822)
<br><br><br>



## JOIN
- JOIN이란?
  - 두 개 이상의 테이블이나 데이터베이스를 연결하여 데이터를 검색하는 행위를 뜻한다.
  - 일반적으로 Primary key 혹은 Foreign key로 두 테이블을 연결한다.
  - 연결하려면 적어도 하나의 칼럼은 서로 공유되고 있어야 한다.
- JOIN의 종류
  - INNER JOIN
    - 기존테이블과 조인한 테이블의 중복값을 보여주는데 결과값은 교집합만 검색
  - LEFT / RIGHT OUTER JOIN
    - 기존 테이블 값 + 교집합
  - FULL OUTER JOIN
    - 합집합
  - CROSS JOIN
    - 모든 경우의 수 (N * M)
  - SELF JOIN
    - 하나의 테이블을 여러번 복사해서 조인
- Ref.
[나눔코딩](https://theheydaze.tistory.com/584)
<br><br><br>



## Transaction
- 트랜잭션이란?
  - 데이터베이스의 상태를 변화시키기 해서 수행하는 작업의 단위를 뜻한다.
- 트랜잭션 특징
  - 원자성(Atomicity)
    - 트랜잭션이 데이터베이스에 모두 반영되던가, 아니면 전혀 반영되지 않아야 한다.
  - 일관성(Consistency)
    - 트랜잭션의 작업 처리 결과가 항상 일관성이 있어야 한다.
  - 독립성(Isolation)
    - 각각의 트랜잭션은 서로 간섭없이 독립적으로 수행되어야 한다.
  - 지속성(Durability)
    - 트랜잭션이 성공적으로 완료됬었을 경우, 결과는 영구적으로 반영되어야 한다.
- 격리수준
  - 레벨 0 (Read Uncommitted)
    - 트랜잭션에서 처리 중인, 아직 커밋 되지 않은 데이터를 다른 트랜잭션에서 읽는 것을 허용한다.
    - Dirty Read, Non-Repeatable Read, Phantom Read 현상이 발생할 수 있다.
      - Dirty Read
        - 다른 트랜잭션에서 커밋되지 않은 변화를 읽음.
        - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/414b1cd4-13ca-4e39-bcff-e091933c00bf)
      - Non-Repeatable Read
        - 같은 데이터를 한 Transaction 에서 읽었음에도 불구하고 값이 달라지는 현상.
        - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/1b7d12af-ef64-4cb8-ac43-17bf55dfcfad)
      - Phantom Read
        - 한 개의 Transaction 에서 같은 조건으로 2번 읽었는데 2 번의 결과가 다른 현상.
        - 없던 데이터가 생기는 현상.
        - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/6bea3fb4-5c29-4335-a542-6f64434f3e55)
  - 레벨 1 (Read Committed)
    - 트랜잭션이 커밋되어 확정된 데이터를 읽는 것을 허용한다.
    - 대부분의 DBMS가 기본 모드로 채택하고 있는 격리수준이다.
    - Non-Repeatable Read, Phantom Read 현상이 발생할 수 있다.
  - 레벨 2 (Repeatable Read)
    - 선행 트랜잭션이 읽은 데이터는 트랜잭션이 종료될 때가지 후행 트랜잭션이 갱신하거나 삭제하는 것은 불허함으로써 같은 데이터를 두 번 쿼리했을 때 일관성 있는 결과를 리턴한다.
    - Phantom Read 현상이 발생할 수 있다.
  - 레벨 3 (Serializable Read)
    - 선행 트랜잭션이 읽은 데이터를 후행 트랜잭션이 갱신하거나 삭제하지 못할 뿐만 아니라 중간에 새로운 레코드를 삽입하는 것도 막아준다.
    - 완벽하게 읽기 일관성 모드를 제공한다.
    - 일관성이 높아지지만 데이터를 처리하는 속도가 느려지게 된다.
- Ref.
[Wonit](https://wonit.tistory.com/462),
[NKLCWDT](https://github.com/NKLCWDT/cs/blob/main/Database/Transaction.md),
[amazelimi](https://amazelimi.tistory.com/entry/DB-Dirty-Read-Non-Repeatable-Read-Phantom-Read-%EC%98%88%EC%8B%9C-%EB%B0%8F-Snapshot-Isolation-Level-LIM)
<br><br><br>



## Index
- Index란?
  - 테이블에 대한 동작의 속도를 높여주는 자료 구조를 일컫는다.
  - 테이블 내의 1개의 컬럼 혹은 여러 개의 컬럼을 이용하여 생성될 수 있다.
- Index의 장단점
  - 장점
    - 테이블을 조회하는 속도와 그에 따른 성능을 향상시킬 수 있다.
    - 전반적인 시스템의 부하를 줄 일 수 있다.
  - 단점
    - 인덱스를 관리하기 위해 DB의 약 10%에 해당하는 저장공간이 필요하다.
    - 인덱스를 관리하기 위해 추가 작업이 필요하다.
    - 인덱스를 잘못 사용하는 경우, 오히려 성능이 저하될 수 있다.
- Index의 자료구조
  - 인덱스를 구현하기 위해서는 다양한 자료구조를 사용할 수 있는데, 가장 대표적으로는 해시 테이블과 B+Tree가 존재한다.
    - 해시 테이블(Hash Table)
      - 해시 테이블은 (Key, Value)로 데이터를 저장하는 자료구조 중 하나로 빠른 데이터 검색이 필요할 때 유용하다.
      - 해시 테이블은 Key값을 이용해 고유한 index를 생성하여 그 index에 저장된 값을 꺼내오는 구조이다.
    - B+Tree
      - B+Tree는 DB의 인덱스를 위해 자식 노드가 2개 이상인 B-Tree를 개선시킨 자료구조이다.
      - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/b7bf6909-9b83-42fc-a262-6712d7c5fbe8)
      - B+Tree는 모든 노드에 데이터(Value)를 저장했던 BTree와 다른 특성을 가지고 있다.
        - 리프노드(데이터노드)만 인덱스와 함께 데이터(Value)를 가지고 있고, 나머지 노드(인덱스노드)들은 데이터를 위한 인덱스(Key)만을 갖는다.
        - 리프노드들은 LinkedList로 연결되어 있다.
        - 데이터 노드 크기는 인덱스 노드의 크기와 같지 않아도 된다.
- Ref.
[망나니개발자](https://mangkyu.tistory.com/96)
<br><br><br>



## SQL vs NoSQL
- SQL
  - 관계형 데이터베이스.
  - 데이터는 정해진 스키마에 따라 테이블에 저장된다.
- NoSQL
  - 비관계형 데이터베이스.
  - 반정형화, 비정형화된 데이터에 적합하다.
  - 대용량의 데이터 저장에 유리하다.
- Ref.
[bolee](https://velog.io/@octo__/SQL-vs-NoSQL),
[NKLCWDT](https://github.com/NKLCWDT/cs/blob/main/Database/RDBMSAndNoSQL.md)
<br><br><br>



## 파티셔닝(Partitioning)
- 파티셔닝(Partitioning)이란?
  - 테이블 또는 인덱스 데이터를 파티션(Partition) 단위로 나누어 저장하는 것을 말한다.
  - '파티셔닝(Partitioning)’기법을 통해 소프트웨어적으로 데이터베이스를 분산 처리하여 성능이 저하되는 것을 방지하고 관리를 보다 수월하게 할 수 있게 되었다.
- 파티셔닝의 목적
  - 성능(Performance)
    - 특정 DML과 Query의 성능을 향상시킨다.
    - 주로 대용량 Data WRITE 환경에서 효율적이다.
    - 특히, Full Scan에서 데이터 Access의 범위를 줄여 성능 향상을 가져온다.
  - 가용성(Availability)
    - 물리적인 파티셔닝으로 인해 전체 데이터의 훼손 가능성이 줄어들고 데이터 가용성이 향상된다.
    - 각 분할 영역(partition별로)을 독립적으로 백업하고 복구할 수 있다.
    - table의 partition 단위로 Disk I/O을 분산하여 경합을 줄이기 때문에 UPDATE 성능을 향상시킨다.
  - 관리용이성(Manageability)
    - 큰 table들을 제거하여 관리를 쉽게 해준다.
- 장단점
  - 장점
    - 전체 데이터를 손실할 가능성이 줄어들어 데이터 가용성이 향상된다.
    - partition별로 백업 및 복구가 가능하다.
    - partition 단위로 I/O 분산이 가능하여 UPDATE 성능을 향상시킨다.
    - 데이터 전체 검색 시 필요한 부분만 탐색해 성능이 증가한다. 즉, Full Scan에서 데이터 Access의 범위를 줄여 성능 향상을 가져온다.
    - 필요한 데이터만 빠르게 조회할 수 있기 때문에 쿼리 자체가 가볍다.
  - 단점
    - table간 JOIN에 대한 비용이 증가한다.
    - table과 index를 별도로 파티셔닝할 수 없다.
- 파티셔닝의 종류
  - 수평 파티셔닝
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/264c805b-cf30-4914-8c25-1e96e67a66de)
    - 하나의 테이블의 각 행을 다른 테이블에 분산시키는 것이다.
    - 퍼포먼스, 가용성을 위해 KEY 기반으로 여러 곳에 분산 저장한다.
    - 일반적으로 분산 저장 기술에서 파티셔닝은 수평 분할을 의미한다.
    - 보통 수평 분할을 한다고 했을 때는 하나의 데이터베이스 안에서 이루어지는 경우를 지칭한다.
    - 장단점
      - 장점
        - 데이터의 개수가 작아지고 따라서 인덱스의 개수도 작아지게 된다. 자연스럽게 성능은 향상된다.
      - 단점
        - 서버간의 연결과정이 많아진다.
        - 데이터를 찾는 과정이 기존보다 복잡하기 때문에 latency가 증가하게 된다.
        - 하나의 서버가 고장나게 되면 데이터의 무결성이 깨질 수 있다.
  - 수직 파티셔닝
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/ce48933f-b0a3-4776-994f-5ae747420c2b)
    - 테이블의 일부 열을 빼내는 형태로 분할한다.정규화도 수직 파티셔닝과 관련된 과정이라고 할 수 있다.
    - 수직 파티셔닝은 이미 정규화된 데이터를 분리하는 과정이라고 생각해야 한다.
    - 관계형 DB에서 3정규화와 같은 개념으로 접근하면 이해하기 쉽다.
    - 장단점
      - 장점
        - 자주 사용하는 컬럼 등을 분리시켜 성능을 향상시킬 수 있다.
        - 한 테이블을 SELECT하면 결국 모든 컬럼을 메모리에 올리게 되므로 필요없는 컬럼까지 올라가서 한 번에 읽을 수 있는 ROW가 줄어든다. 이는 I/O 측면에서 봤을 때 필요한 컬럼만 올리면 훨씬 많은 수의 ROW를 메모리에 올릴 수 있으니 성능상의 이점이 있다.
        - 같은 타입의 데이터가 저장되기 때문에 저장 시 데이터 압축률을 높일 수 있다.
      - 단점
        - 데이터를 찾는 과정이 기존보다 복잡하므로 Latency가 증가한다.
- Ref.
[James](https://velog.io/@kyeun95/%EB%8D%B0%EC%9D%B4%ED%84%B0-%EB%B2%A0%EC%9D%B4%EC%8A%A4-%ED%8C%8C%ED%8B%B0%EC%85%94%EB%8B%9DPartitioning%EC%9D%B4%EB%9E%80)
<br><br><br>



## Sharding
- Sharding이란?
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/e39102a1-6262-489c-bc22-5cd31cf8e3d0)
  - 샤딩은 각 DB 서버에서 데이터를 분할하여 저장하는 방식이다.
  - 샤딩(Sharding)은 DB 트래픽을 분산할 수 있는 중요한 수단이다.
- 파티셔닝과 샤딩의 관계
  - 샤딩은 수평 파티셔닝의 일종으로 볼 수 있다.
  - 그러나 수평적 파티셔닝은 동일한 DB 서버 내에서 테이블을 분할하는 것이고 샤딩은 DB 서버를 분할한다는 것이다.
- 장단점
  - 장점
    - Scale-Out이 가능하다.
    - 스캔 범위를 줄여서 쿼리 속도를 높일 수 있다.
    - 장애가 샤드 단위로 발생한다.
  - 단점
    - 프로그래밍 복잡도가 증가한다.
    - 데이터가 한쪽 샤드로 몰릴 경우, 샤딩이 무의미 해진다.
- 샤딩의 종류
  - 모듈러 샤딩(Modular Sharding)
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/de822d3c-6a63-4b7e-a397-feaf8d6100bf)
    - 모듈러 샤딩(Modular Sharding)은 PK를 모듈러 연산한 결과로 DB를 라우팅하는 방식이다.
  - 레인지 샤딩(Range Sharding)
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/8145d02a-f5ad-431a-bf37-4f9e47184c4d)
    - 레인지 샤딩(Range Sharding)은 PK의 범위를 기준으로 DB를 특정하는 방식이다.
  - 디렉토리 샤딩(Directory Sharding)
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/b95d1c1a-80fd-403d-9fb8-ef4e616f9ba9)
    - 디렉토리 샤딩(Directory Based Sharding)은 별도의 조회 테이블을 사용해서 샤딩을 하는 방식이다.
- Ref.
[James](https://velog.io/@kyeun95/%EB%8D%B0%EC%9D%B4%ED%84%B0%EB%B2%A0%EC%9D%B4%EC%8A%A4-%EC%83%A4%EB%94%A9Sharding%EC%9D%B4%EB%9E%80)
<br><br><br>



## DB Lock
- DB Lock
  - Database에 동시 접근이 일어난다면 데이터가 오염될 가능성이 있기 때문에, 데이터의 일관성과 무결성을 유지하기 위해 Lock을 사용한다.
- Lock의 종류
  - Shared Lock(공유략, Read Lock)
    - 공유락은 데이터를 읽을때 사용하는 Lock이다.
    - Read Lock 끼리는 데이터의 일관성과 무결성을 해치지 않기 때문에 동시에 접근이 가능하다.
    - 만약 특정 데이터에 Shared Locak 이 걸려있다면, 아래 Exclusive Lock을 걸 수 없고, 여러 Shared Lock은 동시에 적용될 수 있다.
  - Exclusive Lock(베타락, Write Lock)
    - 베타락은 데이터를 변경할대 사용하는 Lock이다.
    - 하나의 트랜잭션이 완료될때까지 유지되며, 베타락이 끝날때까지 어떠한 접근도 허용되지 않는다.
    - Exclusive Lock이 걸리면 Shared Lock을 걸 수 없다.
    - Exclusive 상태의 데이터에 대해 다른 트랜잭션이 Exclusive Lock을 걸 수 없다.
- Lock 단위
  - Row Level
    - Row에만 락을 설정한다.
    - 가장 많이 사용되는 Lock이다.
  - Page Level
    - Row가 담긴 Page 에만 락을 설정한다.
    - 같은 페이지에 존재하는 모든 Row는 모두 잠긴다.
  - Table Level
    - Table 과 Index 모두에 락을 설정한다.
    - 전체 테이블에 대한 데이터 변경이 있을 경우 사용한다.
    - 테이블을 제어하는 DDL 구문을 사용할때 Lock이 걸린다고 하여, DDL Lock 이라고도 한다.
  - Database Level
    - Database의 복구나 스키마 변경 시 락을 설정한다.
    - 1개의 세션이 하나의 Database의 데이터에 접근할 수 있다.
    - DB 전체에 영향이 있는 DB 업데이트와 같은 작업에만 사용한다.
  - Column Level
    - 컬럼 기준으로 Lock이 걸린다.
    - Lock 설정 및 해제에 리소스가 많이들어 잘 사용하지 않는다.
- 블로킹(Blocking)
  - Lock 간의 경합(Race Condition)이 발생하여 특정 Transaction이 작업을 진행하지 못하고 멈춰선 상태를 말한다.
  - 공유락끼리는 블로킹이 발생하지 않지만, 베타락은 블로킹을 발생시킨다.
  - (Shared Lock + Exclusive Lock) 또는 (Exclusive Lock + Exclusive Lock) 끼리 블로킹이 발생할 수 있다.
  - 해결방안
    - SQL문이 빠르게 수행될 수 있도록 리팩토링한다.
    - 트랜잭션을 가능한 짧게 정의하여 경합을 줄인다.
    - 동일한 데이터를 동시에 변경하지 않도록 설계한다.
    - LOCK_TIMEOUT을 설정하여 해당 Lock의 최대시간을 조정한다.
- 교착상태(DeadLock)
  - 교착상태는 두 트랜잭션이 각각 Lock을 설정하고 서로의 Lock에 접근하여 값을 얻어오려고 할 때, 이미 각각의 트랜잭션에 의해 Lock이 설정되어 있기 때문에 양쪽 트랜잭션 모두 영원히 처리가 되지않게 되는 상태를 뜻한다.
  - 발생상황
    - Shared Lock + Exclusive Lock
      - 트랜잭션 A가 Shared Lock을 설정하고 sleep 되었을때, 트랜잭션 B가 해당 데이터에 Exclusive Lock을 걸려고 하면 무기한 기다려야하는 교착상태에 빠진다.      
    - Exclusive Lock + Exclusive Lock
      - 트랜잭션 A에서 Exclusive Lock을 걸었을때 트랜잭션 B에서도 다른 데이터에 Exclusive Lock을 걸었을 경우 서로의 Lock된 데이터에 접근하려고할 때 기존의 Lock이 해제될 때까지 기다리게된다.
  - 해결방안
    - Dead Lock이 감지되면 둘 중 하나의 트랜잭션을 강제 종료한다.
    - Dead Lock 방지를 위해 접근 순서를 동일하게 하는 것이 중요하다.
- Ref.
[NKLCWDT](https://github.com/NKLCWDT/cs/blob/main/Database/Lock.md),
[Hyun / Log](https://hstory0208.tistory.com/entry/%EB%9D%BDLock%EC%9D%B4%EB%9E%80-Lock%EC%9D%98-%EC%A2%85%EB%A5%98%EC%99%80-%EA%B5%90%EC%B0%A9%EC%83%81%ED%83%9CDeadLock)
<br><br><br>





<br><br><br>
- - -
<br><br><br>





# CS
## OSI 7계층과 TCP/IP 4계층
- OSI 7계층과 TCP/IP 4계층
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/8f74cf13-703e-43a9-89d2-bd9543525acd)
- OSI 7계층이란?
  - 네트워크 통신이 일어나는 과정을 7단계로 나눈 국제 표준화 기구(ISO)에서 정의한 네트워크 표준 모델이다.
  - 이 모델은 프로토콜을 기능별로 나눈 것이다.
- OSI 7계층 - 계층별 특징
  - 물리 계층(Physical)
    - 전기적, 기계적, 기능적인 특성을 이용하여 통신 케이블로 데이터를 전송한다.
    - 사용되는 통신 단위는 비트(bit)이며, 0또는 1만 나타낼 수 있다.
    - 단지 데이터를 전달만 할 뿐 전송하려는, 또는 받으려는 데이터가 무엇인지는 전혀 신경쓰지 않는다.
    - 대표적인 장치로 통신 케이블, 리피터, 허브 등이 있다.
  - 데이터 링크 계층(Data Link)
    - 물리 계층을 통해 송수신되는 정보의 오류와 흐름을 관리하여 안전한 정보의 수행을 도와주는 역할을 한다.
    - 맥 주소(MAC Address)를 가지고 통신한다.
    - 전송되는 단위를 프레임(frame)이라고 하며, 대표적인 장비로는 브리지, 스위치 등이 있다.
  - 네트워크 계층(Network)
    - 경로를 선택하고 주소를 정하고 경로에 따라 패킷을 전달해주는 역할을 한다.
    - 데이터를 목적지까지 가장 안전하고 빠르게 전달하는 기능(라우팅)을 한다.
    - 대표적인 장비로 라우터, (라우팅 기능이 포함된)스위치가 있으며, IP 주소를 사용한다.
    - 데이터를 연결하는 다른 네트워크를 통해 전달함으로써 인터넷이 가능하게 만드는 계층이다.
  - 전송 계층(Transport)
    - 통신을 활성화하기 위한 계층이다. 보통 TCP 프로토콜을 사용하며, 포트를 열어서 응용 프로그램을 전송한다.
    - 양 끝단의 사용자들이 신뢰성 있는 데이터를 주고 받을 수 있게 해 주어, 상위 계층들이 데이터 전달의 유효성이나 효율성을 생각하지 않도록 한다.
  - 세션 계층(Session)
    - 데이터가 통신하기 위한 논리적인 연결을 한다.
    - 세션 설정, 유지, 종료, 전송 중단시 복구 등의 기능이 있다.
    - 양 끝단의 응용 프로세스가 통신을 관리하기 위한 방법을 제공한다.
    - TCP/IP 세션을 만들고 없애는 책임을 진다.
  - 표현 계층(Presentation)
    - 데이터 표현이 상이한 응용 프로세스의 독립성을 제공하고, 암호화한다.
    - 코드 간의 번역을 담당하여 사용자 시스템에서 데이터의 형식상 차이를 다루는 부담을 응용 계층으로 덜어준다.
    - 해당 데이터가 텍스트인지, 그림인지, GIF인지, JPG인지의 구분 등의 역할을 한다.
  - 응용 계층(Application)
    - 최종 목적지로서 HTTP, FTP, SMTP, Telnet 등과 같은 프로토콜이 있다.
    - 응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행한다.
- TCP/IP 4계층이란?
  - 네트워크 전송 시 데이터 표준을 정리한 것이 OSI 7계층이었다면, 이 이론을 실제로 사용하는 인터넷 표준이 TCP/IP 4계층이다.
- TCP/IP 4계층 - 계층별 특징
  - 네트워크 인터페이스 계층(Network Access/Network Interface)
    - OSI 계층의 1,2 계층에 해당된다.
    - TCP/IP 패킷을 네트워크 매체로 전달하는 것과 네트워크 매체에서 TCP/IP 패킷을 받아들이는 과정을 담당한다.
    - 에러 검출 기능과 패킷의 프레임화 기능을 수행한다.
    - 흐름 제어(Flow Control)는 Header(MAC)에서, 에러 제어(Error Control)는 Tailer(CRC)에서 수행한다.
  - 인터넷 계층(Internet)
    - OSI 계층에서 3계층에 해당된다.
    - 어드레싱(addressing), 패키징(packaging), 라우팅(routing) 기능을 제공한다.
    - 논리적 주소인 IP를 이용한 노드간 전송과 라우팅 기능을 처리하게 된다.
    - 네트워크상 최종 목적지까지 정확하게 연결되도록 연결성을 제공한다.
    - 핵심 프로토콜은 IP, ARP, ICMP, IGMP 등이 있다.
  - 전송 계층(Transport)
    - OSI 계층에서 3,4 계층에 해당된다.
    - 자료의 송수신을 담당한다.
    - 어플리케이션 계층의 세션과 데이터그램 통신서비스를 제공한다.
    - TCP/UDP가 핵심 프로토콜이다. TCP/UDP에 대한 구분을 하고 데이터에 대한 제어 정보가 여기에 포함된다.
  - 응용 계층(Application)
    - 다른 계층의 서비스에 접근할 수 있게 하는 어플리케이션을 제공한다.
    - 어플리케이션들이 데이터를 교환하기 위해 사용하는 프로토콜을 정의한다.
    - TCP/IP 네트워크를 사용하거나 관리하는 것을 도와주는 프로토콜이다.
- Ref.
[DevOwen](https://devowen.com/344)
<br><br><br>



## TCP vs UDP
- TCP(Transmission Control Protocol)
  - TCP는 신뢰성 있는 데이터 전송을 지원하는 연결 지향형 프로토콜이다.
  - 일반적으로 TCP와 IP가 함께 사용되는데, IP가 데이터의 전송을 처리한다면 TCP는 패킷을 추적하고 관리하는 역할을 한다.
  - 연결 지향형인 TCP는 3-way handshaking이라는 과정을 통해 연결 후 통신을 시작하는데, 흐름 제어와 혼잡 제어를 지원하며 데이터의 순서를 보장한다.
  - UDP에 비하여 전송속도가 느리다.
  - 신뢰성이 높다.
- UDP(User Datagram Protocol)
  - UDP는 비연결형 프로토콜이다.
  - 인터넷상에서 서로 정보를 주고받을 때, 신호 절차를 거치지 않고 보내는 쪽에서 일방적으로 데이터를 전달하는 통신 프로토콜이다.
  - TCP와는 다르게 연결 설정이 없으며, 혼잡 제어를 하지 않기 때문에 TCP보다 전송 속도가 빠르다.
  - 데이터 전송에 대한 보장을 하지 않기 때문에 패킷 손실이 발생할 수 있다.
  - 패킷 오버헤드가 적어 네트워크 부하가 감소한다.
  - 신뢰성이 낮다.
- Ref.
[코딩 공부 일지](https://cocoon1787.tistory.com/757)
<br><br><br>



## 3-Way handshake & 4-Way hadnshake
- 3-Way Handshake란?
  - TCP/IP 프로토콜을 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 뜻한다.
- 3-Way Handshake의 동작 순서
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/205cb3fd-340a-43d3-be51-5acaacb663d6)
  - Step1. SYN
    - Client가 Server에게 접속을 요청하는 SYN플래그를 보낸다.
  - Step2. SYN + ACK
    - Server는 Listen상태에서 SYN이 들어온 것을 확인하고 SYN_RECV상태로 바뀌어 SYN + ACK플래그를 Client에게 전송한다.
    - 그 후 Server는 다시 ACK 플래그를 받기 위해 대기상태로 변경된다.
  - Step3. ACKSYN + ACK
    - SYN + ACK 상태를 확인한 Client는 서버에게 ACK를 보내고 연결 성립(Established)이 된다.
- 4-Way Handshake란?
  - 3-Way handshake가 연결확립을 위해 진행했다면 4way handshake는 세션을 종료하기 위해 수행되는 절차를 뜻한다.
- 4-Way Handshake의 동작 순서
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/41c81252-70d4-4856-a598-bb5ce59aa11d)
  - Step1. FIN
    - Client가 연결을 종료하겠다는 FIN플래그를 전송한다.
    - 보낸 후에 FIN-WAIT-1 상태로 변한다.
  - Step2. ACK
    - FIN 플래그를 받은 Server는 확인메세지인 ACK를 Client에게 보내준다.
    - 그 후 CLOSE-WAIT상태로 변한다.
    - Client도 마찬가지로 Server에서 종료될 준비가 됐다는 FIN을 받기위해 FIN-WAIT-2 상태가 된다.
  - Step3. FIN
    - Close준비가 다 된 후 Server는 Client에게 FIN 플래그를 전송한다.
  - Step4. ACK
    - Client는 해지 준비가 되었다는 정상응답인 ACK를 Server에게 보내준다. 이 때, Client는 TIME-WAIT 상태로 변경된다.
    - 여기서 TIME-WAIT 상태는 의도치않은 에러로 인해 연결이 데드락으로 빠지는 것을 방지하기 위해 변경 되는 것인데, 만약 에러로 인해 종료가 지연되다가 타임이 초과되면 CLOSED 상태로 변경된다.
- Ref.
[나의 과거일지](https://jeongkyun-it.tistory.com/180)
<br><br><br>



## 교착상태(Deadlock)
- 교착상태란?
  - 일련의 프로세스들이 서로가 가진 자원을 기다리며 block되어, 더 이상 진행이 될 수 없는 상태를 의미한다.
  - 즉, 둘 이상의 프로세스가 다른 프로세스가 점유하고 있는 자원을 서로 기다릴 때 무한 대기에 빠지는 상황을 일컫는다.
- 교착상태 발생조건
  - 다음의 4가지 조건을 모두 성립해야 데드락이 발생한다.
  - 상호 배제
    - 매 순간 하나의 프로세스만이 자원을 사용할 수 있다.
  - 점유 대기
    - 자원을 가진 프로세스가 다른 자원을 기다릴 때, 보유하고 있는 자원을 놓지 않고 계속 가지고 있다.
  - 비선점
    - 프로세스는 OS에 의해 강제로 자원을 빼앗기지 않는다.
    - 즉, 자원을 강제로 빼앗는게 아니라, 자원을 점유하고 있는 프로세스가 해당 자원을 해제해야 한다는 것이다.
  - 순환 대기
    - 자원을 기다리는 프로세스 간에 사이클이 형성어되야 한다.
- 교착상태 해결법
  - 데드락 예방(Prevention)
    - 자원의 상호 배제 조건 방지
      - 한 번에 여러 프로세스가 공유 자원을 사용할 수 있게한다. (단, 동기화 관련 문제가 발생할 수 있다.)
    - 점유 대기 조건 방지
      - 프로세스 실행에 필요한 모든 자원을 한꺼번에 요구하고 허용할 때까지 작업을 보류해서, 나중에 또다른 자원을 점유하기 위한 대기 조건을 성립하지 않도록 한다.
    - 비선점 조건 방지
      - 이미 다른 프로세스에게 할당된 자원이 선점권이 없다고 가정할 때, 높은 우선순위의 프로세스가 해당 자원을 선점할 수 있도록 한다.
    - 순환 대기 조건 방지
      - 자원을 순환 형태로 대기하지 않도록 일정한 한 쪽 방향으로만 자원을 요구할 수 있도록 한다.
  - 데드락 회피(Avoidance)
    - 데드락 회피법에서는 Safe sequence, Safe state 등이 키워드이다.
    - 시스템의 프로세스들이 요청하는 모든 자원을, 데드락을 발생시키지 않으면서도 차례로 모두에게 할당해 줄 수 있다면 안정 상태(safe state)에 있다고 말한다.
    - 그리고 이처럼 특정한 순서로 프로세스들에게 자원을 할당, 실행 및 종료 등의 작업을 할 때 데드락이 발생하지 않는 순서를 찾을 수 있다면, 그것을 안전 순서(safe sequence)라고 부른다.
    - 회피 알고리즘(Ex. 은행원 알고리즘)을 통해 자원을 할당한 후에도 시스템이 항상 Safe state에 있을 수 있도록 할당을 허용하자는 것이 기본 특징이다.
  - 데드락 탐지(Detection) 및 회복(Recovery)
    - 시스템이 데드락 예방이나 회피법을 사용하지 않았을 때, 데드락이 발생할 수 있으니 여기에서 회복하기 위해 데드락을 탐지하고, 회복하는 알고리즘을 사용한다.
    - 탐지 기법
      - Allocation, Request, Available 등으로 시스템에 데드락이 발생했는지 여부를 탐색한다.
      - 즉, 은행원 알고리즘에서 했던 방식과 유사하게 현재 시스템의 자원 할당 상태를 가지고 파악한다.
      - 이 외에도 자원 할당 그래프를 통해 탐지하는 방법도 있다.
    - 회복 기법
      - 데드락을 탐지 기법을 통해 발견했다면, 순환 대기에서 벗어나 데드락으로부터 회복하기 위한 방법을 사용한다.
        - 단순히 프로세스를 1개 이상 중단시키기
          - 교착 상태에 빠진 모든 프로세스를 중단시키는 방법
            - 계속 연산중이던 프로세스들도 모두 일시에 중단되어 부분 결과가 폐기될 수 있는 부작용이 발생할 수 있다.
          - 프로세스를 하나씩 중단 시킬 때마다 탐지 알고리즘으로 데드락을 탐지하면서 회복시키는 방법
            - 매번 탐지 알고리즘을 호출 및 수행해야 하므로 부담이 되는 작업일 수 있다.
        - 자원 선점하기
          - 프로세스에 할당된 자원을 선점해서, 교착 상태를 해결할 때까지 그 자원을 다른 프로세스에 할당해준다.
- Ref.
[zioo](https://velog.io/@zioo/Deadlock%EA%B5%90%EC%B0%A9-%EC%83%81%ED%83%9C%EC%9D%98-%EA%B0%9C%EB%85%90%EA%B3%BC-%EB%B0%9C%EC%83%9D-%EC%9B%90%EC%9D%B8), 
[ChanBLOG](https://chanhuiseok.github.io/posts/cs-2/),
[Gyoogle](https://github.com/gyoogle/tech-interview-for-developer/blob/b478de0481da8227913c647afb004c5d39c0718e/Computer%20Science/Operating%20System/DeadLock.md)
<br><br><br>



## 뮤텍스와 세마포어
- 임계 영역(Critical Section)이란?
  - 여러 프로세스가 데이터를 공유하며 수행될 때, 각 프로세스에서 공유 데이터를 접근하는 프로그램 코드 블록을 뜻한다.
  - 즉, 여러 프로세스가 동일 자원을 동시에 참조하여 값(공유하는 변수명, 파일 등)이 오염될 위험 가능성이 있는 영역이다.
- 뮤텍스(Mutex)와 세마포어(Semaphore)란?
  - 프로세스 간 메시지를 전송하거나, 공유메모리를 통해 공유된 자원에 여러 개의 프로세스가 동시에 접근하면 Critical Section 문제가 발생할 수 있다.
  - 이를 해결하기 위해 데이터를 한 번에 하나의 프로세스만 접근할 수 있도록 제한을 두는 동기화 방식을 취해야 하는데, 대표적인 동기화 도구에는 뮤텍스와 세마포어가 있다.
- 뮤텍스(Mutex)
  - 동시 프로그래밍에서 공유 불가능한 자원의 동시 사용을 피하기 위해 사용하는 알고리즘이다.
  - 임계구역(Critical Section)을 가진 스레드들의 실행시간(Running Time)이 서로 겹치지 않고 각각 단독으로 실행되도록 하는 기술이다.
  - 한 프로세스에 의해 소유될 수 있는 Key를 기반으로 한 상호배제 기법이다.
  - 다중 프로세스들의 공유 리소스에 대한 접근을 조율하기 위해 동기화(Synchronization) 또는 락(Lock)을 사용한다.
  - 뮤텍스 객체를 두 스레드가 동시에 사용할 수 없다.
- 세마포어(Semaphore)
  - 멀티 프로그래밍 환경에서 공유된 자원에 대한 접근을 제한하는 방법이다.
  - 사용하고 있는 스레드/프로세스의 수를 공통으로 관리하는 하나의 값을 이용해 상호배제를 달성한다.
  - 공유 자원에 접근할 수 있는 프로세스의 최대 허용치만큼 동시에 사용자가 접근할 수 있다.
  - 각 프로세스는 세마포어의 값을 확인하고 변경할 수 있다.
  - 자원을 사용하지 않는 상태가 될 때, 대기하던 프로세스가 즉시 자원을 사용한다.
  - 이미 다른 프로세스에 의해 사용중이라는 사실을 알게 되면, 재시도 전에 일정시간 대기해야 한다.
  - 세마포어를 사용하는 프로세스는 그 값을 확인하고, 자원을 사용하는 동안에는 그 값을 변경함으로써 다른 세마포어 사용자들이 대기하도록 해야 한다.
  - 세마포어는 이진수를 사용하거나 추가적인 값을 가질 수 있다.
- 뮤텍스(Mutex)와 세마포어(Semaphore)의 차이점
  - 가장 큰 차이점은 동기화 대상의 갯수이다. 뮤텍스는 동기화 대상이 오직 1개일 때 사용하고, 세마포어는 동기화 대상이 1개 이상일 때 사용한다.
  - 세마포어는 뮤텍스가 될 수 있지만, 뮤텍스는 세마포어가 될 수 없다.
  - 뮤텍스는 자원 소유가 가능한 반면에 세마포어는 자원 소유가 불가능하다.
  - 뮤텍스는 소유하고 있는 스레드만이 이 뮤텍스를 해제할 수 있지만 세마포어는 세마포어를 소유하지 않은 스레드가 세마포어를 해제할 수 있다.
  - 세마포어는 시스템 범위에 걸쳐있고, 파일 시스템상에 파일로 존재하는 반면에 뮤텍스는 프로세스의 범위를 가지며 프로세스가 종료될 때 자동으로 Clean up된다.
- Ref.
[굳세게 코딩하는 단발머리 첼씨✨](https://chelseashin.tistory.com/40)
<br><br><br>



## 프로세스와 스레드의 차이
- 프로세스(Process)란?
  - 운영체제로부터 시스템 자원을 할당받아 실행되는 프로그램 단위를 뜻한다.
  - 즉, 독립적인 메모리 영역을 가지며, 다른 프로세스와는 독립적으로 실행된다.
  - 프로세스는 각각의 프로세스 ID(PID)를 가지고, 프로세스 간 통신(IPC)을 이용하여 통신할 수 있다.
- 스레드(Thread)란?
  - 프로세스 내에서 실행되는 작업 단위를 뜻한다.
  - 한 프로세스 내에서 여러 개의 스레드가 동시에 실행될 수 있으며, 각 각의 스레드는 프로세스의 메모리 공간을 공유한다.
  - 즉, 스레드는 하나의 프로세스 내에서 독립적으로 실행되지 않으며, 다른 스레드와 메모리를 공유한다.
- 차이점
  - 프로세스는 각각의 독립적인 메모리 공간을 할당받아 실행되므로, 프로세스 간의 자원 공유나 통신을 위해서는 별도의 IPC 기법을 사용해야 하지만
    스레드는 같은 프로세스 내에서 메모리를 공유하기 때문에, 스레드 간의 자원 공유나 통신이 비교적 쉽다.
  - 프로세스는 각각의 독립적인 메모리 공간을 할당받아 실행되므로, 하나의 프로세스가 비정상적으로 종료되더라도 다른 프로세스에는 영향을 주지 않지만
    스레드는 같은 프로세스 내에서 실행되기 때문에, 한 스레드에서 예외가 발생하면 다른 스레드에도 영향을 줄 수 있다.
- Ref.
[윤개승발](https://yuniday2.tistory.com/85),
[aeong98](https://velog.io/@aeong98/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9COS-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EC%8A%A4%EB%A0%88%EB%93%9C)
<br><br><br>



## 단방향 암호화와 양방향 암호화
- 암호화란?
  - 평문을 특정 키를 사용해서 해독할 수 없는 형태로 변경하는 것을 뜻한다.
  - 암호화 방식에는 단방향 암호화와 양방향 암호화 방식이 있다.
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/2a8f6ab3-a3f9-4046-897c-cf182b606f3f)
- 단방향 암호화
  - 평문을 암호화하는 것은 가능하지만 암호문을 평문으로 복호화할 수 없는 기법.
  - 대표적으로 HASH를 사용한 방식이 있다.
- 양방향 암호화
  - 암호문을 평문으로 복호화할 수 있는 기법.
  - 양방향 암호화는 크게 대칭키(비공개키)와 비대칭키(공개키)방식으로 나눠진다.
  - 대칭키 방식은 암호화, 복호화시 모두 동일한 키를 사용하고, 비대칭키(공개키)방식은 암호화 복호화에 서로 다른 키를 사용한다.
   - 대칭키(비공개키) 방식
      - 암/복호화에 서로 동일한 키가 사용되는 암호화 방식.
      - 장점
        - 비대칭키보다 속도가 빠르다.
      - 단점
        - 키를 교환해야하는 키 배송 문제가 발생한다.
        - 키를 교환하는 도중에 키가 탈취될 수 있다.
        - 사람이 증가할수록 각자 따로 키를 교환해야하므로 관리해야할 키가 방대해진다.
      - 종류
        - AES, DES 알고리즘
    - 비대칭키(공개키) 방식
      - 암/복호화에 다른 키가 사용되는 방식
      - 노출시켜도 상관없는 Public Key와 노출시켜서는 안되는 Private Key로 구성된다.
      - 장점
        - 공개키는 공개되어있기 떄문에 키 교환이 필요없다.
        - 개인키를 가지고 있는 수신자만이 복호화할 수 있으므로 인증 기능을 할 수 있다.
      - 단점
        - 대칭키 방식에 비해 속도가 느리다.
      - 종류
        - RSA 알고리즘
- Ref.
[jummi10.log](https://velog.io/@jummi10/%EB%8B%A8%EB%B0%A9%ED%96%A5-%EC%95%94%ED%98%B8%ED%99%94-vs-%EC%96%91%EB%B0%A9%ED%96%A5-%EC%95%94%ED%98%B8%ED%99%94),
[자바공작소](https://javaplant.tistory.com/26)
<br><br><br>



## 고정 소수점과 부동 소수점
- 실수의 표현 방식
  - 컴퓨터에서 실수를 표현하는 방법에는 크게 고정 소수점 방식과 부동 소수점 방식이 있다.
- 고정 소수점 방식
  - 정수를 표현하는 비트와 소수를 표현하는 비트 수를 미리 고정하고 해당 비트만을 활용하여 실수를 표현한다.
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/3eb00f8f-fde6-4719-89d4-dd01b6553b85)
    - 처음 1비트는 sign(부호)을 나타낸다. (0은 양수, 1은 음수)
    - 다음 15비트는 integer part(정수부)를 나타낸다.
    - 다음 16비트는 fractional part(소수부)를 나타낸다.
  - 장점
    - 표현하는 방법이 단순하다.
    - 연산속도가 빠르다.
  - 단점
    - 표현할 수 있는 범위가 적다.
    - 정밀도가 낮다.
- 부동 소수점 방식
  - 정수를 표현하는 비트와 소수를 표현하는 비트 수가 유동적이다.
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/e1c374d0-b98e-4924-ae1d-e4a053110623)
    - 2진수를 정규화 한다.
    - 처음 1비트는 sign(부호)를 나타낸다. (0은 양수, 1은 음수)
    - 다음 8비트는 exponent(지수부)를 나타낸다.
    - 다음 23비트는 mantissa(가수부)를 나타낸다.
  - 장점
    - 더 큰 실수를 표현할 수 있다.
  - 단점
    - 실수 연산이 부정확할 수 있다.
      - 예를 들어 십진수 0.3을 2진수로 변환하면 0.0100110011...(2) 처럼 특성 수가 무한이 반복된다. 따라서 컴퓨터가 실수 부분을 표현할 수 있는 비트 수를 다 써버리게 되어 근사치로 표현되게 된다.
- 부동 소수점의 저장
  - 부동 소수점은 근사값으로 표현되기 때문에 오차가 발생하기도 한다.
    - JAVA에서의 오차 해결
      - BigDecimal 클래스를 사용한다.
    - DB에서의 오차 해결
      - DECIMAL타입을 사용하여 부동 소수점을 고정 소수점 방식으로 사용한다.
- Ref.
[MeongKune_Developer](https://velog.io/@meongkune/%EA%B3%A0%EC%A0%95-%EC%86%8C%EC%88%98%EC%A0%90-vs.-%EB%B6%80%EB%8F%99-%EC%86%8C%EC%88%98%EC%A0%90),
[MJ](https://velog.io/@devp1023/%EC%88%98%ED%95%99-%EA%B3%A0%EC%A0%95-%EC%86%8C%EC%88%98%EC%A0%90%EA%B3%BC-%EB%B6%80%EB%8F%99-%EC%86%8C%EC%88%98%EC%A0%90),
[bahngju의 개발 블로그](https://bahngju.tistory.com/8),
[WOONY's 인사이트](https://woonys.tistory.com/279)
<br><br><br>





<br><br><br>
- - -
