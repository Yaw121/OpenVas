### OBJECTIVE

Gain hands-on experience installing, configuring, and running OpenVAS (Greenbone Vulnerability Management) to perform automated vulnerability scanning within a controlled environment on TryHackMe. The goal was to understand how to set up a comprehensive vulnerability assessment tool and interpret scan results to strengthen an organization’s security posture.

### Skills Learned

<b>OpenVAS Installation & Configuration</b>: Learned how to install and configure the Greenbone Vulnerability Management platform from scratch, including database setup and web UI configuration.

<b>Vulnerability Scanning</b>: Explored how to schedule scans, generate reports, and interpret findings to identify critical vulnerabilities in a target environment.

<b>Network Services & Protocols</b>: Gained a deeper understanding of network services, ports, and protocols commonly found in enterprise environments.

<b>Troubleshooting & System Administration</b>: Enhanced troubleshooting techniques and command-line proficiency by dealing with environment-specific setup issues (firewall rules, dependencies, and resource configuration).

<b>Security Best Practices</b>: Reinforced the importance of regular vulnerability assessments and patch management in securing systems and networks.


### Tools Used

- <b>OpenVAS/Greenbone Vulnerability Manager</b>: Main vulnerability scanning and management platform.

- <b>Ubuntu</b>: Operating systems used for installing OpenVAS and performing scans.

- <b>SSH & Command-Line Tools</b>: Facilitated remote administration, file transfers, and system configuration.

- <b>Web Browser (OpenVAS Web Interface)</b>: Used for managing tasks, scheduling scans, and generating reports.

- <b>TryHackMe Platform</b>: Provided the hands-on environment for practical exercises and deployments.


<details><summary><b>OpenVas Installation
</b></summary>

  I used a docker to install Openvas on Ubuntu OS. First, run a system update, install the docker, and run it after the installation was complete

  ![image](https://github.com/user-attachments/assets/378cbad9-cbbc-44d3-b44b-7cfe0d0f8f87)

  ![image](https://github.com/user-attachments/assets/4fb59ba3-9fa2-4c38-bfef-6a2484c574d9)

  Login into Openvas using the default username and password from Tryhackme
  ![image](https://github.com/user-attachments/assets/2d191baa-9a79-4adb-8b99-947cdf815e0a)

</details>

<details><summary><b>OpenVas Configuration</b></summary>

### Creating a Task

To create a configurable task navigate to the star icon in the upper right-hand corner of the Tasks dashboard and select New Task. 

 ![image](https://github.com/user-attachments/assets/6d56d50a-2640-46fb-8c21-0b14618900ed)

 ![image](https://github.com/user-attachments/assets/e1627d46-9027-4ab5-8875-ffdce4fffb27)

### Scoping a New Target

To scope a new target, navigate to the star icon next to Scan Targets.
![image](https://github.com/user-attachments/assets/0ae906ee-bfe2-49fc-b676-1eafa26e3ba0)

![image](https://github.com/user-attachments/assets/d7d3aebd-12ad-4a9b-8ab2-c8948bc00db3)

Now that we have created our task and target, we can begin scanning our ports and network.  To start the task navigate to the start icon under Actions.
![Screenshot 2024-12-22 222106](https://github.com/user-attachments/assets/8a8e4d95-f5fc-4075-9951-f18f479a9035)

### Results of our Scan

![image](https://github.com/user-attachments/assets/c303f405-94f5-4693-8709-f841600ce7ce)

After the basic host and task information OpenVAS will report on each of the vulnerabilities found. In the screenshot below, the vulnerability breakdown can give a lot of information. We can gather a summary of the vulnerability, detection details, mitigation details, and method of detection.
![image](https://github.com/user-attachments/assets/22c1f637-f9e5-4f03-b22c-a2a88b504f06)

</details>

<details><summary><b>Remediate Vulnerabilies</b></summary>
- We need to disable TCP timestamps based on the vulnerability report

Edit sysctl.conf:
1. Open the /etc/sysctl.conf file in the ubuntu terminal by running; sudo nano /etc/sysctl.conf.

2. Disable TCP Timestamps: Add or update the following line: net.ipv4.tcp_timestamps = 0

  ![image](https://github.com/user-attachments/assets/797b521f-160d-45ae-8f07-9d4fafc68a68)

![image](https://github.com/user-attachments/assets/73204995-1b9d-46a2-8f6d-49bd68ed1307)

Save the file and run: sudo sysctl -p. This ensures the new setting takes effect immediately.

![image](https://github.com/user-attachments/assets/b8523341-dc18-44d7-9c08-29847df9a137)

</details>


<details><summary><b>Verification</b></summary>
After applying the changes, you can verify whether TCP timestamps are disabled: We can do this by running sysctl net.ipv4.tcp_timestamps

![image](https://github.com/user-attachments/assets/21c444e2-b3e6-4476-b3fc-dda631ca2770)

Which returned as " net.ipv4.tcp_timestamps = 0." This means we have successfully disabled TCP timestamps in the systems's TCP/IP stack
</details>
<details><summary><b>Reflection</b></summary>

  This lab provided hands-on experience in setting up and using a vulnerability management scanner with OpenVAS. It highlighted the importance of proactive vulnerability management and the impact of misconfigurations and outdated software on system security.

Configuring OpenVAS for unauthenticated scans and performing the scans allowed me to identify vulnerabilities and understand the need for regular scanning to detect security risks.

Implementing credentialed scans and comparing the results with unauthenticated scans demonstrated the value of using proper credentials for accurate vulnerability identification.
Remediating vulnerabilities by disabling TCP timestamps and verifying the changes through subsequent scans reinforced the importance of timely actions to reduce the attack surface.
</details>

<details><summary><b>Conclusion</b></summary>

This lab enhanced my understanding of vulnerability management and the continuous effort required for maintaining a secure environment. It emphasized the significance of proactive security practices, timely remediation, and the value of comprehensive scanning approaches.

I now possess practical knowledge and skills in vulnerability management using OpenVAS, ready to apply them in real-world scenarios and contribute to effective system protection.

</details>


