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
