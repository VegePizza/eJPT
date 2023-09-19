---
description: eJPT lecture notes
---

# Passive Information Gathering

## **Website Recon and foot printing**

```bash
whatis host
```

show the command do



Host command is for DNS lookup — means resolve DNS to IP address

![](<.gitbook/assets/Pasted Graphic.png>)



If you saw two IPv4, maybe is dealing with some kind of proxy.

```bash
host hackerspolit.org
```

this command will show IPv4, IPv6 and the mail server.

![](<.gitbook/assets/Pasted Graphic 1.png>)\


When you looking for information on a website, the best way to start is /robots.txt file. Almost every website has it.

![](<.gitbook/assets/Pasted Graphic 2.png>)\


Disallow — means the website tells google/bing search engine to disregard which file when curl the website

Wp-content — shows this website running wordpress

![](<.gitbook/assets/Pasted Graphic 3.png>)\


sitemap.xml / sitemaps.xml file —&#x20;

![](<.gitbook/assets/Pasted Graphic 4.png>)\


Try Mozilla add-ons and install buildwith / wappalyzer / whatweb (kali building) / httrack

&#x20;![](<.gitbook/assets/Pasted Graphic 5.png>)

![](<.gitbook/assets/Pasted Graphic 6.png>)\
![](<.gitbook/assets/Pasted Graphic 7.png>)

![](<.gitbook/assets/Pasted Graphic 8.png>)



```bash
whatweb hackerspolit.org
```

![](<.gitbook/assets/Pasted Graphic 11.png>)\


## **Whois Enumeration**

```
whois hackersploit.org
```

![](<.gitbook/assets/Pasted Graphic 12.png>)

![](<.gitbook/assets/Pasted Graphic 13.png>)

```
whois 108.162.192.93
```

![](<.gitbook/assets/Pasted Graphic 14.png>)

## **DNS Recon**

```bash
dnsrecon -d hackersploit.org
```

![](<.gitbook/assets/Pasted Graphic 17.png>)

![](<.gitbook/assets/Pasted Graphic 19.png>)

[https://dnsdumpster.com/](https://dnsdumpster.com/)

![](<.gitbook/assets/Pasted Graphic 20.png>)



## **Netcraft website footprinting**

![](<.gitbook/assets/Pasted Graphic 15 (1).png>)



## WAF with WAFW00F

Used to check a web application firewall

```bash
wafw00f -l
```

```bash
wafw00f hackersploit.org
```

![](.gitbook/assets/image.png)
