# Introduction-to-IoT-Security-and-Threat-Modelling

## Objective
The goal of this lab is to understand IoT security vulnerabilities by performing threat modeling and port scanning on an IoT device using a simulator.
By the end of this experiment, you will be able to:
✅ Identify potential security threats in IoT systems.
✅ Scan IoT devices for open ports and vulnerabilities.
✅ Develop a threat model using the Microsoft Threat Modeling Tool (TMT).
________________________________________
## Required Tools & Software
🔹 IoT Device Simulator: IoTIFY (Online IoT simulator) OR Cisco Packet Tracer.
🔹 Nmap (Network Scanner):
🔹 Microsoft Threat Modeling Tool (TMT):
🔹 Wireshark (Optional for Packet Analysis):
________________________________________
## Step-by-Step Procedure
Step 1: Set up an IoT Device in a Simulator
We will use IoTIFY to simulate an IoT device.

🔹 Option 1: Using IoTIFY Simulator

1.	Go to IoTIFY:
o	Visit IoTIFY and create an account (if not already done).
2.	Create a Virtual IoT Device:
o	Select "Virtual Device Simulator".
o	Configure an ESP8266-based sensor that sends temperature data.
o	Set the device to communicate over MQTT (for later security analysis).
4.	Deploy the Device:
o	Click Run Simulation to start the device.

🔹 Option 2: Using Cisco Packet Tracer
1.	Open Cisco Packet Tracer and create a new project.
2.	Add an IoT Smart Device (e.g., IoT Thermostat).
3.	Connect the device to a Router with Wi-Fi.
4.	Configure the IP address using DHCP or static addressing.
5.	Save the topology for network scanning.
________________________________________
Step 2: Scan for Open Ports Using Nmap

Nmap helps us identify open ports on IoT devices that may be vulnerable to attacks.
🔹 Running Nmap on a Simulated IoT Device
1.	Install Nmap (if not installed) using:
o	Windows: Download and install from here.
o	Linux: Use the command:
bash
CopyEdit
sudo apt install nmap -y
2.	Open Command Prompt (Windows) / Terminal (Linux).
3.	Run the following Nmap scan on the IoT device (replace <IP_ADDRESS> with the actual IP of your IoT device):
bash
CopyEdit
nmap -sV -p 1-65535 <IP_ADDRESS>
4.	If using Cisco Packet Tracer:
o	Find the IP address of the IoT device using:
bash
CopyEdit
ipconfig /all
o	Scan the network from a simulated hacker laptop inside Packet Tracer using:

bash
CopyEdit
nmap -sV 192.168.1.0/24
6.	Analyze the open ports and vulnerabilities in the output.
7.	
🔹 Common Open Ports in IoT Devices:
Port	Service	Security Concern
22	SSH	Can be brute-forced
23	Telnet	Insecure, sends plain text
80	HTTP	Vulnerable to web attacks
1883	MQTT	IoT protocol, often unsecured
✅ Expected Output: List of open ports on the IoT device, revealing security risks.
________________________________________

Step 3: Perform Threat Modeling Using Microsoft Threat Modeling Tool

Threat modeling helps in identifying potential attack vectors in IoT systems.
🔹 Steps to Use Microsoft Threat Modeling Tool (TMT)
1.	Install TMT from here.
2.	Open TMT and create a new project.
3.	Add Components:
o	Drag and drop IoT Device (e.g., ESP8266, Raspberry Pi).
o	Add a Cloud Service for data storage.
o	Add a User Interface (web dashboard).
4.	Define Trust Boundaries:
o	Draw lines between components (e.g., IoT device ↔ Cloud).
o	Mark public networks as untrusted.
5.	Identify Threats Using STRIDE Model:
o	Spoofing: Can an attacker impersonate an IoT device?
o	Tampering: Can someone modify firmware remotely?
o	Repudiation: Is there logging to track changes?
o	Information Disclosure: Is MQTT sending unencrypted data?
o	Denial of Service (DoS): Can an attacker flood the IoT network?
o	Elevation of Privileges: Can a hacker gain admin rights?
6.	Generate a Threat Report:
o	Click "Report" → Generate to get a list of security issues.
✅ Expected Output: A threat model diagram with identified risks and mitigation plans.
________________________________________
## Result & Analysis
🔹 Key Observations
1.	Network Vulnerabilities Identified:
o	Open ports detected on IoT devices (e.g., 22, 23, 80, 1883).
o	Telnet and HTTP were unencrypted, making them risky.
2.	Threat Model Findings:
o	Lack of authentication on MQTT communication.
o	No encryption for transmitted data.
o	Potential for MITM (Man-in-the-Middle) attacks.
3.	Recommendations:
o	Close unused ports and disable Telnet & HTTP.
o	Implement TLS encryption for MQTT.
o	Use strong authentication mechanisms (JWT, OAuth).
________________________________________
## Conclusion
In this experiment, we successfully:
✅ Simulated an IoT device using IoTIFY or Cisco Packet Tracer.
✅ Scanned for vulnerabilities using Nmap.
✅ Performed threat modeling using Microsoft TMT
