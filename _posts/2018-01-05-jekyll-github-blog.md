---
layout: post
title:  "Jekyll + Gitbug Blog 만들기"
date:   2018-01-05 10:28:00
categories: jekyll
tags: jekyll blog github
---

* content
{:toc}

### Github + Jekyll Blog 만들기

> 복잡하면, 정의부터 알아보자

### Github 웹호스팅 서비스 + Jekyll Template

> Github는 별도의 서버, 도메인을 가지고 있지 않아도 repository에 있는 html 파일을 웹페이지 형식으로 보여주는 서비스를 제공해 준다.

> Jekyll은 ruby기반으로 만들어진 손쉽게 blog스타일의 정적 site(html 파일을 내부적으로 생성)를 생성해주는 도구로써, Github Repository로 Fork(가져오기)만 해오면, 바로 사용이 가능하다. 사용자는 html 작성 필요 없이 .md파일만으로 포스팅이 가능하게 된다.
(Jekyll은 한마디로 소스의 구조를 지칭한다고 볼 수 있다)

#### 두가지를 잘 조합하면..

- Github 페이지를 구성한다.

- 페이지 Github Repository에 쓸만한 Jekyll Theme Repository를 Fork해와서, 설정을 바꾸어주면 개인 블로그를 손쉽게 구축이 가능하다.

> 그렇다면, 구체적으로 만들어보자.

### Github 가입 & Github Page 만들기
---------------

- 제일먼저 Githib에 계정을 가지고 있어야 한다. [http://www.github.com](http://www.github.com)에서 유니크한 ID를 선택하고 메일 인증통해서 가입완료
- 가입을 완료하면 repository를 만들면 내 git 저장소를 사용할 수 있게 되는데, 웹페이지 형식으로 repository를 띄우려면, repository이름을 *{계정이름}.github.io*로 생성해야 한다. (계정repository 생성) 
- 그렇게 되면 해당 주소만 입력해도 바로 접근이 가능하다.
(만약 저거 외에 다른 이름을 주면 project url이라고해서 *http://{계정이름}.github.io/{repsitory이름}* 으로 사용할 수 있지만 github에 내장된 page서비스인 jekyll 기능을 사용에 제약이있다)

### Github Page를 Jekyll 템플릿으로 입히기
---------------

- 맘에 드는 Jekyll 테마를 적용 중인 github repository를 찾아서 Fork해오고, 해당 repository setting에서 이름을 본인의 *{계정이름}.github.io* 로 수정해 주고, 저장하면, 본인의 주소로 똑같이 블로그 적용이 가능해진다.

### Jekyll 템플릿이 적용된 Github Page를 커스터마이징 하기
---------------

이제 Jekyll 구조로 된 소스를 차근차근 살펴보자.

**_config.yml**

: page 전반적인 설정정보를 담는다. 전역변수들이 대부분 선언되어 있다. 블로그 title, 이름, email, sns 주소, 블로그 main site path를 설정한다.

**_includes**

: footer, header 등 html flagment들

**_layout**

: page생성시 페이지 앞부분에 선언하여 선택하는 layout (jsp의 tile같은 느낌)

**_posts**

: markdown(.md) 등 블로그 글들이 저장되는 디렉토리

**_sass**

: css모음 (scss)

### Jekyll 템플릿이 적용된 Github Page에 추가기능 구현하기
---------------

템플릿마다 다르지만, 경우에 따라 여러 기능을 붙여주어야할 때가 있다.

- 댓글 기능 적용하기(Disqus - 사이트 가입 및 설정 필요)

- [검색 기능 적용하기](https://imyeonn.github.io/blog/blog/30/)

### Blog Posting 하기
---------------
~~~
---
layout: post
title: First Posting!
---
~~~

Posting은 _posts 폴더 내에 .md 파일을 추가해서, Commit해주는 방식으로 이루어진다.

윗부분에 나와있는 layout은 디렉토리에 있던 것중 1가지로 선택해야 , (없으면 default)
title은 layout내에 변수 매핑되어 사용된다.
