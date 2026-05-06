# Project 2: SIEM Configuration & Log Ingestion

## Objective
To deploy a cloud-native Security Information and Event Management (SIEM) solution and establish a data pipeline to ingest, parse, and monitor security logs from a live Linux target.

## Skills & Tools Demonstrated
* **SIEM Platform:** Microsoft Sentinel
* **Data Management:** Azure Log Analytics Workspace
* **Log Sources:** Linux Syslog (`auth.log`)
* **Core Concepts:** Log Ingestion, Data Connectors, Security Monitoring, Cloud Telemetry.

## The Execution
With the vulnerable `Honeypot-VM` exposed to the internet, the next step was to build the defensive monitoring infrastructure to capture the incoming attacks. 

1. **Log Analytics Workspace:** Deployed an Azure Log Analytics Workspace to serve as the centralized database for all security telemetry.
2. **Data Connectors:** Configured Microsoft Sentinel and linked it to the workspace. I utilized Azure data connectors to establish a continuous pipeline between the `Honeypot-VM` and the SIEM.
3. **Log Parsing:** Specifically targeted the Linux `/var/log/auth.log` directory. This ensured that every time an automated bot or threat actor attempted to brute-force the SSH service, the failed login attempt was immediately ingested into Sentinel for real-time analysis.

## Visual Documentation

<img width="1772" height="822" alt="Screenshot 2026-05-06 at 4 12 51 PM" src="https://github.com/user-attachments/assets/cd501844-cfd5-483a-b08e-7c01fdff3e87" />
