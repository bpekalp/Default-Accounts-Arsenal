# Default Accounts Arsenal 🎯

A comprehensive collection of username and password wordlists designed for penetration testing and security research purposes.

## 📋 Table of Contents

- [Overview](#-overview)
- [Contents](#-contents)
- [Username List](#-username-list)
- [Password List](#-password-list)
- [Usage Examples](#-usage-examples)
- [Sources](#-sources)
- [Disclaimer](#-disclaimer)

## 🔍 Overview

This repository contains carefully curated wordlists that combine commonly used usernames and passwords found in real-world scenarios. These lists are intended for:

- Penetration testing engagements
- Security assessments
- Red team operations
- Educational purposes
- Security research

## 📦 Contents

- `username.txt` - 81 common usernames and their variations
- `passwords.txt` - 40,965 merged and deduplicated passwords

## 👤 Username List

The username list includes **81 entries** covering common default accounts **and their derivatives**:

### System Accounts & Variations
- **Base accounts**: admin, root, user, guest, system
- **Derivatives**: administrator, sysadmin, localadmin, cloudadmin, webadmin

### Database Defaults
- **MySQL/MariaDB**: mysql, mariadb
- **PostgreSQL**: postgres, postgresql, postmaster
- **MongoDB**: mongo, mongodb
- **Oracle**: oracle, db2
- **Redis & Cassandra**: redis, cassandra
- **MSSQL**: mssql, sqlserver

### Web Services & Variants
- **Apache**: apache, httpd
- **Nginx**: nginx
- **Tomcat**: tomcat
- **Web users**: www, www-data, webmaster

### DevOps Tools & Derivatives
- **Container platforms**: docker, kubernetes, k8s
- **CI/CD**: jenkins, gitlab, gitea, bamboo, circleci, travis
- **Configuration management**: ansible, puppet, chef, terraform

### Cloud Platforms & Related
- **Azure**: azure, azureuser
- **AWS**: aws, ec2-user
- **GCP**: gcp, opc
- **Generic**: cloud-user

### Service Accounts
- backup, ftp, mail, smtp, ssh, support, helpdesk, operator

### Legacy & Special Accounts
- nobody, nologin, bin, daemon, service, toor, vagrant, defaultuser0

> **Note**: This list focuses on default credentials and common naming patterns found across various systems, services, and platforms.

## 🔐 Password List

The password list contains **40,965 unique entries** - a merged and deduplicated compilation from the following sources:

- **rockyou-65** (weakpass.com)
- **ignis-10k** (weakpass.com)
- **10_million_password_list_top_10000** (weakpass.com)
- **russkiwlst_top_10k** (weakpass.com)

All duplicate entries have been removed to create an optimized, high-quality wordlist suitable for efficient brute-force testing.

## 🛠️ Usage Examples

### Hydra (SSH Brute Force)
```bash
hydra -L username.txt -P passwords.txt ssh://target-ip -t 4
```

### Hydra (HTTP Form)
```bash
hydra -L username.txt -P passwords.txt target-ip http-post-form "/login:username=^USER^&password=^PASS^:F=incorrect"
```

### Medusa (Multiple Services)
```bash
medusa -h target-ip -U username.txt -P passwords.txt -M ssh -t 4
medusa -h target-ip -U username.txt -P passwords.txt -M ftp
```

### Metasploit
```ruby
use auxiliary/scanner/ssh/ssh_login
set RHOSTS target-ip
set USER_FILE username.txt
set PASS_FILE passwords.txt
set THREADS 10
run
```

### Nmap NSE Scripts
```bash
# SSH brute force
nmap --script ssh-brute --script-args userdb=username.txt,passdb=passwords.txt -p 22 target-ip

# HTTP brute force
nmap --script http-brute --script-args userdb=username.txt,passdb=passwords.txt target-ip
```

### CrackMapExec
```bash
# SMB
crackmapexec smb target-ip -u username.txt -p passwords.txt

# SSH
crackmapexec ssh target-ip -u username.txt -p passwords.txt --threads 10

# WinRM
crackmapexec winrm target-ip -u username.txt -p passwords.txt
```

### Patator
```bash
patator ssh_login host=target-ip user=FILE0 password=FILE1 0=username.txt 1=passwords.txt -x ignore:mesg='Authentication failed'
```

### Burp Suite Intruder
1. Load `username.txt` as payload list 1
2. Load `passwords.txt` as payload list 2
3. Set attack type to "Cluster bomb" or "Pitchfork"
4. Configure grep match for successful authentication

## 📚 Sources

- [WeakPass.com](https://weakpass.com/) - Password wordlist collections
- System documentation and default credentials databases
- Common cloud platform defaults
- DevOps tool documentation
- Official vendor security advisories

## ⚠️ Disclaimer

**IMPORTANT**: This tool is provided for educational and authorized security testing purposes only.

### Legal Notice

- ✅ **Legal Use**: Only use these wordlists against systems you own or have explicit written permission to test
- ❌ **Illegal Use**: Unauthorized access to computer systems is illegal in most jurisdictions (CFAA, Computer Misuse Act, etc.)
- 🎯 **Ethics**: Always follow responsible disclosure practices
- 📜 **Compliance**: Ensure your testing complies with all applicable laws and regulations
- 🔒 **Authorization**: Maintain documentation of testing authorization

### User Responsibility

The author and contributors assume **no liability** for misuse of these materials. Users are **solely responsible** for their actions and must ensure compliance with:

- Local, state, and federal laws
- Organizational policies
- Industry regulations (PCI-DSS, HIPAA, GDPR, etc.)
- Ethical hacking guidelines

**Unauthorized access is a crime. Use responsibly.**
