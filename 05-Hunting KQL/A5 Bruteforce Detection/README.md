# A5 Brute Force Hunting using KQL 

## Objective
Identify repeated failed logon activity consistent with brute-force attempts against the exposed machine.

## Data Source
DeviceLogonEvents (Microsoft Defender for Endpoint / Advanced Hunting)

## Query (Failed logons by remote IP)
```kql
DeviceLogonEvents
| where DeviceName == "mde-test-2"
| where LogonType has_any ("network", "Interactive", "RemoteInteractive", "Unlock")
| where ActionType == "LogonFailed"
| where isnotempty(RemoteIP)
| summarize Attempts = count() by ActionType, RemoteIP, DeviceName
| order by Attempts desc

```

<img width="1188" height="537" alt="image" src="https://github.com/user-attachments/assets/addb27c2-7847-435f-b8d9-98c511383d3a" />

<br>

<img width="1612" height="915" alt="image" src="https://github.com/user-attachments/assets/98396d00-dfaf-43e2-9ba1-e7c7bf910fd9" />

