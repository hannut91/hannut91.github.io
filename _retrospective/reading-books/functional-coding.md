---
title: 개발자 한 달에 책 한 권 읽기 모임 회고 - 쏙쏙 들어오는 함수형 코딩
subTitle:
category:
tags:
createdat: 2023-04-01 17:34:00
createdat: 2023-04-01 17:34:00
---

오늘 모임에서 기대하는 것을 공유하고, 책을 읽으면서 좋았던 부분과 아쉬웠던
부분에 대해서 먼저 공유를 했다. 그리고 그룹으로 나눠져서 이야기를 이야기를
나누고 공유하는 시간을 가졌다.  

기대하는 것을 보니 책에서 나온 내용을 실제로 어떻게 적용하고 있는지에 대해 다들
궁금해하는 것 같았다.  

우리 그룹은 먼저 추상화 레벨에 대해서 이야기했다. 책에서 나온 내용은 상대적으로
단순해서 가능한 것 같은데, 실무의 복잡한 코드에서는 분석 자체가 가능한가?라는
의문으로부터 시작했다. 근데 그전에 추상화란 무엇인가부터 이야기를 나누었다.  

IDEA에는 클래스 레벨을 보여주는 기능이 있어서 참고할 수 있다는 이야기도
했다. 추상화 레벨을 나눈다는 것을 코드를 격리시킨다는 관점으로 바라보면 도움이
된다는 이야기도 했다. 책에서 추상화 레벨을 나누는 예제는 이미 문제를 해결한
상태고 코드가 변경이 된다는 것을 가정하지 않았기 때문에 처음부터 이렇게 추상화를
하는 것은 너무 이른 추상화가 아닌가 이야기도 나눴다. 그렇지만 작게 나누는 것은
재사용성에 좋고 의존성을 파악할 수 있어서 이렇게 추상화 레벨을 나누려는 노력을
하는 것은 좋다는 결론이 나왔다.  

자바스크립에서는 Lodash 같은 라이브러리가 Deep copy를 직접 구현할 필요가 없게
만들어주는데 다른 언어에서는 이런 라이브러리를 사용하지 않아서 직접 구현할 때
복잡성이 많이 증가한다는 이야기도 나눴다.  

함수형을 실제로 사용하는지에 대해서도 이야기를 나눴는데 RxJava를 사용하다 보니
사용하게 되었고, 함수형 자체보다 함수형에서 쓰는 개념 중에 유용한 것들은 많이
사용한다고 이야기를 나누었다.  

다른 그룹에서는 추상화 벽을 어떻게 팀원들과 합의를 해야 하는지에 대해서 이야기를
많이 나눈 것 같다.

## 참고

- [개발자, 한 달에 책 한 권 읽기 2023년 3월 모임](https://festa.io/my/tickets/event/3230)
- [쏙쏙 들어오는 함수형 코딩 서평](https://hannut91.github.io/blogs/books/functional-coding)