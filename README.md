# AI Threat Investigator
Agentic Security Detection and Investigation System

## Overview

Modern security systems generate large volumes of telemetry, making manual analysis slow, inconsistent, and difficult to scale.

This project implements an end-to-end AI-powered system that:
- Ingests system logs (process, command, user activity)
- Detects suspicious behavior using rules and machine learning
- Uses an LLM-based agent to investigate attack sequences
- Generates structured, actionable security reports aligned with MITRE ATT&CK

The system simulates how a security analyst detects and investigates threats, but in an automated and scalable manner.

---

## Problem Statement

Security analysts often need to:
- Filter noisy alerts
- Investigate isolated events
- Reconstruct attack chains manually

This leads to:
- Delayed response times
- Inconsistent analysis
- Limited scalability

This project addresses these challenges by combining detection and automated investigation.

---

## Solution

The system consists of three main layers:

### 1. Detection Layer
- Rule-based detection using security heuristics
- Anomaly detection using Isolation Forest
- Combined scoring to flag suspicious events

### 2. Agentic Investigation Layer
- Retrieves related events within a session
- Uses an LLM to analyze the full sequence
- Reconstructs attack chains
- Maps behavior to MITRE ATT&CK stages

### 3. Reporting Layer
- Generates structured investigation reports
- Includes risk level and confidence
- Provides actionable next steps

---

## Architecture

Logs → Detection → Flagged Events → Agent → Investigation Reports

---

## Example Attack Pattern

- External script download via curl  
- Execution via bash  
- Persistence via cron job  

Mapped to:
- Command and Control (T1105)
- Execution (T1059)
- Persistence (T1053)

---

## Key Features

- Hybrid detection using rules and ML
- Context-aware investigation using agentic reasoning
- MITRE ATT&CK alignment
- Explainability through detection signals
- Structured and actionable outputs

---

## Tech Stack

- Python  
- Pandas  
- NumPy  
- Scikit-learn  
- Groq LLM  

---

## Project Structure

ai-threat-investigator/
│
├── data/
│   └── logs.csv
│
├── outputs/
│   └── reports.json
│
├── main.py
├── requirements.txt
└── README.md

---

## How to Run

### 1. Clone the repository

git clone https://github.com/YOUR_USERNAME/ai-threat-investigator.git  
cd ai-threat-investigator

---

### 2. Install dependencies

pip install -r requirements.txt

---

### 3. Set Groq API Key

Mac/Linux:
export GROQ_API_KEY=your_api_key

Windows:
set GROQ_API_KEY=your_api_key

---

### 4. Prepare input data

Ensure the following file exists:

data/logs.csv

---

### 5. Run the pipeline

python main.py

---

## Output

After running the script, reports will be generated at:

outputs/reports.json

Each report contains:
- Summary of events
- Attack pattern identification
- Attack chain explanation
- MITRE ATT&CK mapping
- Detection signals
- Risk level
- Confidence level
- Recommended actions

---

## Example Output (Simplified)

{
  "session_id": 2,
  "risk": "Critical",
  "confidence": "High",
  "attack_chain": [
    "Download malicious script",
    "Execute script",
    "Establish persistence via cron"
  ]
}

---

## Evaluation

The system evaluates detection performance using:
- Precision and recall
- False positives
- Qualitative validation of investigation outputs

---

## Limitations

- Uses synthetic or semi-structured logs
- Limited feature engineering for anomaly detection
- LLM output may vary depending on prompt and model

---

## Future Improvements

- Integration with real-world logs (auditd, Sysmon)
- Streaming pipeline for real-time detection
- Cross-session correlation
- Feedback loop for continuous learning
- UI dashboard for visualization

---

## About This Project

This project explores how AI and agentic systems can be applied to cybersecurity.

It demonstrates:
- End-to-end system design
- Applied machine learning for anomaly detection
- LLM-based reasoning for investigation
- Translation of analysis into actionable insights

The focus is on building systems that automate analyst workflows and scale threat detection.
