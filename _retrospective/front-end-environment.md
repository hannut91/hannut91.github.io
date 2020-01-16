---
title: 프론트엔드 개발 환경의 이해 강의 회고
subTitle:
category:
tags:
createdat: 2020-01-16 19:09:00
updatedat: 2020-01-16 19:09:00
---

NPM, Babel, Lint, Webpack 등 프런트엔드 개발 환경에 대해 기본부터 실무에서 사용하는 사례까지 배웠다. JavaScript의 모듈 시스템에 대해 잘 몰랐는데 알게 되어서 좋았다. AMD와 CommonJS 등을 공부하고 싶었는데 JavaScript의 역사까지도 알고 있어야 해서 공부하기 참 어려웠다. 간단하게 알려주셔서 쉽게 이해할 수 있었다.  

Babel과 웹팩의 동작원리에 대해 알게 되어서 좋았다. 바벨 커스텀 플러그인과 만들 생각을 해 본 적이 없는데 커스텀 플러그인을 만드는 방법을 통해 동작원리를 알게 됐다. 웹팩의 커스텀 로더와 커스텀 플러그인도 만들어볼 생각이 없었는데 만드는 과정을 알려주셔서 동작원리를 더 잘 이해할 수 있었다. 웹팩의 `DefinePlugin`이란 플러그인을 처음 알게 되었다. 기존에 `react-cli`, `angular-cli` 그리고 `vue-cli`에서 당연하게 사용하던 기능들이었는데 실제로 웹팩에서 어떻게 동작하는지 어떤 플러그인을 사용해서 똑같이 구현할 수 있는지 자세히 알게 됐다. 웹팩을 직접 사용하지 않더라도 내부에서 어떻게 동작하는지를 알게 되어서 나중에 수정할 사항이 생기면 더 쉽게 접근할 수 있을 것 같다. 실무에서 겪었던 사례도 공유해주셔서 문맥이 더 잘 이해할 수 있었다.

## Pull request

강의자료를 보다가 고칠 곳을 발견해서 Pull request를 보냈다. 기여를 해서 일단 좋았고, 간단한 수정사항이라도 자세하게 설명하려고 노력했다. 좋은 연습이 됐다.

* <https://github.com/jeonghwan-kim/lecture-frontend-dev-env/pull/1>
* <https://github.com/jeonghwan-kim/lecture-frontend-dev-env/pull/2>
* <https://github.com/jeonghwan-kim/jeonghwan-kim.github.com/pull/127>

## 좋았던 점

* 초심자부터 숙련자까지 모두 들을 수 있는 강의였다.
* 실무에서 겪은 사례를 같이 얘기해주셔서 좋았다.

## 아쉬웠던 점

* 시간이 부족했다. 실습을 많이 못 해서 아쉬웠다.

## Sources

* <https://github.com/jeonghwan-kim/lecture-frontend-dev-env>
* <http://jeonghwan-kim.github.io/>
