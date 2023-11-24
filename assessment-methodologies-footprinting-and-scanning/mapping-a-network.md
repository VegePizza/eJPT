---
description: eJPT lecture notes
---

# Mapping a Network

## Wireshark

Can use Wireshark while sending a ARP scan in bash

![](<../.gitbook/assets/image (19) (1).png>)

## ARP Scan

(Address Resolution Protocol)&#x20;

Which map IP addresses to MAC addresses.

Will tell me who has 10.142.111.0/24

e.g. 10.142.111.0 is at 00:0c:29:af:ea:d2

\-I interface -g generate based off of subnet

```bash
sudo arp-scan -I eth0 -g 10.142.111.0/24
```

<pre class="language-bash"><code class="lang-bash">┌──(vegepizza㉿kali)-[~]
└─$ ip a
1: lo: &#x3C;LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: &#x3C;BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether 56:61:7b:dc:e9:ed brd ff:ff:ff:ff:ff:ff
    inet 192.168.64.8/24 brd 192.168.64.255 scope global dynamic noprefixroute eth0
       valid_lft 76388sec preferred_lft 76388sec
    inet6 fddd:b85:7b25:9934:c88b:cf78:e417:6a34/64 scope global temporary dynamic 
       valid_lft 594789sec preferred_lft 76116sec
    inet6 fddd:b85:7b25:9934:5461:7bff:fedc:e9ed/64 scope global dynamic mngtmpaddr noprefixroute 
       valid_lft 2591941sec preferred_lft 604741sec
    inet6 fe80::5461:7bff:fedc:e9ed/64 scope link noprefixroute 
       valid_lft forever preferred_lft forever
                                                                                                                                                                                                                                                                                                                                                                           
┌──(vegepizza㉿kali)-[~]
└─$ sudo arp-scan -I eth0 -g 192.168.64.8/24
Interface: eth0, type: EN10MB, MAC: 56:61:7b:dc:e9:ed, IPv4: 192.168.64.8
WARNING: host part of 192.168.64.8/24 is non-zero
Starting arp-scan 1.10.0 with 256 hosts (https://github.com/royhills/arp-scan)
192.168.64.1    f2:2f:4b:c0:8c:64       (Unknown: locally administered)

1 packets received by filter, 0 packets dropped by kernel
Ending arp-scan 1.10.0: 256 hosts scanned in 2.034 seconds (125.86 hosts/sec). 1 responded
<strong>
</strong></code></pre>

## Ping

ICMP (Internet Control Message Protocol)

Which is for diagnose network connectivity.

**Traceroute** tells you all the points between destination and source for packets. And **Ping** echo reply.

```bash
┌──(vegepizza㉿kali)-[~]
└─$ ping 5.196.105.14
PING 5.196.105.14 (5.196.105.14) 56(84) bytes of data.
64 bytes from 5.196.105.14: icmp_seq=1 ttl=53 time=295 ms
64 bytes from 5.196.105.14: icmp_seq=2 ttl=53 time=755 ms
64 bytes from 5.196.105.14: icmp_seq=3 ttl=53 time=456 ms
64 bytes from 5.196.105.14: icmp_seq=4 ttl=53 time=1010 ms
64 bytes from 5.196.105.14: icmp_seq=5 ttl=53 time=396 ms
64 bytes from 5.196.105.14: icmp_seq=6 ttl=53 time=418 ms
^C
--- 5.196.105.14 ping statistics ---
7 packets transmitted, 6 received, 14.2857% packet loss, time 6018ms
rtt min/avg/max/mdev = 294.548/555.025/1010.390/247.956 ms, pipe 2
```

## FPING

FPing will send out pings to multiple hosts at one time and give a cleaner return back.

```bash
┌──(vegepizza㉿kali)-[~]
└─$ fping -I eth0 -g 5.196.105.0/24 
5.196.105.1 is alive
5.196.105.2 is alive
5.196.105.4 is alive
5.196.105.5 is alive
5.196.105.7 is alive

#-a 2>/dev/null will make it only return without error
┌──(vegepizza㉿kali)-[~]
└─$ fping -I eth0 -g 5.196.105.0/24 -a 2>/dev/null
5.196.105.1
5.196.105.2
5.196.105.4
5.196.105.5
5.196.105.7
```

Sometimes some ip can only be found by ARP scan, and not by ping. So should apply both methods.

## NMAP

```bash
┌──(vegepizza㉿kali)-[~]
└─$ nmap -sn  5.196.105.0/24       
Starting Nmap 7.94 ( https://nmap.org ) at 2023-09-29 15:14 NZDT
Nmap scan report for 5.196.105.1
Host is up (0.37s latency).
Nmap scan report for 5.196.105.2
Host is up (0.37s latency).
Nmap scan report for 5.196.105.4
Host is up (0.37s latency).
Nmap scan report for 5.196.105.5
Host is up (0.37s latency).
Nmap scan report for 5.196.105.7
Host is up (0.37s latency).
Nmap scan report for 5.196.105.14
Host is up (0.40s latency).
Nmap scan report for 5.196.105.15
Host is up (0.40s latency).
```

## ZENMAP

It is a GUI version of NMAP

![](<../.gitbook/assets/image (20) (1).png>)
