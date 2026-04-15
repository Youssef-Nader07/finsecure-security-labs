# FinSecure SA : Security Labs Series

> A practical cybersecurity lab series implementing 
> real security controls mapped to regulatory 
> requirements in a fictional financial services 
> environment.

---

## About This Series

This repository documents a series of hands-on 
security labs built around FinSecure SA — a fictional 
Moroccan financial services company. Each lab starts 
from a realistic business scenario, identifies the 
applicable regulatory requirements, implements 
technical controls, and documents the results 
honestly — including what worked, what didn't, 
and what gaps remain.

The goal is not to follow tutorials. The goal is 
to think through real security problems the way 
a practicing security engineer would — with 
regulatory context, architectural decisions, 
and honest gap analysis.

---

## The Company : FinSecure SA

**FinSecure SA** is a fictional Moroccan financial 
services firm used as the lab environment throughout 
this series.

| Detail | Description |
|---|---|
| Headquarters | Casablanca, Morocco |
| Branch Office | Paris, France |
| Employees | 200 |
| Sector | Retail banking and financial services |
| Clients | Individual retail banking clients |

**Data processed:**
- Full names and contact information
- Moroccan national ID numbers (CIN —
  Carte d'Identité Nationale)
- International Bank Account Numbers (IBAN) —
  Moroccan and French formats
- Transaction histories and account balances
- Employment and income information for
  credit assessments

**Regulatory environment:**

| Regulation | Scope | Why it applies |
|---|---|---|
| GDPR | French operations and EU client data | FinSecure France SAS processes personal data of French clients and is subject to GDPR as a data controller |
| ISO/IEC 27001 | Group-wide information security | FinSecure SA maintains ISO 27001 certification as a requirement of the Bank of Africa Group |
| DORA | French financial operations | FinSecure France SAS is regulated by the Banque de France as a payment institution and falls under DORA scope |
| Bank Al-Maghrib regulations | Moroccan operations | Morocco's central bank requires financial institutions to maintain specific information security controls |
| PCI DSS | Payment card processing | FinSecure SA processes client payment card data for certain product lines |

---

## Why FinSecure SA

Most security lab environments use generic corporate 
scenarios that don't reflect the complexity of 
real-world regulated industries. Financial services 
sits at the intersection of strict regulatory 
requirements, sensitive personal data, cross-border 
operations, and sophisticated threat actors.

FinSecure SA was designed to be:

- **Realistic** — scenarios reflect actual incidents 
  and regulatory challenges that financial services 
  security teams face
- **Technically rich** — the environment requires 
  custom implementations that go beyond default 
  Microsoft configurations
- **Regulatory grounded** — every control is mapped 
  to a specific article or annex in a real regulation
- **Honest** — every lab documents limitations and 
  gaps alongside what works

---

## Lab Series

### Lab 01 — The Accidental Breach: Email DLP Implementation
**Status: In Progress**

A junior analyst accidentally emails a spreadsheet 
containing 47 client records — IBANs and national 
ID numbers — to his personal Gmail address. No DLP 
policy exists. Nothing blocked it. The Data Protection 
Officer issues a formal requirement to implement 
technical controls within 30 days.

**Regulatory scope:**
- GDPR Article 5(1)(f) — Integrity and confidentiality
- GDPR Article 25 — Privacy by design and by default
- GDPR Article 32 — Security of processing
- GDPR Article 33 — Breach notification
- ISO/IEC 27001 Annex A.8.12 — Data leakage prevention

**Technical implementation:**
- Custom sensitive information types for Moroccan
  CIN and IBAN formats in Microsoft Purview
- Layered DLP architecture combining Microsoft
  Purview DLP policies and Exchange mail flow rules
- Three-tier response: hard block on personal domains,
  volume-based block with override, policy tip warning

[View Lab 01 →](./lab-01-email-dlp/)

---

### Lab 02 — The Insider Threat: Endpoint and Cloud DLP
**Status: Coming Soon**

Three months after fixing email exfiltration, 
an insider risk alert fires. A senior analyst 
in the Paris office is copying large volumes of 
client data to a USB drive and uploading files 
to a personal OneDrive account. The DLP policy 
from Lab 01 only covered email. Endpoint and 
cloud storage exfiltration was never addressed.

**Regulatory scope:**
- GDPR Article 5(1)(f) — Integrity and confidentiality
- GDPR Article 25 — Privacy by design and by default
- GDPR Article 32 — Security of processing
- ISO/IEC 27001 Annex A.8.12 — Data leakage prevention
- ISO/IEC 27001 Annex A.6.6 — Confidentiality agreements

**Technical implementation:**
- Microsoft Purview Insider Risk Management
- Endpoint DLP — blocking sensitive data copying
  to USB drives and personal cloud storage
- Sensitivity labels — classifying data before
  protecting it
- SharePoint and OneDrive DLP policies
- Alert triage and investigation workflow

[View Lab 02 →](./lab-02-endpoint-cloud-dlp/) *(Coming Soon)*

---

### Lab 03 — The Phantom Admin: Identity Governance
**Status: Coming Soon**

An access review reveals a Global Administrator 
account belonging to a PayFlow employee who left 
before the acquisition completed. The account 
has been active for 67 days with no legitimate 
owner. Nobody knows what it accessed. Investigate 
before remediating — then build controls to ensure 
this never happens again.

**Regulatory scope:**
- ISO/IEC 27001 Annex A.9 — Access control
- GDPR Article 32 — Security of processing
- Zero Trust least privilege principles
- DORA Article 9 — ICT security policies

**Technical implementation:**
- Entra ID audit log investigation and
  timeline reconstruction
- Privileged Identity Management —
  eliminating permanent admin assignments
- Just-In-Time access with approval workflows
- Automated quarterly access reviews
- Incident report documentation

[View Lab 03 →](./lab-03-phantom-admin/) *(Coming Soon)*

---

### Lab 04 — Zero Trust Foundation: Conditional Access Architecture
**Status: Coming Soon**

Following a security incident, the board mandates 
a Zero Trust implementation program. Phase one — 
identity controls. Currently no MFA enforcement 
exists, no device compliance requirement, and no 
risk-based access controls. Any compromised 
credential gives full access from anywhere 
on any device.

**Regulatory scope:**
- ISO/IEC 27001 Annex A.9 — Access control
- NIST SP 800-207 — Zero Trust Architecture
- GDPR Article 32 — Security of processing
- DORA Article 9 — ICT security policies

**Technical implementation:**
- Conditional Access policy architecture —
  device health, user risk, application sensitivity
- Named location policies for Morocco and France
- Entra ID Identity Protection — risk-based
  Conditional Access
- Break glass account strategy
- Dependency mapping and failure mode analysis

[View Lab 04 →](./lab-04-zero-trust/) *(Coming Soon)*

---

### Lab 05 — The Leaky Integration: Third-Party App Governance
**Status: Coming Soon**

A GDPR audit flags that a SaaS tool inherited 
from an acquisition has broad OAuth permissions — 
including read access to all employee emails. 
No Data Processing Agreement exists. Three 
inherited ICT providers are based outside the EU 
with unclear data residency. You have 30 days 
to assess, remediate what you can, and document 
what you cannot.

**Regulatory scope:**
- GDPR Article 28 — Processor obligations
- GDPR Article 25 — Privacy by design
- DORA Article 28 — Third-party ICT risk management
- ISO/IEC 27001 Annex A.5.19 — Supplier relationships

**Technical implementation:**
- OAuth app permission audit in Microsoft Entra ID
- Microsoft Defender for Cloud Apps CASB policies
- App governance configuration
- Third-party ICT risk register
- DORA Article 30 contractual gap analysis

[View Lab 05 →](./lab-05-third-party-risk/) *(Coming Soon)*

---

### Lab 06 — The Breach: Incident Response Under 72 Hours
**Status: Coming Soon**

Monday morning. Sentinel fires at 6:47am. 
An account authenticated from Casablanca and 
Amsterdam within 40 minutes — physically impossible. 
The account downloaded 2.3GB of client financial 
data. It is 9:00am. The CISO is on a flight. 
You have 72 hours before GDPR Article 33 requires 
supervisory authority notification.

**Regulatory scope:**
- GDPR Article 33 — Breach notification
- GDPR Article 34 — Communication to data subjects
- ISO/IEC 27001 Annex A.5.24 — Incident management
- DORA Article 19 — Major incident reporting

**Technical implementation:**
- Microsoft Sentinel investigation and
  timeline reconstruction
- Entra ID impossible travel alert analysis
- Evidence preservation and chain of custody
- GDPR Article 33 notification assessment
- 72-hour incident report in supervisory
  authority format

[View Lab 06 →](./lab-06-breach-response/) *(Coming Soon)*

---

### Lab 07 — DORA Compliance: ICT Incident Classification
**Status: Coming Soon**

FinSecure France SAS is three weeks into DORA 
enforcement. The Banque de France sends a 
supervisory questionnaire asking how major ICT 
incidents are classified and reported within 
4 hours. FinSecure has no automated classification 
system. A Microsoft 365 outage last November 
may have been a DORA major incident — nobody 
knows because no classification framework existed.

**Regulatory scope:**
- DORA Article 18 — ICT incident classification
- DORA Article 19 — Major incident reporting
- ISO/IEC 27001 Annex A.5.24 — Incident management

**Technical implementation:**
- KQL analytics rules in Microsoft Sentinel
  mapping incidents to DORA classification criteria
- DORA compliance dashboard — Sentinel workbook
- Automated Teams notification triggering
  the 4-hour reporting clock
- Retrospective analysis of the November outage
- Supervisory authority questionnaire response

[View Lab 07 →](./lab-07-dora-classification/) *(Coming Soon)*

---

## Technical Environment

| Component | Tool | Purpose |
|---|---|---|
| Identity | Microsoft Entra ID | User management, Conditional Access, PIM |
| Data Protection | Microsoft Purview | DLP, sensitivity labels, insider risk |
| Email | Exchange Online | Email DLP and mail flow rules |
| SIEM | Microsoft Sentinel | Alert detection and incident investigation |
| Endpoint | Microsoft Defender for Business | EDR and endpoint DLP |
| CASB | Microsoft Defender for Cloud Apps | Third-party app governance |

**License:** Microsoft 365 Business Premium trial
with Microsoft Entra ID P2 trial for identity
governance labs.

---

## Lab Writeup Structure

Every lab in this series follows the same structure:

1. **The Incident** — what happened and why it matters
2. **Regulatory Framework** — specific articles and
   controls that apply
3. **Design Decisions** — architectural choices
   and their rationale
4. **Technical Implementation** — step by step
   with annotated screenshots
5. **Testing Results** — full test matrix
   with honest results
6. **Unexpected Findings** — what didn't behave
   as expected
7. **Gaps and Limitations** — what the controls
   don't protect against
8. **Regulatory Mapping Summary** — control to
   regulation mapping table
9. **Lessons Learned** — genuine observations
   from the implementation
10. **References** — regulation links, Microsoft
    documentation, standards

---

## About

These labs were built as independent technical 
practice alongside professional experience in 
cybersecurity, IT audit, and data protection 
across financial environments in Morocco and France.

The FinSecure SA scenario is entirely fictional. 
Any resemblance to real companies, individuals, 
or incidents is coincidental.

---

*Last updated: April 2026*
