# Linux Security Event Testing

These commands were used within the authorized VMware lab to generate Linux authentication and network activity for analysis in Splunk.

## Failed Authentication and Unauthorized SSH Activity

The `5Linux` endpoint was used to attempt an SSH connection to the `6Linux` testing machine with an invalid username:

```bash
ssh fakeuser@192.168.74.60
```

The invalid login attempt generated authentication activity for review in the Linux logs and Splunk.

## Port Scanning

Nmap commands were issued from `6Linux` to scan systems within the isolated VMware network for open ports and available services.

```bash
nmap 192.168.74.50
```

The target address varied according to the system being tested.

## Log Sources Reviewed

The resulting Linux activity was collected from:

```text
/var/log/auth.log
/var/log/syslog
```

The Splunk Universal Forwarder sent these logs to the `linux` index.

Port-scanning and Snort alert activity was also reviewed in the `network` index.

## Testing Results

The testing confirmed that:

- Linux authentication activity was recorded.
- Failed SSH attempts appeared in the collected authentication logs.
- Nmap generated port-scanning traffic within the lab.
- Linux and network events were searchable in Splunk.

---

### *About This Project*

**Created by Molly Bentley Ussery | Senior Capstone Project | July 2026**

This project documents hands-on cybersecurity work completed in a six-system Splunk + Snort SOC lab, including security monitoring, detection, attack simulation, investigation, and analyst documentation.

🔗 **Quick Links** *| [Cybersecurity Portfolio](https://mbbu-beep.github.io/) | [Project Home](https://github.com/mbbu-beep/splunk-snort-soc-lab) | [Video Demo](https://github.com/mbbu-beep/splunk-snort-soc-lab/blob/main/documentation/video-demo.md) | [Cybersecurity Insights](https://github.com/mbbu-beep/cybersecurity-insights) | [LinkedIn](https://www.linkedin.com/in/mollybbussery/) |* 🔒
