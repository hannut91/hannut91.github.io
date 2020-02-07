---
title: 커리된 함수란 무엇인가?
subTitle:
category:
tags:
featured_image: /images/curried.png
createdat: 2020-02-06 11:42:00
updatedat: 2020-02-06 11:42:00
---

![](/images/curried.png)

## 커리된 함수란 무엇인가요?

커리된 함수(Curried function)이란 여러 개의 매개변수를 받는 대신에 항상 정확히 하나의 매개변수를 받는 함수를 말한다.

## 커리된 함수를 왜 사용하나요?

1. 모나드를 사용하기 위해 사용한다.
2. 재사용을 위해 사용한다.
3. 부분 적용을 위해 사용된다.

## 커리된 함수는 어떻게 사용하나요?

예르들어 특정한 문자와 반복할 횟수를 입력받으면 반복한 횟수만큼 문자를 출력하는 함수가 있다.

```js
const repeatWith = (character, count) => character.repeat(count);

console.log(repeatWith('*', 5)); // *****
```

`repeatWith`함수는 두 개의 매개변수를 입력받는다. 이 함수를 매개변수를 하나만 받도록 수정하고, 매개변수를 받았을 때 값을 반환하는 것이 아닌 새로운 함수를 반환하는 함수로 해보자.

```js
const repeatWith = (character) => (count) => character.repeat(count);
```

이렇게 된 함수를 `커리된 함수`라고 부른다. 이제 커리된 함수를 이용해서 동일한 동작을 하도록 코드를 작성해보자.

```js
const repeatWith = (character) => (count) => character.repeat(count);

const repeatStar = repeatWith('*');

console.log(repeatStar(5)); // *****
```

이렇게 매개변수를 하나만 받도록 함수를 작성했고, 매개변수를 다 채우기 전에 함수를 호출하면 해당 매개변수가 적용된 새로운 함수를 반환한다. 반환된 함수를 실행하면 전에 입력했던 변수를 함수가 가지고 있고 이 변수를 이용해서 함수가 동작한다.

## Source

* 가장 쉬운 하스켈 책 5장 고차원 함수 <http://www.kyobobook.co.kr/product/detailViewKor.laf?barcode=9788994774619>
