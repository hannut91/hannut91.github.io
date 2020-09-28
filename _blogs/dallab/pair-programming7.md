---
title: 달랩 멘토링 짝 프로그래밍 실습 7번째 회고
subTitle: 달랩 멘토링 짝 프로그래밍 실습 7번째 회고
category: 
tags: 
createdat: 2019-09-17 23:28:00
updatedat: 2019-09-17 23:28:00
---

## 프론트엔드 CI/CD CircleCI로 구축하기

서버 같은 경우에는 Dockerize를 해서 원하는 곳에 업로드를 하면 되는데 프런트 같은 경우에는 정적 
파일이라서 어떻게 해야 할지 정해야 했다. CircleCI는 빌드가 다 끝난 후 파일을 Artifact로 업로드를 
할 수 있는데 이렇게 되면 웹에서 파일을 다운로드할 수 있다. 간단한 웹을 테스트와 빌드를 하고
빌드 한 파일을 업로드를 하여 CircleCI 웹에서 다운로드할 수 있도록 구현했다. 이 파일을 S3에 올려서 배포하거나 서버로 배포할 수 있다. 다른 사람에게 파일을 전달할 때는 올라간 URL을 전달하여 확인할 수
있다.

## CircleCI와 TravisCI

TravisCI만 사용하다가 CircleCI를 사용했는데 TravisCI에서 쓰던 방식을 CircleCI에서 그대로 
쓰려다 보니 불편한 것도 있었고 제대로 동작하지 않는 것도 있었다. CircleCI에 너무 의존하지 않으려고 
이렇게 했었는데 더 좋은 방식이 있는데 배우려고 하지 않은 것 같다. 지금 구축한 것이 너무 느려서 개선하고 
싶었는데 CircleCI에 대해 좀 더 알아보고 수정해야겠다.

## Git commit guide

깃 커밋의 제목은 내가 한 작업의 의도를 작성하고 설명에는 구체적인 구현을 나타내야 한다는 것을 배웠다.

## 좋았던 점

* 내가 설치한 VS Code Extension에 대해서도 알게 되었다. 내가 설치했는데 사용하질 않아서 있는 지도
 몰랐는데 우연히 알게 됐다. 페어 프로그래밍을 하지 않았다면 아예 몰랐을 것 같다.

## 아쉬웠던 점

* 좋은 기능을 쓰려면 유료다. 사실 맞는 말이지만 공부할 때 돈이 들어서 좀 아쉽다.

## Sources

* <https://dal-lab.com/>
* <https://circleci.com/docs/2.0/artifacts/>
* <https://chris.beams.io/posts/git-commit/>
* <https://github.com/agis/git-style-guide>
