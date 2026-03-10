# GDPR Compliance Checklist – Web-based Booking System

| **Result** | **Personal data mapping and minimization** | **Note**|
| :----: | :--- | :--- |
| &nbsp;✅&nbsp; | Have all personal data collected and processed in the system been<br> identified? (e.g., name, email, age, username) |The system only processes email, birthdate and password| 
| &nbsp;✅&nbsp; | Have you ensured that only necessary personal data is collected (data minimization)? |No additional data like phone number or address is collected when a resource is booked|
| &nbsp;✅&nbsp; | Is user age recorded to verify that the booker is over 15 years old? |This is a rule implemented in the system|

---

| **Result** | **User registration and management** | **Note**|
| :----: | :--- | :--- |
| &nbsp;⚠️&nbsp; | Does the registration form (page) include GDPR-compliant consent for processing<br> personal data (e.g., acceptance of the privacy policy)?|The UI includes an explicit checkbox to accept the Terms of Service, but the linked page is currently blank in the application. Since users cannot read the terms, the current implementation is legally invalid.|
| &nbsp;⚠️&nbsp; | Can users view, edit, and delete their own personal data via their account? | Users can view their account informations but cannot update them or delete its own account |
| &nbsp;❌&nbsp; | Is there a mechanism for the administrator to delete a reserver in<br> accordance with the "right to be forgotten"? | The current administrator interface lacks the actual functionality to delete a user account. This prevents the system from complying with the "right to be forgotten"|
| &nbsp;✅&nbsp; | Is underage registration (under 15 years) and booking functionality restricted? | To login, you cannot say that you are under 15. For every guest, the booking functionality is restricted |

---

| **Result** | **Booking visibility** | **Note**|
| :----: | :--- | :--- |
| &nbsp;✅&nbsp; | Are bookings visible to non-logged-in users only at the resource level<br> (without any personal data)? | The reserver email is hidden when someone is not logged in |
| &nbsp;✅&nbsp; | Is it ensured that names, emails, or other personal data of bookers are not exposed<br> publicly or to unauthorized users? | The reserver email is hidden when someone is not logged in |

--- 

| **Result** | **Access control and authorization** | **Note**|
| :----: | :--- | :--- |
| &nbsp;❌&nbsp; | Have you ensured that only administrators can add, modify, and delete<br> resources and bookings? | Reservers can also modify or delete another user booking. This is a severe security breach. Also, reservers can add a resource. |
| &nbsp;⚠️&nbsp; | Is the system using role-based access control (e.g., reserver vs. administrator)? | Theoritically yes, but as  we said before, there is a security breach allowing users to act as administrator |
| &nbsp;⚠️&nbsp; | Are administrator privileges limited to ensure GDPR compliance (e.g., administrators<br> cannot use data for unauthorized purposes)? | Limited by the terms of service but they have total access to the database |

---

| **Result** | **Privacy by Design Principles** | **Note**|
| :----: | :--- | :--- |
| &nbsp;✅&nbsp; | Has Privacy by Default been implemented (e.g., collecting the minimum data by default)? | Yes |
| &nbsp;✅&nbsp; | Are logs implemented without unnecessarily storing personal data? | Yes |
| &nbsp;⚠️&nbsp; | Are forms and system components designed with data protection in mind<br> (e.g., secured login, minimal fields)? | Backend components lack proper authorization checks (IDOR) |

---

| **Result** | **Data security** | **Note**|
| :----: | :--- | :--- |
| &nbsp;⚠️&nbsp; | Are CSRF, XSS, and SQL injection protections implemented? | Yes, but beware of the IDOR attacks | 
| &nbsp;✅&nbsp; | Are passwords securely hashed using a strong algorithm (e.g., bcrypt, Argon2)? | Yes |
| &nbsp;❌&nbsp; | Are data backup and recovery processes GDPR-compliant? | Currently running on local Docker containers without a documented, encrypted backup strategy |
| &nbsp;✅&nbsp; | Is personal data stored in data centers located within the EU? | Yes, in local |

---

| **Result** | **Data anonymization and pseudonymization** | **Note**|
| :----: | :--- | :--- |
| &nbsp;⚠️&nbsp; | Is personal data anonymized where possible? | A login user can see the mail of a reserver. It is not necessary for him to see who booked a ressource |
| &nbsp;⚠️&nbsp; | Are pseudonymization techniques used to protect data while maintaining its utility? | No complex pseudonimization is actively used in the database |

---

| **Result** | **Data subject rights** | **Note**|
| :----: | :--- | :--- |
| &nbsp;⚠️&nbsp; | Can users download or request all personal data related to them (data access request)? | There is no download my data button. To do it, a user has to contact an administrator. |
| &nbsp;⚠️&nbsp; | Is there an interface or process for users to request the deletion of their personal data? | Same as above. But according to the policy, a user can ask for it. |
| &nbsp;⚠️&nbsp; | Can users withdraw their consent for data processing? | The booking system does not ask for any consent. The legal basis is a contract. To withdraw, they must terminate the contract by deleting their account.|

---

| **Result** | **Documentation and communication** | **Note**|
| :----: | :--- | :--- |
| &nbsp;⚠️&nbsp; | Is there a privacy policy available to users during registration and easily accessible? | The document is written but not available on the main page yet. |
| &nbsp;❌&nbsp; | Are administrators and developers provided with documented data protection practices <br>and processing activities? |While public documentations have been made, no internal documentation is existing at the moment. The administrators are then in the obligation to follow the public documents rules but have no other specifications. |
| &nbsp;❌&nbsp; | Is there a documented data breach response process (e.g., how to notify authorities <br>and users of a breach)? | No response plan exists if the database is compromised. |

---

**Symbols used:**  
✅ Pass (a note can be added)  
❌ Fail (a note can be added)  
⚠️ Attention (a note can be added)
