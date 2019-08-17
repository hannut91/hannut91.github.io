---
title: Python으로 Front-end 개발하기 회고
subTitle: Python으로 Front-end 개발하기 회고
category: 
tags: 
createdat: 2019-08-17 22:50:00
updatedat: 2019-08-17 22:50:00
---

## Python으로 Front-end 개발하기

[아샬](https://www.youtube.com/user/ahastudio1004)님이 파이썬으로 웹 프론트엔드
개발을 실험을 한다고 하셔서 낼름 갔다. 파이썬으로 웹 프론트엔드를 개발하는
다양한 시도들이 있다.  

* Pyodide https://github.com/iodide-project/pyodide/
* Brython https://github.com/brython-dev/brython
* Transcrypt https://github.com/qquick/transcrypt
* PScript https://github.com/flexxui/pscript

이중에서 `Brython`은 브라우저에서 파이썬을 바로 실행할 수 있는 라이브러리다. 이
라이브러리를 이용하여 글만 적을 수 있는 인스타그램 Glstagram을 만들었다. 글을
입력받을 수 있는 input폼이 있고 등록하면 글 목록이 볼 수 있는 간단한 웹을
페어프로그래밍으로 만들었다.  
JavaScript로 개발할 때 `.js`파일을 import하는 것처럼 `.py`을 import하는 것이
신기했다. 그리고 실제로 잘 동작하였다. 테스트는 `pytest`로 테스트를 작성했다.
`document.getElementById`함수도 똑같이 동작하고 심지어 이벤트 바인딩은
`bind("click", function(){})`처럼 써서 더 간단해 보였다. `Vue.js`나
`Angular`처럼 프레임워크처럼 나오면 정말 좋을 것 같다.

## 좋았던 점

* 재밌었다. 웹 프론트라고하면 JavaScript가 기본이었는데 Python으로 한다는 것
  자체가 신기했다.

## 아쉬웠던 점

* 장소가 협소했다. 바닥이 너무 딱딱해서 엉덩이가 아팠다.
* datetime을 쓰는게 어려웠다. 이 부분은 라이브러리에 대해서 더 알아야 할 것
  같다.
