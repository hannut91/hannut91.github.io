---
title: kbuectl에서 유용한 명령어 모음
subTitle: kbuectl에서 유용한 명령어 모음
category: 
tags: 
createdat: 2019-08-02 14:30:00
updatedat: 2019-08-06 10:22:00
---

## 자동완성 사용하기

```
$ kubectl completion bash > ~/.kubectl-completion.bash
```

* 다음과 같이 파일을 생성한 후 `.bashrc`에 다음과 같이 추가합니다.

```
[ -f ~/.kubectl-completion.bash ] && source ~/.kubectl-completion.bash
alias k='kubectl'
complete -F __start_kubectl k
```

## 네임스페이스 변경하기

```bash
$ kubectl config set-context $(kubectl config current-context) --namespace <namespace>
```

## 모든 노드의 IP 얻기

```bash
$ kubectl get no -o jsonpath='{.items[*].status.addresses[?(@.type=="ExternalIP")].address}'
```

## Deployments 관련

### rollout 상태 확인하기

```bash
$ kubectl rollout status deployment <name>
```

### 롤아웃 되돌리기

```bash
$ kubectl rollout undo deployment <name>
```

### 롤아웃 히스토리 조회하기

```
$ kubectl rollout history deployment <name>
```

### 특정 deployment revision으로 롤백하기

```bash
$ kubectl rollout undo deployment <name> --to-revision=1
```

### rollout pause

```bash
$ kubectl rollout pause deploment <name>
```

### roullout resume

```bash
$ kubectl rollout resume deployment <name>
```

## Sources

* <https://kubernetes.io/docs/reference/kubectl/jsonpath>
* <https://kubernetes.io/docs/reference/kubectl/cheatsheet>
