---
title: 달랩 멘토링 짝 프로그래밍 실습 12번째 회고
subTitle:
category: 
tags: 
createdat: 2019-11-05 19:33:00
updatedat: 2019-11-05 19:33:00
---

## CodeceptJS

첫 E2E 테스트를 통과시키기 위해 React에서 상태를 변경시켰다. 클라이언트에서 현재 접속 상태에 따라 현재 상태를 출력해주도록 수정하고 E2E 테스트에서 이를 확인하려고 했는데 자꾸 에러가 발생했다. 이것 때문에 시간을 많이 소모했는데 CodeceptJS가 내부에서 어떤 일을 하는지 몰라서 파악하기 어려웠다. 테스트 실행 시 `verbose`모드로 해서 더 자세한 로그를 확인해서 좀 나아졌지만 정확한 원인을 파악하지 못했다.  

CodeceptJS의 기능을 더 공부해서 수정하던지 아니면 CodeceptJS를 사용하지 않고 `jest`만을 이용해서 테스트를 계속 작성할 것인지 선택해야 한다.

## Sources

* <https://dal-lab.com/>
* <https://github.com/dal-lab/project-auction-sniper>
* <http://www.kyobobook.co.kr/product/detailViewKor.laf?ejkGb=KOR&mallGb=KOR&barcode=9788966260836&orderClick=LAG&Kc=>
