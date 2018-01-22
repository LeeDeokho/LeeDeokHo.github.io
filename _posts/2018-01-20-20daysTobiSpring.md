---
layout: post
title: "토비의 스프링 정리 "
date: 2018-01-20 19:40:06
description: 토비의 스프링 정리
tags: 
 - spring
comments: true
---

# 토비의 스프링 책을 읽으면서 헷갈리는 부분을 조금씩 정리하는 글
---
앞으로 스프링에 관한 포스트를 올릴 태그입니다. 

---

## 1장. 오브젝트와 의존관계

### DAO?
Data Access Object의 약자로서 DB를 사용해 데이터를 조회하거나 조작하는 기능을 전담하도록 만든 오브젝트
<br>

### 리팩토링 
- 기존의 코드를 외부의 동작방식에는 변화 없이 내부 구조를 변경해서 재구성하는 작업 또는 기술.
- 리팩토링을 하면 코드 내부의 설계가 개선되어 코드를 이해하기가 더 편지고, 변화에 효율적으로 대응할 수 있다. 결국 생산성은 올라가고, 코드의 품질은 높아지며, 유지보수하기 용이해진다.
- 추천 저서 [리팩토링](마틴 파울러, 켄트 벡 공저)
<br>
### 원칙
- 객체지향 설계 원칙(SOLID)
    - SRP(The Single Responsibility Principle): 단일 책임 원칙
    - OCP(The Open Closed PRinciple): 개방 폐쇄 원칙
    - LSP(The Liskov Substitution Princple): 리스코프 치환 원칙
    - ISP(The Interface Segregation Principle): 인터페이스 분리 원칙
    - DIP(The Dependency Inversion Principle): 의존관계 역전 원칙


- 개방 폐쇄 원칙(OCP, Open-Closed Principle)
    - 깔끔한 설계를 위해 적용 가능한 객체지향 설계 원칙 중 하나
    - 클래스나 모듈은 확장에는 열려 있어야 하고 변경에는 닫혀 있어야 한다. 
    - 높은 응집도와 낮은 결합도
    - 높은 응집도
        - 응집도가 높다는 것은 하나의 모듈, 클래스가 하나의 책임 또는 관심사에만 집중, 불필요하거나 직접 관련이 없는 외부의 관심과 책임이 얽혀 있지 않으며, 하나의 공통 관심사는 하나의 클래스에 모여 있다.
        - 응집도가 높다는 건 변화가 일어날 때 해당 모듈에서 변하는 부분이 크다는 것으로도 설명 가능
    - 낮은 결합도
        - 낮은 결합도는 높은 응집도 보다 더 민감
        - 책임과 관심사가 다른 오브젝트 또는 모듈과는 낮은 결합도, 즉 느슨하게 연결된 형태를 유지하는 것이 바람직
        - 느슨한 연결관계를 유지한느 데 꼭 필요한 최소한의 방법만 간접적인 형태로 제공하고, 나머지는 서로 독립적이고 알 필요도 없게 만들어주는 것.
        - 결합도가 낮아지면 변화에 대응하는 속도가 높아지고, 구성이 깔끔해지고, 확장하기에도 매우 편리하다.
        - `결합도`란 하나의 오브젝트가 변경이 일얼날 때에 관계를 맺고 있는 다른 오브젝트에게 변화를 요구하는 정도
        

### 디자인 패턴
소프트웨어 설계 시 특정 상황에서 자주 만나는 문제를 해결하기 위해 사용할 수 있는 재사용 가능한 솔루션을 말한다. 모든 패턴에는 간결한 이름이 있어서 잘 알려진 패턴을 적용하고 할 때 간단히 패턴 이름을 언급하는 것만으로도 설계의 의도와 해결책을 함께 설명할 수 있다는 장점이 있다. 디자인 패턴은 주로 객체지향 설계에 관한 것이고, 대부분 객체지향적 설계 원칙을 이용해 문제를 해결한다. 패턴의 설계 구조를 보면 대부분 비슷한데, 그 이유는 객체지향적인 설계로부터 문제를 해결하기 위해 적용할 수 있는 확장성 추구 방법이 대부분 두 가지 구조로 정리되기 때문이다. 하나는 클래스 상속이고, 다른 하나는 오브젝트 합성이다. 

- 템플릿 메소드 패턴
    - 상속을 통해 슈퍼클래스의 기능을 확장할 때 사용하는 가장 대표적인 방법
    - 변하지 않는 기능은 슈퍼클래스에 만들어두고 자주 변경되며 확장할 기능은 서브클래스에서 만들도록 한다
    - 슈퍼 클래스에서는 미리 추상 메소드 또는 오버라이드 가능한 메소드를 정의해두고 이를 활용해 코드의 기본 알고리즘을 담고 있는 템플릿 메소드를 만든다
    - 슈퍼클래스에서 디폴트 기능을 정의해두거나 비워뒀다가 서브클래스에서 선택적으로 오버라이드할 수 있도록 만들어둔 메소드를 훅(hook)메소드라고 한다. 
    - 서브클래스에서는 추상 메소드를 구현하거나, 훅 메소드를 오버라이드하는 방법을 이용해 기능의 일부를 확장한다.

- 팩토리 메소드 패턴
    - 템플릿 메소드 패턴과 마찬가지로 상속을 통해 기능을 확장하게 하는 패턴
    - 슈퍼클래스 코드에서는 서브클래스에서 구현할 메소드를 호출해서 필요한 타입의 오브젝트를 가져와 사용한다. 
    - 이 메소드는 주로 인터페이스 타입으로 오브젝트를 리턴하므로 서브클래스에서 정확히 어떤 클래스의 오브젝트를 만들어 리턴할지는 슈퍼클래스에서는 알지 못한다.
    - 서브클래스에서는 다양한 방법으로 오브젝트를 생성하는 메소드를 재정의할 수 있다.
    - 이렇게 서브클래스에서 오브젝트 생성 방법과 클래스를 결정할 수 있도록 미리 정의해둔 메소드를 팩토리 메소드라고 하고, 이 방식을 통해 오브젝트 생성 방법을 나머지 로직, 즉 슈퍼클래스의 기본 코드에서 독립시키는 방법을 팩토리메소드 패턴이라고 한다.
    - 하지만 상속을 사용했다는 단점이있다.

- 전략 패턴
    - 개방 폐쇄 원칙의 실현에 가장 잘 들어맞는 패턴
    - 자신의 기능 맥락(Context)에서, 필요에 따라 변경이 필요한 알고리즘을 인터페이스를 통해 통째로 외부로 분리시키고, 이를 구현한 구체적인 알고리즘 클래스를 필요에 따라 바꿔서 사용할 수 있게 하는 디자인 패턴.

- IOC(Inversion Of Control): 제어의 역전
    - 간단히 프로그램의 제어 흐름 구조가 뒤바뀌는 것
    - 제어 흐름의 개념을 거꾸로 뒤집는 것
    - 오브젝트 자신이 사용할 오브젝트를 스스로 선택하지 않고, 생성하지도 않는다

- 의존관계 주입(Dependency Injection)
    - 오브젝트 레퍼런스를 외부로부터 제공(주입)받고 이를 통해 여타 오브젝트와 다이내믹하게 의존관계가 만들어지는 것이 핵심
      

### 스프링의 IoC 용어 정리
- 빈(Bean)
    - 빈 또는 빈 오브젝트는 스프링이 IoC방식으로 관리하는 오브젝트
    - 관리되는 오브젝트라고 부르기도
    - 스프링이 직접 그 생성과 제어를 담당하는 오브젝트만을 빈이라고 부른다
- 빈 팩토리(Bean Factory)
    - 스프링의 IoC를 담당하는 핵심 컨테이너를 가리킨다
    - 빈을 등록하고, 생성하고, 조회하고 돌려주고, 그 외에 부가적인 빈을 관리하는 기능을 담당
- 애플리케이션 컨텍스트(Application Context)
    - 빈 팩토리를 확장한 IoC 컨테이너
    - 빈 팩토리의 기능에 스프링이 제공하는 각종 부가 서비스를 추가로 제공
    - ApplicationContext는 BeanFactory를 상속
- 설정정보/설정 메타정보(Configuration metadata)
    -애플리케이션 컨텍스트 또는 빈 팩토리가 IoC를 적용하기 위해 사용하는 메타정보
    - IoC컨테이너에 의해 관리되는 애플리케이션 오브젝틑를 생성하고 구성할 때 사용
- 컨테이너 또는 IoC 컨테이너
    - IoC 방식으로 빈을 관리한다는 의미에서 애플리케이션 컨텍스트나 빈 팩토리를 컨테이너 또는 IoC컨테이너 라고 부른다.
    - 그냥 컨테이너 또는 스프링 컨테이너 라고 할 때는 애플리케이션 컨텍스트를 가리키는 것이라고 보자

- 스프링은 빈을 싱글톤으로 만든다.


### 애노테이션
- @Configuration 
    - 애플리케이션 컨텍스트 또는 빈 팩토리가사용할 설정정보라는 표시
- @Bean
    - 오브젝트 생성을 담당하는 IoC용 메소드라는 표시


## 3장. 템플릿

템플릿이란 바뀌는 성질이 다른 코드 중에서 변경이 거의 일어나지 않으며 일정한 패턴으로 유지되는 특성을 가진 부분을 자유롭게 변경되는 성질을 가진 부분으로부터 독립시켜서 효과적으로 활요할 수 있도록 하는 방법

### 템플릿/콜백 패턴