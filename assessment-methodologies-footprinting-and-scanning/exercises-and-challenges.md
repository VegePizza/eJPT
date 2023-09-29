---
description: eJPT lecture notes
---

# Exercises and Challenges

## NMAP Host Discovery

```bash
root@attackdefense: nmap 10.0.16.191 -Pn -sV -O
Starting Nmap 7.70 ( https://nmap.org ) at 2023-09-29 08:39 IST
Nmap scan report for 10.0.16.191
Host is up (0.0028s latency).
Not shown: 993 filtered ports
PORT      STATE SERVICE            VERSION
80/tcp    open  http               HttpFileServer httpd 2.3
135/tcp   open  msrpc              Microsoft Windows RPC
139/tcp   open  netbios-ssn        Microsoft Windows netbios-ssn
445/tcp   open  microsoft-ds       Microsoft Windows Server 2008 R2 - 2012 microsoft-ds
3389/tcp  open  ssl/ms-wbt-server?
49154/tcp open  msrpc              Microsoft Windows RPC
49155/tcp open  msrpc              Microsoft Windows RPC
Warning: OSScan results may be unreliable because we could not find at least 1 open and 1 closed port
Device type: general purpose
Running: Microsoft Windows 2012
OS CPE: cpe:/o:microsoft:windows_server_2012
OS details: Microsoft Windows Server 2012
Service Info: OSs: Windows, Windows Server 2008 R2 - 2012; CPE: cpe:/o:microsoft:windows

OS and Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 82.19 seconds
```

## Windows Recon: Zenmap

```sh
ipconfig /all
```

