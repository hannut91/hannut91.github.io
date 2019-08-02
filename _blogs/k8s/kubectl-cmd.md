---
title: kbuectl에서 유용한 명령어 모음
subTitle: kbuectl에서 유용한 명령어 모음
category: 
tags: 
createdat: 2019-08-02 14:30:00
updatedat: 2019-08-02 14:30:00
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

## 모든 노드의 IP 얻기

```bash
$ kubectl get no -o jsonpath='{.items[*].status.addresses[?(@.type=="ExternalIP")].address}'
```

## Sources

* <https://kubernetes.io/docs/reference/kubectl/jsonpath>
* <https://kubernetes.io/docs/reference/kubectl/cheatsheet>
