# Risk Register
## GRC Risk Assessment Lab — Home Lab Environment

**Document Version:** 1.0
**Assessment Date:** April 2026
**Prepared By:** Gaurav Koshti
**Framework Reference:** NIST CSF 2.0
**Risk Scoring Method:** Likelihood x Impact (1-5 scale)

---

## Risk Scoring Matrix

**Likelihood Scale:**
| Score | Level | Description |
|-------|-------|-------------|
| 5 | Critical | Almost certain to occur |
| 4 | High | Likely to occur |
| 3 | Medium | Possible |
| 2 | Low | Unlikely |
| 1 | Very Low | Rare |

**Impact Scale:**
| Score | Level | Description |
|-------|-------|-------------|
| 5 | Critical | Complete loss of confidentiality, integrity, or availability |
| 4 | High | Significant impact — major data loss or system outage |
| 3 | Medium | Moderate impact — partial disruption |
| 2 | Low | Minor impact — limited disruption |
| 1 | Very Low | Negligible impact |

**Risk Score = Likelihood x Impact**
| Score Range | Risk Level |
|-------------|------------|
| 20-25 | CRITICAL |
| 12-19 | HIGH |
| 6-11 | MEDIUM |
| 1-5 | LOW |

---

## Risk Register

| Risk ID | Risk Title | Description | Source | CSF Function | Likelihood | Impact | Risk Score | Risk Level | Owner | Status |
|---------|------------|-------------|--------|--------------|------------|--------|------------|------------|-------|--------|
| RSK-001 | No MFA on Administrative Accounts | Administrative accounts on Windows Server 2019 and Windows 11 have no multi-factor authentication. An attacker who obtains credentials gains full access with no secondary barrier. | NIST CSF Gap (PR.AA-02) | Protect | 4 | 5 | 20 | CRITICAL | Gaurav Koshti | Open |
| RSK-002 | No Incident Response Plan | There is no documented incident response plan. In the event of a security incident, response actions would be ad hoc, increasing dwell time and impact. | NIST CSF Gap (RS.MA-01) | Respond | 3 | 5 | 15 | HIGH | Gaurav Koshti | Open |
| RSK-003 | No Data Recovery Plan or Verified Backups | No formal recovery plan exists. VM snapshots are taken informally but never verified for restoration integrity. A ransomware or corruption event could result in permanent data loss. | NIST CSF Gap (RC.RP-01, RC.RP-05) | Recover | 3 | 5 | 15 | HIGH | Gaurav Koshti | Open |
| RSK-004 | Unpatched Vulnerabilities on Endpoints | Nessus Essentials scans identified unpatched vulnerabilities on the Windows 11 endpoint. Exploitation of known CVEs could lead to privilege escalation or lateral movement. | Nessus Scan Findings | Protect | 4 | 4 | 16 | HIGH | Gaurav Koshti | Open |
| RSK-005 | No Written Security Policy | There is no formal security policy governing the lab environment. Without policy, controls are applied inconsistently and cannot be audited or enforced. | NIST CSF Gap (GV.PO-01) | Govern | 5 | 3 | 15 | HIGH | Gaurav Koshti | Open |
| RSK-006 | Disk Encryption Not Enabled | Virtual machine disks are not encrypted. If the physical host were compromised or stolen, all VM data could be accessed directly from disk files. | NIST CSF Gap (PR.DS-01) | Protect | 2 | 4 | 8 | MEDIUM | Gaurav Koshti | Open |
| RSK-007 | No Account Lockout Policy Configured | Windows endpoints do not have an account lockout policy enforced. This enables unlimited brute-force password attempts against local accounts without detection or lockout. | NIST CSF Gap (PR.AA-01) | Protect | 4 | 3 | 12 | HIGH | Gaurav Koshti | Open |
| RSK-008 | No Hardening Baseline Applied | Systems were not configured against any hardening standard (CIS Benchmarks, DISA STIG). Default configurations leave unnecessary services, ports, and features enabled. | NIST CSF Gap (PR.PS-01) | Protect | 3 | 3 | 9 | MEDIUM | Gaurav Koshti | Open |
| RSK-009 | No Automated Alerting or Notification | Wazuh alerts are only visible when the dashboard is manually reviewed. There is no email, SMS, or webhook notification configured for critical alerts. | NIST CSF Gap (DE.AE-06) | Detect | 4 | 3 | 12 | HIGH | Gaurav Koshti | Open |
| RSK-010 | No Threat Intelligence Feed | No threat intelligence feeds (OSINT, ISACs, or commercial feeds) are configured. The lab operates without awareness of emerging threats or indicators of compromise. | NIST CSF Gap (ID.RA-02) | Identify | 2 | 2 | 4 | LOW | Gaurav Koshti | Open |

---

## Risk Summary Dashboard

| Risk Level | Count | Risk IDs |
|------------|-------|----------|
| CRITICAL | 1 | RSK-001 |
| HIGH | 6 | RSK-002, RSK-003, RSK-004, RSK-005, RSK-007, RSK-009 |
| MEDIUM | 2 | RSK-006, RSK-008 |
| LOW | 1 | RSK-010 |
| **TOTAL** | **10** | |

---

## Risk by CSF Function

| CSF Function | Risk Count | Highest Risk |
|--------------|------------|--------------|
| Govern | 1 | RSK-005 (HIGH) |
| Identify | 1 | RSK-010 (LOW) |
| Protect | 4 | RSK-001 (CRITICAL) |
| Detect | 1 | RSK-009 (HIGH) |
| Respond | 1 | RSK-002 (HIGH) |
| Recover | 1 | RSK-003 (HIGH) |

---

## Nessus Scan Integration Note

Risk RSK-004 (Unpatched Vulnerabilities) is sourced directly from Nessus Essentials scan results conducted as part of the Nessus Vulnerability Management Lab project. Key findings that fed into this risk include:

- Medium and High severity CVEs identified on Windows 11 endpoint (10.0.2.122)
- Missing Windows security updates flagged by Nessus plugin checks
- SMB and RDP-related vulnerabilities identified during authenticated scan

Full Nessus findings are documented in the Nessus_Vuln_Management_Lab repository.

---

*This risk register was created as part of the NIST CSF 2.0 GRC Risk Assessment Lab project. Risks will be tracked through remediation. Last updated: April 2026.*
