# k8s

Kubernetes manifests and local cluster config.

## Layout

```
kind-config.yaml          local cluster, for development
helm/                     charts
kustomize/                overlays
gitops/                   ArgoCD / Flux definitions
```

## Local cluster

```console
kind create cluster --config kind-config.yaml
```

## The four repos

| Repo | Holds |
|---|---|
| [`infra-live`](https://github.com/adi4fab/infra-live) | AWS infrastructure — Terragrunt, what exists |
| [`infra-modules`](https://github.com/adi4fab/infra-modules) | Reusable OpenTofu modules — blueprints only |
| **`k8s`** | Kubernetes manifests, this repo |
| [`microservices`](https://github.com/adi4fab/microservices) | Application code |

## Guardrails

- gitleaks + detect-private-key pre-commit hooks
- GitHub secret scanning + push protection
- `main` protected — PR required, no force-push, no deletion, zero bypass

## Setup

```console
brew install mise
pre-commit install
```
