# Suggested exploration order

No Showroom. Use the OpenShift console and product UIs.

1. Wait for RHDP **Running** and Argo CD **Synced / Healthy**  
2. **RHACS** — use the **reencrypt** Central Route (OpenShift cert) for browser login; sample workloads in `security-sandbox-demos`  
3. **Pipelines** — run `sample-sign-verify` in `security-sandbox-pipelines` (unsigned baseline + key-based sign/verify)  
4. **RHTAS** — when Securesign + OIDC are enabled (replace key-based step with Fulcio keyless)  
5. **RHTPA** — CNPG + MCG ObjectBucketClaim deps first; enable `createCR` after OIDC (set `mcg.endpoint` from `rhtpa-storage-endpoint`)  
6. **RHDH** — when the instance is enabled (portal / catalog)  

```bash
tkn -n security-sandbox-pipelines pipeline start sample-sign-verify --showlog
```
