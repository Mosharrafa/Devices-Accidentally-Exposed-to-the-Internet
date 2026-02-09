# Generate Failed Login Attempts

## Purpose
To simulate external authentication attempts against the exposed RDP service in order to generate security log data for investigation.

## Method
Multiple login attempts were performed against the virtual machine using incorrect credentials.

## Expected Outcome
The system should record failed logon events, which will later be analyzed in Windows Event Viewer, Microsoft Defender for Endpoint, and Microsoft Sentinel.

## Why this matters
Without authentication failures, there would be no telemetry available for detection and hunting activities.
