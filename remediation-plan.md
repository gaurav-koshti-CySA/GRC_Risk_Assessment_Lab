# Remediation Plan
## GRC Risk Assessment Lab — Home Lab Environment

**Document Version:** 1.0
**Date:** April 2026
**Prepared By:** Gaurav Koshti
**Framework Reference:** NIST CSF 2.0
**Source:** Risk Register (risk-register.md)

---

## Overview

This remediation plan outlines the actions required to address the risks identified in the GRC Risk Assessment. Items are prioritized by risk score (highest first). Each item includes the remediation action, implementation steps, effort estimate, and current status.

Controls marked as **Implemented** have been applied to the lab environment during this assessment with evidence captured in the screenshots/ folder.

---

## Priority 1 — CRITICAL Risk Remediations

### RSK-001 | No MFA on Administrative Accounts
**Risk Score:** 20 (CRITICAL) | **CSF Control:** PR.AA-02

**Remediation Action:** Enable Windows Hello for Business or configure a local MFA solution on all administrative accounts.

**Implementation Steps:**
1. Enable Windows Hello PIN on Windows 11 endpoint as a secondary authentication factor
2. Configure account lockout policy as a compensating control (see RSK-007)
3. Document MFA enforcement policy

**Effort:** Medium (2-3 hours)
**Priority:** P1
**Target Date:** Week 1
**Status:** Partially Mitigated — Account lockout policy implemented as compensating control

---

## Priority 2 — HIGH Risk Remediations

### RSK-002 | No Incident Response Plan
**Risk Score:** 15 (HIGH) | **CSF Control:** RS.MA-01

**Remediation Action:** Create a basic Incident Response Plan (IRP) tailored to the home lab environment.

**Implementation Steps:**
1. Draft IRP covering: Preparation, Detection, Containment, Eradication, Recovery, Lessons Learned
2. Define roles and responsibilities (single owner — Gaurav Koshti)
3. Document escalation procedures
4. Include Wazuh alert triage process

**Effort:** Medium (3-4 hours)
**Priority:** P2
**Target Date:** Week 1
**Status:** Planned

---

### RSK-003 | No Data Recovery Plan or Verified Backups
**Risk Score:** 15 (HIGH) | **CSF Control:** RC.RP-01, RC.RP-05

**Remediation Action:** Establish a formal backup policy and verify VM snapshot restoration integrity.

**Implementation Steps:**
1. Document backup policy: what is backed up, frequency, retention period
2. Take VM snapshots of all three VMs
3. Test restoration of Win11 snapshot — document result
4. Create recovery runbook

**Effort:** Medium (2-3 hours)
**Priority:** P2
**Target Date:** Week 1
**Status:** Planned

---

### RSK-004 | Unpatched Vulnerabilities on Endpoints
**Risk Score:** 16 (HIGH) | **CSF Control:** PR.PS-02 | **Source:** Nessus Scan

**Remediation Action:** Apply all outstanding Windows security updates on Win11 endpoint and establish a patch management schedule.

**Implementation Steps:**
1. Run Windows Update on Win11 endpoint (10.0.2.122) — install all pending updates
2. Re-run Nessus scan post-patching to verify remediation
3. Document patch management schedule: monthly patching cycle
4. Compare pre/post scan results

**Effort:** Low-Medium (1-2 hours + scan time)
**Priority:** P2
**Target Date:** Week 1
**Status:** Planned

---

### RSK-005 | No Written Security Policy
**Risk Score:** 15 (HIGH) | **CSF Control:** GV.PO-01

**Remediation Action:** Create a simple Lab Security Policy document covering acceptable use, access control, patching, and incident handling.

**Implementation Steps:**
1. Draft security policy with sections: Purpose, Scope, Asset Management, Access Control, Patch Management, Incident Response, Review Cycle
2. Store policy in GitHub repo
3. Set annual review date

**Effort:** Medium (2-3 hours)
**Priority:** P2
**Target Date:** Week 2
**Status:** Planned

---

### RSK-007 | No Account Lockout Policy Configured
**Risk Score:** 12 (HIGH) | **CSF Control:** PR.AA-01

**Remediation Action:** Configure account lockout policy via Group Policy on Windows Server 2019 and local policy on Windows 11.

**Implementation Steps:**
1. Open Group Policy Management on Windows Server 2019
2. Navigate to: Computer Configuration > Windows Settings > Security Settings > Account Policies > Account Lockout Policy
3. Set: Account lockout threshold = 5 invalid attempts
4. Set: Account lockout duration = 30 minutes
5. Set: Reset account lockout counter after = 15 minutes
6. Apply policy and verify via gpupdate /force
7. Test lockout by entering wrong credentials 5 times
8. Screenshot before and after configuration

**Effort:** Low (30-45 minutes)
**Priority:** P2
**Target Date:** Week 1
**Status:** ✅ IMPLEMENTED — Evidence in screenshots/account-lockout-policy.png

---

### RSK-009 | No Automated Alerting or Notification
**Risk Score:** 12 (HIGH) | **CSF Control:** DE.AE-06

**Remediation Action:** Configure Wazuh email or webhook notifications for critical and high severity alerts.

**Implementation Steps:**
1. Configure Wazuh Manager SMTP settings for email alerting
2. Set alert threshold: notify on Level 10+ alerts
3. Test alert delivery by triggering a brute force simulation from Kali
4. Document alert notification configuration

**Effort:** Medium (2-3 hours)
**Priority:** P2
**Target Date:** Week 2
**Status:** Planned

---

## Priority 3 — MEDIUM Risk Remediations

### RSK-006 | Disk Encryption Not Enabled
**Risk Score:** 8 (MEDIUM) | **CSF Control:** PR.DS-01

**Remediation Action:** Enable BitLocker on Windows VMs or use VirtualBox disk encryption.

**Implementation Steps:**
1. Enable BitLocker on Windows 11 VM (requires TPM or startup key)
2. Store recovery key securely
3. Document encryption status

**Effort:** Medium (1-2 hours)
**Priority:** P3
**Target Date:** Week 2
**Status:** Planned

---

### RSK-008 | No Hardening Baseline Applied
**Risk Score:** 9 (MEDIUM) | **CSF Control:** PR.PS-01

**Remediation Action:** Apply CIS Benchmark Level 1 hardening controls to Windows 11 endpoint.

**Implementation Steps:**
1. Download CIS Benchmark for Windows 11
2. Apply key controls: disable unnecessary services, enable Windows Firewall, configure audit policies
3. Enable Windows Firewall on all VM profiles (Domain, Private, Public)
4. Disable Guest account
5. Disable Remote Registry service
6. Screenshot before/after firewall status

**Effort:** Medium-High (3-4 hours)
**Priority:** P3
**Target Date:** Week 2
**Status:** Partially Implemented — Windows Firewall enabled. Evidence in screenshots/firewall-enabled.png

---

## Priority 4 — LOW Risk Remediations

### RSK-010 | No Threat Intelligence Feed
**Risk Score:** 4 (LOW) | **CSF Control:** ID.RA-02

**Remediation Action:** Subscribe to free OSINT threat intelligence feeds and configure Wazuh integration.

**Implementation Steps:**
1. Subscribe to AlienVault OTX free feed
2. Configure Wazuh to ingest threat intel IOCs
3. Document feed sources

**Effort:** Low (1 hour)
**Priority:** P4
**Target Date:** Week 3
**Status:** Planned

---

## Implemented Controls — Evidence Summary

The following controls were implemented during this GRC assessment and are evidenced by screenshots:

| Control | Risk ID | Action Taken | Evidence File |
|---------|---------|--------------|---------------|
| Account Lockout Policy | RSK-007 | Configured via Group Policy — 5 attempts, 30 min lockout | screenshots/account-lockout-policy.png |
| Windows Firewall Enabled | RSK-008 | Enabled all profiles on Win11 endpoint | screenshots/firewall-enabled.png |
| Audit Logging Enabled | RSK-001 | Enabled Logon Events and Policy Change auditing | screenshots/audit-logging-enabled.png |
| Guest Account Disabled | RSK-008 | Disabled via Local Users and Groups | screenshots/guest-account-disabled.png |

---

## Remediation Tracking Summary

| Risk ID | Risk Level | Status | Week |
|---------|------------|--------|------|
| RSK-001 | CRITICAL | Partially Mitigated | W1 |
| RSK-004 | HIGH | Planned | W1 |
| RSK-002 | HIGH | Planned | W1 |
| RSK-003 | HIGH | Planned | W1 |
| RSK-007 | HIGH | Implemented | W1 |
| RSK-005 | HIGH | Planned | W2 |
| RSK-009 | HIGH | Planned | W2 |
| RSK-008 | MEDIUM | Partially Implemented | W2 |
| RSK-006 | MEDIUM | Planned | W2 |
| RSK-010 | LOW | Planned | W3 |

---

*This remediation plan will be updated as controls are implemented. Last updated: April 2026.*
