# Lessons Learned

## Overview

Building this lab taught me that creating a functional security monitoring environment involves much more than installing a SIEM and connecting a few machines.

The project required networking, system administration, log configuration, troubleshooting, security testing, and documentation. It also reinforced that security events are only useful when the complete collection process is working correctly.

**Quick Links:** *| [Project Overview](project-overview.md) | [Lab Architecture](architecture.md) | [Log Sources](log-sources.md) | [Video Demonstration](video-demo.md) |*

## Log Collection Must Be Verified End to End

One of the most important lessons was that enabling a log source does not automatically mean the data is reaching Splunk.

Each stage had to be confirmed:

1. The activity occurred on the endpoint.
2. The operating system or Snort generated a log.
3. The Splunk Universal Forwarder monitored the correct source.
4. The forwarder connected to the Splunk server.
5. Splunk placed the event in the correct index.
6. The event could be found using a search.

This made me more careful about validating the full logging pipeline instead of assuming that a successful installation meant everything was working.

## Configuration Details Matter

Small configuration details had a major effect on whether data was collected successfully.

Examples included:

- Using the correct file path in `inputs.conf`
- Sending data to the correct Splunk server address and port
- Matching events to the intended Splunk index
- Restarting services after configuration changes
- Confirming that the monitored file actually contained current data
- Verifying permissions for log files and configuration directories

A single incorrect path, filename, port, or setting could prevent an entire log source from appearing in Splunk.

## Troubleshooting Is a Major Part of Security Work

A large part of the project involved troubleshooting rather than following a perfect sequence of steps.

Issues included:

- Forwarders not appearing as expected
- Logs not returning in Splunk searches
- Linux permission errors
- Snort alert-file confusion
- Incorrect or incomplete configuration files
- Time differences between systems and Splunk results
- Services that needed to be restarted before changes took effect

The troubleshooting process helped me become more comfortable checking file paths, service status, configuration contents, network connectivity, and log output before changing additional settings.

## Broad Searches Are Useful for Initial Validation

Simple searches such as:

```spl
index=windows
```

```spl
index=linux
```

```spl
index=network
```

were useful for confirming that data was entering Splunk.

After confirming ingestion, searches could be narrowed by:

- Sourcetype
- Host
- Username
- Source IP address
- Event ID
- Keywords
- Time range

This reinforced the value of starting broad during troubleshooting and becoming more specific during an investigation.

## Context Is Required Before Labeling Activity as Malicious

Many of the activities generated in this lab could be either legitimate or suspicious depending on the situation.

Examples included:

- Failed login attempts
- PowerShell execution
- Port scanning
- Account creation
- Administrator-group changes
- File modification
- SSH activity

A single event does not always prove malicious behavior. An analyst must consider the user, source system, timing, frequency, authorization, and related activity before reaching a conclusion.

## PowerShell Logging Provides Valuable Visibility

Enabling Script Block Logging, Module Logging, and the PowerShell Operational Log provided much more information than relying only on basic Windows logs.

This demonstrated why enhanced PowerShell logging is valuable for identifying commands associated with:

- Account changes
- File operations
- Administrative activity
- Potentially suspicious scripts

It also showed that enhanced logging must be configured before the activity occurs if detailed evidence is expected later.

## Network Detection Depends on Visibility and Rules

Snort only generated useful alerts when:

- The sensor could observe the traffic
- The correct rule was enabled
- The traffic matched the rule conditions
- The correct alert file was monitored
- The alert was forwarded to Splunk

This helped me understand that an IDS does not automatically detect every suspicious action. Its effectiveness depends on network placement, configuration, active rules, and the quality of the traffic being inspected.

## Documentation Should Be Created During the Build

Reconstructing commands, searches, filenames, and configuration decisions after the project was complete was more difficult than documenting them during the build.

For future projects, I would maintain:

- A command history
- A configuration-change log
- A screenshot checklist
- A table of log sources
- A list of exact Splunk searches
- Notes describing errors and their solutions

This would make final testing, reporting, and portfolio development more efficient.

## What I Would Improve

Future improvements to the lab may include:

- Expanded testing on `4Windows`
- Active Directory authentication and account testing
- More specific Splunk searches and correlation rules
- Custom Splunk dashboards
- Automated alerts for repeated failed logins
- Additional Snort rules
- Improved Windows Security auditing
- Incident-response playbooks
- Additional attack simulations
- More detailed documentation of exact commands and results

## Final Takeaway

The project gave me hands-on experience with the complete security monitoring process rather than only one tool.

I learned how security activity is generated, recorded, forwarded, indexed, searched, and interpreted. I also learned that successful monitoring depends on careful configuration, continuous validation, and the ability to troubleshoot problems across multiple systems.

---

### *About This Project*

**Created by Molly Bentley Ussery | Senior Capstone Project | July 2026**

This project documents hands-on cybersecurity work completed in a six-system Splunk + Snort SOC lab, including security monitoring, detection, attack simulation, investigation, and analyst documentation.

🔗 **Quick Links** *| [Cybersecurity Portfolio](https://mbbu-beep.github.io/) | [Project Home](https://github.com/mbbu-beep/splunk-snort-soc-lab) | [Video Demo](https://github.com/mbbu-beep/splunk-snort-soc-lab/blob/main/documentation/video-demo.md) | [Cybersecurity Insights](https://github.com/mbbu-beep/cybersecurity-insights) | [LinkedIn](https://www.linkedin.com/in/mollybbussery/) |* 🔒
