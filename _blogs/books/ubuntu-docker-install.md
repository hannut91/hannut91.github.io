---
title: Ubuntu에서 Docker 설치하기
subTitle:
category: 
tags: 
createdat: 2024-06-19 14:28:00
updatedat: 2024-06-19 14:35:50
---

```bash
$curl -fsSL https://get.docker.com -o get-docker.sh
$ sudo sh get-docker.sh
$ sudo usermod -aG docker $USER
```

## 문제 해결

만약 다음과 같이 에러가 발생한다면 현재 사용자가 권한이 없는 것으로 `sudo
usermod -aG docker $USER`명령어가 잘 실행되었는지 확인하고, 재접속해 봐야 합니다.

```bash
permission denied while trying to connect to the Docker daemon socket at unix:///var/run/docker.sock: Get "http://%2Fvar%2Frun%2Fdocker.sock/v1.45/containers/json": dial unix /var/run/docker.sock: connect: permission denied
```

## 참고

- [Install Docker Engine on Ubuntu](https://docs.docker.com/engine/install/ubuntu/#install-using-the-convenience-script)
