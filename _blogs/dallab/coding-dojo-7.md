---
title: 달랩 코딩 도장 7번째 회고
subTitle: 예산
category: 
tags: 
createdat: 2019-12-18 15:00:00
updatedat: 2019-12-18 15:00:00
---

## 예산

예전에 풀어봤던 문제라서 `Kotlin`으로 다시 풀었다. 처음에 `How to solve it`에서 배웠던 대로 계획을 했었는데 `TDD`를 연습하고 싶어서 문제를 더 작게 자르려고 했다.  

첫 번째 실패하는 테스트를 작성하여 `Red`로 만들고 `3`을 직접적으로 리턴하도록 하여 `Green`을 만들고 리팩토링을 진행했다. 왜 `3`을 리턴해야 하는지에 대해 질문을 던졌다. `Magic literals`을 지우면서 코드를 리팩토링하고 올바른 결과가 나오도록 코드를 작성했다. 이미 정답을 알고 있어서 더 어렵게 풀기 위해서 차근차근 진행했다.  

처음에 계획을 작성하고 진행하고는 했는데 TDD는 결과로부터 다시 계획을 만들고 해서 혼돈이 왔다. 그렇다고 해서 계획을 안 하고 할 수는 없는 법이고 TDD로 문제를 작게 만들고 그 작은 문제에서 How to solve it을 이용해서 이해하는 과정과 계획을 세우고 실행하고 회고하여 문제를 푸는 방법을 더 연습해야겠다.

## Sources

* <https://programmers.co.kr/learn/courses/30/lessons/12982>
* <https://github.com/dal-lab/coding-dojo/pull/42>