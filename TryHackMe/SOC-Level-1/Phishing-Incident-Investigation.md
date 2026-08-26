# Phishing Incident Investigation — SOC Level 1

## 1. Investigation Overview

This case study documents a simulated multi-stage intrusion investigated as part of my SOC Level 1 hands-on training.

The investigation followed an attacker from initial payload execution through persistence, Command and Control (C2), privilege escalation, credential dumping, and lateral movement.

### Attack Chain

**Initial Execution → File Implantation → Persistence → C2 → UAC Bypass → Credential Dumping → Lateral Movement → Domain Credential Access**

---

## 2. Initial Access & Payload Execution

The investigation began with the execution of a malicious Stage 1 payload.

During process analysis, I identified the process responsible for launching the initial payload and investigated its execution behavior.

The payload attempted to implant a file into another location on the system before continuing its execution.

### Key Investigation Focus

* Process identification
* Command-line analysis
* File implantation
* Parent/child process relationships
* Suspicious execution behavior

---

## 3. Persistence

The implanted payload was subsequently executed and established persistence on the compromised Windows system.

The persistence mechanism involved the creation of a scheduled task.

This demonstrated how an attacker can maintain access even after the initial execution process has ended.

### Technique Observed

**MITRE ATT&CK: T1053 — Scheduled Task/Job**

---

## 4. Command & Control

Analysis of the implanted payload revealed a potential outbound Command and Control connection.

The connection was investigated using network indicators and process execution context.

**C2 Address:** `[REDACTED]`

### Investigation Focus

* Destination IP and port
* Network connection associated with the malicious process
* Process responsible for the connection
* Relationship between execution and network activity

This stage demonstrated the importance of correlating **process activity with network telemetry** during an incident investigation.

---

## 5. UAC Bypass

After establishing access, the attacker discovered that the current account had local administrator privileges.

The attacker then used a Windows process associated with a known User Account Control bypass technique.

### Process Identified

`fodhelper.exe`

### Technique

**MITRE ATT&CK: T1548.002 — Bypass User Account Control**

This stage highlighted how legitimate Windows components can be abused to execute malicious activity with elevated privileges.

---

## 6. Credential Dumping

With elevated privileges available, the attacker attempted to obtain credentials from the compromised system.

The investigation identified the use of **Mimikatz**, a well-known credential-dumping tool.

The tool was obtained from an external repository during the simulated attack.

### Investigation Focus

* Credential access
* Suspicious tool download
* Privileged process execution
* Authentication material exposure

### Technique

**MITRE ATT&CK: T1003 — OS Credential Dumping**

Sensitive credential values observed during the lab have been intentionally redacted from this public portfolio.

---

## 7. Lateral Movement

Credentials obtained from the first compromised system were subsequently used to access another machine.

The attacker enumerated an accessible remote share and discovered a PowerShell script containing additional credentials.

This demonstrated how compromised credentials and shared files can be used to expand an intrusion across an environment.

### Key Evidence

**Remote file:** `IT_Automation.ps1`

**New credentials:** `[REDACTED]`

### Investigation Focus

* Remote share enumeration
* Credential discovery
* PowerShell activity
* Authentication using compromised credentials
* Movement between Windows systems

---

## 8. Second Compromised Machine

The attacker used the newly discovered credentials to move laterally to another Windows machine.

The hostname identified during the investigation was:

`WKSTN-1327`

The malicious command executed remotely resulted in activity under:

`Wsmprovhost.exe`

This process is associated with Windows Remote Management (WinRM), making process ancestry and remote execution telemetry particularly important during the investigation.

### Technique

**MITRE ATT&CK: T1021.006 — Windows Remote Management**

---

## 9. Second Credential Dump

After gaining access to the second machine, the attacker again attempted to dump credentials.

The investigation identified another privileged account whose credential material had been exposed.

For security and portfolio purposes, the credential hash is **not reproduced here**.

### Investigation Focus

* Credential dumping
* Privileged account activity
* Repeated attacker behavior
* Correlation between compromised hosts

---

## 10. Domain Credential Access

The intrusion subsequently progressed toward the domain environment.

The attacker attempted to obtain credential information from the domain controller using a **DCSync-style credential access technique**.

This stage demonstrates how an attacker who has obtained sufficient privileges can target domain-level authentication material and potentially escalate the impact of a compromise.

### Technique

**MITRE ATT&CK: T1003.006 — DCSync**

---

## 11. Indicators & Evidence

During the investigation, several indicators were identified:

| Indicator                | Finding                     |
| ------------------------ | --------------------------- |
| Initial Payload          | Malicious Stage 1 execution |
| Persistence              | Scheduled Task              |
| UAC Bypass               | `fodhelper.exe`             |
| Credential Tool          | Mimikatz                    |
| Remote File              | `IT_Automation.ps1`         |
| Lateral Movement         | Windows Remote Management   |
| Remote Execution Process | `Wsmprovhost.exe`           |
| Domain Credential Access | DCSync                      |
| C2                       | `[REDACTED]`                |

---

## 12. Detection Opportunities

From a SOC analyst perspective, several detection opportunities could have helped identify the intrusion earlier:

* Monitor suspicious scheduled task creation.
* Alert on unusual execution of `fodhelper.exe`.
* Detect known credential-dumping tools and suspicious access to credential stores.
* Monitor abnormal PowerShell activity.
* Investigate unexpected WinRM connections between workstations.
* Correlate privileged authentication across multiple hosts.
* Monitor unusual network connections from newly executed binaries.
* Alert on suspicious DCSync-related directory replication activity.

---

## 13. Lessons Learned

This investigation reinforced several important SOC concepts.

### 1. Process context matters

A suspicious executable becomes much more meaningful when its parent process, command line, file location, and network activity are correlated.

### 2. One alert rarely tells the whole story

The intrusion consisted of multiple stages. Connecting individual indicators helped reconstruct the complete attack chain.

### 3. Credential security is critical

Once credentials were compromised, the attacker was able to move from one system to another and eventually target domain-level credentials.

### 4. Legitimate Windows tools can be abused

Processes such as `fodhelper.exe` and `Wsmprovhost.exe` can appear legitimate in isolation. Their context and behavior are therefore important during investigation.

### 5. Documentation is part of security work

A strong analyst should not only identify what happened but also explain **why the activity was suspicious, how the evidence was connected, and what could be detected or prevented.**

---

## 14. Skills Demonstrated

Through this investigation I practiced:

* SOC investigation methodology
* Windows process analysis
* Command-line analysis
* Malware and payload investigation
* Persistence analysis
* Network/C2 investigation
* UAC bypass analysis
* Credential access investigation
* PowerShell investigation
* Lateral movement analysis
* WinRM investigation
* MITRE ATT&CK mapping
* Incident timeline reconstruction
* Security documentation

---

## 15. Conclusion

This investigation gave me practical experience following an intrusion across multiple stages rather than analyzing isolated alerts.

The biggest lesson was that effective SOC analysis requires **correlation**: process activity, command lines, network connections, authentication events, and host-to-host movement must be connected to understand the attack.

I am continuing to build my cybersecurity portfolio through hands-on labs, investigation write-ups, and practical security projects.
