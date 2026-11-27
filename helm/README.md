# Helm / GitOps

App of Apps chart for RHDP Field Sourced Content.

- **GitOps Repo URL (HTTPS):** `https://github.com/kanekoh/fsc-security-sandbox.git`
- **GitOps Path:** `helm`
- **Showroom:** not used

## Applications (enabled by default)

| sync-wave | Component | Content |
|---|---|---|
| 0 | rhacs-operator | Subscription |
| 1 | rhacs-central | Central CR |
| 2 | rhacs-crs-job | CRS bootstrap Job |
| 3 | rhacs-secured-cluster | SecuredCluster CR |
| 10 | rhtas-operator | Subscription |
| 20 | rhtpa-operator | Subscription |
| 30 | rhdh-operator | Subscription |
| 40 | pipelines-operator | Subscription |
| 50 | sample-apps | Demo Deployments |

## Disabled until dependencies exist

`rhtasInstance` / `rhtpaInstance` / `rhdhInstance` in `values.yaml`.

## Local check

```bash
helm lint .
helm template fsc-security-sandbox .
```

Order steps: [`../docs/rhdp-order.md`](../docs/rhdp-order.md).
