# Azure SOC Homelab

## Overview

This project documents the deployment of a cloud-based Security Operations Center (SOC) environment within Microsoft Azure. The lab was built to gain hands-on experience with enterprise identity management, Active Directory administration, cloud security monitoring, and SIEM operations using Microsoft Sentinel.

The environment simulates a small enterprise network where Windows authentication events are collected, analyzed, and investigated through Microsoft Sentinel to better understand the responsibilities of a Security Operations Center (SOC) analyst.

---

## Objectives

- Deploy a Windows Server virtual machine in Microsoft Azure
- Configure Active Directory Domain Services (AD DS)
- Integrate Microsoft Entra ID for identity management
- Configure Microsoft Sentinel as the SIEM platform
- Collect Windows Security Event Logs through Log Analytics
- Create detection rules for common security events
- Investigate alerts using Kusto Query Language (KQL)

---

## Environment Architecture

```text
Microsoft Azure
│
├── Resource Group
│
├── Virtual Network
│
├── Windows Server Virtual Machine
│     └── Active Directory Domain Services
│
├── Microsoft Entra ID
│
├── Log Analytics Workspace
│
└── Microsoft Sentinel
      ├── Analytics Rules
      ├── Incidents
      └── Workbooks
```

---

## Technologies Used

- Microsoft Azure
- Microsoft Sentinel
- Microsoft Entra ID
- Active Directory Domain Services
- Windows Server
- Azure Monitor
- Log Analytics Workspace
- Kusto Query Language (KQL)
- PowerShell
- Remote Desktop Protocol (RDP)

---

## Features

- Active Directory domain deployment
- Cloud identity integration with Microsoft Entra ID
- Centralized Windows Security Event Log collection
- Security monitoring through Microsoft Sentinel
- Custom KQL queries for log analysis
- Authentication monitoring
- Incident investigation
- Analytics rule configuration

---

## Sample KQL Query

Retrieve failed Windows logon attempts:

```kql
Event
| where EventLog == "Security"
| where EventID == 4625
| summarize Attempts = count() by bin(TimeGenerated, 5m)
| render timechart
```

Retrieve successful logons:

```kql
SecurityEvent
| where EventID == 4624
| project TimeGenerated, Computer, Account
```

Retrieve newly created user accounts:

```kql
SecurityEvent
| where EventID == 4720
```

<img width="1305" height="769" alt="soc-lab-1" src="https://github.com/user-attachments/assets/0fb92fb2-917f-4c8e-aba6-fbd91ab34ad3" />


---

## Skills Demonstrated

- Azure Administration
- Security Information and Event Management (SIEM)
- Active Directory Administration
- Microsoft Entra ID
- Identity and Access Management (IAM)
- Windows Security Logging
- Log Analytics
- Kusto Query Language (KQL)
- Security Monitoring
- Threat Detection
- Incident Investigation

---

## Lessons Learned

Building this environment provided practical experience with Microsoft's security ecosystem and improved my understanding of:

- Azure resource deployment
- Active Directory configuration
- Cloud identity management
- Windows event logging
- Security event ingestion
- KQL query development
- SIEM configuration
- SOC investigation workflows

---

## Future Improvements

- Integrate Microsoft Defender for Endpoint
- Configure automated incident response using Logic Apps
- Deploy additional Windows endpoints
- Develop custom Sentinel Workbooks
- Expand analytics rules using MITRE ATT&CK techniques
- Simulate attack scenarios for detection validation

---

## Disclaimer

This homelab was created for educational purposes to gain hands-on experience with Microsoft Azure, Active Directory, Microsoft Entra ID, and Microsoft Sentinel. It is intended to demonstrate foundational Security Operations Center (SOC) concepts and cloud security practices.
