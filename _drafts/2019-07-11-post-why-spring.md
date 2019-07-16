---
title: "Spring framework는 왜 쓰는거야?"
author_profile: true
categories: 
  - TECH
#toc: true
tags:
- Spring
- Spring Framework
- Spring boot
- 스프링
- 스프링 프레임워크
---

웹 개발을 하면서 스프링기반으로 프로젝트를 많이 진행을 하였고 지금도 스프링을 이용하여 개발을 하고 았어.

많이?? 지금까지 해온 프로젝트에서 80%이상은 정말 스프링 기반으로 구현을 하였고,
그 중 20%는 스프링부트를 사용하여 개발을 하였지.

스프링프레임워크가 무엇이냐고? 단순히 백엔드 개발을 도와 주는 오픈소스 어플리케이션 프레임워크야.

그럼 스프링을 왜 쓰는건지 고민 해보았을까?.. 아니 고민하지 않았어.

그냥 과거에 어떤 프로젝트에 투입하였더니 이미 스프링프레임워크를 채택하여 세팅이 되어 있으니깐 사용 하였고, 그 후도 상황은 비슷했어.

내가 직접 프로젝트를 세팅하는 경우에도 그냥 스프링프레임워크를 당연히 썻어, 왜냐고? 그냥 이전 프로젝트때도 사용했었고, 익숙하니깐.. 그저 그 이유였어.

그래도 스프링 덕에 ConnectionPool을 만들지도 Connection을 관리하지 않아도 됐어!

그리고 아주 귀찮았던 transaction을 관리하지 않았지. 예전엔 transaction Manager를 작성 해야했어.

에러가 발생하면 그동안 처리된 내역을 Roolback 하지도 않아도 되었고, 프로세스가 Success 되면 Commit을 하는 일을 하는 일이 사라졌다.

음... 그러면 스프링을 써야만 이런게 돼????
그건 아니야... 스트럿츠도있고 EJB도 있거든...

## 근데 왜 굳이 스프링을 사용 해야 되는거 였을까??
일단 그 이유를 알아보려면, 스프링이 왜 나왔는지 먼저 알아야겠어..

이 프로젝트는 아래와 같이 워키백과에 설명이 되었어.
>로드 존슨이 2002년에 출판한 자신의 저서인 Expert One-on-One J2EE Design and Developement 에 선보인 코드를 기반으로 시작하여 점점 발전하게 되었다.


~~~text
The results of using J2EE in practice are often disappointing: applications are often slow, unduly complex, and take too long to develop. Rod Johnson believes that the problem lies not in J2EE itself, but in that it is often used badly. Many J2EE publications advocate approaches that, while fine in theory, often fail in reality, or deliver no real business value.

Expert One-on-One: J2EE Design and Development aims to demystify J2EE development. Using a practical focus, it shows how to use J2EE technologies to reduce, rather than increase, complexity. Rod draws on his experience of designing successful high-volume J2EE applications and salvaging failing projects, as well as intimate knowledge of the J2EE specifications, to offer a real-world, how-to guide on how you too can make J2EE work in practice.

...

It emphasizes the use of OO design and design patterns in J2EE, without becoming a theoretical book
~~~

로드존슨은 실제로 J2EE을 사용한 결과물에 실망을 한거 같아.
> 응용프로그램은 종종 느리고, 지니차게 복잡하며, 개발하는데 너무 오래걸린다.

하지만, 이는 J2EE의 문제가 아닌, 종종 잘못 사용되는 것에 문제가 있음으로 보았고,
J2EE 프로젝트에서 자주 발생되는 실수와 API의 복잡성을 피하고, 가능한 간단하고 실용적인 접근방식으로 디자인패턴으로 사용되길 원한거 같아.
> 이론적 인 책이되지 않고 OO 디자인 및 디자인 패턴을 J2EE에서 사용하는 것을 강조합니다.

이후 점점 발전하게 되어, 2004년 3월 버전1을 발표하고, 2017년 9월 스프링5까지 발표가 되었어.

그럼 불편하을 해소하자고 만들어졌는지는 알았는데.
## 그래서 뭐가 편해졌을까??
스프링은 몇가지의 큰 특징을 가지고 있어.

### 제어 반전 컨테이너
제어 반전(IoC: Inversion of Control) 컨테이너는 스프링의 가장 중요하고 핵심적인 기능으로서 자바의 반영(reflection)을 이용해서 객체의 생명주기를 관리하고 의존성 주입(Dependency Injection)을 통해 각 계층이나 서비스들간의 의존성을 맞춰준다. 이러한 기능들은 주로 환경설정을 담당하는 XML 파일에 의해 설정되고 수행된다.

### 관점 지향 프로그래밍 프레임워크
스프링은 로깅이나 보안, 트랜잭션 등 핵심적인 비즈니스 로직과 관련이 없으나 여러 곳에서 공통적으로 쓰이는 기능들을 분리하여 개발하고 실행 시에 서로 조합할 수 있는 관점 지향 프로그래밍(AOP)을 지원한다. 기존에 널리 사용되고 있는 강력한 관점 지향 프로그래밍 프레임워크인 AspectJ도 내부적으로 사용할 수 있으며, 스프링 자체적으로 지원하는 실행시(Runtime)에 조합하는 방식도 지원한다.

### 데이터 액세스 프레임워크
스프링은 데이터베이스에 접속하고 자료를 저장 및 읽어오기 위한 여러 가지 유명한 라이브러리, 즉 JDBC, iBATIS(MyBatis), Hibernate 등에 대한 지원 기능을 제공하여 데이터베이스 프로그래밍을 쉽게 사용할 수 있다.

### 트랜잭션 관리 프레임워크
스프링은 추상화된 트랜잭션 관리를 지원하며 XML 설정파일 등을 이용한 선언적인 방식 및 프로그래밍을 통한 방식을 모두 지원한다.

### 모델-뷰-컨트롤러 패턴
스프링은 웹 프로그램밍 개발 시 거의 표준적인 방식인 Spring MVC라 불리는 모델-뷰-컨트롤러(MVC) 패턴을 사용한다. DispatcherServlet이 Controller 역할을 담당하여 각종 요청을 적절한 서비스에 분산시켜주며 이를 각 서비스들이 처리를 하여 결과를 생성하고 그 결과는 다양한 형식의 View 서비스들로 화면에 표시될 수 있다.

### 배치 프레임워크
스프링은 특정 시간대에 실행하거나 대용량의 자료를 처리하는데 쓰이는 일괄 처리(Batch Processing)을 지원하는 배치 프레임워크를 제공한다. 기본적으로 스프링 배치는 Quartz 기반으로 동작한다.
