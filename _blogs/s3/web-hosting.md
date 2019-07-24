---
title: S3에서 SPA웹호스팅시 주의할점
subTitle: AWS S3에서 Single Page Application 웹 호스팅시 주의할점
category: 
tags: 
createdat: 2019-07-24 23:54:00
updatedat: 2019-07-24 23:54:00
---

## SPA(Single Page Application)

`SPA`에서 router를 해시모드가아닌 History모드로 사용할 떄 S3 Web hosting의
Error document를 Index document와 동일하게 잡아주어야 한다. 그렇지 않으면
root path가 아닌 다른 경로로 요청하면 403 Forbidden에러가 발생한다.

![](https://user-images.githubusercontent.com/14071105/61809842-0afadf80-ae79-11e9-9c51-1b8800848efb.png)
