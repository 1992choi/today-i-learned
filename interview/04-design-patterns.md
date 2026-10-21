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
        - 컴포지트 (Composite)
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
  - 인스턴스를 매번 생성하는 것이 아니므로 속도 측면에서 이점이 있다. (단, DB 커넥션 풀, 스레드 풀처럼 생성 비용이 큰 객체에 해당되며, 생성 비용이 작은 객체는 체감 효과가 미미하다.)
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
                단, 아래 코드는 동기화 처리가 없어 스레드 세이프(thread-safe)하지 않다.
            */
            if (instance == null) {
                instance = new Singleton();
            }
    
            return instance;
        }
        
    }
    ```
  - 위 기본 구현은 스레드 세이프하지 않다. 여러 스레드가 동시에 `instance == null` 조건을 통과하면 인스턴스가 여러 개 생성될 수 있다.
  - 스레드 세이프한 구현 방법
    - `synchronized` 키워드로 `getInstance()`에 동기화를 거는 방법 (구현이 간단하지만 호출마다 락 경합 비용이 발생한다)
    - ``` java
      public class Singleton {
      
          private static Singleton instance;
      
          private Singleton() {}
      
          public static synchronized Singleton getInstance() {
              if (instance == null) {
                  instance = new Singleton();
              }
      
              return instance;
          }
      
      }
      ```
    - static inner class(Holder)를 이용하는 방법 (클래스 로딩 시점의 초기화 보장을 활용하여 동기화 비용 없이 스레드 세이프하면서도 지연 초기화가 가능하다)
    - ``` java
      public class Singleton {
      
          private Singleton() {}
      
          private static class SingletonHolder {
              private static final Singleton INSTANCE = new Singleton();
          }
      
          public static Singleton getInstance() {
              return SingletonHolder.INSTANCE;
          }
      
      }
      ```
- Ref.
[Caffeine Overflow](https://caffeineoverflow.tistory.com/50)
<br><br><br>



## [GoF] 팩토리 메서드 패턴
- 팩토리 메서드 패턴이란?
  - 팩토리 메서드 패턴은 객체의 생성 과정을 서브 클래스에 위임하는 디자인 패턴이다.
  - 이를 통해 클라이언트 코드는 구체적인 클래스의 인스턴스화 과정을 알 필요 없이 객체를 생성할 수 있다.
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



## [GoF] 추상 팩토리 패턴
- 추상 팩토리 패턴이란?
  - 서로 관련이 있거나 의존적인 객체들의 집합(제품군, Product Family)을 구체적인 클래스를 지정하지 않고 생성할 수 있도록 인터페이스를 제공하는 생성 패턴이다.
  - 팩토리 메서드 패턴이 하나의 제품을 생성하는 데 초점을 둔다면, 추상 팩토리 패턴은 서로 연관된 여러 제품을 하나의 팩토리에서 일관되게 생성하는 데 초점을 둔다.
- 추상 팩토리 패턴의 구조
  - AbstractFactory
    - 관련된 제품들을 생성하는 메서드들을 선언하는 인터페이스.
  - ConcreteFactory
    - AbstractFactory를 구현하여 특정 제품군에 속하는 구체적인 제품들을 생성하는 클래스.
  - AbstractProduct
    - 제품군에 속하는 각 제품이 구현해야 하는 인터페이스.
  - ConcreteProduct
    - 특정 ConcreteFactory에서 생성되는 실제 제품 클래스.
- 추상 팩토리 패턴의 장점
  - 제품군 단위로 객체를 생성하므로, 서로 다른 제품군의 객체들이 섞여서 사용되는(호환되지 않는 조합) 것을 방지할 수 있다.
  - 구체적인 클래스를 클라이언트 코드에서 분리할 수 있어 결합도가 낮아진다.
  - 새로운 제품군을 추가할 때, 기존 코드를 수정하지 않고 새로운 ConcreteFactory와 ConcreteProduct들을 추가하기만 하면 되므로 개방 폐쇄 원칙(OCP)을 지킬 수 있다.
- 추상 팩토리 패턴의 단점
  - 새로운 종류의 제품(기존 제품군에 속하지 않는)을 추가하려면 AbstractFactory 인터페이스 자체를 변경해야 하고, 이는 모든 ConcreteFactory 구현체를 함께 수정해야 하는 부담으로 이어진다.
  - 제품군이 늘어날수록 팩토리와 제품 클래스의 수가 함께 늘어나 코드 복잡도가 증가한다.
- 팩토리 메서드 패턴과의 차이
  - 팩토리 메서드 패턴은 메서드 오버라이딩을 통해 하나의 제품을 생성하는 방법을 서브클래스에 위임하는 반면, 추상 팩토리 패턴은 객체 합성을 통해 여러 제품(제품군 전체)을 생성하는 책임을 팩토리 객체에 위임한다.
  - 팩토리 메서드 패턴에 여러 개의 팩토리 메서드가 모이면 자연스럽게 추상 팩토리 패턴의 형태가 되기도 하여, 두 패턴은 종종 함께 사용된다.
- 구현 예시
  ``` java
  // AbstractProduct
  public interface Button {
      void render();
  }
  public interface Checkbox {
      void render();
  }

  // ConcreteProduct (Windows 제품군)
  public class WindowsButton implements Button {
      @Override
      public void render() {
          System.out.println("Windows 스타일 버튼");
      }
  }
  public class WindowsCheckbox implements Checkbox {
      @Override
      public void render() {
          System.out.println("Windows 스타일 체크박스");
      }
  }

  // ConcreteProduct (Mac 제품군)
  public class MacButton implements Button {
      @Override
      public void render() {
          System.out.println("Mac 스타일 버튼");
      }
  }
  public class MacCheckbox implements Checkbox {
      @Override
      public void render() {
          System.out.println("Mac 스타일 체크박스");
      }
  }

  // AbstractFactory
  public interface GUIFactory {
      Button createButton();
      Checkbox createCheckbox();
  }

  // ConcreteFactory
  public class WindowsFactory implements GUIFactory {
      @Override
      public Button createButton() {
          return new WindowsButton();
      }
      @Override
      public Checkbox createCheckbox() {
          return new WindowsCheckbox();
      }
  }
  public class MacFactory implements GUIFactory {
      @Override
      public Button createButton() {
          return new MacButton();
      }
      @Override
      public Checkbox createCheckbox() {
          return new MacCheckbox();
      }
  }

  // 사용
  GUIFactory factory = new MacFactory(); // OS에 따라 팩토리만 교체하면 제품군 전체가 일관되게 바뀐다.
  Button button = factory.createButton();
  Checkbox checkbox = factory.createCheckbox();
  ```
- Ref.
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
    - 생성 비용이 큰 무거운 객체를 지연 초기화하는 경우, 객체가 필요한 순간에만 초기화하여 사용하므로 불필요한 객체 생성을 줄일 수 있다.
- 프록시 패턴의 단점
  - 복잡성 증가
    - 객체 간의 중간 계층이 추가되어 코드의 복잡성이 증가한다.
  - 성능 저하
    - 생성 비용이 크지 않은 가벼운 객체에 프록시를 남용하면, 중간 계층 호출 오버헤드로 인해 오히려 성능이 저하될 수 있다.
- 프록시 패턴과 데코레이터 패턴
  - 둘 다 원본 객체와 동일한 인터페이스를 구현하는 래퍼(Wrapper) 객체가 원본을 감싸는 구조적으로 유사한 패턴이지만, 의도에 따라 구분된다.
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
  - 중복된 코드를 없애고 SubClass 에서는 비즈니스 로직에만 집중할 수 있다. (DRY)
  - 나중에 새로운 비즈니스 로직이 추가되어도 기존 코드를 수정하지 않아도 된다. (OCP)
- 템플릿 메서드 패턴의 단점
  - 상위 클래스 변화가 생길 경우, 모든 하위 클래스를 수정해야 할 수도 있다.
  - 부모 클래스의 기능을 사용하지 않더라도 상속관계가 되기 때문에 부모 클래스와 강한 의존관계가 형성된다.
- 템플릿 메서드 패턴과 전략 패턴
  - 전략 패턴은 합성(composition)을 통해 해결책을 강구하며, 템플릿 메서드 패턴은 상속(inheritance)을 통해 해결책을 제시한다.
  - 전략 패턴은 클라이언트와 객체 간의 결합이 느슨한 반면, 템플릿 메서드 패턴에서는 두 모듈이 더 밀접하게 결합된다.
  - 전략 패턴에서는 대부분 인터페이스를 사용하지만, 템플릿 메서드 패턴에서는 주로 추상 클래스나 구체적인 클래스를 사용한다.
  - 단일 상속만이 가능한 자바에서 상속 제한이 있는 템플릿 메서드 패턴보다는, 다양하게 많은 전략을 implements 할 수 있는 전략 패턴이 협업에서 많이 사용되는 편이다.
- Ref.
[Hudi](https://hudi.blog/template-method-pattern/),
[뱀귤 블로그](https://bcp0109.tistory.com/369),
[밝은별 개발자](https://brightstarit.tistory.com/38)
<br><br><br>



## [GoF] 전략 패턴
- 전략 패턴이란?
  - 알고리즘군을 캡슐화하여 상호 교환 가능하게 만들고, 클라이언트와 독립적으로 알고리즘을 변경할 수 있게 하는 디자인 패턴이다.
  - 실행(런타임) 중에 알고리즘 전략을 선택하여 객체 동작을 실시간으로 변경할 수 있다.
  - 전략 패턴을 활용하면 OCP를 위반하지 않고 새로운 전략을 추가하여 코드 수정 없이 기능을 추가할 수 있다는 장점이 있다.
- 전략 패턴의 구조
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/d1570ebd-04da-43da-a399-b184ba9dffe1)
  - Context
    - 전략 패턴을 이용하는 역할을 수행한다.
    - 필요에 따라 동적으로 구체적인 전략을 바꿀 수 있도록 setter() 메서드를 제공한다.
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



## [GoF] 빌더 패턴
- 빌더 패턴이란?
  - 복잡한 객체를 생성하는 과정을 단계별로 분리하여, 동일한 생성 절차에서도 다양한 표현(구성)의 객체를 만들 수 있도록 하는 생성 패턴이다.
  - 생성자에 전달해야 하는 필드가 많아질수록 생성자 오버로딩이 늘어나는 이른바 '텔레스코핑 생성자(Telescoping Constructor)' 문제를 해결하기 위해 고안되었다.
- 빌더 패턴이 필요한 이유
  - 생성자의 파라미터가 많아지면 순서를 착각하기 쉽고, 어떤 값이 어떤 필드에 매핑되는지 호출부만 보고 파악하기 어렵다.
  - 선택적(optional)인 필드가 많은 객체를 생성자만으로 표현하려면 다양한 조합의 생성자를 오버로딩해야 하는 문제가 있다.
- 빌더 패턴의 장점
  - 필드에 이름을 붙여 값을 설정하므로 가독성이 높아지고, 필드 순서를 신경 쓰지 않아도 된다.
  - 필요한 필드만 선택적으로 설정할 수 있다.
  - 객체 생성이 완료되는 시점(build() 호출 시점)까지 필드값을 조합할 수 있어, 생성 이후에는 불변(Immutable) 객체로 만들기 용이하다.
- 빌더 패턴의 단점
  - 객체 하나를 만들기 위해 빌더 클래스를 별도로 만들어야 하므로 코드량이 늘어난다.
  - 필드가 적은 단순한 객체에 적용하면 오히려 코드가 장황해질 수 있다.
- 구현 예시
  ``` java
  public class Pizza {

      private final String size;    // 필수
      private final boolean cheese; // 선택
      private final boolean bacon;  // 선택

      private Pizza(Builder builder) {
          this.size = builder.size;
          this.cheese = builder.cheese;
          this.bacon = builder.bacon;
      }

      public static class Builder {
          private final String size; // 필수 값은 생성자에서 받는다.
          private boolean cheese = false;
          private boolean bacon = false;

          public Builder(String size) {
              this.size = size;
          }

          public Builder cheese(boolean value) {
              this.cheese = value;
              return this;
          }

          public Builder bacon(boolean value) {
              this.bacon = value;
              return this;
          }

          public Pizza build() {
              return new Pizza(this);
          }
      }
  }

  // 사용
  Pizza pizza = new Pizza.Builder("L")
          .cheese(true)
          .bacon(true)
          .build();
  ```
  - Lombok의 `@Builder` 어노테이션을 사용하면 위와 같은 빌더 클래스를 직접 작성하지 않고도 컴파일 시점에 자동으로 생성할 수 있다.
- Ref.
<br><br><br>



## [GoF] 어댑터 패턴
- 어댑터 패턴이란?
  - 서로 호환되지 않는 인터페이스를 가진 클래스들을 함께 동작할 수 있도록, 그 사이에서 인터페이스를 변환해주는 구조 패턴이다.
  - 클라이언트가 사용하고자 하는 인터페이스(Target)와 실제로 필요한 기능을 제공하는 기존 클래스(Adaptee)가 다를 때, 그 차이를 흡수하는 중간 변환기 역할을 한다.
- 어댑터 패턴의 구조
  - Target
    - 클라이언트가 사용하는 인터페이스.
  - Adaptee
    - 이미 존재하지만 Target 인터페이스와 호환되지 않는 기존 클래스.
  - Adapter
    - Target 인터페이스를 구현하면서, 내부적으로 Adaptee의 메서드를 호출하여 변환을 수행하는 클래스.
- 어댑터 패턴의 장점
  - 기존 코드(Adaptee)를 변경하지 않고도 클라이언트가 원하는 인터페이스로 재사용할 수 있다.
  - 클라이언트 코드와 기존 클래스 간의 결합도를 낮출 수 있다.
- 어댑터 패턴의 단점
  - 어댑터 클래스가 추가되어 전체적인 코드 복잡도가 증가한다.
  - 기존 인터페이스를 그대로 사용하는 것보다 우회하는 계층이 하나 더 생기므로 약간의 오버헤드가 발생할 수 있다.
- 구현 예시
  ``` java
  // Target: 클라이언트가 사용하는 인터페이스
  public interface ElectronicDevice {
      void powerOn();
  }

  // Adaptee: 기존에 존재하던, Target과 호환되지 않는 클래스
  public class Generator220V {
      public void supply220V() {
          System.out.println("220V 전력을 공급합니다.");
      }
  }

  // Adapter: Target 인터페이스를 구현하면서 Adaptee를 감싼다.
  public class VoltageAdapter implements ElectronicDevice {
      private final Generator220V generator;

      public VoltageAdapter(Generator220V generator) {
          this.generator = generator;
      }

      @Override
      public void powerOn() {
          generator.supply220V(); // 내부적으로 Adaptee의 메서드를 호출
      }
  }
  ```
  - 자바 표준 라이브러리의 `InputStreamReader`가 대표적인 예시로, 바이트(byte) 기반의 `InputStream`을 문자(char) 기반의 `Reader`로 변환해준다.
- Ref.
<br><br><br>



## [GoF] 데코레이터 패턴
- 데코레이터 패턴이란?
  - 객체에 새로운 책임(기능)을 동적으로 추가할 수 있게 해주는 구조 패턴이다.
  - 상속 대신 위임(합성)을 이용해 기능을 확장하기 때문에, 기존 코드를 변경하지 않고도 다양한 기능 조합을 런타임에 구성할 수 있다.
- 데코레이터 패턴의 구조
  - Component
    - 원본 객체와 장식된 객체가 공통으로 구현하는 인터페이스.
  - ConcreteComponent
    - 실제 기능을 수행하는 원본 객체.
  - Decorator
    - Component를 구현하면서 내부에 또 다른 Component를 참조(위임)하는 추상 클래스.
  - ConcreteDecorator
    - Decorator를 상속하여 원본 객체 호출 전/후에 부가 기능을 추가하는 클래스.
- 데코레이터 패턴의 장점
  - 상속보다 유연하게 기능을 추가할 수 있으며, 여러 데코레이터를 조합해서 다양한 기능 조합을 만들 수 있다.
  - 각 데코레이터가 하나의 책임만 가지도록 분리할 수 있어 단일 책임 원칙(SRP)을 지킬 수 있다.
  - 기존 클래스(ConcreteComponent)를 수정하지 않아도 되므로 개방 폐쇄 원칙(OCP)을 지킬 수 있다.
- 데코레이터 패턴의 단점
  - 장식이 많아질수록 유사한 소규모 클래스들이 많아져 코드 파악이 어려워질 수 있다.
  - 여러 데코레이터가 중첩되면 어떤 순서로 어떤 기능이 적용되는지 추적하기 어려워질 수 있다.
- 구현 예시
  ``` java
  // Component
  public interface Coffee {
      int cost();
  }

  // ConcreteComponent
  public class Americano implements Coffee {
      @Override
      public int cost() {
          return 3000;
      }
  }

  // Decorator
  public abstract class CoffeeDecorator implements Coffee {
      protected final Coffee coffee;

      protected CoffeeDecorator(Coffee coffee) {
          this.coffee = coffee;
      }
  }

  // ConcreteDecorator
  public class MilkDecorator extends CoffeeDecorator {
      public MilkDecorator(Coffee coffee) {
          super(coffee);
      }

      @Override
      public int cost() {
          return coffee.cost() + 500; // 원본 기능에 부가 기능(가격)을 추가
      }
  }

  // 사용
  Coffee coffee = new MilkDecorator(new Americano());
  System.out.println(coffee.cost()); // 3500
  ```
  - 자바 표준 라이브러리의 `BufferedReader(new InputStreamReader(...))`처럼 스트림을 겹겹이 감싸는 방식이 대표적인 예시이다.
- 프록시 패턴과의 차이
  - 위 프록시 패턴 항목에서 설명한 것처럼 구조는 유사하지만, 프록시는 접근 제어가 목적이고 데코레이터는 새로운 기능 추가가 목적이라는 점에서 의도가 다르다.
- Ref.
<br><br><br>



## [GoF] 옵저버 패턴
- 옵저버 패턴이란?
  - 한 객체(Subject)의 상태가 변경되었을 때, 이를 구독하고 있는 다른 객체들(Observer)에게 자동으로 알림이 전달되도록 하는 행동 패턴이다.
  - Subject와 Observer는 1:N의 의존 관계를 가지며, 발행-구독(Publish-Subscribe) 모델의 기반이 되는 패턴이다.
- 옵저버 패턴의 구조
  - Subject
    - Observer 목록을 관리하며, 상태 변화가 생기면 등록된 Observer들에게 알림(notify)을 보내는 주체.
  - Observer
    - Subject를 구독하는 인터페이스로, 알림을 받았을 때 수행할 동작(update)을 정의한다.
  - ConcreteSubject / ConcreteObserver
    - 각각 Subject와 Observer 인터페이스를 구현한 실제 클래스.
- 옵저버 패턴의 장점
  - Subject와 Observer 간의 결합도가 낮아, 서로의 구체적인 구현에 영향을 주지 않고 독립적으로 확장할 수 있다.
  - 새로운 Observer를 추가하더라도 Subject의 코드를 수정할 필요가 없어 개방 폐쇄 원칙(OCP)을 지킬 수 있다.
- 옵저버 패턴의 단점
  - Observer가 많아지면 알림이 전파되는 순서를 제어하기 어렵고, 알림 처리 과정에서 성능 저하가 발생할 수 있다.
  - Subject와 Observer 간 알림 흐름이 여러 단계로 이어지면 전체 흐름을 추적하고 디버깅하기 어려워질 수 있다.
  - Observer 해제를 누락하면 Subject가 불필요한 Observer 참조를 계속 들고 있어 메모리 누수로 이어질 수 있다.
- 구현 예시
  ``` java
  public interface Observer {
      void update(String message);
  }

  public class Subject {
      private final List<Observer> observers = new ArrayList<>();

      public void subscribe(Observer observer) {
          observers.add(observer);
      }

      public void unsubscribe(Observer observer) {
          observers.remove(observer);
      }

      public void notifyObservers(String message) {
          for (Observer observer : observers) {
              observer.update(message);
          }
      }
  }

  public class EmailObserver implements Observer {
      @Override
      public void update(String message) {
          System.out.println("이메일 발송: " + message);
      }
  }
  ```
  - 스프링의 이벤트 처리 방식인 `ApplicationEventPublisher`와 `@EventListener`도 옵저버 패턴을 기반으로 동작한다. 특정 이벤트가 발행(publish)되면, 이를 구독(@EventListener)하고 있는 리스너들이 자동으로 호출되는 구조이다.
- Ref.
<br><br><br>



## [GoF] 파사드 패턴
- 파사드 패턴이란?
  - 여러 클래스(서브시스템)로 이루어진 복잡한 내부 구조를, 클라이언트가 사용하기 쉬운 단순한 하나의 인터페이스(파사드)로 감싸서 제공하는 구조 패턴이다.
  - '파사드(Facade)'는 건물의 정면이라는 뜻으로, 클라이언트는 파사드 뒤에 숨겨진 복잡한 서브시스템들의 구현 세부사항을 몰라도 파사드가 제공하는 단순한 메서드만 호출하면 된다.
- 파사드 패턴의 구조
  - Facade
    - 서브시스템의 여러 클래스를 내부에서 조합하여, 클라이언트가 사용할 단순화된 메서드를 제공하는 클래스.
  - Subsystem Classes
    - 실제 기능을 수행하는 기존의 여러 클래스들. 파사드의 존재와 무관하게 독립적으로도 사용될 수 있다.
- 파사드 패턴의 장점
  - 클라이언트는 복잡한 서브시스템의 세부 구현을 몰라도 되므로, 클라이언트 코드와 서브시스템 간의 결합도가 낮아진다.
  - 서브시스템 내부 구현이 변경되어도, 파사드가 제공하는 인터페이스만 유지된다면 클라이언트 코드는 영향을 받지 않는다.
  - 복잡한 로직을 한 곳에 모아두므로 코드 가독성과 사용 편의성이 높아진다.
- 파사드 패턴의 단점
  - 파사드 클래스가 여러 서브시스템에 대한 의존성을 모두 가지게 되어, 서브시스템이 많아질수록 파사드 클래스 자체가 비대해질 수 있다(신 클래스, God Class가 될 위험).
  - 서브시스템에 대한 세밀한 제어가 필요한 경우, 파사드가 제공하지 않는 기능은 여전히 서브시스템에 직접 접근해야 한다.
- 실무에서의 예시
  - 스프링에서 개발자가 트랜잭션 관리, 커넥션 획득/반납, 예외 변환 등 JDBC의 복잡한 절차를 직접 다루지 않고 `JdbcTemplate`의 메서드 하나만 호출하면 되는 것도 파사드 패턴이 적용된 예로 볼 수 있다.
  - 여러 개의 Repository/외부 API 호출을 조합해야 하는 로직을 Service 계층 하나로 감싸서, Controller가 Service의 단순한 메서드 하나만 호출하도록 하는 구조도 넓은 의미의 파사드라 할 수 있다.
- 구현 예시
  ``` java
  // Subsystem Classes
  public class CPU {
      public void freeze() { System.out.println("CPU 정지"); }
      public void jump(long position) { System.out.println("CPU 점프: " + position); }
      public void execute() { System.out.println("CPU 실행"); }
  }
  public class Memory {
      public void load(long position, byte[] data) { System.out.println("메모리 적재: " + position); }
  }
  public class HardDrive {
      public byte[] read(long lba, int size) {
          System.out.println("하드디스크 읽기");
          return new byte[size];
      }
  }

  // Facade
  public class ComputerFacade {
      private final CPU cpu = new CPU();
      private final Memory memory = new Memory();
      private final HardDrive hardDrive = new HardDrive();

      public void start() {
          cpu.freeze();
          memory.load(0, hardDrive.read(0, 1024));
          cpu.jump(0);
          cpu.execute();
      }
  }

  // 사용
  ComputerFacade computer = new ComputerFacade();
  computer.start(); // 클라이언트는 CPU, Memory, HardDrive의 존재를 몰라도 된다.
  ```
- 어댑터 패턴과의 차이
  - 어댑터 패턴은 기존 인터페이스를 클라이언트가 원하는 다른 인터페이스로 '변환'하는 것이 목적이지만, 파사드 패턴은 여러 인터페이스(서브시스템)를 하나로 '단순화'하는 것이 목적이라는 점에서 의도가 다르다.
- Ref.
<br><br><br>



## [GoF] 책임 연쇄 패턴(Chain of Responsibility)
- 책임 연쇄 패턴이란?
  - 하나의 요청을 처리할 수 있는 객체(핸들러)들을 사슬(체인)처럼 연결해두고, 요청이 들어오면 체인을 따라 순차적으로 전달하면서 각 핸들러가 스스로 처리할지, 다음 핸들러에게 넘길지를 판단하도록 하는 행동 패턴이다.
  - 요청을 보내는 클라이언트는 어떤 핸들러가 실제로 요청을 처리하는지 알 필요가 없다.
- 책임 연쇄 패턴의 구조
  - Handler
    - 요청을 처리하는 메서드와, 다음 핸들러로 요청을 전달하는 참조(next)를 정의하는 인터페이스(또는 추상 클래스).
  - ConcreteHandler
    - Handler를 구현하며, 자신이 처리할 수 있는 요청인지 판단해서 처리하거나, 처리할 수 없다면 다음 핸들러(next)에게 요청을 위임하는 클래스.
  - Client
    - 체인의 첫 번째 핸들러에게 요청을 전달하는 주체.
- 책임 연쇄 패턴의 장점
  - 요청을 보내는 클라이언트와 요청을 처리하는 핸들러 사이의 결합도를 낮출 수 있다.
  - 체인에 새로운 핸들러를 추가하거나 순서를 변경하기 쉬워, 기존 코드를 수정하지 않고도 처리 로직을 확장할 수 있다(개방 폐쇄 원칙).
  - 하나의 거대한 if-else/switch 문으로 여러 처리 조건을 분기하는 대신, 각 핸들러가 단일 책임만 갖도록 분리할 수 있다.
- 책임 연쇄 패턴의 단점
  - 요청이 체인의 여러 핸들러를 거치면서 처리되기 때문에, 어떤 핸들러가 실제로 요청을 처리했는지 추적하고 디버깅하기 어려워질 수 있다.
  - 체인 어딘가에서 다음 핸들러로 요청을 전달하는 코드를 빠뜨리면, 요청이 끝까지 처리되지 못하고 누락될 수 있다.
  - 체인이 길어지면 매 요청마다 여러 핸들러를 순차적으로 거쳐야 하므로 성능에 영향을 줄 수 있다.
- 구현 예시
  ``` java
  public abstract class Handler {
      protected Handler next;

      public Handler setNext(Handler next) {
          this.next = next;
          return next;
      }

      public abstract void handle(int level, String message);
  }

  public class InfoHandler extends Handler {
      @Override
      public void handle(int level, String message) {
          if (level <= 1) {
              System.out.println("[INFO] " + message);
          } else if (next != null) {
              next.handle(level, message);
          }
      }
  }

  public class ErrorHandler extends Handler {
      @Override
      public void handle(int level, String message) {
          if (level <= 2) {
              System.out.println("[ERROR] " + message);
          } else if (next != null) {
              next.handle(level, message);
          }
      }
  }

  // 사용
  Handler chain = new InfoHandler();
  chain.setNext(new ErrorHandler());
  chain.handle(2, "요청 처리 실패"); // ErrorHandler까지 전달되어 처리됨
  ```
- 실무에서의 예시
  - 서블릿 필터(Filter)와 스프링 인터셉터(Interceptor)가 대표적인 예시로, 하나의 HTTP 요청이 여러 개의 필터/인터셉터를 순차적으로 거치면서 각자의 역할(인증, 로깅, 인코딩 변환 등)을 수행한 뒤 다음 체인으로 요청을 전달하는 구조가 책임 연쇄 패턴을 기반으로 한다.
  - 스프링 시큐리티의 `FilterChain` 역시 여러 보안 필터가 체인 형태로 연결되어 순차적으로 요청을 처리하는 책임 연쇄 패턴의 예시이다.
- Ref.
<br><br><br>



## [GoF] 커맨드 패턴
- 커맨드 패턴이란?
  - 요청(실행할 작업)을 하나의 객체로 캡슐화하여, 요청을 보내는 쪽(Invoker)과 요청을 실제로 처리하는 쪽(Receiver)을 분리하는 행동 패턴이다.
  - 요청 자체가 객체이기 때문에, 요청을 큐에 저장하거나, 로그로 남기거나, 실행 취소(Undo) 기능을 구현하는 것이 가능해진다.
- 커맨드 패턴의 구조
  - Command
    - 실행할 작업을 위한 `execute()` 메서드를 선언하는 인터페이스.
  - ConcreteCommand
    - Command를 구현하며, 실제 작업을 수행할 Receiver를 참조하여 `execute()`에서 Receiver의 메서드를 호출한다.
  - Receiver
    - 실제 비즈니스 로직을 수행하는 객체.
  - Invoker
    - Command 객체를 가지고 있다가, 필요한 시점에 `execute()`를 호출해 요청을 실행시키는 객체. Command의 구체적인 구현은 알지 못한다.
- 예제코드
  ``` java
  public interface Command {
      void execute();
  }

  public class Light { // Receiver
      public void on() { System.out.println("불이 켜졌습니다."); }
  }

  public class LightOnCommand implements Command { // ConcreteCommand
      private final Light light;

      public LightOnCommand(Light light) {
          this.light = light;
      }

      @Override
      public void execute() {
          light.on();
      }
  }

  public class RemoteControl { // Invoker
      private Command command;

      public void setCommand(Command command) {
          this.command = command;
      }

      public void pressButton() {
          command.execute();
      }
  }
  ```
- 커맨드 패턴의 장점
  - 요청을 보내는 객체와 처리하는 객체 사이의 결합도를 낮출 수 있다.
  - 요청(Command) 객체를 큐에 저장하거나 로그로 남길 수 있어, 작업 이력 관리나 실행 취소(Undo)/재실행(Redo) 기능을 구현하기 쉬워진다.
  - 새로운 Command를 추가하더라도 Invoker나 Receiver의 코드를 수정할 필요가 없다(개방 폐쇄 원칙).
- 커맨드 패턴의 단점
  - 각 요청마다 별도의 Command 클래스를 추가해야 하므로, 기능이 많아질수록 클래스 수가 함께 늘어난다.
- Ref.
<br><br><br>



## [GoF] 상태 패턴
- 상태 패턴이란?
  - 객체의 내부 상태에 따라 행동이 달라져야 할 때, 상태를 별도의 클래스로 분리하고 객체는 현재 상태 객체에게 행동을 위임하는 행동 패턴이다.
  - 상태 변화에 따른 로직을 하나의 거대한 if-else/switch 문으로 처리하지 않고, 각 상태를 독립된 클래스로 캡슐화하여 관리할 수 있다.
- 상태 패턴의 구조
  - Context
    - 현재 상태(State) 객체를 참조하며, 클라이언트의 요청을 현재 상태 객체에게 위임한다.
  - State
    - 상태별 행동을 정의하는 인터페이스.
  - ConcreteState
    - State를 구현하며, 특정 상태에서의 구체적인 행동과, 다른 상태로의 전이 로직을 가진다.
- 예제코드
  ``` java
  public interface OrderState {
      void next(OrderContext context);
  }

  public class PaymentWaitingState implements OrderState {
      @Override
      public void next(OrderContext context) {
          System.out.println("결제 완료");
          context.setState(new ShippingState());
      }
  }

  public class ShippingState implements OrderState {
      @Override
      public void next(OrderContext context) {
          System.out.println("배송 완료");
          context.setState(new DeliveredState());
      }
  }

  public class OrderContext {
      private OrderState state = new PaymentWaitingState();

      public void setState(OrderState state) {
          this.state = state;
      }

      public void next() {
          state.next(this);
      }
  }
  ```
- 상태 패턴의 장점
  - 상태별 로직이 각 State 클래스로 분리되어 응집도가 높아지고, 새로운 상태를 추가하기 쉬워진다(개방 폐쇄 원칙).
  - 거대한 조건문을 제거하여 가독성과 유지보수성을 높일 수 있다.
- 상태 패턴의 단점
  - 상태가 많아질수록 그만큼 클래스 수가 늘어난다.
  - 상태 전이 로직이 여러 State 클래스에 분산되어 있어, 전체 상태 흐름을 한눈에 파악하기 어려울 수 있다.
- 전략 패턴과의 차이
  - 구조적으로는 매우 유사하지만, 전략 패턴은 클라이언트가 알고리즘(전략)을 명시적으로 선택/교체하는 데 초점이 있고, 상태 패턴은 상태 객체 스스로가 상황에 따라 다음 상태로 전이하는 흐름 제어에 초점이 있다는 의도의 차이가 있다.
- Ref.
<br><br><br>



## [GoF] 이터레이터 패턴
- 이터레이터 패턴이란?
  - 컬렉션(집합체)의 내부 구조(배열, 리스트, 트리 등)를 외부에 노출하지 않으면서도, 그 안에 담긴 원소들을 순차적으로 접근할 수 있는 방법을 제공하는 행동 패턴이다.
  - 자바의 `Iterator` 인터페이스, 향상된 for문(for-each)이 내부적으로 이 패턴을 기반으로 동작한다.
- 이터레이터 패턴의 구조
  - Iterator
    - 원소를 순회하기 위한 `hasNext()`, `next()` 같은 메서드를 선언하는 인터페이스.
  - ConcreteIterator
    - 특정 컬렉션에 대한 순회 로직을 구현한 클래스.
  - Aggregate
    - 이터레이터를 생성하는 `createIterator()` 메서드를 선언하는 인터페이스.
  - ConcreteAggregate
    - 실제로 원소들을 보관하고 있는 컬렉션 클래스.
- 예제코드
  ``` java
  public class NameRepository implements Iterable<String> {
      private final List<String> names = new ArrayList<>();

      public void addName(String name) {
          names.add(name);
      }

      @Override
      public Iterator<String> iterator() {
          return names.iterator(); // 내부 구조(List)를 노출하지 않고 순회 방법만 제공
      }
  }

  NameRepository repository = new NameRepository();
  repository.addName("Alice");

  for (String name : repository) { // 향상된 for문이 내부적으로 Iterator를 사용
      System.out.println(name);
  }
  ```
- 이터레이터 패턴의 장점
  - 컬렉션의 내부 구현(배열인지, 연결 리스트인지 등)을 몰라도 동일한 방식으로 순회할 수 있어, 클라이언트 코드와 컬렉션 구현을 분리할 수 있다.
  - 하나의 컬렉션에 대해 여러 종류의 순회 방식(정방향, 역방향 등)을 별도의 Iterator로 구현해 제공할 수 있다.
  - 여러 개의 이터레이터를 동시에 사용해, 하나의 컬렉션을 동시에 여러 지점에서 순회하는 것도 가능하다.
- 이터레이터 패턴의 단점
  - 단순한 컬렉션 순회를 위해 별도의 Iterator 클래스를 만들어야 하므로, 간단한 경우에는 오히려 불필요한 복잡도를 추가할 수 있다.
- Ref.
<br><br><br>



## [GoF] 컴포지트 패턴
- 컴포지트 패턴이란?
  - 객체들을 트리 구조로 구성하여, 개별 객체(Leaf)와 여러 객체를 묶은 복합 객체(Composite)를 클라이언트가 동일한 방식으로 다룰 수 있게 하는 구조 패턴이다.
  - 파일 시스템의 파일/디렉터리처럼, "부분-전체" 계층 구조를 표현할 때 유용하다.
- 컴포지트 패턴의 구조
  - Component
    - Leaf와 Composite이 공통으로 구현할 인터페이스로, 공통 동작(예: `getSize()`)을 정의한다.
  - Leaf
    - 자식을 가지지 않는 개별 객체로, Component의 동작을 직접 구현한다.
  - Composite
    - 여러 Component(Leaf 또는 다른 Composite)를 자식으로 가지며, 자신에게 호출된 동작을 자식들에게 위임하고 결과를 합산/취합한다.
- 예제코드
  ``` java
  public interface FileComponent {
      int getSize();
  }

  public class File implements FileComponent { // Leaf
      private final int size;

      public File(int size) { this.size = size; }

      @Override
      public int getSize() { return size; }
  }

  public class Directory implements FileComponent { // Composite
      private final List<FileComponent> children = new ArrayList<>();

      public void add(FileComponent component) {
          children.add(component);
      }

      @Override
      public int getSize() {
          return children.stream().mapToInt(FileComponent::getSize).sum(); // 자식에게 위임 후 합산
      }
  }
  ```
- 컴포지트 패턴의 장점
  - 클라이언트는 개별 객체인지 복합 객체인지 구분하지 않고 동일한 인터페이스로 다룰 수 있어 코드가 단순해진다.
  - 트리에 새로운 종류의 Leaf/Composite를 추가하기 쉽다(개방 폐쇄 원칙).
- 컴포지트 패턴의 단점
  - 모든 구성 요소가 공통 인터페이스를 따라야 하므로, Leaf에는 의미가 없는 메서드(자식 추가 등)까지 포함될 수 있어 설계가 다소 억지스러워질 수 있다.
- Ref.
<br><br><br>



## [GoF] 프로토타입 패턴
- 프로토타입 패턴이란?
  - 기존 객체(원형, Prototype)를 복제(Clone)하여 새로운 객체를 생성하는 생성 패턴이다.
  - 객체 생성 비용이 크거나(복잡한 초기화 과정이 필요한 경우), 특정 상태를 가진 객체를 기반으로 유사한 객체를 반복적으로 만들어야 할 때 `new`로 매번 생성하는 대신 기존 객체를 복제해서 재사용할 수 있다.
- 자바에서의 구현
  - `Cloneable` 인터페이스를 구현하고 `Object.clone()`을 재정의(오버라이딩)하여 프로토타입 패턴을 구현할 수 있다.
  - ``` java
    public class Sheep implements Cloneable {
        private String name;

        public Sheep(String name) { this.name = name; }

        @Override
        public Sheep clone() {
            try {
                return (Sheep) super.clone();
            } catch (CloneNotSupportedException e) {
                throw new AssertionError(e);
            }
        }
    }

    Sheep original = new Sheep("Dolly");
    Sheep copy = original.clone(); // 원본을 복제하여 새 객체 생성
    ```
- 얕은 복사(Shallow Copy)와 깊은 복사(Deep Copy) 주의사항
  - `Object.clone()`의 기본 동작은 얕은 복사이기 때문에, 객체가 참조 타입 필드를 가지고 있다면 원본과 복제본이 같은 참조를 공유하게 되어 한쪽을 수정하면 다른 쪽에도 영향을 줄 수 있다.
  - 참조 타입 필드까지 독립적으로 복제해야 한다면, `clone()`을 재정의할 때 내부 필드도 함께 복제(깊은 복사)해주어야 한다.
- 프로토타입 패턴의 장점
  - 복잡한 초기화 과정을 반복하지 않고 기존 객체를 복제해 생성 비용을 절감할 수 있다.
  - 런타임에 결정된 구체적인 객체를 기반으로 새로운 객체를 만들 수 있어, 서브클래스를 몰라도 객체를 생성할 수 있다.
- 프로토타입 패턴의 단점
  - 복잡한 객체 그래프(순환 참조 등)를 가진 객체를 깊은 복사로 복제하는 로직을 올바르게 구현하기가 까다로울 수 있다.
- Ref.
<br><br><br>



## [GoF] 플라이웨이트 패턴
- 플라이웨이트 패턴이란?
  - 동일하거나 유사한 객체를 매번 새로 생성하는 대신, 공유 가능한 객체(Flyweight)를 캐싱해서 재사용함으로써 메모리 사용량을 줄이는 구조 패턴이다.
  - 객체의 상태를 변하지 않는 공유 가능한 부분(Intrinsic State)과, 사용할 때마다 외부에서 전달받아야 하는 부분(Extrinsic State)으로 나누는 것이 핵심이다.
- 플라이웨이트 패턴의 구조
  - Flyweight
    - 공유되는 객체로, 내부적으로 변하지 않는 상태(Intrinsic State)만 가진다.
  - FlyweightFactory
    - Flyweight 객체를 생성하고 캐싱하여, 동일한 요청이 들어오면 새로 생성하지 않고 기존 객체를 반환하는 팩토리.
  - Client
    - Flyweight를 사용할 때마다 외부 상태(Extrinsic State)를 전달한다.
- 예제코드
  ``` java
  public class CharacterStyle { // Flyweight (폰트, 색상처럼 공유 가능한 불변 상태)
      private final String font;
      private final String color;

      public CharacterStyle(String font, String color) {
          this.font = font;
          this.color = color;
      }
  }

  public class CharacterStyleFactory {
      private final Map<String, CharacterStyle> cache = new HashMap<>();

      public CharacterStyle getStyle(String font, String color) {
          String key = font + color;
          return cache.computeIfAbsent(key, k -> new CharacterStyle(font, color)); // 이미 있으면 재사용
      }
  }
  ```
  - 문서 편집기에서 각 글자(Character)마다 폰트/색상 객체를 새로 만드는 대신, 동일한 폰트/색상 조합은 하나의 객체를 공유해서 사용하는 식으로 활용할 수 있다.
- 플라이웨이트 패턴의 장점
  - 동일한 데이터를 가진 객체를 반복 생성하지 않고 공유함으로써 메모리 사용량을 크게 줄일 수 있다.
- 플라이웨이트 패턴의 단점
  - 공유 객체와 외부 상태를 분리하는 과정에서 코드가 복잡해질 수 있고, 공유 객체는 반드시 불변(Immutable)이어야 하므로 설계에 제약이 생긴다.
- 자바에서의 예시
  - 래퍼 클래스의 캐싱(`Integer.valueOf()`의 -128~127 범위 캐싱), 문자열 리터럴을 재사용하는 String Pool이 플라이웨이트 패턴과 유사한 아이디어를 기반으로 한다.
- Ref.
<br><br><br>



## [GoF] 브리지 패턴
- 브리지 패턴이란?
  - 추상화(기능) 계층과 구현 계층을 분리하여, 두 계층이 서로 독립적으로 확장될 수 있도록 하는 구조 패턴이다.
  - 상속만으로 기능과 구현의 조합을 표현하면, 기능의 종류와 구현의 종류가 늘어날수록 하위 클래스의 수가 기하급수적으로 늘어나는 "클래스 폭발" 문제가 발생하는데, 브리지 패턴은 상속 대신 합성(Composition)을 이용해 이 문제를 해결한다.
- 브리지 패턴의 구조
  - Abstraction
    - 기능(추상화)을 정의하며, 내부에 Implementor에 대한 참조를 가진다.
  - RefinedAbstraction
    - Abstraction을 확장한 구체적인 기능.
  - Implementor
    - 구현부의 인터페이스를 정의한다.
  - ConcreteImplementor
    - Implementor를 구현한 구체적인 구현체.
- 예제코드
  ``` java
  public interface Device { // Implementor
      void turnOn();
  }

  public class TV implements Device { // ConcreteImplementor
      @Override
      public void turnOn() { System.out.println("TV를 켭니다."); }
  }

  public abstract class RemoteControl { // Abstraction
      protected Device device; // 구현부를 합성으로 참조 (다리 역할)

      protected RemoteControl(Device device) {
          this.device = device;
      }

      public abstract void powerOn();
  }

  public class BasicRemoteControl extends RemoteControl { // RefinedAbstraction
      public BasicRemoteControl(Device device) { super(device); }

      @Override
      public void powerOn() {
          device.turnOn();
      }
  }
  ```
  - 리모컨(기능)의 종류와 전자기기(구현)의 종류가 각각 독립적으로 늘어나도, `RemoteControl`이 `Device`를 합성으로 참조하고 있기 때문에 서로 영향을 주지 않고 자유롭게 조합할 수 있다.
- 브리지 패턴의 장점
  - 추상화와 구현을 독립적으로 확장할 수 있어, 상속으로 인한 클래스 폭발 문제를 방지할 수 있다.
  - 런타임에 구현체를 교체하는 것도 가능하다.
- 브리지 패턴의 단점
  - 추상화와 구현을 분리하는 과정에서 설계가 복잡해질 수 있고, 처음 구조를 파악하기 어려울 수 있다.
- 어댑터 패턴과의 차이
  - 어댑터 패턴은 이미 존재하는 서로 호환되지 않는 인터페이스를 사후적으로 맞춰주는 것이 목적인 반면, 브리지 패턴은 설계 단계에서부터 추상화와 구현이 독립적으로 확장될 수 있도록 미리 분리해두는 것이 목적이라는 차이가 있다.
- Ref.
<br><br><br>



## MVC, MVP, MVVM 패턴
- 공통 목적
  - 세 패턴 모두 화면(View)과 데이터/비즈니스 로직(Model)을 분리하여, 유지보수성과 테스트 용이성을 높이기 위한 아키텍처 패턴이라는 공통점이 있다. 다만 View와 Model을 중개하는 방식에 차이가 있다.
- MVC (Model-View-Controller)
  - Model : 데이터와 비즈니스 로직을 담당한다.
  - View : 사용자에게 보여지는 화면을 담당한다.
  - Controller : 사용자의 입력을 받아 Model을 조작하고, 그 결과를 반영할 View를 선택한다.
  - Controller가 View를 직접 선택하고, View가 Model을 직접 참조해서 데이터를 조회하기도 하는 등 View와 Model 사이에 어느 정도 의존 관계가 남아있을 수 있다. (스프링 MVC가 대표적인 예시이다.)
- MVP (Model-View-Presenter)
  - View와 Model이 서로 전혀 알지 못하고, 모든 상호작용이 Presenter를 통해서만 이루어진다는 점이 MVC와의 가장 큰 차이이다.
  - Presenter는 View의 인터페이스만 알고 있어 View를 직접 조작(갱신)하며, View는 사용자의 입력을 Presenter에게 그대로 전달하는 수동적인 역할만 한다.
  - View와 Presenter가 1:1로 강하게 결합되는 경향이 있어, View가 많아지면 Presenter도 함께 늘어나는 경향이 있다.
- MVVM (Model-View-ViewModel)
  - ViewModel이 View의 상태와 로직을 가지고 있으며, View는 ViewModel을 데이터 바인딩(Data Binding)을 통해 관찰하다가 ViewModel의 상태가 변하면 자동으로 갱신된다.
  - MVP와 달리 ViewModel이 View를 직접 참조하지 않고, View가 양방향 데이터 바인딩을 통해 ViewModel의 변화를 구독하는 구조여서 View와 ViewModel 사이의 결합도가 더 낮다.
  - 안드로이드의 Jetpack ViewModel, 프론트엔드의 Vue.js 등이 MVVM 패턴을 기반으로 한다.
- 비교 요약
  - MVC는 Controller가 View를 선택하는 구조, MVP는 Presenter가 View를 직접 조작하는 구조, MVVM은 View가 데이터 바인딩을 통해 ViewModel을 구독하는 구조라는 점에서 Model과 View 사이의 매개체가 점점 더 View로부터 독립적으로 분리되는 방향으로 발전해왔다고 볼 수 있다.
- Ref.
<br><br><br>



## 안티패턴(Anti-Pattern)
- 안티패턴이란?
  - 처음에는 문제를 해결하는 방법처럼 보이지만, 실제로는 비효율적이거나 유지보수를 어렵게 만드는 잘못된 설계/개발 관행을 의미한다. 디자인 패턴이 "검증된 좋은 해결책"이라면, 안티패턴은 "반복적으로 나타나는 나쁜 해결책"이라고 볼 수 있다.
- God Object(God Class)
  - 하나의 클래스가 너무 많은 책임과 로직을 떠안아, 비대하고 다른 모든 클래스와 강하게 결합되어 있는 상태이다.
  - 단일 책임 원칙(SRP)을 위반하는 대표적인 사례로, 작은 수정 하나가 예상치 못한 다른 부분에 영향을 미칠 위험이 커진다.
- Spaghetti Code(스파게티 코드)
  - 코드의 흐름이 명확한 구조 없이 복잡하게 얽혀 있어, 코드를 읽고 이해하기 어려운 상태를 의미한다. 흔히 깊게 중첩된 조건문/반복문, 전역 변수의 남용 등으로 인해 발생한다.
- Copy-Paste Programming(복사-붙여넣기 프로그래밍)
  - 기존 코드를 이해하고 재사용 가능한 형태로 추출하는 대신, 비슷한 코드를 복사해서 여기저기 붙여넣는 방식이다.
  - 동일한 로직이 여러 곳에 중복되어, 버그를 수정하거나 요구사항이 변경될 때 모든 중복 위치를 일일이 찾아 수정해야 하는 부담이 생긴다.
- Golden Hammer(황금 망치)
  - "모든 문제가 못처럼 보인다"는 속담처럼, 특정 기술/패턴/도구에 익숙하다는 이유만으로 적합하지 않은 상황에까지 무분별하게 적용하는 것을 의미한다. (예: 모든 문제를 디자인 패턴으로 해결하려 하거나, 간단한 데이터 처리에도 과도하게 마이크로서비스를 도입하는 경우)
- Premature Optimization(섣부른 최적화)
  - 실제로 성능에 문제가 되는지 측정하지 않은 상태에서, 가독성이나 단순함을 희생하면서까지 미리 최적화를 시도하는 것을 의미한다.
  - "섣부른 최적화는 모든 악의 근원이다(Donald Knuth)"라는 말처럼, 실제 병목 지점을 프로파일링 등으로 먼저 확인한 뒤 최적화하는 것이 권장된다.
- 안티패턴을 피하기 위한 접근
  - 단일 책임 원칙(SRP) 등 SOLID 원칙을 지키려 노력하고, 코드 리뷰를 통해 문제를 조기에 발견하며, 리팩토링을 지속적으로 수행하는 것이 안티패턴을 예방하는 데 도움이 된다.
- Ref.
<br><br><br>
