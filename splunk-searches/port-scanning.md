# Port Scanning

## Purpose

The purpose of this test was to determine whether network reconnaissance activity could be generated, detected, and analyzed within the lab.

## Source and Target Systems

| System | Role | IP Address |
|---|---|---|
| `1Splunk` | SIEM used to review collected network events | 192.168.74.10 |
| `2Snort` | IDS sensor used to monitor network traffic | 192.168.74.20 |
| `3Windows` | Windows User Workstation | 192.168.74.30 |
| `4Windows` | Domain/Server | 192.168.74.40 |
| `5Linux` | Linux endpoint used as the scan target | 192.168.74.50 |
| `6Linux` | Attack and testing machine used to run the scan | 192.168.74.60 |


## Test Activity

Nmap was run from 6Linux against the 5Linux endpoint to identify open ports and available services within the isolated VMware network.

```bash
nmap 192.168.74.50
```

The scan checked the target system for open ports and available services. The final report identifies `6Linux` as the source of the Nmap activity and describes the purpose as testing whether network reconnaissance could be detected and analyzed. 

## Log and Alert Sources

The resulting network activity could be reviewed through:

- Snort alert data collected from `2Snort`
- The Splunk `network` index
- The Nmap results displayed on `6Linux`

Snort was configured to forward alert data to the `network` index in Splunk.

## Splunk Search

```spl
index=network
```

The search results were narrowed using the appropriate time range to locate activity associated with the port scan.



