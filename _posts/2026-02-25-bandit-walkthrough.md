---
title: "Bandit Walkthrough (OverTheWire)"
date: 2026-02-25
categories: [CTF, Linux]
tags: [Bandit, OverTheWire, SSH, Linux, Networking]
---

# Introduction

Bandit is a beginner-friendly wargame created by OverTheWire to teach fundamental Linux and security concepts.

Instead of focusing on advanced exploitation, Bandit builds strong foundations in:

- Linux command-line usage
- File navigation and manipulation
- SSH authentication
- Networking basics
- Encoding & decoding
- Privilege concepts (SUID, ownership, permissions)

This article summarizes the key concepts I learned while solving the levels.

---

## Level 0 → Level 1

**Concept Learned: SSH Authentication**

```bash
ssh bandit0@bandit.labs.overthewire.org -p 2220
```

Key components:

- **ssh** → Secure remote login tool  
- **-p 2220** → Custom SSH port  
- **bandit0** → Username  
- **bandit.labs.overthewire.org** → Target server  

**Takeaway:**  
Understanding SSH is essential for penetration testing and remote server interaction.

---

## Level 1 → Level 2

**Concept Learned: File Listing & Reading Content**
```bash
ls  
cat readme
```

**Takeaway:**  
Basic file navigation is the starting point of any CTF or system analysis task.

---

## Level 2 → Level 3

**Concept Learned: Handling Special Characters in Filenames**

```bash
cat "file name"
```

**Takeaway:**  
Escaping or quoting filenames is critical when dealing with irregular file naming.

---

## Level 3 → Level 4

**Concept Learned: Hidden Files**

```bash
ls -a
```

**Takeaway:**  
Hidden files often store sensitive configuration or credentials.

---

## Level 4 → Level 5

**Concept Learned: Identifying File Types**

```bash
file <filename>
```

**Takeaway:**  
Identifying file types is crucial before analyzing or extracting data.

---

## Level 5 → Level 6

**Concept Learned: Advanced File Searching**

```bash
find . -type f -size 1033c ! -perm /111
```

**Takeaway:**  
Precise filtering saves time when searching large systems.

---

## Level 6 → Level 7

**Concept Learned: Searching by Ownership**

```bash
find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
```

**Takeaway:**  
Ownership-based filtering is useful in privilege investigations.

---

## Level 7 → Level 8

**Concept Learned: Grep & Pipes**

```bash
cat data.txt | grep "millionth"
```

**Takeaway:**  
Combining commands with pipes increases efficiency.

---

## Level 8 → Level 9

**Concept Learned: Sorting & Unique Lines**

```bash
sort data.txt | uniq -u
```

**Takeaway:**  
Data filtering is essential in log analysis.

---

## Level 9 → Level 10

**Concept Learned: Extracting Strings from Binary Files**

```bash
strings data.txt | grep "====="
```

**Takeaway:**  
Binary files often contain readable strings useful in analysis.

---

## Level 10 → Level 11

**Concept Learned: Base64 Decoding**

```bash
base64 -d data.txt
```

Alternative approach:  
Use CyberChef → From Base64

**Takeaway:**  
Encoding schemes are common in security challenges.

---

## Level 11 → Level 12

**Concept Learned: ROT13 Cipher**

```bash
tr 'A-Za-z' 'N-ZA-Mn-za-m'
```

Alternative approach:  
Use CyberChef → ROT13

**Takeaway:**  
Simple substitution ciphers appear frequently in CTFs.

---

## Level 12 → Level 13

**Concept Learned: Multi-layer Compression**

```bash
file data.txt
gzip -d file.gz
bzip2 -d file.bz2
tar -xf file.tar
```

**Takeaway:**  
Understanding file formats is important during forensic analysis.

---

## Level 13 → Level 14

**Concept Learned: SSH Key Authentication**

```bash
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
```

**Takeaway:**  
Key-based authentication is more secure than passwords.

---

## Level 14 → Level 15

**Concept Learned: Netcat Communication**

```bash
nc localhost 30000
```

**Takeaway:**  
Understanding raw network connections is crucial in service exploitation.

---

## Level 15 → Level 16

**Concept Learned: SSL/TLS Connections**

```bash
ncat --ssl localhost 30001
```

**Takeaway:**  
Some services require encrypted communication.

---

## Level 16 → Level 17

**Concept Learned: Port Scanning**

```bash
nmap -p 31000-32000 localhost
```

**Takeaway:**  
Identifying open ports is a core penetration testing skill.

---

## Level 17 → Level 18

**Concept Learned: File Comparison**

```bash
diff passwords.old passwords.new
```

**Takeaway:**  
Comparing data differences helps detect changes.

---

## Level 18 → Level 19

**Concept Learned: Bypassing Modified Shell Configuration**

```bash
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

**Takeaway:**  
Executing commands directly over SSH can bypass restricted shells.

---

## Level 19 → Level 20

**Concept Learned: SUID Binaries**

```bash
./bandit20-do <command>
```

**Takeaway:**  
SUID binaries can execute commands with elevated privileges.

---

## Level 20 → Level 21

**Concept Learned: Local Listener & Service Interaction**

Steps:

1. Start a local netcat listener.  
2. Execute the SUID binary with the listener port.  
3. Exchange credentials through the connection.  

**Takeaway:**  
Understanding networking flow is essential in privilege-based challenges.

---

# Final Thoughts

Bandit is not about exploitation — it's about foundations.

It strengthened my understanding of:

- Linux navigation  
- File permissions  
- Networking basics  
- Encoding/decoding  
- Privilege concepts  

These fundamentals are essential before moving into advanced web exploitation and bug bounty hunting.
