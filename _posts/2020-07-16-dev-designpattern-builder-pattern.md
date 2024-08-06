---  
layout: post  
title: "[Design Pattern] 빌더 패턴이란?"  
subtitle: "DesignPattern"  
categories: DesignPattern
tags: Dev Java 기술 DesignPattern BuilderPattern
comments: true  
header-img: null
---  

안드로이드 앱 개발 공부를 하면서 예제에서 많이 접했던 방법이었으나, 정확히 이것이 빌더패턴인지는
모르고 있었는데 "스프링 부트와 AWS로 혼자 구현하는 웹 서비스" 책을 읽다가 명확히 알게 되었다.


### 빌더패턴이란?

자바 또는 안드로이드 공부를 하다보면 구글링을 할 때 한번씩은 꼭 봤을 것이다. 빌더패턴과 비교되는 대상은 
여러가지가 있겠지만, 책에서는 생성자를 통해 소개했다.

```java
Example.builder()
	.a(a)
    	.b(b)
    	.build();
```

```java
public Example(String a, String b)
{
	this.a = a;
    this.b = b;
}
```

이 두가지의 차이점은 무엇일까??

만약 개발자가 new Example(b,a) 처럼 a와 b의 위치를 변경해도 코드를 실행하기 전까지는
문제를 찾을 수 없다는 것이다.

하지만 빌더 패턴을 사용하면, 위의 예제와 같이 어느 필드에 어떤 값을 채워야 하는지 명확하게 인지할 수 있다!