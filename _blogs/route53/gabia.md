---
title: 가비아에서 구매한 도메인을 AWS Route53에서 호스팅하기
subTitle: 가비아에서 구매한 도메인을 AWS Route53에서 호스팅하기
category:
tags:
createdat: 2019-07-19 14:53:00
updatedat: 2019-07-19 14:53:00
---

가비아에서 구매한 도메인을 AWS를 통해 서비스하고 싶을 때 Route53을 이용해서
서비스할 수 있다.

## 요약

1. Route53에서 새로운 Hosted zone을 만듭니다.
2. Name server 목록을 가비아에서 네임서버 설정에 등록시킨다.
3. Route53에서 새로운 Record set을 만듭니다.

## Route53에서 Hosted Zone 만들기

![](https://user-images.githubusercontent.com/14071105/61511631-51dc7580-aa32-11e9-9793-a907faa996de.png)

* AWS console에 접속하여 Route53서비스를 선택한 후 `Hosted zones` 탭을 선택한다.
* `Create Hosted Zone`버튼을 클릭하면 오른쪽과 같은 화면이 나옵니다.
* 구매한 도메인을 입력하고 `Create`버튼을 클릭합니다.

![](https://user-images.githubusercontent.com/14071105/61511200-f2ca3100-aa30-11e9-88ab-3aaa523b82df.png)

* 생성된 `Hosed Zone`을 들어가 보면 Type에 `NS`라고 되어있는 값들을 가비아
  네임서버에 등록해 주어야 합니다.

## 가비아에서 네임서버 등록하기

![](https://user-images.githubusercontent.com/14071105/61511923-3f167080-aa33-11e9-8a6d-695a3bda62a5.png)

* 가비아에 접속하여 로그인 후 `My가비아`로 들어간 후 내려보면 내가 구입한
  도메인 목록이 있습니다.
* 해당하는 도메인의 관리 툴을 선택합니다.

![](https://user-images.githubusercontent.com/14071105/61512067-c1069980-aa33-11e9-9893-7ac030973ede.png)

* 네임서버에 설정을 누릅니다.

![](https://user-images.githubusercontent.com/14071105/61512235-383c2d80-aa34-11e9-98d8-abf8c90bfbd2.png)

* 이전에 `Route53`에서 `Hosted Zone`을 만들었을 때 생성됐던 네임서버를 모두
  입력합니다.
* 네임서버는 마지막에 `.`을 지우고 입력하여야 합니다. 예) 
  `ns-123-awsdns-43.com`
* 소유자 인증을 하고 적용을 누릅니다.

## Route53에서 Record Set만들기

![](https://user-images.githubusercontent.com/14071105/61512354-9b2dc480-aa34-11e9-8f5f-a39baa28725d.png)

* 이제 도메인을 연결하는 것은 끝났고 Route53에서 이제 Record set을 만들어
  서비스를 등록하면 됩니다.
* AWS를 이용해서 도메인을 연결한다면 `2`번 `Alias`를 `Yes`로 선택하여 서비스를
  선택합니다.
