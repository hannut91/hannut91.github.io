---
title: 달랩 Front-end TDD 세미나
subTitle: TDD로 프론트엔드 개발하기
category: 
tags: 
createdat: 2019-08-24 13:04:00
updatedat: 2019-08-24 13:04:00
---

## 기대하는 것 키워드들

Use case, UI Framework, Unit test이후, TDD적인 사고, 실무에 적용, TDD를 팀에 
적용, 설계 관점, 협업, 이미 있는 프로젝트에 적용하는 방법들 설무에 어떻게
적용할 수 있을지를 사람들이 고민을 많이 하는 것 같다. 그리고 팀원들이 같이
TDD를 할 수 있을지 고민을 하는 것 같다.

## 학습 목표

TDD의 핵심 아이디어를 이해하고 TDD도입의 출발점을 만들자.

## 왜 TDD를 해야 하나요?

* Ron Jeffries - “clean code that works”
  * 깔끔하고 올바르게 동작하는 코드. 둘 중 하나만 있으면 이상하다.
* Kent Beck - “TDD is a way of managing fear during programming.”
  * 프로그래밍을 하는 동안에 두려움을 업애는 것.
* Kent Beck - “TDD is an awareness of the gap between decision and feedback 
  during programming, and techniques to control that gap.”
  * 설계나 코드를 작성하는 단계에서 피드백을 받는 것.
* GOOSGBT - “Software Development as a Learning Process”
  * 만드는 과정에서 배운다. 피드백으로부터 배운다. 피드백을 빠르게 받음으로써
    빠르게 배울 수 있다.

## TDD의 간단한 두 규칙

1. Don’t write a line of new code unless you first have a failing automated 
  test.
2. Eliminate duplication.

## [질문] 중복을 몰아낸다는 건 어떤 의미인가?  

=> 같은 기능을 하거나 역할을 하는 것을 일반화, 추상화를 통해서 제거한다. 그래서
재사용을 할 수 있다.

## Technical Implications

* You must design organically, with running code providing feedback between 
  decisions
* You must write your own tests, since you can’t wait twenty times a day for 
  someone else to write a test
* Your development environment must provide rapid response to small changes
* Your designs must consist of many highly cohesive, loosely coupled 
  components, just to make testing easy

## [질문] 좋은 설계란 무엇인가? 어떻게 알 수 있는가? 어떻게 배울 수 있는가?

=> 변경하기 쉬운 설계, 변경하고자 할 때 알 수 있다. 여러가지를 찾아보고 배워야
하는데 제일 좋은 것은 팀내에서 같이 의논하며 배우는 것이 좋다.

## TDD하는 법

* Red - write a little test that doesn’t work, perhaps doesn’t even compile at 
  first
* Green - make the test work quickly, committing whatever sins necessary in the 
  process
* Refactor - eliminate all the duplication created in just getting the test to 
  work

## [질문] 작게 시작한다는 건 어떤 의미인가?

일단 input은 무엇이고 output은 무엇인지 생각해보자.

## [질문] 리팩터링의 전제 조건은 무엇인가?

기능을 테스트할 수 있는 테스트. 설계를 변경 후에도 코드가 올바르게 동작하는
것을 확인할 수 잇는 테스트

## 왜 Front-end 개발에 TDD를 적용하기 어렵다고 생각하시나요?

* 문서만 보고 해서 내가 한 게 맞게 한 건지 모르겠다.
* UI 테스트가 어렵다.
* 어디까지 테스트해야 할지 모르겠다.
* API에 대한 Mocking이 쉽지 않다.
* 동료를 설득하기 어렵다.
* 눈으로 보면서 테스트를 할 수 있는데 왜 자동화해야 하는가?
* “UI는 테스트하지 않습니다”란 조언을 들었다.

## 관심사의 분리 (Separation of Concerns)

### SRP (Single Responsibility Principle)

하나의 객체, 모듈이 책임을 하나만 가지게 하자. 변경해야하는 이유가 하나여야
한다. 응집도가 높아야 한다.

### Layered Architecture

DDD에서 얘기하는 Layered Architecture. 각 레이어는 인접한 레이어와 의존한다.

1. UI Layer
2. Application Layer
3. Domain Layer
4. Infrastructure Layer

## 명령형과 선언형 프로그래밍

선언형 프로그래밍은 내가 원하는 의도를 작성한다.

## 좋았던 점

* 다른분들이 실무에서 어떤 어려움이 있는지 간접적으로 알게됐다. 다른분들의
  관심사를 통해 현재 어떤 어려움을 겪고있는지 공감할 수 있었다.
* TDD를 왜 하는지에 대해 다시 생각해볼 수 있었고 원칙들을 배웠다.
* 항상 웹프레임워크를 이용해서 개발을 하다보니 내가 작성하는 코드가 해당
  프레임워크에 의존성이 있어 테스트를 작성하느 방법이 따로 있지 않을까 하는
  생각이 잘못됐음을 알게됐다. UI 로직과 비즈니스 로직을 잘 분리하면
  프론트엔드라고해서 특별한 테스트 방식이 존재하지 않는다. 단 UI와 관련된
  테스트는 조금 다를 수 있다.
* 관심사의 분리를 배웠다. 테스트를 작성하기 전에 굉장히 중요한 것임을 꺠달았다.

## 아쉬웠던 점

* 시간이 부족했다.
* 실습이 없었다. 따라하기에는 시간이 너무 부족했다. 실습은 내가 직접찾아서
  해야겠다.

