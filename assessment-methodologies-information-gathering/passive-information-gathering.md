---
description: eJPT lecture notes
---

# Passive Information Gathering

## **Website Recon and foot printing**

```bash
whatis host
```

This command show the command function

Host command is for DNS lookup — means resolve DNS to IP address

![](<../.gitbook/assets/Pasted Graphic.png>)

_If you saw two IPv4 in result, maybe is dealing with proxy._

```bash
host hackerspolit.org
```

this command will show IPv4, IPv6 and the mail server.

![](<../.gitbook/assets/Pasted Graphic 1.png>)\


When you looking for information on a website, the best way to start is /robots.txt file. Almost every website has it.

![](<../.gitbook/assets/Pasted Graphic 2.png>)\


Disallow — means the website tells google/bing search engine to disregard which file when curl the website

Wp-content — shows this website running wordpress

![](<../.gitbook/assets/Pasted Graphic 3.png>)\


sitemap.xml / sitemaps.xml file —&#x20;

![](<../.gitbook/assets/Pasted Graphic 4.png>)\


Try Mozilla add-ons and install buildwith / wappalyzer / whatweb (kali building) / httrack

&#x20;![](<../.gitbook/assets/Pasted Graphic 5.png>)

![](<../.gitbook/assets/Pasted Graphic 6.png>)\
![](<../.gitbook/assets/Pasted Graphic 7.png>)

![](<../.gitbook/assets/Pasted Graphic 8.png>)



```bash
whatweb hackerspolit.org
```

![](<../.gitbook/assets/Pasted Graphic 11.png>)\


## **Whois Enumeration**

```bash
whois hackersploit.org
```

![](<../.gitbook/assets/Pasted Graphic 12.png>)

![](<../.gitbook/assets/Pasted Graphic 13.png>)

```bash
whois 108.162.192.93
```

![](<../.gitbook/assets/Pasted Graphic 14.png>)

## **DNS Recon**

```bash
dnsrecon -d hackersploit.org
```

![](<../.gitbook/assets/Pasted Graphic 17.png>)

![](<../.gitbook/assets/Pasted Graphic 19.png>)

## DNSDumpster

[https://dnsdumpster.com/](https://dnsdumpster.com/)

![](<../.gitbook/assets/Pasted Graphic 20.png>)



## **Netcraft website footprinting**

[https://www.netcraft.com/](https://www.netcraft.com/)

![](<../.gitbook/assets/Pasted Graphic 15 (1).png>)



## WAF with WAFW00F

Used to check a web application firewall

```bash
wafw00f -l
```

```bash
wafw00f hackersploit.org
```

![](<../.gitbook/assets/image (4) (1) (1).png>)

## Subdomain Enumeration With Sublist3r

{% embed url="https://github.com/aboul3la/Sublist3r" %}

Sublist3r is a python tool designed to enumerate subdomains of websites using OSINT.

```bash
sudo apt-get install sublist3r
```

```bash
sublist3r -d ine.com
```

## Google Dorks

![](<../.gitbook/assets/image (3) (1) (1).png>)

```
site:ine.com inurl:admin
```

![](<../.gitbook/assets/image (3) (1) (1) (1).png>)

```
site:ine.com inurl:forum
```

```
site:*.ine.com
```

```
site:*.ine.com intitle:admin
```

```
site:*.ine.com filetype:pdf
```

```
intitle:index of

(This is for common command for directory listing)
```

![](<../.gitbook/assets/image (2) (1) (1) (1).png>)

```
cache:ine.com

(To check the old website before updates)
```

<pre><code><strong>waybackmachine
</strong><strong>
</strong><strong>(search in google for snapshot old version of websites)
</strong></code></pre>

```
inurl:auth_user_file.txt
```

```
inurl:passwd.txt

(For user info and passwd)
```

## Google Hacking Database

[https://www.exploit-db.com/google-hacking-database](https://www.exploit-db.com/google-hacking-database)

![](<../.gitbook/assets/image (5) (1) (1).png>)

![](<../.gitbook/assets/image (6) (1) (1).png>)

![](<../.gitbook/assets/image (7) (1) (1).png>)

```
inurl:wp-config.bak

(wordpress sql database credentials)
```

## Email Harvesting With theHarvester

The tool gathers names, emails, IPs, subdomains, and URLs.

it can also be used to perform subdomain enumeration

{% embed url="https://github.com/laramies/theHarvester" %}

```bash
theHarvester -d hackersploit.org -b google,linkedin,yahoo,dnsdumpster,duckduckgo
```

![](<../.gitbook/assets/image (8) (1) (1).png>)

## Leaked Password Databases

when user reuse password and perform a password spray attack

_HaveIBeenPwned website can check whether a data breach happened or not_

{% embed url="https://haveibeenpwned.com/" %}

