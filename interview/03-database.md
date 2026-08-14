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
  - 트랜잭션을 제어하는 명령인 COMMIT, ROLLBACK, SAVEPOINT를 따로 분리해서 TCL이라고 표현하고 있다.
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
    - 다른 릴레이션의 기본키 또는 유니크(UNIQUE) 제약이 걸린 속성을 참조하는 속성의 집합
    - 외래키는 참조되는 릴레이션의 기본키(또는 유니크 키)와 대응되어 릴레이션 간에 참조 관계를 표현하는데 중요한 도구로 사용된다.
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
  - 이상 현상은 정규화(Normalization)를 통해 방지할 수 있다.
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
  - 삽입, 삭제, 갱신 이상이 있는 관계를 재구성함으로써 바람직한 스키마를 만들 수 있다.
- 정규화의 종류
  - 1NF
    - 모든 도메인이 원자값으로만 구성된다.
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/505be8f8-f9ed-4f8c-9e02-2a20d42e7547)
  - 2NF
    - 기본키가 아닌 모든 속성이 기본키에 대하여 완전 함수적 종속을 만족한다.
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/8f19a508-0b6e-4746-a161-9036157582de)
  - 3NF
    - 후보키를 제외한 속성들 간에 이행 종속성이 없다.
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/5d66af2e-fd92-41b9-831c-95b319523b41)
  - BCNF
    - 모든 결정자가 후보키일 때, 결정자이면서 후보키가 아닌 것을 제거한다.
    - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/5953a132-4eac-48a4-b951-a19a50091c73)
  - 4NF
    - 다치 종속을 제거한다.
  - 5NF
    - 모든 조인 종속이 후보키를 통해서만 성립한다. 
- Ref.
[star가 되고나서](https://star7sss.tistory.com/822),
[goodGid](https://goodgid.github.io/DB-Normalization%281%29/)
<br><br><br>



## 반정규화(Denormalization)
- 반정규화란?
  - 정규화된 데이터베이스는 데이터 중복을 최소화하고 무결성을 보장하지만, 그만큼 여러 테이블을 JOIN해야 하는 경우가 많아져 조회 성능이 저하될 수 있다.
  - 반정규화는 이러한 조회 성능을 향상시키기 위해, 의도적으로 데이터의 중복을 허용하거나 테이블을 통합/분리하는 것을 뜻한다.
- 정규화와 반정규화의 관계
  - 정규화는 데이터 무결성과 중복 최소화(쓰기 최적화)를, 반정규화는 조회 성능과 개발 편의성(읽기 최적화)을 목적으로 하는 서로 반대되는 방향의 작업이다.
  - 무조건 반정규화가 좋은 것은 아니며, 조회 성능과 데이터 정합성 사이의 트레이드오프를 고려하여 신중하게 적용해야 한다.
- 반정규화 방법
  - 테이블 병합 : 자주 함께 조회되는 테이블을 하나로 합쳐 JOIN을 줄인다.
  - 중복 컬럼 추가 : 자주 JOIN해서 가져오는 컬럼을 참조 테이블에도 중복 저장한다.
  - 파생(계산) 컬럼 추가 : 매번 집계 연산을 하는 대신, 계산된 결과값을 컬럼으로 저장해둔다. (Ex. 게시글의 댓글 수, 주문의 총 금액)
  - 요약 테이블 추가 : 통계성 데이터를 미리 집계해서 별도의 테이블로 관리한다.
- 장점
  - JOIN 횟수와 연산량이 줄어들어 조회 성능이 향상된다.
  - 조회 쿼리가 단순해져 개발 및 유지보수가 쉬워지는 경우가 있다.
- 단점
  - 데이터가 여러 곳에 중복 저장되므로, 값을 변경할 때 모든 곳을 함께 갱신해야 하는 갱신 이상(Update Anomaly)이 발생할 수 있다.
  - 중복 데이터로 인해 저장 공간을 더 많이 차지한다.
  - 데이터 정합성을 유지하기 위한 추가적인 로직(트랜잭션, 배치 등)이 필요해 복잡도가 올라간다.
- Ref.
<br><br><br>



## JOIN
- JOIN이란?
  - 두 개 이상의 테이블이나 데이터베이스를 연결하여 데이터를 검색하는 행위를 뜻한다.
  - 일반적으로 Primary key 혹은 Foreign key로 두 테이블을 연결한다.
  - 연결하려면 적어도 하나의 칼럼은 서로 공유되고 있어야 한다.
- JOIN의 종류
  - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/13aba6a1-b866-4772-a747-82c49d5e1b07)
  - INNER JOIN
    - 조인 조건이 일치하는 행(교집합)만 반환한다.
    - Ex) `SELECT * FROM A INNER JOIN B ON A.id = B.a_id`
  - LEFT / RIGHT OUTER JOIN
    - 기준이 되는 한쪽 테이블의 모든 행 + 교집합을 반환하며, 매칭되지 않는 반대편 테이블의 컬럼은 NULL로 채워진다.
    - Ex) `SELECT * FROM A LEFT JOIN B ON A.id = B.a_id`
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
  - 데이터베이스의 상태를 변화시키기 위해서 수행하는 작업의 단위를 뜻한다.
- 트랜잭션 특징
  - 원자성(Atomicity)
    - 트랜잭션이 데이터베이스에 모두 반영되던가, 아니면 전혀 반영되지 않아야 한다.
  - 일관성(Consistency)
    - 트랜잭션의 작업 처리 결과가 항상 일관성이 있어야 한다.
  - 독립성(Isolation)
    - 각각의 트랜잭션은 서로 간섭없이 독립적으로 수행되어야 한다.
  - 지속성(Durability)
    - 트랜잭션이 성공적으로 완료되었을 경우, 결과는 영구적으로 반영되어야 한다.
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
    - 대부분의 DBMS가 기본 모드로 채택하고 있는 격리수준이다. (단, MySQL(InnoDB)은 REPEATABLE READ를 기본 격리수준으로 채택하고 있다.)
    - Non-Repeatable Read, Phantom Read 현상이 발생할 수 있다.
  - 레벨 2 (Repeatable Read)
    - 선행 트랜잭션이 읽은 데이터는 트랜잭션이 종료될 때까지 후행 트랜잭션이 갱신하거나 삭제하는 것은 불허함으로써 같은 데이터를 두 번 쿼리했을 때 일관성 있는 결과를 리턴한다.
    - Phantom Read 현상이 발생할 수 있다. (단, MySQL InnoDB는 MVCC와 Next-Key Lock을 통해 대부분의 경우 Phantom Read를 방지한다.)
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
    - 전반적인 시스템의 부하를 줄일 수 있다.
  - 단점
    - 인덱스를 관리하기 위해 DB의 약 10%에 해당하는 저장공간이 필요하다.
    - 인덱스를 관리하기 위해 추가 작업이 필요하다.
    - 인덱스를 잘못 사용하는 경우, 오히려 성능이 저하될 수 있다.
- Index의 자료구조
  - 인덱스를 구현하기 위해서는 다양한 자료구조를 사용할 수 있는데, 가장 대표적으로는 해시 테이블, B-Tree, B+Tree가 존재한다.
    - 해시 테이블(Hash table)
      - 해시 테이블은 키(Key)와 해시 값(Hash Value) 쌍으로 이루어진 자료구조이다.
      - O(1)의 시간복잡도를 가지고 있어 상당히 빠른 검색을 할 수 있는 것이 특징이다.
      - 해시 테이블은 검색 속도가 매우 빠르지만, 데이터의 분포에 따라 충돌이 발생할 수 있다.
      - 해시는 등호(=) 연산에만 특화되어 있어 부등호 연산(>, <)이 자주 사용되는 데이터베이스 검색을 위해서는 해시 테이블이 적합하지 않다.
    - B-Tree
      - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/031b6ec4-396b-4948-8443-84e19cfe5c64)
      - B-Tree는 데이터베이스에서 가장 널리 사용되는 인덱스 자료구조 중 하나이다.
      - O(logN)의 시간 복잡도를 가지고 있다.
      - 이진 트리와는 다르게 하나의 노드에 많은 정보를 가지거나, 두 개 이상의 자식을 가질 수도 있다.
      - B-Tree의 각 노드 내 데이터들은 항상 정렬된 상태인 것이 특징이며, 데이터와 데이터 사이의 범위를 이용하여 자식 노드를 가진다.
      - B-Tree의 경우, 키 값과 데이터 값이 노드 안에 함께 저장되기 때문에 노드 크기가 크고, 디스크 I/O 작업이 많아지는 문제가 있기 때문에 B+Tree 구조를 더 많이 사용한다.
    - B+Tree
      - ![image](https://github.com/1992choi/today-i-learned/assets/27760576/2b18df86-d42c-4e07-a83b-b493d301557c)
      - B+Tree는 B-Tree의 변형된 구조이다.
      - B-Tree는 내부 노드와 리프 노드가 모두 데이터를 가지는 반면에 B+Tree는 리프 노드만 데이터를 가지기 때문에 더 적은 I/O 작업을 필요로 한다.
      - B-Tree와 B+Tree 모두 O(log n)의 시간복잡도를 가지지만, B+Tree가 더 작은 크기의 노드들을 읽어나가기 때문에 리프 노드에 더 빨리 도착할 수 있다.
      - B-Tree는 탐색을 위해서 노드를 찾아서 이동해야 한다는 단점을 가지고 있는데, B+Tree는 이러한 단점을 해소하고자 같은 레벨의 모든 키값들이 정렬되어 있고, 같은 레벨의 Sibling node는 연결 리스트 형태로 이어져 있다. 또한 이 자료들은 연결 리스트로 연결되어 있으므로 탐색에 유리하다.
- Ref.
[망나니개발자](https://mangkyu.tistory.com/96),
[IT is True](https://ittrue.tistory.com/331),
[dev.KwonTaeHyeong](https://velog.io/@kwontae1313/%EC%9D%B8%EB%8D%B1%EC%8A%A4Index%EC%97%90-%EB%8C%80%ED%95%B4%EC%84%9C-%EC%95%8C%EC%95%84%EB%B3%B4%EC%9E%90),
[간단히 알아보는 B-Tree, B+Tree, B*Tree](https://ssocoit.tistory.com/217)
<br><br><br>



## 클러스터형 인덱스와 넌클러스터형 인덱스
- 클러스터형 인덱스(Clustered Index)
  - 인덱스의 키 값에 따라 테이블의 데이터 자체가 물리적으로 정렬되어 저장되는 인덱스이다.
  - 인덱스의 리프 노드(Leaf Node)에 데이터 페이지 자체가 저장되어 있어, 인덱스를 찾으면 곧바로 데이터에 도달할 수 있다.
  - 데이터가 물리적으로 하나의 순서로만 정렬될 수 있으므로, 테이블당 1개만 생성할 수 있다.
  - MySQL InnoDB 기준으로 기본키(Primary Key)에 자동으로 생성되며, 기본키가 없으면 UNIQUE 컬럼, 그마저도 없으면 내부적으로 숨겨진 자동 증가 키를 기준으로 클러스터형 인덱스가 생성된다.
- 넌클러스터형 인덱스(Non-Clustered Index)
  - 인덱스와 실제 데이터의 물리적인 저장 순서가 무관한 인덱스이다.
  - 리프 노드에 데이터 자체가 아니라, 데이터의 위치를 가리키는 포인터(또는 클러스터형 인덱스의 키 값)가 저장된다.
  - 한 테이블에 여러 개 생성할 수 있다.
- MySQL InnoDB에서의 동작 방식
  - InnoDB는 PK를 기준으로 한 클러스터형 인덱스(=IOT, Index-Organized Table) 구조를 사용한다.
  - 세컨더리(넌클러스터형) 인덱스의 리프 노드에는 데이터 위치 대신 PK 값이 저장되기 때문에, 세컨더리 인덱스로 조회할 경우 먼저 세컨더리 인덱스에서 PK를 찾은 뒤, 그 PK로 클러스터형 인덱스를 다시 조회하는 과정(2번의 탐색)이 필요할 수 있다. 이를 흔히 '북마크 룩업(Bookmark Lookup)'이라 부른다.
- 장단점 비교
  - 클러스터형 인덱스
    - 장점 : 데이터 접근 시 추가적인 조회 과정 없이 곧바로 데이터에 도달할 수 있어 조회 성능이 좋다. 특히 범위(Range) 검색에 유리하다.
    - 단점 : 데이터 삽입/수정 시 정렬 순서를 유지해야 하므로 페이지 분할(Page Split) 등의 추가 비용이 발생할 수 있으며, 테이블당 1개만 생성 가능하다.
  - 넌클러스터형 인덱스
    - 장점 : 여러 개를 자유롭게 생성할 수 있어 다양한 조회 조건에 대응하기 유리하다.
    - 단점 : 리프 노드에서 실제 데이터로 한 번 더 접근해야 하므로(북마크 룩업), 클러스터형 인덱스보다 조회 성능이 상대적으로 낮을 수 있다.
- Ref.
<br><br><br>



## 커버링 인덱스(Covering Index)
- 커버링 인덱스란?
  - 쿼리를 처리하는 데 필요한 모든 컬럼(SELECT, WHERE, ORDER BY, GROUP BY 절에서 사용되는 컬럼)이 인덱스 자체에 포함되어 있어서, 실제 데이터 페이지에 접근하지 않고 인덱스만으로 쿼리 결과를 반환할 수 있는 경우를 뜻한다.
  - 인덱스만으로 처리가 끝나기 때문에, 앞서 설명한 넌클러스터형 인덱스의 북마크 룩업(추가 데이터 조회) 과정을 생략할 수 있다.
- 예시
  - `user` 테이블에 `(name, age)` 복합 인덱스가 있다고 가정할 때, 다음 쿼리는 인덱스에 포함된 컬럼만으로 결과를 만들 수 있어 커버링 인덱스로 동작한다.
    - `SELECT name, age FROM user WHERE name = 'choi'`
  - 반면 `SELECT name, age, email FROM user WHERE name = 'choi'`처럼 인덱스에 없는 `email` 컬럼을 조회하면, 커버링 인덱스가 아니게 되어 실제 데이터 페이지 조회가 추가로 발생한다.
- 장점
  - 데이터 페이지에 접근하는 디스크 I/O가 줄어들어 쿼리 성능이 향상된다.
  - 인덱스는 일반적으로 전체 데이터보다 크기가 작기 때문에, 메모리(버퍼 풀)에 캐싱되어 있을 가능성이 높아 성능상 이점이 크다.
- 단점
  - 커버링 인덱스를 만들기 위해 인덱스에 포함하는 컬럼 수가 늘어나면, 인덱스 자체의 크기가 커지고 저장 공간을 더 많이 차지한다.
  - 인덱스 컬럼이 많아질수록 데이터 삽입/수정/삭제 시 인덱스를 갱신하는 비용(쓰기 성능 저하)도 함께 증가한다.
- Ref.
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
  - '파티셔닝(Partitioning)' 기법을 통해 소프트웨어적으로 데이터베이스를 분산 처리하여 성능이 저하되는 것을 방지하고 관리를 보다 수월하게 할 수 있게 되었다.
- 파티셔닝의 목적
  - 성능(Performance)
    - 특정 DML과 Query의 성능을 향상시킨다.
    - 주로 대용량 Data WRITE 환경에서 효율적이다.
    - 특히, Full Scan에서 데이터 Access의 범위를 줄여 성능 향상을 가져온다.
  - 가용성(Availability)
    - 물리적인 파티셔닝으로 인해 전체 데이터의 훼손 가능성이 줄어들고 데이터 가용성이 향상된다.
    - 각 분할 영역(partition)별로 독립적으로 백업하고 복구할 수 있다.
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
    - 테이블의 일부 열을 빼내는 형태로 분할한다. 정규화도 수직 파티셔닝과 관련된 과정이라고 할 수 있다.
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
  - Shared Lock(공유락, Read Lock)
    - 공유락은 데이터를 읽을 때 사용하는 Lock이다.
    - Read Lock 끼리는 데이터의 일관성과 무결성을 해치지 않기 때문에 동시에 접근이 가능하다.
    - 만약 특정 데이터에 Shared Lock 이 걸려있다면, 아래 Exclusive Lock을 걸 수 없고, 여러 Shared Lock은 동시에 적용될 수 있다.
  - Exclusive Lock(배타락, Write Lock)
    - 배타락은 데이터를 변경할 때 사용하는 Lock이다.
    - 하나의 트랜잭션이 완료될 때까지 유지되며, 배타락이 끝날 때까지 어떠한 접근도 허용되지 않는다.
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
    - 테이블을 제어하는 DDL 구문을 사용할 때 Lock이 걸린다고 하여, DDL Lock 이라고도 한다.
  - Database Level
    - Database의 복구나 스키마 변경 시 락을 설정한다.
    - 1개의 세션이 하나의 Database의 데이터에 접근할 수 있다.
    - DB 전체에 영향이 있는 DB 업데이트와 같은 작업에만 사용한다.
  - Column Level
    - 컬럼 기준으로 Lock이 걸린다.
    - Lock 설정 및 해제에 리소스가 많이 들어 잘 사용하지 않는다.
- 블로킹(Blocking)
  - Lock 간의 경합(Race Condition)이 발생하여 특정 Transaction이 작업을 진행하지 못하고 멈춰선 상태를 말한다.
  - 공유락끼리는 블로킹이 발생하지 않지만, 배타락은 블로킹을 발생시킨다.
  - (Shared Lock + Exclusive Lock) 또는 (Exclusive Lock + Exclusive Lock) 끼리 블로킹이 발생할 수 있다.
  - 해결방안
    - SQL문이 빠르게 수행될 수 있도록 리팩토링한다.
    - 트랜잭션을 가능한 짧게 정의하여 경합을 줄인다.
    - 동일한 데이터를 동시에 변경하지 않도록 설계한다.
    - LOCK_TIMEOUT을 설정하여 해당 Lock의 최대시간을 조정한다.
- 교착상태(DeadLock)
  - 교착상태는 두 트랜잭션이 각각 Lock을 설정하고 서로의 Lock에 접근하여 값을 얻어오려고 할 때, 이미 각각의 트랜잭션에 의해 Lock이 설정되어 있기 때문에 양쪽 트랜잭션 모두 영원히 처리가 되지 않게 되는 상태를 뜻한다.
  - 발생상황
    - Shared Lock + Exclusive Lock
      - 트랜잭션 A가 Shared Lock을 설정하고 sleep 되었을 때, 트랜잭션 B가 해당 데이터에 Exclusive Lock을 걸려고 하면 무기한 기다려야 하는 교착상태에 빠진다.
    - Exclusive Lock + Exclusive Lock
      - 트랜잭션 A에서 Exclusive Lock을 걸었을 때 트랜잭션 B에서도 다른 데이터에 Exclusive Lock을 걸었을 경우 서로의 Lock된 데이터에 접근하려고 할 때 기존의 Lock이 해제될 때까지 기다리게 된다.
  - 해결방안
    - Dead Lock이 감지되면 둘 중 하나의 트랜잭션을 강제 종료한다.
    - Dead Lock 방지를 위해 접근 순서를 동일하게 하는 것이 중요하다.
- Ref.
[NKLCWDT](https://github.com/NKLCWDT/cs/blob/main/Database/Lock.md),
[Hyun / Log](https://hstory0208.tistory.com/entry/%EB%9D%BDLock%EC%9D%B4%EB%9E%80-Lock%EC%9D%98-%EC%A2%85%EB%A5%98%EC%99%80-%EA%B5%90%EC%B0%A9%EC%83%81%ED%83%9CDeadLock)
<br><br><br>
