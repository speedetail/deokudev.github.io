---
published: true
layout: post
date: '2018-01-08 16:56 +0900'
postname: '[android] 안드로이드 개발 성능 Tip'
tags: programming tip
categories: android
---
## 안드로이드 개발시 성능 Tip

- 불필요한 객체 생성 피하라!
> *가능하다면* 복사보다는 객체 있는 것을 그대로 쓰는 게 할당을 줄인다.

- Static Method 사용을 권장한다!
> static method의 호출 속도가 20% 정도 더 빠르다고 한다.

- 상수에는 static final을 붙여라!
```java
static final int intVal = 12;
static final String strVal = "Hi";
```
> final을 붙여야만, dex 파일 내에 있는 static field initializer에 의해 자동으로 초기화된다고 한다.
> 기존에는 클래스가 처음 사용될 때, 초기화 메소드가 호출되고, 그 때 값이 초기화되므로, 그러므로 시간이 더 소요된다.

- Internal Getter/Setter 사용을 피하라!
> *가능하다면* 내부에서 필드 접근을 다이렉트로 하는 것이 추천된다.
> Virtual method 호출은 비싼 작업이라고 한다.
> 7배 이상의 접근시간 차이를 보일 수 있다.

- 좀더 좋은 for loop 문법을 사용하라!
> for loop(foreach라고 불리는 문법)은 내부적으로 Iteravle 인터페이스를 통해 loop를 돌리게 되는데, 일반 for문보다, 3배 정도 성능이 빨라진다고 한다.
```java
public void zero() {
    int sum = 0;
    for (int i = 0; i &lt; mArray.length; ++i) {
        sum += mArray[i].mSplat;
    } //직접 카운팅하는 경우, JIT이 최적화를 하지 못한다.
}
 
public void forcase() {
    int sum = 0;
    Foo[] localArray = mArray;
    int len = localArray.length;
 
    for (int i = 0; i &lt; len; ++i) {
        sum += localArray[i].mSplat;
    }
} //len 변수를 불러와서 불필요한 lookup을 줄였다.
 
public void foreach() {
    int sum = 0;
    for (Foo a : mArray) {
        sum += a.mSplat;
    }
} //가능하다면, 추천하는 방식이다.
```


