# Monitoring Scripts

This folder contains all backend monitoring and automation scripts used in the Server Performance and Resource Monitoring project.

These scripts run on a Raspberry Pi Linux server using cron jobs for continuous system monitoring and automation.

---

# Scripts Overview

| Script | Description |
|---|---|
| `collect.py` | Collects CPU, RAM, and Disk usage metrics every minute |
| `alert.py` | Checks resource thresholds and generates alerts |
| `load_to_db.py` | Loads CSV monitoring data into SQLite database |
| `check_health.sh` | Bash-based system health monitoring script |

---

# Script Details

## collect.py

### Purpose
Collects:
- CPU usage %
- RAM usage %
- Disk usage %
- Timestamp

The script appends monitoring data into:

```text
data/metrics.csv
```

### Frequency
Runs every 60 seconds using cron.

### Libraries Used

```python
psutil
csv
datetime
```

---

## alert.py

### Purpose

Checks latest system metrics and generates warnings when:

| Resource | Threshold |
|---|---|
| CPU Usage | > 85% |
| RAM Usage | > 80% |
| Disk Usage | > 90% |

### Output

Alerts are logged into:

```text
alerts.log
```

---

## load_to_db.py

### Purpose

Loads monitoring data from CSV into SQLite database.

### Database

```text
data/metrics.db
```

### Libraries Used

```python
pandas
sqlite3
sqlalchemy
```

### Frequency

Runs hourly using cron jobs.

---

## check_health.sh

### Purpose

Linux Bash-based monitoring script using native Linux commands.

### Commands Used

```bash
top
free
df
```

Used as an additional lightweight monitoring mechanism.

---

# Automation Using Cron

Example cron configuration:

```bash
* * * * * python3 collect.py
*/5 * * * * python3 alert.py
0 * * * * python3 load_to_db.py
```

---

# Monitoring Workflow

```text
collect.py
    ↓
metrics.csv
    ↓
load_to_db.py
    ↓
metrics.db
    ↓
Analytics & Dashboard
```

---

# Notes

- All scripts are designed for Linux environments.
- Developed and tested on Raspberry Pi OS.
- Automation is handled entirely using cron jobs.
- Monitoring data continuously grows over time for analytics.

---

# Developed By

- Sai Surendra Munagala
- Shaik Seema Kousar
