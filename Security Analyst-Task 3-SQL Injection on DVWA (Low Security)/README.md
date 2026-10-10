# Task 3: SQL Injection on DVWA (Low Security) — Security Analyst Track

## Overview
This project demonstrates a classic SQL Injection (SQLi) vulnerability exploiting the login form of the Damn Vulnerable Web Application (DVWA) configured on its **Low** security setting[cite: 1]. The objective is to understand how improperly sanitized input handling allows attackers to manipulate backend database queries, extract sensitive information, and learn how developers mitigate these risks[cite: 1].

---

## What is SQL Injection?
SQL Injection is a web security vulnerability that allows an attacker to interfere with the queries that an application makes to its database. It generally occurs when user-supplied input is directly concatenated into dynamic SQL queries without proper sanitization, validation, or parameterization, allowing malicious SQL commands to be executed directly by the database engine.

---

## Attack Walkthrough & Analysis

### 1. Environment Setup
* Deployed DVWA locally via XAMPP on Apache and MySQL[cite: 1].
* Initialized the database schema through the setup interface[cite: 1].
* Configured the security settings level to **Low**[cite: 1], disabling input sanitization and anti-CSRF token checks to simulate vulnerable legacy code.

### 2. Exploitation & Payload Breakdown

#### Payload 1: `' OR '1'='1`[cite: 1]
* **How it works**: The single quote closes the original SQL string literal prematurely, followed by a logical condition `OR '1'='1'` which always evaluates to true. Because the condition is always true, the WHERE clause matches every single record in the database table.
* **Exposed Data**: Bypassed authentication logic, exposing user IDs, first names, surnames, user logins, and hashed passwords for all registered accounts[cite: 1].

#### Payload 2: `' UNION SELECT null, user() --`[cite: 1]
* **How it works**: Uses the `UNION` operator to combine the results of the original query with a malicious query. The `user()` function queries the database management system to return the current database user context, while `--` comments out the remainder of the original query syntax.
* **Exposed Data**: Revealed internal database user privileges and account privileges.

#### Payload 3: `' UNION SELECT null, version() --`[cite: 1]
* **How it works**: Appends a `UNION` query retrieving the database server version (`version()`), allowing an attacker to map software vulnerabilities specific to that database engine release.
* **Exposed Data**: Disclosed the exact backend database system release version.

---

## Remediation & Prevention
To protect applications from SQL injection vulnerabilities, developers must adopt secure coding practices:

1. **Parameterized Queries / Prepared Statements**: The most effective defense. Parameterization ensures that user input is treated strictly as data, never as executable code or query syntax.
2. **Input Validation and Whitelisting**: Ensure inputs conform to expected data types, lengths, and character sets.
3. **Principle of Least Privilege**: Restrict database accounts used by the web application so they only possess permissions necessary for their specific operational scope.
