---
layout: post
title: "Methods and Properties"
date: 2019-02-24 00:30:06
description: Methods와 Properties에 대하여 정리
tags: 
 - iOS-Swift
comments: true
---


# Methods

## Parameters Names 
> 함수에 들어가는 모든 parameter는 `internal`이름과 `external`이름이 있다.

> 아래 코드를 보면, 위에는 함수를 정의하는 부분이고, 아래는 호출하는 부분이다. 첫번째 파라미터, 두번째 파라미터가 있는데, 둘 다 외부 이름과 내부 이름이 있다. 외부 이름이 먼저오고, 내부 이름이 그 다음에 온다.

* Internal name
    * 메소드 내부에서 사용될 지역 변수의 이름
* External name
    * 메소드를 호출할 때 호출하는 사람이 사용하는 변수의 이름

> 함수를 호출할 때 주어진 파라미터에 external name을 전혀 사용하게 하고 싶지 않다면 `_`를 넣어줄 수도 있다. external name으로 `_`를 넣으면 external name이 보이지 않는다.
> 첫번째 파라미터에는 이게 기본값으로 되어있다. 첫번째 파라미터에는 `_`가 기본으로 설정되어 있어서 함수를 새로 만들 때 `_`를 넣어줄 필요가 없다. 기본값으로 `_`를 알아서 넣어준다.
> 다른 파라미터들은 기본값이 내부 이름이다.
> 모든 파라미터의 external name은 바꿀 수 있다.(두번째 파라미터의 external name을 _로 줘서 생략할 수 있다.) (하지만 Swift에 반하는 표현이므로 사용하지 않기를..)


> 위 내용은 Swift 2 기준이므로 현재 사용되는 4.0 이상 버전에서는 다르다.

>Swift
{:.filename}
{% highlight swift %}

func foo(externalFirst first: Int, externalSecond second: Double) {
    var sum = 0.0
    for _ in 0..<first {sum += second }
}

func bar() {
    let result = foo(externalFirst: 123, externalSecond: 5.5)
}

// ... external name을 사용하고 싶지 않다면 ...
func foo(_ first: Int, externalSecond second: Double) {
    var sum = 0.0
    for _ in 0..<first {sum += second }
}

func bar() {
    let result = foo(123, externalSecond: 5.5)
}

// ... 첫번 째 파라미터에는 _를 기본으로 넣어준다. ...
func foo(first: Int, externalSecond second: Double) {
    var sum = 0.0
    for _ in 0..<first {sum += second }
}

func bar() {
    let result = foo(123, externalSecond: 5.5)
}

// ... 두번째 파라미터의 외부 이름을 _ 로 줘서 두번째가 이름을 가지지 않게 할 수도 있다 ...
func foo(forcedFirst first: Int, _ second: Double) {
    var sum = 0.0
    for _ in 0..<first {sum += second }
}

func bar() {
    let result = foo(forcedFirst: 123, 5.5)
}


{% endhighlight %}


## Obviously you can override methods/properties in your superclass
> override란? 상위클래스에서 정의된 메소드와 프로퍼티를 재정의하는 것.
> 프로퍼티와 함수 모두 오버라이드할 수 있다.
> 프로퍼티와 메소드를 final로 표시할 수도 있다. (아무도 서브클래싱 하지 못하게.) (서브클래싱: 하위클래스에서 오버라이드 등을 통해 수정하는 것.)
> 범위를 넓혀서, 클래스 전체에 `override` 키워드를 붙이면 클래스 전체를 서브클래싱 할 수 없다.

## Both types and instances can have methods/properties 
> 타입과 인스턴스 모두 프로퍼티와 메소드를 가질 수 있다.
> 메소드와 프로퍼티를 타입 그 자체로서 가질 수도 있다. 

> 아래의 예제에서 d는 Double의 인스턴스이다. d는 특정값을 가지고 있는 실질적인 Double이다. 
> d가 - 부호를 가지고 있다면 Double의 타입 메소드를 사용하여 절대값으로 바꿔줄 것이다.

> 이런 타입 메소드는 보통 유틸리티 함수나 전역함수로 사용이된다. 클래스오 강하게 연관이 되어 있는 경우에 클래스 메소드로 넣어둔다.

>Swift
{:.filename}
{% highlight swift %}

var d: Double = ...
if d.isSignMinus {
    d = Double.abs(d)
}

// ... abs는 아마 이렇게 정의되어 있을 것이다 ...

static func abs(d: Double) -> Double

{% endhighlight %}

# Properties

## Property Observers

> 프로퍼티의 변화를 감시할 수 있다.
> willSet은 설정되기 전에, didSet은 설정된 후에 호출된다.
> newValue에는 willSet에서 새로 설정될 값이 들어가고, oldValue에는 didSet이 실행되면 전에 갖고 있던 값이 들어간다.
> 이 기능은 저장 프로퍼티나 상속된 프로퍼티에서 사용할 수 있다. + 계산 프로퍼티에서도 할 수 있다.

> willSet과 didSet으로 가장 많이하는 것은 UI를 업데이트하는 것이다.

>Swift
{:.filename}
{% highlight swift %}

var someStoredProperty: Int = 42 {
    willSet { newValue is the new value}
    didSet {oldValue is the old value}
}

override var inheritedProperty {
    willSet {newValue is the new value}
    didSet {oldValue is the old value}
}


// ... 아래에서는 willSet과 didSet은 값타입을 바꿔도 불리게 된다 ... 참조타입에는 해당되지 않는다 (클래스)
var operations: Dictionary<String, operation> = [...] {
    willSet { will be executed if an operation is added/removed }
    didSet { will be executed if an operation is added/removed }
}

{% endhighlight %}

## Lazy Initialization
> lazy initialization은 스위프트에서 약간 속이는 코드표현이다. 
> var가 늦게 초기화되도록 선언할 수 있다.

> 아래의 예에서 보면, 누군가가 brain에 요청하기 전까진 할당되지 않는다. 누가 이 brain에 메시지를 보내려고 한다든가, brain의 프로퍼티를 가져오려고 하면 그떄가 되어서야 초기화가 된다.

> myProperty를 보면, 직접 메소드를 호출해서 내 프로퍼티 중 하나를 초기화하려는데, 보통 lazy 키워드 없이는 잘못된 코드이다.
> lazy가 없어서 안되는 이유는, 전체적으로 초기화되기 전까지는 자신에게 메시지를 보내거나 모든 프로퍼티에 접근할 수 없다. 아래의 코드는 초기화의 일부일 뿐이니까 할 수 없다.

> someProperty를 보면 타입이 주어져 있고 클로져가 있다. 끝부분엔 소괄호가 붙어있고. 
> 이 코드의 의미는 클로져 안의 코드를 실행해서 someProperty를 초기화한다는 의미이다. myProperty와 비슷해 보이지만, 이건 클로져 안에 코드를 넣는 것이다. 무슨 메소드이든지간에 내 프로퍼티를 초기화하는 게 아니다. 
> 초기화의 일부분이기 때문에, 전체가 초기화되기 전에는 self로 아무것도 할 수 없다. 

> lazy를 편법코드라고 하는 이유는, lazy는 모든 변수가 초기화되어야만 한다는 요구조건을 충족시킨다. 그래서 이것들이 늦게라도 초기화된다고 해도, 모든 변수는 초기화되어야만한다는 규칙을 따라 초기화되고 있는 것이다. 

> lazy는 var에만 사용할 수 있다.

> lazy는 변수가 의존성에서 생기는 문제를 극복하는 데에도 쓰일 수 있다.
> 다른 변수에 의존하고 있는 변수 하나가 있다고 해보면, 둘 중 하나를 lazy로 만들어도 괜찮다. (lazy로 만든 변수가 미리 초기화된 변수를 부를거니까.)

>Swift
{:.filename}
{% highlight swift %}

lazy var brain = CalculatorBrain() // nice if CalculatorBrain used lots of resources

lazy var someProperty: Type = {
    // construct the value of someProperty here
    return <the constructed value>
}()

lazy var myProperty = self.initializeMyProperty()

{% endhighlight %}
