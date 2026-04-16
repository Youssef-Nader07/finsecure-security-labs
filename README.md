# FinSecure SA : Security Labs Series

A practical cybersecurity lab series implementing 
real security controls mapped to regulatory 
requirements in a fictional financial services 
environment.

## About This Series

This repository documents a series of hands-on 
security labs built around FinSecure SA, a fictional 
Moroccan financial services company. Each lab starts 
from a realistic business scenario, identifies the 
applicable regulatory requirements, implements 
technical controls, and documents the results 
honestly including what worked, what didn't, 
and what gaps remain.

The goal is not to follow tutorials. The goal is 
to think through real security problems the way 
a practicing security engineer would, with 
regulatory context, architectural decisions, 
and honest gap analysis.

## The Company

FinSecure SA is a fictional Moroccan financial 
services firm headquartered in Casablanca with 
a branch office in Paris. 200 employees. They 
process retail banking client data including 
names, IBANs, Moroccan national ID numbers, 
and transaction histories.

They operate under GDPR for their French operations, 
ISO/IEC 27001 as a Bank of Africa Group requirement, 
DORA as a Banque de France regulated payment 
institution, and PCI DSS for payment card processing.

This regulatory environment was chosen deliberately. 
Financial services sits at the intersection of strict 
compliance requirements, sensitive personal data, 
cross-border operations, and real threat actors. 
Generic lab environments don't reflect that complexity. 
This one tries to.

## Labs

### Lab 01 - The Accidental Breach: Email DLP Implementation
**Status: Complete**

A junior analyst accidentally emails 47 client 
records containing IBANs and national ID numbers 
to his personal Gmail. No DLP policy exists. 
Nothing blocked it. The DPO issues a formal 
requirement to implement technical controls 
within 30 days.

Regulatory scope: GDPR Articles 5, 25, 32, 33 
and ISO/IEC 27001 Annex A.8.12

Technical implementation: custom sensitive 
information types for Moroccan CIN and IBAN 
formats, layered DLP architecture combining 
Microsoft Purview and Exchange mail flow rules, 
three-tier response based on risk level.

[View Lab 01](./lab-01-email-dlp/)

### Lab 02 - The Insider Threat: Endpoint and Cloud DLP
**Status: Coming Soon**

Three months after fixing email exfiltration an 
insider risk alert fires. A senior analyst is 
copying client data to a USB drive and uploading 
files to a personal OneDrive. Email DLP alone 
was never enough.

Regulatory scope: GDPR Articles 5, 25, 32 and 
ISO/IEC 27001 Annex A.8.12

Technical implementation: Microsoft Purview 
Insider Risk Management, endpoint DLP, sensitivity 
labels, SharePoint and OneDrive DLP policies.

### Lab 03 - The Phantom Admin: Identity Governance
**Status: Coming Soon**

An access review reveals a Global Administrator 
account belonging to an employee who left before 
an acquisition completed. Active for 67 days 
with no legitimate owner. Nobody knows what 
it accessed.

Regulatory scope: ISO/IEC 27001 Annex A.9, 
GDPR Article 32, DORA Article 9, Zero Trust 
least privilege principles

Technical implementation: Entra ID audit log 
investigation, Privileged Identity Management, 
Just-In-Time access, automated access reviews.

### Lab 04 - Zero Trust Foundation: Conditional Access
**Status: Coming Soon**

Following a security incident the board mandates 
Zero Trust. No MFA enforcement exists, no device 
compliance requirement, no risk-based access 
controls. Any compromised credential gives full 
access from anywhere.

Regulatory scope: ISO/IEC 27001 Annex A.9, 
NIST SP 800-207, GDPR Article 32, DORA Article 9

Technical implementation: Conditional Access 
policy architecture, named location policies, 
Entra ID Identity Protection, break glass 
account strategy.

### Lab 05 - The Leaky Integration: Third-Party App Governance
**Status: Coming Soon**

A GDPR audit flags that a SaaS tool inherited 
from an acquisition has OAuth read access to 
all employee emails. No Data Processing Agreement 
exists. Three inherited providers are based 
outside the EU with unclear data residency.

Regulatory scope: GDPR Articles 25, 28, 
DORA Article 28, ISO/IEC 27001 Annex A.5.19

Technical implementation: OAuth permission audit, 
Microsoft Defender for Cloud Apps CASB policies, 
third-party ICT risk register, DORA Article 30 
contractual gap analysis.

### Lab 06 - The Breach: Incident Response Under 72 Hours
**Status: Coming Soon**

Monday morning. Sentinel fires at 6:47am. An 
account authenticated from Casablanca and Amsterdam 
within 40 minutes, physically impossible. 2.3GB 
of client data downloaded. The CISO is on a flight. 
72 hours before GDPR Article 33 notification 
is required.

Regulatory scope: GDPR Articles 33, 34, 
ISO/IEC 27001 Annex A.5.24, DORA Article 19

Technical implementation: Microsoft Sentinel 
investigation, impossible travel alert analysis, 
evidence preservation, GDPR Article 33 assessment, 
72-hour supervisory authority report.

### Lab 07 - DORA Compliance: ICT Incident Classification
**Status: Coming Soon**

Three weeks into DORA enforcement the Banque de 
France asks how major ICT incidents are classified 
and reported within 4 hours. FinSecure has no 
automated classification system. A Microsoft 365 
outage last November may have been a major incident. 
Nobody knows.

Regulatory scope: DORA Articles 18, 19 and 
ISO/IEC 27001 Annex A.5.24

Technical implementation: KQL analytics rules 
in Microsoft Sentinel mapped to DORA classification 
criteria, DORA compliance dashboard, automated 
4-hour notification trigger, retrospective 
outage analysis.

## Environment

Microsoft 365 Business Premium trial tenant 
with Microsoft Entra ID P2 for identity 
governance labs. Tools used across the series 
include Microsoft Purview, Exchange Online, 
Microsoft Sentinel, Defender for Cloud Apps, 
and Microsoft Entra ID.

## Writeup Structure

Every lab follows the same structure: the incident, 
regulatory requirements, design decisions, technical 
implementation with screenshots, testing results, 
unexpected findings, gaps and limitations, regulatory 
mapping summary, lessons learned, and references.

## About

Built as independent technical practice alongside 
professional experience in cybersecurity, IT audit, 
and data protection across financial environments 
in Morocco and France.

FinSecure SA is entirely fictional. Any resemblance 
to real companies or incidents is coincidental.

*Last updated: April 2026*
