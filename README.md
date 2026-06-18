# CloudSprout Inc. — Information Security Risk Assessment

**Type:** Mock Assessment | Portfolio Artifact  
**Author:** Alex Truong  
**Date:** June 2026  
**Frameworks:** NIST SP 800-30 Rev. 1 · NIST CSF 2.0 · CCPA  

---

## Overview

This project is a full-scope information security risk assessment conducted against CloudSprout Inc., a fictional 50-person B2B SaaS company headquartered in Seattle, Washington. CloudSprout serves approximately 150 mid-market e-commerce brands and is built entirely on AWS, integrating with third-party platforms including Shopify and Amazon Seller Central.

The assessment was designed to mirror the kind of work a mid-level GRC analyst or security risk practitioner would produce for a real client engagement: starting from an asset inventory, building a structured risk register, scoring risks against a defined methodology, mapping gaps to a recognized security framework, and delivering findings in a format that is actionable at both the executive and technical levels.

CloudSprout Inc. is a fictional company. All findings, assets, personnel, and risk data are invented for portfolio and professional development purposes. No real organization or confidential data is referenced.

---

## What This Project Demonstrates

This assessment was built to show depth across the full risk assessment lifecycle, not just familiarity with frameworks. Specifically, it demonstrates:

**Risk identification and scoring.** Fifteen risks were identified across application, infrastructure, data, and third-party integration categories. Each risk was scored using a 5x5 Likelihood-by-Impact matrix aligned to NIST SP 800-30 Rev. 1, with both inherent and residual scores calculated after evaluating the effectiveness of existing controls.

**Justification rigor.** Every risk score is supported by a written justification log that explains why each likelihood and impact rating was assigned, what existing controls were considered, and what the residual score rationale is. Scores are not asserted -- they are argued.

**Framework mapping.** All fifteen risks are mapped to specific NIST CSF 2.0 categories and NIST SP 800-30 threat tables. A standalone NIST CSF 2.0 gap analysis covers all five CSF functions (Govern, Identify, Protect, Detect, Respond, Recover) with current-state maturity ratings and linked risk IDs.

**Executive communication.** The Executive Summary translates technical findings into business language suitable for a C-suite or board audience. It leads with the "why it matters" framing for each top risk rather than the technical mechanics.

**Prioritized remediation planning.** Recommended actions are organized across four time horizons (0-30 days, 30-90 days, 90-180 days, and ongoing) based on implementation complexity, cost, and risk reduction impact.

---

## Risk Profile Summary

| Risk Level | Inherent Count | Residual Count |
|---|---|---|
| Extreme | 1 | 0 |
| Critical | 2 | 0 |
| High | 5 | 1 |
| Medium | 7 | 12 |
| Low | 0 | 2 |
| **Total** | **15** | **15** |

The inherent profile reflects a company that has scaled its product without a corresponding investment in security governance. One Extreme risk, two Critical risks, and five High risks represent genuine and realistic exposure for a company at this stage. The residual profile shows that targeted, achievable controls eliminate the Extreme and Critical categories entirely and bring the High count from five to one.

---

## Top Five Risks (by Residual Score)

**R-01 — Compromised Customer API Tokens** | Inherent: 20 (Extreme) | Residual: 12 (High)  
CloudSprout stores OAuth tokens and API keys that grant direct access to customers' Shopify and Amazon accounts. A credential theft event creates liability that extends far beyond CloudSprout's own environment. Primary action: implement field-level encryption and enforce a 90-day rotation policy.

**R-04 — Phishing Attack Leads to Account Takeover** | Inherent: 16 (Critical) | Residual: 9 (Medium)  
Without enforced MFA and a security awareness program, a single successful phish could grant an attacker access to Google Workspace, GitHub, or the AWS console. Primary action: enforce MFA with no exceptions across all critical systems.

**R-02 — Ransomware Attack on AWS Environment** | Inherent: 15 (Critical) | Residual: 8 (Medium)  
No immutable backup strategy and no tested disaster recovery runbook means that a ransomware event could cause a total service outage with an unknown recovery timeline. Primary action: enable S3 Object Lock and conduct a DR tabletop exercise.

**R-14 — Customer Data Commingled Across Tenants** | Inherent: 10 (High) | Residual: 8 (Medium)  
A bug allowing one customer to view another's data would immediately disqualify CloudSprout in enterprise procurement and trigger breach notification for every affected tenant. Primary action: commission an external penetration test focused on tenant boundary testing.

**R-03 — Misconfigured AWS S3 Bucket Exposes Customer Data** | Inherent: 12 (High) | Residual: 6 (Medium)  
Without automated scanning or IaC enforcement, a developer could create a public bucket that exposes customer data for weeks before detection. Primary action: block all public S3 access at the AWS account level.

---

## Documents

| Document | Description | Link |
|---|---|---|
| Executive Summary | Board and C-suite narrative of findings, top risks, and recommended actions | [View (Markdown)](./executive-summary.md) |
| Executive Summary (PDF) | Formatted PDF version | [View (Google Drive)](https://drive.google.com/file/d/1S5vItaKQ0N3oLmB_dGa0TXUPoyW9d0TS/view?usp=sharing) |
| Risk Register Workbook | Full risk register, asset inventory, scoring methodology, NIST CSF gap analysis, risk justification log, and dashboard | [Download (Excel)](/Alex_CloudSprout_Risk_Register.xlsx) |

---

## Workbook Tab Guide

The Excel workbook contains seven tabs. Here is what each one contains and why it is included:

**Cover** -- Organization profile, assessment metadata, and scope statement. Establishes the fictional company context and frames the engagement.

**Methodology** -- Defines the 5x5 likelihood and impact scales, risk level bands, and scoring rationale. Ensures the register is self-contained and auditable without reference to external documents.

**Asset Inventory** -- Seventeen assets inventoried across application, infrastructure, data store, hardware, and third-party integration categories. Each asset includes criticality, data classification, and owner role.

**Risk Register** -- The core deliverable. Fifteen risks with full NIST 800-30 threat source and event classification, affected asset mapping, vulnerability description, inherent scoring, existing control evaluation, residual scoring, recommended remediation, risk owner, and treatment decision.

**Risk Justification Log** -- Written rationale for every likelihood and impact score assigned. Explains the evidence base for each rating and the logic behind residual score projections.

**Dashboard** -- Visual summary of risk distribution, top five risks by residual score, key observations, and the full priority action timeline. Designed for executive consumption.

**NIST CSF Gap Analysis** -- Maturity assessment across all NIST CSF 2.0 categories, with current-state descriptions, maturity ratings (1-5), gap descriptions, and linked risk IDs. Includes an overall tier rating and SOC 2 Type II readiness timeline.

---

## Regulatory Context

CloudSprout's primary regulatory exposure is under CCPA. The company processes personal information belonging to California residents on behalf of its customers, creating obligations around deletion request timelines and breach notification. Two specific findings in this assessment directly implicate CCPA: the absence of a data retention and deletion policy (R-11) and the absence of a documented incident response plan (R-09). The assessment also frames remediation recommendations in terms of SOC 2 Type II readiness, as the controls required to address these findings are largely coextensive with what a SOC 2 auditor would evaluate.

---

## Methodology Reference

**Risk Assessment Process:** NIST SP 800-30 Rev. 1 (Guide for Conducting Risk Assessments)  
**Security Framework:** NIST Cybersecurity Framework (CSF) 2.0  
**Scoring Model:** 5x5 Likelihood x Impact matrix with inherent and residual scoring  
**Regulatory Reference:** California Consumer Privacy Act (CCPA)  
**Target Compliance Framework:** SOC 2 Type II  

---

*Mock assessment created for portfolio and professional development purposes. CloudSprout Inc. is a fictional company. All findings, assets, personnel, and risk data are invented for educational purposes. No real organization, systems, or confidential data are referenced.*
