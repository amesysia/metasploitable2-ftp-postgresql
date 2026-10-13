# Metasploitable 2 Walkthrough: Exploiting FTP and PostgreSQL

[Read the full write-up on Medium](https://medium.com/@amesysia/metasploitable-2-walkthrough-exploiting-ftp-and-postgresql-7d130eadd8bd)

> [!WARNING]
> This project was executed in an isolated lab environment and for educational purposes only.


Metasploitable is a vulnerable Ubuntu Linux machine designed for penetration testing practice. In this walkthrough, I will document my step-by-step process of enumerating and exploiting various services on this machine.

Lab Setup and Access
I downloaded Metasploitable and set it up in VirtualBox. I connected it to my own NAT Network so it could communicate with my Kali machine while remaining isolated from my main network.

I logged in using the default credentials (msfadmin:msfadmin) and ran ifconfig to find the machine's IP address: 10.0.2.6.

2. Reconnaissance

I ran nmap on Kali:

nmap -v -sS -A -T4 10.0.2.6 -oN nmapresult.txt
-v (verbose) to see detailed information,
-sS (TCP SYN scan) to perform a SYN scan,
-A (aggressive) to enable OS detection, version detection, script scanning, and traceroute all at once,
-T4 (timing template) to speed up the scan; It is intended for reasonably fast and reliable networks,
-oN to print results to a file.

3.1 FTP — vsftpd 2.3.4 Backdoor
I searched through the Nmap results and saw that anonymous FTP login was allowed. I also noted the vsftpd version was 2.3.4. I ran Metasploit to see if any exploits were available.

Metasploit is a penetration testing framework for finding, testing, and exploiting system vulnerabilities.

Write on Medium
I started Metasploit by running msfconsole and searched for exploits using search vsftpd 2.3.4.

![description](screenshots/screenshot-1.png)
