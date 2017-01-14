---
layout: post
title: "Jekyll와 Github로 blog 만들기"
description: "Jekyll Theme(Chalk)로 github page를 만들어 블로그를 시작했습니다"
tags: [writing, jekyll, development]
---

2013년, 개발공부를 시작하면서 네이버 블로그에 배운 내용을 기록하다가, 그 후에 일을 시작하면서 하지 못했다. 
계속 새로운 블로그를 만들어야겠다고 생각만하다가 이제 다시(사실 처음) 블로깅을 시작하려고 합니다.  
팀장님 추천으로 github page를 알게되고, 검색하다가 jekyll를 알게되고, chalk라는 테마를 적용하여 시작합니다.

첫 포스트로서 간단하게 과정을 적어보자면 
(mac 사용)

## rvm, ruby 설치 
(mac에는 원래 ruby가 설치되어 있지만, theme별로 요구하는 ruby version이 달라서 재설치)

#### rvm 설치
<a href="http://bigmatch.i-um.net/2013/12/%EB%A9%98%EB%B6%95%EC%97%86%EC%9D%B4-rvm%EA%B3%BC-%EB%A3%A8%EB%B9%84-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0/" >rvm, ruby 설치참조</a>

{% highlight bash %}
\curl -L https://get.rvm.io | sudo bash -s stable
{% endhighlight %}
(쉘 껐다 키고)
{% highlight bash %}
sudo adduser [username] rvm 
{% endhighlight %}
(쉘 껐다 키고) 
#### ruby 설치
저는 2.3.1을 설치했습니다. 
{% highlight bash %}
rvm install [ruby-version]
{% endhighlight %}


## Jekyll (chalk theme)
<a href="https://github.com/nielsenramon/chalk">chalk theme</a>
에서 fork받은 페이지를 clone

{% highlight bash %}
sudo git clone https://github.com/taejaehan/chalk.git
{% endhighlight %}
README에 있는데로 ruby, npm을 설치(확인)하고 
bin/setup 파일실행한 후
{% highlight bash %}
bundle exec jekyll serve
{% endhighlight %}
로컬에서 잘 돌아가는 것이 확인되면 github page에 올리기

- bin/deploy 파일을 실행하면 github page에서 돌아갈 수 있는 branch(gh-pages)를 만들어줍니다
- github에 파일이 올라간 것을 확인 후 setting에서 branch(gh-pages)를 source로 선택.
custome domain을 설정하고 좀 기다리면 확인 가능 
- circleci를 사용하면 local에서 master만 push하면, git에서 merge가 되면 bin/deploy파일을 실행하여 자동으로 branch를 다시 만들어 줄 수 있습니다.

git도 익숙하지 않고 jekyll도 처음해봐서 오래 걸렸습니다. 앞으로 글을 올리면서 구조를 좀 더 custom하게 다듬어야 할 것 같습니다.

