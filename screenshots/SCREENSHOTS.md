# Screenshots — Control Evidence

This folder contains screenshots documenting the implementation of 4 compensating controls remediated during the GRC Risk Assessment Lab project.

## Control Evidence Files

### 1. account-lockout-policy.png
**Risk Addressed:** RSK-007 — No Account Lockout Policy  
**Control:** Account Lockout Policy Configuration  
**Evidence:** Group Policy Management Editor showing:
- Account lockout threshold: 5 invalid logon attempts
- Account lockout duration: 30 minutes  
- Reset account lockout counter after: 15 minutes

**Date Implemented:** April 2026  
**Status:** ✅ Implemented

---

### 2. firewall-enabled.png
**Risk Addressed:** RSK-008 — No Hardening Baseline Applied  
**Control:** Windows Defender Firewall Enabled  
**Evidence:** Windows Defender Firewall with Advanced Security showing:
- Domain Profile: Firewall State = On
- Private Profile: Firewall State = On
- Public Profile: Firewall State = On

**Date Implemented:** April 2026  
**Status:** ✅ Implemented

---

### 3. audit-logging-enabled.png
**Risk Addressed:** RSK-001 — No MFA on Administrative Accounts (Compensating Control)  
**Control:** Audit Logging Enabled  
**Evidence:** Local Security Policy — Audit Policy showing:
- Audit logon events: Success, Failure
- Audit policy change: Success, Failure

**Date Implemented:** April 2026  
**Status:** ✅ Implemented

---

### 4. guest-account-disabled.png
**Risk Addressed:** RSK-008 — No Hardening Baseline Applied  
**Control:** Guest Account Disabled  
**Evidence:** Local Users and Groups showing Guest account with disabled icon and properties dialog confirming "Account is disabled" checkbox.

**Date Implemented:** April 2026  
**Status:** ✅ Implemented

---

## Summary

All 4 compensating controls were successfully implemented in the lab environment with evidence captured. These controls address 4 of the 10 identified risks and demonstrate practical security hardening skills.

**Controls Implemented:** 4 / 10 risks addressed  
**Risks Remaining:** 6 high-priority items requiring additional remediation (documented in remediation-plan.md)

---

*Screenshots captured during GRC Risk Assessment Lab project — April 2026*
