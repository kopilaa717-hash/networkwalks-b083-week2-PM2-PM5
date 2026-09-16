# 🔎PENETRATING TEST REPORT
![Focus](https://img.shields.io/badge/Focus-Cybersecurity-blue)![Tool](https://img.shields.io/badge/Tool-Zenmap-red)![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue)![Status](https://img.shields.io/badge/Status-Completed-green)
## ZENMAP | NETWORK RECONNAISSANCE
## Field Detail
## ⭐OVERVIEW 
| Field | Details|
|----|----|
| Author | Kopila Adhikari|
| Batch | B083-Networkwalks |
| Date | 16 September 2026 |
| Authorization | permission secured |
| Assessment Type | Network Reconnaissance & Zenmap
| Module | PM-2 & PM-5 |

## 🛠Tools Used 
| Tools | Purpose|
|-----|------|
| Whois | Domain Registeration details |
| WhatWeb | Web technology fingerprinting(CMS,plugins,server) |
| Curl-I | HTTP rsponse headers inspection |
| Wafw00f | Web Application Firewall detection|
| dnsrecon | DNS record enumeration (NS,MX.TXT,SRV)
| Zenmap(Nmap GUI) | local network host discovery & topology |
#🔐 Key Findings
## Footprinting
<code>(networkwalks.com)</code>
|Finding | Value |
|----|----|
|Register| GoDAddy.com|
|Hosting Provider| Hostgater |
|CMS | WordPress 7.1 |
|plugin | WordPress Download Manager 3.3.58|
|Web Server | Apache |
|WAF | ModSecurity (SpiderLabs) |
|DNS Server | BIND 9.16.23-RH |
|DNS Records Fund | 8(SOA,NS,MX,A,TXT,SRV) |
# Evidence Gallery 
## 1. whois networkwalks.com
```bash
whois networkwalks.com
```







