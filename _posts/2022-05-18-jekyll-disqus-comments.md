---
layout: post
title:  "Jekyll Blog에 Disqus 무료 댓글 추가하기"
date:   2022-05-18 07:21:00 +0900
categories: Github 블로그 프로젝트
Tags : ["jekyll"]
---

## Disqus란?
**Disqus**는 네트워크 커뮤니티 플랫폼으로 소셜 네트워크 통합하여 댓글 시스템을 제공한다. Jekyll Github Pages 블로그에 댓글 기능을 추가하는 방법은 여러가지가 있지만 이 글에서는 Disqus를 이용하여 무료로 댓글 기능 추가하는 방법에 대하여 기술한다.

## 1. Disqus 가입하기
[Disqus](https://disqus.com)에 접속하여 Get Started 버튼을 클릭하고 Signup에 이름, 이메일, 비밀번호를 입력하여 가입해준다.

## 2. Disqus 댓글 만들기
  - **I want to install Disqus on my site**를 선택하고 *Website Name*를 입력한다.
  - **Plan**은 무료인 **Basic**으로 선택하고 **platform**은 **Jekyll**을 선택한다
  - **Configure**에서 **Website URL**에는 https://*username*.github.io 형식의 Github Blog 주소를 입력한다.
  - **Style**은 **Balanced**는 게스트 계정으로 댓글을 달 수 있고 **Strict**는 로그인한 사용자한테만 댓글작성 권한이 주어진다. 각자 필요에 따라 선택을 한다.

## 3. Jekyll과 Disqus 연동하기
_include/disqus_comments.html 파일을 아래와 같은 내용으로 추가해준다.
```html
{%- if page.comments != false and jekyll.environment == "production" -%}

  <div id="disqus_thread"></div>
  <script>
    var disqus_config = function () {
      this.page.url = '{{ page.url | absolute_url }}';
      this.page.identifier = '{{ page.url | absolute_url }}';
    };

    (function() {
      var d = document, s = d.createElement('script');

      s.src = 'https://{{ site.disqus.shortname }}.disqus.com/embed.js';

      s.setAttribute('data-timestamp', +new Date());
      (d.head || d.body).appendChild(s);
    })();
  </script>
  <noscript>Please enable JavaScript to view the <a href="https://disqus.com/?ref_noscript" rel="nofollow">comments powered by Disqus.</a></noscript>
{%- endif -%}
```

_layouts/post.html 파일에 content 부분 다음에 다음과 같은 코드를 삽입한다.
```ruby
  {%- if site.disqus.shortname -%}
    {%- include disqus_comments.html -%}
  {%- endif -%}
```

_config.yml 에 다음 코드를 추가한다.
```yml
# Disqus Comments
disqus:
    # Leave shortname blank to disable comments site-wide.
    # Disable comments for any post by adding `comments: false` to that post's YAML Front Matter.
    shortname: mathematike # Disqus에서 설정한 shortname

url: "https://mathematike.github.io" # Github Blog 접속 주소
```

## 4. Github 블로그에 Push하기
수정을 하였다면 `commit`하고 `push`해주고 잠시 기다리자. 이제 블로그에 접속하여 Disqus 댓글창이 보이는지 확인한다.
