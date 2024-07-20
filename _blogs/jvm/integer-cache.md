---
title: JVM의 정수 캐시란 무엇인가요?
subTitle:
category:
tags:
createdat: 2024-07-20 16:55:00
updatedat: 2024-07-20 17:09:50
---

```java
Integer v1 = 100;
Integer v2 = 100;
System.out.println(v1 == v2); // true

Integer v3 = 200;
Integer v4 = 200;
System.out.println(v3 == v4); // false
```

위의 코드를 실행하면, 윗부분은 true가 출력되고 아래는 false가 출력됩니다. 분명
참조를 비교하고 있는데 결과가 다르게 나오는 걸까요?  

그 이유는 JVM에서는 성능 최적화를 위해서 특정 범위의 정수 객체를 캐싱하기
때문입니다. 기본적으로 -128 ~ 127범위의 정수값을 캐싱합니다. 코드를 보면 마치 두
개의 인티저를 만드는 것 같지만 사실은 이미 만들어져 있는 것을 사용하는 것이죠. 해당 범위에 없는 값은 캐시로 동작하지 않기 때문에, 참조를 비교할 경우 다르다고
나오는 것입니다.  

만약 캐싱하는 값의 범위를 늘리고 싶다면 실행할 때 다음과 같이 옵션을 줄 수
있습니다.

```bash
java -XX:AutoBoxCacheMax=300 Main
```

하지만 만약 생성자를 이용해서 새로운 인스턴스를 만든다면 위와 같이 동작하지
않습니다.

```java
Integer v1 = new Integer(100);
Integer v2 = new Integer(100);

System.out.println(v1 == v2);
```

그래서 생성자를 직접 사용하는 대신 `valueOf` 팩토리 메서드를 사용해서 만들면,
캐싱된 값을 사용할 수 있는 경우 캐싱된 값을 사용하고, 아닌 경우에는 새로운
인스턴스를 만듭니다. 그래서 직접 인스턴스를 생성하는 대신 `valueOf`를 사용하는
것을 권합니다.

```java
Integer v1 = Integer.valueOf(100);
Integer v2 = Integer.valueOf(100);

System.out.println(v1 == v2); // true

Integer v3 = Integer.valueOf(200);
Integer v4 = Integer.valueOf(200);

System.out.println(v3 == v4); // false
```

## 참고

- <https://docs.oracle.com/en/java/javase/21/docs/api/java.base/java/lang/Integer.html>
- <https://kotlinlang.org/docs/numbers.html#numbers-representation-on-the-jvm>
