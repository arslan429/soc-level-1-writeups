# Incident Investigation

## Overview

Incident investigation is the process of analyzing a suspected security event to determine what happened, how it happened, which systems were affected, and what actions should be taken.

A SOC analyst uses logs, alerts, endpoint data, network activity, and other evidence to build an accurate timeline of the incident.

## Investigation Process

A basic incident investigation follows these stages:

1. **Detection** — Identify a suspicious alert or security event.
2. **Validation** — Determine whether the alert represents a genuine security incident.
3. **Scoping** — Identify affected users, hosts, accounts, and systems.
4. **Evidence Collection** — Gather relevant logs and endpoint/network data.
5. **Timeline Analysis** — Establish the sequence of attacker activity.
6. **Containment** — Limit the attacker's access and prevent further damage.
7. **Remediation** — Remove malicious artifacts and fix the underlying issue.
8. **Recovery** — Restore affected systems and monitor for further activity.
9. **Documentation** — Record findings, actions, and lessons learned.

## Evidence Sources

Important sources for SOC investigations include:

* Windows Event Logs
* Linux system logs
* Authentication logs
* Firewall logs
* DNS logs
* Proxy logs
* Endpoint Detection and Response (EDR) telemetry
* Network traffic
* Email security logs
* Antivirus alerts

## Important Windows Events

| Event ID | Description                                    |
| -------- | ---------------------------------------------- |
| 4624     | Successful logon                               |
| 4625     | Failed logon                                   |
| 4688     | New process created                            |
| 4698     | Scheduled task created                         |
| 4720     | User account created                           |
| 4732     | Member added to a security-enabled local group |
| 7045     | New service installed                          |

## Timeline Analysis

Creating a timeline helps investigators understand the attack sequence.

A typical timeline may include:

* Initial suspicious login
* Malicious file execution
* Persistence activity
* Credential access
* Command and control communication
* Lateral movement
* Data access or collection
* Containment actions

Correlating timestamps from multiple log sources can reveal the complete attack chain.

## Indicators of Compromise

During an investigation, analysts may search for:

* Suspicious IP addresses
* Malicious domains
* File hashes
* Unusual processes
* Suspicious PowerShell commands
* Unexpected user accounts
* Abnormal authentication activity
* Persistence mechanisms
* Unusual network connections

## SOC Response

After confirming an incident, the SOC should:

* Isolate affected systems when necessary
* Disable or reset compromised accounts
* Block malicious IPs and domains
* Remove malicious files or persistence mechanisms
* Preserve relevant evidence
* Search for additional affected systems
* Monitor for recurring activity
* Document all investigation and response actions

## Key Takeaway

Effective incident investigation requires a structured approach. By validating alerts, collecting evidence, building timelines, correlating events, and documenting findings, SOC analysts can determine the scope and impact of an incident and support effective containment and remediation.
