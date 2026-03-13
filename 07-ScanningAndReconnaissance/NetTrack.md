# NETTRACK

# Netcat (nc) — Net Track Challenge Notes

---

## Who, What, When, Where, Why

**Who** uses `nc`?
Penetration testers, CTF players, sysadmins, and security researchers.

**Who** is the target?
Any server running a custom or unknown service on a TCP/UDP port.

---

**What** is `nc`?
Netcat is a raw networking utility that reads and writes data across TCP/UDP connections. It assumes no protocol — it just sends and receives bytes. Often called the *"Swiss army knife of networking."*

---

**When** do you use `nc`?
- When a service doesn't behave like a standard protocol (HTTP, SSH, FTP)
- When `nmap -sV` fails to fingerprint or misidentifies a service
- When you need to manually interact with a custom server
- During CTF challenges with custom-built servers
- When probing a port to understand what it does

---

**Where** does `nc` connect?
Directly to a hostname/IP and port over TCP (or UDP with `-u`). No protocol is assumed — raw bytes go in and come out.

---

**Why** use `nc` over other tools?
- Tools like `nmap -sV` send known protocol probes — custom servers may close or ignore them
- `nc` lets you interact manually and freeform
- Lightweight, available on almost every Linux system by default
- Great for discovering undocumented or custom server behavior

---

## The Anomaly — Why nmap -sV Closes the Port

```bash
# Without -sV: port shows as open
nmap [hostname] -p 8090
# PORT      STATE  SERVICE
# 8090/tcp  open   opsmessaging

# With -sV: port shows as closed
nmap [hostname] -p 8090 -sV
# PORT      STATE   SERVICE       VERSION
# 8090/tcp  closed  opsmessaging
```

**Why this happens:**
`nmap -sV` sends protocol-specific probes to fingerprint the service. The custom server likely detects this unexpected input and closes the connection. This is a signal that the service is non-standard and needs manual interaction.

---

## Connecting with Netcat

```bash
nc [hostname] [port]

# Example
nc challenge.server.com 8090
```

Once connected, the terminal appears to hang — but it's actually waiting for your input. Type freely and press Enter to send.

---

## Interacting with the Server

### Step 1 — Send anything to get a hint
```
hello
```
**Response:**
```
Use help to get a list of supported commands
```

---

### Step 2 — Get available commands
```
help
```
**Response:**
```
Here is a list of commands
version
list
get
help
```

---

### Step 3 — Check the server version
```
version
```
Returns the version info of the server software running.

---

### Step 4 — List files on the server
```
list
```
Returns a directory listing of files available on the remote server.

---

### Step 5 — Retrieve a file's contents
```
get [filename]
```

**Example:**
```
get flag.txt
get readme.txt
get notes.txt
```

Returns the raw text content of the file. Iterate through all files from `list` until you find the flag.

---

## Finding File Sizes

Since this is a plain text server with no `stat` or `ls -lh` equivalent, you calculate size manually:

> **Each character in a text file = 1 byte**

So if `get secret.txt` returns:
```
Hello World
```
That's 11 characters = **11 bytes**.

**Workflow to find all file sizes:**
1. Run `list` to get all filenames
2. Run `get [filename]` on each file
3. Count the characters in the output
4. That count = the file size in bytes


---

## Full Challenge Workflow Summary

```bash
# 1. Connect
nc challenge.server.com 8090

# 2. Explore
help
version
list

# 3. Get each file
get file1.txt
get file2.txt
get flag.txt   # <-- flag will be in one of these

# 4. Note character count of each file output = file size in bytes
```

---

## Key Takeaways

| Concept | Detail |
|---|---|
| `nc` connects raw | No protocol assumed, just TCP bytes |
| `nmap -sV` can break things | Service probes may cause custom servers to close |
| Custom servers have custom commands | Always try `help` first |
| Text file size | 1 character = 1 byte |
| Flag hunting | Use `list` then `get` on each file |



## Cyber Gym Challenges

1. What is the name and version of the software?
Run this command `nc net-track.services.cityinthe.cloud 8080` to connect the host,  then type in help to see list of available commands (User version command)  Answer --  Radicalshell v9
-----
2. What is the flag?
Make sure you are connected to the host. Use the list command to list files and then get each file to find the file containing information regarding the flag. (The file to get is secret). `Answer -- SKY-NCAT-3071`
-----
3. What is the size of the largest file in bytes?
Every character in a file takes up 1 byte. Get every file and find the file with the most characters and use a character counter to give u an exact amount of characters in the file (1 character = 1 byte) `Answer -- 40`
-----
