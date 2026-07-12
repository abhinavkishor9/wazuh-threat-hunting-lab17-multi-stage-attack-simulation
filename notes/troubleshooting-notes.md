# Troubleshooting Notes

## Issue 1

### Sysmon Event ID 3 not visible in Wazuh

Symptoms

No results returned when searching:

data.win.system.eventID:3

Possible Causes

- Sysmon configuration does not log Network Connection events.
- Event not yet forwarded to Wazuh.
- Incorrect search time range.
- Wazuh indexing delay.

Resolution

- Verified Sysmon service was running.
- Confirmed Event ID 3 existed locally.
- Expanded Wazuh search time range.
- Continued investigation using available Event IDs.

Status

Resolved (alternative investigation performed)

---

## Issue 2

PowerShell download completed but Event ID 3 unavailable.

Resolution

Verified:

- Event ID 1
- Event ID 11

These confirmed successful execution.

---

## Issue 3

Registry persistence not immediately visible.

Resolution

Verified Run Key using:

Get-ItemProperty HKCU:\Software\Microsoft\Windows\CurrentVersion\Run

Confirmed:

SOCLab

notepad.exe

---

## Issue 4

Scheduled Task verification.

Resolution

Used:

schtasks /query /tn "SOCLabTask"

Confirmed task creation.

---

## Issue 5

Wazuh search returned unrelated events.

Observed

DNS Client logs

OSSEC logs

Other Windows telemetry

Resolution

Filtered specifically using:

data.win.system.eventID

and

agent.id:001

to isolate Sysmon events.

---

## Issue 6

No immediate Wazuh alert after activity.

Possible Causes

- Agent synchronization delay
- Index refresh delay
- Dashboard cache

Resolution

Waited 30–60 seconds and refreshed the search.

---

# Recommendations

- Enable Sysmon Network Connection logging (Event ID 3) in the Sysmon configuration.
- Create custom Wazuh rules for PowerShell downloads.
- Add detections for Registry Run Key persistence.
- Create Scheduled Task detection rules.
- Correlate Event IDs 1, 3, 11, 13, and 19 for richer attack timelines.

---

# Final Status

Lab completed successfully.

Successfully validated:

- Sysmon Event ID 1
- Sysmon Event ID 11
- Registry Run Key Persistence
- Scheduled Task Persistence
- Wazuh Threat Hunting Investigation

The absence of Event ID 3 in Wazuh did not prevent successful completion of the multi-stage attack investigation.
