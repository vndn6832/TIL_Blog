---
title: "Java 접근 제한자"
layout: single
categories:
  - Blog
tags:
  - java
  - public
  - protected
  - default
  - private
---

## [ Java 접근 제한자 ]

public → protected → default → private

⇒ 순서로 접근할 수 있는 범위가 줄어듦.


> Public

접근 범위가 가장 큰 접근 제한자로 클래스, 패키지에 상관없이 무조건 접근이 가능하다.


> Protected

같은 패키지에서만 접근이 가능하며, 다른 패키지에서는 접근할 수 없다.

다만, 다른 패키지의 클래스를 상속받을 시에는 접근이 가능하다.


> Defalut

같은 패키지에서만 접근이 가능하며 다른 패키지에서는 접근할 수 없다.

default는 접근 제한자가 생략되어 있을 경우 적용된다. 이것은 약속이기 때문에 멤버나 클래스에 앞에 default 접근 제한자를 붙여서는 안 된다.


> Private

같은 클래스 내에서만 접근할 수 있다. 같은 패키지여도 접근이 불가능하다.

보통 private으로 해당 멤버에 직접적인 접근을 막으며, 접근하기 위해서 getter, setter 메서드를 사용한다.


### "어떠한 곳에서 사용할 수 있을까?"


> 클래스(Class)

클래스는 기본적으로 public과 default만 사용이 가능하다

```java
public class A {} //public (O)

class B {} //default (O)
```

하지만, 클래스 내부에 선언하는 Inner  Class의 경우 protected와 private 접근 제한자를 사용할 수 있다.

```java
class A {
	public class B {}
	class C {}
	protected class D {}
	private class F {}
}
```


> 생성자(Construtor)

생성자에는 모든 접근 제한자를 사용할 수 있다.

```java
class A {
	public A() {};
	A(int a) {};
	protected A(String a) {};
	private A(int a, String b) {};
}
```


> 멤버 변수(Member Variable)

멤버 변수도 마찬가지로 모든 접근 제한자를 사용할 수 있다.

```java
class A {
	public int a;
	int b;
	protected int c;
	private int d;
}
```


> 멤버 메서드(Member Method)

멤버 메서드 역시 모든 접근 제한자를 사용할 수 있다.

```java
class A {
	public void a() {};
	void b() {};
	protected void c() {};
	private void d() {};
}
```


> 지역 변수(Local Variable)

지역 변수에는 접근 제한자를 사용할 수 없다.

```java
class A {
	public void localVariable(){} {
		int a;
		public int b; //(X)
		private int c; //(X)
		protected int d; //(X)
	}
}
```

