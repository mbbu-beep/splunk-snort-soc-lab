# splunk-snort-soc-lab
A VMware-based SOC lab using Splunk and Snort to collect, simulate, and analyze security events across multiple operating systems and endpoints.
## My **W H Y**
I developed this lab as my Senior-level Capstone Project for Georgia Southern University. I wanted to focus on a simulated enterprise environment that could illustrate problems that are common for small business owners. This lab provides a sandbox environment where I can develop detection rules, test simulated attacks, and practice incident response procedures in a controlled setting.
## Project Overview
This VMware-based lab consists of six virtual machines connected over a NAT network. Splunk operates as the SIEM platform, while Snort provides network intrusion detection. Windows and Linux endpoints generate security activity that is forwarded to Splunk for investigation.
## Lab Environment
| System | Purpose |
|---|---|
| Splunk Server | Central log collection, searching, and analysis |
| Snort IDS | Network traffic monitoring and intrusion detection |
| Windows Endpoint | Windows event and PowerShell log generation |
| Windows Server | Windows authentication and account activity |
| Linux Endpoint | Linux authentication and system log collection |
| Linux Testing Machine | Attack simulation and event generation |
## Technologies Used

- VMware Workstation
- Splunk Enterprise
- Splunk Universal Forwarder
- Snort IDS
- Windows Server
- Windows 11
- Ubuntu Linux
- PowerShell
- Nmap
- SSH

## Security Events Tested

- Failed authentication attempts
- Unauthorized SSH activity
- Port scanning
- Suspicious PowerShell activity
- Windows failed logins
- Privileged account modification
- Snort IDS alerts
- Suspicious file activity

## Project Goals

- Configure centralized logging from Windows, Linux, and Snort systems
- Generate realistic security events in a controlled lab
- Confirm that security logs are searchable in Splunk
- Investigate endpoint and network activity from a SOC analyst perspective
- Document the configuration, testing, troubleshooting, and results

## Project Status
*Last updated 7/27/2026*
