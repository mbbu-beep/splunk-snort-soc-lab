# Unauthorized SSH Activity

## Purpose

The purpose of this test was to verify that an unauthorized SSH connection attempt could be identified in Linux authentication logs and reviewed in Splunk.

## Source and Target Systems

| System | Role | IP Address |
|---|---|---|
| `1Splunk` | SIEM used to collect and review Linux authentication events | `192.168.74.10` |
| `2Snort` | IDS sensor used to monitor network traffic | `192.168.74.20` |
| `3Windows` | Windows user workstation | `192.168.74.30` |
| `4Windows` | Domain/server system available for future testing | `192.168.74.40` |
| `5Linux` | Linux endpoint used to initiate the SSH attempt | `192.168.74.50` |
| `6Linux` | Linux testing machine targeted by the SSH attempt | `192.168.74.60` |

## Test Activity

An SSH connection was attempted from `5Linux` to `6Linux` using an invalid username.

```bash
ssh fakeuser@192.168.74.60
```

An incorrect password was entered to generate a failed SSH authentication event.

## Log Source

The failed SSH attempt was recorded in the Linux authentication log on the target system:

```text
/var/log/auth.log
```

The Splunk Universal Forwarder monitored the authentication log and forwarded the event to the `linux` index.

## Splunk Search

```spl
index=linux
```

The search results were narrowed to the time of the SSH attempt and reviewed for the invalid username, failed password message, source address, or SSH process information.

## Expected Evidence

The resulting event should contain information such as:

- The invalid username `fakeuser`
- A failed SSH authentication result
- The source IP address of `5Linux`
- The target system receiving the connection attempt
- The date and time of the attempt
- The SSH service or process associated with the event

## Analyst Interpretation

A failed SSH attempt does not automatically prove malicious activity. It may result from:

- A mistyped username or password
- An outdated saved credential
- A user connecting to the wrong system
- An automated process using invalid credentials
- Password guessing
- An unauthorized attempt to access the system

A security analyst should review the number and frequency of attempts, the source address, the usernames attempted, whether the source is recognized, and any related activity occurring before or after the event.

Repeated failures involving multiple usernames or rapid attempts from one source would be more concerning than a single failed login.

## Result

The test generated a failed SSH authentication event by attempting to access `6Linux` from `5Linux` with an invalid username and password.

The activity demonstrated that SSH authentication events were recorded in the Linux authentication log, forwarded to Splunk, and available for investigation in the `linux` index.

## Screenshot Evidence

*Screenshots will be added*
