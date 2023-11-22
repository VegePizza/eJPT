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

## Solution 1

**Step 1:** Open the lab link to access the Kali Linux terminal instance

**Step 2:** Identify the target IP address

Before we begin performing a port scan with Nmap, we will need to identify the target IP address.

We can identify the target IP address by running the following command:

**Command:**

```
ip a
```

As shown in the following screenshot, identify the IP address associated with the **eth1** interface, this is the Kali Linux IP. The target IP address is always the next IP in the subnet.

![1](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1784/1.png)

So if the Kali Linux IP is **192.148.40.2** the target IP will be **192.148.40.3**.

**Note:** In your case, the target IP address will be different, ensure you replace the IP of the target system in your lab environment with the IP address outlined below.

We can ping the target IP to verify that it is active, this can be done by running the following command:

**Command:**

```
ping 192.148.40.3
```

As shown in the following screenshot, the host is online and is reachable from our Kali Linux system.

![2](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1784/2.png)

**Step 3:** Port scanning with Nmap

We can now perform a default Nmap port scan on the target to identify the open ports on the target system, this can be done by running the following command:

**Command:**

```
nmap 192.148.40.3
```

As shown in the following screenshot, the default Nmap scan does not reveal any open ports. This is because the default Nmap scan profile only scans 1000 of the most commonly used ports.

![3](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1784/3.png)

In order to get an accurate idea of the open ports on the target system, we will need to scan the entire TCP port range (65,535 ports). This can be done by running the following command:

**Command:**

```
nmap 192.148.40.3 -p-
```

As shown in the following screenshot, the Nmap scan reveals that the target system has 3 open ports.

![4](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1784/4.png)

**Step 4:** Service detection with Nmap

Now that we have identified the open ports on the target, we can learn more about the services running on the open ports by performing a service detection scan with Nmap.

This can be done by running the following command:

**Command:**

```
nmap 192.148.40.3 -p 6421,41288,55413 -sV
```

As shown in the following screenshot, the Nmap service detection scan reveals the names and versions of the services running on the open ports on the target system.

![5](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1784/5.png)

## Solution 2

**Step 1:** Open the lab link to access the Kali Linux terminal instance

**Step 2:** Identify the target IP address

Before we begin performing a port scan with Nmap, we will need to identify the target IP address.

We can identify the target IP address by running the following command:

**Command:**

```
ip a
```

As shown in the following screenshot, identify the IP address associated with the **eth1** interface, this is the Kali Linux IP. The target IP address is always the next IP in the subnet.

![1](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1785/1.png)

So if the Kali Linux IP is **192.206.172.2** the target IP will be **192.206.172.3**.

**Note:** In your case, the target IP address will be different, ensure you replace the IP of the target system in your lab environment with the IP address outlined below.

We can ping the target IP to verify that it is active, this can be done by running the following command:

**Command:**

```
ping 192.206.172.3
```

As shown in the following screenshot, the host is online and is reachable from our Kali Linux system.

![2](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1785/2.png)

**Step 3:** Port scanning with Nmap

To begin with, we can perform an Nmap port scan on the target system to identify whether the BIND DNS server is open. This can be done by running the following command:

**Command:**

```
nmap 192.206.172.3 -p 177 -A
```

As shown in the following screenshot, the DNS BIND server is running on port 177.

![3](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1785/3.png)

We can now perform a UDP port scan on the port range 1-250, this can be done by running the following command:

**Command:**

```
nmap 192.206.172.3 -p 1-250 -sU
```

As shown in the following screenshot, the Nmap scan reveals that the target system has 3 open UDP ports.

![4](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1785/4.png)

**Step 4:** Service detection with Nmap

Now that we have identified the open UDP ports on the target, we can learn more about the services running on the open ports by performing a service detection scan with Nmap.

This can be done by running the following command:

**Command:**

```
nmap 192.206.172.3 -p 134,177,234 -sUV
```

As shown in the following screenshot, the Nmap service detection scan reveals the names and versions of the services running on the open UDP ports on the target system.

![5](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1785/5.png)

The Nmap scan reveals the services running on ports 177 and 234, but not 134. We can perform an Nmap script scan to enumerate information from port 134 by running the following command:

**Command:**

```
nmap 192.206.172.3 -p 134 -sUV --script=discovery
```

As shown in the following screenshot, the Nmap script scan does not reveal any useful information regarding the service running on port 134.

![6](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1785/6.png)

Given that we have discovered that UDP ports 177 and 234 are running a DNS and SNMP server respectively, we can assume that port 134 is running the TFTP server.

We can confirm this by running the following command:

**Command:**

```
tftp 192.206.172.3 134 
```

As shown in the following screenshot, the authentication with the TFTP server is successful and we are provided with an FTP console.

![7](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1785/7.png)

We have successfully been able to identify the ports running the BIND DNS server, SNMP server and TFTP server.

## Solution 3

**Step 1:** Open the lab link to access the Kali Linux terminal instance

**Step 2:** Identify the target IP address

Before we begin performing a port scan with Nmap, we will need to identify the target IP address.

We can identify the target IP address by running the following command:

**Command:**

```
ip a
```

As shown in the following screenshot, identify the IP address associated with the **eth1** interface, this is the Kali Linux IP. The target IP address is always the next IP in the subnet.

![1](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1786/1.png)

So if the Kali Linux IP is **192.57.232.2** the target IP will be **192.57.232.3**.

**Note:** In your case, the target IP address will be different, ensure you replace the IP of the target system in your lab environment with the IP address outlined below.

We can ping the target IP to verify that it is active, this can be done by running the following command:

**Command:**

```
ping 192.57.232.3
```

As shown in the following screenshot, the host is online and is reachable from our Kali Linux system.

![2](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1786/2.png)

**Step 3:** Port scanning with Nmap

To begin with, we can perform an Nmap port scan on the entire TCP port range (65,535 ports) to identify all the open ports on the target system. This can be done by running the following command:

**Command:**

```
nmap 192.57.232.3 -T4 -p-
```

As shown in the following screenshot, target system does not have any open TCP ports.

![3](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1786/3.png)

Given that the target system does not have any TCP ports open, we can perform a UDP port scan do discover any open UDP ports on the target system.

This can be done by running the following command:

**Command:**

```
nmap 192.57.232.3 -T4 -sU
```

As shown in the following screenshot, the Nmap scan reveals that the target system only has one UDP port open (port 161) that is typically used by the SNMP service.

![4](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1786/4.png)

**Step 4:** Service detection with Nmap

Now that we have identified the open UDP port on the target, we can learn more about the service running on the open port by performing a service detection and script scan with Nmap.

This can be done by running the following command:

**Command:**

```
nmap 192.57.232.3 -T4 -sU -p 161 -A
```

As shown in the following screenshot, the Nmap service detection scan confirms that an SNMP server is running on port 161, the scan also enumerates information from the SNMP server.

![5](https://assets.ine.com/content/ptp/Jack/VOD-4369/LAB-1786/5.png)

Go through the results produced by the aforementioned Nmap scan to learn more about the target system.
