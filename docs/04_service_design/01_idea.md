---
layout: default
title: 4.1 Anforderungen
parent: 4. Service Design
nav_order: 1
---

# 4.1 Anforderungen

Die Grundidee ist es ein Kubernetes Cluster auf einem [TurinPi 2 Clusterboard](https://turingpi.com/product/turing-pi-2-5/) zu designen und aufzubauen. Dazu soll eine K8s-Distro, sowie eine Distributed Storage Solution evaluiert werden. Als Services soll eine alternative zu Google Drive, oder OneDrive von Microsoft evaluiert und deployed werden.

Dabei sind folgende Aspekte zu beachten:

- **K8s-Distribution**: Es soll eine K8s-Distribution evaluiert werden, die möglichst cloud-native administriert wird. Zudem soll die Festplatte mit den Daten verschlüsselt werden können.
- **Distributed Storage**: Die Distributed Storage Solution soll einfach zu verwalten sein und eine Möglichkeit bieten, die Daten ausserhalb des Clusters für ein Backup zu speichern.
- **GitOps**: Das Tooling sollte darauf abgestimmt sein, dass die Administration der Services möglichst GitOps-konform verwaltet wird.
- **Future-Proof**: Die ausgewählte Lösung soll sehr wartungsarm sein und einen langen Support bieten.
- **Hardware-Anforderungen**: Der gesamte K8s-Cluster soll auf einem TuringPi 2 Clusterboard betrieben werden.
