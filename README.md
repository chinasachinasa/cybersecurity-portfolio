# 👋 Hi, I am Ali Chinasa Juliet

**Cybersecurity Analyst | SOC Operations | Digital Forensics | Threat Intelligence**

📧 chinasachinasa2014@gmail.com | chinasaali@yahoo.co.uk 
🌍 Lagos, Nigeria  
💼 https://www.linkedin.com/in/chinasa-ali-31a2a8a7 | 🔗 https://github.com/chinasachinasa/cybersecurity-portfolio

---

##  About Me

I am a passionate cybersecurity professional specializing in Security Operations Center (SOC) analysis, incident response, digital forensics, and threat intelligence. As a graduate of the **Girls in Security Operations (GiSOC) Bootcamp**, I've developed hands-on expertise in detecting, investigating, and responding to real-world security threats.

My work focuses on transforming complex security data into actionable intelligence that protects organizations from cyber threats. I combine technical proficiency with analytical thinking to identify vulnerabilities, investigate incidents, and implement robust security measures.

**Core Competencies:**
- 🔍 Digital Forensics & Evidence Analysis
- 🚨 Incident Response & Threat Hunting
- 🎯 Threat Intelligence & Attack Attribution
- 🛡️ Vulnerability Assessment & Management
- 📊 SIEM Operations & Log Analysis
- 🦠 Malware Analysis (Static & Dynamic)
- ☁️ Cloud Security (AWS)

---

## 🛠️ Technical Skills

**Security Tools & Platforms:**
- **SIEM & Monitoring:** Splunk Enterprise, Elastic Security
- **Forensics:** FTK Imager, Registry Explorer, Autopsy
- **Malware Analysis:** PEStudio, Process Monitor, Regshot, Wireshark, REMnux, FlareVM
- **Vulnerability Management:** Nessus Essentials
- **Threat Intelligence:** AlienVault OTX, VirusTotal, CISA KEV Catalog
- **Database Analysis:** DB Browser for SQLite, Kernel OST Viewer
- **Cloud Security:** AWS CloudTrail, VPC Flow Logs, Elastic Defend

**Frameworks & Methodologies:**
- MITRE ATT&CK Framework
- Incident Response Lifecycle
- Digital Forensics Chain of Custody
- CVSS Risk Scoring
- NIST Cybersecurity Framework

---

## 📁 Featured Projects

### 🔍 [Digital Forensics Investigation - Horcrux Disk Image Analysis]
**Case Reference:** HORCRUX-FORENSICS-001 | **Date:** December 2025

Conducted comprehensive forensic examination of a Windows disk image to investigate potential insider threat activity involving user "Karen" and suspicious external communications with entity "TAAUSAI."

**Key Investigation Findings:**
- Discovered intentionally deceptive hostname "TOTALLYNOTAHACK" indicating security awareness
- Uncovered external communications offering $150,000 upfront payment
- Traced international meeting location to Egypt through email coordinate analysis
- Recovered deleted artifacts from browser history (Chrome v72.0.3626.121), Skype communications, and OST email files
- Established complete timeline correlating document access with suspicious job offer discussions

**Forensic Artifacts Recovered:**
- Registry hives (SAM, SYSTEM) for user account and system configuration analysis
- Browser SQLite databases (Web Data, History) containing download URLs and autofill data
- OST email files revealing communications with "Micheal Scotch" from TAAUSAI
- File metadata showing AlpacaCare.docx access patterns
- Secondary partition analysis (Drive A: PacaLady) containing Skype installer

**Technical Skills Demonstrated:**  
Registry forensics, email artifact recovery (Kernel OST Viewer), browser history analysis, SQLite database examination, timeline correlation, evidence preservation, chain of custody maintenance

**Tools Used:** FTK Imager 8.2.0.26, Registry Explorer v2.1.0, DB Browser for SQLite, Kernel OST Viewer, 7-Zip

---

### 🚨 [Incident Response - AWS SSH Brute Force Attack]
**Severity:** High (Risk Score 88) | **Date:** September 2025

Responded to high-severity alert involving suspicious SSH connection attempts targeting AWS EC2 infrastructure. Led complete investigation from initial detection through containment and remediation.

**Attack Timeline:**
- **04:18:34 UTC** - Initial SSH attempt detected from 18.206.107.29
- **04:20:04 UTC** - Elastic Security alert triggered (risk score 88)
- **06:27:00 UTC** - Investigation initiated
- **06:35:00 UTC** - Decision to isolate host
- **06:40:00 UTC** - Host successfully isolated via Elastic Defend

**Investigation Results:**
- Identified scanning campaign targeting multiple EC2 instances (i-06630d676df556c70)
- Analyzed attack patterns from three related IPs: 18.206.107.29, 18.206.107.27, 102.89.68.233
- Source IPs traced to compromised AWS infrastructure being used as launch point
- Confirmed unsuccessful compromise attempts due to key-based authentication
- Prevented potential lateral movement through timely host isolation

**Response Actions:**
- Isolated affected EC2 instance (54.196.228.242) using Elastic Defend
- Added malicious IPs to AWS Security Group deny rules
- Rotated SSH keys as precautionary measure
- Restricted SSH access to VPN IP ranges only
- Created custom watchlist and enhanced monitoring rules

**Recommendations Implemented:**
- Bastion host architecture for SSH access
- SSH port change to reduce scanning exposure
- Just-in-time access implementation for production instances
- Enhanced alert correlation for related scanning attempts

**Technical Skills Demonstrated:** Cloud security (AWS), incident response, host isolation, log correlation (CloudTrail, VPC Flow Logs), threat hunting, security group hardening, MITRE ATT&CK mapping (T1021.004, T1110, T1190)

**Tools Used:** Elastic Security, AWS CloudTrail, VPC Flow Logs, Elastic Defend

---

### 🦠 [Malware Analysis - Mamba Ransomware Investigation]
**Sample Hash:** 2ecc525177ed52c74ddaaacd47ad513450e85c01f2616bf179be5b576164bf63 | **Date:** November 2025

Performed comprehensive static and dynamic analysis of Mamba ransomware sample (131.exe) in isolated laboratory environment. Documented complete disk encryption behavior using embedded DiskCryptor components.

**Static Analysis Findings:**
- File size: 2.30 MB, 32-bit Windows executable
- VirusTotal detection: Flagged by majority of security vendors as ransomware/DiskCryptor threat
- Embedded components: Multiple DiskCryptor drivers, installers, and console utilities for both 32-bit and 64-bit systems
- Requested administrative privileges confirming system-level operations
- String analysis revealed disk mounting operations and driver-related functions

**Dynamic Analysis Results:**
- **Registry Modifications:** Changed 100+ registry values, removed thousands of existing keys
- **Boot Configuration:** Created new keys linked to DiskCryptor and altered boot behavior
- **Process Activity:** Spawned processes tied to embedded DiskCryptor executables
- **Driver Installation:** Wrote drivers and support files to disk
- **Network Behavior:** Outbound HTTP requests captured by INetSim (potential C2 communication)

**Attack Chain Documented:**
1. Initial execution with administrative rights
2. DiskCryptor driver installation to system
3. Registry modification for boot persistence
4. Service creation for encryption preparation
5. Full disk encryption upon next reboot
6. Complete system lockout

**Impact Assessment:**
- Total loss of system access post-reboot
- Recovery only possible through offline backups or complete system rebuild
- High-impact threat requiring immediate detection and response

**Lab Environment:**
- FlareVM and REMnux (host-only network)
- INetSim for controlled DNS and HTTP responses
- Complete isolation from production networks

**Technical Skills Demonstrated:** Malware reverse engineering, sandbox analysis, static analysis (PE structure, strings, imports), dynamic analysis (registry, process, network monitoring), behavioral analysis, safe lab setup and containment

**Tools Used:** PEStudio, Strings, VirusTotal, HashMyFile, Regshot, Process Monitor, Wireshark, REMnux, FlareVM, INetSim

---

### 🔐 [Vulnerability Management - Nessus Security Assessment]
**Target Environment:** Ubuntu 192.168.75.4 | **Date:** October 2025

Conducted comprehensive vulnerability assessment in controlled SOC lab environment, identifying critical security weaknesses in outdated Nginx and OpenSSL configurations.

**Discovered Vulnerabilities:**

**CVE-2019-20372 (Nginx Information Disclosure)**
- CVSS Score: 5.3 (Medium)
- Affected Version: Nginx 1.15.5
- Exploit Status: Publicly available
- Impact: Version exposure through HTTP headers enables targeted reconnaissance
- Risk: Medium - facilitates further attacks through version-specific exploit identification

**CVE-2025-9230 & CVE-2025-9232 (OpenSSL CMS Decryption)**
- CVSS Score: 7.5 (High)
- Affected Version: OpenSSL 1.0.2
- Exploit Status: No known public exploit
- Impact: Out-of-bounds read/write during CMS decryption
- Risk: High - potential denial of service, memory corruption, sensitive data exposure

**Risk Assessment:**
- Combined vulnerabilities significantly reduce system resilience
- Information leakage enables reconnaissance for targeted attacks
- Service disruption risk threatens business continuity
- Highlights critical need for consistent patch management

**Remediation Recommendations:**
- Upgrade Nginx to version 1.17.7+ to eliminate version disclosure
- Update OpenSSL to latest stable release (1.0.2m or later)
- Implement version obfuscation in Nginx configuration
- Establish regular patch schedule and vendor update monitoring
- Conduct periodic vulnerability scans
- Monitor software end-of-life announcements

**Lab Configuration:**
- Scanner: Kali Linux VM with Nessus Essentials
- Target: Ubuntu VM hosting intentionally vulnerable services
- Network: Isolated testing environment

**Challenges Resolved:**
- SSH arcfour cipher compatibility (migrated to 3des-cbc)
- Nessus plugin installation issues

**Technical Skills Demonstrated:** Vulnerability scanning, risk assessment, CVSS scoring, patch management, remediation planning, security hardening, compliance documentation

**Tools Used:** Nessus Essentials, Kali Linux, Ubuntu

---

### 🎯 [Threat Intelligence Research - Multi-CVE Analysis]
**Vulnerabilities Assessed:** CVE-2019-20372, CVE-2025-9230, CVE-2025-46727 | **Date:** October 2025

Comprehensive threat intelligence assessment of three critical vulnerabilities, including real-world exploitation patterns, APT attribution, malware family analysis, and business risk quantification.

**CVE-2019-20372 (Nginx HTTP Request Smuggling) - CVSS 5.3**

**Threat Actor Attribution:**
- Confirmed exploitation in APT campaigns
- Public PoC available enabling widespread exploitation

**Associated Malware Families (via AlienVault OTX):**
- PlugX RAT - Full remote control, keylogging, encrypted C2
- PoisonIvy RAT - Credential theft, screen capture, network tunneling
- FormerFirstRat, Sysget/HelloBridge, NFlog, NewCT

**Attack Methodology:**
- Exploit Nginx parsing inconsistencies to bypass WAF/IPS
- Deploy RAT on backend servers without triggering alerts
- Enable long-term espionage with reduced detection risk

**MITRE ATT&CK Mapping:**
- T1190: Exploit Public-Facing Application (Initial Access)
- T1562.001: Impair Defenses - Disable/Modify Tools (Defense Evasion)
- T1213: Data from Information Repositories (Collection)
- T1071.001: Web Protocols (Command & Control)

**Business Risk Assessment:**
- Corporate espionage and IP theft potential
- Data breach leading to regulatory penalties
- Session hijacking and account takeover
- Operational disruption and brand damage

**CVE-2025-46727 (Rack Ruby Unbounded Parameter DoS) - CVSS 7.5**

**Threat Intelligence:**
- **CISA KEV Listed** - Confirmed active exploitation in the wild
- Date Added: May 7, 2025
- Affects 1+ billion Rack installations globally (Ruby on Rails, Sinatra, Padrino)

**Technical Details:**
- Rack::QueryParser lacks parameter count limits
- Attackers send hundreds of thousands of parameters
- Results in memory exhaustion and complete denial of service
- Attack Vector: Network-based, low complexity, no authentication required

**Likely Threat Actors:**
- Advanced Persistent Threat (APT) Groups - Likelihood: MEDIUM-HIGH
- Limited public IOCs due to recent disclosure

**Financial Impact Assessment:**
- Downtime losses: Up to $500,000 per hour
- SLA penalties and emergency response costs
- Annual exposure: $185,000 - $1.7 million (60% probability)

**Compliance Implications:**
- Threatens SOC 2, ISO 27001 A.12.6.1, PCI-DSS Requirement 6 compliance
- Failures in availability and vulnerability management controls

**SOC Recommendations:**
- Immediate patching to Rack 2.2.14+, 3.0.16+, 3.1.14+
- Real-time alerts for abnormal HTTP parameter counts
- Ruby worker memory monitoring
- Automated incident response activation

**Technical Skills Demonstrated:** Threat intelligence platforms (AlienVault OTX, VirusTotal, CISA KEV), attack attribution, IOC analysis, malware family research, MITRE ATT&CK mapping, risk quantification, business impact analysis, compliance assessment

**Tools Used:** AlienVault OTX, VirusTotal, CISA KEV Catalog, MITRE ATT&CK Navigator

---

### 📊 [SIEM Operations - SSH Brute Force Detection with Splunk]
**Analysis Period:** November 2025 | **Platform:** Splunk Enterprise

Built comprehensive Splunk monitoring solution to detect SSH brute-force attacks and scanning activity across enterprise infrastructure. Created dashboards, correlation rules, and automated alerting for continuous threat detection.

**Investigation Findings:**

**Malicious IP Activity:**
- **183.62.140.253** (Lianjiang, China, Uninet S.A. de C.V.)
  - Repeated failed login attempts and pre-auth disconnects
  - VirusTotal flagged as malicious
  - OTX shows 34 threat pulses (RDP, SSH, brute force tags)
  
- **187.141.143.180** (Mulege, Mexico, Uninet S.A. de C.V.)
  - Multiple authentication failures
  - Community reports of abusive behavior
  - Historical brute-force attack association

**Attack Patterns Identified:**
- Repeated pre-authentication disconnects ("Received disconnect from IP: 11: Bye Bye [preauth]")
- Multiple password attempts in short intervals targeting root and generic accounts
- Activity consistent with automated tools (Hydra, SSH scanners)
- High concentration from cloud-hosted international IPs
- Continuous automated probing matching fingerprinting behavior

**Splunk Implementation:**

**Dashboard Panels Created:**
- Top Source IPs by Failed Attempts
- Authentication Failures Over Time (trend analysis)
- Received Disconnect Events tracking
- Pre-authentication Activity Overview
- Raw Event Table for detailed investigation
- VirusTotal and OTX-Enriched Indicators

**Alert Configuration:**
- Search query: Pre-auth disconnect pattern detection
- Schedule: Daily execution at 8:00 AM
- Trigger threshold: >2 events in 24 hours
- Email notifications to approved domain
- 24-hour alert suppression to prevent duplicates

**Field Extraction:**
- Custom regex for src_ip field extraction
- Enables reliable IP referencing in dashboards and alerts
- Supports correlation across multiple log sources

**Incident Response Actions:**
- Blocked malicious IPs at network perimeter
- Reviewed historical logs for related connections
- Enhanced monitoring for similar activity patterns
- Increased visibility into SSH authentication events

**Recommendations Implemented:**
- Enforced SSH key-based authentication
- Disabled root password login
- Deployed fail2ban protection
- Ingested firewall and IDS logs into Splunk
- Created correlation searches for after-hours login attempts
- Implemented SSH MFA where possible
- Established credential rotation schedule

**Technical Skills Demonstrated:** SIEM operations, SPL (Splunk Processing Language) query development, dashboard creation, alert tuning, field extraction, threat enrichment (OTX, VirusTotal), log correlation, pattern recognition, automated response configuration

**Tools Used:** Splunk Enterprise, AlienVault OTX, VirusTotal

---

## 📜 Certifications & Training

**Girls in Security Operations (GiSOC) Bootcamp** - 2025
- Digital Forensics Investigation
- Incident Response & Threat Hunting
- Malware Analysis (Static & Dynamic)
- Vulnerability Management
- Threat Intelligence Research
- SIEM Operations & Log Analysis

  **Cybersecurity Diploma** -2024 - 2025

---

## 📫 Get In Touch

I'm always interested in collaborating on cybersecurity projects, discussing security research, or exploring new opportunities in SOC operations and threat intelligence.

📧 **Email:** chinasachinasa2014@gmail.com | chinasaali@yahoo.co.uk
💼 **LinkedIn:** https://www.linkedin.com/in/chinasa-ali-31a2a8a7  
🌍 **Location:** Lagos, Nigeria

---



**⭐ If you find my projects helpful, please consider giving them a star!**

*"Protecting digital assets through proactive threat detection and rapid incident response."*
