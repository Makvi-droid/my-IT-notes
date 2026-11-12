## **Authentication vulnerabilities**
- **What it is:** Flaws in how a website verifies _who_ a user is (login, password resets, 2FA, session handling).
- **Why it's critical:** Breaking authentication gives attackers direct access to accounts, sensitive data, and unlocks **new attack surfaces** (pages/features only visible to logged-in users).

---
## **What is the difference between authentication and authorization?**
- Authentication is about verifying that the user accessing a certain system is truly them. This can be applied by using features such as 2fa, MFA, OTP etc. while authorization is what the user can access on the system based on the privileges/permissions allowed onto them.

---
## **Brute-force attacks**
- **What it is:** Automated trial-and-error guessing of login credentials (usernames and passwords) at high speed using wordlists and specialized tools (like Burp Intruder or Hydra).
- **How attackers make it smarter:** Instead of pure random guessing, they use logic and public info (OSINT, leaked data breaches, company naming conventions like `first.last@company.com`) to narrow down guesses and crack accounts much faster.
- **Why it works:** Websites that rely _only_ on passwords without proper defenses (like rate limiting, account lockouts, or CAPTCHAs) can be overwhelmed with thousands of login attempts.

---
## **Brute-forcing usernames**
- **Predictable Patterns:** Usernames are easy to guess when they follow standard company formats (e.g., `firstname.lastname@company.com`) or use default admin names (`admin`, `administrator`, `root`).
- **Where to Look (Recon / Enumeration):**
    - **Public User Profiles:** Even if profile details are private, the display name or URL slug often matches the actual login username.
    - **HTTP Responses:** Inspect source code, headers, and API responses for leaked staff or IT support email addresses.

---
## **Brute-forcing passwords**
- **What it is:** Automated password guessing; how hard it is depends directly on password strength and randomness (**entropy**).
- **How websites defend against it (Password Policies):** Apps force users to create complex, high-entropy passwords by requiring:
    - A minimum character length
    - Mixed-case letters (uppercase + lowercase)
    - Numbers and special characters (e.g., `!@#$`)
- **The Human Weak Link:** Strict password policies backfire because humans prioritize memorability over true randomness. Instead of creating truly random strings, users take a simple word and force it to fit the rules.
- **Predictable Habits:**
    - **Rule-stuffing:** Capitalizing the first letter and adding a number + symbol at the end (e.g., `mypassword` $\rightarrow$ `Mypassword1!`).
    - **Leetspeak:** Swapping letters for lookalike numbers/symbols (e.g., `Myp4$$w0rd`).
    - **Forced Password Rotations:** When forced to change passwords regularly, users make tiny, predictable tweaks (e.g., `Mypassword1!` $\rightarrow$ `Mypassword2!` or `Mypassword1?`).
- **How Attackers Exploit This:** Attackers use rule-based wordlists (like Hashcat rules or Burp Intruder payload processing) to automatically apply these exact human mutations to common words, bypassing the need to guess every random character combination.

---
## **Username enumeration**
- **What it is:** Identifying valid usernames by observing subtle differences in how a website responds to login or registration attempts.
- **Where it happens:**
    - **Login forms:** Entering a valid username with a wrong password triggers a slightly different response than an invalid username (e.g., _"Incorrect password"_ vs. _"Invalid username"_, or tiny differences in response times/status codes).
    - **Registration forms:** Trying to sign up with a username that is already taken returns _"Username unavailable"_.
- **Why it matters:** It cuts brute-force time in half—instead of guessing both username _and_ password, the attacker builds a confirmed shortlist of valid accounts first and focuses solely on cracking their passwords.

---
## **Bypassing two-factor authentication**
- **What it is:** Exploiting flawed 2FA logic to access an account without ever providing the second verification factor (like an OTP or SMS code).
- **The Flaw (Broken Multi-Step State):** When an app separates the login into two pages (Step 1: Password $\rightarrow$ Step 2: 2FA Code), it sometimes treats the user as **already logged in** right after Step 1 succeeds.
- **How it's exploited:**
    1. Log in with a valid username and password.
    2. When redirected to the 2FA verification page, ignore it and manually browse straight to a protected, logged-in URL (e.g., `/my-account` or `/dashboard`).
    3. Because the backend fails to check whether Step 2 was actually completed, it loads the account page anyway.