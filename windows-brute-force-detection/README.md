# Windows Brute Force Detection using Splunk

## 📌 Project Overview

This project is a hands-on SOC lab focused on detecting and investigating potential Windows brute-force attacks using Splunk.

The lab demonstrates how Windows Security Event Logs can be collected, searched, analyzed, and visualized to identify repeated failed authentication attempts.

## 🎯 Objectives

- Monitor Windows Security Event Logs
- Detect failed authentication attempts
- Investigate Windows Event ID 4625
- Analyze repeated login failures
- Identify suspicious authentication patterns
- Create a SOC monitoring dashboard in Splunk
- Practice SIEM-based investigation

## 🛠️ Technologies Used

- Splunk
- Windows Security Event Logs
- PowerShell
- Sysmon
- SPL
- SIEM
- SOC Monitoring

## 🔎 Detection

The primary event investigated in this lab was:

### Event ID 4625

Windows Event ID 4625 represents a failed logon attempt.

Repeated failed authentication attempts can be investigated for possible:

- Brute-force attacks
- Password guessing
- Unauthorized access attempts
- Misconfigured services
- Suspicious authentication activity

Event ID 4625 by itself does not prove a brute-force attack. Additional context such as source IP, username, timing, frequency, and related events should be investigated.

## 🔍 Splunk Investigation

The following SPL query was used to identify Windows failed logon events:

```spl
index=main sourcetype="XmlWinEventLog:Security" EventCode=4625
```

To identify accounts and source IPs generating repeated failed logons:

```spl
index=main sourcetype="XmlWinEventLog:Security" EventCode=4625
| stats count by user, src_ip
| sort - count
```

These searches help identify repeated authentication failures and provide useful information for further SOC investigation.

## 📊 SOC Dashboard

A Splunk dashboard was created to monitor Windows failed authentication activity.

The dashboard provides visibility into:

- Failed logon activity
- Authentication attempts over time
- User accounts
- Source IP addresses
- Potential suspicious login patterns

## 🧪 Investigation Workflow

1. Generate or identify failed authentication attempts.
2. Validate Windows Security events.
3. Search the events in Splunk.
4. Analyze authentication patterns.
5. Identify repeated failed logons.
6. Visualize the activity using a Splunk dashboard.
7. Investigate whether the activity could represent brute-force behavior.

## 🧠 Skills Demonstrated

- SIEM
- Splunk
- SPL
- Windows Event Log Analysis
- Event ID 4625 Investigation
- Authentication Monitoring
- Threat Detection
- SOC Investigation
- Dashboard Development
- PowerShell

## ⚠️ Disclaimer

This project was created in a controlled home lab environment for educational and cybersecurity learning purposes.

No real credentials or sensitive production data are included.

## 👨‍💻 Author

**Tanmay Mayekar**
Cybersecurity / SOC Analyst Enthusiast

Skills: Splunk | SIEM | Windows Security | PowerShell | Threat Detection

Cybersecurity / SOC Analyst Enthusiast

Skills: Splunk | SIEM | Windows Security | PowerShell | Threat Detection
