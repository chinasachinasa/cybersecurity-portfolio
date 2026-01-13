# Incident Response - Suspicious SSH Connection Investigation

## Project Overview
Real-time incident response investigation of suspicious SSH connection attempts targeting AWS EC2 infrastructure. Using Elastic Security SIEM, this investigation identified, analyzed, and contained a potential SSH brute-force attack targeting cloud infrastructure, demonstrating end-to-end incident handling from detection through remediation.

## Incident Details
- **Date:** September 28, 2025
- **Detection Time:** 04:18:34 UTC
- **Severity:** High
- **Risk Score:** 88
- **Status:** Successfully Contained & Remediated
- **SIEM Platform:** Elastic Security

## Executive Summary

On September 28, 2025, Elastic Security detected multiple suspicious SSH connection attempts targeting an AWS EC2 instance in the us-east-1 region. The automated "SSH ATTEMPT DETECTION RULE" triggered a high-severity alert (risk score 88), prompting immediate incident response actions.

**Key Findings:**
- Multiple SSH connection attempts from external IP 18.206.107.29
- Broader scanning campaign targeting multiple AWS instances
- Attack pattern consistent with SSH brute-force reconnaissance
- **Outcome:** No successful compromise - attack prevented by key-based authentication
- **Response:** Host isolated, threat contained, security posture enhanced

## Affected Assets

### EC2 Instance Profile
- **Instance ID:** i-06630d676df556c70
- **Public IP:** 54.196.228.242
- **Internal IP:** 172.31.22.57
- **User Account:** ec2-user@172.31.22.57
- **AWS Region:** us-east-1
- **Asset Classification:** Production cloud infrastructure

## Incident Timeline

| Time (UTC) | Event | Action Taken |
|------------|-------|--------------|
| **04:18:34** | Initial SSH connection attempt detected from 18.206.107.29 to 172.31.22.57 | SIEM alert generated |
| **04:20:04** | Alert escalated in Elastic Security with risk score 88 | Automatic threat intelligence enrichment |
| **06:27:00** | Security team notified and investigation initiated | SOC analyst assigned to incident |
| **06:35:00** | Decision made to isolate host for containment | Incident response team engaged |
| **06:40:00** | Host successfully isolated using Elastic Defend | Network segmentation applied |

**Total Response Time:** 2 hours 22 minutes from detection to containment

## Attack Analysis

### Attack Vector & Methodology

**Primary Attacker IP:** 18.206.107.29

**Attack Pattern Characteristics:**
- Multiple SSH connection attempts targeting port 22
- Systematic scanning of internal AWS IP space (172.31.x.x subnet)
- Related attempts from additional IPs: 18.206.107.27, 102.89.68.233
- Source IPs originating from AWS infrastructure (potential compromised EC2 pivot point)

**Attack Classification:**
- **MITRE ATT&CK T1021.004** - Remote Services: SSH
- **MITRE ATT&CK T1110** - Brute Force
- **MITRE ATT&CK T1190** - Exploit Public-Facing Application

**Attacker Tactics:**
1. **Reconnaissance:** Scanning AWS IP ranges for SSH services
2. **Initial Access Attempt:** Connection attempts to discovered SSH services
3. **Lateral Movement Preparation:** Targeting multiple instances suggesting broader campaign

### Threat Intelligence Context

**Source IP Analysis:**
- IPs traced to AWS infrastructure (us-east-1 region)
- Suggests compromised EC2 instance being used as attack pivot
- Pattern matches known SSH scanning campaigns in cloud environments
- Multiple related IPs indicate coordinated scanning operation

## Investigation Methodology

### 1. Initial Triage

**Verification Steps:**
- Confirmed EC2 instance should NOT accept external SSH connections
- Validated source IP (18.206.107.29) not on organizational allow list
- Reviewed AWS CloudTrail logs for related suspicious activity
- Assessed current security group configurations

**Initial Assessment:**
- High severity due to unauthorized access attempts
- Potential for lateral movement if successful
- Multiple assets potentially targeted

### 2. Host Isolation & Containment

**Containment Actions:**
- **Isolated affected EC2 instance** using Elastic Defend endpoint protection
- Prevented potential lateral movement while maintaining monitoring capabilities
- Blocked outbound connections from compromised subnet
- Maintained forensic evidence collection during isolation

**Rationale:**
- Prevent potential spread if instance was compromised
- Preserve system state for forensic analysis
- Maintain visibility into attacker actions

### 3. Log Analysis & Forensics

**Data Sources Analyzed:**
- SSH authentication logs on target instance
- AWS VPC Flow Logs for network connection patterns
- Elastic Security timeline for attack visualization
- AWS CloudTrail for API activity correlation

**Analysis Findings:**
- Created comprehensive timeline in Elastic Security
- Identified full scope of connection attempts across infrastructure
- Mapped attack progression and related IP addresses
- Confirmed no successful authentication events

### 4. Scope Assessment

**Infrastructure-Wide Review:**
- Analyzed connection attempts to multiple AWS instances
- Identified broader scanning campaign targeting internal subnet
- Confirmed attack pattern consistency across multiple targets
- Assessed potential blast radius of incident

## Key Investigation Findings

### Positive Security Outcomes

✅ **No Successful Compromise Detected**
- SSH connection attempts unsuccessful due to key-based authentication
- No successful login events in authentication logs
- No evidence of command execution or data exfiltration
- Instance integrity verified - no indicators of compromise

✅ **Effective Security Controls**
- Key-based authentication prevented password brute-force
- SIEM detection rules triggered appropriately
- Rapid response limited exposure window
- Network segmentation contained potential impact

### Attack Campaign Characteristics

**Pattern Analysis:**
- Part of broader SSH scanning campaign targeting AWS infrastructure
- Systematic subnet scanning methodology
- Multiple source IPs suggesting coordinated operation
- Matches known SSH reconnaissance patterns in cloud environments

**Attacker Infrastructure:**
- Using AWS infrastructure as attack platform (likely compromised instances)
- Rotating through multiple source IPs to evade detection
- Targeting default SSH port (22) with automated tools

## Response Actions Taken

### Immediate Containment (Within 1 Hour)

**Network Isolation:**
- Isolated affected EC2 instance using Elastic Defend
- Added suspicious IPs (18.206.107.29, 18.206.107.27, 102.89.68.233) to AWS Security Group deny rules
- Restricted SSH access to VPN IP ranges only

**Team Notification:**
- Notified cloud infrastructure team of suspicious activity
- Escalated to incident response team for coordinated response
- Briefed management on incident status and risk level

### Remediation Actions (Within 24 Hours)

**Security Hardening:**
- ✅ Verified SSH configuration - password authentication remains disabled
- ✅ Rotated SSH keys as precautionary measure
- ✅ Updated Security Group rules to restrict SSH access exclusively to VPN IP ranges
- ✅ Enhanced logging for all SSH connection attempts
- ✅ Implemented fail2ban equivalent for automated blocking

**Configuration Changes:**
- Removed public internet SSH access from security groups
- Implemented bastion host architecture for administrative access
- Moved SSH to non-standard port on selected instances
- Enabled AWS Session Manager as alternative access method

### Enhanced Monitoring (Ongoing)

**Detection Improvements:**
- Created custom watch list for identified suspicious IP addresses
- Set up additional alerts for ANY SSH activity from external sources
- Implemented alert correlation to detect related scanning attempts
- Configured automatic blocking for IPs making multiple failed attempts

**Scheduled Reviews:**
- 24-hour follow-up review to confirm no further suspicious activity
- 48-hour monitoring period before releasing host from isolation
- Security review of all EC2 instances for proper SSH configurations

## MITRE ATT&CK Framework Mapping

| Tactic | Technique ID | Technique Name | Evidence |
|--------|--------------|----------------|----------|
| **Initial Access** | T1190 | Exploit Public-Facing Application | SSH service exposed to internet |
| **Initial Access** | T1078 | Valid Accounts | Attempted SSH authentication |
| **Credential Access** | T1110 | Brute Force | Multiple connection attempts |
| **Lateral Movement** | T1021.004 | Remote Services: SSH | SSH connection to internal IP |
| **Discovery** | T1046 | Network Service Discovery | Systematic scanning of subnet |

## Lessons Learned

### What Went Well ✅

1. **Effective Detection** - SIEM rules triggered appropriately with high fidelity
2. **Rapid Response** - Containment achieved within 2.5 hours of detection
3. **Preventive Controls** - Key-based authentication prevented compromise
4. **Team Coordination** - Smooth escalation and communication across teams

### Areas for Improvement 🔧

1. **Alert Response Time** - 2-hour gap between detection and team notification
2. **Baseline Monitoring** - Need better visibility into normal SSH patterns
3. **Automated Response** - Manual containment delayed - consider SOAR integration
4. **External SSH Access** - Instances should never expose SSH to internet by default

## Recommendations

### Immediate Security Improvements

**Architecture Changes:**
- ✅ Implement bastion host/jump server architecture for SSH access
- ✅ Deploy AWS Session Manager as primary administrative access method
- ✅ Move SSH to non-standard ports to reduce automated scanning
- ✅ Implement just-in-time (JIT) access for SSH connections

**Access Control:**
- Enforce VPN-only access for all administrative services
- Implement multi-factor authentication (MFA) for SSH where possible
- Regular access review and key rotation schedule
- Principle of least privilege for SSH access

### Process Improvements

**Detection & Response:**
- Enhance alert correlation to identify related scanning attempts faster
- Implement automated temporary blocking for repeated failed attempts
- Reduce notification delay through improved alerting workflows
- Consider SOAR platform for automated containment actions

**Monitoring & Visibility:**
- Baseline normal SSH patterns for anomaly detection
- Implement geolocation-based alerts for SSH from unexpected regions
- Enhanced logging retention for forensic investigations
- Regular threat hunting exercises focused on access anomalies

### Long-Term Strategic Initiatives

**Cloud Security Posture:**
- Implement cloud security posture management (CSPM) tooling
- Regular security configuration reviews for all cloud assets
- Automated compliance checking for security group rules
- Infrastructure-as-code security scanning

**Security Awareness:**
- Update training to include this incident as case study
- Conduct tabletop exercises simulating SSH compromise scenarios
- Share lessons learned across engineering a
