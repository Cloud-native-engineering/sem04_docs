---
layout: default
title: 1. Einleitung
nav_order: 1
permalink: /
---

# Can Kubernetes with Distributed Storage Replace a Home NAS?

Im Zeitalter der digitalen Transformation suchen immer mehr private Haushalte nach zuverlässigen und effizienten Lösungen zur Speicherung und Verwaltung ihrer Daten. Ein zentraler Aspekt dabei ist die Datenhoheit und der Speicherort der eigenen Daten, welche beim Enduser liegen und nicht bei einem Cloud-Provider wie OneDrive von Microsoft oder Google Drive von Google. Traditionelle NAS-Systeme (Network Attached Storage) sind zwar weit verbreitet, stossen jedoch zunehmend an ihre Grenzen in Bezug auf Skalierbarkeit, Flexibilität und Verwaltung. Kubernetes (K8s) hat sich als leistungsstarke Plattform zur Orchestrierung von containerisierten Anwendungen etabliert, aber kann K8s mit verteiltem Speicher eine tragfähige Alternative zu einem herkömmlichen NAS für den Heimgebrauch darstellen? Diese Semesterarbeit zielt darauf ab, die Machbarkeit und Vorteile eines solchen Setups zu untersuchen. Durch die Implementierung und den Vergleich von Kubernetes mit verteiltem Speicher und einem traditionellen NAS sollen Aspekte wie Leistung, Benutzerfreundlichkeit, Kosten und Skalierbarkeit bewertet werden. Ziel ist es, zu bestimmen, ob K8s mit verteiltem Speicher eine praktikable und vorteilhafte Lösung für die private Datenspeicherung und -verwaltung bieten kann.

```mermaid
mindmap
  root((K8s with Distributed Storage vs. Home NAS))

    A[K8s with Distributed Storage]
      A1[Advantages]
        A1a["Highly scalable"]
        A1b["Automated failover"]
        A1c["Supports dynamic workloads"]
      A2[Challenges]
        A2a["Complex to set up"]
        A2b["Overkill for small environments"]
        A2c["Requires expertise in Kubernetes and storage solutions"]

    B[Home NAS]
      B1[Advantages]
        B1a["Easy to set up and use"]
        B1b["Centralized, simple file sharing"]
        B1c["Cost-effective for small storage needs"]
      B2[Challenges]
        B2a["Limited scalability"]
        B2b["Less dynamic"]
        B2c["Single point of failure without RAID"]

    C[Key Considerations]
      C1["Storage Needs"]
        C1a["Home NAS: Simple, centralized storage"]
        C1b["K8s: Distributed, scalable storage"]
      C2["Complexity vs. Simplicity"]
        C2a["Home NAS: Low complexity"]
        C2b["K8s: High complexity"]
      C3["Cost and Maintenance"]
        C3a["Home NAS: Low upfront cost, easy maintenance"]
        C3b["K8s: Higher cost, requires maintenance expertise"]

    D[Conclusion]
      D1["Home NAS: Better for basic, small-scale storage needs"]
      D2["K8s: Suitable for large, dynamic environments but overkill for home use"]
```

## Ziele

- **K8s vs NAS**: Ziel dieser Analyse ist es, die Stärken und Schwächen von Kubernetes (K8s) im Vergleich zu herkömmlichen NAS-Systemen herauszuarbeiten. Dabei sollen sowohl Leistung und Skalierbarkeit als auch Benutzerfreundlichkeit und Kosten berücksichtigt werden. Durch einen detaillierten Vergleich soll ermittelt werden, in welchen Anwendungsbereichen K8s eine sinnvolle Alternative zu NAS darstellen kann.
- **Distributed Storage**: Ziel ist es, die Implementierung und Nutzung von verteiltem Speicher innerhalb eines Kubernetes-Clusters zu untersuchen. Es soll dargestellt werden, wie diese Technologie zur Verbesserung der Datenverfügbarkeit und Sicherheit beitragen kann und welche Herausforderungen und Vorteile sich daraus für den Heimgebrauch ergeben.
- **GitOps**: Ziel ist es, die Deployment-Strategien einer eigenen personal Cloud für eigene Dateien mit GitOps zu implementieren und zu evaluieren. Dabei soll gezeigt werden, wie durch die Verwendung von GitOps-Praktiken ein automatisierter, effizienter und sicherer Bereitstellungsprozess für den Service erreicht werden kann.

## Dokumente

- [Einreichungsformular Semesterarbeit](../resources/artifacts/2024_Semesterarbeit04_Einreichungsformuar.pdf)

![wave](resources/images/footer.svg)
