---
layout: post
title:  Jekyll 테마와 Github을 이용해 Netlify 블로그 만들기(1) - 설치, 준비
date:   2021-04-17 14:55:09 GMT+0800
image:  '/images/01/01jekyllbackground.jpg'
tags:   [jekyll, netlify, blog]
---

![Beautiful place]({{site.baseurl}}/images/01/01jekyllbackground.jpg)
*Jekyll official site / [Jekyll](https://jekyllrb.com/)*

내 블로그의 첫 글을 <a href="https://jekyllrb.com/">Jekyll</a> 테마와 <a href="https://github.com/">Github</a>을 이용하여 <a href="https://www.netlify.com/">Netlify</a> 블로그 빌딩하는 방법을 써보려고 한다. 나는 평소 글을 자주 쓰는 편도 아니고 기술 블로그를 쓰는 개발자도 아니지만 디자인, 코드, Three.js에 관한 글들을 한데 모아서 note taking 하고싶어서 블로그를 시작하기로 결정했다.<br>Velog, Medium 등을 이용 하고 있지만 굳이 블로그를 직접 만들고 싶었던 이유는 디자이너로서 내 스타일을 반영 할 커스터마이징이 가능 한 플랫폼이 필요했다. 또, 기존의 내 포트폴리오 사이트를 합칠 하이브리드 웹 사이트가 필요하기도 했다. 사실 무엇보다도 새로운것에 삽질하는 것을 좋아한다.<br>+ 내가 Netlify로 호스팅을 하게 된 이유는 Github에서는 Jekyll 테마의 플러그인 사용이 제한됐기 때문이다.

## 비개발자, 초보자도 Github 블로그를 만들 수 있을까?
깃헙이 익숙하지 않은 사람들에게는 과정이 조금 어려울 수 있다. 하지만 여러 다큐멘테이션, 블로그를 보고 차근 차근 따라 만드실 수 있습니다. jekyll를 사용해본 적이 없고, 블로그를 찾아 삼만리를 헤매는 분들을 위해 이 블로그는 한글로 작성 할 예정이다. Netlify에서 작성 된 <a href="https://www.netlify.com/blog/2020/04/02/a-step-by-step-guide-jekyll-4.0-on-netlify/#step-2-link-to-your-github">설명</a>을 참고 할 수 있다.

## 1. Ruby, Jekyll 설치하기
축하한다 앞으로 커맨드 지옥을 맛보게 될것이다. Jekyll를 installing 하기 앞서 먼저 Ruby를 설치하여 환경을 만들어야 한다. 터미널을 열어 아래의 명령어를 타이핑 해 루비의 버전을 확인한다.

{% highlight js %}
$ ruby -v
{% endhighlight %}

터미널에 아래의 커맨드를 입력하여 Jekyll를 설치한다. 만약 루비가 설치 되어 있지 않다면 루비를 먼저 설치하고 아래의 단계를 진행한다.
{% highlight js %}
$ gem install jekyll
{% endhighlight %}

Jekyll가 로컬에 디렉토리를 만들고 필요한 파일들을 설치할 명령어를 입력한다
{% highlight js %}
$ jekyll new PATH/TO/project
{% endhighlight %}

cd 커맨드를 이용하여 생성된 디렉토리로 이동하자
{% highlight js %}
$ cd PATH/TO/project
{% endhighlight %}

자, 이제 명령어를 입력해 로컬 서버를 띄워 볼까?
{% highlight js %}
$ jekyll serve
{% endhighlight %}

여기까지 했으면 반은 다 한거다. locally deployed가 완료 된거다.

## 2. bundle 설치하기
Netlify를 이용하여 deploy 하기 위해서는 Git 레파지토리에 호스팅을 해야한다. 깃 레파지토리를 생성하기 이전에 프로젝트 디렉토리로 가서 아래의 명령어로 bundle을 설치한다.
{% highlight js %}
$ bundle init
$ bundle install
{% endhighlight %}

## 3. Github 레파지토리 생성하기

* 새로운 레파지토리 만들기

이제 Github에서 새로운 repository를 만들자. 아래 이미지 처럼 new repository를 눌러 만든다. 혹시 모를 에러를 예방하기 위해서 README 파일은 일단 생성하지 않도록 한다.
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01new_repo.jpg">
  </div>
</div>

* 새로운 레파지토리 이름 작성

<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01creatingrepo.jpg">
  </div>
</div>

* 프로젝트에 깃 생성하기

생성한 레파지토리의 주소를 아래의 사진처럼 클론한다
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01gitclone.jpg">
  </div>
</div>

터미널에서 내 블로그 폴더의 _site 디렉토리로 이동하여 아래의 명령어들을 차례대로 입력해서 로컬 깃을 생성한다.
{% highlight js %}
$ git init
{% endhighlight %}
{% highlight js %}
$ git add .
{% endhighlight %}
{% highlight js %}
$ git commit -m 'First commit'
{% endhighlight %}

{% highlight js %}
$ git remote add origin [클론한 내 repository URL]
{% endhighlight %}

remote 연동이 됐는지 확인하기 위해 아래의 명령어를 입력해보자.
{% highlight js %}
$ git remote -v
{% endhighlight %}

여기까지 잘 됐다면 아래의 명령어로 마스터 브랜치로 push를 해서 변동 사항을 commit한다
{% highlight js %}
$ git push -u origin master
{% endhighlight %}

<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01commandline.jpg">
  </div>
</div>
Push가 성공적으로 됐다면 내 깃헙 레파지토리에 이렇게 폴더들이 업데이트 된 걸 볼 수 있을것이다.
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01gitpushed.jpg">
  </div>
</div>
이제 거의 다 됐다! Netlify와 연동만 하면 된다 이제.

## 4. Netlify에 깃헙 연동하기
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01netlifylogin.jpg">
  </div>
</div>
이제 <a href="https://www.netlify.com/">Netlify</a> 사이트에서 가입, 로그인을 한 뒤 아래 초록 버튼을 눌러 내 깃과 Netlify를 연동시킨다.
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01netlify.jpg">
  </div>
</div>
<a href="https://www.netlify.com/blog/2020/04/02/a-step-by-step-guide-jekyll-4.0-on-netlify/#step-2-link-to-your-github">여기</a>를 눌러 세팅 방법을 볼 수 있다 6가지 스텝으로 쉽게 따라 할 수 있으니 참고한다.
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01mydomain.jpg">
  </div>
</div>
짜잔, 이제 Jekyll를 이용한 블로그가 만들어진 셈이다! 테마 적용 전의 기본 모습은 저렇다.


## 5. Jekyll 테마 고르기
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01jekylltheme.jpg">
  </div>
</div>
🔗<a href="https://jekyllthemes.io/">https://jekyllthemes.io/</a><br><br>
구글에 jekyll테마 검색하면 정말 많은 테마들이 있다. 무료도 있고 유로도 있는데 나는 블로그 + 포트폴리오를 합친 형태로 커스터마이징 할 생각이여서 좀 더 내 입맛에 맞는 걸 찾다보니 유로 테마를 구매했다.

## 6. Jekyll 테마 내 블로그에 적용하기
자 이제 내가 고른 테마를 내 블로그에 적용시키기만 하면 끝난다. 개발에 대한 지식이 있는 상태라면 여기까지가 정말 쉬웠겠지만...나는...코린이다. 테마 적용까지 4시간의 삽질을 했다; 이 글을 보고있는 누군가는 나보다 덜 삽질하길 바란다.
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01jekyllfolder.jpg">
  </div>
</div>
테마를 다운받으면 사용법 다큐멘테이션과 파일들이 있다. 적용법은 테마마다 다를 수 있으니 다큐멘테이션을 꼭 읽어보길 추천한다. 이제 다운받은 테마의 파일들을 카피해서 내 프로젝트 디렉토리에 던져버린다. 중복되는 파일이 있다. 당연함; 근데 알게 뭐람 그냥 대치 시킨다.
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01copyfiles.jpg">
  </div>
</div>

## 7. 변동 사항 Git Push로 업데이트 하기
이제 내 project에 덮어씌운 테마 파일들을 내 웹 서버에 적용시키기 위해서는 터미널에서 몇가지 커맨드를 입력하면 된다.

{% highlight js %}
$ git add .
{% endhighlight %}


{% highlight js %}
$ git commit -m 'commit message'
{% endhighlight %}

{% highlight js %}
$ git push origin master
{% endhighlight %}

축하한다. 이렇게 푸쉬를 끝냈다면 내 웹사이트에 테마 적용이 돼있을것이다. 난 닉아담스는 아니다.
<div class="gallery-box">
  <div class="gallery">
    <img src="/images/01/01myblog.jpg">
  </div>
</div>

## Congrats! Done! 뭐야 그럼 이제 끝났어요? 집에 가도 돼요?
아니오. 테마 적용 후, 커스터마이징과 깃 버전 관리의 난항에 빠져 괜히 깝쳤다...티스토리나 쓸 걸..이라는 생각을 하게 되는데... 커스터마이징과 Git 버전 관리, Branch 설정에 대한 포스트는 다음 포스트에 하도록 하겠다. 내 주말이 날아갔기 때문이다. 안녕히가세요.

