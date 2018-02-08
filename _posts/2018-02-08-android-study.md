---
published: true
layout: post
date: '2018-02-08 14:43 +0900'
postname: '[TIP] 안드로이드/자바 공부 링크 모음'
categories: android
tags: study
---
## 서론

> 코드 분석하면서, 공부하는 재미가 쏠쏠하지만, 너무 정리하면서 하다가 보면, 흐름이 끊기고 진도가 막히는 경우가 있다. 대충 링크를 보고 이해했다면, 나중에 한번에 링크별로 정리할 수 있도록 링크만 모으도록 하겠다. 왜냐하면, 몰아서 한번에 효율적으로 해야 조급하지도 않고, 즐거울 수 있다.

## 링크 모음

> 자바의 runnable interface : https://blog.naver.com/highkrs/220274474749

- `run 메쏘드 달랑 하나 있는 interface로써, 멀티쓰레드 프로그래밍을 작성하기 위해 사용되는 자바의 추상 interface`이다. 보통 방식은 클래스를 선언하여 runnable을 implement한 후에 추상메쏘드인 run을 재정의 해주고, Thread를 새로 선언하여, 인자로 넘겨준 뒤, Thread.start() 함수를 통해 비동기 처리를 하게 된다. 그러나 바로 Thread의 인자에 new runnable(){}형식으로 넣어주기도 한다.