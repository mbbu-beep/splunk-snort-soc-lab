# Port Scanning

## Purpose

The purpose of this test was to determine whether network reconnaissance activity could be generated, detected, and analyzed within the lab.

## Source and Target Systems

| System | Role | IP Address |
|---|---|---|
| `1Splunk` | SIEM used to review collected network events |
| `2Snort` | IDS sensor used to monitor network traffic |
| `3Windows` |  |
| `4Windows` |  |
| `5Linux` | Linux endpoint used as the scan target |
| `6Linux` | Attack and testing machine used to run the scan |




`6Linux` used the IP address `192.168.74.60`, while the `5Linux` endpoint used `192.168.74.50`.

## Test Activity

Nmap was run from `6Linux` against the `5Linux` endpoint within the isolated VMware network.

```bash
nmap 192.168.74.50
```

The scan checked the target system for open ports and available services. The final report identifies `6Linux` as the source of the Nmap activity and describes the purpose as testing whether network reconnaissance could be detected and analyzed. :contentReference[oaicite:1]{index=1}

## Log and Alert Sources

The resulting network activity could be reviewed through:

- Snort alert data collected from `2Snort`
- The Splunk `network` index
- The Nmap results displayed on `6Linux`

Snort was configured to forward alert data to the `network` index in Splunk. :contentReference[oaicite:2]{index=2}

## Splunk Search

```spl
index=network
```

The search results were narrowed using the appropriate time range to locate activity associated with the port scan.

## Expected Evidence

The test should produce evidence showing:

- Nmap scanning the target host
- Open or responding ports identified by Nmap
- Network traffic originating from `6Linux`
- A related Snort alert, when the traffic matched an enabled rule
- Searchable network events in Splunk

## Analyst Interpretation

Port scanning is commonly used to identify active hosts, open ports, and available services before attempting further access.

A port scan does not automatically prove malicious activity. It may result from:

- Authorized vulnerability testing
- Network troubleshooting
- Asset discovery
- Security monitoring tools
- Unauthorized reconnaissance

A security analyst would review the source IP address, destination system, ports scanned, timing, frequency, and whether the activity was authorized.

## Result

The test generated port-scanning traffic from `6Linux` within the controlled lab environment. The activity demonstrated how Nmap can be used for reconnaissance and how related network data can be reviewed through Snort and the Splunk `network` index.

## Screenshot Evidence

*Screenshot to be added showing the Nmap scan, related Snort alert, or corresponding results in Splunk.*
