# Namma Yatri Ride Data Analysis & Visualization

## Project Objective

This project focuses on performing Exploratory Data Analysis (EDA) on ride-hailing data from Namma Yatri in Bengaluru[cite: 1]. The primary goal is to uncover insights into ride patterns, customer behavior, and operational bottlenecks to guide decisions aimed at improving service efficiency, maximizing revenue, and enhancing customer satisfaction[cite: 1]. This analysis serves as a case study presented through Power BI visualizations and a methodology report[cite: 4, 6].

## Dataset

The dataset captures trip details, customer/driver behavior, and payment information from Namma Yatri rides in Bengaluru, provided via CSV files derived from an Excel source (`nammayatri.xlsx`). It comprises five main tables[cite: 3]:

* **Assembly:** Contains geographical area data (Assembly zones) in Bengaluru[cite: 3].
* **Duration:** Tracks hourly time slots (e.g., "0-1" for 12 AM-1 AM) for temporal analysis[cite: 3].
* **Payment:** Documents transaction methods (e.g., Cash, UPI)[cite: 3].
* **Trip_Details:** Monitors various stages and flags within a trip request funnel (searches, quotes, cancellations, OTP entry, ride end)[cite: 3].
* **Trips:** Records details of completed/logged journeys, including fare, distance, driver/customer IDs, and links to other tables[cite: 3].

A detailed data description is available in the methodology report[cite: 3].

## Tools Used

* **Microsoft Power BI:** For data modeling, analysis (DAX measures), visualization, and dashboarding.
* **Power Query:** For data cleaning and preparation within Power BI.

## Methodology & Analysis Steps

1.  **Data Preparation:**
    * Imported the five CSV datasets into Power BI[cite: 18].
    * Established relationships between the tables in the data model view, ensuring correct cardinality and handling active/inactive relationships (e.g., for pickup/dropoff zones)[cite: 19, 20].
    * Performed data cleaning and consistency checks using Power Query[cite: 21, 22]:
        * Verified and adjusted data types[cite: 25].
        * Checked for errors and missing values[cite: 26, 27]. Investigated and filtered records with blank/null `loc_from` IDs in `Trip_Details` to resolve data integrity issues affecting zone analysis[cite: 33, 34, 38].
        * Checked for duplicates, particularly `tripid` uniqueness[cite: 28].
        * Examined distributions of key numeric fields (`fare`, `distance`) for outliers or anomalies[cite: 30, 36, 37]. Confirmed `searches_got_estimate` flag only contained '1'[cite: 31].

2.  **Exploratory Data Analysis (EDA):** [cite: 40]
    * Classified variables as categorical or numerical[cite: 41].
    * Analyzed ride demand (`Total Trips`) and revenue (`Total Revenue`) patterns over 24 hours, identifying multi-peak trends (commute, mid-day, late-night)[cite: 53, 64, 66].
    * Investigated the relationship between trip hour and `Average Fare`, revealing significant volatility and divergence from volume peaks[cite: 73, 86].
    * Examined payment method popularity, finding relatively balanced usage with Credit Card slightly leading[cite: 97, 101, 106].
    * Identified high-performing zones based on `Total Searches`, `Total Trips`, and `Total Revenue`, noting differences between high-volume and high-value zones[cite: 109, 111, 113, 120].
    * Compared hourly trip patterns across different zones using a matrix visual[cite: 121, 130].
    * Analyzed cancellation rates, finding extremely high levels (~55% failure rate) with significant overlap between customer (~48%) and driver (~47%) cancellations, and a large "Both Cancelled" segment (~41%)[cite: 133, 141, 142].
    * Calculated the overall quote-to-completion rate (~67.6%) but identified data linkage issues preventing reliable hourly analysis of this metric[cite: 143, 174, 185].
    * Used a What-if Parameter to analyze the impact of minimum trip distance on volume and hourly patterns, finding that longest trips peak strongly mid-day and late-night[cite: 145, 155, 158, 162].

3.  **Visualization & Reporting:**
    * Created interactive dashboards in Power BI structured into multiple pages (e.g., Overview, Operational Insights, Customer Behavior, Parameterized Analysis)[cite: 14].
    * Developed visuals including KPIs, line charts, bar charts, donut charts, matrix visuals, and tables to present findings[cite: 13].
    * Summarized key insights and provided actionable recommendations based on the analysis[cite: 17, 164, 186].

## Key Insights Summary

* **High Cancellations:** The extremely high cancellation rate, particularly the ~41% cancelled by both parties, is a critical operational issue needing investigation[cite: 142].
* **Multi-Peak Demand/Value:** Ride demand and revenue have multiple peaks daily, not just standard commutes. Average fare value per trip also varies significantly by hour and doesn't always correlate with volume[cite: 72, 86].
* **Zone Performance Variation:** Zones exhibit different characteristics – some have high search volume but lower revenue/completion (e.g., Mahadevapura), while others generate high revenue from lower search volume (e.g., Bangalore South)[cite: 120, 115].
* **Trip Distance Patterns:** Most trips are short/medium distance (<14km). The longest trips peak most strongly during mid-day and late-night hours[cite: 150, 155, 162].

## Report Structure

The accompanying Power BI report (`.pbix` file) is structured with multiple pages focusing on:
* Executive Overview
* Operational Insights (Zone performance, hourly patterns by zone)
* Customer & Driver Behavior (Cancellations, Funnel analysis)
* Parameterized Analysis (Trip Distance filter)
* Recommendations

