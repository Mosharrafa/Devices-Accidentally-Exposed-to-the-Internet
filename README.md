# Devices-Accidentally-Exposed-to-the-Internet
Azure Security Investigation using Microsoft Defender for Endpoint &amp; Microsoft Sentinel


## Overview
In this project, I simulate a common real-world security incident where an internal device is unintentionally exposed to the public internet.

After exposure, automated internet scanners discover the open service and begin authentication attempts against the system.  
The activity generates security telemetry which is then investigated using Microsoft security tools.

This project follows a real Security Operations Center (SOC) workflow.

---

## What Happens in This Scenario
A Windows virtual machine (**MDE-TEST-2**) is deployed in Azure.

Due to a misconfiguration:
- Remote Desktop (RDP) is publicly accessible
- The machine becomes visible to the internet
- Attackers begin password guessing attempts

The objective is to detect, analyze, and respond to the activity before compromise.

---

## Tools Used
- Azure Virtual Machine
- Network Security Groups (NSG)
- Microsoft Defender for Endpoint (EDR)
- Microsoft Sentinel (SIEM)
- Log Analytics Workspace
- Kusto Query Language (KQL)

---

## Investigation Goals
This lab demonstrates how a security analyst:

- Identifies exposed services
- Detects suspicious login attempts
- Tracks attacker IP addresses
- Hunts activity using logs
- Determines if compromise occurred
- Secures the system

---

## Workflow
Exposure → Discovery → Attack Attempts → Detection → Investigation → Containment → Hardening → Reporting

---

## Why This Matters
Publicly exposed RDP is one of the most frequent causes of enterprise breaches and ransomware incidents.

This project shows how defenders detect early attack indicators and respond before damage occurs.

---

## Skills Demonstrated
- Threat detection
- Log analysis
- KQL hunting
- Incident response
- Security hardening
- Microsoft security ecosystem usage
