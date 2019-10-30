---
title: Git global 설정하기
subTitle: Global로 gitignore를 추가하거나 alias등을 만들 수 있습니다.
category: 
tags: 
createdat: 2019-10-30 14:08:00
updatedat: 2019-10-30 14:08:00
---

## Global gitignore 추가하기

`~/.gitginore_global`파일을 만듭니다.

```
touch ~/.gitignore_global
```

다음 명령어를 실행하여 Global 깃 설정 파일을 수정합니다.

```
git config --global core.excludesfile ~/.gitignore_global
```

혹은 직접 `~/.gitconfig`파일을 수정할 수도 있습니다.

```
[core]
	excludesfile = ~/.gitignore_global
```

## alias 만들기

자주 사용하는 기능은 alias를 만들면 타이핑하기 귀찮은 것들을 쉽게 사용할 수 있습니다. 간단하게는 
다음과 같이 명령어를 입력하여 만들 수 있습니다.

```bash
git config --global alias.co checkout
```

그러면 이제 `git commit`대신에 `git co`를 사용할 수 있습니다.  

혹은 직접 다음과 같이 `~/.gitconfig`파일을 수정하여 만들 수도 있습니다.

```
[alias]
    co = commit
```

단순한 매핑뿐만 아니라 다양한 기능들을 활용할 수 있습니다. 깃 명령어 뿐만 아니라 외부 명령어도 사용할 수 있는데 명령어 앞에 `!`을 붙여 다음과 같이 사용할 수 있습니다.

```bash
git config --global alias.visual '!gitk'
```

다음은 머지 된 브런치들을 한 번에 삭제하는 alias입니다.

```bash
[alias]
    cleanbranch = "!git branch -d $(git branch --merged | grep -v '\\<master\\>')"
```

## Sources

* <http://egorsmirnov.me/2015/05/04/global-gitignore-file.html>
* <https://git-scm.com/book/en/v2/Git-Basics-Git-Aliases>