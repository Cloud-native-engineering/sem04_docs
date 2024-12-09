---
layout: default
title: 5.5. Cilium
parent: 5. Deployment
nav_order: 5
---

# 5.5 Cilium

Cilium wird für den Ganzen Network Stack im K8s Cluster verwendent. Es ermöglicht eine viehlzahl, von welchen nur folgende Benutzt werden:

## IP-Pool

Wie kann man auf die Services zugreifen, die im Cluster bereitgestellt wurden? Zunächst muss dem Cluster ein IP-Pool zugewiesen werden, den Cilium für externe Ressourcen verwenden kann. Dazu muss das folgende Manifest auf dem Cluster angewendet werden:

```yaml
---
apiVersion: "cilium.io/v2alpha1"
kind: CiliumLoadBalancerIPPool
metadata:
  name: "default-pool"
spec:
  blocks:
  - start: "192.168.40.10"
    stop: "192.168.40.20"
...
```

## Loadbalancer

Ein Loadbalancer verteilt den eingehenden Netzwerkverkehr auf mehrere Backend-Services, um die Last zu verteilen und die Verfügbarkeit zu erhöhen. Cilium unterstützt die Konfiguration von Loadbalancern im Kubernetes-Cluster. Bei Cilium ist unteranderem der Ingress im Hintergrund ein Loadbalancer mit einer Externen IP aus dem Address-Pool. Das Setup für den Cilium Ingress wird via das Setup bereits gemacht (Cilium installation).

### Layer 4 Advertising

Layer 4 Advertising bezieht sich auf die Ankündigung von IP-Adressen auf der Netzwerkschicht. Dies ermöglicht es, dass der Datenverkehr auf der Grundlage von IP-Adressen und Ports verteilt wird. Hier ist ein Beispiel für die Konfiguration einer Layer 4 Advertising Policy mit Cilium:

```yaml
---
apiVersion: "cilium.io/v2alpha1"
kind: CiliumL2AnnouncementPolicy
metadata:
  name: announce-cilium-ingress-vip
spec:
  serviceSelector:
    matchLabels:
      arpAdvertise: "true"
  nodeSelector:
    matchExpressions:
      - key: node-role.kubernetes.io/control-plane
        operator: DoesNotExist
  interfaces:
  - ^en.*  # Regular expression to match interfaces starting with "en"
  externalIPs: true
  loadBalancerIPs: true
...
```

Dies wird benötigt, wenn der Cluster seine VIP für die externen IPs zwischen den Nodes wechselt, damit die richtigen Nodes angesprochen werden.

## Ingress

Cilium kann auch für Ingress verwendet werden, um den Datenverkehr in das Cluster zu leiten. Der Ingress Controller kann entweder dediziert (pro Ingress) oder als gemeinsame Komponente erstellt werden. In dieser Arbeit wurde entschieden, das Shared-Modell zu verwenden, da dadurch kostbare Ressourcen gespart werden können, die für weitere Open Source Services benötigt werden.

Der Ingress-Controller wurde bereits beim initial Install von Cilium installiert (Git: sem04_setup)
