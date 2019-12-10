---
title: 당근마켓 웹 개발 챌린지 회고
subTitle:
category:
tags:
createdat: 2019-12-10 10:54:00
updatedat: 2019-12-10 10:54:00
---

## 웹 개발 챌린지

접속 URL: https://www.daangn.shop/

새로운 카테고리를 추가하는 기능을 구현하는 챌린지였다. 기능으로 봤을 때는 단순해서 어려워 보이진 않았다. 리액트를 모르긴 하지만 대충 비빌 수 있다고 생각했다. 어떻게 평가할지가 굉장히 궁금했었는데 확장성과 가독성, 테스트를 고려해서 프로그램을 만들었는지에 대해 평가한다고 했다. 그런데 이런 문구가 있었다. `주어진 레거시 위에서`. 그래서 나는 만약 내가 개발팀에서 이 일을 진행한다면 어떻게 진행해야 할지에 대해서 고민을 하며 과제를 진행했다. 

![pr2](https://user-images.githubusercontent.com/14071105/70490034-afd43b80-1b40-11ea-83d5-ef317135e376.png)

![pr1](https://user-images.githubusercontent.com/14071105/70490024-ad71e180-1b40-11ea-9c72-be0a0a02b230.png)

## CI 적용

메인 `package.json`에는 `lint`를 실행하도록 스크립트가 정의되어 있었는데 막상 서버와 클라이언트에는 `lint`를 실행하는 스크립트가 정의되어 있지 않아 실행되지 않았다. 이것 먼저 고치는 것부터 시작했다. `Circle CI`를 설정하고 일단 실패하도록 설정했다. 그다음에 `lint`를 적용했다.

![](https://user-images.githubusercontent.com/14071105/70489015-d2b12080-1b3d-11ea-88be-cf7e48b97e8b.png)

팀원들과 같이 한다고 가정하고 프로젝트를 진행했다. 무작정 코드를 바꾸기보다는 점진적으로 바꿨고, 무조건 좋은 코드를 작성하는 것보다는 팀원들이 이해할 수 있어야 한다. 그래서 각 룰이 왜 변경되었는지 커맨트를 다 달았다.

### CD 적용

그다음엔 배포를 하기 위해 CD를 적용했다. 인프라를 만들기 위해 `terraform`을 이용해서 정의하여 인프라를 구축하고 `Circle CI`설정을 다음과 같이 정의하여 CD를 구축했다. 매번 pull request를 올릴 때마다 해당 커밋으로 태그를 달아서 AWS ECR에 push 하도록 만들었다. 그러면 내가 배포하고 싶은 커밋으로 배포하면 배포가 된다.

```yml
version: 2
jobs:
  build:
    docker:
      - image: circleci/node:12.13.0
      - image: circleci/mysql:8.0.18
        command: --default-authentication-plugin=mysql_native_password
        environment:
          MYSQL_ROOT_PASSWORD: password
          MYSQL_DATABASE: test

    working_directory: ~/repo

    steps:
      - run:
          name: "Setup custom environment variables"
          command: |
            echo 'export AWS_KEY="<AWS_KEY>"' >> $BASH_ENV
            echo 'export AWS_SECRET="<AWS_SECRET>"' >> $BASH_ENV
            echo 'export REPO="<AWS_ECR_REPO>"' >> $BASH_ENV
            echo 'export IMAGE="<IMAGE_NAME>"' >> $BASH_ENV

      - checkout
      - restore_cache:
          keys:
            - client-{{ checksum "client/package.json" }}

      - restore_cache:
          keys:
            - server-{{ checksum "server/package.json" }}
      - run: |
          cd client
          npm i --no-optional

      - save_cache:
          paths:
            - client/node_modules
          key: client-{{ checksum "client/package.json" }}

      - run: |
          cd server
          npm i

      - save_cache:
          paths:
            - server/node_modules
          key: server-{{ checksum "server/package.json" }}

      - run: |
          cd client
          npm run lint
          npm test
          npm run build:dev

      - run: |
          cd server
          npm run lint
          npm test
          npm run build

      - setup_remote_docker

      - run:
          command: |
            cd client
            npm run build
            cd ../server
            docker build -t $IMAGE .
            $(docker run --rm -e AWS_ACCESS_KEY_ID=$AWS_KEY -e AWS_SECRET_ACCESS_KEY=$AWS_SECRET anigeo/awscli ecr get-login --no-include-email --region ap-northeast-2)
            docker tag $IMAGE $REPO/$IMAGE:${CIRCLE_SHA1::7}
            docker push $REPO/$IMAGE:${CIRCLE_SHA1::7}
```

## e2e 테스트

e2e 테스트는 `CodeceptJS`를 이용해서 작성했다. 정말 제대로 하고 싶었는데 제대로 하려면 백도어 API도 만들고 해야 하는데 이건 너무 어려워서 간단하게 진행하기로 했다. 내가 구현해야 할 기능을 e2e 테스트로 정의하고 이 테스트를 통과시키기 위해 기능을 구현했다.

## Coverage 100%

![coverage](https://user-images.githubusercontent.com/14071105/70489384-fcb71280-1b3e-11ea-8ec5-d3fe2cb4a254.png)

서버 쪽은 커버리지 100%를 달성했다. 내 인생 첫 커버리지 100%였다. pull request를 보낼 때 커버리지를 확인하여 만약 이 전 커버리지보다 낮아지면 merge가 안되도록 하고 싶었다. 그래서 그런 봇들이 있나 찾아봤는데 찾지 못했다. 아마 `Code Climate`을 사용하면 쉽게 되겠지만 유료라서 그렇게 하진 못했다. 직접 만들까 했는데 일단 커버리지 100%를 달성하니까 내 스스로 직접 확인하여 100%인지 확인했다. 자동으로 확인 안 해도 내가 직접 수동으로 확인했다. 역시 한 번 달성하면 절대 내리기 싫었다. 처음에 커버리지를 달성하는 게 중요하다는 것을 배웠다.

## 도메인

`https://www.daangn.shop`도메인을 달았다. 가비아에서 daangn을 검색했는데 500원 밖에 안 해서 구매했다. AWS 로드밸런서에서 `www` 없이 `daangn.shop`에 접속했을 때 다음과 같이 설정하면 `www.daangn.shop`으로 리다렉션 시킬 수 있다는 것을 처음 배웠다.

![](https://user-images.githubusercontent.com/14071105/70489839-2290e700-1b40-11ea-95df-b3ac79bff40b.png)


## 아쉬웠던 점

* 250만점에 129.6점 받았다. 서버를 그냥 처음부터 만들 걸 그랬다. 애초에 레거시는 평가항목에 없었다. 나는 레거시가 있을 때 어떻게 프로젝트를 진행하는 것에 대해 더 집중했다. 그게 중요한 게 아니었다. 그냥 잘 만드는 게 중요한 것이었다.
* 레포를 공개할 수 없다. 저작권 문제 때문에 공개할 수 없어 아쉽다.

## Sources

* <https://programmers.co.kr/competitions/112/2019-daangn-blind-recruitment>
