# Asset Inventory
## GRC Risk Assessment Lab — Home Lab Environment

**Document Version:** 1.0
**Assessment Date:** April 2026
**Prepared By:** Gaurav Koshti
**Framework Reference:** NIST CSF 2.0 — Identify (ID.AM)

---

## 1. Overview

This document provides a complete inventory of all assets within the home lab environment used for the GRC Risk Assessment. The asset inventory forms the foundation of the risk assessment process and aligns with the NIST CSF 2.0 Identify function, specifically asset management controls ID.AM-1 (Physical devices and systems are inventoried) and ID.AM-2 (Software platforms and applications are inventoried).

---

## 2. Hardware Assets

| Asset ID | Asset Name | Type | Host Platform | Purpose |
|----------|------------|------|----------------|---------|
| HW-001 | Physical Workstation | Desktop/Laptop | Physical | VirtualBox Hypervisor Host |

---

## 3. Virtual Machine Inventory

| Asset ID | Hostname | OS | IP Address | Role | Network |
|----------|----------|----|------------|------|---------|
| VM-001 | WinServer2019 | Windows Server 2019 | 10.0.2.15 | Wazuh SIEM Manager / Security Monitoring | LabNetwork (NAT) |
| VM-002 | Win11-Endpoint | Windows 11 Pro | 10.0.2.122 | Wazuh Agent / Monitored Endpoint / Scan Target | LabNetwork (NAT) |
| VM-003 | Kali-Attacker | Kali Linux (Rolling) | 10.0.2.x (DHCP) | Attacker Simulation / Penetration Testing | LabNetwork (NAT) |

---

## 4. Software and Services Inventory

| Asset ID | Software | Version | Installed On | Purpose | Licensing |
|----------|----------|---------|--------------|---------|-----------|
| SW-001 | Oracle VirtualBox | 7.x | Physical Host | Hypervisor / VM Management | Free |
| SW-002 | Wazuh Manager | 4.x | VM-001 | SIEM - Log collection, alerting, compliance | Open Source |
| SW-003 | Wazuh Agent | 4.x | VM-002 | Endpoint monitoring, log forwarding | Open Source |
| SW-004 | Nessus Essentials | Latest | VM-001 | Vulnerability scanning | Free (16 IPs) |
| SW-005 | Windows Defender | Built-in | VM-002 | Endpoint antivirus / EDR | Included with OS |
| SW-006 | Kali Linux Toolset | Rolling | VM-003 | Offensive security tools (nmap, Metasploit, Hydra, etc.) | Open Source |

---

## 5. Network Inventory

| Asset ID | Component | Type | Subnet | DHCP | Notes |
|----------|-----------|------|--------|------|-------|
| NET-001 | LabNetwork | VirtualBox NAT Network | 10.0.2.0/24 | Enabled | Internal lab network, no direct internet exposure |

---

## 6. Data Assets

| Asset ID | Data Type | Location | Sensitivity | Notes |
|----------|-----------|----------|-------------|-------|
| DA-001 | Security Logs (Wazuh) | VM-001 | Internal | SIEM alert logs, event data |
| DA-002 | Vulnerability Scan Reports | VM-001 | Internal | Nessus scan outputs |
| DA-003 | Lab Documentation | GitHub (Public) | Public | Project write-ups, no sensitive data |
| DA-004 | VM Snapshots | Physical Host | Internal | Lab state backups |

---

## 7. Asset Classification Summary

| Classification | Count | Assets |
|----------------|-------|--------|
| Critical | 1 | VM-001 (Wazuh Manager - security monitoring hub) |
| High | 1 | VM-002 (Monitored Endpoint - agent and scan target) |
| Medium | 1 | VM-003 (Kali Attacker - isolated attack simulation) |
| Low | 1 | Physical Host (Hypervisor) |

---

## 8. Asset Owner

| Role | Name | Responsibility |
|------|------|----------------|
| Lab Owner / Administrator | Gaurav Koshti | All assets - provisioning, monitoring, maintenance |

---

*This inventory was created as part of the NIST CSF 2.0 GRC Risk Assessment Lab project. Last updated: April 2026.*
