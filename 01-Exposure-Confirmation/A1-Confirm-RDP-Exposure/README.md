# A1 Confirm RDP Exposure

## Summary
The virtual machine **MDE-TEST-2** was reviewed to verify whether Remote Desktop (RDP) access was available from the public internet.

## Observation
In Azure Portal > Virtual Machines > MDE-TEST-2 >Networking,  
the inbound security rules showed that TCP port 3389 (RDP) was allowed from an external source.

## Result
Public RDP exposure: YES / NO

## Why this matters
Publicly exposed RDP services are frequently targeted by automated login attempts.  
Confirming this exposure ensures that authentication activity can be observed and analyzed in later investigation steps.
