---
title: Mac에서 Gcloud cli 설치하기
subTitle: Mac에서 Gcloud cli 설치하기
category: 
tags: 
createdat: 2019-07-31 19:22:00
updatedat: 2019-07-31 19:22:00
---

## Install

```bash
$ https://dl.google.com/dl/cloudsdk/channels/rapid/downloads/google-cloud-sdk-245.0.0-darwin-x86_64.tar.gz gcloud-sdk.tar.gz
$ tar -xf gcloud-sdk.tar.gz
$ ./google-cloud-sdk/install.sh
$ gcloud version
```

## Init

```bash
$ gcloud init
```

* 실행하면 로그인을 하라고 하고 Y를 입력하면 브라우저가 열려서 구글로 로그인할
  수 있습니다.
* 로그인 하고 기본 프로젝트와 지역을 선택하면 됩니다. 지역 정보는
  [여기](https://cloud.google.com/compute/docs/regions-zones)에서 확인할 수 
  있습니다.

## Connect kubectl to gcloud

* kubectl을 이미 있는 gcloud에 연결하려면 먼저 클러스터목록을 가져옵니다.

```bash
$ gcloud container clusters list
```

* 그 다음과 같이 입력하여 `kubeconfig`를 업데이트하여 kubectl로 gcloud에 연결할
  수 있습니다.

```bash
$ gcloud container clusters get-credentials <cluster-name>
```

## Sources

* <https://cloud.google.com/sdk/docs/quickstart-macos>
* <https://cloud.google.com/compute/docs/regions-zones>
