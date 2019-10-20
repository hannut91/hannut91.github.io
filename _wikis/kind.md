---
title: kind
---

## Create cluster

```
kind create cluster --name <cluster-name> --config <config.yaml>
```

## Delete cluster

```
kind delete cluster --name <cluster-name>
```

## Interact with kind
```
export KUBECONFIG="$(kind get kubeconfig-path)"
kubectl cluster-info

# with cluster name
export KUBECONFIG="$(kind get kubeconfig-path --name="kind-m")"
```

## Sources

* https://github.com/kubernetes-sigs/kind
