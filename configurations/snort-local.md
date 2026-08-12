# Snort Local Rule

This custom Snort rule was used in the controlled VMware SOC lab to detect ICMP traffic directed toward the protected network.

## Rule

```conf
alert icmp any any -> $HOME_NET any (msg:"ICMP Ping Detected"; sid:1000001; rev:1;)
```

## Rule Breakdown

| Element | Meaning |
|---|---|
| `alert` | Tells Snort to generate an alert when the rule conditions are met. |
| `icmp` | Specifies that the rule applies to ICMP traffic, such as ping requests. |
| `any any` | Allows traffic from any source IP address. The second `any` represents the source port field, although ICMP does not use ports in the same way as TCP or UDP. |
| `->` | Indicates the direction of traffic being inspected. |
| `$HOME_NET` | Represents the protected network configured in Snort. |
| `any` | Allows traffic directed to any destination port field. |
| `msg:"ICMP Ping Detected"` | Defines the message that appears when the rule generates an alert. |
| `sid:1000001` | Assigns a unique Snort rule identifier to the custom rule. |
| `rev:1` | Identifies this as revision 1 of the rule. |

## Purpose

The rule was used to confirm that Snort could detect ICMP traffic, generate an alert, and send the resulting event to the Splunk `network` index.


---

### *About This Project*

**Created by Molly Bentley Ussery | Senior Capstone Project | July 2026**

This project documents hands-on cybersecurity work completed in a six-system Splunk + Snort SOC lab, including security monitoring, detection, attack simulation, investigation, and analyst documentation.

🔗 **Quick Links** *| [Cybersecurity Portfolio](https://mbbu-beep.github.io/) | [Project Home](https://github.com/mbbu-beep/splunk-snort-soc-lab) | [Video Demo](https://github.com/mbbu-beep/splunk-snort-soc-lab/blob/main/documentation/video-demo.md) | [Cybersecurity Insights](https://github.com/mbbu-beep/cybersecurity-insights) | [LinkedIn](https://www.linkedin.com/in/mollybbussery/) |* 🔒
