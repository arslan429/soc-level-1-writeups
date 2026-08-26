# Threat Detection — SOC Level 1

## 1. Investigation Overview

This case study documents a threat detection exercise completed during SOC Level 1 training.

The objective was to understand how a SOC analyst identifies suspicious activity, analyses security alerts, correlates available evidence, and determines whether activity represents a potential security incident.

## 2. Detection Objectives

The investigation focused on:

* Identifying suspicious activity
* Analysing security alerts
* Correlating multiple events
* Investigating suspicious processes
* Reviewing authentication activity
* Identifying indicators of compromise
* Mapping activity to MITRE ATT&CK
* Determining appropriate response actions

## 3. Alert Investigation

The investigation began with a security alert indicating potentially suspicious activity.

The following information was reviewed:

* Alert timestamp
* Source and destination systems
* User account involved
* Process name
* Command-line activity
* Source and destination IP addresses
* Event IDs
* File and registry activity

Alerts were assessed using the available context rather than relying on a single event.

## 4. Event Correlation

Multiple events were correlated to determine whether they were part of the same activity.

Useful correlation points included:

* Matching timestamps
* Same user account
* Same host
* Related process activity
* Repeated network connections
* Similar indicators across multiple events

Event correlation helps distinguish isolated events from a broader attack sequence.

## 5. Suspicious Activity Analysis

Potentially suspicious behaviour included:

* Unusual process execution
* Unexpected command-line activity
* Repeated authentication failures
* Successful login following multiple failures
* Unexpected outbound connections
* Suspicious file creation
* Changes to persistence locations

Each observation should be validated against the surrounding system and user context before being classified as malicious.

## 6. Indicators of Compromise

Potential indicators collected during the investigation included:

* IP addresses
* Domains
* File hashes
* File names
* Process names
* Command-line arguments
* File paths
* User accounts
* Registry locations

These indicators can be used for additional searches and threat-hunting activities.

## 7. MITRE ATT&CK Mapping

Relevant techniques that may be associated with detected activity include:

* **T1059 — Command and Scripting Interpreter**
* **T1078 — Valid Accounts**
* **T1053 — Scheduled Task/Job**
* **T1547 — Boot or Logon Autostart Execution**
* **T1071 — Application Layer Protocol**
* **T1105 — Ingress Tool Transfer**

The final technique mapping should always be based on the evidence observed during the investigation.

## 8. SOC Response

When suspicious activity is confirmed, a SOC analyst may:

1. Validate the alert.
2. Determine the affected host and user.
3. Collect relevant evidence.
4. Identify indicators of compromise.
5. Search for related activity.
6. Determine the scope of the incident.
7. Escalate according to the incident response process.
8. Support containment and remediation.

## 9. False Positive Consideration

Not every alert represents malicious activity.

Before escalating an alert, analysts should consider:

* Whether the activity is expected
* Whether the user normally performs the action
* Whether the process is legitimate
* Whether the destination is trusted
* Whether similar activity occurs normally in the environment

Good alert triage reduces unnecessary escalation while ensuring genuine threats are investigated.

## 10. Lessons Learned

This exercise demonstrated the importance of analysing alerts in context.

Effective threat detection requires analysts to combine endpoint activity, authentication events, network information, and other available telemetry to understand the complete sequence of activity.

## 11. Skills Demonstrated

* Threat detection
* Security alert triage
* Event correlation
* IOC identification
* Log analysis
* Incident investigation
* MITRE ATT&CK mapping
* SOC escalation methodology
* False-positive analysis

## 12. Conclusion

This investigation strengthened my understanding of how SOC analysts detect and investigate suspicious activity.

The exercise demonstrated the importance of evidence-based analysis, event correlation, accurate alert classification, and structured incident response.
