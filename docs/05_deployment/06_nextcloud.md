---
layout: default
title: 5.6 Nextcloud
parent: 5. Deployment
nav_order: 6
---

# 5.6 Nextcloud

Nextcloud ist eine Open-Source-Software für Filehosting und Kollaboration, die es ermöglicht, Dateien zu speichern, zu synchronisieren und mit anderen zu teilen. Sie bietet Funktionen wie Kalender, Kontakte, Aufgabenverwaltung und vieles mehr, um die Zusammenarbeit und Produktivität zu verbessern. Diese Software wird als private Cloud auf dem Cluster deployed.

Es wurden zwei Deployment values.yaml definiert. Eines dient als Testinstanz, welche zum Beispiel für das Testen einer neuen Version verwendet werden kann und eine SQLite-Datenbank verwendet. Aber auch eine Produktionsinstanz, welche eine eigene PostgreSQL-Datenbank neben den Applikations-Pods hat.

# Erstellung eines ArgoCD Projekts

1. Setze den aktuellen Namespace auf argocd.

```bash
kubectl config set-context --current --namespace=argocd
```

2. Erstellen einer ArgoCD Application/Projekt


```bash
# INT
kubectl apply -f https://raw.githubusercontent.com/Cloud-native-engineering/sem04_k8s/refs/heads/main/nextcloud-int/nextcloud-application.yaml

# PROD
kubectl apply -f https://raw.githubusercontent.com/Cloud-native-engineering/sem04_k8s/refs/heads/main/nextcloud/nextcloud-application.yaml
```

3. Create K8s Secrets, follow the documentation in the GitOps definition for the APP
   1. PROD: [nextcloud](https://github.com/Cloud-native-engineering/sem04_k8s/blob/main/nextcloud/README.md#secrets)
   2. INT: [nextcloud-int](https://github.com/Cloud-native-engineering/sem04_k8s/blob/main/nextcloud-int/README.md#secrets)

4. Sync the ArgoCD Application (CLI or UI)

## GitOps
