🛡️ NetSentinel
Hybrid Network Intrusion Detection System (NIDS)
NetSentinel is a defensive cybersecurity application designed to monitor authorized network traffic, analyze network flows, identify suspicious activity, and generate security alerts.
The project combines network packet analysis, rule-based detection, machine learning, anomaly detection, and a web dashboard into a single system.
> [!WARNING]
> **Educational and defensive use only.** NetSentinel is intended for monitoring networks and systems that you own or have explicit authorization to monitor.
---
📌 Overview
Traditional network monitoring can generate large amounts of traffic data that are difficult to analyze manually.
NetSentinel aims to automate this process:
```text
Network Traffic
      │
      ▼
┌─────────────────┐
│  Packet Capture │
│      Scapy      │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│  Flow Generator │
└────────┬────────┘
         │
         ▼
┌─────────────────┐
│ Feature         │
│ Extraction      │
└────────┬────────┘
         │
    ┌────┴────┐
    ▼         ▼
┌─────────┐ ┌─────────────┐
│  Rule   │ │ ML Detection│
│Detection│ │             │
└────┬────┘ └──────┬──────┘
     └──────┬──────┘
            ▼
    ┌─────────────┐
    │ Alert Engine│
    └──────┬──────┘
           ▼
      ┌──────────┐
      │  SQLite  │
      └────┬─────┘
           ▼
   ┌────────────────┐
   │ Web Dashboard  │
   └────────────────┘
```
---
🎯 Objectives
NetSentinel aims to:
Capture authorized network traffic
Convert packets into network-flow records
Extract meaningful network features
Detect suspicious network behavior
Implement rule-based detection
Implement machine-learning-based detection
Experiment with anomaly detection
Store network events and alerts
Provide a web-based security dashboard
Evaluate detection performance using cybersecurity-relevant metrics
Provide a modular foundation that can be extended in future research
---
✨ Key Features
📡 Network Traffic Capture
Capture authorized network traffic and extract:
Source IP address
Destination IP address
Source port
Destination port
Protocol
Packet size
Timestamp
TCP flags
🔄 Flow Generation
Instead of analyzing individual packets independently, NetSentinel aggregates packets into network flows.
Example flow:
Field	Example
Source IP	`192.168.1.20`
Destination IP	`192.168.1.10`
Protocol	`TCP`
Destination Port	`443`
Duration	`3.42 seconds`
Packets	`147`
Bytes	`82,451`
Flow-based analysis provides a more useful representation for machine-learning models.
🧩 Feature Extraction
Potential network-flow features include:
Flow duration
Packet count
Byte count
Average packet size
Packets per second
Bytes per second
Source port
Destination port
Protocol
Connection frequency
Number of unique destination ports
🚨 Rule-Based Detection
NetSentinel can detect known suspicious patterns using configurable rules.
Potential detections include:
Port scanning
Abnormally high connection rates
Repeated connection attempts
Suspicious traffic patterns
Example:
```text
Source IP
   │
   ├── Port 21
   ├── Port 22
   ├── Port 23
   ├── Port 25
   ├── Port 53
   ├── Port 80
   ├── Port 110
   └── ...
        │
        ▼
  Possible Port Scan
```
🤖 Machine Learning Detection
Machine-learning models can classify network flows as benign or suspicious.
Initial models may include:
Logistic Regression
Decision Tree
Random Forest
Future experiments may include additional algorithms where appropriate.
📊 Anomaly Detection
The project can explore detecting traffic that significantly differs from normal network behavior.
The goal is to identify potentially suspicious behavior even when a specific attack signature is not available.
🔔 Alert System
Detected events are converted into security alerts.
Example:
```text
┌──────────────────────────────────────┐
│              SECURITY ALERT          │
├──────────────────────────────────────┤
│ Timestamp:       2026-09-22 14:32    │
│ Source IP:       192.168.1.20        │
│ Destination IP:  192.168.1.10        │
│ Detection:       Possible Port Scan  │
│ Severity:        HIGH                 │
│ Confidence:      94%                  │
└──────────────────────────────────────┘
```
🖥️ Web Dashboard
The planned dashboard will provide an overview of network activity.
```text
================================================
                  NETSENTINEL
================================================

Network Status       MONITORING
Total Flows         15,231
Benign Flows        14,782
Suspicious Flows       337
Detected Attacks       112

------------------------------------------------
Recent Alerts

HIGH       Possible Port Scan
HIGH       DoS Pattern
MEDIUM     Anomalous Traffic
LOW        Suspicious Connection

------------------------------------------------
Top Source IPs

192.168.1.20        428 connections
192.168.1.31        312 connections
192.168.1.45        281 connections
================================================
```
---
🧰 Technology Stack
Area	Technologies
Backend	Python, FastAPI, Uvicorn
Network Analysis	Scapy
Data Processing	Pandas, NumPy
Machine Learning	Scikit-learn
Database	SQLite, SQLAlchemy
Frontend	HTML, CSS, JavaScript, Chart.js
Testing	Pytest
Development	Git, GitHub, VS Code, Codex
---
🏗️ Project Architecture
Planned project structure:
```text
NetSentinel/
│
├── app/
│   ├── __init__.py
│   │
│   ├── api/
│   │   ├── __init__.py
│   │   └── routes/
│   │
│   ├── capture/
│   │   ├── __init__.py
│   │   └── packet_capture.py
│   │
│   ├── flows/
│   │   ├── __init__.py
│   │   └── flow_generator.py
│   │
│   ├── features/
│   │   ├── __init__.py
│   │   └── extractor.py
│   │
│   ├── detection/
│   │   ├── __init__.py
│   │   ├── rules.py
│   │   └── alert_engine.py
│   │
│   ├── ml/
│   │   ├── __init__.py
│   │   ├── preprocessing.py
│   │   ├── training.py
│   │   ├── prediction.py
│   │   └── evaluation.py
│   │
│   ├── database/
│   │   ├── __init__.py
│   │   ├── models.py
│   │   └── database.py
│   │
│   ├── config/
│   │   ├── __init__.py
│   │   └── settings.py
│   │
│   └── main.py
│
├── tests/
│   ├── test_capture.py
│   ├── test_flows.py
│   ├── test_features.py
│   ├── test_detection.py
│   └── test_ml.py
│
├── data/
│   ├── raw/
│   └── processed/
│
├── models/
│
├── scripts/
│   ├── prepare_dataset.py
│   ├── train_model.py
│   └── evaluate_model.py
│
├── docs/
│
├── .gitignore
├── AGENTS.md
├── pyproject.toml
└── README.md
```
---
🔍 Detection Architecture
NetSentinel uses a hybrid detection architecture:
```text
             Network Flow
                   │
                   ▼
          Feature Extraction
                   │
            ┌──────┴──────┐
            ▼             ▼
      ┌──────────┐   ┌──────────┐
      │   Rule   │   │    ML    │
      │  Engine  │   │  Engine  │
      └────┬─────┘   └────┬─────┘
           └──────┬───────┘
                  ▼
           ┌─────────────┐
           │ Alert Engine│
           └──────┬──────┘
                  ▼
             ┌─────────┐
             │ Database│
             └────┬────┘
                  ▼
             ┌─────────┐
             │Dashboard│
             └─────────┘
```
This allows known patterns to be detected through explicit rules while machine learning can identify patterns learned from training data.
---
🤖 Machine Learning Pipeline
The planned machine-learning pipeline will use network intrusion datasets such as UNSW-NB15 for experimentation.
```text
Dataset
   │
   ▼
Data Cleaning
   │
   ▼
Feature Selection
   │
   ▼
Encoding
   │
   ▼
Train/Test Split
   │
   ▼
Model Training
   │
   ▼
Model Evaluation
   │
   ▼
Model Selection
   │
   ▼
Saved Model
   │
   ▼
Network Traffic
   │
   ▼
Prediction
```
Models can be compared using:
Accuracy
Precision
Recall
F1-score
Confusion matrix
False-positive rate
False-negative rate
> Accuracy alone will not be used as the sole measure of system performance.
---
🗺️ Development Roadmap
Phase 1 — Project Foundation
[ ] Create GitHub repository
[ ] Create Python project structure
[ ] Configure dependencies
[ ] Configure testing
[ ] Configure linting
[ ] Create application entry point
[ ] Create documentation structure
Phase 2 — Packet Capture
[ ] Implement Scapy packet capture
[ ] Parse IPv4 packets
[ ] Parse TCP/UDP information
[ ] Extract packet metadata
[ ] Add packet parsing tests
[ ] Add capture CLI
Phase 3 — Flow Generation
[ ] Implement flow identification
[ ] Aggregate packets
[ ] Calculate flow duration
[ ] Calculate packet counts
[ ] Calculate byte counts
[ ] Calculate traffic rates
[ ] Add flow tests
Phase 4 — Feature Engineering
[ ] Build feature extraction pipeline
[ ] Handle categorical features
[ ] Handle missing values
[ ] Normalize/scale appropriate features
[ ] Document feature definitions
Phase 5 — Rule-Based Detection
[ ] Port scan detection
[ ] High connection-rate detection
[ ] Repeated connection detection
[ ] Configurable detection thresholds
[ ] Severity classification
[ ] Alert generation
Phase 6 — Machine Learning
[ ] Dataset preparation
[ ] Data cleaning
[ ] Feature selection
[ ] Train baseline models
[ ] Train Random Forest
[ ] Evaluate models
[ ] Generate confusion matrices
[ ] Save trained model
Phase 7 — Real-Time ML Detection
[ ] Load trained model
[ ] Transform live flows
[ ] Generate predictions
[ ] Generate confidence scores
[ ] Integrate ML predictions with alert engine
Phase 8 — Database
[ ] Create database schema
[ ] Store flows
[ ] Store alerts
[ ] Store detection results
[ ] Implement database queries
Phase 9 — API
[ ] Create FastAPI application
[ ] Create alert endpoints
[ ] Create traffic endpoints
[ ] Create statistics endpoints
[ ] Add API documentation
Phase 10 — Dashboard
[ ] Dashboard layout
[ ] Traffic statistics
[ ] Alert table
[ ] Attack-type visualization
[ ] Source-IP visualization
[ ] Historical event view
Phase 11 — Testing & Evaluation
[ ] Unit tests
[ ] Integration tests
[ ] Detection testing
[ ] ML evaluation
[ ] Performance testing
[ ] False-positive analysis
[ ] False-negative analysis
Phase 12 — Documentation
[ ] Architecture documentation
[ ] Installation guide
[ ] User guide
[ ] API documentation
[ ] Detection methodology
[ ] ML methodology
[ ] Testing methodology
[ ] Limitations
[ ] Future work
---
⚙️ Installation
> Installation instructions will be updated as the project develops.
Requirements
Recommended:
Python 3.12+
Git
Clone the Repository
```bash
git clone https://github.com/YOUR_USERNAME/netsentinel.git
cd netsentinel
```
Create a Virtual Environment
Windows
```powershell
python -m venv .venv
.venv\Scripts\activate
```
Linux/macOS
```bash
python3 -m venv .venv
source .venv/bin/activate
```
Install Dependencies
```bash
pip install -e .
```
Run Tests
```bash
pytest
```
---
▶️ Usage
The exact commands will evolve as the application is implemented.
Planned workflow:
```text
1. Start NetSentinel
        ↓
2. Select authorized network interface
        ↓
3. Capture traffic
        ↓
4. Generate flows
        ↓
5. Extract features
        ↓
6. Run rule-based detection
        ↓
7. Run ML detection
        ↓
8. Generate alerts
        ↓
9. Store results
        ↓
10. View dashboard
```
---
🧪 Testing Strategy
Testing will be performed at multiple levels.
Unit Testing
Individual components will be tested independently:
Packet Parser
Flow Generator
Feature Extractor
Detection Rules
ML Preprocessing
Database Operations
Integration Testing
Components will be tested together:
```text
Packet
  ↓
Flow
  ↓
Features
  ↓
Detection
  ↓
Alert
  ↓
Database
```
ML Evaluation
Models will be evaluated using a separate test set.
Evaluation will include:
Confusion Matrix
Precision
Recall
F1-score
False Positive Rate
False Negative Rate
---
🔐 Security & Ethical Considerations
NetSentinel is designed for defensive cybersecurity research and authorized network monitoring.
Users should only capture or analyze network traffic when they have appropriate authorization.
The project does not aim to provide:
Credential theft
Malware deployment
Persistence mechanisms
Unauthorized exploitation
Evasion mechanisms
Unauthorized network access
Testing should be performed using:
Personal systems
Isolated virtual machines
Laboratory networks
Networks where explicit authorization has been provided
---
🧪 Laboratory Environment
A controlled virtual environment can be used for testing.
```text
             Host Computer
                  │
                  ▼
          Host-Only Network
                  │
          ┌───────┴────────┐
          ▼                ▼
     Kali Linux       Test Machine
          │                │
          └───────┬────────┘
                  ▼
             NetSentinel
```
The laboratory environment allows traffic-generation and detection experiments without monitoring unrelated networks.
---
⚠️ Limitations
NetSentinel is an educational and research project and should not initially be considered a replacement for production-grade intrusion detection systems.
Potential limitations include:
Limited attack coverage
Dataset bias
False positives
False negatives
Model generalization problems
Encrypted traffic limitations
Resource consumption during high traffic volumes
Dependence on selected network features
Potential concept drift in real-world networks
These limitations will be documented and evaluated as development progresses.
---
🔮 Future Improvements
Potential future work includes:
More advanced anomaly detection
Deep-learning models
Online learning
Explainable AI
Threat-intelligence integration
IPv6 support
Distributed sensors
Container deployment
Role-based access control
Real-time notifications
Model drift detection
Automated model retraining
Integration with external SIEM platforms
---
🎓 Project Goals
The final goal is to create a working defensive cybersecurity platform that demonstrates practical knowledge of:
```text
Networking
    +
Cybersecurity
    +
Python
    +
Machine Learning
    +
Data Analysis
    +
Backend Development
    +
Database Design
    +
Web Development
    +
Software Testing
```
---
📄 License
This project is intended for educational and defensive cybersecurity research.
License information will be added as the project matures.
---
⚠️ Disclaimer
NetSentinel must only be used on systems and networks for which the user has explicit authorization to monitor or analyze traffic.
The developers are not responsible for unauthorized use of this software.
