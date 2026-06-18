# CloudSprout Inc. — Information Security Risk Assessment
## Executive Summary

**MOCK ASSESSMENT:** This document is a simulated professional artifact created for portfolio and professional development purposes only. CloudSprout Inc. is a fictional company. All findings, assets, personnel, and risk data are invented for educational purposes. No real organization, systems, or confidential data are referenced.

---

**Prepared by:** Alex Truong
**Assessment Date:** June 2025
**Document Status:** Mock Assessment — Portfolio Artifact

---

## Organization at a Glance

CloudSprout Inc. is a 50-person B2B SaaS company headquartered in Seattle, Washington. The company provides automated inventory tracking, predictive ordering, and supplier management software to approximately 150 mid-sized e-commerce brands. CloudSprout processes business-critical data on behalf of its customers, including inventory volumes, supplier contracts, and API tokens connected to third-party marketplaces such as Shopify and Amazon Seller Central.

As a cloud-native platform built entirely on Amazon Web Services, CloudSprout's security posture directly affects its customers' supply chain operations. The company is at a pivotal stage: it has grown organically to its current scale without formal security governance, and is now facing enterprise procurement requirements that demand a demonstrable and documented security posture.

---

## Assessment Overview

This assessment evaluated CloudSprout's information security risk landscape using NIST SP 800-30 Rev. 1 as the risk assessment process framework. Seventeen assets were inventoried across application, infrastructure, data, and third-party integration categories. Fifteen risks were identified, scored, and analyzed using a 5x5 Likelihood-by-Impact model. All organizational details are based on the company's fictional profile as defined for this portfolio exercise.

---

## Deliverable Package

| Document | Description |
|----------|-------------|
| Risk Register Workbook (.xlsx) | Full risk register with 15 risks, asset inventory, scoring methodology, dashboard, and justification log. Gap analysis (NIST CSF 2.0) is included as Tab 7 of this workbook. |
| Executive Summary (this document) | Board and C-suite summary of findings, top risks, and recommended actions. |

---

## Key Findings: Risk Distribution

| Risk Level | Inherent Count | Residual Count |
|------------|---------------|----------------|
| Extreme    | 1             | 0              |
| Critical   | 2             | 0              |
| High       | 5             | 1              |
| Medium     | 7             | 12             |
| Low        | 0             | 2              |
| **Total**  | **15**        | **15**         |

The inherent risk profile reflects a company that has built a functional product and customer base without a corresponding investment in security governance. One Extreme risk (compromised API tokens) and two Critical risks (ransomware, phishing) represent genuine exposure, not theoretical scenarios. The residual distribution shows that applying the recommended controls would eliminate the Extreme and Critical risks, reduce the number of High risks from five to one, and increase Medium risks as formerly high risks are brought into a managed state. The two Low residual risks reflect well-controlled outcomes after remediation.

---

## Top Five Risks (by Residual Score)

### 1. Compromised Customer API Tokens (R-01)
**Why it matters:** CloudSprout stores OAuth tokens and API keys that grant direct access to customers' Shopify and Amazon Seller Central accounts. If stolen, an attacker gains control over a customer's live marketplace operations, creating liability well beyond CloudSprout's own environment.

**Scores:** Inherent 20 (Extreme) | Residual 12 (High)

**Most important action:** Implement field-level encryption for all stored tokens and enforce a 90-day rotation policy before any other remediation effort.

---

### 2. Phishing Attack Leads to Account Takeover (R-04)
**Why it matters:** Phishing is the most common initial access vector across all industries. Without mandatory MFA and security awareness training, a single successful phish could grant an attacker access to Google Workspace, GitHub, or the AWS console.

**Scores:** Inherent 16 (Critical) | Residual 9 (Medium)

**Most important action:** Enforce MFA for every account on Google Workspace, GitHub, and AWS — no exceptions — and deploy quarterly phishing simulations.

---

### 3. Ransomware Attack on AWS Environment (R-02)
**Why it matters:** CloudSprout has no immutable backup strategy and no tested disaster recovery runbook. A ransomware event could cause a total service outage with unknown recovery time, breaking customer contracts and potentially ending the business.

**Scores:** Inherent 15 (Critical) | Residual 8 (Medium)

**Most important action:** Enable S3 Object Lock for backup buckets and conduct a disaster recovery tabletop exercise to establish a documented and tested recovery time objective.

---

### 4. Customer Data Commingled Across Tenants (R-14)
**Why it matters:** CloudSprout serves approximately 150 customers on a shared platform. A bug that allows one customer to view another customer's data would be immediately disqualifying in enterprise procurement conversations and would trigger breach notification obligations for every affected customer.

**Scores:** Inherent 10 (High) | Residual 8 (Medium)

**Most important action:** Commission an external web application penetration test with explicit focus on tenant boundary testing.

---

### 5. Misconfigured AWS S3 Bucket Exposes Customer Data (R-03)
**Why it matters:** S3 misconfiguration is one of the most documented cloud failures. Without automated scanning or infrastructure-as-code review, a developer could manually create a public bucket that exposes customer data for weeks.

**Scores:** Inherent 12 (High) | Residual 6 (Medium)

**Most important action:** Block all public S3 access at the AWS account level — one setting, free, effective immediately.

---

## Priority Actions by Time Horizon

### 0 to 30 Days
- Enforce MFA across all AWS, GitHub, and Google Workspace accounts
- Conduct IAM access review and remove overprivileged roles
- Block all public S3 access at the AWS account level
- Enable AWS CloudTrail in all regions

### 30 to 90 Days
- Draft and ratify an Incident Response Plan with assigned roles
- Enable Dependabot or Snyk in the CI/CD pipeline
- Implement field-level encryption for stored API tokens
- Commission a web application penetration test

### 90 to 180 Days
- Deploy security awareness training for all staff
- Draft a Data Retention and Deletion Policy
- Implement MDM enrollment requirement for all devices
- Enable S3 Object Lock for backup buckets and test the DR runbook

### Ongoing
- Conduct quarterly IAM access reviews
- Run monthly phishing simulation exercises
- Patch critical CVEs within a 14-day SLA
- Monitor vendor security advisories for SaaS tools

---

## Regulatory Context

CloudSprout does not process payment card data directly (Stripe handles payments), which removes PCI-DSS as an immediate compliance obligation. The primary regulatory exposure is under the California Consumer Privacy Act (CCPA), which applies because CloudSprout collects and processes personal information belonging to California residents on behalf of its customers. Several findings in this assessment directly implicate CCPA: the absence of a data retention and deletion policy (R-11) creates risk around honoring consumer deletion requests within the required 45-day window, and the absence of a documented incident response plan (R-09) creates risk around the 72-hour breach notification obligation. As CloudSprout pursues SOC 2 Type II certification, the controls required to address the findings in this assessment are largely coextensive with what a SOC 2 auditor will evaluate.

---

## Mock Assessment Disclaimer

MOCK ASSESSMENT: This document is a simulated professional artifact created for portfolio and professional development purposes only. CloudSprout Inc. is a fictional company. All findings, assets, personnel, and risk data are invented for educational purposes. No real organization, systems, or confidential data are referenced. This document is not affiliated with or endorsed by any real company.
