# Investigation Notes

## Incident Summary

A controlled attack simulation was performed to generate multiple Windows telemetry events for SOC investigation.

The objective was to validate endpoint visibility using Sysmon and Wazuh.

---

# Timeline

### Step 1

Verified Sysmon service.

Status:

Running

---

### Step 2

Verified Wazuh Agent.

Status:

Running

---

### Step 3

Created working directory.

Location:

C:\SOCLab

Observed:

Directory creation.

---

### Step 4

Executed PowerShell web request.

Observed:

PowerShell downloaded a sample webpage.

Relevant ATT&CK

T1105

---

### Step 5

Process Creation

Sysmon Event ID

1

Observed

PowerShell execution

Parent Process

powershell.exe

Child Activity

Invoke-WebRequest

---

### Step 6

File Creation

Sysmon Event ID

11

Observed

example.html created

Location

C:\SOCLab

---

### Step 7

Registry Persistence

Location

HKCU\Software\Microsoft\Windows\CurrentVersion\Run

Value

SOCLab

Executable

notepad.exe

ATT&CK

T1547.001

---

### Step 8

Scheduled Task

Task Name

SOCLabTask

Trigger

At Logon

Executable

notepad.exe

ATT&CK

T1053.005

---

# Wazuh Investigation

Observed Events

✔ Process Creation

✔ File Creation

✔ Registry Modification

✔ Scheduled Task Activity

Some Sysmon Event ID 3 (Network Connection) events were not visible in Wazuh due to local Sysmon configuration. However, other Sysmon telemetry successfully demonstrated attack progression.

---

# Correlation

Attack Chain

PowerShell Execution

↓

File Download

↓

File Creation

↓

Registry Persistence

↓

Scheduled Task Persistence

---

# MITRE Mapping

T1105

Ingress Tool Transfer

T1059

PowerShell

T1547.001

Registry Run Keys

T1053.005

Scheduled Tasks

---

# SOC Analyst Findings

No malware was executed.

All activities were intentionally generated inside a controlled lab.

The collected telemetry demonstrates how multiple attacker techniques can be correlated during a threat hunting investigation.

---

# Lessons Learned

- Individual Windows events rarely provide full attack context.
- Correlating multiple Sysmon events improves investigation accuracy.
- Registry and Scheduled Task persistence remain common attacker techniques.
- Wazuh provides effective visibility into endpoint activity when Sysmon telemetry is properly configured.
