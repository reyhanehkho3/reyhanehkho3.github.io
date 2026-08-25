---
title: OTP
publish: true
date created: 2026-08-23
tags:
  - Backend
  - security
  - codeless
---
To understand a **One-Time Password (OTP)**, imagine a traditional key that works only once and then self-destructs. It is an automatically generated string of numbers, letters, or both that authenticates a user for a **single login session or transaction**. 

Here is a deep dive into how OTPs work, why they are secure, and where they are used.

### 1. How OTPs Work (The Two Main Types)
OTPs are not random; they are mathematically generated. There are two primary algorithms used:

- **HOTP (HMAC-Based OTP):** This is **event-based**. The password is generated using a secret key and a **moving counter** (e.g., every time you press a button on a hardware token, the counter increases by 1). The server knows the counter value, so it increments its own counter to match yours.
- **TOTP (Time-Based OTP):** This is **time-based**. The password is generated using a secret key and the **current Unix timestamp** (usually in 30- or 60-second intervals). Because both the server and your authenticator app (like Google Authenticator) have the exact same time, they generate the exact same code simultaneously. 

### 2. The Authentication Flow (Step-by-Step)
When you log into a bank website, here is what happens behind the scenes:

1. You enter your **static** username and password.
2. The server prompts for your OTP.
3. You open your authenticator app (or receive an SMS) to get the current 6-digit code.
4. You type the code into the website.
5. The server uses its copy of your secret key and the current time (TOTP) to generate its own code.
6. **If your code matches the server's code**, access is granted. The server then **marks that specific timestamp as "used,"** so even if a hacker intercepts that code, they cannot reuse it 5 minutes later.

### 3. Why OTPs are Highly Secure (The "Something You Have" Factor)
In cybersecurity, authentication relies on three factors:

- Something you **know** (password).
- Something you **have** (phone, hardware token).
- Something you **are** (fingerprint).

An OTP represents **"something you have."** Even if a hacker steals your master password via a phishing email, they **cannot** log in because they do not physically possess your phone or hardware token that generates the OTP. This protects against:

- **Credential Stuffing** (using stolen passwords from other data breaches).
- **Keyloggers** (software that records your keystrokes).
- **Phishing** (fake login pages that capture your static password).

### 4. OTP Delivery Methods (With Security Rankings)

- **Authenticator Apps (Highest Security):** Apps like Google Authenticator, Microsoft Authenticator, or Authy. The secret key is stored locally on your device and never transmitted over the network, making them immune to SIM-swapping attacks.
- **Hardware Tokens (Highest Security):** Physical devices (like YubiKeys) that generate OTPs via a button press. Completely immune to malware and phishing.
- **SMS Text Messages (Least Secure):** The OTP is sent via cellular networks. SMS is **not encrypted** and is vulnerable to **SIM-swapping** (where a hacker tricks your mobile carrier into transferring your phone number to their SIM card) and SS7 protocol vulnerabilities. **NIST (National Institute of Standards and Technology) officially discourages the use of SMS for OTP delivery.**

### 5. Important Vulnerabilities (The Weaknesses)
While OTPs are strong, they are not invincible:

- **Man-in-the-Middle (MitM) Phishing:** A hacker sets up a fake login page. You enter your OTP, the hacker instantly forwards it to the real bank server, logs in, and starts a session before your OTP expires. (This is countered by **FIDO2/WebAuthn** or requiring a visual confirmation of the transaction).
- **SMS Interception:** As mentioned, SMS can be intercepted or redirected.
- **Clock Drift:** If your phone's internal clock is off by more than a few seconds, TOTP codes will fail to match the server's codes.

### 6. OTP vs. TOTP vs. 2FA (Clarifying the Terms)
- **2FA (Two-Factor Authentication):** The *strategy*. It means you are using two distinct factors to log in.
- **OTP (One-Time Password):** The *tool*. It is the actual code you type in.
- **TOTP (Time-Based One-Time Password):** The *method* used to generate that specific code.

### 7. The Future of OTPs
Major tech companies (Apple, Google, Microsoft) are actively moving **away** from OTPs toward **passkeys**. Passkeys use public-key cryptography; the server never stores a secret that can be stolen, and there is no 6-digit code to type or intercept. The authentication happens via biometrics (Face ID/fingerprint) and is completely phishing-resistant.

---

**In short:** An OTP is a time-sensitive, mathematically generated code that acts as a physical proof of possession. It is a massive security upgrade over passwords alone, but to get the maximum protection, you should always choose **authenticator apps over SMS** for receiving your codes.


---
[[Back-End]]
[[codeless]]