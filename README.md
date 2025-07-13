# Nmap
- Network Discovery: scan networks and discover devices in them
- Port scanning: determines which ports/services are open and used
- OS Fingerprinting: nmap can attempt to identify the OS running on a target
- Vulnerability Assessment: identify potential vulnerabilities
# Nessus
- Scans for security vulnerabilities in devices/applications/OS...
- Nessus identifies software flaws, missing patches, malware and misconfiguration errors
# Nessus vs Nmap
- Nessus is often considered to be similar to NMAP, but it really is capable of so much more. It can do things like credential scanning which is when we actually have an account that has privileges, which are usually administrator privileges so that we can log in and run system checks.
# Basic Scan
- Here i have started a basic network scan of my home network and as you can see has returned critical errors from my router (192.168.1.1) and kali vm ware machine (.42)
<img width="928" height="455" alt="image" src="https://github.com/user-attachments/assets/e5805295-28e9-44bc-94d3-d1036b227354" />

- The router has a critical error indicating the MiniUPnP which is a plug-n-play technology is inferior to 1.4 and must be upgraded because of:
	- An out of bounds read error
	- Buffer overflow
<img width="927" height="414" alt="image" src="https://github.com/user-attachments/assets/2012f062-8348-4a03-8820-e8922c92b1a2" />

- However, my kali machine indicates a deprecated node version (inferior to 18.19.1), which is subject to multiple vulnerabilities specified in the description
<img width="929" height="429" alt="image" src="https://github.com/user-attachments/assets/c96a0818-5b9e-4134-9174-16ab08df4b9c" />

# Credentialed Scan
- We have done a credentialed network scan which, compared to a normal scan, has access inside the system, not just what’s visible from the network gives us privileged 
- Install and setup SSH with these commands on linux:
```
sudo apt install openssh-server
sudo systemctl enable --now ssh
```
- Configure the scan:
<img width="720" height="553" alt="image" src="https://github.com/user-attachments/assets/04c951c5-5cfe-42c7-89f7-241107a9d3be" />

- We have performed the scan and got multiple results as shown below
<img width="928" height="380" alt="image" src="https://github.com/user-attachments/assets/fef4c7d5-f6f6-43fe-85ba-0b7893f99160" />

- One of them has a critical error, which appears to be the same deprecated node error shown above
<img width="927" height="446" alt="image" src="https://github.com/user-attachments/assets/fa0a25c1-fb1b-4a39-9d37-cddf54bb06a0" />
