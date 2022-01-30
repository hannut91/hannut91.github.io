---
title: 코드숨 도메인 주도 설계 스터디 회고
subTitle:
category:
tags:
createdat: 2022-01-31 00:02:00
updatedat: 2022-01-31 00:02:00
---

코드숨에서 도메인 주도 설계 책을 가지고 6주 동안 스터디를 했다. 그리고
마켓컬리를 DDD를 적용한 프로젝트 스터디를 진행했다.

## 책 스터디

책 스터디는 책 내용만 다루기보다는 어떻게 책을 읽어야 하는지에 대해서 더 많이
다루었다. 이 책은 내용이 어려워서 집중해서 읽지 않으면 내용을 놓치는 것들이 많기
때문이다.

### 질문 만들기

책에서 나온 내용을 질문으로 만든다. 저자가 명확하게 의도를 드러낼 때가 있다면 쉽다.
에를 들어 책 서문에서는 "도메인 모델링과 설계는 뛰어난 소프트웨어 설계자들
사이에서 적어도 20년 동안 매우 중요한 주제로 인식되고 있지만 놀랍게도 뭘 해야
하고 어떻게 해야 하는지에 관해서는 기록된 바가 거의 없다."라고 이야기하고 있다.
즉 도메인 모델링과 설계란 무엇이며 어떻게 해야 하는지에 대해 앞으로 다룰
예정이라는 것이다 그러면 다음과 같이 질문을 작성할 수 있다.

* 도메인 모델링과 설계는 무엇을 해야 하고 어떻게 해야 하는가?

그러면 이 질문에 답할 수 있을 때까지 책을 읽는 것이다. 그러다가 놓치면 다시 이
질문으로 돌아와서 다시 답해본다. 답할 수 없다면 답할 수 있을 때까지 책을 읽는다.

## 프로젝트 스터디

도메인 주도 설계의 이론적이 부분만 공부하는 것은 아무런 의미가 없다고 생각하여
마켓컬리 앱을 클론 하는 프로젝트 스터디를 진행했다. 결제, 회원, 할인, 상품,
마케팅, 프런트팀으로 팀을 나누어서 프로젝트를 진행했는데 나는 마케팅팀으로 프로젝트를 진행했다.

### 사용자 스토리 작성하기

[사용자
스토리](https://github.com/CodeSoom/DDD-Kurly-Clone-Promotion/wiki/%EC%82%AC%EC%9A%A9%EC%9E%90-%EC%8A%A4%ED%86%A0%EB%A6%AC)
먼저 어떤 기능을 만들지 사용자 스토리를 작성했다. 그리고 이 스토리를 만들기
위해서 모델을 만들고 [유비쿼터스
언어](https://github.com/CodeSoom/DDD-Kurly-Clone-Promotion/wiki/UBIQUITOUS-LANGUAGE)를
정의했다.

### 코드리뷰를 할 때도 유비쿼터스 언어를 기준으로

![image](https://user-images.githubusercontent.com/14071105/151707381-cc145b47-49d2-4e44-8480-da07b28785cf.png)

유비쿼터스가 있다 보니, 코드리뷰를 할 때도 유비쿼터스 언어를 기반으로 코드리뷰를
하게 됐다. 코드를 읽다가 우리가 대화할 때 사용한 적 없는 단어가 나오면 이상하게
생각하고 코드리뷰를 하게 됐다. 이게 유비쿼터스 언어의 힘인 것 같다.

## 아쉬웠던 점

* 너무 해야 할 일이 많았다.
* 욕심이 너무 많았다.
* 결과물을 만들어내지 못해서 아쉬웠다.

## 다음에 시도해 볼 점

* 프로젝트형 스터디를 더 해보자.
* 다음 프로젝트형 스터디에서는 정기적인 모임 시간을 정하고, 할 일을 아주 작게
  나누어서 하고 싶은 사람이 자유롭게 참여할 수 있도록 해야겠다.

## Sources

* 도메인 주도 설계 -
  <http://www.kyobobook.co.kr/product/detailViewKor.laf?barcode=9788992939850>
* 도메인 주도 설계 서평 - <https://hannut91.github.io/blogs/books/domain-driven-design>
* [코드숨 스터디 화이트 보드](https://docs.google.com/spreadsheets/d/1r4M9aMCtf9I5-ZEFdTXv-SodmveJcZmr5stMUSFqDc8/edit#gid=0)
* 컬리 프로모션 팀 클론 레포 - <https://github.com/CodeSoom/DDD-Kurly-Clone-Promotion>