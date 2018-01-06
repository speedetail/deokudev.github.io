---
published: true
layout: post
title: 혼자서 안드로이드 APP 기획부터 개발까지!
date: '2018-01-05 03:06 +0900'
categories: android
tags: speedetail tip
---

* content
{:toc}

## 모바일 앱 제작 프로세스
- 서비스 기획 (idea의 구체화, 세부기능)
- 어플리케이션 UI/UX 디자인 (design 시안)
- 서비스 개발 (app / server / system / db 설계)
- 출시/배포 (개발 마무리, 마켓 배포 및 홍보) + 디버깅

## 제작 후 운영 및 서비스
- 서비스 관리
- 유지보수
- 인프라 구축

## TODO
- 아이디어 구체화 (Target, Needs, Service)
- 기능 구체화 (기능 list)
- 주요 UI 구상 및 구체화 (디자인 철학에 따라 + 리스트,탭,배너,상단)
- 스토리보드 및 와이어프레임 그리기 (pencil,oven 앱 사용)

## 세부결정사항
- Android용 앱? or Iphone용 앱?
- 기기지원 범위 결정
- 기본 뼈대가 될 테마,Flatform 선정
- 주색상 & 보조색상 선정
> 기본 상태는 주색상, 강조는 더 진한 색상, 강조안할 부분은 더 연한 색
, 연한 색은 앱의 주요부분이 아닌 곳에 사용
- 아이콘, 기타 테마 이미지 리소스 선정
> 구글이 제공하는 기본 Material Icon을 쓰는 것이 제일 안전하고, 나머지에서는 반드시 저작권
 확인
- API 서버 개발이 필요한지의 여부를 결정 + 매우 중요!(개발비용과 운영)
- 사용자 데이터를 로컬에 저장할 것인가? 서버에 저장할 것인가?
- API 서버 개발하기

## 준비사항
- Material or Flat 테마 공부(문서 참조)

## 주의사항
- 항상 일관성을 유지해야 한다.
- 출시 시에 앱이 디버깅용이 아닌 출시용으로 빌드가 되었는지 확인
- 서버도 디버깅용으로 배포되었는지 확인

## Tip
- [이전 UI인 Holo UI를 커스텀할 수 있도록 도와주는 사이트](http://romannurik.github.io/AndroidAssetStudio/)
- 기본 디자인을 기반으로 만든 오픈소스 GUI 컴포넌트 라이브러리를 사용하면
, 품질향상에 도움이 된다. 만족하는 컴포넌트가 없으면 기본에 입각하여, 직접구현하기
- 최근에는 API 서버를 별도로 개발할 필요없이 손쉽게 구현하는 클라우드 서비스들이 등장해서,
Parse 서비스를 사용해 보라.
- 클라이언트 개발 시에는 꼭 형성관리 도구 사용하기! : Bitbucket
- 앱 개발시 다양한 버전에서 테스트할 때 쉽게 해결 가능: genymotion 
- 서버 API 개발 시에는 Node.js Python(Flask, Django)와 같은 언어로 빠르게, Restful API 서버 구현 가능
- REST API를 손쉽게 테스트할 수 있는 도구는 크롬의 확장도구인 Advanced REST client
- 서버에서 먼저 API 개발해놓아야 기본적인 비즈니스 로직에 따라 화면 로직을 구현하기 편리하다.
- 순서는 데이터모델링 API 설계이다.

## Knowledge
- 안드로이드는 하위 버전에서 Material Design을 구현해내도록 Support
Library를 지원해주지만 살짝 부족함
- 3rd Party 라이브러리로 Material Design을 구현 가능,완성도는 글쎄  

## 배운 곳
- [혼자서 모바일 앱 기획부터 개발까지](http://pjh445.blog.me/220673670493)
