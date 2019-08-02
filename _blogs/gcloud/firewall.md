---
title: Gcloud SDK에서 외부에서 액세스 할 수 있도록 방화벽 규칙 바꾸기
subTitle: Gcloud SDK에서 외부에서 액세스 할 수 있도록 방화벽 규칙 바꾸기
category: 
tags: 
createdat: 2019-08-02 14:25:00
updatedat: 2019-08-02 14:25:00
---

## 방화벽 규칙 목록 출력하기

```bash
$ gcloud compute firewall-rules list
```

## 방화벽 규칙 바꾸기

```bash
$ gcloud compute firewall-rules create <name> --allow=tcp:<port>
```

