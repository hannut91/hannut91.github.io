---
title: git bisect로 문제가 생긴 커밋 찾기
category:
tags:
createdat: 2024-09-25 21:05:00
updatedat: 2024-09-25 21:26:40
---

`bisect`명령어는 이진탐색으로 문제가 처음 생긴 커밋이 어딘지 찾는 명령어입니다.

예를 들어서 현재 커밋에서 문제가 발생하고 있는데, 이게 어떤 커밋부터 있던
문제인지, 올바르게 동작하는 가장 최신의 커밋은 무엇인지 궁금하다고 해봅시다.

프로그램을 실행하면 다음과 같은 에러가 발생하고 있습니다.

```bash
ReferenceError: use is not defined
```

그리고 현재 커밋의 상황은 다음과 같습니다.

```bash
* e87d175 - (HEAD -> main) 이름이 J로 시작하는 사람만 불러와라
* d5dd426 - 나이가 30살 이상인 사람만 불러와라
* cd82e14 - 미국에 사는 사람들만 출력해라
* eb54cdb - README를 추가해라
* bf5a3c6 - First commit
```

그리고 `First commit`은 에러가 없는 곳이 자명하기 때문에, 현재 커밋과 `First commit`사이에
에러가 처음 발생한 커밋이 반드시 있습니다. 이를 탐색하기 위해 `bisect`
명령어를 실행합니다.

```bash
$ git bisect start
status: waiting for both good and bad commits
```

시작하면 위와 같이 good과 bad를 선택해야 한다고 나옵니다. 현재 에러가 발생하고
있으므로 bad입니다. 그래서 다음과 같이 실행합니다.

```bash
$ git bisect bad
status: waiting for good commit(s), bad commit known
```

이제 good을 지정해 줘야 합니다. `First commit`의 해시를 지정해 보겠습니다.

```bash
$ git bisect good bf5a3c6
Bisecting: 1 revision left to test after this (roughly 1 step)
[cd82e14fe34b396884f6a5a9ba9e5cf29df4608c] 미국에 사는 사람들만 출력해라
```

그러면 이진 탐색을 시작하고, 최대 1 스텝이 남았다고 출력됩니다. 그리고 지금
확인 중인 커밋이 무엇인지 출력되고 있습니다.

```bash
* e87d175 - (HEAD -> main) 이름이 J로 시작하는 사람만 불러와라 # Bad
* d5dd426 - 나이가 30살 이상인 사람만 불러와라
* cd82e14 - 미국에 사는 사람들만 출력해라 # <- 현재 위치
* eb54cdb - README를 추가해라
* bf5a3c6 - First commit # Good
```

만약 현재 위치에서도 에러가 발생한다면 그 아래의 커밋도 잘못되었는지 확인해야
합니다. 만약 정상적으로 실행된다면 그 위의 커밋에서 잘못되었는지 확인해야
합니다.

코드를 실행해서 확인해 보니 문제가 없다고 가정해 보겠습니다. 그러면 good
커밋이겠죠?

```bash
$ git bisect good
Bisecting: 0 revisions left to test after this (roughly 0 steps)
[d5dd426b79b7e2fc45415aff341ea80bc7b7e7fa] 나이가 30살 이상인 사람만 불러와라
```

```bash
* e87d175 - (HEAD -> main) 이름이 J로 시작하는 사람만 불러와라 # Bad
* d5dd426 - 나이가 30살 이상인 사람만 불러와라 # <- 현재 위치
* cd82e14 - 미국에 사는 사람들만 출력해라 # Good
* eb54cdb - README를 추가해라 # 얘도 자동으로 Good으로 가정합니다.
* bf5a3c6 - First commit # Good
```

그러면 아래는 이제 검사할 필요가 없이 위의 커밋만 검사하면 됩니다. 이제 현재
커밋을 검사했을 경우 문제가 없다면 가장 위의 커밋이 처음 에러가 발생한 곳이고,
문제가 있다면 현재 커밋이 처음 에러가 발생한 곳입니다.

코드를 실행해보니 에러가 발생하네요. 그럼 이 커밋은 bad 커밋입니다.

```bash
$ git bisect bad
d5dd426b79b7e2fc45415aff341ea80bc7b7e7fa is the first bad commit
commit d5dd426b79b7e2fc45415aff341ea80bc7b7e7fa
Author: Username <user@gmail.com>
Date:   Wed Sep 25 20:00:59 2024 +0900

    나이가 30살 이상인 사람만 불러와라

 app.js | 5 +++--
 1 file changed, 3 insertions(+), 2 deletions(-)
```

이제 이진 탐색이 모두 끝났고 처음 문제가 발생한 커밋을 찾았습니다. 이런 식으로
반씩 나눠가며 문제가 발생한 곳을 훨씬 빠르게 찾을 수 있었습니다.

이제 초기화 명령어를 실행해서 마무리합니다. 이진 탐색 중간에라도 멈추고 싶다면, 초기화 명령어를 실행하면 됩니다.

```bash
$ git bisect reset
Previous HEAD position was d5dd426 나이가 30살 이상인 사람만 불러와라
Switched to branch 'main'
```

## 참고

- <https://git-scm.com/docs/git-bisect>
- <https://git-scm.com/docs/git-bisect-lk2009>
