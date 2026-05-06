# Project 1: Cloud Infrastructure & Honeypot Deployment

## Objective
To provision and configure an enterprise-grade cloud environment in Microsoft Azure, deploying a publicly accessible Linux virtual machine to serve as a honeypot for attracting and analyzing live threat actor activity.

## Skills & Tools Demonstrated
* **Cloud Platform:** Microsoft Azure (IaaS)
* **Operating System:** Ubuntu Linux
* **Core Concepts:** Cloud Infrastructure Provisioning, Network Security Groups (NSGs), Public/Private IP Routing, Virtual Networks (VNet).

## The Execution
To build the foundation for this lab series, I assumed the role of a Cloud Security Architect. The objective was to create a vulnerable environment that would deliberately attract malicious internet traffic without compromising a secure corporate network.

1. **Resource Group Creation:** Established a dedicated Azure Resource Group to logically contain and manage all lab assets.
2. **Virtual Machine Deployment:** Provisioned a standard Ubuntu Linux virtual machine (`Honeypot-VM`). 
3. **Network Configuration:** Configured the Azure Network Security Group (NSG) to strip away default firewalls. I intentionally exposed critical ports (such as Port 22 for SSH and Port 80 for HTTP) to the public internet. This ensured the server would act as a highly visible target for automated internet scanners and brute-force bots.

## Visual Documentation
The image below validates the successful deployment of the target infrastructure in the Azure cloud environment, confirming its active status and public IP assignment.

*(Drag and drop your screenshot of the Azure Portal showing the Honeypot-VM here)*
<img width="864" height="695" alt="Screenshot 2026-05-06 at 3 46 05 PM" src="https://github.com/user-attachments/assets/05460cd7-ac79-491d-92a1-c371d9b3af0c" />


