---
title: 달랩 멘토링 짝 프로그래밍 실습 6번째 회고
subTitle: 달랩 멘토링 짝 프로그래밍 실습 6번째 회고
category: 
tags: 
createdat: 2019-09-10 13:31:00
updatedat: 2019-09-10 13:31:00
---

## Word counter

글자 수를 세는데 MapReduce를 사용하여 만들었습니다. 글자가 어떻게 잘려서 주어질지
모르기 때문에 빈 공백을 제대로 처리하지 않으면 잘못된 결과가 나올 수 있습니다.
이를 처리하는 로직도 만들고 바로 실행하는 게 아니라 값을 가져올 때 실행되도록
lazy 하게 작성하였습니다.

## 좋았던 점

* lazy하게 실행하는 방법을 배웠다.

## 아쉬웠던 점

* node.js에서 멀티쓰레드 구현이 어려웠다.
* Promise를 쓰는 로직이 굉장히 복잡했다.
* 주제를 미리 정해오자.

## Sources

* <https://github.com/hannut91/word-counter>
