# A7 Relating the Activity to MITRE ATT&CK

## What actually happened
After the VM became reachable from the public internet, it did not stay quiet for long.  
Within a short time, authentication attempts started coming in from multiple remote addresses.

The behavior had some clear characteristics:

- The same few usernames were tried again and again
- Attempts came in quick bursts, then paused, then started again
- Different IP addresses were doing the same thing
- No real interactive session ever followed the attempts

This did not look like a person typing a password wrong.  
It looked like something automatically testing credentials.

## How I interpreted it
Before someone can log in, they first have to *find* the service.  
So the activity likely followed this order:

1. The internet scanned and discovered an exposed RDP port
2. Automated tools started trying common usernames and passwords
3. The attempts failed and stopped there

Since we never observed a successful login, the activity never moved past the access attempt phase.

## ATT&CK Mapping
```
Reconnaissance     - T1595  Active Scanning
Discovery          - T1046  Network Service Discovery
Initial Access     - T1110  Brute Force
Credential Access  - T1110.001  Password Guessing
```

## Why these mappings make sense
The service had to be discovered first → that matches scanning behavior.  
Once discovered, repeated authentication attempts began → that matches brute force and password guessing.  
Because the attacker never gained access, later stages like persistence or lateral movement never occurred.

## Analyst Takeaway
The system was exposed and automatically probed by opportunistic attackers on the internet.  
However, the protection controls (authentication failure) prevented the activity from turning into a real compromise.
