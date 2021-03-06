---
title: chown command
subTitle: chown 커맨드 사용방법 정리
category: 
tags: 
createdat: 2019-02-05 23:20:14
updatedat: 2019-02-05 23:20:14
---

## 내용

* `chown`커맨드로 파일이나 디레고리의 소유자를 변경하거나 그룹을 지정할 수
  있습니다.
* 파일을 소유하고 있는 유저이거나 `root`유저만 변경할 수 있습니다.
* `root`유저가 아니라면 소유자가 속해있는 그룹으로만 변경할 수 있습니다.
* 만약 심볼릭 링크가 입력되고 `-h`플래그를 지정하지 않았다면 `chown`커맨드는
  링크 자체가 아닌 링크가 가리키고 있는 파일 혹은 디렉토리의 소유권을 
  변경합니다.
* 만약 `-h`플래그를 지정한다면 `chown`커맨드는 반대로 링크자체의 소유권만
  변경합니다.
* `-R`플래그를 지정한다면 `chown`커맨드는 지정된 디렉토리로 반복적으로
  내려갑니다.
* `-R`과 `-h`둘다 지정한다면 반복적으로 내려가면서 심볼릭 링크가 가리키는 곳이
  아닌 링크만 소유권을 변경합니다.
* userID는 `/etc/passwd`, groupID는 `/etc/group`에서 확인할 수 있습니다.

## 사용법

chown [ -f ] [ -h ] [ -R ] Owner [ :Group ] { File ... | Directory ... }

## Flags

* -f
  * 사용메세지를 제외한 모든 에러 메세지들을 생략합니다.
* -h
  * 심볼릭 링크가 가리키는 것의 소유권을 변경하는게 아니라 링크 자체의 소유권을
    변경합니다.
* -R 
  * 각 파일의 권환을 변경하고 폴더가 있으면 들어가서 소유권을 계속 변경합니다.
    symbolic link가 발견되면 링크가 폴더의 소유권은 변경하지만 그 폴더는 더 
    이상 진행하지 않습니다.

## 예제

### Example #1

* text.txt의 소유권을 foo에게 변경하려고 할 때

```bash
chown foo text.txt
```

### Example #2

* `/src`의 소유권을 foo에게 변경하려고 할 떄

```bash
chown foo -R /src
```

## Sources

* http://nersp.nerdc.ufl.edu/~dicke3/nerspcs/chown.html
