---
published: true
layout: post
date: '2018-01-11 13:57 +0900'
postname: '[개념/문법] 깃과 깃허브란 무엇인가?'
categories: github
tags: git why what how
---
* contents
{:toc}
## 서론

> 1. 왜 깃을 쓰는가?
> 2. 깃이란 무엇인가?
> 3. 깃은 어떻게 사용하는가?

## WHY?

> 프로젝트 수행 시 여러 버전을 유지하기 위해, 계속해서 복사본을 저장해두는 문제가 발생한다.

> 두명의 개발자가 동시에 같은 웹사이트 페이지를 가지고 작업한 후 업로드할 때, 누군가의 작업은 겹쳐쓰여지고, 지워지게 되는 문제가 발생한다.

> 깃은 같은 페이지에 각자의 수정사항을 각각 업로드할 수 있고, 깃은 두개의 복사본을 저장한다. 나중에 변경사항들을 병합할 수 있다. 모든 변경사항의 스냅샷을 저장하므로, 이전 시점의 어떤 버전으로 되돌리는 것이 가능하다.

> 명령어로 조작해야 하는 깃을 깃허브의 경우, [깃허브 소프트웨어](http://github.com/)를 통해 로컬에서 window style로 프로젝트를 관리할 수 있도록 돕는다.

> 깃이 모든 변경사항에 대한 스냅샷을 저장하기 때문에 어떤 데이터도 잃어버리지 않는다.

## WHAT?

> 깃은 프로젝트의 어떤 부분도 겹쳐쓰지 않게 프로젝트의 변경을 관리하는 버전관리 SW를 의미한다.

## How?

@ 가장 처음 시작하는 것이라면, git Bash에서 
$ git config --global user.name "깃허브 사용자이름"
$ git config --global user.email "깃허브 계정메일"

1. 가입 후 온라인 저장소(online repository)를 만들기
2. 온라인 저장소와 같은 이름의 로컬 저장소(local repository)를 만들기, 보통은 ~/ 기호를 통해, 로컬 컴퓨터 파일 구조의 최상위 단계에 만듬
(mkdir 명령어를 통해 폴더를 만들고, cd 명령어를 통해 폴더로 이동)
or 원하는 폴더에서 오른쪽 마우스 누르고 Git Bash Here 실행
3. 해당 로컬 저장소를 일반 폴더에서 git repository로 변경시켜줌, 해당 디렉토리는 Git-ready 상태가 되고, 깃 명령어를 입력 가능하게 된다.
```
git init
```
4. 해당 폴더 내에 원하는 파일을 생성하고, 프로그래밍 한다. 그러나, 깃 저장소가 파일들을 인식하지 못하고, 무시하는 상태(untracked)이다. 즉 git이 변화를 감시하지 않는 상태이다. 현재 깃 상태를 확인하자.
```
git status
```
5. 깃 저장소가 인식할 수 있도록 추가해준다. 추가된 파일, 수정된 파일, 제거한 파일 있으면 무조건 해당 파일을 다시 명령어를 입력한다.
```
git add 파일이름.확장자
```
6. 완료한 작업 또는 추가된 기능에 대해 commit(이력저장)을 통해 메세지와 함께 스냅샷, 체크포인트를 형성한다.
(cf) 커밋은 git이 현재 추적(tracked)하고 있는 파일중 staged 상태의 파일만 골라서 일기로 남기는 행위입니다.
(cf) 다만 수정된 파일이 있으면 반드시 다시 add해주어야 commit 기록에 저장된다.
```
git commit -m "Add file.확장자"
```
7. 로컬 깃 저장소가 깃허브 원격 저장소를 인식할 수 있도록 한다. 해당 주소의 온라인 저장소를 origin으로 지정한다.
```
git remote add origin https://github.com/깃허브사용자이름/myproject.git
```
8. 원격 저장소가 제대로 설정되었는지 확인한다.
```
git remote -v
```
9. 로컬 깃 저장소의 master branch의 변경사항을 원격 저장소에 올린다(push)
```
git push origin master
```

@ 커밋로그를 확인한 뒤 특정 시점으로 돌이키고, 해당 디렉토리로 가면, 현재 시점 파일이 아닌, 그 당시 디렉토리 구조로 복구되어 있어, 복구가 필요한 파일 확인
```
git log
git checkout [커밋아이디의 앞글자 여러개만 쓰기]
```
> 임시로 과거시점으로 돌아가 파일을 복구했지만, 현재 작업하고 있는 시점으로 되돌아가면 다시 사라지게 될 것이다.

@ 마지막 작업 시점으로 다시 돌아가서, 과거 파일을 현재 시점에 되살리자. 이것 또한 변경사항이니, add하고 commit 해주자.
```
git checkout master // 마지막 작업시점으로 돌아가자
git checkout [커밋아이디] [파일명.확장자]
```

@ 온라인 작업 요약
```
git clone https://github.com/KennethanCeyer/tutorial.git //원격저장소 파일을 가져옴
git pull origin master //소스 업데이트,커밋된 내용 가져오기(merge해줌)
git fetch origin master //소스 업데이트,커밋된 내용 가져오기

git push origin [브랜치명] // 생성한 브랜치를 원격 저장소에 등록
git push origin :[브랜치이름] // 삭제되었음을 원격저장소에 반영
```

@ 완전 reset하기
```
git reset 991ee8c --soft //기존 인덱스와 워킹트리는 유지
git reset 991ee8c --mixed //인덱스는 버리고, 워킹트리는 유지
git reset 991ee8c --hard //기존 인덱스와 워킹트리 전부 삭제

```

@ branch란?
- 기본은 master 브랜치라고 불리며, 필수로 제공되는 브랜치이다.
- master 또한 나무가 아니라 branch라는 것을 명심, 평행적 구조를 가짐
- 서로 다른 브랜치들은 같은 조상을 가지고 있다.
- 브랜치를 새로 만들려면..
```
git branch [브랜치 이름] // 보통 실험을 하기 위함
// master 기준으로 시행하면 해당 branch에 동일하게 같은 소스코드 적용
git checkout [브랜치 이름] // 새로운 branch에 접속
git checkout -b [브랜치 이름] // 브랜치를 생성과 동시에 체크아웃
(git checkout master 상태에서)
git branch -d [브랜치 이름] // 브랜치 삭제
```

@ Merge 방식

> master에서 sub branch를 하나 파서, 파일을 수정 후, 맘에 들었으면, 기존의 코드에서 제거된 부분은 사라지고, 겹치는 부분은 그대로이고, 추가된 부분은 추가된다.

```
$ git checkout -f master
$ git merge [subbranch이름]
$ git add *
$ git commit -m "Merge Subbranch" // commit해줌
```

## 요약
```
git config --global user.name "이름"
git config --global user.email "깃허브 메일주소" // 매번 물어보는 귀찮음을 피하기 위해 설정.

mkdir ~/MyProject   // 로컬 디렉토리 만들고
cd ~/myproject      // 디렉토리로 들어가서
git init            // 깃 명령어를 사용할 수 있는 디렉토리로 만든다.
git status          // 현재 상태를 훑어보고
git add 화일명.확장자  // 깃 주목 리스트에 화일을 추가하고 or
git add .           // 이 명령은 현재 디렉토리의 모든 파일을 추가할 수 있다.(추천) 모든 삭제/추가/변경 사항을 기록한다.
$ git add * -f        // ignore 파일 & 삭제한 파일 이력까지 커밋할 경우
$ git status          // 현재 다 staged 상태인지를 확인 후
git commit -m “현재형으로 설명” // 커밋해서 스냅샷을 찍는다.

$ git add *
$ git commit -m "바로 직전 commit 덮어씌우기" --amend

git remote add origin https://github.com/username/myproject.git // 로컬과 원격 저장소를 연결한다.
git remote -v // 연결상태를 확인한다.
git push origin master // 깃허브로 푸시한다.
```

### 깃허브의 추가 기능

1. 다른 사용자의 프로젝트를 자신만의 복사본으로 fork(clone)해올 수 있다.
2. PULL REQUEST 를 통해, 다른 사용자의 프로젝트에 해결책을 제안할 수 있다.

## 용어 정리
- Command Line(명령어 입력 프로그램) > [깃 프로그램(git bash)](https://git-scm.com/downloads) 설치 필요
- Repository(저장소)
- Version Control(버전관리)
- Commit(커밋) : 현 시점의 저장소의 변경 메세지와 함께 스냅샷을 찍는다.
- Branch(브랜치) : 일반적으로 작업자들은 메인 프로젝트의 브랜치를 따와서(branch off), 변경해서 자신만의 버전을 만들고, 메인 디렉토리 master에 브랜치를 merge한다.
- Pull origin : 리모트 저장소의 변경된 내용을 로컬 저장소에 적용하는 작업(브랜치 병합과 같은 병합이 발생한다.)
- Push origin : 내 로컬 저장소의 변경 내용을 리모트로 전송하는 작업

> 함께 작업하는 동료에게서 변경사항을 전송받으려면 리모트 저장소를 경유해야 한다.

## Commit할 때 Tip
1. 유의미한 최소단위로 커밋하라! ex) '각 음료 객체 추가', '전체 메뉴 리스트 추가', '장바구니 추가', '선택기능 추가'

> 주문시스템 전체를 완성해 놓고, 하나의 commit을 만들어서도, 그렇다고 하나의 class or method가 추가될 때마다 일일이 commit을 만들어서도 안된다.

> Test-Driven Developmnet : 원하는 동작에 대한 test 판정 code를 먼저 작성하고 해당 test를 통과할 수 있는 실제 code를 작성해 매우 짧은 사이클의 개발을 반복하는 것

2. 모든 commit은 빌드 및 동작 가능한 상태를 유지해야 한다

## 성공적인 Branch 전략
1. 가급적이면 브랜치 머지는 반드시 자신이 분기되어 나왔던 브랜치로만 하자.
2. Git-flow 모델을 따르라.

![gitmodel]({{site.baseurl}}/assets/post/2018-01-12/git-model.png)

### 깃의 단점
-  깃의 경우, 명령어를 통해 접근하고, 조작해야 된다는 번거로움이 있어, 좀더 쉬운 인터페이스를 가진 깃허브만 사용할 수 있기도 하다.

### Github, Bitbucket, SourceTree(GUI 기반)