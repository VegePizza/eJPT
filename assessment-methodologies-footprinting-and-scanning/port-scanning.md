---
description: eJPT lecture notes
---

# Port Scanning

## Identify Operation System

![](<../.gitbook/assets/image (23).png>)![](<../.gitbook/assets/image (24).png>)

## Scanning for services

Connect to TCP three way handshake

"Stealthy" connection

![](<../.gitbook/assets/image (21).png>)

![](<../.gitbook/assets/image (22).png>)

## Connect to UDP

### NMAP

Use NMap flags

```bash
┌──(vegepizza㉿kali)-[~]
└─$ sudo nmap -iL ips -sV -O     
Failed to open input file ips for reading: No such file or directory (2)
```

![](<../.gitbook/assets/image (26).png>)

![](<../.gitbook/assets/image (27).png>)

<pre class="language-bash"><code class="lang-bash"><strong>┌──(vegepizza㉿kali)-[~]
</strong>└─$ sudo nmap 5.196.105.14 -sV -O -sC
# This -sC means script, will run NSE(Nmap Scripting Engine)
</code></pre>

![](<../.gitbook/assets/image (28).png>)

