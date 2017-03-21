---
layout: post
title: "Javascript 상속"
description: "Javascript Type, 구조화, 코드재사용, 상속/prototype"
tags: [development, javascript]
published: false
---

## Javascript Type
- 수 (Number)
- 문자열 (String)
- 부울 (Boolean)
- 기호 (Symbol)
- 객체 (Object)
	* 함수 (Function)
	* 배열 (Array)
	* 날짜 (Date)
	* 정규식 (RegExp)
- 널 (Null)
- 정의되지 않음 (Undefined)

<br>


## Javascript 구조화

1.Object방식 

{% highlight html %}
var animal = {
	age : 2,
	move : function(){
		console.log('move');
	}
};

animal.move();

{% endhighlight %}

2.Function 리턴 방식
{% highlight html %}
var animal = function(){
	var age = 2;
	var move = function(){
		console.log('move');
	};
	return{
		age : age,
		move : move
	}
}

animal().move();

{% endhighlight %}

3.Function Prototype

{% highlight html %}
var animal = function(){
	this.age = 2;
	this.move = function(){
		console.log('move');
	};
};
animal.prototype.bark = function(){
	console.log('bark');
}
var tiger = new animal();
tiger.move();
tiger.bark();

{% endhighlight %}

## Javascript 상속

- Javascript는 java처럼 class기반의 언어가 아니다.
- 대신 모든 오브젝트는 다른 오브젝트를 가리키는 prototype이라는 내부링크를 가지고 있다. 
- prototype 내부링크가 연쇄적으로 연결되는 구조를 프로토타입 체인이라 부른다. (마지막 오브젝의 prototype은 null을 가리킨다.)

{% highlight html %}
function book(){} 

이라고 book함수가 정의되면 자동으로 book함수의 prototpye객체가 만들어지고 
book함수의 prototype속성은 새롭게 만들어진 prototype객체를 가리킨다.
prototype객체의 constructor속성은 A함수를 가리킨다.

book.prototpye (book함수의 prototpye객체)
book.prototype.constructor (book함수)
{% endhighlight %}

{% highlight html %}
var book1 = new book();

new연산자와 book함수를 통해 생성한 book1이라는 오브젝트는 book.prototpye 객체를 참조한다.
book1의 __proto__라는 숨은 속성은 book.prototpye객체를 가리킨다.
(book함수의 prototpye은 new book(); 를 통해 생성하는 모든 오브젝트의 원형이 된다.)
{% endhighlight %}

{% highlight html %}
book.prototype.getTitle = function(){
	return 'bible'
}

book의 prototype에 getTitle이라는 함수를 추가하면 

console.log(book1.getTitle())


'book함수를 통해 생성된 모든 오브젝트들은 book함수의 
prototpye에 대한 숨은 링크를 가지므로 
해당 prototpye에 접근하여 사용할 수 있다.'

'따라서 book의 prototpye에 정의된 코드를 
재사용 할 수 있고 객체 지향적인 프로그래밍이 가능해진다.'

{% endhighlight %}

프로토타입을 이용하여 코드를 재사용하는 방법은 
위에 처럼 new 연산자를 사용하는 방법과
Object.create()를 사용하는 방법이 있다.

(Object.create()이 현재 권장되고 있고 이미 많이 사용하고있지만, 현재 성능상으로는 new를 사용하는 방법이 더 빠르고 구조가 복잡해지지 않는다면 아직까진 new를 사용해도 문제가 없을 것이다. 따라서 이번 글에는 new를 이용한 방법만 쓰려고 한다)


## Apply, Call

function book(title, author){
	console.log(title);
	console.log(author);
}

function bibleBook(name, price) {
	//fun.call(thisArg[, arg1[, arg2[, ...]]])
	//book.call(this, name, price);
	
	//fun.apply(thisArg[, argsArray])
	book.apply(this, [name, price]);
}

var bible = new bibleBook('성경','15000');





