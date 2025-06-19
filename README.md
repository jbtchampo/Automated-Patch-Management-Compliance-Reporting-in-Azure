# Automated-Patch-Management-Compliance-Reporting-in-Azure
Simulate a real-world enterprise patching strategy using:  Azure Update Management to schedule and deploy updates  Automation via PowerShell or Log Analytics Agent  Kusto Query Language (KQL) to report compliance status

![image](https://github.com/user-attachments/assets/5d1a3871-c873-46d0-bd8e-359028ef7a4e)



# 🔧 Patch Management Simulation in Azure

This project demonstrates how to implement automated patch deployment and compliance reporting using Azure Update Management. It includes scheduling monthly updates, applying them to virtual machines, and using Kusto Query Language (KQL) for compliance tracking.

## 🎯 Project Goals

- Automate patch deployment to Azure VMs
- Schedule recurring monthly patch cycles
- Monitor update success and failures in Azure Automation
- Generate compliance reports using KQL in Log Analytics

## 🛠️ Lab Environment

| Component               | Description                                  |
|------------------------|----------------------------------------------|
| Azure VMs              | Target machines for patching (Windows/Linux) |
| Log Analytics Workspace| Collect update and status logs               |
| Azure Automation       | Schedule and manage update deployments       |
| Update Management      | The actual patching engine                   |
| KQL / Log Analytics    | Reporting and dashboards                     |

## 🔧 Setup Steps

### 1. Provision Azure VMs
Create and configure 1–3 VMs in Azure, ensuring the Log Analytics agent is installed.

### 2. Create Log Analytics Workspace
Use Azure Portal to set up a new workspace and connect it to your VMs.

### 3. Enable Update Management
- Link an Automation Account to your workspace
- Enable Update Management and select your target VMs

### 4. Schedule Patch Deployment
- Create a deployment schedule for monthly patching
- Choose classifications (e.g., Security, Critical)
- Define reboot options and schedule

## 📈 Compliance Reporting Using KQL

### Get Update Status
```kusto
Update
| where TimeGenerated > ago(30d)
| summarize count() by Computer, Classification, UpdateState
```

### Find Devices Missing Security Patches
```kusto
Update
| where UpdateState == "Needed" and Classification == "Security Updates"
| summarize count() by Computer
```

## ✅ Outcomes

- Monthly patch jobs deployed successfully
- Real-time compliance data gathered via KQL
- Insights into update trends and risk exposure

## ✨ Optional Enhancements

- Trigger alerts on patch failure using Azure Monitor
- Create a Power BI dashboard using Log Analytics data
- Automate VM group tagging with PowerShell or Logic Apps

---

**Created by:** Jean Berlin Tchampo  
**LinkedIn:** [linkedin.com/in/jeanberlintchampo1](https://www.linkedin.com/in/jeanberlintchampo1)
