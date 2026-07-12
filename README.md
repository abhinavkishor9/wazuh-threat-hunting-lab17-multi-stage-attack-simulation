# wazuh-threat-hunting-lab17-multi-stage-attack-simulation
## Overview

This lab demonstrates how a Security Operations Center (SOC) analyst can investigate a sequence of attacker activities using Sysmon and Wazuh.

Instead of analyzing a single event, this exercise simulates multiple attacker techniques that commonly appear during the early stages of an intrusion.

The objective is to observe how different Windows activities generate Sysmon telemetry and how Wazuh ingests those logs for investigation.

---

# Lab Objectives

- Verify Sysmon and Wazuh agent status
- Simulate a file download
- Observe Process Creation (Sysmon Event ID 1)
- Observe File Creation (Sysmon Event ID 11)
- Simulate Registry Run Key Persistence
- Simulate Scheduled Task Persistence
- Investigate generated events inside Wazuh
- Correlate attack activity

---

# Lab Environment

Host Machine

- Windows 11

SIEM

- Wazuh Manager
- Wazuh Dashboard

Endpoint Monitoring

- Sysmon
- Wazuh Agent

PowerShell

- PowerShell 7

---

# MITRE ATT&CK Mapping

| Activity | Technique | ATT&CK ID |
|-----------|-----------|-----------|
| File Download | Ingress Tool Transfer | T1105 |
| Process Creation | Command and Scripting Interpreter | T1059 |
| Registry Run Key | Registry Run Keys / Startup Folder | T1547.001 |
| Scheduled Task | Scheduled Task | T1053.005 |
| File Creation | File and Directory Discovery / Artifact Creation | T1083 |

---

# Attack Simulation

## Step 1

Verify Sysmon service.

## Step 2

Verify Wazuh Agent service.

## Step 3

Create working directory.

## Step 4

Download a sample web page using PowerShell.

## Step 5

Observe Process Creation events.

(Sysmon Event ID 1)

## Step 6

Observe File Creation events.

(Sysmon Event ID 11)

## Step 7

Create Registry Run Key.

## Step 8

Create Scheduled Task.

## Step 9

Investigate all related events inside Wazuh.

---

# Investigation Performed

The following Windows artifacts were successfully generated and investigated:

- PowerShell execution
- File creation
- Registry persistence
- Scheduled Task persistence

All activities were searchable from Wazuh for threat hunting purposes.

---


# Detection Opportunities

SOC analysts should monitor:

- PowerShell web downloads
- Unexpected scheduled tasks
- Registry Run key modifications
- File creation in unusual folders
- Parent-child process relationships

---

# Skills Demonstrated

- Windows Event Analysis
- Sysmon
- Wazuh SIEM
- Threat Hunting
- Windows Persistence
- Process Investigation
- Registry Analysis
- Scheduled Task Analysis
- SOC Investigation
- MITRE ATT&CK Mapping

---

# Outcome

Successfully simulated multiple attacker behaviors and validated that Sysmon telemetry was collected and searchable through Wazuh for investigation and threat hunting.
