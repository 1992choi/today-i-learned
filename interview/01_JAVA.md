## Java의 특징
- 객체 지향 언어로써 캡슐화, 상속, 다형성 기능을 완벽하게 지원한다.
- JVM에서 동작하기 때문에 운영체제와 상관없이 독립적으로 작동하여 이식성이 높다.
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
  - 객체의 공통적인 속성과 행위를 추출하여 정의하는 것을 말한다.
  - 공통적인 속성과 행위를 모아 정의하면, 반복적인 코드를 줄일 수 있고, 보다 효과적인 클래스 간의 관계를 설정하여 유지보수가 용이해진다.
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
  ``` java
  public class Animal { // 클래스
      // ...
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
    - ``` java
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
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/6568409b-fdd3-4ab7-9e77-1410f542f1f8)
- 박싱(Boxing) / 언박싱(UnBoxing)
  - Boxing은 기본 타입의 값을 래퍼 클래스로 변환하는 것을 의미한다.
  - Unboxing은 래퍼 클래스를 기본 타입으로 변환하는 것을 의미한다.
  - ``` java
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
  - ``` java
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
  - ``` java
    abstract class Animal {
        abstract void cry();
    }
    ```
  - ``` java
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
  - ``` java
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
  - 인터페이스 안의 모든 추상메서드는 public abstract 타입이다. (생략 가능)
  - 추상클래스와 마찬가지로 인스턴스를 생성할 수 없다.
  - 인터페이스는 다른 인터페이스를 extends 키워드로 상속받을 수 있으며, 다중 상속이 가능하다.
  - 클래스에서 인터페이스의 구현은 implements 키워드를 사용하여 구현할 인터페이스를 지정 후, 추상메서드를 모두 오버라이드하여 내용을 완성해야 한다.
- 인터페이스 장점
  - 개발시간을 단축시킬 수 있다.
    - 인터페이스가 작성되면, 메서드를 호출하는 쪽에서는 선언부만 알면 되기 때문에 구현부의 완성여부와 상관없이 작업을 동시에 진행할 수 있다.
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
  - Java 컴파일러에서 오버로딩된 함수들은 메서드 시그니처를 통해 식별한다.
    - 메서드 시그니처란 메서드명과 매개변수의 자료형을 의미한다.
    - 메서드의 반환 타입은 해당되지 않는다.
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
        - 메모리 고속 복사 연산을 사용한다.
          - 중간 위치에 데이터를 추가할 경우, 추가할 위치 이후의 데이터를 모두 한 칸씩 뒤로 이동시키는 작업을 해야한다.
          - 이 때, 배열의 요소 이동은 시스템 레벨에서 최적화된 메모리 고속 복사 연산을 사용하여 비교적 빠르게 수행된다.
            - System.arraycopy() 사용
      - LinkedList
        - 순차 접근만 가능하여 조회할 때는 불리하지만, 양방향 포인터 구조이기 때문에 데이터의 삽입, 삭제 시에는 유리하다.            
        - 마지막 노드에 대한 참조
          - 순차 접근만 가능하여 배열의 가장 마지막에 데이터를 추가할 때는 이론상 O(n)이 소요되지만, 실제로는 마지막 노드에 대한 참조를 가지고 있어 O(1)의 성능을 제공한다.
        - 마지막 노드를 가지고 있으며 양방향 포인터 구조의 특징 덕분에 사이즈의 절반 크기 이상의 인덱스를 조회할 경우, 뒤에서부터 조회하여 성능을 최적화 할 수 있다.
      - Vector
        - ArrayList와 구현 원리와 기능적인 측면에서 동일하며, 동기화를 지원한다.
    - 시간복잡도
      - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/c3c4f910-beb9-4a2b-988b-30b5ad30d966)
    - 시간 복잡도와 실제 성능
      - 이론적으로 LinkedList의 중간 삽입 연산은 ArrayList보다 빠르다.
      - 그러나 실제 성능은 요소의 순차적 접근 속도, 메모리 할당 및 해제 비용, CPU 캐시 활용도 등 다용한 요소에 의해 결정된다.
        - ArrayList의 경우 요소들이 메모리상에 연속적으로 위치하여 CPU 캐시 효율이 좋고 메모리 접근 속도가 빨라 LinkedList보다 빠를 수 있다.
      - 배열 첫 번째에서 삽입/삭제가 발생하는 경우를 제외하고는 실제 성능은 ArrayList가 더 나은 성능을 보여주는 경우가 많다.
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
    - 시간복잡도
      - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/c2ffd676-f00c-4f06-a20c-ccaea5886118)
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
    - 시간복잡도
      - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/c78422a1-bb45-4909-abf8-d908ff6b0b12)
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/129),
[Medium](https://yogeshkkhichi.medium.com/time-and-space-complexity-of-collections-5a00c7b1d32b)
<br><br><br>



## 람다식(Lambda Expression)
- 람다식(Lambda Expressions) 이란?
  - 람다식이란 프로그래밍 언어에서 사용되는 개념으로 익명 함수를 지칭하는 용어이다.
  - 메서드를 람다식으로 표현하면 메서드의 이름 없이 사용할 수 있게 되는데, 이 때문에 익명 함수라고도 불린다.
  - 람다식은 자바 8부터 사용 가능하며, 이로 인하여 자바에서도 함수형 프로그래밍이 가능하게 되었다.
- 장/단점
  - 장점
    - 코드를 간결하게 만들 수 있다.
    - 식에 개발자의 의도가 명확히 드러나기 때문에 가독성이 높아진다.
    - 메서드를 만드는 과정없이 한 번에 처리할 수 있기 때문에 생산성이 높아진다.
    - 병렬프로그래밍이 용이하다.
  - 단점
    - 람다를 사용하면서 만든 익명 함수는 재사용이 불가능하다.
    - 디버깅이 어렵다.
    - 익명 함수는 재사용이 불가능하기 때문에 람다를 무분별하게 사용할 경우, 비슷한 함수가 중복 생성될 수 있다.
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
  - 함수형 인터페이스의 목적은 자바에서 람다 표현식을 이용해 함수형 프로그래밍을 구현하기 위함이다.
  - 함수형 인터페이스를 표현하기 위하여 @FunctionalInterface 어노테이션을 사용할 수 있다. 해당 어노테이션을 붙여주면 두 개 이상의 메서드 선언 시 컴파일 오류를 발생시켜 개발자의 실수를 줄일 수 있다.
  - 자주 사용할 것 같은 람다 함수 형태를 함수형 인터페이스 표준 API로 미리 만들어 제공해준다.
- 종류
  - Consumer
    - 한 개의 입력을 받아서 결과를 반환하지 않는 함수를 정의한다.
    - void accept(T t) 메서드를 가지며, 이 메서드는 매개변수 T를 받아서 아무런 결과도 반환하지 않는다.
    - 주로 입력값을 이용한 연산이나 출력 등의 동작에 사용된다.
  - Supplier
    - 입력 없이 결과를 반환하는 함수를 정의한다.
    - T get() 메서드를 가지며, 이 메서드는 아무런 매개변수를 받지 않고 결과 T를 반환한다.
    - 파라미터 없이 특정 결과를 생성하는데 사용된다.
  - Function
    - 한 개의 입력을 받아서 결과를 매핑하여 반환하는 함수를 정의한다.
    - R apply(T t) 메서드를 가지며, 이 메서드는 매개변수 T를 받아서 R타입의 결과를 반환한다.
    - 주로 T 타입의 객체를 받아 다른 형태 R로 변환하는데 사용된다.
  - Predicate
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
      - 스트림에서 지정한 첫 번째 요소를 찾는 메서드
      - parallelStream()와 함께 사용
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
  - [샘플코드](https://github.com/1992choi/java/blob/master/src/basic/clazz/object/EqualsEx.java)
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/135)
<br><br><br>



### try / catch / finally
- finally
  - finally는 catch에서 잡지못하는 Exception이 발생하여도 무조건 실행된다.
- Try-with-resources를 통한 자원 해제의 장점
  - 리소스 누수 방지
    - 실수로 finally를 작성하지 않는 실수를 막아준다.
  - 가독성 향상
    - close()가 없어 코드가 더 간결하고 읽기 쉬워진다.
  - 스코프 범위 한정
    - 리소스로 사용되는 변수의 스코프가 try로만 한정되어 코드 유지보수가 더 쉬워진다.
  - 조금 더 빠른 자원해제
    - 기존 방식 : catch 이후 자원 반납
    - Try-with-resources : try 블럭이 끝남과 동시에 반납 후 catch 구문 실행
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
    - ``` java
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



## 프로세스와 스레드
- 프로세스(Process)란?
  - 운영체제로부터 시스템 자원을 할당받아 실행되는 프로그램 단위를 뜻한다.
  - 즉, 독립적인 메모리 영역을 가지며, 다른 프로세스와는 독립적으로 실행된다.
  - 프로세스는 각각의 프로세스 ID(PID)를 가지고, 프로세스 간 통신(IPC)을 이용하여 통신할 수 있다.
- 스레드(Thread)란?
  - 프로세스 내에서 실행되는 작업 단위를 뜻한다.
  - 한 프로세스 내에서 여러 개의 스레드가 동시에 실행될 수 있으며, 각 각의 스레드는 프로세스의 메모리 공간을 공유한다.
  - 즉, 스레드는 하나의 프로세스 내에서 독립적으로 실행되지 않으며, 다른 스레드와 메모리를 공유한다.
- 차이점
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/fb645fff-1b25-45f4-93cd-cb8e9fcc0ca2)
  - 프로세스는 각각의 독립적인 메모리 공간을 할당받아 실행되므로, 프로세스 간의 자원 공유나 통신을 위해서는 별도의 IPC 기법을 사용해야 하지만
    스레드는 같은 프로세스 내에서 메모리를 공유하기 때문에, 스레드 간의 자원 공유나 통신이 비교적 쉽다.
  - 프로세스는 각각의 독립적인 메모리 공간을 할당받아 실행되므로, 하나의 프로세스가 비정상적으로 종료되더라도 다른 프로세스에는 영향을 주지 않지만
    스레드는 같은 프로세스 내에서 실행되기 때문에, 한 스레드에서 예외가 발생하면 다른 스레드에도 영향을 줄 수 있다.
- Ref.
[윤개승발](https://yuniday2.tistory.com/85),
[aeong98](https://velog.io/@aeong98/%EC%9A%B4%EC%98%81%EC%B2%B4%EC%A0%9COS-%ED%94%84%EB%A1%9C%EC%84%B8%EC%8A%A4%EC%99%80-%EC%8A%A4%EB%A0%88%EB%93%9C)
<br><br><br>



## 스레드
- 스레드란?
  - 스레드란 프로세스 내에서 동시에 실행되는 독립적인 실행단위를 뜻한다.
- 스레드의 장점
  - Context Switching이 빠르기 때문에 시스템 처리량이 증가한다.
  - 프로세스 내의 Stack영역을 제외한 모든 메모리를 공유하기 때문에 통신 부담이 적어 프로그램 응답 시간이 단축된다.
- 주의사항
  - Thread를 실행할 때는 run()이 아닌 start()를 호출해야한다.
    - run()으로 호출할 경우, 메인 메서드에서 실행되는 것이기 때문에 의도한 것(=멀티스레드로 구성)과 다르게 동작한다.  
- Thread 클래스와 Runnable 인터페이스 구현 비교
  - ``` java
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



## 스레드 가시성
- 가시성(Visibility)이란?
  - 스레드 환경에서 각 각의 스레드가 공유자원에 대해서 모두 같은 상태를 바라보고 있는 것을 의미한다.
- 가시성 문제
  - 공유하는 변수에 연산이 일어날 때 CPU를 점유하고 동작하는데, 이 때 main memory에만 존재하는 것이 아니라 CPU cache에도 공유하는 자원에 대한 데이터가 들어있다.
    - ![image](https://github.com/user-attachments/assets/7be992e1-badf-48d4-bda9-ce10412f109f)
      - CPU cache와 Main Memory에 저장된 값이 다를 때, 일어날 수 있는 이슈.
  - 이 때 CPU cache를 읽어오는데, 언제 main memory에 옮겨갈 지 모르기 때문에 여러 thread가 동시에 읽음 연산과 쓰기 연산을 한다면 main memory에서 cache로 데이터를 옮기는 과정에서 다른 thread가 연산을 진행하여 결국 데이터 불일치 문제가 생기는 것이다.
  - 이런 불일치 문제를 Thread 가시성 이슈라고 하며 자바에서는 volatile 키워드를 통해 해결할 수 있다.
    - volatile 키워드는 가시성 이슈를 해결할 수 있지만, 동시성 이슈를 해결할 수는 없다.
- Ref.
[Nick_Choi](https://whitehartlane.tistory.com/33)
<br><br><br>



## 멀티스레드와 Thread Safety
- 멀티스레드란?
  - 멀티스레드는 하나의 프로세스 내부에서 여러 개의 스레드가 동시에 실행되는 것이다.
  - 멀티스레드를 사용하면 시스템의 처리량이 향상되고 자원 소모가 줄어들어 자연스럽게 프로그램의 응답 시간이 단축된다는 장점을 가지고 있다.
- Thread Safety란?
  - 다수의 스레드가 공유 자원에 접근해도 프로그램이 문제 없이 동작하는 것을 의미한다.
- Thread Safety한 구현
  - Synchronized 키워드 사용
  - Volatile 키워드 사용
  - ThreadLocal 사용
  - Atomic Object 사용
  - Synchronized Collections 사용
  - Concurrent Collections 사용
- Ref.
[mangoo.log](https://velog.io/@mangoo/java-thread-safety),
[jammmm](https://jammdev.tistory.com/191),
[eckrin.log](https://eckrin.tistory.com/173)
<br><br><br>



## JVM
- JVM이란
  - Java로 개발한 프로그램을 컴파일하여 만들어지는 바이트코드를 실행시키기 위한 가상머신이다.
  - Java와 OS사이에서 중개자 역할을 하여, OS의 종류와 무관하게 동일한 동작을 보장한다.
  - 메모리 관리 및 Garbage Collection을 수행한다.
  - Stack 기반의 가상머신이다.
- JVM 구성
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/d24ea6ce-6f74-4da1-b6d5-3a931e0e7df7)
    - 클래스 로더(Class Loader)
      - JVM 내로 클래스 파일(*.class)을 로드하고, 링크를 통해 배치하는 작업을 수행하는 모듈이다.
    - Runtime Data Area
      - 프로그램을 수행하기 위해 OS에서 할당받은 메모리 공간.
    - Method Area
      - 클래스에 대한 정보와 클래스 변수(static variable)가 저장되는 영역이다.
    - Heap
      - new 키워드를 통해 생성된 인스턴스의 정보, Array와 같이 동적으로 생성된 데이터가 저장되는 영역이다.
    - JVM Stack
      - 메서드가 호출되면, 메서드의 지역 변수와 매개변수가 저장되는 영역이다.
    - PC Register
      - Thread가 시작될 때 생성되며 생성될 때마다 생성되는 공간으로, 스레드마다 하나씩 존재한다.
      - Thread가 어떤 부분을 어떤 명령으로 실행해야할 지에 대한 기록을 하는 부분으로 현재 수행 중인 JVM 명령의 주소를 갖는다.
    - Native Stack
      - JAVA가 아닌 다른 언어로 작성된 코드를 위한 공간이다.
      - Java Native Interface를 통해 바이트 코드로 전환하여 저장하게 된다.
    - 실행 엔진(Excution Engine)
      - 클래스를 실행시키는 역할이다.
      - 자바 바이트 코드(*.class)는 기계가 바로 수행할 수 있는 언어보다는 비교적 인간이 보기 편한 형태로 기술된 것이다. 그래서 실행 엔진은 이와 같은 바이트 코드를 실제로 JVM 내부에서 기계가 실행할 수 있는 형태로 변경한다.
    - Garbage Collector
      - 더이상 사용되지 않는 인스턴스를 찾아 메모리에서 삭제하는 역할을 한다.
- 실행과정
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
  - GC가 실행되면 stop-the-world가 발생한다.
    - `stop-the-world란 GC를 실행하기 위해 JVM이 모든 애플리케이션 실행을 멈추는 것을 말한다.`
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
[Naver D2](https://d2.naver.com/helloworld/1329),
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
  - ``` java
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
    - ``` java
      @Target(ElementType.TYPE)
      @Retention(RetentionPolicy.RUNTIME)
      @Documented
      public @interface MyAnnotation {
          String value() default "";
      }
      ```
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
