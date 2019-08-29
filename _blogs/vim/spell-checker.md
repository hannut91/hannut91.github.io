---
title: Vim에서 한글맞춤법 검사기 만들기
subTitle: Vim에서 편하게 맞춤법을 검사해보자
category: 
tags: 
createdat: 2019-08-29 23:45:00
updatedat: 2019-08-29 23:45:00
---

Vim으로 블로그 글을 작성하다 보면 맞춤벙블 헷갈릴 때가 많다. 확실치 않은
경우에는 네이버 맞춤법 검사기를 통해 검사해서 수정하고 올렸다. 근데 이게 너무
귀찮다. 우리가 JavaScript 코드를 작성할 때는 잘 작성했는지 eslint로 검사를 하여
빠르게 피드백을 받는 것처럼 맞춤법도 맞춤법 lint가 있으면 어떨까 하는 생각에
만들기 시작했다.

## 실행 결과

내가 검사하길 원하는 영역을 선택하여 커맨드를 실행한다.

![](https://user-images.githubusercontent.com/14071105/63954079-7e69bf80-cabd-11e9-8043-84b417ef6682.png)

새로운 window가 열려 수정된 맞춤법을 확인할 수 있다.

![](https://user-images.githubusercontent.com/14071105/63954082-7f9aec80-cabd-11e9-8c48-751b06e27b65.png)

## 실행 방법

`.vimrc`에 다음과 같이 작성한다.

```
function! Spell()
    " 선택한 텍스트를 가져옵니다.
    let l:oldReg = getreg('"')
    normal! gv"ay
    let l:text = getreg('"')
    silent call setreg('"', l:oldReg)

    " Golang으로작성된 프로그램을 실행시켜 결과를 받습니다.
    let l:result = system("spell-checker '" . l:text . "'")

    " 새로운 window를 만들고 텍스트를 출력합니다.
    execute "new"
    silent call setline(1, l:result)

    " newline 캐릭터를 올바르게 출력하도록 수정합니다.
    execute ':%s/\%x00/\r/g'

    " 색깔을 출력합니다.
    execute ':AnsiEsc'
endfunction

command! Spell call Spell()
```

golang이 깔려있다고 가정하고 spell-checker를 설치합니다.

```bash
$ go get github.com/hannut91/spell-checker
```

잘 설치되었는지 확인하려면 다음과 같이 실행해 봅니다.

```bash
$ spell-checker "외않되"

# 외않되왜 않돼
```

## 전체 코드

* <https://github.com/hannut91/spell-checker>
