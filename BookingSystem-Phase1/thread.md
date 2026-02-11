Introduction :

In the part one of the first phase, I identified 5 main security breaches. Those 5 breaches are the following :

- SQL injection
- Cleartext Password in the database
- Absence of Anti-CSRF tokens
- Age Limit Bypass
- Weak Password Policy

During the second part on the first phase, I checked if these issues had been fixed or not fixed.

Below is the status report for each finding, including the verification steps taken to confirm whether the issues have been resolved.


1 : SQL Injection :

Status : Fixed 

Identification (Part 1) : The OWASP ZAP scan successfully injected the boolean payload “foo-bar@example.com AND 1=1 --” into the input field, proving the database was vulnerable to unauthorized manipulation.

Verification (Part 2) : To verify if the issue was fixed, I used two methods. The first one is the OWASP ZAP scan. Then, to double check,I also used the dev tool bar, changing the input type from “email” to “text” to bypass the client side verification to see if the injection was possible or not. 

Result : The backend successfully intercepted the payload and returned an "invalid email" error. Also, the OWASP ZAP scan no longer detects any SQL injection issue. The server-side validation is now functional.

Evidence : This page is the result of the SQL injection test with the email address “foo-bar@example.com AND 1=1 --”
<img width="742" height="269" alt="Capture d&#39;écran 2026-02-11 154150" src="https://github.com/user-attachments/assets/7b0d9b86-4be3-4957-8220-1bf2be45aaa7" />


2 : Cleartext password storage :

Status : Fixed 

Identification (part 1) : I accessed the postgreSQL database via the terminal and observed (with SELECT * FROM booking_users;) that the users passwords were stored without hashing.

Verification (part 2) : After registering another account, I accessed again the postgreSQL database with the command SELECT * FROM booking_users;

Result : The users passwords are now stored with a hash, making it more secure.

Evidence : This image is the database. We can see that the passwords are now hashed.

<img width="1913" height="242" alt="Capture d&#39;écran 2026-02-11 161110" src="https://github.com/user-attachments/assets/73429668-ba92-4a19-81e1-756cbfcb0cb4" />

​​​
3 : Missing Anti-CSRF Tokens:

Status : Not Fixed 

Identification (part 1) : The OWASP ZAP scan showed a medium alert, being the absence of Anti-CSRF Tokens.

Verification (part 2) : I ran an OWASP ZAP scan again

Result : The OWASP ZAP scan report showed the same problem again, no Anti-CRSF Tokens are present in this website.

Evidence : zap_report_round2.md on github
<img width="669" height="98" alt="Capture d&#39;écran 2026-02-11 161602" src="https://github.com/user-attachments/assets/58f7e84a-ae3d-40ed-aefc-048e0f4de08c" />


4 : Age Limit Bypass :

Status : Not Fixed 

Identification (part 1) : I manually attempted to register a user being under 15 years old. The system accepted the registration.

Verification (part 2) : Again, I manually attempted to register a user being under 15 years old. 

Result : The system validated again the registration without showing an error, violating the rule saying that a user should be at least 15 years old.

Evidence : On the database, you can see three users that are underage. The other image is the succesfull registration.
<img width="1913" height="242" alt="Capture d&#39;écran 2026-02-11 161110" src="https://github.com/user-attachments/assets/8dcb7f9c-3106-446d-8b77-e49e62afd26b" />
<img width="807" height="312" alt="Capture d&#39;écran 2026-02-11 152859" src="https://github.com/user-attachments/assets/368b38af-fcc3-4815-9ff3-ce14d787d025" />

​​​​
5 : Weak Password Policy :

Status : Fixed 

Identification (part 1) : I manually tested the password complexity by attempting to register an account using a single character “a”. The system accepted it.

Verification (part 2) : Again, I manually tested the password complexity by attempting to register an account using a single character “a”. 

Result : The application blocked the registration and displayed an error message saying that the password should be at least 8 characters.

Evidence : The error page 

<img width="656" height="312" alt="Capture d&#39;écran 2026-02-11 152945" src="https://github.com/user-attachments/assets/9639bd84-42bd-4122-abf5-98d20a8021c8" />

​​​
You can find the zap report on github under the name “zap_report_round2.md”
