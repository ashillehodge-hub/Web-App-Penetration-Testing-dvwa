# Web Application Security Auditing, DVWA Exploitation & Traffic Analysis

## Overview
This repository documents offensive security testing, web vulnerability assessments, and traffic interception techniques executed within an isolated Kali Linux laboratory environment. It covers the exploitation of common OWASP Top 10 flaws, cleartext credential leakage, proxy-based session hijacking, and structured defensive remediations.

---

## Laboratory Assessments & Findings

### 1. OWASP Top 10 Vulnerabilities on DVWA
Executed black-box and gray-box testing against Damn Vulnerable Web Application (DVWA) targets across Low and Medium security tiers:
* **OS Command Injection:** Exploited improper input sanitization in ping utilities to execute arbitrary shell commands (`&& ls`, `| ls`, path enumeration) on the underlying host operating system.
* **Local File Inclusion (LFI / Path Traversal):** Leveraged unvalidated page parameters to perform directory traversal (`../../../../etc/passwd`), exposing sensitive system files and application files.
* **SQL Injection (SQLi):** Deployed SQLMap to perform error-based and UNION-based blind SQL injection, successfully mapping backend database schemas, extracting table data, and enumerating database versions (MySQL/MariaDB).

### 2. Network Sniffing & Traffic Interception
* **Wireshark Cleartext Interception:** Captured Layer 7 HTTP traffic to isolate unencrypted POST requests during login sequences, exposing cleartext credentials (`uid`, `passw`) and session identifiers (`JSESSIONID`).
* **Burp Suite Proxy Man-in-the-Middle (MitM):** Configured Burp Suite to intercept, modify, and replay client-server HTTP requests, demonstrating session token hijacking and brute-force authentication attacks.

---

## Defensive Remediations & Best Practices
* **Input Validation & Sanitization:** Enforce strict allow-lists (whitelisting) and proper escaping for all user-supplied input to neutralize injection vectors.
* **Parameterized Queries:** Prevent SQL injection by utilizing prepared statements and parameterized database queries.
* **Secure Session Management:** Enforce `HttpOnly`, `Secure`, and `SameSite` flags on all session cookies to mitigate session theft and XSS exposure.
* **Multi-Factor Authentication (MFA):** Implement robust MFA protocols and robust password policies to prevent credential harvesting and brute-force attacks.

---

## Repository Artifacts
* `Kali Linux Lab Ashille Hodge.pdf` — Kali Linux environment setup, package management, and basic command documentation.
* `Network Security Analysis- Wireshark Packet Inspection, Burp Suite Session Interception & DVWA Vulnerability Assessment.pdf` — Wireshark pcap analysis, Burp Suite MitM walkthroughs, and DVWA exploitation reports.
* `Social Engineering and Web application Attacks Ashille Hodge.pdf` — Social engineering simulations, phishing hook methodologies, and SQL injection database extractions.
