
# 🧑‍💻 OWASP Top 10 Demo – SQL Injection (A03:2021)

**Vulnerability:** SQL Injection  
**Category:** OWASP Top 10 – A03:2021 Injection  
**Language:** Node.js (Express + SQLite)  
**Demo Goal:** Show a vulnerable query pattern and apply a secure fix using parameterized queries.

---

## ❌ Before (Vulnerable Code)

```js
// routes/user.js
app.get('/user/:email', function (req, res) {
  const email = req.params.email;
  const query = "SELECT * FROM users WHERE email = '" + email + "'";
  db.get(query, function (err, row) {
    if (err) {
      res.status(500).send("Database error");
    } else {
      res.json(row);
    }
  });
});
```

### 🚨 Risk

This code is vulnerable to SQL Injection.  
For example, if a user inputs: `' OR 1=1 --`  
The query becomes:

```sql
SELECT * FROM users WHERE email = '' OR 1=1 --'
```

This would return all users from the database — potentially leaking sensitive data.

---

## ✅ After (Secure Code – Parameterized Query)

```js
// routes/user.js (patched)
app.get('/user/:email', function (req, res) {
  const email = req.params.email;
  const query = "SELECT * FROM users WHERE email = ?";
  db.get(query, [email], function (err, row) {
    if (err) {
      res.status(500).send("Database error");
    } else {
      res.json(row);
    }
  });
});
```

---

## ✅ Explanation

SQL Injection arises when untrusted user input is directly embedded into SQL statements. In the vulnerable version above, user input is concatenated into the query string, which opens the door to injection attacks.

The secure version uses a **parameterized query**, replacing direct string interpolation with a `?` placeholder. The database driver safely escapes the input, ensuring it’s interpreted as data — not executable SQL.

This simple fix mitigates one of the most common and dangerous web application vulnerabilities.

---

**References:**  
- [OWASP SQL Injection](https://owasp.org/www-community/attacks/SQL_Injection)
- [OWASP Top 10 - A03:2021 Injection](https://owasp.org/Top10/A03_2021-Injection/)
