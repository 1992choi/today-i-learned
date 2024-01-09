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
<details>
<summary><h4>Java의 특징</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/37)
> - 객체 지향 언어로써 캡슐화, 상속, 다형성 기능을 완벽하게 지원한다.
> - 운영체제에 상관없이 독립적으로 작동(JVM에서 동작하기 때문)하여 이식성이 높다.
> - Garbage Collector에 의해 메모리가 관리된다.
> - 스레드 생성 및 제어와 관련된 라이브러리를 제공하기 때문에 운영체제에 상관없이 멀티 스레드를 쉽게 구현할 수 있다.
> - 애플리케이션이 실행될 때 모든 객체가 생성되지 않고, 각 객체가 필요한 시점에 클래스를 동적 로딩해서 생성한다. 또한 유지보수 시 해당 클래스만 수정하면 되기 때문에 전체 애플리케이션을 다시 컴파일 할 필요가 없기 때문에 유지보수가 쉽고 빠르다.

</details>



<details>
<summary><h4>객체지향의 4대 특징</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/38)
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

</details>



<details>
<summary><h4>객체지향의 5대 원칙(SOLID)</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/39)  
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

</details>



<details>
<summary><h4>클래스, 객체, 인스턴스 비교</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/40)  
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

</details>



<details>
<summary><h4>String, StringBuffer, StringBuilder 비교</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/42)  
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

</details>



<details>
<summary><h4>접근 제어자</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/46)
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

</details>



<details>
<summary><h4>final 제어자</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/44)
> - **final 이란?**
>   - Java에서는 불변성을 확보하거나 동작을 제한할 수 있는 final 키워드를 제공한다.
>   - final 키워드는 변수(variable), 메서드(method), 클래스(class)에 사용할 수 있다.
> - **final 변수**
>   - 변수에 final 키워드를 사용할 경우, 더 이상 값을 변경하지 못하도록 제한을 할 수 있다.
> - **final 메서드**
>   - 메서드에 final 키워드를 사용할 경우, 재정의를 제한할 수 있다.
> - **final 클래스**
>   - 클래스에 final 키워드를 사용할 경우, 상속을 제한할 수 있다.

</details>



<details>
<summary><h4>래퍼클래스(Wrapper Class)와 박싱(Boxing), 언박싱(Unboxing)</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/123) 
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

</details>



<details>
<summary><h4>추상클래스</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/124)  
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

</details>



<details>
<summary><h4>인터페이스</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/125)  
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

</details>



<details>
<summary><h4>추상클래스와 인터페이스의 차이</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/126)  
> - **추상클래스와 인터페이스의 차이점**
>   - 추상클래스 : 자식클래스 is kind of 부모클래스
>   - 인터페이스 : 자식클래스 is able to 부모인터페이스
>   - 추상클래스는 계층 구조에서 공통된 속성들을 뽑아서 하나의 클래스로 만들고 자신의 기능들을 하위로 확장시키는 것으로 볼 수 있으며, 인터페이스는 계층 구조는 아니지만 같은 기능이 필요한 경우 사용하는 것으로 볼 수 있다.
>   ![image](https://github.com/Young-Geun/TIL/assets/27760576/960f18b5-d588-4ddc-ac10-c1998b383bb1)

</details>


<details>
<summary><h4>Overloading vs Overriding</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/127)  
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

</details>



<details>
<summary><h4>제네릭(Generic)</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/128)  
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
</details>



<details>
<summary><h4>컬렉션 프레임워크(Collection Framework)</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/129)  
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

</details>



<details>
<summary><h4>람다식(Lambda Expression)</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/130)  
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

</details>



<details>
<summary><h4>스트림 API(Stream API)</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/135)  
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

</details>



<details>
<summary><h4>Checked Exception과 Unchecked Exception</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/138)  
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



</details>



<details>
<summary><h4>스레드</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>JVM</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>Annotation</h4></summary>

[[More+]]()  
> ...

</details>





<br><br><br>
- - -
<br><br><br>





# Web
<details>
<summary><h4>JSP vs Servlet</h4></summary>

[[More+]]()  
> - **JSP**
>   - html 내에 자바코드를 블록화하여 삽입한 것.
>   - JAVA in Html.
> - **Servlet**
>   - Container가 이해할 수 있도록 구성된 자바코드로 이루어진 것.
>   - Html in JAVA.

</details>



<details>
<summary><h4>Session과 Cookie</h4></summary>

[[More+]]()  
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

</details>



<details>
<summary><h4>Framework vs Library</h4></summary>

[[More+]]()  
> - **Framework**
>   - 뼈대가 되는 부분을 미리 구현한 클래스, 인터페이스, 메서드 등의 집합체이다.
> - **Library**
>   - 자주 쓰일 만한 기능들을 따로 구현하여 모아 놓은 클래스의 집합체이다.

</details>



<details>
<summary><h4>스프링 개념</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/5)
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



</details>



<details>
<summary><h4>스프링 MVC</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/6)
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


</details>



<details>
<summary><h4>스프링 DI</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/13)
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

</details>



<details>
<summary><h4>스프링 IoC</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/14)
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

</details>



<details>
<summary><h4>스프링 AOP</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/17)
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

</details>



<details>
<summary><h4>스프링 PSA</h4></summary>

[[More+]](https://sabarada.tistory.com/127)  
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


</details>



<details>
<summary><h4>스프링 POJO</h4></summary>

[[More+]](https://onpups.pe.kr/386)  
> - **POJO (Plain Old Java Object)란?**
>   - '오래된 방식의 간단한 자바 객체' = '단순한 자바 오브젝트' 라는 뜻이다.
>   - 객체 지향적인 원리에 충실하면서 환경과 기술에 종속되지 않고 필요에 따라 재활용될 수 있는 방식으로 설계된 객체를 말한다.
> - **POJO의 조건**
>   - 특정 규약에 종속되면 안된다.
>   - 특정 환경에 종속되면 안된다.
>   - 객체 지향적 원리를 지켜야 한다.

</details>



<details>
<summary><h4>빈 스코프(Bean Scope)</h4></summary>

[[More+]](https://code-lab1.tistory.com/186)  
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


</details>



<details>
<summary><h4>@Transactional</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/139)  
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

</details>



<details>
<summary><h4>JDK Dynamic Proxy VS CGLIB Proxy</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>Spring Filter vs Interceptor</h4></summary>

[[More+]](https://mangkyu.tistory.com/173)  
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

</details>



<details>
<summary><h4>ORM, JPA, Hibernate, Spring Data JPA 개념</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/140)  
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

</details>



<details>
<summary><h4>Test</h4></summary>

[[More+]]()  
> ...

</details>





<br><br><br>
- - -
<br><br><br>





# Database
<details>
<summary><h4>DDL, DML, DCL, TCL</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/121) 
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

</details>



<details>
<summary><h4>Key의 종류와 특징</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>이상(Anomaly)</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>정규화</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>JOIN</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>Transaction</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>Index</h4></summary>

[[More+]]()  
> ...

</details>





<br><br><br>
- - -
<br><br><br>





# TODO
- HashMap 충돌
- non-static 멤버와 static 멤버 차이
- 직렬화
- 리플렉션
- 자바에서 멀티스레드 동기화 방법
- equals & hashCode
- Call by value ve Call by Reference
- GC
- String 메모리 관점
- GET, PUT, POST, PATCH 차이
- CORS
- 웹 브라우저에 URL 입력 시 일어나는 일련의 과정
- TCP/IP 5 Layer
- OSI 7 Layer
- 3-Way handshake & 4-Way hadnshake
- 블락킹과 논블락킹, 동기식과 비동기식
- 교착상태
- CPU 스케줄링 알고리즘
- 프로세스와 스레드의 차이
- Thread-safe
- 뮤텍스와 세마포어


