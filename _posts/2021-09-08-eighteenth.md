---
title: "JDBC, JPA/Hibernate, Mybatis의 차이"
layout: single
categories:
  - Blog
tags:
  - db
  - jdbc
  - jpa
  - hibernate
  - mybatis
---

## [ JDBC, JPA/Hibernate, Mybatis의 차이 ]

1. JDBC(Java Database Connectivity)

- JDBC는 DB에 접근할 수 있도록 Java에서 제공하는 API이다.
- 모든 Java의 Data Access 기술의 근간
- 즉, 모든 Persistence Framework는 내부적으로 JDBC API를 이용한다.
- JDBC는 데이터베이스에서 자료를 쿼리하거나 업데이트 하는 방법을 제공한다.

2.JPA( Java Persistent API)

- 자바 ORM 기술에 대한 API 표준 명세로, Java에서 제공하는 API이다.
    - 자바 플랫폼 SE와 자바 플랫폼 EE를 사용하는 응용프로그램에서 관계형 데이터 베이스의 관리를 표현하는 자바API이다.
    - 즉, JPA는 ORM을 사용하기 위한 표준 인터페이스를 모아둔 것이다.
    - 기존에 EJB에서 제공되던 엔터티 빈(Entity Bean)을 대체하는 기술이다.
- JPA 구성요소(세 가지)

    1) javax.persistence 패키지로 정의된 API 그 자체

    2) JPQL(Java Persistence Query Language)

    3) 객체/관계 메타데이터

- 사용자가 원하는 JPA 구현체를 선택해서 사용할 수 있다.
    - JPA의 대표적인 구현체로는 Hibernate, EclipseLink, DataNucleus, OpenJPA, TopLink Essentials 등이 있다.
    - 이 구현체들을 ORM Framework라고 부른다.

- Hibernate는 JPA의 구현체 중 하나이다.
- Hibernate가 SQL을 직접 사용하지 않는다고 해서 JDBC API를 사용하지 않는다는 것은 아니다.
    - Hibernate가 지원하는 메서드 내부에서는 JDBC API가 동작하고 있으며, 단지 개발자가 직접 SQL을 작성하지 않을 뿐이다.
- HQL(Hibernate Query Language)이라 불리는 매우 강력한 쿼리 언어를 포함하고 있다.
    - HQL은 SQL과 매우 비슷하며 추가적인 컨벤션을 정의할 수도 있다.
    - HQL은 완전히 객체 지향적이며 이로써 상속, 다형성, 관계등의 객체지향의 강점을 누릴 수 있다.
    - HQL 쿼리는 자바 클래스와 프로퍼티의 이름을 제외하고는 대소문자를 구분한다.
    - HQL은 쿼리 결과로 객체를 반환하며 프로그래머에 의해 생성되고 직접적으로 접근할 수 있다.
    - HQL은 SQL에서는 지원하지 않는 페이지네이션이나 동적 프로파일링과 같은 향상된 기능을 제공한다.
    - HQL은 여러 테이블을 작업할 때 명시적인 join을 요구하지 않는다.

- 장점
    - 객체지향적으로 데이터를 관리할 수 있기 때문에 비즈니스 로직에 집중할 수 있으며, 객체지향 개발이 가능하다.
    - 테이블 생성, 변경, 관리가 쉽다. (JPA를 잘 이해하고 있는 경우)
    - 로직을 쿼리에 집중하기 보다는 객체자체에 집중 할 수 있다.
    - 빠른 개발이 가능하다.

- 단점
    - 어렵다. (많은 내용이 감싸져 있기 때문에 알아야 할 것이 많다.)
    - 잘 이해하고 사용하지 않으면 데이터 손실이 있을 수 있다.(persistence context)
    - 성능상 문제가 있을 수 있다.(이 문제 또한 잘 이해해야 해결이 가능하다.)

3.Mybatis

- 개발자가 지정한 SQL, 저장 프로시저 그리고 몇 가지 고급 매핑을 지원하는 SQL Mapper이다.
- JDBC로 처리하는 상당 부분의 코드와 파라미터 설정 및 결과 매핑을 대신해준다.
    - 기존에 JDBC를 사용할 때는 DB와 관련된 여러 복잡한 설정(Connection)들을 다루어야 했지만 SQL Mapper 는 자바 객체를 실제 SQL문에 연결함으로써, 빠른 개발과 편리한 테스트 환경을 제공한다.
- 데이터베이스 record에 원시 타입과 Map 인터페이스 그리고 자바 POJO를 설정해서 매핑하기 위해 xml과 Annotation을 사용할 수 있다.
- MyBatis는 원래 Apache Foundation의 iBatis였으나, 생산성, 개발 프로세스, 커뮤니티 등의 이유로 Goolge Code로 이전되면서 이름이 바뀌었다.
    - iBatis와 바뀐 차이점은 아래와 같다.
    - JDK 1.5, Annotation
    - Dynatic SQL, XML Element

- 장점
    - SQL에 대한 모든 컨트롤을 하고자 할 때 매우 적합하다.
    - SQL 쿼리들이 매우 잘 최적화되어 있을 때에 유용하다.

- 단점
    - 애플리케이션과 데이터베이스 간의 설계에 대한 모든 조작을 하고자 할 때는 적합하지 않다.
    - 애플리케이션과 데이터베이스 간에 서로 잘 구조화되도록 많은 설정이 바뀌어야 하기 때문이다.
