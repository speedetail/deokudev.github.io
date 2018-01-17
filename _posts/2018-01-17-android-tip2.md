---
published: true
layout: post
date: '2018-01-17 21:10 +0900'
postname: '[TIP] 안드로이드 라이브 템플릿 사용하기 (빠른 코딩)'
categories: android
tags: tip fast coding programming androidstudio
---
* contents
{:toc}
## 서론	

> 라이브 템플릿 기능을 사용하면 매우 빠르게 코딩이 가능하다는 장점이 있다.

## 대표적인 라이브 템플릿 기능 사용하기

> Ctrl + Alt + S를 눌러 환경설정에 진입한 뒤, Live Templates 탭을 선택

## 대표적인 템플릿 기능

### Android.xml
- **`const`**: "Define android style int constant"
- _**`fbc`**: "findViewById with cast"_
- _**`foreach`**: "Create a for each loop"_
- **`gone`**: "Set view visibility to GONE"
- **`IntentView`**: "Creates an Intent with ACTION_VIEW"
- **`key`**: "Key for a bundle"
- **`newInstance`**: "create a new Fragment instance with arguments"
- **`noInstance`**: "private empty constructor to prohibit instance creation"
- **`rgS`**: "get a String from resources"
- **`rouiT`**: "runOnUIThread"
- **`sbc`**: "block comment for structuring code"
- **`Sfmt`**: "String format"
- **`starter`**: "Creates a static start(...) helper method to start an Activity"
- **`Toast`**: "Create a new Toast"
- **`ViewConstructors`**: "Adds generic view constructors"
- **`visible`**: "Set view visibility to VISIBLE"
- **`wrapIt`**: "adds a gradle wrapper task"

### AndroidComments.xml
- **`ccode`**: "code tag for javadoc"
- **`cfalse`**: "puts false in a comment section"
- **`clink`**: "link from within javadoc"
- **`ctrue`**: "puts true in a comment section"
- **`fixme`**: "adds // FIXME"
- **`noop`**: "indicate that a method does not have any operations"
- **`stopship`**: "adds // STOPSHIP"
- _**`todo`**: "adds // TODO"_

### AndroidExternal.xml
- **`createObservable`**: "Create RxJava Observable"
- **`Crouton`**: "Creates a new Crouton"
- **`CroutonFragment`**: "Creates a new Crouton for display within a fragment"
- **`CroutonShow`**: "Creates a new Crouton with Crouton.showText"
- **`onEvent`**: "Adds onEvent method for eventbus"
- **`onEventMainThread`**: "Adds onMainThreadEvent method for eventbus"

### AndroidLog.xml
- _**`logd`**: "Log.d(TAG, String)"_
- **`loge`**: "Log.e(TAG, String, Exception)"
- **`logi`**: "Log.i(TAG, String)"
- **`logm`**: "Log method name and its arguments"
- **`logr`**: "Log result of this method"
- **`logt`**: "A static logtag with your current classname"
- **`logw`**: "Log.w(TAG, String, Exception)"
- **`wtf`**: "Log.wtf(TAG, String, Exception)"

### AndroidParcelable.xml
- **`Parcelable`**: "Create a parcelable block for your current class"
- **`ParcelableEnum`**: "Create a parcelable block for your current enum"
- **`ParcelableEnumTest`**: "Creates basic parcelable enum test methods"
- **`ParcelBoolean`**: "writes a single boolean value to a parcel"
- **`UnparcelBoolean`**: "reads a single boolean value from a parcel"
- **`UnparcelIntArray`**: "Unparcels an int array"
- **`UnparcelStringArray`**: "Unparcels a String array"

### AndroidXML.xml
- **`appNs`**: "adds application namespace"
- **`lh`**: "android:layout_height=&quot;&quot;"
- **`lhm`**: "android:layout_height=&quot;match_parent&quot;"
- **`lhw`**: "android:layout_height=&quot;wrap_content&quot;"
- **`lw`**: "android:layout_width=&quot;&quot;"
- **`lwm`**: "android:layout_width=&quot;match_parent&quot;"
- **`lww`**: "android:layout_width=&quot;wrap_content&quot;"
- **`toolsNs`**: "adds tools namespace to Android xml file"
