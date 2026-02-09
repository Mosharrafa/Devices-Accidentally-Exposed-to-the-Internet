# Devices Accidentally Exposed to the Internet
Azure Security Investigation using Microsoft Defender for Endpoint &amp; Microsoft Sentinel


## Scenario
An Azure virtual machine was unintentionally exposed to the public internet via RDP (TCP/3389).  
External attackers discovered the service and began authentication attempts.

## Goal
Investigate the activity using Microsoft Defender for Endpoint and Microsoft Sentinel and determine whether the system was compromised.

## Tools Used
- Azure VM
- Network Security Groups
- Microsoft Defender for Endpoint
- Microsoft Sentinel
- Log Analytics / KQL

## Investigation Flow
1. Confirm exposure
2. Generate attack attempts
3. Analyze security logs
4. Identify attacker behavior
5. Contain access
6. Harden system
7. Document incident

## Skills Demonstrated
Threat detection, log analysis, incident response, and security hardening using Microsoft security stack.

