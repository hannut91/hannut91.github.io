---
title: 엘레강트 오브젝트 서평
subTitle:
category:
tags:
createdat: 2021-03-01 11:27:00
updatedat: 2021-03-01 11:27:00
---

역자 서문에도 나오는 것처럼 저자의 말투가 굉장히 단정적이다. 저자는 객체지향 설계 원칙이 있고, 이것을 지켜야 한다고 말하고 있다.

## 이걸 다 지킬 수 있을까?

* 객체는 4개 이하의 객체를 캡슐화하라
* 항상 인터페이스를 사용하라
* 퍼블릭 상수를 사용하지마라
* 생성자 하나를 주 생성자로 만들어라
* 생성자에는 코드를 넣지 말아라

등등 많은 원칙들이 등장한다. 과연 이것들을 다 지킬 수 있을까? 지키고 있는 사람들이 있긴 한 걸까?  

이러한 원칙들을 무조건 지키기보다는 우리의 코드가 무언가 잘못되었는지 감지하는 신호들로 여기는 게 좋다. 예를 들어 내가 퍼블릭 상수를 만들려고 하고 싶을 때 다른 대안은 없을까? 고민할 수 있고, 객체에 캡슐화된 객체가 너무 많아질 때도 다르게 분리해야 하지 않을까? 고민해 볼 수 있다.

## 적용하기

내가 작성했던 코드들에 대해서 이 원칙들을 가지고 비교를 해봤다. 기존 코드는 객체의 내부 상태를 그대로 밖으로 드러내고, 그 속성을 밖에서 비교하는 코드를 작성했었다.

```typescript
const statusStore = {
  status: Status.Initial,
  message: '',
};

if (statusStore.status === Status.Fail) {
  // Do something
}
```

상태가 성공인지 실패인지를 객체가 하고 있는 것이 아니라 외부에서 무언가가 하고 있다. 이것은 객체를 자율적인 유기체로 바라보는 것이 아니라 단순한 자료구조로 바라보고 있는 것이다. 그래서 객체에게 메시지만 보내고 알아서 처리하도록 변경했다.

```typescript
const statusStore = {
  status: Status.Initial,
  message: string,
  isFail() {
    return this.status === Status.Fail;
  }
}

if (statusStore.isFail()) {
  // Do something
}
```

이제 이 객체는 실패를 내부에서 알아서 판단한다. 내부에서 실패를 판단하는 방법을 객체가 바꾸더라도, 이 퍼블릭 인터페이스를 의존하고 있는 다른 코드들에 영향을 주지 않는다.

## 좋았던 점

* 좋은 객체지향설계에 대한 지향점을 얻을 수 있었다.

## Sources

* 코드숨 엘레강트 오브젝트 스터디 회고 - <https://hannut91.github.io/retrospective/codesoom/elegant-objects>
* 스터디 정리 - GitHub - <https://github.com/CodeSoom/elegant-objects>
* 엘레강트 오브젝트 - 교보문고 - <http://www.kyobobook.co.kr/product/detailViewKor.laf?barcode=9791187497219>
