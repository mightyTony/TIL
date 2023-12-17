
*`EntityManager` 로 `JPAQueryFactory` 생성*

```java
    JPAQueryFactory queryFactory = new JPAQueryFactory(em);

    
```

**Q클래스 인스턴스를 사용하는 2가지 방법**
```java
QMember qMember = new QMember("m"); //별칭 직접 지정 QMember qMember = QMember.member; //기본 인스턴스 사용

Querydsl은 JPQL 빌더
JPQL: 문자(실행 시점 오류), Querydsl: 코드(컴파일 시점 오류) JPQL: 파라미터 바인딩 직접, Querydsl: 파라미터 바인딩 자동 처리


## 결과 조회

- fetch() : 리스트 조회, 데이터 없으면 빈 리스트 반환
- fetchOne() : 단 건 조회
    - 결과가 없으면 : null
    - 결과가 둘 이상이면 : com.querydsl.core.NonUniqueResultException
- fetchFirst() : limit(1).fetchOne()
- fetchResults() : 페이징 정보 포함, total count 쿼리 추가 실행
- fetchCount() : count 쿼리로 변경해서 count 수 조회

```java
//List
List<Member> fetch = queryFactory
        .selectFrom(member)
.fetch();
//단 건
Member findMember1 = queryFactory
        .selectFrom(member)
        .fetchOne();
//처음 한 건 조회
Member findMember2 = queryFactory
        .selectFrom(member)
        .fetchFirst();
//페이징에서 사용
QueryResults<Member> results = queryFactory
        .selectFrom(member)
        .fetchResults();
 
```

