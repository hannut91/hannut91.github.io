---
title: Closure Compiler 알아보기
subTitle: Closure Compiler 알아보기
category: 
tags: 
createdat: 2019-07-10 15:14:00
updatedat: 2019-07-10 15:14:00
---

## 요약

* `Closure Compiler`는 JavaScript를 다운로드와 실행 속도를 줄일 수 있는 도구다.
* 언어를 기계어로 컴파일하는 것이 아니라 JavaScript를 더 좋은 JavaScript로 
컴파일 한다. 
* JavaScript를 파싱하고 분석하여 쓰이지 않는 코드는 삭제하고, 재작성하여 최소화 
한다. 뿐만아니라 문법, 변수 레퍼런스, 타입들을 체크한다.

## 장점

* JavaScript파일 크기를 줄이고 더 효율적으로 실행 될 수 있도록 컴파일 한다.
* 잘못사용되었거나 위험이 있을 수 있는 코드에 대해 경고를 해준다.

## 실행

* 자바앱으로 CLI에서 실행할 수 있다.
* 웹으로 실행할 수 있다.
* RESTfull API로 실행할 수 있다.

## Web을 이용해서 시작하기

1. <https://closure-compiler.appspot.com/home>에 접속한 후 코드를 작성하여
   `compile`버튼을 누르면 오른쪽화면에 결과가 출력된다.

## CLI를 다운로드하여 실행

1. <https://dl.google.com/closure-compiler/compiler-latest.zip>다운로드받는다.
2. 압축을 푼다.
3. ```bash
$ java -jar compiler.jar --js foo.js --js_output_file foo-compiled.js
```

## Webpack을 이용해서 실행

* <https://github.com/webpack-contrib/closure-webpack-plugin>

## Sources 

* <https://developers.google.com/closure/compiler/>
