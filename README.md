Honeypot Deployment and Monitoring Project
Overview

This project focuses on creating and monitoring a honeypot in Microsoft Azure to proactively understand attack techniques and detect threats. The primary goal is to set up a simulated environment resembling an internet-facing host to attract potential attackers and gather insights into their tactics. The project involves deploying an Azure Virtual Machine, configuring Log Analytics Workspace, and implementing a custom PowerShell script to analyze failed RDP login attempts.
Project Steps


Step 1: Build Azure Virtual Machine

  Create an Azure account and access the Azure portal at portal.azure.com.
    Navigate to "Virtual Machines" and create a new VM with specifications resembling the target host.
    Configure the VM settings, including region, OS (Windows 10 Pro), and RDP port (3389).
    Set up inbound rules to allow RDP traffic.
    Deploy the virtual machine.


Step 2: Create Log Analytics Workspace

   Create a Log Analytics Workspace (LAW) for ingesting and analyzing logs.
    Enable Microsoft Defender For Cloud, configure environment settings, and ensure data collection is active.
    Connect the LAW to the virtual machine.


Step 3: Connect and Configure Virtual Machine

   Copy the public IP address of the VM and use it to connect via RDP.
    Access Event Viewer to analyze 'Audit Failure' logs under 'Security' in Windows Logs.
    Ensure domain, private, and public firewalls are disabled for ICMP echo requests.
    Implement a custom PowerShell script to extract failed RDP login data and geolocation information.


Step 4: Set up Custom Log Files and Query

  Create a custom log file from the extracted failed RDP log in Log Analytics Workspace.
    Build a query to parse log files and extract relevant data for visualization.
    Run the query to obtain structured data.


Step 5: Construct Sentinel Map

   Navigate to Microsoft Sentinel, create a new workbook, and add a query widget.
    Paste the custom query to visualize the geographical distribution of potential attackers.
    Observe the Sentinel map for real-time insights into failed RDP login attempts.


Additional Notes

  Ensure proper configuration of firewalls and security groups for the honeypot VM.
    The provided PowerShell script can be found in the project repository: Custom_Security_Log_Exporter.ps1.
    Obtain a free API key from ipgeolocation.io for accurate geolocation data.

Conclusion

This project provides practical experience in deploying a honeypot, analyzing logs, and visualizing threat data. The Sentinel map illustrates the global distribution of potential attackers and their persistence in attempting failed RDP logins. The insights gained contribute to a proactive cybersecurity approach.

Author
Esteban Valverde
