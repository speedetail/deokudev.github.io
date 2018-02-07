---
published: true
layout: post
date: '2018-02-07 15:17 +0900'
postname: '[개념] 컨텐츠 프로바이더(Contents Provider)의 의미와 기능'
categories: android
tags: contents uri
---
## Content Provider는 왜 존재하는가?

> 안드로이드 개발 중 DB의 정보를 가져와서 화면에 보여줘야할 때, 직접 DB를 생성하고 조작하지 않고, 주소록이나 미디어 파일과 같이 다른 어플리케이션의 DB에 접근해야하는 경우에 Android Framework에서는 함부로 Application이 DB에 접근할 수 없도록 권한을 부여해 놓았다.

> 이러한 보안 이슈로 인해 개발자가 명시적으로 제공한 data에 대해서만 접근이 가능하게 되는데, 안드로이드 상에서 `다른 App의 개발자가 명시적으로 제공한 data에 접근해서 가져다쓸 수 있도록 기능을 제공하는 Android Framework`를 의미한다. 

## 간단한 예시

- Contact 어플에서 "내 자료를 가져다 쓰시오" 하고 제공하길 원하는 DB를 `Content Provider`를 통해 입력해 놓는다.
- MyApp 어플에서는 "이 자료를 가져다 쓸 수 있겠군" 하고 `Content Resolver`를 통해 원하는 자료를 가져올 수 있게 된다.

## URI란?

> Content Provider 특성상 다른 Application 사이의 공유를 전제하므로, 자료를 가져다 사용할 때, `Contents의 자료형태`를 지켜주어야 한다.

> Content의 URI 형태는 아래와 같다.

![uri.jpg]({{site.baseurl}}/posts_img/uri.jpg)


- A : Contents URI에는 항상 `content://`을 써주어야 한다.
- B : `기관`을 의미하지만, 자바의 패키지 이름이라고 생각하자. 나중에 Manifest 파일에 명시해주어야 한다.
- C : `Path`라고 한다. 패키지 내 파일의 경로로 생각하면 된다.
- D : 자료의 ID이다. 파일명 대신에 ID를 사용한다.

### URI를 만드는 두가지 방법

- 직접 만들기

```java
public static final Uri CONTENT_URI = Uri.parse("content://" + AUTHORITY + "/images");
```

- android.net.Uri.Builder 클래스와 android.content.ContentUris 클래스를 사용해서 만들기 (주로 많이 사용된다.)

```java
Uri.Builder builder = Contents.CONTENT_URI.buildUpon();

ContentUris.appendId(builder,groupCursor.getLong(GROUP_ID_COLUMN_INDEX));
builder.appendencodePath(Contacts.Data.CONTENT_DIRECTORY);

Uri phoneNumbersUri = builder.build();
```

> 특이한 data 형식을 사용하지 않는 한 Framework에서 제공하고 있는 URI를 사용하면 된다.

## 구현하기

> [ContentProviderOperation](http://developer.android.com/reference/android/content/ContentProviderOperation.html)이라는 자바 클래스를 이용하여 구현이 가능하다.

## 참조

- [Contents Provider - 컨텐츠 프로바이더란?|작성자 애송](https://blog.naver.com/areema/60165412681)
