# CVE-2023-7173: Stored Cross-Site Scripting (XSS) in Hospital Management System

## Vulnerability Details

- **CVE ID:** [CVE-2023-7173](https://nvd.nist.gov/vuln/detail/CVE-2023-7173)
- **Vulnerability Type:** Stored XSS
- **Affected Component:** User login page
- **Vulnerable Parameter:** Fullname
- **Ventor Details:** [phpgurukul.com](https://phpgurukul.com/hospital-management-system-in-php/)
- **Vulnerable Version:** Hospital Management System 1.0

## Vulnerability Description

Stored Cross-Site Scripting (XSS) is a serious web vulnerability that allows malicious code to be injected into a website, stored in the database, and later executed when other users view the infected page. In this specific case, the vulnerability is found in the user login page of a Hospital Management System (HMS), where the "Fullname" parameter is susceptible to stored XSS attacks. The lack of proper input validation and data sanitization allows an attacker to inject malicious scripts, potentially compromising user accounts, stealing sensitive information, or performing unauthorized actions.

## Steps to Reproduce (PoC)


### Clone the Repository:

```bash
git clone https://github.com/sharathc213/CVE-2023-7172.git
cd CVE-2023-7172
```

### Run Docker Compose:

```bash
docker-compose up -d
```

### Access the User Registration Form:
   - Open a web browser and navigate to the user registration form at `http://localhost:8080/hms/registration.php`

### Fill in the Registration Form:
   - Input the following payload in the "Fullname" field:
     ```
     <img src="x" onerror=alert(document.cookie)>
     ```
     ![POC](https://github.com/sharathc213/CVE-2023-7173/blob/main/1.jpg)
   - Complete the other required fields with valid information.

### Submit the Registration Form:
   - Click the "Submit" button to send the registration data to the server.

### Check for Successful Registration:
   - Receive a successful registration confirmation message.

### Login with the Registered Email:
   - Navigate to the login page at `http://localhost:8080/hms/user-login.php`.

### Enter the Registered Email:
   - In the login form, enter the email address used for registration.

### Log In:
   - Submit the login form by clicking the "Log In" button.

### Observing the XSS Payload:
 ![POC](https://github.com/sharathc213/CVE-2023-7173/blob/main/2.jpg)
   - Upon successful login, the XSS payload should trigger an alert box displaying the user's cookies, indicating the existence of the Stored XSS vulnerability.

## Impact of Stored XSS in a Hospital Management System

A Stored XSS vulnerability in a Hospital Management System can have severe consequences, including:

1. **Patient Data Exposure:**
   - Potential theft of sensitive patient data for identity theft or fraud.

2. **Patient Safety Risks:**
   - Unauthorized changes in patient records could jeopardize patient safety.

3. **Unauthorized Actions:**
   - Attacker could execute actions on behalf of users, leading to unauthorized access and potential misuse.

4. **Trust Erosion:**
   - Harm to the reputation of the healthcare facility due to breached trust.

5. **Regulatory Non-Compliance:**
   - Violation of data protection regulations, resulting in fines and legal consequences.

6. **Disruption of Healthcare Services:**
   - Possible disruptions in patient care, prescription errors, or misdiagnoses with severe health implications.

7. **Legal and Ethical Implications:**
   - Legal liability for any harm caused, along with ethical concerns about patient privacy.

8. **Financial Consequences:**
   - Costs associated with remedying the breach, including investigations, system upgrades, and legal expenses.

## Mitigation Recommendations

To address this vulnerability, implement the following mitigation measures:

- **Input Validation and Sanitization:**
  - Implement strict input validation and data sanitization routines to ensure that user-generated content is free from malicious code. This includes validating data on both the client and server sides.

## Disclaimer

This  project is intentionally vulnerable and should only be used for educational and testing purposes. Do not deploy this in a production environment.
