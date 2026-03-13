
# NCL Gym Notes: Nmap & Ncat Guide

A quick cheat‑sheet for **NCL / Cyber Skyline challenges** focusing on
port scanning, service enumeration, and retrieving flags.

Tools covered: - Nmap - Ncat

------------------------------------------------------------------------

# 1. Nmap Basics (Port Scanning)

## Scan a host

``` bash
nmap <IP>
```

Example:

``` bash
nmap 10.0.0.25
```

Purpose: - Finds open ports - Identifies running services

------------------------------------------------------------------------

## Scan all ports

Many flags hide on high ports.

``` bash
nmap -p- <IP>
```

or

``` bash
nmap -p 1-65535 <IP>
```

------------------------------------------------------------------------

## Service version detection

``` bash
nmap -sV <IP>
```

Example output:

    PORT   STATE SERVICE VERSION
    22/tcp open  ssh     OpenSSH
    80/tcp open  http    Apache

------------------------------------------------------------------------

## Default scripts

``` bash
nmap -sC <IP>
```

Runs built-in scripts for: - HTTP titles - FTP anonymous login - SSL
info - other enumeration

------------------------------------------------------------------------

## Combine scans (most common command)

``` bash
nmap -sC -sV <IP>
```

------------------------------------------------------------------------

## Scan specific ports

``` bash
nmap -p 22,80,443 <IP>
```

------------------------------------------------------------------------

## If host appears down

``` bash
nmap -Pn <IP>
```

This skips ping detection.

------------------------------------------------------------------------

# 2. Nmap NSE Scripts

Nmap scripts automate service enumeration.

List scripts:

``` bash
ls /usr/share/nmap/scripts
```

Run scripts:

### NFS enumeration

``` bash
nmap --script nfs* <IP>
```

### RPC enumeration

``` bash
nmap --script rpcinfo <IP>
```

### HTTP enumeration

``` bash
nmap --script http* <IP>
```

------------------------------------------------------------------------

# 3. Ncat Basics

Ncat connects directly to services running on ports.

Common uses: - retrieving flags - interacting with services - sending
commands to servers

------------------------------------------------------------------------

## Connect to a port

``` bash
ncat <IP> <PORT>
```

Example:

``` bash
ncat challenge.server.com 31337
```

------------------------------------------------------------------------

## Verbose connection

``` bash
ncat -v <IP> <PORT>
```

------------------------------------------------------------------------

## Send input to service

``` bash
echo "hello" | ncat <IP> <PORT>
```

------------------------------------------------------------------------

## Listen for connections

``` bash
ncat -l <PORT>
```

Example:

``` bash
ncat -l 4444
```

Used for reverse shells.

------------------------------------------------------------------------

## Send a file

``` bash
ncat <IP> <PORT> < file.txt
```

------------------------------------------------------------------------

# 4. Banner Grabbing

Many services display banners that contain useful information or flags.

Example:

``` bash
ncat <IP> <PORT>
```

Possible output:

    220 Welcome to secret server
    FLAG{example}

------------------------------------------------------------------------

# 5. Common CTF Workflow

## Step 1 --- Scan all ports

``` bash
nmap -p- <IP>
```

## Step 2 --- Identify services

``` bash
nmap -sC -sV <IP>
```

## Step 3 --- Connect to interesting ports

Common ports:

  Port    Service
  ------- -----------------
  21      FTP
  22      SSH
  23      Telnet
  25      SMTP
  80      HTTP
  2049    NFS
  31337   common CTF port

Example:

``` bash
ncat <IP> 31337
```

------------------------------------------------------------------------

## Step 4 --- Try sending commands

Some services respond to input.

Examples:

    help
    flag
    hello
    GET /

------------------------------------------------------------------------

# 6. Troubleshooting

If a port returns nothing:

``` bash
ncat -v <IP> <PORT>
```

If host appears down:

``` bash
nmap -Pn <IP>
```

UDP scan:

``` bash
nmap -sU <IP>
```

------------------------------------------------------------------------

# 7. Quick Command Cheat Sheet

Scan everything:

``` bash
nmap -p- -sC -sV <IP>
```

Connect to port:

``` bash
ncat <IP> <PORT>
```

Send command:

``` bash
echo "flag" | ncat <IP> <PORT>
```

Enumerate NFS:

``` bash
nmap --script nfs* <IP>
```

------------------------------------------------------------------------

# 8. Typical NCL Challenge Patterns

## Hidden Port

Solution:

``` bash
nmap -p- <IP>
```

------------------------------------------------------------------------

## Flag on service

Solution:

``` bash
ncat <IP> <PORT>
```

------------------------------------------------------------------------

## Service requires command

Example:

    ncat <IP> <PORT>
    help
    flag

------------------------------------------------------------------------

## Encoded flags

Common encodings:

-   base64
-   hex
-   rot13

------------------------------------------------------------------------

# Summary

Most NCL networking challenges follow this process:

1.  Scan with Nmap
2.  Identify services
3.  Connect with Ncat
4.  Send commands
5.  Extract the flag
