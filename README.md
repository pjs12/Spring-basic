# Spring-basic

## 스프링이란?
### 스프링 생태계
- 스프링 프레임워크
- 스프링 부트
- 스프링 데이터
- 스프링 세션
- 스프링 시큐리티
- 스프링 Rest Docs
- 스프링 배치
- 스프링 클라우드...

### 스프링 프레임워크
- 핵심기술 : 스프링 DI 컨테이너, AOP, 이벤트, 기타..
- 웹 기술 : 스프링 MVC, 스프링 WebFlux
- 데이터 접근 기술 : 트랜젝션 , JDBC, ORM 지원, XML 지원
- 기술 통합 : 캐시, 이메일, 원격접근, 스케줄링
- 테스트 : 스프링 기반 테스트 지원
- 언어 : 코틀린, 그루비

### 스프링 부트
- **스프링을 편리하게 사용할 수 있도록 지원, 최근에는 기본으로 사용**
- 단독으로 실행할 수 있는 스프링 애플리케이션을 쉽게 생성
- Tomcat 같은 웹 서버를 내장해서 별도의 웹 서버를 설치하지 않아도 됨
- 손쉬운 빌드 구성을 위한 starter 종속성 제공
- 스프링과 3rd parth(외부) 라이브러리 자동 구성
- 메트릭, 상태 확인, 외부 구성 같은 프로덕션 준비 기능 제공
- 관례에 의한 간결한 설정
--------

## 스프링을 왜 만들었을까?
### 스프링의 핵심 개념, 컨셉
- 스프링은 자바 언어 기반의 프레임워크
- 자바 언어의 가장 큰 특징 : **객체 지향 언어**
- 스프링은 객체 지향 언어가 가진 강력한 특징을 살려내는 프레임워크
- **스프링은 좋은 객체 지향 애플리케이션을 개발할 수 있게 도와주는 프레임워크**
--------

## 좋은 객체 지향 프로그래밍이란?
### 객체 지향 특징
- 추상화
- 캡슐화
- 상속
- 다형성

### 객체 지향 프로그래밍
- 객체 지향 프로그래밍은 여러 개의 독립적인 단위, 즉 **"객체"**들의 모임으로 파악하고자 하는 것. 각각의 객체는 메시지를 주고받고, 데이터를 처리할 수 있다.
- 객체 지향 프로그래밍은 프로그램을 **유연하고 변경이 용이하게** 만들기 때문에 대규모 소프트웨어 개발에 많이 사용됨
  - 컴포넌트를 쉽고 유연하게 변경하면서 개발할 수 있는 방법 : **다형성(Polymorphism)**
--------

## 다형성
### 다형성의 실세계 비유
- 역할과 구현으로 세상을 구분
- 자동차 (역할 - 인터페이스) / K3, 아반떼, 테슬라 모델3 (구현 - 구현체)
  - 자동차가 바뀌어도 운전자에게 영향을 주지 않음 (운전자는 어떤 차든 운전이 가능함)
    - 자동차 역할의 인터페이스를 구현했기 때문
  - 운전자는 자동차의 역할(인터페이스)에만 의존함
  - 운전자는 자동차의 내부 구조를 몰라도 됨
  - 자동차 구현체의 내부가 추가, 수정되어도 운전자에게 영향을 주지 않음

- 공연 등장인물(역할 - 인터페이스) / 배우들 (구현 - 구현체)
  - 배우는 대체 가능함
  - 로미오의 구현체가 바뀐다고 줄리엣의 역할에 영향을 주지 않음
  &rarr; 유연하고 변경에 용이함

### 역할과 구현을 분리
- 역할과 구현으로 구분하면 세상이 단순해지고, 유연해지며 변경도 편리해짐
- 장점
  >- 클라이언트는 대상의 역할(인터페이스)만 알면 됨
  >- 클라이언트는 구현 대상의 내부 구조를 몰라도 됨
  >- 클라이언트는 구현 대상의 내부 구조가 변경되어도 영향을 받지 않음
  >- 클라이언트는 구현 대상 자체를 변경해도 영향을 받지 않음

#### 자바 언어
- 자바 언어의 다형성을 활용
  - 역할 = 인터페이스
  - 구현 = 인터페이스를 구현한 클래스, 구현 객체
- 객체를 설계할 때 역할과 구현을 명확히 분리
- 객체 설계 시 역할(인터페이스)을 먼저 부여하고, 그 역할을 수행하는 구현 객체 만들기

### 자바 언어의 다형성
- **오버라이딩**
```java
public class MemberService {
  private MemberRepository memberRepository = new MemoryMemberRepository();
  private MemberRepository memberRepository = new JdbcRepository();
}
```

### 다형성의 본질
- 인터페이스를 구현한 객체 인스턴스를 **실행 시점에 유연하게 변경**할 수 있음
- 다형성의 본질을 이해하려면 협력이라는 객체사이의 관계에서 시작해야함
- **클라이언트를 변경하지 않고, 서버의 구현 기능을 유연하게 변경할 수 있음**
--------

### 스프링과 객체 지향
- 다형성이 가장 중요
- 스프링은 다형성을 극대화하여 이용할 수 있게 도와줌
- 스프링에서 이야기하는 제어의 역전(IoC), 의존관계 주입(DI)은 다형성을 활용해서 역할과 구현을 편리  하게 다룰 수 있도록 지원함
--------

## 좋은 객체 지향 설계의 5가지 원칙(SOLID)
### SOLID
- SRP: 단일 책임 원칙(Single Responsibility Principle)
- OCP: 개방-폐쇄 원칙(Open/Closed Principle)
- LSP: 리스코프 치환 원칙(Liskov Substitution Principle)
- ISP: 인터페이스 분리 원칙(Interface Segregation Principle)
- DIP: 의존관계 역전 원칙(Dependency Inversion Principle)

### SRP 단일 책임 원칙
- 한 클래스는 하나의 책임만 가져야 함
- 하나의 책임이라는 것은 모호함
  - 클 수 있고, 작을 수 있음
  - 문맥과 상황에 따라 다름
- **중요한 기준은 변경.** 변경이 있을 때 파급 효과가 적으면 단일 책임 원칙을 잘 따른 것
- ex) UI 변경, 객체의 생성과 사용을 분리

### OCP 개방-폐쇄 원칙
- 소프트웨어 요소는 **확장에는 열려있지만 변경에는 닫혀있어야 함**
- **다형성**을 활용
- 인터페이스를 구현한 새로운 클래스를 하나 만들어서 새로운 기능을 구현
- 지금까지 배운 역할과 구현의 분리 생각해보기

#### OCP 문제점
```java
public class MemberService {
  private MemberRepository memberRepository = new MemoryMemberRepository();   // 기존 코드
  private MemberRepository memberRepository = new JdbcRepository();           // 변경 코드
}
```
- **구현 객체를 변경하려면 클라이언트 코드를 변경해야 함**
- **분명 다형성을 사용했지만 OCP 원칙을 지킬 수 없음**
- 이 문제의 해결법?
- 객체를 생성하고, 연관관계를 맺어주는 별도의 조립, 설정자가 필요

### LSP 리스코프 치환 원칙
- 프로그램의 객체는 프로그램의 정확성을 깨뜨리지 않으면서 하위 타입의 인스턴스로 바꿀 수 있어야 함
- 다형성에서 하위 클래스는 인터페이스 규약을 다 지켜야 한다는 것, 다형성을 지원하기 위한 원칙, 인터페이스를 구현한 구현체는 믿고 사용하려면, 이 원칙이 필요함
- 단순히 컴파일에 성공하는 것을 넘어서는 이야기
- ex) 자동차 인터페이스의 엑셀은 앞으로 가라는 기능, 뒤로 가게 구현하면 LSP 위반, 느리더라도 앞으로 가야함
- 인터페이스의 규약을 맞춰야 함, 기능적으로 보장해야 함

### ISP 인터페이스 분리 원칙
- 특정 클라이언트를 위한 인터페이스 여러 개가 범용 인터페이스 하나보다 나음
- 자동차 인터페이스 &rarr; 운전 인터페이스, 정비 인터페이스로 분리
- 사용자 클라이언트 &rarr; 운전자 클라이언트, 정비사 클라이언트로 분리
- 분리하면 정비 인터페이스 자체가 변해도 운전자 클라이언트에 영향을 주지 않음
- 인터페이스가 명확해지고, 대체 가능성이 높아짐

### DIP 의존관계 역전 원칙
- 프로그래머는 "추상화에 의존해야지, 구체화에 의존하면 안된다." 의존성 주입은 이 원칙을 따르는 방법 중 하나
- 쉽게 이야기해서 **구현 클래스에 의존하지 말고, 인터페이스에 의존하라**는 뜻
- 앞에서 이야기한 **역할(Role)에 의존하게 해야 한다**는 것과 같음. 객체 세상도 클라이언트가 인테페이스에 의존해야 유연하게 구현체를 변경할 수 있음. 구현체에 의존하게 되면 변경이 아주 어려워짐.
- OCP에서 설명한 MemberService는 인터페이스에 의존하지만, 구현 클래스도 동시에 의존함
  &rarr; DIP 위반

**다형성 만으로는 OCP, DIP를 지킬 수 없음**

--------

## 객체 지향 설계와 스프링
### 스프링과 객체 지향은 무슨 관계?
- **스프링은 다음 기술로 다형성 + OCP, DIP를 가능하게 지원**
  - DI(Dependency Injection): 의존관계, 의존성 주입
  - DI 컨테이너 제공
- **클라이언트 코드의 변경 없이 기능 확장**
- 쉽게 부품을 교체하듯이 개발

### 정리
- 모든 설계에 역할과 구현을 분리하자
- 이상적으로는 모든 설계에 인터페이스를 부여하자
- 하지만 인터페이스를 무분별하게 도입하면 추상화라는 비용이 발생
- 기능을 확장하 가능성이 없다면, 구체 클래스를 직접 사용하고, 향후 꼭 필요할 때 리펙터링해서 인터페이스를 도입하는 것도 방법

--------

##  좋은 객체 지향 설계의 5가지 원칙 적용
여기서 3가지 SRP, DIP, OCP 적용


### SRP 단일 책임 원칙
##### 한 클래스는 하나의 책임만 가져야 함.
- 클라이언트 객체는 직접 구현 객체를 생성하고, 실행하는 다양한 책임을 가지고 있음
- SRP 단일 책임 원칙을 따르면서 관심사를 분리
- **구현 객체를 생성하고 연결하는 책임**은 AppConfig 담당
- **클라이언트 객체는 실행하는 책임만 담당**

### DIP 의존관계 역전 원칙
##### 프로그래머는 추상화에 의존해야지, 구체화에 의존하면 안됨. 의존성 주입은 이 원칙을 따르는 방법 중 하나
- 새로운 할인 정책을 개발하고, 적용하려고 하니 클라이언트 코드도 함께 변경해야 했음.
  왜냐하면 기존 클라이언트 코드(OrderServiceImpl)는 DIP를 지키며 DiscountPolicy 추상화 인터페이스에 의존하는 것 같았지만,
  FixDiscount 구체화 구현 클래스에도 함께 의존했음
- 클라이언트 코드가 DiscountPolicy 추상화 인터페이스에만 의존하도록 코드를 변경
- 하지만 클라이언트 코드는 인터페이스만으로는 아무것도 실행할 수 없음
- AppConfig가 FixDiscountPolicy 객체 인스턴스를 클라이언트 코드 대신 생성해서 클라이언트 코드에 의존관계를 주입했음.

### OCP 개방-폐쇄 원칙
##### 소프트웨어 요소는 확장에는 열려 있지만 변경에는 닫혀 있어야 함
- 다형성 사용하고 클라이언트가 DIP를 지킴
- 애플리케이션을 사용 영역과 구성 영역으로 나눔
- AppConfig가 의존관계를 FixDiscountPolicy -> RateDiscountPolicy로 변경해서 클라이언트 코드에 주입하므로 클라이언트 코드는 변경 필요 없음.
- **소프트웨어 요소를 새롭게 확장해도 사용 영역의 변경은 닫혀 있음**

--------

## IoC, DI 그리고 컨테이너
### 제어의 역전 IoC(Inversion of Control)
- 기존 프로그램은 클라이언트 구현 객체가 스스로 필요한 서버 구현 객체를 생성하고, 연결하고, 실행했음.
  한마디로 구현 객체가 프로그램의 제어 흐름을 스스로 조종함. 개발자 입장에서는 자연스러운 흐름.
- 반면에 AppConfig가 등장한 이후 구현 객체는 자신의 로직을 실행하는 역할만 담당함. 프로그램의 제어 흐름은 이제 AppConfig가 가져감.
  예를 들어 OrderServiceImpl은 필요한 인터페이스들을 호출하지만 어떤 구현 객체들이 실행될지 모름.
- 프로그램에 대한 제어 흐름에 대한 권한은 모두 AppConfig가 가지고 있음. 심지어 OrderServiceImpl도 AppConfig가 생성.
  그리고 AppConfig는 OrderServiceImpl이 아닌 OrderService 인터페이스의 다른 구현 객체를 생성하고 실행할 수 있음.
  그런 사실도 모르채 OrderServiceImpl은 자신의 로직만 실행할 뿐.
- 이렇듯 프로그램의 제어 흐름을 직접 제어하는 것이 아니라 외부에서 관리하는 것을 제어의 역전(IoC)이라 함.

##### 프레임워크 vs 라이브러리
- 프레임워크가 내가 작성한 코드를 제어하고, 대신 실행하면 그것은 프레임워크가 맞음.(JUnit)
- 내가 작성한 코드가 직접 제어의 흐름을 담당한다면 그것은 프레임워크가 아니라 라이브러리.

### 의존관계 주입 DI(Dependency Injection)
- OrderServiceImpl은 DiscountPolicy 인터페이스에 의존함. 실제 어떤 구현 객체가 사용될지는 모름.
- 의존관계는 **정적인 틀래스 의존 관계와 실행 시점에 결정되는 동적인 객체(인스턴스) 의존 관계** 들을 분리해서 생각해야 함.

##### 정적인 클래스 의존관계
- 클래스가 사용하는 import 코드만 보고 의존관계를 쉽게 판단할 수 있음. 정적인 의존관계는 애플리케이션을 실행하지 않아도 분석할 수 있음.
  예를 들어, OrderServiceImpl은 MemberRepository, DiscountPolicy 인터페이스에 의존하지만 실제 어떤 객체가 OrderServiceImpl에 주입될지는 알 수 없음.

##### 동적인 객체 인스턴스 의존 관계
- 애플리케이션 실행 시점에 실제 생성된 객체 인스턴스의 참조가 연결된 의존 관계임.

- **애플리케이션 실행 시점(런타임)** 에 외부에서 실제 구현 객체를 생성하고 클라이언트에 전달해서 클라이언트와 서버의 실제 의존관계가 연결되는 것을 **의존관계 주입**이라 함.
- 객체 인스턴스를 생성하고 그 참조값을 전달해서 연결됨.
- 의존관계 주입을 사용하면 클라이언트 코드를 변경하지 않고 클라이언트가 호출하는 대상의 타입 인스턴스를 변경할 수 있음.
- 의존관계 주입을 사용하면 정적인 클래스 의존관계를 변경하지 않고 동적인 객체 인스턴스 의존관계를 쉽게 변경할 수 있음.

### IoC 컨테이너, DI 컨테이너
- AppConfig처럼 객체를 생성하고 관리하면서 의존관계를 연결해주는 것을 **IoC 컨테이너** 또는 **DI 컨테이너**라고 함.
- 의존관계 주입에 초점을 맞추어 최근에는 주로 DI 컨테이너라고 함.
- 또는 어셈블러, 오브젝트 팩토리 등으로 불림.

