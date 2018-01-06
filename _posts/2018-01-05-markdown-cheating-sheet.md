---
published: true
layout: post
postname: '마크다운 치팅시트'
title: 'markdown-cheating-sheet'
date: '2018-01-05 19:06 +0900'
categories: jekyll
tags: jekyll blog markdown
---

* content
{:toc}

## Markdown 문법
> 지킬 블로그를 시작하면서, 가장 먼저 익혀야할 markdown 문법이다. 매우 매력있다.
다는 몰라도 대표적인 거 몇개만 알면 충분히 사용가능할 거라 본다.

## Text 정리 노트!

> 마크다운 입력창과 표시 결과 형식으로 정리해보자.

### Header 표시하기

```
# Text
## Text
###### Text
```
> # Text
> ## Text
> ###### Text

#### List 표시하기

```
- List Contents
* List Contents
  * Nested List
  
1. List Contents
2. List Contents
3. List Contents
  
```
> - List Contents
> * List Contents
>   * Nested List

> 1. List Contents
> 2. List Contents
> 3. List Contents

#### Blockquotes 표시하기

```
> 문단
>
>> 문단2
>>
>>> 문단3
>>>
```
> 문단
>
>> 문단2
>>
>>> 문단3
>>>

#### Code Block 창 표시하기

> 숫자 1 왼쪽에 물결 표시를 코드 위 아래로 3개씩 찍어주면 된다.

#### Horizontal Bar 표시하기

```
---
***
* * *
```
---
***
* * *

#### Text 기울임,볼드체 표시하기
```
*Text*
_Text_
**Text**
__Text__
```
> *Text*
> _Text_
> **Text**
> __Text__

#### Links 표시하기
```
[Text](http://google.com/)
<http://google.com>
```
> [Text](http://google.com/)
> <http://google.com>

#### Image 표시하기
```
![Alt_Text](/assets/img/logo.png)
```
> ![Alt_Text](/assets/img/logo.png)

### Knowledge
> Markdown 언어는 표준화가 잘 되어 있지 않아서, 여러 가닥으로 파편화되어 있다. github에서는 대표적으로 kramdown이라는 문법을 사용한다.

### 치팅 시트 이미지
![마크다운치팅시트](/assets/img/Markdown.jpg)
