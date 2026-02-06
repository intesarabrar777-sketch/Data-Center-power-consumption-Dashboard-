# Data Center Power Consumption Dashboard

## Overview
This project presents a Power BI dashboard for analyzing data center power consumption, focusing on capacity utilization, efficiency, and backup readiness.This dashboard presents multiple data center locations across Bangladesh under the supervision of a single organization. It enables stakeholders to monitor overall power consumption, evaluate power efficiency and effectiveness, and identify areas requiring improvement. The insights derived from this dashboard support informed decision-making for future capacity expansion, power optimization, and effective utilization of resources.

## Key Metrics
- Sanction Load vs Running consumption load
- Load Utilization (%)
- Power Usage Effectiveness (PUE)
- Battery Backup Hours
- UPS, DG, and Rectifier Usage

## Tools & Technologies
- Power BI
- Microsoft Excel
- DAX
- Power Query

## Features
- Button-based slicer for data center selection
- Conditional formatting for risk indication
- Light and Dark theme support
- Management-friendly visualizations

## Dashboard Preview
![Dashboard](Screenshot/Dashboard%20sample%20screenshot.png)
## Dark Theme Dashboard Preview 
![Dashboard](Screenshot/Dark%20theme%20of%20consumption%20rate%20.png)

## Over capacity monitoring logic (DAX)
This dashboard includes DAX-based threshold logic to identify over-capacity or high-risk operating conditions for critical power infrastructure components (DG, UPS, Rectifier).
For example DG overload capacity monitoring included for a specific Data center such as Bogura DC 

## Dashboard Preview for over conumption of DG 
![Dashboard](Screenshot/Bogura%20Datacenter%20current%20power%20consumption.png)

### DG Capacity Utilization (%)


```DAX
DG Usage (%) =
DIVIDE(
    SUM('Power_Data'[DG Running Load]),
    SUM('Power_Data'[DG Rated Capacity]),
    0
)

```
# Conditional Risk Indicator Logic 
``` DAX 
DG Status Color =
IF(
    AVERAGE[DG Usage (%)] > 0.7,
    "#E74C3C",   -- Critical: Above 70% utilization
    "#2ECC71"    -- Normal operating range
)
```
This DAX operation will be used for prToper visualization of DG utilization 
≤ 70% → Safe operating range
> 70% → Capacity risk, monitoring required

In the gauge chart for the Bogra Data Center, DG utilization is shown to exceed 70%, which is clearly visualized for stakeholders through a red indicator. This visual alert highlights a critical utilization level that requires immediate action  and further analysis.


## Notes
- PUE is capacity-based due to unavailability of metered facility power.
- Battery backup hours are calculated based on available battery capacity and load.

## Author
Abrar Noor Intesar 
(Data Center Power operation & Project co-ordinator specialist)

