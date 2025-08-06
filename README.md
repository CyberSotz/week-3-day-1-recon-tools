# 🛡️ Week 3-day-1 – Reconnaissance Tools Presentation

**Presented by:** Muhammad Naveed  
**Training Program:** Cybersecurity Fundamentals – KaiRiz  
**Week:** 3  
**Focus:** Reconnaissance Tools in Kali Linux  

---

## 📌 Overview

Reconnaissance is the first and one of the most critical phases in the penetration testing lifecycle. In this week, we explored five major tools used to gather information about target systems before launching active attacks.

This presentation focuses on:

- 🕵️‍♂️ Reconnaissance techniques  
- 🧰 Recon tools: Nmap, Whois, Dig, The Harvester, Nikto  
- 🏁 Practical examples using: `http://amsys.uettaxila.edu.pk`

---

## 🔍 Nmap – Network Mapper

**Category:** Network Scanning  
**Purpose:** Host discovery, port scanning, OS and service fingerprinting, vulnerability detection.

### Key Features

- Host discovery (`-sn`)  
- Port scanning (`-p`, `-p-`, `--top-ports`)  
- Scan types: TCP SYN (`-sS`), TCP Connect (`-sT`)  
- OS & service detection: `-O`, `-sV`  
- NSE scripts for vulnerability detection  
- Output options: `-oN`, `-oX`, `-oG`, `-oA`

### Example

```bash
nmap -A -T4 amsys.uettaxila.edu.pk
```

---

## 🌐 Whois – Domain Information Lookup

**Category:** Passive Recon / OSINT  
**Purpose:** Retrieves domain registration details.

### Provides:

- Registrar details  
- Domain creation/expiration dates  
- Contact email & administrative info  
- DNS name servers  

### Example

```bash
whois amsys.uettaxila.edu.pk
```

---

## 🧭 Dig – DNS Interrogation

**Category:** DNS Enumeration  
**Purpose:** Queries DNS records (A, MX, TXT, NS, etc.)

### Common Uses:

- Identify authoritative name servers  
- Extract zone information  
- Discover mail servers and subdomains  

### Examples

```bash
dig any amsys.uettaxila.edu.pk  
dig MX amsys.uettaxila.edu.pk  
dig NS amsys.uettaxila.edu.pk
```

---

## 📧 The Harvester – OSINT Data Collection

**Category:** Email & Subdomain Enumeration  
**Purpose:** Collects emails, subdomains, and IPs from public sources

### Sources:

- Google, Bing, Yahoo, Baidu, etc.  
- Subdomain discovery  
- OSINT emails and links

### Example

```bash
theHarvester -d amsys.uettaxila.edu.pk -b google
```

---

## 🛡️ Nikto – Web Vulnerability Scanner

**Category:** Web Server Scanning  
**Purpose:** Identifies vulnerabilities, outdated software, insecure files, and more.

### Key Features

- Checks over 6700 items  
- Detects outdated versions  
- Detects dangerous files and configuration issues

### Example

```bash
nikto -h http://amsys.uettaxila.edu.pk
```

---

## ⚔️ Comparison Table

| Tool         | Type            | Main Purpose                    | Passive / Active |
|--------------|------------------|----------------------------------|------------------|
| Nmap         | Network Scanner  | Port, OS, service, vuln scan     | Active           |
| Whois        | OSINT            | Domain registration details      | Passive          |
| Dig          | DNS Query        | DNS records and domain mapping   | Passive          |
| Harvester    | OSINT            | Email and subdomain enumeration  | Passive          |
| Nikto        | Web Scanner      | Web server misconfiguration      | Active           |

---

## 🎯 Target Recon Summary

**Target:** http://amsys.uettaxila.edu.pk

Each tool provided a different layer of information:

- Nmap: Open ports, OS, running services  
- Whois: Domain ownership  
- Dig: DNS structure and mail servers  
- Harvester: Email enumeration  
- Nikto: Web server misconfiguration detection

---

## 📚 Conclusion

These tools form the core of reconnaissance in ethical hacking. When used together, they offer a complete blueprint of the target's infrastructure — helping us in both offensive and defensive security tasks.

> “Know the terrain before you step onto the battlefield.”
