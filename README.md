# MaxAB Sales Analysis Case Study

<img width="994" height="570" alt="MaxAB" src="https://github.com/user-attachments/assets/8e37e9c2-02e2-4c63-806e-38f70ac62643" />

## Project Overview

This Power BI project provides a comprehensive analysis of Maxab's sales operations by integrating agent visit data and retailer order information. The solution transforms raw field data into an interactive dashboard that delivers actionable insights across sales performance, retailer behavior, and agent productivity to drive strategic business decisions.

## Business Tasks

The analysis aimed to:
1.  Clean and prepare raw visit and order data for analysis
2.  Measure agent performance through key metrics (Strike Rate, Ticket Size)
3.  Analyze retailer activation patterns (Organic vs Inorganic)
4.  Calculate monthly retention rates and identify growth opportunities
5.  Segment retailers using RFM analysis for targeted strategies
6.  Optimize agent time utilization and route efficiency
7.  Build an interactive dashboard for ongoing performance monitoring

## Data Sources

The analysis uses two primary datasets:
1.  **VISIT Table**: Contains agent visit information (`visit_id`, `agent_id`, `retailer_id`, `visit_date`, `start_time`, `arrive_time`, `end_time`, `visit_reason`, `manager_id`)
2.  **ORDER Table**: Contains order transaction details (`order_id`, `order_date`, `retailer_id`, `NMV`, `sales_status_id`, `sales_order_status_description`)

## Data Model

I built a **Star Schema** data model in Power BI for optimal performance:

*   **Fact Tables:** `VISIT`, `ORDER`
*   **Dimension Tables:** `RETAILERS` (bridge table), `CALENDAR` (custom date table)
*   **Relationships:**
    *   `RETAILERS[Retailer ID]` → `VISIT[retailer_id]` (1:Many)
    *   `RETAILERS[Retailer ID]` → `ORDER[retailer_id]` (1:Many)
    *   `CALENDAR[Date]` → `VISIT[visit_date]` (Active)
    *   `CALENDAR[Date]` → `ORDER[order_date]` (Inactive)

## Key Metrics & Analysis

### Core KPIs
*   Total Visits, Associated Orders, Strike Rate
*   Total NMV, Average Ticket Size
*   Monthly Active Retailers, Retention Rate

### Advanced Analysis

1.  **Agent Performance Segmentation:**
    *   Calculated Strike Rate and Ticket Size for each agent
    *   Identified top performers and coaching opportunities
    *   Analyzed time utilization and travel efficiency

2.  **Retailer Activation Analysis:**
    *   Distinguished between Organic (self-activated) and Inorganic (agent-driven) activations
    *   Tracked daily activation patterns and trends

3.  **RFM Retailer Segmentation:**
    *   Calculated Recency, Frequency, and Monetary value for each retailer
    *   Segmented retailers into categories: Champions, Loyal, At Risk, Need Attention
    *   Developed targeted strategies for each segment

4.  **Visit Impact Analysis:**
    *   Measured effectiveness of agent visits by time of month
    *   Identified optimal timing for maximum impact

## Dashboard

The interactive Power BI report consists of four pages:

1.  **Executive Overview:** High-level KPIs, performance trends, and agent leaderboard
2.  **Agent Performance:** Detailed analysis of strike rates, ticket sizes, and time utilization
3.  **Retailer Analysis:** RFM segmentation, retention trends, and activation patterns
4.  **Operational Insights:** Visit impact analysis and operational efficiency metrics

## Tools & Technologies

*   **Power BI:** Data modeling, DAX measures, visualization, and dashboard design
*   **Power Query (M):** Data transformation and cleaning
*   **DAX:** Advanced calculations for performance metrics and time intelligence

## How to Use

1.  Download the `Maxab_Sales_Analytics.pbix` file
2.  Open in Power BI Desktop
3.  Use the interactive filters to analyze performance by:
    *   Time period (month, quarter, year)
    *   Agent teams or individual performers
    *   Retailer segments
    *   Geographic regions

## Insights & Recommendations

1.  **Agent Performance Optimization:**
    *   Implement targeted coaching for agents with low strike rates
    *   Develop reward programs for top performers
    *   Optimize travel routes to reduce non-productive time

2.  **Retailer Retention Strategy:**
    *   Create tailored engagement programs for At Risk retailers
    *   Develop loyalty rewards for Champion retailers
    *   Implement proactive outreach for declining segments

3.  **Activation Improvement:**
    *   Focus agent efforts on high-potential geographic areas
    *   Develop self-service tools to increase organic activations
    *   Optimize visit scheduling based on impact analysis

4.  **Operational Efficiency:**
    *   Streamline visit reporting and order tracking
    *   Implement real-time performance monitoring
    *   Develop predictive analytics for resource allocation

## Project Structure

```
Maxab-Sales-Analytics/
│
├── Data/
│   ├── VISIT.csv
│   └── ORDER.csv
│
├── Assets/
│   └── dashboard_overview.png
│
├── Documentation/
│   ├── DAX_Measures.pdf
│   └── User_Guide.pdf
│
├── Maxab_Sales_Analytics.pbix
└── README.md
```

## Author

**Mahmoud Abdallah**

### Any Questions
**Mahmoud_Abdallah20@outlook.com**
