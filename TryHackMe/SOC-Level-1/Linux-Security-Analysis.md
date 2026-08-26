# Linux Security Analysis — SOC Level 1

## 1. Investigation Overview

This case study documents a Linux security monitoring and investigation exercise completed as part of SOC Level 1 training.

The investigation focused on identifying suspicious activity through Linux logs, command execution, authentication events, and system activity.

## 2. Investigation Objectives

The main objectives were:

* Identify suspicious authentication activity
* Analyse Linux system logs
* Investigate unusual command execution
* Identify indicators of compromise
* Understand attacker behaviour
* Determine the potential impact of the activity
* Document relevant findings for incident response

## 3. Log Analysis

Linux systems generate several important logs that can help SOC analysts investigate security incidents.

Key sources considered during the investigation included:

* `/var/log/auth.log`
* `/var/log/syslog`
* `/var/log/secure`
* System and authentication events
* User login activity
* Process and command execution information

The investigation focused on identifying unusual login attempts, unexpected users, suspicious processes, and abnormal system activity.

## 4. Authentication Investigation

Authentication events were reviewed to identify:

* Failed login attempts
* Successful logins from unusual sources
* Repeated authentication failures
* Unexpected user activity
* Suspicious privilege usage

Repeated failed authentication attempts can indicate password guessing or brute-force activity, while unexpected successful authentication may require further investigation.

## 5. Suspicious Activity

During analysis, suspicious system activity was investigated by correlating authentication events with process and command execution information.

The investigation considered:

* User accounts involved
* Source of authentication attempts
* Time of activity
* Commands executed
* Processes running on the system
* Changes to system configuration

## 6. Investigation Approach

The investigation followed a basic SOC workflow:

1. Identify suspicious activity
2. Collect relevant logs
3. Establish a timeline
4. Correlate authentication and system events
5. Identify indicators of compromise
6. Assess potential impact
7. Document findings
8. Recommend defensive actions

## 7. Indicators of Compromise

Potential indicators considered during the investigation included:

* Suspicious IP addresses
* Unusual login times
* Unexpected user accounts
* Repeated failed authentication attempts
* Unusual processes
* Suspicious command execution
* Unexpected configuration changes

## 8. MITRE ATT&CK Mapping

Relevant techniques that may apply to Linux security investigations include:

* **T1078 — Valid Accounts**
* **T1110 — Brute Force**
* **T1059 — Command and Scripting Interpreter**
* **T1543 — Create or Modify System Process**
* **T1053 — Scheduled Task/Job**

The exact technique mapping depends on the evidence observed during the investigation.

## 9. Defensive Recommendations

Recommended defensive measures include:

* Monitor authentication logs continuously
* Use strong authentication policies
* Disable unnecessary accounts
* Apply least-privilege principles
* Monitor privileged commands
* Keep Linux systems patched
* Centralise logs in a SIEM
* Investigate repeated authentication failures
* Establish alerts for suspicious process activity

## 10. Lessons Learned

This investigation improved my understanding of Linux security monitoring and the importance of log correlation.

I learned that individual log entries may not provide enough context. A SOC analyst should correlate authentication events, timestamps, users, processes, commands, and system activity to build an accurate incident timeline.

## 11. Skills Demonstrated

* Linux security monitoring
* Log analysis
* Authentication investigation
* Incident investigation
* Threat detection
* Timeline analysis
* Indicator identification
* MITRE ATT&CK mapping
* SOC investigation methodology

## 12. Conclusion

This exercise strengthened my practical understanding of Linux security monitoring from a SOC analyst perspective.

The investigation demonstrated how Linux logs and system activity can be used to identify suspicious behaviour, investigate potential compromise, and support incident response.
