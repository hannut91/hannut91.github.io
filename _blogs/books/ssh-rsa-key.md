---
title: SSH RSA키는 어떻게 만드나요?
subTitle:
category: 
tags: 
createdat: 2024-06-20 14:49:00
updatedat: 2024-06-20 16:26:11
---

```bash
ssh-keygen -t rsa -b 4096 -C "youremail@gmail.com" -f ./key-name -N ""
```

- `-t rsa`는 RSA 형식의 키를 생성합니다.
- `-b 4096`은 비트 크기를 4096으로 설정합니다. 기본값은 2048입니다.
- `-C "youremail@gmail.com"`은 키에 주석을 추가합니다. 주로 키를 구분하기 위해서
  사용됩니다. 입력한 이메일은 퍼블릭 키 맨 뒤에 추가됩니다.
- `-f ./key-name`은 파일을 저장할 위치와 파일 이름을 지정합니다. 기본값은
  `~/.ssh/id_rsa`입니다.
- `-N ""`은 패스프레이즈를 빈 문자열로 설정합니다.
