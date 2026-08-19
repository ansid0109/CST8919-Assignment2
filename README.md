# CST8919 Assignment 2: Multi-Cloud Security & Governance Service Comparison

> **Student Name**: Anoop Sidhu
> **Student ID**: 040984994
> **Course**: CST8915 Full-stack Cloud-native Development
> **Semester**: Winter 2026
> **Report date:** August 2026
> **Pricing verified:** August 2026
> **Scope:** Five Azure security and governance services, their nearest AWS and GCP equivalents, compared on features, compliance, cost, and DevSecOps fit.

---

## Purpose

This report maps five Azure services to their functional equivalents in AWS and GCP, then compares them across five dimensions: **overview**, **core features**, **security & compliance**, **pricing model**, and **DevSecOps integration**.

---

## Identity: Azure Active Directory / Entra ID

**AWS equivalent:** AWS IAM Center
**GCP equivalent:** Cloud Identity

|                     | Azure                                                                                                     | AWS                                                                | GCP                                                                                                                        |
| ------------------- | --------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------ | -------------------------------------------------------------------------------------------------------------------------- |
| Overview            | Primarily and Identity Provider (IdP).                                                                    | Primarily an Access Management System.                             | Cloud identity provides identity/SSO; Cloud IAM does permissions.                                                          |
| Core Features       | - Verifies identity, more user focused.<br>- Conditional Access + Privileged Access.<br>- SSO, MFA, RBAC. | - Defines authorization, more access focused.<br>- SSO, MFA, RBAC. | - Connects to your Google account, big advantage and ease of access over other two due to popularity.<br>- SSO, MFA, RBAC. |
| Security/Compliance | SOC2, ISO 27001, HIPAA, FedRAMP                                                                           | SOC2, ISO 27001, HIPAA, FedRAMP                                    | SOC2, ISO 27001, HIPAA, FedRAMP                                                                                            |
| Pricing             | 7-10$ per user / per month                                                                                | Free                                                               | Premium: 6$ per month                                                                                                      |
| DevSecOps           | OIDC Federation for CI/CD                                                                                 | Same features as Azure.                                            | Same features as Azure.                                                                                                    |

## Monitoring: Azure Monitor

**AWS equivalent:** CloudWatch
**GCP equivalent:** Cloud Logging

|                     | Azure                                                                                  | AWS                                                                                                  | GCP                                                                                               |
| ------------------- | -------------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------- |
| Overview            | The observability platform for Azure resources, applications, and hybrid environments. | Built into the AWS control plane  and most AWS services publish metrics to CloudWatch automatically. | Store, search, analyze, monitor, and alert on **logging** data from **Google** **Cloud** and AWS. |
| Core Features       | - Log search                                                                           | - Trigger Auto Scaling policies, notifications directly.                                             | -                                                                                                 |
| Security/Compliance | Standard certificates.                                                                 | Same.                                                                                                | Same.                                                                                             |
| Pricing (logs)      | 2.30/GB                                                                                | 0.50/GB                                                                                              | 0.50/GB                                                                                           |
| DevSecOps           | Integration with CI/CD pipelines, OpenTelemetry.                                       | Same.                                                                                                | Same.                                                                                             |


## Policy: Azure Policy

**AWS equivalent:** Config + SCPs
**GCP equivalent:** Org Policy

|                     | Azure     | AWS        | GCP        |
| ------------------- | --------- | ---------- | ---------- |
| Overview            |           | 1 sentence | 1 sentence |
| Core Features       | 3 bullets | 3 bullets  | 3 bullets  |
| Security/Compliance | 1 line    | 1 line     | 1 line     |
| Pricing             | 1 line    | 1 line     | 1 line     |
| DevSecOps           | 1 line    | 1 line     | 1 line     |

## CNAPP: Defender for Cloud

**AWS equivalent:** Security Hub
**GCP equivalent:** Security Command Center

|                     | Azure      | AWS        | GCP        |
| ------------------- | ---------- | ---------- | ---------- |
| Overview            | 1 sentence | 1 sentence | 1 sentence |
| Core Features       | 3 bullets  | 3 bullets  | 3 bullets  |
| Security/Compliance | 1 line     | 1 line     | 1 line     |
| Pricing             | 1 line     | 1 line     | 1 line     |
| DevSecOps           | 1 line     | 1 line     | 1 line     |

## SIEM/SOAR: Sentinel

**AWS equivalent:** None
**GCP equivalent:** Google SecOps

|                     | Azure      | AWS        | GCP        |
| ------------------- | ---------- | ---------- | ---------- |
| Overview            | 1 sentence | 1 sentence | 1 sentence |
| Core Features       | 3 bullets  | 3 bullets  | 3 bullets  |
| Security/Compliance | 1 line     | 1 line     | 1 line     |
| Pricing             | 1 line     | 1 line     | 1 line     |
| DevSecOps           | 1 line     | 1 line     | 1 line     |

---
## References

- https://towardsaws.com/the-definitive-comparision-guide-microsoft-entra-id-vs-aws-iam-afdc036b6fca
- https://learn.microsoft.com/en-us/azure/architecture/aws-professional/security-identity
- https://signoz.io/comparisons/aws-cloudwatch-vs-azure-monitor/
