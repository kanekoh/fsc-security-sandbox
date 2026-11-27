# fsc-security-sandbox

[Red Hat Demo Platform (RHDP)](https://demo.redhat.com) の Field Sourced Content (FSC) 向けに、OpenShift 上で Red Hat のセキュリティ関連製品を試せるサンドボックスです。

オーダー後は GitOps でコンポーネントが入ります。**Showroom ガイドは含みません**（各製品コンソールを直接操作します）。

## 含まれるもの

| 製品 | 状態 |
|---|---|
| [Red Hat Advanced Cluster Security for Kubernetes](https://docs.redhat.com/en/documentation/red_hat_advanced_cluster_security_for_kubernetes) (RHACS) | Central + Secured Cluster（同一クラスタ）。登録は自動化 |
| [Red Hat Trusted Artifact Signer](https://docs.redhat.com/en/documentation/red_hat_trusted_artifact_signer) (RHTAS) | Operator まで。インスタンスは OIDC 準備後 |
| [Red Hat Trusted Profile Analyzer](https://docs.redhat.com/en/documentation/red_hat_trusted_profile_analyzer) (RHTPA) | Operator まで。インスタンスは OIDC / DB / オブジェクトストレージ準備後 |
| [Red Hat Developer Hub](https://docs.redhat.com/en/documentation/red_hat_developer_hub) (RHDH) | Operator まで。インスタンスは認証設定後 |
| OpenShift Pipelines | Operator |
| サンプル workload | 脆弱イメージ・未署名・privileged デモ用 Deployment |

## RHDP でのオーダー

詳細は [`docs/rhdp-order.md`](docs/rhdp-order.md)。要点:

| 項目 | 値 |
|---|---|
| Catalog | Field Sourced Content - OpenShift |
| Cloud Provider | CNV |
| cluster_size | **multinode**（SNO 非推奨） |
| OpenShift | **4.17+** |
| Base Workloads | なし |
| GitOps Repo URL | `https://github.com/kanekoh/fsc-security-sandbox.git` |
| GitOps Path | `helm` |
| Deploy Showroom? | オフ |

## ドキュメント

| 文書 | 内容 |
|---|---|
| [`docs/architecture.md`](docs/architecture.md) | 構成・サイジング・RHACS 自動化 |
| [`docs/rhdp-order.md`](docs/rhdp-order.md) | オーダー手順 |
| [`docs/learner-path.md`](docs/learner-path.md) | 触る順番の目安 |
| [`docs/roadmap.md`](docs/roadmap.md) | 今後の予定 |
| [`helm/README.md`](helm/README.md) | Helm / App of Apps |

## 開発

```bash
git clone https://github.com/kanekoh/fsc-security-sandbox.git
cd fsc-security-sandbox/helm
helm lint .
helm template fsc-security-sandbox .
```

秘密情報（パスワード、OIDC client secret、CRS 等）はリポジトリに含めません。

## 参考（公式）

- [RHACS Installing](https://docs.redhat.com/en/documentation/red_hat_advanced_cluster_security_for_kubernetes)
- [field-sourced-content-template](https://github.com/rhpds/field-sourced-content-template)
