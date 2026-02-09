# A8  Recommended Containment and Hardening Actions

## Context
This environment was intentionally left exposed for observation, so no permanent changes were applied during the investigation.

However, in a real environment the behavior would require immediate containment to prevent unauthorized access.

## Immediate Containment (EDR Level)
The first priority would be to reduce risk while preserving evidence.

Using Microsoft Defender for Endpoint, the device can be isolated from the network.  
This blocks all inbound and outbound communication except the management channel, allowing investigation to continue safely without giving the attacker further opportunity.

Purpose:
- Stop ongoing authentication attempts
- Prevent potential lateral movement
- Preserve forensic visibility

## Network Containment
The root cause of the activity was public exposure of RDP.

The exposed access path should be removed:
- Disable public RDP access
- Restrict remote administration to private network paths only
- Allow access only from trusted IP ranges or VPN

## Identity Protection
Even though no compromise occurred, repeated authentication attempts indicate credential risk.

Recommended protections:
- Enforce multi-factor authentication
- Disable or rename default accounts
- Apply account lockout policies

## Long-Term Hardening
To prevent recurrence:

- Avoid direct internet exposure of management services
- Use just-in-time access for administrative sessions
- Continuously monitor authentication anomalies
- Alert on abnormal login patterns

## Security Perspective
The incident demonstrates a common pattern:  
automated internet probing occurs quickly after exposure.

The most effective defense is reducing attack surface rather than reacting to individual login attempts.
