---
layout: single
title: "Cyclistic Bike-Share: Engineering a High-Conversion Data Pipeline"
permalink: /cyclistic-case-study/
author_profile: true
header:
  overlay_image: /assets/images/cyclistic-banner.jpg
  overlay_filter: 0.5
  caption: "Engineering actionable insights from 1.9M+ rows of ridership data."
  excerpt: "A senior-level STAR analysis identifying the 'Conversion Catalysts' for annual membership growth."
---

## 🎯 The Business Task (Situation)
As a Junior Data Analyst, I was tasked by **Lily Moreno (Director of Marketing)** to answer a critical business question: *How do annual members and casual riders use Cyclistic bikes differently?* The goal was to identify behavioral "hooks" that could be used to convert high-value casual riders into profitable annual members.

## 🛠 The Action: Engineering-Grade Data Processing
In engineering, a system's output is only as reliable as its input. I treated the **1.97M+ unique records** (November 2024 – May 2025) as a fluid system where "flow" represents user movement.

### 1. Data Source & Decision Logic
* **Infrastructure:** I utilized **BigQuery** for extraction and transformation because standard tools like Google Sheet reach "failure point" at this scale (1.9M raw records).
* **Source:** Publicly available 7-month trip data provided by **Motivate International Inc**.

### 2. Transformation Rigor (The "Cleaning" Protocol)
* **Standardization:** Implemented `TRIM()` functions across station columns to eliminate string noise.
* **Handling Nulls:** Replaced missing start/end station IDs (approx. 18.4% and 19.2% of fields) with the value `'unknown'` using `IFNULL()`. This preserved total ride volume for high-level metrics while allowing for filtered station-specific deep dives.
* **Calculated Safety Factors:** Used `TIMESTAMP_DIFF` to create `trip_duration_sec` and utilized `LEAST()`/`GREATEST()` logic to ensure all temporal durations were non-negative and physically possible.

## 💡 Key Findings: The 21-Insight Breakdown
My analysis uncovered **21 distinct strategic insights**, categorized into three "Operational Pillars":

### Pillar 1: Temporal Habits (When they ride)
* **Commuter Utility:** Members consistently peak during mid-week mornings and evenings, suggesting a high reliance on Cyclistic for the "Workplace-Home" corridor.
* **Weekend Leisure:** Casual riders peak on **Saturdays**, with their usage volume surging by nearly **40%** compared to their weekday baseline.

### Pillar 2: Ride Characteristics (How they ride)
* **The Duration Gap:** Casual riders maintain significantly longer "Time-on-Bike" (avg. trips often exceeding **1,200s**) compared to the efficient, shorter bursts of members.
* **Asset Preference:** Casual riders show a higher propensity for **Classic Bikes**, especially for leisure-oriented trips.

### Pillar 3: Geographic Concentration (Where they ride)
* **Recreational Hubs:** Casual rides are heavily centered around recreational areas (e.g., *DuSable Lake Shore Dr & Monroe St*), while members are concentrated in educational and business districts.

## 📊 Visualized Demand Patterns  
<div style="text-align: center;">
  <img src="/assets/images/cyclistic-demand-chart.jpg" alt="Cyclistic Demand Analysis: Member vs. Casual Riders" style="border-radius: 8px; box-shadow: 0 4px 8px rgba(0,0,0,0.1);">
  <p><em>'*Figure 1: Comparative analysis of ridership volume, highlighting the strategic 40% surge in casual riders during weekend intervals.*' phenomenon.</em></p>
</div>
> *This visualization highlights the 'Weekend Cross-over'—the strategic window where casual ridership volume provides the highest conversion opportunity.*

## 🚀 Strategic Recommendations
Based on the 21-point analysis, I proposed three long-term actions:
1.  **Seasonal Spring Campaigns:** Partner with parks, museums, and tourism boards to promote memberships at high-traffic casual corridors during peak May surges.
2.  **The "Ride Streak" Mechanic:** Introduce gamified rewards for casual riders who hit frequent usage milestones, building brand attachment before the membership pitch.
3.  **Tiered Membership Options:** Explore a "Weekend-Only" annual pass to capture the high-volume leisure segment.

---

### 📂 Technical Verification
| Artifact | Access Link |
| :--- | :--- |
| **GitHub Repository** | [View Technical SQL & Code](https://github.com/Divine-Ezennia/Cyclistic-Bike-Share-Analysis){: .btn .btn--primary} |
| **Kaggle Notebook** | [View Interactive Analysis](https://www.kaggle.com/code/divineezennia/cyclistic-case-study-strategic-data-analysis){: .btn .btn--info} |
| **Tableau Dashboard** | [View Executive Visuals](https://public.tableau.com/app/profile/ezennia.divine/vizzes){: .btn .btn--success} |
