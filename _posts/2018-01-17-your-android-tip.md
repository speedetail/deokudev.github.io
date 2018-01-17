---
published: true
layout: post
date: '2018-01-17 14:53 +0900'
postname: '[TIP] 안드로이드 성능 디버깅에 필요한 라이브러리'
categories: android
tags: 'debugging '
---
## 서론

> 본격적으로 앱을 출시하려면 여러가지 테스트가 필요하다.

> 아래는 안드로이드 스튜디오와 함께 사용할 수 있는 유용한 디버깅 툴들이다.

## 최종적인 성능 디버깅에 필요한 TOP 3

1. [Library methods count](http://www.methodscount.com/) : 안드로이드 65만개의 메소드를 넘는지 확인해준다. 
2. [Stetho](http://facebook.github.io/stetho/) : 네트워크 트래픽, SQLite DB, Shared Preference를 쉽게 감시할 수 있다.
3. [LeakCanary](https://github.com/square/leakcanary) : 메모리 릭을 감지해준다.
