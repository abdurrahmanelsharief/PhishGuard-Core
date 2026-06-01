# PhishGuard-Core
An automated, multi-tiered email security engine for detecting phishing and zero-day threats using Heuristics, ML, and dynamic sandboxing
# 🛡️ PhishGuard Core - Enterprise Email Security Engine

**PhishGuard** is an automated, multi-tiered email security engine designed to detect, analyze, and neutralize advanced phishing attacks, zero-day payloads, and social engineering attempts in real-time.

## 🚀 Architecture Overview
PhishGuard operates on a "Graceful Degradation" architecture, ensuring that the system remains online and continues scanning even if external threat intelligence APIs timeout or fail. It processes raw `.eml` files through three strict defense layers:

### 1. Layer 1: Heuristics & Authentication (Pre-flight Checks)
* **DNS Verification:** Validates SPF, DKIM, and DMARC records to detect email spoofing.
* **Domain Analysis:** Calculates domain entropy to catch DGA (Domain Generation Algorithms) and newly registered/suspicious TLDs.
* **OCR Scanning:** Extracts text from embedded images to bypass image-based spam filters.

### 2. Layer 2: Machine Learning & NLP
* Utilizes a custom-trained ML pipeline (Scikit-Learn/Joblib) to analyze email body text.
* Detects urgency, financial requests, and social engineering patterns typical of zero-day phishing campaigns.

### 3. Layer 3: Dynamic Sandboxing & Threat Intel
* **URL Rewriting & Analysis:** Proxies suspicious links and checks them against VirusTotal.
* **Payload Detonation:** Hashes attachments and routes unknown/zero-day executables and scripts (e.g., `.bat`, `.vbs`, `.pdf`) to **Hybrid Analysis** for deep behavioral sandboxing.

---

## 🔒 Security Notice & IP Protection
This repository contains the **PhishGuard Core Framework** intended for architectural demonstration and peer review. 

For security and intellectual property reasons, the following components are **NOT** included in this public repository:
- Proprietary Machine Learning `.joblib` models and training datasets.
- Custom YARA rules used for internal threat hunting.
- Production API Keys and `.env` configurations.

---

## ⚙️ Technical Stack
* **Framework:** FastAPI (Python 3.x)
* **Threat Intel Integrations:** Hybrid Analysis API, VirusTotal API
* **Libraries:** `whois`, `dnspython`, `scikit-learn`, `pytesseract`

## 📊 Sample Execution
When a zero-day payload bypasses Layer 1 & 2, the engine automatically queues the file for behavioral analysis:
> `[+] Triggered Rule: WARNING: zero_day_queued_for_sandbox`
> `[+] Threat Score: 0.850 (CRITICAL)`

## 🗺️ Future Roadmap (Under Development)
- [x] Core Heuristics and ML Engine integration.
- [x] External Sandbox API fault tolerance (Graceful Degradation).
- [ ] **Command & Control (C2):** Real-time Telegram Bot integration for instant SOC alerts.
- [ ] **Audit Logging:** SQLite/PostgreSQL database implementation for historical threat analysis.
*Developed by a dedicated Security Researcher aiming to bridge the gap between static analysis and dynamic behavioral response.*
