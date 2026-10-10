# URL Safety Checker

A lightweight and extensible tool designed to inspect, analyze, and detect potentially malicious links, phishing sites, malware distributors, and suspicious redirects before you visit them.

---

## Features

- **Phishing & Malware Detection:** Integrates with threat intelligence feeds and lookup APIs (e.g., Google Safe Browsing, VirusTotal).
- **Domain Reputation & Age Analysis:** Evaluates domain registration details (WHOIS) to spot suspicious new domains commonly used in spoofing attacks.
- **SSL/TLS Certificate Inspection:** Verifies certificate validity, issuer trust, and expiry dates.
- **Redirect Tracing:** Follows URL shorteners and HTTP redirects to uncover the final landing destination.
- **Heuristic Pattern Matching:** Detects homograph/typosquatting attacks, suspicious top-level domains (TLDs), and high-entropy URLs.
- **API & CLI Support:** Run standalone via the command line or integrate it as a microservice in your stack.

---

## Tech Stack

- **Core Engine:** Python 3.9+ (or Node.js / Go)
- **Networking:** Requests / HTTPX
- **Integrations:** Google Safe Browsing API, VirusTotal API, WHOIS
- **Reporting:** JSON export & CLI color-coded reports

---

## Getting Started

### Prerequisites

- Python 3.9 or higher
- An API key for your preferred safety service (e.g., Google Safe Browsing, VirusTotal)

### Installation

1. **Clone the repository:**
   ```bash
   git clone https://github.com/your-username/url-safety-checker.git
   cd url-safety-checker
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure Environment Variables:**
   Copy the `.env.example` file and add your API keys:
   ```bash
   cp .env.example .env
   ```
   Edit `.env`:
   ```env
   SAFE_BROWSING_API_KEY=your_google_safe_browsing_key_here
   VIRUSTOTAL_API_KEY=your_virustotal_key_here
   ```

---

## Usage

### Command Line Interface

Scan a single link:
```bash
python checker.py --url "https://suspicious-link.example.com"
```

Trace full redirect chain:
```bash
python checker.py --url "https://bit.ly/sample-short-link" --trace-redirects
```

Batch scan from a file and save JSON report:
```bash
python checker.py --input-file links.txt --output report.json
```

---

## Risk Assessment Breakdown

| Score / Status | Threat Level | Meaning |
| :--- | :--- | :--- |
| **SAFE** | Low | Valid SSL, aged domain, no blacklist matches. |
| **SUSPICIOUS** | Moderate | Newly registered domain, shortener hiding target, or unverified SSL. |
| **MALICIOUS** | High | Confirmed match in threat feeds (phishing, malware, scam). |

---

## Project Structure

```text
├── checker/
│   ├── analyzers/        # Heuristic and regex checks
│   ├── apis/             # Safe Browsing & VirusTotal integrations
│   ├── redirect_tracer.py# Follows shorteners & 3xx jumps
│   └── ssl_inspector.py  # TLS/SSL verification
├── tests/                # Unit & integration tests
├── .env.example          # Sample environment variables
├── checker.py            # Main CLI entry point
├── requirements.txt      # Project dependencies
└── README.md
```

---

## Contributing

Contributions are welcome! Please open an issue or submit a pull request if you want to add new threat feed integrations, improve heuristic checks, or add a frontend/browser extension.

---

## License

This project is licensed under the [MIT License](LICENSE).