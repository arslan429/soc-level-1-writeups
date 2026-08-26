# Command and Control (C2) — SOC Level 1

## 1. Investigation Overview

This case study documents the analysis of Command and Control (C2) activity during SOC Level 1 training.

The objective was to understand how compromised systems communicate with attacker-controlled infrastructure and how a SOC analyst can identify suspicious network behaviour.

## 2. What is Command and Control?

Command and Control (C2) refers to communication between a compromised system and attacker-controlled infrastructure.

After gaining access to a system, an attacker may establish communication with external infrastructure to:

* Receive commands
* Transfer files
* Execute additional payloads
* Maintain control of the compromised host
* Exfiltrate information

## 3. C2 Investigation

The investigation focused on identifying unusual outbound network connections from a potentially compromised host.

The following information was reviewed:

* Source IP address
* Destination IP address
* Destination port
* Protocol
* Connection frequency
* DNS queries
* Process responsible for the connection
* User account
* Connection timestamps

## 4. Suspicious Network Behaviour

Potential indicators of C2 activity included:

* Repeated outbound connections to the same external destination
* Connections initiated by an unusual process
* Unexpected communication over commonly used ports
* Periodic or beacon-like network connections
* DNS requests to suspicious domains
* Network activity from a process that normally should not communicate externally

A single indicator does not automatically confirm C2 activity. Network behaviour should be investigated in context.

## 5. Process and Network Correlation

Process information was correlated with network activity to identify which application initiated suspicious connections.

Useful questions included:

* Which process created the connection?
* Was the process expected?
* Which user executed the process?
* When did the network communication begin?
* Did the process create or modify files?
* Were there related authentication or endpoint events?

Correlating endpoint and network telemetry helps establish a stronger incident timeline.

## 6. Indicators of Compromise

Potential C2 indicators included:

* Malicious IP addresses
* Suspicious domains
* URLs
* Destination ports
* File hashes
* Suspicious processes
* DNS queries
* Network connection timestamps

These indicators can be used for threat hunting and additional searches across available security logs.

## 7. MITRE ATT&CK Mapping

Potential techniques associated with C2 activity include:

* **T1071 — Application Layer Protocol**
* **T1071.001 — Web Protocols**
* **T1105 — Ingress Tool Transfer**
* **T1573 — Encrypted Channel**
* **T1095 — Non-Application Layer Protocol**

Technique mapping should be based on the evidence observed during the investigation.

## 8. Detection and Response

A SOC analyst investigating suspected C2 activity may:

1. Validate the alert.
2. Identify the affected host.
3. Identify the process responsible for communication.
4. Review destination IPs and domains.
5. Search for related connections across the environment.
6. Identify additional indicators of compromise.
7. Determine the scope of the activity.
8. Escalate the incident when malicious communication is confirmed.
9. Support containment and remediation.

## 9. Lessons Learned

This investigation demonstrated that network connections become more meaningful when correlated with endpoint and process information.

Effective C2 detection requires analysts to look for unusual communication patterns rather than relying on a single IP address, port, or domain.

## 10. Skills Demonstrated

* C2 detection
* Network traffic analysis
* Process-to-network correlation
* IOC identification
* DNS investigation
* Threat hunting
* MITRE ATT&CK mapping
* SOC alert investigation
* Incident escalation

## 11. Conclusion

The exercise strengthened my understanding of how attackers maintain communication with compromised systems and how SOC analysts can identify suspicious C2 behaviour.

The investigation highlighted the importance of correlating network, endpoint, process, and authentication telemetry to build an accurate incident timeline.
