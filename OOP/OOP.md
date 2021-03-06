# OOP (Object Oriented Programming)

## 객체의 3가지 요소
+ 상태 유지 (객체의 상태)
  + 객체는 상태 정보를 저장하고, 유지되어져야 하며 이러한 속성은 변수로 정의 되어져야 한다. 이러한 속성값이 바뀌으로 인하여, 객체의 상태가 변경 될 수 있어야 한다.
+ 기능 제공 (객체의 책임)
  + 객체는 기능을 제공해야 한다. 이 부분은 Method의 제공으로 이루어진다. 이 부분은 캡슐화와 연관이 있으며, 외부로 부터 직접 속성에 접근하여 변경하는 것이 아닌 객체가 제공하는 Method의 기능으로 이루어 져야한다.
+ 고유 식별자 제공 (객체의 유일성)
  + 각각의 객체는 고유한 식별자를 가져야 한다. 예를 들면 카드번호, 계좌번호, 자동차 번호와 같은 속성을 통해서 각각 고유한 값을 줄 수 있으며 이는 이후 db에서 Unique Key, 또는 Primary key 로도 작성이 가능하다.

## 물리 객체
+ 물리적 객체는 실제로 사물이 존재하며, 이를 클래스로 정의한 객체를 의미한다.
## 개념 객체
+ 이후 우리가 개발할 웹 시스템에서 Service에 해당하며 이는 business logic을 처리하는 부분을 의미한다
+ Business logic에서는 여러 객체를 서로 상호작용 하도록 하며, 객체가 제공하는 오퍼레이션 method를 통해 객체의 속성을 변경 시킨다.

## 객체지향의 4대 특성
+ 캡슐화
  + 캡슐화는 객체의 속성을 보호하기 위해 사용
  + Method 설계
    + 속성이 선언되었으나, 이의 상태를 변경하는 method가 없다면 잘못 선언된 속성이다.
    + 실물 객체가 가진 기능을 모두 제공 해야 한다
    + 각각의 Method는 서로 관련성이 있어야한다.
    + 객체 안의 Method는 객체 안의 속성을 처리해야 하며, 다른 객체를 전달받아 해당 다른 객체에 정의 된 속성을 직접 처리하면 안된다.
    + 단, Method에 실행에 필요한 값들은 객체의 형태가 아닌 매개변수의 형태로 전달되어져야 한다.
  + Getter/ Setter Method
    + 외부에서 내부 속성에 직접 접근하는 것이 아닌 Getter / Setter Method를 통해 접근하도록 적용
  + CRUD Method
    + 데이터 처리를 위한 기본적인 CRUD Method를 제공
  + Business Logic Method
    + 비지니스 로직 처리를 위한 Method 제공
  + 객체의 생명 주기 처리 Method
    + 흔히 destroy(), disconnect() 등 quit() 등 소멸에 대한 Method
  + 객체의 영구성 관리 Method
    + 영구성(유효성) 속성에 대한 변경이 필요한 경우 외부에서는 접근이 불가능 하도록 private로 선언하며, 내부의 다른 Method를 통해서 사용 되도록 한다.
  + 장점
    + 객체지향의 패러다임 중 하나인 추상화 제공
    + 재 사용성 향상
    + 유지보수의 효율성 향상
    + 무결성
+ 상속
  + 객체지향에서 상속은, 속성의 상속이 아닌, 하위로 내려갈수록 구체화 되는 것이다.
  + 프로그램 구조에 대한 이해도 향상
  + 재사용성 향상
  + 확장석 향상
  + 유지보수성 향상
+ 다형성
  + 하나의 객체가 여러 개의 형태로 변화 하는 것
  + 오버라이딩을 통해 가능
+ 추상화
  + 객체지향에서 추상화는 모델링이다.
  + 구체적으로 공통적인 부분, 또는 특정 특성을 분리해서 재조합 하는 부분이 추상화입니다
  + 다형성, 상속 모두 추상화에 속한다.

## 객체지향 설계 5원칙 (SOLID)
+ 응집도와 결합도
  + 좋은 소프트웨어 설계는 결합도는 낮추고 응집도는 높여햐 한다.
    + 결합도 : 모듈(클래스) 간의 상호 의존 정도를 나타내는 지표로, 결합도가 낮으면 모듈간의 상호 의존성이 줄어들어 객체의 재사용 및 유지보수가 유리하다.
    + 응집도 : 하나의 모듈 내부에 존재하는 구성요소들의 기능적 관련성으로, 응집도가 높은 모듈은 하나의 책임에 집중하고 독립성이 높아져, 재사용 및 유지보수가 용이하다.
+ SRP (Single Responsibility Principle : 단일 책임 원칙)
  + 어떠한 클래스를 변경해야 하는 이유는 한가지 뿐이여야 한다.
+ OCP (Open Closed Principle : 개방 폐쇄 원칙)
  + 자신의 확장에는 열려있고, 주변의 변화에 대해서는 닫혀 있어햐 한다.
  + 상위 클래스 또는 인터페이스를 중간에 둠으로써, 자신은 변화에 대해서는 폐쇄적이지만, 인터페이스는 외부의 변화에 대해서 확장을 개방해 줄 수 있다.
+ LSP (Liskov Substitution Principle : 리스코프 치환 원칙)
  + 서브 타입은 언제나 자신의 기반(상위) 타입으로 교체 할 수 있어야 한다.
+ ISP (Interface Segregation Principle : 인터페이스 분리 원칙)
  + 클라이언트는 자신이 사용하지 않는 메서드에 의존 관계를 맺으면 안된다.
  + 프로젝트 요구사항과 설계에 따라 SRP/ISP 를 선택한다.
+ DIP (Dependency Inversion Principle : 의존 역전 원칙)
  + 자신보다 변하기 쉬운 것에 의존하지 말아야 한다.

## POJO JAVA (Plain Old Java Object)
+ 순수한 자바 오브젝트
+ 특징
  + 특정 규약에 종속 되지 않는다.
  + 특정 환경에 종속되지 않는다.
+ Spring, Hibernate
  + 하나의 서비스를 개발하기 위해서는, 시스템의 복잡함, 비즈니스 로직의 복잡함 등 다양한 어려움을 맞이 하게 된다.
  + 위의 두 프레임워크는 객체지향적인 설계를 하고 있으며, 또한 POJO를 지향하고 있다.
  + 그러므로 개발자가 서비스 로직에 집중하고 이를 POJO로 쉽게 개발 할 수 있도록 지원한다.


