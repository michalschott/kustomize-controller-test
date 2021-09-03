---
apiVersion: source.toolkit.fluxcd.io/v1beta1
kind: GitRepository
metadata:
  name: podinfo
  namespace: default
spec:
  interval: 15s
  url: https://github.com/michalschott/kustomize-controller-test
---
apiVersion: kustomize.toolkit.fluxcd.io/v1beta1
kind: Kustomization
metadata:
  name: backend
  namespace: default
spec:
  interval: 15s
  path: "./"
  prune: true
  sourceRef:
    kind: GitRepository
    name: podinfo
