# 🔎PENETRATING TEST REPORT
![Focus](https://img.shields.io/badge/Focus-Cybersecurity-blue)![Tool](https://img.shields.io/badge/Tool-Zenmap-red)![Platform](https://img.shields.io/badge/Platform-Kali%20Linux-blue)![Status](https://img.shields.io/badge/Status-Completed-green)
## ZENMAP | NETWORK RECONNAISSANCE
# 1. Field Detail
## ⭐OVERVIEW 
| Field | Details|
|----|----|
| Author | Kopila Adhikari|
| Batch | B083-Networkwalks |
| Date | 16 September 2026 |
| Authorization | permission secured |
| Assessment Type | Network Reconnaissance & Zenmap
| Module | PM-2 & PM-5 |

# 2.🛠Tools Used 
| Tools | Purpose|
|-----|------|
| Whois | Domain Registeration details |
| WhatWeb | Web technology fingerprinting(CMS,plugins,server) |
| Curl-I | HTTP rsponse headers inspection |
| Wafw00f | Web Application Firewall detection|
| dnsrecon | DNS record enumeration (NS,MX.TXT,SRV)
| Zenmap(Nmap GUI) | local network host discovery & topology |

#🔐3. Key Findings
##🐾 Footprinting
<code>(networkwalks.com)</code>
|Finding | Value |
|----|----|
|Register| GoDAddy.com|
|Hosting Provider| Hostgater |
|CMS | WordPress 7.1 |
|plugin | WordPress Download Manager 3.3.58|
|Web Server | Apache |
|CMS | Modsecurity(Spiderlabs)|
|DNS Server | BIND 9.16.23-RH |
|DNS Records Fund | 8(SOA,NS,MX,A,TXT,SRV) |

# 📷4.Evidence Gallery 
## ⭐ whois networkwalks.com
```bash
whois networkwalks.com
```
*Registrar: GoDaddy.com | Name Servers:
NS6135.HOSTGATOR.COM
 NS6136.HOSTGATOR.COM*
<img width="874" height="822" alt="p1" src="https://github.com/user-attachments/assets/6b076d8e-d26b-42dc-8a31-13cebda87a69" />


 ## ⭐ Whatweb networkwalks.com
```bash
Whatweb networkwalks.com
```
*CMS: WordPress 7.1 | plugin:WordPress Download Manager 3.3.58*
<img width="1114" height="577" alt="t2" src="https://github.com/user-attachments/assets/38b4323f-9f83-4eb1-a00f-d79a1b41a280" />


## ⭐ nslookup networkwalks.com
```bash
nslookup networkwalks.com
```
*server:8.8.8.8 | Address: 8.8.8.8#53*
 <img width="1107" height="577" alt="T3" src="https://github.com/user-attachments/assets/01fe0f7d-3ee3-4282-a51f-0e59d05b912d" />


 ## ⭐ curl  -I https://networkwalks.com
 ```bash
 curl  -I https://networkwalks.com
```
*server: Apache | Status code : 200 | cookies*
  <img width="1920" height="1080" alt="t4" src="https://github.com/user-attachments/assets/2deb237d-8490-413d-a30f-5cd28ea1da24" />


 ## ⭐ wafw00f networkwalks.com
  ```bash
 wafw00f networkwalks.com
```
 
*CMS : Modsecurity(Spiderlabs)*
<img width="1920" height="1080" alt="T5" src="https://github.com/user-attachments/assets/4bf4723c-bc56-432f-9766-40adae9974b8" />


## ⭐ dnsrecon -d networkwalks.com
 ```bash
  dnsrecon -d networkwalks.com
```
*SOA,NS,MX,A,TXT,SRV*
<img width="1920" height="1080" alt="t6" src="https://github.com/user-attachments/assets/a36d0e99-ddc2-4912-8b3a-2f1f7973f5aa" />

# 5. Network Scanning with Zenmap

For the second activity, I used **Zenmap** to perform network discovery on my local network. The practical required me to identify my local IP address and subnet, discover live hosts, identify their IP and MAC addresses, and generate a network topology.

I first used the Windows `ipconfig` command to identify my local IP address and LAN subnet. I then entered the subnet into Zenmap and selected **Ping Scan** to identify active hosts.

The example results provided in the practical identified four live hosts:

- `10.0.0.1`
- `10.0.0.2`

The example results also included four MAC addresses.

After completing the scan, I opened the **Topology** section in Zenmap, enabled the legend and saved the network topology in PDF format as required by the practical task.
<img width="1120" height="846" alt="5 3" src="https://github.com/user-attachments/assets/64fbc9ab-2a71-4ba2-a75b-731caac0f61e" />

**Note:** The actual subnet, number of hosts and addresses should be replaced with the results from my own network when submitting the report.


# 6. Risk Analysis / Impact

Based on the information collected during the footprinting and network scanning activities, I identified the following potential risks.

| **\#** | **Risk / Finding**                           | **Evidence / Observation**                                  | **Potential Impact**                                                                                            | **Risk Level** |
|--------|----------------------------------------------|-------------------------------------------------------------|-----------------------------------------------------------------------------------------------------------------|----------------|
| 1      | Web technology information exposed           | WhatWeb identified WordPress and WP Download Manager        | Attackers may use exposed technology/version information to identify software requiring further security review | **● Medium**   |
| 2      | Server IP address identifiable               | Nslookup resolved the domain to `192.232.216.135`           | Provides information about the network location of the web service                                              | **● Low**      |
| 3      | HTTP technical information exposed           | Curl returned HTTP response headers and exposed `/wp-json/` | May assist technology fingerprinting and further enumeration                                                    | **● Low**      |
| 4      | WAF technology identifiable                  | Wafw00f identified ModSecurity (SpiderLabs)                 | Reveals information about the web application’s security architecture                                           | **● Low**      |
| 5      | DNS infrastructure information exposed       | DNSRecon identified DNS, mail and service-related records   | DNS information can help build a broader infrastructure profile                                                 | **● Medium**   |
| 6      | Multiple live hosts visible on local network | Zenmap identified four live hosts in the example network    | Unknown or unauthorized devices may potentially be present on a network                                         | **● Medium**   |

**Risk level key:** ● Critical ● Medium ● Low

The risks above are observations from the footprinting and scanning exercises, not confirmed vulnerabilities.

The practical exercises primarily involved information gathering and host discovery. No exploitation or vulnerability validation was performed as part of these two modules.

Therefore, the presence of information such as a software version, IP address or DNS record does not by itself mean that the system is vulnerable. Further authorized security testing would be required to confirm any actual vulnerability.

# 7. Recommendations

Based on the observations from these activities, I recommend the following security improvements:

1.  **Review publicly exposed technology information**  
    Organizations should regularly review what information about their web technologies, CMS and plugins is publicly visible.

2.  **Keep software updated**  
    CMS platforms, plugins and other web technologies should be regularly updated and reviewed against current security advisories.

3.  **Review HTTP headers**  
    HTTP response headers should be reviewed to determine whether unnecessary technical information is being exposed.

4.  **Review DNS records regularly**  
    DNS records should be checked periodically to ensure that only required information and services are publicly exposed.

5.  **Properly configure and monitor the WAF**  
    Keep the WAF (ModSecurity) enabled and tuned, since it already blocks naive attacks.

6.  **Perform regular internal network discovery**  
    Organizations should periodically scan their own networks to identify active devices.

7.  **Investigate unknown devices**  
    Any unexpected device discovered during network scanning should be investigated and verified.

8.  **Maintain network documentation**  
    Network topology and device information should be documented and updated regularly.

9.  **Perform security testing with authorization**  
    Reconnaissance and scanning should only be performed against systems and networks where appropriate authorization has been provided.

    # 8. Conclusion

During Week 2 of my Cybersecurity & Ethical Hacking internship, I completed practical activities covering footprinting, reconnaissance and network scanning.

In the footprinting activity, I used six Kali Linux tools to collect information about the target domain. I learned how WHOIS can provide domain information, WhatWeb can identify web technologies, Nslookup can resolve domain names, Curl can inspect HTTP headers, Wafw00f can identify a WAF, and DNSRecon can provide additional DNS information.

In the network scanning activity, I used Zenmap to identify my local network configuration and discover active hosts. I also collected IP and MAC address information and created a network topology.

The exercises showed me that information gathering is an important part of cybersecurity. Even before attempting to exploit a system, a security professional can learn a significant amount about an environment by carefully analyzing publicly available information and network responses.

I also learned that technical findings should be documented clearly. A good cybersecurity report should explain what was performed, what was discovered, what the observation means, what risk it may create, and what can be done to reduce that risk.

Finally, I learned that reconnaissance and scanning must always be performed within an authorized scope. These activities were completed as part of the assigned educational cybersecurity lab.

# 👤 Author
**Kopila Adhikari**

Cybersecurity Starter

Cybersecurity Professional B083

LinkedIn:https://lnkd.in/p/g7sw8JZK


# 📌Project Imformation

**Program Name:** Cybersecurity at Networkwalks | **Week: 02 | Project:** Cybersecurity & PENETRATION TESTING REPORT | 
**Repository:** GitHub










 



