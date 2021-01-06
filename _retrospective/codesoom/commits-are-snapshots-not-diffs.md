---
title: 코드숨 Commits are snapshots, not diffs 스터디 회고
subTitle:
category:
tags:
createdat: 2021-01-07 00:30:00
updatedat: 2021-01-07 00:30:00
---

GitHub 블로그 글을 읽고 스터디를 진행했다. 좋은 블로그 글들은 엄청 많은데 항상 스크랩만 해놓고 안 읽는 것 같아서 스터디를 구실로 해서 제대로 읽어보자라고 생각해서 스터디를 하게 되었다.

## 문제집 만들기

이 블로그 글을 읽으면 우리는 무엇을 할 수 있게 될까? 제목처럼 Commit이 diffs가 아니라 snapshot인 이유를 설명할 수 있어야 할 것이다. 또한 실제로 증명도 할 수 있어야 할 것이다.

## 증명하기

Commit이 Snapshot인 이유를 증명하는 것은 간단한다. 파일을 하나 만들고 커밋을 한 다음에, 파일을 수정하고 나서 다시 커밋을 만든다. 그리고 Git에 저장된 실제 데이터를 불러온다. 그러면 이전 파일과 수정한 파일 둘다 데이터가 온전하게 저장되어 있다. 이걸 눈으로 확인했다.

## 예제 만들기

`git cherry-pick`과 `git rebase`에 대해서도 예제를 만들어봤다. 두 개의 브렌치를 만들어서 다른 브렌치의 커밋을 `cherry-pick`을 하여 결과를 확인해 봤다. 블로그에서 배웠던 내용을 실제로 하면서 눈으로 확인하니 더 많이 와닿았다. 그리고 누군가에게 설명할 때도 동일하게 보여줄 수 있을 것이다.

## 아쉬운 점

* 내가 모르는 것은 스터디의 진행이 원활하지 않다. `Patch`에 대해서는 나도 이해를 못 했더니 진행이 잘 안됐다. 앞으로 준비를 더 잘해야 겠다.

## Sources

* Commits are snapshots, not diffs - The GitHub Blog - <https://github.blog/2020-12-17-commits-are-snapshots-not-diffs/>
