🛡️ Log Analyzer for Intrusion Detection (LAID)
Overview
The Log Analyzer for Intrusion Detection (LAID) is a robust, Python-based security tool designed to monitor and analyze high-volume server log files (Apache Access/Error and SSH Authentication logs) for suspicious patterns indicative of cyber attacks. The system employs structured data analysis, rule-based detection, and data visualization to provide actionable security intelligence.

It supports both a Command Line Interface (CLI) for automated processing and a Graphical User Interface (GUI) for interactive analysis and threshold configuration.

🚀 Key Features
Multi-Log Parsing: Structured parsing of both Apache (Common Log Format) and SSH log files using advanced regular expressions for accurate data extraction.

Threat Detection: Rule-based algorithms designed to flag three critical intrusion attempts:

Brute-Force Attacks: High volume of failed login attempts (401 status codes or SSH failed passwords).

Web Scanning: Aggressive probing for vulnerable paths or files (/etc/passwd, /phpmyadmin, etc.).

Denial-of-Service (DoS): Detection of an abnormally high number of requests from a single IP within a short time window.

Threat Intelligence Integration: Cross-references all detected suspicious source IP addresses against a user-maintained, local IP Blacklist file.

Interactive GUI: A Tkinter graphical interface allows users to:

Load files easily.

Dynamically set detection thresholds (e.g., Brute Force attempt count, DoS time window/request count).

View real-time, categorized incident tables.

Data Visualization: Automatically generates analytical charts using Matplotlib to visualize access patterns:

Top 20 Offending IP Addresses by Request Count.

Hourly Access Patterns to identify unusual temporal activity.

Incident Reporting: Exports a detailed, time-stamped text report (reports/incident_report_*.txt) summarizing all flagged incidents, including blacklisting status.

🛠️ Technology Stack & Libraries
Category

Tools & Libraries

Description

Core Language

Python 3.x

Primary development language.

Data Processing

Pandas

Used for creating, manipulating, and querying structured log data (DataFrames) for efficient analysis.

Log Parsing

re (Regex)

Essential for accurately extracting structured data fields from raw, unstructured log lines.

Visualization

Matplotlib

Generates high-quality charts for graphical analysis of security trends.

GUI

Tkinter

Python's standard library used to build the responsive and user-friendly desktop application.

CLI

argparse

Handles robust command-line argument parsing for headless operation.

⚙️ Installation and Setup
Prerequisites
You must have Python 3.x installed on your system.

1. Clone the Repository
git clone [YOUR_REPO_LINK]
cd log-analyzer-intrusion-detection

2. Install Dependencies
Install the required Python packages using pip:

pip install pandas matplotlib

3. Project Structure
Ensure your project directory includes the necessary folders:

.
├── log_analyzer/           # Core detection logic modules
├── logs/                   # (Place your apache/ssh log files here)
├── data/                   # Must contain ip_blacklist.txt
├── reports/                # Output location for incident reports
├── visualisations/         # Output location for Matplotlib charts
├── main.py                 # CLI entry point
└── gui.py                  # GUI launch script

Note: The data/ip_blacklist.txt file must exist (even if empty) for the blacklist check to run without error.

🏃 Usage
Option 1: Launch Graphical Interface (Recommended)
Run the GUI to interactively select files and adjust detection sensitivity.

python main.py --gui
