# RHDP order guide

Use with [demo.redhat.com](https://demo.redhat.com) **Field Sourced Content - OpenShift**.

## Recommendations

| Item | Value | Why |
|---|---|---|
| Visibility of this Git repo | Public | No PAT required |
| Catalog | Shared first; Dedicated if capacity is tight | Four-product footprint is large |
| Showroom | Off | Use product consoles directly |

## Order form

1. Open https://demo.redhat.com  
2. Select **Field Sourced Content - OpenShift (Shared Clusters)** (or Dedicated if needed)  
3. Fill:

| Field | Value |
|---|---|
| Cloud Provider | `CNV` |
| Activity | Practice / Enablement |
| Purpose | Conduct internal training/enablement |
| cluster_size | **`multinode`** |
| OpenShift Version | **4.17 or newer** (catalog options such as 4.20 / 4.21) |
| Select Base Workloads | None |
| Users | None |
| GitOps - Existing Gitops Repo? | Yes |
| GitOps - Private GitOps repo? | No (public repo) |
| GitOps Repo URL | `https://github.com/kanekoh/fsc-security-sandbox.git` |
| GitOps Branch | `main` |
| GitOps Path | `helm` |
| Deploy Showroom? | No |
| AI/LLM Configuration | No |
| Auto-destroy | 4–8 hours recommended |

## After the environment is Running

1. Open the **Console URL** (not the API URL)  
2. Wait until Argo CD Applications under `field-content` are Synced / Healthy  
3. Open RHACS Central (and other product routes when enabled)  

Do not create RHACS init bundles by hand; registration is automated.

## Optional lighter profile

A SNO / subset profile (for example without RHACS) is not packaged yet. See [`roadmap.md`](roadmap.md).
