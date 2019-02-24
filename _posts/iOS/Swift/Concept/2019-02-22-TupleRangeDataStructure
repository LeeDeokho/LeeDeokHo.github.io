---
layout: post
title: "Tuples, Range, Data Structure"
date: 2019-02-22 00:30:06
description: Tuples, Range, Data Structure에 관해 정리
tags: 
 - iOS-Swift
comments: true
---

## Tuple이란?

> Tuple은 스위프트의 타입 중 하나
> 서로 다른 타입들을 그룹으로 묶어서 하나의 타입을 만든다. 타입이 들어갈 자리라면 튜플을 어디에서든 사용할 수 있다.

>Swift
{:.filename}
{% highlight swift %}

let x: (String, Int, Double) = ("hello", 5, 0.85)
let (word, number, value) = x // tuple elements named when accessing the tuple
print(word) // prints hello
print(number) // prints 5
print(value) // prints 0.85

... or the typle elements can be named when the tuple is declared ...

let x: (w: String, i: Int, v: Double) = ("hello", 5, 0.85)
print(x.w) // prints hello
print(x.i) // prints 5
print(x.v) // prints 0.85

... added ... // 두가지 방식을 혼합해서 사용해도 된다.

let (wrd, num, val) = x // this is also legal(renames the tuple's elements on access)

{% endhighlight %}

> 타입이름에 튜가 들어가 있어서 2개만 들어갈 것 같지만, 몇개가 되었든 튜플에 들어갈 수 있다.
> 튜플은 함수에서 여러개의 값을 반환할 수 있기때문에 활용성이 좋다. 

>Swift
{:.filename}
{% highlight swift %}

func getSize() -> (weight: Double, height: Double) { return (250, 80) }

let x = getSize()
print("weight is \(x.weight)") // weight is 250
... or ...
print("height is \(getSize().height)") // height is 80

{% endhighlight %}

> 튜플에서 어떤 값을 무시하고 싶다면 `_`를 사용하면 된다.

## Range란?

> A Range in Swift is just two end points.
> 무엇이든 연속적으로 표현될 수 있는 것의 양 끝 점을 가르킨다.
> Range는 Array처럼 일반화된 타입이기때문에 Int로 된 Range나 무언가의 인덱스로 된 Range도 될 수 있다.
> 개념적으로 startIndex와 endIndex 두 개가 있다.


>Swift
{:.filename}
{% highlight swift %}

struct Range<T> {
    var startIndex: T
    var endIndex: T
}

{% endhighlight %} 

> Array의 Range를 구하려고 한다면 Int로 된 Range가 될 것이다. (Range<Int>)(Array는 Int 타입으로 요소가 구별된다.)
> 참고로, String의 Range는 Int가 아니다. 
> Range<Int>와는 다른 Range<String.Index> 이다.
> 옵셔널처럼 특별하게 ? 와 !가 있는 데, Range를 표현하는 특별한 구문이다.
> `...` 아니면 `..<` 기호이다. 

>Swift
{:.filename}
{% highlight swift %}

let array = ["a", "b", "c", "d"]
let subArray1 = array[2...3] // subArray will be ["c", "d"]
let subArray2 = array[2..<3] // subArray2 wiil be ["C"]
for i in 27...104 {} // Range is enumeratable, like Array, String, Dictionary

{% endhighlight %} 

## Data Structures in Swift

### Classes, Structures and Enumerations 

### Similarities

#### Class, Struct, Enum이 비슷한 점은 모두 똑같은 방법으로 선언이 된다.
* 키워드 + 이름 + {} 구조이다.
  
>Swift
{:.filename}
{% highlight swift %}
// Declaration syntax ...

class CalculatorBrain {

}
struct Vertext {

}
enum Op {

}
{% endhighlight %}

#### 모두 프로퍼티와 함수를 가질 수 있다.
* 다만 enum은 저장 프로퍼티를 가질 수 없다.
    * enum은 계산 프로퍼티는 가질 수 있다.
    * enum이 기억하고 있는 저장소는 case다.
>Swift
{:.filename}
{% highlight swift %}

// Properties and Functions ...
func doit(argument: Type) -> ReturnValue {

}

var storeProperty = <initial value> (not enum)

var computeProperty: Type {
    get {}
    set {}
}

{% endhighlight %}

#### Initializers (again, not enum)
* enum만 제외하고 초기화함수를 가질 수 있다.
    * enum은 연관값을 구별되는 값들에 할당을 해주었기 때문에 초기화함수를 가질 필요가 없다.


>Swift
{:.filename}
{% highlight swift %}

init(argument1: Type, argument2: Type, ...) {

}

{% endhighlight %}

### Differences

#### Inheritance (class only)
* 클래스에선 상속할 수 있고, struct나 enum에선 불가능하다. 

#### Value type (struct, enum) vs. Reference type (class)
* struct와 enum은 값으로 전달되는 값 타입
* class는 참조 타입으로 포인터(메모리 주소)로 전달 (힙 메모리(동적으로 할당되는 메모리)에 있다.

#### Value vs. Reference

> Value (struct and enum)
* 값타입은 함수에서 인자로 전달될 때 복사된다는 점은 명백하다.
* 다른 변수에 할당할 때도 복사를 한다. (단지 할당하는 것도 복사가 된다.)
    * ex) ```var x = y```에서 y가 값타입이라면 x는 y를 복사한 값이다.
* 값타입 개념은 let 변수에 할당한 경우 값을 바꿀 수 없다.
    * Array가 하나 있다면 Array는 구조체니까 값 타입이다.
* function parameters는 constants이다.
* 구조체나 enum이 바뀔지도 모른다면 `mutating` 표시를 해준다.
    * mutating func (이 함수가 구조체를 바꿀수 있는 경우)
* Swift가 복사를 하려고 할 때는 실제로 복사를 하지 않는다.
    * 다른 포인터를 갖고 있다가 값이 바뀌려고 하자마자 그때 복사가 된다. (성능 향상을 위한 절차)

> Reference (class)
* 힙메모리에 저장되어 있다가 참조를 준다. 그 참조는 자동으로 카운트된다. (Swift에는 Gerbage Collection이 없다)
    * 힙에 있는 무언가에 새로운 포인터를 생성할 때마다 Swift가 알아서 추적하고 카운트한다.
    * 그러다가 카운트가 0이 되면(마지막으로 참조하던 포인터가 영역을 벗어났다던가, 마지막 포인터를 다른 걸 가리키기 위해 할당했다던지) 즉시 힙 메모리에서 제거된다.
    * 이 과정에 참여할 수 있는 유일한 방법이 weak와 strong이다. 
* 클래스에 상수 포인터가 있다면 분명히 포인터니까, 여전히 바꿀 수 있다.
    * 구조체인 경우 var y = x에서 y에 무언가를 더해주어도 x 값이 바뀌지 않는다.
    * 똑같이 var y = x 인데, x가 클래스라면, y에 메시지를 보내면 x에게도 보내진다.(같은 것이니까)
        * 힙메모리에 동일한 포인터로 있고, 복사를 하지 않았기 때문에.
        * 모든 let의 뜻은 포인터가 변하지 않을 거라는 것을 뜻한다.(포인터가 가리키는 것이 변하지 않는다는 의미가 아니다.)
* 포인터를 인자로서 클래스에 전달하면, 복사하지 않고 포인터를 전달한다.

> 어느 것을 사용할 지 ?? (Value와 Reference 중에) (enum은 꽤 분명하지만, 구조체와 클래스 중에 고민이 될 것이다.)
* 대부분 구조체보다는 클래스를 더 많이 사용하게 된다. 
    * 객체지향 프로그래밍이니까 클래스를 쓰던 대로 쓰면 된다.
* 반면, 구조체는 더 근본적인 타입으로 사용된다.
    * String, Double, Int, Array, Dictionary같은 타입이나, 그림을 그리기위한 점, 직사각형 등등 ...)
    * 클래스보다는 더 작고 스스로 자립하며, 값으로 복사되는 게 말이 되고 값 타입을 원하는 영역들에서 사용된다.










