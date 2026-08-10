# Splunk Enterprise – Windows Forwarder Home Lab
A complete hands-on lab demonstrating how to forward Windows event logs into Splunk Enterprise using the Universal Forwarder. This project showcases endpoint monitoring, log ingestion, detection engineering, and SOC analysis fundamentals.

---

## 🔥 Project Overview
This lab simulates a real SOC workflow:

- Deploying a Splunk Enterprise instance  
- Installing and configuring the Windows Universal Forwarder  
- Forwarding Security, System, Application, and Sysmon logs  
- Creating indexes and inputs  
- Building dashboards and detections  
- Validating log flow end-to-end  

It is designed as a practical home lab for SOC analysts, blue teamers, and students learning SIEM fundamentals.

---

## 🧩 Architecture Diagram (Text-Based)
[ Windows Endpoint ]
|
|  Universal Forwarder (UF)
|
[ Splunk Enterprise Server ]
|
|  Indexing + Search Head
|
[ Dashboards | Alerts | Detections ]


---


---

## 🚀 Lab Setup Guide

### 1. Install Splunk Enterprise
- Deploy Splunk Enterprise on a VM or local machine  
- Create required indexes (e.g., `win_logs`, `sysmon`)  
- Ensure port **9997** is open for forwarder ingestion  

### 2. Install Windows Universal Forwarder
- Download the UF installer  
- Install using default settings  
- Add the Splunk Enterprise server as the receiving indexer  

### 3. Configure Forwarder Inputs
Place your `inputs.conf` in:
C:\Program Files\SplunkUniversalForwarder\etc\system\local\



Recommended inputs:
- Windows Security logs  
- Windows System logs  
- Windows Application logs  
- Sysmon operational logs  

### 4. Configure Forwarder Outputs
Add your indexer details in `outputs.conf`:
[tcpout]
defaultGroup = default-autolb-group

[tcpout:default-autolb-group]
server = <your-splunk-ip>:9997

### 5. Validate Log Flow
In Splunk Search:
index=win_logs OR index=sysmon | stats count by host sourcetype



You should see events flowing from your Windows endpoint.

---

## 🛡️ Detection Engineering
This lab includes example detections such as:

- Suspicious process creation  
- PowerShell execution  
- Failed logon attempts  
- Sysmon-based event correlation  

Stored in:
/detections/

---

## 📊 Dashboards
Custom dashboards visualize:

- Event volume  
- Host activity  
- Sysmon telemetry  
- Security log anomalies  

Stored in:
/dashboards/

Code

---

## 💡 Why This Project Matters
This home lab demonstrates real SOC skills:

- Endpoint monitoring  
- Log ingestion pipelines  
- SIEM configuration  
- Detection engineering  
- Dashboard creation  
- Incident analysis  

It is ideal for cybersecurity portfolios, interviews, and hands-on learning.

---

## 🛠️ Skills Demonstrated
- Splunk Enterprise Administration  
- Universal Forwarder Configuration  
- Windows Event Logging  
- Sysmon Integration  
- Detection Engineering  
- SIEM Dashboarding  
- SOC Analysis  

---

## 🔧 Future Improvements
- Add Sysmon configuration file  
- Add Sigma → Splunk rule conversions  
- Add more dashboards  
- Add ingestion for Linux endpoints  
- Add correlation searches  

---

## 👤 Author
**Jaden Julius Mascarenhas**  
Cybersecurity & SOC Analyst | Blue Team | Detection Engineer
