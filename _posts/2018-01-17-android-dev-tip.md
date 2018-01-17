---
published: true
layout: post
date: '2018-01-17 15:32 +0900'
postname: '[TIP] 안드로이드 개발 中 디자인 & 성능 TIP'
categories: android
tags: design performance tip
---
## 서론			

> 단순히 코딩하기 보다는 개발의 원칙을 가지고 해야지, 중심을 잃지 않을 수 있다.

## 성능을 위해 코딩 중에 고려하면 좋은 TIP들

1. 불필요한 객체생성을 피하기

> 불필요한 객체생성은 메모리 낭비를 가져오고 GC 작업으로 인해 성능에 악영향을 미친다.

2. Virtual Method보다는 Static Method를 이용하라

3. 상수에는 static final 키워드를 사용하라

> 그렇지 않으면 컴파일러는 매번 검색테이블을 거치는 cost를 지불해야 한다.

4. 클래스 내부에서의 Getter/Setter를 피하라.

> 일반적인 OOP 네이티브 언어(C++,JAVA) 등은 멤버필드의 Getter/Setter를 지향하며, 클래스 네부에서도 사용하기를 권장한다. 그러나 안드로이드는 컴파일러 동작이 다르므로, 클래스 외부에서 get,set를 이용해도 좋지만, 내부에서는 get,set를 피하자.

5. 향상된 For 문을 이용하자

```java
static class Foo {
    int mSplat;
}

Foo[] mArray = ...

public void zero() {
    int sum = 0;
    for (int i = 0; i < mArray.length; ++i) { //매번 length에 접근해야 하므로 느리다.
        sum += mArray[i].mSplat;
    }
}

public void one() {
    int sum = 0;
    Foo[] localArray = mArray;
    int len = localArray.length;

    for (int i = 0; i < len; ++i) {
        sum += localArray[i].mSplat;
    }
}

public void two() {
    int sum = 0;
    for (Foo a : mArray) { //가장 빠르다.
        sum += a.mSplat;
    }
}

```
6. Private Inner 클래스에서의 Private 멤버/메서드 접근은 가급적 피하라

7. 부동소수점 사용을 피하라

> 정수 연산보다는 두배 정도 느리다,

8. System Library를 잘 알고 사용하자.

> 유저가 직접 구현한 것보다 빠르고, 최적화가 잘되있다.



## 디자인시 간과하기 어려운 부분들

1. 너무 많은 베터리 전력을 소모함

2. 다른 화면 크기에서 테스트하는 것을 잊어버림

3. 비동기식 디자인을 사용하지 않음(항상 사용자가 인터넷에 연결된다고 추측x)

## 개발자를 위한 조언

1. 사용자 보안을 최우선 순위로 삼으라.

2. XML과 JAVA를 배우라

> 안드로이드 플랫폼은 XML 기반 UI와 JAVA의 백엔드 코드로 이루어 진다.두개의 언어를 마스터하는 것이 좋다.

3. 메모리를 염두하라.
