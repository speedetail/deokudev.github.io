---
published: true
layout: post
date: '2018-03-02 15:44 +0900'
postname: '[공부] Chapter1.  Java 일반 개념'
categories: java
---
contents {:toc}

## JAVA 개발을 위한 최소한의 준비

> JDK(Java Development Kit) 설치 : www.oracle.com
> 환경 변수 등록 : 내컴퓨터 속성 + 고급 시스템 설정 + 환경변수 + 사용자 변수에 "Path라는 이름으로 bin폴더 경로 지정"
> 환경 변수를 등록하게 되면, 어느 Path 상태에서나, bin 폴더 내의 java 툴들을 실행시킬 수 있다.
> API 문서 참조하기 : http://docs.oracle.com/Javase/8/docs 

## JDK를 설치 하고 나면..

> JAVA로 작성된 프로그램을 컴파일하고, 실행할 수 있는 상황이 만들어짐
> C:\Program Files/Java/jdk 1.8.0/bin 내의 bin 폴더에 자바의 개발 및 실행에 필요한 여러가지 도구(프로그램)이 존재함
> 크게 `javac.exe : 자바 컴파일러` 와 `java.exe : 자바 런처`로 구성되어 있다.

> JAVA 컴파일러의 역할 : 
> **자바 컴파일러는 자바 가상머신이 이해할 수 있는 코드를 생성해 냅니다"**
> 즉 자바 컴파일러는 소스코드를 가상머신이 이해할 수 있는 JAVA BYTECode로 변환하는 역할을 수행한다.
> JAVA 런처의 역할 : 
> 자바 가상머신을 구동하고, 그 위에 자바 프로그램이 실행되도록 돕는 프로그램

## JAVA 소스의 구성

> JAVA 소스 파일의 확장자는 `.java`이다.
> JAVA 소스 파일을 컴파일 하게 되면 `.class`파일이 생성된다.

## 기본 프로그래밍 개념

> Compile이란? `실행을 위한 상태로의 변경` 이다.
> **일반적인 프로그램의 실행 구조**
> Program (or Process) : 명령어의 집합 
> Operating System : 하드웨어를 기반으로 동작, 프로그램을 실행시킴
> Hardware

> **JAVA 프로그램의 실행 구조**
> Program 
> `Java Virtual Machine`
> Operating System
> Hardware
> 운영체제는 자바 가상머신을 실행시키고, 자바 가상머신이 자바 프로그램을 실행시키는 구조로 동작한다.

## JAVA의 장점

> JVM이 운영체제마다 다르므로, 운영체제의 변경 없이 JVM을 운영체제마다 다르게 취함으로써, 소스 수정없이 다양한 운영체제에서 실행시킬 수 있다.
> **운영체제의 차이에서 오는 문제점은 신경 쓰지마, 내가 다 알아서 처리하니까**

## JAVA 프로그램의 골격과 구성

> 클래스, 메소드
> **자바는 중괄호를 이용해서 클래스와 메소드의 영역을 구분한다.**

## JAVA의 기본 출력 함수

> System.out.printIn("출력할 내용");

## JAVA의 주석 처리

> 주석의 의미 : 
> `컴파일의 대상에서 제외되는 문장`을 의미한다.

``java
/* ~ */
//
``

> 들여쓰기(indent) : 클래스 선언 이후 바로 들여쓰기 하고 코딩
