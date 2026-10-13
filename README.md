# ARTEX V 2.0 - Automated Reconnaissance & Threat Exposure Analyzer

![Security](https://img.shields.io/badge/Security-Pentesting-blue)
![Python](https://img.shields.io/badge/Python-3.8%2B-green)
![Flask](https://img.shields.io/badge/Flask-2.3.2-lightgrey)

ARTEX is an advanced web application security analysis platform that automates reconnaissance, vulnerability scanning, vulnerability scanning, threat assessment and AI-powered security recommendations  for modern web applications and infrastructure.

<img width="545" height="402" alt="ChatGPT Image Jul 17, 2025, 10_28_41 AM" src="https://github.com/user-attachments/assets/3357002f-5aa7-41c6-bc7d-090c463a836f" />


## Key Features

- **Comprehensive Scanning**:
  - Subdomain enumeration
  - Port scanning with risk assessment
  - Comprehensive DNS scanning
  - Advanced SSL/TLS scanning & vulns discovering by versions
  - Technology stack fingerprinting
  - Authentication surface detection

- **Intelligent Analysis**:
  - AI-powered security recommendations (Groq/Llama3 integration)
  - Document assistant for custom tasks on PDF, DOCX, TXT, Markdown, CSV and JSON files
  - Dual-perspective reports (Owner vs Hunter views)
  - Automated risk scoring

- **Enterprise Ready**:
  - Parallel scanning engine
  - PDF/JSON report generation
  - REST API for integration

## Installation

### Prerequisites
- Python 3.8+
- Nmap (system installation)
- Redis (for job queueing - optional)

```bash
# Ubuntu/Debian
sudo apt-get install nmap wkhtmltopdf

# macOS
brew install nmap wkhtmltopdf
```

Setup
```bash

git clone https://github.com/yourrepo/artex.git
cd artex

# Create virtual environment (recommended)
python -m venv venv
source venv/bin/activate  # Linux/macOS
# venv\Scripts\activate  # Windows

pip install -r requirements.txt

```
Configuration

Create a Groq key at https://console.groq.com/keys, then copy `.env.example` to `.env` and replace the placeholder with your new key:

```bash
cp .env.example .env
# Edit .env and set GROQ_API_KEY to your key
python app.py
```

Restart the app after changing `.env`. If no key is set, document tasks stay disabled and security scans use rule-based analysis.

The **Documents** page accepts files up to 8 MB and 200,000 extracted characters, with task instructions up to 20,000 characters and responses up to 16,384 tokens. Responses use clean Markdown formatting. Extracted text is sent to Groq for processing and is not stored by ARTEX. Set the key before starting the app to enable document tasks.

Usage
Web Interface
```bash

python app.py

Access the interface at: http://localhost:5000
API Endpoints

    POST /start_scan - Initiate new scan

    GET /scan_status/<scan_id> - Check scan progress

    GET /results/<scan_id> - View results

    GET /export/<scan_id> - Export reports (PDF/JSON)
```

Scan Types
Scan Type	Description	Intensity Levels
Full Audit	Complete security assessment	Light/Normal/Aggressive
Web Focus	Application-layer only	Normal
Infrastructure	Network and server assessment	Aggressive
Quick Scan	Surface-level vulnerabilities	Light
Sample Report Output

Security Notice

This tool is for authorized security assessments only. Unauthorized use against systems you don't own or have permission to test is illegal.
