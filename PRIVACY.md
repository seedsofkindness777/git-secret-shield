# Privacy Policy for GitSecretShield - Secret Sanitizer & Encryptor

**Effective Date:** October 2, 2026  
**Extension Name:** GitSecretShield - Secret Sanitizer & Encryptor  

GitSecretShield ("we", "our", or "us") is dedicated to protecting developer privacy and keeping your credentials secure. This Privacy Policy explains how GitSecretShield handles data when you use our Chrome browser extension.

---

## 1. Zero-Knowledge & Local-First Philosophy

GitSecretShield operates under a strict **Zero-Knowledge** and **100% Local-First** architecture:
* **Local Processing:** All secret detection, `.env` file sanitization, and AES-256-GCM encryption/decryption take place entirely inside your local browser using client-side JavaScript and the Web Crypto API (`crypto.subtle`).
* **No Code Telemetry:** Your source code, `.env` values, secrets, API keys, passphrases, and scanned files are **never** transmitted to external servers, cloud providers, or third-party analytics.
* **No Server Storage of Passphrases:** Encryption master passphrases are never sent over any network or stored on any server. If you lose your passphrase, encrypted files cannot be recovered by anyone.

---

## 2. Information Collection and Use

### Data We Do NOT Collect
* We do **NOT** collect your source code or project files.
* We do **NOT** collect your detected secrets, credentials, or `.env` content.
* We do **NOT** collect personal browsing history or user profiling data.
* We do **NOT** use tracking cookies or analytics trackers (Google Analytics, Mixpanel, etc.).

### Data Handled for Software Licensing & Personal Communications
* **Customer Email Collection:** Personal communication details (such as your customer email address) are collected during purchase strictly to generate and send the software license key, order receipts, and essential license management emails to the customer.
* **License Validation:** When activating or validating your software license within the extension, the extension communicates securely over HTTPS with `https://api.licensr.app`.
* **Payload Transmitted:** Only your user-entered license key and a non-reversible, deterministic machine identifier (hashed hardware/browser characteristics) are sent to verify seat activation. No code or personal file data is included.

---

## 3. Chrome Extension Permissions Justifications

GitSecretShield requests only the minimal necessary permissions to function safely:

| Permission | Purpose & Justification |
| :--- | :--- |
| `storage` | Used exclusively to save local user preferences (e.g., Light/Dark mode) and cache license activation state locally in `chrome.storage.local`. |
| `activeTab` | Used to inspect active browser tabs on supported Git web platforms when the user triggers inline secret scanning. |
| `tabs` | Required to launch and operate the full-dashboard view (`popup.html?mode=fulltab`) for processing large project directories up to 512MB. |
| `downloads` | Required to trigger native Chrome "Save As" file downloads for sanitized project files, `.gitignore` rules, and encrypted ZIP project vaults. |
| `host_permissions` | Restricted to `https://github.com/*` and `https://gitlab.com/*` for web-based Git repository safety overlays, and `https://api.licensr.app/*` for license activation. |

---

## 4. Third-Party Services

* **Licensr.app (`https://api.licensr.app`):** Used solely for software license key generation, key delivery, and seat activation management. You can review their privacy policy at [https://licensr.app](https://licensr.app).

---

## 5. Security of Your Data

All encryption routines leverage standard **AES-256-GCM** with **PBKDF2 key derivation (100,000 iterations)**. Because all cryptographic operations are executed locally within your Chrome browser environment, your unencrypted secrets never leave your device.

---

## 6. Changes to This Privacy Policy

We may update this Privacy Policy from time to time to reflect extension updates or regulatory standards. Any modifications will be posted to this repository with an updated effective date.

---

## 7. Contact Us

If you have any questions or security inquiries regarding GitSecretShield, please open an issue on our GitHub repository:  
**GitHub Repository:** [https://github.com/YourUsername/git-secret-shield](https://github.com/YourUsername/git-secret-shield)
