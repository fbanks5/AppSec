
# 🛡️ Application Security Engineering Demo – Juice Shop

Welcome to the AppSec Engineering showcase repository by **Frantz Banks**. This project demonstrates hands-on security analysis, testing, and remediation of OWASP Juice Shop using industry-standard tools and best practices.

---

## 📌 Project Overview

- **Target Application:** [OWASP Juice Shop](https://owasp.org/www-project-juice-shop/)
- **Environment:** Local Docker instance + GitHub integration
- **Objective:** Simulate a real-world Application Security Engineer workflow including SAST, DAST, SCA, secure coding, and SDLC.

---

## 🧪 Security Activities

| Tool           | Type   | Purpose                                          |
|----------------|--------|--------------------------------------------------|
| OWASP ZAP      | DAST   | Dynamic application security testing             |
| GitHub CodeQL  | SAST   | Static analysis via GitHub Actions               |
| Snyk CLI       | SCA    | Scan open-source dependencies for CVEs           |
| Manual Review  | Manual | SQL Injection example with “before/after” fix    |

---

## 📂 Reports & Artifacts

| File                          | Description                                      |
|-------------------------------|--------------------------------------------------|
| [`reports/zap_juice_report.html`](reports/zap_juice_report.html) | OWASP ZAP DAST scan of Juice Shop |
| [`reports/OWASP_ZAP_Findings.md`](reports/OWASP_ZAP_Findings.md) | ZAP findings summary |
| [`reports/Snyk_Findings.md`](reports/Snyk_Findings.md)           | Snyk vulnerability summary (SCA) |
| [`reports/SAST_Report.md`](reports/SAST_Report.md)               | CodeQL report with 3 top findings |
| [`reports/OWASP_SQLi_Demo.md`](reports/OWASP_SQLi_Demo.md)       | SQL Injection code example and patch |
| [`Risk_Assessment.md`](Risk_Assessment.md)                       | Summary of risks, CWE links, and mitigation |
| [`Secure_SDLC_Checklist.md`](Secure_SDLC_Checklist.md)           | Secure software development lifecycle checklist |

---

## ✅ Key Outcomes

- Identified over 45 vulnerabilities across dynamic, static, and dependency layers.
- Demonstrated remediation of an SQL injection flaw with secure parameterization.
- Built structured reporting artifacts for executive and technical audiences.
- Applied OWASP Top 10 and secure SDLC principles across the project.

---

## 🧠 Skills Demonstrated

- Secure coding practices
- Vulnerability triage and CWE mapping
- Tool integration: ZAP, Snyk, CodeQL, Docker
- Git-based reporting workflows
- Risk assessment and SDLC policy creation

---

## 🚀 How to Run Juice Shop Locally

```bash
docker pull bkimminich/juice-shop
docker run -d -p 3000:3000 bkimminich/juice-shop
```
Then visit: `http://localhost:3000`

---

## 🔒 Author

Frantz Banks – Application Security Engineer  
_WGU Student, Cloud & Blockchain Security Enthusiast_

