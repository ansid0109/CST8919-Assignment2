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

|                     | Azure                                                                                                                                           | AWS                                                                                                                  | GCP                                                                                                                                                                                                     |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Overview            | The observability platform for Azure resources, applications, and hybrid environments.                                                          | Built into the AWS control plane  and most AWS services publish metrics to CloudWatch automatically.                 | Store, search, analyze, monitor, and alert on **logging** data from **Google** **Cloud** and AWS.                                                                                                       |
| Core Features       | - Azure Monitor's investigation is centered on Kusto Query Language (KQL).<br>- Azure Monitor Alerts, an alerting surface across Azure signals. | - Trigger Auto Scaling policies, notifications directly.<br>- CloudWatch Application Signals, AWS X-Ray for tracing. | - Logs explorer: earch, sort, and analyze logs through flexible query statements, along with rich histogram visualizations.<br>- Cloud Audit Logs security teams maintain audit trails in Google Cloud. |
| Security/Compliance | Standard certificates.                                                                                                                          | Same.                                                                                                                | Same.                                                                                                                                                                                                   |
| Pricing (logs)      | 2.30/GB                                                                                                                                         | 0.50/GB                                                                                                              | 0.50/GB                                                                                                                                                                                                 |
| DevSecOps           | Integration with CI/CD pipelines, OpenTelemetry.                                                                                                | Same.                                                                                                                | Same.                                                                                                                                                                                                   |

## Policy: Azure Policy

**AWS equivalent:** Config + SCPs
**GCP equivalent:** Organization Policy

|                     | Azure                                                                                                                   | AWS                                                                                                     | GCP                                                                                                         |
| ------------------- | ----------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| Overview            | A service in Azure that you use to create, assign and, manage policy definitions.                                       | The primary governance mechanism within AWS Organizations.                                              | Rule-based governance to enforce/audit resource configuration.                                              |
| Core Features       | - Enforced on resources.<br>- Policies flow downward (Management Groups, Subscriptions, Resource Groups, and Resources) | - Enforced on identities.<br>- Organizes governance through a root, organizational units, and accounts. | - Organization Policy focuses on _what_, and lets the administrator set restrictions on specific resources. |
| Security/Compliance | Built-in compliance packs (CIS, NIST, PCI)                                                                              | Same                                                                                                    | Same                                                                                                        |
| Pricing             | Free                                                                                                                    | Per config item (0.003$)                                                                                | Free                                                                                                        |
| DevSecOps           | Policy as code support through Terraform                                                                                | Same as Azure.                                                                                          | Policy as code through Rego/OPA.                                                                            |

## CNAPP: Defender for Cloud

**AWS equivalent:** Security Hub
**GCP equivalent:** Security Command Center

|                     | Azure                                                        | AWS                                                                                                 | GCP                                                                                                               |
| ------------------- | ------------------------------------------------------------ | --------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------------- |
| Overview            | Cloud security posture + workload protection platform        | Security Hub is the CSPM, assesses your env against security industry standards and best practices. | Google Cloud's centralized vulnerability and threat reporting service.                                            |
| Core Features       | - Multi Cloud Support<br>- Through logic apps, defender APIs | - Limited integrations compared to Azure.<br>- Through EventBridge and Lambda Functions             | - Advanced security and compliance posture management, attack paths, threat detection, and compliance monitoring. |
| Security/Compliance | Compliance dashboards mapped to major frameworks             | Same                                                                                                | Same                                                                                                              |
| Pricing             | 5$ for paid tier                                             | Per resource unit                                                                                   | Premium Subscription                                                                                              |
| DevSecOps           | Native GitHub/GitLab connections.                            | Needs more setup than Azure.                                                                        | Needs more setup than Azure.                                                                                      |

## SIEM/SOAR: Sentinel

**AWS equivalent:** None
**GCP equivalent:** Google SecOps (soon deprecated)

|                     | Azure                                                                                                                                                                                                                                                         | AWS                                                   | GCP                                                                                                                                                                                                 |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Overview            | Cloud-native SIEM solution that delivers security across multicloud and multiplatform environments. Combines AI, automation, and threat intelligence to support threat detection, investigation, response, and proactive hunting.                             | Closest alternative is Security Lake as a data layer. | Built as a specialized layer on top of Google infrastructure, designed for enterprises to privately retain, analyze, and search the large amounts of security and network telemetry they generate.  |
| Core Features       | - Collect data across all users, devices, applications, and infrastructure, both on-premises and in multiple clouds.<br>- Detect previously undetected threats and minimize false positives using Microsoft's analytics and unparalleled threat intelligence. | N/A                                                   | - Can ingest numerous security telemetry types through a variety of methods.<br>- Gives analysts a way, when they see a potential threat, to investigate further and determine how best to respond. |
| Security/Compliance | 1 line                                                                                                                                                                                                                                                        | N/A                                                   | 1 line                                                                                                                                                                                              |
| Pricing             | $4.30/GB                                                                                                                                                                                                                                                      | N/A                                                   | Custom quoted                                                                                                                                                                                       |
| DevSecOps           | Supports detection-as-code.                                                                                                                                                                                                                                   | N/A                                                   | Supports detection-as-code.                                                                                                                                                                         |

---
## References

- https://towardsaws.com/the-definitive-comparision-guide-microsoft-entra-id-vs-aws-iam-afdc036b6fca
- https://learn.microsoft.com/en-us/azure/architecture/aws-professional/security-identity
- https://signoz.io/comparisons/aws-cloudwatch-vs-azure-monitor/
- https://cloud.google.com/logging
- https://cloudoptimo.com/blog/azure-policy-vs-aws-scps-how-cloud-governance-works-differently/
- https://docs.cloud.google.com/security-command-center/docs
- https://docs.aws.amazon.com/securityhub/latest/userguide/what-is-securityhub.html
- https://learn.microsoft.com/en-us/azure/sentinel/overview?tabs=defender-portal
- https://docs.cloud.google.com/chronicle/docs/secops/secops-overview
