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


## Additional Findings

### Targeted Accounts
Analysis of failed authentication events shows that the activity primarily targeted commonly used and default account names such as administrative and generic user accounts.  
This behavior is typical of automated brute-force tools that attempt widely known usernames in order to gain initial access without prior knowledge of the environment.

<img width="1497" height="848" alt="image" src="https://github.com/user-attachments/assets/75df62c5-97db-4c30-86e3-2c9634d7c9d7" />

<br>



### Attacker Sources
Multiple distinct remote IP addresses were observed generating repeated failed logon attempts against the same device.  
The presence of several sources indicates distributed scanning activity rather than a single manual attacker session.

<img width="1537" height="802" alt="image" src="https://github.com/user-attachments/assets/de67facf-a4c0-4e36-b1e4-6a3061d9ab0e" />

<br>



### Geographic Pattern
The originating IP addresses mapped to different geographic regions.  
This pattern is consistent with internet-wide scanning infrastructure and botnet-driven authentication attempts, rather than targeted human interaction.

<img width="1575" height="587" alt="image" src="https://github.com/user-attachments/assets/d7cb894c-81de-45a8-897b-650f65f6a73b" />


<br>


### Behavioral Pattern
Failed logon attempts did not occur at a constant rate.  
Instead, they appeared in short bursts followed by idle periods.

For example, several authentication attempts were generated within a single 5-minute interval, followed by inactivity and then another burst of activity.
This pattern is consistent with automated retry logic used by scanning or brute-force tools rather than normal user interaction.

<img width="1362" height="598" alt="image" src="https://github.com/user-attachments/assets/1d16d6b3-02e1-4b6b-97d6-1a7db2480d32" />

<br>

### Conclusion
The combined evidence (repeated failures, multiple source IPs, common username targeting, and burst timing) confirms that the device was subjected to automated RDP brute-force probing after being exposed to the public internet.

<img width="1487" height="776" alt="image" src="https://github.com/user-attachments/assets/469e7807-ed41-4ce9-adaf-4d81519c8926" />

