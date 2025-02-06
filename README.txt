---
apiVersion: source.toolkit.fluxcd.io/v1
kind: HelmRepository
metadata:
  name: podinfo
  namespace: default
spec:
  interval: 5m
  url: https://prometheus-community.github.io/helm-charts
---
apiVersion: helm.toolkit.fluxcd.io/v2
kind: HelmRelease
metadata:
  name: podinfo
  namespace: default
spec:
  interval: 10m
  timeout: 1m
  chart:
    spec:
      chart: kube-prometheus-stack
      version: 68.4.*
      sourceRef:
        kind: HelmRepository
        name: podinfo
      interval: 5m
  releaseName: podinfo

# notes
