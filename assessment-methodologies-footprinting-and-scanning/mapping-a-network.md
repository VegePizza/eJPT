---
description: eJPT lecture notes
---

# Mapping a Network

Run ARP scan, will tell me who has 10.142.111.0/24, -I interface -g generate

```bash
sudo arp-scan -I eth0 -g 10.142.111.0/24
```

```bash
┌──(vegepizza㉿kali)-[~]
└─$ ip a
1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
    inet6 ::1/128 scope host noprefixroute 
       valid_lft forever preferred_lft forever
2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
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

```

![](<../.gitbook/assets/image (19).png>)
