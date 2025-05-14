
# 🔍 Snyk Vulnerability Report – OWASP Juice Shop

**Scan Tool:** Snyk CLI  
**Scan Date:** May 14, 2025  
**Target Project:** Juice Shop  
**Total Vulnerabilities Found:** 45  
- 🔴 Critical: 10  
- 🟠 High: 19  
- 🟡 Moderate: 15  
- 🟢 Low: 1

---

## 🚨 Top 3 High/Severe Issues

---

### 1. 🧨 Regular Expression Denial of Service (ReDoS)
- **Vuln ID:** `SNYK-JS-ANSIREGEX-1583908`
- **Package:** `ansi-regex@2.1.1`
- **Severity:** High (CVSS 7.5)
- **Dependency Path:** `juice-shop > chalk > has-ansi > ansi-regex`
- **Description:** Maliciously crafted input can trigger catastrophic backtracking in regex evaluation, leading to CPU exhaustion and DoS conditions.
- **Proof of Concept:** Repeated ANSI escape characters like `\u001B[;;;...` can stall processing.
- **Fix Recommendation:** Upgrade to `ansi-regex@>=6.0.1`
- **Reference:** [ansi-regex GitHub PR #37](https://github.com/chalk/ansi-regex/pull/37)

---

### 2. 🔥 Excessive Platform Resource Consumption via `braces`
- **Vuln ID:** `SNYK-JS-BRACES-6838727`
- **Package:** `braces@2.3.2`
- **Severity:** High (CVSS 7.5)
- **Dependency Path:** `juice-shop > check-dependencies > micromatch > braces`
- **Description:** Improper parsing of nested brace patterns can hang the system when fed deeply nested input strings.
- **Proof of Concept:** Input like `{{{{{{{{{{` can trigger resource exhaustion.
- **Fix Recommendation:** Upgrade to `braces@>=3.0.3`
- **Reference:** [Braces Fix Commit](https://github.com/micromatch/braces/commit/a5851e57f45c3431a94d83fc565754bc10f5bbc3)

---

### 3. 🔐 Weak PBKDF2 Hash in `crypto-js`
- **Vuln ID:** `SNYK-JS-CRYPTOJS-6028119`
- **Package:** `crypto-js@3.3.0`
- **Severity:** High (CVSS 7.2)
- **Dependency Path:** `juice-shop > pdfkit > crypto-js`
- **Description:** Uses SHA-1 and only one iteration for PBKDF2, making it highly susceptible to brute-force attacks.
- **Fix Recommendation:** Upgrade to `crypto-js@4.2.0` or configure PBKDF2 with stronger hash (SHA-256) and more iterations.
- **Reference:** [crypto-js Security Advisory](https://github.com/brix/crypto-js/security/advisories/GHSA-xwcq-pm8m-c4vf)

---

## 📌 Final Notes
These findings demonstrate the importance of scanning for open-source dependency risks (SCA) using tools like Snyk.  
For remediation, always test your app after applying upgrades, and avoid `--force` unless you can validate impact.

