# Sysmon-Splunk-Cloud-Monitoring

# Sysmon + Splunk Cloud Monitoring Lab

## Overview

This lab focused on improving Windows endpoint visibility by installing **Sysmon** and forwarding its event data into **Splunk Cloud** for centralized monitoring and investigation.

Sysmon provides detailed telemetry about system activity such as process creation, parent processes, command-line execution, and other endpoint events. By integrating Sysmon with Splunk, I was able to collect this data in one location and use it to investigate activity occurring on Windows systems in my lab environment.

## Tools Used

* Microsoft Sysmon
* Windows Server
* PowerShell
* Splunk Universal Forwarder
* Splunk Cloud
* Active Directory Domain Controller (DC01)

---

## Step 1: Download and Extract Sysmon

I downloaded Sysmon from Microsoft Sysinternals and extracted the installation files onto the Windows system.

This provided the Sysmon executable required to install the service and begin collecting detailed Windows endpoint telemetry.

<img width="1204" height="662" alt="01-sysmon-extract-installation-files" src="https://github.com/user-attachments/assets/13e0f4c9-add8-49f5-9e1b-67bf53355ed0" />


---

## Step 2: Install Sysmon Using PowerShell

I opened PowerShell with administrative privileges and installed Sysmon on the Windows system.

```powershell
.\Sysmon64.exe -accepteula -i
```

After installation, I confirmed that Sysmon was successfully installed and running.

This allowed Windows to begin generating Sysmon events in the **Microsoft-Windows-Sysmon/Operational** event log.

<img width="1197" height="655" alt="02-sysmon-install-powershell" src="https://github.com/user-attachments/assets/ab9a67a1-0f32-4fbf-a5d9-37fd9ab93e58" />


---

## Step 3: Forward Sysmon Events to Splunk Cloud

After installing Sysmon, I configured the **Splunk Universal Forwarder** to collect Sysmon events and send them to Splunk Cloud.

Once the configuration was complete, I searched Splunk Cloud to confirm that Sysmon telemetry was being successfully received.

This created centralized visibility into activity occurring on the endpoint.

<img width="1904" height="1011" alt="03-sysmon-data-splunk-cloud" src="https://github.com/user-attachments/assets/21e08532-2279-4ed9-ac06-706a2596a96c" />


---

## Step 4: Investigate Process Activity in Splunk

With Sysmon events flowing into Splunk, I used the collected data to investigate process execution.

I reviewed information including:

* Programs that were executed
* The user who launched the process
* Parent processes
* Process IDs
* Command-line arguments
* Execution timestamps

This information can help identify suspicious behavior and understand how processes are launched within an environment.

<img width="1904" height="1011" alt="03-sysmon-data-splunk-cloud" src="https://github.com/user-attachments/assets/5b36eb40-244f-4069-88fc-17110c0a5a41" />


---

## Step 5: Deploy Sysmon to DC01 and Validate Log Collection

I also installed Sysmon on **DC01**, the Active Directory domain controller in my lab.

After installation, I configured the system to forward its Sysmon telemetry to Splunk Cloud and verified that events from DC01 were successfully being aggregated.

This demonstrated that the monitoring setup could collect endpoint telemetry from multiple Windows systems instead of monitoring only a single host.

![DC01 Sysmon Aggregation](images/05-sysmon-dc01-aggregation.png)

---

## Result

The completed configuration created a centralized endpoint-monitoring workflow:

```text
Windows Endpoint
      |
      v
    Sysmon
      |
      v
Splunk Universal Forwarder
      |
      v
 Splunk Cloud
      |
      v
Search / Investigation
```

By completing this lab, I gained practical experience with endpoint telemetry collection, centralized logging, Windows process investigation, and Splunk-based security monitoring.

## Key Skills Demonstrated

* Sysmon deployment and configuration
* Windows endpoint monitoring
* Splunk Universal Forwarder
* Splunk Cloud
* Centralized log aggregation
* Process investigation
* Parent/child process analysis
* Command-line analysis
* PowerShell
* Windows Server administration
* Security monitoring and troubleshooting




Step 1: Download and Extract Sysmon

I downloaded Sysmon from Microsoft Sysinternals and extracted the installation files onto the Windows system.

This provided the Sysmon executable required to install the service and begin collecting detailed Windows endpoint telemetry.

<img width="1204" height="662" alt="01-sysmon-extract-installation-files" src="https://github.com/user-attachments/assets/f66f0aed-79eb-4b6a-88d4-96da63218893" />



Step 2: Install Sysmon Using PowerShell

I opened PowerShell with administrative privileges and installed Sysmon on the Windows system.

.\Sysmon64.exe -accepteula -i

After installation, I confirmed that Sysmon was successfully installed and running.

This allowed Windows to begin generating Sysmon events in the Microsoft-Windows-Sysmon/Operational event log.
<img width="1197" height="655" alt="02-sysmon-install-powershell" src="https://github.com/user-attachments/assets/0246c3cd-c4b3-4cbb-8b96-fbe34491c54b" />





Step 3: Forward Sysmon Events to Splunk Cloud

After installing Sysmon, I configured the Splunk Universal Forwarder to collect Sysmon events and send them to Splunk Cloud.

Once the configuration was complete, I searched Splunk Cloud to confirm that Sysmon telemetry was being successfully received.

This created centralized visibility into activity occurring on the endpoint.
<img width="1904" height="1011" alt="03-sysmon-data-splunk-cloud" src="https://github.com/user-attachments/assets/0598b148-3fa5-4192-a8eb-c1724c6d64f1" />






Step 4: Investigate Process Activity in Splunk

With Sysmon events flowing into Splunk, I used the collected data to investigate process execution.

I reviewed information including:

Programs that were executed
The user who launched the process
Parent processes
Process IDs
Command-line arguments
Execution timestamps

This information can help identify suspicious behavior and understand how processes are launched within an environment.
<img width="1902" height="998" alt="04-sysmon-process-investigation" src="https://github.com/user-attachments/assets/3d4669e3-d36a-425c-8845-f26a9fee2bff" />






Step 5: Deploy Sysmon to DC01 and Validate Log Collection

I also installed Sysmon on DC01, the Active Directory domain controller in my lab.

After installation, I configured the system to forward its Sysmon telemetry to Splunk Cloud and verified that events from DC01 were successfully being aggregated.

This demonstrated that the monitoring setup could collect endpoint telemetry from multiple Windows systems instead of monitoring only a single host.
<img width="1889" height="879" alt="05-sysmon-dc01-aggregation" src="https://github.com/user-attachments/assets/886bfd00-ff12-44cc-93b6-670986a9ccce" />






Result

The completed configuration created a centralized endpoint-monitoring workflow:

Windows Endpoint
      |
      v
    Sysmon
      |
      v
Splunk Universal Forwarder
      |
      v
 Splunk Cloud
      |
      v
Search / Investigation

By completing this lab, I gained practical experience with endpoint telemetry collection, centralized logging, Windows process investigation, and Splunk-based security monitoring.

Key Skills Demonstrated
Sysmon deployment and configuration
Windows endpoint monitoring
Splunk Universal Forwarder
Splunk Cloud
Centralized log aggregation
Process investigation
Parent/child process analysis
Command-line analysis
PowerShell
Windows Server administration
Security monitoring and troubleshooting
