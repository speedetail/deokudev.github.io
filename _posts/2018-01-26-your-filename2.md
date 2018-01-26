---
published: true
layout: post
date: '2018-01-26 14:24 +0900'
postname: '[배움] Util 클래스란? xml 작성 시 Tip'
categories: android
tags: xml utils
---
## 서론

> 가장 피해야할 최악은 클래스마다, 똑같은 함수를 반복적으로 붙여넣는 일이다. 만약 (서로 기능이) 다른 화면 페이지에 따른 클래스는 구성이 다소 비슷하더라도, 계속해서 복붙해서 개별적으로 만들어도, 괜찮겠지만, 그 안에 들어가는 함수가 동일하게 사용될 경우, 유틸성이 좋도록 따로 함수를 빼놓고 사용한다.

> 실제적으로 Toast나 String의 경우 많이 그렇게 사용된다. 해당 클래스는 static 형태로 메소드가 정의된다.

> xml은 기본적으로 기능으로 정의되는 것이 아니라, '형태로 정의' 되도록 해야한다. 만약 내가 week, month, etc에 해당하는 fragment를 만든다고 할 때, 각각 기능이 다르지만, fragment_week, fragment_month, fragment_etc로 따로 만드는 것이 아니라 , 만약 week,etc가 tab+viewpager 구성으로 이루어져 있다면, fragment_tabs, fragment_calendar로 만드는 것이 맞다.

## 참조

- Toast Util

```java

package net.sjava.toast;

import android.content.Context;
import android.os.CountDownTimer;
import android.widget.Toast;

public class ToastUtil {
    
    /**
     * 2초
     * @param c
     * @param message
     */
    public static void show(Context c, String message) {
        if(c == null || StringUtil.isEmpty(message))
            return;
        
        try {
            Toast.makeText(c, message, Toast.LENGTH_SHORT).show();
        } catch(Exception e) {
            // ignore
        }
    }
    
    /**
     * 3.5 초
     * @param c
     * @param message
     */
    public static void showLong(Context c, String message) {
        if(c == null || StringUtil.isEmpty(message))
            return;
        
        try {
            Toast.makeText(c, message, Toast.LENGTH_LONG).show();
        } catch(Exception e) {
            // ignore
        }
    }
    
    /**
     * 커스텀..
     * @param c
     * @param message
     * @param miliseconds
     */
    public static void show(final Context c, final String message, int miliseconds) {
        if(c == null || StringUtil.isEmpty(message))
            return;
        
        int duration = miliseconds;
        if(duration < 2000)
            duration = 2000;
        
        final Toast t = Toast.makeText(c, message, Toast.LENGTH_SHORT);
        new CountDownTimer(duration, 1000) {
            @Override
            public void onTick(long millisUntilFinished) { 
                t.show();
            }
            
            @Override
            public void onFinish() { }
        }.start();
    }
}
```

- String Utils

```java
package net.sjava.toast;

public class StringUtil {

    public static boolean isEmpty(String str) {
        if(str == null || str.trim().length() ==0)
            return true;
        
        return false;
    }
    
    public static boolean isAnyEmpty(String str1, String str2) {
        if(isEmpty(str1) || isEmpty(str2))
            return true;
        
        return false;
    }

    public static boolean isAllEmpty(String str1, String str2) {
        if(isEmpty(str1) && isEmpty(str2))
            return true;
        
        return false;
    }
}
```
