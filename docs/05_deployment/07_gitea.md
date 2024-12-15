---
layout: default
title: 5.7 Gitea
parent: 5. Deployment
nav_order: 7
---

# 5.7 Gitea

Gitea ist eine Open-Source-Software für Versionsverwaltung, die eine einfache, selbst gehostete Git-Service-Lösung bietet. Sie ermöglicht es Benutzern, Repositories zu erstellen, zu verwalten und mit anderen zu teilen. Gitea unterstützt Funktionen wie Issue-Tracking, Code-Review und Continuous Integration, um die Softwareentwicklung zu erleichtern.

# Erstellung eines ArgoCD Projekts

1. Setze den aktuellen Namespace auf argocd.

```bash
kubectl config set-context --current --namespace=argocd
```

2. Erstellen einer ArgoCD Application/Projekt

```bash
kubectl apply -f https://raw.githubusercontent.com/Cloud-native-engineering/sem04_k8s/refs/heads/main/gitea/gitea-application.yaml
```

3. Sync the ArgoCD Application (CLI or UI)
