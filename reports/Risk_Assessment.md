
# 📋 Application Security Risk Assessment – OWASP Juice Shop

**Analyst:** Frantz Banks  
**Date:** May 14, 2025  
**Target:** OWASP Juice Shop  
**Assessment Tools:** OWASP ZAP (DAST), Snyk CLI (SCA), GitHub CodeQL (SAST), Manual Review

---

## 🧪 Summary of Findings

| Type  | Tool        | Vulnerability                               | Severity | CWE       | Status     |
|-------|-------------|---------------------------------------------|----------|-----------|------------|
| DAST  | OWASP ZAP   | Missing CSP Header                          | Medium   | CWE-693   | Open       |
| DAST  | OWASP ZAP   | Cross-Domain JS Inclusion                   | Medium   | CWE-829   | Open       |
| DAST  | OWASP ZAP   | Cross-Origin Misconfiguration (CORS)       | Medium   | CWE-942   | Open       |
| SCA   | Snyk        | ReDoS via ansi-regex                        | High     | CWE-400   | Open       |
| SCA   | Snyk        | Resource exhaustion via braces              | High     | CWE-400   | Open       |
| SCA   | Snyk        | Weak PBKDF2 in crypto-js                    | High     | CWE-916   | Open       |
| SAST  | CodeQL      | SQL Injection via Sequelize                 | High     | CWE-89    | Open       |
| SAST  | CodeQL      | Hardcoded Credentials                       | High     | CWE-798   | Open       |
| SAST  | CodeQL      | Missing SRI in external scripts             | Medium   | CWE-353   | Open       |
| Manual| Review      | SQL Injection demo (patched)                | High     | CWE-89    | ✅ Patched |

---

## 🔥 Risk Prioritization

| Severity | Count |
|----------|-------|
| Critical | 10 (Snyk) |
| High     | 6 (Snyk/SAST) |
| Medium   | 4 (DAST/SAST) |

**Business Risk Impact:**  
Unpatched vulnerabilities may lead to:
- Full account compromise via SQL injection
- Data leakage via misconfigured CORS or JS includes
- Credential exposure from hardcoded secrets
- DoS conditions from ReDoS or excessive parsing

---

## ✅ Recommendations

- **DAST Fixes:** Apply CSP headers, tighten CORS policy, limit JS origins
- **SAST Fixes:** Refactor vulnerable Sequelize queries and remove hardcoded secrets
- **SCA Fixes:** Upgrade vulnerable NPM packages using `npm audit fix` and/or `snyk wizard`
- **SDLC:** Adopt secure coding practices and integrate SAST/SCA/DAST into CI/CD
