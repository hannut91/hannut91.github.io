---
title: VS Code extension 만들기 시작하기
subTitle: 
category: 
tags: 
createdat: 2019-10-02 14:03:00
updatedat: 2019-10-02 14:03:00
---

## 설치하기

[Yeoman](https://yeoman.io/)와 [VS Code Extension Generator](https://www.npmjs.com/package/generator-code)를 설치합니다.

```bash
npm install -g yo generator-code
```

## 프로젝트 생성하기

```bash
yo code
```

<img width="614" src="https://user-images.githubusercontent.com/14071105/66019352-f5133600-e51d-11e9-87b7-128c8ad4000f.png">

실행하면 Yeoman이 실행되면서 프로젝트 이름과 패키지 매니저는 어떤 것을 사용할 것이며 TypeScript를 사용할 것인지 JavaScript를 사용할 것인지 물어봅니다. 원하는 것을 선택합니다. 이 예제에서는 TypeScript를 사용합니다.

## 실행하기

```bash
code ./helloworld
```

생성된 폴더를 VS Code로 열고 `F5`키로 실행하거나 디버깅 탭에서 바로 실행하면 새로운 VS Code 창이 열리고 Command Palette(shfit+cmd+p)에서 `Hello World`라는 명령어를 실행하면 오른쪽 밑 하단에 메세지가 뜨는 것을 확인할 수 있다.

![](https://code.visualstudio.com/api/get-started/your-first-extension/launch.mp4)

## 살펴보기

`package.json`을 살펴보면 다음을 확인할 수 있는데 command는 실행할 커맨드 이름을 나타내고 title은 Command Palette에서 노출될 제목을 나타낸다.

```json
{
  "contributes": {
		"commands": [
			{
				"command": "extension.helloWorld",
				"title": "Hello World"
			}
		]
	}
}
```

`src/extension.ts`를 살펴보면 `registerCommand`함수 호출을 보면 
`extension.helloworld` 문자열이 보인다. `package.json`에서 살펴봤던 커맨드 이름과 같다.  
커맨드 실행시 인자로 받은 함수가 실행되며 `Hello World!`라는 문자열을 보여주는 기능만 있다. 여기서 
문자열을 변경하고 새로 열린 VS Code창에서 `Reload window`커맨드를 실행한다. 그리고 다시
`Hello World`커맨드를 실행해보면 변경된 문자열을 확인할 수 있다.

## Sources

* <https://code.visualstudio.com/api/get-started/your-first-extension>
* <https://github.com/microsoft/vscode-extension-samples>
* <https://code.visualstudio.com/api/references/contribution-points>