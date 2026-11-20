# 🔐 Week 3: PDF Password Cracking & Hash Extraction Labs

**Cybersecurity Internship — Networkwalks**  
**Author:** Vishal Pal ([GitHub](https://github.com/devvishalpal) | [LinkedIn](https://www.linkedin.com/in/vishal-pal-01840324b))

---

## 📌 Overview

This repository documents the completion of **Week 3 Project Modules (PM1 & PM2)** from the **Networkwalks Cybersecurity & Ethical Hacking Internship**. The objective of these labs was to understand how password-protected PDF documents store cryptographic hashes (`$pdf$...`), extract those hashes using both online and local utilities, and execute dictionary/wordlist attacks to recover weak passwords.

---

## 🛠️ Tools & Technologies Used

* **John the Ripper (JTR) Jumbo (`1.9.0-jumbo-1`)** – Command-line password auditing and hash-cracking utility.
* **Johnny (`v2.2`)** – Cross-platform GUI frontend for John the Ripper.
* **OnlineHashCrack (PDF Hash Extractor)** – Web-based `pdf2john` hash extraction tool.
* **Networkwalks Hash Calculator** – Browser-based cryptographic hash generator and `$pdf$` hash extractor.
* **Networkwalks Password Cracker** – Browser-based dictionary attack lab tool for matching `$pdf$` hashes against wordlists.
* **Kali Linux / Windows Environment** – Lab execution environment.

---

## 📂 Project Modules & Methodology

### 🔹 Module 1: Password Cracking with John the Ripper (JTR) & Johnny GUI (`W3-PM1`)
**Objective:** Extract the cryptographic hash from an encrypted PDF (`My Locked PDF1.pdf`) and crack its password using John the Ripper and Johnny.

1. **Setup & Configuration:**
   * Downloaded and configured **John the Ripper Jumbo** and linked `john.exe` inside the **Johnny GUI** settings.
2. **Hash Extraction:**
   * Extracted the `$pdf$` hash string from `My Locked PDF1.pdf` using `pdf2john` / OnlineHashCrack (`$pdf$4*4*128*-1060*...`) and saved it to `hash1.txt`.
3. **Cracking Execution:**
   * Loaded `hash1.txt` into Johnny (`PASSWD` format) and initiated a dictionary attack.
   * *(CLI Alternative on Kali Linux)*:
     ```bash
     pdf2john "My Locked PDF1.pdf" > hash1.txt
     john --format=PDF hash1.txt
     john --show hash1.txt
     ```
4. **Result:**
   * Successfully recovered the password (`password1`) and unlocked the target PDFs to capture the flags.

---

### 🔹 Module 2: Browser-Based Password Cracking with Networkwalks Tools (`W3-PM2`)
**Objective:** Perform end-to-end client-side hash extraction and dictionary-based password recovery using the Networkwalks web security suite.

1. **Client-Side Hash Extraction:**
   * Uploaded `My Locked PDF1.pdf` to the **Networkwalks Hash Calculator** (`networkwalks.com/hash-calculator/`) to parse the file locally and extract the `pdf2john`/`hashcat`-compatible `$pdf$` hash (Revision R4, Version V4, 128-bit key length).
2. **Dictionary Attack:**
   * Pasted the extracted `$pdf$` hash into the **Networkwalks Password Cracker** (`networkwalks.com/password-cracker/`).
   * Executed a dictionary attack against the built-in wordlist (100 common passwords).
3. **Result:**
   * Matched the hash at entry `91/100` (`[+] MATCH password1`) and unlocked the PDF documents.

---

## 🚩 Captured Flags

| Flag ID | Captured Flag String | Source / Module |
| :--- | :--- | :--- |
| **Flag 1** | `nw{cybersecurity_flag_captured_2608}` | Week 3 PDF Lab |
| **Flag 2** | `nw{networkwalks_persistence_jtr_270521}` | JTR Persistence Lab |
| **Flag 3** | `nw{networkwalks_flag_260821_1}` | Week 3 PDF Lab |
| **Flag 4** | `nw{networkwalks_flag1_jtr_270521_1}` | JTR Module 1 Lab |

---

## 📸 Proof of Completion (Screenshots)

* **Hash Extraction (`OnlineHashCrack`):**  
  `![Hash Extraction](./screenshots/hash-extraction.png)`
* **Captured Flags Verification:**  
  `![Flag 1](./screenshots/flag1.png)`  
  `![Flag 2](./screenshots/flag2.png)`  
  `![Flag 3](./screenshots/flag3.png)`  
  `![Flag 4](./screenshots/flag4.png)`

---

## 🛡️ Key Security Takeaways

* **Encryption vs. Hashing:** Encryption is a two-way process reversible with the right key, whereas hashing is a one-way cryptographic function used to verify passwords without storing them in plaintext.
* **Vulnerability of Weak Passwords:** Even with 128-bit PDF encryption, predictable dictionary words like `password1` can be cracked within seconds using standard wordlists.
* **Mitigation:** Always enforce high-entropy passwords (12+ characters combining uppercase, lowercase, numbers, and symbols) to resist dictionary and brute-force attacks.

---

## ⚠️ Disclaimer

All techniques, tools, and findings documented in this repository were performed strictly for **educational purposes** within an authorized lab environment provided by **Networkwalks Academy**.
