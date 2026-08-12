# Windows Failed Login

## Purpose

The purpose of this test was to determine whether failed Windows sign-in attempts were captured in the Windows Security log and available for review in Splunk.

## Source and Monitoring Systems

| System | Role | IP Address |
|---|---|---|
| `1Splunk` | SIEM used to collect and review Windows events | `192.168.74.10` |
| `2Snort` | IDS sensor used to monitor network traffic | `192.168.74.20` |
| `3Windows` | Windows workstation used to generate the failed sign-in activity | `192.168.74.30` |
| `4Windows` | Windows domain/server system available for future testing | `192.168.74.40` |
| `5Linux` | Linux endpoint and log source | `192.168.74.50` |
| `6Linux` | Attack and testing machine | `192.168.74.60` |

## Test Activity

One or more Windows sign-in attempts were made on `3Windows` using invalid credentials.

The activity was intended to generate a failed authentication event in the Windows Security log for review in Splunk. The final report confirms the use of invalid credentials but does not preserve the exact username, password, or number of attempts. 

## Log Source

The relevant log source was:

```text
Windows Security Log
```

The corresponding Splunk sourcetype was:

```text
WinEventLog:Security
```

The Windows Security log was included in the forwarder configuration for `3Windows`. In the project log-source table, its final validation status was listed as deferred, so the GitHub documentation should not claim more than the available evidence confirms. 

## Splunk Search

```spl
index=* sourcetype="WinEventLog:Security"
```

The search can also be limited to the Windows index:

```spl
index=windows sourcetype="WinEventLog:Security"
```

The time range should be narrowed to the period when the failed sign-in attempts were performed.

## Expected Evidence

A failed Windows sign-in may produce evidence showing:

- The account name used in the attempt
- The workstation where the attempt occurred
- The date and time of the failed sign-in
- The logon type
- The failure reason or status
- The source network address, when available
- A Windows failed-logon event such as Event ID `4625`

## Analyst Interpretation

A failed Windows login does not automatically indicate malicious activity. It may result from:

- A mistyped password
- An expired password
- An outdated saved credential
- A locked or disabled account
- A user attempting to access the wrong workstation
- Password guessing or brute-force activity
- An unauthorized attempt to access the endpoint

A security analyst should review the account involved, number and frequency of failures, source system, logon type, failure reason, and whether a successful login followed the failed attempts.

Repeated failures from the same source or attempts against several accounts would generally require closer investigation.

## Result

The test generated controlled failed Windows sign-in activity on `3Windows`.

---

### *About This Project*

**Created by Molly Bentley Ussery | Senior Capstone Project | July 2026**

This project documents hands-on cybersecurity work completed in a six-system Splunk + Snort SOC lab, including security monitoring, detection, attack simulation, investigation, and analyst documentation.

🔗 **Quick Links** *| [Cybersecurity Portfolio](https://mbbu-beep.github.io/) | [Project Home](https://github.com/mbbu-beep/splunk-snort-soc-lab) | [Video Demo](https://github.com/mbbu-beep/splunk-snort-soc-lab/blob/main/documentation/video-demo.md) | [Cybersecurity Insights](https://github.com/mbbu-beep/cybersecurity-insights) | [LinkedIn](https://www.linkedin.com/in/mollybbussery/) |* 🔒

