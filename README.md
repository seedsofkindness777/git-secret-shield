# GitSecretShield - Secret Sanitizer & Encryptor (Chrome Extension)

A Google Chrome Extension (Manifest V3) that inspects, redacts, encrypts (AES-256-GCM), and decrypts `.env` files, production tokens, and cloud API keys before developers commit or upload them to Git repositories.

---

## Architecture & Security Highlights

- **100% Client-Side & Local:** Zero telemetry, zero cloud network calls. All analysis and cryptographic operations run directly in the browser.
- **Standards-Compliant Cryptography:** Uses browser-native `window.crypto.subtle` with **PBKDF2 (100,000 rounds of SHA-256)** key derivation and **AES-256-GCM** authenticated encryption.
- **Deep Cloud Credential Coverage:**
  - Google Cloud / Firebase / Gemini API keys (`AIza...`)
  - AWS Access Key IDs & Secret Access Keys
  - GitHub Personal Access Tokens (`ghp_...`, `github_pat_...`)
  - OpenAI & Anthropic Claude API keys
  - Slack & Stripe keys
  - Private SSH/RSA keys
  - Database connection URIs (`mongodb+srv://`, `postgresql://`)
  - Generic `.env` secret key-values (`JWT_SECRET`, `PASSWORD`, `API_KEY`)
- **Proactive Git Upload Protection:** Injects a guardian into GitHub and GitLab file upload pages (`/upload/*`) to prevent accidental web drag-and-drop of `.env` files.

---

## How to Install in Google Chrome

1. Open Google Chrome and navigate to:
   ```
   chrome://extensions
   ```
2. In the top-right corner, toggle **Developer mode** to **ON**.
3. Click the **Load unpacked** button in the top-left corner.
4. Select the project directory:
   ```
   C:\Users\[User-Computer]\git-secret-shield-extension
   ```
5. Pin **GitSecretShield** to your Chrome toolbar.

---

## Features & Usage

### 1. Scan & Redact Secrets
1. Click the GitSecretShield extension icon to open the popup.
2. Drag and drop any `.env`, `.json`, `.yaml`, or source code file into the dropzone (or paste raw text).
3. The scanner displays all detected secrets categorized by severity (`CRITICAL`, `HIGH`, `MEDIUM`).
4. Click **Redact All Secrets** to replace real keys with safe structured placeholders.
5. Click **Export .env.example** to automatically generate a sanitized template ready for version control.
6. Click **Download Clean File** to get your sanitized code.

### 2. Encrypt Secrets with AES-256-GCM
1. In the **AES-256 Encrypt** tab, enter a master passphrase.
2. Click **Encrypt with AES-256-GCM**.
3. Download the generated `.env.enc` armored envelope. This encrypted file is safe to commit or share with authorized collaborators.

### 3. Decrypt Secrets Locally
1. In the **Decrypt** tab, upload or paste an armored `.env.enc` file.
2. Enter your master passphrase and click **Decrypt Original Secrets**.
3. The original plaintext configuration is restored locally for active development.

### 4. Bulletproof `.gitignore` Generator
- The **.gitignore** tab provides standard rules preventing accidental commits of `.env`, `credentials.json`, service account keys, and SSH certificates.

---

## Running Automated Tests

To run the full suite of unit tests for the scanner, sanitizer, and crypto engine:
```bash
node test/scanner.test.js
```
