# Project 3: Threat Intelligence & Global Attack Mapping

## Objective
To extract actionable threat intelligence from raw server logs by utilizing a custom script and geolocation API, ultimately visualizing the global origin of live cyberattacks on an interactive map.

## Skills & Tools Demonstrated
* **Platforms:** Microsoft Sentinel, Azure Workbooks
* **Concepts:** Threat Intelligence, Geolocation, Log Parsing, Data Visualization
* **Data Sources:** Live attacker IP addresses extracted from syslog data.

## The Execution
Raw logs show that an attack happened, but threat intelligence provides context on *who* is attacking and from *where*. 

1. **Log Extraction:** I utilized a custom script within the `Honeypot-VM` to parse the `/var/log/auth.log` file, specifically filtering for failed SSH login attempts and extracting the originating IP addresses.
2. **Geolocation API Integration:** The script processed these extracted IP addresses through a third-party IP geolocation API. This enriched the raw data by appending physical location metadata (latitude, longitude, country, and state) to each malicious request.
3. **Data Visualization:** Within Microsoft Sentinel, I configured an Azure Workbook to ingest this enriched data. I plotted the geographic coordinates onto a global map, creating a live, visual representation of where the automated brute-force attacks were originating from.

## Visual Documentation
The interactive map below highlights the global distribution of the attacks targeting my honeypot infrastructure, with the size and color of the plotted circles correlating to the frequency of attacks from those specific regions.

<img width="468" height="316" alt="image" src="https://github.com/user-attachments/assets/096437d6-52b4-4c9d-874b-e180de220d61" />
