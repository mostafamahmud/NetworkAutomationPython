# Intelligent Network Automation System (Python & NetDevOps) 🚀

A comprehensive, modular Python-based Network Automation framework designed to streamline network operations, automate configuration deployments, perform compliance audits, and ensure high availability across multi-vendor network devices.

---

## 📌 Problem Statement
Manual network administration via CLI is slow, repetitive, and highly susceptible to human error. This project provides an interactive, multi-threaded automation suite that handles configuration backups, bulk deployments, pre/post-change validation, and automated failure alerting—reducing operational overhead and minimizing network downtime.

---

## ✨ Key Features & Modules

* **🖥️ Interactive CLI Management Menu (`interactive-cli_menu.py`):** A user-friendly terminal interface to trigger IPAM checks, backups, deployments, compliance audits, and device fact gathering from one central hub.
* **⚡ Multi-Threaded Execution (`multi_threading.py`):** Uses Python's `concurrent.futures.ThreadPoolExecutor` to run backups and configuration pushes across multiple devices simultaneously.
* **💾 Automated Timestamped Backups (`backup_running.py`, `netmiko.py`):** Connects via SSH using **Netmiko** to fetch running configurations and saves them locally with precise timestamps (`YYYY-MM-DD_HH-MM-SS`).
* **🧪 Dry-Run & Diff Reporting (`Dry-RUN.py`):** Simulates configuration changes safely before production deployment and uses `difflib` to generate pre-change vs. post-change comparison reports.
* **📋 Compliance Auditing & JSON Reporting (`jison_reporting.py`):** Audits network devices against expected configuration baselines and exports structured compliance reports in `JSON` format.
* **🌐 Multi-Vendor Device Facts (`NAPALM.py`):** Leverages **NAPALM** drivers to retrieve standardized device information (uptime, vendor, model, OS version, hostname).
* **🚨 Logging & Real-Time Failure Alerts (`logging_failure_alerts.py`):** Tracks all execution events in `network_automation.log` and triggers instant **Slack/Webhook** notifications upon connection or authentication failures.

---

## 🛠️ Technologies & Libraries Used

* **Language:** Python 3.x
* **Network Automation:** `Netmiko`, `NAPALM`
* **Concurrency & System:** `concurrent.futures` (Multi-threading), `logging`, `datetime`
* **Data & Validation:** `difflib`, `json`, `requests`

---

## 📂 Project Structure

```text
├── interactive-cli_menu.py     # Main interactive CLI dashboard
├── netmiko.py                  # Core SSH connection & exception handling
├── backup_running.py           # Automated running-config backup logic
├── deploy_config.py            # Bulk parallel configuration deployment
├── multi_threading.py          # Parallel execution engine (ThreadPoolExecutor)
├── Dry-RUN.py                  # Pre-deployment staging & state diff checker
├── jison_reporting.py          # Network compliance audit & JSON exporter
├── NAPALM.py                   # Multi-vendor device facts collector
├── logging_failure_alerts.py   # Event logging & Slack failure alerting
└── requirements.txt            # Project dependencies
```

---

## ⚙️ Installation & Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com
   cd my_project
   ```

2. **Create and activate a virtual environment:**
   ```bash
   python3 -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install the required libraries:**
   ```bash
   pip install netmiko napalm requests
   ```

---

## 🚀 Usage

1. Update the target device inventory (`devices_list`) with your network device IPs, device types, and credentials.
2. Launch the interactive management menu:
   ```bash
   python3 interactive-cli_menu.py
   ```
3. Choose the desired operation (1–6) from the on-screen menu:
   ```text
   =============================================
         نظام إدارة وأتمتة الشبكات الذكي      
   =============================================
   1. عرض وفحص الشبكة الفرعية (IPAM)
   2. جلب وحفظ النسخ الاحتياطية للأجهزة بالتوازي
   3. نشر الإعدادات والتحديثات الجماعية بالتوازي
   4. إجراء تدقيق ومطابقة المعايير (Compliance Check)
   5. جلب بيانات الأجهزة عبر NAPALM
   6. الخروج من البرنامج
   =============================================
   ```

---

## 📊 Sample Outputs

* **Backup Files:** `backup_192.168.1.50_2026-11-13_08-45-00.txt`
* **Compliance Audit (`network_compliance_report.json`):**
  ```json
  [
      {
          "host": "192.168.1.50",
          "expected_setting": "interface GigabitEthernet0/0",
          "status": "Compliant",
          "checked_at": "2026-11-13 08:45:10"
      }
  ]
  ```
* **Execution Logs (`network_automation.log`):** Records connection status, successful backups, and error tracebacks.

---

## 🔒 Security Best Practices
> **Note:** The current scripts include mock/lab credentials for demonstration and testing purposes. Before deploying in a production environment, replace hardcoded credentials with environment variables (`.env`) or a secure vault.

---

## 👤 Author
* **Mostafa Mahmud**
* **GitHub:** [@mostafamahmud](https://github.com)
* **LinkedIn:** [Add Your LinkedIn Profile URL]
