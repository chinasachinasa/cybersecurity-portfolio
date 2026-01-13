# SOC Operations - SSH Log Analysis Using Splunk

## Project Overview
Comprehensive security analysis of SSH authentication logs using Splunk Enterprise to detect brute-force attacks, suspicious IP activity, and automated scanning attempts. This investigation identified active threat actors targeting SSH endpoints and provided actionable security recommendations.

## Investigation Details
- **Analysis Date:** November 14th, 2025
- **Tool Used:** Splunk Enterprise
- **Log Source:** SSH authentication events
- **Focus:** Failed login detection, pre-authentication analysis, threat intelligence correlation

## Key Findings

### Critical Security Incidents Identified

**1. Malicious IP Activity:**
- **183.62.140.253** (Lianjiang, China) - Repeated failed logins, flagged by VirusTotal and OTX
- **187.141.143.180** (Mulege, Mexico) - Multiple authentication failures, community-reported abuse
- Both IPs confirmed via OTX threat intelligence as active brute-force attackers with 34 associated threat pulses

**2. Attack Patterns Detected:**
- Multiple failed SSH login attempts from external IPs
- Repeated pre-authentication disconnect messages indicating automated scanning
- High concentration of attempts from cloud-hosted international IP addresses
- Activity consistent with automated tools (Hydra, SSH scanners)

**3. Targeted Accounts:**
- Root account repeatedly targeted
- Generic account names probed
- Evidence of account enumeration attempts

## Analysis Methodology

### Splunk Investigation Techniques
1. **Log Indexing & Parsing**
   - Indexed SSH logs in Splunk main index
   - Parsed timestamps for time-based analysis
   - Categorized events: successful, failed, pre-auth attempts

2. **Pattern Recognition**
   - Identified multiple password attempts in short intervals
   - Tracked pre-authentication disconnect patterns
   - Correlated authentication trends over time

3. **Threat Intelligence Enrichment**
   - VirusTotal lookups for IP reputation
   - OTX (Open Threat Exchange) investigation
   - Historical threat data correlation

4. **Field Extraction**
   - Created custom field: `src_ip`
   - Implemented regex extraction for reliable IP referencing
   - Enabled dashboard and alert integration

## Dashboards Created

Built comprehensive monitoring dashboards including:
- **Top Source IPs by Failed Attempts** - Identifies most aggressive attackers
- **Authentication Failures Over Time** - Trend analysis of attack patterns
- **Received Disconnect Events** - Pre-auth scanning detection
- **Pre-auth Activity Overview** - Early-stage attack identification
- **Raw Event Table** - Detailed log review capability
- **VirusTotal and OTX-Enriched Indicators** - Threat intelligence integration

## Alert Configuration

**Alert Details:**
- **Search Query:** `"Received disconnect from 112.95.230.3: 11: Bye Bye [preauth]"`
- **Schedule:** Daily at 8:00 AM
- **Trigger Threshold:** More than 2 events in 24 hours
- **Response:** Email notifications to SOC team
- **Suppression:** 24-hour window to avoid alert fatigue

## Incident Response Summary

### Observations
- High volume of failed SSH logins from external IPs
- Repeated pre-authentication disconnect messages
- Automated probing consistent with brute-force tools
- Multiple IPs flagged as malicious by threat intelligence sources

### Attack Types Identified
- SSH password guessing attacks
- SSH service fingerprinting
- Valid account enumeration
- **Status:** No successful compromise detected - host actively targeted but defended

## Recommendations Provided

### Immediate Actions
- Block identified malicious IPs (183.62.140.253, 187.141.143.180) at firewall
- Enforce SSH key-based authentication
- Disable root password login
- Deploy fail2ban or equivalent brute-force protection

### Near-Term Improvements
- Ingest firewall and IDS logs into Splunk
- Create correlation searches for:
  - Repeated failed logins
  - Pre-authentication disconnects
  - Logins outside business hours

### Long-Term Security Enhancements
- Implement SSH Multi-Factor Authentication (MFA)
- Rotate credentials and audit privileged accounts
- Conduct regular vulnerability scans and patch reviews
- Continue threat intelligence enrichment

## Skills Demonstrated
- SIEM platform operations (Splunk)
- Log analysis and correlation
- Threat detection and pattern recognition
- Threat intelligence integration (VirusTotal, OTX)
- Security dashboard creation
- Alert configuration and tuning
- Incident investigation and reporting
- Security recommendations and remediation planning

## Tools & Technologies Used
- **SIEM:** Splunk Enterprise
- **Threat Intelligence:** OTX (Open Threat Exchange), VirusTotal
- **Analysis Techniques:** Regex field extraction, SPL queries, time-series analysis
- **Reporting:** Dashboard visualization, automated alerting

## Deliverables
- Comprehensive SOC analysis report (./ALI_CHINASA_LOGANALYSIS_FINAL_PROJECT.pdf)
- Custom Splunk dashboards for continuous monitoring
- Configured alerts for automated threat detection
- Field extraction rules for improved analysis
- Actionable security recommendations

## Conclusion
This Splunk-based investigation successfully identified continuous external scanning and brute-force attempts targeting SSH services. Threat intelligence validation confirmed active threat actors, and implemented monitoring solutions now provide ongoing visibility and early warning capabilities for similar security events.

---

**Submission Details:**
- **Analyst:** ALI CHINASA JULIET
- **Date:** November 14th, 2025
- **Program:** Girls in Security Operations (GiSOC) Bootcamp - Module 3 (Log & Packet Analysis)
- **Case Reference:** SOC_11_25
