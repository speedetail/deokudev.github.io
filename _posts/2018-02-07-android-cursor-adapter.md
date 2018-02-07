---
published: true
layout: post
date: '2018-02-07 16:04 +0900'
postname: '[개념] 커서어뎁터(CursorAdapter)의 의미와 기능'
categories: android
tags: adapter cursor uri contentsprovider listview
---
## 커서 어뎁터(CursorAdapter)란?

> 안드로이드 개발 중 ListView에 DB에서 직접 데이터를 가져와서 화면에 출력해야 하는 경우, 사용되는 어뎁터이다. 한마디로 `화면과 Database를 연결시켜주는 Adapter`라고 보면 되겠다.

### 어뎁터(Adapter)란?

> `어뎁터란 눈에 보이는 화면과 JAVA 코드, XML 파일을 이어주는 도구`이다. 당신은 어뎁터를 통해서, ListView를 코드를 통해서 원하는대로 동작시킬 수 있다.

### 어뎁터의 2가지 종류

- ArrayAdapter : 화면과 자바 Collection(배열 등등)을 연결시켜주는 Adapter

- CursorAdapter : 화면과 DataBase를 연결시켜주는 Adapter

## 구현 예시

****CursorAdapter 예제코드****

```java
public class AutoComplete extends Activity {

public static final String[] CONTACT_PROJECTION = new String[] {
Contact._ID,
Contact.DISPLAY_NAME

};


private static final int COLUMN_DISPLAY_NAME = 1;


@Override

protect void onCreate(Bundle savedInstanceState) {
super.onCreate(saveInstanceState);
setContectView(R.layout.main);

ContentResolver content = getContentResolver();
Cursor cursor = content.query(Content.CONTENT_URI,
CONTACT_PROJECTION, null, null, null);

ContactListAdapter adapter = new ContactListAdapter(this, cursor);

AutoCompleteTextView textView = (AutoCompleteTextView)findViewById(R.id.edit);

textView.setAdapter(adapter);
}

}
```
- 1.URI를 이용하여 query문을 날리기 위해, 먼저 getContentResolver() 함수를 통해 ContentResolver를 얻어온다.
- 2.원하는 `Data 자료 형태인 URI`와 `DB에서 찾고자하는 형식인 PROJECTION`을 넣고, query문을 날려서 DB를 Cursor로 뽑아온다.
- 3.원하는대로 뽑아진 Cursor를 Adapter에 심는다.(ContactListAdapter는 CursorAdapter를 상속받아 만든 Class이다.)
- 4.setAdapter()함수를 통해 adapter를 적용한다.

****ContactListAdapter.class****

```java
public static class ContactListAdapter extends CursorAdapter {

@Override
public View newView(Context context, Cursor cursor, ViewGroup parent) {

final LayoutInflater inflater = LayoutInflater.from(context);
final TextView view = (TextView)inflater.inflate(
android.R.layout.simple_dropdown_item_1line, parent, false);
return view;

}

@Override

public void bindView(View view, Context context, Cursor cursor){
((TextView)view).setText(cursor.getString(COLUM_DISPLAY_NAME));
}

}
```
> 두가지 Method가 핵심적인 역할을 수행한다.

- newView : 실제로 내가 화면에 보여주고 싶은 layout이나 View를 참조해온다.`화면에 보여지는 부분을 처리`하는 역할을 수행한다.
- bindView : 세부적인 `View들과 cursor의 Data를 연결 및 변경`시켜 준다.

## 참조
- [CursorAdapter](https://blog.naver.com/areema/60167055176)

