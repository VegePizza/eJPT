---
description: eJPT lecture notes
---

# Active Information Gathering

## DNS Zone Transfers

![](<.gitbook/assets/image (17).png>)

**DNS interrogation** is the process of enumerating DNS records for a specific domain.

```bash
dnsenum --help
```

```bash
dnsenum zonetransfer.me
```

Gain more information about the subdomains which know about internal ip addresses and network.

Which we can use after gained access to the target network.&#x20;

![](<.gitbook/assets/image (9).png>)![](<.gitbook/assets/image (10).png>)

```bash
dig axfr @nsztm1.digi.ninja zonetransfer.me
```

![](<.gitbook/assets/image (11).png>)

<pre class="language-bash"><code class="lang-bash"><strong>fierce --domain  zonetransfer.me
</strong></code></pre>

![](<.gitbook/assets/image (12).png>)![](<.gitbook/assets/image (13).png>)

## Host Discovery With Nmap

Perform a ping scan or ping sweep using N-map

```bash
ip a s
```

know about my own network ip

```bash
┌──(vegepizza㉿kali)-[~]
└─$ ip a s  
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 56:61:7b:dc:e9:ed brd ff:ff:ff:ff:ff:ff
    inet 192.168.64.8/24 brd 192.168.64.255 scope global dynamic noprefixroute eth0
       valid_lft 83873sec preferred_lft 83873sec
    inet6 fddd:b85:7b25:9934:c88b:cf78:e417:6a34/64 scope global temporary dynamic 
       valid_lft 602276sec preferred_lft 83603sec
    inet6 fddd:b85:7b25:9934:5461:7bff:fedc:e9ed/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 2591969sec preferred_lft 604769sec
    inet6 fe80::5461:7bff:fedc:e9ed/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
```

```bash
man nmap
```

As a pen-tester, should always do this **(Host discovery)** to discover devices on the target network

Copy all the ip, then do a port scan on each of them to identify services running on the target.

```bash
┌──(vegepizza㉿kali)-[~]
└─$ sudo nmap -sn 192.168.64.8/24
[sudo] password for vegepizza: 
Starting Nmap 7.94 ( https://nmap.org ) at 2023-09-27 10:32 NZDT
Nmap scan report for 192.168.64.1
Host is up (0.0017s latency).
MAC Address: F2:2F:4B:C0:8C:64 (Unknown)
Nmap scan report for 192.168.64.8
Host is up.
Nmap done: 256 IP addresses (2 hosts up) scanned in 2.00 seconds
```

We can also perform this host discovery using **NetDiscover** which send ARP requests to resolve MAC to ip addresses or vice versa.

![](<.gitbook/assets/image (16).png>)

## Port Scanning With Nmap

Perform TCP port (by default) and UDP port scanning

```bash
nmap 10.4.19.218 (default scan 1000 most frequent ports)
nmap -p- 10.4.19.218 (entire range)
nmap -p 80,445,3389 10.4.19.218 (specific ports)
nmap -p1-10000 10.4.19.218 (custom port range)
nmap -F 10.4.19.218 (fastscan 100 ports)
nmap -sU 10.4.19.218 (UDP ports because certain service running on UDP like DNS) 
nmap 10.4.19.218 -v (show details during scan)
nmap -F -sV 10.4.19.218 (fast and service version scan)
nmap -F -sV -O 10.4.19.218 (operation system scan)
nmap -F -sV -O -sC 10.4.19.218 (script scan)
nmap -F -A 10.4.19.218 (aggressive scan which combine -sV-O-sC in one)
nmap -T5 10.4.19.218 (scan speed 0-5 paranoid/sneaky/polite/normal/aggressive/insane)
nmap 10.4.19.218 -oN test.txt  / -oX test.xml
(export scan to file -oN to normal format -oX to xml for Metasploit)
```

