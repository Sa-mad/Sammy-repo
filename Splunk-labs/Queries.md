# Splunk Labs

This folder contains my personal learning projects and hands-on experiments using Splunk for Security Operations and Log Analysis.

## What I'm learning here:
- Basic Splunk Search Language (SPL)
- Creating dashboards and alerts
- Writing queries to detect suspicious activities
- Parsing logs and visualizing security data  

---

## Example SPL queries-

   1.  **Search failed logins**
```spl
index=main sourcetype=linux_secure "Failed password" 
| stats count by user, src, host

   2.  **Find top 10 IP addresses accessing the system**
```sp2
index=main sourcetype=apache:access 
| top limit=10 clientip.

   3.  **Detect multiple failed login attempts from the same IP**
```sp3 
index=main sourcetype=linux_secure "Failed password" 
| stats count by src_ip 
| where count > 5

   4.  **Search for suspicious PowerShell commands**
```sp4
index=windows sourcetype=WinEventLog:Security (CommandLine="*Invoke-Expression*" OR CommandLine="*IEX*")
| stats count by user, host



