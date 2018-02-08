---
published: true
layout: post
date: '2018-02-08 14:09 +0900'
categories: jekyll
postname: '[INFO] 지킬 블로그 커스터마이징 사항'
tags: info
---
## 서론

> 내 블로그는 지킬 테마 + 깃허브 + Prose.io 서비스를 통해 일반 블로그처럼 편하게 포스팅하고 관리할 수 있도록 만들었다. 

> 바탕화면을 정리하다가 블로그 관련 커스터마이징 사항을 정리해둔 텍스트가 있어서 저장해 두려고 한다.

## 기본 참조 테마

- 링크 : https://gaohaoyang.github.io/

## 커스텀 목표

> 기술 블로그이므로, 커스터마이징을 할 때 가장 중요시 한 부분은 `내가 원하는 정보를 찾으러 와서 쉽게 찾고 쉽게 얻어갈 수 있는가` 였다. 두번째로는, 내가 많이 귀찮아하기 때문에, `바로 포스팅이 가능한가?` 였는데, 삽질을 통해 두가지 목표를 어느정도 얻어낼 수 있었다.

## 커스터마이징 사항

**@Setting**

- deokudev.github.io로 수정

**@config.yml**

- 사이트 셋팅
- SNS 계정
- disqus 계정

> 구글 애널리틱스 삽입 필요

- prose 속성 추가
- title 관련으로 속성 변동 필요.

**@index.html(가장 앞에 HOME 화면)**
- 소개글 수정
- 우측에 카테고리/태그 순서 변경, Category 콘텐츠 추가
- ReadMore 부분을 없애고, Recent Post로 대체
- 카테고리 밑에 부분 추가

**@includes/header.html(위에 헤더 수정)**
- logo.png 에셋 폴더 업로드

**@includes/footer.html(위에 헤더 수정)**
- 바닥글 수정

**@sass/index.scss**
- Recent 레이아웃 겹치는 것 방지 수정

**@검색기능 추가**
- 검색에서 Page 제외 작업

**@검색기능 구글 추가(googlesearch)**

**@favicon.ico 추가**

**@Collections / demo 임시 제거**
- page 폴더 내에서, type:page 속성을 default로 바꾸어줌

**@카테고리 수정**

**@Post 관련 수정**
- Post Layout에서 추가
