## Overview

A Python-based command-line interface (CLI) tool that integrates with the VirusTotal API to scan and retrieve malware analysis results for common indicators of compromise (IOCs).

The tool supports scanning:

- URLs
- File uploads
- Domains
- IP addresses

It focuses on securely handling API credentials, normalizing responses from multiple third-party detection engines, and presenting results in a consistent, machine- and human-readable format.

The application can be run locally or containerized with Docker for reproducible, dependency-free execution.

---

## Features

- Python CLI for interacting with the VirusTotal API
- Supports multiple VirusTotal scan endpoints
- Secure API key management via environment variables or runtime flags
- Aggregates and normalizes scan results across multiple detection engines
- Dockerized for portable execution across environments

---

## Requirements

- Python 3.x
- A VirusTotal API key (free tier supported)

---

## Setup

### Clone the Repository

Clone the repository and navigate into the project directory.

### Configure the API Key

Create a `.env` file in the project root and add your VirusTotal API key:

`API_KEY=your_api_key_here`

The application uses `python-dotenv` to automatically load environment variables at runtime.

---

## Running the Script (Local)

After activating your virtual environment and installing dependencies, run the script directly:

`python src/main.py -u http://www.virustotal.com`

If no API_KEY is defined in .env, you may provide one at runtime using the -k flag:

`python src/main.py -k your-api-key -u http://www.virustotal.com`

### Help

To view all available options and supported scan types:

`python src/main.py -h`

---

## Running with Docker

### Build the Image

`docker build -t vt-cli`

### Run the Container

Provide the API key as an environment variable:

`docker run --rm -e API_KEY="your-api-key" vt-cli -u http://www.virustotal.com`

If the API key is already defined in .env at build time, rebuild the image and run:

`docker run --rm vt-cli -u http://www.virustotal.com`

---

## Notes

- Malware analysis is performed by third-party detection engines supported by VirusTotal.
- This tool retrieves and aggregates results but does not perform independent malware analysis.
- Designed for educational and research purposes only.
- Users are responsible for complying with VirusTotal’s terms of service and API usage limits.
