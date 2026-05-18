# 📌 Project Overview
Server Pulse Lite is a real-time system performance monitoring dashboard built using Power BI. It tracks and visualizes key server metrics such as CPU usage, RAM usage, and Disk usage over time — helping identify performance bottlenecks and critical resource spikes.


🎯 Key Metrics (KPI Cards)
MetricDescriptionAvg CPU %Average CPU utilization across all readingsMax Disk %Maximum disk usage percentage recordedHigh CPU CountNumber of times CPU crossed critical thresholdTotal ReadingsTotal number of data records collected.


📈 Visualizations
1. 📋 Data Table
Displays raw readings of RAM %, Disk %, CPU % per day for detailed inspection.
2. 📈 Line Chart — CPU, RAM & Disk % Over Time
Tracks the trend of all three system resources from May 15 to May 18, helping identify usage patterns and spikes.
3. 📈 Line Chart — Sum of CPU % by Date
Shows the cumulative CPU usage trend over time — useful for identifying days with unusually high CPU load.
4. 📊 Bar Chart — High CPU Count by Day
Displays the number of critical CPU spikes per day — helps pinpoint problematic days quickly.


🛠️ Tools & Technologies

1. Power BI Desktop - Dashboard creation & visualization
2.Microsoft Excel - Data cleaning & preprocessing
3. Python (optional) - Data collection from server
4. GitHub - Version control & collaboration
5. CSV - Data storage format.


⚙️ DAX Measures Used

-- Average CPU %
Avg CPU % = AVERAGE(metrics[cpu_percent])

-- Max Disk %
Max Disk % = MAX(metrics[disk_percent])

-- High CPU Count (CPU > 80%)
High CPU Count = 
CALCULATE(
    COUNT(metrics[cpu_percent]),
    metrics[cpu_percent] > 80
)

-- Total Readings
Total Readings = COUNT(metrics[timestamp])


📌 Key Insights


1.⚠️ RAM usage consistently high at 89–92% — server needs attention

2.🔴 CPU spikes occurred 14 times — investigate peak load times

3.✅ Disk usage stable at ~25% — no immediate disk pressure

4.📈 CPU trend increasing from May 15–17 — growing server demand
