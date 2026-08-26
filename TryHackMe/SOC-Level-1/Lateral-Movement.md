# Lateral Movement Analysis

## Overview

Lateral movement is the phase of an attack where an adversary moves from one compromised system to another within a network. The goal is usually to access additional systems, obtain higher privileges, and reach valuable resources.

During SOC investigations, detecting lateral movement helps identify whether an attacker has expanded their access after the initial compromise.

## Common Techniques

* Remote Desktop Protocol (RDP)
* Server Message Block (SMB)
* Windows Remote Management (WinRM)
* PsExec and other remote service execution
* Remote PowerShell
* Pass-the-Hash
* Use of compromised administrative credentials

## Investigation Approach

When investigating suspected lateral movement, I would review:

1. Source and destination IP addresses
2. User accounts involved
3. Authentication events
4. Windows Security Event Logs
5. Remote logon activity
6. Process creation events
7. Network connections
8. Evidence of reused or compromised credentials

## Important Windows Events

| Event ID | Description                                |
| -------- | ------------------------------------------ |
| 4624     | Successful logon                           |
| 4625     | Failed logon                               |
| 4648     | Logon using explicit credentials           |
| 4672     | Special privileges assigned to a new logon |
| 4688     | New process created                        |
| 4776     | Domain controller authentication activity  |

## Indicators of Suspicious Activity

Examples of suspicious lateral movement include:

* A user logging into multiple systems within a short period
* Administrative accounts accessing unusual endpoints
* RDP connections from unexpected hosts
* Repeated failed logons followed by a successful login
* Remote execution tools being launched
* Authentication activity outside normal working patterns
* The same credentials being used across several systems

## SOC Response

A SOC analyst should correlate authentication, endpoint, and network telemetry to determine whether the activity is legitimate or malicious.

If malicious lateral movement is confirmed, recommended response actions include:

* Isolating affected endpoints
* Disabling or resetting compromised accounts
* Investigating other systems accessed by the account
* Reviewing authentication and process logs
* Searching for additional indicators of compromise
* Documenting the timeline and affected systems

## MITRE ATT&CK

Lateral movement can map to several MITRE ATT&CK techniques, including:

* **T1021 — Remote Services**
* **T1047 — Windows Management Instrumentation**
* **T1550.002 — Pass the Hash**
* **T1563 — Remote Service Session Hijacking**

## Key Takeaway

Lateral movement detection requires correlation of authentication logs, endpoint activity, network connections, and user behavior. Understanding these indicators helps SOC analysts determine whether an attacker has moved beyond the initially compromised system.
