# A6 Successful Login Verification

## Objective
Determine whether any of the identified attacker IP addresses successfully authenticated to the system.

## Method
A query was executed to search for successful authentication events originating from previously identified brute-force source IP addresses.

## Query
```kql
let attackers = dynamic(["10.0.8.6","142.163.17.228","10.0.8.8"]);

DeviceLogonEvents
| where DeviceName =~ "mde-test-2"
| where RemoteIP in (attackers)
| where ActionType == "LogonSuccess"
| project Timestamp, DeviceName, AccountName, RemoteIP, LogonType
| order by Timestamp desc
```

## Evidence

<img width="1438" height="705" alt="image" src="https://github.com/user-attachments/assets/d4b5dd43-7901-4008-84ba-1a4cd2f2de31" />
