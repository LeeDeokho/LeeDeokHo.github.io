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

```objectiveC
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

```

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
    ```ObjectiveC
    #import "Fraction.h"
    @interface Fraction (MathOps)
    // 이 코드는 컴파일러에게 Fraction 클래스의 새 카테고리로 MathOps를 정의한다고 알린다.
    - (Fraction *) add: (Fraction *) f;
    - (Fraction *) mul: (Fraction *) f;
    - (Fraction *) sub: (Fraction *) f;
    - (Fraction *) div: (Fraction *) f;
    @end
    ```

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
    ```objectiveC
    @protocol NSCopying
    - (id)copyWithZone: (NSZone *) zone;
    @end
    ```
- 프로토콜을 받아들인다고 알려주려면 아래와 같이 프로토콜의 이름을 <>로 감싸면 된다.
    ```objectiveC
    @interface AddressBook: NSObject <NSCopying>
    ```

- 만일 여러개의 프로토콜을 받아들인다면 <> 안에 쉼표(,)로 구분해서 나열하면 된다.
    ```objectiveC
    @interface AddressBook: NSObject <NSCopying, NSCoding>
    ```

- 프로토콜을 직접 정의하더라도 구현할 필요는 없다.
- 한 클래스가 NSCopying 프로토콜을 따른다면, 서브클래스도 이 프로토콜을 따른다.

- @optional 지시어를 사용하면, 이 지시어 다음에 위치하는 메서드들은 선택 사항이다. 또한 @required를 다시 사용하면, 필수 메서드 목록을 다시 작성할 수 있다.
    ```objectiveC
    @protocol Drawing
    - (void) paint;
    - (void) erase;
    @optional
    - (void) outline;
    @end
    ```
- 어떠한 객체가 프로토콜에 따르는지를 알아보려면 conformsToProtocol: 메서드를 사용하면 된다.
    ```objectiveC
    id currentObject;
    ...
    if ( [currentObject conformsToProtocol: @protocol (Drawing)] == YES)
    {
        // currentObject에 paint, erase, outline 메시지를 보낸다.
    }
    ```

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


## Foundation Framework

