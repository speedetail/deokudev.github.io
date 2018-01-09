---
published: true
layout: post
date: '2018-01-09 20:30 +0900'
categories: android
postname: '[TIP] 안드로이드 개발 팁'
---
* contents
{:toc}
## 서론

> 개발 팁을 어느 정도 알아두고 코딩하면 시행착오를 많이 줄일 수 있다.

> 꼭 유용한 Tip 5개만이라도 참고해서 코딩해야겠다.

## 안드로이드 언어 개발 Tip

- 제 3의 라이브러리를 추가하기 전에 두번 생각해라, 정말로 serious한 commitment 이다.
- 만약 사용자가 그것을 볼 수 없다면 그것이 [그려지게 하지말라!](https://riggaroo.co.za/optimizing-layouts-in-android-reducing-overdraw/)
- 당신이 정말로 필요하지 않는 이상, db는 사용하지 말라
- [RxJava](https://github.com/ReactiveX/RxJava)는 AsyncTasks의 최고의 대안이다.
- [Retrofit](http://square.github.io/retrofit/) 최고의 Networking library이다.
- [RxJava와 Retrofit & Retrolambda를 결합](https://medium.com/swlh/party-tricks-with-rxjava-rxandroid-retrolambda-1b06ed7cd29c)해서 쓰는 것이 최고의 효율을 낸다.
- [EventBus](https://github.com/greenrobot/EventBus)는 좋지만 너무 많이 쓰지마라. 코드가 더러워진다.
- [레이어가 아닌 기능별로 패키징](https://medium.com/the-engineering-team/package-by-features-not-layers-2d076df1964d)해라
- [lint](http://developer.android.com/tools/help/layoutopt.html)해라! 꼭 정독해보기!!! 단축키 중심으로
- 무엇이 build time을 걸리게 하는지 알기위해 빌드의 [profile report](https://medium.com/the-engineering-team/speeding-up-gradle-builds-619c442113cb)를 수행해라.
- [잘 알려진 구조](http://fernandocejas.com/2015/07/18/architecting-android-the-evolution/)를 사용해라!
- 시간 save를 위해[유닛테스팅](http://stackoverflow.com/a/67500/794485)이 너무 중요하다.
- ...

- Optional value를 사용하라

## Unit Test를 할 수 있는 유용한 도구 Top 3

## 사용자 설치 경로 추적하는 방법

## 안드로이드 Gradle Build 시간을 줄이는 Tip

## UI / UX 디자인 개선에 도움을 주는 Tip

- UI : 표시 애니메이션

## 개발 & 디자인시 고려사항

- UI는 마치 농담과 같다. 설명이 필요하다면 별로이다! 즉 UI는 User에게 별다른 설명이 필요없을 만큼 직관적이되, 세련되게 만들어져야 한다.

- 사용자 눈에서 멀어지면, 마음에서도 멀어진다! 보지못한다면, 아무리 쓸모있는 기능이라도 무용지물이다. 가장 중요한 기능은 직관적으로 보여야 된다. 

- 레이어 대신에 기능별로 패키징하라!

- 효율성 극대화를 위한 RxJava를 Retrofit, Retrolambda와 함께 써라!

- 사용자는 앱의 구동 화면에서 앱의 사용 여부를 결정하게 된다.

## 용어 개념 정리

- UI : User Interface, 소프트웨어의 화면 등 사용자와 접하는 면을 의미

- UX : User Experience, 사용자 경험, 소프트웨어를 사용하는 사용자의 '느낌, 태도, 행동'을 의미 한다.

> 경험을 설계해야 한다는 말은 사용자의 "느낌, 태도, 행동"을 설계한다는 것을 의미한다.

> 제품을 사용할 사람가 받을 '느낌, 태도, 행동'을 설계하는 것을 의미한다. 사용자 Context와 목적 또한 고려해야 한다.

> 일관된 목적과 철학이 있어야 한다.

> 복잡한 기능을 제거하고 꼭 필요한 것만 가장 단순하게 제공하면서도 미적인 디테일은 엄청나게 높이는 것(내부적으로는 복잡함이 감춰져 있어야 함)

> 제품의 모든 인터페이스에서 일관되게 구현하면, 자연스럽게 소프트웨어/제품에는 특유의 개성이 생긴다

- [표시애니메이션](https://developer.android.com/training/material/animations.html) : UI 요소 그룹을 표시하거나 숨길 때 사용자에게 시각적 연속성을 제공하는 기능

## 참조

- [안드로이드 개발 팁](https://academy.realm.io/kr/posts/android-weekly-kr-193/)
- [35가지 안드로이드 개발 팁](ttps://medium.com/@cesarmcferreira/building-android-apps-30-things-that-experience-made-me-learn-the-hard-way-313680430bf9)
