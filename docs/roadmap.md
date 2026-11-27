# Roadmap

## Done

- RHACS Operator, Central, CRS bootstrap Job, SecuredCluster (same cluster)
- RHACS Central reencrypt Route for UI (passthrough kept for Sensor)
- Operator Subscriptions for RHTAS, RHTPA, RHDH, OpenShift Pipelines
- Sample Deployments for ACS demos
- Sample Pipelines (`sample-sign-verify`: unsigned check + key-based sign/verify)
- RHTPA in-cluster deps (Postgres + MinIO + secret bootstrap); CR gated on OIDC

## Planned

- Shared OIDC (for example Red Hat build of Keycloak) suitable for demos
- RHTAS Securesign instance (after OIDC)
- RHTPA `createCR: true` once OIDC clients exist
- RHDH instance and optional product plugins
- Optional lighter profile without RHACS
- Publish measured provision times after a full RHDP order

## Contributions

Issues and PRs are welcome. Do not commit secrets, tokens, or cluster credentials.
