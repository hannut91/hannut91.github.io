---
title: 달랩 멘토링 짝 프로그래밍 실습 13번째 회고
subTitle:
category: 
tags: 
createdat: 2019-11-12 19:04:00
updatedat: 2019-11-12 19:04:00
---

## CodeceptJS 제거

우리가 하려는 테스트는 프론트부터 백엔드까지 전부를 테스트하려고 하는 건데 CodeceptJS는 브라우저 동작을 테스트하는 것에 맞춰져 있어서 어려움이 있었다. 결국 CodeceptJS 대신에 jest와 puppeteer만 사용해서 테스트를 하기로 했다.

## 첫 테스트 통과

그래서 드디어 첫 테스트가 통과했다. 책에서 나오는 가장 첫 번째 e2e 테스트 인데 드디어 통과했다. 이 과정에서 Sendbird를 사용할지 Pusher를 사용할지 고민을 하고 테스트는 CodeceptJS를 사용하여 개발할지 jest와 puppeteer로 테스트할지 그리고 Typescript를 사용할지를 시도해보면서 결정을 했다. 동작하는 골격부터 만드는 것이 아니라 처음부터 React를 사용해서 프론트를 만들었다면 이런 고민을 하지 않았을 것이고 나중에 생길 문제들을 일찍 발견하지 못했을 것이다.

## 작성한 코드

* <https://github.com/dal-lab/project-auction-sniper>

## Sources

* <https://dal-lab.com/>
* <https://github.com/dal-lab/project-auction-sniper>
* <http://www.kyobobook.co.kr/product/detailViewKor.laf?ejkGb=KOR&mallGb=KOR&barcode=9788966260836&orderClick=LAG&Kc=>
