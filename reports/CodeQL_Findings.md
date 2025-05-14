
# 🔐 SAST Report: OWASP Juice Shop

**Repository:** [fbanks5/juice-shop](https://github.com/fbanks5/juice-shop)  
**Scan Tool:** GitHub Code Scanning (CodeQL)  
**Date:** May 14, 2025

---

## 🧪 Top 3 Findings

### 1. 🧨 SQL Injection via Sequelize (CWE-89)

- **Severity:** High  
- **File:** `data/static/codefixes/dbSchemaChallenge_1.ts`  
- **Description:** Improper use of Sequelize ORM allows unsanitized user input to be directly embedded in SQL queries, leading to potential SQL injection attacks.  
- **OWASP Reference:** A03:2021 – Injection  
- **Mitigation:**  
  - Use parameterized queries or prepared statements.  
  - Avoid constructing SQL queries using string concatenation with user inputs.  
  - Implement input validation and sanitization mechanisms.  
- **Reference:** [SAST Deep Dive](https://medium.com/@josegpach/deep-dive-into-sast-tools-for-advanced-vulnerability-analysis-in-owasp-juice-shop-ab0984b5d5c9)

---

### 2. 🔐 Hardcoded Credentials (CWE-798)

- **Severity:** High  
- **File:** `data/static/users.yml`  
- **Description:** Presence of hardcoded credentials within the source code can lead to unauthorized access if exposed.  
- **OWASP Reference:** A07:2021 – Identification and Authentication Failures  
- **Mitigation:**  
  - Remove hardcoded credentials from the codebase.  
  - Store sensitive information in secure environment variables or secret management services.  
  - Implement access controls and credential rotation policies.  
- **Reference:** [SAST Deep Dive](https://medium.com/@josegpach/deep-dive-into-sast-tools-for-advanced-vulnerability-analysis-in-owasp-juice-shop-ab0984b5d5c9)

---

### 3. ⚠️ Missing Subresource Integrity (SRI) Checks (CWE-353)

- **Severity:** Medium  
- **File:** `frontend/src/index.html`  
- **Description:** External scripts are loaded without Subresource Integrity (SRI) attributes, making the application vulnerable to supply chain attacks.  
- **OWASP Reference:** A08:2021 – Software and Data Integrity Failures  
- **Mitigation:**  
  - Add `integrity` and `crossorigin` attributes to all external `<script>` and `<link>` tags.  
  - Ensure that SRI hashes are correctly generated and match the content of the external resources.  
- **Reference:** [SAST Deep Dive](https://medium.com/@josegpach/deep-dive-into-sast-tools-for-advanced-vulnerability-analysis-in-owasp-juice-shop-ab0984b5d5c9)

---

## ✅ Summary

| CWE ID   | Vulnerability                         | Severity | OWASP Ref | File Path                                   |
|----------|---------------------------------------|----------|------------|---------------------------------------------|
| CWE-89   | SQL Injection via Sequelize           | High     | A03:2021   | `data/static/codefixes/dbSchemaChallenge_1.ts` |
| CWE-798  | Hardcoded Credentials                 | High     | A07:2021   | `data/static/users.yml`                     |
| CWE-353  | Missing Subresource Integrity (SRI)   | Medium   | A08:2021   | `frontend/src/index.html`                   |

---

## 🔧 Recommendations

- Adopt secure coding standards and conduct regular code reviews.  
- Regularly update and patch dependencies.  
- Implement robust secret management solutions.  
- Configure appropriate security headers to protect against common web vulnerabilities.

