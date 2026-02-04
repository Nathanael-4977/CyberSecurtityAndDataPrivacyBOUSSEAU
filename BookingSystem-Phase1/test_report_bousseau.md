# 1️⃣ Introduction

**Tester(s):**  
- Name:Nathanaël BOUSSEAU  

**Purpose:**  
- Identify vulnerabilities in the registration system of a Booking System.

**Scope:**  
- Tested components: Registration page(inputs and database)  
- Exclusions: Login page, reservation system, administrative dashboard  
- Test approach: Gray-box 

**Test environment & dates:**  
- Start:February 2 2026  
- End: February 4 2026 
- Test environment details (OS, runtime, DB, browsers): Docker Desktop, PostgreSQL database, Windows 11, Google Chrome.

**Assumptions & constraints:**  
-testing was restricted to the register page as the login page was blocked for this part.

# 2️⃣ Executive Summary

**Short summary (1-2 sentences):**  The registration system of this booking system is critically vulnerable to some types of attacks, including SQL injections. Data is not encrypted and the system does not apply business rules like age restrictions.

**Overall risk level:** Critical

**Top 5 immediate actions:**  
1. Use prepared statement: Do not trust client side verification. Do not create dynamic SQL queries using simple string concatenation. Apply a list of allowed and not allowed characters.
2. Secure password storage : Hash or encrypt all sensitive datas on the database.
3. Enable anti CSRF token protection : Add unique and random anti-CRSF tokens to the registration form.
4. Enforce backend validation: Add server-side checks for age requirements (15+). 
5. Enforce strong password: Define and implement minimum requirements for password length and complexity.

---

# 3️⃣ Severity scale & definitions

|  **Severity Level**  | **Description**                                                                                                              | **Recommended Action**           |
| -------------------- | ---------------------------------------------------------------------------------------------------------------------------- | -------------------------------- |
|      🔴 **High**     | A serious vulnerability that can lead to full system compromise or data breach (e.g., SQL Injection, Remote Code Execution). | *Immediate fix required*         |
|     🟠 **Medium**    | A significant issue that may require specific conditions or user interaction (e.g., XSS, CSRF).                              | *Fix ASAP*                       |
|      🟡 **Low**      | A minor issue or configuration weakness (e.g., server version disclosure).                                                   | *Fix soon*                       |
| 🔵 **Info** | No direct risk, but useful for system hardening (e.g., missing security headers).                                            | *Monitor and fix in maintenance* |


---

# 4️⃣ Findings (filled with examples → replace)

> Fill in one row per finding. Focus on clarity and the most important issues.

| ID | Severity | Finding | Description | Evidence / Proof |
|------|-----------|----------|--------------|------------------|
| F-01 | 🔴 High | SQL Injection in registration | Input field allows `AND 1=1 --` injection | ZAP scan : `foo-bar@example.com AND 1=1 --` allowed |
| F-02 | 🔴 High | Visible Passwords | Passwords are not hashed in the database | <img width="843" height="140" alt="image" src="https://github.com/user-attachments/assets/191c9bc4-b1e7-46b4-b502-13b924964199" /> |
| F-03 | 🟠 Medium | Absence of birthdate verification | Allows any birthdate, ignoring the age requirement | <img width="843" height="140" alt="image" src="https://github.com/user-attachments/assets/ede47e6b-5ea3-4a2b-8f1f-62190412613f" /> |
| F-04 | 🟠 Medium | Absence of Anti-CSRF Tokens | Lack of anti-CSRF tokens allows attackers to force unauthorized registrations | Zap Scan |
| F-05 | 🟡 Low | Weak password policy | Accepts passwords like "a"| <img width="843" height="140" alt="image" src="https://github.com/user-attachments/assets/ede47e6b-5ea3-4a2b-8f1f-62190412613f" />|
|

5️⃣ OWASP ZAP Test Report (Attachment):

Link to the zap test report : [./zap_report_round1](https://github.com/Nathanael-4977/CyberSecurtityAndDataPrivacyBOUSSEAU/blob/main/BookingSystem-Phase1/zap_report_round1.md)

