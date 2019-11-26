---
title: 달랩 코딩 도장 6번째 회고
subTitle: 나누어 떨어지는 숫자 배열
category: 
tags: 
createdat: 2019-11-26 19:38:00
updatedat: 2019-11-26 19:38:00
---

## 나누어 떨어지는 숫자 배열

코딩 도장이 시간이 여유가 있다 보니 천천히 문제를 해결하는 방법을 연습할 수 있었다. 같이 한 분이 배우기만 해서 짝 프로그래밍의 의미가 덜한 것 같다고 하셨는데 사실 가르치면서 더 많이 배울 수 있었다. How to solve it을 실천하면서 처음에 문제를 정의하고 계획하는 것은 쉬운데 실행하면서 계획을 다시 점검하거나 이해 단계로 다시 돌아가서 계획을 변경하는 반복적으로 사용해야 하는데 쉽지 않았다. 이번에 정렬하는 계획을 세우지 않았다는 것을 중간에 발견해서 다시 계획을 수정하고 문제를 계속 풀어서 좋은 경험이 되었다.  

먼저 문제를 풀고 리팩토링을 하면서 `Guard Clause` 설명하면서 리팩토링 사이트를 처음 들어가 봤다. 생각보다 설명이 굉장히 간략하게 잘 설명되어 있었다. 심지어 자바스크립트로 모두 바뀌어있어서 더 보기 좋았다.  

깃 마지막에 빈 줄을 그냥 당연시하게 넣었는데 내가 설명하려다 보니 제대로 모르고 있다는 것을 발견했다. 빈 줄을 넣지 않으면 개행문자 들어가지 않아서 코드를 수정했을 때 변경 사항이 이상하게 보일 수 있어서 그런 것이었다.  

리팩토링을 통해 `filter`를 이용해서 풀었는데 `for`반복분을 사용하는 것보다 훨씬 표현력이 좋았다. `map`을 이용해서 풀려면 어떻게 해야 하는지 얘기하면서 `flatmap`얘기도 했다.  

`jest`의 에러 출력 방법이 `JUnit`이랑 달라서 이해하기 어렵다고 하신 분도 있었다. `jest`의 경우 리눅스의 있는 `diff`를 사용해서 출력하기 때문에 이것이 익숙하지 않다면 이해하기 어려울 수 있다고 했다.  

그리고 모나드 얘기도 했는데 아직 잘 몰라서 추가적으로 공부를 해야겠다.

## Sources

* <https://github.com/dal-lab/coding-dojo/pull/22>
* <https://programmers.co.kr/learn/courses/30/lessons/12910>
* <https://docs.google.com/document/d/1rXbprwR8g2-Vf9m5PrSISHsiQnTBYsQ6XFPbbwMzbdw/edit#heading=h.6mqzmiftgwu4>
* <https://refactoring.com/catalog/replaceNestedConditionalWithGuardClauses.html>