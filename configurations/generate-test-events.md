# Windows Test Event Generation

These activities were performed on the `3Windows` workstation inside the controlled VMware SOC lab to generate Windows and PowerShell events for analysis in Splunk.

> **Note:** These procedures were performed only within an authorized lab environment.

## Standard Windows Test Event

The Windows `eventcreate` command was used to generate a manual test event in the Application log.

```powershell
eventcreate /ID 100 /L APPLICATION /T INFORMATION /SO CapstoneLab /D "Manual Capstone test event from 3Windows"
```

The resulting event was reviewed in the Windows logs and confirmed in the Splunk `windows` index.

## PowerShell Activity

PowerShell commands were run on `3Windows` after enabling:

- Script Block Logging
- Module Logging
- The PowerShell Operational Log

The generated PowerShell activity was then reviewed in Splunk.

## Privileged Account Modification

A temporary local user account was:

1. Created on `3Windows`
2. Added to the local Administrators group
3. Removed from the Administrators group
4. Removed from the system

This activity was performed to determine whether account creation and privileged group changes could be identified through Windows and PowerShell logs.

## Suspicious File Activity

PowerShell was used to:

1. Create a test file
2. Modify the file
3. Rename the file
4. Delete the file

The resulting commands and activity were reviewed through PowerShell logging and Splunk.

## Evidence Reviewed

The generated activity was reviewed using:

- Windows Application logs
- Windows Security logs
- PowerShell Operational logs
- Splunk searches within the `windows` index
