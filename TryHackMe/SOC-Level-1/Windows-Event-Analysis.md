# Windows Event Analysis — SOC Level 1

## 1. Investigation Overview

This case study documents a simulated Windows event-log investigation performed as part of my SOC Level 1 hands-on training.

The objective was to review Windows security events, identify suspicious activity, correlate related events, and determine whether the activity could indicate an attempted compromise.

## 2. Investigation Objectives

The investigation focused on:

* Reviewing Windows Security event logs
* Identifying suspicious authentication activity
* Correlating multiple events by user, host, and time
* Investigating failed and successful logon activity
* Identifying potentially abnormal account behavior
* Understanding how Windows Event IDs support SOC investigations

## 3. Important Windows Event IDs

| Event ID | Description                 | SOC Relevance                                                  |
| -------- | --------------------------- | -------------------------------------------------------------- |
| 4624     | Successful logon            | Useful for identifying successful authentication               |
| 4625     | Failed logon                | Useful for detecting password guessing or brute-force activity |
| 4634     | Logoff                      | Helps establish user session timelines                         |
| 4672     | Special privileges assigned | May indicate privileged account activity                       |
| 4688     | Process creation            | Useful for investigating suspicious process execution          |
| 4720     | User account created        | Can indicate unauthorized account creation                     |
| 4740     | Account locked out          | Useful for detecting repeated authentication failures          |

## 4. Investigation Process

The investigation followed a basic SOC workflow:

1. Review the available Windows event logs.
2. Filter events by relevant Event IDs.
3. Establish a timeline of authentication and process activity.
4. Compare failed and successful logon events.
5. Identify unusual users, hosts, times, or processes.
6. Correlate related events.
7. Determine whether the activity appears benign or suspicious.
8. Document findings and recommended defensive actions.

## 5. Authentication Analysis

Failed authentication events can provide useful indicators during an investigation.

A high number of Event ID 4625 entries involving the same account may indicate password guessing or brute-force activity.

A useful investigation should compare:

* Username
* Source workstation or IP address
* Destination host
* Timestamp
* Logon type
* Number of failed attempts
* Whether a successful logon occurred afterward

A successful Event ID 4624 following multiple failed authentication attempts should receive additional investigation.

## 6. Process Creation Analysis

Event ID 4688 can provide visibility into processes created on a Windows system.

During investigation, analysts should examine:

* Process name
* Parent process
* Command-line information
* User account
* Creation time
* Executable location

Unexpected processes or unusual parent-child relationships may indicate suspicious activity and should be correlated with other available telemetry.

## 7. Timeline Analysis

A basic investigation timeline can be structured as follows:

**Authentication Failure → Successful Authentication → Process Creation → Additional System Activity**

Building a timeline helps determine whether separate events are related to the same activity.

The analyst should avoid treating a single event as proof of compromise. Multiple related indicators provide stronger evidence.

## 8. Detection Opportunities

Potential detection rules from this investigation include:

* Multiple failed logons against a single account
* Multiple accounts receiving authentication failures from the same source
* Successful authentication following repeated failures
* Privileged account activity outside expected conditions
* Unexpected account creation
* Suspicious process creation
* Unusual parent-child process relationships

## 9. MITRE ATT&CK Mapping

Relevant MITRE ATT&CK techniques may include:

* **T1110 — Brute Force**
* **T1078 — Valid Accounts**
* **T1059 — Command and Scripting Interpreter**
* **T1548 — Abuse Elevation Control Mechanism**

The exact technique mapping should be validated against the evidence available in the investigation.

## 10. Key Lessons Learned

This investigation reinforced several SOC fundamentals:

* Windows Event Logs are valuable sources of security telemetry.
* Individual events often need to be correlated with other events.
* Authentication activity should be analyzed using both failures and successes.
* Event IDs provide useful context but do not automatically prove malicious activity.
* Building a timeline makes incident investigation easier.
* Good documentation should clearly separate observed evidence from analyst conclusions.

## 11. Recommended Defensive Actions

For suspicious authentication activity:

* Review the affected account and source host.
* Check for additional successful logons.
* Review privileged activity.
* Investigate suspicious process creation.
* Consider account protection measures when appropriate.
* Continue monitoring related hosts and accounts.

## 12. Conclusion

Windows Event Analysis is an important SOC skill because event logs provide visibility into authentication, account, process, and system activity.

This exercise improved my ability to identify relevant Windows Event IDs, correlate events, build an investigation timeline, and document findings from a defensive security perspective.
