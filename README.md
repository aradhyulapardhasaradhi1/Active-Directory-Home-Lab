# Active Directory Home Lab --- `pardhu.com`

A beginner-friendly IT Helpdesk L1 practice lab built with VMware
Workstation 17 and Windows Server 2022.

## Project Overview

In this project, I set up a virtual Windows Server environment and
configured the first domain controller for the lab domain `pardhu.com`.
I assigned the server a static IP address and verified basic network/DNS
connectivity using Windows command-line tools.

## What I Completed

-   [x] Installed VMware Workstation 17.
-   [x] Installed Windows Server 2022 in a virtual machine.
-   [x] Configured the server with a static IP address:
    `192.168.211.139`.
-   [x] Promoted the server to a domain controller for `pardhu.com`.
-   [x] Tested network and DNS configuration using `ipconfig /all`,
    `ping`, and `nslookup`.
-   [x] Confirmed that the commands returned the expected details in my
    lab.

## Lab Environment

  Component                 Configuration
  ------------------------- ------------------------------------------------------
  Virtualization software   VMware Workstation 17
  Server operating system   Windows Server 2022
  Lab domain                `pardhu.com`
  Server static IP          `192.168.211.139`
  Main role                 Active Directory Domain Services (domain controller)
  Network checks            `ipconfig /all`, `ping`, `nslookup`

> **Note:** This is a learning lab. The IP address, subnet mask, default
> gateway, and DNS settings should match your VMware virtual network. Do
> not assume a gateway or subnet mask without checking your own network
> configuration.

## Setup Summary

### 1. Install VMware Workstation 17

1.  Install VMware Workstation 17.
2.  Create a new virtual machine.
3.  Attach the Windows Server 2022 installation ISO.
4.  Allocate suitable CPU, RAM, and disk resources for the host
    computer.
5.  Complete the Windows Server installation.

### 2. Configure a Static IP Address

I configured the server to use:

``` text
192.168.211.139
```

To view the complete network configuration, open Command Prompt and run:

``` bat
ipconfig /all
```

Check the IPv4 address, subnet mask, default gateway, and DNS server
entries. For a domain controller, DNS should point to the appropriate
DNS server for the lab---commonly the domain controller itself after DNS
is configured.

### 3. Install Active Directory Domain Services

1.  Open **Server Manager**.
2.  Select **Manage → Add Roles and Features**.
3.  Install **Active Directory Domain Services (AD DS)**.
4.  Install the DNS Server role if required by the lab setup.
5.  After the role installation, select the notification flag in Server
    Manager.
6.  Select **Promote this server to a domain controller**.
7.  Create a new forest for the lab domain: `pardhu.com`.
8.  Complete the wizard and restart the server when prompted.

### 4. Verify Network and DNS

Run these commands in Command Prompt or PowerShell.

#### View IP configuration

``` bat
ipconfig /all
```

Use this to inspect the IPv4 address, subnet mask, gateway, DNS servers,
and network adapter details.

#### Test basic IP connectivity

``` bat
ping 192.168.211.139
```

This tests connectivity to the server's own IP address when run on that
server. To test another device, replace the address with that device's
IP.

#### Test DNS lookup

``` bat
nslookup pardhu.com
```

This checks whether the configured DNS server can resolve the domain
name. The result depends on the lab's DNS configuration and records.

#### Test domain controller name resolution

``` bat
nslookup
```

Review which DNS server is being used, then query the domain
controller's fully qualified domain name if you know it.

> A successful ping to an IP address does not by itself prove that DNS
> or Active Directory is fully working. Check each service separately.

## Skills Practised

-   Virtual machine creation and operating system installation
-   Windows Server 2022 administration basics
-   Static IPv4 configuration
-   Active Directory Domain Services installation
-   Domain controller promotion and domain setup
-   Basic network troubleshooting with `ipconfig`, `ping`, and
    `nslookup`
-   Basic DNS verification

## Disclaimer

This project is for learning and portfolio purposes. `pardhu.com` is
used here as the lab domain name; keep this setup isolated to your test
environment and ensure DNS/network settings are appropriate for your
lab.
