---
layout: default
title: 8. Fazit und Zusammenfassung
nav_order: 8
---

# 8. Fazit und Zusammenfassung

Im Rahmen meiner Semesterarbeit konzentrierte ich mich auf die Implementierung eines Kubernetes Clusters mit verteiltem Speicher. Ziel war es, einen Vergleich zu einem konventionellen Network-Attached-Storage (NAS) zu machen. Dabei wurden Verfügbarkeit, Skalierbarkeit und Sicherheit zusammen mit den Kosten verglichen. Verschiedene Technologien wie ArgoCD, Longhorn, Talos Linux, Cilium, Cert-Manager, Renovate Bot und Nextcloud wurden integriert.

Die Planung meiner Arbeit erfolgte mittels der Jira Software von Atlassian, welche als öffentliche SaaS-Lösung bezogen wurde. Die gesamte Arbeit wurde in drei agilen Sprints organisiert:
- **Erster Sprint**: Einrichtung des Kubernetes Clusters und Implementierung der grundlegenden Infrastruktur.
- **Zweiter Sprint**: Integration der Distributed Storage Technologie sowie der GitOps-Tools.
- **Dritter Sprint**: Deployment der einzelnen Services, wie Nextcloud oder auch Gitea, und Durchführung von Integrationstests.

Neben der gesamten agilen Projektplanung wurde auch ein Fokus auf die Risiken sowie das Zeitmanagement gelegt, indem sämtliche Arbeitsschritte in Jira dokumentiert wurden.

Mit dem Service Design wurden die optimalen Bausteine für den Kubernetes Cluster gelegt. Dabei wurden die K8s-Betriebssysteme, Storage Provider sowie die Software für CI/CD evaluiert. Des Weiteren wurde die vertiefte Integration in das bestehende Heimnetz geplant. Dabei wurde vertieft auf die Hardware, den TuringPi 2, eingegangen. Auch wurden die Kosten des Setups berücksichtigt, einschliesslich des Stromverbrauchs und dessen indirekten Kosten.

Der TuringPi wurde in einem weiteren Abschnitt mit einem Network Attached Storage verglichen. Dabei wurden die Stärken und Schwächen der beiden Produkte gegenübergestellt und miteinander verglichen. Einer der Hauptunterschiede war, dass die Balance zwischen Kosten und Redundanz unterschiedlich ist. Der Kubernetes-Cluster mit Longhorn bietet jedoch die Möglichkeit, dies variabel zu definieren. Somit kann ich pro PVC definieren, wie sicher die Daten geschützt werden müssen, indem Longhorn verschiedene Replikate auf den K8s-Nodes ablegt.

## Challenges and Solutions

Die Bereitstellung eines unveränderlichen Kubernetes-Clusters mit Talos stellte Herausforderungen dar, insbesondere mit einer frühen Version der Talos Software, die den Rockchip nicht nativ unterstützte. Dies erforderte das eigenständige Kompilieren und Bauen des Kernels, was tiefe Einblicke in den Build-Prozess und Hardware-Kompatibilitätsprobleme bot. Im Januar wurde schliesslich bekannt, dass TALOS Linux den RK1 System-On-Chip nativ in der [factory.talos.dev](https://factory.talos.dev/) unterstützt. Dadurch konnte ich das Setup erfolgreich umstellen und die native Integration von Talos verwenden.

Zunächst wurde Dependabot für das Abhängigkeitsmanagement verwendet, später jedoch auf Renovate Bot umgestellt. Dieser Wechsel erfolgte aufgrund der überlegenen Konfigurationsoptionen von Renovate Bot. Der Hauptgrund war, dass mehrere Technologien unterstützt wurden, wie K8s-YAML-Manifeste, Helm und Kustomize. Zudem konnte Renovate Bot rekursiv scannen, was Dependabot von GitHub nicht konnte.

Ein weiteres Problem trat bei der Verwendung des Gitea Helm Charts auf, das auf Alpine Linux Containern basierte. Es wurde festgestellt, dass der Gitea-Container keine Verbindung zur Datenbank herstellen konnte. Nach eingehender Untersuchung und Debugging mit einem Debug-Init-Container stellte sich heraus, dass das Problem mit dem DNS zusammenhing, das verhinderte, dass der Gitea-Container die Datenbank in einem anderen Container erreichen konnte. Da das Problem darauf zurückzuführen war, dass Alpine-Container vom Helm Chart verwendet wurden, wurde schliesslich beschlossen, eine SQLite-Datenbank für Gitea zu verwenden. Die Last und die Performance des Services erfüllten die Anforderungen, da die Datenbank auf einer SSD-basierten Storage Class liegt.

## Resultate

Rückblickend wurden alle definierten Ziele der Semesterarbeit erreicht. Der Vergleich zwischen einem Home-NAS und dem TuringPi wurde sehr genau durchgeführt und es wurden einzelne Grafiken erstellt, die die Unterschiede aufzeigen. Auch die Integration der einzelnen Services wurde erfolgreich durchgeführt. Die Risiken wurden im Vorfeld erkannt und konnten durch die agile Projektplanung minimiert werden. Auch das Zeitmanagement wurde erfolgreich durchgeführt. Die Kosten wurden im Vorfeld abgeschätzt und konnten eingehalten werden. Die Arbeit wurde erfolgreich abgeschlossen und die Ziele erreicht.

## Future Work

Durch die Arbeit an diesem Projekt habe ich wertvolle Erfahrungen im Umgang mit Kubernetes und verteiltem Speicher gesammelt. Besonders die Integration verschiedener Technologien wie ArgoCD und Longhorn hat mir gezeigt, wie leistungsfähig und flexibel moderne Cloud-native Anwendungen sein können.

Für zukünftige Arbeiten wäre es spannend, die Performance und Skalierbarkeit des Clusters unter realen Lastbedingungen zu evaluieren. Eine interessante Möglichkeit besteht in der Integration von KubeVirt in einen immutable Kubernetes-Cluster. Dies würde die gleichzeitige Ausführung von virtuellen Maschinen und Container-Workloads ermöglichen und die Flexibilität sowie die Einsatzmöglichkeiten des Clusters erheblich erweitern. In diesem Zusammenhang könnte das Setup mit Longhorn weiter getestet werden, um die Leistungsfähigkeit und Zuverlässigkeit des verteilten Speichersystems in Kombination mit KubeVirt zu bewerten. Durch den Einsatz von KubeVirt könnten zudem wertvolle Erfahrungen gesammelt werden, die einen möglichen Ausstieg aus VMware erleichtern würden.

Insgesamt hat dieses Projekt meine Fähigkeiten im Bereich der Cloud-Technologien und der agilen Projektplanung erheblich erweitert und bietet eine solide Grundlage für zukünftige Projekte in diesem Bereich.
