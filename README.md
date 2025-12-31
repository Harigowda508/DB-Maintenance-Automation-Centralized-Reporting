DB Maintenance Automation & Centralized Reporting

A production-ready SQL Server DBA automation framework designed to collect, centralize, monitor,
and alert on database operations across multiple SQL Server instances using SQL Server, PowerShell, Batch scripts, and Scheduled Jobs.

This project demonstrates real-world DBA + DevOps practices, not demo scripts.
🧠 Key Objectives
Centralize DBA operational data into a single Reporting Server
Automate daily, weekly, and monthly health reports
Proactively alert failures via Email / Microsoft Teams
Reduce manual DBA effort
Provide auditable historical data for troubleshooting and capacity planning

🏗️ Architecture Overview
Source Servers (Prod / DR)
        │
        │  (Synonyms, Views, Stored Procedures)
        ▼
Central Reporting Server
        │
        ├── SQL Tables (Historical Data)
        ├── SQL Stored Procedures (Aggregation & Reports)
        ├── PowerShell Scripts (Automation & Alerts)
        └── Batch / Config Files

📁 Repository Structure (Actual)
🔹 ReportingServer
Centralized database used for reporting, alerts, and dashboards.
📂 Config_Files
File	Purpose
configurationformat.bat	Environment & execution configuration for automation
📂 Powershell_Scripts
Automates execution, data collection, reporting, and alerts.
Daily Operations
Backup Success / Failure Reports (Email & Teams)
Archival Job Success / Failure Alerts
Indexing Job Success / Failure Alerts
SQL Agent Job Failures
Disabled Jobs Alerts
Deadlock Reports
Long Running Sessions & Blocking Alerts
Log Shipping Success & Failure Alerts
Drive Space Monitoring
Database Growth Reports
Weekly / Monthly
Weekly Log Shipping Status
Monthly Login Details Audit

📌 Examples:
Daily_Backup_report_failed.ps1
Daily_Backup_report_success_Teams.ps1
Daily_LongRunningSessionAlert.ps1
Daily_Log_Shipping_Alert_teams.ps1
Database_Growth_report.ps1

📂 Stored_Procedures
Core SQL logic to insert, aggregate, and generate reports.
Key Categories
Backup, Archival, Indexing job statistics
SQL Agent job monitoring
Deadlock and blocking session tracking
Long-running session logging
Database & table growth analysis
TempDB usage monitoring
Log Shipping health checks
Paginated reporting procedures

📌 Examples:
dbo.p_GenerateBackupReport.StoredProcedure.sql
dbo.p_GetAllLongRunningSessions.StoredProcedure.sql
dbo.p_GetTableSizeDifference.StoredProcedure.sql
dbo.P_StoredGetAllBackupsReportPaginated.StoredProcedure.sql

📂 Tables

Stores historical and reporting data.
Major Data Areas
Backup & Archival reports
Job execution history
Deadlock & blocking logs
Long running sessions
Database & table growth metrics
Server performance statistics
Log Shipping alerts & success logs

📌 Examples:
dbo.t_DBADailybackupReport.Table.sql
dbo.t_DBAIndexingReport.Table.sql
dbo.t_BlockingSessions.Table.sql
dbo.t_ServerPerformance.Table.sql

📂 Synonyms

Used to query Source Servers securely without hardcoding connections.

📌 Examples:

Blocking Sessions
Deadlocks
IO Statistics
Server Performance
TempDB usage

🔹 SourceServer
Scripts deployed on Source SQL Servers (Production / DR).

📂 Master_DB
Server-level monitoring & admin scripts.
Includes

Blocking session capture
Deadlock reporting
Database growth tracking
TempDB usage
Orphaned user cleanup
Login migration scripts

📂 MSDB

SQL Agent job-level monitoring.
Includes

Daily backup, archival & indexing job inserts
Disabled job tracking
Instant job status views

📂 DR_MSDB
Log Shipping restore status monitoring on DR servers.

🔁 Execution Flow
Source Servers

Views & stored procedures collect live operational data
Synonyms expose data to Reporting Server
Reporting Server
Stored procedures aggregate & store data
PowerShell scripts execute procedures
Alerts sent via Email / Teams

Scheduling

SQL Agent Jobs / Windows Task Scheduler

🔐 Security & Best Practices

Read-only access via Synonyms
No direct cross-server table writes
Modular script structure
Fully schedulable & restart-safe
Production-tested naming conventions

🚀 Skills Demonstrated

SQL Server Administration (Production scale)
PowerShell Automation
Job Monitoring & Alerting
Performance & Capacity Planning
Centralized Reporting Architecture
DevOps-ready automation mindset

📌 Ideal For

SQL Server DBAs
SRE / Platform Engineers
DevOps Engineers transitioning from DBA
Enterprise monitoring implementations

🧑‍💻 Author

Harish M
Database Administrator → Cloud / DevOps Aspirant

📌 This repository represents real operational automation, not sample code.
