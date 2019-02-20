---
layout: post
title: "Objective-C를 읽고 정리2"
date: 2018-07-16 21:12:06
description: Objective-C를 읽고 정리
tags: 
 - ios
comments: true
---

# 목차 

- [Objective-C 프로그램](#Objective-C-Program)
- [PKPushType](#pkpushtype)
- [VoIP Push](#voip-push)
- [What's New in the Apple Push Notification Service](#what's-new-in-the-apple-push-notification-service)
- [Local and Remote Notifications Overview](#local-and-remote-notifications-overview)
- [Managing Your App’s Notification Support](#managing-your-app’s-notification-support)
- [Configuring Remote Notification Support](#configuring-remote-notification-support)

---

# Objective-C Program

## 객체와 메시지
### 메시지 셀렉터(셀렉터)
> 함수가 함수명으로 식별되는 것처럼 메시지는 키워드를 메시지명으로 사용해서 가른 메시지와 구분한다. 이것을 메시지 셀렉터 혹은 셀렉터(selector)라고 부르고 메소드명이라고도 부른다. 인수가 있는 경우 `:`도 메시지 셀렉터의 일부로 간주된다. 즉 아래의 예에서 copy와 copy:는 서로 다른 메시지 셀렉터이다.

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
copy
retain
firstResponder
copy:
objectAtIndex:
cellAtRow:column:
{% endhighlight %}

> 메시지에 인수가 필요한 경우, 메시지 키워드 전체가 영어 문장으로 자연스럽게 읽히도록 기술하는 것이 관례이다. 인수가 여러 개 있을 때는 메시지 키워드의 각 인수가 어떤 의미인지 파악하기 쉽도록 표현해야 한다. 

### 인스턴스의 생성과 초기화
> id 타입의 변수를 선언만 했다면 아직 아무런 객체도 할당되지 않은 상태이다. 객체에게 어떤 처리를 하게 하려면 먼저 클래스에서 인스턴스를 생성할 수 있어야한다. 

> [클래스명 alloc]

> 이렇게 생선된 인스턴스는 메모리에 필요한 공간을 확보만 한 상태이기 때문에 이 객체를 사용하려면 먼저 초기화부터 해야 한다. 초기화를 하기 위한 메소드를 이니셜라이져(initializer)라고 부르기도 하고, 초기화 메소드라고 부르기도 한다. 클래스에 따라 이니셜라이저 역할을 하는 메소드가 다를 수 있고, 한 클래스가 두 개 이상의 이니셜라이저를 가질 수도 있다. 
Cocoa 환경에서 이니셜라이저의 이름은 `init`이거나 `init`로 시작하는 것이 관례이다. 클래스에서 인스턴스를 생성하기 위해서는 아래와 같은 메시지 표현식을 사용한다.

> [[클래스명 alloc] init]

> 한 가지 주의할 것은 초기화 과정이 인스턴스의 정보를 리셋하는 것이 아니라는 것이다. 이니셜라이저에 의한 초기화는 처음 인스턴스가 생성된 직후에 단 1회 수행된다. 정보를 리셋해야 하는 경우, 즉 인스턴스의 변수값을 초기화하는 것이 필요하다면 이니셜라이저를 사용하지 않고, 별도의 메소드를 사용해야 한다.

---

## 클래스 정의

### 클래스 인터페이스
> Objective-C에서는 클래스를 인터페이스와 구현으로 분리해서 기술한다. 인터페이스에서는 클래스의 인스턴스 변수와 메소드를 선언한다. 이 인터페이스는 헤더 파일 역할을 해서 그 클래스를 사용하려는 모듈은 이 인터페이스를 참조해야 한다. 인터페이스의 기술은 아래와 같다.

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
@interface 클래스명: 슈퍼 클래스명
{
    인스턴스 변수 선언;
    ...
}
메소드 선언;
...
@end
{% endhighlight %}

> 클래스명은 C언어에서의 변수 명명법을 따르는 데 첫 글자는 대문자로 사용하는 것이 관례이다. 클래스명은 변수명이나 함수명과 같으면 안된다. 
슈퍼 클래스에는 보통 NSObject를 넣는다. 