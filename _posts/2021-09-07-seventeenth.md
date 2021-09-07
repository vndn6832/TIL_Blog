---
title: "ACID"
layout: single
categories:
  - Blog
tags:
  - db
  - atomicity
  - consistency
  - isolation
  - durability
---

## [ ACID ]

데이터베이스의 트랜잭션이 중간에 실패가 나거나 예기치 못한 상황이 발생해도 데이터를 유효한 상태를 보장하기 위해서 만족해야하는 조건들이다.

- **A**tomicity : 원자성, 트랜잭션은 성공 or 실패다. 부분 성공은 없다.
- **C**onsistency : 일관성, 실행을 성공적으로 완료하면 언제나 일관된 DB 상태로 된다.
- **I**solation : 격리성, 트랜잭션 실행 중에 다른 트랜잭션이나 작업이 접근할 수 없다.
- **D**urability : 영속성, 실행을 성공적으로 끝내면 그 결과를 어떠한 경우에도 보장 받는다는 의미

중간에 시스템 문제(전력 차단등)로 인해 로그가 유실된다거나 하는 문제가 없어야 한다. 비휘발성 메모리에 커밋된 로그를 보존하는 방식이 될 수 있다.
