---
title: 달랩 멘토링 짝 프로그래밍 실습 9번째 회고
subTitle:
category: 
tags: 
createdat: 2019-10-15 12:42:00
updatedat: 2019-10-15 12:42:00
---

## 동작하는 골격 만들기

GOOSGBT 책에서 경매 스나이퍼 프로그램이 자바 기반으로 되어 있고 스윙 같은 모르는 것들로 만들어져 있어서 이해하기 어려웠다. 그래서 TypeScript로 만들면서 실습을 통해 더 공부하기로 했다.  

먼저 어떤 기술들을 사용해서 만들 것인지 상의했다. 프런트는 `TypeScript`와 `React`로 하기로 했고 e2e 테스트는 `CodeceptJS`를 이용하기로 했다. 테스트는 `jest`를 사용하고 자동화된 빌드는 `CircleCI`를 사용하기로 했다. 책에서 XMPP 역할을 하는 것은 `Socket.io`로 직접 구현하려다가 이  것은 중요한 것이 아니라서 `Pusher`와 `Sendbird`중 `Sendbird`를 선택했다.  

책을 읽을 당시에는 경매 서비스가 존재하고 그 서비스에 붙어서 필요한 API를 만들어야 하는 줄 알았는데 거의 채팅 서버랑 같았다. 애초에 거래소가 채팅 서버랑 거의 다를바가 없다는 것을 오늘 처음 알았다. 평소에 리얼타임 애플리케이션을 거의 만들어본 적이 없어서 이해하기 어려웠다.  

먼저 책에 나와있는 데로 이미 구현 코드가 있는 것처럼 e2e 테스트를 작성하고 그 테스트를 통과시키기 위해 코드를 작성했다. 애플리케이션 러너와 가짜 경매 서버를 만들었다. 

## 작성한 코드

* <https://github.com/dal-lab/project-auction-sniper/pull/1>

## 좋았던 점

* 혼자 책만 읽었다면 책을 다 읽어도 몰랐을 내용들을 알게 되었다.

## 아쉬웠던 점

* 바보가 된 느낌이었다.
* 책만 보고 이해한 사람이 몇 명이나 될까 궁금해졌다.

## Sources

* <https://dal-lab.com/>
* <https://github.com/dal-lab/project-auction-sniper>
* <http://www.kyobobook.co.kr/product/detailViewKor.laf?ejkGb=KOR&mallGb=KOR&barcode=9788966260836&orderClick=LAG&Kc=>


