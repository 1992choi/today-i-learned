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