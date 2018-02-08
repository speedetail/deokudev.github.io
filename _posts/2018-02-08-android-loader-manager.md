---
published: true
layout: post
date: '2018-02-08 09:03 +0900'
postname: '[개념] 로더매니저(LoaderManager)의 의미와 기능'
categories: android
tags: 개념
---
(:toc)
## Loader란?

> 안드로이드 3.0 이후부터는 LoaderManager가 제공되었는데, 한마디로 `Loader는 Data의 비동기 Loading 기능`을 수행한다. 추가적으로 밑의 기능을 제공한다.

- `모든 Activity와 Fragment에서 사용 가능`하다는 특징이 있다. (하나의 Activity or Fragment에 하나의 LoaderManager를 갖고, LoaderManager의 경우 여러개의 Loader를 가질 수 있다.)
- 데이터 출처(data source)를 `모니터링하면서 content가 변경되면 전달`해준다.
- 구성(configuration,orientation의 변경 등)이 바뀐 후 `다시 만들어질 때, 자동적으로 마지막에 사용한 loader의 data 관련 cursor에 접속`한다. 즉 필요한 data를 얻어오기 위해 다시 query해와서 cursor에 넣을 필요가 없다.

> 다운로드 시 progress를 activity에서 보여줄 때, 화면 전환으로 인한 값 상실을 방지하기 위해, LoaderManager를 사용하면 좋다고 함

## Loader Callbacks

> Callback 메소드 함수는 일반 함수와 다르게, `내가 호출하려고 만드는 함수가 아니라, 외부에서 호출 받을 때에 특정 기능을 수행하도록 만드는 함수`를 의미한다. 보통은 콜백함수를 만들고, register(등록)해 두는 방식으로 진행된다.

> LoaderManger가 시작할 때와 끝날 때, 우리가 원하는 일을 시킬 수 있게되는데, 이 일을 하는 것이 바로 LoaderCallbacks이다. 즉 `LoaderManager의 시작 시점과 끝 시점에 호출되는 콜백 함수`를 의미한다. 이러한 LoaderCallbacks 은 LoaderManager.initLoader()에서 register(등록)된다.

> LoaderManager.LoaderCallbacks<?>을 implement할 경우, 밑의 3가지 콜백함수를 Override하게 된다.

- onCreateLoader() : LoaderManager.initLoader() 를 호출할 때, 바로 호출되는 함수이다.

- onLoadFinished() : onStart() 이후, AsyncTask(비동기 작업)이 동작을 시작해서 끝난 후에, 호출되는 함수이다. data가 완전히 로딩되고 호출되므로, 해당 데이터를 활용해서 UI를 업데이트 시키는 코드를 작성하면 된다.

- onLoadReset() : LoaderManager.restartLoader()에서 새로운 loader를 가져오고, 쓰이지 않는 loader를 destroy()할 때 호출되는 함수 이다.

## 예시

- https://github.com/alexjlockwood/AppListLoader

> 해당 소스에서는 Fragment가 LoaderManager.LoaderCallbacks를 implement하고 있다.

```java
class AppListFragment extends ListFragment implements
  
      LoaderManager.LoaderCallbacks<List<AppEntry>>
```

## 동작 순서

```
 +--------------------------+------------------------+
 |                          |                        |
 |   +-------------------+  |                        |
 |   | onCreateLoader()  |  |                        |
 |   +--------+----------+  |                        |
 |            |             |                        |
 |   +--------+----------+  |                        |
 |   | onStartLoading()  +--|-----------+            |
 |   +-------------------+  |           |            |
 |                          |           |            |
 |                          |  +--------+----------+ |
 |            +-------------|--+ loadInBackground()| |
 |            |             |  +-------------------+ |
 |            |             |                        |
 |   +--------+----------+  |                        |
 |   | deliverResult()   |  |                        |
 |   +--------+----------+  |                        |
 |            |             |                        |
 |   +--------+----------+  |                        |
 |   | onLoadFinished()  |  |                        |
 |   +-------------------+  |                        |
 +--------------------------+------------------------+

```

- Fragment에서 `LoaderManager.initLoader()를 호출` (onStart() 이전에 호출해야 함) 하면서, LoaderCallBack을 implement하는 Fragment를 LoaderCallBack으로 등록시킨다.

- LoaderManager가 `onCreateLoader()를 호출`한다.

- `AppLoader()가 만들어진다.`

- Activity가 생성되면서 onStart()를 호출 시 밑의 함수를 차례로 호출

```java
LoadManager.doStart() ... 
	AppLoader.startLoading() ... 
 		AsyncTaskLoader.onForceLoading() ...
```
- onForceLoading()이 LoadTask()를 생성 후, Thread를 이용하여 실행

- Thread가 doInBackground()를 실행 (이때부터 비동기로 작업 수행)

- onPostExecute()를 UI thread Handler에게 넘김 (비동기 작업이 끝남) 

- onPostExecute()를 실행하면서,

```java
AppLoader.deliveryResult() ...
	super.deliveryResult() ...
  		onLoadFinished() 호출  
```  
- `onLoadFinished()`에 데이터가 처리되었을 때, UI 데이터 변경 작업을 실시

## 참조

- [LoaderManager 동작 이해](http://i5on9i.blogspot.kr/2013/02/loadermanager.html)
