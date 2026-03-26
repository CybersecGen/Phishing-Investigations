# Phishing Incident Investigation (Email Analysis & IOC Extraction)

**Organization:** Global Payments Provider  
**Project Type:** SOC Investigation / Threat Analysis  

---

## Project Overview

This project evaluates phishing risk and strengthens organisational detection and response capabilities within a global payments environment.  
Focus: **real-world phishing techniques, IOC extraction, and SOC visibility**.

---

## Challenge

Phishing attacks bypassed technical controls and relied on social engineering:

- Limited user identification of malicious emails  
- Low reporting rates to the SOC  
- Ongoing risk of credential harvesting  

---

## SOC Investigation

### Email Characteristics

- **Sender Address:** spoofed domain resembling legitimate provider  
- **Subject:** urgency-driven (e.g., "Account Verification Required")  
- **Attachment/Link:** embedded malicious URL  

### Header Analysis

- SPF/DKIM/DMARC checks: **failed or misaligned**  
- Originating IP: **not associated with legitimate domain**  
- Reply-to mismatch observed  

### URL & Payload Analysis

- Link redirected to lookalike login page  
- Domain contained slight misspelling (typosquatting)  
- HTTPS used to appear legitimate  

### Tools Used

- **VirusTotal** – check URLs, domains, and file hashes  
- **MXToolbox** – verify SPF/DKIM/DMARC and email headers  
- **URLVoid / PhishTool** – check URL reputation  
- **WHOIS Lookup** – verify domain registration  

---

### Indicators of Compromise (IOCs)

- Malicious domain  
- Sender email address  
- Source IP address  
- URL path patterns  

### Investigation Workflow

1. User reported suspicious email  
2. Email analysed for headers and links  
3. IOCs extracted and validated with free tools  
4. Checked SIEM for:
   - Other recipients  
   - Similar emails  
5. Assessed user interaction (clicks/submissions)

---

## SOC Detection Gaps Identified

- No alerting on suspicious domains  
- Lack of email header validation monitoring  
- Limited visibility into user click activity  

---

## Detection & Response Improvements

- Block identified malicious domains/IPs  
- Implement email filtering rules  
- Add alerting for:
  - Domain spoofing  
  - Lookalike domains  
- Integrate reporting into SIEM (e.g., Microsoft Sentinel)  

---

## Example Attack Flow

 ```text
 User receives phishing email → clicks link
 ↓
 Redirected to fake login page
 ↓
 Credentials submitted
 ↓
 SOC validates with VirusTotal / MXToolbox
 ↓
 SOC blocks domain across environment
 ```

---

## Key Takeaway

Strengthening email analysis and IOC extraction enhances SOC detection capabilities
Clear investigation steps transform user reports into actionable intelligence
Integrating findings into SIEM enables proactive threat detection and faster response.
