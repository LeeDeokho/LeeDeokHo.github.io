---
layout: post
title: "Programming Objective-C를 읽고 정리"
date: 2018-03-05 00:40:06
description: Programming Objective-C를 읽고 정리
tags: 
 - ios
comments: true
---


## 다형성, 동적 타이핑, 동적 바인딩

`다형성`은 다른 클래스의 객체들이 동일한 메서드 이름을 사용할 수 있도록 해준다.
<br>
`동적 타이핑`은 객체가 속한 클래스를알아내는 단계를 프로그램이 실행될 때로 미룬다.
<br>
`동적 바인딩`은 객체에 호출되는 실제 메서드를 알아내는 시기를 프로그램 실행 중으로 미룬다.


### 다형성 - 동일한 이름, 다른 클래스

### 동적 바인딩과 id형

Fraction Class와 Complex class에 같은 이름의 print라는 메서드가 있다고 하자.

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
#import "Fraction.h"
#import "Complex.h"

int main(int argc, char *argv[]) {

    @autoreleasepool {
        id dataValue;
        Fraction *f1 = [[Fraction alloc] init];
        Complex *c1  = [[Complex alloc] init];

        [f1 setTo: 2 over: 5];
        [c1 setReal: 10.0 andImaginary: 2.5];

        dataValue = f1;
        [dataValue print];

        dataValue = c1;
        [dataValue print];
    }

    return 0;
}

/*
출력 결과 
2/5
10 + 2.5i
*/

{% endhighlight %}

dataValue가 어떤 클래스의 print를 호출 하는 지 어떻게 알 수 있을까 ??
Objective-C 시스템이 언제나 객체가 속한 클래스를 알고 있다는 사실에 숨어 있다.
또한, 동적 타이핑과 동적 바인딩에도 답이 있다.
이 두 개념을 쓰면 시스템이 컴파일할 때가 아니라 런타임 시에 객체의 클래스가 무엇인지를 알아낸다. 그러므로 호출할 메서드가 무엇인지를 동적으로 알아내는 것이다.

### 컴파일 시기와 런타임 확인

컴파일할 때는 id 변수에 저장된 객체의 데이터 형을 정확히 알 수 없기 때문에 일부 테스트를 런타임 시기, 즉 프로그램을 실행할 때까지 미루게 된다.

### id 데이터 형과 정적 타이핑

`정적 타이핑`은 특정 클래스의 객체로 변수를 정의하는 것
정적 이라는 말은 변수가 언제나 그 특정 클래스를 저장하는 데만 사용된다는 의미.
정적타이핑을 사용하면, 컴파일러는 프로그램에서 변수를 일관성 있게 사용해 최고 성능을 내게 한다. 컴파일러는 객체에 적용되는 메서드가 그 클래스에 의해 정의되거나 상속되었는지를 확인할 수 있고, 그렇지 않은 경우에는 경고 메시지를 표시한다. 
정적타이핑을 사용하는 이유는 프로그램의 `가독성`을 높여주기 때문이다.



## 카테고리와 프로토콜

### 카테고리
- When ? 
    - 클래스 정의를 다루는 도중에 새 메서드를 추가하고 싶을 때
- What ?
    - 클래스 정의를 그룹 짓기
    - 연관된 메서드를 묶어 쉽게 모듈화할 수 있게.
    - 원본 소스코드에 접근하거나 서브클래스를 생성하지 않고도 현존하는 클래스의 정의를 쉽게 확장하는 방법도 제공

- Example
    - Fraction 이라는 클래스에 add, mul, sub, div라는 메서드를 추가하고 싶다고 하자.
    >OBJECTIVE-C
    {:.filename}
    {% highlight swift %}
     #import "Fraction.h"
    @interface Fraction (MathOps)
    // 이 코드는 컴파일러에게 Fraction 클래스의 새 카테고리로 MathOps를 정의한다고 알린다.
    - (Fraction *) add: (Fraction *) f;
    - (Fraction *) mul: (Fraction *) f;
    - (Fraction *) sub: (Fraction *) f;
    - (Fraction *) div: (Fraction *) f;
    @end
    
    {% endhighlight %}

### 클래스 확장
- When ?
    - 숨겨진(private) 메서드를 만들 때 유용
    - 클래스를 작성할 때, 클래스 자신만 접근할 수 있는 데이터와 메서드가 필요할 때
- What ?
    - 카테고리를 () 사이에 아무 이름 없이 사용하는 특수한 경우
    - 추가 인스턴스 변수를 정의해 확장할 수 있다.
    - 이름 없는 카테고리에 선언된 메서드는 분리된 구현 부분이 아니라 클래스의 메인 구현 부분에 구현된다.

### 카테고리를 사용할 때 주의 사항
- 메서드를 재정의한 후에 원래 메서드에 접근할 방법이 없어진다.
- 클래스에 카테고리로 새 메서드를 추가하면, 해당 클래스뿐 아니라, 서브클래스에도 영향을 준다.
- 특정 객체에 대한 카테고리 이름은 반드시 유일무이해야 한다.


### 프로토콜
- 클래스 사이에서 공유되는 메서드 목록
- 프로토콜에 나열된 메서드들은 해당하는 구현 부분이 없다.

- 프로토콜의 정의

    >OBJECTIVE-C
    {:.filename}
    {% highlight swift %}
    @protocol NSCopying
    - (id)copyWithZone: (NSZone *) zone;
    @end
    {% endhighlight %}
    
- 프로토콜을 받아들인다고 알려주려면 아래와 같이 프로토콜의 이름을 <>로 감싸면 된다.

    >OBJECTIVE-C
    {:.filename}
    {% highlight swift %}
    @interface AddressBook: NSObject <NSCopying>
    {% endhighlight %}
    
- 만일 여러개의 프로토콜을 받아들인다면 <> 안에 쉼표(,)로 구분해서 나열하면 된다.
    >OBJECTIVE-C
    {:.filename}
    {% highlight swift %}
    @interface AddressBook: NSObject <NSCopying, NSCoding>
    {% endhighlight %}
    
- 프로토콜을 직접 정의하더라도 구현할 필요는 없다.
- 한 클래스가 NSCopying 프로토콜을 따른다면, 서브클래스도 이 프로토콜을 따른다.

- @optional 지시어를 사용하면, 이 지시어 다음에 위치하는 메서드들은 선택 사항이다. 또한 @required를 다시 사용하면, 필수 메서드 목록을 다시 작성할 수 있다.
    >OBJECTIVE-C
    {:.filename}
    {% highlight swift %}
    @protocol Drawing
    - (void) paint;
    - (void) erase;
    @optional
    - (void) outline;
    @end
    {% endhighlight %}
    
- 어떠한 객체가 프로토콜에 따르는지를 알아보려면 conformsToProtocol: 메서드를 사용하면 된다.
    >OBJECTIVE-C
    {:.filename}
    {% highlight swift %}
    id currentObject;
    ...
    if ( [currentObject conformsToProtocol: @protocol (Drawing)] == YES)
    {
        // currentObject에 paint, erase, outline 메시지를 보낸다.
    }
    {% endhighlight %}
    
- 프로토콜을 두 클래스 간의 `인터페이스`라 생각해도 된다.

### 델리게이션

- 프로토콜을 정의하는 클래스가 프로토콜의 메서드로 정의된 일을 메서드를 구현하는 클래스에게 위임하는 것

- 이런 식으로 특정 이벤트의 응답으로 취하는 특별한 동작이나 특정 속성을 정의하는 등의 일을 델리게이트 클래스가 처리하면, 클래스를 더 일반적으로 정의할 수 있다.


## 하부 C언어 기능

### 블록

- 함수와 비슷하게 생겼고 동작도 유사하다.

- 함수와 달리 함수나 메서드 안에서 정의할 수도 있고, 자식ㄴ과 동일한 범위에 있다면, 블록 바깥에서 정의된 변수에도 접근 가능하다. 

- 보통은 블록 바깥에 정의된 변수의 값을 변경하는 것은 불가능 하지만, `__block`을 사용하면 블록 내에서 이런 변수의 값을 수정할 수 있다.


>OBJECTIVE-C
{:.filename}
{% highlight swift %}
void printMessage (void) {
    NSLOg(@"Programming is fun.");
}

// 이라는 함수를 블록 코드로 바꾸면 아래와 같이 된다.

^(void) {
    NSLOg(@"Programming is fun.");
}

// 또한 블록을 printMessage라는 변수에 대입할 수도 있다.
// 블록을 변수에 대입할 때는 변수를 제대로 선언해줘야 한다.

void (^printMessage) (void) = 
    ^(void) {
        NSLog(@"Programming is fun.");
    } ;

// 변수로 참조한 블록은 함수와 동일한 방식으로 실행할 수 있다.
printMessage ();
{% endhighlight %}

### 함수 포인터

- 선언

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
// int형을 반환하고 인수를 받지 않는 함수의 포인터라고 가정
int (*fnPtr) (void);

// 함수 이름을 대입하면 된다.
fnPtr = lookup;

{% endhighlight %}

- 함수포인터는 흔히 다른 함수의 인수로 건네는 식으로 사용된다.


## 숫자, 스트링, 컬렉션

구조체와 같은 데이터 형을객체로 변환하는 과정을 `래핑`이라고 부른다.

## 메모리 관리와 ARC

>메모리 관리는 사용하지 않는 메모리를 정리해(재활용해) 다시 사용할 수 있게 하는 것.

>만일 객체가 더는 사용되지 않으면, 그 메모리를 재사용하도록 하자. 사실 말을 쉽지만, 누군가가 언제 객체가 더 이상 사용되지 않아 객체가 차지하고 있는 메모리 공간을 재사용할 수 있는지를 결정해야 한다는 것.

>이 수고를 덜기 위해 몇몇 메모리 관리 기법이 개발되었는 데, 그중 두개는 자동화된 방법이다. 컴퓨터가 객체를 추적해 필요에 따라 메모리를 해제한다. 세번째 방법은 하이브리드 접근법을 택한다.

> 자동래 레퍼런스 카운팅(Automatic Reference Counting) 혹은 ARC라는 기능이 추가됨에 따라 프로그래머가 메모리 관리에 대해 더는 신경 쓸 필요가 없어졌다. 

> Objectrive-C 개발자가 사용 가능한 메모리 관리 모델은 세 가지가 존재한다.
>1. 자동 가비지 컬렌션
>2. 수동 레퍼런스 카운팅 및 오토릴리스 풀
>3. 자동 레퍼런스 카운팅(ARC)

>Objective-C 2.0 부터는 자바에서 사용되는 `가비지 컬렉션`이라는 기법으로 메모리 관리를 할 수있지만, Max OS X 프로그램을 개발할 때만 이 기법을 쓸 수 있다. 가비지 컬렉션을 사용하기로 결정했다면, Xcode로 프로그램을 빌드할 때 이 기능을 켜줘야     한다. 프로그램이 구동되는 동안, 메모리 부족 상태에 들어가고 시스템이 메모리 청소를 해야 한다고 결정하면 가비지 컬렉션이 일어난다. 이 작업은 프로세서를 상당히 많이 잡아먹느 일이다. 

### 수동 레퍼런스 카운팅

>객체가 생성되면 초기 레퍼런스 카운트가 1로 설정된다. 매번 객체가 지속되도록 해야 할 때마다 레퍼런스 카운트를 1씩 증가시켜 참조를 생성하게 된다. 이 작업은 다음과 같이 `retain` 메시지를 객체에 보내 수행한다.

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
[MyFraction retain];
{% endhighlight %}
>더 이상 객체가 필요하지 않으면, release 메시지를 보내 레퍼런스 카운트를 1씩 줄여준다.

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
[MyFraction release];
{% endhighlight %}

> 객체의 레퍼런스 카운트가 0이 되면, 해당 객체가 더 이상 사용되지 않음을 시스템이 알 수 있다.(이론상으로, 애플리케이션의 어디서도 참조하지 않음을 의미하기 때문이다.) 그래서 해당 객체가 차지하고 있던 메모리 공간을 해제한다. 이 과정은 객체에 `dealloc` 메시지를 보내 처리한다. 만약 내가 만든 클래스에서 NSArray 객체를 인스턴스 변수로 가지고 있고 이 객체를 alloc으로 생성했다면, 내가 만든 클래스의 dealloc을 재정의해서 객체가 제거될 때 배열도 릴리스해줄 책임을 지게한다.

> 수동 레퍼런스 카운팅을 사용할 때는, Foundation 프레임워크의 몇몇 메서드가 객체의 레퍼런스 카운트를 증가시킬 수 있음에 주의해야 한다. 예제로, NSMutableArray의 addObject: 메서드로 객체를 배열에 추가하거나, UIView의 addSubview: 메서드로 뷰를 추가하면 레퍼런스 카운트가 증가한다. 반대로 감소시키는 메서드들도 존재한다.

> 객체가 파괴된 뒤에(레퍼런스 카운트가 0이 되어 dealloc이 호출된 뒤에), 그 객체를 참조하는 것은 유효하지 않다. 이런 참조를 종종 `길 잃은 포인터(dangling pointer) 참조`라고 한다. 

### 객체 참조와 오토릴리스 풀

> 먼저 객체를(alloc으로) 생성하고 그 객체를 반환하는 메서드를 작성해야 한다고 하자. 메서드는 객체 사용을 마쳤지만 그 객체를 반환해줘야 하므로 릴리스할 수 없다. `NSAutoreleasePoll` 클래스는 이런 문제를 해결하기 위해 만들어졌다. 이후에 릴리스해야 할 객체를 오토릴리스풀이라는 객체에 담아 관리한다. 이후라는 시점은 이 풀에 drain 메시지를 보내 풀이 드레인되는 때다.<br>객체를 오토릴리스 풀이 관리하는 객체 목록에 추가하려면 다음과 깉이 객체에 autorelease 메시지를 보낸다.

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
[result autorelease];
{% endhighlight %}

>Foundation, UIKit, AppKit 프레임워크의 클래스를 사용할 때는 이들 프레임워크의 클래스들이 오토릴리스된 객체를 생성하고 반환해줄 수 있으므로, 반드시 오토릴리스 풀을 생성해야 한다. 

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
NSAutoreleasePool * pool = [[NSAutoreleasePool allc] init];
{% endhighlight %}
> <br>풀을 다 사용했으면 drain 메시지를 보낸다.

>OBJECTIVE-C
{:.filename}
{% highlight swift %}
[pool drain];
{% endhighlight %}

>사실 alloc, copy, mutableCopy, new 라는 이름으로 시작하는 메서드로 생성된 객체는 오토릴리스되지 않는다. 이런 경우 그 객체를 소유하는 것이다. 객체를 소유하면 그 객체를 다 사용한 뒤에 객체가 사용한 메모리 공간을 릴리스해줄 책임이 있다. 이는 객체에 release 메시지를 보내 처리하거나 혹은 autorelease 메시지를 보내 오토릴리스 풀에 더할 수도 있다.

### 이벤트 루프와 메모리 할당 

> 코코아와 iOS애플리케이션은 런 루프(run loop) 혹은 이벤트 루프(event loop) 라는 것 안에서 동작한다.

> 이벤트는 사용자가 (iPhone 버튼을 누르는) 특정 액션을 취하거나 (네트워크로부터 데이터를 받거나 하는) 암묵적인 액션에 따라 발생하는 무언가다. 새 이벤트를 처리하려면, 시스템은 오토릴리스 풀을 새로 생성하고 프로그램에서 처리할 수 있도록 몇몇 메서드를 호출할 것이다. 이벤트 처리를 완료하면 여러분의 메서드가 반환하고, 시스템은 다음 이벤트가 발생하길 기다린다. 그러나 시스템은 그전에 먼저 오토릴리스 풀을 뺀다. 이벤트 처리 과정에서 생성한 오토릴리스된 객체는 따로 리테인하지 않았다면 제거될 것이다. 수동 레퍼런스 카운팅을 사용할 때는 오토릴리스 풀과 이벤트 루프가 끝날 때 풀이 빠지는 상황에서 만들어놓은 객체를 생존시킬지 여부를 생각해야 한다. 

### 자동 레퍼런스 카운팅(ARC)

> 자동 레퍼런스 카운팅은 수동 레퍼런스 카운팅의 잠재적인 함정을 모두 제거해준다. 내부적으로는 레퍼런스 카운트를 여전히 관리하고 추적한다. 

### strong 변수

> 기본적으로 모든 객체 포인터 변수는 `strong` 변수이다. 이 말은, 이런 변수에 객체를 대입하면 자동으로 리테인한다는 것이다. 게다가 참조한 이전 객체는 대입 전에 릴리스된다. 마지막으로, strong 변수는 기본적으로 0으로 초기화된다. 인스턴스 변수든, 로컬 변수든, 글로벌 변수든 모두 0으로 초기화된다. 

### weak 변수

> 때로 두 객체 사이에 서로 참조하는 관계를 만들어야 할 때가 있다(간단히 두 객체 사이의 관계일 수도 있고, 순환 구조를 만드는 객체의 연쇄 구조일 수도 있다.)

> 예를 들어, iOS 애플리케이션을 뷰라는 객체로 홤녀상에 그래픽을 표시한다. 뷰는 계층 구조로 관리된다. 따라서 하나의 뷰는 이미지를 표시할 수 있고, 이 이미지 뷰 안에 미지의 제목을 표시할 수 있다. 이때 이미지 뷰를 메인 뷰로 설정하고, 제목은 서브 뷰로 설정할 수 있다. 메인 뷰가 나타나면 서브 뷰도 자동으로 보여진다. 메인 이미지 뷰를 부모 뷰로 보고 제목 뷰를 자식 뷰로 생각할 수 있을 것이다. 메인 뷰가 나타나면 서브 뷰도 자동으로 보여진다. 메인 이미지 뷰가 서브 뷰를 소유하는 개념이다.이 뷰 구조를 다룰 때, 부모 뷰는 자신의 서브 뷰의 참조를 쥐고 있고 싶을 것이다. 그런데 서브 뷰 입장에서도 자신의 부모 뷰가 누군지 알면 굉장히 편리할 것이다. 따라서 부모 뷰는 서브 뷰의 참조를 갖고, 서브 뷰도 자신의 부모 뷰의 참조를 갖게 된다. 이런 순환 참조는 문제를 야기할 수 있다. 예컨대 부모 뷰를 파괴하면 어떻게 되겠는가? 서브 뷰의 부모 뷰 참조가 더 이상 유효하지 않게 된다. 사실, 존재하지 않는 부모 뷰에 접근하려 하면 애플리케이션이 강제 종료 될 것이다.








