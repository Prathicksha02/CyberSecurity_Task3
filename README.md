# Vulnerability Assessment - Linux System (Task 3)

## Task Overview

**Task 3:** Perform a Basic Vulnerability Scan on your PC  
**Objective:** Identify common vulnerabilities using free tools  
**Tool Used:** Nessus Essentials  
**Scan Targets:**  
- Linux Machine: 192.168.164.59  
- Linux Machine: 192.168.164.249  
**Date of Scan:** 26 June 2025  

---

## Scan Summary

| Target IP         | Critical | High | Medium | Low | Info | Total |
|-------------------|----------|------|--------|-----|------|-------|
| 192.168.164.59    | 0        | 0    | 1      | 2   | 13   | 16    |
| 192.168.164.249   | 0        | 0    | 2      | 0   | 34   | 36    |

---

## Key Vulnerabilities Identified

## **For 192.168.164.59**

#### 1. DNS Server Cache Snooping Remote Information Disclosure  
- **Severity:** Medium  
- **Description:** Allows remote attackers to determine if a domain has been recently resolved by the DNS server.  
- **Suggested Fix:** Restrict access to the DNS server; configure DNS to avoid cache snooping.

#### 2. DHCP Server Detection  
- **Severity:** Low  
- **Description:** DHCP service detected; may reveal network information.  
- **Suggested Fix:** Disable DHCP service if unnecessary, or restrict access.

#### 3. ICMP Timestamp Request Remote Date Disclosure  
- **Severity:** Low  
- **Description:** System responds to ICMP timestamp requests, revealing system uptime.  
- **Suggested Fix:**  
    sudo sysctl -w net.ipv4.icmp_echo_ignore_all=1
  
---

### **For 192.168.164.249**

#### 1. SSL Certificate Cannot Be Trusted  
- **Severity:** Medium  
- **Description:** SSL certificate is not trusted by major browsers or systems.  
- **Suggested Fix:** Install a valid certificate from a trusted Certificate Authority.

#### 2. SMB Signing Not Required  
- **Severity:** Medium  
- **Description:** SMB service does not enforce signing, increasing risk of MitM attacks.  
- **Suggested Fix:**  
  Edit `/etc/samba/smb.conf` and enforce signing:  
    server signing = mandatory
    
  Restart Samba service:  
    sudo systemctl restart smbd

---


## Steps I Followed

1. Installed **Nessus Essentials** on my Windows machine from [Tenable's Official Site](https://www.tenable.com/products/nessus/nessus-essentials).
2. Registered for a free activation code and completed Nessus setup.
3. Found the IP addresses of my Linux machines using:
   ip a
4. Created a Basic Network Scan in Nessus, targeting both Linux machine IPs.
5. Started the scan and waited for it to complete (25 minutes).
6. Reviewed the scan results for vulnerabilities and severity.
7. Identified key vulnerabilities:
    --DNS Cache Snooping
    --ICMP Timestamp response enabled
    --Untrusted SSL Certificate
    --SMB Signing not required
8. Saved the full scan report as a PDF from the Nessus web interface.
     Report pdf is included here: Vulnerability-Assessment-Task3.pdf
9. Took relevant screenshots of the scan summary and vulnerabilities.
     Screenshots pdf is included here: Screenshots_task3.pdf


## Outcomes

1. Gained hands-on experience with Nessus vulnerability scanner
2. Identified real security risks in Linux systems
3. Practiced applying basic system hardening techniques
4. Understood vulnerability severity levels and CVSS basics


