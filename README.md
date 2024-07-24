# 🕵️ Azure Sentinel SIEM Setup 🕵️
## Overview 📖
We will set up Azure Sentinel, a cloud-based SIEM (Security Information and Event Management) solution, along with a virtual machine (VM) in Azure that will act as a honeypot. We will monitor logs from various attacks originating from different places worldwide.
- **What is SIEM?**
  It is an application that collects and analyzes log data to monitor critical activities. It provides real-time visibility, event monitoring and analysis, and automated alerts.
- **What is a Honeypot?**
  It is a security mechanism set up to detect, deflect, or study attempts at unauthorized use of information systems. It acts as a decoy, luring attackers to a system that appears to be an attractive target but is actually isolated and monitored.

## Steps 🛣️
### 1 - Creating a Virtual Machine in Azure 💻
The VM acts as a honeypot. This allows for the capture of attack patterns and behaviors, providing valuable insights into potential threats.<br>
It provides an isolated environment where you can safely monitor and analyze malicious activities without risking your main network and systems.

![vm](https://github.com/user-attachments/assets/0f0e1806-3a08-466c-be0f-2681d7001769)

### 2 - Disabling External and Windows Firewall 🧱
Disabling the firewall on the VM serves a specific purpose: to make the VM an attractive target for attackers.

### 3 - Creating Log Analytics Workspace 🤔
The Log Analytics Workspace serves as a central repository for collecting and analyzing log data from various sources, including the VM honeypot.<br>
We trained this Log Analytics Workspace (LAW) with a file that contains the geolocation information of the intruder. This was made possible by using an API from the ipgeolocation website.<br>
The process involved extracting IP addresses from the VM honeypot logs using a PowerShell script, querying the IP geolocation API to obtain geographical data, and then feeding this data into the Log Analytics Workspace.

![law](https://github.com/user-attachments/assets/bde1d9e1-9dcb-42d0-89c8-28a47406764c)

### 4 - Integrate Azure Sentinel 🌎
Integrating with Azure Sentinel to obtain the location of attempted intrusions.
By integrations with the ipgeolocation API, Sentinel can provide insights into the geographic location of attackers.

![map](https://github.com/user-attachments/assets/72e6d5e4-87aa-4b6b-9647-82f231a35a00)


## Conclusion 🖇️
Throughout this setup, we have successfully implemented Azure Sentinel along with a virtual machine honeypot to monitor and analyze security threats.<br>
During the observation period, we detected several intrusion attempts on the virtual machine, including brute force attacks.<br>
The insights gained from these activities were captured and analyzed in the Log Analytics Workspace, enriched with geolocation data from the IP addresses involved in the attacks. This comprehensive setup not only highlights the importance of proactive monitoring and analysis but also provides valuable information on the origins and methods of potential threats, enhancing our ability to safeguard our network and systems against future security breaches.
