---
layout: default
title: 5.4. Cert-Manager
parent: 5. Deployment
nav_order: 4
---

# 5.4 Cert-Manager

Cert-Manager ist ein Kubernetes-Add-on, das Zertifikate automatisch verwaltet und bereitstellt. In dieser Anleitung wird die Konfiguration von Cert-Manager mit Let's Encrypt und Cloudflare beschrieben.

## Installation von Cert-Manager

1. Erstelle das `cert-manager` Namespace:

```bash
kubectl create namespace cert-manager
```

2. Erstellen eines Secrets mit dem Cloudflare API-Keys

```yaml
apiVersion: v1
kind: Secret
metadata:
  name: cloudflare-api-token-secret
type: Opaque
stringData:
  api-token: <TOKEN>
````

3. ArgoCD Applikation hinzufügen:

```bash
kubectl apply -f https://github.com/Cloud-native-engineering/sem04_k8s/cert-manager/cert-manager.yaml
```

4. Sync ArgoCD Application `cert-manager`

## Ausstellen eines Zertifikats

Der Cert-Manager wird nacher selbständig bei der Ausstellung eines Let's Encrypt Zertifikat die benötigten Überprüfungen vornehmen und die Domain Verifikation anhand DNS-TXT Records vornehmen. Folgendem Beispiel kann ein Ingress mit einem Zertifikat verseht werden:

```yaml
apiVersion: networking.k8s.io/v1
kind: Ingress
metadata:
  name: example-ingress
  namespace: default
  annotations:
    cert-manager.io/cluster-issuer: "letsencrypt-staging"
spec:
  ingressClassName: cilium
  rules:
  - host: git.k8s.wlankabel.ch
    http:
      paths:
      - path: /
        pathType: Prefix
        backend:
          service:
            name: example-service
            port:
              number: 80
  tls:
  - secretName: git-tls
    hosts:
    - git.k8s.wlankabel.ch
```
