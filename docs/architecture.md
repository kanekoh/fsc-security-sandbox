# Architecture

## Scope

Single OpenShift cluster (RHDP FSC) for trying:

| Product | Role |
|---|---|
| RHACS | Runtime, policy, vulnerability |
| RHTAS | Artifact signing / verification (Sigstore) |
| RHTPA | SBOM / OSS dependency risk |
| RHDH | Developer portal |
| OpenShift Pipelines | CI helpers for demos |

Full **Red Hat Advanced Developer Suite - software supply chain** (formerly RHTAP) installer is out of scope; this repo composes selected components via GitOps.

## Cluster sizing

| Guidance | Source |
|---|---|
| Prefer **multinode**; avoid SNO when RHACS Central + Scanner + Sensor are co-located | RHACS resource requirements; RHDP treats ACS as a heavy SNO workload |
| OpenShift **4.17+** | RHTPA Operator prerequisites |
| Capacity floor similar to RHADS-SSC workers (about **5 CPU / 17 GiB per worker**, 3 nodes) when enabling the full set | RHADS-SSC Installing hardware requirements |

RHACS demo values in this repo use reduced requests so Shared RHDP pools can schedule. For production, use the defaults in the RHACS Installing guide (Central DB storage, Scanner sizing, etc.).

## RHACS zero-touch registration

Learners should not manually create init bundles.

```
RHACS Operator
  → Central CR
  → Job: generate Cluster Registration Secret (CRS) via roxctl in Central
  → SecuredCluster CR (central.stackrox.svc:443 on the same cluster)
```

Order is enforced with Argo CD sync-waves. CRS material stays in cluster Secrets only.

- Prefer **CRS** over init bundles (init bundles are deprecated in recent RHACS releases).
- Do **not** use deprecated direct `central-services` / `secured-cluster-services` Helm charts for new installs; use the Operator.

## Other products

| Component | Notes |
|---|---|
| RHTAS instance | Requires an OIDC provider (see product docs) |
| RHTPA instance | Requires OIDC, PostgreSQL (or RDS), and object storage (ODF or S3) |
| RHDH instance | Requires authentication configuration |

Operators may install before those dependencies exist; instances remain disabled in `helm/values.yaml` until ready.

## Layout

```
helm/                         # App of Apps (GitOps Path)
├── templates/applications.yaml
├── values.yaml
└── components/
    ├── rhacs-operator|
    ├── rhacs-central|
    ├── rhacs-crs-job|
    ├── rhacs-secured-cluster|
    ├── rhtas-operator| / rhtas-instance (off)
    ├── rhtpa-operator| / rhtpa-instance (off)
    ├── rhdh-operator| / rhdh-instance (off)
    ├── pipelines-operator|
    └── sample-apps|
```

## References

- [RHACS Installing](https://docs.redhat.com/en/documentation/red_hat_advanced_cluster_security_for_kubernetes)
- [RHTAS documentation](https://docs.redhat.com/en/documentation/red_hat_trusted_artifact_signer)
- [RHTPA Deployment Guide](https://docs.redhat.com/en/documentation/red_hat_trusted_profile_analyzer)
- [RHDH documentation](https://docs.redhat.com/en/documentation/red_hat_developer_hub)
- [RHADS-SSC Installing](https://docs.redhat.com/en/documentation/red_hat_advanced_developer_suite_-_software_supply_chain) (sizing context)
