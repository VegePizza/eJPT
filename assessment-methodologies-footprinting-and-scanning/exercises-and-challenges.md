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

Zenmap is the GUI version of nmap

```sh
ipconfig /all
```

check the ip and subnet are currently on

<figure><img src="../.gitbook/assets/image (29).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (30).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (32).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (31).png" alt=""><figcaption></figcaption></figure>

## Scan the Server 1

```powershell
ip a
```

find our ip address

```powershell
ping 192.148.40.3
```

ping the ip within our subnet

```powershell
nmap 192.148.40.3 -p-
```

Check the top 1000 ports (not the first 1000 ports)

```powershell
nmap 192.148.40.3 -p 6421,41288,55413 -sV
```

Make the service enumeration on the exact open ports

<figure><img src="../.gitbook/assets/image (34).png" alt=""><figcaption></figcaption></figure>



## Scan the Server 2

<figure><img src="../.gitbook/assets/image (35).png" alt=""><figcaption></figcaption></figure>

```powershell
nmap 192.206.172.3 -p 1-250
```

Scan ports from 1-250

```powershell
nmap 192.206.172.3 -p 177 -A
```

make an aggressive scan on the exact port

<figure><img src="../.gitbook/assets/image (37).png" alt=""><figcaption><p>ISC BIND is a DNS service, so a UDP is also expected, keep scanning</p></figcaption></figure>

```powershell
nmap 192.206.172.3 -p 1-250 -sU
```

Checking for UDP ports

<figure><img src="../.gitbook/assets/image (38).png" alt=""><figcaption></figcaption></figure>

```powershell
nmap 192.206.172.3 -p 134,177,234 -sUV
```

```powershell
nmap 192.206.172.3 -p 134 -sUVC
```

```powershell
nmap 192.206.172.3 -p 134 -sUV --script=discovery
```

```powershell
tftp 192.206.172.3 134
```

## Scan the Server 3

```
nmap 192.57.232.3 -T4 -p-
```

scan all TCP ports in speed T4 mode

```
nmap 192.57.232.3 -T4 -sU
```

```
nmap 192.57.232.3 -T4 -sU -p 161 -A
```

<figure><img src="../.gitbook/assets/image (39).png" alt=""><figcaption></figcaption></figure>

