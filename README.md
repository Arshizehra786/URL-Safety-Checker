# URL-Safety-Checker
URL Safety Checker is a lightweight Python-based threat analysis tool designed to identify malicious, deceptive, and high-risk web links. By combining structural heuristic analysis—such as detecting embedded IP addresses, excessive subdomains, suspicious TLDs, and obfuscated tokens—with real-time reputation scoring.
URL Safety CheckerA lightweight and extensible tool designed to inspect, analyze, and detect potentially malicious links, phishing sites, malware distributors, and suspicious redirects before you visit them.FeaturesPhishing & Malware Detection: Integrates with threat intelligence feeds and lookup APIs (e.g., Google Safe Browsing, VirusTotal).Domain Reputation & Age Analysis: Evaluates domain registration details (WHOIS) to spot suspicious new domains commonly used in spoofing attacks.SSL/TLS Certificate Inspection: Verifies certificate validity, issuer trust, and expiry dates.Redirect Tracing: Follows URL shorteners and HTTP redirects to uncover the final landing destination.Heuristic Pattern Matching: Detects homograph/typosquatting attacks, suspicious top-level domains (TLDs), and high-entropy URLs.API & CLI Support: Run standalone via the command line or integrate it as a microservice in your stack.Tech StackCore Engine: Python 3.9+ (or Node.js / Go)Networking: Requests / HTTPXIntegrations: Google Safe Browsing API, VirusTotal API, WHOISReporting: JSON export & CLI color-coded reportsGetting StartedPrerequisitesPython 3.9 or higherAn API key for your preferred safety service (e.g., Google Safe Browsing, VirusTotal)InstallationClone the repository:git clone https://github.com/your-username/url-safety-checker.git
cd url-safety-checker
Install dependencies:pip install -r requirements.txt
Configure Environment Variables:
Copy the .env.example file and add your API keys:cp .env.example .env
Edit .env:SAFE_BROWSING_API_KEY=your_google_safe_browsing_key_here
VIRUSTOTAL_API_KEY=your_virustotal_key_here
UsageCommand Line InterfaceScan a single link:python checker.py --url "https://suspicious-link.example.com"
Trace full redirect chain:python checker.py --url "https://bit.ly/sample-short-link" --trace-redirects
Batch scan from a file and save JSON report:python checker.py --input-file links.txt --output report.json
Risk Assessment BreakdownScore / StatusThreat LevelMeaningSAFELowValid SSL, aged domain, no blacklist matches.SUSPICIOUSModerateNewly registered domain, shortener hiding target, or unverified SSL.MALICIOUSHighConfirmed match in threat feeds (phishing, malware, scam).Project Structure├── checker/
│   ├── analyzers/        # Heuristic and regex checks
│   ├── apis/             # Safe Browsing & VirusTotal integrations
│   ├── redirect_tracer.py# Follows shorteners & 3xx jumps
│   └── ssl_inspector.py  # TLS/SSL verification
├── tests/                # Unit & integration tests
├── .env.example          # Sample environment variables
├── checker.py            # Main CLI entry point
├── requirements.txt      # Project dependencies
└── README.md
ContributingContributions are welcome! Please open an issue or submit a pull request if you want to add new threat feed integrations, improve heuristic checks, or add a frontend/browser extension.LicenseThis project is licensed under the MIT License.
