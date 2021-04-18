---
title: 코드숨 오브젝트 스터디 회고
subTitle:
category:
tags:
createdat: 2021-04-18 18:36:00
updatedat: 2021-04-18 18:36:00
---

코드숨에서 객체지향이라는 주제를 가지고 12주 동안 스터디를 진행했다. 객체지향의 사실과 오해, 루비로 배우는 객체지향 디자인, 엘레강트 오브젝트 그리고 오브젝트로 스터디를 진행했다.  

지금까지는 다양한 주제에 대해서 스터디를 진행했는데, 하나의 주제에 대해서 여러 권의 책들을 가지고 스터디를 진행한 것이 처음이었다. 심지어 다음 책도 테스트 주도 개발로 배우는 객체 지향 설계와 실천
이라서 객체지향에 대해서 다시 공부할 예정이다.

## 한 주제를 깊이 VS 다양한 주제

하나의 주제를 깊이 스터디를 진행했을 때는 스터디 기간 동안 내가 실제로 적용할 수 있는 시간이 길어서 좋았다. 문제를 만났을 때 객체지향 패러다임으로 문제를 해결하면 어떻게 될까? 같은 고민을 했다. 예를 들어 어떤 페이지에서 상태에 따라서 다른 메시지를 보여주도록 하는 코드가 있었다.

```typescript
const { stickerStore } = useStickerStores();

if (stickerStore.status === 'SUCCESS') {
  alert('Do something');
}
```

이러한 코드는 객체를 굉장히 수동적인 객체로 만든다. 객체가 가지고 있는 상태가 밖으로 드러나기 때문에 객체는 단순히 자료형에 지나지 않는다. 우리는 객체에게 질문을 던지고 답변만 받을 수만 있다. 따라서 다음과 같이 현재 성공인지, 실패인지 판단하는 것을 객체에게 맡겼다.

```typescript
const { stickerStore } = useStickerStores();

if (stickerStore.isSuccess()) {
  alert('Do something');
}
```

반면에 하나의 주제를 계속 공부하다 보니 지루해지는 느낌도 있었고, 이미 알고 있는 것 같은 착각에 빠졌다. 
다양한 주제를 다루면서, 교차하면서 같은 주제를 다루고 그 과정에서 적용을 많이 해볼 수 있는 스터디를 만들어야겠다.

## Sources

* 오브젝트 - 교보문고 - <http://www.kyobobook.co.kr/product/detailViewKor.laf?barcode=9791158391409>
* 오브젝트 서평 - <https://hannut91.github.io/blogs/books/object>
