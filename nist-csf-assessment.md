# NIST CSF 2.0 Self-Assessment
## GRC Risk Assessment Lab — Home Lab Environment

**Document Version:** 1.0
**Assessment Date:** April 2026
**Prepared By:** Gaurav Koshti
**Framework:** NIST Cybersecurity Framework (CSF) 2.0
**Scope:** Home lab environment (VirtualBox — 3 VMs)

---

## Scoring Key

| Score | Status | Description |
|-------|--------|-------------|
| 2 | Met | Control fully implemented and documented |
| 1 | Partial | Control partially implemented or informally in place |
| 0 | Not Met | Control not implemented |

**Max Score: 2 per control**

---

## Function 1: GOVERN (GV)

*Establishes and monitors the organization's cybersecurity risk management strategy, expectations, and policy.*

| Control ID | Control Description | Status | Score | Evidence / Notes |
|------------|---------------------|--------|-------|-----------------|
| GV.OC-01 | Organizational mission and cybersecurity objectives are established | Partial | 1 | Informal — lab purpose defined but no written policy |
| GV.OC-02 | Stakeholders and their roles are identified | Partial | 1 | Single owner (Gaurav Koshti) — no formal RACI |
| GV.RM-01 | Risk management objectives are established and agreed upon | Not Met | 0 | No formal risk management policy documented |
| GV.RM-02 | Risk appetite and risk tolerance are established and communicated | Not Met | 0 | Not formally defined |
| GV.PO-01 | Policy for managing cybersecurity risks is established | Not Met | 0 | No written security policy exists for the lab |
| GV.RR-01 | Roles and responsibilities for cybersecurity risk management are established | Partial | 1 | Single admin role — not formally documented |

**Govern Subtotal: 3 / 12**

---

## Function 2: IDENTIFY (ID)

*Helps the organization understand its current cybersecurity risk to systems, people, assets, data, and capabilities.*

| Control ID | Control Description | Status | Score | Evidence / Notes |
|------------|---------------------|--------|-------|-----------------|
| ID.AM-01 | Inventories of hardware managed by the organization are maintained | Met | 2 | asset-inventory.md documents all VMs and hardware |
| ID.AM-02 | Inventories of software managed by the organization are maintained | Met | 2 | Software inventory documented in asset-inventory.md |
| ID.AM-03 | Representations of the organization's authorized network communication are maintained | Partial | 1 | NAT network topology documented; no formal network diagram tool used |
| ID.AM-07 | Inventories of data and corresponding metadata are maintained | Partial | 1 | Data assets listed in asset-inventory.md; no formal data classification policy |
| ID.RA-01 | Vulnerabilities in assets are identified, validated, and recorded | Met | 2 | Nessus Essentials scans conducted; findings documented in Nessus_Vuln_Management_Lab |
| ID.RA-02 | Cyber threat intelligence is received from information sharing forums | Not Met | 0 | No threat intel feeds configured |
| ID.RA-05 | Threats, vulnerabilities, likelihoods, and impacts are used to understand inherent risk | Partial | 1 | Nessus CVSS scores reviewed; no formal risk matrix applied prior to this assessment |
| ID.IM-01 | Improvements are identified from evaluations | Partial | 1 | Improvement actions noted post-Nessus scan; no formal tracking process |

**Identify Subtotal: 10 / 16**

---

## Function 3: PROTECT (PR)

*Supports the ability to limit or contain the impact of a cybersecurity event.*

| Control ID | Control Description | Status | Score | Evidence / Notes |
|------------|---------------------|--------|-------|-----------------|
| PR.AA-01 | Identities and credentials are issued, managed, revoked, and audited for authorized users | Partial | 1 | Local accounts used; no centralized identity management (no Active Directory configured) |
| PR.AA-02 | Identities are proofed and bound to credentials based on context | Not Met | 0 | No MFA configured on any VM |
| PR.AA-05 | Access permissions and authorizations are managed incorporating least privilege | Partial | 1 | Admin accounts used for most tasks; no least-privilege model enforced |
| PR.AT-01 | Personnel are provided with awareness and training so that they possess knowledge to perform tasks | Not Met | 0 | No formal security awareness training program (single-person lab) |
| PR.DS-01 | The confidentiality, integrity, and availability of data-at-rest are protected | Not Met | 0 | Disk encryption not enabled on VMs |
| PR.DS-02 | The confidentiality, integrity, and availability of data-in-transit are protected | Partial | 1 | Wazuh agent-manager communication is encrypted; other traffic not verified |
| PR.IR-01 | Networks and environments are protected from unauthorized logical access | Partial | 1 | VMs isolated on NAT network; no host-based firewall rules formally configured |
| PR.PS-01 | Configuration management practices are established and applied | Not Met | 0 | No formal baseline configuration or hardening standard applied |
| PR.PS-02 | Software is maintained, replaced, and removed commensurate with risk | Partial | 1 | Windows Update enabled; no formal patch management policy or schedule |
| PR.PS-04 | Log records are created and stored internally and externally | Met | 2 | Wazuh SIEM collecting and storing logs from Win11 endpoint |

**Protect Subtotal: 7 / 20**

---

## Function 4: DETECT (DE)

*Enables timely discovery and analysis of anomalies, indicators of compromise, and other potentially adverse cybersecurity events.*

| Control ID | Control Description | Status | Score | Evidence / Notes |
|------------|---------------------|--------|-------|-----------------|
| DE.AE-02 | Potentially adverse events are analyzed to better characterize the events | Partial | 1 | Wazuh alerts reviewed manually; no automated correlation or playbooks |
| DE.AE-03 | Information is correlated from multiple sources | Partial | 1 | Wazuh aggregates logs from Win11 endpoint; Kali attack events mapped to alerts |
| DE.AE-06 | Information on adverse events is provided to authorized staff and tools | Partial | 1 | Wazuh dashboard reviewed by lab owner; no alerting/notification configured |
| DE.CM-01 | Networks are monitored to find potentially adverse events | Partial | 1 | Wazuh network monitoring active; no dedicated IDS/IPS in place |
| DE.CM-03 | Personnel activity and technology usage are monitored to find potentially adverse events | Met | 2 | Wazuh agent monitors Win11 endpoint — logon events, process creation, file changes |
| DE.CM-06 | External service provider activities are monitored to find potentially adverse events | Not Met | 0 | No external service providers in scope |

**Detect Subtotal: 6 / 12**

---

## Function 5: RESPOND (RS)

*Supports the ability to contain the impact of a cybersecurity incident.*

| Control ID | Control Description | Status | Score | Evidence / Notes |
|------------|---------------------|--------|-------|-----------------|
| RS.MA-01 | The incident response plan is executed in coordination with relevant third parties | Not Met | 0 | No formal incident response plan documented |
| RS.MA-02 | Incidents are triaged to determine the appropriate response | Partial | 1 | Wazuh alerts reviewed and triaged manually during SIEM lab exercises |
| RS.AN-03 | Analysis is performed to establish what has occurred during an incident | Partial | 1 | Log analysis performed during Wazuh attack simulations |
| RS.CO-02 | Internal and external stakeholders are notified of incidents | Not Met | 0 | No notification process defined |
| RS.MI-01 | Incidents are contained | Partial | 1 | Manual containment possible (VM isolation); no documented procedure |

**Respond Subtotal: 3 / 10**

---

## Function 6: RECOVER (RC)

*Supports timely restoration of normal operations to reduce the impact of a cybersecurity incident.*

| Control ID | Control Description | Status | Score | Evidence / Notes |
|------------|---------------------|--------|-------|-----------------|
| RC.RP-01 | The recovery portion of the incident response plan is executed | Not Met | 0 | No recovery plan documented |
| RC.RP-02 | Recovery actions are selected, scoped, prioritized, and performed | Not Met | 0 | No formal recovery procedure |
| RC.RP-05 | The integrity of backups and other restoration assets is verified | Not Met | 0 | VM snapshots taken informally; no backup verification process |
| RC.CO-03 | Recovery activities and progress in restoring normal operations are communicated | Not Met | 0 | No communication plan for recovery |

**Recover Subtotal: 0 / 8**

---

## Overall Assessment Summary

| Function | Score | Max | Percentage | Maturity Level |
|----------|-------|-----|------------|----------------|
| Govern | 3 | 12 | 25% | Initial |
| Identify | 10 | 16 | 63% | Developing |
| Protect | 7 | 20 | 35% | Initial |
| Detect | 6 | 12 | 50% | Developing |
| Respond | 3 | 10 | 30% | Initial |
| Recover | 0 | 8 | 0% | Not Started |
| **TOTAL** | **29** | **78** | **37%** | **Initial** |

---

## Risk Heatmap Summary

| Priority | Function | Key Gap |
|----------|----------|---------|
| CRITICAL | Recover | No recovery plan, no verified backups |
| CRITICAL | Govern | No written security policy or risk appetite defined |
| HIGH | Protect | No MFA, no disk encryption, no hardening baseline |
| HIGH | Respond | No incident response plan |
| MEDIUM | Detect | No automated alerting or IDS/IPS |
| LOW | Identify | No threat intel feeds |

---

## Maturity Scale Reference

| Level | Description |
|-------|-------------|
| Not Started | 0-10% — Controls absent |
| Initial | 11-40% — Ad hoc, undocumented |
| Developing | 41-70% — Partially implemented |
| Defined | 71-85% — Documented and consistent |
| Managed | 86-95% — Measured and monitored |
| Optimized | 96-100% — Continuously improving |

---

*Assessment conducted as part of the NIST CSF 2.0 GRC Risk Assessment Lab project. Findings feed directly into the risk register and remediation plan. Last updated: April 2026.*
