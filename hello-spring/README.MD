# 김영한의 스프링 완전 정복 - 스프링 입문

## 라이브러리 살펴보기

### 스프링 부트 라이브러리
* spring-boot-starter-web
    + spring-boot-start-tomcat: 톰캣(웹서버)
    + spring-webmvc: 스프링 웹 MVC
* spring-boot-starter-thymeleaf: 타임리프 템플릿 엔진(View)
* spring-boot-starter(공통): 스프링 부트 + 스프링 코어 + 로깅
    + spring-boot
        - spring-core
    + spring-boot-starter-logging
        - logback, slf4j

### 테스트 라이브러리
* spring-boot-starter-test
    + junit: 테스트 프레임워크
    + mockito: 목 라이브러리
    + assertj: 테스트 코드를 좀 더 편하게 작성하게 도와주는 라이브러리
    + spring-test: 스프링 통합 테스트 지원

## 스프링 웹 개발 기초
* [정적 컨텐츠]
* [MVC와 템플릿 엔진]
* [API]

## 비즈니스 요구사항 정리 (예제)
* 데이터: 회원 ID, 이름
* 기능: 회원 등록, 조회
* 아직 데이터가 선정되지 않음(가상 시나리오)

### 일반적인 웹 애플리케이션 계층 구조

컨트롤러 -> 서비스 -> 리포지토리 -> DB  
　　↓　　　　　↓　　　　↓  
　　　　　　도메인  

* 컨트롤러: 웹 MVC의 컨트롤러 역할
* 서비스: 핵심 비즈니스 로직 구현
* 리포지토리: DB 접근, 도메인 객체를 DB에 저장하고 관리
* 도메인: 비즈니스 도메인 객체. ex) 회원, 주문, 쿠폰 등 주로 DB에 저장 및 관리

### 클래스 의존관계
MemberService ----> MemberRepository(Interface)  
　　　　　　　　　　　　　　　　　　↑  
　　　　　　　　　　　　　　　　　　|  
　　　　　　　　　　　　　　　　　　|  
　　　　　　　　　　　　　　　　　　|  
　　　　　　　　　　　　MemoryMemberRepository

* 아직 데이터 저장소가 선정되지 않아, 우선 인터페이스로 구현 클래스를 변경할 수 있도록 설계
* 데이터 저장소는 RDB, NoSQL 등 다양한 저장소를 고민중인 상황으로 가정
* 개발을 진행하기 위해 초기 개발 단계에선 구현체로 가벼운 메모리 기반의 데이터 저장소 사용

### 테스트 코드
코드를 테스트 할 때 main 메서드를 통하거나 웹 애플리케이션 컨트롤러를 통해 해당 기능을 실행하면 준비와 실행이 오래걸리고 반복이 어렵고 여러 테스트를 진행할 수 없다.
자바는 Junit이라는 프레임워크로 테스트를 실행해 이러한 단점을 보완한다.



