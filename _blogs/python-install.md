---
title: 맥에서 pyenv와 virtualenv로 파이썬 개발 환경 설정하기
subTitle:
category:
tags:
createdat: 2024-06-01 17:24:00
updatedat: 2024-06-01 17:55:37
---

## Homebrew로 설치하기

```bash
brew update
brew upgrade
brew install pyenv pyenv-virtualenv
```

`.zshrc` 혹은 `.bashrc`파일에 다음 내용을 추가하여 pyenv와 pyenv-virtualenv를
초기화합니다.

```bash
eval "$(pyenv init -)"
if which pyenv-virtualenv-init > /dev/null; then eval "$(pyenv virtualenv-init -)"; fi
```

## 설치 확인하기

```bash
pyenv

pyenv 2.4.1
Usage: pyenv <command> [<args>]

Some useful pyenv commands are:
   --version   Display the version of pyenv
   activate    Activate virtual environment
   commands    List all available pyenv commands
# ...생략
```

## 원하는 파이썬 버전 설치하기

```bash
pyenv install 3.12.3
```

제대로 설치되었는지 확인해 봅니다.

```bash
pyenv versions

system (set by /Users/user-name/.pyenv/version)
3.12.3
```

## 프로젝트에 가상 환경 활성화하기

```bash
pyenv virtualenv <python-version> <project-name>

# 정상적으로 만들어졌는지 확인
pyenv virtualenvs
3.12.3/envs/project (created from /Users/user-name/.pyenv/versions/3.12.3)
<project-name> (created from /Users/user-name/.pyenv/versions/3.12.3)
```

## 가상 환경 활성화하기

```bash
pyenv local <project-name>
```

위 명령어를 실행하면 프로젝트 루트에 `.python-version`파일이 생성되고, 주어진
프로젝트 이름이 기록된 것을 확인할 수 있습니다. 그리고 해당 가상 환경이
활성화 됩니다.  

정상적으로 활성화됐다면 터미널 프롬프트 맨 앞에 프로젝트 이름이 붙은 것을 확인할
수 있습니다. 혹은 activate 명령어를 실행하면 다음과 같이 출력되는 것을 확인할 수
있습니다.

```bash
pyenv activate <project-name>
pyenv-virtualenv: version `<project-name>' is already activated
```

그런데 만약 다음과 같이 에러가 출력된다면 pyenv와 pyenv-virtalenv가 초기화가
안된 것으로, 초기화 코드가 제대로 실행되고 있는지 쉘 설정을 확인해야 합니다.

```bash
Failed to activate virtualenv.

Perhaps pyenv-virtualenv has not been loaded into your shell properly.
Please restart current shell and try again.
```

일단 쉘 설정 문제인지, 아니면 다른 문제인지 알아보기 위해서 임시로 두 명령어를
실행한 후 테스트해 보고, 만약 아래 코드가 실행이 안 된다면 pyenv와
pyenv-virtualenv가 제대로 설치된 건지 다시 확인해야 합니다. 만약 코드를 실행하고
올바르게 실행한다면 단순히 쉘 설정을 제대로 불러오지 못하는 것이므로, 쉘 설정을
올바르게 설정해야 합니다.

```bash
eval "$(pyenv init -)"
eval "$(pyenv virtualenv-init -)"
pyenv activate <project-name>
```

## 참고

- [The right way to install Python on a Mac](https://medium.com/marvelous-mlops/the-rightway-to-install-python-on-a-mac-f3146d9d9a32)
