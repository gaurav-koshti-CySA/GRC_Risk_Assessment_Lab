# GRC Risk Assessment Lab

**Author:** Gaurav Koshti
**Date:** April 2026
**Framework:** NIST Cybersecurity Framework (CSF) 2.0
**Environment:** Home Lab (VirtualBox — 3 VMs)
**GitHub:** [gaurav-koshti-CySA](https://github.com/gaurav-koshti-CySA)

---

## Executive Summary

This project documents a Governance, Risk, and Compliance (GRC) risk assessment conducted on a home lab environment using the NIST Cybersecurity Framework (CSF) 2.0 as the assessment standard. The objective was to evaluate the current security posture of the lab, identify control gaps, quantify risk, and produce an actionable remediation plan.

The assessment identified **10 risks** across all six CSF functions, including 1 Critical, 6 High, 2 Medium, and 1 Low. The lab scored **37% overall maturity (Initial level)**, with the Recover function scoring 0% — indicating no recovery or backup controls in place. Four compensating controls were implemented and evidenced during the assessment period.

This project demonstrates practical GRC skills including asset inventory, control gap analysis, risk scoring, and remediation planning — skills directly applicable to GRC Analyst, Security Analyst, and Compliance roles.

---

## Lab Environment

| Asset | OS | IP | Role |
|-------|----|----|------|
| WinServer2019 | Windows Server 2019 | 10.0.2.15 | Wazuh SIEM Manager / Nessus Scanner |
| Win11-Endpoint | Windows 11 Pro | 10.0.2.122 | Monitored Endpoint / Scan Target |
| Kali-Attacker | Kali Linux | 10.0.2.x | Attacker Simulation |

**Network:** VirtualBox NAT Network (10.0.2.0/24)
**Hypervisor:** Oracle VirtualBox 7.x

---

## Assessment Methodology

1. **Asset Inventory** — Documented all hardware, VMs, software, network components, and data assets aligned to NIST CSF ID.AM controls
2. **NIST CSF 2.0 Gap Assessment** — Scored 30 controls across all 6 CSF functions (Govern, Identify, Protect, Detect, Respond, Recover) using a 0/1/2 scoring scale
3. **Risk Register** — Built a 10-item risk register using Likelihood x Impact scoring (1-5 scale), incorporating findings from both the CSF assessment and Nessus vulnerability scans
4. **Remediation Plan** — Developed prioritized remediation actions for all identified risks, including step-by-step implementation guidance
5. **Control Implementation** — Implemented 4 compensating controls directly in the lab with screenshot evidence

---

## NIST CSF 2.0 Assessment Results

| Function | Score | Max | Maturity |
|----------|-------|-----|----------|
| Govern | 3 | 12 | Initial (25%) |
| Identify | 10 | 16 | Developing (63%) |
| Protect | 7 | 20 | Initial (35%) |
| Detect | 6 | 12 | Developing (50%) |
| Respond | 3 | 10 | Initial (30%) |
| Recover | 0 | 8 | Not Started (0%) |
| **Overall** | **29** | **78** | **Initial (37%)** |

**Key Finding:** The Identify function scored highest (63%) due to existing tooling — Nessus vulnerability scanning and Wazuh SIEM providing solid asset visibility and detection capability. The Recover function scored 0%, representing the most critical gap in the environment.

---

## Risk Register Summary

| Risk ID | Risk | Score | Level |
|---------|------|-------|-------|
| RSK-001 | No MFA on Administrative Accounts | 20 | CRITICAL |
| RSK-004 | Unpatched Vulnerabilities (Nessus) | 16 | HIGH |
| RSK-002 | No Incident Response Plan | 15 | HIGH |
| RSK-003 | No Recovery Plan / Unverified Backups | 15 | HIGH |
| RSK-005 | No Written Security Policy | 15 | HIGH |
| RSK-007 | No Account Lockout Policy | 12 | HIGH |
| RSK-009 | No Automated Wazuh Alerting | 12 | HIGH |
| RSK-008 | No Hardening Baseline Applied | 9 | MEDIUM |
| RSK-006 | Disk Encryption Not Enabled | 8 | MEDIUM |
| RSK-010 | No Threat Intelligence Feed | 4 | LOW |

Full risk details, scoring methodology, and Nessus integration notes are in [risk-register.md](risk-register.md).

---

## Controls Implemented During Assessment

The following controls were remediated directly in the lab as part of this project:

| Control | Risk Addressed | Evidence |
|---------|----------------|---------|
| Account Lockout Policy (5 attempts, 30 min) | RSK-007 | screenshots/account-lockout-policy.png |
| Windows Firewall Enabled (All Profiles) | RSK-008 | screenshots/firewall-enabled.png |
| Audit Logging Enabled (Logon + Policy Change) | RSK-001 | screenshots/audit-logging-enabled.png |
| Guest Account Disabled | RSK-008 | screenshots/guest-account-disabled.png |

---

## Repository Structure

```
GRC_Risk_Assessment_Lab/
├── README.md                  ← Executive summary (this file)
├── asset-inventory.md         ← Full hardware, VM, software, network, and data inventory
├── nist-csf-assessment.md     ← Scored NIST CSF 2.0 gap assessment (30 controls)
├── risk-register.md           ← 10-item risk register with Likelihood x Impact scoring
├── remediation-plan.md        ← Prioritized remediation plan with implementation steps
└── screenshots/
    ├── account-lockout-policy.png
    ├── firewall-enabled.png
    ├── audit-logging-enabled.png
    └── guest-account-disabled.png
```

---

## Key Takeaways

- A home lab environment with active security tooling (Wazuh SIEM, Nessus) still has significant GRC gaps — tooling alone does not equal compliance
- The biggest gaps were in Governance and Recovery — areas that require documentation and process, not just technology
- Risk scoring (Likelihood x Impact) provides a structured, defensible way to prioritize limited remediation resources
- Feeding Nessus scan findings directly into the risk register bridges the gap between technical vulnerability management and GRC risk management

---

## Related Projects

- [Nessus_Vuln_Management_Lab](https://github.com/gaurav-koshti-CySA/Nessus_Vuln_Management_Lab) — Vulnerability scanning findings that fed into RSK-004
- [Wazuh_SIEM_Lab](https://github.com/gaurav-koshti-CySA/Wazuh_SIEM_Lab) — SIEM deployment that supports DE and RS functions in this assessment
- [Entra_IAM_Lab](https://github.com/gaurav-koshti-CySA/Entra_Iam_Lab) — Identity and access management project

---

## Certifications

- CompTIA Security+ (Achieved)
- CompTIA CySA+ (In Progress)

---

*This project was completed as part of a home lab security portfolio targeting Security Analyst and GRC Analyst roles. All work is original and conducted in a personal lab environment.*# GRC_Risk_Assessment_Lab
NIST CSF 2.0 risk assessment and remediation project conducted on a home lab environment
