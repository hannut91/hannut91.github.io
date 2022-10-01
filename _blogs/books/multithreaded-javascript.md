---
title: 멀티스레드 기반 자바스크립트 서평
subTitle:
category:
tags:
createdat: 2022-10-01 17:43:00
updatedat: 2022-10-01 17:43:00
---

자바스크립트는 싱글 스레드 기반의 언어이다. 이 말은 자바스크립트가 단일한 환경
아래에서 실행된다는 것을 말한다. VM 인스턴스가 딱 한 개이며, 명령어 포인터가 딱
한 개라는 말이고, 메모리를 관리하는 가비지 컬렉터도 딱 한 개라는 의미다. 그래서
자바스크립트 인터프리터가 한 번에 하나의 명령어만 실행할 수 있는 것이다.  

자바스크립트가 싱글 스레드 기반의 언어긴 하지만, 그렇다고 애플리케이션 구현마저
싱글스레드로 제약을 걸어버릴 필요는 없다. 만들고자 하는 애플리케이션의 특성에
따라 멀티스레딩의 필요 여부와 방법을 판단해야 한다.  

그래서 이 책을 자바스크립트로 멀티스레딩을 구현하는 방법을 브라우저
환경에서부터 Node.js까지 소개해 준다.  

내가 자주 사용하는 것 중에 어디다 써먹을 수 있을까 생각해 봤는데, Redux에서 상태
변경을 하기 위해서 처리하는 부분을 다른 스레드에서 처리하면 어떨까 생각했다.
근데 이 생각을 나만 한 게 아니었다. 없으면 만들어보려고 했는데 이미 만들어진 게
있었다. 바로 `redux-in-worker`이다. reducer를 다른 worker 스레드에서 처리해서
UI를 담당하는 것과 상태 변경을 처리하는 것을 다른 스레드로 분리해낸 게
인상적이었다.

## 참고

* [개발자 한 달에 책 한 권 읽기 모임 회고 - 멀티스레드 기반 자바스크립트](https://hannut91.github.io/retrospective/reading-books/multithreaded-javascript)
* [React + Redux + Comlink = Off-main-thread](https://dassur.ma/things/react-redux-comlink/)
* [redux-in-worker](https://github.com/dai-shi/redux-in-worker)
* [멀티스레드 기반 자바스크립트 \| 토머스 헌터 2세, 브라이언 잉글리시 지음 \| 나민주 옮김 \| 루비페이퍼 \| 2022년 06월](http://www.kyobobook.co.kr/product/detailViewKor.laf?ejkGb=KOR&mallGb=KOR&barcode=9791186710838&orderClick=LAG&Kc=)
