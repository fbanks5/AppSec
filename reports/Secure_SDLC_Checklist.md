
# ✅ Secure Software Development Lifecycle (SDLC) Checklist – Juice Shop

**Assessment Date:** May 14, 2025  
**Assessed by:** Frantz Banks

---

## 🔍 1. Requirements

- [x] Security requirements defined (e.g., data protection, authentication)
- [x] OWASP Top 10 reviewed and used as baseline

---

## 🛠️ 2. Design

- [x] Reviewed for risky components (user input handling, ORM usage)
- [x] Potential attack vectors diagrammed or discussed
- [x] Secure design principles applied

---

## 🧑‍💻 3. Implementation

- [x] Avoided known insecure patterns (e.g., `eval`, string-based SQL)
- [x] Secrets are not hardcoded (identified and flagged via CodeQL)
- [x] Package dependencies are scanned using Snyk/npm audit

---

## 🔬 4. Testing

| Tool      | Type | Coverage |
|-----------|------|----------|
| OWASP ZAP | DAST | Runtime scan against localhost instance |
| CodeQL    | SAST | GitHub-native static scan of codebase |
| Snyk CLI  | SCA  | Package and dependency scanning |
| Manual    | Manual | Custom SQLi test + patch validation |

---

## 🚀 5. Deployment

- [ ] All high/critical vulnerabilities patched before deployment
- [x] CI pipeline includes GitHub Code Scanning
- [ ] Secrets managed in environment variables or secret managers

---

## 🔄 6. Maintenance

- [x] Security tools configured to scan weekly or on every PR
- [ ] Retest after any dependency or ORM updates
- [x] Audit logs enabled (pending verification)

---

**Next Steps:**
- Patch all high/critical vulnerabilities found in SAST and SCA
- Implement runtime protections (e.g., helmet.js, security headers)
- Apply secrets management via `.env` or AWS/GCP secrets manager
