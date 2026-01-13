# Digital Forensics Investigation - Task 1 (DIF-2025)

## Project Overview
Forensic analysis of a Windows disk image as part of the GiSOC Bootcamp DFIR module. The investigation examined Karen's system activity during a job assessment process with TAAUSAI company, uncovering potential security concerns and suspicious communications.

## Case Background
Karen, a security professional, received a job offer from TAAUSAI and was asked to complete technical assessment tasks. A forensic review was conducted on the provided disk image to evaluate her activities and validate the work performed.

## Investigation Objectives
- Identify system configuration and user information
- Analyze communication patterns and external contacts
- Examine document access and download activities
- Establish timeline of events
- Assess potential security risks

## Key Findings

### System Analysis
- **Administrator Username:** Karen
- **OS Build:** 16299
- **Hostname:** TOTALLYNOTAHACK (⚠️ Suspicious naming convention)
- **Timezone:** UTC
- **Chrome Version:** 72.0.3626.121

### Communication Analysis
- **Messaging Application:** Skype
- **External Contact:** Michael Scotch (TAAUSAI)
- **Financial Offer:** $150,000 upfront payment
- **Meeting Location:** Egypt (identified via coordinates in email)

### Evidence of Suspicious Activity
- Intentionally deceptive system hostname
- External communications with monetary incentives
- Downloaded communication software for external contact
- International meeting arrangements

## Tools & Techniques Used

### Forensic Tools
- **FTK Imager** - Disk image acquisition and file system analysis
- **Registry Explorer** - Windows Registry forensics and artifact extraction
- **Kernel OST Viewer** - Email analysis and extraction
- **DB Browser for SQLite** - Browser history and application data analysis

### Analysis Methods
- System registry examination (SAM, SYSTEM hives)
- User profile analysis
- Browser history reconstruction
- Email communication review
- Document metadata analysis
- Timeline correlation

## Investigation Questions Answered

The investigation successfully answered 17 forensic questions covering:
1. System configuration (username, OS build, hostname, timezone)
2. Application usage (messaging software, browser version)
3. Communication analysis (external contacts, financial offers)
4. Document activity (file access times, source websites)
5. Security indicators (password changes, partition layout)

## Skills Demonstrated
- Digital forensics investigation methodology
- Windows system forensics
- Registry analysis
- Email forensics
- Browser forensics
- Artifact correlation and timeline reconstruction
- Evidence documentation
- Threat assessment

## Deliverables
- Comprehensive forensic investigation report /ALI_CHINASA_DIF_TASK1.pdf
- 17 answered investigative questions with supporting evidence
- Screenshots documenting each finding
- Security risk assessment

## Key Takeaways
This investigation demonstrated the importance of thorough digital forensics in identifying potential insider threats. The combination of suspicious system naming, external financial incentives, and compartmentalized communications raised significant red flags requiring further investigation.

---

**Submission Details:**
- **Analyst:** ALI CHINASA JULIET
- **Date:** December 6th, 2025
- **Program:** Girls in Security Operations (GiSOC) Bootcamp - Module 5 (DFIR)
- **Case Reference:** DIF-2025 Task 1
