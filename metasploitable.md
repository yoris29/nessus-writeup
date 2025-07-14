- In this section, we will use Nessus to perform a vulnerabilities on a metasploitable VM

## Lab Setup
- Virtual machine running Kali linux, with Nessus installed.
- Virtual machine with metasploitable2 running.
- Both VM's belong to the same Virtual Network "VMNet0"  with IP address $192.168.214.0$ to allow communication between them.

### Basic Host Discovery Scan
- The first scan to run is a basic host scan to identify the available hosts on the network.
- We choose the Virtual Network's IP address, and then configure Nessus to scan the common ports.
<img width="782" height="450" alt="Pasted image 20250714222624" src="https://github.com/user-attachments/assets/e52a3a1f-2745-4de0-8794-58174634cf59" />

- This is the result of the scan
<img width="1528" height="399" alt="Pasted image 20250714222517" src="https://github.com/user-attachments/assets/710e2fab-04d8-4bec-8816-03830556727e" />

- Notice how there is an IP address with many open ports. That happens to be the IP Address of the VM running metasploitable.
### Vulnerabilities Scan
- The first scan that we're going to run is going to be uncredentialled, meaning that we won't give credentials to allow Nessus to connect to the metasploitable machine.
- After identifying the target machine. We can now perform a basic vulnerabilities scan.
- When creating a new scan. Select the 'Advanced Scan' option.
- Nessus has many configuration options for the scan in-order to tailor it to your needs.
<img width="204" height="358" alt="Pasted image 20250714224148" src="https://github.com/user-attachments/assets/dccda90d-e08b-4bea-9658-bb4fff2ad62a" />

- We won't go through all of them here, but we will go through some ones.
- Under assessment category, we will enable both Web Applications and Malware scans.
<img width="1378" height="551" alt="Pasted image 20250714224559" src="https://github.com/user-attachments/assets/7de986a7-c9e9-4bda-8ff2-5f27d6d7f045" />

- Enable Web Application Scan
<img width="1557" height="623" alt="Pasted image 20250714224636" src="https://github.com/user-attachments/assets/02e1b7ec-1885-474d-b1fe-e0d9d1562646" />

- We can skip the credentials section for now. Let's see what vulnerabilities Nessus can detect without being given access to the machine.
- Save the changes, and then launch the scan.
- After the scan is finished, we get a list vulnerabilities
<img width="1517" height="390" alt="Pasted image 20250714223732" src="https://github.com/user-attachments/assets/24090def-7ec2-434f-9a21-7d7408cf9703" />

<img width="1205" height="703" alt="Pasted image 20250714223746" src="https://github.com/user-attachments/assets/db341204-e88a-4581-8053-f21479ad518e" />

- Lets take a closer look at one of those vulnerabilities.
<img width="1190" height="453" alt="Pasted image 20250714225413" src="https://github.com/user-attachments/assets/5b9045e1-94ee-4fcd-a69c-98d12ecbd211" />

 - A VNC (Virtual Network Computing) server is software that allows remote control of another computer.
 - Due to the weak password used, any attacker can login into the server and control the victim's machine easily.
### Credentialed Vulnerabilities Scan
- This time, to allow Nessus to perform a deeper scan, we will provide SSH credentials to allow it to login to the target machine.
- Go to credentials tab, and add a new SSH authentication.
- Set the authentication method to be password
- Enter metasploitable's username and password `msfadmin/msfadmin`
- <img width="1401" height="681" alt="Pasted image 20250714225822" src="https://github.com/user-attachments/assets/e9105e4e-c8b8-48fe-942f-3922c72ea5d5" />
- Save the changes and then run the scan again.
<img width="1208" height="173" alt="image" src="https://github.com/user-attachments/assets/720a81db-7145-410b-a1a4-234c991f1239" />
<img width="1199" height="704" alt="image" src="https://github.com/user-attachments/assets/44e1d884-dad3-463e-bda7-08ca3f2874f1" />
- We can see that the credentialed scan has discovered even more vulnerabilities.



