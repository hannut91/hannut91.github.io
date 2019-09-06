---
title: TypeScript 개발 환경 만들기
subTitle: test, lint, build까지 구축하기
category: 
tags: 
createdat: 2019-09-06 17:04:00
updatedat: 2019-09-06 17:04:00
---

TypeScript 개발 환경을 구축 해보겠습니다.

## 초기화 

```bash
$ mkdir ts-example
$ cd ts-example
$ npm init -y
```

## 테스트 작성
`src/calculator.test.ts`파일을 만들고 다음과 같이 예제를 작성합니다.
```ts
test("calculator", () => {
  expect(sum(3, 5)).toBe(8);
});
```

이런 `jest`르 설치하지 않아서 편집기에서 test를 인식하지 못합니다. `jest`와 
`typescript`를 설치해 줍시다.

```bash
$ npm i -D typescript jest @types/jest
```

`package.json`에 다음과 같이 추가합니다.

```json
"scripts": {
  "test": "jest"
}
```

그리고 테스트를 실행합니다.

```bash
$ npm test
```

<img width="447" src="https://user-images.githubusercontent.com/14071105/64415323-065c5480-d0d0-11e9-9359-b5a39ed0b026.png">


sum이 없다고 에러가 발생하는군요. sum을 만들어 줍시다. `src/calculator.ts`를
만들고 다음과 같이 작성합니다.

```ts
export const sum = (a: number, b: number) => a + b;
```

그리고 `src/calculator.test.ts`에서 import해줍니다.

```ts
import { sum } from "./calculator";
```

그리고 다시 테스트를 실행합니다. 그러면 에러가 발생합니다. jest에게 우리가
TypeScript를 사용하고 있다고 알리지 않았습니다. 아까 설치한 `ts-jest`를 이용해서
설정할 것입니다. 그전에 설치를 해줍니다.

```bash
$ npm i -D ts-jest
```

그 후 설정파일을 생성합니다.

```bash
$ ./node_modules/.bin/ts-jest config:init
```

그러면 `jest.config.js`파일이 만들어지고 다시 테스트가 잘 통과합니다! 그런데
아까 `sum`을 import할 때 패키지이름에 큰 따옴표를 사용했네요. 현재 큰 따옴표와
작은 따옴표를 섞어서 쓰고 있는데 저는 문자열을 사용할 때 작은 따옴표를 사용하는
것을 선호합니다. 작은 문자열을 강제로 사용하도록 tslint로 강제해봅시다.

## tslint 설정하기

```bash
$ npm i -D tslint
```

설치 후 기본 설정파일을 만듭니다.

```bash
$ ./node_modules/.bin/eslint --init
```

그러면 `tslint.json`이 생성됩니다. `package.json`에 명령어를 등록하여 lint를
실행해봅시다.

```json
"scripts": {
  "test": "jest",
  "lint": "node_modules/.bin/tslint src/**/*.ts"
},
```

```bash
$ npm run lint
```

기본 lint는 문자열을 만들 떄 작은 따옴표 보다는 큰 따옴표를 사용하도록
권장합니다. 작은 따옴표를 사용하도록 설정해봅시다. `tslint.json`에서 다음과 같이 추가합니다.

```json
"rules": {
  "quotemark": [
    true,
    "single"
]
```

그리고 lint를 실행하면 다음과 같이 수정하라고 알려줍니다.

```bash
ERROR: src/calculator.test.ts:1:21 - " should be '
```

직접 수정할 수 있지만 tslint로 바로 고칠 수 있습니다.

```bash
$ npm run lint -- --fix
```

## js로 변환

이제 TypeScript로 작성한 코드를 JavaScript로 바로 실행할 수 있도록 프리컴파일을
해보겠습니다.

먼저 설정파일을 추가합니다.

```bash
$ ./node_modules/.bin/tsc --init
```

 `package.json`에 다음과 같이 추가합니다. 
```json
"scripts": {
  "tsc": "./node_modules/.bin/tsc"
}
```

그리고 컴파일을 합니다.

```bash
$ npm run tsc
```

그러면 src폴더에 js파일이 생성된 것을 확인할 수 있습니다. 그런데 테스트 파일도
같이 컴파일이 되었습니다. 그리고 js파일은 따로 다른 폴더에 생성되도록 하고
싶습니다. 그럴 경우 다음과 같이 `tsconfig.json`을 수정하여 할 수 있습니다.

```json
{
  "compilerOptions": {
    "outDir": "./dist/",
  },
  "include": [
    "./src/**/*.ts"
  ],
  "exclude": [
    "**/*.test.ts"
  ]
}
```

다시 컴파일을 해보면 test파일을 컴파일 되지 않으며 dist파일에 js파일이 생성된 것을 확인할 수 있습니다.

## Sources

* <https://github.com/kulshekhar/ts-jest>