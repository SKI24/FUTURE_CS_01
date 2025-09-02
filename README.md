# FUTURE_CS_01
# Web Application Security Assessment Report  

## Overview  
This project documents a comprehensive security assessment of the **OWASP Juice Shop** web application (an intentionally vulnerable app). The assessment was conducted as part of the **Future Interns Cybersecurity Internship (August 2025)** by **Nnonah Victor C.**  

The evaluation combined **automated testing with OWASP ZAP** and **manual verification**, focusing on vulnerabilities mapped to the **OWASP Top 10 (2021)** framework. The goal was to identify exploitable weaknesses, analyze their impact, and recommend remediation strategies.  

---

## Tools Used  
- **Kali Linux**  
- **OWASP Juice Shop** (Heroku deployment)  
- **OWASP ZAP**  

---

## Identified Vulnerabilities  
1. **Cross-Domain Misconfiguration**  
   - Risk: Medium  
   - Issue: Permissive CORS policy (`Access-Control-Allow-Origin: *`)  
   - Mitigation: Restrict origins, enforce secure CORS policy.  

2. **Content Security Policy (CSP) Header Not Set**  
   - Risk: Medium (High confidence)  
   - Issue: Absence of CSP exposes app to XSS, clickjacking, and injection.  
   - Mitigation: Implement strict CSP headers with monitoring.  

3. **Missing Anti-Clickjacking Header**  
   - Risk: Medium  
   - Issue: Lack of `X-Frame-Options` / `frame-ancestors` directive.  
   - Mitigation: Enforce anti-clickjacking headers.  

4. **Vulnerable JavaScript Library**  
   - Risk: Medium  
   - Issue: Outdated **jQuery 2.2.4** with known vulnerabilities.  
   - Mitigation: Upgrade dependencies and remove unused libraries.  

5. **Session ID in URL Rewrite**  
   - Risk: Medium (High confidence)  
   - Issue: Session IDs exposed in URLs, enabling session hijacking.  
   - Mitigation: Use secure cookies, short timeouts, and unpredictable IDs.  

---

## OWASP Top 10 Mapping  
| Vulnerability                   | OWASP Top 10 (2021) Category                | Risk   |  
|---------------------------------|---------------------------------------------|--------|  
| Cross-Domain Misconfiguration   | A05: Security Misconfiguration              | Medium |  
| CSP Header Not Set              | A05: Security Misconfiguration              | Medium |  
| Missing Anti-Clickjacking Header| A05: Security Misconfiguration              | Medium |  
| Vulnerable JS Library           | A06: Vulnerable & Outdated Components       | Medium |  
| Session ID in URL Rewrite       | A07: Identification & Authentication Failures | Medium |  

---

## Conclusion  
The assessment revealed multiple **medium-risk vulnerabilities** primarily related to **security misconfigurations, outdated components, and weak session handling**. If left unresolved, these could lead to **unauthorized access, data compromise, and account hijacking**.  

Implementing the recommended **mitigation strategies** will significantly strengthen the application’s security posture and resilience against real-world attacks.  
