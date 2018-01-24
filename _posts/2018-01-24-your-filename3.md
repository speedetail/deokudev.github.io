---
published: true
layout: post
date: '2018-01-24 22:13 +0900'
postname: '[INFO] 안드로이드 스튜디오 나만의 라이브러리 만들기'
categories: android
tags: library
---
## 서론

> 검증된 라이브러리를 제외한 3rd party library를 가져다쓰면 에러의 위험을 고스란히 안고 가야되므로, 최대한 해당 3rd 라이브러리에서 필요한 기능만 가진 라이브러리를 따로 만드는 방식도 매우 좋은 것 같다.

> 대부분은 해당 라이브러리를 계속해서 독립적으로 수행하는 것이 아니라, 그냥 가져오는 것이기 때문에 두번째 방법을 추천한다.

## 링크

> [라이브러리 만들기](http://flowarc.tistory.com/entry/Android-Studio%EC%97%90%EC%84%9C-%EB%82%98%EB%A7%8C%EC%9D%98-Library-%EB%A7%8C%EB%93%A4%EC%96%B4%EB%B3%B4%EA%B8%B0)

> [외부라이브러리 폴더 내 저장하고 적용하는 법](http://hashcode.co.kr/questions/98/%EC%95%88%EB%93%9C%EB%A1%9C%EC%9D%B4%EB%93%9C%EC%8A%A4%ED%8A%9C%EB%94%94%EC%98%A4%EC%97%90%EC%84%9C-%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%EC%97%90-%EB%9D%BC%EC%9D%B4%EB%B8%8C%EB%9F%AC%EB%A6%AC-%EC%B6%94%EA%B0%80%ED%95%98%EB%8A%94%EA%B1%B4-%EC%96%B4%EC%BC%80%ED%95%B4%EC%9A%94)

- build.gradle 파일과 src폴더로 구성된 라이브러리 폴더를 메인 프로젝트 폴더에 폴더 채로 불러온다. libs 라는 폴더를 만들고 넣어도 무방하다.(라이브러리 build.gradle파일에는 library 플러그인으로 적혀있을 것이다.)

- 메인 프로젝트의 settings.gradle 파일을 열고 아래 형식으로 추가해준다. 여기서 bottom-bar는 라이브러리 폴더 이름이다.

```java
include ':app' ':libs:bottom-bar'
```
- 메인 프로젝트의 build.gradle Module 파일의 dependencies 부분에 아래와 같이 추가한다.
```java
compile project(":libs:bottom-bar")
```


- 메인 프로젝트의 build.gradle Project 파일의 task clean 괄호 끝나고 빈공간에 아래와 같이 설정에 맞게 해준다.
```java
ext {
    compileSdkVersion = 25
    //buildToolsVersion = "25.0.2"
    minSdkVersion = 11
    targetSdkVersion = 25
    supportLibraryVersion = "25.3.0"
    junitVersion = "4.12"
}
```

- 메인 프로젝트의 build.gradle Module 파일을 아래와 같이 수정한다.
```java
android {
    //compileSdkVersion 26
    compileSdkVersion rootProject.ext.compileSdkVersion
    //buildToolsVersion rootProject.ext.buildToolsVersion
    defaultConfig {
        applicationId "com.speedetail.speedetail"
        //minSdkVersion 19
        //targetSdkVersion 26
        minSdkVersion rootProject.ext.minSdkVersion
        targetSdkVersion rootProject.ext.targetSdkVersion
          ...
```
- 마지막으로 라이브러리의 build.gradle 파일에는 아래와 같이 추가해준다.
```java
apply plugin: 'com.android.library'

android {
    compileSdkVersion rootProject.ext.compileSdkVersion
    buildToolsVersion rootProject.ext.buildToolsVersion

    defaultConfig {
        minSdkVersion rootProject.ext.minSdkVersion
        targetSdkVersion rootProject.ext.targetSdkVersion
        versionCode 1
        versionName "1.0"
        testInstrumentationRunner "android.support.test.runner.AndroidJUnitRunner"
    }

}

dependencies {
    compile fileTree(dir: 'libs', include: ['*.jar'])
    compile 'com.android.support:appcompat-v7:' + rootProject.ext.supportLibraryVersion
    compile 'com.android.support:design:' + rootProject.ext.supportLibraryVersion

    testCompile 'junit:junit:' + rootProject.ext.junitVersion
    androidTestImplementation 'com.android.support.test:runner:1.0.1'
    androidTestImplementation 'com.android.support.test.espresso:espresso-core:3.0.1'
}
```