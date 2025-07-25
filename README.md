# Windows Log Monitoring with Splunk Cloud

This is a real-world cybersecurity and DevOps project that uses the **Splunk Universal Forwarder** to collect logs from a local **Windows 10/11** system and forward them to **Splunk Cloud** for centralized log analysis and monitoring.

---

## 🎯 Project Objective

To demonstrate how logs can be forwarded from a local Windows endpoint to a cloud-based SIEM (Splunk Cloud) for:

- Centralized log management  
- Security event detection  
- Dashboard creation and alerting  
- Hands-on experience with Splunk Search Processing Language (SPL)

---

## 📦 Use Case

- Forward Windows Event Logs to Splunk Cloud:
  - Security
  - System
  - Application
  - PowerShell
  - Sysmon (via Sysmon config)
- Monitor endpoint behavior:
  - User logins (successful and failed)
  - Privilege escalation attempts
  - Script and PowerShell execution
- Visualize data using dashboards and panels
- Enable real-time threat detection and incident investigation

---

## 🛠️ Tools & Technologies

- Windows 10/11
- Splunk Universal Forwarder
- Splunk Cloud Trial
- Sysmon (for enhanced logging)
- Search Processing Language (SPL)
- Event Viewer & PowerShell

---

## 📊 Sample Dashboards & Visualizations

Here are some example panels included in the Splunk dashboard:

### 🔐 Login Activity Panel

- **Failed Logins per User**
  - Helps detect brute-force login attempts.
  ![Failed Logins](screenshots/Failed%20Logins.JPG)
- **Successful Logins per User**
  - Tracks legitimate user access patterns.
    ![Successful Logins](screenshots/Successful%20Logins%20by%20user.JPG)

### 🚨 Privilege Escalation Events

- Identifies users who triggered Event ID 4672 (Special Privileges Assigned).
- Useful for detecting unauthorized administrative access attempts.
  ![Priviledge Escalation](screenshots/Priviledge%20Escalation%20Events.JPG)

### 🔢 Top Event Codes

- Displays the most frequent event codes logged.
- Can be used to monitor:
  - Repeated login failures (4625)
  - Service installations
  - Security policy changes
![Top Events](screenshots/Top%20Event%20Codes.JPG)
    

### 🧠 Script Execution Tracking

- Uses Event ID 4104 (PowerShell logs) and Sysmon logs.
- Flags suspicious command-line or script activity.

### 🔍 Log Search

- Uses the Splunk Search & Reporting App.
- Enables ad-hoc querying using SPL to filter and investigate raw log events.

![Top Events](screenshots/LogSearches.JPG)
---

## 🚀 Getting Started

1. Install the [Splunk Universal Forwarder](https://www.splunk.com/en_us/download/universal-forwarder.html) on your Windows system.
2. Enable the required Windows Event Log channels.
3. Set up forwarder credentials using your Splunk Cloud deployment.
4. Configure inputs.conf to monitor event logs.
5. Verify connectivity on port 9997.
6. Visualize the logs in Splunk Cloud using dashboards or SPL queries.

---

## ✅ Sample SPL Queries

```spl
index=main sourcetype="WinEventLog:Security" EventCode=4625
| stats count by user, host
| sort -count

index=main sourcetype="WinEventLog:Security" EventCode=4672
| table _time, user, host

index=main sourcetype="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational" EventCode=4104
| table _time, user, Message

📌 Author
Munyaradzi Sydney Chinzvende
Empowering African SMEs with Secure, Scalable Software | .NET & Azure Developer | Cybersecurity Advocate | (https://www.linkedin.com/in/chinzvendesm/)

⭐ GitHub Repo Purpose
This project is part of my cybersecurity portfolio to showcase hands-on skills in:

Endpoint monitoring
SIEM integration
Log correlation
Visualization using Splunk


Feel free to fork or use it as a base for your own monitoring setup.

















# windows-log-monitoring-splunk
Real-world cybersecurity monitoring project using the Splunk Universal Forwarder to collect and forward Windows system logs to Splunk Cloud for centralized analysis.

# Windows to Splunk Cloud Monitoring

A real-world cybersecurity and DevOps project that collects and forwards logs from a Windows 10/11 endpoint to **Splunk Cloud Trial** using the **Splunk Universal Forwarder**. Designed to showcase centralized log collection, SIEM integration, and threat detection with dashboards and alerts.

## Use Case

- Forward logs (Security, System, Application, PowerShell, Sysmon) from a local Windows PC
- Centralized monitoring using Splunk Cloud
- Visualize endpoint activity (logins, privilege escalation,script execution)

## Sample Dashboards

Here are some example visualizations included in this project:

### Login Activity Panel
Shows failed logon attempts per user.


Shows successful logins by user


### Priviledge Escalation Events
Detects priveledge escalation events by accounts so that we see if an unathorized account is gainging unathorized access.


### Top Event Codes
Here we have an overview of the most frequently triggered events. This dashboard can help us quickly identify bruteforce attacks or DDoS attack.


### Log Search
This is the Splunk Search and Reporting App which enable us to search for specific events.


