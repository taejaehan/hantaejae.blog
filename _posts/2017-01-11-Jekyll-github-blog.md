---
layout: post
title: "Jekyll와 Github로 blog 만들기"
description: "Jekyll Theme(Chalk)로 blog page를 만들어 Github 페이지에 올려 블로그를 시작했습니다"
tags: [design, jekyll]
---

2013년 개발공부를 시작하면서 네이버 블로그에 배운 내용을 기록하다가, 그 후에 일을 시작하면서 새로운 블로그를 만들어야겠다고 생각만 3년... 그렇게 알아보던 중 github page를 알게되고 jekyll를 알게되고 그렇게 다시(사실 처음) 블로깅을 시작합니다. 

간단하게 과정을 적어보자면 (mac 사용)

### rvm, ruby 설치 
(mac에는 원래 ruby가 설치되어 있지만, theme별로 요구하는 ruby version이 달라서 재설치)

## rvm 설치
http://bigmatch.i-um.net/2013/12/%EB%A9%98%EB%B6%95%EC%97%86%EC%9D%B4-rvm%EA%B3%BC-%EB%A3%A8%EB%B9%84-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0/

{% highlight bash %}
\curl -L https://get.rvm.io | sudo bash -s stable
{% endhighlight %}

(쉘 껐다 키고)

{% highlight bash %}
sudo adduser [username] rvm 
{% endhighlight %}

(쉘 껐다 키고) 

## ruby 설치
저는 2.3.1을 설치했습니다. 

{% highlight bash %}
rvm install [ruby-version]
{% endhighlight %}

### jekyll 기본 테스트
https://jekyllrb.com/

{% highlight bash %}
gem install jekyll bundler
jekyll new my-awesome-site
cd my-awesome-site
bundle exec jekyll serve
{% endhighlight %}

### 테마가 들어있는 페이지

https://github.com/nielsenramon/chalk
에서 fork받은 페이지를 clone

{% highlight bash %}
sudo git clone https://github.com/taejaehan/chalk.git
{% endhighlight %}

#README에 있는데로 ruby, npm을 설치(확인)하고 
#bin/setup 파일대로 진행

{% highlight bash %}
bundle exec jekyll serve
{% endhighlight %}

로컬에서 잘 돌아가는 것이 확인되면 드디어 github page에 올리기

#bin/deploy 파일대로 진행 후 gh-pages로 checkout

git init
git remote add origin https://github.com/username/username.github.io.git
git add .
git commit -m "message"
git push origin master

github에 파일이 올라간 것을 확인 후, https://username.github.io/ 사이트 확인.
