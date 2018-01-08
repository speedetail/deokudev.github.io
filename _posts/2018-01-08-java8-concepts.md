---
published: true
layout: post
date: '2018-01-08 16:38 +0900'
categories: java
postname: '[java] java version 정보'
tags: java8 info
---
## Java 언어

> 자바 언어 또한 계속해서 업데이트가 이루어지고 있는 상황이다.

> 현재는 Java 8이 사용되고 있고, 성능은 계속해서 좋아지고 있다.

## Java Version History

- Java5 (2004~2009)

- Java6 (2006~2013)

- Java7 (2011~ )

- Java8 (2014~ )

- Java9 (2016예정)

- Java10 (2018예정)

(http://en.wikipedia.org/wiki/Java_version_history)

## Java 8에 추가된 주요 기능

- Lambda expressions : Anonymous function인 람다로 코드 표현 가능

```java
// Before
Runnable oldRunner = new Runnable(){
	public void run(){
		System.out.println("I am running");
	}
};
 
// After
Runnable java8Runner = () -> {
	System.out.println("I am running");
};
```

- Optional : 값을 Optional<T>로 캡슐화함으로써 NullPointerException 방지
 
- Default Method : 인터페이스의 구현체를 인터페이스 자체에서 기본으로 제공 가능하다. (이전에는 구현 클래스에서 인터페이스를 구현했어야)

```java
public interface Sized {
	int size();
 
	default boolean isEmpty() {  // Default Method
		return size() == 0;
	}
}
```

- Stream : 기존 for문을 거쳐야 했던 것을 벗어나,  간결하게 Collection의 데이터를 처리하는 기능

```java
// Before 
List<Shape> list = new ArrayList<Shape>();
for (Shape s : shapes) {
	if (s.getColor() == RED) {
		list.add(s);
	}
}
 
// After
shapes.stream().filter(s -> s.getColor() == Red).collect(toList());
```

- New date/time API : 기존 joda-Time의 기능을 java.time 패키지로 추가됨

```java
LocalDate, LocalTime
```