---
title: Kotlin에서 refied란 무엇인가요?
createdat: 2024-07-01 10:21:00
updatedat: 2024-07-01 10:34:55
---

Kotlin과 Java에서는 제네릭을 사용할 때 컴파일러가 타입을 제거합니다. 그래서
런타임에는 제네릭 타입을 인식할 수 없습니다. 이를 타입 소거(type erasure)라고
합니다.

```kotlin
fun <T> printType() {
    println(T::class.java) // 컴파일 오류 발생
}
```

하지만 코틀린 인라인 함수는 함수의 바디가 호출되는 곳에 복사되기 때문에, 컴파일
타임에 타입 정보를 유지할 수 있습니다.

```kotlin
inline fun <reified T> printType() {
    println(T::class.java) // class java.lang.String

}

fun main() {
    printType<String>()
}
```

따라서 `refieid`는 인라인 함수에서만 사용할 수 있고, 런타임에 제네릭 타입 정보를
활용할 때 사용할 수 있습니다.

## 참고

- [Inline functions - Reified type parameters](https://kotlinlang.org/docs/inline-functions.html#reified-type-parameters)
