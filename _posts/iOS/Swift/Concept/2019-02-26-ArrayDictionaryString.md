---
layout: post
title: "Array, Dictionary and String"
date: 2019-02-24 00:30:06
description: Array, Dictionary, String에 대하여 정리
tags: 
 - iOS-Swift
comments: true
---

## Array

>Swift
{:.filename}
{% highlight swift %}

var a = Array<String>()
... is the same as ...
var a = [String]()

let animals = ["Giraffe", "Cow", "Doggie", "Bird"]
animals.append("Ostrich") // want compile, animals is immutable (because of `let`)

 let animal = animals[5] // crash (array index out of bounds)

// enumerating an Array
for animal in animals {
    println("\(animal)")
}


{% endhighlight %}

### Interesting Array<T> methods
> This one creates a new array with any "undesirables" filtered out
> The function passed as the argument retuns false if an element is undesirable

> Array에서의 연산을 하기위해 클로져를 사용한다. `filter`는 Array에 있는 메소드인데, Array에 있는 무슨 타입이든 받아서 Bool을 반환하는 클로져를 제공한다. 그리고 Array의 모든 요소마다 클로져를 실행한다. 클로져와 일치하는 것만 들어있는 새 Array를 filter가 반환할 때까지 계속된다.


>Swift
{:.filename}
{% highlight swift %}

filter(includeElement: (T) -> Bool) -> [T]

let bigNumbers = [2, 47, 118, 5, 9].filter({ $0 > 20}) // bigNumbers = [47, 118]
{% endhighlight %}

> map은 클로져를 받고 클로져는 Array 안에 있는 각 요소들을 다른 것으로 바꿔버린다.
> map 뒤에는 위의 filter처럼 {} 바깥으로 소괄호가 보이지 않는다. `클로져가 함수의 마지막 인자일 때는 이 소괄호들은 넣어도 되고 빼도 된다.`

>Swift
{:.filename}
{% highlight swift %}

map(transform: (T) -> U) -> [U]

let stringfield: [String] = [1, 2, 3].map { String($0) }

{% endhighlight %}

> Reduce는 Array를 하나의 결과로 줄일 수 있다.
> 

>Swift
{:.filename}
{% highlight swift %}

reduce(initial: U, combine: (U, T) -> U) -> U

let sum: Int = [1, 2, 3].reduce(0) {$0 + $1} // adds up the numbers in the Array

{% endhighlight %}

## Dictionary

>Swift
{:.filename}
{% highlight swift %}

var pac10teamRanking = Dictionary<String, Int>()
... is the same as ...
var pac10teamRankings = [String: Int]()

pac10teamRankings = ["Stanford":1, "Cal":10]
let ranking = pac10teamRankings["Ohio State"] // ranking is an Int? (would be nil)

// use a tuple with for-in to enumerate a Dictionary

for (key, value) in pac10teamRankings {
    print("\(key) = \(value)")
}

{% endhighlight %}


## String

> Swift에서는 String이 전부 유니코드이기 때문에 복잡하다. 전체 유니코드는 모든 종류의 언어를 지원한다. (하나의 문자가 정말 많은 코드가 될지도 모르는 언어들도 포함함
> 문자 하나는 더이상 하나의 코드가 아니다. String에 문자단위로 순서를 매길 때 Int로 나타내지 않는 이유다. 



>Swift
{:.filename}
{% highlight swift %}

var characters: String.CharaterView {get} // 문자의 배열처럼 보이는 문자들을 가져온다. 하지만 그렇게 보이는 거지 사실은 그렇지 않다.
// 하지만 Int로 찾을 수 있고 문자를 가져올 수 있다.

{% endhighlight %}

### Other String Methods

>Swift
{:.filename}
{% highlight swift %}

startIndex -> String.Index
endIndex -> String.Index
hasPrefix(Stringl) -> Bool
hasSuffix(String) -> Bool
capitalizedString -> String
lowercaseString -> String
uppercaseString -> String
componentsSeparatedByString(String) -> [String] // "1,2,3".csbs(",") = ["1", "2", "3"]

{% endhighlight %}

## Other Calsses

### NSObject

> 모든 Objective-C 클래스들의 기본 클래스
> Swift에서는 의무적으로 기본클래스를 가지지 않아도 된다. 

### NSNumber

> Objective-C에서의 구조체는 스위프트의 구조체와 같지않다.(멋진 값 타입 형태가 아니다.)
> ObjC의 구조체는 C언어에서의 구조체와 더 비슷하다.
> NSNumber는 원시 타입을 객체 안에 포장하기 위한 방법이다. 



>Swift
{:.filename}
{% highlight swift %}

let n = NSNumber(35.5)
let intversion: Int = n.intValue // also doubleValue, boolValue, etc.

{% endhighlight %}


### NSDate

> UI에 날짜를 넣기를 원한다면 매우 주의해야한다. 날짜는 온 지구상에서 다른 방법으로 표현되기때문에. 
> Date 클래스는 이 방법에 대해서 모두 알고 있다.


### NSData

> bag o'bits다.
> 데이터를 전달할 때 사용한다. (때로는 네트워크 상에서 이미지 데이터 같은 것들을)