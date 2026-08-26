# Persistence — SOC Level 1

## 1. Investigation Overview

This case study documents the investigation of persistence activity during SOC Level 1 training.

The objective was to understand how an attacker can maintain access to a compromised system after initial execution and how a SOC analyst can identify persistence mechanisms.

## 2. What is Persistence?

Persistence is a technique used by attackers to maintain access to a system after events such as reboot, logout, or process termination.

Attackers may use legitimate operating system features or applications to automatically execute malicious programs.

## 3. Persistence Investigation

The investigation focused on identifying changes that could allow suspicious programs to execute automatically.

Areas reviewed included:

* Startup locations
* Scheduled tasks
* Services
* Registry-based execution
* User startup folders
* Recently created or modified files
* Suspicious processes
* Authentication and system events

## 4. Suspicious Indicators

Potential indicators of persistence included:

* Unknown programs configured to start automatically
* Newly created scheduled tasks
* Unexpected services
* Suspicious registry modifications
* Executables stored in unusual directories
* Persistence mechanisms created shortly after initial compromise
* Repeated execution of the same suspicious process

A persistence mechanism should always be correlated with process, file, and authentication activity before determining that it is malicious.

## 5. Timeline Analysis

A useful investigation timeline may include:

1. Initial payload execution
2. File creation or modification
3. Persistence mechanism creation
4. System restart or user logon
5. Automatic execution
6. Network communication
7. Additional attacker activity

Building a timeline helps determine whether the persistence mechanism was related to the original compromise.

## 6. MITRE ATT&CK Mapping

Potential persistence techniques include:

* **T1053 — Scheduled Task/Job**
* **T1547 — Boot or Logon Autostart Execution**
* **T1543 — Create or Modify System Process**
* **T1547.001 — Registry Run Keys / Startup Folder**

Technique mapping should be based on evidence observed during the investigation.

## 7. Detection and Response

A SOC analyst investigating suspected persistence may:

1. Identify the suspicious persistence mechanism.
2. Determine when it was created.
3. Identify the associated executable or process.
4. Review the user account responsible for the change.
5. Search for related indicators across the environment.
6. Determine whether the mechanism is legitimate or malicious.
7. Remove or disable the malicious persistence mechanism during remediation.
8. Continue monitoring the affected system for additional attacker activity.

## 8. Lessons Learned

Persistence analysis demonstrated the importance of monitoring changes to startup mechanisms, scheduled tasks, services, and other operating system features.

A suspicious persistence mechanism becomes more significant when it appears shortly after initial compromise and is associated with unusual processes or network communication.

## 9. Skills Demonstrated

* Persistence detection
* Windows security monitoring
* Event analysis
* Process investigation
* Timeline construction
* IOC identification
* MITRE ATT&CK mapping
* Incident investigation
* Threat hunting

## 10. Conclusion

The investigation strengthened my understanding of how attackers attempt to maintain access to compromised systems and how SOC analysts can identify persistence through endpoint and event telemetry.

Correlating persistence mechanisms with process execution, file activity, authentication events, and network connections helps establish whether the activity is part of a larger intrusion.
