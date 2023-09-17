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
> 1. 객체 지향 언어로써 캡슐화, 상속, 다형성 기능을 완벽하게 지원한다.   
> 2. 운영체제에 상관없이 독립적으로 작동(JVM에서 동작하기 때문)하여 이식성이 높다.   
> 3. Garbage Collector에 의해 메모리가 관리된다.   
> 4. 스레드 생성 및 제어와 관련된 라이브러리를 제공하기 때문에 운영체제에 상관없이 멀티 스레드를 쉽게 구현할 수 있다.   
> 5. 애플리케이션이 실행될 때 모든 객체가 생성되지 않고, 각 객체가 필요한 시점에 클래스를 동적 로딩해서 생성한다. 또한 유지보수 시 해당 클래스만 수정하면 되기 때문에 전체 애플리케이션을 다시 컴파일 할 필요가 없기 때문에 유지보수가 쉽고 빠르다.   


</details>



<details>
<summary><h4>객체지향의 4대 특징</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/38)
> - **캡슐화**   
>   \- 객체의 필드와 메서드를 하나로 묶는 것이며, 이를 통해 정보은닉 효과를 얻을 수 있다.      
> - **추상화**   
>   \- 사물들의 공통적인 특징을 파악해서 하나의 개념으로 다루는 것을 뜻한다.      
>   \- 가령 클래스들의 공통적인 요소를 뽑아내서 상위 클래스로 만들어낼 수 있다.   
> - **다형성**   
>   \- 하나의 객체나 메소드가 여러가지 다른 형태를 가질 수 있는 것을 뜻한다.    
>   \- 오버라이딩과 오버로딩 그리고 상속받은 객체의 참조변수 형변환 등이 있다.   
> - **상속성**   
>   \- 상위 객체의 필드와 메서드를 하위 객체에게 물려주어 하위 객체에서 사용할 수 있도록 해준다.  

</details>



<details>
<summary><h4>객체지향의 5대 원칙(SOLID)</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/39)  
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
> - **의존 역전 원칙(Dependency Inversion Principle)**   
>   \- 상위 모듈은 하위 모듈에 종속되어서는 안된다.   
>   \- 의존 관계를 맺을 때, 구체적인 클래스보다는 인터페이스나 추상 클래스와 관계를 맺어야 한다.
>   
> ```
> 결합도란?
>   - 모듈(클래스) 간의 상호 의존 정도로써, 결합도가 낮으면 상호 의존성이 줄어들어 객체의 재사용이나 수정, 유지보수가 용이해진다.
>
> 응집도란?
>   - 하나의 모듈 내부에 존재하는 구성 요소들의 기능적 관련성으로, 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져 재사용이나 기능의 수정, 유지보수가 용이해진다.
> ```

</details>



<details>
<summary><h4>클래스, 객체, 인스턴스 비교</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/40)  
> - **클래스**   
>   \- 객체를 만들어 내기 위한 설계도로써 객체의 상태를 나타내는 필드(field)와 객체의 행동을 나타내는 메서드(method)로 구성된다.   
> - **객체**   
>   \- 클래스로 구현할 모든 대상을 뜻한다.     
> - **인스턴스**   
>   \- 객체가 메모리에 할당되어 실제 사용될 때를 지칭한다.      
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
>   \- 불변(immutable)의 속성을 갖는다.   
>   \- 변경 연산을 자주 사용할 경우, 힙 메모리에 많은 가비지(Garbage)가 생성되어 힙 메모리 부족으로 이어질 수 있다.   
>   \- 불변성을 가지기 때문에 멀티스레드 환경에서의 thread-safe 하다.      
> - **StringBuffer**   
>   \- String 클래스와 다르게 가변성을 갖는다.   
>   \- 동기화를 지원하여 멀티 스레드 환경에서도 안전하게 동작할 수 있다.   
> - **StringBuilder**   
>   \- String 클래스와 다르게 가변성을 갖는다.   
>   \- 동기화를 지원하지 않는다.

</details>



<details>
<summary><h4>접근 제어자</h4></summary>

[[More+]](https://caffeineoverflow.tistory.com/46)
> - **public**   
>   \- 적용대상 : 필드, 생성자, 메서드, 클래스   
>   \- 모든 접근을 허용한다.   
> - **protected**   
>   \- 적용대상 : 필드, 생성자, 메서드   
>   \- 같은 패키지 또는 다른 패키지이지만 해당 클래스를 상속받은 자식 클래스에서의 접근을 허용한다.   
> - **default**   
>   \- 적용대상 : 필드, 생성자, 메서드, 클래스   
>   \- 같은 패키지 내에서의 접근을 허용한다.   
> - **private**   
>   \- 적용대상 : 필드, 생성자, 메서드   
>   \- 같은 클래스 내에서의 접근만 허용한다.   

</details>



<details>
<summary><h4>final 제어자</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>래퍼클래스(Wrapper Class)와 박싱(Boxing), 언박싱(Unboxing)</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>추상클래스와 인터페이스의 차이</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>Overloading vs Overriding</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>제네릭(Generic)</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>컬렉션 프레임워크(Collection Framework)</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>람다식(Lambda Expression)</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>스트림 API(Stream API)</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>Checked Exception과 Unchecked Exception</h4></summary>

[[More+]]()  
> ...

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
<summary><h4>스프링 개요</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>스프링 MVC</h4></summary>

[[More+]]()  
> ...

</details>





<br><br><br>
- - -
<br><br><br>





# Database
<details>
<summary><h4>DDL, DML, DCL, TCL</h4></summary>

[[More+]]()  
> ...

</details>



<details>
<summary><h4>Key의 종류와 특징</h4></summary>

[[More+]]()  
> ...

</details>
