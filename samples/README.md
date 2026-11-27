# samples/

Optional sample manifests for demos (also deployed via Helm).

| Item | Purpose | Where |
|---|---|---|
| Vulnerable / older UBI image | RHACS vulnerability views | `helm/components/sample-apps` |
| Privileged / `:latest` style workload | RHACS policy demos | `helm/components/sample-apps` |
| Unsigned image Deployment | RHTAS / verify demos | `helm/components/sample-apps` |
| `sample-sign-verify` Pipeline | Unsigned check → copy → key-sign → verify | `helm/components/sample-pipelines` |

## Pipeline quick start

```bash
tkn -n security-sandbox-pipelines pipeline start sample-sign-verify --showlog
```

Key-based signing is a **shape demo** only. Product path after RHTAS Securesign + OIDC:

```bash
export TUF_URL=$(oc get tuf -n trusted-artifact-signer -o jsonpath='{.items[0].status.url}')
cosign initialize --mirror "$TUF_URL" --root "$TUF_URL/1.root.json"
cosign sign --oidc-client-id trusted-artifact-signer <image>
```

(Official: Red Hat Trusted Artifact Signer — Sign and verify containers.)

Use public images only. Do not add credentials.
