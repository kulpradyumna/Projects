# Project 5: Web Application Vulnerability Scanning & Live Remediation

## Objective
To configure a remote attack machine, execute a Dynamic Application Security Testing (DAST) scan against a cloud-hosted web server, and manually deploy live patches to remediate the discovered misconfigurations.

## Skills & Tools Demonstrated
* **Tools:** OWASP ZAP, Apache, Ubuntu Linux, SSH, curl
* **Environment:** Microsoft Azure Virtual Machines (Attacker-VM & Honeypot-VM)
* **Concepts:** DAST, UI Redressing (Clickjacking), Information Disclosure, Server Hardening

## The Architecture
* **Attacker Machine:** Ubuntu VM configured with an XFCE lightweight desktop and xRDP for remote GUI access.
* **Target:** A default Ubuntu Apache web server (`Honeypot-VM`) deployed in Azure. 

<img width="468" height="348" alt="image" src="https://github.com/user-attachments/assets/bea82c54-14c0-498d-a41e-6dfcd75654b2" />


## Phase 1: The Attack (Red Team)
Due to hardware constraints on the cloud VM (freezing during heavy Java execution), I pivoted to a local installation of OWASP ZAP. 

<img width="320" height="352" alt="image" src="https://github.com/user-attachments/assets/7306db67-04d3-4d62-a8f0-059de93b1884" />


I executed an unauthenticated Automated Spider and Active Scan against the target's public IP.

**Vulnerabilities Identified:**
1. **Missing Anti-Clickjacking Header:** Vulnerable to UI redressing (`X-Frame-Options` missing).
2. **Server Version Information Leak:** Passive fingerprinting risk exposing exact OS and Apache versions.

<img width="315" height="400" alt="image" src="https://github.com/user-attachments/assets/a3b03f74-6fd8-47ee-9b22-c73ad5809042" />


## Phase 2: The Remediation (Blue Team)
To close these vulnerabilities, I SSH'd directly into the `Honeypot-VM` to harden the Apache configuration files. 

**Executed Commands:**
1. Enabled the headers module: `sudo a2enmod headers`
2. Edited the security configurations: `sudo nano /etc/apache2/conf-available/security.conf`
3. Restarted the web server: `sudo systemctl restart apache2`

**The Patches Applied:**
* Changed `ServerTokens OS` to `ServerTokens Prod`
* Changed `ServerSignature On` to `ServerSignature Off`
* Activated `Header set X-Frame-Options: "sameorigin"`

## Phase 3: Verification
To prove the vulnerabilities were successfully remediated without relying on the GUI scanner, I queried the HTTP response headers directly from the terminal. 

<img width="468" height="187" alt="image" src="https://github.com/user-attachments/assets/29e7ed48-225c-4e60-9599-7009162e9480" />


As seen in the output, the server banner is sanitized (`Server: Apache`), and the Anti-Clickjacking armor is active (`X-Frame-Options: sameorigin`).
