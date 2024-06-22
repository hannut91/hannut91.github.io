---
title: W292 no newline at end of file는 무엇인가요?
subTitle:
category:
tags:
createdat: 2024-06-22 16:03:00
updatedat: 2024-06-22 16:05:55
---

## 문제

코드를 작성하다 보면 위와 같이 코드에 물결 표시가 나오는 것을 볼 수 있습니다.
마우스를 가져다 대면 파일 끝에 빈 줄이 없다는 에러가 표시되고 있습니다.

```
PEP 8: W292 no newline at end of file
```

## 해결

문서 맨 아래에 빈 줄 하나를 추가해야 합니다.

## 설명

위 경고는 문서가 빈 줄로 끝나지 않아서 나타나는 경고입니다. 빈 줄을 추가해야
하는 이유는 대부분의 에디터가 POSIX(Portable Operating System Interface) 표준을
따르기 때문입니다. 이 표준에 따르면 텍스트 파일의 마지막 라인은 빈 줄(newline)
문자로 끝나야 합니다.

<https://pubs.opengroup.org/onlinepubs/9699919799/basedefs/V1_chap03.html#tag_03_206>

이 마지막 라인에 빈 줄이 없으면 일부 도구는 파일이 제대로 종료되지 않았다고
간주할 수 있습니다.  

GitHub에서는 빈 줄이 없는 경우 다음과 같이 표시됩니다.

![깃헙 이미지](/images/blogs/python/newline/newline.png)

Git과 같은 버전 관리 시스템에서는 파일의 마지막에 빈 줄이 없는 경우 이를 변경 사항으로 간주할 수 있습니다. 이는 코드 리뷰와 병합 과정에서 불필요한 변경 사항으로 인식될 수 있어 혼란을 줄 수 있습니다.

```js
// Hello
```

만약 위와 같이 빈 줄이 없는 코드에서 아래에 코드를 추가하게 되면 GitHub은 다음과 같이 표시합니다.

```js
- // Hello
+ // Hello
+ // World
```

저는 단순히 아래 한 줄만 추가했는데 왜 세줄이 변경되었다고 나오는 걸까요? 그 이유는 줄바꿈 문자 `\n`가 들어갔기 때문입니다.

```js
- // Hello
+ // Hello\n
+ // World
```

만약 미리 빈 줄을 하나 추가한 상태에서 아래에 새로운 코드를 작성할 경우에는 다음과 같이 보여집니다.

```js
+ // World
```

이미 `\n`이 추가되어 있기 때문이죠. 따라서 코드 마지막 줄에 빈 줄 하나를 항상 추가해주는게 좋습니다.
혹은 자동으로 추가할 수 있도록 설정하는 방법도 있습니다.

![저장시 뉴라인 추가 설정](/images/blogs/python/newline/setting.png)
