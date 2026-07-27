# Project Overview

## Project Description

This project is a VMware-based Security Operations Center lab built around Splunk and Snort.

I developed the lab as my senior-level Capstone Project for Georgia Southern University. I wanted to create a simulated enterprise environment that could demonstrate security and monitoring challenges commonly faced by small businesses.

The environment provides a controlled sandbox where I can generate security events, test detection methods, review logs, develop Splunk searches, and practice incident-response procedures without affecting a production network.

## Project Objectives

The primary objectives of the project were to:

- Build a functional multi-system virtual lab
- Configure centralized log collection
- Collect Windows, Linux, PowerShell, and Snort data
- Generate controlled security events
- Confirm that collected events were searchable in Splunk
- Practice interpreting activity from a security analyst perspective
- Document the configuration, testing, troubleshooting, and results
- Create a reusable environment for future cybersecurity projects

## Lab Environment

The lab contains six virtual machines connected through a VMware NAT network.

| System | Role | IP Address |
|---|---|---|
| `1Splunk` | Central Splunk server and SIEM platform | `192.168.74.10` |
| `2Snort` | Snort intrusion detection sensor | `192.168.74.20` |
| `3Windows` | Windows user workstation and event source | `192.168.74.30` |
| `4Windows` | Windows Server system | `192.168.74.40` |
| `5Linux` | Linux endpoint and log source | `192.168.74.50` |
| `6Linux` | Attack simulation and testing machine | `192.168.74.60` |

## Technologies Used

The project incorporated:

- VMware Workstation
- Splunk Enterprise
- Splunk Universal Forwarder
- Snort IDS
- Windows
- Windows Server
- Ubuntu Linux
- PowerShell
- Nmap
- SSH
- Windows Event Viewer
- Linux authentication and system logs

## Centralized Log Collection

Splunk served as the central platform for collecting and reviewing security data.

Splunk Universal Forwarders sent collected events to:

```text
192.168.74.10:9997

The data was organized into separate indexes:

| Splunk | Index |	Data | Type |
|---|---|---|---|
| 'windows' |	Windows Event Logs and PowerShell activity |
| 'linux' |	Linux authentication and system activity |
| 'network' |	Snort alerts and network-related events |

## Security Events Tested

Controlled activity was generated to test the lab’s monitoring capabilities.

The testing included:

-Failed Linux authentication attempts
-Unauthorized SSH activity
-Nmap port scanning
-Suspicious PowerShell activity
-Failed Windows login attempts
-Privileged account modification
-Snort IDS alerts
-Suspicious file activity

Each test is documented separately in the 'splunk-searches' folder.

## Monitoring Process

The project demonstrates the complete flow of a security event:

1. Activity occurs on an endpoint or across the network.
2. Windows, Linux, or Snort generates a log or alert.
3. The Splunk Universal Forwarder collects the data.
4. The event is sent to the central Splunk server.
5. Splunk stores the event in the appropriate index.
6. The activity is located through a Splunk search.
7. The result is reviewed and interpreted from a security analyst perspective.

##Project Results

The completed lab demonstrated that security data could be collected from multiple systems and reviewed through a centralized SIEM platform.

The project also provided hands-on experience with:

-Virtual machine configuration
-Static IP addressing
-Network connectivity
-Windows and Linux administration
-Splunk index and forwarder configuration
-PowerShell logging
-Linux log collection
-Snort alert generation
-Security event simulation
-SPL searches
-Troubleshooting log-ingestion problems
-Security analysis and documentation

## Current Status

The original capstone build and functional testing are complete.

This repository expands the academic project into a long-term cybersecurity portfolio. It contains configuration documentation, security testing procedures, Splunk searches, analyst interpretations, and supporting evidence.

## Future Development

Planned improvements may include:

-Expanded use of 4Windows
-Active Directory testing
-Additional Windows Security auditing
-New Snort detection rules
-More targeted SPL searches
-Splunk alerts and dashboards
-Correlation of endpoint and network events
-Incident-response playbooks
-Additional attack simulations
-Detection-rule development
