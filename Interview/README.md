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
<details>
<summary><h4>Java의 특징</h4></summary>

> - 객체 지향 언어로써 캡슐화, 상속, 다형성 기능을 완벽하게 지원한다.
> - 운영체제에 상관없이 독립적으로 작동(JVM에서 동작하기 때문)하여 이식성이 높다.
> - Garbage Collector에 의해 메모리가 관리된다.
> - 스레드 생성 및 제어와 관련된 라이브러리를 제공하기 때문에 운영체제에 상관없이 멀티 스레드를 쉽게 구현할 수 있다.
> - 애플리케이션이 실행될 때 모든 객체가 생성되지 않고, 각 객체가 필요한 시점에 클래스를 동적 로딩해서 생성한다. 또한 유지보수 시 해당 클래스만 수정하면 되기 때문에 전체 애플리케이션을 다시 컴파일 할 필요가 없기 때문에 유지보수가 쉽고 빠르다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/37)
</details>



<details>
<summary><h4>객체지향의 4대 특징</h4></summary>

> - **캡슐화**
>   - 객체의 필드와 메서드를 하나로 묶는 것이며, 이를 통해 정보은닉 효과를 얻을 수 있다.
> - **추상화**
>   - 사물들의 공통적인 특징을 파악해서 하나의 개념으로 다루는 것을 뜻한다.
>   - 가령 클래스들의 공통적인 요소를 뽑아내서 상위 클래스로 만들어낼 수 있다.
> - **다형성**
>   - 하나의 객체나 메소드가 여러가지 다른 형태를 가질 수 있는 것을 뜻한다.
>   - 오버라이딩과 오버로딩 그리고 상속받은 객체의 참조변수 형변환 등이 있다.
> - **상속성**
>   - 상위 객체의 필드와 메서드를 하위 객체에게 물려주어 하위 객체에서 사용할 수 있도록 해준다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/38)
</details>



<details>
<summary><h4>객체지향의 5대 원칙(SOLID)</h4></summary>

> - **단일 책임 원칙(Single Responsiblity Principle)**
>   - 소프트웨어의 설계 부품(클래스, 함수 등)은 하나의 책임만 가진다.
>   - 클래스의 기능(책임)이 많아지면 내부 함수끼리 강한 결합이 발생할 가능성이 높으므로 응집도는 높이고 결합도는 낮춰야 한다.
>     - `결합도 : 모듈(클래스) 간의 상호 의존 정도로써, 결합도가 낮으면 상호 의존성이 줄어들어 객체의 재사용이나 수정, 유지보수가 용이해진다.`
>     - `응집도 : 하나의 모듈 내부에 존재하는 구성 요소들의 기능적 관련성으로, 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져 재사용이나 기능의 수정, 유지보수가 용이해진다.`
> - **개방-폐쇄 원칙(Open-Closed Principle)**
>   - 소프트웨어 엔티티(클래스, 모듈, 함수 등)는 확장에 대해서는 열려 있어야 하지만 변경에 대해서는 닫혀 있어야 한다.
>   - 이를 위해 인터페이스를 사용하기도 한다.
> - **리스코프 치환 원칙(Liskov Substitution Principle)**
>   - 자식 클래스는 부모 클래스의 기능을 대체해서 수행할 수 있어야 한다.
>   - 부모 클래스의 인스턴스 대신에 자식 클래스의 인스터스를 사용해도 문제가 없어야 한다는 것을 의미한다.
> - **인터페이스 분리 원칙(Interface Segregation Principle)**
>   - 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안된다.
>   - 큰 덩어리의 인터페이스들을 작은 단위들로 분리시키고, 꼭 필요한 메서드들만 사용하여 내부 의존성 관계를 느슨하게 한다.
> - **의존 역전 원칙(Dependency Inversion Principle)**
>   - 상위 모듈은 하위 모듈에 종속되어서는 안된다.
>   - 의존 관계를 맺을 때, 구체적인 클래스보다는 인터페이스나 추상 클래스와 관계를 맺어야 한다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/39)
</details>



<details>
<summary><h4>클래스, 객체, 인스턴스 비교</h4></summary>

> - **클래스**
>   - 객체를 만들어 내기 위한 설계도로써 객체의 상태를 나타내는 필드(field)와 객체의 행동을 나타내는 메서드(method)로 구성된다.
> - **객체**
>   - 클래스로 구현할 모든 대상을 뜻한다.
> - **인스턴스**
>   - 객체가 메모리에 할당되어 실제 사용될 때를 지칭한다.
> - **Ex**
>    ```java
>    public class Animal { // 클래스
>        ...
>    }
>     
>    public class Main {
>         public static void main(String[] args) {
>             Animal cat, dog; // 객체
>    
>             // 인스턴스화
>             cat = new Animal();
>             dog = new Animal();
>         }
>    }
>    ```

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/40)
</details>



<details>
<summary><h4>String, StringBuffer, StringBuilder 비교</h4></summary>

> - **String**
>   - 불변(immutable)의 속성을 갖는다.
>   - 변경 연산을 자주 사용할 경우, 힙 메모리에 많은 가비지(Garbage)가 생성되어 힙 메모리 부족으로 이어질 수 있다.
>   - 불변성을 가지기 때문에 멀티스레드 환경에서의 thread-safe 하다.
> - **StringBuffer**
>   - String 클래스와 다르게 가변성을 갖는다.
>   - 동기화를 지원하여 멀티 스레드 환경에서도 안전하게 동작할 수 있다.
> - **StringBuilder**
>   - String 클래스와 다르게 가변성을 갖는다.
>   - 동기화를 지원하지 않는다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/42)
</details>



<details>
<summary><h4>접근 제어자</h4></summary>

> - **public**
>   - 적용대상 : 필드, 생성자, 메서드, 클래스
>   - 모든 접근을 허용한다.
> - **protected**
>   - 적용대상 : 필드, 생성자, 메서드
>   - 같은 패키지 또는 다른 패키지이지만 해당 클래스를 상속받은 자식 클래스에서의 접근을 허용한다.
> - **default**
>   - 적용대상 : 필드, 생성자, 메서드, 클래스
>   - 같은 패키지 내에서의 접근을 허용한다.
> - **private**
>   - 적용대상 : 필드, 생성자, 메서드
>   - 같은 클래스 내에서의 접근만 허용한다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/46)
</details>



<details>
<summary><h4>final 제어자</h4></summary>

> - **final 이란?**
>   - Java에서는 불변성을 확보하거나 동작을 제한할 수 있는 final 키워드를 제공한다.
>   - final 키워드는 변수(variable), 메서드(method), 클래스(class)에 사용할 수 있다.
> - **final 변수**
>   - 변수에 final 키워드를 사용할 경우, 더 이상 값을 변경하지 못하도록 제한을 할 수 있다.
> - **final 메서드**
>   - 메서드에 final 키워드를 사용할 경우, 재정의를 제한할 수 있다.
> - **final 클래스**
>   - 클래스에 final 키워드를 사용할 경우, 상속을 제한할 수 있다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/44)
</details>



<details>
<summary><h4>래퍼클래스(Wrapper Class)와 박싱(Boxing), 언박싱(Unboxing)</h4></summary>

> - **박싱(Boxing) / 언박싱(UnBoxing)**
>   - Boxing은 원시 타입의 값을 래퍼 클래스(Wrapper class)로 변환하는 것을 의미한다.
>   - Unboxing은 래퍼 클래스를 원시 타입으로 변환하는 것을 의미한다.
>   -
>     ```java
>     int n = 10;
>     
>     // 박싱
>     Integer boxingNum = new Integer(n);
>     System.out.println("boxingNum = " + boxingNum); // 10
>     
>     // 언박싱
>     int unbonxingNum = boxingNum.intValue();
>     System.out.println("unbonxingNum = " + unbonxingNum); // 10
>     ```
> - **오토 박싱(Auto Boxing) / 오토 언박싱(Auto UnBoxing)**
>   - JDK 1.5부터 지원하는 기능으로, 명시적으로 표현하지 않아도 컴파일러가 자동으로 박싱과 언박싱을 처리를 해준다.
>   -
>     ```java
>     int n = 10;
>     
>     // 오토 박싱
>     Integer autoBoxingNum = n;
>     System.out.println("autoBoxingNum = " + autoBoxingNum); // 10
>     
>     // 오토 언박싱
>     int autoUnbonxingNum = autoBoxingNum;
>     System.out.println("autoUnbonxingNum = " + autoUnbonxingNum); // 10
>     ```

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/123)
</details>



<details>
<summary><h4>추상클래스</h4></summary>
 
> - **추상클래스란?**
>   - 추상 메서드를 선언해 놓고 상속을 통해 자식 클래스에서 메서드를 완성하도록 유도하는 클래스이다.
>   - 반드시 사용되어야 하는 메서드를 추상 클래스에 추상 메서드로 선언해 놓으면, 이 클래스를 상속받는 모든 클래스에서는 이 추상 메서드를 반드시 재정의해야 한다.
>   - 추상클래스는 abstract 키워드를 붙여 선언할 수 있다.
>   -
>      ```java
>      abstract class Animal {
>          abstract void cry();
>      }
>      ```
>   -
>      ```java
>      class Bird extends Animal {
>          @Override
>          void cry() { // 반드시 cry()를 구현해야한다.
>              System.out.println("짹짹");
>          }
>      }
>      
>      class Cat extends Animal {
>          @Override
>          void cry() { // 반드시 cry()를 구현해야한다.
>              System.out.println("야옹");
>          }
>      }
>      
>      class Dog extends Animal {
>          @Override
>          void cry() { // 반드시 cry()를 구현해야한다.
>              System.out.println("멍멍");
>          }
>      }
>      ```
> - **추상클래스 특징**
>   - 구현해야 하는 메서드들은 상위 클래스에서 선언을 해놓고, 구현의 책임을 하위클래스에 위임한다.
>   - 메서드와 클래스에 abstract 예약어를 사용한다.
>   - 추상메서드가 없어도 abstract 키워드를 사용하면 추상클래스가 된다. 단, 추상메서드가 하나라도 존재한다면 그 클래스는 반드시 추상 클래스가 돼야 한다.
>   - 생성자를 가질 수 있고, 일반 메서드도 가질 수 있다. (단, 생성자를 갖지만 객체 생성은 불가능하다.)
> - **추상클래스 장점**
>   - 추상클래스를 만든 후 상속을 받는다면 중복코드 제거 및 코드 재사용성 증대 효과를 얻을 수 있다.
>   - 추상클래스를 사용하여 상속을 통해 자식클래스를 구현한다면, 각 각의 클래스들을 그룹화하여 제어할 수 있다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/124)
</details>



<details>
<summary><h4>인터페이스</h4></summary>

> - **인터페이스란?**
>   - 자바에서 클래스들이 구현해야 하는 동작을 지정하는 용도로 사용되는 추상 자료형이다.
>   - 인터페이스는 interface 키워드를 붙여 선언할 수 있으며, 기본적으로는 상수와 추상메서드로 구성된다. 하지만 자바8부터는 default 메서드와  static 메서드를 지원한다.
>   -
>      ```java
>      interface InterfaceSample {
>      
>          public static final int NUM = 10; // public static final 생략 가능. 컴파일 시에 자동 생성
>          public abstract void calc(); // public abstract 생략 가능. 컴파일 시에 자동 생성
>     
>          default void defaultMethod() { // Java8부터 사용 가능한 default 메서드
>              // ...
>         }
>      
>          static void staticMethod() { // Java8부터 사용 가능한 static 메서드
>              // ...
>          }
>        
>      }
>      ```
> - **인터페이스 특징**
>   - 인터페이스는 interface 키워드를 사용하여 정의한다.
>   - 인터페이스는 상수와 추상메서드로 구성되어 있다. (자바8부터 default와  static 메서드 사용 가능)
>   - 인터페이스 안의 모든 상수는 public static final 타입이다. (생략 가능)
>   - 인터페이스 안의 모든 추상메서드는 abstract public 타입이다. (생략 가능)
>   - 추상클래스와 마찬가지로 인스턴스를 생성할 수 없다.
>   - 인터페이스는 다른 인터페이스를 extends 키워드로 상속받을 수 있으며, 다중 상속이 가능하다.
>   - 클래스에서 인터페이스의 구현은 implements 키워드를 사용하여 구현할 인터페이스를 지정 후, 추상메서드를 모두 오버라이드하여 내용을 완성해야 한다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/125)
</details>



<details>
<summary><h4>추상클래스와 인터페이스의 차이</h4></summary>

> - **추상클래스와 인터페이스의 차이점**
>   - 추상클래스 : 자식클래스 is kind of 부모클래스
>   - 인터페이스 : 자식클래스 is able to 부모인터페이스
>   - 추상클래스는 계층 구조에서 공통된 속성들을 뽑아서 하나의 클래스로 만들고 자신의 기능들을 하위로 확장시키는 것으로 볼 수 있으며, 인터페이스는 계층 구조는 아니지만 같은 기능이 필요한 경우 사용하는 것으로 볼 수 있다.
>   ![image](https://github.com/Young-Geun/TIL/assets/27760576/960f18b5-d588-4ddc-ac10-c1998b383bb1)

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/126)
</details>


<details>
<summary><h4>Overloading vs Overriding</h4></summary>
 
> - **오버로딩(Overloading)**
>   - 매개변수의 개수나 자료형을 다르게하여 같은 이름의 메서드를 사용하는 것
>   - ``` java
>     int sum(int num1, int num2) {
>         return num1 + num2;
>     }
>
>     // 새로 추가된 sum() 메서드 - OverLoading이 적용되었다.
>     double sum(double num1, double num2) {
>         return num1 + num2;
>     }
>     ```
> - **오버라이딩(Overriding)**
>   - 오버라이딩이란 부모클래스로부터 상속받은 메서드의 내용을 변경(재정의)하여 사용하는 것
>   - 오버라이딩 X
>      ``` java
>      class ParentClass {
>          void sayName(String name) {
>              System.out.println("[부모클래스] name=" + name);
>          }
>      }
>      
>      class ChildClass extends ParentClass {
>      }
>      
>      public class OverridingTest {
>      
>          public static void main(String[] args) {
>              ChildClass child = new ChildClass();
>              child.sayName("choi"); // [부모클래스] name=choi
>          }
>      
>      }
>     ```
>   - 오버라이딩 O
>      ``` java
>      class ParentClass {
>          void sayName(String name) {
>              System.out.println("[부모클래스] name=" + name);
>          }
>      }
>      
>      class ChildClass extends ParentClass {
>          @Override
>          void sayName(String name) {
>              System.out.println("[자식클래스] name=" + name);
>          }
>      }
>      
>      public class OverridingTest {
>      
>          public static void main(String[] args) {
>              ChildClass child = new ChildClass();
>              child.sayName("choi"); // [자식클래스] name=choi
>          }
>      
>      }
>     ```

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/127)
</details>



<details>
<summary><h4>제네릭(Generic)</h4></summary>

> - **제네릭(Generic)이란**
>   - 제네릭이란 클래스 내부에서 사용할 데이터 타입을 외부에서 지정하는 기법을 의미한다.
>   - Ex)
>      ``` java
>      // String 타입으로 선언 및 생성
>      List<String> stringList = new ArrayList<>();
>      
>      // Integer 타입으로 선언 및 생성
>      List<Integer> integerList = new ArrayList<>();
>     ```
> - **제네릭(Generic)의 장점**
>   - 컴파일 시점에 타입 검사를 통한 예외 방지
>   - 불필요한 캐스팅을 제거

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/128)
</details>



<details>
<summary><h4>컬렉션 프레임워크(Collection Framework)</h4></summary>

> - **컬렉션 프레임워크(Collection Framework)란?**
>   - 다수의 데이터를 쉽고 효과적으로 처리할 수 있는 표준화된 방법을 제공하는 클래스의 집합을 의미한다.
>   - 컬렉션 프레임워크의 주요 인터페이스에는 List, Set, Map이 있으며 각 각의 인터페이스들은 구현체를 가지고 있다.
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/c00b20fb-2031-4b27-ae67-1c0efa18e549)
> - **List**
>   - 순서가 있는 데이터 집합이다.
>   - 데이터의 중복을 허용한다.
>     - ArrayList
>       - 단방향 포인터 구조로 인덱스로 접근하므로 조회할 때 유리하지만, 데이터의 삽입이나 삭제가 발생할 경우 인덱스를 조정하는 추가 작업이 필요하다.
>     - LinkedList
>       - 순차 접근만 가능하여 조회할 때는 불리하지만, 양방향 포인터 구조로 데이터의 삽입, 삭제에 유리하다.
>     - Vector
>       - ArrayList와 구현 원리와 기능적인 측면에서 동일하며, 동기화를 지원한다.
> - **Set**
>   - 순서가 없는 데이터 집합이다.
>   - 데이터의 중복을 허용하지 않는다.
>     - HashSet
>       - 가장 빠르게 접근할 수 있으나 순서를 보장하지 않는다.
>     - TreeSet
>       - 입력한 순서대로 값을 저장하지 않지만, 기본적으로 오름차순으로 정렬한다.
>     - LinkedHashSet
>       - 입력한 순서대로 값을 저장한다.
> - **Map**
>   - 키와 값의 한 쌍으로 이루어진 데이터 집합으로 순서가 없다.
>   - 키의 중복은 허용하지 않고, 값의 중복은 허용한다.
>     - TreeMap
>       - 데이터를 이진 검색 트리(binary search tree)의 형태로 저장하므로 데이터의 삽입이나 삭제가 빠르다.
>     - HashMap
>       - 가장 많이 사용되는 클래스 중 하나이며, 해시 알고리즘(hash algorithm)을 사용하여 검색 속도가 매우 빠르다.
>     - Hashtable
>       - HashMap과 다르게 동기화를 보장한다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/129)
</details>



<details>
<summary><h4>람다식(Lambda Expression)</h4></summary>

> - **람다식(Lambda Expressions) 이란?**
>   - 람다식이란 프로그래밍 언어에서 사용되는 개념으로 익명 함수를 지칭하는 용어이다.
>   - 함수를 람다식으로 표현하면 메서드의 이름 없이 사용할 수 있게 되는데, 이 때문에 익명 함수라고도 불린다.
>   - 람다식은 자바 8부터 사용 가능하며 이로 인하여 자바에서도 함수형 프로그래밍이 가능하게 되었다.
> - **장점**
>   - 코드를 간결하게 만들 수 있다.
>   - 식에 개발자의 의도가 명확히 드러나 가독성이 높아진다.
>   - 함수를 만드는 과정없이 한번에 처리할 수 있어 생산성이 높아진다.
>   - 병렬프로그래밍이 용이하다.
> - **단점**
>   - 람다를 사용하면서 만든 무명함수는 재사용이 불가능하다.
>   - 디버깅이 어렵다.
>   - 람다를 무분별하게 사용할 경우, 비슷한 함수가 중복 생성될 수 있다.
> - **기본 문법**
>   - ``` java
>     interface SquareIF {
>         int square(int num);
>     }
>     
>     public class LambdaSample {
>     
>         public static void main(String[] args) {
>     
>             /*
>              *  추상 메서드를 하나만 갖는 인터페이스를 자바 8부터는 함수형 인터페이스라고 하며,
>              *  이런 함수형 인터페이스만을 람다식으로 표현 가능하다.
>              */
>             SquareIF sif1 = (int a) -> {
>                 return a * a;
>             };
>             System.out.println(sif1.square(1)); // 1
>     
>     
>             /*
>              *  1. 매개변수의 타입을 추론할 수 있는 경우에는 타입을 생략할 수 있다.
>              *     - Square(int num)를 통해 a가 int일 수 밖에 없으므로 int를 생략할 수 있다.
>              *     - (int a)가 (a)로 변경되었다.
>              */
>             SquareIF sif2 = (a) -> {
>                return a * a;
>             };
>             System.out.println(sif2.square(2)); // 4
>     
>     
>             /*
>              *  2. 매개변수가 하나인 경우는 소괄호를 생략할 수 있다.
>              *     - 1번 규칙에 의해 (a)로 변경되었으며, 매개변수가 1개이기 때문에 소괄호도 생략 가능하여 a가 되었다.
>              */
>             SquareIF sif3 = a -> {
>                 return a * a;
>             };
>             System.out.println(sif3.square(3)); // 9
>     
>     
>             /*
>              *  3. 함수의 몸체가 하나의 명령문만 있을 경우, 중괄호도 생략가능하다. 단, return구문은 생략해야한다.
>              */
>             SquareIF sif4 = a -> a * a;
>             System.out.println(sif4.square(4)); // 16
>     
>         }
>     }
>     ```

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/130)
</details>



<details>
<summary><h4>스트림 API(Stream API)</h4></summary>
 
> - **스트림 API(Stream API) 란?**
>   - Java 8에서 추가된 기능으로써 배열 또는 컬렉션 등을 함수형 프로그래밍 기법으로 처리할 수 있도록 도와주는 API이다.
> - **스트림 API(Stream API)의 특징**
>   - 원본 데이터를 변경하지 않는다.
>   - 컬렉션과 달리 재사용이 불가하여 단 1번만 사용할 수 있다.
>   - 내부 반복을 통해 작업을 처리한다.
>   - parallelStream() 메서드를 통한 병렬처리를 지원한다.
> - **스트림 API(Stream API)의 연산**
>   - 생성
>   - 중간 연산(Intermediate Operation)
>     - filter()
>       - 스트림 요소마다 조건문을 만족하는 요소로 구성된 스트림을 반환
>     - distinct()
>       - 스트림 요소들의 중복을 제거한 스트림을 반환
>     - map()
>       - 스트림의 각 요소마다 수행할 연산을 구현할 때 사용
>     - flatMap()
>       - 스트림 요소를 새로운 요소로 대체한 스트림을 생성
>     - limit()
>       - 스트림의 시작 요소로 부터 인자로 전달된 인덱스까지의 요소를 추출해 새로운 스트림을 생성
>     - skip()
>       - 스트림의 시작 요소로 부터 인자로 전달된 인덱스 까지를 제외하고 새로운 스트림을 생성
>     - sorted()
>       - 스트림 요소를 정렬하는 method로 기본적으로 오름차순으로 정렬
>     - peek()
>       - 결과 스트림의 요소를 사용해 추가로 동작을 수행 
>   - 최종 연산(Terminal Operation)
>     - forEach()
>       - 트림의 요소들을 순환하면서 반복해서 처리해야 하는 경우 사용
>     - reduce()
>       - map과 비슷하게 동작하지만 개별연산이 아니라 누적연산이 이루어진다는 차이 존재
>     - findFirst()
>       - 스트림에서 지정한 첫 번째 요소를 찾는 메서드
>     - findAny()
>       - 스트림에서 지정한 첫 번째 요소를 찾는 메서드. parallelStream()와 함께 사용
>     - anyMatch()
>       - 스트림의 요소 중 특정 조건을 만족하는 요소가 하나라도 있는지 검사
>     - allMatch()
>       - 스트림의 요소 중 특정 조건을 모두 만족하는지 검사
>     - noneMatch()
>       - 스트림의 요소 중 특정 조건을 만족하는 요소가 하나도 없는지 검사
>     - count()
>       - 스트림의 원소들로부터 전체 개수 구하기 위한 메서드
>     - min() / max()
>       - 스트림의 원소들로부터 최솟값 / 최댓값을 구하기 위한 메서드
>     - sum() / average()
>       - 스트림 원소들의 합계 / 평균을 구하는 메서드
>     - collect()
>       - 스트림의 결과를 모으기 위한 메서드

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/135)
</details>



<details>
<summary><h4>Checked Exception과 Unchecked Exception</h4></summary>

> - **Checked Exception과 Unchecked Exception**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/569aa4c7-5107-4345-86b5-3902fce637c9)
>   - Checked Exception
>     - 확인시점 : Compile 시점
>     - 처리여부 : 반드시 예외 처리 필요
>     - 롤백여부 : 예외 발생 시, Rollback 수행 안함
>   - Unchecked Exception
>     - 확인시점 : Runtime 시점
>     - 처리여부 : 명시적으로 하지 않아도 무관
>     - 롤백여부 : 예외 발생 시, Rollback 수행
> - **Checked Exception 문제점**
>   - Checked Exception은 반드시 예외를 처리한다는 특성 때문에 Exception을 던지게(throw)되면, 계층 간 종속이 발생할 수 있다.
>   - 만약 아래의 그림과 같이 사용중인 JDBC를 JPA로 변경한다고 가정했을 때, 종속된 모든 계층을 수정해야 하는 상황이 발생한다.
>     - ![image](https://github.com/Young-Geun/TIL/assets/27760576/afeccd8d-ee1d-4c9b-8d00-ca099595cb17)
>     - ![image](https://github.com/Young-Geun/TIL/assets/27760576/59b48da0-1c3f-4107-bf91-d39df636f39f)
>   - 해결방안
>     - Checked Exception을 Unchecked Exception으로 전환한다.
>     -  ```java
>        static class Repository {
>            public void call() {
>                try {
>                    runSQL();
>                } catch (SQLException e) {
>                    /*
>                        Checked Exception인 SQLException 대신에 
>                        Unchecked Exception인 RuntimeSQLException 던진다.
>                     */    
>                    throw new RuntimeSQLException(e);
>                }
>            }
>        
>            private void runSQL() throws SQLException {
>                // SQL 수행 중 오류가 발생했다고 가정.
>                throw new SQLException("ex");
>            }
>        
>        }
>        
>        // RuntimeSQLException은 RuntimeException을 상속받았으므로 Unchecked Exception이 된다.
>        static class RuntimeSQLException extends RuntimeException {
>            public RuntimeSQLException(Throwable cause) {
>                super(cause);
>            }
>        }
>        ```

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/138)
</details>



<details>
<summary><h4>스레드</h4></summary>

> - **프로세스(Process)와 스레드(Thread)**
>   - 프로세스란 실행 중인 프로그램을 뜻한다.
>   - 스레드란 프로세스 내에서 동시에 실행되는 독립적인 실행단위를 뜻한다.
> - **스레드의 장점**
>   - Context Switching이 빠르기 때문에 시스템 처리량이 증가한다.
>   - 프로세스 내의 Stack영역을 제외한 모든 메모리를 공유하기 때문에 통신 부담이 적어 프로그램 응답 시간이 단축된다.
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

Ref.
</details>



<details>
<summary><h4>JVM</h4></summary>

> - **JVM이란?**
>   - Java로 개발한 프로그램을 컴파일하여 만들어지는 바이트코드를 실행시키기 위한 가상머신이다.
>   - Java와 OS사이에서 중개자 역할을 하여, OS의 종류와 무관하게 동일한 동작을 보장한다.
>   - 메모리 관리 및 Garbage Collection 수행한다.
>   - Stack 기반의 가상머신이다.
> - **JVM 구성**
>   - 클래스 로더(Class Loader)
>   - 실행 엔진(Excution Engine)
>   - Garbage Collector
> - **실행과정**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/d24ea6ce-6f74-4da1-b6d5-3a931e0e7df7)
>     1. 프로그램이 실행되면 JVM은 OS로부터 메모리를 할당 받는다.
>     2. 컴파일러가 소스코드(.java)를 읽어 바이트코드(.class)로 변환시킨다.
>     3. 클래스 로더를 통해 class파일들을 JVM에 로딩시킨다.
>     4. 실행 엔진을 통해 로딩된 class파일들을 해석한다.
>     5. 해석된 바이트코드는 Runtime Data Areas에 배치된 후 실행된다. 

Ref.
</details>



<details>
<summary><h4>자바의 메모리 구조</h4></summary>

> - **메서드 영역**
>   - 클래스에 대한 정보와 클래스 변수(static variable)가 저장되는 영역이다.
>   - 모든 스레드에서 정보가 공유된다.
> - **힙 영역**
>   - new 키워드를 통해 생성된 인스턴스의 정보, Array와 같이 동적으로 생성된 데이터가 저장되는 영역이다.
>   - Reference Type 의 데이터가 저장되는 공간이다.
>   - 모든 스레드에서 정보가 공유된다.
> - **스택 영역**
>   - 메서드가 호출되면, 메서드의 지역 변수와 매개변수가 저장되는 영역이다.
>   - 만약, 지역변수이지만 Reference Type일 경우에는 Heap에 저장된 데이터의 주소값을 Stack에 저장해서 사용하게 된다.
>   - 스레드마다 하나씩 존재한다.

Ref.
</details>



<details>
<summary><h4>GC</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>HashMap 충돌</h4></summary>

> - **HashMap 특징 및 동작원리**
>   - HashMap은 KEY - VALUE가 1:1로 매핑되는 자료구조이다.
>   - 위와 같은 특성으로 인하여 삽입, 삭제, 검색이 평균적으로 O(1) 시간복잡도를 갖는다.
>   - HashMap의 내부구조는 배열로 되어있으며 배열의 인덱스는 hashcode() % M로 산출한다.
>   - 하지만 동일 값이 발생하여 해시충돌이 일어날 수 있으며, 이를 방지하기 위한 방법에는 Open Addressing 방식과 Separate Chaining 방식이 있는데 자바에서는 Separate Chaining 방식을 채택했다.
> - **Open Addressing**
>   - Open addressing 방식에도 여러가지 구현 방식이 있는데, 가장 간단한 Linear probing 방식을 예로 들자면 충돌이 일어났을 경우, 빈 버킷이 나올 때까지 순차적으로 다음 인덱스를 탐색한다.
> - **Separate Chaining**
>   - 동일 index로 인해서 충돌이 발생하면 그 index가 가리키고 있는 Linked list에 노드를 추가하여 값을 추가한다.
>   - JDK 1.8의 경우에는 index에 노드가 8개 이하일 경우에는 Linked List를 사용하며, 8개 이상으로 늘어날때는 Tree 구조로 데이타 저장 구조를 바꾸도록 되어 있다.

Ref.
</details>



<details>
<summary><h4>non-static 멤버와 static 멤버 차이</h4></summary>

> - **non-static 멤버**
>   - 멤버는 객체마다 별도로 존재한다.
>   - 인스턴스 멤버라고 부른다.
>   - 객체 생성 시에 멤버가 생성된다.
>   - 객체 생성 후 멤버 사용이 가능하다.
>   - 객체가 사라지면 멤버도 사라진다.
>   - 공유되지 않는다.
>   - 멤버는 객체 내에 각각의 공간을 유지한다.
> - **static 멤버**
>   - 멤버는 클래스당 하나가 생성된다.
>   - 멤버는 별도의 공간에 생성된다.
>   - 클래스 멤버라고도 불린다.
>   - 클래스 로딩 시에 멤버가 생성된다.
>   - 객체가 생기기 전에 사용이 가능하다.(즉, 객체를 생성하지 않고도 사용가능)
>   - 객체가 사라져도 멤버는 사라지지 않는다.
>   - 멤버는 프로그램이 종료될 때 사라진다.
>   - 동일한 클래스의 모든 객체들에 의해 공유된다.

Ref.
</details>



<details>
<summary><h4>직렬화와 역직렬화</h4></summary>

> - **직렬화와 역직렬화**
>   - 직렬화(serialize)란 자바 언어에서 사용되는 Object 또는 Data를 다른 컴퓨터의 자바 시스템에서도 사용 할수 있도록 바이트 스트림(stream of bytes) 형태로 연속전인(serial) 데이터로 변환하는 포맷 변환 기술을 일컫는다.
>   - 그 반대 개념인 역직렬화는(Deserialize)는 바이트로 변환된 데이터를 원래대로 자바 시스템의 Object 또는 Data로 변환하는 기술이다.
> - **직렬화 사용처**
>   - 직렬화를 응용한다면 휘발성이 있는 캐싱 데이터를 영구 저장이 필요할 때 사용할 수도 있다.
>   - 예를들어 JVM의 메모리에서만 상주되어있는 객체 데이터가 시스템이 종료되더라도 나중에 다시 재사용이 될수 있을때 영속화(Persistence)를 해두면 좋다.
>   - 이러한 특성을 살린 자바 직렬화는 다음과 같은 곳에서 응용되기도 한다.
>     - 서블릿 세션 (Servlet Session)
>       - 단순히 세션을 서블릿 메모리 위에서 운용한다면 직렬화를 필요로 하지 않지만, 만일 세션 데이터를 저장 & 공유가 필요할때 직렬화를 이용한다.
>       - 세션 데이터를 데이터베이스에 저장할 때 사용된다.
>       - 톰캣의 세션 클러스터링을 통해 각 서버간에 데이터 공유가 필요할 때 사용된다.
>     - 캐시 (Cache)
>       - 데이터베이스로부터 조회한 객체 데이터를 다른 모듈에서도 필요할때 재차 DB를 조회하는 것이 아닌, 객체를 직렬화하여 메모리나 외부 파일에 저장해 두었다가 역직렬화하여 사용하는 캐시 데이터로서 이용이 가능하다.
>     - 자바 RMI (Remote Method Invocation)
>       - 자바 RMI는 원격 시스템 간의 메시지 교환을 위해서 사용하는 자바에서 지원하는 기술이다.
>       - 이 메세지에 객체 데이터를 직렬화하여 송신하는 것이다.
>       - 최근에는 소켓을 이용하기 때문에 안쓰이는 기술이다.
> - **직렬화 사용법**
>   - Serializable 인터페이스
>     - 우선 객체를 직렬화하기 위해선 java.io.Serializable 인터페이스를 implements 해야 된다. 그렇지 않으면 NotSerializableException 런타임 예외가 발생된다.
>   - ObjectOutputStream / ObjectInputStream 클래스
>     - 직렬화(스트림에 객체를 출력) 에는 ObjectOutputStream을 사용한다.
>     - 역직렬화(스트림으로부터 객체를 입력)에는 ObjectInputStream을 사용한다.
> - **자바 직렬화 버전 관리**
>   - SerialVersionUID
>     - Serializable 인터페이스를 구현하는 모든 직렬화된 클래스는 serialVersionUID(이하 SUID) 이라는 고유 식별번호를 부여 받는다.
>     - 이 식별 ID는 클래스를 직렬화, 역직렬화 과정에서 동일한 특성을 갖는지 확인하는데 사용된다.
>     - 클래스 내부 구성이 수정될 경우, 기존에 직렬화한 SUID와 현재 클래스의 SUID 버전이 다르기 때문에 이를 인지하고 InvalidClassException 예외가 발생시켜 값 불일치 되는 현상을 미연에 방지할 수 있다.
>     - 위와 같은 특징으로 인해 클래스에 조그만한 변경사항이라도 있으면, 모든 사용자에게 재배포를 해야하는 애로사항이 있지만, serialVersionUID를 직접 명시해주어 클래스 버전을 수동으로 관리하게되면 이를 해결할 수 있다.

Ref.
[인파](https://inpa.tistory.com/entry/JAVA-%E2%98%95-%EC%A7%81%EB%A0%AC%ED%99%94Serializable-%EC%99%84%EB%B2%BD-%EB%A7%88%EC%8A%A4%ED%84%B0%ED%95%98%EA%B8%B0)
</details>



<details>
<summary><h4>리플렉션(Reflection)</h4></summary>

> - **리플렉션이란?**
>   - 구체적인 클래스 타입을 알지 못하더라도 그 클래스의 메서드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API이다.
>   - 컴파일 시간이 아닌 실행시간에 동적으로 클래스의 정보를 추출할 수 있는 프로그래밍 기법이다.
> - **리플렉션의 사용용도**
>   - 리플렉션은 프레임워크나 라이브러리에서 주로 사용된다.   
프레임워크나 라이브러리에서는 들어오는 클래스의 정보를 모르기 때문이다.   
코드를 작성한 개발자는 당연히 내가 작성한 클래스의 정보를 알 수 있지만, 프레임워크 입장에서 보면 모르는게 당연하다.   
이때, 리플렉션을 통해 런타임 시 클래스의 정보를 얻고 이를 기반으로 하여 프레임워크나 라이브러리가 지원하는 기능을 수행하는 것이다.   
스프링의 주요 기능인 DI도 리플렉션의 원리가 들어있다.
> - **리플렉션의 사용예시**
>   - 메서드를 직접 호출할 경우, 기능이 추가되면 조건식을 추가하기 위해 매번 코드를 변경해야한다는 단점이 있지만, 리플렉션을 사용할 경우 이러한 단점을 극복할 수 있다.
>   - ```java
>     import java.lang.reflect.Method;
>     
>     public class ReflectionEx {
>     
>         public static void main(String[] args) throws Exception {
>             Theme theme = new Theme();
>             String userSelectTheme = "Blue";
>     
>             // 직접 호출하는 경우 : 항목이 추가될 때마다 코드 변경이 필요하다.
>             if ("Blue".equals(userSelectTheme)) {
>                 theme.changeBlue(); // 파란 테마로 변경
>             } else if ("Red".equals(userSelectTheme)) {
>                 theme.changeRed(); // 빨간 테마로 변경
>             }
>     
>             // Reflection을 사용하는 경우 : 클래스나 메서드 정보를 동적으로 변경할 수 있다는 장점이 있다.
>             //                          '직접 호출하는 경우'와 다르게 메서드를 실행하는 로직을 공통으로 만들 수 있다.
>             Class clazz = Class.forName("basic.reflection.Theme");
>             Method method = clazz.getMethod("change" + userSelectTheme);
>             method.invoke(theme); // 파란 테마로 변경
>         }
>     
>     }
>     
>     class Theme {
>         public void changeBlue() {
>             System.out.println("파란 테마로 변경");
>         }
>     
>         public void changeRed() {
>             System.out.println("빨간 테마로 변경");
>         }
>     }
> - **리플렉션의 장단점**
>   - 장점
>     - 유연성과 확장성
>       - 구체적인 클래스를 알지 못해도 동적으로 클래스를 만들어서 의존 관계를 맺어줄 수 있다.
>       - 개발 규모가 큰 스프링인 경우, 리플렉션을 이용한 Dynamic proxy를 통해서 @AutoWired, @Service, @Controller, @Repository와 같은 DI 어노테이션을 활용할 수 있다.
>     - 접근 제어자에 상관없이 테스트 가능
>       - 접근 제어자가 private이더라도 얼마든지 접근해서 조작할 수 있다.
>   - 단점
>     - 캡슐화 저해
>       - private한 데이터에도 접근이 가능하기 때문에 캡슐화가 깨질 위험성이 존재한다.
>     - 성능
>       - 런타임에 클래스를 분석하므로 속도가 느리다.
>     - 컴파일 시 타입 체크가 불가능
>       - 컴파일 시점이 아닌 런타임 시점에 에러가 발생하기 때문에 주의가 필요하다.

Ref.
[영암사는 승경이네](https://tlatmsrud.tistory.com/112)
</details>



<details>
<summary><h4>자바에서 멀티스레드 동기화 방법</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>equals & hashCode</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>Call by value ve Call by Reference</h4></summary>

> - **Call by Value**
>   - 값에 의한 호출을 의미한다.
>   - 전달받은 값을 복사하여 처리하기 때문에 전달받은 값을 변경하여도 원본의 값은 변경되지 않는다.
> - **Call by Reference**
>   - 참조에 의한 호출을 의미한다.
>   - 전달받은 값을 직접 참조하기 때문에 전달받은 값을 변경하면 원본도 같이 변경된다.

Ref.
</details>



<details>
<summary><h4>String 메모리 관점</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>블락킹과 논블락킹, 동기식과 비동기식</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>Thread-safe</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>어노테이션</h4></summary>

> - Title
>   - Content

Ref.
</details>





<br><br><br>
- - -
<br><br><br>





# Web
<details>
<summary><h4>JSP vs Servlet</h4></summary>

> - **JSP**
>   - html 내에 자바코드를 블록화하여 삽입한 것.
>   - JAVA in Html.
> - **Servlet**
>   - Container가 이해할 수 있도록 구성된 자바코드로 이루어진 것.
>   - Html in JAVA.

Ref.
</details>



<details>
<summary><h4>Session과 Cookie</h4></summary>
 
> - **Session**
>   - 저장위치 : 웹 서버
>   - 브라우저를 종료하거나, 서버에서 세션을 삭제했을 때 삭제된다.
>   - 각 클라이언트에 고유 Session ID를 부여하고, 이 Session ID로 클라이언트를 구분한다.
>   - 동작순서
>     1. 클라이언트가 페이지를 요청한다.
>     2. 서버는 접근한 클라이언트의 Request-Header 필드인 Cookie를 확인하고, 클라이언트가 해당 Session ID를 보냈는지 확인한다.
>     3. Session ID가 존재하지 않는다면, 서버는 Session ID를 생성한 후 클라이언트에게 전달한다.
>     4. 서버에서 클라이언트로 돌려준 Session ID를 쿠키로 사용하여 서버에 저장한다.
>     5. 클라이언트 접속 시, 세션 쿠키를 이용하여 Session ID 값을 서버에 전달한다.
> - **Cookie**
>   - 저장위치 : 클라이언트(=접속자 PC)
>   - 사용자 인증이 유효한 시간을 명시할 수 있으며, 유효 시간이 정해지면 브라우저가 종료되어도 인증이 유지된다.
>   - 동작순서
>     1. 클라이언트가 페이지를 요청한다.
>     2. 웹 서버는 쿠키를 생성하고 정보를 담은 후 HTTP 화면을 돌려줄 때 같이 클라이언트에게 반환한다.
>     3. 클라이언트가 이후 서버에 요청할 때 요청과 함께 쿠키를 전송한다.
>     4. 동일 사이트 재방문 시, 클라이언트의 PC에 해당 쿠키가 있을 경우 요청 페이지와 함께 쿠키를 전송한다.

Ref.
</details>



<details>
<summary><h4>Framework vs Library</h4></summary>

> - **Framework**
>   - 뼈대가 되는 부분을 미리 구현한 클래스, 인터페이스, 메서드 등의 집합체이다.
> - **Library**
>   - 자주 쓰일 만한 기능들을 따로 구현하여 모아 놓은 클래스의 집합체이다.

Ref.
</details>



<details>
<summary><h4>스프링 개념</h4></summary>

> - **스프링이란?**
>   - 자바 엔터프라이즈 개발을 편하게 해주는 오픈소스 경량급 애플리케이션 프레임워크
> - **특징**
>   - 경량 컨테이너로서 자바 객체를 직접 관리한다.
>     - 각각의 객체 생성, 소멸과 같은 라이프 사이클을 관리하며 스프링으로부터 필요한 객체를 얻어올 수 있다.
>   - 스프링은 Plain Old Java Object 방식의 프레임워크이다.
>     - 일반적인 J2EE 프레임워크에 비해 구현을 위해 특정한 인터페이스를 구현하거나 상속을 받을 필요가 없어 기존에 존재하는 라이브러리 등을 지원하기에 용이하고 객체가 가볍다.
>   - 스프링은 제어 반전(IoC : Inversion of Control)을 지원한다.
>     - 컨트롤의 제어권이 사용자가 아니라 프레임워크에 있어서 필요에 따라 스프링에서 사용자의 코드를 호출한다.
>   - 스프링은 의존성 주입(DI : Dependency Injection)을 지원한다.
>     - 각각의 계층이나 서비스들 간에 의존성이 존재할 경우 프레임워크가 서로 연결시켜준다.
>   - 스프링은 관점 지향 프로그래밍(AOP : Aspect-Oriented Programming)을 지원한다.
>     - 트랜잭션이나 로깅, 보안과 같이 여러 모듈에서 공통적으로 사용하는 기능의 경우 해당 기능을 분리하여 관리할 수 있다.
> - **스프링 구조**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/d38101c3-087a-4248-8a61-1847d11dde7a)

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/5)
</details>



<details>
<summary><h4>스프링 MVC</h4></summary>

> - **스프링 MVC란?**
>   - MVC 패턴에 기반을 둔 웹 프레임워크이다.
> - **MVC 패턴**
>   - Mode, View, Controller의 약자이며, 클라이언트와 상호작용하는 소프트웨어를 설계함에 있어서 세 가지 요소로 나누어 설계하는 것을 뜻한다.
>     - Model
>       - Model은 애플리케이션의 정보, 데이터의 가공을 책임지며 데이터베이스와 상호작용하여 비즈니스 로직을 처리하는 모듈.
>       - 즉, 컴포넌트를 뜻한다.
>     - View
>       - View는 클라이언트 단에서 보여지는 결과화면을 반환하는 모듈.
>       - 즉, 사용자 인터페이스 요소를 뜻한다.
>     - Controller
>       - Controller는 클라이언트로부터 요청이 들어왔을 때, 어떤 로직을 실행시킬 것인지 판단하며 Model(모델)과 View(뷰)를 연결해주며 제어하는 모듈.
> - **스프링 MVC의 구성요소와 동작순서**
>   ![image](https://github.com/Young-Geun/TIL/assets/27760576/e675f1ab-e106-415c-a02a-df22a2bf5112)
>   - 구성요소
>     - Dispatcher Servlet
>       - 클라이언트의 요청을 받아 컨트롤러에게 전달한다.
>       - 컨트롤러가 리턴한 결과값을 View에 전달한다.
>     - Handler Mapping
>       - 클라이언트의 요청 URL을 확인하여 요청을 처리할 컨트롤러를 결정한다.
>     - Handler Adapter
>       - DispatcherServlet의 처리 요청을 변환해서 컨트롤러에게 전달한다.
>     - Controller
>       - 클라이언트의 요청에 대한 처리를 하고 결과를 리턴한다.
>     - ModelAndView
>       - 컨트롤러가 처리한 결과 정보 및 뷰 선택에 필요한 정보를 담고 있다.
>     - View Resolver
>       - 컨트롤러의 처리 결과를 생성할 뷰를 결정한다.
>     - View
>       - 컨트롤러의 처리 결과를 보여줄 화면을 생성한다.
>   - 동작순서
>     - 1.클라이언트로부터 요청이 발생하면 모든 요청은 Dispatcher Servlet으로 전달된다.
>     - 2.요청에 대하여 Handler Mapping은 처리를 할 Controller가 있는지 탐색한다. 
>     - 3.Controller가 결정되면 Dispatcher Servlet은 Handler Adaptor에게 요청 처리를 위임한다.
>     - 4.Handler Adaptor에 의해서 컨트롤러가 호출되고 비즈니스 로직이 수행된다. 
>     - 5.Controller는 비즈니스 로직을 처리하고 그 결과를 Model객체에 저장하여 View 페이지명과 함께 응답한다. 
>     - 6.Dispatcher Servlet은 view name을 View Resolver에게 전달하여 View 객체를 얻는다.
>     - 7.View를 호출하면 템플릿 엔진이 동작하여 HTML을 구성한다.
>     - 8.최종적으로 View의 내용이 클라이언트에게 전달된다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/6)
</details>



<details>
<summary><h4>스프링 DI</h4></summary>

> - **DI란?**
>   - 의존성 주입(DI)이란, 객체를 직접 생성하는 것이 아니라 외부에서 객체를 생성한 후 주입 시켜주는 방식을 뜻한다.
> - **의존관계 주입 방법**
>   1. 필드 주입
>   2. 수정자 주입(= Setter 주입)
>   3. 생성자 주입
> - **장점**
>   - 코드의 재사용성, 유연성이 높아진다.
>   - 객체 간 결합도가 낮기 때문에 한 클래스를 수정했을 때, 다른 클래스도 수정해야 하는 상황을 막아준다.
>   - 유지보수가 쉬워지며, 테스트가 용이해진다.
>   - 확장성을 가진다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/13)
</details>



<details>
<summary><h4>스프링 IoC</h4></summary>

> - **IoC (Inversion of Control)란?**
>   - Bean의 생성과 의존 관계 설정, 사용, 제거 등의 작업을 애플리케이션 코드 대신 스프링 컨테이너가 담당한 관리하는 것을 뜻한다.
>   - 즉, 객체를 제어하고 관리하는 역할이 개발자로부터 스프링 컨테이너로 역전된다는 뜻이다.
> - **Bean과 스프링 컨테이너**
>   - Bean
>     - 스프링 컨테이너가 관리하는 자바 객체를 뜻한다.
>   - 스프링 컨테이너
>     - 스프링에서 빈(Bean)을 관리하는 공간을 뜻한다.
>     - 스프링 컨테이너는 IoC 컨테이너 혹은 DI 컨테이너라고도 불리는데, 이는 스프링 컨테이너가 IoC 혹은 DI를 도맡아 진행하기 때문이다.
>     - 스프링 컨테이너는 크게 두 종류(BeanFactory, ApplicationContext)로 나눌 수 있다.
>     - ApplicationContext 컨테이너가 BeanFactory의 기능을 포괄하면서 추가적인 기능을 제공하기 때문에 대부분의 경우에는 ApplicationContext를 사용한다.
>       - BeanFactory와 ApplicationContext 관계
>         ![image](https://github.com/Young-Geun/TIL/assets/27760576/846e9d7f-aa86-464f-8628-560cc2ac2b8a)
>       - BeanFactory
>         - 스프링 컨테이너의 최상위 인터페이스이다.
>         - 스프링 빈을 관리하고 조회하는 역할을 담당한다.
>       - ApplicationContext
>         - BeanFactory 기능을 모두 상속받아서 제공한다.
>         - 다음과 같은 부가기능들을 제공한다.
>           1. 메시지 소스를 활용한 국제화 기능
>           2. 환경변수 - 로컬, 개발, 운영 등을 구분해서 처리
>           3. 애플리케이션 이벤트 관리
>           4. 편리한 리소스 조회
> - **IoC 사용 이점**
>   - 의존성 관리를 IoC 컨테이너가 하므로 개발자는 비즈니스 로직에만 신경을 쓰면 된다.
>   - 객체의 생성과 소멸 등 생명주기를 관리해주므로 메모리를 효율적으로 사용할 수 있다.
>   - 라이프사이클 인터페이스를 이용하여 원하는 작업을 할 수 있다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/14)
</details>



<details>
<summary><h4>스프링 AOP</h4></summary>

> - **AOP(Aspect Oriented Programming)란?**
>   - Aspect Oriented Programming의 약자로 관점 지향 프로그래밍이라고 불린다.
>   - 흩어진 관심사(Crosscutting Concerns)를 모듈화하여 제공하는 프로그래밍 기법이다.
> - **AOP 핵심 용어**
>   - Aspect
>     - 여러 핵심 기능에 적용될 관심사 모듈을 뜻한다.
>     - Aspect는 구체적인 기능을 구현한 Advice와 Advice가 어디에서 적용될지를 결정하는 PointCut의 포괄적인 개념이다.
>   - JoinPoint
>     - 추상적인 개념으로 Advice가 적용될 수 있는 모든 위치를 뜻한다.
>     - 애플리케이션의 어떤 지점에 AOP를 사용하여 추가적인 로직을 삽입할 지 정의한다.
>   - Advice
>     - JoinPoint에서 실행되는 코드를 말한다.
>     - 로그 출력이나 트랜잭션 관리 등의 코드가 기술된다.
>   - Target
>     - Aspect를 적용할 대상을 뜻한다.
>     - 적용 방식에 따라 클래스, 메서드 등이 될 수 있다.
>   - Pointcut
>     - JoinPoint 중에서 Advice가 적용될 위치를 선별하는 기능이다.
>     - 이를통해 메서드명에 'service' 라는 문자열이 있을때만 어드바이스를 호출되도록 기술하는 것이 가능해진다.
>   - Advisor
>     - 스프링 AOP에서만 사용되는 용어로 Advice + Pointcut 한 쌍을 일컫는다.
>   - Weaving
>     - Pointcut으로 결정한 타겟의 JoinPoint에 Advice를 적용하는 것을 뜻한다.
> - **적용방식**
>   - 컴파일 시점
>     - .java 파일을 컴파일러를 통해 .class를 만드는 시점에 부가 기능 로직을 추가하는 방식이다.
>     - 모든 지점에 적용 가능하다.
>     - AspectJ가 제공하는 특별한 컴파일러를 사용해야 하기 때문에 특별할 컴파일러가 필요한 점과 복잡하다는 단점이 있다.
>   - 클래스 로딩 시점
>     - .class 파일을 JVM 내부의 클래스 로더에 보관하기 전에 조작하여 부가 기능 로직 추가하는 방식이다.
>     - 모든 지점에 적용 가능하다.
>     - 특별한 옵션과 클래스 로더 조작기를 지정해야하므로 운영하기 까다롭다.
>   - 런타임 시점
>     - 스프링이 사용하는 방식으로 컴파일이 끝나고 클래스 로더에 이미 다 올라가 자바가 실행된 다음에 동작하는 런타임 방식이다.
>     - 실제 대상 코드는 그대로 유지되고 프록시를 통해 부가 기능이 적용된다.
>     - 프록시는 메서드 오버라이딩 개념으로 동작하기 때문에 메서드에만 적용 가능하다.
>     - 특정 컴파일러, 복잡한 옵션, 클래스 로더 조작기 등을 사용하지 않아도 스프링만 있으면 AOP를 적용할 수 있다.
> - **스프링 AOP 특징**
>   - 순수 자바로 구현되었기 때문에 특별한 컴파일 과정이 필요하지 않다.
>   - 프록시 기반 AOP를 지원한다.
>   - Spring AOP는 메서드 조인 포인트만 지원한다.
> - **스프링 AOP Advice 종류**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/2c3dae3f-f8b6-4f69-b5ec-c54e52a16b29)
>   - @Before
>     - JointPoint가 실행되기 이전 시점에 실행된다.
>   - @After
>     - JointPoint의 정상 완료 여부에 상관없이 항상 실행된다.
>   - @AfterRetruning
>     - JointPoint가 정상 완료된 후 실행된다.
>   - @Around
>     - 메서드 호출 전후에 실행된다.
>   - @AfterThrowing
>     - 메서드가 예외를 던지는 경우 실행된다.
> - **장점**
>   - 중복된 코드를 최대한 제외하여 기능이 필요할 때만 호출하여 쓰기 때문에 재사용성이 높다.
>   - 애플리케이션 전체에 흩어진 공통 기능이 하나의 장소에서 관리되어 보다 유지보수가 수월하다.
>   - 핵심 로직과 부가 기능의 명확한 분리로, 개발자는 핵심 로직에 집중할 수 있게 된다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/17)
</details>



<details>
<summary><h4>스프링 PSA</h4></summary>

> - **PSA(Portable Service Abstraction)란?**
>   - 일관성 있는 서비스 추상화를 뜻한다.
>   - 추상화를 통해 하위 시스템을 알지 못하거나 변경이 있더라도 일관된 방식으로 접근할 수 있게 한다.
>   - 스프링에서의 대표적 PSA 예로는 트랜잭션이 있다.
> - **스프링의 트랜잭션 추상화 계층**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/2b9889f3-3921-44b7-9243-1ae3763c576e)
>   - 스프링에서는 위의 그림과 같이 'JDBC/Connection', 'JTA/UserTransaction', 'Hibernate/Transaction' 등 다양한 트랜잭션 기능을 제공하고 있다.   
>   - 개발자는 DB와 관련된 기능 개발 시, DB접근 기술에 따라 알맞은 트랜잭션 기술을 선택해야한다.   
만약 DB접근 기술이 바뀐다면 변경된 기술에 맞는 트랜잭션으로 변경이 필요하다.   
하지만 PSA가 접목되어 있다면 DB접근 기술과 관계없이 일관된 방식으로 트랜잭션을 제어할 수 있다.
>   - Ex) @Transactional은 각 각의 TransactionManager를 구현하고 있는 것이 아니라 최상위 PlatformTransactionManager를 사용하여 필요한 TransactionManager를 DI로 주입받아 사용한다. 이 때문에 @Transactional을 사용하여 트랜잭션을 관리할 경우, DB접근 기술이 JDBC에서 JPA로 변경되어도 트랜잭션에 대한 수정없이 트랜잭션 처리를 보장 받을 수 있는 것이다.

Ref.
[사바라다는 차곡차곡](https://sabarada.tistory.com/127)
</details>



<details>
<summary><h4>스프링 POJO</h4></summary>

> - **POJO (Plain Old Java Object)란?**
>   - '오래된 방식의 간단한 자바 객체' = '단순한 자바 오브젝트' 라는 뜻이다.
>   - 객체 지향적인 원리에 충실하면서 환경과 기술에 종속되지 않고 필요에 따라 재활용될 수 있는 방식으로 설계된 객체를 말한다.
> - **POJO의 조건**
>   - 특정 규약에 종속되면 안된다.
>   - 특정 환경에 종속되면 안된다.
>   - 객체 지향적 원리를 지켜야 한다.

Ref.
[미노드로그](https://onpups.pe.kr/386)
</details>



<details>
<summary><h4>빈 스코프(Bean Scope)</h4></summary>

> - **빈 스코프(Bean Scope) 란?**
>   - 스프링이 관리하는 빈이 생성되고, 존재하고, 적용되는 범위를 뜻한다.
> - **종류**
>   - Singleton
>     - 기본 스코프, 스프링 컨테이너의 시작과 종료까지 유지되는 가장 넓은 범위의 스코프
>   - Prototype
>     - 스프링 컨테이너는 프로토타입 빈의 생성과 의존관계 주입까지만 관여하고 더는 관리하지 않는 매우 짧은 범위의 스코프
>   - Request (* 웹 스코프)
>     - HTTP 요청 하나가 들어오고 나갈 때까지 유지되는 스코프
>     - 각각의 HTTP 요청마다 별도의 빈 인스턴스가 생성되고 관리된다.
>   - Session (* 웹 스코프)
>     - HTTP Session과 동일한 생명주기를 가지는 스코프
>   - Application (* 웹 스코프)
>     - 서블릿 컨텍스트(ServletContext)와 동일한 생명주기를 가지는 스코프
>   - Websocket (* 웹 스코프)
>     - 웹 소켓과 동일한 생명주기를 가지는 스코프   
>   - `* 웹 스코프 : 웹 스코프는 웹 환경에서만 동작한다.`

Ref.
[코드 연구소](https://code-lab1.tistory.com/186)
</details>



<details>
<summary><h4>@Transactional</h4></summary>
  
> - **트랜잭션이란?**
>   - 트랜잭션은 데이터베이스의 상태를 변환시키는 하나의 논리적 기능을 수행하기 위한 작업의 단위 또는 한꺼번에 수행되어야 할 일련의 연산을 의미한다.
> - **트랜잭션 특징(ACID)**
>   - 원자성 (Atomicity)
>     - 트랜잭션의 연산은 데이터베이스에 모두 반영되던지 아니면 모두 반영되지 않아야 한다.
>     - 트랜잭션 내의 모든 명령은 반드시 완벽히 수행되어야 하며, 하나라도 오류가 발생하면 트랜잭션 전부가 취소되어야 한다. 
>   - 일관성 (Consistency)
>     - 트랜잭션 처리 전과 처리 후 데이터 모순이 없는 상태를 유지하는 것을 의미한다.
>     - 예를 들어서 티스토리 게시판에 글을 쓰는데 제목의 글자 제한이 255 자라고 하자. 트랜잭션이 일어나면 이러한 조건을 만족해야 하는 것이다. 만약 이를 위반하는 트랜잭션이 있다면 거부해야 한다.
>   - 독립성 (Isolation)
>     - 둘 이상의 트랜잭션이 동시에 실행되는 경우 다른 트랜잭션의 연산이 끼어들 수 없다.
>     - 수행 중인 트랜잭션은 완전히 완료될 때까지 다른 트랜잭션에서 수행 결과를 참조할 수 없다.
>   - 지속성 (Durability)
>     - 성공적으로 완료된 트랜잭션의 결과는 영구적으로 반영되어야 한다.
> - **@Transactional**
>   - @Transactional 어노테이션은 스프링에서 많이 사용되는 선언적 트랜잭션 방식이다.
>   - 클래스 또는 메서드 위에 @Transactional을 붙이면 트랜잭션 기능이 적용된 프록시 객체가 생성되며, 트랜잭션 성공 여부에 따라 Commit 또는 Rollback 작업이 이루어진다.
> - **JDK Proxy(Dynamic Proxy) VS CGLib**
>   - 스프링에서 사용하는 프록시 구현체는 JDK Proxy(Dynamic Proxy), CGLib가 있다.
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/3e9696e2-29c2-4b92-a8b3-260b924ad2cb)
>   - JDK Dynamic Proxy
>     - Target 클래스가 인터페이스 구현체일 경우 생성되며, 구현 클래스가 아닌 인터페이스를 프록시 객체로 구현해서 코드에 끼워 넣는 방식이다.
>   - CGLib Proxy
>     - 스프링에서 사용하는 디폴트 프록시 생성방식으로, Target 클래스를 프록시 객체로 생성하여 코드에 끼워 넣는 방식이다.
>     - JDK 방식은 java.lang.Reflection을 이용해서 동적으로 프록시를 생성해 준다. 해당 방식의 단점은 AOP 적용을 위해 반드시 인터페이스를 구현해야 된다는 점, 리플렉션은 private 접근이 가능하다는 점 때문에 스프링 부트에선 기본 방식으로 CGLib 방식을 채택하였다.
> - **격리 수준 (Isolation Level)**
>   - DEFAULT
>     - 데이터베이스에서 설정된 기본 격리 수준을 따른다. 
>   - READ_UNCOMMITED
>     - 트랜잭션이 아직 커밋되지 않은 데이터를 읽을 수 있다.
>     - 세 가지 동시성 부작용(Dirty read, Nonrepeatable read, Phantom read)이 모두 발생한다.
>   - READ_COMMITED
>     - Dirty Read를 방지하기 위해 Commit 된 데이터만 읽을 수 있다.
>     - 나머지 부작용(Nonrepeatable read, Phantom read)은 여전히 발생할 수 있다.
>   - REPEATABLE READ
>     - 트랜잭션이 완료될 때까지 조회한 모든 데이터에 shared lock이 걸리므로 트랜잭션이 종료될 때까지 다른 트랜잭션은 그 영역에 해당하는 데이터를 수정할 수 없다.
>     - Phantom read 부작용은 여전히 발생한다.
>   - SERIALIZABLE
>     - 가장 엄격한 트랜잭션 격리 수준으로, 완벽한 읽기 일관성 모드를 제공한다.
>     - 이 격리 수준에서는 PHANTOM READ 상태가 발생하지 않지만 동시성 처리 성능이 급격히 떨어질 수 있다.
> - **전파 옵션 (Propagation)**
>   - REQUIRED
>     - 이미 시작된 트랜잭션이 있으면 참여하고, 없으면 새로운 트랜잭션을 시작한다.
>   - SUPPORTS
>     - 이미 시작된 트랜잭션이 있으면 참여하고, 없으면 트랜잭션 없이 처리한다.
>   - MANDATORY
>     - 이미 시작된 트랜잭션이 있으면 참여하고, 없으면 예외를 발생시킨다.
>     - 독립적으로 트랜잭션을 진행하면 안 되는 경우 사용한다.
>   - NEVER
>     - 트랜잭션을 사용하지 않도록 강제한다.
>     - 이미 진행 중인 트랜잭션 또한 허용하지 않으며, 있다면 예외를 발생시킨다.
>   - NOT_SUPPORTED
>     - 트랜잭션을 사용하지 않고 처리하도록 합니다. 이미 진행 중인 트랜잭션이 있다면 잠시 보류시킨 후 트랜잭션 없이 진행한다.
>   - REQUIRES_NEW
>     - 항상 새로운 트랜잭션을 시작한다.
>     - 이미 진행 중인 트랜잭션이 있다면 잠시 보류시킨다.
>   - NESTED
>     - 이미 실행 중인 트랜잭션이 있다면 중첩하여 트랜잭션을 진행한다.
>     - 부모 트랜잭션은 중첩 트랜잭션에 영향을 주지만 중첩 트랜잭션은 부모 트랜잭션에 영향을 주지 않는다.
> - **rollbackFor, noRollbackFor**
>   - rollbackFor
>     - 특정 예외가 발생하면 강제로 Rollback 한다.
>   - noRollbackFor
>     - 특정 예외가 발생하더라도 Rollback 하지 않는다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/139)
</details>



<details>
<summary><h4>JDK Dynamic Proxy VS CGLIB Proxy</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>Spring Filter vs Interceptor</h4></summary>
 
> - **Filter vs Interceptor**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/d84d0e77-2367-4f49-ae76-4c102288cd41)
>   - Filter
>     - 관리 컨테이너 : 웹 컨테이너
>     - DispatcherServlet 이전에 실행된다.
>     - 일반적으로 인코딩 변환 처리, XSS방어 등에 대한 처리로 사용된다.
>   - Interceptor
>     - 관리 컨테이너 : 스프링 컨테이너
>     - Dispatcher servlet에서 Handler(Controller)로 가기 전에 정보를 처리한다.
>     - 로그인 체크, 권한 체크, 프로그램 실행시간 계산, 로그 확인 등에 대한 처리로 사용된다.

Ref.
[망나니개발자](https://mangkyu.tistory.com/173)
</details>



<details>
<summary><h4>ORM, JPA, Hibernate, Spring Data JPA 개념</h4></summary>

> - **ORM이란?**
>   - ORM이란 Object-Relational Mapping의 약자로, 객체(Object)와 관계형 데이터(Relational data)를 매핑하기 위한 기술이다.
> - **ORM과 SQL Mapper의 차이점**
>   - ORM
>     - Object와 DB테이블을 매핑하여 데이터를 객체화하는 기술이다.
>     - SQL 문을 직접 작성하지 않아도 메서드로 데이터를 조작할 수 있다. (객체 간 관계를 바탕으로 SQL문을 자동으로 생성한다.)
>     - DBMS에 종속적이지 않다.
>     - 관련기술 : JPA, Hibernate
>   - SQL Mapper
>     - Object와 SQL의 필드를 매핑하여 데이터를 객체화하는 기술이다.
>     - SQL 문으로 직접 디비를 조작한다.
>     - DBMS에 종속적이다.
>     - 관련기술 : Mybatis, jdbcTemplate
> - **JPA란?**
>   - JPA는 Java Persistence API의 약자로, 자바 애플리케이션에서 관계형 데이터베이스를 사용하는 방식을 정의한 인터페이스이다.
>   - 여기서 중요하게 여겨야 할 부분은 JPA는 특정 기능을 가지고 있는 라이브러리가 아니고 말 그대로 인터페이스라는 점이다.
>   - 따라서 JPA를 사용하기 위해서는 JPA를 구현한 Hibernate, EclipseLink, DataNucleus와 같은 ORM 프레임워크를 사용해야 한다.
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/27a0e8c2-59de-42fc-bda0-d76fa1957350)
> - **Hibernate란?**
>   - JPA 구현체의 한 종류이다. 
>   - JPA와 Hibernate는 마치 자바의 interface와 해당 interface를 구현한 class와 같은 관계이다.
> - **Spring Data JPA란?**
>   - Spring Data JPA는 Spring Framework에서 제공하는 모듈 중 하나로, 개발자가 JPA를 더 쉽고 편하게 사용할 수 있도록 도와주는 기술이다.
> - **JPA, Hibernate, Spring Data JPA 관계**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/86508652-90c4-4618-9353-0fe473fcc54b)

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/140)
</details>



<details>
<summary><h4>단위테스트와 통합테스트</h4></summary>

> - **테스트의 개념**
>   - 테스트란?
>     - 테스트란 개발자가 작성한 코드가 의도된 대로 정확히 작동하는지 검증하는 절차이다.
>   - 작성해야하는 이유
>     - 개발 과정 중 예상치 못한 문제를 미리 발견할 수 있다.
>     - 작성한 코드가 의도한 대로 작동하는지 검증할 수 있다.
>     - 코드 수정이 필요한 상황에서 유연하고 안정적인 대응할 할 수 있게 해 준다.
>     - 리팩토링 시 기능 구현이 동일하게 되었다는 판단을 내릴 수 있다.
>     - 문서로서의 역할이 가능하다.
> - **테스트의 종류**
>   - Unit Test(단위 테스트)
>     - 하나의 모듈을 기준으로 독립적으로 진행되는 가장 작은 단위의 테스트이다.
>     - 단위 테스트는 애플리케이션을 구성하는 하나의 기능, 하나의 함수가 올바르게 동작하는지를 독립적으로 테스트하는 것으로, 각각의 조건에 대한 유효성을 검증한다.
>   - Integration Test(통합 테스트)
>     - 모듈을 통합하는 과정에서 서로 다른 모듈 혹은 클래스 간 상호작용의 유효성을 검증하는 테스트이다.
>     - 단위 테스트보다 더 넓은 범위의 종속성까지 테스트함으로써 단위 테스트보다 좀 더 유의미한 테스트가 되는 경우도 많다.
> - **테스트별 장·단점**
>   - Unit Test(단위 테스트)
>     - 장점 1. WebApplication 관련된 Bean들만 등록하기 때문에 통합 테스트보다 빠르다.
>     - 장점 2. 통합 테스트가 어려운 테스트를 진행할 수 있다.
>     - 단점 1. 요청부터 응답까지 모든 테스트를 Mock 기반으로 테스트하기 때문에 실제 환경에서는 제대로 동작하지 않을 수 있다.
>   - Integration Test(통합 테스트)
>     - 장점 1. 스프링 부트 컨테이너를 띄워 테스트하기 때문에 운영환경과 가장 유사한 테스트가 가능하다.
>     - 장점 2. 전체적인 Flow를 쉽게 테스트할 수 있다.
>     - 단점 1. 애플리케이션의 설정, 모든 Bean을 로드하기 때문에 시간이 오래 걸리고 무겁다.
>     - 단점 2. 테스트 단위가 커 디버깅이 어렵다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/141)
</details>



<details>
<summary><h4>단위테스트</h4></summary>

> - **F.I.R.S.T 원칙**
>   - F.I.R.S.T 원칙이란 좋은 단위 테스트를 하기 위한 5가지 요소를 뜻한다.
>     - Fast
>       - 빠르게 실행되고 빠르게 결과를 알아야 한다. 이를 위해서는 하는 일의 단위가 최대한 작아야 한다.
>       - 빠른 테스트를 위해 실제 서버나 데이터베이스를 이용하지 않고 가짜 데이터(모의 데이터)를 만들어서 테스트를 진행해야 한다.
>     - Independent
>       - 독립적이어야 하고 다른 테스트에 의존하거나 영향을 주어선 안된다.
>     - Repeatable
>       - 유닛 테스트는 반복 가능해야 하며, 몇 번을 진행하든 똑같은 결과가 나와야 한다.
>     - Self-Validating
>       - 자체 검증 가능해야 한다.
>       - 테스트 자체로 통과인지 실패인지 결과가 나와야 하며 이것은 자동적으로 이뤄져야 한다.
>     - Thorough / Timely
>       - 유닛 테스트는 철저하고 적절한 때에 작성되어야 한다.
>       - 철저하다는 것은 모든 데이터를 검사해야 하므로 최소에서 최대까지 범위를 포함하고, 역할(사용자일 때 혹은 관리자일 때)에 따라서 바뀌는 데이터를 모두 테스트가 가능해야하며 어떤 케이스가 실패(예외나 오류)하는지도 테스트해야 한다.
> - **단위테스트와 JUnit**
>   - JUnit
>     - 자바에는 JUnit이라는 단위 테스트를 위한 테스팅 프레임워크가 존재한다.
>     - JUnit을 활용하여 단위테스트를 진행한다면, 테스트 결과를 문서로 남기는 것이 아니라 Test Class 자체를 남기기 때문에 코드에 대한 History를 남길 수 있다는 장점이 있다.
> - **JUnit 주요 단언(Assertion) 메서드**
>   - assertEquals(expected, actual) / assertNotEquals(unexpected, actual)
>     - 실제 값(actual)이 기대하는 값(expected)과 같은지 / 같지 않은지 검사한다.
>   - assertSame(Object expected, Object actual) / assertNotSame(Object unexpected, Object actual)
>     - 두 객체가 동일한 / 동일하지 않은 객체인지 검사한다.
>   - assertTrue(boolean condition) / assertFalse(boolean condition)
>     - 값이 true / false인지 검사한다.
>   - assertNull(Object actual) / assertNotNull(Object actual)
>     - 값이 null인지 / null이 아닌지 검사한다.
>   - assertThrows(Class<T> expectedType, Executable executable)
>     - executable을 실행한 결과로 지정한 타입의 익셉션이 발생하는지 검사한다.
> - **JUnit 주요 어노테이션**
>   - @Test
>     - 해당 메서드를 테스트 대상으로 지정한다.
>   - @BeforeAll
>     - 모든 테스트 시작 전에 수행되는 로직에 붙는 어노테이션으로 static을 붙여줘야 하며 접근 제어자는 default 이상이어야 한다.
>   - @AfterAll
>     - 모든 테스트 종료 후에 수행되는 로직에 붙는 어노테이션으로 static을 붙여줘야 하며 접근 제어자는 default 이상이어야 한다.
>   - @BeforeEach
>     - 모든 @Test 어노테이션이 붙은 테스트 대상 메서드 수행 전마다 수행된다.
>   - @AfterEach
>     - 모든 @Test 어노테이션이 붙은 테스트 대상 메서드 수행 종료시마다 수행된다.
> - **Mockito**
>   - Mock이란 실제 객체를 만들어 사용하기에 시간, 비용 등의 Cost가 높거나 혹은 객체 서로 간의 의존성이 강해 구현하기 힘들 경우 가짜 객체를 만들어 사용하는 방법이다.
>   - 이러한 가짜(Mock) 객체를 만들 수 있도록 지원하는 프레임워크 중 Mockito라는 테스트 프레임워크가 있다.
> - **Mockito 주요 어노테이션**
>   - @ExtendWith
>   - @Mock
>   - @Spy
>   - @InjectMocks

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/142),
[Caffeine Overflow](https://caffeineoverflow.tistory.com/143)
</details>



<details>
<summary><h4>어노테이션(Annotation)</h4></summary>

> - **어노테이션(Annotation)이란?**
>   - Annotation(@)은 사전적 의미로는 주석이라는 뜻이다.
>   - 자바에서 Annotation은 코드 사이에 주석처럼 쓰이며 특별한 의미, 기능을 수행하도록 하는 기술이다.
>   - 프로그램에게 추가적인 정보를 제공해 주는 메타데이터라고 볼 수 있다.
> - **스프링의 주요 어노테이션**
>   - @ComponentScan
>     - 빈으로 등록될 준비를 마친 클래스들을 스캔하여, 빈으로 등록해 주는 어노테이션이다.
>     - @Component, @Service, @Repository, @Controller, @Configuration가 그 대상이 된다.
>   - @Component
>     - 개발자가 생성한 Class를 Spring의 Bean으로 등록할 때 사용하는 어노테이션이다.
>   - @Bean
>     - 개발자가 직접 제어가 불가능한 외부 라이브러리 등을 Bean으로 만들려 할 때 사용하는 어노테이션이다.
>   - @Configuration
>     - 설정 클래스임을 명시하거나 Bean을 등록하고자 할 때 사용하는 어노테이션이다.
>     - @Configuration을 클래스에 적용하고 @Bean을 해당 Class의 method에 적용하면 @Autowired로 Bean을 부를 수 있다.
>   - @Autowired
>     - 속성(field), setter method, constructor(생성자)에서 사용하며 Type에 따라 알아서 Bean을 주입해 준다.
>   - @Controller
>     - Presentation Layer의 MVC Controller에 사용한다.
>     - 스프링 웹 서블릿에 의해 웹 요청을 처리하는 컨트롤러 빈으로 선정한다.
>   - @RestController
>     - @Controller와 유사하나 컨트롤러가 Rest 방식을 처리하기 위한 것임을 명시한다.
>     - View로 응답하는 것이 아니라 반환 결과를 JSON 형태로 반환한다.
>   - @Service
>     - Service Class에서 쓰인다.
>     - 비즈니스 로직을 수행하는 Class라는 것을 나타내는 용도이다.
>   - @Repository
>     - DAO 또는 Repository 클래스에 사용한다.
>     - DataAccessException 자동변환과 같은 AOP 적용대상을 선정하기 위해 사용한다.
>   - @Value
>     - properties와 같은 설정파일에서 값을 가져와 적용할 때 사용한다.
>   - @Valid
>     - 유효성 검증이 필요한 객체임을 지정한다.
>   - @RequestBody
>     - 요청 데이터(JSON이나 XML형식)를 바로 Class나 model로 매핑하기 위한 Annotation이다.
>   - @ResponseBody
>     - HttpMessageConverter를 이용하여 JSON 혹은 xml로 요청에 응답할 수 있게 해주는 Annotation이다.
>     - view가 아닌 JSON 형식의 값을 응답할 때 사용하는 Annotation으로, 문자열을 리턴하면 그 값을 http response header가 아닌 response body에 들어간다.
>   - @Transactional
>     - 데이터베이스 트랜잭션을 설정하고 싶은 method에 Annotation을 적용하면 method 내부에서 일어나는 데이터베이스 로직이 전부 성공하게 되거나 데이터베이스 접근 중 하나라도 실패하면 다시 롤백할 수 있게 해주는 Annotation이다.
>   - @Cacheable
>     - method 앞에 지정하면 해당 method를 최초에 호출하면 캐시에 적재하고 다음부터는 동일한 method 호출이 있을 때 캐시에서 결과를 가져와서 return 하므로 method 호출 횟수를 줄여주는 Annotation이다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/145)
</details>



<details>
<summary><h4>@Value VS @ConfigurationProperties</h4></summary>

> - **용도**
>   - 스프링의 properties나 yaml에 있는 값들을 사용하기 위한 어노테이션이다.
> - **@Value**
>   - 단일 값 주입만 할 수 있다.
>   - RelaxedBinding이 불가능하다.
>   - spEL 적용이 가능하다.
> - **@ConfigurationProperties**
>   - 복수의 값을 바인딩할 수 있다.
>   - RelaxedBinding이 가능하다.
>   - spEL 적용이 불가능하다.

Ref.
</details>



<details>
<summary><h4>주요 HTTP 메서드(GET, POST, PUT, PATCH, DELETE)</h4></summary>

> - **GET**
>   - GET 메서드는 리소스의 조회를 위해 사용한다.
>   - 서버에 전달하고 싶은 데이터가 있다면 query(쿼리 파라미터, 쿼리 스트링)에 담아 보낸다.
> - **POST**
>   - POST 메서드는 요청 데이터의 처리를 목적으로 사용한다.
>   - 메시지 바디를 통해 서버로 요청 데이터를 전달하면, 서버는 정해진 로직에 따라 요청 데이터를 처리한다.
>   - 주로, 전달된 데이터를 이용하여 신규 리소스를 등록하거나 프로세스를 처리한다.
> - **PUT**
>   - PUT 메서드는 리소스 전체를 대체한다.
>   - 기존 리소스가 없을 경우 새로 생성한다. 즉, 덮어쓰기를 수행한다고 볼 수 있다.
>   - POST와 차이점은 클라이언트가 리소스의 위치를 알고 URI를 명시해야 한다는 점이다.
> - **PATCH**
>   - PATCH 메서드는 리소스를 부분 변경한다.
>   - 부분 변경이 필요한 상황에서 PATCH를 사용할 수 없다면 POST를 사용한다.
> - **DELETE**
>   - DELETE 메서드는 리소스를 제거한다.

Ref.
[woply](https://velog.io/@woply/HTTP-%EC%A3%BC%EC%9A%94-%EB%A9%94%EC%84%9C%EB%93%9C-5%EA%B0%80%EC%A7%80-%EC%A0%95%EB%A6%ACGET-POST-PUT-PATCH-DELETE)
</details>



<details>
<summary><h4>REST(Representational State Transfer)와 RESTful</h4></summary>

> - **REST(Representational State Transfer)란?**
>   - 자원을 이름(자원의 표현)으로 구분하여 해당 자원의 상태(정보)를 주고 받는 모든 것을 의미한다.
>   - HTTP URI를 통해 자원을 명시하고, HTTP Method(POST, GET, PUT, DELETE)를 통해 해당 자원에 대한 CRUD 수행한다.
> - **REST의 구성 요소**
>   - 자원(Resource) : HTTP URI
>   - 자원에 대한 행위(Verb) : HTTP Method
>   - 자원에 대한 행위의 내용 (Representations) : HTTP Message Pay Load
> - **RESTful이란?**
>   - REST의 원리를 따르는 시스템을 의미한다.
> - **RESTful의 제약조건**
>   - 클라이언트-서버(Client-Server)
>     - 관심사의 명확한 분리가 선행되면 서버의 구성요소가 단순화되고, 확장성이 향상되어 여러 플랫폼을 지원할 수 있다.
>   - 무상태성(Stateless)
>     - 서버에 클라이언트의 상태 정보를 저장하지 않는 것을 말한다.
>     - 단순히 들어오는 요청만 처리하여 구현을 더 단순화시킨다.
>   - 캐시 가능(Cacheable)
>     - 클라이언트의 요청에 대한 응답을 캐시할 수 있어야 한다.
>   - 계층화 시스템(Layered System)
>     - 서버는 중개서버나 로드 밸런싱, 공유 캐시 등의 기능을 사용하여 확장성 있는 시스템을 구성할 수 있다.
>   - 코드 온 디맨드(Code on demand)
>     - 클라이언트 서버에서 자바 애플릿, 자바스크립트 실행 코드를 전송받아 기능을 일시적으로 확장할 수 있다.
>   - 인터페이스 일관성(Uniform interface)
>     - URI로 지정된 리소스에 균일하고 통일된 인터페이스를 제공한다.
>     - 아키텍처를 단순하게 분리하여 독립적으로 만들 수 있다.

Ref.
</details>



<details>
<summary><h4>Hateoas(Hypermedia As The Engine Of Application State)</h4></summary>

> - **Hateoas란?**
>   - 클라이언트의 요청으로부터 응답을 할 때, 요청 이외의 관련된 URI를 응답에 추가적으로 포함시켜 반환하는 개념이다.
>   - 예를 들어, 클라이언트가 사용자를 조회했을 때 사용자 정보만 응답하는 것이 아니라 '사용자 수정', '사용자 삭제' 등을 처리할 수 있는 링크를 같이 포함하여 응답하는 것을 예시로 들 수 있다.
> - **장점**
>   - 요청 URI가 변경되더라도 클라이언트는 이에 대응하여 코드를 변경하지 않아도 된다.
>   - Resource가 포함된 URI를 보여주기 때문에, Resource에 대한 신뢰도를 높일 수 있다.
> - **단점**
>   - 전달되는 data의 크기가 커져서 네트워크 오버헤드가 생길 수 있다.
>   - 링크가 복잡해질 수 있다.

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/28)
</details>



<details>
<summary><h4>CORS</h4></summary>

> - **CORS란?**
>   - 교차 출처 리소스 공유(Cross-origin Resource Sharing)는 추가 HTTP헤더를 사용하여, 한 출처에서 실행 중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에 알려주는 체제이다.
> - **출처(Origin)란?**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/ab8e57b2-8ff9-454c-9f3e-d62489c8fe3a)
>   - 출처(Origin)란 위의 URL 구조에서 Protocol, Host, Port를 합친 것을 의미한다.
>   - 즉, 다른 출처란 Protocol, Host, Port 중 한 개라도 다른 것을 의미한다.
> - **동일 출처 정책(Same-Origin Policy)이란?**
>   - CORS policy 오류가 발생하는 이유는 브라우저가 동일 출처 정책(Same-Origin Policy, SOP)을 지켜서 다른 출처의 리소스 접근을 금지하기 때문이다.

Ref.
[Beomy](https://beomy.github.io/tech/browser/cors/)
</details>



<details>
<summary><h4>CI/CD</h4></summary>

> - **CI/CD란?**
>   - CI/CD란 지속적 통합과 지속적 배포가 통합된 방식을 일컫는다.
> - **CI(Continuous Integration)**
>   - 어플리케이션에 대한 새로운 코드 변경사항이 주기적으로 빌드 및 테스트되어 공통 저장소에 통합되는 개념이다.
>   - 다수의 개발자가 형상관리 툴을 공유하는 경우라면, 자동화된 빌드 및 테스트는 원천 소스코드의 충돌을 방어할 수 있는 장점을 가지고 있다.
> - **CD(Continuous Delivery 또는 Continuous Deployment)**
>   - 배포 자동화 과정을 뜻한다.
>   - CI가 새로운 소스코드의 빌드, 테스트, 병합을 의미한다면 CD는 개발자의 변경 사항을 넘어 고객의 환경까지 릴리즈 되는 것을 의미한다.

Ref.
</details>



<details>
<summary><h4>PRG(POST-Redirect-GET) 패턴</h4></summary>

> - **PRG 패턴이란?**
>   - 웹 디자인 패턴 중 하나로 POST요청에 대한 응답으로 리다이렉트를 통해 GET요청을 할 수 있도록 처리하는 패턴이다.
> - **상세 순서**
>   - 클라이언트는 HTTP POST 요청을 한다.
>   - 서버는 클라이언트에게 'URL'과 'GET요청으로 Redirect 할 수 있는 응답코드(302)'를 응답한다.
>   - Redirection을 통해 서버에게 응답받은 URL로 GET 요청을 한다.
> - **적용하지 않았을 시 문제점**
>   - 데이터를 POST요청으로 보낸 후 클라이언트가 새로고침을 할 경우, 중복 요청이 발생하여 예기치않은 문제점이 발생할 수 있다.

Ref.
</details>



<details>
<summary><h4>Maven과 Gradle</h4></summary>

> - **빌드와 빌드 관리 도구**
>   - Maven과 Gradle은 모두 빌드 관리 도구이다.
>   - 빌드(Build)
>     - 빌드는 소스코드 파일을 컴퓨터에서 실행할 수 있는 독립적인 형태로 변환하는 과정과 결과를 말한다.
>     - 개발자가 작성한 소스코드(.java), 프로젝트에서 쓰인 각 각의 파일 및 자원(.xml, .jpa, .jpg, properties)을 jvm이나 톰캣 같은 WAS가 인식할 수 있도록 패키징하는 과정 및 결과물을 일컫는다.
>   - 빌드 관리 도구(Build Tool)
>     - 빌드 도구란, 소스코드에서 애플리케이션을 생성하면서 여러가지 외부 라이브러리를 사용하는데, 빌드 관리 도구를 사용하게 되면 사용자가 이를 관리하지 않아도 된다.
>     - 필드 관리 도구는 다음과 같은 작업을 수행한다.
>       1. 종속성 다운로드 - 전처리(Preprocessing)
>       2. 소스코드를 바이너리 코드로 컴파일(Compile)
>       3. 바이너리 코드를 패키징(Packaging)
>       4. 테스트 실행(Testing)
>       5. 프로덕션 시스템에 배포(distribution)
>     - 빌드 툴로는 Ant, Maven, Gradle 등이 있다.
> - **Maven**
>   - Maven은 Java 전용 프로젝트 관리 도구로써 Lifecycle 관리 목적 빌드 도구이며, Apache Ant의 대안으로 만들어졌다.
>   - 정해진 Lifecycle에 의하여 작업을 수행하며, 전반적인 프로젝트 관리 기능을 포함하고 있다.
>   - clean - validate - compile - test - package - verify - install - site - deploy의 라이프 사이클을 가진다.
>     - clean : 빌드 시 생성되어있었던 파일들을 삭제한다.
>     - validate : 프로젝트가 올바른지 확인하고 필요한 모든 정보를 사용할 수 있는지 확인하는 단계
>     - compile : 프로젝트 소스코드를 컴파일 하는 단계
>     - test : 단위 테스트를 수행하는 단계. 테스트 실패 시 빌드 실패로 처리하며, 스킵이 가능하다.
>     - package : 실제 컴파일된 소스 코드와 리소스들을 jar, war 등의 파일의 배포를 위한 패키지로 만든다.
>     - verify : 통합 테스트 결과에 대한 검사를 실행하여 품질 기준을 충족하는지 확인한다.
>     - site : 프로젝트 문서와 사이트 작성, 생성하는 단계
>     - deploy : 만들어진 package를 원격 저장소에 release하는 단계
> - **Gradle**
>   - Maven을 대체할 수 있는 프로젝트 구성 관리 및 범용 빌드 툴이며, Ant Builder와 Groovy script를 기반으로 구축되어 기존 Ant의 역할과 배포 스크립의 기능을 모두 사용가능하며 스프링부트와 안드로이드에서 사용된다.
>   - 빌드 속도가 Maven에 비해 10~100배 가량 빠르며, Java, C/C++, Python 등을 지원한다.
> - **Gradle의 장점**
>   - 가독성
>     - 코딩에 의한 간결한 정의가 가능하므로 가독성이 좋다.
>   - 재사용 용이
>     - 설정 주입 방식(Configuration Injection)을 사용하므로 재사용에 용이하다.
>   - 구조적인 장점
>     - Build Script를 Groovy기반의 DSL(Domail Specific Language)을 사용하여 코드로서 설정 정보를 구성하므로 구조적인 장점이 있다.
>   - 편리함
>     - Gradle 설치 없이 Gradle wrapper를 이용하여 빌드를 지원한다.
>   - 멀티 프로젝트
>     - Gradle은 멀티 프로젝트 빌드를 지원하기 위해 설계된 빌드 관리 도구이다.
>   - Maven 지원
>     - Maven을 완전 지원한다.
>   - 빌드와 테스트 실행 속도
>     - 빌드와 테스트 실행 결과 Gradle이 더 빠르다
>     - 캐시를 사용하므로 테스트 반복 시 실행 결과 시간의 차이가 더 커진다.

Ref.
[smlee](https://velog.io/@leesomyoung/Maven%EA%B3%BC-Gradle%EC%9D%98-%EC%B0%A8%EC%9D%B4-%EB%B0%8F-%EB%B9%84%EA%B5%90)
</details>



<details>
<summary><h4>웹 브라우저에 URL 입력 시 일어나는 일련의 과정</h4></summary>

> 1. 브라우저 주소창에 maps.google.com을 입력한다.
> 2. 브라우저가 maps.google.com의 IP 주소를 찾기 위해 캐시에서 DNS 기록을 확인한다.
>     - DNS 기록을 찾기 위해서, 브라우저는 네 개의 캐시를 확인한다.
>       1. DNS 쿼리는 우선 브라우저 캐시를 확인한다. 브라우저는 내가 이전에 방문한 웹 사이트의 DNS 기록을 일정 기간 동안 저장하고 있다.
>       2. 브라우저는 OS 캐시를 확인한다. 브라우저 캐시에 원하는 DNS 레코드가 없다면, 브라우저가 내 컴퓨터 OS에 시스템 호출(ex. 윈도우에서 gethostname 호출)을 통해 DNS 기록을 가져온다.
>       3. 브라우저는 라우터 캐시를 확인한다. 만약 컴퓨터에도 원하는 DNS 레코드가 없다면, 브라우저는 라우터에서 DNS 기록을 저장한 캐시를 확인한다.
>       4. ISP 캐시를 확인한다. 만약 위 모든 단계에서 DNS 기록을 찾지 못한다면, 브라우저는 ISP에서 DNS 기록을 찾는다. ISP(Internet Service Provider)는 DNS 서버를 가지고 있는데, 해당 서버에서 DNS 기록 캐시를 검색할 수 있다.  
> 3. 만약 요청한 URL(maps.google.com)이 캐시에 없다면, ISP의 DNS 서버가 DNS 쿼리로 maps.google.com을 호스팅하는 서버의 IP 주소를 찾는다.
> 4. 브라우저가 해당 서버와 TCP 연결을 시작한다.
>     - 브라우저가 올바른 IP 주소를 수신하면 IP 주소와 일치하는 서버와 연결해 정보를 전송한다.
>     - 브라우저는 인터넷 프로토콜(IP, Internet Protocol)을 사용하여 이러한 연결을 구축한다.
>     - 사용할 수 있는 여러가지의 인터넷 프로토콜이 있지만, 일반적으로 HTTP 요청에서는 TCP(Transmission Control Protocol)라는 전송 제어 프로토콜을 사용한다.
>     - TCP 연결은 TCP/IP 3-way handshake라는 연결 과정을 통해 이뤄진다.
>       1. 클라이언트는 인터넷을 통해 서버에 SYN 패킷을 보내 새 연결이 가능한지 여부를 묻는다.
>       2. 서버에 새 연결을 수락할 수 있는 열린 포트가 있는 경우, SYN/ACK 패킷을 사용하여 SYN 패킷의 ACK(승인)으로 응답한다.
>       3. 클라이언트는 서버로부터 SYN/ACK 패킷을 수신하고 ACK 패킷을 전송하여 승인한다.
> 5. 브라우저가 웹서버에 HTTP 요청을 보낸다.
> 6. 서버가 요청을 처리하고 응답(response)을 보낸다.
> 7. 서버가 HTTP 응답을 보낸다.
> 8. 브라우저가 HTML 컨텐츠를 보여준다.

Ref.
[khy__.log](https://velog.io/@khy226/%EB%B8%8C%EB%9D%BC%EC%9A%B0%EC%A0%80%EC%97%90-url%EC%9D%84-%EC%9E%85%EB%A0%A5%ED%95%98%EB%A9%B4-%EC%96%B4%EB%96%A4%EC%9D%BC%EC%9D%B4-%EB%B2%8C%EC%96%B4%EC%A7%88%EA%B9%8C)
</details>



<details>
<summary><h4>[JPA] 영속성 관리</h4></summary>

> - **영속성 컨텍스트란?**
>   - 영속성 컨텍스트는 엔티티를 영구 저장하는 환경이다.
>   - 엔티티 매니저를 통해서 영속성 컨텍스트에 접근할 수 있고, 영속성 컨텍스트를 관리할 수 있다.
> - **엔티티의 생명주기**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/5ecec14d-0b5e-4fbb-a780-c8581408ff6f)
>   - 비영속(new/transient
>     - 영속성 컨텍스트와 전혀 관계가 없는 새로운 상태
>   - 영속(managed)
>     - 영속성 컨텍스트에 관리되는 상태
>   - 준영속(detached)
>     - 영속성 컨텍스트에 저장되었다가 분리된 상태
>   - 삭제(remove)
>     - 삭제된 상태
> - **영속성 컨텍스트의 특징**
>   - 1차 캐시
>     - 영속성 컨텍스트에 1차 캐시 존재
>     - 캐시는 map 형태로 key-value 저장
>   - 동일성 보장
>     - 같은 트랜잭션 안에서 같은 객체는 == 비교를 보장한다.
>   - 트랜잭션을 지원하는 쓰기 지연
>     - 한 트랜잭션 안에서 DB에 보낼 쿼리문을 모았다가 한 번에 보냄으로써 네트워크 부하를 줄 일 수 있다.
>   - 변경 감지
>     - 영속성 컨텍스트에서 보관하는 데이터에 변경이 일어났는지 확인이 가능하다.
>     - 만약 변경이 일어났다면 JPA가 UPDATE 쿼리문을 날려주기 때문에 값을 변경 후에 UPDATE 쿼리를 명시적으로 수행하지 않아도 된다.
>   - 지연 로딩
>     - 연관된 객체를 바로 조회하지 않고, 값이 사용되는 시점에 DB에서 가져온다.

Ref.
[공부기록](https://velog.io/@suk13574/JPA-%EC%98%81%EC%86%8D%EC%84%B1-%EC%BB%A8%ED%85%8D%EC%8A%A4%ED%8A%B8%EC%9D%98-%EC%A0%84%EB%B0%98%EC%A0%81%EC%9D%B8-%EC%9D%B4%ED%95%B4%EA%B0%9C%EB%85%90-%EC%9E%A5%EC%A0%90-%EB%8F%99%EC%9E%91-%EB%B0%A9)
</details>


<details>
<summary><h4>[JPA] N+1문제</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>[JPA] 즉시 로딩과 지연 로딩</h4></summary>

> - Title
>   - Content

Ref.
</details>





<br><br><br>
- - -
<br><br><br>





# DesignPatterns
<details>
<summary><h4>[GoF] 디자인 패턴이란?</h4></summary>

> - **GoF(Gang of Four)란?**
>   - 이 분야의 4인방(Gang of Four, 줄여 GoF)의 의미로 소프트웨어 설계에 있어 공통된 문제들에 대한 표준적인 해법과 작명법을 제안한 "Design Patterns" 책의 저자들을 지칭한다.
>   - 여러 가지 문제에 대한 설계 사례를 분석하여 서로 비슷한 문제를 해결하기 위한 설계들을 분류하고, 각 문제 유형별로 가장 적합한 설계를 일반화해 패턴으로 정립하였다.
> - **GoF 디자인 패턴의 유형**
>   - GoF(Gang of Four)에서는 23가지 디자인 패턴을 다음의 3가지 유형으로 분류한다.
>     - 생성 패턴(Creational Pattern)
>       - 객체를 생성하는데 관련된 패턴
>       - 객체가 생성되는 과정의 유연성을 높이고 손쉬운 코드의 유지
>       - 종류
>         - 싱글톤 (Singleton)
>         - 추상 팩토리 (Abstract Factory)
>         - 빌더 (Builder)
>         - 팩토리 메소드 (Factory Method)
>         - 프로토타입 (Prototype)
>     - 구조 패턴(Structural Pattern)
>       - 프로그램 구조에 관련된 패턴
>       - 프로그램 내의 자료구조 또는 인터페이스 구조 등 프로그램의 구조를 설계하는 데 활용 가능한 패턴
>       - 클래스나 객체를 조합해 더 큰 구조를 만드는 패턴
>       - 종류
>         - 어댑터 (Adapter)
>         - 브릿지 (Bridge)
>         - 합성 (Composite)
>         - 데코레이터 (Decorator)
>         - 파사드 (Facade)
>         - 플라이웨이트 (Flyweight)
>         - 프록시 (Proxy)
>     - 구조 패턴(Structural Pattern)
>     - 행동 패턴(Behavioral Pattern)
>       - 반복적으로 사용되는 객체들의 상호작용을 패턴화
>       - 결합도를 최소화하는 것에 중점
>       - 객체(클래스) 사이에 알고리즘이나 책임 분배에 관련 패턴
>       - 종류
>         - 책임연쇄 (Chain of Responsibility)
>         - 커맨드 (Command)
>         - 인터프리터 (Interpreter)
>         - 반복자 (Iterator)
>         - 중재자 (Mediator)
>         - 메멘토 (Memento)
>         - 옵저버 (Observer)
>         - 상태 (State)
>         - 전략 (Strategy)
>         - 템플릿 메소드 (Template Method)
>         - 방문자 (Visitor)

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/41)
</details>



<details>
<summary><h4>[GoF] 싱글톤(Singleton) 패턴</h4></summary>

> - **싱글톤(Singleton) 패턴**
>   - 싱글톤 패턴은 '하나'의 인스턴스만 생성하여 사용하는 디자인 패턴이다.
> - **싱글톤 패턴의 장점**
>   - 한 개의 인스턴스만을 생성하고 공유하기 때문에 메모리 낭비를 방지할 수 있다.
>   - 인스턴스를 매번 생성하는 것이 아니므로 속도 측면에서 이점이 있다.
>   - 전역으로 사용하는 인스턴스이기 때문에 다른 여러 클래스에서 데이터를 공유하며 사용할 수 있다.
> - **싱글톤 패턴의 단점**
>   - 의존성이 높아진다.
>   - 멀티스레딩 환경에서 동시성 문제가 발생할 수 있다.
> - **구현 예시**
>   - 싱글톤 패턴의 구현 방법은 매우 다양하지만 다음과 같은 공통사항을 가지고 있다.
>     - private 생성자만을 정의하여 외부 클래스로부터 인스턴스 생성을 막는다.
>     - 싱글톤을 구현하고자 하는 클래스 내부에 멤버 변수로써 private static 객체 변수를 만든다.
>     - public static 메서드를 통해 외부에서 싱글톤 인스턴스에 접근할 수 있도록 접점을 제공한다.
>   - ```
>     public class Singleton {
>     
>         private static Singleton instance;
>         
>         // 생성자를 private으로 하여 다른 클래스에서는 인스턴스를 만들지 못하게 한다. 
>         private Singleton() {}
>     
>         public static Singleton getInstance() {
>             /* 
>                 인스턴스를 사용하기 위하여 getInstance()를 호출하는데,
>                 최초 접근으로 아직 만들어지지 않았다면 인스턴스를 만들고
>                 그렇지 않다면 만들어진 인스턴스를 반환한다.            
>             */
>             if (instance == null) {
>                 instance = new Singleton();
>             }
>     
>             return instance;
>         }
>         
>     }
>     ```

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/50)
</details>


<details>
<summary><h4>[GoF] 팩토리 메서드 패턴</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>[GoF] 프록시 패턴</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>[GoF] 템플릿 메서드 패턴</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>[GoF] 전략 패턴</h4></summary>

> - Title
>   - Content

Ref.
</details>





<br><br><br>
- - -
<br><br><br>





# Database
<details>
<summary><h4>DDL, DML, DCL, TCL</h4></summary>

> - **DDL (Data Definition Language)**
>   - 데이터베이스의 구조를 정의할 때 사용하는 언어이다.
>   - DDL은 명령어를 입력하는 순간 작업이 즉시 반영(Auto Commit)되기 때문에 사용할 때 주의해야 한다.
>   - 종류
>     - CREATE : 테이블, 뷰 또는 인덱스와 같은 새 데이터베이스 개체를 생성
>     - ALTER : 기존 데이터베이스 개체를 수정
>     - DROP : 테이블, 뷰 또는 인덱스와 같은 데이터베이스 개체 삭제
>     - TRUNCATE : 테이블의 모든 행을 삭제(DROP과 달리 테이블의 구조와 인덱스는 그대로 유지)
>     - RENAME : 기존 데이터베이스 개체의 이름을 변경
> - **DML (Data Manipulation Language)**
>   - 데이터베이스 내의 데이터를 조작하는 데 사용하는 언어이다.
>   - 종류
>     - SELECT : 데이터를 조회하는 명령어
>     - INSERT : 데이터를 생성하는 명령어
>     - UPDATE : 데이터를 수정하는 명령어
>     - DELETE : 데이터를 삭제하는 명령어
> - **DCL (Data Control Language)**
>   - 데이터베이스에 접근하고 객체들을 사용하도록 권한을 주고 회수하는 데 사용되는 언어이다.
>   - 종류
>     - GRANT : 권한 부여
>     - REVOKE : 권한을 제한하거나 회수
> - **TCL (Transaction Control Language)**
>   - 데이터베이스의 구조를 정의할 때 사용하는 언어이다.
>   - DDL은 명령어를 입력하는 순간 작업이 즉시 반영(Auto Commit)되기 때문에 사용할 때 주의해야 한다.
>   - 종류
>     - COMMIT : 논리적인 작업의 단위를 묶어서 DML에 의해 조작된 결과를 영구적으로 반영
>     - ROLLBACK : 논리적인 작업의 단위를 묶어서 DML에 의해 조작된 결과를 작업 이전의 상태로 복구
>     - SAVEPOINT : 저장점을 정의하면 롤백할 때 트랜잭션에 포함된 전체 작업을 롤백하는 것이 아니라 현시점에서 SAVEPOINT까지 트랜잭션의 일부만 롤백

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/121)
</details>



<details>
<summary><h4>Key의 종류와 특징</h4></summary>

> - **Key란?**
>   - 데이터베이스에서 조건에 만족하는 튜플을 찾거나 순서대로 정렬할 때 다른 튜플들과 구별할 수 있는 유일한 기준이 되는 Attribute(속성)이다.
> - **Key의 종류**
>   - Candidate Key (후보키)
>     - 튜플을 유일하게 식별할 수 있는 속성들의 부분 집합
>     - 모든 릴레이션은 반드시 하나 이상의 후보키를 가져야 한다.
>     - 유일성과 최소성을 만족해야 한다.
>   - Primary Key (기본키)
>     - 후보키 중에서 선택한 메인이 되는 키
>     - Null 값을 가질 수 없다.
>     - 동일한 값이 중복될 수 없다.
>   - Alternate Key (대체키)
>     - 후보키 중 기본키를 제외한 나머지 키
>   - Super Key (슈퍼키)
>     - 유일성은 만족하지만, 최소성은 만족하지 못하는 키
>     - 릴레이션을 구성하는 모든 튜플에 대해 유일성은 만족하지만, 최소성은 만족시키지 못한다.
>   - Foreign Key (외래키)
>     - 다른 릴레이션의 기본키를 그대로 참조하는 속성의 집합
>     - 외래키는 참조되는 릴레이션의 기본키와 대응되어 릴레이션 간에 참조 관계를 표현하는데 중요한 도구로 사용된다.
>     - 외래키로 지정되면 참조 테이블의 기본키에 없는 값은 입력할 수 없다. (참조 무결성 조건)

Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/122)
</details>



<details>
<summary><h4>이상(Anomaly)</h4></summary>
 
> - **이상(Anomaly)이란?**
>   - 릴레이션에서 일부 속성들의 종속이나 데이터의 중복으로 인해 데이터 조작시 불일치가 발생하는 것을 의미한다.
>   - 이상 현상은 정규화(Normalization)을 통해 방지할 수 있다.
> - **이상의 종류**
>   - 삽입 이상(Insertion Anomaly)
>     - 불필요한 정보를 함께 저장하지 않고서는 어떤 정보를 저장하는 것이 불가능한 현상.
>   - 갱신 이상(Update Anomaly)
>     - 데이터 일부만 변경되어, 데이터가 불일치하는 현상.
>   - 삭제 이상(Deletion Anomaly)
>     - 튜플 삭제로 인하여 꼭 필요한 데이터까지 함께 삭제되는 현상.

Ref.
</details>



<details>
<summary><h4>정규화</h4></summary>

> - **정규화란?**
>   - 관계형 데이터베이스의 설계에서 중복을 최소화하기 위하여 데이터를 구조화하는 프로세스를 뜻한다.
>   - 삽입, 삭제, 갱신 이상이 있는 관계를 재구성함으로써 바람직한 스키마를 만들수 있다.
> - **정규화의 종류**
>   - 1NF
>     - 모든 도메인이 원자값으로만 구성된다.
>   - 2NF
>     - 모든 속성의 부분적 종속이 없이 완전 함수 종속을 만족한다.
>   - 3NF
>     - 기본키를 제외한 속성들 간에 이행 종속성이 없다.
>   - BCNF
>     - 모든 결정자가 후보키일 때, 결정자이면서 후보키가 아닌 것을 제거한다.
>   - 4NF
>     - 다치 종속을 제거한다.
>   - 5NF
>     - 모든 조인 종속이 후보키를 통해서만 성립한다. 

Ref.
[star가 되고나서](https://star7sss.tistory.com/822)
</details>



<details>
<summary><h4>JOIN</h4></summary>
 
> - **JOIN이란?**
>   - 두 개 이상의 테이블이나 데이터베이스를 연결하여 데이터를 검색하는 행위를 뜻한다.
>   - 일반적으로 Primary key 혹은 Foreign key로 두 테이블을 연결한다.
>   - 연결하려면 적어도 하나의 칼럼은 서로 공유되고 있어야 한다.
> - **JOIN의 종류**
>   - INNER JOIN
>     - 기존테이블과 조인한 테이블의 중복값을 보여주는데 결과값은 교집합만 검색
>   - LEFT / RIGHT OUTER JOIN
>     - 기존 테이블 값 + 교집합
>   - FULL OUTER JOIN
>     - 합집합
>   - CROSS JOIN
>     - 모든 경우의 수 (N * M)
>   - SELF JOIN
>     - 하나의 테이블을 여러번 복사해서 조인

Ref.
</details>



<details>
<summary><h4>Transaction</h4></summary>
 
> - **트랜잭션이란?**
>   - 데이터베이스의 상태를 변화시키기 해서 수행하는 작업의 단위를 뜻한다.
> - **트랜잭션 특징**
>   - 원자성(Atomicity)
>     - 트랜잭션이 데이터베이스에 모두 반영되던가, 아니면 전혀 반영되지 않아야 한다.
>   - 일관성(Consistency)
>     - 트랜잭션의 작업 처리 결과가 항상 일관성이 있어야 한다.
>   - 독립성(Isolation)
>     - 각각의 트랜잭션은 서로 간섭없이 독립적으로 수행되어야 한다.
>   - 지속성(Durability)
>     - 트랜잭션이 성공적으로 완료됬었을 경우, 결과는 영구적으로 반영되어야 한다.

Ref.
</details>



<details>
<summary><h4>Index</h4></summary>

> - **Index란?**
>   - 테이블에 대한 동작의 속도를 높여주는 자료 구조를 일컫는다.
>   - 테이블 내의 1개의 컬럼 혹은 여러 개의 컬럼을 이용하여 생성될 수 있다.

Ref.
</details>



<details>
<summary><h4>SQL vs NoSQL</h4></summary>

> - **SQL**
>   - 관계형 데이터베이스.
>   - 데이터는 정해진 스키마에 따라 테이블에 저장된다.
> - **NoSQL**
>   - 비관계형 데이터베이스.
>   - 반정형화, 비정형화된 데이터에 적합하다.
>   - 대용량의 데이터 저장에 유리하다.

Ref.
</details>



<details>
<summary><h4>Sharding</h4></summary>
 
> - 같은 테이블 스키마를 가진 데이터를 다수의 데이터베이스에 분산하여 저장하는 방법

Ref.
</details>



<details>
<summary><h4>SID vs Service Name</h4></summary>

> - **SID**
>   - 인스턴스의 유니크한 이름으로 단 하나의 인스턴스를 지칭한다.
> - **Service Name**
>   - 여러 개의 인스턴스를 모아 하나의 시스템을 구성할 때 사용되는 TNS alias이다.

Ref.
</details>





<br><br><br>
- - -
<br><br><br>





# CS
<details>
<summary><h4>OSI 7계층과 TCP/IP 4계층</h4></summary>

> - **OSI 7계층과 TCP/IP 4계층**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/8f74cf13-703e-43a9-89d2-bd9543525acd)
> - **OSI 7계층이란?**
>   - 네트워크 통신이 일어나는 과정을 7단계로 나눈 국제 표준화 기구(ISO)에서 정의한 네트워크 표준 모델이다.
>   - 이 모델은 프로토콜을 기능별로 나눈 것이다.
> - **OSI 7계층 - 계층별 특징**
>   - 물리 계층(Physical)
>     - 전기적, 기계적, 기능적인 특성을 이용하여 통신 케이블로 데이터를 전송한다.
>     - 사용되는 통신 단위는 비트(bit)이며, 0또는 1만 나타낼 수 있다.
>     - 단지 데이터를 전달만 할 뿐 전송하려는, 또는 받으려는 데이터가 무엇인지는 전혀 신경쓰지 않는다.
>     - 대표적인 장치로 통신 케이블, 리피터, 허브 등이 있다.
>   - 데이터 링크 계층(Data Link)
>     - 물리 계층을 통해 송수신되는 정보의 오류와 흐름을 관리하여 안전한 정보의 수행을 도와주는 역할을 한다.
>     - 맥 주소(MAC Address)를 가지고 통신한다.
>     - 전송되는 단위를 프레임(frame)이라고 하며, 대표적인 장비로는 브리지, 스위치 등이 있다.
>   - 네트워크 계층(Network)
>     - 경로를 선택하고 주소를 정하고 경로에 따라 패킷을 전달해주는 역할을 한다.
>     - 데이터를 목적지까지 가장 안전하고 빠르게 전달하는 기능(라우팅)을 한다.
>     - 대표적인 장비로 라우터, (라우팅 기능이 포함된)스위치가 있으며, IP 주소를 사용한다.
>     - 데이터를 연결하는 다른 네트워크를 통해 전달함으로써 인터넷이 가능하게 만드는 계층이다.
>   - 전송 계층(Transport)
>     - 통신을 활성화하기 위한 계층이다. 보통 TCP 프로토콜을 사용하며, 포트를 열어서 응용 프로그램을 전송한다.
>     - 양 끝단의 사용자들이 신뢰성 있는 데이터를 주고 받을 수 있게 해 주어, 상위 계층들이 데이터 전달의 유효성이나 효율성을 생각하지 않도록 한다.
>   - 세션 계층(Session)
>     - 데이터가 통신하기 위한 논리적인 연결을 한다.
>     - 세션 설정, 유지, 종료, 전송 중단시 복구 등의 기능이 있다.
>     - 양 끝단의 응용 프로세스가 통신을 관리하기 위한 방법을 제공한다.
>     - TCP/IP 세션을 만들고 없애는 책임을 진다.
>   - 표현 계층(Presentation)
>     - 데이터 표현이 상이한 응용 프로세스의 독립성을 제공하고, 암호화한다.
>     - 코드 간의 번역을 담당하여 사용자 시스템에서 데이터의 형식상 차이를 다루는 부담을 응용 계층으로 덜어준다.
>     - 해당 데이터가 텍스트인지, 그림인지, GIF인지, JPG인지의 구분 등의 역할을 한다.
>   - 응용 계층(Application)
>     - 최종 목적지로서 HTTP, FTP, SMTP, Telnet 등과 같은 프로토콜이 있다.
>     - 응용 프로세스와 직접 관계하여 일반적인 응용 서비스를 수행한다.
> - **TCP/IP 4계층이란?**
>   - 네트워크 전송 시 데이터 표준을 정리한 것이 OSI 7계층이었다면, 이 이론을 실제로 사용하는 인터넷 표준이 TCP/IP 4계층이다.
> - **TCP/IP 4계층 - 계층별 특징**
>   - 네트워크 인터페이스 계층(Network Access/Network Interface)
>     - OSI 계층의 1,2 계층에 해당된다.
>     - TCP/IP 패킷을 네트워크 매체로 전달하는 것과 네트워크 매체에서 TCP/IP 패킷을 받아들이는 과정을 담당한다.
>     - 에러 검출 기능과 패킷의 프레임화 기능을 수행한다.
>     - 흐름 제어(Flow Control)는 Header(MAC)에서, 에러 제어(Error Control)는 Tailer(CRC)에서 수행한다.
>   - 인터넷 계층(Internet)
>     - OSI 계층에서 3계층에 해당된다.
>     - 어드레싱(addressing), 패키징(packaging), 라우팅(routing) 기능을 제공한다.
>     - 논리적 주소인 IP를 이용한 노드간 전송과 라우팅 기능을 처리하게 된다.
>     - 네트워크상 최종 목적지까지 정확하게 연결되도록 연결성을 제공한다.
>     - 핵심 프로토콜은 IP, ARP, ICMP, IGMP 등이 있다.
>   - 전송 계층(Transport)
>     - OSI 계층에서 3,4 계층에 해당된다.
>     - 자료의 송수신을 담당한다.
>     - 어플리케이션 계층의 세션과 데이터그램 통신서비스를 제공한다.
>     - TCP/UDP가 핵심 프로토콜이다. TCP/UDP에 대한 구분을 하고 데이터에 대한 제어 정보가 여기에 포함된다.
>   - 응용 계층(Application)
>     - 다른 계층의 서비스에 접근할 수 있게 하는 어플리케이션을 제공한다.
>     - 어플리케이션들이 데이터를 교환하기 위해 사용하는 프로토콜을 정의한다.
>     - TCP/IP 네트워크를 사용하거나 관리하는 것을 도와주는 프로토콜이다.

[DevOwen](https://devowen.com/344)
</details>



<details>
<summary><h4>TCP vs UDP</h4></summary>

> - **TCP(Transmission Control Protocol)**
>   - TCP는 신뢰성 있는 데이터 전송을 지원하는 연결 지향형 프로토콜이다.
>   - 일반적으로 TCP와 IP가 함께 사용되는데, IP가 데이터의 전송을 처리한다면 TCP는 패킷을 추적하고 관리하는 역할을 한다.
>   - 연결 지향형인 TCP는 3-way handshaking이라는 과정을 통해 연결 후 통신을 시작하는데, 흐름 제어와 혼잡 제어를 지원하며 데이터의 순서를 보장한다.
>   - UDP에 비하여 전송속도가 느리다.
>   - 신뢰성이 높다.
> - **UDP(User Datagram Protocol)**
>   - UDP는 비연결형 프로토콜이다.
>   - 인터넷상에서 서로 정보를 주고받을 때, 신호 절차를 거치지 않고 보내는 쪽에서 일방적으로 데이터를 전달하는 통신 프로토콜이다.
>   - TCP와는 다르게 연결 설정이 없으며, 혼잡 제어를 하지 않기 때문에 TCP보다 전송 속도가 빠르다.
>   - 데이터 전송에 대한 보장을 하지 않기 때문에 패킷 손실이 발생할 수 있다.
>   - 패킷 오버헤드가 적어 네트워크 부하가 감소한다.
>   - 신뢰성이 낮다.

Ref.
[코딩 공부 일지](https://cocoon1787.tistory.com/757)
</details>



<details>
<summary><h4>3-Way handshake & 4-Way hadnshake</h4></summary>

> - **3-Way Handshake란?**
>   - TCP/IP 프로토콜을 이용해서 통신을 하는 응용프로그램이 데이터를 전송하기 전에 먼저 정확한 전송을 보장하기 위해 상대방 컴퓨터와 사전에 세션을 수립하는 과정을 뜻한다.
> - **3-Way Handshake의 동작 순서**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/205cb3fd-340a-43d3-be51-5acaacb663d6)
>   - Step1. SYN
>     - Client가 Server에게 접속을 요청하는 SYN플래그를 보낸다.
>   - Step2. SYN + ACK
>     - Server는 Listen상태에서 SYN이 들어온 것을 확인하고 SYN_RECV상태로 바뀌어 SYN + ACK플래그를 Client에게 전송한다.
>     - 그 후 Server는 다시 ACK 플래그를 받기 위해 대기상태로 변경된다.
>   - Step3. ACKSYN + ACK
>     - SYN + ACK 상태를 확인한 Client는 서버에게 ACK를 보내고 연결 성립(Established)이 된다.
> - **4-Way Handshake란?**
>   - 3-Way handshake가 연결확립을 위해 진행했다면 4way handshake는 세션을 종료하기 위해 수행되는 절차를 뜻한다.
> - **4-Way Handshake의 동작 순서**
>   - ![image](https://github.com/Young-Geun/TIL/assets/27760576/41c81252-70d4-4856-a598-bb5ce59aa11d)
>   - Step1. FIN
>     - Client가 연결을 종료하겠다는 FIN플래그를 전송한다.
>     - 보낸 후에 FIN-WAIT-1 상태로 변한다.
>   - Step2. ACK
>     - FIN 플래그를 받은 Server는 확인메세지인 ACK를 Client에게 보내준다.
>     - 그 후 CLOSE-WAIT상태로 변한다.
>     - Client도 마찬가지로 Server에서 종료될 준비가 됐다는 FIN을 받기위해  FIN-WAIT-2 상태가 된다.
>   - Step3. FIN
>     - Close준비가 다 된 후 Server는 Client에게 FIN 플래그를 전송한다.
>   - Step4. ACK
>     - Client는 해지 준비가 되었다는 정상응답인 ACK를 Server에게 보내준다. 이 때, Client는 TIME-WAIT 상태로 변경된다.
>     - 여기서 TIME-WAIT 상태는 의도치않은 에러로 인해 연결이 데드락으로 빠지는 것을 방지하기 위해 변경 되는 것인데, 만약 에러로 인해 종료가 지연되다가 타임이 초과되면 CLOSED 상태로 변경된다.

Ref.
[나의 과거일지](https://jeongkyun-it.tistory.com/180)
</details>



<details>
<summary><h4>교착상태</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>뮤텍스와 세마포어</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>CPU 스케줄링 알고리즘</h4></summary>

> - Title
>   - Content

Ref.
</details>



<details>
<summary><h4>프로세스와 스레드의 차이</h4></summary>

> - Title
>   - Content

Ref.
</details>





<br><br><br>
- - -
