# Suggested exploration order

No Showroom. Use the OpenShift console and product UIs.

1. Wait for RHDP **Running** and Argo CD **Synced / Healthy**  
2. **RHACS** — Central login, vulnerabilities, policies, sample workloads  
3. **RHTAS** — when the instance is enabled (signing / verification)  
4. **RHTPA** — when the instance is enabled (SBOM upload / risk views)  
5. **RHDH** — when the instance is enabled (portal / catalog)  
6. **Pipelines** — optional short runs for signing or SBOM demos  

Sample workloads live in namespace `security-sandbox-demos`.
