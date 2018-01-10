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

> 써드 파티 라이브러리는 관리, 안전성 측면에서도 위험도가 높다.

- 만약 사용자가 그것을 볼 수 없다면 그것이 [그려지게 하지말라!](https://riggaroo.co.za/optimizing-layouts-in-android-reducing-overdraw/)

> Layout을 그릴 때, Overdraw를 최소화하는 것이 성능에 좋다. 만들고 최적화시에 검토해주자.
>> Go to Settings on your device.
>> Go to Developer Options
>> Select “Debug GPU Overdraw”.
>> Select “Show overdraw areas”

```xml
<RelativeLayout
            android:layout_width="match_parent"
            android:layout_height="match_parent"
            android:background="#FFFFFF"> //REMOVE THIS!
```

- 당신이 정말로 필요하지 않는 이상, db는 사용하지 말라

> db가 포함되는 순간 매우 복잡해진다.

- [RxJava](https://github.com/ReactiveX/RxJava)는 AsyncTasks의 최고의 대안이다.

> RxJava의 일반적인 용도 중의 하나는 계산을 수행하는 것인데, 백그라운드 thread 상에서 네트워크 요청을 처리하고 결과또는 에러를 UI thread에 보여주는 역할을 한다.
 
- [Retrofit](http://square.github.io/retrofit/) 최고의 Networking library이다.

> Retrofit는 HTTP API를 Java 인터페이스로 바꾸어주는 역할을 한다. GET, POST, PUT, DELETE, and HEAD 등으로 쉽게 서버 API를 처리할 수 있다.

- [Retrolambda](https://medium.com/android-news/retrolambda-on-android-191cc8151f85)를 사용해서 코드를 짧게 만들어라.

```java
button.setOnClickListener(new View.OnClickListener() {
    @Override
    public void onClick(View v) {
        log("Clicked");
    }
});
button.setOnClickListener(v -> log("Clicked"));
```

- [RxJava와 Retrofit & Retrolambda를 결합](https://medium.com/swlh/party-tricks-with-rxjava-rxandroid-retrolambda-1b06ed7cd29c)해서 쓰는 것이 최고의 효율을 낸다.

- [EventBus](https://github.com/greenrobot/EventBus)는 좋지만 너무 많이 쓰지마라. 코드가 더러워진다.

> Components간의 커뮤니케이션을 간단화한다.

- [레이어가 아닌 기능별로 패키징](https://medium.com/the-engineering-team/package-by-features-not-layers-2d076df1964d)해라

> Packaging stuff together by what it is, and not by what it does
> 구체적으로 무엇을 하는가에 따라 나누지 말고, 그것이 어떤 기능(feature)을 하는가에 따라 구조를 결정해라.

![data]({{site.baseurl}}/https://cdn-images-1.medium.com/max/1200/1*A-m20R0Qve-eB4ishqZc_Q.png)

> bad case
![레이어별]({{site.baseurl}}/https://fernandocejas.com/assets/migrated/package_organization-795x1024.png)

- 모든 작업을 application thread에서 퇴출시켜라.

- [lint](http://developer.android.com/tools/help/layoutopt.html)해라! 꼭 정독해보기!!! 단축키 중심으로

> *유용한 단축키*
> 버전 관리	Alt+9	
> 실행	Shift+F10	
> 디버그	Shift+F9
> Android Monitor	Alt+6

> *코드작성단축키*
> 기본완성 Ctrl + Space : 변수,유형,메쏘드 기본 추천 항목 표시, 두번누르면 더 많은 결과
> 스마트완성 Ctrl + Shift + Space : 상황에 따른 관련 옵션도 추가로
> 명령문 완성 Ctrl + Shitt + enter : 명령문 자동 완성 후, 누락된 소활호, 중괄호 추가
> Alt + enter로 신속하게 수정하고 원하는 액션을 표시 가능

> *탐색키*
> 최근 액세스한 파일간의 전환 : Ctrl + E
> 현재 파일구조보기 : Ctrl + F12
> 파일,폴더 탐색 : Ctrl + Shift + N
> 클래스 탐색 : Ctrl + N
> 메서드,필드 탐색 : Ctrl + Shift + Alt + N
> Alt + F7로 모든 코드조각 탐색

> *스타일 및 서식*
> 탭, 들여쓰기, 공백, 줄바꿈, 괄호, 빈줄 규칙
> File = Settings = Editor = Code Style
> Ctrl + Alt + I로 모든 줄에 자동 들여쓰기 적용가능

> *버전 제어 기본 정보*
> Android Studio의 VCS 메뉴 옵션을 사용함
> 레포지토리를 만들고, 새파일을 버전 제어로 가져오는 방식으로 수행
> 1.VCS 메뉴에서 Enable Version Control Integration을 클릭
> 2.드랍다운 메뉴에서 프로젝트 루트에 연결할 버전제어 시스템 선택한 뒤 OK
> File-Setting-Version Control 참조

> *Gradle 빌드 시스템*
> Android Studio는 빌드 시스템 기반으로 Gradle을 사용하므로, 더 많은 Android 전용 기능이 Gradle용 플러그인을 통해 제공된다.
> build.gradle 파일로 구성

> *Proguard*
> 코드 축소 도구를 의미한다.

> *종속성(dependency) 관리*
> 프로젝트의 종속성은 build.gradle 파일에 이름으로 지정됩니다. Gradle은 종속성을 찾고 빌드에서 사용할 수 있게 만듭니다. 모듈 종속성, 원격 바이너리 종속성 및 로컬 바이너리 종속성을 build.gradle 파일에 선언할 수 있습니다

> 성능 모니터 / 힙 덤프 : 리소스 확인 가능
> Allocation Tracker : 메모리 할당 추적

> *Debugger 도구*
> 1.인라인 디버깅 : 인라인 변수 값, 선택한 객체를 참조하는 참조 객체, 함수반환값, 람다 및 연산자 식, 도움말 값을 나타내준다.
Debug = Settings = Show Values Inline 선택
> 2.Lint 도구 : 잠재적 버그, 정확성, 보안, 성능을 높이기 위해 소스 검사
Analyze > Inspect Code를 클릭한 후 Lint의 Inspection Results 창에서 확인
> cf) 명령줄 또는 Android Studio를 사용하여 Android 프로젝트에서 실행할 수 있는 정적 코드 스캔 도구, 구조적 코드 문제를 검사한다.
> Analyze > Inspect Code

- [gradle build 시간을 줄이자](https://medium.com/the-engineering-team/speeding-up-gradle-builds-619c442113cb).

>/Users/cesarferreira/.gradle/gradle.properties
```java
org.gradle.daemon=true
org.gradle.parallel=true
org.gradle.configureondemand=true
```

- 무엇이 build time을 걸리게 하는지 알기위해 빌드의 [profile report](https://medium.com/the-engineering-team/speeding-up-gradle-builds-619c442113cb)를 수행해라.

> Run the gradle build profile tool & Stick to essential module dependencies

- [잘 알려진 구조](http://fernandocejas.com/2015/07/18/architecting-android-the-evolution/)를 사용해라!

>
![architerture]({{site.baseurl}}/https://fernandocejas.com/assets/migrated/clean_architecture_android.png)

> [클린 구조](https://github.com/android10/Android-CleanArchitecture)
> 최대한 dependency는 줄여라!
> [SOLID](https://ko.wikipedia.org/wiki/SOLID), 객체프로그래밍을 준수하라.
> Dependency Injection을 수행하는 Dagger 2 라이브러리를 사용해라.
> build.gradle 파일에 모두 dependency를 기록하지 마라
```java
def ciServer = 'TRAVIS'
def executingOnCI = "true".equals(System.getenv(ciServer))

// Since for CI we always do full clean builds, we don't want to pre-dex
// See http://tools.android.com/tech-docs/new-build-system/tips
subprojects {
  project.plugins.whenPluginAdded { plugin ->
    if ('com.android.build.gradle.AppPlugin'.equals(plugin.class.name) ||
        'com.android.build.gradle.LibraryPlugin'.equals(plugin.class.name)) {
      project.android.dexOptions.preDexLibraries = !executingOnCI
    }
  }
}
```
```java
apply from: 'buildsystem/ci.gradle'
apply from: 'buildsystem/dependencies.gradle'

buildscript {
  repositories {
    jcenter()
  }
  dependencies {
    classpath 'com.android.tools.build:gradle:1.2.3'
    classpath 'com.neenbedankt.gradle.plugins:android-apt:1.4'
  }
}

allprojects {
  ext {
	...
  }
}
...
```
- 시간 save를 위해[유닛테스팅](http://stackoverflow.com/a/67500/794485)이 너무 중요하다.
- 앱을 더 모듈화 시키고, 테스트하기 쉽도록 [dependency injection](http://fernandocejas.com/2015/04/11/tasting-dagger-2-on-android/)을 사용해라.
- [fragmented podcast](http://fragmentedpodcast.com/)에 대해 듣는 것도 유용할 것이다.
- [절대 당신의 개인 email을 안드로이드 마켓용으로 사용하지 마라](https://www.reddit.com/r/Android/comments/2hywu9/google_play_only_one_strike_is_needed_to_ruin_you/)
- 항상 [적절한 input types](http://developer.android.com/training/keyboard-input/style.html)를 사용해라
- 사용패턴과 버그를 찾기 위해 analytics를 사용해라
- [라이브러리](http://android-arsenal.com/)를 가장 최근 상태로 유지해라.(더 빠르게 그것들을 테스트하기 위해 [dryrun](https://github.com/cesarferreira/dryrun)을 사용해라)
- Service는 필요한 일을 하고, 가능한 한 빠르게 죽어야 한다.
- username과 email addresses에 로그인을 제안하기 위한 [Account manager](http://developer.android.com/reference/android/accounts/AccountManager.html)를 사용해라.
- beta와 production.apk를 빌드하고 배포하기 위해 CI(Continuous Integration)을 사용해라.
- 고유의 CI server를 만들지 말고, circleci, travis, shippable을 사용하라.
- [플레이 스토어의 deployments를 자동화시켜라](https://github.com/Triple-T/gradle-play-publisher)
- 만약 라이브러리가 거대하고 함수들의 작은 부분만 사용한다면, 당신은 대안으로 작은 옵션을 찾아내야 한다.(instance에 대한 [proguard](http://developer.android.com/tools/help/proguard.html)를 참조해라)

_ 당신이 정말로 필요한 것보다 더 많은 모듈들을 사용하지 마라.컴파일 오래 걸릴라.

- [SVGs에 대한 PNGs를 ditching하는 것](http://developer.android.com/tools/help/vector-asset-studio.html)에 대해 생각하라.

- 라이브러리 abstraction classes을 만들어라. 좀더 좋은 옵션이 생겨서, 어느 자리를 swithching하는 것이 필요할 때 더 쉽다. (Log.d(TAG,message) -> [Timber.d(message)](https://github.com/JakeWharton/timber))

- 연결성과 연결의 타입을 감시하라.(wifi일 때, 데이터 업데이트가 더많이 일어나는가?)

- 파워소스와 배터리를 감시하라.(충전 중에 데이터 업데이트가 더 많이 일어나는가? 배터리 낮을 때 업데이트를 중단하는가?)

- 테스트는 성능면에서 뛰어납니다. 느린 (그러나 올바른) 구현을 작성한 다음 최적화가 테스트를 통해 어떤 것도 깨뜨리지 않는지 확인하십시오.

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
- [35가지 안드로이드 개발 팁](https://medium.com/@cesarmcferreira/building-android-apps-30-things-that-experience-made-me-learn-the-hard-way-313680430bf9)
