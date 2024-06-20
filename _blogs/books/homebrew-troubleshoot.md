---
title: brew update 에러가 발생할 때 고치기
subTitle:
category: 
tags: 
createdat: 2024-06-19 17:09:00
updatedat: 2024-06-20 16:26:11
---

```bash
$ brew update
==> Updating Homebrew...
fatal: couldn't find remote ref refs/heads/master
Error: Fetching /opt/homebrew/Library/Taps/heroku/homebrew-brew failed!
Error: Some taps failed to update!
The following taps can not read their remote branches:
  heroku/brew
This is happening because the remote branch was renamed or deleted.
Reset taps to point to the correct remote branches by running `brew tap --repair`
```

이 에러는 Homebrew에서 관리하는 heroku/brew tap의 원격 브랜치가 `master`에서
`main`으로 변경되어서, 브랜치를 찾을 수 없다는 에러입니다. 브랜치를 `main`으로
변경해서 문제를 해결해야 합니다. 다음 명령어를 실행하여 브랜치를 수정합니다.

```bash
brew tap --repair
```
