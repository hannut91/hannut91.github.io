---
title: Mac OS에서 Kubernetes 로컬 개발환경 세팅하기
subTitle: Mac OS에서 Kubernetes 로컬 개발환경 세팅하기
category: 
tags: 
createdat: 2019-07-29 22:08:00
updatedat: 2019-07-29 22:08:00
---

## Install

### Install kubectl

```bash
$ brew install kubernetes-cli
```

### Install a Hypervisor

* Docker Desktop이 깔려있다면 다음과 같은 명령어로 `hyperkit`이 설치되어 있는지
  확인합니다.

```bash
$ hyperkit -h
```

### Install Minikube

```bash
$ brew cask install minikube
```

* 최신 버전의 minikube는 `kubectl`을 패키징하고 있으며 $PATH에 `kubectl`이
  없으면 설치한다.

## Start Minikube

```bash
$ minikube start
```

* 단일 노드 쿠버네티스 클러스터를 실행시킬 뿐 아니라 cluster와 커뮤니케이션하기
  위해 kubectl을 설치하고 설정합니다.

## Sources

* <https://kubernetes.io/docs/setup/learning-environment/minikube/>
