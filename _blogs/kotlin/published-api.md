---
title: Kotlin에서 @PublishedApi 어노테이션은 무엇인가요?
createdat: 2024-10-33 10:33:00
updatedat: 2024-10-08 10:55:34
---

A 모듈에서 다음과 같이 inline 함수가 있다고 가정해 보겠습니다. B 모듈에서는 해당 함수를 사용할 수 있습니다.

```kotlin
inline fun calculateResult(input: Int): Int {
    return input * 42
}
```

A 모듈에서 더 복잡한 코드를 작성하기 위해서 함수를 별도로 만들었습니다.

```kotlin
internal fun complexCalculation(input: Int): Int {
  // ...복잡한 로직 생략
  return input * 42
}

inline fun calculateResult(input: Int): Int {
  return complexCalculation(input)
}
```

그러면 이제 다음과 같은 에러가 발생하면서 컴파일 되지 않습니다.

```bash
Error: Cannot access 'internalFunction': it is internal in 'Module A'
```

internal은 모듈 내부에서만 접근할 수 있는데, inline함수는 함수 본문이 호출
위치에 복사되므로 B 모듈에서는 internal 함수에 대한 접근 권한이 없으므로 컴파일
오류가 발생합니다.

이때 해당 함수를 internal을 지워서 해결할 수도 있지만, 해당 함수를 공개하고
싶지는 않을 수 있습니다. 이때 `@PublishedApi`를 사용할 수 있습니다.

```kotlin
@PublishedApi
internal fun complexCalculation(input: Int): Int {
  // ...복잡한 로직 생략
  return input * 42
}

inline fun calculateResult(input: Int): Int {
  return complexCalculation(input)
}
```

이러면 해당 함수를 공개하지 않으면서, inline 함수 내의 internal 멤버에 접근할 수
있게 됩니다. 따라서 컴파일 오류가 발생하지 않고, inline 함수의 이점을 그대로 사용할 수 있습니다.

## 참고

- <https://kotlinlang.org/docs/inline-functions.html#restrictions-for-public-api-inline-functions>
- <https://kotlinlang.org/api/latest/jvm/stdlib/kotlin/-published-api/>
