# webapp Helm Chart

A production-ready Helm chart for deploying a containerized web application on
Kubernetes. Demonstrates the patterns clients ask for: zero-downtime rolling
updates, autoscaling, ingress with TLS, resource limits, and security-hardened
pod defaults.

## What's included

| Template           | Purpose                                              |
|--------------------|------------------------------------------------------|
| `deployment.yaml`  | Rolling-update deployment, probes, security contexts |
| `service.yaml`     | ClusterIP service in front of the pods               |
| `ingress.yaml`     | Optional ingress with TLS (set `ingress.enabled`)     |
| `hpa.yaml`         | CPU/memory autoscaling (set `autoscaling.enabled`)    |
| `configmap.yaml`   | Optional app config mounted read-only                |
| `serviceaccount.yaml` | Dedicated SA, token automount disabled            |

## Usage

```bash
# Render locally to check output
helm template my-app . --values values.yaml

# Lint
helm lint .

# Install
helm install my-app . --namespace web --create-namespace

# With overrides for staging/prod
helm install my-app . -f values-prod.yaml --namespace web --create-namespace
```

## Security defaults

- Runs as non-root (`runAsNonRoot: true`)
- Drops all Linux capabilities, `readOnlyRootFilesystem: true`
- Resource requests/limits on every container
- Pod anti-affinity spreads replicas across nodes
- ServiceAccount token automount disabled
