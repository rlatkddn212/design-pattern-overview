# design-pattern-overview

디자인 패턴에 대해 한눈에 볼 수 있게 정리한 문서 입니다.



## 디자인 패턴?

- GOF(Gang of Four)라는 소프트웨어 전문가 4명이 제안
- 객체지향 설계에 대한 23가지 해법 제시
- 크게 분류하여 생성 패턴,  구조 패턴, 행동 패턴 3가지로 분류

  - 생성 패턴 (Creational) : 객체를 생성하는 5 가지 패턴이 있다. 직접 new로 객체를 생성하지 않고, 다른 객체를 사용하거나(팩토리), 객체를 단 하나만 생성할 수 있게 제한 하거나(싱글턴) 하여 사례에 따라 프로그램에 유연성을 향상시킬 수 있다.
  - 구조 패턴 (Structural) :  클래스에 구성을 설계하는  7 가지 패턴이 있다. 서로 다른 클래스 사이에 호환성 문제(어뎁터), 객체에 생성과 소멸 같은 기능을 대리해서 처리(프록시)등 클래스의 구성을 달리 하여 새로운 기능을 얻을 수 있다. API 제작을 한다면 필수적으로 봐야할 것.
  - 행동 패턴 (Behavioral) : 객체 간에 커뮤니케이션 행위들에 대한 11가지 패턴이 있다. 발행자와 구독자 객체간에 커뮤니케이션(옵저버), 객체 지향 방식으로 상태 기계를 구현(상태 패턴)
- (개인적으로 객체를 생성하는 생성패턴과 다른 패턴을 구분하긴 쉽지만, 구조 패턴과 행동 패턴에 구분이 모호한 것 같다. 모호한게 너무 많다. 결국 경험이 많지 않으면 디자인 패턴으로 코드를 작성하긴 너무 힘든일이다.)



## 상속보다 인터페이스

- Program to an 'interface', not an 'implementation'.
- 위 말 처럼 디자인 패턴은 인터페이스에 대한 이해가 중요
- 클래스 사용자가 클래스에 대한 구현을 알지 못하고, 인터페이스를 정의 하는 추상 클래스에 대해서만 알고 코드를 작성하게 한다.
- 상속보다 인터페이스를 사용하여 코드를 작성
  - 상속은 부모 클래스의 세부 사항을 알 필요가 있음
  - 부모 클래스가 변경될 경우 자식 클래스들도 수정 필요



## SOLID 원칙

- 객체지향에 5가지 원칙
- 디자인 패턴을 사용하여 SOLID 원칙에 맞게 코딩
- 코드를 변경하려면 변경하려는 코드 부분에 의존적인 모듈을 수정해야하고, 그 모듈에 후속 변경 사항까지 연속적으로 수정해야한다. 즉, 소프트웨어를 변경하기 쉽게하려면 모듈간에 의존성을 줄여야한다.
- 모듈에 너무 많은 기능을 추가하면, 똑같은 기능이 필요하여 만들 때도 재사용할 수 없게 만든다.
- SOLID 원칙을 지켜 코딩 함으로써 의존성을 줄이고, 재사용성을 늘린다.
- 여기선 간단히 언급만 한다.



### The Single Responsibility Principle (SRP)

> 모든 클래스는 하나의 책임만 가지며, 클래스는 그 책임을 완전히 캡슐화해야 함



### The Open Closed Principle (OCP)

>  확장에는 Open, 수정에는 Close 해야한다.

- 모듈을 수정하지 않고 확장 할 수 있어야한다.



### The Liskov Substitution Principle (LSP)

> 클래스 A가 클래스 B의 부모라면 클래스 B는 클래스 A로 치환 할 수 있어야 한다.

- 정사각형과 직사각형관계로 설명하는 예가 많다.
- 정사각형을 직사각형으로 치환하여 사용할 경우 직사각형의 맴버함수로 폭을 변경시키면 정사각형의 폭과 높이가 달라진다.
- 이런 관계는 이 원칙을 위반한다고 볼 수 있다.



### The Dependency Inversion Principle (DIP)

> 추상성이 높은 클래스(interface, 부모 클래스 등)의 경우 구체클래스(구현된 클래스, 자식 클래스 등)에 의존해선 안된다.



### The Interface Segregation Principle (ISP)

> 사용자가 사용하지 않는 메서드에 의존해선 안된다.





# 생성 패턴 (Creational)



추상 팩토리 패턴

빌더 패턴

팩토리 메서드 패턴

프로토타입 패턴

싱글턴 패턴



## 추상 팩토리 패턴



## 빌더 패턴



## 팩토리 메서드 패턴



## 프로토타입 패턴



## 싱글턴 패턴



# 구조 패턴(Structural)

어댑터 패턴

브리지 패턴

컴포지트 패턴

데코레이터 패턴

퍼사드 패턴

플라이웨이트 패턴

프록시 패턴



# 행동 패턴 (Behavioral)



책임 연쇄 패턴

커맨드 패턴

인터프리터 패턴

반복자 패턴

중재자 패턴

메멘토 패턴

옵저버 패턴

상태 패턴

전략 패턴

템플릿 메소드 패턴

비지터 패턴







## 참고 자료

https://web.archive.org/web/20150906155800/http://www.objectmentor.com/resources/articles/Principles_and_Patterns.pdf