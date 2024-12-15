---
layout: default
title: 5.2 ArgoCD
parent: 5. Deployment
nav_order: 2

---

# 5.2 ArgoCD

ArgoCD wird zusammen mit dem Setup installiert. Es sind somit hier keine weiteren Schritte notwendig. Dies geschieht mittels `kubectl`, welches auf das Manifest des ArgoCD Projekts verweist.

## Installation von ArgoCD

1. Erstelle das `argocd` Namespace:

```bash
kubectl create namespace argocd
```

2. Installiere ArgoCD mit dem offiziellen Manifest:

```bash
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Zugriff auf das ArgoCD UI

Der Ingress gehört nicht zu den grundlegenden Diensten und wird in einem späteren Schritt installiert, da der Cert Manager Zertifikate und Secrets beinhaltet. Um dennoch auf ArgoCD zugreifen zu können, kann ein Portforward eingerichtet werden:

Weitere Informationen zur Installation und Konfiguration von Cert-Manager finden Sie in der [Cert-Manager Dokumentation](https://cert-manager.io/docs/).

```bash
kubectl port-forward svc/argocd-server -n argocd 8080:443
```
