---
published: true
layout: post
date: '2018-01-06 19:26 +0900'
postname: 지킬에 Prose.io App 적용
categories: jekyll
tags: jekyll prose.io blog
---
* content
{:toc}

## Jekyll 블로그에 Prose.io(온라인 Markdown 편집기) 붙이기

> 매번 Github로 들어가서, 피곤하게 마크다운 편집하면서, Commit 하기에는 다소 힘들 것 같아서, 온라인 Markdown + Github 자동 커밋을 지원하는 Prose.io를 통해, 간단하게 버튼하나로 삽입/수정이 가능하도록 만드는 작업을 했다.

> 도중에 불필요한 작업을 너무 많이 했다.

## Debugging Process
- Prose.io 특성상 title 필드와  file name을 구분을 안해놓아서, raw metadata에 **title:""** 식으로 표현하면, 멈춰버리는 문제가 발생했다.

> 결국 모든 소스를 탐색해서 title을 postname으로 바꾸어주는 작업을 수행했다..

> 가끔 Prose.io가 권한을 재요청해야 하는 경우가 있는 것 같다.이 경우에는 [Prose재권한요청](prose.io) 요기서, 다시 authorization을 해주면 된다.
    
- 원래는 기존 플랫폼에서 Prose.io로 이동하게 만들려고 했는데, https에서 iframe을 통해 http를 불러오면, 보안 오류가 발생하더라, 온갖 삽질 끝에 그냥 링크 이동으로 만족하련다.

## 마무리

> 아무튼 이제는 쉽게 포스팅 할 수 있어서 매우 좋다..
