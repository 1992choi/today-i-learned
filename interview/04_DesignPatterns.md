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
- [샘플코드](https://github.com/1992choi/design-patterns)
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