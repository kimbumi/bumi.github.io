---
layout: post
title:  Jekyll 테마와 Github을 이용해 Netlify 블로그 만들기(2) - 커스터마이징
date:   2021-04-19 15:55:09 GMT+0800
image:  '/images/03/03.jpg'
tags:   [jekyll, netlify, git, blog]
---

![Beautiful place]({{site.baseurl}}/images/03/03.jpg)
*Jekyll official site / [Jekyll](https://jekyllrb.com/)*

오늘은 Jekyll 테마 커스터마이징에 관한 포스트를 하겠다. 글을 쓰고 있는 지금도 커스터마이징이 100% 완성 되진 않았지만, 일단 미리 기록해두기로 한다.

## Jekyll 사이트 구조
![Beautiful place]({{site.baseurl}}/images/03/jekyll.jpg)
<br><br>
🔗<a href="https://jekyllrb.com/docs/structure/" target="_blank">https://jekyllrb.com/docs/structure/</a><br>
일단 Jekyll 테마를 수정하기 위해 디렉토리 구조를 보고 오자. 근데 나는 사실 대충 읽었다. 왜냐면 봐도 딱히 뭔소린지 모르겠다. 그리고 자신이 고른 테마의 설명을 읽어보도록 하자.


## 수정하기 이전에 Branch를 새로 만들자
![Beautiful place]({{site.baseurl}}/images/03/gitmanaging.jpg)
*Github repository*
나는 이전에 Github을 이용하여 포트폴리오 빌딩, 호스팅까지는 해봤지만 Git, Remote push, branch 관리에 관한 지식은 0이였다. 근데 이번에 지킬 블로그를 만들면서 배우고 사용 해 볼 수 있어서 신기했다.
* 코드 에디터에서 터미널을 열고 프로젝트의 루트 디렉토리로 이동한다
* Git을 생성하자

{% highlight js %}
$ git init
{% endhighlight %}

* 아래 커맨드를 입력해 새로운 브랜치를 생성한다

{% highlight js %}
$ git branch 새브랜치명
{% endhighlight %}

아래 명령어를 입력해 브랜치를 확인한다

{% highlight js %}
$ git branch
{% endhighlight %}

그럼 이렇게 현재 자신이 어느 브랜치에 있는지 알려줄것이다

{% highlight js %}
KimBumi$ git branch
* master
  ver2
{% endhighlight %}

깃헙 레파지토리를 확인해보면 새로운 브랜치가 리모트 생성된것을 볼 수 있다!
![Beautiful place]({{site.baseurl}}/images/03/gitbranch.jpg)
*Git new branch*


* 새로운 브랜치에서 수정을 진행한다
아래의 명령어로 새로운 방금 생성한 브랜치로 switch 한다.
{% highlight js %}
$ git checkout 브랜치명
{% endhighlight %}
그리고 수정 작업을 진행하면 된다.

* 로컬 서버 띄우기
아래의 명령어로 현재 자신이 있는 브랜치에서 로컬을 띄울 수 있다. 수정 중에 바로 바로 확인 할 수 있어 편리하다.

{% highlight js %}
$ bundle exec jekyll serve
{% endhighlight %}



## _config.yml 파일에서 기본적인 세팅
![Beautiful place]({{site.baseurl}}/images/03/default.jpg)
*Jekyll 테마 폴더의 파일들*
comfig.yml 파일을 에디터에서 열어보면 아래의 텍스트처럼 작성이 되어있다.
보통은 설명이 달려있을테니 설명을 따라 title, description 등을 수정하면 된다.


## 자, 이제 스타일을 커스터마이징 한다
CSS file이 아니라 🔗<a href="https://sass-lang.com/" target="_blank">Sass</a>로 스타일링이 되어있는데, 전에 사용 해본적은 없지만 기본적으로 HTML, CSS를 어느정도 할 줄 아는 사람이라면 보다보면 사이트가 어떻게 구성 되어 있는지 알 수 있을거다. 나는 이것 저것 눌러보면서 감으로 알아냈다.
<br>
Sass의 variable들을 수정하여 전체 컬러 스킴과 폰트를 변경하였다. 그리고 태그와 버튼 속성들이 있는 파일들을 찾고 찾아 변경하였다.

![Beautiful place]({{site.baseurl}}/images/03/stylebefore.jpg)
*변경 전*
![Beautiful place]({{site.baseurl}}/images/03/styleafter.jpg)
*변경 후*

포스트 페이지의 Sass 속성들도 변경해줬다.
![Beautiful place]({{site.baseurl}}/images/03/postbefore.jpg)
*포스트 페이지 변경 전*
![Beautiful place]({{site.baseurl}}/images/03/postafter.jpg)
*포스트 페이지 변경 후*

## 수정 완료 후
이제 수정이 어느정도 진행 됐다면
Git을 Push해야 내 웹페이지에 적용이 되겠지? 터미널을 다시 열어 변경 사항을 커밋하고 푸쉬하자

{% highlight js %}
$ git add .
{% endhighlight %}

{% highlight js %}
$ git commit -m 'commit-message'
{% endhighlight %}

{% highlight js %}
$ git push origin 푸쉬할 브랜치명
{% endhighlight %}

## 그 외 해야할 것
* 🔗<a href="https://disqus.com/" target="_blank">Disqus</a> 계정 만들고 Shortname _config.yml에서 설정하기
* Contact form 연동하기
* Mailchimp로 subscribing 연동하기
* 구글 서치 SEO 작업
<br>
블로그를 만들었다면 내 글이 어딘가 검색 되고 보여지길 바랄 것이다. 그래서 SEO를 최적화 해야하는데 이건 나도 전에 공부 해본적이 없어서 잘 모른다.. 일단 계정을 생성하고 몇가지 절차들을 거치면 되는데 지금 sitemap을 어떻게 처리하는지를 몰라서..;모르겠다
<br>
🔗<a href="https://analytics.google.com/" target="_blank">구글 애널리틱스</a>
<br>
🔗<a href="https://search.google.com/" target="_blank">구글 서치 콘솔</a>

## 글을 마치며...
며칠동안 Jekyll 블로그 작업 하면서.. 아니 그냥 있는 플랫폼 쓸걸 이라는 생각을 하긴 했다. 그리고..jekyll 테마가 그렇게 커스터마이저블 한것 같지는 않다. 이건 내가 ruby와 sass를 잘 몰라서 더 그렇겠지만. 생각보다 제한이 많은 느낌이다.
<br>
야호 이제 드디어 Three.js 공부 할 시간이 나겠다.