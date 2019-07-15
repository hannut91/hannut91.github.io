---
title: CircleCI에서 forekd 풀리퀘스트에서도 빌드되도록 수정하기
subTitle: CircleCI에서 forked repository에서 pull request를 만들어도 빌드가 
실행되도록 수정하기
category: 
tags: 
createdat: 2019-06-24 23:45:00
updatedat: 2019-06-24 23:45:00
---

## 문제

CircleCI를 만든 계정의 Pull request에서는 CircleCI 빌드가 실행되지만 forked된
Repo에서 생성한 pull request에서는 빌드가 실행되지 않음

## 해결책

* 프로젝트 설정에서 고급설정으로 들어가면 forked된 repo에서 생성한 pull
  request에서도 빌드될 수 있도록 설정할 수 있는 옵션이 있다.

![](https://user-images.githubusercontent.com/14071105/61230488-178a8400-a765-11e9-9bd0-a4be97ef2a01.png)
![](https://user-images.githubusercontent.com/14071105/61230492-19544780-a765-11e9-80b7-92a51a6b1066.png)
![](https://user-images.githubusercontent.com/14071105/61230498-1b1e0b00-a765-11e9-861c-9084b914c7e5.png)
