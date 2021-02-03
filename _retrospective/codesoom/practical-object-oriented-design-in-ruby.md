---
title: 코드숨 루비로 배우는 객체지향 디자인 스터디 회고
subTitle:
category: 
tags: 
createdat: 2021-02-04 02:06:00
updatedat: 2021-02-04 02:06:00
---

## 무엇? 왜? 어떻게?

각 챕터에서 가장 중요한 질문 하나만 뽑아서 그 질문에 대한 답을 만들어가며 스터디를 진행했다. 하나의 질문이다보니 사실 챕터의 이름이 거의 질문이 되었다. 객체지향 디자인, 의존성, 상속 등등  

각 개념에 대해서 무엇이고, 왜 사용하고, 어떻게 사용하는지에 대해 얘기했다. 그런데 이 개념에 대해 설명하려면 필수적으로 설명이 필요한 것들이 있다. 예를들어서 객체지향 디자인에 대해 얘기하려면 우선 객체지향과 디자인이 무엇인지 얘기해야 한다. 이런식으로 우리의 지식들을 쌓아가며 스터디를 진행했다.

## 예제 만들기

상속, 조합, 덕 타입에 대해서는 같은 문제를 각각의 방법으로 문제를 해결해보면서 문제점을 발견하고, 해결하는 방향으로 진행했다. 예를들어서 음료를 제조하는 것을 객체로 만들어보면 다음과 같다.

```javascript
class Beverage() {
  boil()
}

class Coffee extends Beverage {
  boil()
}

class Tea extends Beverage {
  boil()
}
```

그런데 만약에 스무디 같은 음료가 생기면 어떻게 할까? 스무디는 끓이지 않는다.

```js
class Smoothie extends Beverage {
  boil() {
    // Do nothing
  }

  shake()
}
```

그래서 아주 이상한 코드가 나왔다. 오버라이드하여 아무것도 안하는 것이다. 끓일 수 있는, 흔들 수 있는 행동할 수 있는 것들은 덕 타입이 적절하다.

```js
interface Boilable {
  boil()
}

interface Shakable {
  boil()
}

class Coffee implements Beverage {
  boil()
}

class Tea implements Beverage {
  boil()
}

class Smoothie implements Shakable {
  shake()
}
```

같은 문제를 다른 방식으로 풀어보면서 비교해봤다. 그래서 적합한 도구를 사용하는 것이 중요하다는 것을 배웠다.

## 좋았던 점

* 비교하면서 학습했던 것이 좋았다. 헷갈릴 수 있는 개념들에 대해서 정확히 이해하기 위해서 간단한 예제를 만들어서 적용해봤다. 앞으로도 비슷한 개념들이 있을 경우, 비교해야 할 경우에 예제를 적용해가면서 학습해봐야겠다.

## 아쉬웠던 점

* 책의 있는 예제들을 같이 따라해보는 것도 좋았을 것 같다.

## Sources

* 스터디 정리 - GitHub - <https://github.com/CodeSoom/Practical-Object-Oriented-Design-in-Ruby>
* 루비로 배우는 객체지향 디자인 서평 - <https://hannut91.github.io/blogs/books/practical-object-oriented-design-in-ruby>
* 루비로 배우는 객체지향 디자인 - 교보문고 - <http://www.kyobobook.co.kr/product/detailViewKor.laf?barcode=9788966261239>