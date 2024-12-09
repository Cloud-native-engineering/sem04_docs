---
layout: default
title: 5.3 Longhorn
parent: 5. Deployment
nav_order: 3
---

# 5.3 Longhorn

Ich überlegte eine Weile, wie ich das Setup von Longhorn integrieren soll. Sollte es in den Installer des Clusters integriert werden oder mittels GitOps verwaltet werden?

Schon nach kurzer Zeit war mir klar, dass für den langfristigen Betrieb eine Möglichkeit erforderlich ist, Longhorn zu managen und Updates einzuspielen. Daher entschied ich mich, das Longhorn-Setup getrennt vom Kubernetes-Setup zu erstellen und in ArgoCD zu integrieren.

Da jedoch bereits ein Teil des Storage-Setups die lokalen Disks umfasst, bleibt dieser Teil im Kubernetes-Setup, während die Installation des Longhorn-Layers in ArgoCD vorgenommen wird.

## ArgoCD App definition

Die App-Definition wurde im folgenden GitHub Repository abgelegt: [github.com/cloud-native-engineering/sem04_k8s](https://github.com/Cloud-native-engineering/sem04_k8s)

1. Login to ArgoCD

```bash
argocd login --core
```

2. Set the current namespace to argocd.

```bash
kubectl config set-context --current --namespace=argocd
```

3. Create the Longhorn Application custom resource.

```bash
kubectl apply -f https://github.com/Cloud-native-engineering/sem04_k8s/longhorn/longhorn-application.yaml
```

4. Deploy Longhorn with the configured settings. (The ingress will be created with the app sync)

```bash
argocd app sync longhorn
```

## Datensicherung

Um Daten im schlimmsten Fall zu schützen, ist es wichtig, im Voraus zu planen, wie mit potenziellem Datenverlust oder Datenkorruption durch Container-Updates umgegangen wird.

### Snapshot

Longhorn unterstützt Snapshots, die es ermöglichen, zu einem bestimmten Zeitpunkt zurückzukehren. Dies ist besonders nützlich, wenn Updates eingespielt werden.

Die Snapshots können bequiem via UI oder API in Longhorn erstellt werden

### Backup

Ein CIFS-Share wurde als Backup-Speicher ausserhalb des Clusters eingerichtet. Longhorn integriert sich gut in dieses Setup, und Backups werden gemäss dem definierten Schema ausserhalb des K8s-Clusters gesichert. Die folgenden Schritte waren notwendig, um die Physical Volumes und das NFS-Backup einzurichten:

#### SMB/CIFS Backupstore einrichten

Die Dokumentation für das Setup kann direkt von den Hersteller Dokumentation herausgelesen werden: [Longhorn.io/snapshots-and-backups](https://longhorn.io/docs/1.7.2/snapshots-and-backups/backup-and-restore/set-backup-target/#set-up-smbcifs-backupstore)
