# SMB Lesson

## SMB: Windows Discover & Mount

SMB (Server Message Block) is a windows implementation of a file share

CIFS (Common Internet File System)

1. **Server Message Block (SMB):** SMB is a network file sharing protocol that allows applications and users on a network to read, write, and request services from server systems over a network. Originally developed by IBM, it has been significantly advanced and popularized by Microsoft. SMB enables computers to communicate with each other and share files and printers across a network. It is heavily used in Windows environments but is also compatible with other operating systems.
2. **Common Internet File System (CIFS):** CIFS is a version of the SMB protocol. It was introduced by Microsoft in the 1990s as an enhancement of the original SMB protocol. CIFS runs over TCP/IP and is used to allow file sharing and printing across a network. It's considered a dialect of SMB and is often referred to interchangeably with SMB, especially in the context of Windows networks.

In essence, CIFS is a specific implementation of SMB. Over time, the SMB protocol has evolved, leading to different versions like SMB1, SMB2, and SMB3. Each of these versions brought improvements and changes in aspects such as performance, security, and features.

<figure><img src="../.gitbook/assets/image (41).png" alt=""><figcaption></figcaption></figure>

Port 445 : SMB or CIFS

Port 139/tcp netbios-ssn : usually set up Sessions for SMB



Run a service enumeration and operation system scan:

```bash
nmap 10.4.17.133 -sV -O
```

<figure><img src="../.gitbook/assets/image (42).png" alt=""><figcaption></figcaption></figure>

Run a service and default script scan:

```bash
nmap 10.4.17.133 -sV -sC
```

<figure><img src="../.gitbook/assets/image (44).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (45).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (46).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (47).png" alt=""><figcaption></figcaption></figure>

### Lab: **Windows Recon: SMB Discover and Mount**

<figure><img src="../.gitbook/assets/image (48).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (49).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (50).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (51).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (52).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (54).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (55).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (56).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (57).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (58).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (60).png" alt=""><figcaption></figcaption></figure>

We have successfully discovered a target host machine and mounted their network shared folder to the attacker machine i.e local machine.

## SMB: Nmap Scripts



## SMB: SMBMap