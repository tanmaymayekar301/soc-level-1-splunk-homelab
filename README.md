# SOC Level 1 Security Monitoring Homelab

## Project Overview

This project demonstrates a SOC Level 1 security monitoring homelab built using Splunk Enterprise to analyze Windows authentication activity.

The goal of this lab is to simulate common SOC analyst monitoring tasks, including detecting failed login attempts, successful logins, suspicious authentication behavior, and source IP activity.

## Objectives

* Monitor Windows authentication events.
* Detect failed login attempts.
* Identify successful logins.
* Detect multiple failed login attempts.
* Identify successful logins after multiple failures.
* Analyze source IP addresses associated with failed authentication attempts.
* Build a SOC monitoring dashboard in Splunk Enterprise.

## Lab Environment

**SIEM:** Splunk Enterprise

**Data Source:** Windows authentication events

**Key Windows Event IDs:**

| Event ID | Description      |
| -------- | ---------------- |
| 4624     | Successful logon |
| 4625     | Failed logon     |

## SOC Detection Use Cases

### 1. Multiple Failed Login Attempts

This detection identifies accounts with multiple failed authentication attempts, which may indicate:

* Brute-force activity
* Password guessing
* Unauthorized access attempts

### 2. Successful Login After Multiple Failed Attempts

This detection identifies accounts where a successful login occurs after multiple failed attempts.

This behavior can be suspicious because it may indicate:

* A successful brute-force attempt
* Credential compromise
* Unauthorized account access

### 3. Failed vs Successful Logins

This visualization compares successful and failed authentication events to provide a quick overview of authentication activity.

### 4. Top Source IPs with Failed Login Attempts

This detection identifies the source IP addresses generating failed login attempts.

Analysts can use this information to investigate:

* Suspicious hosts
* Repeated authentication failures
* Potential brute-force sources

### 5. Failed Login Attempts Over Time

This visualization tracks failed authentication activity over time and helps identify unusual spikes.

## Splunk Dashboard Panels

The SOC Level 1 Security Monitoring Dashboard includes:

1. Successful Login After Multiple Failed Attempts
2. Multiple Failed Login Attempts
3. Failed vs Successful Logins
4. Top Source IPs with Failed Login Attempts
5. Multiple Failed Login Attempts by Account
6. Successful Logins After Failed Attempts
7. Top 10 Source IPs with Failed Login Attempts
8. Failed Login Attempts Over Time
9. Total Failed Login Attempts
10. Total Successful Logins

## Dashboard Results

During testing, the dashboard detected:

* **8 Failed Login Attempts**
* **183 Successful Logins**

These results demonstrate how Splunk can be used to monitor authentication activity and provide security visibility for SOC analysts.

## Example SPL Queries

### Failed Login Attempts

```spl
EventCode=4625
| stats count AS failed_attempts
```

### Successful Logins

```spl
EventCode=4624
| stats count AS successful_logins
```

### Failed Login Attempts by Account

```spl
EventCode=4625
| stats count AS failed_attempts BY Account_Name
| sort - failed_attempts
```

### Top Source IPs with Failed Login Attempts

```spl
EventCode=4625
| stats count AS failed_attempts BY src_ip
| sort - failed_attempts
| head 10
```

### Failed Login Attempts Over Time

```spl
EventCode=4625
| timechart count AS failed_attempts
```

## Skills Demonstrated

* Splunk Enterprise
* SIEM Monitoring
* SPL (Search Processing Language)
* Windows Event Log Analysis
* Authentication Monitoring
* Failed Login Detection
* Brute-Force Detection Concepts
* Source IP Analysis
* Security Dashboard Creation
* SOC Level 1 Investigation Skills

## Screenshots

Dashboard screenshots will be added to the `screenshots` directory.

## Future Improvements

Possible improvements for this homelab include:

* Creating real-time alerts for repeated failed logins
* Adding brute-force detection thresholds
* Integrating additional Windows event sources
* Adding PowerShell logging
* Monitoring process creation events
* Integrating Sysmon
* Creating incident investigation workflows
* Mapping detections to the MITRE ATT&CK framework

## Conclusion

This project demonstrates the core workflow of a SOC Level 1 analyst using Splunk Enterprise to monitor authentication events and investigate potentially suspicious activity.

The homelab provides hands-on experience with SIEM monitoring, SPL queries, Windows event analysis, dashboard development, and basic security detection use cases.
