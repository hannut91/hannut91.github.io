---
title: 마이크로 서비스 시작하기
subTitle: 마이크로 서비스 시작하기
category: 
tags: 
createdat: 2019-08-22 22:40:00
updatedat: 2019-08-22 22:40:00
---

마이크로 서비스 인 액션 2장을 읽고 정리해보았습니다.

## 마이크로 서비스가 맞는지 생각하기

도메인에 대한 이해가 필요하다. 빈약한 도메인 지식은 잘못된 설계를 만든다.

## 마이크로 서비스가 올바른 선택일까?

* 시스템 요구사항은 계속 변화한다. 제품의 요구사항, 성장에 대한 압박, 팀의
  역량에 대해 실용주의와 이상주의 사이의 균형을 고려해야 한다.
* 마이크로 서비스 아키텍처를 선택할 때 고려할 요소들
  * 도메인 복잡도
  * 기술적 요구사항
  * 조직 규모 성장
  * 팀 지식

## 새로운 기능을 개발하기

* 최소기능제품 MVP(Minimum Viable Product)를 구축한다.
* 도메인 모델링을 통해 마이크로 서비스 식별하기
  * 제품 탐색(Product discovery)또는 비즈니스 분석등을 통해 비즈니스 기능을
    식별하고 구축할 소프트웨어의 도메인에 대한 이해를 발전시켜야 한다.
  * 도메인을 이해하는 것은 한 번에 끝나지 않고 계속 반복해야 한다. 사용자의
    요구사항이 바뀌고 제품은 끊임없이 진화하기 때문이다.

## 서비스간 협업하기

* 점대점
  * 동기방식
  * 간단하고 이해하기 쉽다.
  * 대부분의 프로그래밍 도구는 이미 알고 있는 전송 메커니즘을 지원한다.
* 이벤트 주도 방식
  * 비동기 방식
* 서비스 계약
  * 각 서비스가 수신하고 응답하는 메시지 계약이라는 것을 통해 정의가 되는데 이는
    협업하는 서비스가 각 서비스를 블랙박스처럼 취급하여 요청을 보내고 응답을
    받으면 그 서비스는 해야 할 일을 잘 하고 있는 것이다.
* 서비스 책임
  * 하나의 서비스가 다수의 책임을 가지게 되면 크기가 점점 커지고 이는 단단한
    결합을 만들어낸다.
* 자율적인 구성
  * 각 서비스가 다른 이벤트에 반응을 수행한다.
  * 매우 느슨하여 독립적으로 배포가 가능하고 변경이 쉬운 서비스를 구축할 수
    있다.
  * 하지만 메세지 큐를 사용한다면 관리와 확장이 필요한 또 다른 인프라스터럭처가
    필요하고 단일 장애지점이 생긴다.
  * 장애가 발생했을 때 다른 서비스에 영향이 가지 않지만 이는 시스템의 전체
    활동을 추적하는 것을 더욱 어렵게 한다.

## 서비스를 외부에 노출하기

* API Gateway
  * 애플리케이션 사용자 입장에서 백엔드를 추상화하여 하위에 있는 마이크로
    서비스들이 어떻게 협업하는지는 알 필요가 없게 한다.

## 운영 환경에 기능 반영하기

* 품질 관리와 자동 배포
  * 개발 프로세스를 표준화해야 한다. 코드리뷰, 테스트 작성, 버전 제어를
    관리한다.
  * 배포 프로세스를 표준화하고 자동화해야 한다. 코드 변경을 운영으로 전달하는
    것을 완전하게 검증하고 엔진니어의 개입을 최소하해야 한다.
* 회복성
  * 실패 시나리오의 영향을 최소화하도록 사전에 대책을 강구할 수 있는지
    고려해야 한다.
* 투명성
  * 로그를 수집하여 그 로그를 볼 수 있어야 한다.
  * 문제가 발생했을 때 알림 시스템을 가지고 있어야 한다.
  * 각 서비스에 하트비트 검사를 반복적으로 해서 응답하지 않으면 팀에 알림을
    보내야 한다.
  * 각 서비스에 대해 운영상 보장을 해야한다. 예를 들어 99.99%의 가용성을
    유지하면서 95%의 서비스가 100ms이내에 응답한다는 목표를 세울 수 있다. 이를
    만족하지 못하면 알림이 오게 만들어야 한다.

## 마이크로 서비스 개발 확장하기

* 기술적 다변화
  * 마이크로 서비스를 통해 다양한 언어와 프레임워크를 선택할 수는 있지만,
    선택에 대한 합리적인 표준과 제한이 없으면 시스템은 장애 확산에 취약하게
    구성된다.
  * 다양성과 확산을 관리하기 위해 모든 계층에 합리적인 표준을 두는 것은 매우
    중요하다. 예) 로그메세지 형식
* 격리
  * 각 팀은 목표가 담당 영역에 국한되더라도 전체 애플리케이션이 매끄럽게 실행될
    수 있도록 긴밀하게 협업해야 한다.

## Sources

* 마이크로 서비스 인 액션 - 모건 부르스, 파울로 페레이라
