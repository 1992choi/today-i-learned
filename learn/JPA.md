# 개요
- 김영한 JPA 강의
- 코드
  - https://github.com/1992choi/jpa

<br><hr>

# 기본편
### SQL 중심적인 개발의 문제점
- SQL에 의존적인 개발을 피하기 어렵다.
- 단순 쿼리를 반복적으로 짜야한다.
- 객체와 관계형 데이터베이스 간의 패러다임 불일치 발생.

### JPA란?
- Java Persistence API
- 자바 진영의 ORM 기술 표준
  - ORM
    - Object-relational mapping(객체 관계 매핑)
    - 객체는 객체대로 설계
    - 관계형 데이터베이스는 관계형 데이터베이스대로 설계
    - ORM 프레임워크가 중간에서 매핑
    - 대중적인 언어에는 대부분 ORM 기술이 존재
- JPA 표준명세
  - JPA는 인터페이스의 모음
  - JPA 2.1 표준 명세를 구현한 3가지 구현체가 존재한다.
    - 하이버네이트, EclipseLink, DataNucleus
- 왜 사용해야 하는가?
  - SQL 중심적인 개발에서 객체 중심으로 개발
  - 생산성이 높아짐.
    - 매번 쿼리를 작성하지 않아도 된다.
  - 유지보수가 쉬워진다.
    - 필드 변경 시 모든 SQL을 수정할 필요가 없다.
  - 패러다임의 불일치 해결.
  - 성능 향상
    - 1차 캐시와 동일성(identity) 보장
    - 트랜잭션을 지원하는 쓰기 지연(transactional write-behind)
    - 지연 로딩(Lazy Loading)

### 영속성 컨텍스트
- 영속성 컨텍스트란?
  - '엔티티를 영구 저장하는 환경' 이라는 뜻
  - 영속성 컨텍스트는 논리적인 개념
  - 엔티티 매니저를 통해서 영속성 컨텍스트에 접근
- 엔티티의 생명주기
  - 비영속 (new/transient)
    - 영속성 컨텍스트와 전혀 관계가 없는 새로운 상태
  - 영속 (managed)
    - 영속성 컨텍스트에 관리되는 상태
  - 준영속 (detached)
    - 영속성 컨텍스트에 저장되었다가 분리된 상태
  - 삭제 (removed)
    - 삭제된 상태
- 영속성 컨텍스트의 이점
  - 1차 캐시
  - 동일성(identity) 보장
  - 트랜잭션을 지원하는 쓰기 지연(transactional write-behind)
  - 변경 감지(Dirty Checking)
  - 지연 로딩(Lazy Loading)
- 플러시
  - 영속성 컨텍스트의 변경내용을 데이터베이스에 반영
  - 영속성 컨텍스트의 내용을 비운다고 잘못 해석될 수 있으나, 비우는 것이 아닌 데이터베이스에 반영하는 것.

### 객체와 테이블 매핑
- @Entity
  - @Entity가 붙은 클래스는 JPA가 관리, 엔티티라 한다.
  - JPA를 사용해서 테이블과 매핑할 클래스는 @Entity 필수
  - 기본 생성자 필수(파라미터가 없는 public 또는 protected 생성자)
  - 속성
    - name
      - JPA에서 사용할 엔티티 이름을 지정한다.
      - 기본값: 클래스 이름을 그대로 사용(예: Member)
- @Table
  - 엔티티와 매핑할 테이블 지정
  - 속성
    - name
      - 매핑할 테이블 이름 엔티티 이름을 사용
    - catalog
      - 데이터베이스 catalog 매핑
    - schema
      - 데이터베이스 schema 매핑
    - uniqueConstraints [DDL]
      - DDL 생성 시에 유니크 제약 조건 생성
- @Column
  - 컬럼 매핑
  - 속성
    - name
      - 필드와 매핑할 테이블의 컬럼 이름 객체의 필드 이름
    - insertable, updatable
      - 등록, 변경 가능 여부 TRUE
    - nullable
      - null 값의 허용 여부를 설정한다. false로 설정하면 DDL 생성 시에 not null 제약조건이 붙는다.
    - unique
      - @Table의 uniqueConstraints와 같지만 한 컬럼에 간단히 유니크 제약조건을 걸 때 사용한다.
    - columnDefinition
      - 데이터베이스 컬럼 정보를 직접 줄 수 있다.
      - ex) varchar(100) default ‘EMPTY'
    - length
      - 문자 길이 제약조건
      - String 타입에만 사용한다.
- @Enumerated
  - 자바 enum 타입을 매핑할 때 사용
  - 속성
    - value
      - EnumType.ORDINAL
        - enum 순서를 데이터베이스에 저장
        - 주의
          - 순서로 저장되기 때문에 1,2,3과 같은 값을 갖는다.
          - 만약 신규로 생성되는 ENUM이 2번째로 끼어들게 되서 순서가 변경되면, 이미 데이터베이스에 2로 저장된 데이터와 신규 2번이 혼용되어 사용될 수 있다.
          - 따라서 ORDINAL는 사용하지 않는 것을 권장한다.
      - EnumType.STRING
        - enum 이름을 데이터베이스에 저장
- @Temporal
  - 날짜 타입(java.util.Date, java.util.Calendar)을 매핑할 때 사용
  - LocalDate, LocalDateTime을 사용할 때는 생략 가능(최신 하이버네이트 지원)
- @Lob
  - 데이터베이스 BLOB, CLOB 타입과 매핑
  - 매핑하는 필드 타입이 문자면 CLOB 매핑, 나머지는 BLOB 매핑
  - CLOB
    - String, char[], java.sql.CLOB
  - BLOB
    - byte[], java.sql. BLOB
- @Transient
  - 필드를 매핑하지 않을 때 사용.
    - 스키마에 없는 필드를 추가하여 사용하고 싶을 때, DB의 컬럼과 매핑되는 변수가 아님을 나타낼 때 사용된다.
  - 데이터베이스에 저장X, 조회X
  - 주로 메모리상에서만 임시로 어떤 값을 보관하고 싶을 때 사용

### 기본키 매핑
- 직접 할당
  - @Id만 사용
- 자동 생성
  - @Id와 함께 @GeneratedValue 사용
    - ```
      Ex) 
      @Id
      @GeneratedValue(strategy = GenerationType.IDENTITY)
      ```
  - 옵션
    - IDENTITY
      - 데이터베이스에 위임, MYSQL
    - SEQUENCE
      - 데이터베이스 시퀀스 오브젝트 사용, ORACLE
      - @SequenceGenerator 필요
    - TABLE
      - 키 생성용 테이블 사용
      - 모든 DB에서 사용 가능하다는 장점이 있다.
      - @TableGenerator 필요
    - AUTO
      - 방언에 따라 자동 지정
      - 기본값

### 양방향 매핑
- 객체와 테이블의 관계 맺음 차이
  - TEAM과 MEMBER가 있다고 가정할 때, 테이블은 외래 키 하나로 연관관계를 맺는다.
  - 반면, 객체는 서로를 알기 위해서는 양방향 매핑이 필요하다.
- 양방향 매핑 규칙
  - 객체의 두 관계중 하나를 연관관계의 주인으로 지정해야한다.
  - 연관관계의 주인만이 외래 키를 관리해야한다.
  - 주인은 mappedBy 속성을 사용하면 안된다.
  - 주인이 아니면 mappedBy 속성으로 주인을 지정해야한다.
  - 그렇다면 누구를 주인으로?
    - 외래 키가 있는 있는 곳을 주인으로 정해라
- 양방향 매핑의 필요성
  - 가장 좋은 것은 복잡도를 낮추기 위하여 단방향 매핑을 가급적 사용하는 것이 좋다.
  - 그러므로 처음 개발 시에는 단방향 매핑으로 진행한 후 필요 시에만 양방향 매핑을 적용한다.
- 예제
  - ```java
    // 외래키를 가지고 있는 Member가 주인. 그러므로 mappedBy 속성을 사용하지 않음.
    @Entity
    public class Member {
      @Id 
      @GeneratedValue
      private Long id;
      
      private String name;
      
      @ManyToOne
      @JoinColumn(name = "TEAM_ID")
      private Team team;
    }
    
    // 주인이 아니므로 mappedBy 속성을 사용.
    @Entity
    public class Team {
      @Id
      @GeneratedValue
      private Long id;
      
      private String name;
      
      @OneToMany(mappedBy = "team") // 주인(=Member)의 team 변수와 매핑
      List<Member> members = new ArrayList<Member>(); // Team 엔티티의 members 필드는 읽기 전용 (변경 불가. 변경해도 쿼리가 실행되지 않음)
    }
    ```
    
### 다양한 양방향 매핑
- 방향에 따른 분류
  - 분류
    - 단방향
    - 양방향
  - 개념
    - 테이블에는 사실 방향의 개념이 없다. 외래 키 하나로 양쪽 조인이 가능하므로.
    - 객체는 참조용 필드가 있는 쪽으로만 참조가 가능한데, 아래와 같이 분류 지을 수 있다.
      - 한쪽만 참조하면 단방향
      - 양쪽이 서로 참조하면 양방향
- 다중성에 따른 분류
  - 다대일
    - @ManyToOne
    - 가장 많이 사용되는 연관관계
    - 다대일이며 양방향이면, 바로 위에서 정리한 개념이 된다.
  - 일대다
    - @OneToMany
    - 일대다 단방향
      - 엔티티가 관리하는 외래키가 다른 테이블에 있는 특이한 구조가 됨. (지양해야할 설계 방식)
      - 위와 같은 이유 때문에 연관관계 관리를 위해 추가로 UPDATE 쿼리가 실행된다. (비효율적)
      - 일대다 단방향 매핑보다는 다대일 단방향 매핑을 사용하는 것이 올바른 방식으로 볼 수 있다.
    - 일대다 양방향
      - 공식적으로 존재하지 않지만, 아래와 같은 옵션을 통해 구현은 할 수 있다.
        - @JoinColumn(insertable=false, updatable=false)
      - 마찬가지로 일대다 양방향보다는 다대일 양방향 매핑을 사용하는 것이 좋다.
  - 일대일
    - @OneToOne
    - 주 테이블이나 대상 테이블 중에 외래키 선택 가능.
      - 주 테이블에 외래 키 (추천 방식)
        - 주 객체가 대상 객체의 참조를 가지는 것 처럼 주 테이블에 외래 키를 두고 대상 테이블을 찾음
        - 객체지향 개발자 선호
        - JPA 매핑 편리
        - 장점: 주 테이블만 조회해도 대상 테이블에 데이터가 있는지 확인 가능
        - 단점: 값이 없으면 외래 키에 null 허용
      - 대상 테이블에 외래 키
        - 대상 테이블에 외래 키가 존재
        - 전통적인 데이터베이스 개발자 선호
        - 장점: 주 테이블과 대상 테이블을 일대일에서 일대다 관계로 변경할 때 테이블 구조 유지
        - 단점: 프록시 기능의 한계로 지연 로딩으로 설정해도 항상 즉시 로딩됨
  - 다대다
    - @ManyToMany
    - 관계형 데이터베이스는 정규화된 테이블 2개로 다대다 관계를 표현할 수 없음
    - 연결 테이블을 추가해서 일대다, 다대일 관계로 풀어내야함
      - @ManyToMany -> @OneToMany, @ManyToOne
    - 한계
      - 편리해 보이지만 실무에서 사용 지양
      - 연결 테이블이 단순히 연결만 하고 끝나지 않음
        - 비즈니스 도메인을 가질 수도 있기 때문에 각종 필드가 추가될 가능성이 높음.
        - 이렇게 되면 복잡도가 높아지게 됨.
        - 따라서 연결 테이블을 추가하여 관계를 풀어줘야함

### 상속관계 매핑
- 관계형 데이터베이스는 상속 관계라는 개념이 없다.
- 슈퍼타입 서브타입 논리 모델을 실제 물리 모델로 구현하는 방법
  - 조인 전략
    - @Inheritance(strategy=InheritanceType.JOINED)
    - <img width="667" alt="image" src="https://github.com/user-attachments/assets/3b065d04-808f-466e-94ab-776902cabe83" />
    - 장점
      - 테이블 정규화
      - 외래 키 참조 무결성 제약조건 활용가능
      - 저장공간 효율화
    - 단점
      - 조회시 조인을 많이 사용, 성능 저하
      - 조회 쿼리가 복잡함
      - 데이터 저장시 INSERT SQL 2번 호출
  - 단일 테이블 전략
    - @Inheritance(strategy=InheritanceType.SINGLE_TABLE)
    - <img width="294" alt="image" src="https://github.com/user-attachments/assets/3111b6e3-007c-4434-80b2-d5fb3e8d6b0f" />
    - 장점
      - 조인이 필요 없으므로 일반적으로 조회 성능이 빠름
      - 조회 쿼리가 단순함
    - 단점
      - 자식 엔티티가 매핑한 컬럼은 모두 null 허용
      - 단일 테이블에 모든 것을 저장하므로 테이블이 커질 수 있다. 상황에 따라서 조회 성능이 오히려 느려질 수 있다.
  - 구현 클래스마다 테이블 전략
    - @Inheritance(strategy=InheritanceType.TABLE_PER_CLASS)
    - <img width="661" alt="image" src="https://github.com/user-attachments/assets/efce7b2f-de7a-4244-9cbb-6c0046c797b7" />
    - 장점
      - 서브 타입을 명확하게 구분해서 처리할 때 효과적
      - not null 제약조건 사용 가능
    - 단점
      - 여러 자식 테이블을 함께 조회할 때 성능이 느림(UNION SQL 필요)
      - 자식 테이블을 통합해서 쿼리하기 어려움

### @MappedSuperclass
- 공통 매핑 정보가 필요할 때 사용
  - 주로 등록일, 수정일, 등록자, 수정자 같은 전체 엔티티에서 공통으로 적용하는 정보를 모을 때 사용
- 상속관계 매핑 방식이 아니다.
- 엔티티로 관리되지 않고, 테이블과 매핑되지도 않는다.
- 부모 클래스를 상속 받는 자식 클래스에 매핑 정보만 제공
- 직접 생성해서 사용할 일이 없으므로 추상 클래스 권장

### 프록시
- Member를 조회할 때 Team도 함께 조회해야 할까?
  - 만약 member.getTeam()이 자주 호출되지 않는다면, 굳이 Team까지 조회를 해야하나?
  - 프록시 엔티티를 조회하는 방식으로 해결할 수 있다.
    - member만 조회할 때는 team을 join해서 조회하지 않고, team을 실제 사용할 때 조회함.
- 프록시 특징
  - 실제 클래스를 상속 받아서 만들어짐.
  - 프록시 객체를 호출하면 프록시 객체는 실제 객체의 메소드 호출.
  - 프록시 객체는 처음 사용할 때 한 번만 초기화.
  - 프록시 객체를 초기화 할 때, 프록시 객체가 실제 엔티티로 바뀌는 것은 아니다.
    - 초기화되면 프록시 객체를 통해서 실제 엔티티에 접근하는 형태
- 프록시가 중요한 이유
  - 이후 지연로딩의 기본 개념이 되기 때문.

### 지연 로딩
- Member를 조회할 때 Team도 함께 조회해야 할까?
  - 만약 member.getTeam()이 자주 호출되지 않는다면, 굳이 Team까지 조회를 해야하나?
    - Ex) member.getUserName();
    - 지연 로딩 LAZY을 사용해서 프록시로 조회
      - ```
        @ManyToOne(fetch = FetchType.LAZY)
        @JoinColumn(name = "TEAM_ID")
        private Team team;
        ```
- 프록시와 즉시로딩(지연로딩의 반대되는 개념) 사용시 주의사항
  - 가급적 지연 로딩만 사용
  - 즉시 로딩을 적용하면 예상하지 못한 SQL이 발생
  - 즉시 로딩은 JPQL에서 N+1 문제를 일으킨다.
  - @ManyToOne, @OneToOne은 기본이 즉시 로딩
    - 때문에 LAZY로 설정 권장
  - @OneToMany, @ManyToMany는 기본이 지연 로딩

### 영속성 전이 (CASCADE)
- 특정 엔티티를 영속 상태로 만들 때 연관된 엔티티도 함께 영속상태로 만들도 싶을 때 사용
  - Ex) 부모 엔티티를 저장할 때 자식 엔티티도 함께 저장.
- 저장
  - @OneToMany(mappedBy="parent", cascade=CascadeType.PERSIST)
  - 예시
    - ```
      @Entity
      public class Parent {
        @OneToMany(mappedBy = "parent", cascade = CascadeType.ALL, orphanRemoval = true)
        private List<Child> childList = new ArrayList<>();
      }
      
      @Entity
      public class Child {
        @ManyToOne
        @JoinColumn(name = "parent_id")
        private Parent parent;
      }
      
      // em.persist(parent); 만 있어도 Child까지 저장 가능.
      ```
- CASCADE의 종류
  - ALL: 모두 적용
  - PERSIST: 영속
  - REMOVE: 삭제
  - MERGE: 병합
  - REFRESH: REFRESH
  - DETACH: DETACH

### 고아 객체
- 부모와 관계가 끊어진 객체를 의미한다.
- 옵션
  - orphanRemoval = true
  - ```
    Parent parent1 = em.find(Parent.class, id);
    parent1.getChildren().remove(0); // orphanRemoval 옵션에 의해 끊어진 객체는 자동 DELETE
    ```
- 주의사항
  - 참조하는 곳이 하나일 때 사용해야한다.
    - 그렇지 않다면 의도지않은 동작을 할 가능성이 높다.
  - @OneToOne, @OneToMany만 가능

### `영속성 전이 + 고아 객체`의 생명주기
- CascadeType.ALL + orphanRemoval=true
- 두 옵션을 모두 활성화 하면 부모 엔티티를 통해서 자식의 생명주기를 관리할 수 있음
- 도메인 주도 설계(DDD)의 Aggregate Root개념을 구현할 때 유용

### 값 타입
- JPA의 데이터 타입 분류
  - 엔티티 타입
    - @Entity로 정의하는 객체
    - 데이터가 변해도 식별자로 지속해서 추적 가능
      - Ex) 회원 엔티티의 키나 나이 값을 변경해도 식별자로 인식 가능
  - 값 타입
    - int, Integer, String처럼 단순히 값으로 사용하는 자바 기본 타입이나 객체
    - 식별자가 없고 값만 있으므로 변경시 추적 불가
      - Ex) 숫자 100을 200으로 변경하면 완전히 다른 값으로 대체
- 값 타입 분류
  - 기본값 타입
    - 자바 기본 타입(int, double ...)
    - 래퍼 클래스(Integer, Long ...)
    - String
  - 임베디드 타입
  - 컬렉션 값 타입
- 값 타입의 특징
  - 기본값 타입
    - 생명주기를 엔티티의 의존
      - Ex) 회원을 삭제하면 이름, 나이 필드도 함께 삭제
    - 값 타입은 공유하면 안된다.
  - 임베디드 타입
    - 새로운 값 타입을 직접 정의할 수 있음
    - 주로 기본 값 타입을 모아서 만들어서 복합 값 타입이라고도 함
      - Ex) 우편번호, 주소, 상세주소를 별도의 임베디드 타입으로 선언
    - 사용법
      - @Embeddable
        - 값 타입을 정의하는 곳에 표시
      - @Embedded
        - 값 타입을 사용하는 곳에 표시
  - 컬렉션 값 타입
    - 값 타입을 하나 이상 저장할 때 사용
    - @ElementCollection, @CollectionTable 사용
    - 데이터베이스는 컬렉션을 같은 테이블에 저장할 수 없다.
    - 컬렉션을 저장하기 위한 별도의 테이블이 필요함
    - 실무에서는 상황에 따라 값 타입 컬렉션 대신에 일대다 관계를 고려

### JPA의 쿼리 방법
- JPQL
  - 가장 단순한 조회 방법
  - JPA의 한계
    - JPA를 사용하면 엔티티 객체를 중심으로 개발.
    - 검색 역시 테이블이 아닌 엔티티 객체를 대상으로 검색
      - 모든 DB 데이터를 객체로 변환해서 검색하는 것은 불가능
      - 애플리케이션이 필요한 데이터만 DB에서 불러오려면 결국 검색 조건이 포함된 SQL이 필요
  - JPA는 SQL을 추상화한 JPQL이라는 객체 지향 쿼리 언어 제공
  - JPQL은 엔티티 객체를 대상으로 쿼리
- JPA Criteria
  - 문자가 아닌 자바코드로 JPQL을 작성할 수 있음
  - JPQL 빌더 역할
  - JPA 공식 기능이나 복잡하고 실용성이 없다.
- QueryDSL
  - 문자가 아닌 자바코드로 JPQL을 작성할 수 있음
  - JPQL 빌더 역할
  - 동적쿼리 작성 편리함
  - 단순하고 쉬움
  - 실무 사용 권장
- 네이티브 SQL
  - JPA가 제공하는 SQL을 직접 사용하는 기능
- JDBC API 직접 사용, MyBatis, SpringJdbcTemplate 함께 사용
  - JPA를 사용하면서 JDBC 커넥션을 직접 사용하거나, 스프링 JdbcTemplate, 마이바티스등을 함께 사용 가능
  - 단, 영속성 컨텍스트를 적절한 시점에 강제로 플러시 필요

### JPQL 기본 문법과 기능
- JPQL 문법
  - Ex) select m from Member as m where m.age > 18
    - 엔티티와 속성은 대소문자를 구분한다.
    - JPQL 키워드는 대소문자를 구분하지 않는다.
    - 엔티티 이름 사용(테이블 이름이 아니다.)
    - 별칭은 필수
- 결과 조회 API
  - query.getResultList()
    - 결과가 하나 이상일 때, 리스트 반환
    - 결과가 없으면 빈 리스트 반환
  - query.getSingleResult()
    - 결과가 정확히 하나, 단일 객체 반환
    - 결과가 정확히 하나가 아니면 오류 발생
      - 결과가 없으면 javax.persistence.NoResultException 발생
      - 둘 이상이면 javax.persistence.NonUniqueResultException 발생
- 파라미터 바인딩
  - 이름 기준 바인딩
    - ```
      SELECT m FROM Member m where m.username=:username
      query.setParameter("username", usernameParam);
      ```
  - 위치 기준 바인딩 (지양)
    - ```
      SELECT m FROM Member m where m.username=?1
      query.setParameter(1, usernameParam);
      ```
    - 기능이 변경되어 순서가 변경된다면, 오류가 발생할 여지가 크다.
- 프로젝션
  - SELECT 절에 조회할 대상을 지정하는 것을 뜻한다.
  - 프로젝션 종류
    - 엔티티 프로젝션 예시
      - SELECT m FROM Member m
      - SELECT m.team FROM Member m
    - 임베디드 타입 프로젝션 예시
      - SELECT m.address FROM Member m
    - 스칼라 타입 프로젝션 예시
      - SELECT m.username, m.age FROM Member m
- 페이징 API
  - JPA는 페이징을 다음 두 API로 추상화한다.
    - setFirstResult(int startPosition)
      - 조회 시작 위치
      - 0부터 시작
    - setMaxResults(int maxResult)
      - 조회할 데이터 수
- 조인
  - 종류
    - 내부 조인
      - Ex) SELECT m FROM Member m [INNER] JOIN m.team t
    - 외부 조인:
      - Ex) SELECT m FROM Member m LEFT [OUTER] JOIN m.team t
    - 세타 조인:
      - Ex)  SELECT count(m) FROM Member m, Team t WHERE m.username = t.name
  - ON 절
    - ON절을 활용한 조인 (JPA 2.1부터 지원)
- 서브 쿼리
  - 서브 쿼리 사용 예시
    - Ex) select m from Member m where m.age > (select avg(m2.age) from Member m2)
    - Ex) select m from Member m where (select count(o) from Order o where m = o.member) > 0
  - 서브 쿼리 지원 함수
    - 그 외 EXISTS, NOT EXISTS, IN, NOT IN, ALL, ANY, SOME 등 지원
  - 서브 쿼리 특이사항
    - 원래는 SELECT와 WHERE 절에만 사용이 가능했지만, 하이버네이트6 부터는 FROM 절의 서브쿼리를 지원
- JPQL 기타 문법
  - SQL과 문법이 같은 식은 대부분 지원한다.
    - EXISTS, IN
    - AND, OR, NOT
    - =, >, >=, <, <=, <>
    - BETWEEN, LIKE, IS NULL
  - 조건식도 지원한다.
    - CASE
    - COALESCE
    - NULLIF
  - JPQL 함수
    - 아래와 같은 기본함수를 제공한다.
      - CONCAT
      - SUBSTRING
      - TRIM
      - LOWER, UPPER
      - LENGTH
      - LOCATE
      - ABS, SQRT, MOD
      - SIZE, INDEX(JPA 용도)
    - 사용자 정의 함수도 사용할 수 있다.
      - 하이버네이트에서 사용 전 방언에 추가하여 사용할 수 있다.
      - 사용예시 
        - select function('group_concat', i.name) from Item i

### JPQL 경로 표현식
- 경로 표현식이란?
  - .(점)을 찍어 객체 그래프를 탐색하는 것을 의미.
- 종류
  - 상태 필드(state field)
    - 단순히 값을 저장하기 위한 필드
    - Ex) m.username
  - 연관 필드(association field)
    - 연관관계를 위한 필드
      - 단일 값 연관 필드
        - @ManyToOne, @OneToOne, 대상이 엔티티인 것
        - Ex) m.team
      - 컬렉션 값 연관 필드
        - @OneToMany, @ManyToMany, 대상이 컬렉션인 것
        - Ex) m.orders
- 경로 표현식 특징
  - 상태 필드
    - 경로 탐색의 끝으로 더 이상 탐색할 수 없음
    - Ex) select `m.username, m.age` from Member m
  - 단일 값 연관 경로
    - 묵시적 내부 조인이 발생
    - 더 탐색할 수 있음
    - Ex) select `o.member` from Order o
  - 컬렉션 값 연관 경로
    - 묵시적 내부 조인이 발생
    - 더 탐색할 수 있음
      - FROM 절에서 명시적 조인을 통해 별칭을 얻으면 별칭을 통해 더 탐색할 수 있음
      - Ex) select `t.members` from Team t
        - members에는 username, age 등이 있지만, 더 이상 탐색 불가.
        - 탐색을 하려면 명시적 조인을 해야한다.
          - Ex) select m.username from Team t join t.members m
- 명시직 조인과 묵시적 조인
  - 명시적 조인
    - join 키워드 직접 사용하는 것
  - 묵시적 조인
    - 경로 표현식에 의해 묵시적으로 SQL 조인 발생하는 것
    - 내부 조인만 가능하다.
    - 가급적 묵시적 조인 대신에 명시적 조인을 사용하는 것이 좋다.
      - 조인은 SQL 튜닝에 중요 포인트인데, 묵시적 조인은 조인이 일어나는 상황을 한눈에 파악하기 어려움.

### JPQL - 페치 조인(fetch join)
- 페치 조인
  - JPQL에서 성능 최적화를 위해 제공하는 기능
  - 연관된 엔티티나 컬렉션을 SQL 한 번에 함께 조회하는 기능
  - Ex)
    - 회원을 조회하면서 연관된 팀도 함께 조회(SQL 한 번에)
    - JPQL
      - select m from Member m join fetch m.team
    - SQL
      - SELECT M.*, T.* FROM MEMBER M INNER JOIN TEAM T ON M.TEAM_ID=T.ID
- 페치 조인과 일반 조인의 차이
  - 일반 조인 실행시 연관된 엔티티를 함께 조회하지 않음
    - JPQL
      - select t from Team t join t.members m where t.name = ‘팀A'
    - SQL
      - SELECT T.* FROM TEAM T INNER JOIN MEMBER M ON T.ID=M.TEAM_ID WHERE T.NAME = '팀A'
  - 반면 페치 조인은 Member 엔티티도 함께 조회한다.
    - JPQL
      - select t from Team t join fetch t.members where t.name = ‘팀A'
    - SQL
      - SELECT T.*, M.* FROM TEAM T INNER JOIN MEMBER M ON T.ID=M.TEAM_ID WHERE T.NAME = '팀A'
- 페치 조인의 특징과 한계
  - 페치 조인 대상에는 별칭을 줄 수 없다.
    - 하이버네이트는 가능하지만, 가급적 사용하지 않는 것이 좋다.
  - 둘 이상의 컬렉션은 페치 조인 할 수 없다.
  - 컬렉션을 페치 조인하면 페이징 API(setFirstResult, setMaxResults)를 사용할 수 없다.
    - 일대일, 다대일 같은 단일 값 연관 필드들은 페치 조인해도 페이징 가능
    - 하이버네이트는 경고 로그를 남기고 메모리에서 페이징(매우 위험)
      - 메모리로 모든 데이터를 로드해서 페이징하는 방식이기 때문에 OOM이 발생 할 수도 있다.
  - 엔티티에 직접 적용하는 글로벌 로딩 전략보다 우선함
    - @OneToMany(fetch = FetchType.LAZY) 와 같이 글로벌 로딩 전략으로 선언되어 있어도 fetch join을 하면 즉시로딩된다.
  - 모든 것을 페치 조인으로 해결할 수 는 없다.
    - 페치 조인은 객체 그래프를 유지할 때 사용하면 효과적
    - 여러 테이블을 조인해서 엔티티가 가진 모양이 아닌 전혀 다른 결과를 내야 하면, 페치 조인 보다는 일반 조인을 사용하고 필요한 데이터들만 조회해서 DTO로 반환하는 것이 효과적

### JPQL - 다형성 쿼리
- TYPE
  - 조회 대상을 특정 자식으로 한정할 때 사용할 수 있다.
  - Ex) select i from Item i where type(i) IN (Book, Movie)
- TREAT
  - 자바의 타입 캐스팅과 유사
  - 상속 구조에서 부모 타입을 특정 자식 타입으로 다룰 때 사용
  - Ex) select i from Item i where treat(i as Book).author = ‘kim’

### JPQL - 엔티티 직접 사용
- JPQL에서 엔티티를 직접 사용하면, SQL에서 해당 엔티티의 기본 키 값을 사용
- 엔티티의 아이디를 사용할 수도 있지만, 엔티티를 직접 사용할 수도 있다.
  - 아이디 사용
    - select count(m.id) from Member m
    - select m from Member m where m.id = :memberId
  - 엔티티 직접 사용
    - select count(m) from Member m 
    - select m from Member m where m = :member

### JPQL - Named 쿼리
- 미리 정의해서 이름을 부여해두고 사용하는 JPQL
- 애플리케이션 로딩 시점에 초기화 후 재사용
  - 코스트 절약
- 애플리케이션 로딩 시점에 쿼리를 검증
- 사용예시
  - ```
    // 선언부 예시
    @Entity
    @NamedQuery(
      name = "Member.findByUsername",
      query="select m from Member m where m.username = :username")
    public class Member {
      // ...
    }
    
    // 사용부 예시
    List<Member> resultList =
        em.createNamedQuery("Member.findByUsername", Member.class)
        .setParameter("username", "회원1")
        .getResultList();
    ```

### JPQL - 벌크 연산
- JPA에서는 한 번에 여러 데이터가 변경된다고 가정했을 때, 변경 감지 기능으로 실행하려면 너무 많은 SQL 실행된다는 단점이 있다.
- 벌크 연산을 사용한다면, 쿼리 한 번으로 여러 테이블 로우 변경할 수 있다.
  - 단, 벌크 연산은 영속성 컨텍스트를 무시하고 데이터베이스에 직접 쿼리를 실행한다.
  - 따라서 `영속성 컨텍스트를 사용하는 코드`와 `벌크 연산을 사용하는 코드`가 모두 존재할 때는 아래 두 가지 방법 중 하나를 선택해서 사용해야한다.
    - 벌크 연산을 먼저 실행
    - 벌크 연산 수행 후 영속성 컨텍스트 초기화

<br><hr>

# 스프링 데이터 JPA
### 공통 인터페이스 설정
- JavaConfig 설정
  - @EnableJpaRepositories 어노테이션을 사용해서 설정 가능
    - Ex) @EnableJpaRepositories(basePackages = "jpabook.jpashop.repository")
    - 스프링 부트 사용시 `@SpringBootApplication` 와 동등 레벨부터 모든 하위를 기본으로 인식한다.
      - 때문에 생략 가능하다.
    - 만약 특정 위치를 지정하고 싶다면 `@EnableJpaRepositories` 필요
- 공통 인터페이스 적용
  - 스프링 데이터 JPA 기반 MemberRepository 적용 예시
  - ```
    public interface MemberRepository extends JpaRepository<Member, Long> {
    }
    ```
    - `@Repository` 어노테이션 생략 가능
  - JpaRepository 인터페이스는 공통 CRUD를 제공한다.
  - 제네릭은 <엔티티 타입, 식별자 타입> 으로 설정한다.
    - Ex) <Member, Long> : 엔티티는 Member이며, Member의 식별자(=PK)는 Long 타입
- 주요 메서드
  - save(S)
    - 새로운 엔티티는 저장하고 이미 있는 엔티티는 병합한다.
  - delete(T)
    - 엔티티 하나를 삭제한다.
    - 내부에서 `EntityManager.remove()` 호출
  - findById(ID)
    - 엔티티 하나를 조회한다.
    - 내부에서 `EntityManager.find()` 호출
  - getOne(ID)
    - 엔티티를 프록시로 조회한다.
    - 내부에서 `EntityManager.getReference()` 호출
  - findAll(…)
    - 모든 엔티티를 조회한다.
    - 정렬(`Sort` )이나 페이징(`Pageable` ) 조건을 파라미터로 제공할 수 있다.

### 메소드 이름으로 쿼리 생성
- 스프링 데이터 JPA는 메소드 이름을 분석해서 JPQL을 생성하고 실행하는 기능을 지원한다.
  - Ex) List<Member> findByUsernameAndAgeGreaterThan(String username, int age);
- 제공하는 쿼리 메소드 기능
  - 조회
    - find…By ,read…By ,query…By get…By,
  - COUNT
    - count…By 반환타입 `long`
  - EXISTS
    - exists…By 반환타입 `boolean`
  - 삭제
    - delete…By, remove…By 반환타입 `long`
  - DISTINCT
    - findDistinct, findMemberDistinctBy
  - LIMIT
    - findFirst3, findFirst, findTop, findTop3

### JPA NamedQuery
- `@NamedQuery` 어노테이션을 사용해서 Named 쿼리를 정의할 수도 있지만, 스프링 데이터 JPA로는 아래와 같이 사용할 수도 있다.
  - ```
    @Query(name = "Member.findByUsername")
    List<Member> findByUsername(@Param("username") String username);
    ```    
    - @Query 를 생략하고 메서드 이름만으로 Named 쿼리를 호출할 수 있다.
      - 이 때는 Entity에 @NamedQuery로 선언되어 있어야한다.
    - 만약 실행할 Named 쿼리가 없으면 메서드 이름으로 쿼리 생성 전략을 사용한다.
    - 스프링 데이터 JPA를 사용하면 실무에서 Named Query를 직접 등록해서 사용하는 일은 드물다.
    - `@Query` 를 사용해서 레포지토리 메소드에 쿼리를 직접 정의해서 쓰는 경우가 대부분이기 때문.

### @Query, 레포지토리 메소드에 쿼리 정의하기
- ```
  @Query("select m from Member m where m.username= :username and m.age = :age")
  List<Member> findUser(@Param("username") String username, @Param("age") int age);
  ```
  - JPA Named 쿼리처럼 애플리케이션 실행 시점에 문법 오류를 발견할 수 있다는 장점이 있다.
  - 아래와 같이 DTO에 직접 담아서 반환할 수도 있다.
    - ```
      @Query("select new study.datajpa.dto.MemberDto(m.id, m.username, t.name) from Member m join m.team t")
      List<MemberDto> findMemberDto();
      ```
      
### 파라미터 바인딩
- 파라미터 바인딩 방식은 '위치 기반' 방식과 '이름 기반' 방식이 있다.
- 위치기반은 순서가 바뀌면 오류가 발생할 여지가 있어 '이름 기반' 방식 사용이 권장된다.
- 사용예시
  - ```
    @Query("select m from Member m where m.username = :name")
    Member findMembers(@Param("name") String username);
    ```
  - ```
    // 컬렉션 파라미터 바인딩 예시
    @Query("select m from Member m where m.username in :names")
    List<Member> findByNames(@Param("names") List<String> names);
    ```

### 반환 타입
- 스프링 데이터 JPA는 유연한 반환 타입을 지원한다.
  - 컬렉션
    - List<Member> findByUsername(String name);
  - 단건
    - Member findByUsername(String name);
  - 단건 Optional
    - Optional<Member> findByUsername(String name);

### 페이징과 정렬
- 페이징과 정렬 사용 예제
  - count 쿼리가 같이 수행되는 경우
    - Page<Member> findByUsername(String name, Pageable pageable);
  - count 쿼리가 같이 수행되지 않는 경우
    - Slice<Member> findByUsername(String name, Pageable pageable);
    - List<Member> findByUsername(String name, Pageable pageable);
    - List<Member> findByUsername(String name, Sort sort);
- 페이징 관련 파라미터
  - `Pageable`은 페이징을 위한 파라미터이다.
  - 인터페이스이며, 구현체로는 `org.springframework.data.domain.PageRequest` 객체를 사용한다.
  - 사용예시
    - ```
      PageRequest pageRequest = PageRequest.of(0, 3, Sort.by(Sort.Direction.DESC,
      Page<Member> page = memberRepository.findByAge(10, pageRequest);
      ```
- 카운트 쿼리 분리
  - 리스트 조회 쿼리와 카운트 쿼리를 분리할 수 있다.
    - Ex) 리스트 쿼리는 Member와 Team을 Join해서 조회해야하는데, 카운트 쿼리는 Member 테이블만 있어도 될 때
    - ```
      @Query(value = "select m from Member m left join m.team t",
          countQuery = "select count(m.username) from Member m")
      Page<Member> findMemberAllCountBy(Pageable pageable);
      ```
      
### 벌크성 수정 쿼리
- 스프링 데이터 JPA에서는 어노테이션으로 벌크성 수정 쿼리를 작성할 수 있다.
  - ```
    @Modifying
    @Query("update Member m set m.age = m.age + 1 where m.age >= :age")
    int bulkAgePlus(@Param("age") int age);
    ```
  - 벌크성 수정, 삭제 쿼리는 `@Modifying` 어노테이션을 사용
  - 벌크성 쿼리를 실행하고 나서 영속성 컨텍스트 초기화 필요.
    - 직접 Entity Manager를 flush / clear 하거나
    - @Modifying()에 옵션을 설정한다.
      - @Modifying(clearAutomatically = true)
      - 기본값은 `false`

### @EntityGraph
- 연관된 엔티티들을 SQL 한번에 조회하는 방법
- 사용하는 이유
  - 지연로딩 관계에서는 N+1 문제가 발생할 수 있다.
  - JPQL 페치 조인으로 해결할 수 있는데, 스프링 데이터 JPA에서는 @EntityGraph 어노테이션을 활용해서 쉽게 해결할 수 있다.
    - 사실상 페치 조인(FETCH JOIN)의 간편 버전
- 사용 예시
  - ```
    // 공통 메서드 오버라이드
    @Override
    @EntityGraph(attributePaths = {"team"})
    List<Member> findAll();
    
    // JPQL + 엔티티 그래프
    @EntityGraph(attributePaths = {"team"})
    @Query("select m from Member m")
    List<Member> findMemberEntityGraph();
    
    // 메서드 이름 쿼리
    @EntityGraph(attributePaths = {"team"})
    List<Member> findByUsername(String username)
    ```

### JPA Hint
- JPA Hint란?
  - SQL 힌트가 아니라 JPA 구현체에게 제공하는 힌트
  - JPA의 기본 동작을 미세 조정할 수 있도록 도와주는 기능이다.
- 주요 힌트 종류
  - org.hibernate.readOnly
    - 읽기 전용 모드로 설정하여 변경 감지를 비활성화
  - org.hibernate.cacheable
    - 2차 캐시를 활성화
  - org.hibernate.fetchSize
    - 한 번에 가져올 레코드 수를 조정하여 페이징 성능 개선
  - org.hibernate.comment
    - 실행되는 SQL에 주석 추가
- 사용예시
  - ```
    @QueryHints(value = @QueryHint(name = "org.hibernate.readOnly", value = "true"))
    Member findReadOnlyByUsername(String username);
    ```
    - readOnly 속성에 의해서 아래 로직에서 Update 쿼리가 실행되지 않는다.
      - ```
        @Test
        public void queryHint() throws Exception {
          // given
          memberRepository.save(new Member("member1", 10));
          em.flush();
          em.clear();
          
          // when
          Member member = memberRepository.findReadOnlyByUsername("member1");
          member.setUsername("member2");
          
          em.flush(); // Update Query 실행X
        }
        ```
        
### Lock
- @Lock 어노테이션
  - JPA에서 비관적 락(Pessimistic Lock)을 적용할 때 주로 사용하는 어노테이션이다.
    - 옵션에 따라서 낙관적 락으로도 사용 가능하다.
- 락 모드
  - PESSIMISTIC_READ
    - 읽기 전용 비관적 락.
    - 다른 트랜잭션이 수정/삭제 못 하게 막음
    - SELECT ... FOR SHARE (DB에 따라 다름)
  - PESSIMISTIC_WRITE
    - 쓰기용 비관적 락.
    - 다른 트랜잭션이 읽기/쓰기/삭제 모두 차단
    - SELECT ... FOR UPDATE
  - PESSIMISTIC_FORCE_INCREMENT
    - PESSIMISTIC_WRITE + 버전 필드(@Version) 증가
    - Hibernate 전용
  - OPTIMISTIC
    - 낙관적 락.
    - @Version 필드를 사용하여 변경 감지
    - @Version 필드가 필요함
  - OPTIMISTIC_FORCE_INCREMENT
    - OPTIMISTIC + 버전 필드를 강제로 증가
    - @Version 필드 필요

### 사용자 정의 리포지토리
- 사용자 정의 리포지토리의 필요성
  - 스프링 데이터 JPA 리포지토리는 인터페이스만 정의하고 구현체는 스프링이 자동 생성.
  - 만약 필요한 메서드를 직접 구현하고 싶다면, 스프링 데이터 JPA가 제공하는 인터페이스를 직접 구현해야하는데 이렇게 되면 구현해야 하는 기능이 너무 많음.
  - 다양한 이유로 인터페이스의 메서드를 직접 구현하고 싶다면?
    - JPA 직접 사용(EntityManager)
    - 스프링 JDBC Template 사용
    - MyBatis 사용
    - 데이터베이스 커넥션 직접 사용 등등...
    - Querydsl 사용
    - 그리고 사용자 정의 인터페이스!
- 구성예시
  - <img width="927" alt="image" src="https://github.com/user-attachments/assets/99750ac2-3aa8-402b-b761-f710f967fb58" />
- 사용자 정의 인터페이스 사용 예시
  - ```
    // 인터페이스 정의
    public interface MemberRepositoryCustom {
      List<Member> findMemberCustom();
    }

    // 인터페이스 구현
    // - 구현체는 리포지토리 인터페이스 이름 + `Impl` 이라는 규칙을 따라야한다. 그래야지 스프링 데이터 JPA가 인식해서 스프링 빈으로 등록한다.
    // - 최신버전에서는 사용자 정의 인터페이스 명 + `Impl` 방식도 지원 (Ex. MemberRepositoryCustomImpl)
    @RequiredArgsConstructor
    public class MemberRepositoryImpl implements MemberRepositoryCustom {
      private final EntityManager em;

      @Override
      public List<Member> findMemberCustom() {
        return em.createQuery("select m from Member m").getResultList();
      }
    }

    // 스프링 데이터 JPA 리포지토리에서 위의 인터페이스 상속 (구현체가 아닌 인터페이스를 상속 받아야한다.)
    public interface MemberRepository extends JpaRepository<Member, Long>, MemberRepositoryCustom {
    }
    ```

### Auditing
- Auditing의 필요성
  - 엔티티 생성, 변경 사항을 추적하기 위하여 아래와 같은 필드들이 대부분의 엔티티에 적용되야 한다면?
    - 등록일
    - 수정일
    - 등록자
    - 수정자
  - 모든 엔티티마다 구현할 필요없이 스프링 데이터 JPA에서 지원해주는 Auditing 기능을 사용하면 된다.
- 설정 예시
  - 설정 클래스에 @EnableJpaAuditing 적용
  - Auditing을 적용한 클래스 생성
    - 클래스에 @EntityListeners(AuditingEntityListener.class) 선언
    - 필드에 아래 어노테이션 사용
      - @CreatedDate
      - @LastModifiedDate
      - @CreatedBy
      - @LastModifiedBy
    - 코드 샘플
      - ```
        @EntityListeners(AuditingEntityListener.class)
        @MappedSuperclass
        @Getter
        public class BaseEntity {
          @CreatedDate
          @Column(updatable = false)
          private LocalDateTime createdDate;
  
          @LastModifiedDate
          private LocalDateTime lastModifiedDate;
  
          @CreatedBy
          @Column(updatable = false)
          private String createdBy;
  
          @LastModifiedBy
          private String lastModifiedBy;
        }
        ```
  - 사용하고자 하는 엔티티에서 BaseEntity 상속받아 사용
    - 만약 모든 엔티티에서 사용하고자하면 별도 설정을 통해서 전체 적용도 가능하다.

### 스프링 데이터 JPA 구현체 분석
- 스프링 데이터 JPA가 제공하는 공통 인터페이스의 구현체
  - org.springframework.data.jpa.repository.support.SimpleJpaRepository
    - 아래 어노테이션을 갖는다.
      - @Repository
        - JPA 예외를 스프링이 추상화한 예외로 변환
      - @Transactional(readOnly = true)
        - JPA의 모든 변경은 트랜잭션 안에서 동작
        - 스프링 데이터 JPA는 변경(등록, 수정, 삭제) 메서드를 트랜잭션 처리
        - 서비스 계층에서 트랜잭션을 시작하지 않으면 리파지토리에서 트랜잭션 시작
        - 서비스 계층에서 트랜잭션을 시작하면 리파지토리는 해당 트랜잭션을 전파 받아서 사용
        - readOnly = true 속성
          - 데이터를 단순히 조회만 하고 변경하지 않는 트랜잭션에서 해당 옵션을 사용하면 플러시를 생략해서 약간의 성능 향상을 얻을 수 있음
- save() 메서드
  - save() 메서드 내부 동작
    - save() 메서드는 새로운 엔티티냐에 따라서
      - 새로운 엔티티면 저장 (persist)
      - 새로운 엔티티가 아니면 병합 (merge)
  - 새로운 엔티티를 판단하는 기본 전략
    - 식별자가 객체(Ex. Long)일 때 `null`로 판단
    - 식별자가 자바 기본 타입(Ex. long)일 때 `0`으로 판단
  - save() 메서드의 동작 과정을 올바르게 이해해야 하는 이유
    - JPA 식별자 생성 전략이 `@GenerateValue` 면 `save()` 호출 시점에 식별자가 없으므로 새로운 엔티티로 인식해서 정상 동작한다.
    - 그런데 JPA 식별자 생성 전략이 `@Id` 만 사용해서 직접 할당하는 방식이면, 이미 식별자 값이 있는 상태로 `save()` 를 호출한다.
      - 따라서 이 경우 `merge()` 가 호출된다.
        - `merge()` 는 우선 DB를 호출해서 값을 확인하고, DB에 값이 없으면 새로운 엔티티로 인지하므로 매우 비효율 적이다.
        - 따라서 `Persistable` 를 사용해서 새로운 엔티티 확인 여부를 직접 구현하게는 효과적이다.

### Specifications
- Specifications 란?
  - 도메인 주도 설계(Domain Driven Design)는 SPECIFICATION(명세)라는 개념을 소개.
  - 스프링 데이터 JPA는 JPA Criteria를 활용해서 이 개념을 사용할 수 있도록 지원하고 있다.
  - AND OR 같은 연산자를 조합해서 다양한 검색조건을 쉽게 생성할 수 있다는 장점이 있지만, 활용도가 높은 편은 아니다.

### Query By Example
- 원하는 검색 조건을 가지고 있는 Probe라고 하는 도메인 객체를 생성하여 Example 객체를 생성하고 검색하는 기술.
- 장점
  - 동적 쿼리를 편리하게 처리
  - 도메인 객체를 그대로 사용
  - 데이터 저장소를 RDB에서 NOSQL로 변경해도 코드 변경이 없게 추상화 되어 있음
  - 스프링 데이터 JPA `JpaRepository` 인터페이스에 이미 포함
- 단점
  - 조인은 가능하지만 내부 조인(INNER JOIN)만 가능함 외부 조인(LEFT JOIN) 안됨
  - 다음과 같은 중첩 제약조건 안됨
    - `firstname = ?0 or (firstname = ?1 and lastname = ?2)`
  - 매칭 조건이 매우 단순함
    - 문자를 제외한 속성은 정확한 매칭(=)만 지원
   
### Projections
- 엔티티 대신에 DTO를 편리하게 조회할 때 사용하는 기술.
- 조회할 엔티티의 필드를 getter 형식으로 지정하면 해당 필드만 선택해서 조회(Projection)
  - ```
    public interface UsernameOnly {
      String getUsername();
    }

    public interface MemberRepository ... {
      // 메서드 이름은 자유, 반환 타입으로 인지
      List<UsernameOnly> findProjectionsByUsername(String username);
    }
    ```
- 종류 (위 기술들과 마찬가지로 활용도가 높은 편은 아니라 코드 예시는 생략)
  - 인터페이스 기반 Closed Projections
  - 인터페이스 기반 Open Proejctions
  - 클래스 기반 Projection
  - 동적 Projections

### 네이티브 쿼리
- JPQL이 아닌 직접 쿼리를 작성할 수 있는 네이티브 쿼리 기능을 지원한다.
- 사용예시
  - ```
    @Query(value = "select * from member where username = ?", nativeQuery = true)
    Member findByNativeQuery(String username);
    ```
- 코드 복잡성이 올라갈 수 있으므로, 네이티브 쿼리보다는 차라리 dbcTemplate 또는 myBatis가 권장된다.   

<br><hr>

# QueryDSL
### Querydsl 기본사용법
- 사용방법
  - EntityManager로 `JPAQueryFactory` 생성
  - JPAQueryFactory를 빌드형태로 사용하여 쿼리를 작성한다.
- 사용예시
  - ```
    JPAQueryFactory queryFactory = new JPAQueryFactory(em);
    QMember m = new QMember("m");
  
    Member findMember = queryFactory
      .select(m)
      .from(m)
      .where(m.username.eq("member1"))
      .fetchOne();
    ```

### 기본 Q-Type 활용
- Q클래스 인스턴스를 사용하는 2가지 방법
  - 별칭 직접 지정
    - QMember qMember = new QMember("m");
  - 기본 인스턴스 사용
    - QMember qMember = QMember.member;
    - 같은 테이블을 조인해야 하는 경우가 아니면 기본 인스턴스를 사용

### 검색 조건 쿼리
- 검색 조건 예시
  - ```
    member.username.eq("member1") // username = 'member1'
    member.username.ne("member1") // username != 'member1'
    member.username.eq("member1").not() // username != 'member1'
    member.username.isNotNull() // is not null
    
    member.age.in(10, 20) // age in (10,20)
    member.age.notIn(10, 20) // age not in (10, 20)
    member.age.between(10,30) // between 10, 30
    member.age.goe(30) // age >= 30
    member.age.gt(30) // age > 30
    member.age.loe(30) // age <= 30
    member.age.lt(30) // age < 30
    
    member.username.like("member%") // like 검색
    member.username.contains("member") // like ‘%member%’ 검색
    member.username.startsWith("member") // like ‘member%’ 검색
    ```

### 결과 조회
- 결과 조회 종류
  - fetch()
    - 리스트 조회, 데이터 없으면 빈 리스트 반환
  - fetchOne()
    - 단 건 조회
    - 결과가 없으면 : null
    - 결과가 둘 이상이면 : com.querydsl.core.NonUniqueResultException
  - fetchFirst()
    - 검색 결과 중 첫 번째 항목만 반환
    - limit(1).fetchOne() 와 검색결과가 같다.
  - fetchResults()
    - 페이징 정보 포함
    - total count 쿼리 추가 실행
  - fetchCount()
    - count 쿼리로 변경해서 count 수 조회
- 사용 예시
  - ```
    // List
    List<Member> fetch = queryFactory
      .selectFrom(member)
      .fetch();
    
    // 단 건
    Member findMember1 = queryFactory
      .selectFrom(member)
      .fetchOne();
    
    // 처음 한 건 조회
    Member findMember2 = queryFactory
      .selectFrom(member)
      .fetchFirst();
    
    // 페이징에서 사용
    QueryResults<Member> results = queryFactory
      .selectFrom(member)
      .fetchResults();
    
    // count 쿼리로 변경
    long count = queryFactory
      .selectFrom(member)
      .fetchCount();
    ```
    
### 정렬
- 일반 정렬
  - desc()
  - asc() 
- null 데이터 순서 부여
  - nullsLast()
  - nullsFirst() 
- 정렬 예시
  - ```
    List<Member> result = queryFactory
      .selectFrom(member)
      .where(member.age.eq(100))
      .orderBy(member.age.desc(), member.username.asc().nullsLast()) // 정렬 사용
      .fetch();
    ```
    
### 페이징
- 조회 건수 제한
  - ```
    List<Member> result = queryFactory
      .selectFrom(member)
      .offset(1) // 0부터 시작
      .limit(2) // 최대 2건
      .fetch();
    ```
- 전체 조회 수를 포함한 조회
  - ```
    QueryResults<Member> queryResults = queryFactory
      .selectFrom(member)
      .orderBy(member.username.desc())
      .offset(1)
      .limit(2)
      .fetchResults();
    
    assertThat(queryResults.getTotal()).isEqualTo(4);
    assertThat(queryResults.getLimit()).isEqualTo(2);
    assertThat(queryResults.getOffset()).isEqualTo(1);
    assertThat(queryResults.getResults().size()).isEqualTo(2);
    ```
  - 주의사항
    - 위 로직은 count 쿼리가 함께 실행된다.
      - 원본 쿼리에 조인이 있다면, 카운트 쿼리도 조인을 하기 때문에 성능 이슈가 발생할 수 있다.
      - count 쿼리에 조인이 필요없는 성능 최적화가 필요하다면, count 전용 쿼리를 별도로 작성해야 한다.

### 집합
- 집합 함수 종류
  - 개수
    - COUNT(m)
  - 합
    - SUM(m.age)
  - 평균
    - AVG(m.age)
  - 최대
    - MAX(m.age)
  - 최소
    - MIN(m.age)
- 예시
  - ```
    List<Tuple> result = queryFactory
      .select(member.count(),
              member.age.sum(),
              member.age.avg(),
              member.age.max(),
              member.age.min())
      .from(member)
      .fetch();
    ```
- GroupBy 및 Having
  - GroupBy 예시
    - ```
      List<Tuple> result = queryFactory
        .select(team.name, member.age.avg())
        .from(member)
        .join(member.team, team)
        .groupBy(team.name)
        .fetch();
      ```
  - Having 예시
    - ```
      …
      .groupBy(item.price)
      .having(item.price.gt(1000))
      …
      ```
      
### 조인
- 기본 조인
  - 조인의 기본 문법은 첫 번째 파라미터에 조인 대상을 지정하고, 두 번째 파라미터에 별칭(alias)으로 사용할 Q 타입을 지정하면 된다.
  - join(조인 대상, 별칭으로 사용할 Q타입)
  - 종류
    - 내부 조인(inner join)
      - join()
      - innerJoin()
    - left 외부 조인(left outer join)
      - leftJoin()
    - right 외부 조인(right outer join)
      - rightJoin()
  - 사용예시
    - ```
      List<Member> result = queryFactory
        .selectFrom(member)
        .join(member.team, team)
        .where(team.name.eq("teamA"))
        .fetch();
      ```
- 세타 조인
  - 연관관계가 없는 필드로 조인
  - from 절에 여러 엔티티를 선택해서 세타 조인이 가능하다.
  - 사용예시 (Ex. 사용자 이름과 팀 이름이 같은 경우)
    - ```
      List<Member> result = queryFactory
        .select(member)
        .from(member, team)
        .where(member.username.eq(team.name))
        .fetch();
      ```
- on절
  - ON절은 크게 2가지 케이스에 사용된다.
    - 조인 대상을 필터링할 때 사용한다.
      - Ex. 회원과 팀을 조인하면서, 팀 이름이 teamA인 팀만 조인, 회원은 모두 조회
         - ```
           List<Tuple> result = queryFactory
             .select(member, team)
             .from(member)
             .leftJoin(member.team, team).on(team.name.eq("teamA"))
             .fetch();
           ```
      - on 절을 활용해 조인 대상을 필터링 할 때,
        - 외부조인이 아니라 내부조인(inner join)을 사용하면, where 절에서 필터링 하는 것과 기능이 동일하다.
        - 따라서 on 절을 활용한 조인 대상 필터링을 사용할 때, 내부조인이면 익숙한 where 절로 해결하고, 정말 외부조인이 필요한 경우에만 이 기능을 사용하자.
    - 연관관계 없는 엔티티 외부 조인
      - Ex. 회원의 이름과 팀의 이름이 같은 대상 외부 조인
        - ```
          List<Tuple> result = queryFactory
            .select(member, team)
            .from(member)
            .leftJoin(team).on(member.username.eq(team.name))
            .fetch();
          ```
- 페치 조인
  - SQL조인을 활용해서 연관된 엔티티를 SQL 한번에 조회하는 기능이다.
    - 지연로딩으로 설정되어 있는 경우, Member를 조회하고 Team에 접근을 하면 N+1 문제가 야기될 수 있다.
    - 이를 보완하기 위해 SQL 한 번에 연관된 엔티티를 조회함으로써 해결할 수 있다.
  - 주로 성능 최적화에 사용하는 방법이다.
  - `join(), leftJoin()` 등 조인 기능 뒤에 `fetchJoin()`을 추가한다.
  - 사용 예시
    - ```
      Member findMember = queryFactory
        .selectFrom(member)
        .join(member.team, team).fetchJoin()
        .where(member.username.eq("member1"))
        .fetchOne();
      ```
      
### 서브 쿼리
- com.querydsl.jpa.JPAExpressions 를 사용해서 구현할 수 있다.
  - ```
    List<Member> result = queryFactory
      .selectFrom(member)
      .where(member.age.eq(
                JPAExpressions
                    .select(memberSub.age.max())
                    .from(memberSub)
      ))
      .fetch();
    ```
- 서브쿼리의 한계와 해결방안
  - JPA JPQL 서브쿼리의 한계점으로 from 절의 서브쿼리(인라인 뷰)는 지원하지 않는다.
    - 때문에 QueryDSL에서도 지원하지 않는다.
  - from절에 서브쿼리가 필요하다면, 아래와 같은 방안도 고려해볼 수 있다.
    - 서브쿼리를 join으로 변경
    - 애플리케이션에서 쿼리를 2번 분리해서 실행
    - nativeSQL을 사용

### Case 문
- select, 조건절(where), order by에서 사용 가능하다.
  - ```
    // 단순 사용
    List<String> result = queryFactory
       .select(member.age
                .when(10).then("열살")
                .when(20).then("스무살")
                .otherwise("기타"))
       .from(membe)
       .fetch();

    // CaseBuilder() 사용하여 복잡한 조건 구현
    List<String> result = queryFactory
      .select(new CaseBuilder()
                .when(member.age.between(0, 20)).then("0~20살")
                .when(member.age.between(21, 30)).then("21~30살")
                .otherwise("기타"))
      .from(member)
      .fetch();
    ```  
    
### 상수, 문자 더하기
- 상수 더하기 - Expressions.constant() 사용
  - ```
    Tuple result = queryFactory
      .select(member.username, Expressions.constant("A"))
      .from(member)
      .fetchFirst();
    ```
- 문자 더하기 - concat() 사용
  - ```
    String result = queryFactory
      .select(member.username.concat("_").concat(member.age.stringValue()))
      .from(member)
      .where(member.us
    ```
  - 문자가 아닌 다른 타입들을 stringValue()를 사용해서 문자로 변환할 수 있다.
    - ENUM 처리 시 유용

### 프로젝션과 결과 반환
- 프로젝션 대상이 하나인 경우
  - 프로젝션 대상이 하나면 타입을 명확하게 지정할 수 있음
  - ```
    List<String> result = queryFactory
      .select(member.username)
      .from(member)
      .fetch();
    ```
- 프로젝션 대상이 둘 이상인 경우
  - 튜플이나 DTO로 조회 필요
  - ```
    // 튜플 사용
    List<Tuple> result = queryFactory
      .select(member.username, member.age)
      .from(member)
      .fetch();
    
    // Querydsl 빈 - 필드
    List<MemberDto> result = queryFactory
      .select(Projections.fields(MemberDto.class, member.username, member.age))
      .from(member)
      .fetch();
    
    // Querydsl 빈 - Setter
    List<MemberDto> result = queryFactory
      .select(Projections.bean(MemberDto.class, member.username, member.age))
      .from(member)
      .fetch();
    
    // Querydsl 빈 - 생성자 사용
    List<MemberDto> result = queryFactory
      .select(Projections.constructor(MemberDto.class, member.username, member.age))
      .from(member)
      .fetch();
    
    // 생성자 + @QueryProjection
    // DTO 생성자에 @QueryProjection 추가 후 사용.
    List<MemberDto> result = queryFactory
      .select(new QMemberDto(member.username, member.age))
      .from(member)
      .fetch();
    ```
  - 마지막 방법인 `생성자 + @QueryProjection` 방식이 컴파일 시점에 타입 체크를 할 수 있는 가장 안전한 방법이다.
    - 그 외 방법은 컴파일 시점에 오류를 발견하지 못할 수도 있다.
      - Ex. 생성자가 userName과 age만 받는데, QueryDSL 문법에서 가령 파라미터를 하나 더 넣을 경우, 런타임 시점에 오류 발생
    - 하지만 DTO에 어노테이션이 사용되기 때문에 QueryDSL이라는 기술에 종속된다.

### 동적 쿼리
- 동적 쿼리를 해결하는 방식은 크게 두가지가 있다.
  - BooleanBuilder
  - Where 다중 파라미터 사용
- BooleanBuilder
  - ```
    BooleanBuilder builder = new BooleanBuilder();
    
    if (usernameCond != null) {
      builder.and(member.username.eq(usernameCond));
    }
    
    if (ageCond != null) {
      builder.and(member.age.eq(ageCond));
    }
    
    return queryFactory
      .selectFrom(member)
      .where(builder)
      .fetch();
    ```
- Where 다중 파라미터 사용
  - ```
    return queryFactory
      .selectFrom(member)
      .where(usernameEq(usernameCond), ageEq(ageCond))
      .fetch();
    
    private BooleanExpression usernameEq(String usernameCond) {
      return usernameCond != null ? member.username.eq(usernameCond) : null;
    }
    
    private BooleanExpression ageEq(Integer ageCond) {
      return ageCond != null ? member.age.eq(ageCond) : null;
    }
    ```
  - 특징 및 장점
    - where 조건에 null 값은 무시된다.
    - 메서드를 다른 쿼리에서도 재활용 할 수 있다.
    - 쿼리 자체의 가독성이 높아진다.

### 수정, 삭제 벌크 연산
- ```
  queryFactory
    .update(member)
    .set(member.username, "비회원")
    .where(member.age.lt(28))
    .execute();
  
  queryFactory
    .delete(member)
    .where(member.age.gt(18))
    .execute();
  ```
- 주의사항
  - JPQL 배치와 마찬가지로 영속성 컨텍스트에 있는 엔티티를 무시하고 실행되기 때문에 배치 쿼리를 실행하고 나면 영속성 컨텍스트를 초기화 하는 것이 안전하다.

### SQL function 호출
- SQL function은 JPA와 같이 Dialect에 등록된 내용만 호출할 수 있다.
- ```
  String result = queryFactory
    .select(Expressions.stringTemplate("function('replace', {0}, {1}, {2})", member.username, "member", "M"))
    .from(member)
    .fetchFirst();
  ```

### CountQuery 최적화
- PageableExecutionUtils.getPage() 메서드를 사용하면, 카운트 쿼리를 최적화할 수 있다.
  - count 쿼리가 생략 가능한 경우 생략해서 처리
    - 페이지 시작이면서 컨텐츠 사이즈가 페이지 사이즈보다 작을 때
    - 마지막 페이지이면서 컨텐츠 사이즈가 페이지 사이즈보다 작을 때
- 사용예시
  - ```
    JPAQuery<Member> countQuery = queryFactory
      .select(member)
      .from(member)
      .leftJoin(member.team, team)
      .where(
             usernameEq(condition.getUsername()), 
             teamNameEq(condition.getTeamName()),
             ageGoe(condition.getAgeGoe()),
             ageLoe(condition.getAgeLoe())
      );
    
    // 보통의 pagination 적용
    // return new PageImpl<>(content, pageable, total);
    
    // 카운트 쿼리 최적화
    return PageableExecutionUtils.getPage(content, pageable, countQuery::fetchCount);
    ```
    
### QuerydslPredicateExecutor
- QuerydslPredicateExecutor 란?
  - Spring Data JPA에서 제공하는 인터페이스로, QueryDSL을 활용한 동적 쿼리 실행을 쉽게 할 수 있도록 지원하는 기능을 한다.
  - 이를 사용하면 `Predicate 객체를 기반으로 동적으로 쿼리를 작성하고 실행`할 수 있다.
    - ```
      public interface QuerydslPredicateExecutor<T> {
        Optional<T> findById(Predicate predicate);
        Iterable<T> findAll(Predicate predicate);
        long count(Predicate predicate);
        boolean exists(Predicate predicate);
        // … more functionality omitted.
      }
      ```
- 적용
  - ```
    interface MemberRepository extends JpaRepository<User, Long>, QuerydslPredicateExecutor<User> {
    }
    ```
- 한계점
  - 조인X (묵시적 조인은 가능하지만 left join이 불가능하다.)
  - 클라이언트가 Querydsl에 의존해야하며, 서비스 클래스가 Querydsl이라는 구현 기술에 의존해야 한다.
    - JpaRepository까지 Predicate를 넘겨야하기 때문
  - 복잡한 실무환경에서 사용하기에는 한계가 명확하다.

### QuerydslRepositorySupport
- QuerydslRepositorySupport 란?
  - Spring Data JPA에서 QueryDSL을 편리하게 사용할 수 있도록 도와주는 유틸리티 클래스이다.
  - QuerydslPredicateExecutor가 제공하는 기능이 제한적인 반면, QuerydslRepositorySupport는 복잡한 쿼리(조인, 서브쿼리, 그룹핑 등)를 보다 쉽게 작성할 수 있도록 도와준다.
- 한계점
  - Querydsl 3.x 버전을 대상으로 만듬
  - Querydsl 4.x에 나온 JPAQueryFactory로 시작할 수 없음
    - select로 시작할 수 없음 (from으로 시작해야함)
  - `QueryFactory` 를 제공하지 않음
  - 스프링 데이터 Sort 기능이 정상 동작하지 않음

### Querydsl 지원 클래스 직접 생성
- 스프링 데이터가 제공하는 `QuerydslRepositorySupport` 가 지닌 한계를 극복하기 위해 직접 Querydsl 지원 클래스를 만들 수 있다.
  - 소스코드 내 Querydsl4RepositorySupport.java 참고