# 🛡️ NetSentinel

### Hybrid Network Intrusion Detection System (NIDS)

<p align="center">
  <img src="https://img.shields.io/badge/Python-3.x-blue?style=for-the-badge&logo=python&logoColor=white" alt="Python">
  <img src="https://img.shields.io/badge/Machine%20Learning-Enabled-success?style=for-the-badge&logo=scikitlearn&logoColor=white" alt="Machine Learning">
  <img src="https://img.shields.io/badge/Status-In%20Development-yellow?style=for-the-badge" alt="Status">
  <img src="https://img.shields.io/badge/License-Educational-orange?style=for-the-badge" alt="License">
</p>

<p align="center">
  <b>A defensive cybersecurity application that monitors authorized network traffic, analyzes network flows, detects suspicious activity, and generates security alerts.</b>
</p>

<p align="center">
  Packet Analysis · Rule-Based Detection · Machine Learning · Anomaly Detection · Web Dashboard
</p>

---

> [!WARNING]
> **Educational and Defensive Use Only**
>
> NetSentinel is intended for monitoring networks and systems that you own or have explicit authorization to monitor. Unauthorized use is strictly prohibited.

---

## 📌 Overview

Traditional network monitoring can generate large amounts of traffic data that are difficult to analyze manually.

**NetSentinel** aims to automate this process by combining network packet analysis, flow generation, rule-based detection, machine learning, anomaly detection, alert management, and a web dashboard into a single modular system.

### 🎯 Objectives

NetSentinel aims to:

* Capture authorized network traffic
* Convert packets into network-flow records
* Extract meaningful network features
* Detect suspicious network behavior
* Implement rule-based detection
* Implement machine-learning-based detection
* Experiment with anomaly detection
* Store network events and security alerts
* Provide a web-based security dashboard
* Evaluate detection performance using cybersecurity-relevant metrics
* Provide a modular foundation for future research and development

---

## 🏗️ System Architecture

```text
                        NETWORK TRAFFIC
                              │
                              ▼
                    ┌───────────────────┐
                    │   Packet Capture  │
                    │      Scapy        │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │   Flow Generator  │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │ Feature Extraction│
                    └─────────┬─────────┘
                              │
                    ┌─────────┴─────────┐
                    │                   │
                    ▼                   ▼
             ┌─────────────┐     ┌─────────────┐
             │ Rule Engine │     │  ML Engine   │
             │  Detection  │     │ Prediction   │
             └──────┬──────┘     └──────┬──────┘
                    │                   │
                    └─────────┬─────────┘
                              ▼
                    ┌───────────────────┐
                    │   Alert Engine    │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │      SQLite       │
                    │     Database      │
                    └─────────┬─────────┘
                              │
                              ▼
                    ┌───────────────────┐
                    │   Web Dashboard   │
                    └───────────────────┘
```

---

## ✨ Key Features

### 📡 Network Traffic Capture

NetSentinel captures authorized network traffic and extracts information such as:

* Source IP address
* Destination IP address
* Source port
* Destination port
* Protocol
* Packet size
* Timestamp
* TCP flags

### 🔄 Flow Generation

Instead of analyzing every packet independently, NetSentinel aggregates packets into meaningful network flows.

Example:

| Field            | Example        |
| ---------------- | -------------- |
| Source IP        | `192.168.1.20` |
| Destination IP   | `192.168.1.10` |
| Protocol         | `TCP`          |
| Destination Port | `443`          |
| Duration         | `3.42 seconds` |
| Packets          | `147`          |
| Bytes            | `82,451`       |

Flow-based analysis provides a more useful representation for machine-learning models and network-behavior analysis.

### 🧩 Feature Extraction

Potential network-flow features include:

* Flow duration
* Packet count
* Byte count
* Average packet size
* Packets per second
* Bytes per second
* Source port
* Destination port
* Protocol
* Connection frequency
* Number of unique destination ports

### 🚨 Rule-Based Detection

Configurable rules can be used to detect known suspicious patterns.

Potential detections include:

* Port scanning
* Abnormally high connection rates
* Repeated connection attempts
* Suspicious traffic patterns

Example port-scan pattern:

```text
                 Source IP
                     │
       ┌─────────────┼─────────────┐
       │             │             │
       ▼             ▼             ▼
    Port 21       Port 22       Port 23
       │             │             │
       └─────────────┼─────────────┘
                     │
                     ▼
              Possible Port Scan
```

### 🤖 Machine Learning Detection

Machine-learning models can classify network flows as benign or suspicious.

Initial models may include:

* Logistic Regression
* Decision Tree
* Random Forest

Additional algorithms may be evaluated as the project develops.

### 📊 Anomaly Detection

NetSentinel can explore anomaly detection techniques to identify traffic that significantly differs from established normal behavior.

The objective is to identify potentially suspicious behavior even when a specific attack signature is unavailable.

### 🔔 Alert System

Detected events are converted into security alerts.

Example:

```text
┌──────────────────────────────────────────┐
│              SECURITY ALERT              │
├──────────────────────────────────────────┤
│ Timestamp:       2026-09-22 14:32        │
│ Source IP:       192.168.1.20            │
│ Destination IP:  192.168.1.10            │
│ Detection:       Possible Port Scan      │
│ Severity:        HIGH                    │
│ Confidence:      94%                     │
└──────────────────────────────────────────┘
```

### 🖥️ Web Dashboard

The planned dashboard will provide an overview of network activity, detected threats, and security alerts.

```text
================================================
                  NETSENTINEL
================================================

Network Status       MONITORING
Total Flows          15,231
Benign Flows         14,782
Suspicious Flows        337
Detected Attacks        112

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

## 🧰 Technology Stack

| Area             | Technology                      |
| ---------------- | ------------------------------- |
| Backend          | Python, FastAPI, Uvicorn        |
| Network Analysis | Scapy                           |
| Data Processing  | Pandas, NumPy                   |
| Machine Learning | Scikit-learn                    |
| Database         | SQLite, SQLAlchemy              |
| Frontend         | HTML, CSS, JavaScript, Chart.js |
| Testing          | Pytest                          |
| Development      | Git, GitHub, VS Code, Codex     |

---

## 🔍 Detection Architecture

NetSentinel uses a hybrid detection architecture that combines rule-based detection with machine-learning-based detection.

```text
                    Network Flow
                         │
                         ▼
                 Feature Extraction
                         │
              ┌──────────┴──────────┐
              │                     │
              ▼                     ▼
       ┌─────────────┐       ┌─────────────┐
       │ Rule Engine │       │  ML Engine  │
       │  Detection  │       │ Prediction  │
       └──────┬──────┘       └──────┬──────┘
              │                     │
              └──────────┬──────────┘
                         ▼
                  ┌──────────────┐
                  │ Alert Engine │
                  └──────┬───────┘
                         │
                         ▼
                  ┌──────────────┐
                  │   Database   │
                  └──────┬───────┘
                         │
                         ▼
                  ┌──────────────┐
                  │  Dashboard   │
                  └──────────────┘
```

This architecture allows explicit rules to detect known patterns while machine-learning models can identify patterns learned from training data.

---

## 🤖 Machine Learning Pipeline

The planned machine-learning pipeline will use network intrusion datasets such as **UNSW-NB15** for experimentation.

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
Live Network Traffic
   │
   ▼
Prediction
```

### Evaluation Metrics

Models can be evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion matrix
* False-positive rate
* False-negative rate

> **Accuracy alone will not be used as the sole measure of system performance.**

---

## 📁 Project Structure

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

## ⚙️ Installation

> **Note:** Installation instructions will be updated as the project develops.

### Requirements

Recommended:

* Python 3.12+
* Git
* Operating system with appropriate permissions for packet capture

### 1. Clone the Repository

```bash
git clone https://github.com/YOUR_USERNAME/netsentinel.git
cd netsentinel
```

### 2. Create a Virtual Environment

**Windows:**

```powershell
python -m venv .venv
.venv\Scripts\activate
```

**Linux/macOS:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install Dependencies

```bash
pip install -e .
```

### 4. Run Tests

```bash
pytest
```

---

## ▶️ Usage

The exact commands will evolve as the application is implemented.

### Planned Workflow

```text
1. Start NetSentinel
        │
        ▼
2. Select authorized network interface
        │
        ▼
3. Capture traffic
        │
        ▼
4. Generate flows
        │
        ▼
5. Extract features
        │
        ▼
6. Run rule-based detection
        │
        ▼
7. Run ML detection
        │
        ▼
8. Generate alerts
        │
        ▼
9. Store results
        │
        ▼
10. View dashboard
```

---

## 🗺️ Development Roadmap

### Phase 1 — Project Foundation

* [ ] Create GitHub repository
* [ ] Create Python project structure
* [ ] Configure dependencies
* [ ] Configure testing
* [ ] Configure linting
* [ ] Create application entry point
* [ ] Create documentation structure

### Phase 2 — Packet Capture

* [ ] Implement Scapy packet capture
* [ ] Parse IPv4 packets
* [ ] Parse TCP/UDP information
* [ ] Extract packet metadata
* [ ] Add packet parsing tests
* [ ] Add capture CLI

### Phase 3 — Flow Generation

* [ ] Implement flow identification
* [ ] Aggregate packets
* [ ] Calculate flow duration
* [ ] Calculate packet counts
* [ ] Calculate byte counts
* [ ] Calculate traffic rates
* [ ] Add flow tests

### Phase 4 — Feature Engineering

* [ ] Build feature extraction pipeline
* [ ] Handle categorical features
* [ ] Handle missing values
* [ ] Normalize/scale appropriate features
* [ ] Document feature definitions

### Phase 5 — Rule-Based Detection

* [ ] Port scan detection
* [ ] High connection-rate detection
* [ ] Repeated connection detection
* [ ] Configurable detection thresholds
* [ ] Severity classification
* [ ] Alert generation

### Phase 6 — Machine Learning

* [ ] Dataset preparation
* [ ] Data cleaning
* [ ] Feature selection
* [ ] Train baseline models
* [ ] Train Random Forest
* [ ] Evaluate models
* [ ] Generate confusion matrices
* [ ] Save trained model

### Phase 7 — Real-Time ML Detection

* [ ] Load trained model
* [ ] Transform live flows
* [ ] Generate predictions
* [ ] Generate confidence scores
* [ ] Integrate ML predictions with alert engine

### Phase 8 — Database

* [ ] Create database schema
* [ ] Store flows
* [ ] Store alerts
* [ ] Store detection results
* [ ] Implement database queries

### Phase 9 — API

* [ ] Create FastAPI application
* [ ] Create alert endpoints
* [ ] Create traffic endpoints
* [ ] Create statistics endpoints
* [ ] Add API documentation

### Phase 10 — Dashboard

* [ ] Dashboard layout
* [ ] Traffic statistics
* [ ] Alert table
* [ ] Attack-type visualization
* [ ] Source-IP visualization
* [ ] Historical event view

### Phase 11 — Testing & Evaluation

* [ ] Unit tests
* [ ] Integration tests
* [ ] Detection testing
* [ ] ML evaluation
* [ ] Performance testing
* [ ] False-positive analysis
* [ ] False-negative analysis

### Phase 12 — Documentation

* [ ] Architecture documentation
* [ ] Installation guide
* [ ] User guide
* [ ] API documentation
* [ ] Detection methodology
* [ ] ML methodology
* [ ] Testing methodology
* [ ] Limitations
* [ ] Future work

---

## 🧪 Testing Strategy

Testing will be performed at multiple levels.

### Unit Testing

Individual components will be tested independently:

* Packet Parser
* Flow Generator
* Feature Extractor
* Detection Rules
* ML Preprocessing
* Database Operations

### Integration Testing

Components will be tested together:

```text
Packet
  │
  ▼
Flow
  │
  ▼
Features
  │
  ▼
Detection
  │
  ▼
Alert
  │
  ▼
Database
```

### ML Evaluation

Models will be evaluated using a separate test set.

Evaluation will include:

* Confusion matrix
* Precision
* Recall
* F1-score
* False-positive rate
* False-negative rate

---

## 🧪 Laboratory Environment

A controlled virtual environment can be used for development and testing.

```text
                    HOST COMPUTER
                         │
                         ▼
                 HOST-ONLY NETWORK
                         │
                 ┌───────┴───────┐
                 │               │
                 ▼               ▼
            Kali Linux       Test Machine
                 │               │
                 └───────┬───────┘
                         │
                         ▼
                    NetSentinel
```

A controlled laboratory environment allows traffic-generation and detection experiments without monitoring unrelated networks.

Recommended testing environments include:

* Personal systems
* Isolated virtual machines
* Laboratory networks
* Networks where explicit authorization has been provided

---

## 🔐 Security & Ethical Considerations

NetSentinel is designed for defensive cybersecurity research and authorized network monitoring.

Users should only capture or analyze network traffic when they have appropriate authorization.

The project does **not** aim to provide:

* Credential theft
* Malware deployment
* Persistence mechanisms
* Unauthorized exploitation
* Evasion mechanisms
* Unauthorized network access

---

## ⚠️ Limitations

NetSentinel is an educational and research project and should not initially be considered a replacement for production-grade intrusion detection systems.

Potential limitations include:

* Limited attack coverage
* Dataset bias
* False positives
* False negatives
* Model generalization problems
* Encrypted traffic limitations
* Resource consumption during high traffic volumes
* Dependence on selected network features
* Potential concept drift in real-world networks

These limitations will be documented and evaluated as development progresses.

---

## 🔮 Future Improvements

Potential future work includes:

* Advanced anomaly detection
* Deep-learning models
* Online learning
* Explainable AI
* Threat-intelligence integration
* IPv6 support
* Distributed sensors
* Container deployment
* Role-based access control
* Real-time notifications
* Model drift detection
* Automated model retraining
* Integration with external SIEM platforms

---

## 🎓 Project Goals

The final goal is to create a working defensive cybersecurity platform that demonstrates practical knowledge across multiple areas:

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

## 🤝 Contributing

Contributions are welcome.

1. Fork the repository.
2. Create a feature branch:

```bash
git checkout -b feature/amazing-feature
```

3. Commit your changes:

```bash
git commit -m "Add amazing feature"
```

4. Push the branch:

```bash
git push origin feature/amazing-feature
```

5. Open a Pull Request.

---

## 📄 License

This project is intended for educational and defensive cybersecurity research.

License information will be added as the project matures.

---

## ⚠️ Disclaimer

NetSentinel must only be used on systems and networks for which the user has explicit authorization to monitor or analyze traffic.

The developers are not responsible for unauthorized use of this software.

---

<p align="center">
  <b>🛡️ Built for defenders, by defenders.</b>
  <br>
  If you find this project useful, consider ⭐ starring the repository.
</p>
