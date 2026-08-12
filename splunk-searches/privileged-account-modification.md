# Privileged Account Modification

## Purpose

The purpose of this test was to determine whether local account creation and changes to administrative privileges could be detected through Windows logging and reviewed in Splunk.

## Source and Monitoring Systems

| System | Role | IP Address |
|---|---|---|
| `1Splunk` | SIEM used to collect and review Windows events | `192.168.74.10` |
| `2Snort` | IDS sensor used to monitor network traffic | `192.168.74.20` |
| `3Windows` | Windows workstation used to generate the account activity | `192.168.74.30` |
| `4Windows` | Windows domain/server system available for future testing | `192.168.74.40` |
| `5Linux` | Linux endpoint and log source | `192.168.74.50` |
| `6Linux` | Attack and testing machine | `192.168.74.60` |

## Test Activity

A temporary local user account was created on `3Windows`.

The account was then:

1. Added to the local `Administrators` group
2. Removed from the local `Administrators` group
3. Removed from the workstation

This controlled activity was used to test whether account creation and privileged group membership changes could be identified through the available Windows and PowerShell logs. The final report confirms these actions but does not preserve the exact username or commands used.

## Log Sources

The activity was reviewed using Windows data forwarded from `3Windows` to the Splunk `windows` index.

Relevant log sources included:

```text
Windows Security Log
Microsoft-Windows-PowerShell/Operational
```

The PowerShell Operational Log was confirmed as a completed log source. Windows Security Log collection was also configured, although the preserved project evidence is strongest for the PowerShell activity associated with this test.

## Splunk Searches

To review PowerShell activity associated with the account changes:

```spl
index=windows sourcetype="WinEventLog:Microsoft-Windows-PowerShell/Operational"
```

To review available Windows Security events:

```spl
index=windows sourcetype="WinEventLog:Security"
```

The results should be narrowed to the time when the temporary account was created and modified.

## Expected Evidence

Depending on the available auditing and log source, the results may show:

- Creation of a temporary local user
- Addition of the user to the local `Administrators` group
- Removal of the user from the local `Administrators` group
- Deletion of the temporary account
- PowerShell commands used to perform the changes
- The user and workstation associated with the activity

## Analyst Interpretation

Changes to privileged accounts are important because administrator-level access can allow a user to modify security settings, install software, access protected information, or make system-wide changes.

This activity is not automatically malicious. It may be caused by:

- Authorized account administration
- Temporary technical support access
- Employee onboarding or offboarding
- A service or application installation
- Unauthorized privilege escalation
- Persistence established after an account compromise

A security analyst should verify who performed the change, whether it was approved, how long the privilege remained active, and whether the account performed any additional activity.

## Result

The test generated controlled account and administrative group changes on `3Windows`. The activity demonstrated how local account creation and privileged membership changes can be reviewed through Windows and PowerShell logging in Splunk.

---

### *About This Project*

**Created by Molly Bentley Ussery | Senior Capstone Project | July 2026**

This project documents hands-on cybersecurity work completed in a six-system Splunk + Snort SOC lab, including security monitoring, detection, attack simulation, investigation, and analyst documentation.

🔗 **Quick Links** *| [Cybersecurity Portfolio](https://mbbu-beep.github.io/) | [Project Home](https://github.com/mbbu-beep/splunk-snort-soc-lab) | [Video Demo](https://github.com/mbbu-beep/splunk-snort-soc-lab/blob/main/documentation/video-demo.md) | [Cybersecurity Insights](https://github.com/mbbu-beep/cybersecurity-insights) | [LinkedIn](https://www.linkedin.com/in/mollybbussery/) |* 🔒
