# Suspicious File Activity

## Purpose

The purpose of this test was to determine whether file operations performed through PowerShell could be identified through PowerShell log analysis in Splunk.

## Source and Monitoring Systems

| System | Role | IP Address |
|---|---|---|
| `1Splunk` | SIEM used to collect and review Windows events | `192.168.74.10` |
| `2Snort` | IDS sensor used to monitor network traffic | `192.168.74.20` |
| `3Windows` | Windows workstation used to generate the file activity | `192.168.74.30` |
| `4Windows` | Windows domain/server system available for future testing | `192.168.74.40` |
| `5Linux` | Linux endpoint and log source | `192.168.74.50` |
| `6Linux` | Attack and testing machine | `192.168.74.60` |

## Test Activity

PowerShell was used on `3Windows` to perform controlled file operations.

The test file was:

1. Created
2. Modified
3. Renamed
4. Deleted

The purpose was not to simulate malware, but to generate a sequence of file-related PowerShell commands that could be reviewed in the PowerShell Operational Log and Splunk.

The final report confirms these four actions, but it does not preserve the exact filename, file path, or PowerShell commands used.

## Log Source

The activity was reviewed through:

```text
Microsoft-Windows-PowerShell/Operational
```

The corresponding Splunk sourcetype was:

```text
WinEventLog:Microsoft-Windows-PowerShell/Operational
```

PowerShell Script Block Logging, Module Logging, and the PowerShell Operational Log were enabled on `3Windows` before the test activity was generated.

## Splunk Search

```spl
index=* sourcetype="WinEventLog:Microsoft-Windows-PowerShell/Operational"
```

The search can also be limited to the Windows index:

```spl
index=windows sourcetype="WinEventLog:Microsoft-Windows-PowerShell/Operational"
```

The time range should be narrowed to the period when the file operations were performed.

## Expected Evidence

The resulting PowerShell events may contain commands associated with:

- Creating a file
- Writing or appending content
- Renaming a file
- Deleting a file
- The user who executed the commands
- The workstation where the activity occurred
- The date and time of execution

## Analyst Interpretation

File creation, modification, renaming, and deletion are normal system activities and are not automatically malicious.

However, a similar sequence may require investigation when it involves:

- Sensitive or protected files
- Unexpected file extensions
- System or startup directories
- Encoded or heavily obfuscated PowerShell commands
- Files downloaded from an external source
- Execution immediately after the file was created
- Deletion intended to remove evidence
- Activity performed by an unexpected user or account

A security analyst should review the command content, file location, user, timing, and related process or network activity before determining whether the behavior is suspicious.

## Result

The test generated controlled file activity on `3Windows` using PowerShell. It demonstrated that file-related commands could be recorded through enhanced PowerShell logging and reviewed in Splunk.

---

### *About This Project*

**Created by Molly Bentley Ussery | Senior Capstone Project | July 2026**

This project documents hands-on cybersecurity work completed in a six-system Splunk + Snort SOC lab, including security monitoring, detection, attack simulation, investigation, and analyst documentation.

🔗 **Quick Links** *| [Cybersecurity Portfolio](https://mbbu-beep.github.io/) | [Project Home](https://github.com/mbbu-beep/splunk-snort-soc-lab) | [Video Demo](https://github.com/mbbu-beep/splunk-snort-soc-lab/blob/main/documentation/video-demo.md) | [Cybersecurity Insights](https://github.com/mbbu-beep/cybersecurity-insights) | [LinkedIn](https://www.linkedin.com/in/mollybbussery/) |* 🔒

