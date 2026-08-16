# Multi-Cloud Security & Governance Service Comparison

> **Report date:** August 2026
> **Pricing verified:** August 2026
> **Scope:** Five Azure security and governance services, their nearest AWS and GCP equivalents, compared on features, compliance, cost, and DevSecOps fit.

---

## 1. Scope & Methodology

### Purpose

This report maps five Azure services to their functional equivalents in AWS and GCP, then compares them across five dimensions: **overview**, **core features**, **security & compliance**, **pricing model**, and **DevSecOps integration**.

## 2. Quick Reference: Service Equivalence Matrix

| # | Azure Service | AWS Equivalent | GCP Equivalent | Mapping Quality |
| --- | --- | --- | --- | --- |
| 1 | **Microsoft Entra ID** (SSO, IAM) | **AWS IAM Identity Center** (workforce SSO) + **AWS IAM** (authorization) + **Amazon Cognito** (customer identity) + **AWS Directory Service** | **Cloud Identity** (directory/SSO) + **Google Cloud IAM** (authorization) + **Identity Platform** (customer identity) + **Managed Service for Microsoft AD** | Partial — Entra ID is both an enterprise IdP *and* a cloud authorization plane; AWS and GCP split these |
| 2 | **Azure Monitor & Log Analytics** | **Amazon CloudWatch** (Metrics, Logs, Logs Insights, Alarms, Dashboards) + **AWS X-Ray** / **CloudWatch Application Signals** + **Amazon Managed Prometheus/Grafana** | **Google Cloud Observability**: **Cloud Monitoring**, **Cloud Logging** (+ Log Analytics), **Cloud Trace**, **Error Reporting**, **Cloud Profiler** | Strong |
| 3 | **Azure Policy** | **AWS Organizations SCPs + RCPs + Declarative Policies** (preventive) + **AWS Config Rules / Conformance Packs** (detective + remediation) + **AWS Control Tower** controls + **CloudFormation Guard** | **Organization Policy Service** (preventive, incl. custom constraints) + **Policy Controller** (OPA/Gatekeeper, via GKE Enterprise) + **Security Health Analytics** (detective) + **Assured Workloads** | Fragmented — no single AWS or GCP service covers Azure Policy's full range |
| 4 | **Microsoft Defender for Cloud** | **AWS Security Hub** (unified, GA Dec 2025) incl. **Security Hub CSPM**, **Amazon GuardDuty**, **Amazon Inspector**, **Amazon Macie** | **Security Command Center** (Standard / Premium / Enterprise) + **Sensitive Data Protection** + **Container Threat Detection** | Strong (post-2025 AWS consolidation) |
| 5 | **Microsoft Sentinel** (SIEM/SOAR) | *No first-party SIEM.* Closest: **Amazon Security Lake** + **Amazon OpenSearch Service** + **Amazon Detective** + **EventBridge/Step Functions** (SOAR) + **AWS Security Incident Response** | **Google Security Operations (SecOps)** — Chronicle SIEM + SOAR + Mandiant Threat Intelligence | AWS gap / GCP strong |

---

## 3. Pricing & DevSecOps Summary

| Capability | Azure — Pricing Model | AWS — Pricing Model | GCP — Pricing Model |
| --- | --- | --- | --- |
| **Identity / SSO** | Per user/month tiers. Free; **P1 $7**; **P2 $10**; Entra Suite $12; Governance +$7 | **Free** (IAM + IAM Identity Center). Cognito billed per monthly active user | **Cloud Identity Free**; **Premium ~$6/user/mo**. Cloud IAM free; Identity Platform per MAU |
| **Monitoring / Logs** | **$2.30/GB** Analytics logs (5 GB/mo free); $0.50/GB Basic; $0.05/GB Auxiliary; commitment tiers from 100 GB/day | **$0.50/GB** log ingestion; $0.03/GB/mo storage; $0.30/custom metric/mo; $3/dashboard/mo | **$0.50/GiB** logs (50 GiB/project/mo free, 30-day retention included); **$0.2580/MiB** metrics; $0.20/M trace spans |
| **Policy / Governance** | **Azure Policy is free** for Azure resources (Arc guest configuration charged separately) | SCPs/RCPs/Declarative Policies **free**; **AWS Config $0.003/config item** + tiered rule evaluations | **Org Policy free**; Policy Controller bundled with GKE Enterprise (per vCPU-hour) |
| **CSPM / CNAPP** | Foundational CSPM **free**; **Defender CSPM ~$5.11/billable resource/mo**; workload plans priced separately (e.g. Servers P2 ~$15/server/mo) | **Security Hub Essentials** per resource-unit (bundles Security Hub + Inspector + CSPM); Threat Analytics (GuardDuty) usage-based; 30-day free trial | **SCC Standard free**; **Premium** subscription or pay-as-you-go (per vCPU-hour across services); **Enterprise** subscription only |
| **SIEM / SOAR** | **~$4.30/GB** PAYG (simplified tier); commitment tiers to ~$2.05/GB; Data Lake tier for cold storage; M365/Defender sources free | No SIEM SKU. **Security Lake** $0.75/GB CloudTrail, $0.25/GB other, $0.035/GB normalization + downstream analytics costs | **SecOps** Standard / Enterprise / Enterprise Plus packages — contact-sales, historically per-employee, now volume-influenced |
| **CI/CD & IaC hooks** | ARM/Bicep, Terraform, Azure DevOps, GitHub Actions, Policy-as-Code via `Microsoft.Authorization` | CloudFormation, CDK, Terraform, CodePipeline, GitHub Actions, CFN Guard, cdk-nag | Deployment Manager (legacy), **Terraform (preferred)**, Cloud Build, Config Connector, Policy Controller (OPA) |

---

## Service-by-Service Analysis

---

### Identity & Access Management (Azure Active Directory / Microsoft Entra ID)

#### Overview

| Platform | Service(s) | Description |
| --- | --- | --- |
| **Azure** | **Microsoft Entra ID** | A full enterprise identity provider **and** the authorization plane for Azure. Handles workforce directory, SSO to thousands of SaaS apps, MFA, Conditional Access, PIM, and identity governance. Uniquely, it doubles as the identity backbone for Microsoft 365. |
| **AWS** | **AWS IAM Identity Center** + **AWS IAM** + **Amazon Cognito** | AWS deliberately separates concerns. IAM Identity Center is the workforce SSO layer (and can federate to an external IdP). IAM is the resource authorization engine — policy documents attached to users, roles, and resources. Cognito handles customer-facing identity (B2C). |
| **GCP** | **Cloud Identity** + **Google Cloud IAM** + **Identity Platform** | Cloud Identity is the directory and SSO product (the identity layer beneath Google Workspace). Cloud IAM binds principals to roles on resources. Identity Platform (a productized Firebase Auth) covers customer identity. |

#### Core Features

| Capability | Microsoft Entra ID | AWS | GCP |
| --- | --- | --- | --- |
| **Workforce SSO (SAML/OIDC)** | Thousands of pre-integrated SaaS apps in the app gallery | IAM Identity Center; smaller app catalog, commonly fronted by an external IdP | Cloud Identity; strong for Google Workspace estates |
| **MFA / passwordless** | Authenticator, FIDO2, Windows Hello, Temporary Access Pass, certificate-based | MFA incl. FIDO2/passkeys; root account MFA now mandatory | Titan keys, passkeys, Google Prompt; 2SV enforcement policies |
| **Risk-based / adaptive access** | **Conditional Access + Identity Protection** (P2) — leaked credentials, atypical travel, anonymous IP, password spray | Policy conditions (IP, MFA, tags) but no native ML risk scoring | **Context-Aware Access** / BeyondCorp Enterprise — device, location, IP posture signals |
| **Privileged access (JIT)** | **Privileged Identity Management (PIM)** — time-bound, approval-gated role elevation (P2) | No native JIT; achieved via role assumption + session policies + external tooling | **Privileged Access Manager (PAM)** — time-bound entitlement grants |
| **Identity governance** | Access Reviews, Entitlement Management, Lifecycle Workflows (P2 / Governance add-on) | IAM Access Analyzer (unused access, external access findings); no full access-review workflow | **Policy Intelligence** / Recommender for role right-sizing; Access Approval |
| **Workload / non-human identity** | Service principals, managed identities, **Workload Identity Federation**; Workload Identities SKU adds Conditional Access for service principals | IAM roles, instance profiles, IRSA/Pod Identity for EKS, roles-anywhere | Service accounts, **Workload Identity Federation**, Workload Identity for GKE |
| **Customer identity (CIAM)** | **Entra External ID** (successor to Azure AD B2C) | **Amazon Cognito** user pools + identity pools | **Identity Platform** (Firebase Auth productized) |
| **Hybrid / on-prem AD** | Entra Connect / Cloud Sync; Entra Domain Services | AWS Directory Service (Managed AD, AD Connector) | Managed Service for Microsoft AD |
| **Cross-cloud** | Entra can act as IdP **for AWS and GCP** | Consumer of external IdPs, rarely the provider | Consumer of external IdPs |

#### Security & Compliance

- **Azure/Entra ID:** Broadest government coverage — FedRAMP High, **DoD Impact Level 4/5/6** via Azure Government and Microsoft 365 Government (GCC High). FIDO2 / NIST SP 800-63B **AAL3** support with hardware keys. Entra ID has the deepest built-in mapping to identity governance controls demanded by SOX and similar frameworks.
- **AWS:** FedRAMP High in GovCloud, **DoD IL2–IL6** (via GovCloud, Secret and Top Secret Regions). IAM's compliance strength is in its auditability — every API call lands in CloudTrail with full principal attribution.
- **GCP:** FedRAMP High, **IL4/IL5** via Assured Workloads. Strong data-residency controls; Access Transparency and **Access Approval** give customers logged (and optionally gated) visibility into Google personnel access — a differentiator for EU sovereignty requirements.

### Integration for DevSecOps

| Concern | Azure | AWS | GCP |
| --- | --- | --- | --- |
| **IaC management** | Terraform `azuread` provider; Bicep/ARM; Microsoft Graph API | Terraform `aws` provider; CloudFormation; CDK | Terraform `google` provider; Config Connector |
| **CI/CD federation (no long-lived secrets)** | **Workload Identity Federation** — GitHub Actions, GitLab, Azure DevOps OIDC | **OIDC provider for GitHub Actions** → assume role, no static keys | **Workload Identity Federation** — GitHub, GitLab, OIDC |
| **Secrets** | Azure Key Vault + managed identity | AWS Secrets Manager / Parameter Store + IAM roles | Secret Manager + service accounts |
| **Least-privilege tooling** | Entra Permissions Management (CIEM); PIM for eligible roles | IAM Access Analyzer (policy generation from CloudTrail); Access Advisor | Policy Intelligence / IAM Recommender; Policy Simulator |
| **Audit stream** | Entra sign-in & audit logs → Log Analytics / Event Hub | CloudTrail → S3 / CloudWatch / Security Lake | Cloud Audit Logs → Cloud Logging / BigQuery |

**Practical takeaway for pipelines:** All three now support OIDC-based workload identity federation, which should be the default. Long-lived `AWS_ACCESS_KEY_ID` secrets and Azure service principal client secrets in CI variables are an anti-pattern with no remaining justification.