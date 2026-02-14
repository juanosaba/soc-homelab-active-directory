# Detection of Kerberos Password Spraying in Active Directory

## Objective

This lab simulates a Kerberos password spraying attack from a single internal IP address within a short time window (~30 seconds).

The objective was to:

- Generate multiple Event ID 4771 (Kerberos pre-authentication failed).
- Analyze source IP consistency.
- Review authentication method (Kerberos).
- Examine failure codes (0x18 – bad password).
- Determine whether the behavior matches a fast password spraying pattern rather than normal user error.

---

## Attack Simulation

- A password spraying attack was simulated by performing multiple failed authentication attempts within a short time window (less than 30 seconds).
- From CLIENT01, login attempts were made using the account `CORP\juan.lab` with an incorrect password repeatedly.
- Security logs were reviewed on the Domain Controller (DC01).
- Multiple Event ID 4771 (Kerberos pre-authentication failed) entries were identified.
- The source IP address (192.168.100.20) was analyzed, confirming that all attempts originated from the same host.
- The failure code 0x18 (bad password) was verified.
- The authentication protocol used was confirmed to be Kerberos.
- The temporal proximity of the events was analyzed, showing that all attempts occurred within a 30-second window.

---

## Analysis & Detection Logic

The observed pattern does not align with typical human behavior due to the high frequency of failed authentication attempts.

While a legitimate user may mistype a password once or twice, the generation of multiple Event ID 4771 entries within a 30-second window strongly suggests automated trial-and-error activity.

The consistency of the source IP address and the rapid succession of attempts reinforce the hypothesis of a fast password spraying attack rather than normal user authentication errors.

---

## Mitigation

To reduce the impact of password spraying attacks, the following measures are recommended:

- Implement an appropriate Account Lockout Policy.
- Configure SIEM alerts for multiple Event ID 4771 entries originating from the same IP address.
- Monitor failed authentication attempts affecting multiple user accounts from a single source.
- Enforce Multi-Factor Authentication (MFA).
- Disable legacy authentication protocols such as NTLM whenever possible.
- Apply the principle of least privilege across user accounts.

---

## Lessons Learned

- A single Event ID 4771 is not sufficient to classify an incident.
- Temporal correlation is critical to distinguish human error from automated attacks.
- Source IP analysis is fundamental for accurate detection.
- Low & slow attacks can be harder to detect than fast spraying attempts.
- Proper audit policy configuration is essential to ensure reliable telemetry.
