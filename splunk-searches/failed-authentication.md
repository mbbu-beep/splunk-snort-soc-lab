# Failed Authentication Attempts

## Purpose

The purpose of this test was to determine whether repeated failed Linux login attempts were recorded and forwarded to Splunk.

## Source System

The activity was generated from `6Linux`, the attack and testing machine.

## Test Activity

Multiple attempts were made to log in to a Linux endpoint using an invalid username or incorrect password.

These attempts generated authentication records in:

```text
/var/log/auth.log
```

The Splunk Universal Forwarder monitored this log and sent the activity to the `linux` index.

## Splunk Search

```spl
index=linux
```

The search results were refined using the event time range and authentication-related terms to locate the failed login activity.

## Analyst Interpretation

Repeated authentication failures may indicate:

- A user entering an incorrect password
- An outdated saved credential
- An unauthorized access attempt
- Password guessing or brute-force activity

The failed events alone do not prove malicious activity. A security analyst would review the source system, username, timing, number of attempts, and surrounding events before reaching a conclusion.

## Result

The test confirmed that Linux authentication failures were recorded in the authentication log, forwarded to the `linux` index, and searchable in Splunk.
