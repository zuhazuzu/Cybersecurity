# GDPR Compliance Checklist – Web-based Booking System

|  **Result**   | **Personal data mapping and minimization**                                                                           |
| :-----------: | :------------------------------------------------------------------------------------------------------------------- |
| &nbsp;✅&nbsp; | Have all personal data collected and processed in the system been<br> identified? (e.g., name, email, age, username) |
| &nbsp;✅&nbsp; | Have you ensured that only necessary personal data is collected (data minimization)?                                 |
| &nbsp;❌&nbsp; | Is user age recorded to verify that the booker is over 15 years old?                                                 |

---

|    **Result**    | **User registration and management**                                                                                                        |
| :--------------: | :------------------------------------------------------------------------------------------------------------------------------------------ |
|  &nbsp;❌&nbsp;   | Does the registration form (page) include GDPR-compliant consent for processing<br> personal data (e.g., acceptance of the privacy policy)? |
| &nbsp;⚠️*1&nbsp; | Can users view, edit, and delete their own personal data via their account?                                                                 |
|  &nbsp;❌&nbsp;   | Is there a mechanism for the administrator to delete a reserver in<br> accordance with the "right to be forgotten"?                         |
| &nbsp;⚠️*2&nbsp; | Is underage registration (under 15 years) and booking functionality restricted?                                                             |
1* User can view their account.
2* Registration is only available for ages 15 and above. this is available in /static/validate-age.js

---

|   **Result**    | **Booking visibility**                                                                                                     |
| :-------------: | :------------------------------------------------------------------------------------------------------------------------- |
| &nbsp;✅*1&nbsp; | Are bookings visible to non-logged-in users only at the resource level<br> (without any personal data)?                    |
| &nbsp;✅*2&nbsp; | Is it ensured that names, emails, or other personal data of bookers are not exposed<br> publicly or to unauthorized users? |
1* Only timetable and resource is visible.
2* Not clearly visible and direct url to /api/users gives unauthorized.

--- 

|   **Result**    | **Access control and authorization**                                                                                                 |
| :-------------: | :----------------------------------------------------------------------------------------------------------------------------------- |
| &nbsp;❌*1&nbsp; | Have you ensured that only administrators can add, modify, and delete<br> resources and bookings?                                    |
| &nbsp;❌*2&nbsp; | Is the system using role-based access control (e.g., reserver vs. administrator)?                                                    |
|  &nbsp;✅&nbsp;  | Are administrator privileges limited to ensure GDPR compliance (e.g., administrators<br> cannot use data for unauthorized purposes)? |
1* Reserver has same rights in resources and booking as admin
2* Reserver has access in same resourses as admin.

---

|    **Result**    | **Privacy by Design Principles**                                                                                 |
| :--------------: | :--------------------------------------------------------------------------------------------------------------- |
|  &nbsp;✅&nbsp;   | Has Privacy by Default been implemented (e.g., collecting the minimum data by default)?                          |
|  &nbsp;✅&nbsp;   | Are logs implemented without unnecessarily storing personal data?                                                |
| &nbsp;⚠️*1&nbsp; | Are forms and system components designed with data protection in mind<br> (e.g., secured login, minimal fields)? |
1* these are minimal, maybe not most secure.

---

|    **Result**    | **Data security**                                                              |
| :--------------: | :----------------------------------------------------------------------------- |
| &nbsp;⚠️*1&nbsp; | Are CSRF, XSS, and SQL injection protections implemented?                      |
| &nbsp;✅*2&nbsp;  | Are passwords securely hashed using a strong algorithm (e.g., bcrypt, Argon2)? |
| &nbsp;⚠️*3&nbsp; | Are data backup and recovery processes GDPR-compliant?                         |
| &nbsp;✅*4&nbsp;  | Is personal data stored in data centers located within the EU?                 |
1* ZAP did not find any weaknesses.
2* example of hashed password for user1@mail.com : ***$2a$10$a1WpeLMUY1MdiIQTdrF/te4rAaCzrBa./hA3wlRxhK/eIja/e1cnK*** 

| Osa                               | Merkitys                                                             |
| --------------------------------- | -------------------------------------------------------------------- |
| `$2a$`                            | Algoritmi = **bcrypt**, versio **2a**                                |
| `10`                              | **Cost factor** (työmäärä / kierrosten määrä) = 2¹⁰ = 1024 kierrosta |
| `a1WpeLMUY1MdiIQTdrF/te`          | **Salt** (22-merkkinen base64)                                       |
| `4rAaCzrBa./hA3wlRxhK/eIja/e1cnK` | Itse **hashattu salasana**                                           |
3* There is not data backups. well basically each person who is doing this task has access to this application, but their databases are unique.
4* It is locally, I am in EU.


---

|   **Result**    | **Data anonymization and pseudonymization**                                         |
| :-------------: | :---------------------------------------------------------------------------------- |
|  &nbsp;❌&nbsp;  | Is personal data anonymized where possible?                                         |
| &nbsp;❌*1&nbsp; | Are pseudonymization techniques used to protect data while maintaining its utility? |
1* When data is accessed via URL or from database, users have no pseudonymizations.

---

|    **Result**    | **Data subject rights**                                                                    |
| :--------------: | :----------------------------------------------------------------------------------------- |
| &nbsp;❌*1&nbsp;  | Can users download or request all personal data related to them (data access request)?     |
| &nbsp;⚠️*1&nbsp; | Is there an interface or process for users to request the deletion of their personal data? |
|  &nbsp;❌&nbsp;   | Can users withdraw their consent for data processing?                                      |
1* I added imaginary email to request personal data in privacypolicy.md (keksitty@mail.md)

---

|  **Result**   | **Documentation and communication**                                                                                 |
| :-----------: | :------------------------------------------------------------------------------------------------------------------ |
| &nbsp;✅&nbsp; | Is there a privacy policy available to users during registration and easily accessible?                             |
| &nbsp;❌&nbsp; | Are administrators and developers provided with documented data protection practices <br>and processing activities? |
| &nbsp;❌&nbsp; | Is there a documented data breach response process (e.g., how to notify authorities <br>and users of a breach)?     |

---

**Symbols used:**  
✅ Pass (a note can be added)  
❌ Fail (a note can be added)  
⚠️ Attention (a note can be added)