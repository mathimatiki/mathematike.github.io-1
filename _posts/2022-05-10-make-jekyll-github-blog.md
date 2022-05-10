---
layout: post
title:  "Jekyll로 Github 블로그 만들기"
date:   2022-05-10 07:21:00 +0900
categories: Github 블로그 프로젝트
Tags : ["git", "jekyll"]
---
## Jekyll이란?

**Jekyll** 은 정적 사이트 생성기이다. 마크업 언어로 작성된 텍스트를 Jekyll 에 넘겨주면 레이아웃을 사용해 정적 웹사이트를 생성한다.

### 정적 웹 페이지
**정적 웹 페이지**(static web page), **플랫 페이지**(flat page, **스테이셔너리 페이지**(stationary page)는 저장된 그대로 사용자에게 전달된다.
모든 상황에서 모든 사용자에게 동일한 정보를 표시하며, 콘텐츠 타입이나 문서 언어의 협상(negotiate)을 위해 웹 서버의 현대적 기능에 종속된다.

### 동적 웹 페이지
**서버사이드 동적 웹페이지**(server-side dynamic web page)는 서버사이드 스크립트를 처리하는  애플리케이션 서버 "애플리케이션 서버")에 의해 통제되는 구조의  웹페이지이다. 서버 사이드 스크립트에서 파라미터는 클라이언트 사이드 처리의 구성을 포함하여, 새로운 모든 웹 페이지의 조합이 어떻게 처리되는지를 결정한다.
**클라이언트 사이드 동적 웹페이지**(client-side dynamic web page)는 로드될 때 브라우저에서 실행되는  HTML 스크립트를 사용하여 웹 페이지를 처리한다. 자바스크립트와 다른 스크립트 언어들은 수신된 페이지의 HTML이  "문서 객체 모델"(DOM)로 구문 분석하는 방식을 결정하며 로드되는 웹 페이지를 표출한다. 동일한 클라이언트 사이드 기법들이 동일한 방식으로 DOM을 동적으로 업데이트하거나 변경한다.

### Github Pages + Jekyll
정적 사이트 생성기인 Jekyll을 이용하여 Gihub Pages에서 무료로 호스팅할 수 있다. 기본적으로 *username*.github.io 무료 도메인도 제공된다. 물론 다른 도메인을 구하여 사용하는 것도 가능하다.

## 1. Github 가입하기
[github](https://github.com)에 접속하여 **Sign Up**을 클릭하여 회원가입을 진행한다.
인증받을 이메일 주소가 필요하다.
이미 회원가입을 한 경우에는 **Sing in**을 클릭하여 로그인한다.

## 2. fork하기
[Jekyll 테마](https://github.com/topics/jekyll-theme)에서 마음에 드는 테마를 선택하여 fork한 뒤, Settings에서 **Repository name**을 ***username*.github.io**로 변경한다.

## 3. Jekyll 설치

### 3-1-a. apt계열 (Debian이나 Ubuntu)
```sh
$ sudo apt-get install ruby-full
```

### 3-1-b. yum 계열 (CentOS, Fedora, RHEL)
```sh
$ sudo yum install ruby
```

### 3-1-c. 윈도우
[ruby 다운로드](https://rubyinstaller.org/downloads/)에서 다운로드 받아서 설치한다.

## 4. Git 설치

[git 다운로드](https://git-scm.com/downloads)에서 다운로드 받아서 설치한다.

## 5. Github Jekyll 연동
```sh
$ git clone https://github.com/username/username.github.io
$ cd username.github.io
username.github.io$ gem install bundler jekyll
username.github.io$ bundle exec jekyll serve
# => Now browse to http://localhost:4000
```

**http://localhost:4000**으로 접속하면 블로그 화면이 보인다. 빌드 과정에서 오류가 안 생기는지 화면이 어떻게 보이는지 미리 확인하고 업데이트할 수 있다.

## 6. 블로그 확인
블로그는 접속 주소는 *username*.github.io다. 로컬에서 수정하여 push 해주면 블로그가 업데이트 된다.
