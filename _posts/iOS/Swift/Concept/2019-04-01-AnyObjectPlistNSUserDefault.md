---
layout: post
title: "AnyObject, Plist, UserDefaults"
date: 2019-04-01 00:30:06
description: AnyObject, Plist, UserDefaults에 대하여
tags: 
 - iOS-Swift
comments: true
---

# AnyObject

## AnyObject란 ??

> AnyObject는 특별한 타입이다. (실제로는 프로토콜이다)
> Objective-C와의 호환을 위해 사용된다.
> Objective-C에는 id라는 중요한 타입이있는 데, id는 모르는 클래스의 객체에 대한 포인터 주소를 말한다.
> AnyObject도 모르는 클래스의 객체에 대한 포인터 주소를 뜻한다.
> Swift에는 Any라고 하는 타입도 있는 데, 구조체든 클래스든 뭐든 될 수 있다.

## AnyObject를 어디서 보게 될까 ??

> 메소드 인자의 타입이 적어도 두개 이상 될 수 있을 때
> 아래의 예를 보면 `sender`는 버튼이 될 수도, 테이블의 한 행이 될 수도 있다. 

>Swift
{:.filename}
{% highlight swift %}

func prepareForSegue(segue: UIStoryboardSegue, sender: Anyobject)

{% endhighlight %}

> AnyObject를 사용하는 다른 예는 cookie(쿠키)를 반환하려고 할 때이다.
> 쿠키는 돌려받는 건데, 누군가한테 뭔가를 주면 그들은 그안에 뭐가 들어있는지 모르고 준사람도 말을 해주지않는다. 그냥 그대로 돌려받기만 하는거다. 쿠키는 상태를 저장하고 뭔가를 기억하고 있다가 돌려준다. 

>Swift
{:.filename}
{% highlight swift %}

var cookie: AnyObject

{% endhighlight %}

## AnyObject를 어떻게 사용할 수 있을까 ??

> AnyObject가 어떤 타입이 될지 모른다. 사용을 하려면 아는 타입으로 변환을 해주어야한다. 사실 이렇게 변환하는 건 불가능할 지도 모른다. (변환하려고 할 때 그 타입이 아닐 수도 있으니까).
> 그래서 Swift에서는 `as` 키워드를 사용한다. `as`는 다른 타입으로 변환하는 걸 `시도`하는 표현이다. as는 optional을 반환한다. 
> 기본적으로 AnyObject를 특정한 클래스로 `캐스팅`하는 것이다.

>Swift
{:.filename}
{% highlight swift %}

let ao: Anyobject = ...
if let foo = as as? SomeClass {
    // we can use foo and know that it is of type SomeClass in here
}

{% endhighlight %}

## AnyObject를 사용하는 또다른 곳은 Property List이다.

> Property List는 기본적으로 Array, Dictionary, String, Double, Int, NSData, NSDate의 조합으로 되어있다. 이 클래스들로 데이터 구조를 만들면 Property List가 생긴다.
> 그러나 AnyObject는 구조체가 아닌 클래스로만 캐스팅 되는 데, String, Array, Dictionary, Double은 구조체이다. 근데 어떻게 이것들이 AnyObject가 되어서 Property List에 들어갈 수 있을까?
> 답은 `브리징`이다. 
> 이것들이 Objective-C로 자동으로 브리징되고 자동으로 클래스인 NSDictionary, NSArray, NSNumber로 다뤄져서 AnyObject가 되도록 허락한다. 
> Property List는 보이지않게 전달된다. 그 안을 보는 사람들은 Dictionary, Array, String 같은 게 있다는 것만 알고 데이터가 무엇을 의미하는지는 아무것도 모른다. 
> 이해하기 쉽게 Property List를 사용하는 iOS의 API를 살펴보자. 

# NSUserDefaults

### Property List의 데이터를 위한 저장 메카니즘

> NSUserDefaults가 하는 일은 Property List를 받아서 디스크에 영구적으로 기억되게 만든다. 그래서 앱을 종료했다가 다시 켜서 봐도 그대로 존재한다. 기본적으로 Property List의 데이터 베이스인 셈이다. Dictionary, Array, String, Date 구조체의 데이터 모음이다. 
> NSUserDefaults는 작은 데이터베이스라서, 영어사전같이 영어 전체를 저장해야하는 큰 데이터에는 사용하면 안된다. `설정` 같은 작은 데이터에 적합하다. 

>Swift
{:.filename}
{% highlight swift %}

// It can store/retrieve entire Property Lists by name (keys) ...
setObject(AnyObject, forKey: String)
objectForKey(String) -> AnyObject?
arrayForKey(String) -> Array<AnyObject>? // returns nil if you setObject(not-an-array)

{% endhighlight %}

> 더 작게 저장하고 불러오는 것도 가능하다.
> 예를 들어 Double로 Property List를 하나 만들 수 있다.
> 왜냐면 Double 그 자체가 Property List이다. 


>Swift
{:.filename}
{% highlight swift %}

// It can also store/retrieve little pieces of data ...
setDouble(Double, forKey: String)
doubleForKey(Stringl) -> Double

{% endhighlight %}

### NSUserDefaults의 사용법

> 클래스 메소드 혹은 타입 메소드를 사용해서 공유해서 사용할 것을 새로 만든다. 
> 아래의 메소드를 사용하면 standardUserDefaults의 공유되는 인스턴스를 만들 수 있다.
> 그리고 특정한 Property List를 가져오도록해서 데이터를 수정하게 되면 자동으로 저장이 되지만 강제로 디스크에 저장하게 하고 싶다면 Bool값을 반환하는 동기화를 해줄 수 있다.
> 반환값은 거의 무시하게 된다 (실패했을 때 무엇을 해야할지 확실하지 않기 때문에)
> 아마 디스크가 꽉 차서 실패하거나 할텐데, 그 시점에 무엇을 해줘야 될지 명확하지않다. 대개는 반환값을 무시하면 된다.



>Swift
{:.filename}
{% highlight swift %}

// Get the defaults reader/writer ...
let defaults = NSUserDefaults.standardUserDefaults()

// Then read and wirte ...
let plist = defaults.objectForKey("foo")
defaults.setObject(plist, forKey:"foo")

// Your changes will be automatically saved.
// But you can be sure they are saved at any time by sunchronizing ...

if !defaults.synchronize() { // failed! but not clear what you can do about it }

// (it's not "free" to synchronize, but it's not that expensive either)

{% endhighlight %}


# Casting

### 캐스팅은 AnyObject에서만 쓰이는 것은 아니다.
> 어떤 클래스의 자식 클래스가 하나 있다고 하면 `as`를 사용해서 캐스팅해 볼 수 있다. 
> 자식 클래스인지 아닌지 확실치 않은 클래스로 캐스팅할 수 있고 as가 대신 자식 클래스인지 아닌지 말해준다. 
> 아래의 예를 보면 ...

>Swift
{:.filename}
{% highlight swift %}

let vc: UIViewController = CalculatorViewController()

{% endhighlight %}

> ViewController의 기본 클래스인 vc가 있다고 하면 vc.displayValue 라고 할 수는 없다. (displayValue는 CalculatorBrain것이라서)
> 하지만 여기에 as를 넣으면 (아래를 보자)
> 아래처럼 쓸 수 있다. as는 AnyObject외에도 쓰이는 것을 볼 수 있다.

>Swift
{:.filename}
{% highlight swift %}

if let calcVC = vc as? CalculatorViewController {
    lex x = calcVC.displayValue // this is okay
}

{% endhighlight %}


