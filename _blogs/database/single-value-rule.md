---
title: SQL에서 Single-Value Rule은 무엇인가?
subTitle:
category:
tags:
createdat: 2024-07-26 20:57:00
updatedat: 2024-07-26 21:07:43
---

Single-Value Rule이란 SQL 데이터베이스에서 `GROUP BY`를 사용해서 집계할 때, 각
그룹에 대해서 반환되는 모든 열이 단일 값을 가져야 한다는 규칙입니다. 예를들어서
다음과 같은 테이블이 있다고 가정해 보겠습니다.

| bug_id | project_id | fixed |
|---|---|---|
| 1001 | 1 | true |
| 1002 | 1 | true |
| 1003 | 2 | false |
| 1004 | 2 | true |

여기서 만약 다음과 같은 쿼리를 실행한다면 어떻게 될까요?

```sql
SELECT *
FROM bugs
WHERE fixed = true
GROUP BY product_id;
```

| bug_id | project_id | fixed |
|---|---|---|
| 1001 | 1 | true |
| 1003 | 2 | true |

위와 같이 출력됩니다. `project_id`로 그룹화 하고 있고 `bug_id`컬럼을 출력하고
있습니다. 예를 들어 `project_id`값 1에 해당하는 `bug_id`는 `1001, 1002` 두 개
입니다. 그러면 SQL은 row 2개로 표현합니다. 하지만 `GROUP BY`를 사용했기 때문에
`product_id`에 해당하는 각각 하나의 row만 반환됩니다.  

SQL은 컬럼에는 하나의 값만 표현할 수 있으므로 `bug_id`를 표현할 방법이 없습니다. 그래서 지금은 그중에 가장
먼저
나왔던 `1001`이 출력되고 있습니다. 이는 잘못된 값입니다. 칼럼에는 하나의
값만 있어야 올바르게 출력할 수 있습니다. 이를 Single-Value Rule이라고 합니다.  

따라서 GROUP_BY를 사용해서 집계할 때는 집계 함수를 사용해서 컬럼의 값이 하나임을 보장해야 합니다.

```sql
SELECT project_id, count(fixed)
FROM bugs
WHERE fixed = true
GROUP BY product_id;
```

| project_id | count |
|---|---|
| 1 | 2 |
| 2 | 1 |

`project_id`로 그룹화했기 때문에 단일 값이 보장되고, `fixed`컬럼을 `count`로 개수를 구하여 단일 값이 보장됐기 때문에 위 결과는 올바른 결과입니다.
