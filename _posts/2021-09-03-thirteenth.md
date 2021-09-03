---
title: "JDK, JRE, JVM"
layout: single
categories:
  - Blog
tags:
  - java
  - JDK
  - JRE
  - JVM
---

## [ JDK, JRE, JVM ]

## JDK(Java Development Kit)

JDK = JRE + 개발툴(ex. apt, appletviewer, javac, jar, jdb)

- javac : java 코드를 컴파일. Java 코드를 byte 코드로 컴파일.
- apt : 어노테이션 툴
- appletviewer : 웹브라우저 없이 자바 애플릿을 실행하고 디버깅하기 위한 툴
- javac : 자바 컴파일러. 자바 소스파일을 바이트코드로 변환
- java : javac가 만든 클래스 파일을 해석 및 실행
- jar : 서로 관련있는 클래스 라이브러리들과 리소스를 하나의 파일로 묶어주는 툴
- jdb : 자바 디버깅 툴

### JDK의 특징

- JDK(Java Development Kit)이 바로 우리가 java라고 일컫는 것이다. JDK는 JVM과 JRE를 포함한다. JDK안에는 JRE를 포함하고 있고, JRE는 JVM을 포함하고 있기 때문에 JDK를 설치하면 JRE와 JVM이 같이 설치되는 것이다.
- 그렇다면 JRE와 JDK는 어떠한 차이가 있는가? JDK에는 JRE에 없는 자바 컴파일러(JAVAC: Java Compiler)가 포함 되어있다. 따라서 자바를 실행만 하고자 한다면 JRE만 있어도 되지만, 자바를 개발하고자 한다면 JDK가 필요한 것이다.
- 상기와 같은 내용이라면, 자바로 구성된 프로그램을 실행하려면 모두가 JDK를 설치해야 한다. 그러나 실제는 그렇지 않다. 자바로 프로그램을 개발하려고 하는 자는 JDK를 설치하여 환경을 구성하고 개발하여야 하지만 실행만 하고자 하는 자는 JRE만 설치한다면 실행만 하는것이 가능하다.

### JDK의 종류

1. Java SE(Standard Edition)

     Java가 어떠한 문법적인 구성을 가졌는지와 같은 것들을 나타내는 명세표

    네트워킹,보안,그래픽 사용자 인터페이스 개발,XML파싱,데이터베이스 등을 지원

2. Java EE(Enterprise Edition)

    Java SE + 서버에서 동작하는 기능추가적으로 웹프로그래밍에 필요한 JSP, Servlet, JDBC 등의 기능을 제공

3. Java ME(Micro Edition)

    Java SE + 휴대전화,PDA에서 java 프로그래밍 지원

## JRE(Java Runtime Enviroment)

JRE = JVM + Java Class Library

Java Class Library : 런타임시 클래스 로딩이 발생하는데, 그때 참조하는 class들이 모여있는 도서관.

### JRE 특징

- JRE(Java Runtime Enviroment)는 JVM이 원활하게 작동할 수 있도록 환경을 맞추어 주는 역할을 한다. JRE에는 JVM과 자바 클래스 라이브러리(Java Class Libraries) 그리고 자바 클래스 로더(Java Class Loader)를 포함한다.
- JRE는 자바 클래스 라이브러리와 자바 클래스 로더를 결합하고, JVM에게 제공하여 JVM을 작동한다. JRE는 단어 그대로 JVM이 실행할 수 있는 환경을 의미한다.

## JVM(Java Virtual Machine)

다른 언어는 OS의 종류에 따라, CPU아키텍처에 따라 동작을 안한다. 즉, 컴파일한 환경과 그 프로그램을 실제 동작시킬 환경이랑 다를때 동작을 안할 수도 있다. 따라서 컴파일 된 코드를 어디서나 실행 될 수 있도록 하는 것이 JVM이다.

![Untitled](https://user-images.githubusercontent.com/26619776/132022714-65ee4817-9625-46ed-9b90-f228b100f90a.png)

### JVM의 구성요소

JVM은 크게 Class Loader, Execution Engine, Runtime Data Areas로 나누어져 있다.

- Class Loader Subsystem – 로드, 링크 및 초기화 담당, 동적 클래스 로드라고도 함
- Runtime Data Areas – method areas, PC registers, stack areas, threads.
- Execution Engine – interpreter, compiler , garbage collection area.

### JVM의 특징

- JVM은 자바 가상머신이다. 자바로 작성된 코드를 실행할 수 있도록 도와주는 가상의 머신이라고 생각하면 된다. 자바로 코딩된 파일은 .class라는 바이너리 파일로 컴파일 되어 실행되는데 이것을 도와주는 일종의 툴이다.
- 자바는 가상환경에서 실행되는 것이기 때문에 윈도우 뿐만 아니라 다른 운영체제 리눅스, 맥, 심지어 기계에서도 실행이 가능하다.

### 가비지 컬렉션(Garbage Collection)

- 가비지 컬렉터(Garbage Collector), JVM내에서 메모리를 관리하는 프로세스를 지칭하는 용어이다. 자바 프로그램상에서 사용하지 않는 메모리를 지속적으로 찾아 제거함으로서 효율적인 메모리 관리를 가능하게 한다.
- 가령 선언하고 사용하지 않는 변수, 불필요하게 정의된 메소드 등 프로그램 내에서 메모리를 사용하였지만 활용되지 않는 요소들을 찾아서 제거하는 역할을 하고 있다. 기존의 타 언어(C ..)는 메모리를 직접 관리하여야 했지만, 자바에서는 가비지 컬렉터와 같은 것으로 메모리를 자동으로 관리해주기 때문에 효율적이다.
