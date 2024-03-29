---
title: HTTP/2 in Action 서평
subTitle:
category:
tags:
createdat: 2024-01-24 21:33:00
updatedat: 2024-01-26 16:26:31
---

HTTP/1.1은 진짜 오래 살아남았다. HTTP/1.1이 오래 살아남을 수 있었던 이유는
확장이 가능한 설계였기 때문이었다. 메서드로 충분한 기능을 구현할 수 있었고,
헤더를 통해서 기능을 확장할 수 있었고, 상태 코드를 분류해 놓아서 앞으로도 새로운
상태 코드를 추가해도 혼란이 크지 않도록 만들었다.  

하지만 본질적인 한계는 존재했다. 대기 시간이 길다는 것이다. 컴퓨터가 일하지 않고
놀고 있는 것을 지켜볼 수 없다. 긴 핸드 쉐이킹 과정, 패킷 손실 상황에서 TCP 통신의
한계, 현대 웹 서비스와 맞지 않는 TCP의 느린 시작, Stateless로 인해 점점 커가는
헤더의 크기 등 더 이상 현대 웹 서비스의 요구를 만족하기는 어려워졌다.  

그래서 Google은 자신만의 프로토콜을 만들고, 증명되어서 HTTP/2 표준이
만들어졌다. 이처럼 기술이 표준보다 훨씬 앞서간다.  

그렇다고 해서 기존의 시스템을 고려하지 않은 기술들은 외면받는다. HTTPS가 잘
전파되었었던 이유는 애플리케이션 서버에서는 전혀 인지하지 못하기 때문이다.
마찬가지로 HTTP/2도 그랬고 앞으로 QUIC도 UDP 위에서 구현한 이유가 기존의
시스템들을 고려했기 때문이다. 아무리 좋은 기술이라도 기존 시스템들을 모두
깨부숴야 한다면 외면받을 것이다.  

책에서는 새로운 기술을 도입할 때 내가 고려해야 하는 것들도 같이 배울 수 있어서
좋았다. 새로운 기술을 도입했다고 무조건 좋아진다기보다는 측정을 해서 검증을
해야 한다. 이전 기술을 최적화했던 게 오히려 새로운 기술에서는 안티 패턴이 될
수 있다. 다중 연결이나 콘텐츠 인라이닝 처럼.  

HTTP가 발전해 오고 있는 현재 상황과 현재의 문제점들에 대해서 알게 됐고 앞으로
어떻게 발전할지 그림을 그릴 수 있었다. 이제 새로운 HTTP가 두렵지 않을 것이다.

## 참고

* [코드숨 HTTP/2 in Action 스터디 회고](https://hannut91.github.io/retrospective/codesoom/http2-in-action)
* [HTTP/2 in Action \| 배리 폴라드 저자(글) · 임혜연 번역 \| 에이콘출판](https://product.kyobobook.co.kr/detail/S000001804952)
