
# 🛡 Reconnaissance Attack Scenario with Techniques

### 🎯 *Target*: amsys.uettaxila.edu.pk  
*Objective*: Gather intelligence, identify vulnerabilities, and map the attack surface using 5 tools.

---

## 🔍 1. *Whois* – Domain Registration & Ownership Info  

**Command:**
```bash
whois amsys.uettaxila.edu.pk
```

**Techniques Used:**
- T1589.002 – Gather Victim Identity: Email Addresses
- T1590.001 – Gather Infrastructure: Domain Properties

**Purpose:**
- Discover domain registrar, creation/expiry dates
- Identify admin contacts, emails, and hosting provider

**Findings:**
- Admin email: admin@uettaxila.edu.pk
- Nameservers: ns1.uettaxila.edu.pk, ns2.uettaxila.edu.pk

---

## 🧠 2. *theHarvester* – Email & Subdomain Enumeration  

**Command:**
```bash
theHarvester -d uettaxila.edu.pk -b google
```

**Techniques Used:**
- T1589.001 – Gather Victim Identity: Employee Names
- T1590.002 – Gather Infrastructure: DNS
- T1592.002 – Gather Technical Info: Software Platforms

**Purpose:**
- Collect emails, subdomains, and employee names from public sources

**Findings:**
- Emails: itdept@uettaxila.edu.pk, support@uettaxila.edu.pk
- Subdomains: cms.uoc.edu.pk, mail.uettaxila.edu.pk

---

## 🌐 3. *Dig* – DNS Enumeration  

**Command:**
```bash
dig amsys.uettaxila.edu.pk any
```

**Techniques Used:**
- T1590.002 – Gather Infrastructure: DNS
- T1590.003 – Gather Infrastructure: Network Trust Dependencies

**Purpose:**
- Discover DNS records (A, MX, NS, TXT)
- Identify mail servers, SPF records, and misconfigurations

**Findings:**
- A record: 111.68.98.140
- MX record: mail.uettaxila.edu.pk
- TXT record: SPF policy allows ~all — weak configuration

---

## 🔎 4. *Nmap* – Port Scanning & Service Detection  

**Command:**
```bash
nmap -sV -T4 -A amsys.uettaxila.edu.pk
```

**Techniques Used:**
- T1595.002 – Active Scanning: Service Scanning
- T1595.001 – Active Scanning: Discovery
- T1580 – Identify Vulnerabilities

**Purpose:**
- Identify open ports, services, and OS
- Detect web server type and SSL certificate

**Findings:**
- Open ports: 80 (HTTP), 443 (HTTPS)
- Web server: Microsoft IIS 10.0
- SSL cert: Cloudflare Origin, valid till 2037
- OS: Linux (likely hardened)

---

## 🧪 5. *Nikto* – Web Vulnerability Scanning  

**Command:**
```bash
nikto -h https://amsys.uettaxila.edu.pk
```

**Techniques Used:**
- T1595.002 – Active Scanning: Service Scanning
- T1592.001 – Gather Technical Info: System Info
- T1580 – Identify Vulnerabilities

**Purpose:**
- Scan for outdated software, misconfigurations, and known vulnerabilities

**Findings:**
- IIS 10.0 exposes verbose headers
- Kerio MailServer interface detected
- No rate limiting on login page
- Potential XSS or outdated plugins (if found)

---

## 🧩 Final Attack Chain Summary

| Phase              | Tool         | Techniques Used                          | Outcome                          |
|--------------------|--------------|------------------------------------------|----------------------------------|
| Passive Recon      | Whois        | T1589.002, T1590.001                      | Domain info, admin contacts      |
| Passive Recon      | theHarvester | T1589.001, T1590.002                      | Emails, subdomains               |
| DNS Enumeration    | Dig          | T1590.002, T1590.003                      | Mail servers, SPF weakness       |
| Active Recon       | Nmap         | T1595.001, T1595.002, T1580              | Open ports, OS, services         |
| Vulnerability Scan | Nikto        | T1595.002, T1592.001, T1580              | Web server flaws, login exposure |

---

## 🧠 Next Steps (Hypothetical Exploitation)
- Credential Stuffing using harvested emails on login page
- Phishing Campaign targeting support@uettaxila.edu.pk
- Subdomain Takeover if cms.uoc.edu.pk is misconfigured
- Exploit IIS or Kerio vulnerabilities if outdated
