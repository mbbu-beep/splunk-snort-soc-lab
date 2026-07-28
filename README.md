## Project Resources

- [Project Overview](documentation/project-overview.md)
- [Lab Architecture](documentation/architecture.md)
- [Log Sources](documentation/log-sources.md)
- [Lessons Learned](documentation/lessons-learned.md)
- [Video Demonstration](documentation/video-demo.md)

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

# Video Demonstration

This video provides a walkthrough of the VMware-based SOC lab, including the lab architecture, log collection, simulated security events, and analysis in Splunk.

## Watch the Demo

[![Watch the Splunk and Snort SOC Lab Demo](https://img.youtube.com/vi/XDrDwW4bpJg/hqdefault.jpg)](https://www.youtube.com/watch?v=XDrDwW4bpJg)

*Click the image to open the video on YouTube.*

## Project Status
*Last updated 7/27/2026*
