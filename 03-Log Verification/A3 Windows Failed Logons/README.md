# A3 Windows Failed Logon Events

## Objective
Verify that failed authentication attempts were recorded by the operating system after exposing RDP and performing login attempts.

## Observation
Within Windows Event Viewer > Windows Logs > Security,  
multiple Event ID 4625 entries were observed.

These events indicate unsuccessful authentication attempts against the system.

## Interpretation
The presence of repeated failed logon events confirms that the machine is receiving external authentication attempts, consistent with brute-force behavior.

## Importance
These logs serve as the primary evidence source for later investigation in Microsoft Defender for Endpoint and Microsoft Sentinel.
