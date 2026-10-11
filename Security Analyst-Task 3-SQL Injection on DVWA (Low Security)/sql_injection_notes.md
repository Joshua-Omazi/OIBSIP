# SQL Injection Technical Log & Analysis

## Lab Overview & Target Details
* **Target Application**: Damn Vulnerable Web Application (DVWA)
* **Target Module**: SQL Injection (SQLi)
* **Security Configuration**: Low Security
* **Execution Environment**: Kali Linux VirtualBox / Local XAMPP Server (Apache & MySQL)

---

## Payload Log & Execution Table

| No. | Payload Syntax | Objective | Observed Result | Screenshot Reference |
| :--- | :--- | :--- | :--- | :--- |
| **1** | `1' OR '1'='1` | Authentication / Logic Bypass | Closed the query string early and forced a true condition, dumping all user accounts and records from the database table. | `assets/step5_payload1_auth.png` |
| **2** | `1' OR 1=1 #` | Query Commenting & Bypass | Leveraged the MySQL comment character (`#`) to bypass validation checks without throwing syntax errors. | `assets/step6_payload2_logic.png` |
| **3** | `1' UNION SELECT user, password FROM users #` | Structural Data Extraction (UNION) | Merged the original query with a custom query to extract user names and cryptographic password hashes. | `assets/step7_payload3_union.png` |

---

## Technical Root Cause Analysis
* **Vulnerability Mechanism**: The underlying PHP code directly concatenates user-supplied input (`$_GET['id']`) into the SQL statement string without prior sanitization, escaping, or parameterization:
  ```php
  $query = "SELECT first_name, last_name FROM users WHERE user_id = '$id';";

